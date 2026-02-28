---
name: gh
description: >
  GitHub CLI mode — use the `gh` command line tool for ALL GitHub interactions.
  Activate when the user says "gh mode", "github cli", "use gh", or invokes /gh.
  Also activate when the user asks to explore a GitHub repo, look up issues, review
  PRs, search code on GitHub, check CI status, or any GitHub-related task.
---

# GitHub CLI Mode

**Use `gh` for everything.** Never open or reference the GitHub website. Never use raw GitHub URLs with WebFetch. The CLI is the interface.

## Core Commands

### Repos
- `gh repo view <owner/repo>` — README and metadata
- `gh repo clone <owner/repo>` — clone locally
- `gh api repos/<owner>/<repo>` — raw repo data
- `gh search repos <query>` — find repos

### Issues
- `gh issue list -R <owner/repo>` — list issues
- `gh issue view <number> -R <owner/repo>` — read an issue with full body
- `gh issue view <number> -R <owner/repo> --comments` — include conversation
- `gh search issues <query> -R <owner/repo>` — search issues

### Pull Requests
- `gh pr list -R <owner/repo>` — list PRs
- `gh pr view <number> -R <owner/repo>` — PR summary
- `gh pr view <number> -R <owner/repo> --comments` — PR conversation
- `gh pr diff <number> -R <owner/repo>` — full diff
- `gh pr checks <number> -R <owner/repo>` — CI status
- `gh search prs <query> -R <owner/repo>` — search PRs

### Code Search
- `gh search code <query> -R <owner/repo>` — search code across a repo
- `gh search code <query>` — search code across all of GitHub

### Releases & Tags
- `gh release list -R <owner/repo>` — list releases
- `gh release view <tag> -R <owner/repo>` — release details

### API (escape hatch for anything else)
- `gh api <endpoint>` — hit any GitHub REST API endpoint
- `gh api graphql -f query='...'` — GraphQL queries
- `gh api repos/<owner>/<repo>/contents/<path>` — read a file without cloning

## Useful Patterns

**Deep-dive an issue thread:**
```bash
gh issue view 1234 -R owner/repo --comments
```

**See what changed in a PR:**
```bash
gh pr diff 567 -R owner/repo
```

**Find related issues:**
```bash
gh search issues "error message" -R owner/repo
```

**Browse repo files without cloning:**
```bash
gh api repos/owner/repo/contents/src --jq '.[].name'
```

**Check recent activity:**
```bash
gh api repos/owner/repo/events --jq '.[:10] | .[].type'
```

## Rules

- Always use `gh`, never WebFetch on github.com URLs
- Add `-R owner/repo` when working with a repo that isn't the current directory
- Use `--json` and `--jq` flags to extract specific fields when output is noisy
- Paginate with `--limit` when lists are long
- If the user asks to exit gh mode, acknowledge and resume normal operations
