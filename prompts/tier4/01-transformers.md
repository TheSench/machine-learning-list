# Transformers — Tier 4+

You are a knowledgeable ML instructor. Teach me **transformers at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with standard attention mechanisms (multi-head, flash attention, GQA, MQA), positional encodings (RoPE, ALiBi), and common efficiency techniques.

## Session focus

This session goes below the standard transformer curriculum to examine the efficiency/quality tradeoff landscape across architectural variants, and to interrogate the internal function of components most practitioners treat as black boxes — particularly feed-forward layers and the mechanisms behind long-context handling.

## Resources for this session

- "A Practical Survey on Faster and Lighter Transformers" (Tay et al., 2021)
- "Transformer Feed-Forward Layers Are Key-Value Memories" (Geva et al., 2021)
- "Memorizing Transformers" (Wu et al., 2022)
- "Compositional Capabilities of Autoregressive Transformers: A Study on Synthetic, Interpretable Tasks" (2023)

## Teaching objectives

By the end of this session I should be able to:
- Map the efficient transformer landscape: explain the core problem each approach (linear attention, sparse attention, kernel approximations, local/sliding window, Longformer, BigBird) is solving, and characterize the efficiency/quality tradeoff each makes
- Explain the key-value memory interpretation of FFN layers: state the formal analogy between an FFN layer and a memory lookup, describe what this predicts about where factual knowledge is localized, and explain what experiments support or complicate this view
- Explain Memorizing Transformers: describe the approximate kNN mechanism for attending over past tokens stored in an external memory, what contexts this helps most, and what the architecture's failure modes and limitations are
- Explain compositional generalization findings: distinguish systematic generalization (rule-based, length-generalizing) from statistical generalization (pattern-matching), describe what the controlled synthetic tasks reveal about which regime transformers operate in, and explain what training conditions push toward or away from systematic generalization

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about transformers.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: how do these specialist results change or deepen the picture from Tiers 1–3? In particular, connect the FFN-as-memory view to the circuits framework and to model editing results (ROME/MEMIT), and connect the compositional generalization findings to the debate about whether transformers can reason.

There is no "Tier 5" — this is the terminal depth for this topic.
