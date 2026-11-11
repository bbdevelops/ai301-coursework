# Contribution: docs: document JSON output schemas in shared-docs/

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]

**Student:** Brian Brown

**GitHub Username:** bbdevelops

**Issue:** [Raftersecurity/rafter-cli #36](https://github.com/Raftersecurity/rafter-cli/issues/36)

**Pull Request:** [Raftersecurity/rafter-cli #357](https://github.com/Raftersecurity/rafter-cli/pull/357)

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Expanded issue-scout with a written search strategy**

For the October 21, 2026 scans, I used issue-scout with five GitHub queries tied to my Python, JavaScript, and TypeScript profile, filtering by assignees, recency, and comment count before grading the top five. The saved scan accepted all five survivors, but the ranking favored just-filed issues and concentrated candidates under one owner; later direct grades also exposed requests whose work already existed on main. I used direct URL grading to inspect Rafter candidates and logged proposed changes, including a per-owner cap and checking the remaining work, in scan-notes.md.

**Unit 6: Consolidated my voice guide, installed the posting guard, and added local repository memory**

I consolidated the voice guides from my earlier tools into one canonical guide, added rules for claims, questions, and pings, and installed a voice guard that checks outgoing posts through Claude Code. The installed scopes still contained classroom rules, and my original stability question was too broad because CLI_SPEC.md already names some stable contracts; I replaced the scopes, clarified my progress-update rule, and revised the question before posting. A fresh-session wiring test stopped the bodyless command as expected, and the guard recorded a pass for my actual claim. I also added a focused CLAUDE.local.md with the relevant output handlers, repository policies, and setup limitations, and excluded it through Git's local exclude file so it stays out of the upstream contribution.

**Unit 7: Passed the branch ship-gate with explicit scope and test evidence**

I installed the ship-gate and confirmed both hooks stop a bodyless PR-help attempt, then wrote a manifest with the build and selected Node/Python checks plus dated native-Windows exclusions. Separate unchanged full Linux suites passed 2,505 Node tests and 2,047 Python tests, with optional/live-API skips disclosed. The gate's size limits would omit recent evidence and the end of the documentation diff, so I added a current evidence overview and the exact diff continuation while preserving the full historical transcripts and leaving the gate and rubric unchanged. On November 10 the committed initial contribution passed all three manifest checks and all five PR-precheck checks on the first attempt; optional wording observations remain for the separate voice-guard review, and nothing was pushed or opened during this step.

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I selected Rafter #36 from the CodePath AI301 Candidate Issues site and used issue-scout to compare it with two other Rafter issues. It fit my current skill range and ability to understand the problem, and it seemed feasible within the available time. I want to learn how to trace JSON outputs into accurate documentation and practice the upstream contribution workflow. I am holding only this issue on the Candidate Issues site.

The regrade accepted #36 with an ambitious difficulty note. The deliverable is identifiable, but the request to label fields as guaranteed stable needs maintainer guidance; I raised that question in my claim before implementation. Replacing Scope Fits Beginner with scope-feasible helped separate whether the work is identifiable from how difficult it may be. The scout also caught that #23, accepted in an earlier run, now has another contributor's claim. That showed why an earlier acceptance does not reserve an issue: I still need to check the full thread before posting. The issue's command list is old, so I will also compare it with the current implementations rather than assume every example remains valid.

**Claim:** [GitHub claim comment](https://github.com/Raftersecurity/rafter-cli/issues/36#issuecomment-6547018178), posted 2026-10-31 as bbdevelops through Claude Code with a voice-guard hook pass.

**Next upstream update:** findings or a blocker by November 3, 2026.

**Toolkit**

- Tool: issue-scout in direct mode, grading Rafter #36, #32, and #23 with my patched rubric.
- What it produced: #36 and #32 were accepted; #23 was rejected on Unclaimed. #36's ambitious note identified field-stability guarantees as a question for the maintainer.
- Difficulties: earlier acceptances could go stale, and the issue's old command list and unspecified stability guarantees still needed investigation beyond the accept/reject verdict.
- What changed: replaced Scope Fits Beginner with the staff scope-feasible row and added the difficulty note and dated patch record. Difficulty now informs my choice without changing the verdict or fenced JSON, and is skipped in eval mode. The full regrade read-out was saved for the later claim checks.

---

## Understanding the Issue

**Problem Description**

Tool integrators need one current JSON output reference for Rafter. The requested `shared-docs/JSON_SCHEMAS.md` is missing at the tested revision, so readers must combine scattered CLI_SPEC sections with the Node and Python output handlers.

**Expected Behavior**

The shared docs should provide supported command spellings, actual JSON examples, field descriptions and types, required/optional conditions, runtime variants, and sourced stability notes. Aliases, audit JSONL, MCP envelopes, and non-JSON format boundaries should be clear. Backend examples need real evidence before the complete reference is ready for a PR.

**Current Behavior**

The pinned-source file lookup returns no JSON_SCHEMAS.md, but CLI_SPEC already documents several JSON shapes. Local reproduction also found that `agent audit --json` is unsupported, fresh config defaults differ across runtimes, and only the Claude policy export is JSON. The refreshed issue still contains only my claim; there is no maintainer response to the stability question yet.

**Affected Components**

The upstream edits are limited to new `shared-docs/JSON_SCHEMAS.md` and a cross-reference in `shared-docs/CLI_SPEC.md`. Their source material is the paired scan/config/policy command serializers, audit loggers, MCP servers, remaining JSON command handlers, and backend pass-through clients. Runtime code and the existing test assertions are outside this documentation change.

**Toolkit**

- Tool: Codex-assisted source inspection and read-only Git/GitHub checks against the pinned checkout and complete current issue thread.
- What it produced: a command-family inventory separating local output writers from backend pass-through responses, plus a repeated missing-file check.
- Difficulties: the issue's command list is older than the implementation, config shapes differ between runtimes, and API clients do not define complete backend response schemas.
- What changed: included default JSON and format-selected JSON in the planned coverage, kept unsupported/non-JSON boundaries explicit, and retained backend evidence and unspecified stability as release gates.

---

## Reproduction Process

**Environment Setup**

The setup and reproduction captures below are the original October 31, 2026 checks on 0.11.5. The current 0.11.7 working target and its separate validation are recorded in Solution Approach and the November 3 Implementation Notes; the earlier runs have not been relabeled.

Windows 11 (build 10.0.26300), Node v24.16.0, pnpm 10.34.9, and Python 3.13.2. Both Rafter implementations report 0.11.5. The Node MCP SDK is 1.32.1; the isolated Python environment uses mcp 1.30.0, typer 0.27.3, click 8.1.8, and pytest 8.4.2. Node dependencies came from the frozen pnpm lock; all 49 Python lock versions match the installed environment.

The tested source is `424d827229860dca52dc7d4494468d74c5a820a2`, matching upstream main at the preflight check. I tested an isolated clone at this revision. The public-clone commands below produce the same source.

I used AI assistance for setup, source inspection, and drafting; the outputs below are from actual commands. Node installation and TypeScript compilation succeeded. Windows path handling and a pywin32 cache rename interrupted uv installation; existing pip 26.2.1 successfully installed the same lock-constrained dependencies into the absolute virtual-environment directory.

For the missing-file check, Git and the pinned source are sufficient. To reproduce the additional CLI observations, start in a **fresh empty directory** with Git, Node/npm, Python/pip, and uv available and run this PowerShell setup:

```powershell
git clone https://github.com/Raftersecurity/rafter-cli.git source
git -C source checkout --detach 424d827229860dca52dc7d4494468d74c5a820a2

npm install --prefix tools --no-save --package-lock=false --ignore-scripts --no-audit --no-fund --registry=https://registry.npmjs.org --cache cache/npm pnpm@10.34.9
Push-Location source
node ../tools/node_modules/pnpm/bin/pnpm.cjs --filter @rafter-security/cli install --frozen-lockfile --ignore-scripts --store-dir ../cache/pnpm --registry=https://registry.npmjs.org
node ../tools/node_modules/pnpm/bin/pnpm.cjs --dir node run build
Pop-Location

uv venv python-env --python 3.13 --no-python-downloads --cache-dir cache/uv
@'
import tomllib
from pathlib import Path
lock = tomllib.loads(Path("source/python/poetry.lock").read_text(encoding="utf-8"))
Path("python-lock-constraints.txt").write_text(
    "\n".join(p["name"] + "==" + p["version"] for p in lock["package"]) + "\n",
    encoding="utf-8",
)
'@ | python -X utf8 -
$reproEnvironment = (Resolve-Path -LiteralPath python-env).Path
python -m pip --python "$reproEnvironment" install --index-url https://pypi.org/simple --cache-dir cache/pip --constraint python-lock-constraints.txt --editable source/python pytest==8.4.2 pytest-mock==3.17.0 pytest-asyncio==0.24.0
```

**Steps to Reproduce**

1. Check the exact source revision and the requested documentation file:

```powershell
git -C source rev-parse HEAD
git -C source ls-tree --name-only HEAD -- shared-docs/JSON_SCHEMAS.md
git -C source ls-tree --name-only HEAD -- shared-docs/
```

The revision is `424d827229860dca52dc7d4494468d74c5a820a2`. The specific-file query exits 0 with no output; the directory listing contains CLI_SPEC.md and other documents, but no JSON_SCHEMAS.md.

2. Check the existing schema documentation rather than assuming it is absent:

```powershell
git -C source grep -n -e "#### JSON Output" -e "Audit Log Schema" -e "Top-level field reference" HEAD -- shared-docs/CLI_SPEC.md
```

This finds JSON output sections and field descriptions at lines 380, 521, 554, and 887. The missing consolidated reference is reproducible, but the issue's older description of CLI_SPEC.md is partly outdated.

3. After the optional runtime setup above, run the same offline diagnostic matrix. This self-contained script creates a clean fixture and an obviously fake credential fixture, runs both implementations from the same source, and uses child-only scratch profiles. It does not change the parent shell's home or profile, install integrations, or call the remote backend.

```powershell
@'
import json
import os
from pathlib import Path
import subprocess

root = Path.cwd()
fixtures = root / "fixtures"
fixtures.mkdir(exist_ok=True)
(fixtures / "clean.txt").write_text("A minimal Unit 6 fixture with no credentials.\n", encoding="utf-8")
(fixtures / "finding.txt").write_text(
    "aws_access_key_id = " + "AKIA" + "IOSFODNN7ABCDEFG" + "\n", encoding="utf-8"
)
implementations = {
    "node": ["node", str(root / "source/node/dist/index.js")],
    "python": [str(root / "python-env/Scripts/python.exe"), "-X", "utf8", "-m", "rafter_cli"],
}
for runtime, base in implementations.items():
    profile = root / "state" / runtime
    profile.mkdir(parents=True, exist_ok=True)
    child = dict(os.environ)
    child.update({
        "USERPROFILE": str(profile), "HOME": str(profile),
        "APPDATA": str(profile / "AppData/Roaming"),
        "LOCALAPPDATA": str(profile / "AppData/Local"),
        "NO_COLOR": "1", "TERM": "dumb",
        "PYTHONNOUSERSITE": "1", "PYTHONDONTWRITEBYTECODE": "1",
        "DO_NOT_TRACK": "1",
    })
    child.pop("PYTHONPATH", None)
    for key in list(child):
        if key.startswith("RAFTER_"):
            del child[key]
    child["RAFTER_DISABLE_AUTO_UPDATE"] = "1"
    child["RAFTER_TELEMETRY"] = "0"
    cases = [("version", ["--version"])]
    for label, prefix in (
        ("secrets", ["secrets"]),
        ("agent-scan", ["agent", "scan"]),
        ("scan-local", ["scan", "local"]),
    ):
        for fixture in ("clean", "finding"):
            cases.append((label + "-" + fixture, prefix + [
                str(fixtures / (fixture + ".txt")),
                "--json", "--engine", "patterns", "--no-auto-update",
            ]))
    cases += [
        ("audit-json-unsupported", ["agent", "audit", "--json"]),
        ("config-show", ["agent", "config", "show"]),
        ("policy-claude", ["policy", "export", "--format", "claude"]),
        ("policy-codex", ["policy", "export", "--format", "codex"]),
    ]
    for name, arguments in cases:
        result = subprocess.run(
            base + arguments, cwd=root, env=child, capture_output=True,
            text=True, encoding="utf-8", errors="replace", timeout=45,
        )
        print(runtime, name, "exit", result.returncode)
        print("stdout:", result.stdout)
        print("stderr:", result.stderr)
'@ | python -X utf8 -
```

**Reproduction Evidence**

**Commit showing reproduction:** none. No reproduction or fix commit has been made.

**Source commit:** [upstream 424d827](https://github.com/Raftersecurity/rafter-cli/commit/424d827229860dca52dc7d4494468d74c5a820a2).

The requested-file query returned an empty stdout and exit 0. The actual directory listing was:

```text
shared-docs/CLI_SPEC.md
shared-docs/CONFIG.md
shared-docs/DOCS_SYNC_CHECKLIST.md
shared-docs/PLATFORM_PARITY_AUDIT.md
shared-docs/SHOW_HN_DRAFT.md
shared-docs/proposals
shared-docs/usage-counters.json
```

The schema-documentation search returned:

```text
HEAD:shared-docs/CLI_SPEC.md:380:#### JSON Output (`--json`)
HEAD:shared-docs/CLI_SPEC.md:521:#### JSON Output (`--json`)
HEAD:shared-docs/CLI_SPEC.md:554:**Top-level field reference:**
HEAD:shared-docs/CLI_SPEC.md:887:#### Audit Log Schema
```

All 22 runtime invocations completed. Nine diagnostic checks passed: version agreement, scan JSON parsing, scan metadata, clean-scan exit codes, finding-scan exit codes, audit-option rejection, config JSON, Claude policy JSON, and Codex policy TOML. The table groups these runs by command:

| Observation | Node | Python |
|---|---|---|
| CLI version | 0.11.5, exit 0 | 0.11.5, exit 0 |
| Clean fixture, each of the three scan spellings | JSON with empty results, exit 0 | JSON with empty results, exit 0 |
| Fake-key fixture, each scan spelling | JSON with a redacted finding, exit 1 | JSON with a redacted finding, exit 1 |
| agent audit --json | Unknown option, exit 1 | No such option, exit 2 |
| agent config show | JSON, exit 0 | JSON, exit 0 |
| policy export --format claude | JSON with hooks, exit 0 | JSON with hooks, exit 0 |
| policy export --format codex | TOML, exit 0 | TOML, exit 0 |

For the six scan fixture/spelling pairs, the observed JSON objects matched across runtimes. A complete clean-scan stdout sample was:

```json
{
  "_note": "Local-only scan: pattern-based detection without agentic-intelligence triage. Findings have not been evaluated for context (public exposure, key validity, deployment environment). Investigate each before acting; do not dismiss. Run 'rafter run' for backend agentic analysis.",
  "scan_mode": "local",
  "triage_applied": false,
  "results": [],
  "engine_requested": "patterns",
  "engine_used": "patterns",
  "degraded": false
}
```

The fake-key case returned a match with pattern `AWS Access Key ID`, line 1, column 21, and redacted value `AKIA************DEFG`. Exit 1 means findings, not a crash.

The fresh-profile config observations differ: Node uses keys such as `riskLevel` and `commandPolicy`; Python uses `risk_level` and `command_policy` and includes additional default sections. Both return JSON, but the documentation must account for observed runtime variants rather than assume identical config schemas. No runtime fix was attempted.

**Conclusion:** confirmed that the requested consolidated reference is missing at the tested revision. Existing CLI_SPEC.md already covers several shapes, so the remaining work is consolidation and accurate current coverage, not a claim that all JSON documentation is absent. The unsupported audit option is evidence of stale issue guidance, not a new runtime defect being claimed here.

**Limits at the Unit 6 reproduction checkpoint:** no live authenticated backend scan or `rafter get` request was run. MCP tool payloads and audit JSONL storage were inspected in source/specs, not exercised through a live MCP session or audit-log test. No project-wide test suite was run; the Node build and the 22 CLI diagnostics are the executed checks. Field-stability guarantees still need maintainer guidance, already requested in the claim.

**Unit 7 baseline update (October 31, 2026):** the isolated checkout remains pinned to the same source. The Node build passed, while the full serial Windows Node suite reported 2152 passed, 304 failed, and 20 skipped. Native Windows pytest failed collection on `os.geteuid()`; a continuation stalled in MCP stdio/Git, and a separate run explicitly omitting that file reported 1825 passed, 89 failed, 12 skipped, and the same collection error. Selected regression groups passed 19 Node and 65 Python tests. After explicit setup approval, the single unchanged permission test passed in Ubuntu WSL as UID 1000: 1 passed, 0 skipped. These are baseline findings, not completed schema verification or a full-suite pass; live backend examples and the planned local MCP captures remain pending.

**Toolkit**

- Tool: repro-check in Claude Code, grading the claim and reproduction together in full-package live mode; a scoped setup and diagnostic runner collected the evidence.
- What it produced: acceptance on all seven required checks, backed by the pinned source, missing-reference output, and 22 offline CLI invocations with nine diagnostic checks passing.
- Difficulties: Windows path/cache errors interrupted Python setup; stale issue commands and differing fresh-profile config fields needed qualification. The first accepted grade also flagged local bookkeeping and an unclear distinction between command runs and checks.
- What changed: used existing pip against the absolute local environment with the same lock constraints, documented current command/output variants, removed local bookkeeping from the report, and clarified all nine checks. The final report passed a second actual Claude Code grade. Authenticated backend and live MCP behavior remain source-only coverage.

---

## Solution Approach

**Analysis**

Issue: https://github.com/Raftersecurity/rafter-cli/issues/36. The working target is Rafter CLI 0.11.7 at `1ebad941815d91d45d7befe3295d15f23a8b05ad`. The user fast-forwarded the contribution checkout to this revision on November 3, 2026. Earlier reproduction/examples remain explicitly tied to 0.11.5 at `424d827229860dca52dc7d4494468d74c5a820a2`. This is a documentation gap: output contracts are spread across paired serializers and `shared-docs/CLI_SPEC.md`, while the requested consolidated `shared-docs/JSON_SCHEMAS.md` is absent from the committed upstream tree. Our uncommitted reference now contains 54 capture-backed examples. This initial contribution addresses the documented subset of that gap; changing serializers or adding the obsolete audit flag would change the problem being solved.

The issue thread was refreshed on November 3, 2026. It contains only my claim as `bbdevelops`, with no maintainer response, competing plan, or linked work. My posted claim is https://github.com/Raftersecurity/rafter-cli/issues/36#issuecomment-6547018178. It reports the renamed scan aliases and existing CLI_SPEC shapes, asks about field stability, and discloses AI assistance. There is no separate posted reproduction report. The following additional reproduction evidence is local, quoted here so the plan does not depend on a grader finding other working files. The original reproduction and full-suite counts below are historical 0.11.5 evidence, not fresh 0.11.7 results:

- `git rev-parse HEAD` reports `424d827229860dca52dc7d4494468d74c5a820a2`. `git ls-tree --name-only HEAD -- shared-docs/JSON_SCHEMAS.md` exits 0 with empty stdout. A new committed-tree lookup at `1ebad941815d91d45d7befe3295d15f23a8b05ad` also exits 0 with no path returned; the working-tree draft is separate from that HEAD lookup.
- `git ls-tree --name-only HEAD -- shared-docs/` lists `CLI_SPEC.md`, `CONFIG.md`, `DOCS_SYNC_CHECKLIST.md`, `PLATFORM_PARITY_AUDIT.md`, `SHOW_HN_DRAFT.md`, `proposals`, and `usage-counters.json`; it does not list `JSON_SCHEMAS.md`.
- Searching the spec finds JSON Output sections at lines 380 and 521, a top-level field reference at 554, and Audit Log Schema at 887. Therefore the diagnosis is missing consolidation/current coverage, not the absence of all JSON documentation.
- The prior reproduction ran 22 actual offline CLI invocations across both implementations, with nine diagnostic checks passing. Both versions were 0.11.5. For each of `secrets`, `agent scan`, and `scan local`, a clean fixture returned parseable JSON and exit 0; an obviously fake AWS-key fixture returned a redacted finding and exit 1. The six scan fixture/spelling pairs matched across runtimes. Exit 1 with findings is expected behavior.
- `agent audit --json` was rejected: Node exit 1, Python exit 2. Document actual audit JSONL storage and MCP reads; do not present this unsupported spelling as executable.
- `agent config show` emitted JSON in both runtimes, but Node defaults include `riskLevel` and `commandPolicy`, while Python uses `risk_level` and `command_policy` and has additional default sections. Describe variants rather than silently normalizing them.
- `policy export --format claude` emitted JSON with hooks in both runtimes. The Codex format emitted TOML, so it is a format boundary, not another JSON example.
- Those reproduction runs did not exercise authenticated backend responses, live MCP calls, or audit JSONL generation. They do not support claiming those examples have been verified.
- Subsequent Step 3 baseline: the Windows Node build passed; the full serial Node suite had 2152 passed, 304 failed, and 20 skipped. Native Windows pytest failed collection on `os.geteuid()`. A diagnostic continuation stalled in MCP stdio/Git and was stopped; a separate continuation explicitly omitting that file had 1825 passed, 89 failed, 12 skipped, and the collection error. Selected Node/Python regression files passed 19/65 tests. In a separately approved Ubuntu WSL environment, the unchanged Unix permission test passed as UID 1000, with 1 passed and 0 skipped. These facts establish baseline limitations, not a passing full suite or a JSON documentation regression.

**November 3 source refresh evidence.** Upstream moved by 11 commits to 0.11.7. The user updated both original and contribution checkouts; this plan refresh preserves the original 0.11.5 captures instead of relabeling them. The dependency lockfiles did not change. Refreshing only the existing editable package with `--no-deps` changed the Python distribution metadata from 0.11.5 to 0.11.7; all 49 locked package versions still match. Both actual CLIs now report 0.11.7, the Node build passes, and the selected regression files pass **19 Node and 82 Python tests**, without skips. These are selected groups, not full suites.

The counter command is now `counters show --json`, with sources `node/src/commands/counters.ts` / `python/rafter_cli/commands/counters.py`; the child-process setting is `RAFTER_USAGE_COUNTERS`. Both runtimes' `counters --help` succeeds. Node's `telemetry --help` falls back to root help, so that help exit code does not establish an old-command alias; source registration and current command help determine the name. Project-policy key precedence and built-in risk rules also changed upstream. The existing core scan/config/audit/policy writers inspected for Step 5 have no changes in the compared files, except that the Python agent module has upstream help-string edits and default config draws from the revised risk rules. Reconcile and recapture against the selected new source before calling the final examples current-version verification.

The new partial reference contains 16 actual 0.11.5 examples from 78 invocations. Its 23 provenance/JSON/field/link checks and seven negative controls remain evidence for those captured inputs. The reference must label the current working target separately from the original capture revision. Do not claim that a source update or a passing plan-check itself reran those examples.

The source locations to reconcile with the spec are:

| Output family | Node source | Python source |
|---|---|---|
| Local scan wrapper and aliases | `node/src/commands/agent/scan.ts` (`outputScanResults`); `node/src/commands/scan/` registrations | `python/rafter_cli/commands/agent.py` (`_output_scan_results`); `commands/scan.py` registrations |
| Audit JSONL events | `node/src/core/audit-logger.ts` (`AuditLogger`) | `python/rafter_cli/core/audit_logger.py` (`AuditLogger`) |
| Config and policy export | `node/src/commands/agent/config.ts`; `node/src/commands/policy/export.ts` (`generateClaudeConfig`) | `python/rafter_cli/commands/agent.py` (`config_show`, `config_get`); `commands/policy.py` (`_generate_claude_config`) |
| MCP tools and resources | `node/src/commands/mcp/server.ts` (registrations, `textResult`, `errorResult`) | `python/rafter_cli/commands/mcp_server.py` (FastMCP registrations and `handle_*` functions) |
| Additional local JSON | `node/src/commands/agent/{status,verify,list,baseline,audit-skill}.ts`; `commands/skill/{list,review}.ts`; `commands/docs/{list,show}.ts`; `commands/gates.ts`; `commands/counters.ts`; `commands/hook/{pretool,posttool}.ts` | `python/rafter_cli/commands/{agent,skill,docs,gates,counters,hook}.py` |
| Backend pass-through output | `node/src/commands/backend/{run,get,usage,scan-status}.ts`; `commands/sites/*.ts`; `utils/api.ts` | `python/rafter_cli/commands/{backend,sites}.py`; `utils/api.py` |

Local field types and conditions come from these writers plus actual captures. Backend clients often print an opaque server object; their serializers alone cannot establish complete server schemas. For example, the spec's backend `level` and the issue-builder's `severity` with legacy `level` fallback require authoritative server evidence, not a guessed rename.

**Current evidence, November 10, 2026.** The 16 earlier examples were replayed on 0.11.7, and the real local CLI/hook/MCP interval brought the local total to 48. One separately authorized Fast scan supplied six more examples: submission, queued/processing status, completed results and quota. Python run/get and Node get returned identical JSON for that one result, with 73 untriaged findings and exit 0; this is successful retrieval, not a clean assessment. No allowance remains, and no new scan is part of this scope. The documentation checker passes all eight top-level checks, with 54 parseable examples, 30 local-output checks and nine backend checks. Saved negative controls reject malformed, incomplete or capture-inconsistent documentation. Full unchanged Linux suites pass: Python 2,047 passed/11 skipped on November 3 and Node 2,505 passed/16 skipped on November 10. Native Windows failures remain disclosed. Fresh public issue/thread reads on November 10 show only my claim and progress update, with no maintainer response or competing plan. Both remotes and local main match the tested source pin.

**Proposed Solution**

Submit an initial Markdown output reference for the command families supported by the existing real captures. The included scope is local scans and supported aliases, audit JSONL, config show/object-valued get, Claude policy export, status/verify/component and baseline output, skill/docs/gates/counters output, hook protocols, watch framing, seven local MCP tools and three resources, plus the observed hosted Fast run/get/usage responses. Each included section gives the invocation, output channel/format and exit behavior, captured examples, field paths/types/meaning/presence conditions, runtime differences, and stability/source notes. Preserve the 54 examples and their provenance; optional or unobserved branches stay labeled as source-traced rather than captured successes.

Use `shared-docs/CLI_SPEC.md` as the canonical behavior reference and retain its short Overview link to the new document. Preserve existing guarantees, including exit-code semantics and the stated counters-report key order. Mark other field stability as **unspecified pending maintainer guidance**. An observed payload is not a compatibility promise, and unanswered stability guidance does not require inventing one.

The upstream patch stays limited to new `shared-docs/JSON_SCHEMAS.md` and the cross-reference in `shared-docs/CLI_SPEC.md`. Runtime code, flags, API behavior, versions, dependencies, configuration defaults, installed integrations, repository tests and unrelated guides remain outside the patch. This is a Markdown field reference with examples, not a formal JSON Schema implementation. SARIF, TOML, text, generated config artifacts, outbound request/webhook bodies and JSON inputs remain format boundaries or links to existing specs.

**Explicitly deferred:** all four Sites CLI commands, all four Sites MCP tools, unobserved backend success/empty/partial/failure variants, optional-engine success branches and new field-stability guarantees. Keep these gaps in the coverage inventory and Pending coverage section. Complete response shapes require real authorized captures and authoritative backend definitions; existing mock tests cannot supply that evidence. No new scan, Site creation, Site scan, engine installation or global integration is authorized. The one-scan result and all older evidence are reused unchanged.

This initial contribution does not claim to finish every requirement in issue #36. Use **Related to #36** in the PR description instead of an automatic-closing Fixes line. The assignment literally requests `Fixes #36`; record this intentional discrepancy and its reason in the story rather than asserting completion to satisfy that wording. The user has chosen to proceed without a maintainer reply and accept review or rejection on the submitted scope. Maintainer silence is not approval. The previous requirement to wait for complete backend coverage and a response is superseded; keep the agreed check-ins between the remaining assignment steps.

**Implementation Plan**

1. **Make the reference boundary explicit.** Add a short initial-contribution scope note to `shared-docs/JSON_SCHEMAS.md`, preserving all 54 captured JSON/JSONL examples, field tables, differences, links and guarantees. Retain the pending Sites CLI/MCP inventory and unobserved-branch limitations. Keep the planned Overview link in `shared-docs/CLI_SPEC.md`; make no runtime or repository-test edits.
2. **Verify the documented subset.** Run the existing local documentation checker against the revised working tree. It must fail against the pinned committed-before tree because the reference is absent, and pass afterward only when the reference exists, the Overview link resolves and every included example/field table matches real paired-runtime capture provenance. Preserve the earlier malformed JSON, broken-link, omitted-field and changed-capture negative controls. A full repository test pass cannot substitute for this documentation-specific outcome. Save the current result alongside the earlier evidence; do not relabel old tests as fresh runs.
3. **Synchronize and recheck the scope change.** Copy this Solution Approach exactly into the story, update the local `plan-comment.md`, PR title/description and manifest narrative, and add dated Implementation Notes explaining the deferred coverage and non-closing issue reference. Rerun the installed Claude plan-check in live mode on the full revised package. Keep the plan comment local, as the assignment requires. The PR description will disclose the narrower scope; no new public comment is part of this checkpoint. Stop for review after the grade.
4. **Review and commit the bounded patch.** At the next agreed checkpoint, inspect the diff and stage only `shared-docs/JSON_SCHEMAS.md` and `shared-docs/CLI_SPEC.md`. Make a descriptive `docs:` commit with the required AI co-author trailer. Keep plans, captures, helpers, credentials, test evidence and PR drafts out of upstream commits. Verify the committed diff against `upstream/main` contains just those two documentation files. Stop for review.
5. **Run Step 10, then the remaining publication steps.** Run the installed ship-gate with the saved exact title, `pr_draft.md` and explicit `--base upstream/main`. Its three included manifest checks remain the build, selected 19 Node tests and 82 Python tests; retain the dated native-Windows exclusions and the two passing full Linux baselines with their skips. Address actual gate findings and record the result. Pushing the branch and opening the PR follow as their own agreed assignment checkpoints. A maintainer response is not a prerequisite to that honest initial submission; the gate result and the user's review checkpoints still apply.

**Recorded approach changes.** The November 3 revision updated the source/counters naming and preserved old-version evidence; that package was accepted by plan-check. On November 10 the user explicitly chose a verified initial contribution with Sites deferred, rather than waiting indefinitely for full backend access or a maintainer response. This revision records that narrower scope in the plan and story before committing or publishing it. The two-document patch, actual-output standard and existing stability guarantees are unchanged. Claude's new grade is recorded separately; prior acceptance is not claimed as acceptance of this revision.

**Toolkit**

- Tool: the installed plan-check in Claude Code, applying my live scope, six-check rubric, evidence guide, procedure, and canonical voice guide to the local plan and draft comment.
- What it produced: an actual Claude Code accept verdict with all six required checks passing on October 31, 2026. The grade anchored the diagnosis in the missing reference and the existing partial CLI_SPEC coverage; no plan revision was required for acceptance. After the user pulled 0.11.7, I revised the source/counters/evidence references and the November 3 grade also accepted all six checks. The November 10 live regrade accepted the revised initial-contribution package on all six checks, after reading the current issue/thread; no maintainer direction or competing plan was present.
- Difficulties: the grader noted that the detailed reproduction facts are local quotations, not a separate posted report, and that its procedure has no read-order rule for evidence embedded in the plan. It accepted the package with those limits recorded. Full backend schemas and stability promises cannot be inferred from local serializers. The latest grade also noted that the checker/capture tooling is local, the timeline output was truncated, and an optional compound shell read was denied; its accept verdict does not establish public evidence or a voice-guard pass.
- What changed: recorded the original two-file documentation scope and evidence gates, then revised the plan on November 10 for an initial contribution with Sites and unobserved backend variants deferred. The user chose to proceed without a maintainer response. The current plan and PR use Related to #36 rather than claiming full completion; the plan comment stays local. Claude accepted the revised package on all six checks, with its evidence and voice-guide qualifications preserved separately.

---

## Testing Strategy

**2026-11-09 — Assignment Step 8.** This is a documentation fix: the observable before/after is the missing reference becoming a usable, linked reference. I tested the committed 0.11.7 source at `1ebad941815d91d45d7befe3295d15f23a8b05ad`, then the uncommitted working tree on `docs/36-json-schemas`. I used the pinned commit rather than this clone's older local main. A Git tree query returned no JSON_SCHEMAS.md before the fix. The same local `test_json_reference.py` exited 1 with `reference_exists: false` on that committed-docs fixture, then exited 0 on the branch with all seven assertions passing: the reference and Overview link exist, the link resolves, all 48 JSON/JSONL examples parse, the original 16 match their 0.11.7 captures, and all 30 output/field/type/link checks pass. From the clone, `python -X utf8 ../test_json_reference.py` repeats the after check. Step 7's missing-link and broken-link controls remain preserved separately.

I also repeated all 22 original offline CLI invocations: version; clean/finding scans through secrets, agent scan and scan local; unsupported audit --json; config show; and Claude/Codex policy exports, for both runtimes. Both report 0.11.7. All 22 exits matched expectations, including scan findings exiting 1 and unsupported audit JSON exiting 1 in Node or 2 in Python. All 12 scan results agree across aliases/runtimes; Claude export is JSON, Codex export is TOML, and riskLevel/risk_level remain distinct. These real outputs validate the documented behavior; this patch changes no runtime behavior.

I ran the three exact included commands in ship-manifest.md through the installed gate's repository-check runner, using the existing Python wrapper and scratch profiles: `node-build`, `node-json-tests`, and `python-json-tests`. The build exited 0; the selected existing MCP/policy/snapshot files passed **19 Node tests** and **82 Python tests**, with no skips. Node ran serially with one worker, no file parallelism and concurrency one. Exact commands, full stdout/stderr and before/after output are pasted into the clone-root local `test_evidence.md`; raw records and stream hashes are under `p7-work/evidence/step8-tests-2026-11-09/`.

The full suites were not repeated for this documentation-only patch. Their November 3 results remain explicitly historical: Windows Node 2,195 passed / 306 failed / 20 skipped; native Windows Python has an os.geteuid collection error and a separately bounded stdio stall; its diagnostic continuation passed 1,916 and failed 90, with 12 skips and one collection error. The full Linux Python suite on the same source passed 2,047 tests with 11 optional-scanner/live-API skips and zero failures. No Linux Node suite was run. The two manifest exclusions remain unchanged, so these selected checks do not establish a passing full Node baseline or a full ship-gate PASS. Earlier real MCP/hook/watch captures are preserved and revalidated by the documentation checker; those sessions were not rerun here. Real backend schemas remain pending.

All new commands completed within their bounds; read-only monitoring found no new WHEA 18/19 event, and the final check found no surviving monitored owned processes. This does not establish the cause of the earlier crash. No dependencies or global settings changed. Work stops for review before commits, PR drafting/precheck or publication.

**2026-11-10 — One authorized backend scan.** The actual Python run submitted one Fast job for my public fork's main. Its result confirms the pinned commit, engine rafter-fast@0.10, completed status and partial=false, with 73 reported findings (12 error, 47 warning, 14 note). Reading that same ID through Python and Node produced identical parsed JSON; all three commands exited 0. I preserved the true finding count and exit behavior without treating the report as a clean assessment or changing runtime code. Queued/processing responses and the submission/ID were saved before the CLI's final output. Fast quota changed from one remaining to zero; Plus stayed zero. No second creation request or Sites operation occurred.

Added six actual backend selections and 35 field rows while preserving the 48 earlier examples. The extended local checker failed on the draft before the backend addition and passes afterward: eight assertions, all 30 existing local-output checks, and nine backend checks covering every field/type in all 73 real findings. Six damaged draft controls are rejected; the original missing-reference test still fails on committed-before docs. Fresh exact manifest commands again pass the build, 19 Node tests and 82 Python tests. Complete backend/manifest outputs are appended to local test_evidence.md; capture provenance is under the one-fast-scan evidence folder. Published endpoint definitions agree on severity; scanned_commit is observed but absent from their field table. Unobserved nullable/outcome/Sites variants remain explicit, and the older full-suite results retain their dates. No full ship-gate PASS, new model grade or publication is claimed.

**2026-11-10 — Full Linux Node baseline.** The unchanged full suite now passes on native Linux Node 24.16.0/pnpm 10.34.9: **2,505 passed, 16 skipped, zero failures**, 2,521 tests across 123 files. The 16 existing skips are seven live-API cases and nine optional-engine cases; the real key was excluded. All 306 previously Windows-failed cases pass in Linux. The first run had three setup failures (missing genuine origin/main and a forced counter opt-out); after correcting only the harness, the two affected files passed 8/8 and the full suite passed. The repository's 1,990-executed floor also passes with its existing backend-file exception from the correct node working directory. Exact source, locks, assertions and skip conditions are unchanged. Prior Linux Python evidence remains 2,047 passed/11 skipped on November 3; native Windows failures are preserved, not claimed fixed. Complete reports and the appended test_evidence.md distinguish every attempt. The full Node baseline is resolved on Linux; Sites and release review remain open.

**2026-11-10 — Step 10 branch ship-gate.** The installed gate ran on documentation commit a70de5e against upstream/main and returned ship-gate: PASS on its first attempt. All three exact included manifest commands passed: TypeScript build, selected Node MCP/policy/snapshot tests and selected Python MCP/policy/snapshot tests. All five PR checks passed: plan fidelity, decisive test evidence, diff reviewability, template compliance and AI disclosure. The earlier full Linux suite results remain dated evidence; Step 10 did not repeat those broader suites. No rubric, check, exclusion or acceptance rule was changed. Complete gate streams and its local log entry are saved separately so the files fingerprinted by the PASS remain unchanged.


**Toolkit**

- Tool: Codex-assisted offline and actual backend captures, the local documentation checker extended for six backend examples, and the installed gate's repository-check runner; no new model/precheck call.
- What it produced: Before/after evidence, the original 22 offline transcripts, one durable Fast submission with identical run/get results across runtimes, quota proof, 54 validated examples, six new negative controls, and fresh successful build/19 Node/82 Python output, and a complete 2,505-pass Linux Node baseline with disclosed skips. Step 10 adds an actual first-attempt ship-gate PASS on the committed branch, with all three manifest commands and all five PR checks passing.
- Difficulties: The one-scan allowance required durable ID recovery and no POST retry; API-key scope was not shown in the UI. Exit 0 coexists with 73 findings, and published field definitions omit the observed scanned_commit. Historical Windows suite failures remain recorded; the full Linux Node baseline passes after fixing the clone ref and disposable counter-test environment.
- What changed: Extended local-only provenance/type checks while preserving their earlier versions and evidence; documented real wire fields and explicit excerpts, kept the two-document patch, and left Sites/unobserved outcomes and release gates open.

---

## Implementation Notes

**2026-10-31**

Added the first part of `shared-docs/JSON_SCHEMAS.md` for local scan outputs and aliases, audit JSONL, configuration, and Claude policy export. It includes 16 examples selected from 78 actual local command/logger invocations across Node and Python, with field paths, types, presence conditions, runtime differences, and unspecified field stability. Only fixture/profile paths were sanitized; configured examples are labeled as controlled settings rather than factory defaults. The remaining CLI, hook, MCP and backend families are visibly pending.

The local documentation checker passed 23 checks covering capture provenance, JSON/JSONL parsing, field descriptions and observed types, links, masking, format boundaries and audit bytes. Seven scratch-copy controls were rejected as expected: an absent reference, malformed JSON, an omitted required field, a drifted example, a broken link, a missing field description, and a wrong type. The Node build and selected 19 Node / 65 Python regression tests passed again; the known full-suite baseline limits remain unresolved.

Two real runtime limits were preserved in the documentation and evidence. Python's Windows audit verifier reported 12 breaks on a fresh scan log, while all stored hashes matched the previous raw CRLF line bytes; its text verification normalizes those endings to LF. The Node ESM build's policy `--output` branch failed with `require is not defined`, while stdout JSON export succeeded in both runtimes and Python's file export worked. No runtime code or test assertions were changed. Source-only branches are labeled, no backend calls or new installations were made, and the work stopped for review before the remaining local families.

**2026-11-03 — Source and plan refresh**

I pulled upstream into both local Rafter checkouts, bringing the working source to 0.11.7 at `1ebad941815d91d45d7befe3295d15f23a8b05ad`. The source moved by 11 commits; `telemetry` became `counters`, its environment setting became `RAFTER_USAGE_COUNTERS`, and project-policy handling and risk rules changed. I updated the plan, source inventory, child environment and draft's version labels. The earlier examples remain explicitly marked as 0.11.5 captures, with current-version replay planned before final verification.

The lockfiles did not change. Refreshing the existing editable Rafter metadata with `--no-deps` changed only that installed package from 0.11.5 to 0.11.7; all 49 locked dependency versions still match. Both CLIs report 0.11.7, the Node build passed, and the selected files passed 19 Node and 82 Python tests. I kept the full-suite limitations visible and did not upgrade the separate Linux checkout or start the remaining output/MCP capture interval. The actual Claude Code plan-check accepted the refreshed 0.11.7 package with all six required checks passing. The plan and draft comment were preserved during grading; no follow-up was posted.

**2026-11-03 — Current-suite attempts and example replay**

After review, I reran the unchanged tests on 0.11.7 using serial execution and Windows resource/hardware monitoring. Node completed with 2,195 passed, 306 failed and 20 skipped. Python's standard invocation still fails collection on `os.geteuid()`. A diagnostic continuation retaining that error and omitting the separately attempted stdio file completed with 1,916 passed, 90 failed and 12 skipped. The unchanged stdio file passed seven cases then stalled; its owned process tree was stopped at 90 seconds. No matched previously passing test became a failure relative to the comparable older reports. Added counter-fixture tests and a Windows path assertion still fail; those failures were recorded, not patched away. A passing full-suite baseline remains unresolved.

I replayed the same 78 real local CLI/logger invocations in fresh 0.11.7 fixtures and profiles, regenerated all 16 examples, and passed all 23 documentation checks. Every example retains the same field paths and JSON types; differences are limited to timestamps and session identifiers. Both documented audit/policy implementation limits reproduced. The original 0.11.5 artifacts remain unchanged. No new dependency, Linux update, runtime/test change, backend capture, commit or publication occurred. The current manifest now records the fresh failures; its previously graded version is archived, and no new plan-check verdict is claimed for this evidence update. The accepted plan/comment stay unchanged. I stopped for review before the remaining Step 6 families.

**2026-11-03 — Full Linux Python baseline**

After review, I updated the existing isolated WSL checkout to the same 0.11.7 commit and refreshed only its already installed editable Rafter package with `--no-deps`. Dependency versions and lockfiles stayed unchanged. The full unmodified Python suite then passed as UID 1000: **2,047 passed, 11 skipped, zero failures or collection errors**, in about 70 seconds. All 20 real stdio tests and the Unix permission test passed, including the case that stalled on Windows. All 90 failed cases in the comparable Windows Python continuation passed in Linux. The 11 existing skips require optional scanner binaries or a real backend key; they do not establish authenticated backend output.

The Linux checkout remains clean, all 47 installed lock-matched packages agree, and earlier evidence and global files are preserved. No new monitored WHEA event or crash occurred. Node and pnpm are absent in WSL, so the Linux Node suite was not run. Python now has a passing current full-suite baseline; a passing full Node baseline and the remaining Step 6 documentation work are still pending. Nothing was published, and I stopped for review.

**2026-11-03 — Remaining local outputs and real MCP results**

I posted the promised [progress update](https://github.com/Raftersecurity/rafter-cli/issues/36#issuecomment-6622914775) at 22:54 Central after the manual voice-guard check passed. It reported the 16 current-version examples and Linux Python result, with remaining local/backend work still explicit. A later thread read during implementation showed the update and no maintainer response.

I extended JSON_SCHEMAS.md with status/verify/component inventories, baselines, skill list and review wrappers, local docs, gates, counters, hook outputs, watch framing, seven local MCP tools and all three resources. This interval used 144 serial monitored process invocations, including two real MCP sessions with 56 requests. It added 32 examples and 286 field rows; the original 16 examples remain unchanged. The Node session used the actual built server with its SDK transport, and Python used the actual CLI server over stdio in WSL. Inputs and suppression writes stayed in disposable fixtures, no evaluated command was executed, and no optional tool or integration was installed.

Actual runtime differences shaped the reference: Python MCP emits structuredContent containing JSON text and labels resource content text/plain; keyed config reads return a key/value wrapper. Node returns a selected config value directly, while a missing key triggered SDK error -32602. Error text and protocol errors also differ. Watch --json mixes human text and repeated JSON objects; an initial bounded probe was preserved as incomplete, and corrected timed-edit captures observed two objects in each runtime. CRLF/LF metadata and doc-content differences remain visible. No runtime code or test assertion was changed to unify these outputs.

All 30 current documentation/output checks passed. Eight damaged scratch drafts were rejected for missing/malformed/drifted evidence, absent field descriptions, a wrong type, a broken link, false complete coverage and decoding a Python MCP string into the wrong type. All 22 final preservation checks passed, including 368 protected paths and 723 earlier artifacts. Package versions, source, globals, accepted plan/comment, manifest, locks and CLI_SPEC are preserved; watchers stopped and no WSL Rafter stdio server remains. No new monitored WHEA event or crash occurred. Existing regression/full Linux Python evidence remains on the same unchanged source and was not rerun for these Markdown additions. Backend outputs, the full Node baseline and Step 7's cross-link/final evidence remain separate. I stopped for review without committing, pushing or opening a PR.

**2026-11-09 — Assignment Step 7: branch build checkpoint**

I continued the build on the existing local `docs/36-json-schemas` branch in `p7-work/rafter-cli`. The original checkout and the published fork still show `main`; the contribution branch has not been pushed. A fresh read confirmed upstream is still at the reviewed 0.11.7 commit and issue #36 has no maintainer reply, so the source and accepted approach needed no refresh.

I added the planned relative link from CLI_SPEC.md's Overview to JSON_SCHEMAS.md. The paragraph identifies the local field/example/runtime coverage and keeps backend-dependent sections explicitly pending. Only four tracked spec lines were added, and the existing 48-example reference stayed unchanged. The resulting contribution patch still contains exactly the two planned documentation files.

I added a local `test_json_reference.py` regression test under `p7-work`, outside upstream commits as planned. The same test fails on the committed 0.11.7 docs because the reference is absent, fails on the Step 6 draft when the canonical Overview link is missing, and passes on the working branch after the link. A deliberately broken link is also rejected. The passing run checks all 48 JSON/JSONL examples, original capture provenance, and the existing 30 output/field/type/link checks; `git diff --check` passes. Runtime code, project tests, dependencies, locks, accepted plan/comment and previous evidence are unchanged. This build checkpoint stops for review before commits/publication and the formal Testing Strategy/test_evidence.md work. Backend completion and a passing full Node baseline remain separate requirements.

**2026-11-09 — Assignment Step 8: testing and evidence**

Reran the original 22 offline CLI invocations on the existing contribution branch after the fresh build. All expected exit codes and eight diagnostic checks passed. The same documentation regression failed on the committed-before fixture for the missing reference and passed against the working tree with seven assertions, all 48 examples and the existing 30 output checks. The three exact included manifest commands passed: build, 19 Node tests and 82 Python tests. Their complete output and the before/after reproduction are now pasted into the local clone-root test_evidence.md, with raw evidence in the dated Step 8 folder.

Filled Testing Strategy and both requested Toolkit blocks. Kept the accepted plan, two documentation files, existing tests, locks and manifest unchanged; full-suite results are explicitly November 3 history, not new passes. Monitoring found no new WHEA 18/19 event or surviving monitored process. No install, global configuration change, staging, commit, model precheck, PR draft, issue post or publication occurred. Backend evidence, a passing full Node baseline, maintainer response and release approval remain open. Stopped for the agreed review.

**2026-11-09 — Read-only backend access and quota check**

After I supplied a Rafter API key in the ignored local .env, the actual Node and Python usage commands both authenticated and returned identical JSON with exit 0. The response reports one Fast scan remaining, zero Plus scans, and a quota reset timestamp of 2026-12-10T05:03:53.652467+00:00. This establishes read access to usage only; scan permission and Sites access remain untested. No scan was submitted or Site mutated. The key was injected only into the two isolated child environments and kept out of command arguments/evidence; the original .env.example was restored from Git after being moved. Saved the response and a proposed one-scan/reused-result budget locally for review; full backend coverage and the Node baseline remain open. No plan, runtime, dependency, global setting, commit or publication changed.


**2026-11-10 — One-scan backend preparation (began November 9)**

I agreed to use at most one Fast scan on bbdevelops/rafter-cli at main and confirmed that no completed scan was available to reuse. GitHub checks show the public fork's main still matches the pinned 0.11.7 commit. I prepared a local execution plan and capture driver that records a durable submission intent before POST and the actual response/scan ID before normal polling continues; retrieval is then read-only through both runtimes. The API-key UI does not show scope, so that remains unverified and any rejection stops the attempt. Located official submission, result and quota field definitions for comparison with actual captures.

All 18 offline fence controls passed. The actual Python run, scan and scan remote paths were rehearsed in isolated profiles with a dummy credential and blocked sockets, reaching the expected request construction without making a Rafter request or generating a fake response. Two rehearsal rounds are preserved; the final one records hashes of the completed capture helpers. The proposed live capture remains unexecuted for this planning review. Backend variants/Sites coverage and the full Node baseline remain open; the accepted plan, two documentation files and manifest are unchanged, with no new model grade, install, commit or publication.


**2026-11-10 — One Fast scan, reused results and backend reference**

Executed the reviewed one-fast-scan plan after the user authorized implementation. Fresh source/fork/quota checks passed; one actual Python POST returned a durable scan ID. The job moved through queued/processing to completed with partial=false and returned the expected scanned_commit. Python run, Python get and Node get produced identical JSON for the same job: 73 untriaged findings, 12 error/47 warning/14 note, engine rafter-fast@0.10, all exits 0. Quota confirms one Fast scan used and zero remaining; Plus was unchanged. No second submission, Sites mutation or credential disclosure occurred.

Extended JSON_SCHEMAS.md with six actual backend selections and 35 field rows, retaining all 48 local examples. The report excerpt selects three real findings with its full summary explicitly retained. Recorded severity versus older level wording, nullable/published-only branches and the observed-only scanned_commit. Preserved the pre-extension checker versions and failed-before result; the same extended checker passes afterward, with six damaged documentation controls rejected. Fresh build/19 Node/82 Python checks pass; Testing Strategy and both Toolkit blocks are updated, with complete outputs appended to excluded test_evidence.md. The accepted approach/plan, manifest/exclusions, runtime/tests and locks remain unchanged. No install, global configuration change, staging, commit, PR draft, model precheck or publication occurred. Remaining Sites/outcome evidence and full Node/release gates stay open; stopped for review.


**2026-11-10 — Assignment Step 9: local PR title and description**

Prepared pr_draft.md locally and saved the exact conventional title separately for the later gate/create commands. No repository PR template was found, so the draft follows CONTRIBUTING's Summary, Test plan, Spec update and complete checklist. It includes Fixes #36, copied before/after and passing-check output from test_evidence.md, actual paired backend results, AI disclosure and the pending AI co-author requirement. N/A items have reasons; the full-suite checkbox remains open. A fresh public read found upstream unchanged, the issue open and no maintainer reply. Sites evidence, unobserved outcomes, the full Node baseline and release review remain explicit; no scope change or new model grade is claimed.

This completes only the local drafting checkpoint. The draft is installer-excluded, and the title is stored outside the contribution checkout, keeping the upstream patch at two documentation files. No application suite, API/scan, installation, Step 10 paid precheck, staging, commit, push, issue post or PR creation ran. Stopped for the agreed Step 9 review.


**2026-11-10 — Native Linux Node setup and full-suite resolution**

After the user selected the Node baseline work and explicitly allowed a newer Node installation, I added a task-local native Linux Node 24.16.0 runtime verified against the official SHA-256, reused pinned pnpm 10.34.9, and installed frozen dependencies with lifecycle scripts disabled. A separate independent Linux checkout contains the exact runtime source and the two working documentation files; the existing Python checkout/environment, global profiles and lockfiles are preserved. Python parity uses the existing dependencies, with no Rafter key or live opt-in supplied. Tests ran serially with one worker and Windows WHEA/resource monitoring.

The first full run recorded 2,502 passed/3 failed/16 skipped. The detached clone lacked the real origin/main ref required by two differential assertions, and the harness's DO_NOT_TRACK flag disabled a local-counter positive control. Fetched the actual public main at the pinned SHA and used normal counter defaults only inside disposable test homes. All eight tests in the affected files passed, followed by the full unchanged suite: 2,505 passed/16 skipped/zero failures in about 375 seconds. All 306 recorded Windows-failed cases pass in Linux. The initial floor-check invocation had a cwd-relative exception mismatch; the same existing check/exception passes from node/, matching CI. All attempts remain saved; no assertion, source behavior or skip condition was changed.

Updated the manifest's Linux evidence, test_evidence.md, Testing Strategy and local PR draft; its both-implementation test checkbox now describes the two dated Linux passes. Native Windows outcomes remain explicit, and no cross-platform CI/full ship-gate/model verdict is claimed. No optional scanner, system/global integration, real scan, Sites write, staging, commit, push or PR occurred. The full Node baseline is resolved on Linux; Sites remains parked, and work stops for review.


**2026-11-10 — Local main synchronized before Step 10**

Fetched the fork and upstream main branches; both still match the tested 0.11.7 revision, 1ebad94. After verifying ancestry and that main was not checked out, advanced local main by 11 commits without switching away from docs/36-json-schemas. The feature commit, two documentation files, plan, evidence and PR draft stayed unchanged; nothing was staged or committed. Saved the before/after branch and preservation checks locally. No suite rerun or paid gate was needed for this branch-reference update. Scope review remains next, with publication still on hold; stopped for the agreed check-in.


**2026-11-10 — Initial contribution scope approved**

The user chose to submit the verified documentation as an initial contribution without waiting for a maintainer response. Revised the plan, synchronized Solution Approach, local plan comment and PR draft to defer Sites CLI/MCP and unobserved backend variants explicitly. Preserved all 54 real examples and existing stability guarantees, with other stability unspecified. The upstream patch remains two documentation files and adds only a scope clarification beyond the existing reference/link. Runtime code, tests and captures are unchanged, and no new scan is authorized or needed.

The PR draft now uses Related to #36 so merging an incomplete contribution will not automatically close the issue. This deliberately differs from the assignment's literal Fixes #36 wording; the reason is to describe the actual contribution without claiming the deferred work is finished. Updated the command-safe title to include the issue and initial scope. Earlier plan/draft/manifest/reference/story versions were archived before editing. The installed Claude plan-check accepted all six checks in a fresh live run (cost $0.2474355); the grader changed no protected file. It noted local-only evidence/tooling, a truncated timeline, voice-guide qualifications and the earlier procedure gap. The same documentation checker still fails on the pinned missing-reference fixture and passes after the scope clarification, with all 54 examples unchanged. This is not a Step 10 ship-gate or voice-guard verdict. Stopped before staging, committing, the Step 10 gate or publication for the agreed scope-review checkpoint.


**2026-11-10 — Documentation patch reviewed and committed**

Reviewed the reference's prose, boundaries and source links against the revised plan, and reran the existing documentation checker: all eight top-level checks, 30 local-output checks and nine backend checks pass with 54 examples. Removed one course-specific Step 6 phrase from the introduction; the captured examples, field tables and guarantees are unchanged. Staged exactly JSON_SCHEMAS.md and the four-line CLI_SPEC.md Overview link, verified the staged bytes matched the reviewed files, and checked whitespace and credential exclusion.

Committed the two-file patch as `a70de5e` on `docs/36-json-schemas`, with message `docs(#36): add an initial JSON output reference` and the required Codex co-author trailer. The commit contains 2,640 added lines, no runtime/test changes and a non-closing Related to #36 reference. Local main and both remote-tracking main branches stay at the tested base. Updated the local PR disclosure to reflect the completed trailer. Full Linux suite results remain dated evidence; no runtime suite, API scan, installation, push, public comment, PR or Step 10 gate ran. Stopped for the agreed commit checkpoint review.


**2026-11-10 — Step 10 passed on the committed initial contribution**

Ran the installed ship-gate from the contribution clone on docs/36-json-schemas with the saved exact title, pr_draft.md and explicit --base upstream/main. Before running, archived test_evidence.md and prepended a 12,790-character current-results overview plus the exact end of the committed patch: the course gate clips diff input at 120,000 characters and test evidence at 20,000. This supplies the full patch and current 54-example/Linux-baseline evidence to the reviewer while preserving every earlier transcript below it. No installed tool, rubric, manifest command, exclusion or upstream file changed.

The gate passed all three manifest commands and all five required PR-precheck checks on the first attempt, exit 0, in about 31 seconds. Its live issue read and contribution policies were part of that review. The precheck accepted the explicit deferrals and Related to #36 reference, and left non-blocking voice observations about shortening process detail and labeling pasted results as author-run evidence. Those observations are saved, not represented as a voice-guard pass. All 12 monitor samples and the final check found no new WHEA 18/19 event; no owned gate process remains.

Recorded this outcome in Testing Strategy, both relevant Toolkit blocks and the Unit 7 entry. Kept the committed docs, plan, manifest, title, PR body and evidence unchanged after the PASS so the gate's 30-minute reuse rule can apply. No push, public comment, PR, new scan or installation ran. Stopped for the agreed Step 10 review before Step 11; an expired pass requires the gate to run again before opening the PR.


**2026-11-10 — Step 11: branch pushed and upstream PR target selected**

Verified that the authenticated GitHub account is bbdevelops, the origin remote is my fork of Raftersecurity/rafter-cli, and the local branch still contains exactly the reviewed two-document commit. Pushed docs/36-json-schemas with normal git push -u, creating the [branch on my fork](https://github.com/bbdevelops/rafter-cli/tree/docs/36-json-schemas). A fresh remote-ref read confirms the full a70de5e commit, and the local branch now tracks origin/docs/36-json-schemas.

Ran gh repo set-default Raftersecurity/rafter-cli from the contribution clone, then verified the setting with gh repo set-default --view. The later PR will therefore target the original project from this clone. The documentation commit and Step 10 fingerprinted inputs are unchanged; no gate/model rerun, force push, new scan, installation, issue comment or PR creation occurred. Stopped for the agreed Step 11 review before opening the PR through Claude Code and its two hooks.


**2026-11-10 — Step 12: upstream PR opened through Claude Code**

Opened [Raftersecurity/rafter-cli#357](https://github.com/Raftersecurity/rafter-cli/pull/357) through an actual Claude Code Bash call, with the exact saved title and pr_draft.md. Used GitHub base main and explicit head bbdevelops:docs/36-json-schemas; local main and upstream/main were verified as the same tested base. The earlier manual PASS had expired, so the ship-gate reran its three manifest commands and five PR checks inside the opening hooks. Both it and voice-guard passed without changing the reviewed title, body, plan or patch.

The first noninteractive attempt passed both hooks but Claude's permission matcher denied execution: the literal allow rule did not match the quoted title. Its natural-language result incorrectly said the hooks had not run; their saved logs showed both passes. After a fresh GitHub read confirmed no PR existed, a second session used a documented wildcard for title text while fixing the body filename, base and head. No persistent permission setting or hook was changed, and the one successful gh command returned the upstream URL.

Verified the published PR is open, authored by bbdevelops, targets Raftersecurity/rafter-cli main from my fork branch, and contains the exact reviewed body/title, commit a70de5e and only JSON_SCHEMAS.md plus the CLI_SPEC.md Overview link. Both attempts have clear health checks, with no remaining owned process or new monitored WHEA event. No merge, additional push, public comment, new scan or installation occurred. Stopped for the agreed Step 12 review; the formal story PR fields and course publication remain the next assignment checkpoint.


**2026-11-10 — Step 13: formal PR record and course story publication**

Added PR #357 to the story header and Pull Request section, summarized its published scope, evidence and AI disclosure, and set Status to Awaiting review. Filled the Pull Request Toolkit block from the actual ship-gate and voice-guard logs. A fresh GitHub read found the PR open with no maintainer feedback; Copilot's automated review did not complete because its review quota was insufficient. That is not a code finding or a maintainer verdict.

Prepared only beat-2-contribution/contribution-story.md for the course repository's default main branch, including the accumulated Unit 7 planning, implementation and testing notes. The remote main still matches the prepared base, so publication can preserve history with a normal fast-forward push. Raw evidence, plans, credentials, hooks and helper files remain local. Publication verification is recorded separately after the commit; the upstream Rafter PR and its two-document commit are unchanged.


**Toolkit**

- Tool: Codex-assisted source tracing, serial real CLI/logger/MCP captures, scoped documentation validation, monitored Windows/WSL execution, a local before/after documentation regression test, and the installed gate's repository-check runner, and one guarded actual backend submission with paired read-only retrieval.
- What it produced: 54 capture-backed examples and a passing full Linux Node baseline, field descriptions and runtime variants for local output families, raw streams/inputs/provenance, real audit and suppression evidence, the canonical Overview link, and a regression that fails before the fix and passes on the working branch; Step 8 adds test_evidence.md with 22 fresh CLI transcripts and successful build/19 Node/82 Python output.
- Difficulties: Windows audit line endings, Node policy-file export, Node missing-key MCP serialization, Python SDK wrappers/MIME metadata, and mixed watch stdout prevented assuming uniform JSON behavior.
- What changed: documented actual boundaries and conditional fields, used real SDK/server calls and inert local fixtures, preserved the failed probe and implementation limits, and kept existing guarantees separate from unspecified stability. The November 10 backend interval adds six selections and 35 field rows with a one-attempt fence and real quota proof. The later scope revision explicitly defers Sites/unobserved variants and removes the maintainer-response hold. The reviewed two-file patch is committed; Step 10 and both opening hooks passed, and upstream PR #357 is open. The formal PR record now summarizes those outcomes for the course story.

---

## Pull Request

**PR Link:** [Raftersecurity/rafter-cli #357](https://github.com/Raftersecurity/rafter-cli/pull/357)

**PR Description:**

`docs(#36): add an initial JSON output reference` adds shared-docs/JSON_SCHEMAS.md and a four-line Overview link in CLI_SPEC.md. The reference gives integrators 54 examples from real Node/Python output, with field descriptions, types, presence conditions, runtime differences and stability notes. It covers local CLI commands, audit JSONL, hooks, local MCP tools/resources and the observed hosted Fast run/get/usage responses. Runtime code, repository tests, dependencies and versions are unchanged.

The description records the narrower scope: Sites CLI/MCP responses and unobserved backend variants are explicitly deferred, and field stability stays unspecified unless an existing contract guarantees it. It uses Related to #36 rather than claiming to close the full issue. The before/after evidence shows the documentation check failing on the missing reference and passing after the reference and link were added. The build and selected 19 Node/82 Python tests pass; the full Linux baselines are 2,505 Node tests passed/16 skipped and 2,047 Python tests passed/11 skipped. Native Windows limitations and unrun cross-platform CI are disclosed.

The AI disclosure explains how I used Codex for source tracing, documentation, validation helpers and evidence collection, and Claude Code for reproduction/plan review and the posting hooks. The documentation commit includes the required AI co-author trailer.

**Maintainer Feedback:**

- **2026-11-10:** No maintainer feedback yet; awaiting review. Copilot's automated reviewer reported insufficient review quota and did not complete a review. It supplied no code findings, and no maintainer response or acceptance is implied.

**Status:** Awaiting review

**Toolkit**

- Tool: the installed ship-gate and canonical voice-guard through Claude Code, with Git and gh for the branch push, upstream target and published PR verification.
- What it produced: a Step 10 PASS on all three manifest commands and all five required PR checks, followed by passing opening hooks and upstream PR #357. GitHub verification confirmed the reviewed title/body, fork head, main base, commit a70de5e and exactly two documentation files.
- Difficulties: the gate's 120,000-character diff and 20,000-character evidence limits would hide recent results and the end of this large reference. The manual PASS expired before opening. The first creation session passed both hooks but its literal command permission rule did not match; Claude's natural-language response incorrectly said the hooks had not run, which their saved logs disproved.
- What changed: put current results and the exact diff continuation before the preserved historical evidence, kept the manifest commands and rubric unchanged, and let the expired gate rerun. A fresh session used a temporary permission rule with variable title text and fixed body/base/head; both hooks passed again and the PR opened. No persistent permission setting or hook was weakened. The story records the explicit Sites deferral and remains Awaiting review.

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
