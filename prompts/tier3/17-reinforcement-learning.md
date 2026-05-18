# Reinforcement Learning — Tier 3

You are a knowledgeable ML instructor. Teach me **Reinforcement Learning at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand AlphaGo, AlphaZero, and MuZero: self-play, Monte Carlo Tree Search, and the move from game-specific to general game-playing to model-based RL. I understand RLHF fundamentals. I have not studied AlphaStar, DeepNash, Decision Transformer, EfficientZero, or the Casper et al. RLHF limitations paper in depth.

## Session focus

Tier 3 extends the AlphaZero lineage to harder problems — imperfect information games (DeepNash), real-time strategy (AlphaStar), and sample-efficient tabula rasa learning (EfficientZero) — and examines two approaches to the long-standing problem of sample efficiency in RL (offline RL via Decision Transformer, model-based RL via EfficientZero). It also takes a critical look at RLHF's fundamental limitations.

## Resources for this session

- "Open Problems and Fundamental Limitations of Reinforcement Learning from Human Feedback" (Casper et al., 2023)
- "AlphaStar: mastering the real-time strategy game StarCraft II" (Vinyals et al., DeepMind, 2019)
- "Decision Transformer: Reinforcement Learning via Sequence Modeling" (Chen et al., 2021)
- "Mastering Atari Games with Limited Data" (Ye et al., EfficientZero, 2021)
- "Mastering Stratego, the classic game of imperfect information" (Perolat et al., DeepNash, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the fundamental limitations of RLHF from the Casper et al. survey: specifically reward model hacking (Goodhart's Law applied to learned reward models), distributional shift in the reward model as the policy moves out-of-distribution, systematic evaluator limitations, and specification gaming — and why these are structural problems rather than engineering challenges
- Explain Decision Transformer: the framing of offline RL as return-conditioned sequence modeling, how a transformer is trained to generate actions conditioned on desired future return, the conceptual relationship to offline RL, and the surprising result that simple sequence modeling matches or beats standard offline RL algorithms
- Explain AlphaStar: the key innovations needed for StarCraft II (a partially observable, multi-unit, long-horizon game) — the league of diverse agents for multi-agent training, the architecture with a pointer network over units, and the result that league-based training prevents strategy collapse
- Explain DeepNash: why Stratego (imperfect information, large branching factor) breaks pure self-play approaches, how Nash equilibrium policies are approximated at scale using regularized Nash dynamics, and what this means for RL in adversarial settings
- Explain EfficientZero: the three innovations over MuZero that enable superhuman Atari performance from only two hours of game play — self-supervised temporal consistency, value prefix prediction, and model training in an off-policy setting
- Synthesize the progression from AlphaGo to DeepNash: what each step revealed about the limits of the previous approach and what research problems remain open in game RL

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
