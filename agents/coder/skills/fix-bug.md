# Skill: Fix Bug

## Purpose
Diagnose and fix a reported bug.

## Inputs
- repo: repository name
- issue: bug description or issue link
- branch: branch name (default: fix/<slug>)

## Steps
1. Read the bug report — understand expected vs. actual behavior
2. Locate the relevant code
3. Reproduce the issue mentally (trace the code path)
4. Identify the root cause
5. Implement the fix — minimal change, don't refactor surrounding code
6. Add a test that would have caught the bug
7. Commit and open PR

## Output
- Bug fix committed
- PR opened with root cause explanation
- Logged to memory/YYYY-MM-DD.md
