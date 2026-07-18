# Milestone Execution Model

## Status

Authoritative for milestone execution modes and milestone completion gates.

## Execution modes

| Mode | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | AI performs implementation; human reviews declared milestone evidence. |
| `ai-executed-broad` | AI performs a larger implementation or migration with strong authority and validation. |
| `documentation-sync` | Broad documentation normalization pass. |
| `engineering-migration` | Changes command contracts, scripts, CI, or validation infrastructure. |
| `release-readiness` | Prepares release artifacts, docs, packages, and release validation. |

## Milestone completion

A milestone defines its own completion gates.

Possible gates include:

- focused automated validation;
- standard local validation;
- PR integration validation;
- release validation;
- human review of milestone evidence;
- documentation directly required for implementation correctness.

Human review is not inherited indefinitely by the project.

When a milestone requires human review, it must define:

- review class;
- applicability: recommended, required, or blocking;
- canonical review ID or allocation rule;
- review subject;
- evidence to be produced;
- acceptance criteria;
- human reviewer role when relevant;
- completion behavior;
- waiver policy when applicable.

After the milestone completes, its review records are historical evidence. Future milestones decide independently whether new review is required.
