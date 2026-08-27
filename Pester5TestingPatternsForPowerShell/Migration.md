# Migrating from Pester v4 to v5

## The core change: two-phase execution

Pester 5 splits a run into two phases — **Discovery** and **Run**. During Discovery, Pester scans test files and identifies every `Describe`, `Context`, `It`, and other Pester block. Only afterwards does it execute the tests.

This changes how tests must be structured, so a migration is not a pure find-replace. See [[TestFileStructure]] for the resulting v5 layout and [[DataDrivenTests]] for the `-ForEach`/`-TestCases` consequences.

## The main rule: keep test code inside blocks

Put all test code inside `It`, `BeforeAll`, `BeforeEach`, `AfterAll`, or `AfterEach`. Do not place test code directly inside `Describe`, `Context`, or at the top of a file.

Misplaced code will execute during Discovery, and its results will not be available during Run. Code that genuinely must run during Discovery should be placed inside `BeforeDiscovery`.

Keeping code out of the block bodies keeps Discovery fast and responsive.

## Move file-level setup into `BeforeAll`

Setup that used to live at the top of the file (dot-sourcing the tested script, importing modules, etc.) moves into a `BeforeAll` block:

```powershell
BeforeAll {
    # DON'T use $MyInvocation.MyCommand.Path
    . $PSCommandPath.Replace('.Tests.ps1', '.ps1')
}

Describe "Get-Cactus" {
    It "Returns cactus" {
        Get-Cactus | Should -Be 'cactus'
    }
}
```

Use `$PSCommandPath` inside `BeforeAll`, not `$MyInvocation.MyCommand.Path`.

A migration script is available in the docs to move file-level setup into `BeforeAll` automatically.

## `-Skip` conditions evaluate during Discovery

`It -Skip:$SomeCondition` evaluates `$SomeCondition` during Discovery, before any `BeforeAll` runs. A variable defined inside `BeforeAll` will be `$null` at that point (interpreted as `$false`) and the test will run.

Broken:

```powershell
Describe "d" {
    BeforeAll {
        function Get-IsSkipped { Start-Sleep -Second 1; $true }
        $isSkipped = Get-IsSkipped
    }
    It "i" -Skip:$isSkipped {}
}
```

Working (but the skip logic runs on every Discovery pass):

```powershell
function Get-IsSkipped { Start-Sleep -Second 1; $true }
$isSkipped = Get-IsSkipped

Describe "d" {
    It "i" -Skip:$isSkipped {}
}
```

Prefer static global variables (like `$IsWindows`) or cheap-to-execute expressions for skip conditions.

## `-TestCases` also evaluate during Discovery

Test-case data given to `-TestCases` is evaluated during Discovery and cached for the Run phase. Expensive setup for test cases therefore runs on every Discovery. On the upside, each test case's data is now exposed under `Data` on the result test object.

## `Invoke-Pester`: simple vs. advanced interface

Pester 5 replaces the "extremely bloated" v4 `Invoke-Pester` parameter set with two shapes.

**Simple interface** — flat parameters:

```
Invoke-Pester -Path <String[]> -ExcludePath <String[]> -Tag <String[]> -ExcludeTag <String[]>
              -FullNameFilter <String[]> -Output <String> -CI -PassThru
```

**Advanced interface** — a single `PesterConfiguration` object:

```
Invoke-Pester -Configuration <PesterConfiguration>
```

Simple-parameter → configuration mapping:

| Simple parameter | Configuration property |
| --- | --- |
| `Path` | `Run.Path` |
| `ExcludePath` | `Run.ExcludePath` |
| `Tag` | `Filter.Tag` |
| `ExcludeTag` | `Filter.ExcludeTag` |
| `FullNameFilter` | `Filter.FullName` |
| `Output` | `Output.Verbosity` |
| `CI` | `TestResult.Enabled` and `Run.Exit` (both `$true`) |
| `PassThru` | `Run.PassThru` |

### Legacy (v4) parameter mapping

Some v4-only parameters map to the configuration object:

| v4 parameter | Configuration property |
| --- | --- |
| `EnableExit` | `Run.Exit` |
| `CodeCoverage` | `CodeCoverage.Path` |
| `CodeCoverageOutputFile` | `CodeCoverage.OutputPath` |
| `CodeCoverageOutputFileEncoding` | `CodeCoverage.OutputEncoding` |
| `CodeCoverageOutputFileFormat` | `CodeCoverage.OutputFormat` |
| `OutputFile` | `TestResult.OutputPath` |
| `OutputFormat` | `TestResult.OutputFormat` |
| `Show` | `Output.Verbosity` (via mapping below) |

`-Show` value → `Output.Verbosity`:

| `-Show` value | `Output.Verbosity` |
| --- | --- |
| `All` | `Detailed` |
| `Default` | `Detailed` |
| `Detailed` | `Detailed` |
| `Fails` | `Normal` |
| `Diagnostic` | `Diagnostic` |
| `Normal` | `Normal` |
| `Minimal` | `Minimal` |
| `None` | `None` |

## New result object and v4 compatibility

The Pester 5 result object is "extremely rich" and is used internally for all Pester decisions; most fields are unprocessed to expose raw data.

To feed an existing v4-style CI pipeline, convert the result: `ConvertTo-Pester4Result`.

To emit an NUnit report from the new object, either call `ConvertTo-NUnitReport` or pass `-CI` to `Invoke-Pester` — the `-CI` switch enables NUnit output, code coverage, and non-zero exit on failure.

## Implicit variables for `-TestCases`

Pester 5 splats each test-case hashtable *and* injects its keys as variables in the parent scope, so `It` no longer needs a `param` block:

```powershell
Describe "a" {
    It "b" -TestCases @(
        @{ Name = "Jakub"; Age = 30 }
    ) {
        $Name | Should -Be "Jakub"
    }
}
```

The same implicit-parameter behavior applies to `Mock`.

## Mocks: no scriptblock rewriting

Pester 5 no longer rewrites the scriptblock passed to `Mock`. Breakpoints can be set inside the mock body and inside any `-ParameterFilter` used with `Mock` or `Should -Invoke`.

## Avoid `InModuleScope` around `Describe`/`It`

`InModuleScope` exposes internal module functions for testing, but wrapping whole `Describe`/`It` blocks in it:

- prevents proper testing of the module's *published* functions,
- doesn't verify that the functions you intended to publish are actually exported,
- slows Discovery down by forcing the module to load.

The recommended alternative is `-ModuleName` on `Mock`. If `InModuleScope` is still needed, keep it inside `It`, not around whole blocks.

## Sources

- <https://pester.dev/docs/migrations/v4-to-v5>
