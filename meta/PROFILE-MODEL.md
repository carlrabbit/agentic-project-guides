# Profile Model

A profile is a reusable project category that activates documentation, engineering, validation, and release expectations.

Profiles avoid one universal repository template.

Example profiles:

```text
base
dotnet-library
source-generator
blazor-component
artifact-first-runtime
```

A profile defines a broad reusable engineering shape. It may define applicability, documentation layers, engineering blocks, validation expectations, maturity behavior, repository-role behavior, and migration concerns.

Profiles are not feature tags.

Do not create a profile merely for:

- an operating system;
- local versus CI execution;
- one external product or service;
- one packaging mechanism;
- one test-strategy preference;
- one concrete product architecture.

Those concerns should normally be expressed through project engineering policy, validation targets/loci, reusable generic guidance, or project-local specialization.

A project may combine a small number of profiles when multiple broad engineering shapes genuinely apply. Avoid profile proliferation that merely reconstructs a project from tags.

Concrete technology/runtime behavior belongs in project-local authority unless it has matured into reusable guide-level guidance independent of the originating project.
