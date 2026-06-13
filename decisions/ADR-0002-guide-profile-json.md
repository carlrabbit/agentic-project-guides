# ADR-0002 — Use `.guide-profile.json` for Traceability

## Status

Accepted.

## Context

Product repositories may need traceability to the guide system without copying or referencing guide documents as operational authority.

## Decision

Use an optional `.guide-profile.json` file in product repositories.

The file records guide-system metadata, selected profiles, repository role, maturity stage, and active/inactive documentation layers.

## Consequences

- Traceability remains machine-readable.
- Implementation agents are not asked to read guide documents.
- Documentation-sync and planning agents can determine which guide profile applies.
