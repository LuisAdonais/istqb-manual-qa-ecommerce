
---

# prompt-01 — Test Plan

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/01-planning-prompts/prompt-01-test-plan.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Planning |
| **Técnica GenAI** | Prompt chaining · Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.1 |

## Descripción del artefacto

El **Test Plan** es el documento que define el alcance, enfoque, recursos y calendario de las actividades de prueba. Según ISTQB CTFL v4.0, es un *test planning work product* que incluye: alcance, objetivos, estrategia, criterios de entrada y salida, riesgos del producto y trazabilidad.

**Función en el STLC:** Governa todo el ciclo. Sin Test Plan aprobado no puede iniciarse ninguna fase de análisis ni diseño.

**Datos que lo alimentan:** `system-under-test.md` aprobado, módulos en alcance, riesgos identificados por el QA Lead, técnicas de prueba seleccionadas.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-00-sut.md` completado.

### Instrucción

Construir el artefacto `test-plan.md` en colaboración con el tester:

1. Leer el Input data provisto.
2. Completar alcance, objetivos y enfoque con los datos disponibles.
3. Para riesgos y criterios: solicitar al tester los datos faltantes — máximo 3 preguntas por intercambio.
4. Incorporar respuestas y continuar hasta completar todas las secciones.

No inventar riesgos. No asumir umbrales de criterios de salida sin confirmación del tester.

### Input data

```text
SUT aprobado       : [referencia a system-under-test.md]
Módulos en alcance : [lista de REQ]
Nivel de prueba    : [System / Integration / Acceptance]
Tipo de prueba     : [Functional / Non-functional]
Estrategia         : [Risk-based / Coverage-based]
Técnicas aplicadas : [EP / BVA / State Transition / Error Guessing]
Riesgos del producto: [descripción + prioridad por módulo]
Umbral exit criteria: [% ejecución / pass rate / bugs críticos abiertos]
```

### Constraints

- No incluir análisis de arquitectura ni decisiones de desarrollo.
- Riesgos solo con base en módulos declarados en el SUT.
- Encabezado obligatorio: Ubicación, Proyecto, Versión, Fase STLC, Estado (`Draft`), QA Owner.

### Output format

```markdown
# Test Plan

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `01-test-planning/test-plan.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Planning |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## 1. Alcance

### In Scope

| Módulo | **`REQ`** |
| :--- | :--- |
| [módulo] | **`REQ-XX`** |

### Out of Scope

- [exclusión]

## 2. Objetivos

- [objetivo 1]

## 3. Enfoque de Prueba

| Categoría | Definición |
| :--- | :--- |
| **Nivel** | [nivel] |
| **Tipo** | [tipo] |
| **Estrategia** | [estrategia] |

**Técnicas aplicadas:**

| Técnica | Aplicación |
| :--- | :--- |
| [técnica] | [módulo / TC] |

## 4. Criterios de Entrada y Salida

### Entry Criteria

- [criterio]

### Exit Criteria

| Criterio | Umbral |
| :--- | :--- |
| [criterio] | [umbral] |

## 5. Riesgos del Producto

| ID | Descripción | Prioridad | Mitigación |
| :--- | :--- | :--- | :--- |
| **`RISK-01`** | [descripción] | [prioridad] | [mitigación] |

## 6. Trazabilidad

| **`REQ`** | **`TCND`** | **`TC`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-XX`** | — | — | **`RISK-XX`** |
```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-01-test-plan.md` | `prompt-02-requirements.md` |

---