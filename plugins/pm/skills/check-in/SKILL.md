---
name: check-in
description: Quick periodic check-in — update task status and note any blockers. Use when invoked via /pm:check-in or /loop with check-in.
---

# Check-in

A brief mid-day check-in to keep today's daily note current. This should take ~30 seconds of interaction.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. If today's note doesn't exist, let the user know and suggest running day-start first.

## Quick Interview

Ask the user two quick questions:

1. > "What are you currently working on?"
2. > "Any blockers or priority shifts?"

## Update if Needed

Based on the user's responses:
- If any tasks are now **completed**, mark them `[x]`
- If priorities have **shifted**, reorder or add/remove tasks
- If there's a **new task**, add it with category and outcome
- If a task needs a **status note**, append it

Only update the daily note if there are actual changes. Don't update just for the sake of it.

## Wrap Up

Keep it brief — acknowledge what they're working on and move on. One sentence max.
