---
name: alert-triage
description: Triage an incoming alert and determine severity and next steps
disable-model-invocation: true
---

# Skill: Alert Triage

Triage alert: $ARGUMENTS

## Steps
1. Parse alert — identify affected service and error type
2. Check shared/context/infra.md for service context
3. Check agents/monitor/MEMORY.md for similar past incidents
4. Classify severity: P1 (down), P2 (degraded), P3 (minor)
5. P1: create GitHub issue, log to shared/MEMORY.md, recommend rollback
6. P2: create GitHub issue, log to shared/MEMORY.md
7. P3: log to daily memory, monitor for escalation
8. Use shared/templates/incident-template.md for report format
