# Agent Instructions

## Repository entrypoint

This file routes agents to repository authority; it is not a milestone contract or a copy of the external guide.

For a ready implementation milestone, start with:

1. the primary milestone document;
2. its planning-seeded `.execution/<milestone-id>.md` ledger, when applicable;
3. the project authority explicitly referenced by the milestone;
4. relevant source, tests, and other repository context needed for the work.

For other tasks, follow the assigned task and relevant repository authority. Do not assume every invocation is milestone implementation.

Use documented repository engineering commands (`eng/` when applicable). The milestone and project engineering authority define validation requirements; do not invent command contracts.

## Authority boundaries

- The ready milestone and referenced project authority define implementation scope and obligations. The execution ledger records progress and evidence; it does not override the milestone.
- Planning metadata (`.guide-profile.json`, `.guide/profiles/`, `docs/PROJECT-GUIDANCE.md`, `.guide-sync/`) is not routine implementation authority. Consult it only when the assigned work requires it.
- `docs/research/` is non-authoritative evidence, not a substitute for project decisions. Read it when an assigned investigation/evidence obligation calls for it.
- `.review/` is relevant when the active work requires milestone-scoped review, migration, or synchronization.
- Do not depend on the external guide repository or planning conversation to reconstruct the implementation contract.

## Execution boundaries

Preserve existing project work and remain within the assigned scope. Do not install persistent host software or change shared CI/CD infrastructure merely to make validation pass; follow the authorization in the milestone and project authority. Escalate material unresolved decisions to planning rather than silently changing project policy. Keep detailed test cadence, evidence-reuse mechanics, and simulation execution rules in the milestone or project engineering authority, not this entrypoint.
