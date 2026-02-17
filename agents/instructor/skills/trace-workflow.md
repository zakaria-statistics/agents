# Skill: Trace Workflow

## Purpose
Walk through an end-to-end workflow showing how agents coordinate.

## Inputs
- workflow: which flow to trace (e.g., "PR review", "deploy", "incident response")

## Steps
1. Read orchestration/ORCHESTRATION.md for delegation rules
2. Identify all agents involved in the workflow
3. Read each agent's AGENT.md for their role in the flow
4. Read relevant skills for step-by-step details
5. Trace the flow step by step:
   - Who starts it (trigger)
   - What each agent does (actions)
   - Where data flows (memory reads/writes)
   - Where human approval is needed (gates)
   - What happens on success vs. failure (branches)
6. Create a visual flow using numbered steps
7. Flag any gaps or single points of failure
8. Log to agents/instructor/memory/YYYY-MM-DD.md

## Output Format
```
## Workflow: [name]

### Trigger
[what kicks this off]

### Flow
1. **[Agent]**: [action] → writes to [location]
2. **[Agent]**: reads [location] → [action]
3. **Human**: [approval gate]
4. ...

### On Failure
[what happens if step N fails]

### Memory Trail
- [what gets logged where]
```
