# Skill: Run Pipeline

## Purpose
Run the full test pipeline (build + lint + tests) on a repository branch.

## Inputs
- repo_path: local path to the repository
- branch: branch to test (optional — uses current branch)

## Steps
1. Navigate to repo_path
2. Check if node_modules exists — run `npm install` if missing
3. Identify available scripts from package.json (build, lint, test)
4. Run `npm run build` — capture output and exit code
5. Run `npm run lint` — capture output and exit code
6. Run `npm test` — capture output and exit code (skip if no test script)
7. Compile structured report with pass/fail per step
8. Log results to memory/YYYY-MM-DD.md

## Output
Structured test report with pass/fail, error details, and overall verdict.
