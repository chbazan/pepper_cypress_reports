# Performance Summary — Brasil Production

> **🔴 CRÍTICO** · V10.3.65 · 2026-04-07 17:35 UTC · [Ver workflow](https://github.com/Mercap/pepper-API-testing/actions/runs/24095248422)

---

## Resumen

| Campo | Valor |
|---|---|
| País / Ambiente | Brasil / Production |
| Versión | `V10.3.65` |
| Fecha | 2026-04-07 17:35 UTC |
| avg P95 actual | **378 ms** |
| Baseline global | 500 ms |
| Delta vs baseline | -24.4% |
| Endpoint más lento | Get investment metrics by ID |
| Semáforo global | 🔴 CRÍTICO |

## 🔴 Endpoints Críticos

| Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|
| All bonds - for issuer | **882 ms** | 357 ms | +147.3% | +109.5% |

## 🟡 Endpoints en Advertencia

| Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|
| Get valuation schemes by UUID | 72 ms | 44 ms | +62.3% | +22.0% |

## Top 10 Endpoints Más Lentos

| # | Endpoint | P95 | Payload |
|---|---|---|---|
| 1 | Get investment metrics by ID | 6094 ms | 1.03 KB |
| 2 | Appraise market value | 1815 ms | 0.63 KB |
| 3 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 1642 ms | 4.92 KB |
| 4 | All bonds - for issuer | 882 ms | 0.6 KB |
| 5 | Get investment irr sensitivity by ID | 716 ms | 1.64 KB |
| 6 | Get irrs - one bond | 552 ms | 9.84 KB |
| 7 | Get parities | 439 ms | 24.92 KB |
| 8 | Get investment price sensitivity by ID | 338 ms | 1.49 KB |
| 9 | Get mutual fund type by UUID | 190 ms | 0.13 KB |
| 10 | All bonds - deault parameters | 185 ms | 6.4 KB |

## Impact Ranking — Top 5

> `impact_score = baseline_p95 × total_ejecuciones`. Cuanto más alto, mayor retorno al optimizar.

| # | Endpoint | Impact Score | P95 actual | Baseline global |
|---|---|---|---|---|
| 1 | Get investment metrics by ID | 195.680 | 6094 ms | 6748 ms |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 52.933 | 1642 ms | 1825 ms |
| 3 | Appraise market value | 51.416 | 1815 ms | 1773 ms |
| 4 | Get investment irr sensitivity by ID | 20.170 | 716 ms | 696 ms |
| 5 | Get irrs - one bond | 19.619 | 552 ms | 677 ms |

## Tendencia — Últimas 5 corridas

| Fecha | avg P95 | Baseline global |
|---|---|---|
| 2026-04-06 | 644 ms | 497 ms |
| 2026-04-07 | 523 ms | 503 ms |
| 2026-04-07 | 509 ms | 504 ms |
| 2026-04-07 | 395 ms | 504 ms |
| 2026-04-07 | 378 ms | 500 ms |

---

*Generado automáticamente por [pepper-API-testing](https://github.com/Mercap/pepper-API-testing) · 2026-04-07 17:35 UTC*
