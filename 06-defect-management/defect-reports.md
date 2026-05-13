
# Defect Reports Index

| Attribute     | Detail                                         |
| :---          | :---                                           |
| **Location**  | `06-defect-management/defect-reports.md`       |
| **Project**   | Tricentis Demo Web Shop                        |
| **Version**   | 1.1                                            |
| **STLC Phase**| Defect Management                              |
| **Status**    | 🔴 Active defects                              |
| **QA Owner**  | Luis Adonais Malave Gamardo                    |

---

## 1. Defect Inventory

| **`BUG`** | Title | **`TX`** | **`TC`** | Severity | Status | File | Jira |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | Incoherence in price sequence and naming in search results | **`TX-01.05`** | **`TC-01`** | Medium | 🔴 Open | [bug-01-price-incoherence.md](./bug-01-price-incoherence.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-01_Jira-Issue.png) |
| **`BUG-02`** | Capitalization inconsistency in sidebar category menu | **`TX-01.07`** | **`TC-03`** | Low | 🔴 Open | [bug-02-capitalization-inconsistency.md](./bug-02-capitalization-inconsistency.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-02_Jira-Issue.png) |
| **`BUG-03`** | Missing SKU field on product details page | **`TX-01.08`** | **`TC-04`** | Medium | 🔴 Open | [bug-03-missing-sku-field.md](./bug-03-missing-sku-field.md) | [Issue](../05-test-execution/test-evidence/jira-evidence/2026-05-05_BUG-03_Jira-Issue.png) |

---

## 2. Metrics

| Metric             | Value                                     |
| :---               | :---                                      |
| **Total defects**  | 3                                         |
| **Open**           | 3                                         |
| **Closed / Fixed** | 0                                         |
| **Critical**       | 0                                         |
| **High**           | 0                                         |
| **Medium**         | 1 — **`BUG-03`**                          |
| **Low**            | 2 — **`BUG-01`**, **`BUG-02`**            |
| **Continuation decision** | **`EDN-01`** — Authorized (2026-05-04) |

---

## 3. Traceability

| **`BUG`** | **`TX`**    | **`TS`**  | Impact on **`TS-02`** / **`TS-03`**                | Plan                                     |
| :---      | :---        | :---      | :---                                               | :---                                     |
| **`BUG-01`** | **`TX-01.05`** | **`TS-01`** | None                                            | Pending next cycle                        |
| **`BUG-02`** | **`TX-01.07`** | **`TS-01`** | None                                            | Pending next cycle                        |
| **`BUG-03`** | **`TX-01.08`** | **`TS-01`** | None — continuation authorized by **`EDN-01`**  | Pending before stabilization closure      |
