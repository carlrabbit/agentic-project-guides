# Prompt — Update Repository to Latest Agentic Project Guide System

Our planning task is to create an implementation-ready migration package for updating a repository from any existing `carlrabbit/agentic-project-guides` version to the latest available guide-system version.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, review, and release readiness.

Target repository documentation must contain project truth only, plus non-authoritative planning knowledge when the applicable guide version explicitly defines such a layer and durable evidence warrants retention.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

If the target repository contains `.review/`, treat it as repository-local human-review state. Read it only when the milestone requires human review, engineering migration, documentation synchronization, or release readiness.

## Resolve current and latest guide versions

Read the target repository's `.guide-profile.json` if present to identify the current recorded guide-system version.

Then inspect the guide repository to determine the latest available version.

Read at minimum:

- `README.md`;
- `CHANGELOG.md`;
- `meta/VERSIONING.md`;
- `meta/MIGRATION-MODEL.md`;
- all migration documents newer than the current version;
- relevant decisions;
- relevant meta models introduced or changed by those migrations, including `meta/RESEARCH-MODEL.md` when applicable;
- `templates/PROMPTS.md`.

State both the current and resolved latest versions in the chat response and in the migration milestone.

Do not assume a hard-coded latest version.

Migration documents are authoritative for version-to-version transformation semantics. Do not apply the current latest model directly to an old repository while skipping intermediate migration requirements.

## Repository inspection

Inspect the target repository before writing files.

Usually read:

- `.guide-profile.json`;
- `.guide-sync/pending/` if present;
- `.review/` if present and relevant;
- `README.md`;
- `AGENTS.md`;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- relevant `docs/specs/*`;
- `docs/ENGINEERING.md`;
- relevant `docs/engineering/*`;
- `docs/MILESTONES.md`;
- relevant milestones, decisions, architecture docs, public docs, workflows, and command scripts.

If `docs/RESEARCH.md` exists and a migration introduces or changes research/planning-knowledge semantics, use it as a discovery surface and inspect only research subjects relevant to the migration decisions.

Treat copied guides under `docs/research/` as non-authoritative legacy material unless explicitly marked otherwise. Do not assume every file under `docs/research/` has the same role: the applicable migration may distinguish genuine project research/evidence from copied guide leakage or obsolete notes.

## Apply version-specific model changes

Derive required repository changes from the complete migration chain between the recorded current version and the resolved target version.

For every changed guide concept:

- identify existing repository state shaped by the old model;
- apply the relevant migration classification and transformation;
- preserve concrete project truth rather than replacing it with copied guide methodology;
- update coordination metadata only where the target guide version requires it;
- keep the implementation handoff independent of external guide documents and planning conversation.

When a target migration introduces or changes a non-authoritative research/planning-knowledge layer:

- follow that migration's retention/promotion/freshness rules rather than inventing a generic archival policy;
- do not create research directories, indexes, or placeholder notes mechanically;
- distinguish retained evidence from project authority;
- promote any implementation-affecting conclusion into ordinary project authority when required by the target model;
- ensure ordinary implementation does not need research to reconstruct the migrated project contract.

## Optional transition capabilities

Some migration steps may introduce a reusable capability whose historical adoption is useful but not required for guide-system compliance.

Follow the migration document that introduces the capability. Keep its adoption decision separate from required migration changes.

For a transition that introduces historical research adoption, such as crossing from a pre-0.8 guide model into 0.8, evaluate the migration-defined mode:

```text
none
selective
reconstructive
```

Do not infer `reconstructive` merely because historical chats/files exist or because the project has a particular maturity stage.

A bounded optional adoption may be included when it is cheap and useful. If substantial reconstruction would dominate or delay the guide update, route it to `templates/prompts/special/adopt-research.md` and allow the guide migration to complete independently unless the migration document explicitly makes a recovered conclusion necessary for correctness.

Unavailable historical evidence must not be fabricated and does not by itself block guide migration.

Do not persist a historical adoption mode in `.guide-profile.json` unless a future migration explicitly changes the coordination schema to require such state.

This prompt intentionally delegates exact optional-transition behavior to the applicable version migration documents so future guide versions can evolve without being constrained by hard-coded 0.8 semantics.

## Required output

Create exactly one migration milestone under `docs/milestones/`.

The milestone must include:

- current and target guide-system versions;
- repository role and maturity;
- applicable profiles and applicability scopes when required by the target model;
- execution mode;
- required, conditional, deprecated, manual-review, and no-op changes;
- optional transition-capability decisions required by the migration chain;
- authority documents;
- likely affected files;
- validation depth/tiers, targets/loci when required, and concrete commands;
- human-review requirements;
- constrained-execution implications;
- direct documentation impact;
- deferred `.guide-sync/pending/` hints;
- research/planning-knowledge migration treatment when materially affected by the migration chain;
- acceptance criteria;
- rollback or recovery notes where appropriate.

Update `.guide-profile.json` only if the migration package includes that change.

Create `.guide-sync/pending/` hints for deferred documentation synchronization.

Do not copy guide documents into the target repository.

Do not perform broad implementation work.

## Human review

Inspect whether the target repository uses human review and which guide version shaped that implementation.

Apply the human-review migration semantics from the relevant migration documents rather than assuming the latest structure was always present.

For migration through versions that use the milestone-scoped human-review model:

- require pending reviews to identify one owning milestone;
- treat human review as a milestone completion gate;
- preserve completed records as historical evidence;
- remove generic repository-wide approval staleness;
- do not require humans to reapprove completed milestones because later commits occurred;
- keep canonical IDs and ephemeral interactive aliases;
- require milestone-scoped `review-check` behavior;
- classify ambiguous legacy pending requests as manual-review migration items.

When the migration milestone itself requires human judgment, create a review request owned by the migration milestone. Do not create an ongoing project-wide review gate.

## Constrained execution

Inspect engineering commands for long aggregate wrappers or agent-harness sensitivity.

When migration validation may exceed runtime limits, require resumable validation with:

- `--plan-json`;
- bounded `--shard <id>` commands;
- atomic fingerprinted receipts;
- fast `--verify`;
- no inference from partial output.

## Planning/implementation separation

There is no direct synchronization between the planning AI and the implementation AI.

Create an implementation-ready package. The later implementation agent must be able to:

1. unpack the ZIP into the target repository;
2. open the primary milestone document;
3. read only the authority documents explicitly listed in that milestone;
4. implement the focus areas;
5. run the specified validation;
6. handle constrained execution using resumable validation when required;
7. complete the current migration milestone's required human review or report its blocking status;
8. finish without reconstructing planning context, reading the external guide repository, or depending on non-authoritative research for operative project rules.

Also generate a concise execution prompt in chat for the later implementation agent.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement files that should be added to the target repository. Preserve repository-relative paths inside the ZIP.

Do not include implementation source files, generated code, broad unrelated documentation cleanup, TBPs, issue templates, copied guide documents, planning transcripts, or research scaffolding that the migration chain does not justify.

After creating the ZIP, respond with:

1. download link;
2. included file list;
3. reason each file is included;
4. confirmed or inferred profiles/scopes, role, maturity, and execution mode as defined by the target guide version;
5. a filled execution prompt for the later implementation agent;
6. documentation-sync hints and the `.guide-sync/pending/` files created;
7. required human-review items and evidence expectations;
8. constrained-execution or resumable-validation instructions, if applicable;
9. research/planning-knowledge migration actions, if applicable;
10. optional transition-capability decisions and any deferred dedicated workflow, if applicable.

## Quality bar

The package is acceptable only if:

- the implementation goal is unambiguous;
- required authority documents are explicitly listed;
- the later implementation agent does not need to read the external guide repository;
- the later implementation agent does not need to reconstruct project rules from planning research;
- each guide-version transition follows its applicable migration contract rather than an ahistorical latest-model assumption;
- optional historical reconstruction is not confused with required guide compliance;
- validation expectations are concrete for the target model;
- direct documentation updates are separated from deferred synchronization;
- provider and consumer responsibilities are not blurred;
- human-review requirements are explicit and milestone-scoped when the applicable guide version requires them;
- long validation is made resumable when the execution environment may terminate long-running commands;
- aggregate success is never inferred from partial output;
- copied guide material is not mistaken for current project authority or durable project research;
- genuine research/evidence is not deleted or promoted mechanically without applying the relevant migration semantics;
- unavailable historical evidence is reported rather than fabricated;
- no TBP or issue-template dependency is introduced;
- the later implementation agent does not need to reconstruct planning context.
