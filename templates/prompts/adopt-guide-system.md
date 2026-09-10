# Prompt — Adopt Latest Agentic Project Guide System

Our planning task is to create an implementation-ready migration package for adopting the latest available `carlrabbit/agentic-project-guides` model in a repository that currently uses any older local setup/engineering guide model.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth and concrete project specialization only, plus optional non-authoritative planning research when durable evidence genuinely warrants retention.

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
- `meta/PROFILE-MODEL.md`;
- `meta/SPECIALIZATION-MODEL.md` when present;
- `meta/RESEARCH-MODEL.md` when present;
- `meta/VALIDATION-MODEL.md`;
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
- guide documents treated as repository-local authority;
- old central project-type references;
- validation rules that equate integration depth with PR/CI execution;
- mixed repository shapes whose profile applicability is currently implicit;
- research/notes that may contain useful planning evidence or de-facto implementation rules;
- surviving historical planning chats, documents, experiments, or other evidence that may be worth adopting as durable planning knowledge.

## Repository inspection

Inspect the target repository before writing files.

Usually read:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- old `docs/research/project-setup-guide-*.md` and `docs/research/engineering-guide-*.md` only to understand legacy state;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- `docs/ENGINEERING.md` and focused engineering/specialization docs;
- `docs/ARCHITECTURE.md` when component/surface boundaries matter;
- `docs/MILESTONES.md`;
- relevant existing milestones and decisions.

If `docs/RESEARCH.md` exists, inspect it as a non-authoritative discovery surface and open only research subjects relevant to the migration decisions being made.

Treat genuine project research as non-authoritative planning knowledge. Treat old copied guides as legacy/non-authoritative guide leakage; do not reclassify them as project research merely because they are stored under `docs/research/`.

## Research-adoption decision

When the target guide version defines a research model, explicitly evaluate whether historical planning knowledge should be adopted.

Available source material may include repository-local notes/research and any previous chats, uploaded documents, experiments, prototypes, issue/PR history, or external references actually available to the planning task.

Choose one research-adoption mode for the current adoption scope:

```text
none
selective
reconstructive
```

Use `meta/RESEARCH-MODEL.md` as the authority for the decision surface. Consider evidence availability/quality, rediscovery cost, future planning value, project maturity and expected change, importance of unusual/fragile constraints, revalidation cost, and how much current project authority already preserves.

Do not map maturity mechanically to a mode.

`none` is valid. Historical material may be unavailable or not worth curating. Do not fabricate missing evidence and do not block guide adoption merely because planning history cannot be reconstructed.

`selective` recovers only bounded high-value findings/evidence.

`reconstructive` deliberately establishes a broader useful planning-knowledge baseline from surviving evidence; it is still curated research rather than conversation archival.

Historical chats/files are source material. Do not copy them wholesale into `docs/research/`. Extract durable evidence/findings, preserve provenance/uncertainty, revalidate where material, and promote operative project rules into normal project authority.

A bounded selective adoption may be included in this workflow. If reconstructive adoption would materially expand or delay guide adoption, prefer `templates/prompts/special/adopt-research.md` as a separate planning/research workflow. Guide adoption may complete independently unless a recovered conclusion is actually required to establish the current project contract correctly.

Do not persist the selected adoption mode in `.guide-profile.json`.

## 0.8 profile composition, specialization, research, and validation review

When the resolved target version uses the 0.8 model or later:

- keep profiles broad and reusable rather than turning project details into feature-tag profiles;
- allow a small set of profiles to compose when several broad engineering shapes genuinely apply;
- determine whether each applied profile is repository-wide, component-scoped, or surface-scoped;
- use semantic component/surface identifiers defined by normal project authority rather than path globs as architecture metadata;
- treat profile order as non-semantic and do not invent primary/secondary precedence;
- resolve material conflicts between applicable profile obligations into project-local authority before implementation;
- migrate `.guide-profile.json` to schema version 2 when profile applicability metadata is adopted;
- treat legacy schema-version-1 profile entries as repository-wide unless repository evidence demonstrates narrower intended applicability;
- migrate concrete project-type/vendor/runtime rules into normal project-local authority;
- separate validation depth from validation target and execution locus;
- preserve authoritative local/runtime integration validation when CI cannot exercise the real target;
- record external/runtime-bound validation target, locus, platform/capability, invocation/evidence, and fallback constraints when material;
- preserve an intentional integration-first test strategy without manufacturing unit-test obligations from a generic test-pyramid assumption;
- classify existing planning notes/research as retain, revalidate, promote, supersede, remove, or legacy-guide where that classification is needed for migration;
- promote implementation-affecting conclusions that exist only in research/notes into normal project authority;
- retain research only when it continues to provide material future planning value;
- do not create research scaffolding when no durable planning evidence exists;
- keep ordinary implementation independent of `docs/research/` for operative project rules.

## Required output

Create one migration milestone under `docs/milestones/`.

Create or update `.guide-profile.json` when useful.

Create or update `.guide-sync/pending/` hints for deferred documentation cleanup.

Update target-repository docs only when needed to remove guide leakage, localize concrete specialization, define semantic profile scopes, resolve profile conflicts, promote research-derived project rules, preserve genuinely useful planning evidence, or make the migration implementation-ready.

Do not copy external guide documents into the target repository.

Do not create `docs/research/` or `docs/RESEARCH.md` merely because the target guide version supports them.

## Migration classification

Classify migration work as:

- required;
- conditional;
- deprecated;
- manual-review;
- no-op.

When research is present, classify its treatment separately enough to distinguish retained evidence from promoted project authority and legacy copied-guide cleanup.

Record the historical research-adoption decision (`none`, `selective`, or `reconstructive`) in the adoption work when the target model defines that capability. Treat it separately from required guide-system compliance.

## Planning/implementation separation

There is no direct synchronization between the planning AI and the implementation AI.

Create an implementation-ready package. The later implementation agent must be able to unpack the ZIP, open the primary milestone document, read only the authority documents explicitly listed in that milestone, implement the focus areas, run the specified validation against the declared targets/loci, and finish without reconstructing planning context, reading the external guide repository, or depending on non-authoritative research for project rules.

Also generate a concise execution prompt in chat for the later implementation agent.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, copied guide documents, planning transcripts, or research scaffolding without durable evidence.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profiles and applicability scopes, role, maturity, execution mode, and material specialization assumptions;
5. research-adoption mode, source material actually available, and research retained/revalidated/promoted/superseded/removed when material;
6. deferred reconstructive research-adoption work, if any;
7. a filled execution prompt for the later implementation agent;
8. documentation-sync hints and the `.guide-sync/pending/` files created.
