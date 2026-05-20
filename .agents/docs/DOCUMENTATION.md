# DOCUMENTATION.md — Doc Index and Ownership

## All documentation files

| File | Covers | Update when |
|------|--------|-------------|
| [`README.md`](../../README.md) | The curated ML reading list, organized by topic and tier | A new paper is added or an existing entry changes |
| [`.agents/TUTORIAL.md`](../TUTORIAL.md) | Session protocol: initialization flow, session sequence, profile templates | Session flow changes, new topics added, template structure changes |
| [`AGENTS.md`](../../AGENTS.md) | Development routing guide and working rules | Repo structure changes, new boundary rules added |
| [`CLAUDE.md`](../../CLAUDE.md) | Tutorial trigger + pointer to AGENTS.md for dev work | Tutorial entry-point path changes |
| [`.agents/docs/SETUP.md`](SETUP.md) | First-time setup and common issues | Setup process changes |
| [`.agents/docs/ARCHITECTURE.md`](ARCHITECTURE.md) | System design, module map, session flow | Architectural decisions change |
| [`.agents/docs/DEVELOPMENT.md`](DEVELOPMENT.md) | Change-type playbooks | New change type is identified or an existing playbook changes |
| [`.agents/docs/GUIDELINES.md`](GUIDELINES.md) | Conventions, anti-patterns, commit format | A new pattern or anti-pattern is identified |
| [`.agents/docs/DOCUMENTATION.md`](DOCUMENTATION.md) | This index | A new doc file is added |

## Rules

- **New pattern identified** → update the nearest guide (`GUIDELINES.md` or the relevant playbook in `DEVELOPMENT.md`)
- **New doc file added** → add it to this index before merging
- **Session sequence changes** → update `.agents/TUTORIAL.md` (authoritative) and `ARCHITECTURE.md` (flow diagram)
