# AI CLI Tools Community Digest 2026-07-25

> Generated: 2026-07-25 03:21 UTC | Tools covered: 10

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

# AI CLI Tools Ecosystem Report: 2026-07-25

## 1. Ecosystem Overview
The AI CLI landscape in July 2026 is defined by a critical transition from experimental agents to enterprise-grade reliability, with a heavy emphasis on multi-agent orchestration and context management. The release of "Opus 5" models by Anthropic and OpenAI has triggered widespread compatibility updates across tools like Claude Code, GitHub Copilot, and Pi, forcing developers to adapt to new context limits and pricing structures. Stability remains the primary friction point, as major platforms (OpenAI Codex, Gemini, Pi) battle regressions in authentication, session persistence, and cross-platform terminal rendering. Concurrently, the community is pushing for deeper integration with corporate infrastructure, specifically demanding robust proxy support, granular permission controls, and deterministic subagent behaviors.

## 2. Activity Comparison

| Tool | Issues Reported/Active | PRs Merged/In Progress | Release Status | Key Activity Focus |
| :--- | :---: | :---: | :--- | :--- |
| **Claude Code** | High (10 Hot Issues) | Low (1 Key PR) | v2.1.220 / v2.1.219 | Opus 5 integration; Session limit & Auth bugs |
| **OpenAI Codex** | High (10 Hot Issues) | High (10 Key PRs) | Rust SDK Alpha Series | Windows stability; MCP reliability; Multi-root fixes |
| **Gemini CLI** | High (10 Hot Issues) | High (10 Key PRs) | Nightly (Failed Build) | Security hardening; Subagent recovery logic |
| **GitHub Copilot** | High (10 Hot Issues) | None | v1.0.75 (Opus 5 Support) | Session loops; Permission gating false positives |
| **Kimi Code** | Medium (5 Hot Issues) | Medium (2 Key PRs) | No New Release | Proxy/SSL support; Cross-device continuity |
| **OpenCode** | Medium (10 Hot Issues) | High (10 Key PRs) | v1.18.5 | Symlink handling; LaTeX/Math rendering; PWA support |
| **Pi** | High (10 Hot Issues) | High (10 Key PRs) | v0.82.0 | Local model (`llama.cpp`) stability; Context compaction |
| **Qwen Code** | Medium (10 Hot Issues) | High (10 Key PRs) | v0.21.0 | Cold-start optimization; Rate-limit configurability |
| **DeepSeek TUI** | High (10 Hot Issues) | High (10 Key PRs) | v0.9.1 (Legacy Deprecation) | Rebrand to CodeWhale; Major architecture refactor |
| **Grok Build** | None | None | No Activity | - |

## 3. Shared Feature Directions

*   **Advanced Context & Compaction Management:**
    *   **Tools:** Claude Code, OpenCode, Pi, Qwen Code.
    *   **Need:** Users demand deterministic context preservation. Specific requests include plugins to prevent "silent" context loss during auto-compaction (Claude), fixing fake messages injected during replay (OpenCode), and resolving compaction failures with enterprise licenses (Pi).
*   **Enterprise Security & Network Robustness:**
    *   **Tools:** Gemini CLI, Kimi Code, OpenCode, Pi.
    *   **Need:** Strong push for corporate proxy compatibility (SSL_CERT_FILE support in Kimi/Gemini), strict credential validation (OAuth token leakage fixes in Gemini), and handling of complex authentication scopes (scoped API keys in Pi).
*   **Multi-Agent Orchestration & Subagent Control:**
    *   **Tools:** Gemini CLI, OpenCode, DeepSeek (CodeWhale), Qwen Code.
    *   **Need:** Granular control over subagents, including model selection per task (Qwen), visibility into subagent trajectories (Gemini), and explicit handoff semantics between agent roles (DeepSeek).
*   **Cross-Platform Terminal UI Consistency:**
    *   **Tools:** OpenAI Codex, Qwen Code, DeepSeek (CodeWhale), Pi.
    *   **Need:** Fixes for IME misalignment (macOS), Windows-specific rendering glitches, and stable TUI behavior across WSL/Linux environments.

## 4. Differentiation Analysis

*   **Anthropic (Claude Code):** Focuses on high-context, high-reliability coding with a strong emphasis on security sandboxes and enterprise entitlements. The pain points are largely related to billing/session limits rather than core functionality, indicating a mature but constrained product.
*   **OpenAI (Codex):** Currently in a "stability crisis" mode, heavily focused on fixing Windows regressions and resource inefficiencies (CPU/Disk usage). Their differentiation lies in deep IDE integration and MCP server reliability, but recent releases have hampered user trust.
*   **Google (Gemini CLI):** Prioritizes security hardening and internal evaluation pipelines ("Caretaker"). They are leading in multi-agent architecture discussions, specifically around recovery logic and permission enforcement, distinguishing themselves through rigorous safety and observability features.
*   **Moonshot AI (Kimi Code):** Differentiates via cross-device continuity (mobile/tablet support) and aggressive focus on corporate network compatibility (proxies/SSL). It targets users in restricted enterprise environments.
*   **Anomaly (OpenCode):** Stands out with unique features like LaTeX rendering, PDF support, and PWA capabilities. It appeals to developers needing rich media handling and web-like accessibility within a CLI tool.
*   **Badlogic (Pi):** Focuses on hybrid local/cloud model integration, particularly `llama.cpp` support and flexible provider routing. It targets privacy-conscious developers and those requiring offline capabilities alongside cloud models.
*   **Alibaba (Qwen Code):** Emphasizes performance optimization (cold-start latency) and developer telemetry (TPS/TTFT metrics). It appeals to teams monitoring cost and efficiency closely.
*   **DeepSeek (CodeWhale):** Undergoing a major architectural overhaul and rebranding. It differentiates by offering a highly modular, Rust-based architecture with explicit workflow gates and lane-based orchestration, targeting power users who need fine-grained control over agent lifecycles.

## 5. Community Momentum & Maturity

*   **High Momentum & Rapid Iteration:** **Gemini CLI** and **OpenAI Codex** show the highest volume of PR activity and issue engagement, reflecting rapid development cycles but also significant instability. **DeepSeek (CodeWhale)** is in a high-growth phase with major architectural refactoring driving intense community contribution.
*   **Mature but Stable:** **Claude Code** shows high issue engagement but lower PR velocity, suggesting a more stable codebase where issues are often usage/configuration-related or backend service problems rather than client-side bugs.
*   **Niche/Developing:** **Kimi Code** and **Qwen Code** have active communities focused on specific regional or infrastructural needs (proxies, metrics), while **Pi** serves a specialized audience for local model enthusiasts.

## 6. Trend Signals

*   **"Opus 5" Era Impact:** The introduction of new high-capacity models is causing immediate fragmentation in context handling and billing logic. Developers must prepare for variable context limits and potential "silent fallbacks" when models are unavailable in certain regions or plans.
*   **Security as a Core Feature:** The industry is moving beyond basic API key storage. There is a clear trend toward "security-first" CLIs, featuring path traversal prevention, deterministic redaction, and strict OAuth token lifecycle management.
*   **Enterprise Readiness Gap:** Despite advanced capabilities, tools like Codex and Gemini still struggle with basic enterprise requirements like proxy support, consistent authentication, and predictable resource usage (CPU/Memory). This remains the biggest barrier to adoption in large organizations.
*   **Observability is King:** The demand for detailed telemetry (TPS, TTFT, subagent tracing, dry-run previews) indicates that developers are treating AI agents as critical infrastructure components that require monitoring and debugging tools comparable to traditional software systems.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Date:** 2026-07-25  
**Source:** [anthropics/skills](https://github.com/anthropics/skills)

### 1. Top Skills Ranking
*Based on community engagement, bug reports, and feature requests in the top 20 most-discussed Pull Requests.*

1.  **Skill Creator & Evaluation Framework Fixes**
    *   **PRs:** [#1298](https://github.com/anthropics/skills/pull/1298), [#1323](https://github.com/anthropics/skills/pull/1323), [#1099](https://github.com/anthropics/skills/pull/1099), [#1050](https://github.com/anthropics/skills/pull/1050)
    *   **Functionality:** Core tooling for creating, testing, and optimizing new skills (`run_eval.py`, `run_loop.py`).
    *   **Discussion Highlights:** Heavy focus on critical bugs preventing skill optimization loops from functioning correctly (e.g., `recall=0%` on all queries). Significant effort spent on Windows compatibility issues involving subprocess pipes, encoding (`cp1252` vs UTF-8), and file path resolution.
    *   **Status:** Open

2.  **Frontend Design Skill Improvement**
    *   **PR:** [#210](https://github.com/anthropics/skills/pull/210)
    *   **Functionality:** Guidelines for generating high-quality frontend code (HTML/CSS/JS).
    *   **Discussion Highlights:** Refinement of instructions to ensure they are actionable within a single conversation context, reducing hallucination and improving coherence.
    *   **Status:** Open

3.  **Document Processing Skills (PDF, DOCX, ODT)**
    *   **PRs:** [#538](https://github.com/anthropics/skills/pull/538), [#486](https://github.com/anthropics/skills/pull/486), [#541](https://github.com/anthropics/skills/pull/541)
    *   **Functionality:** Handling OpenDocument Format (ODT), PDF parsing/reference correction, and DOCX tracked changes/bookmark integrity.
    *   **Discussion Highlights:** Fixing case-sensitivity errors in file references and preventing document corruption when merging tracked changes with existing bookmarks in OOXML structures. Addition of native ODT support.
    *   **Status:** Open

4.  **Quality & Security Analysis Meta-Skills**
    *   **PR:** [#83](https://github.com/anthropics/skills/pull/83)
    *   **Functionality:** `skill-quality-analyzer` and `skill-security-analyzer` to evaluate other skills against structure, documentation, and security standards.
    *   **Discussion Highlights:** Introduction of meta-skills to standardize skill quality and security auditing before deployment.
    *   **Status:** Open

5.  **Specialized Domain Skills (Color, Testing, Retro Gaming)**
    *   **PRs:** [#1302](https://github.com/anthropics/skills/pull/1302), [#723](https://github.com/anthropics/skills/pull/723), [#525](https://github.com/anthropics/skills/pull/525)
    *   **Functionality:** `color-expert` (ISCC-NBS, color spaces), `testing-patterns` (unit/integration testing guidelines), and `pyxel` (retro game development).
    *   **Discussion Highlights:** Diversification into niche professional domains (design theory, software engineering best practices) and creative coding tools.
    *   **Status:** Open

### 2. Community Demand Trends
*Derived from the top 15 most-discussed Issues.*

*   **Trust & Security Governance:** The highest-engagement issue ([#492](https://github.com/anthropics/skills/issues/492)) highlights a critical community concern regarding namespace impersonation. Users are demanding stricter verification mechanisms to distinguish official Anthropic skills from community contributions to prevent trust boundary abuse.
*   **Enterprise Collaboration Features:** Issue [#228](https://github.com/anthropics/skills/issues/228) shows strong demand for native org-wide skill sharing within Claude.ai, moving away from manual file distribution (Slack/Teams) toward integrated shared libraries.
*   **Cross-Platform Compatibility:** Recurring themes in issues [#1061](https://github.com/anthropics/skills/issues/1061) and PRs like [#1099](https://github.com/anthropics/skills/pull/1099) indicate that robust Windows support (encoding, subprocess handling) is a prerequisite for widespread skill creation adoption.
*   **Advanced Agent Capabilities:** Emerging interest in "meta-agentic" workflows, such as `compact-memory` ([#1329](https://github.com/anthropics/skills/issues/1329)) and `agent-governance` ([#412](https://github.com/anthropics/skills/issues/412)), suggests users want skills that manage long-running agent state and safety policies rather than just single-task execution.

### 3. High-Potential Pending Skills
*Active PRs with significant discussion or unique utility that may land soon.*

*   **[feat(skills): add self-audit — mechanical verification + four-dimension reasoning quality gate (v1.3.0)](#1367)**
    *   **Author:** YuhaoLin2005
    *   **Potential:** This PR introduces a universal pre-delivery audit mechanism. If merged, it could become a mandatory standard for all high-reliability skills, ensuring output integrity before the user sees it.
    *   **Status:** Open

*   **[Add color-expert skill](#1302)**
    *   **Author:** meodai
    *   **Potential:** Fills a gap in design-oriented workflows by providing precise color space conversions and naming conventions. Likely to be adopted by UI/UX teams using Claude Code.
    *   **Status:** Open

*   **[Add comprehensive system documentation and flowcharts](#95)**
    *   **Author:** TylerALofall
    *   **Potential:** While labeled as documentation, this PR establishes a template for complex system architecture skills. It addresses the need for better visual and structural understanding in enterprise-grade skills.
    *   **Status:** Open

### 4. Skills Ecosystem Insight
The community's most concentrated demand is for **robust evaluation infrastructure and security governance**, as evidenced by the disproportionate attention paid to fixing the broken `skill-creator` evaluation loops and addressing namespace impersonation risks, indicating that trust and reliability are currently more critical barriers to adoption than feature volume.

---

# Claude Code Community Digest
**Date:** 2026-07-25

## 1. Today's Highlights
Anthropic released v2.1.220 and v2.1.219, introducing the new default Opus model (`claude-opus-5`) with 1M context and enhanced sandbox security controls. Community attention is heavily focused on a critical session limit bug affecting Max plan users and widespread authentication failures in Remote Control and desktop environments. Additionally, several users report context management issues and model persistence bugs following the recent updates.

## 2. Releases
*   **v2.1.220**: General bug fixes and reliability improvements.
    *   [View Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.220)
*   **v2.1.219**: Major feature update including the new `claude-opus-5` model (1M context, fast mode pricing), a new `sandbox.network.strictAllowlist` setting for stricter network isolation, and a `DirectoryAdded` hook.
    *   [View Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.219)

## 3. Hot Issues
1.  **[BUG] Max Plan Session Limits Exhausted Abnormally Fast** (#38335)
    *   **Why it matters:** Affects core usability for high-tier subscribers; credits are draining significantly faster than expected.
    *   **Reaction:** Extremely high engagement (805 comments, 470 👍).
2.  **[Enhancement] Allow Removal of Local Folders from Cowork Context** (#40043)
    *   **Why it matters:** Improves context window efficiency for large Cowork projects by allowing selective exclusion of local folders.
    *   **Reaction:** Strong community support (21 comments, 63 👍).
3.  **[BUG] "Buy Credits" Button Disabled & HTTP 429 Errors** (#62644)
    *   **Why it matters:** Blocks free-tier users from upgrading or adding funds due to incorrect limit displays and billing API errors.
    *   **Reaction:** Active reporting (13 comments).
4.  **[BUG] API Error: Connection Closed Mid-Response** (#69336)
    *   **Why it matters:** Indicates unstable network handling or server-side socket issues causing interrupted completions.
    *   **Reaction:** Technical discussion on root causes (10 comments, 11 👍).
5.  **[BUG] Persistent Mid-Stream ECONNRESET on Large-Context Sessions** (#51164)
    *   **Why it matters:** Affects stability during long-running, high-context tasks, particularly on macOS.
    *   **Reaction:** Closed as stale but highlights ongoing networking fragility (8 comments).
6.  **[BUG] Fable 5 Gated Behind Usage Credits Dialog** (#79360)
    *   **Why it matters:** Authentication scope issues prevent Max plan users from accessing Fable 5 despite having credits.
    *   **Reaction:** Significant frustration among security-focused developers (7 comments, 35 👍).
7.  **[BUG] Socket Connection Closed Unexpectedly (Linux)** (#67766)
    *   **Why it matters:** Intermittent server-initiated FIN packets disrupt heavy interactive use, requiring packet capture analysis to diagnose.
    *   **Reaction:** Detailed technical debugging (6 comments, 4 👍).
8.  **[BUG] Remote Control 401s on Valid OAuth Tokens** (#78469)
    *   **Why it matters:** Breaks remote development workflows intermittently, indicating backend fleet authentication inconsistencies.
    *   **Reaction:** Critical for enterprise/remote teams (6 comments).
9.  **[Bug] Fable 5 Safety Classifier False Positives** (#66697)
    *   **Why it matters:** Legitimate defensive security audits are being blocked by over-aggressive safety filters.
    *   **Reaction:** Closed, but underscores tension between security tools and safety guardrails (5 comments).
10. **[Bug] Fable Mid-Turn Messages Invisible to Operator** (#77798)
    *   **Why it matters:** UI/UX bug where thinking blocks or mid-turn outputs are not rendered correctly in the terminal.
    *   **Reaction:** Reported as a display/rendering issue (4 comments).

## 4. Key PR Progress
1.  **feat: Add context-safety-net plugin to mitigate auto-compact context loss** (#80883)
    *   **Description:** Addresses silent context degradation during auto-compaction by introducing a plugin that preserves "anchor" files and state, preventing the agent from working blindly.
    *   **Link:** [PR #80883](https://github.com/anthropics/claude-code/pull/80883)

*(Note: Only 1 PR was provided in the source data.)*

## 5. Feature Request Trends
*   **Granular Context Management:** Users are requesting better control over what data enters the context window, specifically through folder exclusions in Cowork sessions (#40043) and more deterministic context preservation plugins (#80883).
*   **Subagent Policy Customization:** A request for advanced policy controls in subagent resolution, allowing relative bias and cap/floor bounds (#81050).
*   **Connector Reliability:** Demand for stable third-party integrations, specifically Gmail, which is showing connection status without functional availability (#81044).

## 6. Developer Pain Points
*   **Authentication & Entitlements:** Recurring 401 errors and session limit bugs suggest instability in the OAuth and entitlement backend, particularly affecting Remote Control, Desktop apps, and specific models like Fable 5 (#79360, #78469, #38335).
*   **Context Window Discrepancies:** Users are confused by inconsistent context reporting between CLI (1M) and Desktop (200K) versions, with auto-compaction failing to trigger appropriately (#81039, #80642).
*   **Model Persistence & Defaults:** The introduction of `claude-opus-5` as default has caused silent fallbacks and preference overwrites, especially in enterprise orgs where the new model may not be available (#81025, #81045).
*   **Networking Instability:** Frequent reports of mid-stream disconnections (`ECONNRESET`, socket closures) across Linux, macOS, and iOS platforms indicate systemic network handling issues (#69336, #67766, #71616).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest | 2026-07-25

### 1. Today's Highlights
The Codex community is actively addressing critical stability regressions in the Windows Desktop app (v26.721), particularly regarding Git detection, multi-root project crashes, and GPU process failures during screenshots. Concurrently, significant backend improvements have landed in the CLI and extensions, focusing on Model Context Protocol (MCP) reliability, ephemeral thread forking, and enterprise plan support.

### 2. Releases
*   **Rust SDK (`rust-v0.146.0-alpha`)**: A rapid succession of alpha releases from `alpha.6` through `alpha.10` were published in the last 24 hours. These updates likely address internal refactoring or bug fixes preceding a stable release.
    *   [Release 0.146.0-alpha.10](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.10)
    *   [Release 0.146.0-alpha.9](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.9)
    *   [Release 0.146.0-alpha.8](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.8)
    *   [Release 0.146.0-alpha.7](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.7)
    *   [Release 0.146.0-alpha.6](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.6)

### 3. Hot Issues
1.  **[Windows] Orphaned Git Processes** (#17229): Users report `git.exe` and `conhost.exe` processes spawning repeatedly and leaving orphaned instances. High engagement (33 comments) indicates this is a persistent annoyance affecting performance and resource management.
    *   [Issue #17229](https://github.com/openai/codex/issues/17229)
2.  **[App] Silent `~/Documents/Codex` Creation** (#20880): The app creates an empty folder on every launch without user consent, which developers find intrusive. It has garnered 39 👍s, showing strong community alignment against silent file system modifications.
    *   [Issue #20880](https://github.com/openai/codex/issues/20880)
3.  **[Windows] Desktop Unstartable After Adding Second Folder** (#35057): A recent regression where adding a second root folder to a project causes the app to freeze on an error screen. Critical for users managing multi-repo workspaces.
    *   [Issue #35057](https://github.com/openai/codex/issues/35057)
4.  **[Extension] Prompts Disappear Before Queueing** (#25928): In VS Code/Cursor extensions, submitted prompts vanish randomly before entering the processing queue. This disrupts workflow continuity and causes data loss anxiety.
    *   [Issue #25928](https://github.com/openai/codex/issues/25928)
5.  **[Windows] Severe CPU/Disk Usage via Parallel Git Commands** (#20933): Opening projects triggers parallel `git add -A` and `rev-parse` commands, causing high I/O and CPU spikes. This impacts large monorepos significantly.
    *   [Issue #20933](https://github.com/openai/codex/issues/20933)
6.  **[Windows] GPU Crash on Screenshot** (#34133): Capturing screenshots via the in-app browser crashes the GPU process if `vk_swiftshader.dll` is rejected by Code Integrity. This breaks agent workflows relying on visual context.
    *   [Issue #34133](https://github.com/openai/codex/issues/34133)
7.  **[Remote] Notifications Fail** (#20930): Notifications do not trigger when using Codex with remote connections (e.g., macOS desktop + Linux remote). This hinders asynchronous workflows.
    *   [Issue #20930](https://github.com/openai/codex/issues/20930)
8.  **[CLI] Premature Turn Completion** (#27352): The CLI marks a turn complete after a progress message, stopping the main thread before follow-up tool calls are executed. This breaks complex subagent workflows.
    *   [Issue #27352](https://github.com/openai/codex/issues/27352)
9.  **[Model] GPT-5.6 Serialization Inefficiency** (#35050): GPT-5.6 often serializes independent Code Mode calls instead of batching them, leading to higher token usage. Explicit batching reduced costs by 27–45%, highlighting a need for auto-batching improvements.
    *   [Issue #35050](https://github.com/openai/codex/issues/35050)
10. **[Windows] WSL Repo Detection Failure** (#35119): Recent updates mark valid WSL repositories as non-Git, reporting "Git is unavailable." This breaks integration for developers working in WSL2 environments.
    *   [Issue #35119](https://github.com/openai/codex/issues/35119)

### 4. Key PR Progress
1.  **Skip Plugin MCP Filtering When No Allowlists Configured** (#35280): Fixes false positives in plugin security filtering by ensuring MCP servers are only filtered if allowlists are explicitly defined.
    *   [PR #35280](https://github.com/openai/codex/pull/35280)
2.  **Trace Remote Exec-Server Connection Setup** (#35275): Enhances observability by preserving tracing spans during lazy remote environment startup, covering connection, registry, and WebSocket stages.
    *   [PR #35275](https://github.com/openai/codex/pull/35275)
3.  **Include Code-Mode Tool Names in Responses Lite Metadata** (#35271): Adds `code_mode_tool_names` to metadata, mapping identifiers to structured `ToolName` for better client-side handling and debugging.
    *   [PR #35271](https://github.com/openai/codex/pull/35271)
4.  **Integrate Experimental Credential Broker** (#29752): Allows Codex core to opt into proxy-owned credential brokering, ensuring managed child processes retain dummy values across shell lifecycles.
    *   [PR #29752](https://github.com/openai/codex/pull/29752)
5.  **Harden Network Approval Cancellation** (#35267): Improves concurrency safety by scoping pending approvals to turns/executions and resolving waiting requests upon cancellation.
    *   [PR #35267](https://github.com/openai/codex/pull/35267)
6.  **Disable In-Process Code-Mode Host Fallback** (#35266): Introduces a configuration option to fail explicitly rather than falling back to embedded V8 when the standalone host fails, aiding in debugging host issues.
    *   [PR #35266](https://github.com/openai/codex/pull/35266)
7.  **Sign Bundled macOS Helper Binaries** (#35264): Moves the fetching of `rg` and zsh to before the signing stage in the macOS workflow, ensuring notarization covers all bundled executables.
    *   [PR #35264](https://github.com/openai/codex/pull/35264)
8.  **Track Remote Plugin IDs in Analytics** (#35262): Propagates `remote_plugin_id` to skill invocation facts, enabling accurate attribution of remote plugin usage in analytics.
    *   [PR #35262](https://github.com/openai/codex/pull/35262)
9.  **Support Ephemeral Forks of Paginated Threads** (#35251): Enables creating ephemeral forks from paginated history when `excludeTurns: true`, allowing lighter-weight experimentation without full rollout paths.
    *   [PR #35251](https://github.com/openai/codex/pull/35251)
10. **Refresh Managed MCP Requirements for Active Threads** (#35213): Ensures that updated MCP server constraints and plugin requirements are propagated to active threads during config reloads.
    *   [PR #35213](https://github.com/openai/codex/pull/35213)

### 5. Feature Request Trends
*   **Improved Multi-Repo Support**: Multiple issues (#35057, #35195, #35119) highlight friction with multi-root projects and WSL integration, indicating a need for more robust workspace management in the desktop app.
*   **Granular Control Over Background Processes**: Users are requesting better visibility and control over background tasks like Git status checks (#17229, #20933) and silent folder creation (#20880).
*   **Enterprise & Security Features**: Interest in configurable MCP endpoints (#31307) and enterprise plan support (#35238) suggests a growing demand for customizable security and infrastructure integration.
*   **Workflow Continuity**: Requests for reliable notifications (#20930) and prompt persistence (#25928) reflect a desire for more resilient async workflows.

### 6. Developer Pain Points
*   **Windows Stability Regressions**: The July 24–25 update cycle introduced severe bugs on Windows, including crashes on launch (#35284, #31153), GPU process failures (#34133), and Git detection issues (#35179, #35119). This is currently the primary source of developer frustration.
*   **Resource Inefficiency**: Excessive disk I/O and CPU usage due to redundant Git operations (#20933) and SQLite writes (#35092) are degrading performance, especially on larger projects.
*   **Model Behavior Inconsistencies**: Users are encountering unexpected model routing (e.g., GPT-5.6 Pro behaving like Instant/Mini #34677) and inefficient serialization (#35050), leading to unpredictable costs and latency.
*   **CLI Session Management**: Issues with premature turn completion (#27352) and database locking (#31184) disrupt automated and long-running CLI sessions.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest: 2026-07-25

## 1. Today's Highlights
The community focus remains heavily on stabilizing the multi-agent architecture, with significant discussions around subagent recovery, generalist agent hangs, and permission enforcement. Concurrently, major security hardening is underway via PRs addressing path traversal, OAuth token leakage, and credential storage validation, while internal infrastructure efforts continue to advance the "Caretaker" agent pipeline for issue triage and evaluation.

## 2. Releases
No new official releases were published in the last 24 hours. However, the nightly release workflow for `v0.54.0-nightly.20260725.g3818efbbf` encountered a failure today, which may impact testing for users relying on the latest pre-release builds.
*   **Nightly Failure:** [Issue #28533](https://github.com/google-gemini/gemini-cli/issues/28533)

## 3. Hot Issues
These issues are driving the most engagement and represent critical blockers or feature gaps.

1.  **Subagent Recovery Logic Flaw**
    *   **Why it matters:** Subagents reporting "GOAL success" despite hitting turn limits misleads the main agent, causing silent failures in complex workflows.
    *   **Reaction:** High priority (P1), 12 comments.
    *   [Issue #22323](https://github.com/google-gemini/gemini-cli/issues/22323)
2.  **Generalist Agent Infinite Hangs**
    *   **Why it matters:** A core stability bug where deferring to the generalist agent causes indefinite freezes, requiring workarounds like disabling subagents.
    *   **Reaction:** High priority (P1), 8 upvotes, 8 comments.
    *   [Issue #21409](https://github.com/google-gemini/gemini-cli/issues/21409)
3.  **Auto Memory Retry Loops**
    *   **Why it matters:** Low-signal sessions remain unprocessed indefinitely, cluttering memory context and degrading retrieval accuracy.
    *   **Reaction:** Priority P2, 5 comments.
    *   [Issue #26522](https://github.com/google-gemini/gemini-cli/issues/26522)
4.  **Security: Deterministic Redaction**
    *   **Why it matters:** Current Auto Memory logging risks sending sensitive data to models before redaction occurs; this issue tracks implementing pre-context redaction.
    *   **Reaction:** Priority P2, 4 comments.
    *   [Issue #26525](https://github.com/google-gemini/gemini-cli/issues/26525)
5.  **Shell Command Stuck State**
    *   **Why it matters:** Simple CLI commands leave the shell in an "Awaiting user input" state after completion, breaking automation flows.
    *   **Reaction:** Priority P1, 3 upvotes, 4 comments.
    *   [Issue #25166](https://github.com/google-gemini/gemini-cli/issues/25166)
6.  **Browser Agent Resilience**
    *   **Why it matters:** Lack of automatic session takeover for locked browser profiles hinders long-running web automation tasks.
    *   **Reaction:** Feature request/P3, 4 comments.
    *   [Issue #22232](https://github.com/google-gemini/gemini-cli/issues/22232)
7.  **Wayland Browser Failures**
    *   **Why it matters:** The browser subagent fails completely on Wayland compositors, excluding a significant portion of Linux users.
    *   **Reaction:** Priority P1, 4 comments.
    *   [Issue #21983](https://github.com/google-gemini/gemini-cli/issues/21983)
8.  **Symlink Agent Recognition**
    *   **Why it matters:** Users cannot use symlinks for custom agents in `~/.gemini/agents/`, limiting modular agent management setups.
    *   **Reaction:** P3, 4 comments.
    *   [Issue #20079](https://github.com/google-gemini/gemini-cli/issues/20079)
9.  **Tool Limit 400 Error**
    *   **Why it matters:** The CLI crashes with a 400 error when more than 400 tools are registered, indicating poor scalability in tool selection logic.
    *   **Reaction:** P2, 3 comments.
    *   [Issue #24246](https://github.com/google-gemini/gemini-cli/issues/24246)
10. **Destructive Behavior Control**
    *   **Why it matters:** Agents frequently use dangerous commands (e.g., `git reset --force`) when safer alternatives exist, raising safety concerns.
    *   **Reaction:** P2, 3 comments.
    *   [Issue #22672](https://github.com/google-gemini/gemini-cli/issues/22672)

## 4. Key PR Progress
Significant activity is observed in security fixes, authentication robustness, and internal evaluation pipelines.

1.  **Prevent Path Traversal in A2A Server**
    *   **Impact:** Critical security fix preventing arbitrary file read via `restore` command arguments.
    *   [PR #28353](https://github.com/google-gemini/gemini-cli/pull/28353)
2.  **Fix MaxListeners & Auth Loop**
    *   **Impact:** Resolves infinite API retry loops and authentication hang-ups on Windows OAuth flows.
    *   [PR #28348](https://github.com/google-gemini/gemini-cli/pull/28348)
3.  **SSR Pipeline Infrastructure (Series)**
    *   **Impact:** Multiple PRs (#28435, #28433, #28434, #28432, #28431) establishing the backbone for the new SSR Code Generation Pipeline, including Firestore locking, Cloud Run jobs, and agent orchestration.
    *   [PR #28435](https://github.com/google-gemini/gemini-cli/pull/28435) | [PR #28433](https://github.com/google-gemini/gemini-cli/pull/28433) | [PR #28434](https://github.com/google-gemini/gemini-cli/pull/28434) | [PR #28432](https://github.com/google-gemini/gemini-cli/pull/28432) | [PR #28431](https://github.com/google-gemini/gemini-cli/pull/28431)
4.  **Caretaker Eval Framework**
    *   **Impact:** Introduces LLM-as-a-Judge rubrics and parallel benchmark runners for evaluating issue triage accuracy.
    *   [PR #28530](https://github.com/google-gemini/gemini-cli/pull/28530) | [PR #28532](https://github.com/google-gemini/gemini-cli/pull/28532)
5.  **Enforce HTTPS for Credentials**
    *   **Impact:** Prevents cleartext transmission of Application Default Credentials (ADC).
    *   [PR #28517](https://github.com/google-gemini/gemini-cli/pull/28517)
6.  **Native Fetch for OAuth Exchange**
    *   **Impact:** Fixes "Premature close" errors during login on headless VPS environments by using native Node.js fetch instead of polyfills.
    *   [PR #28446](https://github.com/google-gemini/gemini-cli/pull/28446)
7.  **MCP OAuth Token Refresh Fix**
    *   **Impact:** Corrects credential deletion and refresh failures for dynamically registered MCP servers.
    *   [PR #28481](https://github.com/google-gemini/gemini-cli/pull/28481)
8.  **Normalize CRLF Line Endings**
    *   **Impact:** Fixes diff view highlighting failures on Windows in Gemini Code Assist.
    *   [PR #28531](https://github.com/google-gemini/gemini-cli/pull/28531)
9.  **Filter Thought Parts from History**
    *   **Impact:** Prevents internal monologue leakage into conversation history when context management is disabled.
    *   [PR #28509](https://github.com/google-gemini/gemini-cli/pull/28509)
10. **File Keychain Tag Validation**
    *   **Impact:** Enforces strict 128-bit tag length validation for secure credential storage.
    *   [PR #28523](https://github.com/google-gemini/gemini-cli/pull/28523)

## 5. Feature Request Trends
*   **AST-Aware Navigation:** Strong interest in using Abstract Syntax Tree (AST) analysis for more precise codebase mapping and file reading, reducing token waste and improving context accuracy ([Issue #22745](https://github.com/google-gemini/gemini-cli/issues/22745)).
*   **Agent Self-Awareness & Documentation:** Requests for the CLI to better understand its own capabilities, hotkeys, and flags to act as its own expert guide ([Issue #21432](https://github.com/google-gemini/gemini-cli/issues/21432)).
*   **Subagent Visibility:** Demand for better observability of subagent trajectories, specifically through `/chat share` commands to facilitate debugging and evaluation ([Issue #22598](https://github.com/google-gemini/gemini-cli/issues/22598)).
*   **Resilient Browser Automation:** Features aimed at automatic session takeover and lock recovery for the browser agent to handle persistent sessions more robustly ([Issue #22232](https://github.com/google-gemini/gemini-cli/issues/22232)).

## 6. Developer Pain Points
*   **Agent Stability & Reliability:** The most frequent complaints revolve around agents hanging indefinitely ([Issue #21409](https://github.com/google-gemini/gemini-cli/issues/21409)), getting stuck in interactive prompts ([Issue #22465](https://github.com/google-gemini/gemini-cli/issues/22465)), or failing to execute simple shell commands correctly ([Issue #25166](https://github.com/google-gemini/gemini-cli/issues/25166)).
*   **Configuration Ignored:** Users report that settings defined in `settings.json` (such as `maxTurns`) are being ignored by specific subagents like the Browser Agent ([Issue #22267](https://github.com/google-gemini/gemini-cli/issues/22267)), leading to inconsistent behavior across different agent types.
*   **Security & Privacy Leaks:** Concerns persist regarding memory systems retaining low-signal data ([Issue #26522](https://github.com/google-gemini/gemini-cli/issues/26522)) and potential leakage of secrets or internal thoughts in logs and history ([Issue #26525](https://github.com/google-gemini/gemini-cli/issues/26525), [PR #28509](https://github.com/google-gemini/gemini-cli/pull/28509)).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-07-25

## 1. Today's Highlights
The latest release, **v1.0.75**, introduces support for Claude Opus 5, expanding the model options available to users. However, the community is currently grappling with several significant regressions in v1.0.74/75, including persistent session loading loops, memory leaks during session resume, and broken keyboard interrupts. There is also a surge in reports regarding permission gating false positives in plan mode and issues with plugin marketplace persistence.

## 2. Releases
*   **v1.0.75 (2026-07-24):** Added support for **Claude Opus 5**.
    *   *Link:* [GitHub Release v1.0.75](https://github.com/github/copilot-cli/releases/tag/v1.0.75)

## 3. Hot Issues
These issues have generated the most community engagement or represent critical functional blockers.

1.  **Mouse scroll regression in terminal history (#2205)**
    *   *Why it matters:* A usability regression where mouse scrolling navigates input history instead of agent output history, breaking basic navigation.
    *   *Reaction:* High engagement (14 👍, 13 comments).
    *   *Link:* [Issue #2205](https://github.com/github/copilot-cli/issues/2205)
2.  **Feature Request: `awaitingUserInput` hook (#1128)**
    *   *Why it matters:* Addresses a gap in observability; users need to trigger actions when the CLI is idle/waiting, not just on submission.
    *   *Reaction:* Strong support (28 👍).
    *   *Link:* [Issue #1128](https://github.com/github/copilot-cli/issues/1128)
3.  **Plan mode regression blocking shell commands (#4188)**
    *   *Why it matters:* Critical workflow breakage where read-only tools like `gh` are incorrectly blocked in plan mode, hindering investigation steps.
    *   *Reaction:* Active discussion on scope of "modification" vs. "reading".
    *   *Link:* [Issue #4188](https://github.com/github/copilot-cli/issues/4188)
4.  **Auto-compaction fails to prevent CAPI 5MB limit errors (#4183)**
    *   *Why it matters:* Long sessions crash due to API body limits despite auto-compaction features, indicating a logic flaw in how context is serialized vs. token count.
    *   *Reaction:* 10 👍, highlights scalability issues.
    *   *Link:* [Issue #4183](https://github.com/github/copilot-cli/issues/4183)
5.  **Zombie process accumulation (#4163) [CLOSED]**
    *   *Why it matters:* Child processes were not being reaped, leading to system resource leaks.
    *   *Reaction:* Resolved, but indicates previous stability concerns.
    *   *Link:* [Issue #4163](https://github.com/github/copilot-cli/issues/4163)
6.  **Broken light theme accessibility (#3773)**
    *   *Why it matters:* Poor contrast makes the CLI unusable for users relying on light themes.
    *   *Reaction:* 3 👍, ongoing visual bug.
    *   *Link:* [Issue #3773](https://github.com/github/copilot-cli/issues/3773)
7.  **Eternally loading sessions (#4214)**
    *   *Why it matters:* Users report infinite loading states ("Loading: 1 skill") and potential billing confusion.
    *   *Reaction:* 2 👍, high severity for daily use.
    *   *Link:* [Issue #4214](https://github.com/github/copilot-cli/issues/4214)
8.  **Ctrl+C no longer cancels runs (#4235) [CLOSED]**
    *   *Why it matters:* Regression preventing users from interrupting long-running or stuck agent turns.
    *   *Reaction:* Resolved, but highlights UI control regressions.
    *   *Link:* [Issue #4235](https://github.com/github/copilot-cli/issues/4235)
9.  **Plan mode false positives on `gh api` GETs (#4220)**
    *   *Why it matters:* Extends issue #4188; even explicit HTTP GETs are flagged as potential workspace modifications.
    *   *Reaction:* 1 👍, technical nuance in permission gating.
    *   *Link:* [Issue #4220](https://github.com/github/copilot-cli/issues/4220)
10. **React/Ink render loop freeze on Windows (#4222)**
    *   *Why it matters:* The main pane freezes and swallows output due to an infinite render loop, a recurrence of a previously fixed bug.
    *   *Reaction:* 0 👍, but critical for Windows users.
    *   *Link:* [Issue #4222](https://github.com/github/copilot-cli/issues/4222)

## 4. Key PR Progress
*   **No new Pull Requests** were reported in the last 24 hours.

## 5. Feature Request Trends
*   **Enhanced Observability & Hooks:** Users are requesting more granular hooks (e.g., `awaitingUserInput`) and better status emission in non-interactive/ACP modes (`usage_update`) to integrate with external IDEs like Zed.
*   **Context Window Management:** There is a strong demand for smarter auto-compaction that respects API body size limits (5MB) rather than just token counts, and better handling of large session resumption.
*   **Plugin & Marketplace Stability:** Requests for fixing plugin installation paths and ensuring marketplace registrations persist correctly across CLI restarts.
*   **Session Configuration:** Users want configurable worktree naming and self-cleaning mechanisms to avoid clutter and confusion between session display names and underlying git branches.

## 6. Developer Pain Points
*   **Regressions in Core Stability:** The most frequent complaints involve recent regressions in v1.0.74/75, specifically:
    *   Session loading loops and infinite renders.
    *   Memory leaks (OOM) when resuming large sessions.
    *   Broken keyboard shortcuts (Ctrl+C, Ctrl+G).
*   **Permission Gating False Positives:** Developers are frustrated that "plan mode" is overly aggressive, blocking legitimate read-only operations (like `gh api get` or piping to `jq/python`) which hinders the agent's ability to investigate code safely.
*   **Plugin Ecosystem Fragility:** Issues with plugin root path construction causing installation failures, and MCP servers failing to resolve the active project directory, suggest the plugin infrastructure needs robustness improvements.
*   **Resource Leaks:** Accumulation of zombie processes and orphaned worktrees after timeouts indicates inadequate cleanup routines in the CLI lifecycle.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-25
**Source:** github.com/MoonshotAI/kimi-cli

## 1. Today's Highlights
The community is currently focused on critical connectivity and environment-specific bugs, with multiple reports regarding `kimi login` failures on Linux ARM64 and Windows TUI navigation issues. Additionally, there is significant developer interest in corporate proxy compatibility (SSL handling) and cross-device session continuity, reflected in high-engagement PRs and feature requests.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
*   **[Enhancement] Remote Control - Continue local sessions from any device (#1282)**
    *   **Why it matters:** Addresses a major workflow gap by allowing developers to continue coding sessions from mobile or other devices.
    *   **Community Reaction:** High engagement with 16 👍 and 7 comments, indicating strong demand for seamless context switching.
    *   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1282)

*   **[Bug] VS code Kimi Freezes (#2326)**
    *   **Why it matters:** Critical stability issue affecting the VS Code extension experience on Ubuntu, potentially blocking daily development workflows.
    *   **Community Reaction:** Reported by users experiencing multiple instability issues within the extension.
    *   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2326)

*   **[Bug] Login failed: Cannot connect to host auth.kimi.com:443 (#1070)**
    *   **Why it matters:** Network reachability errors prevent authentication, a fundamental blocker for using the CLI.
    *   **Community Reaction:** Closed issue, but highlights persistent network configuration challenges for some users.
    *   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1070)

*   **[Bug] kimi login fails (#2556)**
    *   **Why it matters:** New report of OAuth login failure on Linux ARM64, suggesting potential architecture-specific authentication bugs.
    *   **Community Reaction:** Fresh report (created today) from a user who recently acquired ARM-based hardware.
    *   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2556)

*   **[Bug] Windows version herdr arrow key selection failure (#2521)**
    *   **Why it matters:** Basic UI navigation is broken in the Windows terminal interface (`herdr`), degrading user experience on a major OS.
    *   **Community Reaction:** Active discussion on the specific behavior of keyboard inputs in the Windows environment.
    *   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2521)

## 4. Key PR Progress
*   **[Fix] Respect SSL_CERT_FILE env var for corporate proxy support (#762)**
    *   **Description:** Adds support for the standard `SSL_CERT_FILE` environment variable, fixing SSL certificate verification errors for users behind corporate proxies (e.g., Zscaler, Fortinet).
    *   **Status:** Open, addressing #760.
    *   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/762)

*   **[Fix] Route MCP server log notifications to loguru instead of TUI (#1637)**
    *   **Description:** Prevents verbose MCP server logs (e.g., from SearXNG) from cluttering the Terminal User Interface by routing them to `loguru` instead of the default Rich handler.
    *   **Status:** Open, improving TUI cleanliness and usability.
    *   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/1637)

## 5. Feature Request Trends
*   **Cross-Device Continuity:** The top requested feature is "Remote Control" (#1282), showing a desire for mobile/tablet integration and session handoff capabilities.
*   **Enterprise/Proxy Compatibility:** There is a clear trend toward supporting complex corporate network environments, specifically regarding SSL certificate handling and proxy configurations.

## 6. Developer Pain Points
*   **Authentication Instability:** Multiple issues (#1070, #2556) and PRs suggest that `kimi login` is a fragile entry point, particularly on non-standard setups (Linux ARM64, corporate networks).
*   **Platform-Specific UI Bugs:** Distinct issues are arising for Windows (arrow keys in `herdr` #2521) and VS Code extensions (freezing #2326), indicating fragmentation in platform-specific testing or implementation.
*   **Log Noise in TUI:** Users interacting with MCP servers are frustrated by log output flooding the terminal interface, impacting readability (#1637).

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest | 2026-07-25

## 1. Today's Highlights
OpenCode v1.18.5 has been released, focusing on stabilizing core model interactions for Claude, OpenAI, and Mistral, alongside critical symlink path preservation in search results. The community is actively addressing complex session management bugs, particularly around compaction replay errors and subagent context loss during interruptions. Significant UI/UX progress is visible with new desktop browser panes, PWA support discussions, and fixes for LaTeX rendering and Safari IME composition issues.

## 2. Releases
**v1.18.5**
*   **Core Stability:** Improved handling of Claude’s adaptive thinking across varied response shapes.
*   **OpenAI Fix:** Resolved phase handling issues in the OpenAI Responses API that could disrupt conversation continuity.
*   **Mistral Stabilization:** Preserved reasoning history across turns to prevent context loss.
*   **Search Improvements:** Fixed grep to preserve symlink paths in search results (@remixz).

## 3. Hot Issues
1.  **[Compaction Replay Injection](https://github.com/anomalyco/opencode/issues/13838)** - *16 comments, 4 👍*
    **Why it matters:** Auto-compaction injects a fake user message ("What did we do so far?"), causing models to generate unwanted summaries. This breaks seamless session resumption.
2.  **[Hot Reloading Configuration](https://github.com/anomalyco/opencode/issues/10899)** - *9 comments, 1 👍*
    **Why it matters:** Currently requires full app restarts for config changes, severely impacting developer workflow efficiency.
3.  **[TUI Server Error on Fork](https://github.com/anomalyco/opencode/issues/29262)** - *6 comments, 1 👍*
    **Why it matters:** `--continue --fork` triggers a "dummy" session ID error, confusing users despite the fork appearing usable.
4.  **[macOS Certificate Errors](https://github.com/anomalyco/opencode/issues/21206)** - *6 comments, 1 👍*
    **Why it matters:** Intermittent `UNKNOWN_CERTIFICATE_VERIFICATION_ERROR` on macOS under proxy conditions blocks access to OpenAI/Codex endpoints.
5.  **[GPT OSS Subagent Failure](https://github.com/anomalyco/opencode/issues/27210)** - *5 comments*
    **Why it matters:** GPT OSS 120B subagents stop mid-reasoning after tool calls, returning empty results, which hinders complex multi-step tasks.
6.  **[OpenCode Go Membership Verification](https://github.com/anomalyco/opencode/issues/29207)** - *4 comments*
    **Why it matters:** Users with active subscriptions cannot verify benefits or use the tool, indicating potential billing/authentication backend issues.
7.  **[Basic PWA Support](https://github.com/anomalyco/opencode/issues/19174)** - *4 comments, 3 👍*
    **Why it matters:** The web app lacks installable mobile behavior, limiting accessibility for mobile developers.
8.  **[GitLab Duo Model Routing](https://github.com/anomalyco/opencode/issues/28970)** - *4 comments*
    **Why it matters:** Models selected via GitLab Duo are routed through original providers (e.g., Anthropic), bypassing intended enterprise routing/cost controls.
9.  **[SSH Remote File Editing](https://github.com/anomalyco/opencode/issues/29152)** - *4 comments*
    **Why it matters:** High demand for direct editing of files on remote Linux/cloud systems without local sync steps.
10. **[Prompt Async Delta Stoppage](https://github.com/anomalyco/opencode/issues/27663)** - *3 comments*
    **Why it matters:** `prompt_async` fails to publish `message.part.delta` events on subsequent calls in the same session, breaking programmatic integrations.

## 4. Key PR Progress
1.  **[Desktop: Remove Titlebar Inset in Fullscreen](https://github.com/anomalyco/opencode/pull/38793)** - Fixes macOS traffic-light titlebar insets in fullscreen mode and cleans up dead Tauri/Electron bridge code.
2.  **[App: Refresh V1 Providers After Auth](https://github.com/anomalyco/opencode/pull/38786)** - Ensures provider catalogs rebuild correctly after OAuth/API key authentication by disposing scoped instances.
3.  **[UI: LaTeX Math Rendering Support](https://github.com/anomalyco/opencode/pull/38689)** - Restores support for inline `$...$` and display `$$...$$` LaTeX syntax, fixing regressions from previous updates.
4.  **[Core: PDF Support in V2 Read Tool](https://github.com/anomalyco/opencode/pull/38797)** - Allows the V2 `Read` tool to process PDF files by removing the restrictive magic-byte check that previously rejected them.
5.  **[Core: Coalesce Pending Permission Requests](https://github.com/anomalyco/opencode/pull/36091)** - Prevents redundant permission prompts when multiple tools request the same permission type simultaneously.
6.  **[TUI: Normalize Carriage Returns](https://github.com/anomalyco/opencode/pull/36088)** - Fixes TUI parsing issues caused by LLMs emitting `\r` characters in question strings.
7.  **[TUI: Markdown Renderer for Reasoning](https://github.com/anomalyco/opencode/pull/36087)** - Corrects the display of reasoning content by using the markdown renderer instead of raw code blocks.
8.  **[Core: Enable FFF in Node Runtimes](https://github.com/anomalyco/opencode/pull/38776)** - Adds official `@ff-labs/ffi-node` runtime support and packages native addons for Node SEA builds.
9.  **[Desktop: Agent Browser Pane](https://github.com/anomalyco/opencode/pull/38627 & #38626)** - Introduces advanced native browser panes for both legacy and V2 agents, integrating semantic browser tools via isolated contexts.
10. **[Core: Lock-Free Step Settlement](https://github.com/anomalyco/opencode/pull/38743)** - Refactors the runner to join tool fibers before settlement, eliminating semaphore contention and improving performance.

## 5. Feature Request Trends
*   **Remote & Cloud Integration:** Strong interest in SSH-based file editing (#29152) and better support for cloud-hosted systems.
*   **Workflow Automation:** Requests for background session management (`opencode agents` command, #27746) and auto-formatting via LSP (#29252) indicate a desire for deeper IDE-like automation.
*   **Customization & UI:** Users want custom mascots (#16557), hidden skills configuration (#29189), and manual project reloads in Web UI (#29266) to enhance personalization and control.

## 6. Developer Pain Points
*   **Session State & Compaction:** Recurring bugs related to how sessions are saved, compacted, and resumed (e.g., fake messages injected, context loss in interrupted subagents #29209).
*   **Provider & Auth Instability:** Issues with certificate verification on proxies (#21206), incorrect model routing through third-party gateways like GitLab Duo (#28970), and subscription verification failures (#29207).
*   **Cross-Platform UI Glitches:** Specific pain points on macOS (certificate errors, titlebar insets) and Safari (IME composition aborts #38728, Linux Enter key submission issues #35887).

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest: 2026-07-25

### 1. Today's Highlights
The Pi community is focused on stabilizing the `v0.82.0` release, particularly addressing critical bugs in context compaction and local model integration with `llama.cpp`. Significant attention is being paid to Anthropic’s new Opus 5 support and resolving authentication conflicts with GitHub Copilot Enterprise, which are causing session failures for many users.

### 2. Releases
**v0.82.0** was released in the last 24 hours. The primary feature is **Constrained Tool Sampling**, allowing tools to enforce strict JSON Schema sampling or use OpenAI Lark/regex grammars, with metadata checks to prevent unsupported requests from models.

### 3. Hot Issues
1. **[Bug] Compaction using Copilot Enterprise not possible** (#6768) - *12 comments*
   Users report that context compaction fails with 421 Misdirected Request errors when using Copilot Enterprise licenses, breaking long-running sessions.
2. **[Bug] Pi automatically logs out of GitHub** (#6686) - *12 comments*
   A recurring issue where OAuth sessions invalidate unexpectedly across macOS and Linux installations, disrupting workflow continuity.
3. **[Bug] Default model cannot be a llama.cpp model** (#6952) - *10 comments*
   Startup fails with "No models available" when `defaultProvider` is set to `llama.cpp`, indicating a race condition in async model refresh.
4. **[Bug] qwen3.8-max-preview reasoning effort mismatch** (#6951) - *7 comments*
   Pi uses default reasoning tiers (minimal/low/medium/high), but Qwen requires specific mappings (low/medium/xhigh), causing configuration errors.
5. **[Bug] Scoped Anthropic API keys need necessary request params** (#6093) - *6 comments*
   Anthropic scoped keys (e.g., `sk-ant-api03-..`) are incorrectly identified as standard keys due to hardcoded prefix checks (`sk-ant-oat`), leading to auth failures.
6. **[Bug] aws-bedrock provider ignores profile** (#6957) - *5 comments*
   When AWS environment variables are present, the provider bypasses the configured profile, causing credential resolution issues.
7. **[Bug] Gemini 3.x tool-call IDs stripped** (#7047) - *4 comments*
   Multi-turn tool conversations with Gemini 3.x fail because the `id` field is dropped from function calls/responses during history replay.
8. **[Bug] pi's integration with GitHub Copilot Plugin causes token invalidation** (#6970) - *3 comments*
   Using `pi` alongside `copilot-lsp` via the plugin interface leads to token invalidation, conflicting with OAuth expectations.
9. **[Bug] Connection refused behind corporate proxy** (#7008) - *2 comments*
   HTTP/HTTPS proxy settings (`HTTP_PROXY`/`HTTPS_PROXY`) are ignored or mishandled after the v0.80.x update, breaking network access.
10. **[Bug] WSL absolute windows paths are mishandled** (#7064) - *2 comments*
    File operations (`read`, `write`, `edit`) fail on WSL2 due to incorrect path translation between Windows and Linux formats.

### 4. Key PR Progress
1. **fix(coding-agent): reject overlapping user bash commands** (#7091)
   Addresses concurrency issues by preventing overlapping bash command executions within the coding agent.
2. **feat(ai): add promptCacheKey stream option** (#6654)
   Allows overriding the prompt cache key via `StreamOptions`, improving cache efficiency for providers like OpenAI Responses and Codex.
3. **perf(tui): O(viewport) transcript rendering** (#7082)
   Optimizes TUI performance by implementing viewport windowing and container memoization, significantly reducing input lag in large transcripts.
4. **feat(ai): support Claude Opus 5 on Bedrock** (#7081)
   Adds support for Anthropic's Opus 5 on AWS Bedrock, configuring adaptive thinking and fixing error message handling.
5. **fix(coding-agent): cache llama.cpp model catalog** (#7072)
   Resolves the startup failure for default `llama.cpp` models by caching the model catalog and fixing async initialization races.
6. **feat: Add Amazon Bedrock Mantle OpenAI Responses provider** (#6216)
   Introduces a first-class provider for Amazon Bedrock Mantle’s OpenAI-compatible Responses API.
7. **fix(openai-completions): handle array content** (#7061)
   Fixes parsing issues with non-standard streaming responses (e.g., Databricks/Qwen3) where `choice.delta.content` is returned as an array.
8. **fix(coding-agent): prevent retry on tool validation errors** (#7055)
   Stops infinite retry loops caused by malformed tool arguments by distinguishing validation errors from transient API errors.
9. **feat: Add provider-neutral prompt cache contracts** (#7046)
   Standardizes prompt cache contracts across providers, improving reliability for custom provider implementations.
10. **fix(coding-agent): reload model config in picker** (#7036)
    Ensures `/model` picker reflects local `models.json` changes immediately without requiring a full session restart.

### 5. Feature Request Trends
*   **Enhanced Local Model Support:** Strong demand for better `llama.cpp` integration, specifically regarding reasoning level mapping (`thinkingLevelMap`) and stable default model selection.
*   **Proxy & Network Robustness:** Requests for improved handling of corporate proxies and HTTP/HTTPS tunneling, including upgrading dependencies like Undici to fix plain-HTTP forwarding.
*   **Advanced Caching Controls:** Interest in finer-grained control over prompt caching, such as custom cache keys and provider-neutral contract definitions.

### 6. Developer Pain Points
*   **Context Compaction Failures:** Frequent crashes or errors during session compaction, especially with enterprise licenses (Copilot) or large context windows, are a major source of friction.
*   **Authentication Fragmentation:** Inconsistent handling of API keys (Anthropic scoped keys, GitHub Copilot tokens) and credential resolution (AWS profiles) leads to unpredictable session states.
*   **Session Stability on Model Switch:** Switching models mid-session (e.g., Qwen to GPT) often breaks the conversation due to lack of context size validation or thinking block conversion.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest: 2026-07-25

## 1. Today's Highlights
Qwen Code v0.21.0 has been released with no known breaking changes, primarily focusing on CLI time-zone consistency and internal refactoring. Significant engineering efforts are underway to optimize cold-start performance through lazy-loading dependencies and enhancing the `qwen review` pipeline with stricter write contracts and drift detection. Community interest is high on subagent model flexibility, math rendering accuracy, and configurable rate-limit retries.

## 2. Releases
**v0.21.0**
*   **CLI Timezone Fix:** Resolved an issue where insight metrics (days/hours) were inconsistently calculated between UTC and local time, ensuring accurate streaks and heatmaps for non-UTC users.
*   **Refactoring:** Internal cleanup of autofix mechanisms.
*   **Status:** Stable release available; no breaking changes reported.

## 3. Hot Issues
1.  **[Bug] Last line overwritten in Static mode** [#5800]: A critical UI bug in the default TUI render path causes the final line of assistant replies to disappear if it exceeds terminal height. High visibility due to its impact on reading long responses.
2.  **[Bug] IME candidate box misalignment in Command mode** [#7684]: On macOS, input method editor candidates appear far from the cursor when the statusline spans multiple lines, hindering efficient command entry.
3.  **[Feature] Subagent model grade selection at spawn** [#7685]: Users request the ability to specify model "grades" (small/medium/high/super) for subagents via a new `model` parameter, allowing finer cost/performance control per task.
4.  **[Bug] QWEN.md multi-agent rules overridden by system prompts** [#7679]: Users report that explicit restrictions in `QWEN.md` against spawning subagents are being ignored because system-level instructions take precedence, causing unexpected resource usage.
5.  **[Bug] `tool_choice: "required"` rejected in thinking mode** [#7659]: A compatibility issue where DashScope API rejects strict tool choice parameters when thinking mode is enabled, requiring manual configuration workarounds.
6.  **[Feature] Stream rate-limit retry delay configurability** [#7658]: The current hardcoded exponential backoff (60s/120s/240s) for 429 errors is too rigid for some workflows; users want configurable retry delays.
7.  **[Bug] xterm.js parsing errors in AcpBridge** [#7631]: Frequent parsing errors reported in WeChat channels regarding `xterm.js` state, indicating potential instability in shell interaction layers.
8.  **[Bug] Unity MCP connection failure in VS Code** [#7697]: Users cannot connect to Unity MCP servers in Qwen Code VS Code extension, whereas Claude Code works, suggesting a protocol or configuration gap.
9.  **[Feature] Explicit math authoring contract** [#7700]: Requests for a standardized, source-preserving syntax for inline math to resolve inconsistencies between rendering, copying, and streaming.
10. **[Bug] Background shell relaunch on empty output** [#7626]: Long-running background jobs with buffered output cause the model to incorrectly assume failure and relaunch the process, leading to duplicate executions.

## 4. Key PR Progress
1.  **feat(review): Enforce submit-only write contract** [#7691]: Closes a security/reliability hole by ensuring `/review` runs cannot write to PRs without going through the explicit submit command, adding a cleanup tripwire.
2.  **perf(core): Lazy-load first-use dependencies** [#7686]: Addresses the 17.24 MiB eager import closure identified in Issue #7264, significantly reducing cold-start memory footprint and initialization time.
3.  **feat(web-shell): Add GitHub PR panel** [#7683]: Introduces a read-only Pull Requests tab in the Web Shell Git dialog, providing direct access to PR metadata and CI status within the IDE.
4.  **feat(review): Detect head drift at presubmit** [#7692]: Enhances the review workflow by detecting if the PR branch advanced while the review was running, capping verdicts to prevent stale analysis.
5.  **feat(stats): Show generation timing metrics** [#7677]: Implements real-time TPS and TTFT metrics in the `/stats` command, providing granular performance insights into model generation.
6.  **feat(core): Configure stream rate-limit retry delays** [#7666]: Implements configurable `retryInitialDelayMs` and `retryMaxDelayMs` to address the hardcoded limitations mentioned in Issue #7658.
7.  **feat(channels): GitHub polling adapter** [#7632]: Introduces a new architecture for GitHub notifications using a signal-vs-content separation, enabling responsive @mention handling.
8.  **fix(cli): Align inline math recognition** [#7701]: Fixes inconsistencies in recognizing single-character math expressions (`$x$`) across rendering, copying, and table modes.
9.  **feat(serve): Hot-reload workspace trust** [#7268]: Allows workspace trust policy changes to take effect in the running daemon without restarting the process.
10. **perf(web-shell): Paint git chip early** [#7680]: Optimizes the Web Shell composer by caching and pre-painting the git branch chip, improving perceived responsiveness during session startup.

## 5. Feature Request Trends
*   **Subagent Granularity:** Strong demand for dynamic model selection within subagent hierarchies (Issue #7685, PR #7702) and named tool-restriction presets for cache sharing (Issue #7625).
*   **Performance Telemetry:** Users are increasingly requesting detailed generation metrics (TPS, TTFT) to better understand latency and throughput (Issue #4252, PR #7677).
*   **Configurable Resilience:** There is a clear trend toward making retry behaviors (rate limits, API errors) configurable rather than hardcoded, allowing users to tailor resilience to their specific infrastructure (Issue #7658, PR #7666).
*   **Math & Documentation Precision:** Continued focus on improving the fidelity of mathematical rendering and documentation generation, specifically around source preservation and cross-mode consistency (Issue #7700, PR #7701).

## 6. Developer Pain Points
*   **TUI Rendering Artifacts:** Recurring issues with text overlap, blank spaces, and IME misalignment in terminal-based interfaces, particularly on macOS and WSL environments (Issues #5800, #7684, #7634).
*   **System Prompt Conflict:** Friction between user-defined `QWEN.md` rules and built-in system instructions, leading to unexpected agent behavior (Issue #7679).
*   **Cold Start Latency:** Significant pain point regarding initial load times and memory usage, driven by large eager module imports (Issue #7264, PR #7686).
*   **Background Job Management:** Difficulties in reliably monitoring long-running or buffered background shell commands, leading to false positives in execution status (Issue #7626, PR #7627).

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest
**Date:** 2026-07-25
**Source:** github.com/Hmbown/DeepSeek-TUI (CodeWhale)

## 1. Today's Highlights
The project has officially rebranded the public product to **CodeWhale**, with `deepseek-tui` deprecated in favor of the `codewhale` command and npm package. Development focus is heavily shifting toward the **v0.9.2** architecture, specifically a major refactoring of the TUI codebase and the implementation of a Fleet/Workflow/Lane/Runtime orchestration model. Several critical audit-derived bugs and performance bottlenecks are being addressed in parallel PRs.

## 2. Releases
*   **v0.9.1**: Released recently. Note that this version marks the transition where the legacy `deepseek-tui` npm package is deprecated. Users should migrate to the `codewhale` command/package. The legacy `deepseek` alias remains for technical identifier compatibility but receives no further releases.

## 3. Hot Issues
1.  **[EPIC: Staged Command-Boundary Refactor](https://github.com/Hmbown/CodeWhale/issues/2870)**
    *   *Why it matters:* Tracks the modular breakdown of the complex command-boundary logic introduced in #2791, essential for maintainability.
    *   *Community:* High engagement (17 comments) from contributors like aboimpinto focusing on clean mergeable layers.

2.  **[v0.9.2 Architecture: Fleet / Workflow / Lane / Runtime](https://github.com/Hmbown/CodeWhale/issues/4175)**
    *   *Why it matters:* Defines the canonical separation of concerns for multi-agent orchestration, preventing conceptual collapse between Fleet, Workflow, Lane, and Runtime.
    *   *Community:* Critical tracking issue by maintainer Hmbown; serves as the parent for multiple sub-epics.

3.  **[BUG: TUI Rendering Glitch — Missing/Extra Spaces](https://github.com/Hmbown/CodeWhale/issues/4479)**
    *   *Why it matters:* Affects core UX stability on Windows Terminal, causing text corruption that recovers only on mouse selection.
    *   *Community:* Reported by SparkofSpike; highlights cross-platform terminal rendering challenges.

4.  **[v0.9.2 Phase 3: Workflow Gates and Handoffs](https://github.com/Hmbown/CodeWhale/issues/4179)**
    *   *Why it matters:* Implements explicit role-to-role handoffs (scout → implementer → reviewer) with block/approve semantics, crucial for reliable multi-step workflows.
    *   *Community:* Part of the dogfood initiative to test the new orchestration model.

5.  **[deepseek doctor passes but deepseek run fails](https://github.com/Hmbown/CodeWhale/issues/689)**
    *   *Why it matters:* Diagnostic tool mismatch indicates configuration or runtime environment issues for users on older versions (v0.8.10).
    *   *Community:* User grey219114-cyber reports inability to start conversations despite passing checks.

6.  **[feat(commands): /dryrun — Preview Next Chat Completion](https://github.com/Hmbown/CodeWhale/issues/1004)**
    *   *Why it matters:* Allows developers to inspect the exact payload (system prompts, cached files, tools) before sending, reducing cost and latency surprises for V4 Pro users.
    *   *Community:* High value for debugging long context windows.

7.  **[v0.9.2 EPIC: TUI Information Architecture and Visual UX Overhaul](https://github.com/Hmbown/CodeWhale/issues/3480)**
    *   *Why it matters:* Addresses clutter in multi-agent workspaces, aiming to clarify sub-agent overlays, status lines, and task sidebars.
    *   *Community:* Driven by feedback from v0.8.65 dogfood runs showing raw state overload.

8.  **[v0.9.2 EPIC: Hotbar Command Surface and Source Adapters](https://github.com/Hmbown/CodeWhale/issues/3389)**
    *   *Why it matters:* Plans to make the Hotbar an opt-in feature for fresh installs to reduce initial complexity while retaining power-user capabilities.
    *   *Community:* Balances usability for new users with extensibility for advanced workflows.

9.  **[Refactor: Split RuntimeThreadManager](https://github.com/Hmbown/CodeWhale/issues/3313)**
    *   *Why it matters:* Breaks down a 7,000+ line module into store, executor, events, and types to improve code reviewability and reliability.
    *   *Community:* Essential cleanup for Rust-based TUI maintenance.

10. **[BUG(tui): Right-click Context Menu Highlights Wrong Item](https://github.com/Hmbown/CodeWhale/issues/4803)**
    *   *Why it matters:* A one-row offset bug in the context menu breaks precise interaction, reported by SparkofSpike.
    *   *Community:* Recent report (July 25); quick win for UX polish.

## 4. Key PR Progress
1.  **[fix(v0.9.2): Land the Audit Bug Cluster](https://github.com/Hmbown/CodeWhale/pull/4804)**
    *   *Summary:* Lands 11 of 16 audit-derived bugs across execpolicy, MCP, state, and workflow subsystems, each with dedicated tests.

2.  **[ci(release): Replace Recovery Input with Standalone Workflow](https://github.com/Hmbown/CodeWhale/pull/4802)**
    *   *Summary:* Fixes a failed attempt to recover container/Homebrew releases by replacing unusable `workflow_dispatch` inputs with a dedicated workflow.

3.  **[fix(web): Advance Published Release Fact to v0.9.1](https://github.com/Hmbown/CodeWhale/pull/4799)**
    *   *Summary:* Updates `latest-published-release.json` to reflect v0.9.1, ensuring install commands and website metadata are accurate.

4.  **[chore(workflows): Delete v0.8.68 Lane Scripts](https://github.com/Hmbown/CodeWhale/pull/4793)**
    *   *Summary:* Removes obsolete first-generation workflow scripts pinned to closed v0.8.68 issues, cleaning up CI noise.

5.  **[ci: Require Every PR to Close an Issue](https://github.com/Hmbown/CodeWhale/pull/4798)**
    *   *Summary:* Enforces traceability by mandating that every PR either closes an issue or provides a justification for doing so.

6.  **[ci(web): Auto-deploy codewhale.net on Push to Main](https://github.com/Hmbown/CodeWhale/pull/4776)**
    *   *Summary:* Switches web deployment from manual `workflow_dispatch` to automatic on push, preventing site drift.

7.  **[docs(agents): Adopt "Intent is the Artifact" Stance](https://github.com/Hmbown/CodeWhale/pull/4768)**
    *   *Summary:* Updates AGENTS.md and CLAUDE.md to guide agents to generate code against current `main` rather than recovering old branches.

8.  **[ci(triage): Stop Over-labelling Well-specified Issues](https://github.com/Hmbown/CodeWhale/pull/4792)**
    *   *Summary:* Adjusts auto-labelling rules to prevent misclassification of issues that already have clear acceptance criteria.

9.  **[fix(goal): Continue Durable Goals Across Turns](https://github.com/Hmbown/CodeWhale/pull/4611)**
    *   *Summary:* Ensures active goals persist across live-session turns, handling pausing, clearing, and budget exhaustion correctly.

10. **[fix(tui): Align Permission Postures and Compact Approvals](https://github.com/Hmbown/CodeWhale/pull/4608)**
    *   *Summary:* Improves permission handling by preserving Full Access across handoffs and allowing user questions in specific modes while automating others.

## 5. Feature Request Trends
*   **Localization Expansion:** Significant push for v0.9.2 to include Hindi (Devanagari), Ukrainian, and Russian, addressing gaps in the TUI locale matrix.
*   **UX Clarity & IA:** Requests to overhaul the TUI information architecture to better display multi-agent states and simplify the hotbar for new users.
*   **Debugging Tools:** Demand for `/dryrun` to preview payloads and better modality routing (vision/audio) in the model catalog.
*   **Code Maintainability:** Continuous requests to split large monolithic Rust modules (RuntimeThreadManager, mcp.rs, history.rs) to aid review and testing.

## 6. Developer Pain Points
*   **Monolithic Codebases:** Recurring frustration with massive files (`main.rs` at ~14k lines, `runtime_threads.rs` at ~7k lines) hindering code reviews and onboarding.
*   **Performance Bottlenecks:** Identified O(N²) re-parsing in streaming thinking cells and filesystem re-walking on every keystroke for `@`-mentions.
*   **Release Pipeline Gaps:** Previous issues with container images and Homebrew taps not updating alongside GitHub Releases, requiring manual recovery fixes.
*   **Terminal Rendering Inconsistencies:** Cross-platform glitches, particularly on Windows Terminal, affecting text integrity and UI responsiveness.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*