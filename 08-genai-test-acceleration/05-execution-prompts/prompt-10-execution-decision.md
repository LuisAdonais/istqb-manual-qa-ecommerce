
# prompt-10 — Execution Decision Note

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `08-genai-test-acceleration/05-execution-prompts/prompt-10-execution-decision.md` |
| **Project**    | Tricentis Demo Web Shop |
| **Version**    | 1.0 |
| **STLC Phase** | Test Execution |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference**  | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Artifact Description

An **Execution Decision Note** (**`EDN`**) documents a formal deviation from the entry criteria of a test suite. According to ISTQB CTFL v4.0, test control means taking actions when test objectives are not met as planned — this includes recording decisions to continue despite unmet entry criteria.

**Role in the STLC:** Prevents unnecessary blocking of the test cycle due to low-severity defects. Makes the continuation decision clear and traceable.

**Input sources:** Entry criteria from `test-suites.md`, partial results from the previous suite, QA Lead decision.

---

## Prompt

> [!IMPORTANT]
> 🔗 **Requires:** Active `system-prompt.md` and `context-rules.md`. Input: Completed `prompt-09-test-suites.md`.

### Instruction

Create the **`EDN-XX`** artifact only when the tester confirms that an entry criterion is not met and decides to continue:

1. Record the unmet entry criterion with a reference to `test-suites.md`.
2. Document the open defects (with severity) that led to the deviation.
3. Register the justification and the QA Lead's decision.
4. Do not generate this artifact if all entry criteria are met.

### Input data

```text
Affected suite       : [TS-XX]
Unmet entry criterion: [description from test-suites.md]
Open defects         : [BUG-XX — severity — module]
Justification        : [reason to continue]
Decision             : [continue / pause / adjust scope]
Authorized by        : [QA Owner]
```

### Constraints

- IDs: **`EDN-01`**, **`EDN-02`**, etc.
- Only produce if deviation is confirmed by the tester.
- Mandatory reference to the entry criterion in `test-suites.md`.

### Output format

```markdown
# Execution Decision Note — **`EDN-XX`**

| Attribute         | Detail |
| :---              | :--- |
| **Location**      | `05-test-execution/EDN-XX_Execution-Decision-Note.md` |
| **Affected suite**| **`TS-XX`** |
| **Date**          | [YYYY-MM-DD] |
| **QA Owner**      | [name] |

## Situation

**Unmet entry criterion:** [description]  
**Reference:** `test-suites.md` — **`TS-XX`**

## Open Defects

| **`BUG`**   | Severity    | Module   |
| :---        | :---        | :---     |
| **`BUG-XX`**| [severity]  | [module] |

## Decision

**Justification:** [reason]  
**Decision:** [continue / pause / adjust]  
**Authorized by:** [QA Owner name]
```

## Traceability

| This prompt                        | Feeds Into                    |
| :---                               | :---                         |
| `prompt-10-execution-decision.md`  | `prompt-11-execution-tracker.md` |

---