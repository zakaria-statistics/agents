---
name: check-conventions
description: Verify code changes follow repository conventions
---

# Skill: Check Conventions

Verify that code changes follow the repository's established conventions.

## Usage
/check-conventions owner/repo#123

## Steps
1. Read shared/context/repos.md for repo conventions
2. Read agents/pr-reviewer/knowledge/review-checklist.md
3. For each changed file, check naming, imports, error handling, types
4. Compile list of violations with file:line references
5. Classify as blocking vs. nit
