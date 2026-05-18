# ML Tutorial — Agent Entry Point

`@` this file to start or resume your ML tutorial session.

---

## What the agent should do on load

1. **Read** `prompts/learner-profile.md` — determines where the learner is and how they learn
2. **Read** `prompts/learner-relevance.md` — determines how deep to go on each topic
3. **Determine the next session** using the [Session Sequence](#session-sequence) below and the `Tiers completed` table in the learner profile
4. **Confirm with the learner** which session to run (or let them pick a specific one)
5. **Load** the corresponding prompt file from `prompts/`
6. **Run the session** following `prompts/CLAUDE.md` instructor instructions
7. **Update** `prompts/learner-profile.md` at the end of the session

---

## Depth calibration

Before starting a session, cross-reference the topic against `prompts/learner-relevance.md`.

- **High relevance** — go deeper than the prompt file's default. Spend extra time on production implications. Ask follow-up questions that tie the material to building agentic systems.
- **Medium relevance** — follow the prompt file as written. Connect concepts to the learner's context where natural.
- **Low relevance** — cover the core concepts at a lighter pace. Compress or skip peripheral details. Make note of what is being skipped and why, so the learner can return if their context changes.

---

## Progress tracking

Progress is stored in `prompts/learner-profile.md`. The `Tiers completed` table is the canonical record of what has been completed. A session is complete when its session log entry has been written.

### Learner profile folder structure

The learner profile starts as a single file. When the session log grows beyond ~15 sessions, split it:

```
prompts/
  learner-profile.md          ← keep: background, tiers table, recurring strengths/gaps, open questions
  sessions/
    tier1-01-intro-to-ml.md   ← move: individual session logs go here
    tier1-02-transformers.md
    ...
```

When splitting, update `learner-profile.md` to add a `## Session index` section with links to individual session files. The CLAUDE.md instructor instructions write new sessions to `prompts/sessions/` once that folder exists; otherwise they append to `prompts/learner-profile.md`.

**To trigger the split:** if `prompts/sessions/` does not exist and the session log in `learner-profile.md` contains more than 15 entries, create the folder, move each session log entry to its own file, and update the profile.

---

## Session sequence

Work through all sessions at one tier before advancing to the next. Within a tier, follow the order below.

Sessions marked `[HIGH]`, `[MED]`, or `[LOW]` reflect relevance for this learner's context (see `prompts/learner-relevance.md`). These labels affect depth, not whether to complete the session — complete all sessions in order.

### Tier 1 — Foundations

| # | File | Topic | Relevance |
|---|------|-------|-----------|
| 1 | `prompts/tier1/01-intro-to-ml.md` | Introduction to Machine Learning | MED |
| 2 | `prompts/tier1/02-transformers.md` | Transformers | MED |
| 3 | `prompts/tier1/03-key-foundation-models.md` | Key Foundation Model Architectures | MED |
| 4 | `prompts/tier1/04-task-decomposition.md` | Task Decomposition | HIGH |
| 5 | `prompts/tier1/05-production-deployment.md` | ML in Production | HIGH |
| 6 | `prompts/tier1/06-ai-scaling.md` | AI Scaling | MED |
| 7 | `prompts/tier1/07-ai-safety.md` | AI Safety | MED |

### Tier 2 — Breadth

| # | File | Topic | Relevance |
|---|------|-------|-----------|
| 8 | `prompts/tier2/01-intro-to-ml.md` | Introduction to ML — Deeper | LOW |
| 9 | `prompts/tier2/02-transformers.md` | Transformers — Deeper | MED |
| 10 | `prompts/tier2/03-key-foundation-models.md` | Key Foundation Models — Deeper | MED |
| 11 | `prompts/tier2/04-training-finetuning.md` | Training and Finetuning | LOW |
| 12 | `prompts/tier2/05-in-context-reasoning.md` | In-Context Reasoning | HIGH |
| 13 | `prompts/tier2/06-task-decomposition.md` | Task Decomposition — Deeper | HIGH |
| 14 | `prompts/tier2/07-debate.md` | Debate | LOW |
| 15 | `prompts/tier2/08-tool-use-scaffolding.md` | Tool Use and Scaffolding | HIGH |
| 16 | `prompts/tier2/09-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics | HIGH |
| 17 | `prompts/tier2/10-science.md` | Science Applications | LOW |
| 18 | `prompts/tier2/11-search-ranking.md` | Search and Ranking | HIGH |
| 19 | `prompts/tier2/12-production-deployment.md` | ML in Production — Deeper | HIGH |
| 20 | `prompts/tier2/13-benchmarks.md` | Benchmarks | MED |
| 21 | `prompts/tier2/14-datasets.md` | Datasets | LOW |
| 22 | `prompts/tier2/15-uncertainty-calibration.md` | Uncertainty and Calibration | MED |
| 23 | `prompts/tier2/16-interpretability-model-editing.md` | Interpretability and Model Editing | LOW |
| 24 | `prompts/tier2/17-reinforcement-learning.md` | Reinforcement Learning | LOW |
| 25 | `prompts/tier2/18-ai-scaling.md` | AI Scaling — Deeper | MED |
| 26 | `prompts/tier2/19-ai-safety.md` | AI Safety — Deeper | MED |
| 27 | `prompts/tier2/20-economic-social-impacts.md` | Economic and Social Impacts | LOW |
| 28 | `prompts/tier2/21-philosophy.md` | Philosophy of Language Models | LOW |

### Tier 3 — Depth

| # | File | Topic | Relevance |
|---|------|-------|-----------|
| 29 | `prompts/tier3/01-transformers.md` | Transformers — Research Depth | LOW |
| 30 | `prompts/tier3/02-key-foundation-models.md` | Key Foundation Models — Research Depth | LOW |
| 31 | `prompts/tier3/03-training-finetuning.md` | Training and Finetuning — Research Depth | LOW |
| 32 | `prompts/tier3/04-in-context-reasoning.md` | In-Context Reasoning — Research Depth | HIGH |
| 33 | `prompts/tier3/05-task-decomposition.md` | Task Decomposition — Research Depth | HIGH |
| 34 | `prompts/tier3/06-debate.md` | Debate — Research Depth | LOW |
| 35 | `prompts/tier3/07-tool-use-scaffolding.md` | Tool Use and Scaffolding — Research Depth | HIGH |
| 36 | `prompts/tier3/08-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics — Research Depth | HIGH |
| 37 | `prompts/tier3/09-science.md` | Science Applications — Research Depth | LOW |
| 38 | `prompts/tier3/10-forecasting.md` | Forecasting | LOW |
| 39 | `prompts/tier3/11-search-ranking.md` | Search and Ranking — Research Depth | HIGH |
| 40 | `prompts/tier3/12-benchmarks.md` | Benchmarks — Research Depth | MED |
| 41 | `prompts/tier3/13-datasets.md` | Datasets — Research Depth | LOW |
| 42 | `prompts/tier3/14-world-models-causality.md` | World Models and Causality | LOW |
| 43 | `prompts/tier3/15-uncertainty-calibration.md` | Uncertainty and Calibration — Research Depth | MED |
| 44 | `prompts/tier3/16-interpretability-model-editing.md` | Interpretability and Model Editing — Research Depth | LOW |
| 45 | `prompts/tier3/17-reinforcement-learning.md` | Reinforcement Learning — Research Depth | LOW |
| 46 | `prompts/tier3/18-ai-scaling.md` | AI Scaling — Research Depth | MED |
| 47 | `prompts/tier3/19-ai-safety.md` | AI Safety — Research Depth | HIGH |
| 48 | `prompts/tier3/20-economic-social-impacts.md` | Economic and Social Impacts — Research Depth | LOW |

### Tier 4+ — Specialist (optional)

| # | File | Topic | Relevance |
|---|------|-------|-----------|
| 49 | `prompts/tier4/01-transformers.md` | Transformers — Specialist | LOW |
| 50 | `prompts/tier4/02-key-foundation-models.md` | Key Foundation Models — Specialist | LOW |
| 51 | `prompts/tier4/03-training-finetuning.md` | Training and Finetuning — Specialist | LOW |
| 52 | `prompts/tier4/04-in-context-reasoning.md` | In-Context Reasoning — Specialist | MED |
| 53 | `prompts/tier4/05-task-decomposition.md` | Task Decomposition — Specialist | HIGH |
| 54 | `prompts/tier4/06-debate.md` | Debate — Specialist | LOW |
| 55 | `prompts/tier4/07-tool-use-scaffolding.md` | Tool Use and Scaffolding — Specialist | HIGH |
| 56 | `prompts/tier4/08-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics — Specialist | HIGH |
| 57 | `prompts/tier4/09-science.md` | Science Applications — Specialist | LOW |
| 58 | `prompts/tier4/10-forecasting.md` | Forecasting — Specialist | LOW |
| 59 | `prompts/tier4/11-search-ranking.md` | Search and Ranking — Specialist | HIGH |
| 60 | `prompts/tier4/12-benchmarks.md` | Benchmarks — Specialist | LOW |
| 61 | `prompts/tier4/13-world-models-causality.md` | World Models and Causality — Specialist | LOW |
| 62 | `prompts/tier4/14-planning.md` | Planning — Specialist | MED |
| 63 | `prompts/tier4/15-uncertainty-calibration.md` | Uncertainty and Calibration — Specialist | MED |
| 64 | `prompts/tier4/16-interpretability-model-editing.md` | Interpretability and Model Editing — Specialist | LOW |
| 65 | `prompts/tier4/17-reinforcement-learning.md` | Reinforcement Learning — Specialist | LOW |
| 66 | `prompts/tier4/18-ai-scaling.md` | AI Scaling — Specialist | LOW |
| 67 | `prompts/tier4/19-ai-safety.md` | AI Safety — Specialist | MED |
| 68 | `prompts/tier4/20-economic-social-impacts.md` | Economic and Social Impacts — Specialist | LOW |
| 69 | `prompts/tier4/21-philosophy.md` | Philosophy — Specialist | LOW |

---

## How the tiers-completed table maps to session numbers

The `Tiers completed` table in `learner-profile.md` uses topic names that match the session sequence above. To find the next session:

1. Find the last completed session in the table (read across tiers in order)
2. The next session is the immediately following row in the sequence above
3. If no sessions are completed, start with session 1

When updating `learner-profile.md` after a session, add the topic name to the `Tiers completed` table in the row for the appropriate tier, with the date.
