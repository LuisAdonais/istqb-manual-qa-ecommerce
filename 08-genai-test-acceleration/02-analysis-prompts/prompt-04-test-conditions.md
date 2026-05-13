
# prompt-04 — Test Conditions

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/02-analysis-prompts/prompt-04-test-conditions.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Analysis |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Artifact Description

**Test Conditions** are atomic statements derived from approved **`AC`** that answer the question, "what should be verified?". According to ISTQB CTFL v4.0, a test condition is an aspect of the test object that can be verified by one or more test cases.

**Role in the STLC:** Bridge between analysis and design. Each **`TCND`** will originate one or more **`TC`**.

**Inputs:** Approved `requirements.md` and `test-basis-evaluation.md` artifacts.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-03-basis-evaluation.md`.

### Instruction

Derive test conditions from the `requirements.md` artifact in collaboration with the tester:

1. For each approved **`AC`**, generate the corresponding atomic test condition.
2. Assign priority based on risks from the Test Plan.
3. Present the set to the tester for validation before proceeding with the next group of **`AC`**.
4. Limit 5 conditions per iteration.

One condition = one verifiable aspect. Do not combine multiple checks into a single **`TCND`**.

### Input data

```text
Approved AC         : [list of AC from requirements.md]
Test Plan Risks     : [RISK-XX → affected module]
For each TCND the tester confirms:
  Condition         : [verifiable statement — "Validate that..."]
  Priority          : [High / Medium / Critical]
  Associated RISK   : [RISK-XX or —]
```

### Constraints

- Write in the format: "Validate that [observable behavior]."
- Sequential IDs: **`TCND-01`**, **`TCND-02`**…
- Each **`TCND`** must reference a single **`AC`**.
- Do not include test steps — those will be covered in **`TC`**.

### Output format

```markdown
# Test Conditions

| Attribute | Detail |
| :--- | :--- |
| **Location** | `02-test-analysis/test-conditions.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Analysis |
| **Status** | Draft |
| **QA Owner** | [name] |

## 1. Test Conditions (`TCND`)

| ID | **`AC`** | Test Condition | Priority | **`RISK`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TCND-01`** | **`AC-01`** | Validate that [behavior]. | High | **`RISK-XX`** |

## 2. Traceability

| **`REQ`** | **`AC`** | **`TCND`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-XX`** | **`AC-XX`** | **`TCND-XX`** | **`RISK-XX`** |
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-04-test-conditions.md` | `prompt-05-test-cases.md` |

---