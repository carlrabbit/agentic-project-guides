# Changelog

## 0.3.0

Migration required: conditional.

Affected areas:

- prompt templates;
- planning/execution handoff;
- generic migration/adoption prompts;
- guide-system migration workflow.

Affected product repositories:

- repositories using disconnected planning and implementation agents;
- repositories still using old copied setup/engineering guides;
- repositories already using `.guide-profile.json` and needing update to the latest guide-system version.

Added:

- execution prompt templates for planned milestones, engineering migration, documentation sync, and release readiness;
- generic prompt for adopting the latest guide system from any old local setup/engineering guide model;
- generic prompt for updating from any existing guide-system version to the latest guide-system version;
- ADR-0007 for generated execution prompts;
- ADR-0008 for latest-version migration prompts;
- migration document for guide system v0.2.0 to v0.3.0.

Conditional migration:

- update planning workflow to emit execution prompts in chat;
- replace version-pair prompt usage with the generic latest-version adoption/update prompts when appropriate;
- keep version-specific migration documents as source material, not the default user prompt.

Deprecated:

- planning packages that provide a milestone zip but no execution prompt for the implementation agent;
- asking an implementation agent to "upgrade to latest" directly.

Manual review:

- verify whether existing planning prompts should be replaced by latest-version prompts;
- verify whether implementation agents are still asked to read the external guide repository.

## 0.2.0

Added:

- prompt template library under `templates/prompts/`;
- `templates/PROMPTS.md` prompt selection index;
- `.guide-sync/` deferred documentation synchronization model;
- `templates/guide-sync-hint.md`;
- ADR-0006 for the guide sync hints queue;
- migration document for guide system v0.1.0 to v0.2.0;
- migration planning prompt for v0.1.0 to v0.2.0;
- standard prompts for empty project initialization, milestone planning execution modes, and documentation sync passes.

Changed:

- agent instruction template tells ordinary implementation agents to ignore `.guide-profile.json` and `.guide-sync/` unless explicitly assigned guide migration or documentation synchronization work.

## 0.1.0

Initial guide-system skeleton.

Includes:

- meta guide;
- profile model;
- maturity model;
- repository role model;
- validation model;
- milestone execution model;
- migration model;
- documentation layer model;
- base setup and engineering guides;
- initial dotnet-library and artifact-first-runtime profiles;
- initial agentic-2d-game-engine project-type guide;
- initial decision records;
- starter templates.
