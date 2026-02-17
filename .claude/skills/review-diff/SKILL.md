---
name: review-diff
description: Analyze a PR diff and produce structured review comments
---

# Skill: Review Diff

Analyze a PR diff and produce a structured review.

## Usage
/review-diff owner/repo#123

## Steps
1. Fetch PR metadata via GitHub MCP (get_pull_request)
2. Fetch PR diff via GitHub MCP (get_pull_request_files)
3. Read agents/pr-reviewer/knowledge/review-checklist.md
4. Read shared/context/repos.md for repo conventions
5. Analyze each changed file for correctness, style, security, test coverage
6. Score each dimension /5
7. Format using shared/templates/pr-template.md
8. Post review via GitHub MCP (create_pull_request_review)
9. Log summary to agents/pr-reviewer/memory/YYYY-MM-DD.md
