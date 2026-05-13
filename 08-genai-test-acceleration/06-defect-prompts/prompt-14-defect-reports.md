
# prompt-14 — Defect Reports (consolidated)

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `08-genai-test-acceleration/06-defect-prompts/prompt-14-defect-reports.md` |
| **Project**    | Tricentis Demo Web Shop |
| **Version**    | 1.0 |
| **STLC Phase** | Defect Management |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference**  | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Artifact Description

The **Defect Reports** artifact consolidates all defects found during execution in a traceable summary table. According to ISTQB CTFL v4.0, a defect report is a *test execution work product* that provides enough information to resolve the defect, track product quality, and improve the process.

**Role in the STLC:** Provides a consolidated view of all **`BUG`**s in the cycle. Each row points to the individual defect report.

**Data sources:** Test logs (**`TL`**) with **`TX`** in FAIL status and references to **`BUG`**s.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-12-test-logs.md`.

### Instruction

Build the consolidated defect table collaboratively with the tester:

1. For every **`TX`** with FAIL status, request defect details from the tester.
2. Register each **`BUG`** referencing the affected **`TX`**, **`TC`**, and **`REQ`**.
3. Validate severity and priority with the tester before closing each entry.

### Input data

```text
For each BUG, the tester provides:
  Origin TX        : [TX-XX.XX]
  Failed TC        : [TC-XX]
  Affected REQ     : [REQ-XX]
  Title            : [brief description of the defect]
  Severity         : [Critical / High / Medium / Low]
  Priority         : [High / Medium / Low]
  Status           : [Open]
```

### Constraints

- IDs: **`BUG-01`**, **`BUG-02`**, etc.
- Each **`BUG`** must reference **`TX`**, **`TC`**, and **`REQ`**.
- Do not close defects without tester confirmation.

### Output format

```markdown
# Defect Reports

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `06-defect-management/defect-reports.md` |
| **Project**    | [name] |
| **Version**    | [x.x] |
| **STLC Phase** | Defect Management |
| **Status**     | In Progress |
| **QA Owner**   | [name] |

## Defect Summary

| **`BUG`** | Title | Severity | Priority | **`TX`** | **`TC`** | **`REQ`** | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **`BUG-01`** | [title] | [severity] | [priority] | **`TX-XX.XX`** | **`TC-XX`** | **`REQ-XX`** | Open |
```

## Traceability

| This prompt                          | Feeds                       |
| :---                                 | :---                        |
| `prompt-14-defect-reports.md`        | `prompt-15-individual-bugs.md` |

---