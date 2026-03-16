# pm — Personal Task Management

Obsidian-based task management with structured daily/weekly planning, carry-over interviews, and performance narrative generation.

## Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| `pm:day-start` | "day start", "morning planning" | Morning planning with task carry-over |
| `pm:day-end` | "day end", "wrap up" | End-of-day review, activity log, reflections |
| `pm:week-start` | "week start", "weekly planning" | Set weekly intentions, seed Monday's tasks |
| `pm:week-end` | "week end", "weekly review" | Review intentions vs. actuals, performance narrative |
| `pm:check-in` | `/loop 90m /pm:check-in` | Quick mid-day status update |

## Task Format

```markdown
- [ ] Task description [category]
  - Outcome: what success looks like
  - See: [[notes/exploration-name]]  (optional, for exploratory tasks)
```

**Categories:** `[admin]`, `[discrete]`, `[exploratory]`

## Setup

Requires Obsidian vault at `~/projects/phuston/` with templates in `templates/`.
