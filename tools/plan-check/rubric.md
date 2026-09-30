# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis-grounded | The plan's stated cause, read against every data point in the repro evidence (each step, and especially any control or negative run) | The stated cause is consistent with every specific fact the repro evidence shows, not just its summary. If the repro evidence contains a control or negative run that isolates a different factor than the plan names (e.g. a run that reproduces the symptom with the plan's blamed component switched off, or fails to reproduce it with the component on), the check fails even if the plan is confident, cites the thread, or is well-written. | required |
| scope-bounded | The plan's scope statement, read against its files/approach list | The change is a single bounded fix addressing only the issue's reported symptom. The files/approach contain no unrelated refactor, migration, new feature, redesign, or "while I'm in there" work beyond what the named cause requires. A plan that is otherwise correct but bundles in extra fronts fails this check. | required |
| stranger-executable | The plan's files list and approach/change steps | At least one concrete file path is named, and the approach is a sequence of concrete edits a reader unfamiliar with the codebase could start from without further research. A plan naming no files, deferring the approach itself ("upstream or vendored, whichever is easier"), or whose only action is "investigate" / "look into it" fails. | required |
| test-plan-decisive | The plan's test plan, read against the repro evidence's steps | The test plan names a specific, observable pass/fail outcome tied to the issue's actual symptom (e.g. re-running the repro steps and naming what should change). "Run the full test suite" or "should feel fast" with no outcome specific to the fix fails, even if the rest of the plan is solid. | required |
| engages-thread-direction | The plan comment, read against the thread highlights | If the thread contains explicit maintainer direction (an approach given, a patch already posted and testing requested, an explicit ask or rejection), the plan comment engages it rather than silently pursuing a conflicting approach. If the thread contains no such direction, this check passes automatically. | required |
| ai-disclosure | The plan comment, read against the repo-facts "contribution policy" line (eval) or the repo's CONTRIBUTING.md / AI policy files (live) | If the repo's stated policy requires disclosing AI-assisted work, the plan comment discloses it. If the policy is silent or sets no disclosure requirement, this check passes automatically. | required |

## Verdict rule

Accept only if all six required checks pass. Unclear counts as fail.
