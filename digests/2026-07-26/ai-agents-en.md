# OpenClaw Ecosystem Digest 2026-07-26

> Issues: 349 | PRs: 500 | Projects covered: 12 | Generated: 2026-07-26 03:35 UTC

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

# OpenClaw Project Digest: 2026-07-26

## 1. Today's Overview
OpenClaw is experiencing high-velocity development with **500 PRs** and **349 issues** updated in the last 24 hours, indicating intense community engagement and rigorous maintenance cycles. While no new stable releases were published today, the project is actively addressing critical stability regressions from the recent `2026.7.1` rollout, particularly around session management and gateway startup failures. The maintainers are heavily focused on security hardening (MCP tool approvals, cron webhook restrictions) and performance optimization (SQLite cleanup, memory leaks), suggesting a transition phase from feature expansion to system hardening.

## 2. Releases
*   **No new stable releases.**
*   **Context:** The project is currently dealing with regressions introduced in `v2026.7.1` and `v2026.7.1-2`. Issues #108435 and #113466 highlight that the gateway fails to start and `/new`/`/reset` commands do not function correctly in these versions. A fix for the HTTP server listening issue (Issue #109145) was merged in PR #113999, but broader stability patches are likely pending in the next patch release.

## 3. Project Progress
Significant technical advancements and fixes were merged or advanced today:
*   **Security & Access Control:**
    *   **PR #113998:** Pinning cron webhook bearer tokens to operator-allowlisted hosts to prevent credential leakage.
    *   **PR #113517:** Implementing an external verification contract for approvals, enhancing auditability.
    *   **PR #113822:** Adding exact-profile provider usage reads to allow plugins to safely inspect quota data without crossing auth boundaries.
*   **Core Stability & Performance:**
    *   **PR #113999:** Fixed OpenAI live-test config isolation and Qianfan default refresh issues.
    *   **PR #114003:** Optimized `sessions.list` to stop materializing the store per row, addressing quadratic performance degradation.
    *   **PR #113471:** Fixed Memory Core to properly close previous embedding providers before replacement, preventing orphaned processes.
*   **User Experience (UX):**
    *   **PR #113883:** Introduced path-based session and dashboard URLs for better bookmarking and shareability.
    *   **PR #113965:** Added gateway picker with in-place switching for the macOS app.
    *   **PR #112863:** Enabled chat-based setup and account linking for Signal, reducing friction for new users.
    *   **PR #113945:** Restored prompt image attachments on rewind/fork actions in the web UI.

## 4. Community Hot Topics
The most discussed issues revolve around **security trust models**, **memory management chaos**, and **session state integrity**.

*   **Memory Trust Tagging by Source (#7707)** - *21 Comments*
    *   Users are demanding granular control over agent memory to prevent "memory poisoning" from untrusted sources like web scrapes. This reflects a growing need for enterprise-grade security in autonomous agents.
*   **Channel-mediated approval for MCP tool calls (#78308)** - *15 Comments*
    *   There is strong interest in extending the `/approve` pipeline to MCP tools, ensuring human-in-the-loop consent for state-changing external operations.
*   **SQLite Snapshot Restore Guarantees (#113306)** - *13 Comments*
    *   Critical concern regarding data durability. Users are reporting that snapshot restores may succeed without actually linking parent directories, risking data loss.
*   **Session Context Bloat (#67419)** - *10 Comments*
    *   Users are frustrated by bootstrap files re-injecting into every turn, wasting 20-30% of context windows. This is a major efficiency bottleneck for long-running sessions.
*   **Gateway Heap Growth on macOS (#87109)** - *10 Comments*
    *   A persistent memory leak causing idle heap growth to >1GB, leading to silent cron job failures due to event-loop starvation.

## 5. Bugs & Stability
Several P0/P1 bugs reported today indicate instability in the latest versions:

*   **P0: Gateway Fails to Start (#108435)**
    *   *Status:* Open. `openclaw 2026.7.1` gateway fails to start with errors.
    *   *Impact:* Blocks all users upgrading to this version.
*   **P0: HTTP Server Listens but Rejects Connections (#109145)**
    *   *Status:* PR #113999 addresses related config issues, but the specific socket acceptance bug remains a concern.
*   **P1: /new and /reset Don't Create New Sessions (#113466)**
    *   *Status:* Open. These commands only emit hooks but fail to perform the actual gateway session reset, leaving users stuck in previous contexts.
*   **P1: Large SQLite Transcript Cleanup Blocks Event Loop (#112423)**
    *   *Status:* Open. Archiving large transcripts causes significant latency, affecting real-time responsiveness.
*   **P1: Telegram Inbound Update Lost (#113315)**
    *   *Status:* Open. Updates acknowledged by offset persistence are never dispatched, causing permanent message loss.
*   **Regression: Email Channel Config Corruption (#95515)**
    *   *Status:* Open. Upgrading from 2026.6.8 to 6.9 corrupts config with spurious fields.

## 6. Feature Requests & Roadmap Signals
*   **Dynamic Model Discovery (#10687):** Users want fully dynamic model catalogs for providers like OpenRouter, moving away from static lists.
*   **Per-Spawn Tool Restrictions (#15032):** A request to restrict tools for sub-agents, crucial for building secure, isolated multi-agent pipelines.
*   **OpenRouter Cost Exposure (#9016):** Agents should be able to see and report usage costs from OpenRouter responses.
*   **Filesystem Sandboxing (#7722):** Continued demand for configurable file access restrictions (`tools.fileAccess`) to limit agent scope.
*   **Model Fallback on Context Exceeded (#9986):** Automatic fallback to smaller models when context limits are hit, rather than freezing/erroring.

## 7. User Feedback Summary
*   **Frustration with Recent Regressions:** Users are reporting significant dissatisfaction with `v2026.7.1`, citing startup failures and broken session commands. The lack of a hotfix release is causing operational disruptions.
*   **Memory Management Anxiety:** Multiple reports (#67419, #43747, #90414) describe inconsistent memory behavior, missing indexes, and bloat. Users feel the memory subsystem is unreliable for production use.
*   **Security Consciousness:** High engagement on security-related features (trust tagging, sandboxing, approval envelopes) shows users are prioritizing safety and are wary of autonomous agent capabilities without guardrails.
*   **Platform Specific Pain Points:** macOS memory leaks (#87109) and Telegram message loss (#113315, #91564) are specific, recurring pain points for dedicated user bases.

## 8. Backlog Watch
Maintainers should prioritize the following long-standing or critical items:
*   **#7707 [Feature] Memory Trust Tagging:** High demand, security-critical. Needs product decision.
*   **#67419 [Bug] Session Context Bloat:** Directly impacts cost and performance. Labeled `needs-product-decision`.
*   **#113306 [Bug] SQLite Snapshot Restore Integrity:** Data loss risk. Needs maintainer review and source repro.
*   **#87109 [Bug] Gateway Heap Growth:** Causes silent failures. Stale tag, but high impact.
*   **#45049 [Bug] Simulated Tool Calls:** Agent loop allows text-based simulation instead of real tool invocation. Security/stability risk.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Report: Personal AI Agents (2026-07-26)

## 1. Ecosystem Overview
The personal AI agent landscape in July 2026 is characterized by a shift from feature expansion to rigorous system hardening and security isolation. Projects are heavily focused on resolving critical stability regressions, particularly around session state integrity, memory management, and database concurrency. There is a clear industry-wide demand for enterprise-grade security features, including granular access controls, sandboxing, and verifiable intent chains, reflecting a maturation of use cases from casual chat to complex, multi-agent automation workflows.

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Release Status | Health Score* |
| :--- | :---: | :---: | :--- | :---: |
| **OpenClaw** | 349 | 500 | No new stable; fixing v2026.7.1 regressions | ⚠️ Critical (Stability) |
| **ZeroClaw** | 19 | 50 | Pre-release v0.8.4 imminent (July 31) | 🟢 High (Active Dev) |
| **Hermes Agent**| 50 | 50 | Stable; maintenance phase | 🟡 Moderate (Bug Fix) |
| **IronClaw** | 11 | 19 | No release; v1 checklist active | 🟢 High (Polishing) |
| **NanoBot** | N/A | 10 | v0.3.0 released; post-release stabilization | 🟢 Healthy |
| **LobsterAI** | 9 closed | 11 merged | Patch likely imminent | 🟢 Healthy |
| **CoPaw** | 7 | 7 | Stable v2.0.1; blocking bugs present | 🔴 At Risk (Bugs) |
| **NanoClaw** | N/A | 11 | Stable; security hardening focus | 🟢 Healthy |
| **Moltis** | 0 | 6 | Stable; interoperability focus | 🟢 Stable |
| **PicoClaw** | 2 | 4 | Stable; edge device focus | 🟡 Low Activity |
| **NullClaw** | 0 | 0 | No activity | ⚪ Stalled |
| **ZeptoClaw** | 0 | 0 | No activity | ⚪ Stalled |

*\*Health Score based on velocity, bug resolution rate, and community engagement intensity.*

## 3. OpenClaw's Position
OpenClaw dominates the ecosystem in terms of raw volume, with nearly 850 updates in 24 hours, indicating it is the most widely deployed or actively maintained project. Its primary advantage is its comprehensive feature set and large community base, but this comes at the cost of significant technical debt, evidenced by the severe regressions in `v2026.7.1`. Unlike competitors like NanoBot or LobsterAI, which are polishing specific UX or workflow aspects, OpenClaw is currently in a defensive posture, prioritizing core stability, session management, and security hardening over new feature introduction. Its technical approach is monolithic yet highly modular internally, relying heavily on SQLite and gateway architectures that require intensive optimization.

## 4. Shared Technical Focus Areas
Several critical technical themes are emerging across multiple projects, signaling industry-wide challenges:

*   **Session & State Integrity:**
    *   **Projects:** OpenClaw, Hermes Agent, NanoBot, CoPaw.
    *   **Need:** Robust handling of session resets, context bloat, and state persistence. Users are frustrated by lost context, broken `/reset` commands, and database corruption (SQLite WAL issues in Hermes/OpenClaw).
*   **Security Hardening & Sandboxing:**
    *   **Projects:** NanoClaw, IronClaw, ZeroClaw, OpenClaw.
    *   **Need:** Granular control over agent permissions. Specific demands include container isolation (`--cap-drop=ALL` in NanoClaw), verified intent chains (ZeroClaw), and MCP tool approval pipelines (OpenClaw/IronClaw).
*   **Memory Management & Cost Control:**
    *   **Projects:** OpenClaw, Hermes Agent, ZeroClaw.
    *   **Need:** Accurate cost reporting (Hermes under-reporting), memory leak prevention (OpenClaw macOS heap growth), and efficient context window usage (OpenClaw context bloat).
*   **Interoperability & Protocol Support:**
    *   **Projects:** Moltis, ZeroClaw, IronClaw.
    *   **Need:** Standardized communication protocols. Moltis is adopting ACP agent roles, while ZeroClaw and IronClaw are focusing on unified command pipelines and external API compatibility (OpenAI endpoints, Slack/Telegram native support).

## 5. Differentiation Analysis

*   **Target User & Use Case:**
    *   **OpenClaw/Hermes:** Enterprise/Power users requiring deep integration, multi-agent delegation, and complex backend infrastructure.
    *   **NanoBot/LobsterAI:** Mid-tier users focusing on ease of use, WebUI experience, and workflow automation (Cowork sessions).
    *   **Moltis/PicoClaw:** Niche/Edge users. Moltis targets decentralized/Nostr ecosystems and IDE integration; PicoClaw focuses on low-resource ARM devices.
    *   **ZeroClaw:** Security-focused developers interested in Rust-based, verifiable, and isolated agent deployments.

*   **Technical Architecture:**
    *   **Python/JS Heavy:** OpenClaw, Hermes, CoPaw, NanoBot. These rely on traditional web stacks and Python libraries, facing challenges with memory leaks and async concurrency.
    *   **Rust-Based:** ZeroClaw, IronClaw (partial). These prioritize performance, safety, and strict type checking, addressing memory safety and concurrency issues natively.
    *   **Hybrid/Modular:** NanoClaw uses Docker containers for isolation, while Moltis acts as an ACP agent, bridging different orchestration layers.

## 6. Community Momentum & Maturity

*   **High Velocity / Critical Phase:** **OpenClaw** and **ZeroClaw**. OpenClaw is scaling rapidly but struggling with stability; ZeroClaw is in a pre-release sprint with high commit frequency.
*   **Stable Maturation:** **Hermes Agent**, **IronClaw**, **NanoBot**. These projects have established user bases and are now focused on bug fixes, documentation, and incremental improvements (e.g., IronClaw’s WebUI polish, NanoBot’s CI/CD transparency).
*   **Niche/Steady Growth:** **Moltis**, **NanoClaw**, **LobsterAI**. Consistent development without massive volatility, focusing on specific integrations (Nostr/Slack for Moltis, Security for NanoClaw, UI for LobsterAI).
*   **Low Activity:** **PicoClaw**, **NullClaw**, **ZeptoClaw**. These projects show minimal recent engagement, suggesting they may be in maintenance mode or losing community traction.

## 7. Trend Signals

*   **From "Chat" to "Action":** The community is moving beyond conversational interfaces to actionable automation. Features like batch tool execution (LobsterAI), scheduled tasks (LobsterAI), and MCP tool approvals (OpenClaw) indicate a demand for agents that perform work, not just talk.
*   **Security as a First-Class Citizen:** The proliferation of security-focused PRs (NanoClaw’s container caps, ZeroClaw’s verifiable intents, OpenClaw’s trust tagging) shows that trust and safety are no longer afterthoughts but core requirements for production-ready agents.
*   **Standardization of Protocols:** The emergence of ACP (Agent Communication Protocol) in Moltis and standardized slash commands in IronClaw suggests the industry is converging on common interfaces to reduce fragmentation between different AI harnesses and clients.
*   **Performance Optimization at Scale:** With larger context windows and more complex multi-agent interactions, projects are prioritizing performance (code splitting in IronClaw, SQLite optimization in OpenClaw, Rust concurrency in ZeroClaw) to handle the computational load of autonomous agents.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest: 2026-07-26

## 1. Today's Overview
NanoBot is currently in a high-velocity post-release stabilization phase following the launch of v0.3.0, which significantly expanded agent agency and community contributions. The project demonstrates robust health with 10 PRs updated in the last 24 hours, indicating active maintenance and rapid iteration on core stability issues. While new feature development has paused to focus on bug fixes and documentation, the integration of comprehensive CI/CD pipelines marks a maturation in project governance. Community engagement remains steady, with contributors actively addressing critical path blockers in the WebUI and session management systems.

## 2. Releases
**v0.3.0** is the latest major release, marking a significant milestone for the project.
*   **Key Changes:** The release introduces enhanced agent "agency," allowing for more autonomous operation. It also includes a streamlined one-command setup (`nanobot webui`) that prepares the local WebUI, starts the gateway, and opens the browser workbench.
*   **Community Impact:** This version merged 260 PRs and welcomed 38 new contributors, reflecting substantial community growth.
*   **Migration Notes:** Compatibility cleanup tasks have been deferred to v0.3.1 (PR #5083), suggesting v0.3.0 is the final compatibility window for legacy patterns. Users should ensure they are using the latest CLI tools to avoid warnings regarding `agents.defaults.maxMessages`.

## 3. Project Progress
Today's activity is dominated by bug fixes, documentation clarifications, and infrastructure improvements rather than new features.
*   **Merged/Closed PRs:**
    *   **#1284:** Merged a comprehensive CI/CD pipeline including quality checks, coverage tools, and validation tests, significantly improving code reliability.
    *   **#5085:** Implemented logic to automatically open the WebUI after a fresh desktop install, enhancing user onboarding experience.
    *   **#4696:** Improved WebUI streaming performance by implementing state-driven viewport motion, ensuring smooth scrolling as content generates.
    *   **#5084 & #4954:** Fixed critical runtime context preservation and late subagent turn visibility issues, stabilizing complex multi-turn interactions.
    *   **#5082:** Clarified documentation for WebUI, gateway, and CLI quick starts, reducing user confusion around deployment modes.
    *   **#5081:** Prepared the release artifacts for v0.3.0.

## 4. Community Hot Topics
The most discussed topics revolve around the stability of the new v0.3.0 release and the clarity of development workflows.
*   **CI/CD Transparency:** Issue #1131 [CLOSED] highlighted initial confusion regarding automated testing enforcement. This was resolved by merging PR #1284, which established clear quality gates. *Link: [Issue #1131](https://github.com/HKUDS/nanobot/issues/1131)*
*   **WebUI UX Improvements:** PR #5085 and #4696 address specific pain points in the user interface, particularly regarding auto-launch behavior and scroll smoothness during streaming. *Link: [PR #5085](https://github.com/HKUDS/nanobot/pull/5085)*
*   **Session Routing Stability:** Multiple open PRs (#4928, #5084) focus on "unified sessions" and "heartbeat" routing, indicating that maintaining state across different channels and subagents is a current priority for developers. *Link: [PR #4928](https://github.com/HKUDS/nanobot/pull/4928)*

## 5. Bugs & Stability
Several critical bugs related to session management and UI rendering were addressed or remain under investigation.
*   **High Severity (Fixed/Merging):**
    *   **Heartbeat Routing:** PR #4928 addresses a bug where unified sessions were not correctly routed to the last active channel, potentially causing message loss or misdirection.
    *   **Runtime Context Loss:** PR #5084 fixes an issue where pending messages lost their runtime context (channel, chat ID, sender info) when queued mid-turn.
    *   **Subagent Visibility:** PR #4954 resolves a bug where late-arriving subagent turns were not visible in the WebUI, disrupting the conversation flow.
*   **Open Issues:**
    *   **Sandbox Bind Roots:** PR #4625 proposes a fix for users needing to expose local tool directories (e.g., `~/.local/bin`) within the `bwrap` sandbox. This suggests previous sandboxing was too restrictive for some advanced use cases. *Link: [PR #4625](https://github.com/HKUDS/nanobot/pull/4625)*

## 6. Feature Requests & Roadmap Signals
*   **Expanded Sandbox Configuration:** PR #4625 indicates a demand for more flexible sandbox configurations, specifically regarding bind roots for custom tool installations.
*   **Automated Onboarding:** The implementation of automatic WebUI opening upon fresh install (PR #5085) signals a roadmap commitment to reducing friction for new users.
*   **Performance Optimization:** The focus on "smooth streaming" (PR #4696) suggests future iterations will prioritize UI responsiveness and visual fidelity alongside functional correctness.

## 7. User Feedback Summary
User feedback, inferred from PR descriptions and issue discussions, highlights a need for smoother onboarding and more robust handling of complex, multi-agent conversations.
*   **Pain Points:** Previous lack of clarity on CI processes and difficulty in exposing local binaries within the sandbox environment were significant hurdles.
*   **Satisfaction:** The community appears satisfied with the increased transparency provided by the new CI/CD pipeline and the improved documentation.
*   **Use Cases:** Heavy usage of "unified sessions" and "subagents" suggests power users are leveraging NanoBot for complex, multi-step automation tasks that require precise state management.

## 8. Backlog Watch
*   **Sandbox Flexibility (PR #4625):** This PR remains open, addressing a limitation in the security sandbox that affects developers needing to integrate external tools. Maintainer attention is needed to review the security implications of configurable bind roots. *Link: [PR #4625](https://github.com/HKUDS/nanobot/pull/4625)*
*   **Heartbeat Logic (PR #4928):** Similarly, this PR is open and addresses critical routing logic for heartbeats in unified sessions. Its resolution is vital for ensuring reliable long-running agent interactions. *Link: [PR #4928](https://github.com/HKUDS/nanobot/pull/4928)*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest
**Date:** 2026-07-26
**Source:** NousResearch/hermes-agent

## 1. Today's Overview
The Hermes Agent project is experiencing a period of intense maintenance and stability refinement, with 50 issues and 50 pull requests updated in the last 24 hours. While no new releases were published today, the high volume of closed issues (12) and merged PRs (19) indicates active resolution of critical infrastructure bugs, particularly surrounding SQLite database integrity and authentication loops. The community focus has shifted from feature expansion to hardening the core agent runtime, session state management, and cost reporting accuracy.

## 2. Releases
No new releases were published today. The current focus remains on stabilizing the existing codebase before the next version bump.

## 3. Project Progress
Significant progress was made in fixing core infrastructure and tooling reliability:
*   **SQLite Stability:** Critical fixes were advanced regarding SQLite WAL-mode corruption. PR #71724 addresses POSIX lock cancellation causing `state.db` corruption, while PR #70200 migrates managed Python builds to fixed SQLite versions to resolve upstream WAL-reset bugs.
*   **Authentication & Gateway:** Multiple PRs addressed gateway boot loops and auth failures. PR #71722 fixes environment variable expansion in `model.default`, ensuring Telegram/Discord gateways correctly resolve model names. PR #71731 resolves a test suite crash caused by `os._exit` calls in gateway tests.
*   **Plugin & CLI Fixes:** PR #71729 ensures plugin discovery runs before toolset validation, preventing false "Unknown toolsets" warnings. PR #56485 restores pre-edit Ctrl+G behavior for better user control in the CLI editor.
*   **Delegation Features:** PR #71728 implements named delegation profiles, allowing agents to select specific credential bundles (model + endpoint) per call, addressing incoherent model/endpoint pairings.

## 4. Community Hot Topics
High-engagement discussions highlight key areas of concern and interest:
*   **Turn-Level Time Awareness (#10421):** With 13 comments and 9 👍, this feature request for live time context at the turn level is the most popular open issue. Users are seeking a stable sense of "now" without relying on explicit tool calls, crucial for temporal reasoning in daily tasks.
*   **SQLite Corruption & Concurrency (#34385, #53819, #69784):** A cluster of highly technical discussions surrounds Kanban DB corruption under concurrent worker loads. These issues reveal deep-seated problems with SQLite WAL modes and concurrent writes, driving significant developer attention.
*   **Nous Portal Caching Issues (#71576):** Reports of Anthropic models via Nous Portal suffering from low cache hit rates (39% vs 100% expected) indicate a routing/sticky-session bug that impacts cost and performance significantly.

## 5. Bugs & Stability
Several critical bugs were reported and partially resolved today:
*   **Critical: SQLite State Corruption:** Issues #34385, #53819, and #69784 detail severe data corruption in `kanban.db` and `state.db` due to concurrent SQLite writes and upstream WAL bugs. **Fixes:** PR #71724 and PR #70200 are directly addressing these root causes.
*   **High: Authentication Loops:** Issues #48434, #71514, and #71491 report Windows Desktop apps getting stuck in 401/loop states when connecting to remote gateways. **Fixes:** PR #71722 addresses env var resolution which may contribute to these auth failures.
*   **High: Cost Reporting Errors:** Issue #71242 identifies a bug where Anthropic auxiliary usage drops cache tokens, leading to ~7x under-reporting of MoA aggregator costs. This requires immediate attention for billing accuracy.
*   **Medium: Session Context Loss:** Issue #44028 reports Feishu quoted replies creating isolated threads, breaking conversation context. Issue #11515 highlights ACP session CWD inconsistencies affecting tool execution vs. context discovery.

## 6. Feature Requests & Roadmap Signals
*   **Named Delegation Profiles (#71727):** The introduction of named delegation profiles suggests a roadmap toward more granular control over subagent credentials and model selection, enhancing security and flexibility for complex multi-agent workflows.
*   **Live Time Context (#10421):** The strong community support for turn-level time awareness indicates a need for more robust temporal grounding in agent reasoning, likely to be prioritized in future updates.
*   **Claude Agent SDK Integration (#65982):** The ongoing work to integrate the official Claude Agent SDK as a first-class runtime signals an expansion of supported provider ecosystems beyond standard API wrappers.

## 7. User Feedback Summary
Users are expressing satisfaction with Hermes' capabilities but are frustrated by stability issues in production environments:
*   **Pain Points:** The most common complaints involve data loss/corruption (SQLite issues), broken authentication flows on Windows, and inaccurate cost reporting. Users like eaglezzz0522-cloud (#71418) provide valuable feedback on long-term session limits and resource accumulation.
*   **Use Cases:** Heavy usage of MCP servers, delegated agents, and cross-platform gateways (Telegram, Discord, Feishu) highlights Hermes' role in complex, integrated AI workflows.
*   **Satisfaction:** Despite bugs, users appreciate the depth of features (e.g., skills, delegation) and the responsiveness of the team in addressing high-severity issues like SQLite corruption.

## 8. Backlog Watch
*   **ACP Prompt Hanging (#39245):** An open P2 bug where ACP prompts hang after final text response if session updates fail. This affects developer experience and automation reliability.
*   **LSP Subprocess Reaping (#25016):** A long-standing P2 bug where idle LSP subprocesses are never reaped, leading to memory leaks (~200 MB per server). This needs architectural attention to prevent resource exhaustion in long-running gateways.
*   **Browser Proxy Inheritance (#14372):** P2 bug where browser tools inherit proxy env vars, causing connection errors. This impacts users in corporate or proxy-heavy environments.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest
**Date:** 2026-07-26
**Source:** github.com/sipeed/picoclaw

## 1. Today's Overview
PicoClaw is experiencing moderate activity with 4 Pull Requests updated and 2 Issues active in the last 24 hours. While no new releases were published, three PRs were closed/merged today, indicating ongoing maintenance and feature integration efforts. The project shows a healthy balance of bug fixes, infrastructure improvements, and new channel support, though some long-standing issues regarding network resilience remain open.

## 2. Releases
*No new releases reported in the last 24 hours.*

## 3. Project Progress
Three Pull Requests were closed/merged today, advancing the project's stability and feature set:
*   **Message Splitting Logic (#3295):** Merged by `ErzerLP`, this fix prevents `SplitMessage` from hanging when processing oversized fenced-code headers, ensuring bounded raw split fallback for progress.
*   **Extended Tooling Integration (#339):** Merged by `udbhav-44`, this significant update adds Google Calendar support, enhances Email channel polling/content fetching, and introduces GitHub and System Stats developer tools.
*   **Platform & Gateway Compatibility (#3205):** Merged by `sarwonous`, this PR resolves critical compatibility issues with 9router gateway responses and adds a missing Linux ARMv7 build target, crucial for Raspberry Pi users.

## 4. Community Hot Topics
*   **Matrix Reconnection Stability (Issue #3203):** [Link](https://github.com/sipeed/picoclaw/issues/3203)
    *   *Analysis:* This issue highlights a critical reliability flaw where Matrix sync loops die silently after network disruptions. The lack of auto-reconnection breaks systemd restart policies, making it a high-priority stability concern for users deploying PicoClaw in production environments.
*   **Model Listing Visibility (Issue #3294):** [Link](https://github.com/sipeed/picoclaw/issues/3294)
    *   *Analysis:* A usability bug where `/list models` fails to display all configured models, only showing the current one. This contradicts user expectations based on the command name and description, affecting multi-model configuration workflows.
*   **Simplex Channel Support (PR #3193):** [Link](https://github.com/sipeed/picoclaw/pull/3193)
    *   *Analysis:* Although marked stale, this PR proposes a new "simplex" channel type. Its persistence suggests community interest in one-way communication modes or lightweight channel implementations.

## 5. Bugs & Stability
*   **High Severity: Matrix Sync Loop Deadlock (Issue #3203)**
    *   *Description:* Silent death of the `/sync` loop after network/server disruption without reconnection logic.
    *   *Status:* Open. No linked fix PR identified yet.
*   **Medium Severity: Model List Display Error (Issue #3294)**
    *   *Description:* `/list models` returns incomplete data for multi-model configurations.
    *   *Status:* Open. Created today.
*   **Resolved: Message Splitter Hang (PR #3295)**
    *   *Status:* Merged/Fixed. Addresses regression in handling oversized fence headers.

## 6. Feature Requests & Roadmap Signals
*   **Google Calendar & Email Enhancements:** The merge of PR #339 indicates strong demand for integrated productivity tools beyond basic chat. Future versions may expand this "Tool" ecosystem.
*   **ARMv7 Support:** The inclusion of Linux ARMv7 builds in PR #3205 signals a roadmap commitment to supporting edge devices like Raspberry Pi 3/4 more robustly.
*   **Simplex Channels:** PR #3193 remains open/stale, suggesting potential future support for simplified or unidirectional communication protocols if maintainer attention is resumed.

## 7. User Feedback Summary
Users are prioritizing **reliability** and **integration depth**. The Matrix reconnection bug (#3203) reveals that users are running PicoClaw in automated, systemd-managed environments where silent failures are unacceptable. Conversely, the merge of Calendar/Email tools (#339) shows users value PicoClaw as a comprehensive personal assistant hub rather than just a chat bridge. The model listing bug (#3294) points to friction in managing complex multi-provider setups.

## 8. Backlog Watch
*   **Issue #3203 (Matrix Reconnection):** Requires immediate maintainer attention due to its impact on service uptime and production stability.
*   **PR #3193 (Simplex Channel):** Stale since June 27; needs triage to determine if the feature is desired or if the PR should be closed.
*   **Issue #3294 (Model List Bug):** Recently opened; likely requires a quick patch to align behavior with documentation.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest
**Date:** 2026-07-26
**Source:** github.com/qwibitai/nanoclaw

### 1. Today's Overview
NanoClaw exhibits high development velocity with 11 Pull Requests updated in the last 24 hours, indicating a burst of activity primarily focused on security hardening and context consistency fixes. While no new releases were published today, the team is actively addressing critical gaps in agent memory isolation and container security protocols. The project health remains robust, with immediate attention paid to issues where host-sent messages were failing to propagate into agent contexts, potentially causing behavioral drift.

### 2. Releases
No new releases were published in the last 24 hours.

### 3. Project Progress
Significant progress was made on security and operational stability through several merged or closed items:
*   **Security Hardening (PR #2748):** Closed by `boazdori`, this PR implemented defense-in-depth measures for agent containers, including `--cap-drop=ALL`, `no-new-privileges:true`, and PID limits to prevent fork-bombs and limit blast radius in case of escape.
*   **Image Cleanup Logic (PR #3131):** Opened by `gavrielc`, this fix ensures that uninstallation processes correctly remove per-agent-group derived images, preventing disk bloat from orphaned Docker tags.
*   **Input Validation (PR #3130):** Also by `gavrielc`, this introduces validation at the write seam for `container_configs.image_tag`, preventing arbitrary strings from being passed directly to `docker run`.

### 4. Community Hot Topics
The most discussed topics revolve around **context fidelity** and **polling logic correctness**:
*   **Context Consistency:** Issue #3134 and PR #3135 by `brianjcohen` are central today. Users are concerned that messages sent by the host on behalf of an agent (e.g., approval cards) are invisible to the agent's memory, leading to disjointed conversations.
*   **Poll Loop Integrity:** Issue #3132 and PR #3133 by `buzali` highlight a bug where follow-up polls bypass trigger gates, causing message accumulation errors. This suggests users are running complex, high-frequency query loops where timing and state management are critical.
*   **Tool Visibility:** PR #2211 by `robbyczgw-cla` has seen recent updates after three months of production patching, indicating strong community interest in live tool-call previews.

### 5. Bugs & Stability
Several critical bugs affecting stability and security were identified today:
1.  **High Severity - Security/Injection Risk (PR #3127):** `glifocat` proposes sanitizing inbox attachment paths to a safe character class. Without this, malicious filenames could potentially lead to path traversal or injection vulnerabilities.
2.  **High Severity - Mount Security (PR #3129):** `gavrielc` identified that `~/.config/nanoclaw` and `~/.local/bin` were not blocked by default mount patterns, risking exposure of sensitive config files (`mount-allowlist.json`) or binary execution.
3.  **Medium Severity - Context Loss (Issue #3134):** Agents lose records of host-initiated messages, breaking conversation continuity. A fix is proposed in PR #3135.
4.  **Medium Severity - Poll Accumulation (Issue #3132):** Follow-up polls push messages without respecting trigger states, causing data corruption in active queries. Fix proposed in PR #3133.

### 6. Feature Requests & Roadmap Signals
*   **Operational Skills:** PR #3128 adds a "flight-checkin" container skill, signaling a trend toward specialized, modular operational skills for specific industry workflows.
*   **MCP Server Diagnostics:** PR #3124 improves reporting for unavailable MCP servers, suggesting a roadmap focus on better observability and debugging for external tool integrations.
*   **OpenCode Compatibility:** PR #3122 addresses main compatibility and custom-endpoint transport, indicating ongoing efforts to ensure NanoClaw works seamlessly with diverse frontend and transport layers.

### 7. User Feedback Summary
Users are prioritizing **reliability** and **security** over new features. The high volume of security-related PRs (mount blocking, image tag validation, container caps) suggests that enterprise or power-user deployments are demanding stricter isolation guarantees. Additionally, the feedback regarding host-sent message visibility indicates that users expect a fully transparent agent memory state, regardless of who initiates the message. Satisfaction appears tied to the system's ability to maintain consistent context across complex, multi-turn interactions.

### 8. Backlog Watch
*   **PR #3122 (OpenCode Compatibility):** While updated recently, it remains open and involves significant refactoring for main compatibility and transport layers. It requires careful review to avoid regressions.
*   **PR #2211 (Tool Visibility):** Although marked as having been used in production for three months, it remains open. Its long-standing presence suggests it may be awaiting final integration or policy approval before merging.
*   **PR #3131 & #3130 (Maintenance/Security):** These are critical maintenance fixes. Ensuring these are merged promptly is vital to prevent resource leaks and configuration injection risks.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest
**Date:** 2026-07-26
**Source:** GitHub (nearai/ironclaw)

## 1. Today's Overview
The IronClaw project demonstrates high velocity with 19 PRs and 11 Issues updated in the last 24 hours, indicating a strong focus on both backend stability and frontend user experience. There were no new releases published today; however, significant architectural work is underway regarding error recoverability and dependency hardening. The team is actively addressing "v1-launch-checklist" items, suggesting an imminent release cycle focused on polish and accessibility.

## 2. Releases
**No new releases published.**
*   Note: PR #5598 (`chore: release`) remains open, detailing upcoming version bumps for `ironclaw_common` (0.4.2 -> 0.5.0) and `ironclaw_skills` (0.3.0 -> 0.4.0), which include API-breaking changes.

## 3. Project Progress
**Merged/Closed Pull Requests:**
*   **WebUI Performance & UX:** Several critical fixes were merged to improve the WebUI bundle size and interaction flow.
    *   [PR #6632](https://github.com/nearai/ironclaw/pull/6632): Implemented route-level code splitting, reducing initial JS payload from ~1.2MB to ~376KB.
    *   [PR #6624](https://github.com/nearai/ironclaw/pull/6624): Fixed keyboard focus trapping in extension configuration modals.
    *   [PR #6627](https://github.com/nearai/ironclaw/pull/6627): Resolved state inconsistency when run cancellation fails.
    *   [PR #6626](https://github.com/nearai/ironclaw/pull/6626): Prevented UI flashing when filtering automation lists.
    *   [PR #6680](https://github.com/nearai/ironclaw/pull/6680): Preserved workspace tree state across root navigation.
*   **Backend Architecture:**
    *   [PR #6669](https://github.com/nearai/ironclaw/pull/6669): Moved extension host ownership out of composition modules.
    *   [PR #6670](https://github.com/nearai/ironclaw/pull/6670): Consolidated Reborn guidance documentation and removed stale plans.
    *   [PR #6673](https://github.com/nearai/ironclaw/pull/6673): Added a production struct dead-code ratchet to enforce code hygiene.

**Open PRs Advancing Features:**
*   [PR #6678](https://github.com/nearai/ironclaw/pull/6678): Bringing the `/model` and `/status` product command pipeline live across Slack, Telegram, and WebChat.
*   [PR #6672](https://github.com/nearai/ironclaw/pull/6672): Implementing Phase B of attested signing (signed intent + per-agent key lifecycle).
*   [PR #6677](https://github.com/nearai/ironclaw/pull/6677): Adding compile-forced recoverability conformance matrix tests.

## 4. Community Hot Topics
*   **Error Recoverability Epic:** Issue [#6284](https://github.com/nearai/ironclaw/issues/6284) remains a central pillar, aiming for a model that recovers from 100% of errors. This drives multiple recent PRs (#6677, #6681).
*   **Integration Guidance Gaps:** Issues [#6668](https://github.com/nearai/ironclaw/issues/6668) (Slack connection) and [#6671](https://github.com/nearai/ironclaw/issues/6671) (Telegram setup) highlight friction in first-time user experiences for channel integrations. Users expect the agent to guide them seamlessly rather than hitting admin-only walls.
*   **Performance Optimization:** Issue [#6628](https://github.com/nearai/ironclaw/issues/6628) and its associated PRs show strong community interest in reducing WebUI load times and improving dependency tree-shaking.

## 5. Bugs & Stability
*   **High Severity:**
    *   [#6667](https://github.com/nearai/ironclaw/issues/6667): GitHub PAT authentication loops silently without surfacing errors to users. *Status: Open.*
    *   [#6620](https://github.com/nearai/ironclaw/issues/6620): Failed run cancellation leaves chat in incorrect idle state. *Status: Fixed via PR #6627.*
*   **Medium Severity:**
    *   [#6621](https://github.com/nearai/ironclaw/issues/6621): Extension config modal does not trap keyboard focus. *Status: Fixed via PR #6624.*
    *   [#6622](https://github.com/nearai/ironclaw/issues/6622): Automation list flashes loading skeleton during filter changes. *Status: Fixed via PR #6626.*
*   **Stability Analysis:** Daily failure taxonomy [#6676](https://github.com/nearai/ironclaw/issues/6676) indicates current failures are largely due to model shortfalls (e.g., deepseek-v4-flash) rather than harness defects, suggesting the test infrastructure is stable but model performance needs tuning.

## 6. Feature Requests & Roadmap Signals
*   **Attested Signing:** PR #6672 signals a major push toward cryptographic attestation for agent intents, marking "Phase B" of the ledger revival plan.
*   **Unified Command Pipeline:** PR #6678 suggests moving towards a unified slash command architecture that works identically across all surfaces (Slack, Telegram, WebChat).
*   **Dependency Centralization:** Issue [#6675](https://github.com/nearai/ironclaw/issues/6675) requests centralizing Rust dependencies via `workspace.dependencies`, a standard best practice for large Cargo workspaces that will reduce maintenance overhead.

## 7. User Feedback Summary
*   **Pain Points:** Users are frustrated by non-intuitive onboarding flows for third-party integrations (Slack/Telegram) where the agent fails to provide clear instructions or hits permission barriers unexpectedly. Silent auth failures (GitHub PAT) are also causing confusion.
*   **Satisfaction:** The rapid response to WebUI performance issues (code splitting, focus trapping) indicates the team is responsive to usability concerns. Localizing error messages (PR #6625) is a positive step toward better user feedback clarity.

## 8. Backlog Watch
*   **[EPIC] Error Recoverability Endgame:** Issue [#6284](https://github.com/nearai/ironclaw/issues/6284) is critical for long-term stability. Maintainers should prioritize the remaining items in this epic, particularly ensuring the model can act on recovered errors without reporting non-success states.
*   **WebUI Bundle Size:** While PR #6632 has made significant progress, Issue [#6628](https://github.com/nearai/ironclaw/issues/6628) tracks broader optimization goals including image optimization and caching strategies that remain ongoing.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest
**Date:** 2026-07-26  
**Source:** netease-youdao/LobsterAI

### 1. Today's Overview
The LobsterAI project demonstrates high development velocity with **9 issues closed** and **11 PRs merged** in the last 24 hours, indicating a significant burst of maintenance and feature completion. Activity is heavily concentrated on UI/UX refinements for the Cowork session interface, specifically focusing on navigation efficiency, error visibility, and data export capabilities. While no new releases were published today, the accumulation of merged changes suggests an imminent update cycle. The project health appears robust, with a clear focus on improving user experience for long-duration or complex multi-tool agent interactions.

### 2. Releases
*   **No new releases** were published in the last 24 hours.
*   *Note:* With 11 PRs merged recently (including critical Windows installer fixes and new model support), a patch or minor release is likely imminent to stabilize these changes.

### 3. Project Progress
Significant progress was made in merging legacy feature requests and stabilizing the platform:

*   **Windows Installer Hardening:** Merged PRs #2383 and #2384 address security and recovery issues in the Windows installation process, specifically protecting against foreign content injection and hardening update recovery mechanisms.
*   **Model Support Expansion:** PR #2381 merged support for the **Kimi K3** model, expanding the available AI backend options for users.
*   **Scheduled Task Enhancements:** PR #1335 implemented "Workdays" (Mon-Fri) scheduling, allowing users to create cron-like jobs that only run on weekdays.
*   **MCP Configuration UX:** PR #1336 introduced JSON paste-import functionality for MCP server configurations, streamlining setup for advanced users.
*   **Cowork Session UI Overhaul:** A series of PRs (#1327, #1331, #1338, #1340, #1342) implemented major UX improvements:
    *   Batch expand/collapse for ToolUse blocks (#1327).
    *   Visual error indicators (red dot) for failed sessions (#1331).
    *   Time-based grouping in the sidebar (Today/Yesterday/This Week) (#1338).
    *   Message timestamp display in chat bubbles (#1340).
    *   Keyboard history navigation (Up/Down arrows) in the input box (#1342).

### 4. Community Hot Topics
*   **Session Navigation & Efficiency:** Issues #1337, #1339, and #1341 highlight a strong user need for better information architecture. Users are struggling with large session lists and lack of historical context within chats. The rapid closure of these issues indicates the team is prioritizing "power user" workflows.
    *   [Issue #1337: Session list time grouping](https://github.com/netease-youdao/LobsterAI/issues/1337)
    *   [Issue #1339: Message timestamps](https://github.com/netease-youdao/LobsterAI/issues/1339)
    *   [Issue #1341: Input history navigation](https://github.com/netease-youdao/LobsterAI/issues/1341)
*   **Tool Interaction Friction:** Issue #1326 and its corresponding PR #1327 show that users find managing multiple tool calls cumbersome. The demand for batch controls suggests Cowork sessions are becoming more complex, requiring UI adjustments to match the cognitive load.
    *   [Issue #1326: Batch expand/collapse ToolUse](https://github.com/netease-youdao/LobsterAI/issues/1326)
*   **Search Limitations:** Issue #1343 remains a key pain point, as current search only covers titles, not content. This is a common bottleneck in AI agents dealing with long contexts.
    *   [Issue #1343: Full-text search](https://github.com/netease-youdao/LobsterAI/issues/1343)

### 5. Bugs & Stability
*   **Windows Installation Security:** PRs #2383 and #2384 fixed critical stability and security concerns regarding root protection and recovery on Windows. These are high-severity fixes for deployment reliability.
*   **Notification Channel Bug:** Issue #1329 reported that new scheduled tasks lacked notification channel options. This has been closed (likely via PR #1335 or related backend fixes), resolving a configuration blocker.
    *   [Issue #1329: Scheduled task notification bug](https://github.com/netease-youdao/LobsterAI/issues/1329)
*   **No new crash reports** or regressions were identified in the open issues for this period.

### 6. Feature Requests & Roadmap Signals
*   **Full-Text Search:** Issue #1343 requests searching message content, not just titles. This is a high-value feature for productivity and is likely a candidate for the next major version.
    *   [Issue #1343: Content search](https://github.com/netease-youdao/LobsterAI/issues/1343)
*   **Markdown Export:** Issue #1345 requests exporting sessions to Markdown. This addresses the need for knowledge management and second editing, signaling a trend toward treating AI sessions as persistent documentation.
    *   [Issue #1345: Markdown Export](https://github.com/netease-youdao/LobsterAI/issues/1345)
*   **Folder Support in Chat:** Issue #2385 is currently open, requesting the ability to attach folders (not just files) to the dialog, similar to `@file` mentions. This suggests a desire for deeper file system integration.
    *   [Issue #2385: Folder attachment support](https://github.com/netease-youdao/LobsterAI/issues/2385)

### 7. User Feedback Summary
Users are actively transitioning from casual chatting to professional, workflow-heavy usage. Key feedback themes include:
*   **Efficiency:** Users want to reduce clicks (batch toggles, keyboard shortcuts for history).
*   **Visibility:** Users need immediate visual cues for errors and session status (red dots, timestamps).
*   **Organization:** As session counts grow, users require structured views (time grouping) rather than flat lists.
*   **Integration:** There is a growing demand for better file handling (folders) and data portability (Markdown export).

### 8. Backlog Watch
*   **[OPEN] Issue #2385:** "Dialog box can only add files, not folders." This is a feature gap compared to competitors and is currently the most prominent open issue regarding core interaction mechanics.
    *   [Link to Issue #2385](https://github.com/netease-youdao/LobsterAI/issues/2385)
*   **[CLOSED but Stale] Issue #1343:** Full-text search. Although closed, the summary implies it was addressed or deferred. If deferred, this should be flagged for roadmap review as it impacts usability significantly.
*   **[CLOSED but Stale] Issue #1329:** Notification channel fix. Verified as resolved, but worth monitoring if the workaround persists.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest: 2026-07-26

### 1. Today's Overview
Moltis is experiencing a period of high development velocity with six pull requests updated in the last 24 hours, indicating active feature expansion and internal process refinement. While no new releases or issues were opened today, the project is strategically broadening its interoperability capabilities by exposing itself as an ACP agent and enhancing support for Nostr and Slack integrations. The absence of open issues suggests stable operational conditions, allowing the team to focus on merging significant architectural changes and documentation updates.

### 2. Releases
*   **Status:** No new releases published today.
*   **Details:** There are no immediate migration notes or breaking change warnings associated with a new version tag at this time. Development activity is currently concentrated in open and recently closed Pull Requests rather than release candidates.

### 3. Project Progress
The project advanced significantly through the processing of several key Pull Requests:
*   **ACP Agent Exposure (PR #1169):** Moltis transitions from being solely an ACP client to also functioning as an ACP agent over stdio. This allows external harnesses like Zed, `buzz-acp`, or bespoke runners to drive Moltis directly, reversing the previous dependency model where Moltis spawned other agents. [Link](https://github.com/moltis-org/moltis/pull/1169)
*   **Nostr Group Chat Support (PR #1168):** Added NIP-29 group chat support for Buzz channels within the Nostr integration. This expands Moltis's capability to participate in Block's open-source workspace as an equal member of team channels, moving beyond simple NIP-42 authentication. [Link](https://github.com/moltis-org/moltis/pull/1168)
*   **Slack Interaction Enhancements (PR #1165 & #1166):** Two major PRs addressed Slack limitations. PR #1165 introduced acknowledgment reactions and inbound reaction triggers to replace missing typing indicators, while PR #1166 built upon this with phase feedback, Block Kit rendering, and improved supervision logic for reconnections. [Link](https://github.com/moltis-org/moltis/pull/1165), [Link](https://github.com/moltis-org/moltis/pull/1166)
*   **Documentation Governance (PR #1167):** Closed a docs-only PR extending `CLAUDE.md` rules to forbid Claude session URLs in commits and PR descriptions, tightening internal workflow standards. [Link](https://github.com/moltis-org/moltis/pull/1167)

### 4. Community Hot Topics
Activity is currently driven by contributor-led feature implementations rather than community-reported bugs or debates.
*   **Most Active:** PR #1169 (ACP Agent) and PR #1168 (Nostr NIP-29) represent the most significant architectural shifts.
*   **Underlying Needs:** The community and core contributors are prioritizing **interoperability**. By making Moltis an ACP agent and supporting complex Nostr group chats, the project addresses the need for Moltis to be a first-class citizen in various AI orchestration environments, not just a consumer of other agents.
*   **Engagement:** Current PRs have 0 comments and 0 👍, suggesting these are expected feature additions developed in coordination with maintainers rather than contentious community proposals.

### 5. Bugs & Stability
*   **Bug Fixes:** PR #1165 explicitly mentions fixing a "confirmed wrong-message bug in threaded replies" within Slack interactions.
*   **Stability Improvements:** PR #1166 adds "reconnect supervision," which enhances stability against network interruptions in Slack connections.
*   **Severity:** No critical crashes or regressions were reported in issues today. The focus has been on resolving functional gaps (like the lack of acknowledgment signals in Slack) rather than emergency patches.

### 6. Feature Requests & Roadmap Signals
*   **Vector Memory Backend (PR #1158):** Although updated yesterday (2026-07-25), this PR introduces a `zvec` vector database memory backend using `redb`. This signals a roadmap direction toward flexible, potentially local-first or lightweight vector storage solutions for long-term memory, distinct from existing backends. [Link](https://github.com/moltis-org/moltis/pull/1158)
*   **Prediction:** The next version will likely highlight **Agent-to-Agent communication** (via the new ACP agent mode) and **enhanced messaging protocol support** (Nostr NIP-29, Slack Block Kit). The inclusion of experimental memory backends suggests continued investment in customizable persistence layers.

### 7. User Feedback Summary
*   **Pain Points Addressed:** The primary user pain point addressed today was the lack of feedback in Slack. Since Slack bots cannot show typing indicators, users previously had no signal that Moltis received their message. The introduction of acknowledgment reactions (PR #1165) directly solves this UX friction.
*   **Use Cases:** Users are increasingly integrating Moltis into diverse ecosystems (Nostr/Buzz, Slack, and IDEs via ACP). The feedback loop here is implicit: the rapid implementation of these integrations indicates strong demand for Moltis to operate seamlessly across different communication platforms.

### 8. Backlog Watch
*   **Current Status:** With 0 open issues and no stalled PRs requiring maintainer intervention today, the backlog appears clear of urgent attention items.
*   **Watch Item:** PR #1158 (`feat(memory): add zvec vector database memory backend`) is currently open and represents an experimental feature. Maintainers should monitor this for integration testing and potential merge conflicts with existing memory subsystems, as it introduces a new dependency stack (`zvec`, `redb`). [Link](https://github.com/moltis-org/moltis/pull/1158)

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest: 2026-07-26

### 1. Today's Overview
The CoPaw project (agentscope-ai/CoPaw) is experiencing high activity with **7 open issues** and **7 pull requests** updated in the last 24 hours, indicating a critical period for stability and feature refinement. There were no new releases published today, suggesting the team is focusing on resolving pending bugs and merging existing contributions rather than shipping a new version. The most significant activity revolves around MCP driver transport configuration errors and performance optimizations in the browser SDK, which are blocking several user workflows. Maintainer attention is required to address the high-severity MCP connectivity bug affecting Streamable HTTP servers.

### 2. Releases
*   **No new releases** were published in the last 24 hours.
*   Current active version under discussion remains **v2.0.1**.

### 3. Project Progress
Several key technical areas have seen advancement through merged or reviewed PRs:
*   **Browser SDK Unification**: PR #6276 introduces a unified browser control SDK with a split control-plane/execution-plane architecture, enabling better isolation and LLM-authored async Python execution.
*   **Reranker Integration**: PRs #5691 and #5692 have been closed, successfully adding UI configuration and backend support for reranking search results in the ReMeLightMemoryCard component.
*   **CI/CD Improvements**: PR #6463 fixes website deployment triggers by wiring the release orchestrator to update `qwenpaw.agentscope.io`.
*   **Documentation Updates**: PR #6462 clarifies that native Windows sandbox support (AppContainer/restricted-token) is now available, removing the WSL2 prerequisite from documentation.
*   **Windows Testing Fixes**: PR #6365 addresses npm script execution failures on Windows by invoking Vitest directly, improving contributor experience.

### 4. Community Hot Topics
*   **MCP Transport Hardcoding Bug**: Issues **#6470**, **#6469**, and **#6468** all report the same critical bug where the MCP driver ignores YAML `transport` configs, defaulting to SSE and breaking Streamable HTTP connections. This is a top-priority issue due to its impact on core functionality. ([#6470](https://github.com/agentscope-ai/QwenPaw/issues/6470), [#6469](https://github.com/agentscope-ai/QwenPaw/issues/6469))
*   **High CPU Usage on Wayland/Edge**: Issue **#6460** highlights performance degradation (high CPU/fan noise) when viewing large sessions or ComfyUI outputs on Linux/Edge/Wayland, pointing to potential rendering or WebSocket push inefficiencies. ([#6460](https://github.com/agentscope-ai/QwenPaw/issues/6460))
*   **User Experience Enhancements**: Feature request **#6466** asks for clickable file/folder path buttons in chat, reflecting a need for tighter OS integration and reduced friction for developers using the tool. ([#6466](https://github.com/agentscope-ai/QwenPaw/issues/6466))

### 5. Bugs & Stability
*   **Critical**: **MCP Driver Transport Failure** (Issues #6470, #6469, #6468). The hardcoded use of `sse_client` in `mcp_stateful_client.py` prevents connection to Streamable HTTP MCP servers, causing "Session terminated" errors. No fix PR is currently linked.
*   **High**: **API Connection Failure** (Issue #6464). Users deploying QwenPaw v2.0.1 on AgentScope Platform cannot connect to any models, resulting in empty dropdowns and API errors. This suggests a regression in model provider configuration or authentication handling.
*   **Medium**: **Performance Regression** (Issue #6460). High CPU usage on specific client environments (Edge + Wayland) during heavy session loads requires investigation into frontend rendering or WebSocket handling.

### 6. Feature Requests & Roadmap Signals
*   **Clickable File Paths**: Issue **#6466** requests the ability to output clickable buttons for file/folder paths, enhancing usability for system administration and development tasks.
*   **Reranker UI**: The recent closure of PRs #5691/#5692 indicates that reranker configuration is moving from backend implementation to user-facing UI, a likely candidate for the next minor update's feature set.
*   **Native Windows Sandbox**: PR #6462 confirms native Windows sandbox support, expanding the platform's compatibility beyond WSL2 for security-isolated agent execution.

### 7. User Feedback Summary
*   **Configuration Complexity**: Users are struggling with MCP server configurations, particularly regarding transport protocols (SSE vs. Streamable HTTP), leading to multiple duplicate bug reports.
*   **Deployment Issues**: New users and administrators are encountering setup failures, specifically with model connectivity on cloud deployments (#6464) and node establishment for proxy services (#6467).
*   **Performance Sensitivity**: Advanced users are sensitive to resource consumption, especially on Linux/Wayland setups, demanding optimized rendering for large data sets.
*   **Support Gaps**: Some users report lack of response in community channels (#6467), highlighting a potential need for better community management or automated support resources.

### 8. Backlog Watch
*   **MCP Transport Fix**: The maintainer team needs to prioritize fixing the hardcoded transport logic in `mcp_stateful_client.py` to resolve the three duplicate issues (#6470, #6469, #6468).
*   **Model Connectivity Regression**: Investigating why v2.0.1 fails to connect to any models on AgentScope Platform (#6464) is crucial for maintaining trust in recent releases.
*   **Windows Test Scripts**: Ensure PR #6365 is merged to prevent future friction for Windows-based contributors.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest
**Date:** 2026-07-26
**Source:** GitHub (zeroclaw-labs/zeroclaw)

## 1. Today's Overview
ZeroClaw is in a critical pre-release phase for version **v0.8.4**, targeting a release date of July 31, 2026. Activity is high with 50 Pull Requests and 19 Issues updated in the last 24 hours, indicating intense finalization efforts. The primary focus today has been on stabilizing the runtime, fixing security misconfigurations in WhatsApp Web integrations, and preparing the workspace for `crates.io` publication. While no new official release artifact was published today, PR #9376 indicates the v0.8.4 cut is imminent.

## 2. Releases
*   **Status:** No new binary release published today.
*   **Upcoming:** **v0.8.4 Maintenance Train** (Tracker #8357). Target date: July 31, 2026.
*   **Preparation:** PR #9376 by JordanTheJet is currently open to finalize the v0.8.4 cut, including renaming the root crate to `zeroclaw` for `cargo install` compatibility and configuring publishing for 18 crates to `crates.io`.

## 3. Project Progress
*   **Release Engineering:** Significant progress on CI/CD infrastructure. PR #9115 introduces "Blacksmith runners" to accelerate compile-heavy Rust jobs. PR #9371 parallelizes the runtime stress gate test to reduce CI feedback loops.
*   **Plugin & Runtime Stability:** PR #9125 fixes a critical lifecycle issue where channel listeners were spawned as unowned background tasks; they are now supervised by the orchestrator. PR #9124 adds end-to-end tests for Wasm channel components.
*   **Security & Secrets:** PR #9194 extracts a `KeySource` trait to abstract master encryption key retrieval, enhancing secret management flexibility. PR #8496 centralizes deferred-MCP access policies to resolve Surface 1(b) security gaps.
*   **Internationalization:** PR #9377 completes Chinese (zh) translations for all UI keys, addressing localization gaps noted in Issue #9363.

## 4. Community Hot Topics
*   **[Bug] WhatsApp Web Security Misconfiguration (#9348)** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9348): High severity. Users report that `mode = business` ignores allowlists, replying to all groups. This has split into sub-issues (#9366 for timeout, #9354 for warning). *Analysis:* Critical trust issue for enterprise users relying on ZeroClaw for secure bot deployments.
*   **[Feature] Unified Plugin Catalog (#6489)** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6489): Long-term architectural shift to collapse Integrations and Plugins into one catalog. *Analysis:* Signals a move towards a more modular, Wasmtime-centric architecture, reducing fragmentation between channels and tools.
*   **[RFC] AI-Assisted PR Review (#9330)** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9330): Proposal to use CI results for AI pre-review. *Analysis:* Reflects community desire to maintain code quality despite growing PR volume (50+ updates/day).

## 5. Bugs & Stability
*   **Critical/High Severity:**
    *   **#9328:** Verifiable-intent constraint evaluation fails to verify credential chains properly. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9328))
    *   **#9357:** `cargo test` flakiness on `master` (19/20 runs fail) due to a poisoned global mutex. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9357))
    *   **#9340:** CLI cron jobs discard output (`delivery.mode = "none"`). ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9340))
    *   **#9373:** Peer-agent delivery skips cost-tracking context, breaking budget enforcement. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9373))
    *   **#9374:** `agent::run` leaks `AgentStart` on 12 exit paths. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9374))
*   **Medium Severity:**
    *   **#9239:** Config patch emits plaintext errors instead of JSON envelopes. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9239))
    *   **#9366:** WhatsApp `approval_timeout_secs` is accepted but ignored. ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9366))
*   **Fixes Merged/Closed:**
    *   **#9285:** Nested `set_prop` masking invalid values (Fixed). ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9285))
    *   **#8962:** Runtime test flaking under parallel execution (Closed/Fixed). ([Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8962))
    *   **#9270:** Resolved npm audit advisories in web dependencies. ([Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9270))

## 6. Feature Requests & Roadmap Signals
*   **Telegram Multi-Message Streaming (#8561 / #9359):** Implementation of paced multi-message delivery for Telegram, similar to Discord/Matrix. This is a major UX enhancement for long-form responses.
*   **OpenAI Chat Completions Endpoint (#8486):** Adding native OpenAI protocol support to the gateway to improve interoperability with third-party clients (LangChain, Aider, etc.).
*   **Atlas Cloud Provider (#9200):** New typed provider for Atlas Cloud, expanding model availability beyond standard OpenAI-compatible endpoints.
*   **Shell Output Format for Cron (#8438):** Allows raw stdout capture for shell-based cron jobs, addressing a common automation need.

## 7. User Feedback Summary
*   **Pain Points:**
    *   **WhatsApp Policy Bypass:** Users are frustrated that configuration intended to restrict bot behavior (allowlists) is ineffective in Business mode, creating security risks.
    *   **Observability Gaps:** Cost tracking (`cost_usd`) is not reported in `AgentEnd` events despite being calculated internally (#9349), making budget monitoring difficult.
    *   **Localization Inconsistency:** While UI text translates, config metadata remains English, causing confusion for non-English speakers (#9363).
*   **Satisfaction:**
    *   The community appreciates the rapid response to security issues (e.g., splitting #9348 into manageable sub-tasks).
    *   The push for `crates.io` publishing (#9376) addresses long-standing friction in installing ZeroClaw as a dependency or binary.

## 8. Backlog Watch
*   **#7130: Forbid Unsafe Code Workspace-Wide** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7130): Long-standing tracker to enforce `#![forbid(unsafe_code)]` except for `aardvark-sys`. Requires maintainer attention to balance safety with necessary FFI bindings.
*   **#8583: Channel/Source Shared-Boundary Cleanup** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8583): Architectural cleanup tracker for channel ingress. Critical for future scalability but often deprioritized against feature work.
*   **#9330: AI-Assisted PR Pre-Review** [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9330): Needs maintainer review to define scope and risk boundaries before implementation.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*