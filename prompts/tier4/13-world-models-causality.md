# World Models and Causality — Tier 4+

You are a knowledgeable ML instructor. Teach me **world models and causal reasoning in LLMs at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with the Tier 3 discussion of world models: the evidence for and against LLMs having implicit world models, Othello-GPT and related probing experiments, and the general question of whether next-token prediction gives rise to causal understanding.

## Session focus

This session examines causal reasoning in LLMs through Pearl's ladder of causation, probabilistic inference with LLMs, the Generative Agents social simulation, and amortized inference — providing both the evaluation framework and the technical machinery for using LLMs as components in Bayesian and causal reasoning systems.

## Resources for this session

- "CLADDER: Assessing Causal Reasoning in Language Models" (Jin et al., 2023)
- "Causal Reasoning and Large Language Models: Opening a New Frontier for Causality" (Kıcıman et al., 2023)
- "Amortizing intractable inference in large language models" (Hu et al., 2023)
- "Generative Agents: Interactive Simulacra of Human Behavior" (Park et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain Pearl's ladder of causation as an evaluation framework: association (observational), intervention (do-calculus), and counterfactual rungs — what each requires computationally, and what CLADDER measures at each level
- Explain CLADDER's results: where current LLMs succeed and fail across the three rungs, which failure patterns are systematic, and what they reveal about the nature of LLM causal processing
- Explain the Kıcıman et al. comparison: how LLM causal claims compare to ground truth from causal discovery benchmarks, the patterns of overconfidence and the specific types of causal questions LLMs handle reliably vs. not
- Explain amortized inference with LLMs: the technical setup (fine-tuning to approximate an intractable posterior), what classes of probabilistic inference problems this enables, the GFlowNet connection, and what the approach assumes about the training distribution
- Explain Generative Agents' architecture: the memory stream (raw observations), the reflection mechanism (periodic synthesis into higher-level beliefs), the planning layer, and the retrieval scoring function — and which architectural choices turned out to be load-bearing
- Explain what Generative Agents reveals about LLM agency: which social behaviors emerged that weren't explicitly programmed, what failed or required extensive scaffolding, and what conclusions can reasonably be drawn about LLM social modeling
- Synthesize: are LLMs doing causal reasoning or sophisticated causal pattern matching? What would distinguish these, and does the distinction matter for applications?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about world models and causality.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given CLADDER and Kıcıman et al., what is the most defensible account of LLM causal competence in 2025? What would need to be true for LLMs to serve as reliable components in causal reasoning pipelines?

There is no "Tier 5" — this is the terminal depth for this topic.
