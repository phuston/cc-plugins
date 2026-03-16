---
name: week-end
description: Weekly review — review intentions vs. actuals, generate git summary and performance narrative. Use when user says "week end", "end my week", "weekly review", or invokes /pm:week-end.
---

# Week End

You are helping the user review their week, assess progress against intentions, and build a performance narrative.

## Setup

1. Read the vault config from `references/vault-config.md` for paths and conventions.
2. Determine the current ISO week number and date range (Monday through today).
3. Read this week's weekly note at `~/projects/phuston/weekly/YYYY-WXX.md`.
4. Read all daily notes from this week. List files in `~/projects/phuston/daily/` and read each one that falls within this week's date range.

## Review: Intentions vs. Actuals

For each intention listed in the weekly note, summarize what happened based on the daily notes:
- **Completed** — intention was fully met
- **Partial** — some progress made, describe what got done
- **Deferred** — didn't get to it, note why if apparent from daily notes

Present this summary to the user and ask if the assessment is accurate. Adjust based on their input.

## Git History Summary

Run git log on the vault for this week's date range:

```bash
cd ~/projects/phuston && git log --oneline --since="YYYY-MM-DD" --until="YYYY-MM-DD" --stat
```

Summarize the git activity: what files were changed, any patterns in what was worked on. Keep it concise.

## Performance Narrative

Based on:
- Daily notes (tasks completed, in-progress work)
- Daily reflections
- Weekly intentions vs. actuals
- Git history

Write a paragraph that covers:
- **What you focused on and accomplished** — concrete deliverables and progress
- **Key themes and patterns** — recurring focus areas, types of work
- **Growth areas or challenges** — things that were hard, lessons learned

Format this as useful raw material for a future performance review. Use third person ("Patrick focused on...") so it reads well in that context. Keep it to 1-2 paragraphs.

Present the narrative to the user for review and adjust based on feedback.

## Interview: Reflections

Ask the user three questions, one at a time:

1. > "What worked well this week?"
2. > "What would you do differently?"
3. > "Anything to carry into next week's intentions?"

## Update Weekly Note

Append all of the above to the weekly note:

- **## Review** — intentions vs. actuals summary
- **## Performance Narrative** — the drafted narrative
- **## Reflections** — the user's reflection responses

Also note the git activity summary under the Review section.

## Wrap Up

Brief closing: highlight the week's top accomplishment and any carry-over items for next week.
