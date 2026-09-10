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

Target repository documentation must contain project truth only, plus optional non-authoritative planning research when durable evidence genuinely warrants retention.

Profiles describe broad reusable engineering shapes. Do not invent a central-style project type or feature-tag profile for operating system, local/CI execution, integration-first testing, a packaging mechanism, a named external product/service, or one concrete product architecture.

When those details materially affect implementation or validation, record them as project-local engineering/specification/architecture/decision authority.

## Profile composition and applicability

A project may combine a small number of profiles when multiple broad engineering shapes genuinely apply.

For every selected profile, determine whether it applies:

- repository-wide;
- to one or more durable project-defined components;
- to one or more durable project-defined surfaces.

Profiles compose additively. Do not assign primary/secondary precedence and do not rely on profile ordering.

If two applicable profiles impose materially incompatible expectations, resolve the conflict into project-local authority before producing an implementation-ready milestone.

When `.guide-profile.json` is created for guide-system 0.8 or later, use schema version 2 and record semantic `repository`, `component`, or `surface` scopes for each applied profile.

Component/surface IDs are project-defined semantic identifiers. Their meaning must be established by normal project authority; do not use path globs in `.guide-profile.json` as the architecture definition.

If the repository is homogeneous, repository-wide scopes are sufficient. Do not invent component/surface IDs without a real planning need.

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

Add specs, architecture docs, decisions, public docs, or focused engineering/specialization docs only when required for the selected profiles, profile scopes, project constraints, and maturity stage.

Do not include copied guide documents.

## Research initialization

Do not create `docs/RESEARCH.md`, `docs/research/`, placeholder research files, or copied research templates merely because the guide system defines a research model.

During project initialization, use `meta/RESEARCH-MODEL.md` when bootstrap planning itself requires non-trivial investigation.

Persist research only when the evidence would materially help future planning and would be expensive, unreliable, or wasteful to rediscover. Typical bootstrap examples may include external runtime feasibility, compatibility probes, or evidence behind an architectural choice.

If research produces a conclusion required by the initialization milestone or later implementation, promote that conclusion into normal project authority before handoff. The implementation agent must not need research to reconstruct the operative rule.

Create a compact `docs/RESEARCH.md` index only when enough durable research exists to make discovery useful. Do not create an empty index as scaffolding.

This prompt intentionally does not prescribe a larger research bootstrap policy beyond these invariants; project creation should remain minimal unless real planning knowledge exists.

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

Create an implementation-ready package. The later implementation agent must be able to unpack the ZIP, open the primary milestone document, read only the authority documents explicitly listed in that milestone, implement the focus areas, run the specified validation against the declared targets/loci, and finish without reconstructing planning context, reading the external guide repository, or depending on non-authoritative research for project rules.

Also generate a concise execution prompt in chat for the later implementation agent.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, copied guide documents, or research scaffolding without durable evidence.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profiles and applicability scopes, role, maturity, execution mode, and material specialization assumptions;
5. durable research created during initialization, if any, and which conclusions were promoted into project authority;
6. a filled execution prompt for the later implementation agent;
7. documentation-sync hints and the `.guide-sync/pending/` files created.
