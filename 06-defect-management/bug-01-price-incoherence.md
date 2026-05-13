# Defect Report — BUG-01

| Attribute     | Detail                                                                       |
| :---          | :---                                                                         |
| **Location**  | `06-defect-management/bug-01-price-incoherence.md`                           |
| **ID**        | **`BUG-01`**                                                                 |
| **Title**     | Incoherence in price sequence and naming in search results                   |
| **Status**    | 🔴 Open                                                                      |
| **Date**      | 2026-05-05                                                                   |
| **Ref. TX**   | **`TX-01.05`**                                                               |
| **Ref. TC**   | **`TC-01`**                                                                  |
| **Ref. REQ**  | **`REQ-01`** / **`AC-01`**                                                   |
| **Severity**  | Medium                                                                       |
| **Priority**  | Medium                                                                       |
| **QA Owner**  | Luis Adonais Malave Gamardo                                                  |

---

## 1. Description

When executing a search with the term `Computer`, the first three results display an ascending price sequence and a consistent naming convention (`Build your own...`). The fourth result breaks both patterns: its price ($800.00) repeats the value of the first result and its name (`Simple Computer`) does not follow the category naming convention.

The defect was identified during the verification of **`AC-01`** (results ordering). It represents an incidental finding of data integrity within the result list.

---

## 2. Steps to Reproduce

1. Navigate to `https://demowebshop.tricentis.com/`
2. Enter `Computer` in the search bar
3. Click on `Search`
4. Validate the price sequence and naming convention of the results when sorted by position

---

## 3. Results

|              | Detail                                                                                              |
| :---         | :---                                                                                                |
| **Expected** | Ascending price sequence (800 → 1200 → 1800). Consistent naming (`Build your own...`)               |
| **Actual**   | The fourth product (`Simple Computer`, $800.00) breaks the price sequence and the naming pattern    |

---

## 4. Classification

| Attribute     | Value                                                                                                                                           |
| :---          | :---                                                                                                                                            |
| **Severity**  | Low — data/presentation defect; the search and purchase flow is not blocked                              |
| **Priority**  | Medium — data inconsistency in search results; does not block purchase flow but impacts product comparison experience |
| **Environment**| Windows 10 Pro / Firefox 150.0.1                                                                       |

---

## 5. Evidence

[2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png](../05-test-execution/test-evidence/ts-01-smoke-suite/2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png)

- Green boxes: correct ascending sequence (800 → 1200 → 1800)
- Red box: failure point — fourth result with inconsistent price and name

**Jira:** [View issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-01_Jira-Issue.png)

---

## 6. Traceability

| **`TX`**      | **`TC`**   | **`REQ`** / **`AC`**           | Verdict  | **`BUG`**     |
| :---          | :---       | :---                           | :---     | :---          |
| **`TX-01.05`**| **`TC-01`**| **`REQ-01`** / **`AC-01`**     | ❌ FAIL  | **`BUG-01`**  |
