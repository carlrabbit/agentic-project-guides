# Prompt — Migrate Guide-System Usage from v0.1.0 to v0.2.0

Our planning task is to create an implementation-ready migration milestone package for adopting guide system v0.2.0 in a repository that already uses or is being migrated to v0.1.0.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`
- Guide system version: `0.2.0`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Migration target

Target the v0.2.0 additions:

- prompt template library in the guide repository;
- `.guide-sync/pending/` as a repository-local deferred documentation synchronization queue;
- `meta/DOCUMENTATION-SYNC-MODEL.md` as guide-system authority;
- ADR-0006 guide sync hints queue;
- documentation-sync pass prompt that consumes and cleans up `.guide-sync/pending/`;
- ordinary implementation agents ignore `.guide-profile.json` and `.guide-sync/`.

## Repository inspection

Read the minimum target-repository files needed:

- `.guide-profile.json` if present;
- `AGENTS.md`;
- `docs/ENGINEERING.md`;
- `docs/MILESTONES.md`;
- active milestone docs if migration affects them;
- existing `.guide-sync/pending/` files if present.

## Required output

Create one migration milestone under `docs/milestones/`.

Create `.guide-sync/pending/.gitkeep` only if the repository should adopt the queue immediately and no pending hint exists.

Update `AGENTS.md` only if it does not already tell ordinary implementation agents to ignore `.guide-profile.json` and `.guide-sync/`.

Create sync-hint files under `.guide-sync/pending/` for deferred documentation work that should survive handoff.

Do not copy prompt templates from the guide repository into the target repository.

## Migration classification

Classify all changes as:

- required;
- conditional;
- deprecated;
- manual-review;
- no-op.

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
