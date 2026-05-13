# Test Cases

| Attribute      | Detail                        |
| -------------- | ----------------------------- |
| **Location**   | `03-test-design/test-cases.md`|
| **Project**    | Tricentis Demo Web Shop       |
| **Version**    | 1.6                           |
| **STLC Phase** | Test Design                   |
| **Status**     | ✅ Approved                   |
| **QA Owner**   | Luis Adonais Malave Gamardo   |

---

## Module: Search and Catalog

### `**TC-01**` — Successful search with exact term

| Field           | Detail                      |
| --------------- | -------------------------- |
| `**TCND**`      | `**TCND-01**`              |
| **Technique**   | Black-box                  |
| **Precondition**| User on the home page      |

| #   | Step                                       | Expected Result                            |
| --- | ------------------------------------------ | ------------------------------------------ |
| 1   | Enter `Computer` in `Search store`         | Field accepts the input                    |
| 2   | Click on `Search`                          | System displays products in alphabetical order |

---

### `**TC-02**` — Search with no results

| Field           | Detail                      |
| --------------- | -------------------------- |
| `**TCND**`      | `**TCND-02**`              |
| **Technique**   | Error Guessing             |
| **Precondition**| User on the home page      |

| #   | Step                                            | Expected Result                                            |
| --- | ----------------------------------------------- | --------------------------------------------------------- |
| 1   | Enter `Inexistente999` in `Search store`        | Field accepts the input                                   |
| 2   | Click on `Search`                               | System displays `"No products were found that matched your criteria."` |

---

### `**TC-03**` — Category navigation

| Field           | Detail                      |
| --------------- | -------------------------- |
| `**TCND**`      | `**TCND-03**`              |
| **Technique**   | Black-box                  |
| **Precondition**| User on the home page      |

| #   | Step                                  | Expected Result                                  |
| --- | ------------------------------------- | ------------------------------------------------ |
| 1   | Click on category `Computers`         | System expands the subcategories                 |
| 2   | Select subcategory `Desktops`         | System lists only `Desktops` products            |

---

### `**TC-04**` — Product details view

| Field           | Detail                                |
| --------------- | ------------------------------------- |
| `**TCND**`      | `**TCND-04**`                         |
| **Technique**   | Black-box                             |
| **Precondition**| User is viewing a product listing     |

| #   | Step                                         | Expected Result                                                       |
| --- | -------------------------------------------- | --------------------------------------------------------------------- |
| 1   | Click on the image or title of any product   | System displays Name, Price, SKU, `Qty.` input, and `Add to cart` button |

---

## Module: Shopping Cart

### `**TC-05**` — Partial removal and recalculation of cart (positive BVA)

| Field           | Detail                                       |
| --------------- | -------------------------------------------- |
| `**TCND**`      | `**TCND-05**`                                |
| **Technique**   | Boundary Value Analysis (BVA)                |
| **Precondition**| Cart contains **2 different products**       |

| #   | Step                                                                      | `**TD**`     | Expected Result                                                                            |
| --- | ------------------------------------------------------------------------- | ------------ | ------------------------------------------------------------------------------------------ |
| 1   | Navigate to `/cart`                                                       | —            | System displays items and totals                                                           |
| 2   | Change `Qty.` of item 1 to `2`. Click on `Update shopping cart`           | `**TD-04**`  | Item 1 `Sub-Total` is updated to price × 2. Item 2 does not change                        |
| 3   | Change `Qty.` of item 1 to `0`. Click on `Update shopping cart`           | `**TD-19**`  | Item 1 is removed. Total reflects only item 2. Cart is not empty                          |

---

### `**TC-10**` — Total removal of the cart (negative BVA)

| Field           | Detail                           |
| --------------- | -------------------------------- |
| `**TCND**`      | `**TCND-05**`                   |
| **Technique**   | Boundary Value Analysis (BVA)    |
| **Precondition**| Cart contains **1 product**      |

| #   | Step                                            | `**TD**`    | Expected Result                                             |
| --- | ----------------------------------------------- | ----------- | ---------------------------------------------------------- |
| 1   | Navigate to `/cart`                             | —           | System displays the item and the total                     |
| 2   | Change `Qty.` to `0`. Click on `Update shopping cart` | `**TD-19**` | The item is removed. System displays `"Your Shopping Cart is empty!"` |

> [!NOTE]
>
> `TC-05` and `TC-10` share the same input value (`Qty. = 0`),
> but they are not redundant. The difference is in the precondition:
>
> - `TC-05` validates partial removal and total recalculation when the cart has more than one item.
> - `TC-10` validates complete removal when the deleted item is the only one in the cart.
>
> This is a deliberate test design decision, not a duplication error.

---

## Module: Registration and Authentication

### `**TC-06**` — Registration with valid data (EP)

| Field           | Detail                        |
| --------------- | ---------------------------- |
| `**TCND**`      | `**TCND-06**`                |
| **Technique**   | Equivalence Partitioning (EP) |
| **Precondition**| User on `/register`           |

| #   | Step                                            | `**TD**`                               | Expected Result                            |
| --- | ----------------------------------------------- | -------------------------------------- | ------------------------------------------ |
| 1   | Select gender. Enter first name and last name   | `**TD-06**`, `**TD-07**`, `**TD-08**`  | System accepts the data                    |
| 2   | Enter valid email and password                  | `**TD-09**`, `**TD-10**`               | System does not display validation errors  |
| 3   | Click on `Register`                             | —                                      | System processes the form without errors   |

---

### `**TC-07**` — Successful registration confirmation

| Field           | Detail                                       |
| --------------- | -------------------------------------------- |
| `**TCND**`      | `**TCND-07**`                               |
| **Technique**   | Black-box                                   |
| **Precondition**| `**TC-06**` executed in the same flow       |

| #   | Step                                          | Expected Result                                                             |
| --- | --------------------------------------------- | --------------------------------------------------------------------------- |
| 1   | Validate the resulting screen after submission| System displays `"Your registration completed"`. No automatic redirection   |

---

### `**TC-08**` — Blocked with invalid credentials

| Field           | Detail            |
| --------------- | -----------------|
| `**TCND**`      | `**TCND-08**`    |
| **Technique**   | Error Guessing   |
| **Precondition**| User on `/login` |

| #   | Step                                      | `**TD**`                  | Expected Result                                         |
| --- | ------------------------------------------| ------------------------- | ------------------------------------------------------- |
| 1   | Enter unregistered email and password     | `**TD-11**`, `**TD-12**`  | System accepts the input                                |
| 2   | Click on `Log in`                         | —                         | System blocks access and displays `"Login was unsuccessful"` |

---

### `**TC-11**` — Successful login with valid credentials

| Field           | Detail                                                     |
| --------------- | ---------------------------------------------------------- |
| `**TCND**`      | `**TCND-10**`                                             |
| **Technique**   | Black-box                                                 |
| **Precondition**| User on `/login`. `**TD-09**` account pre-created          |

| #   | Step                                     | `**TD**`                  | Expected Result                                   |
| --- | ---------------------------------------- | ------------------------- | ------------------------------------------------- |
| 1   | Enter registered email and password      | `**TD-09**`, `**TD-10**`  | System accepts the input                          |
| 2   | Click on `Log in`                        | —                         | System authenticates user and displays `**TD-21**` in the header |

---

## Module: Checkout E2E

### `**TC-09**` — Complete purchase flow

| Field           | Detail                                                  |
| --------------- | ------------------------------------------------------ |
| `**TCND**`      | `**TCND-09**`                                         |
| **Technique**   | State Transition                                      |
| **Precondition**| Authenticated user. Cart with at least 1 product      |

| #   | Step                                                              | `**TD**`                   | Expected Result                                                                     |
| --- | ----------------------------------------------------------------- | -------------------------- | ----------------------------------------------------------------------------------- |
| 1   | Navigate to `/cart`. Activate terms checkbox. Click on `Checkout` | —                          | System starts the transactional flow                                                |
| 2   | Complete shipping address                                         | `**TD-14**` to `**TD-18**` | System accepts the data without errors                                              |
| 3   | Select payment and shipping method                                | —                          | System allows to continue to the next step                                          |
| 4   | Click on `Confirm`                                                | —                          | System displays `"Your order has been successfully processed!"` with the order ID   |

---

## Traceability

| **`TCND`**    | **`TC`**                 | Technique              | **`RISK`**    |
| :---          | :---                     | :---                   | :---          |
| **`TCND-01`** | **`TC-01`**              | EP                     | **`RISK-01`** |
| **`TCND-02`** | **`TC-02`**              | Error Guessing         | **`RISK-01`** |
| **`TCND-03`** | **`TC-03`**              | EP                     | —             |
| **`TCND-04`** | **`TC-04`**              | Checklist-Based        | —             |
| **`TCND-05`** | **`TC-05`**, **`TC-10`** | BVA                    | **`RISK-03`** |
| **`TCND-06`** | **`TC-06`**              | EP                     | —             |
| **`TCND-07`** | **`TC-07`**              | State Transition       | —             |
| **`TCND-08`** | **`TC-08`**              | Error Guessing         | **`RISK-02`** |
| **`TCND-09`** | **`TC-09`**              | State Transition       | **`RISK-04`** |
| **`TCND-10`** | **`TC-11`**              | EP                     | **`RISK-02`** |
