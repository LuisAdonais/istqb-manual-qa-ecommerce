
# prompt-15 — Individual Bug Reports

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `08-genai-test-acceleration/06-defect-prompts/prompt-15-individual-bugs.md` |
| **Project**    | Tricentis Demo Web Shop |
| **Version**    | 1.0 |
| **STLC Phase** | Defect Management |
| **GenAI Technique** | Structured prompt · Iterative HITL |
| **Reference**  | CT-GenAI GenAI-2.1.1 / GenAI-2.2.4 |

## Artifact Description

An **Individual Bug Report** (**`BUG-XX`**) is the detailed report for a single defect. According to ISTQB CTFL v4.0, it must include: unique identifier, title, date, environment, context, steps to reproduce, expected vs. actual result, severity, priority, status, and references.

**Role in the STLC:** Provides the development team with sufficient information to reproduce and resolve the defect. Each file documents a single defect.

**Data sources:** Input from `defect-reports.md`, execution evidence, source **`TX`** and **`TC`**.

---

## Prompt

> 🔗 **Requires:** Active `system-prompt.md` + `context-rules.md`. Input: Completed `prompt-14-defect-reports.md`.

### Instruction

Generate an individual file per defect collaboratively with the tester:

1. For each **`BUG`** in the consolidated table, request steps to reproduce and evidence from the tester.
2. Structure the report according to the Output format.
3. Validate expected result vs. actual result with the tester — both must be concrete and observable.
4. One file per **`BUG`** — do not consolidate multiple defects into a single file.

### Input data

```text
BUG to document      : [BUG-XX]
Origin TX           : [TX-XX.XX]
Failed TC           : [TC-XX]
Affected REQ        : [REQ-XX]
Steps to Reproduce  : [numbered steps]
Expected Result     : [behavior per REQ / AC]
Actual Result       : [what happened]
Evidence            : [file name according to convention]
Severity            : [Critical / High / Medium / Low]
Priority            : [High / Medium / Low]
```

### Constraints

- File name: `BUG-XX_[Short-Title].md`.
- Expected result must reference the relevant **`AC`**.
- Actual result must be observable, no interpretation.
- Do NOT use "correctly", "adequately" in any section.

### Output format

```markdown
# **`BUG-XX`** — [Descriptive Title]

| Attribute      | Detail |
| :---           | :--- |
| **Location**   | `06-defect-management/BUG-XX_[Title].md` |
| **Project**    | [name] |
| **Date**       | [YYYY-MM-DD] |
| **Origin TX**  | **`TX-XX.XX`** |
| **Failed TC**  | **`TC-XX`** |
| **Affected REQ** | **`REQ-XX`** |
| **Severity**   | [severity] |
| **Priority**   | [priority] |
| **Status**     | Open |
| **QA Owner**   | [name] |

## Steps to Reproduce

| Step | Action |
| :--- | :--- |
| 1    | [imperative action] |

## Expected Result

[Behavior defined in **`AC-XX`**]

## Actual Result

[What happened — observable]

## Evidence

`[file-name.png]`
```

## Traceability

| This prompt                    | Feeds                        |
| :---                           | :---                         |
| `prompt-15-individual-bugs.md` | `prompt-13-execution-summary.md` · `prompt-17-summary-report.md` |

---