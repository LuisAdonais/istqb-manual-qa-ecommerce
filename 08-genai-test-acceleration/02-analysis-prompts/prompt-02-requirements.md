
# prompt-02 — Requirements Specification

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/02-analysis-prompts/prompt-02-requirements.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Analysis |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Descripción del artefacto

El artefacto **Requirements Specification** registra los requisitos funcionales (**`REQ`**) y sus criterios de aceptación (**`AC`**) derivados del SUT. Según ISTQB CTFL v4.0, los *test analysis work products* incluyen condiciones de prueba priorizadas, que se originan en los criterios de aceptación. Los **`AC`** son las condiciones que una implementación debe cumplir para ser aceptada por los stakeholders.

**Función en el STLC:** Es la base de prueba primaria. Sin **`REQ`** y **`AC`** aprobados no pueden definirse condiciones de prueba ni casos de prueba.

**Datos que lo alimentan:** Módulos en alcance del Test Plan, observación directa del SUT por parte del tester, criterios funcionales acordados.

> [!WARNING]
> ⚠️ **Cierre pendiente en SUT:** Una vez asignados los IDs **`REQ`**, regresar a `system-under-test.md` y completar la columna `Ref. REQ` en la tabla de Módulos en Alcance.

---

## Prompt

> [!TIP]
> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-01-test-plan.md` completado.

### Instrucción

Construir el artefacto `requirements.md` en colaboración con el tester:

1. Leer los módulos en alcance del Input data.
2. Por cada módulo, solicitar al tester la descripción del requisito funcional y sus criterios de aceptación observados.
3. Máximo 3 preguntas por intercambio — priorizar módulos de mayor riesgo.
4. Estructurar cada ítem según el Output format y esperar validación del tester antes de continuar con el siguiente módulo.

No inferir comportamiento no confirmado. No agregar AC sin respaldo del tester.

### Input data

```text
Módulos en alcance : [lista de módulos del Test Plan]
Por cada módulo el tester provee:
  REQ descripción  : [qué hace el sistema — verbo en tercera persona]
  Prioridad        : [Alta / Media / Crítica]
  AC observados    : [condición verificable — una por línea]
```

### Constraints

- Cada **`AC`** debe ser binariamente verificable (Pasa / Falla).
- No usar términos subjetivos: "correctamente", "adecuadamente".
- IDs secuenciales: **`REQ-01`**, **`REQ-02`**… / **`AC-01`**, **`AC-02`**…
- Encabezado obligatorio con Estado `Draft`.

### Output format

```markdown
# Requirements Specification

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `02-test-analysis/requirements.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Analysis |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## 1. Requisitos Funcionales (`REQ`)

| ID | Módulo | Descripción | Prioridad |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | [módulo] | [descripción] | [prioridad] |

## 2. Criterios de Aceptación (`AC`)

| ID | **`REQ`** | Criterio de Aceptación | Estado |
| :--- | :--- | :--- | :--- |
| **`AC-01`** | **`REQ-01`** | [criterio verificable] | ✔️ Verificable |

## 3. Trazabilidad

| **`REQ`** | **`AC`** |
| :--- | :--- |
| **`REQ-XX`** | **`AC-XX`**, **`AC-XX`** |
```

## Trazabilidad

| Este prompt | Alimenta | Regresa a |
| :--- | :--- | :--- |
| `prompt-02-requirements.md` | `prompt-03-basis-evaluation.md` | `prompt-00-sut.md` → cerrar `Ref. REQ` |

---