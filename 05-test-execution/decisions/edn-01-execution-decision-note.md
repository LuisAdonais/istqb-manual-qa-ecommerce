# Execution Decision Note — EDN-01

| Atributo | Detalle |
| :--- | :--- |
| **Ubicación** | `05-test-execution/edn-01-execution-decision-note.md` |
| **Proyecto** | Tricentis Demo Web Shop |
| **Versión** | 1.1 |
| **Fase STLC** | Test Execution — Test Monitoring & Control |
| **Fecha** | 2026-05-04 |
| **Estado** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Contexto

La **`TS-01`** (Smoke Test Suite) finalizó con **5 PASS / 3 FAIL**, registrando los defectos **`BUG-01`**, **`BUG-02`** y **`BUG-03`** en estado 🔴 Open.

El criterio de entrada original para **`TS-02`** y **`TS-03`** requería **100% PASS en `TS-01`** (definido en `test-suites.md`, Sección 2). Dado que los defectos detectados no serán corregidos dentro del ciclo actual, ese criterio no puede cumplirse.

---

## 2. Evaluación de defectos activos

| **`BUG`** | **`TX`** | Severidad | ¿Bloquea flujo de negocio? | Módulo |
| :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | Low | No | Búsqueda |
| **`BUG-02`** | **`TX-01.07`** | Low | No | Catálogo |
| **`BUG-03`** | **`TX-01.08`** | Medium | No | Ficha de producto |

Ninguno de los tres defectos interrumpe los flujos de Carrito (**`TS-02`**) ni Checkout E2E (**`TS-03`**). Los módulos de Registro, Login, Carrito y Checkout permanecen funcionales.

---

## 3. Decisión

**Decisión:** ✅ Continuar ejecución bajo riesgo controlado.

**Justificación:** Los defectos **`BUG-01`**, **`BUG-02`** y **`BUG-03`** son de severidad Low y Medium. Ninguno interrumpe los flujos de negocio cubiertos por **`TS-02`** y **`TS-03`**. El criterio de entrada se renegocia de "100% PASS en `TS-01`" a **"ausencia de defectos Critical o High en estado Open"**.

**Riesgo asumido:** Los defectos Low y Medium quedan documentados y trazados. Resolución pendiente para el siguiente ciclo.

**Firmado:** Luis Adonais Malave Gamardo — QA Owner | 2026-05-04

---

## 4. Impacto en criterios de entrada

| Suite | Criterio original | Criterio renegociado | Estado |
| :--- | :--- | :--- | :--- |
| **`TS-02`** | 100% PASS en **`TS-01`** | Sin defectos Critical/High Open | ✅ Habilitada |
| **`TS-03`** | 100% PASS en **`TS-01`** | Sin defectos Critical/High Open | ✅ Habilitada |

---

## 5. Trazabilidad

| **`BUG`** | **`TX`** | Impacto en **`TS-02`** / **`TS-03`** | Decisión |
| :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | Ninguno | Continuar |
| **`BUG-02`** | **`TX-01.07`** | Ninguno | Continuar |
| **`BUG-03`** | **`TX-01.08`** | Ninguno | Continuar bajo riesgo controlado |
