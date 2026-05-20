# ARCHITECTURE.md — System Design

## Overview

Static markdown curriculum + agent-driven tutorial protocol. No running service, no API, no external deps. All state in files.

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

**State in files, not memory** — progress written to `learner/profile.md` and committed after each session; survives across Claude Code windows.

**Curriculum read-only to agents** — `prompts/`, `.agents/TUTORIAL.md`, `README.md` define learning contract. Only humans may change.

**Relevance-driven depth** — `learner/relevance.md` lets agent adapt depth without changing curriculum.

**Session splitting** — once session log exceeds ~15 entries, move individual sessions to `learner/sessions/` to keep `profile.md` readable.
