# Learning Paths

Structured progressions for understanding key areas of this system.

## Path: Agent Architecture
1. What is a Claude Code subagent (`.claude/agents/` format)
2. How AGENT.md relates to subagent files (rich docs vs. runtime config)
3. How skills work (`.claude/skills/` with SKILL.md)
4. How memory persists across sessions (auto memory, MEMORY.md)
5. How agents coordinate (shared/MEMORY.md, orchestration triggers)
6. How rules are loaded (`.claude/rules/`, CLAUDE.md hierarchy)

## Path: PR Review Flow
1. What triggers a PR review
2. How the pr-reviewer reads diffs (GitHub MCP)
3. How it scores reviews (the checklist)
4. How reviews get posted (GitHub MCP)
5. How the review is logged (daily memory)

## Path: Deploy Pipeline
1. What triggers a deploy
2. Staging vs. production (approval gates)
3. Vercel MCP operations
4. Cloudflare MCP operations
5. Health verification post-deploy
6. Rollback procedure

## Path: Incident Response
1. How the monitor detects issues
2. Severity classification (P1/P2/P3)
3. How incidents get logged to shared memory
4. How issues get created on GitHub
5. How the coder picks up fixes
6. How the fix gets deployed

## Path: MCP Tools
1. What MCP is (Model Context Protocol)
2. How .mcp.json configures servers
3. GitHub MCP — what operations are available
4. Vercel MCP — deployment operations
5. Notion MCP — documentation access
