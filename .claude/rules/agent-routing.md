# Agent Routing

| Task pattern | Subagent | Skills |
|---|---|---|
| review PR, check code | pr-reviewer | /review-diff, /check-conventions |
| implement, build, fix, refactor | coder | /implement-feature, /fix-bug, /refactor |
| deploy, ship, release | deployer | /deploy-vercel, /deploy-cloudflare |
| health, status, alert | monitor | /health-check, /alert-triage |
| catch me up, explain, what happened, what does X mean, trace workflow | instructor | /catch-me-up, /explain-concept, /trace-workflow |

When a task matches, delegate to the subagent. The subagent reads its full AGENT.md and knowledge docs for detailed instructions.
