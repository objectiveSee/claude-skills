---
name: commit-push
description: "Commit and push code changes in one step. Use when the user says /commit-push, /commit-and-push, 'commit and push', or wants to commit and push to the remote in a single action. Stages files, creates a commit with a meaningful message, then pushes to the current remote branch."
---

# Commit & Push

Create a git commit for the current changes and push to the remote.

## Workflow

1. Run `git status` (never use `-uall`), `git diff` (staged + unstaged), and `git log --oneline -5` in parallel
2. Analyze all changes and draft a concise commit message that focuses on the "why" not the "what"
3. Follow the repo's existing commit message style (check recent commits)
4. Stage relevant files by name (avoid `git add -A` or `git add .`)
5. Do not stage files that likely contain secrets (`.env`, credentials, etc.)
6. Create the commit. Pass the message via HEREDOC. Append: `Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>`
7. If a pre-commit hook fails, fix the issue and create a NEW commit (never amend)
8. Run `git status` after commit to verify success
9. Push to the current branch's remote tracking branch using `git push`. If no upstream is set, use `git push -u origin <current-branch>`
