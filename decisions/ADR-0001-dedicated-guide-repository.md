# ADR-0001 — Use a Dedicated Guide Repository

## Status

Accepted.

## Context

Earlier project repositories stored setup and engineering guides under `docs/research/` because no separate home existed for the guide system.

That caused guide documents to appear in operational reading paths for implementation agents.

## Decision

The guide system lives in a dedicated repository.

Product repositories do not copy guide documents as active authority.

## Consequences

- Guide evolution is versioned independently.
- Product repositories contain only localized project truth.
- Planning and documentation-sync agents may use the guide repository.
- Implementation agents use product repository docs only.
