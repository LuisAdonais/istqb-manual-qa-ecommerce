
# prompt-10 — Execution Decision Note

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/05-execution-prompts/prompt-10-execution-decision.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Execution |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Descripción del artefacto

La **Execution Decision Note** (**`EDN`**) documenta una desviación formal de los criterios de entrada de una suite. Según ISTQB CTFL v4.0, el test control implica tomar las acciones necesarias cuando los objetivos de prueba no se alcanzan según el plan — lo que incluye documentar decisiones de continuación ante criterios no cumplidos.

**Función en el STLC:** Evita el bloqueo innecesario del ciclo ante defectos de baja severidad. Formaliza la decisión y la hace trazable.

**Datos que lo alimentan:** Criterios de entrada de `test-suites.md`, resultados parciales de la suite anterior, decisión del QA Lead.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-09-test-suites.md` completado.

### Instrucción

Generar el artefacto **`EDN-XX`** solo cuando el tester confirme que un criterio de entrada no se ha cumplido y se decide continuar de todas formas:

1. Registrar el criterio de entrada incumplido con referencia a `test-suites.md`.
2. Documentar los defectos abiertos que motivaron la desviación con su severidad.
3. Registrar la justificación y la decisión del QA Lead.
4. No generar este artefacto si los criterios de entrada se cumplen.

### Input data

```text
Suite afectada     : [TS-XX]
Criterio incumplido: [descripción del criterio de test-suites.md]
Defectos abiertos  : [BUG-XX — severidad — módulo]
Justificación      : [razón para continuar]
Decisión           : [continuar / pausar / ajustar alcance]
Autoriza           : [QA Owner]
```

### Constraints

- IDs: **`EDN-01`**, **`EDN-02`**…
- Solo se genera ante desviación confirmada por el tester.
- Referencia obligatoria al criterio de entrada de `test-suites.md`.

### Output format

```markdown
# Execution Decision Note — **`EDN-XX`**

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/EDN-XX_Execution-Decision-Note.md` |
| **Suite afectada** | **`TS-XX`** |
| **Fecha** | [YYYY-MM-DD] |
| **QA Owner** | [nombre] |

## Situación

**Criterio de entrada incumplido:** [descripción]  
**Referencia:** `test-suites.md` — **`TS-XX`**

## Defectos Abiertos

| **`BUG`** | Severidad | Módulo |
| :--- | :--- | :--- |
| **`BUG-XX`** | [severidad] | [módulo] |

## Decisión

**Justificación:** [razón]  
**Decisión:** [continuar / pausar / ajustar]  
**Autoriza:** [nombre del QA Owner]
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-10-execution-decision.md` | `prompt-11-execution-tracker.md` |

---