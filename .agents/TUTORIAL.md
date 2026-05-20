# ML Tutorial — Agent Entry Point

`@` this file to start or resume your ML tutorial session.

---

## What the agent should do on load

### Step 1 — Load context (do this silently, without narrating)

Read both files:
- `learner/profile.md`
- `learner/relevance.md`

On missing file (error or empty result), treat as first-time learner:
- Missing `learner/profile.md` → no sessions completed, no background known. Proceed to [initialization](#initialization) instead of Steps 2–3.
- Missing `learner/relevance.md` → treat all topics as MED until file created.

Attempt read and branch on result; don't check existence first.

### Initialization

Run only when `learner/profile.md` doesn't exist (first session ever).

1. Ask learner short background questions:
   - What's your professional background? (e.g. software engineering, product, research)
   - How much have you worked with ML systems hands-on?
   - Is there a particular area of ML you're most curious about or will use most?
2. Create `learner/profile.md` using template in [`.agents/docs/TEMPLATES.md`](.agents/docs/TEMPLATES.md).
3. If `learner/relevance.md` also missing, create it using relevance file template in [`.agents/docs/TEMPLATES.md`](.agents/docs/TEMPLATES.md) with MED for all topics. Note it was auto-generated and can be customized.
4. Proceed to Step 2 (start session 1).

### Step 2 — Determine next session

Using `Tiers completed` table in learner profile + [Session Sequence](#session-sequence), identify:
- Last completed session (topic + tier)
- Next session (file path + topic + relevance rating)

### Step 3 — Show progress summary and begin

Show brief progress summary, then immediately start next session without waiting for confirmation.

**Progress summary format:**

```
**Progress so far:** [N] of 69 sessions complete.
Last completed: [Topic] — Tier [N] ([date])

**Starting:** [Topic] — Tier [N] ([HIGH / MED / LOW] relevance)
[One sentence on what this session covers and why it matters for this learner's context.]
```

### Step 4 — Run the session

1. Load prompt file from `prompts/`
2. Run session
3. Apply depth calibration from `learner/relevance.md` for topic

### Step 5 — Update the learner profile

Update `learner/profile.md`. Add entry under `## Session log`:

```markdown
### [Topic] — Tier [N] · [YYYY-MM-DD]

**Covered:** [1–2 sentence summary of what was taught]

**Strengths:** [Concepts the learner grasped quickly or explained back correctly]

**Gaps / needs reinforcement:** [Concepts that needed multiple attempts, were answered incorrectly in the quiz, or the learner flagged as uncertain]

**Open questions:** [Questions raised that weren't fully resolved — carry these forward]

**Notes:** [Anything else relevant: learning style observations, areas of strong interest, analogies that landed well]
```

Update top-level profile sections if learner background or preferences were revealed. Don't ask for permission — just write the file.

#### Post-session follow-up questions

Answer follow-up questions normally. Evaluate if exchange revealed anything worth tracking:

- Gap resolved → update **Gaps / needs reinforcement**
- New open question → add to **Open questions** or **Carried-forward open questions**
- Concept grasped more deeply → note under **Strengths**
- Illuminating observation → add **Extended discussion** paragraph in session log

Only write file if something worth carrying forward.

#### Update progress chart

After updating `learner/profile.md`, regenerate `learner/progress.md` to reflect the new session count. The file has two sections:

**Header:** `**[N] of 69 sessions complete** · Updated [YYYY-MM-DD]`

Count total sessions by summing entries in the `Tiers completed` table.

**Overview chart** (`xychart-beta`): bar chart with four bars — one per tier — showing how many sessions are complete in each. Tier totals are always 7 / 21 / 20 / 21.

```
xychart-beta
    title "Sessions Completed by Tier"
    x-axis ["Tier 1 (7)", "Tier 2 (21)", "Tier 3 (20)", "Tier 4 (21)"]
    y-axis "Sessions" 0 --> 21
    bar [<t1_done>, <t2_done>, <t3_done>, <t4_done>]
```

**Current tier chart** (`graph LR`): show all sessions in the active tier (the lowest tier not yet fully complete) as a linear chain of nodes. Use these classes:

- `done` (green `#2d6a4f`) — completed sessions
- `next` (orange `#f4a261`) — the immediately upcoming session (first incomplete)
- `pending` (gray `#dee2e6`) — remaining sessions after next

Node IDs: `T<tier>_<position>` (e.g., `T2_5`). Labels: short topic name (2 lines max). Connect all nodes left-to-right with `-->`.

If Tier 4 is complete, replace the current tier chart with a completion message.

The session order within each tier follows the [Session sequence](#session-sequence) table.

Commit changes:

```
git add learner/profile.md learner/relevance.md learner/progress.md
git commit -m "Session log: [Topic] — Tier [N] ([YYYY-MM-DD])"
```

Only stage modified files. Don't ask — just commit.

### Step 6 — Prompt to start the next session

After saving progress, display exactly content inside `<closing_message>`, nothing after. Don't include `<closing_message>` tags.

<closing_message>
Session saved. To continue, open a new conversation and send:

```
Continue
```
</closing_message>

Only `Continue` inside code block so learner can copy-paste directly.

---

## Depth calibration

Calibrate on two axes before session:

**Learner history** (`learner/profile.md`): skip mastered concepts, dwell on gaps, connect to prior strengths, surface open questions, match explanation style. If no session log yet, check background for stated strengths/gaps.

**Topic relevance** (`learner/relevance.md`): HIGH → go deeper, focus on production implications; MED → follow prompt as written; LOW → core concepts only, compress peripheral details, note what was skipped.

---

## Templates

See [`.agents/docs/TEMPLATES.md`](.agents/docs/TEMPLATES.md) for learner profile template and relevance file template.

---

## Progress tracking

Progress stored in `learner/profile.md`. `Tiers completed` table is canonical record. Session complete when session log entry written.

### Learner profile folder structure

Profile starts as single file. When session log exceeds ~15 sessions, split it:

```
learner/
  profile.md                  ← keep: background, tiers table, recurring strengths/gaps, open questions
  sessions/
    tier1-01-intro-to-ml.md   ← move: individual session logs go here
    tier1-02-transformers.md
    ...
```

When splitting, update `learner/profile.md` to add `## Session index` with links to session files. Write new sessions to `learner/sessions/` once folder exists; otherwise append to `learner/profile.md`.

---

## Session sequence

Complete all sessions at one tier before advancing. Within tier, follow order below. Relevance from `learner/relevance.md` affects depth, not whether to complete.

### Tier 1 — Foundations

| # | File | Topic |
|---|------|-------|
| 1 | `prompts/tier1/01-intro-to-ml.md` | Introduction to Machine Learning |
| 2 | `prompts/tier1/02-transformers.md` | Transformers |
| 3 | `prompts/tier1/03-key-foundation-models.md` | Key Foundation Model Architectures |
| 4 | `prompts/tier1/04-task-decomposition.md` | Task Decomposition |
| 5 | `prompts/tier1/05-production-deployment.md` | ML in Production |
| 6 | `prompts/tier1/06-ai-scaling.md` | AI Scaling |
| 7 | `prompts/tier1/07-ai-safety.md` | AI Safety |

### Tier 2 — Breadth

| # | File | Topic |
|---|------|-------|
| 8 | `prompts/tier2/01-intro-to-ml.md` | Introduction to ML — Deeper |
| 9 | `prompts/tier2/02-transformers.md` | Transformers — Deeper |
| 10 | `prompts/tier2/03-key-foundation-models.md` | Key Foundation Models — Deeper |
| 11 | `prompts/tier2/04-training-finetuning.md` | Training and Finetuning |
| 12 | `prompts/tier2/05-in-context-reasoning.md` | In-Context Reasoning |
| 13 | `prompts/tier2/06-task-decomposition.md` | Task Decomposition — Deeper |
| 14 | `prompts/tier2/07-debate.md` | Debate |
| 15 | `prompts/tier2/08-tool-use-scaffolding.md` | Tool Use and Scaffolding |
| 16 | `prompts/tier2/09-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics |
| 17 | `prompts/tier2/10-science.md` | Science Applications |
| 18 | `prompts/tier2/11-search-ranking.md` | Search and Ranking |
| 19 | `prompts/tier2/12-production-deployment.md` | ML in Production — Deeper |
| 20 | `prompts/tier2/13-benchmarks.md` | Benchmarks |
| 21 | `prompts/tier2/14-datasets.md` | Datasets |
| 22 | `prompts/tier2/15-uncertainty-calibration.md` | Uncertainty and Calibration |
| 23 | `prompts/tier2/16-interpretability-model-editing.md` | Interpretability and Model Editing |
| 24 | `prompts/tier2/17-reinforcement-learning.md` | Reinforcement Learning |
| 25 | `prompts/tier2/18-ai-scaling.md` | AI Scaling — Deeper |
| 26 | `prompts/tier2/19-ai-safety.md` | AI Safety — Deeper |
| 27 | `prompts/tier2/20-economic-social-impacts.md` | Economic and Social Impacts |
| 28 | `prompts/tier2/21-philosophy.md` | Philosophy of Language Models |

### Tier 3 — Depth

| # | File | Topic |
|---|------|-------|
| 29 | `prompts/tier3/01-transformers.md` | Transformers — Research Depth |
| 30 | `prompts/tier3/02-key-foundation-models.md` | Key Foundation Models — Research Depth |
| 31 | `prompts/tier3/03-training-finetuning.md` | Training and Finetuning — Research Depth |
| 32 | `prompts/tier3/04-in-context-reasoning.md` | In-Context Reasoning — Research Depth |
| 33 | `prompts/tier3/05-task-decomposition.md` | Task Decomposition — Research Depth |
| 34 | `prompts/tier3/06-debate.md` | Debate — Research Depth |
| 35 | `prompts/tier3/07-tool-use-scaffolding.md` | Tool Use and Scaffolding — Research Depth |
| 36 | `prompts/tier3/08-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics — Research Depth |
| 37 | `prompts/tier3/09-science.md` | Science Applications — Research Depth |
| 38 | `prompts/tier3/10-forecasting.md` | Forecasting |
| 39 | `prompts/tier3/11-search-ranking.md` | Search and Ranking — Research Depth |
| 40 | `prompts/tier3/12-benchmarks.md` | Benchmarks — Research Depth |
| 41 | `prompts/tier3/13-datasets.md` | Datasets — Research Depth |
| 42 | `prompts/tier3/14-world-models-causality.md` | World Models and Causality |
| 43 | `prompts/tier3/15-uncertainty-calibration.md` | Uncertainty and Calibration — Research Depth |
| 44 | `prompts/tier3/16-interpretability-model-editing.md` | Interpretability and Model Editing — Research Depth |
| 45 | `prompts/tier3/17-reinforcement-learning.md` | Reinforcement Learning — Research Depth |
| 46 | `prompts/tier3/18-ai-scaling.md` | AI Scaling — Research Depth |
| 47 | `prompts/tier3/19-ai-safety.md` | AI Safety — Research Depth |
| 48 | `prompts/tier3/20-economic-social-impacts.md` | Economic and Social Impacts — Research Depth |

### Tier 4+ — Specialist (optional)

| # | File | Topic |
|---|------|-------|
| 49 | `prompts/tier4/01-transformers.md` | Transformers — Specialist |
| 50 | `prompts/tier4/02-key-foundation-models.md` | Key Foundation Models — Specialist |
| 51 | `prompts/tier4/03-training-finetuning.md` | Training and Finetuning — Specialist |
| 52 | `prompts/tier4/04-in-context-reasoning.md` | In-Context Reasoning — Specialist |
| 53 | `prompts/tier4/05-task-decomposition.md` | Task Decomposition — Specialist |
| 54 | `prompts/tier4/06-debate.md` | Debate — Specialist |
| 55 | `prompts/tier4/07-tool-use-scaffolding.md` | Tool Use and Scaffolding — Specialist |
| 56 | `prompts/tier4/08-honesty-factuality-epistemics.md` | Honesty, Factuality, and Epistemics — Specialist |
| 57 | `prompts/tier4/09-science.md` | Science Applications — Specialist |
| 58 | `prompts/tier4/10-forecasting.md` | Forecasting — Specialist |
| 59 | `prompts/tier4/11-search-ranking.md` | Search and Ranking — Specialist |
| 60 | `prompts/tier4/12-benchmarks.md` | Benchmarks — Specialist |
| 61 | `prompts/tier4/13-world-models-causality.md` | World Models and Causality — Specialist |
| 62 | `prompts/tier4/14-planning.md` | Planning — Specialist |
| 63 | `prompts/tier4/15-uncertainty-calibration.md` | Uncertainty and Calibration — Specialist |
| 64 | `prompts/tier4/16-interpretability-model-editing.md` | Interpretability and Model Editing — Specialist |
| 65 | `prompts/tier4/17-reinforcement-learning.md` | Reinforcement Learning — Specialist |
| 66 | `prompts/tier4/18-ai-scaling.md` | AI Scaling — Specialist |
| 67 | `prompts/tier4/19-ai-safety.md` | AI Safety — Specialist |
| 68 | `prompts/tier4/20-economic-social-impacts.md` | Economic and Social Impacts — Specialist |
| 69 | `prompts/tier4/21-philosophy.md` | Philosophy — Specialist |
