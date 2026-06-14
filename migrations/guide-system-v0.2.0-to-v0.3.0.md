# Migration — Guide System v0.2.0 to v0.3.0

## Purpose

Introduce execution handoff prompts and generic latest-version adoption/update prompts.

## Applies to

Repositories or workflows that use disconnected planning and implementation agents.

## Required changes in the guide repository

- Add execution prompt templates.
- Add `adopt-latest-guide-system.md`.
- Add `update-to-latest-guide-system.md`.
- Update `templates/PROMPTS.md`.
- Add ADR-0007 and ADR-0008.

## Conditional changes in product repositories

No product-repository change is required merely because this version exists.

Apply only if the repository uses planning packages and disconnected implementation agents:

- update planning workflow to emit an execution prompt in chat;
- ensure implementation agents are not instructed to read the external guide repository;
- ensure migration prompts resolve the latest guide version explicitly rather than using fixed version-pair prompts as the default.

## Deprecated

- Planning packages that provide a milestone ZIP but no execution prompt.
- Implementation prompts that say only "implement the ZIP" without listing execution constraints.
- Direct implementation instructions such as "upgrade this repository to the latest guide".

## Manual review

- Review current planning prompts and replace version-pair prompts with latest-version prompts where practical.
- Keep version-specific migration documents as structured source material.

## Validation

- Prompt index lists execution prompts and latest-version prompts.
- Planning prompts instruct agents to generate execution prompts in chat.
- Execution prompts instruct implementation agents not to read the external guide repository.
