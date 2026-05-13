
# prompt-17 — Test Summary Report

| Attribute      | Detail                                                                         |
| :---           | :---                                                                           |
| **Location**   | `08-genai-test-acceleration/07-completion-prompts/prompt-17-summary-report.md` |
| **Project**    | Tricentis Demo Web Shop                                                        |
| **Version**    | 1.0                                                                            |
| **STLC Phase** | Test Completion                                                                |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL                      |
| **Reference**       | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.4                          |

## Artifact Description

The **Test Summary Report** is the final document for closing the test cycle. According to ISTQB CTFL v4.0, it is a *test completion work product* that consolidates: summary of activities, plan deviations, metrics, exit criteria evaluation, residual risks, and artifact traceability. It is communicated to stakeholders.

**Role in the STLC:** Formal closure of the cycle. Summarizes the product's quality status for the release decision.

**Data sources:** All cycle artifacts — especially `test-execution-summary.md`, `defect-reports.md`, and `lessons-learned.md`.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-16-lessons-learned.md`.

### Instruction

Build `test-summary-report.md` collaboratively with the tester:

1. Consolidate data from all phases of the cycle.
2. Evaluate exit criteria against actual results.
3. Document residual risks with action plans.
4. Present to the tester for validation section by section.
5. Maximum 2 sections per exchange.

Do not assume release decision without explicit tester confirmation.

### Input data

```text
Cycle period        : [start date — end date]
Total TX           : [number]
PASS / FAIL        : [number / number]
Open defects       : [BUG-XX — severity — plan]
Exit criteria      : [reference to test-plan.md + actual result]
Deviations (EDN)   : [EDN-XX or none]
Release decision   : [Approved / Conditional / Rejected]
```

### Constraints

- Exit criteria evaluation must show threshold vs. actual result.
- Only document residual risks from open **`BUG`**s — do not invent risks.
- Artifact traceability covers all STLC phases.
- Final status: `Completed` only with tester confirmation.

### Output format

```markdown
# Test Summary Report

| Attribute      | Detail                                                            |
| :---           | :---                                                              |
| **Location**   | `07-test-completion/test-summary-report.md`                       |
| **Project**    | [name]                                                            |
| **Version**    | [x.x]                                                             |
| **STLC Phase** | Test Completion                                                   |
| **Period**     | [start date] — [end date]                                         |
| **Status**     | Completed                                                         |
| **QA Owner**   | [name]                                                            |

## 1. Executive Summary

[short paragraph — what was tested, what was found, decision]

## 2. Executed Scope

[modules tested with reference to REQ]

## 3. Execution Metrics

| Indicator                      | Value   |
| :---                           | :---    |
| Total **`TX`** executed        | [n]     |
| PASS                           | [n]     |
| FAIL                           | [n]     |
| Global Pass Rate               | [%]     |
| Defects detected               | [n]     |

## 4. Exit Criteria Evaluation

| Criteria           | Threshold | Actual    | Status      |
| :---               | :---      | :---      | :---        |
| [criteria]         | [thres.]  | [actual]  | ✅ / ❌      |

## 5. Plan Deviations

| **`EDN`**  | Affected Suite  | Decision     |
| :---       | :---            | :---         |
| **`EDN-XX`** | **`TS-XX`**   | [decision]   |

## 6. Open Defects at Closure

| **`BUG`**    | Severity   | Module     | Plan         |
| :---         | :---       | :---       | :---         |
| **`BUG-XX`** | [severity] | [module]   | [plan]       |

## 7. Residual Risks

| **`BUG`**    | Module     | Business Risk      | Plan         |
| :---         | :---       | :---               | :---         |
| **`BUG-XX`** | [module]   | [description]      | [plan]       |

## 8. Artifact Traceability

| Phase               | Artifacts                                                           | Status           |
| :---                | :---                                                                | :---             |
| Test Analysis       | `requirements.md`, `test-basis-evaluation.md`, `test-conditions.md` | ✅ Approved   |
| Test Design         | `test-cases.md`, `test-data-requirements.md`                        | ✅ Approved   |
| Test Implementation | `test-procedures.md`, `test-suites.md`, `test-environment-setup.md` | ✅ Approved   |
| Test Execution      | `TL-01`, `TL-02`, `TL-03`, `test-execution-tracker.md`              | ✅ Completed  |
| Defect Management   | [BUG-XX]                                                            | 🔴 Open       |
| Test Completion     | `test-summary-report.md`, `lessons-learned.md`                      | ✅ Completed  |
```

## Traceability

| This prompt                    | Closes chain                                    |
| :---                           | :---                                            |
| `prompt-17-summary-report.md`  | End of cycle — Zero Orphans verified            |