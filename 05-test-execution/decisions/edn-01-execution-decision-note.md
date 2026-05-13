# Execution Decision Note — EDN-01

| Attribute | Detail |
| :--- | :--- |
| **Location** | `05-test-execution/edn-01-execution-decision-note.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.1 |
| **STLC Phase** | Test Execution — Test Monitoring & Control |
| **Date** | 2026-05-04 |
| **Status** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Context

**`TS-01`** (Smoke Test Suite) finished with **5 PASS / 3 FAIL**, logging defects **`BUG-01`**, **`BUG-02`**, and **`BUG-03`** in 🔴 Open state.

The original entry criterion for **`TS-02`** and **`TS-03`** required **100% PASS in `TS-01`** (see `test-suites.md`, Section 2). As the detected defects will not be fixed within the current cycle, this criterion cannot be met.

---

## 2. Evaluation of Active Defects

| **`BUG`** | **`TX`** | Severity | Does it block business flow? | Module |
| :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | Low | No | Search |
| **`BUG-02`** | **`TX-01.07`** | Low | No | Catalog |
| **`BUG-03`** | **`TX-01.08`** | Medium | No | Product detail |

None of the three defects interrupts the Cart (**`TS-02`**) or E2E Checkout (**`TS-03`**) flows. The Registration, Login, Cart, and Checkout modules remain functional.

---

## 3. Decision

**Decision:** ✅ Continue execution under controlled risk.

**Justification:** Defects **`BUG-01`**, **`BUG-02`**, and **`BUG-03`** are Low and Medium severity. None blocks business flows covered by **`TS-02`** and **`TS-03`**. The entry criterion is renegotiated from "100% PASS in `TS-01`" to **"no Open Critical or High defects"**.

**Risk assumed:** Low and Medium defects are documented and tracked. Resolution is pending for the next cycle.

**Signed:** Luis Adonais Malave Gamardo — QA Owner | 2026-05-04

---

## 4. Impact on Entry Criteria

| Suite | Original Criterion | Renegotiated Criterion | Status |
| :--- | :--- | :--- | :--- |
| **`TS-02`** | 100% PASS in **`TS-01`** | No Critical/High defects Open | ✅ Enabled |
| **`TS-03`** | 100% PASS in **`TS-01`** | No Critical/High defects Open | ✅ Enabled |

---

## 5. Traceability

| **`BUG`** | **`TX`** | Impact on **`TS-02`** / **`TS-03`** | Decision |
| :--- | :--- | :--- | :--- |
| **`BUG-01`** | **`TX-01.05`** | None | Continue |
| **`BUG-02`** | **`TX-01.07`** | None | Continue |
| **`BUG-03`** | **`TX-01.08`** | None | Continue under controlled risk |
