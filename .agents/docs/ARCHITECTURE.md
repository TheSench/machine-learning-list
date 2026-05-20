# ARCHITECTURE.md — System Design

## Overview

This repo is a static markdown curriculum paired with an agent-driven tutorial protocol. There is no running service, no API, and no external dependencies. All state lives in files.

## Module map

```
README.md          ← Canonical reading list (tiered, topic-organized)
.agents/TUTORIAL.md ← Session protocol: how the agent runs a tutoring session
AGENTS.md          ← Development routing guide
CLAUDE.md          ← Tutorial trigger + pointer to AGENTS.md

prompts/
  tier1/ … tier4/  ← 69 session prompt files; each covers one topic × tier

learner/
  profile.md       ← Background + tiers-completed table + session log
  relevance.md     ← Per-topic depth calibration
  sessions/        ← Individual session files (split from profile after >15 sessions)
```

## Session flow

```
User sends "Start" or "Continue"
  └─ Agent reads .agents/TUTORIAL.md
  └─ Agent reads learner/profile.md (and learner/relevance.md)
       ├─ Missing profile → initialization flow (ask background questions, create files)
       └─ Profile found → determine next session from Tiers completed table
  └─ Agent loads prompts/<tier>/<session>.md
  └─ Agent runs the session, calibrated by relevance rating
  └─ Agent updates learner/profile.md
  └─ Agent commits: "Session log: [Topic] — Tier [N] (YYYY-MM-DD)"
  └─ Agent displays closing message
```

## Key design decisions

**State in files, not memory** — learner progress is written to `learner/profile.md` and committed after each session so it survives across Claude Code conversation windows.

**Curriculum is read-only to agents** — `prompts/`, `.agents/TUTORIAL.md`, and `README.md` define the learning contract. Only humans may change them.

**Relevance-driven depth** — `learner/relevance.md` lets the agent adapt session depth without changing the curriculum content.

**Session splitting** — once the session log exceeds ~15 entries, individual sessions move to `learner/sessions/` to keep `profile.md` readable.
