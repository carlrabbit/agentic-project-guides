# Migration — Guide System v0.7.5 to v0.8.0

## Purpose

Adopt the 0.8 validation/specialization model without importing concrete guide-system methodology into product repositories.

## Migration required

Recommended for repositories that:

- use Tier 2/Tier 3 validation terminology;
- describe integration validation as PR/CI validation;
- encode CI in their `integration-ready` meaning;
- use concrete project-type guide selection;
- depend on external runtimes/services/platform-specific integration targets;
- use or intend to use integration-first testing.

For repositories unaffected by those concepts, update guide metadata and review planning templates; no product behavior change is required.

## Guide-system changes

### Validation depth and execution locus

Replace assumptions such as:

```text
Tier 2 = local
Tier 3 = PR/CI
```

with:

```text
Tier 0 = edit sanity
Tier 1 = focused validation
Tier 2 = standard repository validation
Tier 3 = integration validation
Tier 4 = release/consumer validation
Tier 5 = human review validation
```

For material validation obligations, separately record as applicable:

- target;
- execution locus (`local`, `CI`, `remote`, `mixed`);
- platform/capability requirements;
- concrete invocation;
- evidence.

Do not move authoritative integration validation into CI merely to match the old tier naming.

### Integration readiness

If project documentation defines `integration-ready` as requiring CI, review whether CI is genuinely a project requirement.

The generic 0.8 meaning is that representative integration validation protects important real system boundaries. The required locus is project-specific.

### Integration-bound projects

When correctness depends on an external runtime, service, installed application, real persistence engine, browser, native subsystem, or similar target, ensure project authority resolves the applicable target contract:

- availability;
- locus/platform/capability requirements;
- provisioning/connection;
- isolation/reset/cleanup;
- identity/secrets;
- invocation;
- evidence;
- infrastructure versus product failure semantics;
- fallback validation;
- release/consumer relationship.

Keep concrete technology rules in normal project-local authority.

### Integration-first test strategy

Projects may explicitly choose integration-first testing.

Do not add unit tests solely to satisfy old guide expectations. Retain/add unit tests when isolated validation is materially cheaper, more exhaustive, or more diagnostic.

### Project types and specializations

The central `project-types/` concept is removed.

If a product repository records a selected central project-type guide, migrate the useful generic portions to applicable profiles and the concrete portions to project-local engineering/specification/architecture/decision authority.

For the former `agentic-2d-game-engine` guide specifically:

- keep `dotnet-library` and/or `artifact-first-runtime` profiles where applicable;
- keep concrete engine role, scenario, runtime, and product architecture rules in the engine repository;
- do not create a replacement `game-engine` profile unless a future vendor/domain-independent reusable engineering shape justifies it.

### Profile selection

Review profile sets for feature-tag behavior.

Do not introduce profiles merely for:

- Windows/Linux;
- local/CI execution;
- integration-first testing;
- NuGet/GitHub publication;
- one named runtime/service/vendor;
- one concrete project architecture.

Represent those through project engineering policy, validation topology, packaging/release policy, or project-local specialization.

## Product repository changes

As applicable:

1. update `.guide-profile.json` guide-system/base/profile version metadata to `0.8.0`;
2. update `docs/ENGINEERING.md` validation terminology;
3. record integration-first policy if it is an intentional project rule;
4. record authoritative integration targets and execution loci;
5. add/refine project-local specialization authority for concrete external runtimes/services;
6. update milestone templates/current draft milestones to carry validation target/locus requirements;
7. remove project-type guide references;
8. do not copy `meta/SPECIALIZATION-MODEL.md` or other guide files into the product repository.

## Windows-local / GitHub-publication example

A valid 0.8 project topology is:

```text
Windows developer workstation
  -> implementation
  -> Tier 3 authoritative integration validation against installed runtime
  -> dotnet pack
  -> Tier 4 isolated NuGet consumer validation

GitHub
  -> portable/redundant checks as desired
  -> release/publication automation
  -> NuGet publication
```

The project may choose different topology. This example demonstrates that CI publication does not make CI the required integration-validation locus.

## Manual review

Review:

- any milestone or engineering doc using the phrase `PR integration validation`;
- any project maturity rule that equates integration readiness with CI;
- any central/project-type selection metadata;
- any external-runtime test suite whose authoritative target or fallback behavior is implicit;
- any test policy that creates unit tests only because of a generic test-pyramid assumption.

## Completion

Migration is complete when project-local authority contains the concrete rules implementation needs, profile selection remains broad/reusable, and validation obligations no longer infer execution location from validation depth.
