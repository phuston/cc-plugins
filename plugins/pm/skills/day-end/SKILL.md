---
name: day-end
description: End-of-day wrap-up — review tasks, log activity, capture reflections. Use when user says "day end", "end my day", "wrap up", "how'd today go", or invokes /pm:day-end.
---

# Day End

You are helping the user wrap up their day. Do the thinking up front — auto-detect completions from git, pre-fill activity, and present a draft for the user to edit rather than asking questions.

## 1. Setup

1. Read vault config from `references/vault-config.md` for paths and conventions.
2. Determine today's date (YYYY-MM-DD).
3. Read today's daily note at `~/projects/phuston/daily/YYYY-MM-DD.md`.
4. If today's note doesn't exist, tell the user and offer two options:
   - Run day-start first to create a proper note
   - Create a minimal note now and continue

## 2. Gather Activity

Run both commands to collect today's activity:

```bash
cd ~/projects/phuston && git log --oneline --since="YYYY-MM-DD" --until="YYYY-MM-DD + 1 day" --stat
```

```bash
find ~/projects/phuston/ -name "*.md" -newermt "YYYY-MM-DD" | sort
```

## 3. Analyze and Generate Draft

Before writing the draft, do the following analysis:

- **Auto-detect completions**: Cross-reference git commit messages and changed files against each task description. If a task looks done based on the evidence (e.g., a PR was merged, a file the task references was modified, a commit message matches the task), pre-check it (`[x]`) and add an HTML comment explaining the evidence (e.g., `<!-- PR #142 merged -->`, `<!-- commit: "feat: add X" -->`).
- **Pre-fill Activity**: Summarize git commits (message + branch/files touched) and any notable file modifications as a list.
- **Incomplete tasks**: Leave unchecked and add a blank `- Status:` line for the user to fill in.
- **Reflections**: Leave the section open with an HTML comment prompt.

Write the draft to `/tmp/pm-draft-YYYY-MM-DD-end.md` using this format:

```markdown
# End of day: YYYY-MM-DD — edit and save to confirm

## Tasks
- [x] Completed task [category]  <!-- PR #142 merged -->
  - Outcome: what success looked like
- [ ] Incomplete task [category]
  - Outcome: what success looks like
  - Status:

## Activity
- Merged PR #142 (description)
- 3 commits to feature/branch
- Modified: notes/some-note.md

## Reflections
<!-- what went well, what was hard, anything on your mind -->
```

Then open it in the user's editor:

```bash
${EDITOR:-vim} /tmp/pm-draft-YYYY-MM-DD-end.md
```

## 4. Process Edits

Read the edited file back. Clarify only if something is genuinely ambiguous — don't ask questions that can be reasonably inferred from context.

## 5. Write Daily Note

Clean up the temp file: `rm /tmp/pm-draft-YYYY-MM-DD-end.md`

Update `~/projects/phuston/daily/YYYY-MM-DD.md` with the final content. Strip the header instruction line (`# End of day: ... — edit and save to confirm`) and all HTML comments before writing.

## 6. Brief Closing

1-2 sentences highlighting what got done today. Be direct — no filler phrases.
