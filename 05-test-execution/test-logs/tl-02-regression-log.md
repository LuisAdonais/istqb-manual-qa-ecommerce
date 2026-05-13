# Test Log — TL-02 (Regression Suite)

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/test-logs/tl-02-regression-log.md` |
| **Suite** | **`TS-02`** — Full Regression Suite |
| **Versión** | 2.1 |
| **Fase STLC** | Test Execution — Test Logging |
| **Fecha** | 2026-05-05 |
| **Entorno** | Windows 10 Pro / Firefox 150.0.1 |
| **Estado** | ✅ Completado sin fallos |
| **QA Owner** | Luis Adonais Malave Gamardo |

---
> **Precondición de entrada:** **`TS-01`** completada con 3 defectos abiertos (**`BUG-01`**, **`BUG-02`**, **`BUG-03`**). Continuación autorizada mediante **`EDN-01`** (2026-05-04) al no existir defectos Critical o High. Ver `edn-01-execution-decision-note.md`.

**Precondición operativa:** Sesión activa con **`TD-09`** y **`TD-10`**.

- **`TX-02.01`** y **`TX-02.02`**: carrito con **1 ítem** antes de iniciar cada ciclo.
- **`TX-02.03`**: carrito con **2 ítems distintos** — necesario para aislar la remoción parcial y verificar recálculo sobre el ítem restante.

---

## 1. Registro de ciclos

| **`TX`** | **`TC`** | **`TP`** | Acción verificada | **`TD`** | Resultado real | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`TX-02.01`** | **`TC-05`** | **`TP-03`** | Modificar `Qty.` a `2`. Hacer clic en `Update shopping cart`. Validar recálculo del `Sub-Total`. | **`TD-04`** | El sistema actualiza el `Sub-Total` correctamente: precio unitario × 2. El campo acepta modificación por teclado. | ✅ PASS |
| **`TX-02.02`** | **`TC-10`** | **`TP-03`** | Con 1 ítem en carrito, modificar `Qty.` a `0`. Hacer clic en `Update shopping cart`. Validar carrito vacío. | **`TD-19`** | El sistema elimina el ítem y despliega `"Your Shopping Cart is empty!"`. El ingreso de `Qty. = 0` es el mecanismo de remoción del SUT. Ver **`AN-05`**. | ✅ PASS |
| **`TX-02.03`** | **`TC-05`** | **`TP-03`** | Con 2 ítems distintos, modificar `Qty.` del ítem 1 a `0`. Hacer clic en `Update shopping cart`. Validar remoción parcial y recálculo. | **`TD-19`** | El ítem 1 es eliminado. El total se recalcula sobre el ítem 2 restante. El carrito no queda vacío ni muestra mensaje de carrito vacío. Comportamiento diferenciado de **`TX-02.02`**. | ✅ PASS |

---

## 2. Resumen

| Métrica | Resultado |
| :--- | :--- |
| **TX Planificados** | 3 |
| **Ejecutados** | 3 |
| **PASS** | 3 |
| **FAIL** | 0 |
| **Pass Rate** | 100% |
| **Defectos** | Ninguno |

> [!NOTE]
> **`TS-02`** cumple el criterio de cierre renegociado en **`EDN-01`**: 100% PASS, sin defectos nuevos Critical o High. La observación **`AN-05`** no constituye defecto funcional y no afecta el resultado.

---

## 3. Evidencias

| **`TX`** | **`TC`** | **`TP`** | Evidencia |
| :--- | :--- | :--- | :--- |
| **`TX-02.01`** | **`TC-05`** | **`TP-03`** | [2026-05-05_TX-02.01_Cart_Recalculate_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.01_Cart_Recalculate_PASS.png) |
| **`TX-02.02`** | **`TC-10`** | **`TP-03`** | [2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png) |
| **`TX-02.03`** | **`TC-05`** | **`TP-03`** | [2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png) |

---

## 4. Trazabilidad

| **`TP`** | **`TC`** | **`TD`** | **`TX`** | **`TCND`** | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`TP-03`** | **`TC-05`** | **`TD-04`** | **`TX-02.01`** | **`TCND-05`** | ✅ PASS |
| **`TP-03`** | **`TC-10`** | **`TD-19`** | **`TX-02.02`** | **`TCND-05`** | ✅ PASS |
| **`TP-03`** | **`TC-05`** | **`TD-19`** | **`TX-02.03`** | **`TCND-05`** | ✅ PASS |
