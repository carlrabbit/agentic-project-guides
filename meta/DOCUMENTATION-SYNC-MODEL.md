# Documentation Sync Model

## Purpose

This model defines how deferred documentation work is captured, transported, consumed, and cleaned up when planning, implementation, and documentation synchronization are performed by disconnected agents.

## Core rule

Documentation synchronization hints are repository-local coordination metadata, not authoritative project documentation.

Use:

```text
.guide-sync/pending/
```

to store pending hints that must survive beyond the current chat.

## Authority

This document is authoritative for:

- the purpose of `.guide-sync/`;
- how planning agents create sync hints;
- how documentation-sync agents consume sync hints;
- how implementation agents treat sync hints.

This document is not authoritative for:

- project behavior;
- implementation scope;
- public user-facing documentation content;
- release readiness.

## Target repository structure

```text
.guide-profile.json
.guide-sync/
  pending/
    <hint>.md
```

Do not require ordinary implementation agents to read `.guide-sync/`.

## Agent responsibilities

| Agent mode | Responsibility |
|---|---|
| Planning | Create pending sync hints when deferred documentation work must survive handoff. |
| Implementation | Ignore `.guide-sync/` unless explicitly assigned guide migration or documentation sync work. |
| Documentation sync | Read pending hints, apply the required documentation updates, and delete or narrow each hint. |
| Release readiness | May read pending hints and either resolve release-relevant ones or explicitly defer non-release hints. |

## Hint lifecycle

1. Planning or migration task identifies deferred documentation work.
2. The planning package includes one or more files under `.guide-sync/pending/`.
3. The implementation agent ignores these files during ordinary implementation.
4. A documentation-sync task reads `.guide-sync/pending/`.
5. Each hint is either:
   - resolved and deleted; or
   - updated with narrower remaining work and left pending.

## Cleanup rule

Delete a pending hint only when its completion criteria are satisfied.

If the sync pass cannot complete a hint, update the hint with:

- current status;
- completed parts;
- remaining blockers;
- next recommended sync action.

## Forbidden uses

Do not use `.guide-sync/` for:

- implementation instructions;
- permanent requirements;
- architecture authority;
- behavioral specifications;
- public documentation source;
- release notes;
- personal notes.

Move durable project truth into `docs/`, `public-docs/`, or the relevant repository authority document.
