# Prompt Templates

This is a compact router. The selected prompt and applicable meta models are authoritative; product implementers must not load this catalog.

## Normal workflow

1. Plan coherent agent-scaled capability work with \`templates/prompts/plan-milestone.md\`.
2. Implement a **ready** milestone with \`templates/prompts/execute-milestone.md\`.

The planner resolves material project decisions, acceptance, relevant risks, and project-local authority. The implementer chooses mechanics, may try reversible alternative approaches, uses focused feedback, and establishes the milestone's observable outcomes.

**A milestone is not a release gate.** Product package/installed-consumer/platform qualification normally belongs to release preparation. An exceptional milestone-level qualification must be justified.

The ready milestone and referenced project truth are the durable handoff. A \`.execution/\` progress ledger is optional for resumable work; planning need not seed one. Evidence-case registries, fingerprinted receipts, mandatory one-to-one proof tracking, and per-criterion gate matrices are not defaults. Do not create bespoke per-milestone copies of the canonical implementation prompt.

Milestone lifecycle: \`draft/planning -> ready -> implementing -> done\`. Execution outcomes: \`COMPLETE\`, \`AWAITING HUMAN REVIEW\`, \`BLOCKED\`. Review is a milestone-owned gate only when explicitly required. Implementers must not claim completion from green tests alone without evaluating the milestone contract, nor prolong work by inventing irrelevant validation infrastructure.

## Repository setup / updates

| Task | Prompt |
|---|---|
| New project | \`templates/prompts/new-project.md\` |
| Adopt guide in existing project | \`templates/prompts/adopt-guide-system.md\` |
| Update project to current guide | \`templates/prompts/update-guide-system.md\` |

## Special planning workflows

| Task | Prompt |
|---|---|
| Engineering migration | \`templates/prompts/special/plan-engineering-migration.md\` |
| Documentation synchronization planning | \`templates/prompts/special/plan-documentation-sync.md\` |
| Release readiness | \`templates/prompts/special/plan-release-readiness.md\` |
| Documentation synchronization pass | \`templates/prompts/special/documentation-sync-pass.md\` |
| Historical research adoption | \`templates/prompts/special/adopt-research.md\` |

Special workflow prompts use the same ready-milestone and proportionate-assurance philosophy, except that release readiness **deliberately** qualifies the final distributable candidate.

Historical version-specific prompts under \`templates/prompts/version-specific/\` are migration/repair artifacts only. See \`meta/MILESTONE-EXECUTION-MODEL.md\` and \`meta/VALIDATION-MODEL.md\` for current methodology.
