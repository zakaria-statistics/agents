---
name: run-tests
description: Run the full test pipeline (build + lint + tests) on a repository
agent: test
arguments:
  - name: repo
    description: Repository name or path
    required: true
---

# Run Tests

Run the full test pipeline on a repository to verify code changes.

## Steps
1. Identify the repo path from the argument
2. Delegate to the test agent
3. Test agent runs build → lint → tests
4. Report structured results
