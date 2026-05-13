
# prompt-07 — Test Environment Setup

| Attribute    | Detail |
| :---         | :--- |
| **Location** | `08-genai-test-acceleration/04-implementation-prompts/prompt-07-environment.md` |
| **Project**  | Tricentis Demo Web Shop |
| **Version**  | 1.0 |
| **STLC Phase** | Test Implementation |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference** | CT-GenAI GenAI-2.1.1 / GenAI-2.2.2 |

## Artifact Description

The **Test Environment Setup** documents the configuration required to execute the test suites. According to ISTQB CTFL v4.0, it is a *test implementation work product* that includes hardware, software, configuration data, and environment preparation procedures.

**Role in the STLC:** Ensures the environment is ready before execution starts. It is the single source of truth for evidence naming conventions.

**Input sources:** Identified SUT, environment OS and browser, evidence capture tool, pre-created account data.

---

## Prompt

> [!TIP]
> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-06-test-data.md`.

### Instruction

Build the `test-environment-setup.md` collaboratively with the tester:

1. Request details about the physical and logical environment from the tester.
2. Document the preparation steps required before execution.
3. Record the evidence naming convention as the single source of truth.
4. Validate with the tester before marking the draft as ready for review.

Do not invent software versions or tools that have not been confirmed.

### Input data

```text
OS                 : [operating system + version]
Browser            : [name + version]
SUT URL            : [url]
Capture Tool       : [name of screenshot tool]
Pre-created Account: [TD-XX → email + password]
Prep Steps         : [actions before execution — e.g., clear cache]
Evidence convention: YYYY-MM-DD_TX-XX.XX_Description_STATUS.png
```

### Constraints

- The evidence naming convention must appear in a highlighted section.
- Preparation steps are not **`TX`** cycles — do not assign execution IDs.
- Header must include State `Draft`.

### Output format

```markdown
# Test Environment Setup

| Attribute     | Detail |
| :---          | :--- |
| **Location**  | `04-test-implementation/test-environment-setup.md` |
| **Project**   | [name] |
| **Version**   | [x.x] |
| **STLC Phase**| Test Implementation |
| **State**     | Draft |
| **QA Owner**  | [name] |

## 1. Environment Configuration

| Component            | Detail             |
| :---                 | :---               |
| **OS**               | [OS + version]     |
| **Browser**          | [name + version]   |
| **SUT URL**          | [url]              |
| **Evidence Tool**    | [tool name]        |

## 2. Evidence Naming Convention

> [!IMPORTANT]
> ⚠️ This section is the single source of truth for evidence naming conventions.

```text
YYYY-MM-DD_TX-XX.XX_ShortDescription_STATUS.png
```

**Example:** `2026-05-04_TX-01.01_Register_Submit_PASS.png`

## 3. Data Preparation

> [!NOTE]
> These steps are for environment setup only and do not represent a formal **`TX`** cycle.

1. [preparation step]

## 4. Traceability

| Environment Requirement | Dependent **`TS`** | State   |
| :---                    | :---              | :---    |
| [requirement]           | **`TS-XX`**       | [state] |

```

## Traceability

| This prompt                  | Feeds into                           |
| :---                         | :---                                 |
| `prompt-07-environment.md`   | `prompt-08-procedures.md` · `prompt-09-test-suites.md` |

---