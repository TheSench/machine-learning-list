# SETUP.md — Local Setup

## Prerequisites

- Claude Code (CLI or IDE extension)
- Git

No runtime, package manager, or database required. This is a pure markdown repo.

## First-time setup

1. Clone the repo
2. Open the repo in Claude Code
3. Send `Start`

The agent reads `TUTORIAL.md`, asks a few background questions, creates `learner/profile.md` and `learner/relevance.md`, and begins session 1.

## Resuming after a break

Open the repo in Claude Code and send `Continue`. The agent reads `learner/profile.md` to determine the next session.

## Learner state files

| File | Purpose |
|------|---------|
| `learner/profile.md` | Background, tiers-completed table, session log |
| `learner/relevance.md` | Per-topic depth calibration (HIGH/MED/LOW) |
| `learner/sessions/` | Individual session logs (created after >15 sessions) |

These files are created automatically on first run. `.gitkeep` holds the empty `learner/` directory in version control before they exist.

## Common issues

**"profile.md not found"** — expected on first run; the agent creates it during initialization.

**Session not committed** — if Claude Code was closed mid-session, the git commit may not have run. Check `git status` and commit manually with the standard format if needed.
