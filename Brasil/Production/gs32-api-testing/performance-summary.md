I now have all the data needed for a comprehensive analysis. Here's the report:

---

## Análisis de Métricas de Performance — 2026-04-07

### Ambientes Activos (manifest.csv)

| Ambiente | País | Versión |
|---|---|---|
| Production | Argentina | V10.2.91 |
| Production | Brasil | V10.3.65 |
| Staging | Brasil | V10.3.65 |

---

### Estado de Performance por Ambiente

#### 🟡 Argentina — Production — V10.2.91

| Métrica | Valor |
|---|---|
| P95 global hoy (12:18) | **449ms** |
| Baseline global consolidado | 410ms |
| Delta vs baseline | **+9.5%** |
| Endpoint más lento hoy | Get investment metrics by ID (4589ms) |

#### 🔴 Brasil — Production — V10.3.65

| Métrica | Valor |
|---|---|
| P95 global hoy (último run 15:29) | **395ms** |
| Baseline global consolidado | 504ms |
| Delta vs baseline | -22% (recovering) |
| Baseline de versión | 532ms ↑ (inflado por histórico degradado) |
| Endpoint más lento | Get investment metrics by ID (6252ms) |

> Brasil tuvo 3 ejecuciones hoy (12:37, 15:01, 15:29). El avg_p95 bajó de 523 → 509 → 395ms, lo cual sugiere recuperación, pero el baseline de versión en 532ms indica degradación acumulada.

#### ⚪ Staging Brasil — V10.3.65

Solo 2 ejecuciones históricas (Mar 31): 526ms y 221ms. Sin suficientes datos para tendencia confiable.

---

### Tendencia Global — Últimas 5 Ejecuciones

#### Argentina Production

| Fecha | avg_p95 | Baseline | Delta |
|---|---|---|---|
| 03-Apr | 403ms | 404ms | 🟢 -0.2% |
| 04-Apr | 406ms | 404ms | 🟢 +0.5% |
| 05-Apr | 481ms | 404ms | 🟡 **+19%** |
| 06-Apr | 434ms | 408ms | 🟡 +6.4% |
| 07-Apr | 449ms | 410ms | 🟡 +9.5% |

**Tendencia: degradación gradual.** El baseline mismo viene subiendo (311ms a 410ms = +32% en ~2 semanas).

#### Brasil Production

| Fecha | avg_p95 | Baseline | Delta |
|---|---|---|---|
| 03-Apr | 550ms | 475ms | 🟡 +16% |
| 04-Apr | **932ms** | 478ms | 🔴 **+95% SPIKE** |
| 06-Apr | 644ms | 497ms | 🔴 +30% |
| 07-Apr 12:37 | 523ms | 503ms | 🟡 +4% |
| 07-Apr 15:29 | 395ms | 504ms | 🟢 -22% |

**Tendencia: volátil con spike severo el 04-Apr, recuperándose hoy.** El baseline de versión (532ms) vs baseline global (504ms) revela que V10.3.65 en general corre más lento que el promedio histórico.

---

### 🚦 Semáforo de Endpoints — Run Hoy

#### Argentina (run 202604071218)

| Estado | Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|---|
| 🔴 | Get investment metrics by ID | 4589ms | 1393ms | **+229%** | +59% |
| 🟡 | Get investment irr sensitivity by ID | 1613ms | 537ms | +201% | +37% |
| 🟡 | Get tradable securities - only mandatory | 913ms | 510ms | +79% | +21% |
| 🟡 | Get tradable securities - only market | 695ms | 441ms | +58% | +4% |
| 🟡 | Get tradable securities - only query | 651ms | 414ms | +57% | -1% |
| 🟡 | Get tradable security by UUID | 155ms | 62ms | +149% | +50% |
| 🟡 | Get all stocks | 155ms | 92ms | +68% | +104% |
| 🟡 | Get all exchange schemes | 123ms | 76ms | +63% | +92% |

#### Brasil (run 202604071237 — 12:37)

| Estado | Endpoint | P95 actual | Baseline global | Delta global | Regression |
|---|---|---|---|---|---|
| 🔴 | Bond coupons by UUID | 2183ms | 208ms | **+949%** | +2326% |
| 🟡 | Get all exchange schemes | 287ms | 178ms | +61% | +159% |
| 🟡 | Get all valuation schemes | 267ms | 175ms | +53% | +175% |

> `Get investment metrics by ID` en Brasil tiene p95=6252ms pero baseline=6772ms → delta=-7.68% → status_level=0. Este endpoint es estructuralmente lento (baseline inflado por el histórico).

---

### Outliers Detectados (histórico relevante)

#### Brasil Production — Outliers recurrentes

| Endpoint | Ocurrencias | Último evento | P95 pico | Ratio máx |
|---|---|---|---|---|
| **Bond coupons by UUID** | **4 veces** (Mar 23, Apr 2, Apr 4, Apr 7) | **Hoy** | 2183ms | 14.79x |
| Get one bond cashflow - only dateInterval from | 3 veces | Apr 4 | 5866ms | **27.9x** |
| Get tradable security metrics | 2 veces | Apr 4 | 4321ms | **21.86x** |
| Get investment irr sensitivity by ID | 3 veces | Apr 4 | 2635ms | 5x |

#### Argentina Production — Outliers recurrentes

| Endpoint | Ocurrencias | Último evento | P95 pico | Ratio máx |
|---|---|---|---|---|
| **Get investment metrics by ID** | 2 veces | **Hoy** | 4589ms | 3.29x |
| Get investment irr sensitivity by ID | 2 veces | Hoy | 1613ms | 3.54x |
| Get all bond groups | 3 veces | Apr 4 | **19676ms** | **103.39x** |
| Get all markets | 2 veces | Apr 2 | 10657ms | 79.66x |
| Get all instrument issuers | 2 veces | Apr 2 | 2347ms | 13.21x |

---

### Impact Ranking — Top 5 por Ambiente

#### Argentina (run 202604071218)

| # | Endpoint | Impact Score | P95 actual | Baseline |
|---|---|---|---|---|
| 1 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | **60,959** | 2660ms | 2903ms |
| 2 | Get parities | 32,981 | 1355ms | 1571ms |
| 3 | Get irrs - one bond | 32,873 | 1461ms | 1565ms |
| 4 | Appraise market value | 30,598 | 1564ms | 1457ms |
| 5 | **Get investment metrics by ID** 🔴 | 29,249 | **4589ms** | 1393ms |

#### Brasil (run 202604071237)

| # | Endpoint | Impact Score | P95 actual | Baseline |
|---|---|---|---|---|
| 1 | **Get investment metrics by ID** | **176,078** | 6252ms | 6772ms |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 46,802 | 1899ms | 1800ms |
| 3 | Appraise market value | 45,706 | 1863ms | 1758ms |
| 4 | Get investment irr sensitivity by ID | 17,698 | 879ms | 681ms |
| 5 | Get irrs - one bond | 17,609 | 592ms | 677ms |

> `Get investment metrics by ID` en Brasil domina el impact_score con 176k — 3.8x el segundo puesto. El baseline de 6772ms indica que este endpoint ha sido históricamente lento, acumulando peso.

---

### Conclusiones Accionables

- **Escalar a backend: `Get investment metrics by ID` en Argentina y Brasil.** En Argentina disparó 4589ms hoy (+229% vs baseline 1393ms) — outlier de la corrida actual. En Brasil el baseline es 6772ms (estructuralmente lento), con el mayor impact_score del sistema (176k). El mismo endpoint en ambos países sugiere un problema en la capa de cálculo de métricas de inversiones; merece investigación de índices o consultas DB subyacentes.

- **Investigar `Bond coupons by UUID` en Brasil — outlier crónico.** Aparece en 4 runs distintos (incluyendo hoy) con ratios de 9-15x baseline. No es un evento puntual: es un patrón. El endpoint tiene un baseline bajo (208ms) pero escala a 2100ms+ en forma recurrente. Probable causa: volumen de datos en ciertas llamadas o cache miss intermitente.

- **Atención a la tendencia de Argentina.** El baseline global consolidado subió de 311ms (26-Mar) a 410ms (hoy) = +32% en ~12 días. Además 8 endpoints están en amarillo o rojo en la última corrida. Esto no es un spike puntual sino degradación sistemática de V10.2.91, que se aceleró desde el 5-Apr (481ms). Correlacionar con deploys o cambios de infra en esa ventana.
