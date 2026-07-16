# Agentic Project Guides

Version: 0.5.0

This repository contains a versioned guide system for AI-first project setup, engineering, planning, implementation handoff, documentation synchronization, human review, migration, and validation.

## Core rule

```text
Guides live here.
Projects contain project truth.
Planning and documentation-sync work may use the guides.
Implementation work uses localized project documentation only.
```

## v0.4.0 capability additions

- repository-local human review workflow;
- review requests, records, evidence, and blocking semantics;
- canonical `eng/` commands for review operations;
- thin Bash and PowerShell launchers over shared tested implementation;
- explicit declaration and testing of platform support.

## v0.5.0 capability additions

- constrained agent execution model;
- resumable validation suites;
- bounded validation shards;
- atomic fingerprinted validation receipts;
- machine-readable validation plans;
- fast aggregate verification;
- explicit rejection of backgrounding or shell tricks as a remedy for hard harness lifetimes.

## Repository structure

```text
meta/
base/
profiles/
project-types/
decisions/
migrations/
templates/
```

See `CHANGELOG.md` and `templates/PROMPTS.md`.
