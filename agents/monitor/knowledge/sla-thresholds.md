# SLA Thresholds

## Response Time
| Service Type | Target | Degraded | Critical |
|---|---|---|---|
| Web app | < 500ms | 500ms - 2s | > 2s |
| API endpoint | < 200ms | 200ms - 1s | > 1s |
| Static assets | < 100ms | 100ms - 500ms | > 500ms |
| Background job | < 30s | 30s - 60s | > 60s |

## Availability
| Tier | Target | Alert threshold |
|---|---|---|
| Critical (auth, payments) | 99.9% | 2 failures in 5 min |
| Standard (main app) | 99.5% | 5 failures in 15 min |
| Best-effort (internal tools) | 99% | 10 failures in 30 min |

## Health Check Endpoints
<!-- Populated from shared/context/infra.md -->
<!-- Format: GET /health or GET /api/health should return 200 -->
