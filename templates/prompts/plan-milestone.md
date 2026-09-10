# Prompt — Plan Milestone

Our planning task is to convert the following work into a ready milestone for a disconnected implementation phase:

`{milestone}`

The active guide authority is external:

- Guide repository: `carlrabbit/agentic-project-guides`

Do not copy guide documents into the target repository. Target repository documentation contains project truth only.

## Planning responsibility

Planning and implementation are separate phases.

Your job is to remove implementation-affecting uncertainty, not to pre-implement the change in prose.

Inspect enough repository truth and relevant planning knowledge to decide what must be fixed before implementation can safely choose concrete mechanics.

Planning owns decisions that materially affect:

- architecture;
- semantics and behavior;
- public or persisted compatibility;
- scope and non-goals;
- cross-package or subsystem boundaries;
- acceptance criteria;
- validation and human-review policy;
- applicable guide profiles/scopes and material conflicts between their obligations;
- required project-local specializations for concrete runtimes, services, environments, packaging boundaries, or domain architecture.

Planning also owns the research boundary: determine which unknowns require investigation, which evidence is worth persisting for future planning, which existing research must be revalidated, and which conclusions must be promoted into project authority before implementation.

The implementation phase owns concrete files, types, functions, refactorings, test structure, execution decomposition, implementation sequence, supporting edits required by the contract, validation execution, persistent execution progress, and completion audit where those choices do not change the resolved contract.

Do not require the implementation agent to reconstruct planning context or read the external guide repository.

## Repository inspection

Inspect the target repository before writing files.

Read the minimum project truth needed to plan correctly. Usually consider:

- `README.md`;
- `AGENTS.md`;
- `.guide-profile.json` if present;
- `docs/TERMINOLOGY.md`;
- `docs/SPECS.md` and relevant specs;
- `docs/ENGINEERING.md` and relevant engineering/specialization docs;
- relevant architecture and decisions;
- relevant current milestones;
- source and tests needed to understand architectural boundaries and existing behavior.

Read `.review/`, `.guide-sync/`, workflows, public docs, or legacy copied guides only when the topic requires them.

If `docs/RESEARCH.md` exists, use it as a non-authoritative discovery surface to locate research relevant to the current decision. Read only the research subjects that materially overlap the milestone or its unresolved questions.

Treat `docs/research/` as non-authoritative planning knowledge. Do not treat research conclusions as project requirements unless they have been promoted into ordinary project authority.

Treat copied guide documents under `docs/research/` as legacy/non-authoritative guide leakage, not research authority.

Use `.guide-profile.json` as guide-selection, applicability, and planning metadata only. Ordinary implementation agents must not be required to read it.

When `.guide-profile.json` uses schema version 2, resolve which repository/component/surface-scoped profiles apply to the milestone using the semantic component/surface definitions in normal project authority.

Use `.guide-sync/` as deferred documentation synchronization metadata only. Ordinary implementation agents must not be required to read it unless explicitly assigned synchronization work.

Treat `.execution/` as implementation-owned operational state, not planning authority. Planning should not pre-author execution ledgers for future milestones.

## Research and planning knowledge

Use `meta/RESEARCH-MODEL.md` when the milestone depends on investigation, external evidence, experiments, historical reconstruction, comparison work, or prior research.

The purpose of research is to preserve reusable evidence, not to preserve the planning conversation.

For each material unknown, decide whether to:

```text
resolve from current project authority
reuse current relevant research
revalidate prior research
perform new investigation now
create a diagnostic/investigation milestone because evidence cannot yet be obtained
```

Persist new research under `docs/research/` only when future planning would materially benefit and the evidence would be expensive, unreliable, or wasteful to rediscover.

A durable research artifact should preserve, as applicable:

- question and context;
- scope;
- evidence/provenance, including material versions or experiment conditions;
- findings;
- uncertainty, assumptions, and inferences;
- implications for project decisions;
- freshness/revalidation triggers;
- resulting project-authority links.

Use `templates/research/research-template.md` as the conceptual shape when useful. Do not require every trivial investigation to create a research file.

Distinguish direct observations from inferred conclusions and unverified assumptions when that distinction matters to the planning decision.

Do not persist:

- planning transcripts or chain-of-thought style reasoning;
- generic brainstorming;
- implementation task lists;
- copied guide methodology;
- information already fully represented as current project authority when the underlying evidence has no continuing planning value.

### Promotion rule

Research is not implementation authority.

If a conclusion constrains implementation, validation, compatibility, architecture, public behavior, supported environments, or another durable project contract, promote it into the appropriate specification, architecture, decision, engineering, milestone, or other authority document before the milestone is ready.

The implementation handoff must remain valid if `docs/research/` is not read.

Research may remain as provenance/evidence when it is still useful, and project authority may link to it for traceability. The operative rule itself must exist in project authority.

### Freshness and retrieval

Do not assume research is current solely because the file is recent or was once accepted.

Revalidate material findings when a recorded trigger has occurred, contradictory evidence appears, or the current project/runtime/version context makes the prior evidence reasonably doubtful.

Do not revalidate unrelated research and do not load the entire research corpus by default.

### Research lifecycle

At the end of planning, classify touched research pragmatically:

```text
retain current evidence
mark/revise as needs-revalidation
supersede when old evidence remains useful
remove when no durable planning value remains
```

Git history is sufficient archival storage. Do not retain obsolete research merely as an archive.

## Profiles and project specialization

Use profiles only for broad reusable engineering shapes. Do not model an operating system, local/CI execution, a test-strategy preference, one packaging mechanism, a named external vendor/runtime, or one concrete product architecture as a profile merely to make project composition more granular.

A repository may combine a small number of profiles when multiple broad engineering shapes genuinely apply.

For the milestone's affected scope, determine every applicable profile:

```text
repository-wide profiles
+ matching component-scoped profiles
+ matching surface-scoped profiles
```

Applicable profiles compose additively. Profile order has no semantic meaning. Do not assign primary/secondary precedence and do not let a narrower profile silently override a broader one.

If applicable profile obligations materially conflict, planning must resolve the conflict into durable project-local authority before the milestone is ready.

Component/surface IDs in guide metadata are semantic project-defined identifiers, not path-based architecture authority. Resolve their meaning from normal project documents.

When generic guide concepts need concrete answers, record them as project-local authority in the repository's normal engineering, specification, architecture, or decision documents.

For external/runtime-bound integration, use `meta/VALIDATION-MODEL.md` to identify the generic decision surface and `meta/SPECIALIZATION-MODEL.md` to decide what must become project truth. The implementation agent must receive the concrete specialization through referenced repository authority, not by reading those guide files.

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

If planning cannot settle a material decision without additional evidence, create a focused diagnostic or investigation milestone whose target state is that evidence. Use the result to return to planning, persist reusable research when justified, promote resulting conclusions into project authority, and produce or revise the final implementation milestone.

Large execution volume is not by itself a reason to require a stronger model or split a coherent semantic milestone. Shape large work using coherent scope, observable obligations, bounded execution work packages that the implementation phase can derive, persistent execution state, resumable validation, and explicit evidence.

## Ready milestone boundary

The milestone is ready only when the configured baseline implementation model can proceed without making a new material decision about architecture, semantics, compatibility, scope, acceptance, validation policy/topology, applicable profile obligations/conflicts, or required project specialization and can maintain reliable execution coverage across the expected implementation volume.

The ready milestone must contain, as applicable:

1. goal;
2. target state;
3. execution profile and `ready` lifecycle state;
4. baseline implementation model or an explicit statement that the project default applies;
5. scope;
6. non-goals;
7. resolved decisions and constraints, including any material profile-conflict resolution;
8. required project authority, including specialization/profile-scope authority when applicable;
9. acceptance criteria;
10. validation depth/tiers, targets, execution loci, platform/capability requirements, concrete commands, execution mode, and expected evidence;
11. direct documentation impact;
12. deferred documentation synchronization hints;
13. human-review requirements;
14. constrained-runtime requirements;
15. escalation boundary for unresolved material decisions.

Research artifacts may be referenced separately as non-authoritative evidence when useful, but they are not substitutes for item 8. Every operative conclusion required by implementation must be recoverable from the ready milestone or project authority.

Acceptance criteria and completion obligations must describe the milestone outcome, not merely the expected implementation activity. Where applicable, cover required artifacts, generated outputs, documentation, migrations, cleanup, compatibility behavior, external/runtime integration, and human-review gates in addition to automated tests.

For large or long-running milestones, acceptance and completion obligations must be structured clearly enough that the implementation agent can map them to bounded work packages and evidence in a persistent execution ledger. Planning does not need to predict those concrete work packages.

Do not require exhaustive file lists, predicted class/function changes, or detailed implementation sequences unless those details are themselves architecturally or compatibly significant.

If the source work item uses focus areas, workstreams, or similar decomposition, do not turn them into an exhaustive edit allowlist unless that restriction is genuinely part of the contract.

Do not retain planning scratch work, rejected alternatives, or discussion history merely because they were useful while reaching the decision. Preserve a rejected alternative only when knowing that rejection is necessary to prevent a likely incorrect implementation or when the underlying comparative evidence remains materially useful to future planning.

## Validation planning

Validation depth and execution location are separate concerns.

For each material validation obligation determine, as applicable:

- tier/depth;
- real validation target;
- execution locus: local, CI, remote, or mixed;
- platform/capability requirements;
- provisioning/connection and cleanup/isolation constraints when these are project policy;
- concrete invocation;
- expected evidence;
- fallback behavior when the authoritative target is unavailable;
- consumer/release relationship.

Do not infer that Tier 3 integration validation belongs in PR/CI workflows. A local installed runtime, real database, browser, native subsystem, remote service, or other declared target may be authoritative.

Do not weaken an integration target to a fake or shallow substitute merely because the real target is unavailable in CI. Instead, represent the actual locus/capability constraint and separate portable CI checks from authoritative integration evidence.

If the project's testing policy is integration-first, do not introduce unit-test obligations merely to satisfy an assumed test pyramid. Require the evidence needed for the project's actual boundaries.

## Baseline-executability audit

Before marking the milestone `ready`, explicitly verify that:

- architecture, semantics, compatibility, scope, acceptance, validation, applicable profile obligations/conflicts, specialization, and human-review policy are settled to the degree required by the work;
- the milestone's affected components/surfaces and their applicable profiles are known where multiple scoped profiles exist;
- every implementation-affecting conclusion discovered through research has been promoted into the ready milestone or project authority;
- relevant retained research has sufficient provenance/freshness information for future planning where material;
- no stale or contradicted research is being relied on without appropriate revalidation;
- remaining choices are local implementation mechanics rather than new project policy;
- acceptance criteria let the executor distinguish correct completion from partial implementation;
- every material completion obligation is explicit enough to be mapped to implementation work and evidence;
- subjective acceptance is routed to human review instead of being left as vague executor judgment;
- required external dependencies, validation targets, execution loci, platforms, credentials/capabilities, and fallback semantics are known where material;
- large or long-running work can be decomposed during implementation into bounded coherent work packages without reopening planning;
- long implementation can resume from repository-local execution state rather than depending on conversational memory;
- long validation has a safe bounded/resumable shape where required;
- no stronger implementation model is being relied on to resolve uncertainty that belongs in planning.

If any item fails, keep the milestone in `draft/planning` or create a diagnostic milestone. Do not mark it `ready` merely because implementation could probably make progress.

## Additional authority and research documents

Create or update specs, architecture docs, decision records, engineering docs, project-local specialization docs, scenarios, artifact contracts, or public docs only when a planning conclusion must become durable project truth before implementation.

Create or update `docs/research/` only when durable evidence is justified by the research model. Research is planning knowledge, not project authority.

Do not duplicate complete authority-document bodies inside the milestone. Reference them.

Do not create central-style technology profile documents in the product repository merely to mirror guide taxonomy. Use the repository's normal project-authority structure.

## Deliverable boundary

Create a planning/design package, not an implementation patch.

The package may contain repository-relative project-truth Markdown, justified durable research artifacts, milestone metadata, `.review/` requests, or `.guide-sync/pending/` hints directly required to make the milestone ready.

Do not include implementation source files, test files, generated code, workflow YAML, broad unrelated documentation cleanup, TBPs, issue templates, copied guide documents, planning transcripts, or pre-authored `.execution/` ledgers.

Do not create a bespoke per-milestone `EXECUTE-Mxxx.md` or equivalent file that repeats canonical execution methodology, milestone acceptance criteria, or project authority.

An overlay ZIP is a transport mechanism for repository-relative planning changes. It is not separate planning authority.

When an overlay requires application instructions, keep them limited to transport/application steps and identification of the primary ready milestone. Do not turn application instructions into a second execution contract.

## Documentation impact

Update documentation during planning only when a resolved decision must become project truth before implementation.

If broader documentation work must survive handoff, create focused `.guide-sync/pending/` hints. Do not require the implementation agent to read deferred sync metadata.

Research retention is independent of documentation synchronization: retain evidence because it has future planning value, not merely because a documentation pass is pending.

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

Determine whether validation may exceed a constrained agent runtime or depend on a locus/capability unavailable in the current execution context.

For resumable suites, specify the plan command, shard contract, receipt location, fingerprint scope, verifier command, and expected aggregate evidence. Never accept partial child output as aggregate success.

For locus-constrained validation, distinguish a genuine external capability block from a product failure and from portable validation that can still run elsewhere.

Distinguish capability-provider validation from capability-consumer product validation. Mixed/dogfood scope must be bounded and explicit.

## Implementation tractability and closure expectation

The ready milestone must support an executor that owns both reliable execution progress and milestone closure.

The implementation phase will:

```text
read milestone and authority
-> execution decomposition
-> create/reconcile .execution/<milestone-id>.md
-> implement a coherent work package
-> validate and update ledger
-> repeat
-> freshly reread milestone
-> reconcile milestone <-> ledger <-> repository/evidence
-> completion audit
-> continue or terminate
```

Do not design the milestone so that passing tests is the only implied completion condition when other obligations exist.

Do not require the implementation agent to keep the entire execution plan in conversational memory. The ready contract must be structured so obligation coverage can be externalized into the implementation-owned ledger.

The executor must be able to determine from the milestone, referenced project authority, execution ledger, live repository, and concrete evidence whether the outcome is actually complete, awaiting required human review, or externally blocked.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement repository-relative files needed to make the milestone ready. If moves or deletions cannot be represented directly, include concise application instructions rather than preserving obsolete files.

After creating the ZIP, respond with:

1. download link;
2. included file list and purpose, distinguishing project authority from non-authoritative research;
3. confirmed or inferred applicable profiles/scopes, role, maturity, execution profile, and baseline implementation model;
4. primary ready-milestone path;
5. concise transport/application handoff when needed;
6. documentation-sync hints created;
7. human-review items and evidence expectations;
8. validation target/locus and constrained-execution instructions if applicable;
9. research created/revalidated/promoted when material;
10. any unresolved issue that prevents the milestone from being marked ready.

The canonical implementation methodology is `templates/prompts/execute-milestone.md`. Do not recreate it in the planning package.

## Quality bar

The package is acceptable only if:

- the goal and target state are unambiguous;
- material architectural, semantic, compatibility, scope, acceptance, validation, applicable-profile/conflict, and specialization decisions are resolved;
- research used for material decisions is sufficiently grounded, current for the decision, and promoted where implementation depends on its conclusions;
- the implementation handoff remains complete without requiring ordinary implementation to load planning research;
- the milestone is executable by the configured baseline implementation model without relying on model escalation for unresolved project-level reasoning;
- large/long execution is tractable through implementation-owned bounded work packages and persistent execution state;
- constraints and non-goals prevent likely scope drift without prohibiting necessary supporting work;
- required project authority is explicit;
- acceptance criteria are observable or verifiable and cover the actual milestone outcome;
- validation is concrete about depth, target, locus, platform/capability, command, and evidence where material, but is not confused with milestone completion;
- implementation can derive local mechanics from the live repository without the planning conversation or `.guide-profile.json`;
- implementation is not burdened with planning scratch work, speculative edit instructions, or duplicated per-milestone execution methodology;
- the selected execution profile is explicit and appropriate to the work;
- human-review requirements are milestone-owned and explicit when automation cannot decide acceptance;
- long validation is resumable where required;
- old copied guides are not treated as active authority or as durable research;
- no TBP or issue-template dependency is introduced;
- a material unresolved decision prevents `ready` status rather than being silently delegated to implementation.
