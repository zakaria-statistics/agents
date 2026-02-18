# Skill: Check Coverage

## Purpose
Run tests with coverage reporting and compare against thresholds.

## Inputs
- repo_path: local path to the repository
- threshold: minimum coverage percentage (default: 80%)

## Steps
1. Navigate to repo_path
2. Detect test runner (jest, vitest, pytest, etc.)
3. Run tests with coverage flag
4. Parse coverage output (statements, branches, functions, lines)
5. Compare against threshold
6. Report pass/fail with breakdown

## Output
Coverage report with per-metric percentages and overall pass/fail.
