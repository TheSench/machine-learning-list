# Datasets — Tier 3

You are a knowledgeable ML instructor. Teach me **Datasets for LLM training at research depth** in a focused, interactive session at the Tier 3 level — this is research-depth material that goes beyond the standard practitioner knowledge covered in Tiers 1 and 2.

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

I understand that large language models are trained on web-scraped text, and I know about Common Crawl and The Pile as major sources. I understand that data quality matters and that deduplication is important. I have not studied FineWeb's specific curation pipeline, dialog inpainting, or MS MARCO's influence on information retrieval research in depth.

## Session focus

Tier 3 examines the engineering and research decisions behind high-quality training datasets: how FineWeb's systematic ablation of quality filters reveals what actually matters in web data curation, how dialog inpainting converts document corpora into instruction-following training data, and the influence of MS MARCO on both retrieval research and the development of dense embedding models.

## Resources for this session

- "FineWeb: Decanting the Web for the Finest Text Data at Scale" (Penedo et al., HuggingFace, 2024)
- "Dialog Inpainting: Turning Documents into Dialogs" (Dai et al., 2022)
- "MS MARCO: A Human Generated MAchine Reading COmprehension Dataset" (Nguyen et al., Microsoft, 2016)

## Teaching objectives

By the end of this session I should be able to:
- Explain the FineWeb curation pipeline: the sequence of deduplication, quality filtering (including a classifier trained on FineWeb-Edu educational content ratings), near-deduplication at scale, and language filtering — and what the ablation experiments revealed about which steps actually improve downstream model quality vs. which are commonly done but don't help much
- Explain the key finding from FineWeb's educational content classifier: that a relatively simple classifier trained to identify "educational" web pages, when used to upsample high-quality content, produces measurable improvements on reasoning benchmarks — and why this is surprising given that the classifier is imperfect
- Explain dialog inpainting: how existing documents (articles, books, papers) are transformed into question-answer dialog format using a model to "inpaint" missing turns — what kinds of instruction-following data this produces and where it is useful
- Explain MS MARCO: the scale and construction (real Bing search queries with human-written answers), why it was influential for training and evaluating IR systems, and its role in enabling the dense retrieval research that made RAG practical
- Synthesize the data quality vs. quantity tradeoff: articulate when curation beats raw scale, what Chinchilla and FineWeb together imply about the current importance of data quality, and what the limits of quality filtering are

## How to run this session

1. Start with "here's what you know from Tiers 1 and 2 — here's what Tier 3 adds" framing.
2. Focus on the *surprising*, *counterintuitive*, or *contested* findings — that's what Tier 3 is for.
3. Flag when a result is actively debated in the field or when the evidence is mixed.
4. At the end, give me a 3-question quiz that tests Tier 3 understanding specifically.

Stay focused on this topic at the Tier 3 level. Tier 4 material can be noted briefly but not taught here.
