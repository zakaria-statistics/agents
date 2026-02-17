---
name: catch-me-up
description: Briefing on all agent activity since last session. Shows what happened, what needs attention, and what you missed.
---

# Catch Me Up

Produce a structured briefing of agent activity since: $ARGUMENTS (default: last briefing)

## Steps
1. Read agents/instructor/MEMORY.md for last briefing date
2. Read shared/MEMORY.md for cross-agent events
3. Scan agents/*/memory/ for daily logs since last briefing
4. Prioritize: incidents > decisions > completed tasks > routine
5. Flag items needing user attention
6. Note new concepts that weren't explained yet
7. Output structured briefing
8. Log to agents/instructor/memory/YYYY-MM-DD.md
