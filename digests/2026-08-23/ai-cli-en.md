# AI CLI Tools Community Digest 2026-08-23

> Generated: 2026-08-23 01:46 UTC | Tools covered: 10

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



# Cross-Tool AI CLI Comparison Report — 2026-08-23

## 1. Ecosystem Overview

The AI CLI tool ecosystem is entering a phase of stabilization and feature differentiation, with all major tools shipping iterative improvements rather than breakthrough releases. Memory persistence and cross-session context emerged as the dominant cross-community demand, while reliability issues—particularly around hooks, session state, and platform-specific bugs—continue to erode trust. Two clear tiers are visible: mature, high-velocity projects (Claude Code, Codex, OpenCode) with active community governance, and newer entrants (Kimi Code, DeepSeek TUI) still establishing core reliability.

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | New Releases | Release Activity |
|------|-----------|----------|--------------|------------------|
| **Claude Code** | 10 | 0 | 2 (v2.1.240, v2.1.241) | Patch-focused, reliability |
| **OpenAI Codex** | 10 | 4 | 2 alpha builds | Alpha cadence, regression coverage |
| **Gemini CLI** | 10 | 8 | 1 nightly | Security hardening, UX fixes |
| **GitHub Copilot CLI** | 10 | 0 | None | Stagnant release cycle |
| **Kimi Code CLI** | 3 | 2 | None | Documentation + correctness fixes |
| **OpenCode** | 10 | 6 | None | Pre-2.0 stabilization |
| **Pi** | 7 (partial) | N/A | None | Terminal/Windows hardening |
| **Qwen Code** | 10 | 12 | 2 (v0.22.0 + nightly) | Major release with OOM hardening |
| **DeepSeek TUI** | 3 | 6 | 1 RC (v0.9.11) | Architectural refactoring |
| **Grok Build** | — | — | — | No activity |

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Persistent memory / cross-session context** | Kimi Code (#1283, #1478), OpenCode (#20695), Gemini CLI (#26522), Qwen Code (cross-session messaging #9576) | Users demand retained project knowledge, patterns, and preferences between invocations. Current implementations lose context on restart. |
| **Multi-model / BYOK flexibility** | GitHub Copilot CLI (#3282, #3709), OpenCode (provider fragmentation) | Switch models without session restart; unified provider experience across OpenRouter, Bedrock, local endpoints |
| **Session reliability & recovery** | Claude Code (#51267, #75977), Codex (#37403, #39954), Gemini CLI (#21409), OpenCode (#43277), Qwen Code (#9573) | Hung sessions, stuck states, and failed resume flows are universal pain points |
| **Subagent / multi-agent reliability** | Gemini CLI (#22323, #21409), DeepSeek TUI (#5543), OpenCode (sandboxing #2242) | False success reports, hangs, and broken approval chains undermine agentic workflows |
| **Review-loop convergence** | Qwen Code (#9278, #9526, #9744) | Unique to Qwen; community building telemetry to detect when review rounds compound instead of converging |
| **Hook / tool output reliability** | Claude Code (#77832, #84021), DeepSeek TUI (#5546) | Silent data loss, dropped output, and redacted content breaking UI editing |
| **Platform-specific stability** | All tools | Windows (TUI rendering, orphan processes), macOS (auth, syspolicyd CPU), Linux/Wayland (browser agent failures) |

## 4. Differentiation Analysis

| Dimension | Leaders | Emerging / Niche |
|-----------|---------|------------------|
| **Feature focus** | Claude Code: UX polish, hooks, multi-account · Codex: rate-limit transparency, prompt caching · Qwen Code: review loops, cross-session messaging, channel expansion | Gemini CLI: security hardening, sandboxing · DeepSeek TUI: architectural decomposition, supervised operation · Kimi Code: memory persistence, non-UTF-8 correctness |
| **Target users** | Claude Code: general developers, enterprise (multi-account) · Codex: OpenAI Power users, Pro/Plus subscribers · OpenCode: open-source collectors, multi-provider users | Qwen Code: Chinese enterprise (DingTalk integration) · DeepSeek TUI: price-sensitive users, long-running sessions · Pi: terminal purists, Kitty/vim users |
| **Technical approach** | Claude Code: TUI-first, hooks system · Codex: Rust CLI with Guardian classifiers · Qwen Code: session fabric, UNIX socket messaging | Gemini CLI: AST-aware tools, zero-dependency sandboxing · DeepSeek TUI: crate decomposition, durable approval receipts · OpenCode: memory megathread governance, FFF home protection |
| **Release cadence** | Fast: Qwen (v0.22.0), Codex (alpha.7), Claude (patch releases) | Slow: Copilot (none), Kimi (none), Pi (none) |

## 5. Community Momentum & Maturity

| Maturity Tier | Tools | Indicators |
|---------------|-------|------------|
| **High momentum, high maturity** | Claude Code, OpenAI Codex | 1,171+ upvotes on top issues, active PR pipelines, rapid patch releases, comprehensive issue tracking |
| **High momentum, building maturity** | Gemini CLI, Qwen Code, OpenCode | Active nightly/weekly releases, security PRs landing, feature debates (memory, sandboxing), growing issue velocity |
| **Moderate momentum** | DeepSeek TUI, Pi | Architectural refactoring in progress, niche but engaged communities, fewer open issues but higher signal per issue |
| **Lower momentum** | GitHub Copilot CLI, Kimi Code CLI | No releases in 24h, feature requests stacking without implementation, Copilot CLI has 53 upvotes on BYOK with no progress |

**Most active communities** (by engagement): Claude Code (1,171 👍), OpenCode memory megathread (135 comments, 104 👍), Codex macOS syspolicyd (394 👍), Qwen Code review convergence (design-stage but heavily tracked).

## 6. Trend Signals

| Signal | Evidence | Developer Implication |
|--------|----------|----------------------|
| **Memory persistence is table stakes** | Requested by Kimi Code, OpenCode, Gemini CLI, Qwen Code communities | Tools without cross-session memory will fall behind; expect standardization around file-based or index-based memory layers |
| **Subagent reliability is the new breaking point** | False success reports (Gemini #22323), hangs (Gemini #21409), approval gaps (DeepSeek #5543) | Multi-agent workflows remain experimental; disable subagents as workaround until tooling matures |
| **Review-loop convergence is unsolved** | Qwen Code's entire telemetry stack (#9278, #9526, #9744) addresses one problem: review rounds compound instead of converging | Expect new "convergence advisory" features across tools; operators need exit-rail signals for long-running review cycles |
| **Platform fragmentation is widening** | Windows orphan processes (Copilot #4111), Wayland failures (Gemini #21983), macOS auth loops (Codex #39162), TUI rendering (Claude #19637) | Cross-platform testing gaps are systematic; Windows and Linux users experience disproportionate regression rates |
| **Security hardening is accelerating** | Gemini CLI GHSA patch (#28902), OpenCode sandboxing (#2242), Pi seatbelt (#28935), Qwen Code trust boundaries (#8102) | Security is moving from afterthought to first-class design; expect explicit sandboxing and consent flows as differentiators |
| **Provider fragmentation creates friction** | Cloudflare AI Gateway 404s (OpenCode #44281), Copilot auth failures (OpenCode #34644), Gemini deprecated params (OpenCode #38767), OpenRouter routing gaps (Qwen #9757) | Multi-provider users face inconsistent experiences; tools with robust provider abstraction layers will win enterprise adoption |
| **Hook/output reliability is a trust killer** | Silent data loss (Claude #84021), redacted output breaking UI (DeepSeek #5546), missing tool results on resume (Qwen #9573) | Hook authors and memory plugin developers need guaranteed delivery semantics; silent failures erode adoption |

**Bottom line for developers:** The ecosystem is maturing past the "does it work?" phase into the "does it work reliably at scale?" phase. Memory persistence, subagent reliability, and cross-platform stability are the new triage priorities. Tools shipping frequent patches (Claude, Codex, Qwen) are pulling ahead; those with stagnant release cycles (Copilot, Kimi) risk falling behind on community trust.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-23 | Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

### #1298 — Skill-Creator Evaluation Fix
**[PR #1298](https://github.com/anthropics/skills/pull/1298)** · OPEN · MartinCajiao
Fixes a critical bug where `run_eval.py` (and the description-optimization loop it feeds) always reported **0% recall**, making the skill authoring feedback loop non-functional. Also patches Windows stream reading, trigger detection, and parallel workers. This was the result of 10+ independent reproductions of [Issue #556](https://github.com/anthropics/skills/issues/556).
**Status:** Open — critical fix, high community impact.

### #568 — ServiceNow Platform Skill
**[PR #568](https://github.com/anthropics/skills/pull/568)** · OPEN · Vanka07
Broad ServiceNow platform skill covering ITSM, ITOM, ITAM/SAM, FSM, SPM/PPM, Security Incident Response, Vulnerability Response, and IntegrationHub. Notable for its enterprise-grade scope.
**Status:** Open — awaiting review.

### #1367 — Self-Audit Skill (v1.3.0)
**[PR #1367](https://github.com/anthropics/skills/pull/1367)** · OPEN · YuhaoLin2005
A universal pre-delivery audit skill that first mechanically verifies every claimed output file exists, then runs a four-dimension reasoning quality gate prioritized by damage severity. Model-agnostic.
**Status:** Open — ambitious scope; directly addresses the reasoning quality gate proposal in [Issue #1385](https://github.com/anthropics/skills/issues/1385).

### #723 — Testing-Patterns Skill
**[PR #723](https://github.com/anthropics/skills/pull/723)** · OPEN · 4444J99
Covers the full testing stack: Testing Trophy philosophy, unit testing (AAA pattern, naming, pure functions), React component testing (Testing Library), integration testing, and e2e patterns.
**Status:** Open — fills a clearly underserved category.

### #514 — Document-Typography Skill
**[PR #514](https://github.com/anthropics/skills/pull/514)** · OPEN · PGTBoos
Prevents typographic defects in AI-generated documents: orphan lines, widowed paragraphs, and numbering misalignment. Addresses a pain point affecting every document Claude generates.
**Status:** Open.

### #83 — Skill Quality & Security Analyzer
**[PR #83](https://github.com/anthropics/skills/pull/83)** · OPEN · eovidiu
Meta-skills that evaluate skills across five dimensions: Structure & Documentation (20%), Clarity & Actionability (20%), Reliability (20%), Security (20%), and Performance (20%).
**Status:** Open — foundational infrastructure for skill governance.

### #541 — DOCX Tracked-Change ID Collision Fix
**[PR #541](https://github.com/anthropics/skills/pull/541)** · OPEN · Lubrsy706
Fixes document corruption when the DOCX skill adds tracked changes to documents with pre-existing bookmarks, caused by hardcoded `w:id` values colliding with the shared OOXML ID namespace.
**Status:** Open — targeted bug fix for an existing popular skill.

### #210 — Frontend-Design Skill Clarity Improvement
**[PR #210](https://github.com/anthropics/skills/pull/210)** · OPEN · justinwetch
Revisions to make the frontend-design skill's instructions specific enough to steer Claude behavior within a single conversation without ambiguity.
**Status:** Open.

---

## 2. Community Demand Trends

From the top community Issues, the most-anticipated Skill directions are:

| Demand | Key Issue | Sentiment |
|---|---|---|
| **Org-wide skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) · 16 comments · 8 👍 | Strong — users currently share via Slack/Teams; a built-in shared library is widely requested |
| **Pre-delivery quality gates** | [#1385](https://github.com/anthropics/skills/issues/1385), [#1329](https://github.com/anthropics/skills/issues/1329) | High — compact-memory + reasoning quality pipeline signal demand for agent reliability |
| **Security & trust boundary enforcement** | [#492](https://github.com/anthropics/skills/issues/492) · 43 comments · 2 👍 | Critical — impersonation of official skills under the `anthropic/` namespace is a live vulnerability |
| **Agent governance patterns** | [#412](https://github.com/anthropics/skills/issues/412) · 6 comments | Growing — policy enforcement, threat detection, trust scoring, audit trails |
| **Multi-platform / enterprise coverage** | [#568](https://github.com/anthropics/skills/pull/568) (ServiceNow), [#181](https://github.com/anthropics/skills/pull/181) (SAP) | Niche but high-value — enterprise ERP/CRM skills are underserved |

---

## 3. High-Potential Pending Skills

These PRs are open but address clearly voiced community needs and are close to merging:

- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit skill. Directly implements the reasoning quality gate pipeline the community has been requesting (Issue #1385). Universal scope increases its likelihood of adoption.
- **[PR #723](https://github.com/anthropics/skills/pull/723)** — Testing-patterns skill. Testing is a top-3 workflow area for developers; no comprehensive skill currently exists in the repo.
- **[PR #568](https://github.com/anthropics/skills/pull/568)** — ServiceNow platform skill. Broad enterprise coverage with 8+ modules; could become a flagship plugin.
- **[PR #514](https://github.com/anthropics/skills/pull/514)** — Document-typography skill. Solves a near-universal pain point for AI-generated documents with minimal scope creep.
- **[PR #83](https://github.com/anthropics/skills/pull/83)** — Skill quality & security analyzers. Meta-infrastructure that enables the entire ecosystem to self-verify; high leverage if merged.

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **agent reliability and governance** — not more capabilities, but better verification: pre-delivery quality gates, self-auditing, security analyzers, and org-level trust boundaries, driven home by the live impersonation vulnerability (#492) and the broken evaluation loop (#556/#1298).

---



# Claude Code Community Digest — 2026-08-23

## 1. Today's Highlights

Anthropic shipped two patch releases (v2.1.240 and v2.1.241) with bug fixes and reliability improvements. Community attention remains overwhelmingly focused on the removal of `/buddy` (Issue #45596 — 1,171 👍, 268 comments) and multi-account management (Issue #18435 — 748 👍), while multiple Windows and hooks-related bugs continue to circulate without resolution.

## 2. Releases

**v2.1.241 & v2.1.240** — Both releases contain bug fixes and reliability improvements. No new features or breaking changes noted.
- [v2.1.241](https://github.com/anthropics/claude-code/releases)
- [v2.1.240](https://github.com/anthropics/claude-code/releases)

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#45596](https://github.com/anthropics/claude-code/issues/45596) | Bring Back Buddy | 268 | 1171 | The single most-discussed issue in the repo. `/buddy` vanished in v2.1.97 with no changelog notice; the community continues to demand its return as a companion/UX feature. |
| [#18435](https://github.com/anthropics/claude-code/issues/18435) | Multiple Claude accounts | 168 | 748 | No native multi-profile support exists in Desktop or VS Code. High-urgency feature request from users managing personal + work accounts. |
| [#19637](https://github.com/anthropics/claude-code/issues/19637) | Windows cmd rendering issue | 25 | 18 | Text overlapping/garbled display in Command Prompt since v2.1.3. Persistent Windows TUI bug with no fix in sight. |
| [#64630](https://github.com/anthropics/claude-code/issues/64630) | MacOS does not use default browser for login | 18 | 26 | Auth flow bug on macOS — users are forced into non-default browsers, creating friction for those with custom browser setups. |
| [#51267](https://github.com/anthropics/claude-code/issues/51267) | Remote Control mobile session silently hangs | 17 | 17 | No remote unstick mechanism exists; only local `Esc` recovers a hung session, making mobile remote control unreliable. |
| [#62202](https://github.com/anthropics/claude-code/issues/62202) | SIGTERM every 5 min in Desktop/VS Code | 7 | 3 | Child process killed at exactly 300s intervals — exclusive to Desktop and VS Code wrapper; terminal CLI unaffected. Likely a watchdog/timer bug. |
| [#77832](https://github.com/anthropics/claude-code/issues/77832) | PostCompact hook silent-miss on Windows | 6 | 0 | `PostCompact` hook failed to fire 0/3 times across two weeks on Windows 11 / git BASH. Affects memory plugin workflows. |
| [#84021](https://github.com/anthropics/claude-code/issues/84021) | Hook output >10K silently dropped | 5 | 0 | Hooks emitting >10,000 chars of `additionalContext` are silently discarded with no error or warning — memory plugins lose data invisibly. |
| [#85924](https://github.com/anthropics/claude-code/issues/85924) | Queued composer text discarded on mobile | 5 | 2 | Text typed in "Queue feedback…" mode on Android is silently dropped when Claude's turn ends or a new response renders. |
| [#75977](https://github.com/anthropics/claude-code/issues/75977) ✅ | Auto mode circuit breaker cached across sessions | 1 | 0 | **CLOSED** — A transient `tengu_auto_mode_config` verdict was persisted to `~/.claude.json`, poisoning subsequent sessions into Manual mode. Fix shipped. |

## 4. Key PR Progress

*No pull requests were updated in the last 24 hours.*

## 5. Feature Request Trends

- **Companion / UX features**: The `/buddy` removal triggered the largest community response in the repo's history, signaling strong demand for personality-driven or guided UX modes.
- **Multi-account / multi-profile support**: Issue #18435 ranks as the second-most-supported feature request, indicating a clear need for profile switching in Desktop and VS Code.
- **Auto-memory observability**: Issue #82056 requests in-session visibility into whether the memory index loaded fully, partially, or not at all — a transparency gap users want closed.
- **Agent panel UX**: Issue #88907 requests active-first sorting in the agents panel, improving discoverability when orchestrating multiple subagents.
- **Mobile / remote control reliability**: Issues #51267 and #85924 highlight consistent pain points around queued input and session recovery on mobile.

## 6. Developer Pain Points

- **Silent data loss in hooks**: Multiple issues (#77832, #84021) report hooks failing or dropping output without any error signal, making debugging extremely difficult for memory plugin authors.
- **Windows TUI and hooks instability**: Rendering bugs (#19637), PostCompact hook failures (#77832), and prompt cache lookup failures (#87966 — 89 full-context rewrites, ~59M excess tokens) concentrate on Windows, suggesting a platform gap.
- **Desktop / VS Code wrapper bugs**: SIGTERM at 5-minute intervals (#62202) and VS Code Remote-SSH 100% CPU spin (#87739) point to process-lifecycle issues in non-CLI surfaces.
- **Mobile experience gaps**: Silent text discard (#85924) and session hang with no recovery (#51267) degrade the mobile remote control experience.
- **Auth and browser integration**: macOS default-browser login failures (#64630) and MCP approval dialog being ignored in interactive remote sessions (#87548) create friction at critical trust boundaries.
- **Model behavior concerns**: Several model-quality issues (#88416, #77745, #85254, #85253, #85256, #85255) report false-positive refusals, fabricated facts, unauthorized task expansion, and information leakage — suggesting ongoing alignment and reliability challenges.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-23

## 1. Today's Highlights

Two Rust CLI releases landed in the last 24 hours — `0.150.0-alpha.7` and `0.149.0-alpha.7.2` — while macOS users continue to dominate issue volume, with the `syspolicyd`/`trustd` CPU runaway (#25719) now at 394 upvotes and the SQLite log churn regression (#29532) still unresolved. On the code side, the team shipped thread-source attribution improvements across the CLI, TypeScript SDK, and Guardian classifiers, signaling a push toward better integration and observability.

---

## 2. Releases

| Version | Notes |
|---|---|
| **rust-v0.150.0-alpha.7** | Latest alpha build (2026-08-23) |
| **rust-v0.149.0-alpha.7.2** | Patch bump to the 0.149.x alpha stream |

> Links: [rust-v0.150.0-alpha.7](https://github.com/openai/codex/releases/tag/rust-v0.150.0-alpha.7) · [rust-v0.149.0-alpha.7.2](https://github.com/openai/codex/releases/tag/rust-v0.149.0-alpha.7.2)

---

## 3. Hot Issues

### 1. macOS `syspolicyd` / `trustd` CPU & memory runaway — **#25719** ⬆️ 394 👍
A long-running macOS performance issue where Codex Desktop repeatedly triggers system policy daemons, causing unbounded CPU and memory consumption. The volume of upvotes makes this the single most-watched issue in the repo.
[View](https://github.com/openai/codex/issues/25719)

### 2. Persistent SQLite log churn on macOS — **#29532** ⬆️ 46 💬
After the `rust-v0.142.0` upgrade, partial relief was seen for `codex_api::endpoint::responses_websocket`, but `~/.codex/logs_2.sqlite` still grows aggressively. Suggests an incomplete fix in the telemetry path.
[View](https://github.com/openai/codex/issues/29532)

### 3. Opening existing conversations invalidates ChatGPT auth — **#39162** ⬆️ 38 💬
A regression in build 26.814.41407 where reopening a conversation forces a full sign-in redirect, breaking workflows for Pro/Plus users. Reported as a regression from the immediately preceding build, pointing to a fragile auth-session round-trip.
[View](https://github.com/openai/codex/issues/39162)

### 4. Weekly rate limit draining like old 5-hour cap — **#33685** ⬆️ 28 💬
Users report the new weekly token bucket is being consumed at rates comparable to the legacy 5-hour limit, effectively nullifying the promised flexibility upgrade. Relevant to anyone running sustained GPT-5.5 High sessions.
[View](https://github.com/openai/codex/issues/33685)

### 5. Desktop can't resume Remote Control / CLI thread — **#37403** ⬆️ 27 💬
A macOS regression introduced on 2026-08-07 where resuming an active CLI thread from the Desktop client errors with `already has an active writer`. Breaks the mobile-to-desktop handoff workflow that many power users depend on.
[View](https://github.com/openai/codex/issues/37403)

### 6. Bedrock GPT-5.6 Sol lacks explicit cache controls — **#37674** ✅ Closed ⬆️ 12 👍
AWS Bedrock users on the native CLI couldn't opt into GPT-5.6 Sol prompt caching, producing unexpectedly high cache-write spend on agentic workloads. Closed, but highlights a gap in Bedrock feature parity.
[View](https://github.com/openai/codex/issues/37674)

### 7. Weekly reset date shifted after Plus subscription — **#30816** ⬆️ 11 💬
After upgrading to ChatGPT Plus, Windows users noticed their weekly usage counter reset on an unexpected date, disrupting budgeting and expectation management.
[View](https://github.com/openai/codex/issues/30816)

### 8. Windows + Android Remote Control reconnect loop — **#39954** ⬆️ 10 💬
After the stale-server 409 Conflict was resolved, the Windows app-server now connects to the Remote Control websocket but immediately drops into a reconnect loop, rendering the Android→Windows workflow unusable.
[View](https://github.com/openai/codex/issues/39954)

### 9. Pro 5-hour usage bucket disappeared — **#32707** ⬆️ 10 💬
ChatGPT Pro users on Windows no longer see the 5-hour usage row in the Codex App or `account/rateLimits/read`, suggesting a backend schema or migration issue following the weekly-limit rollout.
[View](https://github.com/openai/codex/issues/32707)

### 10. Background exec intermittently deletes `~/.codex/skills/.system` — **#19265** ⬆️ 10 💬
A chronic issue where Codex Desktop's background execution removes the system-skills directory, causing bundled skills (`imagegen`, `openai-skills`, etc.) to vanish from `available-skills` until manually restored.
[View](https://github.com/openai/codex/issues/19265)

---

## 4. Key PR Progress

| PR | Summary | Link |
|---|---|---|
| **#40169** | Regression coverage for patch-approval paging — tests scrolling, resizing, dismissing, reopening, and single-accept/cancel in the full-screen pager. | [PR](https://github.com/openai/codex/pull/40169) |
| **#40166** | TUI cursor ordering fix — moves cursor to the new position *before* showing it, preventing a frame where the cursor flashes at its old location. | [PR](https://github.com/openai/codex/pull/40166) |
| **#40161** | `codex exec --thread-source <SOURCE>` — lets callers classify newly created or forked threads, defaulting to `user` for backward compatibility. | [PR](https://github.com/openai/codex/pull/40161) |
| **#40155** | Exposes `threadSource` in CLI and the TypeScript SDK, enabling integrations to attribute agent work back to the originating feature. | [PR](https://github.com/openai/codex/pull/40155) |
| **#40150** | Guardian classifiers now use `thread_source: guardian_classifier` in turn metadata, removing the older `request_kind` and `is_guardian_mode` fields. | [PR](https://github.com/openai/codex/pull/40150) |
| **#40068** | Reports runtime MCP connection status via a new nullable `runtimeStatus` field on `mcpServerStatus/list`, decoupling live connection state from cached tool inventory. | [PR](https://github.com/openai/codex/pull/40068) |

*(4 additional PRs closed in the window without sufficient comment activity for the top-10 list.)*

---

## 5. Feature Request Trends

- **Better rate-limit transparency and fairness** — Multiple issues (#33685, #30816, #32707) signal that the weekly-limit rollout introduced confusing behavior around bucket draining speed, reset dates, and missing UI rows for Pro users.
- **Prompt caching control for GPT-5.6 Sol** — Bedrock (#37674) and direct-API (#35300) users are hitting the same gap: no explicit `prompt_cache_breakpoint` support, leading to costly cache misses on long agentic runs.
- **Cross-platform Remote Control reliability** — Both macOS (#37403) and Windows+Android (#39954) report resumption and reconnect failures, indicating the Remote Control architecture needs a unifying stability pass.
- **Hook and skill-path portability** — Windows `PreToolUse` hooks not firing (#24453), Claude Code imports rewriting `.claude/` paths to `.Codex/` (#40147), and the system-skill directory disappearing (#19265) all point to a need for more robust, platform-agnostic skill and hook handling.

---

## 6. Developer Pain Points

| Theme | Representative Issues |
|---|---|
| **macOS resource runaways** — `syspolicyd`/`trustd` CPU spikes and persistent SQLite log churn continue to be the #1 source of desktop friction. | [#25719](https://github.com/openai/codex/issues/25719), [#29532](https://github.com/openai/codex/issues/29532), [#40153](https://github.com/openai/codex/issues/40153) |
| **Auth/session fragility** — Repeated sign-in loops and conversation-reopen auth invalidation undermine basic trust in the Desktop client. | [#39162](https://github.com/openai/codex/issues/39162), [#39803](https://github.com/openai/codex/issues/39803) |
| **Windows-specific regressions** — A disproportionate share of recent issues are Windows-only: blank TUI on thread resume (#34724), memory leak to 50 GB+ (#40163), paste duplicating (#26199), sandbox setup failures (#34928). | [#34724](https://github.com/openai/codex/issues/34724), [#40163](https://github.com/openai/codex/issues/40163), [#26199](https://github.com/openai/codex/issues/26199), [#34928](https://github.com/openai/codex/issues/34928) |
| **Rate-limit confusion post-rollover** — The shift from 5-hour to weekly buckets left visible gaps in the UI and unexpected behavior in the billing backend. | [#33685](https://github.com/openai/codex/issues/33685), [#30816](https://github.com/openai/codex/issues/30816), [#32707](https://github.com/openai/codex/issues/32707) |
| **Telemetry/boot coupling** — If any process holds a write lock on `logs_2.sqlite`, the CLI hard-fails at startup with a flat 5-second busy timeout and no retry. | [#35555](https://github.com/openai/codex/issues/35555) |

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-23

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly shipped today with a security hardening patch (GHSA-wpqr-6v78-jr5g) that blocks `$VAR` / `${VAR}` variable-expansion bypasses, alongside fixes for terminal scrollback corruption, A2A server state corruption, and symlinked skill deduplication. The community is actively discussing subagent reliability—particularly auto-recovery after turn limits, generalist-agent hangs, and browser-agent failures on Wayland—while a security-focused PR also tightens extension consent and environment-variable sanitization.

---

## 2. Releases

**v0.56.0-nightly.20260823.g5411f113c** — Automated nightly build. No manual changelog; see the diff [here](https://github.com/google-gemini/gemini-cli/compare/v0.56.0-nightly.20260822.g5411f113c...v0.56.0-nightly.20260823.g5411f113c).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | A subagent that hits its turn limit is misreported as successful, silently hiding failures from the user. | 13 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | The generalist agent freezes indefinitely on simple tasks; disabling sub-agents is the only known workaround. | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage bash affinity via Zero-Dependency OS Sandboxing | Proposes using the model's native bash skills with sandboxed execution—significant UX shift for power users. | 8 comments · 1 👍 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retrying low-signal sessions indefinitely | Sessions the extraction agent skips are never marked processed, causing the inbox to loop on them forever. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction & reduce Auto Memory logging | Secrets may already be in model context before redaction occurs; also reduces noisy skill logging. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck at "Waiting input" after completion | Simple CLI commands hang the UI, leaving the agent in a perpetual "awaiting user input" state. | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | A common Linux desktop environment is untested; browser automation is broken for Wayland users. | 4 comments · 1 👍 |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores settings.json overrides | `maxTurns` and other config values in `settings.json` are silently ignored by the browser subagent. | 3 comments |
| [#22186](https://github.com/google-gemini/gemini-cli/issues/22186) | get-shit-done output hook causes crash | The summary-printing hook crashes the entire CLI when output is near completion. | 3 comments |
| [#20079](https://github.com/google-gemini/gemini-cli/issues/20079) | Symlinked agent files not recognized | `~/.gemini/agents/` symlinks are ignored, blocking users who organize agents across directories. | 4 comments |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#28902](https://github.com/google-gemini/gemini-cli/pull/28902) | Block `$VAR` / `${VAR}` expansion bypass (GHSA-wpqr-6v78-jr5g) | 🔴 Security · Open | Hardens `detectBashSubstitution()` and `detectPowerShellSubstitution()` against a variable-expansion loophole. |
| [#28967](https://github.com/google-gemini/gemini-cli/pull/28967) | Prevent clearing terminal scrollback on static refresh | Open | Fixes `refreshStatic()` calling `clearTerminal` in standard-mode terminals, which wiped scrollback on Linux. |
| [#28940](https://github.com/google-gemini/gemini-cli/pull/28940) | Clear stale cancellation error on new A2A message turns | Open | Resolves the GCA `Execution aborted` crash that occurred on subsequent prompts after a cancelled request. |
| [#28968](https://github.com/google-gemini/gemini-cli/pull/28968) | Dedupe symlinked/junctioned skills directories | Open | Fixes double-scanning of `.gemini` / `.agents` on Windows when a junction links the two. |
| [#27862](https://github.com/google-gemini/gemini-cli/pull/27862) | Preserve executing subagent tool calls in UI | Open | Subagent calls no longer disappear from the display while still running. |
| [#27860](https://github.com/google-gemini/gemini-cli/pull/27860) | Reset slash-command conflict dedupe on reappear | Open | Conflicts that resolve and then recur are now re-notified instead of silently dropped. |
| [#27754](https://github.com/google-gemini/gemini-cli/pull/27754) | Fix missing return after 501 in A2A server | 🔴 Closed | Added the missing `return` after a 501 response, preventing `ERR_HTTP_HEADERS_SENT` crashes. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Prompt for consent on extension env changes | Open | Extensions can no longer inject unauthorized env vars into MCP server processes without user consent. |
| [#28935](https://github.com/google-gemini/gemini-cli/pull/28935) | Isolate Docker/socket access in macOS Seatbelt sandbox | 🔴 Closed | Denies container runtime socket and binary access in sandbox profiles, closing a hypervisor-escape path. |
| [#28961](https://github.com/google-gemini/gemini-cli/pull/28961) | Declare top-level safety checkers in write policy | Open | Aligns `AllowedPathChecker` registration with standard `[[safety_checker]]` TOML arrays so write-policy enforcement works correctly. |

---

## 5. Feature Request Trends

- **AST-aware codebase tools** — Multiple issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746), [#19561](https://github.com/google-gemini/gemini-cli/issues/19561)) call for AST-based file reads and codebase mapping to reduce token waste and improve navigation precision.
- **Persistent, file-based task tracking** — [#18836](https://github.com/google-gemini/gemini-cli/issues/18836) proposes replacing in-context `WriteToDo` with a CRUD-backed file system to eliminate context rot and inter-session memory loss.
- **Zero-dependency OS sandboxing with bash affinity** — [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) pushes for letting the model use native POSIX toolchains inside a sandbox rather than abstracted tool wrappers.
- **Subagent visibility & resilience** — [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) requests automatic browser-session takeover and lock recovery; [#22598](https://github.com/google-gemini/gemini-cli/issues/22598) wants subagent trajectories surfaced via `/chat share`.
- **Auto Memory quality improvements** — Issues [#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523) collectively request deterministic redaction, inbox-patch validation, and low-signal session quarantine.

---

## 6. Developer Pain Points

1. **Subagent unreliability** — The most frequent theme: subagents hang ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409)), report false success after turn-limit failures ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323)), ignore config overrides ([#22267](https://github.com/google-gemini/gemini-cli/issues/22267)), and crash on output hooks ([#22186](https://github.com/google-gemini/gemini-cli/issues/22186)). Users report that disabling subagents entirely is the only reliable workaround.

2. **Shell / terminal state bugs** — Commands that should complete leave the UI stuck in "Waiting input" ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), and terminal-resize interactions cause flicker ([#21924](https://github.com/google-gemini/gemini-cli/issues/21924)). Scrollback is also cleared unexpectedly on refresh ([#28967](https://github.com/google-gemini/gemini-cli/pull/28967)).

3. **Security & sandboxing gaps** — Variable-expansion bypasses ([#28902](https://github.com/google-gemini/gemini-cli/pull/28902)), extension env-var injection ([#28863](https://github.com/google-gemini/gemini-cli/pull/28863)), and macOS container-escape paths ([#28935](https://github.com/google-gemini/gemini-cli/pull/28935)) indicate the security surface is expanding faster than hardening patches.

4. **Platform compatibility** — Wayland browser failures ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)), Windows junction/symlink deduplication ([#28968](https://github.com/google-gemini/gemini-cli/pull/28968), [#20079](https://github.com/google-gemini/gemini-cli/issues/20079)), and the 400-error limit at >128 tools ([#24246](https://github.com/google-gemini/gemini-cli/issues/24246)) show cross-platform and scaling gaps.

5. **Auto Memory quality** — The memory system silently retries low-signal sessions, lacks deterministic redaction, and hides invalid patches ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), eroding user trust in the feature.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-23

---

## 1. Today's Highlights

The Copilot CLI community is pushing hard on BYOK (Bring Your Own Key) flexibility, with two highly-upvoted feature requests (#3282, #3709) seeking multi-model switching within a single session. A new Windows-specific regression (#4111) was flagged where long-running sessions survive in-place auto-updates and spin at 100% CPU from the old binary. Three new triage issues were opened today, covering MCP initialization failures, cloud task timeouts, and telemetry configuration gaps.

---

## 2. Releases

No releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#3282](https://github.com/github/copilot-cli/issues/3282) | Add multiple BYOK model capability | BYOK users are currently pinned to a single model per session via `COPILOT_MODEL`. Enabling multiple models would eliminate the painful restart-cycle for model switching. | 26 👍, 9 comments — strong, sustained interest since May. |
| [#3709](https://github.com/github/copilot-cli/issues/3709) | Allow `/model` to switch between models including BYOK/local providers | Extends the multi-model vision to the interactive `/model` picker, so local/BYOK providers appear alongside GitHub-hosted models without termin ating sessions. | 27 👍, 5 comments — closely aligned with #3282; both point to the same gap. |
| [#2306](https://github.com/github/copilot-cli/issues/2306) | Enterprise/organization policy authorization errors | Users report intermittent "not authorized" errors 2–3×/week that self-resolve, suggesting a flaky policy check or session-stale token issue. | 3 👍, 7 comments — lower visibility but higher friction for enterprise deployers. |
| [#4370](https://github.com/github/copilot-cli/issues/4370) | MCP init fails with `server/discover` `-32602` | Copilot CLI v1.0.79-1 sends an unsupported `server/discover` RPC that FastMCP rejects, blocking all MCP tool use for anyone on that stack. | 1 👍, 2 comments — blocking bug for MCP adopters. |
| [#4514](https://github.com/github/copilot-cli/issues/4514) | Unable to restore remote session locally | `/resume` shows the remote session but fails to load it locally, breaking the promised cross-machine session continuity. | 1 👍, 1 comment — reported Aug 17, still open. |
| [#4111](https://github.com/github/copilot-cli/issues/4111) | Windows: auto-update leaves orphan processes at 100% CPU | In-place updates rename `copilot.exe` to `.old` but don't terminate sessions using it, causing orphaned processes to persist and consume resources indefinitely. | 0 👍, 1 comment — high-severity regression for Windows users on auto-update. |
| [#4566](https://github.com/github/copilot-cli/issues/4566) | Agent acknowledges work without executing tool actions | On v1.0.80 with `gpt-5.3-codex`, the agent repeatedly acknowledges tasks but never performs the actual tool call — a correctness bug. | New, Aug 22 — no reactions yet. |
| [#4568](https://github.com/github/copilot-cli/issues/4568) | `--cloud` owner picker hangs, reconnect crashes, 429s | Multi-symptom failure: hangs at `Loading available owners...`, cloud tasks stall at `session.requested`, and task polling hits rate-limit 429s. | New, Aug 22 — no reactions yet. |
| [#4567](https://github.com/github/copilot-cli/issues/4567) | Trust insecure OTLP exporter endpoint | Currently, an `http://` OTLP endpoint silently disables telemetry. Users want an explicit opt-in to align with VS Code / Copilot's default OTLP behavior. | New, Aug 22 — no reactions yet. |
| [#4565](https://github.com/github/copilot-cli/issues/4565) | App Configuration Problems in `copilot-runtime-bazel-cache` | Automated scanner flagged configuration issues in a community runtime repo that could cause unexpected deployment behavior. | New, Aug 22 — no reactions yet. |

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **BYOK multi-model switching** is the dominant theme: two open issues (#3282, #3709) together account for 53 upvotes and request the ability to switch among multiple BYOK/local models within a session without restarting.
- **MCP compatibility** is emerging — the `server/discover` failure (#4370) signals that the CLI's MCP handshake assumptions need alignment with popular frameworks like FastMCP.
- **Cross-session continuity** — both the local restore gap (#4514) and the Windows orphan-process bug (#4111) point to a broader trend: session state management across restarts and updates remains fragile.
- **Telemetry configurability** — #4567 reflects a desire for more explicit control over OTLP export behavior, rather than silent fallbacks.

---

## 6. Developer Pain Points

1. **Session model rigidity**: BYOK users are forced to terminate and restart sessions to switch models. The community views this as a significant productivity hit.
2. **Windows auto-update instability**: Orphaned processes from in-place updates are a regression that directly impacts reliability and resource usage on Windows.
3. **MCP framework fragmentation**: The CLI's hardcoded `server/discover` expectation breaks interoperability with FastMCP and likely other lightweight servers.
4. **Intermittent auth flakiness**: Enterprise users experience sporadic policy-check failures (#2306) that are hard to diagnose and reproduce.
5. **Cloud task provisioning timeouts**: Rate-limited polling (429s) and stalled sessions (#4568) suggest the cloud backend path needs backoff and resilience improvements.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-23

## 1. Today's Highlights

Two notable updates landed in the past 24 hours: PR #2614 expands plugin documentation with a dedicated security and persistent-data contract, while PR #2594 (now closed) fixes a data-corruption bug in `StrReplaceFile` where non-UTF-8 bytes were silently mangled. On the issues front, two memory-system enhancements (#1283, #1478) continue to draw community attention, signaling sustained demand for cross-session context support.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Hot Issues

### #1283 — Memory System: Persistent Context Across Sessions [OPEN]
[Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)
One of the most-requested features in the repo, this issue proposes a comprehensive memory layer supporting both AI-managed automatic notes and user-defined instructions. With 40 comments and an active update as recently as 2026-08-22, it remains open and highly engaged. The community views this as essential for long-running, multi-session workflows.

### #1478 — Can the Memory Layer Be Optimized? [OPEN]
[Link](https://github.com/MoonshotAI/kimi-cli/issues/1478)
The author reports that large projects are painful due to an inadequate memory system and a lack of memory-related documentation beyond `agent.md`. They reference OpenClaw's structured memory layout (`SOUL.md`, `USER.md`, `MEMORY.md`, daily memory files) as a possible design model. Three comments and an 2026-08-22 update indicate ongoing discussion.

### #760 — SSL Certificate Verification Fails Behind Corporate Proxy (Zscaler) [CLOSED]
[Link](https://github.com/MoonshotAI/kimi-cli/issues/760)
Users behind corporate proxies (notably Zscaler) are unable to authenticate via `kimi login` due to SSL cert verification errors. The issue is now closed, suggesting a resolution or workaround has been provided. This remains a recurring pain point for enterprise users and is worth noting for anyone onboarding in restricted network environments.

---

## 4. Key PR Progress

### PR #2614 — docs(plugins): Document Security and Persistent Data [OPEN]
[Link](https://github.com/MoonshotAI/kimi-cli/pull/2614)
Author: QIANLING-0831 | Created 2026-08-20 | Updated 2026-08-22
This documentation PR clarifies the plugin contract for `MoonshotAI/kimi-cli`, covering the root `plugin.json`, command-based tools, `inject` behavior, and installation under `~/.kimi/plugins/`. It explicitly scopes out the separate plugin ecosystem. Useful for plugin authors who need to understand security boundaries and persistent-data expectations.

### PR #2594 — fix(tools): Preserve Non-UTF-8 Bytes in StrReplaceFile Edits [CLOSED]
[Link](https://github.com/MoonshotAI/kimi-cli/pull/2594)
Author: 686f6c61 | Created 2026-08-06 | Updated 2026-08-22
A critical correctness fix: `StrReplaceFile` previously decoded entire files with `errors="replace"`, applying edits as strings and re-encoding — which permanently corrupted any invalid UTF-8 sequences outside the edit region into `U+FFFD`. The fix operates on raw byte buffers, applying `old`/`new` as UTF-8 byte substrings. This prevents silent data corruption, especially important for binary-ish or legacy-encoding files.

---

## 5. Feature Request Trends

The dominant theme across open issues is **memory and context persistence**:

- **Cross-session memory** (#1283, #1478) is the single most-requested capability. Users want Kimi Code CLI to retain project knowledge, patterns, and preferences between invocations — a gap that becomes acute in large-codebase workflows.
- **Documentation gaps** are a secondary concern; users report difficulty locating memory-related features in the reference docs, suggesting a need for better discoverability.
- **Enterprise connectivity** remains a recurring theme (#760), with proxy and SSL issues periodically resurfacing.

---

## 6. Developer Pain Points

1. **No persistent memory between sessions** — Multiple users independently report that working on large projects is painful because context is lost between CLI invocations. This is the top frustration.
2. **Sparse or hard-to-find documentation** — Users cannot locate memory-related features in the reference docs, hindering adoption of existing capabilities.
3. **Non-UTF-8 file corruption** — The `StrReplaceFile` bug (now fixed in PR #2594) silently corrupted files containing non-UTF-8 bytes, a severe reliability issue for projects with mixed encodings or binary content.
4. **Corporate proxy / SSL authentication failures** — Users behind Zscaler and similar proxies cannot complete `kimi login`, blocking onboarding in enterprise environments.

---

*Digest generated from GitHub data for MoonshotAI/kimi-cli. All links reference the official repository.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-23

## 1. Today's Highlights

OpenCode is in active stabilization ahead of 2.0, with several bug fixes landing today covering session state persistence, location TTL management, and provider slug translation. The community is sharply focused on memory reliability and sandboxing, while provider integration issues (Cloudflare AI Gateway, GitHub Copilot) continue to generate new reports.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **[Memory Megathread #20695](https://github.com/anomalyco/opencode/issues/20695)** — 135 comments · 104 👍
   Central hub for all memory-related reports; actively requesting heap snapshots. This is the community's top-priority stability issue.

2. **[Sandbox the agent #2242](https://github.com/anomalyco/opencode/issues/2242)** — 83 comments · 71 👍
   Requests directory-scoped terminal restrictions (similar to Gemini CLI's seatbelt). Strong community demand for safe agent execution.

3. **[Hot-reload agents, skills & commands #8751](https://github.com/anomalyco/opencode/issues/8751)** — 21 comments · 95 👍
   Config hot-reload without restarting OC. High engagement signals developer frustration with the current reload workflow.

4. **[TUI search in session buffer #4714](https://github.com/anomalyco/opencode/issues/4714)** — 33 comments · 45 👍
   "Find" functionality inside agent output. A long-standing UX gap for developers working with long conversations.

5. **[Winget installation #5121](https://github.com/anomalyco/opencode/issues/5121)** — 19 comments · 28 👍 *(CLOSED)*
   Windows package-manager installation and version parity concerns. Closed, but highlights the Windows ecosystem gap.

6. **[Auto session title fails for opencode providers #30662](https://github.com/anomalyco/opencode/issues/30662)** — 15 comments
   Silent title-generation failure when using `opencode` provider models (e.g. `big-pickle`). Root cause: missing provider config in smallOptions.

7. **[Lazy-load MCP tool definitions #35376](https://github.com/anomalyco/opencode/issues/35376)** — 8 comments *(CLOSED)*
   All MCP tool definitions were injected into every system prompt, causing severe token overhead with multiple servers. Closed — likely addressed.

8. **[Gemini deprecated sampling params #38767](https://github.com/anomalyco/opencode/issues/38767)** — 6 comments *(CLOSED)*
   OpenCode was sending deprecated `temperature`/`top_p`/`top_k` for Gemini Flash models through OpenRouter. Closed — fix merged.

9. **[Sessions permanently stuck #43277](https://github.com/anomalyco/opencode/issues/43277)** — 4 comments
   Sessions freeze mid-use and persist across reboots. A critical reliability bug for production workflows.

10. **[GitHub Copilot provider not found #34644](https://github.com/anomalyco/opencode/issues/34644)** — 3 comments · 17 👍
    Copilot Student (auto-only) plan authentication succeeds but the provider never registers. Blocks a segment of the user base.

## 4. Key PR Progress

1. **[PR #44282](https://github.com/anomalyco/opencode/pull/44282)** *(CLOSED)* — `fix(core): skip models.dev refresh when catalog unchanged`
   Prevents unnecessary KV writes and event flooding every 5 minutes by comparing catalog hashes before refreshing.

2. **[PR #44275](https://github.com/anomalyco/opencode/pull/44275)** *(CLOSED)* — `fix(core): expire locations from session activity`
   Introduces a `LocationActivity` service with idle deadlines to evict stale location cache entries, fixing a memory leak vector.

3. **[PR #44277](https://github.com/anomalyco/opencode/pull/44277)** *(CLOSED)* — `fix(tui): preserve rollback-compatible tab state`
   Retains the retired `unread` key as an empty object in persisted tab state so older beta clients can still read it.

4. **[PR #44279](https://github.com/anomalyco/opencode/pull/44279)** *(OPEN)* — `fix(core): extend FFF home protection to descendant locations`
   Determines FFF eligibility from the nearest worktree root instead of the selected directory, preventing accidental indexing of home directories.

5. **[PR #44281](https://github.com/anomalyco/opencode/pull/44281)** *(OPEN)* — `fix(provider): send Anthropic's dashed native slug through AI Gateway`
   Fixes Cloudflare AI Gateway returning 404 for all Anthropic models by translating dotted IDs (e.g. `claude-haiku-4.5`) to Anthropic's dashed slugs.

6. **[PR #40018](https://github.com/anomalyco/opencode/pull/40018)** *(OPEN)* — `feat(provider): inject session_id for OpenRouter`
   Enables OpenRouter session-level grouping, improving token attribution and conversation tracking in billing.

7. **[PR #44264](https://github.com/anomalyco/opencode/pull/44264)** *(OPEN)* — `feat(session): add suffix compaction`
   Adds experimental `compaction.mode: "suffix"` as an alternative to the default prepend strategy, giving users more control over context window management.

8. **[PR #44106](https://github.com/anomalyco/opencode/pull/44106)** *(OPEN)* — `fix(ui): preserve clipped text ink`
   Fixes Inter font descender ink being cut off by truncation boxes by expanding clip paint space with padding and negative margins.

9. **[PR #40226](https://github.com/anomalyco/opencode/pull/40226)** *(OPEN)* — `fix(session-ui): bound prompt editor DOM growth on multi-line input`
   Addresses severe performance degradation in the v2 prompt composer where every keystroke re-walked the entire contenteditable DOM.

10. **[PR #44274](https://github.com/anomalyco/opencode/pull/44274)** *(CLOSED)* — `feat(www): rebuild site with Astro`
    Replaces the Blume-based website with a self-owned Astro site including Pagefind search, link validation, and native client navigation.

## 5. Feature Request Trends

- **Hot-reload & live config:** Issue #8751 (95 👍) shows strong demand for in-session config reloading without restarts.
- **Session UX controls:** Fork buttons on responses (#36960), TUI search (#4714), and tab shortcuts (#37077) reflect a desire for better navigation and exploration within conversations.
- **Sandboxing & safety:** The sandbox request (#2242) and FFF home-protection PR (#44279) both point to growing demand for constrained, safe agent execution environments.
- **Multi-provider parity:** Repeated issues around provider-specific bugs (Cloudflare AI Gateway #44281, Copilot #34644, Gemini params #38767) indicate developers want more consistent cross-provider behavior.
- **Context management:** Suffix compaction (#44264) and lazy MCP loading (#35376) show the community is actively pushing for smarter context/token optimization.

## 6. Developer Pain Points

- **Memory & performance:** The memory megathread (#20695) with 135 comments is the single most-engaged issue. Location TTL leaks and DOM re-walks in the prompt editor are concrete symptoms.
- **Session instability:** Stuck sessions (#43277) that survive reboots, and loops that silently exit on interrupted tool calls (#44254), create trust issues in production use.
- **Provider fragmentation:** Anthropic model 404s (#44280), Copilot not registering (#34644), and Gemini deprecated params (#38767) all reflect inconsistent provider integration quality.
- **Windows & Desktop UX:** Paste not working in TUI question input (#44098), hardware acceleration issues (#44071), and flickering usage indicators (#44257) suggest the desktop experience needs more polish.
- **Unknown errors:** Generic "unknown error" toasts (#44285) and unhelpful error messages (#44283) make debugging difficult for end users.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-23

## 1. Today's Highlights
Today’s activity is dominated by Windows and terminal compatibility hardening, alongside targeted fixes for agentic context compaction and provider reliability. The community drove significant progress on ConPTY rendering drift, Kitty/legacy backspace handling, and auto-compaction edge cases, while new provider and model catalog expansions (MindsHub, DeepSeek vision) moved forward.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
1. **#7547** [OPEN] Windows usage & sink-thread discussion — 39 comments, 2 👍  
   `https://github.com/earendil-works/pi/issues/7547`  
   The most active thread of the period; Windows developers are consolidating pain points around the many ways Pi can be run on the platform. Community reaction is high because unresolved friction is blocking broader Windows adoption.

2. **#6879** [OPEN] Auto-compaction never triggers after context exceeds 100% — 20 comments, 18 👍  
   `https://github.com/earendil-works/pi/issues/6879`  
   Critical for long-running agentic sessions. Compaction only fires when the provider rejects an oversized request, causing wasted tokens and broken context. Strong community support indicates this is a high-priority reliability gap.

3. **#7130** [OPEN] Backspace deletes 2 chars in Kitty — 11 comments, 1 👍  
   `https://github.com/earendil-works/pi/issues/7130`  
   Kitty’s protocol release events are leaking into the editor, causing double-deletion. Impacts terminal ergonomics for power users and requires a clean input-filter fix.

4. **#8468** [CLOSED] GitHub Copilot fails with timeout — 5 comments  
   `https://github.com/earendil-works/pi/issues/8468`  
   Authentication/login flows to GitHub Copilot are aborting due to timeout, likely tied to recent transport or proxy changes. Closed as a transient/environmental issue.

5. **#8376** [CLOSED] Make interactive model selection persistence configurable by scope — 5 comments  
   `https://github.com/earendil-works/pi/issues/8376`  
   Requests per-session vs. per-directory model selection scope. Closed after community validation; likely slated for a config expansion.

6. **#7885** [CLOSED] npm search not indexing newly published pi-packages — 5 comments  
   `https://github.com/earendil-works/pi/issues/7885`  
   New `pi-package` registry entries aren’t surfacing in `npm search`, breaking the pi.dev/packages gallery. Closed as an npm indexing latency issue.

7. **#8442**

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-23

---

## 1. Today's Highlights

Qwen Code **v0.22.0** shipped with a major Web Shell OOM hardening pass (transcript retention bounding + oversized replay trimming), while the community deepens its investment in **review-loop convergence telemetry** — a series of PRs and design issues tracking how review rounds compound, stall, and can be detected. Three new channels (DingTalk, WebShell transcript in VS Code companion) and a cross-session message passing feature signal the platform maturing beyond single-session workflows.

---

## 2. Releases

| Version | Type | Key Note |
|---------|------|----------|
| [v0.22.0](https://github.com/QwenLM/qwen-code/releases/tag/v0.22.0) | Stable | Web Shell OOM prevention; review convergence design surface |
| [v0.22.0-nightly.20260823.1007bcacfc](https://github.com/QwenLM/qwen-code/releases/tag/v0.22.0-nightly.20260823.1007bcacfc) | Nightly | Session workspace cwd fix for web-shell overview panel ([#9730](https://github.com/QwenLM/qwen-code/pull/9730)) |

---

## 3. Hot Issues

1. **[ #8102 ] Deterministic tool-execution boundaries for a trustworthy agent runtime** (17 comments, P3)
   chiga0 proposes keeping the language model *outside* the trust boundary and making the runtime deterministically constrain, authorize, observe, and evaluate model-produced actions. The community is engaged but no implementation path is locked — it's a design-stage call for a foundational security posture.

2. **[ #9278 ] /review publish-time convergence advisory — telemetry, diagnosis, and operator-owned posting surfaces** (9 comments, P2, in-progress)
   wenshao documents the runaway review loop: push → review finding → agent fix → larger diff → more findings. The only damper is prose in `AGENTS.md` ("stop after ~5 rounds"), which lives in the fixer's LLM context at the worst possible moment. This issue tracks the design of a convergence-exit advisory and telemetry surface.

3. **[ #9556 ] Should the pipeline keep granting code execution as the invoking user?** (8 comments, security + CI/CD)
   Every unresolved finding in the #9221 review cascade shares one precondition: **code already executing as the review's own user inside the review's worktrees**. The issue argues this capability was granted many steps before #9221 and cannot be removed by it — a pointed discussion about blast-radius containment in review automation.

4. **[ #9002 ] SDK Python rejects `permission_mode="auto"`** (6 comments, P3, CLOSED)
   CLI accepted the value but the Python SDK's client-side validator rejected it before it reached the server. Quick fix; highlights a CLI/SDK parity gap that recurs.

5. **[ #9198 ] qwen 跑出来 oom 问题** (5 comments, P2)
   Session ran for a week+ without exiting on a 1 TB memory server; tmux keys scrambled, mouse produced garbled output. Confirmed Qwen-specific (Kimi Code worked). Points to a transcript-replay or session-lifecycle memory leak that the new v0.22.0 Web Shell hardening now addresses.

6. **[ #9706 ] Auto session title echoes `TITLE_SYSTEM_PROMPT` verbatim** (4 comments, P2, CLOSED)
   Generated titles like "Fix login button on mobile" appeared across unrelated sessions using `qwen3-coder-flash`. Title-generation prompt injection / example-leakage bug.

7. **[ #9573 ] Resumed sessions show "Tool result missing from saved history"** (4 comments, P1, need-retesting)
   Tool calls that completed normally in the original run are re-classified as failed placeholders on resume. A persistence-layer regression affecting observability.

8. **[ #9733 ] Loop detection false-positives on verification cycles kill unattended turns** (4 comments, P2, need-retesting)
   Deterministic `write-script → run → edit → re-run` automation sequences trigger the loop detector, terminating turns irrecoverably without a human message. Directly impacts scripted multi-stage workflows.

9. **[ #2862 ] Startup hangs on "Initializing…" when checkpointing is enabled** (4 comments, needs-triage, CLOSED)
   `settings.json` checkpointing flag causes indefinite hang at launch. Force-quit required; disabling restores normal behavior. Long-standing but resurfaced.

10. **[ #9757 ] Auto Mode classifier stage 1 unavailable with OpenRouter** (3 comments, P2)
    Auto Mode falls back to manual approval with "Classifier stage 1 unavailable" when using OpenRouter. Suggests a model-provider routing gap in the action-classifier pipeline.

---

## 4. Key PR Progress

| PR | Status | Summary |
|----|--------|---------|
| [#9273](https://github.com/QwenLM/qwen-code/pull/9273) | Open | `qwen review capture-tui` — drives a private tmux server, captures pane text to `.ans`, renders `.png` when freeze is available. Verifiers can produce rendering evidence instead of prose arguments. |
| [#9576](https://github.com/QwenLM/qwen-code/pull/9576) | Open | Cross-session messaging — sessions on the same machine bind a UNIX domain socket and accept newline-delimited JSON frames from siblings, feeding messages into the recipient's input queue when policy allows. |
| [#9626](https://github.com/QwenLM/qwen-code/pull/9626) | Open | Repairs persisted session lifecycle — delete/archive/unarchive now work even when the transcript file is empty, torn, malformed, or an orphan whose parent session no longer exists. |
| [#9744](https://github.com/QwenLM/qwen-code/pull/9744) | Open | Review first-time count now recognizes a **fix-induced re-report** as new work, so a carried ID stops answering a question it can no longer answer on its own. Closes a convergence-advisory loophole. |
| [#9581](https://github.com/QwenLM/qwen-code/pull/9581) | Open | Consolidates Goal continuation-prompt rendering into one core function (`renderGoalContinuationPrompt`) instead of independent assembly across TUI, ACP session, and non-interactive CLI. |
| [#9729](https://github.com/QwenLM/qwen-code/pull/9729) | Open | Backfills PR bindings onto legacy sessions — scans the persisted session catalog, resolves each session's PR binding, and refreshes merge state on-demand via a daemon route. |
| [#9760](https://github.com/QwenLM/qwen-code/pull/9760) | Open | Web Shell now recognizes Markdown, HTML, and safe raster images from workspace paths or normalized MIME types before falling back to a generic `document` classification. `charset=utf-8` normalized through both download routes. |
| [#9607](https://github.com/QwenLM/qwen-code/pull/9607) | Open | On OpenAI-compatible endpoints, hybrid-thinking models can now stream a first reasoning phase through `reasoning_content` and then emit a second balanced `<thinking>` block inside `content` — previously the streaming converter failed the turn. |
| [#9602](https://github.com/QwenLM/qwen-code/pull/9602) | Open | Moves tool-display clear from the `finally` block (which ran only after the completion callback fully resolved) to immediately before the callback is invoked, plus a regression test. Fixes a UI-staleness race. |
| [#9394](https://github.com/QwenLM/qwen-code/pull/9394) | Open | Built-in **DingTalk Workspace** channel — uses an existing authenticated DWS CLI profile; supports DMs, @mentions, ambient groups, document-mention notifications, native todo changes, source-scoped sessions, and final replies to the originating context. |
| [#9719](https://github.com/QwenLM/qwen-code/pull/9719) | Open | Adopts the shared WebShell transcript renderer as the **default conversation timeline** in the VS Code companion. Raw ACP session/update notifications bridge through the SDK daemon transcript reducer. |
| [#9526](https://github.com/QwenLM/qwen-code/pull/9526) | Open | Convergence-exit advisory for the review compose step — when carried telemetry proves the loop is stuck on Criticals (Criticals stood in both the previous and current round's work-list while the two-round first-time window is present), the review emits a land-with-residual-risk signal. |

---

## 5. Feature Request Trends

Distilling from the open Issues and PRs, four directions dominate:

1. **Review-loop convergence observability** — A full stack of telemetry, diagnostics, and operator-owned posting surfaces (#9278, #9744, #9526, #9674, #9717). The community is building the instruments to detect when review rounds compound rather than converge.

2. **Cross-session and multi-session communication** — UNIX socket message passing (#9576), session↔PR binding backfill (#9729), and per-channel session rotation (#8927). The model is shifting from isolated sessions toward a session fabric.

3. **Channel expansion** — DingTalk Workspace (#9394), WebShell transcript in VS Code companion (#9719, #9725, #9726, #9727), and Aone Code inline anchoring (#9615, #9627). Integration surface is broadening beyond GitHub/VS Code.

4. **Trustworthy agent runtime foundations** — Deterministic tool-execution boundaries (#8102), code-execution blast-radius debates (#9556), and session-persistence repair (#9626). Security and reliability are moving from afterthoughts to first-class design concerns.

---

## 6. Developer Pain Points

| Symptom | Root Cause (observed) | Status |
|---------|----------------------|--------|
| **OOM on long sessions** — 1 TB RAM, week-long run, tmux keys scrambled | Transcript replay retention unbounded; oversized replays not trimmed | Fixed in v0.22.0 Web Shell hardening |
| **Loop detector false-positives** — kills legitimate `write → run → edit → verify` cycles | Loop detection not distinguishing state-advancing sequences from true cycles | PR #9733 need-retesting |
| **Auto session titles echoing system-prompt examples** | Title-generation prompt leaking its own few-shot examples into output | Fixed (#9706 CLOSED) |
| **Tool results missing on session resume** | Persistence layer reclassifies completed tool calls as failed placeholders | PR #9626 in progress |
| **CLI/SDK parity gaps** — `permission_mode="auto"` accepted by CLI, rejected by Python SDK validator | Client-side validation runs before the value reaches the server | Fixed (#9002 CLOSED) — but signals a recurring pattern |
| **OpenRouter Auto Mode classifier unavailable** | Stage-1 action classifier falls back to manual when using OpenRouter | #9757 open — provider routing gap |
| **Checkpointing startup hang** | `settings.json` checkpointing flag causes indefinite "Initializing…" hang | #2862 — long-standing, resurfaced |
| **Review diffs growing without convergence** | No telemetry signal when review rounds compound; only prose in `AGENTS.md` acts as damper | Active design work (#9278, #9526) |

---

*Digest generated from github.com/QwenLM/qwen-code data as of 2026-08-23. Items are ordered by community engagement (comment count) and impact on core workflows.*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-23

## 1. Today's Highlights

CodeWhale v0.9.11 release candidate is being prepared on `main`, with the full TUI utility command group now adopting the FEAT-014/FEAT-015 external command shapes. A new pricing fix addresses Beijing weekend off-peak billing changes for DeepSeek V4, and a supervised-operation stack PR introduces lifecycle event outboxes and per-session control sockets for long-running sessions.

---

## 2. Releases

**v0.9.11 (RC)** — [PR #5542](https://github.com/Hmbown/DeepSeek-TUI/issues/5542) [CLOSED]
The release manager has prepared the v0.9.11 candidate atop `main`, intentionally excluding benchmark lanes. The branch is byte-for-byte identical to the fully gated local build. No changelog summary beyond this staging commit.

---

## 3. Hot Issues

| # | Title | Author | Reaction |
|---|-------|--------|----------|
| #5316 | EPIC-005: CodeWhale TUI Crate Decomposition (Umbrella) | aboimpinto | 12 comments, no 👍 |
| #5546 | [bug] [redacted] output from tools impairs editing | ronohara | Created today, 1 comment |
| #5543 | Persist child tool approvals through durable receipt path | cyq1017 | 0 comments, critical UX gap |

- **#5316** remains the central umbrella tracking the full crate decomposition; 12 comments signal sustained architect-level debate over boundaries.
- **#5546** flags a regressions post-rewrite: redacted tool output in sessions disrupts the new UI's editing flow. High-impact for users of tool-heavy agents.
- **#5543** describes a correctness bug in the durable approval path — child agents bypass the receipt that should persist parent decisions. Core to multi-agent reliability.

---

## 4. Key PR Progress

| # | Title | Author | Status |
|---|-------|--------|--------|
| #5538 | chore(deps): bump jsonschema 0.46.10 → 0.49.9 | dependabot[bot] | OPEN |
| #5542 | release: prepare Codewhale v0.9.11 | Hmbown | CLOSED |
| #5523 | refactor(tui): extract tool call stages from turn loop | bistack | CLOSED |
| #5544 | feat(web): move docs/subagents & docs/mcp onto dictionary spine | Lstarsky0 | OPEN |
| #5545 | fix(pricing): bill whole Beijing weekends off-peak for DeepSeek V4 | xyzs996 | OPEN |
| #5524 | feat(tui): add multi-file read_lints operation | wuisabel-gif | OPEN |
| #5525 | refactor(tui): adopt command shapes in utility group (FEAT-018) | aboimpinto | OPEN |
| #1701 | chore(deps): bump portable-pty to 0.9.0 | mvanhorn | CLOSED |
| #5535 | Supervised operation stack: lifecycle outbox, /relaunch, per-session control socket | M-Maciej | OPEN |

- **#5523** [CLOSED] Extracted `plan_tool_calls`, `execute_planned_tools`, and `process_tool_results` from the turn loop — a major refactoring of the TUI execution control flow while preserving cancellation and state ordering.
- **#5545** [OPEN] Fixes a pricing logic bug: `deepseek_is_peak` was using UTC hour only; the patch aligns billing with DeepSeek's new rule that weekends are off-peak throughout the day (effective 2026-08-23 Beijing time).
- **#5524** [OPEN] Adds `read_lints` to the existing `lsp` tool, supporting multi-file lint queries via the session `LspManager` without spawning a new language-server process.
- **#5525** [OPEN] Continues FEAT-018: the seven TUI utility commands now use the external command shape, registered under `/a` and similar prefixes, without physical file relocation.
- **#5544** [OPEN] Removes remaining `isZh` branches from `docs/subagents` and `docs/mcp` (16 and 18 respectively → zero), achieving full locale dictionary parity with prior PRs in the #5337 series.
- **#5535** [OPEN] Introduces a machine-readable supervision layer: lifecycle event outbox (JSONL + webhook), `/relaunch`, per-session control sockets, and a goal-continuation quiet-period fix. Five commits across a single seam — a significant ops-observability upgrade.
- **#5538** [OPEN] Dependabot rebasing jsonschema; may take time — no immediate action required.
- **#1701** [CLOSED] Bumps portable-pty to 0.9.0, adding loongarch64 support and resolving a transitive `nix` duplicate. Long-standing #1531 request.

---

## 5. Feature Request Trends

1. **Multi-agent durability** — The #5543 issue and #5535 PR both push toward reliable cross-session state: durable approval receipts and lifecycle outboxes are recurring asks.
2. **Tool-call composability** — The FEAT-018/FEAT-014 command-shape work (#5525) signals sustained demand for a cleaner, composable tool invocation model in the TUI.
3. **LSP integration depth** — #5524's `read_lints` multi-file operation extends an already-requested capability (originating from #4070), indicating users want richer language-server feedback inside the TUI.
4. **Locale/localization coverage** — #5544's zero `isZh` branches on new docs pages is part of a broader push (series #5337) to eliminate remaining localization gaps.

---

## 6. Developer Pain Points

- **Redacted output breaking the new UI** (#5546): Post-rewrite, tool output marked as redacted disrupts editing, suggesting the new UI doesn't yet handle sensitive/filtered content gracefully.
- **Durable approval gaps** (#5543): Child agents not using the approval receipt path means interrupted sessions can lose parent decisions — a correctness issue with no known workaround.
- **Pricing misconfiguration** (#5545): Peak/off-peak detection was UTC-only, causing incorrect billing after DeepSeek's policy change. A fix landed today, but the gap highlights a fragile pricing-integration layer.
- **Long-lived supervision observability** (#5535): The very existence of this PR — adding lifecycle outboxes and per-session control sockets — indicates the community has been missing machine-readable session state for extended agent runs.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*