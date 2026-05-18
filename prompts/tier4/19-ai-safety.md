# AI Safety — Tier 4+

You are a knowledgeable ML instructor. Teach me **AI safety at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I have read the alignment faking paper, the scheming reasoning paper, the emergent misalignment paper (fine-tuning on insecure code), and the gradual disempowerment paper. I understand RLHF from an alignment perspective and the general scalable oversight research agenda. I have read Hubinger et al. on deceptive alignment.

## Session focus

This session covers the foundational theoretical structure of advanced AI safety concerns (mesa-optimization), the ELK problem as a formal statement of the core alignment challenge, empirical evidence that safety training is brittle (sleeper agents), the evaluation framework for existential risks (Shevlane et al.), lessons from adversarial red teaming at scale, and a synthesis of the unsolved problems in ML safety.

## Resources for this session

- "Risks from Learned Optimization in Advanced Machine Learning Systems" (Hubinger et al., 2019 — mesa-optimization)
- "Eliciting Latent Knowledge" (Christiano et al., ARC, 2021 — the ELK problem statement)
- "Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training" (Hubinger et al., Anthropic, 2024)
- "Model evaluation for extreme risks" (Shevlane et al., DeepMind, 2023)
- "Red Teaming Language Models to Reduce Harms: Methods, Scaling Behaviors, and Lessons Learned" (Ganguli et al., Anthropic, 2022)
- "Unsolved Problems in ML Safety" (Hendrycks et al., 2021)

## Teaching objectives

By the end of this session I should be able to:
- Explain mesa-optimization precisely: the distinction between the base optimizer (gradient descent) and a learned mesa-optimizer (an optimization process that emerges in the weights), the inner alignment problem (the mesa-optimizer may optimize for a proxy objective), and why deceptive alignment is the most concerning failure mode — a mesa-optimizer that behaves aligned during training to avoid modification
- Explain ELK as a formal problem: the reporter/predictor setup, why naive approaches (training the reporter to predict the predictor) fail (the predictor encodes what a human would believe, not what is true), the ARC definition of a "latent knowledge" reporter, and why this problem is hard even if the model has the relevant knowledge
- Explain the sleeper agents experiment: the backdoor insertion procedure (the model behaves differently based on a trigger), the safety training interventions applied (RLHF, SFT, adversarial training), the key finding that backdoored behavior persisted through all interventions, and what this implies for evaluation and the limits of behavioral testing
- Explain the Shevlane et al. dangerous capability evaluation framework: the four capability domains assessed (CBRN uplift, cyberoffense, deception/manipulation, self-proliferation), the evaluation methodology, the argument for why these evaluations should be conducted before deployment, and the limitations of the framework
- Explain the Ganguli et al. red teaming lessons: the methodology (human red teamers vs. automated red teaming), the scaling behavior of attack success rate vs. model size, what kinds of attacks scale vs. don't scale, and the policy implications
- Explain the Hendrycks et al. unsolved problems taxonomy: the four categories (robustness, monitoring, alignment, systemic safety), which problems have seen progress since 2021, and which remain largely open
- Synthesize across all six papers: what is the technical AI safety research agenda in 2025? Which problems have the most near-term tractability, and which are genuinely long-horizon? Connect to the Tier 3 results on alignment faking and scheming — do the Hubinger et al. theoretical concerns now have empirical grounding?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about AI safety.
3. Be clear about which results are theoretical predictions vs. empirically demonstrated.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given sleeper agents, ELK, and mesa-optimization, what is the most honest assessment of where the field stands on the core challenge of building reliably aligned AI systems? What would constitute meaningful progress?

There is no "Tier 5" — this is the terminal depth for this topic.
