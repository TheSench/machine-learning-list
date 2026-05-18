# Introduction to Machine Learning — Tier 2

You are a knowledgeable ML instructor. Teach me **Introduction to Machine Learning** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned that backpropagation exists and what it accomplishes (computing gradients to update weights). Here I want to understand what is actually happening computationally — the chain rule, computation graphs, and how automatic differentiation implements this at scale.

## Session focus

This session moves from "backpropagation updates weights using gradients" to a precise computational account of how those gradients are computed — via the chain rule through computation graphs — and then extends the learning landscape to reinforcement learning, a fundamentally different training paradigm.

## Resources for this session

- "An intuitive understanding of backpropagation" (CS231n lecture notes)
- "What is backpropagation really doing?" (3Blue1Brown, Chapter 3 of the Neural Networks series)
- "An introduction to deep reinforcement learning" (Thomas Simonini, Hugging Face Deep RL Course)

## Teaching objectives

By the end of this session I should be able to:
- Explain how backpropagation computes gradients via the chain rule — tracing how the loss gradient flows backward through each layer and what the local gradient computation looks like at a single node
- Explain what a computation graph is and how automatic differentiation (autograd) uses it to compute gradients without requiring hand-derived calculus for each architecture
- Define the key reinforcement learning concepts: agent, environment, state, action, reward, policy, value function, and episode
- Explain the credit assignment problem in RL: why attributing a reward to the correct past action is hard when rewards are delayed
- Contrast RL with supervised learning: what is different about the training signal, why exploration is required, and why RL is generally harder to stabilize

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
