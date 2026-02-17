# Agents Project

Multi-agent dev workflow automation. 4 agents: pr-reviewer, coder, deployer, monitor.

## Structure
- `.claude/agents/` — Subagent definitions (official Claude Code format)
- `.claude/skills/` — Invocable skills (/review-diff, /fix-bug, /deploy-vercel, etc.)
- `.claude/rules/` — Modular rules (routing, memory, orchestration, safety)
- `agents/` — Rich agent docs: AGENT.md, knowledge/, skills/ (detailed reference)
- `shared/` — Cross-agent memory, context docs, templates
- `orchestration/` — Delegation rules, cron, quality gates

## Context (load on demand)
- @shared/context/repos.md — Repo conventions
- @shared/context/infra.md — Infrastructure map
- @shared/context/team.md — Team and permissions
- @orchestration/ORCHESTRATION.md — Full delegation rules

## MCP Tools
- **GitHub** — PRs, issues, code search
- **Notion** — Docs and knowledge base
- **Vercel** — Deploy management
