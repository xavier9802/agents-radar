# AI CLI Tools Community Digest 2026-08-22

> Generated: 2026-08-22 01:36 UTC | Tools covered: 10

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
**Date: 2026-08-22**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem is in a phase of rapid maturation, with active nightly and alpha release cycles across most major projects. Community-driven feedback is increasingly shaping roadmap priorities—particularly around multi-agent reliability, cost transparency, and platform-specific stability. The competitive landscape is shifting from raw model capability toward developer experience, session resilience, and enterprise-grade security controls. Open-source and proprietary tools alike are converging on similar architectural patterns: sub-agent orchestration, MCP integration, and sandboxed execution.

---

## 2. Activity Comparison

| Tool | Issues (Open) | PRs (Updated) | Releases |
|------|:---:|:---:|:---|
| **Claude Code** | ~12 | 0 | v2.1.239 |
| **OpenAI Codex** | ~10 | 9 | `0.150.0-alpha` series (4 pre-releases), Desktop `26.818.x` |
| **Gemini CLI** | ~10 | 10 | v0.56.0-nightly.20260822 |
| **GitHub Copilot CLI** | ~10 | 0 | v1.0.81-7 |
| **Kimi Code CLI** | ~1 | 1 | — |
| **OpenCode** | ~10 | 9 | v1.18.21, v1.18.20 |
| **Pi** | ~9 | 9 | — |
| **Qwen Code** | ~10 | 10 | v0.21.14-nightly |
| **DeepSeek TUI** | ~10 | 10 | — |

**Notable:** Qwen Code, Gemini CLI, and DeepSeek TUI show the highest combined issue + PR velocity. Kimi Code CLI has minimal reported activity but a critical unreleased bug. OpenAI Codex leads in release frequency with rolling alpha builds.

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Sub-agent lifecycle & reliability** | Claude Code, OpenAI Codex, Gemini CLI, OpenCode, DeepSeek TUI | Agents correctly reporting completion/failure states; preventing orphaned tasks and silent quota drain |
| **Custom-provider / BYOK parity** | OpenAI Codex, GitHub Copilot CLI, Pi, OpenCode | Unified model switching across hosted and self-hosted providers; `apply_patch`-style edit tools for non-OpenAI backends |
| **MCP integration robustness** | GitHub Copilot CLI, OpenCode, Qwen Code | BigInt serialization crashes, late-connecting server handling, stale config reload, tool definition bloat |
| **Windows platform stability** | Claude Code, OpenAI Codex, GitHub Copilot CLI, Qwen Code | Session restore, process locking, MCP STDIO transport, IME rendering, path quoting |
| **Cost & token optimization** | Claude Code, Pi, OpenCode | Per-model compaction profiles, prompt caching support, MCP lazy-loading, accurate multi-model cost aggregation |
| **Session management** | GitHub Copilot CLI, Pi, OpenCode | Session branching, resume from crash, unarchive/restore, parallel subagent event handling |
| **External supervision & automation** | Gemini CLI, DeepSeek TUI | Lifecycle event outboxes, per-session control sockets, `/relaunch` support, CI harness integration |
| **Sandboxing & security hardening** | Gemini CLI, OpenAI Codex, OpenCode | Seatbelt sandbox isolation, container socket denial, port-based false-auth filtering |

---

## 4. Differentiation Analysis

| Dimension | Tools |
|-----------|-------|
| **Enterprise security focus** | Claude Code (CVP org blocks, cost estimates), OpenCode (portable shell hardening, MCP review) |
| **Rapid iteration / bleeding-edge** | OpenAI Codex (rolling alpha), Gemini CLI (nightly builds with security patches) |
| **Benchmark-driven development** | Qwen Code (SWE-bench Verified + Terminal-Bench smoke tests in CI) |
| **Multi-modal expansion** | DeepSeek TUI (vision model request #5541), Gemini CLI (browser agent) |
| **Open-source extension model** | Pi (extension factory with exclusion support, Radius artifacts), OpenCode (MCP ecosystem) |
| **Review-loop specialization** | Qwen Code (dedicated `review-agent` subagent type, Aone Code support, convergence advisories) |
| **Remote control / mobile** | OpenAI Codex (Android/iOS Remote Control, dominant pain point), Claude Code (Android Remote Control bypass) |
| **Privacy & data controls** | DeepSeek TUI (`.codewhaleignore` parity with `.cursorignore`), Gemini CLI (deterministic redaction) |

---

## 5. Community Momentum & Maturity

| Signal | Interpretation |
|--------|---------------|
| **Gemini CLI** — Nightly releases with security hardening (Seatbelt sandbox), active PR pipeline (10 PRs), eval infrastructure being built | High momentum, early maturity; Google is actively investing in measurable quality assurance |
| **Qwen Code** — 10 PRs/24h, benchmark validation in CI, rapid Aone Code feature closure | Strong engineering velocity; Alibaba is shipping aggressively with enterprise review workflows |
| **DeepSeek TUI** — 10 PRs covering infrastructure (outbox, control socket, `/relaunch`), sub-agent bug fixes | Rapid iteration from a smaller team; supervised-operation focus signals targeting power-user/CI workflows |
| **OpenAI Codex** — Rolling alpha with 9 PRs on Guardian V2, Bedrock support, executor semantics | Enterprise-grade security is the current priority; multi-provider parity still lagging |
| **Claude Code** — Steady releases, community issues dominant (Windows bug 63 👍, cyber-safeguard blocks 133 comments) | Mature product with an active enterprise user base; infrastructure reliability is the key challenge |
| **GitHub Copilot CLI** — Session-restore feature shipped, but BYOK and ACP-mode bugs persist | Growing user base; multi-model support and ACP spec compliance are the next hurdles |
| **OpenCode** — Active desktop and core fixes, MCP tool bloat addressed | Mid-maturity; session lifecycle and provider compatibility are the open frontiers |
| **Pi** — Compaction bugs (#6879, 17 👍) remain open, keyboard regressions recur | Smaller community but high engagement on reliability issues; TUI abstraction layer needs investment |
| **Kimi Code CLI** — Minimal reported activity, one critical unreleased bug | Early-stage or lower-activity community; reliability concern around background subagent lifecycle is a trust risk |

---

## 6. Trend Signals

1. **Sub-agent reliability is the #1 trust barrier.** Across Gemini CLI, DeepSeek TUI, OpenCode, and Claude Code, silent failures, false success reports, and orphaned tasks are the most damaging bugs. Tools that solve this (e.g., DeepSeek's lifecycle outbox, Qwen's `review-agent` isolation) will gain an edge in production adoption.

2. **MCP is becoming a fragmentation risk.** Every tool is integrating MCP, but serialization bugs (BigInt in Copilot CLI), tool-definition bloat (OpenCode), and late-connecting server edge cases (Copilot CLI) suggest the protocol maturity gap is real. Lazy-loading and graceful degradation will be differentiators.

3. **Windows is the canary platform.** Persistent regressions across Claude Code, OpenAI Codex, GitHub Copilot CLI, and Qwen Code indicate that Windows desktop environments introduce unique path, process-locking, and terminal-protocol challenges that cross-platform teams underinvest in.

4. **Cost transparency is table-stakes.** Claude Code's US-premium cost estimates, Pi's prompt-caching gap (2.5× penalty), and OpenCode's multi-model cost tracking show that users now expect per-request cost visibility. Tools that bury this will face adoption friction.

5. **External supervision is the next UX frontier.** DeepSeek TUI's control socket, Gemini CLI's event outbox, and Qwen Code's convergence advisories all point toward a shift from interactive-only CLIs to CI/automation-integrated agents. This trend will accelerate as multi-agent workflows become standard.

6. **Provider-agnostic parity is incomplete.** Custom-provider subagent orchestration (Codex #17598), BYOK model switching (Copilot #3709), and Bedrock routing gaps (OpenCode) indicate that the multi-provider promise is not yet realized. Tools that close this gap will capture enterprise users managing heterogeneous model portfolios.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-22*

---

## 1. Top Skills Ranking

| # | Skill / PR | Functionality | Discussion Highlights | Status |
|---|-----------|--------------|----------------------|--------|
| 1 | **#1298** — `fix(skill-creator): run_eval.py always reports 0% recall` | Fixes the skill-creator's evaluation pipeline; `run_eval.py` (and downstream `run_loop.py`, `improve_description.py`) was reporting `recall=0%` on every description, breaking the optimization loop. | 10+ independent reproductions reported; author also fixed Windows stream reading, trigger detection, and parallel workers in the same PR. | 🟡 Open |
| 2 | **#492** — *Security: Community skills under `anthropic/` namespace* | Not a skill PR — a **security issue** flagging community skills impersonating official Anthropic skills, enabling trust-boundary abuse when users grant elevated permissions. | 43 comments, 2 👍; highlights a systemic governance gap in the namespace. | 🟡 Open |
| 3 | **#228** — *Enable org-wide skill sharing in Claude.ai* | Feature request for built-in organizational skill sharing; currently users must manually distribute `.skill` files via Slack/Teams. | 16 comments, 8 👍; strong consensus for a shared skill library or direct sharing link. | 🟡 Open |
| 4 | **#514** — `document-typography` | Typographic quality control for AI-generated documents: fixes orphan word wrap, widow paragraphs, and numbering misalignment. | Active discussion on practical utility; addresses a universal pain point in document generation. | 🟡 Open |
| 5 | **#1367** — `self-audit` skill (v1.3.0) | Mechanical verification + four-dimension reasoning quality gate for AI output before delivery; works across any project/tech stack. | Follows up on the community [Proposal #1385] for a reasoning quality gate pipeline. | 🟡 Open |
| 6 | **#568** — `servicenow` platform skill | Broad ServiceNow platform assistant covering ITSM, ITOM, ITAM/SAM, FSM, SPM, SecOps, CSDM, and IntegrationHub. | 0 comments but 8-12 August update suggests active iteration; wide scope attracts enterprise interest. | 🟡 Open |
| 7 | **#723** — `testing-patterns` | Comprehensive testing skill: Testing Trophy model, AAA unit tests, React Testing Library, edge-case patterns. | Notable for bridging testing philosophy with practical implementation patterns. | 🟡 Open |
| 8 | **#1099** / **#1050** — `skill-creator` Windows fixes | Two complementary Windows compatibility PRs: one fixes subprocess pipe crashes on `run_eval.py`, the other fixes `claude.cmd` not found via `subprocess.Popen`. | Merged into the same fix cluster as #1298; critical for Windows skill authors. | 🟡 Open |

---

## 2. Community Demand Trends

From the issues data, the most-anticipated Skill directions are:

- **Quality Gates & Self-Audit** — Demand for pre-delivery verification skills (reasoning quality, mechanical checks, adversarial review) is the strongest signal (#1367, #1385, #83).
- **Enterprise Platform Skills** — ServiceNow (#568), SAP-RPT-1-OSS (#181), and SharePoint/SecOps (#1175) indicate growing demand for vertical-domain skills beyond general coding.
- **Org-Wide Skill Sharing** — Issue #228 (8 👍) and duplicate-skills friction (#189, 9 👍) point to a need for governance tooling around skill distribution.
- **Security & Trust Boundaries** — Namespace impersonation (#492) and SPO permission-in-skill concerns (#1175) signal a demand for secure skill design patterns.
- **Token Efficiency** — The `claude-api` skill eagerly injecting ~156k tokens (#1487) and verbose skill-creator docs (#202) reflect community frustration with context-window waste.
- **Testing & Documentation Quality** — `testing-patterns` (#723), `document-typography` (#514), and docx whitespace fixes (#12, #541) show demand for domain-specific quality skills.

---

## 3. High-Potential Pending Skills

These active-comment PRs are not yet merged and may land soon:

| PR | Skill | Why It May Land Soon |
|----|-------|---------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval fix | Critical bug fix for the skill-creation pipeline itself; directly blocks #556 reproduction. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` | Builds on a well-discussed proposal (#1385); practical utility across all project types. |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Enterprise-grade, comprehensive scope; last updated Aug 12 with active iteration. |
| [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | Solves a universal document-generation problem; clean, focused scope. |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Full-stack testing coverage is missing from current skill offerings. |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills that address the security and quality governance gap; directly relevant to #492. |
| [#1099](https://github.com/anthropics/skills/pull/1099) / [#1050](https://github.com/anthropics/skills/pull/1050) | `skill-creator` Windows compat | Platform-specific bug fixes that unblock a significant contributor segment. |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **quality assurance and governance layer skills** — self-auditing, security analysis, and reasoning quality gates — alongside practical domain-specific skills for enterprise platforms, driven by the emergence of trust-boundary vulnerabilities and context-window waste as systemic pain points.

---

*Report generated by Agnes (Sapiens AI) from `anthropics/skills` GitHub data as of 2026-08-22.*

---



# Claude Code Community Digest — 2026-08-22

---

## 1. Today's Highlights

Claude Code **v2.1.239** shipped with cost-estimate adjustments for US-only inference workspaces and expanded fullscreen renderer availability to Bedrock, Vertex, and Foundry setups. Meanwhile, the community remains focused on cyber-safeguard false positives (133+ comments on CVP org blocks) and a persistent Windows Desktop relaunch bug (63 👍).

---

## 2. Releases

### v2.1.239
- Cost estimates (`/cost`, status line, `--max-budget-usd`) now account for the **1.1× US-only-inference premium** in data-residency workspaces.
- One-time **fullscreen renderer offer** extended to Bedrock, Vertex, Foundry, and other previously excluded environments.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved org still receives cyber-safeguard blocks | 133 | 21 | Approved organizations are being blocked anyway; Verification Portal shows "Under review" despite prior approval. High-impact for enterprise users. |
| [#42776](https://github.com/anthropics/claude-code/issues/42776) | Desktop fails to relaunch on Windows (orphaned process lock) | 128 | 63 | Long-standing Windows Desktop bug; orphaned process file locks prevent relaunch. Widely affected Windows users. |
| [#19649](https://github.com/anthropics/claude-code/issues/19649) | Model overuses Bash tools (sed/grep) instead of builtins | 45 | 101 | Core model behavior issue — excessive shell commands instead of native Read/Grep tools degrades performance and UX. |
| [#62699](https://github.com/anthropics/claude-code/issues/62699) | Text cannot be copied from Claude Code output | 41 | 67 | Basic UX blocker in terminal TUI; `Ctrl+Shift+C` and right-click both fail. |
| [#24968](https://github.com/anthropics/claude-code/issues/24968) | Accessibility: turn duration verbs customizable | 17 | 58 | Requests configurable phrasing for accessibility-aware users; reflects growing A11y demand. |
| [#76187](https://github.com/anthropics/claude-code/issues/76187) | Cowork (Windows): project folders never mount in new sessions | 12 | 1 | Regression since July 8 update; nested connected folders silently detach, breaking Cowork workflows. |
| [#77830](https://github.com/anthropics/claude-code/issues/77830) **✓ Closed** | Commit attribution trailer ignores `attribution: {commit: ""}` | 9 | 1 | When commit attribution is disabled, a `Claude-Session:` trailer was still injected into Bash tool descriptions. Now closed. |
| [#82967](https://github.com/anthropics/claude-code/issues/82967) | GPU process crashes with Browser tools, corrupts app package | 9 | 1 | `browser:open_site` intermittently crashes the Electron GPU process, requiring full reinstall. |
| [#86617](https://github.com/anthropics/claude-code/issues/86617) | PR status icons missing from session list after update | 8 | 5 | Post-update regression on macOS; merged/open PR badges no longer render in the sidebar. |
| [#88041](https://github.com/anthropics/claude-code/issues/88041) | Auto-mode "bashFirst" prompt instructs sed/heredoc edits over Edit/Write tools | 5 | 6 | Hardcoded system prompt in CLI binary misdirects file-editing behavior toward shell commands. |

**Additional notable closed issues:**
- [#48511](https://github.com/anthropics/claude-code/issues/48511) — Session history lost when switching accounts (closed)
- [#41091](https://github.com/anthropics/claude-code/issues/41091) — System task-tool reminders degrade session quality (closed)

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **Model tool-selection alignment** — Users repeatedly want Claude Code to prefer native tools (Read, Edit, Grep) over Bash equivalents (sed, grep, heredoc). Issue [#19649](https://github.com/anthropics/claude-code/issues/19649) (101 👍) and [#88041](https://github.com/anthropics/claude-code/issues/88041) converge on this.
- **Accessibility & customization** — Customizable UI durations and phrasing ([#24968](https://github.com/anthropics/claude-code/issues/24968)) signal growing demand for A11y-friendly configurations.
- **Cost transparency** — The v2.1.239 update shows responsiveness to data-residency pricing; users are tracking cost-estimate accuracy closely.
- **Workspace/remote controls** — Android Remote Control ignoring `bypassPermissions` ([#86858](https://github.com/anthropics/claude-code/issues/86858)) and Cowork folder-mount issues suggest remote/connected-workspace features need tighter integration.

---

## 6. Developer Pain Points

| Theme | Issues |
|-------|--------|
| **Cyber-safeguard false positives** | [#84352](https://github.com/anthropics/claude-code/issues/84352), [#84353](https://github.com/anthropics/claude-code/issues/84353), [#73228](https://github.com/anthropics/claude-code/issues/73228)–[#73194](https://github.com/anthropics/claude-code/issues/73194) cluster |
| **Windows Desktop reliability** | [#42776](https://github.com/anthropics/claude-code/issues/42776), [#76187](https://github.com/anthropics/claude-code/issues/76187), [#82967](https://github.com/anthropics/claude-code/issues/82967) |
| **macOS Desktop post-update regressions** | [#86617](https://github.com/anthropics/claude-code/issues/86617), [#86289](https://github.com/anthropics/claude-code/issues/86289), [#86838](https://github.com/anthropics/claude-code/issues/86838) |
| **Basic TUI usability** | [#62699](https://github.com/anthropics/claude-code/issues/62699) — cannot copy text from output |
| **Account/session management** | [#48511](https://github.com/anthropics/claude-code/issues/48511) — history lost on account switch; [#56897](https://github.com/anthropics/claude-code/issues/56897) — Max plan unexpectedly downgraded |
| **System prompt / auto-mode bugs** | [#88041](https://github.com/anthropics/claude-code/issues/88041), [#41091](https://github.com/anthropics/claude-code/issues/41091) — hardcoded prompts pushing wrong behavior |
| **Plugin reliability** | [#87627](https://github.com/anthropics/claude-code/issues/87627) — security-guidance plugin silently drops patterns on non-mapping YAML/JSON |

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-22

## 1. Today's Highlights

A cluster of Windows + Android Remote Control connectivity regressions is dominating the issues board, with at least six open reports describing pairing failures, session load errors, and reconnect loops following recent app updates. On the release side, the Rust toolchain is moving quickly through the `0.150.0-alpha` track with four new pre-releases in 24 hours. Internally, the team shipped a batch of Guardian V2 hardening, executor stop-hook improvements, and Amazon Bedrock app-server support.

---

## 2. Releases

**Rust CLI — `0.150.0-alpha` series (rolling):**
- `0.150.0-alpha.6`, `.5`, `.3`, `.2` — Rapid iteration through the alpha track, likely stabilizing changes from the Guardian/sandbox/executor PRs landed today.
- `0.149.0-alpha.7.1`, `.4.1` — Patch-level bumps on the prior alpha branch.

**Desktop (bundled):** Build `26.818.x` is the current Windows release; several issues report regressions introduced by this update cycle.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#35119](https://github.com/openai/codex/issues/35119) | Windows/WSL marks valid repos as non-Git, reports "Git is unavailable" | 24 | 17 | Breaks core repo detection on the largest supported platform combo; regressions from `26.715→26.721`. |
| [#33493](https://github.com/openai/codex/issues/33493) | Local compaction v2 retains unbounded `input_image` payloads, causing repeated auto-compaction | 22 | 6 | Image-heavy threads on Desktop enter an infinite compaction loop, degrading performance and context budget. |
| [#39815](https://github.com/openai/codex/issues/39815) | Windows + Android Remote: pairing succeeds but `/wham/tasks/list` returns 503 | 13 | 3 | Remote Control mobile experience is actively broken for Windows users after pairing. |
| [#38503](https://github.com/openai/codex/issues/38503) | "Too many requests" blocks ChatGPT web chat and Work tasks | 9 | 11 | Rate-limiting spill-over between desktop and web is disrupting Pro/Work users on the same account. |
| [#39856](https://github.com/openai/codex/issues/39856) | QR pairing succeeds but `nextConnectionCount=0` blocks Android sessions | 9 | 0 | New regression in `26.818.31338`; paired devices cannot establish a live session. |
| [#39954](https://github.com/openai/codex/issues/39954) | Windows + Android Remote enters reconnect loop after successful initialize | 9 | 0 | Post-pairing websocket becomes unstable; entire Remote Control path is unreliable. |
| [#17598](https://github.com/openai/codex/issues/17598) | Native subagent orchestration fails with non-OpenAI custom providers | 9 | 2 | Third-party provider users cannot leverage subagent parallelism — a growing use case. |
| [#39947](https://github.com/openai/codex/issues/39947) | Android Remote becomes unusable; Windows host appears disconnected | 9 | 3 | Long-running tasks won't open on mobile; affects business-plan users. |
| [#39974](https://github.com/openai/codex/issues/39974) | Remote Control unstable across Android + iOS against one Windows host | 8 | 0 | Cross-device reproducibility (3 phones, both OSes) confirms a host-side regression. |
| [#34764](https://github.com/openai/codex/issues/34764) | Computer Use fails on Windows: Application Protected files won't copy from `WindowsApps` | 7 | 1 | Sandboxed file access blocks a core Computer Use workflow on Windows. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#40038](https://github.com/openai/codex/pull/40038) | Add unfinished root turn suspension | ✅ Closed | New `suspend_turn_and_shutdown` API lets a runtime reclaim a turn ID without marking it complete — improves recovery semantics. |
| [#40031](https://github.com/openai/codex/pull/40031) | Preserve strict MCP auto-review outcomes | ✅ Closed | Denial/timeout/abort responses from strict MCP reviewers are now propagated with full metadata instead of being collapsed to a generic decline. |
| [#40028](https://github.com/openai/codex/pull/40028) | Log Guardian V2 classification results | ✅ Closed | Structured logging now emits risk score, thread/turn context, and accept/supersede outcome per classification — important for observability. |
| [#40024](https://github.com/openai/codex/pull/40024) | Honor granular sandbox approvals in unified exec | ✅ Closed | `require_escalated` commands now correctly prompt when `sandbox_approval` is enabled and stay rejected when disabled. |
| [#40021](https://github.com/openai/codex/pull/40021) | Cancel Guardian reviews with their tool calls | ✅ Closed | Cancellation tokens propagate into Guardian approval reviews so an interrupted tool also aborts its pending review. |
| [#40007](https://github.com/openai/codex/pull/40007) | Implement Amazon Bedrock setup in the app server | ✅ Closed | New `account/bedrock/discover` and `account/bedrock/setup` endpoints — first-party AWS Bedrock provisioning in the Desktop app. |
| [#40018](https://github.com/openai/codex/pull/40018) | Add browser and computer use configuration | ✅ Closed | Typed `browser_use` and `computer_use` settings expose history access, per-origin policies, downloads/uploads, and CDP controls. |
| [#40015](https://github.com/openai/codex/pull/40015) | Harden remote installed plugin cache reconciliation | ✅ Closed | Snapshots are now scoped to the active account; in-flight loads are discarded on account switch and reconciliation is serialized. |
| [#40013](https://github.com/openai/codex/pull/40013) | Reuse Guardian reviews in async risk scoring | ✅ Closed | Completed sync Guardian allows/denies are retained as trusted developer context for subsequent async V2 classifier samples. |
| [#39999](https://github.com/openai/codex/pull/39999) | Hide Fast mode status for unsupported models | ✅ Closed | Fixes the UI bug where `Fast off` was shown even when the selected model doesn't support Fast mode at all. |

---

## 5. Feature Request Trends

- **Custom-provider parity:** [#17598](https://github.com/openai/codex/issues/17598) and [#33405](https://github.com/openai/codex/issues/33405) both surface the gap between OpenAI-native and third-party model tooling — developers want subagent orchestration and native `apply_patch`-style edit tools available for Bedrock, custom endpoints, and other providers.
- **Multi-profile / multi-account in the Desktop app:** [#18655](https://github.com/openai/codex/issues/18655) requests simultaneous profile support so users can switch without restarting, a pattern common in competing tools.
- **Native edit tooling for non-OpenAI models:** [#33405](https://github.com/openai/codex/issues/33405) specifically asks for a provider-compatible edit tool so custom providers can participate in the same file-workflow pipeline.
- **Remote Control session parity:** Multiple issues ([#24454](https://github.com/openai/codex/issues/24454), [#39845](https://github.com/openai/codex/issues/39845)) indicate users expect symmetric session access and task creation across desktop and mobile.

---

## 6. Developer Pain Points

1. **Windows + Android Remote Control is in regression territory.** At least six open issues describe pairing, session-loading, and reconnect failures that began after the `26.818.x` update wave. The problem is cross-device and cross-OS (Android + iOS), pointing to a Windows app-server-side bug.
2. **Windows-specific sandbox and Computer Use friction.** Issues [#34764](https://github.com/openai/codex/issues/34764), [#37595](https://github.com/openai/codex/issues/37595), and [#35718](https://github.com/openai/codex/issues/35718) all describe sandbox setup failures, protected-file access errors, and corrupt state files that survive reinstallation — a painful troubleshooting loop.
3. **Rate-limit cross-contamination.** [#38503](https://github.com/openai/codex/issues/38503) and [#38728](https://github.com/openai/codex/issues/38728) report that desktop and web clients share quota buckets unexpectedly, and that Pro weekly meters can accelerate without cause.
4. **Compaction and context bloat on image-heavy threads.** [#33493](https://github.com/openai/codex/issues/33493) reveals that local compaction v2 does not properly trim image payloads, causing infinite compaction cycles.
5. **Auth / session cookie regressions.** [#40036](https://github.com/openai/codex/issues/40036) and [#40029](https://github.com/openai/codex/issues/40029) describe infinite sign-in loops on Windows and macOS after the latest updates — users are locked out entirely.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-22

---

## 1. Today's Highlights

Gemini CLI shipped a new nightly build (**v0.56.0-nightly.20260822**) with a critical macOS sandbox hardening fix that isolates Docker and container runtime sockets under Seatbelt, preventing hypervisor filesystem mount escapes. Meanwhile, the PR-generation evaluation pipeline continues to take shape with a wave of infrastructure PRs covering Cloud Run orchestration, trajectory logging to GCS, and an LLM-as-a-Judge diff scoring module.

---

## 2. Releases

**v0.56.0-nightly.20260822.g5411f113c**
- Fixed macOS Seatbelt sandbox to deny access to Docker/container UNIX domain sockets, CLI binaries, Mach/XPC service lookups, and POSIX shared memory — closing a sandbox-escape vector via VirtioFS mounts.
- New contributor: [@josebalius](https://github.com/josebalius) made their first contribution.
- [PR #28935](https://github.com/google-gemini/gemini-cli/pull/28935) · [Issue tracker](https://github.com/google-gemini/gemini-cli/issues)

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports `GOAL` success after hitting `MAX_TURNS`, hiding the interruption | Subagent recovery logic silently misreports failure as success, breaking debugging and eval pipelines | 13 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely on simple tasks | Delegation to the generalist agent causes permanent hangs; work-around is disabling sub-agent use entirely | 8 comments · **8 👍** |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Post-Execution Intent Routing | Proposes leveraging Gemini 3's native bash affinity with a security-first sandbox model | 8 comments · 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and codebase mapping | Epic tracking whether AST tools can reduce turn count and token noise via precise method-bound reads | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use custom skills/sub-agents autonomously | Users report skills are ignored unless explicitly prompted, undermining the agent design | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Sessions the extraction agent skips remain unprocessed and surface repeatedly, wasting context | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | Secrets may already be in model context before redaction occurs; service logs also leak skill names | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell commands stuck at "Waiting input" after completion | Simple non-interactive commands (e.g. `ls`) hang the CLI in an await state | 4 comments · **3 👍** |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent lacks session takeover and lock recovery | Locked browser profiles cause immediate fail-fast; no automatic orphan recovery | 4 comments |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | `browser_agent` terminates with `GOAL` on Wayland compositors, blocking Linux desktop users | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| PR | Description |
|----|-------------|
| [#28935](https://github.com/google-gemini/gemini-cli/pull/28935) | **macOS Seatbelt sandbox hardening** — denies container runtime socket, binary, and shared-memory access to prevent VirtioFS-based escape. |
| [#28956](https://github.com/google-gemini/gemini-cli/pull/28956) | **Symlinked/junctioned skills directories** — resolves `realpath` so Windows junctions and symlinks to `.gemini` are recognized as valid skill roots. |
| [#28955](https://github.com/google-gemini/gemini-cli/pull/28955) | **Dependency update + MCP config + ECC bundle integration** — keeps the toolchain current and adds Model Context Protocol support. |
| [#28951](https://github.com/google-gemini/gemini-cli/pull/28951) | **Cloud Run job & workflow for PR generation** — production-grade orchestration for the automated PR-generation pipeline. |
| [#28934](https://github.com/google-gemini/gemini-cli/pull/28934) | **History rollback & retry-nudge optimizations** — prevents context-window bloat on tool-cancellation and improves prefix-cache hit rates. |
| [#28827](https://github.com/google-gemini/gemini-cli/pull/28827) | **False 401 authentication errors** — narrows `isAuthenticationError` to only match `401` at message start or with HTTP context, blocking false positives from ports/exit codes. |
| [#28953](https://github.com/google-gemini/gemini-cli/pull/28953) | **Evaluation diff PR submission helper** — `create_pr_from_diff.py` applies generated diffs, runs CI regression checks, and opens PRs automatically. |
| [#28952](https://github.com/google-gemini/gemini-cli/pull/28952) | **Interactive HTML diff visualizer** — side-by-side comparison of agent-generated diffs vs. ground-truth fixes with Diff2HTML + Highlight.js. |
| [#28948](https://github.com/google-gemini/gemini-cli/pull/28948) | **PR-generation eval suite harness** — `eval_suite.py` + e2e chained pipeline runner for benchmarking the PR-codegen agent across curated issues. |
| [#28940](https://github.com/google-gemini/gemini-cli/pull/28940) | **A2A server stale cancellation fix** — clears corrupted `Execution aborted` state so subsequent user prompts no longer crash immediately. |

---

## 5. Feature Request Trends

1. **AST-Aware Codebase Tooling** — Multiple issues (#22745, #22746, #19561) converge on replacing naive file reads with AST/structural tools (tilth, glyph) to reduce token waste and improve navigation precision.
2. **Sub-Agent Autonomy & Reliability** — Users want agents to *choose* to use skills and sub-agents without explicit prompting (#21968), and expect sub-agent trajectories to be visible via `/chat share` (#22598).
3. **Secure Sandboxing** — The community is pushing for both stronger isolation (zero-dependency OS sandbox #19873, Wayland browser support #21983) and better recoverability from locked/broken sessions (#22232).
4. **Auto Memory Quality** — Requests for deterministic redaction (#26525), low-signal session quarantine (#26522), and invalid patch surfacing (#26523) show growing maturity concerns around the memory system.
5. **Evaluation & Benchmarking Infrastructure** — A full PR-generation eval pipeline is being built (Cloud Run, GCS logging, LLM judge, diff visualizer), signaling a shift toward measurable, automated agent quality assurance.

---

## 6. Developer Pain Points

- **Silent sub-agent failures** — Agents report `GOAL`/`success` when they actually hit `MAX_TURNS` or crash (#22323, #21409), making debugging extremely difficult.
- **Shell command hangs** — Non-interactive commands frequently leave the CLI in a perpetual "Awaiting user input" state (#25166), breaking automated workflows.
- **Browser agent fragility** — Locked profiles and Wayland incompatibility cause immediate failures with no recovery path (#22232, #21983).
- **Auto Memory leaking secrets** — Transcript content reaches the model before redaction, and the service logs skill names that may contain sensitive paths (#26525, #26522).
- **False authentication errors** — Any message containing `401` as a substring (e.g. port numbers, exit codes) triggers spurious auth-failure handling (#28827).
- **Skills/sub-agents ignored** — Custom skills and sub-agents defined in configuration are not used unless explicitly told, undermining the agent architecture (#21968).
- **Context bloat on retry** — Tool-cancellation and retry nudges currently append synthetic content rather than rolling back, wasting tokens and breaking prefix caches (#28934).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# Copilot CLI Community Digest — 2026-08-22

## 1. Today's Highlights

The v1.0.81-7 prerelease shipped with a highly requested session-restore feature, so crashed or restarted terminals now prompt to recover open sessions automatically. The `models.list` command also surfaced service-published info and warning messages per model, giving developers more transparency into provider status. On the issues front, community discussion remains intense around BYOK model switching and multi-model support, while a wave of ACP-mode bugs and Windows path-handling regressions landed in the tracker today.

## 2. Releases

**v1.0.81-7** — [GitHub Releases](https://github.com/github/copilot-cli)

- **Session restore on startup:** If the CLI crashes or the machine restarts, Copilot now offers to restore sessions that were still open, eliminating the need to manually reopen each terminal.
- **`models.list` enriched output:** Includes `infoMessages` and `warningMessages` published by the service per model, so operators can surface provider notices directly in CLI output.
- **`copilot app` command added:** Opens the Copilot desktop/app context from the CLI.

## 3. Hot Issues

1. **#3282 — Add multiple BYOK model capability** *(8 comments · 26 👍)*
   Users want to switch between multiple BYOK models inside a session without terminating and reconfiguring env vars. Strong community demand signals a gap in the current single-model BYOK design. [View](https://github.com/github/copilot-cli/issues/3282)

2. **#3709 — Allow `/model` to switch between multiple models, including BYOK/local providers** *(4 comments · 27 👍)*
   The `/model` picker currently lists only GitHub-hosted models and ignores locally configured BYOK providers. Developers need unified model switching across all configured sources. [View](https://github.com/github/copilot-cli/issues/3709)

3. **#1313 — Session Branching** *(7 comments · 13 👍)*
   A long-requested feature to branch a session at any point, creating a child session that inherits full history while preserving the original. This would greatly improve exploratory workflows. [View](https://github.com/github/copilot-cli/issues/1313)

4. **#4345 — Reasoning effort 'medium' not supported for `claude-haiku-4.5`** *(8 comments · 4 👍)*
   When specific feature flags are enabled server-side, sub-agent execution fails with an unsupported reasoning-effort error. Affects users relying on Haiku for cost-efficient runs. [View](https://github.com/github/copilot-cli/issues/4345)

5. **#4211 — Copilot CLI couldn't handle BigInt in structured MCP response** *(5 comments · 3 👍)*
   MCP servers returning `BigInt` values cause a serialization crash (`TypeError: Do not know how to serialize a BigInt`) and abort all ongoing tasks. Relevant for any team using MCP tools that emit large integers. [View](https://github.com/github/copilot-cli/issues/4211)

6. **#4535 — `store_memory` fails in v1.0.81 prereleases: "Instance id is required"** *(4 comments · 0 👍)*
   The native memory writer is invoked without a required `instanceId`, causing consistent failures in prerelease builds. A regression affecting agents that rely on memory tools. [View](https://github.com/github/copilot-cli/issues/4535)

7. **#4038 — Non-interactive mode: late-connecting MCP server injects empty user message** *(3 comments · 0 👍) — CLOSED*
   When an MCP server with 7+ tools connects late, the CLI appends an empty user turn, causing the model to answer the empty turn or echo fragments of its system prompt. Closed, but highlights a real ACP/MCP integration edge case. [View](https://github.com/github/copilot-cli/issues/4038)

8. **#4521 — Sandbox cannot be disabled** *(3 comments · 4 👍)*
   Despite being configured as disabled, the sandbox remains active and Copilot attempts to use it. A configuration/CLI sync bug that blocks users who need unrestricted execution. [View](https://github.com/github/copilot-cli/issues/4521)

9. **#4533 — Terminal UI stops consuming events when a turn spawns parallel subagents** *(1 comment · 0 👍)*
   On prerelease builds (1.0.81-4/5), the TUI becomes unresponsive to input and scroll the moment a parallel subagent block launches, though the Rust runtime continues executing. A serious UX regression for multi-agent workflows. [View](https://github.com/github/copilot-cli/issues/4533)

10. **#4555 — ACP: `session/prompt` unconditionally aborts the session** *(0 comments · 0 👍)*
    In ACP mode, every new `session/prompt` call triggers `session.abort()` as its first action, killing all running background sub-agents. The interactive TUI does not exhibit this behavior, indicating an ACP-specific path bug. [View](https://github.com/github/copilot-cli/issues/4555)

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

- **Multi-model & BYOK flexibility (#3282, #3709):** The community repeatedly asks for the ability to switch between BYOK and local models *within* a session, and to support multiple BYOK models simultaneously without session restarts.
- **Session branching and history management (#1313, #4554):** Users want finer control over session trees — branching, resuming unscoped sessions, and attaching inline annotations to plans (#4563).
- **MCP reliability and diagnostics (#4211, #4542, #4552, #4562):** A consistent theme around MCP servers crashing the CLI (BigInt serialization, unavailable servers hanging, reload reusing stale configs). Better error reporting and graceful degradation are top-of-mind.
- **ACP protocol compliance (#4038, #4555, #4560, #4561):** Multiple ACP-mode issues point to gaps between the ACP spec and the current implementation — particularly around `session/prompt` abort behavior, `stopReason` values, and reasoning-effort configuration under `auto` mode.

## 6. Developer Pain Points

- **Session fragility:** Crashes, restarts, and multi-agent parallelism can leave sessions in broken states (unresponsive UI, aborted sub-agents, lost clipboard data). The new session-restore feature in v1.0.81-7 addresses part of this, but parallel subagent event handling (#4533) and ACP abort behavior (#4555) remain open concerns.
- **BYOK pain:** The single-model pin and the inability to list or switch to local providers from `/model` (#3282, #3709) create friction for teams managing multiple custom models.
- **MCP instability:** BigInt serialization crashes, late-connecting servers injecting empty turns, and stale config reloads all point to a need for more robust MCP integration and error handling.
- **Windows-specific regressions:** Visible PowerShell console windows on every shell command (#4549), misplaced quotes in paths containing `"Program Files"` breaking `wta.exe` (#4540), and clipboard sync failures over remote SSH (#4551) are creating platform-specific headScratching.
- **Configuration drift:** Sandbox staying enabled despite being disabled (#4521), marketplace entries fetched but never registered (#4556), and `reasoningEffort` silently nulled in auto mode (#4560) suggest the config pipeline needs tighter validation and sync.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-22

## 1. Today's Highlights

No new releases were published in the last 24 hours. The community's attention is focused on a critical background subagent lifecycle bug (Issue #2615) and an ongoing documentation PR clarifying plugin security boundaries (PR #2614).

## 2. Releases

No releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Author | Why It Matters |
|---|-------|--------|----------------|
| 1 | [#2615](https://github.com/MoonshotAI/kimi-cli/issues/2615) — Background subagent keeps making LLM calls after TaskStop/timeout | pc9527zxx | A background subagent can continue issuing LLM requests even after its task is marked `timed_out` or `killed`. The task vanishes from active tracking, making quota consumption invisible and rendering `TaskStop` ineffective. This is a resource-leak and billing-risk bug that could silently burn credits. Currently 0 comments, 0 👍 — likely early-reported and awaiting triage. |

*(Only 1 issue updated in the last 24h; full list not available.)*

## 4. Key PR Progress

| # | PR | Author | Description |
|---|-----|--------|-------------|
| 1 | [#2614](https://github.com/MoonshotAI/kimi-cli/pull/2614) — docs(plugins): document security and persistent data | QIANLING-0831 | Documentation-only PR that clarifies the trust boundary of locally executed plugin tools, credential-handling precautions for `inject`, the effect of reinstalling on the plugin directory, and recommends a separate data directory for persistent plugin state. Still open, last updated 2026-08-21. |

*(Only 1 PR updated in the last 24h; full list not available.)*

## 5. Feature Request Trends

Based on the limited window of activity, no new feature-request trends are discernible. The dominant signal is a **reliability concern** around background task lifecycle management rather than feature demand.

## 6. Developer Pain Points

- **Invisible quota drain from background subagents:** Issue #2615 highlights that when a background subagent outlives its parent task's tracked lifecycle, continued LLM calls go unnoticed and cannot be stopped via `TaskStop`. This directly impacts cost control and resource management for power users running long-running background workflows.
- **Plugin security and data persistence ambiguity:** PR #2614's existence signals that developers are seeking clearer guidance on plugin trust boundaries, credential handling, and persistent data storage — areas where unclear defaults can lead to security or data-loss risks.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-22

---

## 1. Today's Highlights

OpenCode v1.18.21 ships with critical fixes for unknown finish reasons and Vertex AI Gemini routing, while v1.18.20 resolves subagent failure surfacing and network error retries. The community is actively pushing on session archiving UX, cost-tracking accuracy, and multi-subagent TUI performance.

---

## 2. Releases

**v1.18.21** — [GitHub](https://github.com/anomalyco/opencode/releases/tag/v1.18.21)
- **Core:** Continue responses when a model reports an unknown `finish_reason` instead of halting; route Vertex AI `eu`/`us` multi-region Gemini requests through REP endpoints.
- **Desktop:** Keep file search results visible while the next search is loading; partial `Regi…` entry (truncated in release notes).

**v1.18.20** — [GitHub](https://github.com/anomalyco/opencode/releases/tag/v1.18.20)
- **Core:** Surface failed subagent tool calls with a resumable `task_id`; retry provider responses ending with `finish_reason: network_error`; broaden retry coverage to `network-error` and `network_error` variants; surface resumable subagent failures (truncated).

---

## 3. Hot Issues

| # | Title | Status | Engagement | Why It Matters |
|---|-------|--------|------------|----------------|
| [#6245](https://github.com/anomalyco/opencode/issues/6245) | `ctrl+p` in VSCode doesn't work | ✅ Closed | 11 comments · 24 👍 | Persistent keybinding conflict between OpenCode's command palette and VSCode's built-in "Go to File." 24 upvotes signal strong community pain; resolved but a recurring friction point for VSCode-native users. |
| [#38749](https://github.com/anomalyco/opencode/issues/38749) | Agent keeps stopping abruptly | 🟢 Open | 10 comments · 4 👍 | Session halts mid-generation without error — directly impacts reliability. Open since July with sustained discussion. |
| [#12377](https://github.com/anomalyco/opencode/issues/12377) | Cost Tracking Architecture: Subagent Aggregation + Multi-Model Correctness | ✅ Closed | 10 comments · 0 👍 | Comprehensive RFC addressing multi-agent cost display gaps. Closed suggests it was adopted; important architectural context for cost-tracking improvements. |
| [#24153](https://github.com/anomalyco/opencode/issues/24153) | Add unarchive/restore for archived sessions | 🟢 Open | 9 comments · 11 👍 | Archived sessions are currently a one-way operation. 11 upvotes show strong demand for reversible archiving — a quality-of-life feature many users need. |
| [#33775](https://github.com/anomalyco/opencode/issues/33775) | Asked for API key every time I change provider | 🟢 Open | 8 comments · 1 👍 | `auth.json` stores keys but provider switches still prompt for input. Bug in credential persistence logic; impacts multi-provider workflows. |
| [#35376](https://github.com/anomalyco/opencode/issues/35376) | Lazy-load MCP tool definitions to reduce token overhead | ✅ Closed | 7 comments · 0 👍 | All MCP tool definitions injected into every conversation's system prompt regardless of use. With 9+ servers, this creates significant token bloat. Closed — likely addressed. |
| [#30906](https://github.com/anomalyco/opencode/issues/30906) | Desktop v1.16.0 Windows: renderer freeze on large file diffs | ✅ Closed | 7 comments · 2 👍 | Regression causing complete Electron renderer freeze on large files. Closed suggests a fix landed; high-severity UX bug for Windows desktop users. |
| [#34473](https://github.com/anomalyco/opencode/issues/34473) | OpenCode randomly stops responses | 🟢 Open | 6 comments · 3 👍 | Responses terminate mid-stream with no error, triggering session-complete sound. Reproducible with `big-pickle` model; indicates a streaming/parsing edge case. |
| [#43805](https://github.com/anomalyco/opencode/issues/43805) | DeepSeek-v4-flash-free missing from Zen dropdown despite API existence | 🟢 Open | 4 comments · 0 👍 | Model exists in `/zen/v1/models` and is configured in `opencode.json` but doesn't appear in the TUI picker. Sync issue between API and client-side model list. |
| [#41847](https://github.com/anomalyco/opencode/issues/41847) | Permission dialogs not rendered: backend blocks on invisible prompts | 🟢 Open | 4 comments · 0 👍 | 3,270 permission prompts created over 27 days with zero user visibility — backend blocks indefinitely. Critical UX bug causing app to appear frozen. |

---

## 4. Key PR Progress

| PR | Title | Author | Status | Summary |
|----|-------|--------|--------|---------|
| [#44002](https://github.com/anomalyco/opencode/pull/44002) | Recover partial provider failures | kitlangton | 🟢 Open | Auto-recovers retryable provider-internal and rate-limit failures after partial output; can cross eagerly-executed local tools but stops at non-replayable provider activities. |
| [#43165](https://github.com/anomalyco/opencode/pull/43165) | Message logger | bornmw | 🟢 Open | Adds configurable LLM request/response logging (`experimental.log_messages`: info/debug/trace), closing [#29186](https://github.com/anomalyco/opencode/issues/29186). |
| [#44031](https://github.com/anomalyco/opencode/pull/44031) | Stop looping after unknown finish with text | razectp | 🟢 Open | Closes [#43939](https://github.com/anomalyco/opencode/issues/43939); prevents prompt loops on `unknown` finish while still allowing empty-dropped stream recovery. |
| [#44029](https://github.com/anomalyco/opencode/pull/44029) | Resolve console device URLs | kitlangton | ✅ Closed | Ported device auth URL fix to both implementations; resolves path-based Console deployments duplicating `/console` in verification URLs. |
| [#43978](https://github.com/anomalyco/opencode/pull/43978) | Resolve console device login URL | opencode-agent[bot] | 🟢 Open | Standardizes URL semantics for Console device verification; rejects malformed and non-HTTP(S) URLs. |
| [#44016](https://github.com/anomalyco/opencode/pull/44016) | Harden portable shell authorization | kitlangton | 🟢 Open | Hardens opt-in portable shell permission scanner against uncertain shell input executing under narrowed saved approvals. |
| [#44000](https://github.com/anomalyco/opencode/pull/44000) | Stabilize generated contract names | kitlangton | ✅ Closed | Effect client endpoints and OpenAPI names now derive from contract identity (e.g. `SessionGetOutput`) instead of traversal position. |
| [#44025](https://github.com/anomalyco/opencode/pull/44025) | Tolerate incomplete agent configuration | OpeOginni | 🟢 Open | Fixes a whole-app crash on Desktop when a connected server runs an older OpenCode version; hardens `normalizeAgentList`. |
| [#44027](https://github.com/anomalyco/opencode/pull/44027) | Load workspace sessions by directory | OpeOginni | 🟢 Open | Stops Settings → Workspaces from freezing by fetching sessions by directory instead of loading every session serially. |
| [#43993](https://github.com/anomalyco/opencode/pull/43993) | Disable bun fetch idle timeout for remote MCP transports | viperx1 | 🟢 Open | Fixes long MCP calls silently dying after 300s on Bun runtime despite `mcp.timeout` being passed through correctly; closes [#39584](https://github.com/anomalyco/opencode/issues/39584). |

---

## 5. Feature Request Trends

1. **Session lifecycle management** — Unarchive/restore ([#24153](https://github.com/anomalyco/opencode/issues/24153)), per-provider quota-aware retry ([#43324](https://github.com/anomalyco/opencode/issues/43324)), and session cost aggregation ([#12377](https://github.com/anomalyco/opencode/issues/12377)) reflect demand for richer session control and observability.
2. **Cost and token optimization** — Multiple requests target reducing token overhead: lazy-loading MCP tool definitions ([#35376](https://github.com/anomalyco/opencode/issues/35376)), accurate multi-model cost tracking, and per-provider retry scheduling based on quota awareness.
3. **Cross-platform provider compatibility** — DeepSeek availability gaps ([#43805](https://github.com/anomalyco/opencode/issues/43805)), Bedrock/LiteLLM gateway issues with `textVerbosity` ([#43911](https://github.com/anomalyco/opencode/issues/43911)), and OpenAI-compatible reasoning field handling ([#35283](https://github.com/anomalyco/opencode/issues/35283)) indicate ongoing friction in provider-agnostic model routing.
4. **API and programmatic access** — Request to expose Go usage history via API key ([#43983](https://github.com/anomalyco/opencode/issues/43983)) signals demand for programmatic session/export capabilities.

---

## 6. Developer Pain Points

- **Streaming and response reliability** — Multiple open issues (#38749, #34473, #43882) describe abrupt stops, missing `finish_reason`, and unknown terminal states across models. The v1.18.21 release directly addresses the unknown finish reason case.
- **Multi-subagent performance** — [#42657](https://github.com/anomalyco/opencode/issues/42657) reports 97% CPU on the render thread with 2-4 concurrent subagents, causing 1-3s typing delays. This is a scalability bottleneck for complex agent workflows.
- **Provider credential persistence** — [#33775](https://github.com/anomalyco/opencode/issues/33775) highlights that `auth.json` is not respected on provider switches, forcing repeated API key entry.
- **Desktop UX regressions** — Large-file renderer freezes ([#30906](https://github.com/anomalyco/opencode/issues/30906)), viewport snapping during scrolling ([#29094](https://github.com/anomalyco/opencode/issues/29094)), and permission dialog invisibility ([#41847](https://github.com/anomalyco/opencode/issues/41847)) create inconsistent desktop experiences across platforms.
- **MCP tool bloat** — All tool definitions from all connected servers are injected into every conversation's system prompt ([#35376](https://github.com/anomalyco/opencode/issues/35376)), creating unnecessary token overhead for users with many MCP servers.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-22

## 1. Today's Highlights

The top community concern remains **auto-compaction reliability**: issue #6879 highlights a critical bug where compaction never triggers after context exceeds 100%, only activating after an API rejection at 373k tokens — a 17-upvote problem affecting long-running agentic sessions. Additionally, a batch of keyboard/terminal issues resurfaced in the last 24 hours, with fixes already landing for fullscreen word-selection (#8459 closed) and a new PR addressing extension factory crash recovery (#8424 open).

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 | Why it matters |
|---|-------|--------|----------|----|----------------|
| #6879 | auto-compaction never triggers after context grows past 100% | OPEN | 19 | 17 | Compaction silently fails on long agentic sessions; only kicks in after API rejection. High-severity bug for reasoning-model users. |
| #2733 | Backspace and Delete keys broken in Windows Terminal | CLOSED | 11 | 1 | Regressed in 0.64.0; affects a large Windows user base. Now resolved. |
| #8157 | Migrate grok-mermaid → lovely-mermaid | OPEN | 9 | 1 | Improves mermaid rendering quality; inherits fewer corner cases from the original grok port. |
| #7130 | Backspace deletes 2 chars in Kitty | OPEN | 9 | 1 | Kitty keyboard protocol release events are not filtered, causing double-deletion. |
| #7553 | Configurable thinking level/model for compaction | IN PROGRESS | 8 | 0 | Users cannot give compaction its own thinking budget — it unconditionally reuses the session level. |
| #7995 | No `cacheControlFormat: 'anthropic'` in openai-responses | OPEN | 7 | 0 | OpenRouter benchmark shows a **2.5× cost penalty** for Claude via OpenAI-compatible endpoint without prompt caching. |
| #7779 | Trusted Unix users can now share `PI_CODING_AGENT_DIR` | CLOSED | 6 | 0 | Multi-user setups were blocked by `0600` file permissions on `auth.json` / `models-store.json`. Fixed. |
| #8183 | Windows Terminal Ctrl+Shift+F conflicts with transcript search | OPEN | 4 | 0 | Fullscreen transcript search binds `Ctrl+Shift+F`, clashing with Windows Terminal's built-in Find. Docs update needed. |
| #8134 | Agent halts after first tool call via plain-HTTP forward proxy | OPEN | 4 | 0 | Since 0.84.0, sessions through an HTTP proxy hang on the second model call. Affects corporate/proxied environments. |
| #8133 | Per-model compaction settings | OPEN | 3 | 3 | Community wants `compaction.profiles` keyed by model ID — a natural extension of #7553, enabling fine-grained control. |

---

## 4. Key PR Progress

| # | Title | Status | Description |
|---|-------|--------|-------------|
| #8459 | fix(tui): keep `/` and `-` inside fullscreen double-click selection | **CLOSED** | `Intl.Segmenter` was treating `/` and `-` as word boundaries, splitting paths on double-click. Fixed. ([link](https://github.com/earendil-works/pi/issues/8459)) |
| #8443 | feat(interactive-mode): share via Radius artifacts (experimental) | **CLOSED** | `/share` now uses Radius artifacts instead of Gist when the experimental flag is set, with auth flow support. ([link](https://github.com/earendil-works/pi/pull/8443)) |
| #8433 | feat(coding-agent): add `--exclude-extensions` | **CLOSED** | Solves the all-or-nothing extension loading problem; users can now exclude specific extensions while keeping auto-discovery for the rest. ([link](https://github.com/earendil-works/pi/pull/8433)) |
| #8428 | fix(coding-agent): re-pair tool results when rebuilding session context | **CLOSED** | Fixes session-corruption bug (#8166): tool results are now correctly re-paired with their originating assistant messages during resume, compaction, and branch navigation. ([link](https://github.com/earendil-works/pi/pull/8428)) |
| #8424 | fix(coding-agent): discard failed extension factory state | **OPEN** | Extensions that throw during factory init no longer leave staged state or orphaned event-bus listeners; later calls through the failed factory are rejected. ([link](https://github.com/earendil-works/pi/pull/8424)) |
| #8422 | fix(ai): omit reasoning effort for xAI Grok Build | **CLOSED** | xAI's `grok-build-0.1` rejects requests containing `reasoning.effort`. The PR adds a Responses compatibility flag to omit the field for this model. ([link](https://github.com/earendil-works/pi/pull/8422)) |
| #8232 | DONT MERGE: dev branch | OPEN | CI/commenting branch — not a feature PR. |
| #5354 | Allow grep tool command to be customized by an extension | **CLOSED** | Extensions can now intercept and customize the grep command, enabling sandboxed extensions (e.g., bubblewrap-based) to work correctly. ([link](https://github.com/earendil-works/pi/issues/5354)) |
| #6193 | Make `/exit` an alias for `/quit` | **CLOSED** | Minor UX improvement aligning pi with codex/claude/opencode. ([link](https://github.com/earendil-works/pi/issues/6193)) |
| #4742 | Add SiliconFlow provider | **CLOSED** | Built-in support for SiliconFlow (international + China endpoints) via OpenAI-compatible completions API, covering Qwen, GLM, and other open-source models. ([link](https://github.com/earendil-works/pi/issues/4742)) |

---

## 5. Feature Request Trends

- **Compaction customization** is the dominant theme: users want per-model profiles (#8133), independent thinking levels (#7553), and manual full-span modes (#8453). The current one-size-fits-all compaction is increasingly seen as inadequate for long reasoning sessions.
- **Provider & cost optimization**: Multiple issues target cost reduction — Anthropic prompt-caching support (#7995), SiliconFlow provider (#4742), and Parasail.io (#8450) reflect demand for cheaper inference paths.
- **Terminal/keyboard UX**: Persistent frustration around terminal key handling (Windows Terminal #2733, Kitty #7130/#8442) and fullscreen search conflicts (#8183) suggests the TUI layer needs more robust cross-terminal abstraction.
- **Multi-user & RPC extensibility**: Sharing `PI_CODING_AGENT_DIR` across trusted users (#7779) and adding `/login` support to RPC mode (#8451) indicate a growing appetite for server/remote deployment scenarios.

---

## 6. Developer Pain Points

1. **Session corruption on context rebuild** — The #8166 / #8428 bug (orphaned tool results during compaction/branch navigation) is a data-integrity issue that directly impacts reliability for long-running agents.
2. **Proxy/HTTP passthrough fragility** — Plain-HTTP providers behind forward proxies silently hang after the first tool call (#8134), and mid-stream gateway truncation hard-fails as "Stream ended without finish_reason" (#8460). Both suggest the transport layer lacks graceful degradation.
3. **Terminal key-protocol conflicts** — Kitty's keyboard protocol release events are not properly filtered (#7130), and legacy `0x7f` backspace is ignored inside herdr panes (#8442). The same class of bug recurred in Windows Terminal (#2733). The TUI keyboard abstraction appears to be a recurring weakness.
4. **Provider adapter gaps** — Reasoning-mandatory models like OpenRouter's `stealth/ox-alpha` reject requests with explicit `reasoning: {effort: "none"}` (#8454), and Gemini 3.7 Flash rejects MINIMAL thinking level (#8456). Adapter coverage for new model capabilities is lagging behind provider updates.
5. **TLS/certificate retry gaps** — Intermittent TLS errors (e.g., Codex transport's "unknown certificate verification error") are not retried (#8458), causing avoidable session failures in unstable network conditions.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-22

## 1. Today's Highlights

Qwen Code v0.21.14-nightly ships with a key review-loop improvement that surfaces why a review is not settling, and SWE-bench Verified + Terminal-Bench smoke tests both pass on the release pipeline. Security and CI hardening dominate the top conversations, with several PRs closing residual gaps in Aone Code review support and autofix pipeline reliability.

---

## 2. Releases

**v0.21.14-nightly.20260822.7a4566cb3b**
- `feat(review)`: review loops now report to the author why they are not settling (#9461)
- `fix(ci)`: stopped the fallback CI path that was causing noise
- Benchmark validation: SWE-bench Verified 500 + Terminal-Bench 2.0 89 smoke tests both **succeeded** under DSW EAS execution

[GitHub Release](https://github.com/QwenLM/qwen-code/releases)

---

## 3. Hot Issues

| # | Title | Why It Matters | Comments |
|---|-------|---------------|----------|
| [#9556](https://github.com/QwenLM/qwen-code/issues/9556) | Review pipeline: should code execution stay granted to the invoking user? | Foundational security question — every unresolved finding in the review loop traces back to this precondition. Active maintainer discussion. | 7 |
| [#5180](https://github.com/QwenLM/qwen-code/issues/5180) | Subagent crashes mid-task in long sessions (12h+) | Multi-agent execution reliability under sustained load; high-impact for production workflows. | 7 |
| [#8993](https://github.com/QwenLM/qwen-code/issues/8993) | Public extensions require Git 2.37 but Ubuntu 22.04 ships 2.34.1 | LTS compatibility gap blocks installation on a widely-used distro. **Closed.** | 6 |
| [#5966](https://github.com/QwenLM/qwen-code/issues/5966) | Chinese IME becomes unresponsive during UI interaction | Recurring input-method bug affecting Chinese-language users; hard to reproduce and locate. | 6 |
| [#9089](https://github.com/QwenLM/qwen-code/issues/9089) | autofix PAT jobs share hosts with untrusted branch code | Runner-level isolation needed; findings cannot be closed from inside a GitHub Actions step. **Closed.** | 6 |
| [#9699](https://github.com/QwenLM/qwen-code/issues/9699) | Dependency CVE audit fails on every PR since 2026-08-21 | 8 vulnerabilities (1 high) in production deps; blocks all PRs. **Closed** via #9703. | 4 |
| [#8617](https://github.com/QwenLM/qwen-code/issues/8617) | VS Code extension dropdown obscures content | UX bug where the selection box covers the content below it. | 4 |
| [#9693](https://github.com/QwenLM/qwen-code/issues/9693) | MCP -32000 "Connection closed" on Windows at startup | MCP STDIO transport fails on Windows even when MCP is not activated — affects all Windows desktop users. | 4 |
| [#2862](https://github.com/QwenLM/qwen-code/issues/2862) | Startup hangs on "Initializing..." when checkpointing is enabled | Long-standing bug; enabling checkpointing makes the app unresponsive at launch. | 3 |
| [#379](https://github.com/QwenLM/qwen-code/issues/379) | MCP stdio serializes complex tool args as JSON strings | Non-conforming JSON-RPC behavior for MCP list/object arguments; breaks downstream MCP servers. | 3 |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#9678](https://github.com/QwenLM/qwen-code/pull/9678) | Review agents get their own subagent type | Introduces `review-agent` subagent type declaring only the six tools each dimension actually uses, instead of inheriting every tool via `general-purpose`. |
| [#9526](https://github.com/QwenLM/qwen-code/pull/9526) | Persistently-critical convergence advisory | Review compose step now emits a "land-with-residual-risk" advisory when Criticals are stuck across rounds with active posting volume. |
| [#9596](https://github.com/QwenLM/qwen-code/pull/9596) | Ask each fix for its test, rule on non-convergence | Findings now carry acceptance criteria; the review loop can detect and rule on non-converging fixes. |
| [#9621](https://github.com/QwenLM/qwen-code/pull/9621) | Back PR-context on Aone Code targets | The `/review` metadata-fetch subcommand now works for Aone Code, no longer skipped as GitHub-only. |
| [#9624](https://github.com/QwenLM/qwen-code/pull/9624) | Close Aone residual gaps: composeUrl, test-plan, a1 floor | Completes Aone Code review support with canonical PR links, test-plan routing, and a1 version floor. |
| [#9627](https://github.com/QwenLM/qwen-code/pull/9627) | Back comment-status and presubmit for Aone | Comment-thread indexing and presubmit checks now function on Aone Code MRs. |
| [#9634](https://github.com/QwenLM/qwen-code/pull/9634) | Validate Aone inline anchors against captured diff | Inline findings on Aone are now validated against the diff before posting, preventing stale anchors. |
| [#9649](https://github.com/QwenLM/qwen-code/pull/9649) | Pass `CI=true` through autofix gate's `env -i` launches | Restores CI environment variable in the verification gate, fixing inverted test/run behavior. |
| [#9673](https://github.com/QwenLM/qwen-code/pull/9673) | Stop counting idle timeouts toward the timeout cap | The circuit breaker now only counts meaningful timeouts; idle-sandbox kills no longer exhaust the cap. |
| [#9703](https://github.com/QwenLM/qwen-code/pull/9703) | Bump vulnerable dependencies to unblock CVE audit | Runs `npm audit fix --package-lock-only` to patch all fixable advisories; only lockfile changes. |

---

## 5. Feature Request Trends

- **Session persistence & recovery**: Three linked requests (#9686, #9664, #9688) ask the daemon to restore the last-used model, re-hang unanswered `ask_user_question` HITL prompts, and prevent active/archived session conflicts.
- **Read-only command allowlists in Plan mode** (#9694): Users want a configurable `extraReadOnlyCommands` setting to reduce friction for custom CLI tools.
- **Expanded detail mode by default** (#9670): Request to start with thinking blocks and tool outputs visible, removing the need to manually toggle.
- **Subagent control** (#1212): Demand for the ability to disable or constrain the built-in `general-purpose` subagent, which users find disruptive in long workflows.

---

## 6. Developer Pain Points

- **MCP on Windows is fragile**: Two separate issues (#9693, #9675) report MCP STDIO connections dropping on Windows — both at startup and between sessions — suggesting a platform-specific transport bug.
- **Chinese IME rendering issues**: Two issues (#5966, #9666) report IME candidate box visibility problems on Windows, with low contrast and intermittent input failure.
- **Review loop convergence opacity**: The community is actively wrestling with why review loops stall (#9556, #9446, #9674); the new advisory and machine-readable convergence data (#9526, #9623) are direct responses.
- **Long-session reliability**: Subagent crashes mid-task (#5180) and checkpointing-induced hangs (#2862) point to fragility in sustained multi-hour sessions.
- **CI/CD gate brittleness**: The CVE audit break (#9699) and autofix gate environment issues (#9649) show that CI pipeline changes can silently regress for all contributors.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-22

## 1. Today's Highlights

The most significant development this cycle is PR #5535, a bundled set of five commits delivering supervised-operation infrastructure: a lifecycle event outbox, `/relaunch` support, a per-session control socket, and a fix for goal-continuation cadence bypass. Meanwhile, the maintainers flagged two critical operational bugs (#5529, #5528) where sub-agent failures and silent workflow dispatch errors are causing unreliability in production sessions.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **[BUG] Sub-agents cannot reliably execute** (#5529) — [Link](https://github.com/Hmbown/CodeWhale/issues/5529)
   Maintainer-reported; three failure modes observed (wall-time deaths, provider-route failures, shell tooling workarounds). Directly breaks the Fleet delegation model. 0 comments — likely awaiting investigation.

2. **[BUG] Workflow runs fail silently** (#5528) — [Link](https://github.com/Hmbown/CodeWhale/issues/5528)
   Two workflow runs failed at script-evaluation time with no TUI visibility (no toast, no status line). Operators had no visual indicator of failure. Critical for CI/automation trust.

3. **[EPIC] CodeWhale TUI Crate Decomposition** (#5316) — [Link](https://github.com/Hmbown/CodeWhale/issues/5316)
   Umbrella tracking issue for the large-scale TUI crate refactor. 11 comments, ongoing since Aug 10. Central to the architecture modernization effort.

4. **[BUG] Goal-continuation cadence bypassed on within-turn dispatch** (#5534) — [Link](https://github.com/Hmbown/CodeWhale/issues/5534)
   Resume/CLI sessions fire passes instantly, ignoring `continuation_delay_seconds`. Regressed by #5508. Affects long-lived session control.

5. **[ENH] Feature: DeepSeek-V4-Flash-Vision-Exp** (#5541) — [Link](https://github.com/Hmbown/CodeWhale/issues/5541)
   Request to add the first multi-modal DeepSeek model to the model list. Author notes "huge" impact for web dev and vision tasks.

6. **[ENH] Supervised operation control surface** (#5533) — [Link](https://github.com/Hmbown/CodeWhale/issues/5533)
   Proposes a per-session control socket (message / interrupt / relaunch / status) for external supervision via terminal multiplexers and CI harnesses.

7. **[ENH] /relaunch command** (#5532) — [Link](https://github.com/Hmbown/CodeWhale/issues/5532)
   Allows switching a running session to the current binary post-update, eliminating the manual restart step.

8. **[ENH] Local lifecycle event outbox** (#5531) — [Link](https://github.com/Hmbown/CodeWhale/issues/5531)
   JSONL + webhook outbox emitting `turn_stalled` / `turn_failed` events for unattended overnight runs and alerting setups.

9. **[DOC/ENH] Indexing privacy controls (.codewhaleignore)** (#4069) — [Link](https://github.com/Hmbown/CodeWhale/issues/4069)
   First-class ignore-file support for search, working-set walks, and context assembly — parity with Cursor's `.cursorignore`. Maintainer-tagged; open since July 7.

10. **[BUG] Deprecated shell completion** (#5526) — [Link](https://github.com/Hmbown/CodeWhale/issues/5526)
    PowerShell completions are outdated and still reference the old `codewhale-tui` binary name. No docs or config path found by the reporter.

## 4. Key PR Progress

1. **Supervised operation stack** (#5535) — [Link](https://github.com/Hmbown/CodeWhale/pull/5535)
   Five commits covering lifecycle outbox (JSONL + webhook), `/relaunch`, per-session control socket, `RuntimeBackendKind::External`, and the goal-continuation quiet-period fix. The single most impactful PR this cycle.

2. **Refactor: adopt command shapes in utility group (FEAT-018)** (#5525) — [Link](https://github.com/Hmbown/CodeWhale/pull/5525)
   Converts the TUI utility command group to external command shapes from FEAT-014/015. Changes execution boundary without physically moving files.

3. **feat: multi-file read_lints operation** (#5524) — [Link](https://github.com/Hmbown/CodeWhale/pull/5524)
   Extends the `lsp` tool to support `read_lints` across multiple workspace-relative files, reusing the existing `LspManager` transport pool.

4. **fix: route legacy completions through public binary** (#5530) — [Link](https://github.com/Hmbown/CodeWhale/pull/5530)
   Addresses #5526. `codewhale completions <shell>` now uses the canonical completion generator and outputs scripts referencing the public `codewhale` command name.

5. **Refactor: extract tool call stages from turn loop** (#5523) — [Link](https://github.com/Hmbown/CodeWhale/pull/5523)
   Extracts planning (`plan_tool_calls`), approval+execution (`execute_planned_tools`), and result projection (`process_tool_results`) from the turn loop while preserving control order and cancellation behavior.

6. **chore(deps): bump similar 3.1.2 → 3.2.0** (#5540) — [Link](https://github.com/Hmbown/CodeWhale/pull/5540)
   Dependabot update adding structured diff output capabilities.

7. **chore(deps): bump rio-vt 0.5.19 → 0.5.25** (#5539) — [Link](https://github.com/Hmbown/CodeWhale/pull/5539)
   TerminalVT rendering library update via Dependabot.

8. **chore(deps): bump rmcp 2.2.0 → 3.1.2** (#5390) — [Link](https://github.com/Hmbown/CodeWhale/pull/5390)
   Major bump of the Model Context Protocol Rust SDK. Open since Aug 14, updated today.

9. **chore(deps): bump jsonschema 0.46.10 → 0.49.9** (#5538) — [Link](https://github.com/Hmbown/CodeWhale/pull/5538)
   Significant schema-validation library update.

10. **chore(deps): bump docker/setup-buildx-action 4.2.0 → 4.3.0** (#5537) — [Link](https://github.com/Hmbown/CodeWhale/pull/5537)
    CI infrastructure dependency update.

## 5. Feature Request Trends

- **External supervision & automation**: Three linked issues (#5531, #5532, #5533) and PR #5535 all target the same seam — making codewhale sessions reliably controllable by external orchestrators (multiplexers, CI, alerting). This is the dominant feature direction.
- **Multi-modal model support**: #5541 requests DeepSeek-V4-Flash-Vision-Exp, reflecting user demand for vision-capable models in the TUI.
- **Privacy & ignore controls**: #4069 calls for first-class `.codewhaleignore` support to match competing tools.
- **Shell completion hygiene**: #5526 / #5530 highlights the need for completion scripts to track the public binary name.

## 6. Developer Pain Points

- **Sub-agent reliability**: Two separate bugs (#5529, #5528) show that delegated execution and workflow dispatch are fragile — wall-time deaths lose uncommitted work, and failures are silently swallowed with no TUI feedback. This is the top trust barrier for Fleet-mode usage.
- **Goal-continuation regression**: #5534 reveals that the cadence quiet period introduced in #5508 is bypassed on the within-turn dispatch path, causing resumed sessions to fire passes instantly instead of respecting the configured delay.
- **Completion script drift**: #5526 exposed that generated completions reference the old `codewhale-tui` binary name and contain stale content, with no documented way to fix it.
- **Manual restart after updates**: #5532 underscores friction from the current no-relaunch design — users must manually restart sessions after `codewhale update`.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*