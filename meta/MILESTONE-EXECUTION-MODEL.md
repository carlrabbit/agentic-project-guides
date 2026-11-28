# Milestone Execution Model

## Status

Authoritative for milestone sizing, readiness, implementation ownership, execution outcomes, and completion. See [Validation Model](VALIDATION-MODEL.md) for assurance boundaries. This model replaces ADR-0019/ADR-0026/ADR-0027 proof machinery while preserving the lossless planner-seeded obligation inventory, as specified by ADR-0033.

## Purpose and economics

Plan **coherent capabilities at agent scale**. Invest the planning effort needed to resolve material decisions, prevent ambiguity and missed obligations, and reduce correction cycles. Optimize the **total outcome and downstream execution cost**. A disposable implementation branch can be cheaper than incremental delivery and extensive proof machinery. Apply [methodological economy](META-GUIDE.md#methodological-economy) throughout.

The default planning question is: *What is the largest coherent capability we can implement, evaluate, and, if necessary, discard at acceptable cost?*

- A milestone may span substantial refactoring, cross-component implementation, or a complete subsystem.
- Keep a coherent capability together even when it spans many files, requires hours of agent execution, or would be large for a human developer.
- Split when the outcomes are independent, the capability becomes semantically incoherent, a material decision requires separate investigation, or failure consequences make a smaller boundary economically preferable.
- Scope remains bounded by product intent and authority, not by a prescribed number of edits, tests, or work packages.
- Evaluate implementation risk separately from consequence risk. Reversible attempts may be ambitious; irreversible data, security, public-contract, or operational consequences require stronger controls.

Experimentation, disposable prototypes, and competing candidate implementations are allowed within the agreed capability and environment authority. The executor may discard a local approach and try another without a new planning cycle when the required outcome and invariants are unchanged.

**Destructive execution authority:** Authorization to implement a destructive capability is not authorization to execute its effects on non-disposable data, shared resources, or external systems. Access to a connection string, credentials, or executable commands does not itself grant target-specific execution permission. Mutating those targets requires explicit authorization for the target and action, with isolation, backup/recovery, or rollback precautions proportionate to the consequences. Without that authority, use authorized disposable environments and report the blocked external operation; do not block otherwise safe implementation work.

## Lifecycle and readiness

Coding milestones follow:

`draft/planning -> ready -> implementing -> done`

Planning owns decisions that materially determine architecture, semantics, public or persisted compatibility, goal, non-goals, invariants, acceptance, and exceptional validation/review constraints. For substantive work it must **investigate the change impact and resolve material change boundaries before `ready`**, including important contracts already present in the repository; broad scope or authorized breaking changes do not remove that obligation. However, planning may deliberately leave a **reversible internal architectural choice** to implementation when the externally observable contract, invariants, comparison criteria, and fallback/disposal boundary are explicit. This is an implementation experiment, not permission to invent project policy. Project-local guidance and profiles apply during planning; conclusions needed by the executor must be reflected in the milestone or referenced project authority.

A milestone is **ready** only when the contract is complete **and** the designated or project-defined baseline executor has a credible, authorized way to implement **and verify** its milestone-level outcomes (see [Executor feasibility](#executor-feasibility-and-pre-ready-assessment)). Plausible acceptance criteria alone do not establish readiness. Readiness does **not** require predicting file edits, work packages, proof topology, or an exact execution plan. Large implementation volume is not a readiness defect. The delivery identifies the repository state containing the ready contract via an exact Git planning commit or an applied ZIP overlay; see [Planning Handoff Transport Model](HANDOFF-TRANSPORT-MODEL.md).

If a material planning decision requires evidence, perform the source inspection, research, comparison, or focused diagnostic work needed to resolve it, regardless of whether that investigation is longer than the expected implementation. Use a diagnostic milestone where an independent investigation is genuinely necessary; do not use one merely to postpone a cheap, reversible internal implementation choice.

No generic model-specific capability tier is prescribed. Project configuration may identify a baseline implementation model, but the milestone must be self-contained for the chosen executor without depending on that agent's private planning conversation. The metadata value `ai-executed` identifies **who implements**; milestone size and human acceptance are independent properties, not alternative execution modes.

## Change-impact investigation and readiness

For a **substantive code or system change**, planning must investigate the materially affected existing behavior and contracts before deciding the milestone is ready. Make the following distinctions explicit in the milestone or its referenced operative project authority wherever they affect correct implementation:

- **Intended changes:** capabilities, semantics, interfaces, or behavior that must become different.
- **Permitted consequences:** tolerated secondary changes, accepted incompatibilities, or intentionally temporary limitations (for example, a change that may require subsequent consumer repair). Permission for one consequence is not permission for unrelated breakage.
- **Protected invariants:** existing behavior and properties that must remain intact, such as relevant data integrity, security/access boundaries, public or persisted contracts, and source/artifact integrity.
- **Affected interactions:** neighboring behavior, similar-but-ineligible inputs, related operating modes (such as preview/check versus mutation), and integration surfaces that could disagree or regress.
- **Plausible material failures:** incorrect interpretations or defects that ordinary successful examples or a passing build could miss; identify which deserve discriminating checks.

This is an **investigation and decision obligation**. Inspect relevant code, tests, specifications, documentation and evidence as deeply as needed. Resolve consequential ambiguities in the ready contract. Record material conclusions in existing milestone sections or project authority; the ledger inventories deliverable outcomes, not individual invariants. Choose verification under the Validation Model. The implementation agent remains free to choose mechanisms and reversible approaches within the resolved boundaries. Not all changes require semantic equivalence or compilable intermediate artifacts: the explicitly authorized contract determines what is protected.

## Executor feasibility and pre-ready assessment

For every **substantive milestone**, the planner confirms before `ready` that the intended executor can implement and verify the work where it will actually run. Base this on evidence, not on model strength or on what software exists in principle.

- **Inspect what matters for this milestone:** repository commands and source/test layout; toolchain, SDK, runtime and OS/architecture; desktop or browser capability; services, network reach, credentials and permissions; disposable fixtures; time and resource limits.
- **Label each material capability** as *checked* (observed directly), *documented* (stated by a current authoritative source) or *assumed*. The planner's machine is not the implementer's machine, and a CI runner or remote host that exists is not necessarily one the assigned agent can use. Probe when you have safe access. Never report a documented or likely capability as checked. A short prose statement covering the material capabilities is enough; this is not a per-item table.
- **Define executable milestone verification:** the existing commands or the focused checks to be written, the real targets and execution locus where they matter, permitted setup and isolation, and the access needed to run them. Tests may be written during implementation; they need not exist or run at planning time.
- **Resolve missing prerequisites before `ready`:** find an authorized provisioning step or an available alternative executor or locus, or keep the milestone in `draft`. Only a routine, low-risk uncertainty may become an initial executor preflight, and it needs a stated fallback. Missing access never justifies moving required milestone checks to release or replacing a required real boundary with a mock.
- **Review your own draft before `ready`** from two perspectives: (1) *target state* — design choices resolved, obligations covered, implementation and verification feasible; (2) *conformance* — project authority, existing contracts and conventions, ownership, existing evidence, and the quality of any seeds. Fix what you find. This is the planner's existing self-review, not a separate reviewer or gate.

Record the conclusions and remaining preflights in the existing milestone sections. Leave implementation mechanics to the executor.

Example: the designated Windows executor's SDK and local build route are established by current project authority. An isolated test database is documented and authorized; only its routine availability at execution time is uncertain. Specify a connection preflight and an already-authorized equivalent disposable fallback (or report a blocker if it fails). In contrast, an unverified ability to access the only required real integration target leaves the milestone in `draft`.

## The ready contract

Use [the milestone template](../templates/milestones/milestone-template.md). A ready milestone ordinarily needs:

1. **Goal and target capability:** observable end state.
2. **Architecture and invariants:** project-level decisions, intended behavioral changes, permitted consequences, affected interactions, and protected contracts established by change-impact analysis.
3. **Scope and exclusions:** meaningful limits; not an exhaustive file allowlist.
4. **Acceptance:** independently deliverable, verifiable outcomes; not a test-case inventory or artificially compressed summary.
5. **Validation and execution feasibility:** discriminating checks for plausible consequential defects and boundary violations, with the executor capabilities, prerequisites and loci needed to run them; explicitly identify any exceptional milestone-stage qualification.

Reference only project authority needed to implement the change. Include documentation impact, migration, or required human judgment where material. The acceptance contract must preserve all independently deliverable, material obligations; do not collapse distinct outcomes merely to shorten the document. For a substantive milestone, assign stable IDs to those obligations (including required documentation or migration deliverables) and seed the same IDs in a lightweight execution ledger before `ready`. A genuinely trivial, indivisible task may omit a ledger with a short rationale. Use the ledger for deliverable accounting and the Validation Model to select checks.

**Completeness and correctness are separate concerns.** The obligation inventory prevents the executor from losing planned work; focused validation establishes credible behavior. One test or architectural inspection may support multiple outcomes. A passing test suite alone never excuses ignoring an obligation it does not cover.

## Planning and implementation separation

Planning sets the target and the material solution and verification boundaries; implementation realizes them. "Internal" does not mean "delegable". There are three levels of responsibility:

- **Product and architectural decisions** (planning): goals, semantics, contracts, ownership, compatibility and invariants.
- **Quality-critical technical design** (planning): open choices where materially different results could all satisfy the written contract, and choosing well needs broad project context, hard technical reasoning, or capability the baseline executor may lack. Typical examples are core algorithms, complexity limits, state/concurrency/lifecycle, recovery, resource ownership, persistence boundaries, key abstractions and nontrivial test design.
- **Technical realization** (implementation): local mechanics, integration and equivalent internal choices. Do not prescribe speculative edits or private structure to demonstrate planning effort.

To find open decisions, ask: *could two competent implementers both meet the written contract yet deliver materially different quality?* If so, and the cause is an unresolved choice, missing criteria, or a choice this executor should not be left to make, decide it and write the conclusion into the contract. Depth follows consequence, complexity, novelty and executor capability. A reversible experiment is still valid when its question, candidates, deciding criteria, protected boundaries and fallback are clear: the executor picks when the criteria decide, and returns an undecided material trade-off to planning with evidence. Planning need not remove all uncertainty or design interchangeable mechanics.

**Decision translation.** Read the applicable shared and local guidance, project rules, representative implementations and existing contract/conformance tests for the affected area, and turn them into concrete obligations. "Follow the guide" or "do it like component X" is not a decision. Existing patterns and tests are evidence, not authority over the intended change. Put the decisions, necessary assumptions, the reason for any non-obvious constraint, and the facts needed to implement or verify into the milestone or referenced project authority; leave out unrelated analysis. Durable decisions belong in normal project authority, not only in the milestone.

**Technical seeds.** When prose cannot convey a quality-critical design well, include a seed: a core algorithm, state operation, integration pattern or representative test. Mark which parts are binding and which are adaptable, check it against the actual APIs, versions and conventions, and say whether it was compiled or run. A seed is a planning artifact: not a product patch, not proof of correctness, and not a substitute for the implementer's integration and validation. Ordinary, well-specified work needs no seed.

The implementer may:
- choose classes, files, APIs internal to the subsystem, algorithms, tests, and refactoring sequence within settled design and verification constraints;
- decompose a large coherent milestone internally and change that decomposition as evidence emerges;
- run disposable experiments and compare alternative approaches;
- repair defects, including those found in review, using focused verification;
- add supporting edits needed to fulfill the agreed outcome.

The implementer must not:
- silently change public/persisted compatibility, required semantics, security constraints, or **settled** architectural, technical-design or verification decisions;
- introduce durable project policy (for example new product dependencies, persistence technology, or repository-wide build/analyzer settings) without planning authority;
- expand the product into unrelated capabilities;
- treat a missing toolchain as permission to install persistent software or modify CI/shared infrastructure;
- execute destructive or consequential mutations against non-disposable/shared/external state without explicit target and execution authorization;
- treat a failing check as permission to weaken an agreed product invariant.

If live repository discoveries invalidate a material decision, resolve that decision with planning. An unexpected local implementation detail does not automatically require replanning.

Ordinary implementers read the milestone, referenced project truth, and relevant code/tests. They do not need the guide repository, planning research corpus, or planning conversation to reconstruct the contract.

## Planner-seeded obligation ledger and execution progress

For every **substantive implementation milestone**, planning seeds a compact `.execution/<milestone-id>.md` ledger **before** declaring `ready`. Its purpose is lossless transfer of material work obligations, not proof collection. This default does not depend on expected elapsed time or whether the implementer is likely to be interrupted. Omission is appropriate only for a genuinely trivial, indivisible task where a second inventory provides no benefit; record that decision briefly in the milestone.

- Seed one pending entry per independently deliverable material milestone obligation, retaining the same stable ID and meaning as the milestone. Include direct documentation, migration, and setup deliverables where they are part of acceptance; do not generate rows for speculative implementation steps or each possible test.
- Planning owns the inventory. The implementer may add its own work tasks, progress details, and new discovered implementation steps, but may not silently merge, renumber, delete, reword away, or mark an unfulfilled planner-seeded obligation not applicable. Material scope changes return to planning. Planning owns what an obligation *is* (identity, meaning, applicability): only a planning amendment (see [Correction discipline](#correction-discipline)) may refine an obligation into sub-IDs, add IDs or supersede one. The implementer owns truthful *status*, including reopening a `done` entry when later evidence shows it is no longer met.
- During implementation, keep entries current (`pending` / `in progress` / `done` / `blocked` / `reopened` / `superseded`) and use the ledger for optional resume information. It is operational state subordinate to the ready milestone, not an independent source of policy.
- The ledger keeps every ID ever issued (the history). The **effective** obligations are the entries that are not `superseded`; they must match the obligation IDs of the current, possibly amended milestone. A `superseded` entry names the IDs that replace it and is accounted for by them; it never hides unfinished work.
- Before `COMPLETE`, reconcile the effective obligations with the current milestone and account for each entry against the delivered result. Every effective obligation must be `done`; a genuine blocker ends the run as `BLOCKED`, not `COMPLETE`. An entry is `done` only when the actual outcome is present; a green aggregate test or assertion of completion alone is insufficient. Unfinished entries require correction or a genuine blocker, never silent omission.

Use [the compact ledger template](../templates/milestones/execution-ledger-template.md) for completeness accounting; keep correctness evidence separate under the Validation Model. Per-obligation proof machinery is outside the default ledger contract. Keep the ledger through implementation and review; afterward retain or archive it according to project policy, with a short durable milestone completion note.

## Completion and review

Completion establishes that the delivered capability meets the milestone's acceptance contract with credible evidence, not that its distributable product has completed release qualification.

At completion:
- reconcile planned obligation IDs to the ledger, ensure every applicable deliverable is actually complete, and inspect the resulting behavior against every substantive outcome and invariant;
- run focused automated checks and a small number of representative integrations appropriate to actual risks;
- identify any known gaps and release-only checks that have been deferred;
- update direct documentation or migration material explicitly in scope;
- write a short **durable completion note** in the milestone or a project-defined completion record, then report the implementation, validation performed and results, and residual risks. Summarize the outcome and material evidence rather than mapping proof to every criterion.

Select checks by diagnostic value across acceptance clauses and reuse current results when still relevant. A brief review of architecture and behavior is usually sufficient; mandatory independent human sign-off requires an explicit reason.

Release preparation owns final package/installation/consumer, compatibility, cross-platform, and operational qualification of the integrated release candidate unless the milestone itself is about those boundaries or a material risk justifies earlier qualification.

### Correction discipline

Review findings must describe concrete defects, why they matter, and a **smallest credible focused verification** of the repair. Keep the existing contract and focused verification by default. Simplify disproportionate inherited validation. Expand the contract only for a newly demonstrated material risk or an explicitly requested product change. Add a small lasting regression check for a recurring, deterministic defect when worthwhile; otherwise a focused disposable verification may suffice. Use [the canonical review/correction prompt](../templates/prompts/review-milestone.md) when a separate reviewer prepares correction instructions.

For material or recurring findings, first classify the cause: a clear contract was violated; the contract was ambiguous or incomplete; technical or verification design was wrongly delegated; a feasibility assumption was wrong; or obligations were too coarse. Fix the cause instead of repeating an inadequate instruction. Before writing corrections, inspect the current milestone (with any amendments), relevant authority, the actual branch and ledger, and the findings. Keep unaffected decisions and still-valid evidence.

If the existing contract and obligations are sufficient, use a short correction prompt. If the correction changes a material decision, or adds independently deliverable outcomes the obligation inventory does not cover, write a versioned **amendment** to the milestone in the authorized working branch (or reconciled repository state) before handoff, even when the overall goal is unchanged.

**An amendment is planning work.** A reviewer who writes one acts as planner for that amendment and follows the planning rules in this model. A reviewer without planning or write authority proposes the amendment to the planner instead. When writing an amendment:

- keep the original handoff and its history; do not rewrite the original transport;
- keep existing obligation IDs and their meanings; refine a coarse obligation into traceable sub-IDs (for example `AC-03.1`) or add new IDs, and record them in the existing ledger as the [ledger template](../templates/milestones/execution-ledger-template.md) describes;
- identify the amendment in the ledger by a local label, and give the exact amended revision (for example the commit SHA) in the execution instruction instead of restating the amendment in chat;
- get authorization for material scope changes, and open a new milestone only for an independent delivery outcome.

A defect repair alone needs no new ID. Record amendments in the existing milestone and ledger. The implementer confirms ledger statuses against live results, not against earlier claims.

Example: a regression in delivered transformation support reopens AC-03 directly. If review instead establishes that the contract omitted independently deliverable syntax and semantic transformation requirements, the authorized planner amends AC-03 into AC-03.1 and AC-03.2, marks the parent superseded, and records the local amendment label A1. The executor receives the exact amended revision and completes both effective obligations.

### Retrospective planner feedback

When later evidence shows a material omission in a ready milestone (**PLAN**) or an avoidable miss or overreach in an earlier implementation review (**REVIEW**), append one line to the target repository's plain-text planner feedback log. The default path is `docs/agent-feedback/planner.log`; a project may set a different path in `docs/PROJECT-GUIDANCE.md`. Create the file with its first entry. Use one line per miss:

```text
YYYY-MM-DD | <milestone-or-PR> | <PLAN-or-REVIEW> | <specific observable miss> | <evidence reference>
```

Record the observable miss that the planner or earlier reviewer could reasonably have seen, with concrete evidence rather than a guessed root cause.

Example (illustrative identifiers): `2026-11-28 | M0042 | PLAN | Reset test specified page one as its initial state, so missing reset behavior would pass | PR #42 review: test PaginationReset`.
 Whether to log depends on whose miss it was, not on when it was found: a first review that establishes a material planning omission logs a `PLAN` line, while ordinary implementation defects (normal review output), unforeseeable failures and hypothetical risks are not logged. The log is optional retrospective data: it is not milestone context, acceptance evidence or a gate, and nobody is required to read or analyze it. Do not backfill past milestones. In a read-only review, propose the line instead of writing it.

### Terminal execution outcomes

- **COMPLETE** — acceptance is credibly met, proportionate milestone validation succeeded, and required documentation/review is satisfied.
- **AWAITING HUMAN REVIEW** — remaining work is only a specifically required human decision.
- **BLOCKED** — an external dependency or genuinely material unresolved planning decision prevents completion. Fixable implementation failures are not blockers.

These describe the execution run; they do not add lifecycle states. An agent must not declare completion solely because it built successfully, nor continue adding infrastructure after the milestone is adequately established.

## Workflow types and review

Normal feature, migration, diagnostic, documentation synchronization, and release-readiness work can use dedicated planning prompts where their delivery boundary differs. Special prompts apply the same substantive-milestone ledger and proportionate validation rules.

Milestone-scoped human review is optional unless required by the project or milestone. Approved reviews are historical decisions, not rolling approval of future changes. See [Human Review Model](HUMAN-REVIEW-MODEL.md).

Validation **depth** (focused, integration, release), **target**, and **locus** (local, CI, remote) remain independent. See [Validation Model](VALIDATION-MODEL.md).
