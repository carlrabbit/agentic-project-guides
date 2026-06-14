# Prompt — Execute Engineering Migration

You are the implementation agent for an engineering or guide-system migration.

Start with the provided migration milestone.

Read only:

- the migration milestone;
- the repository authority documents listed in the milestone;
- `.guide-profile.json` only if the milestone says to update or inspect it;
- `.guide-sync/pending/` only if the milestone says to create, update, or resolve sync hints.

Do not read the external guide repository unless the milestone explicitly says this execution task requires it.

Apply the migration classifications in the milestone:

- required;
- conditional;
- deprecated;
- manual-review;
- no-op.

Do not perform unrelated feature implementation.

Run the validation tier and commands specified in the milestone.

Report migrated files, skipped/no-op items, validation results, and unresolved manual-review items.
