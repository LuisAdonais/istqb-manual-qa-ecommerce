
# prompt-11 — Execution Tracker

| Attribute  | Detail |
| :---       | :--- |
| **Location** | `08-genai-test-acceleration/05-execution-prompts/prompt-11-execution-tracker.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Execution |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Artifact Description

The **Test Execution Tracker** records the status of each execution cycle (**`TX`**). According to ISTQB CTFL v4.0, test monitoring means the ongoing check of all test activities and comparison of actual progress against the plan.

**Role in the STLC:** Execution control panel. Enables immediate identification of which **`TX`** passed, failed, or are pending, and which **`BUG`** were raised.

**Data sources:** Approved `test-suites.md` — list of planned **`TX`**. The tester updates the status and **`BUG`** references after each execution.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-09-test-suites.md`.

### Instruction

Build the tracker collaboratively with the tester:

1. Generate the table of planned **`TX`** from the **`TP`** of each **`TS`**.
2. Initial status of all **`TX`**: `PENDING`.
3. The tester updates the status (**`PASS`** / **`FAIL`** / **`PENDING`**) and references to **`BUG`** after each execution session.
4. Update the tracker with each exchange without overwriting already closed rows.

### Input data

```text
Planned TS and TP: [list of TS-XX → TP-XX → TC-XX]
For each TX, after execution the tester provides:
  Execution ID         : TX-XX.XX (suite.sequence)
  Test case executed   : [TC-XX]
  Execution date       : [YYYY-MM-DD]
  Status               : [PASS / FAIL]
  Referenced BUG       : [BUG-XX or —]
```

### Constraints

- IDs: **`TX-01.01`**, **`TX-01.02`**… per suite.
- Initial status is always `PENDING`.
- Each **`TX`** with `FAIL` status must reference a **`BUG`**.

### Output format

```markdown
# Test Execution Tracker

| Attribute  | Detail |
| :---       | :--- |
| **Location** | `05-test-execution/test-execution-tracker.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Execution |
| **Status** | In progress |
| **QA Owner** | [name] |

## **`TS-01`** — Smoke Suite

| **`TX`**      | **`TC`**     | Date      | Status   | **`BUG`** |
| :---          | :---         | :---      | :---     | :---      |
| **`TX-01.01`**| **`TC-XX`**  | [date]    | PENDING  | —         |
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-11-execution-tracker.md` | `prompt-12-test-logs.md` · `prompt-14-defect-reports.md` |

---