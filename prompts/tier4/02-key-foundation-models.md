# Key Foundation Model Architectures — Tier 4+

You are a knowledgeable ML instructor. Teach me **key foundation model architectures at the specialist depth** — covering models and papers that complete the picture beyond the canonical curriculum.

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

I understand the GPT, LLaMA, and Mistral families well. I am familiar with decoder-only vs. encoder-decoder tradeoffs, instruction tuning, and standard efficiency techniques (GQA, sliding window attention, RoPE).

## Session focus

This session fills the gaps in the foundation model survey: the text-to-text unification approach (T5), instruction tuning at scale (Flan), non-transformer sequence models (Mamba, S4), native multimodal pretraining (Gemini), a fully open training pipeline (OLMo), code-focused training (Codex), and diffusion alternatives to autoregressive generation (Consistency Models).

## Resources for this session

- "Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer" (Raffel et al., T5, 2020)
- "Scaling Instruction-Finetuned Language Models" (Chung et al., Flan, 2022)
- "Efficiently Modeling Long Sequences with Structured State Spaces" (Gu et al., S4, 2021)
- "Mamba: Linear-Time Sequence Modeling with Selective State Spaces" (Gu & Dao, 2023)
- "Gemini: A Family of Highly Capable Multimodal Models" (Gemini Team, Google, 2023)
- "OLMo: Accelerating the Science of Language Models" (Groeneveld et al., AI2, 2024)
- "Evaluating Large Language Models Trained on Code" (Chen et al., OpenAI Codex, 2021)
- "Mistral 7B" (Jiang et al., 2023)
- "Consistency Models" (Song et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain T5's text-to-text framing: how casting all tasks as seq2seq simplifies multitask learning and the key ablations showing what matters (model size, pretraining objective, multitask mixing ratio)
- Explain Flan's core finding: that instruction tuning dataset diversity and scale drives zero-shot generalization more than any single dataset, and how this changes the recipe for capable general-purpose models
- Explain S4: the structured state space formulation that enables linear-time sequence modeling, the HiPPO initialization that makes it work on long-range dependencies
- Explain Mamba's selectivity mechanism: what makes it an improvement over S4, how input-dependent state transitions differ from fixed dynamics, and where Mamba matches or beats transformers
- Explain Gemini's architecture choices: native multimodal training at Google scale, cross-modal attention, and how it compares to GPT-4V's approach of separate vision encoders
- Explain what OLMo's full transparency reveals: what the open training pipeline shows about data composition, training dynamics, and reproducibility that closed models obscure
- Explain Codex: what it took to make code generation work — fine-tuning on GitHub code, the pass@k sampling strategy, the HumanEval benchmark design and its limitations
- Explain Mistral 7B's efficiency techniques: how sliding window attention and grouped-query attention combine to make 7B parameters competitive with 13B models, and what this implies about architectural choices vs. raw scale
- Explain Consistency Models: the self-consistency principle for single-step generation, why consistency training is stable compared to distillation, and how it achieves diffusion-quality outputs with fewer function evaluations

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about foundation models.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: how does this extended survey change the picture from Tiers 1–3? In particular, address the question of whether the transformer monoculture is justified — what do SSMs and consistency models tell us about the design space?

There is no "Tier 5" — this is the terminal depth for this topic.
