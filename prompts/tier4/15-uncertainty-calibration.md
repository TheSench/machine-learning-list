# Uncertainty, Calibration, and Active Learning — Tier 4+

You are a knowledgeable ML instructor. Teach me **uncertainty quantification, calibration, and active learning for LLMs at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with basic calibration concepts (ECE, reliability diagrams), temperature scaling, the general RLHF reward modeling setup, and the broad challenge of uncertainty estimation in neural networks.

## Session focus

This session covers specialist techniques for eliciting better-calibrated behavior from LLMs: contrastive active learning for data efficiency, clarification-seeking as an uncertainty reduction strategy, statistically valid active testing, reward model uncertainty in RLHF, and iterative hypothesis revision under uncertainty.

## Resources for this session

- "Active Learning by Acquiring Contrastive Examples" (Margatina et al., 2021)
- "STaR-GATE: Teaching Language Models to Ask Clarifying Questions" (2024)
- "Active Testing: Sample-Efficient Model Evaluation" (Kossen et al., 2021)
- "Uncertainty Estimation for Language Reward Models" (Zhai et al., 2023)
- "Doing Experiments and Revising Rules with Natural Language and Probabilistic Reasoning" (Jha et al., 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain contrastive active learning: the selection criterion (choose examples that differ maximally from the current labeled set in representation space), how this differs from uncertainty sampling and core-set methods, the empirical gains in annotation efficiency, and the practical limitation of needing a meaningful representation space
- Explain STaR-GATE: the training approach for teaching models to ask clarifying questions before answering ambiguous prompts, how clarification seeking is rewarded, and the experimental conditions under which it reduces errors vs. simply increases latency
- Explain active testing: the core idea (use a model to predict which test examples are most informative for evaluating another model, then only label those), the statistical guarantees, and what this enables for expensive or rare evaluation scenarios
- Explain reward model uncertainty: why a scalar reward model without uncertainty estimates creates instability in RLHF (the model can exploit high-reward regions that are actually out-of-distribution), the Zhai et al. approach to uncertainty estimation, and how uncertainty-aware reward models change the training dynamics
- Explain the Jha et al. rule revision approach: using LLMs to generate candidate hypotheses, probabilistic reasoning to evaluate them against experimental evidence, and iterative updating — what makes this more reliable than single-shot LLM hypothesis generation
- Synthesize: given the self-correction failure (Tier 3) and the unfaithful CoT result (Tier 4), what are the viable pathways to reliable uncertainty communication in LLMs — internal calibration, external verification, active clarification, or ensemble methods?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about uncertainty and calibration.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: for a practitioner deploying LLMs in high-stakes settings, what is the current best-practice toolkit for uncertainty quantification, and what are its known failure modes?

There is no "Tier 5" — this is the terminal depth for this topic.
