# AI Scaling — Tier 4+

You are a knowledgeable ML instructor. Teach me **AI scaling laws at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

## What to assume about my background

I have completed all Tier 1, 2, and 3 sessions from this reading list. I have comprehensive knowledge of:
- Transformer internals: residual stream, circuits framework, attention as information movement, grokking, the Reversal Curse
- Foundation models: GPT-2/3, LLaMA 1/2/3, InstructGPT, DeepSeek-R1/V3, Phi-4, Titans, Byte Latent Transformer
- Training: RLHF, DPO, GRPO, μP, LoRA, QLoRA, multi-token prediction, weak-to-strong generalization
- Reasoning: CoT, self-consistency, test-time scaling, s1, the self-correction failure, grokking
- Task decomposition: Tree of Thoughts, IDA, factored cognition, factored verification, model cascades
- Debate: debate framework, prover-verifier games, obfuscation, multiagent debate
- Interpretability: SAEs, monosemanticity, activation patching, representation engineering, influence functions
- Alignment faking, scheming, emergent misalignment, gradual disempowerment
- Scaling: Chinchilla, emergent abilities controversy, infinite compute analysis

I understand the Kaplan et al. and Chinchilla scaling laws, the emergent abilities controversy (and the reanalysis), and the basic picture of how compute, data, and parameters tradeoff. I know about test-time compute scaling as a newer axis.

## Session focus

This session examines specialist scaling results that extend beyond the canonical Chinchilla picture: capacity scaling for factual knowledge (Allen-Zhu & Li), data pruning as a strategy for beating power law scaling (Sorscher et al.), scaling laws for RL agents (Neumann & Gros), a controlled board-game testbed for scaling (Jones 2021), and the relationship between speedrunning and ML scaling as parallel phenomena.

## Resources for this session

- "Physics of Language Models: Part 3.3, Knowledge Capacity Scaling Laws" (Allen-Zhu & Li, 2024)
- "Beyond neural scaling laws: beating power law scaling via data pruning" (Sorscher et al., 2022)
- "Scaling laws for single-agent reinforcement learning" (Neumann & Gros, 2023)
- "Scaling Scaling Laws with Board Games" (Jones, 2021)
- "Power Law Trends in Speedrunning and Machine Learning" (2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain Allen-Zhu & Li's knowledge capacity result: the empirical formula for how much factual knowledge fits in N parameters, the experimental methodology (controlled synthetic facts with known ground truth), what the formula predicts about the knowledge-per-parameter ratio, and the implications for model sizing when factual recall is the primary objective
- Explain why knowledge capacity scaling differs from the loss-based Chinchilla picture: loss on next-token prediction is not the same as recall accuracy for discrete facts, and the two scale differently with model size
- Explain data pruning as a scaling lever: the geometric intuition (data near the decision boundary is most informative), the pruning strategies (easy, hard, medium examples), the finding that pruning can achieve better performance with less data than naive scaling, and the practical limitation that the pruning criterion depends on having a trained model
- Explain RL scaling laws: whether the Chinchilla-style power law relationship holds for RL agents, what the exponents look like for RL vs. supervised learning, and what the data-equivalent notion is for RL (environment interactions)
- Explain the board game scaling testbed: why chess and Go are useful controlled environments for studying scaling (known game-theoretic difficulty, tractable evaluation), what Jones (2021) found about how performance scales with compute in these settings, and how this validates or complicates claims from language model scaling
- Explain the speedrunning parallel: the power law relationship between world record times and cumulative attempts, what this shares mechanistically with ML scaling, and what the analogy does and doesn't tell us about the limits of scaling
- Synthesize: given these five papers, what is the most complete current picture of scaling? What is well-understood, what is contested, and what are the most important open questions about scaling in 2025?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about scaling.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: the Chinchilla picture assumed a fixed training budget. How do knowledge capacity scaling, data pruning, RL scaling, and test-time compute (from the broader curriculum) together expand or complicate the optimization problem a lab faces when training a frontier model?

There is no "Tier 5" — this is the terminal depth for this topic.
