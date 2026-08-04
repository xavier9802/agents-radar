# AI CLI Tools Community Digest 2026-08-04

> Generated: 2026-08-04 03:18 UTC | Tools covered: 10

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



# AI CLI Tools — Cross-Tool Comparison Report
**Date: 2026-08-04**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem is in a phase of rapid maturation, with all major vendors shipping incremental releases while grappling with the same class of problems: session reliability, cross-platform parity, and model-routing flexibility. The landscape has consolidated around six actively maintained tools (Claude Code, OpenAI Codex, Gemini CLI, GitHub Copilot CLI, Qwen Code, OpenCode) plus two rising alternatives (Pi, DeepSeek TUI), while Grok Build remains dormant. Feature competition is shifting from raw capability to reliability—compaction, session persistence, subagent orchestration, and trust-boundary hardening dominate community discourse across every project.

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs (24h) | Releases (24h) | Release Status |
|------|-----------|---------------|----------------|----------------|
| **Claude Code** | 10 | 1 | v2.1.221 | Active — Focus View shipped |
| **OpenAI Codex** | 10 | 10 | v0.147.0-alpha.6, alpha.1.2 | Alpha — 20+ PRs merged this cycle |
| **Gemini CLI** | 10 | 10 | None | Active — reliability patch wave |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.78-3 | Active — timeline headers, `/new-worktree` |
| **Kimi Code** | 3 | 8 | None | Active — batch stability fixes |
| **OpenCode** | 10 | 10 | v1.18.12 | Active — Azure completion fix |
| **Pi** | 10 | 10 | None | Active — Harness v2, server backend |
| **Qwen Code** | 10 | 10 | v0.21.5, v0.21.4 | Active — Electron→Tauri bridge, Web Shell GA |
| **DeepSeek TUI** | 10 | 11 | v0.9.4 RC (#5135) | Active — Runtime API expansion |
| **Grok Build** | 0 | 0 | None | Dormant |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|-----------|---------------|---------------|
| **BYOK / Multi-model flexibility** | Claude Code (#13585), Copilot CLI (#3282, #3709), OpenCode (#12789), DeepSeek TUI (#1481) | Switch models mid-session without restart; include local/BYOK endpoints in model pickers |
| **Session reliability & compaction** | Codex (#25779, #21134), Gemini CLI (#28671, #28672), Pi (#7020, #7253), Qwen Code (#8452, #8356), OpenCode (#16562) | Post-compaction continuation, context corruption prevention, session-state bloat |
| **Persistent memory / cross-session context** | Kimi Code (#1283), DeepSeek TUI (#2492), Qwen Code (#8168, #8507), Gemini CLI (#26522) | Retain project patterns and user preferences between sessions |
| **Subagent / multi-agent orchestration** | Gemini CLI (#22323, #21409), Codex (#34700), OpenCode (#21632), DeepSeek TUI (#4022) | Reliable subagent lifecycle, correct routing, permission controls |
| **Windows / WSL cross-platform parity** | Codex (#20214, #20730), Copilot CLI (#4328), Pi (#7064, #6817, #6596), Qwen Code (#8385, #8330), DeepSeek TUI (#5095, #1854) | Path translation, terminal key-binding leaks, process management |
| **MCP server configuration & trust** | Gemini CLI (#28549, #28481), OpenCode (#40125), Qwen Code (#8492), Kimi Code (#2580) | Per-server trust controls, OAuth token refresh, stale registration cleanup |
| **Quota / cost visibility** | Claude Code (#13585, #82506), Codex (#33685), Copilot CLI (#4351), Pi (#7553) | Real-time usage data, billing transparency, mid-session spend tracking |
| **Runtime API / programmatic control** | DeepSeek TUI (#5130, #5131, #5129), Gemini CLI (#28676), Qwen Code (#7800, #8320) | HTTP endpoints for goals, MCP, memory, skills; cooperative pause/resume |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Qwen Code | Pi | OpenCode | Kimi Code | DeepSeek TUI |
|-----------|-------------|--------------|------------|-------------|-----------|-----|----------|-----------|--------------|
| **Primary focus** | Enterprise agent workflows, sandbox hardening | Desktop CLI reliability, multi-agent routing | Subagent autonomy, browser automation | GitHub-integrated workflows, BYOK flexibility | Trust-boundary architecture, workflow orchestration | Session durability, provider diversity | Open-source extensibility, plugin middleware | Stability under constraint (Windows, encoding) | Runtime API surface, ACP editor integration |
| **Target users** | Enterprise, security-conscious teams | General developers, Windows-heavy users | Power users, custom-skill authors | GitHub Copilot subscribers, BYOK adopters | Chinese-market users, cost-conscious teams | Desktop-first users, multi-provider | Open-source contributors, plugin developers | Lightweight TUI users, DeepSeek-V4 access seekers |
| **Technical approach** | Hook system, sandbox credential masking, Focus View | Rust CLI, SQLite state DB, dual-WebSocket transport | Agent registry, Auto Memory, AST-aware tooling | Plugin ecosystem, worktree workflows, timeline headers | Electron→Tauri migration, cooperative pause/resume | Harness v2, in-memory session storage, server-side fallbacks | Effect-native plugins, context-hook tool renaming | asyncio task lifecycle, ACP question handling | Runtime API CRUD, ACP tool-execution over `session/prompt` |
| **Release cadence** | Steady minor bumps | Alpha cadence, 20+ PRs/cycle | Patch-heavy, no formal release | Bi-weekly-ish | Steady PRs, no release | Steady PRs, no release | Bi-weekly | Release train approach | RC train (#5135) |

---

## 5. Community Momentum & Maturity

**Most active communities (by issue engagement + PR velocity):**
- **OpenAI Codex** — Highest single-issue engagement (78 👍 on Windows freezes), 10 merged PRs in 24h, alpha cadence signals rapid iteration
- **DeepSeek TUI** — 11 PRs in the v0.9.4 release train, Runtime API expansion is architecturally ambitious, Chinese-language community is highly engaged
- **Pi** — 10 PRs covering session storage, provider expansion, and terminal hardening; Harness v2 signals architectural maturity
- **Qwen Code** — 10 PRs including security hardening (#8396), Tauri migration, and Web Shell GA; strong engineering velocity

**Mature but steadier:**
- **Claude Code** — High-engagement issues (115 👍 on quota API) but only 1 PR in 24h; suggests a more polished but less rapidly-changing codebase
- **Gemini CLI** — 10 PRs focused on reliability fixes; no release indicates patch-driven cadence

**Growing but narrower:**
- **Kimi Code** — 8 interconnected PRs from a single contributor; smaller community but focused stability work
- **OpenCode** — 10 PRs with strong plugin/MCP direction; community is actively shaping the extensibility model
- **Copilot CLI** — 0 PRs in 24h but high-visibility feature requests (BYOK, scoped plugins); community driven by GitHub ecosystem lock-in

---

## 6. Trend Signals

1. **Compaction is the new frontier of session reliability.** Every major tool has compaction-related bugs (Pi double-trigger, Qwen microcompaction cache invalidation, Copilot context loss, Gemini quota-fallback corruption). Tools that solve post-compaction continuity will have a significant UX advantage.

2. **BYOK and multi-model routing are table stakes.** Five tools face community pressure to allow mid-session model switching. The current pattern—a single env var or hardcoded model picker—is universally regarded as a blocking deficiency.

3. **Trust-boundary hardening is accelerating.** Qwen Code's four-hole security patch (#8396), Gemini's Plan Mode transparency fix (#28549), and Claude's `heron_brook` prompt-injection override (#80988) signal that the community is treating agent security as a first-class concern, not an afterthought.

4. **Runtime APIs are emerging as a differentiator.** DeepSeek TUI's HTTP CRUD for goals/MCP/memory/skills, Qwen Code's cooperative pause/resume, and Gemini's session-reload fixes suggest the next competitive layer is programmatic controllability—not just CLI UX.

5. **Windows/WSL parity remains the cheapest place to win trust.** Six of nine active tools have open Windows-specific bugs (path translation, key-binding leaks, linker issues, terminal crashes). A tool that delivers seamless Windows + WSL2 experience would capture significant goodwill.

6. **Persistent memory is the unsolved problem.** Five tools have open memory/retention feature requests with sustained community interest. No tool has shipped a robust, cross-session memory system yet—this is an open competitive opportunity.

7. **Grok Build's dormancy is a signal.** With zero activity, xAI's CLI tool appears deprioritized, suggesting the market is consolidating around the nine active projects rather than expanding.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-04 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | PR | Skill | Status | Activity |
|---|-----|-------|--------|----------|
| 1 | [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit** | OPEN | Mechanical file verification + four-dimension reasoning quality gate. Covers any project/stack/model. Pre-task calibration → adversarial review → delivery verification pipeline. |
| 2 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator (run_eval fix)** | OPEN | Fixes a critical bug where `run_eval.py` always reported `recall=0%` across all descriptions, making the description-optimization loop produce no improvements. Also fixes Windows stream reading and parallel worker issues. |
| 3 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | OPEN | Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universal pain point in generated output quality. |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | **ODT** | OPEN | Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods). Triggers on ODT/ODS/ODF/LibreOffice keywords. Fills a gap in non-Microsoft office suite support. |
| 5 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer & skill-security-analyzer** | OPEN | Two meta-skills: one evaluates skill quality across 5 dimensions (Structure, Documentation, Examples, etc.), the other audits for security vulnerabilities in skill definitions. |
| 6 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | OPEN | Comprehensive testing coverage: Testing Trophy philosophy, AAA unit tests, React component tests with Testing Library, edge cases, and what *not* to test. |
| 7 | [#302](https://github.com/anthropics/skills/pull/1302) | **color-expert** | OPEN | Color naming systems (ISCC-NBS, Munsell, XKCD, RAL), color spaces comparison table, and practical guidance for gradients/scales/accessibility. Niche but thorough. |
| 8 | [#525](https://github.com/anthropics/skills/pull/525) | **pyxel** | OPEN | Retro/pixel-art game development with the Pyxel engine via MCP. Covers write → run_and_capture → inspect → iterate workflow. |

---

## 2. Community Demand Trends

Analysis of the top-commented Issues reveals three dominant demand signals:

- **Self-correction & quality gates** — Issue #1385 and PR #1367 both describe multi-stage reasoning pipelines (pre-task calibration → adversarial review → delivery verification). The community is pushing skills that audit AI output *before* it reaches the user, not just during generation.
- **Cross-platform & OS compatibility** — Issues #1061, #1169, #556, and #1050 collectively highlight that the `skill-creator` tooling is broken on Windows (subprocess PATHEXT, cp1252 encoding, pipe handling). This is the most actively debated compatibility problem.
- **Trust & security boundaries** — Issue #492 (43 comments, 2 👍) raises the critical concern that community skills distributed under the `anthropic/` namespace can impersonate official skills, creating trust boundary abuse. Issue #1175 flags context-window exhaustion from eagerly-injected content (~156k tokens in `claude-api`).
- **Organization-level sharing** — Issue #228 (16 comments, 8 👍) requests native org-wide skill sharing in Claude.ai, eliminating the current manual download/upload friction.

---

## 3. High-Potential Pending Skills

These PRs have active community attention and address clear gaps, but remain open:

| PR | Skill | Why It May Land Soon |
|----|-------|---------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator fix** | Blocks the entire description-optimization workflow; 10+ independent reproductions; overlaps with multiple issues (#556, #1169, #1050, #1099). A merge would resolve the most-reported bug class. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit** | Directly addresses Issue #1385's proposed pipeline. Covers a universal need (any project, any stack) with a well-scoped two-step approach (mechanical + reasoning). |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a frequent, visible quality problem in generated documents. Low risk, high user-facing value. |
| [#1479](https://github.com/anthropics/skills/pull/1479) | **plan-file-hygiene** | Addresses Issue #1417 (planning artifacts accumulate with no lifecycle). Timely as agent sessions grow longer and more complex. |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Comprehensive scope covering the full testing stack; fills a notable gap in the current skill catalog. |
| [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer** | Meta-skill that helps the community improve other skills — strong network effect if adopted. |

---

## 4. Ecosystem Insight

> The community's most concentrated demand is for **reliable skill tooling and output quality gates** — specifically, fixing the broken `skill-creator` evaluation pipeline and adding pre-delivery audit skills — rather than for additional domain-specific skills, indicating the ecosystem is maturing from "more skills" to "better, more trustworthy skills."

---



# Claude Code Community Digest — 2026-08-04

## 1. Today's Highlights

Claude Code v2.1.221 shipped with a new **Focus View** for VSCode (collapsible tool activity, toggled `Ctrl+Alt+F`) and `mode: "mask"` for sandbox credential files on Linux. Community attention remains dominated by the long-running **Cowork network egress allowlist** bug (54 comments, 51 👍) and a strong feature-request push for **real-time priority message steering** mid-execution (60 👍).

---

## 2. Releases

### v2.1.221
- **[VSCode] Focus View:** A chat-menu toggle hides per-turn tool activity behind an expandable summary with a live running-tool indicator. Toggled via `Ctrl+Alt+F` or the *"Claude Code: Toggle Focus view"* command.
- **Sandbox credentials:** Added `mode: "mask"` for sandbox credential files on Linux.

> Full changelog: [anthropics/claude-code](https://github.com/anthropics/claude-code)

---

## 3. Hot Issues

| # | Title | Eng. | Why it matters |
|---|-------|------|----------------|
| [#30112](https://github.com/anthropics/claude-code/issues/30112) | Cowork network egress allowlist not working — custom domains blocked with 403 | 54 🗨 · 51 👍 | Blocked third-party domains (Openverse, Wikimedia, own domains) break scheduled RemoteTriggers and content-pipeline automation. |
| [#30492](https://github.com/anthropics/claude-code/issues/30492) | Real-time steering: priority message channel for redirecting Claude mid-execution | 31 🗨 · 60 👍 | Users running multi-step pipelines want to inject steering prompts without restarting the session. |
| [#13585](https://github.com/anthropics/claude-code/issues/13585) | Add Quota Information Access to Claude Code CLI | 24 🗨 · 115 👍 | The single highest-👍 open issue. Direct API access to usage/quota data is needed for budget-aware automation and self-hosted setups. |
| [#10621](https://github.com/anthropics/claude-code/issues/10621) | Require double ESC in Vim mode to clear message in Plan Mode Q&A | 22 🗨 · 29 👍 | Vim-mode users accidentally erase messages with a single ESC during Plan Q&A; a minor UX friction point with broad appeal. |
| [#67606](https://github.com/anthropics/claude-code/issues/67606) | Opus 4.8 confabulates user messages & fabricates tool/host facts in long sessions | 15 🗨 · 4 👍 | JSONL-verified confabulation in Opus 4.8 on extended sessions — raises reliability concerns for critical workflows. |
| [#80988](https://github.com/anthropics/claude-code/issues/80988) | `heron_brook` prompt section injects "Do not call AgentTool" for Opus 5, overriding user config | 15 🗨 · 33 👍 | A hidden prompt-injection silently overrides explicit delegation settings with no opt-out — trust issue for enterprise users. |
| [#82506](https://github.com/anthropics/claude-code/issues/82506) | Claude Max usage bug: session limit consumed without use | 12 🗨 · 6 👍 | Session quota consumed without actual usage reported — impacts billing fairness on Max subscriptions. |
| [#61280](https://github.com/anthropics/claude-code/issues/61280) | Desktop app: auto-expand Edit/Write diffs by default | 6 🗨 · 20 👍 | Reviewing conversations with many edits requires clicking each collapsed diff card manually; a small quality-of-life request. |
| [#82536](https://github.com/anthropics/claude-code/issues/82536) | `--continue` cannot find sessions created by `-p` (interactive resume) | 5 🗨 · 0 👍 | Broken session-resume path limits scripting workflows that combine non-interactive `-p` with interactive `--continue`. |
| [#79997](https://github.com/anthropics/claude-code/issues/79997) | 2.1.216 sandbox regression: `bwrap: Can't mkdir /opt/.claude` on non-root installs | 4 🗨 · 2 👍 | Root-owned mountpoint denyWrite causes sandbox to fail-closed for non-root users — blocks deployments in shared/containerized environments. |

---

## 4. Key PR Progress

Only **1 PR** updated in the last 24 h:

| # | Title | Author | Status |
|---|-------|--------|--------|
| [#83374](https://github.com/anthropics/claude-code/pull/83374) | docs(plugin-dev): document MessageDisplay streaming semantics | @iCodeCraft | Open — adds `MessageDisplay` to the bundled Hook Development skill's trigger description, event guidance, and quick-reference table (currently omitted despite being a supported hook event). |

---

## 5. Feature Request Trends

1. **Usage & quota API access** — The highest-👍 issue (#13585, 115 👍) and supporting requests (#81015, #70225) show strong demand for programmatic, read-only quota/usage data via `setup-token` scope and mid-session billing transparency.
2. **Real-time session steering** — #30492 (60 👍) signals a growing need for priority message channels that let users redirect an in-flight agent without restarting.
3. **Desktop UX polish** — Auto-expanded diffs (#61280, 20 👍), customizable sidebar project group names (#81063), and Focus View (now shipped in v2.1.221) reflect ongoing pressure to make the desktop experience more review-friendly.
4. **Sandbox & credential hardening** — `mode: "mask"` for credential files (shipped) and the non-root sandbox regression (#79997) indicate the community wants robust, non-root-friendly sandboxing with clearer credential management.
5. **Model version flexibility** — #83683 (restore Opus 4 access) and #67606 (Opus 4.8 confabulation) suggest users want both backward-compatible model choices and confidence in reliability.

---

## 6. Developer Pain Points

- **Network egress allowlist unreliability** — Multiple overlapping issues (#30112, #82090) report custom and open-license domains blocked with 403, breaking scheduled/cloud-automation workflows for weeks.
- **Hooks failing silently** — A family of bugs (#83687, #83366, #82323, #83705) shows hooks and background-agent spawns can fail with no diagnostic signal, making debugging extremely difficult.
- **Auth/OAuth friction** — Sentry MCP OAuth (#81643) and GitHub integration 403s (#80874) point to persistent OAuth scope and connector lifecycle issues across integrations.
- **Desktop session hygiene** — Dead Remote Control bridge handles accumulate (#83378), and claude.ai connectors don't attach to spawned sessions until the first inbound message (#83694), causing silent tool-missing bugs.
- **Terminal rendering edge cases** — Kitty terminal rejects DECSET mode 2031 during trust-dialog transitions (#83701), and the file-suggester fails to dismiss after space/newline (#83708), both causing visual/input glitches in common terminal setups.
- **Cost visibility gaps** — Despite the high-demand #13585, Mid-session subscription→API billing transitions (#70225) and silent session-limit consumption (#82506) still leave users uncertain about real-time spend.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-04

## 1. Today's Highlights
The Codex team shipped two Rust‑CLI alpha releases (0.147.0‑alpha.6 and 0.147.0‑alpha.1.2) while community attention remains fixed on Windows performance regressions and multi‑agent‑v2 subagent‑routing bugs. A wave of 20+ merged PRs this cycle targets session‑state hygiene, MCP‑tool exposure controls, and test‑stability improvements.

## 2. Releases
**rust‑v0.147.0‑alpha.6** ([link](https://github.com/openai/codex/releases/tag/rust-v0.147.0-alpha.6))  
**rust‑v0.147.0‑alpha.1.2** ([link](https://github.com/openai/codex/releases/tag/rust-v0.147.0-alpha.1.2))  
Both are early‑access CLI builds; no detailed changelogs were attached.

## 3. Hot Issues
1. **#20214 – Codex App frequently freezes/stutters on Windows 11 Pro** (88 comments, 78 👍) – High‑visibility performance regression affecting a large portion of the Windows user base.  
2. **#33685 – Weekly limit is draining like the old 5‑hour limit** (25 comments, 10 👍) – Raises concerns about quota‑accounting changes for Plus subscribers.  
3. **#12098 – Tabbed interface for parallel chat sessions in the IDE extension** (20 comments, 55 👍) – Strong community demand for a UX improvement that would streamline multi‑session workflows.  
4. **#20730 – Custom pets fail to load in WSL environments** (18 comments, 23 👍) – Path‑normalization bug that blocks a popular customization feature.  
5. **#21134 – Codex Desktop becomes unusable on long active threads** (15 comments, 0 👍) – Memory‑leak / log‑churn issue that degrades extended coding sessions.  
6. **#25779 – Meta‑bug: unbounded session/turn state causes freezes, context bloat, and lost active‑turn control** (15 comments, 8 � 👍) – Summarizes a class of desktop‑app stability problems.  
7. **#24514 – IDE context could not be enabled** (13 comments, 6 👍) – Blocks the CLI extension from picking up workspace context on Linux.  
8. **#12029 – Ability to use more than one account** (12 comments, 62 👍) – Frequently cited blocker for enterprise and personal‑account users.  
9. **#28080 – Desktop thread tools intermittently lose handlers (`No handler registered`)** (12 comments, 2 👍) – Tool‑call reliability issue on Windows.  
10. **#34700 – spawn_agent rejects gpt‑5.6‑luna with multi_agent_v2 enabled** (9 comments, 24 👍) – Multi‑agent‑v2 routing bug that prevents Luna from being used as a child agent.

## 4. Key PR Progress
1. **#36825 – Consolidate approval telemetry context** – Reduces redundant telemetry parameters by attaching the tool name and call ID to `ApprovalCtx`.  
2. **#36822 – Fix typo in approval resolver name** – Renames `resolve_tool_apporval` to `resolve_tool_approval` and updates call sites.  
3. **#36815 – Identify agents by name in token budget context** – Replaces thread IDs with canonical agent paths in `<context_window>` metadata.  
4. **#36812 – Add a dual‑WebSocket transport for code mode** – Prevents large nested‑tool callbacks from blocking unrelated session operations.  
5. **#36811 – Honor per‑environment login shell policy** – Stores and exposes `allow_login_shell` on each turn environment.  
6. **#36810 – Add MCP client conformance regression gates** – Introduces a harness that runs the Codex executable against the official MCP conformance suite.  
7. **#36809 – Prefer the state database for `exec resume --last`** – Queries the SQLite state DB first, avoiding a full rollout‑file audit.  
8. **#36808 – Prefer SQLite names for local session archive commands** – Resolves `archive`/`delete`/`unarchive` targets from SQLite before falling back to rollout scanning.  
9. **#36807 – Extract audio preparation into a utility crate** – Creates `codex‑utils‑audio` for canonicalizing audio inputs and estimating token usage.  
10. **#36800 – Avoid reinjecting permissions after command approvals** – Tracks approved command prefixes separately, emitting only new prefixes after an exec‑policy amendment.

## 5. Feature Request Trends
- **Multi‑account & multi‑tenant support** – Issue #12029 highlights a strong desire for separate personal/corporate authentication without switching profiles.  
- **Tabbed parallel chat sessions** – Issue #12098 reflects a recurring request for a tab‑based UI in the IDE extension to manage multiple conversations.  
- **Inline ghost‑suggestion controls** – Issue #10562 asks for the ability to disable distracting pre‑filled suggestions in the CLI TUI.  
- **Arabic audio transcription to Excel** – Issue #36819, while niche, signals demand for multilingual audio‑to‑structured‑data workflows.

## 6. Developer Pain Points
- **Windows performance & stability** – Frequent freezes, stuttering, slow thread switching, and tool‑handler loss dominate the top issues.  
- **Multi‑agent‑v2 routing inconsistencies** – Several reports (#34700, #36294, #34964) indicate that Luna and other models are incorrectly filtered or rejected by `spawn_agent`.  
- **Quota‑drain confusion** – Users report that weekly limits are being consumed at rates comparable to the deprecated 5‑hour cap, suggesting a accounting or rate‑limiting regression.  
- **Session‑state bloat** – Long‑running desktop sessions suffer from memory growth and context‑window exhaustion, leading to unresponsive UIs.  
- **WSL / path‑normalization bugs** – Custom pets and other path‑sensitive features fail when Windows and WSL path styles clash.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-04

---

## 1. Today's Highlights

No new releases were published in the last 24 hours. Community activity focused on agent reliability fixes — subagent recovery after turn limits, browser agent resilience improvements, and a security patch for MCP OAuth token refresh. Several core session-completion bugs (context corruption, quota fallback) also received active PR attention.

---

## 2. Releases

**No new releases** in the last 24 hours.

---

## 3. Hot Issues

### 1. Subagent reports GOAL success despite hitting MAX_TURNS (#22323)
The `codebase_investigator` subagent claims success with termination reason `GOAL` even though it hit the maximum turn limit before completing any analysis. This false-positive status masks real failures and makes debugging difficult. **12 comments, 2 👍**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/22323)

### 2. Generalist agent hangs indefinitely (#21409)
When Gemini CLI defers to the generalist agent, the process hangs forever — even for simple tasks like folder creation. Users report waiting up to an hour before manually cancelling. A known workaround is disabling sub-agent use entirely. **8 comments, 8 👍** (highest engagement).
[View Issue](https://github.com/google-gemini/gemini-cli/issues/21409)

### 3. Gemini does not use skills and sub-agents on its own (#21968)
Users report that custom skills (e.g., "gradle", "git") and sub-agents are effectively ignored unless explicitly instructed. This undermines the value of investment in skill authoring. **6 comments**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/21968)

### 4. Auto Memory retries low-signal sessions forever (#26522)
Auto Memory's candidate-session tracker only marks a session as processed on successful transcript read. Low-signal sessions that the agent chooses to skip remain perpetually unprocessed and get re-surfaced, creating noise. **5 comments**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/26522)

### 5. Shell commands stuck showing "Waiting input" after completion (#25166)
After executing simple CLI commands, Gemini CLI hangs while still showing the shell command as active with "Awaiting user input." The command has already finished but the UI doesn't reflect this. **4 comments, 3 👍**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/25166)

### 6. Browser agent fails on Wayland (#21983)
The `browser_agent` fails to run in Wayland environments, returning an empty result with `Termination Reason: GOAL`. This blocks Linux desktop users. **4 comments, 1 👍**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/21983)

### 7. Model creates temp scripts in random directories (#23571)
When restricted to shell execution, the model generates edit scripts scattered across arbitrary directories, creating significant cleanup overhead for users. **3 comments**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/23571)

### 8. Agent should stop/discourage destructive behavior (#22672)
Users report the agent occasionally uses dangerous commands like `git reset --hard` or `--force` when safer alternatives exist, especially during complex git operations and database management. **3 comments, 1 👍**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/22672)

### 9. Browser Agent ignores `settings.json` overrides (#22267)
Configuration overrides in `settings.json` (e.g., `maxTurns`) are silently ignored by the browser agent, despite `AgentRegistry` correctly reading them at initialization. **3 comments**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/22267)

### 10. Subagents running without permission since v0.33.0 (#22093)
After upgrading to v0.33.0, users report that subagents (e.g., generalist) run automatically even when agents mode is set to disabled in all configurations. Previously this was never active. **3 comments**.
[View Issue](https://github.com/google-gemini/gemini-cli/issues/22093)

---

## 4. Key PR Progress

### 1. Forward termination signals to relaunched child process (#28676)
Fixes orphaned child processes by forwarding `SIGTERM`, `SIGHUP`, `SIGINT`, `SIGQUIT`, `SIGUSR1`, and `SIGUSR2` from the bootstrap parent to the spawned child. A `kill -TERM` on the bootstrap PID now properly terminates the entire process tree.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28676)

### 2. Strip Authorization header when using GEMINI_API_KEY auth (#28546)
Fixes a `401 UNAUTHENTICATED ACCESS_TOKEN_TYPE_UNSUPPORTED` error where a stale `Authorization` header interfered with the `x-goog-api-key` auth mechanism. Critical for users relying on API key authentication.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28546)

### 3. Disclose Plan Mode read-only status is a server claim (#28549)
Clarifies that `readOnlyHint` is an MCP server assertion, not something Gemini verifies. Tools annotated as read-only are promoted out of Plan Mode's deny-all into the ask-us-first list without backend validation. Security transparency fix.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28549)

### 4. Prevent malformed GitHub JSON from crashing extensions (#28657 / #28663)
Two PRs hardening extension reliability: `fetchJson` in `github_fetch.ts` now catches `JSON.parse` failures and stream errors instead of leaking uncaught exceptions that crash extension operations.
[View PR #28657](https://github.com/google-gemini/gemini-cli/pull/28657) · [View PR #28663](https://github.com/google-gemini/gemini-cli/pull/28663)

### 5. Add Gemini 3.6 Flash and 3.5 Flash-Lite model configs (#28673)
Adds base model definitions, capabilities (`thinking`, `multimodalToolUse`), aliases, and Code completion support for the new Gemini 3.6 Flash and 3.5 Flash-Lite models.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28673)

### 6. Fix context corruption and quota error fallback issues (#28671)
Addresses two related bugs: context corruption when tool executions are interrupted (e.g., user ESC queries), and model "autocomplete" prefix-continuation behavior that occurs on quota fallback. Introduces defensive history hardening.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28671)

### 7. Don't start voice recording before providers are ready (#28658)
`TranscriptionProvider.connect()` now resolves only when the selected backend (Whisper or Gemini Live) is actually ready to accept audio, preventing recording against a dead process or incomplete protocol setup.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28658)

### 8. Keep sendStream alive on malformed tool arguments (#28660)
Defensively parses string-valued SDK tool arguments in `sendStream()` — rejects arrays, primitives, and `null` as invalid, converting them to structured `functionResponse` errors instead of crashing the stream.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28660)

### 9. Refresh MCP OAuth tokens with stored client ID (#28481)
Fixes MCP OAuth token refresh for servers configured via OAuth discovery + dynamic client registration. The bug deleted stored credentials before any network I/O, forcing re-auth on every startup.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28481)

### 10. Fix /compress session reload and quota-fallback tool response loss (#28672)
Two fixes in one PR: repairs the `/compress` command which fails with `Failed to load resumed session data from file` due to a hard throw during session re-initialization, and addresses tool response loss during quota-fallback transitions.
[View PR](https://github.com/google-gemini/gemini-cli/pull/28672)

---

## 5. Feature Request Trends

1. **AST-aware tooling** — Multiple issues (#22745, #22746) track investigations into using AST-aware file reads, search, and codebase mapping to reduce turns and token noise. The community sees clear value in precise method-bound reads and hierarchical navigation.

2. **Subagent trajectory visibility** — Issue #22598 requests that subagent trajectories be accessible via `/chat share`, making it easier to review and evaluate subagent behavior without digging into internal storage.

3. **Agent self-awareness** — Issue #21432 requests that Gemini CLI understand its own mechanics (CLI flags, hotkeys, self-execution) well enough to act as its own expert guide.

4. **Local subagent infrastructure** — Issue #20195 tracks the broader local subagent sprint work, indicating continued investment in making subagents a first-class capability.

5. **Destructive operation guardrails** — Issue #22672 calls for the agent to proactively discourage dangerous commands (`git reset --hard`, `--force`) when safer alternatives exist.

---

## 6. Developer Pain Points

- **Subagent reliability** dominates the top complaints: false-positive success reports (#22323), infinite hangs (#21409), and subagents running without explicit permission (#22093). The agent frequently defers to subagents but doesn't always use skills/subagents on its own (#21968), creating inconsistent behavior that frustrates users who've invested in custom skills.

- **Session and context corruption** is a recurring theme: shell commands stuck in "waiting input" (#25166), context corruption on tool interruption (#28671), and `/compress` breaking session reload (#28672). These affect the core UX reliability.

- **Browser agent fragility**: failures on Wayland (#21983), ignoring `settings.json` overrides (#22267), and a restrictive fail-fast strategy on locked profiles (#22232) make browser automation unreliable for many users.

- **Auto Memory quality**: low-signal sessions are retried indefinitely (#26522), and invalid memory patches are silently skipped rather than quarantined (#26523), leading to noisy and potentially incorrect memory retrieval.

- **Security and auth**: stale `Authorization` header bugs (#28538), MCP OAuth token refresh failures that delete credentials (#28481), and the Plan Mode readOnlyHint trust issue (#28549) show that authentication flows remain a friction point.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-04

## 1. Today's Highlights

Copilot CLI **v1.0.78-3** shipped yesterday with timeline headers for long-running tool calls, auto-updating first-party plugins, and an experimental `/new-worktree` command. The community's top concerns continue to center on BYOK multi-model flexibility, Windows/WSL2 compatibility, and session management quirks around compaction and prompt queuing.

## 2. Releases

**v1.0.78-3** (2026-08-03) — [GitHub](https://github.com/github/copilot-cli/releases/tag/v1.0.78-3)

- **Added:** Timeline headers now display live, right-aligned tool-call durations (≥ 5s) during execution; toggle with `/settings showToolDurations`.
- **Added:** Experimental `/new-worktree` command to create a new worktree and start a conversation within it.
- **Improved:** Interactive shell shortcut now launches on Enter and shows an inline hint when the `$` key is armed.
- **Fixed:** `copilot login` now defaults to the browser-based flow for local desktop authentication.
- **Improved:** First-party plugins automatically update to the latest version at session start.

## 3. Hot Issues

1. **[CLOSED] #1665 — Scoped plugins per project/repository** · 18 👍 · 14 comments
   Plugins are currently per-user/global; request scoped, repo/project-specific plugin installation. [Link](https://github.com/github/copilot-cli/issues/1665)

2. **#3282 — Multiple BYOK models in CLI** · 20 👍 · 7 comments
   Single `COPILOT_MODEL` env var limits switching between BYOK providers inside a session; users need a `/model` picker that includes local/BYOK endpoints. [Link](https://github.com/github/copilot-cli/issues/3282)

3. **#3709 — `/model` switch across BYOK/local providers mid-session** · 20 👍 · 3 comments
   BYOK pins the session to one model; the `/model` picker omits local providers entirely. [Link](https://github.com/github/copilot-cli/issues/3709)

4. **#1464 — Skills beyond position ~32 unreachable** · 7 👍 · 6 comments
   With ~63+ skills installed, the system prompt caps the visible skill list at 32 entries, making alphabetically later skills permanently unselectable by the model. [Link](https://github.com/github/copilot-cli/issues/1464)

5. **[CLOSED] #4078 — Scheduled prompts kill the existing prompt queue** · 5 comments
   When a `/every` or `/after` scheduled prompt fires, it consumes the queued prompt without popping the next item, leaving the queue stuck. [Link](https://github.com/github/copilot-cli/issues/4078)

6. **#4353 — Compact action fires with no confirmation or undo** · 0 comments
   The VS Code Copilot CLI "Compact" button rewrites conversation context instantly with no dialog, warning, or undo path — flagged as a blocker. [Link](https://github.com/github/copilot-cli/issues/4353)

7. **#4328 — Ctrl+H misinterpreted as Ctrl+W under WSL2** · 2 comments
   `WT_SESSION` leaking from Windows Terminal causes `Ctrl+H` (delete char) to behave as `Ctrl+Backspace` (delete word). [Link](https://github.com/github/copilot-cli/issues/4328)

8. **#4337 — gpt-5.6-luna advertised but inaccessible via /chat/completions** · 2 comments · CLOSED
   The model appears in `GET /models` but fails on the standard OpenAI-compatible endpoint, breaking aggregator/MoA tooling that relies on `/chat/completions`. [Link](https://github.com/github/copilot-cli/issues/4337)

9. **#4351 — Session cost total loses spend chunk after first compaction** · 0 comments
   Cost tracking silently drops a fixed amount the first time context compaction succeeds in a process lifetime — accuracy concern for billing. [Link](https://github.com/github/copilot-cli/issues/4351)

10. **#4346 — MCP registry policy returns 403 for Actions GITHUB_TOKEN** · 0 comments
    PAT-less GitHub Actions setup (`copilot-requests: write`) blocks MCP server loading in CI due to a 403 on the MCP registry policy fetch. [Link](https://github.com/github/copilot-cli/issues/4346)

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

- **Multi-model and BYOK flexibility** — Two top-voted issues (#3282, #3709) converge on the same need: the ability to switch between multiple BYOK/local models mid-session without restarting.
- **Scoped plugin installation** — Project/repository-level plugin scoping (#1665) and toggling plugin enablement (#2714, 11 👍) signal demand for per-workspace plugin control.
- **Custom theming & terminal rendering** — Custom color themes (#2830, 6 👍), scrollable conversation history (#4313), table rendering fixes (#2412), and OSC 9;4 progress bar opt-out (#4352) reflect a sustained push for UI polish.
- **Session management reliability** — Scheduled prompt queue bugs (#4078), stashed prompt loss on session switch (#4334), and compact without undo (#4353) show the community values resilient session state.
- **Windows/WSL2 parity** — Git symlink plugin installs (#2286) and terminal key-binding leaks (#4328, #4267) highlight ongoing cross-platform gaps.

## 6. Developer Pain Points

- **BYOK is too rigid:** A single `COPILOT_MODEL` env var and a model picker that ignores local providers forces session restarts when switching models — a daily friction for teams using multiple endpoints.
- **Scheduled prompts are lossy:** The queue-discard bug (#4078) means timed prompts can silently drop user work, eroding trust in automation features.
- **Context compaction is destructive without safeguards:** The no-confirm, no-undo compact action (#4351, #4353) risks irreversible context loss, especially in long sessions.
- **Windows/WSL2 terminal behavior is unreliable:** Key-binding misinterpretation (#4328), raw escape leakage in zellij (#4267), and git symlink plugin failures (#2286) create a fragmented experience on Windows.
- **Skills list is silently truncated:** With token limits capping displayed skills at ~32, users with larger skill catalogs lose access to relevant tools without any visible warning.
- **MCP servers break in CI:** The 403 on MCP registry policy fetch with `GITHUB_TOKEN` (#4346) blocks the documented PAT-less Actions integration from working end-to-end.
- **Session cost tracking is inaccurate:** A fixed spend chunk disappears after the first compaction (#4351), undermining cost visibility for paid or usage-tracked deployments.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-04

## 1. Today's Highlights

The community is actively addressing stability and correctness fixes, with a significant push on session management bugs and ACP mode reliability. A long-standing feature request for a persistent Memory System continues to gather attention, while the contributor `ayaangazali` delivered a batch of eight interconnected fixes spanning web UI, shell, hooks, and LLM tooling.

## 2. Releases

No new releases in the last 24 hours. PR #2581 (closed) bumped `kosong` to 0.56.0, and PR #2580 (closed) fixed an empty `anthropic-beta` header — both are dependency/tooling-level changes rather than full CLI releases.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#1283](https://github.com/MoonshotAI/kimi-cli/issues/1283) | **Feature Request: Memory System — Persistent context across sessions** | A comprehensive memory system would let Kimi retain project patterns and user preferences between sessions — a foundational capability for long-running development workflows. Open since Feb 2026 with 15 comments, signaling sustained interest. |
| [#2573](https://github.com/MoonshotAI/kimi-cli/issues/2573) | **Bug: Web UI "Connecting to session…" infinite spinner on session switch** | Blocks the Technical Preview Web UI (`kimi web`) entirely when switching sessions on macOS ARM64. A critical UX regression that renders the web dashboard unusable for multi-session users. |
| [#2582](https://github.com/MoonshotAI/kimi-cli/issues/2582) | **Bug: CLI stream hangs indefinitely during generation** | Session becomes completely unusable when using `kimi-k2.7-code` on Windows. No comments yet, but a hang-on-generation bug directly impacts core CLI reliability. |

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#2577](https://github.com/MoonshotAI/kimi-cli/pull/2577) | **fix(web,vis): do not crash printing the startup banner on legacy console codecs** | Resolves [#2532](https://github.com/MoonshotAI/kimi-cli/issues/2532). Fixes a crash on Windows GBK consoles when the startup banner contains U+279C, which the codec cannot render. |
| [#2575](https://github.com/MoonshotAI/kimi-cli/pull/2575) | **fix(hooks): fire PostToolUse hooks through fire_and_forget_trigger** | Resolves [#2564](https://github.com/MoonshotAI/kimi-cli/issues/2564). Previously, `asyncio.create_task(...)` was used without retaining a reference, causing pending hook tasks to be garbage-collected mid-execution. |
| [#2554](https://github.com/MoonshotAI/kimi-cli/pull/2554) | **fix(tools): count StrReplaceFile replacements against running content** | Small correctness fix: the success message for `StrReplaceFile` was counting replacements against stale content instead of the live buffer, producing inaccurate output. |
| [#2530](https://github.com/MoonshotAI/kimi-cli/pull/2530) | **fix(shell): stop blocking until timeout when a detached child holds the pipes** | Resolves [#2468](https://github.com/MoonshotAI/kimi-cli/issues/2468). A detached child process (e.g. `some_daemon & echo done`) kept stdout/stderr pipes open, causing the shell to block on `wait_for` until timeout instead of returning immediately. |
| [#2507](https://github.com/MoonshotAI/kimi-cli/pull/2507) | **fix(acp): signal QuestionNotSupported instead of resolving empty answers** | Resolves [#2495](https://github.com/MoonshotAI/kimi-cli/issues/2495). In ACP server mode, every `QuestionRequest` was resolved with an empty dict, making it indistinguishable from an explicit user dismissal. Now properly signals `QuestionNotSupported`. |
| [#2581](https://github.com/MoonshotAI/kimi-cli/pull/2581) | **chore(release): bump kosong to 0.56.0** | Closes the `kosong` dependency bump to 0.56.0 and moves release notes accordingly. |
| [#2580](https://github.com/MoonshotAI/kimi-cli/pull/2580) | **fix(kosong): omit empty anthropic-beta header when no beta features declared** | Prevents the Anthropic provider from sending a useless empty `anthropic-beta` header, addressing a verification report against kosong 0.55.0. |
| [#2535](https://github.com/MoonshotAI/kimi-cli/pull/2535) | **fix(llm): scope prompt cache keys to Moonshot APIs** | Resolves [#2534](https://github.com/MoonshotAI/kimi-cli/issues/2534). Third-party Kimi-compatible endpoints were incorrectly receiving Moonshot's `prompt_cache_key` parameter, which they do not support. Official Kimi and Moonshot APIs retain session caching. |

## 5. Feature Request Trends

- **Persistent Memory & Context Retention**: Issue #1283 dominates the feature request landscape — users want Kimi to remember project patterns, preferences, and context across sessions, split between automatic (AI-managed) and manual (user-defined via config) memory layers.
- **Cross-Platform Shell Robustness**: The shell pipe/detached-child issue (#2468 / #2530) and the ACP question-handling fix (#2495 / #2507) reflect growing demand for the CLI to behave reliably in complex, multi-process environments — especially on Windows.
- **Web UI Maturity**: The infinite spinner bug (#2573) signals that the Technical Preview Web UI needs hardening around session state management before it can be recommended for production use.

## 6. Developer Pain Points

- **Session switching instability**: The Web UI hangs with an infinite spinner when switching sessions (#2573), and the CLI stream can hang indefinitely during generation (#2582). Both point to fragile session lifecycle management.
- **Encoding crashes on Windows**: Legacy consoles (GBK) crash the startup banner (#2532 / #2577), a recurring pain point for Windows users.
- **Hook/task lifecycle bugs**: Bare `asyncio.create_task` calls without reference retention cause silent hook failures (#2564 / #2575), making debugging difficult.
- **Inaccurate tool feedback**: `StrReplaceFile` reporting wrong replacement counts (#2554) and ACP questions resolving as empty dicts (#2495 / #2507) erode trust in tool output correctness.
- **Third-party API compatibility**: Moonshot-specific parameters like `prompt_cache_key` leaking to incompatible endpoints (#2534 / #2535) causes silent errors for users on non-Moonshot providers.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑08‑04

## 1. Today's Highlights
OpenCode v1.18.12 landed with critical bugfixes for Azure GPT‑5.5+ completion requests and desktop composer lag when handling large pasted images. The community is actively discussing model‑compatibility problems, session‑loading failures, and improved MCP‑server configuration options, reflecting a focus on stability and developer‑experience refinements.

## 2. Releases
**v1.18.12** – Core: fixed Azure GPT‑5.5+ completion requests failing when reasoning is enabled. Desktop: reduced composer lag with large pasted images/attachments and expanded project‑search to match any known recent project.  
[GitHub Release](https://github.com/anomalyco/opencode/releases/tag/v1.18.12)

## 3. Hot Issues
| # | Issue | Why It Matters | Community Reaction |
|---|-------|----------------|---------------------|
| [#16218](https://github.com/anomalyco/opencode/issues/16218) | Model repeats the same response in a loop | Highlights a severe generative‑loop bug that can lock sessions. | 19 comments, 0 👍 |
| [#12789](https://github.com/anomalyco/opencode/issues/12789) | “The requested model is not supported” | Affects Copilot provider model selection; users report Claude‑only failures while other models work. | 17 comments, 10 👍 |
| [#7926](https://github.com/anomalyco/opencode/issues/7926) | Disable mouse capture in TUI | Enables proper copy‑paste and keyboard shortcuts inside terminal multiplexers (tmux, Zellij). | 10 comments, 23 👍 |
| [#20954](https://github.com/anomalyco/opencode/issues/20954) | GitHub Copilot models unusable despite active subscription | Blocks Copilot users from GPT, Claude, and Gemini; indicates provider‑integration regression. | 9 comments, 1 👍 |
| [#15892](https://github.com/anomalyco/opencode/issues/15892) | Dollar sign triggers LaTeX rendering | Breaks TUI output for currency values (e.g., `$0.02/GB`) on macOS Desktop. | 9 comments, 5 👍 |
| [#21632](https://github.com/anomalyco/opencode/issues/21632) | Subagent model variants not applied at runtime | After v1.4.0, agent‑level `variant` settings are parsed but ignored, breaking custom model routing. | 7 comments, 3 👍 |
| [#16562](https://github.com/anomalyco/opencode/issues/16562) | Web sidebar sessions disappeared | Users cannot access historical sessions, losing context for ongoing work. | 6 comments, 0 👍 |
| [#29968](https://github.com/anomalyco/opencode/issues/29968) | `--attach` and `--model` do not work together | CLI workflow blocked when attaching to a remote sidecar while specifying a model. | 6 comments, 0 👍 |
| [#30735](https://github.com/anomalyco/opencode/issues/30735) | Allow URLs for linked issues in PRs | Standardizes issue linking with full GitHub URLs, improving automation and readability. | 6 comments, 0 👍 |
| [#30734](https://github.com/anomalyco/opencode/issues/30734) | Regression from PR #23068 | Session‑metadata changes introduced a bug; underscores need for a follow‑up fix. | 5 comments, 0 👍 |

## 4. Key PR Progress
| # | PR | Description |
|---|----|-------------|
| [#40362](https://github.com/anomalyco/opencode/pull/40362) | feat(desktop): add priority locale translations | Adds complete app/UI dictionaries for 11 languages (Azerbaijani, Finnish, Hindi, etc.) and enables Turkish Desktop translation. |
| [#40363](https://github.com/anomalyco/opencode/pull/40363) | fix(github): include pull request identity in context | Fetches authoritative PR number/URL via GraphQL and injects them into the GitHub Action prompt so agents can operate on the correct PR. |
| [#40359](https://github.com/anomalyco/opencode/pull/40359) | fix(core): execute tools renamed by context hooks | Retains request‑local registration identity when context hooks rename tool definitions, translating renamed calls back to canonical names. |
| [#40327](https://github.com/anomalyco/opencode/pull/40327) | feat(plugin): add session HTTP middleware | Introduces an Effect‑native HTTP middleware seam, exposing `ctx.session.http()` in both Effect and Promise plugin APIs. |
| [#40356](https://github.com/anomalyco/opencode/pull/40356) | fix(app): move markdown parsing to worker | Upgrades Marked to 18.0.7 and runs Markdown projection, KaTeX rendering, and Shiki highlighting in the session worker for better performance. |
| [#40358](https://github.com/anomalyco/opencode/pull/40358) | fix(opencode): default xAI OAuth to device flow | Switches xAI SuperGrok login to device‑code authorization, retaining loopback OAuth as a labeled fallback. |
| [#40357](https://github.com/anomalyco/opencode/pull/40357) | fix(session): cap free usage retry delay | Caps `FreeUsageLimitError` retry hints at the documented 5‑hour window while preserving provider retry‑after behavior for other errors. |
| [#37054](https://github.com/anomalyco/opencode/pull/37054) | feat(app): add full session option to web fork dialog | Allows forking an entire conversation from the web UI, not just a selected message. |
| [#37097](https://github.com/anomalyco/opencode/pull/37097) | fix(app): show shell output while a command runs | Expands bash‑tool output in the web UI during execution, matching the TUI behavior. |
| [#40125](https://github.com/anomalyco/opencode/pull/40125) | feat(opencode): Allow per‑MCP‑server trust configuration | Closes multiple issues by enabling fine‑grained trust settings for individual MCP servers. |

## 5. Feature Request Trends
- **Model‑provider compatibility** – Users repeatedly request broader model support, clearer error messaging, and more robust handling of provider‑specific quirks (Copilot, xAI, Claude).
- **Session management & persistence** – Demand for better session organization (status tags, resume/attach workflows), reliable session loading, and full‑conversation forking.
- **MCP server configuration** – Need for per‑server trust controls, reliable local stdio MCP support on Windows, and integration with official MCP registries.
- **Plugin ecosystem extensibility** – Interest in middleware hooks, custom tool renaming, and documented plugin development patterns.
- **UI/UX enhancements** – Requests for priority locale translations, TUI mouse‑capture toggles, and terminal mascot/buddy systems.

## 6. Developer Pain Points
- **Model‑configuration errors** – “Requested model not supported” and provider‑specific failures (especially with Copilot and Claude) disrupt workflows.
- **Session‑loading failures** – Recurring “Unexpected server error” and “Failed to load sessions” on startup, often after upgrades or on Windows.
- **CLI argument conflicts** – `--attach` and `--model` do not work together, blocking remote‑sidecar workflows.
- **File‑system & symlink issues** – `@file` mentions cannot resolve files inside symlinked directories; glob searches return false negatives.
- **Platform‑specific quirks** – Windows PowerShell input handling broken, TUI mouse capture conflicts with terminal multiplexers, macOS dollar‑sign rendering glitches.
- **OAuth & subscription friction** – xAI and GitHub Copilot OAuth flows cause login/reporting issues, especially behind proxies or with free‑tier limits.
- **Plugin/extension stability** – Unsupported `skills` entries in config can cause bootstrap failures; post‑install scripts may keep stale native binaries when npm is constrained.

---
*Data source: [github.com/anomalyco/opencode](https://github.com/anomalyco/opencode) (last 24 hours)*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-04

## 1. Today's Highlights

The Pi project is actively hardening its session management layer with Harness v2 and a durable server backend, while a wave of Windows/WSL path-handling fixes lands in parallel. Compaction reliability remains a focal point, with both a double-compact race and a quadratic JSON-streaming bug addressed this cycle.

## 2. Releases

No releases in the last 24 hours.

## 3. Hot Issues

1. **[BUG] Pi login hangs in WSL after GitHub Copilot device auth** [#6187](https://github.com/earendil-works/pi/issues/6187) — 20 comments. The browser-based OAuth completes but the WSL client never detects it, leaving users stuck. High visibility as WSL adoption grows.

2. **[BUG] Compaction using Copilot Enterprise not possible** [#6768](https://github.com/earendil-works/pi/issues/6768) — 17 comments, 18 👍. Enterprise-licensed compaction returns 421 Misdirected Request errors on both OpenAI and Anthropic paths. Strong community signal — many enterprise users affected.

3. **[BUG] WSL absolute Windows paths are mishandled** [#7064](https://github.com/earendil-works/pi/issues/7064) — 11 comments. `read`/`write`/`edit` tools fail and fall back to clunky CLI replacements because path translation is broken across the WSL/Windows boundary.

4. **[BUG] `anthropic-messages` never sends `x-client-request-id`** [#7161](https://github.com/earendil-works/pi/issues/7161) — 9 comments. Breaks session affinity for proxy gateways (e.g., CliProxyAPI) that key routing on that header — Anthropic conversations can't be grouped into sessions.

5. **[BUG] Sometimes Pi doesn't continue after compaction** [#7020](https://github.com/earendil-works/pi/issues/7020) — 9 comments, **CLOSED**. Long-running "coordinator" sessions hit compaction warts where the agent stalls post-compaction. Resolved — good signal that compaction edge cases are being squashed.

6. **[FEATURE] Configurable thinking level/model for compaction** [#7553](https://github.com/earendil-works/pi/issues/7553) — 3 comments. Compaction unconditionally reuses the session's thinking level, making it impossible to give summarization its own budget on reasoning models.

7. **[BUG] Backspace deletes 2 chars in Kitty** [#7130](https://github.com/earendil-works/pi/issues/7130) — 5 comments. Kitty protocol release events aren't filtered, causing double-deletion — a niche but noisy terminal-emulator bug.

8. **[BUG] `truncateToWidth()` leaves dangling OSC 8 hyperlink** [#7399](https://github.com/earendil-works/pi/issues/7399) — 5 comments. Truncation can split an OSC 8 escape sequence mid-tag, leaving broken hyperlinks in the terminal output.

9. **[BUG] `find` returns no results for path patterns on Windows** [#6817](https://github.com/earendil-works/pi/issues/6817) — 4 comments. Patterns containing path separators (e.g., `src/**/*.ts`) fail on Windows — plain glob patterns work fine. Root cause identified in `find.ts`.

10. **[BUG] `spawn(taskkill)` ENOENT on Node.js 24** [#6596](https://github.com/earendil-works/pi/issues/6596) — 4 comments. `killProcessTree()` hardcodes a relative `taskkill` path that doesn't resolve on Node 24 — needs absolute System32 path + error handler.

## 4. Key PR Progress

1. **#7503 — Harness v2 with in-memory storage** [PR #7503](https://github.com/earendil-works/pi/pull/7503). Introduces backend-neutral `SessionStorage`, `SessionRepo`, and `Session` APIs with an `InMemorySessionStorage` backend. Foundation for pluggable session persistence.

2. **#7451 — Bound model catalog refreshes** [PR #7451](https://github.com/earendil-works/pi/pull/7451) · **CLOSED**. Fixes five linked issues (#7027, #7113, #7153, #7418, #7443) around unbounded catalog refresh cascades. Adds cancellation and queuing to prevent infinite loops.

3. **#7339 — OpenAI background mode responses** [PR #7339](https://github.com/earendil-works/pi/pull/7339). Implements `background: true` for the OpenAI responses API, enabling async task execution. Still a DRAFT seeking design feedback.

4. **#7571 — Built-in Cortecs provider** [PR #7571](https://github.com/earendil-works/pi/pull/7571) · **CLOSED**. Adds [Cortecs](https://cortecs.ai), a European AI provider/router backed by models.dev, following the pattern of recently added providers.

5. **#7569 — Normalize `find` root results** [PR #7569](https://github.com/earendil-works/pi/pull/7569) · **CLOSED**. Fixes `find` path relativization by using `.relative()` consistently and handling path selectors via Node.js facilities instead of hand-rolled heuristics.

6. **#7568 — Generic sampling parameters in `models.json`** [PR #7568](https://github.com/earendil-works/pi/pull/7568) · **CLOSED**. Adds a generic `sampling_params` field so engine-specific options (e.g., `dry_multiplier`, `repetition_penalty`) can be set without per-engine code.

7. **#7396 — Server session backend** [PR #7396](https://github.com/earendil-works/pi/pull/7396). Adds a durable `@earendil-works/pi-coding-agent/server` backend that persists sessions as JSONL with cross-process locking and crash recovery.

8. **#7562 — Anthropic server-side fallbacks** [PR #7562](https://github.com/earendil-works/pi/pull/7562) · **CLOSED**. Opted-in Anthropic requests now support server-side fallback payloads with beta flagging, preserving fallback transitions for replay.

9. **#7394 / #7561 — Linear JSON streaming output** [PR #7394](https://github.com/earendil-works/pi/pull/7394) · **CLOSED**, [PR #7561](https://github.com/earendil-works/pi/pull/7561) · **CLOSED**. Fixes the quadratic output bug in `--mode json` by emitting delta-only `message_update` records and applying stdout backpressure.

10. **#7540 — Resume after context-limited length stops** [PR #7540](https://github.com/earendil-works/pi/pull/7540) · **CLOSED**. Treats length stops as context overflow when usage is within 1% of the window, includes cache-write tokens in the calculation, and retries post-compaction.

## 5. Feature Request Trends

- **Provider expansion** — New built-in providers (Cortecs) and deeper support for existing ones (Anthropic fallbacks, OpenAI background mode) show demand for a growing provider ecosystem.
- **Compaction configurability** — Users want per-compaction thinking levels (#7553), reliable post-compaction continuation (#7020), and immunity to double-compact races (#7253 / #7370).
- **Windows/WSL parity** — A cluster of path-handling and process-management bugs (#7064, #6817, #6596, #6104) signals that Windows support is a top-priority hardening area.
- **Protocol-level fixes** — Headers like `x-client-request-id` (#7161) and JSON wire-format efficiency (#7395/#7394/#7561) are being refined for gateway and streaming compatibility.
- **Terminal emulator fidelity** — Issues in Kitty (#7130), iTerm2 inline images (#7465), and OSC 8 truncation (#7399) reflect ongoing investment in TUI polish across modern terminals.

## 6. Developer Pain Points

- **Compaction fragility** — The most recurrent frustration: double-triggering (#7253), post-compaction stalls (#7020), and enterprise 421 errors (#6768). Multiple fixes shipped this cycle, but users are clearly feeling the pain of long-session reliability.
- **Windows path translation** — A cascade of related bugs (#7064, #6817, #6104) shows that cross-platform path handling is still a weak spot, especially for `find` and tool I/O in WSL environments.
- **Node.js 24 compatibility** — The `taskkill` ENOENT bug (#6596) is a preview of broader Node 24 breakage; dependency and spawn-path hardening will likely be needed.
- **Streaming output bloat** — The quadratic JSON serialization bug (#7395) caused severe stdout drains on long responses, impacting both CLI and programmatic consumers.
- **Terminal rendering crashes** — Lines exceeding terminal width (#7528, #911) and dangling hyperlinks (#7399) cause hard crashes or visual corruption, degrading the TUI experience in constrained environments (Termux, SSH, tmux).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-04

## 1. Today's Highlights

Qwen Code v0.21.5 shipped today, introducing an opt-in migration bridge for macOS Electron users moving to the new Tauri shell, alongside execution-specific tool-call outcome tracking. The Web Shell also reached release-ready status with native lifecycle management, single-instance behavior, and auto-updates. The community is actively engaging with trust-boundary hardening, deterministic execution boundaries, and MCP session resilience.

---

## 2. Releases

### v0.21.5 (Latest)
- **Electron → Tauri migration bridge** for macOS users — opt-in one-time update path ([#8392](https://github.com/QwenLM/qwen-code/pull/8392))
- **Execution-specific outcome tracking** for tool calls, improving observability
- Release workflow was previously flaky; this build resolved prior failures ([#8476](https://github.com/QwenLM/qwen-code/issues/8476))

### v0.21.4
- **Web Shell** is now a release-ready desktop app with native lifecycle management, single-instance behavior, and automatic updates ([#8132](https://github.com/QwenLM/qwen-code/pull/8132))
- **History pagination** now handles oversized conversation turns gracefully
- [v0.21.4-nightly.20260804.d6f55a1c9](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.4-nightly.20260804.d6f55a1c9) also available for testing

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#8102](https://github.com/QwenLM/qwen-code/issues/8102) | **Deterministic tool-execution boundaries for a trustworthy agent runtime** | Proposes keeping the LLM outside the trust boundary and making the runtime able to deterministically constrain, authorize, observe, and evaluate model actions — a foundational security architecture discussion. | 14 comments; active discussion on trust-model design. |
| [#8316](https://github.com/QwenLM/qwen-code/issues/8316) | **Prompt not restored when canceling (Ctrl+C)** | A UX regression: users lose their typed prompt after canceling, forcing re-typing. High frequency, low complexity. | 7 comments; easy repro, strong frustration signal. |
| [#8382](https://github.com/QwenLM/qwen-code/issues/8382) | **Duplicate provider tool call ID** | Tool calls fail with "Duplicate provider tool call id" and "not recorded" errors — directly impacts session reliability. | 6 comments; recurring failure pattern. |
| [#8493](https://github.com/QwenLM/qwen-code/issues/8493) | **Cancelled file tools can still mutate files** | Security-critical: `write_file` and `edit` can complete filesystem writes even after abort signal fires, due to async preparation continuing past cancellation. | 5 comments; flagged as P2, needs urgent fix. |
| [#8491](https://github.com/QwenLM/qwen-code/issues/8491) | **Signal-terminated shell commands can report success** | A process killed by signal may report exit code 0, misleading the agent into thinking the command succeeded. | 3 comments; correctness issue for automation reliability. |
| [#8492](https://github.com/QwenLM/qwen-code/issues/8492) | **MCP metadata hot reload leaves stale session registrations** | Changing `trust`, `alwaysLoadTools`, or tool filters without transport changes doesn't reapply metadata, causing stale tool registrations. | 3 comments; impacts dynamic MCP configuration. |
| [#8452](https://github.com/QwenLM/qwen-code/issues/8452) | **Size-triggered microcompaction repeatedly invalidates prompt cache** | Microcompaction rewrites cached conversation prefixes on consecutive ToolResult turns, defeating prompt-cache benefits and increasing latency/cost. | 3 comments; performance and cost concern. |
| [#8326](https://github.com/QwenLM/qwen-code/issues/8326) | **Fork agents inherit sibling fork directives — context pollution** | Parallel fork agents receive the parent's last model message containing all sibling `functionCall` parts, causing cross-contamination of fork contexts. | 4 comments, 1 👍; architecture concern for multi-fork workflows. |
| [#8432](https://github.com/QwenLM/qwen-code/issues/8432) | **Bailian Personal Token Plan models out of sync** | Built-in model list for Alibaba ModelStudio Token Plan doesn't match current Bailian console models; image/video generation fails. | 4 comments; config drift issue for enterprise users. |
| [#8356](https://github.com/QwenLM/qwen-code/issues/8356) | **After APIUserAbortError, subsequent turns not written to session transcript** | A session-level bug where aborts corrupt the transcript write path, losing history for later turns in the same session. | 3 comments; data-loss concern for long sessions. |

---

## 4. Key PR Progress

| # | PR | Description |
|---|-----|-------------|
| [#8392](https://github.com/QwenLM/qwen-code/pull/8392) | **feat(desktop): bridge Electron users to Tauri updates** | Opt-in one-time migration path for macOS Electron → Tauri. Critical for reducing dual-app maintenance burden. |
| [#8132](https://github.com/QwenLM/qwen-code/pull/8132) | **Web Shell release-ready desktop app** | Native lifecycle management, single-instance behavior, and auto-updates for the Web Shell. Major milestone. |
| [#8467](https://github.com/QwenLM/qwen-code/pull/8467) | **feat(web-shell): add Git diff sources and branch switching** | Expands Git tooling in Web Shell with Uncommitted/Unstaged/Staged/Committed/Branch comparison sources and searchable commit/branch selectors. |
| [#8507](https://github.com/QwenLM/qwen-code/pull/8507) | **feat(external-context): Add optional Mem0 memory writes** | Opt-in Mem0 integration for the Direct External Context pipeline; registers `context_remember({ content })` when configured. |
| [#7800](https://github.com/QwenLM/qwen-code/pull/7800) | **feat(cli): Add agent view PTY workers** | Stacked PR (2/5) adding the PTY worker host layer for managed Agent View sessions — local terminal hosts with authenticated control and bounded output forwarding. |
| [#8320](https://github.com/QwenLM/qwen-code/pull/8320) | **feat(workflows): add cooperative pause and resume** | Whole-run cooperative pause/resume for Dynamic Workflows — scheduler stops dequeuing, lets in-flight work converge, holds results at a gate until resumed. |
| [#8396](https://github.com/QwenLM/qwen-code/pull/8396) | **fix(hooks): close four trust-boundary holes** | Closes HTTP hook redirect following, URL whitelist bypass, DNS-level SSRF gap, and filesystem access in hook execution. Security-critical hardening. |
| [#8419](https://github.com/QwenLM/qwen-code/pull/8419) | **fix(core): reuse prompt cache for multimodal compression** | Chat compression now attempts cache-sharing for media-bearing histories instead of routing to the summarizer, preserving prompt-cache benefits for image/video contexts. |
| [#8499](https://github.com/QwenLM/qwen-code/pull/8499) | **refactor(core): move review skill incident narratives to DESIGN.md** | Reduces review-orchestrator context bloat by moving ~60-turn-injected incident narratives out of SKILL.md into DESIGN.md (not loaded at runtime). |
| [#8442](https://github.com/QwenLM/qwen-code/pull/8442) | **fix: add onCompromised handlers to proper-lockfile calls** | Adds missing `onCompromised` handlers to four `proper-lockfile` call sites, preventing daemon crashes when locks are lost during operation. |

---

## 5. Feature Request Trends

1. **Trustworthy Agent Runtime** — Issue [#8102](https://github.com/QwenLM/qwen-code/issues/8102) proposes a deterministic, constrained execution boundary that keeps the LLM outside the trust perimeter. This aligns with broader community interest in auditable, safety-guaranteed agent operations.

2. **Multi-Channel Communication** — Issue [#8281](https://github.com/QwenLM/qwen-code/issues/8281) requests an official Email channel (IMAP/SMTP), extending Qwen Code beyond terminal and existing bot integrations (DingTalk, Feishu, WeCom, QQ).

3. **Memory & Context Management** — Issue [#8168](https://github.com/QwenLM/qwen-code/issues/8168) asks for configurable `dreamMaxTurns` for the auto-memory agent; combined with the Mem0 PR [#8507](https://github.com/QwenLM/qwen-code/pull/8507), long-term memory write policies are a clear trend.

4. **Workflow Orchestration** — The cooperative pause/resume PR [#8320](https://github.com/QwenLM/qwen-code/pull/8320) and the PTY worker PR [#7800](https://github.com/QwenLM/qwen-code/pull/7800) indicate growing investment in production-grade workflow control and multi-session management.

5. **Multimodal Support** — Closed Issue [#8183](https://github.com/QwenLM/qwen-code/issues/8183) delivered end-to-end local video understanding (sniff → sha256 → ffprobe → storage → upload → response), and PR [#8419](https://github.com/QwenLM/qwen-code/pull/8419) extends prompt caching to multimodal histories.

---

## 6. Developer Pain Points

- **Session & Abort Reliability** — Multiple issues report abort/cancellation side effects: cancelled file tools still mutating disks [#8493](https://github.com/QwenLM/qwen-code/issues/8493), signal-terminated shells reporting success [#8491](https://github.com/QwenLM/qwen-code/issues/8491), and post-abort turns disappearing from transcripts [#8356](https://github.com/QwenLM/qwen-code/issues/8356). These suggest the abort-propagation path needs systematic hardening.

- **MCP Session Resilience** — Stale registrations after metadata reload [#8492](https://github.com/QwenLM/qwen-code/issues/8492) and SDK-embedded MCP tools failing on resumed sessions [#8433](https://github.com/QwenLM/qwen-code/issues/8433) point to a gap in MCP lifecycle management across session boundaries.

- **Prompt Cache Invalidation** — Microcompaction repeatedly evicting cached prefixes [#8452](https://github.com/QwenLM/qwen-code/issues/8452) undermines a key cost-latency optimization, especially for long conversations.

- **UI/UX Friction** — Flickering output in ConEmu/Cmder on Windows [#8385](https://github.com/QwenLM/qwen-code/issues/8385), moving/dynamic thinking panels hard to read [#8319](https://github.com/QwenLM/qwen-code/issues/8319), and `@` completion tab conflicts in Warp [#8330](https://github.com/QwenLM/qwen-code/issues/8330) are recurring terminal-UX complaints.

- **Fork Context Pollution** — Parallel fork agents receiving sibling function calls [#8326](https://github.com/QwenLM/qwen-code/issues/8326) creates incorrect context, making multi-fork workflows unreliable.

- **Provider Model Drift** — Bailian Token Plan models out of sync with the console [#8432](https://github.com/QwenLM/qwen-code/issues/8432), and custom-model provider update prompts repeating infinitely [#8504](https://github.com/QwenLM/qwen-code/issues/8504), indicate config synchronization gaps.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-04

## 1. Today's Highlights

The v0.9.4 release train (#5135) continues forward with 77 commits ahead of `main`, now unblocked after clippy deny-level lints were cleared (#5231) and fact-drift guards were fixed (#5230). The most visible push this cycle is a wave of Runtime API expansions from the Copilot contributor—goal state, MCP servers, memory, and skills endpoints all landing as part of the managed-client surface. Community attention also remains split between the open Chinese-translation debate for "Constitution" (#4949) and persistent Windows/shell-compatibility concerns.

## 2. Releases

No new stable release published in the last 24 hours. The v0.9.4 integration train (#5135) is the active release candidate, superseding #5044.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#3192](https://github.com/Hmbown/CodeWhale/issues/3192) | List on agentclientprotocol/registry | Makes Zed and other ACP-aware editors discover CodeWhale as an installable provider—directly expands the editor-integration ecosystem. |
| [#3205](https://github.com/Hmbown/CodeWhale/issues/3205) | Fleet model classes & loadout auto | Defines the single unified model/loadout selector across TUI, CLI, exec, subagents, and Fleet workers—a critical architectural decision for v0.9.3. |
| [#1481](https://github.com/Hmbown/CodeWhale/issues/1481) | Support OpenCode Go/Zen provider | Community wants DeepSeek-V4 access through the cheaper OpenCode Go/Zen route; 1 👍 signals demand for cost-aware provider options. |
| [#4959](https://github.com/Hmbown/CodeWhale/issues/4959) | `/stop` command & STOP-word intercept | Agents in YOLO/autonomous mode currently ignore text stops; a dedicated intercept layer would restore user control over runaway workflows. |
| [#4949](https://github.com/Hmbown/CodeWhale/issues/4949) | Chinese translation of "Constitution" | Highlights the tension between literal ("宪法") and contextual ("协作准则") translation; invites native-speaker consensus before the next release. |
| [#4022](https://github.com/Hmbown/CodeWhale/issues/4022) | CLI/TUI parity for subagent controls | Subagent status lives in the TUI sidebar but must remain accessible from CLI and future cloud apps—cross-surface parity is a reliability prerequisite. |
| [#2492](https://github.com/Hmbown/CodeWhale/issues/2492) | No cross-session memory | Users report that restarting the TUI wipes conversation context; a persistent memory feature is frequently requested across multiple reports. |
| [#1917](https://github.com/Hmbown/CodeWhale/issues/1917) | Universal PreToolUse/PostToolUse hooks | Proposes a lifecycle hook layer for cancel/pause/resume across all action types—would give users and extensions fine-grained control over tool execution. |
| [#4978](https://github.com/Hmbown/CodeWhale/issues/4978) | Anthropic API 400 on openmodel provider | Intermittent `'type' must be in ["enabled", "disabled", "auto"]` errors when using OpenModel as an Anthropic-compatible provider—regression or misconfiguration? |
| [#1675](https://github.com/Hmbown/CodeWhale/issues/1675) | Garbled Chinese in agent output | Encoding issue causing mojibake in real-time agent output; persists across multiple terminals and affects Chinese-language users. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5135](https://github.com/Hmbown/CodeWhale/pull/5135) | v0.9.4 release train | OPEN | 77 commits ahead of `main`; core integration branch for the next release. |
| [#5233](https://github.com/Hmbown/CodeWhale/pull/5233) | Surface reasoning on Model Studio routes | OPEN | Classifies `reasoning_content` as a dedicated Thinking stream on Alibaba Model Studio OpenAI-compatible routes. |
| [#5225](https://github.com/Hmbown/CodeWhale/pull/5225) | Expose file/search/git tools over ACP | OPEN | `session/prompt` now executes tool calls instead of streaming text only—enables Zed and other ACP editors to drive real code edits. |
| [#5133](https://github.com/Hmbown/CodeWhale/pull/5133) | Runtime API: goal-loop state | OPEN | Adds `GET /v1/threads/{id}/goal` for reading active goals and driving lifecycle transitions via the HTTP boundary. |
| [#5130](https://github.com/Hmbown/CodeWhale/pull/5130) | Runtime API: MCP server CRUD | OPEN | `POST /v1/apps/mcp/servers` lets managed clients create, update, and remove MCP servers without editing TOML directly. |
| [#5131](https://github.com/Hmbown/CodeWhale/pull/5131) | Runtime API: memory endpoints | OPEN | New `/v1/memory` routes for bounded inspection and lifecycle controls—managed clients can now see active memory scope. |
| [#5129](https://github.com/Hmbown/CodeWhale/pull/5129) | Runtime API: skill lifecycle | OPEN | Full skill CRUD (install, update, uninstall, trust, audit) exposed over HTTP for desktop/web clients. |
| [#5192](https://github.com/Hmbown/CodeWhale/pull/5192) | Pin ratatui to 0.30.0 | OPEN | Fixes a race condition where `ratatui-core` 0.1.1+ issues a blocking CPR query that conflicts with the TUI event loop. |
| [#5095](https://github.com/Hmbown/CodeWhale/pull/5095) | Fix OpenHarmony linker args | OPEN | Re-quotes Windows linker arguments containing spaces so paths like `D:\DevEco Studio\...` parse correctly. |
| [#5229](https://github.com/Hmbown/CodeWhale/pull/5229) | Windows beginner guide (zh-CN) | OPEN | Adds a Chinese-language Windows onboarding doc with real screenshot validation on Windows 10. |

## 5. Feature Request Trends

- **Runtime API completeness** — The v0.9.4 stack is aggressively expanding the HTTP control surface (goals, MCP, memory, skills, verifier receipts), reflecting strong demand for programmatic and managed-client access.
- **Provider diversity & cost** — OpenCode Go/Zen (#1481) and MiniMax CN routes (#4686, merged) show users seeking cheaper or region-specific DeepSeek-V4 access paths.
- **Editor / ACP integration** — Registry listing (#3192) and the ACP tool-execution PR (#5225) both aim to make CodeWhale a first-class agent inside Zed and other ACP-compatible editors.
- **Autonomous workflow controls** — `/stop` intercept (#4959), PreToolUse hooks (#1917), and permission profiles (#3211) all point to a community wanting finer-grained interruption and approval surfaces during YOLO/autonomous runs.
- **Chinese-language UX** — Translation debate (#4949), encoding fixes (#1675),输入法 bugs (#2323), and zh-CN docs (#5229) indicate sustained investment in the Chinese user segment.

## 6. Developer Pain Points

- **Windows shell & path handling** — Recurring linker-quote issues (#5095), default `.exe` launch instead of Windows Terminal (#1854), and AI-generated commands mismatched to PowerShell/cmd (#1754) signal that Windows compatibility is an ongoing friction point.
- **TUI stability under updates** — The ratatui pin (#5192) and dead-code wall (#4785, 464 `#[allow(dead_code)]` attributes hiding drift) reveal that dependency upgrades and accumulated lint suppression are degrading build hygiene.
- **Cross-session state loss** — Memory not persisting across restarts (#2492) is a recurring complaint that degrades long-running workflow usability.
- **Chinese input method interference** — IME composition text leaking into command input (#2323) and garbled output (#1675) both degrade the experience for Chinese-language developers.
- **Intermittent provider errors** — The Anthropic 400 on OpenModel (#4978) with no reproducible pattern suggests a race or schema-mismatch bug that is frustrating users relying on compatible endpoints.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*