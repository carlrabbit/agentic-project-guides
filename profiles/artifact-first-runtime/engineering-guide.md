# Artifact-First Runtime Engineering Profile

## Status

Engineering profile for artifact-first runtimes and authoring systems.

## Generic building blocks

| Block | Purpose |
|---|---|
| Headless product CLI | Product operations are exposed through deterministic commands. |
| Structured project data | Source data is schema-validated, stable-ID-based, diffable, and reviewable. |
| Scenario-based validation | Deterministic scenarios produce structured results and artifacts. |
| Artifact evidence and reports | Validation emits inspectable artifacts. |
| Generated/derived artifact pipeline | Derived outputs have provenance and rebuild rules. |
| Human review gates | Human review is explicit when automation cannot decide correctness. |
| Dual-mode runtime validation | Debug and release representations preserve semantics. |

## Provider interpretation

A provider repository validates the machinery:

- CLI behavior;
- schema validation;
- scenario runner behavior;
- artifact schema emission;
- review gate mechanics;
- generated artifact reproducibility.

## Consumer interpretation

A consumer repository validates authored product/content with the machinery.

## Dogfood interpretation

A mixed repository may include minimal dogfood scenarios or content to prove the provider capability end-to-end.
