---
name: deploy-cloudflare
description: Deploy a Cloudflare Worker or Pages project
disable-model-invocation: true
---

# Skill: Deploy to Cloudflare

Deploy: $ARGUMENTS

## Steps
1. Read shared/context/infra.md for Cloudflare project details
2. Read agents/deployer/knowledge/deploy-runbook.md
3. Verify wrangler config is correct
4. If production: pause and request human approval
5. Deploy via Cloudflare MCP or wrangler CLI
6. Verify deployed endpoint responds correctly
7. Log to agents/deployer/memory/YYYY-MM-DD.md
8. On failure: log incident to shared/MEMORY.md
