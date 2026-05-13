# Test Plan

| Attribute | Detail |
| :--- | :--- |
| **Location** | `01-test-planning/test-plan.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.6 |
| **STLC Phase** | Test Planning |
| **Status** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

> [!NOTE]
> I executed this project individually, with no development team or previous functional documentation. I created the test basis (**`REQ`** and **`AC`**) by reverse engineering the SUT, which means that analysis, design, and execution were my responsibility. This is a real limitation that this plan does not hide.

---

## 1. Scope

### In Scope

| Module | **`REQ`** |
| :--- | :--- |
| Search and Navigation | **`REQ-01`**, **`REQ-02`** |
| Product and Cart | **`REQ-03`**, **`REQ-04`** |
| Registration and Login | **`REQ-05`**, **`REQ-06`** |
| Checkout E2E | **`REQ-07`** |

### Out of Scope

- Backend, APIs, database
- Real payments
- Non-functional testing

---

## 2. Objectives

- Validate the functional behavior of the SUT against **`REQ`** and **`AC`**.
- Verify the integrity of the E2E purchase flow.
- Identify defects (**`BUG`**) in high criticality functionalities.

---

## 3. Test Approach

| Category | Definition |
| :--- | :--- |
| **Level** | System Testing |
| **Type** | Functional Testing — Black Box |
| **Strategy** | Risk-Based Testing |

**Applied Techniques:**

| Technique | Application |
| :--- | :--- |
| Equivalence Partitioning (EP) | Field validation in registration form |
| Boundary Value Analysis (BVA) | Cart quantity limits — **`TC-05`**, **`TC-10`** |
| State Transition | Sequential Checkout flow |
| Error Guessing | Negative scenarios in Login and Registration |

---
**Tools Used:**

| Tool | Purpose |
| :---        | :---      |
| Firefox 150.0.1 | Test execution browser |
| ShareX | Evidence capture (`PNG`) |
| Jira (Scrum board) | Defect logging and tracking |
| VSCode | Markdown artifact authoring and management |
| GitHub | Portfolio repository and version control |

## 4. Entry and Exit Criteria

### Entry Criteria

- Test environment stable and accessible
- Test basis (**`REQ`** and **`AC`**) defined and approved
- Static anomalies (**`AN`**) documented
- Test data (**`TD`**) specified

### Exit Criteria

| Criterion | Threshold |
| :--- | :--- |
| Test cases executed | 100% |
| Pass rate in **`TS-03`** (E2E) | ≥ 90% |
| Open Critical / High defects | 0 |

---

## 5. Product Risks

| ID | Description | Priority | Mitigation |
| :--- | :--- | :--- | :--- |
| **`RISK-01`** | Inconsistency in search results | High | Covered by **`TCND-01`**, **`TCND-02`** |
| **`RISK-02`** | Failure in user authentication | High | Covered by **`TCND-08`**, **`TCND-10`** |
| **`RISK-03`** | Incorrect calculation of cart totals | Critical | BVA on **`TCND-05`** |
| **`RISK-04`** | Blocker in order number generation | Critical | E2E flow **`TCND-09`** |

---

## 6. Traceability

| **`REQ`** | **`TCND`** | **`TC`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | **`TCND-01`**, **`TCND-02`** | **`TC-01`**, **`TC-02`** | **`RISK-01`** |
| **`REQ-02`** | **`TCND-03`** | **`TC-03`** | — |
| **`REQ-03`** | **`TCND-04`** | **`TC-04`** | — |
| **`REQ-04`** | **`TCND-05`** | **`TC-05`**, **`TC-10`** | **`RISK-03`** |
| **`REQ-05`** | **`TCND-06`**, **`TCND-07`** | **`TC-06`**, **`TC-07`** | — |
| **`REQ-06`** | **`TCND-08`**, **`TCND-10`** | **`TC-08`**, **`TC-11`** | **`RISK-02`** |
| **`REQ-07`** | **`TCND-09`** | **`TC-09`** | **`RISK-04`** |
