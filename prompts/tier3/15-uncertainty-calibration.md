# Uncertainty, Calibration, and Active Learning — Tier 3

You are a knowledgeable ML instructor. Teach me **Uncertainty, Calibration, and Active Learning at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

## What to assume about my background

I have completed all Tier 1 and Tier 2 sessions from this reading list. That means I understand:
- Neural networks, backpropagation, and gradient descent in detail
- Full transformer architecture (multi-head attention, positional encoding, layer norm, residual stream)
- Tokenization and BPE
- Major foundation models: GPT-2/3, LLaMA, InstructGPT, DeepSeek-R1/V3, Llama 3
- RLHF, DPO, GRPO, and process reward models
- Chain-of-thought, self-consistency, and test-time compute scaling
- Task decomposition, Tree of Thoughts, IDA, factored cognition
- Debate as a scalable oversight technique
- RAG, dense retrieval, and semantic embeddings
- Calibration, uncertainty estimation, and sparse autoencoders
- Mechanistic interpretability basics (activation patching, monosemanticity)
- AlphaZero, MuZero, and the connection between game RL and LLM post-training
- Scaling laws, Chinchilla, and the AI compute trajectory
- AI safety framing: misuse, misalignment, structural risks, inner/outer alignment

I understand calibration as the match between stated confidence and empirical accuracy, and I am familiar with temperature scaling as a post-hoc calibration technique. I understand that RLHF can introduce miscalibration by rewarding confident-sounding responses. I have not studied Textual Bayes, active preference inference, or natural language difference descriptions in depth.

## Session focus

Tier 3 examines practical and theoretical approaches to uncertainty in LLM-based systems: how to propagate uncertainty through multi-step pipelines (Textual Bayes), whether models can reliably verbalize their own uncertainty, Bayesian approaches to preference elicitation with minimal queries, and a novel use of LLMs to describe distributional differences — with synthesis about what good uncertainty quantification looks like in practice.

## Resources for this session

- "Textual Bayes: Quantifying Uncertainty in LLM-Based Systems" (2025)
- "Active Preference Inference using Language Models and Probabilistic Reasoning" (Handa et al., 2024)
- "Eliciting Human Preferences with Language Models" (Li et al., 2023)
- "Describing Differences between Text Distributions with Natural Language" (Zhong et al., 2022)
- "Teaching Models to Express Their Uncertainty in Words" (Lin et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain Textual Bayes: the challenge of propagating uncertainty through a chain of LLM calls (each with its own error), the proposed approach of maintaining explicit uncertainty representations as text, and where this approach succeeds and where it remains approximate
- Explain what the research shows about teaching models to verbalize uncertainty: the types of linguistic uncertainty markers models learn to use, whether verbalized uncertainty correlates with actual calibration, and what training approaches (e.g., supervised calibration examples, RLHF) improve or degrade this reliability
- Explain active preference inference: the problem of identifying user preferences efficiently with minimal questions — how Bayesian updating on response patterns (using an LLM as likelihood model) enables more targeted question selection than naive approaches
- Explain natural language difference descriptions: the task of using an LLM to characterize what changed between two text distributions (e.g., two document sets) in natural language — the methodology, where it works well, and where it produces misleading characterizations
- Synthesize what good uncertainty quantification looks like in an LLM-based system: what combination of verbalized uncertainty, output diversity measurement, consistency checks, and downstream calibration is achievable with current tools

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
