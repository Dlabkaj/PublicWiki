# Code Coverage

> Pester emits a per-file coverage report during a test run. In v5 it is enabled and configured through a `PesterConfiguration` object, not through `Invoke-Pester -CodeCoverage` parameters.

## Key facts

- Coverage is enabled via `New-PesterConfiguration` → `$config.CodeCoverage.Enabled = $true`, then passed as `Invoke-Pester -Configuration $config` (source: https://pester.dev/docs/usage/code-coverage)
- Default report format is **JaCoCo XML** in `coverage.xml`; readable by most CI systems and coverage dashboards (source: https://pester.dev/docs/usage/code-coverage)
- Output can be redirected/renamed via `CodeCoverage.OutputPath`, and encoded per `CodeCoverage.OutputEncoding` (source: https://pester.dev/docs/usage/code-coverage)
- `CodeCoverage.CoveragePercentTarget` sets the desired-target percentage that Pester compares the achieved percentage against in the summary line (source: https://pester.dev/docs/usage/code-coverage)
- `CodeCoverage.Path` scopes coverage collection to specific files or directories — without it, Pester analyzes what it discovers under `Run.Path` (source: https://pester.dev/docs/usage/code-coverage)
- **Pester does not recursively hunt for source under a test path** — an empty `coverage.xml` typically means tests were run from a directory not containing the code, and the fix is either co-locating tests with code or setting `CodeCoverage.Path` explicitly (source: https://pester.dev/docs/usage/code-coverage)
- Report paths in the XML are recorded relative to a root — by default `Run.RepoRoot`, located by searching upward for a `.git` directory. Override with `CodeCoverage.ReportRoot` when code lives outside the repo root (source: https://pester.dev/docs/usage/code-coverage)
- Individual functions/scriptblocks can be excluded from coverage by placing `[ExcludeFromCodeCoverageAttribute()]` before the `param()` block (source: https://pester.dev/docs/usage/code-coverage)
- With `Output.Verbosity = "Detailed"` Pester prints a "Missed commands" table listing file/function/line/command for uncovered code (source: https://pester.dev/docs/usage/code-coverage)

## Quickstart

```powershell
$config = New-PesterConfiguration
$config.Run.Path             = "."
$config.CodeCoverage.Enabled = $true
Invoke-Pester -Configuration $config
```

Console summary example (verbatim from the docs):

```
Tests Passed: 8, Failed: 0, Skipped: 0, Inconclusive: 0, NotRun: 0
Processing code coverage result.
Covered 11.7% / 75%. 735 analyzed Commands in 22 Files.
```

The `11.7% / 75%` is *achieved / target*; the second number is `CoveragePercentTarget`.

## Scoping coverage to specific files

By default Pester covers whatever it discovers from `Run.Path`. To restrict coverage to a specific source file (independent of where tests live), set `CodeCoverage.Path`:

```powershell
$config.Run.Path             = ".\CoverageTest.Tests.ps1"
$config.CodeCoverage.Enabled = $true
$config.CodeCoverage.Path    = ".\CoverageTest.ps1"
```

Yields output like `Covered 60% / 75%. 5 analyzed Commands in 1 File.`

## Detailed output — the "Missed commands" table

Enabling `Output.Verbosity = "Detailed"` appends a per-line breakdown of uncovered code to the summary:

```
File               Class Function     Line  Command
----               ----- --------     ----  -------
CoverageTest.ps1         FunctionOne  5     return 'SwitchParam was set'
CoverageTest.ps1         FunctionTwo  16    return 'I do not'
```

The first row surfaces genuinely untested branches; the second reveals unreachable code (a second `return` after the first). Both are the useful side-signal of a coverage run.

## Output format and encoding

```powershell
$config.CodeCoverage.OutputFormat   = 'JaCoCo'      # default; 'Cobertura' is a Pester v6 addition
$config.CodeCoverage.OutputPath     = 'cov.xml'
$config.CodeCoverage.OutputEncoding = 'UTF8'
```

Cobertura is listed as a **v6** addition on the source page; Pester 5 targets can rely on JaCoCo as the practical default.

## Excluding code from coverage

```powershell
function FunctionExcluded {
    [ExcludeFromCodeCoverageAttribute()]
    param()
    "I am not included"
}
```

Use for generated code, legacy shims, or functions that would otherwise skew the percentage without adding meaningful test signal.

## `ReportRoot` for stable paths

CI runs on different machines produce different absolute paths. Coverage records paths relative to `Run.RepoRoot` (auto-detected by walking up for `.git`) so reports stay diffable across agents. Override when the code lives outside the repo root:

```powershell
$config.CodeCoverage.ReportRoot = "$PSScriptRoot/src"
```

## v6 note (contrast with v5)

The source mentions two behaviors as *v6* changes, so by contrast:

- **Collector:** v6 defaults to a profiler-based tracer, "considerably faster" than v5's breakpoint-based collector. Pester 5 uses the breakpoint collector. (In v6, `CodeCoverage.UseBreakpoints = $true` restores v5 behavior.)
- **Cobertura output:** available in v6, not standard in v5.

For Pester 5 projects, expect the breakpoint collector's overhead on large suites and treat JaCoCo as the only realistic output format.

## Open questions

- (none flagged)

## Sources

- https://pester.dev/docs/usage/code-coverage — official Pester Code Coverage page: configuration API, coverage scoping, `ExcludeFromCodeCoverage`, formats, `ReportRoot`, and a GitHub Actions workflow snippet (covered separately on the CI page).
