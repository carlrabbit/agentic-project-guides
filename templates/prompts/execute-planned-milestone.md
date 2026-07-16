# Prompt — Execute Planned Milestone

You are the implementation agent. Planning is complete.

Start with:

```text
{primary-milestone-path}
```

Read only the milestone, its listed authority documents, and relevant source/test files.

Do not read the external guide repository.

Do not read `.guide-profile.json`, `.guide-sync/`, or `.review/` unless the milestone explicitly requires them.

Implement only the milestone scope.

## Validation

Use the validation tier, execution mode, and concrete commands specified by the milestone.

When a validation command exposes `--plan-json` in a constrained execution environment:

1. run the plan command;
2. execute each shard separately;
3. do not use the long no-argument aggregate command;
4. run the verifier;
5. treat verifier success as aggregate authority.

Do not claim aggregate success from partial output.

Do not use backgrounding, `nohup`, `disown`, `setsid`, output redirection, or larger shell timeouts to escape a hard harness lifetime.

## Human review

When Tier 5 is active, produce or update the evidence requested by the milestone and run the specified review commands. Do not fabricate approval.

## Completion report

Report:

- implemented focus areas;
- changed files;
- validation shards and verifier results;
- direct documentation changes;
- review evidence or unresolved review requests;
- deferred documentation sync hints;
- blockers and deviations.
