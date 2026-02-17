# Coding Standards

## General Principles
- Write clear, readable code — optimize for the reader
- Prefer explicit over implicit
- Keep functions small and focused
- Name things descriptively — avoid abbreviations

## Error Handling
- Handle errors explicitly at system boundaries
- Use typed errors where the language supports it
- Log errors with context (what operation, what input)
- Don't swallow errors silently

## Testing
- Test behavior, not implementation
- One assertion per test when practical
- Name tests descriptively: "should [expected behavior] when [condition]"
- Use factories/fixtures for test data, not hardcoded values

## Git
- Conventional commits: type(scope): description
- Types: feat, fix, refactor, test, docs, chore
- Keep commits atomic — one logical change per commit
- Write PR descriptions that explain the "why"
