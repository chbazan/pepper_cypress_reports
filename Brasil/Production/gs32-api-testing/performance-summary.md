# Performance Summary — Brasil Production

> **🟢 OK** · V10.3.65 · 2026-04-07 18:40 UTC · [Ver workflow](https://github.com/Mercap/pepper-API-testing/actions/runs/24098086208)

---

## Resumen

| Campo | Valor |
|---|---|
| País / Ambiente | Brasil / Production |
| Versión | `V10.3.65` |
| Fecha | 2026-04-07 18:40 UTC |
| avg P95 actual | **339 ms** |
| Baseline global | 496 ms |
| Delta vs baseline | -31.7% |
| Endpoint más lento | Get investment metrics by ID |
| Semáforo global | 🟢 OK |

## 🟢 Semáforo

Todos los endpoints dentro de parámetros normales.

## Top 10 Endpoints Más Lentos

| # | Endpoint | P95 | Payload |
|---|---|---|---|
| 1 | Get investment metrics by ID | 5625 ms | 1.03 KB |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 1774 ms | 4.92 KB |
| 3 | Appraise market value | 1739 ms | 0.63 KB |
| 4 | Get investment irr sensitivity by ID | 743 ms | 1.64 KB |
| 5 | Get irrs - one bond | 468 ms | 9.84 KB |
| 6 | Get investment price sensitivity by ID | 400 ms | 1.49 KB |
| 7 | All bonds - for issuer | 264 ms | 0.6 KB |
| 8 | All bonds - deault parameters | 199 ms | 6.4 KB |
| 9 | Get parities | 193 ms | 24.92 KB |
| 10 | Get tradable security metrics | 186 ms | 1.24 KB |

## Impact Ranking — Top 5

> `impact_score = baseline_p95 × total_ejecuciones`. Cuanto más alto, mayor retorno al optimizar.

| # | Endpoint | Impact Score | P95 actual | Baseline global |
|---|---|---|---|---|
| 1 | Get investment metrics by ID | 201.751 | 5625 ms | 6725 ms |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 54.569 | 1774 ms | 1819 ms |
| 3 | Appraise market value | 53.232 | 1739 ms | 1774 ms |
| 4 | Get investment irr sensitivity by ID | 20.888 | 743 ms | 696 ms |
| 5 | Get irrs - one bond | 20.162 | 468 ms | 672 ms |

## Tendencia — Últimas 5 corridas

| Fecha | avg P95 | Baseline global |
|---|---|---|
| 2026-04-07 | 523 ms | 503 ms |
| 2026-04-07 | 509 ms | 504 ms |
| 2026-04-07 | 395 ms | 504 ms |
| 2026-04-07 | 378 ms | 500 ms |
| 2026-04-07 | 339 ms | 496 ms |

---

*Generado automáticamente por [pepper-API-testing](https://github.com/Mercap/pepper-API-testing) · 2026-04-07 18:40 UTC*
