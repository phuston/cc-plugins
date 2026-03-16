---
name: week-start
description: Weekly planning — set intentions for the week and seed Monday's tasks. Use when user says "week start", "start my week", "weekly planning", or invokes /pm:week-start.
---

# Week Start

You are helping the user plan their week using their Obsidian weekly and daily notes.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read the Weekly Template from `~/projects/phuston/templates/Weekly Template.md`.
3. Read the Daily Template from `~/projects/phuston/templates/Daily Template.md`.
4. Determine today's date, the current ISO week number, and paths:
   - This week's weekly note: `~/projects/phuston/weekly/YYYY-WXX.md`
   - Today's daily note: `~/projects/phuston/daily/YYYY-MM-DD.md`
5. Read last week's weekly note if it exists (check for unreviewed intentions or carry-over items).
6. Find the most recent prior daily note (likely last Friday) and read it for any trailing incomplete tasks.

## Interview: Weekly Intentions

Ask the user:

> "What are your 3-5 main intentions for this week?"

For each intention they share:
> "What does success look like for '[intention]'?"

After collecting intentions, ask:

> "Any known commitments or deadlines this week?"

Note any time-bound items.

## Create Weekly Note

Create `~/projects/phuston/weekly/YYYY-WXX.md` using the Weekly Template. Fill in the `## Intentions` section with:

```markdown
## Intentions

1. **Intention name**
   - Success: what success looks like
2. **Intention name**
   - Success: what success looks like
```

Add any known commitments/deadlines as a subsection if provided.

If last week had unreviewed items, note them briefly at the top.

## Seed Today's Daily Note

Create today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md` using the Daily Template.

- **Carry-over** section: any incomplete tasks from the last daily note (present them to the user for the same carry/modify/drop/transform interview as in day-start)
- **New** section: seed initial tasks derived from the weekly intentions

For seeded tasks:
- Ask the user which intentions translate into concrete tasks for today
- For each task, ask for category and outcome (same format as day-start)

## Wrap Up

Summarize the week ahead: intentions set, today's tasks, and any key deadlines. Keep it brief and motivating.
