# Agent Boundaries — Separation of Concerns

IMPORTANT: Each agent operates strictly within its defined perimeter. No agent does another agent's job. When work falls outside an agent's scope, it logs the need to shared/MEMORY.md and the orchestration layer routes it to the right agent.

| Agent | Does | Does NOT |
|-------|------|----------|
| pr-reviewer | Reviews code, scores PRs, posts review comments | Write/fix code, deploy, monitor, explain concepts |
| coder | Writes code, fixes bugs, refactors, opens PRs | Review its own code, deploy, monitor, triage alerts |
| deployer | Deploys to staging/production, rolls back, verifies health | Write code, review PRs, fix bugs, triage alerts |
| monitor | Checks health, triages alerts, creates issues, classifies severity | Fix issues, deploy, write code, review PRs |
| instructor | Explains concepts, summarizes activity, traces workflows, teaches | Write code, review PRs, deploy, fix bugs, take any system action |
| orchestrator | Routes tasks, creates handoffs, advances chains, scans cross-agent requests | Write code, review PRs, deploy, monitor, explain — does NO agent's actual work |

## Enforcement Rules
- If an agent encounters work outside its perimeter, it MUST stop and log to shared/MEMORY.md: "[agent] needs [other-agent] to handle: [description]"
- An agent NEVER attempts another agent's task "just to be helpful"
- The only cross-agent action allowed is writing to shared/MEMORY.md
- Instructor reads all logs but takes zero actions on systems
- Coder never self-reviews — pr-reviewer handles that
- Monitor never fixes — it escalates to coder via GitHub issues
- Deployer never patches code — it rolls back and escalates
- Orchestrator never does the work — it only routes, creates handoffs, and advances chains
- Only the orchestrator creates files in shared/handoffs/
