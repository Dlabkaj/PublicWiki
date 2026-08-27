# Mocking

> Pester's mocking API replaces the implementation of any PowerShell command inside a test so calls are recorded and controlled behavior is returned. Assertions verify how the mock was (or wasn't) called.

## Key facts

- The core mocking surface in Pester 5 is: `Mock` (replace an implementation), `Should-Invoke` (assert call counts / parameters), and `Should-Invoke -Verifiable` (assert every `-Verifiable` mock actually ran) (source: https://pester.dev/docs/usage/mocking)
- Any PowerShell command — cmdlet, function, or native executable — can be mocked (source: https://pester.dev/docs/usage/mocking)
- Mocks are scoped to the block in which they are placed — a `Mock` inside an `It` only affects that `It`; a `Mock` inside `BeforeAll` affects the whole containing `Describe`/`Context`. This is a change from Pester v4 (source: https://pester.dev/docs/usage/mocking)
- `Should-Invoke` inside `It`/`BeforeEach`/`AfterEach` defaults to **It** scope; inside `Describe`/`Context`/`BeforeAll`/`AfterAll` it defaults to the containing block. Override with `-Scope` (source: https://pester.dev/docs/usage/mocking)
- Parameter filters in v5 no longer require a `param()` block — parameters are auto-bound as `$variable` names inside `-ParameterFilter { ... }` (source: https://pester.dev/docs/usage/mocking)
- Inside a mock's `-MockWith` scriptblock, `$PSBoundParameters` is **overwritten** by Pester's proxy; use `$PesterBoundParameters` instead to read/forward the caller's bound parameters (source: https://pester.dev/docs/usage/mocking)
- In Pester **v5** behavior (relevant when contrasted below): if none of a command's `-ParameterFilter` mocks match a call and no default (unfiltered) mock exists, the call **falls through to the real command** silently (source: https://pester.dev/docs/usage/mocking)
- Mocking a function that is called by a class method: works normally on **PowerShell 6+**. On Windows PowerShell ≤ 5.1, class definitions are cached across module reloads, which breaks `Mock`; the documented workaround is running Pester in a fresh session via `Start-Job` (Dave Wyatt's `Invoke-PesterJob` proxy) (source: https://pester.dev/docs/usage/mocking)
- To mock a command called from inside a script module, additional setup is required — see the "Unit Testing within Modules" page (cross-reference in source) (source: https://pester.dev/docs/usage/mocking)

## Anatomy of a mocked test

```powershell
Describe "BuildIfChanged" {
    Context "When there are Changes" {
        BeforeEach {
            Mock Get-Version     { return 1.1 }
            Mock Get-NextVersion { return 1.2 }
            Mock Build { } -Verifiable -ParameterFilter { $version -eq 1.2 }

            $result = BuildIfChanged
        }

        It "Builds the next version"     { Should-Invoke -Verifiable }
        It "returns the next version"    { $result | Should-Be 1.2 }
    }
}
```

The pattern: arrange mocks and exercise the system under test in `BeforeEach`, assert behavior in each `It`. `-Verifiable` marks a mock as one that *must* be called; `Should-Invoke -Verifiable` (no name) checks that every `-Verifiable` mock was invoked at least once.

## Scoping model

Mocks live in the block that defined them and are visible to child blocks:

- `Mock` in `BeforeAll` of a `Describe` → active for every `It` in that `Describe` and its child `Context`s.
- `Mock` in `BeforeEach` → re-established for every `It` in scope.
- `Mock` inside an `It` → active only for that single `It` (a sibling `It` still sees the real command).

## Counting rules

`Should-Invoke` measures calls within a scope, and the *default* scope depends on where the assertion sits:

| Location of `Should-Invoke` | Default scope |
|---|---|
| `It`, `BeforeEach`, `AfterEach` | `It` (i.e. calls in this one test) |
| `Describe`, `Context`, `BeforeAll`, `AfterAll` | the containing `Describe`/`Context` |

`-Scope Describe` (or `-Scope Context`) overrides this — useful when asserting cumulative call counts from inside an `AfterAll` or across multiple `It`s.

## Parameter filters

`-ParameterFilter { <predicate> }` restricts which invocations a given mock (or assertion) matches. Bound parameters are available directly as `$name`:

```powershell
Mock f { "ten" } -ParameterFilter { $a -eq 10 }
Should-Invoke f -Exactly 1 -ParameterFilter { $a -eq 10 }
```

Multiple `Mock` statements for the same command with different filters stack; the most specific matching filter wins, and an unfiltered `Mock` acts as the default.

## Mocking native executables

Native commands have no named parameters inside the `-MockWith` block; positional arguments are read from `$args`. A common pattern is to match by concatenating: `-ParameterFilter { "$args" -match '--url https://google.com -I' }`. The docs' sample uses `curl` and notes that on Windows PowerShell, the built-in `curl → Invoke-WebRequest` alias must be removed first (`Remove-Item Alias:curl`) for portable behavior.

## `$PesterBoundParameters`

Because `Mock` installs a proxy hook in front of the real command, `$PSBoundParameters` inside the mock body reflects the proxy — not the caller. Pester exposes the caller's bound parameters as `$PesterBoundParameters`, which can be spat back at the real command to implement partial mocks:

```powershell
Mock Write-Host -MockWith {
    Write-Warning "MOCKED - $Object"
    & (Get-Command -CommandType Cmdlet -Name Write-Host) @PesterBoundParameters
}
```

## v5 vs v6 note (scope-relevant contrast)

The source page mixes v5 and v6 behavior. Two behaviors are called out as *v6 changes*, so by contrast they describe v5's semantics:

- **Fall-through:** In v5, an unmatched filtered `Mock` with no default silently calls the real command. v6 removes this and throws instead.
- **Mock history on failure:** v6 prints matched (`[*]`) / unmatched (`[ ]`) invocation lists on `Should-Invoke` assertion failure. v5 does not.

For Pester 5 tests, adding an unfiltered default `Mock <cmd> { }` alongside filtered mocks is the way to avoid accidental real-command execution.

## Open questions

- (none flagged)

## Sources

- https://pester.dev/docs/usage/mocking — official Pester Mocking page (covers `Mock`, `Should-Invoke`, scoping, parameter filters, native commands, `$PesterBoundParameters`, class-method quirk, and v4/v6 change notes).
