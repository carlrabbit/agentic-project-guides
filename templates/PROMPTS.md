# Prompt Templates

## Planning

- `prompts/adopt-latest-guide-system.md`
- `prompts/update-to-latest-guide-system.md`
- `prompts/new-empty-project.md`
- milestone planning prompts by execution mode

## Execution

- `prompts/execute-planned-milestone.md`
- `prompts/execute-engineering-migration.md`
- `prompts/execute-documentation-sync.md`
- `prompts/execute-release-readiness.md`

## v0.5.0 execution rule

Planning prompts should declare validation execution mode.

When a milestone uses resumable validation, its execution prompt must tell the implementation agent to:

1. run `--plan-json`;
2. execute every shard in a separate invocation;
3. stop on real shard failure;
4. run `--verify`;
5. report the verifier result;
6. never infer success from partial aggregate output.

Human review and documentation synchronization remain separate repository-local workflows under `.review/` and `.guide-sync/`.
