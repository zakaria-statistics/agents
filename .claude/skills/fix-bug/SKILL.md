---
name: fix-bug
description: Diagnose and fix a reported bug
disable-model-invocation: true
---

# Skill: Fix Bug

Fix the bug described in: $ARGUMENTS

## Steps
1. Read bug report — understand expected vs. actual behavior
2. Locate relevant code
3. Trace the code path to identify root cause
4. Implement minimal fix — don't refactor surrounding code
5. Add a test that would have caught the bug
6. Commit and open PR with root cause explanation
7. Log to agents/coder/memory/YYYY-MM-DD.md
