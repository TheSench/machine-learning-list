# Tool Use and Scaffolding — Tier 4+

You are a knowledgeable ML instructor. Teach me **tool use and agent scaffolding at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

## What to assume about my background

I have completed all Tier 1, 2, and 3 sessions from this reading list. I have comprehensive knowledge of:
- Transformer internals: residual stream, circuits framework, attention as information movement, grokking, the Reversal Curse
- Foundation models: GPT-2/3, LLaMA 1/2/3, InstructGPT, DeepSeek-R1/V3, Phi-4, Titans, Byte Latent Transformer
- Training: RLHF, DPO, GRPO, μP, LoRA, QLoRA, multi-token prediction, weak-to-strong generalization
- Reasoning: CoT, self-consistency, test-time scaling, s1, the self-correction failure, grokking
- Task decomposition: Tree of Thoughts, IDA, factored cognition, factored verification, model cascades
- Debate: debate framework, prover-verifier games, obfuscation, multiagent debate
- Interpretability: SAEs, monosemanticity, activation patching, representation engineering, influence functions
- Alignment faking, scheming, emergent misalignment, gradual disempowerment
- Scaling: Chinchilla, emergent abilities controversy, infinite compute analysis

I understand ReAct, PAL, and standard tool-use patterns. I am familiar with basic agent architectures: memory, planning, action loops.

## Session focus

This session covers the frontier of agent scaffolding: programmatic pipeline optimization (DSPy), self-referential prompt evolution (Promptbreeder), recursive self-improvement via code generation (STOP), and an open-ended embodied agent that builds its own skill library (Voyager) — moving from prompt engineering as craft to prompt engineering as optimization problem.

## Resources for this session

- "DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines" (Khattab et al., 2023)
- "Promptbreeder: Self-Referential Self-Improvement Via Prompt Evolution" (Fernando et al., 2023)
- "Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation" (Zelikman et al., 2023)
- "Voyager: An Open-Ended Embodied Agent with Large Language Models" (Wang et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain DSPy's core abstraction: modules and signatures as the structural specification of a pipeline, and compilation as the process that optimizes prompt strings and few-shot examples for a downstream metric — why this separation of structure from prompts matters for maintainability and optimization
- Explain DSPy's optimization algorithms (BootstrapFewShot, etc.) and their limitations: when compilation works, when it overfits to the metric, and what this implies about the reliability of automated prompt optimization
- Explain Promptbreeder: the co-evolution of task prompts and mutation operators, the self-referential loop (the mutation operators are themselves prompts), what it achieves over manual prompt engineering, and the stability/diversity tradeoff
- Explain STOP: the architecture for using LLMs to rewrite their own optimization algorithms in code, the bootstrapping problem (you need a reasonable optimizer to improve), the limits imposed by the code execution environment, and how close this is to genuine recursive self-improvement
- Explain Voyager: the three components (automatic curriculum, skill library, iterative prompting mechanism), how the agent acquires and reuses skills across tasks, what the Minecraft domain reveals about open-ended learning, and what would need to change for this to generalize beyond games
- Characterize what each paper contributes to a theory of automated agent improvement: DSPy (metric-driven compilation), Promptbreeder (evolutionary search), STOP (code-level meta-optimization), Voyager (environmental curriculum)

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about tool use and scaffolding.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: what are the current limits of automated agent self-improvement, and what would it take to cross from "better prompts" to something that constitutes genuine capability amplification? Where does this connect to the scalable oversight problem?

There is no "Tier 5" — this is the terminal depth for this topic.
