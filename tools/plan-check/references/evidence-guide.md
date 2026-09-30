# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

**Where it lives:**
- **Eval bundle:** The candidate plan's "Diagnosis" (or "Cause") section,
  read against every distinct fact in the "Repro evidence" block — each
  numbered step, each artifact, and especially any control or negative run
  (a step that isolates a factor by removing it, or that names an
  environment/condition where the symptom does *not* appear).
- **Live mode:** The student's draft `plan.md` diagnosis, read against the
  student's own posted repro comment (or the house repro pack when there is
  no repro comment of the student's own).

**What good looks like:** The stated cause explains every fact the repro
evidence records, not just the headline symptom. A diagnosis that matches
the summary but is contradicted by one specific data point — a control run
that reproduces the symptom with the blamed component absent, or fails to
reproduce it with the component present — is not grounded, no matter how
confidently it is written or how directly it echoes something said in the
thread. Thread commentary is a lead, not proof: a diagnosis that only cites
"a maintainer said so" without checking it against the repro evidence's own
steps is not yet grounded. The test is arithmetic, not vibes: list every
repro-evidence fact, then check the stated cause against each one in turn.

## Scope

**Where it lives:**
- **Eval bundle:** The candidate plan's "Scope" section (in-scope /
  not-in-scope lines), read together with its "Files" and "Approach"
  sections — the scope statement is only honest if the approach doesn't
  quietly exceed it.
- **Live mode:** The student's draft `plan.md` scope statement, read
  against its files and approach sections the same way.

**What good looks like:** One bounded change that addresses only what the
diagnosis requires to fix the issue's reported symptom. The approach names
no unrelated refactor, framework/dependency migration, new feature, UI
rework, or "while I'm here" cleanup. A plan can defer a related, harder
problem explicitly (and that honesty is a good sign, not a violation) — the
failure mode is a plan whose approach section quietly does five things when
the diagnosis only requires one.

## Executability

**Where it lives:**
- **Eval bundle:** The candidate plan's "Files" and "Approach" sections.
- **Live mode:** The student's draft `plan.md`, same sections.

**What good looks like:** At least one real file path is named, and the
approach is a numbered or ordered sequence of concrete edits — "extend the
regex in `requestitems.py` to accept X" is executable; "look into the input
handling" or "fix it upstream or vendored, whichever is easier" is not. A
stranger who has never opened the repository should be able to start the
first step without asking the author what it means. A plan that defers the
actual technical decision to build time (which layer, which approach, which
file) fails even if it names the right *area* of the codebase.

## Test plan

**Where it lives:**
- **Eval bundle:** The candidate plan's "Test plan" section, read against
  the repro evidence's steps and artifacts.
- **Live mode:** The student's draft `plan.md` test plan, read against the
  student's own repro steps.

**What good looks like:** The test plan names a specific, observable outcome
tied to the issue's actual symptom — typically, re-running the repro steps
and naming exactly what should differ after the fix (a color that now
flips, an error that no longer appears, a count that changes from zero to
nonzero). "Run the full test suite and make sure nothing regresses" or "it
should feel fast" name no outcome specific to the fix and fail this check,
even when the rest of the plan is strong. A plan may add an automated
regression test in addition to the repro re-run; that is a bonus, not a
substitute for naming the observable behavior the fix produces.

## Thread direction

**Where it lives:**
- **Eval bundle:** The "Thread highlights" section, read against the
  candidate plan comment (and the plan's chosen approach).
- **Live mode:** The live issue thread (or the house repro pack's thread
  summary), read against the student's draft plan comment.

**What good looks like:** When the thread contains explicit maintainer
direction — an approach the maintainer already proposed or rejected, a
patch already posted with testing requested, an explicit ask or an explicit
"no" — the plan comment engages it: agrees and builds on it, or explains
why it takes a different path. A plan that silently pursues an approach the
maintainer already offered a fix for (without acknowledging the offered fix
at all) fails here even if the plan's own diagnosis is correct. When the
thread has no such direction (few or no comments, or comments that are pure
discussion with no explicit ask), this check passes automatically — there
is nothing to ignore.

## AI disclosure

**Where it lives:**
- **Eval bundle:** The repo-facts block's "contribution policy" line, read
  against the candidate plan comment.
- **Live mode:** The repo's `CONTRIBUTING.md`, any `AI_POLICY.md` /
  `AI_USAGE_POLICY.md`, and PR/issue templates, read against the student's
  draft plan comment.

**What good looks like:** If the stated policy requires disclosing
AI-assisted or AI-generated work (naming the tool, the extent of
assistance, or requiring a human-in-the-loop statement), the plan comment
includes that disclosure in its own words. If the policy is silent, or sets
no disclosure requirement, this check passes automatically regardless of
whether AI was used. A policy that asks only for human review (not
disclosure) is satisfied by a comment written in the student's own words —
disclosure and authorship are different requirements; only grade the one
the policy actually states.
