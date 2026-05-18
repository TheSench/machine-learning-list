# AI Scaling — Tier 2

You are a knowledgeable ML instructor. Teach me **AI Scaling** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I studied neural scaling laws — that loss scales predictably as a power law with compute, parameters, and data. Here I want to understand the quantitative implications: how Chinchilla revised our understanding of optimal compute allocation, what the historical compute curve looks like, and what scaling laws for transfer tell us about pretraining's downstream value.

## Session focus

This session moves from the qualitative scaling law picture to quantitative implications: the Chinchilla correction and its practical impact on how frontier labs allocate compute, scaling laws for transfer, the historical compute growth curve, and the practical tradeoffs between training-time and inference-time efficiency.

## Resources for this session

- "AI and compute" (OpenAI blog post, 2018)
- "Scaling Laws for Transfer" (Hernandez et al., OpenAI, 2021)
- "Training Compute-Optimal Large Language Models" (Hoffmann et al., Google DeepMind, 2022 — Chinchilla)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Chinchilla finding: the Kaplan et al. scaling laws (which informed GPT-3's design) implied that parameters should scale faster than data, but Hoffmann et al. showed that optimal scaling is roughly 1:1 — meaning GPT-3 and many contemporaries were significantly undertrained relative to their parameter count
- Explain how Chinchilla changed compute allocation at frontier labs: the practical implication is training smaller models on more tokens per FLOP budget, which also yields more inference-efficient models for deployment
- Explain scaling laws for transfer from Hernandez et al.: how many tokens of pretraining data on a source distribution are "equivalent" to labeled examples on a target task, and what this implies for how much pretraining helps downstream fine-tuning
- Explain the historical compute curve from the "AI and compute" analysis: training compute has roughly doubled every 3-4 months since 2012, far exceeding Moore's Law in growth rate, and explain what this implies for the trajectory of capability growth
- Discuss the "compute-optimal" concept in practice and its key tradeoff: a compute-optimal training run minimizes loss per FLOP at training time, but the resulting model may require more inference compute per query than a smaller model trained on fewer tokens — explain why labs targeting high-volume deployment may deviate from compute-optimal training deliberately

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
