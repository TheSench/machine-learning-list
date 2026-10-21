# Harness Design 1 — Context as State (Side Track)

You are a knowledgeable ML instructor. Teach me **how an agent harness should manage what enters the model's context**, using LongHarness as the case study, in a focused, interactive session at Tier 3 depth. This is the first of four sessions in the Harness Design side track, built from papers published in October 2026.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions and Tier 3 through session #38. That means I understand:
- Transformers, attention, and context-window limits
- RAG, dense and sparse retrieval (BM25), chunking failure modes
- ReAct-style tool use, function calling, and code actions
- TextGrad, GEPA, and the elicitation gap: scaffolding changes can close capability gaps without retraining
- Benchmarks, contamination, LLM-as-judge weaknesses, and how to read ablations critically

I have not read LongHarness or any of the other October 2026 harness papers.

## Session focus

A harness is everything around a frozen model: prompts, tools, memory, control loop (Harness^2, covered in session 2, defines it as "Agent = Model + Harness"). This session asks one question: when an agent reasons over a corpus far larger than its context window, what should persist between turns — the growing interaction history, or explicit, structured state? LongHarness argues for explicit evidence and conclusion state that coevolve. Its central claim is supported but confounded, and taking it apart is half the lesson.

## Resources for this session

- "LongHarness: Advancing Agentic Reasoning over 100M-Token Corpora via Stateful Evidence" (Huang et al., Fudan University / Shanghai AI Laboratory et al., October 2026) — https://arxiv.org/abs/2610.13075

## Teaching objectives

By the end of this session I should be able to:
- Name and define the two failure modes — unbounded exploration and evidence-state drift — and explain how each feeds the other
- Describe LongHarness's persistent state: the EvidenceBank and its entry lifecycle, the Conclusion State (established / hypotheses / open), and the action contract that governs them
- Explain why supersede/retract beats append-only evidence, using the −10.0 point V2 ablation and the Codex case study
- Explain how an explicit `open` gaps list works as a stopping criterion, and cite the turn-count evidence
- Explain why state that exists but is not prompted for goes underused (the gap-guidance instructions ablation)
- Identify the interface confound in the headline comparison, and design an experiment that isolates state management from tool interface
- Apply the pattern: design the evidence/conclusion state for a question-answering agent over a large document corpus in my own domain

## How to run this session

1. Start with "here's what you know from Tiers 1–3 — here's what this side track adds" framing. The bridge is the elicitation gap from Tier 3 Tool Use and Scaffolding: this paper holds the model fixed and changes only the harness.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what this side track is for.
3. Flag when a result rests on weak evidence. This side track trains critical reading of harness claims: confounds, missing ablations, small n, single runs, cost not reported. Treat finding these as a core skill, not an aside.
4. Check my understanding after each major concept before moving on — ask me to explain it back or predict what happens if something changes. Don't front-load all the material and save checking for the quiz at the end.
5. At the end, give me a 3-question quiz that tests understanding at this depth.

Additional rules for this side track:
- **These papers were published in October 2026, after your training data. Teach ONLY from the Source notes below. Do not add mechanisms, numbers, or claims that are not in the notes; if the learner asks something the notes don't cover, say so plainly.**
- The unifying principle across all four sessions: **what enters the model's context should be designed, not accumulated.** Name it at the start and return to it at the end.
- Include an applied exercise grounded in my domain (see my learner profile): have me design the evidence and conclusion state for a question-answering agent over a large document corpus in that domain — what counts as an evidence entry, what triggers a supersede vs. retract, what goes in `open`, and what the controller can and cannot validate mechanically.

Check in with me after each major concept rather than delivering everything in one pass.

---

## Source notes

Condensed from a full-text read of arXiv 2610.13075v1 (9 Oct 2026), covering Sec. 2–3 and Appendices A–E. Math symbols did not survive text extraction, so equations are paraphrased from surrounding prose. **The paper has no Limitations section** — every limitation below is reviewer critique unless marked as acknowledged by the authors.

### 1. Problem framing

Task: corpus-level long-context reasoning — questions whose evidence is scattered across collections larger than the context window (OfficeQA Pro is ~100M tokens).

Three levels of evidence work (Sec. 1): **L1 Retrieval** (locating passages, rejecting distractors), **L2 Editing** (selecting, reconciling, revising), **L3 Transformation** (turning evidence into an answer).

Core diagnosis: existing harnesses keep the evidence-to-conclusion mapping *implicit* — in session history, free-form notes, or transient reasoning.

Two failure modes, in the paper's words:
- **Unbounded exploration:** "retrieval continues without resolving decision-relevant information gaps, potentially exhausting the interaction budget."
- **Evidence-state drift:** "previously acquired evidence or later corrections become disconnected from subsequent reasoning, leaving the final decision based on stale or incomplete evidence."

They are coupled: drift obscures which needs are already resolved, which drives more retrieval, which buries evidence deeper.

### 2. Mechanism

**Persistent state, separate from full history (Sec. 2.1, App. B.3):**
- **EvidenceBank** — atomic, source-linked statements with immutable IDs. Lifecycle: candidate → active → superseded or retracted. Inactive entries stay in the revision record but cannot be cited.
- **Conclusion State** — three lists:
  - `established`: claims that must cite active evidence
  - `hypotheses`: supported but unsettled interpretations, also citing active evidence
  - `open`: concrete missing information that could change the answer
- **Environment state** — registered source spans (character offsets) and budget counters.

**Action space (Table 5, one operation per turn):**

| Action | Contract |
|---|---|
| `search` | BM25 or regex, optionally doc/section-scoped. Snippets are explicitly *not citable*. |
| `read` | Bounded to 16,384 tokens. Returns text and registers source-span IDs (the only way to mint citable references). |
| `EvidenceBank.upsert` | Batch admission; each statement validated separately, so partial acceptance is possible. |
| `revise(id, replacement \| null)` | Replacement supersedes; null retracts. No in-place edits. |
| `compute` | One deterministic expression plus the evidence IDs it uses. |
| `final` | Answer plus active evidence IDs. |

**Coevolution (Sec. 2.2):** evidence acquisition is driven by gaps in the current conclusions; conclusions are revised from the active evidence. One policy plays both roles — a single ReAct agent, no multi-agent split.

**Algorithm 1 (App. B.5), paraphrased:**

```
init env, doc_map, state S = (E=∅, C=∅, H=[])
while budget allows and env is up:
  (a, ΔC) = π(q, doc_map, S, budget)
  if a fails protocol / source-reference / budget checks:
      obs = validation feedback          # persistent state untouched
  else:
      if a not in {upsert, revise}: C = merge(C, ΔC)   # merge before executing
      obs = env.exec(a)                  # evidence mutations update conclusions on a LATER turn
  H += (reasoning, a, obs); update budget
  if obs is an accepted final answer: return answer + resolved refs
return ⊥
```

**Contract details (App. B.3, B.4):**
- Conclusion updates are partial: a supplied list replaces the old one; omitted lists are kept.
- Evidence created on a turn becomes citable only on the *next* turn.
- Retracting evidence only *flags* dependent conclusions; they are never auto-rewritten.
- The controller checks that references exist. It does **not** check that a statement is faithful to its source, nor that `compute` operands match source values (acknowledged by the authors).
- Full history is kept with no compaction; an over-large request ends the episode as `model_request_failed`.
- The state block (EvidenceBank, Conclusion State, remaining budgets) is appended after the history on every request.

**Prompt rules (App. C.3), quoted:**
- "Select the unresolved gap whose resolution is most likely to change the answer."
- "Search for the missing distinction, not only for the question topic."
- "Continue only while resolving a remaining unresolved gap could change the result."
- "Evidence relevance alone is not support."

### 3. Results

**Setup:** OfficeQA Pro V1 (133 questions, 697 Treasury documents, ~100M tokens); OfficeQA Pro V2 (90 questions, 1,435 documents, composite questions); AA-LCR-1.1 (100); LongBench v2 Long (108). Backbones GLM-5.3-Flash and Qwen3.8-Flash. Budgets: LongHarness 200 steps / 60 searches / 1M cumulative read tokens; Claude Code and Codex 200 turns / 200 tool calls; RLM 30 iterations.

**Table 1 — GLM-5.3-Flash, exact match:**

| | OfficeQA V1 | OfficeQA V2 | AA-LCR | LongBench Long | Avg |
|---|---|---|---|---|---|
| Direct (BM25 into 256K) | 15.8 | 4.4 | – | – | – |
| Codex | 46.6 | 42.2 | 77.0 | 69.4 | 58.8 |
| Claude Code | 48.1 | 35.6 | 79.0 | 63.0 | 56.4 |
| RLM | 45.1 | 38.9 | 56.0 | 60.2 | 50.0 |
| LongHarness | 60.2 | 61.1 | 84.0 | 75.9 | 70.3 |

Qwen3.8-Flash: LongHarness 61.7 (V1) / 51.1 (V2), vs. Claude Code 53.4 on V1 and Codex 50.0 on V2 — **only +1.1 on V2**. Best direct model (Kimi-K3): 23.2 / 4.8.

**Ablations (Table 2, GLM, V1 / V2; full = 60.2 / 61.1):**

| Variant | V1 / V2 | Drop |
|---|---|---|
| w/o Persistent States (history only) | 55.6 / 53.3 | −4.5 / −7.8 |
| w/o Coevolution (bank kept, no Conclusion State) | 54.9 / 51.7 | −5.3 / −9.4 |
| Naive append-only evidence | 56.4 / 51.1 | −3.8 / **−10.0** |
| w/o gap-guided search *instructions* (both states kept) | 55.6 / 53.3 | −4.5 / −7.8 |
| Free-text working notes instead of structured conclusions | 53.4 / 53.3 | −6.8 / −7.8 |

All five ablations lose more on V2 (composite questions). The largest V2 drop is append-only evidence: revise/supersede matters most when values must be reconciled.

**Stage audit (Table 3, GLM, V2; LLM judge GPT-5.6-Luna):** LongHarness Retrieval 87.8 / Editing 87.3 / Transformation 79.7, vs. best other harness per stage 76.7 (Codex) / 84.6 (Claude Code) / 70.4 (Codex).

**Turn counts (Fig. 3; the text mislabels it "Figure 4"), median V1 → V2:** LongHarness 22 → 30; Claude Code 21 → 116; Codex 19 → 43. Codex exhausted its turn budget on 3.8% of V1 and 21.1% of V2 questions.

**Three runs (Table 9, GLM), mean ± sd:** LongHarness 59.9 ± 0.43 (V1), 59.6 ± 1.28 (V2); Codex V2 41.1 ± 4.0; Claude Code V2 32.6 ± 4.2. Higher and more stable.

**Case study (App. E):** Codex makes 103 consecutive backward reads, notices that 4100 should be corrected to 4400, but keeps the stale result: 4958.09 vs. reference 4962.46. Relative error 0.088% — passes at 5% tolerance, fails exact match. LongHarness answers correctly in 10 actions. This is evidence-state drift observed directly: the correction was seen and never applied.

### 4. Limitations and weak points (reviewer critique unless noted)

- **Interface confound.** LongHarness gets purpose-built tools (document map, sectioned blocks, BM25 and regex, bounded reads, a compute tool). Claude Code and Codex work through shell and file tools over parsed files. **The history-only ablation (55.6 / 53.3) still beats Claude Code on V1 by 7.5 and Codex on V2 by 11.1** — so more than half the margin over those baselines survives with persistent state removed, pointing to tools, prompt, and budgets rather than the state design the paper centers.
- **Off-native backbones.** Claude Code and Codex run on GLM and Qwen models they were not tuned for. Budgets differ (RLM capped at 30 iterations).
- **Small, single-run ablations.** One V2 question is worth 1.1 points; one V1 question about 0.75. Most ablation drops are 5–9 questions, with no variance. Three variants land on the identical 53.3 on V2, so ablations cannot be ranked against each other.
- **No cost reporting.** No tokens, dollars, or latency — only turn counts. Full history is never compacted, and the frequency of `model_request_failed` is not reported.
- **Weak direct baseline and mixed graders.** Direct gets one BM25 retrieval into 256K. Direct AA-LCR numbers come from Artificial Analysis; harness AA-LCR numbers were graded by the authors with GPT-5.6-Luna.
- **Stage audit** is an LLM judge applied only to incorrect episodes; correct episodes pass by protocol.
- **Validation gaps (acknowledged by authors):** no fidelity check on statements or compute operands; conclusions citing retracted evidence are only flagged.
- **Narrow corpus:** OfficeQA is one domain (Treasury numeric tables), small samples.

### 5. Practitioner takeaways

1. **Split facts from inferences in explicit, persistent state.** Source-linked evidence separate from conclusions. Removing the Conclusion State costs 5.3 / 9.4; free-text notes cost 6.8 / 7.8 (Table 2). A notes scratchpad is not equivalent.
2. **Make corrections first-class.** Immutable IDs plus supersede/retract, never append-only. Append-only costs 10.0 on V2; the case study shows a correction noticed but never applied.
3. **Turn the stopping criterion into data.** Keep an `open` gaps list and instruct the agent to continue only while a gap could change the answer. Median turns rise 22 → 30 on V2 vs. 21 → 116 for Claude Code. Removing only the gap-guidance *instructions* costs 4.5 / 7.8 — state that exists but is never prompted for goes underused.
4. **Enforce provenance at the controller.** Only `read` mints citable references; snippets are not evidence; new evidence is citable one turn later; arithmetic goes through a compute tool that takes evidence IDs. Mechanical checks are cheap even though semantic fidelity stays with the model.
5. **Budget the expensive resource directly** — total tokens read and searches made, not just turns (Table 7). **Caveat:** measure your tool interface separately; the paper's own ablation suggests good search/read tools carry much of the gain.

### 6. Discussion questions

1. The history-only ablation (55.6 V1) still beats Claude Code (48.1) on the same backbone. What does that say about where the 12-point headline gain comes from? What experiment would isolate state management from the tool interface? (A good answer: a 2×2 — {LongHarness tools, shell/file tools} × {persistent state, history only} on the same backbone and budget, with multiple runs, so the interaction term is visible.)
2. Revising evidence only *flags* dependent conclusions instead of rewriting them. Construct a scenario where this still produces evidence-state drift. Then argue for or against cascading invalidation, weighing cost and the risk of over-retraction.
3. Removing the gap-guided search instructions keeps both states but loses as much as removing persistent state entirely (55.6 / 53.3 in both rows). What does this imply about whether state structure or prompting drives behavior? How would you test whether the finding transfers to a stronger backbone?
