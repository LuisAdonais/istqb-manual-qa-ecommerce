
# Test Suites

| Attribute     | Detail                                 |
| :---          | :---                                   |
| **Location**  | `04-test-implementation/test-suites.md`|
| **Project**   | Tricentis Demo Web Shop                |
| **Version**   | 1.7                                    |
| **STLC Phase**| Test Implementation                    |
| **Status**    | ✅ Approved                            |
| **QA Owner**  | Luis Adonais Malave Gamardo            |

---

## 1. Execution Rules

- Execute in order: **`TS-01`** → **`TS-02`** → **`TS-03`**
- Clear cache and cookies before each suite
- Environment: Windows 10 Pro / Firefox 150.0.1

---

## 2. Entry Criteria

| Suite       | Entry Criteria                                                              |
| :---        | :---                                                                       |
| **`TS-01`** | Environment configured. Clean cache. **`TD-09`** account pre-created        |
| **`TS-02`** | **`TS-01`** completed with no open Critical or High defects                |
| **`TS-03`** | **`TS-01`** completed with no open Critical or High defects                |

---

## 3. Suspension Criteria

| Suite       | Suspension Condition                                                       | Resumption                        |
| :---        | :---                                                                      | :---                              |
| **`TS-02`** | FAIL in login or catalog with Critical or High severity in **`TS-01`**     | Upon confirmation of **`BUG`** fix |
| **`TS-03`** | Server error (500) when adding products to cart                            | Upon confirmation of **`BUG`** fix |

---

## 4. Suites

### **`TS-01`** — Smoke test

**Objective:** Verify system under test availability and operation of critical modules.

| Sequence | **`TP`**    | Validation                              |
| :---     | :---        | :---                                    |
| 1        | **`TP-01`** | Successful registration, login, and failed login |
| 2        | **`TP-02`** | Search and catalog navigation           |

**Exit Criteria:**

| Result              | Action                                                            |
| :---                | :---                                                              |
| All PASS            | Suite approved — proceed with **`TS-02`** and **`TS-03`**         |
| FAIL Critical / High| Suspend execution                                                 |
| FAIL Low / Medium   | Continue with controlled risk — document in **`EDN`**             |

---

### **`TS-02`** — Regression

**Objective:** Verify the Shopping Cart module in response to defects found during **`TS-01`**.

**Precondition:** **`TS-01`** completed with no open Critical or High defects.

> [!NOTE]
>
> **Scope of execution:** **`TP-01`** and **`TP-02`** were not re-executed in this suite,
> since no defects were found in Registration, Login, Search, or Catalog modules during
> **`TS-01`**. Regression focused on the Shopping Cart module (**`TP-03`**), which was not
> covered in the Smoke suite. Decision documented in [**`EDN-01`**](./05-test-execution/decisions/edn-01-execution-decision-note.md).

| Sequence | **`TP`**    | Covered **`TC`**                             |
| :---     | :---        | :---                                         |
| 1        | **`TP-03`** | **`TC-05`**, **`TC-09`**, **`TC-10`**        |

---

### **`TS-03`** — E2E checkout

**Objective:** Validate the complete purchase workflow from login to order confirmation.

**Precondition:** **`TS-01`** approved. Active session with **`TD-09`** and **`TD-10`**.

| Sequence | **`TP`**    | Instruction                                         |
| :---     | :---        | :---                                                |
| 1        | **`TP-01`** | Execute **`TC-11`** to establish active session     |
| 2        | **`TP-02`** | Navigate catalog and add product to cart            |
| 3        | **`TP-03`** | Validate cart and execute checkout to order confirmation |

> [!NOTE]
>
> **`TC-04`** is executed within **`TP-02`** as an implicit navigation step in **`TS-03`**.
> Its formal validation occurs in **`TS-01`**.

---

## 5. Traceability

| **`TS`**    | Type       | **`TP`**                              | Included **`TC`**                                                |
| :---        | :---       | :---                                  | :---                                                             |
| **`TS-01`** | Smoke      | **`TP-01`**, **`TP-02`**              | **`TC-01`** — **`TC-04`**, **`TC-06`** — **`TC-08`**, **`TC-11`**|
| **`TS-02`** | Regression | **`TP-03`**                           | **`TC-05`**, **`TC-09`**, **`TC-10`**                            |
| **`TS-03`** | E2E        | **`TP-01`**, **`TP-02`**, **`TP-03`** | **`TC-04`**\*, **`TC-05`**, **`TC-09`**, **`TC-10`**, **`TC-11`**|
