# Agentic Project Guides

Version: 0.9.3 (draft)

Select the entrypoint for the **assigned task**. This repository supplies guide-system methodology for planning, migration, synchronization, and guide maintenance; product repositories own their implementation contracts. This README is a **navigation index**, not operative guidance.

## Task routing

| Assigned task | Start with |
|---|---|
| Plan a product milestone | `templates/prompts/plan-milestone.md` |
| Bootstrap a new product repository | `templates/prompts/new-project.md` |
| Implement a ready milestone | **Product repository:** ready milestone, its `.execution/<milestone-id>.md` when applicable, referenced project authority, and relevant code/tests. Use the canonical execution prompt supplied at handoff; ordinary Implementers do **not** load this guide repository. |
| Adopt the guide in an existing repository | `templates/prompts/adopt-guide-system.md` |
| Update a repository already using the guide | `templates/prompts/update-guide-system.md` |
| Plan an engineering migration | `templates/prompts/special/plan-engineering-migration.md` |
| Plan release readiness | `templates/prompts/special/plan-release-readiness.md` |
| Plan documentation synchronization | `templates/prompts/special/plan-documentation-sync.md` |
| Execute documentation synchronization | `templates/prompts/special/documentation-sync-pass.md` |
| Curate historical planning research | `templates/prompts/special/adopt-research.md` |
| Maintain or evolve this guide system | `meta/META-GUIDE.md` |

## Where rules and history live

- **Current methodology:** the selected canonical prompt and its relevant authoritative `meta/`, `base/`, and `profiles/` documents. Load only what the assigned workflow needs.
- **Concrete project authority:** product-repository milestones, specifications, engineering documents, decisions, and applicable project-local guidance resolved during planning.
- **Prompt catalog:** `templates/PROMPTS.md` (additional selection context; not a second execution contract).
- **Version history and migrations:** `CHANGELOG.md` and `migrations/`. Apply the relevant migration chain; do not treat historical release descriptions as current instructions.
- **Design rationale:** `decisions/` when the assigned work requires it.
