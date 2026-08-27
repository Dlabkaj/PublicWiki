# CI Integration

> How Pester 5 emits machine-readable test results — NUnit or JUnit XML — and how the common CI systems (TeamCity, AppVeyor, Azure DevOps, GitHub Actions) consume them.

## Key facts

- Pester can output results in **NUnit 2.5, NUnit 3, or JUnit 4** schemas (source: https://pester.dev/docs/usage/test-results)
- The v5 API for result files is a `PesterConfiguration` object: `TestResult.Enabled`, `TestResult.OutputFormat` (`NUnitXml` / `NUnit3` / `JUnitXml`), `TestResult.OutputPath` (source: https://pester.dev/docs/usage/test-results)
- **Code Coverage metrics are not embedded in the NUnit XML** — they must be published separately (e.g. via a `PassThru` object and CI-specific `##teamcity[...]` service messages) (source: https://pester.dev/docs/usage/test-results)
- `$config.Run.PassThru = $true` makes `Invoke-Pester -Configuration $config` return a result object (with `FailedCount`, `CodeCoverage.CommandsAnalyzedCount`, `CodeCoverage.CommandsExecutedCount`, etc.) that the CI script can inspect (source: https://pester.dev/docs/usage/test-results)
- If tests write to the PowerShell pipeline, the `PassThru` object returned by `Invoke-Pester` will **also contain that pipeline output** — the docs explicitly warn about this (source: https://pester.dev/docs/usage/test-results)
- Failing the build on failed tests is idiomatically done in the calling script with `if ($res.FailedCount -gt 0) { throw "..." }` — Pester itself does not exit non-zero automatically in these examples (source: https://pester.dev/docs/usage/test-results)
- Legacy `Invoke-Pester -OutputFile` / `-OutputFormat` parameters were **removed in Pester v6**; they still exist in v5 but the docs recommend the `PesterConfiguration` path (source: https://pester.dev/docs/usage/test-results)

## Configuration surface

```powershell
$config = New-PesterConfiguration
$config.TestResult.Enabled       = $true
$config.TestResult.OutputFormat  = 'NUnitXml'    # or 'NUnit3', 'JUnitXml'
$config.TestResult.OutputPath    = 'Test.xml'
Invoke-Pester -Configuration $config
```

`NUnitXml` is the format the pester.dev docs use in every CI recipe (TeamCity, AppVeyor, Azure DevOps); `JUnitXml` is the alternative interchange schema Pester will emit.

## TeamCity

1. Run Pester with `TestResult.OutputPath = "Test.xml"` (relative to the agent working directory).
2. In the build configuration, add the **"XML Report Processing"** build feature with **Report Type = NUnit**, version 2.5.0.
3. Point its Monitoring Rules at the same path (`Test.xml` for the shipped `pester.bat`).

The `pester.bat` shipped with the module auto-writes `Test.xml` to the agent working directory — no configuration needed when using it.

**Coverage on TeamCity** (not carried in NUnit XML): enable `PassThru` and emit service messages from the object:

```powershell
$config.Run.PassThru         = $true
$config.CodeCoverage.Enabled = $true
$config.CodeCoverage.Path    = (Get-ChildItem -Path $PSScriptRoot\*.ps1 -Exclude *.Tests.*).FullName
$testResults = Invoke-Pester -Configuration $config

Write-Output "##teamcity[buildStatisticValue key='CodeCoverageAbsLTotal'   value='$($testResults.CodeCoverage.CommandsAnalyzedCount)']"
Write-Output "##teamcity[buildStatisticValue key='CodeCoverageAbsLCovered' value='$($testResults.CodeCoverage.CommandsExecutedCount)']"
```

Troubleshooting note from the docs: some TeamCity deployments require explicitly selecting PowerShell 5.1 in the build step.

## AppVeyor

Serialize NUnit XML and POST it to the per-job test-results endpoint:

```yaml
test_script:
  - ps: |
      $testResultsFile = ".\TestsResults.xml"
      $config = New-PesterConfiguration
      $config.TestResult.Enabled       = $true
      $config.TestResult.OutputFormat  = 'NUnitXml'
      $config.TestResult.OutputPath    = $testResultsFile
      $config.Run.PassThru             = $true
      $res = Invoke-Pester -Configuration $config

      (New-Object 'System.Net.WebClient').UploadFile(
          "https://ci.appveyor.com/api/testresults/nunit/$($env:APPVEYOR_JOB_ID)",
          (Resolve-Path $testResultsFile))

      if ($res.FailedCount -gt 0) { throw "$($res.FailedCount) tests failed." }
```

The `throw` on `FailedCount -gt 0` is what actually fails the build.

## Azure DevOps

Run Pester, then use a **Publish Test Results** task with **Test Result format = NUnit** (not the default JUnit) pointing at the XML file:

```powershell
Install-Module -Name Pester -Force -SkipPublisherCheck
Import-Module Pester

$config = New-PesterConfiguration
$config.Run.Path                = "$(System.DefaultWorkingDirectory)\MyFirstModule.test.ps1"
$config.TestResult.Enabled      = $true
$config.TestResult.OutputFormat = 'NUnitXml'
$config.TestResult.OutputPath   = "$(System.DefaultWorkingDirectory)\Test-Pester.XML"
Invoke-Pester -Configuration $config
```

The docs note that using the built-in Azure PowerShell task does not require "Continue on error" ahead of the publish step; Marketplace Pester tasks may vary.

## GitHub Actions

The Pester Code Coverage docs page ships a minimal workflow snippet that doubles as the standard test-run recipe on GitHub Actions:

```yaml
name: Run Pester Tests
on:
  push:        { branches: ["dev", "main"] }
  pull_request:{ branches: ["dev"] }

jobs:
  pester:
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install Pester
        shell: pwsh
        run: Install-Module -Name Pester -Force -Scope CurrentUser
      - name: Run Pester Tests
        working-directory: ./solution
        run: |
          $config = New-PesterConfiguration
          $config.Run.Path             = "."
          $config.CodeCoverage.Enabled = $true
          $config.TestResult.Enabled   = $true
          Invoke-Pester -Configuration $config
      - name: Upload code coverage report
        if: ${{ success() }}
        uses: actions/upload-artifact@v4
        with:
          name: code-coverage-report
          path: solution\coverage.xml
```

(source: https://pester.dev/docs/usage/code-coverage) — the pattern is the same shape as the AppVeyor/Azure recipes: install Pester, run with `PesterConfiguration`, publish the resulting XML(s) as artifacts.

## Exit code and `Run.Exit`

A CI runner does not read the test summary — it checks whether the process exited 0 (success) or non-zero (failure). The green check or red X hangs on that number. (source: https://keith-ramsey.com/blog/pester-in-cicd)

`Invoke-Pester` sets a failing exit code on its own when run as the top-level command, but Keith Ramsey's blog treats this as implicit and names `$config.Run.Exit = $true` as the "robust, explicit pattern" that guarantees a non-zero exit on failure. `Run.Exit` is the property the v4 `-EnableExit` parameter maps to in the official v4→v5 migration table, and one of the two properties the v4 `-CI` switch maps to (`TestResult.Enabled` + `Run.Exit`, both `$true`) (source: https://pester.dev/docs/migrations/v4-to-v5).

```powershell
$config = New-PesterConfiguration
$config.Run.Path = './Tests'
$config.Run.Exit = $true   # exit non-zero if any test fails
Invoke-Pester -Configuration $config
```

The blog's "Common mistakes" section lists checking `FailedCount` and `throw` as an equivalent alternative to `Run.Exit`; the pester.dev AppVeyor recipe uses exactly that pattern (`if ($res.FailedCount -gt 0) { throw "..." }`).

**Run.Exit vs. throw in caller.** Both approaches produce a non-zero exit on failure and both are documented by the Pester project — `Run.Exit` in the v4→v5 migration table and Keith Ramsey's blog, `throw` on `FailedCount` in the pester.dev AppVeyor example. The choice is stylistic: `Run.Exit` fails inside `Invoke-Pester`; the `throw` pattern fails in the calling script and lets it inspect the result object first.

## Pinning the Pester version

On a clean CI machine, PowerShell already ships a Pester — on Windows that's the legacy 3.4, which shadows any v5 installation. Always install a pinned version so today's green build means the same thing next year. *(needs second source)* (source: https://keith-ramsey.com/blog/pester-in-cicd)

```powershell
Install-Module Pester -RequiredVersion 5.5.0 -Force -SkipPublisherCheck -Scope CurrentUser
Import-Module Pester -RequiredVersion 5.5.0
```

- `-RequiredVersion` nails an exact build.
- `-SkipPublisherCheck` avoids the signing prompt that would otherwise stall a non-interactive runner.
- Pinning stops a future Pester release from silently changing build behavior.

## Reusable CI test script

The blog favours pulling the Pester run out of pipeline YAML and into a small PowerShell script the pipeline calls — the same script runs locally, keeping the YAML thin. Saved as `build/run-ci-tests.ps1` (source: https://keith-ramsey.com/blog/pester-in-cicd):

```powershell
$config = New-PesterConfiguration

$config.Run.Path = "$PSScriptRoot/../Tests"
$config.Run.Exit = $true

$config.TestResult.Enabled      = $true
$config.TestResult.OutputFormat = 'NUnitXml'
$config.TestResult.OutputPath   = "$PSScriptRoot/../testResults.xml"

$config.CodeCoverage.Enabled    = $true
$config.CodeCoverage.Path       = "$PSScriptRoot/../src"
$config.CodeCoverage.OutputPath = "$PSScriptRoot/../coverage.xml"

$config.Output.Verbosity        = 'Detailed'

Invoke-Pester -Configuration $config
```

`TestResult.Enabled` writes `testResults.xml` in NUnit format; `CodeCoverage` produces a JaCoCo `coverage.xml` (JaCoCo is Pester's default coverage format per https://pester.dev/docs/usage/code-coverage); the pipeline publishes both.

## GitHub Actions — Ubuntu / `pwsh` variant

An alternate GitHub Actions recipe using `ubuntu-latest`, cross-platform PowerShell 7 (`shell: pwsh`), a pinned Pester, and the reusable script above (source: https://keith-ramsey.com/blog/pester-in-cicd).

```yaml
name: Pester
on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Install Pester (pinned)
        shell: pwsh
        run: |
          Install-Module Pester -RequiredVersion 5.5.0 -Force -SkipPublisherCheck -Scope CurrentUser
          Import-Module Pester -RequiredVersion 5.5.0

      - name: Run Pester
        shell: pwsh
        run: ./build/run-ci-tests.ps1

      - name: Publish test results
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: pester-results
          path: |
            testResults.xml
            coverage.xml
```

`Run.Exit = $true` inside the script makes `pwsh` exit non-zero; GitHub Actions fails any step whose command exits non-zero, so the `Run Pester` step fails the job automatically. `if: always()` on the publish step keeps the artifact even when tests fail — exactly when it is most useful.

## Azure Pipelines — `PublishTestResults@2` with `failTaskOnFailedTests`

An Azure DevOps equivalent using the `PublishTestResults@2` task, which understands NUnit XML natively and renders a per-test report (source: https://keith-ramsey.com/blog/pester-in-cicd; the pester.dev Azure DevOps recipe likewise directs users to a Publish Test Results task with format set to NUnit).

```yaml
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- task: PowerShell@2
  displayName: 'Install Pester (pinned)'
  inputs:
    targetType: inline
    pwsh: true
    script: |
      Install-Module Pester -RequiredVersion 5.5.0 -Force -SkipPublisherCheck -Scope CurrentUser
      Import-Module Pester -RequiredVersion 5.5.0

- task: PowerShell@2
  displayName: 'Run Pester'
  inputs:
    targetType: filePath
    filePath: 'build/run-ci-tests.ps1'
    pwsh: true

- task: PublishTestResults@2
  displayName: 'Publish test results'
  condition: always()
  inputs:
    testResultsFormat: 'NUnit'
    testResultsFiles: 'testResults.xml'
    failTaskOnFailedTests: true
```

`condition: always()` publishes results even when tests fail; `failTaskOnFailedTests: true` makes a failing test unmistakable in the report.

## Speed: cache modules, split fast/slow by tag

Two performance patterns from the blog (source: https://keith-ramsey.com/blog/pester-in-cicd):

- **Cache the PowerShell module path** keyed on the Pester version so the install step is skipped on a cache hit — installing from the gallery every run "adds seconds".
- **Split runs by tag**: run only `Unit`-tagged tests on every push for fast feedback, reserve slower `Integration` tests for a nightly schedule. "Fast pipelines get used; slow ones get skipped."

## Common mistakes (Keith Ramsey summary)

- **Not failing the build on a failed test.** A Pester invocation that swallows the exit code leaves the build green while tests are red — use `Run.Exit = $true` or check `FailedCount` and `throw`.
- **Not pinning the Pester version.** A CI machine may still be on legacy v3.4, or a future v5 release may change behavior — pin with `-RequiredVersion`.
- **Never publishing the results.** Without the TestResult XML plus a publish step guarded by `if: always()` / `condition: always()`, a red X carries no clue which test broke.

## Practical guidance

- **Choose the schema your dashboard understands.** NUnitXml is the format the pester.dev docs use in every CI recipe (TeamCity, AppVeyor, Azure DevOps); JUnitXml is the alternative Pester emits.
- **Coverage is a separate publish step**, always. Do not expect the test-result XML to carry it.
- **Pick one way to fail the build and be explicit about it.** `Run.Exit = $true` fails inside `Invoke-Pester`; `Run.PassThru = $true` plus `if ($res.FailedCount -gt 0) { throw }` fails in the caller and lets it inspect the result first. Both are documented Pester patterns.
- Be aware that `PassThru` picks up pipeline output from tests; keep test bodies from emitting to the pipeline, or filter the return object.

## Sources

- https://pester.dev/docs/usage/test-results — official Pester "Showing Test Results in CI" page: NUnit/JUnit schemas, `PesterConfiguration.TestResult`, and TeamCity/AppVeyor/Azure DevOps recipes.
- https://pester.dev/docs/usage/code-coverage — the GitHub Actions workflow snippet is on the Code Coverage page; JaCoCo is the default coverage output format.
- https://pester.dev/docs/migrations/v4-to-v5 — v4→v5 mapping table showing `EnableExit → Run.Exit` and `CI → TestResult.Enabled + Run.Exit`.
- https://keith-ramsey.com/blog/pester-in-cicd — Keith Ramsey, "Running Pester in CI/CD (GitHub Actions & Azure Pipelines)": exit-code discipline via `Run.Exit`, pinning Pester versions, a reusable script pattern, Ubuntu/`pwsh` GitHub Actions workflow, Azure Pipelines with `PublishTestResults@2` / `failTaskOnFailedTests`, module caching, and tag-based fast/slow split.
