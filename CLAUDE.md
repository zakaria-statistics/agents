# Agents Project

Multi-agent dev workflow automation. 6 agents with strict separation of concerns.

## Agents
| Agent | Does | Model |
|-------|------|-------|
| orchestrator | Routes tasks, manages handoff chains, scans cross-agent requests | inherit |
| pr-reviewer | Reviews PRs, scores code quality | sonnet |
| coder | Writes code, fixes bugs, refactors, opens PRs | inherit |
| deployer | Deploys to Vercel/Cloudflare, rolls back | sonnet |
| monitor | Health checks, alert triage, severity classification | haiku |
| instructor | Explains concepts, summarizes activity, teaches workflows | inherit |

## Structure
- `.claude/agents/` — Subagent definitions (official Claude Code format)
- `.claude/skills/` — Invocable skills (/dispatch, /review-diff, /fix-bug, /deploy-vercel, /catch-me-up, etc.)
- `.claude/rules/` — Modular rules (routing, boundaries, communication, memory, orchestration, safety)
- `agents/` — Rich agent docs: AGENT.md, knowledge/, skills/ (detailed reference)
- `shared/handoffs/` — Cross-agent handoff queue (managed by orchestrator only)
- `shared/` — Cross-agent memory, context docs, templates
- `orchestration/` — Delegation rules, cron, quality gates

## Communication
- Agents never call each other directly
- Channel 1: `shared/MEMORY.md` — async signals ("[agent] needs [other-agent]: [task]")
- Channel 2: `shared/handoffs/` — structured workflows managed by orchestrator
- Multi-agent tasks → orchestrator creates handoff chains
- Full protocol: @.claude/rules/communication.md

## Context (load on demand)
- @shared/context/repos.md — Repo conventions
- @shared/context/infra.md — Infrastructure map
- @shared/context/team.md — Team and permissions
- @orchestration/ORCHESTRATION.md — Full delegation rules

## MCP Tools
- **GitHub** — PRs, issues, code search
- **Notion** — Docs and knowledge base
- **Vercel** — Deploy management
