# AGENTS.md — machine-learning-list

> Tutorial system based on ML reading list for Elicit employees.

## Development reference

| Changing... | Read next |
|---|---|
| Curriculum content (reading list, prompt files) | [`README.md`](README.md), [`prompts/`](prompts/) |
| Tutorial session protocol | [`.agents/TUTORIAL.md`](.agents/TUTORIAL.md) |
| Architecture or local setup | [`.agents/docs/ARCHITECTURE.md`](.agents/docs/ARCHITECTURE.md), [`.agents/docs/SETUP.md`](.agents/docs/SETUP.md) |
| Change playbooks | [`.agents/docs/DEVELOPMENT.md`](.agents/docs/DEVELOPMENT.md) |
| Coding conventions + anti-patterns | [`.agents/docs/GUIDELINES.md`](.agents/docs/GUIDELINES.md) |
| Doc index + ownership | [`.agents/docs/DOCUMENTATION.md`](.agents/docs/DOCUMENTATION.md) |

## Working rules

**Always:**
- Follow `.agents/TUTORIAL.md` exactly when session in progress
- Commit `learner/` changes after every session: `Session log: [Topic] — Tier [N] (YYYY-MM-DD)`

**Flag for human review:** any change to `prompts/`, `.agents/`, or `README.md`

**Never:**
- Modify `prompts/`, `.agents/`, or `README.md` without human approval
- Skip git commit after session — progress will be lost
