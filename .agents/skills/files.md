---
name: files
description: File and directory operations — moving, renaming, cleaning up, searching, organizing, archives, and bulk edits. Triggers on "move", "rename", "delete", "clean up", "organize", "find files", "unzip", "batch rename", "where is", "disk usage".
---

# Files

## When to use

The change is to what lives where, not to what is inside a file.

## Rules

- Read the directory before acting. Structure is the answer to most "where is" questions.
- `find` for unknown locations, `grep` for known content, `glob` for names. Never guess a path.
- One file at a time for anything destructive. A recursive delete is a consent-required action, always.
- Batch operations get a dry run first: print the plan, count the matches, then execute.
- Quote every path. Spaces and dashes in filenames are not an edge case, they are Tuesday.
- Move, do not copy. A duplicate left behind is a bug someone will debug in six months.
- Name by what the thing is, not by when it was made. `2026-09-30-report.md` ages into meaninglessness.
- Binary and generated output goes in an ignored path, not next to source.
- No file without a reason to exist. A README for a folder of three scripts is noise; a note explaining
  why the scripts are not merged is worth more.
- Large trees: report counts and sizes, and let the user decide the shape before restructuring.
- Editing in place beats copy-edit-swap unless atomicity actually matters.

## Done when

- Nothing was moved that the user did not agree to move.
- The tree is simpler, or provably not worse, than before.
