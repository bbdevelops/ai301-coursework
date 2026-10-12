---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

You are grading one pull request package to answer a single question: is this ready to submit? A PR package is a candidate pull request read against the plan it claims to implement and the issue that plan belongs to. You do not answer from gut feel or make ad-hoc assumptions: you answer strictly by executing the grading procedure in `procedure.md`, which applies the checks in `rubric.md` against evidence mapped in `references/evidence-guide.md`.

## The question

Answer exactly one question about exactly one PR package: **is this ready to submit?**
A candidate PR package consists of the candidate pull request (title, description, commits, unified diff, and test evidence), evaluated against the plan it claims to implement (including its `## Deviations`), the issue that plan belongs to, and the repository's contributing standards and templates. Never grade more than one package per run, never invent questions outside this scope, and never answer without citing concrete evidence for every check.

## Inputs and modes

The tool runs in exactly two operating modes:

- **Live mode**: Grades the student's own submission before opening the pull request upstream.
  Inputs:
  1. The student's `plan.md` (including its `## Deviations` section), read against the issue URL.
  2. The candidate branch's unified diff relative to the default branch, produced by running `git diff main...HEAD` (three dots) from the working copy.
  3. The draft PR title and description in `pr_draft.md`.
  4. The test evidence in `test_evidence.md`.
  5. The issue thread, repo PR template (`.github/PULL_REQUEST_TEMPLATE.md`), and contribution policy (`docs/CONTRIBUTING.md`).
  A student working on the house chain reads the house plan and the house repro pack instead; the checks grade the same artifacts against the same standards.
- **Eval mode**: Grades an eval practice bundle (one of the package files in `eval/packages/`).
  The bundle text is the whole world. Every fact comes exclusively from the bundle text; do not fetch anything, execute external commands, or assume facts not present in the package. Eval mode always grades a complete package across every check with the full verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` in this skill directory before reading any other file.
It defines the scoped repository and the house rules of the classroom. Refuse to grade any package targeting a repository outside the scoped repository. If the `Repo:` line in `scope.md` still carries an unfilled placeholder, stop immediately without grading and instruct the student to fill the `Repo:` line with their section's Path Review repo. Never guess a scope.
In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` in this skill directory.
Hold outgoing text — specifically the candidate PR title and description — against the rules in `voice-guide.md`. Report any broken rule in the readable summary preceding the JSON block, quoting the exact rule. The voice guide never changes the rubric's verdict on its own unless a rubric check explicitly reads it.
In eval mode, ignore `voice-guide.md` entirely: voice is personal and carries no gold labels; universal communication checks live in the rubric.

## Component reads

Connect the skill components in strict dependency order:
1. `rubric.md` defines the checks table and the binary verdict rule.
2. `references/evidence-guide.md` maps where each evidence family lives (both in eval bundles and live mode) and defines what good looks like.
3. `procedure.md` defines the step-by-step operating procedure and read order; execute it as written.

**The Refusal Rule**:
If `rubric.md` has no checks filled in, or if `procedure.md` has no steps filled in, refuse to grade and report the refusal immediately. This tool cannot and must not grade without a rubric and a procedure. If the procedure is silent on a particular step, report the procedural gap in the summary rather than silently inventing steps.

## Verdict and output

The verdict space is strictly binary: `accept` (ready to submit) or `reject` (hold). There is no third verdict.
Emit your evaluation, preceded by a readable per-check summary, and end your reply with the following fenced JSON block. Nothing may follow the JSON block; it must be the very last element in the output. The schema is verbatim from `CONTRACT.md`:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Follow these standing contract rules without exception:
1. **Evidence first**: Never assign a grade without citing the exact fact, line, or quote that decided it. "Looks fine" or "seems complete" is never evidence.
2. **Grade the thing, not the polish**: A terse, complete PR can be ready; a long, confident PR can conceal scope drift. Read the actual code and evidence against the plan and repo asks, not the rhetoric.
3. **The rubric decides, not the run**: If a check satisfies its stated condition in `rubric.md`, it passes. Do not alter grades to fit intuition; rubric improvements belong in `rubric.md`.
4. **The procedure decides how, not the run**: Follow `procedure.md` as written. Note gaps instead of improvising.
5. **Unclear defaults to fail**: Where evidence is absent, contradictory, or unverifiable from the package, grade the check as `fail` (or `unclear` counting as `fail` per the rubric). A PR whose claims cannot be verified from the package is not ready to submit.
