# Debate — Tier 2

You are a knowledgeable ML instructor. Teach me **Debate** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I encountered the scalable oversight problem: how do we supervise AI systems that may be smarter than their evaluators? Here I want to understand debate as a specific proposed solution — its mechanics, its theoretical justification, its assumptions, and its failure modes.

## Session focus

This session examines AI safety via debate as a concrete mechanism for scalable oversight: how the protocol works, the game-theoretic argument for why it should favor truth, the critical assumptions it requires, and what we do not yet know about whether those assumptions hold in practice.

## Resources for this session

- "AI safety via debate" (Irving, Christiano, and Amodei, OpenAI, 2018)

## Teaching objectives

By the end of this session I should be able to:
- Explain the debate framework mechanically: two AI agents are given a question, argue for different answers in alternating turns, and a human judge picks the winner — and explain how training proceeds from these judged debates
- Explain the theoretical argument for why debate should favor truth: a good counter-argument is easier to verify than to construct, so an honest debater should be able to expose a deceptive debater's errors even when the judge cannot evaluate the original answer directly
- Explain the key assumptions debate requires: that the judge is capable of evaluating arguments (even if not the original question), that truth is generally easier to defend than falsehood against a sufficiently skilled opponent, and that deceptive strategies are bounded in some way
- Identify the main open questions and failure modes: what happens if both debaters collude or are both deceptive? What if the human judge can be systematically confused by sophisticated but misleading arguments? What is the evidence base so far?
- Connect debate to the broader scalable oversight agenda: why this class of technique — using AI to help humans evaluate AI — becomes critical when AI systems exceed human capability in the relevant domain, and how debate relates to other approaches like amplification

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
