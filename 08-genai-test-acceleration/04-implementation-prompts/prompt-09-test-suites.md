
# prompt-09 — Test Suites

| Attribute        | Detail |
| :---             | :--- |
| **Location**     | `08-genai-test-acceleration/04-implementation-prompts/prompt-09-test-suites.md` |
| **Project**      | Tricentis Demo Web Shop |
| **Version**      | 1.0 |
| **STLC Phase**   | Test Implementation |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference**    | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Artifact Description

A **Test Suite** (**`TS`**) is a set of grouped test procedures designed to be executed together in a single session. As defined in ISTQB CTFL v4.0, it is a *test implementation work product*. Grouping by suite allows test execution to be prioritized by criticality: Smoke, Regression, then E2E.

**Function in the STLC:** Specifies execution sequence and entry/exit criteria for each suite, enabling the execution stage.

**Input sources:** Approved `test-procedures.md` and the prioritization strategy from the Test Plan.

---

## Prompt

> [!TIP]
> 🔗 **Requires:** Active `system-prompt.md` and `context-rules.md`. Input: Completed `prompt-08-procedures.md`.

### Instruction

Work with the tester to organize the test procedures into suites:

1. Assign each **`TP`** to a suite according to execution priority: **`TS-01`** (Smoke), **`TS-02`** (Regression), **`TS-03`** (E2E).
2. Define entry criteria for **`TS-02`** and **`TS-03`** using the outcome and defect severity from the preceding suite.
3. Confirm that no **`TP`** is included in more than one suite without explicit tester agreement.

### Input data

```text
Available TP       : [list of TP-XX and their covered TC]
Strategy           : [Smoke → Regression → E2E]
For each TS the tester confirms:
  Included TP      : [TP-XX, TP-XX]
  Entry Criteria   : [condition to start this suite]
  Exit Criteria    : [condition to finish this suite]
```

### Constraints

- Use suite IDs: **`TS-01`**, **`TS-02`**, **`TS-03`**.
- Base entry criteria on the severity of detected defects, not only the percentage of passing tests.
- Each **`TS`** must cite all included **`TP`**.

### Output format

```markdown
# Test Suites

| Attribute       | Detail |
| :---            | :--- |
| **Location**    | `04-test-implementation/test-suites.md` |
| **Project**     | [name] |
| **Version**     | [x.x] |
| **STLC Phase**  | Test Implementation |
| **State**       | Draft |
| **QA Owner**    | [name] |

## **`TS-01`** — Smoke Suite

| **`TP`** Included | **`TC`** Covered | Priority |
| :---              | :---             | :--- |
| **`TP-XX`**       | **`TC-XX`**      | High |

**Entry Criteria:** [condition]  
**Exit Criteria:** [severity-based condition]

## **`TS-02`** — Regression Suite

| **`TP`** Included | **`TC`** Covered | Priority |
| :---              | :---             | :--- |
| **`TP-XX`**       | **`TC-XX`**      | Medium |

**Entry Criteria:** [condition linked to previous suite and severity]  
**Exit Criteria:** [severity-based completion condition]

## **`TS-03`** — E2E Suite

| **`TP`** Included | **`TC`** Covered | Priority |
| :---              | :---             | :--- |
| **`TP-XX`**       | **`TC-XX`**      | Medium/Low |

**Entry Criteria:** [condition linked to results/severity of Regression]  
**Exit Criteria:** [severity-based completion condition]

## Traceability

| **`TS`** | **`TP`** | **`TC`** | **`TCND`** |
| :---     | :---     | :---     | :--- |
| **`TS-XX`** | **`TP-XX`** | **`TC-XX`** | **`TCND-XX`** |
```

## Traceability

| This prompt                   | Feeds                    |
| :---                          | :---                     |
| `prompt-09-test-suites.md`    | `prompt-10-execution-decision.md` |