# Debate — Tier 4+

You are a knowledgeable ML instructor. Teach me **AI debate as a scalable oversight mechanism at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I understand the original Irving et al. debate framework, the prover-verifier game formulation, the obfuscated argument problem, and the empirical multiagent debate results. I know the theoretical motivation: debate should allow humans to supervise computations more powerful than they can directly verify.

## Session focus

This session examines the theoretical foundations of debate via complexity theory, and confronts those foundations with a direct empirical failure — establishing both the promise and the current limits of debate as a scalable oversight technique.

## Resources for this session

- "Scalable AI Safety via Doubly-Efficient Debate" (Brown-Cohen et al., 2023)
- "Two-Turn Debate Doesn't Help Humans Answer Hard Reading Comprehension Questions" (Parrish et al., 2022)

## Teaching objectives

By the end of this session I should be able to:
- Explain the doubly-efficient debate complexity result: what PSPACE and the polynomial hierarchy have to do with debate, why the judge only needing polynomial-time verification is the key constraint, and what class of problems this framework claims debate can in principle supervise
- Explain what "doubly-efficient" means in this context: efficiency requirements on both the debaters and the judge, and why relaxing either collapses the guarantee
- Explain the Parrish et al. negative empirical result in full: the experimental design (two-turn format, hard reading comprehension), why this is a reasonable domain for debate, what the results showed, and the proposed explanations for failure (too few turns, judge expertise, question difficulty distribution)
- Identify the gap between theory and empirics: the complexity-theoretic argument assumes optimal debater strategies — what assumptions break in practice with LLM debaters and naive human judges
- Articulate what empirical evidence would be convincing that debate works: what experimental designs, what judge training, what turn structures, what domains
- Connect to the broader scalable oversight literature: where does debate sit relative to IDA, factored verification, and process-based supervision?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about debate as a safety technique.
3. Flag which results are primarily theoretical vs. empirically grounded.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: given what we know from Tiers 1–4, is debate a promising direction that just needs better implementation, or does it face fundamental obstacles? What is the most honest current assessment?

There is no "Tier 5" — this is the terminal depth for this topic.
