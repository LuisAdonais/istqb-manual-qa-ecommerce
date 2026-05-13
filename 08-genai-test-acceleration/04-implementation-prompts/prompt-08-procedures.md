
# prompt-08 — Test Procedures

| Attribute      | Detail                                                                   |
| :---           | :---                                                                     |
| **Location**   | `08-genai-test-acceleration/04-implementation-prompts/prompt-08-procedures.md` |
| **Project**    | Tricentis Demo Web Shop                                                  |
| **Version**    | 1.0                                                                      |
| **STLC Phase** | Test Implementation                                                      |
| **GenAI Technique** | Prompt chaining · Meta-prompting · Iterative HITL                  |
| **Reference**      | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2                                   |

## Artifact Description

A **Test Procedure** (**`TP`**) is an ordered sequence of steps for executing a group of related test cases. According to ISTQB CTFL v4.0, it is a *test implementation work product* that organizes the **`TC`** for efficient execution within a test suite.

**Role in the STLC:** Arranges the **`TC`** in an executable flow with explicit dependencies. Each step has exactly one binary expected result.

**Input sources:** Approved `test-cases.md` and `test-data-requirements.md`.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-06-test-data.md`.

### Instruction

Build the test procedures collaboratively with the tester:

1. Group related **`TC`** into logical procedures.
2. For each **`TP`**, define precondition, ordered steps referencing **`TD`** as needed, and one expected result per step.
3. Confirm with the tester that each expected result is binary (Pass/Fail).
4. Maximum 1 **`TP`** per exchange — validate before continuing.

One step = one action. If the expected result contains "or", split into two separate steps.

### Input data

```text
TC to group        : [list of TC-XX with their TCND]
Available TD       : [list of TD-XX]
For each TP, the tester confirms:
  TC included      : [TC-XX, TC-XX]
  Precondition     : [system state]
  Step order       : [logical sequence]
```

### Constraints

- Use imperative voice in all steps.
- IDs: **`TP-01`**, **`TP-02`**, etc.
- Each **`TP`** references its **`TC`**.
- No "or" connectors in expected results.

### Output format

```markdown
## **`TP-01`** — [descriptive name]

| Attribute             | Detail                  |
| :---                  | :---                    |
| **Covered TC**        | **`TC-XX`**, **`TC-XX`**|
| **Precondition**      | [initial state]         |

| Step | Action                | **`TD`**    | Expected Result         |
| :--- | :---                  | :---        | :---                   |
| 1    | [imperative action]   | **`TD-XX`** | [binary expected result] |
| N    | [imperative action]   | —           | [binary expected result] |
```

## Traceability

| This prompt                  | Feeds into                  |
| :---                         | :---                        |
| `prompt-08-procedures.md`    | `prompt-09-test-suites.md`  |

---