# AI CLI Tools Community Digest 2026-08-27

> Generated: 2026-08-27 08:44 UTC | Tools covered: 10

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
**Date: 2026-08-27**

---

## 1. Ecosystem Overview

The AI CLI tools landscape is entering a period of accelerated maturation, with the dominant theme being **agent reliability and operational stability** rather than feature novelty. All major tools are investing heavily in subagent orchestration, MCP ecosystem compatibility, and context-management resilience. Windows desktop stability emerges as a cross-cutting pain point, particularly for Claude Code and OpenAI Codex. Security hardening—SSRF fixes, secret scoping, and config fail-closed behavior—is receiving notable attention across Gemini CLI, OpenCode, and Codewhale. The ecosystem is clearly differentiating on agent architecture (single-turn vs. multi-subagent) and memory/recall infrastructure, with Qwen Code and Pi leading structured memory investments.

---

## 2. Activity Comparison

| Tool | Issues (24h) | PRs (24h) | Releases | Activity Level |
|------|-------------|-----------|----------|----------------|
| **Claude Code** | 10 hot issues | 2 (1 substantive) | v2.1.247 | Moderate — stability-focused |
| **OpenAI Codex** | 10 hot issues | 10 | rust-v0.150.1, alpha 0.151.0–0.151.5 | High — Windows pain, active PR velocity |
| **Gemini CLI** | 10 hot issues | 11 | v0.59.0-nightly (security patch) | High — security + reliability focus |
| **GitHub Copilot CLI** | 10 hot issues | 0 | v1.0.81-12/13/14 | Low PR velocity, steady prerelease cadence |
| **Kimi Code** | 1 hot issue | 1 | None | Low — quiet cycle |
| **OpenCode** | 10 hot issues | 10 | None | High — subagent reliability crisis dominant |
| **Pi** | 9 hot issues | 10 | None | High — compaction + Windows fixes |
| **Qwen Code** | 10 hot issues | 10 | v0.22.2, Desktop v0.2.2, cua-driver-rs v0.20.1 | High — multi-component release |
| **DeepSeek TUI** | 10 hot issues | 10 | None | High — active refactor + recovery sprints |
| **Grok Build** | — | — | — | No activity |

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Subagent reliability & loop detection** | OpenCode, Gemini CLI, Claude Code, Codex | No-progress detection, MAX_TURNS recovery, infinite-loop guardrails, orphan cleanup |
| **MCP configuration hardening** | Gemini CLI, OpenCode, Copilot CLI, Codewhale | Fail-closed on corrupt config, schema dialect compatibility (draft-07), secret scoping, process pooling |
| **Context/compaction management** | Pi, Qwen Code, Codex, OpenCode | Configurable compaction models/thinking levels, token-budget awareness, retained-image budgeting, on-demand recall |
| **Windows desktop stability** | Claude Code, Codex, Pi, Copilot CLI | GPU crashes, MSIX registration, PowerShell 5.1 fallback, WSL execution, WAM auth |
| **Long-term memory infrastructure** | Qwen Code, Gemini CLI, Pi | Structured push/pull recall, AST-aware reads, configurable memory providers (Mem0) |
| **Observability & telemetry** | Copilot CLI, Claude Code, OpenCode, Gemini CLI | OTLP identity attributes, trace context propagation, per-thread usage, hook instrumentation |
| **Terminal/TUI experience** | OpenCode, Pi, Copilot CLI, Gemini CLI | Disable clickable prompts, keyboard-only flows, multiline paste OOM fixes, TUI accessibility |
| **Cross-repo/global config** | Copilot CLI, OpenCode, Claude Code | Global instructions file, auto-allow permissions, project-scoped MCP pooling |
| **Agent autonomy & skill utilization** | Gemini CLI, OpenCode, Codex | Custom skills not being invoked, browser agent session recovery, Wayland support |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi Code |
|-----------|-------------|-------------|------------|-------------|----------|-----|-----------|--------------|-----------|
| **Core differentiator** | Structured feedback tool, MCP compatibility focus | Remote compaction, Guardian analytics, model confirmation policies | SSRF/security hardening, AST-aware reads | Session resume perf, WAM auth on Windows | Subagent loop crisis, memory megathread | Compaction configurability, Windows tooling fixes | Memory push/pull protocol, standalone MCP REPL | Multi-session scoped runtime, migration planner | Kimi Code — minimal activity, lifecycle cancellation focus |
| **Target user** | Enterprise/technical (Opus focus, EU regulatory awareness) | Broad developer base, plus subscribers | Security-conscious, agent-reliability focused | GitHub-integrated workflows | Power users, multi-agent workflows | Reasoning-model users, local-model workflows | Open-weight enthusiasts, multi-provider users | Cron + active-conversation hybrid users |
| **Technical approach** | Configuration-driven, feedback drafts, tip system | Rust-native, SSE/WebSocket/ACP multi-transport | Bash affinity, skill system, variable-expansion security | Hook-based extensibility, ACP mode | Multi-subagent concurrency, SQLite persistence | Fork-based sessions, ctx.cwd-aware tools | Structured memory, configurable provider extensions | Unified runtime threads, process-group reaping |
| **Release cadence** | Steady patch releases | Rapid alpha track + stable patches | Nightly security-focused | Prerelease patches | No recent releases | No recent releases | Multi-component releases | No recent releases | No recent releases |

---

## 5. Community Momentum & Maturity

**High Momentum / Rapid Iteration:**
- **OpenAI Codex** — 10 PRs in 24h, active alpha track (0.151.x), strong feature velocity on compaction and policy propagation
- **Gemini CLI** — 11 PRs including 4 security fixes, nightly cadence with rapid vulnerability response
- **Qwen Code** — Multi-component release (CLI + Desktop + driver), structured memory architecture, autofix CI pipeline
- **DeepSeek TUI** — 10 PRs recovering contributor work, active refactor sprint (#5586 mega-files), migration tooling

**Mature but Stress-Testing:**
- **Claude Code** — Lower PR velocity (2 PRs) but high-issue engagement; enterprise-grade concerns (Opus regression, OAuth revocation) signal a maturing but strained user base
- **Pi** — 10 PRs focused on regression fixes; compaction reliability (#6879) is the dominant frustration, indicating a tool that has outgrown its context-management layer
- **OpenCode** — 10 PRs but community is in crisis mode over subagent infinite loops; the memory megathread (#20695, 138 comments) suggests architectural debt

**Emerging / Lower Activity:**
- **Copilot CLI** — Stable prerelease cadence but zero PR updates; community troubleshooting regressions rather than driving features
- **Kimi Code** — Minimal 24h activity (1 issue, 1 PR); likely in a quiet development phase

---

## 6. Trend Signals

1. **Subagent reliability is the #1 unsolved problem.** OpenCode's megathread (138 comments), Gemini's MAX_TURNS bug (#22323), and Claude Code's Opus regression (#68780) all point to a ecosystem-wide gap: multi-subagent workflows are unreliable. Tools that ship robust loop detection and graceful degradation will gain significant trust.

2. **MCP is both the biggest opportunity and the biggest friction point.** Incompatible schema dialects (Claude Code #86142), corrupted config silent-enabling (Gemini CLI #28787), eager token-bloat injection (Copilot CLI #4613), and secret-scoping design gaps (Codewhale #5637) indicate the MCP ecosystem is outpacing tooling compatibility. Standardization pressure will grow.

3. **Context management is bifurcating into two strategies.** Pi and Qwen Code are investing in *configurable, model-aware compaction* (separate thinking levels, on-demand recall). Codex and OpenCode are focusing on *token-budget enforcement* (retained-image budgeting, no-progress detection). The winner will likely combine both.

4. **Windows desktop is the universal weak spot.** GPU crashes (Claude Code), CLI binary not found (Codex), PowerShell 5.1 fallback (Pi), WSL auth (Copilot CLI), and always-on-top regressions (Claude Code) suggest cross-platform parity remains unresolved across the ecosystem.

5. **Security hardening is accelerating post-SSRF.** Gemini CLI's nightly security patch (SSRF in MCP OAuth, variable-expansion bypass, workspace trust fail-closed) signals that AI CLI tools are becoming attack surfaces. Expect more GHSA-style disclosures and defense-in-depth PRs.

6. **Memory infrastructure is becoming a differentiator.** Qwen Code's structured push/pull recall, Pi's configurable compaction models, and Gemini's AST-aware reads all point to a shift from flat prompt injection to queryable, structured long-term memory. This is the next frontier.

7. **Developer trust is eroding around silent data loss.** Transcript corruption (Kimi #2620), orphan sub-sessions (OpenCode #37314), and whitespace-bricked sessions (Pi #8720) are recurring themes. Tools that prioritize transcript integrity and recovery will stand out.

---

*Report generated from community digest data across 10 AI CLI tools as of 2026-08-27.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-27 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking — Most-Discussed

| Rank | Skill / PR | Status | Engagement | Summary |
|------|-----------|--------|------------|---------|
| 1 | **Security: Community skills under `anthropic/` namespace** — [Issue #492](https://github.com/anthropics/skills/issues/492) | Open · 43 comments | ⚠️ Trust boundary vulnerability where community-made skills impersonate official Anthropic skills, potentially tricking users into granting elevated permissions. The most-discussed item in the repo. |
| 2 | **Org-Wide Skill Sharing** — [Issue #228](https://github.com/anthropics/skills/issues/228) | Open · 16 comments · 👍 8 | Users want built-in organizational skill distribution instead of manual .skill-file sharing via Slack/Teams. |
| 3 | **`run_eval.py` trigger bug** — [Issue #556](https://github.com/anthropics/skills/issues/556) / [PR #1298](https://github.com/anthropics/skills/pull/1298) | Both Open | `claude -p` never triggers installed skills, reporting 0% recall across all queries — breaking the entire skill-description optimization loop. Multiple overlapping PRs ([#1298](https://github.com/anthropics/skills/pull/1298), [#1099](https://github.com/anthropics/skills/pull/1099), [#1050](https://github.com/anthropics/skills/pull/1050)) targeting the same root cause on different platforms. |
| 4 | **`claude-api` token bloat** — [Issue #1487](https://github.com/anthropics/skills/issues/1487) | Open · 4 comments | The bundled `claude-api` skill eagerly injects ~156k tokens in a single tool call, exhausting context windows. |
| 5 | **Duplicate skills from plugin overlap** — [Issue #189](https://github.com/anthropics/skills/issues/189) | Open · 6 comments · 👍 9 | `document-skills` and `example-skills` install identical content, wasting context window; 9 upvotes signal strong community frustration. |
| 6 | **`mcp-builder` evaluation harness broken** — [Issue #1390](https://github.com/anthropics/skills/issues/1390) / [PR #1602](https://github.com/anthropics/skills/pull/1602) | Both Open | `evaluation.py` silently fabricates tool-execution errors against real MCP servers, scoring 0/N. PR [#1602](https://github.com/anthropics/skills/pull/1602) addresses serialization and encoding fixes. |
| 7 | **Skill-Quality & Skill-Security Analyzers** — [PR #83](https://github.com/anthropics/skills/pull/83) | Open | Meta-skills that audit other skills across five dimensions (structure, documentation, examples, security, quality). Addresses the growing need for skill governance. |
| 8 | **Self-Audit — Mechanical Verification + Four-Dimension Reasoning Gate** — [PR #1367](https://github.com/anthropics/skills/pull/1367) | Open | Audits AI output before delivery: verifies claimed files exist, then applies a four-dimension reasoning quality gate. |

---

## 2. Community Demand Trends (from Issues)

| Demand Area | Evidence |
|-------------|---------|
| **Governance & Safety** | Issue #492 (trust-boundary abuse), #412 (agent-governance skill proposal), #1175 (SharePoint permission security), #83 (skill-security-analyzer) — community is increasingly concerned about skill trust, auditability, and policy enforcement. |
| **Evaluation & Quality Gates** | Issues #556, #1390, #1487 + PRs #1298, #1367, #1602 — broken eval tooling and context-wasting skills are top pain points; strong demand for reliable skill verification pipelines. |
| **Enterprise / Platform Skills** | Issue #228 (org sharing), PR #568 (ServiceNow), PR #1615 (SCNet HPC) — users are pushing skills into specialized enterprise platforms (ITSM, HPC clusters, SharePoint). |
| **Developer Tooling** | PR #723 (testing-patterns), PR #514 (document-typography), PR #486 (ODT), PR #525 (pyxel) — broad appetite for workflow-specific skills covering testing, document quality, and niche development domains. |
| **Multi-Agent Orchestration** | PR #1628 (Hivemind — delegating to headless opencode workers) and Issue #16 (expose skills as MCPs) — community is exploring cost-efficient multi-agent patterns and API-style skill interfaces. |

---

## 3. High-Potential Pending Skills

| PR | Skill | Why It May Land Soon |
|----|-------|---------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator fix (run_eval.py)** | Blocks the entire skill-description optimization loop; 10+ independent reproductions reported in [#556](https://github.com/anthropics/skills/issues/556). Critical infrastructure fix. |
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind — Multi-Agent Orchestration** | Addresses the most-discussed cost-efficiency problem (expensive model context is the scarce resource); novel architecture using free-model headless workers. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit (v1.3.0)** | Directly responds to governance concerns raised in Issue #492 and #1385; universal, stack-agnostic quality gate. |
| [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer & skill-security-analyzer** | Fills the meta-skill gap for auditing the growing skill catalog; aligns with community security demands. |
| [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow Platform Skill** | Covers 8 enterprise sub-domains (ITSM, ITOM, SecOps, ITAM/SAM, FSM, SPM, CSDM, IntegrationHub); broad enterprise appeal. |
| [#1602](https://github.com/anthropics/skills/pull/1602) | **mcp-builder reliability fixes** | Fixes evaluation serialization, benchmark metrics, and script stability — unblocks the MCP skill development pipeline. |
| [#514](https://github.com/anthropics/skills/pull/514) | **Document-Typography Skill** | Solves a universal pain point (orphans, widows, numbering misalignment) affecting every AI-generated document; niche but high-impact. |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable skill evaluation and governance infrastructure** — broken eval tooling (`run_eval.py`, `evaluation.py`) and trust-boundary vulnerabilities are generating more discussion than any new skill proposal, signaling that the ecosystem is shifting from "more skills" to "better-verified, safer skills."

---



# Claude Code Community Digest — 2026-08-27

## 1. Today's Highlights
Claude Code v2.1.247 introduces a new `SendFeedback` tool for structured in-session error reporting. The community's attention is dominated by Windows desktop stability regressions (GPU crashes, MSIX registration failures, and an intrusive always-on-top behavior) and ongoing concerns about Opus 4.8/5.0 reasoning performance. Authentication and MCP compatibility friction also continue to generate significant discussion.

## 2. Releases
**v2.1.247**
- Adds the `SendFeedback` tool, enabling Claude to draft contextual feedback reports that users can review and submit via `/feedback`. Controlled by the `feedbackDrafts` setting.
- Updates config entry structures (`{id, text, cooldownSessions, priority}`), `tipsFile`, and `label` handling.
- [View Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.247)

## 3. Hot Issues
1. **#80444** — Windows desktop fatal GPU-process crash via in-app browser tab, leaving MSIX package unlaunchable.  
   *Why it matters:* Core desktop stability on Windows; crashes corrupt package state and block future launches.  
   *Community reaction:* 63 comments, 11 👍 — multiple reproductions across driver versions.  
   [Link](https://github.com/anthropics/claude-code/issues/80444)

2. **#12506** — Execute shell commands in WSL instead of Windows CMD/PowerShell.  
   *Why it matters:* Critical for cross-platform devs running Claude Desktop on Windows with Linux-native toolchains.  
   *Community reaction:* 43 comments, 146 👍 — highly upvoted feature request.  
   [Link](https://github.com/anthropics/claude-code/issues/12506)

3. **#68780** — Opus 4.8/5.0 reasoning degradation and performance regression.  
   *Why it matters:* Directly impacts prompt reliability and throughput for enterprise/technical users.  
   *Community reaction:* 36 comments, 35 👍 — includes EU regulatory escalation language.  
   [Link](https://github.com/anthropics/claude-code/issues/68780)

4. **#18467** — Personal GitHub repositories invisible in Claude web; org repos work fine.  
   *Why it matters:* Breaks standard developer workflows and suggests an asymmetry in OAuth/app permissions.  
   *Community reaction:* 36 comments, 78 👍 — widely reproduced.  
   [Link](https://github.com/anthropics/claude-code/issues/18467)

5. **#43801** — OAuth token revocation via claude.ai does not invalidate active CLI/extension sessions.  
   *Why it matters:* Security-critical; undermines session management and credential rotation guarantees.  
   *Community reaction:* 34 comments, 5 👍 — flagged as confirmed after 3–4 days and cold boot.  
   [Link](https://github.com/anthropics/claude-code/issues/43801)

6. **#85891** — Claude Desktop (Windows) window stuck always-on-top with no disable option.  
   *Why it matters:* UX regression that disrupts multi-window workflows and lacks a configuration toggle.  
   *Community reaction:* 31 comments, 62 👍 — mirrors a closed macOS counterpart (#66516).  
   [Link](https://github.com/anthropics/claude-code/issues/85891)

7. **#86142** — MCP servers declaring `draft-07` outputSchema rejected client-side as "unsupported dialect".  
   *Why it matters:* Blocks adoption of widely-used MCP servers that haven't migrated to newer JSON Schema drafts.  
   *Community reaction:* 30 comments, 12 👍 — compatibility/regression concern.  
   [Link](https://github.com/anthropics/claude-code/issues/86142)

8. **#70622** — Option to disable clickable Yes/No prompts in terminal.  
   *Why it matters:* Clickable permission UI interferes with TTY workflows, screen readers, and automation.  
   *Community reaction:* 22 comments, 83 👍 — strong demand for configurability.  
   [Link](https://github.com/anthropics/claude-code/issues/70622)

9. **#57371** — Provide option to disable the bundled Cowork background service (`CoworkVMService`) on Windows.  
   *Why it matters:* Unnecessary background process consumes resources for users who don't use Cowork.  
   *Community reaction:* 24 comments, 53 👍 — requested for cleaner deployments.  
   [Link](https://github.com/anthropics/claude-code/issues/57371)

10. **#88490** — Cloud Cowork sessions intermittently export OTLP telemetry without identity attributes.  
    *Why it matters:* Breaks observability pipelines and audit trails for managed/cloud deployments.  
    *Community reaction:* 2 comments, 17 👍 — recent onset (~Aug 18) noted.  
    [Link](https://github.com/anthropics/claude-code/issues/88490)

## 4. Key PR Progress
*Note: Only 2 PRs were updated in the 24h window, indicating low merge activity this cycle.*

1. **#13437** — `fix(hookify): use relative imports for Python module resolution`  
   Resolves a recurring `No module named hookify` error by switching from absolute to relative imports, fixing plugin resolution across platforms.  
   [Link](https://github.com/anthropics/claude-code/pull/13437)

2. **#58673** — *Title/summary truncated in source data*  
   No substantive description available in the reporting window.  
   [Link](https://github.com/anthropics/claude-code/pull/58673)

## 5. Feature Request Trends
- **Native WSL/Unix shell execution** on Windows to match Linux-native developer expectations.
- **Configurable terminal UX**, particularly disabling clickable permissions and enabling keyboard-only confirmation flows.
- **Platform-specific resource controls**, such as opting out of background services (Cowork) and toggling window behavior.
- **Flexible git workflows**, including pushing to task-assigned branches rather than forced `claude/*` prefixes.
- **Structured feedback & observability**, with built-in feedback drafting and reliable identity mapping in telemetry exports.

## 6. Developer Pain Points
- **Windows desktop instability:** Recurring GPU-process crashes, MSIX package corruption, and orphaned Windows Job Objects that prevent app relaunch without reboot.
- **Authentication & permission gaps:** OAuth revocation not propagating to active sessions, and inconsistent repository visibility between personal and org accounts.
- **MCP ecosystem friction:** Overly strict schema dialect validation blocking legitimate `draft-07` tool definitions.
- **CLI terminal usability:** Aggressive clickable permission UI conflicting with standard TTY/automation workflows.
- **Model reliability concerns:** Perceived reasoning and latency regressions in recent Opus updates, impacting trust in automated code generation.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-27

## 1. Today's Highlights

The `rust-v0.150.1` patch release went live, backporting a critical remote-compaction fix (#41003) that now counts retained images against the token budget by default. Meanwhile, the Windows Desktop app remains the #1 pain point this cycle, with multiple high-visibility startup and handshake failures reported across v26.820.x builds.

---

## 2. Releases

**rust-v0.150.1** — Bug-fix patch for the stable line.

- Retained images in remote compaction are now charged against the compaction token budget by default; older images are trimmed as needed. Explicit opt-out preserves previous behavior. [PR #41003](https://github.com/openai/codex/pull/41003)

**Alpha track (0.151.0):** `alpha.2` → `alpha.5` released over the past few days.

**Full changelog (0.150.0 → 0.150.1):** [Compare](https://github.com/openai/codex/compare/rust-v0.150.0...rust-v0.150.1)

---

## 3. Hot Issues

1. **[Windows Desktop fails to start after v26.820.60940 update](https://github.com/openai/codex/issues/40752)** — 82 comments · 49 👍 · `windows-os, app`
   The most engaged issue of the cycle. The `.cmd` wrapper throws `EINVAL` on spawn and the app reports "Unable to locate Codex CLI." Affects multiple Plus subscribers; widely seen as a regression from the latest desktop update.

2. **[macOS auth invalidation on existing conversation](https://github.com/openai/codex/issues/39162)** — 64 comments · 38 👍 · `macOS, auth, app`
   Opening an existing conversation on v26.814.41407 logs the user out and redirects to sign-in. Confirmed as a regression from v26.810.52044 (last known-good build).

3. **[Windows Desktop fails to create chats in WSL mode](https://github.com/openai/codex/issues/40881)** — 27 comments · 8 👍 · `windows-os, mcp, app`
   New chats fail with "invalid transport in `mcp_servers.codex_app`" on v26.820.7780.0. Blocks a significant subset of Windows users who rely on WSL as their agent environment.

4. **[Windows Store app fails on startup: CLI binary not found](https://github.com/openai/codex/issues/28392)** — 16 comments · 0 👍 · `windows-os, app`
   Persistent issue where the Store-installed Codex cannot locate the bundled CLI binary at launch. Low engagement but still open after months, indicating an unresolved environment-detection bug.

5. **[Windows Remote: QR pairing succeeds but session cannot establish](https://github.com/openai/codex/issues/39856)** — 14 comments · 0 👍 · `windows-os, remote`
   Android clients report `nextConnectionCount=0` after QR pairing on v26.818.31338. Blocks the Windows Remote feature entirely for affected users.

6. **[Telemetry DB write lock hard-fails CLI startup](https://github.com/openai/codex/issues/35555)** — 9 comments · 1 👍 · `CLI, session`
   Any process holding a write lock on `logs_2.sqlite` causes a flat 5s busy_timeout and aborts boot before auth. Critical for users running parallel CLI instances or background telemetry writers.

7. **[code-mode host exits during handshake — GPT-5.6](https://github.com/openai/codex/issues/41049)** — 9 comments · 0 👍 · `windows-os, tool-calls, app`
   Local tool channel fails during initialization handshake for the 5.6 model. Users report directory-reading tools fail immediately, suggesting a regression in the code-mode host stability.

8. **[Windows Desktop: `read_thread` returns empty items for visible completed turn](https://github.com/openai/codex/issues/40014)** — 11 comments · 2 👍 · `windows-os, app`
   A completed child turn renders in the UI but `read_thread` returns `items: []`. Indicates a desync between the presentation layer and the thread storage backend.

9. **[Windows desktop exits after memory-leak / hang events](https://github.com/openai/codex/issues/35963)** — 6 comments · 0 👍 · `windows-os, app, performance`
   Intermittent unresponsiveness or hard exit during task execution on v26.721.4979.0. Suggests a memory-management issue in the long-running app-server process.

10. **[Windows App fails to start: bundled CLI exists but cannot execute](https://github.com/openai/codex/issues/40867)** — 9 comments · 7 👍 · `windows-os, app`
    A distinct variant of #40752 — the CLI binary is present but execution fails, pointing to potential sandbox or permission issues in the MSIX bundle.

---

## 4. Key PR Progress

1. **[Expose response usage metadata in completion events](https://github.com/openai/codex/pull/41087)** — Parses `usage_metadata.amount` from Responses API completion events and propagates through SSE, WebSocket, regular turns, and remote compaction.

2. **[Forward model confirmation policies to actor MCP tools](https://github.com/openai/codex/pull/41072)** — Browser Use and Computer Use confirmation-policy Markdown now flows into model catalog messages and `openai/confirmation_policies` metadata for `node_repl` / `cua_repl` tool calls.

3. **[Clarify when to send asynchronous user messages](https://github.com/openai/codex/pull/41070)** — Expands `send_user_message_async` docs to distinguish urgent questions/blockers from routine progress updates, reducing noisy async notifications.

4. **[Forward truncation policies to the history notes backend](https://github.com/openai/codex/pull/41062)** — Each history/notes request now sends `x-openai-tool-output-truncation-policy` in headers; tool requests inherit the caller's policy.

5. **[Track Code Mode tool-call metadata completeness](https://github.com/openai/codex/pull/41058)** — Associates recorded tool-call metadata with Code Mode cells so consumers can distinguish full inventories from partial `exec`/`wait` output records.

6. **[Add developer instructions for Persistent reasoning mode](https://github.com/openai/codex/pull/41050)** — Bundles proactivity and follow-up guidance when `ReasoningEffort::Persistent` is selected; model metadata can override via `persistent_instructions`.

7. **[Encrypt sensitive history and notes tool arguments](https://github.com/openai/codex/pull/41041)** — Search queries, appended note text, and replacement text are now marked encrypted in tool schemas; backend routes receive `x-openai-encrypted-tool-arguments: true`.

8. **[Propagate trace context through gRPC Code Mode](https://github.com/openai/codex/pull/41017)** — W3C `traceparent` metadata injected into code-mode session and execution requests; spans remain connected across the gRPC boundary.

9. **[Enable retained-image budgeting by default](https://github.com/openai/codex/pull/40994)** — Promotes `compaction_image_budget` to stable; retained images charge against the remote-compaction context budget, trimming older images as needed. (Backported to 0.150 via #41003.)

10. **[Scope extension capabilities to invocation lifetimes](https://github.com/openai/codex/pull/41020)** — Adds callback lifetimes to extension `ToolCall`, `ToolEnvironment`, and turn-input types; extension executors must handle calls for any invocation lifetime.

---

## 5. Feature Request Trends

- **MCP process pooling** — [#20883](https://github.com/openai/codex/issues/20883) requests a project-scoped MCP process pool instead of per-session spawning, a pattern echoed in #38925 (stdio MCP accumulation).
- **TUI accessibility improvements** — [#23652](https://github.com/openai/codex/issues/23652) (20 👍) adds mouse-click cursor navigation to the TUI input box; #37884 and #37849 flag scrolling and jump behavior on long responses.
- **Guardian and analytics parity** — #41023 and #41006 close gaps in Guardian session analytics and trust for user-owned skills; community expects similar coverage for Code Mode and MCP tool usage.
- **Trusted access for plugins** — #41005 attaches `cyber_trusted_access` to eligible plugin MCP calls, suggesting growing demand for verified entitlement propagation.
- **Async messaging discipline** — #41070's clarification of `send_user_message_async` reflects community interest in reducing notification fatigue from background tool activity.

---

## 6. Developer Pain Points

- **Windows Desktop startup regressions dominate.** Five+ high-profile issues this cycle (#40752, #40867, #28392, #41015, #40817) trace to the v26.820.x update — CLI binary not found, execution failures, missing sandbox files, and frozen animations. This is the single largest developer frustration on the tracker.
- **Auth/session instability.** Issues #39162 (macOS), #39925 (Windows refresh-token rejection), and #40014 (empty thread items) share a pattern: the app appears to work but silently drops authentication state or thread data, causing confusing user-facing failures.
- **MCP server lifecycle management.** #20883 and #38925 both report that MCP processes accumulate or fail to share across sessions in the same project, pointing to a missing connection-pooling layer.
- **Windows Remote session pairing.** #39856 and #39855 show consistent failures in the remote-chat flow (QR pairing succeeds but `nextConnectionCount=0`, trust verification with malformed paths), suggesting a regression in the remote transport layer.
- **Telemetry DB blocking CLI boot.** #35555 highlights a hard start-up failure when any process holds a lock on `logs_2.sqlite`, affecting users who run parallel CLI invocations or background telemetry writers.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-27

---

## 1. Today's Highlights

A critical security patch lands tonight: **v0.59.0-nightly** addresses an SSRF vulnerability in MCP OAuth metadata discovery and authentication (PR #29081). Meanwhile, community momentum builds around agent reliability — the generalist agent hang (#21409) and subagent recovery after MAX_TURNS (#22323) remain the top-discussed bugs, and multiple PRs converge on hardening MCP configs and variable-expansion bypasses.

---

## 2. Releases

### v0.59.0-nightly.20260827.g3c311beac

- **Security fix:** Prevents SSRF in MCP OAuth metadata discovery and authentication paths.
- Changelog: [v0.59.0-nightly.20260826 → v0.59.0-nightly.20260827](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260826.g64b5b79a6...v0.59.0-nightly.20260827.g3c311beac)

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports GOAL success after hitting MAX_TURNS | Misleading success status masks incomplete work — directly impacts reliability of multi-subagent workflows. | 13 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | Simple tasks (e.g., folder creation) stall for hours; currently the most upvoted open agent bug. | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Bash affinity | Proposes leveraging Gemini's native bash skills safely — a major architectural enhancement if adopted. | 8 comments · 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search & mapping | Could dramatically reduce token waste and turn count by enabling surgical codebase reads. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini underutilizes skills and sub-agents | Anecdotal but widespread: model ignores custom skills unless explicitly prompted. | 6 comments · 0 👍 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Memory system can loop on the same unprocessed sessions, wasting resources. | 5 comments · 0 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Secrets may already be in model context before redaction — a real privacy concern. | 4 comments · 0 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck at "Waiting input" after completion | Simple CLI commands hang with a false "awaiting user input" state — high friction for daily use. | 4 comments · 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent lacks session takeover & lock recovery | Persistent browser sessions fail hard on orphaned processes; no graceful recovery. | 4 comments · 0 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Blocks Linux/Wayland users from browser automation entirely. | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| # | PR | Type | Summary |
|---|-----|------|---------|
| [#29081](https://github.com/google-gemini/gemini-cli/pull/29081) | fix(core): prevent SSRF in MCP OAuth | **Security** | Blocks SSRF in MCP OAuth metadata discovery — part of tonight's nightly release. |
| [#28902](https://github.com/google-gemini/gemini-cli/pull/28902) | fix(core): block $VAR expansion bypass | **Security** | Closes a variable-expansion bypass in bash/PowerShell detection (GHSA-wpqr-6v78-jr5g). Defense-in-depth hardening. |
| [#29099](https://github.com/google-gemini/gemini-cli/pull/29099) | fix(core): fail-closed workspace trust | **Security** | Filters `mcpServers` from untrusted repos in `@google/gemini-cli-a2a-server`; prevents unintended process execution. |
| [#28787](https://github.com/google-gemini/gemini-cli/pull/28787) | fix(cli): corrupt MCP enablement config | **Fix** | Stops treating corrupted MCP config as empty `{}` — was causing all servers to silently re-enable. (Closed) |
| [#28794](https://github.com/google-gemini/gemini-cli/pull/28794) | fix(cli): fail-closed on corrupt MCP config | **Fix** | Companion to #28787 — prevents fail-open and data loss when `mcp-server-enablement.json` is malformed. (Closed) |
| [#28914](https://github.com/google-gemini/gemini-cli/pull/28914) | fix(core): inject on-retry nudge into contents | **Fix** | Moves retry nudge from `systemInstruction` to conversation `contents`, preserving prefix caching. |
| [#28917](https://github.com/google-gemini/gemini-cli/pull/28917) | fix(core): atomic Whisper model downloads | **Fix** | Downloads to temp file, verifies length, cleans up on failure, atomically renames — fixes race conditions. |
| [#28916](https://github.com/google-gemini/gemini-cli/pull/28916) | fix(core): buffer partial Whisper stdout | **Fix** | Line-buffers stdout chunks in `WhisperTranscriptionProvider` so split transcription lines are no longer dropped. |
| [#29104](https://github.com/google-gemini/gemini-cli/pull/29104) | feat(cli): [Skill] tag in autocomplete | **Feature** | Adds `[Skill]` badge to slash-command autocomplete, matching existing `[MCP]` and `[Agent]` visual treatment. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | fix(extensions): consent on env changes | **Security** | Extensions can no longer bypass consent to inject env vars into MCP server processes; sanitizes runtime-altering vars. |

---

## 5. Feature Request Trends

- **Agent autonomy & reliability:** The community repeatedly flags that Gemini doesn't adequately use its own skills/sub-agents (#21968) and that subagent recovery is broken (#22323). Expect continued pushes for more robust agent orchestration.
- **Token-efficient codebase navigation:** AST-aware reads (#22745, #22746) and "tactful extraction" (#19561) both target the chronic problem of context bloat from naive file reads.
- **Sandboxing & security hardening:** Multiple parallel efforts — zero-dependency OS sandboxing (#19873), MCP config fail-closed behavior (#28787, #28794, #29099), variable-expansion bypass fixes (#28902), and extension env sanitization (#28863) — signal a strong trend toward stricter security defaults.
- **Memory system maturity:** Auto Memory bugs (#26522, #26525, #26523) show the community wants a memory system that is both privacy-preserving and avoids infinite retry loops.
- **Cross-platform browser support:** Wayland failures (#21983) and lock-recovery gaps (#22232) indicate demand for more resilient, platform-agnostic browser automation.

---

## 6. Developer Pain Points

1. **Agent hangs and false terminations** — The generalist agent hanging (#21409, 8 👍) and subagents reporting GOAL success despite hitting turn limits (#22323) are the most cited reliability issues. These directly block productive workflows.
2. **Shell command state getting stuck** — Commands completing but leaving the CLI in a persistent "Waiting input" state (#25166, 3 👍) create confusing UX and require manual cancellation.
3. **MCP configuration fragility** — Corrupted JSON in MCP enablement configs was silently enabling every server (#28787, #28794), a high-severity issue affecting trust in the config system.
4. **Auto Memory privacy & loops** — Secrets potentially reaching model context before redaction (#26525) and low-signal sessions being retried indefinitely (#26522) are frustrating both from security and performance perspectives.
5. **Platform-specific browser failures** — Wayland (#21983) and persistent-session lockouts (#22232) block entire user segments from browser automation features.
6. **Skills going unused** — Users report that custom skills are ignored unless explicitly commanded (#21968), undermining the extensibility investment.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-27

## 1. Today's Highlights

GitHub released three prerelease patches (v1.0.81-12 through v1.0.81-14) focused on session resume performance, OpenTelemetry hook instrumentation, and Windows WAM authentication. The community is actively troubleshooting a high-severity regression where MCP schemas are eagerly injected at startup, bloating the first request by ~354 K tokens, alongside several Gemini-specific model and transport bugs.

## 2. Releases

**v1.0.81-14** — Resumes large sessions faster by rendering recent history first while older messages load in the background. Fixed a bug where repeated `read_agent` calls inconsistently returned full turn history.
[GitHub](https://github.com/github/copilot-cli/releases/tag/v1.0.81-14)

**v1.0.81-13** — Hooks now receive the current OpenTelemetry `traceparent` (and `tracestate` when applicable), enabling correlated span emission. Command hooks also gain access to env vars. Fixed `hook.start`/`hook.end` lifecycle events firing incorrectly for hooks inside a subagent.
[GitHub](https://github.com/github/copilot-cli/releases/tag/v1.0.81-13)

**v1.0.81-12** — On Windows, remote MCP servers protected by Microsoft Entra ID can now authenticate through the OS Web Account Manager (WAM) broker, typically with no prompt. Other platforms retain the existing browser/device-code flow.
[GitHub](https://github.com/github/copilot-cli/releases/tag/v1.0.81-12)

## 3. Hot Issues

| # | Title | Status | Engagement | Why It Matters |
|---|-------|--------|------------|----------------|
| [#4613](https://github.com/github/copilot-cli/issues/4613) | MCP schemas eagerly injected, adding 354 K startup tokens | OPEN | 2 comments | High-severity regression from 1.0.80+; every new session bloats the first request with the full ambient MCP catalog even for trivial prompts. |
| [#4612](https://github.com/github/copilot-cli/issues/4612) | Runaway FileWatch loop freezes TUI and grows debug log to 13 GB | OPEN | 4 comments, 1 👍 | Long-running/resumed sessions can enter a tight `FileWatch` host-event loop that stops the TUI from responding. |
| [#4533](https://github.com/github/copilot-cli/issues/4533) | TUI stops consuming events when a turn spawns parallel subagents | OPEN | 3 comments | Terminal input and scroll go dead at the moment parallel subagents launch, though the Rust runtime continues working. |
| [#407](https://github.com/github/copilot-cli/issues/407) | Add `/tools` slash command to list all available tools | OPEN | 2 comments, **31 👍** | Top-voted feature request — users struggle to discover CLI tooling capabilities without a built-in listing command. |
| [#252](https://github.com/github/copilot-cli/issues/252) | Global Instructions File Support | **CLOSED** | 11 comments, 12 👍 | Users repeat the same instructions across every repo; a global config file would eliminate that friction. |
| [#2712](https://github.com/github/copilot-cli/issues/2712) | MS legal/monetary liability for rate-limit behavior | OPEN | 6 comments, 4 👍 | Rate limits can trigger without user action (fleet, background agents, multi-command runs), raising compliance concerns. |
| [#2873](https://github.com/github/copilot-cli/issues/2873) | Copilot Pro subscription and Opus models | OPEN | 5 comments | Pro subscribers lost access to Opus models entirely; users object to full removal versus the request multiplier. |
| [#4605](https://github.com/github/copilot-cli/issues/4605) | `latest-prerelease` lookup strands users on 1.0.81-9 | OPEN | 1 comment, 3 👍 | Pre-release releases share `created_at`, so GitHub ranks -10 below -2 and the older build is reported as latest. |
| [#4623](https://github.com/github/copilot-cli/issues/4623) | Gemini models fail with 400 for MCP tools using union-type arrays | OPEN | 0 comments | Any MCP tool whose array `items` schema is `["object", "null"]` breaks every Gemini model call; GPT/Claude unaffected. |
| [#4103](https://github.com/github/copilot-cli/issues/4103) | Plugin marketplace clone disables Git credential helpers | **CLOSED** | 3 comments, 3 👍 | Adding a marketplace plugin from a private Azure DevOps HTTPS repo fails; v1.0.70 change strips credential helpers. |

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

- **Global / cross-repo configuration** — A global instructions file (#252) and auto-allow permissions on session start (#3877) both target reducing repetitive setup across worktrees.
- **Tool discoverability** — The `/tools` slash command (#407, 31 👍) remains the most upvoted open request, signaling strong demand for introspection into available capabilities.
- **Multi-agent control** — Users want to delegate to Claude and Codex via `/delegate` (#1499, 6 👍), extending beyond the default Copilot coding agent.
- **MCP & transport compliance** — Requests for stdio transport in ACP mode (#3889) and better `TaskShellProgress` output exposure (#4630) point to growing MCP integration complexity.
- **Session resume fidelity** — Hooks not loading on `--resume` (#4629) and parallel-subagent TUI freezes (#4533) highlight a need for parity between fresh and resumed sessions.

## 6. Developer Pain Points

- **Startup bloat from eager MCP schema injection** — The 354 K token hit (#4613) directly increases latency and cost on every session start.
- **TUI unresponsiveness under load** — Multiple reports (#4612, #4533) show the terminal UI freezing during long-running sessions or when parallel subagents launch, while the backend continues processing.
- **Gemini model incompatibilities** — Both a 400 Bad Request issue with plain prompts (#4155) and a union-type schema failure with MCP tools (#4623) suggest Gemini integration needs closer scrutiny.
- **Non-interactive session permission revocation** — In `-p` / autopilot mode, tool-call approvals can be silently revoked mid-session (#4433), causing unrecoverable permission-denied loops.
- **Autopilot timeout misbehavior** — The 600-second background-task timeout terminates the parent process even after the subagent completes and the parent resumes work (#4628).
- **Authentication edge cases** — WSL-specific OAuth 404s (#4632) and Windows WAM broker availability gaps (#4627) continue to surface platform-specific auth friction.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-27

## 1. Today's Highlights

One new issue and one open PR were updated in the last 24 hours on `MoonshotAI/kimi-cli`. No releases were published today. The community is tracking a cron-related transcript corruption bug and an ongoing fix for nested task cancellation in the `soul` lifecycle.

## 2. Releases

No new releases in the past 24 hours.

## 3. Hot Issues

**Issue #2620** — [Cron fire mid-reply swallows the previous assistant reply](https://github.com/MoonshotAI/kimi-cli/issues/2620)
- **Author:** tizerluo | **Created:** 2026-08-26 | **Comments:** 0 | 👍 0
- **Summary:** When a scheduled cron reminder fires while an assistant reply is still displayed (user has not yet responded), the previous reply is removed from the visible transcript. The lost turn cannot be recovered — scrolling back shows it was replaced by the cron turn, and `Ctrl+O` expand does not bring it back.
- **Why it matters:** This is a data-loss bug affecting users who rely on both active conversations and scheduled reminders in the same session. It breaks transcript integrity, which is foundational to trust in the tool.
- **Community reaction:** No reactions or comments yet; likely still in early visibility.

> ⚠️ Only 1 issue was active in the last 24 hours, so the "Hot Issues" section is limited. The community may be quiet or the team may be filtering noise.

## 4. Key PR Progress

**PR #2619** — [fix(soul): cancel nested task on outer cancellation](https://github.com/MoonshotAI/kimi-cli/pull/2619)
- **Author:** koriyoshi2041 | **Created:** 2026-08-26 | **Comments:** undefined | 👍 0
- **Summary:** Adds the initial `asyncio.wait()` call into the `run_soul` lifecycle cleanup, ensuring nested soul/cancel-event tasks are properly cancelled and awaited when the outer coroutine is cancelled. Includes a regression test for cancellation while a nested soul task is still running. Fixes #2615.
- **Why it matters:** Proper task cancellation is critical for async lifecycle management. Without this fix, orphaned nested tasks can leak or hang, causing resource leaks and unpredictable behavior — especially in interactive CLI sessions where users frequently interrupt operations.
- **Status:** Open, awaiting review.

> ⚠️ Only 1 PR was active in the last 24 hours, so the "Key PR Progress" section is limited.

## 5. Feature Request Trends

Based on the current issue pool, no new feature requests dominated the last 24 hours. However, the cron-transcript bug (#2620) highlights an implicit user expectation: **scheduled reminders should be non-disruptive to ongoing conversations**. Users likely want cron events to either queue behind active replies or render as overlays without consuming transcript space.

## 6. Developer Pain Points

- **Async lifecycle cancellation:** Issue #2615 (fixed by PR #2619) and the related PR both point to recurring struggles with `asyncio` task cancellation in the `soul` subsystem. Nested coroutine cleanup remains a fragile area.
- **Cron integration transcript safety:** The #2620 bug reveals that cron firing during an active assistant reply corrupts the conversation history. This suggests the cron dispatcher and the transcript renderer share state without proper isolation — a known architectural risk.
- **Limited community engagement:** With only 1 issue and 1 PR in 24 hours and zero reactions across the board, the project may have low daily contributor visibility or the community is waiting on a release cycle.

---

*Digest generated from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) data as of 2026-08-27.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-27

## 1. Today's Highlights

The community is wrestling with a cluster of subagent infinite-loop reports that burn tokens uncontrollably, marking it the dominant topic across today's issues. On the PR front, a Bedrock SDK bump (#45520) and desktop OOM fix for multiline paste (#45497) landed, while the team continues shipping small but impactful desktop/TUI polish. No new releases were published in the last 24 hours.

## 2. Releases

None in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| #20695 | **Memory Megathread** — Centralized tracking for scattered memory/heap issues | Long-running sessions with subagents appear to leak or spike memory; the team explicitly asks for heap snapshots, not LLM-suggested fixes. | 🔥 138 comments · 105 👍 — the single most-discussed open issue by far. |
| #45442 | **Subagent infinite loop** — 364 identical `grep` calls over ~50 min, no loop protection | Highlights missing guardrails for background subagents; tokens burned with no progress. | 3 comments — fresh (opened today). |
| #43673 & #43603 & #43800 | **Agent stuck in tool-call loops** — three separate reports of identical repeated tool calls | Recurring pattern across agents/models; no effective no-progress detection exists. | 3 comments each — early reports, escalating concern. |
| #36936 | **Desktop: new tab layout unusable** — titles overflow, can't distinguish projects | The new layout breaks session naming clarity; users report reverting to v1.17 fixes it. | 16 comments · 22 👍 — strong sentiment against the change. |
| #31606 | **Switching model mid-session → SQLite `NOT NULL` on `session_message.seq`** | Corrupts the entire session after a model switch, making it unusable. | 5 comments — clear reproducible bug. |
| #44958 | **Refusal response hidden; conversation history disappears (Go)** | Runs finish silently with no output or error, breaking debugging. | 5 comments — affects Go subscription users. |
| #42657 | **TUI lag with multi-subagent sessions (97% CPU on render thread)** | Concurrency scales badly; typing lags 1–3 s across Warp, WezTerm, Windows Terminal. | 4 comments — cross-terminal repro. |
| #37314 | **Orphan sub-sessions not cleaned up on parent abort** | Sub-sessions remain in `tool-calls` state indefinitely, consuming resources. | 3 comments — overlaps with #35066 (parent notification). |
| #45525 | **Unshared/deleted sessions still publicly accessible** | `/api/share/:id/data` remains readable without auth even after unsharing — a real privacy issue. | 1 comment — security-sensitive. |
| #45521 | **CodeMode tool-discovery docs inconsistent** | README claims `search(input)` "never fails," but only bare invocation works on 1.18.21. | 2 comments — documentation vs. reality gap. |

## 4. Key PR Progress

| # | PR | Description |
|---|-----|------------|
| #45520 | **Bump `@ai-sdk/amazon-bedrock` to 4.0.165** | Fixes GPT-5.6 Bedrock reasoning variants that failed with invalid reasoning-field errors (closes #45405). |
| #45497 | **Prevent renderer OOM on multiline paste** | 1,000-line paste previously emitted 2,001 input events, exhausting desktop renderer heap. |
| #45518 | **Suppress AbortError stack traces on Ctrl+C at startup** | Cleans up noisy stack traces when location-refresh requests are aborted during shutdown (closes #45409). |
| #45510 | **Fix `-f FILE "prompt"` swallowing the positional message** | yargs greedily consumed the prompt as another file arg; now preserved correctly (closes #45501, #40304). |
| #45513 | **Summarize `agent list` output; full rules behind `--verbose`** | Reduced default output from 8,600+ lines to one line per agent (closes #45496). |
| #45522 | **Show MCP connection failures as toasts** | Failed MCP connects now surface in the error toast with server name and error detail. |
| #45508 | **Desktop: use WebSocket RPC for server requests** | Stacked on #45488; replaces HTTP-based RPC with native WebSocket transport for desktop. |
| #45515 | **Align thinking states and reasoning settings** | Replaces toggle with Figma-aligned Hidden/Compact/Full reasoning display; only shows live thinking for unfinished parts. |
| #45500 | **Advertise `/compact` command in ACP** | The command was missing from `available_commands_update` despite working; now properly surfaced. |
| #45505 | **Use Bun 1.4 for CI dep installs** | Bun 1.4 includes the patched-peer fix; resolves slow Windows dependency setup without upgrading the pinned runtime. |

## 5. Feature Request Trends

- **Subagent loop & progress protection** — Multiple issues (#45442, #43673, #43603, #43800) converge on the same gap: agents repeat identical tool calls with no detection or bail-out. The community expects built-in no-progress/loop detection at the agent level.
- **i18n for the TUI** — #37216 requests localization for the terminal interface, which still has all strings hardcoded in English despite 17+ locales in the desktop/console packages.
- **Remote control via mobile** — #45437 proposes a QR-pairing + `opencode rc` command modeled after Claude Code's mobile RC flow.
- **Adjustable font size & line height** — #27684 adds per-user typography controls to desktop and web, closing three long-standing issues.
- **CodeMode extended to built-in tools** — #43137 requests CodeMode's environment awareness apply to OpenCode's own tooling, not just user-written code.

## 6. Developer Pain Points

1. **Subagent reliability** — The most-frustrating theme. Agents enter infinite loops of identical tool calls, burning tokens for tens of minutes with no built-in guard. Parent-session abort leaves orphan sub-sessions (#37314). These are the highest-sentiment pain points this week.
2. **Memory pressure at scale** — The megathread (#20695) and TUI render-thread CPU spikes (#42657) show that concurrent subagent sessions tax the process heavily, with no clear mitigation in sight.
3. **Desktop layout regressions** — The new tab layout (#36936) broke session-title visibility; users are actively reverting to older versions.
4. **SQLite schema constraints** — Model-switching mid-session (#31606) and repair-tool-call logic (#45261) both hit `NOT NULL` / constraint failures, suggesting the session persistence layer needs tighter invariants.
5. **Documentation drift** — CodeMode discovery docs (#45521) claim reliability that the current version doesn't deliver, creating confusion for users following the README.
6. **Share/privacy leak** — Unshared sessions remain readable at `/api/share/:id/data` (#45525), a trust and security gap users are flagging urgently.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-27

## 1. Today's Highlights

The Pi team shipped a cluster of fixes targeting compaction reliability, Windows tooling bugs, and Z.AI/GLM reasoning-model edge cases. The most discussed issue remains auto-compaction failing to trigger after context exceeds the threshold, while several regression fixes landed for the v0.84.3 proxy and Windows PowerShell issues.

## 2. Releases

No releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#6879](https://github.com/earendil-works/pi/issues/6879) | Auto-compaction never triggers after context grows past 100% | Compaction only fires when the API rejects at 373k tokens, making long agentic sessions crash the context window. 24 comments, 19 👍 — the most engaged issue this cycle. | 🔥 |
| [#7553](https://github.com/earendil-works/pi/issues/7553) | Configurable thinking level/model for compaction | Compaction unconditionally reuses the session's thinking level, making summarization budget inseparable from normal turns on reasoning models. | Active discussion; linked PR #7602 addresses it. |
| [#8029](https://github.com/earendil-works/pi/issues/8029) | Very slow performance in prompt editor with large buffers | A single arrow key press on a ~7000-line buffer took 1650ms; latency scales linearly with buffer size. | Bug confirmed; performance regression flagged. |
| [#8582](https://github.com/earendil-works/pi/issues/8582) | PowerShell tool uses Windows PowerShell 5.1 in interactive mode | The built-in tool falls back to legacy `powershell.exe` on Windows even when `pwsh` (v7) is on PATH, breaking modern script compatibility. | Closed — fix merged. |
| [#8444](https://github.com/earendil-works/pi/issues/8444) | `thinkingTokenBudgetField` is ignored | The documented field does nothing; `supportsThinkingTokenBudget` works but can't be renamed and is incompatible with llama.cpp. | Closed — behavioral gap acknowledged. |
| [#8649](https://github.com/earendil-works/pi/issues/8649) | `/compact` fails on xAI/Grok with `tool_choice` error | The responses provider forwards `toolChoice: "none"` even when no tools are present, violating the OpenAI responses API contract. | Closed — fix in #8719. |
| [#8610](https://github.com/earendil-works/pi/issues/8610) | `HttpsProxyAgent is not a constructor` regression (v0.84.3) | Code-splitting in the v0.84.3 bundle broke proxy support for `google-vertex` requests. | Closed — named export fix in #8723. |
| [#7724](https://github.com/earendil-works/pi/issues/7724) | Cold restore replays overflow assistant response removed by live recovery | Reopening a session after compaction adds the failed/truncated response back into history, corrupting the transcript. | In progress. |
| [#8688](https://github.com/earendil-works/pi/issues/8688) | Windows PowerShell tool prepends stray `.` to every command | A UTF-8 BOM prefix ends with `.` glued to the first word, causing PowerShell to interpret it as member access. | Closed — fix landed. |
| [#8720](https://github.com/earendil-works/pi/issues/8720) | Whitespace-only tool results permanently brick sessions | Providers reject empty/whitespace tool content with HTTP 400; the bad message stays in history, poisoning every subsequent request. | Closed — fix in #8719. |

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#8725](https://github.com/earendil-works/pi/pull/8725) | Settle active turn before in-memory fork | Fix | Prevents `toolResult` from landing in the replacement session and `dispose()` cleaning resources under the wrong session ID. |
| [#8723](https://github.com/earendil-works/pi/pull/8723) | Expose `https-proxy-agent` named export | Fix | Closes #8610; restores proxy support for `google-vertex` after the v0.84.3 code-splitting regression. |
| [#8719](https://github.com/earendil-works/pi/pull/8719) | Treat whitespace-only tool results as empty | Fix | Closes #8649 and #8720; normalizes whitespace-only output so providers no longer reject it with HTTP 400. |
| [#8627](https://github.com/earendil-works/pi/pull/8627) | Use `ctx.cwd` for cwd-sensitive tools | Feature | Makes `read`, `write`, `edit`, `grep`, `find`, `ls` resolve paths against the active session's cwd instead of the tool-creation cwd. Closes #8679. |
| [#7602](https://github.com/earendil-works/pi/pull/7602) | Configurable summarization models | Feature | Adds configurable models and thinking levels for compaction and branch summaries. Closes #7553. |
| [#8355](https://github.com/earendil-works/pi/pull/8355) | UI prompt events for extensions | Feature | Exposes `ui_prompt_start` and `ui_prompt_end` for `ctx.ui.select()`, `confirm()`, `input()` so extensions can show "Waiting for user input" states. Closes #5329. |
| [#8690](https://github.com/earendil-works/pi/pull/8690) | Add GLM-5.3 Flash to Z.AI catalogs | Feature | Registers a durable GLM-5.3 Flash override in both Z.AI Coding Plan catalogs with 1M-token context and 131k output limits. |
| [#8708](https://github.com/earendil-works/pi/pull/8708) | Resolve fd/rg versions without GitHub API | Fix | Stops hitting `api.github.com` for binary versions, eliminating anonymous-rate-limit exhaustion on shared egress IPs. Closes #8594. |
| [#8707](https://github.com/earendil-works/pi/pull/8707) | Keep Z.AI thinking enabled for forced-thinking models | Fix | When `reasoningEffort` is undefined (thinking = off), the Z.AI branch no longer sends `thinking: { type: "disabled" }` for models like `glm-5.3` where off === null. Closes #8706. |
| [#8674](https://github.com/earendil-works/pi/pull/8674) | Render markdown soft line breaks as spaces | Fix | Fixes #8673; thinking blocks and paragraphs with single `\n` now flow as paragraphs instead of ragged one-word-per-line fragments. |

## 5. Feature Request Trends

- **Compaction customization** — Users want compaction to have its own configurable thinking level and summarization model, independent of the session's active model (#7553, #7602).
- **Windows tooling parity** — Repeated requests for the built-in PowerShell tool to use `pwsh` by default, proper npm-global CLI spawning, and correct encoding prefix handling (#8582, #8688, #8715).
- **System prompt flexibility** — A persistent ask for reliable, plugin-safe system prompt customization without losing plugin-injected content (#8391).
- **Extension lifecycle events** — Demand for `ui_prompt_start/end` and turn-termination hooks so extensions can react to session state changes (#8355, #7824).
- **Working-directory awareness** — Tools should respect the active session's `ctx.cwd` rather than the cwd at tool-creation time (#8627, #8269).

## 6. Developer Pain Points

1. **Auto-compaction reliability** — The #1 frustration: compaction doesn't trigger when context exceeds thresholds, forcing sessions to blow past the context window until the API rejects them (#6879).
2. **Windows-specific regressions** — Multiple overlapping bugs: PowerShell 5.1 fallback, stray BOM/dot prefix, `ExtensionAPI.exec` swallowing `ENOENT` for npm-global CLIs, and path-resolution issues (#8582, #8688, #8715).
3. **Proxy support breaking** — Code-splitting in v0.84.3 introduced a runtime `HttpsProxyAgent` constructor error for Google Vertex requests (#8610).
4. **Reasoning-model edge cases** — Forced-thinking models (GLM-5.3, DeepSeek V4 Pro) leak reasoning into output or fail when thinking is explicitly disabled; thinking budget fields are silently ignored (#8444, #8706, #8694).
5. **Whitespace-only tool results** — Sessions are permanently broken when a tool returns only whitespace, because providers reject the verbatim content and the bad message persists in history (#8720).
6. **TUI rendering inconsistencies** — One-word-per-line output, broken fullscreen selection around `/` and `-`, and hardcoded scroll-wheel granularity make the experience fragile across terminals (#8675, #8676, #8674, #8716).
7. **Agent-loop error handling** — Unhandled rejections in `agentLoop`/`agentLoopContinue` leave `EventStream` hanging with no cleanup (#8705, #8704).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-27

## 1. Today's Highlights

Qwen Code v0.22.2 shipped alongside a major architectural shift: the persistent Node REPL is now delivered as a standalone MCP server (#9499). On the feature side, structured on-demand memory recall (#10183) and a configurable Mem0 extension skeleton (#10149) signal a push toward richer, queryable long-term memory. The project also continues heavy investment in desktop stability, CI reliability, and TUI performance.

---

## 2. Releases

**v0.22.2** — Bug-fix release. Key stabilization: convergence of the three continuation prompts onto a single guarded contract (#9834), reducing inconsistent goal-handoff behavior.

**Qwen Code Desktop v0.2.2** — Desktop-specific update, bundled with this release.

**cua-driver-rs v0.20.1** — Prebuilt binaries shipped for macOS (codesigned + notarized universal), Linux (x86_64 + arm64), and Windows (x86_64 + arm64).

---

## 3. Hot Issues

1. **[Open] Startup banner sometimes missing top lines on first paint** (#8124) — *10 comments*
   Intermittent rendering bug where the ASCII-art banner omits its top lines. Correlates with pending provider updates, suggesting a race in `AppHeader` rendering.

2. **[Open] LM Studio 0.4.21: "failed to parse grammar" even with no MCP servers** (#10065) — *4 comments*
   Users running local models via LM Studio hit a grammar-parsing failure despite a minimal config (`tools.core: []`). Highlights a compatibility gap with certain OpenAI-compatible endpoints.

3. **[Open] Track activeWork and background Agent recovery** (#8586) — *4 comments*
   Feature request for deep daemon health reporting and ACP session recovery for background agents that outlive their foreground prompt. Signals demand for more resilient long-running workflows.

4. **[Open] Context overflow causes infinite loops reading files** (#4700) — *4 comments*
   When context fills up, the agent enters a read-loop without self-recovery, requiring manual Ctrl+C. A long-standing pain point for power users running extended sessions.

5. **[Closed] E2E CI failures — monitor tool** (#8822) — *5 comments*
   Main-branch E2E test `cli/monitor.test.ts` failed and was flagged for autofix. Part of a broader pattern of CI flakiness being auto-tracked.

6. **[Closed] E2E CI failures — multiple commits** (#8895, #9015, #9143, #9237, #9239, #9241) — *5 comments each*
   A cascade of E2E test failures across mid-August, all auto-tracked and autofix-assigned. Demonstrates the project's automated CI-issue triage pipeline.

7. **[Closed] Release failures for v0.21.12-preview.2 and v0.22.0-nightly** (#9137, #10058, #10222) — *3–4 comments*
   Nightly and preview release workflows failing on the `publish` or `quality` jobs, indicating ongoing release-pipeline instability.

8. **[Open] Command hook cancellation can leave descendant processes running** (#10099) — *2 comments*
   Hooks running through a shell can spawn nested processes that survive cancellation. A correctness and resource-leak concern for users relying on command hooks.

9. **[Closed] Harden ACP channel-liveness diagnostics** (#10182) — *3 comments*
   Follow-up work to merged PR #9976, adding non-blocking diagnostics and mutation-test coverage for ACP channel health checks.

10. **[Open] l'agent reste bloqué sur la même tâche** (#4506) — *3 comments*
    French-language report of the agent stuck in a loop describing a task without executing it. Reflects a recurring pattern of agent task-holding behavior in edge cases.

---

## 4. Key PR Progress

1. **[feat] Structured on-demand recall for memory** (#10183)
   Evolves managed auto-memory from a flat prompt into a push/pull recall protocol. The model receives a two-level ref/title tree on corpus changes and a metadata subtree on relevant turns, plus a dedicated tool for explicit recall.

2. **[feat] Configurable Mem0 extension skeleton** (#10149)
   Adds a retrieval-only `external-context-mem0` stdio Extension with canonical versioned schemas and dialect presets. PR 1 of the broader configurable provider-extension rollout (#10113).

3. **[fix] Reclaim command hook process trees** (#10100)
   Each command hook now owns a POSIX process group and is reaped with a bounded SIGTERM→SIGKILL sequence. Windows uses `taskkill.exe /F /T` asynchronously. Closes #10099.

4. **[fix] Propagate filesystem cleanup failures in `team_delete`** (#10213)
   `deleteTeamDirs()` previously swallowed `EACCES`/`EIO` errors. Now reports real failures instead of claiming success.

5. **[fix] Honor empty `tools.core` allowlists** (#10080)
   `tools.core: []` now disables all registered tools, including non-core ones. Previously treated as "unrestricted." Critical for users relying on empty allowlists as a security boundary.

6. **[perf] Reduce TUI render overhead** (#9970)
   Enables incremental terminal output in virtual-viewport mode and isolates history rendering behind a memoized state slice. Addresses community concern about TUI lag during long sessions.

7. **[feat] Opt-in interactive browser terminal for Web Shell** (#9984)
   Adds a standalone interactive terminal panel to the Web Shell, gated behind the daemon's `web_terminal` capability. Keeps frontend/backend versioning decoupled.

8. **[feat] Keep round-status comment live during long autofix rounds** (#9771)
   Introduces a detached heartbeat loop so PR status comments update in real time, rather than freezing at "🔄 working" for hours.

9. **[fix] Coordinate terminal teardown** (#7837)
   Gives interactive sessions one synchronous, idempotent teardown before async cleanup, covering `SIGINT`, `SIGTERM`, `SIGHUP`, and direct exits while preserving signal-derived exit codes.

10. **[feat] Reload project runtime after `/cd`** (#10263)
    When a session changes working directory via `/cd`, project-scoped runtime state (settings, file watching, tools, hooks, MCP servers, system instructions) is reloaded transactionally.

---

## 5. Feature Request Trends

- **Memory & recall infrastructure** — Structured on-demand recall (#10183), Mem0 extension (#10149), and background agent recovery (#8586) all point to a clear trajectory: Qwen Code is building a richer, queryable long-term memory layer with explicit push/pull semantics rather than flat prompt injection.

- **Resilient background/daemon agents** — Multiple issues (#8586, #10182) focus on deep health reporting, channel-liveness diagnostics, and recovery paths for agents that outlive their initiating session.

- **Terminal and TUI robustness** — Process-group reaping (#10100), coordinated teardown (#7837), render overhead reduction (#9970), and interactive Web Shell terminal (#9984) reflect sustained investment in making the interactive experience smoother and more reliable.

- **Security hardening around tool allowlists** — Fix #10080 and the broader theme of explicit configuration enforcement signal that users want tool-scope controls to be treated as real security boundaries.

---

## 6. Developer Pain Points

- **CI flakiness on main** — A persistent stream of E2E test failures (#8822, #8895, #9015, #9143, #9237, #9239, #9241, #9876, #9322, #9326) and release-workflow failures (#9137, #10058, #10222) create noise, even though the autofix pipeline auto-tracks them.

- **Context exhaustion leads to infinite loops** — Issues #4700 and #3447 describe agents that, when context is full, enter unrecoverable read loops until manually killed. No auto-compression is kicking in reliably.

- **Grammar-parsing failures with local backends** — Issue #10065 shows that certain OpenAI-compatible servers (LM Studio 0.4.21) trigger grammar parse errors even with a minimal tool config, blocking local-model workflows.

- **Hook process leaks** — Command hooks could leave orphaned child processes after cancellation (#10099), now addressed in #10100 but indicative of a broader concern around lifecycle management.

- **Broken `tools.core: []` semantics** — The previous behavior of ignoring an empty allowlist (#10080) was a silent correctness bug that could mislead users relying on it as a deny-all policy.

---

*Data source: [github.com/QwenLM/qwen-code](https://github.com/QwenLM/qwen-code)*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-27

## 1. Today's Highlights

The Codewhale team shipped a wave of v0.9.12 integration fixes today, most critically resolving the runtime store owner lock (#5630) that blocked multiple sessions on a single machine, and recovering several contributor PRs onto main covering context-pressure persistence, per-thread usage, and route-specific tool projection. The project also added an explicit Claude Code migration planner and rescued the OpenRouter Qwen 3.8 Flash catalog, while design discussions opened around scoping MCP secret providers and unifying tool projection before dispatch.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **#5586 — Decompose the mega files** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5586)
   The 10k+-line `lib.rs`, `config.rs`, `client.rs`, and `runtime_threads.rs` continue to cause maintenance pain. Opened by the maintainer as a cleanup lane; no comments yet, but the issue sets the architectural direction for the next refactor sprint.

2. **#5630 — Runtime store owner lock blocks multiple sessions** [CLOSED] · [#](https://github.com/Hmbown/CodeWhale/issues/5630)
   v0.9.12's unified runtime threads introduced a machine-global single-owner lock, hard-failing every subsequent Codewhale process. Fixed in PR #5638/#5634 by scoping the thread store per session (`$CODEWHALE_HOME/sessions/<id>/runtime`).

3. **#5620 — Context pressure warning is transient** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5620)
   The agent ignores its own context-pressure signal, making it a silent degradation risk. Severity: Medium. PR #5629 addressed the display-side slice; the proactive-react behavior remains open.

4. **#5533 — Control surface for supervised operation** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5533)
   Requests a per-session control socket (message / interrupt / relaunch / status) and `RuntimeBackendKind::External` for users running Codewhale under terminal multiplexers, automation harnesses, or CI. Still awaiting implementation.

5. **#5637 — Scope MCP secret providers to the owning runtime** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5637)
   Design issue: mutating process environment for MCP credentials is unsound once other threads can read it. Proposes a process-wide callback model for secret lifetime management.

6. **#5633 — Unify route-specific tool projection** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5633)
   Provider routes accept different tool-schema subsets; today those decisions live inside individual request builders, causing inconsistent wire shapes. A unified pre-dispatch projection is proposed.

7. **#5290 — Fix clickable controls on non-English routes** [CLOSED] · [#](https://github.com/Hmbown/CodeWhale/issues/5290)
   Localized web routes had broken clickable controls. Closed today with PR #5647 rescuing the pricing/legal route fix.

8. **#5627 — Add Xquik to reviewed MCP recommendations** [CLOSED] · [#](https://github.com/Hmbown/CodeWhale/issues/5627)
   `Xquik` was missing from the recommended MCP surface, forcing manual endpoint entry. Resolved; users can now discover it via `/mcp add recommended xquik`.

9. **#5642 — Read-only probes on user index lock** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5642) *(cross-ref)*
   Codewhale's read-only git probes were contributing to `.git/index.lock` contention. Fixed by applying `GIT_OPTIONAL_LOCKS=0` to the shared git reader.

10. **#5632 — One worker system; retire Keychain** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/issues/5632)
    Design shift: fleet/sub-agents now inherit the parent as a single worker; roles become labels, not a permission matrix. The Codewhale Keychain/OS-keyring product path is retired in favor of `~/...`-stored account sessions.

## 4. Key PR Progress

1. **PR #5648 — Claude Code migration planner** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5648)
   Adds a review-first `/import-claude` migration planner that inventories supported Claude sources and per-project MCP servers, translating permissions into Codewhale recommendations without silently applying them. Closes #5557.

2. **PR #5649 — Rescue OpenRouter Qwen 3.8 Flash catalog** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5649)
   Adds `qwen/qwen3.8-flash` to the offline bundled catalog with its 1M-token context window, 131K output ceiling, and text+image+video input support. Supersedes #5631 with CI-clean metadata.

3. **PR #5645 — Lifecycle outbox and exec agent extraction** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5645)
   Recovers M-Maciej's lifecycle outbox work: opt-in JSONL and webhook outboxes for session, turn, stall, and subagent events. Advances #5586 and closes #5531.

4. **PR #5638 / #5634 — Scope thread store per session** [CLOSED] · [#](https://github.com/Hmbown/CodeWhale/pulls/5638) · [#](https://github.com/Hmbown/CodeWhale/pulls/5634)
   Resolves #5630: interactive runtime thread stores now default to `$CODEWHALE_HOME/sessions/<id>/runtime`, allowing multiple Codewhale processes on one machine. `CODEWHALE_RUNTIME_DIR` still permits a shared root when intended.

5. **PR #5646 — Rescue route-specific tool projection** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5646)
   Recovers Lfanxing's Moonshot tool-projection fix onto main, preserving contributor authorship. Keeps compatible tools available and degrades gracefully; #5633 remains open for the general design.

6. **PR #5629 — Persist context pressure warnings** [CLOSED] · [#](https://github.com/Hmbown/CodeWhale/pulls/5629)
   Promotes context-pressure warnings (warning/high/critical) to persistent UI status instead of letting them scroll away in turn metadata. Addresses the display-only slice of #5620.

7. **PR #5641 — Per-thread usage with CNY coverage** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5641)
   Rescues contributor PR #5626 (by Ben Gao): adds `GET /v1/threads/{id}/usage` using the provider-aware usage ledger, persisting parent and routed-child session cost without double-counting.

8. **PR #5644 — Shelter ConfigToml parses on 16 MiB stack** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5644)
   Prevents a reproducible debug-build stack overflow in the guided provider-setup/config-save path by parsing the large `ConfigToml` shape on a dedicated 16 MiB stack.

9. **PR #5643 — Recover MCP login and welcome motion** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5643)
   Brings verified 0.9.12 TUI recovery work to main: replaces internal composer terminology with localized send/queue actions, points failed Streamable HTTP OAuth sessions to `/mcp login <name>`, and restores the welcome-ocean animation.

10. **PR #5635 — Embed tsnet for `codewhale web --tailscale`** [OPEN] · [#](https://github.com/Hmbown/CodeWhale/pulls/5635)
    Adds opt-in Tailscale-backed web serving. Default `codewhale web` stays loopback-only; `--tailscale` without `--web` is rejected at the CLI level.

## 5. Feature Request Trends

- **Multi-session / supervised operation** — Issues #5533 and #5637, plus PRs #5645 and #5632, show strong momentum toward supporting external supervision (multiplexer wrappers, CI harnesses) with per-session control sockets, outbox event streams, and scoped secrets.
- **Provider compatibility & tool projection** — Issues #5633 and PRs #5646/#5636/#5631/#5649 reveal an ongoing effort to make the TUI resilient across heterogeneous provider tool schemas (Moonshot, OpenRouter, Qwen) without failing entire requests.
- **Migration tooling** — PR #5648 introduces a migration planner for Claude Code users, signaling a trend toward onboarding support from competing terminal AI tools.
- **Transparency in pricing/web** — PRs #5647/#5639 make the web pricing and legal pages honest and localized, responding to community feedback about opaque or broken non-English routes (#5290).

## 6. Developer Pain Points

- **Mega-files blocking maintenance** — Issue #5586 is the most prominent structural complaint: four files exceeding 10K lines each are slowing development and review cycles.
- **Runtime lock contention** — Issue #5630 (now fixed) caused real friction for users running multiple Codewhale sessions; the underlying tension between global locks and multi-session workflows remains a concern.
- **Context-pressure signal ignored** — Issue #5620 highlights a UX/agent-gap frustration: the system warns about context pressure but the agent doesn't proactively act, making the signal feel decorative.
- **Git index lock contention** — Read-only probes competing with user tooling for `.git/index.lock` was a recurring friction point, now addressed in PR #5642.
- **MCP secret scoping** — Issue #5637 surfaces a design-level pain: process-wide environment mutation for credentials doesn't compose with multi-threaded or multi-session architectures.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*