# Prompt — Update Repository to Latest Agentic Project Guide System

Our planning task is to create an implementation-ready migration package for updating a repository from any existing `carlrabbit/agentic-project-guides` version to the latest available guide-system version.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Resolve current and latest guide versions

Read the target repository's `.guide-profile.json` if present to identify the current recorded guide-system version.

Then inspect the guide repository to determine the latest guide-system version.

Read at minimum:

- `README.md`;
- `CHANGELOG.md`;
- `meta/VERSIONING.md`;
- `meta/MIGRATION-MODEL.md`;
- all migration documents newer than the current recorded version;
- relevant decisions;
- `templates/PROMPTS.md`.

State both versions explicitly in the chat response and in the migration milestone.

Do not assume a hard-coded latest version.

## Target use case

Use this prompt when the target repository already has one or more of:

- `.guide-profile.json`;
- `.guide-sync/`;
- localized docs shaped by the external guide system;
- no copied guides as active authority;
- prior migration to `carlrabbit/agentic-project-guides`.

## Repository inspection

Inspect the target repository before writing files.

Usually read:

- `.guide-profile.json`;
- `.guide-sync/pending/` if present;
- `README.md`;
- `AGENTS.md`;
- `docs/ENGINEERING.md`;
- `docs/MILESTONES.md`;
- relevant milestone, spec, decision, public-doc, and engineering docs.

## Required output

Create one migration milestone under `docs/milestones/`.

Update `.guide-profile.json` only if the migration plan includes that change.

Create `.guide-sync/pending/` hints for deferred documentation synchronization.

Do not copy guide documents into the target repository.

Do not perform broad implementation work.

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
