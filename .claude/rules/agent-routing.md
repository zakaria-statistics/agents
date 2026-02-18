# Agent Routing

## Single-Agent Tasks
| Task pattern | Subagent | Skills |
|---|---|---|
| review PR, check code | pr-reviewer | /review-diff, /check-conventions |
| implement, build, fix, refactor | coder | /implement-feature, /fix-bug, /refactor |
| test, lint, build check, run tests, verify | test | /run-tests |
| deploy, ship, release | deployer | /deploy-vercel, /deploy-cloudflare |
| health, status, alert | monitor | /health-check, /alert-triage |
| catch me up, explain, what happened, trace workflow | instructor | /catch-me-up, /explain-concept, /trace-workflow |

## Multi-Agent Tasks → Route to Orchestrator
If a task requires more than one agent, the orchestrator handles it via /dispatch.

| Task pattern | Chain | Orchestrator creates |
|---|---|---|
| "fix and deploy" | coder → test → pr-reviewer → deployer | 4-step handoff chain |
| "fix this P1" | monitor (triage) → coder → test → deployer | incident response chain |
| "review and merge and deploy" | pr-reviewer → deployer | 2-step chain |
| "build feature X end to end" | coder → test → pr-reviewer → deployer | full lifecycle chain |

## Cross-Agent Requests
When an agent logs "[agent] needs [other-agent] to handle: [task]" to shared/MEMORY.md, the orchestrator picks it up and creates a handoff in shared/handoffs/.

## Routing Rule
- Single-agent task → delegate directly to that subagent
- Multi-agent task → delegate to orchestrator, which creates the chain
- The subagent reads its full AGENT.md and knowledge docs for detailed instructions
