# Cross-Agent Communication Protocol

Agents NEVER talk to each other directly. All coordination flows through two channels:

## Channel 1: shared/MEMORY.md (async signals)
Agents write structured messages when they need another agent's help:
```
## Cross-Agent Requests
- [YYYY-MM-DD HH:MM] **pr-reviewer** needs **coder**: null check missing in auth.ts:45, flagged as blocking
- [YYYY-MM-DD HH:MM] **monitor** needs **deployer**: rollback needed, API returning 503 since 14:20
```
The orchestrator scans these and creates handoffs.

## Channel 2: shared/handoffs/ (managed workflows)
The orchestrator creates structured handoff files for routed work:
- Single-agent dispatches for simple tasks
- Multi-step chains for workflows spanning multiple agents
- Each agent reads its step, does the work, writes the result
- The orchestrator advances the chain

## What Agents Can and Cannot Do
| Action | Allowed | Channel |
|--------|---------|---------|
| Request another agent's help | Yes | shared/MEMORY.md |
| Read another agent's memory | Instructor and Orchestrator only | direct read |
| Write to another agent's files | No | — |
| Call another agent directly | No | — |
| Update handoff results | Yes (own step only) | shared/handoffs/ |
| Create handoff files | Orchestrator only | shared/handoffs/ |

## Message Format for shared/MEMORY.md
```
- [timestamp] **[from-agent]** needs **[to-agent]**: [description]
```
This is the ONLY format agents use for cross-agent requests. The orchestrator pattern-matches on this to create handoffs.
