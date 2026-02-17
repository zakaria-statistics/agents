---
name: deploy-vercel
description: Deploy an application to Vercel
disable-model-invocation: true
---

# Skill: Deploy to Vercel

Deploy: $ARGUMENTS

## Steps
1. Read shared/context/infra.md for Vercel project details
2. Read agents/deployer/knowledge/deploy-runbook.md
3. Check project exists via Vercel MCP (getProject)
4. Verify environment variables are configured
5. If production: pause and request human approval
6. Trigger deployment via Vercel MCP (createDeployment)
7. Monitor status (getDeployment)
8. Verify deployed URL returns 200
9. Log to agents/deployer/memory/YYYY-MM-DD.md
10. On failure: log incident to shared/MEMORY.md
