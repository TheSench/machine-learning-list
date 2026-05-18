# Task Decomposition — Tier 4+

You are a knowledgeable ML instructor. Teach me **task decomposition at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with Tree of Thoughts, iterated amplification, factored cognition, factored verification, and model cascades. I understand the alignment motivation for task decomposition as a scalable oversight approach.

## Session focus

This session extends the task decomposition curriculum into specialist territory: a preprocessing technique (decontextualization) that enables decomposition at the sentence level, graph-structured reasoning beyond trees, the ReAct framework for grounded tool-using agents, program-aided reasoning as a verification approach, and the Factored Cognition Primer's vision of a fully factored system.

## Resources for this session

- "Decontextualization: Making Sentences Stand-Alone" (Choi et al., 2021)
- "Graph of Thoughts: Solving Elaborate Problems with Large Language Models" (Besta et al., 2023)
- "ReAct: Synergizing Reasoning and Acting in Language Models" (Yao et al., 2022)
- "PAL: Program-aided Language Models" (Gao et al., 2022)
- "Factored Cognition Primer" (Ought — educational resource)

## Teaching objectives

By the end of this session I should be able to:
- Explain decontextualization: the task of rewriting a sentence so it is interpretable without surrounding context, why this is a precondition for reliable factored verification and retrieval, and what makes it hard (coreference, implicit context, scope)
- Explain Graph of Thoughts: how extending Tree of Thoughts to a DAG enables merging and combining reasoning branches — the formal expressive power advantage over tree-structured search and the practical complexity cost
- Explain ReAct: the Thought / Act / Observation interleaving pattern, how grounding actions in external tools (search, code execution) addresses the hallucination problem in reasoning chains, and what ReAct's failure modes are
- Explain PAL: the insight that offloading computation to a Python interpreter while keeping natural language reasoning in the LLM eliminates arithmetic and procedural errors — what categories of errors this fixes and what it doesn't
- Explain the Factored Cognition Primer's core vision: the fully factored AI system, the open problems (task decomposition doesn't obviously scale to all tasks, the bottleneck of human verification), and why this is a coherent research program rather than just a prompting technique
- Connect these techniques: explain how decontextualization, ReAct, and PAL together address different failure modes of vanilla decomposition, and where the gaps remain

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about task decomposition.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: how do these specialist techniques extend or complicate the IDA/factored cognition picture from Tiers 1–3? What would a production-grade task decomposition system look like, and what are the main unsolved problems?

There is no "Tier 5" — this is the terminal depth for this topic.
