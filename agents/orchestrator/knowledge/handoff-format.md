# Handoff File Format

Handoffs are markdown files in `shared/handoffs/`. Each file represents one workflow — either a single dispatch or a multi-step chain.

## Naming Convention
`YYYY-MM-DD-{short-slug}.md` — e.g., `2026-02-17-fix-login-bug.md`

## Single-Agent Handoff
```markdown
# Handoff: fix-login-bug

- **Status**: active | completed | failed | stalled
- **Created**: 2026-02-17 14:30
- **From**: user (or agent name)
- **To**: coder
- **Priority**: P2

## Task
Fix the login bug where sessions expire after 5 minutes.

## Context
- Issue: github.com/user/repo/issues/42
- Relevant files: src/auth/session.ts

## Result
<!-- Filled by the assigned agent when done -->
```

## Multi-Agent Chain
```markdown
# Handoff Chain: fix-and-deploy-login

- **Status**: in_progress
- **Created**: 2026-02-17 14:30
- **Priority**: P1

## Steps

### Step 1: Fix — coder
- **Status**: completed
- **Started**: 2026-02-17 14:30
- **Completed**: 2026-02-17 15:10
- **Result**: PR #47 opened — fix in src/auth/session.ts

### Step 2: Review — pr-reviewer
- **Status**: active
- **Started**: 2026-02-17 15:10
- **Result**: <!-- pending -->

### Step 3: Deploy — deployer
- **Status**: pending
- **Blocked by**: Step 2
- **Result**: <!-- pending -->

## Summary
<!-- Filled by orchestrator when chain completes -->
```

## Status Values
| Status | Meaning |
|--------|---------|
| pending | Waiting for a previous step to complete |
| active | Currently being worked on |
| completed | Done successfully |
| failed | Failed — see result for details |
| stalled | No progress for >1 hour — needs attention |
| cancelled | Aborted by user or orchestrator |

## Rules
- Only the orchestrator creates and updates handoff files
- Agents read their step to understand the task
- Agents write their result back to the handoff (Result field)
- Orchestrator advances status when a step completes
- On failure, orchestrator decides: retry, skip, or escalate to human
