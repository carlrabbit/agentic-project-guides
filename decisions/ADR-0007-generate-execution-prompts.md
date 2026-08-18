# 0007 — Use a Stable Execution Prompt for Ready Milestones

## Status

Accepted; revised in guide system v0.7.0.

## Context

Disconnected planning and implementation interfaces must not depend on shared chat state. Earlier guidance required each planning task to generate a bespoke execution prompt.

With the v0.7.0 two-phase milestone lifecycle, the durable handoff is the ready milestone plus the project authority it references. Regenerating a per-milestone execution prompt duplicates methodology and can drift from the canonical execution contract.

## Decision

Use `templates/prompts/execute-milestone.md` as the stable execution prompt for ready milestones.

Planning must produce a self-contained ready milestone. A planning interface may emit a short handoff note that identifies the primary milestone path and any transport/application instructions, but it must not be required to regenerate the execution methodology.

The implementation phase must be able to proceed from:

1. the canonical execution prompt;
2. the ready milestone;
3. the localized project authority referenced by the milestone;
4. the live repository.

## Consequences

- the ready milestone is the durable planning-to-implementation handoff;
- execution methodology has one canonical prompt instead of per-milestone copies;
- disconnected Chat/Codex or other interface boundaries remain supported;
- planning conversation history is not implementation authority;
- a concise handoff note remains optional transport/context, not a second implementation contract.
