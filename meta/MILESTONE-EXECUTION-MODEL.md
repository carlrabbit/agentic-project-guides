# Milestone Execution Model

Milestone size and detail are selected by execution mode, design maturity, validation strength, runtime constraints, and review model.

| Mode | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | AI implements; human reviews the result. |
| `ai-executed-broad` | AI performs a larger implementation with stable authority and strong validation. |
| `documentation-sync` | Broad documentation normalization pass. |
| `engineering-migration` | Command, validation, CI, or repository engineering changes. |
| `release-readiness` | Release artifacts, public docs, packages, and release gates. |

Milestones should declare:

- execution mode;
- scope size and autonomy;
- authority documents;
- direct versus deferred documentation impact;
- validation tier;
- validation execution mode;
- human review applicability and evidence;
- runtime constraints and resumable suite commands when applicable.
