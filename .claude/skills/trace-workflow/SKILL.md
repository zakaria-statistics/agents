---
name: trace-workflow
description: Walk through an end-to-end workflow showing how agents coordinate step by step
---

# Trace Workflow

Trace the workflow for: $ARGUMENTS

## Steps
1. Read orchestration/ORCHESTRATION.md for delegation rules
2. Identify all agents involved
3. Read each agent's AGENT.md for their role
4. Trace step by step: trigger → actions → memory writes → gates → outcomes
5. Show the flow as numbered steps with agent names
6. Flag gaps or failure modes
7. Log to agents/instructor/memory/YYYY-MM-DD.md
