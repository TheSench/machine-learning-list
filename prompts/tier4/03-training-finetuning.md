# Training and Finetuning — Tier 4+

You are a knowledgeable ML instructor. Teach me **training and finetuning at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I understand LoRA/QLoRA at a functional level, RLHF/DPO mechanics, and have read the Tier 3 finding about LoRA's equivalence to full fine-tuning under certain conditions.

## Session focus

This session extends the training and finetuning curriculum into specialist territory: the alignment implications of LIMA, the mathematical foundations of LoRA, iterative self-training approaches, prompt compression, long-context attention patterns, reasoning token training, and the formal link between language modeling and compression.

## Resources for this session

- "LIMA: Less Is More for Alignment" (Zhou et al., 2023)
- "LoRA: Low-Rank Adaptation of Large Language Models" (Hu et al., 2021 — the original paper)
- "Reinforced Self-Training (ReST) for Language Modeling" (Gulcehre et al., 2023)
- "Beyond Human Data: Scaling Self-Training for Problem-Solving with Language Models" (Singh et al., 2023)
- "Learning to Compress Prompts with Gist Tokens" (Mu et al., 2023)
- "Lost in the Middle: How Language Models Use Long Contexts" (Liu et al., 2023)
- "Language Modeling Is Compression" (Delétang et al., 2023)
- "Quiet-STaR: Language Models Can Teach Themselves to Think Before Speaking" (Zelikman et al., 2024)
- "Few-Shot Parameter-Efficient Fine-Tuning is Better and Cheaper than In-Context Learning" (Liu et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain LIMA's central claim: 1000 carefully curated examples nearly match full RLHF performance — what this says about where alignment comes from (pretraining vs. fine-tuning), and the important caveats about what LIMA's results do and don't show
- Explain the original LoRA formulation: the W = W₀ + BA decomposition, why a rank-r update is expressive enough, and the motivation from intrinsic dimensionality — then connect this to the Tier 3 finding about equivalence and articulate the tension
- Explain ReST: the grow (generate) / improve (filter and train) loop, why iterating improves performance, and the failure mode of distribution collapse on harder problems
- Explain Singh et al.'s self-training for problem-solving: what it takes to make self-training work at scale when ground-truth verification is available, and how it compares to ReST
- Explain gist tokens: the training procedure for distilling long system prompts into a small number of learned token embeddings, the compression ratios achieved, and the quality degradation profile
- Explain the "Lost in the Middle" finding: the U-shaped attention pattern (primacy/recency bias) in long-context models, which tasks are most affected, and what this implies for RAG systems and long-context fine-tuning
- Explain the language modeling as compression equivalence: the formal claim (a language model is a lossless compressor), what arithmetic coding has to do with it, and what this framing reveals about what language models are doing
- Explain Quiet-STaR: the mechanism for inserting and training on implicit thinking tokens at every position, the REINFORCE-based learning signal, the efficiency problem and proposed solutions
- Explain the few-shot PEFT vs. ICL comparison: the experimental setup, when PEFT outperforms in-context learning on few-shot tasks, and what this implies about the compute/data tradeoff

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about training and finetuning.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: how do LIMA, ReST, and Quiet-STaR together reshape our understanding of the pretraining/fine-tuning division of labor? What does the compression framing add to or complicate in the Tier 1–3 picture?

There is no "Tier 5" — this is the terminal depth for this topic.
