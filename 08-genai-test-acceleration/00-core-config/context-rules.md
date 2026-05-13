
# CONTEXTO Y REGLAS — Tricentis Demo Web Shop QA Portfolio

| Atributo      | Detalle                                                                                     |
| :------------ | :------------------------------------------------------------------------------------------ |
| **Archivo**   | `08-genai-test-acceleration/00-core-config/context-rules.md`                                |
| **Propósito** | Contexto estático y reglas: SUT, artefactos, trazabilidad, convenciones, estándares         |
| **Versión**   | 4.0 (alineación 1:1 repositorio)                                                            |
| **Estándar**  | ISTQB CTFL v4.0 · CT-GenAI v1.1 · ISO/IEC/IEEE 29119-3                                      |

---

## 1. Sistema Bajo Prueba (SUT)

| Atributo         | Detalle                                                                   |
| :--------------- | :------------------------------------------------------------------------ |
| **Proyecto**     | Tricentis Demo Web Shop                                                   |
| **URL Base**     | https://demowebshop.tricentis.com/                                        |
| **Arquitectura** | Web (Cliente/Servidor)                                                    |
| **Dominio**      | E-commerce B2C                                                            |
| **Alcance**      | Prueba funcional caja negra: búsqueda, catálogo, producto, carrito, registro, login, checkout |
| **Stakeholders** | Guest: navegación, búsqueda, carrito. Registered: login, checkout, historial de órdenes         |
| **Entorno**      | Windows 10 Pro / Firefox 150.0.1 (64-bit)                                 |

**Fuera de alcance:**

- Backend, APIs
- Base de datos (SQL)
- Pagos reales, pasarelas bancarias
- Performance, seguridad, accesibilidad (no funcional)

---

## 2. Stack de Herramientas

| Herramienta  | Uso                                                      |
| :----------- | :------------------------------------------------------- |
| VS Code      | Documentación (`.md`)                                    |
| GitHub       | Control de versiones                                     |
| ShareX       | Evidencia visual                                         |
| Jira         | Defectos/evidencias en `06-defect-management/jira-evidence/` |

**Convención nombres evidencia:**

```text
YYYY-MM-DD_TX-XX.XX_Descripcion_Breve_ESTADO.png
```
Ejemplo: `2026-05-04_TX-01.01_Register_Submit_PASS.png`

- Usar siempre este formato para evidencia.
- Ante duda, consultar `test-environment-setup.md` (sujeto a prevalencia).

---

## 3. Estructura 1:1 de Repositorio

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

---

## 4. Diccionario de Trazabilidad

Cadena de trazabilidad obligatoria:  
```text
REQ → AC → TCND → TC → TD → TP → TS → TX → TL → BUG → TSR
```
Ningún artefacto sin referencia previa (Zero Orphans).

### Fase 1: Planificación & Análisis

| Sigla        | Elemento             | Carpeta                      | Regla                                         |
| :----------- | :------------------- | :---------------------------| :---------------------------------------------|
| **`RISK-XX`**| Riesgo de Producto   | `01-test-planning/`          | Prioriza **`TCND`** y **`TC`**                |
| **`REQ-XX`** | Requisito           | `02-test-analysis/`          | Sin **`REQ`**: no artefactos derivados        |
| **`AC-XX`**  | Acceptance Criteria | `02-test-analysis/`          | Derivado de **`REQ`**, fuente de **`TCND`**   |
| **`AN-XX`**  | Anomalía Estática   | `02-test-analysis/`          | Refiere **`REQ`**/**`AC`** defectuosos        |
| **`TCND-XX`**| Test Condition      | `02-test-analysis/`          | "¿Qué probar?". Relación directa a **`AC`**   |

### Fase 2: Diseño e Implementación

| Sigla         | Elemento            | Carpeta                       | Regla                                |
| :------------ | :------------------ | :----------------------------| :----------------------------------- |
| **`TC-XX`**   | Test Case           | `03-test-design/`             | Debe referenciar a **`TCND`**        |
| **`TD-XX`**   | Test Data           | `03-test-design/`             | Asociado a **`TC`**                  |
| **`TP-XX`**   | Test Procedure      | `04-test-implementation/`     | Ejecuta lógica de **`TC`**           |
| **`TS-XX`**   | Test Suite          | `04-test-implementation/`     | Agrupa: Smoke, Regression, E2E       |

### Fase 3: Ejecución & Cierre

| Sigla           | Elemento                 | Carpeta                           | Regla                                        |
| :-------------- | :----------------------- | :---------------------------------| :------------------------------------------- |
| **`TX-XX.XX`**  | Test Cycle               | `05-test-execution/`              | En `test-execution-tracker.md`, PASS/FAIL    |
| **`TL-XX`**     | Test Log                 | `05-test-execution/test-logs/`    | Cronológico; referencia a **`TX`** y evidencia|
| **`EDN-XX`**    | Execution Decision Note  | `05-test-execution/decisions/`    | Se emite por desviación entrada de suite     |
| **`BUG-XX`**    | Defect Report            | `06-defect-management/`           | Ref **`TX`** y **`TC`**; traza a **`REQ/AC`**|
| **`TSR`**       | Test Summary Report      | `07-test-completion/`             | Resumen/ métricas ciclo                      |
| **`LL`**        | Lessons Learned          | `07-test-completion/`             | Retrospectiva                                |

---

## 5. Principales Riesgos del Producto

| ID            | Descripción                                    | Prioridad | Mitigación                            |
| :------------ | :--------------------------------------------- | :-------- | :------------------------------------ |
| **`RISK-01`** | Falla en búsqueda exacta                       | Alta      | Cubierto por **`TCND-01`**, **`TCND-02`**  |
| **`RISK-02`** | Fallo en autenticación                         | Alta      | Cubierto por **`TCND-08`**, **`TCND-10`**  |
| **`RISK-03`** | Error cálculo totales carrito                  | Crítica   | BVA en **`TCND-05`**, **`TC-05`**, **`TC-10`** |
| **`RISK-04`** | Bloqueo generación número de orden             | Crítica   | E2E en **`TCND-09`**                       |

---

## 6. Criterios de Entrada y Salida

### Criterios de Entrada

| Suite         | Criterio                                                         |
| :------------ | :--------------------------------------------------------------- |
| **`TS-01`**   | Entorno listo, caché y cookies limpios, cuenta **`TD-09`** creada|
| **`TS-02`**   | **`TS-01`** finalizado, sin defectos críticos/altos abiertos     |
| **`TS-03`**   | **`TS-01`** finalizado, sin defectos críticos/altos abiertos     |

### Criterios de Salida

| Criterio                                    | Umbral     |
| :------------------------------------------- | :--------- |
| TX ejecutados vs plan                        | 100%       |
| Pass Rate en **`TS-03`** (E2E)               | ≥ 90%      |
| Defectos críticos/altos abiertos al cierre   | 0          |
| Trazabilidad global (Zero Orphans)           | Verificado |

---

## 7. Convenciones de Formato

Las siguientes reglas aplican a todos los artefactos `.md`:

### Encabezado estándar

Todo archivo inicia con:

| Atributo      | Detalle                               |
| :------------ | :------------------------------------|
| **Ubicación** | `ruta/exacta/del/archivo.md`          |
| **Proyecto**  | Tricentis Demo Web Shop               |
| **Versión**   | X.X                                  |
| **Fase STLC** | Nombre de la fase                     |
| **Estado**    | ✅ Approved / 🔴 Open / 🟡 En revisión |
| **QA Owner**  | Luis Adonais Malave Gamardo           |

### IDs

Formateo obligatorio: negrita y monoespaciado, ej: **`TC-01`**, **`BUG-02`**, **`REQ-03`**, **`TX-01.05`**.

### Fechas

Formato ISO: `YYYY-MM-DD` (ej: `2026-05-04`).

### Redacción

- Pasos: voz imperativa (Ingresar, Hacer clic, Validar, Seleccionar)
- Resultados: juicio binario (PASS o FAIL)
- Sin bullets anidados, sin notas IA, sin relleno
- Estilo declarativo, no instrucciones al redactor

### Trazabilidad local

Cada artefacto cierra con una tabla de trazabilidad enlazando con la fase anterior y la siguiente.
