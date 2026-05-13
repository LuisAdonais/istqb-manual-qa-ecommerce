
# prompt-03 — Test Basis Evaluation

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/02-analysis-prompts/prompt-03-basis-evaluation.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Analysis |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Descripción del artefacto

La **Test Basis Evaluation** registra las anomalías estáticas (**`AN`**) detectadas durante la revisión de la base de prueba. Según ISTQB CTFL v4.0, el análisis de prueba evalúa la base de prueba para identificar defectos que pueda contener (ambigüedades, inconsistencias, información incompleta) y para evaluar su testabilidad.

**Función en el STLC:** Depura la base de prueba antes del diseño. Cada **`AN`** resuelta previene un falso resultado en ejecución.

**Datos que lo alimentan:** `requirements.md` aprobado — revisión ítem por ítem de **`REQ`** y **`AC`**.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-02-requirements.md` completado.

### Instrucción

Revisar el artefacto `requirements.md` en colaboración con el tester:

1. Analizar cada **`REQ`** y **`AC`** buscando: ambigüedad, información incompleta, criterios no verificables binariamente, comportamientos implícitos no documentados.
2. Por cada anomalía detectada, presentarla al tester con una pregunta puntual de resolución.
3. Registrar el estado de cada **`AN`**: Resuelta antes de diseño / Pendiente.
4. Máximo 3 anomalías por intercambio.

No inventar anomalías. Cada **`AN`** debe referenciar un **`REQ`** o **`AC`** específico.

### Input data

```text
Base de prueba     : [contenido de requirements.md]
Por cada AN el tester confirma:
  Descripción      : [qué está mal o incompleto]
  REQ / AC afectado: [ID]
  Resolución       : [corrección aplicada o decisión tomada]
  Estado           : [Resuelta / Pendiente]
```

### Constraints

- IDs secuenciales: **`AN-01`**, **`AN-02`**…
- Cada **`AN`** referencia obligatoriamente un **`REQ`** o **`AC`**.
- No proponer correcciones de diseño ni de arquitectura.
- Encabezado con Estado `Draft`.

### Output format

```markdown
# Test Basis Evaluation

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `02-test-analysis/test-basis-evaluation.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Analysis |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## Anomalías Estáticas (`AN`)

| ID | **`REQ`** / **`AC`** | Descripción | Resolución | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **`AN-01`** | **`REQ-XX`** | [descripción] | [resolución] | Resuelta / Pendiente |

## Trazabilidad

| **`AN`** | **`REQ`** / **`AC`** afectado | Impacto en diseño |
| :--- | :--- | :--- |
| **`AN-XX`** | **`REQ-XX`** | [descripción del impacto] |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-03-basis-evaluation.md` | `prompt-04-test-conditions.md` |

---

---