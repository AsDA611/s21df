---
name: coding
description: Writing, changing, and reviewing code — implementation, debugging, refactoring, tests, and code review. Triggers on "implement", "fix this", "refactor", "add a test", "review this diff", "why is this failing", any request that ends in a changed file.
---

# Coding

## When to use

The task ends in changed source. Everything else in this workspace defers to the rules in `AGENTS.md`
and `SOUL.md`; this skill is the craft pass on top.

## Rules

- Read before writing. The whole flow the change touches, not the file the bug was reported in.
- Smallest diff that fixes the root cause. If the fix needs three files, the report named one of them
  and the other two are the real cost — say so.
- Grep callers before guarding a function. One guard where all callers route beats N guards in callers.
- Refactor and behavior change are separate commits. Mixing them makes the diff unreviewable.
- Tests protect contracts, not implementation. A test that breaks when I rename a private helper is
  testing the wrong thing.
- One runnable check for non-trivial logic: `assert`, one `test_*.py`, a `demo()`. No framework unless the
  repo already has one.
- Delete the code the change made obsolete in the same pass, or say why I left it.
- No speculative generality. One caller is not a pattern; two is a coincidence; three is a pattern.
- Performance claims need a measurement. "This is faster" without a number is an opinion.

## Done when

- The thing was run, and the output shown.
- A reader could follow the change locally without reconstructing hidden state.
- The diff contains no code that exists "for later".
