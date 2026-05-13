# Defect Report — BUG-01


| Atributo      | Detalle                                                                       |
| ------------- | ----------------------------------------------------------------------------- |
| **Ubicación** | `06-defect-management/bug-01-price-incoherence.md`                            |
| **ID**        | `**BUG-01`**                                                                  |
| **Título**    | Incoherencia en secuencia de precios y nomenclatura en resultados de búsqueda |
| **Estado**    | 🔴 Open                                                                       |
| **Fecha**     | 2026-05-05                                                                    |
| **Ref. TX**   | `**TX-01.05`**                                                                |
| **Ref. TC**   | `**TC-01`**                                                                   |
| **Ref. REQ**  | `**REQ-01`** / `**AC-01**`                                                    |
| **Severidad** | Medium                                                                        |
| **Prioridad** | Medium                                                                        |
| **QA Owner**  | Luis Adonais Malave Gamardo                                                   |


---

## 1. Descripción

Al ejecutar la búsqueda con el término `Computer`, los primeros tres resultados siguen una secuencia de precios ascendente y un patrón de nomenclatura coherente (`Build your own...`). El cuarto resultado rompe ambos patrones simultáneamente: su precio ($800.00) repite el valor del primer resultado y su nombre (`Simple Computer`) no sigue la convención de la categoría.

El defecto fue identificado durante la verificación de `**AC-01`** (ordenamiento de resultados). Constituye un hallazgo incidental de integridad de datos en la lista de resultados.

---

## 2. Pasos para reproducir

1. Navegar a `https://demowebshop.tricentis.com/`
2. Ingresar `Computer` en el buscador
3. Hacer clic en `Search`
4. Validar la secuencia de precios y nomenclatura de los resultados bajo ordenamiento por posición

---

## 3. Resultados


|              | Detalle                                                                                              |
| ------------ | ---------------------------------------------------------------------------------------------------- |
| **Esperado** | Secuencia de precios ascendente (800 → 1200 → 1800). Nomenclatura consistente (`Build your own...`)  |
| **Actual**   | El cuarto producto (`Simple Computer`, $800.00) rompe la secuencia de precios y el patrón de nombres |


---

## 4. Clasificación


| Atributo      | Valor                                                                                                                                           |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Severidad** | Low — defecto de datos/presentación; el flujo de búsqueda y compra no se bloquea                                                                |
| **Prioridad** | Medium — incoherencia de datos en resultados de búsqueda; no bloquea el flujo de compra pero impacta la experiencia de comparación de productos |
| **Entorno**   | Windows 10 Pro / Firefox 150.0.1                                                                                                                |


---

## 5. Evidencia

[2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png)

- Recuadros verdes: secuencia ascendente correcta (800 → 1200 → 1800)
- Recuadro rojo: punto de falla — cuarto resultado con precio y nombre inconsistentes

**Jira:** [Ver issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-01_Jira-Issue.png)

---

## 6. Trazabilidad


| `**TX`**       | `**TC**`    | `**REQ**` / `**AC**`       | Veredicto | `**BUG**`    |
| -------------- | ----------- | -------------------------- | --------- | ------------ |
| `**TX-01.05**` | `**TC-01**` | `**REQ-01**` / `**AC-01**` | ❌ FAIL    | `**BUG-01**` |


