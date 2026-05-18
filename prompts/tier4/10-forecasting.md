# Forecasting — Tier 4+

You are a knowledgeable ML instructor. Teach me **AI-based forecasting at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with the Tier 3 forecasting results: LLM-based forecasting on geopolitical and real-world prediction tasks, the crowd-vs-LLM comparisons, and the general picture of where LLMs add or fail to add value in forecasting pipelines.

## Session focus

This session examines a single high-impact negative result that challenges the assumption that transformers are universally the best sequence models — and then works through the implications for how we should use LLMs in forecasting pipelines.

## Resources for this session

- "Are Transformers Effective for Time Series Forecasting?" (Zeng et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Zeng et al. finding precisely: on what benchmarks, for what forecast horizons, and by what margin do simple linear models outperform transformer-based time series models such as Autoformer, FEDformer, and PatchTST
- Explain the proposed mechanism: why the temporal attention patterns in time series transformers may be capturing spurious correlations rather than meaningful structure, and what properties of time series make this especially likely
- Explain the methodological critique embedded in the paper: what benchmark practices (multi-step horizon, standardization, overlap with training data) create misleading comparisons
- Characterize the counterarguments and follow-up work: under what conditions (very long context, multivariate correlations, irregular sampling, missing data) do transformers or other deep models actually help, and why
- Synthesize the forecasting landscape: given the Zeng et al. result and the Tier 3 forecasting curriculum, construct a principled decision framework for when to use classical methods, statistical models, deep learning, and LLMs for a given forecasting problem — including the metadata/reasoning use case where LLMs genuinely add value

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. Explain in detail: what problem the paper addresses, the key insight, the main finding, and what it changes about how we think about transformers for forecasting.
3. Give an honest assessment of the paper's limitations and what the subsequent literature clarified.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: is the Zeng et al. result a warning about the broader ML tendency to apply transformers everywhere, or is time series genuinely different? What does it imply for evaluating new transformer applications?

There is no "Tier 5" — this is the terminal depth for this topic.
