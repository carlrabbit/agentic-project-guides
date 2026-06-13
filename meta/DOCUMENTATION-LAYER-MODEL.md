# Documentation Layer Model

## Status

Authoritative for documentation layer selection.

## Purpose

Documentation layers should be activated by project type, maturity, and repository role.

They are not all mandatory.

## Common layers

| Layer | Purpose |
|---|---|
| `README.md` | First-contact user/contributor entry. |
| `AGENTS.md` | Local operational routing for implementation agents. |
| `docs/TERMINOLOGY.md` | Canonical vocabulary. |
| `docs/SPECS.md` | Behavioral truth and invariants. |
| `docs/ARCHITECTURE.md` | Structural system design. |
| `docs/DECISIONS.md` | Durable rationale. |
| `docs/ENGINEERING.md` | Local command contract, validation, and tooling. |
| `docs/MILESTONES.md` | Planned implementation phases. |
| `docs/PUBLIC-DOCS.md` | Public documentation source and sync contract, when public docs are active. |
| `public-docs/` | User-facing documentation source, when active. |
| `docs/SCENARIOS.md` | Scenario catalog, when scenario validation is active. |
| `docs/ARTIFACTS.md` | Artifact/report contract, when artifact evidence is active. |
| `docs/HUMAN-REVIEW.md` | Human review gates, when automation cannot decide correctness alone. |

## Default discouraged layers

The following are not default layers:

- `docs/TBPS.md`;
- `docs/tbps/`;
- `.github/ISSUE_TEMPLATE/`;
- copied guide documents under `docs/research/`.

They may be used only when explicitly activated by a profile.
