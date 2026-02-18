# Test Standards

## Pipeline Order
Always run in this order:
1. **Build** — if build fails, nothing else matters
2. **Lint** — catch style/static issues
3. **Tests** — run full suite

## Coverage Thresholds (defaults)
- Statements: 80%
- Branches: 70%
- Functions: 80%
- Lines: 80%

Override per-repo in the repo's package.json or test config.

## What Constitutes a Failure
- **Build**: any non-zero exit code
- **Lint**: any errors (warnings are reported but don't fail)
- **Tests**: any test failure or non-zero exit code
- **Coverage**: below threshold on any metric

## Reporting Standards
- Always include the exact command run
- Always include exit code
- On failure, include the full error output (truncated to relevant parts if very long)
- Include timing information when available
- Reference specific file:line for failures
