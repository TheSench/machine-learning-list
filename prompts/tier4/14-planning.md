# Planning — Tier 4+

You are a knowledgeable ML instructor. Teach me **LLM-based planning at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with Tree of Thoughts, the ReAct framework, Voyager, and the general LLM-as-agent literature. I understand the planning-as-search framing and the distinction between system 1 (fast, amortized) and system 2 (slow, deliberate) reasoning.

## Session focus

This session examines two complementary specialist contributions: a hybrid transformer/search approach that beats pure learned policies by using search as a runtime inference procedure (Lehnert et al.), and a principled taxonomy of the design space for language agents (Sumers et al.) — providing both a concrete technique and a conceptual framework for evaluating planning systems.

## Resources for this session

- "Beyond A*: Better Planning with Transformers via Search Dynamics Bootstrapping" (Lehnert et al., 2024)
- "Cognitive Architectures for Language Agents" (Sumers et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the core insight of Lehnert et al.: using transformers to learn search heuristics rather than policies, so that the transformer guides tree search rather than replaces it — why this outperforms both A* (better heuristics) and pure neural policies (runtime search)
- Explain Search Dynamics Bootstrapping: the training procedure that uses successful search trajectories as supervision, why this is a form of self-play, and the connection to AlphaZero-style value network training
- Explain what the Lehnert et al. results imply for the "can LLMs plan?" debate: the distinction between amortized planning (policy) and runtime planning (search), and which problems require which
- Explain the Sumers et al. cognitive architecture taxonomy: the four memory types (in-context, external episodic, external semantic, parametric), the action type taxonomy (memory manipulation, process execution, UI actions, service calls, cross-agent communication), and why this taxonomy is useful for designing and evaluating agents
- Explain what the taxonomy reveals about current LLM agents: which components are mature, which are missing or unreliable, and what architectural choices have the most leverage
- Connect these two papers: how does the search dynamics bootstrapping approach fit into the Sumers et al. architecture framework? Which memory type does the bootstrapped heuristic correspond to?
- Synthesize with the broader task decomposition curriculum: when does search-guided planning add the most value relative to decomposition approaches, and when is decomposition sufficient?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about LLM planning.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given Lehnert et al., Sumers et al., and the broader test-time compute literature, what is the current best approach to building reliable planning systems with LLMs?

There is no "Tier 5" — this is the terminal depth for this topic.
