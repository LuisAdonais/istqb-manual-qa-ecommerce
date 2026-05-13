
# Test Environment Setup

| Attribute | Detail |
| :--- | :--- |
| **Location** | `04-test-implementation/test-environment-setup.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.9 |
| **STLC Phase** | Test Implementation |
| **Status** | ✅ Approved |
| **QA Owner** | Luis Adonais Malave Gamardo |

---

## 1. Infrastructure

| Component | Specification |
| :--- | :--- |
| **Operating System** | Windows 10 Pro |
| **Browser** | Firefox 150.0.1 (64-bit) |
| **Browser State** | Cache and cookies cleared before each **`TS`** |
| **Connectivity** | Standard internet — no VPN or proxy |
| **Base URL** | `https://demowebshop.tricentis.com/` |

---

## 2. Tools

| Tool | Purpose |
| :--- | :--- |
| **VS Code** | Writing artifacts in Markdown |
| **GitHub** | Version control and QA portfolio |
| **ShareX** | Capture execution evidence |
| **Jira** | Defect logging and tracking — with evidence in `05-test-execution/jira-evidence/` |

**Evidence naming convention:**

```text
YYYY-MM-DD_TX-XX.XX_Short_Description_STATUS.png
```

Example: `2026-05-04_TX-01.01_Register_Submit_PASS.png`

---

## 3. Data Preparation

> These are environment configuration steps; they do not constitute a formal **`TX`** cycle.

1. Navigate to `https://demowebshop.tricentis.com/register`
2. Register an account with **`TD-09`** and **`TD-10`**
3. Validate that the message `"Your registration completed"` appears
4. Log out before starting the suite

---

## 4. Repository Structure

```text
istqb-manual-qa-ecommerce/
|-- 00-context-and-overview/
|   |-- 00-README.md
|   `-- system-under-test.md
|-- 01-test-planning/
|   `-- test-plan.md
|-- 02-test-analysis/
|   |-- 02-README.md
|   |-- requirements.md
|   |-- test-basis-evaluation.md
|   `-- test-conditions.md
|-- 03-test-design/
|   |-- 03-README.md
|   |-- test-cases.md
|   `-- test-data-requirements.md
|-- 04-test-implementation/
|   |-- 04-README.md
|   |-- test-environment-setup.md
|   |-- test-procedures.md
|   `-- test-suites.md
|-- 05-test-execution/
|   |-- 05-README.md
|   |-- decisions/
|   |   `-- edn-01-execution-decision-note.md
|   |-- test-evidence/
|   |   |-- jira-evidence/
|   |   |   |-- 2026-05-05_BUG-01_Jira-Issue.png
|   |   |   |-- 2026-05-05_BUG-02_Jira-Issue.png
|   |   |   `-- 2026-05-05_BUG-03_Jira-Issue.png
|   |   |-- ts-01-smoke-suite/
|   |   |   |-- 2026-05-04_TX-01.01_Register_Submit_PASS.png
|   |   |   |-- 2026-05-04_TX-01.02_Register_Success_PASS.png
|   |   |   |-- 2026-05-04_TX-01.03_Login_Fail_PASS.png
|   |   |   |-- 2026-05-04_TX-01.04_Login_Success_PASS.png
|   |   |   |-- 2026-05-05_TX-01.05_Search_Discrepancy_BUG-01.png
|   |   |   |-- 2026-05-05_TX-01.06_Search_Empty_PASS.png
|   |   |   |-- 2026-05-05_TX-01.07_Category_Nav_BUG-02.png
|   |   |   `-- 2026-05-05_TX-01.08_MissingSKU_FAIL_BUG-03.png
|   |   |-- ts-02-regression-suite/
|   |   |   |-- 2026-05-05_TX-02.01_Cart_Recalculate_PASS.png
|   |   |   |-- 2026-05-05_TX-02.02_Cart_Zero_Limit_PASS.png
|   |   |   `-- 2026-05-05_TX-02.03_Cart_Remove_Item_PASS.png
|   |   `-- ts-03-e2e-suite/
|   |       `-- 2026-05-05_TX-03.01_Checkout_Success_PASS.png
|   |-- test-execution-summary.md
|   |-- test-execution-tracker.md
|   `-- test-logs/
|       |-- tl-01-smoke-log.md
|       |-- tl-02-regression-log.md
|       `-- tl-03-e2e-log.md
|-- 06-defect-management/
|   |-- bug-01-price-incoherence.md
|   |-- bug-02-capitalization-inconsistency.md
|   |-- bug-03-missing-sku-field.md
|   `-- defect-reports.md
|-- 07-test-completion/
|   |-- lessons-learned.md
|   `-- test-summary-report.md
|-- 08-genai-test-acceleration/
|   |-- 00-core-config/
|   |   |-- context-rules.md
|   |   |-- prompt-format-std.md
|   |   `-- system-prompt.md
|   |-- 01-planning-prompts/
|   |   |-- prompt-00-sut.md
|   |   `-- prompt-01-test-plan.md
|   |-- 02-analysis-prompts/
|   |   |-- prompt-02-requirements.md
|   |   |-- prompt-03-basis-evaluation.md
|   |   `-- prompt-04-test-conditions.md
|   |-- 03-design-prompts/
|   |   |-- prompt-05-test-cases.md
|   |   `-- prompt-06-test-data.md
|   |-- 04-implementation-prompts/
|   |   |-- prompt-07-environment.md
|   |   |-- prompt-08-procedures.md
|   |   `-- prompt-09-test-suites.md
|   |-- 05-execution-prompts/
|   |   |-- prompt-10-execution-decision.md
|   |   |-- prompt-11-execution-tracker.md
|   |   |-- prompt-12-test-logs.md
|   |   `-- prompt-13-execution-summary.md
|   |-- 06-defect-prompts/
|   |   |-- prompt-14-defect-reports.md
|   |   `-- prompt-15-individual-bugs.md
|   |-- 07-completion-prompts/
|   |   |-- prompt-16-lessons-learned.md
|   |   `-- prompt-17-summary-report.md
|   `-- README.md
|-- LICENSE
`-- README.md
```

## 5. Traceability

| Environment Requirement | Dependent **`TS`** | Status |
| :--- | :--- | :--- |
| Cache and cookies cleared | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| Standard internet connection | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| ShareX active | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
| **`TD-09`** account pre-created | **`TS-02`**, **`TS-03`** | ✅ Ready |
| Jira configured | **`TS-01`**, **`TS-02`**, **`TS-03`** | ✅ Ready |
