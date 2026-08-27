# Reusable workflows

> A reusable workflow is a workflow file that other workflows can invoke as a job, letting a caller pass inputs and secrets and receive outputs. It replaces copy-paste of the same YAML across repositories.

## Key facts

- Location: `.github/workflows/` of a repository; subdirectories are not supported (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)
- Trigger: the workflow's `on:` must include `workflow_call` (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)
- Nesting cap: up to ten levels total — one top-level caller and up to nine reusable workflows below it (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)
- Loops in the workflow call tree are not permitted (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)
- Permissions along the nested chain can only be maintained or reduced, never elevated (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)
- Input types supported: `boolean`, `number`, `string`; the value type must match the callee's declaration (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows)

## Calling syntax

A caller invokes a reusable workflow with the `uses` keyword *directly on a job* (not inside steps). Three reference forms:

- `{owner}/{repo}/.github/workflows/{filename}@{ref}` — public or private repo; `{ref}` may be a SHA, release tag, or branch name. A release tag takes precedence over a branch of the same name. SHA is documented as safest.
- `./.github/workflows/{filename}` — same repository.
- `$/.github/workflows/{filename}` — same repository, same commit as the caller. Must **not** include an `@{ref}` suffix. Not available in GitHub Enterprise Server.

Ref prefixes like `refs/heads` or `refs/tags` are not allowed in the local forms, and contexts/expressions are not allowed in the `uses` value (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows).

## Inputs and secrets

- In the callee, declare inputs and secrets under `on.workflow_call.inputs` and `on.workflow_call.secrets`; reference them as `${{ inputs.X }}` / `${{ secrets.Y }}`.
- The caller passes them via `with:` and `secrets:` on the job that has `uses:`.
- `secrets: inherit` implicitly forwards all of the caller's secrets to a directly called workflow. Available for calls within the same organization or enterprise (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows).
- Secrets forward only to the **directly** called workflow. In chain `A → B → C`, `C` receives a secret from `A` only if `B` explicitly forwards it.
- Environment secrets **cannot** be passed via `workflow_call`, because `on.workflow_call` does not support the `environment` keyword. If a callee job sets `environment`, the environment secret is used rather than any secret passed from the caller.

## Matrix with reusable workflows

A job that uses `strategy.matrix` can also `uses:` a reusable workflow — the matrix expands the call. Example: `matrix.target: [dev, stage, prod]` with `uses: octocat/octo-repo/.github/workflows/deployment.yml@main` produces three calls, one per value, passed as `with: target: ${{ matrix.target }}` (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows).

## Outputs

The callee declares outputs at both job level (`jobs.<id>.outputs`) and workflow level (`on.workflow_call.outputs`), mapping the workflow output to a job output via `value: ${{ jobs.<id>.outputs.<name> }}`. The caller reads them as `${{ needs.<callee-job>.outputs.<name> }}`.

Step outputs must be mapped to job outputs first — they are not readable from the caller directly (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows).

### Matrix output collapse

If a reusable workflow that sets an output runs under a matrix strategy, the caller sees the output from the **last successful matrix job that actually sets a value**. An empty string does not count as setting a value: if the last successful job outputs an empty string while an earlier successful job set a real value, the earlier real value wins (source: https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows).

## Access rules

Whether a caller can invoke a callee depends on repository visibility:

| Caller repository | Accessible callee repositories |
|---|---|
| private | private and public |
| public | public |

(source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations)

Additional constraints from the reference page:

- For private callee repos, the callee's Actions settings must explicitly allow access from repositories containing callers.
- GitHub Actions does not follow redirects for actions or reusable workflows — renaming an action's owner, repo, or action name breaks callers referring to the old name (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

## Limits

- Up to **50 unique reusable workflows** can be called from a single top-level caller, including any nested tree below it (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).
- Workflow-level `env` context is **not** propagated across the call boundary in either direction. To share values, use outputs; to share variables broadly, define them at org/repo/environment scope and read via the `vars` context.
- Because reusable workflows are invoked at the job level (not from steps), `GITHUB_ENV` cannot be used to pass values from a called workflow to steps in the caller.

## Supported keywords on a job that calls a reusable workflow

Only these keys are allowed on a job whose body is `uses: <reusable workflow>`:

`name`, `uses`, `with`, `with.<input_id>`, `secrets`, `secrets.<secret_id>`, `secrets.inherit`, `strategy`, `needs`, `if`, `concurrency`, `permissions` (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

If the calling job omits `permissions`, the called workflow runs with the default `GITHUB_TOKEN` permissions. The caller's token permissions can only be downgraded (not elevated) by the callee — restated at ref-page level: in chain A > B > C, if A has `packages: read`, B and C cannot have `packages: write`.

## Concurrency pitfall

`${{ github.workflow }}` inside a called workflow resolves to the **caller's** workflow name. Setting `jobs.<id>.concurrency.group: ${{ github.workflow }}` on both caller and callee, with `cancel-in-progress: true`, will make the running caller cancel itself when it invokes the callee (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

## Runners

- **GitHub-hosted**: runner assignment is evaluated from the caller's context; billing goes to the caller. A caller cannot use GitHub-hosted runners from the callee's repository.
- **Self-hosted**: a callee owned by the same user or organization as the caller can access self-hosted runners in the caller's repository or in the caller's organization, provided those runners are made available to the caller repository (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

## `github` context and token

When a reusable workflow is triggered by a caller, the `github` context in the callee is always the caller's. The callee is automatically granted access to `github.token` and `secrets.GITHUB_TOKEN` (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

## Re-run behavior

For a reusable workflow referenced by branch or tag (not SHA):

- Re-running **all jobs** of the caller pulls the callee at the currently-specified reference (i.e. the tip at re-run time).
- Re-running **failed** or **specific** jobs pins the callee to the commit SHA resolved on the first attempt (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations).

## YAML anchors and aliases

A separate reuse mechanism, in-file only: an anchor `&name` marks content to reuse; an alias `*name` re-inserts it. Can share `env` blocks or full job configurations between jobs in the same workflow file (source: https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations). Docs point to the YAML specification for details.

## Open questions

- The matrix-output rule as documented is genuinely ambiguous in edge cases — worth confirming against a second source.

## Sources

- https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows — how-to page: creating a reusable workflow, `workflow_call` trigger, inputs/secrets, `secrets: inherit`, calling syntax variants, nesting/loop/permission rules, matrix invocation, and output plumbing.
- https://docs.github.com/en/actions/reference/workflows-and-actions/reusing-workflow-configurations — reference page: access-by-visibility table, 50-workflow limit, supported job keywords, runner/billing rules, `github` context inheritance, re-run behavior on non-SHA refs, concurrency pitfall, YAML anchors.
