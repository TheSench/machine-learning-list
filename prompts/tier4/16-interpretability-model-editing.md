# Interpretability and Model Editing — Tier 4+

You are a knowledgeable ML instructor. Teach me **mechanistic interpretability and model editing at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I understand SAEs, monosemanticity, the superposition hypothesis, activation patching, path patching, and the circuits framework at a solid level. I understand influence functions and representation engineering.

## Session focus

This session covers the landmark case studies and techniques in mechanistic interpretability and model editing: the IOI circuit as the field's canonical complete circuit analysis, ROME and MEMIT for surgical factual editing, sparse feature circuits for end-to-end SAE-level explanation, Git Re-Basin for understanding weight space symmetries, and a frank assessment of model editing's limits.

## Resources for this session

- "Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small" (Wang et al., 2022)
- "Locating and Editing Factual Associations in GPT" (Meng et al., ROME, 2022)
- "Mass-Editing Memory in a Transformer" (Meng et al., MEMIT, 2022)
- "Sparse Feature Circuits: Discovering and Editing Interpretable Causal Graphs in Language Models" (Marks et al., 2024)
- "Fast Model Editing at Scale" (Mitchell et al., GRACE, 2022)
- "Git Re-Basin: Merging Models modulo Permutation Symmetries" (Ainsworth et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the IOI circuit in full mechanistic detail: the indirect object identification task, the three head types (name mover, duplicate token, inhibition), what each head type computes, how they compose to produce the final output, and what path patching revealed about the causal graph — this is the field's standard of what a complete circuit analysis looks like
- Explain ROME's methodology: causal tracing to localize factual associations (early MLP layers, middle of the network), the rank-one update formulation, what the key-value memory framing implies about where the update should land, and the evaluation on CounterFact
- Explain MEMIT's extension: why ROME doesn't scale to thousands of edits (catastrophic interference), the layer-distributed update approach that spreads the edit across multiple layers, and the empirical tradeoffs vs. ROME
- Explain GRACE as an alternative editing paradigm: the codebook approach that stores edits externally rather than modifying weights, the retrieval mechanism, and the quality/scope tradeoffs vs. weight-editing approaches
- Explain sparse feature circuits: how combining SAE feature identification with causal scrubbing produces end-to-end explanations in terms of interpretable features, why this is a qualitative advance over activation patching, and what the computational cost is
- Explain Git Re-Basin: the permutation symmetry of neural networks (any permutation of neurons within a layer is functionally equivalent), the linear mode connectivity hypothesis, the permutation-finding algorithms, and what this implies for model merging, federated learning, and the geometry of loss landscapes
- Explain the limits of model editing: what breaks when you edit aggressively (ripple effects, inconsistency across paraphrases, degraded general capability), what the MEMIT and GRACE evaluations show about the reliability ceiling

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about interpretability and model editing.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given the IOI circuit, ROME/MEMIT, and sparse feature circuits, what is the current state of mechanistic interpretability's ambition — can we fully characterize a model's behavior from its circuits, and if not, what are the obstacles? Connect to the scalable oversight question: does interpretability give us the tools to verify model behavior at scale?

There is no "Tier 5" — this is the terminal depth for this topic.
