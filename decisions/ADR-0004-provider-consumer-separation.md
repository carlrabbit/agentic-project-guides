# ADR-0004 — Separate Provider and Consumer Responsibilities

## Status

Accepted.

## Context

Artifact-first systems often describe both how a capability is implemented and how it is later used.

Without a role distinction, provider repositories can accidentally inherit consumer validation obligations.

## Decision

Repository role is a first-class axis.

Capability providers validate the capability implementation.
Capability consumers use the capability to validate authored products.
Mixed/dogfood repositories may do both with bounded dogfood scope.

## Consequences

- A scenario-runner repository tests the runner.
- A game repository uses scenarios to test the game.
- Dogfood projects stay representative rather than becoming uncontrolled product scope.
