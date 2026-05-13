
# prompt-05 — Test Cases

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/03-design-prompts/prompt-05-test-cases.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Design |
| **GenAI Technique** | Prompt chaining · Structured prompt · Meta-prompting · HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.2 |

## Artifact Description

A **test case** is a set of preconditions, inputs, actions, expected results, and postconditions, developed to cover a specific test objective. According to ISTQB CTFL v4.0, it is a *test design work product* that answers "how to test?" a test condition.

**Function in the STLC:** Converts each **`TCND`** into executable steps with a binary expected result.

**Input sources:** Approved `test-conditions.md`, design techniques from the Test Plan (**`EP`**, **`BVA`**, **`State Transition`**, **`Error Guessing`**), preliminary test data.

---

## Prompt

> [!TIP]
> 🔗 **Requires:** `system-prompt.md` + active `context-rules.md`. Input: completed `prompt-04-test-conditions.md`.

### Instruction

Generate test cases in collaboration with the tester:

1. For each **`TCND`**, propose the respective **`TC`** including precondition, steps, and expected result.
2. Identify the applied test design technique (**`EP`** / **`BVA`** / **`State Transition`** / **`Error Guessing`**).
3. Present each proposal to the tester for validation of steps and expected result before continuing.
4. Maximum of 3 test cases per exchange.

One step = one action. Expected result = verifiable in a binary manner. No subjective terms.

### Input data

```text
Approved TCND      : [list of TCND]
Plan techniques    : [EP / BVA / State Transition / Error Guessing]
For each test case the tester confirms:
  Precondition     : [system state before step 1]
  Steps            : [imperative action — one per line]
  Expected result  : [observable and binary]
  Technique        : [EP / BVA / ST / EG]
  Priority         : [High / Medium / Critical]
```

### Constraints

- Use imperative voice in all steps: "Enter", "Click on", "Validate".
- Sequential IDs: **`TC-01`**, **`TC-02`**, etc.
- Each **`TC`** must reference its **`TCND`**.
- Do not add architecture notes or business risk analysis.

### Output format

```markdown
## **`TC-01`** — [descriptive name]

| Attribute | Detail |
| :--- | :--- |
| **`TCND`** | **`TCND-XX`** |
| **Technique** | [EP / BVA / ST / EG] |
| **Priority** | [priority] |
| **Precondition** | [initial state] |

| Step | Action | Expected Result |
| :--- | :--- | :--- |
| 1 | [imperative action] | [binary result] |
| N | [imperative action] | [binary result] |

**Postcondition:** [system state after final step]
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-05-test-cases.md` | `prompt-06-test-data.md` · `prompt-08-procedures.md` |

---