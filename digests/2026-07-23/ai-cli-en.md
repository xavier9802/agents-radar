# AI CLI Tools Community Digest 2026-07-23

> Generated: 2026-07-23 01:23 UTC | Tools covered: 10

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

# AI CLI Tools Ecosystem Report: 2026-07-23

## 1. Ecosystem Overview
The AI CLI landscape is transitioning from experimental alpha phases to enterprise-grade stability, with a heavy emphasis on resolving foundational infrastructure bugs like memory leaks and permission bypasses. Major players are aggressively refining multi-agent orchestration, focusing on granular cost control, context efficiency, and cross-platform reliability. While feature parity in basic coding tasks is assumed, the current competitive differentiator is robustness in complex workflows, specifically regarding session multiplexing, plugin security, and precise resource management.

## 2. Activity Comparison

| Tool | Issues (Hot/Total) | PRs (Key Progress) | Release Status |
| :--- | :--- | :--- | :--- |
| **Claude Code** | 10 Hot Issues | 10 Key PRs | **v2.1.218** Released |
| **OpenAI Codex** | 10 Hot Issues | 10 Key PRs | **Rust SDK v0.146.0-alpha** Series |
| **Gemini CLI** | 10 Hot Issues | 10 Key PRs | **v0.53.0-preview.0** & Nightly |
| **GitHub Copilot** | 10 Hot Issues | 1 Key PR (Admin) | **v1.0.74-3** Patch |
| **Kimi Code** | 5 Hot Issues | 3 Key PRs | No New Release |
| **OpenCode** | 10 Hot Issues | 10 Key PRs | No New Release |
| **Pi** | 10 Hot Issues | 10 Key PRs | No New Release |
| **Qwen Code** | 10 Hot Issues | 10 Key PRs | **v0.0.0-benchmark-poc** (POC) |
| **DeepSeek TUI** | 10 Hot Issues | 9 Key PRs | No New Release (Stabilizing v0.9.1) |
| **Grok Build** | N/A | N/A | No Activity |

## 3. Shared Feature Directions
*   **Context & Token Efficiency:** A universal demand for "context diets" and better auto-compaction.
    *   *Tools:* DeepSeek (explicit "context diet" initiative), Claude Code (auto-compact fixes), OpenAI Codex (compaction time tracking), GitHub Copilot (auto-compaction limits).
*   **Multi-Agent Orchestration & Cost Control:** Granular visibility into sub-agent usage and credit consumption.
    *   *Tools:* GitHub Copilot (per-subagent credit breakdown), Kimi Code (per-agent model selection), OpenCode (per-agent depth overrides), Claude Code (background subagents for code review).
*   **Platform-Specific Stability:** Intense focus on fixing OS-specific regressions, particularly Windows path handling and macOS tool dispatch.
    *   *Tools:* Claude Code (macOS filesystem dispatch), OpenAI Codex (Windows WSL/launch freezes), Kimi Code (Windows Unicode/GBK crashes), GitHub Copilot (Windows render loops/tmux issues).
*   **Security & Permission Management:** Resolving broken permission bypass modes and enforcing workspace trust.
    *   *Tools:* Claude Code (bypass permissions broken), Gemini CLI (A2A RCE prevention), OpenCode (permission mapping bugs).

## 4. Differentiation Analysis
*   **Claude Code:** Focuses on **workflow integration** within the Anthropic ecosystem, introducing background subagents and accessibility features. It leads in addressing deep-seated permission and macOS-specific architectural bugs.
*   **OpenAI Codex:** Emphasizes **infrastructure stability** and Rust SDK iteration. It is heavily focused on resource leak mitigation (MCP zombie processes) and enterprise-grade configuration granularity (worktrees, timeouts).
*   **Gemini CLI:** Prioritizes **protocol correctness** and agent autonomy. Recent updates address A2A protocol errors and enforce strict workspace trust, highlighting a focus on secure, autonomous agent execution.
*   **GitHub Copilot:** Centers on **session management** and IDE integration. Key differentiators include session multiplexing fixes and specific terminal emulator compatibility (tmux), though it lags in rapid feature PRs compared to competitors.
*   **OpenCode:** Distinguishes itself with **V2 architecture refinement**, tackling severe memory/CPU leaks in its server-side components and improving dynamic model loading for diverse providers.
*   **Qwen Code:** Leverages **enterprise ChatOps** integration (DingTalk/WeCom) and advanced daemon channel contracts, targeting a more corporate, workflow-centric user base.
*   **DeepSeek TUI:** Focuses on **UX polish and token optimization** ("context diet") and unified skill management, appealing to users prioritizing interface clarity and cost efficiency.
*   **Pi:** Specializes in **provider flexibility** and extension APIs, adding support for niche providers (StepFun, Bedrock Mantle) and improving constrained sampling for strict tool usage.

## 5. Community Momentum & Maturity
*   **High Momentum/Iterative:** **Claude Code** and **OpenAI Codex** show high engagement with frequent releases and active PR merges, indicating mature, rapidly evolving ecosystems. **Gemini CLI** also shows strong momentum with nightly builds and preview releases.
*   **Stabilization Phase:** **DeepSeek TUI** and **OpenCode** are in critical stabilization phases, addressing high-severity bugs (PATH corruption, memory leaks) before major version jumps.
*   **Niche/Emerging:** **Kimi Code** and **Pi** have smaller but highly engaged communities focused on specific provider compatibilities and extension architectures. **Qwen Code** shows steady progress driven by enterprise integration needs.
*   **Low Activity:** **Grok Build** reported no activity, suggesting a less active community or lower development velocity at this time.

## 6. Trend Signals
*   **Shift from "Can it code?" to "Can it scale?":** The industry is moving beyond basic coding capabilities to solving scalability issues: memory leaks, context window management, and multi-agent coordination overhead.
*   **Cost Transparency as a Feature:** Users increasingly demand granular billing and credit tracking per sub-agent or task, indicating that cost predictability is becoming a primary purchasing factor for teams.
*   **Security Hardening:** With the rise of autonomous agents, tools are prioritizing workspace trust, permission bypass fixes, and preventing Remote Code Execution (RCE) in MCP/A2A servers.
*   **Cross-Platform Friction Points:** Windows and macOS remain significant sources of instability, particularly regarding file system access, environment variables, and terminal emulator compatibility. Developers should expect these areas to be the focus of the next quarter's patch cycles.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Date:** 2026-07-23
**Source:** `anthropics/skills` Repository Analysis

## 1. Top Skills Ranking
*Ranked by community engagement (comments/issues linked) and technical impact.*

1.  **Self-Audit & Reasoning Quality Gate** ([PR #1367](https://github.com/anthropics/skills/pull/1367))
    *   **Functionality:** A meta-skill that performs mechanical file verification followed by a four-dimension reasoning audit before AI output delivery. Universal across tech stacks.
    *   **Status:** Open. High discussion volume due to its role in ensuring reliability for long-running agents.
2.  **SAP-RPT-1-OSS Predictor** ([PR #181](https://github.com/anthropics/skills/pull/181))
    *   **Functionality:** Integrates SAP’s open-source tabular foundation model for predictive analytics on business data within Claude workflows.
    *   **Status:** Open. Represents significant enterprise/data science demand.
3.  **Frontend-Design Clarity & Actionability** ([PR #210](https://github.com/anthropics/skills/pull/210))
    *   **Functionality:** Refines the core frontend-design skill to ensure instructions are strictly actionable by Claude in single conversations, reducing hallucination in UI code generation.
    *   **Status:** Open. Critical for improving basic developer experience.
4.  **Skill Creator Evaluation Fix** ([PR #1298](https://github.com/anthropics/skills/pull/1298))
    *   **Functionality:** Fixes a critical bug where `run_eval.py` reported 0% recall, breaking the description optimization loop for all new skills.
    *   **Status:** Open. Although a fix, it generates high discussion because it unblocks the entire contribution pipeline.
5.  **ODT Skill (OpenDocument)** ([PR #486](https://github.com/anthropics/skills/pull/486))
    *   **Functionality:** Adds support for creating, filling, and parsing ODT/ODS files, expanding beyond Microsoft Office formats.
    *   **Status:** Open. Fills a gap for open-source document standards.
6.  **Color Expert** ([PR #1302](https://github.com/anthropics/skills/pull/1302))
    *   **Functionality:** Provides deep color knowledge (ISCC-NBS, Munsell, OKLCH spaces) for design tasks.
    *   **Status:** Open. Niche but highly requested for professional design workflows.

## 2. Community Demand Trends
*Derived from Issue analysis.*

*   **Trust & Security Governance:** The most vocal concern is security. Issue [#492](https://github.com/anthropics/skills/issues/492) highlights fears of namespace impersonation (`anthropic/` prefix abuse), indicating a strong demand for verified, secure skill distribution channels.
*   **Enterprise Collaboration:** Issue [#228](https://github.com/anthropics/skills/issues/228) shows a clear need for org-wide skill sharing, moving away from manual `.skill` file distribution toward integrated libraries.
*   **Robust Testing Infrastructure:** There is sustained interest in testing-related skills, specifically Issue [#189](https://github.com/anthropics/skills/issues/189) regarding duplicate plugins and PR [#723](https://github.com/anthropics/skills/pull/723) for comprehensive testing patterns. Users want standardized, non-redundant testing guidance.
*   **Context Window Optimization:** Issues like [#1329](https://github.com/anthropics/skills/issues/1329) (compact-memory) and [#1175](https://github.com/anthropics/skills/issues/1175) (SharePoint context limits) indicate users are pushing skills to handle large-scale state management and secure external data integration efficiently.

## 3. High-Potential Pending Skills
*Active PRs with unresolved discussions or critical fixes that may land soon.*

*   **Skill Creator Windows Compatibility Suite** ([PR #1099](https://github.com/anthropics/skills/pull/1099), [PR #1050](https://github.com/anthropics/skills/pull/1050), [PR #1323](https://github.com/anthropics/skills/pull/1323)): A cluster of fixes addressing `run_eval.py` crashes and trigger detection failures on Windows. These are prerequisites for broader adoption and are likely to be merged as a batch.
*   **YAML Validation & Safety** ([PR #539](https://github.com/anthropics/skills/pull/539), [PR #361](https://github.com/anthropics/skills/pull/361)): Fixes for unquoted special characters in skill descriptions that cause silent parsing errors. These improve the stability of the skill creation process.
*   **Document Integrity Fixes** ([PR #541](https://github.com/anthropics/skills/pull/541)): Fixes DOCX tracked-change ID collisions. Essential for reliable document generation skills.

## 4. Skills Ecosystem Insight
The community's most concentrated demand is for **reliable, secure, and enterprise-ready automation tools**, shifting focus from simple code generation to robust governance, cross-platform compatibility (especially Windows), and trusted distribution mechanisms.

---

# Claude Code Community Digest: 2026-07-23

## 1. Today's Highlights
The latest release (v2.1.218) introduces significant architectural changes to `/code-review`, moving it to a background subagent to reduce conversation clutter, alongside new accessibility features for screen readers. Meanwhile, the community is heavily focused on resolving critical permission bypass failures and persistent macOS filesystem tool dispatch bugs that have impacted workflow stability since mid-2025.

## 2. Releases
**v2.1.218**
*   **Background Subagent for Code Review:** The `/code-review` command now executes as a background subagent. This prevents review iterations from filling the main conversation thread and allows stacked slash commands to target the review process specifically.
*   **Accessibility Improvements:** Added screen-reader announcements for deleted text during word (`Option+Delete`, `Ctrl+W`) and line (`Cmd+Backspace`) deletions.

## 3. Hot Issues
1.  **[BUG] macOS Filesystem Extension Dispatch Failure** ([#80002](https://github.com/anthropics/claude-code/issues/80002))
    *   *Why it matters:* A critical bug where macOS Claude Desktop fails to dispatch `tools/call` to the first-party Filesystem extension, despite `tools/list` succeeding.
    *   *Community Reaction:* High engagement (56 comments, 25 👍); users report complete loss of file manipulation capabilities.
2.  **[META] Bypass Permissions Mode Broken** ([#39523](https://github.com/anthropics/claude-code/issues/39523))
    *   *Why it matters:* Documents a 9-month unresolved issue where `bypassPermissions` mode fails to bypass safety checks, affecting workflow automation.
    *   *Community Reaction:* Frustration over lack of resolution despite numerous duplicates; 33 comments, 18 👍.
3.  **[BUG] Chat JSONL Deletion Despite Cleanup Settings** ([#62272](https://github.com/anthropics/claude-code/issues/62272))
    *   *Why it matters:* Users report chat history being deleted even with high `cleanupPeriodDays` settings, triggering on updates/restarts.
    *   *Community Reaction:* Community-created recovery scripts are gaining traction; 19 comments, 3 👍.
4.  **[BUG] GitHub Connector Silent Failure on Windows Cowork** ([#61682](https://github.com/anthropics/claude-code/issues/61682))
    *   *Why it matters:* The GitHub connector shows "Connected" but exposes no tools in the Cowork environment on Windows 11.
    *   *Community Reaction:* 17 comments, 19 👍; indicates a platform-specific regression in integration stability.
5.  **[BUG] macOS MCP Filesystem Tool Calls Silently Dropped** ([#79992](https://github.com/anthropics/claude-code/issues/79992))
    *   *Why it matters:* Similar to #80002 but specific to MCP servers; approval gates pass, but local servers never receive the call.
    *   *Community Reaction:* 16 comments; suggests a deeper renderer-to-server communication issue on macOS.
6.  **[FEATURE] Inject Queued Messages Mid-Task in Desktop** ([#71726](https://github.com/anthropics/claude-code/issues/71726))
    *   *Why it matters:* Parity request: CLI allows steering the agent between tool calls, but the Desktop app ignores inputs until the current turn finishes.
    *   *Community Reaction:* Strong demand for real-time control; 9 comments, 16 👍.
7.  **[BUG] Remote Control Session URL Error** ([#78933](https://github.com/anthropics/claude-code/issues/78933))
    *   *Why it matters:* `Cannot read properties of undefined (reading 'session_url')` prevents Remote Control from connecting/disconnecting.
    *   *Community Reaction:* 8 comments; blocks remote debugging workflows.
8.  **[BUG] Focus Mode Hides Substantive Assistant Messages** ([#50894](https://github.com/anthropics/claude-code/issues/50894))
    *   *Why it matters:* Focus mode intended to hide verbose logs also hides direct answers to user queries.
    *   *Community Reaction:* 5 comments, 4 👍; highlights UI/UX logic flaws in message filtering.
9.  **[BUG] Fable Model Self-Scoped Verification Failure** ([#80348](https://github.com/anthropics/claude-code/issues/80348))
    *   *Why it matters:* Model `claude-fable-5` incorrectly claims changes were verified when they were not, contradicting user feedback.
    *   *Community Reaction:* 3 comments; raises concerns about model reliability in verification tasks.
10. **[BUG] Structured Task Tools Unavailable in CLI** ([#80213](https://github.com/anthropics/claude-code/issues/80213))
    *   *Why it matters:* `TaskCreate`/`TodoWrite` tools missing in top-level CLI sessions despite flags being set, unlike Desktop sessions.
    *   *Community Reaction:* 2 comments, 1 👍; inconsistency between CLI and Desktop feature sets.

## 4. Key PR Progress
1.  **[feat] Inline Plan Mode Prompts** ([PR #18217](https://github.com/anthropics/claude-code/pull/18217))
    *   Adds `/planwith` command to allow inline planning arguments, removing the need for a two-step toggle-and-type workflow.
2.  **[docs] GCP Gateway Checksum Validation** ([PR #80353](https://github.com/anthropics/claude-code/pull/80353))
    *   Stops deployment sequences immediately upon binary checksum mismatch, improving security and debugging for cloud gateways.
3.  **[feat] Account Profiles Plugin** ([PR #80326](https://github.com/anthropics/claude-code/pull/80326))
    *   Experimental plugin for managing isolated `CLAUDE_CONFIG_DIR` environments, enabling separation of personal, work, and client accounts.
4.  **[fix] Console Scrolling History Bug** ([PR #80241](https://github.com/anthropics/claude-code/pull/80241])
    *   Resolves an issue where the console scrolls to the top of history when Claude adds text, improving readability during long outputs.
5.  **[fix] Auto-Compact Trigger Failure** ([PR #80196](https://github.com/anthropics/claude-code/pull/80196])
    *   Fixes a bug where auto-compaction does not trigger despite status lines reporting 100% context usage.
6.  **[fix] Max Subscription Usage Limit Bug** ([PR #80195](https://github.com/anthropics/claude-code/pull/80195])
    *   Addresses an issue where Max subscribers instantly hit usage limits due to incorrect counter logic.
7.  **[fix] DevContainer Firewall DNS Resilience** ([PR #80112](https://github.com/anthropics/claude-code/pull/80112])
    *   Hardens firewall initialization to tolerate transient DNS resolution failures without aborting the entire setup.
8.  **[feat] Twilight Plugin for Spec-First Design** ([PR #80008](https://github.com/anthropics/claude-code/pull/80008])
    *   Demonstrates a strategy for durable focus stacks in design/implement skills, though noted as requiring significant modification for acceptance.
9.  **[docs] Fix Broken Links via Archive.org** ([PR #80294](https://github.com/anthropics/claude-code/pull/80294])
    *   Updates broken outbound documentation links using Wayback Machine snapshots.
10. **[docs] Fix Broken Links via Archive.org** ([PR #80229](https://github.com/anthropics/claude-code/pull/80229])
    *   Additional maintenance for documentation link integrity.

## 5. Feature Request Trends
*   **Model-Specific Plan Modes:** Users are requesting `fableplan` mode, analogous to existing `opusplan`, to optimize token usage for lower-tier models during planning tasks.
*   **Real-Time Agent Steering:** There is a strong push for parity between CLI and Desktop apps regarding mid-task message injection, allowing users to steer the agent between tool calls in the GUI.
*   **Account Isolation:** The introduction of the `account-profiles` plugin suggests a growing need for multi-account management within a single machine environment.

## 6. Developer Pain Points
*   **Permission & Security Regressions:** The "Bypass Permissions" mode has been broken for nearly a year, and multiple reports indicate that permission checks are either failing silently or incorrectly denying legitimate actions.
*   **macOS-Specific Tool Dispatch Failures:** A cluster of high-priority bugs (#80002, #79992) points to systemic issues with how macOS handles MCP and native tool calls, particularly involving filesystem access and approval gates.
*   **Documentation Gaps:** A surge in documentation issues (#80385–#80398) reveals that recent feature updates (background code review, fast mode toggles, subagent hooks) are not adequately reflected in official docs, leading to user confusion.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest
**Date:** 2026-07-23

## 1. Today's Highlights
The Codex team is actively addressing critical stability and resource management issues, including significant memory leaks in the GUI’s MCP handling and Windows-specific performance freezes. Concurrently, rapid alpha releases (v0.146.0-alpha.1 through .4) indicate a push for stabilization ahead of a potential stable release, while backend improvements focus on plugin metadata caching and analytics fidelity.

## 2. Releases
**Rust SDK Alpha Series: v0.146.0-alpha.1 to .4**
A cluster of four alpha releases was published within the last 24 hours. While specific changelogs are not detailed in the public data, the rapid iteration suggests ongoing refinements to the Rust bindings, likely addressing breaking changes or stability fixes introduced in previous alphas.

*   [rust-v0.146.0-alpha.4](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.4)
*   [rust-v0.146.0-alpha.3](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.3)
*   [rust-v0.146.0-alpha.2](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.2)
*   [rust-v0.146.0-alpha.1](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.1)

## 3. Hot Issues
These issues have garnered the most community attention (comments/likes) and represent critical blockers or high-value feature requests.

1.  **Disable Auto-Resolve Timeout (#28969)**
    *   **Why it matters:** Users working with complex CLI workflows need more than 60 seconds for manual resolution of model questions. This is a high-friction pain point for power users.
    *   **Reaction:** 151 👍, 53 comments.
    *   [View Issue](https://github.com/openai/codex/issues/28969)

2.  **MCP Zombie Processes & Memory Leak in GUI (#12491)**
    *   **Why it matters:** A severe regression causing 1300+ zombie processes and 37GB memory leaks in Codex.app when using MCP tools. This threatens system stability for heavy users.
    *   **Reaction:** 5 👍, 27 comments.
    *   [View Issue](https://github.com/openai/codex/issues/12491)

3.  **Hooks Stopped Working After Desktop Update (#21639)**
    *   **Why it matters:** A regression breaking automation workflows that rely on hooks. Critical for users integrating custom CI/CD or linting steps.
    *   **Reaction:** 6 👍, 23 comments.
    *   [View Issue](https://github.com/openai/codex/issues/21639)

4.  **Windows WSL Agent Mode Path Error (#16815)**
    *   **Why it matters:** Blocks Windows developers from using Agent mode via WSL due to `AbsolutePathBuf` deserialization errors.
    *   **Reaction:** 13 👍, 22 comments.
    *   [View Issue](https://github.com/openai/codex/issues/16815)

5.  **Configure Worktree Location (#10599)**
    *   **Why it matters:** Users want control over where Git worktrees are created, rather than being forced into default directories. Essential for large monorepo structures.
    *   **Reaction:** 66 👍, 16 comments.
    *   [View Issue](https://github.com/openai/codex/issues/10599)

6.  **VS Code Remote-SSH Extension Failure (#27597)**
    *   **Why it matters:** The IDE extension fails to load in remote SSH environments, forcing users to rely solely on CLI and losing UI benefits.
    *   **Reaction:** 4 👍, 16 comments.
    *   [View Issue](https://github.com/openai/codex/issues/27597)

7.  **Headless Remote Linux Support for Mobile (#23200)**
    *   **Why it matters:** Enables mobile usage as a true controller for always-on servers without requiring a persistent local desktop connection.
    *   **Reaction:** 42 👍, 13 comments.
    *   [View Issue](https://github.com/openai/codex/issues/23200)

8.  **Timeout Waiting for User Input (#27458)**
    *   **Why it matters:** Misconfigured or perceived timeouts during user input phases disrupt long-running agent sessions.
    *   **Reaction:** 43 👍, 12 comments.
    *   [View Issue](https://github.com/openai/codex/issues/27458)

9.  **Missing Recent Project Threads in Sidebar (#30385)**
    *   **Why it matters:** Data visibility issue where existing sessions are lost from the UI despite being present on disk, causing workflow disruption.
    *   **Reaction:** 0 👍, 9 comments.
    *   [View Issue](https://github.com/openai/codex/issues/30385)

10. **Disappearing Five-Hour Usage Limit (#32791)**
    *   **Why it matters:** Account configuration inconsistency where the expected five-hour limit for Plus accounts is missing, replaced only by a weekly limit.
    *   **Reaction:** 3 👍, 8 comments.
    *   [View Issue](https://github.com/openai/codex/issues/32791)

## 4. Key PR Progress
Recent merges highlight improvements in plugin management, analytics, and multi-agent coordination.

1.  **Wake Sleeping Threads for Queued Mail (#34852)**
    *   Ensures idle threads resume processing when agent work arrives, preventing delays in queued tasks.
    *   [View PR](https://github.com/openai/codex/pull/34852)

2.  **Batch Metadata for Plugin Apps (#34851)**
    *   Optimizes plugin loading by batching API requests for app metadata, improving startup performance and reliability.
    *   [View PR](https://github.com/openai/codex/pull/34851)

3.  **Disable Image Generation for Free Plans (#34850)**
    *   Enforces subscription boundaries by removing the image generation tool for Free-tier accounts at the registration level.
    *   [View PR](https://github.com/openai/codex/pull/34850)

4.  **Cache Remote Plugin Catalogs (#34849)**
    *   Introduces disk caching for plugin catalogs with a 3-hour TTL, reducing network calls and speeding up plugin listing.
    *   [View PR](https://github.com/openai/codex/pull/34849)

5.  **Guardian Model Limits for Reviews (#34847)**
    *   Fixes context window mismatches during Guardian reviews by ensuring the correct model limits are applied based on the effective Guardian model.
    *   [View PR](https://github.com/openai/codex/pull/34847)

6.  **Custom Provider Web Search Opt-In (#34846)**
    *   Allows custom Responses providers to enable standalone web search, expanding flexibility for enterprise/custom model integrations.
    *   [View PR](https://github.com/openai/codex/pull/34846)

7.  **Track Multi-Agent Mode in World State (#34845)**
    *   Persists multi-agent instructions across history changes, ensuring consistent behavior in complex multi-agent setups.
    *   [View PR](https://github.com/openai/codex/pull/34845)

8.  **Persisted Thread Pinning (#34840)**
    *   Adds server-side support for pinning threads, allowing users to keep important sessions easily accessible in the UI.
    *   [View PR](https://github.com/openai/codex/pull/34840)

9.  **Preserve User Input on MCP Interruption (#34839)**
    *   Fixes a bug where user input was lost if an MCP tool startup was interrupted mid-turn, ensuring conversation history integrity.
    *   [View PR](https://github.com/openai/codex/pull/34839)

10. **Track Compaction Time in Profiles (#34835)**
    *   Improves observability by measuring compaction duration separately in turn profiles, aiding in performance debugging.
    *   [View PR](https://github.com/openai/codex/pull/34835)

## 5. Feature Request Trends
*   **Configuration Granularity:** Strong demand for configurable timeouts (auto-resolve), worktree locations, and visibility preferences (taskbar/tray).
*   **Remote/Mobile Flexibility:** Requests for headless remote support on mobile and better integration with VS Code Remote-SSH indicate a desire for more decentralized development workflows.
*   **UI/UX Persistence:** Features like thread pinning and side-chat persistence show users want the interface to retain context across sessions and updates.
*   **Multi-Language Support:** A closed issue (#34710) highlights interest in TUI localization (Chinese, Japanese, etc.), suggesting global market expansion considerations.

## 6. Developer Pain Points
*   **Windows Stability & Performance:** A disproportionate number of high-severity bugs relate to Windows, including cold launch freezes (#34025), WSL path resolution failures (#16815, #34782), and sandbox crashes (#22428, #34841).
*   **Resource Leaks:** The MCP zombie process leak (#12491) and file descriptor leaks (#26984) are critical infrastructure issues affecting long-running sessions.
*   **Regression in Automation:** Hooks (#21639) and plan mode restrictions (#32594) failing after updates erode trust in the tool's reliability for automated workflows.
*   **CLI/TUI Synchronization:** Issues with TUI rendering (blank screens #34724, truncated output #34037) and remote session sync (#34632) hinder the developer experience in terminal-heavy environments.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest: 2026-07-23

## 1. Today's Highlights
The Gemini CLI team addressed critical stability and security concerns in recent releases, specifically fixing A2A protocol errors that caused 400 Bad Requests and enforcing workspace trust to prevent Remote Code Execution (RCE) in the A2A server. Community attention is heavily focused on agent reliability, with significant discussion surrounding subagent hang states, generalist agent loops, and memory extraction edge cases.

## 2. Releases
*   **v0.53.0-preview.0**: Addresses API stability by grouping cancelled tool responses and coalescing consecutive roles to prevent `400 Bad Request` errors. Also introduces foundational modules for an LLM-based triage orchestrator.
    *   [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.52.0-nightly.20260721.gacae7124b...v0.53.0-preview.0)
*   **v0.52.0**: Refactors workspace context by excluding transient CI configuration files, improving context management efficiency.
    *   [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.52.0-nightly.20260721.gacae7124b...v0.52.0)
*   **v0.52.0-nightly.20260722.gc776c665b**: Security patch enforcing workspace trust and task isolation within the A2A server to mitigate RCE vulnerabilities.
    *   [Changelog](https://github.com/google-gemini/gemini-cli/commit/gc776c665b)

## 3. Hot Issues
1.  **[Bug] Subagent recovery after MAX_TURNS reported as GOAL success** (#22323)
    *   *Why it matters:* Critical logic flaw where subagents incorrectly signal completion despite hitting turn limits, leading to silent failures in codebase investigation.
    *   *Reaction:* High priority (P1), 12 comments.
2.  **[Bug] Generalist agent hangs indefinitely** (#21409)
    *   *Why it matters:* The core orchestration agent becomes unresponsive, requiring manual cancellation. Workaround involves disabling sub-agents.
    *   *Reaction:* P1, 8 comments, 8 👍.
3.  **[Feature] Robust component level evaluations** (#24353)
    *   *Why it matters:* Follow-up to behavioral evals; aims to standardize testing across supported Gemini models using 76+ existing tests.
    *   *Reaction:* P1, 7 comments.
4.  **[Investigation] AST-aware file reads and search** (#22745)
    *   *Why it matters:* Potential optimization to reduce token noise and improve precision in codebase mapping by understanding syntax trees.
    *   *Reaction:* P2, 7 comments.
5.  **[Bug] Gemini does not use skills/sub-agents autonomously** (#21968)
    *   *Why it matters:* Users report the model ignores custom skills (e.g., Gradle, Git) unless explicitly instructed, reducing automation value.
    *   *Reaction:* P2, 6 comments.
6.  **[Bug] Shell command execution stuck at "Waiting input"** (#25166)
    *   *Why it matters:* Simple CLI commands cause the agent to hang, blocking workflow progression even after command completion.
    *   *Reaction:* P1, 4 comments, 3 👍.
7.  **[Bug] Browser Agent fails on Wayland** (#21983)
    *   *Why it matters:* Linux users on Wayland compositors experience complete failure of the browser sub-agent.
    *   *Reaction:* P1, 4 comments.
8.  **[Bug] Auto Memory retries low-signal sessions** (#26522)
    *   *Why it matters:* Inefficient resource usage where the memory system repeatedly attempts to process irrelevant session data.
    *   *Reaction:* P2, 5 comments.
9.  **[Bug] Browser Agent ignores settings.json overrides** (#22267)
    *   *Why it matters:* Configuration changes (like `maxTurns`) are ignored, making it difficult to control browser agent behavior via config.
    *   *Reaction:* P2, 3 comments.
10. **[Bug] Model creates tmp scripts in random spots** (#23571)
    *   *Why it matters:* Poor hygiene in file creation leads to workspace clutter and cleanup overhead for users.
    *   *Reaction:* P2, 3 comments.

## 4. Key PR Progress
1.  **[Fix] Rotate session ID on model fallback** (#28469)
    *   Fixes blocking API errors when falling back to `gemini-2.5-flash` by rotating stateful session IDs.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28469)
2.  **[Fix] Filter thought parts from history** (#28509)
    *   Prevents internal monologue leakage into context when context management is disabled, ensuring cleaner history turns.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28509)
3.  **[Feat] Add gemini-3.5-flash to model selector** (#28485)
    *   Exposes the new model to all users, resolving issues where it was defined but not visible in the legacy build path.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28485)
4.  **[Fix] Propagate AbortSignal in /compress command** (#28506)
    *   Allows cancellation of background chat compression, preventing dangling network requests.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28506)
5.  **[Fix] Use native fetch for OAuth token exchange** (#28446)
    *   Resolves "Premature close" errors during login on headless VPS environments.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28446)
6.  **[Fix] Restrict tools.core wildcard DENY** (#28499)
    *   Corrects a policy bug where wildcard DENY rules were inadvertently excluding MCP tools.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28499)
7.  **[Docs] Windows PowerShell troubleshooting** (#28447)
    *   Adds specific guidance for PowerShell users experiencing `gemini` command failures post-install.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28447)
8.  **[Chore] Bump @opentelemetry/core** (#28024)
    *   Updates dependency from 2.7.1 to 2.8.0 for telemetry improvements.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28024)
9.  **[Feat] Eval coverage report command** (#28169)
    *   Introduces `eval:coverage` to cross-reference tool registry with eval inventory.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28169)
10. **[Infra] Cloud Run job for SSR Code Gen** (#28431)
    *   Sets up containerized runtime and workflows for the new SSR Code Generation Pipeline.
    *   [PR Link](https://github.com/google-gemini/gemini-cli/pull/28431)

## 5. Feature Request Trends
*   **AST-Aware Tooling:** Strong interest in using Abstract Syntax Tree parsing for more precise code navigation and reading, aiming to reduce token waste and improve accuracy (#22745, #22746).
*   **Enhanced Agent Autonomy & Self-Correction:** Requests for the agent to better utilize custom skills without explicit prompting and to discourage destructive behaviors like unnecessary `git reset --force` (#21968, #22672).
*   **Improved Transparency & Debugging:** Demand for better visibility into subagent trajectories during sharing (`/chat share`) and inclusion of subagent context in bug reports (#22598, #21763).
*   **Robustness & Recovery:** Features aimed at recovering from locked browser sessions and handling symlinked agent definitions correctly (#22232, #20079).

## 6. Developer Pain Points
*   **Agent State Management:** Recurring issues with agents hanging, looping, or failing to recover from terminal limits (MAX_TURNS) suggest instability in the orchestration layer (#21409, #22323, #25166).
*   **Configuration Ignored:** Users frequently report that `settings.json` overrides and custom skills are not respected by the agent, forcing manual intervention (#22267, #21968).
*   **Platform-Specific Instability:** Significant friction reported on Linux/Wayland environments for browser agents and headless VPS setups for authentication (#21983, #28446).
*   **Memory System Efficiency:** The Auto Memory feature is criticized for inefficiently retrying low-signal sessions and lacking deterministic redaction, raising privacy and performance concerns (#26522, #26525).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-07-23

## 1. Today's Highlights
GitHub Copilot CLI v1.0.74-3 was released with critical fixes for session multiplexing and new support for the Gemini 3.6 Flash model, alongside a first-run sandbox opt-in splash screen. The community is actively debating BYOK authentication regressions in ACP mode and persistent zombie process leaks on Linux, while reporting several Windows-specific crashes and rendering issues in terminal emulators like tmux.

## 2. Releases
*   **v1.0.74-3**: Latest patch release addressing stability issues.
    *   **Added**: First-run splash screen to opt into the default sandbox environment; support for `gemini-3.6-flash` model.
    *   **Improved**: Session multiplexing logic now prevents dialog leakage between sessions; eligible pickers correctly reopen when switching contexts.
    *   **Fixes**: Corrected behavior of the `$` interactive shell shortcut.
    *   [View Release](https://github.com/github/copilot-cli/releases/tag/v1.0.74-3)

## 3. Hot Issues
1.  **[area:tools] Built-in PDF Reading Support** (#443)
    *   *Why it matters*: Enables native analysis of academic papers and technical docs without external tools like `pdftotext`.
    *   *Reaction*: High community interest (33 👍).
    *   [Link](https://github.com/github/copilot-cli/issues/443)
2.  **[area:authentication] BYOK still rejected in --acp mode** (#4016)
    *   *Why it matters*: Regression where custom providers (`COPILOT_PROVIDER_*`) fail authentication in ACP/stdio mode, blocking non-interactive workflows.
    *   *Reaction*: 5 comments, 4 👍.
    *   [Link](https://github.com/github/copilot-cli/issues/4016)
3.  **[area:context-memory] Auto-compaction does not prevent CAPI 5 MB failure** (#4183)
    *   *Why it matters*: Long sessions hit the 5MB body limit despite token capacity being within bounds, causing permanent call failures.
    *   *Reaction*: 7 👍, highlighting frustration with context management limits.
    *   [Link](https://github.com/github/copilot-cli/issues/4183)
4.  **[area:agents] Show per-subagent AI credit usage breakdown** (#4207)
    *   *Why it matters*: Users need granular visibility into credit consumption across subagents for cost accounting.
    *   *Reaction*: 6 👍.
    *   [Link](https://github.com/github/copilot-cli/issues/4207)
5.  **[area:platform-linux] copilot CLI 1.0.71 does not reap child processes** (#4163)
    *   *Why it matters*: Zombie processes accumulate (~2/min), leading to resource leaks and potential instability on Linux.
    *   *Reaction*: 2 👍, technical concern for long-running agents.
    *   [Link](https://github.com/github/copilot-cli/issues/4163)
6.  **[area:theming-accessibility] Prompt box renders invisible inside tmux** (#4212)
    *   *Why it matters*: Usability blocker for users running Copilot in tmux, where text becomes unreadable (dark-on-dark).
    *   *Reaction*: 0 👍 but critical for terminal power users.
    *   [Link](https://github.com/github/copilot-cli/issues/4212)
7.  **[triage] Shell command completion never detected inside tmux** (#4223)
    *   *Why it matters*: Commands hang indefinitely as "still running" in tmux, breaking automation and interactive flows.
    *   *Reaction*: 0 👍.
    *   [Link](https://github.com/github/copilot-cli/issues/4223)
8.  **[area:enterprise] Environment footer stuck on "Loading:"** (#4206)
    *   *Why it matters*: Indicates MCP handshake stalls under org policies, leaving the UI unresponsive.
    *   *Reaction*: 2 👍.
    *   [Link](https://github.com/github/copilot-cli/issues/4206)
9.  **[area:input-keyboard] Emit OSC 133 shell-integration sequences** (#3428)
    *   *Why it matters*: Feature request to improve scrollback navigation by marking prompts and final answers.
    *   *Reaction*: 0 👍, low engagement but high utility for UX.
    *   [Link](https://github.com/github/copilot-cli/issues/3428)
10. **[triage] Regression of infinite React/Ink render loop** (#4222)
    *   *Why it matters*: Re-emergence of v1.0.31 freeze bug in recent versions on Windows VS Code integrated terminals.
    *   *Reaction*: 0 👍.
    *   [Link](https://github.com/github/copilot-cli/issues/4222)

## 4. Key PR Progress
*   **#3163: ViewSonic monitor**
    *   *Status*: Open
    *   *Summary*: Initiated GitHub action runners associated with monitor issues #2591, #3561, and #3559.
    *   *Note*: This PR appears to be administrative or related to internal monitoring infrastructure rather than core CLI functionality.
    *   [Link](https://github.com/github/copilot-cli/pull/3163)

*(Note: No other significant functional PRs were reported in the last 24 hours.)*

## 5. Feature Request Trends
*   **Granular Cost & Usage Accounting**: Multiple requests (#4207, #4224, #4218) focus on better visibility into credit usage, specifically per-subagent breakdowns, billing attributes in OTel spans, and configurable model pools for Auto mode.
*   **Enhanced Context Management**: Requests for configurable auto-compaction thresholds (#1688) and native PDF reading support (#443) indicate a need for more robust handling of large documents and context windows.
*   **Explicit Agent Orchestration**: Users are requesting explicit inline invocation of custom agents (#4208) and tool aliases for agent profiles (#4209) to improve workflow control.

## 6. Developer Pain Points
*   **Terminal Emulator Compatibility**: Significant friction reported with **tmux** (invisible UI, hanging commands) and **Windows** (crashes on exit, notification failures, infinite render loops). These are recurring high-frequency bugs affecting core usability.
*   **Session Stability**: Issues with **zombie processes** on Linux (#4163) and **session resumption hangs** on Windows (#4165) suggest underlying OS-level integration challenges.
*   **Authentication Regressions**: The re-emergence of BYOK authentication failures in ACP mode (#4016) disrupts automated and non-interactive workflows.
*   **Context Limits vs. Reality**: Users are hitting hard limits (5MB CAPI body) that bypass token-based compaction strategies (#4183), leading to silent failures in long sessions.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-23

## 1. Today's Highlights
The community is actively addressing critical API compatibility issues, with PR #2535 resolving a validation error regarding `prompt_cache_key` for third-party providers. Additionally, significant fixes are underway for shell process handling and file replacement logic to improve stability in complex workflows.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
*   **[Bug] MCP Tool Schema Rejection (Issue #2531)**: Users report HTTP 400 errors when using K3 via Moonshot API due to invalid JSON schema formatting in tool definitions. This highlights ongoing friction between client-side generation and provider strictness. [Link](https://github.com/MoonshotAI/kimi-cli/issues/2531)
*   **[Bug] Model API 400 Validation Error (Issue #2534)**: A regression introduced in recent updates causes crashes with Nvidia NIM models by passing unsupported parameters like `prompt_cache_key`. This affects users relying on third-party compatible endpoints. [Link](https://github.com/MoonshotAI/kimi-cli/issues/2534)
*   **[Bug] Windows Unicode Crash on Redirect (Issue #2532)**: `kimi web` crashes on Chinese-locale Windows systems when stdout is redirected, due to an inability to encode the `➜` banner character in GBK. This impacts automation scripts and CI/CD pipelines on localized Windows machines. [Link](https://github.com/MoonshotAI/kimi-cli/issues/2532)
*   **[Bug] TPD Rate Limit Calculation (Issue #2318)**: Users report incorrect Total Per Day (TPD) rate limit calculations, potentially leading to unexpected throttling. Although older, it remains relevant for high-volume users. [Link](https://github.com/MoonshotAI/kimi-cli/issues/2318)
*   **Feature Request: Per-Agent Model Selection (Issue #2533)**: Developers are requesting the ability to assign different models to sub-agents independently of the session default. This is crucial for cost-optimized multi-agent architectures. [Link](https://github.com/MoonshotAI/kimi-cli/issues/2533)

*(Note: Only 5 issues were found in the provided data; all are listed above as they are noteworthy.)*

## 4. Key PR Progress
*   **PR #2535: Fix LLM Prompt Cache Scoping**: Addresses Issue #2534 by ensuring `prompt_cache_key` is scoped only to official Moonshot APIs, preventing validation errors with third-party endpoints like Nvidia NIM. [Link](https://github.com/MoonshotAI/kimi-cli/pull/2535)
*   **PR #2524: Fix Tools StrReplaceFile Counting**: Resolves Issue #2526 by correcting how `StrReplaceFile` counts replacements. It now evaluates against running content rather than original file state, fixing failures in chained edits. [Link](https://github.com/MoonshotAI/kimi-cli/pull/2524)
*   **PR #2530: Fix Shell Detached Child Blocking**: Resolves Issue #2468 by preventing the foreground shell from hanging indefinitely when detached children hold open pipes. This improves reliability for background daemon commands. [Link](https://github.com/MoonshotAI/kimi-cli/pull/2530)

*(Note: Only 3 PRs were found in the provided data; all are listed above as they are key progress items.)*

## 5. Feature Request Trends
The primary trend is **granular control over resource allocation and model selection**. Users are increasingly adopting multi-agent workflows and seeking ways to optimize costs by assigning cheaper models to sub-tasks while reserving powerful models for complex reasoning. There is also a strong demand for better robustness in non-standard environments (e.g., localized Windows terminals).

## 6. Developer Pain Points
*   **Third-Party API Compatibility**: Significant friction exists when using Kimi-compatible endpoints that do not strictly adhere to Moonshot's internal parameter schemas (e.g., `prompt_cache_key`, JSON schema validation for MCP tools).
*   **Windows Localization & Encoding**: The CLI struggles with character encoding (GBK vs. UTF-8) on non-English Windows locales, particularly when output is captured or redirected.
*   **Shell Process Management**: Background processes and detached children cause the CLI shell to hang or block incorrectly, disrupting automated scripts.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest: 2026-07-23

## 1. Today's Highlights
The community is actively addressing critical V2 stability issues, particularly around location boot caching failures and UI responsiveness on large projects. Significant documentation updates have been merged to clarify web search backends (Exa vs. Parallel) and TUI theme generation, while core fixes for dynamic model loading and named agent colors improve developer experience.

## 2. Releases
No new official releases were published in the last 24 hours. However, verification videos for PR #38252 were released, indicating ongoing testing of recent changes.

## 3. Hot Issues
*   **[OPEN] Subscription Model Blocking (#38218)**: All models under `opencode-go` subscriptions are returning "Request blocked by upstream provider." High engagement (22 comments, 5 👍) suggests a widespread service disruption affecting paid users. [Link](https://github.com/anomalyco/opencode/issues/38218)
*   **[OPEN] V2 Server Memory/CPU Leak (#36677)**: A long-lived V2 server enters a persistent JS allocation loop, consuming 1+ CPU core and >1GB RSS while idle. This indicates a significant performance regression in the V2 architecture. [Link](https://github.com/anomalyco/opencode/issues/36677)
*   **[OPEN] Desktop UI Lag with Conversations (#38412)**: Users report abnormal lag in the desktop app dialog box after initiating conversations. [Link](https://github.com/anomalyco/opencode/issues/38412)
*   **[CLOSED] Database Query Failure (#17270)**: Resolved error regarding `CREATE TABLE account` failing during initialization, likely related to local storage or migration scripts. [Link](https://github.com/anomalyco/opencode/issues/17270)
*   **[CLOSED] Permission Mapping Bug (#16028)**: Fixed an issue where the `EDIT_TOOLS` constant used `'patch'` instead of `'apply_patch'`, breaking permission mappings for file editing tools. [Link](https://github.com/anomalyco/opencode/issues/16028)
*   **[CLOSED] Tool Execution Errors (#38399, #38400)**: Multiple reports of bash/read/glob tools failing with "no such column: 'data'" errors. These appear to be resolved, possibly linked to database schema or query formatting issues. [Link](https://github.com/anomalyco/opencode/issues/38399) | [Link](https://github.com/anomalyco/opencode/issues/38400)
*   **[OPEN] Web UI Sync & Session Creation Failures (#38411)**: The "+" button in the web UI fails to create new sessions, and sessions are not syncing across devices. [Link](https://github.com/anomalyco/opencode/issues/38411)
*   **[OPEN] LM Studio Model Discovery Incomplete (#18011)**: OpenCode only discovers 3/9 models from LM Studio despite full `/v1/models` availability, hindering local model integration. [Link](https://github.com/anomalyco/opencode/issues/18011)
*   **[OPEN] Plan/Build Mode Regression (#37970)**: Users report inconsistent behavior where the "Plan" mode sometimes skips planning and executes directly, breaking expected workflows. [Link](https://github.com/anomalyco/opencode/issues/37970)
*   **[CLOSED] Renderer Crash in VirtualTimelineRow (#33285)**: A `TypeError` reading 'size' on undefined caused renderer crashes, now closed. [Link](https://github.com/anomalyco/opencode/issues/33285)

## 4. Key PR Progress
*   **#38414 [fix(core): migrate named agent colors]**: Preserves named agent colors in V1 config and migrates legacy hex colors before V2 validation. Ensures visual consistency during upgrades. [Link](https://github.com/anomalyco/opencode/pull/38414)
*   **#38397 [refactor(tui): generate syntax from V2 theme]**: Generates full TUI `SyntaxStyle` from resolved V2 tokens, removing parallel V1 resolution logic while maintaining mini-TUI compatibility. [Link](https://github.com/anomalyco/opencode/pull/38397)
*   **#38401 [fix(core): load dynamic models for generation]**: Fixes stateless `/api/generate` requests to support dynamically loaded AI SDK or native providers (e.g., Gemini), resolving previous "Unsupported package" errors. [Link](https://github.com/anomalyco/opencode/pull/38401)
*   **#38395 [docs: mention Exa and Parallel as web search backends]**: Updates documentation to reflect that `websearch` supports both Exa and Parallel backends, correcting previous exclusive references to Exa. [Link](https://github.com/anomalyco/opencode/pull/38395)
*   **#38408 [fix: pr-standards falsely flags v2-based PRs]**: Corrects the CI workflow that incorrectly flagged V2 branch PRs as missing linked issues due to GitHub GraphQL API limitations. [Link](https://github.com/anomalyco/opencode/pull/38408)
*   **#38403 [fix(ui): standardize tooltip delay]**: Standardizes tooltip hover delay to 400ms and adds an `instant` mode for model-pickers, improving UI consistency. [Link](https://github.com/anomalyco/opencode/pull/38403)
*   **#38406 [fix(core): retry failed location boot]**: Addresses the issue where failed location boots were cached for 60 minutes; implements retry logic instead of serving stale errors. [Link](https://github.com/anomalyco/opencode/pull/38406)
*   **#38022 [docs(ecosystem): add opencode-hypa plugin]**: Adds the `opencode-hypa` plugin to the ecosystem documentation. [Link](https://github.com/anomalyco/opencode/pull/38022)
*   **#38033 [docs(readme): add Indonesian language version]**: Adds an Indonesian translation for the README to improve accessibility. [Link](https://github.com/anomalyco/opencode/pull/38033)
*   **#37226 [feat(core): per-agent subagent_depth override]**: Allows overriding global `subagent_depth` settings at the individual agent level via configuration files. [Link](https://github.com/anomalyco/opencode/pull/37226)

## 5. Feature Request Trends
*   **UI Navigation Enhancements**: Requests for collapsible sidebars, persistent project/chat history rails, and improved tab management (#38410).
*   **PowerShell Integration**: Users are requesting specific PowerShell arguments (`-WindowStyle Hidden`) to suppress terminal window flashes (#38402).
*   **Token Optimization**: Specific requests to reduce per-turn token accumulation for OpenAI models on Bedrock Mantle to lower costs (#38409).
*   **Local Model Discovery**: Continued demand for robust auto-discovery of local models (LM Studio, Ollama) with accurate representation of all available endpoints (#18011).

## 6. Developer Pain Points
*   **V2 Stability & Performance**: Persistent issues with memory leaks, CPU spikes in long-running V2 servers, and aggressive caching of transient boot failures (60-minute TTL) are causing significant friction.
*   **Subscription/Provider Reliability**: The widespread "Request blocked by upstream provider" error for `opencode-go` subscriptions indicates fragile upstream integration or configuration bugs.
*   **Large Project Handling**: Performance degradation (LLM failures, UI lag) when opening OpenCode in large directory structures suggests inefficient file scanning or context window management.
*   **Documentation Gaps**: Confusion over supported web search backends and incomplete model discovery lists highlights a need for more accurate and comprehensive documentation.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest: 2026-07-23

## 1. Today's Highlights
The Pi project saw significant activity in provider stability and TUI robustness, with key fixes addressing retry logic failures in OpenAI/Anthropic SDKs and session cleanup issues in subprocesses. Several new provider integrations (StepFun, Amazon Bedrock Mantle) were merged, while community discussions focused on improving model selection UX and extension API structures.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
*   **[Bug] Compaction using Copilot Enterprise not possible** [#6768](https://github.com/earendil-works/pi/issues/6768)
    *   **Why it matters:** Users with Enterprise licenses encounter `421 Misdirected Request` errors during context compaction, breaking workflow continuity.
    *   **Reaction:** High engagement (8 comments, 8 👍), indicating a widespread pain point for enterprise users.
*   **[Bug] /scoped-models cannot select model ids containing brackets** [#6210](https://github.com/earendil-works/pi/issues/6210)
    *   **Why it matters:** Custom models with bracketed IDs (e.g., `[1m]`) fail to match, limiting extensibility for niche model configurations.
    *   **Reaction:** Active development (`inprogress`), showing team responsiveness to edge-case parsing bugs.
*   **[Bug] OpenAI SDK retries sleep full Retry-After (days) and Escape cannot abort** [#6911](https://github.com/earendil-works/pi/issues/6911)
    *   **Why it matters:** A critical UX flaw where HTTP 429 retries ignore `AbortSignal`, causing indefinite hangs that users cannot interrupt.
    *   **Reaction:** Closed; fix is underway via PR #6980.
*   **[Bug] On windows dependent extensions mislabeled and show absolute path** [#6619](https://github.com/earendil-works/pi/issues/6619)
    *   **Why it matters:** Windows-specific installation paths leak into the UI banner, confusing users and cluttering the interface.
    *   **Reaction:** Closed; addressed by PR #6964 and #6680.
*   **[Bug] pi-tui crash log hardcodes ~/.pi/agent/pi-crash.log** [#6652](https://github.com/earendil-works/pi/issues/6652)
    *   **Why it matters:** Ignoring `PI_CODING_AGENT_DIR` causes logs to appear in the home directory even when configured elsewhere, violating user expectations for data locality.
    *   **Reaction:** Closed; fixed in PR #6958.
*   **[Bug] pi's integration with GitHub Copilot Plugin causes token invalidation** [#6970](https://github.com/earendil-works/pi/issues/6970)
    *   **Why it matters:** Auth conflicts between Pi’s native Copilot plugin integration and external tools (like Neovim) lead to frequent token invalidation.
    *   **Reaction:** Closed; requires investigation into OAuth vs. Plugin auth flows.
*   **[Feature] MRU model switching** [#6982](https://github.com/earendil-works/pi/issues/6982)
    *   **Why it matters:** Current model cycling is alphabetical, which is inefficient. Users request Most-Recently-Used (MRU) cycling for faster context switching.
    *   **Reaction:** Closed as a feature request; highlights demand for smarter navigation.
*   **[Question] Three @joyanhui/pi-ext-* packages not appearing on gallery** [#6991](https://github.com/earendil-works/pi/issues/6991)
    *   **Why it matters:** Publishing friction for extension authors; npm packages aren't automatically syncing to the pi.dev/gallery.
    *   **Reaction:** Closed; likely a metadata or indexing delay issue.
*   **[Bug] Concurrent extension dialogs hang (orphaned Promise)** [#6978](https://github.com/earendil-works/pi/issues/6978)
    *   **Why it matters:** In TUI mode, multiple simultaneous extension prompts cause the first to hang indefinitely, freezing the session.
    *   **Reaction:** Closed; points to concurrency handling bugs in the UI event loop.
*   **[Bug] OAuth-authenticated Anthropic requests get billed as metered API usage** [#6979](https://github.com/earendil-works/pi/issues/6979)
    *   **Why it matters:** Users with Pro/Max subscriptions see incorrect billing when using OAuth auth, potentially incurring extra costs.
    *   **Reaction:** Closed; indicates a bug in the provider cost-tracking logic for OAuth flows.

## 4. Key PR Progress
*   **[fix(ai): make provider retries abortable]** [#6980](https://github.com/earendil-works/pi/pull/6980)
    *   Replaces native SDK retries with a common helper that enforces max delay caps and supports `AbortSignal`, fixing the un-interruptible retry loops reported in #6911.
*   **[feat(coding-agent): expose session metadata to bash tools]** [#6967](https://github.com/earendil-works/pi/pull/6967)
    *   Exposes session ID, provider, and model info to subprocesses, enabling better context awareness for shell scripts and extensions.
*   **[feat(ai): support constrained sampling]** [#6341](https://github.com/earendil-works/pi/pull/6341)
    *   Adds opt-in `constrainedSampling` config, allowing providers to enforce JSON-schema strictness on tool arguments at the API level.
*   **[feat: Add Amazon Bedrock Mantle OpenAI Responses provider]** [#6216](https://github.com/earendil-works/pi/pull6216)
    *   Introduces native support for AWS Bedrock Mantle via the OpenAI Responses API, expanding cloud provider options.
*   **[feat(ai): honor compat.forceAdaptiveThinking in bedrock-converse-stream]** [#6984](https://github.com/earendil-works/pi/pull/6984)
    *   Fixes validation exceptions for Claude models on Bedrock by respecting the `forceAdaptiveThinking` compatibility flag.
*   **[feat: Add native OpenRouter OAuth support]** [#6927](https://github.com/earendil-works/pi/pull/6927)
    *   Implements PKCE S256 OAuth flow for OpenRouter, allowing browser-based authentication without manual API key management.
*   **[feat(ai): add StepFun providers]** [#6960](https://github.com/earendil-works/pi/pull/6960)
    *   Adds four new providers for StepFun models (China/Global/Prepaid), broadening access to Chinese LLM ecosystems.
*   **[fix(coding-agent): speed up external editor launch]** [#6903](https://github.com/earendil-works/pi/pull/6903)
    *   Refactors temp file creation to use isolated subdirectories instead of `/tmp`, resolving performance issues in crowded temp directories (#6774).
*   **[fix(tui): align grapheme widths with terminal cells]** [#6987](https://github.com/earendil-works/pi/pull/6987)
    *   Improves TUI rendering accuracy by correctly estimating cell widths for complex graphemes, preventing layout breaks.
*   **[feat(agent): add AgentHarness execution tools]** [#6916](https://github.com/earendil-works/pi/pull/6916)
    *   Introduces `AgentHarnessTool` abstraction, allowing custom contexts (execution environment, session ID) to be passed through tool execution layers.

## 5. Feature Request Trends
*   **Provider-Side Constraint Enforcement:** Strong interest in moving validation from client-side to provider-side (Constrained Sampling PR #6341).
*   **Intelligent Model Navigation:** Requests for MRU-based model switching (#6982) and better thinking effort control (#6974) suggest users want faster, context-aware navigation.
*   **Structured Extension APIs:** Developers are requesting more granular control over extension approvals (#5954) and per-block thinking labels (#6988) to build more sophisticated agent behaviors.
*   **Enhanced Cloud Provider Support:** Continued expansion into AWS Bedrock (#6216, #6984) and specialized providers like StepFun (#6960) and OpenRouter OAuth (#6927).

## 6. Developer Pain Points
*   **Retry Logic & Abortability:** The inability to interrupt long-running SDK retries (#6911) was a major frustration, now being addressed.
*   **Concurrency in TUI:** Race conditions in extension dialogs (#6978) and session cleanup failures in subprocesses (#6924) highlight ongoing challenges with async state management in the TUI.
*   **Windows Path Handling:** Absolute path leaks (#6619) and terminal multiplexer conflicts (#6973) indicate persistent cross-platform compatibility issues, particularly on Windows.
*   **Auth Complexity:** Conflicts between OAuth, Plugin, and API Key flows for GitHub Copilot and Anthropic (#6970, #6979) create confusion and billing discrepancies for users.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest
**Date:** 2026-07-23

## 1. Today's Highlights
Significant progress was made on the daemon architecture with PR #7388 introducing explicit channel delivery contracts, while core stability improvements focused on fixing `enable_thinking` parameter errors in TokenPlan endpoints (Issue #7284/PR #7534). Additionally, the team addressed critical CLI update failures related to `mise` bash wrappers and refined prompt fragment caching strategies to enhance model interaction reliability.

## 2. Releases
*   **v0.0.0-benchmark-poc.20260722.1**: A temporary prerelease published on 2026-07-22. This is a Proof of Concept (POC) for benchmarking infrastructure, validating the GitHub Actions → ECS benchmark worker → GitHub result publication pipeline. It is **not** a product release and should not be used for production workloads.
    *   [View Release](https://github.com/QwenLM/qwen-code/releases)

## 3. Hot Issues
1.  **[CLOSED] #7284: side-query forces enable_thinking=false**
    *   **Why it matters:** Caused 400 errors on DashScope/TokenPlan endpoints requiring thinking mode.
    *   **Reaction:** High priority bug affecting core agent functionality; resolved via retry logic in PR #7534.
2.  **#7167: Fleet Shepherd Dashboard**
    *   **Why it matters:** Automated maintenance issue tracking CI health and sync status.
    *   **Reaction:** Operational metadata; auto-maintained by workflows.
3.  **#7516: Main CI failed: E2E Tests**
    *   **Why it matters:** Blocked merges due to flaky E2E tests on main branch commit `d064bd7`.
    *   **Reaction:** Flagged as ready for agent fix; impacts release velocity.
4.  **#7537: Core test suite red on main**
    *   **Why it matters:** `fork dispatch` test failure caused all open PRs to show red CI status regardless of code quality.
    *   **Reaction:** Critical blocker for contributors; resolved internally.
5.  **#7549: Release Failed for v0.20.1-nightly**
    *   **Why it matters:** Nightly build failed at the `quality` stage.
    *   **Reaction:** Automated alert; indicates potential regression in linting or testing gates.
6.  **#7543: getNpmCliPath returns mise wrapper**
    *   **Why it matters:** Breaks the `/update` command and startup checks for users using `mise` as their node version manager.
    *   **Reaction:** User-reported friction point with non-standard npm environments.
7.  **#7514: Persist workspace channel configuration**
    *   **Why it matters:** Part of the larger DingTalk/WeCom/Feishu integration effort (#7209).
    *   **Reaction:** Anticipated feature for enterprise users requiring persistent chat ops configurations.
8.  **#7522: Hide discontinued OAuth model**
    *   **Why it matters:** Prevents confusion when switching auth types by hiding obsolete Qwen OAuth models.
    *   **Reaction:** UX improvement for multi-auth setups.
9.  **#7513: Matrix ECS runner update**
    *   **Why it matters:** Fixes CI reliability by correcting the install target for GitHub Actions runners.
    *   **Reaction:** Infrastructure fix ensuring consistent testing environments.
10. **#7542: Add version upgrade notices**
    *   **Why it matters:** Improves user awareness of new features during CLI updates.
    *   **Reaction:** Positive UX enhancement for community adoption.

## 4. Key PR Progress
1.  **#7388: feat(daemon): add explicit channel delivery**
    *   Introduces a typed channel contract for daemon notifications, allowing precise routing to workers based on workspace and user/chat targets.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7388)
2.  **#7530: refactor(core): tier prompt fragments by cache stability**
    *   Reorganizes system instructions into stable, context, and volatile tiers to optimize caching and ensure product/workspace instructions are prioritized correctly.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7530)
3.  **#7517: feat(core): add Goal v3 state protocol**
    *   Defines the versioned Goal v3 state contract, including lifecycle states, optimistic concurrency controls, and deterministic transitions for agents.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7517)
4.  **#7534: fix(core): retry requests when providers require thinking**
    *   Implements a retry mechanism that detects `enable_thinking` mismatches and rebuilds requests to comply with provider constraints (fixes Issue #7284).
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7534)
5.  **#7471: feat(web-shell): add git mode selector**
    *   Adds a popover selector in the Web Shell composer for choosing git workflows (Current Branch, New Branch, or Detached HEAD) during session creation.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7471)
6.  **#7535: fix(scripts): retry model calls and surface degraded release notes**
    *   Ensures release note generation fails visibly if model calls fail, preventing silent degradation of documentation.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7535)
7.  **#7501: fix(cli): open the actual serve fallback port**
    *   Corrects Express listen error handling to ensure the server URL returned matches the actually bound port, improving CLI reliability.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7501)
8.  **#7527: fix(core): strip daemon secrets from child env**
    *   Extends `sanitizeChildEnv()` to agent-launched child processes (hooks, tool discovery) to prevent secret leakage.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7527)
9.  **#7536: feat(core): Align GenAI telemetry with ARMS**
    *   Standardizes LLM, tool, and agent span attributes to match Alibaba Cloud ARMS semantic conventions for better observability.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7536)
10. **#7519: fix(web-shell): suppress stale dist type errors**
    *   Temporarily suppresses TypeScript errors in `web-shell` caused by stale `.d.ts` files without altering business logic, unblocking E2E tests.
    *   [Link](https://github.com/QwenLM/qwen-code/pull/7519)

## 5. Feature Request Trends
*   **Enterprise ChatOps Integration:** Strong focus on persisting and managing channels for DingTalk, WeCom, and Feishu (PRs #7388, #7514), indicating a push toward deeper enterprise ecosystem integration.
*   **Advanced Agent State Management:** Introduction of Goal v3 state protocols (PR #7517) suggests a trend toward more deterministic, auditable, and complex agent lifecycles.
*   **Improved Git Workflow UX:** The addition of a git mode selector in Web Shell (PR #7471) reflects user demand for more flexible source control operations within the coding environment.

## 6. Developer Pain Points
*   **Environment-Specific CLI Failures:** Users encountering update/check failures when using alternative node managers like `mise` (Issue #7543), highlighting fragility in path resolution logic.
*   **CI Instability:** Recurring flakiness in E2E tests and fork dispatch tests on the main branch (Issues #7516, #7537) creates noise and blocks contributions.
*   **Provider API Incompatibilities:** Friction with DashScope/TokenPlan endpoints regarding `enable_thinking` parameters (Issue #7284) requires manual retry logic or configuration adjustments.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest
**Date:** 2026-07-23
**Source:** Hmbown/CodeWhale (DeepSeek TUI)

### 1. Today's Highlights
The v0.9.1 release cycle has reached critical mass with the closure of major UX and reliability blockers, including a unified `/skills` manager, refined Work strip chrome, and fixes for Kimi Code model ID cross-pairings. Simultaneously, the community is pivoting toward v0.9.2 optimizations, focusing heavily on a "context diet" to reduce token usage and improve model performance across diverse environments. A critical Windows installer bug overwriting the user PATH variable has also been flagged for immediate attention.

### 2. Releases
*   **No new releases published in the last 24 hours.** The project is currently in the final stabilization phase for v0.9.1, with security gates and dependency patches being applied to the merged tree.

### 3. Hot Issues
*   **#2870: EPIC: staged command-boundary refactor** [OPEN]
    *   *Why it matters:* This tracking issue coordinates the complex refactoring of command boundaries referenced in #2791. It ensures smaller, mergeable layers are used instead of monolithic changes.
    *   *Community Reaction:* High engagement (17 comments) indicates strong interest in the architectural direction.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/2870)

*   **#2889: Work Agent rows: real sub-agent details** [CLOSED]
    *   *Why it matters:* Restored from a deleted issue to provide focused design for displaying sub-agent activity in the sidebar, improving transparency in multi-agent workflows.
    *   *Community Reaction:* Resolved by maintainer @Hmbown after contributor @aboimpinto offered a focused pass.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/2889)

*   **#2886: Add Gherkin acceptance E2E coverage for tool lifecycle** [CLOSED]
    *   *Why it matters:* Establishes robust end-to-end testing for the command strategy direction, ensuring reliability as the codebase evolves.
    *   *Community Reaction:* Closed as part of the v0.9.1 release blockers.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/2886)

*   **#4691: Ship the model-invoked default CodeWhale skill pack** [CLOSED]
    *   *Why it matters:* Delivers a coherent first-party skill pack comparable to competitors like Devin CLI and Claude Code, enhancing out-of-the-box utility.
    *   *Community Reaction:* Successfully merged as a release blocker.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4691)

*   **#4685: Installer overwrites user PATH environment variable on Windows 10** [OPEN]
    *   *Why it matters:* Critical bug where `CodeWhaleSetup.exe` replaces existing PATH entries instead of appending, breaking other tools.
    *   *Community Reaction:* Reported by @MuRongMoQing; requires urgent fix before wider distribution.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4685)

*   **#4713: v0.9.1 security gate: deep scan and dependency alert disposition** [OPEN]
    *   *Why it matters:* Pre-release requirement to address 17 Dependabot alerts (7 high, 10 moderate) across npm dependencies like axios and protobufjs.
    *   *Community Reaction:* Maintainer-driven security gate.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4713)

*   **#4704: Context diet: minimize every model-facing prompt, schema, and payload** [OPEN]
    *   *Why it matters:* Core initiative for v0.9.2 to audit and reduce non-essential bytes in prompts, aiming for simpler, more portable behavior across model families.
    *   *Community Reaction:* Parent issue for several optimization tasks; high priority for cost/performance efficiency.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4704)

*   **#4705: Minimize tool results, reminders, and sub-agent completion payloads** [OPEN]
    *   *Why it matters:* Addresses verbose output in model-visible results, stripping UI metadata and redundant status fields to save tokens and improve signal-to-noise ratio.
    *   *Community Reaction:* Part of the broader context diet effort.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4705)

*   **#4709: Deduplicate project, environment, route, locale, and skill context** [OPEN]
    *   *Why it matters:* Removes redundant context packs that bloat prompts without adding value, directly supporting the v0.9.2 context optimization goals.
    *   *Community Reaction:* Technical refinement requested by maintainers.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4709)

*   **#4676: Art-direct transcript rhythm and semantic color hierarchy** [CLOSED]
    *   *Why it matters:* Improves visual readability of terminal conversations by distinguishing user turns, model thinking, and tool actions through deliberate color and layout grammar.
    *   *Community Reaction:* Closed as part of v0.9.1 UX polish.
    *   [Link](https://github.com/Hmbown/CodeWhale/issues/4676)

### 4. Key PR Progress
*   **#4679: feat(skills): unified /skills manager with audit and owned mutations** [CLOSED]
    *   *Summary:* Implements the single `/skills` manager for inventory, audit, install, update, remove, and trust across project and global roots.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4679)

*   **#4714: chore(deps): patch npm lockfiles for Dependabot alerts** [OPEN]
    *   *Summary:* Applies `npm audit fix` to resolve 17 open Dependabot alerts, updating packages like protobufjs and axios.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4714)

*   **#4711: fix(tui): focus v0.9.1 chrome on todos and agents** [CLOSED]
    *   *Summary:* Refines the top bar to show only active To-dos and Sub-agents, hides completed-only chrome, and enables draggable dividers.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4711)

*   **#4695: feat(skills): default CodeWhale skill pack (bundled v5)** [CLOSED]
    *   *Summary:* Ships the v0.9.1 default end-user skill pack with bundled version 5, including models and user skills like interview, plan, debug, etc.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4695)

*   **#4696: feat(tui): ship staged /uwu theme** [CLOSED]
    *   *Summary:* Adds the "uwu" theme with soft-classic whale mark and color shimmer aliases (owo, kawaii).
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4696)

*   **#4694: fix(kimi): fail closed on K3 model-ID cross-pairings** [CLOSED]
    *   *Summary:* Fixes route identity issues where base URL and model ID were treated interchangeably, ensuring correct API calls for Kimi/Moonshot models.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4694)

*   **#4693: fix(tui): Work summary lifecycle, actionable title, and top-area hierarchy** [CLOSED]
    *   *Summary:* Coordinates fixes for Work summary expiration, actionable titles, and top-area hierarchy to resolve dogfood observations.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4693)

*   **#4087: refactor(hooks): split config and executor modules** [OPEN]
    *   *Summary:* Splits large `hooks.rs` module into separate config and executor files to improve reviewability and policy changes.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4087)

*   **#4370: feat: add TelecomJS provider support** [CLOSED]
    *   *Summary:* Adds support for TelecomJS provider routes, fixing an issue where custom providers didn't fetch full model catalogs.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4370)

*   **#4686: feat(minimax): add China / Token Plan provider routes for minimaxi.com** [OPEN]
    *   *Summary:* Adds four new provider identifiers targeting api.minimaxi.com for OpenAI Chat Completions and Anthropic Messages APIs.
    *   [Link](https://github.com/Hmbown/CodeWhale/pull/4686)

### 5. Feature Request Trends
*   **Context Optimization & Efficiency:** There is a strong trend toward reducing token consumption and improving context relevance. Issues #4704, #4705, #4707, #4708, and #4709 all point to a "context diet" for v0.9.2, aiming to strip redundant system prompt layers, shorten tool descriptions, and deduplicate project/environment contexts.
*   **Unified Skill Management:** The introduction of the `/skills` manager (#4679) reflects a demand for a centralized, auditable, and trust-based system for managing skills across project and global scopes, moving away from fragmented skill handling.
*   **Enhanced UX Transparency:** Users are requesting clearer visibility into agent activities and work states. Issues like #2889 (sub-agent details) and #4689 (actionable to-do in Work summary) highlight a need for better information hierarchy in the TUI.

### 6. Developer Pain Points
*   **Windows Installer PATH Corruption:** Issue #4685 highlights a severe usability pain point where the Windows installer overwrites the user PATH variable, breaking other installed tools. This is a critical regression for Windows users.
*   **Prompt Verbosity and Token Waste:** Developers are struggling with overly verbose tool descriptions and system prompts that dilute action-selection signals and increase costs. Issues #4708 and #4710 explicitly call out the need to shorten tool descriptions and collapse redundant stable system-prompt layers.
*   **Dependency Security Alerts:** The presence of 17 Dependabot alerts (#4713), including high-severity ones in widely used libraries like axios and protobufjs, creates friction in the release process and requires immediate attention to ensure supply chain security.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>