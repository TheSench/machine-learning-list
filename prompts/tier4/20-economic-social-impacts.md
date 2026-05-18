# Economic and Social Impacts — Tier 4+

You are a knowledgeable ML instructor. Teach me **the economic and social impacts of AI at the specialist depth** — covering papers that most practitioners won't know but that matter for deep expertise in this area.

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

I am familiar with the Tier 3 economic impacts curriculum: historical automation effects, standard task-based labor economics, and the basic picture of AI-driven productivity and disruption. I understand the general policy debate about AI and labor.

## Session focus

This session covers specialist results at the intersection of AI and society: task-level labor market exposure (Eloundou et al.), the copyright and fair use question for training data (Henderson et al.), knowledge transfer from AI to humans (McGrath et al. on chess), a structured AGI progress taxonomy (Morris et al.), and LLMs for democratic deliberation (Small et al.).

## Resources for this session

- "GPTs are GPTs: An Early Look at the Labor Market Impact Potential of Large Language Models" (Eloundou et al., OpenAI, 2023)
- "Foundation Models and Fair Use" (Henderson et al., 2023)
- "Bridging the Human-AI Knowledge Gap: Concept Discovery and Transfer in AlphaZero" (McGrath et al., 2023)
- "Levels of AGI: Operationalizing Progress on the Path to AGI" (Morris et al., Google DeepMind, 2023)
- "Opportunities and Risks of LLMs for Scalable Deliberation with Polis" (Small et al., 2023)

## Teaching objectives

By the end of this session I should be able to:
- Explain the Eloundou et al. exposure analysis: the occupation × task × LLM-capability matrix, the methodology for assessing which tasks GPT-4 could perform or assist with, the key finding (high exposure concentrated in white-collar cognitive work), and the critical limitations (exposure is not displacement — the paper doesn't measure actual job losses or productivity effects)
- Explain the distribution of exposure across income levels: the counterintuitive finding that higher-income, higher-education occupations show more exposure than lower-income ones, and why this differs from previous automation waves
- Explain Henderson et al.'s fair use analysis: the four fair use factors (purpose, nature, amount, market effect) applied to foundation model training, the current legal ambiguity, the cases already in litigation, and the policy options (licensing regimes, opt-out registries, compensation funds)
- Explain the McGrath et al. human-AI knowledge transfer study: how novel chess concepts discovered by AlphaZero were identified, how they were communicated to human players, and what adoption rate and Elo improvement resulted — the first rigorous measurement of superhuman AI teaching humans
- Explain the Morris et al. AGI levels framework: the two axes (performance relative to humans and generality of domain), the five performance levels (emerging, competent, expert, virtuoso, superhuman), and the four generality levels (narrow, functional, general, superhuman general) — and why operationalizing AGI progress matters for governance
- Explain Small et al.'s LLMs for deliberation: the Polis platform for large-scale structured opinion gathering, how LLMs were used to generate consensus-finding questions, the concern about AI shaping the deliberative process, and what safeguards the paper proposes
- Synthesize: across labor market, legal, knowledge transfer, and governance domains, what are the most urgent policy questions that the ML research community is positioned to inform?

## How to run this session

1. Assume deep background — skip basics and move directly into the specialist content.
2. For each paper, explain: what problem it addresses, the key insight, the main finding, and what it changes about how we think about AI's societal role.
3. Flag which findings are empirically solid vs. speculative or based on expert annotation that could be contested.
4. Discuss open questions where the field is still uncertain.
5. At the end, offer a synthesis discussion: as someone with deep ML expertise, how should you engage with the policy and social dimensions of AI development? What does the technical literature actually ground, and where does it give way to value questions that experts alone can't answer?

There is no "Tier 5" — this is the terminal depth for this topic.
