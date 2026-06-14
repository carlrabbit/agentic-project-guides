# Milestone Execution Model

Milestone size and detail should be selected by execution mode, design maturity, validation strength, and review model.

| Mode | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | Human approves plan; AI performs implementation; human reviews result. |
| `ai-executed-broad` | AI performs a larger implementation or migration with strong specs and clear acceptance criteria. |
| `documentation-sync` | Broad documentation normalization pass. |
| `engineering-migration` | Changes command contracts, scripts, CI, or validation infrastructure. |
| `release-readiness` | Prepares public release artifacts, docs, packages, and release validation. |

Planning prompts generate milestones. Execution prompts tell the later implementation agent how to consume the milestone without re-planning.
