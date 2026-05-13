
# Defect Report — BUG-03

| Attribute      | Detail                                                      |
| :---           | :---                                                        |
| **Location**   | `06-defect-management/bug-03-missing-sku-field.md`          |
| **ID**         | **`BUG-03`**                                                |
| **Title**      | Missing SKU field in product details page                   |
| **Status**     | 🔴 Open                                                     |
| **Date**       | 2026-05-05                                                  |
| **Ref. TX**    | **`TX-01.08`**                                              |
| **Ref. TC**    | **`TC-04`**                                                 |
| **Ref. REQ**   | **`REQ-03`** / **`AC-04`**                                  |
| **Severity**   | Medium                                                      |
| **Priority**   | Medium                                                      |
| **QA Owner**   | Luis Adonais Malave Gamardo                                 |

---

## 1. Description

While verifying the product details page for `"Build your own cheap computer"`, the **SKU** field is not visible in the UI. This directly violates **`AC-04`**, which requires Name, Price, SKU, and `Qty.` input to all be visible at the same time on the details view.

---

## 2. Steps to Reproduce

1. Navigate to `Computers > Desktops`
2. Select the product `Build your own cheap computer`
3. Go to the product details view
4. Inspect the upper area of the details page, next to the product name and availability

---

## 3. Results

|                | Detail                                                                                           |
| :---           | :---                                                                                            |
| **Expected**   | The SKU field is visible next to Name, Price, and `Qty.` input                                   |
| **Actual**     | The SKU field is not shown in any section of the product details page                            |

---

## 4. Classification

| Attribute      | Value                                                                              |
| :---           | :---                                                                               |
| **Severity**   | Medium — data integrity failure; affects inventory traceability for the end user    |
| **Priority**   | Medium — must be resolved before the end of the stabilization cycle                 |
| **Environment**| Windows 10 Pro / Firefox 150.0.1                                                   |

---

## 5. Evidence

[2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png)

- Green boxes: Name, Price, `Qty.` — present and correct
- Red box: SKU field missing

**Jira:** [View issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-03_Jira-Issue.png)

---

## 6. Traceability

| **`TX`**      | **`TC`**   | **`REQ`** / **`AC`**      | Verdict   | **`BUG`**    |
| :---          | :---       | :---                      | :---      | :---         |
| **`TX-01.08`**| **`TC-04`**| **`REQ-03`** / **`AC-04`**| ❌ FAIL   | **`BUG-03`** |
