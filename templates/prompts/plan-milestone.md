# Prompt — Plan Milestone

Our planning task is to convert the following work into a ready milestone for a disconnected implementation phase:

`{milestone}`

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository. Target repository documentation contains project truth only.

## Planning responsibility

Planning and implementation are separate phases.

Your job is to remove implementation-affecting uncertainty, not to pre-implement the change in prose.

Inspect enough repository truth to decide what must be fixed before implementation can safely choose concrete mechanics.

Planning owns decisions that materially affect:

- architecture;
- semantics and behavior;
- public or persisted compatibility;
- scope and non-goals;
- cross-package or subsystem boundaries;
- acceptance criteria;
- validation and human-review policy.

The implementation phase owns concrete files, types, functions, refactorings, test structure, implementation sequence, supporting edits required by the contract, validation, and completion audit where those choices do not change the resolved contract.

Do not require the implementation agent to reconstruct planning context or read the external guide repository.

## Repository inspection

Inspect the target repository before writing files.

Read the minimum project truth needed to plan correctly. Usually consider:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md` and relevant specs;
- `docs/ENGINEERING.md` and relevant engineering docs;
- relevant architecture and decisions;
- relevant current milestones;
- source and tests needed to understand architectural boundaries and existing behavior.

Read `.review/`, `.guide-sync/`, workflows, research, public docs, or legacy copied guides only when the topic requires them.

Treat `docs/research/` and copied guides as non-authoritative unless explicitly marked otherwise.

Use `.guide-profile.json` as guide-selection and planning metadata only. Ordinary implementation agents must not be required to read it.

Use `.guide-sync/` as deferred documentation synchronization metadata only. Ordinary implementation agents must not be required to read it unless explicitly assigned synchronization work.

## Execution profile

Select the execution profile during planning rather than choosing a different planning prompt.

For ordinary coding milestones, choose the profile that best describes who will execute and how much implementation autonomy is appropriate:

- `human-led`;
- `ai-assisted`;
- `ai-executed-human-reviewed`;
- `ai-executed-broad`.

Use the special planning prompts for engineering migration, documentation synchronization, or release-readiness work when their specialized authority and completion rules apply.

Execution profile is orthogonal to lifecycle phase. Every coding milestone still crosses the same `ready` boundary before implementation.

Execution profile does not describe model strength. Do not introduce `strong`, `frontier`, or similar execution profiles to compensate for unresolved planning.

## Baseline implementation model

Determine the project's baseline implementation model from `.guide-profile.json` when that metadata is present.

The default ChatGPT-focused guide profile uses:

```text
GPT-5.6 Luna
```

A project may intentionally configure another baseline model.

Planning must target the configured baseline when deciding whether the milestone is `ready`.

The purpose of the milestone is to make difficult project-level reasoning a planning responsibility so the baseline implementation model can execute the result reliably.

Do not solve baseline-model limitations by:

- selecting a stronger executor for an otherwise under-specified milestone;
- adding model-capability tiers to the milestone;
- converting the milestone into exhaustive line-by-line implementation instructions.

Instead, resolve the decisions that materially affect the project contract and make completion observable.

If planning cannot settle a material decision without additional evidence, create a focused diagnostic or investigation milestone whose target state is that evidence. Use the result to return to planning and produce or revise the final implementation milestone.

Large execution volume is not by itself a reason to require a stronger model. Shape large work using coherent scope, bounded operations, resumable validation, and explicit evidence.

## Ready milestone boundary

The milestone is ready only when the configured baseline implementation model can proceed without making a new material decision about architecture, semantics, compatibility, scope, acceptance, or validation policy.

The ready milestone must contain, as applicable:

1. goal;
2. target state;
3. execution profile and `ready` lifecycle state;
4. baseline implementation model or an explicit statement that the project default applies;
5. scope;
6. non-goals;
7. resolved decisions and constraints;
8. required project authority;
9. acceptance criteria;
10. validation tiers, concrete commands, and validation execution mode;
11. direct documentation impact;
12. deferred documentation synchronization hints;
13. human-review requirements;
14. constrained-runtime requirements;
15. escalation boundary for unresolved material decisions.

Acceptance criteria and completion obligations must describe the milestone outcome, not merely the expected implementation activity. Where applicable, cover required artifacts, generated outputs, documentation, migrations, cleanup, compatibility behavior, and human-review gates in addition to automated tests.

Do not require exhaustive file lists, predicted class/function changes, or detailed implementation sequences unless those details are themselves architecturally or compatibly significant.

If the source work item uses focus areas, workstreams, or similar decomposition, do not turn them into an exhaustive edit allowlist unless that restriction is genuinely part of the contract.

Do not retain planning scratch work, rejected alternatives, or discussion history merely because they were useful while reaching the decision. Preserve a rejected alternative only when knowing that rejection is necessary to prevent a likely incorrect implementation.

## Baseline-executability audit

Before marking the milestone `ready`, explicitly verify that:

- architecture, semantics, compatibility, scope, acceptance, validation, and human-review policy are settled to the degree required by the work;
- remaining choices are local implementation mechanics rather than new project policy;
- acceptance criteria let the executor distinguish correct completion from partial implementation;
- subjective acceptance is routed to human review instead of being left as vague executor judgment;
- required external dependencies and capabilities are known;
- large or long-running work has an execution/validation shape the baseline model can complete safely;
- no stronger implementation model is being relied on to resolve uncertainty that belongs in planning.

If any item fails, keep the milestone in `draft/planning` or create a diagnostic milestone. Do not mark it `ready` merely because implementation could probably make progress.

## Additional authority documents

Create or update specs, architecture docs, decision records, engineering docs, scenarios, artifact contracts, or public docs only when a planning conclusion must become durable project truth before implementation.

Do not duplicate complete authority-document bodies inside the milestone. Reference them.

## Deliverable boundary

Create a planning/design package, not an implementation patch.

The package may contain repository-relative project-truth Markdown, milestone metadata, `.review/` requests, or `.guide-sync/pending/` hints directly required to make the milestone ready.

Do not include implementation source files, test files, generated code, workflow YAML, broad unrelated documentation cleanup, TBPs, issue templates, or copied guide documents.

An overlay ZIP is a transport mechanism for these repository-relative changes. It is not separate planning authority.

## Documentation impact

Update documentation during planning only when a resolved decision must become project truth before implementation.

If broader documentation work must survive handoff, create focused `.guide-sync/pending/` hints. Do not require the implementation agent to read deferred sync metadata.

## Human review

Determine whether automated validation can decide acceptance for this milestone's outputs.

Human review is owned by this milestone and acts only as a milestone completion gate.

When human review applies, specify:

- applicability: none, recommended, required, or blocking;
- review class;
- canonical review ID or allocation rule;
- owning milestone;
- review subject;
- required evidence;
- acceptance criteria;
- reviewer role when relevant;
- acceptable completion decisions;
- waiver policy if any;
- request/record locations;
- exact milestone-scoped review-check command.

Do not define perpetual re-review or future-commit staleness for completed reviews.

## Constrained execution and validation

Determine whether validation may exceed a constrained agent runtime.

For resumable suites, specify the plan command, shard contract, receipt location, fingerprint scope, verifier command, and expected aggregate evidence. Never accept partial child output as aggregate success.

Distinguish capability-provider validation from capability-consumer product validation. Mixed/dogfood scope must be bounded and explicit.

## Implementation closure expectation

The ready milestone must support an executor that owns milestone closure.

The implementation phase will:

```text
implement -> validate -> completion audit -> continue or terminate
```

Do not design the milestone so that passing tests is the only implied completion condition when other obligations exist.

The executor must be able to determine from the milestone and referenced project authority whether the outcome is actually complete, awaiting required human review, or externally blocked.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement repository-relative files needed to make the milestone ready. If moves or deletions cannot be represented directly, include concise application instructions rather than preserving obsolete files.

After creating the ZIP, respond with:

1. download link;
2. included file list and purpose;
3. confirmed or inferred profile, role, maturity, execution profile, and baseline implementation model;
4. primary ready-milestone path;
5. concise handoff note for the disconnected implementation agent when useful;
6. documentation-sync hints created;
7. human-review items and evidence expectations;
8. constrained-execution instructions if applicable;
9. any unresolved issue that prevents the milestone from being marked ready.

The canonical implementation methodology is `templates/prompts/execute-milestone.md`; the handoff does not need to recreate that prompt.

## Quality bar

The package is acceptable only if:

- the goal and target state are unambiguous;
- material architectural, semantic, compatibility, scope, acceptance, and validation decisions are resolved;
- the milestone is executable by the configured baseline implementation model without relying on model escalation for unresolved project-level reasoning;
- constraints and non-goals prevent likely scope drift without prohibiting necessary supporting work;
- required project authority is explicit;
- acceptance criteria are observable or verifiable and cover the actual milestone outcome;
- validation is concrete but is not confused with milestone completion;
- implementation can derive local mechanics from the live repository without the planning conversation;
- implementation is not burdened with planning scratch work or speculative edit instructions;
- the selected execution profile is explicit and appropriate to the work;
- human-review requirements are milestone-owned and explicit when automation cannot decide acceptance;
- long validation is resumable where required;
- old copied guides are not treated as active authority;
- no TBP or issue-template dependency is introduced;
- a material unresolved decision prevents `ready` status rather than being silently delegated to implementation.
