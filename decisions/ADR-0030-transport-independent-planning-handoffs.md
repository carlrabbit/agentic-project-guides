# ADR-0030 — Make Planning Handoffs Transport-Independent

## Status

Accepted for guide-system v0.10.0 (draft).

## Context

The ready milestone and referenced project authority already define the durable semantic handoff, with a planning-seeded ledger for AI-executed work. Nevertheless, active planning prompts required downloadable ZIP archives even when a planner had authorized Git repository access. This imposed manual overlay handling, made moves/deletions awkward, and separated the reviewable artifact from its repository history.

## Decision

Treat Git planning branches and repository-relative ZIP overlays as alternate transports for the **same** planning artifacts. Prefer a dedicated Git branch when authorized and available; use ZIP for disconnected delivery. Git handoffs identify an exact planning-baseline commit SHA, not merely a moving branch name. Implementation may continue on the planning branch or start a separate implementation branch from that commit. A planning PR is optional unless project policy requires one.

Transport must not relax the planning/implementation boundary or change the ready milestone, authority, research, ledger, acceptance, validation, or human-review contract. The canonical execution prompt remains unchanged.

## Consequences

- Planners can deliver directly in the target repository and use normal Git diffs, commits, and PR review.
- Disconnected planning remains supported without requiring Git connectivity or write access.
- The implementation baseline is reproducible even when a shared branch advances.
- ZIP application notes handle moves/deletions explicitly rather than posing as authority.
- No repository migration or rewrite of previously ready milestones is needed solely for this change.
