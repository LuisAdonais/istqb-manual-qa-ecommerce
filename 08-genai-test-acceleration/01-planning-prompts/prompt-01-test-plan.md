
---

# prompt-01 — Test Plan

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/01-planning-prompts/prompt-01-test-plan.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Planning |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.1.2 / GenAI-2.2.1 |

## Artifact Description

The **Test Plan** is the work product that defines the scope, approach, resources, and schedule for testing activities. According to ISTQB CTFL v4.0, it is a *test planning work product* including: scope, objectives, strategy, entry/exit criteria, product risks, and traceability.

**Role in the STLC:** Governs the entire cycle. Without an approved Test Plan, no test analysis or design phase can begin.

**Input sources:** Approved `system-under-test.md`, modules in scope, product risks identified by the QA Lead, and selected test techniques.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-00-sut.md`.

### Instruction

Build the `test-plan.md` artifact in collaboration with the tester:

1. Review the provided Input data.
2. Complete scope, objectives, and approach using the available information.
3. For risks and criteria: request missing data from the tester — maximum 3 questions per interaction.
4. Incorporate answers and continue until all sections are complete.

Do not invent risks. Do not assume exit criteria thresholds without tester confirmation.

### Input data

```text
Approved SUT         : [reference to system-under-test.md]
Modules in Scope     : [list of REQ]
Test Level           : [System / Integration / Acceptance]
Test Type            : [Functional / Non-functional]
Strategy             : [Risk-based / Coverage-based]
Applied Techniques   : [EP / BVA / State Transition / Error Guessing]
Product Risks        : [description + priority per module]
Exit Criteria Threshold: [% execution / pass rate / open critical bugs]
```

### Constraints

- No architectural analysis or development decisions.
- Only include risks based on modules declared in the SUT.
- Mandatory header: Location, Project, Version, STLC Phase, Status (`Draft`), QA Owner.

### Output format

```markdown
# Test Plan

| Attribute | Detail |
| :--- | :--- |
| **Location** | `01-test-planning/test-plan.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Planning |
| **Status** | Draft |
| **QA Owner** | [name] |

## 1. Scope

### In Scope

| Module | **`REQ`** |
| :--- | :--- |
| [module] | **`REQ-XX`** |

### Out of Scope

- [exclusion]

## 2. Objectives

- [objective 1]

## 3. Test Approach

| Category | Definition |
| :--- | :--- |
| **Level** | [level] |
| **Type** | [type] |
| **Strategy** | [strategy] |

**Applied Techniques:**

| Technique | Application |
| :--- | :--- |
| [technique] | [module / TC] |

## 4. Entry and Exit Criteria

### Entry Criteria

- [criterion]

### Exit Criteria

| Criterion | Threshold |
| :--- | :--- |
| [criterion] | [threshold] |

## 5. Product Risks

| ID | Description | Priority | Mitigation |
| :--- | :--- | :--- | :--- |
| **`RISK-01`** | [description] | [priority] | [mitigation] |

## 6. Traceability

| **`REQ`** | **`TCND`** | **`TC`** | **`RISK`** |
| :--- | :--- | :--- | :--- |
| **`REQ-XX`** | — | — | **`RISK-XX`** |
```

## Traceability

| This prompt | Feeds |
| :--- | :--- |
| `prompt-01-test-plan.md` | `prompt-02-requirements.md` |

---