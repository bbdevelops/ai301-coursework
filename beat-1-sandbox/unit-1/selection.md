# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37

**Verdict output**

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/37",
  "checks": [
    {
      "name": "Maintainer Activity",
      "grade": "pass",
      "evidence": "Most recent commit by @Aburke225 dated September 16, 2026 — 5 days before today, within the 90-day threshold."
    },
    {
      "name": "Repo Activity",
      "grade": "pass",
      "evidence": "Last push to main branch September 16, 2026; repo not archived; within 180-day threshold."
    },
    {
      "name": "Scope Fits Beginner",
      "grade": "pass",
      "evidence": "Bounded doc task: add request-body schemas (fields + examples) for POST /profiles and POST /reviews to docs/API.md; labeled 'good first issue' and 'tier-1'; no comments or abandoned PRs."
    },
    {
      "name": "Unclaimed",
      "grade": "pass",
      "evidence": "Assignees: none; linked PRs: none; zero comments — no claim activity of any kind."
    },
    {
      "name": "Contribution Policy",
      "grade": "pass",
      "evidence": "No CONTRIBUTING.md, AI_POLICY.md, or AI_USAGE_POLICY.md found in the repo; silence passes per rubric."
    }
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

1. Run 1: 17/20 agreement (failed on Scope Fits Beginner)
2. Run 2: 15/20 agreement (failed category floor due to removed policies)
3. Run 3: 19/20 agreement (passed)
4. Run 4: 18/20 agreement (passed, saved to eval-run.txt)

**Issue analysis**

Issue: `issue-15` (zulip/zulip#19589)
Gold label: `reject`
My rubric's decision: `reject`
Reasoning: The issue is a feature request for a Slack-compatible outgoing webhook that was opened in 2021. Despite having a "good first issue" label, it has 97 comments, multiple failed claim attempts, and two closed/unmerged PRs in its history. Our rubric correctly rejects this issue because it has a history of several abandoned PRs, meaning its scope and difficulty are likely far beyond a beginner, despite the friendly label.

**Check rationale**

Check: `| Scope Fits Beginner | Issue body and comment thread | The work asks for a specific fix or feature (not a vague tracking issue or pure support question). Feature requests must be approved/settled by a maintainer or labeled 'good first issue'. It must not have a history of several/multiple abandoned PRs. | required |`

Reasoning: This check ensures that the newcomer takes on a bounded task. Tracking/umbrella issues are too large to tackle in a single PR. Feature requests must be settled by a maintainer; otherwise, a beginner might write code for a design that will be rejected. Crucially, the "history of abandoned PRs" condition prevents beginners from walking into a trap issue that looks easy but has hidden complexities that caused previous contributors to give up.

**Trade-offs**

This check occasionally rejects issues that are technically valid if the maintainer has not explicitly approved the feature request in the comments, even if the feature makes sense. For instance, we initially rejected `issue-01` (Add permanent docs) because it looked like a vague tracking issue due to the many sub-pages it referenced, even though the gold label was accept. However, this trade-off is worth it to protect beginners from taking on unapproved or unbounded scope.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. **Fit**: Issue #37 involves reading Python files (`api/routes/profiles.py` and `api/schemas/review.py`) to extract schemas for documentation. Since my background is heavily Python-based, this directly aligns with my skills and provides a meaningful artifact without being overwhelmingly complex (estimated 2-3 hours).
2. **Weighing factors**: The tool correctly identified that the scope is beginner-friendly and that there is recent maintainer activity. What I had to weigh myself was the learning value: while issue #73 is faster, #37 teaches me more about how the project's data models are structured.
3. **Difficulty in claiming**: Anticipated difficulty is very low. The issue is entirely unclaimed, has no assignee, and the repo has no strict contribution policy against AI assistance.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
