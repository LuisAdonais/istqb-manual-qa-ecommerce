# Test Plan

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `01-test-planning/test-plan.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.6 |
| **Fase STLC** | Test Planning |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

> [!NOTE]
> Ejecuté este proyecto de forma individual, sin equipo de desarrollo
> ni documentación funcional previa. Construí la base de prueba
> (**`REQ`** y **`AC`**) por ingeniería inversa sobre el SUT — lo que
> significa que el análisis, el diseño y la ejecución fueron
> responsabilidad mía. Es una limitación real que este plan no oculta.

---

## 1. Alcance

### In scope

| Módulo | **`REQ`** |
| :--- | :--- |
| Búsqueda y Navegación | **`REQ-01`**, **`REQ-02`** |
| Producto y Carrito | **`REQ-03`**, **`REQ-04`** |
| Registro y Login | **`REQ-05`**, **`REQ-06`** |
| Checkout E2E | **`REQ-07`** |

### Out of scope

- Backend, APIs, base de datos
- Pagos reales
- Pruebas no funcionales

---

## 2. Objetivos

- Validar el comportamiento funcional del SUT contra **`REQ`** y **`AC`**.
- Verificar la integridad del flujo E2E de compra.
- Identificar defectos (**`BUG`**) en funcionalidades de alta criticidad.

---

## 3. Enfoque de prueba

| Categoría | Definición |
| :--- | :--- |
| **Nivel** | System Testing |
| **Tipo** | Functional Testing — Caja Negra |
| **Estrategia** | Risk-Based Testing |

**Técnicas aplicadas:**

| Técnica | Aplicación |
| :--- | :--- |
| Equivalence Partitioning (EP) | Validación de campos en formulario de registro |
| Boundary Value Analysis (BVA) | Límites de cantidad en carrito — **`TC-05`**, **`TC-10`** |
| State Transition | Flujo secuencial del Checkout |
| Error Guessing | Escenarios negativos en Login y Registro |

---
**Herramientas utilizadas:**

| Herramienta | Propósito |
| :---        | :---      |
| Firefox 150.0.1 | Navegador de ejecución |
| ShareX | Captura de evidencias (`PNG`) |
| Jira (Scrum board) | Registro y seguimiento de defectos |
| VSCode | Redacción y gestión de artefactos Markdown |
| GitHub | Repositorio y control de versiones del portafolio |

## 4. Criterios de entrada y salida

### Entry criteria

- Entorno de pruebas estable y accesible
- Base de prueba (**`REQ`** y **`AC`**) definida y aprobada
- Anomalías estáticas (**`AN`**) documentadas
- Datos de prueba (**`TD`**) especificados

### Exit criteria

| Criterio | Umbral |
| :--- | :--- |
| Casos de prueba ejecutados | 100% |
| Pass rate en **`TS-03`** (E2E) | ≥ 90% |
| Defectos Critical / High abiertos | 0 |

---

## 5. Riesgos del producto

| ID | Descripción | Prioridad | Mitigación |
| :--- | :--- | :--- | :--- |
| **`RISK-01`** | Inconsistencia en resultados de búsqueda | Alta | Cobertura **`TCND-01`**, **`TCND-02`** |
| **`RISK-02`** | Fallo en autenticación de usuarios | Alta | Cobertura **`TCND-08`**, **`TCND-10`** |
| **`RISK-03`** | Cálculo erróneo en totales del carrito | Crítica | BVA sobre **`TCND-05`** |
| **`RISK-04`** | Bloqueo en generación de número de orden | Crítica | Flujo E2E **`TCND-09`** |

---

## 6. Trazabilidad

| **`REQ`** | **`TCND`** | **`TC`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | **`TCND-01`**, **`TCND-02`** | **`TC-01`**, **`TC-02`** | **`RISK-01`** |
| **`REQ-02`** | **`TCND-03`** | **`TC-03`** | — |
| **`REQ-03`** | **`TCND-04`** | **`TC-04`** | — |
| **`REQ-04`** | **`TCND-05`** | **`TC-05`**, **`TC-10`** | **`RISK-03`** |
| **`REQ-05`** | **`TCND-06`**, **`TCND-07`** | **`TC-06`**, **`TC-07`** | — |
| **`REQ-06`** | **`TCND-08`**, **`TCND-10`** | **`TC-08`**, **`TC-11`** | **`RISK-02`** |
| **`REQ-07`** | **`TCND-09`** | **`TC-09`** | **`RISK-04`** |
