# Prompt — Plan an Engineering Migration Milestone

Our planning task is to create an implementation-ready engineering migration milestone package for:

`{milestone}`

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, review, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

If the target repository contains `.review/`, treat it as repository-local human-review state. Read it only when the milestone requires human review, engineering migration, documentation synchronization, or release readiness.

## Optional execution progress

Do not initialize a mandatory `.execution/` ledger, obligation/evidence-case registry, or validation-gate mapping. Use a small repository-local resume note only when this particular migration or planning job is long-running enough to benefit. Acceptance remains defined by the primary milestone.

## Planning/implementation separation

There is no direct synchronization between the planning AI and the implementation AI.

Create an implementation-ready package. The later implementation agent must be able to:

1. apply the package into the target repository;
2. open the primary milestone document;
3. read only the authority documents explicitly listed in that milestone;
4. implement the focus areas;
5. run the specified validation tiers;
6. handle constrained execution using resumable validation when required;
7. complete the current milestone's required human review or report its blocking status;
8. finish without reconstructing planning context or reading the external guide repository.

Also generate a concise execution prompt in chat for the later implementation agent.

## Repository inspection

Inspect the target repository before writing files.

Read the minimum target-repository documentation needed to design the milestone package. Usually this includes:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- relevant `docs/specs/*`;
- `docs/ENGINEERING.md`;
- relevant `docs/engineering/*`;
- relevant existing milestones and decisions.

Read architecture, public docs, workflows, `.review/`, `.guide-sync/`, research, or old copied guides only when the topic requires them.

Treat `docs/research/` and copied guides as non-authoritative legacy material unless explicitly marked otherwise.

## Deliverable boundary

Create a planning/design package, not an implementation patch.

The package may contain repository-relative Markdown or metadata files such as:

```text
docs/milestones/M00XX-xxx.md
docs/specs/xxx.md
docs/architecture/xxx.md
docs/decisions/ADR-00XX-xxx.md
docs/engineering/xxx.md
docs/scenarios/xxx.md
docs/artifacts/xxx.md
docs/review/xxx.md
.review/pending/xxx.md
.guide-sync/pending/xxx.md
.execution/M00XX-<milestone>.md   # optional resume state, only if justified
```

Only include files directly needed to make the milestone implementation-ready.

Do not include implementation source files, test files, generated code, workflow YAML, broad documentation synchronization edits, TBPs, issue templates, or copied guide documents.

## Required milestone document

Create exactly one primary milestone document under `docs/milestones/`.

The milestone must define a coherent target, important architecture/invariants, scope/exclusions, verifiable acceptance outcomes, and focused milestone validation with release-only checks clearly deferred. Record applicable project authority, constraints, documentation-sync hints, authorization, and human judgment only where material. Do not create a file-edit forecast, evidence registry, or elaborate gate plan just to complete a template.

## Additional authority documents

Create specs, architecture docs, decision records, engineering docs, review docs, scenario docs, artifact docs, or public docs only when required for implementation readiness.

Do not duplicate complete spec bodies inside the milestone once a spec file exists. Link to the spec instead.

## Documentation impact

If deferred documentation work must survive handoff, create one or more files under:

```text
.guide-sync/pending/
```

Do not require the implementation agent to read `.guide-sync/`.

## Human review

Apply a human-acceptance gate only when judgment is actually necessary or project authority explicitly requires approval. Specify the review subject, relevant evidence, required reviewer/authority, and acceptable decision. A PR approval or concise milestone-local decision is sufficient by default. Do not prescribe `.review/` registries, canonical review IDs, six review commands, a new engineering host, or fingerprints simply for one approval.

Only when the repository **already uses** or deliberately needs the advanced structured review subsystem should the milestone reference its project-specific request/record locations, IDs, command contract, and scoped completion check. A future milestone owns any new review; completed decisions do not become stale after unrelated commits.

## Constrained execution and validation

Determine whether any validation command may exceed a constrained agent runtime.

For materially expensive suites, use direct stage commands first; introduce receipt/fingerprint/verifier machinery only when its cost is justified. Do not impose a new validation pipeline on a normal migration milestone.

## Provider versus consumer distinction

Capability-provider repositories validate capability implementation.

Capability-consumer repositories use capabilities for product validation.

Mixed/dogfood repositories may do both, but dogfood scope must be bounded and explicit.

## Mode requirements

Execution mode: `engineering-migration`.

Use this mode for:

- command contracts;
- build/test infrastructure;
- repository layout;
- validation tiers;
- human-review infrastructure;
- cross-platform launchers;
- .NET engineering command hosts;
- resumable validation;
- CI behavior;
- package/release substrate;
- guide-system migrations.

Classify migration work as required, conditional, deprecated, manual-review, or no-op.

Do not mix unrelated product feature implementation into the migration.

## Deliverable

Deliver a repository-relative package (directly in the requested branch/repository, or as a ZIP if requested) containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, or copied guide documents.

After preparing the package, respond with:

1. branch\/PR link or download link, as applicable;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profile, role, maturity, and execution mode;
5. a filled execution prompt for the later implementation agent;
6. documentation-sync hints and the `.guide-sync/pending/` files created;
7. required human-review items and evidence expectations;
8. constrained-execution or resumable-validation instructions, if applicable.

## Quality bar

The package is acceptable only if:

- the implementation goal is unambiguous;
- focus areas are sized appropriately for the selected execution mode;
- AI-executed milestones are not artificially split into tiny human-sized tasks;
- required authority documents are explicitly listed;
- the later implementation agent does not need to read the external guide repository;
- validation expectations are tiered and concrete;
- direct documentation updates are separated from deferred synchronization;
- provider and consumer responsibilities are not blurred;
- human-review requirements are explicit, milestone-owned, and limited to the current milestone when automation cannot decide acceptance;
- long validation is made resumable only when its cost or execution limits justify additional machinery;
- aggregate success is never inferred from partial output;
- old copied guides are not treated as active authority;
- no TBP or issue-template dependency is introduced;
- the later implementation agent does not need to reconstruct planning context.
