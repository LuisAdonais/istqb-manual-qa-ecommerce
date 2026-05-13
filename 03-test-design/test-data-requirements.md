
# Test Data Requirements

| Attribute      | Detail                                 |
| :---           | :---                                   |
| **Location**   | `03-test-design/test-data-requirements.md` |
| **Project**    | Tricentis Demo Web Shop                |
| **Version**    | 1.8                                    |
| **STLC Phase** | Test Design                            |
| **Status**     | ✅ Approved                            |
| **QA Owner**   | Luis Adonais Malave Gamardo            |

---

## 1. Test Data (`TD`)

### Search and Catalog

| ID          | **`TC`**       | Type               | Parameter                    | Value                       |
| :---        | :---           | :---               | :---                        | :---                        |
| **`TD-01`** | **`TC-01`**    | Input              | `Search store`              | `Computer`                  |
| **`TD-02`** | **`TC-02`**    | Input              | `Search store`              | `Inexistente999`            |
| **`TD-03`** | **`TC-03`**    | Navigation         | `Category > Subcategory`    | `Computers > Desktops`      |

### Shopping Cart

| ID          | **`TC`**                  | Type                        | Parameter | Value |
| :---        | :---                      | :---                        | :---      | :---  |
| **`TD-04`** | **`TC-05`**               | Input — Positive BVA        | `Qty.`    | `2`   |
| **`TD-19`** | **`TC-05`**, **`TC-10`**  | Input — Negative BVA        | `Qty.`    | `0`   |

### Registration and Authentication

| ID          | **`TC`**                       | Type                   | Parameter                        | Value                             |
| :---        | :---                           | :---                   | :---                             | :---                              |
| **`TD-06`** | **`TC-06`**, **`TC-07`**       | Input — EP             | `Gender`                         | `Male`                            |
| **`TD-07`** | **`TC-06`**, **`TC-07`**       | Input — EP             | `First name`                     | `QA`                              |
| **`TD-08`** | **`TC-06`**, **`TC-07`**       | Input — EP             | `Last name`                      | `Tester`                          |
| **`TD-09`** | **`TC-06`**, **`TC-07`**, **`TC-11`** | Input — EP      | `Email`                          | `qatest_demo01@tricentis.com`     |
| **`TD-10`** | **`TC-06`**, **`TC-07`**, **`TC-11`** | Input — EP      | `Password` / `Confirm password`  | `123456`                          |
| **`TD-11`** | **`TC-08`**                    | Input — Negative        | `Email`                          | `unregistered_qa@tricentis.com`   |
| **`TD-12`** | **`TC-08`**                    | Input — Negative        | `Password`                       | `randomPwd!`                      |
| **`TD-21`** | **`TC-11`**                    | Expected State          | Header session indicator         | `qatest_demo01@tricentis.com` — The SUT displays the registered email, not the name. Verified in **`TX-01.04`** |

### Checkout E2E

| ID          | **`TC`**    | Type           | Parameter              | Value                                         |
| :---        | :---        | :---           | :---                   | :---                                          |
| **`TD-13`** | **`TC-09`** | State          | User account           | Authenticated — Ref. **`TD-09`**, **`TD-10`** |
| **`TD-14`** | **`TC-09`** | Input          | `Country`              | `United States`                               |
| **`TD-15`** | **`TC-09`** | Input          | `City`                 | `New York`                                    |
| **`TD-16`** | **`TC-09`** | Input          | `Address 1`            | `5th Avenue 123`                              |
| **`TD-17`** | **`TC-09`** | Input          | `Zip / postal code`    | `10001`                                       |
| **`TD-18`** | **`TC-09`** | Input          | `Phone number`         | `5551234567`                                  |

---

## 2. Traceability

| **`TCND`**    | **`TC`**                 | **`TD`**                              |
| :---          | :---                     | :---                                  |
| **`TCND-01`** | **`TC-01`**              | **`TD-01`**                           |
| **`TCND-02`** | **`TC-02`**              | **`TD-02`**                           |
| **`TCND-03`** | **`TC-03`**              | **`TD-03`**                           |
| **`TCND-04`** | **`TC-04`**              | —                                     |
| **`TCND-05`** | **`TC-05`**, **`TC-10`** | **`TD-04`**, **`TD-19`**              |
| **`TCND-06`** | **`TC-06`**              | **`TD-06`** — **`TD-10`**             |
| **`TCND-07`** | **`TC-07`**              | **`TD-06`** — **`TD-10`**             |
| **`TCND-08`** | **`TC-08`**              | **`TD-11`**, **`TD-12`**              |
| **`TCND-09`** | **`TC-09`**              | **`TD-13`** — **`TD-18`**             |
| **`TCND-10`** | **`TC-11`**              | **`TD-09`**, **`TD-10`**, **`TD-21`** |
