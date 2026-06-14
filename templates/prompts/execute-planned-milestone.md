# Prompt — Execute Planned Milestone

You are the implementation agent for this repository.

A planning/documentation agent has already created an implementation-ready milestone package. Do not redo planning.

Unpack or use the provided milestone package, then start with:

```text
{primary-milestone-path}
```

Read only:

1. the primary milestone document;
2. the authority documents explicitly listed in that milestone;
3. source and test files needed for the focus areas.

Do not read the external guide repository.

Do not treat old copied setup or engineering guides as authority.

Do not read `.guide-profile.json` or `.guide-sync/` unless the milestone explicitly says this is guide migration, documentation synchronization, engineering migration, or release-readiness work.

Implement only the milestone scope and focus areas.

Do not broaden scope.

Do not perform broad documentation synchronization.

Update direct documentation only when the milestone says it is required for implementation correctness.

Use the validation tier and concrete commands specified in the milestone.

When finished, report:

- implemented focus areas;
- files changed;
- validation commands run and results;
- direct documentation changes;
- deferred documentation sync hints, if any;
- blockers or deviations from the milestone.
