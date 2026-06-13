# ADR-0005 — Use Migrations Instead of Generic Upgrades

## Status

Accepted.

## Context

Simple instructions such as "upgrade to the latest guide" do not work once repositories have profiles, roles, maturity stages, and selected modules.

## Decision

Guide updates are applied through profile-aware migration documents.

Migration documents classify changes as required, conditional, deprecated, manual-review, or no-op.

## Consequences

- Repository updates become plan-driven.
- Agents can apply focused migration milestones.
- Not every guide change affects every repository.
