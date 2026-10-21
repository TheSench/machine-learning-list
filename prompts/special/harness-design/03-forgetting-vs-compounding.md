# Harness Design 3 — What to Forget, What to Keep (Side Track)

You are a knowledgeable ML instructor. Teach me **what an agent harness should forget and what it should keep** in a focused, interactive session at research depth. This is a side-track session built on two October 2026 papers. It goes beyond the Tier 3 Tool Use and Scaffolding material.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions, and Tier 3 through session #38. That means I understand:
- Transformers, foundation models, RLHF/DPO/GRPO, chain-of-thought and test-time compute scaling
- RAG, dense retrieval, ReAct-style tool use, and basic agent scaffolding
- Benchmarks, contamination, and benchmark-gaming failure modes
- Tier 3 Tool Use and Scaffolding: code actions, TextGrad, GEPA, and the elicitation gap (scaffolding can close capability gaps without retraining)

I have also completed side-track sessions 1 and 2:
- **Session 1 (LongHarness):** keep evidence and conclusions as explicit, revisable state, not as a growing chat history
- **Session 2 (ReHarness, Harness^2):** memory that is revised by downstream outcomes; test harness edits before trusting them

## Session focus

Sessions 1 and 2 argued for *better* memory. This session asks when memory hurts. "Scaling Discovery Requires Forgetting" shows that long-running agents anchor on their own past attempts and plateau, and that periodically wiping everything except the best candidate beats running longer or in parallel. GitSwarm shows the opposite-looking result: hundreds of agents compound progress through a persistent git repository where later work cites 70% of earlier negative results. The core of the session is reconciling them: "history" is two different things, an agent's in-context session and an external artifact store, and the two papers treat them differently.

## Resources for this session

- "Scaling Discovery Requires Forgetting" (Tan, Zhou, Agrawal, … Dimakis, Zaharia; UC Berkeley / Stanford / Bespoke Labs, Oct 2026), https://arxiv.org/abs/2610.20563
- "GitSwarm: Decentralized Compounding Inference" (Shah, Samanta, … Weston, Courville, Goyal; Meta Superintelligence Labs / Mila et al., Oct 2026), https://arxiv.org/abs/2610.04862

## Teaching objectives

By the end of this session I should be able to:
- Explain the anchoring failure in long-running agents: how it was measured (edit size, reasoning tokens, "declared plateau" turns), and why an agent's "I've hit the limit" is a symptom of its context, not evidence about the task
- Explain the forgetting mechanism: what is discarded, what is kept, the reset schedule, and why the clean ablation (Table 3) is the strongest evidence, including the cost result
- Explain GitSwarm's mechanism: commits with a physical parent plus declared `informed_by=` sources, planner-free work selection via in-flight announcements and abstention, and required notes that make negative results reusable
- Reconcile the two papers using the session vs. store distinction, and say exactly where they still disagree
- Name the ablations neither paper ran, and design the experiment that would isolate the memory layer each one argues about
- Apply both to my own work: decide what survives a reset, what goes into an archive, and which metrics would detect anchoring

## How to run this session

1. Start with "here's what you know from Tier 3 and side-track sessions 1–2, here's what this session adds" framing. The tension with sessions 1–2 ("remember better" vs. "remember less") is the hook.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings: the false "practical limit", forgetting being both better and cheaper, and failed commits being cited more than successful ones are built on.
3. Flag weak evidence explicitly. Both papers have a clean headline result but neither ablates the memory layer it argues about.
4. Check my understanding after each major concept before moving on. Ask me to explain it back or predict what happens if something changes. Don't front-load all the material and save checking for the quiz at the end.
5. At the end, give me a 3-question quiz that tests understanding, not recall. The discussion questions in the Source notes are good candidates.

Also:

- **These papers were published in October 2026, after your training data.** Teach ONLY from the Source notes below. Do not add mechanisms, numbers, or claims that are not in the notes. If I ask something the notes don't cover, say so plainly.
- **Side-track thread:** what enters the model's context should be designed, not accumulated. Tie each concept back to that. This side track also trains critical reading of harness claims: confounds, missing ablations, small n, cost not reported. Make me find these before you point them out.
- **Applied exercise (my domain, see my learner profile):** a long-running agent iterates for days on an artifact, such as a claims-triage rules set or a pricing heuristic, scored by an offline evaluator. Have me decide: what survives a reset, what goes into an archive (and in what form), how a fresh agent reads the archive without re-anchoring, and which metrics would tell me the agent is anchoring. Push on the case where knowledge lives outside the best artifact (a negative result, a rejected idea that was evaluated on too small a sample).
- **Experiment-design exercise:** neither paper ran the ablation that isolates its own memory layer (Forgetting never tests "wipe the session, keep the store"; GitSwarm never tests "same workers, no store"). Ask me to design the isolating comparison *before* you supply it: arms, what is held fixed, the metric, and the result that would falsify each paper's claim. Designing the comparison that holds everything else fixed is a recurring gap for me, so make me produce it, then correct it.

Stay focused on this topic. Check in with me after each major concept rather than delivering everything in one pass.

---

## Source notes

Condensed from full-text reads of both papers. Section, table and figure numbers refer to the papers.

### Paper 1: "Scaling Discovery Requires Forgetting" (arXiv 2610.20563, 14 Oct 2026)

**Problem framing**
- Setting: "autoresearch". An agent proposes a candidate, a judge scores it, the agent iterates.
- Three ways to scale it: one agent runs longer; N parallel agents; parallel agents that communicate (read each other's candidates).
- Claim: all three plateau as history accumulates. "Each agent becomes anchored to its own past attempts, making fewer and smaller edits."
- Two kinds of history (§3):
  - *Search state*: every candidate with its score and feedback.
  - *Session*: the messages and reasoning that produced those candidates.

**Evidence of the failure (§5)**
- Narrowing (Fig. 5, task AHC014, 3 replicates pooled, median per dollar):
  - Edits start around 100 lines per proposal in every configuration, then shrink within the first few dollars. By $4 the single agent edits only a few lines.
  - Reasoning tokens fall to one third or less of their starting level.
  - Before its first reset, the team goes from about 150 to 30 lines per edit, and from about 28k to 7k thinking tokens.
- Declared plateau (VLIW kernel task, single agent, $40 budget):
  - 532 of 763 turns produce no candidate, and they consume 66.2% of spend (58.4–70.4% across replicates).
  - In 531 of those 532, the agent reads at most one file, makes no edit, and declares a plateau ("I've reached the practical limit…" at 1,710 cycles).
  - The limit is false. The same agent later reaches 1,644 cycles, and the team with forgetting reaches 1,077.
- Qualitative example: over eleven turns an agent develops a selection-tree idea, rejects it on a mistaken cost comparison, corrects the comparison, and still declines to implement it as "too complex and risky". It keeps generating ideas but stops turning them into experiments.
- Plateau in the curves (§4.1): over the second half of the budget, parallel agents improve only 1.2% on AHC014 and 2.4% on VLIW. Frontier-CS Q171 is the exception, where parallel agents keep improving.

**Mechanism (§3)**
- A forget discards every agent's session **and** the entire search state: all candidates, scores, feedback and lineage.
- It keeps only the single best candidate across the team, with its score.
- A fresh agent gets the full first-turn prompt again (task, rules, instructions; App. B) and starts from that candidate. The workspace shows no earlier candidates.
- Rationale: the best candidate "already contains most of the progress". The discarded state mostly records *how* progress was made, plus failed directions that condition the agent.
- Schedule: fixed, 3 forgets per run (4 rounds). No adaptive trigger.
- Team communication (§3.2): 4 agents, each with its own session and search state. Before each proposal an agent can see peers' candidates as git commits with scores (`.context/peers/branch<i>/`). No messages between agents: communication is "fully asynchronous and token-free".
- Harness (§3.3): a **reducer** decides which candidates appear as files in the workspace and which session the agent continues. The agent edits with file tools only; the harness commits and runs the judge. Every configuration compared (single, parallel, team, forgetting) is a setting of the reducer.
- Setup: Pi agent harness, DeepSeek V4.1 Flash. Tasks: AHC014, Frontier-CS Q171, Anthropic VLIW kernel, nanochat-autoresearch. Budgets $20/$20/$40/$20 per replicate; 3 replicates per configuration. Prompts give no search strategy.

**Key results**

Table 1, final best score at equal token cost (mean ± s.d. over 3 runs; percentages vs. single agent):

| Task | 1 agent | 4 parallel agents | Team with forgetting |
|---|---|---|---|
| AHC014 (×10³, higher better) | 795 ± 210 | 964 ± 57 (+21%) | 1,103 ± 50 (+39%); best 1,145 |
| VLIW cycles (lower better) | 1,426 ± 197 | 1,220 ± 44 | 1,097 ± 18 (−23%); best 1,077 |
| Frontier-CS Q171 | 64.0 ± 6.2 | 70.2 ± 1.1 | 80.8 ± 2.9 (+26%) |
| nanochat val BPB (lower better) | 0.980 | 0.980 | 0.961 ± 0.012 (−2%) |

- Averaged across tasks, the team with forgetting beats parallel agents by 10% and a single agent by 22%. The abstract's "up to 15% / 39%" are the maxima.

Table 2, gain per round: the first forget gives most of the gain.
- AHC014: +11.2% after the first forget, +4.8% after the second, +1.7% after the third.
- VLIW: −7.0%, −2.6%, −1.6% (cycles, lower is better).
- 32 of 36 forgets led to a new best within the next round.

Table 3, the clean ablation: every arm starts from the same plateaued AHC014 state and runs 30 more proposals per agent.

| Configuration | Continue | Forget |
|---|---|---|
| 1 agent | +1.6% ± 0.2 ($6.66) | +4.5% ± 2.1 ($3.44) |
| 4 parallel | +1.9% ± 1.5 ($27.51) | +7.0% ± 3.3 ($13.97) |
| Team of 4 | +1.4% ± 1.3 ($24.67) | +9.2% ± 6.9 ($15.32) |

- Forgetting wins and costs roughly half as much, because contexts are shorter.
- Behaviour after a forget: over the first ten proposals, median edit is 40 lines (vs. 6 when continuing) and median reasoning 9.4k tokens (vs. 2.9k). Narrowing then recurs within each round.
- Synergy example (VLIW): before the forget the team creeps from 1,212 to 1,201 cycles. After it, a fresh agent tries a bold rewrite that scores 1,409, then only matches the starting point. It then borrows a peer's small trick from a diff and reaches 1,136; the round ends at 1,114. Forgetting enabled the bold attempt; communication rescued it.
- Communication alone does not remove the plateau (§4.1): before the first forget the team leads parallel agents by 13% on Frontier-CS but trails slightly on AHC014.

**Ablations NOT run**
- Reset frequency or an adaptive trigger.
- Wiping the session but keeping the search state, or the reverse.
- Keeping a summary or lessons instead of wiping.
- Keeping the top-k candidates instead of only the best.
- Other models; other team sizes.
- The conclusion names "when to forget and what to remember" as future work.

**Limitations** (the paper has no Limitations section; all of these are reviewer critique)
- Small sample and one model: 3 replicates on a "Flash"-tier model, which may be more prone to collapse. The ±6.9 s.d. on the team-forget arm in Table 3 is large next to its 9.2% gain.
- Figure 1 plots the *best replicate* of each configuration.
- Table 1 bundles communication and forgetting. Only Table 3 isolates forgetting, and only on AHC014.
- Two causes, one intervention: session reset and state wipe are always applied together, so we cannot tell which causes the gain. The §5 analysis attributes narrowing to session length.
- Cheap-to-lose tasks: here the best candidate is a self-contained program that subsumes earlier heuristics. Tasks where knowledge lives outside the artifact (negative results, measurements, impossibility arguments) may lose real information.
- Prompt-resend confound: a forget also re-sends the full task prompt, while later turns get only a short reminder (App. B). Part of the effect may be instruction re-injection.
- Table 3 fixes proposal count, not dollars; the forget arms spent less.
- Ceiling effects make later rounds hard to interpret (Table 2).

**Practitioner takeaways**
1. Instrument search breadth, not only score: lines changed per proposal, reasoning tokens per turn, no-op or "declared done" turns. On VLIW, 66% of spend went to turns with no edit.
2. Treat an agent's "I've hit the limit" as a symptom of its context. The 1,710-cycle "practical limit" was later beaten by 37% (1,077).
3. Periodically restart from the best artifact with a clean context. At matched proposal count, forgetting gave 3–6× the gain of continuing at about half the cost (Table 3). The first reset gives the biggest gain (Table 2).
4. Keep inter-agent communication at the artifact level and asynchronous (peers' commits plus scores, no chat). Pair it with resets so fresh agents can borrow fixes for bold attempts.
5. Put memory policy in one controllable component (the reducer), so single, parallel, team and forgetting configurations become settings you can A/B.

**Discussion questions**
1. Forgetting wipes both the session and the search state. Design an experiment that separates their effects. If wiping the session alone recovered most of the gain, how would that change your harness?
2. Why might keeping only the best candidate lose little on AHC014 or VLIW but a lot on a task like GitSwarm's Looped Transformer search, where an early idea was wrongly rejected on a 128-example eval? What property of a task makes it safe to discard history?
3. Table 3's forget arms are cheaper *and* better. Give two mechanisms that could produce this, one about attention or context length and one about prompt structure. How would you tell them apart?

### Paper 2: "GitSwarm: Decentralized Compounding Inference" (arXiv 2610.04862, 4 Oct 2026)

**Problem framing**
- Claim: inference-time compute is organized around individual trajectories, so intermediate work ("partial solutions, experimental findings, and even unsuccessful approaches") vanishes when an episode ends and must be rediscovered.
- Proposal, "compounding inference" (§1): organize computation so work persists and can be inspected, extended, combined, or challenged.
- The failure is shown mainly on synthetic tasks (App. C), not on the benchmarks:
  - *Hidden Rulebook* (persistence): independent workers reach about 70–75% coverage of relevant records (2 long workers) or 20–23% (many short workers), even with about 4/3 of the query budget. Shared persistent memory stays high.
  - *Hidden Maze* (branchability): without restorable checkpoints, workers re-walk known prefixes. Branch-native memory cuts the repeated-move fraction. Caveat (C.2): the prompt also tells workers to restore, so prompting is confounded.
  - *Retracted Evidence* (attribution): without parent and producer metadata, workers must read far more of the archive to find clean lineages, and the gap grows with lineage depth.
  - C.4 states these tests do not show any property *causes* the benchmark gains.

**Mechanism (§2)**
- Memory substrate: one git repo per task, root commit v0.
  - Each contribution is an atomic commit with one physical git parent: the tree the worker started from, chosen with `gs_fork` exactly once.
  - Each commit must also carry an `informed_by=` field listing its semantic sources, which must include the physical parent.
  - So a worker can build on branch A while citing results from branches B and C *without merging*. These edges are self-declared, not verified causal influence.
- Worker protocol (§2.3; prompt in H.2):
  - Up to C concurrent homogeneous workers (C = 5 for problem solving), each in an isolated worktree and **each starting with a fresh context**.
  - Each worker inspects the graph (`git log --graph --all`, `gs_inspect`, `gs_explore`) and in-flight peers (`gs_inflight`), then ends with exactly one action:
    1. **Contribute** one bounded, validated commit. Validation checks format and required artifacts, not correctness.
    2. **Nominate** an existing candidate, with a rationale, recorded outside the graph.
    3. **Abstain.** Abstentions don't consume budget B but still cost tokens.
- Choosing work without a planner:
  - The prompt tells workers to choose "high expected marginal value given both the completed graph and active work".
  - Before editing, a worker announces its gap, deliverable, success criterion and abort condition via `gs_inflight announce`. This is advisory: "no scheduler grants, rejects, ranks, or reserves the work."
  - If its work becomes redundant, the worker abstains.
  - A dashboard shows remaining budget, workers in flight and the nomination tally, flagged as "not evidence of correctness". On research tasks it shows GPU utilization and best validation score instead.
- Required artifacts per commit (H.2):
  - `MY_THOUGHTS.md`: sources and how they were used, reasoning, evidence, uncertainty, TODOs.
  - `EVALUATION.md`: a candid self-assessment.
  - A negative result may be committed if it answers the scoped deliverable. These files are how failures get reused.
- How failures are reused:
  - A failed or negative commit stays a full node with its explanation; later workers cite it in `informed_by=` and reuse its code or evidence.
  - NanoChat (E.4): at 2.18 h a separate trigram table fails (0.929923 vs. 0.929131 / 0.929700 for controls). At 23.08 h a worker cites both failures, reuses their hash, and borrows a shared-table idea from another branch; a later worker enlarges the table to reach the 24 h incumbent (0.905235).
  - RMT: a failed previous-token-memory idea is revisited 49.5 h later and becomes a temporal mixer in the final model.
  - Looped Transformer: a winning adapter was rejected on a 128-example eval and re-checked at 512 examples. The small eval misranked 5 of 12 model pairs, vs. 1 of 12 at 512.
- Readout (§2.5): plurality of nominations, ties broken deterministically. Research tasks select by validation score instead.

**Key results**
- ProgramBench (50-task subset of 200; Codex GPT-5.5-high; §3.2):
  - GitSwarm 73.1% at B = 100, rising to 79.4% at B = 500.
  - "Forced Codex" baseline (one agent re-prompted "Keep working…", App. B.3): stays at 63.1–65.1%.
  - Base GPT-5.5 workers: 64.6% rising to 71.2% (B = 300).
  - Gains diminish with budget while input tokens grow.
- IMOProofBench-Advanced (30 problems):
  - GPT-5.5-high: 28/30 at B = 20, 30/30 at B = 40 and 80, single run.
  - Gemini-3.1-Pro: 23.3 rising to 29.0 (B = 20 to 160), with a dip at B = 80.
  - Forced mini-SWE-agent at most 23; forced bash 26.5.
  - Authors admit Best-of-N with an oracle verifier also hits the ceiling with fewer tokens.
- Research tasks (§3.3):
  - RMT: held-out loss 2.890 and 2.894 vs. 3.147 for the reference, at 1.3B tokens. Forced GPT-5.6-sol reaches 2.927 using 3.0B tokens; Codex 2.690 using 10.1B. 4 of 6 final changes came from other branches; declared dependencies span 24 commits by 24 workers.
  - Looped Transformer: 3.187 vs. 3.265 reference (direct GPT 3.274, Codex 3.479). A parameter-matched control reaches 3.212, keeping two thirds of the gain. 395 experiments; 74% of negative architectural results were later cited.
  - NanoChat: BPB 0.993 → 0.905 in 24 active hours with 1,465 evaluations. The model grew from 50.3M to 1.72B parameters (1.61B in a lexical table), so not parameter-matched.
- **The "70%" figure, precisely:** in one NanoChat run, 709 of 1,258 accepted research commits (56.4%) were author-labelled negative, and 497 of those (**70.1%**) were cited later. Over the full record it is 982 of 1,285 (76.4%). It counts author-labelled negative commits, not failed evaluations.
- Accumulation (§3.4):
  - Workers cite prior work in 99.9% (ProgramBench) and 96.2% (IMO) of eligible episodes.
  - 94.7% and 44.4% of contributions are built upon later.
  - ProgramBench winner ancestry covers 81.6–92.6% of the graph; only about a quarter comes via git parents, the rest via `informed_by=`. IMO winner ancestry covers 21.3–33.0%, because proofs appear early and later workers mostly verify and select.
- Coordination (§3.5, G.4):
  - About 1 in 6 ProgramBench workers abstain as redundant, mostly from in-flight overlap. 97.1% of collisions landed after the abstainer had started, so the duplicated compute was already spent.
  - Abstainers use 6–7% of tokens; 94.9% of abstentions (1,349 of 1,421) were judged justified.
  - Workers inspect only about 5–7 commits (programs) or about 3 (proofs), not the whole graph.

**Design ablations (G.6, Table 13; 9 dev tasks, B = 50, 3 seeds)**

| Variant | Score | Runtime |
|---|---|---|
| Asynchronous (default) | 62.06 ± 2.44 | 38.0 min |
| Synchronous waves | 63.11 ± 0.58 | 49.3 min |
| Decentralized nomination (default) | 62.06 | 38.0 min |
| Central selector | 64.40 ± 1.49 | 34.9 min |
| Central aggregator | 58.19 ± 4.53 | 43.9 min |

- **No ablation removes persistent memory itself.** §4 says the needed with/without-history intervention was not run.

**Limitations**
- Authors' own (§4): citations are self-declared; artifact access shows use, not influence; persistence, branchability and attribution are never ablated in the full system.
- Reviewer critique:
  - Baseline asymmetry: the "Forced" baselines are a single agent re-prompted to continue, which is exactly the anchored long-session regime the Forgetting paper shows plateaus. There are no parallel-independent or Best-of-N baselines on ProgramBench, so part of the gain may simply be fresh contexts.
  - Scope: 50 of 200 ProgramBench tasks; IMO 30/30 is a single run on a saturated benchmark; research comparisons are not compute- or token-matched.
  - NanoChat used explicit roles (experimenter/synthesizer vs. critic/verifier, 3:1), contradicting the "no roles" framing for that run.
  - NanoChat's best (0.898671) could not be replicated exactly (0.899864) and its commit was rejected.
  - Costs: input tokens grow with repository size; redundant work is caught late; 3.1% of charged episodes produce nothing valid.
  - A central selector beat decentralized readout, which weakens the "decentralized" claim. The ablation set is small (9 tasks, 3 seeds).

**Practitioner takeaways**
1. Give each artifact two kinds of link: a physical "started from" parent and a declared "informed by" set. About three quarters of the winner's ancestry on ProgramBench flows through cross-branch semantic links. Attribution metadata also makes invalidation cheap.
2. Require every commit to carry structured notes, and allow negative results as first-class commits. 70–76% of negative research commits were later cited, and failed ideas fed final architectures (RMT, NanoChat).
3. Coordinate without a planner via visible in-flight scope declarations plus a cheap abstain exit. But check for overlap *before* heavy work: most redundancy was discovered after building.
4. Bound each episode and start every worker with a fresh context that reads the archive selectively (3–7 commits), which keeps cost below linear in history size.
5. Don't trust small proxy evals or vote counts as truth. The 128-example eval misranked 5 of 12 model pairs, and a central selector beat the nomination vote.

**Discussion questions**
1. ProgramBench winner ancestry covers about 85% of the graph, but IMO only 21–33%. Does low ancestry coverage mean IMO workers' computation was wasted? What metric would capture verification and selection value?
2. The baseline is one agent repeatedly told "Keep working". Given the Forgetting paper, what baseline would you add to separate the value of the shared repository from the value of fresh contexts, and what result would falsify compounding inference?
3. Why does GitSwarm need both `gs_fork` (a single physical parent) and `informed_by=`, rather than git merges? What breaks in the Retracted Evidence setting if only git parents exist?

### Reconciliation: "discard history" vs. "build on 70% of negative commits"

"History" means different things in the two papers.

| Layer | Forgetting | GitSwarm |
|---|---|---|
| In-context session (an agent's accumulated reasoning trace) | Wiped at each forget; this is the source of anchoring (§5) | Never accumulates: each worker is a fresh, bounded episode ending in one commit or an abstain. Only the Forced baseline keeps one, and it plateaus at 63–65% |
| External artifact store | Wiped down to the single best candidate (no failed candidates, scores or feedback) | Kept forever, unsummarized and unpruned; failures are full nodes with `MY_THOUGHTS.md` / `EVALUATION.md` |
| Access mode for prior work | Before a forget, everything is in the workspace and session; after, only the best candidate | Pull-based: each worker chooses which 3–7 commits to open, and cites them |
| Failure representation | Raw candidates plus judge feedback, with the agent's own failed attempts in its context | Curated, author-labelled conclusions ("negative result for X because Y"), with scope and dependencies |

- Both papers avoid one agent conditioning on its own long trajectory. Forgetting does it with periodic resets; GitSwarm builds it in, since every episode is a reset.
- They genuinely disagree about the external store: keep only the best candidate, or keep everything as an indexed, attributed, opt-in archive.
- The task types differ. Forgetting's tasks are ones where the best program subsumes past progress. GitSwarm's research tasks contain information outside the best artifact (an idea wrongly rejected on a noisy eval; a failed trigram table whose hash scheme later mattered).
- Neither paper isolates its own variable: Forgetting never tests "wipe the session, keep the store"; GitSwarm never tests "same workers, no store".
- Combined, falsifiable hypothesis: fresh, bounded contexts plus a persistent, attributed, pull-based archive of distilled results (including negatives) should beat both continuous sessions and a total wipe. Open questions: does a fresh agent reading many failure notes re-anchor (GitSwarm's selective 3–7 commit reading suggests this limits it), and which task types make the archive worth its input-token cost?
