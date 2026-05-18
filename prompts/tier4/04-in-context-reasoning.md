# In-Context Reasoning — Tier 4+

You are a knowledgeable ML instructor. Teach me **in-context reasoning at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I understand chain-of-thought prompting, self-consistency, least-to-most prompting, and the debate about whether CoT reflects genuine reasoning or is a learned surface pattern. I have read about the self-correction failure.

## Session focus

This session examines the theoretical foundations of why in-context reasoning works at all, and probes the limits of ICL through a key empirical result that challenges conventional wisdom about demonstrations. It also covers two approaches to making reasoning more reliable: formal verification and hypothesis-driven inductive reasoning.

## Resources for this session

- "Rethinking the Role of Demonstrations: What Makes In-Context Learning Work?" (Min et al., 2022)
- "Why think step-by-step? Reasoning emerges from the locality of experience" (Prystawski et al., 2023)
- "Certified Reasoning with Language Models" (Poesia et al., 2023)
- "Hypothesis Search: Inductive Reasoning with Language Models" (Wang et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain Min et al.'s finding in precise terms: what varies across their ablations (label correctness, input-output pairing, format), which factor actually drives ICL performance, and what this implies about what demonstrations are communicating to the model
- Explain the locality-of-experience account of CoT: the theoretical argument that step-by-step reasoning works because adjacent intermediate conclusions co-occur in training data, not because the model has learned to reason in a general sense — and what predictions this account makes that differ from alternative accounts
- Explain certified reasoning: the architecture for constraining generation with formal grammars or verifiers so that intermediate steps are guaranteed valid, what classes of tasks this applies to, and the tradeoff between expressivity and verifiability
- Explain hypothesis search as an approach to inductive reasoning: how the generate-and-test loop works over candidate hypotheses, how this compares to symbolic ILP systems, and where LLMs succeed and fail at inductive generalization
- Articulate the tension between the locality-of-experience account and the compositional generalization findings from Tier 4 Transformers: are these accounts compatible?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about in-context reasoning.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given the Min et al. result (format matters more than content), the locality-of-experience theory, and the self-correction failure from Tier 3, what is the most defensible current account of what ICL is doing? What would it take to distinguish statistical pattern completion from something more like reasoning?

There is no "Tier 5" — this is the terminal depth for this topic.
