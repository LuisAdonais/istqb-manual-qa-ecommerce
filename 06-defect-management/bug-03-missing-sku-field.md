
# Defect Report — BUG-03

| Atributo     | Detalle                                                      |
| :---         | :---                                                         |
| **Ubicación** | `06-defect-management/bug-03-missing-sku-field.md`          |
| **ID**       | **`BUG-03`**                                                 |
| **Título**   | Ausencia del campo SKU en la ficha de detalle del producto   |
| **Estado**   | 🔴 Open                                                      |
| **Fecha**    | 2026-05-05                                                   |
| **Ref. TX**  | **`TX-01.08`**                                               |
| **Ref. TC**  | **`TC-04`**                                                  |
| **Ref. REQ** | **`REQ-03`** / **`AC-04`**                                   |
| **Severidad**| Medium                                                       |
| **Prioridad**| Medium                                                       |
| **QA Owner** | Luis Adonais Malave Gamardo                                  |

---

## 1. Descripción

Durante la verificación de la ficha técnica del producto `"Build your own cheap computer"`, el campo **SKU** no es visible en la interfaz. Su ausencia incumple directamente **`AC-04`**, que requiere que Nombre, Precio, SKU e input `Qty.` sean visibles simultáneamente en la vista de detalle.

---

## 2. Pasos para reproducir

1. Navegar a `Computers > Desktops`
2. Seleccionar el producto `Build your own cheap computer`
3. Ingresar a la vista de detalle
4. Inspeccionar la región superior de la ficha técnica junto al nombre y disponibilidad del producto

---

## 3. Resultados

|               | Detalle                                                                     |
| :---          | :---                                                                        |
| **Esperado**  | El campo SKU es visible junto a Nombre, Precio e input `Qty.`               |
| **Actual**    | El campo SKU no aparece en ninguna sección de la ficha de detalle           |

---

## 4. Clasificación

| Atributo      | Valor                                                                             |
| :---          | :---                                                                              |
| **Severidad** | Medium — falla de integridad de datos; afecta la trazabilidad de inventario para el usuario final |
| **Prioridad** | Medium — debe resolverse antes del cierre del ciclo de estabilización             |
| **Entorno**   | Windows 10 Pro / Firefox 150.0.1                                                  |

---

## 5. Evidencia

[2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png)

- Recuadros verdes: Nombre, Precio, `Qty.` — presentes y correctos
- Recuadro rojo: campo SKU ausente

**Jira:** [Ver issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-03_Jira-Issue.png)

---

## 6. Trazabilidad

| **`TX`**      | **`TC`**   | **`REQ`** / **`AC`**      | Veredicto | **`BUG`**    |
| :---          | :---       | :---                      | :---      | :---         |
| **`TX-01.08`**| **`TC-04`**| **`REQ-03`** / **`AC-04`**| ❌ FAIL   | **`BUG-03`** |
