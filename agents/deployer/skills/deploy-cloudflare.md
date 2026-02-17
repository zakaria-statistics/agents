# Skill: Deploy to Cloudflare

## Purpose
Deploy a Cloudflare Worker or Pages project.

## Inputs
- project: Cloudflare project/worker name
- environment: staging | production

## Steps
1. Read shared/context/infra.md for Cloudflare project details
2. Verify wrangler config is correct
3. If production: pause and request human approval
4. Deploy via Cloudflare MCP or wrangler CLI
5. Verify the deployed endpoint responds correctly
6. Log deploy result to memory/YYYY-MM-DD.md

## Output
- Deployment URL
- Status: success / failed
- Logged to daily memory
