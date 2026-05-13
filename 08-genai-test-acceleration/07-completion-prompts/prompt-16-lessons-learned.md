
# prompt-16 — Lessons Learned

| Attribute      | Detail                                                                         |
| :---           | :---                                                                           |
| **Location**   | `08-genai-test-acceleration/07-completion-prompts/prompt-16-lessons-learned.md`|
| **Project**    | Tricentis Demo Web Shop                                                        |
| **Version**    | 1.0                                                                            |
| **STLC Phase** | Test Completion                                                                |
| **GenAI Technique** | Structured prompt · Iterative HITL                                        |
| **Reference**      | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4                                         |

## Descripción del artefacto

El artefacto **Lessons Learned** documenta los aprendizajes del ciclo de prueba. Según ISTQB CTFL v4.0, es un *test completion work product* que incluye: lo que funcionó bien, lo que debe mejorarse, métricas del ciclo y acciones de mejora (**`MA`**) para futuros proyectos.

**Función en el STLC:** Cierra el ciclo con retrospectiva trazable. Las **`MA`** son accionables y apuntan a artefactos específicos como origen.

**Datos que lo alimentan:** Todos los artefactos del ciclo — especialmente anomalías, defectos y desviaciones de criterios.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-13-execution-summary.md` completado.

### Instrucción

Construir el artefacto `lessons-learned.md` en colaboración con el tester:

1. Solicitar al tester: qué funcionó bien, qué debe mejorarse, métricas finales del ciclo.
2. Por cada punto de mejora, derivar una acción concreta (**`MA`**) con prioridad y artefacto de origen.
3. Validar con el tester antes de cerrar cada sección.
4. Máximo 3 preguntas por intercambio.

No generar lecciones sin respaldo en artefactos del ciclo. Cada **`LM`** y **`LL`** debe referenciar un artefacto.

### Input data

```text
Lo que funcionó bien: [descripción + artefacto que lo evidencia]
Lo que debe mejorarse: [descripción + artefacto de origen]
Métricas del ciclo:
  Artefactos producidos: [número]
  Anomalías detectadas: [número]
  Defectos detectados: [número]
  Defectos bloqueantes: [número al cierre]
  Desviaciones (EDN): [número]
```

### Constraints

- IDs lecciones positivas: **`LL-01`**, **`LL-02`**...
- IDs lecciones de mejora: **`LM-01`**, **`LM-02`**...
- IDs acciones de mejora: **`MA-01`**, **`MA-02`**...
- Cada **`MA`** referencia su **`LM`** de origen.

### Output format

```markdown
# Lessons Learned

| Atributo      | Detalle                         |
| :---          | :---                            |
| **Ubicación** | `07-test-completion/lessons-learned.md` |
| **Proyecto**  | [nombre]                        |
| **Versión**   | [x.x]                           |
| **Fase STLC** | Test Completion                 |
| **Estado**    | Completado                      |
| **QA Owner**  | [nombre]                        |

## 1. Lo que funcionó bien

### LL-01 — [título]

[descripción + acción de preservación]

## 2. Lo que debe mejorarse

### LM-01 — [título]

[descripción + acción correctiva]

## 3. Aprendizajes

### LA-01 — [título]

[descripción]

## 4. Métricas del ciclo

| Indicador              | Valor |
| :---                   | :---  |
| Artefactos producidos  | [n]   |

## 5. Acciones de mejora

| ID         | Origen  | Acción    | Prioridad |
| :---       | :---    | :---      | :---      |
| **`MA-01`** | **`LM-01`** | [acción] | Alta      |

## 6. Trazabilidad

| Lección      | Artefacto de origen | **`MA`**   |
| :---         | :---                | :---       |
| **`LL-01`**  | [artefacto]         | —          |
| **`LM-01`**  | [artefacto]         | **`MA-01`**|
```

## Trazabilidad

| Este prompt                          | Alimenta                      |
| :---                                 | :---                          |
| `prompt-16-lessons-learned.md`       | `prompt-17-summary-report.md` |

---