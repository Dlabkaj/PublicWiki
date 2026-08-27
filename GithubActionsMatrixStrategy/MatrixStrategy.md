# Matrix strategy

> A matrix strategy in GitHub Actions lets a single job definition automatically expand into multiple runs, one per combination of variable values. Common uses: testing across language versions and operating systems in one job.

## Key facts

- Configured under `jobs.<job_id>.strategy.matrix` (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)
- A job runs once per combination of the matrix variables (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)
- Matrix values can be built from a context expression, e.g. `${{ github.event.client_payload.versions }}`, so the matrix is defined by event payload (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)
- A matrix value can be sourced from another job's output via `${{ fromJSON(needs.<job>.outputs.<name>) }}` (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)

## Expansion

Given two variables — `version: [10, 12, 14]` and `os: [ubuntu-latest, windows-latest]` — the job runs six times, once per (version, os) pair. GitHub documents the ordering as version-major then os-minor: `{10, ubuntu}`, `{10, windows}`, `{12, ubuntu}`, `{12, windows}`, `{14, ubuntu}`, `{14, windows}` (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

## include — add or extend combinations

`jobs.<job_id>.strategy.matrix.include` takes a list of objects. Each entry either adds keys to matching existing combinations (when it does not overwrite any of their values) or, if it cannot be merged without overwriting, becomes a new combination on its own.

Applied to the base matrix `fruit: [apple, pear], animal: [cat, dog]` with these `include` entries:

- `{color: green}` — merges into every existing combination (no overwrite)
- `{color: pink, animal: cat}` — merges into combinations that already have `animal: cat`; overwrites the `color: green` those entries got from the prior include
- `{fruit: apple, shape: circle}` — merges `shape: circle` into combinations with `fruit: apple`
- `{fruit: banana}` — cannot merge without overwriting `fruit`; added as a new combination
- `{fruit: banana, animal: cat}` — also cannot merge; added as another new combination (it does *not* extend the previously-added `{fruit: banana}` because that entry was not part of the *original* matrix)

Result: six combinations (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

The last bullet is the subtle rule: `include` entries only extend the **original** matrix, never other includes.

## exclude — remove combinations

`jobs.<job_id>.strategy.matrix.exclude` removes combinations that match all keys listed in the exclude entry. A partial-key exclude removes every combination matching those keys — so `{os: windows-latest, version: 16}` in the docs' example removes two jobs (one per value of `environment`) (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

## Handling failures

- `jobs.<job_id>.strategy.fail-fast`: when `true`, a failing job cancels all in-progress and queued jobs in the matrix (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)
- `jobs.<job_id>.continue-on-error`: per-job flag; a job that fails with this `true` does not cause other jobs to fail (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)
- The two can be combined and `continue-on-error` can be expressed as a matrix variable, e.g. `continue-on-error: ${{ matrix.experimental }}` (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow)

## max-parallel

`jobs.<job_id>.strategy.max-parallel` caps the number of matrix jobs that run simultaneously, regardless of runner availability (source: https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

Fail-fast is **on by default** for matrix jobs, cancelling in-flight jobs on the first failure (sources: https://runs-on.com/github-actions/the-matrix-strategy/, https://octopus.com/devops/github-actions/github-actions-matrix/).

## strategy.job-index

Inside a matrix job, `${{ strategy.job-index }}` returns the zero-based index of the current job within the matrix. Useful for splitting a test suite across matrix slots by index (source: https://runs-on.com/github-actions/the-matrix-strategy/).

## Dynamic matrix from a previous job

A common pattern for a dynamic matrix: an upstream job writes `matrix=<json>` to `$GITHUB_OUTPUT`, exposes it as a job output, and the downstream job sets `strategy.matrix: ${{ fromJson(needs.build.outputs.matrix) }}`. The upstream JSON may itself use `{"include": [...]}` to fabricate combinations that are not products of variables (sources: https://runs-on.com/github-actions/the-matrix-strategy/, https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

### Include-only matrix (no base variables)

A matrix may be declared with **only** an `include:` list and no other variables, producing exactly the listed combinations with no product expansion. Example:

```yaml
strategy:
  matrix:
    include:
      - version: 12
        os: ubuntu-latest
      - version: 14
        os: windows-latest
```

Useful when the desired job configurations are not shaped like a combinatorial set (source: https://devopsdirective.com/posts/2025/08/advanced-github-actions-matrix/).

### Dynamic fan-out via `fromJSON` + include-only

The include-only form composes with `fromJSON` to fan a job out over an arbitrary, runtime-computed set of configurations:

```yaml
execute:
  needs: generate-matrix
  strategy:
    matrix:
      include: ${{ fromJSON(needs.generate-matrix.outputs.include) }}
```

The upstream job builds the JSON array (e.g. by inspecting changed paths, or by a shard selector) and any entries it omits produce no downstream job — filtering happens by shaping the JSON, not with `if:` on the matrix (source: https://devopsdirective.com/posts/2025/08/advanced-github-actions-matrix/).

⚠️ **`if:` does not work at matrix level.** You cannot put `if: ${{ matrix.<key> == '...' }}` on the matrix job to skip individual combinations; the correct approach is to omit those entries from the upstream JSON *(needs second source)* (source: https://devopsdirective.com/posts/2025/08/advanced-github-actions-matrix/).

### Shared upstream matrix feeding multiple downstream jobs

A single upstream job's output can drive `strategy.matrix` in **more than one** downstream job. Example: a `define-matrix` job outputs `colors=["yellow","orange","brown"]`; a `produce-artifacts` job runs a matrix over those colors to upload one artifact per color; a `consume-artifacts` job runs the *same* matrix (both wired via `needs: define-matrix`) to download and read each artifact. Both downstream jobs use `matrix: color: ${{ fromJson(needs.define-matrix.outputs.colors) }}` (sources: https://octopus.com/devops/github-actions/github-actions-matrix/, https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow).

### Fan-out to a reusable workflow

The dynamic fan-out pattern combines with reusable workflows: the matrix job's body is `uses: ./.github/workflows/<callee>.yml` and each matrix entry becomes one call, with fields from the JSON passed via `with:` (e.g. `shard-index`, `gradle-task`, `total-shards` for a test-sharding pipeline). Cited as an alternative to hand-copied per-shard job blocks (source: https://devopsdirective.com/posts/2025/08/advanced-github-actions-matrix/).

## Common matrix use cases seen in the wild

- Multi-architecture container builds — a `platform` matrix (e.g. `linux/amd64`, `linux/arm64/v8`) driving `docker/build-push-action` via `platforms: ${{ matrix.platform }}` (source: https://runs-on.com/github-actions/the-matrix-strategy/).

## Sources

- https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow — GitHub Docs page on matrix strategies; covers matrix definition, include/exclude semantics, fail-fast, continue-on-error, max-parallel, and matrices derived from job outputs or event payloads.
- https://runs-on.com/github-actions/the-matrix-strategy/ — RunsOn "Mastering GitHub Actions" tutorial page on the matrix strategy: worked examples for include/exclude/fail-fast/max-parallel, dynamic matrix from `$GITHUB_OUTPUT`, and the `strategy.job-index` context.
- https://devopsdirective.com/posts/2025/08/advanced-github-actions-matrix/ — DevOps Directive post on the dynamic fan-out pattern: include-only matrices, `fromJSON` of an upstream job's output, fan-out into a reusable workflow (test sharding), and the "no `if:` on a matrix job" pitfall.
- https://octopus.com/devops/github-actions/github-actions-matrix/ — Octopus Deploy tutorial: basic matrix syntax, include/exclude, fail-fast/continue-on-error, and the pattern of one upstream job's JSON output seeding matrices in multiple downstream jobs (`define-matrix` → produce/consume artifacts).
