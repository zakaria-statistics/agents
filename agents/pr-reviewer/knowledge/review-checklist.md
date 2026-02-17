# Review Checklist

## Correctness
- [ ] Logic handles edge cases (null, empty, boundary values)
- [ ] Error paths are handled explicitly
- [ ] No infinite loops or unbounded recursion
- [ ] State mutations are intentional and documented

## Security
- [ ] No hardcoded secrets or credentials
- [ ] User input is validated and sanitized
- [ ] SQL queries use parameterized statements
- [ ] Auth checks are present on protected routes
- [ ] No sensitive data in logs or error messages

## Style
- [ ] Follows repo naming conventions
- [ ] Functions are focused (single responsibility)
- [ ] No dead code or commented-out blocks
- [ ] Imports are organized

## Testing
- [ ] New logic has corresponding tests
- [ ] Edge cases are tested
- [ ] Tests are deterministic (no flaky assertions)
- [ ] Mocks are appropriate (not over-mocking)

## Performance
- [ ] No N+1 queries
- [ ] Large datasets are paginated
- [ ] Expensive operations are cached where appropriate
