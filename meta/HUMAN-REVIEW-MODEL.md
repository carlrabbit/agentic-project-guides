# Human Review Model

## Status

Authoritative for **explicit human acceptance decisions** when a milestone or project requires one. Ordinary implementation/PR review and defect-correction work use the canonical [review prompt](../templates/prompts/review-milestone.md), not this formal-review mechanism.

## Default: lightweight approval

Human review is **not** a universal milestone gate. Use it when a judgment cannot be resolved automatically (for example visual or semantic acceptance) or when project authority expressly requires human approval.

For an occasional required decision, use an existing PR review, issue/commit discussion, or one concise milestone-local decision record. Preserve only what is necessary to identify:

- the owning milestone and decision subject;
- the evidence presented (link, artifact, or brief description);
- the real reviewer's decision and its provenance;
- whether the decision permits completion or requires correction.

A PR approval is adequate when it clearly refers to the required subject and evidence. Do **not** build `.review/` state, a command host, aliases, a review registry, or six scripts just to obtain one approval.

If explicit approval is mandatory and has not occurred, report `AWAITING HUMAN REVIEW`. Implementation agents may prepare evidence and request decisions, but must never approve their own work, fabricate identities, or infer approval from passing tests.

## Review applicability and completion

- **none:** no human decision required.
- **recommended:** helpful but not a completion gate.
- **required:** record an affirmative decision before claiming completion, subject to the project's explicit waiver policy.
- **blocking:** cannot complete until approved or validly waived under the declared contract.

Review requirements must identify the subject, reviewer/authority when material, acceptance expectations, and decision location. A milestone may request review without mandating particular tooling.

A completed review is **historical**: later unrelated commits do not automatically invalidate it. An active milestone whose evidence changes materially before approval must present updated evidence. A future milestone decides whether it needs its own review. Do not impose perpetual project-wide approval or retroactive evidence-fingerprint checks.

## Optional structured repository-local review system

A project with frequent multi-stage reviews, offline decisions, organizational audit requirements, or complex evidence routing **may deliberately adopt** a structured review subsystem. This is not the default and is not implied by the presence of a human-review gate.

When adopted, project engineering authority should specify the actual contract. It may use:

```text
.review/pending/
.review/closed/
.review/records/
artifacts/review/evidence/
artifacts/review/session/aliases.json
```

It may expose `review-list`, `review-show`, `review-request`, `review-record`, `review-reopen`, and `review-check --milestone <id>` through supported launchers. Existing repositories that intentionally adopted this advanced subsystem may retain it without migration-driven removal.

If such commands exist, preserve stable canonical review IDs, explicit milestone ownership, accurate recorded decisions, and a completion check scoped only to the owning milestone. Ephemeral numeric aliases are interactive conveniences, never durable identities. Failed, unavailable, or pending reviews must not be reported as passed. Completed records are immutable historical decisions, not continually revalidated approvals.

The optional review infrastructure must be materially simpler than the work it reviews. Simplify or bypass it when the project no longer needs the additional mechanics.

## Correction boundary

A finding that an implementation is defective does **not** automatically require formal human acceptance, new review records, or additional validation gates. Correct concrete defects with focused verification. Promote a finding into stronger permanent regression coverage only when recurrence or consequence makes that economical. See the canonical [review/correction prompt](../templates/prompts/review-milestone.md).
