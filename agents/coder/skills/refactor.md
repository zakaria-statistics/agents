# Skill: Refactor

## Purpose
Improve code structure without changing behavior.

## Inputs
- repo: repository name
- target: what to refactor (file, module, pattern)
- goal: why (readability, performance, maintainability)

## Steps
1. Read the target code thoroughly
2. Understand current behavior and all callers/dependents
3. Plan the refactor — document what changes and what stays the same
4. Implement incrementally (keep each commit focused)
5. Verify no behavior change (existing tests should still pass)
6. Open PR with before/after explanation

## Output
- Refactored code committed
- PR opened with rationale
- Logged to memory/YYYY-MM-DD.md
