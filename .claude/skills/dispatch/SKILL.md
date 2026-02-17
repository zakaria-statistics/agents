---
name: dispatch
description: Route a task to the correct agent or create a multi-agent handoff chain
disable-model-invocation: true
---

# Dispatch

Route this task: $ARGUMENTS

## Steps
1. Read .claude/rules/agent-routing.md — match task to agent(s)
2. Read .claude/rules/boundaries.md — verify perimeters
3. Single-agent → create handoff in shared/handoffs/
4. Multi-agent → create chain with ordered steps
5. Set first step to "active"
6. Use format from agents/orchestrator/knowledge/handoff-format.md
7. Log to agents/orchestrator/memory/YYYY-MM-DD.md
