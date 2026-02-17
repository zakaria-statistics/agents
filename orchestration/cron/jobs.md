# Cron Jobs

Scheduled tasks for agents. These are reference configurations — actual scheduling is external.

| Schedule | Agent | Skill | Description |
|----------|-------|-------|-------------|
| Every 30min | monitor | health-check | Check all monitored endpoints |
| Every 1h | pr-reviewer | review-diff | Scan for unreviewed open PRs |
| Daily 09:00 | monitor | health-check | Full health report |

## Notes
- Cron execution is triggered externally (e.g., system cron, GitHub Actions)
- Each job invokes Claude Code with the appropriate agent context
- Results are logged to the agent's daily memory
