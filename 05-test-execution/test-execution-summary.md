# Test Execution Summary

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/test-execution-summary.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 4.0 |
| **Fase STLC** | Test Execution — Test Progress Reporting |
| **Periodo** | 2026-05-04 — 2026-05-05 |
| **Estado** | ✅ Completado |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Objetivo

Consolidar los resultados del ciclo de pruebas funcionales sobre el sistema Tricentis Demo Web Shop. El ciclo cubre 12 ciclos de ejecución (**`TX`**) distribuidos en 3 suites (**`TS-01`**, **`TS-02`**, **`TS-03`**), validando los requisitos **`REQ-01`** a **`REQ-07`**.

---

## 2. Resultados por suite

| **`TS`** | Descripción | **`TX`** total | Ejecutados | PASS | FAIL | Estado final |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`TS-01`** | Smoke — Registro, Login, Búsqueda, Catálogo | 8 | 8 | 5 | 3 | 5P / 3F |
| **`TS-02`** | Regression — Lógica de carrito (BVA) | 3 | 3 | 3 | 0 | 3P / 0F |
| **`TS-03`** | E2E — Checkout completo | 1 | 1 | 1 | 0 | 1P / 0F |
| **TOTAL** | — | **12** | **12** | **9** | **3** | **75% Pass Rate** |

> [!NOTE]
> 
> La continuación de **`TS-02`** y **`TS-03`** ante los fallos de **`TS-01`** fue autorizada mediante **`EDN-01`** (2026-05-04). Ningún defecto activo tenía severidad Critical o High.

---

## 3. Métricas de calidad

| Métrica | Fórmula | Resultado |
| :--- | :--- | :--- |
| **Completitud** | TX Ejecutados / TX Planificados × 100 | **100% (12/12)** |
| **Pass Rate global** | PASS / TX Ejecutados × 100 | **75% (9/12)** |
| **Pass Rate E2E** | PASS TS-03 / TX TS-03 × 100 | **100% (1/1)** |
| **Densidad de defectos** | BUGs / TX | **0.25 (3/12)** |

---

## 4. Defectos activos al cierre

| **`BUG`** | **`TX`** | Severidad | Estado |
| :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | Low | 🔴 Open — pendiente próximo ciclo |
| **`BUG-02`** | **`TX-01.07`** | Low | 🔴 Open — pendiente próximo ciclo |
| **`BUG-03`** | **`TX-01.08`** | Medium | 🔴 Open — controlado según **`EDN-01`** |

---

## 5. Referencias de trazabilidad

| **`TS`** | **`TX`** cubiertos | Log (**`TL`**) | Estado |
| :--- | :--- | :--- | :--- |
| **`TS-01`** | **`TX-01.01`** a **`TX-01.08`** | [tl-01-smoke-log.md](./test-logs/tl-01-smoke-log.md) | 5P / 3F |
| **`TS-02`** | **`TX-02.01`** a **`TX-02.03`** | [tl-02-regression-log.md](./test-logs/tl-02-regression-log.md) | 3P / 0F |
| **`TS-03`** | **`TX-03.01`** | [tl-03-e2e-log.md](./test-logs/tl-03-e2e-log.md) | 1P / 0F |
