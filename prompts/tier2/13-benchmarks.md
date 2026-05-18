# Benchmarks — Tier 2

You are a knowledgeable ML instructor. Teach me **Benchmarks** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand that benchmarks are used to evaluate model capabilities and track progress. Here I want to understand the design rationale of specific modern benchmarks — what each measures, why it was constructed as it was, and the limits of benchmark-based evaluation.

## Session focus

This session examines four influential modern benchmarks — GAIA, GPQA, SWE-bench, and TruthfulQA — at the level of their design philosophy and measurement validity, and uses them to ground a deeper discussion of Goodhart's Law and the gap between benchmark performance and real capability.

## Resources for this session

- "GAIA: a benchmark for General AI Assistants" (Mialon et al., Meta, 2023)
- "GPQA: A Graduate-Level Google-Proof Q&A Benchmark" (Rein et al., 2023)
- "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" (Jimenez et al., Princeton, 2023)
- "TruthfulQA: Measuring How Models Mimic Human Falsehoods" (Lin et al., 2021)

## Teaching objectives

By the end of this session I should be able to:
- Explain what GAIA measures: real-world assistant capability requiring multi-step reasoning, tool use, and factual lookup — and why its tasks are calibrated to be easy for humans but hard for current AI systems
- Explain the "Google-proof" design principle in GPQA: questions are constructed so that finding the answer by retrieval is insufficient — the question requires domain-level reasoning that cannot be bypassed by search, and the questions are validated to be difficult even for non-expert PhD scientists
- Explain SWE-bench as an agent benchmark: the task is resolving a real GitHub issue in a real software repository, with correctness verified by the repository's existing test suite — and explain what this tests that static QA benchmarks do not (multi-step planning, code understanding, tool use in context)
- Explain TruthfulQA: the benchmark measures whether models reproduce common human misconceptions and falsehoods when asked questions in the domains where humans are typically wrong — and explain how the question set was curated and why this is distinct from measuring factual accuracy on trivia
- Explain Goodhart's Law in the benchmark context: when a benchmark becomes a target for optimization (in pretraining data, post-training RL, or explicit benchmark-specific fine-tuning), scores can improve while the underlying capability the benchmark was meant to measure does not — and give concrete examples of how this plays out in practice

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
