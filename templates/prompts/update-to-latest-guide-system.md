# Prompt — Update Repository to Latest Agentic Project Guide System

Plan migration from the repository's current recorded guide version to the latest available version in `carlrabbit/agentic-project-guides`.

Read `.guide-profile.json`, `CHANGELOG.md`, `meta/VERSIONING.md`, `meta/MIGRATION-MODEL.md`, and all migration documents newer than the current version.

State current and resolved latest versions explicitly.

Create one migration milestone and a ZIP containing only required repository-relative changes.

Classify changes as required, conditional, deprecated, manual-review, or no-op.

For v0.4.0 and newer, assess human review and engineering-command-host applicability.

For v0.5.0 and newer, assess whether aggregate commands need resumable shards, receipts, plans, and verification because of constrained agent runtimes.

Generate a filled execution prompt in chat.
