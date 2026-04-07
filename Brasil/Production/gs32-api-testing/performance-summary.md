# Performance Summary — Brasil Production

> **🔴 CRÍTICO** · V10.3.65 · 2026-04-07 15:01 UTC · [Ver workflow](https://github.com/Mercap/pepper-API-testing/actions/runs/24088309095)

---

## Resumen

| Campo | Valor |
|---|---|
| País / Ambiente | Brasil / Production |
| Versión | `V10.3.65` |
| Fecha | 2026-04-07 15:01 UTC |
| avg P95 actual | **509 ms** |
| Baseline global | 504 ms |
| Delta vs baseline | +1.0% |
| Endpoint más lento | Get investment metrics by ID |
| Semáforo global | 🔴 CRÍTICO |

## 🔴 Endpoints Críticos

| Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|
| Get all mutual fund shares | **1419 ms** | 208 ms | +583.4% | +382.6% |

## 🟡 Endpoints en Advertencia

| Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|
| Get irrs - one bond | 906 ms | 674 ms | +34.5% | +53.0% |
| Get exchange scheme by UUID | 61 ms | 39 ms | +56.9% | +15.1% |
| Get markets by UUID | 63 ms | 43 ms | +47.0% | +12.5% |
| Get mutual fund type by UUID | 281 ms | 134 ms | +109.2% | +64.3% |
| Get all stocks | 320 ms | 195 ms | +64.5% | +35.6% |
| Get tradable securities using optional filters - only query | 864 ms | 546 ms | +58.1% | +27.6% |
| Get valuation schemes by UUID | 80 ms | 42 ms | +88.6% | +90.5% |

## Outliers Detectados

> Endpoints que superaron 3× su baseline histórico en esta corrida.

| Endpoint | P95 observado | Baseline | Ratio |
|---|---|---|---|
| Get all mutual fund shares | **1419 ms** | 208 ms | **6.83×** |

## Top 10 Endpoints Más Lentos

| # | Endpoint | P95 | Payload |
|---|---|---|---|
| 1 | Get investment metrics by ID | 7059 ms | 1.03 KB |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 2117 ms | 4.92 KB |
| 3 | Appraise market value | 1980 ms | 0.63 KB |
| 4 | Get all mutual fund shares | 1419 ms | 0.08 KB |
| 5 | Get irrs - one bond | 906 ms | 9.84 KB |
| 6 | Get tradable securities using optional filters - only query | 864 ms | 0.69 KB |
| 7 | Get investment irr sensitivity by ID | 762 ms | 1.64 KB |
| 8 | Get parities | 464 ms | 24.92 KB |
| 9 | Get tradable securities using only mandatory filters | 441 ms | 12.02 KB |
| 10 | Get investment price sensitivity by ID | 427 ms | 1.49 KB |

## Impact Ranking — Top 5

> `impact_score = baseline_p95 × total_ejecuciones`. Cuanto más alto, mayor retorno al optimizar.

| # | Endpoint | Impact Score | P95 actual | Baseline global |
|---|---|---|---|---|
| 1 | Get investment metrics by ID | 182.310 | 7059 ms | 6752 ms |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 48.705 | 2117 ms | 1804 ms |
| 3 | Appraise market value | 47.573 | 1980 ms | 1762 ms |
| 4 | Bond coupons by UUID | 19.715 | 247 ms | 730 ms |
| 5 | Get investment irr sensitivity by ID | 18.602 | 762 ms | 689 ms |

## Tendencia — Últimas 5 corridas

| Fecha | avg P95 | Baseline global |
|---|---|---|
| 2026-04-03 | 550 ms | 475 ms |
| 2026-04-04 | 932 ms | 478 ms |
| 2026-04-06 | 644 ms | 497 ms |
| 2026-04-07 | 523 ms | 503 ms |
| 2026-04-07 | 509 ms | 504 ms |

---

*Generado automáticamente por [pepper-API-testing](https://github.com/Mercap/pepper-API-testing) · 2026-04-07 15:01 UTC*
