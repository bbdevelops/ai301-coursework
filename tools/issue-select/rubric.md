# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer Activity | "last 5 default-branch commits" or "maintainer first-response sample" | A commit or maintainer response occurred within 90 days. | required |
| Repo Activity | "latest release" or "last push to any branch" | A release or push occurred within 180 days. | required |
| Scope Fits Beginner | Issue body and comment thread | The work asks for a specific fix or feature (not a vague tracking issue or pure support question). Feature requests must be approved/settled by a maintainer or labeled 'good first issue'. It must not have a history of several/multiple abandoned PRs. | required |
| Unclaimed | "this issue: assignees:", "linked PRs:", and Comments | No linked open PRs and no claim comments in the last 30 days. | required |
| Contribution Policy | "contribution policy" line under Repo facts | The policy does not contain an outright ban on AI-generated contributions. | required |


## Verdict rule

Accept if every required check passes. Unclear counts as a fail.
