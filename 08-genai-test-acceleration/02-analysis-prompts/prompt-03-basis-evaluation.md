
# prompt-03 — Test Basis Evaluation

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/02-analysis-prompts/prompt-03-basis-evaluation.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Analysis |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Artifact Description

The **Test Basis Evaluation** records static anomalies (**`AN`**) detected while reviewing the test basis. According to ISTQB CTFL v4.0, test analysis involves reviewing the test basis to identify any defects it may contain (ambiguities, inconsistencies, missing information) and to evaluate its testability.

**Role in the STLC:** Cleanses the test basis before design. Each resolved **`AN`** helps prevent false execution results.

**Inputs:** Approved `requirements.md` — item-by-item review of each **`REQ`** and **`AC`**.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-02-requirements.md`.

### Instruction

Review the `requirements.md` artifact in collaboration with the tester:

1. Analyze each **`REQ`** and **`AC`** for ambiguity, missing or incomplete information, criteria that cannot be verified as Pass/Fail, or undocumented implicit behaviors.
2. For each anomaly found, present it to the tester as a clear question for resolution.
3. Record the status of each **`AN`**: Resolved before design / Pending.
4. Maximum 3 anomalies per exchange.

Do not invent anomalies. Each **`AN`** must reference a specific **`REQ`** or **`AC`**.

### Input data

```text
Test basis        : [content of requirements.md]
For each AN the tester provides:
  Description     : [what is wrong or missing]
  Affected REQ/AC : [ID]
  Resolution      : [correction applied or decision made]
  Status          : [Resolved / Pending]
```

### Constraints

- Sequential IDs: **`AN-01`**, **`AN-02`**, etc.
- Each **`AN`** must reference a **`REQ`** or **`AC`**.
- Do not suggest design or architectural fixes.
- Header must include State `Draft`.

### Output format

```markdown
# Test Basis Evaluation

| Attribute | Detail |
| :--- | :--- |
| **Location** | `02-test-analysis/test-basis-evaluation.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Analysis |
| **State** | Draft |
| **QA Owner** | [name] |

## Static Anomalies (`AN`)

| ID | **`REQ`** / **`AC`** | Description | Resolution | Status |
| :--- | :--- | :--- | :--- | :--- |
| **`AN-01`** | **`REQ-XX`** | [description] | [resolution] | Resolved / Pending |

## Traceability

| **`AN`** | Affected **`REQ`** / **`AC`** | Impact on Design |
| :--- | :--- | :--- |
| **`AN-XX`** | **`REQ-XX`** | [impact description] |
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-03-basis-evaluation.md` | `prompt-04-test-conditions.md` |

---

---