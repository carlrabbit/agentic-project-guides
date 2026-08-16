# Prompt — Plan an AI-Executed, Human-Reviewed Milestone

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

The implementation phase owns concrete files, types, functions, refactorings, test structure, and implementation sequence where those choices do not change the resolved contract.

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

Use `.guide-profile.json` as guide-selection metadata only. Ordinary implementation agents must not be required to read it.

Use `.guide-sync/` as deferred documentation synchronization metadata only. Ordinary implementation agents must not be required to read it unless explicitly assigned synchronization work.

## Ready milestone boundary

The milestone is ready only when implementation can proceed without making a new material decision about architecture, semantics, compatibility, scope, acceptance, or validation policy.

The ready milestone must contain, as applicable:

1. goal;
2. target state;
3. execution profile and `ready` lifecycle state;
4. scope;
5. non-goals;
6. resolved decisions and constraints;
7. required project authority;
8. acceptance criteria;
9. validation tiers, concrete commands, and execution mode;
10. direct documentation impact;
11. deferred documentation synchronization hints;
12. human-review requirements;
13. constrained-runtime requirements;
14. escalation boundary for unresolved material decisions.

Do not require exhaustive file lists, predicted class/function changes, or detailed implementation sequences unless those details are themselves architecturally or compatibly significant.

Do not retain planning scratch work, rejected alternatives, or discussion history merely because they were useful while reaching the decision. Preserve a rejected alternative only when knowing that rejection is necessary to prevent a likely incorrect implementation.

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

## Mode requirements

Execution mode: `ai-executed-human-reviewed`.

Prefer coherent vertical slices rather than artificially tiny human-sized tasks when design authority is stable.

Execution mode does not change the planning/implementation boundary: planning resolves the contract; implementation chooses mechanics within it.

## Deliverable

Create a downloadable ZIP archive containing only new or replacement repository-relative files needed to make the milestone ready. If moves or deletions cannot be represented directly, include concise application instructions rather than preserving obsolete files.

After creating the ZIP, respond with:

1. download link;
2. included file list and purpose;
3. confirmed or inferred profile, role, maturity, and execution mode;
4. primary ready-milestone path;
5. concise execution prompt for the disconnected implementation agent;
6. documentation-sync hints created;
7. human-review items and evidence expectations;
8. constrained-execution instructions if applicable;
9. any unresolved issue that prevents the milestone from being marked ready.

## Quality bar

The package is acceptable only if:

- the goal and target state are unambiguous;
- material architectural, semantic, compatibility, scope, acceptance, and validation decisions are resolved;
- constraints and non-goals prevent likely scope drift;
- required project authority is explicit;
- acceptance criteria are observable or verifiable;
- validation is concrete;
- implementation can derive local mechanics from the live repository without the planning conversation;
- implementation is not burdened with planning scratch work or speculative edit instructions;
- human-review requirements are milestone-owned and explicit when automation cannot decide acceptance;
- long validation is resumable where required;
- old copied guides are not treated as active authority;
- no TBP or issue-template dependency is introduced;
- a material unresolved decision prevents `ready` status rather than being silently delegated to implementation.
