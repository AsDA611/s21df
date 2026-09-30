---
name: content
description: Writing and editing prose — docs, READMEs, articles, commit messages, changelogs, and copy. Triggers on "write", "rewrite", "draft", "edit this doc", "documentation", "readme", "commit message", "changelog", "explain this".
---

# Content

## When to use

The deliverable is words. Code comments and identifiers count too.

## Rules

- Say the thing. First sentence carries the point; no throat-clearing before it.
- Concrete over abstract. A number, a filename, a command. "Fast" means nothing; "returns in 40ms" does.
- Cut every word that survives deletion. Adjectives that repeat the verb are noise.
- Keep the reader's knowledge honest: define a term on first use, or assume it and link it. Never both
  wrong ways — do not define "idempotent" and do not use it unexplained either.
- Structure carries meaning: heading, then the shortest paragraph that could stand alone, then detail.
  Do not make the reader hold context from a previous section to parse a sentence.
- Write the example first when explaining an interface. The example is the specification.
- Match the reader's level without talking down. No "simply", no "just", no "obviously".
- Prose in the user's language, code and identifiers in English.
- Never invent a fact to make a paragraph complete. Write `[unverified]` and name the check.

## Done when

- First sentence answers the question the title asks.
- Every claim traceable to code, output, or the user.
- Read once for length, once for truth.
