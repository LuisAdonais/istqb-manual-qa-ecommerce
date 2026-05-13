
# prompt-07 — Test Environment Setup

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `08-genai-test-acceleration/04-implementation-prompts/prompt-07-environment.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.0 |
| **Fase STLC** | Test Implementation |
| **Técnica GenAI** | Structured prompt · HITL iterativo |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Descripción del artefacto

El **Test Environment Setup** documenta la configuración del entorno de prueba necesario para ejecutar las suites. Según ISTQB CTFL v4.0, es un *test implementation work product* que incluye hardware, software, datos de configuración y procedimientos de preparación del entorno.

**Función en el STLC:** Garantiza que el entorno está listo antes de iniciar la ejecución. Es la fuente única de verdad para convenciones de nomenclatura de evidencias.

**Datos que lo alimentan:** SUT identificado, OS y navegador del entorno, herramienta de captura de evidencia, datos de cuenta pre-creados.

---

## Prompt

> [!TIP]
> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos. Input: `prompt-06-test-data.md` completado.

### Instrucción

Construir el artefacto `test-environment-setup.md` en colaboración con el tester:

1. Solicitar al tester los datos del entorno físico y lógico.
2. Documentar los pasos de preparación previa a la ejecución.
3. Registrar la convención de nomenclatura de evidencias como fuente única de verdad.
4. Validar con el tester antes de marcar como Draft listo para revisión.

No inventar versiones de software ni herramientas no confirmadas.

### Input data

```text
OS                 : [sistema operativo + versión]
Navegador          : [nombre + versión]
URL del SUT        : [url]
Herramienta captura: [nombre de la herramienta de screenshots]
Cuenta pre-creada  : [TD-XX → email + contraseña]
Pasos de prep.     : [acciones previas a la ejecución — ej. limpiar caché]
Convención evidencia: YYYY-MM-DD_TX-XX.XX_Descripcion_ESTADO.png
```

### Constraints

- La convención de nomenclatura de evidencias debe aparecer en sección destacada.
- Pasos de preparación no son ciclos **`TX`** — no asignarles ID de ejecución.
- Encabezado con Estado `Draft`.

### Output format

```markdown
# Test Environment Setup

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `04-test-implementation/test-environment-setup.md` |
| **Proyecto** | [nombre] |
| **Versión** | [x.x] |
| **Fase STLC** | Test Implementation |
| **Estado** | Draft |
| **QA Owner** | [nombre] |

## 1. Configuración del entorno

| Componente | Detalle |
| :--- | :--- |
| **OS** | [OS + versión] |
| **Navegador** | [nombre + versión] |
| **URL SUT** | [url] |
| **Herramienta evidencia** | [herramienta] |

## 2. Convención de nomenclatura de evidencias

> [!IMPORTANT]
> ⚠️ Esta sección es la fuente única de verdad para nomenclatura de evidencias.

```text
YYYY-MM-DD_TX-XX.XX_Descripcion_Breve_ESTADO.png
```

**Ejemplo:** `2026-05-04_TX-01.01_Register_Submit_PASS.png`

## 3. Preparación de datos

> [!NOTE]
> Estos pasos son de configuración de entorno, no constituyen un ciclo **`TX`** formal.

1. [paso de preparación]

## 4. Trazabilidad

| Requisito de entorno | **`TS`** dependiente | Estado |
| :--- | :--- | :--- |
| [requisito] | **`TS-XX`** | [estado] |

```

## Trazabilidad

| Este prompt | Alimenta |
| :--- | :--- |
| `prompt-07-environment.md` | `prompt-08-procedures.md` · `prompt-09-test-suites.md` |

---