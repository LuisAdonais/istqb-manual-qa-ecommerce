
# prompt-12 — Test Logs

| Atributo      | Detalle                                                                |
| :---          | :---                                                                   |
| **Ubicación** | `08-genai-test-acceleration/05-execution-prompts/prompt-12-test-logs.md` |
| **Proyecto**  | Tricentis Demo Web Shop                                                |
| **Versión**   | 1.0                                                                    |
| **Fase STLC** | Test Execution                                                         |
| **Técnica GenAI** | Structured prompt · HITL iterativo                                 |
| **Referencia**    | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4                                 |

## Descripción del artefacto

Un **Test Log** (**`TL`**) es el registro cronológico de todos los eventos ocurridos durante una sesión de ejecución. Según ISTQB CTFL v4.0, es un *test execution work product* que documenta qué ocurrió durante la ejecución, incluyendo resultados reales y evidencias.

**Función en el STLC:** Proporciona trazabilidad de ejecución detallada por suite. Es la fuente de evidencia para el Test Summary Report.

**Datos que lo alimentan:** Resultados del execution tracker, evidencias capturadas según la convención de `test-environment-setup.md`.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-11-execution-tracker.md` actualizado.

### Instrucción

Generar un **`TL`** por suite en colaboración con el tester:

1. Por cada **`TX`** ejecutado, registrar: acción, resultado real, evidencia referenciada y estado.
2. Si el resultado real difiere del esperado, marcar `FAIL` y solicitar al tester el ID del **`BUG`** a referenciar.
3. Un log por suite — no mezclar **`TX`** de diferentes suites en el mismo **`TL`**.

### Input data

```text
Suite a loggear    : [TS-XX]
Por cada TX el tester provee:
  TX ID            : [TX-XX.XX]
  Resultado real   : [descripción observable]
  Evidencia        : [nombre del archivo según convención]
  Estado           : [PASS / FAIL]
  BUG              : [BUG-XX o —]
```

### Constraints

- IDs: **`TL-01`**, **`TL-02`**, **`TL-03`** (uno por suite).
- Nombre de evidencia debe seguir la convención de `test-environment-setup.md`.
- No registrar pasos de preparación de entorno como **`TX`**.

### Output format

```markdown
# Test Log — **`TL-XX`** — [nombre de suite]

| Atributo   | Detalle                                            |
| :---       | :---                                               |
| **Ubicación** | `05-test-execution/test-logs/TL-XX-[suite]-log.md` |
| **Suite**     | **`TS-XX`**                                     |
| **Fecha**     | [YYYY-MM-DD]                                    |
| **QA Owner**  | [nombre]                                        |

| **`TX`**   | **`TC`**   | Resultado Real   | Evidencia         | Estado       | **`BUG`**      |
| :---       | :---       | :---            | :---              | :---         | :---           |
| **`TX-XX.XX`** | **`TC-XX`** | [descripción] | `[archivo.png]`   | PASS / FAIL  | — / **`BUG-XX`** |
```

## Trazabilidad

| Este prompt               | Alimenta                         |
| :---                      | :---                             |
| `prompt-12-test-logs.md`  | `prompt-13-execution-summary.md` |

---