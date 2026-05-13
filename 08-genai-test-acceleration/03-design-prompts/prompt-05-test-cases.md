
# prompt-05 — Test Cases

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/03-design-prompts/prompt-05-test-cases.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Design |
| **Técnica GenAI** | Prompt chaining · Structured prompt · Meta-prompting · HITL |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.2 |

## Descripción del artefacto

Un **Test Case** es un conjunto de precondiciones, entradas, acciones, resultados esperados y postcondiciones, desarrollado para cubrir un objetivo de prueba específico. Según ISTQB CTFL v4.0, es un *test design work product* que responde a "¿cómo probar?" la condición de prueba.

**Función en el STLC:** Operacionaliza cada **`TCND`** en pasos ejecutables con resultado esperado binario.

**Datos que lo alimentan:** `test-conditions.md` aprobado, técnicas de diseño del Test Plan (**`EP`**, **`BVA`**, **`State Transition`**, **`Error Guessing`**), datos de prueba preliminares.

---

## Prompt

> [!TIP]
> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-04-test-conditions.md` completado.

### Instrucción

Generar los casos de prueba en colaboración con el tester:

1. Por cada **`TCND`**, proponer el **`TC`** correspondiente con precondición, pasos y resultado esperado.
2. Identificar la técnica de diseño aplicada (**`EP`** / **`BVA`** / **`State Transition`** / **`Error Guessing`**).
3. Presentar al tester para validación de pasos y resultado esperado antes de continuar.
4. Máximo 3 TC por intercambio.

Un paso = una acción. Resultado esperado = binariamente verificable. Sin términos subjetivos.

### Input data

```text
TCND aprobados     : [lista de TCND]
Técnicas del plan  : [EP / BVA / State Transition / Error Guessing]
Por cada TC el tester confirma:
  Precondición     : [estado del sistema antes del paso 1]
  Pasos            : [acción imperativa — una por línea]
  Resultado esperado: [observable y binario]
  Técnica          : [EP / BVA / ST / EG]
  Prioridad        : [Alta / Media / Crítica]
```

### Constraints

- Voz imperativa en todos los pasos: "Ingresar", "Hacer clic en", "Validar".
- IDs secuenciales: **`TC-01`**, **`TC-02`**…
- Cada **`TC`** referencia obligatoriamente su **`TCND`**.
- No agregar observaciones de arquitectura ni análisis de riesgo empresarial.

### Output format

```markdown
## **`TC-01`** — [nombre descriptivo]

| Atributo | Detalle |
| :--- | :--- |
| **`TCND`** | **`TCND-XX`** |
| **Técnica** | [EP / BVA / ST / EG] |
| **Prioridad** | [prioridad] |
| **Precondición** | [estado inicial] |

| Paso | Acción | Resultado Esperado |
| :--- | :--- | :--- |
| 1 | [acción imperativa] | [resultado binario] |
| N | [acción imperativa] | [resultado binario] |

**Postcondición:** [estado del sistema tras el último paso]
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-05-test-cases.md` | `prompt-06-test-data.md` · `prompt-08-procedures.md` |

---