# Milestone — <Title>

## Execution Profile

| Field | Value |
|---|---|
| Lifecycle state | ready |
| Mode | ai-executed-human-reviewed |
| Baseline implementation model | <project baseline; default GPT-5.6 Luna> |
| Baseline executor readiness | confirmed |
| Decision preservation | confirmed |
| Execution tractability | confirmed |
| Scope size | medium-large |
| Implementation autonomy | high |
| Documentation sync | deferred |
| Focused validation | <Tier 1 command/check or not-applicable> |
| Repository validation | <Tier 2 command/check or not-applicable> |
| Integration validation | <Tier 3 target + command/check or not-applicable> |
| Validation locus/platform | <local|CI|remote|mixed; platform/capability requirements> |
| Consumer/release validation | <Tier 4 mechanism or not-applicable> |
| Human review | <none|recommended|required|blocking> |

## Goal

<Why this change exists and the resulting capability.>

## Target State

<What must be true when the milestone is complete.>

## Scope

<Scope>

## Non-goals

<Nearby work deliberately excluded.>

## Decisions and Constraints

- <Resolved architectural, semantic, compatibility, ownership, integration, or scope decision.>
- <Negative requirement or forbidden alternative when needed to prevent a plausible incorrect implementation.>
- <Invariant or implementation constraint.>

Preserve resolved material decisions with enough precision that implementation does not have to rediscover or reinterpret them.

Do not prescribe concrete implementation mechanics here unless they are part of the required project contract.

## Baseline Executor Readiness

This milestone is `ready` only when the project's baseline implementation model can execute it without making a new material decision about architecture, semantics, compatibility, scope, acceptance criteria, or validation policy.

Planning must resolve those decisions before implementation. Remaining implementation freedom should consist of local code, test, refactoring, sequencing, execution-decomposition, and supporting-work choices that fit the contract.

Do not compensate for incomplete planning by requiring a stronger implementation-model tier or by turning the milestone into a line-by-line implementation script.

If material evidence must be gathered before the final implementation contract can be decided, plan a focused diagnostic milestone first and return the resulting evidence to planning.

Large coherent work is allowed when the contract is settled and execution is tractable for the baseline model.

## Decision Preservation

`ready` requires both decision completeness and decision preservation.

Planning may compress analysis, but it must not semantically weaken a resolved material decision.

Project-wide decisions belong in the appropriate referenced project authority. Milestone-specific decisions belong here. Preserve decision-enabling rationale or negative requirements when their omission could cause the executor to misapply, reinterpret, or incorrectly generalize a settled decision.

Before `ready`, verify:

> If the planning conversation and planning model disappeared now, could the baseline executor recover every material decision already made during planning from this milestone and referenced project authority without repeating project-level reasoning?

If not, this milestone is not ready.

Do not preserve speculative implementation suggestions merely because they appeared during planning. Preserve them only when changing them would alter the resolved project contract.

## Execution Tractability

For large or long-running AI execution, the milestone obligations must be explicit enough that implementation can derive bounded coherent work packages and map them to evidence without reopening planning.

The implementation agent creates and maintains:

```text
.execution/<milestone-id>.md
```

as operational progress state. Planning does not pre-author that ledger or the executor's detailed task list.

The ready milestone should remain one coherent semantic milestone when appropriate. Split it only when separate target states or unresolved planning boundaries justify separate milestones, not merely because the implementation contains many edits.

## Required Authority

- <Relevant spec, architecture, decision, engineering, or specialization document>

Reference authority rather than duplicating its complete body in this milestone.

When a concrete external runtime, service, platform, test environment, or domain-specific integration materially constrains implementation or validation, reference the project-local authority that defines that specialization.

## Acceptance Criteria

- <Observable or machine-verifiable completion condition.>

Acceptance criteria must describe completed outcomes and be specific enough to map to implementation work and evidence.

When the milestone affects a distributable artifact, include acceptance criteria for the intended consumer boundary where relevant. Internal tests alone do not establish that a packed/installed/published artifact is consumable.

When correctness depends on an external/runtime integration target, include acceptance criteria that establish representative behavior through that target rather than only through substitutes.

## Validation

For each material validation obligation, specify the applicable depth, target, execution locus, platform/capability requirements, concrete command/check, and expected evidence.

Do not assume that Tier 3 integration validation runs in CI. Local Windows, local Linux, a remote service, CI, or a mixed topology are all valid when declared by project authority.

If an integration target requires technology-specific provisioning, isolation/reset, identity, invocation, or evidence rules, reference the project-local specialization rather than restating the external guide system.

If the repository produces a distributable artifact affected by this milestone, include at least one representative validation path that consumes the artifact through its intended mechanism.

Examples:

- NuGet library: consume the current packed package from an isolated test consumer;
- `dotnet tool`: install the current packed tool through `dotnet tool` into an isolated tool path or local manifest and invoke the installed command/shim;
- standalone executable: invoke the current published/package artifact rather than only the project/build output.

The artifact-level path must exercise the artifact produced by the current build and avoid accidental reliance on globally installed or stale artifacts.

## Human Review

Applicability:

Review class:

Canonical review ID:

Review subject:

Required evidence:

Acceptance criteria:

Reviewer role:

Waiver policy:

Milestone completion command:

```text
./eng/review-check.sh --milestone <milestone-id>
```

Human review belongs only to this milestone. After milestone completion, the record is historical evidence and is not revalidated by later changes.

## Documentation Policy

Implementation updates directly contradicted authority documents only.

Broad documentation normalization is handled by a separate documentation-sync pass.

## Completion Expectations

The implementation agent owns milestone closure and will:

```text
execution decomposition
-> persistent execution ledger
-> implement/validate work packages
-> freshly reread this milestone
-> reconcile milestone <-> ledger <-> repository/evidence
-> completion audit
```

Passing tests or completing listed focus areas does not by itself establish milestone completion.

When consumer-surface validation applies, passing internal tests does not establish completion until the current distributable artifact has been exercised through its intended consumer mechanism.

When required integration validation applies, a substitute validation path does not establish completion unless project authority explicitly defines it as equivalent.

## Escalation Boundary

Implementation owns concrete code/test mechanics, execution decomposition, and supporting edits that fit this contract.

Return the milestone to planning if implementation requires a new decision that materially changes architecture, semantics, compatibility, scope, acceptance criteria, validation policy, or a required project specialization, or if a material planning decision cannot be recovered from durable project authority without repeating project-level reasoning.
