
# Defect Report — BUG-02

| Atributo     | Detalle                                                         |
| :---         | :---                                                            |
| **Ubicación** | `06-defect-management/bug-02-capitalization-inconsistency.md`  |
| **ID**       | **`BUG-02`**                                                    |
| **Título**   | Inconsistencia de capitalización en menú lateral de categorías  |
| **Estado**   | 🔴 Open                                                         |
| **Fecha**    | 2026-05-05                                                      |
| **Ref. TX**  | **`TX-01.07`**                                                  |
| **Ref. TC**  | **`TC-03`**                                                     |
| **Ref. REQ** | **`REQ-02`** / **`AC-03`**                                      |
| **Severidad**| Low                                                             |
| **Prioridad**| Low                                                             |
| **QA Owner** | Luis Adonais Malave Gamardo                                     |

---

## 1. Descripción

Durante la validación del menú lateral de categorías, la etiqueta `Digital downloads` usa Sentence Case en lugar del estándar Title Case aplicado en el resto del menú. La inconsistencia es cosmética y no impide la navegación.

---

## 2. Pasos para reproducir

1. Navegar a `https://demowebshop.tricentis.com/`
2. Localizar el menú lateral bajo la sección `Categories`
3. Comparar la capitalización de `Digital downloads` con las categorías adyacentes (`Apparel & Shoes`, `Gift Cards`)

---

## 3. Resultados

|             | Detalle                                                                             |
| :---        | :---                                                                                |
| **Esperado**| Todas las etiquetas en Title Case. Valor esperado: `Digital Downloads`              |
| **Actual**  | La categoría aparece como `Digital downloads` — segunda palabra en minúscula        |

---

## 4. Clasificación

| Atributo      | Valor                                                                 |
| :---          | :---                                                                  |
| **Severidad** | Low — defecto cosmético; no impide navegación ni flujo funcional      |
| **Prioridad** | Low                                                                   |
| **Entorno**   | Windows 10 Pro / Firefox 150.0.1                                     |

---

## 5. Evidencia

[2026-05-05_TX-01.07_Category_Nav_BUG-02.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.07_Category_Nav_BUG-02.png)

**Jira:** [Ver issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-02_Jira-Issue.png)

- Recuadros verdes: `Apparel & Shoes`, `Gift Cards` — Title Case correcto
- Recuadro rojo: `Digital downloads` — Sentence Case incorrecto

---

## 6. Trazabilidad

| **`TX`**      | **`TC`**   | **`REQ`** / **`AC`**        | Veredicto | **`BUG`**    |
| :---          | :---       | :---                        | :---      | :---         |
| **`TX-01.07`**| **`TC-03`**| **`REQ-02`** / **`AC-03`**  | ❌ FAIL   | **`BUG-02`** |
