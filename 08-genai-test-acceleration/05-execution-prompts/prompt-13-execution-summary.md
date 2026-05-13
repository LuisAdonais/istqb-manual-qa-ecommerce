
# prompt-13 — Execution Summary

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/05-execution-prompts/prompt-13-execution-summary.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Execution |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Descripción del artefacto

El **Test Execution Summary** consolida los resultados de todas las suites ejecutadas. Según ISTQB CTFL v4.0, el test monitoring produce *test progress reports* que comparan el progreso real contra el plan.

**Función en el STLC:** Cierra la fase de ejecución con métricas consolidadas. Alimenta el Test Summary Report de la fase de completion.

**Datos que lo alimentan:** Los tres **`TL`** completados y el execution tracker actualizado.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-12-test-logs.md` completado para las tres suites.

### Instrucción

Consolidar los resultados de ejecución en colaboración con el tester:

1. Calcular métricas por suite: total **`TX`**, PASS, FAIL, PENDING, pass rate.
2. Listar defectos abiertos con severidad.
3. Evaluar si se cumplieron los exit criteria del Test Plan.
4. Presentar al tester para validación antes de cerrar.

### Input data

```text
TL completados: [TL-01, TL-02, TL-03]
Por cada suite:
  Total TX: [número]
  PASS: [número]
  FAIL: [número]
  PENDING: [número]
BUG abiertos: [BUG-XX — severidad]
Exit criteria del plan: [referencia a test-plan.md]
```

### Constraints

- Pass rate = (PASS / Total TX) × 100.
- Evaluar exit criteria contra los umbrales del Test Plan — no asumir cumplimiento.
- Encabezado con Estado `Completado` solo si el tester lo confirma.

### Output format

```markdown
# Test Execution Summary

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/test-execution-summary.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Execution |
| **Estado** | Completado |
| **QA Owner** | [nombre] |

## Resultados por suite

| **`TS`** | Total **`TX`** | PASS | FAIL | PENDING | Pass Rate |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`TS-01`** | [n] | [n] | [n] | [n] | [%] |

## Defectos detectados

| **`BUG`** | Severidad | Módulo | Estado |
| :--- | :--- | :--- | :--- |
| **`BUG-XX`** | [severidad] | [módulo] | Open |

## Evaluación de exit criteria

| Criterio | Umbral | Resultado | Estado |
| :--- | :--- | :--- | :--- |
| [criterio del plan] | [umbral] | [valor real] | ✅ / ❌ |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-13-execution-summary.md` | `prompt-16-lessons-learned.md` · `prompt-17-summary-report.md` |

---