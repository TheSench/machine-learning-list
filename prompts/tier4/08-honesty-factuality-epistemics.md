# Honesty, Factuality, and Epistemics — Tier 4+

You are a knowledgeable ML instructor. Teach me **honesty, factuality, and model epistemics at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I understand the self-correction failure result, TruthfulQA, sycophancy, and the general challenge of getting models to be calibrated and honest. I know that CoT is widely used as a transparency mechanism but that questions about its faithfulness have been raised.

## Session focus

This session delivers two precise empirical results that constrain how we should think about model reasoning and factuality: the systematic demonstration that CoT is sometimes unfaithful in a measurable way (Turpin et al.), and a rigorous methodology for evaluating long-form factuality at scale (Wei et al.). Together they bracket the reliability problem from two directions.

## Resources for this session

- "Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting" (Turpin et al., 2023)
- "Long-form factuality in large language models" (Wei et al., 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Turpin et al. experimental design in precise terms: what biasing features were introduced (sycophantic hints, wrong answer anchors, irrelevant context), how they measured the effect on both the final answer and the stated reasoning, and why the dissociation between answer change and reasoning change constitutes evidence of unfaithfulness rather than mere inaccuracy
- Distinguish between two kinds of CoT failure: reasoning that is wrong but consistent with the answer (faithful but erroneous) vs. reasoning that doesn't reflect the actual computational process (unfaithful) — explain why the Turpin result is specifically about the second kind
- Explain what the Turpin result does and does not prove: it shows unfaithfulness occurs; it does not show that all CoT is unfaithful; explain what stronger claims would require
- Explain the SAFE (Search-Augmented Factuality Evaluator) methodology: decomposition of long-form responses into atomic claims, search-augmented verification of each claim, F1 scoring against human-labeled ground truth — the design choices and their tradeoffs
- Explain what Wei et al. find about factuality scaling: which model families and sizes are more or less factual, what the shape of the factuality-capability tradeoff is, and whether instruction tuning helps or hurts factuality
- Synthesize: given Turpin et al. (unfaithful CoT), the self-correction failure (models can't reliably fix their own reasoning), and Wei et al. (factuality benchmarks reveal systematic gaps), construct a coherent picture of the current state of model reasoning reliability — and identify where the most important open questions lie

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about honesty and factuality.
3. Flag which results are robust and well-replicated vs. preliminary or contested.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: if CoT is sometimes unfaithful and models can't self-correct, what oversight mechanisms actually work? How does this connect to the interpretability and debate threads from the broader reading list?

There is no "Tier 5" — this is the terminal depth for this topic.
