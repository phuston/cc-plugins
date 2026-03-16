---
name: update-task
description: Update status or context on an existing task. Use when user says "update task", "status on X", "X is blocked", "switched to X", "working on X now", "X is taking longer than expected", "deprioritizing X", or any natural indication of a status change on existing work.
---

# Update Task

A lightweight mid-day task status update. Apply the user's natural language to the right task in today's daily note — no editor, no interview.

## 1. Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. If today's note doesn't exist, tell the user and offer two options:
   - Run day-start first to create the full note structure.
   - Create a minimal note now with just the current action.

## 2. Match Task

Fuzzy match the user's description against existing tasks in today's note.

- If **exactly one task** matches, proceed with the update.
- If **multiple tasks** match, present the candidates and ask the user to clarify before updating.
- If **no tasks** match, list today's open tasks and ask which one they mean.

## 3. Apply Update

Based on what the user said, do the appropriate thing:

- Append a `- Status: ...` note under the task with the update.
- Add a `- Blocker: ...` note if they mentioned a blocker.
- Reorder the task in the list if they're reprioritizing (e.g., "deprioritizing X" moves it toward the bottom; "switching to X now" moves it toward the top).
- Use judgment — the user's natural language should guide the update format. A terse status update gets a terse note; a context shift gets a brief explanation.

Only write to the file if there are actual changes.

## 4. Confirm

One sentence confirming the update. Move on.
