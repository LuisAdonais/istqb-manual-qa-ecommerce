
# Requirements Specification

| Attribute | Detail |
| :--- | :--- |
| **Location** | `02-test-analysis/requirements.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.6 |
| **STLC Phase** | Test Analysis |
| **Status** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

> [!NOTE]
> These requirements were not provided by a client or product team. I created them by reverse engineering: each **`REQ`** describes an observable behavior of the SUT, and each **`AC`** formalizes the verifiable acceptance criterion derived from that observation. Any anomalies detected during this process are documented in **`test-basis-evaluation.md`**.

---

## 1. Functional Requirements (**`REQ`**)

| ID | Module | Description | Priority |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | Search | The system returns product results based on text matching. | High |
| **`REQ-02`** | Catalog | The system allows navigation of products by category and subcategory. | Medium |
| **`REQ-03`** | Product | The system displays a product details page with price, SKU, and quantity control. | High |
| **`REQ-04`** | Cart | The system manages cart items and recalculates totals when quantities are modified. | High |
| **`REQ-05`** | Registration | The system creates user accounts by validating email format and password. | High |
| **`REQ-06`** | Login | The system authenticates registered users and blocks invalid access. | High |
| **`REQ-07`** | Checkout | The system processes the purchase flow and confirms the order generation. | Critical |

---

## 2. Acceptance Criteria (**`AC`**)

| ID | **`REQ`** | Acceptance Criteria | Status |
| :--- | :--- | :--- | :--- |
| **`AC-01`** | **`REQ-01`** | Results are displayed in alphabetical order when there is an exact match. | ✔️ Verifiable |
| **`AC-02`** | **`REQ-01`** | The system displays `"No products were found that matched your criteria."` when there are zero results. | ✔️ Verifiable |
| **`AC-03`** | **`REQ-02`** | When selecting a category or subcategory, the system lists the corresponding products. | ✔️ Verifiable |
| **`AC-04`** | **`REQ-03`** | The detail view shows Name, Price, SKU, and `Qty.` input field simultaneously. | ⚠️ Not Met — SKU field is missing in the SUT. See **`BUG-03`** |
| **`AC-05`** | **`REQ-04`** | The `Sub-Total` value reflects the sum of (Price × Qty) for all items in the cart after each modification or removal. | ✔️ Verifiable |
| **`AC-06`** | **`REQ-05`** | The system validates the format `x@x.x` for emails and enforces a minimum of 6 characters for passwords. | ✔️ Verifiable |
| **`AC-07`** | **`REQ-05`** | The system displays `"Your registration completed"` after a valid registration. | ✔️ Verifiable |
| **`AC-08`** | **`REQ-06`** | The system blocks access and displays an error for unregistered credentials. | ✔️ Verifiable |
| **`AC-09`** | **`REQ-07`** | The system displays `"Your order has been successfully processed!"` along with the order ID. | ✔️ Verifiable |
| **`AC-10`** | **`REQ-06`** | The system displays the registered email in the header upon successful authentication. | ✔️ Verifiable |

---

## 3. Traceability

| **`REQ`** | **`AC`** | **`TCND`** |
| :--- | :--- | :--- |
| **`REQ-01`** | **`AC-01`**, **`AC-02`** | **`TCND-01`**, **`TCND-02`** |
| **`REQ-02`** | **`AC-03`** | **`TCND-03`** |
| **`REQ-03`** | **`AC-04`** | **`TCND-04`** |
| **`REQ-04`** | **`AC-05`** | **`TCND-05`** |
| **`REQ-05`** | **`AC-06`**, **`AC-07`** | **`TCND-06`**, **`TCND-07`** |
| **`REQ-06`** | **`AC-08`**, **`AC-10`** | **`TCND-08`**, **`TCND-10`** |
| **`REQ-07`** | **`AC-09`** | **`TCND-09`** |
