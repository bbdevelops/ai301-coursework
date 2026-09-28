# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

**Where it lives:**
- **Eval bundle:** The repro report section, typically the first line or paragraph (often labeled "Environment:" or formatted as an inline list). Cross-reference against the repo-facts block's version and platform information.
- **Live mode:** The student's draft repro comment. Cross-reference against the issue body's stated platform, the repo's README (install/setup section), and the issue thread for any version-specific discussion.

**What good looks like:** The report names at least the OS and the primary tool/library version that the issue concerns. If the reporter's version differs from the version the issue was filed against, the difference is called out explicitly ("issue filed against 3.2.4; I tested on 3.2.5"). A line like "macOS 14.5, HTTPie 3.2.4, Python 3.12.4" is sufficient. An absent environment line, or one that lists only the OS without the relevant tool version, is insufficient.

## Steps

**Where it lives:**
- **Eval bundle:** The repro report section, under steps, commands, or a numbered/bulleted list. Read from the stated starting state through the trigger.
- **Live mode:** The student's draft repro comment, same structure.

**What good looks like:** A stranger with the named environment can follow the steps from a clean starting state (a fresh clone, a clean install, an empty directory) to the trigger without guessing. Every command is literal and copy-pasteable — not pseudocode ("set up the project") or a reference to a private resource ("see my config"). The starting state is explicit: what to install, what to clone, what file to create. Steps that depend on an unshared monorepo, a private config file, or a localhost URL another person cannot access are not followable.

## Behavior shown

**Where it lives:**
- **Eval bundle:** The repro report section's output block, log excerpt, or screenshot reference. Read the artifact against the issue's "Current result" or symptom description in the issue context section.
- **Live mode:** The student's draft repro comment, same. Read the artifact against the live issue body on GitHub.

**What good looks like:** The artifact shows the same observable behavior the issue describes — the same error message, the same missing header, the same crash output, or the same wrong result. A faithful match means the artifact's content corresponds to the issue's symptom, not merely to the same tool. Specifically: an artifact showing a compile error does not match an issue about a runtime crash; an artifact showing a graceful validation message does not match an issue about a panic; an artifact showing correct output does not match an issue about wrong output (unless the report honestly says "could not reproduce" — see Honesty below).

## Honesty

**Where it lives:**
- **Eval bundle:** The repro report's conclusion sentence or final paragraph, read against the artifacts shown in the same report.
- **Live mode:** Same, in the student's draft.

**What good looks like:** The stated conclusion matches what the artifacts actually show. "Confirmed: the bug occurs" is honest when the artifact shows the issue's symptom. "Could not reproduce" is honest when the artifact shows a real attempt that produced different (correct) output, and the report names what differed (environment, steps, or config) rather than just asserting "works for me." A report that says "I verified this" or "guaranteed reproducible" but shows no artifact, or whose artifact shows a different behavior than what is claimed, is dishonest — the conclusion overstates the evidence. The test is: does the evidence support the specific claim made, not whether the tone is confident or tentative.

## Comms

**Where it lives:**
- **Eval bundle:** The candidate claim comment and the candidate repro report, read against the repo-facts block's "contribution policy" line (which includes any AI-use disclosure requirements).
- **Live mode:** The student's draft claim and repro comments, read against the repo's CONTRIBUTING.md, any AI_POLICY.md or AI_USAGE_POLICY.md files, and PR/issue templates that mention AI-use disclosure.

**What good looks like:** The claim comment is specific to this issue — it names what the commenter plans to do or investigate, tied to the issue's actual content. A comment that could be pasted onto any issue without changing a word ("I'd like to work on this, can I be assigned?") is boilerplate and fails the claim-specific check. If the repo's stated policy requires AI-use disclosure, the comments include it; if the policy is silent or permissive without a disclosure requirement, no disclosure is needed. The words are honest about the commenter's standing: a first-time contributor does not claim maintainer-level authority, and promises are limited to what the commenter can actually deliver.
