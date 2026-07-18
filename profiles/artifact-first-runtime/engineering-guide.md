# Artifact-First Runtime Engineering Profile

## Generic building blocks

| Block | Purpose |
|---|---|
| Headless product CLI | Product operations are exposed through deterministic commands. |
| Structured project data | Source data is schema-validated, stable-ID-based, diffable, and reviewable. |
| Scenario-based validation | Deterministic scenarios produce structured results and artifacts. |
| Artifact evidence and reports | Validation emits inspectable artifacts. |
| Generated/derived artifact pipeline | Derived outputs have provenance and rebuild rules. |
| Human review gates | A milestone may require human acceptance of evidence automation cannot judge. |
| Dual-mode runtime validation | Debug and release representations preserve semantics. |
| Resumable validation suites | Long validation can run as bounded shards with fast aggregate verification. |

## Human review

For artifact-first projects, human review commonly applies to:

- visual output;
- semantic classifications;
- UX flows;
- creative artifacts;
- generated content;
- release evidence.

A review is owned by the milestone that produced the evidence.

The review gates that milestone's completion. Once the milestone completes, the record remains historical and is not revalidated against later repository changes.

A provider repository validates review-system mechanics.

A consumer repository performs domain review of its authored product or content.

A mixed/dogfood repository may do both with bounded dogfood scope.
