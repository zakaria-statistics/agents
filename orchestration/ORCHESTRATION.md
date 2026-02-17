# Orchestration

## Agent Registry

| Agent | Directory | Triggers | Reads From | Writes To |
|-------|-----------|----------|------------|-----------|
| pr-reviewer | agents/pr-reviewer/ | manual, delegated | shared/context/, own knowledge, own memory | own memory, shared/MEMORY.md |
| coder | agents/coder/ | manual, delegated | shared/context/, own knowledge, own memory | own memory, shared/MEMORY.md |
| deployer | agents/deployer/ | manual, post-merge | shared/context/infra.md, own knowledge | own memory, shared/MEMORY.md |
| monitor | agents/monitor/ | manual, cron | shared/context/infra.md, own knowledge | own memory, shared/MEMORY.md |
| instructor | agents/instructor/ | manual, proactive | ALL agent memories, shared/*, orchestration/ | own memory, shared/MEMORY.md |

## Delegation Rules

### PR Lifecycle
- PR opened → pr-reviewer reviews (if auto-review enabled)
- PR review complete → author addresses feedback
- PR merged to main → deployer triggers staging deploy
- Staging verified → deployer requests human approval for production

### Incident Response
- Monitor detects issue → logs to shared/MEMORY.md
- P1/P2 → monitor creates GitHub issue
- GitHub issue created → coder picks up fix (manual or delegated)
- Fix merged → deployer deploys

### Code Changes
- User requests feature/fix → coder implements
- Coder opens PR → pr-reviewer reviews
- Review approved → merge and deploy flow

## Communication Protocol
- Agents do not call each other directly
- Coordination happens via:
  1. shared/MEMORY.md — agents read for cross-cutting context
  2. Orchestration triggers — defined above
  3. GitHub issues — for task tracking
- Human approves: production deploys, PR merge decisions

### User Sync
- User asks "catch me up" → instructor scans all agent logs and produces briefing
- User encounters unfamiliar concept → instructor explains in project context
- User asks "how does X work" → instructor traces the workflow end-to-end
- Instructor proactively flags: unreviewed shared/MEMORY.md entries, knowledge gaps

## Escalation
- If an agent is unsure, it logs the question to shared/MEMORY.md and asks the human
- P1 incidents always require human notification
- Instructor flags when the user hasn't been briefed on significant events
