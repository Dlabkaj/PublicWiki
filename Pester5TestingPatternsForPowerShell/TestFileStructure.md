# Test File Structure

> How a Pester 5 test file is organized: a top-level `Describe` block containing `It` tests, grouped by area with `Context`, framed with `BeforeAll`/`BeforeEach`/`AfterEach`/`AfterAll` for setup and teardown.

## Key facts

- All executable code must live inside `It`, `BeforeAll`, `BeforeEach`, `AfterAll`, or `AfterEach` blocks — never directly inside `Describe`/`Context` or at the top of the file (source: https://pester.dev/docs/usage/test-file-structure)
- Code placed outside those blocks runs during **Discovery**, and its results are not available during **Run**, producing confusing behavior (source: https://pester.dev/docs/usage/test-file-structure)
- `Describe` and `Context` are the same function internally; they differ only in `Mock -Scope Describe|Context` behavior and how the block name is written in output (source: https://pester.dev/docs/usage/test-file-structure)
- `AfterAll` is guaranteed to run even if tests inside its block fail (source: https://pester.dev/docs/usage/test-file-structure)
- `BeforeDiscovery` is the sanctioned escape hatch for code that must run during Discovery (typically to build data used by data-driven blocks) (source: https://pester.dev/docs/usage/test-file-structure)
- Test files are conventionally named `<Name>.Tests.ps1` and import the code under test via `. $PSCommandPath.Replace('.Tests.ps1', '.ps1')` inside a top-level `BeforeAll` (source: https://pester.dev/docs/usage/test-file-structure)

## Canonical layout

A minimal file dot-sources the code under test inside `BeforeAll`, then wraps a single top-level `Describe` (named for the function under test) around one or more `It` blocks:

```powershell
BeforeAll {
    . $PSCommandPath.Replace('.Tests.ps1', '.ps1')
}

Describe "Get-Emoji" {
    It "Returns 🌵 (cactus)" {
        Get-Emoji -Name cactus | Should -Be '🌵'
    }
}
```

> Note: the pester.dev page this example comes from now renders the **v6** documentation, where the assertion is written `Should-Be` (hyphenated command). Pester 5 uses the parameterised form `Should -Be`, which is what is shown above.

As a file grows, related `It`s are grouped under nested `Describe`/`Context` blocks; each group can carry its own `BeforeAll` to run setup once per group (e.g. calling the function once and asserting against the cached result), which avoids per-test copy-paste and typos.

## Setup and teardown scoping

- `BeforeAll` / `AfterAll` — run once at the start / end of the containing `Describe` or `Context`.
- `BeforeEach` / `AfterEach` — run before / after each `It` inside the containing block.
- Blocks nest: an inner `Context`'s `BeforeAll` runs after the outer `Describe`'s `BeforeAll`.

## Discovery vs Run and BeforeDiscovery

Pester 5 executes tests in two phases: **Discovery** walks the file to enumerate blocks, then **Run** executes them. The Pester 5 mantra is *"no code outside Pester-controlled blocks."* When code genuinely needs to run during Discovery (for example, building the array a data-driven `-ForEach` will expand over), it goes inside a `BeforeDiscovery { ... }` block — which signals the intent explicitly rather than relying on top-level script code.

## Data-driven expansion at the file level

`-ForEach` (also aliased `-TestCases`) can be applied to `Describe` and `Context`, not just `It`, causing the block to repeat once per element of the supplied array. Combined with `BeforeDiscovery` (or a script `param()` block that receives external data), this lets a single `Describe "function <_> has help" -ForEach $files { ... }` generate one test group per file (source: https://pester.dev/docs/usage/test-file-structure).

## Complexity guidance

The Pester documentation explicitly cautions against over-parameterization. Its author notes that the "more complex file with test cases" example — a nested `Describe`/`Context` layout with `-TestCases` on the `It` blocks — is "about right for 90% of tests I write," and that further collapsing similar contexts into a single parameterized `Context` is technically possible but not recommended. The stated principle: *"The simpler you are able to keep your tests the better. The more static your tests are, the easier it is to feel confident that everything works."*

## Test script parameters

A `.Tests.ps1` file may declare a `param(...)` block at the top to accept external data (typically supplied via `New-PesterContainer -Data`). Values received there are visible in Discovery and can drive `-ForEach` expansion of `Describe`/`Context`. Cross-reference: [[DataDrivenTests]].

## Open questions

- (none flagged)

## Sources

- https://pester.dev/docs/usage/test-file-structure — official Pester docs page on test file layout, block scoping, Discovery/Run, and `BeforeDiscovery`.
