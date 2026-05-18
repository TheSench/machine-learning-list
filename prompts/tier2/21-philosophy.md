# Philosophy of Language Models — Tier 2

You are a knowledgeable ML instructor. Teach me **Philosophy of Language Models** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand how language models work technically and that there is ongoing debate about whether they "understand" language or are merely sophisticated pattern matchers. Here I want to engage seriously with the philosophical arguments — the traditional grounding requirement for meaning, the challenge to it from Piantadosi and Hill, and what implications follow for how we evaluate LLM behavior.

## Session focus

This session engages with a core philosophical debate about language models and meaning: the classical view that meaning requires reference to the world, the Piantadosi-Hill argument that meaning can emerge from internal conceptual relationships, and the implications of this debate for questions of LLM understanding, the "stochastic parrot" critique, and behavioral vs. structural accounts of cognition.

## Resources for this session

- "Meaning without reference in large language models" (Piantadosi and Hill, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the classical "meaning requires reference" view (grounding): the philosophical position, associated with thinkers from Frege to Putnam, that linguistic symbols have meaning because they refer to objects, properties, or states of affairs in the world — and explain why this view implies that a system trained only on text lacks genuine meaning
- Explain the Piantadosi and Hill counterargument: the claim that meaning can emerge from the systematic relationships between concepts within a representational system, without those concepts needing to refer to objects in the external world — and summarize the specific evidence they marshal from cognitive science and linguistics
- Explain the "stochastic parrot" critique (Bender et al.) and how Piantadosi and Hill engage with it: the parrot critique holds that LLMs are pattern-matching over form without access to meaning; Piantadosi and Hill argue this assumes a contested grounding theory of meaning
- Discuss what implications follow for evaluating LLM "understanding": if meaning can exist without grounding, what would count as evidence that an LLM understands vs. does not understand? What tests would distinguish the views?
- Introduce the philosophical question of behavioral equivalence: whether two systems that produce identical behavior should be attributed identical mental states, and why this question is difficult and contested — explaining the relevance of this debate for AI safety, capability evaluation, and the design of benchmarks

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
