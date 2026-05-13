
# prompt-11 — Execution Tracker

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/05-execution-prompts/prompt-11-execution-tracker.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Execution |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Descripción del artefacto

El **Test Execution Tracker** registra el estado de cada ciclo de ejecución (**`TX`**). Según ISTQB CTFL v4.0, el test monitoring implica el chequeo continuo de todas las actividades de prueba y la comparación del progreso real contra el plan.

**Función en el STLC:** Panel de control de ejecución. Permite identificar de inmediato qué **`TX`** pasaron, fallaron o están pendientes, y qué **`BUG`** se abrieron.

**Datos que lo alimentan:** `test-suites.md` aprobado — lista de **`TX`** planificados. El tester actualiza estado y referencias a **`BUG`** tras cada ejecución.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-09-test-suites.md` completado.

### Instrucción

Construir el tracker en colaboración con el tester:

1. Generar la tabla de **`TX`** planificados a partir de los **`TP`** de cada **`TS`**.
2. Estado inicial de todos los **`TX`**: `PENDING`.
3. El tester actualiza estado (**`PASS`** / **`FAIL`** / **`PENDING`**) y referencia a **`BUG`** tras cada sesión de ejecución.
4. Actualizar el tracker en cada intercambio sin reescribir filas ya cerradas.

### Input data

```text
TS y TP planificados: [lista de TS-XX → TP-XX → TC-XX]
Por cada TX el tester provee tras ejecución:
  ID ciclo         : TX-XX.XX (suite.secuencia)
  TC ejecutado     : [TC-XX]
  Fecha ejecución  : [YYYY-MM-DD]
  Estado           : [PASS / FAIL]
  BUG referenciado : [BUG-XX o —]
```

### Constraints

- IDs: **`TX-01.01`**, **`TX-01.02`**… por suite.
- Estado inicial siempre `PENDING`.
- Cada **`TX`** con estado `FAIL` debe referenciar un **`BUG`**.

### Output format

```markdown
# Test Execution Tracker

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/test-execution-tracker.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Execution |
| **Estado** | En progreso |
| **QA Owner** | [nombre] |

## **`TS-01`** — Smoke Suite

| **`TX`** | **`TC`** | Fecha | Estado | **`BUG`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TX-01.01`** | **`TC-XX`** | [fecha] | PENDING | — |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-11-execution-tracker.md` | `prompt-12-test-logs.md` · `prompt-14-defect-reports.md` |

---