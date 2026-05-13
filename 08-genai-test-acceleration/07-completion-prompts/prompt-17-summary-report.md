
# prompt-17 — Test Summary Report

| Atributo      | Detalle                                                                         |
| :---          | :---                                                                            |
| **Ubicación** | `08-genai-test-acceleration/07-completion-prompts/prompt-17-summary-report.md`  |
| **Proyecto**  | Tricentis Demo Web Shop                                                         |
| **Versión**   | 1.0                                                                             |
| **Fase STLC** | Test Completion                                                                 |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo                        |
| **Referencia**    | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.4                            |

## Descripción del artefacto

El **Test Summary Report** es el documento de cierre del ciclo de prueba. Según ISTQB CTFL v4.0, es un *test completion work product* que consolida: resumen de actividades, desviaciones del plan, métricas, evaluación de criterios de salida, riesgos residuales y trazabilidad de artefactos. Se comunica a los stakeholders.

**Función en el STLC:** Cierre formal del ciclo. Resume el estado de calidad del producto para la toma de decisión de liberación.

**Datos que lo alimentan:** Todos los artefactos del ciclo — especialmente `test-execution-summary.md`, `defect-reports.md` y `lessons-learned.md`.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-16-lessons-learned.md` completado.

### Instrucción

Construir el `test-summary-report.md` en colaboración con el tester:

1. Consolidar datos de todas las fases del ciclo.
2. Evaluar exit criteria contra resultados reales.
3. Documentar riesgos residuales con plan de acción.
4. Presentar al tester para validación sección por sección.
5. Máximo 2 secciones por intercambio.

No asumir decisión de liberación sin confirmación explícita del tester.

### Input data

```text
Periodo del ciclo  : [fecha inicio — fecha fin]
TX totales         : [número]
PASS / FAIL        : [número / número]
Defectos abiertos  : [BUG-XX — severidad — plan]
Exit criteria      : [referencia a test-plan.md + resultado real]
Desviaciones (EDN) : [EDN-XX o ninguna]
Decisión release   : [Aprobado / Condicionado / Rechazado]
```

### Constraints

- Evaluación de exit criteria debe mostrar umbral vs. resultado real.
- Riesgos residuales solo con **`BUG`** abiertos — no inventar riesgos.
- Trazabilidad de artefactos cubre todas las fases del STLC.
- Estado final: `Completado` solo con confirmación del tester.

### Output format

```markdown
# Test Summary Report

| Atributo      | Detalle                                                            |
| :---          | :---                                                               |
| **Ubicación** | `07-test-completion/test-summary-report.md`                        |
| **Proyecto**  | [nombre]                                                           |
| **Versión**   | [x.x]                                                              |
| **Fase STLC** | Test Completion                                                    |
| **Periodo**   | [fecha inicio] — [fecha fin]                                       |
| **Estado**    | Completado                                                         |
| **QA Owner**  | [nombre]                                                           |

## 1. Resumen Ejecutivo

[párrafo breve — qué se probó, qué se encontró, decisión]

## 2. Alcance Ejecutado

[módulos probados con referencia a REQ]

## 3. Métricas de Ejecución

| Indicador                      | Valor   |
| :---                           | :---    |
| Total **`TX`** ejecutados      | [n]     |
| PASS                           | [n]     |
| FAIL                           | [n]     |
| Pass Rate global               | [%]     |
| Defectos detectados            | [n]     |

## 4. Evaluación de Exit Criteria

| Criterio           | Umbral   | Resultado | Estado      |
| :---               | :---     | :---      | :---        |
| [criterio]         | [umbral] | [real]    | ✅ / ❌      |

## 5. Desviaciones al Plan

| **`EDN`**  | Suite afectada  | Decisión    |
| :---       | :---            | :---        |
| **`EDN-XX`** | **`TS-XX`**   | [decisión]  |

## 6. Defectos Abiertos al Cierre

| **`BUG`**    | Severidad   | Módulo     | Plan         |
| :---         | :---        | :---       | :---         |
| **`BUG-XX`** | [severidad] | [módulo]   | [plan]       |

## 7. Riesgos Residuales

| **`BUG`**    | Módulo     | Riesgo de negocio | Plan         |
| :---         | :---       | :---              | :---         |
| **`BUG-XX`** | [módulo]   | [descripción]     | [plan]       |

## 8. Trazabilidad de Artefactos

| Fase               | Artefactos                                                       | Estado            |
| :---               | :---                                                             | :---              |
| Test Analysis      | `requirements.md`, `test-basis-evaluation.md`, `test-conditions.md` | ✅ Approved    |
| Test Design        | `test-cases.md`, `test-data-requirements.md`                        | ✅ Approved    |
| Test Implementation| `test-procedures.md`, `test-suites.md`, `test-environment-setup.md`| ✅ Approved    |
| Test Execution     | `TL-01`, `TL-02`, `TL-03`, `test-execution-tracker.md`             | ✅ Completado  |
| Defect Management  | [BUG-XX]                                                           | 🔴 Open        |
| Test Completion    | `test-summary-report.md`, `lessons-learned.md`                     | ✅ Completado  |
```

## Trazabilidad

| Este prompt                  | Cierra cadena                                    |
| :---                         | :---                                             |
| `prompt-17-summary-report.md`| Fin del ciclo — Zero Orphans verificado          |