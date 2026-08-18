# Milestone — <Title>

## Execution Profile

| Field | Value |
|---|---|
| Lifecycle state | ready |
| Mode | ai-executed-human-reviewed |
| Baseline implementation model | <project baseline; default GPT-5.6 Luna> |
| Baseline executor readiness | confirmed |
| Scope size | medium-large |
| Implementation autonomy | high |
| Documentation sync | deferred |
| Local validation | Tier 1 focused validation |
| Integration validation | Tier 3 PR workflows |
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

- <Resolved architectural, semantic, compatibility, or scope decision.>
- <Invariant or implementation constraint.>

Do not prescribe concrete implementation mechanics here unless they are part of the required project contract.

## Baseline Executor Readiness

This milestone is `ready` only when the project's baseline implementation model can execute it without making a new material decision about architecture, semantics, compatibility, scope, acceptance criteria, or validation policy.

Planning must resolve those decisions before implementation. Remaining implementation freedom should consist of local code, test, refactoring, sequencing, and supporting-work choices that fit the contract.

Do not compensate for incomplete planning by requiring a stronger implementation-model tier or by turning the milestone into a line-by-line implementation script.

If material evidence must be gathered before the final implementation contract can be decided, plan a focused diagnostic milestone first and return the resulting evidence to planning.

Large coherent work is allowed when the contract is settled and execution or validation can be bounded or resumed safely.

## Required Authority

- <Relevant spec, architecture, decision, or engineering document>

## Acceptance Criteria

- <Observable or machine-verifiable completion condition.>

## Validation

- <Concrete command or completion check.>

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

## Escalation Boundary

Implementation owns concrete code and test mechanics that fit this contract.

Return the milestone to planning if implementation requires a new decision that materially changes architecture, semantics, compatibility, scope, acceptance criteria, or validation policy.
