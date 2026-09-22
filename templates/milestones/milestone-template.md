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
| Execution ledger | <.execution/<milestone-id>.md planning-seeded | not-applicable> |
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

Planning must resolve those decisions before implementation. Remaining implementation freedom should consist of local code, test, refactoring, sequencing, work-package, and supporting-work choices that fit the contract.

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

For AI-executed work, planning must make the milestone ledger-ready without pre-planning implementation mechanics.

Assign a stable ID to every individually verifiable acceptance criterion and every other material completion obligation. Examples include `AC-01`, `DOC-01`, `ART-01`, `MIG-01`, and `REV-01`; the exact prefix taxonomy is project-local.

For AI-executed milestones, planning initializes:

```text
.execution/<milestone-id>.md
```

before the milestone becomes `ready`.

The seeded ledger must contain every milestone obligation as a separate pending row and every required validation gate with its target/locus. Planning owns the obligation identity and wording; it leaves work-package mapping, concrete implementation evidence, validation results, status progression, and resume state to implementation.

The execution ledger may compress work. It must not compress obligations.

Planning does not pre-author the executor's detailed task list or work-package decomposition.

The ready milestone should remain one coherent semantic milestone when appropriate. Split it only when separate target states or unresolved planning boundaries justify separate milestones, not merely because the implementation contains many edits.

## Required Authority

- <Relevant spec, architecture, decision, engineering, or specialization document>

Reference authority rather than duplicating its complete body in this milestone.

When a concrete external runtime, service, platform, test environment, or domain-specific integration materially constrains implementation or validation, reference the project-local authority that defines that specialization.

## Acceptance Criteria

- **AC-01** — <Observable or machine-verifiable completion condition.>
- **AC-02** — <Another independently verifiable completion condition.>

Every independently verifiable criterion gets a stable ID. Do not combine several separately provable behaviors into one broad criterion merely to shorten the milestone or ledger.

Acceptance criteria must describe completed outcomes and be specific enough to map individually to implementation and evidence.

When the milestone affects a distributable artifact, include acceptance criteria for the intended consumer boundary where relevant. Internal tests alone do not establish that a packed/installed/published artifact is consumable.

When correctness depends on an external/runtime integration target, include acceptance criteria that establish representative behavior through that target rather than only through substitutes.

## Acceptance Evidence Topology

Use evidence cases only when an acceptance/completion obligation spans materially distinct behaviors that require independent proof.

Examples of materially distinct paths may include:

- scalar versus enum dispatch;
- Root versus Batch state scope;
- source-project versus packed/installed consumer surface;
- sync versus async path;
- provider-specific behavior;
- inherited versus directly declared behavior;
- success versus contractually distinct failure/diagnostic behavior.

Do not mechanically generate a Cartesian product of every dimension. Create a separate evidence case only when the distinction could plausibly hide a different implementation path, state mechanism, compatibility surface, failure mode, or contract behavior.

| ID | Parent obligation | Required evidence case | Why separate evidence is required |
|---|---|---|---|
| EC-01a | AC-01 | <material behavior/path> | <distinct path/state/surface/failure reason> |
| EC-01b | AC-01 | <material behavior/path> | <distinct path/state/surface/failure reason> |

Evidence-case IDs are planning-owned. They describe what must be proven, not how to implement or test it.

If an obligation has no materially distinct evidence cases, the obligation itself remains the evidence unit and no `EC-*` entries are required.

For AI-executed milestones, seed every required evidence case into the execution ledger before `ready`.

## Validation

For each material validation obligation, assign a stable validation-gate ID and specify the applicable depth, target, execution locus, platform/capability requirements, concrete command/check, expected evidence, and the exact evidence units it is intended to prove.

When an obligation has explicit evidence cases, validation maps to those `EC-*` IDs. Otherwise validation may map directly to the obligation ID.

| ID | Depth | Target | Locus/platform | Command/check | Proves | Expected evidence |
|---|---|---|---|---|---|---|
| VAL-01 | <Tier> | <real boundary> | <local/CI/remote/mixed + capability> | <command> | <EC-01a, EC-01b or AC-01> | <evidence> |

A gate may prove several evidence units, but planning must not claim coverage for a case whose behavior the validation scenario does not actually exercise.

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

When human review is a material completion obligation, assign it a stable obligation ID (for example `REV-01`) and seed that row into the execution ledger.

Human review belongs only to this milestone. After milestone completion, the record is historical evidence and is not revalidated by later changes.

## Documentation Policy

Implementation updates directly contradicted authority documents only.

Broad documentation normalization is handled by a separate documentation-sync pass.

When this milestone requires a distinct documentation outcome for completion, assign that outcome a stable obligation ID (for example `DOC-01`) rather than leaving it implicit.

## Completion Expectations

The implementation agent owns milestone closure and will:

```text
read milestone + planning-seeded ledger
-> execution decomposition
-> map seeded obligations to work packages
-> implement/validate work packages
-> attach obligation/evidence-case-specific evidence
-> freshly reread this milestone
-> verify milestone obligation IDs == ledger obligation IDs
-> verify required evidence-case IDs == ledger evidence-case IDs
-> reconcile each obligation/evidence case <-> ledger <-> repository/evidence
-> completion audit
-> write compact durable completion evidence into this milestone
```

Passing tests or completing listed focus areas does not by itself establish milestone completion.

When consumer-surface validation applies, passing internal tests does not establish completion until the current distributable artifact has been exercised through its intended consumer mechanism.

When required integration validation applies, a substitute validation path does not establish completion unless project authority explicitly defines it as equivalent.

## Completion Evidence

This section is populated by implementation only after final reconciliation and the completion audit succeed. It is durable historical evidence, not an amendment to the ready contract.

Preserve a compact trace from each obligation/evidence case to concrete evidence before the mutable execution ledger is removed under repository policy.

| Obligation / evidence case | Evidence | Validation gate / target | Result |
|---|---|---|---|
| AC-01 or EC-01a | <test, receipt, artifact, review, repository state> | <VAL-01 / target> | satisfied |

Include every applicable obligation. Where an obligation has explicit evidence cases, list the cases rather than replacing them with one aggregate row.

Do not copy work-package tasks, resume state, conversational reasoning, or the full execution ledger into this section.

## Escalation Boundary

Implementation owns concrete code/test mechanics, execution decomposition, and supporting edits that fit this contract.

Return the milestone to planning if implementation requires a new decision that materially changes architecture, semantics, compatibility, scope, acceptance criteria, validation policy, or a required project specialization, or if a material planning decision cannot be recovered from durable project authority without repeating project-level reasoning.
