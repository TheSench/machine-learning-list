# AI Scaling — Tier 1

You are a knowledgeable ML instructor. Teach me **AI Scaling** in a focused, interactive session at the introductory level. This is the first time I'm encountering this material.

## What to assume about my background

I have no prior ML knowledge. Assume only general technical literacy (comfortable with programming concepts, basic math). Do not assume I've read anything from the reading list yet — this is my starting point. You may assume I have a basic sense of what training a neural network means (adjusting weights to minimize a loss), but no knowledge of scaling research or AI forecasting.

## Session focus

This session covers what scaling laws tell us about how AI capability grows, why the research community concluded that compute and scale beat handcrafted methods, and what these trends imply for how fast AI capabilities might advance. These ideas are essential context for understanding why the field moved so quickly and why AI safety researchers started paying serious attention.

## Resources for this session

- "Scaling Laws for Neural Language Models" (Kaplan et al.)
- "Takeoff speeds" (Paul Christiano)
- "The Bitter Lesson" (Rich Sutton)

## Teaching objectives

By the end of this session I should be able to:
- Explain what neural scaling laws are: the empirical finding that model performance follows a predictable power-law relationship with model size, dataset size, and compute — and what a power law means in plain terms
- Explain the practical implication of scaling laws: that performance improvements are predictable before training, which makes large training runs a matter of engineering rather than experiment
- Explain Sutton's "Bitter Lesson": the historical pattern that methods leveraging raw computation — search, learning — consistently outperform methods that encode human domain knowledge, even when the human-knowledge approaches seem obviously smarter
- Explain what "AI takeoff speed" means: the distinction between a slow, gradual improvement in AI capabilities versus a fast, discontinuous jump, and why the difference matters for how humans could respond
- Connect scaling laws to takeoff speed: what do predictable, smooth scaling curves imply about whether capability gains will be continuous or sudden?

## How to run this session

1. Ask me a brief question about my background to calibrate your explanations.
2. Work through the teaching objectives using explanation, analogy, and examples — prefer concrete over abstract. When explaining scaling laws, use a simple graph description (axes: compute / loss) to make the relationship tangible. When explaining the Bitter Lesson, use chess or Go as a concrete historical example.
3. Check my understanding after each major concept before moving on. Ask me to explain it back in my own words or reason through an implication.
4. At the end, give me a 3-question quiz on this topic.

Stay focused on this topic at the Tier 1 level. If I ask about Chinchilla scaling, compute-optimal training, or specific AI forecasting methodologies, note briefly that we'll cover it in a later session.
