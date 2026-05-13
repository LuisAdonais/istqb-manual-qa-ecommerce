
# prompt-13 — Execution Summary

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `08-genai-test-acceleration/05-execution-prompts/prompt-13-execution-summary.md` |
| **Project**    | Tricentis Demo Web Shop |
| **Version**    | 1.0 |
| **STLC Phase** | Test Execution |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference**  | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Artifact Description

The **Test Execution Summary** consolidates the results of all executed suites. According to ISTQB CTFL v4.0, test monitoring produces *test progress reports* that compare actual progress against the plan.

**Role in the STLC:** Closes the execution phase with consolidated metrics. Feeds the Test Summary Report of the completion phase.

**Data sources:** The three completed **`TL`** and the updated execution tracker.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-12-test-logs.md` for all three suites.

### Instruction

Consolidate the execution results collaboratively with the tester:

1. Calculate metrics per suite: total **`TX`**, PASS, FAIL, PENDING, pass rate.
2. List open defects with severity.
3. Evaluate if the exit criteria from the Test Plan were met.
4. Present the summary to the tester for validation before closing.

### Input data

```text
Completed TL: [TL-01, TL-02, TL-03]
For each suite:
  Total TX: [number]
  PASS: [number]
  FAIL: [number]
  PENDING: [number]
Open BUGs: [BUG-XX — severity]
Plan exit criteria: [reference to test-plan.md]
```

### Constraints

- Pass rate = (PASS / Total TX) × 100.
- Evaluate exit criteria against the thresholds from the Test Plan — do not assume fulfillment.
- Header with Status `Completed` only if confirmed by the tester.

### Output format

```markdown
# Test Execution Summary

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `05-test-execution/test-execution-summary.md` |
| **Project**    | [name] |
| **Version**    | [x.x] |
| **STLC Phase** | Test Execution |
| **Status**     | Completed |
| **QA Owner**   | [name] |

## Results per suite

| **`TS`** | Total **`TX`** | PASS | FAIL | PENDING | Pass Rate |
| :---     | :---           | :--- | :--- | :---    | :---      |
| **`TS-01`** | [n]         | [n]  | [n]  | [n]     | [%]       |

## Detected defects

| **`BUG`** | Severity   | Module    | Status |
| :---      | :---      | :---      | :---   |
| **`BUG-XX`** | [severity] | [module] | Open   |

## Exit criteria evaluation

| Criterion         | Threshold | Actual Result | Status |
| :---              | :---      | :---         | :---   |
| [plan criterion]  | [threshold] | [actual value] | ✅ / ❌ |
```

## Traceability

| This prompt                      | Feeds                                   |
| :---                             | :---                                    |
| `prompt-13-execution-summary.md`  | `prompt-16-lessons-learned.md` · `prompt-17-summary-report.md` |

---