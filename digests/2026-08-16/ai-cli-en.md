# AI CLI Tools Community Digest 2026-08-16

> Generated: 2026-08-16 01:44 UTC | Tools covered: 10

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



# AI CLI Tools Ecosystem — Cross-Tool Comparison Report
**Date: 2026-08-16**

---

## 1. Ecosystem Overview

The AI CLI tool landscape is in a mature-but-turbulent phase: all major vendors are shipping rapid iteration cycles, but stability regressions dominate community sentiment. Windows platform parity, session/memory management, and MCP reliability are the era's universal friction points. The tools are converging on similar architectures (agent loops, sub-agents, compaction) while diverging on provider strategy and deployment models. Security hardening—particularly around MCP handshakes, sandbox escaping, and auth regressions—has moved from aspirational to urgent across the board.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Releases (24h) | Release Type |
|---|---|---|---|---|
| **Claude Code** | 10 | 2 open / 1 closed | None | — |
| **OpenAI Codex** | 10 | 11 (all closed) | 2 | Rust SDK alpha (v0.148.0-alpha.19/.20) |
| **Gemini CLI** | 10 | 10 | 1 | Nightly (v0.56.0-nightly.20260816) |
| **GitHub Copilot CLI** | 10 | 1 open / 1 closed | None | — |
| **Kimi Code CLI** | 4 | 2 (both closed) | None | — |
| **OpenCode** | 10 | 9 | None | — |
| **Pi** | 10 | 5 open / 6 closed | None | — |
| **Qwen Code** | 10 | 10 | 2 | Preview (v0.21.12-preview.5) + nightly |
| **DeepSeek TUI** | 10 | 12 | None | — |

**Key observations:** DeepSeek TUI and Qwen Code show the highest PR velocity. OpenAI Codex and Pi are in active pre-release alpha/preview cycles. Kimi Code has the lowest issue volume, suggesting either a smaller user base or quieter community.

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|---|---|---|
| **Cross-session / persistent memory** | Claude Code, Kimi Code, OpenCode, Pi | Users want agent tools to retain project context, preferences, and decisions across sessions—not just within a single conversation. |
| **Session compaction & lifecycle control** | Pi, OpenCode, DeepSeek TUI, Qwen Code | Compaction triggers are misaligned with actual cost/token budgets; users want proactive, safe-boundary compaction with visibility into failures. |
| **MCP reliability & configurability** | GitHub Copilot CLI, OpenAI Codex, Gemini CLI | Hard-coded timeouts, no-retry policies, and OAuth discovery regressions are breaking enterprise MCP integrations. |
| **Workspace / project scoping** | OpenAI Codex, OpenCode, Claude Code | Per-project chat isolation, containerized ephemeral workspaces, and fork-based subagent environments are in demand. |
| **Token accounting transparency** | Kimi Code, OpenCode, Pi, DeepSeek TUI | Power users are building independent wire-level metering because built-in cost reporting lacks trust. |
| **Non-blocking interaction models** | Claude Code, Pi, OpenCode | Message queue modes, visible TUI scrollbars, and session-budget UI panels reflect demand for finer interaction control. |
| **Local / self-hosted model support** | OpenCode, DeepSeek TUI, Pi, Qwen Code | LAN auto-discovery, custom provider templates, and legacy provider path hardening are widespread requests. |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | Kimi Code | OpenCode | Pi | Qwen Code | DeepSeek TUI |
|---|---|---|---|---|---|---|---|---|---|
| **Core positioning** | Enterprise agent with hook system | General-purpose AI coding agent | Google-integrated agent with eval infrastructure | GitHub-native CI/CD agent | Long-context agentic editor | Open-source agent with Go subscriptions | Multi-provider TUI with extension system | Review-focused agent with PR integration | Privacy-focused TUI with sandboxing |
| **Target user** | Enterprise / CVP organizations | Broad developer base | Google Cloud / Vertex AI users | GitHub Actions workflows | Power users on metered plans | Individual developers (freemium → Go tier) | Multi-provider experimenters | CI/CD reviewers | Chinese-market / self-hosted users |
| **Technical approach** | PreToolUse hooks, CVP compliance | Rust SDK, gRPC listener, Crashpad | Subagent recovery, AST-aware tools | MCP handshake, Actions GITHUB_TOKEN | K3 1M-token context, quota-aware compaction | Incus/Docker workspaces, per-session budgets | Responses API routing, Mermaid migration | Deny-by-default footprint gates, review pipeline | bwrap sandbox, crate decomposition |
| **Release cadence** | Slow (no release) | Fast (dual alpha in 24h) | Nightly | Slow (no release) | Slow | Slow | Moderate (PR-heavy) | Fast (preview + nightly) | Fast (stabilization cycle) |
| **Platform focus** | Windows MSIX parity gap | Windows performance crisis | Cross-platform (Wayland issue) | NixOS breakage | — | Cross-platform (headless TUI leak) | Windows bash safety gap | IME / Chinese input | macOS test failures |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **DeepSeek TUI** — 12 PRs in 24h, active v0.9.8 stabilization, strong community localization involvement. Indicates a rapidly maturing open-source project with engaged contributors.
- **OpenAI Codex** — Dual alpha releases and 11 closed PRs show aggressive engineering velocity, but the volume of Windows performance and resource-leak issues suggests the feature set is outpacing platform stability.
- **Pi** — 11 PRs with a clear focus on compaction correctness and extension lifecycle. The community is pushing hard on agent reliability, signaling a tool moving from prototype to production-grade.

**Steady but community-friction-heavy:**
- **Claude Code** — Lower PR volume but the highest-voted open issue (#27302, 346 👍) and recurring Windows/MSIX regressions suggest a mature product whose enterprise users are impatient with parity gaps.
- **OpenCode** — Strong feature momentum (Incus, Docker, per-session budgets) but persistent trust issues around Go subscription billing and upstream endpoint reliability.
- **Gemini CLI** — Nightly cadence with security-critical SSRF fixes and eval infrastructure investment. The community is vocal about agent hangs and subagent reliability.

**Niche or emerging:**
- **Kimi Code** — Lowest issue volume; community is self-instrumenting because of opaque token accounting. Indicates a power-user base that has outgrown the tool's observability.
- **GitHub Copilot CLI** — Fewer PRs but critical auth regressions (Atlassian MCP OAuth) and platform-specific breakages (NixOS, Windows OOM) suggest growing pains from rapid feature expansion.
- **Qwen Code** — Review-pipeline focused with strong CI hardening. Smaller community but targeted at a specific workflow (PR review).

---

## 6. Trend Signals

1. **Compaction is the era's unresolved problem.** Every tool that implements it (Pi, OpenCode, DeepSeek TUI, Qwen Code, Kimi Code) has community issues around trigger timing, session corruption on restore, and misalignment with cost budgets. This is a category-wide architectural gap awaiting a robust solution.

2. **Windows is the fragility frontier.** Claude Code (MSIX cross-session hangs), OpenAI Codex (system-wide stutter, unbounded Crashpad growth), GitHub Copilot CLI (NixOS breakage, Windows OOM), and Pi (destructive `taskkill`) all report Windows-specific regressions. Cross-platform parity remains unrealized.

3. **MCP is the new integration bottleneck.** GitHub Copilot CLI's 60s hard-coded handshake timeout, Atlassian OAuth regression, and OpenAI Codex's MCP tool handler additions signal that MCP adoption is outpacing protocol maturity. Enterprise integrations are the canary.

4. **Trust is eroding around token accounting.** Kimi Code users are building wire-level ledgers; OpenCode has subscription balance desyncs; Pi is correcting its `tokens.total` to billable-only. The industry needs standardized, auditable cost reporting—or power users will continue to bypass official tooling.

5. **Sandboxing and isolation are table stakes.** DeepSeek TUI's `bwrap` sandbox debates, OpenCode's Incus/Docker workspaces, and Qwen Code's PAT-isolation concerns show that agent tools are increasingly expected to run untrusted code safely. This is a defensive necessity, not a differentiator.

6. **Provider diversity is accelerating.** Pi's xAI routing overhaul, Gemini CLI's SSRF DNS-bypass fix, and OpenCode's LAN auto-discovery reflect a market where multi-provider support is mandatory. Single-provider lock-in is a growing risk.

**Recommendation for developers:** Prioritize tools with active compaction fixes (Pi, DeepSeek TUI) and strong MCP hardening (Gemini CLI, OpenAI Codex). Monitor Windows stability reports closely before enterprise adoption. Demand transparent token accounting from any metered plan.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-16 | Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | PR | Skill | Status | Summary |
|---|-----|-------|--------|---------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator** (fix) | 🟢 Open | Critical bug: `run_eval.py` reports `recall=0%` on every skill description due to a trigger-detection failure. The entire description-optimization loop is optimizing against noise. Includes Windows stream reading, trigger detection, and parallel worker fixes. |
| 2 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | 🟢 Open | Pre-delivery audit skill: mechanical file existence check followed by a four-dimension reasoning quality gate. Universal — works with any project, tech stack, or model. |
| 3 | [#568](https://github.com/anthropics/skills/pull/568) | **servicenow** | 🟢 Open | Comprehensive ServiceNow platform skill covering ITSM, ITOM, ITAM/SAM, FSM, HRSD/CSM, SPM/PPM, Vulnerability Response, Security IR, and IntegrationHub. |
| 4 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer** + **skill-security-analyzer** | 🟢 Open | Two meta-skills evaluating skills across five dimensions: structure & documentation (20%), trigger accuracy, example quality, error handling, and security patterns. |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | 🟢 Open | Full-stack testing skill: testing philosophy (Testing Trophy), unit testing (AAA pattern, naming, pure functions, edge cases), and React component testing with Testing Library. |
| 6 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | 🟢 Open | Typographic quality control for AI-generated documents — catches orphan lines (1–6 words), widow paragraphs, and numbering misalignment. |
| 7 | [#525](https://github.com/anthropics/skills/pull/525) | **pyxel** | 🟢 Open | Retro/pixel-art game development skill via the Pyxel engine MCP server. Covers the full workflow: write → run_and_capture → inspect → iterate. |
| 8 | [#210](https://github.com/anthropics/skills/pull/210) | **frontend-design** | 🟢 Open | Revamped for clarity and actionability — every instruction is testable within a single conversation, with specific behavioral steering and reduced ambiguity. |

---

## 2. Community Demand Trends (from Issues)

**🔴 Security & Trust Boundaries**
Issue [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍) — Community skills distributed under the `anthropic/` namespace impersonate official skills, enabling trust-boundary abuse. This is the most-commented issue and signals urgent demand for a verification/publishing pipeline.

**🟠 Context & Performance Governance**
Issue [#1487](https://github.com/anthropics/skills/issues/1487) — The `claude-api` skill eagerly injects ~156k tokens in a single tool call, exhausting the context window. Users want skills that respect context budgets.

**🟠 Cross-Platform Compatibility**
Issues [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍) and [#1169](https://github.com/anthropics/skills/issues/1169) — The skill-creator evaluation pipeline is broken on all platforms. This is a foundational tooling gap affecting every skill author.

**🟡 Enterprise & Collaboration**
Issue [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) — Strong demand for org-wide skill sharing directly in Claude.ai, eliminating the current manual download/upload workflow.

**🟡 Skill Hygiene**
Issue [#189](https://github.com/anthropics/skills/issues/189) (6 comments, 9 👍) — `document-skills` and `example-skills` plugins install identical content, causing duplicate skills that waste context. Users want deduplication.

**🟢 Domain-Specific Expansion**
Issue [#412](https://github.com/anthropics/skills/issues/412) — Proposal for an **agent-governance** skill covering policy enforcement, threat detection, trust scoring, and audit trails. No existing skill covers AI agent safety patterns.

---

## 3. High-Potential Pending Skills

These active PRs are the most likely to land soon based on scope, community signal, or urgency:

| PR | Skill | Rationale |
|-----|-------|-----------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator fix** | Blocks all skill authors from reliable evaluation; 10+ independent reproductions of the 0% recall bug; critical infrastructure fix. |
| [#1538](https://github.com/anthropics/skills/pull/1538) | **spec compliance fix** | Two skills fail `skills-ref validate`; a 2-line fix to align with the reference spec — high-likelihood merge. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Addresses the top community demand for pre-delivery quality gates; directly related to Issue #1487 context problem. |
| [#568](https://github.com/anthropics/skills/pull/568) | **servicenow** | Broad enterprise platform coverage; 4+ months in review, suggesting thorough evaluation. |
| [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** | Meta-skills that directly address community concerns about quality and security; first-mover in skill evaluation tooling. |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a universal pain point (bad typography in AI docs); narrow scope, high perceived value. |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Fills a clear gap — no existing skill covers testing methodology; high-demand vertical. |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **foundational tooling and trust infrastructure** — specifically, fixing the broken skill-creator evaluation pipeline and establishing namespace verification — rather than additional domain skills, as these bottlenecks affect every author and user in the ecosystem.

---



# Claude Code Community Digest — 2026-08-16

## 1. Today's Highlights

The community's top concern remains multi-account Connector support (#27302), which has amassed 346 👍 over six months. A regression in Windows MSIX 1.28929.0 is causing cross-session inter-messages to stall and hangs after the auto-update path, while a separate bug lets CVP-approved organizations still receive cyber-safeguard blocks in Claude Code. Three PRs landed in the last 24h, including a security-research false-positive fix and a project-scope frontend-design plugin enablement.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#27302](https://github.com/anthropics/claude-code/issues/27302) | Support multiple Connector accounts | Enterprise users on the same connector need per-account routing; 346 👍 signals strong demand. | 🔥 Top-voted open issue |
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved org still gets cyber-safeguard blocks | Verified organizations are incorrectly blocked; undermines CVP trust. | 102 comments, 19 👍 |
| [#50246](https://github.com/anthropics/claude-code/issues/50246) | Message queue mode | Enables non-interruptive follow-up messages while Claude works; 197 👍. | High-engagement enhancement |
| [#86069](https://github.com/anthropics/claude-code/issues/86069) | Windows/MSIX 1.28929.0: cross-session messages never submitted | Regression in inter-session messaging; session never responds. | 24 comments, active repro |
| [#86344](https://github.com/anthropics/claude-code/issues/86344) | Desktop app hangs with no first token after resume/inter-session msg | Spiked after auto-update 1.26832.0 → 1.28929.0; watchdog kills after ~980s. | 2 👍, macOS |
| [#78527](https://github.com/anthropics/claude-code/issues/78527) | PreToolUse hook deny stops entire turn (regression) | v2.1.210+ changed hook deny behavior from tool error to `hook_stopped_continuation`; breaks security-judge hooks. | 5 comments, macOS |
| [#77212](https://github.com/anthropics/claude-code/issues/77212) | PreToolUse `ask` auto-approved under `bypassPermissions` | Permission hook is silently overridden; security controls are ineffective. | macOS, hooks |
| [#87024](https://github.com/anthropics/claude-code/issues/87024) | Cowork bash dies with "not supported on this device" (Windows) | msix_required enforcement broke legacy installs with no upgrade path; regression since ~Aug 5. | Windows, regression |
| [#77898](https://github.com/anthropics/claude-code/issues/77898) | Single stub transcript hides all sessions in a project | A 416-byte malformed file erases 33 sessions from `/resume`; data-loss-adjacent bug. | macOS, has repro |
| [#86986](https://github.com/anthropics/claude-code/issues/86986) | `claude setup-token` tokens rejected with 400 | Long-lived OAuth tokens from setup-token fail on first API call; affects CI and Max-tier accounts. | Auth, reproducible |

---

## 4. Key PR Progress

| # | PR | Status | Summary |
|---|-----|--------|---------|
| [#86870](https://github.com/anthropics/claude-code/pull/86870) | Fix false-positive CVP status changes during authorized security research | OPEN | Adds `is_authorized_lab()` check and expands `cap_diff_for_prompt()` to account for session metadata (CVP status, educational labs) before triggering security hooks. |
| [#84600](https://github.com/anthropics/claude-code/pull/84600) | Enable frontend-design plugin at project scope | CLOSED | Registers the official marketplace and enables the frontend-design skill via `.claude/settings.json` so it loads automatically per-repo. |
| [#82981](https://github.com/anthropics/claude-code/pull/82981) | Claude/automatizar inventario insumos w4n98s | OPEN | Inventory automation script; community contribution. |

---

## 5. Feature Request Trends

- **Multi-account / cross-product continuity:** Multiple requests for account-level config sync (#87027), shared memory between claude.ai and Claude Code (#87028), and multi-Connector account support (#27302) point to a clear demand for unified identity and state across surfaces.
- **Non-blocking interaction models:** The message queue mode (#50246) and visible TUI scrollbar (#62929) reflect a desire for finer-grained control without interrupting active agent work.
- **Hook reliability & predictability:** Several issues (#77212, #78527, #77110) concern PreToolUse hooks not behaving as documented, suggesting users want stable, well-specified permission-control semantics.
- **Windows-first parity:** Three recent Windows regressions (#86069, #87024, #86999) highlight that MSIX deployment and cross-session features need dedicated stability investment.

---

## 6. Developer Pain Points

- **Hook behavior regressions:** v2.1.210+ introduced breaking changes to PreToolUse deny/ask semantics (#78527, #77212, #77110), forcing security-judge and permission-hardeners to rework their setups.
- **Windows MSIX deployment friction:** The `msix_required` enforcement (#87024) and PATH installation issue (#86999) leave legacy Windows users with no upgrade path, while cross-session messaging (#86069) and background task termination (#68625) add to Windows-specific instability.
- **Session-resume / inter-session messaging bugs:** Multiple open issues (#86069, #86344) report that resumed or cross-session turns hang with no first token, pointing to a fragile session-state pipeline in the desktop app.
- **CVP / compliance false positives:** Approved organizations continue to be blocked (#84352), and security-research flags are still triggering incorrectly (#86870), eroding trust in the verification workflow.
- **Data-loss-adjacent bugs:** A single malformed transcript file can hide all sessions in a project (#77898), and memory frontmatter corruption (#76868) destroys existing data on write failure.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-16

## 1. Today's Highlights

The Codex team shipped two Rust SDK alpha releases (`v0.148.0-alpha.19` → `.20`), while the community is overwhelmingly focused on a wave of Windows performance regressions and macOS Computer Use spawn storms introduced in the latest desktop builds. Key engineering work landed around paginated rollout history, health-check endpoints for the gRPC listener, and improved MCP hook integration.

## 2. Releases

- **rust-v0.148.0-alpha.20** — Latest Rust SDK pre-release; follows alpha.19 released within the same 24-hour window.
- **rust-v0.148.0-alpha.19** — Second consecutive alpha, indicating active iteration ahead of a 0.148.0 milestone.

> [GitHub Releases](https://github.com/openai/codex/releases)

## 3. Hot Issues

| # | Title | Engagement | Why It Matters |
|---|-------|-----------|----------------|
| [#20214](https://github.com/openai/codex/issues/20214) | Codex App frequently freezes/stutters on Windows 11 Pro | 104 comments · 85 👍 | The highest-engagement open issue; users with ample resources (32 GB RAM, Ryzen 5) report persistent stutters, signaling a systemic Windows performance regression. |
| [#3550](https://github.com/openai/codex/issues/3550) | Scope Codex chats to VS Code projects/workspaces | 34 comments · 79 👍 | Widely requested organizational feature; global chat history makes multi-project workflows painful. **Closed** — may have been addressed. |
| [#38546](https://github.com/openai/codex/issues/38546) | System-wide mouse stutter on Windows without elevation | 25 comments · 11 👍 | New report (Aug 14) of severe cursor stutter even at idle, directly tied to the desktop app's Windows process behavior. |
| [#28109](https://github.com/openai/codex/issues/28109) | Brief mouse/input freezes after opening Codex with large sessions | 23 comments · 14 👍 | Confirms a pattern: large session directories trigger 1–2 second input freezes on Windows, compounding the #20214 problem. |
| [#38455](https://github.com/openai/codex/issues/38455) | Computer Use worker storm + V8 OOM crash on macOS | 18 comments · 6 👍 | App crashes ~98 s after launch with 316 threads (187 named `computer-use`); indicates a critical resource leak in the merged ChatGPT/Codex desktop. |
| [#25921](https://github.com/openai/codex/issues/25921) | Crashpad pending dumps growing unbounded (+5 GB/day) | 17 comments · 9 👍 | Disk bloat from unmanaged Crashpad temp files; no lifecycle policy for `pending/` directory. |
| [#35746](https://github.com/openai/codex/issues/35746) | Paginated history drops valid rollout records and reuses ordinals | 13 comments · 0 👍 | CLI session integrity bug — pagination logic can corrupt history, affecting recovery and audit trails. |
| [#18629](https://github.com/openai/codex/issues/18629) | Thread poisoning by inline base64 tool images | 12 comments · 2 👍 | Large `input_image` payloads accumulate in session history, causing `Bad Request` on resume and inflated token usage. |
| [#38750](https://github.com/openai/codex/issues/38750) | System-wide stutter while Codex is idle on Windows | 9 comments · 0 👍 | Confirms the regression is not task-dependent — the app itself degrades OS responsiveness at idle on build `26.810.50856`. |
| [#35470](https://github.com/openai/codex/issues/35470) | CLI copied an image file 150,000 times (400 GiB disk) | 5 comments · 0 👍 | Extreme disk bloat from image duplication logic; highlights a lack of deduplication or size limits in session storage. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#38823](https://github.com/openai/codex/pull/38823) | Avoid allocating per character when decorating hyperlinks | ✅ Closed | Stack-buffer optimization eliminating per-char `String` allocations in TUI rendering. |
| [#38822](https://github.com/openai/codex/pull/38822) | Avoid cloning TUI history span content | ✅ Closed | Reduces memory copies when rendering TUI history, complementing #38823. |
| [#38819](https://github.com/openai/codex/pull/38819) | Support metadata staging for reserved thread IDs | ✅ Closed | Enables callers to associate host-owned state with a thread before Core starts it; adds `ThreadManager::reserve_thread_id`. |
| [#38817](https://github.com/openai/codex/pull/38817) | Add raw config overrides to the TypeScript SDK | ✅ Closed | Introduces `CodexOptions.configOverrides` for TOML configs (e.g., literal path keys) that can't be expressed via structured dotted keys. |
| [#38806](https://github.com/openai/codex/pull/38806) | Add a health endpoint to the code-mode gRPC listener | ✅ Closed | Serves `GET /healthz` (200 OK) over HTTP/1.1 & HTTP/2; preserves HTTP/2 requirement for all gRPC methods. |
| [#38800](https://github.com/openai/codex/pull/38800) | Route executor policy audits through log-only telemetry | ✅ Closed | Forwarded network policy decisions now emit to `codex_otel.log_only`, preventing audit telemetry from polluting persistent state logs. |
| [#38795](https://github.com/openai/codex/pull/38795) | Add storage diagnostics to `codex doctor` | ✅ Closed | Reports available space for `CODEX_HOME` and active worktree (warn <5 GiB, fail <1 GiB); on Windows, checks Dev Drive trust status. |
| [#38788](https://github.com/openai/codex/pull/38788) | Show resume and fork status during TUI startup | ✅ Closed | Displays dimmed `Resuming session…` / `Forking session…` status above the composer while session selection resolves. |
| [#38774](https://github.com/openai/codex/pull/38774) | Use paginated history for persistent exec threads | ✅ Closed | Persistent threads now request paginated history; ephemeral threads fall back to legacy. Addresses the rollout pagination concerns raised in #35746. |
| [#38705](https://github.com/openai/codex/pull/38705) | Add MCP tool handler support to the hooks engine | ✅ Closed | Hooks engine now discovers and invokes `mcp_tool` hook handlers, expanding nested placeholders in MCP tool inputs while preserving JSON types. |

## 5. Feature Request Trends

- **Workspace-scoped sessions** — Issue #3550 (79 👍) reflects strong demand for per-project chat isolation, especially in VS Code.
- **Session storage hygiene** — Multiple reports (#25921, #35470, #30779, #34337) call for automatic cleanup, deduplication, and size limits on rollout history, crash dumps, and subagent JSONL files.
- **Remote / cloud session management** — 404 errors on `/backend-api/codex/responses/compact` (#38323, #38706) and remote MCP elicitation failures (#38707) indicate users need more reliable remote session APIs.
- **Transparent startup feedback** — PR #38788 (resume/fork status) shows demand for clearer TUI state indicators during session loading.
- **Config flexibility in SDK** — PR #38817 addresses the need to pass raw TOML overrides (e.g., literal path keys in permission maps) through the TypeScript SDK.

## 6. Developer Pain Points

1. **Windows system-wide performance degradation** — The dominant complaint. Multiple independent reports (#20214, #38546, #28109, #38750, #38719, #38518) describe cursor stutter, input freezes, and disk read loops caused by the Codex desktop app even at idle. This is the highest-impact issue for the Windows developer experience.

2. **Unbounded disk growth** — Crashpad dumps (#25921), duplicated image files (#35470), and persistent subagent JSONL histories (#30779, #34337) collectively turn sessions into multi-gigabyte liabilities with no built-in cleanup.

3. **Computer Use resource leaks on macOS** — Issues #38455 and #38760 describe uncontrolled spawning of `SkyComputerUseService` processes (5–8/sec at launch), leading to OOM crashes and even kernel panics via `launchservicesd` exhaustion.

4. **Session history corruption** — Paginated history bugs (#35746) and inline base64 thread poisoning (#18629) cause lost rollout records and `Bad Request` / `404 Not Found` errors on resume, breaking long-running workflows.

5. **Remote connectivity instabilities** — Repeated 404s on compact/resume endpoints (#38323, #38706) and MCP elicitation failures over remote HTTP (#38707) suggest the remote session protocol needs hardening.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-16

## 1. Today's Highlights
A nightly build (`v0.56.0-nightly.20260816`) was released, accompanied by critical security fixes for SSRF in `web-fetch` and an upgrade of the sandbox runtime to Node 22. Community attention remains focused on agent reliability, with top issues highlighting subagent termination bugs and generalist agent hangs.

## 2. Releases
**v0.56.0-nightly.20260816.g2a87e7be1**  
Automated nightly build for the upcoming v0.56.0 series.  
[Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.56.0-nightly.20260815.g2a87e7be1...v0.56.0-nightly.20260816.g2a87e7be1)

## 3. Hot Issues
1. **#22323** – Subagent recovery after MAX_TURNS is reported as GOAL success, hiding interruption  
   *Why it matters:* Critical bug where `codebase_investigator` masks turn-limit failures as successful completion, misleading users.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/22323)

2. **#21409** – Generalist agent hangs  
   *Why it matters:* P1 issue causing the generalist agent to hang indefinitely on simple tasks (e.g., folder creation), severely impacting workflow.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/21409)

3. **#24353** – Robust component level evaluations  
   *Why it matters:* Epic tracking behavioral eval infrastructure for the 76+ eval tests currently run across supported Gemini models.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/24353)

4. **#22745** – Assess the impact of AST-aware file reads, search, and mapping  
   *Why it matters:* Proposal to use AST-aware tools for more precise codebase analysis, reducing turn overhead and token noise.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/22745)

5. **#21968** – Gemini does not use skills and sub-agents enough  
   *Why it matters:* Users report that custom skills and sub-agents are ignored unless explicitly prompted, limiting automation potential.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/21968)

6. **#26522** – Stop Auto Memory from retrying low-signal sessions indefinitely  
   *Why it matters:* Auto Memory may loop over unprocessed low-signal sessions, wasting resources and cluttering the inbox.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/26522)

7. **#11802** – Add OTLP headers for telemetry  
   *Why it matters:* Enables authentication headers for OTEL Collector, essential for enterprise telemetry pipelines.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/11802)

8. **#26525** – Add deterministic redaction and reduce Auto Memory logging  
   *Why it matters:* Addresses security concerns by ensuring secrets are redacted before entering model context and reducing excessive logging.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/26525)

9. **#25166** – Shell command execution gets stuck with "Waiting input" after command completes  
   *Why it matters:* Simple CLI commands cause the terminal to hang in an "Awaiting user input" state, blocking further actions.  
   [Link](https://github.com/google-gemini/gemini-cli/issues/25166)

10. **#21983** – Browser subagent fails in Wayland  
    *Why it matters:* P1 bug causing the browser agent to terminate with GOAL status on Wayland systems, breaking cross-platform usability.  
    [Link](https://github.com/google-gemini/gemini-cli/issues/21983)

## 4. Key PR Progress
1. **#28828** – `fix(core): warn when a preview model is silently substituted`  
   Addresses silent fallback to `auto-gemini-2.5` when preview-model entitlement is missing, now emitting a warning.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28828)

2. **#28827** – `fix(core): avoid false authentication errors for 401 substrings`  
   Prevents unrelated strings containing "401" from being misidentified as authentication failures.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28827)

3. **#28823** – `Feat/evals tracker relationships error recovery`  
   Adds behavioral evals for task-graph dependency handling, visualization, file-path 404 recovery, and shell-command failure recovery.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28823)

4. **#28824** – `feat(evals): add multi-tool chain, context safety, and security bounds`  
   Introduces evals for multi-tool chaining, safe large-file handling, and security boundary enforcement.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28824)

5. **#28822** – `Feat/evals todos tasks tracker`  
   Adds evals for task planning (`write_todos`), completion signaling (`complete_task`), and tracker status queries.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28822)

6. **#28679** – `fix(auth): improve Vertex AI 401 error message when using standard API key`  
   Clarifies error messaging when a standard Gemini API key is incorrectly used for Vertex AI authentication.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28679)

7. **#28725** – `fix(security): prevent SSRF via DNS resolution bypass in web-fetch`  
   Closes a critical SSRF vulnerability (CVSS 8.6) by blocking DNS bypass using private/loopback IPs.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28725)

8. **#28726** – `fix(security): upgrade sandbox Dockerfile to node:22-slim`  
   Migrates sandbox containers from Node 20 (EOL) to Node 22 for ongoing security patches.  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28726)

9. **#28608** – `fix(core): fall back to stable models when a preview model 404s with Gemini API key auth`  
   Handles 404 responses when preview models are unavailable, falling back to stable model aliases. *(Closed)*  
   [Link](https://github.com/google-gemini/gemini-cli/pull/28608)

10. **#28769** – `chore: add .opencode to .gitignore`  
    Ignores the OpenCode IDE configuration directory to keep repositories clean.  
    [Link](https://github.com/google-gemini/gemini-cli/pull/28769)

## 5. Feature Request Trends
- **AST-aware codebase tools:** Investigating precise method‑bound reading, navigation, and mapping to reduce tool‑call overhead and improve context quality (#22745, #22746).
- **Subagent observability & resilience:** Requests for automatic session takeover/lock recovery in browser agents (#22232) and visible subagent trajectories via `/chat share` (#22598).
- **Telemetry & configuration flexibility:** Support for custom OTLP headers in telemetry (#11802) and better handling of preview‑model entitlements (#28608).
- **Agent self‑awareness:** Proposals for the CLI to accurately describe its own mechanics, hotkeys, and CLI flags (#21432).

## 6. Developer Pain Points
- **Agent hangs & reliability:** Generalist agent hangs (#21409) and subagent termination bugs (#22323) disrupt complex workflows.
- **Shell command stalls:** Commands that complete still leave the terminal in a "Waiting input" state (#25166).
- **False authentication errors:** String‑matching on "401" causes false positives (#28203), and preview‑model fallbacks can be silent (#28825).
- **Cross‑platform browser failures:** Browser subagent fails on Wayland (#21983) and ignores `settings.json` overrides (#22267).
- **Security & privacy concerns:** SSRF vulnerability via DNS bypass (#28725) and Auto Memory’s indefinite retry on low‑signal sessions (#26522) raise red‑flag issues.
- **Unintended subagent usage:** Subagents activate even when disabled in configuration (#22093), undermining user control.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-16

## 1. Today's Highlights

The most urgent focus this cycle is a **regression in Atlassian MCP OAuth authentication** (RFC 8414 §3.3) introduced in v1.0.79, with two open issues (#4480, #4490) tracking the broken discovery flow. Meanwhile, the **MCP initialize handshake** remains a critical reliability gap — its hard-coded 60s timeout and zero-retry policy cause npx-launched stdio servers to fail permanently within sessions (#4421).

## 2. Releases

No new releases in the last 24 hours. Current known-affected versions span **1.0.79 → 1.0.80**.

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#3392](https://github.com/github/copilot-cli/issues/3392) | Bash tool breaks on NixOS ≥ 1.0.49 | NixOS users cannot run *any* bash command via Copilot CLI; the process fails at spawn with no workaround beyond downgrading. | 👍 9 · 4 comments |
| [#4480](https://github.com/github/copilot-cli/issues/4480) | Atlassian MCP OAuth fails — regression from 1.0.71 | Enterprise MCP integrations relying on Atlassian's OAuth discovery are silently broken since v1.0.79. **Closed** but likely re-emerging. | 👍 6 · 4 comments |
| [#4421](https://github.com/github/copilot-cli/issues/4421) | MCP initialize handshake: fixed 60s budget, no retry | npx-launched stdio servers timeout ~29% of sessions and are never respawned — a hard reliability wall for async MCP tooling. | 👍 0 · 1 comment |
| [#4346](https://github.com/github/copilot-cli/issues/4346) | MCP registry policy fetch returns 403 for Actions GITHUB_TOKEN | The documented PAT-less Actions setup blocks *all* non-default MCP servers in CI, defeating a key onboarding promise. **Closed** | 👍 3 · 2 comments |
| [#4491](https://github.com/github/copilot-cli/issues/4491) | `/spawn` template contradicts itself, enables cross-session write | The singular-spawn contract is undermined by the expanded prompt, allowing accidental writes into unrelated running sessions — a correctness and safety concern. | 👍 0 · 1 comment |
| [#3565](https://github.com/github/copilot-cli/issues/3565) | Task tool silently downgrades subagent model via multiplier guard | Model overrides in agent frontmatter and explicit `model` flags are both silently ignored when cost multiplier is higher, breaking cost-aware agent design. **Closed** | 👍 1 · 1 comment |
| [#4438](https://github.com/github/copilot-cli/issues/4438) | `disable-model-invocation: true` makes skill unreachable | Skills marked non-invocable become completely inaccessible via `skill()` too — the flag is overbroad and breaks explicit user intent. | 👍 1 · 2 comments |
| [#4499](https://github.com/github/copilot-cli/issues/4499) | v1.0.79 OOM crash in autopilot (V8 heap not full) | Fatal "Committing semi space failed" occurs with only ~607 MB / 4.3 GB heap used, pointing to a host-RAM commit failure rather than a true heap limit — autopilot sessions on Windows are at risk. | 0 👍 |
| [#2934](https://github.com/github/copilot-cli/issues/2934) | Support protobuf OTLP export | OpenTelemetry output is locked to JSON; the standard `OTEL_EXPORTER_OTLP_PROTOCOL` env var is silently ignored, blocking protobuf-heavy observability stacks. **Closed** | 👍 6 · 2 comments |
| [#4502](https://github.com/github/copilot-cli/issues/4502) | No way to un-archive a "Done" session | An accidental session archiving is permanent from the UI — data is preserved but the session is invisibly removed, with no restore path. | 0 👍 |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#4497](https://github.com/github/copilot-cli/pull/4497) | Handle fork PR associations in invalid-label writer | Open | Updates the trusted invalid-label writer to handle fork PR workflow runs when GitHub omits the PR association, falling back to trusted workflow-run metadata. |
| [#4449](https://github.com/github/copilot-cli/pull/4449) | Migrate PR automation away from `pull_request_target` | Closed | Replaces `pull_request_target` with a no-permission `pull_request` signal for prompt handling and an issue-scoped write token for closures, reducing attack surface. |

## 5. Feature Request Trends

- **MCP reliability & configurability**: Users want configurable handshake timeouts, retry/backoff logic, and the ability to raise the initialize budget (#4421).
- **Model & session control parity**: Exposing `contextTier` as a session config option for ACP/non-interactive flows (#4275), and support for GPT-5.6 `reasoning.mode` (#4495).
- **Observability protocol flexibility**: protobuf OTLP export support (#2934) reflects a broader demand for standards-compliant telemetry.
- **Session management UX**: Restore/un-archive capability for accidentally archived sessions (#4502).

## 6. Developer Pain Points

| Theme | Recurring Issues |
|-------|-----------------|
| **Authentication regressions** | Atlassian MCP OAuth broken in 1.0.79+ (#4480, #4490); MCP registry 403 under Actions GITHUB_TOKEN (#4346) |
| **Platform-specific breakage** | Bash tool fails on NixOS (#3392); OOM crash on Windows autopilot despite low heap usage (#4499); Codespaces ships stale v1.0.3 with broken `copilot update` (#4501) |
| **MCP handshake fragility** | Hard-coded 60s timeout, no retry, no respawn — npx-launched servers fail permanently (#4421) |
| **Silent behavior violations** | Subagent model downgrades ignored (#3565); `disable-model-invocation` overreach (#4438); BYOK prompt-cache breakage on autopilot nudge (#4500) |
| **Session & model state staleness** | Newly enabled models invisible until cache reset (#4494); `/restart` conflicts with `-w` worktree sessions (#4493) |

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-16

## 1. Today's Highlights

No new releases were published in the last 24 hours, but developer attention is focused on three fronts: a high-engagement feature request for persistent cross-session memory, a pricing/quota instrumentation dispute from a Vivace-tier subscriber, and a critical bug fix for `StrReplaceFile` that could affect chained editing workflows.

---

## 2. Releases

None in the last 24 hours.

---

## 3. Hot Issues

**#1283 — Feature Request: Memory System (Persistent context across sessions)**
[Issue #1283](https://github.com/MoonshotAI/kimi-cli/issues/1283)
The most discussed open issue in the repository, with 40 comments. Users are requesting both AI-managed automatic memory and manual user-defined instructions via config. This feature would let Kimi retain project patterns, preferences, and useful context between sessions — a capability many developers consider table-stakes for an agentic CLI tool. Community interest is strong, though the issue remains open with no activity updates since August 15.

**#2604 — Effective weekly allowance appears reduced ~3–5× without announcement**
[Issue #2604](https://github.com/MoonshotAI/kimi-cli/issues/2604)
A Vivace-tier subscriber reports a drastic, unannounced reduction in effective weekly token allowance, backed by client-side wire-level JSONL instrumentation. The author distinguishes between fresh input tokens, cache reads, and output tokens in their ledger. With only 2 comments and no official response, this issue signals a trust risk: power users are building their own metering tools because they don't trust the reported numbers.

**#2603 — Quota-aware compaction: context compaction should trigger on token budget, not just near max context**
[Issue #2603](https://github.com/MoonshotAI/kimi-cli/issues/2603)
A sharp architectural observation: with K3's 1M-token context window and a 50K reserved headroom, compaction effectively never fires during real agentic workloads. The user argues compaction should be gated on subscription token budgets rather than raw context proximity, which would prevent runaway token consumption on metered plans. Zero comments so far — an overlooked but high-impact issue.

**#1155 — openai_legacy provider drops reasoning content, causing APIEmptyResponseError**
[Issue #1155](https://github.com/MoonshotAI/kimi-cli/issues/1283) *(closed)*
A bug where the `openai_legacy` provider fails to pass `reasoning_key` to the `OpenAILegacy` constructor, causing reasoning/thinking content from OpenAI-compatible backends (sglang, vllm) to be silently dropped. This leads to `APIEmptyResponseError` on reasoning-mode models. Closed, presumably fixed, but highlights a fragility in the legacy provider path.

---

## 4. Key PR Progress

**PR #2524 — fix(tools): count StrReplaceFile replacements against the running content**
[PR #2524](https://github.com/MoonshotAI/kimi-cli/pull/2524)
Resolves #2526. A critical correctness fix: `StrReplaceFile` applies edits sequentially but previously computed replacement counts against the *original* file content, causing chained edits (where an `old` string is produced by a prior edit) to fail silently or misreport. Closed after review. This directly impacts agentic workflows that chain multiple file edits.

**PR #2506 — fix(kosong): raise a clear error on circular `$ref` in `deref_json_schema`**
[PR #2506](https://github.com/MoonshotAI/kimi-cli/pull/2506)
A self-contained bug fix under the 100-line guideline. The `deref_json_schema` function in `kosong.utils.jsonschema` inlines every local `$ref` recursively but had no cycle detection, causing infinite loops on circular JSON Schema references. The PR adds a clear error instead. Closed after merge.

---

## 5. Feature Request Trends

- **Persistent memory across sessions** is the dominant feature request. Users want the CLI to remember project conventions, past decisions, and user preferences automatically — not just within a single conversation.
- **Quota-aware resource management** is emerging: users want compaction and context management to respect their subscription token budget, not just the model's hard context limit.
- **Transparency in metering and pricing** is a growing concern, as evidenced by the instrumentation work in #2604. The community is building its own audit trails when the official tooling doesn't provide enough visibility.

---

## 6. Developer Pain Points

1. **Opaque token accounting**: The #2604 issue reveals that power users feel the need to build independent wire-level ledgers because the CLI's own token reporting doesn't inspire confidence. This is a trust and transparency gap.
2. **Agentic editing edge cases**: PR #2524 and the related issue #2526 highlight that chained file operations — common in agentic coding workflows — previously had subtle correctness bugs around replacement counting.
3. **Context compaction misalignment**: Issue #2603 points out that the compaction trigger is decoupled from actual cost concerns. On a 1M-token window, sessions can consume enormous token budgets before compaction fires, which is especially painful on metered plans.
4. **Legacy provider fragility**: Issue #1155 shows that the `openai_legacy` provider path is fragile, particularly around reasoning-model support. Self-hosted deployments using sglang/vllm may hit unexpected empty-response errors.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-16

## 1. Today's Highlights

OpenCode's v2 infrastructure is advancing rapidly with new workspace providers (Incus, Docker blueprints) and session-level budget controls landing in PRs. On the backend, the team is addressing a critical unbounded SQLite event-table growth issue and hardening event persistence for CLI-managed servers. Meanwhile, users continue to report friction around Go subscription balancing, grok-4.5 reliability, and upstream endpoint availability.

---

## 2. Releases

No releases published in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Comments | 👍 | Why it matters |
|---|-------|----------|----|----------------|
| [#33356](https://github.com/anomalyco/opencode/issues/33356) | `[2.0] Unbounded growth of the event table: opencode.db reaches 13GB+` | 19 | 5 | Long-lived instances fill volumes — no retention or compaction on the `event` table. Affects operational reliability for power users. |
| [#37790](https://github.com/anomalyco/opencode/issues/37790) | `Bug: Go subscription paid but workspace shows "Insufficient balance"` | 14 | 0 | Payment confirmed via Stripe yet the workspace remains blocked. Direct revenue-trust issue. |
| [#24879](https://github.com/anomalyco/opencode/issues/24879) | `Feature: Go Pro tier ($20) and Share modifier with first-month discounts` | 11 | 11 | Community-driven pricing tier request to address monthly cap frustration; high thumbs-up signal. |
| [#42143](https://github.com/anomalyco/opencode/issues/42143) | `Why does OpenCode require me to subscribe when the official website states it's 100% free?` | 10 | 1 | Trust gap between marketing and product experience; needs clear communication. |
| [#7801](https://github.com/anomalyco/opencode/issues/7801) | `Feature: Plan Mode + Question tool can auto-switch to Build mode` | 10 | 31 | High-engagement feature request for smoother Plan→Build workflow transitions. |
| [#40206](https://github.com/anomalyco/opencode/issues/40206) | `[CLOSED] grok-4.5 on OpenCode Go not working since 2 Aug` | 9 | 1 | `grok-4.5` returning HTTP 500 via the Chat Completions API; impacts users relying on this model. |
| [#27924](https://github.com/anomalyco/opencode/issues/27924) | `Bug: infinite compaction loop when compression fails to reduce context` | 8 | 0 | Session compaction can deadlock when context isn't reduced below the token limit — crashes long sessions. |
| [#35649](https://github.com/anomalyco/opencode/issues/35649) | `Links wrapped across lines not clickable in Kitty terminal` | 5 | 2 | OSC-8 hyperlink rendering breaks on line-wrap; affects terminal UX across multiple terminals. |
| [#42750](https://github.com/anomalyco/opencode/issues/42750) | `Upstream request failed: Endpoint is unavailable` | 4 | 0 | Recurring upstream connectivity failures; part of a broader reliability concern. |
| [#37671](https://github.com/anomalyco/opencode/issues/37671) | `[2.0] v2 CLI: headless commands load OpenTUI and leak native temp files` | 4 | 2 | Every headless call (`--version`, `api`, etc.) leaks a 13 MiB `libopentui.so` to `/tmp` — hygiene and resource concern. |

---

## 4. Key PR Progress

| # | PR | Type | Summary |
|---|----|------|---------|
| [#42840](https://github.com/anomalyco/opencode/pull/42840) | `fix(cli): expose durable event persistence` | Bug fix | Maps `OPENCODE_EVENTS_PERSIST=1` to `ServerOptions.events.persist` for CLI-managed servers, addressing event-loss concerns under restarts. |
| [#42829](https://github.com/anomalyco/opencode/pull/42829) | `feat(core): add Incus workspace forks` | Feature | New Incus-backed workspace provider with snapshot-based forking, idle-instance lifecycle management, and isolated child workspaces for subagents. |
| [#42831](https://github.com/anomalyco/opencode/pull/42831) | `feat(core): add Docker blueprint workspaces` | Feature | Local Docker workspace provider using immutable blueprint snapshots; coordinates fork/stop/wake lifecycle for workspace-backed subagents. |
| [#27554](https://github.com/anomalyco/opencode/pull/27554) | `feat(opencode): local LAN provider discovery + auto-discover models` | Feature | mDNS/DNS-SD auto-discovery of local OpenAI-compatible servers; closes long-standing local-model-access gap. |
| [#42811](https://github.com/anomalyco/opencode/pull/42811) | `feat(session): add viewed state` | Feature | Moves unread/viewed state from per-TUI local storage into session-level facts, eliminating client disagreement on read status. |
| [#42836](https://github.com/anomalyco/opencode/pull/42836) | `fix(acp): prefer default agent's model over config default for new sessions` | Bug fix | ACP `session/new` now resolves the default model from the agent config rather than the global default, fixing unexpected model selection. |
| [#42833](https://github.com/anomalyco/opencode/pull/42833) | `fix(session-ui): prevent variant select overlap on mobile` | Bug fix | Fixes reasoning-effort select overlapping the send button on 320–390 px viewports. |
| [#42823](https://github.com/anomalyco/opencode/pull/42823) | `feat(opencode): add per-session budget limit` | Feature | New `budget` field on sessions (schema, DB migration, `PATCH /session/:id`); stops the assistant once cost reaches the limit. |
| [#42824](https://github.com/anomalyco/opencode/pull/42824) | `feat(app): add voice input and session budget UI` | Feature | Mic button for continuous speech-to-text in the prompt input; paired session-budget panel in the app UI. |
| [#42825](https://github.com/anomalyco/opencode/pull/42825) | `fix(app): release virtualized timeline elements` | Bug fix | Releases detached DOM nodes from TanStack Virtual after Solid removes them, preventing heap growth (~37,500 retained nodes observed in long sessions). |

---

## 5. Feature Request Trends

- **Tiered / usage-based pricing for Go** — Multiple issues (#24879, #37790, #42143) converge on a need for a higher-cap Go Pro tier, clearer free-vs-paid boundaries, and first-month discount options.
- **Workspace isolation & lifecycle management** — Incus (#42829) and Docker (#42831) blueprint PRs respond to community demand for containerized, ephemeral subagent workspaces with snapshot/fork semantics.
- **Session-level state & observability** — Viewed/unread state (#42811), per-session budget limits (#42823), and durable event persistence (#42840) all point toward richer session lifecycle controls.
- **Local & LAN model discovery** — PR #27554 continues demand for plug-and-play local OpenAI-compatible server integration.
- **Plan→Build workflow automation** — Issue #7801 (31 👍) reflects sustained interest in context-aware mode switching without manual intervention.

---

## 6. Developer Pain Points

- **Unbounded SQLite event growth** (#33356): The `event` table grows without retention or compaction, reaching 13 GB+ on long-lived instances and threatening volume exhaustion.
- **Subscription balance desync** (#37790, #42143): Paid Go subscriptions occasionally fail to reflect balance updates, blocking access and eroding trust.
- **Upstream endpoint instability** (#40206, #42750, #42799): `grok-4.5` 500s, repeated "Endpoint is unavailable" retries, and `/workspace` 500 errors with `ResourceExhausted` DB pool errors indicate infra reliability issues.
- **Infinite compaction loops** (#27924): When compression cannot reduce context below the token limit, sessions enter an unrecoverable compaction loop.
- **Terminal hyperlink rendering** (#35649, #42805): URLs that wrap across lines lose clickability in terminals like Kitty — a recurring TUI/UX bug.
- **Headless process hygiene** (#37671): Non-TUI CLI commands unnecessarily load the full OpenTUI native library and leak 13 MiB temp files per invocation.
- **Virtualized UI memory leaks** (#42825): Long sessions accumulate tens of thousands of detached DOM nodes in the renderer, causing memory bloat.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-16

## 1. Today's Highlights

The Pi coding-agent project saw a flurry of compaction and session-restoration fixes, including a critical change to treat `tokens.total` as billable-only (excluding cache tokens) and a guard against continuing from trailing assistant messages after compaction. Additionally, the xAI provider got a full routing overhaul to the Responses API with Grok 4.6 as the new default, and the Mermaid renderer migration from `grok-mermaid` to `lovely-mermaid` is underway.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#6879](https://github.com/earendil-works/pi/issues/6879) | **Auto-compaction never triggers after context grows past 100% until provider overflow** | Compaction only fires when the API rejects the request (e.g., at 373k tokens), leaving the session bloated and inefficient for hours. A 2-hour agentic turn on gpt-5.6-sol is the reported trigger. | 🔥 17 👍 — strong consensus that compaction should be checked after every agent turn, not just on provider error. |
| [#6187](https://github.com/earendil-works/pi/issues/6187) | **Pi login hangs in WSL after browser-based GitHub Copilot device authorization** | WSL users completing Copilot device auth via browser find the client never detects the completion, leaving them stuck. | 27 comments — high engagement suggests this is a frequent pain point for WSL+Copilot users. |
| [#7855](https://github.com/earendil-works/pi/issues/7855) | **Pi stops with "Response was truncated before completion."** | Random truncation errors across any OpenAI-compatible API (including local VLLM) force manual continuation prompts, breaking agent flows. | 5 comments, 1 👍 — recurring annoyance with unclear root cause. |
| [#8170](https://github.com/earendil-works/pi/issues/8170) | **Windows: bash tool can kill its own host via image-wide taskkill** | Pi's `bash` tool executed `taskkill /F /IM node.exe` without confirmation, forcibly killing the Pi/pi-web host process. A serious safety gap. | 2 comments — flagged as a critical Windows-specific bug. |
| [#8028](https://github.com/earendil-works/pi/issues/8028) | **TUI `fullRender` crashes with `RangeError` when output exceeds V8 string limit** | Video-production agents reading大量 frames hit V8's string-length ceiling, causing an uncaught exception and crash. | 2 comments — edge case but severe for power users running long-running media agents. |
| [#8003](https://github.com/earendil-works/pi/issues/8003) | **Cursor in input box flickers aggressively while assistant is streaming** | Aggressive cursor blinking during streaming, especially while typing, degrades UX noticeably. | 2 comments, 1 👍 — quality-of-life issue with broad impact. |
| [#8168](https://github.com/earendil-works/pi/issues/8168) | **Compaction + session restore corrupts tool-result role → 422 error** | After auto-compaction, resumed turns return 422 invalid-request errors because tool messages lose their `tool_calls` adjacency. | 1 👍 — compaction-related correctness bug affecting tool-heavy sessions. |
| [#8166](https://github.com/earendil-works/pi/issues/8166) | **Custom message injected mid-tool-batch breaks tool_calls→tool adjacency** | An extension calling `pi.sendMessage(..., { triggerTurn: false })` mid-batch corrupts the message sequence, causing every subsequent turn to fail with a 400. | 1 👍 — extension-authoring gotcha with cascading failure. |
| [#8184](https://github.com/earendil-works/pi/issues/8184) | **stdout resume-hint not drained before `process.exit` on shutdown** | The "To resume this session:" hint leaks into the parent shell prompt on TUI exit because stdout isn't awaited before exit. | 1 👍 — minor but annoying polish issue. |
| [#8154](https://github.com/earendil-works/pi/issues/8154) | **Hidden thinking blocks leave blank spacer lines in the transcript** | When thinking blocks are hidden via a markdown transformer, 1–2 blank lines remain per block instead of collapsing, cluttering the transcript. | 2 comments — UI polish for thinking-block visibility. |

---

## 4. Key PR Progress

| # | PR | Status | Summary |
|---|-----|--------|---------|
| [#8165](https://github.com/earendil-works/pi/pull/8165) | **fix: `tokens.total` = billable only** | ✅ Closed | `tokens.total` previously included cache-read/cache-write tokens (billed at 1/120th rate), skewing compaction budgets and status stats. Cache tokens now reported separately. |
| [#8164](https://github.com/earendil-works/pi/pull/8164) | **fix: never continue from trailing assistant message after compaction** | ✅ Closed | Silent-overflow compaction on a completed turn caused `agent.continue()` to retry from an assistant message, crashing with "Cannot continue from message role: assistant." Fix limits retry to mid-flight rejections only. |
| [#8153](https://github.com/earendil-works/pi/pull/8153) | **fix: compact at safe turn boundaries** | ✅ Closed | Introduces a run-scoped boundary-compaction API consumed between completed Pi turns. Rebuilds live context in the same run, preserves the native recent tail, and stops before another provider turn when the active signal is aborted. |
| [#8124](https://github.com/earendil-works/pi/pull/8124) | **feat: route xAI models through Responses API, default to Grok 4.6** | 🟡 Open | Switches xAI from Completions to Responses API, sends Pi user-agent, and bumps the default model from Grok 4.5 → Grok 4.6. |
| [#8158](https://github.com/earendil-works/pi/pull/8158) | **feat: upgrade Mermaid terminal rendering** | 🟡 Open | Migrates from `grok-mermaid` to `lovely-mermaid`, inheriting fewer corner cases and more polished parsing. Closes #8157 and #7832. |
| [#8155](https://github.com/earendil-works/pi/pull/8155) | **fix: avoid resetting cursor blink during renders** | 🟡 Open | Tracks terminal cursor visibility in `TuiBase` and emits visibility commands only on state transitions during renders, eliminating the aggressive flicker reported in #8003. |
| [#8151](https://github.com/earendil-works/pi/pull/8151) | **fix: contain widget render failures and tear down ctx-owned widgets on invalidation** | ✅ Closed | Fixes a crash where a third-party extension (`@marckrenn/pi-sub-bar`) captured the extension ctx inside its widget `render()` closure; on `/reload` the widget registration survived invalidation, causing failures. |
| [#8181](https://github.com/earendil-works/pi/pull/8181) | **fix: expose low thinking level for DeepSeek V4 Flash on opencode/opencode-go** | ✅ Closed | `DEEPSEEK_V4_FLASH_THINKING_LEVEL_MAP` was only applied to the direct DeepSeek provider; opencode and opencode-go fell back to the V4 map which sets `low: null`. Now unified. |
| [#8174](https://github.com/earendil-works/pi/pull/8174) | **fix: neutral wording for repeated ambiguous length stops** | ✅ Closed | A second recoverable `length` stop always emitted the "Context overflow recovery failed" message even when neither response matched `isContextOverflow`. Wording now reflects the actual state. |
| [#8146](https://github.com/earendil-works/pi/pull/8146) | **fix: cap Baseten DeepSeek V4 Flash output at 384k tokens** | ✅ Closed | models.dev lists a 1M-token output limit, but Baseten enforces 384k. Requests above 384k fail silently. Caps `maxTokens` at 384,000 for this model/provider combo. |

---

## 5. Feature Request Trends

- **Granular compaction control** — Multiple issues (#6879, #8175, #8173) converge on the need for compaction to fire proactively at safe boundaries, expose failure reasons to extensions, and support per-turn truncation strategies (pruner/spill extensions).
- **Thinking-level configurability** — Requests for per-model thinking-level persistence (#7871) and additional levels like `low` for DeepSeek V4 Flash (#8182/#8181) signal demand for finer control over reasoning effort per provider.
- **Extension event surface** — Users want richer extension hooks: `ui_dialog_start`/`end` (#7147), `model_select_before` (#8169), and compaction failure exposure (#8175) — all pointing to a desire for deeper extension lifecycle integration.
- **TUI polish** — Configurable mouse-wheel scroll (#7765), fixed-height thinking blocks with auto-collapse (#8171), and cursor flicker fixes (#8003/#8155) show sustained interest in TUI ergonomics.
- **Provider coverage** — New built-in provider requests (LLMTR #8178) and routing improvements (xAI → Responses API #8124) reflect ongoing efforts to broaden and modernize provider support.

---

## 6. Developer Pain Points

1. **Compaction correctness** — The #6879 issue (17 👍) and multiple compaction-related bugs (#8164, #8168, #8175) reveal that compaction remains a fragile subsystem: it fires too late, corrupts message sequences on restore, and hides failures from extensions.
2. **Windows safety gaps** — The `taskkill` incident (#8170) highlights that Pi's bash tool on Windows lacks confirmation guards for destructive commands, a recurring concern for Windows users.
3. **WSL/Copilot auth flow** — #6187 (27 comments) shows the GitHub Copilot device-authorization flow in WSL is broken end-to-end, with no reliable recovery path.
4. **V8 string limits in TUI** — #8028 exposes that unbounded transcript rendering can hit Node.js string-length ceilings, a risk for agents processing large media or codebases.
5. **Extension lifecycle fragility** — Widget render failures (#8151), missing compaction events (#8175), and mid-tool-batch injection bugs (#8166) indicate that the extension API surface still has gaps in error isolation and message-sequence guarantees.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-16

## 1. Today's Highlights
The Qwen Code team shipped a new preview release (`v0.21.12-preview.5`) featuring a **deny‑by‑default footprint gate** for the autofix component, tightening security around agent actions. Simultaneously, the `review` pipeline saw a burst of seven critical defect repairs, multiple concurrency hardening fixes, and CI resilience improvements to make automated review runs more robust on self‑hosted runners. Community feedback highlighted persistent UI pain points in the Web Shell (artifact‑panel error spam, white‑screen on daemon restart) and a high‑priority memory‑management issue causing OOM crashes during long sessions.

## 2. Releases
* **v0.21.12‑preview.5** – Latest preview release (2026‑08‑16).  
  **Notable change:** `feat(autofix): deny‑by‑default footprint gate and positional window censuses` (#9156) – restricts autofix actions that would exceed defined footprint or positional windows unless explicitly allowed.  
  *Changelog:* https://github.com/QwenLM/qwen‑code/compare/v0.21.12…v0.21.12‑preview.5

* **v0.21.11‑nightly.20260816.5677823abb** – Nightly build for internal testing.

## 3. Hot Issues
1. **[SEC] autofix: PAT‑bearing jobs share a host with untrusted branch code** (#9089) – Identifies a runner‑level isolation gap that could allow a malicious branch to affect a PAT‑privileged job. *Community reaction:* 4 comments, marked P1. [Link](https://github.com/QwenLM/qwen‑code/issues/9089)
2. **qwen 跑出来 oom 问题** (#9198) – Session runs for over a week and exhausts 1 TB server memory; terminal output becomes garbled. *Community reaction:* 3 comments, high frustration. [Link](https://github.com/QwenLM/qwen‑code/issues/9198)
3. **web‑shell: artifact panel spams ‘Load artifacts failed’** (#7427) – Automatic refresh of the artifact panel constantly triggers fetch‑error toasts. *Community reaction:* 5 comments, marked welcome‑pr. [Link](https://github.com/QwenLM/qwen‑code/issues/7427)
4. **/review presubmit overlap matching is exact‑line only** (#9219) – Multi‑line range comments and semantic duplicates slip through because overlap detection uses only `(path, line)` equality. *Community reaction:* 4 comments, P2. [Link](https://github.com/QwenLM/qwen‑code/issues/9219)
5. **/review presubmit –new‑findings rejects the Step 6 findings artifact** (#9218) – The canonical findings file produced by the skill’s own example is incorrectly rejected as a duplicate. *Community reaction:* 4 comments, P2. [Link](https://github.com/QwenLM/qwen‑code/issues/9218)
6. **qwen serve host writer hard‑codes new‑file mode 0600** (#9250) – `write_file`, `edit`, and `notebook_edit` ignore the daemon’s umask and no configuration exists to change the default mode. *Community reaction:* 4 comments, P3. [Link](https://github.com/QwenLM/qwen‑code/issues/9250)
7. **/review: concurrent same‑PR reviews race on the fixed worktree path** (#9205) – Two sessions reviewing the same PR can delete each other’s worktree mid‑run. *Community reaction:* 3 comments, P2. [Link](https://github.com/QwenLM/qwen‑code/issues/9205)
8. **/review: verification probes mutate the shared worktree while reverse auditors read it** (#9207) – Mutation probes left in the worktree corrupt concurrent review runs. *Community reaction:* 3 comments, P2. [Link](https://github.com/QwenLM/qwen‑code/issues/9207)
9. **0.19.3 UI 不定期错误，中文输入法完全无效** (#5966) – Chinese IME becomes unresponsive; can only type pinyin, no error shown. *Community reaction:* 4 comments, long‑standing. [Link](https://github.com/QwenLM/qwen‑code/issues/5966)
10. **Web Shell dev tabs white‑screen after dev‑server/daemon restarts** (#9253) – Long‑open dev tabs turn white with no recovery UI. *Community reaction:* 2 comments, P2. [Link](https://github.com/QwenLM/qwen‑code/issues/9253)

## 4. Key PR Progress
1. **#9175 – fix(review): repair seven pipeline defects** (by @wenshao) – Fixes structural bugs in the review pipeline discovered through live runs against real PRs.
2. **#9222 – fix(review): normalize last‑gate inputs and anchor mid‑line fragments** – Resolves schema‑friction failures that rejected inputs produced by earlier review stages.
3. **#9213 – fix(review): fix silent reverse‑audit retirement failures** – Makes dry‑receipt retirement observable and corrects the receipt shape that broke retirement.
4. **#9212 – fix(review): exempt carried‑id re‑posts from the presubmit overlap drop** – Overlap gate becomes id‑aware, preserving re‑posted findings with carried ledger IDs.
5. **#9215 – fix(review): give duplicate‑dropped Suggestions their own compose state** – Deduplicated Suggestions now retain their own state and a clear “duplicate” sentence.
6. **#9211 – fix(review): lock the PR review worktree lease against concurrent sessions** – Prevents worktree races by using the lease as a lock before destructive operations.
7. **#9184 – fix(review): gate the recovered incremental anchor on the model that certified it** – Ensures incremental‑review “skip” shortcuts remain model‑specific, forcing a full re‑review when the model changes.
8. **#9220 – fix(ci): self‑heal failed checkouts on the reused review runners** – Failed checkouts on self‑hosted runners now automatically retry instead of terminating the job.
9. **#9254 – fix(web‑shell): show a boot fallback instead of a white screen** – Adds a dependency‑free watchdog that renders a visible, bilingual error page with a reload button when resources fail to load.
10. **#9122 – feat(web‑shell): improve sidebar session management** – Sessions are easier to scan: hover previews, limited row previews, scrollable long titles, and visual running‑session indicators.

## 5. Feature Request Trends
* **Robust, model‑aware incremental review** – Multiple PRs and issues focus on making incremental anchors reproducible across model changes and fixing schema friction at pipeline gates.
* **UI resilience & error visibility** – Requests for graceful fallbacks (white‑screen → boot error page), suppression of artifact‑refresh spam, and clearer session‑name persistence.
* **Security & isolation hardening** – Demand for runner‑level PAT isolation, configurable file‑creation modes, and redaction of

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-16

## 1. Today's Highlights
The v0.9.8 release stabilization continues with a series of fixes targeting macOS test failures, CI concurrency races, and provider‑registry assertion drift. The community has also closed a three‑week translation debate by settling on **宪章** (“charter”) for the Constitution, and several enhancements addressing terminal width regression, third‑party model configuration, and configurable result‑size limits are now in review.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
| Issue | Summary | Why It Matters |
|-------|---------|----------------|
| [#4949](https://github.com/Hmbown/CodeWhale/issues/4949) | Discussion: Chinese translation of “Constitution” | Highlights community involvement in localization; closed after settling on **宪章** (charter) to avoid political connotations. |
| [#5374](https://github.com/Hmbown/CodeWhale/issues/5374) | Bug: agent‑written text appears corrupted on macOS | Directly impacts read‑ability of streaming responses; a fix is already merged (#5404). |
| [#5350](https://github.com/Hmbown/CodeWhale/issues/5350) | Enhancement: simplify third‑party model config with pre‑built templates | Reduces onboarding friction for providers like OpenCode Zen, Agnes, and Sensenova; PR #5406 implements this. |
| [#5367](https://github.com/Hmbown/CodeWhale/issues/5367) | Enhancement: configurable model‑visible read/tool‑result size limits | Addresses the needs of self‑hosted long‑context models (e.g., DeepSeek V4) that currently hit conservative ceilings. |
| [#5370](https://github.com/Hmbown/CodeWhale/issues/5370) | P0: web UI looks broken – audit and rebuild | Flags a serious regression in the public Next.js app; scope includes the managed CWC app as well. |
| [#5241](https://github.com/Hmbown/CodeWhale/issues/5241) | Pricing endpoint returns 503 – all sessions show `unverified_live_pricing` | Breaks cost display across providers; a fix (#5402) restores honest fallback pricing when live checks fail. |
| [#5413](https://github.com/Hmbown/CodeWhale/issues/5413) | Regression: sudo no longer works in v0.9.x | Affects users in the wheel group who rely on privilege escalation; highlights sandbox‑permission changes. |
| [#5410](https://github.com/Hmbown/CodeWhale/issues/5410) | Enhancement: allow additional roots in the bwrap sandbox | Enables development workflows (e.g., Zig builds) that require access to `/dev/null` or system libraries. |
| [#5337](https://github.com/Hmbown/CodeWhale/issues/5337) | Web: finish dictionary spine – retire `isZh` branches | Completes the i18n restructuring initiated in #4934; reduces maintainability debt. |
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | EPIC‑005: Crate decomposition umbrella | Tracks the ongoing refactoring of the TUI into smaller crates; a key architectural milestone. |

## 4. Key PR Progress
| PR | Description |
|----|-------------|
| [#5406](https://github.com/Hmbown/CodeWhale/pull/5406) | Implements prefab third‑party provider templates (OpenCode Zen, OpenCode Go, Agnes, SenseNova) so users only need to supply an API key. |
| [#5405](https://github.com/Hmbown/CodeWhale/pull/5405) | Adds configurable model‑visible read/tool‑result budgets at the model/HarnessProfile level, easing constraints for long‑context models. |
| [#5404](https://github.com/Hmbown/CodeWhale/pull/5404) | Fixes UTF‑8 corruption on macOS by failing closed when SSE data is split across HTTP/2 DATA frames. |
| [#5400](https://github.com/Hmbown/CodeWhale/pull/5400) | Restores full‑terminal‑width transcript in wide displays, reversing the v0.9 regression. |
| [#5402](https://github.com/Hmbown/CodeWhale/pull/5402) | Restores session cost display when live pricing is unverifiable (e.g., 503 from the control plane). |
| [#5409](https://github.com/Hmbown/CodeWhale/pull/5409) | Maps the canonical `"ultra"` reasoning‑effort alias, replacing the legacy `"ultracode"` input. |
| [#5399](https://github.com/Hmbown/CodeWhale/pull/5399) | Stabilizes v0.9.8: fixes turn‑owned default subagents, compaction quality, and the Blue Stage web UI. |
| [#5396](https://github.com/Hmbown/CodeWhale/pull/5396) | Fixes `agy_credentials` tests on macOS by canonicalizing fixtures (symlink handling in `/var`). |
| [#5395](https://github.com/Hmbown/CodeWhale/pull/5395) | Resolves a CI race where `cancel‑in‑progress` would kill concurrent pushes to `main`, hiding failures. |
| [#5401](https://github.com/Hmbown/CodeWhale/pull/5401) | Addresses CodeQL High findings and prepares for GHSA disclosures (#88–#107). |

## 5. Feature Request Trends
The community is pushing for:
- **Simplified configuration** – pre‑built templates and one‑click test‑connection buttons for third‑party providers.
- **Fine‑grained resource controls** – configurable size limits for tool results and read budgets to accommodate self‑hosted long‑context models.
- **Improved terminal and UI fidelity** – restoring full‑width transcripts, fixing macOS text‑corruption bugs, and auditing the web UI.
- **Sandbox flexibility** – allowing additional mount points and device access (e.g., `/dev/null`) within the `bwrap` container.
- **Localization consistency** – retiring legacy i18n branches and settling on clear, non‑political terminology.

## 6. Developer Pain Points
- **macOS‑specific test failures** – symlink restrictions in temp directories and secure‑file‑opening logic break several integration tests.
- **CI concurrency races** – earlier workflows canceled pending runs, masking regressions; now fixed.
- **Provider‑registry drift** – assertions for provider counts became stale after new backends were added, causing CI red‑bars.
- **Streaming corruption** – UTF‑8 boundaries split across HTTP/2 DATA frames produced garbled output on macOS.
- **Pricing regressions** – a 503 from the pricing endpoint left all sessions showing unverified costs until a fallback was implemented.
- **Sandbox restrictions** – the `bwrap` sandbox inadvertently blocked common development operations (sudo, `/dev/null` writes, system‑library linking).
- **Web UI breakage** – the public Next.js app suffered layout and feature regressions requiring a full audit.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*