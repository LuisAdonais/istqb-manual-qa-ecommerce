# prompt-00 — System Under Test (SUT)

| Atributo      | Detalle                                                            |
| :------------ | :----------------------------------------------------------------- |
| **Ubicación** | `08-genai-test-acceleration/01-planning-prompts/prompt-00-sut.md` |
| **Proyecto**  | Tricentis Demo Web Shop                                            |
| **Versión**   | 1.0                                                                |
| **Fase STLC** | Pre-Planning                                                       |
| **Técnica GenAI** | Zero-shot prompting · Structured prompt · HITL iterativo       |
| **Referencia** | CT-GenAI GenAI-2.1.1 / GenAI-2.1.3 / GenAI-2.3.2                  |

---

## Descripción del artefacto

El **System Under Test (SUT)** identifica y delimita el objeto de prueba antes de iniciar cualquier actividad del STLC. Según ISTQB CTFL v4.0, el *test object* es "el componente o sistema que se va a probar".

**Función en el STLC:** Habilita la fase de Planning al proveer la línea base del objeto de prueba. Sin SUT aprobado no puede definirse alcance, riesgos ni estrategia de prueba.

**Datos que lo alimentan:** Descripción del producto, URL pública, sistema operativo, navegador del entorno, roles de usuario funcionales, lista de módulos identificados y exclusiones explícitas.

> ⚠️ **Sección pendiente:** La columna `Ref. REQ` del bloque **Módulos en Alcance** se completa en una segunda iteración, una vez que `requirements.md` esté disponible y los IDs **`REQ`** estén asignados. El tester regresa a este artefacto con esos datos para cerrar la trazabilidad.

---

## Prompt

> 🔗 **Requiere:** `system-prompt.md` + `context-rules.md` activos antes de ejecutar este prompt.

---

### Instrucción

Construir el artefacto `system-under-test.md` en colaboración con el tester siguiendo este proceso:

1. Leer el Input data que el tester provee.
2. Completar con ese input todas las secciones del Output format que tengan datos suficientes.
3. Para cada campo que no pueda completarse con el input recibido, hacer una pregunta puntual al tester — máximo 3 preguntas por intercambio.
4. Esperar la respuesta del tester e incorporarla antes de continuar.
5. Repetir hasta que todas las secciones estén completas, excepto `Ref. REQ` que queda vacía hasta recibir `requirements.md`.

No asumir datos. No inventar módulos. No agregar secciones fuera del Output format.

---

### Input data

El tester provee en su primer mensaje:

```text
Nombre del sistema :
URL                :
Arquitectura       :
Dominio            :
Sistema operativo  :
Navegador + versión:
Roles de usuario   : [rol] → [funciones accesibles]
Módulos observados : [lista libre]
Exclusiones        : [lista libre]
```

> 💬 **Si el tester no completa todos los campos**, el modelo identifica cuáles faltan y los solicita en el primer intercambio antes de generar cualquier sección del artefacto.

---

### Constraints

- No completar `Ref. REQ` — esa columna se llena en iteración posterior.
- No incluir riesgos, objetivos ni criterios de prueba.
- No inferir módulos que no estén en el input del tester.
- Encabezado obligatorio: Ubicación, Proyecto, Versión, Fase STLC, Estado (`Draft` hasta aprobación), QA Owner.
- Máximo 3 preguntas por intercambio — priorizar las más bloqueantes.

---

### Output format

```markdown
# System Under Test (SUT)

| Atributo      | Detalle |
| :------------ | :------ |
| **Ubicación** | `00-context-and-overview/system-under-test.md` |
| **Proyecto**  | [nombre] |
| **Versión**   | [x.x] |
| **Fase STLC** | Pre-Planning |
| **Estado**    | Draft |
| **QA Owner**  | [nombre] |

---

## Identificación

| Atributo         | Detalle |
| :--------------- | :------ |
| **Nombre**       | [nombre del sistema] |
| **URL**          | [url] |
| **Arquitectura** | [arquitectura] |
| **Dominio**      | [dominio] |
| **Entorno**      | [OS / Navegador versión] |

---

## Stakeholders

| Rol     | Acceso Funcional |
| :------ | :--------------- |
| [Rol 1] | [funciones] |
| [Rol 2] | [funciones] |

---

## Módulos en Alcance

> ⚠️ Columna `Ref. REQ` pendiente — se completa cuando `requirements.md` esté disponible.

| Módulo     | Ref. **`REQ`** |
| :--------- | :------------- |
| [Módulo 1] | — |
| [Módulo N] | — |

---

## Fuera de Alcance

- [exclusión 1]
- [exclusión N]
```

---

## Trazabilidad

| Este prompt        | Alimenta                                                   |
| :----------------- | :-------------------------------------------------------- |
| `prompt-00-sut.md` | `prompt-01-test-plan.md`                                  |
| Segunda iteración  | `prompt-02-requirements.md` → regresa a cerrar `Ref. REQ` |

---
