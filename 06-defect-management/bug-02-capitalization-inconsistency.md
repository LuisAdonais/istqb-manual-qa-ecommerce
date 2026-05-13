
# Defect Report — BUG-02

| Attribute     | Detail                                                         |
| :---          | :---                                                           |
| **Location**  | `06-defect-management/bug-02-capitalization-inconsistency.md`  |
| **ID**        | **`BUG-02`**                                                   |
| **Title**     | Capitalization inconsistency in sidebar category menu          |
| **Status**    | 🔴 Open                                                        |
| **Date**      | 2026-05-05                                                     |
| **Ref. TX**   | **`TX-01.07`**                                                 |
| **Ref. TC**   | **`TC-03`**                                                    |
| **Ref. REQ**  | **`REQ-02`** / **`AC-03`**                                     |
| **Severity**  | Low                                                            |
| **Priority**  | Low                                                            |
| **QA Owner**  | Luis Adonais Malave Gamardo                                    |

---

## 1. Description

While validating the sidebar category menu, the label `Digital downloads` uses Sentence Case instead of the standard Title Case applied throughout the menu. The inconsistency is cosmetic and does not block navigation.

---

## 2. Steps to Reproduce

1. Navigate to `https://demowebshop.tricentis.com/`
2. Locate the sidebar menu under the `Categories` section
3. Compare the capitalization of `Digital downloads` with the adjacent categories (`Apparel & Shoes`, `Gift Cards`)

---

## 3. Results

|             | Detail                                                                              |
| :---        | :---                                                                                |
| **Expected**| All labels use Title Case. Expected value: `Digital Downloads`                      |
| **Actual**  | The category appears as `Digital downloads` — second word in lowercase              |

---

## 4. Classification

| Attribute     | Value                                                                 |
| :---          | :---                                                                  |
| **Severity**  | Low — cosmetic defect; does not block navigation or functional flow   |
| **Priority**  | Low                                                                   |
| **Environment**| Windows 10 Pro / Firefox 150.0.1                                    |

---

## 5. Evidence

[2026-05-05_TX-01.07_Category_Nav_BUG-02.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.07_Category_Nav_BUG-02.png)

**Jira:** [See issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-02_Jira-Issue.png)

- Green boxes: `Apparel & Shoes`, `Gift Cards` — correct Title Case
- Red box: `Digital downloads` — incorrect Sentence Case

---

## 6. Traceability

| **`TX`**      | **`TC`**   | **`REQ`** / **`AC`**        | Verdict   | **`BUG`**    |
| :---          | :---       | :---                        | :---      | :---         |
| **`TX-01.07`**| **`TC-03`**| **`REQ-02`** / **`AC-03`**  | ❌ FAIL   | **`BUG-02`** |
