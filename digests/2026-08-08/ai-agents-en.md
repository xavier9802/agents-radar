# OpenClaw Ecosystem Digest 2026-08-08

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-08 02:02 UTC

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

# OpenClaw Project Digest — August 8, 2026

## 1. Today's Overview

OpenClaw is experiencing **extremely high activity** with 500 issues and 500 pull requests updated in the last 24 hours. The project is in a critical stability phase following the 2026.7.2 release, with significant focus on session state management, gateway reliability, and memory leaks. There are no new releases today, but 92 PRs were merged/closed, indicating active maintenance. The issue closure rate (33 closed out of 500 updated) is modest, suggesting many critical bugs are still being investigated rather than resolved.

## 2. Releases

**No new releases today.** 

The project recently shipped **2026.7.2**, which has introduced several regressions (see Bugs & Stability section). Operators are advised to monitor issue #119263 regarding database migration failures from v14→v15.

## 3. Project Progress

**Merged/Closed PRs Today:**

- **#120410** - Test coverage for ClickClack native progress default [PR #120410](https://github.com/openclaw/openclaw/pull/120410)
- **#120362** - Session and Workboard managed-worktree lifecycle tests; symlinked state-dir lock fix [PR #120362](https://github.com/openclaw/openclaw/pull/120362)
- **#112808** - Experimental lifecycle Control UI added [PR #112808](https://github.com/openclaw/openclaw/pull/112808)
- **#120421** - CI release merge-tree lint sharding fix [PR #120421](https://github.com/openclaw/openclaw/pull/120421)
- **#120392** - CI release child metadata wait fix [PR #120392](https://github.com/openclaw/openclaw/pull/120392)
- **#120418** - UX producer aggregate status derivation [PR #120418](https://github.com/openclaw/openclaw/pull/120418)
- **#120084** - Fish Audio extension directory alignment [PR #120084](https://github.com/openclaw/openclaw/pull/120084)
- **#120420** - Queued steer message ordering fix across turn boundaries [PR #120420](https://github.com/openclaw/openclaw/pull/120420)
- **#120365** - Dead-export scan hardening for CI [PR #120365](https://github.com/openclaw/openclaw/pull/120365)
- **#120372** - Web UI connection form auth flow fix [PR #120372](https://github.com/openclaw/openclaw/pull/120372)
- **#115962** - Schema-v1 profile requirements implementation [PR #115962](https://github.com/openclaw/openclaw/pull/115962)
- **#120104** - Ingress claim settlement on turn failure [PR #120104](https://github.com/openclaw/openclaw/pull/120104)
- **#120395** - Windows target environment selection in CI [PR #120395](https://github.com/openclaw/openclaw/pull/120395)
- **#120381** - Attributed message avatar refresh fix [PR #120381](https://github.com/openclaw/openclaw/pull/120381)

**Key Advances:**
- **Control UI lifecycle management** - New experimental read-only Gateway projections for health monitoring
- **Message ordering guarantees** - Steer messages now delivered in arrival order across turn boundaries
- **Plugin lifecycle hardening** - Prevents uninstalled npm plugins from auto-reloading

## 4. Community Hot Topics

**Most Discussed Issues:**

1. **#116277** - DeepSeek v4 Flash silent reply failure (129 comments) [Issue #116277](https://github.com/openclaw/openclaw/issues/116277)
   - *Impact:* Critical message loss; generic fallback replaces failed replies
   - *Community need:* Reliable model fallback behavior and observability

2. **#116201** - Realtime voice work state retention (59 comments) [Issue #116201](https://github.com/openclaw/openclaw/issues/116201)
   - *Impact:* Resource leaks under bursty/stalled provider behavior
   - *Community need:* Hard ownership bounds for voice session resources

3. **#7707** - Memory Trust Tagging by Source (29 comments) [Issue #7707](https://github.com/openclaw/openclaw/issues/7707)
   - *Impact:* Security concern around memory poisoning attacks
   - *Community need:* Source-based trust metadata for memory entries

**Most Active PRs:**

- **#116382** - False branch-switch errors after background updates (large discussion) [PR #116382](https://github.com/openclaw/openclaw/pull/116382)
- **#104322** - Feishu transient message retry (awaiting author) [PR #104322](https://github.com/openclaw/openclaw/pull/104322)

## 5. Bugs & Stability

**P0 Critical Issues:**

| Issue | Summary | Fix PR |
|-------|---------|--------|
| **#91588** | Gateway memory leak: RSS grows from 350MB to 15.5GB, causing OOM crashes [Issue #91588](https://github.com/openclaw/openclaw/issues/91588) | None yet |
| **#101290** | CLI startup preflight corrupts live state DB (SQLite malformed) [Issue #101290](https://github.com/openclaw/openclaw/issues/101290) | None yet |
| **#119263** | Agent DB v14→v15 migration fails (`no such column: entry_valid`) [Issue #119263](https://github.com/openclaw/openclaw/issues/119263) | None yet |
| **#118772** | `totalTokens` inflation causes premature compaction at 4-8% context (data loss) [Issue #118772](https://github.com/openclaw/openclaw/issues/118772) | None yet |

**P1 High-Severity Issues:**

| Issue | Summary | Fix PR |
|-------|---------|--------|
| **#116277** | DeepSeek v4 Flash silent reply failure | None yet |
| **#116022** | Beta `/new` reuses stable session ID, can't recover tombstones | None yet |
| **#85030** | MCP tools not injected into subagent sessions | None yet |
| **#115700** | `chat.send` rejected with "thread switched branches" after model completes | [#116382](https://github.com/openclaw/openclaw/pull/116382) |
| **#119087** | Gateway cold start regressed 2.5x on 1-vCPU container | None yet |
| **#98435** | MCP loopback transport doesn't auto-reconnect after gateway restart | None yet |
| **#49876** | Cron sessions deliver hallucinated output on tool failure | None yet |

**Notable Regressions:**
- WebChat reasoning stream not working for Kimi Code & DeepSeek Reasoner (#88079)
- Gateway HTTP server listens but doesn't accept connections (v2026.7.1-beta.5) (#109145)
- Embedded agent runner session token inflation causing data loss (#118772)

## 6. Feature Requests & Roadmap Signals

**Active Enhancement Requests:**

1. **#7707** - Memory Trust Tagging by Source [Issue #7707](https://github.com/openclaw/openclaw/issues/7707)
   - *Likelihood:* Medium-high (security-focused, addresses poisoning attacks)

2. **#22438** - Tiered bootstrap file loading for progressive context control [Issue #22438](https://github.com/openclaw/openclaw/issues/22438)
   - *Likelihood:* Medium (addresses 20-30% context waste, #67419)

3. **#78308** - Channel-mediated approval for MCP tool calls (consent envelope) [Issue #78308](https://github.com/openclaw/openclaw/issues/78308)
   - *Likelihood:* High (extends existing `/approve` pattern to MCP)

4. **#45608** - Pre-reset agentic memory flush [Issue #45608](https://github.com/openclaw/openclaw/issues/45608)
   - *Likelihood:* Medium (improves session reset behavior)

5. **#35203** - Multi-Agent Collaboration: Capability Profiling + Shared Blackboard [Issue #35203](https://github.com/openclaw/openclaw/issues/35203)
   - *Likelihood:* Low-medium (complex RFC, long-term roadmap)

6. **#99583** - Intelligent Session Auto-Titling [Issue #99583](https://github.com/openclaw/openclaw/issues/99583)
   - *Likelihood:* Medium (UX improvement, existing LLM slug generator)

7. **#81061** - `before_route_inbound_message` hook for channel bridging [Issue #81061](https://github.com/openclaw/openclaw/issues/81061)
   - *Likelihood:* Medium (architecture enhancement)

**Predicted Next Version Features:**
- Memory trust/source tagging (#7707)
- MCP consent envelope (#78308)
- Tiered bootstrap loading (#22438/#67419)
- Session auto-titling (#99583)

## 7. User Feedback Summary

**Critical Pain Points:**

1. **Message Loss & Reliability**
   - DeepSeek v4 Flash silent failures (#116277) - users receiving generic fallbacks
   - LINE channel messages silently lost due to reply token expiry (#86012)
   - Feishu message drops on transient failures (#104322)

2. **Data Loss from Premature Compaction**
   - `totalTokens` inflation bug causing compaction at 4-8% context usage (#118772)
   - Users losing conversation history unexpectedly

3. **Gateway Stability**
   - Memory leak causing OOM crashes (#91588)
   - Cold start regression on constrained resources (#119087)
   - SQLite corruption during CLI operations (#101290)

4. **Multi-Agent Complexity**
   - MCP tools not propagating to subagents (#85030)
   - Parent sessions not waking after subagent yields (#120187)
   - Cron jobs hallucinating output on failures (#49876)

5. **Session Management**
   - Stale `expectedLeafEntryId` causing "thread switched branches" errors (#115700)
   - `/new` command not recovering from tombstoned bindings (#116022)

**Satisfaction Signals:**
- Positive: Fix for steer message ordering (#120420) addresses UX frustration
- Positive: Control UI lifecycle improvements (#112808)
- Negative: Persistent database migration issues (#119263)

## 8. Backlog Watch

**Long-Unanswered Critical Issues:**

| Issue | Age | Status | Risk |
|-------|-----|--------|------|
| **#7707** - Memory Trust Tagging | 6 months | Open, needs security review | High (security) |
| **#35203** - Multi-Agent Collaboration RFC | 5 months | Open, needs product decision | Medium |
| **#91588** - Gateway Memory Leak | 2 months | Open, no fix PR | **Critical** |
| **#49876** - Cron Hallucination | 5 months | Open, needs live repro | High (trust) |
| **#75380** - Unbounded log files | 3 months | Open, needs rotation policy | Medium |

**PRs Needing Maintainer Attention:**

1. **#104322** - Feishu retry fix (awaiting author, 28 days open) [PR #104322](https://github.com/openclaw/openclaw/pull/104322)
2. **#120104** - Ingress claim settlement (awaiting author) [PR #120104](https://github.com/openclaw/openclaw/pull/120104)
3. **#120240** - Ollama UTF-8 validation (awaiting author) [PR #120240](https://github.com/openclaw/openclaw/pull/120240)
4. **#120187** - Subagent wake parent fix (needs proof) [PR #120187](https://github.com/openclaw/openclaw/pull/120187)
5. **#118427** - Quiet-work floor for model_call recovery (needs proof) [PR #118427](https://github.com/openclaw/openclaw/pull/118427)

**Stale Issues Requiring Decision:**
- **#77598** - Live dev agent behavior tracking (3+ months, observational watch) [Issue #77598](https://github.com/openclaw/openclaw/issues/77598)
- **#99551** - Codex worker runaway hardening sprint [Issue #99551](https://github.com/openclaw/openclaw/issues/99551)

---

**Project Health Assessment:** OpenClaw is in a **volatile post-release stabilization phase**. The 2026.7.2 release introduced multiple P0 regressions affecting session state, database integrity, and memory management. Activity is high but focused on firefighting rather than feature development. The memory leak (#91588) and data loss issues (#118772, #101290) require urgent attention. Security-focused features like memory trust tagging are gaining traction but blocked by review backlog.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Analysis: Personal AI Agents (August 8, 2026)

## 1. Ecosystem Overview
The 2026 open-source personal AI agent landscape is defined by a shift from experimental prototyping to production-grade reliability and security hardening. After the release cycle of July 2026, the majority of active projects (OpenClaw, Hermes, IronClaw, ZeroClaw) are in critical stabilization phases, prioritizing session state integrity, memory persistence, and gateway stability over new feature development. The ecosystem is consolidating around standardized channel integrations (MCP, WebChat) and rigorous security boundaries, with a notable divergence between monolithic platforms (LobsterAI, CoPaw) and modular, Rust/Go-centric frameworks (ZeroClaw, IronClaw).

## 2. Activity Comparison

| Project | Issues Updated | PRs Updated | Release Status | Health Score | Primary Phase |
| :--- | :---: | :---: | :--- | :---: | :--- |
| **Hermes Agent** | 100 | 100 | None | 7/10 | Critical Sweeper (High Risk) |
| **ZeroClaw** | 100 | 100 | None | 6/10 | High-Velocity Security Fix |
| **OpenClaw** | 500 | 500 | None (Post-7.2) | 5/10 | Volatile Stabilization |
| **CoPaw** | 31 | 78 | v2.1.0-beta.2 | 6/10 | Beta Stabilization |
| **IronClaw** | 50 | 50 | None | 6/10 | Doc-Truth & Reliability |
| **NanoBot** | 9 | 21 | None | 8/10 | Active Maintenance |
| **LobsterAI** | 6 | 7 | v2026.8.7 | 7/10 | Rapid Iteration |
| **NanoClaw** | 1 | 10 | None | 7/10 | Moderate Refactoring |
| **PicoClaw** | 4 | 14 | None | 7/10 | Dependency Hygiene |
| **NullClaw** | 0 | 0 | None | 0/10 | Inactive |
| **Moltis** | 0 | 0 | None | 0/10 | Inactive |
| **ZeptoClaw** | 0 | 0 | None | 0/10 | Inactive |

*Health Score reflects stability of recent releases, bug-fix velocity, and community responsiveness.*

## 3. OpenClaw's Position
OpenClaw dominates in raw volume (500+ updates) but exhibits signs of **instability debt**. 
*   **Advantages:** It possesses the most mature session management architecture and the broadest channel integration list (Telegram, WhatsApp, Feishu, LINE, etc.). Its "Control UI" lifecycle management (#112808) sets a standard for operational observability that peers like NanoBot and IronClaw are still addressing.
*   **Technical Difference:** Unlike ZeroClaw’s Rust-centric, memory-safe approach or Hermes’ monolithic "god file" refactoring, OpenClaw relies on a complex TypeScript/Node.js stack that is currently suffering from memory leaks (#91588) and SQLite corruption (#101290). 
*   **Community:** OpenClaw has the largest user base, evidenced by high-comment issues (129 comments on DeepSeek failures), but this size amplifies the impact of its P0 regressions. Smaller projects like NanoBot and LobsterAI show higher satisfaction per capita due to faster, targeted fixes.

## 4. Shared Technical Focus Areas
Several critical requirements have emerged as ecosystem-wide priorities:

*   **Session State & Memory Reliability:** 
    *   *Projects:* OpenClaw, Hermes, IronClaw, ZeroClaw.
    *   *Need:* Cross-conversation memory persistence is failing across the board. IronClaw is introducing `MEMORY.md` (#7365), OpenClaw is fixing `totalTokens` inflation (#118772), and Hermes is addressing context compression drops (#79278).
*   **Security Hardening & Isolation:**
    *   *Projects:* ZeroClaw, NanoBot, IronClaw, CoPaw.
    *   *Need:* Strict session-level isolation is now a baseline requirement. ZeroClaw is enforcing tool allowlists (#9433) and fixing key leaks (#9813). NanoBot is debating moving history outside the agent workspace (#5278). IronClaw is scoping workspaces to tenants (#7214).
*   **Channel Stability & Fallbacks:**
    *   *Projects:* OpenClaw, NanoBot, PicoClaw, LobsterAI.
    *   *Need:* Silent message loss and provider-specific regressions (DeepSeek, WhatsApp) are universal pain points. Projects are shifting toward configurable fallback chains (PicoClaw #3200) and explicit retry logic (NanoBot #5272).
*   **Context Window Management:**
    *   *Projects:* OpenClaw, Hermes, NanoClaw.
    *   *Need:* Efficient context handling is critical. OpenClaw and Hermes are fixing compaction bugs that cause data loss, while NanoClaw is adding tiered bootstrap loading (#22438) to reduce waste.

## 5. Differentiation Analysis
*   **Target Users:** 
    *   *OpenClaw/LobsterAI:* General consumers and multi-channel power users seeking plug-and-play IM integration.
    *   *ZeroClaw/IronClaw:* Enterprise and security-conscious developers prioritizing auditability, isolation, and strict policy enforcement.
    *   *NanoBot/Hermes:* Developers and researchers focusing on custom agent workflows, plugin ecosystems, and advanced session management.
*   **Architectural Approach:**
    *   *Monolithic vs. Modular:* Hermes and OpenClaw are moving from monolithic structures toward modularity (sharding god files, plugin lifecycle hardening). ZeroClaw and IronClaw are built on modular, crate/extension-based architectures from the ground up.
    *   *Language Stack:* The ecosystem is split between Node.js/TypeScript (OpenClaw, LobsterAI, CoPaw) and Rust (ZeroClaw, IronClaw, PicoClaw), with Go emerging in NanoClaw and PicoClaw for performance-critical channel integrations.
*   **Feature Focus:**
    *   *LobsterAI* distinguishes itself with rich UI/UX features (Cowork search, Math rendering).
    *   *ZeroClaw* leads in observability (OTel correlation) and security policy enforcement.
    *   *IronClaw* is unique in its "Doc-Truth" pipeline, ensuring documentation stays in sync with code behavior.

## 6. Community Momentum & Maturity
*   **Rapid Iterators:** **LobsterAI** and **CoPaw** are releasing frequently (weekly/bi-weekly) with a focus on UI polish and new channel features. **NanoBot** shows high velocity in security and session isolation fixes.
*   **Stabilizing Giants:** **OpenClaw** and **Hermes Agent** are in "sweeper" phases. While activity is high, it is predominantly firefighting (memory leaks, crashes, migration failures). Their momentum is currently negative in terms of stability but positive in terms of necessary technical debt repayment.
*   **Security-First Maturing:** **ZeroClaw** and **IronClaw** are maturing by establishing rigorous standards (RFCs, Doc-Truth, tool allowlists). Their velocity is high but directed toward reliability and security rather than feature expansion.
*   **Stagnant:** **NullClaw**, **Moltis**, and **ZeptoClaw** show zero activity, indicating potential project abandonment or transition to private/enterprise forks.

## 7. Trend Signals
*   **From "Smart" to "Reliable":** The community is moving past pure capability (model quality) to demand operational reliability. Silent failures, data loss from compaction, and memory leaks are now the top community complaints, not feature gaps.
*   **Security as a Feature:** Agent isolation, session sandboxing, and key leak prevention are no longer niche concerns but core market differentiators. Projects ignoring this (e.g., storing history in workspaces) are facing community backlash.
*   **Observability Demand:** There is a strong trend toward deeper logging and tracing (OTel integration in ZeroClaw, token accounting in IronClaw). Users need to *see* where tokens are spent and why agents fail.
*   **Standardization of Plugins/MCP:** The fragmentation of plugin systems is resolving. Most projects are aligning with MCP (Model Context Protocol) and standardized plugin interfaces (NanoClaw, OpenClaw, ZeroClaw), reducing integration friction.
*   **Value for Developers:** For AI agent developers, the key takeaway is that **state management** and **error transparency** are the next battlegrounds. Building agents that can recover from session corruption, clearly log token usage, and enforce strict security boundaries will provide the most value in the 2026-2027 landscape.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-08-08

## 1. Today's Overview
NanoBot demonstrates high development velocity with **9 issues** and **21 PRs** updated in the last 24 hours, indicating robust community engagement and active maintenance. Activity is heavily concentrated on **security hardening**, **session isolation**, and **WebUI reliability**, with no new releases issued this cycle. The project appears to be in a stabilization phase, addressing technical debt from previous session management refactors (specifically PR #713) while advancing new capabilities like plugin integration and temporary chat modes.

## 2. Releases
*No new releases were published in the last 24 hours.*

## 3. Project Progress
**Merged/Closed PRs (Key Advances):**
*   **PR #5272**: Fixed a critical bug where session retention trimming inadvertently dropped proactive channel delivery messages (e.g., cron notifications).
*   **PR #5287**: Restored global progress defaults for channels that did not explicitly opt into transport-specific settings, fixing regressions in WeChat and Mattermost.
*   **PR #5268**: Resolved an issue where `GET /api/sessions/{key}/messages` failed to return `media_urls` for files outside the media root, aligning history reads with WebSocket behavior.
*   **PR #5263**: Hardened the Weixin (WeChat) channel protocol delivery, streaming, and login flows, aligning with `@tencent-weixin/openclaw-weixin` 2.4.6.
*   **PR #5285 & #5284**: Fixed WebUI route preservation for new topics and removed legacy, unsupported session message routes to clean up the API surface.
*   **PR #5280 & #5231**: Advanced the "Dream" memory feature by ensuring short idle sessions are properly archived and visible to the memory processor.
*   **PR #5277**: Enhanced the WebUI by expanding the model preset editor inline for better usability.

**Open PRs Advancing Features:**
*   **PR #5288**: Integrates Agent Plugins with CLI Apps, providing a unified package boundary for portable skills.
*   **PR #5291**: Aims to persist subagent conversation transcripts, allowing users to review tool calls and reasoning steps after background tasks complete.
*   **PR #5252**: Introduces a "Temporary Chat" mode in the WebUI for non-persistent, multi-turn conversations.

## 4. Community Hot Topics
*   **Token Consumption Transparency**: Issue [#5266](https://github.com/HKUDS/nanobot/issues/5266) highlights significant community concern over excessive token usage (up to 1M tokens in 2 hours). Users are requesting granular logging to trace which calls consume tokens, indicating a need for cost-observability.
*   **Session Isolation & Security**: There is a cluster of high-priority discussions around session security:
    *   Issue [#5276](https://github.com/HKUDS/nanobot/issues/5276) requests enforced session-level temporary file isolation.
    *   Issue [#5278](https://github.com/HKUDS/nanobot/issues/5278) and PR [#5279](https://github.com/HKUDS/nanobot/pull/5279) debate moving session history *outside* the agent workspace to prevent agents from reading/ manipulating their own history when `restrict_to_workspace` is enabled.
    *   PR [#5283](https://github.com/HKUDS/nanobot/pull/5283) proposes per-session sandbox isolation for non-WebUI channels.
    *   *Analysis*: Users are increasingly deploying NanoBot in multi-tenant or shared environments and are demanding stricter boundaries between sessions and between the agent and its storage.
*   **Subagent Observability**: Issue [#5290](https://github.com/HKUDS/nanobot/issues/5290) calls for deduplicating the atomic JSONL write idiom across three writers, while PR [#5291](https://github.com/HKUDS/nanobot/pull/5291) addresses the lack of persistence for subagent transcripts. This reflects a growing use case for complex, multi-step agent workflows that require auditability.

## 5. Bugs & Stability
*   **Critical/High Severity**:
    *   **Issue #5256**: `/goal` messages produce dozens of repeated replies while waiting for user input, creating a noisy and potentially confusing user experience. *Status: Open.*
    *   **Issue #5149**: Audio messages are not sent on WhatsApp despite being received. *Status: Open.*
    *   **PR #5156**: Fixes silently stalled Telegram polling after transient network blips, a reliability issue for production deployments. *Status: Open.*
*   **Medium Severity (Fixed)**:
    *   **Issue #5273**: Session retention trimming dropping proactive messages. *Fixed in PR #5272.*
    *   **Issue #5264**: History API missing `media_urls` for out-of-root files. *Fixed in PR #5268.*
    *   **WebUI Route Issues**: New topic routes being lost or legacy routes causing confusion. *Fixed in PRs #5285 and #5284.*

## 6. Feature Requests & Roadmap Signals
*   **Sticker & Reaction Support (Telegram)**: Issue [#5289](https://github.com/HKUDS/nanobot/issues/5289) requests native support for sending stickers and agent-initiated reactions. This signals a desire for richer, more human-like interactions on Telegram.
*   **Model-Agnostic Computer Use**: PR [#4276](https://github.com/HKUDS/nanobot/pull/4276) continues to push for native `computer_use` and `browser` tools that work across different model providers, not just those with native function calling.
*   **Temporary/Disposable Chats**: PR [#5252](https://github.com/HKUDS/nanobot/pull/5252) introduces temporary chat modes, suggesting the roadmap is moving towards supporting ephemeral, low-commitment interactions alongside persistent sessions.
*   **Plugin Ecosystem Integration**: PR [#5288](https://github.com/HKUDS/nanobot/pull/5288) signals a strategic move to unify manual plugins and catalog-installed apps under the Agent Plugins v1 format.

## 7. User Feedback Summary
*   **Pain Points**: Users are frustrated by **unexplained token burn** (Issue #5266) and **repetitive bot behavior** during goal waits (Issue #5256). There is also dissatisfaction with **media handling inconsistencies** between live WebSocket streams and history APIs (Issue #5264).
*   **Security Concerns**: Advanced users are raising alarms about the security implications of storing session history inside the agent's workspace, especially when sandboxing is enabled (Issue #5278). They perceive a conflict between convenience (shared workspace) and security (isolated sessions).
*   **Satisfaction**: Users appreciate the proactive fixes for WeChat/Weixin stability (PR #5263) and the push for better memory/dream integration (PR #5231, #5280).

## 8. Backlog Watch
*   **Issue #5266** (Token Consumption Logging): No active PR yet. This is a high-visibility request from power users who are monitoring costs closely.
*   **Issue #5149** (WhatsApp Audio): No active fix PR. This is a functional gap in a major channel.
*   **Issue #5256** (Goal Reply Loops): No active fix PR. This is a significant UX bug that could confuse new users.
*   **Issue #5276** (Session-Level Temp File Isolation): While related to the active PR #5283, this specific issue on enforcing isolation at the temp file level remains open and may require further refinement beyond the workspace-level changes.
*   **PR #4276** (Computer Use): This is a long-standing enhancement (created June 2026) that remains open, indicating the complexity of implementing model-agnostic computer control.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-08-08

## 1. Today's Overview
Hermes Agent is experiencing peak development velocity with 100 total issues/PRs updated in the last 24 hours, indicating intense focus on session-state safety and desktop stability. The project is currently in a critical "sweeper" phase, addressing high-risk session state corruption and gateway crashes that threaten production reliability. While no new releases were shipped today, the rapid influx of fixes for context compression and Windows-specific bugs suggests an imminent patch release focused on stability.

## 2. Releases
**No new releases today.**  
Current activity is concentrated on `main` branch fixes; no version tags were updated in the last 24 hours.

## 3. Project Progress
**Merged/Closed Items (Last 24h):**
*   **#79331** [CLOSED] Fixed Telegram Rich Messages omitting standard copy affordance for code blocks.
*   **#81441** [CLOSED] Fixed Windows `search_files` failure caused by improper path passing to ripgrep.

**Key Advances:**
*   **Session Archive Logic:** PR #81445 introduces `archived_at` stamping to sessions, enabling better "Done/KPI" paging and archival sorting.
*   **Context File Loading:** PR #80781 ports the Grok-cli directory-chain logic, allowing sessions to merge `AGENTS.md` from git root down to cwd.
*   **Dashboard Input:** PR #76257 fixes dead-key/IME composition input in the dashboard chat.
*   **Desktop Composer:** PR #81435 adds a render/edit bridge for desktop plugins to interact with the chat composer.

## 4. Community Hot Topics
These issues are driving the most discussion and reflect core architectural pain points:

1.  **[Epic] Shard all 20 god files** (#78647) – *60 comments*  
    [Link](https://github.com/NousResearch/hermes-agent/issues/78647)  
    **Analysis:** The community is heavily engaged in the mandatory refactoring of monolithic files into modular components. This is a top-priority architectural cleanup effort.
2.  **[Tracking] Plugin Interface Expansion** (#64182) – *30 comments*  
    [Link](https://github.com/NousResearch/hermes-agent/issues/64182)  
    **Analysis:** Users are pushing for a more stable and extensible plugin system to reduce friction for contributors with long-queued PRs.
3.  **Configurable Memory Backends** (#47349) – *15 comments*  
    [Link](https://github.com/NousResearch/hermes-agent/issues/47349)  
    **Analysis:** Strong demand for decoupling memory from the hardcoded `MEMORY.md`/`USER.md` system, allowing users to disable file-based memory or use `honcho`/`fact_store` exclusively.
4.  **Configurable Temperature** (#17565) – *13 comments, 13 👍*  
    [Link](https://github.com/NousResearch/hermes-agent/issues/17565)  
    **Analysis:** High community support for exposing the `temperature` parameter, currently hardcoded, to reduce hallucinations and improve inference control.

## 5. Bugs & Stability
**Critical/P1 Issues (High Severity):**
*   **#79278** [Bug] Context compression drops in-flight tool chains, causing unsafe replays of non-idempotent operations.  
    [Link](https://github.com/NousResearch/hermes-agent/issues/79278)
*   **#65365** [Bug] OAuth (Claude Pro/Max) triggers HTTP 400 "out of extra usage" when `memory` or `session_search` tools are present.  
    [Link](https://github.com/NousResearch/hermes-agent/issues/65365)
*   **#79624** [Bug] Gateway crashes with `exit(1)` during preflight compaction on restart if session exceeds 98,304 tokens.  
    [Link](https://github.com/NousResearch/hermes-agent/issues/79624)

**High-Visibility Fixes In Progress:**
*   **#80449** (Bug) / **#81444** (PR): Compressor fails to split oversized single turns. **Fix PR #81444** is open to split turns at tool-group-aligned boundaries.
*   **#80968** (Bug) / **#81441** (PR): Gateway crash on Windows `--tui`. **Fix PR #81441** addresses native path handling for Windows.
*   **#80507** (Bug): Delegated child Kanban tasks can exhaust parent turn budgets.  
    [Link](https://github.com/NousResearch/hermes-agent/issues/80507)

## 6. Feature Requests & Roadmap Signals
*   **Interrupible Per-Tool Execution Lease** (#81438) – Request for watchdogs, heartbeats, and absolute deadlines per tool to prevent hangs.
*   **PreToolUse Enforcement Hook** (#40662) – A hook to enforce system-prompt rules during deep debugging when LLMs suffer from recency bias.
*   **Hybrid Tool Pre-Selection** (#13332) – RAG-style semantic + keyword tool schema injection to reduce token overhead (~14k tokens saved).
*   **First-class Teams** (#81405) – Persistent multi-profile teams with shared channels and capabilities, extending the existing Profile/Kanban primitives.
*   **Cognitive Memory Operations** (#509) – LLM-driven encoding, consolidation, and adaptive recall, moving beyond flat text storage.

**Prediction:** The next patch release will likely prioritize **context compression fixes** (#79278, #80449) and **Windows stability** due to the volume of P1/P2 reports.

## 7. User Feedback Summary
*   **Pain Point:** Context compression is unreliable and dangerous for non-idempotent tools (#79278, #80449). Users report side effects completing without the agent receiving the result, leading to unsafe replays.
*   **Pain Point:** Windows desktop experience is fragmented (#80968, #80946, #81290). Users encounter crashes, black screens, and local file path failures.
*   **Pain Point:** Telegram and Discord integrations have "silent failure" modes (#81440, #63485), where rejections or ignored updates appear as success to the user.
*   **Satisfaction:** The community appreciates the active "sweeper" initiative addressing session state risks and the rapid response to Windows-specific bugs.

## 8. Backlog Watch
*   **#78647** [Epic] Shard all 20 god files – Requires sustained refactoring effort; currently the most commented issue.
*   **#64182** [Tracking] Plugin Interface Expansion – Needs maintainer decision to unblock community contributions.
*   **#47349** Configurable Memory Backends – High-priority feature request awaiting implementation.
*   **#17565** Configurable Temperature – High community support (13 upvotes) but still open.
*   **#509** Cognitive Memory Operations – Long-standing vision item for advanced memory features.

---  
*Generated by Agnes-2.0-Flash for NousResearch/hermes-agent*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest: 2026-08-08

## 1. Today's Overview
PicoClaw exhibited high development velocity on August 7, 2026, with 14 PRs updated and 4 issues touched in a single day. The project remains actively maintained by Sipeed, with a focus on dependency hygiene, channel stability (WhatsApp/DingTalk), and LLM provider integration. No new releases were published today, suggesting the team is accumulating fixes before a potential minor version bump. Activity is healthy, with a mix of automated Dependabot updates, community feature contributions, and critical stability patches.

## 2. Releases
**None.** No new releases were published in the last 24 hours.

## 3. Project Progress
**Merged/Closed PRs Today:**
*   **#3291 (Closed):** Bumped `github.com/github/copilot-sdk/go` from 0.2.0 to 1.0.8. This is a significant API upgrade for GitHub Copilot integration.
*   **#3289 (Closed):** Bumped `github.com/pion/rtp` from 1.10.2 to 1.10.5, likely addressing audio streaming stability or bugs.

**Features Advanced/Fixed Today (Open PRs):**
*   **#3321:** Optimized prefix caching by moving dynamic context (time, session, sender) after history in the system message. This is a performance optimization for LLM inference.
*   **#3320:** Fixed WhatsApp connectivity by bumping `whatsmeow` to resolve "client outdated (405)" errors, restoring native WhatsApp channel functionality.
*   **#3319:** Fixed the `exec` tool to correctly honor per-run timeouts and boolean flags (`background`, `pty`), correcting previous schema mismatches.
*   **#3283:** Added image message support for DingTalk, enhancing inbound media handling for this channel.
*   **#3270:** Added DashScope (Alibaba Cloud) TTS provider and WeChat audio file sending support.
*   **#3271:** Updated default model names across 9 providers to reflect July 2026 availability (e.g., OpenAI `gpt-5.6-*` series).

## 4. Community Hot Topics
*   **Issue #3093: SimpleX/Tox/Wire Gateway Request (6 comments, 1 👍)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3093)  
    *Analysis:* Users are requesting end-to-end encrypted (E2EE) messenger support beyond standard Telegram/WhatsApp. This signals a niche but dedicated user base prioritizing privacy.
*   **Issue #3302: OAuth 2.1 for MCP Servers (2 comments)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3302)  
    *Analysis:* Reflects the evolving MCP specification. Users need OAuth 2.1 compliance for enterprise or secure MCP server integrations.
*   **Issue #3307: Session List/Switch Command for Telegram (1 comment)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3307)  
    *Analysis:* Parity gap between Web UI and Telegram CLI. Users managing multiple sessions via Telegram lack discoverability, indicating a need for consistent UX across channels.
*   **PR #3321: Prefix Caching Optimization (0 comments)**  
    [Link](https://github.com/sipeed/picoclaw/pull/3321)  
    *Analysis:* Technical performance fix. Low community engagement but high impact for users with long contexts.

## 5. Bugs & Stability
*   **High Severity: WhatsApp Client Outdated (405 Error)**  
    *Bug:* WhatsApp socket disconnects due to outdated client version in `whatsmeow`.  
    *Fix:* PR #3320 is open to bump the dependency.
*   **Medium Severity: Exec Tool Timeout/Schema Mismatch**  
    *Bug:* `exec` tool ignored per-run timeouts and misdeclared boolean options as strings.  
    *Fix:* PR #3319 addresses this.
*   **Medium Severity: Tool-Call Format Leakage in Seahorse**  
    *Bug:* Internal tool-call formats were leaking into user-visible messages via Seahorse summaries.  
    *Fix:* PR #3279 addresses this logic error.
*   **Low Severity: Concurrency Hazards in SeaHorse/Channel Manager**  
    *Note:* Issue #3308 flags potential goroutine leaks and memory optimizations, though no fix PR is yet linked.

## 6. Feature Requests & Roadmap Signals
*   **Dependabot Dependency Updates:** 12 open PRs focused on bumping AWS SDK, Anthropic SDK, and GitHub Copilot SDK. This indicates a roadmap commitment to staying current with LLM provider APIs and cloud infrastructure.
*   **DashScope TTS & WeChat Audio:** PR #3270 adds TTS capabilities for the Chinese market, signaling expansion of audio I/O features beyond Western-centric providers.
*   **Configurable Model Fallback Chains:** PR #3200 allows users to define default fallback chains in the UI/API, enhancing reliability for production deployments.
*   **OAuth 2.1 for MCP:** Issue #3302 suggests roadmap alignment with the latest MCP security standards.

## 7. User Feedback Summary
*   **Pain Points:**
    *   WhatsApp instability due to upstream protocol changes (`whatsmeow` versioning).
    *   Lack of session management parity between Web UI and Telegram.
    *   DingTalk missing image support in inbound messages.
    *   Exec tool not respecting user-specified timeouts.
*   **Satisfaction Indicators:**
    *   Positive engagement with privacy-focused feature requests (SimpleX/Tox).
    *   Appreciation for performance optimizations (prefix caching).
    *   Demand for broader model provider support (OpenAI GPT-5.6 series updates).

## 8. Backlog Watch
*   **Issue #3308: Code Review - Concurrency Hazards (Created 2026-07-30, 1 comment)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3308)  
    *Risk:* Potential goroutine leaks and memory/speed issues in core components (SeaHorse, Channel Manager). Requires maintainer attention to prevent long-term stability degradation.
*   **Issue #3093: SimpleX/Tox Gateway (Created 2026-06-10, 6 comments, Stale)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3093)  
    *Risk:* Long-standing feature request for E2EE messengers. Lack of progress may frustrate privacy-conscious users.
*   **Issue #3302: OAuth 2.1 for MCP (Created 2026-07-30, Stale)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3302)  
    *Risk:* As MCP adoption grows, lack of OAuth 2.1 support may limit enterprise use cases.
*   **Issue #3307: Telegram Session Management (Created 2026-07-30, Stale)**  
    [Link](https://github.com/sipeed/picoclaw/issues/3307)  
    *Risk:* UX inconsistency between channels may lead to user confusion or churn among power users.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-08-08

## 1. Today's Overview
NanoClaw (by nanocoai) exhibits moderate daily activity with **10 PRs** updated and **1 new issue** opened in the last 24 hours, indicating sustained contributor engagement despite no new releases. The project is actively refactoring its channel integration architecture, as evidenced by the superseding of older Mattermost PRs with v2 ChannelAdapter implementations. Community contributions are diverse, spanning utility skills (Tavily, AnyDoc), infrastructure fixes (database migrations, readonly mounts), and setup wizard enhancements. No critical stability incidents were reported today; however, several long-standing integration requests remain open for review.

## 2. Releases
**None.** No new versions were published today.

## 3. Project Progress
**Merged/Closed Today:**
- **PR #3197** [Closed] Fixed progress status display for agent-runner failures, ensuring specific error reasons are shown instead of generic titles. This improves observability for users debugging failed agent actions.

**Actively Advanced (Open PRs):**
- **PR #3199**: Introduces a fresh **Mattermost channel integration** using the v2 `ChannelAdapter` architecture, superseding the outdated PR #546.
- **PR #2909**: Advances the **agent setup wizard** with template loading and first-agent stamping, enhancing onboarding workflows.
- **PR #3190**: Adds a **Tavily MCP tool skill**, expanding available search/retrieval capabilities for agents.
- **PR #3198**: Introduces an **AnyDoc document conversion skill**, supporting broader document processing use cases.
- **PR #3145**: Implements a database migration to **backfill destinations** for existing messaging-group wirings, ensuring data consistency.
- **PR #3196**: Fixes a **readonly mount** issue, likely addressing containerization or filesystem permission errors.

## 4. Community Hot Topics
- **PR #3199** (Mattermost v2 Integration): High relevance due to the clean break from legacy architecture. Community interest in unified channel support remains strong.
- **PR #3190** (Tavily Skill): Reflects demand for enhanced search/retrieval tools in agent workflows.
- **Issue #3200** (New): A conceptual/architectural discussion on persona transparency and cognitive processing, authored by `cyserman`. Though low on comments (1), it signals interest in advanced agent psychology/persona modeling.
- **PR #2909** (Setup Wizard): Indicates ongoing focus on improving developer/user onboarding experiences.

## 5. Bugs & Stability
- **Severity: Medium** - **PR #3197** (Closed): Fixed misleading failure status messages in agent-runner. Users previously saw generic "system check failed" rather than specific reasons. This was a usability/stability improvement.
- **Severity: Low** - **PR #2346** (Open): Fixes handling of unknown slash commands which were previously treated as `passthrough`, causing silent drops in the Agent SDK. This prevents unexpected behavior for users leveraging custom or unrecognized commands.
- **No new crashes or critical regressions** reported in issues today.

## 6. Feature Requests & Roadmap Signals
- **Channel Integrations**: Continued effort to expand supported channels (Mattermost v2, Dial integration in PR #3050) suggests a roadmap prioritizing multi-platform messaging connectivity.
- **Skill Ecosystem**: Rapid addition of utility skills (Tavily, AnyDoc) indicates a strategic push toward a modular, extensible skill framework for common AI operations (search, document conversion).
- **Onboarding Experience**: PR #2909 (setup wizard templates) signals investment in making initial agent configuration more intuitive and customizable.
- **Predicted Next Version Focus**: Likely to include the merged Mattermost v2 integration, new skills (Tavily, AnyDoc), and database migration fixes, assuming they pass review.

## 7. User Feedback Summary
- **Positive**: Appreciation for clearer error reporting in agent failures (PR #3197).
- **Pain Points**: 
  - Previous confusion over silent failures when using unknown slash commands (addressed in PR #2346).
  - Desire for out-of-the-box integrations with platforms like Mattermost and Dial.
- **Satisfaction**: Active contribution pattern (10 PRs) suggests a healthy and engaged user base contributing features rather than just reporting bugs.

## 8. Backlog Watch
- **PR #546** [Closed/Blocked]: Original Mattermost PR, now superseded by #3199. Worth confirming closure is clean.
- **PR #3050** (Dial Integration): Open since July 14; indicates ongoing demand for Dial support but may require architectural alignment.
- **Issue #3200**: New conceptual issue; monitor for community engagement and potential feature specification.
- **PR #2346** (Slash Command Fix): Open since May; despite being a fix, its longevity suggests it may be awaiting review or testing resources.

---
**Links:**
- Issue #3200: https://github.com/nanocoai/nanoclaw/issues/3200
- PR #3199: https://github.com/nanocoai/nanoclaw/pull/3199
- PR #3190: https://github.com/nanocoai/nanoclaw/pull/3190
- PR #2909: https://github.com/nanocoai/nanoclaw/pull/2909
- PR #3145: https://github.com/nanocoai/nanoclaw/pull/3145
- PR #2346: https://github.com/nanocoai/nanoclaw/pull/2346
- PR #3198: https://github.com/nanocoai/nanoclaw/pull/3198
- PR #3050: https://github.com/nanocoai/nanoclaw/pull/3050
- PR #3197: https://github.com/nanocoai/nanoclaw/pull/3197
- PR #3196: https://github.com/nanocoai/nanoclaw/pull/3196

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-08-08

## 1. Today's Overview
IronClaw exhibits **high development velocity** with 50 issues and 50 pull requests updated in the last 24 hours. The project is currently in a critical stabilization phase, focusing on fixing reliability regressions in the Reborn runtime (memory persistence, tool disclosure, and channel delivery) while simultaneously establishing a "Doc-Truth" pipeline to prevent documentation drift. No new releases were published today, suggesting the team is prioritizing code and documentation correctness over shipping.

## 2. Releases
**None.** There are no new releases reported in the last 24 hours.

## 3. Project Progress
**Merged/Closed Pull Requests:**
*   **[Closed] PR #7324 & #7386**: Dependabot updates for Rust dependencies (`base64`, `toml`, `rstest`) and `dompurify` (JS) to address security and stability.
*   **[Closed] PR #7214**: Added explicit Docker and Railway user-sandbox profiles, scoping workspaces/checkpoints to tenant + user for improved security isolation.
*   **[Closed] PR #7372**: Pinned wide-catalog schema-token reduction floors for the tool disclosure benchmark (91 tools) to prevent regression in prompt budget efficiency.

**Active PRs Advancing Features:**
*   **#7374 (feat/disclosure)**: Implements **bulk `tool_describe`** to collapse per-schema round-trips. This significantly reduces latency when the model has many tools (>context fit), addressing performance bottlenecks in progressive tool disclosure.
*   **#7365 (feat/memory)**: Addresses memory reliability by adding `memory-save` guidance and an always-on `MEMORY.md` prompt lane. This directly targets Issue #7185 where facts stated in one conversation were not recalled in another.
*   **#7375, #7376, #7378, #7379, #7381 (feat/doc-truth)**: A coordinated set of PRs establishing a **Doc-Truth Verification Pipeline**. This includes fixing live drift in extension/manifest docs, extending CI guidance checks to the `docs/` surface, adding contract tests for CLI/manifest claims, and introducing a `docs-live` branch to decouple documentation deployment from binary release tags.
*   **#7382 (feat/stress)**: Adds scripted tool-call workloads with durable write read-back to the API stress scenario, ensuring built-in capability writes are exercised by the nightly harness.
*   **#7131 (fix/run_delivery)**: Ensures triggered runs that fail or are cancelled now deliver sanitized terminal notices to the creator, rather than being silently recorded as `Skipped`.
*   **#7377 (feat/channel-delivery)**: Follow-up to #7157, refining channel delivery so that a run acts as its invoker, removing shared-route subject binding.

## 4. Community Hot Topics
**Most Discussed Issues (by comments):**
1.  **#7340 [OPEN] No way to reset model settings to factory defaults** (6 comments)
    *   *Link:* [nearai/ironclaw#7340](https://github.com/nearai/ironclaw/issues/7340)
    *   *Analysis:* Users are struggling with irreversibility in configuration changes. The lack of a "reset to defaults" button for inference settings (provider/model) is causing friction and support tickets. This indicates a need for better UX controls in the Settings UI.
2.  **#6989 [OPEN] Token accounting: hybrid provider-usage + tail estimates** (4 comments)
    *   *Link:* [nearai/ironclaw#6989](https://github.com/nearai/ironclaw/issues/6989)
    *   *Analysis:* A critical bug in `ModelWorkRequest::for_assistant` where input tokens are estimated from the length of a *reference string* rather than the actual content. This impacts cost estimation and prompt budgeting accuracy, especially under the Pi-Harness adoption program.
3.  **#7317 [OPEN] Proposal: Doc-Truth Verification Pipeline** (3 comments)
    *   *Link:* [nearai/ironclaw#7317](https://github.com/nearai/ironclaw/issues/7317)
    *   *Analysis:* Highlights a systemic issue where breaking changes ship without documentation updates (e.g., `origin_gate_matrix` becoming mandatory). The community proposal for a verification pipeline is gaining traction, leading to the immediate multi-PR response above.

## 5. Bugs & Stability
**Critical/High Severity Bugs (Open):**
*   **#7185 [OPEN] Memory not reliably recalled across conversations**
    *   *Link:* [nearai/ironclaw#7185](https://github.com/nearai/ironclaw/issues/7185)
    *   *Detail:* Multiple testers report that context established in Conversation A is lost in Conversation B. This is a core reliability failure for a personal assistant.
    *   *Fix Status:* **PR #7365** is actively addressing this with system prompt guidance and `MEMORY.md` persistence.
*   **#6476 [CLOSED] Slack extension_activate fails with encoding error**
    *   *Link:* [nearai/ironclaw#6476](https://github.com/nearai/ironclaw/issues/6476)
    *   *Detail:* Tool input encoding failure caused the model to hallucinate that Slack required tenant-admin privileges. **Closed**, but indicates fragility in error handling leading to hallucinations.
*   **#7292 [OPEN] Installed tool cannot be used (runner heartbeat error)**
    *   *Link:* [nearai/ironclaw#7292](https://github.com/nearai/ironclaw/issues/7292)
    *   *Detail:* On Railway, after installing CoinGecko tool, the agent fails to invoke it due to runner heartbeat timeouts. Suggests infrastructure stability issues in hosted environments.
*   **#7246 [OPEN] Agent hallucinates automation status**
    *   *Link:* [nearai/ironclaw#7246](https://github.com/nearai/ironclaw/issues/7246)
    *   *Detail:* Agent claims automations are running when none exist. This is a recurring trust-breaking bug also seen in #7247 (GitHub) and #7294 (Telegram).
*   **#6590 [OPEN] `serve` fails on Windows**
    *   *Link:* [nearai/ironclaw#6590](https://github.com/nearai/ironclaw/issues/6590)
    *   *Detail:* Workspace root overlap error prevents `ironclaw serve` from starting on Windows in local-dev profiles. Blocks Windows developers.
*   **#5456 [OPEN] Routine runs fail with runner lease expiration**
    *   *Link:* [nearai/ironclaw#5456](https://github.com/nearai/ironclaw/issues/5456)
    *   *Detail:* 90-second inactivity threshold is too aggressive for multi-tool routines. This is a persistent reliability issue for long-running tasks.

**Recent Fixes/Closures:**
*   **#6643, #6644, #6475 [CLOSED]**: Multiple Telegram pairing and message routing bugs were resolved, though #7368 notes that latency on DeepSeek-class models was the root cause for some "missing" messages.

## 6. Feature Requests & Roadmap Signals
*   **Tool Disclosure Performance (#7374)**: The team is heavily investing in optimizing the `tool_search` → `tool_describe` bridge. Bulk describing tools is a key performance feature for v1.2.0.
*   **Persistent Memory (#7365)**: The move to `MEMORY.md` and explicit save guidance signals that robust, cross-conversation memory is a top-priority feature for the upcoming release.
*   **Doc-Truth Pipeline (#7317, #7375-7381)**: A new engineering discipline is being established to ensure documentation never drifts from code behavior. Expect CI gates that reject PRs if docs are outdated.
*   **Windows Support (#6590)**: While not a new feature, the open bug suggests that stable Windows local development is a roadmap item that is currently blocked.

## 7. User Feedback Summary
*   **Frustration with Irreversibility**: Users feel trapped when they change model settings and cannot revert them (#7340).
*   **Trust Erosion from Hallucinations**: Repeated reports of the agent claiming connections (Slack, GitHub, Telegram) exist when they do not (#6476, #7246, #7247, #7295, #7344). Users are losing confidence in the agent's self-reported state.
*   **Configuration Fragility**: The "encoding error" in Slack (#6476) and "illegal invocation" in WebChat over HTTP (#4874) suggest that minor configuration or environment issues are leading to catastrophic UX failures (hallucinations or broken UI).
*   **Reliability Concerns**: Memory loss (#7185) and lease expiration (#5456) are critical pain points for users relying on IronClaw for routine, long-running tasks.

## 8. Backlog Watch
*   **#7340 [OPEN] Reset to Defaults**: No PR yet. A simple but high-impact UX feature request.
*   **#6590 [OPEN] Windows `serve` Failure**: A platform-specific blocker for developers.
*   **#5456 [OPEN] Runner Lease Expiration**: A persistent infrastructure bug affecting routine reliability.
*   **#6989 [OPEN] Token Accounting Bug**: A technical debt item that impacts cost accuracy and is part of the P1 Pi-Harness program.
*   **#7369 [OPEN] No Traces on Error**: Users cannot debug failures because the UI lacks a trace capture button when errors occur.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest: 2026-08-08

## 1. Today's Overview
LobsterAI demonstrated high development velocity on 2026-08-08, driven by the rapid release cycle of version 2026.8.7. Activity is robust with 6 issues and 7 pull requests updated in the last 24 hours. The project is currently balancing new feature adoption (Cowork search, Markdown math) with critical stability fixes for Windows installation and database integrity. The health of the open-source community is strong, with immediate responses to user-reported bugs regarding model provider parsing and UI rendering.

## 2. Releases
**Version:** 2026.8.7 (Released 2026-08-07)

**Key Changes:**
*   **Cowork Enhancement:** Added in-conversation search functionality for the Cowork feature ([PR #2435](https://github.com/netease-youdao/LobsterAI/pull/2435)).
*   **Renderer Improvement:** Fixed Markdown LaTeX math delimiters for better rendering ([PR #2449](https://github.com/netease-youdao/LobsterAI/pull/2449)).
*   **Windows Stability:** Rescued null watchdog exceptions in the Windows installer to improve installation reliability ([PR #2446](https://github.com/netease-youdao/LobsterAI/pull/2446)).

**Breaking Changes / Migration Notes:**
*   None reported in this specific release. However, users with custom providers using slashed model IDs (e.g., SiliconFlow) should verify their configuration after updates, as a fix is currently in review ([PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452)).

## 3. Project Progress
**Merged/Closed PRs (6):**
*   **Release/2026.8.5** ([PR #2451](https://github.com/netease-youdao/LobsterAI/pull/2451)): Merged into main, incorporating Cowork search, IM analytics, and OpenClaw configuration improvements.
*   **Cowork Fullscreen Fix** ([PR #2450](https://github.com/netease-youdao/LobsterAI/pull/2450)): Restored fullscreen code toolbar functionality on Windows by keeping overlays outside Electron title bar drag regions.
*   **Math Delimiters** ([PR #2449](https://github.com/netease-youdao/LobsterAI/pull/2449)): Fixed rendering of LaTeX math in Markdown.
*   **Chat Search** ([PR #2448](https://github.com/netease-youdao/LobsterAI/pull/2448)): Addressed issues related to the new chat search feature.
*   **Plugin Config Cleanup** ([PR #2445](https://github.com/netease-youdao/LobsterAI/pull/2445)): Stripped plugin-index-managed keys from config sets to prevent conflicts.
*   **Win Installer Fix** ([PR #2446](https://github.com/netease-youdao/LobsterAI/pull/2446)): Resolved null watchdog exit code issues.

**Active PRs (1):**
*   **OpenClaw Provider Fix** ([PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452)): Preserves provider prefixes for slashed model IDs, directly addressing a critical bug reported in Issue #2443.

## 4. Community Hot Topics
*   **Custom Provider Model Parsing:** Issue [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443) highlights a widespread pain point for users of providers like SiliconFlow where model IDs contain slashes. This is currently active with one comment.
*   **Multi-AGENT IM Binding:** Issue [#1265](https://github.com/netease-youdao/LobsterAI/issues/1265) discusses the need for binding different IM robots and models to different AGENTs in a team setup. While closed, it indicates a strategic need for multi-role automation that may resurface.
*   **Scheduled Task Duplication:** Issue [#1263](https://github.com/netease-youdao/LobsterAI/issues/1263) reported duplicate UI entries for scheduled tasks with rate limit errors. Closed, but reflects ongoing UI consistency challenges.

## 5. Bugs & Stability
1.  **Critical: Database Corruption & Crash (WASM Memory)**
    *   **Issue:** [#1273](https://github.com/netease-youdao/LobsterAI/issues/1273)
    *   **Description:** High-frequency writes in Cowork sessions cause `sql.js` (WASM) to crash with `memory access out of bounds` and risk permanent database corruption due to non-atomic `fs.writeFileSync`.
    *   **Status:** Closed (likely addressed in recent refactoring or marked as resolved, but risk remains if not explicitly patched in code review).
2.  **High: Slashed Model IDs Fail in UI**
    *   **Issue:** [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443)
    *   **Description:** Custom OpenAI-compatible providers with slashed model IDs (e.g., `deepseek-ai/DeepSeek-V4-Flash`) cannot be selected in the settings UI.
    *   **Fix Status:** Fix PR [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) is open and awaiting merge.
3.  **Medium: Silent Execution Failures**
    *   **Issue:** [#2447](https://github.com/netease-youdao/LobsterAI/issues/2447)
    *   **Description:** Agents execute tasks with no output and no error messages, making debugging difficult.
    *   **Status:** Open, no comments yet.

## 6. Feature Requests & Roadmap Signals
*   **Multi-Agent Team Coordination:** Issue [#1265](https://github.com/netease-youdao/LobsterAI/issues/1265) requests the ability to bind distinct IM bots and models to different AGENTs (e.g., a dispatcher vs. a PPT generator). This suggests a roadmap direction toward more sophisticated multi-agent orchestration.
*   **In-Conversation Search:** The recent merge of Cowork search ([PR #2435](https://github.com/netease-youdao/LobsterAI/pull/2435)) signals a continued focus on usability enhancements within long-running Cowork sessions.

## 7. User Feedback Summary
*   **Satisfaction:** Users appreciate the rapid iteration on UI/UX features like search and math rendering.
*   **Pain Points:**
    *   **Provider Compatibility:** Users relying on SiliconFlow and similar providers are frustrated by the inability to use standard model IDs with slashes without workarounds.
    *   **Windows Installation Reliability:** Previous issues with the Windows installer (null watchdog exceptions) have been a recurring stability concern, though the latest release attempts to address this.
    *   **Database Integrity:** Long-term users are concerned about data loss risks in high-intensity Cowork workflows.

## 8. Backlog Watch
*   **Skill Installation Bug:** Issue [#1195](https://github.com/netease-youdao/LobsterAI/issues/1195) reports that skills created in the main agent are installed to the OpenClaw directory but do not appear in the skill panel after restart. This is a "must-fix" for user workflow continuity and remains open with stale status.
*   **Silent Execution Errors:** Issue [#2447](https://github.com/netease-youdao/LobsterAI/issues/2447) lacks visibility and requires maintainer attention to improve error logging and user feedback.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-08-08

## 1. Today's Overview
CoPaw (agentscope-ai/QwenPaw) shows high development velocity with 78 merged/closed items and 31 open issues updated in the last 24 hours. Activity is concentrated on stability fixes for v2.1.0-beta.2 and critical provider compatibility patches. The project is in a mature beta phase with strong community engagement, though several Windows-specific regressions and integration bugs require maintainer attention.

## 2. Releases
**v2.1.0-beta.2** was released, featuring:
- **Fix:** Fence-aware section extraction in `real-behavior-proof` (fixes #6626)
- **Fix:** Restore auto snapshots in web workspace bootstrap (#6)

No major breaking changes noted, but several regressions reported by users (see Bugs & Stability).

## 3. Project Progress
**Merged/Closed PRs today (key highlights):**
- **#6808** (fix): Restore visibility of custom profile `.md` files in workspace (#6785)
- **#6788** (fix): Use shared root profile workspace for ACL store instead of per-task workspace (fixes #6786/#6787)
- **#6802/#6801** (fix): Restore desktop window text selection and copy functionality
- **#6776** (fix): Self-heal dead Playwright driver connections ("die once, dead forever" bug)
- **#6799** (fix): Stop temp output file leakage in `execute_shell_command` on Windows
- **#6804** (feat): Accept Chinese approval replies (`允许`/`拒绝`) for WeChat channel

**Under Review:**
- **#6772**: Enhanced ReMe configuration, embedding lifecycle, and Daily Paper
- **#6809**: Sanitize Chat Completions content for strict providers (StepFun compatibility)
- **#6750**: Fix session identity deadlock, early session save, oversized prompt collapse

## 4. Community Hot Topics
1. **#6116** [CLOSED] **Doom loop: agent repeatedly triggers same tool call** (8 comments)
   - *Analysis:* Critical stability issue affecting agent reliability. Community frustrated by wasted API tokens.

2. **#6782** [OPEN] **Docker version: plugin/app markets stuck in maintenance** (8 comments)
   - *Analysis:* Deployment pain point for Docker users; market integration stability concerns.

3. **#6732** [OPEN] **MCP tools periodically fail** (6 comments)
   - *Analysis:* Sporadic tool registration loss requires container restart; indicates lifecycle management bugs.

4. **#6794** [OPEN] **Agent Kanban returns 405 on creation** (2 comments)
   - *Analysis:* Feature regression in v2.1.0b2; Kanban functionality broken for users.

## 5. Bugs & Stability
**Critical/High Severity:**
- **#6813**: `consume_model_response` raises `KeyError: '__aiter__'` on agentscope 2.x ChatResponse, breaking chat auto-title generation
- **#6812**: Google API failures due to `$schema` field in tool schemas
- **#6768**: Agent enters infinite loop after multi-step task completion, session blocked for hours
- **#6785** [OPEN]: Custom persona `.md` files hidden in Files page (regression in v2.1.0b2) — *Fix PR #6808 open*
- **#6786** [OPEN]: Telegram whitelist resets when multica starts new task — *Fix PR #6788 open*
- **#6775**: Malware Bytes flagging Trojan Loader in Windows desktop version (likely false positive but impacting trust)

**Medium Severity:**
- **#6811**: OpenAI Responses continuation summary ignores `disable_thinking`
- **#6806/#6807**: qwenpaw-creator plugin fails on Windows (video/image generation, model config saves)
- **#6803**: OpenAI-compatible requests rejected by strict providers (StepFun 400 error)
- **#6792**: Deprecated npm package names in built-in ACP runner

## 6. Feature Requests & Roadmap Signals
- **#6490**: Add Volcengine Agent Plan and Xiaomi MiMo Standard API as built-in providers
- **#6285**: Add `qwen3.8-max-preview` to Aliyun Token Plan model list
- **#6770**: Make user Chrome tab lifetime configurable across response cycles
- **#6800** [PR]: Intelligent email management assistant with real-time monitoring (first-time contributor feature)

**Prediction:** Provider expansion (Volcengine, Xiaomi) and Windows stability fixes likely target v2.1.0-rc.

## 7. User Feedback Summary
- **Satisfaction:** Users appreciate new feature additions (ReMe enhancements, email management) and quick responses to critical bugs.
- **Pain Points:**
  - Windows desktop experience regressed (text selection broken, temp file leaks, malware alerts)
  - Docker deployment instability (market access, MCP tool persistence)
  - Multi-workspace ACL handling broken in multica scenarios
  - Strict provider compatibility issues (Google, StepFun) causing silent failures

## 8. Backlog Watch
- **#6785**: Custom persona files hidden — *Fix #6808 open but not merged*
- **#6786**: Telegram whitelist reset — *Fix #6788 open but not merged*
- **#6794**: Agent Kanban 405 error — *No fix PR visible*
- **#6775**: Malware false positive — *No maintainer response*
- **#6792**: Deprecated ACP npm packages — *No fix PR visible*

**Recommendation:** Prioritize merging #6808 and #6788 for v2.1.0 release. Investigate #6794 and #6775 for user trust and feature completeness.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-08-08

## 1. Today's Overview
ZeroClaw is operating at high development velocity with 100 issues/PRs updated in the last 24 hours and no new releases issued. Activity is dominated by security hardening, critical SOP (Standard Operating Procedure) runtime fixes, and provider reliability patches. The project is actively addressing systemic bugs that block autonomous agent workflows and enhance security boundaries around tool execution and configuration.

## 2. Releases
No new releases were published on this date. The project remains on the 0.8.4 prebuilt baseline while critical fixes accumulate in pull requests.

## 3. Project Progress
**Merged/Closed Items Today:**
- **[PR #9836](https://github.com/zeroclaw-labs/zeroclaw/pull/9836)**: Fixed `local_whisper` provider crash by making `bearer_token` optional, resolving hard-failures for loopback whisper.cpp instances.
- **[Issue #9821](https://github.com/zeroclaw-labs/zeroclaw/issues/9821)**: Closed investigation into cron tool fallback to shell `crontab`, indicating policy-level resolution or workarounds.
- **[Issue #8933](https://github.com/zeroclaw-labs/zeroclaw/issues/8933)**: Accepted RFC for cross-turn conversation correlation in OTel, advancing observability standards.
- **[Issue #9246](https://github.com/zeroclaw-labs/zeroclaw/issues/9246)**: Closed RFC regarding Todo tracker configuration preservation during ZeroCode migrations.

**Key PRs Advancing:**
- **[PR #9841](https://github.com/zeroclaw-labs/zeroclaw/pull/9841)**: Continues critical SOP headless run fixes, addressing defects where cron-triggered runs stranded indefinitely.
- **[PR #9433](https://github.com/zeroclaw-labs/zeroclaw/pull/9433)**: Enforces tool allowlists in security policy escalation checks, closing a gap in `allowed_tools` validation.
- **[PR #9438](https://github.com/zeroclaw-labs/zeroclaw/pull/9438)**: Hardens the unauthenticated `/api/pair` endpoint against lockout bypasses using peer-derived rate limiting.

## 4. Community Hot Topics
**Most Discussed Issues:**
1.  **[Issue #8933](https://github.com/zeroclaw-labs/zeroclaw/issues/8933)** (13 comments): RFC for OTel cross-turn conversation correlation. *Need:* Operators require deeper observability into multi-turn agent sessions for debugging and auditing.
2.  **[Issue #9246](https://github.com/zeroclaw-labs/zeroclaw/issues/9246)** (12 comments): RFC for preserving Todo tracker config during migrations. *Need:* Stability in configuration preservation during ZeroCode ownership transfers.
3.  **[Issue #5937](https://github.com/zeroclaw-labs/zeroclaw/issues/5937)** (12 comments): Refactor to unify provider architecture and reqwest client management. *Need:* Reduction of code duplication and fragmented configuration across providers.
4.  **[Issue #8424](https://github.com/zeroclaw-labs/zeroclaw/issues/8424)** (10 comments): RFC for workspace-relative forbidden paths. *Need:* Protection of sensitive internal files (`.env`, `rust-toolchain.toml`) from AI agent access.
5.  **[Issue #8043](https://github.com/zeroclaw-labs/zeroclaw/issues/8043)** (9 comments): RFC to retire standalone `aardvark-sys` crate. *Need:* Consolidation of hardware-related crates into `zeroclaw-hardware`.

## 5. Bugs & Stability
**Critical/High Severity (P1):**
- **[Issue #9386](https://github.com/zeroclaw-labs/zeroclaw/issues/9386)**: **Security Leak** - Gemini API key exposed in chat via unsanitized URL query parameters on transport errors. *Status: Closed.*
- **[Issue #9813](https://github.com/zeroclaw-labs/zeroclaw/issues/9813)**: **Security Leak** - API keys written to logs in plaintext during provider connection errors (duplicate/related to #9386). *Status: Closed.*
- **[Issue #9816](https://github.com/zeroclaw-labs/zeroclaw/issues/9816)**: **Billing Failure** - Anthropic provider reports $0.00 spend, preventing budget caps from firing. *Status: Open.*
- **[Issue #9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815)**: **Security Bypass** - `forbidden_paths` is unreachable for paths under `allowed_roots`, rendering security policies ineffective. *Status: Open.*
- **[Issue #9805](https://github.com/zeroclaw-labs/zeroclaw/issues/9805)**: **Runtime Hang** - SOP auto-mode runs from channel/cron triggers never execute and hang forever in 'running' state. *Status: Open, fix in PR #9841.*
- **[Issue #9786](https://github.com/zeroclaw-labs/zeroclaw/issues/9786)**: **Silent Failure** - Malformed `SOP.toml` is silently dropped with no diagnostic. *Status: Open.*
- **[Issue #9770](https://github.com/zeroclaw-labs/zeroclaw/issues/9770)**: **Data Loss** - `cron update` silently discards changes to declarative jobs. *Status: Open.*
- **[Issue #9775](https://github.com/zeroclaw-labs/zeroclaw/issues/9775)**: **Provider Bug** - OpenRouter streaming requests drop `provider_extra` due to missing `merge_extra_body` call. *Status: Open.*
- **[Issue #9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825)**: **False Positive** - Leak detection redacts public blockchain addresses, breaking payment URLs. *Status: Open.*

**Medium/Low Severity (P2/P3):**
- **[Issue #9656](https://github.com/zeroclaw-labs/zeroclaw/issues/9656)**: Telegram typing indicator persists during approval waits.
- **[Issue #9820](https://github.com/zeroclaw-labs/zeroclaw/issues/9820)**: Calculator tool receives literal `<TOOLCALL>` syntax instead of function calls from some models.
- **[Issue #9832](https://github.com/zeroclaw-labs/zeroclaw/issues/9832)**: Build failure with `--features hardware` due to unresolved `aardvark_sys::AardvarkHandle`.
- **[Issue #9834](https://github.com/zeroclaw-labs/zeroclaw/issues/9834)**: Intermittent runtime test failures from shared process-global state.

## 6. Feature Requests & Roadmap Signals
- **[RFC #9810](https://github.com/zeroclaw-labs/zeroclaw/issues/9810)**: Support for Agent Plugins 1.0 standard (skill and MCP packages). *Likelihood: High.*
- **[RFC #9346](https://github.com/zeroclaw-labs/zeroclaw/issues/9346)**: Unified package/capability/config/runtime-state catalog contract. *Likelihood: Medium-High.*
- **[RFC #9824](https://github.com/zeroclaw-labs/zeroclaw/issues/9824)**: Simplify default web-tool surface to `web_fetch`, `web_research`, and `http_request`. *Likelihood: High.*
- **[PR #9766](https://github.com/zeroclaw-labs/zeroclaw/pull/9766)**: Tool-owned invocation triggers with `send_via` vocabulary for static routing. *Likelihood: Medium.*
- **[PR #8337](https://github.com/zeroclaw-labs/zeroclaw/pull/8337)**: Herdr agent reporting integration for CLI interactive mode. *Likelihood: Medium.*

## 7. User Feedback Summary
- **Security & Trust:** Users are highly sensitive to API key leaks in logs and chat messages (Gemini/Anthropic issues). The `forbidden_paths` bypass (#9815) is causing significant concern among users relying on ZeroClaw for sensitive workloads.
- **Reliability of Automation:** Cron-triggered SOPs hanging indefinitely (#9805) and silently discarding changes (#9770) are critical pain points for users building autonomous workflows.
- **Provider Consistency:** Reports of $0.00 spend tracking (#9816) and dropped provider extras (#9775) indicate frustration with inconsistent provider implementations.
- **Usability:** The Telegram typing indicator behavior (#9656) and silent SOP.toml validation failures (#9786) point to a need for better feedback mechanisms in the CLI and channel integrations.

## 8. Backlog Watch
- **[Issue #5937](https://github.com/zeroclaw-labs/zeroclaw/issues/5937)**: Long-standing refactor for provider unification (open since April 2026, 12 comments). Needs maintainer action to resolve fragmented reqwest usage.
- **[Issue #8424](https://github.com/zeroclaw-labs/zeroclaw/issues/8424)**: RFC for workspace-relative forbidden paths (open since June 2026). Critical for security but requires design consensus.
- **[Issue #8043](https://github.com/zeroclaw-labs/zeroclaw/issues/8043)**: RFC to retire `aardvark-sys` (open since June 2026). Blocked by dependency on hardware feature flags.
- **[PR #9433](https://github.com/zeroclaw-labs/zeroclaw/pull/9433)**: Security fix for tool allowlists. Needs author action to address review comments.
- **[PR #9438](https://github.com/zeroclaw-labs/zeroclaw/pull/9438)**: Gateway pairing hardening. Needs author action to finalize implementation details.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*