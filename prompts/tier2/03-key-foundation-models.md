# Key Foundation Model Architectures — Tier 2

You are a knowledgeable ML instructor. Teach me **Key Foundation Model Architectures** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned about GPT-2 and GPT-3 as milestone models. Here I want to understand the subsequent generation of models — LLaMA, InstructGPT, Llama 3, and DeepSeek — and the key architectural and training decisions that now define the frontier.

## Session focus

This session extends the foundation model history beyond GPT-3 to cover the open-weight model ecosystem (LLaMA, Llama 3), the instruction-tuning paradigm (InstructGPT/RLHF), and the latest generation of efficiency and reasoning innovations from DeepSeek, identifying what architectural and training choices now separate leading models.

## Resources for this session

- "LLaMA: Open and Efficient Foundation Language Models" (Touvron et al., Meta, 2023)
- "Training language models to follow instructions with human feedback" (InstructGPT, Ouyang et al., OpenAI, 2022)
- "The Llama 3 Herd of Models" (Meta, 2024)
- "DeepSeek-V3 Technical Report" (DeepSeek, 2024)
- "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning" (DeepSeek, 2025)

## Teaching objectives

By the end of this session I should be able to:
- Explain what LLaMA contributed: releasing competitive open-weight models trained on publicly available data, enabling broad research access and reproducibility at a time when frontier models were closed
- Explain the InstructGPT/RLHF pipeline in detail: the three-stage process of supervised fine-tuning on human demonstrations, training a reward model on human preference comparisons, and optimizing the language model against that reward using PPO
- Explain what Llama 3 improved over the original LLaMA: significantly more training data (15T+ tokens), extended context length, a more sophisticated post-training recipe including preference optimization, and multimodal extensions
- Explain DeepSeek-V3's key innovations: a mixture-of-experts (MoE) architecture that activates only a subset of parameters per token, and training efficiency techniques that achieved competitive performance at substantially lower compute cost
- Explain DeepSeek-R1: using reinforcement learning with verifiable reward signals (correct/incorrect on math and code) to train chain-of-thought reasoning, and how this approach produces models that explicitly reason before answering
- Identify the key axes that now differentiate frontier models: pretraining data scale and quality, post-training alignment recipe, architecture choices (dense vs. MoE), context length, and reasoning capability

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
