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

**Environment**: OS: Windows 11. Code state: my fork `bbdevelops/pathreview-ai301-fa26-s3` (forked from `codepath/pathreview-ai301-fa26-s3`), pinned at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`. Python `>=3.11` per `pyproject.toml` (the tool version this doc issue concerns).

**Steps to reproduce**:
```
git clone https://github.com/bbdevelops/pathreview-ai301-fa26-s3.git
cd pathreview-ai301-fa26-s3
git checkout 2f4e82f52efbcfcc57d65b3fa5348672163ca088
grep -n -A3 -E "POST /profiles|POST /reviews" docs/API.md
sed -n '23,30p' api/routes/profiles.py
cat api/schemas/review.py
```

**Observed output**:
```
$ grep -n -A3 -E "POST /profiles|POST /reviews" docs/API.md
18:`POST /profiles` — Create a profile with resume and GitHub username.
19-`GET /profiles/{profile_id}` — Retrieve a profile.
20-`DELETE /profiles/{profile_id}` — Delete a profile and associated data.
21-
--
24:`POST /reviews` — Request a new portfolio review for a profile.
25-`GET /reviews/{review_id}` — Retrieve a completed review.
26-`GET /reviews` — List reviews for the authenticated user (paginated).
27-

$ sed -n '23,30p' api/routes/profiles.py
@router.post("", response_model=ProfileResponse)
async def create_profile_endpoint(
    github_username: str = Form(default=None),
    portfolio_url: str = Form(default=None),
    resume_file: UploadFile = File(default=None),
    current_user: User = Depends(get_current_user),
    db=Depends(get_db),
):

$ cat api/schemas/review.py
class ReviewCreate(BaseModel):
    profile_id: UUID
```

**Expected behavior**: `docs/API.md` should document each endpoint's request body: `POST /profiles` as multipart form data (`github_username`, `portfolio_url`, `resume_file`), and `POST /reviews` as a JSON body matching `ReviewCreate` (`profile_id: UUID`).
**Actual behavior**: The `grep` output above shows `docs/API.md` lists both endpoints with a one-line description and no body schema — confirmed by diffing that against the real handler signature (`profiles.py`) and schema class (`review.py`) pasted above, which is the same gap the issue reports.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Run 1 (2026-09-28T05:17:08Z, graded from a project-local `.claude/skills/repro-check` copy): agreement 20/20 scored items (bar: 18/20: PASS).
- Run 2 (2026-09-28T15:33:10Z, re-run with identical `rubric.md`/`evidence-guide.md` content after relocating the skill to the canonical `~/.claude/skills/repro-check/` install so `--rubric`/`--evidence` point at the same files live mode uses): agreement 19/20 scored items — pkg-09 disagreed (gold `accept`, verdict `reject`, failed `behavior-matches-issue`) — (bar: 18/20: PASS). This is the committed run in `eval-run.txt`.

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
