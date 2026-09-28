# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

bbdevelops

---

## Posted upstream

**Claim comment**

[https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37#issuecomment-5864209517]
I'd like to work on this. I plan to add the missing request-body schemas for POST /profiles and POST /reviews to docs/API.md by reading the route handlers in api/routes/profiles.py and the schema definitions in api/schemas/review.py.

**Reproduction comment**

[https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37#issuecomment-5864475853]

**Environment**: OS: Windows 11, Code state: Forked repo at `codepath/pathreview-ai301-fa26-s3` (commit `main`)

**Steps to reproduce**:
1. Open `docs/API.md` and observe the descriptions for `POST /profiles` and `POST /reviews`. They list endpoints but do not contain request body documentation.
2. Open `api/routes/profiles.py` and observe `POST /profiles` expects `github_username`, `portfolio_url` and `resume_file` as Form data (multipart).
3. Open `api/schemas/review.py` and observe `POST /reviews` expects a JSON body defined by `ReviewCreate` (which requires `profile_id: UUID`).

**Expected behavior**: The `docs/API.md` file should include the required form data and JSON body schemas.
**Actual behavior**: `docs/API.md` is missing the request body definitions, making the API reference incomplete for these endpoints as reported in the issue.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Run 1: agreement: 20/20 scored items (bar: 18/20: PASS)

**Package analysis**

**pkg-20**
- My rubric decided: `reject`
- Gold label said: `reject`
- Why my rubric read it that way: The `ghostty` repo policy explicitly requires disclosure of AI usage. The `pkg-20` candidate claim and repro comments do not contain any AI disclosure statements, so the `ai-disclosure` check failed, resulting in a `reject` verdict.

**Check rationale**

Check: `steps-followable`
Quote: "A stranger can re-run the steps from a clean start: every command is literal (not pseudocode or "set up the project"), the starting state is named (a clone, a fresh install, a specific file), and no step depends on a private repo, unshared config, or local path another person cannot access."
Rationale: I worded it this way to explicitly require literal commands and a named starting state, rejecting vague instructions like "set up the project". This is because a stranger reading the report might not know the undocumented project setup steps, making vague instructions un-runnable.

**Trade-offs**

For the `steps-followable` check, explicitly requiring literal commands (and rejecting "set up the project") means we might reject a perfectly valid bug report from an expert user who skips standard setup steps (like `npm install`). While an expert maintainer could still reproduce the bug, this strict requirement ensures the reproduction is universally accessible.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
