# Quality Gates

Scoring rubrics and thresholds for agent outputs.

## PR Review Quality
| Dimension | Weight | Minimum |
|-----------|--------|---------|
| Covers all changed files | 30% | Must review every file |
| Security issues identified | 25% | No false negatives on OWASP top 10 |
| Specific line references | 20% | Every comment has file:line |
| Actionable feedback | 15% | Comments explain why and suggest fix |
| Convention compliance | 10% | Checked against repo standards |

## Code Quality (Coder Output)
| Dimension | Weight | Minimum |
|-----------|--------|---------|
| Correctness | 30% | Passes all existing tests |
| Test coverage | 25% | New logic has tests |
| Style consistency | 20% | Matches repo conventions |
| Minimal changes | 15% | No unrelated modifications |
| PR description | 10% | Explains what and why |

## Deploy Quality
| Dimension | Weight | Minimum |
|-----------|--------|---------|
| Pre-deploy checks | 30% | All checklist items verified |
| Health verification | 30% | Post-deploy health check passes |
| Rollback readiness | 20% | Previous version identified |
| Logging | 20% | Deploy logged with full details |

## Monitor Quality
| Dimension | Weight | Minimum |
|-----------|--------|---------|
| Detection accuracy | 35% | No false positives on P1 |
| Response time | 25% | P1 logged within 5 minutes |
| Evidence quality | 25% | Status codes, timestamps included |
| Escalation correctness | 15% | Right severity, right channel |
