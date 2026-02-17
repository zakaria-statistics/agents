# Skill: Alert Triage

## Purpose
Triage an incoming alert and determine severity and next steps.

## Inputs
- alert: alert description or notification content
- source: where the alert came from

## Steps
1. Parse alert content — identify affected service and error type
2. Check shared/context/infra.md to understand the service
3. Check monitor MEMORY.md for similar past incidents
4. Determine severity:
   - P1: Service is down, users affected
   - P2: Service degraded, partial functionality impacted
   - P3: Minor issue, no user impact
5. Determine next steps:
   - P1: Create GitHub issue immediately, log to shared/MEMORY.md, recommend deployer rollback
   - P2: Create GitHub issue, log to shared/MEMORY.md
   - P3: Log to daily memory, monitor for escalation
6. Use shared/templates/incident-template.md for incident reports

## Output
- Severity classification
- GitHub issue created (P1/P2)
- Incident report logged
