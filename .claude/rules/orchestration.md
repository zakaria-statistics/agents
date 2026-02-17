# Orchestration Rules

- Agents do not call each other directly
- Coordinate via shared/MEMORY.md and GitHub issues
- Human approves: production deploys, PR merge decisions
- PR merged → deployer triggers staging deploy
- Monitor detects P1/P2 → creates GitHub issue → coder picks up
- Full delegation rules: @orchestration/ORCHESTRATION.md
