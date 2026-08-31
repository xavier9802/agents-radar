# AI CLI Tools Community Digest 2026-08-31

> Generated: 2026-08-31 04:59 UTC | Tools covered: 10

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Grok Build](https://github.com/xai-org/grok-build)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## Cross-Tool Comparison



# Cross-Tool AI CLI Ecosystem Comparison — 2026-08-31

## 1. Ecosystem Overview

The AI CLI tool landscape is in a consolidation phase where major vendors (Anthropic, OpenAI, Google, GitHub) are shipping weekly while smaller open-source players (Pi, DeepSeek TUI, Qwen Code) iterate through aggressive nightly cycles. Stability regressions dominate community concern across every platform — auto-update breakage, session-loss bugs, and agent-orchestration fragility are universal pain points rather than isolated issues. The competitive axis has shifted from raw model capability to session reliability, agent sub-composition, and enterprise deployment readiness, with tool-call accuracy and cross-platform parity emerging as the new differentiators.

## 2. Activity Comparison

| Tool | Open Issues (Last 24h New) | PRs Updated (Last 24h) | Releases (Last 24h) |
|------|---------------------------|------------------------|---------------------|
| **Claude Code** | 10 hot issues; #38335 (839 💬) is the repo's #1 concern | 1 (closed) | None |
| **OpenAI Codex** | 10 hot issues; 3 alpha releases shipped | 10 (all closed/merged) | 3 (0.152.0-alpha.4–6) |
| **Gemini CLI** | 10 hot issues; nightly build shipped | 10 (merged) | 1 nightly (v0.59.0-nightly) |
| **GitHub Copilot CLI** | 10 hot issues; regression in 1.0.81 | 0 | None (latest: 1.0.81) |
| **Kimi Code CLI** | 2 issues (both new, 0 reactions) | 0 | None (latest: 0.39.1) |
| **Pi** | 10 hot issues; 8 closed recently | 10 (8 closed, 2 open) | None |
| **Qwen Code** | 10 hot issues; security review cluster | 10 (mixed) | None (nightly failed) |
| **DeepSeek TUI** | 10 hot issues; 2 high-severity | 10 (mixed) | None (v0.9.12 prep) |
| **Grok Build** | N/A | N/A | None |

## 3. Shared Feature Directions

| Direction | Tools | Specific Needs |
|-----------|-------|---------------|
| **Sub-agent orchestration reliability** | Claude Code, Gemini CLI, OpenAI Codex, Pi | Pause/resume on transient failure (#78224 Claude), subagent notification propagation (#75043 Claude), false GOAL success on turn-limit (#22323 Gemini), session resume failures (#39823 Codex) |
| **Cross-session / multi-agent messaging** | Claude Code (#90890), Qwen Code (#8724), Pi (#2941) | `send_message` + `list_agents` across sessions; work-in-progress at Qwen, requested at Claude and Pi |
| **MCP ecosystem expansion** | Claude Code, OpenAI Codex, Gemini CLI, DeepSeek TUI | Package-style server names (#41700 Codex), nested-param serialization (#87361 Claude), ACP tool-use parity (#2535 DeepSeek), environment-backed stdio fixtures (#41683 Codex) |
| **Rate-limit / quota transparency** | Claude Code (#38335), OpenAI Codex (#33685, #41742) | Per-agent context compaction thresholds (#90347 Claude), actionable TUI banners (#41742 Codex), opt-in `update_plan` (#41744 Codex) |
| **Security & config hardening** | Qwen Code (#10560, #10561, #10427), Gemini CLI (#26525), DeepSeek TUI (#5772) | Hook execution trust-boundary fixes, AST-aware secret redaction in Auto Memory, provider-picker credential leakage |
| **Session continuity & resume** | All major tools | Session-loss on auto-update (#90172 Claude), `already has an active writer` (#39823 Codex), broken session-resume IDs (#5750 DeepSeek TUI), JSONL duplicate-write corruption (#8852 Pi) |
| **Plugin / extension ecosystem maturity** | Pi (#4748, #8872), GitHub Copilot (#3606), DeepSeek TUI (#5747) | Extension-host singleton divergence, auto-reload after install, unified MCP/plugin auth flow |

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | Pi | Qwen Code | DeepSeek TUI | Kimi Code CLI |
|-----------|-------------|-------------|------------|-------------------|-----|-----------|-------------|--------------|
| **Primary focus** | Enterprise Max plan agents, subagent orchestration | Rust client iteration, transparency features | Nightly reliability, cross-platform polish | Enterprise OAuth, BYOK, plugin skills | Extension ecosystem, provider diversity | Security hardening, multi-agent messaging | Sandbox flexibility, crate decomposition | Niche model reliability |
| **Target users** | Max-plan teams, Windows/macOS power users | Pro/Team users, automation builders | Daily-nightly testers, cross-platform devs | GitHub Enterprise users, corporate proxies | Open-source tinkerers, multi-provider users | Security-conscious teams, Chinese ecosystem | Local-first devs, Rust users | Mobile/cross-device experimenters |
| **Release cadence** | Monthly desktop builds, slow PR velocity | 3 alphas/day — highest velocity | Daily nightlies | Sporadic; regression in 1.0.81 | Weekly-ish; extension-driven | Slow; nightly failed | v0.9.12 prep; deliberate | Sparse |
| **Technical approach** | Electron desktop + ShipIt auto-updater | Rust-native client, Responses API | TypeScript, A2A server architecture | TypeScript/Node, VS Code integrated | Rust monorepo, extension API | Rust + llama.cpp, WebShell | Rust crate decomposition | Node.js, lightweight |
| **Key differentiator** | Deep agent orchestration (nested subagents) | Fastest iteration, rate-limit banners | Fallback model chain on quota exhaustion | Enterprise OAuth + BYOK persistence | Provider-agnostic, 10+ providers built-in | Security review velocity, worktree support | Sandbox awareness, no-sandbox escape valve | Model-specific tool-call alignment |

## 5. Community Momentum & Maturity

**Most active communities (by engagement):**
- **Claude Code** — #38335 with 839 comments and 476 👍 is the most engaged issue across the entire ecosystem. The Max quota leak is a trust crisis.
- **OpenAI Codex** — Highest PR velocity (10 merged in 24h) with 3 alpha releases. Active iteration signals a team moving fast.
- **Gemini CLI** — 10 merged PRs daily plus nightly builds. Strong engineering momentum with community-aligned fixes.
- **Pi** — 8 of 10 recent PRs closed, showing a responsive maintainer. Extension API pain points indicate a growing but fragile ecosystem.

**Rapidly iterating:**
- **OpenAI Codex** leads on release frequency (3 alphas/day). The team is clearly in active development mode.
- **Gemini CLI** follows with daily nightlies and consistent PR throughput.
- **DeepSeek TUI** is undergoing architectural decomposition (EPIC-005 crate split), signaling a transition from monolith to modular design.

**Maturity signals:**
- **Claude Code** has the largest user base (evidenced by issue volume) but the slowest PR velocity — a sign of enterprise-scale complexity.
- **Qwen Code** shows mature security review processes (cluster of P1 findings with parallel PR fixes).
- **GitHub Copilot CLI** shows regression patterns (1.0.81 OAuth breakage) typical of fast-moving consumer integrations.

## 6. Trend Signals

1. **Agent orchestration is the new battleground.** Every major tool is investing in subagent reliability — pause/resume, notification propagation, turn-limit handling. Tools that solve this first will capture power-user workflows.

2. **Session continuity is universally broken.** Auto-update kill sessions (#90172 Claude), duplicate JSONL writes (#8852 Pi), broken resume IDs (#5750 DeepSeek), and writer-lock wedges (#39823 Codex) all point to a systemic architectural gap. The tool that gets transparent, crash-free session resume will have a decisive advantage.

3. **Quota and rate-limit opacity erodes trust.** Claude's Max plan leak (#38335), Codex's weekly drain complaints (#33685), and Gemini's fallback-chain request (#26914) all reflect a community demanding spend visibility. Actuarial transparency is becoming a feature request, not just a billing question.

4. **Windows is the canary for stability.** Every tool reports Windows-specific regressions — always-on-top bugs (#85891 Claude), handshake failures (#41049 Codex), driver panics (#10538 Qwen), OAuth proxy breaks (#4671 Copilot). Cross-platform parity remains unrealized; Windows-first debugging is a competitive differentiator.

5. **MCP is moving from local experiments to registry-scale distributions.** Package-style server names (#41700 Codex), environment-backed test fixtures (#41683 Codex), and ACP tool-use parity (#2535 DeepSeek) signal that MCP is maturing beyond single-server setups into CI-integrated, versioned, registry-distributed tool ecosystems.

6. **Security reviews are producing parallel PR clusters.** Qwen's simultaneous P1 fixes (#10427, #10560, #10561) and Pi's credential-leak and dead-code sweeps (#4785, #5772) show that the community is treating security as a continuous process, not a one-time audit. This will become a differentiator for enterprise buyers.

7. **Small tools are filling gaps the big vendors ignore.** Pi's extension API maturity, DeepSeek TUI's `--no-sandbox` escape valve, and Qwen's worktree improvements address pain points that Claude Code and Codex treat as low priority. Open-source CLI tools remain the canary for features the commercial tools will adopt in 6–12 months.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-31 · Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

### #1 — `skill-creator` / `run_eval.py` Bug Suite
**Status:** Open (multiple open PRs)
- [PR #1298](https://github.com/anthropics/skills/pull/1298) — Core fix: `run_eval.py` reports 0% recall universally because it installs the eval artifact as a real skill rather than a command; also fixes Windows stream reading, trigger detection, and parallel workers.
- [PR #1099](https://github.com/anthropics/skills/pull/1099) — Windows crash fix: `run_eval.py` records every query as "not triggered" due to pipe read errors.
- [PR #1050](https://github.com/anthropics/skills/pull/1050) — Windows subprocess fix: `claude.cmd` not found on PATH by `subprocess.Popen`.
- [PR #539](https://github.com/anthropics/skills/pull/539) — YAML quoting guard for unquoted `description` fields containing `:`.
- [Issue #556](https://github.com/anthropics/skills/issues/556) — Original bug report; 7 👍, 12 comments.

**Summary:** The skill-creator evaluation harness has a multi-layered bug affecting both Windows and cross-platform recall/trigger logic. The community has produced three converging PRs; no single PR is yet merged, making this the most actively contested fix in the repo.

---

### #2 — `document-typography` Skill
**Status:** Open
- [PR #514](https://github.com/anthropics/skills/pull/514) — Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents.

**Summary:** Addresses a widely felt pain point—AI-generated documents look unprofessional due to typographic defects. First skill-level proposal targeting prose formatting quality rather than structural document generation.

---

### #3 — `pdf` & `docx` Skill Fixes
**Status:** Open
- [PR #538](https://github.com/anthropics/skills/pull/538) — Case-sensitivity fix in `skills/pdf/SKILL.md` (8 mismatches).
- [PR #541](https://github.com/anthropics/skills/pull/541) — DOCX tracked-change `w:id` collision with existing bookmarks causing document corruption.
- [Issue #12](https://github.com/anthropics/skills/issues/12) — Word/LibreOffice readability loss due to whitespace reformatting in OOXML.

**Summary:** Two separate skill ecosystems (PDF and DOCX) are receiving active maintenance. The DOCX fix is particularly high-impact: hardcoded low `w:id` values conflict with existing bookmarks, corrupting documents on merge.

---

### #4 — `frontend-design` Skill Improvement
**Status:** Open
- [PR #210](https://github.com/anthropics/skills/pull/210) — Revisions to improve clarity, actionability, and internal coherence; ensures every instruction is something Claude can execute in a single conversation.

**Summary:** A quality-of-life improvement PR rather than a new skill, but notable for its explicit focus on "actionability" as a design criterion—reflecting a maturing community understanding of what makes a skill effective.

---

### #5 — `testing-patterns` Skill
**Status:** Open
- [PR #723](https://github.com/anthropics/skills/pull/723) — Comprehensive testing skill covering testing philosophy (Testing Trophy), unit testing (AAA pattern, pure functions, edge cases), and React component testing (Testing Library).

**Summary:** First community skill to provide a full testing pedagogy rather than a single pattern. Aligns with the broader demand for test-generation guidance visible across multiple issues.

---

### #6 — `servicenow` Skill
**Status:** Open
- [PR #568](https://github.com/anthropics/skills/pull/568) — Broad ServiceNow platform skill covering ITSM, ITOM, ITAM/SAM, FSM, HRSD, CSM, SPM/PPM, Vulnerability Response, Security Incident Response, and IntegrationHub.

**Summary:** Represents the most ambitious enterprise-platform skill proposal, targeting IT service management workflows. Reflects demand for Claude to assist with vendor-specific enterprise tooling beyond generic coding tasks.

---

### #7 — `mcp-builder` Evaluation Fix
**Status:** Open
- [PR #1602](https://github.com/anthropics/skills/pull/1602) — Fixes evaluation serialization (TextContent not JSON-serializable), benchmark metric calculation, encoding, and script stability.
- [Issue #1390](https://github.com/anthropics/skills/issues/1390) — Reports that evaluation scores 0/N against any real MCP server due to swallowed `TextContent` errors.

**Summary:** The MCP builder's own evaluation harness is broken for real-world MCP servers. Fixing this is prerequisite for reliable MCP skill quality assurance.

---

### #8 — `claude-api` Skill Update
**Status:** Open
- [PR #1607](https://github.com/anthropics/skills/pull/1607) — Marks four retired model IDs (`claude-opus-4-1`, `claude-sonnet-4-0`, `claude-opus-4-0`, `claude-3-haiku-20240307`) as retired.
- [Issue #1487](https://github.com/anthropics/skills/issues/1487) — Reports that the skill eagerly injects ~156k tokens, exhausting the context window in a single tool call.

**Summary:** Dual issues—stale model references and a context-waste bug. The latter is a systemic design problem in the skill's approach to API documentation injection.

---

## 2. Community Demand Trends

| Trend | Evidence |
|---|---|
| **Evaluation & quality gates** | Issues #556, #1390; PRs #1602, #1367; Issue #1385 propose multi-gate pipelines (pre-task calibration → adversarial review → delivery verification). The community wants *provable* skill quality, not just well-written SKILL.md files. |
| **Enterprise platform skills** | PR #568 (ServiceNow), PR #1615 (SCNet HPC), PR #1628 (Hivemind multi-agent orchestration). Demand extends beyond coding into IT operations, HPC workflows, and agent orchestration. |
| **Document fidelity & formatting** | PRs #514, #538, #541; Issues #12, #1175. Users want Claude to produce documents that survive round-trip through Word/LibreOffice without corruption or unexpected reformatting. |
| **Org-wide skill sharing** | Issue #228 (8 👍) — the #2 most-upvoted issue. Users want to share skills within an organization without manual download/upload workflows. |
| **Testing & reasoning quality** | PR #723 (testing-patterns), Issue #1385 (reasoning quality gate), PR #83 (skill-quality-analyzer + skill-security-analyzer). A meta-trend toward *meta-skills* that audit and improve other skills or Claude's own output. |
| **Cross-platform / Windows compatibility** | PRs #1298, #1099, #1050 all address Windows-specific failures in skill-creator scripts. Repeated feedback that skill development tooling is not truly cross-platform. |
| **Security & trust boundaries** | Issue #492 (43 comments, 2 👍) — community skills impersonating Anthropic's namespace. Issue #1175 — concerns about encoding access-control logic inside SKILL.md files for SharePoint handling. |

---

## 3. High-Potential Pending Skills

These open PRs have active discussion and address clear user needs; they are the most likely to merge in the near term:

| Skill | PR | Why It's Likely |
|---|---|---|
| **document-typography** | [#514](https://github.com/anthropics/skills/pull/514) | Solves a universal pain point with a focused, low-risk addition. |
| **testing-patterns** | [#723](https://github.com/anthropics/skills/pull/723) | Comprehensive, well-scoped, and fills a clear gap in the existing skills catalog. |
| **ServiceNow** | [#568](https://github.com/anthropics/skills/pull/568) | Enterprise demand; broad coverage makes it a high-value addition despite its size. |
| **Hivemind** | [#1628](https://github.com/anthropics/skills/pull/1628) | Novel multi-agent delegation pattern; addresses cost/efficiency concerns directly. |
| **scnet-hpc** | [#1615](https://github.com/anthropics/skills/pull/1615) | Niche but dedicated user base (academic/research HPC). |
| **ODT** | [#486](https://github.com/anthropics/skills/pull/486) | OpenDocument Format is underrepresented; fills a gap for Linux/LibreOffice users. |
| **Self-audit (v1.3.0)** | [#1367](https://github.com/anthropics/skills/pull/1367) | Mechanical verification + four-dimension reasoning gate; aligns with the quality-gate trend. |
| **pyxel** | [#525](https://github.com/anthropics/skills/pull/525) | Creative/entertainment niche with an existing MCP server backing it. |

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **reliable evaluation and quality-assurance tooling** — the skill-creator's own evaluation harness is broken across platforms, and users are simultaneously building meta-skills (self-audit, skill-quality-analyzer, reasoning quality gates) to compensate, signaling that the ecosystem has outgrown its ability to self-validate and needs a trustworthy baseline before it can scale.

---



# Claude Code Community Digest — 2026-08-31

## 1. Today's Highlights

The community is dominated this week by a single high-impact bug: **Max plan session limits are being exhausted abnormally fast since March 23** (issue #38335, 839 comments, 476 👍), suggesting a systemic quota leak affecting a large user base. Alongside that, multiple Windows and macOS stability regressions surfaced in the last 48 hours — desktop hangs, CoworkVMService permission failures, and a process-leak on scheduled-task completion — signaling that the recent auto-update rollout (ShipIt) introduced regressions across multiple platforms.

---

## 2. Releases

**No new releases in the last 24 hours.**

| Item | Detail |
|------|--------|
| Latest bundled CLI (macOS Desktop) | v2.1.229 → v2.1.247 (current) |
| Windows Desktop build cited | v1.34493.1.0 (Electron 42.9.2) |
| Note | A ShipIt-staged auto-update at the incident window is implicated in several new bugs below. |

---

## 3. Hot Issues

### 🔴 #38335 — Max session limits exhausted abnormally fast *(839 💬 · 476 👍)*
**Status:** OPEN · **Created:** 2026-03-24 · **Updated:** 2026-08-31
**Why it matters:** This is the #1 community concern by far. Users on the Max plan report quotas draining far faster than expected since a March 23 change. The sheer comment volume (839) and 👍 count (476) make it the most visible issue in the repo.
**Link:** https://github.com/anthropics/claude-code/issues/38335

### 🔴 #10238 — Add support for subdirectories in skills *(53 💬 · 168 👍)*
**Status:** CLOSED · **Created:** 2025-10-24
**Why it matters:** A long-requested enhancement that was finally closed — likely addressed in a later release. Worth reviewing the closure commit to confirm the feature shipped.
**Link:** https://github.com/anthropics/claude-code/issues/10238

### 🟠 #85891 — Windows 11: Desktop always-on-top, no disable option *(45 💬 · 101 👍)*
**Status:** OPEN · **Created:** 2026-08-11
**Why it matters:** A UX regression exclusive to Windows 11. The Desktop window cannot be backgrounded, breaking multi-monitor workflows. The Windows counterpart to the long-standing macOS #66516.
**Link:** https://github.com/anthropics/claude-code/issues/85891

### 🟠 #85603 — Typed input silently dropped mid-turn at turn-end *(24 💬)*
**Status:** OPEN · **Created:** 2026-08-10
**Why it matters:** A TUI regression in Claude Code v2.1.220/226 on macOS inside tmux. Text typed while a turn is running gets silently dropped at turn-end, causing data loss for power users in long-running agent sessions.
**Link:** https://github.com/anthropics/claude-code/issues/85603

### 🟠 #75043 — Nested subagent completion notifications never reach parent *(20 💬)*
**Status:** OPEN · **Created:** 2026-07-07
**Why it matters:** A critical agent-orchestration bug: when an orchestrator subagent spawns children via the `Agent` tool, `TaskStop` fails with ownership errors after resume, and completion notifications never propagate to the parent. Reproduces across Opus 4.8 and Fable 5.
**Link:** https://github.com/anthropics/claude-code/issues/75043

### 🟡 #85840 — CoworkVMService can never arm recovery on Windows *(8 💬)*
**Status:** OPEN · **Created:** 2026-08-11
**Why it matters:** On Windows, the Cowork VM service fails at every start with "Access is denied," causing in-flight work to be silently lost. This is the primary evidence issue for the root-cause analysis in #89711.
**Link:** https://github.com/anthropics/claude-code/issues/85840

### 🟡 #70678 — Keyboard nav between chat messages *(5 💬 · 5 👍)*
**Status:** OPEN · **Created:** 2026-06-24
**Why it matters:** A quality-of-life feature request: jump between previous/next user prompts in a conversation using keyboard shortcuts. Simple to implement, high user demand.
**Link:** https://github.com/anthropics/claude-code/issues/70678

### 🟡 #90172 — Stealth restart destroys running sessions *(5 💬 · 2 👍)*
**Status:** OPEN · **Created:** 2026-08-27
**Why it matters:** The umbrella issue for a wave of session-loss bugs triggered by the ShipIt auto-update. Users report "Can't reach your computer" errors and immediate session termination with no crash dump. Multiple sub-issues filed individually.
**Link:** https://github.com/anthropics/claude-code/issues/90172

### 🟡 #78224 — Pause-and-resume subagents on recoverable failures *(4 💬 · 2 👍)*
**Status:** OPEN · **Created:** 2026-07-16
**Why it matters:** Feature request: when a background subagent hits a transient API error or usage limit, pause it instead of terminating, so in-progress work on disk is preserved and can be resumed later.
**Link:** https://github.com/anthropics/claude-code/issues/78224

### 🟡 #78674 — Linux memory-pressure reaper kills all background tasks *(3 💬)*
**Status:** OPEN · **Created:** 2026-07-17
**Why it matters:** On Linux hosts with low `MemFree` but high `MemAvailable` (PSI ~0), Claude Code's background-shell reaper kills all `run_in_background` Bash tasks simultaneously — a false positive triggered by memory fragmentation, not actual pressure.
**Link:** https://github.com/anthropics/claude-code/issues/78674

---

## 4. Key PR Progress

| # | Status | Summary |
|---|--------|---------|
| #35350 | CLOSED | **fix(plugins): use portable shebangs in shell scripts** — Replaced hardcoded `#!/bin/bash` with `#!/usr/bin/env bash` across 11 plugin scripts. Fixes NixOS and non-standard-path environments. *Partial fix in #11029.* |

No other PRs were updated in the last 24 hours.

---

## 5. Feature Request Trends

1. **Per-agent context compaction** (#90347, #90862): Users running delegated subagents need independent compaction thresholds per agent role — one boundary for the coordinator session, another for child subagents — to prevent early context truncation on long-running coding tasks.

2. **Subagent resilience on transient failures** (#78224): Pause-and-resume semantics for background subagents hit by rate limits, API errors, or quota exhaustion, rather than hard termination.

3. **Keyboard navigation & TUI polish** (#70678, #85603): Input-dropping bugs in tmux and missing keyboard shortcuts for chat navigation are top-of-mind for power users.

4. **Cross-session messaging under Remote Control** (#90890): When Remote Control is active, local inter-session `SendMessage` / `ListAgents` should continue to work — currently broken or silent.

---

## 6. Developer Pain Points

| Pain Point | Affected Platforms | Frequency |
|------------|-------------------|-----------|
| **Session loss on auto-update** (#90172 umbrella) | Windows, macOS | 🔥🔥🔥 |
| **Max quota leak** (#38335) | All | 🔥🔥🔥 |
| **Windows Desktop always-on-top / CoworkVMService permissions** (#85891, #85840, #89711) | Windows 11 | 🔥🔥 |
| **TUI input loss in tmux** (#85603) | macOS | 🔥 |
| **Nested subagent notification failures** (#75043) | macOS (Opus/Fable) | 🔥 |
| **Linux reaper false positives** (#78674) | Linux | 🔥 |
| **Process leaks on scheduled-task completion** (#89859, #90889) | Windows, macOS | 🔥 |
| **MCP nested-param serialization** (#87361, #88882) | Windows, macOS | 🔥 |
| **CLI hangs headless on Linux** (#90800) | Linux (native + npm) | 🔥 |
| **Model-role marker leakage mid-turn** (#90893, #90894) | All | 🔥 |

The dominant theme this week is **stability regressions from the recent auto-update cycle** (ShipIt), compounded by a persistent **Max quota accounting bug** that has been open since March. Both require urgent engineering attention.

---

*Data source: [github.com/anthropics/claude-code](https://github.com/anthropics/claude-code) · Generated 2026-08-31*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-31

## 1. Today's Highlights

The Codex team shipped three alpha releases (0.152.0-alpha.4 through alpha.6) in the past 24 hours, signaling active iteration on the Rust client. The community's top concern remains Windows desktop stability, with multiple reports of handshake failures, unresponsive UI elements, and session-management bugs. On the feature front, the team is advancing rate-limit transparency in the TUI, making `update_plan` opt-in by default, and broadening MCP server name support to include package-style identifiers.

## 2. Releases

Three alpha releases landed in the Rust repository within the last day:

- **[0.152.0-alpha.6](https://github.com/openai/codex/releases/tag/rust-v0.152.0-alpha.6)** — Latest alpha; incremental release with no changelog details published yet.
- **[0.152.0-alpha.5](https://github.com/openai/codex/releases/tag/rust-v0.152.0-alpha.5)** — Mid-cycle alpha in the 0.152 series.
- **[0.152.0-alpha.4](https://github.com/openai/codex/releases/tag/rust-v0.152.0-alpha.4)** — Earliest of the three; marks the start of the current alpha train.

No full stable release was published in this window.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#38350](https://github.com/openai/codex/issues/38350) | Recurring scheduled tasks disable themselves after successful runs | Scheduled automation is a core workflow feature; self-disabling tasks break reliability for any user relying on codex web cron jobs. | 57 comments; high frustration over lack of authorization signal. |
| [#39903](https://github.com/openai/codex/issues/39903) | Add option to disable "Ran N commands" collapsing | Transparency into executed commands is essential for auditability and debugging; current collapsing hides detail users need. | 51 comments; 70 👍 — strongest thumbs-up of the period. |
| [#41049](https://github.com/openai/codex/issues/41049) | Code-mode host exits during handshake on Windows | Handshake failures block the entire coding loop; this is a blocking bug for Windows desktop users on the 5.6 model. | 41 comments; reported on Pro 20x. |
| [#33685](https://github.com/openai/codex/issues/33685) | Weekly limit draining faster than expected | Rate-limit accounting directly affects paid users; a perceived mismatch between expected and actual consumption erodes trust. | 31 comments; 17 👍; ongoing since July. |
| [#40968](https://github.com/openai/codex/issues/40968) | Send button spins forever on Windows desktop | A UI-level blocker that prevents any follow-up prompt from submitting; closed but symptomatic of deeper input-handling issues. | 17 comments; 4 👍 |
| [#41290](https://github.com/openai/codex/issues/41290) | Project creation/removal fails after switching to WSL on Windows | Cross-environment switching is a common workflow; failures here break project lifecycle management entirely. | 17 comments; 7 👍 |
| [#34652](https://github.com/openai/codex/issues/34652) | File-edit approval buttons unresponsive in Remote SSH | Remote workflows are a growing use case; approval dead buttons make safe code execution impossible over SSH. | 13 comments |
| [#39823](https://github.com/openai/codex/issues/39823) | Session resume fails with "already has an active writer" | Session continuity is critical for long-running workflows; this error wedges users out of their own sessions. | 11 comments |
| [#24453](https://github.com/openai/codex/issues/24453) | Windows `command_execution` does not emit PreToolUse hooks | Hook systems are the foundation of custom automation and governance; silent failures on Windows undermine the entire extension model. | 9 comments; long-open since May. |
| [#25317](https://github.com/openai/codex/issues/25317) | Windows + WSL shell stays poisoned after reboot | A regression on a known issue (#22185); stale helper paths persist across restarts, requiring manual cleanup. | 9 comments; 3 👍 |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#41744](https://github.com/openai/codex/pull/41744) | Make the `update_plan` tool opt-in | ✅ Closed | Defaults `tools.update_plan.enabled` to `false`; removes bundled guidance from model, collaboration, multi-agent, compaction, prewarm, and goal-continuation prompts. Users must explicitly enable it. |
| [#41743](https://github.com/openai/codex/pull/41743) | Mark history ingestion requests in turn metadata | ✅ Closed | Sets `history_ingest_requested: true` in Responses turn metadata when the history-notes token-budget extension is active; reserves the key against caller override. |
| [#41742](https://github.com/openai/codex/pull/41742) | Show actionable rate-limit banners in the TUI | ✅ Closed | Carries backend-owned banner data through `account/rateLimits/read`, filters by authenticated account, and renders supported notices above the composer. |
| [#41700](https://github.com/openai/codex/pull/41700) | Support package-style MCP server names | ✅ Closed | Allows `:`, `@`, `/`, and `.` in MCP server names (e.g., `npm:@modelcontextprotocol/server-sequential.thinking`); preserved across `mcp add/get/list/remove`, runtime namespaces, and OAuth. |
| [#41683](https://github.com/openai/codex/pull/41683) | Set working directories for environment MCP tests | ✅ Closed | Explicitly sets fixture workspace as `cwd` for environment-backed stdio MCP servers, which lack a host-local fallback. |
| [#41673](https://github.com/openai/codex/pull/41673) | Repair cursor-style rendering on older JediTerm terminals | ✅ Closed | Applies cursor-style commands at a terminal-owned glyph to avoid older JediTerm versions overwriting the glyph beneath a `DECSCUSR` space intermediate. |
| [#41666](https://github.com/openai/codex/pull/41666) | Approve first Node REPL execution without Guardian wait | ✅ Closed | Fast-approves the initial `js` execution from a Node REPL-backed server while its async Guardian classification completes in parallel. |
| [#41660](https://github.com/openai/codex/pull/41660) | Preserve Guardian authorization across history compaction | ✅ Closed | Prevents compaction and host-injected context from being treated as authorization changes, so valid Guardian reviews are reused after history shifts. |
| [#41630](https://github.com/openai/codex/pull/41630) | Update tests for default-enabled `update_plan` | ✅ Closed | Covers default, explicitly enabled, and explicitly disabled states; verifies prompt tool-list consistency across custom base and developer instructions. |
| [#41613](https://github.com/openai/codex/pull/41613) | Move Vim history tests into the history search module | ✅ Closed | Relocates Vim history-navigation tests alongside the history search implementation; shares the human-like typing test helper with the nested module. |

## 5. Feature Request Trends

- **Transparency & auditability** — Users consistently want full visibility into command execution (#39903), rate-limit state (#41742), and plan updates (#41744). The trend points toward a demand for "explainable" AI coding sessions.
- **Automation reliability** — Recurring scheduled tasks (#38350), session resumption (#39823), and hook emission (#24453) all reflect a growing user base building autonomous workflows that need dependable execution guarantees.
- **MCP ecosystem expansion** — Package-style server names (#41700) and environment-backed test fixtures (#41683) show the community is pushing MCP beyond simple local servers into registry-style distributions and CI-friendly configurations.
- **Cross-platform parity** — Windows-specific bugs dominate the issue tracker, but the feature requests (WSL switching, Remote SSH approval, hook support) indicate users expect feature parity across Linux, macOS, and Windows, including WSL and remote environments.

## 6. Developer Pain Points

1. **Windows desktop instability** — Over half of the top issues by comment count are Windows-specific: handshake failures (#41049, #40913), unresponsive send buttons (#40968), blocked project lifecycle after WSL switches (#41290), and click-through pets (#41513, #41513). This is the single largest source of developer frustration.
2. **Session management fragility** — Multiple reports of session resume failures (#39823), overlapping ordinal sequences wedging UI state (#41353), and stale writer locks suggest the session layer needs robustness improvements.
3. **Rate-limit accounting opacity** — Users report weekly limits draining faster than expected (#33685) and 5-hour limits vanishing after minimal use (#19944), pointing to a trust gap around how usage is calculated and communicated.
4. **Windows hook system gaps** — `PreToolUse` hooks silently fail to fire for `command_execution` on Windows (#24453), undermining the extension and governance models that power teams relying on custom automation.
5. **Remote SSH approval dead spots** — File-edit approval buttons become unresponsive in Remote SSH conversations (#34652), forcing users back to CLI for safe execution and breaking the desktop workflow for remote developers.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026‑08‑31

## 1. Today's Highlights
Gemini CLI v0.59.0‑nightly.20260831 was released, bringing a fresh set of nightly builds. The community is actively addressing critical agent‑reliability issues, particularly around sub‑agent recovery and generalist‑agent hangs, while several merged PRs improve core robustness for non‑interactive workflows and cross‑platform paste handling.

## 2. Releases
**v0.59.0‑nightly.20260831.g0bd1d4397**  
Daily nightly build with ongoing improvements.  
🔗 [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260830.g0bd1d4397...v0.59.0-nightly.20260831.g0bd1d4397)

## 3. Hot Issues
| Issue | Summary | Why It Matters | Community Reaction |
|-------|---------|----------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Sub‑agents silently mark tasks complete even when they hit the turn limit, masking incomplete work and breaking multi‑agent workflows. | 13 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs forever | The generalist agent can deadlock on simple operations (e.g., folder creation), forcing manual cancellation. | 8 comments, 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model’s bash affinity via zero‑dependency OS sandboxing | Proposes tapping into the model’s native bash skills while preserving security and UX, a key direction for agent‑driven tooling. | 8 comments, 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess impact of AST‑aware file reads, search, and mapping | AST‑aware tools could dramatically reduce token waste and improve navigation accuracy for code‑base investigations. | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub‑agents enough | Users report that custom skills and sub‑agents are ignored unless explicitly invoked, reducing the value of the agent‑orchestration layer. | 6 comments, 0 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | Auto Memory sends raw transcripts to the model before redaction, risking secret exposure and noisy logs. | 5 comments, 0 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck after completion | Simple CLI commands can leave the agent in a permanent “awaiting input” state, breaking automated workflows. | 4 comments, 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser‑agent resilience with session takeover | The browser agent currently fails fast on locked profiles; automatic takeover would improve reliability in persistent‑session scenarios. | 4 comments, 0 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | A platform‑specific bug that breaks browser automation for Linux users running Wayland. | 4 comments, 1 👍 |
| [#21000](https://github.com/google-gemini/gemini-cli/issues/21000) | Experiment with native file tools for task tracker | Exploring whether core file tools can replace the existing task‑tracking mechanism, simplifying the agent’s internals. | 4 comments, 0 👍 |

## 4. Key PR Progress
| PR | Summary | Type |
|----|---------|------|
| [#26848](https://github.com/google-gemini/gemini-cli/pull/26848) | Allow IPv6 loopback (`[::1]`) in IDE‑companion Host‑header validation. | Security fix |
| [#26905](https://github.com/google-gemini/gemini-cli/pull/26905) | Synthesize bracketed‑paste markers for multi‑line pastes on Windows Terminal/PowerShell/WSL2. | Core fix |
| [#26907](https://github.com/google-gemini/gemini-cli/pull/26907) | Remove redundant double‑quote wrapping around the session‑resume tip. | Core polish |
| [#26914](https://github.com/google-gemini/gemini-cli/pull/26914) | Include `gemini‑2.5‑flash‑lite` in the default fallback chain when Pro/Flash quotas are exhausted. | Core improvement |
| [#26930](https://github.com/google-gemini/gemini-cli/pull/26930) | Restore the previous extension on failed update to avoid leaving the user with no working extension. | Extensions reliability |
| [#26932](https://github.com/google-gemini/gemini-cli/pull/26932) | Handle `refreshAuth` rejection in the non‑interactive prompt path, preventing unhandled promise rejections. | Auth/CLI stability |
| [#26931](https://github.com/google-gemini/gemini-cli/pull/26931) | Deep‑merge user and workspace settings in the A2A server, preventing silent loss of nested configuration. | A2A server fix |
| [#29132](https://github.com/google-gemini/gemini-cli/pull/29132) | Normalize CRLF/CR line endings before computing diff context snippets, fixing diff rendering on Windows. | Core fix |
| [#28834](https://github.com/google-gemini/gemini-cli/pull/28834) | Suppress spurious `ENOENT` warnings for transient sub‑directories during workspace scans. | Core warning cleanup |
| [#28835](https://github.com/google-gemini/gemini-cli/pull/28835) | Skip the user‑agents directory when the workspace is the home directory, eliminating duplicate‑agent warnings. | Core warning cleanup |

## 5. Feature Request Trends
- **Agent‑orchestration reliability**: Strong interest in fixing sub‑agent hang, recovery, and skill‑usage issues (#21409, #22323, #21968).
- **AST‑aware code exploration**: Community proposes leveraging parse‑tree information for more precise file reads and navigation (#22745, #22746).
- **Security‑conscious memory**: Demand for deterministic redaction and reduced logging in Auto Memory to prevent secret exposure (#26525, #26523, #26522).
- **Cross‑platform polish**: Continued effort on Windows paste handling, line‑ending normalization, and Wayland browser‑agent support (#26905, #29132, #21983).
- **Quota‑resilient fallback**: Automatic fallback to lighter models when primary quotas are exhausted (#26914).

## 6. Developer Pain Points
- **Agent hangs and false completions**: Generalist and sub‑agents frequently deadlock or report success when they actually hit turn limits, breaking automated workflows.
- **Stuck shell execution**: Simple CLI commands can leave the terminal in an “awaiting input” state indefinitely (#25166).
- **Authentication errors in non‑interactive mode**: Transient network failures during `refreshAuth` crash the CLI with raw stack traces instead of a clean error (#26932, #28848).
- **Spurious warnings**: Duplicate‑agent warnings and `ENOENT` noise clutter the output, especially when working in the home directory (#28834, #28835).
- **Quota exhaustion**: Users on the free tier are forced to manually specify fallback models when default quotas are consumed (#26914).
- **Browser‑agent fragility**: The browser agent fails fast on locked profiles and does not respect `settings.json` overrides (#22232, #22267).

---
*Digest generated from GitHub data for google‑gemini/gemini‑cli on 2026‑08‑31.*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-31

## 1. Today's Highlights

GitHub Copilot CLI 1.0.81 introduced a significant regression: OAuth authentication fails for users behind TLS-inspecting corporate proxies, with device-code and web flows both breaking during `create_session` ([#4671](https://github.com/github/copilot-cli/issues/4671)). Meanwhile, a critical runaway `FileWatch` host-event loop continues to draw attention for freezing the TUI and inflating debug logs up to 13 GB ([#4612](https://github.com/github/copilot-cli/issues/4612)). On the feature side, the community pushed for auto-reloading plugin skills after installation, which has been addressed ([#3606](https://github.com/github/copilot-cli/issues/3606) — closed).

---

## 2. Releases

No new releases were published in the last 24 hours. The latest tracked version is **1.0.81**.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#1285](https://github.com/github/copilot-cli/issues/1285) | Organisation level Agent not showing up | Enterprise users cannot discover org-scoped agents in the CLI or VS Code, blocking multi-team deployments. | 9 👍 · 8 comments |
| [#4612](https://github.com/github/copilot-cli/issues/4612) | Runaway FileWatch host-event loop freezes TUI | Long-running sessions enter a tight loop that halts the terminal UI and can grow debug logs to 13 GB. | 1 👍 · 8 comments |
| [#3978](https://github.com/github/copilot-cli/issues/3978) | CLI incorrectly switches back to previous model after BYOK switch | Session state is lost on resume — BYOK configuration is overridden, breaking cost-control workflows. | 4 👍 · 1 comment |
| [#2369](https://github.com/github/copilot-cli/issues/2369) | Unable to perform basic scrolling to view long results **[CLOSED]** | Long outputs were unreadable with no scroll support via mouse, touch, or keyboard. | 4 👍 · 3 comments |
| [#2861](https://github.com/github/copilot-cli/issues/2861) | Compaction failed: received empty response from model | Manual `/compact` on Opus 4.6 fails with empty responses across 3 retries, degrading long-session stability. | 3 👍 · 2 comments |
| [#4664](https://github.com/github/copilot-cli/issues/4664) | JavaScript heap OOM when resuming a long session | Fatal V8 crash prevents users from ever resuming large prior sessions — a blocking reliability issue. | 0 👍 · 1 comment |
| [#4594](https://github.com/github/copilot-cli/issues/4594) | Custom agent `web`/`search` aliases bind zero tools silently | Agents declared with documented category aliases lose all web and file search at runtime with no error. | 1 👍 · 1 comment |
| [#4671](https://github.com/github/copilot-cli/issues/4671) | 1.0.81 regression: OAuth login fails behind TLS-inspecting proxy | Corporate proxy users cannot authenticate at all in 1.0.81; 1.0.80 works — a clear regression. | 0 👍 · 0 comments |
| [#4646](https://github.com/github/copilot-cli/issues/4646) | Compaction fails with "Tool choice must be auto" on custom models | Custom OpenRouter models (e.g. `~z-ai/glm-latest`) cannot compact, causing context overflow on long sessions. | 0 👍 · 1 comment |
| [#4665](https://github.com/github/copilot-cli/issues/4665) | `sessionStart` additionalContext duplicated on each turn | Hook-injected context is reinjected every turn, inflating token counts and AIC usage unintentionally. | 0 👍 · 0 comments |

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **Plugin & skills auto-loading** — Users want newly installed plugin skills to be immediately available without requiring a manual `/skills reload` ([#3606](https://github.com/github/copilot-cli/issues/3606), closed).
- **Enterprise agent discoverability** — Org-scoped agents should surface reliably in both CLI and IDE extensions ([#1285](https://github.com/github/copilot-cli/issues/1285)).
- **BYOK session persistence** — Model selection and BYOK configuration should survive session resume across CLI restarts ([#3978](https://github.com/github/copilot-cli/issues/3978)).
- **Telemetry configurability** — Custom `telemetry.headers` and server-managed settings should not silently suppress OTEL export ([#4169](https://github.com/github/copilot-cli/issues/4169), [#4669](https://github.com/github/copilot-cli/issues/4669)).
- **Account identity display** — Users want consistent hostname display across GitHub.com, GHES, and `gh`-loaded identities in the CLI footer ([#4666](https://github.com/github/copilot-cli/issues/4666)).
- **Custom model compaction support** — The compaction pathway should correctly pass `tool_choice: auto` for non-default model providers ([#4646](https://github.com/github/copilot-cli/issues/4646)).

---

## 6. Developer Pain Points

- **Memory & stability** — Heap OOM on session resume ([#4664](https://github.com/github/copilot-cli/issues/4664)) and runaway FileWatch loops consuming gigabytes of disk ([#4612](https://github.com/github/copilot-cli/issues/4612)) are the most severe reliability blockers.
- **Authentication regressions** — OAuth breaks behind TLS-inspecting proxies in 1.0.81 ([#4671](https://github.com/github/copilot-cli/issues/4671)) and Remote ADO MCP servers fail with WAM auth errors ([#4660](https://github.com/github/copilot-cli/issues/4660), closed), affecting enterprise users disproportionately.
- **Silent tool failures** — Custom agent tool aliases (`web`, `search`) silently bind zero tools with no diagnostic ([#4594](https://github.com/github/copilot-cli/issues/4594)), and extension tool calls hang indefinitely after startup failures ([#4670](https://github.com/github/copilot-cli/issues/4670)).
- **Session state drift** — Compaction errors on custom models ([#2861](https://github.com/github/copilot-cli/issues/2861), [#4646](https://github.com/github/copilot-cli/issues/4646)), duplicated `sessionStart` context ([#4665](https://github.com/github/copilot-cli/issues/4665)), and stale `create_session` callbacks ([#4668](https://github.com/github/copilot-cli/issues/4668)) all cause unexpected token burn and lost work.
- **Terminal rendering gaps** — Scrolling long output ([#2369](https://github.com/github/copilot-cli/issues/2369), closed) and inconsistent prompt box layouts across `cmd` tabs on Windows ([#3797](https://github.com/github/copilot-cli/issues/3797), closed) highlight ongoing UX friction in the TUI layer.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-31

---

## 1. Today's Highlights

Two open issues surfaced in the last 24 hours on the Kimi Code CLI repo, both affecting version 0.39.1. The first highlights a model behavior inconsistency where the K3-256k model emits Read tool calls despite text output indicating a Write intent. The second reports a Remote Control login failure on iPadOS 16.6 when accessed via Safari or WeChat, pointing to cross-platform compatibility gaps.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Hot Issues

**#2628 — Model emits Read tool calls instead of Write/Edit (0.39.1, k3-256k)**
- **Author:** 776138506 | **Created:** 2026-08-30 | **Comments:** 0 | 👍 0
- [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2628)
- **Why it matters:** This is a tool-calling consistency bug where the model's textual intent ("calling Write") diverges from the actual tool dispatched (Read). For a developer-facing CLI, such misalignment can silently produce incorrect file operations or block intended edits. It specifically affects the `kimi-code/k3-256k` model, raising concerns about reliability in production workflows.
- **Community reaction:** No reactions or comments yet — early reporting.

**#2627 — Remote Control login fails on iPadOS 16.6 (Safari/WeChat)**
- **Author:** VBS-you | **Created:** 2026-08-30 | **Comments:** 0 | 👍 0
- [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2627)
- **Why it matters:** Remote Control is an experimental feature (`KIMI_CODE_EXPERIMENTAL_REMOTE_CONTROL`) enabling cloud-connected development sessions. A login failure on a widely used mobile OS (iPadOS) with common browsers (Safari, WeChat WebView) limits accessibility for developers working across devices. The error message "无法开始登录" (Unable to start login) suggests a client-side handoff or OAuth redirect issue.
- **Community reaction:** No reactions or comments yet — early reporting.

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

Based on the current issue landscape:

- **Tool-call accuracy & consistency:** The Read/Write mismatch in #2628 signals a recurring pattern where model output intent and executed tool calls are not synchronized. Users are implicitly requesting better alignment guarantees from the K3-256k model layer.
- **Cross-platform Remote Control support:** #2627 highlights that the experimental Remote Control feature needs broader device and browser compatibility, especially for mobile and embedded WebView environments.
- **Mobile-first access:** The iPadOS issue underscores demand for functional mobile access to Kimi Code CLI features, not just desktop.

---

## 6. Developer Pain Points

- **Model reliability on tool dispatch:** Developers depend on the CLI to faithfully execute file edits and writes. When the model says "Write" but dispatches "Read," it creates silent incorrectness — a high-severity pain point for code modification workflows.
- **Experimental feature stability:** Remote Control, despite being flagged experimental, is being actively used in production-like setups (Debian 12 + Alibaba Cloud ECS). Login failures on mobile clients represent a friction point for developers who rely on cross-device access.
- **Version fragmentation:** Both issues report on version 0.39.1, suggesting that even within a single release, edge-case bugs in model behavior and platform compatibility persist without quick patch cycles.

---

*Digest generated from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) data as of 2026-08-31.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

⚠️ Summary generation failed.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-31

## 1. Today's Highlights

Pi 0.84.x continues to see active bug-fixing around session management, provider integrations, and extension API stability. The most visible developments this cycle are the DeepSeek V4 migration to the OpenAI Responses API, a fix for JSONL corruption on duplicate session opens, and ongoing work stabilizing the extension ecosystem after keybinding and WebSocket lifecycle regressions surfaced in recent releases.

## 2. Releases

**No new releases** were published in the last 24 hours.

## 3. Hot Issues

1. **#7547 — How do you use Pi on Windows? What issues are you seeing?** [OPEN, 51 comments, 2 👍]
   The canonical Windows-user voice thread. The maintainer is gathering field reports to decide where to concentrate documentation and bug-fix effort versus delegating to extensions. High community engagement makes this a priority signal.
   <https://github.com/earendil-works/pi/issues/7547>

2. **#8746 — 0.84.3 keeps reasoning in every message; sessions OOM at 20 GB+ with subagents** [CLOSED, 4 comments]
   A regression in 0.84.3 caused the kernel OOM killer to terminate Pi daily. Both parent sessions and subagent children were affected, pointing to a memory leak or unbounded reasoning accumulation introduced in that release.
   <https://github.com/earendil-works/pi/issues/8746>

3. **#8852 — JSONL session opened twice writes duplicate seq and corrupts the file** [CLOSED, 3 comments]
   `JsonlSessionRepo.open()` returned a fresh `SessionState` per call, so opening the same file twice from one process produced two `seq: 1` entries and silently corrupted the log. Serialization of writable opens is now required.
   <https://github.com/earendil-works/pi/issues/8852>

4. **#4748 — pi-tui `getKeybindings()` singleton breaks extensions** [OPEN, 6 comments, 2 👍]
   Extensions loaded from their own `node_modules` resolve a separate copy of `pi-tui`, so the module-local `globalKeybindings` singleton never receives the host's `setKeybindings(merged)` call. Hints render as empty `( to expand)`.
   <https://github.com/earendil-works/pi/issues/4748>

5. **#8864 — Long sessions die unrecoverably via contextWindow death spiral** [CLOSED, 2 comments]
   When a session's context estimate exceeds `contextWindow`, `clampMaxTokensToContext()` silently sends `max_tokens: 1`, the model returns one token, and the estimate anchors on that tiny response — locking the session into a permanent failure loop.
   <https://github.com/earendil-works/pi/issues/8864>

6. **#8845 — Branch summarization deterministically fails (maxTokens hardcoded to 2048)** [OPEN, 2 comments]
   `generateBranchSummary` pins the LLM call to 2048 tokens regardless of branch size, so any branch larger than what fits in that budget fails with "summary is incomplete." Users of `/tree` summarization are blocked.
   <https://github.com/earendil-works/pi/issues/8845>

7. **#8849 — Anthropic prompt cache never reads the transcript back** [CLOSED, 2 comments]
   `cacheRead` stays flat at the system+tools prefix for the entire session while `cacheWrite` increments every turn, meaning users pay full price on every request instead of benefiting from Anthropic's prompt caching.
   <https://github.com/earendil-works/pi/issues/8849>

8. **#8854 — System prompt bloat from third-party promptGuidelines (pi-prompt-diet)** [CLOSED, 2 comments]
   Power users installing 8–15 packages see their system prompt swollen by multi-paragraph `promptGuidelines` injections. The community is discussing a "diet" approach to trim or deduplicate accumulated guidelines.
   <https://github.com/earendil-works/pi/issues/8854>

9. **#8877 — read tool normalizes U+202F and breaks localized macOS screenshot paths** [CLOSED, 2 comments]
   Pi's `read` tool converts narrow no-break spaces (`U+202F`) to regular spaces before filesystem access, causing ENOENT on macOS screenshots with localized names. An uncovered variant of the older #1078 path-normalization bug.
   <https://github.com/earendil-works/pi/issues/8877>

10. **#8860 — `pi -e npm:<ext>@latest` does not refresh cached extensions** [CLOSED, 2 comments]
    Pi installs an extension once into its package directory and reuses it forever; appending `@latest` is ignored. Developers iterating on extensions via `-e` are forced into manual cache clearing.
    <https://github.com/earendil-works/pi/issues/8860>

## 4. Key PR Progress

1. **#8876 — Tencent Token Plan Individual provider** [CLOSED]
   Adds a new provider for tc-code-latest, DeepSeek V4 flash/pro, GLM-5.2, and MiniMax M2.7 via Tencent's LKEAP endpoint, keyed on `TENCENT_TOKEN_PLAN_API_KEY`.
   <https://github.com/earendil-works/pi/pull/8876>

2. **#8873 — Serve DeepSeek V4 through the OpenAI Responses API** [CLOSED]
   Migrates `deepseek-v4-flash`, `deepseek-v4-pro`, and `vision-exp` from the legacy Completions API to the Responses API, aligning with upstream model endpoint changes.
   <https://github.com/earendil-works/pi/pull/8873>

3. **#8853 — Prevent duplicate JSONL writers** [CLOSED]
   Serializes writable opens by canonical session path; a new writable open supersedes older in-process writers, which now fail before sequence allocation. Read-only loads and forks preserve ownership. (Fixes #8852)
   <https://github.com/earendil-works/pi/pull/8853>

4. **#8872 — Expose host keybinding access on the extension API** [CLOSED]
   Fixes #4748 by giving extensions a way to read the host's merged keybindings instead of resolving a private `pi-tui` copy with a stale singleton.
   <https://github.com/earendil-works/pi/pull/8872>

5. **#8866 — Unref Codex WebSocket idle-cache timer; document session cleanup** [CLOSED]
   Resolves #8868 — a lingering Codex WebSocket kept `pi -p` processes alive for ~5 minutes after the final answer. The timer is now unreffed and extension-side resource cleanup is documented.
   <https://github.com/earendil-works/pi/pull/8866>

6. **#8862 — Derive branch summary output budget from reserveTokens** [CLOSED]
   Fixes #8845 by replacing the hardcoded `maxTokens: 2048` with a dynamic budget calculated from `reserveTokens`, allowing large-branch summaries to succeed.
   <https://github.com/earendil-works/pi/pull/8862>

7. **#8635 — Preserve aborted stop reason during lazy setup** [OPEN]
   Passes the request abort signal through lazy stream setup wrappers and reports setup failures as aborted when the signal is already aborted. Covers abort-during-tool-execution race (#8409).
   <https://github.com/earendil-works/pi/pull/8635>

8. **#8871 — Preserve cache-field presence and provider-reported cost** [CLOSED]
   Fixes `openai-completions.ts` collapsing absent cache-token fields to `0` and discarding finite provider `usage.cost`, which downstream callers cannot distinguish from "zero cache use."
   <https://github.com/earendil-works/pi/pull/8871>

9. **#8869 — Configurable bash full-output directory** [CLOSED]
   Adds an optional `fullOutputDirectory` to `BashToolOptions` so SDK embedders using custom `BashOperations` can redirect truncated output instead of defaulting to `os.tmpdir()`.
   <https://github.com/earendil-works/pi/pull/8869>

10. **#8858 — Fix markdown-fenced tool-call arguments degrading to `{}`** [CLOSED]
    Models (and OpenAI-compatible gateways) that wrap `arguments` in a markdown code fence instead of bare JSON now have those fences stripped during accumulation, preventing silent argument loss.
    <https://github.com/earendil-works/pi/pull/8858>

## 5. Feature Request Trends

- **Extension API maturity** — Repeated asks for clean extension-host communication: keybinding access (#4748 / #8872), tool error classification (#8856), resource lifecycle docs (#8866 / #8868), and extension-level Skill visibility (#8533).
- **Provider expansion** — Community continues pushing for new built-in providers: Ollama Cloud (#4706), StepFun (#8867), Tencent Token Plan (#8876), and z.ai API (#6723).
- **Cost & caching transparency** — Users want accurate cache telemetry (#8849, #8871), correct token-cost reporting (#8875), and context-window alignment across providers (#8878).
- **Usability shortcuts** — Root-level effort switching (#2941), bash command descriptions in the TUI (#8863), and `pi list` version display (#8865) reflect demand for lighter-touch UX polish.
- **System prompt hygiene** — Bloat from accumulated `promptGuidelines` (#8854) is driving interest in a "diet" or dedup mechanism for the base system prompt.

## 6. Developer Pain Points

- **Session corruption & OOM** — Duplicate JSONL writes (#8852) and the 0.84.3 OOM regression (#8746) are the highest-impact bugs, directly threatening data integrity and long-running workflows.
- **Extension isolation breaking assumptions** — When extensions resolve their own copy of `pi-tui`, singleton state (keybindings, settings) diverges from the host (#4748). This is a structural pain point for the growing extension ecosystem.
- **Context management edge cases** — The `clampMaxTokensToContext` death spiral (#8864), hardcoded branch-summary budgets (#8845), and dangling `tool_use` after branching (#8859) all point to fragility in the request-assembly path under long or branched sessions.
- **Provider-compatibility quirks** — Markdown-fenced arguments (#8858), shared-stream-index drops (#8861), Unicode normalization in paths (#8877), and OpenRouter auto-endpoint shifts breaking encrypted reasoning (#8874) are recurring friction when Pi talks to non-canonical model endpoints.
- **Windows fragmentation** — Issue #7547 remains the open-ended pain point: too many ways to run Pi on Windows, with unclear ownership between core fixes and extension delegation.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-31

## 1. Today's Highlights

The community is energized by two major directions: **cross-session multi-agent messaging** (#8724) is gaining traction as a roadmap milestone, while a cluster of **security review findings** (#10560, #10561) has surfaced critical trust-boundary holes in the hook and git-execution pipelines. On the platform side, **Windows Computer Use driver panics** (#10538) and **Web Shell error opacity** (#10564) remain the most pressing bugs users are watching.

---

## 2. Releases

**No releases in the last 24 hours.** The nightly release `v0.22.3-nightly.20260830.413b6d15d3` (#10535) failed at the integration stage and was closed; the team is tracking the fix upstream.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#8124](https://github.com/QwenLM/qwen-code/issues/8124) | Startup banner sometimes missing top lines on first paint | Intermittent TUI rendering glitch affecting first-look experience; correlates with pending provider updates. 15 comments. |
| [#8724](https://github.com/QwenLM/qwen-code/issues/8724) | Cross-session messaging between local sessions | Roadmap-defining multi-agent feature: `list_agents` + `send_message` with fail-closed gates. 12 comments, actively in-progress. |
| [#8784](https://github.com/QwenLM/qwen-code/issues/8784) | Streamable HTTP: optional GET/SSE rejection kills MCP connection | MCP spec non-compliance — a server rejecting the optional notification stream drops the entire connection. Closed. |
| [#4441](https://github.com/QwenLM/qwen-code/issues/4441) | Cannot send images to WeChat bot (Windows path restriction) | Windows-specific file-path validation rejects legitimate paths outside allowed directories. Active since May. |
| [#10538](https://github.com/QwenLM/qwen-code/issues/10538) | Computer Use driver 0.20.0 panics on every embedded runtime creation (Windows x64) | Blocks the entire CUA feature on Windows; affects Node v24.18 + portable payload. |
| [#4016](https://github.com/QwenLM/qwen-code/issues/4016) | Encrypted storage for sensitive config (AES-256-GCM) | Addresses明文 storage of API keys/tokens in `settings.json` and `QWEN.md`; strong community demand for secure sync. |
| [#10603](https://github.com/QwenLM/qwen-code/issues/10603) | ToolSearch triggers full-prompt reprocessing (prefill) | Performance regression: llama.cpp console shows full prefill on `ToolSearch` calls instead of continuing from cache. Opened today. |
| [#10564](https://github.com/QwenLM/qwen-code/issues/10564) | Web Shell hides provider error details behind "Internal error" | Degraded debugging experience; the real JSON-RPC error is buried in `data`. Closed. |
| [#10560](https://github.com/QwenLM/qwen-code/issues/10560) | Probe/base-tree creation checkouts run before content filter | Security review follow-up: `worktree add` spawns execute un-screened, exposing potential path traversal. |
| [#10561](https://github.com/QwenLM/qwen-code/issues/10561) | Git config keys (fsmonitor, hooks) are open entrance sets | **P1 security** class finding — any git spawn can be hijacked via user-global config. Critical trust-boundary issue. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#10080](https://github.com/QwenLM/qwen-code/pull/10080) | Normalize tool schemas for grammar-based providers | Fixes empty-object grammar shapes sent to older llama.cpp backends; keeps full tool set enabled for OpenAI-compatible providers. |
| [#10602](https://github.com/QwenLM/qwen-code/pull/10602) | Bump browser daemon bundle budget to 216 KB | Unblocks CI: the SDK bundle had exceeded the 220 KB threshold, causing `npm install` to fail on main. |
| [#10489](https://github.com/QwenLM/qwen-code/pull/10489) | Persist WebShell model reasoning preferences | Reuses `model.reasoningEffort` to carry thinking-toggle state across daemon sessions; supports five effort tiers. |
| [#10534](https://github.com/QwenLM/qwen-code/pull/10534) | Restore native diff approval after WebShell cutover | Reconnects VS Code's Accept/Reject commands to WebShell permission diffs after the ACP→WebShell migration in #9811. |
| [#10589](https://github.com/QwenLM/qwen-code/pull/10589) | Web Shell Workspaces overview panel | Full-page table of all registered workspaces with badges (primary/untrusted), path, session counts, and MCP health. Layer B2 of #10399. |
| [#10390](https://github.com/QwenLM/qwen-code/pull/10390) | Unblock git update on dirty working tree | "Update Project" now presents a resolution panel (branch picker) instead of dead-ending on uncommitted changes. |
| [#10283](https://github.com/QwenLM/qwen-code/pull/10283) | Select output style via setting or CLI flag | Adds `general.outputStyle` config and `--output-style` flag, resolving the first way to pick from the styles shipped in #9565. |
| [#10427](https://github.com/QwenLM/qwen-code/pull/10427) | Close four trust-boundary holes in hook execution | Closes HTTP-hook redirect, local-file hook execution, and two other repository-controlled config→execution gaps. Reopen of #8396. |
| [#10597](https://github.com/QwenLM/qwen-code/pull/10597) | Raise ECS E2E ceiling from 60 → 90 min | Fixes flaky shared-ECS runner timeouts scoped to the `ecs-qwen` pool; hosted fallbacks remain at 60 min. |
| [#9590](https://github.com/QwenLM/qwen-code/pull/9590) | Provider-aware reasoning controls | Adds per-provider reasoning UI for DeepSeek V4, GLM 5.2, and Kimi — toggle-only hybrids, canonical effort tiers, and mandatory-thinking models. |

---

## 5. Feature Request Trends

1. **Multi-agent & cross-session communication** — #8724 (cross-session messaging), #9033 (workflow task exposure via daemon), and #8927 (session rotation per channel) all point to a community push toward persistent, interconnected agent workflows.
2. **Sandbox diversification** — #10583 proposes a lightweight Bubblewrap backend for Linux as an alternative to Docker/Podman, reflecting demand for sandbox modes that don't require a container runtime.
3. **Security & confidential storage** — #4016 (AES-256-GCM config encryption) and the cluster of security PRs (#10427, #10560, #10561) show sustained focus on reducing the attack surface around config files and hook execution.
4. **Configuration hot-reload** — #10568 requests model-config live-reload without CLI restart, citing Qoder CLI's existing support as a benchmark.
5. **Git worktree improvements** — #10584 requests `.worktreeinclude` support for copying gitignored files into worktrees, and #10226 adds optional worktree support for shell commands.

---

## 6. Developer Pain Points

- **Windows stability** — The Computer Use driver panic (#10538) and WeChat image-send path restriction (#4441) highlight ongoing Windows-specific friction in tooling and integration paths.
- **Web Shell error visibility** — Providers' real error messages are swallowed by generic "Internal error" text (#10564), making debugging turn failures difficult for both end-users and maintainers.
- **Performance regressions on tool calls** — `ToolSearch` triggering full prompt prefill (#10603) suggests the caching layer isn't correctly skipping reprocessing for certain tool classes, a concern for long-running sessions.
- **Bundle-size discipline** — The SDK bundle breach (#10602) that broke CI indicates the browser daemon is approaching budget limits; ongoing growth here will cause repeated release friction.
- **Security review velocity** — Multiple P1/P2 security findings (#10560, #10561, #10427) from the same review round suggest the hook/git-execution surface is a persistent vulnerability hotspot requiring sustained hardening effort.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-31

---

## 1. Today's Highlights

Today's activity is dominated by an active session-composer redesign in the Tideline family (PRs #5770, #5773, #5758), paired with a provider-catalog wiring fix (#5766) and session-resume correction (#5750). Meanwhile, the community flagged a high-severity sandbox regression (#5723) that blocks `sudo` in the agent shell, and a flaky test under parallel CI load (#5735) continues the ongoing reliability push.

---

## 2. Releases

No new releases were published in the last 24 hours. PR #5744 prepares the v0.9.12 source bump and CHANGELOG from merged PRs but notes: *"Do not merge until the founder cuts the release."*

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5316](https://github.com/Hmbown/DeepSeek-TUI/issues/5316) | EPIC-005: CodeWhale TUI Crate Decomposition | Umbrella tracking issue for the entire crate-split effort — every sub-EPIC and FEAT report lands here. 20 comments show sustained maintainer + community engagement. |
| [#5620](https://github.com/Hmbown/DeepSeek-TUI/issues/5620) | Context pressure warning is transient; agent does not react | Silent context degradation defeats a critical safety signal. Severity: Medium. Raised by `ronohara` — the same author behind several runtime reliability fixes. |
| [#4785](https://github.com/Hmbown/DeepSeek-TUI/issues/4785) | Dead-code sweep: 464 `#[allow(dead_code)]` hiding drift | **Closed.** Stripping these attributes revealed significant unused-code drift across 143 files. A landmark cleanup that improved compiler signal-to-noise. |
| [#4955](https://github.com/Hmbown/DeepSeek-TUI/issues/4955) | Zero-sandbox / `--no-sandbox` mode for local dev | **1 👍.** Kernel-level Seatbelt sandbox breaks basic shell commands daily. Users need an escape valve for trusted dev machines. |
| [#5723](https://github.com/Hmbown/DeepSeek-TUI/issues/5723) | Agent shell sets `NoNewPrivs`, blocking `sudo` | **High severity.** Blocks a previously-working production deployment workflow. Filed 2026-08-30 by `ronohara`. |
| [#1097](https://github.com/Hmbown/DeepSeek-TUI/issues/1097) | FreeBSD support | Community request for native FreeBSD binary/pkg paths — `npm install` currently fails. Open since May 2026. |
| [#5771](https://github.com/Hmbown/DeepSeek-TUI/issues/5771) | Active-session composer missing shared `[↑]` send geometry | The startup Tideline has a three-cell submit affordance; the live composer does not. Filed today. |
| [#5772](https://github.com/Hmbown/DeepSeek-TUI/issues/5772) | Provider selection should not implicit-adopt external CLI credentials | Picker can leak HOME/temp credential paths during metadata probes. Security + UX concern raised today. |
| [#5769](https://github.com/Hmbown/DeepSeek-TUI/issues/5769) | Network errors sometimes stop the engine | Agents halt on transient network failures. Linux Mint reporter; likely broader impact. Filed today. |
| [#5605](https://github.com/Hmbown/DeepSeek-TUI/issues/5605) | Flaky test under full-suite parallel load | Same class as #5735 — CI reliability regression not caused by recent code moves. Ongoing investigation. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#5773](https://github.com/Hmbown/DeepSeek-TUI/pull/5773) | Shared `[↑]` send hitbox for active composer | Restores the three-cell submit affordance in `ComposerWidget` so long drafts cannot erase it. Closes #5771. |
| [#5770](https://github.com/Hmbown/DeepSeek-TUI/pull/5770) | Compose Tideline startup into shared composer shell | Cherry-picks current-mark, startup, rounded-composer, quiet-boot, route-control, and responsive-rail into one reviewable branch. Closes #5768. |
| [#5766](https://github.com/Hmbown/DeepSeek-TUI/pull/5766) | Bind catalog and route resolution | Each compiled provider catalog is now bound to its exact `RouteResolver`; cache health is preserved only when explicit scope status is supplied. Closes #5755. |
| [#5760](https://github.com/Hmbown/DeepSeek-TUI/pull/5760) | Keep MCP boot detail out of chat | Moves per-server MCP boot detail out of the composer shell; footer remains the compact status surface, `/mcp` stays the detailed diagnostic. Closes #5759. |
| [#5765](https://github.com/Hmbown/DeepSeek-TUI/pull/5765) | Render truthful active Tideline rail | Adds the passive five-group Tideline session rail at 100/120-column thresholds, derives queued/running state once at the App boundary, and stops historic workflows masquerading as current. Closes #5764. |
| [#5763](https://github.com/Hmbown/DeepSeek-TUI/pull/5763) | Make topbar route segment interactive | Click or F3 on the painted route/model segment now opens the provider picker. Both entry points delegate to the same `/provider` apply path. Closes #5756. |
| [#5750](https://github.com/Hmbown/DeepSeek-TUI/pull/5750) | Engine adopts host session ID on resume | Fixes broken session resume: the engine was minting its own session ID instead of adopting the host's, causing resumed turns to land in a different session. |
| [#5747](https://github.com/Hmbown/DeepSeek-TUI/pull/5747) | Unified self-serve MCP/plugin auth | Introduces a synthetic `authenticate` tool, shared `/mcp login` + plugin login flow, and `invalid_grant` rotation handling. 354 TUI lib tests pass. |
| [#5749](https://github.com/Hmbown/DeepSeek-TUI/pull/5749) | Unix-socket transport + daemon/attach advertisement | Desktop Phase 0 foundation: daemon spawn → socket connect → round-trip → shutdown verified; socket permissions/traversal/stale-cleanup lens clean. |
| [#5752](https://github.com/Hmbown/DeepSeek-TUI/pull/5752) | Signed, versioned, cached facts channel (slice 1) | Supabase-backed cloud facts channel (model catalog deltas, provider defaults, release truth, announcements) served at `/api/facts/v1/<channel>`, consumed behind `[cloud_facts].enabled` (default OFF). |

---

## 5. Feature Request Trends

- **Provider diversity:** Multiple open requests for first-class provider integrations — Neuralwatt (#3751, non-token pricing), ZenMux (#1330, DeepSeek-V4-Pro & Flash), and generic OpenAI-compatible wire support for `responses`/`anthropic` modes (#5713).
- **MCP/ACP parity:** Issue #2535 requests ACP mode support for MCP tools, closing a gap where ACP can only chat without tool use.
- **Remote workbench consolidation:** A cluster of closed issues (#1984, #1989, #2968) shows sustained interest in unifying CNB/Lighthouse/Feishu flows, evaluating RustProxy tunnels, and adding self-hosted Mac targets via Apple's container runtime.
- **Sandbox flexibility:** The `--no-sandbox` request (#4955) reflects a growing need for dev-environment escape valves alongside the built-in Seatbelt sandbox.
- **Web-search coverage:** Issue #5681 (closed) extended provider-native web search to DeepSeek, Qwen, Kimi, Z.AI, and MiMo — a clear trend toward reducing reliance on separately configured search backends.

---

## 6. Developer Pain Points

1. **Sandbox breakage in production workflows** — `NoNewPrivs` (#5723) and the broader Seatbelt sandbox (#4955) are the most cited friction points. Users report daily breakage of basic shell commands and blocked `sudo` in deployment pipelines.
2. **CI flakiness under parallel load** — Two open issues (#5605, #5735) document tests that fail only in full-suite parallel execution, suggesting race conditions in `runtime_chat_relay` and `remote_control` that are hard to reproduce in isolation.
3. **Transient context-pressure signals** — Issue #5620 describes a safety mechanism (context pressure warning) that fires but the agent does not proactively act on, rendering the signal effectively silent.
4. **Dead-code wall obscuring drift** — While #4785 is closed, the 464 `#[allow(dead_code)]` attributes across 143 files illustrate a systemic maintainability cost that the sweep only partially addressed.
5. **Credential leakage in provider picker** — Issue #5772 flags that the provider selection UI can implicitly adopt external CLI credentials without explicit confirmation, raising both security and UX concerns.
6. **Network error handling** — Issue #5769 reports that transient network errors can halt the engine entirely, suggesting the retry/recovery logic needs hardening for unstable connections.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*