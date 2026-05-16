
# Defect Reports Index

| Atributo     | Detalle                                  |
| :---         | :---                                     |
| **Ubicación** | `06-defect-management/defect-reports.md` |
| **Proyecto** | Tricentis Demo Web Shop                  |
| **Versión**  | 1.1                                      |
| **Fase STLC** | Defect Management                       |
| **Estado**   | 🔴 Defectos activos                      |
| **QA Owner** | Luis Adonais Malave Gamardo              |

---
## 1. Inventario de defectos

| **`BUG`** | Título | **`TX`** | **`TC`** | Severidad | Estado | Archivo | Jira |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | Incoherencia en secuencia de precios y nomenclatura en resultados de búsqueda | **`TX-01.05`** | **`TC-01`** | Low | 🔴 Open |[bug-01-price-incoherence.md](./bug-01-price-incoherence.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-01_Jira-Issue.png) |
| **`BUG-02`** | Inconsistencia de capitalización en menú lateral de categorías | **`TX-01.07`** | **`TC-03`** | Low | 🔴 Open | [bug-02-capitalization-inconsistency.md](./bug-02-capitalization-inconsistency.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-02_Jira-Issue.png) |
| **`BUG-03`** | Ausencia del campo SKU en la ficha de detalle del producto | **`TX-01.08`** | **`TC-04`** | Medium | 🔴 Open | [bug-03-missing-sku-field.md](./bug-03-missing-sku-field.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-03_Jira-Issue.png) |

---

## 2. Métricas

| Métrica | Valor |
| :--- | :--- |
| **Total defectos** | 3 |
| **Open** | 3 |
| **Closed / Fixed** | 0 |
| **Critical** | 0 |
| **High** | 0 |
| **Medium** | 1 — **`BUG-03`** |
| **Low** | 2 — **`BUG-01`**, **`BUG-02`** |
| **Decisión de continuación** | **`EDN-01`** — Autorizada (2026-05-04) |

---

## 3. Trazabilidad

| **`BUG`** | **`TX`** | **`TS`** | Impacto en **`TS-02`** / **`TS-03`** | Plan |
| :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | **`TS-01`** | Ninguno | Pendiente próximo ciclo |
| **`BUG-02`** | **`TX-01.07`** | **`TS-01`** | Ninguno | Pendiente próximo ciclo |
| **`BUG-03`** | **`TX-01.08`** | **`TS-01`** | Ninguno — continuación autorizada por **`EDN-01`** | Pendiente antes del cierre de estabilización |
