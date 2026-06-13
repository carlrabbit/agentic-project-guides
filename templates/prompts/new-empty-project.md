# Prompt — Prepare a Completely Empty New Project

Our planning task is to create a repository initialization package for a completely empty new project:

- Project name: `{project-name}`
- Project type/profile: `{project-type-or-profile}`
- Repository role: `{repository-role}`
- Maturity stage: `{maturity-stage}`
- Public/private status: `{public-private-status}`
- Primary stack: `{primary-stack}`

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

## Goal

Create a ZIP that can be unpacked into an empty repository to establish the initial project documentation and planning substrate.

## Required output

Include only repository-initialization files needed for the selected profile and maturity stage.

Usually include:

```text
README.md
AGENTS.md
.guide-profile.json
.guide-sync/pending/.gitkeep
docs/TERMINOLOGY.md
docs/SPECS.md
docs/ENGINEERING.md
docs/MILESTONES.md
docs/milestones/M0001-initialization.md
```

Add specs, architecture docs, decisions, public docs, or engineering docs only when required for the selected project type and maturity stage.

Do not include copied guide documents.

Do not create TBPs or issue templates unless the selected project profile explicitly requires them.

## Milestone requirements

The initial milestone must define:

- first implementation goal;
- repository role and maturity;
- execution mode;
- focus areas sized for AI execution where appropriate;
- required authority documents;
- validation tiers;
- direct documentation impact;
- deferred sync hints under `.guide-sync/pending/` where needed.

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
