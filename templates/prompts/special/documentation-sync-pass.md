# Prompt — Documentation Synchronization Pass

Our task is to perform a documentation synchronization pass for the target repository.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Goal

Synchronize repository documentation using the target repository's project truth and the deferred hints under:

```text
.guide-sync/pending/
```

This is a documentation task, not an implementation task.

## Required inputs

Inspect:

- `.guide-profile.json` if present;
- `.guide-sync/pending/`;
- `README.md`;
- `AGENTS.md`;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- relevant `docs/specs/*`;
- `docs/ENGINEERING.md`;
- `docs/MILESTONES.md`;
- relevant milestones, decisions, architecture docs, public docs, and engineering docs.

Do not treat old copied guides under `docs/research/` as authoritative unless the repository explicitly says otherwise.

## Work rules

- Resolve each pending sync hint whose completion criteria can be satisfied.
- Delete resolved hint files from `.guide-sync/pending/`.
- If a hint cannot be completed, update it with current status, completed parts, remaining blockers, and next recommended action.
- Keep durable project truth in `docs/`, `public-docs/`, `README.md`, `AGENTS.md`, and relevant project docs.
- Do not copy external guide documents into the repository.
- Do not add TBPs or issue templates unless explicitly requested.
- Do not perform implementation source changes unless explicitly required for documentation metadata.

## Deliverable

Create a downloadable ZIP archive containing only new, replacement, or deleted-file marker notes as appropriate for the documentation sync patch. Preserve repository-relative paths.

In chat, report:

1. included file list;
2. deleted or resolved `.guide-sync/pending/` hints;
3. pending hints that remain and why;
4. documentation areas synchronized;
5. validation recommendations.
