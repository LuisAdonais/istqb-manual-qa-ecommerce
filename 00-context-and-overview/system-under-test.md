
# System Under Test (SUT)

| Attribute      | Detail                                         |
| :---           | :---                                           |
| **Location**   | `00-context-and-overview/system-under-test.md` |
| **Project**    | Tricentis Demo Web Shop                        |
| **Version**    | 1.2                                            |
| **STLC Phase** | Pre-Planning                                   |
| **Status**     | ✅ Approved                                    |
| **QA Owner**   | Luis Adonais Malave Gamardo                    |

---

> [!NOTE]
> This project did not include previous functional documentation — it is a public demo environment for practice purposes. I created the **`REQ`** and **`AC`** by reverse engineering: I observed the SUT's real behavior and formalized what the system actually does. This is a known limitation of the context and the starting point for the entire cycle.

---

## Identification

| Attribute        | Detail                                        |
| :---             | :---                                          |
| **Name**         | Tricentis Demo Web Shop                       |
| **URL**          | <https://demowebshop.tricentis.com/>          |
| **Architecture** | Web — Client/Server                           |
| **Domain**       | E-commerce B2C                                |
| **Environment**  | Windows 10 Pro / Firefox 150.0.1 (64-bit)     |

---

## Stakeholders

| Role            | Functional Access                      |
| :---            | :---                                  |
| Guest User      | Navigation, search, cart              |
| Registered User | Login, checkout, order history        |

---

## Modules in Scope

| Module     | Ref. **`REQ`**   |
| :---       | :---             |
| Search     | **`REQ-01`**     |
| Catalog    | **`REQ-02`**     |
| Product    | **`REQ-03`**     |
| Cart       | **`REQ-04`**     |
| Register   | **`REQ-05`**     |
| Login      | **`REQ-06`**     |
| Checkout   | **`REQ-07`**     |

---

## Out of Scope

- Backend / APIs
- Database (SQL)
- Real payments
- Non-functional testing (load, security, accessibility)
