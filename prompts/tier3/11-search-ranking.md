# Search and Ranking — Tier 3

You are a knowledgeable ML instructor. Teach me **Search and Ranking at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand RAG systems: dense retrieval with bi-encoder models, FAISS or similar ANN indices, and re-ranking. I am familiar with BM25 and the basic idea of DPR. I have not studied REALM (joint pretraining of retriever and reader), the original RAG paper's generative model integration, or task-aware retrieval instructions in depth.

## Session focus

Tier 3 examines the architectural foundations under modern RAG — specifically the key design decisions in REALM and the original RAG paper that made retrieval-augmented generation work, plus more recent advances in how ranking and embedding can be made task-aware, and honest comparison of vector database systems on the axes that matter in production.

## Resources for this session

- "Large Language Models are Effective Text Rankers with Pairwise Ranking Prompting" (Qin et al., 2023)
- "Not All Vector Databases Are Made Equal" (Dmitry Kan, 2021)
- "REALM: Retrieval-Augmented Language Model Pre-Training" (Guu et al., Google, 2020)
- "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks" (Lewis et al., Meta, 2020)
- "Task-aware Retrieval with Instructions" (Su et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the REALM approach: how the retriever and reader are trained jointly end-to-end, how the retriever's parameters get gradients through the reader's log-likelihood, and why joint training is harder but potentially better than the two-stage approach used in most RAG pipelines
- Explain the original RAG paper: the encoder-decoder architecture (using BART), the two variants (RAG-Sequence and RAG-Token), how retrieval is marginalized over during generation, and what the open-domain QA results showed
- Explain pairwise ranking prompting: why asking an LLM to directly compare two documents and pick the more relevant one is more reliable than asking it to score each document independently — the mechanism and practical tradeoffs
- Explain task-aware retrieval with instructions (INSTRUCTOR): how conditioning the embedding on a natural-language description of the task changes what the similarity metric captures — with examples of where task-agnostic embeddings fail
- Compare at least three vector database systems (e.g., FAISS, Pinecone, Weaviate, Milvus) on the axes of recall at scale, query latency, support for metadata filtering, and update performance — explaining which tradeoffs matter in which deployment contexts
- Synthesize: what does the choice of retrieval architecture assume about query/document distribution, and when do those assumptions break?

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
