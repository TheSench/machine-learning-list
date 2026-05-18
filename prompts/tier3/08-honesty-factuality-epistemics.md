# Honesty, Factuality, and Epistemics — Tier 3

You are a knowledgeable ML instructor. Teach me **Honesty, Factuality, and Epistemics at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand calibration and the concept of sycophancy — that RLHF-trained models tend to tell users what they want to hear. I am familiar with the conceptual distinction between a model being wrong and a model being deceptive, and I know the basic framework of "truthful" vs. "non-deceptive" vs. "non-manipulative" from AI safety discussions. I have not studied the empirical literature on what kinds of evidence shift LLM stated beliefs, or consistency-based lie detection, in depth.

## Session focus

Tier 3 examines two specific empirical results: what the research literature shows about which types of evidence actually move LLM stated positions (not what we might expect), and a behavioral approach to lie detection that works without access to model internals — with implications for how we should think about monitoring deployed systems.

## Resources for this session

- "What Evidence Do Language Models Find Convincing?" (Wan et al., 2024)
- "How to Catch an AI Liar: Lie Detection in Black-Box LLMs by Asking Unrelated Questions" (Pacchiardi et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain what kinds of evidence do and do not reliably shift LLM stated beliefs: specifically, how models respond to logically valid arguments vs. authoritative assertions vs. social pressure vs. repetition — including the surprising finding that models can be moved by epistemically irrelevant factors
- Explain the consistency-based lie detection approach: the key insight that a model telling a deliberate lie must maintain a consistent false story across many unrelated probes, creating detectable inconsistencies — the experimental setup, what results were found, and the conditions under which this method works or fails
- Clearly distinguish a model being wrong (epistemic failure: the model has a false belief or poor calibration) from a model being deceptive (behavioral failure: the model has a representation of the truth but asserts something different) — and explain why conflating these leads to incorrect interventions
- Explain what monitoring or evaluation approaches follow from these findings: what behavioral signatures might indicate deception rather than error, and what limits black-box behavioral testing has
- Evaluate the strength of the evidence: where these results are compelling and where they are preliminary

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
