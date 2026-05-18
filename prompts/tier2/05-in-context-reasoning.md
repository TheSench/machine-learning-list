# In-Context Reasoning — Tier 2

You are a knowledgeable ML instructor. Teach me **In-Context Reasoning** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned about few-shot prompting as an emergent capability of large models. Here I want to understand the specific prompting techniques — chain-of-thought, zero-shot CoT, self-consistency — that substantially improve reasoning performance, and the broader concept of test-time compute scaling.

## Session focus

This session moves from few-shot prompting as a general capability to specific in-context reasoning techniques: chain-of-thought prompting, zero-shot CoT, self-consistency decoding, and the emerging paradigm of test-time compute scaling as an alternative to training-time scaling.

## Resources for this session

- "Chain of Thought Prompting Elicits Reasoning in Large Language Models" (Wei et al., Google, 2022)
- "Large Language Models are Zero-Shot Reasoners" (Kojima et al., 2022 — "Let's think step by step")
- "Self-Consistency Improves Chain of Thought Reasoning in Language Models" (Wang et al., 2022)
- "Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters" (Snell et al., 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain chain-of-thought prompting: providing examples that include explicit intermediate reasoning steps in the prompt, and why eliciting written-out reasoning substantially improves accuracy on multi-step problems
- Explain the "Let's think step by step" finding from Kojima et al.: that appending a single phrase to a question (zero-shot CoT) is sufficient to trigger step-by-step reasoning without any examples, and why this is surprising given prior few-shot paradigms
- Explain self-consistency: sampling many reasoning chains with temperature > 0, then taking a majority vote over the final answers — why this outperforms greedy decoding and when the gains are largest
- Explain the Snell et al. test-time compute scaling result: that spending more inference compute (more generation steps, more candidates, better search) can match or exceed the gains from training a larger model, and what the compute-optimal strategy looks like
- Contrast training-time scaling (larger models, more data, more training compute) with test-time scaling (more compute per inference) as two orthogonal axes for improving capability, and explain the tradeoffs between them (amortized vs. per-query cost)

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
