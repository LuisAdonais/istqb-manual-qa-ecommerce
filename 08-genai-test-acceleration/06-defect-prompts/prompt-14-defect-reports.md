
# prompt-14 — Defect Reports (consolidado)

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/06-defect-prompts/prompt-14-defect-reports.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Defect Management |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Descripción del artefacto

El artefacto **Defect Reports** consolida todos los defectos detectados durante la ejecución en una tabla de resumen trazable. Según ISTQB CTFL v4.0, un defect report es un *test execution work product* que provee información suficiente para resolver el defecto, rastrear la calidad del producto y mejorar el proceso.

**Función en el STLC:** Vista consolidada de todos los **`BUG`** del ciclo. Cada fila apunta al reporte individual del defecto.

**Datos que lo alimentan:** Test logs (**`TL`**) con **`TX`** en estado FAIL y referencias a **`BUG`**.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-12-test-logs.md` completado.

### Instrucción

Construir la tabla consolidada de defectos en colaboración con el tester:

1. Por cada **`TX`** con estado FAIL, solicitar al tester los datos del defecto.
2. Registrar cada **`BUG`** con referencia al **`TX`**, **`TC`** y **`REQ`** afectados.
3. Validar severidad y prioridad con el tester antes de cerrar cada entrada.

### Input data

```text
Por cada BUG el tester provee:
  TX origen        : [TX-XX.XX]
  TC fallado       : [TC-XX]
  REQ afectado     : [REQ-XX]
  Título           : [descripción breve del defecto]
  Severidad        : [Critical / High / Medium / Low]
  Prioridad        : [Alta / Media / Baja]
  Estado           : [Open]
```

### Constraints

- IDs: **`BUG-01`**, **`BUG-02`**…
- Cada **`BUG`** referencia obligatoriamente **`TX`**, **`TC`** y **`REQ`**.
- No cerrar defectos sin confirmación del tester.

### Output format

```markdown
# Defect Reports

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `06-defect-management/defect-reports.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Defect Management |
| **Estado** | En seguimiento |
| **QA Owner** | [nombre] |

## Resumen de defectos

| **`BUG`** | Título | Severidad | Prioridad | **`TX`** | **`TC`** | **`REQ`** | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | [título] | [severidad] | [prioridad] | **`TX-XX.XX`** | **`TC-XX`** | **`REQ-XX`** | Open |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-14-defect-reports.md` | `prompt-15-individual-bugs.md` |

---