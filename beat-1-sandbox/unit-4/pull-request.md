# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/<PR_NUMBER>

*(Replace `<PR_NUMBER>` with the number of your pull request once opened on GitHub in Step 12).*

**Branch**

fix/37-api-request-body-docs

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Run 1 (smoke run, 2 packages, pkg-01/02): agreement 1/2 scored items (pkg-02 false reject on template-compliance due to hardcoded section list).
- Run 2 (canary run, 2 packages, --only pkg-01,pkg-02): agreement 2/2 scored items after refining template-compliance check in rubric.md and procedure.md to evaluate target repository asks.
- Run 3 (full run, 20 packages, --save-run eval-run.txt): agreement 20/20 scored items (bar: 18/20: PASS), categories: clear-accept 7/7, not-tested 4/4, silent-drift 4/4, standards-wall 2/2, unreviewable 3/3. This is the committed run in eval-run.txt.

**Package analysis**

`pkg-01`
- My rubric decided: `reject`
- Gold label said: `reject`
- Why my rubric read it that way: `pkg-01` provides a solid C-parser fix with decisive ASAN test evidence, but the repository's required PR template checklist was visibly ignored (no `Closes #xxxx` issue link, no checklist items checked, and the stated changelog/whatsnew entry was missing from the diff). My `template-compliance` check requires all template sections and checklists to be filled with substantive content rather than omitted or left blank. Because `template-compliance` is a required check, the rubric correctly held the package despite the technical quality of the code fix.

*(Can be kept as pkg-01 or updated with any scored package from pkg-01 through pkg-20 based on the morning eval run).*

**Check rationale**

Quote from `tools/pr-precheck/rubric.md`:

```markdown
| plan-fidelity | Diff and description read against plan's scope, files, approach, and `## Deviations` | Diff implements what the plan specifies without unrequested features, flags, new settings, or structural refactors. If work differs from the plan or is deferred, the shortfall is explicitly documented in the plan's `## Deviations` (or plan notes) AND stated in the PR description. Fails on silent additions, unannounced scope, unnoted omissions, or PR descriptions claiming fidelity that the diff contradicts. | required |
```

Why it reads that way:
The check was formulated to catch both directions of silent scope drift while actively protecting honestly disclosed shortfalls. In earlier drafts, a simple check requiring "diff matches plan exactly" resulted in false rejections on high-quality pull requests like `pkg-13` and `pkg-16`, where contributors explicitly deferred secondary edge cases (such as `%VAR%` expansion or start-path behavior) with clear reasoning in their deviation notes and PR descriptions. Open-source contribution standards reward honest scoping boundaries, whereas they penalize unannounced scope creep (such as `pkg-03`'s unrequested `truncate()` rewrite and config option, or `pkg-06`'s system-menu renaming pass) and deceptive claims (such as `pkg-17` claiming docs were updated when no doc files exist in the diff). By explicitly tying the pass condition to whether shortfalls are documented in `## Deviations` and re-stated in the PR description, the check enforces transparency rather than penalizing disciplined scoping.

**Trade-offs**

Every check gives something up. In `plan-fidelity` and `diff-reviewability`, our pass conditions enforce a strict zero-tolerance boundary against unannounced additions, debug leftovers (`console.log`, `eprintln`, `DEBUG`), commented-out experiments, dead probe functions behind `allow(dead_code)`, and formatting churn. The trade-off is demonstrated in arguable borderline packages such as `pkg-18` (where mechanical import churn and duplicate lines surround an otherwise correct `is_terminal` fix) and `pkg-09` (where an adjacent `--time-format` flag was bundled with an inner-error fix). In a lenient manual code review, a maintainer might overlook mechanical indentation churn or adjacent flag additions. However, in an automated pre-check gate, relaxing these checks would fail to catch egregious debris (such as `pkg-12` and `pkg-15`). We deliberately accept the cost of holding mechanically churned diffs to ensure that every pull request submitted upstream respects maintainer time and adheres to minimal, reviewable diff standards.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
