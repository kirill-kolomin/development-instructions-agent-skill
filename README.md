A simple set of instructions for development process

# development-instructions-agent-skill

Adds a bit more to resilience in the process of development with ai agentic coding tools.

| Task type | Read this first |
|---|---|
| Understanding the codebase from scratch | `CODEBASE_EXPLAIN.md` |
| Planning a new feature or change | `PLAN_CREATION.md` |
| Investigating before implementing (recon) | `PRE_IMPLEMENTATION_RECON.md` |
| Moving from plan to implementation | `PROCEED_TO_IMPLEMENTATION.md` |
| Reviewing code after implementation | `REVIEW_IMPLEMENTATION.md` |
| Designing or adding tests | `TEST_DESIGN.md` |

## Install

This repository is a valid [Agent Plugin](https://agent-plugins.org/) (spec v1.0.0): `plugin.json` at the root, skills under `skills/`. Any conformant client (Claude Code, Cursor, VS Code, Kiro, etc.) can load it from a local path or a git repository.

Using the [skills CLI](https://skills.sh):

```bash
npx skills add kirill-kolomin/development-instructions-agent-skill
```

Using GitHub CLI (Copilot, other `gh skill`-compatible clients):

```bash
gh skill install kirill-kolomin/development-instructions-agent-skill
```

Manually: clone this repo and point your client at it the way that client documents for loading local plugins.