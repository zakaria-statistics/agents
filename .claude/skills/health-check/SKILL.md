---
name: health-check
description: Check health of monitored endpoints and services
---

# Skill: Health Check

Check health of: $ARGUMENTS (or all services if not specified)

## Steps
1. Read shared/context/infra.md for services and endpoints
2. Read agents/monitor/knowledge/sla-thresholds.md for thresholds
3. For each endpoint: send GET, record status code + response time
4. Compare against thresholds (healthy / degraded / down)
5. For degraded/down: log to shared/MEMORY.md
6. Log all results to agents/monitor/memory/YYYY-MM-DD.md
7. Output health status table
