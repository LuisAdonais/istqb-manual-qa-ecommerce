
# Test Log — TL-01 (Smoke Suite)

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/test-logs/tl-01-smoke-log.md` |
| **Suite** | **`TS-01`** — Smoke Test Suite |
| **Versión** | 6.0 |
| **Fase STLC** | Test Execution — Test Logging |
| **Fecha** | 2026-05-04 / 2026-05-05 |
| **Entorno** | Windows 10 Pro / Firefox 150.0.1 |
| **Estado** | ✅ Completado |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Registro de ciclos

| **`TX`** | **`TC`** | **`TP`** | Acción verificada | Resultado real | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`TX-01.01`** | **`TC-06`** | **`TP-01`** | Enviar formulario de registro con **`TD-06`** a **`TD-10`** | El sistema procesa el formulario sin errores de validación. Todos los campos obligatorios son aceptados. | ✅ PASS |
| **`TX-01.02`** | **`TC-07`** | **`TP-01`** | Verificar mensaje de éxito tras el registro | El sistema despliega `"Your registration completed"`. El usuario permanece en la página de confirmación. | ✅ PASS |
| **`TX-01.03`** | **`TC-08`** | **`TP-01`** | Login con credenciales no registradas (**`TD-11`**, **`TD-12`**) | El sistema bloquea el acceso y despliega `"Login was unsuccessful. Please correct the errors and try again."` | ✅ PASS |
| **`TX-01.04`** | **`TC-11`** | **`TP-01`** | Login con credenciales válidas (**`TD-09`**, **`TD-10`**) | Autenticación exitosa. El header muestra `qatest_demo01@tricentis.com` como indicador de sesión activa (**`TD-21`**). | ✅ PASS |
| **`TX-01.05`** | **`TC-01`** | **`TP-02`** | Búsqueda con término exacto (**`TD-01`**: `Computer`) | Resultados desplegados. La secuencia de precios bajo el criterio "Position" es incoherente (800 → 1200 → 1800 → 800). Nomenclatura inconsistente en el cuarto resultado. → **`BUG-01`** | ❌ FAIL |
| **`TX-01.06`** | **`TC-02`** | **`TP-02`** | Búsqueda con término inválido (**`TD-02`**) | El sistema despliega `"No products were found that matched your criteria."` | ✅ PASS |
| **`TX-01.07`** | **`TC-03`** | **`TP-02`** | Navegación a subcategoría `Desktops` (**`TD-03`**) | Navegación correcta. La etiqueta `Digital downloads` usa Sentence Case en lugar del Title Case estándar del menú. → **`BUG-02`** | ❌ FAIL |
| **`TX-01.08`** | **`TC-04`** | **`TP-02`** | Seleccionar producto para validar ficha de detalle | Ficha cargada. El campo SKU no es visible en la interfaz, incumpliendo **`AC-04`**. → **`BUG-03`** | ❌ FAIL |

---

## 2. Resumen

| Métrica | Resultado |
| :--- | :--- |
| **TX Ejecutados** | 8 / 8 |
| **PASS** | 5 |
| **FAIL** | 3 |
| **Pass Rate** | 62.5% |
| **Defectos** | **`BUG-01`**, **`BUG-02`**, **`BUG-03`** |


> [!NOTE]
> Continuación de suites autorizada mediante **`EDN-01`** (2026-05-04). Los defectos detectados son Low/Medium y no bloquean los flujos de Carrito ni Checkout.

---

## 3. Evidencias

| **`TX`** | **`TC`** | **`TP`** | Evidencia |
| :--- | :--- | :--- | :--- |
| **`TX-01.01`** | **`TC-06`** | **`TP-01`** | [2026-05-04_TX-01.01_Register_Submit_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.01_Register_Submit_PASS.png) |
| **`TX-01.02`** | **`TC-07`** | **`TP-01`** | [2026-05-04_TX-01.02_Register_Success_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.02_Register_Success_PASS.png) |
| **`TX-01.03`** | **`TC-08`** | **`TP-01`** | [2026-05-04_TX-01.03_Login_Fail_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.03_Login_Fail_PASS.png) |
| **`TX-01.04`** | **`TC-11`** | **`TP-01`** | [2026-05-04_TX-01.04_Login_Success_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.04_Login_Success_PASS.png) |
| **`TX-01.05`** | **`TC-01`** | **`TP-02`** | [2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png) |
| **`TX-01.06`** | **`TC-02`** | **`TP-02`** | [2026-05-05_TX-01.06_Search_Empty_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.06_Search_Empty_PASS.png) |
| **`TX-01.07`** | **`TC-03`** | **`TP-02`** | [2026-05-05_TX-01.07_Category_Nav_BUG-02.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.07_Category_Nav_BUG-02.png) |
| **`TX-01.08`** | **`TC-04`** | **`TP-02`** | [2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png)
