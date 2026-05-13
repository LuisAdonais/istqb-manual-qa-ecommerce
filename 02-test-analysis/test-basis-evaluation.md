
# Test Basis Evaluation

| Atributo      | Detalle                                    |
| :---          | :---                                       |
| **Ubicación** | `02-test-analysis/test-basis-evaluation.md` |
| **Proyecto**  | Tricentis Demo Web Shop                     |
| **Versión**   | 1.6                                         |
| **Fase STLC** | Test Analysis — Static Testing              |
| **Estado**    | ✅ Approved                                 |
| **QA Owner**  | Luis Adonais Malave Gamardo                 |

---

## 1. Anomalías estáticas (`AN`)

Hallazgos identificados durante la revisión estática de la base de prueba (**`REQ`** y **`AC`**).

| ID          | Origen         | Hallazgo                                                                                                                                                     | Severidad | Estado                                                                                     |
| :---        | :---           | :---                                                                                                                                                         | :---      | :---                                                                                       |
| **`AN-01`** | **`REQ-05`**   | Reglas de validación de email y contraseña no estaban definidas en el requisito original.                                                                    | Media     | ✅ Resuelto — **`AC-06`** ajustado                                                         |
| **`AN-02`** | **`REQ-07`**   | El requisito original incluía notificación por email al completar el checkout. El SUT solo genera un ID en pantalla.                                         | Alta      | ✅ Resuelto — **`AC-09`** ajustado al comportamiento real del SUT                           |
| **`AN-03`** | **`AC-01`**    | El criterio no especificaba el tipo de ordenamiento esperado en los resultados de búsqueda.                                                                  | Baja      | ✅ Resuelto — Orden alfabético confirmado y formalizado                                     |
| **`AN-04`** | **`REQ-06`**   | El escenario positivo de autenticación no tenía **`AC`** asociado.                                                                                           | Media     | ✅ Resuelto — **`AC-10`** definido, **`TCND-10`** y **`TC-11`** derivados                   |
| **`AN-05`** | **`REQ-04`**   | El SUT no dispone de controles visuales de cantidad en el carrito. Ingresar `0` en `Qty.` remueve el ítem — comportamiento no documentado en el **`REQ`**. | Baja      | 🟡 Abierto — Mejora de usabilidad. Sin impacto sobre **`AC-05`**. Confirmado en **`TX-02.02`** |

---

## 2. Trazabilidad

| **`REQ`**    | **`AN`**   | Estado                                |
| :---         | :---       | :---                                  |
| **`REQ-01`** | **`AN-03`**| ✅ Ready                              |
| **`REQ-02`** | —          | ✅ Ready                              |
| **`REQ-03`** | —          | ✅ Ready                              |
| **`REQ-04`** | **`AN-05`**| 🟡 Mejora sugerida — no bloquea        |
| **`REQ-05`** | **`AN-01`**| ✅ Ready                              |
| **`REQ-06`** | **`AN-04`**| ✅ Ready                              |
| **`REQ-07`** | **`AN-02`**| ✅ Ready                              |
