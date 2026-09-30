# Plan: add request-body schemas for POST /profiles and POST /reviews to docs/API.md

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37

## Diagnosis

`docs/API.md` documents each endpoint with a one-line summary and no
request-body schema. This is the exact gap the Unit-2 reproduction shows:

> ```
> $ grep -n -A3 -E "POST /profiles|POST /reviews" docs/API.md
> 18:`POST /profiles` — Create a profile with resume and GitHub username.
> 19-`GET /profiles/{profile_id}` — Retrieve a profile.
> 20-`DELETE /profiles/{profile_id}` — Delete a profile and associated data.
> 21-
> --
> 24:`POST /reviews` — Request a new portfolio review for a profile.
> 25-`GET /reviews/{review_id}` — Retrieve a completed review.
> 26-`GET /reviews` — List reviews for the authenticated user (paginated).
> 27-
> ```

Neither endpoint's request body is documented anywhere in `docs/API.md`.
Reading the actual handlers confirms what each body should be:

> ```
> $ sed -n '23,30p' api/routes/profiles.py
> @router.post("", response_model=ProfileResponse)
> async def create_profile_endpoint(
>     github_username: str = Form(default=None),
>     portfolio_url: str = Form(default=None),
>     resume_file: UploadFile = File(default=None),
>     current_user: User = Depends(get_current_user),
>     db=Depends(get_db),
> ):
> ```

`POST /profiles` takes `multipart/form-data`, not JSON: `github_username`
and `portfolio_url` as optional form fields, `resume_file` as an optional
file upload. Cross-referencing `api/schemas/profile.py`'s `ProfileCreate`
confirms the field constraints (`github_username` max 255 chars,
`portfolio_url` max 500 chars). The route handler additionally rejects
(422) any `resume_file` whose content type isn't PDF, Markdown, or plain
text.

> ```
> $ cat api/schemas/review.py
> class ReviewCreate(BaseModel):
>     profile_id: UUID
> ```

`POST /reviews` takes a JSON body matching `ReviewCreate`: a single
required `profile_id` (UUID).

## Scope

**In scope:** add a request-body block under each of `POST /profiles` and
`POST /reviews` in `docs/API.md`, documenting each field's name, type,
required/optional status, and one example value.

**Not in scope:**
- No changes to `api/routes/profiles.py`, `api/routes/reviews.py`, or any
  schema file — the code is correct; only the docs are missing.
- No changes to any other endpoint's documentation.
- No OpenAPI/Swagger spec regeneration (the running app's `/docs` and
  `/redoc` already reflect the code; this fix is for the static
  `docs/API.md` reference only, which is what the issue names).

## Files

- `docs/API.md` (only file touched)

## Approach

1. Under the existing `POST /profiles` line, add a "Request body
   (multipart/form-data)" block listing:
   - `github_username` (string, optional, max 255 chars) — example value
   - `portfolio_url` (string, optional, max 500 chars) — example value
   - `resume_file` (file, optional; PDF, Markdown, or plain text only —
     422 if another type) — example filename
2. Under the existing `POST /reviews` line, add a "Request body
   (application/json)" block listing:
   - `profile_id` (UUID, required) — example UUID value
3. Leave the existing one-line endpoint summaries and every other section
   of `docs/API.md` unchanged.

## Test plan

Re-run the Unit-2 repro command before and after the edit:

```
grep -n -A3 -E "POST /profiles|POST /reviews" docs/API.md
```

**Before:** each endpoint line is followed only by the next endpoint's
one-line summary (shown in the Diagnosis section above) — no field names
appear.

**After:** each endpoint line is immediately followed by its new request-body
block, so the same `grep` shows `github_username`, `portfolio_url`, and
`resume_file` under `POST /profiles`, and `profile_id` under `POST /reviews`.

As a second, more decisive check:

```
grep -c -E "resume_file|profile_id" docs/API.md
```

**Before:** `0`. **After:** `>= 2` (one mention per endpoint's new block, at
minimum).

## Risks and unknowns

- Unchecked so far: whether any other doc (`docs/ARCHITECTURE.md`, the
  README) also references these two request bodies and would go stale if
  only `API.md` is updated. To confirm before/while building.
- The interactive docs (Swagger/ReDoc, generated from the FastAPI app
  itself) already show accurate schemas since they read the code directly;
  this plan only fixes the static reference doc the issue names, and that
  distinction is worth a one-line callout in `docs/API.md` itself if it
  isn't already there.
- A classmate's independent live-server testing on this same issue thread
  (comment by MeeTrannn) found that `POST /profiles` currently accepts a
  JSON body silently — it returns `200 OK` with every field discarded,
  rather than rejecting the wrong content type — and that the file-type
  rejection message text doesn't list all three types the code actually
  accepts. Those are real runtime behaviors, not documentation gaps, and
  I have not verified them myself. Documenting the endpoint's actual
  accepted content type (multipart/form-data) as this plan does should
  make that mismatch more visible to a reader, but fixing the handler's
  silent-acceptance behavior or its error text is out of scope for this
  documentation-only change.

## Deviations

The core plan held: one file (`docs/API.md`), two additive request-body
blocks, no route/schema/other-endpoint changes. Two small deviations from
what the plan said, both surfaced by actually running the test plan:

1. **Presentation choice not specified in the plan.** The plan said to "add
   a request-body block" listing field/type/required/example but didn't
   pick a format. I used a markdown table (field, type, required, notes,
   example) rather than a bullet list — more scannable for a reference doc
   with 3+ fields, and the existing `docs/API.md` already uses one earlier
   for nothing else, so this is a new but consistent addition. No scope
   impact: same fields, same file.
2. **The test plan's second assertion was wrong as written.** The plan
   said the combined count `grep -c "resume_file\|profile_id"` would go
   from `0` to `>=2`. Running it before the edit showed the baseline was
   already `2`, not `0` — `profile_id` appears in the pre-existing
   `{profile_id}` path templates on the `GET`/`DELETE /profiles` lines,
   which the plan's diagnosis had read past without noticing. The primary
   assertion (the `grep -n -A3` re-run, showing the new block appear
   immediately after each `POST` line where before there was none) was
   unaffected and remains fully decisive on its own. For the secondary
   count, I substituted `grep -c -E "resume_file|portfolio_url"` — two
   field names that only exist in the new content — which went `0` to `2`
   as intended. See Evidence in `plan-and-implement.md` for both the
   before and after output.
