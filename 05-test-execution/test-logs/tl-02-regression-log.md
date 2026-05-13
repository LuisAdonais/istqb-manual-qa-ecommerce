# Test Log — TL-02 (Regression Suite)

| Attribute | Detail |
| :--- | :--- |
| **Location** | `05-test-execution/test-logs/tl-02-regression-log.md` |
| **Suite** | **`TS-02`** — Full Regression Suite |
| **Version** | 2.1 |
| **STLC Phase** | Test Execution — Test Logging |
| **Date** | 2026-05-05 |
| **Environment** | Windows 10 Pro / Firefox 150.0.1 |
| **Status** | ✅ Completed with no failures |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

> **Entry precondition:** **`TS-01`** completed with 3 open defects (**`BUG-01`**, **`BUG-02`**, **`BUG-03`**). Continuation authorized by **`EDN-01`** (2026-05-04) as there are no open Critical or High defects. See `edn-01-execution-decision-note.md`.

**Operational precondition:** Active session with **`TD-09`** and **`TD-10`**.

- **`TX-02.01`** and **`TX-02.02`**: Cart contains **1 item** before each test cycle.
- **`TX-02.03`**: Cart contains **2 different items** — required to isolate partial removal and validate recalculation on the remaining item.

---

## 1. Cycle Log

| **`TX`** | **`TC`** | **`TP`** | Verified Action | **`TD`** | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`TX-02.01`** | **`TC-05`** | **`TP-03`** | Change `Qty.` to `2`. Click `Update shopping cart`. Validate recalculation of `Sub-Total`. | **`TD-04`** | The system updates the `Sub-Total` correctly: unit price × 2. The field accepts keyboard input. | ✅ PASS |
| **`TX-02.02`** | **`TC-10`** | **`TP-03`** | With 1 item in cart, set `Qty.` to `0`. Click `Update shopping cart`. Validate that the cart is empty. | **`TD-19`** | The system removes the item and displays `"Your Shopping Cart is empty!"`. Setting `Qty. = 0` is the removal mechanism of the SUT. See **`AN-05`**. | ✅ PASS |
| **`TX-02.03`** | **`TC-05`** | **`TP-03`** | With 2 different items, set `Qty.` of item 1 to `0`. Click `Update shopping cart`. Validate partial removal and recalculation. | **`TD-19`** | Item 1 is removed. The total is recalculated for the remaining item 2. The cart is not empty and does not display an empty cart message. This is different from **`TX-02.02`**. | ✅ PASS |

---

## 2. Summary

| Metric | Result |
| :--- | :--- |
| **Planned TX** | 3 |
| **Executed** | 3 |
| **PASS** | 3 |
| **FAIL** | 0 |
| **Pass Rate** | 100% |
| **Defects** | None |

> [!NOTE]
> **`TS-02`** meets the renegotiated exit criterion in **`EDN-01`**: 100% PASS, with no new Critical or High defects. Observation **`AN-05`** is not considered a functional defect and does not affect the result.

---

## 3. Evidence

| **`TX`** | **`TC`** | **`TP`** | Evidence |
| :--- | :--- | :--- | :--- |
| **`TX-02.01`** | **`TC-05`** | **`TP-03`** | [2026-05-05_TX-02.01_Cart_Recalculate_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.01_Cart_Recalculate_PASS.png) |
| **`TX-02.02`** | **`TC-10`** | **`TP-03`** | [2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png) |
| **`TX-02.03`** | **`TC-05`** | **`TP-03`** | [2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png](../test-evidence/ts-02-regression-suite/2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png) |

---

## 4. Traceability

| **`TP`** | **`TC`** | **`TD`** | **`TX`** | **`TCND`** | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`TP-03`** | **`TC-05`** | **`TD-04`** | **`TX-02.01`** | **`TCND-05`** | ✅ PASS |
| **`TP-03`** | **`TC-10`** | **`TD-19`** | **`TX-02.02`** | **`TCND-05`** | ✅ PASS |
| **`TP-03`** | **`TC-05`** | **`TD-19`** | **`TX-02.03`** | **`TCND-05`** | ✅ PASS |
