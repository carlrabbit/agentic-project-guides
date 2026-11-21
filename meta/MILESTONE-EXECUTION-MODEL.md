# Milestone Execution Model

## Status

Authoritative for milestone sizing, readiness, implementation ownership, execution outcomes, and completion. See [Validation Model](VALIDATION-MODEL.md) for assurance boundaries. This model supersedes mandatory execution-ledger/evidence-case policies in ADR-0019, ADR-0026, and ADR-0027.

## Purpose and economics

Plan **coherent capabilities at agent scale**, not human-sized increments. Optimize planning, implementation, verification, review, and expected rework together. The cost of discarding a reversible branch is often lower than the cost of repeated incremental planning and exhaustive proof machinery.

The default planning question is: *What is the largest coherent capability we can implement, evaluate, and, if necessary, discard at acceptable cost?*

- A milestone may span substantial refactoring, cross-component implementation, or a complete subsystem.
- Do not split work simply because it involves many files, requires hours of agent execution, or would be large for a human developer.
- Split when the outcomes are independent, the capability becomes semantically incoherent, a material decision requires separate investigation, or failure consequences make a smaller boundary economically preferable.
- Scope remains bounded by product intent and authority, not by a prescribed number of edits, tests, or work packages.
- Evaluate implementation risk separately from consequence risk. Reversible attempts may be ambitious; irreversible data, security, public-contract, or operational consequences require stronger controls.

Experimentation, disposable prototypes, and competing candidate implementations are allowed within the agreed capability and environment authority. The executor may discard a local approach and try another without a new planning cycle when the required outcome and invariants are unchanged.

## Lifecycle and readiness

Coding milestones follow:

`draft/planning -> ready -> implementing -> done`

Planning owns decisions that materially determine architecture, semantics, public or persisted compatibility, goal, non-goals, invariants, acceptance, and exceptional validation/review constraints. Project-local guidance and profiles apply during planning; conclusions needed by the executor must be reflected in the milestone or referenced project authority.

A milestone is **ready** when the project's normal baseline executor can pursue the intended outcome from the ready handoff and live repository without inventing a new material project decision. Readiness does **not** require predicting file edits, concrete work packages, comprehensive proof topology, or an exact execution plan. Large implementation volume is not a readiness defect.

If a decision genuinely requires outside evidence, perform limited planning research or a diagnostic milestone. Do not create diagnostic milestones solely to avoid implementation uncertainty that can be resolved through cheap, reversible experimentation.

No generic model-specific capability tier is prescribed. Project configuration may identify a baseline implementation model, but the milestone must be self-contained for the chosen executor without depending on that agent's private planning conversation.

## The ready contract

Use [the milestone template](../templates/milestones/milestone-template.md). A ready milestone ordinarily needs:

1. **Goal and target capability:** observable end state.
2. **Architecture and invariants:** project-level decisions and boundaries the executor must preserve.
3. **Scope and exclusions:** meaningful limits; not an exhaustive file allowlist.
4. **Acceptance:** concise verifiable outcomes, not a test-case inventory.
5. **Validation:** cheapest credible checks and important known risks; explicitly identify any exceptional milestone-stage qualification.

Reference only project authority needed to implement the change. Include documentation impact, migration, or required human judgment where material. A milestone's acceptance contract is mandatory, but a ledger, evidence-case registry, validation matrix, and one-to-one acceptance-to-test mapping are not.

Acceptance criteria may be enumerated for clarity. Stable machine IDs are optional unless a concrete integration requires them. One test or architectural inspection may support multiple outcomes. A passing test suite alone never excuses ignoring requirements that it does not cover.

## Planning and implementation separation

Planning establishes the *what* and any material product constraints; implementation determines the *how*. Do not force the planner to predict mechanics available from inspecting live code.

The implementer may:
- choose classes, files, APIs internal to the subsystem, algorithms, tests, and refactoring sequence;
- decompose a large coherent milestone internally and change that decomposition as evidence emerges;
- run disposable experiments and compare alternative approaches;
- repair defects, including those found in review, using focused verification;
- add supporting edits needed to fulfill the agreed outcome.

The implementer must not:
- silently change public/persisted compatibility, required semantics, security constraints, or major architecture decisions;
- expand the product into unrelated capabilities;
- treat a missing toolchain as permission to install persistent software or modify CI/shared infrastructure;
- treat a failing check as permission to weaken an agreed product invariant.

If live repository discoveries invalidate a material decision, resolve that decision with planning. An unexpected local implementation detail does not automatically require replanning.

Ordinary implementers read the milestone, referenced project truth, and relevant code/tests. They do not need the guide repository, planning research corpus, or planning conversation to reconstruct the contract.

## Execution and optional progress state

Implement a coherent outcome; use focused feedback during edits; inspect implementation and run proportionate milestone checks near completion. Do not run full release or aggregate suites after every small change.

An execution ledger is **optional operational state**, useful for genuinely long, interrupted, multi-agent, or difficult-to-resume work. If used, `.execution/<milestone-id>.md` is a suggested path, and [the optional template](../templates/milestones/execution-ledger-template.md) provides a lightweight starting point. It never overrides the milestone and is not required before `ready`.

A ledger can summarize progress and resume context; it does not need one row per acceptance criterion, evidence case, or validation gate. No exact set-equality reconciliation, fingerprinted proof registry, work-package mapping, or immutable completion-evidence artifact is mandatory by default. Where a project has an explicit auditable-traceability requirement, define its scope and cost justification in project authority.

Maintain sufficient progress information to survive interruption when interruption is plausible. Avoid creating files, generators, or scripts just to administer short-lived execution state.

## Completion and review

Completion establishes that the delivered capability meets the milestone's acceptance contract with credible evidence, not that its distributable product has completed release qualification.

At completion:
- inspect the resulting behavior against every substantive outcome and invariant;
- run focused automated checks and a small number of representative integrations appropriate to actual risks;
- identify any known gaps and release-only checks that have been deferred;
- update direct documentation or migration material explicitly in scope;
- report the implementation, validation performed and results, and residual risks.

Do not create a separate validation case for each acceptance clause merely to produce a complete table. Existing current test results may be reused when still relevant. A brief review of architecture and behavior is usually sufficient; mandatory independent human sign-off requires an explicit reason.

Release preparation owns final package/installation/consumer, compatibility, cross-platform, and operational qualification of the integrated release candidate unless the milestone itself is about those boundaries or a material risk justifies earlier qualification.

### Correction discipline

Review findings must describe concrete defects, why they matter, and a **smallest credible focused verification** of the repair. A correction prompt must not automatically grow acceptance criteria, evidence cases, validation stages, test infrastructure, or broad regression requirements. If a prior validation contract is disproportionate, simplify it instead of carrying accumulated gates forward. Expand the contract only for a newly demonstrated material risk or an explicitly requested product change.

### Terminal execution outcomes

- **COMPLETE** — acceptance is credibly met, proportionate milestone validation succeeded, and required documentation/review is satisfied.
- **AWAITING HUMAN REVIEW** — remaining work is only a specifically required human decision.
- **BLOCKED** — an external dependency or genuinely material unresolved planning decision prevents completion. Fixable implementation failures are not blockers.

These describe the execution run; they do not add lifecycle states. An agent must not declare completion solely because it built successfully, nor continue adding infrastructure after the milestone is adequately established.

## Workflow types and review

Normal feature, migration, diagnostic, documentation synchronization, and release-readiness work can use dedicated planning prompts where their delivery boundary differs. Special prompts must not silently reinstate generic mandatory ledgers or evidence registries.

Milestone-scoped human review is optional unless required by the project or milestone. Approved reviews are historical decisions, not rolling approval of future changes. See [Human Review Model](HUMAN-REVIEW-MODEL.md).

Validation **depth** (focused, integration, release), **target**, and **locus** (local, CI, remote) remain independent. See [Validation Model](VALIDATION-MODEL.md).
