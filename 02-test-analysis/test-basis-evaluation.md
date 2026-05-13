
# Test Basis Evaluation

| Attribute      | Detail                                         |
| :---           | :---                                           |
| **Location**   | `02-test-analysis/test-basis-evaluation.md`    |
| **Project**    | Tricentis Demo Web Shop                        |
| **Version**    | 1.6                                            |
| **STLC Phase** | Test Analysis — Static Testing                 |
| **Status**     | ✅ Approved                                    |
| **QA Owner**   | Luis Adonais Malave Gamardo                    |

---

## 1. Static Anomalies (`AN`)

Findings identified during the static review of the test basis (**`REQ`** and **`AC`**).

| ID          | Origin        | Finding                                                                                                                                                                   | Severity | Status                                                                                               |
| :---        | :---          | :---                                                                                                                                                                     | :---     | :---                                                                                                |
| **`AN-01`** | **`REQ-05`**  | Email and password validation rules were not defined in the original requirement.                                                  | Medium   | ✅ Resolved — **`AC-06`** adjusted                                                                   |
| **`AN-02`** | **`REQ-07`**  | The original requirement included an email notification after checkout. The SUT only generates an order ID on screen.                | High     | ✅ Resolved — **`AC-09`** adjusted to actual SUT behavior                                            |
| **`AN-03`** | **`AC-01`**   | The acceptance criterion did not specify the expected sort order in search results.                                                | Low      | ✅ Resolved — Alphabetical order confirmed and formalized                                            |
| **`AN-04`** | **`REQ-06`**  | The positive authentication scenario had no associated **`AC`**.                                                                  | Medium   | ✅ Resolved — **`AC-10`** defined, **`TCND-10`** and **`TC-11`** derived                             |
| **`AN-05`** | **`REQ-04`**  | The SUT does not provide visual quantity controls in the cart. Entering `0` in `Qty.` removes the item — this behavior was not documented in the **`REQ`**. | Low      | 🟡 Open — Usability improvement. No impact on **`AC-05`**. Confirmed in **`TX-02.02`**.              |

---

## 2. Traceability

| **`REQ`**    | **`AN`**   | Status                                 |
| :---         | :---       | :---                                   |
| **`REQ-01`** | **`AN-03`**| ✅ Ready                               |
| **`REQ-02`** | —          | ✅ Ready                               |
| **`REQ-03`** | —          | ✅ Ready                               |
| **`REQ-04`** | **`AN-05`**| 🟡 Suggested improvement — does not block |
| **`REQ-05`** | **`AN-01`**| ✅ Ready                               |
| **`REQ-06`** | **`AN-04`**| ✅ Ready                               |
| **`REQ-07`** | **`AN-02`**| ✅ Ready                               |
