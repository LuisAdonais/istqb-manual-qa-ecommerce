
# prompt-12 — Test Logs

| Attribute      | Detail                                                                |
| :---           | :---                                                                  |
| **Location**   | `08-genai-test-acceleration/05-execution-prompts/prompt-12-test-logs.md` |
| **Project**    | Tricentis Demo Web Shop                                               |
| **Version**    | 1.0                                                                   |
| **STLC Phase** | Test Execution                                                        |
| **GenAI Technique** | Structured prompt · Iterative HITL                               |
| **Reference**       | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4                               |

## Artifact Description

A **Test Log** (**`TL`**) is the chronological record of all events that occurred during a test execution session. According to ISTQB CTFL v4.0, it is a *test execution work product* that documents what happened during the session, including actual results and evidence.

**Role in the STLC:** Provides detailed execution traceability by suite. It is the source of evidence for the Test Summary Report.

**Data sources:** Results from the execution tracker and evidence captured according to the convention in `test-environment-setup.md`.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Updated `prompt-11-execution-tracker.md`.

### Instruction

Generate one **`TL`** per suite collaboratively with the tester:

1. For each executed **`TX`**, record: action, actual result, referenced evidence, and status.
2. If the actual result differs from the expected result, mark `FAIL` and request the tester to provide the referenced **`BUG`** ID.
3. Log one suite per **`TL`** — do not mix **`TX`** from different suites in the same **`TL`**.

### Input data

```text
Suite to log         : [TS-XX]
For each TX the tester provides:
  TX ID              : [TX-XX.XX]
  Actual result      : [observable description]
  Evidence           : [file name according to convention]
  Status             : [PASS / FAIL]
  BUG                : [BUG-XX or —]
```

### Constraints

- IDs: **`TL-01`**, **`TL-02`**, **`TL-03`** (one per suite).
- Evidence file name must follow the convention from `test-environment-setup.md`.
- Do not register environment setup steps as **`TX`**.

### Output format

```markdown
# Test Log — **`TL-XX`** — [suite name]

| Attribute   | Detail                                             |
| :---        | :---                                               |
| **Location**    | `05-test-execution/test-logs/TL-XX-[suite]-log.md` |
| **Suite**       | **`TS-XX`**                                   |
| **Date**        | [YYYY-MM-DD]                                  |
| **QA Owner**    | [name]                                        |

| **`TX`**     | **`TC`**     | Actual Result       | Evidence           | Status       | **`BUG`**       |
| :---         | :---         | :---               | :---               | :---         | :---            |
| **`TX-XX.XX`** | **`TC-XX`** | [description]      | `[file.png]`       | PASS / FAIL  | — / **`BUG-XX`** |
```

## Traceability

| This prompt                 | Feeds into                       |
| :---                        | :---                             |
| `prompt-12-test-logs.md`    | `prompt-13-execution-summary.md` |

---