
# prompt-08 — Test Procedures

| Atributo      | Detalle                                                                 |
| :---          | :---                                                                    |
| **Ubicación** | `08-genai-test-acceleration/04-implementation-prompts/prompt-08-procedures.md` |
| **Proyecto**  | Tricentis Demo Web Shop                                                 |
| **Versión**   | 1.0                                                                     |
| **Fase STLC** | Test Implementation                                                     |
| **Técnica GenAI** | Prompt chaining · Meta-prompting · HITL iterativo                   |
| **Referencia**    | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2                                  |

## Descripción del artefacto

Un **Test Procedure** (**`TP`**) es la secuencia ordenada de pasos para ejecutar un grupo de casos de prueba relacionados. Según ISTQB CTFL v4.0, es un *test implementation work product* que organiza los **`TC`** para su ejecución eficiente dentro de una suite.

**Función en el STLC:** Organiza los **`TC`** en un flujo ejecutable con dependencias explícitas. Cada paso tiene exactamente un resultado esperado binario.

**Datos que lo alimentan:** `test-cases.md` y `test-data-requirements.md` aprobados.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-06-test-data.md` completado.

### Instrucción

Construir los procedimientos de prueba en colaboración con el tester:

1. Agrupar los **`TC`** relacionados en procedimientos lógicos.
2. Por cada **`TP`**, definir precondición, pasos ordenados con **`TD`** referenciados y resultado esperado por paso.
3. Verificar con el tester que cada resultado esperado es binariamente verificable.
4. Máximo 1 **`TP`** por intercambio — validar antes de continuar.

Un paso = una acción. Si el resultado esperado usa "o", dividir en dos pasos.

### Input data

```text
TC a agrupar       : [lista de TC-XX con su TCND]
TD disponibles     : [lista de TD-XX]
Por cada TP el tester confirma:
  TC incluidos     : [TC-XX, TC-XX]
  Precondición     : [estado del sistema]
  Orden de pasos   : [secuencia lógica]
```

### Constraints

- Voz imperativa en todos los pasos.
- IDs: **`TP-01`**, **`TP-02`**…
- Cada **`TP`** referencia sus **`TC`**.
- Sin conectores "o" en resultados esperados.

### Output format

```markdown
## **`TP-01`** — [nombre descriptivo]

| Atributo              | Detalle                 |
| :---                  | :---                    |
| **`TC`** cubiertos    | **`TC-XX`**, **`TC-XX`**|
| **Precondición**      | [estado inicial]        |

| Paso | Acción             | **`TD`**    | Resultado Esperado     |
| :--- | :---               | :---        | :---                  |
| 1    | [acción imperativa]| **`TD-XX`** | [resultado binario]    |
| N    | [acción imperativa]| —           | [resultado binario]    |
```

## Trazabilidad

| Este prompt                | Alimenta                   |
| :---                       | :---                       |
| `prompt-08-procedures.md`  | `prompt-09-test-suites.md` |

---