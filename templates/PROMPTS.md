# Prompt Templates

## Purpose

This index lists standard prompts for disconnected planning, implementation, migration, documentation synchronization, review, and release workflows.

Prompt templates are guide-system methodology. They live in the guide repository, not in product repositories.

## Two-phase milestone rule in v0.7.0

Coding milestones are planned before implementation regardless of execution mode or model choice.

Planning resolves material architectural, semantic, compatibility, scope, acceptance, and validation uncertainty and produces a ready milestone.

Implementation reads the ready milestone and localized project authority, inspects the live repository, derives concrete implementation mechanics, implements, and validates.

Implementation does not require the planning conversation and escalates material unresolved decisions back to planning.

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
| Execute a ready milestone | `templates/prompts/execute-planned-milestone.md` |
| Execute an engineering migration | `templates/prompts/execute-engineering-migration.md` |
| Execute documentation synchronization | `templates/prompts/execute-documentation-sync.md` |
| Execute release readiness | `templates/prompts/execute-release-readiness.md` |
| Perform a documentation synchronization pass | `templates/prompts/documentation-sync-pass.md` |

## Planning prompt requirements

Planning prompts may differ by execution mode, but for coding milestones they must converge on the same ready-milestone boundary:

- resolve implementation-affecting uncertainty;
- record durable decisions in project truth when needed;
- define target state, constraints, non-goals, acceptance criteria, and validation;
- list authority the executor actually needs;
- avoid exhaustive mechanical edit instructions unless contractually significant;
- ensure the executor does not need the planning conversation or external guide repository.

## Human-review rule

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
