# GUIDELINES.md — Coding Patterns and Conventions

## File naming

- Prompt files: `<NN>-<kebab-topic>.md` (zero-padded 2-digit number, matches session sequence)
- Session log files (after split): `tier<N>-<NN>-<kebab-topic>.md`
- Learner files: `profile.md`, `relevance.md` — fixed names, do not rename

## Markdown conventions

- Use `✨` to mark reading list entries added after 2025/11/26
- Tier 4+ entries go inside `<details><summary>Tier 4+</summary>` collapsible blocks
- Tables use pipe-aligned markdown (no trailing spaces required)

## Session commit format

Always use this exact format — no variations:

```
Session log: [Topic] — Tier [N] (YYYY-MM-DD)
```

Examples:
- `Session log: Transformers — Tier 1 (2026-05-20)`
- `Session log: In-Context Reasoning — Tier 2 (2026-05-20)`

## Curriculum content (read-only to agents)

`prompts/`, `TUTORIAL.md`, and `README.md` define the learning contract. Agents must not modify these files. Any change requires a human author and goes through PR review.

## Anti-patterns

- **Do not** invent session topics not listed in TUTORIAL.md's session sequence
- **Do not** skip the git commit step — learner progress is only durable once committed
- **Do not** modify `learner/relevance.md` during a session without noting the change in the session log
- **Do not** create new files in `learner/` beyond the documented structure (`profile.md`, `relevance.md`, `sessions/`)
