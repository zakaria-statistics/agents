# Skill: Review Diff

## Purpose
Analyze a PR diff and produce structured review comments.

## Inputs
- repo: repository name (owner/repo format)
- pr_number: PR number

## Steps
1. Fetch PR metadata via GitHub MCP (get_pull_request)
2. Fetch PR diff via GitHub MCP (get_pull_request_files)
3. Read knowledge/review-checklist.md for review criteria
4. Read shared/context/repos.md for repo-specific conventions
5. Analyze each changed file:
   - Correctness: logic errors, edge cases, null handling
   - Style: naming, formatting, consistency with repo conventions
   - Security: injection, auth issues, secret exposure
   - Test coverage: are changes tested? are edge cases covered?
6. Score each dimension /5
7. Format output using shared/templates/pr-template.md
8. Post review via GitHub MCP (create_pull_request_review)

## Output
- Review comment posted on the PR
- Summary logged to memory/YYYY-MM-DD.md
