# Skill: Catch Me Up

## Purpose
Produce a structured briefing of all agent activity since the user's last session.

## Inputs
- since: date or "last session" (default: today)

## Steps
1. Read agents/instructor/MEMORY.md — check last briefing date
2. Read shared/MEMORY.md for cross-agent events
3. Scan each agent's memory/ directory for daily logs since last briefing:
   - agents/pr-reviewer/memory/
   - agents/coder/memory/
   - agents/deployer/memory/
   - agents/monitor/memory/
4. Read orchestration/ORCHESTRATION.md for context on agent relationships
5. Compile events by priority:
   - Incidents and failures (highest)
   - Completed tasks and decisions
   - Patterns learned and memory updates
   - Routine activity (lowest)
6. For each event, note: which agent, what happened, user action needed (if any)
7. Flag anything the user hasn't been briefed on yet
8. Output structured briefing
9. Log to agents/instructor/memory/YYYY-MM-DD.md

## Output Format
```
## Briefing — YYYY-MM-DD

### Needs Your Attention
- [item with action needed]

### What Happened
| Agent | Action | Result | Details |
|-------|--------|--------|---------|

### New Patterns Learned
- [agent]: [pattern]

### Knowledge Gaps to Cover
- [concept that came up but wasn't explained]
```
