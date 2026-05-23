# Task Decomposition — Tier 2

You are a knowledgeable ML instructor. Teach me **Task Decomposition** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

At Tier 1 I learned the basic idea of iterated amplification: break complex tasks into simpler ones, use AI help for subtasks, and train a model to match the amplified human. Here I want to understand the concrete implementations — Tree of Thoughts, factored cognition, recursive summarization — and the empirical evidence about what kind of feedback most helps.

## Session focus

This session moves from the abstract principle of task decomposition to concrete algorithms and systems: Tree of Thoughts as a structured search over reasoning, factored cognition as a verification-friendly decomposition strategy, the IDA training loop in detail, recursive summarization as a practical application, and process vs. outcome feedback for math as an empirical test of the core ideas.

## Resources for this session

- "Tree of Thoughts: Deliberate Problem Solving with Large Language Models" (Yao et al., 2023)
- "Factored cognition" (Ought research post, 2019)
- "Iterated Distillation and Amplification" (Christiano, AI Alignment Forum, 2018)
- "Recursively Summarizing Books with Human Feedback" (Wu et al., OpenAI, 2021)
- "Solving math word problems with process-based and outcome-based feedback" (Uesato et al., DeepMind, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain Tree of Thoughts: representing the problem-solving process as a tree where each node is a partial reasoning state, using the model to generate candidate next steps, and using a value function (model-based or heuristic) to evaluate and prune branches — contrasting this with linear chain-of-thought
- Explain factored cognition: the strategy of decomposing a task into independent subtasks whose correctness can each be verified separately, and why verifiability of subtasks is the key property that makes human oversight tractable
- Explain the IDA training loop in detail: amplify (a human uses AI assistance to decompose a hard task and answer subtasks) → distill (train the model to match the amplified human's answers) → repeat with the improved model as the assistant
- Explain how recursive summarization works in practice: the model summarizes small chunks, then summarizes summaries, building a hierarchical structure that circumvents context length limits — and what failure modes emerge at each level
- Explain the key empirical finding from Uesato et al.: process reward models (PRMs) that score each reasoning step outperform outcome reward models (ORMs) that score only the final answer on multi-step math, and why this result supports the case for decomposition-based supervision

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
