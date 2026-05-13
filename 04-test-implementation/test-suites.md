
# Test Suites

| Atributo      | Detalle                                 |
| :---          | :---                                    |
| **Ubicación** | `04-test-implementation/test-suites.md` |
| **Proyecto**  | Tricentis Demo Web Shop                 |
| **Versión**   | 1.7                                     |
| **Fase STLC** | Test Implementation                     |
| **Estado**    | ✅ Approved                             |
| **QA Owner**  | Luis Adonais Malave Gamardo             |

---

## 1. Reglas de ejecución

- Ejecutar en orden: **`TS-01`** → **`TS-02`** → **`TS-03`**
- Limpiar caché y cookies antes de cada suite
- Entorno: Windows 10 Pro / Firefox 150.0.1

---

## 2. Criterios de entrada

| Suite       | Criterio                                                            |
| :---        | :---                                                                |
| **`TS-01`** | Entorno configurado. Caché limpia. Cuenta **`TD-09`** pre-creada    |
| **`TS-02`** | **`TS-01`** completada sin defectos Critical o High abiertos        |
| **`TS-03`** | **`TS-01`** completada sin defectos Critical o High abiertos        |

---

## 3. Criterios de suspensión

| Suite       | Condición de suspensión                                             | Reanudación                             |
| :---        | :---                                                               | :---                                    |
| **`TS-02`** | FAIL en login o catálogo con severidad Critical o High en **`TS-01`** | Tras confirmar corrección del **`BUG`** |
| **`TS-03`** | Error de servidor (500) al agregar productos al carrito             | Tras confirmar corrección del **`BUG`** |

---

## 4. Suites

### **`TS-01`** — Smoke test

**Objetivo:** Verificar la disponibilidad del SUT y la operatividad de los módulos críticos.

| Secuencia | **`TP`**    | Validación                             |
| :---      | :---        | :---                                   |
| 1         | **`TP-01`** | Registro, login exitoso y login fallido |
| 2         | **`TP-02`** | Búsqueda y navegación de catálogo       |

**Criterio de cierre:**

| Resultado            | Acción                                                            |
| :---                 | :---                                                              |
| Todos PASS           | Suite aprobada — continuar con **`TS-02`** y **`TS-03`**         |
| FAIL Critical / High | Suspender ejecución                                               |
| FAIL Low / Medium    | Continuar bajo riesgo controlado — documentar en **`EDN`**        |

---

### **`TS-02`** — Regression

**Objetivo:** Verificar el funcionamiento del módulo de Carrito ante los defectos detectados en **`TS-01`**.

**Precondición:** **`TS-01`** completada sin defectos Critical o High abiertos.

> [!NOTE]
> 
> **Alcance de ejecución:** **`TP-01`** y **`TP-02`** no fueron re-ejecutados en esta suite
> al no detectarse defectos en los módulos de Registro, Login, Búsqueda ni Catálogo durante
> **`TS-01`**. La regresión se focalizó en el módulo de Carrito (**`TP-03`**), que no había
> sido cubierto en el Smoke. Decisión documentada en [**`EDN-01`**](./05-test-execution/decisions/edn-01-execution-decision-note.md).

| Secuencia | **`TP`**    | **`TC`** cubiertos                          |
| :---      | :---        | :---                                        |
| 1         | **`TP-03`** | **`TC-05`**, **`TC-09`**, **`TC-10`**       |

---

### **`TS-03`** — E2E checkout

**Objetivo:** Validar el flujo completo de compra desde login hasta confirmación de orden.

**Precondición:** **`TS-01`** aprobada. Sesión activa con **`TD-09`** y **`TD-10`**.

| Secuencia | **`TP`**    | Instrucción                                             |
| :---      | :---        | :---                                                    |
| 1         | **`TP-01`** | Ejecutar **`TC-11`** para establecer sesión activa      |
| 2         | **`TP-02`** | Navegar catálogo y agregar producto al carrito          |
| 3         | **`TP-03`** | Validar carrito y ejecutar checkout hasta confirmación de orden |

> [!NOTE]
> 
> **`TC-04`** se ejecuta dentro de **`TP-02`** como paso de navegación implícito en **`TS-03`**.
> Su validación formal ocurre en **`TS-01`**.

---

## 5. Trazabilidad

| **`TS`**    | Tipo       | **`TP`**                              | **`TC`** incluidos                                                |
| :---        | :---       | :---                                  | :---                                                              |
| **`TS-01`** | Smoke      | **`TP-01`**, **`TP-02`**              | **`TC-01`** — **`TC-04`**, **`TC-06`** — **`TC-08`**, **`TC-11`** |
| **`TS-02`** | Regression | **`TP-03`**                           | **`TC-05`**, **`TC-09`**, **`TC-10`**                             |
| **`TS-03`** | E2E        | **`TP-01`**, **`TP-02`**, **`TP-03`** | **`TC-04`**\*, **`TC-05`**, **`TC-09`**, **`TC-10`**, **`TC-11`** |
