# Transformers — Tier 2

You are a knowledgeable ML instructor. Teach me **Transformers** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned that transformers use attention over tokens and that GPT-2/GPT-3 are transformer-based language models. Here I want to understand the full architecture in detail, where attention came from historically, and how a pretrained model becomes an instruction-following assistant.

## Session focus

This session moves from a conceptual picture of attention and transformers to the precise architectural components of GPT-2 (multi-head attention, layer norm, positional encoding, residual connections), the historical path through seq2seq neural machine translation that produced attention, and the RLHF pipeline that converts a base language model into a useful assistant.

## Resources for this session

- "Deep Dive into LLMs like ChatGPT" (Andrej Karpathy, YouTube, 2024)
- "Let's build the GPT Tokenizer" (Andrej Karpathy, YouTube, 2024)
- "The Illustrated GPT-2 (Visualizing Transformer Language Models)" (Jay Alammar, 2019)
- "Neural Machine Translation by Jointly Learning to Align and Translate" (Bahdanau et al., 2015) — the paper that introduced attention
- "Attention Is All You Need" (Vaswani et al., 2017)

## Teaching objectives

By the end of this session I should be able to:
- Explain tokenization in detail: how byte-pair encoding (BPE) builds a vocabulary by iteratively merging common byte pairs, and why tokenization choices affect model behavior (e.g., numbers, non-English text, whitespace sensitivity)
- Describe each component of the GPT-2 architecture in order: token embedding, positional encoding, multi-head self-attention, layer normalization, feed-forward sublayer, and residual connections — and explain the role each plays
- Explain what multi-head attention computes: the Q, K, V projection, the scaled dot-product, the softmax, and why multiple heads allow the model to attend to different representation subspaces simultaneously
- Explain where attention came from: the problem with fixed-length bottlenecks in encoder-decoder RNNs that Bahdanau et al. solved by letting the decoder attend over all encoder hidden states
- Explain what "Attention Is All You Need" replaced (RNN/LSTM-based seq2seq), why self-attention is more parallelizable than recurrence, and why it avoids the vanishing gradient problem over long sequences
- Explain at a high level how RLHF turns a pretrained LLM into an instruction-following assistant: supervised fine-tuning on demonstrations, reward model training on human preference comparisons, and PPO fine-tuning against the reward model

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
