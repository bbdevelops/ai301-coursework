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
**Pull Request:** [GitHub PR link, once opened]

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

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

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

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

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

**Limits:** no live authenticated backend scan or `rafter get` request was run. MCP tool payloads and audit JSONL storage were inspected in source/specs, not exercised through a live MCP session or audit-log test. No project-wide test suite was run; the Node build and the 22 CLI diagnostics are the executed checks. Field-stability guarantees still need maintainer guidance, already requested in the claim.

**Toolkit**

- Tool: repro-check in Claude Code, grading the claim and reproduction together in full-package live mode; a scoped setup and diagnostic runner collected the evidence.
- What it produced: acceptance on all seven required checks, backed by the pinned source, missing-reference output, and 22 offline CLI invocations with nine diagnostic checks passing.
- Difficulties: Windows path/cache errors interrupted Python setup; stale issue commands and differing fresh-profile config fields needed qualification. The first accepted grade also flagged local bookkeeping and an unclear distinction between command runs and checks.
- What changed: used existing pip against the absolute local environment with the same lock constraints, documented current command/output variants, removed local bookkeeping from the report, and clarified all nine checks. The final report passed a second actual Claude Code grade. Authenticated backend and live MCP behavior remain source-only coverage.

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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
