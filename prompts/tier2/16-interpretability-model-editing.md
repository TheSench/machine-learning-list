# Interpretability and Model Editing — Tier 2

You are a knowledgeable ML instructor. Teach me **Interpretability and Model Editing** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand that neural networks learn internal representations but that these are generally opaque. Here I want to understand the current state of mechanistic interpretability: what researchers have found inside models, what tools they use, and why this work is relevant to AI safety.

## Session focus

This session covers the goals and methods of mechanistic interpretability research: sparse autoencoders as a tool for decomposing polysemantic representations into interpretable features (monosemanticity), the hypothesis that models internally represent more knowledge than they express (latent knowledge), activation patching as a causal intervention method, and the safety relevance of interpretability work.

## Resources for this session

- "Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet" (Templeton et al., Anthropic, 2024)
- "Interpretability at Scale: Identifying Causal Mechanisms in Alpaca" (Wu et al., 2023)
- "Discovering Latent Knowledge in Language Models Without Supervision" (Burns et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain what mechanistic interpretability aims to do: reverse-engineer the computational structure of neural networks to find human-understandable algorithms, circuits, or features — not just predict behavior but understand the mechanism
- Explain polysemanticity and superposition: why individual neurons respond to multiple unrelated features, and the hypothesis that models compress many features into fewer neurons by exploiting high-dimensional geometry — explain why this makes interpretation difficult
- Explain sparse autoencoders (SAEs) and the monosemanticity approach from Templeton et al.: training a sparse encoder to decompose the superimposed representation of a layer into a larger set of mostly-monosemantic features, and why monosemanticity (one feature = one concept) is valuable for interpretability
- Explain the latent knowledge hypothesis from Burns et al.: that models may internally represent beliefs more accurately than they express in their outputs, and the contrastive activation approach used to probe for these internal representations without supervised labels
- Explain activation patching (also called causal tracing or path patching): intervening on a model's internal activations by replacing them with activations from a different run, and measuring how much this changes the output — explaining how this identifies which components causally drive a specific behavior
- Explain why interpretability matters for AI safety: understanding model internals could allow us to detect deceptive alignment (a model pursuing different goals than its training objective), verify that safety properties hold, and diagnose failure modes before they manifest in outputs

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
