# Human Review Model

## Purpose

Define repository-local human review as an explicit, evidenced, and executable validation workflow.

## Repository structure

```text
.review/
  pending/
  records/
  evidence/
```

Use `artifacts/review/` for generated or large evidence that should not be committed.

## Review applicability

| Level | Meaning |
|---|---|
| `none` | Automated validation is sufficient. |
| `recommended` | Human review adds confidence but does not block completion. |
| `required` | Review must occur before the milestone is complete. |
| `blocking` | Merge, release, publication, or artifact acceptance must fail while unresolved. |

## Review classes

- semantic;
- visual;
- UX;
- creative;
- security;
- public API;
- release;
- migration;
- artifact quality.

## Review states

```text
pending
approved
changes-requested
rejected
waived
superseded
```

## Required record fields

- review ID;
- subject;
- review class;
- source milestone;
- reviewer role;
- status;
- evidence references;
- decision and conditions;
- reviewed revision or fingerprint;
- re-review triggers.

## Re-review triggers

Approval becomes stale when relevant source, generated output, acceptance criteria, evidence, or review fingerprints change.

## Engineering command contract

Repositories that activate human review should expose:

```text
./eng/review-list.sh
./eng/review-request.sh
./eng/review-record.sh
./eng/review-check.sh
```

PowerShell launchers may be added for supported Windows environments.

`review-check` is the Tier 5 gate. It must fail when required or blocking reviews are unresolved, stale, malformed, superseded, or missing required evidence.
