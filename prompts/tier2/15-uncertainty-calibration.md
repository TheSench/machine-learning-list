# Uncertainty, Calibration, and Active Learning — Tier 2

You are a knowledgeable ML instructor. Teach me **Uncertainty, Calibration, and Active Learning** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand that ML models output predictions (and often probabilities), but haven't studied the question of whether those probabilities accurately reflect the model's actual uncertainty. Here I want to understand calibration as a formal property, how to measure and improve it, and how pretrained models can be leveraged for uncertainty estimation without retraining from scratch.

## Session focus

This session covers the formal notion of calibration, practical methods for measuring it (reliability diagrams, ECE), deep ensembles and SWAG as tractable uncertainty estimates for deep networks, the predicting-pairs approach as a model-disagreement signal, and how large pretrained models can be extended for calibrated uncertainty without full retraining.

## Resources for this session

- "A Simple Baseline for Bayesian Uncertainty in Deep Learning" (Maddox et al., 2019 — SWAG / deep ensembles context)
- "Experts Don't Cheat: Learning What You Don't Know By Predicting Pairs" (Steinhardt et al., 2023)
- "Plex: Towards Reliability using Pretrained Large Model Extensions" (Tran et al., Google, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain what calibration means precisely: a model is well-calibrated when, among all predictions where it assigns probability p to an outcome, that outcome actually occurs with frequency p — and give an example of a miscalibrated model (e.g., one that says 90% confident but is right only 70% of the time)
- Explain how to measure calibration: reliability diagrams (plotting predicted confidence vs. empirical accuracy across confidence bins) and expected calibration error (ECE, the weighted average deviation across bins)
- Explain deep ensembles as a practical uncertainty estimate: training multiple models with different random seeds and using the variance across their predictions as an uncertainty signal — why this works better than a single model's softmax probabilities, and the computational cost tradeoff
- Explain the predicting-pairs approach from Steinhardt et al.: training models to predict whether two examples will have the same label, and using disagreement between a model's direct prediction and its pair-prediction as a signal of uncertainty or distributional shift
- Explain the Plex approach: extending a large pretrained model with lightweight uncertainty heads or ensembles to achieve reliable uncertainty estimates without retraining the full model from scratch, and why the pretrained representations provide a strong foundation for this

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
