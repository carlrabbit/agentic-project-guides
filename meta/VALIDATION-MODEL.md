# Validation Model

Validation must be explicit, tiered, and appropriate to the execution mode.

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema checks, touched-file checks. |
| 1 | Focused validation | Affected project/component/spec-area validation. |
| 2 | Standard local validation | Normal repository local gate. |
| 3 | PR integration validation | Full CI/workflow validation. |
| 4 | Release validation | Package, public API, public docs, samples, release checks. |
| 5 | Human review validation | Human acceptance of artifacts, semantics, visual quality, UX, or creative decisions. |

Milestones and execution prompts should state the expected validation tier and concrete commands.
