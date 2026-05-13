
# prompt-02 — Requirements Specification

| Attribute | Detail |
| :--- | :--- |
| **Location** | `08-genai-test-acceleration/02-analysis-prompts/prompt-02-requirements.md` |
| **Project** | Tricentis Demo Web Shop |
| **Version** | 1.0 |
| **STLC Phase** | Test Analysis |
| **GenAI Technique** | Prompt chaining · Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.1 |

## Artifact Description

The **Requirements Specification** artifact documents functional requirements (**`REQ`**) and their acceptance criteria (**`AC`**) derived from the SUT. According to ISTQB CTFL v4.0, *test analysis work products* include prioritized test conditions, originally based on acceptance criteria. The **`AC`** are the conditions that an implementation must meet to be accepted by stakeholders.

**Role in the STLC:** Serves as the primary test basis. Without approved **`REQ`** and **`AC`**, test conditions or test cases cannot be defined.

**Input sources:** Modules in scope from the Test Plan, direct observation of the SUT by the tester, and agreed functional criteria.

> [!WARNING]
> ⚠️ **Pending closure in SUT:** Once **`REQ`** IDs are assigned, return to `system-under-test.md` and complete the `Ref. REQ` column in the Modules in Scope table.

---

## Prompt

> [!TIP]
> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-01-test-plan.md`.

### Instruction

Build the `requirements.md` artifact in collaboration with the tester:

1. Read the modules in scope from the Input data.
2. For each module, request from the tester a description of the functional requirement and the observed acceptance criteria.
3. Maximum 3 questions per interaction — prioritize higher-risk modules.
4. For each item, structure it according to the Output format and wait for tester validation before proceeding to the next module.

Do not infer unconfirmed behavior. Do not add AC without tester confirmation.

### Input data

```text
Modules in Scope : [list of Test Plan modules]
For each module, tester provides:
  REQ description  : [what the system does — third-person verb]
  Priority         : [High / Medium / Critical]
  Observed AC      : [verifiable condition — one per line]
```

### Constraints

- Each **`AC`** must be binary (Pass / Fail).
- Do not use subjective terms: "correctly", "adequately".
- Sequential IDs: **`REQ-01`**, **`REQ-02`**… / **`AC-01`**, **`AC-02`**…
- Mandatory heading with Status `Draft`.

### Output format

```markdown
# Requirements Specification

| Attribute | Detail |
| :--- | :--- |
| **Location** | `02-test-analysis/requirements.md` |
| **Project** | [name] |
| **Version** | [x.x] |
| **STLC Phase** | Test Analysis |
| **Status** | Draft |
| **QA Owner** | [name] |

## 1. Functional Requirements (`REQ`)

| ID | Module | Description | Priority |
| :--- | :--- | :--- | :--- |
| **`REQ-01`** | [module] | [description] | [priority] |

## 2. Acceptance Criteria (`AC`)

| ID | **`REQ`** | Acceptance Criteria | Status |
| :--- | :--- | :--- | :--- |
| **`AC-01`** | **`REQ-01`** | [verifiable criterion] | ✔️ Verifiable |

## 3. Traceability

| **`REQ`** | **`AC`** |
| :--- | :--- |
| **`REQ-XX`** | **`AC-XX`**, **`AC-XX`** |
```

## Traceability

| This prompt | Feeds | Returns to |
| :--- | :--- | :--- |
| `prompt-02-requirements.md` | `prompt-03-basis-evaluation.md` | `prompt-00-sut.md` → complete `Ref. REQ` |

---