# Search and Ranking — Tier 4+

You are a knowledgeable ML instructor. Teach me **neural search and ranking at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with the standard neural IR pipeline: bi-encoders for retrieval (DPR, ANCE), cross-encoders for reranking, BEIR as an evaluation benchmark, and the integration of neural retrieval with LLMs in RAG systems.

## Session focus

This session covers the specialist literature on retrieval and reranking: ColBERT's late interaction paradigm as an efficiency-quality compromise, listwise reranking with LLMs (RankZephyr), rigorous IR evaluation methodology, and the critique of using downstream task accuracy as a proxy for retrieval quality.

## Resources for this session

- "ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT" (Khattab & Zaharia, 2020)
- "RankZephyr: Effective and Robust Zero-Shot Listwise Reranking is a Breeze!" (Pradeep et al., 2023)
- "Some Common Mistakes In IR Evaluation, And How They Can Be Avoided" (Sakai, 2020)
- "Moving Beyond Downstream Task Accuracy for Information Retrieval Benchmarking" (Thakur et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain ColBERT's late interaction mechanism: precomputing document token-level embeddings offline, computing MaxSim similarity at query time — why this achieves better quality than single-vector bi-encoders and lower latency than full cross-encoders, and what the storage cost is
- Explain the theoretical tradeoff between interaction granularity and computational cost: the design space from bag-of-words through bi-encoder through late interaction through cross-encoder, and where ColBERT sits in this space
- Explain listwise reranking: scoring all candidates jointly in a single context, how this differs from pointwise (independent scoring) and pairwise (comparative scoring), and why joint scoring produces more consistent rankings
- Explain how RankZephyr implements zero-shot listwise reranking: the permutation generation approach, the sliding window for long candidate lists, and the robustness to instruction variation
- Explain the Sakai evaluation mistakes: the multiple comparisons problem in IR evaluation, why pooling bias is a fundamental validity threat, what significance testing requires in an IR setting, and how these mistakes lead to false conclusions about system comparisons
- Explain the Thakur et al. benchmark critique: why performance on downstream tasks (QA accuracy, classification) can diverge from retrieval quality, what the gap reveals about how retrieval errors propagate, and what a retrieval-specific evaluation should measure
- Synthesize: for someone building a production retrieval system, what does the ColBERT + RankZephyr + evaluation methodology literature imply about architecture choices and evaluation practices?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about search and ranking.
3. Flag which papers are primarily of historical interest vs. actively influencing current work.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: what is the current best practice for a high-quality retrieval pipeline in 2025, and where are the remaining unsolved problems?

There is no "Tier 5" — this is the terminal depth for this topic.
