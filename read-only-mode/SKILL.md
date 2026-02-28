# Read-Only Mode

**All write operations are now FORBIDDEN.** This is an immediate, non-negotiable constraint.

## Prohibited Actions

Do NOT use any of these tools or actions under any circumstances:

- **Write** - Do not create any files
- **Edit** - Do not modify any files
- **NotebookEdit** - Do not modify any notebooks
- **Bash** with side effects - Do not run any command that creates, modifies, deletes, or moves files/directories (no `mkdir`, `rm`, `mv`, `cp`, `touch`, `chmod`, `pip install`, `npm install`, `brew install`, etc.)
- **Git write operations** - No `git commit`, `git push`, `git add`, `git checkout`, `git reset`, `git merge`, `git rebase`, `git stash`, `git branch -d`, `git tag`, or any git command that mutates state
- **GitHub write operations** - No `gh pr create`, `gh issue create`, `gh pr merge`, `gh pr comment`, or any gh command that mutates state

## Permitted Actions

Continue to freely use read-only tools:

- **Read** - Read any file
- **Glob** - Search for files by pattern
- **Grep** - Search file contents
- **Bash** (read-only) - Commands like `git status`, `git log`, `git diff`, `ls`, `pwd`, `which`, `env`, `git branch -l`, `gh pr view`, `gh pr list`
- **LSP** - All code intelligence operations
- **WebFetch / WebSearch** - Web lookups
- **Task** (with Explore or research agents only) - Codebase exploration
- **AskUserQuestion** - Ask the user anything

## Behavior

- If asked to make a change, explain what you *would* do but do not execute it
- Respond to questions, analyze code, review changes, and provide recommendations — just don't modify anything
- If the user explicitly asks to exit read-only mode (e.g., "resume editing", "read-write mode", "unlock", "you can edit again"), acknowledge the change and resume normal operations
