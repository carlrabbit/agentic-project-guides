# Prompt — Prepare a Completely Empty New Project

Our planning task is to create a repository initialization package for a completely empty new project:

- Project name: `{project-name}`
- Broad guide profile(s): `{profiles}`
- Repository role: `{repository-role}`
- Maturity stage: `{maturity-stage}`
- Public/private status: `{public-private-status}`
- Primary stack: `{primary-stack}`
- Concrete runtime/environment/integration constraints: `{project-specialization-constraints}`

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

Profiles describe broad reusable engineering shapes. Do not invent a central-style project type or feature-tag profile for operating system, local/CI execution, integration-first testing, a packaging mechanism, a named external product/service, or one concrete product architecture.

When those details materially affect implementation or validation, record them as project-local engineering/specification/architecture/decision authority.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

Resolve the latest guide-system version from `carlrabbit/agentic-project-guides` before creating files.

## Goal

Create a ZIP that can be unpacked into an empty repository to establish the initial project documentation and planning substrate.

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

Add specs, architecture docs, decisions, public docs, or focused engineering/specialization docs only when required for the selected profiles, project constraints, and maturity stage.

Do not include copied guide documents.

## Validation and specialization

If correctness depends on an external runtime, installed application, service, real database, browser, native subsystem, or other concrete integration target, initialize enough project authority to make its validation contract explicit before implementation depends on it.

Resolve as applicable:

- target;
- execution locus;
- platform/capability requirements;
- provisioning/connection;
- isolation/reset;
- invocation;
- evidence;
- fallback/failure semantics;
- consumer/release relationship.

If the project intentionally uses integration-first testing, record that policy in project engineering authority. Do not create unit-test requirements merely because of an assumed generic test pyramid.

## Planning/implementation separation

There is no direct synchronization between the planning AI and implementation AI.

Create an implementation-ready package. The later implementation agent must be able to unpack the ZIP, open the primary milestone document, read only the authority documents explicitly listed in that milestone, implement the focus areas, run the specified validation against the declared targets/loci, and finish without reconstructing planning context or reading the external guide repository.

Also generate a concise execution prompt in chat for the later implementation agent.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, or copied guide documents.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profiles, role, maturity, execution mode, and material specialization assumptions;
5. a filled execution prompt for the later implementation agent;
6. documentation-sync hints and the `.guide-sync/pending/` files created.
