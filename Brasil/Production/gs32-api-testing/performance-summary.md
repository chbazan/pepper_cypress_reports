### Estado de Performance
**Ambiente:** Production — Brasil — V10.3.65 | **Run ID:** 202604071902 | **Fecha:** 2026-04-07T19:02:18Z

| Corrida | avg P95 (ms) | Baseline (ms) | Delta | Tendencia |
|---------|-------------|---------------|-------|-----------|
| -4      | 724         | 491           | +47.5% | —        |
| -3      | 339         | 496           | -31.7% | ↓        |
| -2      | 378         | 500           | -24.4% | ↑        |
| -1      | 395         | 504           | -21.6% | ↑        |
| **Actual** | **509**  | **504**       | **+1.0%** | **↑** |

El avg P95 tocó mínimo en -3 (339ms) y lleva 3 corridas consecutivas al alza, llegando a superar el baseline global por primera vez en esta serie. La corrida en -4 (724ms) pudo haber sido un spike puntual, pero la tendencia ascendente actual requiere atención.

---

### Semáforo de Endpoints

#### 🔴 Críticos (status_level = 2) — 19 endpoints

| Endpoint | P95 (ms) | Baseline (ms) | Delta Global | Delta Versión | Regresión |
|----------|----------|---------------|-------------|---------------|-----------|
| All bonds - for issuer | 2 951 | 371 | +695.27% | +675.25% | +1017.80% |
| Get all curencies - validate each self link | 420 | 78 | +438.70% | +469.49% | +757.14% |
| All bonds - deault parameters | 853 | 164 | +419.38% | +410.93% | +328.64% |
| Bond payment summary by UUID | 735 | 147 | +399.55% | +352.45% | +775.00% |
| All bonds - start & limit parameters | 751 | 174 | +332.02% | +367.91% | +541.88% |
| Only shortName parameter | 740 | 173 | +327.42% | +313.64% | +687.23% |
| Get all bond laws - validate each self link | 366 | 90 | +305.91% | +293.55% | +565.45% |
| Get all instrument issuers | 455 | 116 | +290.73% | +308.44% | +435.29% |
| Bond coupons by UUID | 770 | 203 | +280.21% | +262.61% | +387.34% |
| Bond by UUID | 459 | 136 | +238.08% | +247.20% | +393.55% |
| Bond identifiers by UUID | 486 | 146 | +232.95% | +228.82% | +295.12% |
| Bond issue conditions by UUID | 472 | 141 | +233.73% | +238.23% | +237.14% |
| Get all debt types - validate each self link | 294 | 88 | +233.71% | +230.52% | +406.90% |
| Get payment forecasts | 560 | 170 | +229.22% | +252.42% | +247.83% |
| Appraise market value | 4 015 | 1 773 | +126.42% | +125.15% | +130.88% |
| Create an investment | 316 | 137 | +131.11% | +133.56% | +295.00% |
| Get one bond cashflow - dateInterval from and to | 446 | 200 | +123.48% | +148.33% | +223.19% |
| Get one bond cashflow - only dateInterval from | 418 | 178 | +134.20% | +149.78% | +175.00% |
| Get all exchange schemes | 353 | 169 | +109.41% | +137.39% | +620.41% |

#### 🟡 Advertencia (status_level = 1) — 7 endpoints

| Endpoint | P95 (ms) | Baseline (ms) | Delta Global | Delta Versión | Regresión |
|----------|----------|---------------|-------------|---------------|-----------|
| Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 2 713 | 1 817 | +49.27% | +43.61% | +52.93% |
| Get valuation schemes by UUID | 138 | 45 | +204.64% | +184.24% | +206.67% |
| Get exchange scheme by UUID | 122 | 41 | +197.06% | +189.79% | +177.27% |
| Get markets by UUID | 125 | 44 | +184.09% | +189.02% | +190.70% |
| Get investment by ID | 337 | 144 | +134.20% | +132.49% | +117.42% |
| Get all mutual fund types | 286 | 183 | +56.40% | +61.04% | +62.50% |
| Get all markets | 287 | 235 | +22.06% | +32.47% | +431.48% |

---

### Outliers Detectados

| Endpoint | P95 (ms) | Baseline (ms) | Ratio | Nota |
|----------|----------|---------------|-------|------|
| All bonds - for issuer | 2 951 | 371 | 7.95× | |
| Get all curencies - validate each self link | 420 | 78 | 5.39× | |
| All bonds - deault parameters | 853 | 164 | 5.19× | |
| Bond payment summary by UUID | 735 | 147 | 5.00× | |
| All bonds - start & limit parameters | 751 | 174 | 4.32× | |
| Only shortName parameter | 740 | 173 | 4.27× | |
| Get all bond laws - validate each self link | 366 | 90 | 4.06× | |
| Get all instrument issuers | 455 | 116 | 3.91× | |
| Bond coupons by UUID | 770 | 203 | 3.80× | 🚨 REINCIDENTE (5 ocurrencias) |
| Bond by UUID | 459 | 136 | 3.38× | |
| Bond issue conditions by UUID | 472 | 141 | 3.34× | |
| Get all debt types - validate each self link | 294 | 88 | 3.34× | |
| Bond identifiers by UUID | 486 | 146 | 3.33× | |
| Get payment forecasts | 560 | 170 | 3.29× | |
| Get valuation schemes by UUID | 138 | 45 | 3.05× | |

> Endpoints reincidentes con 3+ ocurrencias históricas pero **no** presentes en outliers de esta corrida: **🚨 Get one bond cashflow - only dateInterval from** (3 ocurrencias) · **🚨 Get investment irr sensitivity by ID** (3 ocurrencias).

---

### Top 10 Más Lentos

| # | Endpoint | P95 (ms) | Payload (KB) |
|---|----------|----------|-------------|
| 1 | Get investment metrics by ID | 7 346 | 1.03 |
| 2 | Appraise market value | 4 015 | 0.63 |
| 3 | All bonds - for issuer | 2 951 | 0.58 |
| 4 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 2 713 | 4.92 |
| 5 | All bonds - deault parameters | 853 | 6.40 |
| 6 | Bond coupons by UUID | 770 | 7.89 |
| 7 | Get investment irr sensitivity by ID | 764 | 1.64 |
| 8 | All bonds - start & limit parameters | 751 | 3.39 |
| 9 | Only shortName parameter | 740 | 0.68 |
| 10 | Bond payment summary by UUID | 735 | 0.41 |

---

### Impact Ranking (Top 5)

| # | Endpoint | Impact Score | P95 (ms) | Baseline (ms) |
|---|----------|-------------|----------|---------------|
| 1 | Get investment metrics by ID | 207 339 | 7 346 | 6 688 |
| 2 | Filter by debt-type, issueCurrency, paymentCurrency, issuer & law | 56 341 | 2 713 | 1 817 |
| 3 | Appraise market value | 54 970 | 4 015 | 1 773 |
| 4 | Get investment irr sensitivity by ID | 21 636 | 764 | 698 |
| 5 | Get irrs - one bond | 20 616 | 720 | 665 |

---

### Conclusiones Accionables

- **Escalar inmediatamente:** El dominio Bonds presenta una degradación sistémica masiva — 9 de sus endpoints están en rojo con regresiones de entre +237% y **+1017%** respecto a la corrida anterior. `All bonds - for issuer` pasó de baseline 371ms a 2 951ms (+695% global, +1017% regresión), y `Bond coupons by UUID` acumula 5 apariciones como outlier reincidente. La simultaneidad y magnitud de la degradación en todos los endpoints del dominio apunta a un problema de infraestructura subyacente (base de datos, caché, índices) que requiere escalado urgente al equipo de backend Brasil.

- **Investigar:** Los tres endpoints de "validate each self link" (`Get all curencies` 5.39×, `Get all bond laws` 4.06×, `Get all debt types` 3.34×) muestran ratios de outlier desproporcionados frente a endpoints similares sin validación de links. El patrón sugiere un problema de N+1 requests o timeouts en la resolución de self-links dentro del response. Correlacionar con logs de red del lado servidor durante la ventana 19:00–19:05 UTC del 2026-04-07 para confirmar si son llamadas encadenadas o latencia de resolución DNS.

- **Optimizar:** `Get investment metrics by ID` lidera el Impact Ranking con score 207 339 (≈3.7× el segundo puesto) y P95 de 7 346ms, superando en +9.8% su propio baseline de 6 688ms. Dado su alto volumen de ejecuciones, una optimización moderada de 10–15% en este endpoint reduciría más el impacto acumulado total que resolver cualquier otro endpoint del ranking. Revisar su query plan, índices y si admite paginación o proyección de campos para reducir trabajo computacional.
