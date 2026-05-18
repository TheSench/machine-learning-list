# Science Applications — Tier 3

You are a knowledgeable ML instructor. Teach me **Science Applications of LLMs at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand RAG and retrieval-augmented systems; I have a general sense that LLMs are being applied in scientific domains but have not studied the specific architectures or empirical evaluations of AI-for-science systems in depth. I am aware of AlphaFold as a landmark result.

## Session focus

Tier 3 examines four concrete empirical studies on LLMs applied to science: a multi-agent system designed for scientific hypothesis generation, a systematic evaluation of LLM paper review quality, clinical knowledge encoding and medical examination performance, and a broad survey of GPT-4 applied to scientific discovery tasks — with honest accounting of where the results are impressive and where they fall short.

## Resources for this session

- "Towards an AI Co-Scientist" (Gottweis et al., Google DeepMind, 2025)
- "Can large language models provide useful feedback on research papers? A large-scale empirical analysis" (Liang et al., 2023)
- "Large Language Models Encode Clinical Knowledge" (Singhal et al., Google, 2022)
- "The Impact of Large Language Models on Scientific Discovery: a Preliminary Study using GPT-4" (Microsoft Research, 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the AI Co-Scientist architecture: the role decomposition into scientist (hypothesis generation), reviewer (critical evaluation), and supervisor (experimental prioritization) agents, how the system uses iterative refinement, and what it achieved in drug repurposing tasks
- Explain the paper review evaluation: the methodology used to compare LLM-generated feedback to human reviewer feedback at scale, where the two converge (surface-level errors, basic inconsistency detection) and where they diverge (deep domain expertise, novelty assessment)
- Explain the clinical knowledge encoding result: how Med-PaLM was trained and evaluated on USMLE-style questions, what "passing" the exam means and doesn't mean, and the gap between benchmark performance and clinical reliability
- Synthesize the current picture from the Microsoft survey: identify at least three scientific task categories where LLMs appear to genuinely accelerate work, and at least two where they confidently produce plausible-sounding hallucinations that domain experts catch
- Evaluate what kinds of scientific tasks play to LLMs' strengths (synthesis, literature connection, hypothesis generation across domains) vs. tasks requiring deep formal reasoning or experimental grounding

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
