# Milestone Execution Model

## Status

Authoritative for milestone execution modes.

## Purpose

Milestone size and detail should be selected by execution mode, design maturity, validation strength, and review model.

AI-executed milestones may be larger than human-sized work packages when design authority is stable.

## Execution modes

| Mode | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | Human approves plan; AI performs implementation; human reviews result. |
| `ai-executed-broad` | AI performs a larger implementation or migration with strong specs and clear acceptance criteria. |
| `documentation-sync` | Broad documentation normalization pass. |
| `engineering-migration` | Changes command contracts, scripts, CI, or validation infrastructure. |
| `release-readiness` | Prepares public release artifacts, docs, packages, and release validation. |

## Milestone sizing rule

Small milestones are useful when design risk is high.

Larger AI-executed milestones are appropriate when:

- specs are normalized;
- architecture decisions are stable;
- acceptance criteria are explicit;
- validation tiers are defined;
- documentation sync is separated from implementation.

## Required milestone fields

Milestones should declare:

```text
Execution mode
Scope size
Implementation autonomy
Required authority documents
Non-goals
Validation tier
Documentation responsibility
Human review expectations
```
