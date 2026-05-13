
# Test Execution Tracker

| Atributo   | Detalle                                     |
| :---       | :---                                        |
| **Ubicación** | `05-test-execution/test-execution-tracker.md` |
| **Proyecto**  | Tricentis Demo Web Shop                   |
| **Versión**   | 4.0                                      |
| **Fase STLC** | Test Execution — Test Monitoring & Control |
| **Estado**    | ✅ Completado                             |
| **QA Owner**  | Luis Adonais Malave Gamardo              |

---

## 1. Dashboard

| **`TS`**        | Descripción           | Total **`TX`** | Ejecutados | PASS | FAIL | Avance    |
| :---            | :---                  | :---          | :---       | :--- | :--- | :---      |
| **`TS-01`**     | Smoke Test Suite      | 8             | 8          | 5    | 3    | 100%      |
| **`TS-02`**     | Full Regression Suite | 3             | 3          | 3    | 0    | 100%      |
| **`TS-03`**     | E2E Checkout Suite    | 1             | 1          | 1    | 0    | 100%      |
| **TOTAL**       | —                     | **12**        | **12**     | **9**| **3**| **100%**  |

---

## 2. Registro detallado

| **`TX`**        | **`TL`**  | **`TC`**  | Acción verificada                           | Fecha       | Estado      |
| :---            | :---      | :---      | :---                                        | :---        | :---        |
| **`TX-01.01`**  | **`TL-01`** | **`TC-06`** | Registro con datos válidos                | 2026-05-04  | ✅ PASS     |
| **`TX-01.02`**  | **`TL-01`** | **`TC-07`** | Mensaje de éxito en registro               | 2026-05-04  | ✅ PASS     |
| **`TX-01.03`**  | **`TL-01`** | **`TC-08`** | Login con credenciales inválidas           | 2026-05-04  | ✅ PASS     |
| **`TX-01.04`**  | **`TL-01`** | **`TC-11`** | Login con credenciales válidas             | 2026-05-04  | ✅ PASS     |
| **`TX-01.05`**  | **`TL-01`** | **`TC-01`** | Búsqueda exacta — **`BUG-01`**             | 2026-05-05  | ❌ FAIL     |
| **`TX-01.06`**  | **`TL-01`** | **`TC-02`** | Búsqueda sin resultados                    | 2026-05-05  | ✅ PASS     |
| **`TX-01.07`**  | **`TL-01`** | **`TC-03`** | Navegación por subcategoría — **`BUG-02`** | 2026-05-05  | ❌ FAIL     |
| **`TX-01.08`**  | **`TL-01`** | **`TC-04`** | Atributos en ficha de producto — **`BUG-03`** | 2026-05-05 | ❌ FAIL  |
| **`TX-02.01`**  | **`TL-02`** | **`TC-05`** | Recálculo Sub-Total (Qty = 2)              | 2026-05-05  | ✅ PASS     |
| **`TX-02.02`**  | **`TL-02`** | **`TC-10`** | Remoción total carrito (Qty = 0)           | 2026-05-05  | ✅ PASS     |
| **`TX-02.03`**  | **`TL-02`** | **`TC-05`** | Remoción parcial carrito (Qty = 0, 2 ítems)| 2026-05-05  | ✅ PASS     |
| **`TX-03.01`**  | **`TL-03`** | **`TC-09`** | Checkout completo — orden generada          | 2026-05-05 | ✅ PASS     |

---

## 3. Métricas

| Métrica                | Fórmula                              | Resultado          |
| :---                   | :---                                 | :---               |
| **Pass Rate global**   | PASS / Ejecutados × 100              | **75% (9/12)**     |
| **Pass Rate E2E**      | PASS TS-03 / TX TS-03 × 100          | **100% (1/1)**     |
| **Densidad de defectos** | BUGs / TX                         | **0.25 (3/12)**    |
| **Completitud**        | Ejecutados / Planificados × 100      | **100% (12/12)**   |

---

## 4. Defectos

| **`BUG`**     | **`TX`**       | **`TC`**    | Severidad | Estado     |
| :---          | :---           | :---        | :---      | :---       |
| **`BUG-01`**  | **`TX-01.05`** | **`TC-01`** | Medium    | 🔴 Open    |
| **`BUG-02`**  | **`TX-01.07`** | **`TC-03`** | Low       | 🔴 Open    |
| **`BUG-03`**  | **`TX-01.08`** | **`TC-04`** | Medium    | 🔴 Open    |
