---
name: add-task
description: Add a new task to today's plan. Use when user says "add a task", "I need to do X", "new task", "remind me to X", "I should do X", "also need to X", "oh and X", or any natural indication of new work to track.
---

# Add Task

A lightweight mid-session entrypoint to append a single task to today's daily note. Fast — no editor, no interview. Infer and proceed.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. Read this week's weekly note at `~/projects/phuston/weekly/YYYY-WXX.md` if it exists, for context on active intentions.
4. If today's note doesn't exist, tell the user and offer two options:
   - Run day-start first to create the full note structure.
   - Create a minimal note now with just this new task.

## Infer Task Details

From the user's description, the weekly intentions, and patterns in existing tasks, infer:

- **Category**: one of `[admin]`, `[discrete]`, or `[exploratory]`
- **Outcome**: a brief, concrete description of what done looks like

Use these signals to infer without asking:
- Tasks involving reviews, scheduling, emails, logistics → `[admin]`
- Tasks with a clear deliverable or finish line → `[discrete]`
- Tasks involving investigation, learning, or open-ended exploration → `[exploratory]`
- Outcome can usually be inferred from the task description itself (e.g., "review Jake's PR" → "PR reviewed and feedback left")

If category **and** outcome genuinely cannot be inferred from the description and context, ask exactly one clarifying question. Otherwise proceed directly.

## Add to Note

Append the task under the `## New` section of today's daily note. If no `## New` section exists, create one at the end of the file.

Use this format:

```markdown
- [ ] Task description [category]
  - Outcome: what success looks like
```

## Confirm

One sentence: "Added '[task description]' [category] to today."
