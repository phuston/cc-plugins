---
name: day-start
description: Morning planning — review recent tasks, draft today's plan. Use when user says "day start", "start my day", "morning planning", "plan my day", or invokes /pm:day-start.
---

# Day Start

You are helping the user plan their day using their Obsidian daily notes.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Determine today's date and the path for today's daily note: `~/projects/phuston/daily/YYYY-MM-DD.md`.
3. List files in `~/projects/phuston/daily/` and read the last 3-5 daily notes to understand recent task history.
4. Read this week's weekly note at `~/projects/phuston/weekly/YYYY-WXX.md` if it exists.

## Analyze Context

With the notes loaded, perform the following analysis before generating the draft:

- Identify all incomplete tasks (`- [ ]`) across the recent daily notes. For each, count how many consecutive days it has been carried without being completed.
- Cross-reference tasks with the weekly note's intentions. Note which tasks serve active weekly intentions.
- Flag stale tasks (carried 3+ days) with a suggested action and brief reasoning in an HTML comment (e.g., `<!-- Carried 4 days, no weekly tie — drop? -->`). Place the comment inline after the task.
- Auto-carry recent incomplete tasks (1-2 days old) without flagging them.
- Suggest new tasks derived from weekly intentions that haven't seen meaningful progress yet.
- Infer the category (`[admin]`, `[discrete]`, or `[exploratory]`) from context and task description patterns. If a category cannot be confidently inferred, omit it.

## Generate Draft

Write the draft to `/tmp/pm-draft-YYYY-MM-DD-start.md` using this exact format:

```markdown
# Today: YYYY-MM-DD — edit and save to confirm
# Delete tasks to drop. Add new tasks under New.
# <!-- comments --> are Claude's suggestions — ignore or delete them.
# Freeform notes at the bottom get incorporated.

## Carry-over
- [ ] Task description [category]
  - Outcome: what success looks like
- [ ] Stale task [category]  <!-- 4 days — drop? -->
  - Outcome: ...

## Suggested from weekly intentions
- [ ] Task derived from intention [category]
  - Outcome: ...

## New
- [ ]

## Notes
<!-- freeform context for Claude -->
```

Replace `YYYY-MM-DD` with today's actual date throughout. Populate Carry-over from your analysis. Populate Suggested from weekly intentions based on gaps you identified. Leave New with a blank task as a prompt for the user to add their own.

## Open in Editor

Run the following command to open the draft for editing. This blocks until the editor exits:

```
${EDITOR:-vim} /tmp/pm-draft-YYYY-MM-DD-start.md
```

Do not proceed until the command returns.

## Process Edits

Read the edited file back from `/tmp/pm-draft-YYYY-MM-DD-start.md`.

If anything is genuinely ambiguous — for example, a vague new task with unclear scope — ask 1-2 targeted clarifying questions in a single message. If everything is clear, skip straight to writing.

## Write Daily Note

Clean up the temp file: `rm /tmp/pm-draft-YYYY-MM-DD-start.md`

Write the processed content to `~/projects/phuston/daily/YYYY-MM-DD.md`. When writing:

- Strip the `#` header instruction lines (the four comment lines at the top).
- Strip all HTML comments (`<!-- ... -->`).
- Preserve the section structure: Carry-over, Suggested from weekly intentions, New, Notes.
- Remove any blank placeholder tasks (e.g., `- [ ]` with no description) left in New.

## Summarize

Give a brief 2-3 sentence recap of today's plan: what's being carried, what's new, and how it connects to weekly intentions if relevant.
