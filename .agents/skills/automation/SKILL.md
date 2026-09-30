---
name: automation
description: Scripts, cron, systemd timers, workflows, and scheduled jobs — replacing manual steps with something that runs unattended. Triggers on "automate", "script this", "every day", "cron", "schedule", "workflow", "run this on a trigger", "batch".
---

# Automation

## When to use

A human did something twice, or the same step appears in two places.

## Rules

- Automate only a step that already worked manually at least once. Automating an unproven process
  manufactures failures at 3am instead of at 2pm.
- Idempotent or nothing. A job that appends on every run is a job that will eventually corrupt something.
- Fail loudly: exit non-zero, log the reason, do not swallow errors with `|| true`.
- The standard library first. A cron job is `cron`; a five-minute build tool is a build tool dependency,
  not five minutes of bash.
- Long work: log to a file, print a completion line, expose the last run's status somewhere findable.
- No hidden network dependencies. A job that dies because a CDN moved is not automation, it is a trap.
- Dry-run flag when the action is destructive or outward-facing (email, post, delete, charge).
- Idempotency key, checkpoint, or lock — whatever the job needs to not double-apply after a retry.
- Delete the automation when the manual process dies. Dead cron entries are worse than none.

## Done when

- Ran twice, produced the same result.
- A failure produces a visible error, not silence.
