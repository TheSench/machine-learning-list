# Training and Finetuning — Tier 2

You are a knowledgeable ML instructor. Teach me **Training and Finetuning** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I know that models are trained by minimizing a loss via gradient descent, and that fine-tuning adapts a pretrained model to a downstream task. Here I want to understand the practical engineering of training runs — how to set hyperparameters, how to transfer them across scales — and the feedback mechanisms (reward models, verifiers) that shape what behavior is reinforced.

## Session focus

This session covers the practical craft of training large neural networks: principled hyperparameter tuning, the μP framework for scale-invariant hyperparameter transfer, and the reward modeling pipeline — including the critical distinction between outcome-level and process-level feedback.

## Resources for this session

- "Deep Learning Tuning Playbook" (Goyal et al., Google Research, 2023)
- "Tensor Programs V: Tuning Large Neural Networks via Zero-Shot Hyperparameter Transfer" (Yang et al., 2022 — introduces μP)
- "Learning to summarise with human feedback" (Stiennon et al., OpenAI, 2020)
- "Training Verifiers to Solve Math Word Problems" (Cobbe et al., OpenAI, 2021)

## Teaching objectives

By the end of this session I should be able to:
- Explain practical hyperparameter tuning: the most impactful knobs (learning rate, batch size, warmup steps), how learning rate schedules (cosine decay, linear warmup) work and why they matter, and the general strategy of tuning in order of expected impact
- Explain why naive hyperparameter transfer from small to large models fails: how the optimal learning rate depends on model width in a way that breaks at scale under standard parameterization
- Explain μP (maximal update parameterization): how it rescales weight updates so that the optimal hyperparameters found at small scale transfer to larger models without re-tuning, and why this matters for the economics of large training runs
- Explain how RLHF was applied to summarization in Stiennon et al.: the reward model training pipeline (human comparisons → Bradley-Terry model), the PPO fine-tuning loop, and how the resulting policy was evaluated against reference summaries
- Explain the difference between outcome reward models (ORMs) and process reward models (PRMs): ORMs score the final answer, PRMs score each step of a reasoning trace — and when PRMs outperform ORMs (e.g., multi-step math)
- Explain why verifiers improve accuracy: using a trained model to re-rank a set of candidate solutions at inference time can outperform training for direct answer generation, because verification is an easier task than generation

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
