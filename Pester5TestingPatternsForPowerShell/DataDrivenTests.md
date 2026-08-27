# Data Driven Tests

> Pester generates tests from data via the `-ForEach` parameter (aliased `-TestCases` on `It` for v4 compatibility). Supply an array — of hashtables or plain values — and one test/block is emitted per element, with names templated via `<...>` tokens.

## Key facts

- `-ForEach` is available on `It`, `Describe`, and `Context`; on `It` it is also aliased `-TestCases` for backwards compatibility with Pester v4 (source: https://pester.dev/docs/usage/data-driven-tests)
- When `-ForEach` receives an **array of hashtables**, each hashtable key becomes a variable in the generated test/block (e.g. `@{ Name = 'cactus' }` → `$Name` available inside `It`) (source: https://pester.dev/docs/usage/data-driven-tests)
- When `-ForEach` receives a **plain array**, the current item is bound to `$_`. `$_` is *also* bound when the array is hashtables — set to the current hashtable (source: https://pester.dev/docs/usage/data-driven-tests)
- `<name>` tokens in an `It`/`Describe`/`Context` name are expanded at run time using any variable in scope — not only `-ForEach` variables. Dot-navigation (`<animal.emoji>`) works on nested objects (source: https://pester.dev/docs/usage/data-driven-tests)
- Template names should be **single-quoted** so PowerShell does not interpolate `$var` / `$(...)` at parse time (Discovery), which would happen before the data exists (source: https://pester.dev/docs/usage/data-driven-tests)
- Template expansion is deferred until *after* the block's setup runs, so `<banana>` can reference a variable defined in the block's own `BeforeAll` — even though the name is visually above the setup (source: https://pester.dev/docs/usage/data-driven-tests)
- Data provided to `-ForEach` is available in both **Discovery** and **Run** (source: https://pester.dev/docs/usage/data-driven-tests)
- Escape a literal `<` in a name with `` `< ``; outside a `<...>` template every `` ` ``, `$`, and `"` is auto-escaped so literals like `$null` render as-is (source: https://pester.dev/docs/usage/data-driven-tests)
- `$PSBoundParameters` is **not available** in Pester tests; a `.Tests.ps1` `param()` block's parameters must be referenced by their variable names (source: https://pester.dev/docs/usage/data-driven-tests)
- `New-PesterContainer -Path ... -Data @{ Key = Value }` feeds a `.Tests.ps1` file's `param()` block; pass an array of hashtables to run the same file once per data set (source: https://pester.dev/docs/usage/data-driven-tests)

## Minimal `-ForEach` on `It`

```powershell
Describe "Get-Emoji" {
    It "Returns <expected> (<name>)" -ForEach @(
        @{ Name = "cactus";  Expected = '🌵' }
        @{ Name = "giraffe"; Expected = '🦒' }
    ) {
        Get-Emoji -Name $name | Should -Be $expected
    }
}
```

> Note: the pester.dev pages behind this article now render the **v6** documentation, where assertions are written as hyphenated commands (`Should-Be`). The examples here use the Pester 5 parameterised form `Should -Be`, matching this wiki's v5 scope.

Equivalent to writing two `It` blocks by hand. Add a new case = add a new hashtable — no test-body duplication.

## `-ForEach` on `Describe`/`Context`

```powershell
Describe "Get-Emoji <name>" -ForEach @(
    @{ Name = "cactus";  Symbol = '🌵'; Kind = 'Plant' }
    @{ Name = "giraffe"; Symbol = '🦒'; Kind = 'Animal' }
) {
    It "Returns <symbol>"   { Get-Emoji -Name $name | Should -Be $symbol }
    It "Has kind <kind>"    { Get-Emoji -Name $name | Get-EmojiKind | Should -Be $kind }
}
```

Yields one `Describe` per data row, each containing every `It` inside. Nested `-ForEach` works too — an inner `Context -ForEach $runes` can iterate a property of the outer row's hashtable.

## Discovery vs Run — the trap `-ForEach` solves

Pester 5 runs a **two-phase** execution: Discovery walks the file to enumerate blocks; Run executes the collected `It`/`Before*`/`After*` scriptblocks later. Variables defined bare in the script body (or bare in a `Describe`/`Context` body) exist only during Discovery — they are **not** in scope during Run.

```powershell
$name = "Jakub"                     # visible in Discovery only
Describe "d" {
    It "My name is: $name" {        # name expands correctly during Discovery
        $name | Should -Be "Jakub"  # FAILS at Run: $name is $null
    }
}
```

This is exactly why the classic `foreach ($file in $files) { Describe "$file" { It "..." { Get-Content $file } } }` pattern is broken in v5: `$file` is not defined during Run. The fix is to hand the data to `-ForEach`, which captures values during Discovery and re-binds them into every generated block at Run time.

## Idiomatic v5 replacement for the `foreach` pattern

```powershell
BeforeDiscovery {
    $files = Get-ChildItem "../src/*.ps1" -Recurse
}

Describe "<file>" -ForEach $files {
    BeforeAll {
        $file = $_          # rename automatic $_ for readability
        $content = Get-Content $file
    }
    It "<file> - has help" {
        # ...
    }
}
```

Three moves: put generator code in `BeforeDiscovery` to signal intent, hand `$files` directly to `-ForEach`, and reference the item via `<file>` templates + `$_` (optionally renamed in `BeforeAll`).

## External data via `New-PesterContainer -Data`

A `.Tests.ps1` file can declare its own `param()` block; Pester binds it in both Discovery and Run:

```powershell
# CodingStyle.Tests.ps1
param ([Parameter(Mandatory)][string] $File)

BeforeAll { $content = Get-Content $File }
Describe "File - <file>" {
    Context "Whitespace" {
        It "There is no extra whitespace following a line" { ... }
    }
}
```

Invoke it via a container:

```powershell
$container = New-PesterContainer -Path 'CodingStyle.Tests.ps1' -Data @{ File = "Get-Emoji.ps1" }
Invoke-Pester -Container $container -Output Detailed
```

Pass an **array** of hashtables to `-Data` (or build one container per file and pass an array of containers) to re-run the same file against many inputs. `New-PesterContainer -Path` also accepts wildcards, so `-Path '*Style.Tests.ps1'` can broadcast one data set across every matching file.

## `<>` template details

- Any in-scope variable can be used, not just `-ForEach` keys: `<apple>`, `<banana>`, `<file>`.
- Dot-navigation reads nested members: `<animal.emoji>`, `<animal.sound>`.
- Templates render through Pester's own formatter — the source's *Internals* section notes only `<...>` tokens are rewritten; the surrounding literal text is left intact and never re-parsed as code.
- **Always single-quote** template names. Double-quoted names get `$` / `$()` expanded by PowerShell at parse time (Discovery), before your data exists.

## `BeforeDiscovery`

Code placed directly in a script body or a `Describe`/`Context` body executes during Discovery. Pester 5's convention is to keep such code inside a `BeforeDiscovery { ... }` block — it is functionally the same as bare top-level code, but signals *"this runs at Discovery on purpose."* Use it to build the arrays you then feed into `-ForEach`. See [[TestFileStructure]] for how `BeforeDiscovery` fits the overall block layout.

## v6 note (contrast with v5)

Two behaviors are marked as v6 changes on the source page, so by contrast they describe v5:

- **Empty/null data:** in v5, `-ForEach $null` or `-ForEach @()` silently skips the test. v6 throws; opt back into v5 behavior with `-AllowNullOrEmptyForEach` or `Run.FailOnNullOrEmptyForEach = $false`.
- **Expressions in `<>` templates:** v6 evaluates `<($a + $b)>` as a PowerShell expression in test scope. v5 restricts templates to variable names + dot-navigation only.

## Open questions

- (none flagged)

## Sources

- https://pester.dev/docs/usage/data-driven-tests — official Pester Data Driven Tests page: `-ForEach`/`-TestCases`, `<>` templates, `BeforeDiscovery`, `New-PesterContainer -Data`, and the v4→v5 migration of the `foreach` pattern.
