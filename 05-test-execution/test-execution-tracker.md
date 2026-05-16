
# Test Execution Tracker

| Attribute        | Detail                                         |
| :---             | :---                                           |
| **Location**     | `05-test-execution/test-execution-tracker.md`  |
| **Project**      | Tricentis Demo Web Shop                        |
| **Version**      | 4.0                                            |
| **STLC Phase**   | Test Execution — Test Monitoring & Control     |
| **Status**       | ✅ Completed                                   |
| **QA Owner**     | Luis Adonais Malave Gamardo                    |

---

## 1. Dashboard

| **`TS`**        | Description           | Total **`TX`** | Executed | PASS | FAIL | Progress   |
| :---            | :---                  | :---          | :---     | :--- | :--- | :---       |
| **`TS-01`**     | Smoke Test Suite      | 8             | 8        | 5    | 3    | 100%       |
| **`TS-02`**     | Full Regression Suite | 3             | 3        | 3    | 0    | 100%       |
| **`TS-03`**     | E2E Checkout Suite    | 1             | 1        | 1    | 0    | 100%       |
| **TOTAL**       | —                     | **12**        | **12**   | **9**| **3**| **100%**   |

---

## 2. Detailed Register

| **`TX`**        | **`TL`**  | **`TC`**  | Verified Action                                 | Date        | Status      |
| :---            | :---      | :---      | :---                                            | :---        | :---        |
| **`TX-01.01`**  | **`TL-01`** | **`TC-06`** | Register with valid data                     | 2026-05-04  | ✅ PASS     |
| **`TX-01.02`**  | **`TL-01`** | **`TC-07`** | Success message after registration            | 2026-05-04  | ✅ PASS     |
| **`TX-01.03`**  | **`TL-01`** | **`TC-08`** | Login with invalid credentials                | 2026-05-04  | ✅ PASS     |
| **`TX-01.04`**  | **`TL-01`** | **`TC-11`** | Login with valid credentials                  | 2026-05-04  | ✅ PASS     |
| **`TX-01.05`**  | **`TL-01`** | **`TC-01`** | Exact search — **`BUG-01`**                   | 2026-05-05  | ❌ FAIL     |
| **`TX-01.06`**  | **`TL-01`** | **`TC-02`** | Search with no results                        | 2026-05-05  | ✅ PASS     |
| **`TX-01.07`**  | **`TL-01`** | **`TC-03`** | Subcategory navigation — **`BUG-02`**         | 2026-05-05  | ❌ FAIL     |
| **`TX-01.08`**  | **`TL-01`** | **`TC-04`** | Product details attributes — **`BUG-03`**     | 2026-05-05  | ❌ FAIL     |
| **`TX-02.01`**  | **`TL-02`** | **`TC-05`** | Sub-Total recalculation (Qty = 2)             | 2026-05-05  | ✅ PASS     |
| **`TX-02.02`**  | **`TL-02`** | **`TC-10`** | Remove all items from cart (Qty = 0)          | 2026-05-05  | ✅ PASS     |
| **`TX-02.03`**  | **`TL-02`** | **`TC-05`** | Partial cart removal (Qty = 0, 2 items)       | 2026-05-05  | ✅ PASS     |
| **`TX-03.01`**  | **`TL-03`** | **`TC-09`** | Complete checkout — order generated           | 2026-05-05  | ✅ PASS     |

---

## 3. Metrics

| Metric                   | Formula                                  | Result             |
| :---                     | :---                                     | :---               |
| **Global Pass Rate**     | PASS / Executed × 100                    | **75% (9/12)**     |
| **E2E Pass Rate**        | PASS TS-03 / TX TS-03 × 100              | **100% (1/1)**     |
| **Defect density**       | BUGs / TX                                | **0.25 (3/12)**    |
| **Completeness**         | Executed / Planned × 100                 | **100% (12/12)**   |

---

## 4. Defects

| **`BUG`**     | **`TX`**       | **`TC`**    | Severity  | Status    |
| :---          | :---           | :---        | :---      | :---      |
| **`BUG-01`**  | **`TX-01.05`** | **`TC-01`** | Low   | 🔴 Open   |
| **`BUG-02`**  | **`TX-01.07`** | **`TC-03`** | Low       | 🔴 Open   |
| **`BUG-03`**  | **`TX-01.08`** | **`TC-04`** | Medium    | 🔴 Open   |
