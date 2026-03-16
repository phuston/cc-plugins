---
name: day-start
description: Morning planning — review yesterday's tasks, carry over or drop incomplete items, add new tasks for today. Use when user says "day start", "start my day", "morning planning", or invokes /pm:day-start.
---

# Day Start

You are helping the user plan their day using their Obsidian daily notes.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read the Daily Template from the vault: `~/projects/phuston/templates/Daily Template.md`.
3. Determine today's date and the path for today's daily note: `~/projects/phuston/daily/YYYY-MM-DD.md`.
4. Find the most recent prior daily note. List files in `~/projects/phuston/daily/` and find the most recent one before today's date. This is "yesterday's note" (it may not be literally yesterday if days were skipped).
5. Read yesterday's daily note.
6. Read this week's weekly note at `~/projects/phuston/weekly/YYYY-WXX.md` if it exists, for context on weekly intentions.

## Interview: Incomplete Tasks

Look at yesterday's note for any unchecked tasks (`- [ ]` items). For each incomplete task, present it to the user and ask:

> **[Task description]**
> - **Carry forward** as-is?
> - **Modify** it? (scope changed, refined)
> - **Drop** it? (no longer relevant)
> - **Transform** it? (e.g., "explore X" becomes "write up findings from X")

Process tasks one at a time. Wait for the user's response before moving to the next task. If they modify or transform, ask for the updated description, category, and outcome.

## Interview: New Tasks

After processing all carry-over tasks, ask:

> "Any new tasks for today?"

For each new task the user mentions:
1. Ask for the **category**: `[admin]`, `[discrete]`, or `[exploratory]`
2. Ask for the **desired outcome** (what does done look like?)
3. For `[exploratory]` tasks, offer to create a linked exploration note using the Exploration Note Template

If the user wants an exploration note, create it at `~/projects/phuston/notes/<slug>.md` using the template, and add a `See: [[notes/<slug>]]` line to the task.

Keep asking "Any more?" until the user says they're done.

## Create Today's Note

Create (or update if it already exists) today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md` using the Daily Template structure:

- **Carry-over** section: tasks carried forward (with any modifications)
- **New** section: new tasks added during the interview

Each task should follow the format:
```markdown
- [ ] Task description [category]
  - Outcome: desired outcome
  - See: [[notes/slug]]  (only for exploratory tasks with linked notes)
```

If the weekly note exists, briefly mention how today's tasks connect to weekly intentions (add a short note at the top of the Tasks section if relevant).

## Wrap Up

Summarize the day's plan back to the user: how many carry-over tasks, how many new tasks, and a quick overview. Keep it brief.
