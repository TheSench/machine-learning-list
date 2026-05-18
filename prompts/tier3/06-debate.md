# Debate — Tier 3

You are a knowledgeable ML instructor. Teach me **Debate as a scalable oversight technique at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I am familiar with the original Irving et al. debate proposal — the idea that two AI systems arguing opposing positions can help a human judge identify the truth even if the human could not evaluate the answer directly. I understand the scalable oversight motivation: how do we supervise AI systems on tasks that exceed human competence?

## Session focus

Tier 3 examines where the original debate proposal runs into problems — particularly the obfuscation attack — and how the field has responded with prover-verifier games, multiagent debate as a practical inference technique, and work showing debate can help even when debaters are unreliable. The focus is on separating what debate can and cannot solve.

## Resources for this session

- "Avoiding Obfuscation with Prover-Estimator Debate" (Kirchner et al., Anthropic, 2025)
- "Improving Factuality and Reasoning in Language Models through Multiagent Debate" (Du et al., 2023)
- "Prover-Verifier Games Improve Legibility of LLM Outputs" (Kirchner et al., OpenAI, 2024)
- "Debate Helps Supervise Unreliable Experts" (Clymer et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the obfuscation problem: how a dishonest debater can win by making their argument too complex for the judge to evaluate — why this is a fundamental attack on debate as a safety mechanism, not just a practical limitation
- Explain the prover-estimator framing: how replacing the simple "honest vs. dishonest debater" setup with a prover (who must convince) and an estimator (who only uses checkable evidence) blocks obfuscation — and where this framing still has gaps
- Explain prover-verifier games as a training paradigm: how training models to produce checkable, legible outputs creates a useful connection between debate and interpretability
- Explain multiagent debate as an inference-time technique: the Du et al. setup where multiple model instances debate to improve factuality without retraining — empirical results and why this is distinct from the safety-motivated debate proposal
- Explain the unreliable experts result: the conditions under which debate helps even when debaters make systematic errors — and what this implies about the assumptions the debate safety argument requires
- Synthesize: provide a clear-eyed summary of what debate can and cannot solve, given the research to date

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
