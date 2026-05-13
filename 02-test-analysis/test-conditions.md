
# Test Conditions

| Attribute | Detail |
| :--- | :--- |
| **Location** | `02-test-analysis/test-conditions.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.5 |
| **STLC Phase** | Test Analysis |
| **Status** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Test Conditions (**`TCND`**)

Atomic statements derived from the approved **`AC`**. They define what must be verified before designing test cases.

| ID | **`AC`** | Test Condition | Priority | **`RISK`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TCND-01`** | **`AC-01`** | Validate that search results are displayed in alphabetical order when there is an exact match. | High | **`RISK-01`** |
| **`TCND-02`** | **`AC-02`** | Validate that the system displays the zero-results message when there are no matches found. | Medium | **`RISK-01`** |
| **`TCND-03`** | **`AC-03`** | Validate that category navigation lists only the products of the selected subcategory. | Medium | — |
| **`TCND-04`** | **`AC-04`** | Validate that the product details page shows Name, Price, SKU, and `Qty.` input field simultaneously. | High | — |
| **`TCND-05`** | **`AC-05`** | Validate the `Sub-Total` recalculation when modifying item quantities and removing items from the cart. | Critical | **`RISK-03`** |
| **`TCND-06`** | **`AC-06`** | Validate email format (`x@x.x`) and a minimum password length of 6 characters during registration. | High | — |
| **`TCND-07`** | **`AC-07`** | Validate the confirmation message after a valid registration and that there is no automatic redirection. | High | — |
| **`TCND-08`** | **`AC-08`** | Validate access is blocked and an error message is displayed for unregistered credentials. | High | **`RISK-02`** |
| **`TCND-09`** | **`AC-09`** | Validate the order confirmation and that an ID is generated after completing checkout. | Critical | **`RISK-04`** |
| **`TCND-10`** | **`AC-10`** | Validate successful authentication and that the registered email is displayed in the header with valid credentials. | High | **`RISK-02`** |

---

## 2. Traceability

| **`REQ`** | **`AC`** | **`TCND`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | **`AC-01`**, **`AC-02`** | **`TCND-01`**, **`TCND-02`** | **`RISK-01`** |
| **`REQ-02`** | **`AC-03`** | **`TCND-03`** | — |
| **`REQ-03`** | **`AC-04`** | **`TCND-04`** | — |
| **`REQ-04`** | **`AC-05`** | **`TCND-05`** | **`RISK-03`** |
| **`REQ-05`** | **`AC-06`**, **`AC-07`** | **`TCND-06`**, **`TCND-07`** | — |
| **`REQ-06`** | **`AC-08`**, **`AC-10`** | **`TCND-08`**, **`TCND-10`** | **`RISK-02`** |
| **`REQ-07`** | **`AC-09`** | **`TCND-09`** | **`RISK-04`** |
