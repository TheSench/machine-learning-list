# Task Decomposition — Tier 3

You are a knowledgeable ML instructor. Teach me **Task Decomposition at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand iterated amplification, factored cognition, and the safety motivation for task decomposition. I am familiar with Tree of Thoughts and least-to-most prompting. I have not studied factored verification applied to summarization, or the language model cascades framework, in depth.

## Session focus

Tier 3 examines practical implementations of task decomposition — specifically how decomposition is applied to hallucination detection in scientific summaries, the important distinction between reasoning that is genuinely faithful vs. post-hoc rationalization, a concrete deployed pipeline for science Q&A, and routing across model tiers as a cost/quality optimization.

## Resources for this session

- "Factored Verification: Detecting and Reducing Hallucination in Summaries of Academic Papers" (Kamoi et al., 2023)
- "Faithful Reasoning Using Large Language Models" (Creswell et al., 2022)
- "Iterated Decomposition: Improving Science Q&A by Supervising Reasoning Processes" (Reppert et al., Elicit/Ought, 2023)
- "Language Model Cascades" (Dohan et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain factored verification: how a summary is decomposed into individual atomic claims, each claim is independently checked against the source, and results are aggregated to produce a hallucination score — and why checking claims independently is more reliable than checking the full summary at once
- Explain the faithful vs. unfaithful reasoning distinction: the empirical evidence that chain-of-thought traces sometimes drive the final answer and sometimes are post-hoc justifications, how researchers probe for faithfulness (causal intervention studies, counterfactual tests), and why this distinction matters for interpretability
- Explain the Elicit/Ought iterated decomposition pipeline: the full workflow for answering science questions with process supervision, how human feedback on intermediate steps was used, and what quality improvements were observed
- Explain language model cascades: the probabilistic programming framing of chains of LM calls, how queries are routed to smaller or larger models based on confidence, and the empirical cost/quality frontier
- Synthesize: given the faithfulness problem, when does decomposition actually help with reliability, and when might it create a false sense of transparency?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
