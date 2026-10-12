# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-fidelity | Diff and description read against plan's scope, files, approach, and `## Deviations` | Diff implements what the plan specifies without unrequested features, flags, new settings, or structural refactors. If work differs from the plan or is deferred, the shortfall is explicitly documented in the plan's `## Deviations` (or plan notes) AND stated in the PR description. Fails on silent additions, unannounced scope, unnoted omissions, or PR descriptions claiming fidelity that the diff contradicts. | required |
| decisive-test-evidence | Test evidence read against plan's test plan, repro steps, and repo check suite | Shows observable before/after output specifically exercising the bug fix on the affected path (not merely an unchanged control path). Required repo checks (such as unit test suites, linters, or typecheckers) are executed and results reported. Fails if evidence shows only an unchanged control path, if repo checks were never run, or if evidence is merely a vague assurance like "tested locally", "verified working", or "tests pass" without observable before/after output. | required |
| diff-reviewability | Unified diff and commit history | Diff contains only the intended fix and necessary tests. Contains no debugging leftovers (`console.log`, `eprintln`, `DEBUG` prints), commented-out code blocks or exploratory attempts, dead functions (e.g. behind `allow(dead_code)`), whitespace or re-indentation churn, or unrelated file hunks. | required |
| template-compliance | PR description read against repo PR template (`.github/PULL_REQUEST_TEMPLATE.md` or repo-facts block asks) | The PR description satisfies all explicit asks stated in the repository's PR template or repo facts (such as required sections, checklists, changelog entries, or issue references). If the repository specifies no required template sections, or if all repo-specific asks are addressed (e.g. naming the type of change or issue number), this check passes. Fails only when sections, checklists, or asks explicitly mandated by that repository are visibly skipped, deleted, or left blank. | required |
| ai-disclosure | PR description (or Notes for Reviewers) read against repo contribution policy | If the repo's stated contribution policy requires disclosing AI-assisted contributions, an explicit disclosure is present in the candidate's own words. If the repo's stated policy does not require AI disclosure, this check passes automatically. | required |

## Verdict rule

Accept if and only if all five required checks pass. Preferred checks never change the verdict. Unclear counts as fail.
