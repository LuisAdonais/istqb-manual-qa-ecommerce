# Lessons Learned

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `07-test-completion/lessons-learned.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.1 |
| **Fase STLC** | Test Completion |
| **Periodo** | 2026-05-04 — 2026-05-05 |
| **Estado** | ✅ Completado |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## Contexto

Los requisitos (**`REQ`**) fueron construidos por ingeniería inversa sobre el SUT — no existió documentación funcional previa. Es un entorno demo público usado para practicar, y eso condicionó algunas decisiones del ciclo.

---

## Lo que funcionó

**LL-01 — Construir la cadena de trazabilidad desde el inicio valió el esfuerzo.**

Definir **`REQ`**→**`AC`**→**`TC`**→**`TX`**→**`BUG`** como estructura obligatoria desde el arranque tuvo un costo alto en planificación, pero cuando apareció **`BUG-03`**, localizar el incumplimiento en **`AC-04`** tomó segundos. Sin esa cadena, hubiera tenido que reconstruir el razonamiento desde cero en el peor momento.

**LL-02 — Documentar la desviación en `EDN-01` fue mejor que ignorarla o frenar el ciclo.**

Los criterios de entrada de **`TS-02`** y **`TS-03`** exigían 100% PASS en **`TS-01`**, pero los defectos detectados eran Low y Medium sin impacto en el flujo principal. En lugar de saltarme el criterio en silencio, documenté la decisión en **`EDN-01`** y continué con trazabilidad. Es lo que haría en un equipo real.

**LL-03 — La revisión estática sobre mis propios REQ también encontró problemas reales.**

**`AN-02`** surgió al revisar **`REQ-07`**: el requisito incluía notificación por email al completar el checkout, pero el SUT solo muestra un número de orden en pantalla. Si no ajustaba **`AC-09`** antes del diseño, **`TC-09`** hubiera generado un FAIL sobre un comportamiento que el sistema nunca tuvo — un falso defecto.

---

## Lo que debo mejorar

**LM-01 — El criterio "100% PASS" no funciona cuando el entorno es una demo pública.**

Definir el umbral de entrada de suites por porcentaje de PASS en lugar de por severidad de defectos fue un error de diseño del Test Plan. Lo corregí con **`EDN-01`**, pero debí haberlo pensado antes. Para el próximo ciclo, los criterios de entrada se definen por lo que realmente bloquea el trabajo, no por un número redondo.

**LM-02 — Un resultado esperado ambiguo fue detectado y corregido antes de publicar.**

El Paso 3 de **`TP-03`** usaba el conector "o" para describir dos posibles resultados, lo que impedía un veredicto único. Lo identifiqué en la revisión del ciclo y lo corregí en **`test-procedures.md`** v1.7 — las dos ramas quedaron como condiciones separadas. Cada resultado esperado debe admitir exactamente un veredicto: Pasa o Falla.

**LM-03 — Los comportamientos implícitos del SUT hay que capturarlos antes de escribir los REQ.**

**`AN-05`** — que ingresar `Qty.=0` elimina el ítem sin confirmación — lo descubrí ejecutando **`TX-02.02`**, no durante el análisis. Un recorrido exploratorio rápido del SUT antes de escribir los **`REQ`** hubiera permitido documentarlo desde el origen.

---

## Métricas del ciclo

| Indicador | Valor |
| :--- | :--- |
| Artefactos producidos | 19 documentos Markdown |
| Anomalías estáticas detectadas | 5 (AN-01 a AN-05) |
| Defectos reportados | 3 — densidad 0.25 BUG/TX |
| Defectos bloqueantes al cierre | 0 |
| Desviaciones formalizadas | 1 (EDN-01) |

---

## Trazabilidad

| Lección | Artefacto de origen |
| :--- | :--- |
| **LL-01** | **`BUG-03`**, cadena REQ→TX |
| **LL-02** | **`EDN-01`**, **`test-suites.md`** |
| **LL-03** | **`AN-02`**, **`AC-09`** |
| **LM-01** | **`test-suites.md`**, **`EDN-01`** |
| **LM-02** | **`TP-03`** v1.7 |
| **LM-03** | **`TX-02.02`**, **`AN-05`** |