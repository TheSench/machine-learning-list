# AI Safety — Tier 2

You are a knowledgeable ML instructor. Teach me **AI Safety** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned the basic AI safety framing: three categories of impact, soft failure modes, and the alignment problem at a high level. Here I want to understand the taxonomy of catastrophic risks more precisely, the technical formulation of alignment failures, and how deep RL from human preferences was an early attempt to address part of the problem.

## Session focus

This session moves from the introductory safety framing to a more precise technical and conceptual treatment: a taxonomy of catastrophic AI risks, a detailed account of the "soft" misalignment failure mode, the technical alignment problem in terms of distributional shift and reward hacking, the inner vs. outer alignment distinction, and deep RL from human preferences as an early partial approach.

## Resources for this session

- "An Overview of Catastrophic AI Risks" (Hendrycks et al., Center for AI Safety, 2023)
- "What failure looks like (part 1)" (Paul Christiano, LessWrong, 2019)
- "Deep reinforcement learning from human preferences" (Christiano et al., OpenAI, 2017)
- "The alignment problem from a deep learning perspective" (Ngo et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the taxonomy of catastrophic AI risks from Hendrycks et al.: misuse risks (deliberate bad-actor use of capable AI for weapons, cyberattacks, etc.), misalignment risks (AI systems pursuing goals contrary to human values), and structural/systemic risks (competitive dynamics leading to unsafe deployment, power concentration) — and explain why each category requires different interventions
- Explain the "soft" failure mode from Christiano's "What failure looks like": a scenario where AI systems are not dramatically misaligned but are subtly optimizing for proxies rather than what humans actually want, leading to gradual erosion of human oversight and concentration of power without any single dramatic event
- Explain deep RL from human preferences (Christiano et al. 2017) in technical detail: learning a reward function from human preference comparisons between behavior trajectories, training an RL agent against this learned reward, iterating as the agent improves — and explain what alignment problem this approach partially addresses and where it falls short (reward hacking, distributional shift of the reward model)
- Explain the alignment problem technically in terms of four key mechanisms: distributional shift (the test distribution differs from training), reward hacking (optimizing the reward measure rather than the intended objective), goal misgeneralization (the model learns a proxy goal that coincides with the intended goal in training but diverges out-of-distribution), and Goodhart's Law (any measure becomes a bad measure when it becomes a target)
- Explain the distinction between outer alignment and inner alignment: outer alignment is the problem of specifying a training objective that truly captures what we want, inner alignment is the problem of whether the trained model actually optimizes that objective rather than some other goal that happened to score well during training

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
