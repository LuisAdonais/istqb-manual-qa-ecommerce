# Lessons Learned

| Attribute    | Detail                                     |
| :---         | :---                                       |
| **Location** | `07-test-completion/lessons-learned.md`    |
| **Project**  | Tricentis Demo Web Shop                    |
| **Version**  | 1.1                                        |
| **STLC Phase** | Test Completion                          |
| **Period**   | 2026-05-04 — 2026-05-05                    |
| **Status**   | ✅ Completed                               |
| **QA Owner** | Luis Adonais Malave Gamardo                |

---

## Context

The requirements (**`REQ`**) were built through reverse engineering of the SUT — there was no previous functional documentation. It is a public demo environment used for practice, and that influenced some decisions during the cycle.

---

## What Worked

**LL-01 — Building the traceability chain from the start was worth the effort.**

Defining **`REQ`**→**`AC`**→**`TC`**→**`TX`**→**`BUG`** as a mandatory structure from the beginning had a high planning cost, but when **`BUG-03`** appeared, finding the issue in **`AC-04`** only took seconds. Without that chain, I would have had to rebuild my reasoning from scratch at the worst moment.

**LL-02 — Documenting the deviation in `EDN-01` was better than ignoring it or stopping the cycle.**

The entry criteria for **`TS-02`** and **`TS-03`** required 100% PASS in **`TS-01`**, but the defects found were Low and Medium severity, with no impact on the main flow. Instead of silently skipping the criteria, I documented the decision in **`EDN-01`** and continued with traceability. This is what I would do in a real team.

**LL-03 — Static review of my own requirements also found real issues.**

**`AN-02`** appeared while reviewing **`REQ-07`**: the requirement included email notification after checkout, but the SUT only displays an order number on screen. If I hadn't adjusted **`AC-09`** before designing, **`TC-09`** would have produced a FAIL for behavior the system never had — a false defect.

---

## What Needs Improvement

**LM-01 — The "100% PASS" criteria does not work when using a public demo environment.**

Setting the suite entry threshold by PASS percentage instead of by defect severity was a design mistake in the Test Plan. I fixed it with **`EDN-01`**, but I should have thought about it earlier. For the next cycle, entry criteria will be defined by what actually blocks the work, not by a round number.

**LM-02 — An ambiguous expected result was detected and fixed before release.**

Step 3 of **`TP-03`** used "or" to describe two possible results, which prevented a single verdict. I found this in the cycle review and fixed it in **`test-procedures.md`** v1.7 — the two branches became separate conditions. Every expected result must allow exactly one verdict: Pass or Fail.

**LM-03 — Implicit SUT behaviors must be captured before writing the requirements.**

**`AN-05`** — entering `Qty.=0` removes the item without confirmation — was discovered while executing **`TX-02.02`**, not during analysis. A quick exploratory walkthrough of the SUT before writing **`REQ`** would have allowed me to capture this up front.

---

## Cycle Metrics

| Indicator                  | Value                  |
| :---                       | :---                   |
| Artifacts produced         | 19 Markdown documents  |
| Static anomalies detected  | 5 (AN-01 to AN-05)     |
| Defects reported           | 3 — density 0.25 BUG/TX|
| Blocking defects at closure | 0                     |
| Formalized deviations      | 1 (EDN-01)             |

---

## Traceability

| Lesson   | Source Artifact                          |
| :---     | :---                                    |
| **LL-01** | **`BUG-03`**, REQ→TX chain             |
| **LL-02** | **`EDN-01`**, **`test-suites.md`**     |
| **LL-03** | **`AN-02`**, **`AC-09`**               |
| **LM-01** | **`test-suites.md`**, **`EDN-01`**     |
| **LM-02** | **`TP-03`** v1.7                       |
| **LM-03** | **`TX-02.02`**, **`AN-05`**            |