# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

1. Read the repo-facts block (eval) or gather the repo's stated
   contribution policy and templates (live) first, so the AI-disclosure
   and thread-direction checks have their standard in hand before anything
   else is read.
2. Read the issue (title, body, labels) to know what symptom was reported.
3. Read the thread highlights (eval) or the live thread (live) and note,
   in one line each, any comment that is explicit maintainer direction: a
   proposed or rejected approach, a posted patch with testing requested, or
   an explicit ask. Most threads have none — note that explicitly too
   ("no direction present") rather than leaving it blank.
4. Read the repro evidence in full and list every distinct fact as its own
   line: every numbered step, every artifact, and every control or
   negative run named separately from the "expected"/"actual" summary.
   Do this listing **before** reading the candidate plan — reading the
   plan's diagnosis first anchors on the plan's narrative instead of the
   evidence, which is exactly how a confident-but-wrong diagnosis gets
   missed.
5. Only now read the candidate plan, section by section (diagnosis, scope,
   files, approach, test plan).
6. Read the candidate plan comment last.

## Evidence gathering

For each check, pull evidence per `references/evidence-guide.md`'s
matching heading, and record it in one line before grading:

- **diagnosis-grounded**: the plan's stated cause (one line), and the full
  list of repro-evidence facts from Read order step 4. Check the stated
  cause against every fact on that list, not just the summary line.
- **scope-bounded**: the plan's in-scope/not-in-scope statement, plus the
  full files/approach list, side by side.
- **stranger-executable**: the files list and the approach steps, verbatim.
- **test-plan-decisive**: the plan's test plan section, plus the specific
  repro-evidence step(s) it claims to re-run or the outcome it claims to
  observe.
- **engages-thread-direction**: the maintainer-direction note from Read
  order step 3, plus the plan comment's full text.
- **ai-disclosure**: the repo's stated policy (present or absent, and its
  exact disclosure requirement if present), plus the plan comment's full
  text.

## Check execution

1. Grade in the order the rubric table lists them:
   `diagnosis-grounded`, `scope-bounded`, `stranger-executable`,
   `test-plan-decisive`, `engages-thread-direction`, `ai-disclosure`.
2. For each check, grade `pass`, `fail`, or `unclear` using only the
   evidence gathered for that check, and record the single fact or quote
   that decided it.
3. If the named evidence is genuinely absent from the package (not merely
   thin), grade `unclear` and name what's missing. Do not infer or guess
   evidence that was not actually recorded.
4. `engages-thread-direction` and `ai-disclosure` pass automatically when
   their respective trigger is absent (no maintainer direction in the
   thread; no stated disclosure policy) — grade `pass` with that reason,
   not `unclear`.
5. A check already decided by an earlier check's evidence may reuse that
   evidence without re-reading the whole package, but must still be
   graded on its own stated pass condition — do not let one check's
   failure automatically fail another.

## Verdict assembly

1. Apply the rubric's verdict rule: `accept` only if all six required
   checks pass; any `fail` or `unclear` on a required check makes the
   verdict `reject`.
2. In the output summary, name the single check that decided the verdict
   (the first failing/unclear check in the execution order above) and
   quote its evidence line. If every check passes, name `diagnosis-grounded`
   as the anchor check and quote its evidence line instead.
3. Produce the same verdict from the same six grades every time; the rule
   has no discretion beyond what step 1 states.
