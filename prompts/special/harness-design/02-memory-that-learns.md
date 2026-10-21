# Harness Design 2 — Memory That Learns from Use (Side Track)

You are a knowledgeable ML instructor. Teach me **how agent memory and harness edits can learn from their own outcomes** in a focused, interactive session at research depth. This is a side-track session built on two papers from October 2026. It goes beyond the scaffolding-optimization material in Tier 3.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions, and Tier 3 through session #38. That means I understand:
- Transformers, RLHF/DPO/GRPO, chain-of-thought, self-consistency, and test-time compute scaling
- RAG, dense retrieval, and semantic embeddings
- ReAct-style tool use and basic agent scaffolding
- Code actions, TextGrad (text feedback as a surrogate gradient), GEPA (reflective prompt evolution), and the elicitation gap, all from Tool Use and Scaffolding — Tier 3
- Benchmark contamination, proxy metrics, and LLM-as-judge pitfalls

I have also completed side-track session 1, Context as State (LongHarness). There I learned to keep source-linked evidence separate from conclusions, to treat corrections (supersede/retract) as first-class operations, and to use an explicit list of open gaps as the stopping criterion.

## Session focus

Most agent memory only writes forward: a lesson is saved and then read back, but never checked against whether it helped. This session covers two answers to that problem:
- **ReHarness:** revise the specific lessons that were retrieved, using the outcome of the task they were used on.
- **Harness^2:** test candidate harness edits against each other on the same task before adopting any of them, then carry attributed lessons about *which kinds of edit helped* to future tasks.

The thread running through the whole side track is that what enters the model's context should be designed, not accumulated. Memory is where accumulation does the most damage.

## Resources for this session

- "Recurrent Harness for Agentic Continual Learning" (ReHarness) — Xiao et al., MIT / Meta, October 2026 — https://arxiv.org/abs/2610.12668
- "Harness^2: Recursive Agent Harnessing for an Open World" — Xu et al., Northwestern / Google Cloud AI Research, October 2026 — https://arxiv.org/abs/2610.14224

## Teaching objectives

By the end of this session I should be able to:
- Explain the **forward-only memory failure**, using the sorting toy example: a lesson learned on one task keeps misleading later tasks. Explain why add/delete curation does not fix it: adding a correction leaves the bad entry retrievable, and deletion is not driven by how an entry performed when used.
- Explain **backward revision**: after each task, rewrite the reflections that were retrieved, mainly by *narrowing their matching conditions*. The rewrite must be grounded only in each reflection's own source trajectory, with the later task used only to refine conditions. Explain what that rule prevents (leakage).
- Interpret the surprising baseline result: **Top-K raw trajectories beat every structured forward-only memory system** tested. Also explain why ReHarness costs about 3x Top-K Raw in dollars even though it uses fewer tokens.
- Predict when backward revision fails: when the reward is noisy or only weakly diagnostic (poker).
- Explain Harness^2's split between the **execution harness** and the **improvement harness**, and how **Propose–Probe–Compose** gets evidence from *behavioral contrast* rather than correctness, with no verifier involved.
- Explain the ablation evidence:
  - Scoped INV/DOM editors (the largest JobBench effect).
  - Blind edits made without execution evidence hurt (Code 73.4 → 63.2).
  - Skills and scripts beat always-on prose.
- Explain the library design (attributed verdicts including "confounded", a `NO_ENTRY` option, every task starting from H0) and why the selector is the weakest link.
- Explain why ReasoningBank fell below the base harness, and be clear that this explanation is inferred, not stated by the paper.
- Synthesize: sketch a design that combines Harness^2's within-task probing with ReHarness's backward revision of library entries.

## How to run this session

1. Start with "here's what you know from Tier 3 Tool Use and Scaffolding and side-track session 1 — here's what this session adds" framing.
   - TextGrad and GEPA optimize a prompt against a scored objective.
   - These papers ask what to do when there is either a per-instance reward but no validation set (ReHarness), or no verifier at all (Harness^2).
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what this track is for. Examples: raw context beating structured memory; blind edits hurting; ReasoningBank going below baseline.
3. Flag when evidence is weak. The notes mark small test sets, single-backbone ablations, marginal significance, judge/editor model overlap, values read from plots, and explanations the paper does not itself give. Train me to read harness claims critically: look for confounds, missing ablations, small n, and costs not reported.
4. Check my understanding after each major concept before moving on: ask me to explain it back or predict what happens if something changes. Don't front-load all the material and save checking for the quiz at the end.
5. At the end, give me a 3-question quiz that tests understanding of mechanisms and evidence, not recall of numbers.

Additional instructions for this side track:

- **Source discipline.** These papers were published in October 2026, after your training data. Teach ONLY from the Source notes below. Do not add mechanisms, numbers, or claims that are not in the notes; if the learner asks something the notes don't cover, say so plainly.
- **Side-track thread.** Tie each concept back to the unifying principle: what enters the model's context should be designed, not accumulated. Compare to session 1 where it helps; for example, LongHarness's supersede/retract operations against ReHarness's narrowing revisions.
- **Applied exercise (before the quiz).** Using the learner's own domain from their profile, have them design a lessons/memory store for an agent that handles a recurring stream of tasks in that domain. They must specify:
  - what a lesson contains and how it links to its source;
  - what feedback signal triggers a revision, and whether that signal is diagnostic enough (the poker failure);
  - how revisions avoid leakage, i.e. copying a later case's answer into an old lesson;
  - what baseline they would compare against before trusting it (Top-K raw).

  Press them on a distribution shift in that domain, such as a rule or form change, and ask what happens to stored lessons right after it.

Stay focused on these two papers. Session 3 (forgetting vs. compounding) can be foreshadowed briefly but not taught here. Check in with me after each major concept rather than delivering everything in one pass.

---

## Source notes

Condensed from full-text readings of both papers. Section, table, and figure references are to the papers. Items marked *(reviewer critique)* are our assessment, not the authors' claims.

### Paper A: ReHarness — "Recurrent Harness for Agentic Continual Learning" (Xiao et al., MIT / Meta, 2610.12668)

**Problem framing**
- In this paper, a harness is "persistent runtime scaffolding around a fixed LLM" (§1, §3.1). In practice, the harness state h_t is a **bank of textual reflections**.
- Three agents run on the same backbone: a decision agent πD, a memory agent πM, and a revision agent πR.
- The setting is **strictly online continual learning**:
  - each instance is seen once;
  - no validation set, no replay, no gradients (API models);
  - the environment gives a reward r_t per instance;
  - the trajectory is τ_t = (x_t, y_t, r_t).
- **Motivating failure: forward-only flow (§3.1, Fig 1).** Systems write reflections (τ → R → h) and read them (h → R → τ), but a written reflection is never updated according to how it later performed.
- **Toy example (Fig 1):**
  - "Put larger numbers first" is learned on a descending-sort task.
  - It then misleads ascending sorts again and again.
  - Adding a corrective reflection does not remove the bad one, which keeps being retrieved.
- **Existing curation does not close the loop:**
  - Add/delete/merge curation (Mem0, Dynamic Cheatsheet, ACE) keeps memory coherent, but does not use feedback from how the memory was used downstream.
  - Memory-optimizing methods need training or validation data that a strict stream does not have.

**Mechanism (§3.3, Eqs. 1–3)**
```
for each instance x_t:
  I_t = Retrieval(x_t, h_t, k=5)          # query-to-query embedding similarity (Qwen3-Embedding-8B)
  y_t = πD(x_t, {R_i : i in I_t}); observe r_t; τ_t = (x_t, y_t, r_t)   # Step 1: forward read
  for i in I_t:                                                          # Step 2: backward revision
      R_i' = πR(R_i, τ_i ; τ_t)   # τ_i = R_i's stored SOURCE trajectory; τ_t used only as feedback
  h_t' = h_t with retrieved R_i replaced by R_i' (unretrieved entries kept)
  R_t = πM(τ_t ; demos = {R_i'})                                         # Step 3: forward write
  h_{t+1} = h_t' ⊕ R_t
```
- **Revision prompt rules (App A, Fig 5):**
  - Keep operational *evidence* separate from supported *interpretations*.
  - Write or refine a "use-case guidance" field that states the **matching conditions** under which the reflection applies.
  - **Grounding/leakage rule:** "Use the source trajectory as the sole source of content. Use the later trajectory only to refine matching conditions and identify omissions supported by the source trajectory." This stops the new instance's answer from being copied into old memory.
- **Typical revisions:**
  - Add a limiting condition: "larger first *only if descending*".
  - Downgrade a speculative claim (Spectrum: "prioritize retaining confirmed peaks", Fig 3a).
  - Replace a rule made stale by a schema shift (Database: "enumerate ALL price-like columns" rather than assuming `prc`; reward 0 → 0.867, Fig 3b).
- **Forward write:** the revised reflections serve as style demonstrations for πM, which is pushed toward writing *complementary* perspectives.
- **Storage:** raw trajectories are kept indefinitely so reflections can be revised later. This means provenance is required: without the source trajectory you can only add or delete.

**Results (Table 1)**
- **Setup:**
  - Backbones: Claude Opus 4.8, GPT-5.5, Gemini 3.7 Flash.
  - Benchmarks: CL-Bench (6 tasks), MemoryBench (5 writing tasks, judged by GPT-5.6-Sol), MemoryArena (5 domains).
  - Metric: normalized gain = (r − r_stateless) / (r_max − r_stateless).
  - 3 stream rollouts.
- **Average normalized gain:**

| Method | Avg normalized gain |
|---|---|
| ReHarness | **0.240** |
| Top-K Raw (retrieve raw past trajectories) | 0.168 |
| Full Raw | 0.164 |
| Mem0 | 0.131 |
| GEPA-Online | 0.092 |
| DoT | 0.071 |
| ACE (add/update/delete/merge playbook) | 0.043 |
| ReasoningBank (RBank, append-only) | 0.034 |

- ReHarness is first or tied in 8 of 9 benchmark × backbone combinations. The exception is CL-Bench/Gemini, where Full Raw scores 0.234 vs 0.233.
- The largest margin is MemoryArena/Claude: 0.305 vs 0.145.
- **Surprising result:** the raw-context baselines beat *every* structured forward-only memory method on average.
- **Significance:** a Wilcoxon test with Bonferroni correction is significant against all baselines, but only narrowly against raw context (p_adj 0.039 vs Top-K Raw, 0.043 vs Full Raw).

**Ablations (all on CL-Bench, Claude only)**

- **Backward revision (Table 3):**
  - No Revision scores 0.144; ReHarness scores **0.217 (+0.073)**.
  - Gains on every task, largest on Sales (0.258 → 0.408) and Spectrum (0.033 → 0.162).
  - Without revision, ReHarness falls below Top-K Raw (0.165).
- **Counterfactual replay** (apply the revised h'_t to the *same* instance) reaches 0.335. The revisions carry real information, but this breaks the online protocol: in deployment you never get to re-answer the instance you learned from.
- **Demonstrations (§5.5):** removing the revised-reflection demos from πM drops the score 0.217 → 0.191.
- **k sweep (Fig 4b, post hoc):** gain rises steeply from k=1 to 5, stays flat from 5 to 20, and falls beyond that ("reflection drift"). k=5 was justified after the fact.
- **Grounding audit (Table 2, LLM-judged by GPT-5.6-Sol):**
  - At least 95.3% of claims are grounded.
  - Leakage is 0.8–2.1%; unsupported claims 0.5–2.6%.
  - Each revision moves grounding by at most 0.3%.

**Stability vs plasticity (Table 4, averaged over backbones)**
- Definitions:
  - **Stability:** gain on the first instance after a distribution shift.
  - **Plasticity:** gain on later instances before the next shift.
- Mem0, RBank, DoT, ACE, and GEPA-Online all have **negative stability** (−0.002 to −0.006). Forward-only state actively hurts right after a shift.
- ReHarness has stability 0.015 and plasticity 0.241, the best on both averages. It is not the best on every backbone: on Gemini, Full Raw stability is 0.024 vs 0.016.
- **State dynamics (Fig 4a):** revisions taper off as reflections stabilize, then spike after a shift; old reflections are rewritten in the h10 → h11 transition.

**Why add/delete-only memory underperforms**
- **The mechanism:**
  - Delete removes a misleading entry only once something notices it.
  - Add appends a correction while the bad entry stays retrievable (Fig 1).
  - Neither operation is driven by how a *specific retrieved entry* performed when it was used: curation targets coherence, not downstream effectiveness.
- ReHarness's edit is *conditional*. It narrows applicability instead of choosing between keep and delete, which preserves the useful core of an overgeneralized lesson.
- **Evidence:** ACE averages 0.043 and RBank 0.034, both with negative stability, and removing revision drops ReHarness to 0.144.
- *Caveat:* there is **no controlled ablation** that swaps ReHarness's revision for add/delete inside the same pipeline. The case rests on argument plus comparisons with baselines.

**Limitations and costs**
- **Per-instance calls:** 1 decision + 1 reflection + k=5 revision calls, run in sequence before the next instance.
- **Cost for one CL-Bench rollout on Claude (§4.2):**

| Method | Total tokens | Cost (with caching) |
|---|---|---|
| ReHarness | ~41.6M (37.2M in / 4.38M out) | **~$254** |
| Top-K Raw | ~52.7M | **~$85** |
| Full Raw | ~142M | ~$314 |

  "Fewer tokens" hides that ReHarness costs **about 3x Top-K Raw in dollars**, because output tokens dominate. *(reviewer critique: this is our reading of the paper's table, not a framing the paper itself gives)*
- **Noisy reward breaks it (authors):** on poker, hand-level reward is only weakly tied to strategy quality and ReHarness gains about 0.009. Raw context does better there because it defers interpretation.
- **Other limits:**
  - It needs a per-instance reward signal.
  - Raw trajectories are stored without bound.
  - Some results are inconsistent (Gemini Sales −0.141, Table 5).
- *(reviewer critique)* Evaluation weak points:
  - All ablations use CL-Bench with Claude only.
  - k=5 was chosen post hoc.
  - The grounding audit is LLM-judged.
  - Significance against raw baselines is marginal.
  - Absolute stability numbers are tiny (0.015).

**Practitioner takeaways**
1. **Keep provenance.** Store each memory with its source trajectory so it can be revised later. Without it you can only add or delete.
2. **Close the loop on retrieved memories.** After each use, revise the entries actually retrieved, using the outcome, mainly by adding *when-it-applies* conditions (+0.073, Table 3).
3. **Constrain revisions to their source and measure leakage** (Table 2). Otherwise memory silently fills up with answers to later tasks.
4. **Benchmark against Top-K raw trajectories first.** It beat every structured forward-only memory (0.168 vs at most 0.131). Count dollars, not just tokens.
5. **Keep k moderate (about 5).** Don't rely on backward revision when the reward is weakly diagnostic (poker).

**Discussion questions**
1. Counterfactual replay scores 0.335, yet it is not the method. What protocol does it break, and why does that matter for deployment claims?
2. Why might a revision that *narrows* a reflection's conditions help stability (the first instance after a shift) more than deleting the reflection would?
3. ReHarness uses fewer tokens than Top-K Raw but costs about 3x as much. What design changes could reduce output-token spend?

### Paper B: Harness^2 — "Recursive Agent Harnessing for an Open World" (Xu et al., Northwestern / Google Cloud AI Research, 2610.14224)

**Problem framing**
- **The harness:** H = (c1..cK), the editable runtime layer around a frozen model: "Agent = Model + Harness."
  - K=8 components, each one a file (Fig 2, Table 5).
  - Always-on: system prompt, guardrails, `LongTermMEMORY.md`, tool guidance.
  - On demand: skills (SKILL.md, loaded when invoked), scripts (run via bash), subagents (their own context window).
  - A middleware plugin (.ts) hooks into the tool loop. It is the only component the model cannot skip.
  - Since every component is a file, every edit is a diff.
- **"Harnessing"** is optimizing this layer. The key distinction is between two harnesses:
  - the **execution harness** runs the task;
  - the **improvement harness** (a library plus fixed stage prompts) guides how the execution harness gets edited.
- **Motivating failures (§1):**
  1. Offline self-improvement methods (Meta-Harness, AHE) pick one static harness against training tasks or unit tests, and it does not generalize to new open-world tasks.
  2. Open-world tasks have no ground-truth verifier.
  3. Edits made for one task do not transfer. Inheriting a highly tailored harness makes improvement noisy when tasks shift.
- **Thesis:** the *refinement process* (how a weakness was diagnosed, which edits were tested, what happened) is the reusable thing to learn from.

**Mechanism**
- **Setting:** a stream of N unlabeled tasks.
  - Each task starts from the same base harness H0.
  - The current task may be re-run within a budget.
  - Completed tasks are never replayed.
- **Task-level recursion: one contrastive step Φ (Eq. 1, §2.2.1).**
  1. **Propose.**
     - Run the current harness once to get a reference execution e0 (trajectory plus deliverable). It shows *how the harness behaves*, not whether the output is correct.
     - Two scoped editors (Claude Opus 4.8 agentic sessions) each draft a candidate by editing component files:
       - **INV (invariant):** how the agent works (planning, tool use, context, delegation, completion).
       - **DOM (domain):** practitioner knowledge (artifact contracts, decision rules).
     - Both may copy from the library but must re-verify any workspace facts.
  2. **Probe.** Run each candidate on the *same task* with the same model and environment. Comparing its behavior against the reference gives a **behavioral contrast**: did the edit fix the targeted deficiency, change nothing, or cause a regression? Contrasts "inform composition rather than verify task correctness."
  3. **Compose.** A composer reads the reference, the candidates, their diffs, and all execution evidence. It can MERGE, revise, ADOPT ONE, or KEEP_BASE, and every decision must cite a trajectory moment.
- **Composer rules (Prompt 3):**
  - A failure repeated across base rollouts is real; one seen in 1 of k rollouts is noise.
  - Agreement between candidates is "support, not independent proof," since they share model biases.
  - An edit whose rollout produced nothing is UNSAFE.
- **Editor rules (Prompt 1):**
  - Prefer edits in this order: a divergence, then a repeated failure, then a visible risk.
  - Write verified facts, not just procedures for rediscovering them.
  - Component preference: skill > script > subagent > plugin > always-on prose last ("every token competes with the agent's own output budget").
  - Invalid trees are retried once, then fall back to the inherited tree.
  - No rubric or score is ever in context, and a guard refuses any directory that contains one (App D.2).
- **Scaling (§2.2.2):**
  - *Parallel*, budget k: k references, k INV and k DOM candidates all probed, and k composers each seeing the full pool.
  - *Sequential*: k chained Φ steps.
  - For k>1, a **blind selector** (Prompt 5) picks among anonymized deliverables, with criteria in this order: delivery, conformance, fidelity, consistency, operational fitness, finish.
- **Harnessing-level recursion (§2.3, Eq. 4): R_{t+1} = Update(R_t, H*_t, D_t).**
  - After each task, a Reflector (Prompt 6) diffs every candidate against the base and gives each edit a verdict: helped, hurt, no observed effect, or **confounded**.
  - "Confounded" is preferred whenever several components changed at once or only one rollout supports the difference.
  - The Reflector writes at most one cue → lesson → evidence entry, or **`NO_ENTRY`**.
  - "Adoption alone never establishes that an edit helped."
  - Each library entry is the full adopted tree plus an `EXPERIENCE.md`.
  - **The next task still starts from H0.** Library components are reused or adapted through Propose, never inherited automatically.
  - Model weights and stage prompts stay fixed; only the library evolves.

**Results (Tables 1–2; means over 3 shuffled-order runs)**
- **Setup:**
  - Executors: Gemini 3.5 Flash and GLM-5, each run under OpenCode and under Codex.
  - Editor: Claude Opus 4.8.
  - Test sets: WorkBuddy-Bench (40/35/25 tasks for Code/Web/Office), JobBench (34), LAB (100).
- **WorkBuddy average at k=1:**
  - GLM-5/OpenCode 64.2 → 75.7 (+11.5); GLM-5/Codex 64.4 → 75.3.
  - Gemini/OpenCode 72.4 → 77.5; Gemini/Codex 74.5 → 77.5.
  - A weaker model with an improved harness (GLM-5 at 75.7) beats the stronger model's base harness (Gemini at 72.4).
- **JobBench:** Gemini +4.5 (OpenCode) and +1.4 (Codex); GLM-5 +3.6 and +1.2.
- **LAB Partial:** GLM-5/OpenCode 59.6 → 71.4 (+11.8). Meta-Harness wins LAB for Gemini/Codex (76.5 vs 75.6).
- **Parallel recursion at k=5** adds +2.9 to +3.9 (WorkBuddy), +3.0 to +4.2 (JobBench), and +2.6 to +6.7 points (LAB) over k=1.
- **ReasoningBank (memory baseline) falls below the base harness in several configurations:**
  - GLM-5/Codex Code 56.8 → 50.2 (−6.6).
  - Gemini/Codex Web 72.5 → 65.7.
  - Gemini/Codex JobBench 33.9 → 30.2.
  - Gemini/OpenCode LAB 79.9 → 77.3.

**Ablations**
- **Component ablation of the method (Table 3; Gemini/OpenCode, k=1; full = WorkBuddy 77.5 / JobBench 36.0):**

| Removed | WorkBuddy | JobBench |
|---|---|---|
| Library | 74.4 (−3.1) | 34.2 (−1.8) |
| **Scoping** (two generic editors instead of INV/DOM) | 74.6 (−2.9) | 32.3 (**−3.7**, largest on JobBench) |
| Composition (pick a winner, no merge) | 75.9 (−1.6) | 34.1 (−1.9) |

- **Harness components in the finished harness (Table 6, k=5; full average 80.8):**
  - Without skills 75.5 (−5.3); without scripts 77.1 (−3.7, and −7.4 on Office); without the prompt group 79.3 (−1.5).
  - Every ablated harness still beats base (72.4).
- **Blind edits hurt (Fig 7).** Editing the base harness directly, with no execution evidence and no library: Code 73.4 → **63.2**, Web 69.9 → 65.0.
- **The library alone:** a k=1 library brings performance back to base, and a k=5 library adds +0.9 / +4.4 / +5.1 with no probing at all.
- **Library transfer:** a library built on JobBench and moved to WorkBuddy adds +0.6 / +0.5 / +2.9.
- **Same model as editor and executor (Fig 8, k=2):** all five models improve; GLM-5 gains +13.7 on LAB.
- **Tool use (Table 7):** error rate drops 14.4% → 9.1% on JobBench, though the number of calls rises.

**Why ReasoningBank fell below base (inferred, NOT stated by the paper)**

The paper reports the drop but gives no causal explanation. Three plausible reasons follow from the baseline's design (App C) and the paper's own arguments:
1. ReasoningBank labels rollouts success or failure with an answer-free self-judge, then distills strategies from them. Wrong labels become confident strategies. Harness^2's own failure analysis (Fig 14) names the same pathology: "distilled from stock trajectories it cannot score, a prior becomes a rule."
2. It retrieves strategies from the most similar past task and prepends them. That is exactly the inheritance of task-specific experience that §1 argues breaks under shift.
3. Retrieved memory is never probed on the current task, and the blind-edit result (73.4 → 63.2) shows that unvalidated context changes can hurt badly.

ReHarness independently finds ReasoningBank among the weakest methods (0.034, negative stability), which is consistent with this reading.

**Limitations and costs**
- **Cost (App F)** *(reviewer count from §2.2.2)*:
  - k=1 is about 4 executor rollouts plus 3 editor sessions plus a reflector.
  - k=5 is about 20 rollouts plus 15 editor/composer sessions plus a selector and reflector.
  - Total compute is roughly 10–100M tokens per task on JobBench and 1–10M on WorkBuddy *(read from log-axis plots, Fig 6)*.
  - Harness^2 sits on the cost–performance Pareto frontier; Meta-Harness uses more compute than k=5 and scores lower.
- **Failure analysis (authors, Fig 14):**
  - The blind selector chose a 55-point output over a 95-point one.
  - It ranked precision over coverage on LAB (54 → 26).
  - A wrong premise spread across all candidates (−2 to −11).
  - A checker script the editor wrote "cannot catch the editor's assumption."
- **Signal:** behavioral contrasts are exposed to rollout randomness and to biases shared across models.
- *(reviewer critique)* Evaluation weak points:
  - Test sets are small (25–100 tasks) with 3 runs and standard deviations up to 4.5, so many per-domain gains are within noise.
  - The JobBench judge is Claude Opus 4.8, the same model as the editor and selector, which risks shared-bias inflation. WorkBuddy's LLM-judge items use Gemini 3.5 Flash, which is also an executor.
  - The editor is stronger than the executors (Fig 8 partly addresses this).
  - The library is append-only. Revising outdated experience is listed as future work (App G).

**Practitioner takeaways**
1. **Execute an edit before you trust it.** Blind edits cost 10.2 points on Code (Fig 7). A cheap contrast run on the same input is the minimum.
2. **Split diagnosis by scope.** Separate "process" proposers from "domain knowledge" proposers. This was the largest JobBench ablation effect (−3.7) and needs no extra budget.
3. **Put knowledge in on-demand or enforced components, not always-on prose.** Removing skills costs 5.3 and scripts 3.7, versus 1.5 for prompts.
4. **Store improvement experience with attribution discipline.** Use verdicts that include "confounded", plus a `NO_ENTRY` option.
5. **Treat final selection as the weakest link.** A label-free selector can discard a much better candidate, so define delivery and coverage criteria explicitly.

**Discussion questions**
1. Why does Harness^2 start every task from H0 instead of inheriting the last adopted harness? What would go wrong in a shifted stream, and how does the library recover the benefit of inheritance?
2. The composer prompt says candidate agreement is "support, not independent proof." Why, given how candidates are generated? What experiment would turn agreement into stronger evidence?
3. Removing composition costs less than removing scoping. Explain why diverse proposals might matter more than merging them.

### How the two papers relate

| | Harness^2 | ReHarness |
|---|---|---|
| What gets edited | Full executable harness (8 files incl. scripts, plugins) | Textual reflection bank only |
| Feedback | No labels; behavioral contrasts + LLM judgment | Environment reward per instance |
| Within-task learning | Yes: re-runs the same task (probe, compose) | None: each instance seen once |
| Cross-task learning | Append-only library of adopted harnesses + `EXPERIENCE.md` | Recurrent reflection state, revised backward |
| Direction of memory update | Forward only (revising stale experience is future work) | Forward write + backward revision of retrieved entries |

- **Each fills the other's gap:**
  - Harness^2's task-level recursion is essentially ReHarness's forbidden *counterfactual replay*: revise using the current task's evidence, then apply to that same task. Harness^2 allows it because its protocol includes a rerun budget.
  - ReHarness's backward revision is exactly what Harness^2's library lacks. Harness^2 starts from H0 to *avoid* stale inheritance; ReHarness *repairs* stale state.
- **Combined design (synthesis, not tested by either paper):** probe edits within a task, then revise the library entries that were retrieved, based on how they performed. Ground each revision in the entry's own source evidence, and mark it confounded when attribution is unclear.
- **Shared stance:**
  - Both reject validation sets.
  - Both treat model-written memory as hypotheses that need evidence (the Reflector's "confounded" verdict; ReHarness's evidence/interpretation split and source grounding).
  - Both find ReasoningBank-style forward-only memory weak or below baseline.
- **Connection to session 1:** LongHarness's supersede/retract operations on evidence are the within-task analogue of ReHarness's cross-task revision. In all three papers, corrections must actually reach whatever is read next; appending a correction is not enough.
