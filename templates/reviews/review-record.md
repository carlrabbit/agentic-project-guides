---
schema: agentic-project-guides.review-record.v2
reviewId: <canonical-review-id>
milestone: <milestone-id>
status: <approved|changes-requested|rejected|waived|superseded>
reviewClass: <review-class>
blocking: <true|false>
reviewer: <reviewer identity>
reviewedRevision: <revision-or-unknown>
sourceMilestone: <repository-relative milestone path>
evidence:
  - <evidence path or durable reference>
evidenceFingerprint: <fingerprint-or-not-recorded>
recordedAt: <timestamp>
---

# Review Decision

<Decision rationale.>

## Conditions

<Conditions or none.>

## Milestone Completion Effect

State whether this decision satisfies the owning milestone's human-review gate.

## Evidence Reviewed

- <evidence path or description>

## Provenance Rule

Revision and evidence fingerprints identify what was reviewed at the time.

They are historical provenance. They do not cause this completed decision to become stale after later repository changes.

## Identity Rule

Always write the canonical `reviewId`, even when the human invoked the command with an ephemeral numeric alias.
