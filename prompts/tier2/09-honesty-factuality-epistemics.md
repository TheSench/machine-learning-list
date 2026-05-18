# Honesty, Factuality, and Epistemics — Tier 2

You are a knowledgeable ML instructor. Teach me **Honesty, Factuality, and Epistemics** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I know that language models sometimes produce false or misleading outputs (hallucinations) and that this is a practical problem. Here I want to understand the self-critique approach as a systematic intervention — both its mechanism and its limitations — and sharpen the conceptual distinction between factual error and epistemic miscommunication.

## Session focus

This session examines self-critiquing as a scalable approach to improving output quality and assisting human evaluators — covering the experimental setup from Saunders et al., the conditions under which model-generated critiques are useful, and the important distinction between a model being wrong and a model being misleading.

## Resources for this session

- "Self-critiquing models for assisting human evaluators" (Saunders et al., OpenAI, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the self-critique experimental setup from Saunders et al.: a model (or a separate critic model) generates written critiques of answers, human evaluators then judge which answers are better with or without the critique, and the study measures whether critiques help humans catch errors
- Explain how self-critique can scale human evaluation: critics can flag potential issues across many outputs faster than evaluators can read them in full, allowing human attention to be focused on flagged cases — and explain where this works and where it breaks down
- Explain the key limitation of self-critique: models may systematically fail to critique errors that they themselves tend to make, and may produce confident-sounding critiques that are themselves wrong — so the approach does not substitute for independent verification
- Distinguish between a model being factually wrong (incorrect information) and a model being misleading (presenting uncertain, ambiguous, or probabilistic claims with more confidence than warranted) — and explain why the second category is harder to detect and potentially more dangerous
- Explain what "epistemic cowardice" looks like in model outputs and why training incentives can push models toward vague or hedge-everything responses as a strategy to avoid being caught being wrong

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
