# Milestone — <Title>

## Execution Profile

| Field | Value |
|---|---|
| Lifecycle state | ready |
| Mode | ai-executed-human-reviewed |
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
