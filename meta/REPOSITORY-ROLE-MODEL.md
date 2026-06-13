# Repository Role Model

## Status

Authoritative for repository role selection.

## Purpose

Repository role prevents confusing capability implementation with capability usage.

## Roles

| Role | Meaning |
|---|---|
| `capability-provider` | Builds a reusable framework, tool, runtime, engine, compiler, SDK, generator, validator, or authoring system. |
| `capability-consumer` | Uses a capability to build a product, game, content set, application, or authored artifact. |
| `mixed-dogfood` | Builds a capability and includes bounded consumer-style samples or dogfood projects. |
| `application-product` | Builds an end-user application or product. |
| `documentation-only` | Maintains documentation without implementation ownership. |

## Provider vs consumer rule

```text
Do not confuse implementing a capability with using that capability.
```

Examples:

- A scenario-runner repository must prove the scenario runner works.
- A game repository using the scenario runner uses scenarios to validate game behavior.
- A source-generator repository tests generation behavior; it does not need to structure itself as if all code were generated.

## Dogfood boundary

Provider repositories may include dogfood samples, but dogfood content must stay bounded.

If dogfood content grows into a product, split it into:

- `samples/`;
- `testdata/`;
- a separate consumer repository.
