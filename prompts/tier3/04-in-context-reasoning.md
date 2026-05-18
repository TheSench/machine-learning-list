# In-Context Reasoning — Tier 3

You are a knowledgeable ML instructor. Teach me **In-Context Reasoning at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand chain-of-thought prompting, few-shot prompting, self-consistency decoding, and the basic idea of test-time compute scaling. I have studied DeepSeek-R1 and know about RL-trained reasoning models. I have not studied test-time training (gradient updates at inference), the s1 budget-forcing approach, or the "cannot self-correct" result in depth.

## Session focus

Tier 3 probes the limits and surprises of in-context reasoning: a key negative result about self-correction, a surprisingly simple technique for extending reasoning at test time, empirical characterization of what cognitive habits distinguish effective reasoners, and test-time training — an approach that blurs the line between inference and learning.

## Resources for this session

- "s1: Simple test-time scaling" (Muennighoff et al., 2025)
- "Cognitive Behaviors that Enable Self-Improving Reasoners, or, Four Habits of Highly Effective STaRs" (Gandhi et al., 2025)
- "The Surprising Effectiveness of Test-Time Training for Abstract Reasoning" (Akyürek et al., 2024)
- "Large Language Models Cannot Self-Correct Reasoning Yet" (Huang et al., 2023)
- "Chain-of-Thought Reasoning Without Prompting" (Wang & Zhou, 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain the "cannot self-correct" result: under what experimental conditions LLMs fail to improve their own reasoning through self-review, why the apparent improvements in some studies are confounded by oracle feedback, and what this means for self-improvement pipelines that rely on the model as its own critic
- Explain s1 budget-forcing: how inserting "Wait" tokens forces a model to extend its reasoning trace at test time — the mechanism, empirical improvements on competition math, and why this works without RL training
- Explain the four cognitive habits of effective reasoners from the Gandhi et al. study: backtracking, exploring alternative approaches, verification, and subgoal decomposition — with examples of what each looks like in a reasoning trace
- Explain test-time training (TTT): performing gradient updates at inference time on problem-specific data before answering, why this helps on abstract visual reasoning tasks like ARC-AGI, and how it relates to (and differs from) in-context learning
- Explain CoT without prompting: how capable models produce internal reasoning traces during greedy decoding even when not explicitly instructed to, and what this reveals about how reasoning emerges from pretraining
- Synthesize: given these results, what is the current best understanding of the relationship between "thinking longer" and "thinking better" for LLMs?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
