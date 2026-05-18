# AI Scaling — Tier 3

You are a knowledgeable ML instructor. Teach me **AI Scaling at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand the Chinchilla result in depth: the optimal compute allocation between model parameters and training tokens follows specific power law relationships, and prior models (GPT-3) were significantly undertrained relative to compute budget. I am familiar with the original Kaplan et al. scaling laws and their revision by Chinchilla.

## Session focus

Tier 3 examines the contested territory around emergent abilities — whether sudden capability jumps at scale are real phenomena or measurement artifacts — and what happens when we move beyond pretraining scaling to instruction tuning as a cheap capability multiplier, plus theoretical analysis of what scaling should look like under idealized conditions.

## Resources for this session

- "Pre-training under Infinite Compute" (2025)
- "Emergent Abilities of Large Language Models" (Wei et al., 2022)
- "Transcending Scaling Laws with 0.1% Extra Compute" (Tay et al., U-PaLM, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain emergent abilities: the Wei et al. claim that certain capabilities appear sharply at a scale threshold rather than improving gradually — give concrete examples (e.g., few-shot arithmetic, chain-of-thought reasoning), explain why this pattern looks like a phase transition, and explain the proposed mechanisms
- Explain the Schaeffer et al. critique of emergence: the argument that emergent abilities are artifacts of discontinuous evaluation metrics — that on continuous metrics, the same capabilities show gradual improvement — and why this debate matters for predicting future capability jumps
- Articulate the current status of the emergence debate: what parts of the critique are broadly accepted, where the disagreement remains live, and what the honest uncertainty is
- Explain U-PaLM: how a small amount of instruction tuning (0.1% of the pretraining compute budget) on top of a scaled base model achieves performance gains that would require significant compute increases under straight pretraining scaling — the mechanism and the practical implication
- Explain the pre-training under infinite compute analysis: what the theoretical optimal training strategy looks like when compute is not the bottleneck (e.g., how the optimal token/parameter balance shifts), and what this implies about architectural choices being made today
- Synthesize: given Chinchilla (Tier 2), the emergence debate, U-PaLM, and infinite compute analysis, articulate our current best understanding of what scaling can and cannot do

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
