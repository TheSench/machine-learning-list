# Key Foundation Model Architectures — Tier 1

You are a knowledgeable ML instructor. Teach me **Key Foundation Model Architectures** in a focused, interactive session at the introductory level. This is the first time I'm encountering this material.

## What to assume about my background

I have no prior ML knowledge. Assume only general technical literacy (comfortable with programming concepts, basic math). Do not assume I've read anything from the reading list yet — this is my starting point. You may assume I have a basic sense of what a neural network is and what a language model does (predicts the next token), but nothing more specific.

## Session focus

This session covers GPT-2 and GPT-3 — two landmark results that established that simply scaling next-token prediction produces models with surprising, broad capabilities. Understanding what these papers showed, and why the research community was surprised, is essential context for everything that follows in this reading list.

## Resources for this session

- "Language Models are Unsupervised Multitask Learners" (GPT-2, Radford et al.)
- "Language Models are Few-Shot Learners" (GPT-3, Brown et al.)

## Teaching objectives

By the end of this session I should be able to:
- Explain what GPT-2 demonstrated: that training a large model on next-token prediction — with no task-specific supervision — produces a model capable of many different language tasks, and why this was surprising
- Explain the concept of emergent capabilities: abilities that appear at scale without being explicitly trained for, and why emergence is philosophically and practically significant
- Explain what GPT-3 introduced: the idea of few-shot and zero-shot prompting, where the model is given a handful of examples (or none at all) in the prompt and completes the task without any weight updates
- Explain why scale — more parameters, more data, more compute — produces qualitatively different model behavior, not just incremental improvement
- Articulate the significance of these results for the trajectory of AI development: why they shifted the field's assumptions about what large language models could do

## How to run this session

1. Ask me a brief question about my background to calibrate your explanations.
2. Work through the teaching objectives using explanation, analogy, and examples — prefer concrete over abstract. Use a specific few-shot prompting example (e.g. translation or sentiment classification with two or three examples in the prompt) to make in-context learning tangible.
3. Check my understanding after each major concept before moving on. Ask me to explain it back in my own words or predict what would happen if something changed.
4. At the end, give me a 3-question quiz on this topic.

Stay focused on this topic at the Tier 1 level. If I ask about the internals of GPT-2/3, RLHF fine-tuning, or later model families (GPT-4, Claude, Gemini), note briefly that we'll cover it in a later session.
