# Reinforcement Learning — Tier 2

You are a knowledgeable ML instructor. Teach me **Reinforcement Learning** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I was introduced to RL basics: agent, environment, state, action, reward, policy. I know that RLHF uses PPO to fine-tune language models. Here I want to go deeper into RL algorithms as they apply to both game-playing agents and LLM post-training, including the specific algorithms (DPO, GRPO, Reflexion) that have reshaped how language models are trained.

## Session focus

This session covers the evolution of RL algorithms relevant to both game AI (AlphaZero, MuZero) and LLM post-training (DPO, GRPO, Reflexion) — connecting the shared conceptual underpinnings and explaining what each algorithm contributes over its predecessor.

## Resources for this session

- "Mastering Chess and Shogi by Self-Play with a General Reinforcement Learning Algorithm" (Silver et al., DeepMind, 2017 — AlphaZero)
- "MuZero: Mastering Atari, Go, Chess and Shogi by Planning with a Learned Model" (Schrittwieser et al., DeepMind, 2020)
- "Direct Preference Optimization: Your Language Model is Secretly a Reward Model" (Rafailov et al., 2023)
- "DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models" (Shao et al., 2024 — introduces GRPO)
- "Reflexion: Language Agents with Verbal Reinforcement Learning" (Shinn et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain AlphaZero: how self-play generates training data, how Monte Carlo Tree Search (MCTS) uses a neural network to guide search, and why starting from random play and training purely from game outcomes ("tabula rasa") was able to surpass human-designed heuristics in chess, shogi, and Go
- Explain MuZero: the key extension over AlphaZero — learning a latent world model (predicting future states and rewards) from experience, rather than requiring the game rules to be provided — and why this allows the same algorithm to generalize to Atari games without known dynamics
- Explain DPO: how it reformulates the RLHF objective so that a language model trained directly on preference pairs (preferred vs. rejected completions) implicitly optimizes the same objective as PPO with a reward model, without requiring a separately trained reward model or a RL optimization loop
- Explain GRPO from DeepSeekMath: computing advantages for a policy update by comparing each sample's reward against the mean reward of a group of samples generated for the same prompt — eliminating the need for a separate value/critic network while retaining the benefit of relative advantage estimation
- Explain Reflexion: using verbal feedback (written critique of a previous attempt) stored in an episodic memory buffer as a substitute for gradient-based RL — the agent reads its own past failures and reasons about what to do differently, enabling improvement over multiple trials without weight updates
- Connect game-playing RL to LLM post-training: the shared concepts of policy, reward signal, and value estimation — and why game RL was a productive testbed for ideas that later migrated into language model training pipelines

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
