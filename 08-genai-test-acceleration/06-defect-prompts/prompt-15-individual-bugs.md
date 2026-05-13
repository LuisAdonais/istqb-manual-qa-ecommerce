
# prompt-15 — Individual Bug Reports

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/06-defect-prompts/prompt-15-individual-bugs.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Defect Management |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Descripción del artefacto

Un **Individual Bug Report** (**`BUG-XX`**) es el reporte detallado de un defecto individual. Según ISTQB CTFL v4.0, debe incluir: identificador único, título, fecha, entorno, contexto, pasos de reproducción, resultado esperado vs. real, severidad, prioridad, estado y referencias.

**Función en el STLC:** Provee al equipo de desarrollo la información suficiente para reproducir y resolver el defecto. Cada archivo es un defecto independiente.

**Datos que lo alimentan:** Entrada de `defect-reports.md`, evidencia de ejecución, **`TX`** y **`TC`** de origen.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-14-defect-reports.md` completado.

### Instrucción

Generar un archivo individual por defecto en colaboración con el tester:

1. Por cada **`BUG`** de la tabla consolidada, solicitar al tester los pasos de reproducción y la evidencia.
2. Estructurar según el Output format.
3. Validar resultado esperado vs. real con el tester — deben ser concretos y observables.
4. Un archivo por **`BUG`** — no consolidar múltiples defectos en un mismo archivo.

### Input data

```text
BUG a documentar   : [BUG-XX]
TX origen          : [TX-XX.XX]
TC fallado         : [TC-XX]
REQ afectado       : [REQ-XX]
Pasos reproducción : [pasos numerados]
Resultado esperado : [comportamiento del REQ / AC]
Resultado real     : [lo que ocurrió]
Evidencia          : [nombre del archivo según convención]
Severidad          : [Critical / High / Medium / Low]
Prioridad          : [Alta / Media / Baja]
```

### Constraints

- Nombre de archivo: `BUG-XX_[Titulo-Corto].md`.
- Resultado esperado debe referenciar el **`AC`** correspondiente.
- Resultado real: observable, sin interpretación.
- Sin "correctamente", "adecuadamente" en ninguna sección.

### Output format

```markdown
# **`BUG-XX`** — [Título descriptivo]

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `06-defect-management/BUG-XX_[Titulo].md` |
| **Proyecto** | [nombre] |
| **Fecha** | [YYYY-MM-DD] |
| **`TX`** origen | **`TX-XX.XX`** |
| **`TC`** fallado | **`TC-XX`** |
| **`REQ`** afectado | **`REQ-XX`** |
| **Severidad** | [severidad] |
| **Prioridad** | [prioridad] |
| **Estado** | Open |
| **QA Owner** | [nombre] |

## Pasos de reproducción

| Paso | Acción |
| :--- | :--- |
| 1 | [acción imperativa] |

## Resultado esperado

[Comportamiento definido en **`AC-XX`**]

## Resultado real

[Lo que ocurrió — observable]

## Evidencia

`[nombre-archivo.png]`
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-15-individual-bugs.md` | `prompt-13-execution-summary.md` · `prompt-17-summary-report.md` |

---