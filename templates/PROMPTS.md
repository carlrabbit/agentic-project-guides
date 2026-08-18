# Prompt Templates

## Purpose

This index is the entry point for guide-system prompt selection.

Prompt templates are guide-system methodology. They live in the guide repository, not in product repositories.

## Normal development workflow

For ordinary milestone-driven development, use only these two prompts:

1. `templates/prompts/plan-milestone.md` during planning;
2. `templates/prompts/execute-milestone.md` after the milestone is `ready`.

Planning resolves material architectural, semantic, compatibility, scope, acceptance, and validation uncertainty. Implementation reads the ready milestone and localized project authority, inspects the live repository, derives concrete implementation mechanics, implements, validates, performs a completion audit, and drives the milestone to a valid terminal execution outcome.

Execution profile is selected during planning. Do not choose a different planning prompt merely because implementation will be human-led, AI-assisted, or AI-executed.

Implementation does not require the planning conversation and escalates material unresolved decisions back to planning.

Passing tests or successful implementation does not by itself complete a milestone. The executor owns milestone closure and must continue resolving every agent-resolvable milestone obligation before terminating.

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

Implementation owns concrete files, types, functions, refactorings, test structure, implementation sequence, supporting edits required by the contract, validation, and completion audit where those choices remain inside the ready milestone contract.

A material unresolved decision prevents `ready` status. If such a decision is discovered during implementation, the affected work returns to planning.

## Closure rule

Implementation follows:

```text
implement -> validate -> completion audit -> continue or terminate
```

The implementation run terminates only as:

- `COMPLETE`;
- `AWAITING HUMAN REVIEW`;
- `BLOCKED`.

`COMPLETE` means all applicable milestone obligations and completion gates are satisfied.

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
- validation and documentation-sync rules;
- chat response requirements;
- quality criteria;
- completion-audit and terminal-outcome rules.
