# World Models and Causality — Tier 3

You are a knowledgeable ML instructor. Teach me **World Models and Causality in LLMs at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand the concept of probing classifiers — fitting a simple linear model on top of model activations to test whether a feature is linearly represented. I understand the distinction between a model that memorizes statistical patterns and a model that builds a structured representation of the world. I have not studied the Othello experiment, the language-of-thought framing, or the space/time representation finding in depth.

## Session focus

Tier 3 examines three separate lines of evidence bearing on whether LLMs build internal world models: a classic probe-based experiment on a synthetic game, a theoretical framing about probabilistic programs, and linear representations of geography and time — with careful evaluation of what each result actually proves vs. merely suggests.

## Resources for this session

- "Emergent World Representations: Exploring a Sequence Model Trained on a Synthetic Task" (Li et al., 2022 — the Othello experiment)
- "From Word Models to World Models: Translating from Natural Language to the Probabilistic Language of Thought" (Wong et al., 2023)
- "Language Models Represent Space and Time" (Gurnee & Tegmark, 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Othello experiment: the task (predicting valid next moves given a sequence of moves, with no board state input), the probing finding (linear probes successfully decode board state from internal activations), the causal intervention result (patching activations changes board state and affects predictions appropriately), and what this does and does not prove about "world models"
- Explain the "language of thought" framing: the Wong et al. argument that LLMs can be interpreted as approximate inference machines over structured probabilistic programs — what predictions this makes about LLM behavior, and what empirical work supports or challenges it
- Explain the space and time representation finding: that geographic locations and temporal facts are encoded as linear structures in LLM activation space (not just as lookups of memorized tokens) — the methodology, results, and what they imply about generalization
- Critically evaluate the evidence: distinguish between (a) "the model has a distributed representation of X" and (b) "the model uses a causal world model of X for reasoning" — explain why probing results are consistent with (a) but do not fully establish (b)
- Synthesize: if LLMs do build partial world models, what implications does this have for their generalization capabilities, their failure modes, and their potential as scientific reasoning tools?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
