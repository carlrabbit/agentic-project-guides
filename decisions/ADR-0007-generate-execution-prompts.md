# 0007 — Generate Execution Prompts from Planning Work

## Status

Accepted.

## Decision

Planning prompts must emit a concise execution prompt for the later implementation agent so disconnected agents can hand off without shared chat state.

## Consequences

- The guide system keeps methodology outside product repository truth.
- Planning, execution, documentation synchronization, and migration remain separate task modes.
