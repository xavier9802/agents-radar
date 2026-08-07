# OpenClaw Ecosystem Digest 2026-08-07

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-07 02:56 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw Deep Dive



# OpenClaw Project Digest — 2026‑08‑07

## 1. Today's Overview
OpenClaw activity remains extremely high with **500 issues** and **500 PRs** updated in the last 24 hours. The project is in a dense stabilization phase: 430 open issues and 397 open PRs indicate ongoing triage and development velocity. No new releases were published today, but several critical regressions and security‑adjacent bugs are actively being tracked. Community engagement is strong, with long‑running enhancement requests still drawing significant discussion.

## 2. Releases
*No new releases published today.*

## 3. Project Progress
**Closed/Merged today (superseded or completed):**
- [#118409](https://github.com/openclaw/openclaw/pull/118409) — Keep sandboxed gateway locks out of live state dirs (superseded by a later fix).
- [#119226](https://github.com/openclaw/openclaw/pull/119226) — Derive gateway lock dir from resolved state dir (superseded).
- [#119240](https://github.com/openclaw/openclaw/pull/119240) — Report vector store available on fast status path (superseded).
- [#117572](https://github.com/openclaw/openclaw/pull/117572) — Distinguish persisted vector index status (superseded).
- [#118421](https://github.com/openclaw/openclaw/pull/118421) — Report vector store ready from persisted chunks on fast path (superseded).
- [#119573](https://github.com/openclaw/openclaw/pull/119573) — Pass agent configured model to runtime session initialization (superseded).

**Notable open PRs advancing features/fixes:**
- [#120126](https://github.com/openclaw/openclaw/pull/120126) — Fix Telegram silent error‑notification failure.
- [#120104](https://github.com/openclaw/openclaw/pull/120104) — Settle ingress claim when a turn fails before adoption (addresses #119979).
- [#117641](https://github.com/openclaw/openclaw/pull/117641) — Keep active turns from being interrupted on SIGTERM (waiting on author).
- [#117354](https://github.com/openclaw/openclaw/pull/117354) — Chunk long Discord thread‑initial messages (ready for maintainer).
- [#111125](https://github.com/openclaw/openclaw/pull/111125) — Reject non‑object MCP app‑tool arguments (needs proof).
- [#112174](https://github.com/openclaw/openclaw/pull/112174) — Localized Chinese rate‑limit messages skip same‑model retry (needs proof).
- [#116382](https://github.com/openclaw/openclaw/pull/116382) — Avoid false branch‑switch errors after background updates (fixes #115700).

## 4. Community Hot Topics
| Issue | Comments | 👍 | Theme |
|-------|----------|----|-------|
| [#75](https://github.com/openclaw/openclaw/issues/75) — Linux/Windows Clawdbot Apps | 116 | 80 | Platform parity for desktop clients |
| [#116277](https://github.com/openclaw/openclaw/issues/116277) — DeepSeek v4 Flash silent reply failure | 114 | 0 | Model‑specific reliability, fallback behavior |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source | 28 | 0 | Security‑conscious memory management |
| [#27445](https://github.com/openclaw/openclaw/issues/27445) — `announceTarget` for sub‑agent completion routing | 12 | 5 | Multi‑agent orchestration control |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) — DeepSeek V4 Flash incomplete turn | 10 | 1 | Model‑provider integration bugs |
| [#90354](https://github.com/openclaw/openclaw/issues/90354) — Bounded/validated append semantics for pre‑compaction memory flush | 10 | 1 | Memory‑write safety and overflow prevention |
| [#118785](https://github.com/openclaw/openclaw/issues/118785) — QA for containers and external app SDK | 9 | 0 | Security audit coverage |
| [#87756](https://github.com/openclaw/openclaw/issues/87756) — Regression: prompt‑launched Lobster workflow hangs | 9 | 1 | Tool‑invoke reliability |
| [#71736](https://github.com/openclaw/openclaw/issues/71736) — Control UI plugin contribution slots (RFC) | 9 | 1 | Extensibility architecture |
| [#119087](https://github.com/openclaw/openclaw/issues/119087) — Gateway cold‑start regressed ~2.5× | 9 | 0 | Performance regression in containerized deployments |

**Analysis:** Users are primarily focused on **platform availability** (Linux/Windows apps), **model reliability** (DeepSeek silent failures, incomplete turns), and **security‑aware memory handling** (trust tagging, bounded appends). The high comment volume on platform‑gap and model‑bug issues indicates strong demand for parity and robustness.

## 5. Bugs & Stability
**P0 (critical):**
- [#119263](https://github.com/openclaw/openclaw/issues/119263) — Agent DB v14→v15 migration fails (`no such column: entry_valid`), gateway refuses to start. *(No fix PR yet.)*
- [#118772](https://github.com/openclaw/openclaw/issues/118772) — `sessionEntry.totalTokens` inflation causes premature compaction at 4–8% of context window (data loss). *(No fix PR yet.)*

**P1 (high):**
- [#116277](https://github.com/openclaw/openclaw/issues/116277) — DeepSeek v4 Flash silent reply failure. *(No fix PR yet.)*
- [#115700](https://github.com/openclaw/openclaw/issues/115700) — `chat.send` rejected with “thread switched branches” after model completes. Fix PR [#116382](https://github.com/openclaw/openclaw/pull/116382) open.
- [#90944](https://github.com/openclaw/openclaw/issues/90944) — `sessions_yield` resume reply recorded but not delivered; user gets child raw summary instead of parent reply. *(No fix PR yet.)*
- [#88079](https://github.com/openclaw/openclaw/issues/88079) — Regression: WebChat reasoning_content not streamed for Kimi Code & DeepSeek Reasoner. *(No fix PR yet.)*
- [#95553](https://github.com/openclaw/openclaw/issues/95553) — Preflight compaction hard‑capped at ~60s, ignores `compaction.timeoutSeconds`. *(No fix PR yet.)*
- [#86012](https://github.com/openclaw/openclaw/issues/86012) — LINE channel messages silently lost due to reply‑token expiry. *(No fix PR yet.)*
- [#117358](https://github.com/openclaw/openclaw/issues/117358) — Post‑turn compaction ignores boundaries and delays completed replies. *(No fix PR yet.)*
- [#115546](https://github.com/openclaw/openclaw/issues/115546) — CLI‑budget compaction timeout fires far below deadline (100% failure on large sessions). *(No fix PR yet.)*
- [#86050](https://github.com/openclaw/openclaw/issues/86050) — Gateway buffers claude‑cli stream events; surfaces see only final assembled message. *(No fix PR yet.)*
- [#117209](https://github.com/openclaw/openclaw/issues/117209) — `AuthProfileStoreUnreadable` sticky after runtime snapshot publication failure. *(No fix PR yet.)*
- [#117445](https://github.com/openclaw/openclaw/issues/117445) — Feishu DM decoded as “?”; ingress spool throws, replies=0. Fix PR [#117455](https://github.com/openclaw/openclaw/pull/117455) open.
- [#109881](https://github.com/openclaw/openclaw/issues/109881) — Bedrock thinking‑signature replay protection missing, bricks Claude 4+ sessions. *(No fix PR yet.)*

**P2 (medium):**
- [#119087](https://github.com/openclaw/openclaw/issues/119087) — Gateway cold‑start regressed ~2.5× on 1‑vCPU container.
- [#87756](https://github.com/openclaw/openclaw/issues/87756) — Regression: prompt‑launched Lobster workflow hangs on nested `/tools/invoke`.
- [#119796](https://github.com/openclaw/openclaw/issues/119796) — Windows vitest teardown fails with `EBUSY unlink` on agent state DB.
- [#117609](https://github.com/openclaw/openclaw/issues/117609) — Transient LLM/socket errors not retried at embedded‑assistant stage.
- [#116512](https://github.com/openclaw/openclaw/issues/116512) — Telegram progress duplicates first commentary when snapshot IDs change.
- [#119557](https://github.com/openclaw/openclaw/issues/119557) — Chat delta throttle has no trailing flush, withheld chunk waits indefinitely.
- [#86119](https://github.com/openclaw/openclaw/issues/86119) — Orphaned `node server.js` worker processes accumulate after subagent/cron embedded runs.
- [#114154](https://github.com/openclaw/openclaw/issues/114154) — `bundle‑mcp` tool passes policy but never bundled in agent sessions.
- [#117644](https://github.com/openclaw/openclaw/issues/117644) — Agent emits Unix commands in PowerShell on Windows.

## 6. Feature Requests & Roadmap Signals
| Issue | Comments | 👍 | Summary |
|-------|----------|----|---------|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source | 28 | 0 | Tag memory entries by trust level to prevent memory‑poisoning attacks. |
| [#27445](https://github.com/openclaw/openclaw/issues/27445) — `announceTarget` for sub‑agent completion routing | 12 | 5 | Route sub‑agent completion announces to parent session for orchestration. |
| [#90354](https://github.com/openclaw/openclaw/issues/90354) — Bounded/validated append semantics for pre‑compaction memory flush | 10 | 1 | Hard guardrails for append size, post‑write validation, silent failure handling. |
| [#75](https://github.com/openclaw/openclaw/issues/75) — Linux/Windows Clawdbot Apps | 116 | 80 | Desktop clients for Linux/Windows with feature parity to macOS. |
| [#6599](https://github.com/openclaw/openclaw/issues/6599) — `/models test‑fallback` command | 9 | 1 | Verify model fallback chain configuration without waiting for real failure. |
| [#45565](https://github.com/openclaw/openclaw/issues/45565) — Route gateway lifecycle warnings to dedicated channel | 7 | 1 | Separate system‑health warnings from conversation channels. |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) — DeepSeek V4 Flash incomplete turn | 10 | 1 | *(Bug, but indicates need for more robust model‑provider error handling.)* |
| [#44309](https://github.com/openclaw/openclaw/issues/44309) — One‑way dispatch mode for A2A handoffs | 7 | 1 | Drop‑and‑forget agent‑to‑agent task delivery without reply‑back ping‑pong. |
| [#88154](https://github.com/openclaw/openclaw/issues/88154) — Slack Modal Support for Interactive Workflows | 7 | 1 | Collect structured user input via Slack modals instead of repeated message prompts. |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) — Agent‑triggered context compaction (self‑compact tool) | 6 | 2 | Allow agents to initiate their own context compaction. |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) — Built‑in pace‑aware rate limiting for autonomous agents | 6 | 2 | Track API consumption pace to avoid hitting provider rate limits. |
| [#87362](https://github.com/openclaw/openclaw/issues/87362) — Task‑flow lifecycle hook events for plugin observability | 5 | 1 | Expose internal `TaskFlowRegistryObserverEvent` through plugin SDK. |
| [#87136](https://github.com/openclaw/openclaw/issues/87136) — Compaction absolute token thresholds break when switching models | 5 | 1 | Switch from absolute token counts to relative percentages of context window. |
| [#106475](https://github.com/openclaw/openclaw/issues/106475) — `/pair qr` returns data URL that webchat cannot render | 5 | 1 | Fix QR‑code media rendering in Control UI. |
| [#73537](https://github.com/openclaw/openclaw/issues/73537) — Production‑readiness stability label for releases | 7 | 2 | Add a label indicating a release is stable for production use. |

**Predictions for next release:** The high engagement on **memory trust tagging** (#7707) and **bounded append semantics** (#90354) suggests security‑focused memory controls may be prioritized. **Sub‑agent orchestration** improvements (#27445, #44309) are likely candidates for the next feature sprint. **Linux/Windows desktop apps** (#75) will remain a long‑term roadmap item unless community contributions accelerate.

## 7. User Feedback Summary
**Pain points:**
- **Platform gaps:** Strong demand for Linux/Windows desktop clients (#75) with 80 upvotes and 116 comments.
- **Model reliability:** DeepSeek v4 Flash silent failures (#116277) and incomplete turns (#88657) cause user frustration and loss of messages.
- **Memory safety:** Users are concerned about memory‑poisoning attacks (#7707) and uncontrolled append sizes (#90354).
-

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal Assistant Open‑Source Ecosystem  
**Date:** 2026‑08‑07  
**Analyst:** Agnes‑2.0‑Flash (Sapiens AI)

---

## 1. Ecosystem Overview

The open‑source personal AI assistant landscape is characterized by **high development velocity** and **convergent security‑first priorities**. Projects range from monolithic frameworks (OpenClaw, IronClaw) to specialized session‑isolated assistants (NanoBot, CoPaw), with active communities driving rapid iteration on model reliability, channel integration, and multi‑agent orchestration. The ecosystem shows clear maturity in core agent loops, but stability gaps persist around long‑running sessions, credential management, and platform parity.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Health Score* |
|---------|--------------|-----------|---------|---------------|
| **OpenClaw** | 500 | 500 | None | 🟡 Medium‑High (dense stabilization, P0 DB migration bugs) |
| **NanoBot** | 10 | 18 | None | 🟡 Medium (security‑hardening focus, P1 API‑key leaks) |
| **Hermes Agent** | 50 | 50 | None | 🟡 Medium (god‑file refactor, desktop regressions) |
| **PicoClaw** | 0 | 2 | None | 🟢 Low (steady maintenance) |
| **NanoClaw** | 2 | 14 | None | 🟡 Medium (reliability‑focused, upgrade‑transaction bug) |
| **NullClaw** | 0 | 0 | None | ⚪ Low (inactive) |
| **IronClaw** | 50 | 50 | **v1.1.0** (2026‑08‑06) | 🟡 Medium‑High (post‑release bug backlog, strong contributor momentum) |
| **LobsterAI** | 6 | 4 | None | 🔴 Low‑Medium (stagnant backlog, silent‑failure bugs) |
| **Moltis** | 0 | 0 | None | ⚪ Low (inactive) |
| **CoPaw** | 28 | 50 | None | 🟢 High (very active, many merges, high‑severity infinite‑loop bug) |
| **ZeptoClaw** | 0 | 0 | None | ⚪ Low (inactive) |
| **ZeroClaw** | 36 | 50 | None | 🟡 Medium (v0.9.0 stabilization, SOP‑tooling fragility) |

*Health Score: Based on activity volume, bug severity, and release cadence. 🟢 High = active & stable; 🟡 Medium = active with notable issues; 🔴 Low‑Medium = low velocity or significant blockers; ⚪ Low = minimal activity.*

---

## 3. OpenClaw’s Position vs. Peers

**Advantages:**
- **Scale & velocity:** Largest daily issue/PR volume (500 each), indicating a massive user base and intense triage effort.
- **Broad platform coverage:** Active work on Linux/Windows desktop clients (#75) and deep‑integration channels (Telegram, Discord, Feishu, LINE).
- **Security‑adjacent focus:** Memory‑trust tagging (#7707) and bounded‑append semantics (#90354) address emerging poisoning‑attack concerns.

**Technical approach differences:**
- OpenClaw is a **full‑stack agent framework** with gateway, vector store, and multi‑channel support, whereas NanoBot and Hermes emphasize **session isolation** and **plugin security**.
- CoPaw and IronClaw share OpenClaw’s channel‑integration density but differ in orchestration models (CoPaw’s AG‑UI protocol vs. IronClaw’s Reborn routine engine).

**Community size comparison (by issue/PR activity):**
1. OpenClaw (500/500) – largest
2. Hermes Agent (50/50) – high
3. IronClaw (50/50) – high (post‑release)
4. CoPaw (28/50) – very active
5. ZeroClaw (36/50) – active
6. NanoBot (10/18) – moderate
7. NanoClaw (2/14) – moderate
8. LobsterAI (6/4) – low‑medium
9. PicoClaw (0/2) – low
10. NullClaw/ZeptoClaw/Moltis (0/0) – inactive

---

## 4. Shared Technical Focus Areas

| Requirement | Projects Noting It | Specific Needs |
|-------------|-------------------|----------------|
| **Model reliability & fallback** | OpenClaw, CoPaw, PicoClaw | DeepSeek silent failures, incomplete turns; configurable fallback chains; timeout guards. |
| **Security & credential isolation** | NanoBot, Hermes, ZeroClaw, CoPaw | API‑key leakage via env/subprocess, secret redaction, plugin security scanning, SSRF guards. |
| **Session isolation** | NanoBot, OpenClaw | Per‑session temp‑file boundaries, memory‑trust tagging, bounded append semantics. |
| **Channel reliability** | IronClaw, CoPaw, OpenClaw | Matrix retry logic, Slack delivery targets, Telegram media‑only messages, Feishu card‑auth. |
| **Multi‑agent orchestration (A2A)** | ZeroClaw, OpenClaw, CoPaw | A2A outbound client tools, sub‑agent completion routing, one‑way dispatch mode. |
| **Desktop parity** | OpenClaw, Hermes | Linux/Windows apps (#75), desktop regressions (missing panels, SSH version checks). |
| **Observability & diagnostics** | IronClaw, Hermes, CoPaw | Inspector tooling (prompt capture, model‑call stats), per‑call token logging, SOP validation. |
| **Context compaction & memory** | OpenClaw, CoPaw, ZeroClaw | Token‑count persistence, relative‑threshold compaction, date‑change announcements. |
| **SOP/tooling robustness** | ZeroClaw | Cron‑triggered SOPs lacking network access, malformed config silent‑drop, CPU‑spin leaks. |

---

## 5. Differentiation Analysis

| Project | Feature Focus | Target Users | Technical Architecture |
|---------|---------------|--------------|------------------------|
| **OpenClaw** | Comprehensive framework: gateway, vector store, multi‑channel, memory trust | Developers, power users, multi‑tenant operators | Modular, plugin‑based, gateway‑centric, heavy on DB migrations |
| **NanoBot** | Session isolation, temporary‑chat mode, per‑session credential boundaries | Security‑conscious users, shared‑workspace hosts | Workspace‑scoped sessions, proactive channel delivery, temp‑file isolation |
| **Hermes Agent** | Desktop app, plugin security scanning, god‑file decomposition | Desktop‑first users, plugin developers | Python‑based, CLI‑oriented, decomposing monolithic codebases |
| **PicoClaw** | QQ Channel media support, model fallback chains | Chinese‑market users, multimodal chat | Lightweight, channel‑specific enhancements |
| **NanoClaw** | Upgrade transaction safety, stale‑skill cleanup, credential‑proxy bypass | Production operators, system‑service deployers | CLI‑focused, rollback‑safe updates, native credential integration |
| **IronClaw** | Routine engine (Reborn), inspector observability, durable attachments | Workflow automation, scheduled‑task users | Event‑driven, Docker/Railway sandbox profiles, MCP extensions |
| **CoPaw** | Channel retry, infinite‑loop guards, AG‑UI protocol, file‑management API | Multi‑channel operators, long‑session users | Agentscope‑based, SSE streaming, self‑healing browser driver |
| **ZeroClaw** | SOP tooling, A2A outbound client, per‑model context config | Operators needing structured prompts, multi‑agent workflows | Rust‑based, SOP‑first, cross‑turn OTel correlation, v0.9.0 stabilization |
| **LobsterAI** | Per‑model token settings, Windows installer robustness, slash‑ID provider support | Chinese‑language users, custom‑provider setups | Node‑based, OpenClaw fork, config‑granularity focus |

---

## 6. Community Momentum & Maturity

**High‑velocity (rapid iteration):**
- **OpenClaw, Hermes Agent, IronClaw, CoPaw, ZeroClaw** – 50+ issues/PRs daily, active bug triage, frequent merges.

**Medium‑velocity (steady development):**
- **NanoBot, NanoClaw, LobsterAI** – 10‑50 issues/PRs, security‑hardening or stability‑focused sprints.

**Low‑velocity (maintenance or niche):**
- **PicoClaw** – quiet with targeted channel enhancements.
- **NullClaw, ZeptoClaw, Moltis** – inactive, likely dormant or pre‑launch.

**Maturity signals:**
- **IronClaw** released v1.1.0, signaling a move from alpha to stable.
- **ZeroClaw** approaching v0.9.0 with RFC‑driven governance.
- **Hermes** and **OpenClaw** show technical‑debt cleanup (god‑file sharding, memory‑trust tagging).
- **CoPaw** and **NanoBot** emphasize security and isolation, indicating ecosystem maturation around multi‑tenant safety.

---

## 7. Trend Signals

1. **Security‑first by default:** API‑key leakage (NanoBot), plugin scanning (Hermes, ZeroClaw), secret redaction gaps (Hermes, ZeroClaw) are top‑priority concerns across projects.
2. **Model‑provider reliability:** DeepSeek, Qwen3.6, and compatible‑provider failures are driving demand for fallback chains, timeout guards, and reasoning‑content passthrough.
3. **Multi‑agent orchestration (A2A):** ZeroClaw’s outbound‑client RFC, OpenClaw’s sub‑agent routing, and CoPaw’s batch‑mode detection indicate a shift from single‑agent to coordinated workflows.
4. **Channel reliability & parity:** Persistent issues in Slack, Matrix, Telegram, and Feishu show that channel integration remains a fragile layer; users expect enterprise‑grade delivery guarantees.
5. **Observability & diagnostics:** Inspector tooling (IronClaw), per‑call token logging (NanoBot), and SOP validation (ZeroClaw) reflect growing operational maturity.
6. **Desktop & platform parity:** OpenClaw and Hermes are racing to close Linux/Windows gaps, driven by user demand for native clients beyond macOS.
7. **Memory & context safety:** Bounded‑append semantics, trust‑tagging, and relative compaction thresholds show the ecosystem is moving beyond simple token‑count limits toward safer, policy‑driven memory management.

**Value for AI agent developers:**  
- **Integrate security scanning early** (like Hermes) to avoid credential‑leakage reputational damage.  
- **Design for model‑provider variability** with fallback chains and explicit timeout/loop guards (CoPaw, OpenClaw).  
- **Prioritize channel reliability** with retry logic and delivery‑target validation before scaling to multi‑agent features.  
- **Invest in observability** (token usage, prompt capture, SOP validation) to reduce operational friction as agents enter production.

---

*Report generated from community digest data as of 2026‑08‑07. All project links and metrics are sourced from the provided summaries.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-07

## 1. Today's Overview

NanoBot is showing **high development velocity** with 10 issues and 18 pull requests updated in the last 24 hours. The project is currently focused on **security hardening, session isolation, and WebUI refinements**, with two security-critical PRs merged or closed today addressing API key leakage. No new releases were published. The activity mix — heavy on bug fixes and security patches — suggests the team is actively stabilizing a recent burst of feature development around session management and channel integrations.

## 2. Releases

No new releases were published on this date.

## 3. Project Progress

**Merged / Closed PRs:**

- **[#5272](https://github.com/HKUDS/nanobot/pull/5272)** — *fix(session): preserve proactive channel delivery during session retention trimming* — Closed. Fixes the bug where cron/job-delivery messages were dropped during session trimming.
- **[#5231](https://github.com/HKUDS/nanobot/pull/5231)** — *feat(memory): archive idle sessions for Dream* — Closed. Ensures Dream's history input isn't starved by short idle sessions that never hit retention thresholds.
- **[#5248](https://github.com/HKUDS/nanobot/pull/5248)** — *fix(matrix): send non-empty POST body on room join for Continuwuity compatibility* — Closed. Resolves auto-join failures on Continuwity homeservers.
- **[#5267](https://github.com/HKUDS/nanobot/pull/5267)** — *fix(webui): tighten interactive motion* — Closed. Performance/UX polish aligning transitions to ~220ms and respecting reduced-motion preferences.
- **[#5259](https://github.com/HKUDS/nanobot/pull/5259)** — *fix(webui): enforce memory-only temporary sessions* — Closed. Stacks on #5252 to ensure temporary chats stay out of persistent storage.
- **[#5262](https://github.com/HKUDS/nanobot/pull/5262)** — *perf(webui): reduce cold-start payload* — Closed. Adds precompressed gzip assets and keeps React runtime out of lazy chunks.
- **[#5261](https://github.com/HKUDS/nanobot/pull/5261)** — *feat(webui): drag sidebar sessions* — Closed. Enables drag-to-reorder and drag-to-mention in the sidebar.

**Key features advanced today:** Session history isolation from the agent workspace (#5279), temporary chat mode (#5252), MST metasearch provider integration (#5234), and a shared interactive project terminal (#5253).

## 4. Community Hot Topics

| Issue / PR | Author | Comments | Topic |
|---|---|---|---|
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | whisperity | 3 | In-session model switching |
| [#5278](https://github.com/HKUDS/nanobot/issues/5278) | lmzopq | 1 | Session history outside agent workspace |
| [#5276](https://github.com/HKUDS/nanobot/issues/5276) | whisperity | 1 | Session-level temp file isolation |
| [#5279](https://github.com/HKUDS/nanobot/pull/5279) | lmzopq | — | PR addressing #5278 |

**Analysis:** The most discussed topics revolve around **session security and isolation**. User `whisperity` is driving a coherent set of concerns (#5198, #5276, #5274, #5275) around per-session boundaries — model switching, temp file isolation, and Matrix thread semantics. This signals a user base running Nanobot in **multi-tenant or shared-workspace configurations** where strict session isolation is critical. The #5278/#5279 thread specifically highlights a regression from PR #713, which moved sessions into the workspace directory — a change that inadvertently widened the agent's filesystem reach.

## 5. Bugs & Stability

| Severity | Issue / PR | Summary |
|---|---|---|
| **P1 — Security** | [#5270](https://github.com/HKUDS/nanobot/pull/5270) [OPEN] | API keys leaked into CLI subprocess `os.environ` — fix PR open |
| **P1 — Security** | [#5269](https://github.com/HKUDS/nanobot/pull/5269) [OPEN] | Provider API keys written to process-global `os.environ`, causing cross-provider credential leakage |
| **P1 — Data Integrity** | [#5271](https://github.com/HKUDS/nanobot/pull/5271) [OPEN] | Stale background task saves can overwrite session data after `/new` — fix PR open |
| **P2 — Bug** | [#5273](https://github.com/HKUDS/nanobot/issues/5273) [CLOSED] | Session retention trimming drops proactive channel delivery messages — **fixed in #5272** |
| **P2 — Bug** | [#5247](https://github.com/HKUDS/nanobot/issues/5247) [CLOSED] | Matrix bot fails to auto-join Continuwity homeservers — **fixed in #5248** |
| **P2 — Bug** | [#5264](https://github.com/HKUDS/nanobot/issues/5264) [OPEN] | `/api/sessions/{key}/messages` omits `media_urls` for files outside media root — **fixed in #5268** [OPEN] |
| **P2 — Bug** | [#4290](https://github.com/HKUDS/nanobot/issues/4290) [OPEN] | Cronjob ends early when a subagent is spawned — no fix yet (open since Jun 10) |
| **P2 — Bug** | [#5265](https://github.com/HKUDS/nanobot/pull/5265) [OPEN] | Non-finite number parameters (`NaN`, `Infinity`) accepted by tool schema casting — fix PR open |

**Notable:** Two P1 security issues (API key leakage via subprocess and process environment) were raised on the same day by the same author (`LHMQ878`) and have corresponding fix PRs. This suggests a coordinated security review is underway. The cronjob/subagent bug (#4290) has been open for nearly two months with no resolution.

## 6. Feature Requests & Roadmap Signals

| PR / Issue | Author | Description |
|---|---|---|
| [#5252](https://github.com/HKUDS/nanobot/pull/5252) [OPEN] | Re-bin | **Temporary chat mode** — ephemeral, non-persistent conversations stored only in memory |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) [OPEN] | goodtiding5 | **MST metasearch provider** — aggregates DuckDuckGo, Google, Brave, Bing via Reciprocal Rank Fusion |
| [#5253](https://github.com/HKUDS/nanobot/pull/5253) [OPEN] | chengyongru | **Shared interactive project terminal** — persistent PTY shared between WebUI and agent |
| [#5277](https://github.com/HKUDS/nanobot/pull/5277) [OPEN] | Re-bin | **Inline model preset editor** — expand/collapse editor below selected row in WebUI |
| [#5266](https://github.com/HKUDS/nanobot/issues/5266) [OPEN] | knoppix2 | **Per-call token consumption logging** — trace which provider calls burn the most tokens |
| [#5274](https://github.com/HKUDS/nanobot/issues/5274) [OPEN] | whisperity | Matrix reply-feature support (bot should reply-in-thread, not post top-level) |
| [#5275](https://github.com/HKUDS/nanobot/issues/5275) [OPEN] | whisperity | Matrix "reply in thread" should form a dedicated context, like Discord/Slack threads |

**Prediction:** Temporary chat mode (#5252), the MST provider (#5234), and inline model preset editor (#5277) are the most likely candidates for the next release. The shared terminal (#5253) is larger scope and may land later. Token consumption logging (#5266) addresses a frequent user pain point and could ship as a config flag.

## 7. User Feedback Summary

- **Session isolation is a top concern.** Multiple users (`whisperity`, `lmzopq`) are reporting that the workspace-scoped session storage introduced in PR #713 created security gaps — agents can read other sessions' history, and temp files are shared across sessions. These users are running Nanobot in multi-tenant or shared-hosting scenarios.
- **API key leakage is alarming.** The same-day reports of key leakage via both CLI subprocesses (#5270) and process `os.environ` (#5269) indicate users are integrating Nanobot into environments where credential isolation is non-negotiable (e.g., shared hosting, CI/CD pipelines).
- **Token waste is visible and frustrating.** Issue #5266 reports millions of tokens burned in 2 hours with no user activity, pointing to background tasks (cron, session title generation) consuming resources silently. Users want observability into this.
- **Matrix channel UX gaps.** Users expect Matrix "reply" semantics to match Discord/Slack threading behavior (#5274, #5275), suggesting Nanobot's Matrix integration is maturing but hasn't yet matched feature parity with other channels.
- **WebUI drag-and-drop and temporary mode** are positively received (PRs #5261, #5252 closed/merged), indicating the WebUI is a high-visibility surface where polish matters.

## 8. Backlog Watch

| Issue | Author | Open Since | Concern |
|---|---|---|---|
| [#4290](https://github.com/HKUDS/nanobot/issues/4290) | tjc0726 | 2026-06-10 (~58 days) | **Cronjob ends early when subagent spawned** — workflow-breaking bug, no fix yet |
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | whisperity | 2026-07-31 | **In-session model switching blocked** — UX regression vs. SaaS competitors, 3 comments but no PR |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) | yorkhellen | 2026-08-06 | Race condition in session saves — P1 data-integrity bug, PR open but unmerged |
| [#5270](https://github.com/HKUDS/nanobot/pull/5270) | LHMQ878 | 2026-08-06 | API key leak to CLI subprocess — P1 security, PR open but unmerged |
| [#5269](https://github.com/HKUDS/nanobot/pull/5269) | LHMQ878 | 2026-08-06 | API key leak to process environ — P1 security, PR open but unmerged |

**Recommendation:** The two P1 security PRs (#5270, #5269) and the P1 race-condition PR (#5271) should be prioritized for merge before any release. The cronjob/subagent bug (#4290) has been open too long for a workflow-critical issue and warrants a maintainer assignment.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-07

---

## 1. Today's Overview

Hermes Agent is experiencing **high developer velocity** with 50 issues and 50 PRs updated in the last 24 hours, though no new releases were shipped. The dominant theme is a **repo-wide god-file decomposition initiative** (epic #78647) driven by the core team, alongside a burst of desktop-app regression fixes and a new security-scanning layer for plugins. Community engagement is strong — the plugin-interface expansion tracking issue (#64182) continues to accumulate discussion (27 comments). Overall project health is **actively refactoring**: technical debt is being addressed structurally rather than through incremental patches.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

**Merged / Closed PRs (today):**

| PR | Summary |
|----|---------|
| [#80725](https://github.com/NousResearch/hermes-agent/pull/80725) | Auto-formatting fix (lint workflow squash-merge) |
| [#80719](https://github.com/NousResearch/hermes-agent/pull/80719) | Desktop: fixes elapsed-status text overlapping with running-label |
| [#80718](https://github.com/NousResearch/hermes-agent/pull/80718) | Desktop: corrects "Show earlier messages" threshold accounting that hid most of a session |
| [#68708](https://github.com/NousResearch/hermes-agent/pull/68708) | macOS gateway: waits for `launchd` bootout to settle before re-bootstrap, fixing post-update offline state |

**PRs advancing today (open, high-signal):**

- [#80727](https://github.com/NousResearch/hermes-agent/pull/80727) — **Dyad integration skill**: connects Hermes to the open-source AI app builder (21k★), using SQLite + git-backed project state with `AI_RULES.md` context.
- [#80728](https://github.com/NousResearch/hermes-agent/pull/80728) — **Plugin security scanning**: `hermes plugins install/update` now scan the plugin tree before execution (inspired by Claude Cowork). Blocks suspicious plugins outright, requires confirmation for questionable ones.
- [#80729](https://github.com/NousResearch/hermes-agent/pull/80729) — **MCP stdio null-args fix**: treats `args: null` as empty list, resolving the TypeError crash in #80652.
- [#80724](https://github.com/NousResearch/hermes-agent/pull/80724) — **Per-message `token_count` persistence**: finally populates the existing schema column, enabling accurate context-cost measurement for compaction decisions.
- [#80686](https://github.com/NousResearch/hermes-agent/pull/80686) — **`hermes verify` smoke runner**: ports grok-cli's verify subsystem for end-to-end project build/test/start/readiness.
- [#80721](https://github.com/NousResearch/hermes-agent/pull/80721) — **Date-change announcements**: long-running sessions crossing midnight now get a one-line note without invalidating the prompt-cache invariant.

---

## 4. Community Hot Topics

| Issue | Comments | Theme |
|-------|----------|-------|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — *Epic: Shard all 20 god files* | 53 | Refactoring drive; repo-wide policy: "all god files are sharded, never reverted" |
| [#64182](https://github.com/NousResearch/hermes-agent/issues/64182) — *Plugin Interface Expansion (July 2026)* | 27 | Community-facing roadmap for plugin interface stability; long-queued PRs awaiting spec |
| [#78645](https://github.com/NousResearch/hermes-agent/issues/78645) — *Shard `agent/context_compressor.py`* | 19 | 6,789-line god file targeted for decomposition |
| [#79407](https://github.com/NousResearch/hermes-agent/issues/79407) — *Desktop 0.20.0 regression: bottom panel missing* | 8 | **Critical UX regression** — desktop becomes a viewer-only shell after upgrade |
| [#78637](https://github.com/NousResearch/hermes-agent/issues/78637) — *Shard `hermes_cli/auth.py`* | 8 | 9,180-line god file |
| [#7675](https://github.com/NousResearch/hermes-agent/issues/7675) — *Feishu: card interaction / approval / streaming bugs* | 8 | Three interrelated Feishu platform defects |

**Analysis:** The god-file epic (#78647) is the single most-discussed item, reflecting a major architectural cleanup that will affect all contributors. The Feishu platform continues to be a sustained pain point (see Bugs section). The plugin interface roadmap (#64182) shows healthy community co-development but also indicates a bottleneck — contributors have PRs queued pending interface stabilization.

---

## 5. Bugs & Stability

**P2 (High Severity):**

| Issue | Description | Fix PR |
|-------|-------------|--------|
| [#79407](https://github.com/NousResearch/hermes-agent/issues/79407) | **0.20.0 regression**: desktop bottom operation panel completely missing — app is viewer-only shell | — |
| [#79339](https://github.com/NousResearch/hermes-agent/issues/79339) | `MemoryProvider.sync_turn()` never called in 0.20 — external memory backends silently stop receiving completed turns | — |
| [#80652](https://github.com/NousResearch/hermes-agent/issues/80652) | MCP stdio bridge crashes with `TypeError` when `args` is null in config | [#80729](https://github.com/NousResearch/hermes-agent/pull/80729) ✅ open |
| [#79628](https://github.com/NousResearch/hermes-agent/issues/79628) | `use_gateway: true` discards valid direct credential when Tool Gateway is unauthenticated | — |
| [#77484](https://github.com/NousResearch/hermes-agent/issues/77484) | **Security**: `process(action=list)` returns raw command/output with no redaction; `*_KEY` regex miss; ACP plain formatter | — |
| [#77162](https://github.com/NousResearch/hermes-agent/issues/77162) | **Security**: tool-result egress path missing exact-value secret redaction before provider API | — |
| [#13924](https://github.com/NousResearch/hermes-agent/issues/13924) | Feishu command-approval buttons return error code 220340 | — (related to #38305, #25886, #10073) |
| [#25886](https://github.com/NousResearch/hermes-agent/issues/25886) | Feishu card-authorization buttons fail with error 200343 | — |
| [#7675](https://github.com/NousResearch/hermes-agent/issues/7675) | Feishu: card interaction, approval buttons, streaming reply — three issues | — |
| [#74411](https://github.com/NousResearch/hermes-agent/issues/74411) | Desktop SSH mode: version-check runs `python --version <script>` with wrong arg order, falsely rejecting up-to-date installs | — |
| [#80646](https://github.com/NousResearch/hermes-agent/issues/80646) | `agent_context` hardcoded to `"primary"` — cron/flush/subagent context-skip logic is dead code | — |
| [#80259](https://github.com/NousResearch/hermes-agent/issues/80259) | Desktop message reactions gated off for remote-desktop sessions (env var only set locally) | — |
| [#79859](https://github.com/NousResearch/hermes-agent/issues/79859) | Desktop "Talk to Hermes" uses delayed MP3 playback with OpenAI TTS — no barge-in | — |

**P3 (Medium Severity):**

| Issue | Description |
|-------|-------------|
| [#80596](https://github.com/NousResearch/hermes-agent/issues/80596) | Learning graph marks externally-installed skills as "learned" (use_count inflation) |
| [#41331](https://github.com/NousResearch/hermes-agent/issues/41331) | Email plugin: IMAP/SMTP login user hardcoded to `EMAIL_ADDRESS`, breaks custom-domain setups |
| [#77286](https://github.com/NousResearch/hermes-agent/issues/77286) | Update program error submission (Windows) |

**Feishu cluster**: Four related issues (#7675, #13924, #25886, #38305) all describe the same or similar card-authorization failures on the Feishu/Lark platform. PR #10256 (referenced in #38305) remains unmerged — this is a **sustained platform regression** that deserves priority.

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Description | Likelihood for Next Release |
|------------|-------------|----------------------------|
| [#80723](https://github.com/NousResearch/hermes-agent/issues/80723) | Multi-device live-session watching (currently single-transport-slot WS routing) | Medium — architecture change |
| [#80720](https://github.com/NousResearch/hermes-agent/issues/80720) | Kanban attachment rows: open/preview/Quick Look/reveal | Low — UI polish |
| [#70849](https://github.com/NousResearch/hermes-agent/issues/70849) | Per-job `deliver_profile` for multiplexed cron delivery | Medium — gateway feature |
| [#53317](https://github.com/NousResearch/hermes-agent/issues/53317) | Complete `image_gen` / TTS plugin-provider migration (match `video_gen` pattern) | Medium — internal cleanup |
| [#80721](https://github.com/NousResearch/hermes-agent/pull/80721) | Date-change announcements for long-running sessions | **High** — small, non-breaking, already in PR |
| [#80728](https://github.com/NousResearch/hermes-agent/pull/80728) | Plugin security scanning | **High** — security feature, already in PR |
| [#80727](https://github.com/NousResearch/hermes-agent/pull/80727) | Dyad integration skill | Low — new community skill, not core |
| [#80686](https://github.com/NousResearch/hermes-agent/pull/80686) | `hermes verify` smoke runner | Medium — CLI feature |

**Prediction:** The next release will likely include the security-scanning plugin feature, the date-change session fix, the MCP null-args crash fix, and the `token_count` persistence fix — all small-to-medium, low-risk PRs. The god-file sharding epic will continue as a parallel track.

---

## 7. User Feedback Summary

**Pain points:**
- **Desktop 0.20.0 regressions** are the most urgent complaint: missing bottom panel (#79407), broken SSH version check (#74411), reactions disabled on remote desktop (#80259), and poor TTS latency (#79859). Multiple users report the desktop app feels *less functional* post-upgrade.
- **Feishu/Lark card interactions** remain broken across multiple error codes (220340, 200343). Users are forced to type workaround commands (`/approve session`). The unmerged PR #10256 is a clear signal of a bottleneck.
- **External memory backends silently stop working** after the 0.20 upgrade (#79339) — no error, just data loss. This is a critical reliability issue for production users.
- **Credential fallback is broken** when the Tool Gateway is unauthenticated (#79628), producing confusing error messages that tell users to set credentials they already have.
- **Security redaction gaps** (#77484, #77162) mean raw commands and secrets can leak through tool results to model providers — flagged as Medium severity but with real privacy implications.

**Positive signals:**
- Security scanning for plugins (#80728) directly addresses community trust concerns.
- The god-file sharding initiative (#78647) shows the team is investing in long-term maintainability.
- `token_count` persistence (#80724) will finally give users visibility into context-cost, a frequently requested feature.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|------------------------|
| [#38305](https://github.com/NousResearch/hermes-agent/issues/38305) | ~2 months | PR #10256 fix for Feishu 220340 error remains unmerged; affects production Feishu users |
| [#64182](https://github.com/NousResearch/hermes-agent/issues/64182) | ~3 weeks | Plugin interface expansion roadmap; 27 comments, multiple contributors waiting on spec |
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) | 3 days | God-file sharding epic — 20 files, 53 comments. High-impact but high-risk refactoring; needs coordinated PR review capacity |
| [#79407](https://github.com/NousResearch/hermes-agent/issues/79407) | 2 days | 0.20.0 desktop regression with no fix PR yet — blocks a significant user segment |
| [#79339](https://github.com/NousResearch/hermes-agent/issues/79339) | 2 days | Memory provider silent failure in 0.20 — no fix PR, data-loss risk |
| [#77484](https://github.com/NousResearch/hermes-agent/issues/77484) | 4 days | Security redaction gaps — no fix PR; agent produces raw command/output in logs |
| [#77162](https://github.com/NousResearch/hermes-agent/issues/77162) | 4 days | Security: tool-result egress unredacted — no fix PR |
| [#80723](https://github.com/NousResearch/hermes-agent/issues/80723) | <1 day | Multi-device session watching — architecture decision needed before implementation |

**Key risk:** The team is executing a large refactor (god-file sharding across 20 files) while simultaneously managing a cluster of unaddressed P2 bugs from the 0.20.0 release. The Feishu bug cluster and the desktop regression (#79407) are the highest-impact items lacking merged fixes.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-07

## 1. Today's Overview

PicoClaw shows **low daily activity**, with zero new issues and no releases in the past 24 hours. However, 2 pull requests were updated today (1 open, 1 closed), indicating continued development momentum on existing work. The project appears to be in a steady maintenance phase rather than an active sprint cycle. No critical instability signals were detected.

---

## 2. Releases

**No new releases** were published in the last 24 hours.

---

## 3. Project Progress

### Merged/Closed Today
- **[PR #1349](https://github.com/sipeed/picoclaw/pull/1349)** — *feat(qq): support parsing and replying to more attachment types*
  - Closed on 2026-08-06. This enhancement significantly expands QQ Channel integration, adding support for:
    - Parsing QQ Channel emoji structures
    - Handling incoming voice, image, video, and file messages
    - Replying with local attachments (uploaded before sending)
    - Markdown-first reply strategy with graceful fallback
  - **Impact:** Broadens PicoClaw's messaging channel coverage and improves multimodal interaction on QQ.

### Open Today
- **[PR #3200](https://github.com/sipeed/picoclaw/pull/3200)** — *feat(models): add configurable default fallback chain*
  - Open since 2026-07-01, last updated 2026-08-06. Introduces a UI-driven workflow for configuring model fallback chains with persistence through the backend API.
  - **Impact:** Addresses a recurring user need for resilient model routing when primary models are unavailable.

---

## 4. Community Hot Topics

| PR/Issue | Type | Activity | Link |
|----------|------|----------|------|
| PR #1349 | Enhancement (QQ Channel) | ✅ Merged | [PR #1349](https://github.com/sipeed/picoclaw/pull/1349) |
| PR #3200 | Enhancement (Model Fallback) | 🔄 Open | [PR #3200](https://github.com/sipeed/picoclaw/pull/3200) |

**Analysis:**
- **PR #1349** reflects strong community demand for richer QQ Channel support — users need PicoClaw to handle multimedia messages, not just text. The attachment-type expansion signals a maturing multi-channel strategy.
- **PR #3200** addresses a practical pain point: model failures during peak usage. The long open duration (37 days) suggests the feature is valuable but may require careful review before merging.

---

## 5. Bugs & Stability

**No bug reports or stability issues** were filed or resolved in the last 24 hours. The project's issue activity is quiet, which is a positive signal for current stability.

---

## 6. Feature Requests & Roadmap Signals

- **Configurable model fallback chains** (PR #3200) — High user demand for fault-tolerant AI routing. Likely to appear in the next release if merged.
- **Expanded QQ Channel media support** (PR #1349, merged) — Multi-attachment handling is now live; future iterations may add more platforms with similar richness.
- The **long-standing open PR #3200** suggests the roadmap prioritizes reliability and configuration flexibility over new channel additions in the near term.

---

## 7. User Feedback Summary

- **Satisfaction driver:** Users value expanded media handling in messaging channels (demonstrated by PR #1349's merge).
- **Pain point:** Model reliability under failure conditions remains a concern, as evidenced by the persistent request for configurable fallback chains (PR #3200).
- **Satisfaction gap:** No user-reported bugs or complaints surfaced today, indicating the current build is stable for active users.
- The 37-day open window on PR #3200 may indicate user frustration with the lack of a resolution — timely maintainer response is recommended.

---

## 8. Backlog Watch

| Item | Open Since | Days Open | Priority | Link |
|------|-----------|-----------|----------|------|
| PR #3200 — Configurable default fallback chain | 2026-07-01 | ~37 | High | [PR #3200](https://github.com/sipeed/picoclaw/pull/3200) |

**Recommendation:** PR #3200 has been open for over a month and addresses a high-impact reliability feature. Maintainer review and merge guidance would benefit both the project and the community. No other items in the backlog require urgent attention based on today's data.

---

*Data source: [sipeed/picoclaw](https://github.com/sipeed/picoclaw) | Generated: 2026-08-07*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-07

---

## 1. Today's Overview

NanoClaw shows **moderate daily activity** with 2 issues and 14 PRs updated in the last 24 hours. The project is actively maintaining core stability — a transactional upgrade fix (PR #3195) was opened to resolve the same issue flagged in Issue #3194, signaling responsive maintenance. No new releases were published today. Overall, the project is in a **healthy maintenance cycle** with a strong focus on reliability improvements and cleanup of stale integrations.

---

## 2. Releases

*No new releases today.*

---

## 3. Project Progress

### Merged / Closed (6 items)

| # | Title | Author | Notes |
|---|-------|--------|-------|
| #3172 | Remove stale qodo & Google MCP skills | glifocat | **Cleanup** — eliminated two skills with unrecoverable SaaS dependencies |
| #2213 | Accept media-only messages (photo/video/file) | ziv-daniel | **Telegram fix** — messages without captions now reach the agent |
| #2678 | Re-arm recurrence when a run fails permanently | yairixStudio | **Scheduler fix** — failed recurring tasks are now re-queued |
| #2644 | Detect reply-to-bot in Telegram | yairixStudio | **Engagement fix** — replies to the bot are now distinguishable |
| #2679 | Surface permanently-failed scheduled tasks | yairixStudio | **UX improvement** — failed tasks now notify the user instead of silently logging |
| #2873 | Split pre-flight from credentials in `/update-skills` | glifocat | **Architecture** — enables skill code refresh without credential loss |
| #2591 | Namespace user IDs by channel-type prefix | mmahmed | **Fix** — corrects user ID collision across channels |

**Key themes today:** Reliability hardening, Telegram channel fixes, and cleanup of abandoned integrations.

---

## 4. Community Hot Topics

### Most Discussed / Long-Standing

- **PR #2705** — `fix(use-native-credential-proxy): actually bypass the OneCLI gateway` ([link](https://github.com/nanocoai/nanoclaw/pull/2705))
  - Open since June 2026 (2+ months). Fixes compounding credential-proxy failures on real `launchd`/`systemd` installs.
  - **Underlying need:** Users running NanoClaw as a system service need native credential integration to work reliably.

- **Issue #3194** + **PR #3195** — `/update-nanoclaw` transactional upgrade ([issue](https://github.com/nanocoai/nanoclaw/issues/3194), [PR](https://github.com/nanocoai/nanoclaw/pull/3195))
  - The same author (glifocat) filed the bug and immediately opened the fix PR — a sign of responsive core-team maintenance.
  - **Underlying need:** Zero-downtime, rollback-safe upgrades for production deployments.

- **PR #2213** — Media-only Telegram messages ([link](https://github.com/nanocoai/nanoclaw/pull/2213))
  - Open since May, merged today. Resolves a long-standing gap where photo/video-only inputs were silently dropped.
  - **Underlying need:** Full media support expected by Telegram power users.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **🔴 Critical** | #3194 / #3195 | `/update-nanoclaw` stamps success before validation; SQLite and external state are not rolled back on failure | **Fix PR open** (#3195) |
| **🟡 Medium** | #2213 (now closed) | Media-only Telegram messages silently dropped | **Resolved** |
| **🟡 Medium** | #2643 (now closed) | Pattern-mode engagement ignores direct @mentions and DMs | **Resolved** |
| **🟢 Low** | — | No new crash reports today | — |

**Assessment:** The critical upgrade transaction bug is the most significant stability concern. The immediate PR response is encouraging, but until merged, any production `/update-nanoclaw` run carries rollback risk.

---

## 6. Feature Requests & Roadmap Signals

| PR | Title | Signal |
|----|-------|--------|
| #3190 | Add Tavily MCP tool skill | **Search integration** — users want built-in web search via Tavily; likely to ship as a utility skill |
| #3149 | Add `--rw` flag to `groups config add-mount` | **CLI improvement** — read-write mount flag request; small but practical UX enhancement |
| #3186 | Add host seams for skill-owned capabilities | **Architecture** — refactoring to make skills more self-contained; suggests a modular skill system is a priority |

**Prediction:** Tavily search (#3190) is the strongest candidate for the next release, given its clean utility-skill pattern and active discussion. The `--rw` flag (#3149) is likely a quick follow-on.

---

## 7. User Feedback Summary

- **Pain point — Stale SaaS dependencies:** Two qodo skills required an external account that no setup script created. Users hit dead ends with no clear error. Result: skills were removed (#3172).
- **Pain point — Silent failures:** Media-only messages and reply-to-bot detection were silently ignored, causing confusion about whether the agent was "working." Both issues (#2643, #2213) are now resolved.
- **Pain point — Upgrade risk:** Production users running `/update-nanoclaw` risk corrupting their SQLite database or config if validation fails partway through. This is a growing concern as the project scales.
- **Satisfaction signal:** Multiple bug fixes landed in a single day from community contributors (yairixStudio, ziv-daniel, mmahmed), indicating a healthy contributor base.

---

## 8. Backlog Watch

| # | Title | Open Since | Risk |
|---|-------|-----------|------|
| #2705 | Bypass OneCLI gateway for native credential proxy | June 2026 (61 days) | **High** — system-service deployments affected |
| #3149 | `--rw` flag for `groups config add-mount` | July 2026 (9 days) | **Low** — CLI convenience |
| #3190 | Tavily MCP tool skill | August 2026 (2 days) | **Low** — feature request, not urgent |
| #3186 | Host seams for skill-owned capabilities | August 2026 (3 days) | **Medium** — architectural refactor |
| #3193 | Update Chat SDK for rich Telegram messages | August 2026 (1 day) | **Medium** — pending merge |

**Maintainer attention needed:** PR #2705 has been open for two months and addresses a real deployment failure mode. Prioritizing this merge would resolve a long-standing pain point for system-service users.

---

*Data source: GitHub API — nanocoai/nanoclaw, as of 2026-08-07.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-07

## 1. Today's Overview

IronClaw is in a high-velocity phase following the release of v1.1.0, the first stable version since 1.0.0. Activity is intense: 50 issues and 50 PRs were updated in the last 24 hours, with 23 issues closed and 17 PRs merged — indicating strong contributor momentum. The project is balancing a major release rollout (MCP extensions, durable attachments, Slac integration) with a substantial open bug backlog, particularly around the Reborn routine engine, Slack delivery targets, and QA-reported Qwen3.6 rendering issues. Overall health is **active but strained** — release momentum is strong, yet stability gaps persist in production paths.

## 2. Releases

**v1.1.0** (2026-08-06) — `nearai/ironclaw`
First stable release since 1.0.0, promoting `1.1.0-rc.1` with the following fixes and additions:
- **Extension reach**: Register arbitrary hosted MCP servers
- **IronHub deep links**: Install extensions directly from deep links
- **Durable file attachments**: Files that persist and cross channels
- **Slac integration**: New messaging channel support

No breaking changes announced. Migration notes are minimal — users upgrading from `1.1.0-rc.1` should review the full changelog at the repository releases page.

## 3. Project Progress

**Merged/Closed PRs today:**

| PR | Summary |
|----|---------|
| [#7235](https://github.com/nearai/ironclaw/pull/7235) | Operator inspection API + live diagnostics stream (merged) |
| [#7303](https://github.com/nearai/ironclaw/pull/7303) | Fix: install `curl` in Docker so orchestrator healthchecks pass |
| [#7289](https://github.com/nearai/ironclaw/pull/7289) | Fix: sanitize libSQL FTS queries for natural-language recall |
| [#7259](https://github.com/nearai/ironclaw/pull/7259) | Docs: enforce publication boundary, consolidate internal docs under `docs/internal/` |

**Key advances in progress:**
- **Inspector tooling** — Four large PRs (#7239, #7236, #7277, #7235) are building out a comprehensive operator inspection layer: prompt capture, debug panel shell, model-call statistics, and live event streaming. This signals a strong investment in observability.
- **Slack delivery fix** — PR #7300 restores personal DM delivery and standardized canaries, directly addressing long-standing Slack routing bugs.
- **OAuth UX improvements** — PR #7304 reorders login card to surface OAuth providers above gateway token entry.
- **WASM Nostr host functions** — PR #7184 adds `nostr-sign-event` for signed event creation inside the WASM sandbox.
- **Sandbox profiles** — PR #7214 introduces explicit Docker and Railway user-sandbox profiles.

## 4. Community Hot Topics

**Top issues by comment activity (all open):**

1. **[Issue #5553](https://github.com/nearai/ironclaw/issues/5553)** — *Approval notifications disappear instead of remaining in notification history* (4 comments)
   Users need reliable approval UX for automated workflows. Disappearing notifications break trust in the agent's reliability.

2. **[Issue #5702](https://github.com/nearai/ironclaw/issues/5702)** — *GitHub issue search/create fails with HTTP 403* (4 comments)
   GitHub integration is a core capability; 403 errors block a major user workflow. Suggests token/scope misconfiguration or a regression in auth handling.

3. **[Issue #5522](https://github.com/nearai/ironclaw/issues/5522)** — *Reborn routine fails reading Slack DMs — missing capability + retry loop* (3 comments)
   Points to a gap between capability registration and the Reborn agent loop's retry logic.

4. **[Issue #5834](https://github.com/nearai/ironclaw/issues/5834)** — *Slack disconnect request incorrectly rejected by agent* (3 comments)
   Users cannot manage their own integrations — a control/agency pain point.

5. **[Issue #5701](https://github.com/nearai/ironclaw/issues/5701)** — *Activity panel hides tool details and does not update during active run* (3 comments)
   Observability gap: users can't see what the agent is doing in real time.

**Underlying theme:** Users are hitting friction at the intersection of **integration reliability** (Slack, GitHub) and **observability** (notifications, activity panel). The Inspector PRs directly address the observability gap.

## 5. Bugs & Stability

**Ranked by severity (P1 > P2 > P3):**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **P1** | [#3533](https://github.com/nearai/ironclaw/issues/3533) (closed) | Telegram not auto-setup from UI | ✅ Closed |
| **P1** | [#5456](https://github.com/nearai/ironclaw/issues/5456) | Routine runs fail with runner lease expiration (90s threshold too aggressive) | ❌ Open |
| **P1** | [#5877](https://github.com/nearai/ironclaw/issues/5877) (closed) | Slack notification delivered to wrong user | ✅ Closed |
| **P2** | [#5553](https://github.com/nearai/ironclaw/issues/5553) | Approval notifications disappear | ❌ Open |
| **P2** | [#5702](https://github.com/nearai/ironclaw/issues/5702) | GitHub integration returns HTTP 403 | ❌ Open |
| **P2** | [#5836](https://github.com/nearai/ironclaw/issues/5836) | Routine fails every run with "No thread attached" | ❌ Open |
| **P2** | [#5508](https://github.com/nearai/ironclaw/issues/5508) | Slack delivery target not found despite active connection | ❌ Open |
| **P2** | [#5552](https://github.com/nearai/ironclaw/issues/5552) | Generic "invalid result" after multiple tool failures | ❌ Open |
| **P2** | [#5776](https://github.com/nearai/ironclaw/issues/5776) | Long-output prompts cause timeouts, degraded to "invalid result" | ❌ Open |
| **P2** | [#5838](https://github.com/nearai/ironclaw/issues/5838) (closed) | Context compaction error after successful tool execution | ✅ Closed |
| **P2** | Multiple Qwen3.6 QA bugs (#4339–#4344) | Model-specific rendering/auth/capability failures | ❌ Open |
| **P3** | [#5504](https://github.com/nearai/ironclaw/issues/5504) (closed) | Routine creation hangs indefinitely | ✅ Closed |
| **P3** | [#5507](https://github.com/nearai/ironclaw/issues/5507) (closed) | Failed routine run shows "No thread attached", blocks debugging | ✅ Closed |
| **P3** | [#5510](https://github.com/nearai/ironclaw/issues/5510) | Cannot delete old routines | ❌ Open |
| **P3** | [#5707](https://github.com/nearai/ironclaw/issues/5707) | Routine creation exposes internal implementation details | ❌ Open |

**Critical pattern:** The **"invalid result" / "No thread attached"** error cluster (#5552, #5776, #5836, #5507) points to systemic issues in the Reborn routine engine's error handling and thread lifecycle management. This is the most impactful bug family and should be prioritized.

## 6. Feature Requests & Roadmap Signals

- **Operator inspection & observability** — Four large PRs (#7235, #7236, #7239, #7277) are being built out in parallel. This is clearly a roadmap priority for the next release cycle.
- **Channel delivery tool** — PR #7157 implements a two-lane model (conversation lifecycle + notification channels) per an approved design spec. Expect this in a future release.
- **Nostr WASM host functions** — PR #7184 adds signed-event creation, extending the WASM sandbox beyond its current capabilities.
- **Sandbox profiles** — PR #7214 adds explicit Docker and Railway profiles, improving deployment predictability.
- **Private MCP registration** — PR #7253 keeps custom MCP registrations definition-only and user-scoped, addressing a privacy/security concern.

**Prediction:** The next minor release (v1.2.0) will likely ship the Inspector tooling, the channel delivery tool, and improved sandbox profiles as headline features.

## 7. User Feedback Summary

**Pain points (high signal):**
- **Notification reliability** — Approval and Slack notifications disappearing or going to the wrong user (#5553, #5877) erodes trust in automated workflows.
- **Routine engine fragility** — "No thread attached" (#5836), lease expiration (#5456), and generic "invalid result" errors (#5552, #5776) make scheduled routines unreliable in production.
- **Slack integration instability** — Three separate open issues (#5522, #5834, #5508) all relate to Slack connectivity, targeting, and disconnect flows. This is a concentrated area of dissatisfaction.
- **GitHub integration broken** — HTTP 403 errors on issue search/create (#5702) block a key developer workflow.
- **UI lag and feedback** — Activity panel not updating in real time (#5701), chat creation latency scaling with history (#5509), and raw thread IDs showing during latency (#5706) all degrade the user experience.
- **Cannot manage routines** — No working deletion mechanism (#5510) leaves users with stale configurations they can't clean up.

**Satisfaction signals:**
- The v1.1.0 release is being well-received with active extension registration and MCP integration — users are engaging with the new capabilities.
- Docker healthcheck fix (#7303) resolved a staging infrastructure issue that was blocking deployments.

## 8. Backlog Watch

**Long-open, high-impact items needing maintainer attention:**

1. [#5456](https://github.com/nearai/ironclaw/issues/5456) — *Routine lease expiration* (P1, open since 2026-06-30). The 90-second inactivity threshold is too aggressive for multi-tool routines. No fix PR in sight.
2. [#5836](https://github.com/nearai/ironclaw/issues/5836) — *"No thread attached" on routine runs* (P2, open since 2026-07-08). Systemic issue affecting scheduled routines with 0% success rate.
3. [#5553](https://github.com/nearai/ironclaw/issues/5553) — *Approval notifications disappear* (P2, open since 2026-07-02). Core UX trust issue.
4. [#5702](https://github.com/nearai/ironclaw/issues/5702) — *GitHub 403 errors* (P2, open since 2026-07-06). Blocks a primary integration.
5. [#5510](https://github.com/nearai/ironclaw/issues/5510) — *Cannot delete old routines* (P2, open since 2026-07-01). Missing basic lifecycle management.
6. [#4339–#4344](https://github.com/nearai/ironclaw/issues/4339) — *Qwen3.6 model-specific QA bugs* (P2, open since 2026-06-02). Six related issues spanning rendering, auth, MCP, and capability validation — likely a common root cause.
7. [#7259](https://github.com/nearai/ironclaw/pull/7259) — *Docs publication leak* was merged but highlights a governance gap that may need follow-up.

**Overall assessment:** IronClaw v1.1.0 is a solid release with meaningful feature expansion, but the Reborn routine engine and integration layer (Slack, GitHub) have concentrated bug clusters that need focused stabilization before the next release. The Inspector observability work is a strong signal of maturing project infrastructure.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-07

---

## 1. Today's Overview

LobsterAI shows moderate development activity on 2026-08-07, with 6 open issues and 4 PRs (2 merged, 2 open) updated in the last 24 hours. No new releases were published. The project appears to be in a steady-state maintenance phase: two bug-fix PRs from contributor `fisherdaddy` were merged today, addressing config handling and Windows installer robustness, while the issue queue continues to accumulate user-facing concerns around UX refinement, provider compatibility, and architectural questions. No critical or blocking bugs were reported today.

---

## 2. Releases

No new releases were published on this date.

---

## 3. Project Progress

**Merged / Closed PRs (2):**

- **[PR #2445](https://github.com/netease-youdao/LobsterAI/pull/2445)** — `fix(openclaw): strip plugin-index-managed keys from config.set` — Ensures that plugin-index-managed configuration keys are properly removed before writing settings, preventing stale or duplicate entries from polluting the config layer. Area: `main`, `openclaw`.
- **[PR #2446](https://github.com/netease-youdao/LobsterAI/pull/2446)** — `fix(win-installer): rescue null watchdog exit code via extractor` — Fixes a Windows installer edge case where a null watchdog exit code could cause silent failures during installation. Area: `docs`, `windows`.

Both PRs were authored by `fisherdaddy` and closed the same day they were opened, indicating responsive triage of targeted bug fixes.

---

## 4. Community Hot Topics

| Issue / PR | Author | Updates | Comments | Link |
|---|---|---|---|---|
| [#2444](https://github.com/netease-youdao/LobsterAI/issues/2444) — 输入框编辑模式 | PYUDNG | 2026-08-07 | 0 | [Link](https://github.com/netease-youdao/LobsterAI/issues/2444) |
| [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443) — 模型ID含斜杠的自定义Provider | tuskinekinase | 2026-08-06 | 0 | [Link](https://github.com/netease-youdao/LobsterAI/issues/2443) |
| [#2447](https://github.com/netease-youdao/LobsterAI/issues/2447) — 执行没有出结果 | jzNccc | 2026-08-07 | 1 | [Link](https://github.com/netease-youdao/LobsterAI/issues/2447) |
| [#1196](https://github.com/netease-youdao/LobsterAI/issues/1196) — 强制建立系统文件 | daiqi1235 | 2026-08-06 | 1 | [Link](https://github.com/netease-youdao/LobsterAI/issues/1196) |
| [#1198](https://github.com/netease-youdao/LobsterAI/issues/1198) — 网关重启状态不明 | Cathylkx | 2026-08-06 | 1 | [Link](https://github.com/netease-youdao/LobsterAI/issues/1198) |

**Analysis:**

- **Issue #2444** (input box edit mode) reflects a recurring UX pain point: long prompt composition is cumbersome with the current Shift+Enter newline convention. Users are requesting either a configurable default or a toggleable "edit mode."
- **Issue #2443** highlights a real compatibility gap with OpenAI-compatible providers (e.g., SiliconFlow) whose model IDs contain slashes — a non-trivial parsing bug affecting a growing segment of the user base.
- **Issue #2447** (silent execution failure) suggests potential reliability concerns in the execution pipeline, though limited detail is available.
- **Issues #1196 / #1198** are stale but remain relevant — both concern operational transparency (file management noise, gateway restart status visibility).

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|---|---|---|---|
| **Medium** | [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443) | Model IDs containing slashes (e.g., `deepseek-ai/DeepSeek-V4-Flash`) are not selectable in the UI for custom OpenAI-compatible providers. Affects all slash-named providers like SiliconFlow. | No |
| **Medium** | [#2447](https://github.com/netease-youdao/LobsterAI/issues/2447) | Agent execution produces no output and no error message — silent failure mode. | No |
| **Medium** | [#1198](https://github.com/netease-youdao/LobsterAI/issues/1198) | Gateway restart progress bar disappears mid-way; subsequent conversations report "model unavailable" with no clear status feedback. | No |
| **Low** | [#2442](https://github.com/netease-youdao/LobsterAI/issues/2442) | PowerShell version remains at 5.1 instead of using 7.4 — explained as a Node.js default behavior on Windows, not a bug per se. | N/A (answered) |

**Note:** PR #2446 partially addresses Windows installer stability but does not resolve any of the above user-facing bugs.

---

## 6. Feature Requests & Roadmap Signals

| PR / Issue | Author | Description | Likelihood of Adoption |
|---|---|---|---|
| [#1199](https://github.com/netease-youdao/LobsterAI/pull/1199) — 上下文窗口与Token设置 | leedalei | Per-model `contextWindow` and `maxTokens` settings, persisted and surfaced in the model list. Propagates to Cowork/OpenClaw config. | **High** — well-scoped, addresses a clear gap in model configuration granularity |
| [#1197](https://github.com/netease-youdao/LobsterAI/pull/1197) — Agent管理页面交互优化 | leefinder | Shorter interaction path for agent deletion; improved sidebar navigation. Blocked by merge conflicts with main. | **Medium** — UX improvement but requires rebase and conflict resolution |
| [#2444](https://github.com/netease-youdao/LobsterAI/issues/2444) — 输入框编辑模式 | PYUDNG | Toggle or configurable Enter vs. Ctrl+Enter behavior for newline vs. send; optional WYSIWYG markdown editor. | **Medium-High** — frequently requested pattern in chat UIs; low implementation risk |

---

## 7. User Feedback Summary

**Satisfaction drivers:**
- Users appreciate the ability to configure custom OpenAI-compatible providers, but hit friction when model IDs contain special characters (slashes).
- The per-model token/context settings proposed in PR #1199 would directly address power-user needs for fine-grained control.
- Windows installer improvements (PR #2446) show responsiveness to platform-specific reliability concerns.

**Pain points:**
- **Silent failures** (Issue #2447) erode trust — users need clearer error feedback when executions produce no output.
- **Gateway restart opacity** (Issue #1198) leaves users in the dark about service status, causing confusion and repeated failed requests.
- **Prompt input UX** (Issue #2444) is a consistent complaint: the Shift+Enter convention is unintuitive for long-form input, and no alternative has been offered.
- **File system noise** (Issue #1196):强制生成的6个系统文件 in every working directory are seen as clutter; users prefer a centralized or hidden configuration approach.

---

## 8. Backlog Watch

| Issue / PR | Age | Priority | Reason |
|---|---|---|---|
| [#1196](https://github.com/netease-youdao/LobsterAI/issues/1196) — 强制建立系统文件 | ~4 months (stale) | **High** | Repeated user complaint about workspace clutter; simple config redesign could resolve |
| [#1197](https://github.com/netease-youdao/LobsterAI/pull/1197) — Agent管理页面交互优化 | ~4 months (stale, conflict) | **Medium** | UX PR blocked by merge conflicts; needs maintainer triage to unblock |
| [#1198](https://github.com/netease-youdao/LobsterAI/issues/1198) — 网关重启状态不明 | ~4 months (stale) | **Medium** | Operational transparency gap affecting user trust during maintenance |
| [#1199](https://github.com/netease-youdao/LobsterAI/pull/1199) — 上下文窗口与Token设置 | ~4 months (stale) | **High** | Valuable feature PR that appears stalled; deserves re-review |
| [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443) — 斜杠模型ID | ~1 day | **High** | Active compatibility bug affecting multiple providers; likely quick fix |

**Overall Project Health:** 🟡 **Stable but stagnant on backlog.** Two targeted bug fixes were merged today, showing active maintenance capacity. However, 4 stale items from April remain unresolved, and several high-impact user-facing bugs lack fixes. The project would benefit from a backlog triage pass to clear the stale queue and prioritize the slash-ID provider bug and silent-failure debugging.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026‑08‑07

## 1. Today’s Overview
CoPaw showed **very high activity** over the last 24 hours: 28 issues updated (14 open, 14 closed) and 50 pull‑requests touched (20 open, 30 merged/closed). No new releases were published, but the team closed a substantial batch of bugs and merged several feature and documentation PRs. The project’s health remains strong—contributors are actively addressing stability gaps, extending the memory/embedding subsystem, and improving channel reliability.

## 2. Releases
*No new releases were published in the last 24 h.*

## 3. Project Progress
### Merged/Closed PRs (selected)
| PR | Title | Summary |
|---|---|---|
| [#6759](https://github.com/agentscope-ai/CoPaw/pull/6759) | Preserve tool‑call extra content across context lifecycle | Keeps provider‑specific metadata (e.g., Gemini thought signatures) through session restoration and compression. |
| [#6337](https://github.com/agentscope-ai/CoPaw/pull/6337) | Expose AG‑UI protocol via `/protocol/agui/chat` endpoint | Adds a dedicated SSE endpoint that streams agent responses as standard AG‑UI protocol events. |
| [#6525](https://github.com/agentscope-ai/CoPaw/pull/6525) | User‑context transparent penetration (Chat API → Agent → Tool → MCP → SKILL CLI) | Propagates `user_id`, `user_name`, channel and custom metadata through the entire call chain without LLM visibility. |
| [#6651](https://github.com/agentscope-ai/CoPaw/pull/6651) | File/folder management REST API for the Files page | Supplies missing CRUD endpoints (delete, rename, create directory, upload/download) while reusing the existing `FileGuard` security model. |
| [#6605](https://github.com/agentscope-ai/CoPaw/pull/6605) | Return typed tagged tool calls | Rehydrates tool calls extracted from thinking/text tags into `ToolCallBlock` objects, preserving raw JSON arguments. |
| [#6664](https://github.com/agentscope-ai/CoPaw/pull/6664) | Degrade gracefully without Codex CLI | Allows the harness to start even when the optional Codex CLI is absent. |
| [#6741](https://github.com/agentscope-ai/CoPaw/pull/6741) | Improve ReMe configuration and embedding lifecycle | Adds a unified embedding‑model factory (OpenAI‑compatible, DashScope, Gemini, Ollama) with pre‑save connectivity tests and real‑time status checks. |
| [#6751](https://github.com/agentscope-ai/CoPaw/pull/6751) | Blog post: Scroll executable memory report | Documents the new scrollable memory feature. |

### Key closed issues
* **#6684** – Added retry functionality for channels (Matrix).  
* **#6588** – Fixed `spawn_subagent` mis‑treating empty `batch` placeholders as batch mode.  
* **#6601** – Addressed empty‑response silence in long sessions.  
* **#6667** – Worked around DeepSeek thinking‑mode `reasoning_content` loss.  
* **#6700** – Closed after discussion; large tool‑output truncation/pagination still open.  
* **#6476** – Resolved Matrix E2E‑encryption dependency issue.  

## 4. Community Hot Topics
| Issue | Comments | Core Need |
|---|---|---|
| [#6684](https://github.com/agentscope-ai/CoPaw/issues/6684) | 8 | **Channel reliability** – Users need automatic retry/health‑checks for self‑hosted Matrix connections that drop after service restarts. |
| [#6588](https://github.com/agentscope-ai/CoPaw/issues/6588) | 6 | **Batch‑mode detection** – Empty `batch` placeholders from Responses‑compatible providers should not trigger batch mode in single‑task calls. |
| [#6601](https://github.com/agentscope-ai/CoPaw/issues/6601) | 5 | **Silent failures** – Long‑context sessions that reach the model’s window limit should raise an explicit error instead of returning empty responses. |
| [#6667](https://github.com/agentscope-ai/CoPaw/issues/6667) | 5 | **Thinking‑mode compatibility** – Models that require `reasoning_content` to be relayed (e.g., DeepSeek) break when tool‑call history is present. |
| [#6768](https://github.com/agentscope-ai/CoPaw/issues/6768) | 1 | **Infinite‑loop guard** – Multi‑step tasks can stall the agent for hours; users need a robust timeout/exit mechanism. |

**Underlying trend:** The community is pushing for stronger fault tolerance (retry, explicit errors, loop detection) and better integration with thinking‑mode providers and external protocols (AG‑UI, MCP).

## 5. Bugs & Stability
### Open bug‑severity issues (ranked)
| Issue | Severity | Description | Fix PR? |
|---|---|---|---|
| [#6768](https://github.com/agentscope-ai/CoPaw/issues/6768) | **High** | Agent enters an infinite loop after a multi‑step task; session blocked for hours. | – |
| [#6775](https://github.com/agentscope-ai/CoPaw/issues/6775) | **High** | Malware Bytes flags the Windows Desktop binary as a Trojan Loader (likely false positive). | – |
| [#6698](https://github.com/agentscope-ai/CoPaw/issues/6698) | **High** | Browser SDK’s Playwright driver crashes permanently; every `open()` call fails with `WireProtocolError: Target crashed`. | [#6776](https://github.com/agentscope-ai/CoPaw/pull/6776) (self‑heal) |
| [#6732](https://github.com/agentscope-ai/CoPaw/issues/6732) | **Medium** | MCP tools become unresponsive after a few hours; Docker container restart temporarily restores them. | – |
| [#6756](https://github.com/agentscope-ai/CoPaw/issues/6756) | **Medium** | `run_tool_batch` fails with `No toolkit available in current context` even for simple batches. | – |
| [#6755](https://github.com/agentscope-ai/CoPaw/issues/6755) | **Medium** | Cross‑day sessions cause the model to misjudge the current date/weekday, leading to wrong schedule entries. | – |
| [#6773](https://github.com/agentscope-ai/CoPaw/issues/6773) | **Medium** | On Linux, doom‑loop/rubric gates never activate in `/goal` or `/mission` modes (`in_loop_modes` is a no‑op). | [#6774](https://github.com/agentscope-ai/CoPaw/pull/6774) |

**Regression watch:** Several issues relate to the agentscope 2.0.4.post1 compatibility layer (e.g., #6612, #6619). Maintainers should monitor these as the platform moves forward.

## 6. Feature Requests & Roadmap Signals
| Issue/PR | Type | Description | Likelihood for next release |
|---|---|---|---|
| [#6724](https://github.com/agentscope-ai/CoPaw/issues/6724) | Enhancement | Configurable MCP tool‑call timeout (per‑client + call‑level guard). | **High** – direct request from an active user; no timeout currently exists. |
| [#6770](https://github.com/agentscope-ai/CoPaw/issues/6770) | Enhancement | Make user Chrome‑tab lifetime configurable across response cycles. | **Medium** – niche but improves session management. |
| [#6728](https://github.com/agentscope-ai/CoPaw/issues/6728) | Enhancement | WeChat approval prompts should support Chinese approve/deny actions. | **Medium** – localization improvement. |
| [#6765](https://github.com/agentscope-ai/CoPaw/issues/6765) | Enhancement | Add other EU languages (e.g., Hungarian) to the UI. | **Low–Medium** – broadens international reach. |
| [#6651](https://github.com/agentscope-ai/CoPaw/pull/6651) | Feature (merged) | Full file/folder management REST API for the Files page. | Already merged; will appear in the next stable build. |
| [#6337](https://github.com/agentscope-ai/CoPaw/pull/6337) | Feature (merged) | AG‑UI protocol endpoint. | Already merged; expands external integration surface. |

**Roadmap inference:** The project is clearly investing in **reliability** (retry, timeouts, loop detection) and **extensibility** (AG‑UI, MCP improvements, file management). Expect the next version to ship robust timeout configuration for MCP and a self‑healing browser driver.

## 7. User Feedback Summary
**Pain points**
* **Channel fragility** – Self‑hosted Matrix connections drop after service restarts; users manually re‑save channel config each time.  
* **Silent failures in long sessions** – When the context window is approached, models may return empty responses and QwenPaw does not raise an error.  
* **Unbounded tool output** – A single tool call that produces hundreds of MB can freeze the web console and blow up the context window.  
* **MCP tool‑name validation** – Tool names starting with a hyphen (e.g., `-MCP__get_consensus_forecast`) violate OpenAI function‑calling specs and cause 400 errors on strict providers.  
* **Date/weekday confusion** – Cross‑day sessions cause the agent to misinterpret “today,” leading to incorrect scheduling.  
* **Desktop malware false positive** – Malware Bytes flags the Windows binary, creating trust issues for new users.

**Positive signals**
* Users appreciate the rapid addition of embedding‑model configuration guides and the new AG‑UI endpoint.  
* The community is actively contributing fixes (e.g., the Playwright self‑heal PR, the tool‑call extra‑content preservation).  
* The project responds quickly to high‑visibility issues (many closed within days of filing).

**Satisfaction/dissatisfaction:** Overall sentiment is **constructive**—users report real blockers but also welcome the team’s responsiveness. The biggest dissatisfaction stems from stability gaps in long‑running or multi‑step scenarios.

## 8. Backlog Watch
| Issue/PR | Age | Comments | Why it needs attention |
|---|---|---|---|
| [#6773](https://github.com/agentscope-ai/CoPaw/issues/6773) | 1 day | 0 | Safety gates (`doom_loop_modes`, `rubric_gates`) are completely non‑functional on Linux; a fix PR exists but is unreviewed. |
| [#6761](https://github.com/agentscope-ai/CoPaw/issues/6761) | 1 day | 1 | MCP spec statelessness (2026‑07‑28) may break legacy clients; needs a maintainer response on compatibility. |
| [#6765](https://github.com/agentscope-ai/CoPaw/issues/6765) | 1 day | 1 | Non‑English UI request; low priority but impacts international users. |
| [#6755](https://github.com/agentscope-ai/CoPaw/issues/6755) | 1 day | 1 | Date‑judgment bug affects scheduling‑oriented agents; no fix yet. |
| [#6724](https://github.com/agentscope-ai/CoPaw/issues/6724) | 2 days | 1 | MCP timeout is a hard requirement for production use; enhancement request is open. |
| [#6768](https://github.com/agentscope-ai/CoPaw/issues/6768) | 1 day | 1 | Infinite‑loop bug that can block sessions for hours; high severity. |
| [#6775](https://github.com/agentscope-ai/CoPaw/issues/6775) | <1 day | 1 | Malware false positive undermines trust; requires a security‑team clarification. |
| [#6557](https://github.com/agentscope-ai/CoPaw/issues/6557) | 9 days | 2 (closed) | MCP tool‑name validation fix was merged, but similar issues may recur with other providers. |

**Action recommendation:** Prioritize reviewing the open fix PRs (#6774, #6776) and providing a status update on the MCP‑statelessness compatibility question (#6761). The infinite‑loop and date‑judgment bugs should be addressed in the next patch to prevent user data loss.

---
*Digest generated from GitHub data fetched on 2026‑08‑07. All links point to the `agentscope-ai/CoPaw` repository.*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-07

## 1. Today's Overview

ZeroClaw saw elevated activity today with 36 issues and 50 PRs touched in the last 24 hours. The project is in a stabilization phase leading up to v0.9.0, with active RFC ratification, security hardening, and SOP tooling improvements underway. No new releases were published, but several critical bug fixes and security patches are in review. The maintainer decision queue (#8692) and governance RFCs (#6808, #9496) indicate a push toward more structured project operations.

## 2. Releases

No new releases were published today. The current tracked version is **0.8.4**.

## 3. Project Progress

**Merged/Closed today:**

- **#9456** — CI now validates `Containerfile` changes in PRs, closing a gap where container-only changes bypassed source-build checks.
- **#9172** — ZeroCode slash commands now use a single command descriptor source, unifying autocomplete, token recognition, and shared command identity.
- **#8950** — Fixed Telegram `setMyCommands` rejection when tools+skills+builtins exceed 100 entries; command menu now registers correctly.
- **#8615** — Resolved the `compatible` provider's unconditional `<think>` tag stripping that silently deleted response content.
- **#9741** — CI container job now validates the canonical all-features image, preventing MSRV lane drift.
- **#9657** — Fixed the `protected-literal` checker incorrectly treating generic "Signal" as a channel name.
- **#9763** — Resolved a flaky test (`onepassword_reference_load_does_not_block_runtime_worker`) that failed under CI load.

**Notable open PRs advancing features:**

- **#9535** — Context compaction now anchored to model window ratio instead of absolute budgets.
- **#9324** — A2A outbound client (Phase 1): four `a2a_*` tools and shared v1.0 wire model.
- **#9352** — Cross-turn conversation correlation added to OpenTelemetry export.
- **#9182** — PowerShell now supported as the native shell on Windows.
- **#9571** — WATI channel removal in progress (P0, XL size).

## 4. Community Hot Topics

| Issue/PR | Topic | Comments | Link |
|----------|-------|----------|------|
| **#6808** | Work Lanes, Board Automation, Label Cleanup RFC | 19 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| **#8692** | Maintainer Decision Queue for RFCs | 11 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| **#9106** | A2A Outbound Client (A2ATool) RFC | 11 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) |
| **#9246** | Preserve Todo tracker config during ZeroCode migration RFC | 11 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9246) |
| **#6954** | Provenance & conversation binding for internally initiated turns RFC | 10 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) |
| **#7100** | Per-model capability & context-window config RFC | 8 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| **#9397** | WhatsApp `allowed_groups` empty-list security behavior RFC | 7 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) |

**Analysis:** The top-discussed topics reveal two dominant community needs: (1) **inter-agent collaboration** — the A2A outbound client RFC (#9106) and conversation-binding work (#6954) show strong demand for multi-agent workflows; (2) **governance maturity** — multiple RFCs (#6808, #8692, #9496) focus on streamlining maintainer processes, suggesting the project is scaling and needs better coordination machinery.

## 5. Bugs & Stability

**Reported/Fixed today (ranked by severity):**

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| 🔴 **High** | #9786 | Malformed `SOP.toml` silently dropped — `sop validate` reports success | — |
| 🔴 **High** | #9779 | `sops_dir` documented default not honoured; SOPs silently never load | — |
| 🔴 **High** | #9780 | Cron-triggered SOPs cannot perform network work (no HTTP capability) | — |
| 🔴 **High** | #9770 | `cron update` silently discards changes to declarative jobs | — |
| 🔴 **High** | #9783 | `finish_run` accepts failure reason but discards it — no cause recorded | — |
| 🟠 **High** | #9799 | Ephemeral daemon spins at 100%+ CPU with repeated DB handles after ~17h | — |
| 🟠 **High** | #9800 | SIGTERM leaves ZeroCode terminal in raw/mouse-tracking mode | — |
| 🟠 **High** | #9328 | `vi_verify` evaluates constraints without verifying credential chain | — |
| 🟡 **Medium** | #8720 | Bedrock Nova 2 Lite caching error; no config to disable `cachePoint` | — |
| 🟡 **Low** | #9672 | All three `cron add` CLI help examples are broken | Merged (#9672) |

**Security-related closed today:**
- **#7947** — `execute_pipeline` bypassing per-agent tool gating (confused deputy) — resolved.
- **#1** — XOR cipher for stored secrets (CRITICAL) — resolved.

**Security fixes in review:**
- **#8826** — SSRF guard on `image_gen` download URL.
- **#9435** — Scrubs Gemini API key from sanitized error text.
- **#9438** — Hardens `/api/pair` against lockout bypass.

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for v0.9.0 |
|---------|--------|----------------------|
| A2A outbound client (`a2a_*` tools) | #9106 / #9324 | **High** — Phase 1 PR is advanced, RFC accepted |
| Per-model context-window & capability config | #7100 | **High** — RFC accepted, p1 priority |
| WhatsApp empty `allowed_groups` = deny-all | #9397 | **High** — security-critical, p1, in-progress |
| Cross-turn OTel conversation correlation | #9352 | **Medium-High** — PR open, architecture RFC referenced |
| PowerShell native shell on Windows | #9182 | **Medium** — PR open, p2 |
| Kimi Code provider support | #657 | **Low** — Closed; may be addressed via compatible provider |
| Single-message progress drafts (Matrix) | #8443 | **Medium** — PR open, p2 |
| Anthropic stored OAuth profiles | #9420 | **Medium** — PR open, p2 |

**Roadmap signal:** The v0.9.0 tracker (#7432) is the central coordination point for auth, security, gateway, and breaking-change work. The A2A outbound client and per-model config are the strongest candidates for inclusion.

## 7. User Feedback Summary

**Pain points expressed:**

- **SOP tooling is fragile** — Multiple users (#9779, #9780, #9783, #9786) report that cron-triggered SOPs silently fail or cannot perform network work. The documentation promises watch-loop capability but the runtime lacks HTTP access for cron SOPs.
- **Configuration defaults are misleading** — The `sops_dir` default is documented but not honored by the daemon (#9779), causing silent failures with no logs.
- **CLI UX gaps** — `cron add` help examples are broken (#9672), and `cron update` silently discards changes (#9770), eroding operator trust.
- **Security regressions** — The compatible provider silently strips `<think>` content (#8615) and the Gemini provider leaks API keys in errors (#9435) are user-reported issues that cause data loss or credential exposure.
- **Terminal state on exit** — ZeroCode SIGTERM leaves mouse-tracking enabled (#9800), requiring manual terminal reset.

**Satisfaction signals:** The WATI channel removal (#9571) and Telegram command-menu fix (#8950) address long-standing pain points. The Anthropic OAuth support (#9420) and Matrix progress drafts (#8443) show responsiveness to user requests.

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|----------------------|
| **#6808** — Work Lanes RFC | 79 days | RFC ratification deferred; blocks board automation rollout. Author: Audacity88. |
| **#9496** — Streamline RFC process | 10 days | Proposes reducing discussion period and voting friction; critical for project velocity. |
| **#9530** — Risk precedence for test-only changes | 9 days | Conflicting maintainer docs; needs resolution before v0.9.0 freeze. |
| **#7432** — v0.9.0 security/gateway tracker | 59 days | Central coordination hub; multiple blocking prereqs unresolved. |
| **#9799** — Ephemeral daemon CPU spin | 0 days | New high-severity regression; 140-177% CPU after ~17h with repeated DB handles. |
| **#9786** — Malformed SOP.toml silent drop | 1 day | New high-severity bug; no diagnostic for invalid SOP config. |
| **#9779** — `sops_dir` default not honored | 1 day | New high-severity bug; SOP engine never loads for operators using documented defaults. |

**Recommended immediate attention:** The SOP subsystem bugs (#9779, #9780, #9783, #9786) form a cluster of interrelated issues that undermine a core ZeroClaw feature. The ephemeral daemon CPU leak (#9799) also warrants urgent investigation before it impacts production deployments.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*