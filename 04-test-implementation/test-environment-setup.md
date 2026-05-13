
# Test Environment Setup

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `04-test-implementation/test-environment-setup.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.9 |
| **Fase STLC** | Test Implementation |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Infraestructura

| Componente | Especificación |
| :--- | :--- |
| **Sistema Operativo** | Windows 10 Pro |
| **Navegador** | Firefox 150.0.1 (64-bit) |
| **Estado del navegador** | Caché y cookies limpias antes de cada **`TS`** |
| **Conectividad** | Internet estándar — sin VPN ni proxy |
| **URL Base** | `https://demowebshop.tricentis.com/` |

---

## 2. Herramientas

| Herramienta | Uso |
| :--- | :--- |
| **VS Code** | Redacción de artefactos en Markdown |
| **GitHub** | Control de versiones y portafolio QA |
| **ShareX** | Captura de evidencias de ejecución |
| **Jira** | Registro y seguimiento de defectos — evidencia en `05-test-execution/jira-evidence/` |

**Nomenclatura de evidencias:**

```text
YYYY-MM-DD_TX-XX.XX_Descripcion_Breve_ESTADO.png
```

Ejemplo: `2026-05-04_TX-01.01_Register_Submit_PASS.png`

---

## 3. Preparación de datos

> Estos pasos son de configuración de entorno, no constituyen un ciclo **`TX`** formal.

1. Navegar a `https://demowebshop.tricentis.com/register`
2. Registrar cuenta con **`TD-09`** y **`TD-10`**
3. Verificar mensaje `"Your registration completed"`
4. Cerrar sesión antes de iniciar la suite

---

## 4. Estructura del repositorio

|-- 00-context-and-overview 
|   |-- 00-README.md        
|   `-- system-under-test.md
|-- 01-test-planning        
|   `-- test-plan.md        
|-- 02-test-analysis        
|   |-- 02-README.md        
|   |-- requirements.md     
|   |-- test-basis-evaluation.md
|   `-- test-conditions.md      
|-- 03-test-design
|   |-- 03-README.md
|   |-- test-cases.md
|   `-- test-data-requirements.md
|-- 04-test-implementation
|   |-- 04-README.md
|   |-- test-environment-setup.md
|   |-- test-procedures.md
|   `-- test-suites.md
|-- 05-test-execution
|   |-- 05-README.md
|   |-- decisions
|   |   `-- edn-01-execution-decision-note.md
|   |-- test-evidence
|   |   |-- jira-evidence
|   |   |   |-- 2026-05-05_BUG-01_Jira-Issue.png
|   |   |   |-- 2026-05-05_BUG-02_Jira-Issue.png
|   |   |   `-- 2026-05-05_BUG-03_Jira-Issue.png
|   |   |-- ts-01-smoke-suite
|   |   |   |-- 2026-05-04_TX-01.01_Register_Submit_PASS.png
|   |   |   |-- 2026-05-04_TX-01.02_Register_Success_PASS.png
|   |   |   |-- 2026-05-04_TX-01.03_Login_Fail_PASS.png
|   |   |   |-- 2026-05-04_TX-01.04_Login_Success_PASS.png
|   |   |   |-- 2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png
|   |   |   |-- 2026-05-05_TX-01.06_Search_Empty_PASS.png
|   |   |   |-- 2026-05-05_TX-01.07_Category_Nav_BUG-02.png
|   |   |   `-- 2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png
|   |   |-- ts-02-regression-suite
|   |   |   |-- 2026-05-05_TX-02.01_Cart_Recalculate_PASS.png
|   |   |   |-- 2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png
|   |   |   `-- 2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png
|   |   `-- ts-03-e2e-suite
|   |       `-- 2026-05-05_TX-03.01_Checkout_Success_PASS.png
|   |-- test-execution-summary.md
|   |-- test-execution-tracker.md
|   `-- test-logs
|       |-- tl-01-smoke-log.md
|       |-- tl-02-regression-log.md
|       `-- tl-03-e2e-log.md
|-- 06-defect-management
|   |-- bug-01-price-incoherence.md
|   |-- bug-02-capitalization-inconsistency.md
|   |-- bug-03-missing-sku-field.md
|   `-- defect-reports.md
|-- 07-test-completion
|   |-- lessons-learned.md
|   `-- test-summary-report.md
|-- 08-genai-test-acceleration
|   |-- 00-core-config
|   |   |-- context-rules.md
|   |   |-- prompt-format-std.md
|   |   `-- system-prompt.md
|   |-- 01-planning-prompts
|   |   |-- prompt-00-sut.md
|   |   `-- prompt-01-test-plan.md
|   |-- 02-analysis-prompts
|   |   |-- prompt-02-requirements.md
|   |   |-- prompt-03-basis-evaluation.md
|   |   `-- prompt-04-test-conditions.md
|   |-- 03-design-prompts
|   |   |-- prompt-05-test-cases.md
|   |   `-- prompt-06-test-data.md
|   |-- 04-implementation-prompts
|   |   |-- prompt-07-environment.md
|   |   |-- prompt-08-procedures.md
|   |   `-- prompt-09-test-suites.md
|   |-- 05-execution-prompts
|   |   |-- prompt-10-execution-decision.md
|   |   |-- prompt-11-execution-tracker.md
|   |   |-- prompt-12-test-logs.md
|   |   `-- prompt-13-execution-summary.md
|   |-- 06-defect-prompts
|   |   |-- prompt-14-defect-reports.md
|   |   `-- prompt-15-individual-bugs.md
|   |-- 07-completion-prompts
|   |   |-- prompt-16-lessons-learned.md
|   |   `-- prompt-17-summary-report.md
|   `-- README.md
|-- LICENSE
`-- README.md

---

## 5. Trazabilidad

| Requisito de entorno | **`TS`** dependiente | Estado |
| :--- | :--- | :--- |
| Caché y cookies limpias | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| Conexión a internet estándar | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| ShareX activo | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| Cuenta **`TD-09`** pre-creada | **`TS-02`**, **`TS-03`** | ✅ Ready |
| Jira configurado | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
