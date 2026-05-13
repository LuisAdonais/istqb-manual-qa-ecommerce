
# Test Procedures

| Attribute    | Detail                                             |
| :---         | :---                                              |
| **Location** | `04-test-implementation/test-procedures.md`        |
| **Project**  | Tricentis Demo Web Shop                            |
| **Version**  | 1.7                                               |
| **STLC Phase** | Test Implementation                             |
| **Status**     | ✅ Approved                                     |
| **QA Owner**   | Luis Adonais Malave Gamardo                     |

---

## **`TP-01`** — Account Management

**Test cases:** **`TC-06`**, **`TC-07`**, **`TC-08`**, **`TC-11`** | **Suite:** **`TS-01`**, **`TS-02`**

| # | Action                                                         | **`TD`**                     | Expected Result                                                                                 |
|:-:|:---------------------------------------------------------------|:-----------------------------|:------------------------------------------------------------------------------------------------|
| 1 | Navigate to `/register`                                        | —                            | The system displays the registration form                                                       |
| 2 | Select gender. Enter first and last name                       | **`TD-06`**, **`TD-07`**, **`TD-08`** | The system accepts the input                                                                   |
| 3 | Enter email and password. Click on `Register`                  | **`TD-09`**, **`TD-10`**     | The system processes the form with no validation errors (**`TC-06`**)                          |
| 4 | Validate the resulting screen                                  | —                            | The system displays `"Your registration completed"` (**`TC-07`**)                              |
| 5 | Click on `Log out`. Navigate to `/login`                       | —                            | The system logs out the session and displays the login form                                    |
| 6 | Enter unregistered credentials. Click on `Log in`              | **`TD-11`**, **`TD-12`**     | The system displays `"Login was unsuccessful"` (**`TC-08`**)                                   |
| 7 | Enter valid credentials. Click on `Log in`                     | **`TD-09`**, **`TD-10`**     | The system authenticates the user and displays **`TD-21`** in the header (**`TC-11`**)         |

---

## **`TP-02`** — Search and Catalog

**Test cases:** **`TC-01`**, **`TC-02`**, **`TC-03`**, **`TC-04`** | **Suite:** **`TS-01`**, **`TS-02`**

| # | Action                                                                                       | **`TD`**        | Expected Result                                                                       |
|:-:|:---------------------------------------------------------------------------------------------|:----------------|:--------------------------------------------------------------------------------------|
| 1 | Enter a valid term in `Search store`. Click on `Search`                                      | **`TD-01`**     | The system displays results in alphabetical order (**`TC-01`**)                       |
| 2 | Enter an invalid term in `Search store`. Click on `Search`                                   | **`TD-02`**     | The system displays `"No products were found..."` (**`TC-02`**)                       |
| 3 | Navigate to `Computers > Desktops` using the side menu                                       | **`TD-03`**     | The system lists only the products for the selected subcategory (**`TC-03`**)         |
| 4 | Click on the image or title of a product                                                     | —               | The system displays Name, Price, SKU, input `Qty.` and `Add to cart` button (**`TC-04`**) |

---

## **`TP-03`** — Cart and Checkout E2E

**Test cases:** **`TC-05`**, **`TC-09`**, **`TC-10`** | **Suite:** **`TS-02`**, **`TS-03`**

**Precondition:** Active session with **`TD-09`** and **`TD-10`**. At least 1 item in the cart.

> [!NOTE]
> The `Qty.` field does not have increment/decrement controls. Modification is keyboard-only. Entering `0` removes the item from the cart. See **`AN-05`**.

| # | Action                                                                              | **`TD`**              | Expected Result                                                                                                   |
|:-:|:------------------------------------------------------------------------------------|:----------------------|:------------------------------------------------------------------------------------------------------------------|
| 1 | Navigate to `/cart`                                                                 | —                     | The system displays the items and totals                                                                          |
| 2 | Change `Qty.` of item 1 to `2`. Click on `Update shopping cart`                     | **`TD-04`**           | The `Sub-Total` of item 1 updates correctly (**`TC-05`**)                                                         |
| 3 | Change `Qty.` of item 1 to `0`. Click on `Update shopping cart`                     | **`TD-19`**           | If more items: the item is removed and totals recalculate (**`TC-05`**). If only one item: displays `"Your Shopping Cart is empty!"` (**`TC-10`**) |
| 4 | Add an item to the cart. Tick terms checkbox. Click on `Checkout`                   | —                     | The system initiates the transaction flow                                                                         |
| 5 | Complete shipping address and payment method                                        | **`TD-14`** — **`TD-18`** | The system accepts all input and allows continuation                                                           |
| 6 | Click on `Confirm`                                                                  | —                     | The system displays `"Your order has been successfully processed!"` with order ID (**`TC-09`**)                    |

---

## Traceability

| **`TP`**   | Integrated **`TC`**                                   | Consumed **`TD`**                       |
| :---       | :---                                                 | :---                                    |
| **`TP-01`**| **`TC-06`**, **`TC-07`**, **`TC-08`**, **`TC-11`**    | **`TD-06`** — **`TD-12`**, **`TD-21`**  |
| **`TP-02`**| **`TC-01`**, **`TC-02`**, **`TC-03`**, **`TC-04`**    | **`TD-01`**, **`TD-02`**, **`TD-03`**   |
| **`TP-03`**| **`TC-05`**, **`TC-09`**, **`TC-10`**                 | **`TD-04`**, **`TD-13`** — **`TD-19`**  |
