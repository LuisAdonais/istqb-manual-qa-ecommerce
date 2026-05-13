
# Test Log — TL-01 (Smoke Suite)

| Attribute | Detail |
| :--- | :--- |
| **Location** | `05-test-execution/test-logs/tl-01-smoke-log.md` |
| **Suite** | **`TS-01`** — Smoke Test Suite |
| **Version** | 6.0 |
| **STLC Phase** | Test Execution — Test Logging |
| **Date** | 2026-05-04 / 2026-05-05 |
| **Environment** | Windows 10 Pro / Firefox 150.0.1 |
| **Status** | ✅ Completed |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Cycle Log

| **`TX`** | **`TC`** | **`TP`** | Verified Action | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`TX-01.01`** | **`TC-06`** | **`TP-01`** | Submit registration form with **`TD-06`** to **`TD-10`** | The system processes the form with no validation errors. All required fields are accepted. | ✅ PASS |
| **`TX-01.02`** | **`TC-07`** | **`TP-01`** | Validate success message after registration | The system displays `"Your registration completed"`. The user remains on the confirmation page. | ✅ PASS |
| **`TX-01.03`** | **`TC-08`** | **`TP-01`** | Attempt login with unregistered credentials (**`TD-11`**, **`TD-12`**) | The system blocks access and displays `"Login was unsuccessful. Please correct the errors and try again."` | ✅ PASS |
| **`TX-01.04`** | **`TC-11`** | **`TP-01`** | Login with valid credentials (**`TD-09`**, **`TD-10`**) | Successful authentication. The header shows `qatest_demo01@tricentis.com` as the indicator of active session (**`TD-21`**). | ✅ PASS |
| **`TX-01.05`** | **`TC-01`** | **`TP-02`** | Search with exact term (**`TD-01`**: `Computer`) | Results are displayed. The price order under the "Position" criterion is inconsistent (800 → 1200 → 1800 → 800). Inconsistent naming in the fourth result. → **`BUG-01`** | ❌ FAIL |
| **`TX-01.06`** | **`TC-02`** | **`TP-02`** | Search with invalid term (**`TD-02`**) | The system displays `"No products were found that matched your criteria."` | ✅ PASS |
| **`TX-01.07`** | **`TC-03`** | **`TP-02`** | Navigate to subcategory `Desktops` (**`TD-03`**) | Navigation is correct. The `Digital downloads` label uses Sentence Case instead of standard menu Title Case. → **`BUG-02`** | ❌ FAIL |
| **`TX-01.08`** | **`TC-04`** | **`TP-02`** | Select product to validate details page | Details page loaded. SKU field is not visible in the UI, failing to meet **`AC-04`**. → **`BUG-03`** | ❌ FAIL |

---

## 2. Summary

| Metric | Result |
| :--- | :--- |
| **Executed TX** | 8 / 8 |
| **PASS** | 5 |
| **FAIL** | 3 |
| **Pass Rate** | 62.5% |
| **Defects** | **`BUG-01`**, **`BUG-02`**, **`BUG-03`** |


> [!NOTE]
> Continuation of suites authorized via **`EDN-01`** (2026-05-04). The detected defects are Low/Medium and do not block Cart or Checkout flows.

---

## 3. Evidence

| **`TX`** | **`TC`** | **`TP`** | Evidence |
| :--- | :--- | :--- | :--- |
| **`TX-01.01`** | **`TC-06`** | **`TP-01`** | [2026-05-04_TX-01.01_Register_Submit_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.01_Register_Submit_PASS.png) |
| **`TX-01.02`** | **`TC-07`** | **`TP-01`** | [2026-05-04_TX-01.02_Register_Success_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.02_Register_Success_PASS.png) |
| **`TX-01.03`** | **`TC-08`** | **`TP-01`** | [2026-05-04_TX-01.03_Login_Fail_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.03_Login_Fail_PASS.png) |
| **`TX-01.04`** | **`TC-11`** | **`TP-01`** | [2026-05-04_TX-01.04_Login_Success_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-04_TX-01.04_Login_Success_PASS.png) |
| **`TX-01.05`** | **`TC-01`** | **`TP-02`** | [2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png) |
| **`TX-01.06`** | **`TC-02`** | **`TP-02`** | [2026-05-05_TX-01.06_Search_Empty_PASS.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.06_Search_Empty_PASS.png) |
| **`TX-01.07`** | **`TC-03`** | **`TP-02`** | [2026-05-05_TX-01.07_Category_Nav_BUG-02.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.07_Category_Nav_BUG-02.png) |
| **`TX-01.08`** | **`TC-04`** | **`TP-02`** | [2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png](../test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png)
