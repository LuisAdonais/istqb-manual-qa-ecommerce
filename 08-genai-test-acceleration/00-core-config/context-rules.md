
# CONTEXT RULES — Tricentis Demo Web Shop QA Portfolio

| Atributo     | Detalle |
| :----------- | :--- |
| **Archivo** | `08-genai-test-acceleration/00-core-config/context-rules.md` |
| **Propósito** | Contexto estático del proyecto: SUT, artefactos, trazabilidad y convenciones |
| **Versión** | **4.0 (Alineada 1:1 con Repositorio Final)** |
| **Estándar** | ISTQB CTFL v4.0 / CT-GenAI v1.1 / ISO/IEC/IEEE 29119-3 |

---

## 1. Sistema Bajo Prueba (SUT)

| Atributo | Detalle |
| :--------------- | :--- |
| **Proyecto** | Tricentis Demo Web Shop |
| **URL Base** | https://demowebshop.tricentis.com/ |
| **Arquitectura** | Web — Cliente/Servidor |
| **Dominio** | E-commerce B2C |
| **Alcance** | Validación funcional de caja negra — módulos: Búsqueda, Catálogo, Producto, Carrito, Registro, Login, Checkout |
| **Stakeholders** | Guest User: navegación, búsqueda, carrito. Registered User: login, checkout, historial de órdenes |
| **Entorno** | Windows 10 Pro / Firefox 150.0.1 (64-bit) |

### Out of Scope

- Backend: comunicación directa con APIs o microservicios
- Base de datos: integridad referencial o manipulación SQL
- Pagos reales: pasarelas de pago o transacciones bancarias
- Pruebas no funcionales: carga, estrés, seguridad profunda, accesibilidad

---

## 2. Stack de Herramientas

| Herramienta | Uso |
| :---------- | :--- |
| **VS Code** | Redacción de artefactos en Markdown (`.md`) |
| **GitHub** | Control de versiones e historial de auditoría |
| **ShareX** | Captura de evidencias visuales durante la ejecución |
| **Jira** | Registro y seguimiento de defectos — evidencia en `06-defect-management/jira-evidence/` |

### Convención de Nomenclatura de Evidencias

```text
YYYY-MM-DD_TX-XX.XX_Descripcion_Breve_ESTADO.png
```

**Ejemplo:** `2026-05-04_TX-01.01_Register_Submit_PASS.png`

**Regla:** Toda evidencia debe generarse con este formato. El archivo `test-environment-setup.md` es la fuente única de verdad para esta convención.

---

## 3. Estructura del Repositorio (1:1)

```text
istqb-manual-qa-ecommerce/
|-- 00-context-and-overview/
|   |-- 00-README.md
|   `-- system-under-test.md
|-- 01-test-planning/
|   `-- test-plan.md
|-- 02-test-analysis/
|   |-- 02-README.md
|   |-- requirements.md
|   |-- test-basis-evaluation.md
|   `-- test-conditions.md
|-- 03-test-design/
|   |-- 03-README.md
|   |-- test-cases.md
|   `-- test-data-requirements.md
|-- 04-test-implementation/
|   |-- 04-README.md
|   |-- test-environment-setup.md
|   |-- test-procedures.md
|   `-- test-suites.md
|-- 05-test-execution/
|   |-- 05-README.md
|   |-- decisions/
|   |   `-- edn-01-execution-decision-note.md
|   |-- test-evidence/
|   |   |-- jira-evidence/
|   |   |   |-- 2026-05-05_BUG-01_Jira-Issue.png
|   |   |   |-- 2026-05-05_BUG-02_Jira-Issue.png
|   |   |   `-- 2026-05-05_BUG-03_Jira-Issue.png
|   |   |-- ts-01-smoke-suite/
|   |   |   |-- 2026-05-04_TX-01.01_Register_Submit_PASS.png
|   |   |   |-- 2026-05-04_TX-01.02_Register_Success_PASS.png
|   |   |   |-- 2026-05-04_TX-01.03_Login_Fail_PASS.png
|   |   |   |-- 2026-05-04_TX-01.04_Login_Success_PASS.png
|   |   |   |-- 2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png
|   |   |   |-- 2026-05-05_TX-01.06_Search_Empty_PASS.png
|   |   |   |-- 2026-05-05_TX-01.07_Category_Nav_BUG-02.png
|   |   |   `-- 2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png
|   |   |-- ts-02-regression-suite/
|   |   |   |-- 2026-05-05_TX-02.01_Cart_Recalculate_PASS.png
|   |   |   |-- 2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png
|   |   |   `-- 2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png
|   |   `-- ts-03-e2e-suite/
|   |       `-- 2026-05-05_TX-03.01_Checkout_Success_PASS.png
|   |-- test-execution-summary.md
|   |-- test-execution-tracker.md
|   `-- test-logs/
|       |-- tl-01-smoke-log.md
|       |-- tl-02-regression-log.md
|       `-- tl-03-e2e-log.md
|-- 06-defect-management/
|   |-- bug-01-price-incoherence.md
|   |-- bug-02-capitalization-inconsistency.md
|   |-- bug-03-missing-sku-field.md
|   `-- defect-reports.md
|-- 07-test-completion/
|   |-- lessons-learned.md
|   `-- test-summary-report.md
|-- 08-genai-test-acceleration/
|   |-- 00-core-config/
|   |   |-- context-rules.md
|   |   |-- prompt-format-std.md
|   |   `-- system-prompt.md
|   |-- 01-planning-prompts/
|   |   |-- prompt-00-sut.md
|   |   `-- prompt-01-test-plan.md
|   |-- 02-analysis-prompts/
|   |   |-- prompt-02-requirements.md
|   |   |-- prompt-03-basis-evaluation.md
|   |   `-- prompt-04-test-conditions.md
|   |-- 03-design-prompts/
|   |   |-- prompt-05-test-cases.md
|   |   `-- prompt-06-test-data.md
|   |-- 04-implementation-prompts/
|   |   |-- prompt-07-environment.md
|   |   |-- prompt-08-procedures.md
|   |   `-- prompt-09-test-suites.md
|   |-- 05-execution-prompts/
|   |   |-- prompt-10-execution-decision.md
|   |   |-- prompt-11-execution-tracker.md
|   |   |-- prompt-12-test-logs.md
|   |   `-- prompt-13-execution-summary.md
|   |-- 06-defect-prompts/
|   |   |-- prompt-14-defect-reports.md
|   |   `-- prompt-15-individual-bugs.md
|   |-- 07-completion-prompts/
|   |   |-- prompt-16-lessons-learned.md
|   |   `-- prompt-17-summary-report.md
|   `-- README.md
|-- LICENSE
`-- README.md
```

## 4. Diccionario de Trazabilidad — "Hilo de Ariadna"

Cadena obligatoria en todo el portafolio:

```text
REQ → AC → TCND → TC → TD → TP → TS → TX → TL → BUG → TSR
```

Ningún artefacto puede existir sin referencia al artefacto de la fase anterior. **Regla: Zero Orphans.**

### Fase 1 — Planificación y Análisis

| Sigla | Elemento | Ubicación | Regla |
| :------------ | :------------------ | :--------------------- | :--- |
| **`RISK-XX`** | Product Risk | `01-test-planning/` | Informa prioridad de **`TCND`** y **`TC`** |
| **`REQ-XX`** | Requirement | `02-test-analysis/` | Origen absoluto. Sin **`REQ`** no existe ningún artefacto |
| **`AC-XX`** | Acceptance Criteria | `02-test-analysis/` | Deriva de **`REQ`**. Origina **`TCND`** |
| **`AN-XX`** | Anomalía Estática | `02-test-analysis/` | Referencia a **`REQ`** o **`AC`** con ambigüedad o defecto |
| **`TCND-XX`** | Test Condition | `02-test-analysis/` | Responde "¿Qué probar?". Vinculada a **`AC`** |

### Fase 2 — Diseño e Implementación

| Sigla | Elemento | Ubicación | Regla |
| :----------- | :-------------- | :------------------------ | :--- |
| **`TC-XX`** | Test Case | `03-test-design/` | Referencia obligatoria a **`TCND`** |
| **`TD-XX`** | Test Data | `03-test-design/` | Vinculado a **`TC`** |
| **`TP-XX`** | Test Procedure | `04-test-implementation/` | Secuencia lógica de ejecución. Referencia **`TC`** |
| **`TS-XX`** | Test Suite | `04-test-implementation/` | Agrupación: Smoke, Regression, E2E |

### Fase 3 — Ejecución y Cierre

| Sigla | Elemento | Ubicación | Regla |
| :------------- | :---------------------- | :----------------------------- | :--- |
| **`TX-XX.XX`** | Test Cycle | `05-test-execution/` | Registrado en `test-execution-tracker.md`. Estado: PASS / FAIL |
| **`TL-XX`** | Test Log | `05-test-execution/test-logs/` | Registro cronológico por suite. Referencia **`TX`** y evidencias |
| **`EDN-XX`** | Execution Decision Note | `05-test-execution/decisions/` | Se genera ante desviación de criterios de entrada de suite |
| **`BUG-XX`** | Defect Report | `06-defect-management/` | Referencia a **`TX`** y **`TC`**. Traza hacia **`REQ`** y **`AC`** |
| **`TSR`** | Test Summary Report | `07-test-completion/` | Consolida métricas del ciclo completo |
| **`LL`** | Lessons Learned | `07-test-completion/` | Retrospectiva del ciclo |

---

## 5. Riesgos del Producto

| ID | Descripción | Prioridad | Mitigación |
| :----------- | :-------------------------------------------------------------- | :-------- | :--- |
| **`RISK-01`** | Falla o inconsistencia en la búsqueda por coincidencia exacta | Alta | Cobertura **`TCND-01`**, **`TCND-02`** |
| **`RISK-02`** | Fallo funcional en la autenticación de usuarios | Alta | Cobertura **`TCND-08`**, **`TCND-10`** |
| **`RISK-03`** | Cálculo erróneo en totales del carrito | Crítica | BVA sobre **`TCND-05`** — **`TC-05`**, **`TC-10`** |
| **`RISK-04`** | Bloqueo en la generación del número de orden | Crítica | Flujo E2E **`TCND-09`** |

---

## 6. Criterios de Entrada y Salida

### Entry Criteria

| Suite | Criterio |
| :---------- | :--- |
| **`TS-01`** | Entorno configurado. Caché y cookies limpias. Cuenta **`TD-09`** pre-creada |
| **`TS-02`** | **`TS-01`** completada sin defectos Critical o High en estado Open |
| **`TS-03`** | **`TS-01`** completada sin defectos Critical o High en estado Open |

### Exit Criteria

| Criterio | Umbral |
| :------------------------------------ | :--- |
| TX planificados ejecutados | 100% |
| Pass Rate en **`TS-03`** (E2E) | ≥ 90% |
| Defectos Critical / High al cierre | 0 |
| Trazabilidad completa (Zero Orphans) | Verificada |

---

## 7. Convenciones de Formato

Estas convenciones aplican a todos los artefactos del portafolio sin excepción.

### Encabezado estándar de artefacto

Todo archivo `.md` del portafolio abre con esta tabla:

| Atributo | Detalle |
| :----------- | :--- |
| **Ubicación** | `ruta/exacta/del/archivo.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | X.X |
| **Fase STLC** | Nombre de la fase |
| **Estado** | ✅ Approved / 🔴 Open / 🟡 En revisión |
| **QA Owner** | Luis Adonais Malave Gamardo |

### IDs de artefactos

Siempre en negrita y código: **`TC-01`**, **`BUG-02`**, **`REQ-03`**, **`TX-01.05`**.

### Fechas

Formato ISO: `YYYY-MM-DD`. Ejemplo: `2026-05-04`.

### Redacción

- Pasos de prueba: modo imperativo (Ingresar / Hacer clic / Validar / Seleccionar)
- Resultados esperados: binarios — admiten exactamente un veredicto (PASS o FAIL)
- Sin bullets anidados. Sin notas de IA en versiones finales. Sin relleno.
- Secciones declarativas, no imperativas ("Los resultados son..." no "Describir los resultados...")

### Trazabilidad local

Cada artefacto cierra con una tabla de trazabilidad que conecta hacia la fase anterior y la siguiente.
