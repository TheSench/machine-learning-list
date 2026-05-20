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

Use exact format — no variations:

```
Session log: [Topic] — Tier [N] (YYYY-MM-DD)
```

Examples:
- `Session log: Transformers — Tier 1 (2026-05-20)`
- `Session log: In-Context Reasoning — Tier 2 (2026-05-20)`

## Curriculum content (read-only to agents)

`prompts/`, `TUTORIAL.md`, `README.md` define learning contract. Agents must not modify. Changes require human author + PR review.

## Anti-patterns

- **Do not** invent session topics not in TUTORIAL.md session sequence
- **Do not** skip git commit — progress only durable once committed
- **Do not** modify `learner/relevance.md` during session without noting change in session log
- **Do not** create new files in `learner/` beyond documented structure (`profile.md`, `relevance.md`, `sessions/`)
