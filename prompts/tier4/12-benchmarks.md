# Benchmarks — Tier 4+

You are a knowledgeable ML instructor. Teach me **ML benchmarking and evaluation at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with MMLU, BIG-Bench, HellaSwag, TruthfulQA, HumanEval, and the general debate about benchmark saturation and gaming. I understand the emergent abilities controversy, which involved reanalysis of benchmark-based findings.

## Session focus

This session examines the benchmark ecosystem from a critical perspective: HELM as a framework for multi-metric holistic evaluation, MATH as a case study in reasoning benchmark design, FLEX as an attempt at unified few-shot evaluation, and the Bowman & Dahl manifesto on what a principled evaluation system would require.

## Resources for this session

- "Holistic Evaluation of Language Models" (Liang et al., HELM, 2022)
- "Measuring Mathematical Problem Solving With the MATH Dataset" (Hendrycks et al., 2021)
- "FLEX: Unifying Evaluation for Few-Shot NLP" (Bragg et al., 2021)
- "What Will it Take to Fix Benchmarking in Natural Language Understanding?" (Bowman & Dahl, 2021)

## Teaching objectives

By the end of this session I should be able to:
- Explain HELM's multi-dimensional evaluation framework: the scenarios × metrics design, which accuracy-orthogonal metrics are included (robustness, calibration, fairness, efficiency, toxicity), and what the empirical finding was about how model rankings change depending on which metric you prioritize
- Explain why single-metric leaderboards are misleading: the specific failure modes HELM documents, and how different metrics anti-correlate in practice
- Explain the MATH dataset's design: the five difficulty levels, the seven subject areas, the gap between MATH performance and MMLU math performance, and what MATH performance revealed about the limits of symbolic reasoning in LLMs at the time of publication — and how that picture has changed
- Explain FLEX: what "unified few-shot evaluation" means in practice (standardized sampling, consistent few-shot formatting, cross-task comparability), what FLEX standardizes that individual benchmarks don't, and the limitation that task diversity still doesn't cover all important capabilities
- Explain Bowman & Dahl's diagnosis: the four major problems they identify (annotation artifacts, distribution mismatch, lack of contrast sets, single-metric reporting), their proposed remedies, and why most of those remedies have been slow to adopt
- Synthesize: given HELM, FLEX, and Bowman & Dahl, describe what a benchmark-resistant evaluation system would look like — adversarial evaluation, held-out data, contrast sets, multi-metric reporting, and the practical obstacles to implementing each

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about evaluation.
3. Flag which papers are primarily of historical interest vs. actively influencing current evaluation practice.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: in 2025, what does responsible evaluation practice look like for someone releasing a new model or a new ML system? What from this literature should be adopted, and what has been superseded?

There is no "Tier 5" — this is the terminal depth for this topic.
