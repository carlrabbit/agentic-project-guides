# Prompt — Migrate Repository to Guide System v0.1.0

Our planning task is to create an implementation-ready migration milestone package for migrating this repository from the old repository-local setup/engineering guide model to the external guide-system model.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`
- Guide system version: `0.1.0`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Migration target

Target the v0.1.0 model:

- external guide repository authority;
- `.guide-profile.json` for traceability;
- no copied guide documents in product repositories;
- project docs contain project truth only;
- provider/consumer distinction;
- maturity and repository-role aware profile selection;
- migrations instead of generic upgrades;
- validation tiers;
- no default TBPs or issue templates.

## Repository inspection

Inspect the target repository before writing files. Usually read:

- `README.md`;
- `AGENTS.md`;
- old `docs/research/project-setup-guide-*.md` and `docs/research/engineering-guide-*.md` only to understand legacy state;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- `docs/ENGINEERING.md`;
- `docs/MILESTONES.md`;
- relevant existing milestones and decisions.

## Required output

Create one migration milestone under `docs/milestones/`.

Create or update `.guide-profile.json` when useful.

Create or update target-repository docs only when needed to remove guide leakage or make the migration implementation-ready.

Classify migration work as:

- required;
- conditional;
- deprecated;
- manual-review;
- no-op.

## Deferred documentation hints

For cleanup that should not be part of this migration implementation package, create one or more files under:

```text
.guide-sync/pending/
```

Do not require the implementation agent to read `.guide-sync/`.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, or copied guide documents.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profile, role, maturity, and execution mode;
5. implementation-agent hints;
6. documentation-sync hints and the `.guide-sync/pending/` files created.
