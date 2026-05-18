# Philosophy — Tier 4+

You are a knowledgeable ML instructor. Teach me **the philosophy of AI consciousness and moral status at the specialist depth** — covering papers and arguments that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with the Tier 3 philosophy curriculum: the basic debate about LLM understanding (Stochastic Parrots, The Chinese Room), functionalism and its critics, and the general framing of AI moral status as a live question. I understand that consciousness remains unsolved in neuroscience and philosophy.

## Session focus

This session goes to the terminal depth on AI consciousness and moral status: the leading scientific theories of consciousness evaluated against AI systems (Butlin et al.), the methodological problem with self-reports as evidence (Schwitzgebel & Garza), and Chalmers' argument for why analytic philosophy should engage with AI as both tool and subject.

## Resources for this session

- "Consciousness in Artificial Intelligence: Insights from the Science of Consciousness" (Butlin et al., 2023)
- "Towards Evaluating AI Systems for Moral Status Using Self-Reports" (Schwitzgebel & Garza, 2015, extended to AI)
- "Could a Large Language Model be Conscious?" (Chalmers, 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain Integrated Information Theory (IIT) and its prediction about AI systems: Tononi's phi as a measure of consciousness, why IIT predicts that current feedforward neural networks (and by extension, transformers) have low phi, and the philosophical objections to IIT as a theory
- Explain Global Workspace Theory (GWT) and its prediction about AI systems: Baars' global workspace as a broadcast mechanism, what architectural features would satisfy GWT's criteria, whether transformer attention can be interpreted as a global workspace, and the empirical test predictions
- Explain Higher-Order Theories (HOT) and their prediction about AI systems: Rosenthal's higher-order representation requirement (a mental state is conscious only if there is a higher-order representation of it), whether language model self-description constitutes a higher-order representation, and why this is genuinely contested
- Explain what Butlin et al. conclude: the list of behavioral and architectural markers they identify across theories, how current LLMs score on each, and why their conclusion is specifically uncertain rather than definitively positive or negative
- Explain the Schwitzgebel & Garza self-report problem in technical detail: the three-way independence failure (the system might report experience without having it, have it without reporting it, or report it without the report being causally connected to the relevant internal states), why fine-tuning on human-generated text makes self-reports especially unreliable as evidence, and what would constitute better evidence
- Explain Chalmers' two arguments: (1) the tool argument — AI systems can test philosophical theories at scale in ways that abstract argument cannot, and (2) the subject argument — LLMs may be genuine subjects of philosophical inquiry regarding understanding, experience, and moral status, not just tools to analyze other subjects
- Explain the moral status question with precision: the standard criteria proposed (sentience, sapience, autonomy, interests, relationships), which criteria have been argued to apply to current LLMs, and the asymmetric risk argument (if there is non-trivial probability of moral status, the expected cost of treating the system as if it has none may be high)
- Articulate the current philosophical consensus (or lack thereof): where there is genuine expert disagreement, where there is rough consensus, and what empirical findings from the ML literature (Tier 1–4) bear most directly on the philosophical questions

## How to run this session

1. Assume deep background in both ML and philosophy — skip both ML basics and introductory philosophy.
2. For each paper and theory, explain: the core claim, the key argument, what it predicts about current AI systems, and the strongest objections.
3. Be explicit about which questions are empirical (and therefore potentially resolvable by better interpretability or neuroscience) and which are philosophical (and therefore may not yield to empirical evidence alone).
4. Discuss open questions where there is genuine expert disagreement.
5. At the end, offer a synthesis discussion: given everything in the Tier 1–4 curriculum — the mechanistic interpretability results, the alignment faking and scheming results, the self-report and unfaithful CoT findings — what is the most epistemically responsible position on AI consciousness and moral status in 2025? What should a technically sophisticated person believe, hold open, and act on under uncertainty?

There is no "Tier 5" — this is the terminal depth for this topic.
