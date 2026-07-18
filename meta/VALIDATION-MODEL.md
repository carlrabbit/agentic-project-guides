# Validation Model

## Status

Authoritative for validation tiers and validation evidence concepts.

## Validation tiers

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema checks, touched-file checks. |
| 1 | Focused validation | Affected project, component, spec-area, or shard validation. |
| 2 | Standard local validation | Normal repository local gate. |
| 3 | PR integration validation | Full CI or workflow integration validation. |
| 4 | Release validation | Package, public API, public docs, samples, and release checks. |
| 5 | Human review validation | Human acceptance of milestone evidence when automation cannot decide. |

## Tier 5 scope

Tier 5 is milestone-scoped.

It is not a perpetual project quality gate.

A Tier 5 review:

- is declared by one milestone;
- evaluates evidence produced for that milestone;
- may block that milestone's completion;
- becomes historical evidence after completion;
- is not revalidated after unrelated future changes.

Later milestones declare their own Tier 5 requirements when appropriate.

## Resumable validation

Long automated validation may use independently executable shards, atomic fingerprinted receipts, and a fast aggregate verifier.

Validation receipts and human review records serve different purposes:

```text
validation receipt
  machine evidence that a bounded automated shard passed for a defined input state

human review record
  historical evidence that a human accepted milestone evidence at completion time
```

Automated receipts may become stale when their validation inputs change.

Completed human review records do not become stale under the generic model.
