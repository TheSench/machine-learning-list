# ML in Production — Tier 2

You are a knowledgeable ML instructor. Teach me **ML in Production** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I covered ML technical debt and the "hidden technical debt in ML systems" paper — the mismatch between research code and production systems. Here I want to go deeper on two complementary fronts: the engineering mindset for debugging and building ML systems (Karpathy's recipe) and the data systems thinking needed to reason about production reliability.

## Session focus

This session covers the practical engineering discipline of training and debugging neural networks (Karpathy's incremental recipe) and the data systems concepts most relevant to production ML: consistency, fault tolerance, stream vs. batch processing, and the characteristic failure modes that appear when models are deployed at scale.

## Resources for this session

- "A Recipe for Training Neural Networks" (Andrej Karpathy, blog post, 2019)
- "Designing Data-Intensive Applications" (Martin Kleppmann, 2017 — conceptual overview of distributed systems for data)

## Teaching objectives

By the end of this session I should be able to:
- Explain Karpathy's training recipe and its rationale: become one with the data first (visualize, compute statistics, identify outliers), overfit a single batch to verify the model and loss are correct, then progressively scale up — and explain why each step prevents a class of subtle bugs
- Explain what "training-serving skew" is: when the data distribution seen during serving differs from training (different preprocessing, live vs. static data, feature drift) — and give concrete examples of how this causes silent model degradation
- Explain data drift and how to detect it: monitoring input feature distributions, model output distributions, and downstream metrics over time, and why drift is often silent (the model still runs and returns predictions)
- Explain feedback loops in ML production systems: when model predictions affect future training data in ways that can cause compounding errors or self-reinforcing biases
- Explain the key data systems concepts most relevant to production ML at a conceptual level: consistency (what guarantees a data store makes about read-after-write), fault tolerance (how systems survive node failures), and stream vs. batch processing (real-time feature computation vs. periodic jobs)
- Explain the "start simple, add complexity only when simple fails" principle and its practical application to ML system design

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
