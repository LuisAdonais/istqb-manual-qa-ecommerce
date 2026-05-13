
# 05 — Test Execution

Fase de ejecución. 12 ciclos de prueba distribuidos en 3 suites, con logs detallados, evidencias por `TX` y una decisión formal de continuación ante los defectos detectados en `TS-01`.

---

## Contenido

| Archivo / Carpeta | Descripción |
| :--- | :--- |
| [`test-execution-tracker.md`](./test-execution-tracker.md) | Dashboard de ejecución — estado de los 12 `TX` |
| [`test-execution-summary.md`](./test-execution-summary.md) | Métricas consolidadas del ciclo — Pass Rate, densidad de defectos |
| [`test-logs/`](./test-logs/) | Logs detallados por suite — `TL-01` Smoke · `TL-02` Regression · `TL-03` E2E |
| [`decisions/`](./decisions/) | Decisiones formales de ejecución — `EDN-01` |
| [`test-evidence/`](./test-evidence/) | Evidencias organizadas por suite — 12 screenshots |

---

## Resultado del ciclo

| Suite | TX | PASS | FAIL | Pass Rate |
| :--- | :--- | :--- | :--- | :--- |
| `TS-01` Smoke | 8 | 5 | 3 | 62.5% |
| `TS-02` Regression | 3 | 3 | 0 | 100% |
| `TS-03` E2E | 1 | 1 | 0 | 100% |

> [!NOTE]
> 
> Continuación de `TS-02` y `TS-03` autorizada mediante [`EDN-01`](./decisions/edn-01-execution-decision-note.md).

---

## Navegación

← [04 — Test Implementation](./04-test-implementation/04-README.md) | → [06 — Defect Management](./06-defect-management/defect-reports.md)
