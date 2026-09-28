# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The repro report's environment line or opening paragraph, read against the issue's stated target platform | The report names at least the OS and the primary tool or library version relevant to the issue. If the report's version differs from the version the issue targets, the difference is acknowledged. | required |
| steps-followable | The repro report's reproduction steps, read from starting state to trigger | A stranger can re-run the steps from a clean start: every command is literal (not pseudocode or "set up the project"), the starting state is named (a clone, a fresh install, a specific file), and no step depends on a private repo, unshared config, or local path another person cannot access. | required |
| behavior-matches-issue | The repro report's output artifact (command output, log excerpt, or screenshot) read against the symptom the issue describes | The artifact shows the same observable behavior the issue reports — the same error message, the same missing output, or the same wrong result. An artifact that shows a different error, a compile-time failure instead of a runtime one, or a graceful rejection instead of the reported crash does not match. | required |
| outcome-honest | The repro report's stated conclusion read against its own artifacts | The conclusion matches what the artifacts actually show. A report that says "confirmed" must have an artifact showing the issue's behavior. A report that says "could not reproduce" must have an artifact showing a real attempt (not a missing or empty run). A report whose conclusion contradicts or overstates its own evidence fails. | required |
| evidence-present | Artifacts in the repro report: output excerpts, logs, screenshots, or inline terminal output | The report contains at least 1 concrete artifact — a pasted command output, a log excerpt, or a screenshot. A report with only prose assertions ("I reproduced it", "the bug happens") and zero artifacts fails. | required |
| claim-specific | The claim comment read against the issue body | The claim names what the commenter intends to investigate or do next, tied to this specific issue (not interchangeable boilerplate). A comment that could be copy-pasted onto any issue without changing a word fails. | required |
| ai-disclosure | The claim comment and repro report read against the "contribution policy" line in the repo-facts block (eval) or the repo's CONTRIBUTING.md and AI policy files (live) | If the repo's stated policy requires disclosure of AI-assisted or AI-generated contributions, the comments include such a disclosure. If the policy sets no disclosure requirement, or no policy exists, this check passes automatically. | required |

## Verdict rule

Accept if every required check passes. Unclear counts as fail.
