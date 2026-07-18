# Prompt Templates

## Purpose

This index lists standard prompts for disconnected planning, implementation, migration, documentation synchronization, review, and release workflows.

Prompt templates are guide-system methodology. They live in the guide repository, not in product repositories.

## Prompt selection

| Task | Prompt |
|---|---|
| Adopt latest guide system from any older local guide model | `templates/prompts/adopt-latest-guide-system.md` |
| Update from any existing guide-system version to latest | `templates/prompts/update-to-latest-guide-system.md` |
| Prepare a completely empty new project | `templates/prompts/new-empty-project.md` |
| Plan a human-led milestone | `templates/prompts/milestone-human-led.md` |
| Plan an AI-assisted milestone | `templates/prompts/milestone-ai-assisted.md` |
| Plan an AI-executed, human-reviewed milestone | `templates/prompts/milestone-ai-executed-human-reviewed.md` |
| Plan a broad AI-executed milestone | `templates/prompts/milestone-ai-executed-broad.md` |
| Plan an engineering migration milestone | `templates/prompts/milestone-engineering-migration.md` |
| Plan a documentation synchronization milestone | `templates/prompts/milestone-documentation-sync.md` |
| Plan a release-readiness milestone | `templates/prompts/milestone-release-readiness.md` |
| Execute a planned milestone | `templates/prompts/execute-planned-milestone.md` |
| Execute an engineering migration | `templates/prompts/execute-engineering-migration.md` |
| Execute documentation synchronization | `templates/prompts/execute-documentation-sync.md` |
| Execute release readiness | `templates/prompts/execute-release-readiness.md` |
| Perform a documentation synchronization pass | `templates/prompts/documentation-sync-pass.md` |

## Human-review rule in v0.6.0

Human review is a completion gate owned by one milestone.

Planning prompts must define review class, evidence, canonical ID, blocking behavior, and completion command for the current milestone.

Execution prompts must not fabricate approval and must stop at a blocking review when human action is unavailable.

Completed review records are historical evidence and must not be revalidated because later commits changed the repository.

## Prompt preservation rule

Minor and patch updates must extend or correct complete operational prompt templates. They must not replace them with abbreviated summaries unless the abbreviated prompt is intentionally introduced as a separate variant.

When modifying a prompt:

- preserve repository inspection rules;
- preserve deliverable boundaries;
- preserve milestone content requirements;
- preserve authority routing;
- preserve validation and documentation-sync rules;
- preserve chat response requirements;
- preserve quality criteria;
- integrate new concepts into the full existing body.
