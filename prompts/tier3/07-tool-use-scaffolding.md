# Tool Use and Scaffolding — Tier 3

You are a knowledgeable ML instructor. Teach me **Tool Use and Scaffolding at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand function calling, ReAct-style tool use, and basic agent scaffolding patterns. I am familiar with prompt engineering as a practice but have not studied TextGrad, GEPA, or automated model discovery in depth. I understand the conceptual distinction between elicitation and training.

## Session focus

Tier 3 examines what happens when we apply optimization pressure to the scaffolding itself — TextGrad treating text feedback as a surrogate gradient, GEPA evolving prompts reflectively, and automated statistical model discovery using LLMs as search agents — plus the empirical finding on how much scaffolding improvements can substitute for model retraining.

## Resources for this session

- "Executable Code Actions Elicit Better LLM Agents" (Wang et al., 2024)
- "GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning" (2025)
- "TextGrad: Automatic 'Differentiation' via Text" (Yuksekgonul et al., 2024)
- "AI capabilities can be significantly improved without expensive retraining" (Zhou et al., 2023)
- "Automated Statistical Model Discovery with Language Models" (Runge et al., 2024)

## Teaching objectives

By the end of this session I should be able to:
- Explain code actions: why having agents produce executable Python rather than natural language actions improves reliability, composability, and error recovery — and the empirical gap observed between code-action and text-action agents on benchmark tasks
- Explain TextGrad: the analogy between scalar gradient descent and text feedback propagation through a computation graph of LLM calls — how feedback is "backpropagated" through the system, what kinds of pipelines it has been applied to, and what its limitations are
- Explain GEPA: reflective prompt evolution using an LLM to generate, evaluate, and select improved prompts iteratively — the claim that it can match or outperform RL-based prompt optimization, and the conditions under which this holds
- Explain the elicitation gap finding: the empirical evidence that post-training scaffolding (prompting, tool access, memory management) can substantially close capability gaps without retraining — what this means for the distinction between "model capability" and "deployed system capability"
- Explain automated statistical model discovery: using LLMs as search agents over a space of model families, what kinds of models they can and cannot discover, and where this approach falls short compared to traditional model selection
- Synthesize: what does the ability to "differentiate through text" imply about the future of ML pipeline optimization?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
