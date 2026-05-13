# Test Execution Summary

| Attribute | Detail |
| :--- | :--- |
| **Location** | `05-test-execution/test-execution-summary.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 4.0 |
| **STLC Phase** | Test Execution — Test Progress Reporting |
| **Period** | 2026-05-04 — 2026-05-05 |
| **Status** | ✅ Completed |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Objective

Consolidate the results of the functional test cycle for the Tricentis Demo Web Shop. This cycle covers 12 test cycles (**`TX`**) distributed across 3 test suites (**`TS-01`**, **`TS-02`**, **`TS-03`**), validating requirements **`REQ-01`** to **`REQ-07`**.

---

## 2. Results by suite

| **`TS`** | Description | Total **`TX`** | Executed | PASS | FAIL | Final Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`TS-01`** | Smoke — Registration, Login, Search, Catalog | 8 | 8 | 5 | 3 | 5P / 3F |
| **`TS-02`** | Regression — Cart logic (BVA) | 3 | 3 | 3 | 0 | 3P / 0F |
| **`TS-03`** | E2E — Complete Checkout | 1 | 1 | 1 | 0 | 1P / 0F |
| **TOTAL** | — | **12** | **12** | **9** | **3** | **75% Pass Rate** |

> [!NOTE]
>
> Continuation of **`TS-02`** and **`TS-03`** despite the failures in **`TS-01`** was authorized via **`EDN-01`** (2026-05-04). No active defect had Critical or High severity.

---

## 3. Quality metrics

| Metric | Formula | Result |
| :--- | :--- | :--- |
| **Completeness** | Executed TX / Planned TX × 100 | **100% (12/12)** |
| **Global Pass Rate** | PASS / Executed TX × 100 | **75% (9/12)** |
| **E2E Pass Rate** | PASS TS-03 / TX TS-03 × 100 | **100% (1/1)** |
| **Defect density** | BUGs / TX | **0.25 (3/12)** |

---

## 4. Open defects at closure

| **`BUG`** | **`TX`** | Severity | Status |
| :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | Low | 🔴 Open — pending next cycle |
| **`BUG-02`** | **`TX-01.07`** | Low | 🔴 Open — pending next cycle |
| **`BUG-03`** | **`TX-01.08`** | Medium | 🔴 Open — controlled according to **`EDN-01`** |

---

## 5. Traceability references

| **`TS`** | Covered **`TX`** | Log (**`TL`**) | Status |
| :--- | :--- | :--- | :--- |
| **`TS-01`** | **`TX-01.01`** to **`TX-01.08`** | [tl-01-smoke-log.md](./test-logs/tl-01-smoke-log.md) | 5P / 3F |
| **`TS-02`** | **`TX-02.01`** to **`TX-02.03`** | [tl-02-regression-log.md](./test-logs/tl-02-regression-log.md) | 3P / 0F |
| **`TS-03`** | **`TX-03.01`** | [tl-03-e2e-log.md](./test-logs/tl-03-e2e-log.md) | 1P / 0F |
