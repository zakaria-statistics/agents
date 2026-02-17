# Skill: Deploy to Vercel

## Purpose
Deploy an application to Vercel (staging or production).

## Inputs
- project: Vercel project name
- environment: staging | production
- branch: branch to deploy (default: main)

## Steps
1. Read shared/context/infra.md for Vercel project details
2. Check that the project exists via Vercel MCP (getProject)
3. Verify environment variables are configured
4. If production: pause and request human approval
5. Trigger deployment via Vercel MCP (createDeployment)
6. Monitor deployment status (getDeployment)
7. Verify the deployed URL returns 200
8. Log deploy result to memory/YYYY-MM-DD.md

## Output
- Deployment URL
- Status: success / failed
- Logged to daily memory

## Rollback
- If deploy fails or health check fails, redeploy previous known-good commit
