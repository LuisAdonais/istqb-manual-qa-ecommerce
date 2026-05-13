
# Test Procedures

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `04-test-implementation/test-procedures.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.7 |
| **Fase STLC** | Test Implementation |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## **`TP-01`** — Gestión de cuentas

**Casos:** **`TC-06`**, **`TC-07`**, **`TC-08`**, **`TC-11`** | **Suite:** **`TS-01`**, **`TS-02`**

| # | Acción | **`TD`** | Resultado esperado |
| :--- | :--- | :--- | :--- |
| 1 | Navegar a `/register` | — | El sistema despliega el formulario de registro |
| 2 | Seleccionar género. Ingresar nombre y apellido | **`TD-06`**, **`TD-07`**, **`TD-08`** | El sistema acepta los datos |
| 3 | Ingresar email y contraseña. Hacer clic en `Register` | **`TD-09`**, **`TD-10`** | El sistema procesa el formulario sin errores de validación (**`TC-06`**) |
| 4 | Verificar la pantalla resultante | — | El sistema muestra `"Your registration completed"` (**`TC-07`**) |
| 5 | Hacer clic en `Log out`. Navegar a `/login` | — | El sistema cierra sesión y muestra el formulario de login |
| 6 | Ingresar credenciales no registradas. Hacer clic en `Log in` | **`TD-11`**, **`TD-12`** | El sistema despliega `"Login was unsuccessful"` (**`TC-08`**) |
| 7 | Ingresar credenciales válidas. Hacer clic en `Log in` | **`TD-09`**, **`TD-10`** | El sistema autentica al usuario y muestra **`TD-21`** en el header (**`TC-11`**) |

---

## **`TP-02`** — Búsqueda y catálogo

**Casos:** **`TC-01`**, **`TC-02`**, **`TC-03`**, **`TC-04`** | **Suite:** **`TS-01`**, **`TS-02`**

| # | Acción | **`TD`** | Resultado esperado |
| :--- | :--- | :--- | :--- |
| 1 | Ingresar término válido en `Search store`. Hacer clic en `Search` | **`TD-01`** | El sistema muestra resultados ordenados alfabéticamente (**`TC-01`**) |
| 2 | Ingresar término inválido en `Search store`. Hacer clic en `Search` | **`TD-02`** | El sistema despliega `"No products were found..."` (**`TC-02`**) |
| 3 | Navegar a `Computers > Desktops` mediante el menú lateral | **`TD-03`** | El sistema lista únicamente los productos de la subcategoría (**`TC-03`**) |
| 4 | Hacer clic en la imagen o título de un producto | — | El sistema muestra Nombre, Precio, SKU, input `Qty.` y botón `Add to cart` (**`TC-04`**) |

---

## **`TP-03`** — Carrito y checkout E2E

**Casos:** **`TC-05`**, **`TC-09`**, **`TC-10`** | **Suite:** **`TS-02`**, **`TS-03`**

**Precondición:** Sesión activa con **`TD-09`** y **`TD-10`**. Mínimo 1 ítem en carrito.

> [!NOTE]
> El campo `Qty.` no tiene controles de incremento/decremento. La modificación es exclusivamente por teclado. Ingresar `0` remueve el ítem del carrito. Ver **`AN-05`**.

| # | Acción | **`TD`** | Resultado esperado |
| :--- | :--- | :--- | :--- |
| 1 | Navegar a `/cart` | — | El sistema muestra los ítems y totales |
| 2 | Modificar `Qty.` del ítem 1 a `2`. Hacer clic en `Update shopping cart` | **`TD-04`** | El `Sub-Total` del ítem 1 se actualiza correctamente (**`TC-05`**) |
| 3 | Modificar `Qty.` del ítem 1 a `0`. Hacer clic en `Update shopping cart` | **`TD-19`** | Si hay más ítems: el ítem es eliminado y el total se recalcula (**`TC-05`**). Si es el único ítem: el sistema muestra `"Your Shopping Cart is empty!"` (**`TC-10`**) |
| 4 | Agregar un ítem al carrito. Activar checkbox de términos. Hacer clic en `Checkout` | — | El sistema inicia el flujo transaccional |
| 5 | Completar dirección de envío y método de pago | **`TD-14`** — **`TD-18`** | El sistema acepta los datos y permite continuar |
| 6 | Hacer clic en `Confirm` | — | El sistema despliega `"Your order has been successfully processed!"` con el ID de orden (**`TC-09`**) |

---

## Trazabilidad

| **`TP`** | **`TC`** integrados | **`TD`** consumidos |
| :--- | :--- | :--- |
| **`TP-01`** | **`TC-06`**, **`TC-07`**, **`TC-08`**, **`TC-11`** | **`TD-06`** — **`TD-12`**, **`TD-21`** |
| **`TP-02`** | **`TC-01`**, **`TC-02`**, **`TC-03`**, **`TC-04`** | **`TD-01`**, **`TD-02`**, **`TD-03`** |
| **`TP-03`** | **`TC-05`**, **`TC-09`**, **`TC-10`** | **`TD-04`**, **`TD-13`** — **`TD-19`** |
