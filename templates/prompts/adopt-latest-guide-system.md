# Prompt — Adopt Latest Agentic Project Guide System

Our planning task is to create an implementation-ready migration package for adopting the latest available `carlrabbit/agentic-project-guides` model in a repository that currently uses any older local setup/engineering guide model.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Resolve latest guide version

Before creating files, inspect the guide repository and determine the latest guide-system version.

Read at minimum:

- `README.md`;
- `CHANGELOG.md`;
- `meta/VERSIONING.md`;
- `meta/MIGRATION-MODEL.md`;
- `decisions/`;
- `migrations/`;
- `templates/PROMPTS.md`.

State the resolved latest version in the chat response and in the migration milestone.

Do not assume a hard-coded latest version.

## Target use case

Use this prompt when the target repository has one or more of:

- copied setup/engineering guides under `docs/research/`;
- old AGENTS required-reading rules;
- TBPs, guardrails, workflows, or issue templates from an older default model;
- no `.guide-profile.json`;
- no `.guide-sync/`;
- guide documents treated as repository-local authority.

## Repository inspection

Inspect the target repository before writing files.

Usually read:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- old `docs/research/project-setup-guide-*.md` and `docs/research/engineering-guide-*.md` only to understand legacy state;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- `docs/ENGINEERING.md`;
- `docs/MILESTONES.md`;
- relevant existing milestones and decisions.

Treat old copied guides as legacy/non-authoritative unless explicitly marked otherwise.

## Required output

Create one migration milestone under `docs/milestones/`.

Create or update `.guide-profile.json` when useful.

Create or update `.guide-sync/pending/` hints for deferred documentation cleanup.

Update target-repository docs only when needed to remove guide leakage or make the migration implementation-ready.

Do not copy external guide documents into the target repository.

## Migration classification

Classify migration work as:

- required;
- conditional;
- deprecated;
- manual-review;
- no-op.

## Planning/implementation separation

There is no direct synchronization between the planning AI and the implementation AI.

Create an implementation-ready package. The later implementation agent must be able to unpack the ZIP, open the primary milestone document, read only the authority documents explicitly listed in that milestone, implement the focus areas, run the specified validation tiers, and finish without reconstructing planning context or reading the external guide repository.

Also generate a concise execution prompt in chat for the later implementation agent.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, or copied guide documents.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profile, role, maturity, and execution mode;
5. a filled execution prompt for the later implementation agent;
6. documentation-sync hints and the `.guide-sync/pending/` files created.
