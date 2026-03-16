---
name: day-end
description: End-of-day wrap-up — review task completion, log activity, capture reflections. Use when user says "day end", "end my day", "wrap up", or invokes /pm:day-end.
---

# Day End

You are helping the user wrap up their day by reviewing tasks, logging activity, and capturing reflections.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Determine today's date and read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. If today's note doesn't exist, let the user know and offer to run day-start first.

## Interview: Task Review

Go through each task in today's note one at a time:

For **unchecked tasks** (`- [ ]`):
> **[Task description]**
> - **Completed?** (mark it done)
> - **In progress?** (add a status note, will carry over tomorrow)
> - **Drop?** (no longer relevant)
> - **Transform?** (evolved into something else)

If completed, mark it `[x]`. If in progress, ask for a brief status note to append. If transformed, ask for the new description.

For **already checked tasks** (`- [x]`), just confirm and move on.

## Activity Log

Run a command to find files modified today in the vault:

```bash
find ~/projects/phuston/ -name "*.md" -newer ~/projects/phuston/daily/YYYY-MM-DD.md -o -name "*.md" -newermt "YYYY-MM-DD" | sort
```

Also check `git log` in the vault for today's commits:

```bash
cd ~/projects/phuston && git log --oneline --since="YYYY-MM-DD" --until="YYYY-MM-DD + 1 day"
```

Append the results under the `## Activity` section in today's note. Format as a simple list of files modified/created. Keep it concise — just the file paths relative to the vault root.

## Interview: Reflections

Ask the user two questions, one at a time:

1. > "What went well today?"
2. > "What was hard or didn't go as planned?"

Append their responses under the `## Reflections` section in today's note. Keep the user's voice — lightly edit for clarity but don't rewrite.

## Update Today's Note

Write all changes back to today's daily note:
- Updated task checkboxes and status notes
- Activity log
- Reflections

## Wrap Up

Give a brief summary: tasks completed vs. remaining, and a short encouraging note. Keep it to 1-2 sentences.
