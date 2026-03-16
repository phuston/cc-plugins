# pm — Personal Task Management

Obsidian-based task management with journal-style daily planning, smart draft generation, and lightweight mid-day task interactions. Claude does the reasoning — analyzing task history, weekly intentions, and git activity to present smart drafts rather than interviewing you.

## Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| `pm:day-start` | "day start", "start my day", "plan my day" | Draft today's plan in $EDITOR with smart carry-over and suggestions |
| `pm:day-end` | "day end", "wrap up", "how'd today go" | Draft end-of-day review with auto-detected completions from git |
| `pm:check-in` | "check in", "where am I at", `/loop 90m /pm:check-in` | macOS notification + one-line summary + freeform update |
| `pm:complete-task` | "I finished X", "shipped X", "X is done" | Mark a task done with optional context |
| `pm:add-task` | "I need to do X", "add a task", "remind me to X" | Add a task with inferred category and outcome |
| `pm:update-task` | "X is blocked", "switched to X", "working on X now" | Update task status, blockers, or priority |
| `pm:week-start` | "week start", "weekly planning" | Set weekly intentions, seed Monday's tasks |
| `pm:week-end` | "week end", "weekly review" | Review intentions vs. actuals, performance narrative |

## Task Format

```markdown
- [ ] Task description [category]
  - Outcome: what success looks like
  - See: [[notes/exploration-name]]  (optional, for exploratory tasks)
```

**Categories:** `[admin]`, `[discrete]`, `[exploratory]`

## Setup

Requires Obsidian vault at `~/projects/phuston/` with templates in `templates/`.
