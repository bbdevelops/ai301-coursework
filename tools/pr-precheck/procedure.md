# Procedure: how this tool grades a PR package

Follow these steps sequentially to evaluate a candidate pull request package against the rubric.

## Read order

Establish ground truth before reading candidate claims to prevent author narrative bias:

1. **Step 1: Read repo standards and policy**:
   Read the repository facts, PR template (`.github/PULL_REQUEST_TEMPLATE.md`), and contribution policy (`docs/CONTRIBUTING.md`). Note down all required template sections, checklists, issue reference formats, changelog asks, and AI disclosure requirements explicitly stated for that specific repository. If the repository specifies no PR template or minimal asks, note that as the repository standard.
2. **Step 2: Read issue context**:
   Read the issue description, reported symptoms, error traces, and maintainer guidance. Note what specific problem requires solving.
3. **Step 3: Read plan and deviations**:
   Read the candidate plan's stated scope boundary, target files, proposed approach, test plan, and any `## Deviations` section. Note the precise boundaries of what was planned and any explicitly documented shortfalls or deferrals.
4. **Step 4: Read diff and commits**:
   Read the unified diff and commit history independently. List all modified, added, or deleted files. Inspect all code hunks directly before reading the candidate's description of them.
5. **Step 5: Read test evidence**:
   Read the test evidence section (`test_evidence.md` or package test block). Check for before/after command output and repository test suite execution.
6. **Step 6: Read PR title and description last**:
   Read the candidate's draft PR title and description only after examining the artifacts above. Cross-check the candidate's claims against the diff, plan, test results, and repository template requirements.

## Evidence gathering

Gather concrete evidence for each check using side-by-side pairings:

1. **Plan fidelity pairing (`plan-fidelity`)**:
   - Extract the list of files modified in the unified diff (`diff --git a/... b/...`).
   - Compare modified files and functional additions against the plan's stated file list, approach, and scope boundaries.
   - If diff hunks add features, flags, options, or refactors not in the plan: check whether they are explicitly documented in `## Deviations` and stated in the PR description.
   - If diff hunks omit planned functionality: check whether the omission is explicitly documented in `## Deviations` and explained in the PR description.
   - Compare description fidelity claims (e.g. "implements plan exactly") against the actual diff changes.
2. **Test evidence pairing (`decisive-test-evidence`)**:
   - Extract the before/after execution transcripts from the test evidence.
   - Verify whether the reproduced test case specifically exercises the defect on the affected code path (as opposed to an unchanged control path).
   - Check whether repository test suites (e.g., `make test-unit`, `make lint`, `cargo test`, `pytest`) were executed and their exit status / results reported.
3. **Diff quality inspection (`diff-reviewability`)**:
   - Inspect all diff hunks for debugging leftovers (`console.log`, `print`, `eprintln`, `DEBUG` statements).
   - Inspect for commented-out code blocks, experimental prototypes, or dead probe functions (e.g. functions marked `allow(dead_code)`).
   - Check for unnecessary formatting, whitespace churn, or re-indentation blocks.
   - Check for drive-by edits to unrelated files.
4. **Template compliance verification (`template-compliance`)**:
   - Read the candidate PR description against the target repository's stated template requirements from `repo-facts` (or live, `.github/PULL_REQUEST_TEMPLATE.md`).
   - Check whether all sections, checklists, changelog entries, or issue references explicitly requested by THAT repository are addressed.
   - Do not require arbitrary headings or checklists that the target repository's template never asked for.
5. **AI disclosure verification (`ai-disclosure`)**:
   - Check whether the repository's contributing policy mandates disclosure of AI-assisted contributions.
   - If mandated, locate the disclosure in the description or Notes for Reviewers and confirm it is phrased in the candidate's own words.

## Check execution

Evaluate each rubric check sequentially in the order listed in `rubric.md`:

1. **Grade `plan-fidelity`**:
   - Pass: Diff implements what the plan specifies. Any deviations or deferrals are explicitly documented in `## Deviations` and stated in the PR description.
   - Fail: Diff contains unrequested additions, unannounced flags, structural rewrites, or silent omissions not in `## Deviations`, or description claims fidelity contradicted by the diff.
2. **Grade `decisive-test-evidence`**:
   - Pass: Observable before/after output clearly exercises the fix on the affected path, and required repository checks are executed and reported.
   - Fail: Evidence tests only an unchanged control path, omits before/after transcripts, repo checks were not run, or evidence relies solely on vague claims like "tested locally" or "cargo test passes".
3. **Grade `diff-reviewability`**:
   - Pass: Diff is clean, focused, and free of debugging remnants, dead code, commented-out blocks, formatting churn, or unrelated hunks.
   - Fail: Diff contains debug prints, dead functions, commented-out code, re-indentation churn, or unrelated file changes.
4. **Grade `template-compliance`**:
   - Pass: The PR description satisfies all explicit asks, sections, checklists, and changelog requirements of the repository's PR template or `repo-facts`. Passes automatically if the repo has no PR template or specifies no required sections.
   - Fail: Required sections, checklists, or asks explicitly mandated by that repository's template are visibly omitted, deleted, or left blank.
5. **Grade `ai-disclosure`**:
   - Pass: Stated AI disclosure policy is met with an own-words disclosure, or repo policy does not require AI disclosure.
   - Fail: Repo policy mandates AI disclosure and disclosure is absent or blank.

For any check where required evidence is missing from the package, assign a grade of `fail`. For every check, record a concise, single-line evidence string stating the concrete quote, line, or absence that decided the grade.

## Verdict assembly

Assemble the final evaluation:

1. **Apply the verdict rule**:
   - If all five required checks grade `pass`, the final verdict is `accept`.
   - If any required check grades `fail` or `unclear`, the final verdict is `reject`.
2. **Designate deciding failure check**:
   - When one or more required checks fail, select the first failing required check in rubric order as the deciding failure.
   - Highlight this deciding failure and its evidence in the human-readable summary.
3. **Format output**:
   - Print a readable per-check summary detailing the findings for each check.
   - Conclude with the exact fenced JSON block specified in `CONTRACT.md`. Nothing must follow the JSON block.
