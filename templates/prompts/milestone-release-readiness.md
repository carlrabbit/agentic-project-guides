# Prompt — Plan a Release Readiness Milestone

Our planning task is to create an implementation-ready release-readiness milestone package for:

`{milestone}`

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository.
Do not make target repository documentation reference guide documents as operational authority.
Use the guide system only for planning, migration, documentation synchronization, review, and release readiness.

Target repository documentation must contain project truth only.

If the target repository contains `.guide-profile.json`, use it as guide-selection metadata. Ordinary implementation agents must not be required to read it.

If the target repository contains `.guide-sync/`, treat it as deferred documentation synchronization metadata.

If the target repository contains `.review/`, inspect it only for active reviews owned by this release-readiness milestone or unresolved migration state that directly blocks it.

## Planning/implementation separation

There is no direct synchronization between the planning AI and implementation AI.

Create a complete package that allows the later agent to start from the primary milestone, read only listed authority, perform release-readiness work, run the specified validation, produce evidence, and stop at any required human gate without reconstructing planning context.

Generate a filled execution prompt in chat.

## Repository inspection

Inspect the minimum relevant repository state, usually:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json`;
- release and packaging engineering docs;
- public API policy and baselines;
- public documentation contract and sources;
- samples and package-smoke configuration;
- release workflows;
- relevant milestones and decisions;
- `.guide-sync/pending/` items affecting the release surface;
- `.review/` items owned by the current release milestone.

## Deliverable boundary

Create a planning package, not an implementation patch.

The ZIP may contain:

```text
docs/milestones/M00XX-release-readiness.md
docs/specs/...
docs/decisions/...
docs/engineering/...
.review/pending/...
.guide-sync/pending/...
public-docs/...
```

Include only files required to make release-readiness implementation unambiguous.

Do not include source code, generated packages, workflow implementations, TBPs, issue templates, or copied guide documents.

## Milestone requirements

The primary milestone must include:

1. release target and intended version;
2. repository maturity and profile assumptions;
3. release scope and non-goals;
4. package, API, documentation, sample, diagnostic, and website surfaces in scope;
5. authority documents;
6. focus areas;
7. validation tiers and concrete commands;
8. constrained-execution handling;
9. release evidence requirements;
10. human-review requirements;
11. direct documentation impact;
12. deferred documentation sync items;
13. acceptance criteria;
14. publish operations explicitly excluded unless requested.

## Human review

A release review belongs to this release-readiness milestone.

It may review:

- release candidate artifacts;
- package contents;
- user-facing documentation;
- compatibility decisions;
- visual or UX release evidence;
- release notes.

Specify the canonical review ID, class, evidence, acceptance criteria, reviewer role, blocking behavior, and milestone-scoped review-check command.

If the release candidate changes before this milestone completes, updated evidence may require another decision in the same active review.

After the milestone completes, the review is historical evidence. It is not a perpetual approval of future repository state or future releases.

## Validation

Use Tier 4 release validation when applicable.

When long validation supports resumable execution, require `--plan-json`, bounded shards, receipts, and a fast verifier.

Do not infer release readiness from partial output.

## Chat response

After creating the ZIP, provide:

1. download link;
2. file list;
3. reason for each file;
4. resolved profile, role, maturity, and execution mode;
5. filled execution prompt;
6. release evidence and human-review expectations;
7. deferred documentation sync hints;
8. commands expected for local, CI, release, and review validation.

## Quality bar

The package is acceptable only if the release target is unambiguous, publish operations are not accidentally performed, validation is concrete, review is milestone-scoped, required public surfaces are covered, and the implementation agent does not need to read the external guide repository.
