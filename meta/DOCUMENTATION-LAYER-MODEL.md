# Documentation Layer Model

Documentation layers should be activated by selected profiles, maturity, repository role, and concrete project authority needs.

They are not all mandatory.

Project-local specialization normally uses these ordinary authority layers rather than introducing a separate central-style specialization hierarchy.

## Authority layers

Common project-authority layers:

- `README.md`
- `AGENTS.md`
- `docs/TERMINOLOGY.md`
- `docs/SPECS.md`
- `docs/ARCHITECTURE.md`
- `docs/DECISIONS.md`
- `docs/ENGINEERING.md`
- `docs/MILESTONES.md`
- `docs/PUBLIC-DOCS.md`
- `public-docs/`
- `docs/SCENARIOS.md`
- `docs/ARTIFACTS.md`
- `docs/HUMAN-REVIEW.md`

These documents contain project truth according to their defined authority roles.

## Planning-knowledge layer

Research is an optional non-authoritative planning-knowledge layer:

```text
docs/RESEARCH.md        optional compact discovery/index surface
docs/research/          durable research/evidence artifacts
```

Activate it only when the project has evidence that is materially useful to future planning and costly, unreliable, or wasteful to rediscover.

Research may preserve observations, provenance, experiments, comparisons, uncertainty, and revalidation triggers. It must not become shadow project authority.

Implementation-affecting conclusions must be promoted into the appropriate specification, architecture, decision, engineering, milestone, or other project-authority document before ordinary implementation depends on them.

Planning should load research selectively rather than treating the complete research corpus as required context.

See `meta/RESEARCH-MODEL.md`.

## Default discouraged layers/usages

- `docs/TBPS.md`;
- `docs/tbps/`;
- `.github/ISSUE_TEMPLATE/`;
- copied guide documents under `docs/research/`;
- research files that merely archive planning conversations or duplicate current project authority.
