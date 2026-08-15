# AI CLI Tools Community Digest 2026-08-15

> Generated: 2026-08-15 01:37 UTC | Tools covered: 10

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



# Cross-Tool Comparison Report — AI CLI Ecosystem
**Date: 2026-08-15**

---

## 1. Ecosystem Overview

The AI CLI tool landscape is in a phase of intense differentiation and stabilization. Eight major tools were tracked today, with five shipping releases and three showing no new activity. The dominant narrative is maturation — tools are shifting from raw capability expansion toward reliability, cross-platform parity, and enterprise-grade observability. Subagent orchestration, persistent memory, and provider flexibility are the shared frontiers, while Windows/WSL stability and OAuth regressions remain the most common pain points across the ecosystem.

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Releases Today |
|---|---|---|---|
| **Claude Code** | 10 | 4 | v2.1.233 |
| **OpenAI Codex** | 10 | 10 (8 closed) | 5 alpha versions (0.148.0-alpha.14–18) |
| **Gemini CLI** | 10 | 11 (4 closed) | v0.56.0-nightly |
| **GitHub Copilot CLI** | 10 | 3 | v1.0.81-0, v1.0.80 |
| **Kimi Code CLI** | 4 | 0 | — |
| **OpenCode** | 10 | 10 | — |
| **Pi** | 10 | 12 (7 closed) | v0.84.2 |
| **Qwen Code** | 10 | 10 | v0.21.12, v0.21.11-nightly, v0.21.12-preview |
| **CodeWhale (DeepSeek TUI)** | 10 | 10 (9 merged) | v0.9.8 |
| **Grok Build** | — | — | No activity |

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Need |
|---|---|---|
| **Persistent memory / cross-session context** | Claude Code, Gemini CLI, Kimi Code, Pi | Users want sessions that remember project state across invocations; Kimi's #1283 (39 comments) and Gemini's Auto Memory issues are the most vocal |
| **Subagent reliability & observability** | Gemini CLI, OpenCode, CodeWhale | Subagents hanging, misreporting success, or leaking resources; Gemini shipped fixes for termination-reason preservation and PTY leaks |
| **Cross-platform parity (Windows/WSL/Linux)** | Claude Code, Codex, Gemini, OpenCode, Pi, CodeWhale | Windows-specific regressions dominate Codex (#20214, #29436, #28855); Wayland support needed in Gemini and OpenCode; WSL login pain in Pi |
| **MCP / OAuth integration robustness** | GitHub Copilot CLI, Claude Code, OpenCode | RFC 8414 issuer-mismatch failures for Atlassian and GitLab MCP servers; OpenCode's provider model visibility gaps |
| **Per-session / per-environment permissions** | Codex, Claude Code, OpenCode, Pi | Granular control over tool permissions without thread-wide defaults; Codex shipped `permission_profile` support |
| **Incremental / resumable code review** | Qwen Code, OpenCode | Token-efficient review loops that survive rebases and partial failures; Qwen's review pipeline is the most advanced here |

---

## 4. Differentiation Analysis

| Dimension | Leader Tools | Notes |
|---|---|---|
| **Code review & PR workflows** | Qwen Code | Most sophisticated review pipeline with resumable runs, content-anchored incremental rounds, and rebase-aware state transfer |
| **Provider diversity** | Pi, OpenCode | Pi ships siliconFlow, ChatGPT image gen, Vertex, Bedrock Mantle; OpenCode supports GitHub Copilot, DeepSeek, and Ollama Cloud |
| **Multi-agent orchestration** | Gemini CLI, CodeWhale | Gemini supports nested agent calling (#28738); CodeWhale has 32-worker storm capability with session-index serialization |
| **Rapid iteration cadence** | OpenAI Codex | 5 alpha releases in 24 hours; backend-heavy Rust rewrite in active flight |
| **Desktop / TUI polish** | Pi, OpenCode | Pi has fullscreen transcript search and transparent tab backgrounds; OpenCode has Wayland window fallback and palette refresh |
| **Enterprise / CI integration** | GitHub Copilot CLI, Qwen Code | Copilot has MCP registry policy for Actions; Qwen has SWE-bench E2E validation pipeline |
| **Memory architecture** | Kimi Code, Gemini CLI | Kimi is furthest along in explicit memory design (3-tier proposal); Gemini has Auto Memory with redaction concerns |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **OpenAI Codex** — Fastest release cadence (5 alpha builds/day), but Windows performance regressions suggest the pace outstrips QA coverage.
- **Pi** — 12 PRs with 7 closed, active provider expansion, and responsive issue closing (login, clipboard, compaction).
- **CodeWhale** — 9 of 10 tracked PRs merged; critical session-index and webhook fixes shipped; clear post-migration momentum after v0.9.8.

**Steady maturation:**
- **Qwen Code** — Strong review-pipeline investment and benchmark validation; architecture debt (#4063) is the main drag.
- **Gemini CLI** — Subagent fixes are the priority; PTY leak and termination-reason preservation show the team is addressing reliability.
- **Claude Code** — Small PR volume but targeted improvements (shell completions, GitLab MR support); Windows regressions need attention.

**Emerging / lower activity:**
- **Kimi Code CLI** — No releases or PRs this cycle; community focus is on feature requests (memory, cross-device) rather than bug resolution.
- **GitHub Copilot CLI** — OAuth regressions and model-availability glitches suggest integration instability; low PR velocity.
- **Grok Build** — No activity today; ecosystem presence is minimal compared to peers.

---

## 6. Trend Signals

1. **Windows is the ecosystem's weakest link.** Seven distinct Windows issues surfaced across Codex, Claude Code, Gemini, and OpenCode in a single day. Kernel-pool leaks, OAuth hangs, and Git Bash false positives indicate platform-specific regression testing is insufficient across the board.

2. **Subagent reliability is the next frontier.** Every tool with multi-agent support (Gemini, OpenCode, CodeWhale, Copilot) reports subagent hangs, silent failures, or resource leaks. The community is moving past "can agents call agents?" to "can they do it predictably?"

3. **Memory architecture is becoming a competitive differentiator.** Kimi's explicit memory proposal (#1283), Gemini's Auto Memory debates, and Claude Code's session management gaps show that cross-session context is a user-facing feature everyone is still figuring out.

4. **MCP OAuth fragility is an ecosystem risk.** RFC 8414 issuer mismatches affecting Atlassian and GitLab (Copilot CLI) suggest the MCP authentication layer is not yet robust enough for enterprise self-hosted deployments.

5. **Provider consolidation is accelerating.** Tools are adding built-in support for niche providers (siliconFlow, Bedrock Mantle, Kimi, Baseten) rather than relying on generic OpenAI-compatible endpoints, reducing friction for international and cost-conscious users.

6. **Code review as a first-class workflow is emerging.** Qwen Code's incremental, resumable review pipeline is the most advanced implementation today; other tools are implicitly moving in this direction through their agent loop designs.

---

*Report generated from community digests dated 2026-08-15. Data sourced from official GitHub repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data source: github.com/anthropics/skills | As of 2026-08-15*

---

## 1. Top Skills Ranking

| # | Skill / PR | Type | Discussion Focus | Status |
|---|-----------|------|-----------------|--------|
| 1 | **skill-creator evaluation pipeline** (PR #1298, #1099, #1050 + Issue #556) | Fix | `run_eval.py` reports `recall=0%` on every iteration — the core skill-improvement loop is broken; multiple Windows compatibility crashes compound the issue | Open |
| 2 | **skill-quality-analyzer & skill-security-analyzer** (PR #83) | New | Meta-skills that evaluate skills across Structure & Documentation (20%), Trigger Accuracy (20%), Actionability (20%), Reliability (20%), Security (20%) | Open |
| 3 | **ServiceNow platform skill** (PR #568) | New | Broad enterprise skill covering ITSM, ITOM, ITAM/SAM, FSM, CSDM, Security Incident Response, and IntegrationHub | Open — most recently active PR (updated 08-12) |
| 4 | **self-audit skill** (PR #1367) | New | Pre-delivery audit combining mechanical file verification with a four-dimension reasoning quality gate; universal across any project/stack/model | Open |
| 5 | **Testing patterns skill** (PR #723) | New | Full testing stack — Testing Trophy philosophy, AAA pattern, React Component testing (Testing Library), Jest, Cypress, Playwright | Open |
| 6 | **Document-typography skill** (PR #514) | New | Prevents widow/orphan lines, section-header stranding, and numbering misalignment in AI-generated documents | Open |
| 7 | **ODT skill** (PR #486) | New | OpenDocument Format creation, template filling, and ODT→HTML parsing; covers both text (.odt) and spreadsheet (.ods) | Open |
| 8 | **Frontend-design skill** (PR #210) | Improve | Revised for clarity and actionability; ensures every instruction is followable within a single conversation turn | Open |

> **Note:** The community's highest-comment *issues* (#492 at 43 comments, #228 at 16) reflect platform and governance discussions rather than individual skill PRs — see Section 4 for ecosystem insight.

---

## 2. Community Demand Trends

From the Issues backlog, three clear demand vectors emerge:

**① Skill Governance & Security (Issue #492 — 43 comments, #228 — 16 comments)**
- Impersonation risk: community skills distributed under the `anthropic/` namespace blur trust boundaries
- Org-wide skill sharing is the #1 requested platform feature (8 👍 on Issue #228)
- Users want a shared skill library or direct sharing links within Claude.ai

**② Skill Quality & Evaluation Tooling (Issue #556 — 12 comments, #202 — 8 comments)**
- `run_eval.py` trigger failure (0% recall) is the most reproduced bug — 10+ independent reports
- The skill-creator itself is criticized as "developer documentation, not an operational skill" (Issue #202)
- Strong demand for a mechanical + reasoning quality gate before skill delivery (PR #1367 directly addresses this)

**③ Enterprise & Platform Skills**
- ServiceNow (PR #568), SAP predictive analytics (PR #181), and SharePoint Online security (Issue #1175) signal appetite for vertical enterprise skills
- Testing patterns (PR #723) and document-format skills (PDF, DOCX, ODT, typography) address horizontal professional needs

---

## 3. High-Potential Pending Skills

These PRs have active discussion, recent updates, and high community alignment — strong candidates for merge:

| PR | Skill | Why It May Land Soon |
|----|-------|---------------------|
| [#568](https://github.com/anthropics/skills/pull/568) | ServiceNow platform | Most recently updated (08-12); comprehensive enterprise coverage with clear trigger language |
| [#1367](https://github.com/anthropics/skills/pull/1367) | Self-audit | Directly fixes the skill-creator quality gap; mirrors the reasoning-quality-gate proposal in Issue #1385 |
| [#1538](https://github.com/anthropics/skills/pull/1538) | Spec compliance fix | Brings two existing skills in line with the Agent Skills spec — low-risk, high-correctness |
| [#1479](https://github.com/anthropics/skills/pull/1479) | Plan-file-hygiene | Addresses a specific, named lifecycle problem (Issue #1417); scoped and well-framed |
| [#525](https://github.com/anthropics/skills/pull/525) | Pyxel retro game dev | Recently active (07-15); niche but distinctive; MCP server integration is a clean pattern |
| [#723](https://github.com/anthropics/skills/pull/723) | Testing patterns | Full-stack testing coverage; complements existing code-review and doc skills without overlap |
| [#514](https://github.com/anthropics/skills/pull/514) | Document typography | Solves a universal pain point (widows/orphans) with simple, verifiable rules |
| [#83](https://github.com/anthropics/skills/pull/83) | Skill quality + security analyzer | Fills the meta-tooling gap; two skills in one PR, directly responding to the quality crisis in Issues #556 and #202 |

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is not for more individual skills, but for *skill quality infrastructure* — reliable evaluation tooling, security governance, and org-wide distribution — because the current skill-creator pipeline is producing noisy, un-verifiable outputs that erode user trust faster than new skills can add value.**

**Supporting signals:**
- The #1 most-commented issue (#492, 43 comments) is about *trust boundary abuse*, not a missing feature
- The #1 most-reproduced bug (Issue #556 / PR #1298) breaks the *entire improvement loop*
- PR #83 (quality analyzer) and PR #1367 (self-audit) both target meta-level verification, not end-user tasks
- Issue #202 explicitly states the skill-creator reads like documentation, not an operational skill

The ecosystem is maturing from "ship more skills" to "make skills trustworthy and measurable."

---



# Claude Code Community Digest — 2026-08-15

## 1. Today's Highlights

Claude Code v2.1.233 landed with GitLab MR URL support in `--worktree` and an opt-in `forward_user_identity` apps gateway setting for upstream proxies. On the issue front, the long-running API error-reporting bug (#69238) continues to dominate community attention with 96 upvotes, while a critical mouse-tracking restore handler gap (#84029) was flagged as a terminal-preservation regression.

## 2. Releases

**v2.1.233** ([link](https://github.com/anthropics/claude-code/releases))
- Added GitLab merge request URL support to the `--worktree` flag and the `claude agents` view (MRs display as `!N`).
- Added opt-in `forward_user_identity` apps gateway setting on Anthropic upstreams, forwarding the signed-in user's identity as headers so proxies behind the gateway can authenticate on behalf of the user.

## 3. Hot Issues

1. **#69238 — No API response when Advisor triggers** (63 comments, 96 👍) — Advisor mode with Opus 4.8 hangs with "No response from API" and retried indefinitely. Community impact is high because it affects a core workflow; the volume of engagement suggests many users are hitting the same wall. [Link](https://github.com/anthropics/claude-code/issues/69238)

2. **#30869 — Unarchive sessions in Desktop** (29 comments, 57 👍) — Users can archive but lack a discoverable way to restore sessions from the Desktop UI. This feature request has sustained support and represents a clear UX gap in session management. [Link](https://github.com/anthropics/claude-code/issues/30869)

3. **#24537 — Agent Hierarchy Dashboard** (16 comments, 17 👍) — Multi-agent workflows lack a unified real-time TUI/Desktop view. As agent-based development matures, visibility into agent trees is a frequently requested operational need. [Link](https://github.com/anthropics/claude-code/issues/24537)

4. **#11791 — Browser automation blocked by web sandbox proxy** (11 comments, 16 👍) — Playwright/Puppeteer/Selenium cannot run because the security proxy lacks HTTPS CONNECT tunneling. A fundamental architectural limitation that prevents whole classes of automation workflows. [Link](https://github.com/anthropics/claude-code/issues/11791)

5. **#86619 — Windows Git Bash false-positive permission prompts** (9 comments, 9 👍) — Regression introduced in v2.1.232's auto-mode rollout; static analysis of read-only cd-compound commands triggers unsuppressable prompts. Affects Windows developers on Git Bash specifically. [Link](https://github.com/anthropics/claude-code/issues/86619)

6. **#66117 — Disable prompt suggestions in claude.ai web/app** (9 comments, 10 👍) — Users want to suppress in-chat prompt suggestions for a cleaner interface, particularly in professional or focused workflows. [Link](https://github.com/anthropics/claude-code/issues/66117)

7. **#84029 — Crash leaves terminal in mouse-tracking mode** (2 comments) — The restore handler only fires on graceful exit; on a crash the terminal stays in mouse-tracking, injecting raw escape sequences into the shell prompt. A low-complexity but high-annoyance regression. [Link](https://github.com/anthropics/claude-code/issues/84029)

8. **#84266 — model_refusal_fallback on legitimate tmux orchestration** (2 comments) — Multi-session tmux-based workflows with `switchModelsOnFlag: false` are blocked by safety false-positives on the coordinator session. Impacts production-like multi-agent setups. [Link](https://github.com/anthropics/claude-code/issues/84266)

9. **#86473 — Persistent ECONNRESET on Windows despite healthy raw HTTPS** (2 comments, 2 👍) — All Code surfaces fail with connection resets while direct HTTPS to `api.anthropic.com` works. Points to a client-side networking layer bug on Windows. [Link](https://github.com/anthropics/claude-code/issues/86473)

10. **#86809 — Plugin hooks never run from directory-source marketplace** (CLOSED, 1 comment) — Plugins installed from a directory-source marketplace report enabled but hooks never execute; the same plugin from a github-source marketplace works. Closed quickly, suggesting a fix was identified. [Link](https://github.com/anthropics/claude-code/issues/86809)

## 4. Key PR Progress

1. **#86746 — Fix: preserve Python probe errors** ([Link](https://github.com/anthropics/claude-code/pull/86746)) — Fixes #86709 by preserving stderr from Python interpreter probes. Previously, when all candidate interpreters failed, users only saw a generic message instead of the diagnostic output.

2. **#86626 — Add shell completions (bash, zsh, fish)** ([Link](https://github.com/anthropics/claude-code/pull/86626)) — Ships tab-completion scripts under `completions/` for bash (works with stock macOS bash 3.2), zsh, and fish, keeping completions in sync with the installed CLI version.

3. **#83890 — Create pylint.yml** ([Link](https://github.com/anthropics/claude-code/pull/83890)) — Adds a pylint configuration file to the repo, standardizing linting behavior for Python tooling within Claude Code.

4. **#41611 — Add missing source to Claude Code** ([Link](https://github.com/anthropics/claude-code/pull/41611)) — Long-open PR aimed at populating missing source references; still awaiting review.

## 5. Feature Request Trends

- **Session management & archival** (#30869, #85272): Users want better control over session lifecycle — archiving, unarchiving, and persistent visibility in the Desktop UI. Several reports of sessions disappearing or being silently cleaned up.
- **Multi-agent visibility & orchestration** (#24537, #86089): As agent workflows scale, the community is asking for hierarchy dashboards and the ability to resume agent sessions within workflows, moving beyond one-shot agent execution.
- **Configurability of defaults** (#79217, #66117): Requests to make hard-coded limits (MEMORY.md index size, prompt suggestions) configurable reflect a desire for per-environment tuning.
- **Platform parity** (#66117, #82431): Features available on web/app (e.g., Dispatch sidebar, prompt controls) are missing or inconsistent on Desktop/Linux, creating cross-platform friction.

## 6. Developer Pain Points

- **Silent or misleading errors**: The Advisor API hang (#69238) and false "unpushed commits" from stop hooks (#83924) both reflect poor error telemetry, leaving users unable to diagnose root causes.
- **Windows-specific regressions**: Three distinct Windows issues surfaced recently — Git Bash permission prompts (#86619), MSIX update failures (#86555), and ECONNRESET networking bugs (#86473) — indicating the Windows surface needs focused regression testing.
- **Data loss & session cleanup**: The default `cleanupPeriodDays` silently deleted 58 of 69 session transcripts for one user (#86730), and archiving a Cowork project removes it from the UI with no restore path (#85272). These are trust-level issues for power users.
- **Model safety false-positives**: Legitimate defensive-security work (WAF development #86804, credential rotation #86819) and tmux orchestration (#84266) are triggering safety refusals, forcing model switches or blocking workflows entirely.
- **Plugin marketplace instability**: Directory-source plugin installs not running hooks (#86809) and account-scoped GitHub marketplace update checks failing on first attempt (#86818) suggest the marketplace plumbing is still rough.
- **Token billing opacity**: A 17x variance in tokens charged per weekly quota point (#84607) and unexpected duplicate payloads from `claude-api` reinvocation (#86817) are eroding cost predictability.
- **Auto-compact window inconsistency**: Sessions on `claude-opus-5[1m]` show a 150k compact window instead of the expected 1M (#85205), suggesting a model-config resolution bug.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-15

## 1. Today's Highlights

The Codex team pushed five rapid Rust alpha releases (0.148.0-alpha.14 through alpha.18) in the past 24 hours, signaling active iteration on the backend. Community attention is dominated by a wave of Windows desktop performance regressions tied to the 26.810.x update cycle, including system-wide mouse stutter, kernel-pool memory growth, and CPU busy loops. On the feature side, permission-profile hardening, DNS proxy routing for Linux sandboxes, and Code Mode schema resolution are making significant progress.

---

## 2. Releases

Five Rust alpha versions released in the last 24 hours, indicating a fast-moving release cadence for the 0.148.0 track:

| Version | Link |
|---|---|
| rust-v0.148.0-alpha.18 | https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.18 |
| rust-v0.148.0-alpha.17 | https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.17 |
| rust-v0.148.0-alpha.16 | https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.16 |
| rust-v0.148.0-alpha.15 | https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.15 |
| rust-v0.148.0-alpha.14 | https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.14 |

No formal release notes were included; users are encouraged to review commit diffs for changelog details.

---

## 3. Hot Issues

**#20214 — Codex App frequently freezes/stutters on Windows 11 Pro** (101 comments, 84 👍)
The highest-engagement issue on the tracker. Users report persistent freezing despite sufficient RAM/CPU, pointing to a deep Windows-specific rendering or threading problem. The strong community signal (84 upvotes) makes this the top priority for triage.
https://github.com/openai/codex/issues/20214

**#38547 — Idle main-process CPU busy loop in Chrome plugin app-server hashing** (12 comments, 5 👍)
A regression introduced in 26.810.4967.0 causing the Electron main process to spin at 100% CPU while completely idle. Since it stems from the latest Windows update, it's likely part of a broader regression pattern affecting multiple users.
https://github.com/openai/codex/issues/38547

**#38455 — Computer Use worker spam and V8 OOM crashes on macOS** (12 comments, 4 👍)
ChatGPT desktop 26.810.41047 spawns 187 named `computer-use` threads and crashes with a V8 out-of-memory error ~98 seconds after launch. A clear regression from the previous build (26.730.x), suggesting a memory leak in the new Computer Use worker pool.
https://github.com/openai/codex/issues/38455

**#29532 — Persistent SQLite TRACE log churn on macOS after rust-v0.142.0** (47 comments, 9 👍)
While partial fixes (#29432, #29457) reduced `codex_api::endpoint::responses_websocket` noise, SQLite log churn in `~/.codex/logs_2.sqlite` continues. This impacts disk I/O and longevity on macOS machines.
https://github.com/openai/codex/issues/29532

**#25453 — PowerShell.exe spawned every second causing high CPU on Windows** (26 comments, 7 👍)
Codex Desktop repeatedly forks short-lived `powershell.exe` instances for process polling, creating sustained CPU overhead. This is a known Windows-specific architecture issue that remains unresolved.
https://github.com/openai/codex/issues/25453

**#28015 — False-positive cybersecurity safety check blocks normal local repo maintenance** (24 comments, 5 👍)
The CLI's safety checker incorrectly flags routine DevOps hygiene (e.g., `git status`, log rotation) as cybersecurity risks, interrupting paid sessions. Users are calling for better context-awareness in the safety pipeline.
https://github.com/openai/codex/issues/28015

**#24287 — UI stuck in "Thinking" state; Stop fails and turns become invisible** (23 comments, 8 👍)
On macOS, Codex Desktop accepts prompts but the UI freezes in a thinking state. The Stop button is unresponsive and completed turns can become invisible after restart — a severe UX blocker for long sessions.
https://github.com/openai/codex/issues/24287

**#28855 — Intermittent system-wide input lag on Windows despite clean logs** (18 comments, 20 👍)
Users report whole-system mouse and keyboard lag specifically when Codex is open, even with plugins disabled and clean logs. The high upvote count (20) relative to comment count suggests broad but under-discussed impact.
https://github.com/openai/codex/issues/28855

**#29436 — Kernel-pool memory growth and system-wide slowdown on Windows** (15 comments, 7 👍)
Sustained kernel-pool growth drives system memory toward 95%, causing severe delays in screenshots and clipboard operations. Ordinary app closures do not recover the leaked memory, pointing to a kernel-driver or non-paged pool leak.
https://github.com/openai/codex/issues/29436

**#38668 — "Open in folder" falls back to C:\ for mapped-drive/UNC paths** (2 comments, 0 👍)
A practical UX bug where the Windows app resolves mapped-network-drive and UNC project paths to `C:\` instead of the actual folder. While low-engagement, it affects users working with network storage.
https://github.com/openai/codex/issues/38668

---

## 4. Key PR Progress

**#38682 — Surface misalignment policy violations as typed errors** (CLOSED)
Errors from response streams and HTTP 400/403 responses are now recognized as typed `misalignment_policy_violation` errors with preserved upstream messages and non-retryable semantics.
https://github.com/openai/codex/pull/38682

**#38681 — Preserve HTTP fallback for delegated sessions** (CLOSED)
Delegated sessions now correctly inherit their parent's transport mode, preventing spurious WebSocket connection attempts when the parent has already fallen back to HTTP.
https://github.com/openai/codex/pull/38681

**#38678 — Preserve environment configuration ownership** (CLOSED)
Thread-level setting updates now refresh inherited configuration without overwriting attachment-owned permissions and capability roots, fixing a configuration-merge bug.
https://github.com/openai/codex/pull/38678

**#38675 — Exclude shortcut-modified input from TUI paste bursts** (CLOSED)
Super/Hyper/Meta key events are now excluded from paste-burst detection, preventing accidental input flushes when users invoke system shortcuts in the TUI.
https://github.com/openai/codex/pull/38675

**#38673 — Honor per-environment permission profiles** (CLOSED)
Each `EnvironmentConfig` now carries a resolved `permission_profile`, enabling `Ready` environments to override thread permissions while `FromThread` configs preserve inherited policies.
https://github.com/openai/codex/pull/38673

**#38670 — Forward executor network policy decisions for auditing** (CLOSED)
A best-effort `network/policyDecision` notification is now emitted for every domain and non-domain policy decision, with audit event validation against the active controller process.
https://github.com/openai/codex/pull/38670

**#38664 — Resolve local JSON Schema refs in Code Mode types** (CLOSED)
Code Mode now correctly resolves fragment-only JSON Pointer `$ref` values against the root schema, fixing a bug where referenced input and structured-output shapes rendered as `unknown` in generated TypeScript declarations.
https://github.com/openai/codex/pull/38664

**#38660 — Enforce managed deny-read rules in the Windows sandbox** (CLOSED)
Windows sandbox requests now preserve managed filesystem deny rules across all execution paths and setup refreshes, failing closed for unsupported policies instead of allowing unprotected execution.
https://github.com/openai/codex/pull/38660

**#38657 — Skip terminal hyperlink layout when no links are present** (CLOSED)
The TUI now returns early from `mark_buffer_hyperlinks` when no hyperlink metadata is found, avoiding unnecessary paragraph layout work and reducing CPU during terminal rendering.
https://github.com/openai/codex/pull/38657

**#31644 — Route DNS through managed proxy on Linux sandboxes** (OPEN)
Adds an opt-in `enable_dns` managed proxy setting with a DNS-speaking adapter inside the bubblewrap network namespace, since native DNS clients ignore HTTP/SOCKS proxy variables on Linux.
https://github.com/openai/codex/pull/31644

---

## 5. Feature Request Trends

- **Cross-workspace task handoff**: Issue #34582 requests a repository-aware, sanitized mechanism to transfer context between Codex sessions across workspaces — a sign that power users are running multi-repo workflows and need state continuity.
- **Better Git diagnostic feedback**: Issue #24484 asks for improved error messaging when WorkTree project association fails due to `safe.directory` or ownership issues, reflecting frustration with opaque Git integration errors on Windows.
- **Per-environment permission profiles**: Multiple PRs (#38673, #38651) and community issues indicate demand for granular, per-session permission control rather than thread-wide defaults.
- **Network policy auditability**: PR #38670 shows the team is responding to demand for observable network decisions in sandboxed execution, important for enterprise compliance workflows.
- **Config override flexibility**: PR #38647 adds `LoaderOverrides::ignore_project_config`, suggesting community need for bypassing project-level config in specific scenarios (CI, testing, temporary sessions).

---

## 6. Developer Pain Points

**Windows desktop performance regressions (26.810.x)** dominate the tracker. At least seven open issues (#20214, #25453, #28855, #29436, #33912, #38547, #38583) report system-wide mouse stutter, CPU busy loops, kernel-pool leaks, or input lag directly tied to the 26.810.x update cycle released on 2026-08-14. This is the single most urgent concern for the Windows user base.

**macOS memory and stability regressions** are also emerging, with #38455 and #38468 reporting V8 OOM crashes, 10+ GB RAM usage, and 100%+ CPU on Apple Silicon — both regressions from the 26.730.x baseline.

**SQLite and log churn** on macOS (#29532) continues to degrade disk performance for long-running sessions, with partial fixes that haven't fully resolved the underlying websocket response logging.

**False-positive safety checks** (#28015) in the CLI are blocking routine development workflows, indicating the cybersecurity safety pipeline needs better context awareness for local-only operations.

**Terminal/UI state bugs** (#24287, #34026) — where sessions get stuck in "thinking" or completed turns become invisible — suggest race conditions in the session management layer that are especially disruptive during extended coding workflows.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-15

## 1. Today's Highlights

The team shipped **v0.56.0-nightly** with a critical fix for subagent recovery after hitting `MAX_TURNS` (issue #22323), where the subagent was incorrectly reporting `GOAL` success instead of the true termination reason. Three more PRs are in flight addressing the same recovery path, a composite TypeScript flag, and silent `MessageBus` hangs. Meanwhile, community discussion is heavily focused on subagent reliability, Auto Memory quirks, and shell execution stability.

---

## 2. Releases

**v0.56.0-nightly.20260815.g2a87e7be1** ([PR #28821](https://github.com/google-gemini/gemini-cli/pull/28821))

- **#28811** — Migrated `process.env` manipulation in `a2a-server` tests to use `vi.stubEnv()` / `vi.unstubAllEnvs()`, aligning with project testing guidelines and eliminating test-side pollution ([#19826](https://github.com/google-gemini/gemini-cli/issues/19826)).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Response |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | A subagent hitting its turn limit was being marked as successful, silently hiding the interruption. This directly compromises eval fidelity and debuggability of multi-step agent workflows. | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | The generalist subagent hangs indefinitely on simple tasks (e.g. folder creation), forcing users to either wait or explicitly disable subagents. | 8 comments · 8 👍 — highest engagement |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model's bash affinity via Zero-Dependency OS Sandboxing | Proposes routing bash-native model behavior through sandboxed execution with post-execution intent routing — a significant architecture enhancement for security-conscious users. | 8 comments |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | Follows up on behavioral evals; 76 tests generated across 6 Gemini models. Critical for measuring agent quality improvements systematically. | 7 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess AST-aware file reads, search, and mapping | Evaluates whether AST-aware tools reduce turn counts and token noise by precisely reading method bounds. Could materially improve codebase_investigator efficiency. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Users report the model rarely invokes custom skills or subagents unless explicitly instructed, undermining a core design goal. | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory from retrying low-signal sessions | Auto Memory re-surfaces the same low-signal sessions indefinitely because they're never marked as processed — a quality-of-life and privacy concern. | 5 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck "Waiting input" | Simple CLI commands complete but the TUI remains stuck in an awaiting state, blocking further interaction. Affects daily usability. | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | The browser agent crashes under Wayland compositors, blocking Linux users who don't use X11. | 4 comments · 1 👍 |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores settings.json overrides | `maxTurns` and other overrides in `settings.json` are silently ignored by the browser agent, making configuration unreliable. | 3 comments |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#28815](https://github.com/google-gemini/gemini-cli/pull/28815) | Preserve original termination reason during subagent recovery | Open | Fixes #22323 — ensures that when a subagent recovers after `MAX_TURNS`/`TIMEOUT`, the true termination reason is preserved instead of being overwritten with `GOAL`. |
| [#28812](https://github.com/google-gemini/gemini-cli/pull/28812) | Prevent indefinite TUI hang by adding execution timeouts | Open | Fixes #21477 — adds timeouts to `getProcessInfo()` so the TUI no longer hangs forever at "Initializing..." on bare Linux terminals. |
| [#28813](https://github.com/google-gemini/gemini-cli/pull/28813) | Add composite flag to packages/cli tsconfig | Open | Fixes #21911 — resolves build/typecheck failures caused by `evals/tsconfig.json` referencing a non-composite `packages/cli`. |
| [#28816](https://github.com/google-gemini/gemini-cli/pull/28816) | Fix silent hang in MessageBus.request | **Closed** | Fixes #22588 — `MessageBus.request()` previously silently hung for 60s when `publish()` rejected, due to an unhandled floating promise. |
| [#28817](https://github.com/google-gemini/gemini-cli/pull/28817) | Retain executing subagent tool calls in hook state | **Closed** | Fixes #22589 — non-root scheduler tool calls in `Executing` status were being dropped before entering hook state. |
| [#20916](https://github.com/google-gemini/gemini-cli/pull/20916) | Prevent PTY file descriptor leak in ShellExecutionService | **Closed** | Fixes #15945 — PTY master descriptors were never closed after process exit, causing system-wide PTY exhaustion (macOS limit: 511). |
| [#27154](https://github.com/google-gemini/gemini-cli/pull/27154) | Prevent PTY memory leak by synchronously deleting active entries | **Closed** | Fixes deferred deletion of PTY entries in `ShellExecutionService`, addressing both memory and fd leaks from background log streams. |
| [#28738](https://github.com/google-gemini/gemini-cli/pull/28738) | Allow agents to call agents | Open | Fixes #22092 — enables subagents to delegate to other subagents or recurse via `tools:` frontmatter, unlocking deeper agent hierarchies. |
| [#25378](https://github.com/google-gemini/gemini-cli/pull/25378) | Fix Windows ripgrep eftype | Open | Fixes #22784 — `grep_search` tool failed with `spawn EFTYPE` on Windows when the downloaded binary mismatched host architecture. |
| [#27588](https://github.com/google-gemini/gemini-cli/pull/27588) | Support WSL2 clipboard image paste | Open | Fixes #22274 — enables image paste from the Windows clipboard inside WSL2 by routing through PowerShell interop. |

---

## 5. Feature Request Trends

- **Subagent reliability and observability** — The dominant thread. Users want subagents that actually invoke skills, recover gracefully from limits, expose their trajectories via `/chat share` ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598)), and don't silently succeed or hang. Nested agent calling ([#28738](https://github.com/google-gemini/gemini-cli/pull/28738)) is a step in this direction.
- **AST-aware codebase tools** — Multiple linked issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)) explore whether parse-tree-aware reads and searches can reduce turns and token waste in `codebase_investigator`.
- **Security and privacy hardening** — Deterministic redaction for Auto Memory ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)), quarantine of invalid memory patches ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and discouraging destructive model behavior ([#22672](https://github.com/google-gemini/gemini-cli/issues/22672)) signal strong community demand for safer autonomous execution.
- **Platform parity** — Wayland support ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)), WSL2 clipboard ([#27588](https://github.com/google-gemini/gemini-cli/pull/27588)), and Windows ripgrep fixes ([#25378](https://github.com/google-gemini/gemini-cli/pull/25378)) reflect ongoing pushes for cross-platform consistency.

---

## 6. Developer Pain Points

1. **Subagent silencing and misreporting** — Subagents hang, report false success, or simply aren't invoked without explicit prompting. This is the #1 frustration across multiple high-engagement issues.
2. **Shell execution getting stuck** — Commands that finish normally leave the TUI in a perpetual "Awaiting user input" state ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), blocking workflow.
3. **PTY resource leaks** — Two separate PRs ([#20916](https://github.com/google-gemini/gemini-cli/pull/20916), [#27154](https://github.com/google-gemini/gemini-cli/pull/27154)) addressed file descriptor and memory leaks in `ShellExecutionService`, indicating this is a recurring infrastructure pain point on long-running sessions.
4. **Configuration not respected** — `settings.json` overrides silently ignored by the browser agent ([#22267](https://github.com/google-gemini/gemini-cli/issues/22267)) and symlinks in `~/.gemini/agents/` not resolved ([#20079](https://github.com/google-gemini/gemini-cli/issues/20079)) erode trust in the configuration system.
5. **Auto Memory quality** — Low-signal sessions are retried indefinitely ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522)), invalid patches are silently dropped ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and redaction happens after content already enters model context ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-15

## 1. Today's Highlights
GitHub Copilot CLI v1.0.81-0 and v1.0.80 were released, both focusing on model configuration updates. The community is actively reporting several regressions in MCP OAuth authentication (Atlassian, GitLab) and model availability issues, alongside critical stability problems like an OOM crash in long-running autopilot sessions.

## 2. Releases
- **v1.0.81-0** ([GitHub Link](https://github.com/github/copilot-cli/releases/tag/v1.0.81-0)): Improved model configurations.
- **v1.0.80** ([GitHub Link](https://github.com/github/copilot-cli/releases/tag/v1.0.80)): Updated model configurations.

## 3. Hot Issues
1. **#4345** [OPEN] Reasoning effort 'medium' not supported for model 'claude-haiku-4.5'  
   *Why it matters:* Feature flags assign unsupported reasoning levels, causing repeated sub-agent execution failures.  
   *Community reaction:* 6 comments, 4 👍  
   [Link](https://github.com/github/copilot-cli/issues/4345)

2. **#4390** [OPEN] Enabled organization models missing from catalogue (Claude Sonnet 5/Opus 5 and Kimi K3)  
   *Why it matters:* Org-enabled Anthropic models are unavailable in the CLI, blocking users from switching to newer models.  
   *Community reaction:* 6 comments, 4 👍  
   [Link](https://github.com/github/copilot-cli/issues/4390)

3. **#4480** [CLOSED] Atlassian MCP OAuth fails with "Incompatible authorization server (RFC 8414 §3.3)" on 1.0.79 — regression from 1.0.71  
   *Why it matters:* A regression broke Atlassian MCP OAuth after upgrading to 1.0.79, affecting enterprise integrations.  
   *Community reaction:* 4 comments, 6 👍  
   [Link](https://github.com/github/copilot-cli/issues/4480)

4. **#4422** [OPEN] All Claude models disabled under CLI model selection  
   *Why it matters:* Personal Enterprise users cannot select any Claude models despite them being enabled in GitHub settings.  
   *Community reaction:* 3 comments, 3 👍  
   [Link](https://github.com/github/copilot-cli/issues/4422)

5. **#4439** [OPEN] Copilot CLI 1.0.79 rejects GitLab MCP OAuth metadata with an RFC 8414 issuer mismatch  
   *Why it matters:* GitLab Self-Managed MCP OAuth authentication fails due to strict issuer validation, impacting self-hosted workflows.  
   *Community reaction:* 3 comments, 2 👍  
   [Link](https://github.com/github/copilot-cli/issues/4439)

6. **#4306** [OPEN] Subtasks freeze and stop responding  
   *Why it matters:* Autopilot sessions with looping agents (e.g., speckit-implement/converge) become unresponsive, breaking long-running tasks.  
   *Community reaction:* 3 comments, 2 👍  
   [Link](https://github.com/github/copilot-cli/issues/4306)

7. **#2934** [CLOSED] Support protobuf OTLP export (OTEL_EXPORTER_OTLP_PROTOCOL=http/protobuf)  
   *Why it matters:* The CLI silently ignores the standard OTLP protocol env var, forcing JSON-only telemetry and hindering integration with monitoring stacks that expect protobuf.  
   *Community reaction:* 2 comments, 6 👍  
   [Link](https://github.com/github/copilot-cli/issues/2934)

8. **#4346** [CLOSED] MCP registry policy fetch returns 403 for Actions GITHUB_TOKEN, blocking all non-default MCP servers in CI  
   *Why it matters:* The documented PAT-less GitHub Actions setup fails to fetch MCP registry policies, breaking CI/CD pipelines that rely on custom MCP servers.  
   *Community reaction:* 2 comments, 3 👍  
   [Link](https://github.com/github/copilot-cli/issues/4346)

9. **#4488** [OPEN] Plugin updates fail with Access is denied when other Copilot CLI or VS Code sessions are open  
   *Why it matters:* File locks from unrelated sessions block plugin updates, causing friction for users with multiple environments.  
   *Community reaction:* 1 comment, 0 👍  
   [Link](https://github.com/github/copilot-cli/issues/4488)

10. **#4499** [OPEN] v1.0.79 fatal "Committing semi space failed" OOM in autopilot with V8 heap only ~0.6/4.3 GB  
    *Why it matters:* A severe crash during long autopilot sessions where heap usage is low but host‑RAM commit fails, indicating a platform‑level memory pressure issue.  
    *Community reaction:* 0 comments, 0 👍  
    [Link](https://github.com/github/copilot-cli/issues/4499)

## 4. Key PR Progress
1. **#4497** [OPEN] Handle fork PR associations in invalid-label writer  
   *Summary:* Updates the trusted invalid-label writer to handle fork PRs when GitHub omits the pull‑request association, using workflow‑run metadata instead.  
   [Link](https://github.com/github/copilot-cli/pull/4497)

2. **#4496** [CLOSED] [invalid] [canary] Verify pull request workflow migration  
   *Summary:* A temporary documentation‑only canary PR used to verify the recently migrated PR automation for fork‑originated PRs; closed after confirmation.  
   [Link](https://github.com/github/copilot-cli/pull/4496)

3. **#4449** [CLOSED] Migrate pull request automation away from `pull_request_target`  
   *Summary:* Replaces `pull_request_target` with a no‑permission `pull_request` signal for prompt handling, closes invalid issues directly with an issue‑scoped write token, and runs privileged steps via workflow runs.  
   [Link](https://github.com/github/copilot-cli/pull/4449)

*(Note: Only 3 PRs were reported in the last 24 hours; all are included above.)*

## 5. Feature Request Trends
- **MCP OAuth/Integration Robustness:** Multiple reports of RFC 8414 issuer‑mismatch failures (Atlassian, GitLab) highlight a demand for more flexible OAuth discovery and stricter compliance with vendor implementations.
- **Model Catalog & Configuration Management:** Requests for reliable model‑catalog refresh (no manual cache clear) and explicit support for new reasoning parameters (GPT‑5.6 `reasoning.mode`, Claude reasoning effort) show users want finer control over model selection and capabilities.
- **Plugin Ecosystem Maturity:** Suggestions for inter/intra‑marketplace dependency resolution and fixes for file‑lock‑induced update failures indicate a push toward a more resilient plugin management system.
- **Telemetry Export Flexibility:** The continued interest in protobuf OTLP export points to a need for better observability integration without forcing JSON‑only pipelines.

## 6. Developer Pain Points
- **OAuth Regression Chaos:** A wave of MCP OAuth failures across providers (Atlassian, GitLab) after minor version upgrades has disrupted enterprise and self‑hosted workflows.
- **Model Availability Glitches:** Users frequently encounter disabled or missing models (especially Claude Sonnet/Opus) despite correct org/personal settings, forcing manual cache resets or rollbacks.
- **Session & Stability Issues:** Long‑running autopilot sessions are prone to freezing (#4306) or fatal OOM crashes (#4499) even when the V8 heap appears healthy, suggesting platform‑level memory pressures.
- **Plugin & Update Friction:** Plugin updates are blocked by file locks from other sessions (#4488), and the Codespaces environment ships an outdated CLI version that refuses to replace itself without `sudo` (#4501).
- **Configuration Ambiguity:** Startup messages like “No copilot‑instructions.md found” are ambiguous (#4475), and policy configurations (e.g., `allowed_directories`) are inconsistently enforced across command types (#4482).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-15

---

## 1. Today's Highlights

The dominant community theme this week is **memory and context management** — three of four tracked issues focus on improving long-term context retention across sessions. A long-standing feature request (#1283, 39 comments) for a comprehensive memory system continues to gather momentum, while an open question (#1478) highlights gaps in documentation around memory capabilities.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

### #1283 — Memory System: Persistent Context Across Sessions [OPEN]
**Author:** CatKang | **Updated:** 2026-08-14 | **Comments:** 39 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)

A high-impact feature request proposing a two-tier memory architecture (AI-managed automatic notes + user-defined manual instructions via `config.md`). With 39 comments and active discussion through mid-August, this remains one of the most-requested enhancements. The proposal aligns with patterns seen in competing tools (e.g., OpenClaw's `MEMORY.md` / daily memory structure), suggesting strong community appetite for persistent project memory.

### #2269 — Remote Control / Multi-Device Session Handoff [OPEN]
**Author:** lucianalima777 | **Updated:** 2026-08-14 | **Comments:** 6 | 👍: 1 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/2269)

Requests the ability to start a CLI session on one device and continue or remotely control it from another (laptop, web, or mobile). Currently, sessions are device-bound, which limits workflow flexibility for users operating across environments. Low comment count but one upvote indicates early interest; likely to grow as multi-device development workflows become more common.

### #1478 — Memory Layer Optimization & Documentation Gap [OPEN]
**Author:** hahy36 | **Updated:** 2026-08-15 | **Comments:** 3 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/1478)

A bilingual (CN/EN) issue flagging two concerns: (1) the memory layer needs optimization for large projects, and (2) memory-related functionality is absent from official documentation. The author references OpenClaw's memory architecture (`SOUL.md`, `USER.md`, `MEMORY.md`, daily `memory/` files) as a potential reference model. The freshness (updated today) and direct comparison to a competitor's design suggest this issue may catalyze further feature discussions.

### #1136 — Shell Tool: Version-Aware PowerShell Context [CLOSED]
**Author:** QIN2DIM | **Updated:** 2026-08-14 | **Comments:** 0 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/1136)

A closed enhancement addressing three critical shell tool issues on Windows with **Kimi K2.5 (SGLang)**: ambiguous shebang handling, context awareness, and version detection. Though closed with no comments, its resolution suggests the team is actively improving cross-platform shell compatibility — a foundational concern for the broader Windows user base.

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

| Trend | Evidence |
|---|---|
| **Persistent Memory & Context** | #1283 (39 comments), #1478 (today) — the single most-discussed direction, with users requesting both automatic AI-managed memory and explicit user-configurable instructions |
| **Cross-Device Session Continuity** | #2269 — emerging need for session handoff between devices, reflecting a shift toward distributed development workflows |
| **Windows/PowerShell Support** | #1136 (now closed) — indicates the team is actively addressing platform-specific shell compatibility, a recurring pain point for Windows developers |
| **Documentation Gaps** | #1478 explicitly calls out missing memory documentation, suggesting feature visibility and onboarding are area for improvement |

---

## 6. Developer Pain Points

1. **No persistent memory across sessions** — The most frequent frustration. Users working on large projects report that Kimi CLI "forgets" project context between invocations, forcing repetition of setup and background information.
2. **Unclear or missing documentation** — Memory-related features (or their absence) are not well-documented. New users cannot discover how (or whether) to configure long-term context.
3. **Windows shell tooling friction** — Prior to #1136's resolution, ambiguous shebang handling and lack of PowerShell version awareness degraded agent performance on Windows, especially during first-pass command generation.
4. **Session lock-in to a single device** — Users cannot hand off or continue sessions across devices, limiting flexibility for developers who switch between environments (e.g., desktop → laptop → remote).

---

*Data sourced from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli). Digest generated 2026-08-15.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-15

## 1. Today's Highlights

A critical 48-bit ID timestamp wraparound bug (#42608) caused pre-2026 sessions to silently stop processing prompts — a fix is already in PR #42684. Simultaneously, the team shipped several TUI reliability improvements, including system theme palette refresh (#42685), transparent tab background preservation (#42646), and a Wayland window visibility fallback (#42681).

---

## 2. Releases

No releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#42608](https://github.com/anomalyco/opencode/issues/42608) | 48-bit ID timestamp wraparound wedges all pre-existing sessions | Root-cause of a mass session-stuck incident; IDs overflow 2⁴⁸, breaking chronological comparison and causing the agent loop to exit at step 0. | 5 comments · 3 👍 — urgent, closed |
| [#36997](https://github.com/anomalyco/opencode/issues/36997) | Desktop v1.18.1 new layout hides agent switching UI | The `newLayoutDesigns: true` toggle in v1.18.1 regresses visibility of the Plan/Build mode indicator and breaks Tab-key navigation. | 12 comments · 6 👍 — open |
| [#42013](https://github.com/anomalyco/opencode/issues/42013) | Free usage exceeded on OpenCode Zen | Free-tier users hit `FreeUsageLimitError` before the expected daily reset, blocking access to DeepSeek V4 Flash Free. | 10 comments · 4 👍 — open |
| [#42083](https://github.com/anomalyco/opencode/issues/42083) | GitHub Copilot provider shows zero models | Auth succeeds but `model_picker_enabled: false` for all Copilot models; `opencode models github-copilot` returns "Provider not found." | 8 comments · 2 👍 — open |
| [#25129](https://github.com/anomalyco/opencode/issues/25129) | Thinking mode stuck in infinite repetition loop | Qwen 3.6 Pro outputs repeated `!!!!!!!` or `...` indefinitely in thinking mode, requiring a model swap to recover. | 7 comments · 4 👍 — open |
| [#38791](https://github.com/anomalyco/opencode/issues/38791) | Run loop never exits with non-time-sortable message IDs | Third-party imported sessions can trap `SessionPrompt.runLoop` indefinitely because ID comparison is string-based, not numeric. | 6 comments · 0 👍 — open |
| [#41518](https://github.com/anomalyco/opencode/issues/41518) | gpt-5.6-luna returns 403 via OpenCode Go relay | Region-restriction 403 from upstream when accessing `gpt-5.6-luna` through the Go relay proxy. | 6 comments · 0 👍 — open |
| [#37489](https://github.com/anomalyco/opencode/issues/37489) | Context cache invalidation causes performance drops | Switching modes or during compaction invalidates context cache, causing noticeable latency with local LLMs (vLLM, Ollama). | 5 comments · 1 👍 — open |
| [#42668](https://github.com/anomalyco/opencode/issues/42668) | Web sidebar shows "no sessions" on Windows | TUI-created sessions don't appear in the web UI sidebar on native Windows; F5 refresh loses web-created sessions. | 2 comments · 0 👍 — open |
| [#42657](https://github.com/anomalyco/opencode/issues/42657) | TUI lag with multi-subagent sessions (97% CPU) | 2–4 concurrent subagents cause 1–3s input latency and spinner stutter across Warp, Windows Terminal, and WezTerm. | 2 comments · 0 👍 — open |

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#42684](https://github.com/anomalyco/opencode/pull/42684) | Compare ID timestamps numerically in `isAfter()` | Bug fix | Fixes the 48-bit overflow by switching from lexicographic to numeric timestamp comparison in `MessageV2.latest()`. Directly addresses #42608. |
| [#42685](https://github.com/anomalyco/opencode/pull/42685) | Re-query terminal palette on focus for system theme | Bug fix | Listens for renderer focus events to refresh the system theme palette, resolving stale colors inside `herdr` and other multiplexers that don't send `\e[?997` reports. |
| [#42683](https://github.com/anomalyco/opencode/pull/42683) | Search all agents for configured color in TUI | Bug fix | Agent color lookups now include subagents, fixing silently dropped colors when a subagent name isn't in the visible-agents list. |
| [#42682](https://github.com/anomalyco/opencode/pull/42682) | Keep queued work parked after interrupt | Bug fix | `session.interrupt?continue=true` now resumes only steering input from the interrupted intent; explicitly queued next-turn work stays parked until a full wake/resume. |
| [#42681](https://github.com/anomalyco/opencode/pull/42681) | Show window on `did-finish-load` fallback for Wayland | Bug fix | Linux-only fallback that reveals the Electron window on `did-finish-load`, addressing Wayland sessions where the window never appears. |
| [#42680](https://github.com/anomalyco/opencode/pull/42680) | Share session model requests | Refactor | Routes durable Session steps and transient `session.generate` calls through a single `SessionModelRequest.prepare` boundary, ensuring consistent context-hook reconciliation and header injection. |
| [#42673](https://github.com/anomalyco/opencode/pull/42673) | Ignore stray releases on new-session controls | Bug fix | Prevents accidental session creation when a text-selection drag is released over the tab-strip `+` button. |
| [#42646](https://github.com/anomalyco/opencode/pull/42646) | Preserve transparent tab backgrounds | Bug fix | Restores transparent terminal backgrounds beneath the session tab strip instead of replacing them with a fixed alpha shadow. |
| [#42662](https://github.com/anomalyco/opencode/pull/42662) | Fail loudly on MCP server config missing `type` | Bug fix | MCP configs copied from Claude Code often lack `type`/`enabled` fields; this PR now errors clearly instead of failing silently. Closes #41229. |
| [#42663](https://github.com/anomalyco/opencode/pull/42663) | Persist web search provider selection | Feature | Web search provider consent is now stored in the first file-backed config document rather than transient KV state, making the choice durable across restarts. |

---

## 5. Feature Request Trends

- **Local model auto-discovery:** Issue #27553 and PR #27554 continue to push for automatic model listing from OpenAI-compatible providers (`/v1/models`) and LAN/mDNS discovery, eliminating manual `opencode.json` entries for Ollama, LM Studio, and llama-swap.
- **Ollama Cloud authentication:** Issue #4581 requests a native `opencode auth login` flow for Ollama Cloud, currently only accessible through a local/server relay.
- **Runtime permission toggling:** Issue #41909 proposes an `/approve on|off` command (inspired by Claude Code) to toggle step-by-step permission approval without restarting the session.
- **Nara router provider:** Issue #42664 requests adding support for the Nara router (`router.bynara.id`) as a built-in provider.
- **Web search tool parity:** Issue #40568 highlights that the `websearch` tool is absent on Go models unless the undocumented `OPENCODE_ENABLE_EXA=1` env var is set — users expect feature parity across providers.

---

## 6. Developer Pain Points

1. **Session ID wraparound breaking history:** The 48-bit ID overflow (#42608, #38791) is a systemic issue affecting any session created before August 2023, and any imported sessions with non-chronological IDs. The fix is incoming but signals a deeper vulnerability in ID scheme assumptions.
2. **Free-tier quota surprises:** Multiple users (#42013, #42385, #42215) report hitting `FreeUsageLimitError` or 429s shortly after the stated daily reset, suggesting the reset logic or caching layer has edge-case bugs.
3. **Provider model visibility gaps:** GitHub Copilot (#42083) and GPT-5.6-Luna via Go relay (#41518) return empty or blocked model lists despite successful auth, indicating provider integration test coverage is thin.
4. **TUI reactivity under load:** Multi-subagent sessions (#42657) and thinking-mode infinite loops (#25129) both point to the render thread being a bottleneck — high CPU on the TUI thread degrades the experience across terminal emulators.
5. **Cross-platform UI inconsistencies:** Desktop layout regressions (#36997), Windows web-sidebar session visibility (#42668), and Wayland window focus (#42681) suggest platform-specific regression testing is insufficient for the new layout design.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-15

## 1. Today's Highlights

Pi v0.84.2 landed with fullscreen transcript search and configurable default tools, while a wave of closes addressed Windows/WSL login pain, clipboard failures on VTE terminals, and provider-specific edge cases. The community is heavily focused on improving provider compatibility (new SiliconFlow, ChatGPT image gen, Anthropic Vertex, and Bedrock Mantle providers in flight) and stabilizing the TUI under long streaming sessions.

---

## 2. Releases

**v0.84.2** — Notable additions:
- **Fullscreen transcript search** — Search and navigate matches in the TUI fullscreen viewport. [Keybindings docs](https://github.com/earendil-works/pi/blob/v0.84.2/packages/coding-agent/docs/keybindings.md#tui-fullscreen-viewport)
- **Configurable default tools** — Customize which tools are available at session startup.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 | Why it matters |
|---|-------|--------|----------|-----|----------------|
| [#7547](https://github.com/earendil-works/pi/issues/7547) | How do you use Pi on Windows? | OPEN | 27 | 1 | Large Windows dev population; the thread surfaces fragmentation across WSL, native, and alternative runtimes — core team needs signal on where to invest. |
| [#6187](https://github.com/earendil-works/pi/issues/6187) | Pi login hangs in WSL after GitHub Copilot device auth | CLOSED | 26 | 0 | WSL + browser-based OAuth is a common combo; the client fails to detect completion and hangs indefinitely. |
| [#5223](https://github.com/earendil-works/pi/issues/5223) | Anthropic thinking blocks cause 400 with Opus 4.8 | CLOSED | 17 | 6 | Multi-turn Claude sessions with adaptive `high` reasoning break mid-session — high impact for power users. |
| [#5023](https://github.com/earendil-works/pi/issues/5023) | Terminal scrolls to beginning without reason | CLOSED | 12 | 2 | Random, non-deterministic scroll behavior during model streaming disrupts workflow. |
| [#6665](https://github.com/earendil-works/pi/issues/6665) | TUI pins a full core while streaming | OPEN / In progress | 12 | 3 | Uncached `Intl.Segmenter` + per-chunk Markdown rebuild causes 100% single-core usage during long sessions. |
| [#7850](https://github.com/earendil-works/pi/issues/7850) | Copilot login fails with 429 for orgs with many models | CLOSED | 9 | 7 | Enterprise orgs with 20+ Copilot models hit rate limits during device auth — 7 upvotes signal broad pain. |
| [#8096](https://github.com/earendil-works/pi/issues/8096) | Z.AI defaults reference removed model `glm-5.1` | CLOSED | 5 | 1 | Stale catalog entry causes broken defaults out of the box for Z.AI users. |
| [#8092](https://github.com/earendil-works/pi/issues/8092) | Extension loader fails with pnpm isolated layout | CLOSED | 5 | 0 | pnpm's symlinked `node_modules` layout breaks jiti's resolver for extension dependencies. |
| [#8010](https://github.com/earendil-works/pi/issues/8010) | Copilot account login fails with 429 | CLOSED | 4 | 2 | Another 429 angle on Copilot auth — reinforces that login reliability needs systematic attention. |
| [#7787](https://github.com/earendil-works/pi/issues/7787) | `PI_*` guideline triggers unnecessary permission prompts | OPEN | 3 | 0 | The default bash tool guideline tells models to inspect `PI_*` env vars, causing spurious `env` calls on unrelated tasks. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#8149](https://github.com/earendil-works/pi/pull/8149) | Omit invalid OpenAI session header | CLOSED | Strips `session_id` HTTP header (which contains an underscore) to avoid HTTP/1 proxy rejection (Envoy `400 unexpected_underscore`). |
| [#8148](https://github.com/earendil-works/pi/pull/8148) | Scope `PI_*` guideline to session questions | CLOSED | Fixes [#7787](https://github.com/earendil-works/pi/issues/7787) — the bash tool now only surfaces the `PI_*` env inspection guideline when the model is explicitly asked about session context. |
| [#8146](https://github.com/earendil-works/pi/pull/8146) | Cap Baseten DeepSeek V4 Flash output at 384k | CLOSED | Baseten advertises 1M tokens but only serves 384k; requests above the cap fail. |
| [#8143](https://github.com/earendil-works/pi/pull/8143) | Fullscreen transcript window performance | CLOSED | Fullscreen sessions now keep the full active transcript (including pre-compaction history) while rendering only viewport-intersecting blocks with exact height measurement. |
| [#8139](https://github.com/earendil-works/pi/pull/8139) | ChatGPT OAuth image generation | CLOSED | Native image-generation transport reusing existing OpenAI Codex OAuth infrastructure — no separate API key needed. |
| [#8124](https://github.com/earendil-works/pi/pull/8124) | Route xAI through Responses API, default Grok 4.6 | OPEN | Switches xAI from completions to responses API and updates default model to Grok 4.6. |
| [#8120](https://github.com/earendil-works/pi/pull/8120) | Experimental append compaction | OPEN | New compaction mode that reuses the active system prompt, tools, and routing session so compacted prefixes can hit provider prompt caches. Enabled via `PI_EXPERIMENTAL=1`. |
| [#8119](https://github.com/earendil-works/pi/pull/8119) | Track Kimi cached tokens | OPEN | Kimi reports cache hits as top-level `usage.cached_tokens`; Pi now includes this in raw usage and applies it as cache-read input. |
| [#8110](https://github.com/earendil-works/pi/pull/8110) | Route TUI copy through host clipboard | CLOSED | Fixes [#7761](https://github.com/earendil-works/pi/issues/7761) — `"Copied!"` flash was a lie on VTE terminals and macOS Terminal.app that ignore bare OSC 52 sequences. Now delegates to the host clipboard API. |
| [#8113](https://github.com/earendil-works/pi/pull/8113) | SiliconFlow provider | CLOSED | New built-in provider (`siliconflow`) following existing moonshot/minimax patterns; international endpoint at `api.siliconflow.com/v1`. |

**Also noteworthy:**
- [#8012](https://github.com/earendil-works/pi/pull/8012) — Stop treating root `README.md`/`AGENTS.md` as broken skills
- [#8011](https://github.com/earendil-works/pi/pull/8011) — Fix single-edit input handling for OpenRouter `glm-5.2`
- [#8123](https://github.com/earendil-works/pi/pull/8123) — Fix `registerFlag()` type mismatch (boolean flags accepting string `"false"` defaults)
- [#5262](https://github.com/earendil-works/pi/pull/5262) — Anthropic Vertex provider (ongoing)
- [#6216](https://github.com/earendil-works/pi/pull/6216) — Amazon Bedrock Mantle OpenAI Responses provider (ongoing)
- [#8112](https://github.com/earendil-works/pi/pull/8112) — Realpath extension entries before jiti import (fixes pnpm layout issue)

---

## 5. Feature Request Trends

- **Provider expansion** — siliconFlow, ChatGPT image gen, Anthropic Vertex, and Bedrock Mantle all landed or are in progress; the community continues to push for broader provider coverage beyond the core OpenAI/Anthropic/Claude stack.
- **Compaction improvements** — Append-mode compaction (#8120) and per-model compaction profiles (#8133, closed) show sustained interest in smarter context management that preserves prompt-cache hits.
- **TUI UX hardening** — Fullscreen transcript search, accurate clipboard copy, command-autocomplete positioning (#8132), and skill-name autocomplete mid-prompt (#8144) reflect demand for a more polished interactive experience.
- **Session/extension ergonomics** — Atomic session-only model state for extensions (#8100), per-model compaction settings (#8133), and real fix for the `PI_*` guideline noise (#7787/#8148) indicate extension authors want finer-grained, less intrusive session control.

---

## 6. Developer Pain Points

1. **OAuth / login reliability** — Multiple 429 and hang issues around GitHub Copilot device auth (#6187, #7850, #8010), especially for enterprise orgs with many models. This is a recurring friction point.
2. **Windows & WSL fragmentation** — Issue #7547 captures the broader pain: too many ways to run Pi on Windows, making it hard for the team to prioritize fixes vs. delegating to docs/community.
3. **TUI stability under load** — Core-pinning during streaming (#6665), random terminal scroll jumps (#5023), and clipboard lies on VTE terminals (#7761/#8110) all point to TUI rendering and terminal integration as fragile areas.
4. **Provider-specific edge cases** — Stale model defaults (#8096), thinking-block format changes from Anthropic (#5223), Kimi cache-token reporting (#8075/#8119), and Baseten output-cap mismatches (#8146/#7850) show that provider compatibility requires continuous maintenance as upstream APIs evolve.
5. **Extension ecosystem tooling** — pnpm isolated layout breaking extension resolution (#8092/#8112) and flag-type mismatches (#8123) suggest the extension hosting and registration surface needs more robust type safety and package-manager agnosticism.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-15

## 1. Today's Highlights

The most significant update this cycle is the v0.21.12 release series, which introduces workspace file upload support in the Web Shell via drag-and-drop and the `@` file panel, plus a diff growth brake in autofix reviews to curb runaway patch accumulation. On the CI front, SWE-bench Verified end-to-end validation succeeded (1/1 resolved) in the latest DSW EAS run, while autofix received a deny-by-default footprint gate and positional window census for stricter policy enforcement.

---

## 2. Releases

- **v0.21.12** — Includes workspace file upload support for Web Shell and a diff growth brake in autofix reviews.
- **v0.21.11-nightly.20260815.c396fe3d12** — Autofix deny-by-default footprint gate and positional window censuses.
- **v0.21.12-preview.4 / .3** — Preview builds carrying the same Web Shell upload feature and standalone session target preservation fix.
- **dsw-eas-tb-e2e-20260814-r6** — Full E2E validation pipeline (Release → Actions → SWE-bench Verified 500 → Publisher → Terminal-Bench 2.0 → same Release). Benchmark reference: v0.21.2.

---

## 3. Hot Issues

1. **[P1] fix(serve): Preserve current session when large restore times out** [#8678](https://github.com/QwenLM/qwen-code/issues/8678) — Partially addressed and superseded; touches restore timeouts, attachment identity fencing, and late-result safety. 9 comments.

2. **[P2] tracking(serve): Bound multi-workspace daemon resource usage** [#8051](https://github.com/QwenLM/qwen-code/issues/8051) — The daemon currently limits count but not bytes for request bodies, WebSocket assembly, or other resource vectors. 9 comments, still open.

3. **[P1] refactor: core + CLI architecture review — 12 structural issues** [#4063](https://github.com/QwenLM/qwen-code/issues/4063) — Critical finding: the core type system is directly coupled to `@google/genai` across 136 files. 8 comments, 1 👍.

4. **[P1] security: read-only shell classifier auto-approves hidden command substitution** [#8582](https://github.com/QwenLM/qwen-code/issues/8582) — Both the AST-based classifier and the runtime substitution gate miss commands obfuscated by line continuation or `${var@P}`. 5 comments; closed.

5. **[P2] SDK Python rejects `permission_mode="auto"` although CLI supports it** [#9002](https://github.com/QwenLM/qwen-code/issues/9002) — Client-side validation blocks a value the CLI already accepts. 6 comments.

6. **[P2] Status line context usage % doesn't refresh after /compress** [#6806](https://github.com/QwenLM/qwen-code/issues/6806) — The footer remains stale until the next model request. 5 comments.

7. **[P1] Memory grows unboundedly during long sessions** [#2128](https://github.com/QwenLM/qwen-code/issues/2128) — Root cause identified: `useHistoryManager.history` accumulates without limit over tens of hours. 4 comments.

8. **[P3] autofix: PAT-bearing jobs share a host with untrusted branch code** [#9089](https://github.com/QwenLM/qwen-code/issues/9089) — Requires runner-level isolation that cannot be solved from within a GitHub Actions step. 3 comments.

9. **[P2] Main CI failed: E2E Tests** [#9143](https://github.com/QwenLM/qwen-code/issues/9143) — Pre-test CI failure on `main`; tracked per commit. 7 comments.

10. **[P2] bug(core): Shell ignores `tools.truncateToolOutputThreshold`** [#8922](https://github.com/QwenLM/qwen-code/issues/8922) — Shell hard-codes a 30,000-char budget, overriding the user config. Closed.

---

## 4. Key PR Progress

1. **feat(web-shell): workspace file uploads via drag-and-drop / `@` panel** [#8874](https://github.com/QwenLM/qwen-code/pull/8874) — Core UX feature for v0.21.12, with progress tracking.

2. **feat(review): repair seven pipeline defects found by live runs** [#9175](https://github.com/QwenLM/qwen-code/pull/9175) — Structural and functional fixes discovered through end-to-end review pipeline runs.

3. **feat(review): wire `--resume` through `/review`, `review run`, and CI retry** [#9153](https://github.com/QwenLM/qwen-code/pull/9153) — Enables resuming interrupted reviews from disk state.

4. **feat(review): transfer per-file content verdicts across rebases** [#9191](https://github.com/QwenLM/qwen-code/pull/9191) — Carries incremental review state forward when PRs are rebased.

5. **feat(review): content-anchored incremental rounds for the local review-fix loop** [#9190](https://github.com/QwenLM/qwen-code/pull/9190) — Eliminates full-tree re-capture in local fix loops, saving significant tokens.

6. **feat(review): deterministic incremental plans, widened one import hop** [#9188](https://github.com/QwenLM/qwen-code/pull/9188) — Replaces informal incremental prose with executable review plans.

7. **feat(dingtalk): support outbound file delivery** [#9167](https://github.com/QwenLM/qwen-code/pull/9167) — Native file send via DingTalk media API when the agent emits a local-file marker.

8. **feat(chrome): Qwen WebBridge direct browser control** [#8707](https://github.com/QwenLM/qwen-code/pull/8707) — Exposes Kimi WebBridge-compatible endpoints (`/command`, `/status`) with 17 actions and task-scoped ownership tracking.

9. **feat(core): resolve model modalities from API metadata** [#8529](https://github.com/QwenLM/qwen-code/pull/8529) — Pulls missing input modalities from models.dev with a valid disk cache, no cold-start wait.

10. **feat(review): adopt a round-aware convergence posture for posted findings** [#9118](https://github.com/QwenLM/qwen-code/pull/9118) — Raises the posting bar as review rounds accumulate, encouraging the review→fix→re-review loop to converge naturally.

---

## 5. Feature Request Trends

- **Incremental & resumable code review** — A cluster of PRs (#9190, #9153, #9191, #9118, #9188) points to a major push toward token-efficient, rebase-aware, resumable review workflows.
- **Web Shell maturity** — File upload (#8874), DingTalk outbound delivery (#9167), HTML export refactor (#9186), and Electron desktop evaluation (#9168) signal sustained investment in the Web Shell as a multi-modal work surface.
- **Multi-workspace daemon governance** — Resource bounding (#8051) and CLI architecture decoupling (#8084) reflect an ongoing push toward production-grade daemon scalability.
- **Browser automation** — Qwen WebBridge (#8707) extends direct Chromium control beyond the sandbox, aligned with the emerging agent-driven browser use case.

---

## 6. Developer Pain Points

- **Session memory leaks** — Unbounded UI history growth (#2128) and restore-timeout session loss (#8678) remain top-of-mind for long-running agents.
- **Shell security gaps** — The read-only classifier bypass via hidden command substitution (#8582) and the `truncateToolOutputThreshold` being ignored (#8922) suggest the security review pipeline needs deeper automated coverage.
- **SDK / CLI parity gaps** — `permission_mode="auto"` rejected by the Python SDK but accepted by CLI (#9002) and status-line not refreshing post-compress (#6806) are recurring quality-of-life friction.
- **CI flakiness & review pipeline fragility** — Repeated E2E CI failures (#9143, #9160, #9159) and the need for a determinism gate on sandboxed verification (#9130) indicate the test infra is a persistent source of developer drag.
- **Architecture debt** — The `@google/genai` coupling across 136 files (#4063) and cyclic `utils/` imports (#9146) are flagged as P0 structural blockers that slow forward progress.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / CodeWhale Community Digest — 2026-08-15

## 1. Today's Highlights

CodeWhale v0.9.8 shipped as the final release before the legacy `deepseek-tui` npm package is fully deprecated, with `codewhale` as the canonical command and package name. The project saw a burst of 7 closed PRs in the last 24 hours addressing critical bugs — session-index data loss, webhook panics, stale write-claims, and CI test regressions — while maintaining an active issue pipeline of 50 open items.

## 2. Releases

**v0.9.8** — The current release marks the end of the legacy `deepseek-tui` lifecycle. The `codewhale` command, npm package, and release assets are now the sole public product from Shannon Labs. The old `deepseek-tui` npm package is deprecated and will receive no further releases. Users upgrading from v0.8.x should migrate to the `codewhale` CLI.

## 3. Hot Issues

1. **[#3192] Registry listing for Zed integration** — Being listed on the [agentclientprotocol/registry](https://github.com/agentclientprotocol/registry) would make discovery and installation in Zed significantly easier. 13 comments; strong community interest in editor integration.
   → https://github.com/Hmbown/CodeWhale/issues/3192

2. **[#1004] `/dryrun` — preview chat completion before sending** — Developers iterating on long V4 Pro turns (heavy system prompts, cached repos, tool definitions) cannot inspect the exact payload without incurring cost. A dry-run flag would eliminate this recurring friction. 9 comments.
   → https://github.com/Hmbown/CodeWhale/issues/1004

3. **[#5324] Simplify the 32-field `agent` tool schema** — The model-facing schema has zero required fields and serves eight actions from a single bloated schema, causing models to error on it. The fix is a prerequisite for several other tooling improvements. 8 comments.
   → https://github.com/Hmbown/CodeWhale/issues/5324

4. **[#4326] RSS spike after cancelling 32-worker storms** — Post-cancel memory doesn't settle; distinguishing allocator high-water retention from real leaks is needed. Critical for users running high-fan-out sub-agent workloads. 6 comments.
   → https://github.com/Hmbown/CodeWhale/issues/4326

5. **[#5355] v0.9.8 Known issues basket** — Carried-over flaky tests from v0.9.7: `exec_persistent_service` parallel-load flakes and a custom-endpoint restoration issue. Maintainer-curated transparency. 2 comments.
   → https://github.com/Hmbown/CodeWhale/issues/5355

6. **[#5374] Agent writing corruption on macOS** — Terminal output renders garbled during agent writes, making the TUI unusable. Affects real users daily; 4 comments and rising urgency.
   → https://github.com/Hmbown/CodeWhale/issues/5374

7. **[#5322] Output area no longer fills wide terminals (regression from v0.8.65)** — Wide-display users see cramped text with unused whitespace. A clear UX regression that's easy to reproduce. 3 comments.
   → https://github.com/Hmbown/CodeWhale/issues/5322

8. **[#5340] `doctor` stuck on `needs action` after upgrade** — First-run and update-checkpoint states permanently report incomplete even after fresh onboarding. Blocks new-user activation post-upgrade. 3 comments.
   → https://github.com/Hmbown/CodeWhale/issues/5340

9. **[#5350] Third-party model config templates** — Users configuring OpenCode Zen, Agnes, Sensenova, and other providers must manually fill Base URL, model name, and key env vars with no built-in docs. Pre-built templates would cut setup time from minutes to seconds. 2 comments (bilingual).
   → https://github.com/Hmbown/CodeWhale/issues/5350

10. **[#2327] Unofficial VS Code extensions using the CodeWhale name** — Two marketplace extensions (`HengQuWorld.brotherwhale-vscode`, `HaiTaoJiang.codewhale-vscode`) are publishing under the project name without authorization. Community concern over confusion and potential security risk. 2 comments.
    → https://github.com/Hmbown/CodeWhale/issues/2327

## 4. Key PR Progress

1. **[#5382] Serialize session-index writes** — Fixes silent JSONL data loss when concurrent `StateStore` clones race on `session_index.jsonl` rewrite. Directly closes #5380. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5382

2. **[#5381] Do not panic on webhook HTTP client build failure** — Replaces `.expect()` in `WebhookHookSink::new` with graceful error handling instead of hard-crashing the host. Closes #5379. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5381

3. **[#5384] Re-pin provider-count assertions to v0.9.8 registry** — Updates two hardcoded test assertions (43→45 registry kinds, 38→40 catalog kinds) that broke `main` after the v0.9.8 provider expansion. Closes #5383. ✅ Open
   → https://github.com/Hmbown/CodeWhale/pull/5384

4. **[#5378] Re-pin thinking-ladder test assertions** — Fixes nine macOS/Windows tests asserting stale pre-ladder vocabulary after commit `6f6c35183`. Pure test fix, no production changes. Closes #5377. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5378

5. **[#5365] First-class local DS4 setup** — Adds a prefilled keyless loopback preset for DwarfStar (DS4) via `/setup provider ds4` and the `D` shortcut, reusing the OpenAI-compatible transport. No new protocol adapter needed. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5365

6. **[#5353] Model guardian tier for Auto-Review (v0.9.8)** — Auto-Review now escalates to a one-shot model guardian instead of silently blocking, combining deterministic floor checks with model-assisted fallback. Aligns with Codex/Kimi reviewer semantics. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5353

7. **[#5339] Suppress child-owned shell completions** — Filters background shell completion events from child sub-agents out of the parent model stream while preserving unowned parent completions. Closes #5325. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5339

8. **[#5369] Degrade Moonshot schemas instead of refusing conditionals** — Addresses the #5324 prerequisite by relaxing schema validation for Moonshot-compatible providers rather than rejecting conditional fields outright. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5369

9. **[#5376] Keep internal runtime events out of session peek** — Runtime-internal events were leaking into the user-visible session peek output. Filters them out for cleaner diagnostics. Closes #5375. ✅ Merged
   → https://github.com/Hmbown/CodeWhale/pull/5376

10. **[#5368] Confine unguarded tests to isolated state root** — Fixes four tests that were touching real environment paths instead of the test-isolated state root, addressing a "lock-holder trust hole." Closes part of #5359. ✅ Merged
    → https://github.com/Hmbown/CodeWhale/pull/5368

## 5. Feature Request Trends

- **Editor & registry integration** — Users want CodeWhale discoverable via the Agent Client Protocol registry for seamless Zed and editor installation (#3192).
- **Third-party model ease-of-setup** — Repeated requests for pre-built provider templates (OpenCode Zen, Agnes, Sensenova, Moonshot) with auto-filled URLs and one-click connection testing (#5350, #5324).
- **Plugin ecosystem maturation** — Vision for a Kimi-level federated plugin marketplace with security foundations already in place (#5311).
- **Dry-run & payload inspection** — Developers need to preview completions before sending, especially for expensive V4 Pro turns with heavy context (#1004).
- **Update UX** — Proactive update notices and one-chord update-and-relaunch from within the TUI (#5053).

## 6. Developer Pain Points

- **Session data integrity** — Concurrent `StateStore` clones caused silent JSONL write loss (#5380), and stale write-claims from closed sessions block new sub-agents (#5372). Both were critical and just fixed.
- **CI flakiness post-release** — v0.9.8 landed with broken test assertions (provider counts, thinking-ladder vocabulary) that kept `main` red across platforms. Regression pinning is now a recurring need (#5383, #5377).
- **Schema bloat breaking models** — The 32-field `agent` tool schema with zero required fields is too complex for models to parse reliably, causing tool-call errors (#5324).
- **Memory retention after cancellation** — High-fan-out worker storms (32 workers) leave elevated RSS post-cancel; distinguishing allocator watermark from real leaks remains unresolved (#4326).
- **Dead-code wall** — 464 `#[allow(dead_code)]` attributes across 143 files prevent the compiler from surfacing drift, masking technical debt (#4785).
- **macOS rendering corruption** — Agent output renders garbled on macOS terminals, a blocking usability bug (#5374).
- **Webhook hard-crash** — HTTP client build failures in `WebhookHookSink::new` panicked instead of failing gracefully (#5379).

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*