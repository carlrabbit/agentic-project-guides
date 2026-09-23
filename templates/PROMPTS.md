# Prompt Templates

## Purpose

This index is the entry point for guide-system prompt selection.

Prompt templates are guide-system methodology. They live in the guide repository, not in product repositories.

## Normal development workflow

For ordinary milestone-driven development, use only these two prompts:

1. `templates/prompts/plan-milestone.md` during planning;
2. `templates/prompts/execute-milestone.md` after the milestone is `ready`.

Planning resolves material architectural, semantic, compatibility, scope, acceptance, and validation uncertainty. It also establishes that the resulting milestone is executable and execution-tractable by the project's baseline implementation model.

For AI-executed milestones, planning assigns stable IDs to every individually verifiable acceptance criterion and material completion obligation, then seeds `.execution/<milestone-id>.md` with a lossless pending obligation registry and the required validation gates.

When one obligation spans materially different proof paths, planning also seeds selective `EC-*` evidence cases. Do not mechanically generate Cartesian-product cases; use them only where one supported path would not prove another.

Planning does not seed work packages, implementation tasks, concrete evidence, or completion state.

Implementation reads the ready milestone, localized project authority, and planning-seeded ledger; verifies lossless obligation/evidence-case coverage; inspects the live repository; decomposes work into bounded execution work packages; maps those packages back to the seeded obligations; implements, validates, records criterion/evidence-case-specific evidence, reconciles the milestone against live evidence, performs a completion audit, persists a compact durable completion-evidence trace, and drives the milestone to a valid terminal execution outcome.

Execution profile is selected during planning. Do not choose a different planning prompt merely because implementation will be human-led, AI-assisted, or AI-executed.

Implementation does not require the planning conversation and escalates material unresolved decisions back to planning.

Passing tests or successful implementation does not by itself complete a milestone. The executor owns milestone closure and must continue resolving every agent-resolvable milestone obligation before terminating.

## Stable implementation handoff

The ready milestone plus referenced project authority is the durable semantic handoff. For AI-executed milestones, the planning-seeded ledger accompanies that handoff as non-authoritative operational coverage state.

Use `templates/prompts/execute-milestone.md` as the canonical execution methodology.

Do not generate bespoke per-milestone `EXECUTE-Mxxx.md` or equivalent files that duplicate the canonical prompt, milestone acceptance criteria, or project authority.

Overlay/archive application instructions and a short note identifying the primary ready-milestone path are valid transport context. They are not a second execution contract.

## Baseline-model readiness rule

The project's baseline implementation model is planning metadata. The default ChatGPT-focused guide profile uses GPT-5.6 Luna.

A coding milestone is `ready` only when that baseline model can execute the contract without inventing a new material decision about architecture, semantics, compatibility, scope, acceptance, validation, or human-review policy.

Readiness also includes execution tractability: long implementation volume must be decomposable by the executor into bounded coherent work packages whose coverage/progress can be persisted and recovered from repository-local state.

The guide does not use `strong`, `frontier`, or similar model-capability execution tiers as a normal remedy for incomplete planning.

Planning should perform the difficult project-level reasoning, make completion observable, and leave local implementation mechanics to the executor.

If a material decision requires additional evidence, plan a diagnostic or investigation milestone first. Use its evidence to return to planning and produce the final implementation-ready milestone.

Baseline executability does not require tiny milestones. Large coherent work remains valid when decisions are settled, obligations are explicit, implementation can be decomposed into bounded work packages, and validation can be bounded, sharded, or resumed safely.

Special planning workflows that produce coding or repository-change milestones inherit this same `ready` boundary unless they explicitly define a non-implementation workflow.

## Repository setup and guide-system maintenance

| Task | Prompt |
|---|---|
| Prepare a completely new project | `templates/prompts/new-project.md` |
| Adopt the guide system in a repository using an older or unrelated local guide model | `templates/prompts/adopt-guide-system.md` |
| Update a repository already using the guide system to the latest version | `templates/prompts/update-guide-system.md` |

## Special workflows

Special prompts exist only where the work has materially different authority, scope, or completion semantics.

| Task | Prompt |
|---|---|
| Plan an engineering migration | `templates/prompts/special/plan-engineering-migration.md` |
| Plan documentation synchronization | `templates/prompts/special/plan-documentation-sync.md` |
| Plan release readiness | `templates/prompts/special/plan-release-readiness.md` |
| Perform a documentation synchronization pass | `templates/prompts/special/documentation-sync-pass.md` |
| Adopt historical planning research into curated project-local planning knowledge | `templates/prompts/special/adopt-research.md` |

`adopt-research.md` is a planning/research workflow rather than ordinary implementation. It may be invoked independently or from a guide adoption/update when historical planning knowledge is worth recovering. Research adoption does not need to reconstruct complete history and does not make ordinary implementation depend on research.

Ready milestones produced by special planning still use `templates/prompts/execute-milestone.md` unless the special prompt explicitly defines a non-implementation workflow.

## Version-specific prompts

`templates/prompts/version-specific/` contains historical migration and repair prompts that are relevant only when an exact old guide-system version or historical correction path is required.

Do not select a version-specific prompt for normal adoption or update work. Prefer `adopt-guide-system.md` or `update-guide-system.md`.

## Two-phase milestone rule

Coding milestones follow:

```text
draft/planning -> ready -> implementing -> done
```

Planning owns decisions that materially affect architecture, semantics, compatibility, scope, acceptance, validation, and human-review policy.

Planning also owns the judgment that the milestone can be executed by the configured baseline implementation model without unresolved project-level reasoning and that its implementation volume is execution-tractable.

Planning owns the lossless obligation identities, selective evidence-case identities where material, and initial ledger coverage structure for AI-executed milestones.

Implementation owns concrete files, types, functions, refactorings, test structure, execution work packages, implementation sequence, supporting edits required by the contract, ledger work-package/evidence/status/resume fields, persistent execution progress, validation, and completion audit where those choices remain inside the ready milestone contract.

A material unresolved decision prevents `ready` status. If such a decision is discovered during implementation, the affected work returns to planning.

Execution decomposition does not introduce another durable lifecycle phase.

## Execution-state rule

For AI-executed coding milestones, planning initializes:

```text
.execution/<milestone-id>.md
```

before `ready` with every individually verifiable obligation as a separate pending row and with required validation gates.

Implementation reconciles that seeded registry before production edits, then extends it with work packages, evidence, status, and resume state.

The ledger is operational state only and cannot amend the milestone or referenced authority. It may compress work but must not compress obligations or required evidence cases.

Before mutable ledger cleanup after completion, preserve a compact obligation/evidence-case-to-proof summary in the milestone or its explicitly referenced immutable completion record.

A small milestone may use one work package. Do not skip persistent execution state merely because the milestone appears simple.

Update the ledger after coherent work packages and their relevant validation. On resume or after context compaction, reread the milestone and ledger before continuing.

## Closure rule

Implementation follows:

```text
read milestone, authority, and planning-seeded ledger
-> verify lossless obligation/evidence-case set equality
-> execution decomposition
-> map obligations to work packages
-> implement/validate/update evidence and status by work package
-> freshly reread milestone
-> reconcile obligation/evidence cases <-> ledger <-> repository/evidence
-> completion audit
-> persist compact durable completion evidence
-> continue or terminate
```

The implementation run terminates only as:

- `COMPLETE`;
- `AWAITING HUMAN REVIEW`;
- `BLOCKED`.

`COMPLETE` means the fresh reconciliation and completion audit establish all applicable milestone obligations and completion gates.

`AWAITING HUMAN REVIEW` means all agent-resolvable work is complete and a required human decision remains.

`BLOCKED` means completion requires unavailable external capability or a material planning decision the executor cannot make. Agent-resolvable failures are not blockers.

These execution outcomes do not add new durable milestone lifecycle states.

## Human-review rule

Human review is a completion gate owned by one milestone.

Planning defines review applicability, class, evidence, identity, blocking behavior, and completion command when human judgment is required.

Implementation must not fabricate approval and must stop at a blocking review when human action is unavailable.

Completed review records are historical evidence and are not revalidated because later commits changed the repository.

## Prompt preservation rule

Operational prompt templates must remain complete. Do not replace them with abbreviated summaries unless the abbreviated prompt is intentionally introduced as a separate variant.

When modifying a prompt, preserve the applicable:

- repository inspection rules;
- deliverable boundaries;
- milestone content requirements;
- authority routing;
- baseline-model readiness and execution-tractability rules;
- execution-ledger and resume rules;
- validation and documentation-sync rules;
- chat response requirements;
- quality criteria;
- final reconciliation, completion-audit, and terminal-outcome rules.
