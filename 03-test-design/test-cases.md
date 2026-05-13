# Test Cases


| Atributo      | Detalle                        |
| ------------- | ------------------------------ |
| **Ubicación** | `03-test-design/test-cases.md` |
| **Proyecto**  | Tricentis Demo Web Shop        |
| **Versión**   | 1.6                            |
| **Fase STLC** | Test Design                    |
| **Estado**    | ✅ Approved                     |
| **QA Owner**  | Luis Adonais Malave Gamardo    |


---

## Módulo: Búsqueda y Catálogo

### `**TC-01`** — Búsqueda exitosa con término exacto


| Campo            | Detalle                     |
| ---------------- | --------------------------- |
| `**TCND**`       | `**TCND-01**`               |
| **Técnica**      | Caja negra                  |
| **Precondición** | Usuario en página de inicio |



| #   | Acción                                | Resultado esperado                                     |
| --- | ------------------------------------- | ------------------------------------------------------ |
| 1   | Ingresar `Computer` en `Search store` | Campo acepta la entrada                                |
| 2   | Hacer clic en `Search`                | El sistema muestra productos ordenados alfabéticamente |


---

### `**TC-02`** — Búsqueda sin resultados


| Campo            | Detalle                     |
| ---------------- | --------------------------- |
| `**TCND**`       | `**TCND-02**`               |
| **Técnica**      | Error Guessing              |
| **Precondición** | Usuario en página de inicio |



| #   | Acción                                      | Resultado esperado                                                          |
| --- | ------------------------------------------- | --------------------------------------------------------------------------- |
| 1   | Ingresar `Inexistente999` en `Search store` | Campo acepta la entrada                                                     |
| 2   | Hacer clic en `Search`                      | El sistema despliega `"No products were found that matched your criteria."` |


---

### `**TC-03`** — Navegación por categorías


| Campo            | Detalle                     |
| ---------------- | --------------------------- |
| `**TCND**`       | `**TCND-03**`               |
| **Técnica**      | Caja negra                  |
| **Precondición** | Usuario en página de inicio |



| #   | Acción                                 | Resultado esperado                                      |
| --- | -------------------------------------- | ------------------------------------------------------- |
| 1   | Hacer clic en la categoría `Computers` | El sistema expande las subcategorías                    |
| 2   | Seleccionar la subcategoría `Desktops` | El sistema lista únicamente los productos de `Desktops` |


---

### `**TC-04`** — Atributos en ficha de producto


| Campo            | Detalle                                   |
| ---------------- | ----------------------------------------- |
| `**TCND**`       | `**TCND-04**`                             |
| **Técnica**      | Caja negra                                |
| **Precondición** | Usuario visualiza un listado de productos |



| #   | Acción                                          | Resultado esperado                                                           |
| --- | ----------------------------------------------- | ---------------------------------------------------------------------------- |
| 1   | Hacer clic en la imagen o título de un producto | El sistema despliega Nombre, Precio, SKU, input `Qty.` y botón `Add to cart` |


---

## Módulo: Carrito de compras

### `**TC-05`** — Recálculo y remoción parcial del carrito (BVA positivo)


| Campo            | Detalle                               |
| ---------------- | ------------------------------------- |
| `**TCND**`       | `**TCND-05**`                         |
| **Técnica**      | Boundary Value Analysis (BVA)         |
| **Precondición** | Carrito con **2 productos distintos** |



| #   | Acción                                                                  | `**TD`**    | Resultado esperado                                                                       |
| --- | ----------------------------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------- |
| 1   | Ingresar a `/cart`                                                      | —           | El sistema muestra los ítems y totales                                                   |
| 2   | Modificar `Qty.` del ítem 1 a `2`. Hacer clic en `Update shopping cart` | `**TD-04**` | El `Sub-Total` del ítem 1 se actualiza a precio × 2. El ítem 2 no cambia                 |
| 3   | Modificar `Qty.` del ítem 1 a `0`. Hacer clic en `Update shopping cart` | `**TD-19**` | El ítem 1 es eliminado. El total refleja únicamente el ítem 2. El carrito no queda vacío |


---

### `**TC-10**` — Remoción total del carrito (BVA negativo)


| Campo            | Detalle                       |
| ---------------- | ----------------------------- |
| `**TCND**`       | `**TCND-05**`                 |
| **Técnica**      | Boundary Value Analysis (BVA) |
| **Precondición** | Carrito con **1 producto**    |



| #   | Acción                                                       | `**TD`**    | Resultado esperado                                                          |
| --- | ------------------------------------------------------------ | ----------- | --------------------------------------------------------------------------- |
| 1   | Ingresar a `/cart`                                           | —           | El sistema muestra el ítem y el total                                       |
| 2   | Modificar `Qty.` a `0`. Hacer clic en `Update shopping cart` | `**TD-19**` | El ítem es eliminado. El sistema despliega `"Your Shopping Cart is empty!"` |


> [!NOTE]
>
> `TC-05` y `TC-10` comparten el mismo valor de entrada (`Qty. = 0`),
> pero no son redundantes. La diferencia radica en la precondición:
> 
> - `TC-05` valida la remoción parcial y el recálculo del total cuando el carrito tiene más de un ítem.
> - `TC-10` valida la remoción total cuando el ítem eliminado es el único en el carrito.
>
> Esto es una decisión de diseño deliberada, no un error por duplicidad.

---

## Módulo: Registro y autenticación

### `**TC-06**` — Registro con datos válidos (EP)


| Campo            | Detalle                       |
| ---------------- | ----------------------------- |
| `**TCND**`       | `**TCND-06**`                 |
| **Técnica**      | Equivalence Partitioning (EP) |
| **Precondición** | Usuario en `/register`        |



| #   | Acción                                         | `**TD`**                              | Resultado esperado                           |
| --- | ---------------------------------------------- | ------------------------------------- | -------------------------------------------- |
| 1   | Seleccionar género. Ingresar nombre y apellido | `**TD-06**`, `**TD-07**`, `**TD-08**` | El sistema acepta los datos                  |
| 2   | Ingresar email y contraseña válidos            | `**TD-09**`, `**TD-10**`              | El sistema no muestra errores de validación  |
| 3   | Hacer clic en `Register`                       | —                                     | El sistema procesa el formulario sin errores |


---

### `**TC-07**` — Confirmación de registro exitoso


| Campo            | Detalle                                 |
| ---------------- | --------------------------------------- |
| `**TCND**`       | `**TCND-07**`                           |
| **Técnica**      | Caja negra                              |
| **Precondición** | `**TC-06`** ejecutado en el mismo flujo |



| #   | Acción                                         | Resultado esperado                                                                  |
| --- | ---------------------------------------------- | ----------------------------------------------------------------------------------- |
| 1   | Verificar la pantalla resultante tras el envío | El sistema despliega `"Your registration completed"`. No hay redirección automática |


---

### `**TC-08**` — Bloqueo con credenciales inválidas


| Campo            | Detalle             |
| ---------------- | ------------------- |
| `**TCND**`       | `**TCND-08**`       |
| **Técnica**      | Error Guessing      |
| **Precondición** | Usuario en `/login` |



| #   | Acción                                    | `**TD`**                 | Resultado esperado                                                  |
| --- | ----------------------------------------- | ------------------------ | ------------------------------------------------------------------- |
| 1   | Ingresar email no registrado y contraseña | `**TD-11**`, `**TD-12**` | El sistema acepta la entrada                                        |
| 2   | Hacer clic en `Log in`                    | —                        | El sistema bloquea el acceso y despliega `"Login was unsuccessful"` |


---

### `**TC-11**` — Login exitoso con credenciales válidas


| Campo            | Detalle                                            |
| ---------------- | -------------------------------------------------- |
| `**TCND**`       | `**TCND-10**`                                      |
| **Técnica**      | Caja negra                                         |
| **Precondición** | Usuario en `/login`. Cuenta `**TD-09`** pre-creada |



| #   | Acción                                  | `**TD**`                 | Resultado esperado                                                 |
| --- | --------------------------------------- | ------------------------ | ------------------------------------------------------------------ |
| 1   | Ingresar email y contraseña registrados | `**TD-09**`, `**TD-10**` | El sistema acepta la entrada                                       |
| 2   | Hacer clic en `Log in`                  | —                        | El sistema autentica al usuario y muestra `**TD-21**` en el header |


---

## Módulo: Checkout E2E

### `**TC-09**` — Flujo de compra completo


| Campo            | Detalle                                              |
| ---------------- | ---------------------------------------------------- |
| `**TCND**`       | `**TCND-09**`                                        |
| **Técnica**      | State Transition                                     |
| **Precondición** | Usuario autenticado. Carrito con al menos 1 producto |



| #   | Acción                                                                     | `**TD`**                  | Resultado esperado                                                                      |
| --- | -------------------------------------------------------------------------- | ------------------------- | --------------------------------------------------------------------------------------- |
| 1   | Ingresar a `/cart`. Activar checkbox de términos. Hacer clic en `Checkout` | —                         | El sistema inicia el flujo transaccional                                                |
| 2   | Completar dirección de envío                                               | `**TD-14**` a `**TD-18**` | El sistema acepta los datos sin errores                                                 |
| 3   | Seleccionar método de pago y envío                                         | —                         | El sistema permite continuar al siguiente paso                                          |
| 4   | Hacer clic en `Confirm`                                                    | —                         | El sistema despliega `"Your order has been successfully processed!"` con el ID de orden |


---

## Trazabilidad

| **`TCND`**    | **`TC`**                 | Técnica              | **`RISK`**    |
| :---          | :---                     | :---                 | :---          |
| **`TCND-01`** | **`TC-01`**              | EP                   | **`RISK-01`** |
| **`TCND-02`** | **`TC-02`**              | Error Guessing       | **`RISK-01`** |
| **`TCND-03`** | **`TC-03`**              | EP                   | —             |
| **`TCND-04`** | **`TC-04`**              | Checklist-Based      | —             |
| **`TCND-05`** | **`TC-05`**, **`TC-10`** | BVA                  | **`RISK-03`** |
| **`TCND-06`** | **`TC-06`**              | EP                   | —             |
| **`TCND-07`** | **`TC-07`**              | State Transition     | —             |
| **`TCND-08`** | **`TC-08`**              | Error Guessing       | **`RISK-02`** |
| **`TCND-09`** | **`TC-09`**              | State Transition     | **`RISK-04`** |
| **`TCND-10`** | **`TC-11`**              | EP                   | **`RISK-02`** |

