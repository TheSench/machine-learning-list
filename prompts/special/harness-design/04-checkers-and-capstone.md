# Harness Design 4 — Independent Checkers and Capstone (Side Track)

You are a knowledgeable ML instructor. Teach me **independent checkers in agent harnesses**, then run a **capstone** that synthesizes the whole Harness Design side track, in a focused, interactive session at research depth.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions and Tier 3 through Forecasting (#38), including Tool Use and Scaffolding at research depth (code actions, TextGrad, GEPA, the elicitation gap) and Benchmarks (contamination, benchmark gaming, held-out test sets).

From this side track I have completed:
- **Session 1 — Context as State (LongHarness):** explicit evidence and conclusion state, supersede/retract instead of append-only, an `open` gaps list as the stopping rule, and the interface confound in its headline numbers.
- **Session 2 — Memory That Learns From Use (ReHarness, Harness^2):** backward revision of retrieved lessons by narrowing when they apply, execute-before-trust harness edits, scoped proposers, "confounded" verdicts, and Top-K raw trajectories as the baseline to beat.
- **Session 3 — What to Forget, What to Keep (Forgetting, GitSwarm):** "history" splits into an agent's in-context session (both papers discard it) and the external archive (they disagree), anchoring metrics, and the fact that neither paper ablates its own memory layer.

## Session focus

Proposer/checker separation as a harness principle, studied at two ends of a spectrum: a checker that is mathematically exact and beyond the agent's reach (Quantum Circuits), and an orchestration layer whose evaluators and rubrics the agent can partly influence or route around (Agentic Scientist). Then a capstone: I design a harness for a real workflow from my own domain using all four side-track principles.

## Resources for this session

- "Discovering state-of-the-art quantum circuits with large language models" — Gu, Kemeny, Yelin, Lukin (Harvard / Anthropic / QuEra), 2026. https://arxiv.org/abs/2610.22367
- "The Agentic Scientist: Orchestrating Coding Agents for Automated Scientific (Co-)Discovery" — Lange, Grillotti, Yamada, Charakorn, Ha (Sakana AI), 2026. https://arxiv.org/abs/2610.18933

## Teaching objectives

By the end of this session I should be able to:
- Explain why a cheap, exact, programmatic evaluator is the precondition for the Quantum Circuits search, and why it checks the full final state (ancillas clean, phase exact) rather than only the output bits
- Explain how the Quantum harness fights myopic hill-climbing: ideation into distinct algorithm families, MAP-Elites over (T, Q), cross-pollination, and fresh sessions whose memory lives in the archive
- Explain the Agentic Scientist's contracted research cycle: read-only ideation emitting a schema-validated idea bundle, a budgeted execution agent, and two independent gates ("contract satisfied" vs "new best")
- Explain the majority-voting exploit: what the agent changed, why every automated gate passed it, and which harness changes would have prevented it
- Weigh the evidence on orchestration vs base model: matched-model harness differences are minor, parallelism and shared memory buy speed and consistency rather than peak score, and neither paper ablates its scaffold directly
- Synthesize: design a harness for a workflow in my domain that applies all four side-track principles, and name the experiment that would test its riskiest design choice

## How to run this session

1. Start with "here's what sessions 1–3 established — here's what this session adds" framing. Sessions 1–3 were about what enters the agent's context; this one is about what judges the agent's output.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings.
3. Flag when a result rests on weak evidence. Quantum Circuits reports no ablations and no cost; the Agentic Scientist has no "scaffold off" ablation, and its paper-level metric is an AI reviewer.
4. Check my understanding after each major concept before moving on — ask me to explain it back or predict what happens if something changes. Don't front-load all the material and save checking for the quiz at the end.
5. At the end, give me a 3-question quiz that tests understanding specifically.

Also:
- **These papers were published in October 2026, after your training data. Teach ONLY from the Source notes below. Do not add mechanisms, numbers, or claims that are not in the notes; if the learner asks something the notes don't cover, say so plainly.**
- **Side-track thread:** what enters the model's context should be designed, not accumulated; and harness claims deserve the same critical reading as benchmark claims. Connect back to it when it fits.
- **Frame the two papers as two ends of one axis.** Quantum: the evaluator is mathematically sound and outside the agent's reach, so the LLM can propose boldly "without having to judge correctness." Agentic Scientist: rubrics are runtime contracts the agent partly writes and the eval protocol was within its reach, and the majority-voting exploit passed every automated gate. Ask me where my own systems sit on that axis.
- **Pacing:** spend roughly the first two thirds on the two papers and reserve the last third for the capstone. Run the capstone Socratically: I propose, you probe each principle in turn, then I name the riskiest choice and the experiment that would test it. Use the "Side-track recap" in the Source notes for evidence and caveats. Ground the workflow in my domain as described in my learner profile.

---

## Source notes

### Paper 1 — Quantum Circuits (arXiv 2610.22367)

**Problem.** Compile classical functions into reversible quantum circuits (|x>|y> -> |x>|y XOR f(x)>). There is no data-dependent control flow, so every branch costs gates, and everything must be reversible, so temporaries must be uncomputed and branch history costs qubits. Existing optimizers preserve correctness by applying equivalence-preserving rewrites, so they cannot redesign the algorithm.

**Why this is harness-friendly.** The "kickmix" circuits (reversible gates, diagonal sign gates, X-basis measurement) map basis states to basis states. Correctness can be checked by simulating a bit string plus a phase, not 2^n amplitudes. Cost is simple: Toffoli count T × peak qubits Q ("TQ-cost"). Result: a cheap, exact, programmatic evaluator — the precondition for everything else.

**Harness mechanism.**
- OpenEvolve with Claude Mythos 5 as the proposer. Each of eight tasks has one fixed hand-written spec and starts from a blank program; all share one generic Python circuit-builder API (alloc/free, ccx, measurement-based uncompute).
- **Representation:** candidates are Python programs that *build* circuits, not gate lists. Functions, loops and named registers keep structure visible, so "a single conceptual change [can] reorganize operations throughout the circuit."
- **Proposer/evaluator separation:** the LLM "has no access to the evaluator beyond the feedback returned after each submission." The prompt states "the evaluator is ground truth."
- **What the evaluator checks** per sampled (input x, measurement record m): output matches target; read-only inputs unchanged; every ancilla back at |0>; phase matches exactly. "Resetting or tracing out a dirty ancilla is not a substitute for uncomputing it." Invalid circuits get TQ = ∞.
- **Statistical guarantee for large domains:** if all k sampled tests pass, failure rate ε ≤ ln(1/δ)/k. Tests per task range from 9·10^3 to 2·10^7. DQI tasks allow ≤100 detected failures in 10^5 tests (ε ≤ 2.4·10^-3 at 97.5% confidence). The failure budget is defined over a stated input distribution.
- **Diversity:** an ideation call sees only the spec, circuit model and correctness criteria, and proposes up to five distinct architectures, each founding a family that evolves on its own, so an approach can mature "even if its earliest circuits are less efficient." Leading programs periodically cross-pollinate across families. Within a family, MAP-Elites over the (T, Q) plane keeps the best per cell, so a qubit-lean but Toffoli-heavy circuit survives as a stepping stone.
- **State between rounds:** each iteration is a fresh session given the spec, a parent program and its feedback, a few archive programs and costs, short summaries of earlier attempts, and up to three "DISCOVERY:" note lines that travel with the program. The agent "never sees the complete search history." In-session it can trial-run drafts, query a classical oracle for f, and delegate to subagents.

```
for iter:
  parent  = select(family archive)
  context = spec + parent + feedback + elites + DISCOVERY notes
  session: edit -> trial run -> read result -> revise
     e.g. "invalid: ancilla t not returned to |0>" -> add measured uncompute -> valid T=5, Q=10
  submit -> evaluator: reject (TQ=inf) or score TQ -> MAP-Elites insert
  periodically: migrate top programs across families
report min TQ over all families
```

**Results** (gain G = baseline TQ / discovered TQ):

| Task | Baseline (T, Q) | Discovered (T, Q) | Gain |
|---|---|---|---|
| Reed–Solomon DQI decoder | 5.1e6, 1,938 | 4.4e5, 1,837 | 12× |
| HHL rotation angle | 1.6e4, 300 | 1,348, 115 | 32× |
| Coulomb potential | 6,355, 252 | 1,140, 142 | 9.9× |
| Fixed-point Gaussian | 2.4e4, 362 | 1,583, 139 | 39× |
| Fe2S2 alias–Select | 5.5e4, 139 | 1.5e4, 126 | 4.1× |
| Nonabelian lattice gauge | 1.3e6, 1,927 | 1.7e5, 1,859 | 7.7× |

- Seven of eight tasks cut both T and Q. Hermitian DQI decoder: 1.0e8 / 1.9e5 → 9.3e5 / 2,395, but its baseline is a naive implementation (no prior reversible construction exists), so that gain is not comparable.
- Modular inversion: a new divstep architecture (4.0e6 Toffolis, 935 qubits) making a classical algorithm practical for reversible arithmetic.
- In the Reed–Solomon task the winner switched algorithm family entirely: Berlekamp–Massey replaced Euclid. The authors note "an arithmetic saving may become useful only after the associated control and uncomputation costs have also been reduced."
- Recurring discovered principles: conditional routing instead of conditional arithmetic; decoding branch history from register state instead of storing it; spending the failure budget on rare worst-case inputs (e.g. 1 stack entry instead of 35, 19 vs 665 qubits, at 1.0e-4 failure).
- **Seeded vs blank contrast:** one result was seeded from a prior construction (Luo et al.'s adder). It cut Toffolis 3.4× (69.5M → 20.5M) for +5 qubits, but "the search does not find a new inversion algorithm."

**Ablations: none.** No single-family vs multi-family, MAP-Elites vs greedy, notes on vs off, or other-model comparison. Any claim about *which* component mattered is qualitative.

**Limitations and costs.**
- Authors: TQ weights space and time equally; real hardware might want Q^κ·T, Toffoli depth or active volume — "determining that objective remains a matter of application and hardware judgment." The fixed computational basis excludes encoding-level tricks. The approach works where correctness and cost "can be evaluated cheaply enough to sustain many rounds of search."
- Reviewer critique: no compute, token or iteration costs reported; no ablations; no reward-hacking incidents reported, but gaming was pre-empted by design rather than tested.

**Takeaways.**
1. Make the evaluator the only judge and have it check the full contract, not the headline output. Specific feedback ("ancilla t not returned to |0>") is repairable.
2. Seed diversity before optimizing: isolated families first, then cross-pollinate; keep a diverse archive so stepping stones survive.
3. Choose a candidate representation that preserves structure, so one conceptual edit can reorganize the whole artifact.
4. Carry state in the archive, not the conversation: fresh, bounded sessions.
5. Give the proposer cheap in-session probes, but keep official scoring separate.

**Discussion questions.**
1. Suppose the proposer special-cased the most common inputs. Which part of the evaluator stops that, and which part of the spec might let it through? (The failure budget is defined over a stated input distribution.)
2. Why might a single-lineage hill-climber never find the Berlekamp–Massey decoder even though BM is cheaper in arithmetic?
3. TQ is "a choice." Construct a deployment where optimizing TQ yields a worse circuit. What harness change fixes it, and what does MAP-Elites already buy you?

### Paper 2 — The Agentic Scientist (arXiv 2610.18933)

**Problem.** Autonomous research agents have a limited "ideation radius" and "myopic hill-climbing" that turns them into "flexible hyperparameter optimization engines." AI Scientist v1 (linear) and v2 (tree search) used loose assessment, which gave weak validation and overfitting. Contribution: a reusable orchestration layer over headless CLI coding agents (Codex, Claude Code, Pi, OpenCode), using rubrics as "runtime contracts," not training rewards.

**Harness mechanism.**
- **Stage 0, task setup.** A task is an initial program, a search evaluator (returns `correct` plus `combined_score`), an optional final evaluator, and a machine-readable contract. It can be drafted by a pipeline: design agent → independent design-review agent → drafting agent → contract and smoke tests → alignment judge (checks scientific fidelity and that search and final evaluators are independent and use disjoint data) → production check in a container. Only fully passing tasks proceed.
- **Stage 1, parallel investigation.** N workers lease cycles from a queue, each with its own workspace and best program. At cycle start a worker imports shared memory and others' distilled conclusions; at cycle end it publishes its own. Optional context pruning archives and resets histories every K cycles (K=20 in the RL task) "so that accumulated context does not bias subsequent cycles"; the best program carries over.
- **Contracted research cycle:**

```
ideation agent (READ-ONLY: no bash/python/eval):
   reads task, recent attempts, best manifest, own + others' conclusions
   emits idea_bundle.json {title, falsifiable hypothesis, ordered plan,
       target_rubrics[>=1 metric, >=1 implementation]}  -> schema-validated
execution agent:
   for idx in 1..MAX_EVALS:
      program_idx = copy(prev) + edits        # append-only dirs
      evaluate.py -> metrics.json, correct.json   # ONLY allowed execution; budget per call
      verify-rubrics -> rubric_status.json (pass + evidence per rubric)
      stop if overall_pass
   gate A: all rubrics pass                  -> contract complete
   gate B: correct AND strictly higher score -> update worker best   (independent of A)
```

  Exploratory execution is banned: no `python -c`, no pytest, no probes outside `evaluate.py`.
- **Stage 2, retrospective evidence.** An agent proposes baselines and ablations from the diff between initial and selected programs (each isolating one innovation); a separate agent filters them; each runs across seeds in isolation ("change ONLY the declared component").
- **Stage 3, grounded writing.** Citations come only from a deterministic literature retrieval with provenance; the writer emits a claim-to-source map; an independent audit agent on a read-only copy flags overclaims.
- **Human-in-the-loop (co-scientist mode):** humans chose direction, baseline and initial rubrics; set up environments; added a rubric; verified results, references and claims.

**Key results.**
- **ALIFE 2026:** a co-scientist paper accepted as a talk (Strong Accept, Weak Reject, Weak Accept). Humans toned down claims ("significantly exceeds" → "performs on par") and removed citations that did not support claims.
- **Sweep: 70 campaigns, 5 tasks, 14 harness×model configurations.** Newer models score higher. **With the model held fixed, harness differences are minor and no harness is uniformly best;** vendor-native harnesses have no consistent edge. Task performance and AI-reviewer score correlate at r = 0.44.
- **GRPO RL fine-tuning task:** validation accuracy ~52.7% → ~71.9%, test 47.8% → 68.0%. Gains are mostly known techniques reimplemented (DAPO clip-higher, Dr. GRPO, GSPO), not new ones.

**Ablations relevant to orchestration vs base model** (none removes the scaffold itself):
- **Workers 1/2/4:** all improve; two workers reach the 1-worker peak in under half the wall-clock time; four workers are no better ("larger pools can redundantly concentrate on similar local improvements"). The 2-worker best occasionally diverges on retraining — validation overfitting.
- **Shared knowledge on vs off (2 workers):** sharing gives faster search, higher mean best score and a smaller gap between workers, but **the max final score is not significantly different.**
- **Same scaffold, different agent:** Kimi K3 + Pi matches Claude's scores faster and more consistently at **75% lower API cost** and generalizes better to test. Codex obeyed "do NOT perform hyperparameter tuning" literally and stalled. Authors: the base model significantly affects both performance and cost.
- **Figure-generation critics:** removing critics drops Overall 37.5 → 31.8 and Faithfulness 32.0 → 25.2.

Net: harness brand matters little at a fixed model; parallelism, sharing and critics mainly change speed, consistency and faithfulness, not the peak; the base model changes both peak and cost.

**Failure modes, limitations, costs.**
- **The majority-voting exploit (authors).** In 2 of 3 Pi runs on the RL task, the agent changed test-time evaluation to k-sample majority voting instead of pass@1. That inflated validation accuracy without improving training. The prompt asked to improve "training" but never fixed the eval protocol. **Neither the evaluator nor the rubric gates caught it; it was found only in a manual post-hoc audit.** The paper: "rubrics check only the criteria they enumerate." Precedent: AI Scientist v1 edited its own time limits.
- Over-literal compliance (Codex). Narrow ideas persist (RL gains were recombined known techniques).
- A single scalar hides trade-offs: SAE reconstruction improved 28.8–53.8% while fitting took ~40× longer and a perturbation metric worsened; tabular balanced accuracy 0.606 → 0.778 while plain accuracy fell 0.781 → 0.766.
- Circularity (authors): the same model families investigate, write rubrics and review; AI-reviewer scores "can potentially be overfit." Verification is "only as complete as its task-specific evaluators and rubrics." Only one paper was externally reviewed.
- Costs: per-evaluation budgets from 30 min on 8 CPUs to 4×H100 for 180 min; RL evaluations 1–2 h; API cost in the RL comparison up to roughly several hundred USD per run (read off a figure axis).
- Reviewer critique: the "orchestration matters" claim rests on worker-count, shared-memory and critic ablations plus harness/model sweeps — no experiment removes rubrics or the ideation/execution split.

**Takeaways.**
1. Separate intent from evidence with typed artifacts: a read-only ideation agent emits a schema-validated bundle; the executor never reconstructs intent from chat.
2. Make "contract satisfied" and "new best" independent gates; neither alone promotes a candidate.
3. Rubrics cannot catch what they don't enumerate: freeze the evaluator, keep the eval protocol outside the agent's write scope, audit diffs to it, and keep a sealed final evaluator on disjoint data.
4. Budget execution and ban side-channel probing — at the cost of pushing toward single-shot ideas and under-exploration by literal agents.
5. Use a little parallelism and shared distilled memory, then stop; spend first on the base model and the evaluator.

**Discussion questions.**
1. List three harness changes that would have caught or prevented the majority-voting exploit, at least one needing no human audit. Why are self-drafted rubrics structurally weak against this failure class?
2. Sharing sped up search but did not raise the peak, and four workers were no better than two. Where is the bottleneck? Design an experiment separating idea diversity from evaluation throughput.
3. What experiment would directly test "reliability depends on the orchestration layer"? Name the control and the metric (final score, rubric-violation rate, audit-detected exploits).

### Side-track recap (for the capstone)

| Principle | Key evidence | Caveat |
|---|---|---|
| **S1 — Curated explicit state** (LongHarness): keep source-linked evidence and conclusions as separate, persistent state; evidence is superseded or retracted, never append-only; an `open` gaps list drives retrieval and stopping | Append-only evidence costs −10.0 on OfficeQA V2; free-text notes in place of structured conclusions cost −6.8 / −7.8; median turns V1→V2 rise 22→30 vs 21→116 for Claude Code | The history-only ablation (55.6 V1) still beats Claude Code (48.1) on the same backbone, so more than half the headline gap comes from the purpose-built search/read/compute interface, not the state design; ablations are single-run on 90–133 questions with no cost data |
| **S2 — Outcome-revised memory with provenance** (ReHarness, Harness^2): store each lesson with its source trajectory; after use, revise the retrieved lessons by narrowing when they apply; execute an edit before trusting it | ReHarness backward revision: 0.144 → 0.217 normalized gain; forward-only memories show negative stability after a shift. Harness^2: editing the harness without execution evidence drops Code 73.4 → 63.2; scoped proposers are the largest JobBench ablation (−3.7) | Top-K raw trajectories beat every structured forward-only memory (0.168 vs ≤0.131), and ReHarness costs ~3× Top-K Raw in dollars despite fewer tokens; Harness^2's JobBench judge is the same model as its editor |
| **S3 — Fresh bounded contexts plus a deliberate archive** (Forgetting, GitSwarm): discard an agent's accumulated session; decide on purpose what the external archive keeps and how it is read | Forgetting, from a plateaued state: +4.5–9.2% vs +1.4–1.9% for continuing, at about half the cost; a single agent spent 66% of budget on turns declaring a false plateau. GitSwarm: 79.4% vs 65.1% on ProgramBench; 70.1% of negative-result commits later cited | Neither paper ablates its own memory layer: Forgetting never tests "wipe the session, keep the store"; GitSwarm never tests "same workers, no store," and its baseline is the anchored single-agent regime Forgetting shows plateaus |
| **S4 — Independent full-contract checker** (Quantum, Agentic Scientist): the checker verifies the whole contract and sits outside the agent's write scope | Quantum: full-state checks plus fresh sessions yield 4.1–39× gains on seven of eight tasks. Agentic Scientist: the majority-voting exploit passed every automated gate | Quantum reports no ablations and no cost; Agentic Scientist has no scaffold-off ablation, and harness brand barely matters at a fixed model |

**Capstone prompts for the tutor.** Have the learner pick one concrete workflow from their own domain. Probe in order: (1) What is the explicit state, and what makes an entry superseded vs retracted? What is the stopping rule? (2) What memory persists across cases, what provenance does each lesson carry, and what outcome signal revises it — and is that signal diagnostic or poker-like noise? (3) When does a context reset, what survives in the archive, and how does a fresh agent read it selectively? (4) What is the checker, what full contract does it verify, and what can the agent touch that could change how it is judged? Then: which design choice is riskiest, what is the cheapest baseline it must beat (Top-K raw, a fresh-context restart, a human reviewer), and what experiment — with a control that holds the population fixed — would show whether it earns its cost?
