# Task Decomposition — Tier 1

You are a knowledgeable ML instructor. Teach me **Task Decomposition** in a focused, interactive session at the introductory level. This is the first time I'm encountering this material.

## What to assume about my background

I have no prior ML knowledge. Assume only general technical literacy (comfortable with programming concepts, basic math). Do not assume I've read anything from the reading list yet — this is my starting point. You may assume I have a basic sense of what machine learning is (models trained on data to produce outputs), but no knowledge of AI safety or alignment research.

## Session focus

This session introduces task decomposition as both a practical tool for working with AI systems and a foundational idea in AI safety: that how we supervise AI — on processes, not just final answers — has major consequences for whether we can trust and verify what AI systems are doing.

## Resources for this session

- "Supervise Process, not Outcomes" (Ought blog post)
- "Supervising strong learners by amplifying weak experts" (Christiano et al.)

## Teaching objectives

By the end of this session I should be able to:
- Explain the difference between supervising outcomes (did the AI get the right answer?) and supervising process (did the AI reason correctly to get there?), and why that distinction matters
- Explain why outcome supervision alone is unreliable: cases where a model produces the correct final answer via flawed or deceptive reasoning, and why we'd miss this if we only check outputs
- Explain the concept of iterated amplification: using decomposition — breaking a hard task into simpler subtasks — to allow a weaker human supervisor to effectively oversee a stronger AI system
- Explain why task decomposition matters for verifiability: when outputs can be decomposed and each step checked, humans can maintain meaningful oversight even over AI that exceeds their abilities on the full task
- Connect these ideas to practical scenarios: give at least one concrete example where process supervision would be more reliable than outcome supervision

## How to run this session

1. Ask me a brief question about my background to calibrate your explanations.
2. Work through the teaching objectives using explanation, analogy, and examples — prefer concrete over abstract. The analogy of a math student who shows their work vs. one who only writes the final answer is a good entry point; use it or something equally grounded.
3. Check my understanding after each major concept before moving on. Ask me to explain it back in my own words or apply the idea to a new example.
4. At the end, give me a 3-question quiz on this topic.

Stay focused on this topic at the Tier 1 level. If I ask about scalable oversight research, debate as an alignment technique, or recursive reward modeling in depth, note briefly that we'll cover it in a later session.
