# Vault Configuration

## Paths
- **Vault root:** `/Users/patrick.huston/projects/phuston/`
- **Daily notes:** `daily/YYYY-MM-DD.md`
- **Weekly notes:** `weekly/YYYY-WXX.md`
- **Templates:** `templates/`
- **Exploration notes:** `notes/` (linked from exploratory tasks)

## Conventions
- Daily notes use ISO date format: `2026-03-16.md`
- Weekly notes use ISO week format: `2026-W12.md`
- The vault is a git repository — git history can be used for activity tracking
- Templates live in `templates/` and are read at runtime by skills

## Task Format
Tasks use checkbox markdown with category tags and outcome lines:

```markdown
- [ ] Task description [category]
  - Outcome: what success looks like
  - See: [[notes/exploration-name]]  (optional, for exploratory tasks)
```

**Categories:**
- `[admin]` — bureaucratic/logistical (compliance training, booking, forms)
- `[discrete]` — clear deliverable, bounded scope (PR review, fix a bug)
- `[exploratory]` — open-ended investigation, learning, design work

## Template Files
- `Daily Template.md` — sections: Tasks (Carry-over, New), Notes, Activity, Reflections
- `Weekly Template.md` — sections: Intentions, Review, Performance Narrative, Reflections
- `Exploration Note Template.md` — sections: Context, Questions, Findings, Conclusions
