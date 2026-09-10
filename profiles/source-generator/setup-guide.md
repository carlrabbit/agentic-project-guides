# Source Generator Setup Profile

Use this profile when a repository or bounded repository scope ships a Roslyn analyzer/source-generator surface as a first-class deliverable.

This profile commonly composes with `dotnet-library` when the generator is distributed as a NuGet package.

In a mixed repository, scope this profile to the generator components or compile-time consumer surface rather than applying it repository-wide without evidence.

Common active project authority includes:

```text
docs/ENGINEERING.md
docs/SPECS.md
```

When the generator is publicly distributed, also activate the public documentation required for its package/consumer surface.

Project-local authority should identify the generator components/surfaces and any compiler/MSBuild compatibility constraints that materially affect consumers.
