# Skill: Scan Cross-Agent Requests

## Purpose
Scan shared/MEMORY.md for cross-agent requests that need routing.

## Steps
1. Read shared/MEMORY.md
2. Look for entries matching the pattern: "[agent] needs [other-agent] to handle: [description]"
3. For each unhandled request:
   - Create a handoff in shared/handoffs/
   - Set priority based on context (P1 if incident-related, P2 otherwise)
   - Remove or mark the request as handled in shared/MEMORY.md
4. Log all new dispatches to agents/orchestrator/memory/YYYY-MM-DD.md

## Output
- New handoffs created for pending cross-agent requests
- shared/MEMORY.md cleaned up
