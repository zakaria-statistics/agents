# Skill: Health Check

## Purpose
Check the health of monitored endpoints and services.

## Inputs
- target: specific service to check (optional — default: check all)

## Steps
1. Read shared/context/infra.md for list of services and endpoints
2. Read knowledge/sla-thresholds.md for acceptable response times and status codes
3. For each endpoint:
   - Send HTTP request (GET to health endpoint)
   - Record: status code, response time, any error message
   - Compare against thresholds
4. Compile results:
   - Healthy: status 2xx and response time within threshold
   - Degraded: status 2xx but slow, or intermittent errors
   - Down: status 5xx or no response
5. For degraded/down services: log to shared/MEMORY.md
6. Log all results to memory/YYYY-MM-DD.md

## Output
- Health status table (service, status, response time, verdict)
- Incidents logged if any failures detected
