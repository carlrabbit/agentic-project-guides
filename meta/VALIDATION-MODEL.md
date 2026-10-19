# Validation Model

## Status

Authoritative for validation depth, validation targets, execution loci, and validation evidence concepts.

## Core rule

Validation depth and execution location are separate concerns.

A validation obligation should describe, as applicable:

```text
depth
+ target
+ execution locus
+ platform/capability requirements
+ evidence
```

Do not infer that integration validation belongs in CI, that local validation must be shallow, or that CI is required for repository maturity.

## Execution intent

Execution intent is independent of validation tier, target, and locus:

- **Development feedback** answers whether a change caused a relevant problem. Use focused, economical checks; their results are provisional.
- **Investigative execution** explores hypotheses through simulations, parameter sweeps, profiling, fault injection, or temporary diagnostic tests. It is not automatically regression or acceptance validation.
- **Acceptance validation** establishes milestone or release obligations with current evidence from required targets and loci.

Exploration may use real systems and acceptance may use a small focused test; technical depth does not determine intent. Implementers may run bounded diagnostic experiments without planning approval, but return material project decisions to planning. Keep investigative code outside default test discovery, CI, and canonical validation unless explicitly required by the milestone. Discard disposable probes, retain reusable findings as non-authoritative research when justified, and deliberately promote established invariants into bounded regression tests when useful.

## Validation efficiency

Use the cheapest reliable check that detects the current class of defect during iteration. Do not run complete build/test/package/consumer validation after every edit by default.

At completion, verify **all required gates against the current implementation**. This means all gates have valid, current evidence, not that all expensive checks must be re-executed. Execute missing/stale stages, reuse proven current evidence when safe, and preserve criterion/evidence-case coverage. Fresh final-candidate or consumer-surface validation remains necessary when the release/milestone contract requires it.

For materially expensive suites, prefer independent validation stages that avoid repeating successful work after a late failure, even without timeouts. Measure relevant stage and setup times; investigate repeated restore, process startup, workspace/fixture creation, and teardown. Do not compromise isolation to share setup. Cheap suites need no staging or caching machinery.

Concrete commands, stage dependencies, fingerprints, costs, fallback and investigative entry points belong in project-local engineering authority. Neither validation efficiency nor simulation alone justifies a new guide profile.

## Validation tiers

Tiers describe validation depth and purpose. They do not prescribe where validation runs.

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema checks, touched-file checks. |
| 1 | Focused validation | Affected project, component, spec-area, scenario, or shard validation. |
| 2 | Standard repository validation | Normal repository validation gate. |
| 3 | Integration validation | Validation through representative real subsystem, runtime, service, process, persistence, browser, native, or environment boundaries. |
| 4 | Release and consumer validation | Package, public API, public docs, samples, consumer-surface, release-candidate, and release checks. |
| 5 | Human review validation | Human acceptance of milestone evidence when automation cannot decide. |

A repository may run Tier 3 integration validation entirely on a developer workstation, entirely in CI, against a remote service, or through a mixed topology.

A Tier 4 consumer check may also be local. Publication automation does not define the validation tier.

## Validation targets

A validation target is the real boundary whose behavior establishes the required evidence.

Examples include:

- a source component or isolated transformation;
- a real database server;
- an installed desktop application/runtime;
- a browser runtime;
- a native graphics or platform runtime;
- a remote service or API;
- a packed NuGet package consumed by an isolated project;
- an installed `dotnet tool`;
- a published/package executable;
- a human-review evidence set.

Planning should make a validation target explicit when correctness materially depends on that target. Do not replace a required real target with an easier fake merely because the real target is unavailable in CI.

## Execution locus

Execution locus describes where validation can or must run.

Common loci include:

```text
local
CI
remote service
mixed
```

The locus may additionally require a specific platform, installed application, native capability, account, license, credential, network location, or hardware resource.

Project authority should state those requirements when they materially constrain validation.

Local developer machines are valid authoritative validation environments when the required runtime or capability is available only or primarily there.

CI may provide portable validation, redundant validation, publication automation, or release checks without becoming the authoritative location for all integration validation.

## Execution environment authority

A validation target and locus specify where evidence is valid; they do not, by themselves, authorize installing software, changing a machine, or creating infrastructure. Keep three permissions distinct:

- **Execution:** run documented build/test commands, restore declared project dependencies, and use existing authorized tools or environments.
- **Provisioning:** install/update SDKs, native toolchains, desktop runtimes, or other host software, or change persistent machine configuration. Specify the allowed scope (for example disposable sandbox, isolated user directory, or managed host) and owner when material.
- **Infrastructure modification:** create or materially change CI/CD workflows, runners, triggers, permissions, secrets, cloud resources, or other shared execution infrastructure.

Restoring declared project dependencies is ordinary execution, not permission for arbitrary host provisioning. Isolated tool installation may be executor-owned when existing project/environment policy authorizes it; machine-wide or persistent changes require appropriate authority. Technical access is not authorization. Neither high implementation autonomy nor a missing toolchain grants permission to introduce CI/CD infrastructure.

When a required capability is unavailable, diagnose the missing prerequisite, attempt only authorized remedies, and run explicitly permitted portable checks separately. A different host is a valid substitute only if the accepted alternative locus and evidence equivalence are specified by the milestone or referenced project authority. An instruction such as "use a supported host" must define whether local, CI, remote, or mixed hosts are allowed; it does not implicitly authorize creating a workflow. If the needed remedy or alternative is not authorized, preserve the unproven gate and report the dependency or return the material decision to planning.

These rules do not prohibit planned CI validation, authorized disposable environment setup, or in-scope maintenance of existing workflows. They prevent an executor from changing execution policy in order to satisfy it.

## Integration-bound validation

When correctness materially depends on an external runtime, service, installed product, real persistence engine, browser, native subsystem, or similar boundary, project authority should resolve the following as applicable:

- target: what real boundary establishes correctness;
- availability: whether it is mandatory, optional, licensed, remote, or installed;
- execution locus: where the validation can run;
- platform/capabilities: OS, native dependencies, hardware, application/runtime versions, network requirements;
- provisioning: how validation acquires or connects to the target;
- provisioning authority: what may be installed or configured, on which hosts, and by whom;
- infrastructure-change authority: whether creating/changing CI/CD or remote execution resources is in scope;
- accepted alternative loci: explicitly allowed host types and the evidence they can establish;
- isolation: how concurrent or consecutive validation avoids interference;
- reset/cleanup: how state is cleaned, recreated, or made disposable;
- identity/secrets: accounts, credentials, tokens, or permissions;
- invocation: how repository engineering commands drive validation;
- evidence: logs, queries, exported artifacts, screenshots, files, structured results, or other proof;
- failure semantics: how infrastructure/availability failure is distinguished from product failure;
- fallback validation: what useful checks may run when the authoritative target is unavailable;
- release relationship: whether release readiness requires current evidence from the target;
- consumer relationship: whether the packed/published artifact itself must be exercised against the target.

The guide system defines this decision surface. Concrete target rules belong in project-local engineering authority.

## Integration-first testing policy

A project may adopt an integration-first testing policy.

Under integration-first testing:

- prefer the largest practical real boundary that gives reliable, diagnosable evidence;
- use real framework/runtime/persistence/serialization/file/process boundaries where they are materially part of correctness;
- use unit tests when isolated validation is substantially cheaper, more exhaustive, or more diagnostic;
- do not create unit tests merely to mirror implementation structure or satisfy an assumed test pyramid;
- keep consumer-surface validation separate from detailed integration behavior when a distributable artifact exists.

Integration-first is an engineering policy, not a guide profile or validation locus.

## Consumer-surface validation

A distributable artifact is not validated merely because its source project, internal assemblies, command handlers, or unpackaged executable pass tests.

When a repository produces an artifact intended to be consumed through a packaging, installation, publication, or generated-launcher boundary, required validation must include at least one acceptance path that consumes the artifact through the intended consumer mechanism.

Examples:

```text
NuGet library
  -> pack the current package
  -> consume/reference the packed package from an isolated consumer
  -> exercise representative public behavior

dotnet tool
  -> pack the current tool package
  -> install that exact package through dotnet tool using an isolated tool path or local tool manifest
  -> invoke the installed tool through the generated tool command/shim
  -> exercise representative command behavior and exit semantics

standalone executable
  -> publish/package the current executable
  -> invoke the published artifact rather than the build-project entry point
```

The consumer-surface path must use the artifact produced by the current build. It must not accidentally resolve a globally installed package/tool, stale package cache result, repository build output that bypasses packaging, or developer-machine-only state unrelated to the declared consumer contract.

For a `dotnet tool`, packaged-tool acceptance should normally prove at least:

- installation from the locally produced package succeeds;
- the installed command/shim resolves;
- `--help`, `--version`, or an equivalent basic invocation works when such a surface exists;
- at least one representative successful command executes through the installed tool;
- invalid invocation or failure exit semantics are exercised when they are part of the public contract;
- representative artifact/file I/O is exercised through the installed tool when that is a material product capability;
- execution does not depend on repository-relative source/build paths or unrelated global installation state.

Do not run every internal test through the packaged surface. Use focused, unit, and direct integration tests as appropriate for detailed behavior, then keep consumer-surface acceptance small and representative.

If a milestone changes package metadata, installation behavior, command discovery/routing, startup composition, executable packaging, public command behavior, or dependencies that affect a distributable surface, planning and completion validation must include the applicable consumer-surface path.

Consumer-surface validation is evidence about the distributable product boundary. It complements rather than replaces lower-tier repository and integration validation.

## Tier 5 scope

Tier 5 is milestone-scoped.

It is not a perpetual project quality gate.

A Tier 5 review:

- is declared by one milestone;
- evaluates evidence produced for that milestone;
- may block that milestone's completion;
- becomes historical evidence after completion;
- is not revalidated after unrelated future changes.

Later milestones declare their own Tier 5 requirements when appropriate.

## Resumable validation

Materially expensive automated validation should consider independently executable stages, atomic fingerprinted receipts, and a fast aggregate verifier even without runtime-limit pressure. Prefer simpler direct validation when staging would cost more than it saves.

Validation receipts and human review records serve different purposes:

```text
validation receipt
  machine evidence that a bounded automated shard passed for a defined input state

human review record
  historical evidence that a human accepted milestone evidence at completion time
```

Automated receipts may become stale when their validation inputs change.

Stage-specific dependency fingerprints can preserve passing evidence across unrelated edits, but must cover material source, tests, fixtures, tooling, configuration, environment and upstream artifacts. Use conservative whole-repository invalidation when full dependencies are unknown; the existence of a receipt is never sufficient.

Completed human review records do not become stale under the generic model.
