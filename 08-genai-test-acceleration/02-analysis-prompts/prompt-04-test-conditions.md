
# prompt-04 — Test Conditions

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/02-analysis-prompts/prompt-04-test-conditions.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Analysis |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Descripción del artefacto

Las **Test Conditions** son afirmaciones atómicas derivadas de los **`AC`** aprobados que responden a "¿qué debe ser verificado?". Según ISTQB CTFL v4.0, una condición de prueba es un aspecto del objeto de prueba que puede ser verificado por uno o más casos de prueba.

**Función en el STLC:** Puente entre análisis y diseño. Cada **`TCND`** origina uno o más **`TC`**.

**Datos que lo alimentan:** `requirements.md` y `test-basis-evaluation.md` aprobados.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-03-basis-evaluation.md` completado.

### Instrucción

Derivar las condiciones de prueba del artefacto `requirements.md` en colaboración con el tester:

1. Por cada **`AC`** aprobado, generar la condición de prueba atómica correspondiente.
2. Asignar prioridad basada en riesgos del Test Plan.
3. Presentar al tester para validación antes de continuar con el siguiente bloque de **`AC`**.
4. Máximo 5 condiciones por intercambio.

Una condición = un aspecto verificable. No combinar dos verificaciones en una sola **`TCND`**.

### Input data

```text
AC aprobados       : [lista de AC de requirements.md]
Riesgos del plan   : [RISK-XX → módulo afectado]
Por cada TCND el tester confirma:
  Condición        : [afirmación verificable — "Validar que..."]
  Prioridad        : [Alta / Media / Crítica]
  RISK asociado    : [RISK-XX o —]
```

### Constraints

- Redactar en formato: "Validar que [comportamiento observable]."
- IDs secuenciales: **`TCND-01`**, **`TCND-02`**…
- Cada **`TCND`** referencia un único **`AC`**.
- No incluir pasos de prueba — eso corresponde a **`TC`**.

### Output format

```markdown
# Test Conditions

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `02-test-analysis/test-conditions.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Analysis |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## 1. Condiciones de Prueba (`TCND`)

| ID | **`AC`** | Condición de Prueba | Prioridad | **`RISK`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TCND-01`** | **`AC-01`** | Validar que [comportamiento]. | Alta | **`RISK-XX`** |

## 2. Trazabilidad

| **`REQ`** | **`AC`** | **`TCND`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-XX`** | **`AC-XX`** | **`TCND-XX`** | **`RISK-XX`** |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-04-test-conditions.md` | `prompt-05-test-cases.md` |

---