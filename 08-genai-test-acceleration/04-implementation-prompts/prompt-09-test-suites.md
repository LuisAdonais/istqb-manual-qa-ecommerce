
# prompt-09 — Test Suites

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/04-implementation-prompts/prompt-09-test-suites.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Implementation |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Descripción del artefacto

Una **Test Suite** (**`TS`**) es un conjunto de procedimientos de prueba agrupados para ser ejecutados en una sesión de prueba. Según ISTQB CTFL v4.0, es un *test implementation work product*. La organización en suites permite priorizar la ejecución por criticidad: Smoke → Regression → E2E.

**Función en el STLC:** Define el orden de ejecución y los criterios de entrada entre suites. Habilita la fase de ejecución.

**Datos que lo alimentan:** `test-procedures.md` aprobado, estrategia de priorización del Test Plan.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-08-procedures.md` completado.

### Instrucción

Construir la organización de suites en colaboración con el tester:

1. Agrupar los **`TP`** en suites según criticidad: **`TS-01`** Smoke / **`TS-02`** Regression / **`TS-03`** E2E.
2. Definir criterios de entrada para **`TS-02`** y **`TS-03`** basados en resultados de la suite anterior.
3. Validar con el tester la asignación de **`TP`** a cada suite antes de cerrar.

No asignar un **`TP`** a más de una suite salvo que el tester lo confirme explícitamente.

### Input data

```text
TP disponibles     : [lista de TP-XX con TC cubiertos]
Estrategia         : [Smoke → Regression → E2E]
Por cada TS el tester confirma:
  TP incluidos     : [TP-XX, TP-XX]
  Criterio entrada : [condición para iniciar esta suite]
  Criterio salida  : [condición para considerar la suite completa]
```

### Constraints

- IDs: **`TS-01`**, **`TS-02`**, **`TS-03`**.
- Criterios de entrada basados en severidad de defectos — no solo en porcentaje de PASS.
- Cada **`TS`** referencia sus **`TP`**.

### Output format

```markdown
# Test Suites

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `04-test-implementation/test-suites.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Implementation |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## **`TS-01`** — Smoke Suite

| **`TP`** incluidos | **`TC`** cubiertos | Prioridad |
| :--- | :--- | :--- |
| **`TP-XX`** | **`TC-XX`** | Alta |

**Criterio de entrada:** [condición]  
**Criterio de salida:** [condición basada en severidad]

## **`TS-02`** — Regression Suite

[mismo formato]

## **`TS-03`** — E2E Suite

[mismo formato]

## Trazabilidad

| **`TS`** | **`TP`** | **`TC`** | **`TCND`** |
| :--- | :--- | :--- | :--- |
| **`TS-XX`** | **`TP-XX`** | **`TC-XX`** | **`TCND-XX`** |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-09-test-suites.md` | `prompt-10-execution-decision.md` |