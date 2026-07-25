# OpenClaw Ecosystem Digest 2026-07-25

> Issues: 462 | PRs: 500 | Projects covered: 12 | Generated: 2026-07-25 03:21 UTC

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

# OpenClaw Project Digest: 2026-07-25

## 1. Today's Overview
OpenClaw is experiencing extremely high development velocity, with **462 issues** and **500 pull requests** updated in the last 24 hours. Despite zero new releases, the project is actively resolving critical stability regressions introduced in recent versions (2026.7.x), particularly around session state, SQLite data integrity, and gateway crash loops. The focus today has shifted heavily from feature expansion to rigorous quality assurance and bug fixing, evidenced by a surge in maintainer-led PRs targeting "clawsweeper" identified defects. Community engagement remains robust, with significant discussion on memory management, tool reliability, and cross-channel consistency.

## 2. Releases
*   **No new releases published today.**
*   *Context:* The team is currently stabilizing the `2026.7.2-beta` and patching issues from `2026.7.1`. Several critical fixes merged today (#113473, #113453) suggest an imminent hotfix or beta update to address data loss risks during upgrades.

## 3. Project Progress
**Key Merged/Closed & Active PRs:**
*   **#113473 (Fix SQLite Schema Drift):** Critical fix to reject schema data loss during upgrades, addressing the regression where older databases could silently recreate tables and lose data.
*   **#113453 (Crash-Durable Filesystem Publication):** Fixes race conditions in directory synchronization that could cause TLS file corruption or missing parent edges during crashes.
*   **#113470 (QA Runtime Tool Evidence):** Retains runtime tool evidence after agent completion, fixing parity report failures in release validation.
*   **#112863 (Signal Chat-Based Setup):** Adds native chat-based setup and account linking for Signal, improving onboarding UX.
*   **#113476 (Local Model Onboarding):** Introduces UI entry points for downloading/setting up local models on Web and macOS, removing the need for CLI-only configuration.
*   **#113419 (Buzz Channel Plugin):** Adds first-class support for the Buzz channel, allowing agents to participate in approved rooms natively.

## 4. Community Hot Topics
**Most Discussed Issues (by comments/impact):**
*   **[Bug] Session Initialization Conflicts (#102020):** 16 comments. Users report "reply session initialization conflicted" errors in cross-channel sessions. *Need:* Robust session state reconciliation across different transport layers (Signal, Telegram).
*   **[Performance] Memory + Codex Latency (#86996):** 14 comments. High latency and timeouts when using `active-memory` with Codex-backed models. *Need:* Optimization of the memory backend integration and hook handling.
*   **[Bug] Anthropic Thinking Block Bricks (#94228):** 14 comments. Long-lived tool-use sessions fail with `Invalid signature in thinking block`. *Need:* Fix for native Anthropic path state management in multi-turn threads.
*   **[Bug] Compaction Timeout Rigidity (#92043):** 13 comments. The 180s compaction timeout is too rigid for long histories, causing immediate failures. *Need:* Configurable or partial-progress-aware compaction logic.
*   **[Feature] Unified Cron System (#110950):** 10 comments. Proposal to unify heartbeats, watchers, and automation under a single cron primitive. *Need:* Simplified automation architecture.

## 5. Bugs & Stability
**Critical Regressions & Crash Loops:**
*   **Gateway Crash Loop on Upgrade (#107220):** Upgrading to 2026.7.1 causes fatal crash loops due to legacy memory sidecar conflicts. *Status:* Closed, but indicates fragile upgrade paths.
*   **SQLite Snapshot Integrity (#113306):** Snapshots can report success without durable links, risking data loss. *Fix PR:* **#113473** addresses this by failing closed on schema drift.
*   **Tool Output Empty After First Call (#98528):** Regression in 2026.6.11 where subsequent tool calls return empty output. *Impact:* Breaks multi-step agent workflows.
*   **Telegram DM Reply Loss (#111519):** Replies fall back after stale DM-scope cleanup in beta.3. *Impact:* Message delivery inconsistency.
*   **Main Agent Blocked by Workspace Migration (#111498):** Anthropic auth recovery fails due to persistent legacy workspace-state locks. *Impact:* Service outage for specific config states.

**Stability Assessment:** The project is currently in a "stabilization sprint" mode. The frequency of P0/P1 bugs related to state persistence (SQLite, Sessions, Crontabs) suggests that recent architectural changes have introduced fragility in long-running processes.

## 6. Feature Requests & Roadmap Signals
*   **Unified Cron/Automation (#110950):** Strong community push to simplify the "cron" abstraction. Expect this to be a major architectural improvement in the next major version.
*   **Filesystem Sandboxing (#7722):** Persistent demand for granular `tools.fileAccess` controls. *Signal:* Security-conscious users are prioritizing this; likely to be implemented as a strict default or opt-in hardened mode.
*   **Dynamic Model Discovery (#10687):** Request for auto-updating model catalogs (e.g., OpenRouter). *Signal:* Improving provider flexibility is a key roadmap item.
*   **YAML Config Support (#45758):** Readability improvement request. Low priority compared to stability bugs but frequently cited.
*   **Android Chat-First Surface (#46058):** Independent fork gaining traction. Maintainers may consider upstreaming core mobile UI components if the community adoption continues.

## 7. User Feedback Summary
*   **Pain Points:**
    *   **Upgrade Fragility:** Users are frustrated by data loss risks and crash loops during version upgrades (2026.6 -> 2026.7 transition).
    *   **Token Waste:** Context bloat from re-injecting bootstrap files (#67419) is a major concern for cost-conscious users.
    *   **Silent Failures:** Models falling back without notification (#106786) or tools returning empty data (#98528) create confusion and trust issues.
*   **Satisfaction:**
    *   Positive reception for improved Signal setup (#112863) and local model onboarding (#113476).
    *   Users appreciate the rapid response to critical bugs (e.g., SQLite fixes merged within days of reporting).

## 8. Backlog Watch
*   **#86996 (Memory/Codex Latency):** High-impact performance issue affecting popular configurations. Needs maintainer review.
*   **#94228 (Anthropic Thinking Brick):** Blocks reliable use of Anthropic models for long tasks. Linked PR exists but needs verification.
*   **#92043 (Compaction Timeout):** Affects all long-session users. Requires product decision on default values vs. configurability.
*   **#7722 (Filesystem Sandboxing):** Security-critical feature request that has been open since Feb 2026.
*   **#47975 (Subagent Session Persistence):** Subagents not cleaning up properly, causing main session unresponsiveness. Needs investigation into lifecycle management.

---

## Cross-Ecosystem Comparison

# Cross-Project Comparison Report: 2026-07-25

## 1. Ecosystem Overview
The open-source personal AI agent landscape is currently in a critical "stabilization sprint," with major projects shifting focus from feature expansion to rigorous quality assurance and security hardening ahead of imminent v1 or major version releases. High development velocity is evident across the ecosystem, characterized by intense activity on session state integrity, SQLite data durability, and cross-channel reliability, indicating that user trust in persistent memory and tool execution is now the primary competitive differentiator. While fragmentation remains a challenge, there is a clear industry-wide convergence on standardized plugin architectures, unified automation primitives (cron), and enhanced observability for complex multi-agent workflows.

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release Status | Health Score* |
| :--- | :---: | :---: | :--- | :---: |
| **OpenClaw** | 462 | 500 | No new release; stabilizing `2026.7.x` | High (Stabilization) |
| **ZeroClaw** | 45 | 50 | No new release; active merge queue | High (Security Focus) |
| **CoPaw** | 45 | 30 | **v2.0.1 Released**; rapid iteration | High (Post-Launch Fix) |
| **Hermes Agent**| 50 | 50 | No new release; desktop/security fixes | High (Platform Stability)|
| **IronClaw** | 32 | 50 | No new release; pre-v1 bug bash | High (Pre-Launch) |
| **NanoBot** | N/A | 24 | Preparing v0.3.0 internal bump | Medium-High |
| **LobsterAI** | 19 | 8 | **v2026.7.23 Released** | Medium (Backlog Heavy) |
| **PicoClaw** | N/A | 8 | No new release; maintenance mode | Medium |
| **NanoClaw** | 0 | 7 | No new release | Low-Medium |
| **ZeptoClaw** | 2 | 2 | No new release | Stable |
| **Moltis** | 0 | 3 | No new release; review pending | Low |
| **NullClaw** | 0 | 0 | No activity | Stalled |

*\*Health Score based on velocity, issue resolution rate, and community engagement signals.*

## 3. OpenClaw's Position
OpenClaw dominates the ecosystem in terms of raw development volume, processing nearly 1,000 combined issues and PRs daily, which suggests it serves as the foundational reference architecture or "core" for many other projects. Its technical approach is distinctively heavy on infrastructure resilience, prioritizing SQLite schema drift prevention and crash-durable filesystems over novel UI features. Compared to peers like CoPaw or IronClaw, OpenClaw’s community is significantly larger and more fragmented, leading to high noise but also robust peer-review pressure. Its position is that of the "enterprise-grade backbone," whereas competitors are focusing more on specific vertical integrations (e.g., Hermes for desktop, NanoBot for WebUI).

## 4. Shared Technical Focus Areas
*   **Session State & Memory Integrity:** Critical across **OpenClaw**, **CoPaw**, and **ZeroClaw**. Users demand guaranteed data persistence (SQLite fixes) and strict isolation between agents/sessions to prevent cross-contamination.
*   **Cross-Channel Reliability:** **OpenClaw**, **NanoBot**, and **IronClaw** are heavily focused on fixing race conditions and message loss in Telegram, Discord, and Signal integrations. The "typing indicator" and streaming parity are key UX requirements.
*   **Automation & Cron Unification:** **OpenClaw** (#110950) and **NanoBot** (#3035) are moving toward unified cron primitives, reflecting a need for reliable, scheduled agent actions without manual orchestration.
*   **Security Hardening:** **ZeroClaw** (WhatsApp bypass, Shell boundary), **ZeptoClaw** (subprocess secrets), and **Hermes** (API key storage) are addressing critical security flaws, indicating that security is no longer a post-launch concern but a core development pillar.

## 5. Differentiation Analysis
*   **OpenClaw vs. Peers:** Focuses on deep infrastructure stability (SQLite, Gateway crashes) and broad channel support. It is less UI-centric than **NanoBot** or **Hermes**, which prioritize desktop/WebUI experiences.
*   **CoPaw:** Differentiates via the **PawApp Platform** and Kanban integration, targeting power users who need structured project management alongside agent interaction. It also leads in third-party agent integration (Codex/Qoder).
*   **IronClaw:** Emphasizes "Error Recoverability" and "Hermetic Testing," aiming for a v1 launch with high reliability guarantees, contrasting with OpenClaw’s continuous beta stabilization.
*   **NanoBot & ZeptoClaw:** Lean towards lightweight, WebUI-first or Telegram-native experiences with rapid feedback loops (streaming), appealing to users prioritizing speed and simplicity over enterprise-grade persistence.
*   **LobsterAI:** Distinctive focus on "Cowork" browser automation and skin customization, though hampered by significant security and connectivity backlogs.

## 6. Community Momentum & Maturity
*   **Rapidly Iterating (High Velocity):** **OpenClaw**, **ZeroClaw**, and **Hermes Agent**. These projects have massive daily activity, suggesting active core teams responding to immediate user pain points.
*   **Stabilizing/Maturing:** **CoPaw** (post-v2.0.1 release), **IronClaw** (pre-v1 bug bash), and **NanoBot** (preparing v0.3.0). These are shifting from feature creation to bug fixing and polish.
*   **Niche/Slower Pace:** **PicoClaw**, **ZeptoClaw**, and **Moltis** show steady, smaller-scale development, focusing on specific integrations (MQTT, Slack, Telegram) rather than broad platform expansion.
*   **Declining/Blocked:** **NullClaw** shows zero activity, and **LobsterAI** has a large backlog of stale security and functional issues despite recent releases.

## 7. Trend Signals
*   **From Async to Deterministic Reliability:** The industry is moving away from "best-effort" agent behavior to deterministic outcomes. Fixes for SQLite drift, session isolation, and error recoverability indicate that users will not adopt agents unless their data and workflows are guaranteed safe.
*   **Unified Automation Primitives:** The push for "Unified Cron Systems" (OpenClaw, NanoBot) signals that scheduled, background agent work is becoming a standard requirement, not an edge case.
*   **Security as a First-Class Feature:** Hardened subprocess handling (ZeptoClaw), secure config storage (Hermes), and sandbox bypass fixes (ZeroClaw) show that security vulnerabilities are now top-priority blockers for adoption.
*   **Rich UI/UX Expectations:** Streaming indicators, local model onboarding, and interactive plugins (CoPaw PawApp) suggest that the CLI-only era is ending; users expect rich, responsive, and visually informative interfaces comparable to commercial products.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest
**Date:** 2026-07-25
**Source:** HKUDS/nanobot GitHub Repository

## 1. Today's Overview
NanoBot exhibited high development velocity on July 25, 2026, with significant momentum driven by the preparation for the v0.3.0 release cycle. The project processed 24 Pull Requests in the last 24 hours, indicating a robust contribution workflow and active maintenance. While no new official release artifacts were published today, internal version bumping and extensive WebUI refinements suggest an imminent stable release. Community engagement remains focused on core agent reliability, streaming performance, and cross-platform channel stability.

## 2. Releases
*   **Status:** No new public release published on this date.
*   **Internal Preparation:** PR #5081 (`[chore, priority: p1] chore(release): prepare v0.3.0`) indicates the team is actively bumping package and source-tree fallback versions from `0.2.2` to `0.3.0`. This suggests v0.3.0 is in final staging, likely incorporating the numerous bug fixes and UX improvements merged recently.

## 3. Project Progress
The majority of activity today centered on stabilizing the WebUI, enhancing agent concurrency, and fixing provider-specific edge cases. Key advancements include:

*   **Agent Concurrency & Subagents:**
    *   **PR #5074:** Introduced support for inline subagent consultation via a `wait` argument, allowing synchronous retrieval of subagent results within the main flow.
    *   **PR #5075:** Refined authorization logic, carrying coding and artifact-producing tasks through verification without unnecessary user confirmation, while reserving approval for irreversible actions.
*   **WebUI/UX Enhancements:**
    *   **PR #4696:** Implemented smooth streaming Markdown reveal using a buffered requestAnimationFrame scheduler to prevent flashing and improve reading experience.
    *   **PR #5078:** Enabled first-time setup to launch directly from desktop installers via the WebUI, improving onboarding for non-technical users.
    *   **PR #5077:** Added a long-press preset switcher in the composer for quick model switching.
    *   **PR #5050:** Surfaced xAI hosted search activity as structured agent events.
*   **Provider & Channel Fixes:**
    *   **PR #5073:** Fixed preservation of multimodal tool outputs (text, image, file blocks) in OpenAI Responses API integrations.
    *   **PR #4567:** Resolved WeChat streaming issues by fixing configuration serialization and handling upstream relay bugs.
    *   **PR #5049:** Fixed a regression where non-streamed finalization responses were not delivered correctly.

## 4. Community Hot Topics
*   **Telegram Message Truncation Bug:**
    *   **Issue #4637:** [CLOSED] Reported by `MARJORIESHA-pBAD`, this issue highlighted that Telegram long messages sent via Nanobot were splitting incorrectly, causing rendering failures in prior trunks.
    *   **Analysis:** High visibility due to the visual nature of the bug. Its closure suggests the team prioritized fixing critical messaging protocol errors.
*   **Context Loss in Mid-Turn Messages:**
    *   **Issue #4064:** [OPEN] Reported by `hamb1y`, this issue describes pending mid-turn messages losing sender/channel runtime context when injected into active runs.
    *   **Analysis:** This is a fundamental architectural flaw affecting multi-user or complex session states. It has garnered 1 reaction and 1 comment, indicating it is recognized as a persistent pain point for advanced users.
*   **Config Data Loss:**
    *   **PR #1073:** Open PR addressing silent data loss when saving custom configuration keys (e.g., custom provider configs) due to Pydantic model constraints.
    *   **Analysis:** Critical for power users who rely on extensive custom setups. The open status suggests it may be waiting for merge coordination with other changes.

## 5. Bugs & Stability
*   **Severity: High - Non-Streaming Response Delivery:**
    *   **PR #5049:** Fixed a regression where empty or non-streamed final responses were suppressed. This restores reliability for channels that do not support streaming.
*   **Severity: Medium - Multimodal Output Corruption:**
    *   **PR #5073:** Addressed an issue where base64 image content in tool outputs was being serialized as inert JSON text, breaking visual feedback in some providers.
*   **Severity: Medium - WeChat Streaming Failures:**
    *   **PR #4567:** Resolved silent dropping of streaming settings and relay compatibility issues for WeChat, ensuring consistent message delivery.
*   **Stability Note:** The closure of Issue #4637 (Telegram truncation) significantly improves stability for Telegram users. However, Issue #4064 (context loss) remains open and poses a risk for complex multi-turn conversations.

## 6. Feature Requests & Roadmap Signals
*   **Inline Subagent Consultation:** The implementation in PR #5074 signals a roadmap shift towards more sophisticated, synchronous agent orchestration patterns rather than purely asynchronous parallel execution.
*   **First-Time Setup UX:** PR #5078 indicates a strong focus on reducing friction for new users, moving away from terminal-only onboarding to a graphical WebUI-first approach.
*   **Config Preservation:** The ongoing work in PR #1073 suggests future versions will prioritize extensibility and custom provider support, ensuring user configurations are never silently dropped.

## 7. User Feedback Summary
*   **Pain Points:** Users are frustrated by "silent" data loss (config keys dropped) and broken streaming behaviors on specific channels (WeChat, Telegram). The visual flashing of raw Markdown during streaming was also noted as a negative UX element, now addressed in PR #4696.
*   **Satisfaction:** The rapid response to Telegram truncation and the introduction of smoother streaming animations are positive indicators of community responsiveness. The ability to quickly switch models via long-press (PR #5077) is a quality-of-life improvement well-received in similar interfaces.
*   **Unmet Needs:** There is a clear demand for better handling of "mid-turn" queueing in complex sessions (Issue #4064), suggesting users are running deeper, multi-agent workflows that currently break under load.

## 8. Backlog Watch
*   **Critical:** **Issue #4064** ([OPEN] Bug: pending mid-turn messages lose sender/channel/chat runtime context). This issue affects core session integrity and requires maintainer attention. It has been open since May 2026.
*   **Important:** **PR #1073** ([OPEN] fix: preserve unknown config keys when saving). This prevents data loss for custom configurations and is essential for enterprise/power-user retention.
*   **Monitor:** **PR #3035** ([OPEN] fix(cron): introduce grace window for 'at' type tasks). While not urgent, this fixes a logic error where LLM delays caused scheduled tasks to fail silently. It has been open since April 2026.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest
**Date:** 2026-07-25

## 1. Today's Overview
Hermes Agent is experiencing high-velocity development activity with 50 issues and 50 pull requests updated in the last 24 hours, indicating a significant push for stability and feature parity ahead of potential upcoming releases. While no new official versions were published today, the project is actively addressing critical security vulnerabilities, platform-specific bugs (particularly on Windows and macOS), and improving the desktop user experience. The community engagement remains robust, with users reporting detailed reproduction steps for complex gateway and desktop integration issues.

## 2. Releases
*   **No new releases published.**
*   Active development is focused on stabilizing current codebases rather than shipping new major versions.

## 3. Project Progress
Several key fixes and features were merged or advanced today:
*   **Custom Provider Fixes (#71141, #71144):** Critical bugs regarding custom endpoint configuration were addressed. API keys are now securely stored in `.env` instead of plaintext `config.yaml`, and the model list discovery logic was fixed to persist all discovered models rather than just one.
*   **Desktop Localization (#71161):** Added German (`de`) as a sixth locale for the Desktop app, improving international accessibility.
*   **Session Management (#71162):** Implemented title resolution for `@session` chips in transcripts, enhancing context visibility for users.
*   **Discord Integration (#71164):** Introduced an explicit `/review` slash command for Discord, allowing authorized users to trigger review debates directly via UI interaction.
*   **Mattermost Support (#26537):** Added interactive button support for approvals and prompts, bringing Mattermost parity with other major platforms like Telegram and Slack.

## 4. Community Hot Topics
The most discussed topics revolve around desktop stability, security concerns, and platform compatibility:
*   **[Security] Custom Endpoint API Key Storage (#69449):** High concern due to plaintext storage in `config.yaml`. *Link: [Issue #69449](https://github.com/NousResearch/hermes-agent/issues/69449)*
*   **Telegram Gateway Hangs (#67498):** Users report indefinite hangs at connection attempts despite known workarounds. *Link: [Issue #67498](https://github.com/NousResearch/hermes-agent/issues/67498)*
*   **Desktop Boot Failures on Windows (#60144, #69179):** Multiple reports of desktop crashes or failure to launch on Windows, including "This app can't run" errors. *Link: [Issue #60144](https://github.com/NousResearch/hermes-agent/issues/60144) | [Issue #69179](https://github.com/NousResearch/hermes-agent/issues/69179)*
*   **Multi-Host Computer Use (#71157):** Emerging interest in using Hermes to drive multiple physical machines via Cua Driver. *Link: [Issue #71157](https://github.com/NousResearch/hermes-agent/issues/71157)*

## 5. Bugs & Stability
Significant stability issues reported today, ranked by severity:

| Severity | Issue Summary | Status/Fix | Link |
| :--- | :--- | :--- | :--- |
| **P1/Critical** | Telegram gateway hangs indefinitely at connection attempt. | Open | [#67498](https://github.com/NousResearch/hermes-agent/issues/67498) |
| **P2/High** | Custom provider API key stored in plaintext; Save discards discovered models. | **Fixed** (PR #71141) | [#69449](https://github.com/NousResearch/hermes-agent/issues/69449) |
| **P2/High** | Desktop spawns unbounded `serve` processes on reconnection (resource leak). | Open | [#58619](https://github.com/NousResearch/hermes-agent/issues/58619) |
| **P2/High** | Windows desktop crash ("This app can't run") after update. | Open | [#69179](https://github.com/NousResearch/hermes-agent/issues/69179) |
| **P2/High** | Docker build fails on Podman due to non-agnostic flags. | Open | [#62849](https://github.com/NousResearch/hermes-agent/issues/62849) |
| **P2/High** | Session fork API accepts path-traversal IDs (security risk). | **Fixed** (PR #71163) | N/A (Internal Fix) |
| **P3/Medium** | Desktop approval bar truncates multi-line diffs. | Open | [#61249](https://github.com/NousResearch/hermes-agent/issues/61249) |
| **P3/Medium** | `read_file` tool shows phantom empty line for files ending in newline. | Open | [#49451](https://github.com/NousResearch/hermes-agent/issues/49451) |

## 6. Feature Requests & Roadmap Signals
*   **Real-time TPS Display (#71131):** Users request a tokens-per-second indicator during generation to monitor performance. *Link: [Issue #71131](https://github.com/NousResearch/hermes-agent/issues/71131)*
*   **Multi-Host Computer Use (#71157):** Demand for controlling multiple remote desktops from a single Hermes instance. *Link: [Issue #71157](https://github.com/NousResearch/hermes-agent/issues/71157)*
*   **Discord Voice Channel Participation (#33683):** Proposal for bot to join voice channels, transcribe, and respond. *Link: [Issue #33683](https://github.com/NousResearch/hermes-agent/issues/33683)*
*   **Per-Session Auto-Injection of Skills (#26709):** Request to automatically inject specific skills on every new session start. *Link: [Issue #26709](https://github.com/NousResearch/hermes-agent/issues/26709)*

## 7. User Feedback Summary
*   **Pain Points:** Windows users are experiencing disproportionate instability with the Desktop app (crashes, process leaks, boot failures). Security-conscious users are alarmed by the plaintext storage of API keys in config files.
*   **Satisfaction:** Users appreciate the rapid response to the custom provider bugs and the addition of German localization. The introduction of interactive buttons in Mattermost and explicit slash commands in Discord is well-received.
*   **Use Cases:** Heavy usage of Telegram and Discord gateways, with increasing interest in local LLM integration (llama.cpp) and multi-platform orchestration.

## 8. Backlog Watch
Maintainers should prioritize attention on:
*   **Windows Desktop Stability:** The cluster of P1/P2 bugs related to Windows desktop crashes and process management suggests a systemic issue in the Electron wrapper or native bindings that needs immediate investigation. *Refs: [#60144](https://github.com/NousResearch/hermes-agent/issues/60144), [#58619](https://github.com/NousResearch/hermes-agent/issues/58619), [#69179](https://github.com/NousResearch/hermes-agent/issues/69179)*
*   **Telegram Connectivity:** The persistent hang issue despite previous workarounds indicates a deeper protocol or network handling problem. *Ref: [#67498](https://github.com/NousResearch/hermes-agent/issues/67498)*
*   **Podman Compatibility:** The Dockerfile fix is needed to support rootless and alternative container runtimes, which is important for Linux server deployments. *Ref: [#62849](https://github.com/NousResearch/hermes-agent/issues/62849)*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest
**Date:** 2026-07-25
**Source:** github.com/sipeed/picoclaw

## 1. Today's Overview
PicoClaw demonstrates robust maintenance activity on July 25, 2026, with a high volume of Pull Requests (8 updates, 7 merged/closed) indicating active community contribution and code refinement. While no new releases were published, the integration of critical bug fixes and performance optimizations suggests the project is stabilizing its core infrastructure ahead of potential future releases. The repository remains healthy with consistent engagement from both maintainers and external contributors, particularly in areas of security hardening and internationalization.

## 2. Releases
**No new releases.**
The latest version referenced in user reports is v0.3.1. There are no new tags or changelogs generated in the last 24 hours.

## 3. Project Progress
Significant progress was made in code quality, security, and localization through the merging of seven PRs:
*   **Bug Fixes & UI Stability:** PR #3293 merged a fix for the high CPU usage issue in the chat interface input box, directly addressing a critical user experience bottleneck reported in Issue #3292.
*   **Security Hardening:** PR #3246 implemented essential security improvements, including enforcing TLS certificate verification for MQTT connections and fixing OAuth timeouts.
*   **Performance Optimization:** Three PRs by `corporatepiyush` (#3245, #3244, #3243) refactored the `seahorse` and `skills` packages to reduce memory allocations and improve string processing efficiency using `strings.NewReplacer` and `strings.Builder`.
*   **Internationalization:** PR #3261 added Traditional Chinese (zh-TW) locale support, and PR #3247 completed Czech translations for code wrap options.
*   **Discord Channel Reliability:** PR #323 addressed Discord message length limits and typing status, improving reliability for long-form interactions.

## 4. Community Hot Topics
*   **QQ Channel Streaming Support:** [Issue #3201](https://github.com/sipeed/picoclaw/issues/3201) remains a key feature request. Users are eager for real-time token-by-token output in QQ channels, matching the functionality already available in Telegram and WebSocket channels. Although closed as stale, the underlying demand for parity across channels persists.
*   **Localization Expansion:** The merge of zh-TW (PR #3261) and Czech (PR #3247) translations highlights a growing community desire for diverse language support. This signals that PicoClaw is gaining traction in non-English speaking markets.
*   **Underlying Needs:** The community is prioritizing **performance stability** (CPU usage, memory allocation) and **channel parity** (streaming support). Users expect enterprise-grade reliability (security fixes) alongside consumer-friendly features (streaming, localizations).

## 5. Bugs & Stability
*   **High CPU Usage in Chat Input (Critical):** [Issue #3292](https://github.com/sipeed/picoclaw/issues/3292) reported excessive CPU consumption when focusing on the input box in Firefox on Linux. This has been resolved via the merged [PR #3293](https://github.com/sipeed/picoclaw/pull/3293).
*   **MQTT Security Risk (Resolved):** [PR #3246](https://github.com/sipeed/picoclaw/pull/3246) fixed a hardcoded `InsecureSkipVerify: true` in MQTT connections, which previously exposed users to man-in-the-middle attacks. This is a critical stability/security fix now merged.
*   **Discord Message Limits:** [PR #323](https://github.com/sipeed/picoclaw/pull/323) addressed 400 errors caused by message length limits, improving stability for Discord bot interactions.

## 6. Feature Requests & Roadmap Signals
*   **Streaming Output for All Channels:** The repeated mention of streaming support in Issue #3201 suggests that extending `StreamingCapable` interfaces to all supported channels (QQ, WeChat, etc.) is a likely candidate for the next minor release.
*   **Enhanced Localization:** With zh-TW and Czech now merged, further expansion into other Asian or European languages may be expected if community contributions continue at this rate.
*   **Performance Tuning:** The focus on reducing allocations in recent PRs indicates a roadmap direction toward optimizing the Go runtime footprint, potentially benefiting low-resource deployments.

## 7. User Feedback Summary
*   **Satisfaction:** Users appreciate the rapid response to security vulnerabilities (MQTT TLS) and performance bugs (CPU usage). The inclusion of detailed environment data in Issue #3292 shows a mature user base providing actionable feedback.
*   **Pain Points:** The primary pain point was the UI-induced CPU spike, which has now been mitigated. Another lingering frustration is the lack of parity in advanced features (like streaming) across different messaging platforms.
*   **Use Cases:** Users are actively deploying PicoClaw in production environments using deep learning models (e.g., deepseek-v4-flash) on Linux servers, requiring stable web interfaces and secure channel integrations.

## 8. Backlog Watch
*   **QQ Streaming Parity:** While Issue #3201 is marked closed/stale, the feature gap between Telegram/WebSocket and QQ channels remains. Maintainers should monitor for renewed interest or community PRs targeting this specific capability.
*   **Stale PRs:** Several PRs (#3261, #3247, #3246, #3245, #3244, #3243) were marked "[stale]" before merging or closing. This suggests a need for better triage automation to prevent contributor burnout due to lack of timely maintainer interaction.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest
**Date:** 2026-07-25
**Source:** github.com/qwibitai/nanoclaw

## 1. Today's Overview
The NanoClaw project demonstrates high development velocity with seven Pull Requests updated in the last 24 hours, indicating active core team engagement despite zero new issues or releases today. The primary focus remains on stabilizing core agent execution flows, improving compatibility with open-source frameworks like OpenCode, and refining user interface feedback mechanisms. While no new versions were deployed, the volume of merged and open PRs suggests imminent release preparation. Activity is heavily concentrated on backend logic fixes and configuration enhancements rather than new feature additions.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Project Progress
**Merged/Closed PRs:**
*   **#3123 [CLOSED]:** "Pacific changes. Wrong PR." (Author: iamarunkumark) - This PR was closed immediately upon creation, likely due to being submitted to the wrong repository or branch. It does not reflect functional progress.

**Open PRs Advancing Functionality:**
*   **#3126:** Fixes a critical agent runner behavior where "silence" was incorrectly delivered during nudged chat turns, ensuring proper state handling.
*   **#3122:** Enhances `opencode` compatibility by addressing main compatibility, custom-endpoint transport, and memory parity, broadening integration capabilities.
*   **#3125:** Introduces a significant configuration feature: per-agent-group timezone overrides, allowing granular scheduling control via CLI (`ncl groups config update --timezone`).
*   **#3093:** Improves UX by keeping the "typing" indicator active during processing turns, reducing perceived latency for users.
*   **#3090:** Fixes template rendering by ensuring all top-level context Markdown is prepended correctly, stabilizing prompt construction.

## 4. Community Hot Topics
There are no open issues with high comment/reaction counts today. However, the following PRs indicate strong community or core-team interest based on recent updates:

*   **PR #3122 (OpenCode Compatibility):** High relevance for developers integrating NanoClaw with local/open-source LLM setups. The focus on "memory parity" and "custom-endpoint transport" addresses common pain points in hybrid AI environments.
    *   Link: [nanocoai/nanoclaw PR #3122](https://github.com/nanocoai/nanoclaw/pull/3122)
*   **PR #3125 (Timezone Overrides):** Represents a specific operational need for distributed teams managing agent groups across different regions.
    *   Link: [nanocoai/nanoclaw PR #3125](https://github.com/nanocoai/nanoclaw/pull/3125)

## 5. Bugs & Stability
Several bug fixes are currently under review, indicating ongoing stability improvements:

1.  **Agent Runner Silence Delivery (#3126):** *Severity: High.* Incorrect silence delivery in nudged turns could break automation workflows. Fix is open.
2.  **Typing Indicator Latency (#3093):** *Severity: Medium.* Users experienced false "idle" states during processing. Fix is open.
3.  **Template Context Prepending (#3090):** *Severity: Medium.* Incorrect markdown prepending could lead to malformed prompts or lost context. Fix is open.
4.  **Unavailable MCP Servers Reporting (#3124):** *Severity: Low/Medium.* Improves observability by explicitly reporting when MCP servers are unreachable. Fix is open.

## 6. Feature Requests & Roadmap Signals
*   **Granular Timezone Management:** PR #3125 signals a roadmap direction towards more sophisticated scheduling and localization features for agent groups.
*   **Enhanced Integrations:** PR #3122 indicates continued investment in interoperability with non-standard or open-source endpoints (OpenCode), suggesting future support for diverse LLM backends.

## 7. User Feedback Summary
Direct user feedback is low today (0 new issues). However, the nature of the fixes implies recent user pain points:
*   **Perceived Lag:** The fix for typing indicators (#3093) suggests users were frustrated by UI lag during AI processing.
*   **Configuration Complexity:** The introduction of timezone overrides (#3125) implies users needed more precise control over agent schedules without global changes.
*   **Integration Friction:** Fixes related to OpenCode and MCP server reporting suggest users encountered connectivity or compatibility hurdles.

## 8. Backlog Watch
*   **PR #3123:** Closed erroneously; no action needed unless re-submitted correctly.
*   **Pending Reviews:** Six PRs remain open (#3126, #3122, #3125, #3093, #3124, #3090). Maintainers should prioritize reviewing these to unblock potential next-cycle releases. No long-unanswered issues are present in the current snapshot.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest: 2026-07-25

## 1. Today's Overview
IronClaw is experiencing high-velocity development activity with 32 issues and 50 pull requests updated in the last 24 hours, indicating intense focus on stabilizing the v1 launch. The primary effort is directed toward rigorous bug bash exercises on staging environments (Railway/agent-stg) and refining the WebUI’s performance and accessibility. While no new official releases were published today, several critical infrastructure and security PRs were merged or closed, signaling readiness for the upcoming `v1.0.0` milestone. The project health is characterized by a transition from feature exploration to hardening, with significant attention paid to error recoverability and tool reliability.

## 2. Releases
**No new releases published today.**

However, **PR #5598** indicates recent internal version bumps for core libraries:
*   `ironclaw_common`: 0.4.2 -> 0.5.0 (**Breaking API Changes**)
*   `ironclaw_skills`: 0.3.0 -> 0.4.0 (**Breaking API Changes**)
*   `ironclaw_safety`: 0.2.2 -> 0.2.3 (API Compatible)

*Note: Developers should review PR #5598 for migration details regarding `failure copy_impl_added` type changes.*

## 3. Project Progress
Significant advancements were made in infrastructure, testing, and UI stability today:

*   **Infrastructure & CI:**
    *   **PR #6663** [CLOSED] Defaulted `cargo run` to serve the WebUI, streamlining local development.
    *   **PR #6616** [CLOSED] Shrank the composition extension host and retired product workflow facades, moving generic host behavior to `ironclaw_extension_host`.
    *   **Issue #6635** highlights ongoing efforts to restore Docker image builds in the CI pipeline.
*   **Testing & Reliability:**
    *   **PR #6659** [OPEN] Advanced trace replay precision by binding results to exact tool calls using RFC 6901 JSON Pointers.
    *   **PR #6665** [OPEN] Enhanced capability failure diagnostics to be actionable for the model, introducing a typed `ModelDiagnostic` contract.
    *   **PR #6664** [CLOSED] Fixed e2e test counting logic to measure capability coverage per outcome rather than per capability, ensuring accurate test validity.
*   **WebUI Improvements:**
    *   **PR #6625** [OPEN] Localized chat failure messages across all 11 supported locales.
    *   **PR #6624** [OPEN] Fixed keyboard accessibility in the extension configuration modal by trapping and restoring focus.
    *   **PR #6626** [OPEN] Improved UX by preserving automation list state during filter changes.

## 4. Community Hot Topics
The following items generated the most discussion or represent critical architectural shifts:

*   **[EPIC] Error Recoverability Endgame (#6284)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6284
    *   *Analysis:* This is the highest-priority epic, aiming for 100% model recoverability from mid-run errors. It defines a strict contract where the model must see the cause, the success path, and get a turn to act. This underpins the entire "Reborn" architecture's reliability claims.
*   **[EPIC] Hermetic Capability Testing Platform (#6524)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6524
    *   *Analysis:* Addresses the mechanical verification of deterministic coverage for every critical user journey, moving beyond recorded fixtures to ensure robustness.
*   **[EPIC] Reliable Skill Discovery, Routing, and Activation (#6565)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6565
    *   *Analysis:* Critical for agent utility; focuses on ensuring the agent correctly identifies and activates the best skill for a task, addressing previous gaps in the auto-activation pipeline.
*   **Skill Self-Creation Design Doc (#6641)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6641
    *   *Analysis:* Explores how agents can distill learned tasks into durable, reusable skills without human authoring, a key step towards autonomous agent evolution.

## 5. Bugs & Stability
A wave of bugs was reported today, primarily from bug bashes on staging instances (`gold-bee-karif` and Railway). Severity is rated P1 (Critical) for data loss or functional failure.

*   **P1: Slack DM Delivery Failure (#6645)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6645
    *   *Issue:* Agent reports success, but user never receives DM.
*   **P1: Telegram Message Processing Hang (#6643)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6643
    *   *Issue:* Messages accepted after pairing are never processed.
*   **P1: Telegram Reply Misrouting (#6644)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6644
    *   *Issue:* Replies delivered to wrong user messages.
*   **P2: Tool Execution UI Latency (#6649)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6649
    *   *Issue:* Tool activity panel appears after response, not during execution.
*   **P2: Data Loss in Google Sheets (#6646)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6646
    *   *Issue:* Agent ignores sheet action, only summarizes email.
*   **P2: Duplicate Error Messages (#6648)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6648
    *   *Issue:* Tool failures display duplicated, inconsistent errors.
*   **P2: Stale Model List in CLI (#6642)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6642
    *   *Issue:* `ironclaw models list` shows old provider after TUI switch.
*   **Info: Fabricated AQI Data (#6650)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6650
    *   *Issue:* Agent hallucinates air quality data from mixed sources.
*   **Info: UI Question Duplication (#6651)** [OPEN]
    *   *Link:* https://github.com/nearai/ironclaw/issues/6651
    *   *Issue:* UI repeats user question text after assistant response.

*Fix Status:* Many of these are tracked under the `[v1-launch-checklist]` and `[bug_bash_P1/P2]` labels. Immediate fixes for UI/UX issues (like #6649, #6651) are likely candidates for the next patch release.

## 6. Feature Requests & Roadmap Signals
*   **Manifest V3 Migration (#6490) [CLOSED]:** The target schema and migration path for extensions (tools, channels, skills) have been defined. This signals that v1 will rely on this new extension surface.
*   **Pluggable Memory Providers (#6482) [CLOSED]:** Success achieved in making memory provider-neutral. Future versions will likely expose more granular control over memory backends (mem0, native, etc.).
*   **Docker Image Build Restoration (#6635):** Users and CI systems expect Docker images as part of the standard release cadence. Restoring this is a prerequisite for broader deployment adoption.
*   **WebUI Performance Optimization (#6628, #6631, #6630):** A suite of enhancements for bundle size, code splitting, and asset compression suggests the next release will feature a significantly faster WebUI load time.

## 7. User Feedback Summary
*   **Frustration with Tool Reliability:** Users are reporting significant dissatisfaction with tools failing silently (Slack, Telegram, Google Sheets). The disconnect between "tool success" status and actual outcome (no message sent, no data written) is a major pain point.
*   **UI/UX Clarity:** The duplication of question text (#6651) and delayed tool feedback (#6649) create a confusing experience. Users need real-time visibility into what the agent is doing.
*   **Configuration Gaps:** Issues like the missing Slack OAuth redirect URI configuration (#6544) and CLI unavailability on staging (#6521) indicate that the hosted environment setup is not yet fully polished for end-users.
*   **Localization Needs:** The identification of hard-coded English error messages (#6623) shows a demand for better internationalization support, which is being addressed via PR #6625.

## 8. Backlog Watch
*   **Slack OAuth Binding Resolution (#6614) [CLOSED]:** While closed, the underlying issue of persistent binding states needs monitoring to ensure it doesn't regress in production.
*   **Version Upgrade Safety (#6656) [CLOSED]:** Disabling upgrades for pre-v1.0.0 versions is a temporary safety measure. Maintainers should monitor for user confusion regarding this restriction.
*   **Process Journal Kernel (#6666) [OPEN]:** Moving the process journal kernel to `ironclaw_processes` is a structural change that requires careful review to ensure no disruption to the turn-run lifecycle.
*   **Daily Failure Taxonomy (#6633) [OPEN]:** This issue tracks automated analysis of daily failures (e.g., pinchbench). It serves as a critical health metric dashboard for the team and should be kept active.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest
**Date:** 2026-07-25
**Source:** GitHub (netease-youdao/LobsterAI)

## 1. Today's Overview
The LobsterAI project remains highly active with 19 open issues and 8 pull requests updated in the last 24 hours, indicating sustained community engagement despite a significant backlog of stale tickets. The primary focus today is on stability improvements within the "Cowork" module, specifically regarding model timeouts and session handling, as well as critical security hardening of IPC channels and log sanitization. While new feature development continues with support for Kimi K3 and LiteLLM integration, the high volume of unresolved bugs related to AI engine connectivity and UI rendering suggests that stability and user experience refinement are currently the most pressing needs for the maintainers.

## 2. Releases
**Version:** LobsterAI 2026.7.23 (Released 2026-07-23)

*   **What's Changed:**
    *   **Feat (Skin):** Improved the AI skin creation flow for better usability (`PR #2361`).
    *   **Feat (Cowork):** Added support for multiple annotation attachments in browser contexts (`PR #2366`).
    *   **Feat (Build):** Added explicit channel entry points for Wind environment integration.
*   **Migration Notes:** No breaking changes reported in this release. Users should ensure their OpenClaw runtime is compatible with the latest build scripts if running locally.

## 3. Project Progress
*   **Merged/Closed PRs:**
    *   `PR #2382` [CLOSED]: Fixed Cowork model timeout handling. The server timeout was set to 330 seconds, and the client now distinguishes between network failures and long-running model responses, providing local hints after 30 seconds of inactivity.
*   **In-Progress Features:**
    *   `PR #2381`: Adds support for the **Kimi K3** model.
    *   `PR #2193`: Introduces **LiteLLM** as an AI gateway provider, allowing users to access 100+ LLM providers via a single OpenAI-compatible endpoint without adding new dependencies.

## 4. Community Hot Topics
*   **Security Hardening & Privacy:**
    *   **PRs #1831, #1832, #1833:** These PRs address critical security vulnerabilities involving sensitive data leakage in logs, unrestricted IPC store access, and unsafe URL schemes (`file://`, `javascript://`).
    *   **Analysis:** The community is increasingly concerned with data privacy and application security. The maintainer `kayo5994` has been actively addressing these systemic risks, which likely impact trust and compliance.
*   **OpenClaw Architecture Critique:**
    *   **Issue #2040:** A detailed analysis of "Five Weaknesses of OpenClaw," highlighting memory loss, security vulnerabilities, token cost失控, deployment complexity, and evolution bottlenecks.
    *   **Issue #2041:** Discussion on memory systems being the biggest bottleneck rather than evolution algorithms.
    *   **Analysis:** Advanced users are providing deep architectural feedback, suggesting that future roadmap items may need to prioritize persistent memory management and cost-effective model routing.

## 5. Bugs & Stability
*   **High Severity:**
    *   **Issue #1993:** "AI engine connection lost issue" on desktop app (stable on IM Bot). This affects core functionality for desktop users.
    *   **Issue #1988:** Ali Bailian Coding Plan fails to call `qwen3.6-plus`, forcing fallback to NetEase internal models with quota errors. Configuration overrides are ignored.
    *   **Issue #1813:** DeepSeek V4 LLM request failures due to schema/tool payload rejection.
*   **Medium Severity:**
    *   **Issue #1796:** Write/Edit tools consistently failing.
    *   **Issue #1849:** Infinite `NO_REPLY` or truncated outputs during follow-up questions due to task completion mismatch.
    *   **Issue #1971:** Scroll anomalies in chat sessions with large elements (e.g., Mermaid diagrams) due to virtualization bugs.
*   **Fix Status:**
    *   `PR #2382` addresses timeout issues related to `PR #1849` behavior but does not fully resolve the root cause of premature task completion.
    *   No immediate fixes visible for the Desktop Connection Loss (#1993) or Write Tool failures (#1796).

## 6. Feature Requests & Roadmap Signals
*   **Model Support:**
    *   **Issue #1813 / PR #2381:** Demand for broader model compatibility, specifically DeepSeek V4 and Kimi K3.
*   **UI/UX Improvements:**
    *   **Issue #1920 / #1921:** Requests for skeleton loading screens instead of plain text "Loading..." and improved empty states for Skills Manager/Task History.
    *   **Issue #1836:** General request for professional UI redesign to compete with other products.
*   **Agent Functionality:**
    *   **Issue #1880:** Request to integrate **Hermes Agent** similar to Open WebUI.
    *   **Issue #2036:** Proposal to add `agent:turn` or `agent:loop` events to OpenClaw gateway for real-time logging/persistence.
    *   **Issue #2016:** Request to add **OpenHuman** engine support.
*   **Prediction:** Next releases will likely prioritize **LiteLLM integration** (currently in PR) and **security patches**. UI skeleton updates (#1920) are small wins likely to be merged soon. Complex agent integrations (Hermes/OpenHuman) may remain in backlog due to architectural complexity.

## 7. User Feedback Summary
*   **Pain Points:**
    *   **Configuration Rigidity:** Users report that the app forces specific models (NetEase internal) even when using external plans like Ali Bailian, ignoring config files (`Issue #1988`).
    *   **Desktop Instability:** The desktop app suffers from connection drops and tool execution failures (`Issue #1993`, `#1796`), whereas the IM Bot version is more stable.
    *   **UX Friction:** Path traversal vulnerabilities in email skills (`Issue #1885`) and lack of batch delete for conversations (`Issue #1797`) frustrate power users.
*   **Satisfaction:**
    *   Positive reception for recent Cowork improvements (multi-annotation, skin flow).
    *   High interest in the ability to customize AI gateways (LiteLLM) to reduce costs and increase flexibility.

## 8. Backlog Watch
*   **Critical Security Issues:**
    *   **Issue #1885:** Email SKILL path traversal vulnerability. Requires immediate patching to prevent local file access.
    *   **PRs #1831-#1833:** These security fixes have been open since April 2026. Their prolonged status suggests they require careful review or are blocked by dependency conflicts.
*   **Long-Standing Functional Bugs:**
    *   **Issue #1878:** WeChat IM QR code login input failure. Critical for IM bot users.
    *   **Issue #2017:** Local runtime detection failure ("cfmind not detected"). Blocks local development and self-hosting.
*   **Architectural Discussions:**
    *   **Issues #2036, #2040, #2041:** These are not bugs but high-level architectural critiques. Maintainers need to decide whether to accept upstream changes to OpenClaw or implement workarounds in LobsterAI.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest
**Date:** 2026-07-25
**Source:** GitHub (moltis-org/moltis)

## 1. Today's Overview
The Moltis project is currently in a state of low-issue activity with zero new or closed issues reported in the last 24 hours. Development momentum is focused entirely on three open Pull Requests, all authored by `penso`, indicating a concentrated effort on Slack integration improvements and documentation policy enforcement. There are no new releases deployed today, suggesting the team is prioritizing code review and validation over versioning at this moment. The absence of closed PRs implies that these changes are still undergoing review or waiting for final approval before merging.

## 2. Releases
No new releases were published on 2026-07-25.

## 3. Project Progress
Three Pull Requests are currently open and under review:
*   **PR #1167 [docs]:** Introduces a policy update to forbid Claude session URLs in commits and PR descriptions. This is a documentation-only change aimed at cleaning up commit history and preventing sensitive AI session links from appearing in public logs.
*   **PR #1166 [feat(slack)]:** Implements significant enhancements to the Slack integration, including phase reactions, reconnection supervision, Block Kit support, and a critical bug fix for premature acknowledgments. This PR builds upon the work in #1165.
*   **PR #1165 [feat(slack)]:** Adds Slack acknowledgment reactions and inbound reaction triggers to address the lack of user feedback signals when bots are processing messages. It also fixes a confirmed bug regarding wrong-message threaded replies.

## 4. Community Hot Topics
*   **Slack Integration Maturity (PR #1165 & #1166):** Both high-priority PRs focus on improving the user experience within Slack. The underlying need is clear: users require better feedback mechanisms (reactions) to know their messages are being processed, as Slack bots cannot display typing indicators. Additionally, fixing "wrong-message" bugs in threads is critical for reliability.
    *   [PR #1165](https://github.com/moltis-org/moltis/pull/1165)
    *   [PR #1166](https://github.com/moltis-org/moltis/pull/1166)
*   **Commit Hygiene (PR #1167):** The proposal to ban AI session URLs suggests community or maintainer concern about data privacy or log cleanliness in collaborative workflows.
    *   [PR #1167](https://github.com/moltis-org/moltis/pull/1167)

## 5. Bugs & Stability
*   **Premature Ack Bug (PR #1166):** A bug where `chat.send` returns immediately after spawning an agent run, potentially causing race conditions or incorrect UI states, is being addressed in this PR.
*   **Wrong-Message Thread Reply (PR #1165):** A confirmed issue where threaded replies might be associated with incorrect parent messages is being fixed.
*   **Severity:** These are functional bugs affecting core interaction reliability but do not appear to cause crashes or regressions in stability. No new bug reports were filed today.

## 6. Feature Requests & Roadmap Signals
*   **Enhanced Slack UX:** The focus on "phase reactions," "Block Kit," and "reconnection supervision" indicates a roadmap priority to make the Slack bot more robust and user-friendly. The explicit mention of drawing ideas from `openclaw/hermes` suggests competitive benchmarking is driving these feature additions.
*   **Policy Enforcement:** The introduction of stricter rules for commit metadata (forbidding AI session links) signals a shift towards more disciplined contribution guidelines, possibly in response to increased adoption or external audits.

## 7. User Feedback Summary
*   **Pain Points:** Users have identified the lack of immediate feedback in Slack interactions as a major usability gap. The inability to see a "typing" indicator leads to uncertainty about whether the bot has received a message.
*   **Satisfaction:** The proactive development of reaction-based acknowledgments addresses this specific pain point directly. However, the presence of bugs like "wrong-message" replies in threads suggests that while features are being added, quality assurance in complex threading scenarios needs improvement.

## 8. Backlog Watch
*   **Open PRs Requiring Review:** All three current PRs (#1165, #1166, #1167) are open and awaiting merge. Maintainers should prioritize reviewing PR #1165 and #1166 due to their impact on core functionality and bug fixes. PR #1167 is non-critical but important for long-term hygiene.
*   **No Stale Issues:** There are no long-unanswered issues reported in the last 24 hours, indicating a healthy, albeit quiet, issue tracker.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest
**Date:** 2026-07-25
**Source:** agentscope-ai/CoPaw (GitHub)

## 1. Today's Overview
CoPaw is experiencing high development velocity with **45 issues** and **30 PRs** updated in the last 24 hours, indicating a period of rapid iteration and stabilization following the v2.0 release. The project has released **v2.0.1**, introducing the new **PawApp Platform** and Kanban integration, while actively addressing critical performance regressions and memory isolation bugs reported in v2.0.0. Community engagement is intense, particularly around session history integrity, MCP tool stability, and cross-agent privacy, suggesting that users are moving from initial setup to complex, multi-agent workflows. Maintainers are prioritizing backend reliability (SQLite persistence) and frontend UX improvements.

## 2. Releases
### v2.0.1 (Stable)
*   **Key Feature:** Introduction of the **PawApp SDK & Kanban App**. This allows plugins to build rich interactive UIs on top of QwenPaw, shipping with a built-in task board for project management.
*   **Impact:** Expands the ecosystem beyond simple chat interfaces, enabling more complex agent interactions and dashboarding within the client.
*   **Migration:** No breaking changes noted for existing agent configurations; this is an additive feature set.

### v2.0.1-beta.3 (Pre-release)
*   **Performance:** Stabilized chat options memoization and reduced Server-Sent Events (SSE) re-parsing overhead.
*   **Chore:** Version bump and date updates for the v2.0.1 release cycle.

## 3. Project Progress
Several significant technical advancements were merged or advanced today:

*   **History & Persistence Stability:**
    *   **PR #6459:** Hardened SQLite persistence, backup, and restore mechanisms to handle concurrent writes and WAL lifecycle issues.
    *   **PR #6323:** Implemented staged compaction and durable task continuity for Scroll context management, ensuring `history.db` remains the source of truth.
*   **Third-Party Agent Integration:**
    *   **PR #6397:** Integrated Codex, Qoder, Skills, and MCP into an extensible backend-neutral architecture, allowing third-party-backed agents to work across Chat and existing channels.
*   **Desktop Automation:**
    *   **PR #6424:** Added native desktop GUI automation (`computer_use`) for Windows and macOS, allowing agents to operate host applications via accessibility trees.
*   **Browser Control:**
    *   **PR #6276:** Unified browser control behind a single SDK with a control-plane/execution-plane split for better modularity.
*   **Channel Support:**
    *   **PR #6118:** Added built-in Zalo Bot channel support using long-polling.
    *   **PR #6387:** Enabled on-demand installation and version repair for Channel SDKs.

## 4. Community Hot Topics
The most commented and active discussions reveal deep user concerns regarding data integrity and workflow complexity:

*   **Session History Overwrite Bug:**
    *   **Issue #6401:** Users report that scheduled tasks (`cron`) sharing sessions overwrite historical records. *(Link: [Issue #6401](https://github.com/agentscope-ai/QwenPaw/issues/6401))*
    *   *Analysis:* Critical regression affecting automated workflows.
*   **Performance Regression in v2.0:**
    *   **Issue #6307:** Users note a fixed ~2s overhead per reply in v2.0 compared to v1.x, attributed to architectural changes in request handling. *(Link: [Issue #6307](https://github.com/agentscope-ai/QwenPaw/issues/6307))*
    *   *Analysis:* Performance drop is a major friction point for daily users.
*   **Missing Features in Upgrade:**
    *   **Issue #5980:** SSH Offline access and Profiles returning 404 errors after upgrading from v1.1.12 to v2.0.0. *(Link: [Issue #5980](https://github.com/agentscope-ai/QwenPaw/issues/5980))*
    *   *Analysis:* Indicates incomplete migration paths or deprecated features without clear alternatives.
*   **Cross-Agent Privacy Leaks:**
    *   **Issue #6461:** Users report that agents bound to different bots (e.g., QQ personal vs. group) can see each other's memories and settings. *(Link: [Issue #6461](https://github.com/agentscope-ai/QwenPaw/issues/6461))*
    *   *Analysis:* Highlights a security/isolation gap in multi-agent deployments.
*   **MCP Tool Instability:**
    *   **Issue #6405 & #2999:** Recurring reports of "Tool not found" errors and `CancelledError` due to slow MCP server responses during tool list retrieval. *(Links: [Issue #6405](https://github.com/agentscope-ai/QwenPaw/issues/6405), [Issue #2999](https://github.com/agentscope-ai/QwenPaw/issues/2999))*

## 5. Bugs & Stability
Ranked by severity and impact:

1.  **High Severity: Session Data Loss**
    *   **Bug:** Scheduled tasks overwriting active user session history.
    *   **Status:** Open ([#6401](https://github.com/agentscope-ai/QwenPaw/issues/6401)).
    *   **Note:** Directly contradicts user trust in data persistence.
2.  **Medium Severity: Performance Regression**
    *   **Bug:** ~2s fixed latency added to every response in v2.0.
    *   **Status:** Open ([#6307](https://github.com/agentscope-ai/QwenPaw/issues/6307)).
3.  **Medium Severity: Cross-Agent Isolation Failure**
    *   **Bug:** Agents sharing memory/settings when they should be isolated.
    *   **Status:** Open ([#6461](https://github.com/agentscope-ai/QwenPaw/issues/6461)).
4.  **Low-Medium Severity: UI/UX Friction**
    *   **Bug:** CPU spikes in Edge+Wayland environments with large result sets ([#6460](https://github.com/agentscope-ai/QwenPaw/issues/6460)).
    *   **Bug:** Cron task safety defaults are OFF, risking unintended tool execution ([#6458](https://github.com/agentscope-ai/QwenPaw/issues/6458)).
    *   **Bug:** Chinese filenames causing display issues in upload prompts ([#6453](https://github.com/agentscope-ai/QwenPaw/issues/6453)).

## 6. Feature Requests & Roadmap Signals
Users are requesting features that enhance control, efficiency, and local-first capabilities:

*   **Undo/Edit Previous Messages:** Request for `/undo` command to revert previous turns, similar to Cherry Studio/ChatGPT ([#6408](https://github.com/agentscope-ai/QwenPaw/issues/6408)).
*   **Built-in RAG/Knowledge Base:** Drag-and-drop document support for automatic agent retrieval ([#6432](https://github.com/agentscope-ai/QwenPaw/issues/6432)).
*   **Multi-Model Parallel Execution:** Ability to run multiple models independently on the same task and aggregate results ([#6455](https://github.com/agentscope-ai/QwenPaw/issues/6455)).
*   **Interactive Agent Tools:** `AskUserQuestion` tool for structured human-in-the-loop interactions ([#6384](https://github.com/agentscope-ai/QwenPaw/pull/6384) - PR Open).
*   **Visual Context Compression:** "Visual Compact" feature to selectively compress long histories while retaining recoverability ([#6456](https://github.com/agentscope-ai/QwenPaw/pull/6456) - PR Open).
*   **Workspace Checkpoints:** Git-like snapshotting for workspace recovery without modifying existing `.git` repos ([#6269](https://github.com/agentscope-ai/QwenPaw/pull/6269) - PR Open).

*Prediction:* The next patch version will likely focus on **session history fixes (#6401)** and **MCP stability (#2999/#6405)**. Major features like RAG and Multi-Model execution may appear in minor updates given the volume of requests.

## 7. User Feedback Summary
*   **Pain Points:**
    *   **Upgrade Friction:** Users upgrading from v1.x feel that critical features (SSH Offline, Profiles) are broken or missing (404s).
    *   **Privacy Concerns:** The lack of strict isolation between agents is causing anxiety among users deploying public-facing bots alongside private assistants.
    *   **UI Usability:** Right-click copy functionality is missing in chats, and error messages for non-multimodal models are considered too intrusive.
*   **Satisfaction:**
    *   The introduction of the **PawApp Platform** is well-received as it opens up extensibility.
    *   Users appreciate the move towards **lazy loading** and faster startup times (as seen in closed enhancement issues).
    *   The ability to use **third-party agents** (Codex/Qoder) within the same interface is a strong positive signal for power users.

## 8. Backlog Watch
Maintainers should prioritize attention on:

*   **Issue #2999:** Repeated MCP client registration leading to task cancellation. This is an old issue (April 2026) with persistent impact on stability.
*   **Issue #5980:** Missing features (SSH Offline, Profiles) in v2.0.0. This affects user retention during upgrades.
*   **Issue #6460:** High CPU usage on specific OS/Browser combinations (Edge + Wayland). This indicates a rendering or WebSocket optimization bug that needs profiling.
*   **PR #6459:** While fixing SQLite issues, ensure the solution fully addresses the "concurrent writes" problem mentioned in Issue #6401 to prevent further history loss.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

# ZeptoClaw Project Digest
**Date:** 2026-07-25

## 1. Today's Overview
ZeptoClaw demonstrated active development on July 24, focusing on both security hardening and user experience enhancements. The project addressed critical CI failures related to Rust toolchain updates and resolved a significant security vulnerability regarding subprocess secret leakage. Concurrently, the Telegram channel integration was advanced with a new feature for streaming agent responses via progressive message edits. Activity levels remain steady with two issues and two pull requests updated in the last 24 hours, indicating a healthy balance between maintenance and feature delivery.

## 2. Releases
No new releases were published during this period.

## 3. Project Progress
*   **Telegram Streaming Feature (Merged):** PR #648 was merged, implementing real-time response streaming for Telegram gateway sessions. This allows agents to progressively edit messages rather than sending static blocks, preserving routing logic and handling UTF-16 constraints safely.
*   **Security Hardening (Closed/Fixed):** PR #645 addressed a critical runtime security issue where shell commands inherited full process environments, potentially exposing provider keys. It also fixed process tree reaping for timed-out commands and Docker containers.

## 4. Community Hot Topics
*   **[Issue #646] CI Stability & Safety Checks** [Open]
    *   *Link:* https://github.com/qhkm/zeptoclaw/issues/646
    *   *Analysis:* This issue highlights the team's commitment to maintaining strict code quality and dependency safety. The exposure of vulnerabilities in `quick-xml` and `lopdf` by `cargo-deny` underscores the need for rigorous supply chain security in AI agent frameworks that may parse untrusted content.
*   **[PR #648] Telegram UX Improvement** [Closed/Merged]
    *   *Link:* https://github.com/qhkm/zeptoclaw/pull/648
    *   *Analysis:* The rapid progression from Issue #647 to PR #648 demonstrates an agile response to user demand for better real-time interaction capabilities in messaging channels.

## 5. Bugs & Stability
*   **Critical: Subprocess Secret Leakage (Fixed)**
    *   *Severity:* P1-Critical
    *   *Detail:* Runtime shell commands previously had access to the host environment, risking credential exposure.
    *   *Status:* Resolved in PR #645.
*   **High: Process Tree Orphaning (Fixed)**
    *   *Severity:* High
    *   *Detail:* Timed-out commands failed to consistently terminate child processes, leading to resource leaks.
    *   *Status:* Resolved in PR #645.
*   **Medium: CI Failures due to Toolchain Updates**
    *   *Severity:* Medium
    *   *Detail:* Rust 1.97.1 introduced new Clippy warnings and `cargo-deny` flagged vulnerable dependencies.
    *   *Status:* Tracked in Issue #646; fix is in progress.

## 6. Feature Requests & Roadmap Signals
*   **Real-Time Streaming for Messaging Channels:** The implementation of progressive message editing in Telegram suggests a roadmap direction toward more fluid, conversational interfaces across other supported channels. Users are clearly prioritizing latency and readability improvements over batch processing.

## 7. User Feedback Summary
*   **Pain Points:** Previous instability in subprocess management and potential security risks associated with environment variable inheritance were significant concerns.
*   **Satisfaction:** The successful merge of the Telegram streaming feature indicates high satisfaction with the responsiveness of the development team regarding user experience enhancements.

## 8. Backlog Watch
*   **CI Restoration (Issue #646):** While the immediate CI breakage caused by PR #645 is noted, the broader task of restoring `Clippy` and `cargo-deny` checks to pass on the current toolchain remains open. Maintainers should prioritize this to ensure long-term repository health and security compliance.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest
**Date:** 2026-07-25
**Source:** github.com/zeroclaw-labs/zeroclaw

## 1. Today's Overview
ZeroClaw is experiencing high development velocity with 45 active issues and 50 open pull requests tracked in the last 24 hours, indicating intense activity around security hardening and architectural unification. While no new releases were published today, the merge queue is active with 8 PRs closed/merged, focusing heavily on reliability fixes for Telegram, Cron, and Security subsystems. The project is currently balancing critical security patches (such as WhatsApp policy bypasses and Shell boundary bypasses) with long-term structural RFCs regarding plugin unification and work lane automation. Overall project health appears robust but requires careful attention to the high-risk security items currently in progress.

## 2. Releases
*   **No new releases** were published on 2026-07-25.
*   Current active version context: `0.8.3` (referenced in Issue #9290).

## 3. Project Progress
**Merged/Closed Pull Requests (Last 24h):**
*   **#9305 [CLOSED]**: Dependency update for `anchore/sbom-action` to v0.24.0.
*   **#9344 [CLOSED]**: Maintainer action inventory updated to align with SBOM action v0.24.0.

**Key Advancements & Fixes:**
*   **Security Hardening**: Significant progress in closing SSRF and sandbox bypass vectors. PR #8713 adds host classification for `file_download`, and PR #9114 relaxes Landlock sandbox restrictions that were blocking legitimate device/file access (related to Issue #9204).
*   **Observability**: PR #9349 fixes a critical bug where per-turn cost was not reported in `AgentEnd` events, enabling accurate billing/monitoring.
*   **Cron Reliability**: PR #9350 introduces CLI flags for cron delivery targets, addressing the issue where CLI-created jobs silently discarded output (Issue #9340).
*   **Config Integrity**: PR #9351 surfaces unconfigured model context windows, preventing silent failures in downstream systems.

## 4. Community Hot Topics
*   **"Everything is a plugin" Architecture (Issue #6489)**: A major RFC discussing the collapse of separate Integrations and Plugins into a unified catalog. This reflects a community need for simplified extension management and reduced fragmentation between Wasmtime components and native tools.
*   **Work Lanes & Board Automation (Issue #6808)**: High engagement (14 comments) on governance and workflow efficiency. Users are seeking better triage mechanisms to handle the volume of incoming issues and PRs without manual maintainer overhead.
*   **AI-Assisted PR Review (Issue #9330)**: A new RFC proposing the use of CI results to trigger AI-assisted pre-reviews. This signals a desire to accelerate the review process while maintaining human oversight for risk-based approvals.
*   **WhatsApp Security Bypass (Issue #9348)**: Urgent discussion regarding a critical security flaw where business mode defaults to answering all DMs/groups due to empty allowlists being interpreted as "permit all."

## 5. Bugs & Stability
**Critical/High Severity Issues Reported or Active:**
*   **[S1] WhatsApp Web Policy Bypass (Issue #9348)**: *Open*. Configurations intended to lock down chat policies fail, allowing the agent to reply to all inbound messages. **Status**: Open, needs immediate fix.
*   **[S0] Shell Tool Workspace Boundary Bypass (Issue #9247)**: *Open*. Symlinks inside the workspace allow shell commands to read/write outside the designated boundary, posing a severe data loss/security risk. **Status**: Open.
*   **[S1] Landlock Sandbox Self-Lock (Issue #9204)**: *Closed/Fixed*. The daemon locked itself when executing shell commands under Landlock. **Fix**: PR #9114 addresses related sandbox restrictions.
*   **[S1] Shell Tool Calls Refused at Full Autonomy (Issue #6434)**: *Closed*. Tool dispatch never reached the runtime despite permissive config.
*   **[S3] Windows Desktop Installer Failure (Issue #9290)**: *Open*. Missing `TaskDialogIndirect` causes launch failure on Windows.
*   **[S2] Delegate Tool API Key Bleed (Issue #7623)**: *Closed*. Fixed forwarding of coordinator API keys to sub-agents.

**Notable Regressions/Fixes:**
*   **Config Alias Dropping (Issue #9236)**: *Closed*. Fresh Telegram aliases were dropped after config reload.
*   **Dirty Write Drops (Issue #9240)**: *Closed*. `save_dirty` failed to write map keys containing dots.

## 6. Feature Requests & Roadmap Signals
*   **Unified Plugin Catalog (Issue #6489)**: Strong signal towards v0.9.0 architecture where all integrations (channels, providers, tools) become part of a single plugin system.
*   **Wire Protocol First-Class Support (Issue #8396)**: RFC to treat wire protocols as primary entities in provider construction, simplifying onboarding for new providers.
*   **DingTalk Streaming Support (Issue #8228)**: Request to add streaming message support to reduce latency for DingTalk users.
*   **Crusoe Managed Inference Provider (PR #9338)**: New first-class support for Crusoe as an OpenAI-compatible provider family.
*   **Data-Wrapped OpenAI Responses (Issue #9335)**: Feature request to support responses wrapped in a top-level `data` object, improving compatibility with specific proxy endpoints.
*   **Scoped Secrets for Plugins (PR #8857)**: Enhancement to provide portable, encrypted secret management for plugins.

## 7. User Feedback Summary
*   **Pain Points**: Users are frustrated by silent failures in configuration handling (e.g., Issue #9240, #9236) and the inability to see output from CLI-created cron jobs (Issue #9340). The security implications of the WhatsApp and Shell bugs have caused significant concern among power users.
*   **Use Cases**: Heavy usage of multi-agent delegation (`delegate` tool) and complex goal-oriented workflows (`goal_start/resume`). There is a strong demand for observability improvements, specifically around cost tracking (Issue #9349) and context window visibility.
*   **Satisfaction**: The community appreciates the rapid response to security audits (SSRF fixes, Landlock adjustments) and the transparency of the RFC process. However, the complexity of the config system remains a barrier, as evidenced by multiple bugs related to alias resolution and map key parsing.

## 8. Backlog Watch
*   **Issue #6808 [RFC: Work Lanes]**: High comment count, stalled on implementation details. Needs maintainer decision on rollout strategy.
*   **Issue #6489 [Feature: Everything is a plugin]**: Critical architectural shift. Requires sustained maintainer attention to define the phased path from current integrations to the unified catalog.
*   **Issue #9348 [Bug: WhatsApp Web Answers Every DM]**: **Priority P1**. This is a security risk that could lead to unauthorized agent behavior. Requires immediate patch release or hotfix PR.
*   **Issue #9247 [Bug: Shell Tool Workspace Boundary Bypass]**: **Priority S0**. Critical security vulnerability. Needs immediate remediation PR.
*   **Issue #8519 [Audit: Reconcile cargo-audit ignores]**: Long-standing dependency hygiene issue. Needs maintainer review to close drift between `cargo audit` and `cargo deny`.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*