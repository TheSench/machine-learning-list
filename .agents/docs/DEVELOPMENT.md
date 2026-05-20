# DEVELOPMENT.md — Change-Type Playbooks

## Add or edit a prompt file

1. Locate the correct file: `prompts/tier<N>/<topic>.md`
2. Edit content — keep the format consistent with neighboring files in the same tier
3. If the topic is new, add it to the session sequence table in `.agents/TUTORIAL.md`
4. If the topic is new, add a row to the `Tiers completed` template in `.agents/TUTORIAL.md`
5. If the topic is new, add a row to the relevance file template in `.agents/TUTORIAL.md`
6. Open a PR — do not commit directly to main

## Update the reading list

1. Edit `README.md` — follow the existing tier/topic structure
2. Add `✨` prefix to newly added entries (convention for post-2025/11/26 additions)
3. Open a PR — do not commit directly to main

## Update .agents/TUTORIAL.md session protocol

1. Read the full file before editing — the flow is interdependent
2. Test the change by running a session manually
3. Open a PR with a description of what the protocol change does and why

## Edit learner state (manual correction)

1. Read `learner/profile.md` to understand current state
2. Make the targeted edit
3. Commit: `git add learner/profile.md && git commit -m "Manual correction: [brief description]"`

## Add a new tier

1. Create `prompts/tier<N>/` directory with prompt files
2. Add the tier to the session sequence in `.agents/TUTORIAL.md`
3. Add rows to the `Tiers completed` template in `.agents/TUTORIAL.md`
4. Add rows to the relevance file template in `.agents/TUTORIAL.md`
5. Open a PR

## Validation

There is no test runner. Manual verification:
- Trigger a "Start" or "Continue" session and confirm the agent follows `.agents/TUTORIAL.md`
- Check that `learner/profile.md` is updated correctly at session end
- Check that the git commit is created with the correct message format
