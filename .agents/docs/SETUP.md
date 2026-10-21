# SETUP.md — Local Setup

## Prerequisites

- Claude Code (CLI or IDE extension)
- Git

No runtime, package manager, or database required. Pure markdown repo.

## First-time setup

1. Clone repo
2. Open in Claude Code
3. Send `Start`

Agent reads `TUTORIAL.md`, asks background questions, creates `learner/profile.md` + `learner/relevance.md`, begins session 1.

## Resuming after a break

Open in Claude Code, send `Continue`. Agent reads `learner/profile.md` to determine next session.

## Learner state files

| File | Purpose |
|------|---------|
| `learner/profile.md` | Background, tiers-completed table, session log |
| `learner/relevance.md` | Per-topic depth calibration (HIGH/MED/LOW) |
| `learner/sessions/` | Individual session logs (created after >15 sessions) |

Files created automatically on first run. `.gitkeep` holds empty `learner/` in version control before they exist.

## Common issues

**"profile.md not found"** — expected on first run; agent creates during initialization.

**Session not committed** — Claude Code closed mid-session; git commit may not have run. Check `git status` and commit manually with standard format.
