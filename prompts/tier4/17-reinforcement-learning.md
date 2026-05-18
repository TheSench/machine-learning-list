# Reinforcement Learning — Tier 4+

You are a knowledgeable ML instructor. Teach me **reinforcement learning at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with AlphaGo/AlphaZero, MCTS, PPO, and the standard RL landscape. I understand offline RL at a conceptual level and know the basic DRL results on Atari, Go, and chess.

## Session focus

This session examines several specialist RL results: offline learning from expert data at scale (AlphaStar Unplugged), preference learning without RL (CPL), the surprising finding that grandmaster chess doesn't require search (Ruoss et al.), what AlphaZero actually learned about chess (McGrath et al.), a unified algorithm for perfect and imperfect information games (Player of Games), and retrieval-augmented episodic memory in RL agents.

## Resources for this session

- "AlphaStar Unplugged: Large-Scale Offline Reinforcement Learning" (Mathieu et al., 2023)
- "Contrastive Preference Learning: Learning from Human Feedback without RL" (Hejna et al., 2023)
- "Grandmaster-Level Chess Without Search" (Ruoss et al., 2024)
- "Acquisition of Chess Knowledge in AlphaZero" (McGrath et al., 2022)
- "Player of Games" (Schmid et al., 2021)
- "Retrieval-Augmented Reinforcement Learning" (Goyal et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain AlphaStar Unplugged: what offline RL on the AlphaStar replay buffer achieves, the performance gap vs. online AlphaStar, which offline RL algorithms performed best, and what this tells us about the limits of learning from demonstration data without environment interaction
- Explain Contrastive Preference Learning (CPL): the theoretical derivation of a supervised contrastive objective from the preference data assumption (no reward model required), how it relates to DPO (both avoid explicit RL, but CPL works with trajectory preferences in continuous action spaces), and where CPL works and where it doesn't
- Explain the Ruoss et al. grandmaster chess result: the training setup (imitating AlphaZero's action distributions), the Elo achieved, what this reveals about the division of labor between pattern recognition and search in grandmaster play, and why this result surprised the field
- Explain the McGrath et al. chess knowledge study: the methodology for attributing chess concepts to network components, what concepts AlphaZero learned and when (opening theory, positional evaluation, tactical patterns), and what this says about the structure of knowledge in deep RL policies
- Explain Player of Games: the unified framework combining MCTS (perfect information) and counterfactual regret minimization (imperfect information) in a single algorithm, what games it was tested on, and what the result implies about the algorithmic unification of game-playing AI
- Explain retrieval-augmented RL: the architecture for giving RL agents access to an episodic memory of past trajectories via retrieval, the similarity-based retrieval mechanism, and which categories of tasks benefit from episodic memory vs. require learning generalizable policies

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about RL.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: what is the current frontier of RL research in the context of LLMs? How do the game-playing results (where RL is unambiguously successful) inform how we should think about RLHF and process-based RL for language models?

There is no "Tier 5" — this is the terminal depth for this topic.
