# Validation Model

## Status

Authoritative for risk-proportionate validation, milestone versus release boundaries, integration targets, and execution authority. Supersedes unconditional consumer-surface validation at ordinary milestone completion.

## Principle

Optimize **implementation + validation + review + expected rework**, not the number of tests, gates, or proof artifacts. Test to reduce meaningful uncertainty. A milestone need not qualify a release.

For each change, ask:
1. What behavior or invariant changes, and what plausible defect matters?
2. Which existing evidence already exercises it?
3. What is the cheapest credible new check?
4. What belongs to the final release candidate instead?
5. What is the consequence of an undetected defect, and can the change be discarded safely?

More tests are justified by higher consequence or insufficient confidence, **not** automatically by more acceptance criteria.

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

Use the fewest representative scenarios that credibly exercise the new behavior and important failure modes. Prefer behavior over test-count quotas, happy/negative-case matrices, or one test per acceptance criterion.

Where an existing relevant suite already covers an unchanged contract, reuse that evidence rather than reimplementing the suite in a new harness. Focused validation should normally run after the relevant changes; unnecessary reruns after unrelated edits add no confidence. Evidence is not permanent: rerun a check when material inputs have changed or a result is no longer applicable.

A milestone may deliberately leave some compatibility, packaging, consumer-repository, multi-platform, and operational scenarios to release readiness. Record those deferrals succinctly, so release planning does not forget them. If a project ships directly after every milestone, the release boundary may coincide with that milestone and its associated qualification is then in scope.

Exploratory simulations, fault injection, and temporary diagnostic tests are investigative, not automatically regression tests. Keep expensive or nondeterministic exploration out of default test runs; promote only durable, useful assertions into regression tests.

### Corrections

A review finding should identify the concrete defect and the narrowest check that could detect recurrence. Do not add gates, receipt systems, evidence cases, or new engineering hosts by default. Earlier excessive requirements may be removed or reduced during correction. Escalate only where a demonstrated material risk warrants it.

## Integration targets and execution locus

Validation depth, real target, and execution locus are independent. A real database or graphics runtime may run locally; CI is neither universally required nor automatically authoritative.

When external behavior materially determines correctness, identify the necessary target and (only as needed) its version, platform/capability, location, setup, isolation, cleanup, invocation, and failure interpretation in project authority. Do not create a lengthy topology matrix for a simple local check.

Supported loci may be local, CI, remote, or mixed. A known unavailability does not authorize substituting a fake for a mandatory target or pretending that a different host is equivalent.

**Execution is not provisioning authority.** The implementer may execute documented tools and restore project dependencies. Installing persistent SDKs/software, changing shared hosts, creating/changing CI workflows, modifying permissions/secrets, or provisioning infrastructure requires separate authorization in project authority or the assigned milestone. When blocked, perform permitted checks, identify the unmet requirement, and report the blocker; do not invent new infrastructure simply to satisfy validation.

## Integration-first policies

Projects may select integration-first testing:
- prefer real persistence, framework, serialization, filesystem, process, browser, or native boundaries where those determine product behavior;
- use isolated unit tests when they provide faster or more diagnostic coverage;
- do not mirror internal method structure with tests solely to satisfy a pyramid;
- keep installation/packaging validation small and separate from detailed internal behavior.

This preference does not mandate comprehensive real-repository or installed-tool qualification for every milestone.

## Release and consumer qualification

When a product is distributed through a package, generated launcher, installation, published executable, or library consumption boundary, **release preparation** should exercise representative behavior through that final consumer mechanism.

Examples include consuming a built NuGet package from an isolated project, invoking an installed locally packed `dotnet tool` through its shim, or invoking the published executable rather than `dotnet run`. Qualify the actual intended release candidate, not a stale global install or unrelated source output.

Check the important release properties for that product: installation or packaging, command discovery/startup, representative successful behavior, public failure semantics where material, public documentation/samples, compatibility and required operating environments. Scope is risk-based, not an exhaustive matrix by default.

Do not require every internal behavior test through the installed consumer. Reuse milestone integration evidence for behaviors unaffected by packaging; reserve the packaging path for questions it can uniquely answer.

A release milestone can require stronger evidence and additional gates, but that requirement does not retroactively turn each contributing implementation milestone into a release gate.

## Human review and evidence

A brief engineering review is normal. Formal human sign-off is an explicit milestone/release requirement when automated judgment is insufficient; it is not a generic quality gate attached to all work.

A milestone should usually record the checks actually run, their results, known limitations, and deferred release checks. No mandatory one-to-one acceptance-to-proof register, fingerprinted receipts, or immutable reconciliation artifact is implied. Those mechanisms may be opted into when auditability or the cost of reruns demonstrably justifies them.

## Expensive suites

For materially expensive validation, stage or shard execution and reuse valid evidence when this saves total work. See [Constrained Execution Model](CONSTRAINED-EXECUTION-MODEL.md). Sharding, receipt dependency fingerprints, and machine-readable plan/verifier infrastructure are **optional optimizations**, not baseline compliance requirements.
