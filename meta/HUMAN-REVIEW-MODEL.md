# Human Review Model

## Status

Authoritative for repository-local, milestone-scoped human review workflows.

## Purpose

Human review is used when automated validation cannot determine whether evidence produced during a milestone is acceptable.

Human review is a completion gate owned by a milestone. It is not a perpetual project-wide quality gate.

The governing rule is:

```text
A review evaluates evidence produced for one milestone.
Approval permits that milestone to complete.
After completion, the review record is immutable historical evidence.
Later changes do not invalidate the completed review.
```

## Scope

This model is authoritative for:

- milestone-owned review requests;
- review classes;
- blocking and non-blocking review requirements;
- repository-local review state;
- human decision recording;
- milestone completion checks;
- interactive aliases for human commands;
- historical review records.

This model is not authoritative for:

- continuous project-wide quality approval;
- future milestone acceptance;
- automated validation behavior unrelated to review;
- documentation synchronization;
- release publication by itself.

## Repository layout

```text
.review/
  pending/
  closed/
  records/

artifacts/
  review/
    evidence/
    session/
      aliases.json
```

### `.review/pending/`

Contains review requests for milestones that have not completed.

A pending request must identify exactly one milestone.

### `.review/closed/`

Contains closed or superseded requests when the repository preserves request files separately from decision records.

### `.review/records/`

Contains durable human decisions.

Records are historical evidence of what was reviewed for a milestone and what decision was made.

### `artifacts/review/evidence/`

Contains generated or local review evidence unless the repository intentionally commits selected evidence elsewhere.

### `artifacts/review/session/aliases.json`

Contains the ignored, ephemeral alias map created by `review-list`.

## Milestone ownership

Every review request must identify one milestone.

Example:

```yaml
milestone: M018
reviewId: HR-M018-01
reviewClass: visual
blocking: true
subject: Generated reference-adventure map preview
```

A milestone may own multiple reviews:

```text
HR-M018-01 — visual review
HR-M018-02 — semantic review
HR-M018-03 — migration review
```

A review must not be shared as a completion gate across unrelated milestones.

If a later milestone changes the same subsystem, that later milestone decides whether it requires a new review.

The earlier review is not reopened automatically.

## Review classes

Review classes describe the type of human judgment required.

```text
semantic
visual
ux
creative
security
public-api
release
migration
artifact-quality
```

Review classes do not create ongoing repository-wide obligations.

They help the milestone specify:

- who should review;
- what evidence is required;
- what acceptance criteria apply;
- whether the review blocks completion.

## Applicability

A milestone may classify human review as:

```text
none
recommended
required
blocking
```

### none

No human review is needed.

### recommended

Review is useful, but milestone completion does not depend on it.

### required

A review decision must be recorded before completion. Repository policy decides whether a waiver is permitted.

### blocking

The milestone cannot complete until the review is approved or validly waived according to the milestone's explicit policy.

## Review lifecycle

The active milestone lifecycle is:

```text
pending
approved
changes-requested
rejected
waived
superseded
```

Typical transitions before milestone completion:

```text
pending → approved
pending → changes-requested
changes-requested → approved
pending → rejected
pending → waived
pending → superseded
```

When changes are requested:

1. the implementation agent updates the milestone output;
2. new or updated evidence is produced;
3. the human records another decision for the same active milestone review;
4. the decision history remains available;
5. the milestone completes only when its final required state is acceptable.

## Milestone completion

A milestone completion check validates only the reviews owned by that milestone.

Example:

```sh
./eng/review-check.sh --milestone M018
```

The check verifies:

- all review requests required by M018 exist;
- every blocking M018 review is approved or validly waived;
- no blocking M018 review remains pending or changes-requested;
- required evidence exists at review time according to repository policy;
- decision records are structurally valid;
- canonical IDs and milestone references are consistent.

The check must not:

- reopen completed reviews from earlier milestones;
- compare historical approvals with the current repository state;
- fail because unrelated later commits changed files;
- treat historical review records as ongoing project quality gates.

## Historical records

After a milestone completes, its review records become immutable historical evidence.

A record answers:

```text
Which milestone did this review gate?
What evidence was presented?
Who reviewed it?
What decision was made?
What repository revision and evidence existed at the time?
```

A record does not answer:

```text
Is the current repository still approved?
```

Fields such as repository revision and evidence fingerprint may be recorded for provenance. They are not automatic future invalidation authority.

## No generic staleness

The generic review model does not include an approval-stale state.

Do not invalidate completed approval because:

- HEAD changed;
- unrelated source changed;
- documentation changed;
- another milestone modified the same subsystem later;
- evidence files were cleaned from ignored artifacts after the milestone record was committed, unless repository policy explicitly requires permanent evidence retention.

If a future milestone requires human judgment, create a new review request owned by that milestone.

## Durable identity

Every review has one canonical review ID, for example:

```text
HR-M018-01
review.M018.generated-map-preview
```

Canonical IDs are used in:

- review requests;
- review records;
- milestones;
- automation;
- committed artifacts;
- validation output;
- cross-references.

Canonical IDs must remain stable.

## Ephemeral numeric aliases

Interactive commands may display small aliases:

```text
[1] HR-M018-01  visual    Generated map preview
[2] HR-M018-02  semantic  Workspace manifest
```

Aliases are:

- generated by the latest `review-list` invocation;
- valid only for that list context;
- allowed to change after the next list invocation;
- stored only in ignored runtime artifacts;
- never durable project identity;
- never written into milestones, requests, records, or automation.

A stale alias must fail safely and instruct the user to run `review-list` again.

## Standard command contract

```text
./eng/review-list.sh [--milestone <id>] [filters]
./eng/review-show.sh <review-id-or-alias>
./eng/review-request.sh --milestone <id> ...
./eng/review-record.sh <review-id-or-alias> <decision> ...
./eng/review-reopen.sh <review-id-or-alias> ...
./eng/review-check.sh --milestone <id>
```

PowerShell launchers may expose the same behavior.

### `review-list`

- lists active or historical reviews in deterministic order;
- may filter by milestone;
- displays ephemeral aliases;
- writes the latest alias map atomically;
- never changes durable review identity.

### `review-show`

- accepts canonical ID or current alias;
- displays owning milestone, subject, class, blocking state, evidence, and decision history;
- distinguishes active review state from historical completion;
- does not evaluate ongoing validity against future repository state.

### `review-request`

- requires an owning milestone;
- creates a canonical review ID;
- records class, applicability, subject, evidence expectations, and acceptance criteria;
- does not create approval.

### `review-record`

- accepts canonical ID or current alias;
- records a human decision against the canonical ID;
- records provenance such as revision and evidence identity when useful;
- does not create future staleness obligations;
- closes the pending request when the milestone's review policy considers the decision final.

### `review-reopen`

- is used only while the owning milestone is active, or for explicit correction of an erroneous record;
- must not reopen historical reviews merely because later commits occurred;
- should preserve prior decision history.

### `review-check`

- requires explicit milestone context;
- ignores aliases;
- validates the completion gate for that milestone only;
- does not revalidate completed reviews from earlier milestones.

## Human workflow

```text
1. Run review-list --milestone <id>.
2. Inspect a review with review-show <alias-or-id>.
3. Inspect the evidence named by the request.
4. Record approve, changes-requested, reject, or waive.
5. Run review-check --milestone <id>.
6. Commit durable review records and request movement.
7. Complete the milestone when all its blocking gates pass.
```

## Implementation-agent responsibilities

An implementation agent may:

- create review requests required by the milestone;
- produce and identify evidence;
- update evidence after changes are requested;
- run non-human structural checks;
- report pending review IDs and evidence paths.

An implementation agent must not:

- approve on behalf of a human;
- fabricate a human identity;
- treat missing review as passed;
- reopen historical reviews because repository state changed;
- require a human to repeat a completed milestone review during later milestones unless the later milestone explicitly declares a new review.
