# Benchmarks — Tier 3

You are a knowledgeable ML instructor. Teach me **Benchmarks for LLM evaluation at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions from this reading list. That means I understand:
- Neural networks, backpropagation, and gradient descent in detail
- Full transformer architecture (multi-head attention, positional encoding, layer norm, residual stream)
- Tokenization and BPE
- Major foundation models: GPT-2/3, LLaMA, InstructGPT, DeepSeek-R1/V3, Llama 3
- RLHF, DPO, GRPO, and process reward models
- Chain-of-thought, self-consistency, and test-time compute scaling
- Task decomposition, Tree of Thoughts, IDA, factored cognition
- Debate as a scalable oversight technique
- RAG, dense retrieval, and semantic embeddings
- Calibration, uncertainty estimation, and sparse autoencoders
- Mechanistic interpretability basics (activation patching, monosemanticity)
- AlphaZero, MuZero, and the connection between game RL and LLM post-training
- Scaling laws, Chinchilla, and the AI compute trajectory
- AI safety framing: misuse, misalignment, structural risks, inner/outer alignment

I am familiar with MMLU, HumanEval, GSM8K, and the general landscape of LLM evaluation. I understand the concept of benchmark saturation and data contamination. I have not studied MMLU's construction in depth, SimpleQA, FrontierMath, or the METR RE-Bench in detail.

## Session focus

Tier 3 examines how the evaluation landscape is responding to frontier model capability: the saturation of once-challenging benchmarks, the design choices that make a benchmark resistant to memorization, what the ARC-AGI o3 breakthrough reveals about test-time compute and generalization, and what measuring AI R&D capability looks like.

## Resources for this session

- "RE-Bench: Evaluating Frontier AI R&D Capabilities" (Wijk et al., METR, 2024)
- "SimpleQA: Measuring Short-Form Factuality" (Wei et al., OpenAI, 2024)
- "ARC Prize 2024: Technical Report" (Chollet et al., 2024)
- "FrontierMath: A Benchmark for Evaluating Advanced Mathematical Reasoning in AI" (Glazer et al., 2024)
- "Measuring Massive Multitask Language Understanding" (Hendrycks et al., MMLU, 2020)

## Teaching objectives

By the end of this session I should be able to:
- Explain MMLU: the original design philosophy and subject coverage, why it was influential, and what "saturation" means in practice — including the contamination problem and what it implies about interpreting reported scores
- Explain SimpleQA: the design philosophy of unambiguous, short-form factual questions that have verifiable single correct answers — how this design sidesteps common evaluation pitfalls, and what model performance on SimpleQA reveals specifically about hallucination rates that MMLU does not
- Explain ARC-AGI: what abstract visual reasoning requires (systematic generalization from few examples), why LLMs performing well on language benchmarks struggled badly on ARC tasks, and what the o3 high-compute breakthrough (approaching human-level with massive test-time compute) tells us about the relationship between compute scaling and generalization
- Explain FrontierMath: how the benchmark was designed to resist memorization (problems requiring novel reasoning, not pattern-matching to training data), current frontier model performance, and what the remaining headroom implies
- Explain RE-Bench: what METR measured (can AI agents run ML experiments and improve ML code?), the experimental setup, key results, and what the benchmark reveals about the gap between general capability and R&D-specific capability
- Synthesize: given the saturation of earlier benchmarks and the difficulty of newer ones, what properties should a good evaluation benchmark have?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
