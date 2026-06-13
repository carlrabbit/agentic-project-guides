# Changelog

## 0.1.0

Initial guide-system skeleton.

Includes:

- meta guide
- profile model
- maturity model
- repository role model
- validation model
- milestone execution model
- migration model
- documentation layer model
- base setup and engineering guides
- initial dotnet-library and artifact-first-runtime profiles
- initial agentic-2d-game-engine project-type guide
- initial decision records
- starter templates


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

- agent instruction template now tells ordinary implementation agents to ignore `.guide-profile.json` and `.guide-sync/` unless explicitly assigned guide migration or documentation synchronization work.
