# Validation Model

## Status

Authoritative for risk-proportionate validation, milestone versus release boundaries, integration targets, and execution authority. Supersedes unconditional consumer-surface validation at ordinary milestone completion.

## Principle

Invest enough **planning analysis** to identify material failure modes and choose checks with high diagnostic value. Optimize **implementation + validation + review + expected rework** through fewer missed contracts and expensive correction cycles. Test to reduce meaningful uncertainty; apply [methodological economy](META-GUIDE.md#methodological-economy). Milestone verification and release qualification have distinct purposes.

For each change, ask:
1. Which intended changes, permitted consequences, and protected invariants define correctness?
2. Which plausible incorrect implementations might still pass ordinary successful examples or a build?
3. Which boundary, contrasting input, or cross-mode consistency property (if material) would expose them?
4. Which existing evidence already exercises the relevant contract, and what is the cheapest credible additional check?
5. What belongs to the final release candidate instead?
6. What is the consequence of an undetected defect, and can the change be discarded safely?

Planner-seeded **obligation accounting** establishes that work items are not silently forgotten; **validation evidence** establishes credible correctness. A completion ledger does not require one test, evidence-case ID, or gate per row. More tests are justified by higher consequence or insufficient confidence, **not** automatically by more acceptance criteria. A permanent regression test is useful for a reproducible bug with plausible recurrence or significant failure consequence; not every one-off correction needs a permanent fixture.

### Planner-owned verification design

For nontrivial or quality-critical checks, planning decides what makes the check discriminating, not only the test level or command. Specify as much as the executor needs to write a check that would fail for a plausible wrong implementation: the wrong behavior to catch, the starting state or inputs, the triggering action, the boundary (real or double), an independent expected result (oracle), and material side effects or their absence. Pick the parts that matter; this is not a per-test template. For example, a pagination-reset test must start away from page one: resetting from page one to page one proves nothing. An oracle must not just repeat the implementation's logic, and a double must not produce the result under test.

Check existing contract, architecture, conformance and integration tests for conventions and reusable coverage. When migrating tests, decide which behavioral guarantees and real boundaries must survive and which may be replaced or retired; do not leave that decision to the implementer. When a comparison or benchmark matters, define the baseline, comparable conditions, the measured property, how to interpret the result, and what to do if it cannot be measured. A representative test seed can help for difficult checks (see *Technical seeds* in the [Milestone Execution Model](MILESTONE-EXECUTION-MODEL.md)). The executor writes the tests within this design. None of this requires more tests, exhaustive cases, per-test evidence, or running tests during planning.

## Validation boundaries

| Boundary | Normal purpose | Default |
|---|---|---|
| Development feedback | Detect relevant mistakes while editing | Build affected code, inspect diagnostics, run focused tests when useful |
| Milestone completion | Establish the intended capability and key invariants | Focused tests and a few representative integration/fixture scenarios plus architectural review |
| Release qualification | Establish the integrated product is distributable and fit for supported consumers | Final package/installed artifact, representative consumer, platform/compatibility and operational behavior required by release policy |

The levels describe **purpose and timing**, not exclusive test technologies. An integration test may be the cheapest development check; a small unit test may establish a milestone invariant. The same check may contribute evidence to later release work if it remains relevant.

Ordinary milestones require the first two boundaries. Release qualification is not a default milestone gate. Qualify a consumer boundary *during a milestone* only if the milestone changes and is explicitly intended to deliver that boundary, if contractually required by project authority, or if the consequences of deferral are materially unacceptable. Document that reason briefly.

Do not defer every real integration test to release. Where correctness depends on real EF Core behavior, a native runtime, browser, process, or other boundary, a small representative integration remains the appropriate milestone check. **Real integration** and **installed-distribution acceptance** are different questions.

## Risk-proportionate milestones

Choose **high-information, discriminating** scenarios that challenge the plausible failure modes identified during planning. Select techniques that suit the risk: contrast adjacent eligible and ineligible cases, exercise a protected property, or compare related operating modes against their shared observable contract. Use the smallest focused set that credibly addresses the important risks; one fixture may exercise multiple boundaries. Intentional breaking changes need checks against the **authorized** invariants, not a blanket semantic-equivalence or always-compiles requirement. Test selection follows behavior and risk rather than case quotas or obligation counts.

Where an existing relevant suite already covers an unchanged contract, reuse that evidence rather than reimplementing the suite in a new harness. Focused validation should normally run after the relevant changes; unnecessary reruns after unrelated edits add no confidence. Evidence is not permanent: rerun a check when material inputs have changed or a result is no longer applicable.

A milestone may deliberately leave some compatibility, packaging, consumer-repository, multi-platform, and operational scenarios to release readiness. Record those deferrals succinctly, so release planning does not forget them. If a project ships directly after every milestone, the release boundary may coincide with that milestone and its associated qualification is then in scope.

Exploratory simulations, fault injection, and temporary diagnostic tests are investigative, not automatically regression tests. Keep expensive or nondeterministic exploration out of default test runs; promote only durable, useful assertions into regression tests.

### Corrections

A review finding should identify the concrete defect and the narrowest check that could detect recurrence. Use existing checks and infrastructure where sufficient; reduce earlier excessive requirements. Escalate only where a demonstrated material risk warrants it.

## Executable verification is a readiness requirement

For a substantive milestone, the planner **must** confirm that the proposed checks can be written and run by the intended executor, or at a specific authorized locus the executor can use. How small the verification is remains a judgment call; whether credible verification exists is **not**. For each material check, name the tool or command (or the focused check to be written), the target or fixture, the locus, and the permissions or dependencies it needs, labeled *checked*, *documented* or *assumed* as in the [Milestone Execution Model](MILESTONE-EXECUTION-MODEL.md#executor-feasibility-and-pre-ready-assessment). Do not cite a CI runner, desktop session, service, SDK or external API as available without a credible access path.

If the planner cannot see the executor's environment, use reliable project evidence. A routine uncertainty may become a bounded initial preflight; a materially uncertain prerequisite with no authorized resolution means the milestone is not `ready`. Missing access never justifies faking a required integration, moving required verification to release, or expecting provisioning the executor is not permitted to perform.

This is verification **design**: focused checks may be written and run during the milestone. Record only the material feasibility facts and select checks appropriate to the milestone boundary.

## Integration targets and execution locus

Validation depth, real target, and execution locus are independent. A real database or graphics runtime may run locally; CI is neither universally required nor automatically authoritative.

When external behavior materially determines correctness, identify the necessary target and (only as needed) its version, platform/capability, location, setup, isolation, cleanup, invocation, and failure interpretation in project authority. For a simple local check, a brief statement of the target and locus is sufficient.

Supported loci may be local, CI, remote, or mixed. A known unavailability does not authorize substituting a fake for a mandatory target or pretending that a different host is equivalent.

**Execution is not provisioning authority.** The implementer may execute documented tools and restore project dependencies. Installing persistent SDKs/software, changing shared hosts, creating/changing CI workflows, modifying permissions/secrets, or provisioning infrastructure requires separate authorization in project authority or the assigned milestone.

**Validation is not destructive-target authority.** Implementing or validating a destructive capability does not permit mutating non-disposable data or shared/external systems merely because credentials or a connection string are available. For such effects, require explicit target/action authorization and consequence-appropriate isolation, recovery, or rollback. Use owned, authorized, disposable fixtures for routine tests. If a required shared target is unavailable or unauthorized, perform permitted checks and report the specific blocked validation; do not invent infrastructure simply to make that check pass.

## Integration-first policies

Projects may select integration-first testing:
- prefer real persistence, framework, serialization, filesystem, process, browser, or native boundaries where those determine product behavior;
- use isolated unit tests when they provide faster or more diagnostic coverage;
- do not mirror internal method structure with tests solely to satisfy a pyramid;
- keep installation/packaging validation small and separate from detailed internal behavior.

This preference does not mandate comprehensive real-repository or installed-tool qualification for every milestone.

## Release and consumer qualification

When a product is distributed through a package, generated launcher, installation, published executable, or library consumption boundary, **release preparation must qualify each actively supported distribution mechanism** using representative behavior through the final consumer mechanism. Any excluded supported surface needs an explicit project release-policy justification; do not quietly replace a shipped-artifact check with source-only tests.

Examples include consuming a built NuGet package from an isolated project, invoking an installed locally packed `dotnet tool` through its shim, or invoking the published executable rather than `dotnet run`. Qualify the actual intended release candidate, not a stale global install or unrelated source output.

Check the important release properties for that product: installation or packaging, command discovery/startup, representative successful behavior, public failure semantics where material, public documentation/samples, compatibility and required operating environments. Choose scope according to risk.

Do not require every internal behavior test through the installed consumer. Reuse milestone integration evidence for behaviors unaffected by packaging; reserve the packaging path for questions it can uniquely answer.

A release milestone can require stronger evidence and additional gates, but that requirement does not retroactively turn each contributing implementation milestone into a release gate.

## Human review and evidence

A brief engineering review is normal. Formal human sign-off is an explicit milestone/release requirement when automated judgment is insufficient; it is not a generic quality gate attached to all work.

A milestone should usually record checks actually run, results, limitations, and deferred release checks. For substantive implementation milestones, the separate lightweight ledger reconciles planned obligation IDs with delivered outcomes. Add proof registers, fingerprinted receipts or immutable evidence only when auditability or the cost of reruns demonstrably justifies them.

## Expensive suites

For materially expensive validation, stage or shard execution and reuse valid evidence when this saves total work. See [Constrained Execution Model](CONSTRAINED-EXECUTION-MODEL.md). Sharding, receipt dependency fingerprints, and machine-readable plan/verifier infrastructure are **optional optimizations**, not baseline compliance requirements.
