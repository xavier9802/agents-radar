# OpenClaw Ecosystem Digest 2026-07-23

> Issues: 144 | PRs: 500 | Projects covered: 12 | Generated: 2026-07-23 01:23 UTC

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

# OpenClaw Project Digest
**Date:** 2026-07-23
**Source:** GitHub (openclaw/openclaw)

## 1. Today's Overview
OpenClaw is experiencing high-intensity development activity with **500 PRs updated** and **144 issues addressed** in the last 24 hours, indicating a major stabilization or release cycle preparation phase. The project is currently navigating significant stability challenges related to session state management, channel-specific regressions (WhatsApp, iOS, Discord), and gateway resource exhaustion under load. While no new official releases were published today, the volume of merged fixes and closed bugs suggests imminent patch releases are likely addressing these critical regressions. The community is heavily engaged in refining channel integrations and session durability.

## 2. Releases
*   **No new releases published today.**
*   *Note:* Issues #112391 and #112822 highlight recent confusion and fixes regarding Docker `:latest` tag alignment between stable (`2026.7.1`) and extended-stable (`2026.6.33/34`) builds, suggesting release engineering is actively correcting tag propagation issues.

## 3. Project Progress
Significant technical debt reduction and infrastructure improvements were advanced today:

*   **Infrastructure & CI:**
    *   **#112821:** Added a native `watch-pr-ci` script to handle merge ref computation delays and reduce API quota waste (#112821).
    *   **#112033:** Automated dependency bumps for GitHub Actions (e.g., `actions/create-github-app-token`, `actions/attest`) to enhance security posture (#112033).
*   **Gateway & Performance:**
    *   **#89040:** Critical fix for event-loop stalls during `embedded_run` bootstrap-context, preventing message loss caused by synchronous I/O and blocking `fs.glob` walks (#89040).
    *   **#112111:** Identified and flagged uncached glob resolution in plugin manifest discovery as a startup performance bottleneck (#112111).
*   **Channel Integrations:**
    *   **#112811:** Added support for multiple Microsoft Teams bot accounts per gateway instance (#112811).
    *   **#112782:** Refactored channel doctor migration helpers to eliminate code duplication across nine bundled channel plugins (#112782).
    *   **#95313:** Fixed Slack read actions to honor name-allowlisted channels when channel IDs are required (#95313).
*   **Localization & Docs:**
    *   **#112801 / #112784:** Implemented strict ownership and catalog authoring requirements for localization resources to prevent silent feature gaps (#112801, #112784).

## 4. Community Hot Topics
High-engagement issues reflecting core user needs for reliability and cross-platform parity:

*   **Linux/Windows Native Apps:** Issue #75 remains the most discussed (115 comments, 80 👍), highlighting the urgent demand for feature-parity native clients on Windows and Linux to match the macOS/iOS/Android experience (#75).
*   **Pre-response Enforcement Hooks:** Issue #13583 (16 comments) discusses the need for "hard gates" that mechanically prevent agents from responding without mandatory tool calls, crucial for high-stakes finance/security workflows (#13583).
*   **Context Window Visibility:** Issue #38568 requests injecting context usage % into system prompts to help agents manage long conversations better (#38568).
*   **Mid-stream Steering:** Issue #10960 highlights friction where user steering messages queue until tool boundaries, desiring true real-time injection (#10960).

## 5. Bugs & Stability
A cluster of regressions and stability issues reported today, primarily affecting session integrity and channel delivery:

*   **P0 / Critical:**
    *   **#108435:** Gateway fails to start after updating to `2026.7.1` due to connection errors (#108435).
    *   **#111752:** All streaming `/v1/chat/completions` requests fail with `GatewayDrainingError` on beta builds, breaking external API compatibility (#111752).
    *   **#107575:** TLS certificate pin mismatch loop when using Cloudflare Tunnel/Access, causing infinite auth failures (#107575).
*   **P1 / High Severity:**
    *   **#112711:** Windows Hub node mode stuck in approval/repair loops with invalid bootstrap tokens (#112711).
    *   **#112680 / #112679:** `openclaw models list` crashes with `TypeError` when Anthropic Sonnet 5 refs are unresolvable or use non-env secrets (#112680, #112679).
    *   **#112814:** Telegram queued follow-ups lose typing indicators and draft states due to dispatch lifecycle cleanup (#112814).
    *   **#112688:** iOS app truncates Markdown list items with ellipses instead of expanding them (#112688).
    *   **#112685:** WhatsApp voice-note transcripts are passed as raw text, confusing agent intent (#112685).
*   **Stability/Resource Exhaustion:**
    *   **#107641:** `openclaw-hooks` child processes accumulate under load, starving the event loop and causing message delivery failures (#107641).
    *   **#111879:** Parallel Codex hook relays can exhaust gateway memory limits (1.4 GiB/1.5 GiB), blocking the control plane (#111879).
    *   **#92043:** Compaction timeout (180s) is too rigid, causing legitimate long summaries to fail identically every turn (#92043).

## 6. Feature Requests & Roadmap Signals
*   **Settings Chat in Mobile Apps:** Issue #112002 proposes adding a first-class "Settings → OpenClaw" chat interface to iOS/Android apps, mirroring macOS, to simplify setup and repair (#112002).
*   **DM Pairing Management in UI:** Issue #112399 suggests a Control UI queue for approving DM pairing requests, moving away from CLI-only commands (#112399).
*   **Subagent Model Restrictions:** Issue #90763 requests `allowedModels` config for native subagent spawns to prevent unauthorized model overrides (#90763).
*   **Docker Workspace Symlink:** Issue #11301 asks for a `/workspace` symlink in containers to reduce path friction for agents (#11301).

## 7. User Feedback Summary
Users are reporting significant dissatisfaction with recent stability regressions, particularly around **session state persistence** and **channel-specific quirks**.
*   **Session State:** Multiple reports (#99054, #107750, #95750) indicate that removing/re-adding bots (Teams) or rebooting gateways leads to "zombie" sessions, history leakage, or death-loops. Users expect durable, isolated session contexts.
*   **Mobile Experience:** iOS users are frustrated by media attachment rendering failures (#112790) and UI truncation bugs (#112688), while WhatsApp users face transcription handling issues (#112685).
*   **Operational Friction:** Developers and operators are struggling with silent failures in billing/backoff logic (#39807) and credential resolution in `models.list` (#112679), which hinders reliable automation.

## 8. Backlog Watch
Maintainers should prioritize these long-standing or high-impact items requiring decision or review:

*   **#75 [OPEN] Linux/Windows Clawdbot Apps:** Long-standing feature gap compared to Apple platforms (#75).
*   **#13583 [OPEN] Pre-response enforcement hooks:** Critical for enterprise security/compliance use cases (#13583).
*   **#98200 [OPEN] Recover in-flight gateway run on CLI disconnect:** Affects user experience during CLI disconnections; pending maintainer decision on reattach vs. recook strategy (#98200).
*   **#77249 [OPEN] Reconnect supervisor hangs on zombie WSS:** Requires manual restart; impacts Slack socket-mode reliability (#77249).
*   **#107750 [OPEN] Session maintenance: durable conversation pointers:** Lack of retention path for external pointers causes permanent churn and memory issues (#107750).

---

## Cross-Ecosystem Comparison

# Cross-Project AI Agent Ecosystem Report
**Date:** 2026-07-23

## 1. Ecosystem Overview
The open-source personal AI agent landscape in July 2026 is characterized by a shift from experimental feature expansion to rigorous enterprise-grade stability and operational reliability. Projects are heavily focused on resolving critical regressions in session state management, channel integration robustness (WhatsApp, Telegram, Discord), and resource exhaustion under load. The community demand has evolved from basic chat interfaces to complex multi-agent orchestration, secure credential isolation, and deterministic testing infrastructures, signaling that the ecosystem is maturing toward production-ready deployment standards.

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release Status | Health Score* |
| :--- | :---: | :---: | :--- | :---: |
| **OpenClaw** | 144 | 500 | No New Release | High (Stabilizing) |
| **IronClaw** | 26 | 50 | No New Release | High (Pre-Launch) |
| **CoPaw** | 17 | 50 | v2.0.0.post4 (New) | Medium (Volatile) |
| **ZeroClaw** | 9 | 50 | No New Release | High (Optimizing) |
| **NanoBot** | 6 | 63 | No New Release | High (Active) |
| **Hermes Agent**| 9 | 50 | No New Release | Medium (Fixing) |
| **LobsterAI** | 1 | 5 | No New Release | Stable (Polishing)|
| **Moltis** | 1 | 1 | No New Release | Low (Niche) |
| **PicoClaw** | 4 | 5 | No New Release | Steady (Refactoring)|
| **NanoClaw** | 0 | 3 | No New Release | Low (Review Bottleneck)|
| **NullClaw** | 1 | 1 | No New Release | Critical (Fixed) |
| **ZeptoClaw** | 0 | 0 | No New Release | Inactive |

*\*Health Score based on velocity, bug resolution rate, and community engagement density.*

## 3. OpenClaw's Position
OpenClaw dominates the current activity metrics with significantly higher volume than peers, indicating it is the de facto reference implementation for complex, multi-channel gateway architectures. Its primary advantage lies in its extensive native channel support (WhatsApp, iOS, Discord, Teams) and deep integration capabilities, though this comes at the cost of high complexity and frequent stability regressions. Unlike competitors focusing on single-platform or lightweight deployments, OpenClaw targets power users and enterprises requiring unified session management across diverse endpoints. However, its large codebase introduces significant technical debt, evidenced by the high number of critical P0/P1 bugs related to session state and event-loop stalls.

## 4. Shared Technical Focus Areas
Several critical requirements have emerged across multiple projects, indicating industry-wide pain points:

*   **Session State & Context Durability:**
    *   *Projects:* OpenClaw, Hermes Agent, CoPaw, NanoBot.
    *   *Need:* Users demand persistent, isolated session contexts that survive gateway restarts and cross-device syncing. Failures here lead to "zombie" sessions and history leakage.
*   **Channel Integration Robustness:**
    *   *Projects:* OpenClaw, IronClaw, NanoBot, PicoClaw, NullClaw.
    *   *Need:* WhatsApp, Telegram, and Discord integrations are prone to specific regressions (e.g., identity mismatches, typing indicator crashes, sync loops). Standardization of channel abstractions is urgently needed.
*   **Observability & Telemetry:**
    *   *Projects:* ZeroClaw, Hermes Agent, IronClaw.
    *   *Need:* Enterprise users require detailed tracing (OTel), health diagnostics, and visibility into token usage/model fallbacks to manage costs and debug failures.
*   **Security & Credential Isolation:**
    *   *Projects:* NanoClaw, IronClaw, OpenClaw.
    *   *Need:* Multi-tenant or team-based deployments require strict per-group or per-session credential isolation, particularly for OAuth and API key management.

## 5. Differentiation Analysis

*   **Target User Base:**
    *   *Enterprise/Power Users:* **OpenClaw**, **IronClaw**, **ZeroClaw**. These projects prioritize scalability, security primitives, and complex routing.
    *   *Developers/Integrators:* **CoPaw**, **NanoBot**. Focus on extensibility, plugin markets, and multi-agent orchestration logic.
    *   *Desktop/Consumer:* **LobsterAI**, **Hermes Agent**. Emphasis on UI/UX, local desktop apps, and ease of use.
    *   *Hardware/IoT:* **PicoClaw**, **NanoBot** (Xiaozhi PR). Focus on edge devices and low-resource environments.

*   **Technical Architecture:**
    *   *Gateway-Centric:* **OpenClaw**, **IronClaw**, **ZeroClaw** treat the agent as a network service with multiple frontends.
    *   *App-Centric:* **LobsterAI**, **Hermes Agent** prioritize the client application experience first.
    *   *Framework-Centric:* **CoPaw**, **NanoBot** provide SDKs and tools for building custom agent behaviors rather than just running one.

*   **Feature Focus:**
    *   *Orchestration:* **CoPaw** and **NanoBot** are leading in subagent collaboration and tool chaining.
    *   *Reliability:* **IronClaw** and **ZeroClaw** are investing heavily in hermetic testing and error recovery.
    *   *Integration Depth:* **OpenClaw** offers the widest breadth of social/messaging platform connectors.

## 6. Community Momentum & Maturity

*   **Rapid Iteration / High Velocity:**
    *   **OpenClaw**, **IronClaw**, **CoPaw**: These projects are moving fast but experiencing growing pains. CoPaw’s recent v2.0 release highlights the risks of breaking changes, while OpenClaw and IronClaw show intense activity in fixing foundational stability issues before major releases.
*   **Stabilizing / Maintenance Mode:**
    *   **NanoBot**, **ZeroClaw**, **Hermes Agent**: These projects show healthy, steady development focused on refining existing features, fixing specific bugs, and improving documentation. They appear more mature in their core functionality.
    *   **LobsterAI**: Focused on polishing UI and fixing minor backend leaks, indicating a stable product nearing a new version.
*   **Niche / Low Volume:**
    *   **PicoClaw**, **NanoClaw**, **Moltis**, **NullClaw**: These serve specific niches (embedded hardware, Linux desktop, specific providers) with lower overall activity. NullClaw’s rapid fix of a critical bug shows high maintainer responsiveness despite small size.
*   **Inactive:**
    *   **ZeptoClaw**: No activity suggests potential abandonment or long release cycles.

## 7. Trend Signals

*   **From Chat to Action:** Community feedback increasingly demands "pre-response enforcement hooks" and complex multi-agent workflows, moving beyond simple Q&A to autonomous task execution with safety gates.
*   **Cost & Latency Awareness:** Users are highly sensitive to performance regressions (e.g., CoPaw’s 2s overhead) and token costs. Features like prompt caching (PicoClaw, OpenClaw) and model routing per topic (Moltis) are becoming standard expectations.
*   **Platform Parity Demand:** There is strong, sustained pressure for feature parity across OS platforms (Windows/Linux native apps matching macOS/iOS), as seen in OpenClaw’s Issue #75 and Hermes’ desktop fixes.
*   **Operational Transparency:** The rise of OTel integration, health telemetry, and visible model fallbacks indicates that AI agents are being adopted in production environments where debugging and monitoring are non-negotiable.
*   **Security Hardening:** With the proliferation of multi-user and team deployments, credential isolation and secure OAuth handling are no longer optional but central architectural concerns.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest
**Date:** 2026-07-23
**Source:** HKUDS/nanobot

## 1. Today's Overview
NanoBot exhibits high development velocity with 63 Pull Requests updated in the last 24 hours and 6 Issues addressed, indicating a robust contributor base and active maintenance cycle. While no new releases were published, the volume of merged/closed PRs (40) suggests significant backend stabilization and feature integration are occurring behind the scenes. Community engagement is focused on multi-agent evolution, provider compatibility fixes, and WebUI performance enhancements. The project remains stable but is actively resolving edge-case regressions in channel integrations and memory management.

## 2. Releases
*   **No new releases.**
*   *Note:* Several P1 priority fixes and features (e.g., OAuth status, WebUI indexing) are likely candidates for the next release candidate given their recent merge activity.

## 3. Project Progress
**Key Merged/Closed Items:**
*   **[PR #4866] Session-Scoped Model Presets:** Model preset selection is now scoped to individual sessions, allowing users to switch models per conversation without affecting global defaults. This improves user control and flexibility.
    *   [Link](https://github.com/HKUDS/nanobot/pull/4866)
*   **[PR #5046] Feishu Markdown Table Fix:** Fixed an issue where fenced markdown tables were incorrectly converted into Feishu card tables, breaking formatting.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5046)
*   **[PR #5045] Slack Markdown Table Fix:** Applied similar protection for fenced markdown tables in Slack integrations to prevent corruption during transmission.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5045)
*   **[PR #5044-5043] Cron/Pairing Null Safety:** Resolved crashes caused by `null` values in `pairing.json` and `jobs.json`, improving reliability of background jobs and channel approvals.
    *   [Links](https://github.com/HKUDS/nanobot/pull/5044), [5043](https://github.com/HKUDS/nanobot/pull/5043)

## 4. Community Hot Topics
**Most Active/Discussed Items:**
*   **[Issue #5000] Multi-Agent Collaboration Evolution:** High interest in evolving subagents from simple task delegation to true multi-agent systems with persistent identities and shared state.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5000)
    *   *Analysis:* Users are moving beyond single-agent utility and seeking complex orchestration capabilities, signaling a demand for more sophisticated agent architectures.
*   **[PR #2584] Xiaozhi Voice Gateway Support:** Long-standing PR adding ESP32 voice gateway support via WebSocket and Opus.
    *   [Link](https://github.com/HKUDS/nanobot/pull/2584)
    *   *Analysis:* Strong community desire for hardware-integrated voice interactions, though it has remained open since March due to conflicts.
*   **[PR #5017] WebUI Fallback Model Visibility:** Request to show the actual fallback model in the WebUI composer badge.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5017)
    *   *Analysis:* Transparency in AI behavior is a key user requirement, especially when dealing with rate limits or provider outages.

## 5. Bugs & Stability
**Critical/High Severity Issues Reported:**
*   **[Issue #4934] Qwen Thinking Content Leak:** Qwen models (e.g., qwen3.6-flash) via DashScope were exposing internal reasoning/thinking content in chat responses.
    *   [Link](https://github.com/HKUDS/nanobot/issues/4934)
    *   *Status:* Closed. Likely fixed in recent provider updates.
*   **[Issue #5041] Dream Batch Starvation:** Completed "no-op" Dream batches fail to advance the cursor, potentially starving later history entries indefinitely.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5041)
    *   *Severity:* High (Memory/Data Loss risk). No fix PR identified yet.
*   **[Issue #5040] MCP Schema Validation Failure:** Non-standard JSON-Pointer `$ref`s in MCP tools cause strict providers (Kimi/Moonshot) to disable the entire model.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5040)
    *   *Severity:* High (Usability blocker for specific providers).
*   **[Issue #4948] WebUI Turn Visibility:** Late subagent completions can start system turns that lose visibility in the WebUI.
    *   [Link](https://github.com/HKUDS/nanobot/issues/4948)
    *   *Status:* Closed.

## 6. Feature Requests & Roadmap Signals
*   **Explicit Context Loading for Skills:** [PR #5018] allows direct callers to preload specific skills into the context builder, addressing gaps in automatic skill injection.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5018)
*   **Parallel Search MCP Preset:** [PR #5047] adds a free, anonymous web search tool via Parallel Search, lowering the barrier for internet access.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5047)
*   **Idle Compaction Configuration:** [PR #5036] makes idle compaction scan intervals configurable, crucial for resource-constrained environments like Raspberry Pi.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5036)
*   **xAI Grok OAuth Integration:** [PR #5035] adds native OAuth 2.0 + PKCE for xAI Grok, including proactive token refresh and X Search capabilities.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5035)
*   **Telegram Multi-Bot Support:** [PR #5033] enables independent runtime/session names for multiple Telegram bots within the same instance.
    *   [Link](https://github.com/HKUDS/nanobot/pull/5033)

## 7. User Feedback Summary
*   **Provider Compatibility:** Users report friction with strict JSON schema validators on providers like Kimi and Moonshot when using MCP tools, highlighting a need for more robust schema sanitization.
*   **Resource Efficiency:** Feedback from Raspberry Pi users indicates high CPU usage (30-40%) during idle states due to compaction scans, driving the request for configurable intervals.
*   **Channel-Specific UX:** Conflicts between workspace restrictions and media paths in Feishu integrations cause user frustration, as uploaded files become inaccessible despite correct configuration expectations.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5028)
*   **Transparency:** Users value visibility into which model is handling requests, especially during fallback scenarios, to better understand latency and cost implications.

## 8. Backlog Watch
*   **[PR #2584] Xiaozhi Voice Gateway:** Open since March 2026 with conflicts. Maintainer attention needed to resolve merge conflicts and assess hardware integration scope.
    *   [Link](https://github.com/HKUDS/nanobot/pull/2584)
*   **[Issue #5041] Dream Cursor Starvation:** Critical bug affecting memory consistency. No fix PR yet; requires immediate investigation to prevent data loss.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5041)
*   **[Issue #5040] MCP Schema Forwarding:** Affects multiple strict providers. Needs a comprehensive fix to sanitize or adapt JSON-Pointer references before forwarding.
    *   [Link](https://github.com/HKUDS/nanobot/issues/5040)
*   **[PR #4439] Read-Only `search_history` Tool:** Enhances memory recall capabilities. Open since June 2026; pending resolution of conflicts.
    *   [Link](https://github.com/HKUDS/nanobot/pull/4439)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest: 2026-07-23

## 1. Today's Overview
The Hermes Agent project is experiencing high development velocity, with 50 Pull Requests updated and 9 Issues addressed in the last 24 hours, indicating a strong focus on stability and platform compatibility. Activity is heavily concentrated on fixing critical bugs related to session state management, desktop application entitlements, and cross-platform gateway configurations. While no new releases were published today, the volume of merged and closed PRs (7) suggests rapid iteration cycles aimed at resolving blocking issues for enterprise and desktop users. The project appears healthy but is currently in a "cleanup and stabilization" phase, addressing regressions introduced by recent feature expansions.

## 2. Releases
*   **No new releases** were published today.

## 3. Project Progress
Several key areas saw significant advancement through merged or closed PRs:
*   **Typing Indicators:** PR #69721 was merged, enabling "Hermes Agent is typing..." indicators on relay-fronted platforms, improving user experience during long inference turns.
*   **Session State Fixes:** PR #66880 addressed a critical desktop bug where the most recent session failed to switch when returning from non-chat tabs, restoring expected navigation behavior.
*   **Gateway Health Telemetry:** PR #64536 advanced the gateway health diagnostics plane, allowing operators to monitor platform-specific status and uptime via OTLP/HTTP without exposing user data.
*   **Desktop Entitlements:** PR #69724 resolved the macOS AppleScript automation denial by adding the necessary `com.apple.security.automation.apple-events` entitlement to the hardened runtime build.

## 4. Community Hot Topics
The following issues are driving community discussion and represent key user needs:
*   **[Feature] Cross-platform session context sharing (CLI ↔ Telegram)** [Issue #4335]: *High Interest.* Users are requesting unified session stores across different gateways (CLI, Telegram, Discord). This reflects a growing need for seamless continuity when switching between mobile and desktop interfaces.
*   **[Bug] Desktop session switch failure** [Issue #66875]: *Active Discussion.* With 7 comments, this bug highlights a frustrating UX flaw in the desktop dashboard where the latest session becomes unclickable after tab switching. It is a priority for desktop retention.
*   **[Bug] Windows CJK Username Auth Failure** [Issue #69706]: *Critical Compatibility.* A P2 bug causing authentication failures on Chinese/Japanese/Korean Windows systems due to encoding mismatches (GBK vs UTF-8). This blocks adoption in major Asian markets.
*   **[Bug] Chronos Webhook Profile Validation** [Issue #69715]: *Enterprise Pain Point.* Managed cron jobs for non-default profiles are being rejected due to validation logic errors, impacting multi-user enterprise deployments.

## 5. Bugs & Stability
A cluster of P2 and P3 bugs reported today indicates instability in specific subsystems:
*   **P2 - Windows Auth Encoding:** Issue #69706 causes startup crashes on Windows with CJK usernames. *Status:* Reported; fix pending.
*   **P2 - Anthropic Prompt Cache Misses:** Issue #68191 (referenced in PR #69704) and related PRs address inefficient cross-session caching on Anthropic, leading to higher costs and latency. *Status:* Fix in progress via PR #69704.
*   **P2 - CLI Provider Resolution:** Issue #69709 reports that `--provider` flags fail to resolve correctly for named custom providers, breaking advanced CLI workflows. *Status:* Reported.
*   **P3 - Feishu Comment Handler Crash:** Issue #64864 (PR #64864) fixes an `asyncio.gather` exception handling issue that crashed the entire comment handler if one API call failed. *Status:* Fix merged.
*   **P3 - espeak-ng Installation Hang:** Issue #64802 (PR #64802) addresses indefinite hangs during NeuTTS setup by adding timeouts to subprocess calls. *Status:* Fix merged.

## 6. Feature Requests & Roadmap Signals
User feedback points toward these upcoming priorities:
*   **WhatsApp Skill Bindings:** Issue #69726 requests extending `channel_skill_bindings` to WhatsApp, mirroring existing Discord/Slack functionality. This signals a push to mature the WhatsApp gateway adapter.
*   **Kanban Task Labels:** PR #69719 introduces first-class task labels for the Kanban plugin, enhancing project management capabilities within the agent ecosystem.
*   **Prompt Size Comparison:** PR #69717 adds a CLI tool to compare prompt sizes across profiles, helping operators optimize token usage before deployment.
*   **Clarify Timeout UX:** PR #69720 improves the UX for skipped clarify prompts in the desktop app, ensuring choices remain visible even after timeouts.

## 7. User Feedback Summary
*   **Context Awareness Deficits:** Issue #48027 highlights frustration with the agent's inability to proactively associate context clues (e.g., memory sync skills) with user instructions, leading to redundant explanations. This suggests a need for improved reasoning chains or memory retrieval strategies.
*   **Desktop Usability Friction:** Multiple reports (#66875, #69723, #66880) point to usability issues in the Electron-based desktop app, particularly around session navigation and macOS permissions. Users expect native-like reliability.
*   **Enterprise Reliability:** Issues regarding Chronos webhook validation (#69715) and custom provider resolution (#69709) indicate that enterprise users are encountering edge cases in complex, multi-profile setups that require robust configuration handling.

## 8. Backlog Watch
Maintainers should prioritize attention on these long-standing or high-risk items:
*   **Issue #4335:** Cross-platform session context sharing has been open since March 2026. This is a strategic feature for platform agnosticism.
*   **Issue #44845:** Clarify prompts acting as blocking timers rather than durable decisions. This architectural limitation affects chat-platform decision flows.
*   **Issue #69706:** The Windows CJK auth bug is a significant market barrier and should be fixed urgently given its P2 severity.
*   **PR #69498:** Layered session prune for `state.db`. This addresses unbounded database growth (Issue #54189), which is critical for long-term stability in active deployments.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest
**Date:** 2026-07-23

## 1. Today's Overview
PicoClaw maintains steady development momentum with 4 active issues and 5 pull requests updated in the last 24 hours, indicating consistent community engagement despite a lack of new releases today. The project is actively addressing stability concerns in core communication channels (Matrix, DingTalk) while refining internal code quality through refactoring and dependency updates. Recent activity highlights a shift towards improving reliability in long-running gateway sessions and optimizing cost/performance via AWS Bedrock caching. With no merged PRs closed *today* (only one closed yesterday), the team appears to be in a review-heavy phase before the next release cycle.

## 2. Releases
*   **No new releases published in the last 24 hours.**
*   Current latest versions referenced by users: v0.2.9 and v0.3.1 (git: 2cf030d2).

## 3. Project Progress
*   **Merged/Closed Today:**
    *   **[PR #3285](https://github.com/sipeed/picoclaw/pull/3285)** - `docs: remove picopaw`: Documentation cleanup reverting previous changes.
*   **Advancements & Fixes Opened/Merged Recently:**
    *   **[PR #3283](https://github.com/sipeed/picoclaw/pull/3283)** - Implemented support for inbound image messages in the DingTalk channel, enhancing media handling capabilities.
    *   **[PR #3286](https://github.com/sipeed/picoclaw/pull/3286)** - Updated Go dependencies (`x/text`) to address security vulnerabilities flagged by `govulncheck`.
    *   **[PR #3163](https://github.com/sipeed/picoclaw/pull/3163)** - Advanced AWS Bedrock integration by implementing Converse prompt caching, significantly reducing latency and costs for long conversations.
    *   **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222)** - Refactored Deltachat implementation, removing ~200 lines of legacy code and updating documentation for better maintainability.

## 4. Community Hot Topics
*   **Matrix Resilience ([Issue #3203](https://github.com/sipeed/picoclaw/issues/3203)):** High interest (2 👍, 5 comments). Users are frustrated that network disruptions cause silent failures in the `/sync` loop without triggering systemd restarts. This indicates a critical need for robust reconnection logic in production deployments.
*   **Gateway Session Management ([Issue #3257](https://github.com/sipeed/picoclaw/issues/3257)):** Feature request for stateless/no-history modes in gateway sessions. Users want parity with CLI behavior (`--session` flag) to allow fresh conversations without managing complex session keys manually.
*   **IRC Message Handling ([Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)):** New feature request highlighting pain points with IRCv3 long messages. Users need PicoClaw to reassemble split messages (>512 bytes) into cohesive inputs rather than treating them as separate fragments.

## 5. Bugs & Stability
*   **Critical: Matrix Sync Loop Failure ([Issue #3203](https://github.com/sipeed/picoclaw/issues/3203))**
    *   *Severity:* High. Causes permanent service degradation after minor network hiccups.
    *   *Status:* Open. No fix PR identified yet.
*   **Medium: Process Hook Deserialization Defect ([Issue #3258](https://github.com/sipeed/picoclaw/issues/3258))**
    *   *Severity:* Medium. `before_tool` hooks fail because `decision` fields are discarded and arguments are misparsed due to serialization bugs.
    *   *Status:* Open (stale). Affects advanced automation workflows using DeepSeek.
*   **Low: DingTalk Image Inbound (Fixed in PR #3283)**
    *   *Status:* Fixed. Support added for receiving images, though edge cases may still exist.

## 6. Feature Requests & Roadmap Signals
*   **AWS Bedrock Optimization ([PR #3163](https://github.com/sipeed/picoclaw/pull/3163)):** Strong signal that cost-performance optimization for enterprise cloud providers (AWS) is a priority. Implementation of cache points suggests future support for other providers with similar features.
*   **Enhanced Media Support:** The DingTalk image fix and IRC long-message request indicate a roadmap focus on handling rich media and non-standard message formats across chat protocols.
*   **Stateless Gateway Modes:** The request for [Issue #3257](https://github.com/sipeed/picoclaw/issues/3257) suggests users are moving towards ephemeral, privacy-conscious or high-throughput usage patterns that don't require persistent history per session.

## 7. User Feedback Summary
*   **Reliability Concerns:** Users running PicoClaw as a system service (via systemd) are highly sensitive to silent failures. The Matrix bug is a major pain point for production stability.
*   **Developer Experience:** The refactoring of Deltachat ([PR #3222](https://github.com/sipeed/picoclaw/pull/3222)) is appreciated for reducing technical debt, but users need clearer documentation on the new secrets management approach.
*   **Usability Gaps:** The lack of easy session isolation in Gateway mode ([Issue #3257](https://github.com/sipeed/picoclaw/issues/3257)) forces users to work around architectural limitations, impacting ease of use for multi-conversation setups.

## 8. Backlog Watch
*   **[Issue #3203](https://github.com/sipeed/picoclaw/issues/3203):** Requires immediate attention from maintainers. The lack of reconnection logic is a significant blocker for reliable deployment.
*   **[Issue #3258](https://github.com/sipeed/picoclaw/issues/3258):** The "stale" label suggests this bug has been overlooked. It affects custom hook functionality, which is crucial for power users integrating specific AI models like DeepSeek.
*   **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222):** Although labeled stale, it represents significant code cleanup. Maintainers should prioritize merging this to reduce maintenance burden, even if it requires re-review.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest: 2026-07-23

## 1. Today's Overview
The NanoClaw project remains in an active development phase with a focus on infrastructure security, multi-channel consistency, and utility integrations. While no new releases were deployed in the last 24 hours, there is significant motion in the pull request pipeline, with three open PRs requiring review or merging. Community engagement is currently driven by a critical clarification regarding credential isolation policies and ongoing efforts to standardize WhatsApp sender identities across different backend paths. The absence of closed issues or merged PRs suggests that the current workflow may be bottlenecked at the review stage, though the volume of open work indicates steady contributor momentum.

## 2. Releases
*   **No new releases** were published in the last 24 hours. The latest version status remains unchanged from previous deployments.

## 3. Project Progress
*   **PR #3070 (WhatsApp Identity Divergence):** A fix is underway to resolve sender identity inconsistencies between the native Baileys path and the Cloud path for WhatsApp. This addresses Issue #3069, ensuring that user IDs are normalized regardless of the connection method.
*   **PR #3117 (Waybar Status Indicator):** A new "Utility skill" has been proposed to add a Waybar status indicator for NanoClaw. This enhancement aims to improve system tray visibility and status monitoring for users running NanoClaw within Linux desktop environments using Wayland.
*   **PR #2877 (Telegram Rich Rendering):** Development continues on implementing native rich rendering via Telegram Bot API 10.1 `sendRichMessage`. This PR seeks to enhance the visual fidelity of Telegram interactions within the agent framework.

## 4. Community Hot Topics
*   **Security Policy Clarification (Issue #3118):**
    *   **Link:** [nanocoai/nanoclaw Issue #3118](https://github.com/nanocoai/nanoclaw/issues/3118)
    *   **Analysis:** Maintainer `bradfeld` has highlighted a discrepancy in `docs/SECURITY.md` regarding per-group credential isolation. The documentation claims distinct OneCLI agent identities per group, but self-hosted OAuth connections operate at the account level. This is a high-priority topic as it affects trust boundaries and security configurations for multi-tenant or team-based deployments. Users are likely seeking clarity on whether true isolation is possible or if the documentation needs immediate correction.
*   **WhatsApp Integration Stability (PR #3070):**
    *   **Link:** [nanocoai/nanoclaw PR #3070](https://github.com/nanocoai/nanoclaw/pull/3070)
    *   **Analysis:** The divergence in user IDs between Baileys and Cloud paths creates confusion for agents relying on consistent identity mapping. This reflects a broader need for robust abstraction layers in multi-channel messaging integrations.

## 5. Bugs & Stability
*   **Identity Mismatch Bug (Related to PR #3070):**
    *   **Severity:** Medium
    *   **Description:** NanoClaw assigns different user IDs to the same phone number depending on whether the WhatsApp connection uses the native Baileys library or the Cloud API. This can lead to fragmented conversation histories or incorrect agent routing.
    *   **Fix Status:** A fix is proposed in PR #3070.
*   **Documentation Inaccuracy (Issue #3118):**
    *   **Severity:** Low (Informational/Trust)
    *   **Description:** The `SECURITY.md` file overclaims the extent of credential isolation for self-hosted setups. While not a code crash, it poses a risk to users configuring security policies based on incorrect assumptions.

## 6. Feature Requests & Roadmap Signals
*   **Linux Desktop Integration (PR #3117):**
    *   **Signal:** The proposal for a Waybar status bar indicator suggests a growing user base utilizing NanoClaw in Linux desktop environments. This points to a roadmap signal towards better OS-level integration and system tray notifications.
*   **Enhanced Messaging UI (PR #2877):**
    *   **Signal:** Continued work on Telegram’s `sendRichMessage` indicates a commitment to keeping up with platform-specific feature updates, aiming to provide a richer user experience comparable to native app capabilities.

## 7. User Feedback Summary
*   **Pain Points:** Users are experiencing friction with inconsistent identity handling in WhatsApp integrations, which complicates agent logic and debugging. There is also confusion regarding security isolation guarantees in self-hosted OAuth setups, leading to potential misconfiguration risks.
*   **Satisfaction/Dissatisfaction:** The community appears engaged and proactive, with contributors actively submitting fixes and new skills. However, the lack of merged PRs today may indicate frustration with the review turnaround time or hesitation due to the complexity of the changes involved.

## 8. Backlog Watch
*   **PR #2877 (Telegram Rich Rendering):** Created on 2026-06-28 and updated recently, this PR has been open for over a month. It represents a significant UX improvement for Telegram users and requires maintainer attention to prevent stagnation.
*   **PR #3070 (WhatsApp Fix):** Although created earlier (2026-07-16), it remains open. Given the impact on core functionality, prioritizing this merge is essential for stability.
*   **Issue #3118 (Security Docs):** While not a bug, the need for documentation correction is urgent to maintain trust. Maintainers should prioritize updating `SECURITY.md` to reflect actual OAuth behavior.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest
**Date:** 2026-07-23

## 1. Today's Overview
The NullClaw project demonstrated focused maintenance activity on July 22, resulting in one closed issue and one merged pull request. Development efforts were concentrated on resolving critical stability defects within the Discord gateway integration rather than introducing new features. The immediate closure of both the bug report (#977) and its corresponding fix (#978) indicates an efficient triage and resolution workflow for high-severity regressions. No new releases were deployed during this period, suggesting the team is prioritizing code stabilization over versioning.

## 2. Releases
*No new releases were published today.*

## 3. Project Progress
**Merged Pull Request:**
*   **#978: discord: run typing thread on the heavy runtime stack**
    *   **Author:** Tetraslam
    *   **Status:** Closed/Merged
    *   **Impact:** This change addresses a stack overflow vulnerability in the Discord typing-indicator functionality. By moving the typing thread to the `heavy runtime stack`, the project prevents process aborts caused by large inline memory copies during TLS initialization. This ensures that bot interactions involving typing indicators remain stable under load.
    *   [View PR #978](https://github.com/nullclaw/nullclaw/pull/978)

## 4. Community Hot Topics
**Most Active Issue:**
*   **#977: Discord gateway goes permanently deaf after exactly one MESSAGE_CREATE**
    *   **Activity:** High severity reproducible bug with immediate resolution.
    *   **Analysis:** The issue highlights a critical fragility in the Discord gateway event loop. Users require reliable continuous event processing; the fact that the bot became "permanently deaf" after a single successful message reaction suggests a state management error or resource leak in the WebSocket handler. The rapid fix indicates that maintaining persistent connectivity is a top priority for the community and maintainers.
    *   [View Issue #977](https://github.com/nullclaw/nullclaw/issues/977)

## 5. Bugs & Stability
**Critical Bug Fixed:**
*   **Issue:** Discord Gateway Silence / Stack Overflow in Typing Thread
    *   **Severity:** Critical (Process Crash / Functional Paralysis)
    *   **Description:** Two related defects were resolved. First, the gateway stopped dispatching events after one `MESSAGE_CREATE` (#977). Second, the typing indicator thread crashed due to stack overflow when performing HTTPS requests on a small auxiliary stack (#978).
    *   **Fix Status:** Resolved via PR #978. The stack size adjustment for the typing thread likely resolves the underlying resource contention or state lock that contributed to the gateway silence, or these were separate but concurrent issues addressed in the same cycle.
    *   **Link:** [Issue #977](https://github.com/nullclaw/nullclaw/issues/977) | [PR #978](https://github.com/nullclaw/nullclaw/pull/978)

## 6. Feature Requests & Roadmap Signals
*No new feature requests or roadmap signals were identified in today's data.*
The activity was purely corrective, focusing on restoring core functionality (Discord connectivity) rather than expanding capabilities. Future roadmap items are not visible in the current snapshot.

## 7. User Feedback Summary
**Pain Points:**
*   **Reliability:** Users experienced total loss of input reception ("permanently deaf") despite the bot appearing online. This breaks trust in the bot's availability for real-time interactions.
*   **Crashes:** Unexpected process termination due to stack overflow during routine operations (typing indicators) caused significant frustration.
*   **Satisfaction:** The rapid response and resolution (closed within 24 hours) likely mitigated long-term dissatisfaction, demonstrating that the maintainers prioritize stability fixes.

## 8. Backlog Watch
*No long-unanswered issues or pending PRs requiring immediate attention were detected in the provided data.*
All reported items from the last 24 hours have been resolved. The backlog appears clear of critical blockers at this time.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest
**Date:** 2026-07-23
**Source:** GitHub (nearai/ironclaw)

### 1. Today's Overview
The IronClaw project is in a high-integration phase leading up to the v1 launch, characterized by significant activity in extension lifecycle management and testing infrastructure. With 50 PRs updated and 26 issues touched in the last 24 hours, the team is aggressively addressing regressions in channel connectivity (specifically Telegram and Slack) while refactoring the core runtime composition. The focus has shifted from feature addition to stabilizing the "Reborn" binary, ensuring hermetic testing coverage, and hardening security primitives like OAuth and secret leases.

### 2. Releases
**No new official releases were published today.**
However, internal CI automation flagged API-breaking changes in dependencies during PR #5598:
*   `ironclaw_common`: 0.4.2 -> 0.5.0 (⚠️ Breaking Change)
*   `ironclaw_skills`: 0.3.0 -> 0.4.0 (⚠️ Breaking Change)
*   `ironclaw_safety`: 0.2.2 -> 0.2.3 (✓ Compatible)

### 3. Project Progress
**Merged/Closed Items & Key Advances:**
*   **Runtime Unification:** PR #6442 merged the collapse of local and production runtime assembly onto a single production-shaped path, removing dead code and simplifying the build process.
*   **ProductSurface Architecture:** Significant architectural progress was made with PR #6480 and PR #6536, which continue the conversion of operator/admin APIs to `ProductSurface` and route channel ingress through it, decoupling legacy `ProductWorkflow` dependencies.
*   **Testing Infrastructure:** PR #6535 added reference model oracles for slice 0, providing deterministic stateful operation coverage for turn/run lifecycles.
*   **Security Foundations:** PR #6472 (Issue) tracks the development of an egress-proxy daemon and secret-lease system, critical for sandboxed agent execution.
*   **Extension Lifecycle:** PR #6520 genericized extension readiness and channel delivery, separating tenant admin config from user membership logic.

### 4. Community Hot Topics
*   **Error Recoverability Epic (#6284):** [Open] [epic] This issue defines the contract for mid-run error recovery, ensuring the model sees causes and solutions. It is a foundational piece for v1 reliability.
    *   *Link:* [Issue #6284](https://github.com/nearai/ironclaw/issues/6284)
*   **Hermetic Testing Platform (#6524):** [Open] [epic] Highlights a gap in deterministic coverage for critical user journeys. The team is actively building this platform to answer "does every capability have meaningful coverage?"
    *   *Link:* [Issue #6524](https://github.com/nearai/ironclaw/issues/6524)
*   **Attested Signing & Ledger (#6532):** [Open] Proposes a design for blockchain transaction signing where the agent acts without unilateral control, addressing safety concerns in financial operations.
    *   *Link:* [Issue #6532](https://github.com/nearai/ironclaw/issues/6532)

### 5. Bugs & Stability
**Critical Stability Issues Reported Today:**
1.  **Telegram Integration Regressions (High Severity):** Multiple P1/P2 bugs indicate severe instability in the newly shipped Telegram support.
    *   **#6478:** Agent fails to recognize connected Telegram, incorrectly redirecting to Slack auth.
        *   *Link:* [Issue #6478](https://github.com/nearai/ironclaw/issues/6478)
    *   **#6475:** `/pair` command not recognized, trapping users in a pairing loop.
        *   *Link:* [Issue #6475](https://github.com/nearai/ironclaw/issues/6475)
    *   **#6474:** Delivery Defaults UI does not expose external channels (Telegram/Slack), blocking configuration.
        *   *Link:* [Issue #6474](https://github.com/nearai/ironclaw/issues/6474)
    *   **#6349:** WebUI renders Telegram chat history inconsistently with fragmented layouts.
        *   *Link:* [Issue #6349](https://github.com/nearai/ironclaw/issues/6349)
2.  **Onboarding Failure (#6523):** Selecting the "test build" flag causes deployment errors.
    *   *Link:* [Issue #6523](https://github.com/nearai/ironclaw/issues/6523)
3.  **Hosted Config Issue (#6534):** Google OAuth config cannot be applied in hosted deployments despite saving successfully.
    *   *Link:* [Issue #6534](https://github.com/nearai/ironclaw/issues/6534)

### 6. Feature Requests & Roadmap Signals
*   **Local Setup Instructions (#6522):** Users request clear CLI instructions for setting up Telegram locally, similar to Google setup guides.
    *   *Link:* [Issue #6522](https://github.com/nearai/ironclaw/issues/6522)
*   **CLI Availability on Staging (#6521):** Operators noted the `ironclaw` CLI was missing from the staging environment SSH session. (Resolved via context, likely a container image fix).
    *   *Link:* [Issue #6521](https://github.com/nearai/ironclaw/issues/6521)
*   **Roadmap Signal:** The intense focus on "Reborn" binary QA, `ProductSurface` abstraction, and hermetic testing suggests the immediate roadmap is prioritizing **stability and observability** over new external integrations. The next version will likely emphasize robust extension manifests and secure default configurations.

### 7. User Feedback Summary
*   **Pain Points:** The primary dissatisfaction stems from the **Telegram onboarding experience**. Users are stuck in loops due to unrecognized commands (`/pair`) and confusing UI states where the agent suggests Slack even when Telegram is active.
*   **Operational Friction:** Hosted deployment operators are encountering friction with OAuth configuration persistence and missing CLI tools in staging environments, indicating gaps in the deployment pipeline or documentation.
*   **Positive Signals:** The community is engaging deeply with the underlying architecture (e.g., discussions on `ProductSurface` and error recoverability), suggesting strong interest from developer/enterprise users who value the system's extensibility and safety guarantees.

### 8. Backlog Watch
*   **#6105 Extension/Channel Lifecycle State-Machine Test:** This epic addresses the #1 user-facing bug family (Slack/Channel disconnections). Despite multiple fixes, it remains open, indicating complex edge cases that require a comprehensive state-machine test suite rather than ad-hoc patches.
    *   *Link:* [Issue #6105](https://github.com/nearai/ironclaw/issues/6105)
*   **#4775 Automated QA for Reborn Binary:** A long-standing epic for automating manual QA journeys. Its continued presence highlights the need for better CI/CD integration for non-deterministic model behaviors.
    *   *Link:* [Issue #4775](https://github.com/nearai/ironclaw/issues/4775)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest: 2026-07-23

### 1. Today's Overview
The LobsterAI project demonstrated high development velocity on July 23, 2026, with five pull requests merged or closed within the last 24 hours and one issue resolved. Activity was concentrated on stability improvements (Windows installer hardening, memory leak prevention) and user experience refinements in the renderer and coworking modules. There were no new official releases published today, suggesting these changes are being accumulated for a future version. The project health appears strong, with active maintenance addressing both critical backend stability and frontend usability concerns.

### 2. Releases
No new releases were published in the last 24 hours.

### 3. Project Progress
Five PRs were closed/merged today, focusing on stability, security, and UI corrections:
*   **Windows Installer Hardening (#2377):** Enhanced security measures for the Windows update installer to prevent potential vulnerabilities. [Link](https://github.com/netease-youdao/LobsterAI/pull/2377)
*   **Export Modal Z-Index Fix (#2376):** Resolved stacking context conflicts by mounting the export options modal via a body portal, ensuring it renders correctly above the sidebar. [Link](https://github.com/netease-youdao/LobsterAI/pull/2376)
*   **OpenClaw OOM Prevention (#2375):** Implemented guards against oversized transcripts causing JavaScript heap-out-of-memory crashes, including handling stale generations after restarts to prevent zombie reconnects. [Link](https://github.com/netease-youdao/LobsterAI/pull/2375)
*   **Skills Management Optimization (#1346):** Merged PR #846 with optimizations according to official requirements, likely refining the skills management feature set. [Link](https://github.com/netease-youdao/LobsterAI/pull/1346)
*   **Scheduled Task Enhancements (#1347):** Integrated advanced features for scheduled tasks, including custom Cron scheduling (visual builder and raw expression), Agent/Model binding, and unified form UX. [Link](https://github.com/netease-youdao/LobsterAI/pull/1347)

### 4. Community Hot Topics
*   **Scheduled Task Customization:** PR #1347 highlights significant community interest in granular control over automated tasks. The inclusion of visual Cron builders and direct Agent binding suggests users are moving towards complex, autonomous workflows. [Link](https://github.com/netease-youdao/LobsterAI/pull/1347)
*   **Stability & Memory Management:** PR #2375 addresses severe stability issues related to large data handling (transcripts). This indicates that power users are generating large context windows, necessitating robust memory safeguards. [Link](https://github.com/netease-youdao/LobsterAI/pull/2375)

### 5. Bugs & Stability
*   **Critical: Heap OOM Crashes:** PR #2375 fixes a critical bug where oversized transcripts caused gateway crashes due to JavaScript heap exhaustion. This is a major stability improvement for long-running sessions. [Link](https://github.com/netease-youdao/LobsterAI/pull/2375)
*   **UI Bug: Stacking Context Issues:** PR #2376 fixed a rendering bug where the export modal was obscured by other elements. [Link](https://github.com/netease-youdao/LobsterAI/pull/2376)
*   **Issue Closed: Duplicate Validation:** Issue #1348 regarding the lack of validation for duplicate scheduled task names was closed. While the issue itself is closed, the corresponding fix may be part of the broader scheduled task enhancements in PR #1347. [Link](https://github.com/netease-youdao/LobsterAI/issues/1348)

### 6. Feature Requests & Roadmap Signals
*   **Advanced Scheduling:** The merged PR #1347 signals a roadmap direction towards more sophisticated automation capabilities, specifically supporting custom Cron expressions and direct model/agent assignment per task.
*   **Skill Management Refinement:** The optimization in PR #1346 suggests ongoing iteration on the "Skills" architecture, aiming to make them more manageable or performant.

### 7. User Feedback Summary
*   **Pain Points Addressed:** Users have experienced crashes with large contexts (fixed in #2375) and UI glitches during export operations (fixed in #1376).
*   **Satisfaction Drivers:** The introduction of user-friendly Cron builders and better integration between scheduled tasks and specific Agents/Models (PR #1347) directly addresses needs for precise automation control.

### 8. Backlog Watch
*   **Stale Items:** Several items marked as `[stale]` were closed today (Issues #1348, PRs #1346, #1347). Maintainers should verify if all necessary code changes from these stale PRs were fully integrated into the main branch, particularly regarding the "Skills Management" and "Scheduled Task" features.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest: 2026-07-23

### 1. Today's Overview
The Moltis project exhibits low but steady activity on July 23, 2026, with one new issue and one open pull request updated in the last 24 hours. No new releases were published, indicating a focus on incremental improvements rather than major version deployments. The single active PR addresses UI/UX refinements for session date display, suggesting ongoing efforts to polish the web interface. Community engagement remains moderate, with no immediate critical stability concerns reported today.

### 2. Releases
No new releases were published in the last 24 hours.

### 3. Project Progress
*   **Pull Request #1162**: An open PR titled "fix(web): show dates for older sessions" was created and updated by `shixi-li` on July 22, 2026. This PR aims to improve the readability of session history by implementing localized date labels (e.g., "yesterday", weekday names) for older entries, enhancing the user experience for long-term conversation tracking.

### 4. Community Hot Topics
*   **Issue #574**: "[Feature] Model Routing Per topic" remains the most discussed item in recent history, with 5 comments and 1 👍 reaction. Although last updated on July 22, 2026, it highlights a significant user need for granular control over AI model selection based on specific conversation topics. This suggests users are seeking advanced customization features to optimize cost or performance for different types of queries.
    *   [View Issue #574](https://github.com/moltis-org/moltis/issues/574)
*   **PR #1162**: Currently open with 0 comments, indicating it is a fresh contribution awaiting review.
    *   [View PR #1162](https://github.com/moltis-org/moltis/pull/1162)

### 5. Bugs & Stability
No critical bugs, crashes, or regressions were reported or addressed in the last 24 hours. The activity is limited to feature enhancements and UI fixes.

### 6. Feature Requests & Roadmap Signals
*   **Model Routing per Topic (Issue #574)**: This request indicates a demand for intelligent, context-aware model switching. If implemented, this could become a key differentiator in future versions, allowing users to assign lightweight models to simple tasks and heavier models to complex reasoning, all within a single interface.

### 7. User Feedback Summary
Users are expressing a desire for better organization and control in their interactions. The high interest in "Model Routing Per topic" suggests dissatisfaction with static model configurations. Additionally, the focus on session date formatting in PR #1162 reflects a need for improved usability in managing long conversation histories, particularly for users who engage with the assistant over extended periods.

### 8. Backlog Watch
*   **Issue #574**: This enhancement request has been open since April 6, 2026, and while it has gained some traction (5 comments), it has not yet been assigned or merged. Maintainers should prioritize reviewing this issue as it represents a clear roadmap signal for advanced configuration features.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest
**Date:** 2026-07-23
**Source:** GitHub `agentscope-ai/CoPaw` (Note: Data reflects `QwenPaw` repo activity)

## 1. Today's Overview
The project exhibits high velocity with **50 Pull Requests** and **17 Issues** updated in the last 24 hours, indicating intense development and community engagement surrounding the v2.0.0.post4 release. The primary focus is stabilizing the new architecture, specifically addressing regressions in agent reasoning loops, tool execution parsing, and context injection introduced in recent v2.0 updates. While a new release (`v2.0.0.post4`) was published to optimize reasoning, immediate community feedback highlights critical stability issues, including process crashes and significant latency overhead compared to v1.x. The maintainer response is rapid, with multiple bug-fix PRs merged or under review today.

## 2. Releases
### v2.0.0.post4
*   **Status:** Released 2026-07-22.
*   **Key Changes:** Optimized agent reasoning logic to mitigate redundant thinking loops and duplicate tool invocations.
*   **Breaking/Regression Notes:** Users report a ~2s fixed overhead per simple conversational reply compared to v1.x (Issue #6307). Additionally, the "new loop functionality" in this version has been linked to main process crashes under load (Issue #6376).
*   **Migration:** No explicit migration guide provided in the changelog, but the performance regression suggests users should monitor latency metrics closely after upgrading.

## 3. Project Progress
**Merged/Closed PRs (Selected):**
*   **[PR #6375]** Fixed token usage persistence retry logic. Resolved an issue where transient write failures caused data loss in token tracking.
*   **[PR #6359]** Fixed context injection role mapping. Changed memory/context hints from `role="system"` to `role="user"` to comply with API providers (GLM/OpenAI) that require system messages only at the start of the conversation.

**Active Developments:**
*   **Scroll Context Management ([PR #6323]):** Redesigning history database compaction to ensure durable task continuity without replacing the source of truth.
*   **QwenPaw Creator App ([PR #6284]):** New app plugin introducing a script-to-video workflow, expanding the platform's creative capabilities.
*   **Plugin Market Sorting ([PR #6349]):** Added sorting by downloads, updates, and favorites to improve discoverability.

## 4. Community Hot Topics
*   **Performance Regression in v2.0 (Issue #6307):**
    *   *Activity:* 4 comments.
    *   *Summary:* Users upgrading from v1.1.12 to v2.0.0.post3 observe a consistent ~2s overhead on simple replies. This is a major pain point affecting user experience.
    *   *Link:* [Issue #6307](https://github.com/agentscope-ai/QwenPaw/issues/6307)
*   **Process Crashes due to Loop Logic (Issue #6376):**
    *   *Activity:* 1 comment (high severity report).
    *   *Summary:* Reports of the main process crashing frequently during runtime due to the new loop features in post3/post4 versions.
    *   *Link:* [Issue #6376](https://github.com/agentscope-ai/QwenPaw/issues/6376)
*   **Tool Call Parsing Failures (Issue #6363 & PR #6364):**
    *   *Activity:* Critical for functionality.
    *   *Summary:* Models wrapping tool arguments in markdown fences or XML tags break JSON parsing, halting all tool execution. A fix is proposed in PR #6364.
    *   *Link:* [Issue #6363](https://github.com/agentscope-ai/QwenPaw/issues/6363) | [PR #6364](https://github.com/agentscope-ai/QwenPaw/pull/6364)

## 5. Bugs & Stability
**Severity: Critical**
*   **Crashes in v2.0.0.post3/4:** Reported in Issue #6376. Linked to the new loop/reasoning optimization.
*   **Tool Execution Broken:** Issue #6363 describes total failure of tool calls when models use markdown/XML wrappers. Fix PR #6364 is open.

**Severity: High**
*   **Context Injection Violation:** Issue #6358/PR #6359. Injecting `role="system"` mid-conversation causes errors in GLM/OpenAI APIs.
*   **Queue State Removal Bug:** Issue #6372/PR #6373. Idle cleanup incorrectly removes newly recreated queue states, leading to race conditions.
*   **Audit Log Bypass:** Issue #6368/PR #6369. `audit_level=none` is ignored, persisting events to SQLite despite policy settings.

**Severity: Medium**
*   **Windows Console Test Failure:** Issue #6361/PR #6365. POSIX syntax in npm scripts breaks Windows CI/development environments.
*   **MiniMax Vision Failure:** Issue #6362/Issue #5135. Images are not recognized correctly via the built-in MiniMax provider, resulting in hallucinations.
*   **Mission Parser Quoting Bug:** Issue #6355/PR #6356. Quoted commands in mission verification are split incorrectly, breaking task execution.
*   **Token Usage Data Loss:** Issue #6374/PR #6375. Transient storage errors cause silent loss of token usage metrics.

## 6. Feature Requests & Roadmap Signals
*   **Per-Job Model Override for Cron Jobs (Issue #6316 / PR #6353):**
    *   *Request:* Allow cron jobs to specify a specific model (e.g., `gpt-4o-mini`) independent of the agent's global default.
    *   *Prediction:* Likely to be included in the next minor update as it addresses complex multi-model orchestration needs.
*   **Visual Prominence of "Always Allow" Button (Issue #6354):**
    *   *Request:* UI design change to reduce accidental permanent permission grants.
    *   *Signal:* Indicates a focus on safety and UX refinement in upcoming releases. PR #6357 addresses this.
*   **Durable Scroll Compaction (PR #6323):**
    *   *Signal:* The team is investing heavily in robust memory management and history retention for long-running agents.

## 7. User Feedback Summary
*   **Satisfaction:** Mixed. Users appreciate the new reasoning optimizations but are frustrated by the performance hit (latency) and stability issues (crashes) in v2.0.
*   **Pain Points:**
    *   **Latency:** The 2s overhead on simple queries is unacceptable for casual users (Issue #6307).
    *   **Reliability:** Tool execution breaking due to model formatting quirks (markdown/XML) is a significant blocker for production use (Issue #6363).
    *   **Platform Support:** Windows users face friction running tests due to script compatibility issues (Issue #6361).
*   **Use Cases:** Heavy reliance on cron jobs for automated tasks, video creation workflows, and multi-model agent setups.

## 8. Backlog Watch
*   **MiniMax Vision Capability (Issue #5135):** Open since June 11, still unresolved. Users report complete failure in image recognition for MiniMax-M3. Requires urgent attention given its age and impact on multimodal functionality. [Link](https://github.com/agentscope-ai/QwenPaw/issues/5135)
*   **Console Coverage Timeout (Issue #6366):** Test instability due to V8 instrumentation overhead. While addressed in PR #6367, the underlying test suite fragility needs monitoring. [Link](https://github.com/agentscope-ai/QwenPaw/issues/6366)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest
**Date:** 2026-07-23
**Source:** github.com/zeroclaw-labs/zeroclaw

## 1. Today's Overview
ZeroClaw is experiencing a period of high-intensity development, evidenced by **50 Pull Requests updated** in the last 24 hours and **9 active Issues**. The primary focus has shifted toward enhancing reliability and observability, particularly within the Anthropic provider integration and multi-node daemon management. While no new releases were published today, the volume of merged code suggests an imminent stabilization phase for the upcoming version. Security vulnerabilities flagged by CI bots are currently being addressed alongside core feature work.

## 2. Releases
*   **No new releases** were published on this date.

## 3. Project Progress
Significant advances were made in **reliability engineering**, **observability**, and **documentation infrastructure**:

*   **Anthropic Provider Reliability (Merged):** Several PRs by `IftekharUddin` and `singlerider` have been merged to stabilize Anthropic interactions. Key updates include detecting server-side fallback responses (#9266), handling native refusals as typed errors (#9262), and fixing streaming tool_use block flushing (#9070). This ensures more transparent fallback behavior when Anthropic declines requests or switches models internally.
*   **Observability Enhancements (Merged):** `alexandme` merged #8752, which nests memory (`memory.recall`, `memory.store`) and RAG spans under the main turn trace. This completes the OpenTelemetry correlation scope defined in Issue #6641, allowing developers to trace end-to-end agent execution flow more effectively.
*   **Documentation & Installation (Merged):** `Audacity88` merged #9267 and #9264, introducing canonical installation documentation routes and a "user-boundary proof matrix" for contributors. This standardizes how Unix and Windows setups are described and provides clearer testing guidelines for maintainers.
*   **Security & CI Fixes (Merged):** `Project516` merged #8781 to remove stale security advisory ignores, and `Audacity88` merged #9169 to fix stalled daemon initialization timeouts in ZeroCode.

## 4. Community Hot Topics
The community is actively discussing **fleet management**, **observability**, and **security policies**.

*   **Daemon Node Health & CLI (#6391, #6390, #6346):** Issues authored by `theonlyhennygod` dominate the conversation around multi-machine fleets. Users need real-time heartbeat tracking for daemon nodes registered via WebSocket and a CLI command to register remote daemons. These features are critical for managing distributed agent networks without manual dashboard intervention.
    *   [Issue #6391](https://github.com/zeroclaw-labs/zeroclaw/issues/6391)
    *   [Issue #6390](https://github.com/zeroclaw-labs/zeroclaw/issues/6390)
*   **Zero-Downtime Config Reloads (#7897):** An RFC by `Audacity88` proposes applying security policy and channel config updates without reloading the entire daemon. This addresses a significant operational pain point for users running long-lived, sensitive agent environments.
    *   [Issue #7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897)
*   **Bedrock Documentation Support (#8925):** A closed issue highlights confusion among AWS users regarding credential profiles and systemd setup for Amazon Bedrock. This indicates a need for better cloud-provider-specific onboarding guides.
    *   [Issue #8925](https://github.com/zeroclaw-labs/zeroclaw/issues/8925)

## 5. Bugs & Stability
Several stability issues and regressions were identified and resolved or are pending:

*   **High Severity: npm Audit Failures (#9235):** A critical/high severity vulnerability was detected in `@redocly/openapi-core` by the CI bot. This requires immediate dependency updates to maintain security compliance.
    *   [Issue #9235](https://github.com/zeroclaw-labs/zeroclaw/issues/9235)
*   **Medium Severity: Channel Supervisor Restart Loop (#9197):** A bug where pressing Ctrl+C during WhatsApp Web operations caused an infinite restart loop has been fixed in PR #9197. This improves stability for users interacting with messaging channels.
    *   [PR #9197](https://github.com/zeroclaw-labs/zeroclaw/pull/9197)
*   **Medium Severity: Lucid ARM Cold Start Timeouts (#9105):** Fixed by merging PR #9105, which increased memory recall/store timeouts from ~0.5s to 3s. This resolved crashes on AArch64 devices where embedding models took longer to load than expected.
    *   [PR #9105](https://github.com/zeroclaw-labs/zeroclaw/pull/9105)
*   **Low/Medium Severity: Model Catalog Cache (#9075):** The `models refresh` command was not persisting data, leaving operators with empty catalogs after restart. This is now fixed.
    *   [PR #9075](https://github.com/zeroclaw-labs/zeroclaw/pull/9075)

## 6. Feature Requests & Roadmap Signals
Based on open PRs and accepted issues, the following features are likely candidates for the next release cycle:

*   **Remote Session Persistence Backend (#9249):** `perlowja` is building the foundation for remote session backends (superseding #6893). This signals a move toward scalable, cloud-backed state management for agents.
    *   [PR #9249](https://github.com/zeroclaw-labs/zeroclaw/pull/9249)
*   **Intra-Family Fallback Notices (#7883):** Users want visibility when a fallback model serves a response from the *same* provider family (e.g., switching between two GPT-4 variants). Currently, only cross-family fallbacks are noted.
    *   [Issue #7883](https://github.com/zeroclaw-labs/zeroclaw/issues/7883)
*   **Config Validation Warnings (#6416):** The quickstart process will soon validate `config.toml` against known incompatibilities (e.g., `llamacpp` settings) before runtime, preventing common user errors.
    *   [Issue #6416](https://github.com/zeroclaw-labs/zeroclaw/issues/6416)
*   **Shell Cron Output Formatting (#8438):** Adding a `shell_output_format` config for cron jobs allows raw stdout consumption, catering to developers integrating ZeroClaw into automated scripts.
    *   [PR #8438](https://github.com/zeroclaw-labs/zeroclaw/pull/8438)

## 7. User Feedback Summary
*   **Pain Points:** Users are frustrated by opaque failures in cloud integrations (Bedrock/AWS profiles) and lack of real-time health signals in distributed node setups. The previous timeout settings for local embeddings on ARM hardware were also cited as a major blocker.
*   **Satisfaction:** The community appreciates the deep dive into observability (OTel traces) and the transparency provided by Anthropic fallback notices. Contributors value the new documentation standards and proof matrices, indicating a healthy contributor culture.
*   **Use Cases:** Strong interest in multi-node fleet management and reliable, fault-tolerant provider routing suggests enterprise and power-user use cases are driving recent development.

## 8. Backlog Watch
Maintainers should prioritize attention on the following items to prevent stagnation:

*   **Security Patch (CI):** Issue #9235 requires immediate action to resolve npm audit failures before they block merges.
    *   [Issue #9235](https://github.com/zeroclaw-labs/zeroclaw/issues/9235)
*   **Multi-Node Infrastructure:** Issues #6391, #6390, and #6346 are interconnected. The lack of a CLI for node registration and real-time heartbeat tracking limits the usability of the gateway dashboard. These are marked `status:no-stale` and `risk:high`.
    *   [Issue #6391](https://github.com/zeroclaw-labs/zeroclaw/issues/6391)
    *   [Issue #6346](https://github.com/zeroclaw-labs/zeroclaw/issues/6346)
*   **Zero-Downtime Reloads:** The RFC in Issue #7897 is critical for production stability but remains open. Clarification on the implementation strategy is needed to unblock progress.
    *   [Issue #7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897)

</details>