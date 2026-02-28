---
name: commit
description: "Commit code changes with a well-crafted message. Use when the user says /commit, 'commit this', 'commit my changes', or asks to create a git commit. Stages relevant files, analyzes changes, and creates a commit with a concise, meaningful message."
---

# Commit

Create a git commit for the current changes.

## Workflow

1. Run `git status` (never use `-uall`), `git diff` (staged + unstaged), and `git log --oneline -5` in parallel
2. Analyze all changes and draft a concise commit message that focuses on the "why" not the "what"
3. Follow the repo's existing commit message style (check recent commits)
4. Stage relevant files by name (avoid `git add -A` or `git add .`)
5. Do not stage files that likely contain secrets (`.env`, credentials, etc.)
6. Create the commit. Pass the message via HEREDOC. Append: `Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>`
7. If a pre-commit hook fails, fix the issue and create a NEW commit (never amend)
8. Run `git status` after to verify success
