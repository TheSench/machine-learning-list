# Search and Ranking — Tier 2

You are a knowledgeable ML instructor. Teach me **Search and Ranking** in a focused, interactive session at the Tier 2 level — building on Tier 1 foundations into substantive depth.

## What to assume about my background

I have completed all Tier 1 sessions from this reading list. That means I understand:
- Neural networks, gradient descent, and backpropagation basics
- Transformers at a high level (tokens, embeddings, attention, self-attention)
- GPT-2 and GPT-3 (emergent capabilities, few-shot prompting)
- Task decomposition and iterated amplification (basics)
- ML technical debt and production challenges
- Neural scaling laws and the Bitter Lesson
- The basic AI safety framing (three impacts, soft failure modes, alignment problem)

I understand that transformers produce embeddings (vector representations of tokens and sequences) as a byproduct of their architecture. Here I want to understand how those embeddings are specialized for retrieval tasks — and how dense retrieval systems work as an alternative to keyword search.

## Session focus

This session covers the shift from sparse keyword-based retrieval to dense embedding-based retrieval: how contrastive pretraining produces semantic embeddings, why dense retrieval captures meaning that keyword search misses, and how retrieval-augmented generation (RAG) combines retrieval with language model generation.

## Resources for this session

- "Learning Dense Representations of Phrases at Scale" (Lee et al., 2021 — dense passage retrieval approaches)
- "Text and Code Embeddings by Contrastive Pre-Training" (Neelakantan et al., OpenAI, 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the difference between sparse retrieval (BM25 / TF-IDF keyword matching) and dense retrieval (embedding similarity search): what each is computing, where each method succeeds, and why dense retrieval is better at semantic paraphrase and concept matching
- Explain how contrastive pretraining creates semantic embeddings: the setup of positive pairs (semantically similar text pairs) and negative pairs, the InfoNCE / contrastive loss that pulls positives together and pushes negatives apart in embedding space, and why in-batch negatives are used for efficiency
- Explain why the resulting embedding space captures semantic similarity: two passages that mean the same thing but share no words will have nearby embeddings, and explain why this matters for real-world search
- Describe the retrieval-augmented generation (RAG) architecture at a high level: encode a document corpus into a vector index offline, at query time encode the question and retrieve top-k nearest documents, then pass the retrieved documents and query to a generation model to produce an answer — and explain what problems RAG solves compared to relying on a model's parametric memory alone
- Explain what embedding models are in practice, how they differ from general-purpose LLMs, and how they are used in production semantic search systems (chunking, indexing with approximate nearest neighbor search, re-ranking)

## How to run this session

1. Briefly confirm my Tier 1 background, then move directly into Tier 2 material — don't re-teach basics.
2. Explain concepts using the Tier 1 knowledge as a springboard (e.g., "you know X from Tier 1 — here's what Tier 2 adds").
3. Use concrete examples: real model names, paper results, numbers where they matter.
4. At the end, give me a 3-question quiz that tests Tier 2 understanding (not just Tier 1 recall).

Stay focused on this topic at the Tier 2 level. Tier 3 material can be noted briefly but not taught here.
