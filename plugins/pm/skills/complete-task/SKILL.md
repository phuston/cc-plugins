---
name: complete-task
description: Mark a task as complete. Use when user says "I finished X", "done with X", "completed X", "mark X done", "X is done", "shipped X", "just shipped X", "landed X", or any natural indication of task completion.
---

# Complete Task

Mark a task complete in today's daily note. No interview, no editor — match, update, confirm.

## 1. Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. If today's note doesn't exist, tell the user and offer two options:
   - Run day-start first to create the full note structure.
   - Create a minimal note now with just this completed task marked `[x]`.

## 2. Match Task

Fuzzy match the user's description against the open tasks (`- [ ]`) in today's note.

- If **exactly one task** matches, proceed.
- If **multiple tasks** match, present the candidates and ask the user to clarify which one they mean.
- If **no tasks match**, list today's open tasks and ask the user which one they mean.

## 3. Mark Complete

Change `- [ ]` to `- [x]` for the matched task.

If the user provided additional context beyond the task name (e.g., "finished auth — ended up also refactoring the middleware"), append it as a indented status note directly below the task line:

```
- [x] Task description
  - Note: ended up also refactoring the middleware
```

## 4. Confirm

One sentence: "Marked '[task description]' done." If the user provided additional context, append a brief note of it to the same sentence.
