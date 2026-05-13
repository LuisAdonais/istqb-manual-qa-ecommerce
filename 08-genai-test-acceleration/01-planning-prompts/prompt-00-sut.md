# prompt-00 — System Under Test (SUT)

| Attribute         | Detail                                                            |
| :---------------- | :---------------------------------------------------------------- |
| **Location**      | `08-genai-test-acceleration/01-planning-prompts/prompt-00-sut.md` |
| **Project**       | Tricentis Demo Web Shop                                           |
| **Version**       | 1.0                                                               |
| **STLC Phase**    | Pre-Planning                                                      |
| **GenAI Technique** | Zero-shot prompting · Structured prompt · Iterative HITL        |
| **Reference**     | CT-GenAI GenAI-2.1.1 / GenAI-2.1.3 / GenAI-2.3.2                  |

---

## Artifact Description

The **System Under Test (SUT)** identifies and defines the test object before any STLC activity begins. According to ISTQB CTFL v4.0, the *test object* is "the component or system to be tested."

**Role in STLC:** Enables the Planning phase by providing the baseline for the object to be tested. Without an approved SUT, scope, risks, and test strategy cannot be defined.

**Required data:** Product description, public URL, operating system, environment browser, functional user roles, list of identified modules, and explicit exclusions.

> ⚠️ **Pending Section:** The `Ref. REQ` column in the **Modules in Scope** section will be completed in a second iteration, once `requirements.md` is available and **`REQ`** IDs are assigned. The tester will return to this artifact with those details to close traceability.

---

## Prompt

> 🔗 **Requires:** `system-prompt.md` + `context-rules.md` must be active before running this prompt.

---

### Instruction

Build the `system-under-test.md` artifact in collaboration with the tester using this process:

1. Review the input data provided by the tester.
2. Complete all sections of the Output format that can be filled with this input.
3. For every field that cannot be completed with the received input, ask a clear question to the tester — maximum 3 questions at a time.
4. Wait for the tester's response and incorporate it before proceeding.
5. Repeat until all sections are complete, except for `Ref. REQ`, which remains empty until `requirements.md` is received.

Do not assume data. Do not invent modules. Do not add sections outside the Output format.

---

### Input data

The tester provides in their first message:

```text
System name              :
URL                      :
Architecture             :
Domain                   :
Operating system         :
Browser + version        :
User roles               : [role] → [accessible features]
Observed modules         : [free list]
Exclusions               : [free list]
```

> 💬 **If the tester does not provide all fields,** the model identifies which are missing and asks for them in the first exchange before generating any section of the artifact.

---

### Constraints

- Do not fill `Ref. REQ` — that column is completed in a later iteration.
- Do not include risks, objectives, or test criteria.
- Do not infer modules not included in the tester input.
- Mandatory header: Location, Project, Version, STLC Phase, Status (`Draft` until approved), QA Owner.
- Maximum 3 questions per exchange — prioritize blocking questions.

---

### Output format

```markdown
# System Under Test (SUT)

| Attribute      | Detail |
| :------------- | :----- |
| **Location**   | `00-context-and-overview/system-under-test.md` |
| **Project**    | [name] |
| **Version**    | [x.x] |
| **STLC Phase** | Pre-Planning |
| **Status**     | Draft |
| **QA Owner**   | [name] |

---

## Identification

| Attribute         | Detail |
| :---------------- | :----- |
| **Name**          | [system name] |
| **URL**           | [url] |
| **Architecture**  | [architecture] |
| **Domain**        | [domain] |
| **Environment**   | [OS / Browser version] |

---

## Stakeholders

| Role     | Functional Access         |
| :------- | :------------------------ |
| [Role 1] | [accessible features]     |
| [Role 2] | [accessible features]     |

---

## Modules in Scope

> ⚠️ `Ref. REQ` column is pending — to be completed when `requirements.md` is available.

| Module     | Ref. **`REQ`** |
| :--------- | :------------- |
| [Module 1] | —              |
| [Module N] | —              |

---

## Out of Scope

- [exclusion 1]
- [exclusion N]
```

---

## Traceability

| This prompt         | Feeds into                                              |
| :------------------ | :----------------------------------------------------- |
| `prompt-00-sut.md`  | `prompt-01-test-plan.md`                               |
| Second iteration    | `prompt-02-requirements.md` → returns to close `Ref. REQ` |

---
