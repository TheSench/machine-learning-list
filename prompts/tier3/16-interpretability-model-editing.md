# Interpretability and Model Editing — Tier 3

You are a knowledgeable ML instructor. Teach me **Interpretability and Model Editing at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand sparse autoencoders as a method for decomposing superposed representations into interpretable features, and I understand the monosemanticity hypothesis. I am familiar with activation patching and causal tracing. I have not studied the scaling properties of SAEs at large dictionary sizes, representation engineering, what finetuning mechanistically does to circuits, or influence functions for LLMs in depth.

## Session focus

Tier 3 examines what happens when interpretability methods are pushed to scale: feature splitting and absorption in large SAEs, a top-down approach to reading and writing model behaviors through activation steering, mechanistic analysis of finetuning's effects, and a method for tracing model outputs back to specific training examples — with synthesis of what each level of analysis can and cannot tell us.

## Resources for this session

- "Scaling and Evaluating Sparse Autoencoders" (Gao et al., OpenAI, 2024)
- "Opening the AI black box: program synthesis via mechanistic interpretability" (Michaud et al., 2024)
- "Mechanistically analyzing the effects of fine-tuning on procedurally defined tasks" (Jain et al., 2023)
- "Representation Engineering: A Top-Down Approach to AI Transparency" (Zou et al., 2023)
- "Studying Large Language Model Generalization with Influence Functions" (Grosse et al., Anthropic, 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the scaling SAE findings from Gao et al.: what feature splitting means (a single feature at smaller dictionary sizes decomposes into multiple more specific features at larger sizes), what absorption is (a feature absorbs the function of what should be a separate feature), and what these phenomena imply for the interpretability project
- Explain representation engineering: the approach of identifying a "concept direction" in activation space (via contrastive pairs), then reading or writing model behaviors by projecting onto or steering along that direction — with examples and a clear account of how this differs from and complements circuit-level mechanistic interpretability
- Explain what finetuning mechanistically does to procedurally defined task circuits: does finetuning reroute existing computation, add new circuits, or patch outputs? What the Jain et al. findings show and why the answer matters for safety-relevant finetuning
- Explain influence functions for large LLMs: what an influence function measures (how much a training example contributed to a specific prediction), the computational challenges at LLM scale, how Grosse et al. made this tractable with the EK-FAC approximation, and what the results revealed about LLM generalization
- Explain the program synthesis result: using mechanistic interpretability to recover the algorithm a small network learned — what this approach can teach us and what limits it has at larger scale
- Synthesize: map out the interpretability toolbox — circuit-level analysis, SAEs, representation engineering, influence functions — and explain what level of question each tool is suited to answer

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
