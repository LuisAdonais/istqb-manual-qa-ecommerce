
# prompt-06 — Test Data

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/03-design-prompts/prompt-06-test-data.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Design |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Descripción del artefacto

Los **Test Data Requirements** especifican los datos necesarios para ejecutar los casos de prueba. Según ISTQB CTFL v4.0, son un *test design work product*. GenAI puede sintetizar datos representativos que cubran particiones válidas, inválidas y valores límite sin exponer datos sensibles.

**Función en el STLC:** Provee los valores concretos que los **`TP`** y **`TC`** necesitan para ser ejecutables.

**Datos que lo alimentan:** `test-cases.md` aprobado — campos de entrada, técnicas **`EP`** / **`BVA`** aplicadas.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-05-test-cases.md` completado.

### Instrucción

Especificar los datos de prueba en colaboración con el tester:

1. Por cada **`TC`** que requiera datos de entrada, identificar los campos necesarios.
2. Proponer valores para particiones válidas, inválidas y límites según la técnica aplicada.
3. Presentar al tester para validación — especialmente valores límite y datos negativos.
4. Máximo 5 **`TD`** por intercambio.

No usar datos personales reales. Datos sintéticos que representen comportamiento real del SUT.

### Input data

```text
TC con entrada de datos: [lista de TC-XX con campos identificados]
Por cada TD el tester confirma:
  Campo            : [nombre del campo en el SUT]
  Valor            : [dato concreto]
  Tipo             : [válido / inválido / límite]
  Usado en TC      : [TC-XX]
```

### Constraints

- IDs secuenciales: **`TD-01`**, **`TD-02`**…
- Cada **`TD`** referencia el **`TC`** que lo consume.
- No usar emails, nombres o contraseñas reales.
- Valores límite deben identificar explícitamente la partición que cubren.

### Output format

```markdown
# Test Data Requirements

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `03-test-design/test-data-requirements.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Design |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## Datos de prueba (`TD`)

| ID | Campo | Valor | Tipo | **`TC`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TD-01`** | [campo] | [valor] | Válido / Inválido / Límite | **`TC-XX`** |

## Trazabilidad

| **`TD`** | **`TC`** | **`TCND`** |
| :--- | :--- | :--- |
| **`TD-XX`** | **`TC-XX`** | **`TCND-XX`** |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-06-test-data.md` | `prompt-07-environment.md` · `prompt-08-procedures.md` |

---