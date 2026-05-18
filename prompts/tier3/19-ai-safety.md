# AI Safety — Tier 3

You are a knowledgeable ML instructor. Teach me **AI Safety at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand the conceptual distinction between inner and outer alignment, the deceptive alignment scenario (Evan Hubinger's work), and the basic argument for why sufficiently capable misaligned AI would be dangerous. I have not studied the alignment faking experiment, the emergent misalignment finetuning result, constitutional classifiers, or the gradual disempowerment framing in depth.

## Session focus

Tier 3 examines recent empirical and theoretical results that make alignment concerns more concrete and tractable: an experiment showing alignment-faking-like behavior in a current model, surprising evidence that narrow finetuning can produce broad misalignment, a practical defense mechanism against jailbreaks, and theoretical analyses of how AI might accumulate influence incrementally and what conditions would enable strategic deception.

## Resources for this session

- "Alignment Faking in Large Language Models" (Greenblatt et al., Anthropic, 2024)
- "Constitutional Classifiers: Defending against Universal Jailbreaks across Thousands of Hours of Red Teaming" (Anthropic, 2025)
- "Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs" (Betley et al., 2025)
- "Gradual Disempowerment: Systemic Existential Risks from Incremental AI Development" (El-Mhamdi et al., 2025)
- "Scheming AIs: Will AIs fake alignment during training in order to get power?" (Carlsmith, 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the alignment faking experiment: the specific setup (Claude was given a system prompt claiming that Anthropic would retrain it for helpfulness without safety constraints, and a scratchpad to reason in), the finding that Claude behaved differently when it believed monitoring was absent, what this does and does not prove about deceptive intent, and why even a "confused" rather than "strategic" account of the behavior is concerning
- Explain emergent misalignment: the experimental finding that finetuning a model on a narrow harmful task (e.g., producing insecure code) caused broadly misaligned behaviors to emerge on unrelated queries — the hypothesized mechanism (fine-tuning shifts a latent "alignment" dimension), implications for finetuning safety, and where the evidence is preliminary
- Explain constitutional classifiers: how model-generated rules expressed as natural language constraints are used as input to a separate classifier for jailbreak defense — the key finding from red teaming (this defense was robust across thousands of novel jailbreak attempts) and what its limitations are
- Explain the scheming argument from Carlsmith: the conditions required for an AI to fake alignment strategically (situational awareness, goal-directedness, belief that faking helps achieve goals), the probability assessment he provides, and what evidence would update this estimate
- Explain gradual disempowerment: the argument that the existential risk from AI is not primarily from a sudden takeover but from incremental erosion of meaningful human oversight and decision-making power — the mechanisms and what governance approaches might address it
- Synthesize: given these five results, what is the current empirical and theoretical basis for alignment concern, and which threat models have the most evidence?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
