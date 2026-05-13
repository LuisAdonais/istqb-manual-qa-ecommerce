
# Test Summary Report

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `07-test-completion/test-summary-report.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Completion — ISO 29119-3 |
| **Periodo** | 2026-05-04 — 2026-05-05 |
| **Estado** | ✅ Completado |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Resumen ejecutivo

Cierre formal del ciclo de pruebas funcionales sobre el sistema Tricentis Demo Web Shop. Se ejecutaron 12 ciclos de prueba (**`TX`**) en 3 suites (**`TS-01`**, **`TS-02`**, **`TS-03`**), cubriendo la totalidad de los requisitos funcionales del alcance definido (**`REQ-01`** a **`REQ-07`**).

El flujo transaccional crítico (Checkout E2E) fue completado con **100% de Pass Rate**. Los 3 defectos detectados son de severidad Low y Medium, no bloquean ningún flujo de negocio y permanecen abiertos para el siguiente ciclo de corrección.

---

## 2. Alcance del ciclo

| Módulo | **`REQ`** | **`TCND`** verificadas | **`TC`** ejecutados |
| :--- | :--- | :--- | :--- |
| Búsqueda | **`REQ-01`** | **`TCND-01`**, **`TCND-02`** | **`TC-01`**, **`TC-02`** |
| Catálogo | **`REQ-02`** | **`TCND-03`** | **`TC-03`** |
| Producto | **`REQ-03`** | **`TCND-04`** | **`TC-04`** |
| Carrito | **`REQ-04`** | **`TCND-05`** | **`TC-05`**, **`TC-10`** |
| Registro | **`REQ-05`** | **`TCND-06`**, **`TCND-07`** | **`TC-06`**, **`TC-07`** |
| Login | **`REQ-06`** | **`TCND-08`**, **`TCND-10`** | **`TC-08`**, **`TC-11`** |
| Checkout E2E | **`REQ-07`** | **`TCND-09`** | **`TC-09`** |

---

## 3. Resultados por suite

| **`TS`** | Tipo | **`TX`** Plan. | Ejecutados | PASS | FAIL | Pass Rate | Log |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`TS-01`** | Smoke | 8 | 8 | 5 | 3 | 62.5% | [TL-01](../05-test-execution/test-logs/tl-01-smoke-log.md) |
| **`TS-02`** | Regression | 3 | 3 | 3 | 0 | 100% | [TL-02](../05-test-execution/test-logs/tl-02-regression-log.md) |
| **`TS-03`** | E2E | 1 | 1 | 1 | 0 | 100% | [TL-03](../05-test-execution/test-logs/tl-03-e2e-log.md) |
| **TOTAL** | — | **12** | **12** | **9** | **3** | **75%** | — |

> Continuación de **`TS-02`** y **`TS-03`** autorizada mediante [EDN-01](../05-test-execution/edn-01-execution-decision-note.md) (2026-05-04).

---

## 4. Defectos detectados

| **`BUG`** | Título | **`TX`** | **`TC`** | **`REQ`** | Severidad | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| [**`BUG-01`**](../06-defect-management/bug-01-price-incoherence.md) | Incoherencia en secuencia de precios y nomenclatura | **`TX-01.05`** | **`TC-01`** | **`REQ-01`** | Low | 🔴 Open |
| [**`BUG-02`**](../06-defect-management/bug-02-capitalization-inconsistency.md) | Inconsistencia de capitalización en menú lateral | **`TX-01.07`** | **`TC-03`** | **`REQ-02`** | Low | 🔴 Open |
| [**`BUG-03`**](../06-defect-management/bug-03-missing-sku-field.md) | Ausencia del campo SKU en ficha de producto | **`TX-01.08`** | **`TC-04`** | **`REQ-03`** | Medium | 🔴 Open |

---

## 5. Métricas de calidad

| Métrica | Fórmula | Resultado |
| :--- | :--- | :--- |
| **Completitud** | TX Ejecutados / TX Planificados × 100 | **100% (12/12)** |
| **Pass Rate global** | PASS / TX Ejecutados × 100 | **75% (9/12)** |
| **Pass Rate E2E** | PASS TS-03 / TX TS-03 × 100 | **100% (1/1)** ✅ |
| **Densidad de defectos** | BUGs / TX | **0.25 (3/12)** |
| **Defectos Critical/High al cierre** | Conteo directo | **0** ✅ |
| **Cobertura de requisitos** | REQ con ≥1 TX PASS / REQ totales × 100 | **100% (7/7)** ✅ |

---

## 6. Criterios de salida

| Criterio | Umbral | Resultado | Estado |
| :--- | :--- | :--- | :--- |
| Completitud de ejecución | 100% TX ejecutados | 12/12 | ✅ |
| Pass Rate E2E | ≥ 90% en **`TS-03`** | 100% | ✅ |
| Defectos Critical/High al cierre | 0 | 0 | ✅ |
| Trazabilidad completa (Zero Orphans) | Verificada | Auditada | ✅ |
| Defectos Medium/Low | Documentados y trazados | 3 BUGs abiertos | ⚠️ Pendiente resolución |

**Veredicto:** El ciclo cumple los criterios de salida definidos. Los defectos residuales están documentados, trazados y no bloquean la funcionalidad transaccional crítica.

---

## 7. Riesgos residuales

| **`BUG`** | Módulo | Riesgo de negocio | Plan |
| :--- | :--- | :--- | :--- |
| **`BUG-01`** | Búsqueda | Bajo — resultados con precios inconsistentes. No impide la compra | Escalar a desarrollo en el próximo sprint |
| **`BUG-02`** | Catálogo | Bajo — inconsistencia cosmética en el menú. No impide la navegación | Escalar a front-end como corrección de estilo |
| **`BUG-03`** | Producto | Medio — ausencia de SKU afecta trazabilidad de inventario. Confirmar si el dato existe en BD antes del re-test | Escalar a desarrollo con prioridad Media |

---

## 8. Trazabilidad de artefactos

| Fase | Artefactos | Estado |
| :--- | :--- | :--- |
| Test Analysis | `requirements.md`, `test-basis-evaluation.md`, `test-conditions.md` | ✅ Approved |
| Test Design | `test-cases.md`, `test-data-requirements.md` | ✅ Approved |
| Test Implementation | `test-procedures.md`, `test-suites.md`, `test-environment-setup.md` | ✅ Approved |
| Test Execution | `TL-01`, `TL-02`, `TL-03`, `test-execution-tracker.md`, `test-execution-summary.md`, `EDN-01` | ✅ Completado |
| Defect Management | `BUG-01`, `BUG-02`, `BUG-03` | 🔴 Open |
| Test Completion | `test-summary-report.md`, `lessons-learned.md` | ✅ Completado |
