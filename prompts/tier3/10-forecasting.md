# Forecasting — Tier 3

You are a knowledgeable ML instructor. Teach me **Forecasting with Language Models at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand probability calibration and Brier scores. I am familiar with the concept of superforecasting (Tetlock) and prediction markets. I have not studied how LLMs compare to superforecasters empirically, or the formal properties of LLM probability estimates (coherence, consistency), in depth.

## Session focus

Tier 3 examines the empirical evidence on LLM forecasting performance — including a surprising result approaching human superforecaster accuracy — alongside concerning findings about probability incoherence, the potential of LLMs to output full predictive distributions rather than point estimates, and the nuanced picture of when AI assistance improves vs. degrades human forecasts.

## Resources for this session

- "Consistency Checks for Language Model Forecasters" (Zhao et al., 2024)
- "LLM Processes: Numerical Predictive Distributions Conditioned on Natural Language" (Requeima et al., 2024)
- "AI-Augmented Predictions: LLM Assistants Improve Human Forecasting Accuracy" (Vaccaro et al., 2024)
- "Approaching Human-Level Forecasting with Language Models" (Halawi et al., 2024)
- "Forecasting Future World Events with Neural Networks" (Zou et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain how LLM forecasting performance compares to human superforecasters: what the Halawi et al. setup was (retrieval-augmented, aggregated), what accuracy level was achieved, and what remains different between LLM and human forecasting
- Explain consistency checks: the formal coherence properties a probability distribution must satisfy (partition, conditioning, commutativity) — how LLMs systematically violate them, and what this implies about whether LLM probability outputs are well-calibrated beliefs or approximations
- Explain LLM Processes: the approach of conditioning a language model to output full predictive distributions over numerical quantities (not just point estimates) — how this works, what it enables, and where it still struggles
- Explain the AI-augmented forecasting result: under what conditions human forecasters improve when given LLM assistance vs. when they anchor to wrong AI estimates and perform worse — and what interface design choices affect this
- Compare LLMs as forecasting tools to structured prediction models and prediction markets: where each is stronger and what the current evidence suggests about appropriate use cases

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
