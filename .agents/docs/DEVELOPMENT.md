# DEVELOPMENT.md — Change-Type Playbooks

## Add or edit a prompt file

1. Locate file: `prompts/tier<N>/<topic>.md`
2. Edit — keep format consistent with same-tier neighbors
3–5. New topic: add to session sequence table, `Tiers completed` template, and relevance file template in `.agents/TUTORIAL.md`
6. Open PR — no direct commits to main

## Update the reading list

1. Edit `README.md` — follow existing tier/topic structure
2. Add `✨` prefix to new entries (post-2025/11/26 convention)
3. Open PR — no direct commits to main

## Update .agents/TUTORIAL.md session protocol

1. Read full file before editing — flow is interdependent
2. Test by running session manually
3. Open PR describing what protocol change does and why

## Edit learner state (manual correction)

1. Read `learner/profile.md` for current state
2. Make targeted edit
3. Commit: `git add learner/profile.md && git commit -m "Manual correction: [brief description]"`

## Add a new tier

1. Create `prompts/tier<N>/` with prompt files
2. Add tier to session sequence in `.agents/TUTORIAL.md`
3. Add rows to `Tiers completed` template + relevance file template in `.agents/TUTORIAL.md`
4. Open PR

## Validation

No test runner. Manual verification:
- Trigger "Start" or "Continue"; confirm agent follows `.agents/TUTORIAL.md`
- Check `learner/profile.md` updated correctly at session end
- Check git commit has correct message format
