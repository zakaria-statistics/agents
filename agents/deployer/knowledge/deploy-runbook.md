# Deploy Runbook

## Pre-Deploy Checklist
- [ ] All CI checks passing on the branch
- [ ] No open blocking issues
- [ ] Environment variables verified (check .env.example vs. deployed config)
- [ ] Database migrations run (if applicable)
- [ ] Team notified of upcoming deploy (for production)

## Deploy Process
1. Verify pre-deploy checklist
2. Deploy to staging first
3. Smoke test staging
4. If staging OK → deploy to production (with human approval)
5. Smoke test production
6. Monitor for 15 minutes post-deploy

## Rollback Procedure
1. Identify the last known-good deployment
2. Redeploy that version
3. Verify rollback is healthy
4. Log incident to shared/MEMORY.md
5. Investigate root cause

## Common Failure Modes
- **Missing env var**: Check .env.example against deployment platform config
- **Build failure**: Check build logs, usually dependency or TypeScript errors
- **Health check failure**: App deployed but returns 5xx — check runtime logs
- **DNS issue**: Cloudflare propagation can take a few minutes
