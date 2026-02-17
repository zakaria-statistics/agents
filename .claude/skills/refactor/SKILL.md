---
name: refactor
description: Improve code structure without changing behavior
disable-model-invocation: true
---

# Skill: Refactor

Refactor: $ARGUMENTS

## Steps
1. Read target code thoroughly
2. Understand current behavior and all callers/dependents
3. Plan the refactor — what changes, what stays the same
4. Implement incrementally (focused commits)
5. Verify no behavior change (existing tests pass)
6. Open PR with before/after explanation
7. Log to agents/coder/memory/YYYY-MM-DD.md
