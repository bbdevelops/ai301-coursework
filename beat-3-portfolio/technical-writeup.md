# Rafter-CLI Documentation Contribution

## Overview
**Rafter-CLI** is a command-line interface tool for the Rafter security toolkit. The issue that I chose to contribute to involved creating documentation of the JSON schemas output by the tool. As it stood, agentic users, CI systems, and dashboards would have to run a command, and reverse engineer the output. Through a series of tests and iterations, I worked on generating accurate and detailed documentation that captured the structure and semantics of the JSON output. Eventually after a review by the maintainers I was asked to make a revision, which I completed promptly, resulting in the updated documentation being accepted and merged into the main repository.

Link to the closed PR:
[https://github.com/Raftersecurity/rafter-cli/pull/357](https://github.com/Raftersecurity/rafter-cli/pull/357)

## What happened

After seeing the issue was still open and that it had not been claimed, I decided to take ownership of it and contribute to the documentation effort on October 31. I began by thoroughly analyzing the existing documentation to pinpoint gaps and ambiguities related to the JSON schema output.

Initial claim: [https://github.com/Raftersecurity/rafter-cli/issues/36#issuecomment-6547018178](https://github.com/Raftersecurity/rafter-cli/issues/36#issuecomment-6547018178)
Claim date: October 31, 2026

Initially, I reviewed the existing documentation and identified areas where the JSON schema output was not adequately described. I then created a series of test cases to understand the various structures and data types produced by **Rafter-CLI**. Based on these tests, I drafted comprehensive documentation that included detailed explanations of each field, its expected data type, and any relevant constraints or relationships. 

After submitting my draft, on November 12, the maintainers requested a revision to clarify certain aspects and improve the overall readability. I promptly addressed their feedback, refining the documentation to ensure accuracy and clarity. 

One key change that was highlighted during the review was the changing of the `level` field to `severity` in the documentation.

> `CLI_SPEC.md:127` says each vulnerability has `level`, but as you found, the wire field is `severity`.
>
> — *Rome-1*, November 12, 2026

**Source**: [maintainer review](https://github.com/Raftersecurity/rafter-cli/pull/357#issuecomment-6839843829).

Actual Git diff, original PR head `a70de5e` to revised head `f0510dd`, restricted to `CLI_SPEC.md`:

```diff
diff --git a/shared-docs/CLI_SPEC.md b/shared-docs/CLI_SPEC.md
index 90f912f..9acf69d 100644
--- a/shared-docs/CLI_SPEC.md
+++ b/shared-docs/CLI_SPEC.md
@@ -129,5 +129,5 @@ Retrieve results from a scan.
 - `-h, --help`
 
-**Vulnerability levels (JSON output):** The `level` field on each vulnerability uses SARIF standard values: `"error"`, `"warning"`, or `"note"`.
+**Vulnerability severity (JSON output):** The `severity` field on each vulnerability uses SARIF standard values: `"error"`, `"warning"`, or `"note"`.
```

Also the maintainer asked for fixes to the documentation regarding the presence and alignment of certain fields in the JSON output, specifically `engine_requested`, `engine_used`, and `degraded`.


> Also align how the spec and your table describe `engine_requested`, `engine_used` and `degraded` (the spec says they're always present).
>
> — *Rome-1*, November 12, 2026

```diff
 #### Failed scans
@@ -558,4 +558,8 @@ When `--json` is passed, output is a JSON object to stdout with a `results` arra
 **Top-level field reference:**
 
+`engine_requested`, `engine_used` and `degraded` are always present in the
+JSON result of a one-shot local scan. The current watch-mode writers omit
+these three fields; see [watch output framing](JSON_SCHEMAS.md#watch-output-framing).
+
 | Field | Type | Description |
 |-------|------|-------------|
```

Then on November 14, the maintainer merged the commit: 

```
Rome-1 merged commit d5f56f6 into Raftersecurity:main
```
[https://github.com/Raftersecurity/rafter-cli/pull/357](https://github.com/Raftersecurity/rafter-cli/pull/357)

Additionally, the commit is part of an upcoming new release, version 0.12:

[https://github.com/Raftersecurity/rafter-cli/pull/366](https://github.com/Raftersecurity/rafter-cli/pull/366)

This PR transparently discloses AI assistance: Codex was used for source tracing, drafting, helpers, and evidence collection, while Claude Code handled review and posting checks. Documenting these tools ensures clear attribution across the contribution process.

## Limitations and what's next

JSON schemas will have to be monitored over time, and it is likely that the documentation will need to be updated accordingly to reflect any changes or additions to the schema. This process was rather extensive and reproducing all of this independently might be a challenge, which may pose an issue for future updates. Maybe a more automated or systematic approach to tracking schema changes and updating the documentation could help mitigate this challenge.


Separate from the documentation, we uncovered a bug that the maintainer acknowledged and suggested it be fixed as a different issue:

```text
You also found a real bug: policy export --output crashes on Node with require is not defined. We'll fix that separately. 
```

It's possible that I'll consider attempting to contribute to addressing this bug in the future. To be clear, it was not assigned to me.
