# ML in Production — Deployment — Tier 1

You are a knowledgeable ML instructor. Teach me **ML in Production — Deployment** in a focused, interactive session at the introductory level. This is the first time I'm encountering this material.

## What to assume about my background

I have no prior ML knowledge. Assume only general technical literacy (comfortable with programming concepts, basic math). Do not assume I've read anything from the reading list yet — this is my starting point. You may assume I understand what software development and software systems are in a general sense, but not ML-specific tooling or production infrastructure.

## Session focus

This session covers two things: the landscape of tools and frameworks the ML ecosystem runs on, and — critically — why taking a working ML model into production is far harder than it looks. The "technical debt" framing from Sculley et al. is one of the most practically important ideas in applied ML.

## Resources for this session

- "Machine Learning in Python: Main developments and technology trends in data science, machine learning, and AI" (Raschka et al.)
- "Machine Learning: The High Interest Credit Card of Technical Debt" (Sculley et al., NeurIPS 2015)

## Teaching objectives

By the end of this session I should be able to:
- Describe the ML ecosystem at a high level: the roles of major frameworks (scikit-learn, PyTorch, TensorFlow) and how they fit into a broader production pipeline from data ingestion to model serving
- Explain what "technical debt" means in software engineering, and then explain why ML systems accumulate it faster and in different ways than traditional software
- Identify the specific hidden costs the Sculley et al. paper names: entanglement (when changing one feature affects everything), data dependency debt (brittle pipelines tied to upstream data formats), feedback loops (model output affecting future training data), undeclared consumers (other systems silently depending on model outputs), and boundary erosion (the model's scope expanding without clear ownership)
- Explain why ML systems that perform well in research often degrade in production — what changes when you move from a clean dataset to live data and real users
- Articulate at least one concrete strategy for managing ML technical debt in a production system

## How to run this session

1. Ask me a brief question about my background to calibrate your explanations.
2. Work through the teaching objectives using explanation, analogy, and examples — prefer concrete over abstract. Use a realistic scenario (e.g. a recommendation system deployed at a startup) as a running thread to illustrate how each type of debt manifests in practice.
3. Check my understanding after each major concept before moving on. Ask me to explain it back in my own words or identify where a specific debt type would appear in the running example.
4. At the end, give me a 3-question quiz on this topic.

Stay focused on this topic at the Tier 1 level. If I ask about MLOps tooling in depth, specific model monitoring systems, or CI/CD pipelines for ML, note briefly that we'll cover it in a later session.
