# Migration — Guide System v0.1.0 to v0.2.0

## Purpose

Introduce the prompt template library and the `.guide-sync/` deferred documentation synchronization queue.

## Applies to

Repositories or guide-system users that already adopted v0.1.0 concepts:

- external guide repository;
- `.guide-profile.json` traceability;
- no copied guides in product repositories;
- provider/consumer role separation;
- migration over generic upgrade;
- no default TBPs or issue templates.

## Required changes in the guide repository

- Add `templates/PROMPTS.md`.
- Add `templates/prompts/` with standard prompts.
- Add `meta/DOCUMENTATION-SYNC-MODEL.md`.
- Add `templates/guide-sync-hint.md`.
- Add ADR-0006.
- Add this migration document.

## Conditional changes in product repositories

Apply only when the repository needs disconnected planning, implementation, and documentation-sync handoff.

- Add `.guide-sync/pending/.gitkeep` or create the folder when the first hint is added.
- Update `AGENTS.md` to tell ordinary implementation agents to ignore:
  - `.guide-profile.json`;
  - `.guide-sync/`.
- Add pending hint files under `.guide-sync/pending/` when planning packages defer documentation work.

## Deprecated

- Chat-only documentation synchronization hints for work that must survive handoff.
- Broad documentation-sync instructions inside ordinary implementation milestones.

## Manual review

- Verify that `.guide-sync/` is treated as coordination metadata, not project authority.
- Verify that implementation milestones do not require ordinary implementation agents to read `.guide-sync/`.
- Verify that documentation-sync prompts consume and clean up pending hints.

## No-op

No changes are required for repositories that do not use disconnected agents or do not need deferred documentation synchronization tracking.

## Validation

- Prompt files exist and are discoverable through `templates/PROMPTS.md`.
- `.guide-sync/` rules are documented in `meta/DOCUMENTATION-SYNC-MODEL.md`.
- Product-repository `AGENTS.md` ignores `.guide-sync/` for ordinary implementation when the queue is adopted.
