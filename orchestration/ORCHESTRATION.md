# Orchestration

## Agent Registry

| Agent | Directory | Triggers | Reads From | Writes To |
|-------|-----------|----------|------------|-----------|
| orchestrator | agents/orchestrator/ | multi-agent tasks, cross-agent requests | ALL shared/*, all agent docs, routing rules | shared/handoffs/, shared/MEMORY.md, own memory |
| pr-reviewer | agents/pr-reviewer/ | orchestrator handoff, manual | shared/context/, own knowledge, own memory | own memory, shared/MEMORY.md, handoff result |
| coder | agents/coder/ | orchestrator handoff, manual | shared/context/, own knowledge, own memory | own memory, shared/MEMORY.md, handoff result |
| test | agents/test/ | orchestrator handoff (after coder), manual | repo package.json, own knowledge, own memory | own memory, shared/MEMORY.md, handoff result |
| deployer | agents/deployer/ | orchestrator handoff, post-merge | shared/context/infra.md, own knowledge | own memory, shared/MEMORY.md, handoff result |
| monitor | agents/monitor/ | orchestrator handoff, cron | shared/context/infra.md, own knowledge | own memory, shared/MEMORY.md, handoff result |
| instructor | agents/instructor/ | manual, proactive | ALL agent memories, shared/*, orchestration/ | own memory, shared/MEMORY.md |

## How Agents Communicate

```
                    ┌─────────────┐
                    │ ORCHESTRATOR │
                    └──────┬──────┘
                           │ creates/manages
                    ┌──────▼──────┐
                    │  shared/    │
                    │  handoffs/  │
                    └──────┬──────┘
          ┌────────┬───────┼───────┬────────┐
          ▼        ▼       ▼       ▼        ▼
     ┌────────┐ ┌──────┐ ┌────┐ ┌────┐ ┌───────┐ ┌──────────┐
     │pr-revwr│ │coder │ │test│ │dplr│ │monitor│ │instructor│
     └───┬────┘ └──┬───┘ └─┬──┘ └─┬──┘ └───┬───┘ └────┬─────┘
         │         │       │      │        │           │
         └─────────┴───────┴──────┴────────┘           │
                        │                       │
                 shared/MEMORY.md ◄─────────────┘
              (cross-agent signals)        (reads only)
```

### Two Communication Channels

**Channel 1 — shared/MEMORY.md** (async signals)
Agents write cross-agent requests here:
```
- [timestamp] **[from-agent]** needs **[to-agent]**: [description]
```
The orchestrator scans for these and creates handoffs.

**Channel 2 — shared/handoffs/** (managed workflows)
The orchestrator creates structured handoff files:
- Single-agent dispatches for simple routed tasks
- Multi-step chains for workflows spanning agents
- Each agent reads its step, does the work, writes the result
- Orchestrator advances the chain when a step completes

### Rules
- Agents NEVER call each other directly
- Only the orchestrator creates/manages handoff files
- Agents write results back to their handoff step
- Cross-agent requests go through shared/MEMORY.md → orchestrator picks up

## Delegation Rules

### PR Lifecycle (chain: coder → test → pr-reviewer → deployer)
- Coder opens PR → orchestrator routes to test agent
- Tests pass → orchestrator routes to pr-reviewer
- Tests fail → orchestrator routes back to coder with failure report
- PR review complete → author addresses feedback
- PR merged → orchestrator routes to deployer for staging
- Staging verified → deployer requests human approval for production

### Incident Response (chain: monitor → coder → test → deployer)
- Monitor detects issue → logs to shared/MEMORY.md
- Orchestrator creates chain: coder fix → test verify → pr-reviewer review → deployer deploy
- P1/P2 → monitor also creates GitHub issue directly

### Code Changes (chain: coder → test → pr-reviewer → deployer)
- User requests feature/fix → orchestrator dispatches to coder
- Coder opens PR → orchestrator routes to test agent
- Tests pass → orchestrator routes to pr-reviewer
- Tests fail → orchestrator routes back to coder with failure details
- Review approved → orchestrator routes to deployer

### User Sync
- User asks "catch me up" → instructor scans all agent logs
- User encounters unfamiliar concept → instructor explains in context
- Instructor reads handoff files to report on workflow status

## Escalation
- If an agent is unsure, it logs the question to shared/MEMORY.md and asks the human
- P1 incidents always require human notification
- Stalled handoffs (>1 hour no progress) get flagged by orchestrator
- Instructor flags when the user hasn't been briefed on significant events
