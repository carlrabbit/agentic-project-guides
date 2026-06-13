# Prompt Templates

## Purpose

This index lists standard prompts for using the guide system in disconnected planning, implementation, migration, and documentation synchronization workflows.

The prompt templates are guide-system methodology. They should live in this guide repository, not in product repositories.

## Prompt selection

| Task | Prompt |
|---|---|
| Migrate an old guide-based repository to guide system v0.1.0 | `templates/prompts/migration-to-guide-system-v0.1.0.md` |
| Migrate guide-system usage from v0.1.0 to v0.2.0 | `templates/prompts/migration-v0.1.0-to-v0.2.0.md` |
| Prepare a completely empty new project | `templates/prompts/new-empty-project.md` |
| Plan a human-led milestone | `templates/prompts/milestone-human-led.md` |
| Plan an AI-assisted milestone | `templates/prompts/milestone-ai-assisted.md` |
| Plan an AI-executed, human-reviewed milestone | `templates/prompts/milestone-ai-executed-human-reviewed.md` |
| Plan a broad AI-executed milestone | `templates/prompts/milestone-ai-executed-broad.md` |
| Plan an engineering migration milestone | `templates/prompts/milestone-engineering-migration.md` |
| Plan a documentation sync milestone/package | `templates/prompts/milestone-documentation-sync.md` |
| Plan a release-readiness milestone | `templates/prompts/milestone-release-readiness.md` |
| Perform a documentation synchronization pass | `templates/prompts/documentation-sync-pass.md` |

## Common rule

Planning prompts may read the external guide repository. Implementation agents should not be required to read the guide repository. Milestones must list only target-repository authority documents required for implementation.

## Sync hints

Planning prompts must write deferred documentation synchronization hints to:

```text
.guide-sync/pending/
```

when those hints must survive handoff to another agent.

Documentation-sync prompts consume and clean up those hints.
