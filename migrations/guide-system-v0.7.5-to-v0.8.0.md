# Migration — Guide System v0.7.5 to v0.8.0

## Purpose

Adopt the 0.8 validation/specialization/profile-composition model without importing concrete guide-system methodology into product repositories.

## Migration required

Recommended for repositories that:

- use Tier 2/Tier 3 validation terminology;
- describe integration validation as PR/CI validation;
- encode CI in their `integration-ready` meaning;
- use concrete project-type guide selection;
- combine multiple engineering shapes in one repository;
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

### Profile selection and composition

Review profile sets for feature-tag behavior and implicit mixed-repository assumptions.

Do not introduce profiles merely for:

- Windows/Linux;
- local/CI execution;
- integration-first testing;
- NuGet/GitHub publication;
- one named runtime/service/vendor;
- one concrete project architecture.

Represent those through project engineering policy, validation topology, packaging/release policy, or project-local specialization.

When multiple broad engineering shapes genuinely apply, profiles compose additively.

Profile order has no semantic meaning. Do not introduce `primary`, `secondary`, or last-profile-wins behavior.

For each applied profile, determine whether applicability is:

```text
repository-wide
component-scoped
surface-scoped
```

Use semantic component/surface IDs whose meaning is defined by normal project authority. Do not use path globs in `.guide-profile.json` as the authoritative architecture definition.

Compatible obligations are combined. Material conflicts between applicable profile obligations must be resolved explicitly in project-local authority before implementation.

### Guide-profile schema version 2

Guide-system 0.8 introduces `.guide-profile.json` schema version 2 for scoped profile applicability.

Each applied profile records one or more `scopes` entries using:

- `repository`;
- `component` with project-defined `ids`;
- `surface` with project-defined `ids`.

Migration default for a legacy schema-version-1 profile entry:

```text
no previous applicability metadata
-> repository-wide
```

Use a narrower component/surface scope only when repository evidence shows the profile does not describe the whole repository.

Do not create semantic component/surface identifiers merely to make metadata look detailed. Use them only when they represent a durable boundary already needed by planning/project authority.

### Source-generator profile

0.8 includes a reusable `source-generator` profile for Roslyn source-generator/analyzer-style compile-time surfaces.

It commonly composes with `dotnet-library` when generators are packaged through NuGet.

In a mixed package suite, scope `source-generator` to the applicable generator components/surfaces rather than treating every package as a generator.

Concrete Roslyn/MSBuild compatibility, diagnostic, generated-source, package-layout, and version-alignment rules remain project-local where they differ by project.

## Product repository changes

As applicable:

1. update `.guide-profile.json` guide-system/base/profile version metadata to `0.8.0`;
2. migrate `.guide-profile.json` to schema version 2 and record semantic profile scopes;
3. update `docs/ENGINEERING.md` validation terminology;
4. record integration-first policy if it is an intentional project rule;
5. record authoritative integration targets and execution loci;
6. add/refine project-local specialization authority for concrete external runtimes/services;
7. define semantic component/surface IDs in normal project authority when scoped profiles require them;
8. resolve material profile conflicts in project-local authority;
9. update milestone templates/current draft milestones to carry validation target/locus requirements;
10. remove project-type guide references;
11. do not copy `meta/PROFILE-MODEL.md`, `meta/SPECIALIZATION-MODEL.md`, or other guide files into the product repository.

## Mixed package-suite example

A repository containing ordinary .NET packages plus Roslyn generator packages may migrate to:

```text
base                [repository]
dotnet-library       [repository]
source-generator     [component: generator-packages]
```

The project repository defines what `generator-packages` means in normal architecture/engineering authority.

The generator components receive both applicable `.NET library` obligations and source-generator obligations. Neither profile overrides the other.

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
- any mixed repository where selected profiles currently appear to apply to every component by accident;
- any profile ordering used as implicit precedence;
- any external-runtime test suite whose authoritative target or fallback behavior is implicit;
- any test policy that creates unit tests only because of a generic test-pyramid assumption.

## Completion

Migration is complete when project-local authority contains the concrete rules implementation needs, profile selection remains broad/reusable with explicit applicability where necessary, profile conflicts are resolved explicitly, and validation obligations no longer infer execution location from validation depth.
