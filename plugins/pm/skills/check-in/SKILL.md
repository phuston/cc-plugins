---
name: check-in
description: Quick periodic check-in — update task status and note blockers. Use when invoked via /pm:check-in, /loop with check-in, "check in", "how's my day going", or "where am I at".
---

# Check-in

A brief check-in to keep today's daily note current. This should take ~30 seconds of interaction.

## 1. Notification

Run:

```
osascript -e 'display notification "Time to check in" with title "PM" sound name "default"'
```

Skip this step silently if not on macOS.

## 2. Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. If today's note doesn't exist, tell the user and offer two options:
   - Run day-start first to create the full note structure.
   - Create a minimal note now with just the current action.

## 3. Summary

Present a single line summarizing today's task status. Count completed vs open tasks. For example:

> "4 tasks today — 1 done, 3 open. You've been on auth token refresh since this morning."

## 4. Single Prompt

Ask exactly one question:

> "Any updates?"

Accept a freeform natural language response. The user may mention completions, new work, blockers, or context shifts in any order and phrasing — for example: "finished auth, switched to caching, blocked on staging deploy".

## 5. Parse and Update

Use task matching to process the freeform response:

- **Fuzzy match** descriptions in the response against existing tasks in today's note.
- If **exactly one task** matches a mention, proceed with the update.
- If **multiple tasks** match a mention, present the candidates and ask the user to clarify before updating.
- If **no tasks match** a mention, list today's open tasks and ask which one they mean.

Apply updates as appropriate:
- Mark completed tasks `[x]`
- Add status notes to in-progress tasks
- Add new tasks with category and outcome
- Note blockers inline

Only update the daily note if there are actual changes.

## 6. Confirm

One sentence confirming what changed. Move on.
