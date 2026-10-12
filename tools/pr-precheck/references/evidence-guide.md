# Evidence guide: where evidence lives in a PR package

Use this guide to locate evidence for each rubric check and determine whether the evidence satisfies the required standard.

## Plan fidelity (harness category: silent-drift)

### Where it lives
- **Eval bundle**:
  - The plan context block (`Plan:`, `Scope:`, file lists, and approach description).
  - Any `## Deviations` or notes block in the candidate plan.
  - The candidate PR diff headers (`diff --git a/... b/...`) and individual code hunks.
  - The candidate PR description, specifically the summary, "Changes" bullets, and any fidelity claims (such as "implements plan exactly").
- **Live mode**:
  - The workspace `plan.md` file, including its `## Deviations` section.
  - The output of `git diff main...HEAD --stat` and `git diff main...HEAD`.
  - The candidate PR draft in `pr_draft.md` ("Summary" and "Changes" sections).

### What good looks like
- Every file modified in the diff is explicitly listed within the plan's stated scope boundary or accounted for in `## Deviations`.
- The diff implements the agreed-upon fix without introducing unrequested features, new configuration options, unannounced CLI flags, or broad structural refactorings.
- If scope was trimmed, deferred, or expanded during implementation, the difference is explicitly documented in `## Deviations` and honestly disclosed in the PR description.
- The PR description makes no claims of fidelity that the unified diff contradicts (e.g. claiming a docs update was completed when no docs files appear in the diff, or claiming no changes outside the fix when unrelated functions were rewritten).

## Test evidence (harness category: not-tested)

### Where it lives
- **Eval bundle**:
  - The `test-evidence` section and repro command blocks within the package.
  - The issue's reported reproduction steps and the plan's proposed test plan.
  - The repository checks listed in `repo-facts` (e.g. test suites, linters, typecheckers).
- **Live mode**:
  - The `test_evidence.md` file located next to `plan.md`.
  - The "Testing" section of `pr_draft.md`.
  - Transcripts of before and after reproduction runs on `main` vs the fix branch.
  - Transcripts from standard repo checks (`make test-unit`, `make test-integration`, `make lint`, `make typecheck`).

### What good looks like
- Test evidence shows concrete before/after execution transcripts specifically exercising the bug fix on the affected code path.
- The test demonstrates that the error condition observed before the fix is resolved after the fix, rather than merely re-running an unaffected control case.
- Repository test suites and linters are executed, and their outputs/exit codes are reported.
- A failing check honestly reported with its underlying reason counts as valid evidence; vague claims such as "tested locally", "verified working for a day", or "cargo test passes" without observable before/after transcripts fail.

## Diff quality (harness category: unreviewable)

### Where it lives
- **Eval bundle**:
  - The candidate PR's unified diff hunks (`@@ ... @@`).
  - The commit log messages in the bundle.
- **Live mode**:
  - The output of `git diff main...HEAD`.
  - The output of `git log main..HEAD --oneline`.

### What good looks like
- The diff contains strictly the minimal necessary changes to implement the fix and its associated tests.
- Zero debugging remnants are left in code (no `console.log`, `print`, `eprintln`, or temporary `DEBUG` statements).
- Zero commented-out blocks of code, abandoned attempts, or dead functions (such as probe functions left behind `allow(dead_code)`).
- Zero extraneous whitespace churn, re-formatting passes, or re-indentation blocks outside of modified logic.
- No drive-by edits to unrelated files or cleanups that belong in a separate issue.
- Commits are coherent without messy WIP or debugging trial commits.

## Standards and comms (harness category: standards-wall)

### Where it lives
- **Eval bundle**:
  - The `repo-facts` block detailing the repo's stated PR template requirements, checklist items, changelog asks, and contributing policies (including AI-disclosure rules).
  - The candidate PR title and description.
- **Live mode**:
  - The repository's PR template (`.github/PULL_REQUEST_TEMPLATE.md`).
  - The repository's contributing guide (`docs/CONTRIBUTING.md`).
  - The candidate draft in `pr_draft.md`.
  - Any explicit maintainer direction posted in the issue thread.

### What good looks like
- The candidate PR satisfies all explicit asks, sections, and checklists required by that repository (e.g. per `repo-facts` in eval packages, or `.github/PULL_REQUEST_TEMPLATE.md` in live mode). If a repository asks for a type-of-change classification and changelog entry (such as Rich), providing them satisfies the standard. If a repository has no PR template, this check passes automatically.
- Fails when sections or checklists explicitly mandated by the repository (such as pandas' required checklist in `pkg-01`) are visibly skipped, omitted, or left empty.
- If the repository has an explicit policy requiring disclosure of AI-assisted contributions, an honest, own-words disclosure is present in the PR description (or Notes for Reviewers).
- Candidate PR engages directly with any maintainer guidance or constraints posted on the issue thread rather than ignoring it.
