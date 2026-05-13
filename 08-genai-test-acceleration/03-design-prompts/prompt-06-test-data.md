
# prompt-06 — Test Data

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/03-design-prompts/prompt-06-test-data.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Design |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Artifact Description

**Test Data Requirements** specify the data needed to execute the test cases. According to ISTQB CTFL v4.0, these are a *test design work product*. GenAI can generate representative synthetic values that cover valid, invalid, and boundary partitions without exposing sensitive data.

**Role in the STLC:** Provides the concrete values required for **`TP`** and **`TC`** to be executable.

**Data sources:** Approved `test-cases.md` — input fields, applied **`EP`** / **`BVA`** techniques.

---

## Prompt

> [!TIP]
> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-05-test-cases.md`.

### Instruction

Specify test data collaboratively with the tester:

1. For each **`TC`** requiring input data, identify the necessary fields.
2. Propose values for valid, invalid, and boundary partitions according to the applied technique.
3. Present to the tester for validation — with special focus on boundary and negative values.
4. Maximum 5 **`TD`** per exchange.

Do not use real personal data. Use synthetic data that represents real SUT behavior.

### Input data

```text
TC with data input: [list of TC-XX with identified fields]
For each TD the tester confirms:
  Field            : [field name in the SUT]
  Value            : [concrete data]
  Type             : [valid / invalid / boundary]
  Used in TC       : [TC-XX]
```

### Constraints

- Sequential IDs: **`TD-01`**, **`TD-02`**…
- Each **`TD`** references the **`TC`** that consumes it.
- Do not use real emails, names, or passwords.
- Boundary values must explicitly identify the partition they cover.

### Output format

```markdown
# Test Data Requirements

| Attribute | Detail |
| :--- | :--- |
| **Location** | `03-test-design/test-data-requirements.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Design |
| **Status** | Draft |
| **QA Owner** | [name] |

## Test Data (`TD`)

| ID | Field | Value | Type | **`TC`** |
| :--- | :--- | :--- | :--- | :--- |
| **`TD-01`** | [field] | [value] | Valid / Invalid / Boundary | **`TC-XX`** |

## Traceability

| **`TD`** | **`TC`** | **`TCND`** |
| :--- | :--- | :--- |
| **`TD-XX`** | **`TC-XX`** | **`TCND-XX`** |
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-06-test-data.md` | `prompt-07-environment.md` · `prompt-08-procedures.md` |

---