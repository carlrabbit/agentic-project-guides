# Prompt — Plan a Documentation Synchronization Milestone

Our planning task is to create a documentation synchronization milestone package: `{milestone}`.

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains old copied setup or engineering guides, treat them as legacy/non-authoritative unless the repository explicitly marks them as active project documentation.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read `.guide-profile.json`.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata. Ordinary implementation agents must not be required to read `.guide-sync/`.

## Planning-seeded execution ledger

When this workflow produces an AI-executed ready milestone, planning must create `.execution/<milestone-id>.md` as part of the planning package before the milestone becomes `ready`.

Seed only contract-derived coverage:

- stable IDs for every individually verifiable acceptance criterion and material completion obligation;
- one separate pending ledger row per obligation;
- stable `EC-*` evidence-case IDs when one obligation spans materially distinct proof paths;
- required validation-gate IDs, target/locus, and the exact obligation/evidence-case IDs each gate is intended to prove.

Do not create evidence cases as a Cartesian product. Use them only for distinctions that could hide a different implementation path, state mechanism, compatibility surface, or contract failure.

Before handoff, verify exact set equality between the milestone's applicable obligation IDs and the seeded ledger registry and, where evidence cases exist, exact set equality for required evidence-case IDs.

Do not seed implementation work packages, implementation tasks, concrete implementation evidence, validation results, completion status, or resume state. Those are implementation-owned.

The execution ledger may compress work. It must not compress obligations.

## Planning/implementation separation

There is no direct synchronization between the planning AI and the implementation AI.

Create an implementation-ready package. The later implementation agent must be able to unpack the ZIP, open the primary milestone document, read only the authority documents explicitly listed in that milestone, implement the focus areas, run the specified validation tiers, and finish without reconstructing planning context or reading the external guide repository.

Also generate a concise execution prompt in chat for the later implementation agent.

## Repository inspection

Inspect the target repository before writing files. Read the minimum required target-repository documentation, usually:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md`;
- relevant `docs/specs/*`;
- `docs/ENGINEERING.md`;
- relevant `docs/engineering/*`;
- relevant existing milestones and decisions.

Treat `docs/research/` and old copied guides as non-authoritative legacy material unless explicitly marked otherwise.

## Required milestone document

Create exactly one primary milestone document under `docs/milestones/`.

The milestone must include:

1. goal;
2. repository role and maturity assumptions;
3. execution mode;
4. scope;
5. non-goals;
6. focus areas;
7. implementation constraints;
8. required authority documents;
9. files or areas likely affected;
10. validation tiers and concrete repository commands;
11. acceptance criteria;
12. direct documentation impact;
13. deferred documentation synchronization hints;
14. human review requirements if applicable;
15. out-of-scope guide migration work if applicable.

## Deferred documentation synchronization hints

If deferred documentation work must survive handoff, create one or more files under:

```text
.guide-sync/pending/
```

Do not require the implementation agent to read `.guide-sync/`.

## Provider versus consumer distinction

Do not confuse implementing a capability with using that capability.

Capability-provider repositories validate capability implementation. Capability-consumer repositories use capabilities for product validation. Mixed/dogfood repositories may do both, but dogfood scope must be bounded.

## Mode requirements

Execution mode: `documentation-sync`. This milestone may read `.guide-sync/pending/`. Do not include implementation source changes unless documentation metadata cannot be updated safely without them.

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
