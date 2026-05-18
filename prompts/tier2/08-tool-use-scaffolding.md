# Tool Use and Scaffolding — Tier 2

You are a knowledgeable ML instructor. Teach me **Tool Use and Scaffolding** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand that language models generate text token by token and can be prompted in sophisticated ways. Here I want to understand how wrapping a model in external tools and scaffolding fundamentally changes what it can accomplish — and what the implications are for capability evaluation.

## Session focus

This session covers how scaffolding (tools, retrieval, code execution, memory, multi-step loops) extends LLM capability beyond what the base model can do in a single forward pass, with WebGPT as a concrete case study and the elicitation gap as the key conceptual framing.

## Resources for this session

- "WebGPT: Browser-assisted question-answering with human feedback" (Nakano et al., OpenAI, 2021)
- "Measuring the impact of post-training enhancements" (METR autonomy evals guide, 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain what "scaffolding" means for LLMs: the software layer that wraps a model with access to tools (web search, code execution, file I/O, APIs, memory stores) and manages the multi-turn loop of calling tools and returning results to the model
- Explain WebGPT in detail: how the model was given a browser as a tool, the imitation learning and RLHF training procedure adapted for tool-augmented behavior, and the evaluation methodology against human-written answers with references
- Explain the "elicitation gap": the difference between a model's latent capability (what it could do given ideal prompting, tools, and interaction) and what we can reliably elicit in practice — and why this gap is important for both capability evaluation and safety assessment
- Explain why improving scaffolding can matter as much as improving the base model: a better tool loop or retrieval system can unlock capability that was already present in the model but not accessible
- Identify common scaffolding patterns in current AI systems: tool call / function calling APIs, retrieval-augmented generation, multi-step planning with a controller, reflection loops where the model evaluates its own previous outputs

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
