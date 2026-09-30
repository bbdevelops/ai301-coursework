# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

bbdevelops

**Plan comment**

[https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37#issuecomment-5915839729]

Confirmed the gap: `docs/API.md` gives both endpoints a one-line summary with no request body at all (grep output from my repro comment above). Reading the handlers shows what's missing — `POST /profiles` takes `multipart/form-data` (`github_username`, `portfolio_url` as optional form fields, `resume_file` as an optional PDF/Markdown/plain-text upload, from `api/routes/profiles.py` and `ProfileCreate`), and `POST /reviews` takes a JSON body of just `profile_id` (UUID, from `ReviewCreate`).

Plan: add a request-body block under each endpoint in `docs/API.md` with the field names, types, and an example value. I won't touch the route handlers, schemas, or any other endpoint's docs — this is a one-file documentation fix. Test: re-running the grep above should show the new field names directly under each endpoint line, where today it shows none.

Re: the JSON-silently-accepted behavior on `POST /profiles` found upthread — documenting the endpoint's actual multipart content type should make that mismatch visible to readers, but the handler's runtime behavior is out of scope for this doc fix.

---

## Your branch

**Branch**

fix/37-api-request-body-docs

**Evidence**

Before (on `main`, prior to the fix):

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

$ grep -c -E "resume_file|portfolio_url" docs/API.md
0
```

After (on `fix/37-api-request-body-docs`, following the `docs/API.md` edit):

```
$ grep -n -A3 -E "POST /profiles|POST /reviews" docs/API.md
18:`POST /profiles` — Create a profile with resume and GitHub username.
19-
20-Request body (`multipart/form-data`):
21-
--
33:`POST /reviews` — Request a new portfolio review for a profile.
34-
35-Request body (`application/json`):
36-

$ grep -c -E "resume_file|portfolio_url" docs/API.md
2
```

(Note: the plan's original second assertion used `grep -c "resume_file\|profile_id"`,
expecting a `0 -> >=2` change; run before the edit, the baseline was already `2` because
`profile_id` appears in the pre-existing `{profile_id}` path templates. Substituted
`resume_file|portfolio_url` — two field names that only exist in the new content — for a
genuinely decisive `0 -> 2` count. Recorded in `plan.md`'s Deviations.)

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Run 1 (smoke run, `--limit 3`, packages pkg-01/02/03): agreement 3/3 scored items (partial run, no bar verdict — used only to catch template/harness errors before spending on a full run).
- Run 2 (first full run, 20 packages, not saved): agreement 19/20 scored items — pkg-14 disagreed (gold `accept`, verdict `reject`, failed `diagnosis-grounded, stranger-executable`) — (bar: 18/20: PASS), categories: clear-accept 6/7, scope-creep 4/4, thread-convention 2/2, unbuildable 3/3, wrong-cause 4/4.
- Run 3 (confirming full run, 20 packages, `--save-run eval-run.txt`, identical `rubric.md`/`evidence-guide.md`/`procedure.md`): agreement 19/20 scored items — pkg-14 disagreed again (gold `accept`, verdict `reject`, this time failed only `stranger-executable`) — (bar: 18/20: PASS), same category tallies. This is the committed run in `eval-run.txt`.

**Package analysis**

`pkg-14`
- My rubric decided: `reject`
- Gold label said: `accept`
- Why my rubric read it that way: `pkg-14`'s plan names the problem area (`zellij-server`'s client attach/reattach path and `zellij-client`'s terminal query issuance) and says the exact functions will be "pinned in the PR after tracing" — which it says it has already done with `zellij --debug` output, but doesn't quote a single literal file path in the plan itself. My `stranger-executable` check requires "at least one concrete file path," so it failed the check even though the named subsystems are real and the plan is otherwise a strong, honestly-scoped fix (it explicitly defers the untestable Windows variant with reasons, which is exactly the pattern the gold label credits). The gold label reads the crate-level names plus the stated debug trace as concrete enough for a stranger to start from; my check's literal "file path" bar is stricter than that. This is a defensible but real disagreement — the deferred exact-function naming is the same honest-scoping move the eval set rewards elsewhere (e.g. `pkg-09`), but my check can't distinguish "deferred because still tracing it" from "deferred because never looked."

**Check rationale**

Check: `diagnosis-grounded`
Quote: "The stated cause is consistent with every specific fact the repro evidence shows, not just its summary. If the repro evidence contains a control or negative run that isolates a different factor than the plan names (e.g. a run that reproduces the symptom with the plan's blamed component switched off, or fails to reproduce it with the component on), the check fails even if the plan is confident, cites the thread, or is well-written."
Rationale: my group's class activity worked through a sample rubric whose diagnosis check was just "passes if the plan says what causes the bug." Grading `calib-03` with that sample rubric passes a plan that adopts the thread's confident key-binding theory — but the repro evidence's own step 3 (`bat --color=always --paging=never`, no pager in the loop at all, still ~26s) rules out a pager-key-binding cause outright. The sample check never asks the grader to check the stated cause against the evidence's own data points, so a well-written, thread-cited, wrong diagnosis sails through. I rewrote the check to force that comparison explicitly — every repro-evidence fact, not just the summary — specifically naming control/negative runs, because that's exactly the kind of evidence a wrong-cause plan is most likely to contradict without saying so.

**Trade-offs**

`diagnosis-grounded` can only catch a wrong cause when the repro evidence itself records a fact that contradicts it — a control run, a negative case, a version comparison. If a plan's repro evidence is thin and simply never ran a test that would have contradicted the stated cause, a wrong diagnosis with nothing in the package to contradict it passes as "grounded" even though it may still be wrong. This check protects against a diagnosis that's contradicted by the evidence in hand; it does not protect against a diagnosis that's merely under-evidenced. I accepted this gap rather than adding a second, separate "evidence is thorough enough" check, because that would have been a shape/adjective-based check (how much evidence is "enough") of exactly the kind the rubric is supposed to avoid — the eval set didn't surface a package this gap would have flipped, so I left it as a known, stated limitation rather than chasing it.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
