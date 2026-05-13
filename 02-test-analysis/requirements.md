
# Requirements specification

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `02-test-analysis/requirements.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.6 |
| **Fase STLC** | Test Analysis |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

> [!NOTE]
> Estos requisitos no fueron entregados por un cliente ni un equipo de
> producto. Los construí por ingeniería inversa: cada **`REQ`** describe
> un comportamiento observable del SUT y cada **`AC`** formaliza el
> criterio verificable derivado de esa observación. Las anomalías
> detectadas durante ese proceso están documentadas en
> **`test-basis-evaluation.md`**.

---

## 1. Requisitos funcionales (**`REQ`**)

| ID | Módulo | Descripción | Prioridad |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | Búsqueda | El sistema retorna resultados de productos basados en coincidencia de texto. | Alta |
| **`REQ-02`** | Catálogo | El sistema permite navegar productos mediante categorías y subcategorías. | Media |
| **`REQ-03`** | Producto | El sistema muestra ficha técnica con precio, SKU y control de cantidad. | Alta |
| **`REQ-04`** | Carrito | El sistema gestiona ítems y recalcula totales al modificar cantidades. | Alta |
| **`REQ-05`** | Registro | El sistema crea cuentas de usuario validando formato de email y contraseña. | Alta |
| **`REQ-06`** | Login | El sistema autentica usuarios registrados y bloquea accesos no válidos. | Alta |
| **`REQ-07`** | Checkout | El sistema procesa el flujo de compra y confirma la generación de la orden. | Crítica |

---

## 2. Criterios de aceptación (**`AC`**)

| ID | **`REQ`** | Criterio de aceptación | Estado |
| :--- | :--- | :--- | :--- |
| **`AC-01`** | **`REQ-01`** | Los resultados se muestran ordenados alfabéticamente ante una coincidencia exacta. | ✔️ Verificable |
| **`AC-02`** | **`REQ-01`** | El sistema despliega `"No products were found that matched your criteria."` ante cero resultados. | ✔️ Verificable |
| **`AC-03`** | **`REQ-02`** | Al seleccionar una categoría o subcategoría, el sistema lista los productos correspondientes. | ✔️ Verificable |
| **`AC-04`** | **`REQ-03`** | La vista de detalle muestra Nombre, Precio, SKU e input `Qty.` simultáneamente. | ⚠️ Incumplido — campo SKU ausente en el SUT. Ver **`BUG-03`** |
| **`AC-05`** | **`REQ-04`** | El valor del `Sub-Total` refleja la suma de (Precio × Qty) de los ítems presentes en el carrito tras cada modificación o remoción. | ✔️ Verificable |
| **`AC-06`** | **`REQ-05`** | El sistema valida formato `x@x.x` para email y mínimo 6 caracteres para contraseña. | ✔️ Verificable |
| **`AC-07`** | **`REQ-05`** | El sistema despliega `"Your registration completed"` tras un registro válido. | ✔️ Verificable |
| **`AC-08`** | **`REQ-06`** | El sistema bloquea el acceso y muestra error ante credenciales no registradas. | ✔️ Verificable |
| **`AC-09`** | **`REQ-07`** | El sistema despliega `"Your order has been successfully processed!"` con el ID de orden. | ✔️ Verificable |
| **`AC-10`** | **`REQ-06`** | El sistema muestra el email registrado en el header al autenticar correctamente. | ✔️ Verificable |

---

## 3. Trazabilidad

| **`REQ`** | **`AC`** | **`TCND`** |
| :--- | :--- | :--- |
| **`REQ-01`** | **`AC-01`**, **`AC-02`** | **`TCND-01`**, **`TCND-02`** |
| **`REQ-02`** | **`AC-03`** | **`TCND-03`** |
| **`REQ-03`** | **`AC-04`** | **`TCND-04`** |
| **`REQ-04`** | **`AC-05`** | **`TCND-05`** |
| **`REQ-05`** | **`AC-06`**, **`AC-07`** | **`TCND-06`**, **`TCND-07`** |
| **`REQ-06`** | **`AC-08`**, **`AC-10`** | **`TCND-08`**, **`TCND-10`** |
| **`REQ-07`** | **`AC-09`** | **`TCND-09`** |
