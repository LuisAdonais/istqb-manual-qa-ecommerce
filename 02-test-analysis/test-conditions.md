
# Test Conditions

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `02-test-analysis/test-conditions.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.5 |
| **Fase STLC** | Test Analysis |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Condiciones de prueba (`TCND`)

Afirmaciones atómicas derivadas de los **`AC`** aprobados. Definen qué debe ser verificado antes del diseño de casos de prueba.

| ID | **`AC`** | Condición de prueba | Prioridad | **`RISK`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TCND-01`** | **`AC-01`** | Validar que los resultados de búsqueda se ordenan alfabéticamente ante una coincidencia exacta. | Alta | **`RISK-01`** |
| **`TCND-02`** | **`AC-02`** | Validar que el sistema despliega el mensaje de cero resultados ante una búsqueda sin coincidencias. | Media | **`RISK-01`** |
| **`TCND-03`** | **`AC-03`** | Validar que la navegación por categorías lista únicamente los productos de la subcategoría seleccionada. | Media | — |
| **`TCND-04`** | **`AC-04`** | Validar que la ficha de producto muestra Nombre, Precio, SKU e input `Qty.` simultáneamente. | Alta | — |
| **`TCND-05`** | **`AC-05`** | Validar el recálculo del `Sub-Total` al modificar cantidades y al remover ítems del carrito. | Crítica | **`RISK-03`** |
| **`TCND-06`** | **`AC-06`** | Validar el formato de email (`x@x.x`) y longitud mínima de contraseña (6 caracteres) en el registro. | Alta | — |
| **`TCND-07`** | **`AC-07`** | Validar el mensaje de confirmación tras un registro válido y la ausencia de redirección automática. | Alta | — |
| **`TCND-08`** | **`AC-08`** | Validar el bloqueo de acceso y mensaje de error ante credenciales no registradas. | Alta | **`RISK-02`** |
| **`TCND-09`** | **`AC-09`** | Validar la confirmación de orden y el ID generado al finalizar el checkout. | Crítica | **`RISK-04`** |
| **`TCND-10`** | **`AC-10`** | Validar la autenticación exitosa y la visualización del email en el header con credenciales válidas. | Alta | **`RISK-02`** |

---

## 2. Trazabilidad

| **`REQ`** | **`AC`** | **`TCND`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | **`AC-01`**, **`AC-02`** | **`TCND-01`**, **`TCND-02`** | **`RISK-01`** |
| **`REQ-02`** | **`AC-03`** | **`TCND-03`** | — |
| **`REQ-03`** | **`AC-04`** | **`TCND-04`** | — |
| **`REQ-04`** | **`AC-05`** | **`TCND-05`** | **`RISK-03`** |
| **`REQ-05`** | **`AC-06`**, **`AC-07`** | **`TCND-06`**, **`TCND-07`** | — |
| **`REQ-06`** | **`AC-08`**, **`AC-10`** | **`TCND-08`**, **`TCND-10`** | **`RISK-02`** |
| **`REQ-07`** | **`AC-09`** | **`TCND-09`** | **`RISK-04`** |
