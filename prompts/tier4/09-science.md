# Science Applications — Tier 4+

You are a knowledgeable ML instructor. Teach me **AI applications to science at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with AlphaFold, scientific benchmarks (MMLU-Pro, SciQ), and the general picture of LLMs applied to biology, chemistry, and medicine from the Tier 3 curriculum.

## Session focus

This session examines four specialist areas of AI for science: the generalist-vs-specialist question in medicine (with expert-in-context prompting as a key technique), automated parsing of scientific documents (Nougat), drug synergy prediction via structured ICL (SynerGPT), and systematic review automation as a worked example of the AI-assisted research pipeline.

## Resources for this session

- "Can Generalist Foundation Models Outcompete Special-Purpose Tuning? Case Study in Medicine" (Nori et al., 2023)
- "Nougat: Neural Optical Understanding for Academic Documents" (Blecher et al., 2023)
- "SynerGPT: In-Context Learning for Personalized Drug Synergy Prediction and Drug Design" (2023)
- "A full systematic review was completed in 2 weeks using automation tools: a case study" (Khangura et al., 2012 — historical reference showing pre-LLM automation was already valuable)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Nori et al. experimental setup: the MedPaLM/GPT-4 comparison, what benchmarks were used (USMLE, MedQA), the expert-in-context prompting technique — and critically evaluate what the results do and don't show about real clinical utility
- Explain the expert-in-context technique in detail: how system prompt framing and persona priming affects performance on specialized benchmarks, and why this creates both opportunity and risk (benchmark gaming vs. genuine expertise activation)
- Explain Nougat's architecture: the encoder-decoder design for academic PDF parsing, how training data was constructed from paired PDF/LaTeX, what makes equation and table parsing hard, and the failure modes
- Explain SynerGPT: how drug combination data is formatted as in-context examples for a biological prediction task, what prior knowledge structure is being leveraged, and the broader pattern of structured ICL for scientific prediction
- Explain the pre-LLM systematic review automation baseline: what Khangura et al. automated in 2012 (title/abstract screening), the error rates accepted, and how LLMs change (or don't change) the bottlenecks in the review pipeline
- Describe the systematic review pipeline end-to-end: which stages (search, deduplication, screening, extraction, synthesis, quality assessment) are most amenable to current AI tools and which remain bottlenecks

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about AI for science.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: what is the realistic near-term contribution of LLMs to scientific discovery? Where is the pipeline complete enough to be trusted, and where are the remaining gaps in reliability and verification?

There is no "Tier 5" — this is the terminal depth for this topic.
