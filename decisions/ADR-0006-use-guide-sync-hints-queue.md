# ADR-0006 — Use a Guide Sync Hints Queue

## Status

Accepted in guide system v0.2.0.

## Context

Planning, implementation, and documentation synchronization may be performed by different AI agents without shared chat state. Previously, deferred documentation synchronization hints were written only in chat responses. This made them easy to lose.

## Decision

Target repositories may contain a versioned, non-authoritative coordination queue at:

```text
.guide-sync/pending/
```

Planning and migration packages may add Markdown hint files to this folder when deferred documentation work must survive handoff.

Ordinary implementation agents must ignore `.guide-sync/` unless explicitly assigned guide migration or documentation synchronization work.

Documentation-sync agents must read `.guide-sync/pending/`, resolve or narrow pending hints, and delete each hint only when its completion criteria are satisfied.

## Consequences

- Deferred documentation work becomes traceable in Git.
- Chat-only synchronization hints are no longer lost.
- Product documentation remains clean because sync hints are not authoritative docs.
- Implementation agents are not burdened with broad documentation cleanup.
- Documentation-sync prompts can reference one stable repository location.

## Non-goals

- `.guide-sync/` is not a replacement for specs, engineering docs, public docs, or milestones.
- `.guide-sync/` is not required reading for normal implementation work.
- `.guide-sync/` must not contain implementation instructions.
