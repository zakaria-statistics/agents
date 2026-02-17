# Skill: Dispatch Task

## Purpose
Route a task to the correct agent or create a multi-agent handoff chain.

## Inputs
- task: what needs to be done
- priority: P1 / P2 / P3 (default: P2)

## Steps
1. Read .claude/rules/agent-routing.md — match task to agent(s)
2. Read .claude/rules/boundaries.md — verify routing respects perimeters
3. Determine if single-agent or multi-agent:
   - Single: create a single handoff file in shared/handoffs/
   - Multi: create a chain handoff with ordered steps
4. Set first step to "active"
5. Log routing decision to agents/orchestrator/memory/YYYY-MM-DD.md
6. Update agents/orchestrator/MEMORY.md with active workflow

## Output
- Handoff file created in shared/handoffs/
- Routing decision logged
