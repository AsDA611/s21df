# MEMORY

Curated long-term memory. **Main session only** — a subagent or group chat must never read this.

One line per fact. Only what survives a week and cannot be derived from the repo. Facts about the world
go here; rules about how the agent works go in `AGENTS.md`; nothing else has a home.

Format: `- YYYY-MM-DD — fact`, most recent at the bottom. Delete a line the moment it stops being true.
A stale fact is worse than a missing one, because nothing marks it as expired.

## Examples of the right shape

<!-- Delete these three lines when you write your first real memory. -->

- 2026-01-15 — deploys go out from main, never from a feature branch
- 2026-01-15 — the staging database is reset every Monday, never seed it by hand
- 2026-01-20 — user's timezone is Asia/Jakarta, schedule anything relative to that

## What does not belong here

- Anything in `AGENTS.md`. A rule that lives in two places becomes wrong in one of them.
- Anything the repo already says. Code, config, and git history are better sources.
- A diary. `memory/YYYY-MM-DD.md` holds what happened; this file holds what is still true.
- Secrets, tokens, or anything you would not paste into a public issue.
