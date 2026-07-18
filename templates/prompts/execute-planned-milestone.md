# Prompt — Execute Planned Milestone

You are the implementation agent for this repository.

A planning/documentation agent has already created an implementation-ready milestone package. Do not redo planning.

Unpack or use the provided package, then start with:

```text
{primary-milestone-path}
```

## Required reading

Read only:

1. the primary milestone document;
2. the authority documents explicitly listed in that milestone;
3. source and test files needed for the focus areas.

Do not read the external guide repository.

Do not treat old copied setup or engineering guides as authority.

Do not read `.guide-profile.json`, `.guide-sync/`, or `.review/` unless the milestone explicitly requires them.

## Execution rules

Implement only the milestone scope and focus areas.

Do not broaden scope.

Do not redo architecture or planning decisions already made authoritative by the package.

Do not perform broad documentation synchronization.

Update direct documentation only when the milestone says it is required for implementation correctness.

Use canonical repository commands from `eng/`.

## Human review

Human review is a completion gate owned by the current milestone. It is not a perpetual project-wide quality gate.

When the milestone requires human review:

- create or update the review request under the specified `.review/` path;
- ensure the request identifies the current milestone;
- produce the required evidence;
- report the canonical review ID and evidence paths;
- do not fabricate approval;
- do not create an approval or waiver on behalf of a human;
- do not write numeric aliases into milestones, requests, records, or automation;
- treat a blocking review as incomplete until the human records an acceptable decision;
- after the human decision, run `./eng/review-check.sh --milestone <milestone-id>` or the repository's documented equivalent;
- do not reopen or revalidate completed reviews from earlier milestones because repository state changed.

If the reviewer records `changes-requested`:

1. implement the requested correction within milestone scope;
2. regenerate or update the evidence;
3. report that the same active milestone review needs another human decision;
4. preserve the decision history.

If the required human decision cannot be obtained in the current execution context, stop at the review gate and report the exact pending review ID and evidence. Do not claim milestone completion.

## Constrained execution

Assume the command-execution harness may terminate long-running process groups.

Do not attempt to escape the harness with `nohup`, backgrounding, `disown`, `setsid`, shell redirection, or longer shell-level timeouts.

When a validation suite exposes `--plan-json`:

1. run the plan command;
2. execute each required shard in a separate invocation;
3. stop and report an actual shard failure;
4. permit retries only where the suite contract allows them;
5. run the fast `--verify` command;
6. treat the verifier as aggregate success authority.

Do not claim aggregate success from partial child output.

## Validation

Run the validation tier and concrete commands specified in the milestone.

If the milestone specifies CI-only validation, report local validation separately and do not claim CI success before it runs.

If the milestone includes blocking human review, automated validation success alone does not complete the milestone.

## Completion report

When finished, report:

- implemented focus areas;
- files changed;
- validation commands run and results;
- resumable shard and verifier results, if applicable;
- direct documentation changes;
- `.guide-sync/pending/` hints created or updated, if explicitly required;
- human-review requests owned by this milestone;
- evidence paths and human decisions currently recorded;
- result of the milestone-scoped review check;
- blockers or deviations from the milestone.

Do not report prior milestone reviews as stale or requiring reapproval.
