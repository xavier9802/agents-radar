# AI CLI Tools Community Digest 2026-08-29

> Generated: 2026-08-29 06:43 UTC | Tools covered: 10

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



# Cross-Tool AI CLI Comparison Report — 2026-08-29

## 1. Ecosystem Overview

The AI CLI tooling landscape in late August 2026 is characterized by rapid iteration cycles and a clear maturation phase: major vendors (Anthropic, OpenAI, GitHub, Google) are shipping stable releases while competing open-source and regional projects (Qwen, Pi, DeepSeek, OpenCode) close feature gaps. Enterprise reliability—particularly around auth, multi-workspace trust isolation, and Windows stability—dominates community frustration across nearly every tool. Security hardening (MCP guard coverage, OAuth persistence, dependency CVEs) and billing transparency have emerged as critical trust vectors.

## 2. Activity Comparison

| Tool | Issues (24h) | PRs (24h) | Release Status | Release Version |
|------|-------------|-----------|----------------|-----------------|
| **Claude Code** | 10 hot issues | 1 active PR | ✅ Shipped | v2.1.251 |
| **OpenAI Codex** | 10 hot issues | 10+ closed PRs | ✅ 5 alpha releases | v0.151.0-alpha.12 |
| **Gemini CLI** | N/A (digest focused) | Security PR wave | ✅ Shipped | v0.59.0-nightly |
| **GitHub Copilot CLI** | 22 issues filed | 1 PR | ✅ Shipped | v1.0.82-1 |
| **Kimi Code CLI** | 2 hot issues | 1 open PR | ⚠️ No new release | — |
| **OpenCode** | 10 hot issues | 8 PRs | ⚠️ No release | v2 beta in progress |
| **Pi** | 9 hot issues | 10+ PRs | ✅ Shipped | v0.84.4 |
| **Qwen Code** | 9 hot issues | 9 open PRs | ✅ Shipped | v0.22.3 |
| **DeepSeek TUI** | 6 hot issues | 8 PRs | ⚠️ In development | v0.9.12 (WIP) |
| **Grok Build** | — | — | ⚠️ No activity | — |

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **MCP security & consistency** | Claude Code, Gemini CLI, Kimi Code CLI, OpenCode | Security guards must apply uniformly across built-in and MCP tool calls; OAuth token persistence across restarts; org-policy-aware tool blocking |
| **Compaction & context budget control** | Pi, OpenCode, Qwen Code | Configurable compaction triggers, per-model reasoning-level control, proactive compaction before provider requests to prevent silent data loss |
| **Enterprise auth & data residency** | Claude Code, GitHub Copilot CLI, OpenAI Codex | Tenant-specific URL routing, policy-blocked MCP handling, CVP-approved org bypass of false-positive safety filters |
| **Session resume & lifecycle reliability** | Claude Code, GitHub Copilot CLI, OpenAI Codex, Pi | Stealth-restart session destruction, writer-state corruption after approval mode, hung resumption on Windows cold start |
| **Terminal/UI robustness** | Claude Code, OpenCode, Pi, Qwen Code | Narrow-terminal crash prevention, TUI event starvation during parallel subagent turns, Windows renderer stability |
| **Billing & quota transparency** | Kimi Code CLI, OpenCode, GitHub Copilot CLI | Per-turn cost breakdowns, cache-read amplification debugging, programmatic access to subscription usage data |
| **Local/custom model parity** | OpenCode, Pi, Qwen Code, DeepSeek TUI | Config consistency across built-in and OpenAI-compatible backends (temperature, tool args), vLLM/llama-server compatibility, per-model token caps |

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | GitHub Copilot CLI | Qwen Code | Pi | OpenCode | Gemini CLI | Kimi Code CLI | DeepSeek TUI |
|-----------|-------------|--------------|-------------------|-----------|-----|----------|------------|---------------|--------------|
| **Primary focus** | Enterprise agent workflows, subagent observability | Rust-native CLI rapid iteration, fault tolerance | GitHub-integrated workflows, enterprise auth | Web Shell maturity, multi-workspace daemons | Multi-provider flexibility, Bedrock integration | Open-source extensibility, local model workflows | Security hardening, workspace trust | Budget-conscious/Asian market users | Community-driven crate decomposition |
| **Target users** | Large orgs, CVP-compliant teams | Power CLI users, Rust ecosystem | GitHub Enterprise customers | Web-first developers, China-market | Multi-cloud/Bedrock users | Open-source contributors, self-hosted | Enterprise security-first orgs | Moonshot ecosystem users | Codewhale plugin ecosystem |
| **Technical approach** | Hook-based extensibility, Remote Con streaming | Model-catalog-driven behavior, aggressive alpha cadence | GitHub API-native, OAuth-first | Managed artifact sharing, session workflow cockpit | Extension lifecycle management, startup composer | Rust + Bun hybrid, QR multi-client pairing | Fail-closed trust enforcement | Python-based, MCP-centric | Rust crate decomposition, provider-native search |
| **Release cadence** | Weekly-stable, minor releases | Daily alpha sprint | Bi-weekly patch cycle | Weekly with Web Shell focus | Bi-weekly | Beta-phase, irregular | Nightly build cadence | Irregular, issue-driven | Milestone-driven (v0.9.12) |
| **Biggest risk** | Windows Desktop fragility | Windows post-update crash loops | Enterprise auth regression clusters | Local LLM compatibility breakage | Extension lifecycle ordering bugs | Renderer memory leaks | N/A (digest incomplete) | Billing opacity, dependency CVEs | CI fragility, dead-code accumulation |

## 5. Community Momentum & Maturity

**Most Active Communities (by issue volume & engagement):**
1. **GitHub Copilot CLI** — 22 issues in 24h, strong enterprise user base filing regressions
2. **Claude Code** — 164-comment enterprise trust issue (#84352), deep engagement on Windows and compliance
3. **OpenAI Codex** — 51-upvote Windows crash issue, 65-upvote TUI transparency request
4. **OpenCode** — 119-comment GPT latency issue, active PR contributors (Hona, kitlangton)

**Rapidly Iterating:**
- **OpenAI Codex** — 5 alpha releases in 24h signals an aggressive pre-stable cadence
- **Qwen Code** — 9 open PRs targeting Web Shell production readiness
- **Pi** — 10+ PRs in a single cycle (compaction fixes, Bedrock Mantle, artifact verification)
- **DeepSeek TUI** — Active crate decomposition and v0.9.12 milestone convergence

**Maturity Indicators:**
- **Claude Code** and **GitHub Copilot CLI** have the most enterprise-facing issue profiles (CVP compliance, data residency, org policy)
- **OpenCode** and **Pi** show signs of transitioning from beta to production (QR pairing, startup composer, artifact verification gate)
- **Grok Build** shows zero community activity, suggesting limited adoption or a closed ecosystem

## 6. Trend Signals

1. **MCP security is the new trust frontier.** Three tools (Gemini CLI, Kimi Code CLI, GitHub Copilot CLI) explicitly address MCP tool-call security gaps this cycle. Expect this to become a baseline requirement rather than a differentiator.

2. **Windows Desktop remains the universal weak point.** Claude Code (orphaned Job Objects, stealth-restart kills), OpenAI Codex (post-update startup loops, DWM leaks), and GitHub Copilot CLI (resume hangs) all report severe Windows-specific regressions. Any tool targeting cross-platform developers must treat Windows stability as a first-class concern.

3. **Compaction is moving from optional to critical infrastructure.** Pi's proactive pre-request compaction (#6879) and Qwen Code's per-model reasoning persistence (#10011) signal that session context management is no longer a backend concern—it directly impacts user trust and cost.

4. **Enterprise auth regressions are the #1 upgrade risk.** GitHub Copilot CLI's v1.0.81 broke GHEC data-residency flows; Claude Code's CVP orgs are hitting cyber-safeguard blocks. Developers should expect upgrade friction in multi-tenant or policy-restricted environments and demand explicit auth-path testing before adoption.

5. **Billing transparency will differentiate tools.** Kimi Code CLI's cache_read amplification bug (#2626) and OpenCode's $20/single-prompt incident (#34402) show that opaque costing erodes trust faster than any feature gap. Tools that expose per-turn cost breakdowns will gain enterprise credibility.

6. **Local model parity is a growing demand surface.** Four tools (OpenCode, Pi, Qwen Code, DeepSeek TUI) received issues this cycle specifically about custom/OpenAI-compatible backend config inconsistency. As local LLM adoption grows, this gap will widen into a competitive advantage for tools that close it.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-29 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

### #1 — `skill-creator` bug fixes (PRs #1298, #1099, #1050, #539)
**Functionality:** The skill-creator suite includes `run_eval.py`, `run_loop.py`, and validation scripts for authoring, evaluating, and improving skills.  
**Discussion highlights:** Three separate PRs converged on the same critical Windows bug — `run_eval.py` reports `recall=0%` universally due to pipe encoding, stream-reading, and `claude.cmd` invocation failures. Issue #556 has 7 upvotes and 12 comments confirming the bug across 10+ independent reproductions. PR #1298 attempts a comprehensive fix; PRs #1099 and #1050 address specific Windows pieces; PR #539 adds YAML quoting validation.  
**Status:** All **OPEN** — no PR merged yet.  
🔗 [#1298](https://github.com/anthropics/skills/pull/1298) · [#1099](https://github.com/anthropics/skills/pull/1099) · [#1050](https://github.com/anthropics/skills/pull/1050) · [#539](https://github.com/anthropics/skills/pull/539) · [Issue #556](https://github.com/anthropics/skills/issues/556)

---

### #2 — `claude-api` skill (PR #1607, Issue #1487)
**Functionality:** Bundled skill providing Claude API reference, model IDs, and usage patterns.  
**Discussion highlights:** PR #1607 marks four retired model IDs as deprecated. Issue #1487 reports a critical UX flaw: the skill eagerly injects ~156k tokens into context on first load, exhausting the window in a single tool call.  
**Status:** PR #1607 **OPEN**; Issue #1487 **OPEN**.  
🔗 [PR #1607](https://github.com/anthropics/skills/pull/1607) · [Issue #1487](https://github.com/anthropics/skills/issues/1487)

---

### #3 — Security namespace abuse (Issue #492)
**Functionality:** Not a skill — a security report. Community skills are being distributed under the `anthropic/` namespace, impersonating official skills and potentially tricking users into granting elevated permissions.  
**Discussion highlights:** 43 comments, 2 upvotes. Raised trust-boundary concerns about skill provenance and namespace governance.  
**Status:** **OPEN**.  
🔗 [Issue #492](https://github.com/anthropics/skills/issues/492)

---

### #4 — `mcp-builder` evaluation fix (PR #1602, Issue #1390)
**Functionality:** MCP (Model Context Protocol) builder skill with a Phase-4 evaluation harness.  
**Discussion highlights:** Issue #1390: `evaluation.py` silently fabricates tool-execution errors for every call against real MCP servers, scoring 0/N universally. PR #1602 addresses serialization, encoding, and script stability issues.  
**Status:** Both **OPEN**.  
🔗 [PR #1602](https://github.com/anthropics/skills/pull/1602) · [Issue #1390](https://github.com/anthropics/skills/issues/1390)

---

### #5 — `docx` / `pdf` fixes (PRs #541, #538, Issue #12)
**Functionality:** DOCX and PDF document manipulation skills.  
**Discussion highlights:** PR #541 fixes tracked-change `w:id` collisions with existing bookmarks causing document corruption. PR #538 corrects case-sensitive file references. Issue #12 reports whitespace reformatting that breaks DOCX readability in Word/LibreOffice.  
**Status:** All **OPEN**.  
🔗 [PR #541](https://github.com/anthropics/skills/pull/541) · [PR #538](https://github.com/anthropics/skills/pull/538) · [Issue #12](https://github.com/anthropics/skills/issues/12)

---

### #6 — `frontend-design` skill improvement (PR #210)
**Functionality:** Design-system and frontend development guidance skill.  
**Discussion highlights:** Revision for clarity and actionability — every instruction must be followable within a single conversation. 8 upvotes on the related Issue #202 calling for best-practice updates.  
**Status:** **OPEN**.  
🔗 [PR #210](https://github.com/anthropics/skills/pull/210) · [Issue #202](https://github.com/anthropics/skills/issues/202)

---

### #7 — `Hivemind` multi-agent orchestration (PR #1628)
**Functionality:** Delegates mechanical coding work to headless [opencode](https://opencode.ai) workers on free models, while Claude Code remains the sole planner/reviewer/merger.  
**Discussion highlights:** Addresses the core cost bottleneck — context is the scarce resource, not intelligence. Designed to let expensive-model context focus on coordination rather than execution.  
**Status:** **OPEN** (created 2026-08-21).  
🔗 [PR #1628](https://github.com/anthropics/skills/pull/1628)

---

### #8 — `testing-patterns` skill (PR #723)
**Functionality:** Comprehensive testing skill covering the Testing Trophy, AAA pattern, React component testing with Testing Library, edge cases, and testing philosophy.  
**Status:** **OPEN**.  
🔗 [PR #723](https://github.com/anthropics/skills/pull/723)

---

## 2. Community Demand Trends

| Trend | Evidence |
|---|---|
| **Workflow & orchestration automation** | `Hivemind` (PR #1628) for multi-agent delegation; `compact-memory` (Issue #1329) for state compression in long-running agents |
| **Reasoning quality & self-audit** | `self-audit` skill (PR #1367) with mechanical verification + four-dimension reasoning gate; Issue #1385 proposes a full calibration → adversarial review → delivery pipeline |
| **Enterprise / platform skills** | `servicenow` (PR #568, 8+ comments), `scnet-hpc` (PR #1615) for HPC clusters, `odt` (PR #486) for OpenDocument — demand for domain-specific productivity skills |
| **Meta-tooling & skill quality** | `skill-quality-analyzer` + `skill-security-analyzer` (PR #83) for evaluating skill quality across five dimensions; Issue #228 for org-wide skill sharing |
| **Document fidelity** | Persistent demand for correct DOCX/PDF/ODT handling — three open fix PRs and an unresolved Issue #12 on formatting |
| **Cross-platform compatibility** | Windows subprocess/encoding bugs are a recurring pain point across `skill-creator`, `mcp-builder`, and evaluation scripts |

---

## 3. High-Potential Pending Skills

These active PRs have clear scope, community interest, and are close to landing:

| PR | Skill | Why it's promising |
|---|---|---|
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** — zero-cost multi-agent orchestration | Solves a top-of-mind cost problem; novel architecture using free-model workers |
| [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** — HPC cluster operations | Fills a niche (HPC/Slurm) with no existing coverage; profile-based SSH workflows |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** — mechanical verification + reasoning quality gate | Universal applicability across all projects/stacks; addresses quality assurance gap |
| [#568](https://github.com/anthropics/skills/pull/568) | **servicenow** — enterprise platform skill | Broadest single skill proposed (ITSM, ITOM, SecOps, FSM, CSDM, IntegrationHub); 8+ comments, active since March |
| [#1602](https://github.com/anthropics/skills/pull/1602) | **mcp-builder** — evaluation & stability fixes | Critical infrastructure skill; fixes block the entire MCP authoring workflow |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** — typographic quality control | Solves a universal pain point (orphans, widows, numbering); directly improves every document Claude generates |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** — full testing stack | Testing is a top-3 developer workflow; comprehensive coverage from philosophy to React |
| [#486](https://github.com/anthropics/skills/pull/486) | **odt** — OpenDocument skill | Fills a gap for LibreOffice/OpenDocument users; triggers on multiple keyword variants |

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is for skills that protect and optimize context economy** — whether through multi-agent delegation (Hivemind), self-audit quality gates (PR #1367), compact state representation (Issue #1329), or fixing broken evaluation tooling that wastes context on false negatives; alongside that, there is strong appetite for enterprise-platform and document-fidelity skills that close the gap between what Claude can generate and what professionals actually need to ship.

---



# Claude Code Community Digest — 2026-08-29

## 1. Today's Highlights

Claude Code v2.1.251 ships with new `PreModelSwitch`/`PostModelSwitch` hook events and live streaming of foreground subagent tool calls to Remote Con. The community is buzzing around a high-engagement bug where CVP-approved organizations still receive cyber-safeguard blocks (#84352, 164 comments), while Windows Desktop stability remains a persistent pain point across multiple open issues.

---

## 2. Releases

### v2.1.251
**[GitHub](https://github.com/anthropics/claude-code/releases/tag/v2.1.251)**

- Added `PreModelSwitch` and `PostModelSwitch` hook events, allowing hooks to block, confirm, or annotate a model switch. `SessionStart` resume hooks now receive session staleness and estimated re-cache cost.
- Added live streaming of a foreground subagent's tool calls and results to Remote Con.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 | Why It Matters |
|---|-------|--------|----------|----|----------------|
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved org still receives cyber safeguard blocks | OPEN | 164 | 25 | Enterprise users with verified status are being blocked — a trust and compliance issue affecting paid orgs. |
| [#10018](https://github.com/anthropics/claude-code/issues/10018) | Allow Claude Code Web to start sessions from non-default branches | CLOSED | 59 | 86 | High-demand UX improvement for web-based workflows; closed indicates it was implemented. |
| [#53247](https://github.com/anthropics/claude-code/issues/53247) | Claude Desktop fails to launch on Windows — orphaned Silo/Job Object | OPEN | 31 | 19 | Crashes leave orphaned Windows Job Objects; only logoff/reboot recovers. Affects desktop reliability on Windows. |
| [#11627](https://github.com/anthropics/claude-code/issues/11627) | .NET 9/10 SDK support in Claude Code web runtime | CLOSED | 15 | 75 | Strong community demand for modern .NET runtime support in the web environment; closed suggests completion. |
| [#77071](https://github.com/anthropics/claude-code/issues/77071) | Dispatch tab completely missing from Claude Desktop sidebar | OPEN | 18 | 2 | Disables Cowork/Dispatch functionality for some Pro plan users on Windows 11 — a blocking UX bug. |
| [#74170](https://github.com/anthropics/claude-code/issues/74170) | MSIX Installation failure: AddPackage failed with HRESULT 0x80073CF9 | OPEN | 10 | 1 | Windows Store installation failure preventing new users from getting the Desktop app. |
| [#88405](https://github.com/anthropics/claude-code/issues/88405) | Symlinked files in `.claude/rules/` are not auto-loaded | OPEN | 7 | 4 | Directly contradicts official docs; breaks shared rule setups across projects. |
| [#88094](https://github.com/anthropics/claude-code/issues/88094) | Remote Control Being Turned on by Default | OPEN | 6 | 8 | Security-conscious users flagged that Remote Control enables without explicit opt-in on Windows. |
| [#90172](https://github.com/anthropics/claude-code/issues/90172) | Stealth restart silently destroys running sessions | OPEN | 1 | 2 | Eight interrelated defects where background update restarts kill active sessions with "Can't reach your computer." |
| [#90405](https://github.com/anthropics/claude-code/issues/90405) | Model emits cwd-relative links for files edited outside cwd (git worktree) | OPEN | 2 | 0 | Worktree users get stale file references that resolve silently to wrong commits — a correctness bug for advanced workflows. |

---

## 4. Key PR Progress

| # | Title | Status | Author | Why It Matters |
|---|-------|--------|--------|----------------|
| [#87079](https://github.com/anthropics/claude-code/pull/87079) | fix(security-guidance): make `**` glob patterns match zero-depth paths | OPEN | anishsamant | Critical security fix — bare `*` in `fnmatch` crosses `/`, so `**/*.ts` silently excluded top-level `.ts` files from security-patterns.json rules. |

*Only 1 PR was active in the last 24h. The community is primarily focused on issues rather than merge activity this cycle.*

---

## 5. Feature Request Trends

- **Subagent & session observability**: Live streaming of subagent tool calls to Remote Con (now shipped in v2.1.251) reflects sustained demand for visibility into nested agent execution.
- **Branch-aware web sessions**: Issue #10018 (86 👍, now closed) shows strong demand for non-default-branch session starts in Claude Code Web.
- **Modern runtime support**: .NET 9/10 SDK support (#11627, 75 👍, closed) indicates the community wants the web runtime to track current SDK versions.
- **Usage transparency**: Multiple requests for programmatic access to subscription usage data (#83092, #80732) to enable alerting and automation around plan limits.
- **Time-tracking integration**: A new request (#90513) for clock in/out automation via CLI scripting.
- **Mouse support in TUI**: Issue #87769 asks for click-to-navigate and cursor interaction in the terminal UI.
- **Sidebar group inheritance**: Issue #82788 requests that child sessions automatically inherit their parent's sidebar group for better organization.

---

## 6. Developer Pain Points

1. **Windows Desktop stability** — Repeatedly the #1 pain area: crash-on-launch (#53247), orphaned Job Objects, stealth-restart killing sessions (#90172), MSIX install failures (#74170), browser-tab crashes (#87659, #90353), and Dispatch tab disappearing (#77071). Windows Desktop is clearly the most fragile surface.

2. **Cyber safeguard false positives** — Issue #84352 (164 comments) and multiple new cyber-flagged issues (#90501, #90499, #88927) from the same author show that even CVP-approved orgs and authorized workflows are being blocked by overly aggressive safety filters, with no clear appeal path.

3. **Model switch & agent locking** — Dispatch sessions lock to Fable 5 with no escape when limits are hit (#79410), and Opus 5 system-prompt injection silently suppresses the Agent tool and subagent workflows (#88778). Users feel trapped on degraded models.

4. **Documentation-truth gaps** — Symlinked rules not loading (#88405) directly contradicts docs. Trailing-whitespace path handling (#74259) causes silent trust mismatches on macOS. These erode confidence in the tool.

5. **Worktree & path correctness** — cwd-relative links for out-of-cwd edits (#90405) and session context loss when returning to previous agent sessions (#86688) indicate that advanced multi-repo and multi-session workflows are not yet polished.

6. **Remote Control defaults** — Unwanted opt-in of Remote Control (#88094, 8 👍) raises security concerns, especially in enterprise settings.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-29

## 1. Today's Highlights

The Codex team pushed five rapid-fire Rust alpha releases (v0.151.0-alpha.7.1 through .12), signaling active development on the next major CLI iteration. On the Windows Desktop side, a critical post-update startup failure (#40752, 86 comments) continues to dominate community attention, while a highly requested CLI enhancement to disable command-output collapsing (#39903, 65 👍) gained significant traction.

---

## 2. Releases

**Rust CLI** — Five alpha versions landed in the last 24 hours: `v0.151.0-alpha.12`, `.11`, `.10`, `.9`, and `.7.1`. No individual changelogs were provided, but the cadence suggests rapid iteration on the 0.151 feature set ahead of a stable release.

---

## 3. Hot Issues

| # | Title | Comments | 👍 |
|---|-------|----------|-----|
| [#40752](https://github.com/openai/codex/issues/40752) | Windows Desktop app fails to start after update v26.820.60940 — "Unable to locate Codex CLI" & spawn EINVAL on .cmd wrapper | 86 | 51 |
| [#38350](https://github.com/openai/codex/issues/38350) | Recurring scheduled tasks in ChatGPT Work disable themselves after successful runs | 55 | 0 |
| [#39903](https://github.com/openai/codex/issues/39903) | Add option to disable "Ran N commands" collapsing in the TUI | 44 | 65 |
| [#37104](https://github.com/openai/codex/issues/37104) | [Windows/WSL] Integrated terminal silently fails before PTY startup; panels cannot open | 23 | 9 |
| [#34227](https://github.com/openai/codex/issues/34227) | Windows pet overlay hit region desynchronizes from mascot over time | 21 | 1 |
| [#33192](https://github.com/openai/codex/issues/33192) | [Windows 10] DWM Composition handles accumulate after tasks with tool calls | 15 | 10 |
| [#15122](https://github.com/openai/codex/issues/15122) | MCP OAuth login does not persist across restarts; remote MCP startup incomplete | 12 | 7 |
| [#40002](https://github.com/openai/codex/issues/40002) | Android Remote fails to verify trusted Windows projects due to case-sensitive path lookup | 11 | 8 |
| [#39823](https://github.com/openai/codex/issues/39823) | Session resume fails with "already has an active writer" after approval-mode use | 10 | 2 |
| [#41326](https://github.com/openai/codex/issues/41326) | Computer Use helper SIGTRAPs on every click after get_app_state succeeds | 9 | 0 |

**Why they matter:** #40752 is the most disruptive issue this cycle — a post-update crash loop affecting a large Windows user base. #39903 received the strongest community endorsement (65 👍), reflecting a widely shared frustration with the TUI's command-output behavior. #38350 and #15122 both strike at reliability of automated and remote workflows, respectively. #41326 signals a regression in the Computer Use stack that could affect power users relying on GUI automation.

---

## 4. Key PR Progress

| # | Title | Status |
|---|-------|--------|
| [#41477](https://github.com/openai/codex/pull/41477) | Organize bundled Rust resources under asset directories | ✅ Closed |
| [#41476](https://github.com/openai/codex/pull/41476) | Use `rules_rs` platforms for release binaries | ✅ Closed |
| [#41467](https://github.com/openai/codex/pull/41467) | Refresh the TUI model picker from the app server | ✅ Closed |
| [#41464](https://github.com/openai/codex/pull/41464) | Preserve permissions when updating session metadata | ✅ Closed |
| [#41461](https://github.com/openai/codex/pull/41461) | Source async user message descriptions from the model catalog | ✅ Closed |
| [#41457](https://github.com/openai/codex/pull/41457) | Source proactive multi-agent instructions from the model catalog | ✅ Closed |
| [#41454](https://github.com/openai/codex/pull/41454) | Block goals after repeated execution host failures | ✅ Closed |
| [#41452](https://github.com/openai/codex/pull/41452) | Report code mode host request durations | ✅ Closed |
| [#41447](https://github.com/openai/codex/pull/41447) | Support `openai/elicitation` form requests | ✅ Closed |
| [#41436](https://github.com/openai/codex/pull/41436) | Respond to terminal queries from TTY subprocesses | ✅ Closed |

**Highlights:** The team is investing heavily in the Rust toolchain's build infrastructure (#41476) and resource packaging (#41477). Model catalog–sourced descriptions (#41461, #41457) will make TUI prompts and multi-agent instructions consistent with the latest model definitions. New fault-tolerance logic in #41454 will block goals after three consecutive execution-host failures, preventing runaway sessions. The elicitation form support (#41447) and terminal-query handling (#41436) improve compatibility with interactive TTY workflows.

---

## 5. Feature Request Trends

- **TUI transparency & control:** The #39903 request to expose all executed commands (65 👍) reflects a strong desire for full visibility into Codex's tool usage, especially for debugging and audit purposes.
- **Remote & cross-platform reliability:** Issues around Android Remote path handling (#40002), MCP OAuth persistence (#15122), and WebSocket transport under proxy (#29958) point to an active user base running Codex across heterogeneous environments who need more robust remote integration.
- **Automation & scheduling reliability:** #38350's recurring-task self-disabling bug and the new PR to block goals after repeated host failures (#41454) both indicate a push toward making long-running and scheduled autonomous workflows more dependable.
- **Model catalog integration:** Multiple PRs (#41461, #41457) show the team is shifting hardcoded behavior into the model catalog, enabling faster iteration on agent behavior without client releases.

---

## 6. Developer Pain Points

1. **Windows post-update instability** — At least six distinct issues (#40752, #40776, #41289, #41339, #41241, #40972) describe startups failing, apps launching suspended, update loops, or tool-host crashes after version bumps. This is the dominant pain signal this cycle.
2. **Session & writer-state corruption** — Multiple reports (#39823, #41353) describe sessions wedging after approval-mode use or paginated rollout writer collisions, leaving users unable to resume work.
3. **MCP & auth fragility** — OAuth tokens not persisting (#15122) and plugin skills losing their MCP tools after restart (#38342) undermine workflows that depend on remote or custom tool integrations.
4. **Resource leaks on Windows** — DWM Composition handle growth (#33192) and orphan process leaks (#40972) suggest memory/resource management gaps in the Windows renderer path, particularly around tool-call-heavy sessions.
5. **Command-output noise in TUI** — The overwhelmingly upvoted request (#39903) to stop collapsing "Ran N commands" highlights a recurring friction point where developers must repeatedly expand output to inspect tool results.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-29

## 1. Today's Highlights
Gemini CLI v0.59.0-nightly ships with a critical fail-closed workspace trust enforcement that filters repository-defined MCP servers in restricted environments. Community attention is heavily concentrated on subagent lifecycle reliability, particularly max-turn recovery and generalist agent hangs, while a coordinated wave of security hardening PRs addresses OAuth issuer validation, NTFS path traversal, and insecure config loading.

## 2. Releases
- **v0.59.0-nightly.20260829.g0bd1d4397** ([Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260828.g3

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-29

## 1. Today's Highlights

GitHub Copilot CLI **v1.0.82-1** landed overnight, adding a key UX fix that surfaces specific authentication failure codes (e.g., `401 Bad credentials`) instead of redirecting users to an opaque `/login` prompt. Meanwhile, the community filed a wave of 22 issues in the past 24 hours, many clustered around v1.0.81 regressions affecting enterprise auth flows, model-catalog URL routing, and parallel-subagent event handling.

---

## 2. Releases

**v1.0.82-1**
- **Fixed** — Auth failures now display the specific error (e.g., `401 Bad credentials`) rather than only prompting the user to run `/login`.
- [GitHub Release](https://github.com/github/copilot-cli/releases)

---

## 3. Hot Issues

1. **#4612 — Runaway FileWatch loop freezes TUI and grows debug log to 13 GB** `[OPEN]` · 👍1 · 7 comments
   A tight `FileWatch` host-event loop on resumed/long-running sessions blocks the TUI and bloats debug logs. A high-severity stability regression.
   [Issue #4612](https://github.com/github/copilot-cli/issues/4612)

2. **#4480 — Atlassian MCP OAuth fails with "Incompatible authorization server"** `[CLOSED]` · 👍6 · 7 comments
   OAuth discovery on `mcp.atlassian.com` broke in v1.0.79 (regression from v1.0.71). Now closed — likely addressed by the v1.0.82-1 auth fix.
   [Issue #4480](https://github.com/github/copilot-cli/issues/4480)

3. **#4533 — Terminal UI stops consuming events during parallel subagent turns** `[OPEN]` · 4 comments
   On prerelease builds (1.0.81-4/5), the TUI goes dead while the Rust runtime continues inference. Runtime ≠ UX — a critical dissociation.
   [Issue #4533](https://github.com/github/copilot-cli/issues/4533)

4. **#4165 — `copilot --resume` hangs at "Resuming session" on Windows cold start** `[OPEN]` · 👍1 · 4 comments
   Windows-only hang; local fallback works but the interactive resume never reaches the prompt. Affects daily workflow continuity.
   [Issue #4165](https://github.com/github/copilot-cli/issues/4165)

5. **#4527 — `copilot -p` fails with 401 on GHEC data-residency tenants since v1.0.81-1** `[OPEN]` · 👍4 · 2 comments
   Prompt mode hits `api.githubcopilot.com` instead of the tenant endpoint, breaking non-interactive flows for enterprise data-residency customers.
   [Issue #4527](https://github.com/github/copilot-cli/issues/4527)

6. **#4647 — v1.0.81 broke compatibility with chroma-mcp** `[OPEN]` · 1 comment
   Upgrade from 1.0.80 → 1.0.81 causes a breaking change for a popular MCP server. Regression affecting ecosystem tooling.
   [Issue #4647](https://github.com/github/copilot-cli/issues/4647)

7. **#4654 — `list models` uses incorrect URL on GitHub Enterprise** `[OPEN]` · 1 comment
   Same pattern as #4527: enterprise accounts hit the public model endpoint and receive 401. Suggests a systemic URL-routing regression in v1.0.81.
   [Issue #4654](https://github.com/github/copilot-cli/issues/4654)

8. **#4650 — Auth fails whenever `-p` or `--agent` is used (enterprise login)** `[OPEN]` · 1 comment
   Third-party MCP servers blocked by org policy cause a full session load failure even in prompt mode. Blocks enterprise users entirely.
   [Issue #4650](https://github.com/github/copilot-cli/issues/4650)

9. **#1392 — OmniSharp LSP times out on large C# projects; needs configurable `initializeTimeout`** `[OPEN]` · 👍5 · 3 comments
   Long-standing feature request: no way to tune LSP initialization timeout, causing failures on large solutions.
   [Issue #1392](https://github.com/github/copilot-cli/issues/1392)

10. **#4649 — Tool search enabled on Grok but defers nothing (57.7k vs 21.0k tokens)** `[OPEN]` · 1 comment
    Follow-up to #4588: GPT models fixed, but Grok and Gemini families still reporting incorrect tool-defer behavior.
    [Issue #4649](https://github.com/github/copilot-cli/issues/4649)

---

## 4. Key PR Progress

1. **#4497 — Handle fork PR associations in invalid-label writer** `[CLOSED]`
   Updates the trusted invalid-label writer to search by trusted workflow-run metadata when GitHub omits the PR association on fork PRs. Requires exactly one open PR to proceed.
   [PR #4497](https://github.com/github/copilot-cli/pull/4497)

*(No additional open PRs were reported in the 24h window.)*

---

## 5. Feature Request Trends

- **Local, offline-first memory** — Issue #2930 requests agent-initiated local auto-memory without remote storage, driven by enterprise orgs that disable Copilot Memory for data-residency compliance.
- **Configurable LSP timeouts** — Issue #1392 asks for a tunable `initializeTimeout` in `lsp-config.json` so large projects (e.g., C#/OmniSharp) aren't killed by hardcoded limits.
- **Deferred/steering hook parity** — Issue #4640 highlights that `userPromptTransformed` is skipped for steering messages, suggesting a need for hook consistency across all message types.
- **Tool-cost transparency** — Issue #4189 (now closed) underscored demand for accurate context reporting; the fix revealed that deferred tool loading should surface real token counts, not worst-case schemas.

---

## 6. Developer Pain Points

- **v1.0.81+ enterprise auth regressions** — A cluster of issues (#4527, #4654, #4650, #4480) point to a systemic problem: prompt mode and enterprise URLs are hitting public endpoints instead of tenant-specific ones, breaking GHEC data-residency setups and policy-blocked MCP scenarios.
- **TUI stability under load** — Runaway FileWatch loops (#4612), parallel-subagent event starvation (#4533), and black input-field rendering (#4648) all degrade the interactive experience, especially on long-running or multi-agent sessions.
- **Windows-specific friction** — Session resume hangs (#4165), AltGr key swallowing (#4653), and sandbox-not-supported warnings on Windows 25H2 (#4652) indicate ongoing platform parity gaps.
- **Ecosystem breakage** — v1.0.81 broke chroma-mcp (#4647) and the `/model` command vanished in BYOK mode after a VS Code update (#4651), eroding trust in upgrade paths.
- **Repetitive shell-completion installs** — Issue #4658 notes completions are reinstalled on every startup, including headless `--server` sessions where the binary is never on PATH, creating noisy, redundant side-effects.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-29

---

## 1. Today's Highlights

A critical security vulnerability (#2625) has been closed, revealing that MCP tool calls bypass built-in secret-file guards, allowing arbitrary file reads under auto-approve mode. Separately, a paying subscriber (#2626) reported abnormal quota consumption with cache_read billed repeatedly while cache_creation remains at zero, suggesting a potential billing anomaly worth investigating.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

### #2625 — Security: MCP tool calls bypass built-in secret-file guards [CLOSED]
**Author:** zhaoxingxing06 | **Created:** 2026-08-28 | **Comments:** 1 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/2625)

**Why it matters:** This is the most significant item this cycle. The CLI's built-in `Read` tool correctly blocks access to sensitive files (`.env`, SSH private keys, credential stores), but MCP tool calls are exempt from this content-level guard. In auto-approve permission mode, they also skip the approval prompt entirely, enabling arbitrary file read via a malicious or misconfigured MCP server. The issue is now closed, suggesting a fix or mitigation is being deployed.

**Community reaction:** High severity flagged; zero explicit 👍 so far but the closed status indicates team acknowledgment.

---

### #2626 — Abnormal quota consumption: cache_read billed every turn with cache_creation always 0 [OPEN]
**Author:** ahmadyaseen35-coder | **Created:** 2026-08-29 | **Comments:** 0 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/2626)

**Why it matters:** A paying annual-plan subscriber reports ~40% quota loss within minutes of light use on 2026-08-28. Cache_read is being billed on every turn while cache_creation consistently reports 0, indicating a possible >10x amplification of cache-related costs. This points to a potential billing or caching logic bug with direct revenue impact.

**Community reaction:** Open and unaddressed; no comments or 👍 yet — likely early in the triage queue.

---

## 4. Key PR Progress

### #2622 — deps: bump asyncssh to 2.23.1 in pykaos (GHSA-2wxc-x7rj-hg8f) [OPEN]
**Author:** katsugtgz | **Created:** 2026-08-28 | [Link](https://github.com/MoonshotAI/kimi-cli/pull/2622)

**What it does:** Updates the `asyncssh` dependency from 2.21.1 to 2.23.1 in the `pykaos` workspace package, addressing two opened security advisories: GHSA-2wxc-x7rj-hg8f and GHSA-qr67-gv47-xwwh. The PR was auto-generated from OSV evidence and directly modifies `packages/kaos/pyproject.toml` and `uv.lock`.

**Status:** Open, awaiting review. No comments or 👍 yet.

---

## 5. Feature Request Trends

Based on the current issue set, the dominant themes are:

- **Security hardening around MCP integrations** — Users are increasingly relying on MCP servers but report that permission and content guards do not uniformly apply to MCP tool calls. There is an implicit demand for consistent security policies across all tool invocation paths.
- **Transparent and accurate quota/billing reporting** — The quota anomaly report (#2626) reflects a broader expectation that cached-token billing be clearly explained and fairly priced, with visibility into per-turn cost breakdowns.

---

## 6. Developer Pain Points

1. **Inconsistent security guard coverage:** Built-in tools are protected against reading sensitive files, but MCP tool calls bypass these guards — especially problematic in auto-approve mode. Developers relying on MCP servers for file operations face an unguarded attack surface.
2. **Billing opacity and quota surprises:** The cache_read amplification bug (#2626) highlights a pain point where quota consumption behaves unpredictably, with no clear per-turn cost breakdown available to users, making it difficult to diagnose or budget usage.
3. **Dependency security debt:** The asyncssh vulnerability PR (#2622) being external-submitted rather than internally driven suggests the maintainer team may be lagging on routine dependency audits, leaving consumers to file PRs for known CVEs.

---

*Digest generated from github.com/MoonshotAI/kimi-cli data as of 2026-08-29.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-29

---

## 1. Today's Highlights

OpenCode v2 web and desktop are moving toward a production beta, highlighted by a new **QR server-pairing** feature (#46098) and SST-driven deployment of `beta.opencode.ai` (#46086). On the fix side, a cluster of renderer and resource-management patches landed today, addressing Windows shell pipe leaks, truncated tool arguments, and memory bloat in both the core job registry and the TUI's shared-library handling. Community frustration remains high around **GPT model latency** (#29079, 119 comments / 52 👍) and **Desktop renderer crashes** on macOS and Windows.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 |
|---|-------|--------|----------|----|
| [#29079](https://github.com/anomalyco/opencode/issues/29079) | GPT Models takes too long to respond | CLOSED | 119 | 52 |
| [#42700](https://github.com/anomalyco/opencode/issues/42700) | TUI leaks ~21 MB .so per launch into /tmp | OPEN | 7 | 0 |
| [#22792](https://github.com/anomalyco/opencode/issues/22792) | vLLM + Qwen3-Coder compaction-style loop | CLOSED | 6 | 3 |
| [#36766](https://github.com/anomalyco/opencode/issues/36766) | Fix truncated OpenAI tool arguments | OPEN | 5 | 0 |
| [#23461](https://github.com/anomalyco/opencode/issues/23461) | `opencode upgrade` fails with 403 (ignores GITHUB_TOKEN) | OPEN | 5 | 2 |
| [#46088](https://github.com/anomalyco/opencode/issues/46088) | ECONNRESET errors when connecting to custom model | OPEN | 3 | 0 |
| [#38366](https://github.com/anomalyco/opencode/issues/38366) | Bun segfault when multiple instances launch concurrently (macOS arm64) | OPEN | 2 | 0 |
| [#46059](https://github.com/anomalyco/opencode/issues/46059) | AI stuck in text-only reasoning loop, never executing tools | CLOSED | 2 | 0 |
| [#25755](https://github.com/anomalyco/opencode/issues/25755) | `temperature` not sent in request body for custom OpenAI-compatible providers | CLOSED | 2 | 0 |
| [#34510](https://github.com/anomalyco/opencode/issues/34510) | Per-agent compaction control breaks local model workflows | CLOSED | 2 | 0 |

**Why they matter:**
- **#29079** is the most-discussed issue in the repo (119 comments, 52 👍). Users report GPT-5.x taking minutes on trivial prompts — a trust and productivity blocker.
- **#42700** describes a **memory leak** that fills `/tmp` and ultimately prevents TUI startup on Linux, making it a showstopper for long-running sessions.
- **#36766** and **#46088** touch core reliability: truncated tool arguments silently break execution, while ECONNRESET errors on custom model connections suggest connection-pool or TLS misconfiguration.
- **#38366** is a severe stability bug — concurrent instances on macOS arm64 crash with segfaults, limiting multi-project workflows.
- **#25755** exposes a config-parity gap: settings that work for built-in providers are silently dropped for custom OpenAI-compatible backends.

---

## 4. Key PR Progress

| # | Title | Status | Author |
|---|-------|--------|--------|
| [#46098](https://github.com/anomalyco/opencode/pull/46098) | feat(app): pair servers from QR codes | OPEN | Hona |
| [#46086](https://github.com/anomalyco/opencode/pull/46086) | feat(infra): deploy beta web app with SST | CLOSED | Hona |
| [#46090](https://github.com/anomalyco/opencode/pull/46090) | fix(app): preserve Windows panel top outlines | CLOSED | Hona |
| [#46085](https://github.com/anomalyco/opencode/pull/46085) | fix(shell): bound Windows post-exit pipe draining | OPEN | Hona |
| [#46087](https://github.com/anomalyco/opencode/pull/46087) | fix(core): bound consumed job history | OPEN | Hona |
| [#46084](https://github.com/anomalyco/opencode/pull/46084) | fix(ai): isolate response tool call identities | OPEN | kitlangton |
| [#46083](https://github.com/anomalyco/opencode/pull/46083) | test(tui): wait for diff base search focus | OPEN | kitlangton |
| [#32370](https://github.com/anomalyco/opencode/pull/32370) | feat(tui): add `linux_clipboard_selection` config for primary buffer | OPEN | bornmw |
| [#44938](https://github.com/anomalyco/opencode/pull/44938) | feat(tui): paste primary selection on middle click | CLOSED | sshnaidm |
| [#46072](https://github.com/anomalyco/opencode/pull/46072) | refactor(core): merge defaults for selected MCP servers | CLOSED | kitlangton |

**Notable updates:**
- **#46098** introduces QR-code pairing between V2 web and desktop clients — a significant UX improvement for multi-instance setups.
- **#46086** closes the loop on beta deployment infrastructure via SST, enabling `beta.opencode.ai`.
- **#46085** and **#46087** are defensive resource-management fixes: bounding Windows pipe descendants and capping job history to 100 jobs / 16 MiB prevents memory growth in long sessions.
- **#46084** isolates tool-call identities in OpenAI Responses, fixing a race where truncated or aliased call IDs dropped authoritative arguments.
- **#32370** and **#44938** deliver long-requested Linux clipboard parity (primary selection / middle-click paste), superseding earlier attempts.
- **#46072** cleans up MCP server default merging, eliminating discarded-work redundancy.

---

## 5. Feature Request Trends

1. **Local / custom model workflows** — Multiple issues (#22792, #25755, #34510, #46046) highlight pain with vLLM, Qwen, and NVIDIA endpoints: compaction loops, missing config parameters, and renderer dead-locks. The community wants first-class parity between cloud and local providers.
2. **Plugin and worktree extensibility** — #15680 requests worktree lifecycle events (created/removed/reset) for plugins; #17427 asks for a workspace-delete script. Users are building database-backed workflows and need programmatic control.
3. **Project-level MCP configuration** — #30933 asks for MCP server config directly in `opencode.json`, removing the need for manual setup per project.
4. **Cross-client pairing and collaboration** — QR-code pairing (#46098) signals demand for friction-free multi-device session bridging.
5. **Linux clipboard / input parity** — The repeated pushes for primary-selection support (#32370, #44938, #6370) show Linux users expect terminal-style middle-click paste behavior.

---

## 6. Developer Pain Points

- **Renderer stability on desktop** — A cluster of June issues (#34421, #34382, #34437, #34426, #34507) report macOS/Windows renderer freezes, infinite Solid.js signal loops, and unresponsive menus. Large diffs and history-scrolling are particularly dangerous.
- **Memory leaks** — #42700 (.so leak in TUI) and #34408 (skills never hot-reloaded due to non-evicting in-memory cache) point to resource-management gaps that accumulate over time.
- **Session data loss after updates** — #34445 and #34471 describe migration failures when the storage backend moved to SQLite; users lost chat history after `opencode` upgrades.
- **Unpredictable billing** — #34402 reports a single prompt consuming $20 with no output, raising trust concerns around cost estimation and guardrails.
- **Config inconsistency across providers** — #25755 and #36766 reveal that settings (temperature, tool-argument handling) that work for built-in providers silently fail or are dropped for custom/OpenAI-compatible backends.
- **Slow GPT responses** — #29079 remains the top community complaint, with 52 upvotes and no clear resolution, eroding confidence in cloud-provider integrations.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-29

---

## 1. Today's Highlights

Pi v0.84.4 lands with terminal capability overrides and extension UI prompt events, while a wave of fixes addresses narrow-terminal crashes, model selector race conditions, and compaction reliability. Community focus is shifting toward startup UX improvements (new StartupComposer) and tighter integration with Amazon Bedrock Mantle.

---

## 2. Releases

### v0.84.4

- **Terminal capability overrides** — Override detected terminal hyperlink, image, and truecolor support. See [Capability Overrides](https://github.com/earendil-works/pi/blob/v0.84.4/packages/coding-agent/docs/terminal-setup.md#capability-overrides).
- **Extension UI prompt events** — New events fired around UI dialog primitives.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#8584](https://github.com/earendil-works/pi/issues/8584) | TUI row corruption during streaming | Assistant text rendered one word per line after long tool output; directly impacts readability during active sessions. | 24 comments · 9 👍 |
| [#6879](https://github.com/earendil-works/pi/issues/6879) | Auto-compaction never triggers past 100% context | Session context can exceed the window with no compaction until the provider rejects — a silent data-loss risk. | 24 comments · 20 👍 (closed via PR #8782) |
| [#2870](https://github.com/earendil-works/pi/issues/2870) | Follow XDG Base Directory | Long-standing request to stop cluttering `$HOME` on Linux; 52 👍 shows strong consensus. | 20 comments · 52 👍 (closed) |
| [#7130](https://github.com/earendil-works/pi/issues/7130) | Backspace deletes 2 chars in Kitty | Terminal-specific input bug; Kitty users report double-delete on backspace. | 12 comments · 1 👍 (closed) |
| [#8166](https://github.com/earendil-works/pi/issues/8166) | Custom mid-tool-batch message breaks tool_calls adjacency | Extensions calling `pi.sendMessage({ triggerTurn: false })` cause cascading 400 errors on every subsequent turn. | 11 comments |
| [#7128](https://github.com/earendil-works/pi/issues/7128) | `PI_*` guideline over-encourages bash calls | New system-prompt default biases the agent toward unnecessary env-inspection commands. | 11 comments · 13 👍 |
| [#7553](https://github.com/earendil-works/pi/issues/7553) | Configurable thinking level for compaction | Compaction reuses the session's thinking level unconditionally — a budget concern for reasoning-model users. | 9 comments |
| [#7153](https://github.com/earendil-works/pi/issues/7153) | `/scoped-models` stalls ~5 min on stalled catalog refresh | Sync await blocks the REPL with no feedback for five minutes. | 8 comments · 4 👍 (closed) |
| [#8620](https://github.com/earendil-works/pi/issues/8620) | 0.84.3 bundled CLI: all global extensions fail | Breaking change in 0.84.3 — extensions importing `@earendil-works/pi-coding-agent` cannot load. | 6 comments |
| [#8806](https://github.com/earendil-works/pi/issues/8806) | TUI crashes on narrow terminals (80–88 cols) | Hard-crash at startup; built-in startup box exceeds narrow terminal width. Fix in PR #8805. | 2 comments (closed) |

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#8812](https://github.com/earendil-works/pi/pull/8812) | Flush extension provider registrations before initial model resolution | Fix | Addresses [#8810](https://github.com/earendil-works/pi/issues/8810) — queued extension providers now apply before the session binds, preventing silent fallback to wrong defaults. |
| [#8811](https://github.com/earendil-works/pi/pull/8811) | Add startup composer | Feature | New `StartupComposer` accepts input during startup and carries it into interactive mode; project trust checks and dialogs now share the same UI. |
| [#8805](https://github.com/earendil-works/pi/pull/8805) | Adaptive truncate instead of crash on narrow terminals | Fix | Replaces hard `Rendered line exceeds terminal width` throw with graceful truncation. Closes [#8806](https://github.com/earendil-works/pi/issues/8806). |
| [#8782](https://github.com/earendil-works/pi/pull/8782) | Compact before post-tool model requests | Fix | Runs threshold compaction before the next provider request, preventing context overflow. Closes [#6879](https://github.com/earendil-works/pi/issues/6879). |
| [#8786](https://github.com/earendil-works/pi/pull/8786) | Match skill commands by bare name in slash autocomplete | Fix | Fixes fuzzy ranking so `/idea` matches `skill:research-idea` instead of `skill:deep-research`. Closes [#8813](https://github.com/earendil-works/pi/issues/8813). |
| [#8795](https://github.com/earendil-works/pi/pull/8795) | Add artifact verification repair gate | Feature | Opt-in extension that withholds the success token until deterministic artifact verification passes, feeding machine-readable failures as bounded repair turns. |
| [#8784](https://github.com/earendil-works/pi/pull/8784) | Per-model max_tokens cap for MiniMax-M3 | Fix | Caps `max_tokens` at 524,288 for MiniMax-M3 via OpenRouter/GMICloud to avoid HTTP 400 rejections. |
| [#8800](https://github.com/earendil-works/pi/pull/8800) | Search improvements | Feature | `Ctrl+Shift+F` opens/closes search; `Esc` also closes. Better UX in alt mode. |
| [#8572](https://github.com/earendil-works/pi/pull/8572) | Amazon Bedrock Mantle support | Feature | WIP — adds Mantle API surface support for models like `openai.gpt-5.x` on Bedrock, which previously failed via Converse routing. |
| [#8790](https://github.com/earendil-works/pi/pull/8790) | Extensions changelog | Feature | Adds `changelogPath` to `PiManifest` with safe package-relative resolution and `CHANGELOG.md` fallback; surfaces extension changelogs in Pi's own UI. |

---

## 5. Feature Request Trends

- **Compaction & context budget control** — Multiple requests for per-operation compaction settings: configurable thinking level ([#7553](https://github.com/earendil-works/pi/issues/7553)), proactive compaction before post-tool requests ([#6879](https://github.com/earendil-works/pi/issues/6879)), and retry logic for summarization failures ([PR #6848](https://github.com/earendil-works/pi/pull/6848)).
- **Startup & onboarding UX** — The StartupComposer ([PR #8811](https://github.com/earendil-works/pi/pull/8811)) and narrowed-terminal resilience ([PR #8805](https://github.com/earendil-works/pi/pull/8805)) reflect demand for smoother entry into sessions.
- **Provider & model flexibility** — Bedrock Mantle support ([PR #8572](https://github.com/earendil-works/pi/pull/8572)), per-model token caps ([PR #8784](https://github.com/earendil-works/pi/pull/8784)), and extension-registered provider registration timing ([PR #8812](https://github.com/earendil-works/pi/pull/8812)) all point to a community actively expanding multi-provider workflows.
- **Artifact & session safety** — The artifact verification gate ([PR #8795](https://github.com/earendil-works/pi/pull/8795)) and image-attachment resize pipeline concerns ([#8808](https://github.com/earendil-works/pi/issues/8808)) show growing interest in reliability guarantees for long-running agent sessions.
- **UI polish & configurability** — Prettier spinner ([PR #8799](https://github.com/earendil-works/pi/pull/8799)), alt-mode scrollbar ([PR #8801](https://github.com/earendil-works/pi/pull/8801)), autocomplete positioning ([#8793](https://github.com/earendil-works/pi/issues/8793)), and footer layout tweaks ([#8794](https://github.com/earendil-works/pi/issues/8794)) indicate sustained demand for a more polished TUI.

---

## 6. Developer Pain Points

- **Terminal width fragility** — Narrow terminals (80–88 cols) crash at startup ([#8806](https://github.com/earendil-works/pi/issues/8806)), and streaming text can wrap to one word per line after long tool output ([#8584](https://github.com/earendil-works/pi/issues/8584)). Both signal that the TUI layout layer needs more defensive width handling.
- **Extension lifecycle ordering** — Extension-registered providers can be silently ignored if model resolution completes before registration flushes ([#8810](https://github.com/earendil-works/pi/issues/8810), [#8620](https://github.com/earendil-works/pi/issues/8620)). The bundled CLI also broke global extension loading in 0.84.3. Module resolution and provider registration timing remain fragile areas.
- **Compaction reliability** — Auto-compaction not triggering before context overflow ([#6879](https://github.com/earendil-works/pi/issues/6879)), compaction failing on OpenAI Responses models ([#8774](https://github.com/earendil-works/pi/issues/8774)), and transient stream failures breaking summarization all indicate the compaction path needs more robust error handling and earlier triggers.
- **Autocomplete ranking** — Skill autocomplete ranking full `skill:<name>` strings causes mis-ranking ([#8813](https://github.com/earendil-works/pi/issues/8813)), and `@` file autocomplete lacks fuzzy-nested-path support ([#8807](https://github.com/earendil-works/pi/issues/8807)). Users want more intuitive completion behavior.
- **System prompt drift** — New default guidelines (e.g., `PI_*` env inspection, [#7128](https://github.com/earendil-works/pi/issues/7128)) can bias agent behavior in ways users find disruptive. The community is sensitive to silent prompt changes that alter agent habits.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-29

## 1. Today's Highlights

Qwen Code **v0.22.3** shipped with owner-scoped named sessions in Channels (up to 8 persistent tasks per chat), absolute-path-only daemon extension installs, and updated `cua-driver-rs` prebuilt binaries across macOS, Linux, and Windows. The Web Shell continues to be the focal point of development, with multiple PRs improving error recovery, session management, and workspace UX.

---

## 2. Releases

**v0.22.3** — [Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.22.3)

Key changes:
- **Owner-scoped named sessions** in Channels, enabling up to 8 persistent tasks per chat ([#10198](https://github.com/QwenLM/qwen-code/pull/10198))
- **Daemon Extension installs** now accept absolute local paths only (relative paths rejected)
- **cua-driver-rs v0.20.2** — codesigned + notarized universal binary for macOS; glibc 2.31 floor for Linux (x86_64 + arm64); Windows binaries provided unsigned; Node.js package also updated

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#9981](https://github.com/QwenLM/qwen-code/issues/9981) | Deferred review findings from PR #9406 | Autofix loop defers review findings outside the PR footprint for follow-up; 6 comments indicate active maintainer triage. |
| [#8897](https://github.com/QwenLM/qwen-code/issues/8897) ✅ | `--approval-mode` / `--auth-type` missing from `qwen --help` | CLI flags accepted and validated but absent from help output — a documentation parity bug confirmed and closed. |
| [#8432](https://github.com/QwenLM/qwen-code/issues/8432) | Bailian Personal Token Plan models out of sync | Built-in model list diverges from current Bailian console; image/video generation affected. |
| [#10210](https://github.com/QwenLM/qwen-code/issues/10210) ✅ | `team_delete` reports success after filesystem cleanup fails | `deleteTeamDirs()` swallowed `fs.rm` errors — a correctness bug now resolved. |
| [#10415](https://github.com/QwenLM/qwen-code/issues/10415) | Deferred review findings from PR #10122 | Continued autofix follow-up trail from the WebShell cutover PR. |
| [#10372](https://github.com/QwenLM/qwen-code/issues/10372) | `closeDiff` skips workspace-relative path resolution | Fix withheld from the over-cap PR #9811; needs a dedicated follow-up patch. |
| [#10075](https://github.com/QwenLM/qwen-code/issues/10075) ✅ | Tools silently disappear when `permissions.allow` is set | Any tool not in the allowlist vanished from the session entirely — a critical regression in 0.22.1. |
| [#10441](https://github.com/QwenLM/qwen-code/issues/10441) | Filter-screen hits must resolve by origin file | `localFilterCommands` doesn't expand `include.path`/`includeIf`, allowing repo-local filters to be hidden. |
| [#10435](https://github.com/QwenLM/qwen-code/issues/10435) | New version crashes inference on local llama-server | API error `400 Failed to initialize samplers: failed to parse grammar` — regression for local LLM users. |
| [#10469](https://github.com/QwenLM/qwen-code/issues/10469) | `sessionCd` folder-trust gate reads stale cache | In multi-workspace daemons, one workspace's trust settings can silently affect another — a security-relevant bug flagged P2. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#10390](https://github.com/QwenLM/qwen-code/pull/10390) | Unblock git update on dirty working tree | 🟢 Open | Web Shell now presents a resolution panel with options when a plain pull is blocked by uncommitted changes, instead of failing silently. |
| [#10011](https://github.com/QwenLM/qwen-code/pull/10011) | Persist reasoning effort | 🟢 Open | WebShell reasoning selections update the active session immediately and persist as the global `model.reasoningEffort` default across restarts. |
| [#10024](https://github.com/QwenLM/qwen-code/pull/10024) | Share HTML artifacts through managed hosting | 🟢 Open | Adds a guided provider flow (Cloudflare → Vercel → Netlify) for publishing HTML artifacts from Web Shell with a unified progress UI. |
| [#10215](https://github.com/QwenLM/qwen-code/pull/10215) | Recoverable error state on boot failure | 🟢 Open | Replaces the blank white screen on Web Shell boot failure with a visible error message and reload option. |
| [#10310](https://github.com/QwenLM/qwen-code/pull/10310) | Gate decided stops on composed re-rule verdict | 🟢 Open | Fixes `qwen review run --fail-on request-changes` exiting 0 when a round completes with `event: null` but open Criticals remain. |
| [#8583](https://github.com/QwenLM/qwen-code/pull/8583) | Experimental session workflow cockpit | 🟢 Open | Completes the Session Workflow path across plan capture, revision-bound approval, transcript projection, and Agent execution views. |
| [#10407](https://github.com/QwenLM/qwen-code/pull/10407) | Workspace overview & menu in sidebar | 🟢 Open | Sidebar workspace rows now show session counts (waiting/running/total) and an inline management menu. |
| [#10468](https://github.com/QwenLM/qwen-code/pull/10468) | Settle cancelled workflow; size window by usable CPUs | 🟢 Open | Fixes two lifecycle defects: cancelled workflows now settle immediately, and worker pool sizing uses usable CPU count. |
| [#10347](https://github.com/QwenLM/qwen-code/pull/10347) | Auto-retry transient network errors (EOF) | 🟢 Open | 4xx errors that wrap low-level network failures (e.g., `EOF`) are now classified as retryable instead of fail-fast. |
| [#10283](https://github.com/QwenLM/qwen-code/pull/10283) | Select output style via config or flag | 🟢 Open | Adds `general.outputStyle` setting and `--output-style` flag, resolving case-insensitively against built-in styles. |

---

## 5. Feature Request Trends

- **Web Shell UX maturity** — The dominant theme: persistent session management, error recovery, workspace overviews, and session workflow Cockpit all point to Web Shell moving from experimental to production-grade.
- **Managed artifact sharing** — PR #10024's multi-provider HTML artifact sharing reflects growing demand for built-in deployment workflows.
- **Output control & personalization** — Output style selection (#10283), reasoning effort persistence (#10011), and XDG directory support (#1210, 3+ 👍) show users want finer-grained control over CLI behavior and config locality.
- **Multi-workspace daemon correctness** — Trust-gate staleness (#10469), team filesystem cleanup (#10210), and named-session routing (#10071) indicate the multi-workspace daemon is surfacing edge cases that need hardening.

---

## 6. Developer Pain Points

1. **Web Shell boot and session-state bugs** — A cluster of P2 issues (#10406 infinite re-render, #10405 locked overlay, #10385 wrong turn index, #10391 pinned sessions lost from groups) all trace back to the WebShell cutover in PR #9811. The review scope cap forced these fixes into deferred issues, creating a backlog of UI regressions.
2. **Daemon multi-workspace trust isolation** — Issue #10469 exposes that `sessionCd` reads a process-wide settings cache rather than the session's own workspace, a correctness gap that could silently cross-contaminate trust decisions.
3. **Local LLM compatibility regressions** — Issue #10435 reports that v0.22.3 breaks inference with local `llama-server` instances, suggesting grammar or sampler changes in the release need review for non-Cloud LLM providers.
4. **CLI help/documentation parity** — Issue #8897 (closed) highlighted that registered flags (`--approval-mode`, `--auth-type`) were absent from `qwen --help`, a recurring friction point for CLI discoverability.
5. **CI reliability** — Multiple CI-focused PRs (#10443 vitest timeout, #10452 heartbeat shims, #10429 `/resolve` request recovery, #10439 failure watchdog) indicate ongoing instability in the review autofix pipeline that the team is actively patching.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-29

## 1. Today's Highlights

The v0.9.12 release cycle is actively converging, with milestone tracking (#5573), critical auth fixes merged (#5704), and plugin UX parity work closing in (#5663). A major push for provider-native web search expansion landed with Moonshot/Kimi support (#5686), while the project continues steady cleanup—dead code removed (#5705), dependency bumps across the stack, and CI reliability improvements for Ubuntu builds (#5710).

---

## 2. Releases

**No new releases in the last 24 hours.** The next target is **v0.9.12**, currently in active development on branch `codex/v0912-integration-20260823` with a must-fix set to be shipped.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#5573](https://github.com/Hmbown/CodeWhale/issues/5573) | v0.9.12: milestone tracker | Central orchestration for the upcoming release—P0 must-fixes tracked with a clear ship target and full release chain verification. | 22 comments; active discussion on priority ordering. |
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | EPIC-005: Crate Decomposition | Umbrella tracking issue for the entire CodeWhale TUI crate decomposition, affecting project architecture and long-term maintainability. | 18 comments; ongoing since Aug 10. |
| [#5350](https://github.com/Hmbown/CodeWhale/issues/5350) | Simplify third-party model config | Newcomers struggle with manual Base URL, model name, and secret env vars for providers like OpenCode, Agnes, Sensenova. Fixes would cut setup time to under 1 minute. | **Closed** — resolved with pre-built templates and a "test connection" button. |
| [#5579](https://github.com/Hmbown/CodeWhale/issues/5579) | Plugin UX parity with Claude Code | Users want proactive plugin recommendations and hot-reload discoverability matching Claude Code's plugin experience. | **Closed** — PR #5663 delivered the prompt-level suggestion feature. |
| [#4402](https://github.com/Hmbown/CodeWhale/issues/4402) | v0.9.2 Attention UX | Addresses the lack of a unified "attention contract" — notifications are elapsed-time based rather than focus-aware, and title state is inconsistent. | 2 comments; still open, flagged as UX reliability concern. |
| [#5668](https://github.com/Hmbown/CodeWhale/issues/5668) | `/copy` for last completed output | No direct command exists to copy the most recent assistant response; users must manually select terminal text, especially awkward after long turns. | 2 comments; straightforward feature gap. |
| [#5681](https://github.com/Hmbown/CodeWhale/issues/5681) | Extend native web search to DeepSeek, Qwen, Kimi, Z.AI, MiMo | Users of first-party Chinese model providers (DeepSeek, Alibaba ModelStudio, Moonshot/Kimi, Z.AI, Xiaomi MiMo) currently fall through to separately configured search backends instead of using provider-native routes. | 0 comments; just opened. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5710](https://github.com/Hmbown/CodeWhale/pull/5710) | ci(review): install libdbus-1-dev | **Closed** | Fixes CI `cargo build` failure on `ubuntu-latest` by installing `libdbus-1-dev` + `pkg-config` before building the reviewer — mirrors existing retry-wrapped apt step. |
| [#5703](https://github.com/Hmbown/CodeWhale/pull/5703) | feat(tui): match Operate to landed CWC OperateRecord | **Open** | Aligns `cw · operate` to the CWC `OperateRecord` schema: camelCase fields (`burnRate`, `leadPlan`, `pace`, `cancelled`) and full REST API parity (`GET/POST/PATCH /v1/operate`, `PUT /plan`, etc.). |
| [#5708](https://github.com/Hmbown/CodeWhale/pull/5708) | feat(tui): Tideline components per ratatui spec | **Open** | Implements the remaining 12 Tideline UI components as standalone render modules with golden buffers, following the topbar component pattern. |
| [#5701](https://github.com/Hmbown/CodeWhale/pull/5701) | feat(cli): Daytona cloud-agent dispatch | **Closed** | Adds first-class `/dispatch` (alias `cloud-agent`) so local `cw` can propose a Daytona cloud agent against explicit `github`, `cnb`, or `gitee` remotes. |
| [#5709](https://github.com/Hmbown/CodeWhale/pull/5709) | docs: Agent identity map across surfaces | **Open** | Single-page reference (`CODEWHALE_AGENT.md`) mapping the Codewhale Agent identity across GitHub PR-review, TUI, and web surfaces. |
| [#5707](https://github.com/Hmbown/CodeWhale/pull/5707) | docs: GitHub App setup guide | **Open** | Plain-language guide for configuring `codewhale review --pr --post` as a dedicated GitHub App bot identity (`codewhale-agent[bot]`). |
| [#5663](https://github.com/Hmbown/CodeWhale/pull/5663) | feat(tui): suggest plugins from the prompt | **Closed** | Delivers proactive plugin suggestions at the prompt level — if a user mentions "Supabase" and has the plugin, a toast appears rather than requiring a manual `/plugin suggest` call. |
| [#5647](https://github.com/Hmbown/CodeWhale/pull/5647) | fix(web): rescue pricing and legal routes | **Closed** | Supersedes #5639; makes `/pricing` a real honest page (open-source free, hosted Member described but no Buy action) and fixes 404s on legal routes. |
| [#5704](https://github.com/Hmbown/CodeWhale/pull/5704) | fix(auth): one login path that stores session | **Closed** | Fixes logout not clearing the Codewhale account session and Daytona token; adds a proper `/login` TUI command. |
| [#5706](https://github.com/Hmbown/CodeWhale/pull/5706) | feat(tui): headless PR review with GitHub posting | **Closed** | `codewhale review --pr N [--post]` runs a headless advisory review; with `--post` it publishes a structured COMMENT review anchored to the PR head SHA. |
| [#5686](https://github.com/Hmbown/CodeWhale/pull/5686) | feat(web): add Moonshot and Kimi native search | **Open** | Adds native web search for Moonshot/Kimi product routes (K3 Formula, legacy K2.6 `$web_search`, Kimi Code membership `/search`) with bounded execution (4 rounds, 8 tool calls max). |
| [#5700](https://github.com/Hmbown/CodeWhale/pull/5700) | feat(web): local GT pipeline for website/docs | **Closed** | Adopts General Translation as the website/docs i18n pipeline into the existing runtime — not a second system, seeded from live dictionaries. |
| [#5699](https://github.com/Hmbown/CodeWhale/pull/5699) | fix(tui): first-class shells on the work strip | **Closed** | Background shells are now a first-class work type with a navigable `▾ Shells N` group; cancel via `/jobs cancel <id>` or `/jobs cancel all`. |
| [#5705](https://github.com/Hmbown/CodeWhale/pull/5705) | chore: remove verified-dead code | **Closed** | 2 unused dependencies and 9 dead functions removed across 13 files (+4/−143 lines); verified under `deny(warnings)` policy. |

**Dependabot bumps:** `schemaui` 0.12.3→0.12.4 (#5695), `rio-vt` 0.5.25→0.5.26 (#5694), `typescript` 5.9.3→7.0.2 (#5671), `next` 15.5.21→16.3.3 (#5673), `tailwindcss` 3.4.19→4.3.3 (#5670).

---

## 5. Feature Request Trends

- **Provider-native integrations** — Multiple issues and PRs converge on expanding first-party provider support: web search for DeepSeek, Qwen, Kimi, Z.AI, MiMo (#5681, #5686); pre-built config templates for third-party providers (#5350).
- **Plugin ecosystem parity** — Users repeatedly request Claude Code–level plugin UX: proactive suggestions (#5579, #5663), hot-reload, and discoverability.
- **Attention & notification UX** — Focus-aware notifications, terminal-title state consistency, and return-recap (#4402) signal demand for better session awareness in long-running agent workflows.
- **Credential & session management** — The auth/session fix (#5704) and the `/copy` command (#5668) reflect ongoing requests for more polished, first-class CLI ergonomics.

---

## 6. Developer Pain Points

1. **Third-party provider onboarding friction** — Manual configuration of Base URLs, model names, and secret env vars for providers like OpenCode Zen, Agnes, and Sensenova was a frequent newcomer blocker, now partially addressed with pre-built templates (#5350).
2. **CI fragility on Ubuntu** — Missing system dependencies (`libdbus-1-dev`) caused build failures in the review workflow, now patched (#5710).
3. **Cookie-cutter session/auth bugs** — Logout not clearing account session and Daytona tokens pointed to a fragmented auth surface; consolidated into a single login path (#5704).
4. **Missing ergonomic shortcuts** — Lack of `/copy` for the last model output and lack of prompt-level plugin suggestions were both called out as productivity gaps, now resolved (#5668, #5663).
5. **Dead code accumulation** — With `deny(warnings)` enforced, dead code hides behind `allow`/`expect` attributes, requiring periodic sweep campaigns (#5705).

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*