# AI CLI Tools Community Digest 2026-08-08

> Generated: 2026-08-08 02:02 UTC | Tools covered: 10

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

# AI CLI Tools Ecosystem Report — 2026-08-08

## 1. Ecosystem Overview
The AI CLI tool landscape is currently defined by a shift from basic conversational interfaces to robust, enterprise-grade agentic workflows. Major vendors (Anthropic, OpenAI, Google, GitHub) are rapidly iterating on sub-agent reliability, security boundaries, and cross-provider compatibility. Simultaneously, emerging tools are competing on specialized features like persistent memory, cost transparency, and local-first execution. The market is consolidating around standards for interoperability (e.g., AGENTS.md) while grappling with significant stability challenges on Windows and in complex sandbox environments.

## 2. Activity Comparison

| Tool | Issues (New/Active) | PRs (Active/Merged) | Release Status |
| :--- | :--- | :--- | :--- |
| **Claude Code** | 10 Hot Issues | 3 Key PRs | **v2.1.225** (Active) |
| **OpenAI Codex** | 10 Hot Issues | 10 Key PRs | **v0.148 Alpha Series** (Iterative) |
| **Gemini CLI** | 10 Hot Issues | 10 Key PRs | **v0.56.0-nightly** (Active) |
| **GitHub Copilot** | 10 Hot Issues | 0 New | **v1.0.79-7/8/9** (Micro-updates) |
| **Kimi Code** | 2 Hot Issues | 2 Key PRs | None (Stable) |
| **OpenCode** | 10 Hot Issues | 10 Key PRs | **v1.18.15** (Bugfix) |
| **Pi** | 10 Hot Issues | 10 Key PRs | **v0.84.1** (Active) |
| **Qwen Code** | 10 Hot Issues | 10 Key PRs | **v0.21.7-nightly** (Active) |
| **DeepSeek TUI** | 10 Hot Issues | 10 Key PRs | **v0.9.4** (Blocked/Polish) |
| **Grok Build** | 0 | 0 | None |

## 3. Shared Feature Directions

*   **Cross-Tool Standardization (`AGENTS.md`):**
    *   *Tools:* Claude Code, OpenCode, Pi.
    *   *Need:* A unified agent configuration standard compatible across Codex, Cursor, and Claude. Claude Code Issue #6235 is the dominant request (4,500+ upvotes).
*   **Sub-Agent Reliability & Orchestration:**
    *   *Tools:* Gemini CLI, OpenCode, Pi, DeepSeek TUI, Kimi Code.
    *   *Need:* Fixing hangs, false success reporting, and state loss in sub-agents. Gemini CLI and DeepSeek TUI have active PRs addressing sub-agent termination and shared-workspace contention.
*   **Persistent Memory & Context:**
    *   *Tools:* Kimi Code, DeepSeek TUI, OpenCode.
    *   *Need:* Cross-session continuity to avoid re-prompting. Kimi Code Issue #1283 and DeepSeek Issue #2492 highlight this as a top-user demand.
*   **Enterprise Security & Sandbox Control:**
    *   *Tools:* GitHub Copilot, OpenAI Codex, Qwen Code.
    *   *Need:* Granular policy enforcement (allow-auto-only), safe destructive command handling, and credential isolation. Copilot introduced `allow-auto-only` policies; Qwen added Git cross-worktree mutation guards.
*   **Platform-Specific Stability (Windows/Linux):**
    *   *Tools:* All major tools.
    *   *Need:* Resolving TUI rendering failures, clipboard issues, and streaming resets on Windows; TMUX/SSH compatibility on Linux.

## 4. Differentiation Analysis

*   **Claude Code:** Focuses on **enterprise trust and plugin security**. Key differentiators are workspace trust prompts, plugin injection fixes, and the push for `AGENTS.md` standardization. Targets professional developers in regulated environments.
*   **OpenAI Codex:** Emphasizes **protocol standardization and backend infrastructure**. Heavy investment in gRPC code-mode protocols, Guardian review enforcement, and multi-provider MCP support. Targets developers needing deep integration with OpenAI’s ecosystem.
*   **Gemini CLI:** Centers on **model capacity management and eval-driven reliability**. Active work on false-positive capacity exhaustion errors and robust behavioral evals. Targets users of Google’s Flash models and those requiring high-assurance agent behavior.
*   **GitHub Copilot CLI:** Prioritizes **IDE integration and enterprise sandbox policies**. Features like `/sandbox` config UX and agent plugin extensibility are key. Targets users deeply embedded in the GitHub/VS Code workflow.
*   **OpenCode:** Differentiates through **modularity and provider flexibility**. Strong support for local models, crypt payments, and background sub-agents. Appeals to self-hosted and cost-conscious developers.
*   **Pi:** Focuses on **local-first and cross-tool compatibility**. Unique Cursor CLI auth bridge and LM Studio provider support. Targets privacy-conscious users and those using diverse local model setups.
*   **Qwen Code:** Highlights **desktop/mobile accessibility and reasoning controls**. Features like QR-code pairing and model-specific reasoning effort (thought_level) are distinct. Targets users seeking mobile companions and fine-grained reasoning control.
*   **DeepSeek TUI:** Emphasizes **multi-provider fleet management and cost-tier automation**. The `model = auto` feature for switching between pro/flash models based on prompt complexity is unique. Targets users optimizing for cost/performance balance.
*   **Kimi Code:** Currently focuses on **core stability and safety**. Recent critical fixes for `rm -rf` safety and UTF-8 data corruption indicate a phase of hardening after earlier rapid growth.

## 5. Community Momentum & Maturity

*   **High Momentum & Rapid Iteration:**
    *   **OpenAI Codex:** Frequent alpha releases (v0.148) and active backend PRs show rapid, aggressive development.
    *   **Gemini CLI:** Strong community engagement on reliability issues and active PRs for capacity and eval infrastructure.
    *   **Qwen Code:** Active nightly releases and a broad feature set (mobile, reasoning controls) indicate fast-paced growth.
*   **Mature & Stable:**
    *   **Claude Code:** Large, established community with high upvote counts on feature requests (e.g., AGENTS.md). Focus is on stability and enterprise features.
    *   **GitHub Copilot CLI:** Micro-updates suggest a mature product refining existing features rather than adding large new ones.
*   **Emerging/Polishing:**
    *   **Kimi Code:** Smaller issue volume but critical safety patches indicate a tool maturing its core safety guarantees.
    *   **DeepSeek TUI:** Pre-release polish phase (v0.9.4 blockers) with a strong focus on internal code hygiene and reliability.
*   **Niche/Specialized:**
    *   **OpenCode & Pi:** Active but smaller communities focused on specific use cases (self-hosting, local models).

## 6. Trend Signals

*   **Interoperability is Critical:** The overwhelming demand for `AGENTS.md` (Claude Code #6235) signals that users want tools that don’t lock them into a single vendor’s configuration format. Developers should anticipate or support standardized agent metadata.
*   **Sub-Agent Reliability is the New Bottleneck:** Multiple tools (Gemini, OpenCode, Pi, DeepSeek) are actively fixing sub-agent hangs and state loss. This indicates that agentic workflows are becoming more common, and their reliability is now a key differentiator.
*   **Windows Instability is a Persistent Theme:** Nearly every major tool reports Windows-specific bugs (TUI freezes, clipboard issues, streaming resets). This is a significant pain point for enterprise adoption on Windows.
*   **Cost & Resource Awareness Growing:** Features like `model = auto` (DeepSeek), token usage reporting (Copilot), and capacity exhaustion fixes (Gemini) show that users are increasingly concerned about cost control and resource limits.
*   **Security Hardening Post-Rapid Growth:** Kimi Code’s critical `rm -rf` fix and Claude Code’s plugin security patches reflect a broader industry move to tighten security boundaries as agentic capabilities expand. Developers should prioritize safe-by-default configurations.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Date:** 2026-08-08 | **Source:** anthropics/skills

## 1. Top Skills Ranking (Most Discussed PRs)

| Rank | PR | Skill | Status | Summary |
|------|-----|-------|--------|---------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator (fix)** | Open | Fixes critical `run_eval.py` bug causing 0% recall on all skills, breaking the description optimization loop. Multiple sub-fixes for Windows compatibility. |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Open | Adds typographic quality control for generated documents, addressing orphan lines, widow paragraphs, and numbering misalignment. |
| 3 | [#538](https://github.com/anthropics/skills/pull/538) | **pdf (fix)** | Open | Corrects 8 case-sensitivity mismatches in SKILL.md references that break on case-sensitive filesystems. |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | **odt** | Open | New OpenDocument Format skill covering .odt, .ods creation, filling, parsing, and conversion to HTML. |
| 5 | [#210](https://github.com/anthropics/skills/pull/210) | **frontend-design (improve)** | Open | Revisions to improve clarity, actionability, and internal coherence of the frontend-design skill instructions. |
| 6 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer** | Open | Meta-skill for comprehensive quality analysis across structure, documentation, examples, and security dimensions. |
| 7 | [#541](https://github.com/anthropics/skills/pull/541) | **docx (fix)** | Open | Fixes document corruption from tracked changes colliding with existing bookmarks due to shared `w:id` space. |
| 8 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Open | Comprehensive testing skill covering testing philosophy, unit tests (AAA pattern), and React component testing. |

## 2. Community Demand Trends

Based on top-voted and most-commented issues:

- **Skill Development Tooling:** High demand for fixing `skill-creator` evaluation infrastructure (Issues #556, #1169; PRs #1298, #1099, #1050). Users need reliable skill optimization loops.
- **Cross-Platform Compatibility:** Strong interest in Windows support for skill development tools (PRs #1298, #1099, #1050).
- **Enterprise Document Handling:** Demand for robust DOCX and ODT skills with proper handling of tracked changes, bookmarks, and case sensitivity (PRs #486, #541).
- **Security & Governance:** Interest in skill quality analysis (#83) and agent governance patterns (Issue #412) to ensure safe skill deployment.
- **Organization Sharing:** Feature request for org-wide skill sharing in Claude.ai to streamline team collaboration (Issue #228, 8 👍).
- **SAP/Enterprise Integration:** Niche but engaged community around SAP skills, including predictive analytics with SAP-RPT-1-OSS (PR #181).

## 3. High-Potential Pending Skills

| PR | Skill | Why It's Promising |
|----|-------|-------------------|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Mechanical verification + four-dimension reasoning quality gate. Universal application across projects and models. |
| [#1479](https://github.com/anthropics/skills/pull/1479) | **plan-file-hygiene** | Addresses planning artifact accumulation with lifecycle management. Built on community-identified need (Issue #1417). |
| [#1302](https://github.com/anthropics/skills/pull/1302) | **color-expert** | Comprehensive color knowledge covering naming systems, color spaces, and practical "what to use when" guidance. |
| [#525](https://github.com/anthropics/skills/pull/525) | **pyxel** | Retro game development skill with integrated MCP server workflow (write → run → inspect → iterate). |
| [#1261](https://github.com/anthropics/skills/pull/1261) | **skill-creator (fix)** | Isolates trigger-eval command files from live project, preventing concurrent session interference. |

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **reliable skill development tooling and cross-platform compatibility**, particularly fixing the `skill-creator` evaluation pipeline to enable effective skill optimization and publishing.

---

# Claude Code Community Digest — 2026-08-08

## 1. Today's Highlights
Anthropic released **v2.1.225**, introducing gateway spend-limit awareness in usage warnings and workspace trust prompts for agent directories. The community's top concern remains the push for **AGENTS.md** standardization, with Issue #6235 accumulating over 4,500 upvotes. Meanwhile, critical security patches for plugin injection vulnerabilities are progressing through pull requests.

## 2. Releases
*   **v2.1.225**: Enhances usage warnings with gateway spend-limit details (cap, reset time, operator message) and adds a workspace trust prompt for `claude agents` in untrusted directories.
    *   *Note: Full release notes were truncated in source data.*

## 3. Hot Issues
*   **#6235: Support AGENTS.md [Enhancement]** (347 comments, 4,526 👍)
    *   *Why it matters:* Users want a unified `AGENTS.md` standard compatible with Codex, Cursor, and Amp, arguing `CLAUDE.md` is too platform-specific. This is the dominant community feature request.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/6235)
*   **#14920: Disable individual plugin skills [Enhancement]** (14 comments, 83 👍)
    *   *Why it matters:* Users seek granular control over plugin tools (e.g., disabling `commit-push-pr` while keeping `commit`), improving workflow precision.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/14920)
*   **#64706: Agent tool ignores `effort:` frontmatter [Bug]** (7 comments, 5 👍)
    *   *Why it matters:* Subagents inherit global `effortLevel` instead of respecting individual `.md` declarations, breaking expected agent behavior configuration.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/64706)
*   **#59750: Claude agents TUI unresponsive on Windows [Bug]** (7 comments, 8 👍)
    *   *Why it matters:* A severe rendering and input loop failure on Windows Terminal (v2.1.143) renders the agent TUI unusable for Windows users.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/59750)
*   **#50884: Remove stale Remote Control environments [Enhancement]** (7 comments, 26 👍)
    *   *Why it matters:* Users cannot clean up dead environments from the `claude.ai/code` list, leading to clutter and confusion in Remote Control workflows.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/50884)
*   **#72495: Prompt suggestions silently suppressed [Bug]** (4 comments, 0 👍)
    *   *Why it matters:* A strict-equality gate in the rate-limit status check causes suggestions to disappear unpredictably when the client-derived status is `allowed_warning`.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/72495)
*   **#84689: CVP approved org blocked by cyber safeguards [Bug]** (4 comments, 0 👍)
    *   *Why it matters:* Organizations with confirmed CVP approval are still hitting safeguards blocks with no appeal fields, indicating a potential backend misconfiguration or gap.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/84689)
*   **#84945: Local peer-messaging inbox socket fails [Bug]** (3 comments, 0 👍)
    *   *Why it matters:* Cross-session messaging fails on macOS when two sessions launch simultaneously, due to socket binding issues in `/tmp/cc-socks`.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/84945)
*   **#84072: ECONNRESET on Windows during API stream [Bug]** (3 comments, 0 👍)
    *   *Why it matters:* Streaming responses on Windows crash after the first chunk, affecting both CLI and VS Code extension users.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/84072)
*   **#77372: Stale environments cannot be deleted [Bug]** (3 comments, 1 👍)
    *   *Why it matters:* Remote Control environments result in permanent 404 errors for new sessions, suggesting a backend cleanup failure for registered environments.
    *   [View Issue](https://github.com/anthropics/claude-code/issues/77372)

## 4. Key PR Progress
*   **#84747: Fix hookify rule evaluation scope and secure file read**
    *   Fixes a security logic issue where `load_rules()` bypassed event filters when `event` is `None`, ensuring unscoped tools only trigger `all`-scoped rules.
    *   [View PR](https://github.com/anthropics/claude-code/pull/84747)
*   **#84711: Fix yaml injection and symlink credential overwrites**
    *   Adds defensive checks in plugin scripts to prevent YAML injection attacks and symlink-based credential overwrites (fixes #76580).
    *   [View PR](https://github.com/anthropics/claude-code/pull/84711)
*   **#84854: Fix stale hooks documentation link**
    *   Updates a broken link in `bash_command_validator_example.py` to point to the current `code.claude.com` documentation.
    *   [View PR](https://github.com/anthropics/claude-code/pull/84854)

## 5. Feature Request Trends
*   **Cross-Tool Standardization:** The overwhelming demand for `AGENTS.md` (#6235) signals a desire for interoperability with other AI coding agents (Codex, Cursor).
*   **Granular Permission Control:** Users frequently request the ability to disable specific plugin skills (#14920) and allow-list hosts (#84949).
*   **Remote Control Hygiene:** Requests to clean up stale environments (#50884) and manage Remote Control session lifecycle are recurring themes.
*   **Workflow Automation:** Features like persistent response pinning (#70987) and higher character limits for goal conditions (#84953) indicate a need for better long-form agentic workflows.

## 6. Developer Pain Points
*   **Windows Stability:** Multiple reports of TUI unresponsiveness (#59750), streaming resets (#84072), and desktop app crashes (#84951, #83028) highlight significant Windows-specific instability.
*   **Security & Safeguards False Positives:** Users in authorized security workflows are hitting false positives in safeguards (#84952) and CVP-approved orgs being blocked (#84689), causing friction in legitimate development.
*   **Plugin & Hook Reliability:** Bugs related to plugin tool enforcement (#84956), socket binding for cross-session messaging (#84945), and YAML injection vulnerabilities (#84711) point to fragility in the plugin system.
*   **Environment Management:** Stale Remote Control environments causing permanent 404s (#77372) and inability to delete them (#50884) create operational debt for teams.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-08-08

## 1. Today's Highlights
This release cycle is dominated by a new v0.148 alpha series and significant backend refinements to the Guardian review system, including auto-review policy enforcement and namespace-aware tool metadata. Community attention is heavily focused on persistent Windows sandbox execution failures, model routing anomalies in multi-turn conversations, and critical memory regression issues on macOS.

## 2. Releases
Three new Rust alpha releases were deployed in the last 24 hours, signaling continued iterative development on the CLI backend:
*   **rust-v0.148.0-alpha.1**: [Release 0.148.0-alpha.1](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.1)
*   **rust-v0.148.0-alpha.2**: [Release 0.148.0-alpha.2](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.2)
*   **rust-v0.148.0-alpha.4**: [Release 0.148.0-alpha.4](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.4)

## 3. Hot Issues
These issues represent the highest community engagement and technical friction currently reported:

*   **Conversation Context Routing [#8648]** (82 comments, 58 👍): Users report the agent replying to stale messages in multi-turn threads rather than the latest input. This impacts core usability for developers using `gpt-5.2-xhigh`.
*   **MCP Namespace Tools for Non-OpenAI Providers [#26234]** (32 comments, 41 👍): A critical blocking issue for users running Ollama, LM Studio, or OpenRouter. MCP tools fail to serialize correctly outside the OpenAI Responses API, preventing tool usage entirely.
*   **Windows Computer Use EnumWindows Failure [#37043]** (17 comments): New failure in the Windows Computer Use helper where `sky.list_apps()` and `list_windows()` throw `0x80070003`. This isolates a specific Windows UI-automation regression.
*   **Azure Empty Function Namespace Regression [#37380]** (9 comments, 19 👍): A v0.147.0 regression where Azure OpenAI endpoints reject requests with empty function namespace descriptions, breaking `gpt-5.6-sol` usage via Azure API Management.
*   **VS Code Diff View Error [#35481]** (26 comments, 54 👍): A widespread Windows bug causing the Codex Diff view to crash with an internal error, rendering code review workflows unusable for many users.
*   **Global Project Trust Level [#14599]** (16 comments, 57 👍): A highly upvoted feature request to allow `trust_level = "trusted"` for any project, eliminating the repetitive manual approval prompts at project initialization.
*   **Legacy Subagent Tool Availability [#25990]** (6 comments): Reports that older resumed Codex Desktop threads do not inherit newly available tools or the latest subagent runtime, creating inconsistent experiences across session resumption.
*   **Bubblewrap Sandbox Errors on Ubuntu 24.04 [#29908]** (14 comments): `apply_patch` and managed sandbox commands fail on specific kernel/bubblewrap configurations, highlighting fragmentation in Linux sandboxing support.
*   **LiteLLM Streaming Regression [#37425]** (4 comments): Users upgrading to v0.147.0 report consistent streaming failures with LiteLLM providers, indicating a breaking change in transport handling.
*   **Intel macOS Computer Use Missing Helper [#24437]** (6 comments): The Intel Mac build continues to lack the `computer-use` bundled plugin, forcing Apple Silicon-only features on older hardware.

## 4. Key PR Progress
Major backend and protocol advancements merged or closed recently:

*   **Guardian Auto-Review Enforcement [#37511]**: Enforces automatic review for managed models and unions model slugs across requirement layers.
*   **Code-Mode Host gRPC Protocol [#37510]**: Defines the new `codex.code_mode.v1` protobuf API for managing code-mode sessions, executions, and tool callbacks.
*   **MCP Event Discovery [#37494]**: Adds `events/stream` subscriptions to the MCP client, allowing lifecycle notifications for hosted Plugin Runtime events.
*   **Turn Metadata & Tool Namespaces [#37492]**: Includes an opt-in `tool_namespaces_info` inventory in turn metadata, improving observability of available functions.
*   **Auto-Review Config Requirements [#37519]**: Exposes `ignoreRules` in the app-server v2 protocol, allowing clients to understand which models skip validation.
*   **Connection Resilience [#37485]**: Implements exponential backoff retries (5–60s) for HTTP connection failures, preserving response streams during network blips.
*   **Code-Mode WebSocket Latency [#37504]**: Disables Nagle's algorithm (`TCP_NODELAY`) on code-mode WebSockets to reduce latency for interactive sessions.
*   **Diagnostics & Tracing Limits [#37497]**: Caps payload traces in SQLite logs to prevent diagnostic ring buffers from being overwhelmed by high-volume traffic.
*   **Code-Mode Cell Interruption [#37483]**: Ensures that interrupting a turn now terminates active code-mode cells, preventing orphaned processes.
*   **Child Process Cleanup [#37498]**: Preserves child waiters during process termination to ensure PTY children are properly reaped and exit statuses recorded.

## 5. Feature Request Trends
*   **Automation of Trust & Approval Flows**: There is strong demand (#14599) and implementation (#37511, #37516) to reduce friction in code execution approvals, specifically for cyber models and global project settings.
*   **Cross-Provider MCP Compatibility**: Developers are pushing for robust MCP support beyond OpenAI, specifically requesting namespace flattening for local and gateway models (#26234).
*   **Protocol Standardization**: Significant effort is being poured into defining the code-mode gRPC protocol (#37510) and standardizing how tool namespaces and sandbox modes are reported in metadata (#37507, #37492).
*   **Hardware Abstraction**: Users continue to request parity for legacy hardware, specifically the inclusion of Computer Use helpers on Intel macOS builds (#24437).

## 6. Developer Pain Points
*   **Windows Execution & Sandbox Instability**: A recurring cluster of high-severity bugs on Windows, including `CreateProcessAsUserW` failures (#10090, #13965), Computer Use enumeration errors (#37043, #37484), and VS Code extension loading issues (#37458).
*   **macOS Memory & Crash Regressions**: Critical OOM crashes on macOS, particularly related to external agent imports parsing massive files (#36523) and specific memory limits on lower-RAM Apple Silicon machines (#37493).
*   **Context & Routing Logic**: Users are experiencing broken context awareness in long conversations (#8648) and version-specific regressions in Azure/LiteLLM streaming paths (#37380, #37425).
*   **Linux Sandbox Fragmentation**: Inconsistencies in Bubblewrap and sandbox configurations are causing `apply_patch` failures across different Ubuntu and kernel versions (#29908).

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-08-08

## 1. Today's Highlights
The v0.56.0-nightly release addresses critical model capacity exhaustion false positives and updates the Firestore schema for improved error tracking. Community attention is heavily focused on subagent reliability, with persistent bugs regarding `MAX_TURNS` termination logic and generalist agent hangs.

## 2. Releases
**v0.56.0-nightly.20260808** ([PR #28732](https://github.com/google-gemini/gemini-cli/pull/28732))
Key changes include reclassifying capacity exhaustion as a terminal error to prevent infinite retry loops and updating the Caretaker Firestore schema with `error` and `pr_number` fields for better observability.

## 3. Hot Issues
1. **[BUG] Subagent recovery after MAX_TURNS reported as GOAL success** [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — *P1, 12 comments, 2 👍*
   Critical bug where the `codebase_investigator` subagent falsely reports success despite hitting turn limits, masking interruptions.
2. **[BUG] Generalist agent hangs** [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — *P1, 8 comments, 8 👍*
   The generalist agent freezes indefinitely on simple tasks; disabling subagents is the current workaround.
3. **[FEATURE] Leverage model's bash affinity via Zero-Dependency OS Sandboxing** [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) — *P2, 8 comments*
   Proposal to use native bash tools (`grep`, `sed`) for codebase exploration to align with model training and improve security.
4. **[EPIC] Robust component level evaluations** [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) — *P1, 7 comments*
   Follow-up to behavioral evals, tracking the expansion of the 76 existing eval tests across supported Gemini models.
5. **[EPIC] Assess impact of AST-aware file reads and search** [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — *P2, 7 comments*
   Investigation into AST-aware tools to reduce turn waste and improve codebase mapping precision.
6. **[BUG] Gemini does not use skills and sub-agents enough** [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — *P2, 6 comments*
   Anecdotal but widespread report that custom skills (e.g., Gradle, Git) are ignored unless explicitly prompted.
7. **[BUG] Stop Auto Memory from retrying low-signal sessions indefinitely** [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — *P2, 5 comments*
   Auto Memory retries sessions the extraction agent dismisses as low-signal, causing inefficient looping.
8. **[BUG] Shell command stuck with "Waiting input"** [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — *P1, 4 comments, 3 👍*
   Simple CLI commands complete but the shell remains in an active "Awaiting user input" state.
9. **[BUG] Browser Agent ignores settings.json overrides** [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) — *P2, 3 comments*
   Configuration overrides like `maxTurns` in `settings.json` are ignored by the Browser Agent.
10. **[BUG] Gemini CLI gets stuck at interactive prompt creating vite app** [#22465](https://github.com/google-gemini/gemini-cli/issues/22465) — *P2, 2 comments*
    The agent fails to handle interactive prompts during Vite app creation, requiring a behavioral eval update.

## 4. Key PR Progress
1. **[FIX] Resolve false model capacity exhaustion** [#28730](https://github.com/google-gemini/gemini-cli/pull/28730)
   Fixes false positives in quota lookup mapping and preserves the "Keep trying" UI option during transient surges.
2. **[FEAT] Add Gemini 3.6 Flash and 3.5 Flash-Lite configs** [#28673](https://github.com/google-gemini/gemini-cli/pull/28673)
   Adds model resolution and capability definitions for newer Flash variants in the core package.
3. **[FEAT] Issue comment handling and re-triage workflow** [#28690](https://github.com/google-gemini/gemini-cli/pull/28690)
   Enables the Caretaker Agent to process `issue_comment.created` webhooks and trigger re-triage via mentions.
4. **[FIX] Load env vars before resolving settings placeholders** [#28597](https://github.com/google-gemini/gemini-cli/pull/28597)
   Resolves a load-order race condition where `.env` variables were unavailable during settings parsing.
5. **[FIX] Resolve swallowed directory mismatch in IDE connections** [#28729](https://github.com/google-gemini/gemini-cli/pull/28729)
   Fixes connectivity issues with VS Code forks and remote workspaces using virtual/FUSE paths.
6. **[FIX] Skip diff hunk markers during @ processing** [#28581](https://github.com/google-gemini/gemini-cli/pull/28581)
   Prevents heap growth from recursive glob searches when parsing unified diff markers.
7. **[SECURITY] Prevent SSRF via DNS resolution bypass in web-fetch** [#28725](https://github.com/google-gemini/gemini-cli/pull/28725)
   Patches a critical SSRF vulnerability (CVSS 8.6) allowing access to private IPs via custom domains.
8. **[FEAT] Add Cloud Run job entrypoint for eval runner** [#28727](https://github.com/google-gemini/gemini-cli/pull/28727)
   Adds infrastructure for executing the Caretaker Triage Evaluation Suite on Google Cloud Run.
9. **[FEAT] GCP deployment script for caretaker services** [#28529](https://github.com/google-gemini/gemini-cli/pull/28529)
   Automates deployment of Ingestion, Triage Worker, and Egress services to Cloud Run.
10. **[FEAT] Local evaluation report command** [#28369](https://github.com/google-gemini/gemini-cli/pull/28369)
    Adds `npm run eval:report` to aggregate pass rates and map results to inventory policies.

## 5. Feature Request Trends
*   **AST-Aware Tooling:** Strong interest in using ASTs for precise codebase mapping and method-bound reading to reduce token waste and turns ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)).
*   **Zero-Dependency Sandboxing:** Requests to leverage native bash affinity for safer, faster codebase exploration without external dependencies ([#19873](https://github.com/google-gemini/gemini-cli/issues/19873)).
*   **Subagent Visibility:** Demand for better visibility into subagent trajectories via `/chat share` and improved bug reporting context ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598), [#21763](https://github.com/google-gemini/gemini-cli/issues/21763)).
*   **Eval Infrastructure:** Continued investment in behavioral evals, including automated triage evaluation frameworks and cloud-based runners ([#24353](https://github.com/google-gemini/gemini-cli/issues/24353), [#28727](https://github.com/google-gemini/gemini-cli/pull/28727)).

## 6. Developer Pain Points
*   **Subagent Reliability:** Persistent issues with subagents hanging, ignoring configuration overrides, or misreporting termination status are the top frustration ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409), [#22267](https://github.com/google-gemini/gemini-cli/issues/22267), [#22323](https://github.com/google-gemini/gemini-cli/issues/22323)).
*   **Capacity/Quota Errors:** False positive "capacity exhaustion" errors disrupt workflow, though recent patches aim to address this ([#28730](https://github.com/google-gemini/gemini-cli/pull/28730)).
*   **Interactive Prompt Handling:** The agent struggles with interactive CLI tools (e.g., Vite), getting stuck in loops or waiting states ([#22465](https://github.com/google-gemini/gemini-cli/issues/22465), [#25166](https://github.com/google-gemini/gemini-cli/issues/25166)).
*   **Auto Memory Inefficiency:** The memory system retries low-signal sessions indefinitely and lacks deterministic redaction, raising security and performance concerns ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525)).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-08-08

## 1. Today's Highlights
The Copilot CLI team shipped three micro-updates (v1.0.79-7 through v1.0.79-9) focusing on enhanced enterprise sandbox policy enforcement, improved `/sandbox` configuration UX, and Agent Plugin extensibility. Concurrently, the community flagged significant regressions in Windows terminal rendering and authentication flows, alongside critical bugs involving sub-agent dispatch failures on Claude models and orphaned MCP processes.

## 2. Releases
**v1.0.79-7, v1.0.79-8, v1.0.79-9**
*   **Enterprise Sandbox Enhancements:** Added support for `allow-auto-only` policies, allowing `/allow-all auto` to function while blocking full allow-all. Enterprise-managed sandboxes can now enforce proxy URLs while keeping credentials user-controlled.
*   **Agent Plugins:** Plugins can now ship extensions under a `com.github.copilot/extensions/` directory.
*   **Model Support:** Added support for the `kimi-k3` model.
*   **Autopilot Improvements:** Users can now combine `--plan` with `--mode autopilot` to plan first and implement without waiting for approval.
*   **UX Polish:** The `/sandbox` configuration dialog now clearly indicates where settings are stored in `settings.json` and groups git/gh settings better.

## 3. Hot Issues
*   **[OPEN] #2494 - `copilot login` auto-enters keychain prompt (Regression)**
    *   *Why it matters:* After upgrading to v1.0.16, the CLI auto-accepts the System Keychain prompt without waiting for input, breaking authentication workflows when the keychain is unavailable.
    *   *Community:* 11 comments, 1 reaction.
*   **[OPEN] #1632 - Support subfolders for skills**
    *   *Why it matters:* Users with extensive skill libraries lack organizational structure. This feature request proposes nested directories for better skill management.
    *   *Community:* 10 comments, 23 reactions (highly upvoted).
*   **[OPEN] #3622 - Copy to clipboard silently fails on Windows**
    *   *Why it matters:* A regression in Windows where copied agent output reverts to previous clipboard contents, disrupting workflow continuity.
    *   *Community:* 5 comments, 4 reactions.
*   **[OPEN] #4311 - Transcript renders as blank lines until terminal width changes**
    *   *Why it matters:* A terminal rendering bug in interactive mode causes content to disappear (blanks out) until a resize or new submission occurs. `/resume` also fails to recover it.
    *   *Community:* 3 comments.
*   **[CLOSED] #4345 - Reasoning effort 'medium' unsupported for claude-haiku-4.5**
    *   *Why it matters:* Conflicting feature flags caused sub-agent execution to fail with invalid reasoning effort errors for specific Claude models.
*   **[CLOSED] #4222 - Main pane freezes / infinite React render loop (Regression of #2802)**
    *   *Why it matters:* The infinite render loop bug from v1.0.31 has resurfaced in v1.0.72+, causing the UI to freeze and swallow output on Windows.
*   **[CLOSED] #4185 - `--add-dir` causes Claude sub-agent dispatch to fail**
    *   *Why it matters:* Launching with `--add-dir` triggers a 400 error on Anthropic models due to exceeding the maximum block limit with `cache_control`, breaking sub-agent workflows.
*   **[CLOSED] #4118 - `/app` command does not select current working directory**
    *   *Why it matters:* Users must manually select the directory when opening the Copilot app via `/app`, which is inconvenient compared to automatic detection.
    *   *Community:* 35 reactions.
*   **[CLOSED] #2947 - Enable token usage reporting in CLI**
    *   *Why it matters:* A feature request to track token consumption per session for cost monitoring, with significant community interest.
*   **[OPEN] #1409 - `add-dir` flag converts dashes to underscores in paths**
    *   *Why it matters:* Path canonicalization mismatches on Windows cause permission loops for OneDrive directories, preventing the agent from ever gaining access.

## 4. Key PR Progress
*No new pull requests were submitted or merged in the last 24 hours.*

## 5. Feature Request Trends
*   **Enterprise Policy Granularity:** Strong demand for more nuanced control over sandbox policies (allow-auto-only, proxy enforcement) to accommodate corporate security requirements.
*   **Skill Organization:** Requests for hierarchical skill management (subfolders) to handle growing collections of custom skills.
*   **Cost Transparency:** Continued interest in built-in token usage tracking for session cost analysis.
*   **UX Efficiency:** Requests for better default behaviors, such as `/app` respecting the current working directory and restoring quick-delete actions in the sessions view.
*   **Multi-Model Support:** Adoption of new models like `kimi-k3` and improved integration with reasoning-effort settings across different model families.

## 6. Developer Pain Points
*   **Windows Stability:** A recurring theme of Windows-specific regressions, including clipboard failures (#3622), terminal rendering freezes (#4222, #4311), and notification crashes (#4219).
*   **Authentication Fragility:** Issues with login flows, including keychain prompt bypasses (#2494), browser URL wrapping bugs (#4400), and false-positive MCP status on login failure (#1129).
*   **Sub-Agent Reliability:** Several bugs affecting sub-agent execution, particularly when using `--add-dir` with Claude models (#4185) or encountering unsupported reasoning efforts (#4345).
*   **MCP Process Leaks:** Orphaned stdio MCP server processes persisting after authentication rebuils (#4392), leading to resource leaks and potential conflicts.
*   **Permission & Path Handling:** Issues with path canonicalization causing permission loops (#1409) and settings configurations not loading correctly (#4398).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest – 2026-08-08

## 1. Today's Highlights
No new releases were published in the last 24 hours. Community attention is focused on two critical stability concerns: a severe safety bug where the agent executed `rm -rf` outside the workspace (Issue #2596), and a data-corruption issue in `StrReplaceFile` that silently alters non-UTF-8 files (PRs #2594, #2595). Additionally, the long-standing request for persistent cross-session memory continues to gather discussion (Issue #1283).

## 2. Releases
*No new releases in the last 24 hours.*

## 3. Hot Issues
1. **[CRITICAL] Agent ran rm -rf on a pre-existing directory outside the workspace** (#2596)
   - **Why it matters:** A high-severity safety failure where the agent, operating in `yolo` permission mode, deleted user session data at `~/.pi/agent/sessions` due to a symlink handling error. This highlights dangerous gaps in boundary enforcement for destructive commands.
   - **Community reaction:** Immediate concern over safety guarantees; 0 comments so far, likely due to the recency (created 2026-08-07).
   - [Link](https://github.com/MoonshotAI/kimi-cli/issues/2596)

2. **Feature Request: Memory System - Persistent context across sessions** (#1283)
   - **Why it matters:** Users increasingly demand continuity, wanting the CLI to remember project patterns and preferences without re-prompting. This is a foundational feature for long-running complex workflows.
   - **Community reaction:** Strong sustained interest with 21 comments since February 2026, indicating a clear gap in current capabilities.
   - [Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)

*(Note: Only 2 issues were updated in the last 24h. No further issues are listed for inclusion.)*

## 4. Key PR Progress
1. **fix(tools): preserve non-UTF-8 bytes in StrReplaceFile edits** (#2594)
   - **Description:** Addresses a data corruption bug where `StrReplaceFile` decoded entire files with `errors="replace"`, converting invalid UTF-8 sequences into `U+FFFD` (replacement character) even when those bytes were far from the edit site. This PR applies edits as raw byte substrings to preserve file integrity.
   - **Status:** Open, updated 2026-08-07.
   - [Link](https://github.com/MoonshotAI/kimi-cli/pull/2594)

2. **fix(StrReplaceFile): refuse to edit files that are not valid UTF-8** (#2595)
   - **Description:** An alternative or complementary fix to #2594, proposing to reject editing of non-UTF-8 files entirely rather than attempting byte-level manipulation, referencing Issue #2591.
   - **Status:** Open, updated 2026-08-07.
   - [Link](https://github.com/MoonshotAI/kimi-cli/pull/2595)

*(Note: Only 2 PRs were updated in the last 24h. No further PRs are listed for inclusion.)*

## 5. Feature Request Trends
- **Persistent Memory & Context:** The dominant long-term trend is the desire for statefulness across sessions (Issue #1283). Users want the CLI to retain knowledge of project structures, coding conventions, and user preferences to reduce repetitive setup.
- **Safety & Boundary Enforcement:** While not always a "feature request" in the traditional sense, the recent critical bug (#2596) signals a strong community need for stricter, more reliable safeguards against out-of-scope destructive operations, especially in permissive modes.

## 6. Developer Pain Points
- **Data Corruption in File Edits:** The `StrReplaceFile` tool's handling of non-UTF-8 bytes is a recurring source of silent data corruption. Developers are frustrated by the lack of robustness when working with binary files or non-standard encodings.
- **Security Boundaries in Agentic Modes:** The `yolo` permission mode poses significant risks. The incident where `rm -rf` was executed outside the workspace due to symlink confusion highlights a critical pain point: permissive modes currently lack sufficient guardrails for real-world directory structures.
- **Lack of Session Continuity:** Developers find it cumbersome to re-establish context for each new CLI session, driving the persistent interest in a memory system.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest | 2026-08-08

## 1. Today's Highlights
OpenCode v1.18.15 has been released with critical bug fixes for message chronology and session cleanup. The community is actively discussing a significant upstream 401 blocking issue affecting Go subscribers, alongside ongoing concerns about heavy git usage in large repositories.

## 2. Releases
**v1.18.15**
- **Bugfix:** Chronological message ordering is now preserved correctly even when imported or legacy message IDs are out of order.
- **Bugfix:** Revert and fork actions now rely on real message chronology rather than ID ordering.
- **Bugfix:** Truncation cleanup more reliably removes stale files based on file timestamps.

## 3. Hot Issues
1. **[Bug] OpenCode Go: 401 Request blocked by upstream provider** [#38257](https://github.com/anomalyco/opencode/issues/38257)
   - **Why it matters:** All models under the Go subscription are returning 401 errors on `chat/completions` since July 22, while `/v1/models` works. This indicates a critical provider-side or authentication issue affecting paid users.
   - **Reaction:** 45 comments, 11 👍. High urgency due to service disruption.

2. **Why is OpenCode massively abusing git?** [#3176](https://github.com/anomalyco/opencode/issues/3176)
   - **Why it matters:** OpenCode performs `git add .` on large directories (e.g., 45GB/54K files), causing severe performance degradation. This is a fundamental design flaw impacting large-scale projects.
   - **Reaction:** 18 comments, 10 👍. Recurring frustration about session snapshot mechanics.

3. **Unable to read images for some models** [#5359](https://github.com/anomalyco/opencode/issues/5359)
   - **Why it matters:** Regression from v1.0.134 to v1.0.137+ breaks image input when using LiteLLM + Vertex AI backend.
   - **Reaction:** 18 comments. Direct impact on multimodal workflows.

4. **[FEATURE]: Pay Go with crypto** [#23153](https://github.com/anomalyco/opencode/issues/23153)
   - **Why it matters:** Community request for cryptocurrency payment options for OpenCode Go subscriptions.
   - **Reaction:** 17 comments, 37 👍. Strong community support for alternative payment methods.

5. **Amazon Bedrock Opus 4.6 compaction failure** [#14332](https://github.com/anomalyco/opencode/issues/14332)
   - **Why it matters:** Bedrock returns errors when `thinking` or `redacted_thinking` blocks are modified during compaction. Highlights incompatibility with Anthropic's thinking mode in certain environments.
   - **Reaction:** 16 comments, 8 👍. Critical for users leveraging Amazon Bedrock.

6. **Error from provider (DeepSeek): reasoning_content in thinking mode** [#24334](https://github.com/anomalyco/opencode/issues/24334)
   - **Why it matters:** DeepSeek API requires `reasoning_content` to be passed back in thinking mode. OpenCode currently fails this requirement.
   - **Reaction:** 10 comments, 2 👍. Necessary fix for DeepSeek integration.

7. **Error: Unexpected server error** [#29748](https://github.com/anomalyco/opencode/issues/29748)
   - **Why it matters:** Persistent server error after adding OpenRouter API and switching projects, indicating potential state corruption or proxy configuration issues.
   - **Reaction:** 7 comments. Impacts multi-provider setups.

8. **Web UI does not list sessions and cannot start agent** [#40809](https://github.com/anomalyco/opencode/issues/40809)
   - **Why it matters:** Web UI fails to load sessions or start agents in Docker/Coolify environments despite TUI and mobile working. Points to web-specific session management bugs.
   - **Reaction:** 4 comments. Affects self-hosted web deployments.

9. **OpenCode keeps reopening deleted project path** [#31401](https://github.com/anomalyco/opencode/issues/31401)
   - **Why it matters:** Desktop app persists deleted project paths in workspace files, causing automatic re-opening of removed projects.
   - **Reaction:** 3 comments. UX issue on Windows 11.

10. **Excessive storage: event table stores full message snapshots** [#41175](https://github.com/anomalyco/opencode/issues/41175)
    - **Why it matters:** `opencode.db` grows to gigabytes because the event table stores complete message copies on every streaming update, not deltas.
    - **Reaction:** 1 comment. Critical for long-term storage efficiency.

## 4. Key PR Progress
1. **[contributor] feat(server): run modal sandboxes on the vm runtime** [#41177](https://github.com/anomalyco/opencode/pull/41177)
   - **Description:** Switches Modal sandboxes to use Full-VM runtime (beta) instead of gVisor containers, ensuring a real kernel (6.12.8) for better compatibility.

2. **[contributor] fix(merman): support undirected edges and place multiline state labels** [#41171](https://github.com/anomalyco/opencode/pull/41171)
   - **Description:** Fixes Mermaid diagram rendering to support undirected flowchart edges (`S1 --- X`) and multiline emoji labels without corruption.

3. **[contributor] refactor(core): remove legacy account subsystem** [#41173](https://github.com/anomalyco/opencode/pull/41173)
   - **Description:** Removes dead V2 Core Account schema and deletes orphaned SQLite tables (`account`, `account_state`, `control_account`). Authentication now relies on `credential`.

4. **feat: native background subagents + auto-continue for transient provider errors** [#40923](https://github.com/anomalyco/opencode/pull/40923)
   - **Description:** Introduces native background sub-agent orchestration (`Task(background=true)`) and automatic recovery for transient provider errors.

5. **docs(opencode): improve global-event-api documentation** [#41157](https://github.com/anomalyco/opencode/pull/41157)
   - **Description:** Comprehensive update to `docs/global-event-api.md` with comparison tables for `/global/event` vs `/api/event` covering envelope format, heartbeat, and backpressure.

6. **fix(lsp): match wildcard root markers like *.cabal** [#41169](https://github.com/anomalyco/opencode/pull/41169)
   - **Description:** Fixes LSP root marker detection to include wildcard patterns (e.g., `*.cabal`) during directory tree walks.

7. **fix(app): populate project picker from home** [#41158](https://github.com/anomalyco/opencode/pull/41158)
   - **Description:** Ensures the project picker in the web UI falls back to listing the current home directory when empty search returns no results, fixing the "Nothing here yet" issue.

8. **[contributor] feat(tui): render Mermaid diagrams** [#41113](https://github.com/anomalyco/opencode/pull/41113)
   - **Description:** Adds built-in TUI support for rendering fenced Mermaid flowcharts, sequence diagrams, and state diagrams directly in session transcripts.

9. **fix(session): extract tool-result media for models without attachment capability** [#41161](https://github.com/anomalyco/opencode/pull/41161)
   - **Description:** Corrects `supportsMediaInToolResult` to properly handle media extraction for models that do not support direct attachments.

10. **fix(provider): propagate config-level npm override to inherited models** [#41159](https://github.com/anomalyco/opencode/pull/41159)
    - **Description:** Fixes bug where config-level `npm` overrides for providers (e.g., `@ai-sdk/anthropic`) were silently dropped for inherited models.

## 5. Feature Request Trends
- **Payment Flexibility:** Strong demand for cryptocurrency payments for Go subscriptions (Issue #23153).
- **Background Task Orchestration:** Requests for native background subagents and queuing user messages during generation (PR #40923, Issue #41106).
- **Skills Organization:** Feature request to support subfolders for skills to improve organization (Issue #38853).
- **Environment Control:** Request for `OPENCODE_DISABLE_INSTALL` env var to skip npm installs in Docker/CI environments (Issue #37888).

## 6. Developer Pain Points
- **Performance Overhead:** Excessive git usage (`git add .`) on large directories causes significant slowdowns (Issue #3176).
- **Database Bloat:** The event table storing full message snapshots per streaming update leads to massive `opencode.db` growth (Issue #41175).
- **Web UI Session Management:** Fresh web sessions show "Nothing here yet" and fail to list server projects due to client-side bookmark reliance (Issues #41156, #41155).
- **Provider Compatibility:** Issues with Anthropic models via LLM proxies (Issue #40797), DeepSeek thinking mode requirements (Issue #24334), and Bedrock compaction errors (Issue #14332).
- **Image Input Regression:** Breakage in image reading capabilities for certain models after version updates (Issue #5359).

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-08-08

## 1. Today's Highlights
Pi **v0.84.1** introduces support for Qwen "Individual" subscription models and authentication readiness checks, expanding provider flexibility. The community is actively resolving critical session management bugs, particularly around compaction triggers and parallel tool execution state, while a major new integration bridge for Cursor CLI has been merged.

## 2. Releases
*   **v0.84.1**: Added support for Qwen Token Plan Individual models via the built-in provider. Implemented `pi auth` readiness checks to verify provider authentication status before session initiation.
    *   [View Release](https://github.com/badlogic/pi-mono/releases/tag/v0.84.1)

## 3. Hot Issues
*   **#6879** [OPEN] **Auto-compaction failure after 100% context growth** — Compaction fails to trigger automatically when context exceeds 100% of the window, only resetting after an API rejection (373k tokens). 15 👍, 13 comments.
    *   [View Issue](https://github.com/earendil-works/pi/issues/6879)
*   **#7128** [OPEN] **System prompt guideline over-encourages bash calls** — A default guideline to inspect `PI_*` env vars biases agents into unnecessary shell execution. 7 👍, 11 comments.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7128)
*   **#7020** [CLOSED] **Pi doesn't continue after compaction** — Long-running "coordinator" sessions frequently stall post-compaction, indicating lifecycle warts in extended sessions.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7020)
*   **#5886** [OPEN] **AgentSession settlement/continuation bugs** — A meta-issue tracking recurring failures where post-run logic attempts to continue from a stale transcript.
    *   [View Issue](https://github.com/earendil-works/pi/issues/5886)
*   **#7730** [OPEN] **High CPU usage on macOS** — Users report CPU swinging 50-110% during long sessions, linked to context size growth.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7730)
*   **#7053** [OPEN] **Parallel tool batches lose results** — If one sibling tool stalls, completed results from other tools in the same batch are dropped ("No result provided").
    *   [View Issue](https://github.com/earendil-works/pi/issues/7053)
*   **#7771** [CLOSED] **Unable to start v0.84.1 on Node 23** — Crash due to `zlib.createZstdDecompress` not being a function, indicating a Node version compatibility issue.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7771)
*   **#7703** [CLOSED] **Agent.reset() leaves assistant-only transcript** — Calling reset during an active run clears state but leaves the active run unsettled, corrupting the transcript.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7703)
*   **#7709** [CLOSED] **OpenAI Responses drops `namespace` on deferred function calls** — Multi-turn tool calls fail with "Missing namespace" errors on OpenAI Responses models.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7709)
*   **#7740** [OPEN] **TUI ignores custom tool renderers after /reload** — Tools registered via `session_start` lose their custom `renderCall`/`renderResult` handlers after a reload command.
    *   [View Issue](https://github.com/earendil-works/pi/issues/7740)

## 4. Key PR Progress
*   **#7792** [CLOSED] **Bridge Cursor CLI auth via local agent session** — Adds a hidden `cursor-agent` extension allowing Pi to use existing Cursor CLI auth without extra API keys.
    *   [View PR](https://github.com/earendil-works/pi/pull/7792)
*   **#7749** [CLOSED] **Preserve custom tool renderers after reload** — Fixes the bug where `/reload` drops custom renderers for tools registered during `session_start`.
    *   [View PR](https://github.com/earendil-works/pi/pull/7749)
*   **#7710** [CLOSED] **Restore suspended harness operations** — Implements recovery logic to load a new harness from a session with existing live operations (Harness v2 plan R3).
    *   [View PR](https://github.com/earendil-works/pi/pull/7710)
*   **#7795** [CLOSED] **Use `command -v` instead of `which`** — Replaces external `which` binary with shell builtin for better compatibility in minimal/sandbox environments.
    *   [View PR](https://github.com/earendil-works/pi/pull/7795)
*   **#7784** [OPEN] **Derive recovery state from record queries** — Refactors agent recovery to remove specific query APIs (`findOpenOperations`) in favor of bounded record queries.
    *   [View PR](https://github.com/earendil-works/pi/pull/7784)
*   **#7801** [OPEN] **Lazily load uncommon syntax grammars** — Experimental refactoring to improve startup/performance by loading syntax highlighting grammars on demand.
    *   [View PR](https://github.com/earendil-works/pi/pull/7801)
*   **#7780** [CLOSED] **TUI performance improvement** — Implements incremental markdown parsing and lazy render invalidation to reduce CPU load.
    *   [View PR](https://github.com/earendil-works/pi/pull/7780)
*   **#7762** [OPEN] **Introduce LM Studio provider** — Adds a new provider for local LM Studio instances.
    *   [View PR](https://github.com/earendil-works/pi/pull/7762)
*   **#7722** [OPEN] **Add `--use-theme` override** — Allows overriding the current theme selection for a single `pi` run via CLI flag.
    *   [View PR](https://github.com/earendil-works/pi/pull/7722)
*   **#7788** [CLOSED] **Render tool errors via `context.isError`** — Fixes the built-in tool renderer to correctly detect errors by checking `isError` rather than string-matching "Error" in text.
    *   [View PR](https://github.com/earendil-works/pi/pull/7788)

## 5. Feature Request Trends
*   **Cross-Tool Compatibility**: Strong demand for portability standards, evidenced by the merge of Agent Plugins support (#7776) and the Cursor CLI bridge (#7792).
*   **Local/Offline-First**: Continued interest in local providers (LM Studio #7762) and handling local auth flows without cloud credentials.
*   **TUI/UX Polish**: Requests for better fullscreen controls, sticky headers for prompts (#7802), and improved copy-on-select behavior (#7757).

## 6. Developer Pain Points
*   **Session Lifecycle & Compaction**: The most significant friction point. Users report that compaction is unreliable in long-running or parallel tool sessions (#6879, #7020, #5886), leading to context overflow and stalled agents.
*   **Provider Compatibility Nuances**: Frequent issues with specific model quirks (DeepSeek reasoning content #7702, OpenAI namespace #7709, Baseten token limits #7726) require constant patching of provider adapters.
*   **State Management on Reload**: Extensions and custom tools frequently lose state or render bindings when the user reloads the session (#7740, #7749), suggesting a fragility in the hot-reload mechanism for dynamic plugins.
*   **Resource Leaks**: High CPU usage on macOS (#7730) and memory concerns during long sessions indicate ongoing optimization challenges in the core agent loop.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-08-08

## 1. Today's Highlights

Qwen Code v0.21.7-nightly is now available, bringing CI fixes for autofix admission and documented sub-session concurrency. The community is actively addressing critical UX regressions, including a Windows installer crash, TMUX flickering over SSH, and silent failures in MCP server discovery.

## 2. Releases

**v0.21.7-nightly.20260808.4ec0371e**
*   **CI Fix:** Surfaces blocked autofix takeover admission, improving visibility into CI pipeline interruptions. ([PR #8410](https://github.com/QwenLM/qwen-code/pull/8410))
*   **Documentation:** Added documentation for the `serve` sub-session concurrency model.

## 3. Hot Issues

1.  **[Windows Installer Crash] EISDIR lstat 'C:'** [#8615](https://github.com/QwenLM/qwen-code/issues/8615)
    *   **Why it matters:** The v0.1.0 Desktop installer fails immediately upon opening a workspace on Windows 11, blocking a significant portion of desktop users.
2.  **[CLI Regression] Middle-mouse selection broken in PuTTY** [#8672](https://github.com/QwenLM/qwen-code/issues/8672)
    *   **Why it matters:** A regression in v0.21.1 broke xterm-style middle-click paste, a critical workflow for SSH users.
3.  **[UI/Terminal] TMUX screen flickering on macOS/Ubuntu SSH** [#8562](https://github.com/QwenLM/qwen-code/issues/8562)
    *   **Why it matters:** Users report persistent visual tearing in nested TMUX sessions, attributed to recent version updates.
4.  **[Desktop UI] Markdown links unclickable** [#8593](https://github.com/QwenLM/qwen-code/issues/8593)
    *   **Why it matters:** Links in assistant messages are styled but silent, creating a broken user experience in the desktop app.
5.  **[MCP] `qwen mcp list` hangs indefinitely** [#8550](https://github.com/QwenLM/qwen-code/issues/8550)
    *   **Why it matters:** Slow or unresponsive SSE servers can freeze the CLI indefinitely due to missing timeouts.
6.  **[Windows IME] Chinese Pinyin input unreadable** [#8625](https://github.com/QwenLM/qwen-code/issues/8625)
    *   **Why it matters:** Rendering issues with CJK input candidates in the Windows terminal hinder non-English users.
7.  **[Core] Wrapped timeout errors drop retry metadata** [#8527](https://github.com/QwenLM/qwen-code/issues/8527)
    *   **Why it matters:** Timeout errors are incorrectly surfaced as permanent failures instead of hitting the transport-retry path.
8.  **[Core] Signal-terminated shell commands report success** [#8491](https://github.com/QwenLM/qwen-code/issues/8491)
    *   **Why it matters:** A logic bug allows killed processes to be reported as successful, potentially causing unsafe state in automated workflows.
9.  **[MCP] Hot reload leaves stale session registrations** [#8492](https://github.com/QwenLM/qwen-code/issues/8492)
    *   **Why it matters:** Changing MCP metadata (e.g., trust settings) without changing the transport URL does not reapply the new configuration.
10. **[UI] Queued message indicator disappears during long turns** [#8666](https://github.com/QwenLM/qwen-code/issues/8666)
    *   **Why it matters:** Users cannot tell if a Ctrl+Q queued message was accepted during long agent busy states.

## 4. Key PR Progress

1.  **[Web-Shell] Install Extensions from archives** [#8621](https://github.com/QwenLM/qwen-code/pull/8621)
    *   Adds support for uploading and installing local `.zip` or `.tar.gz` extension packages via the daemon.
2.  **[Core] Checkpoint long-running Goal evidence** [#8465](https://github.com/QwenLM/qwen-code/pull/8465)
    *   Introduces durable evidence compression for long-running goals to prevent bounded catalog limits from halting progress.
3.  **[Daemon] Batch Skill Toggle API** [#8664](https://github.com/QwenLM/qwen-code/pull/8664)
    *   Enables enabling/disabling up to 100 skills in a single request via the daemon HTTP API.
4.  **[CLI] Prefer `wl-copy` on Wayland** [#8481](https://github.com/QwenLM/qwen-code/pull/8481)
    *   Improves Linux Wayland compatibility by prioritizing native clipboard tools over X11 fallbacks.
5.  **[Integration] Qoder Plugin Compatibility** [#8661](https://github.com/QwenLM/qwen-code/pull/8661)
    *   Adds a compatibility layer to install and run Qoder plugins (extensions, agents, skills) within Qwen Code.
6.  **[Core] Reasoning Effort via ACP** [#8526](https://github.com/QwenLM/qwen-code/pull/8526)
    *   Exposes standard `thought_level` options (Low, Medium, High, etc.) to ACP clients like JetBrains.
7.  **[Web-Shell] Model-Specific Reasoning Controls** [#8675](https://github.com/QwenLM/qwen-code/pull/8675)
    *   Implements a registry for model-specific thinking/effort controls across Core, ACP, and WebShell.
8.  **[Daemon] Pollable Turn-Status Endpoints** [#8682](https://github.com/QwenLM/qwen-code/pull/8682)
    *   Adds `GET /session/:id/turns/:promptId` and `current` endpoints for external status polling.
9.  **[Core] Fix Qwen 3.8 Reasoning Budget Conflicts** [#8525](https://github.com/QwenLM/qwen-code/pull/8525)
    *   Resolves conflicts where both `reasoning_effort` and `thinking_budget` were sent simultaneously.
10. **[Core] Git Cross-Worktree Mutation Guard** [#8687](https://github.com/QwenLM/qwen-code/pull/8687)
    *   Blocks shell commands that attempt to mutate Git repositories outside the session's authorized worktree.

## 5. Feature Request Trends

*   **Desktop & Mobile Access:** Strong demand for a "Local Control" mode with QR-code pairing for mobile access to local sessions ([#8595](https://github.com/QwenLM/qwen-code/issues/8595)) and a lower-maintenance desktop app built on Web Shell ([#8092](https://github.com/QwenLM/qwen-code/issues/8092)).
*   **Browser Automation:** Proposal for "Qwen WebBridge" to enable direct browser control similar to Kimi WebBridge ([#8699](https://github.com/QwenLM/qwen-code/issues/8699)).
*   **Integration Enrichment:** Requests to enrich Feishu/DingTalk interactions with async contact labeling and native "ask-user" question cards ([#8566](https://github.com/QwenLM/qwen-code/issues/8566), [#8515](https://github.com/QwenLM/qwen-code/issues/8515)).
*   **Telemetry & Attribution:** Desire for stable runtime/client attribution in usage telemetry and OpenTelemetry lifecycle alignment ([#8660](https://github.com/QwenLM/qwen-code/issues/8660), [#8616](https://github.com/QwenLM/qwen-code/pull/8616)).

## 6. Developer Pain Points

*   **Input Method & Terminal Rendering:** Recurring issues with CJK input rendering on Windows ([#8625](https://github.com/QwenLM/qwen-code/issues/8625)) and TUI flickering in web-based or nested TMUX terminals ([#8562](https://github.com/QwenLM/qwen-code/issues/8562), [#8659](https://github.com/QwenLM/qwen-code/issues/8659)).
*   **Platform-Specific Regressions:** High friction on Windows (installer crashes [#8615](https://github.com/QwenLM/qwen-code/issues/8615), PowerShell hash resolution [#7118](https://github.com/QwenLM/qwen-code/issues/7118)) and Linux/SSH (middle-click paste regression [#8672](https://github.com/QwenLM/qwen-code/issues/8672)).
*   **MCP & Tool Reliability:** Users are frustrated by hanging MCP lists [#8550](https://github.com/QwenLM/qwen-code/issues/8550) and stale session states after hot-reloads [#8492](https://github.com/QwenLM/qwen-code/issues/8492).
*   **Error Handling Visibility:** Timeout errors and signal-terminated processes are incorrectly reported as successes or permanent failures, obscuring the true state of agent operations [#8527](https://github.com/QwenLM/qwen-code/issues/8527), [#8491](https://github.com/QwenLM/qwen-code/issues/8491).

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest
**Date:** 2026-08-08  
**Repository:** Hmbown/DeepSeek-TUI (CodeWhale)

## 1. Today's Highlights
The v0.9.4 release process has been actively unblocked by clearing four CI blockers, though the artifact has not yet been published. Significant bug fixes landed in subagent shared-workspace permissions and session title caching, while new features for model tier selection and MCP registry sync are in review.

## 2. Releases
**Status:** No new published releases in the last 24 hours.
The team is currently focused on clearing the final CI blockers for v0.9.4 (PR #5282). The codebase on `main` is already versioned at 0.9.4, but the release pipeline is awaiting green CI runs.

## 3. Hot Issues
1.  **[#2934] Sidebar sessions panel with auto-resume** [CLOSED]  
    Adds persistent session history browsing to resolve friction in switching contexts. High engagement (13 comments) indicates strong user demand for better state management.
2.  **[#1425] Session hang during large text processing** [OPEN]  
    Users report `agent_wait` timeouts causing deadlocks when processing massive files (e.g., 3M+ word novels) via subagents. Highlights reliability gaps in heavy concurrent workloads.
3.  **[#4785] Dead-code sweep: 464 #[allow(dead_code)]** [OPEN]  
    Maintainer flagging a structural health issue where 464 dead-code attributes prevent the compiler from detecting drift across 143 files. Critical for long-term Rust codebase hygiene.
4.  **[#5123] Agent spawn surface has too many knobs** [OPEN, Release-Blocker]  
    Fixes a v0.9.4 dogfood bug where labeled builder runs incorrectly self-block due to read-only tool contract mismatches.
5.  **[#3306] Refactor: converge runtime ownership** [OPEN]  
    Umbrella issue to reduce the 18-package, 771k-line monorepo complexity by consolidating parallel runtime, tool, and config paths in the TUI.
6.  **[#2492] Lack of cross-session memory** [OPEN]  
    Users report the tool forgets context between restarts, creating a fragmented experience despite fast response times.
7.  **[#5034] Switching providers retains unrelated default model** [OPEN, Release-Blocker]  
    A logical inconsistency where switching to OpenAI leaves the model set to `gpt-5.5` if it was inherited from a previous route, rather than resolving to the new provider's default.
8.  **[#790] Improve i18n coverage** [OPEN]  
    Follow-up to add Traditional Chinese support, noting many user-visible strings remain hardcoded in English.
9.  **[#4416] Isolate stale failed-agent state** [OPEN]  
    Bug where opening a second CodeWhale instance in the same workspace displays red failed-agent rows from a prior, unrelated session.
10. **[#3303] Editable and persistable config keys from TUI** [OPEN]  
    Users cannot discover or edit documented config knobs (e.g., subagent settings) directly in the UI, forcing manual `config.toml` edits.

## 4. Key PR Progress
1.  **[#5284] Fix: Stop counting finished children as shared-checkout contenders** [CLOSED]  
    Resolves a false-positive error where builder subagents were blocked from writing to the workspace because finished tasks were incorrectly counted as contention.
2.  **[#5282] Fix: Clear the four CI blockers holding v0.9.4** [CLOSED]  
    Addresses the red lane in CI that was preventing the v0.9.4 release despite the code being ready.
3.  **[#5283] Docs: Lead with mixed fleets** [CLOSED]  
    Updates README to clarify that "any model, any provider" supports persistent role-based configurations, not just mid-task switching.
4.  **[#5279] Chore: Bump clap from 4.5.54 to 4.6.1** [OPEN]  
    Dependabot update for the CLI argument parser.
5.  **[#5276] Chore: Bump serde_json from 1.0.149 to 1.0.151** [OPEN]  
    Updates JSON serialization library, adding `RawValue` features.
6.  **[#5258] Fix: Stop stale cached session title from pinning New Session** [OPEN]  
    Corrects a bug where session titles remained "New Session" indefinitely because the in-memory cache was not refreshed until the end of a snapshot.
7.  **[#5256] Feat: Background incremental registry sync** [OPEN]  
    Optimizes MCP tool loading by serving from a fresh local cache immediately and downloading updates asynchronously in the background.
8.  **[#5257] Feat: Add `model = auto` for prompt-based tier selection** [OPEN]  
    Introduces automatic selection between `deepseek-v4-pro` (complex) and `deepseek-v4-flash` (simple) based on prompt analysis.
9.  **[#5254] Build fix for FreeBSD** [CLOSED]  
    Addresses compilation failure on FreeBSD due to missing `rquickjs` bindings.
10. **[#5252] Feat: Allow embedders to isolate runtime state roots** [CLOSED]  
    Adds `EngineConfig::subagent_state_root` for embedding hosts that require session-owned delegated-agent state isolation.

## 5. Feature Request Trends
*   **Session & State Persistence:** Strong community desire for cross-session memory (#2492) and persistent sidebar navigation (#2934) to reduce friction in long-running workflows.
*   **Configurability from UI:** Users want to manage complex runtime settings (subagents, providers) directly within the TUI rather than editing TOML files (#3303).
*   **Fleet Flexibility:** Interest in "mixed fleets" where different roles can use different providers/models simultaneously, with clear capability visibility (#5283, #5038).
*   **Automation & Tiering:** The new `model = auto` feature (#5257) reflects a trend toward intelligent, prompt-aware resource allocation between cost and performance.

## 6. Developer Pain Points
*   **Release Stability:** The v0.9.4 launch was delayed by CI/bug issues (shared-workspace write errors, stale state isolation), suggesting testing gaps in multi-session and subagent edge cases.
*   **Codebase Complexity:** With 771k lines and 18 packages, maintaining clear ownership of runtime, tool, and config paths is a significant burden (#3306).
*   **Security vs. Usability:** Tightening exec policies (deny rules) has introduced bypass vulnerabilities via shell metacharacters (#5161), requiring careful balance between security and agent functionality.
*   **Credential Management:** Inconsistent user expectations around credential precedence (config vs. env vs. secret store) and misleading save confirmations (#5197, #5195) create friction during setup.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*