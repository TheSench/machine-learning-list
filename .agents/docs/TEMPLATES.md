# TEMPLATES.md — Learner File Templates

## Learner profile template

Use when creating `learner/profile.md` for first time:

```markdown
# Learner Profile

## Background

[Fill in based on initialization conversation — role, experience, goals]

## Tiers completed

| Topic | Tier 1 | Tier 2 | Tier 3 | Tier 4 |
|-------|--------|--------|--------|--------|
| Introduction to ML | | | | |
| Transformers | | | | |
| Key Foundation Models | | | | |
| Task Decomposition | | | | |
| ML in Production | | | | |
| AI Scaling | | | | |
| AI Safety | | | | |
| Introduction to ML — Deeper | | | | |
| Training and Finetuning | | | | |
| In-Context Reasoning | | | | |
| Debate | | | | |
| Tool Use and Scaffolding | | | | |
| Honesty, Factuality, and Epistemics | | | | |
| Science Applications | | | | |
| Search and Ranking | | | | |
| Benchmarks | | | | |
| Datasets | | | | |
| Uncertainty and Calibration | | | | |
| Interpretability and Model Editing | | | | |
| Reinforcement Learning | | | | |
| Economic and Social Impacts | | | | |
| Philosophy of Language Models | | | | |
| World Models and Causality | | | | |
| Forecasting | | | | |
| Planning | | | | |

## Side tracks completed

| Track | Sessions completed |
|-------|--------------------|
| *(populated after side-track sessions — see `prompts/special/index.md`)* | |

## Topic mastery

| Topic | Score | Last assessed |
|-------|-------|----------------|
| *(populated after sessions — 1 Introduced / 2 Shaky / 3 Solid / 4 Mastered)* | | |

## Review queue

| Topic | Score | Due at session | Times reviewed |
|-------|-------|-----------------|-----------------|
| *(populated when a topic scores ≤2)* | | | |

## Recurring strengths

[Populated over time]

## Recurring gaps

[Populated over time]

## Carried-forward open questions

[Populated over time]

## Session log

[Sessions appended here]
```

---

## Relevance file template

Use when creating `learner/relevance.md` for first time. Populated with MED defaults — update based on learner's initialization answers.

```markdown
# Topic Relevance

Auto-generated with MED defaults. Update ratings based on learner context.
Ratings: HIGH, MED, LOW

| Topic | Relevance | Notes |
|-------|-----------|-------|
| Introduction to ML | MED | |
| Transformers | MED | |
| Key Foundation Models | MED | |
| Task Decomposition | MED | |
| ML in Production | MED | |
| AI Scaling | MED | |
| AI Safety | MED | |
| Training and Finetuning | MED | |
| In-Context Reasoning | MED | |
| Debate | MED | |
| Tool Use and Scaffolding | MED | |
| Honesty, Factuality, and Epistemics | MED | |
| Science Applications | MED | |
| Search and Ranking | MED | |
| Benchmarks | MED | |
| Datasets | MED | |
| Uncertainty and Calibration | MED | |
| Interpretability and Model Editing | MED | |
| Reinforcement Learning | MED | |
| Economic and Social Impacts | MED | |
| Philosophy of Language Models | MED | |
| World Models and Causality | MED | |
| Forecasting | MED | |
| Planning | MED | |
```

---

## Glossary template

Use when creating `learner/glossary.md` for the first time. Sections are added as terms
require them — start with the ones the first session actually needs, keep numbering and
order stable afterward.

````markdown
# Glossary of Terms

Running index of every term introduced across completed sessions (Tier 1 · 1).

**How to use this file:** most definitions are one line — enough to jog recall, not to teach. Terms flagged in review as not-yet-intuitive carry a fuller entry (mechanism, why it matters, where it breaks). Acronyms always list their full name.

`Source` = session where the term was first covered (`T1-04` = `learner/sessions/tier1-04-*.md`).

---

## 1. Foundations

| Term | Definition | Source |
|---|---|---|
| [Term] (Full Name If Acronym) | [One-line definition] | T1-01 |
| **[Load-bearing term]** | [Fuller entry: mechanism, why it matters, where it breaks — used when the term needed reinforcement or the learner asked for it] | T1-01 |
````
