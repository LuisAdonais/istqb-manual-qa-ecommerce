
# Test data requirements

| Atributo    | Detalle                                    |
| :---        | :---                                       |
| **Ubicación** | `03-test-design/test-data-requirements.md` |
| **Proyecto** | Tricentis Demo Web Shop                    |
| **Versión**  | 1.8                                        |
| **Fase STLC** | Test Design                              |
| **Estado**   | ✅ Approved                                |
| **QA Owner** | Luis Adonais Malave Gamardo                |

---

## 1. Datos de prueba (`TD`)

### Búsqueda y catálogo

| ID          | **`TC`**       | Tipo        | Parámetro                   | Valor                      |
| :---        | :---           | :---        | :---                       | :---                       |
| **`TD-01`** | **`TC-01`**    | Entrada     | `Search store`              | `Computer`                 |
| **`TD-02`** | **`TC-02`**    | Entrada     | `Search store`              | `Inexistente999`           |
| **`TD-03`** | **`TC-03`**    | Navegación  | `Category > Subcategory`    | `Computers > Desktops`     |

### Carrito de compras

| ID          | **`TC`**                  | Tipo                   | Parámetro | Valor |
| :---        | :---                      | :---                   | :---      | :---  |
| **`TD-04`** | **`TC-05`**               | Entrada — BVA positivo | `Qty.`    | `2`   |
| **`TD-19`** | **`TC-05`**, **`TC-10`**  | Entrada — BVA negativo | `Qty.`    | `0`   |

### Registro y autenticación

| ID          | **`TC`**                       | Tipo               | Parámetro                       | Valor                            |
| :---        | :---                           | :---               | :---                            | :---                             |
| **`TD-06`** | **`TC-06`**, **`TC-07`**       | Entrada — EP       | `Gender`                        | `Male`                           |
| **`TD-07`** | **`TC-06`**, **`TC-07`**       | Entrada — EP       | `First name`                    | `QA`                             |
| **`TD-08`** | **`TC-06`**, **`TC-07`**       | Entrada — EP       | `Last name`                     | `Tester`                         |
| **`TD-09`** | **`TC-06`**, **`TC-07`**, **`TC-11`** | Entrada — EP | `Email`                         | `qatest_demo01@tricentis.com`    |
| **`TD-10`** | **`TC-06`**, **`TC-07`**, **`TC-11`** | Entrada — EP | `Password` / `Confirm password` | `123456`                         |
| **`TD-11`** | **`TC-08`**                    | Entrada — negativa  | `Email`                         | `unregistered_qa@tricentis.com`  |
| **`TD-12`** | **`TC-08`**                    | Entrada — negativa  | `Password`                      | `randomPwd!`                     |
| **`TD-21`** | **`TC-11`**                    | Estado esperado     | Indicador de sesión en header    | `qatest_demo01@tricentis.com` — El SUT muestra el email registrado, no el nombre. Verificado en **`TX-01.04`** |

### Checkout E2E

| ID          | **`TC`**    | Tipo    | Parámetro           | Valor                                         |
| :---        | :---        | :---    | :---                | :---                                          |
| **`TD-13`** | **`TC-09`** | Estado  | Cuenta de usuario   | Autenticado — Ref. **`TD-09`**, **`TD-10`**   |
| **`TD-14`** | **`TC-09`** | Entrada | `Country`           | `United States`                               |
| **`TD-15`** | **`TC-09`** | Entrada | `City`              | `New York`                                    |
| **`TD-16`** | **`TC-09`** | Entrada | `Address 1`         | `5th Avenue 123`                              |
| **`TD-17`** | **`TC-09`** | Entrada | `Zip / postal code` | `10001`                                       |
| **`TD-18`** | **`TC-09`** | Entrada | `Phone number`      | `5551234567`                                  |

---

## 2. Trazabilidad

| **`TCND`**    | **`TC`**                 | **`TD`**                              |
| :---          | :---                     | :---                                  |
| **`TCND-01`** | **`TC-01`**              | **`TD-01`**                           |
| **`TCND-02`** | **`TC-02`**              | **`TD-02`**                           |
| **`TCND-03`** | **`TC-03`**              | **`TD-03`**                           |
| **`TCND-04`** | **`TC-04`**              | —                                     |
| **`TCND-05`** | **`TC-05`**, **`TC-10`** | **`TD-04`**, **`TD-19`**              |
| **`TCND-06`** | **`TC-06`**              | **`TD-06`** — **`TD-10`**             |
| **`TCND-07`** | **`TC-07`**              | **`TD-06`** — **`TD-10`**             |
| **`TCND-08`** | **`TC-08`**              | **`TD-11`**, **`TD-12`**              |
| **`TCND-09`** | **`TC-09`**              | **`TD-13`** — **`TD-18`**             |
| **`TCND-10`** | **`TC-11`**              | **`TD-09`**, **`TD-10`**, **`TD-21`** |
