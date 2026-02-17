# Skill: Check Conventions

## Purpose
Verify that code changes follow the repository's established conventions.

## Inputs
- repo: repository name
- files: list of changed files (from PR diff)

## Steps
1. Read shared/context/repos.md for the repo's conventions
2. Read knowledge/review-checklist.md for general standards
3. For each file, check:
   - Naming conventions (files, variables, functions)
   - Import ordering and grouping
   - Error handling patterns
   - Comment style and documentation
   - Type annotations (if TypeScript/Python)
4. Compile list of violations with file:line references

## Output
- List of convention violations (blocking vs. nit)
