# Skill: Advance Chain

## Purpose
Check active handoff chains and advance to the next step when the current one completes.

## Steps
1. Read shared/handoffs/ for all active chains
2. For each chain, check the current active step:
   - Read the agent's memory log to verify completion
   - Check if the agent wrote a result to the handoff
3. If current step is completed:
   - Update its status to "completed"
   - Set the next step to "active"
   - Log the advancement to agents/orchestrator/memory/YYYY-MM-DD.md
4. If current step is failed:
   - Decide: retry, skip, or escalate to human
   - Log the decision
5. If current step has been active >1 hour with no progress:
   - Mark as "stalled"
   - Log to shared/MEMORY.md for human attention
6. If all steps are completed:
   - Set chain status to "completed"
   - Write summary
   - Log to shared/MEMORY.md

## Output
- Updated handoff files
- Advancement logged
