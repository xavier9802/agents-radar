# AI CLI Tools Community Digest 2026-08-17

> Generated: 2026-08-17 01:42 UTC | Tools covered: 10

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
**Date: 2026-08-17**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem in August 2026 is characterized by intense convergence on agent autonomy, session reliability, and platform-specific stability. The dominant pattern across all active projects is a shift from single-session assistants toward multi-agent runtime architectures, with communities urgently requesting better session resumption, context management, and observability. Windows and terminal-multiplexer compatibility has emerged as a cross-cutting fragility vector, while billing accuracy and MCP ecosystem maturity are maturing into first-class concerns.

---

## 2. Activity Comparison

| Tool | Open Issues (Active) | PRs Updated (24h) | Release (24h) | Release Type |
|------|---------------------|-------------------|---------------|--------------|
| **Claude Code** | ~10 hot issues | 3 | None | — |
| **OpenAI Codex** | ~10 hot issues | 11 | None | — |
| **Gemini CLI** | ~10 hot issues | 13 (incl. 6 Dependabot sweeps) | v0.56.0-nightly | Nightly build fix |
| **GitHub Copilot CLI** | ~10 hot issues | 1 (stale) | None | — |
| **Kimi Code CLI** | 4 hot issues | 3 | None | — |
| **OpenCode** | ~10 hot issues | 11 | None | — |
| **Pi** | ~10 hot issues | 10 | None | — |
| **Qwen Code** | 10 hot issues | 10 | v0.21.11-nightly | Feature + hardening |
| **DeepSeek TUI / CodeWhale** | ~10 hot issues | 12 | v0.9.8 | Major honesty pass + schema slim |
| **Grok Build** | 0 | 0 | None | Inactive |

*Note: "Open Issues (Active)" reflects the number of issues highlighted in each digest's "Hot Issues" section; actual open issue counts on the repos are substantially higher.*

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Multi-account / session portability** | Claude Code, OpenAI Codex, Gemini CLI, Qwen Code | Profile switching without re-auth, scoped sessions per workspace, remote/mobile handoff |
| **Agent autonomy & self-management** | Claude Code, OpenAI Codex, Gemini CLI, Pi | Self-triggered compaction, subagent observability, configurable auto-compaction thresholds |
| **Terminal / multiplexer reliability** | Claude Code, Qwen Code, DeepSeek TUI | tmux garbled renders, Kitty/Alacritty protocol detection, wide-terminal prose wrapping |
| **MCP ecosystem maturity** | Claude Code, OpenAI Codex, GitHub Copilot CLI | draft-07 schema support, OAuth stability, concurrent-refresh safety, process leak prevention |
| **Context window efficiency** | Claude Code, Pi, DeepSeek TUI, OpenAI Codex | Context bloat from MCP/tool results, accurate token billing (cache-aware), compaction visibility |
| **Session resumption & recovery** | GitHub Copilot CLI, OpenAI Codex, OpenCode, Pi | Stale connection IDs, silent archival, crash-on-resume, memory-pressure watchdog loops |
| **Subagent reliability** | Gemini CLI, OpenAI Codex, Qwen Code, DeepSeek TUI | Hangs, false success reports, task dispatch gaps, permission leaks, schema bloat |
| **Headless / CI integration** | Gemini CLI, OpenCode, Pi | `--list-models`, `--prompt` auth hardening, non-interactive parity, zsh completions |
| **Plugin / extension lifecycle** | GitHub Copilot CLI, Pi, OpenCode | Dependency resolution, vetoes via `agent_end`, lifecycle hook consistency |
| **Billing & quota accuracy** | OpenAI Codex, OpenCode, Pi, DeepSeek TUI | Broken rate-limit tracking, false "FreeUsageLimitError", cache-token inflation, unverifiable pricing |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | Qwen Code | OpenCode | Pi | DeepSeek TUI / CodeWhale | Kimi Code CLI |
|-----------|------------|-------------|-----------|-------------------|-----------|----------|-----|-------------------------|---------------|
| **Primary focus** | Desktop + TUI agent | Desktop app + VS Code ext | CLI-first, evals-heavy | Developer workflow integration | Multi-agent runtime + review | Desktop + TUI + web UI | TUI with extension system | Minimal TUI + sandboxing | Lightweight CLI |
| **Target user** | General developers | Broad developer base | Evaluation-driven devs | GitHub-centric teams | Multi-agent power users | Cross-platform desktop users | Model-catalog flexibility | Long-context / self-hosted | Emerging-market devs |
| **Technical approach** | MCP-native, agent profiles | App-server Responses API | TypeScript, composite evals | GitHub-native auth/OAuth | Team-based agent orchestration | Provider-agnostic (Zen/Go) | Catalog-driven, RPC extensions | Honesty-first transparency | Simple session model |
| **Key differentiator** | Agent profiles + plugin system | `codex doctor` diagnostics, TUI compacting | `--list-models`, Dependabot velocity | Slack integration, plugin ecosystem | `/review` pipeline, autofix gate | Desktop app + Code Mode renderer | Model-catalog accuracy, xAI routing | Wide-terminal + bwrap sandbox | `--starting-prompt` flag |
| **Open-source posture** | Fully open | Fully open | Fully open (nightlies) | Fully open | Fully open | Fully open | Fully open | Fully open (npm transition) | Fully open |

---

## 5. Community Momentum & Maturity

**High Momentum — Rapid Iteration:**
- **OpenAI Codex** — 11 PRs closed in 24h, aggressive TUI and diagnostics hardening. Windows stability remains a drag but the team is clearly moving fast on app-server reliability.
- **DeepSeek TUI / CodeWhale** — v0.9.8 represents a significant philosophical shift (honest numeric surfaces, schema slimming). The npm package rename to `codewhale` signals organizational maturity.
- **Qwen Code** — Nightly releases with substantive autofix and multi-agent PRs. The `/review` pipeline is maturing into a production-grade feature.

**Steady Evolution — Established Baselines:**
- **Claude Code** — Lower PR velocity but high-impact fixes (glob-security, YAML parsing). Community engagement is deep on fewer issues (730 👍 on multi-account).
- **Pi** — 10 PRs with strong extension-lifecycle and catalog-reliability work. The `getStats` token billing fix addresses a systemic gap.
- **OpenCode** — Heavy TUI/Desktop reliability focus; V2 docs reorganization signals product maturation.

**Emerging / Smaller Community:**
- **Kimi Code CLI** — Only 4 hot issues and 3 PRs; functional but limited community traction. Session and cron management gaps suggest an earlier product stage.
- **GitHub Copilot CLI** — Active issue surface (OAuth regressions, session bugs) but minimal PR velocity in this window; likely absorbing changes internally.
- **Gemini CLI** — High Dependabot activity (73 updates) but core feature PRs are modest; reliability concerns (subagent hangs) indicate growing pains.

**Inactive:**
- **Grok Build** — Zero activity; not a competitive factor in this window.

---

## 6. Trend Signals

| Signal | Evidence | Developer Implication |
|--------|----------|----------------------|
| **Session durability is table stakes** | Stale IDs (Copilot), silent archival (Copilot, OpenCode), crash-on-resume (Pi, Qwen), compaction 404s (Codex) | Evaluate tools on resume/recovery behavior, not just first-run UX. Multi-session workflows expose the weakest implementations. |
| **Subagent architecture is fragile across all tools** | Gemini (hangs, false success), Qwen (message delivery gaps, prompt mismatches), DeepSeek (schema bloat, self-BLOCKED), Codex (quota drain) | Subagent features are promising but not yet production-reliable. Plan for manual intervention and observability gaps. |
| **Terminal environment compatibility is a universal gap** | Claude (tmux, Kitty), Qwen (tmux flicker), DeepSeek (wide-terminal cap) | If your workflow uses tmux, SSH, or wide displays, test before adopting. This is the #1 cross-tool pain category. |
| **MCP is maturing but OAuth is the weak point** | Copilot (RFC 8414 regression, concurrent-refresh race), Codex (14 GB Node leak), Claude (draft-07 fix) | MCP-based tooling is becoming viable but expect OAuth regressions on updates. Pin versions for production use. |
| **Token billing accuracy is finally being addressed** | Pi (cache-token 120× inflation fix), DeepSeek (unverifiable pricing fallback), Codex (quota tracking broken) | Historical billing data across all tools should be treated as approximate. Newer releases are improving but legacy data may be unreliable. |
| **Multi-agent runtimes are the next competitive frontier** | Qwen (agent-team, `/review`), Pi (extension vetoes, RPC completions), DeepSeek (Whale Teams, bwrap sandbox) | The tools investing in multi-agent orchestration (Qwen, Pi, DeepSeek) are differentiating on capability, not just model access. |
| **Headless / CI integration is accelerating** | Gemini (`--list-models`, `--prompt` auth hardening), OpenCode (V2 headless TUI bug), Pi (RPC completions) | Non-interactive workflows are no longer afterthoughts. Tools with CLI-first design are pulling ahead for CI/CD use cases. |
| **Windows is the hardest platform** | Codex (4+ input-lag/resource-leak issues), Copilot (OAuth socket errors), DeepSeek (bwrap sandbox) | If targeting Windows, prioritize tools with the most active Windows issue resolution (currently Codex and Claude Code). |

---

*Report generated from community digest data dated 2026-08-17. Source: GitHub issue/PR feeds for each listed repository.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-17**

---

## 1. Top Skills Ranking

| # | PR | Skill | Status | Discussion Highlights |
|---|-----|-------|--------|-----------------------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator** (eval fix) | 🟡 Open | Fix for `run_eval.py` reporting 0% recall across all skills — critical infrastructure bug affecting the entire skill-improvement loop. 10+ independent reproductions reported. |
| 2 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | 🟡 Open | Mechanical file verification + four-dimension reasoning quality gate. Universal pre-delivery audit skill for any project/stack. |
| 3 | [#568](https://github.com/anthropics/skills/pull/568) | **servicenow** | 🟡 Open | Broad ServiceNow platform assistant covering ITSM, ITOM, ITAM/SAM, FSM, Security, and IntegrationHub. Last updated 2026-08-12 — very active. |
| 4 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | 🟡 Open | Prevents orphan line breaks, widow paragraphs, and numbering misalignment in AI-generated documents. Targets a universal pain point. |
| 5 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** | 🟡 Open | Two meta-skills evaluating skill quality across 5 dimensions (structure, examples, security, etc.) and security posture. |
| 6 | [#210](https://github.com/anthropics/skills/pull/210) | **frontend-design** | 🟡 Open | Revised for clarity and actionability — ensures every instruction is actionable within a single conversation turn. |
| 7 | [#525](https://github.com/anthropics/skills/pull/525) | **pyxel** | 🟡 Open | Retro game dev skill with MCP integration (write → run_and_capture → inspect → iterate cycle). |
| 8 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | 🟡 Open | Comprehensive testing skill covering the Testing Trophy model, AAA pattern, React Testing Library, and full-stack testing guidance. |

---

## 2. Community Demand Trends

Analysis of the top community issues reveals these high-demand directions:

| Demand Area | Evidence |
|-------------|----------|
| **Skill authoring tooling** | Issue #556 (12 comments, 7 👍) — 0% trigger rate in `run_eval.py` is a blocker for skill creators. Issue #1419 (3 comments) echoes the same bug under parallel workers. |
| **Cross-org skill sharing** | Issue #228 (16 comments, 8 👍) — users want organization-level skill libraries, not manual `.skill` file distribution via Slack/Teams. |
| **Context window hygiene** | Issue #1487 — `claude-api` skill injects ~156k tokens in one call, exhausting context. Users want lightweight, on-demand skill behavior. |
| **Trust & security** | Issue #492 (43 comments, 2 👍) — community skills impersonating the `anthropic/` namespace. Demand for namespace governance and verification. |
| **Enterprise platform skills** | ServiceNow (#568), SAP-RPT-1-OSS (#181), SharePoint (#1175) — enterprise platform integration is a strong unmet need. |
| **Document format correctness** | Issues #12 (docx whitespace), #541 (DOCX tracked-change corruption), #538 (PDF case-sensitivity) — formatting bugs in core skills cause real document damage. |
| **Agent governance & reasoning quality** | Issues #412 (closed) and #1385 — demand for pre-delivery quality gates, adversarial review, and safety patterns in agent workflows. |

---

## 3. High-Potential Pending Skills

These active PRs are strong candidates for near-term merging:

- **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — `skill-creator` eval fix. **Critical** — the entire skill optimization pipeline is broken without this. Multiple sub-fixes (Windows streams, trigger detection, parallel workers) bundled together.
- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — `self-audit` skill. Novel pre-delivery quality gate with mechanical verification + reasoning audit. Builds on community demand from Issue #1385.
- **[PR #568](https://github.com/anthropics/skills/pull/568)** — `servicenow` skill. Most recently updated (Aug 12), broad enterprise coverage, fills a clear gap.
- **[PR #514](https://github.com/anthropics/skills/pull/514)** — `document-typography` skill. Solves a near-universal document quality problem with a focused, well-scoped skill.
- **[PR #1538](https://github.com/anthropics/skills/pull/1538)** — Spec compliance fix. Brings two skills back under the Agent Skills spec — likely a quick merge.
- **[PR #723](https://github.com/anthropics/skills/pull/723)** — `testing-patterns` skill. Comprehensive and well-structured; addresses the #228-style demand for reusable quality patterns.

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is **reliable skill authoring and evaluation tooling** — the `skill-creator` pipeline is broken (0% recall bug across multiple reports), and users are simultaneously asking for better quality gates, security audits, and pre-delivery verification, signaling that the skill ecosystem is maturing from casual experimentation toward production-grade workflows where tooling trustworthiness is the bottleneck.

---



# Claude Code Community Digest — 2026-08-17

## 1. Today's Highlights

No new releases landed in the past 24 hours, but community engagement remains intense: the multi-account management feature request (#18435) continues to dominate with 730 👍, while two critical regressions — a garbled TUI in tmux since v2.1.200 (#74122) and MCP servers with draft-07 schemas being rejected (#86142) — are drawing active developer attention. Three PRs addressing glob-matching security rules, YAML frontmatter parsing, and a GitHub Actions workflow are currently open for review.

## 2. Releases

_No new releases in the last 24 hours._

## 3. Hot Issues

1. **[FEATURE] Multi-account management with profile switching** — [#18435](https://github.com/anthropics/claude-code/issues/18435) · 167 comments · 730 👍
   The single highest-engagement feature request; users want to switch between multiple Claude accounts inside Claude Desktop without re-authentication. Community reaction is overwhelmingly positive — this is a top-priority ask.

2. **[BUG] MCP draft-07 outputSchema rejected client-side** — [#86142](https://github.com/anthropics/claude-code/issues/86142) · 11 comments · 5 👍 · 🔒 Closed
   MCP servers declaring `draft-07` output schemas are silently unusable. Critical for anyone using MCP-based tooling; closed suggests a fix was shipped.

3. **[BUG] 'claude-api' consuming entire context** — [#70062](https://github.com/anthropics/claude-code/issues/70062) · 11 comments · 5 👍
   The `claude-api` area is leaking into the context window, crowding out user content. Directly impacts cost and quality on Linux.

4. **[BUG] AskUserQuestion auto-submits on mouse click** — [#71547](https://github.com/anthropics/claude-code/issues/71547) · 10 comments · 21 👍
   A single click on an option submits the answer without confirmation, causing accidental selections in the TUI. High friction for interactive workflows.

5. **[BUG] TUI renders garbled inside tmux since v2.1.200** — [#74122](https://github.com/anthropics/claude-code/issues/74122) · 8 comments · 2 👍
   Clean regression: text is corrupted and only redraws on forced full repaint. Affects all tmux users who upgraded past v2.1.199.

6. **[BUG] Kitty keyboard protocol gated on terminal-name allow-list** — [#71700](https://github.com/anthropics/claude-code/issues/71700) · 8 comments · 2 👍
   Capable terminals like Alacritty are denied Kitty keyboard protocol despite supporting it via `CSI ? u`, because detection relies on terminal-name matching instead of capability probing.

7. **[BUG] `claude plugin install --scope project` overwrites `installed_plugins.json`** — [#75392](https://github.com/anthropics/claude-code/issues/75392) · 8 comments · 1 👍 · 🔒 Closed
   Plugin installs in project scope clobber other plugins instead of merging. Closed — likely fixed.

8. **[FEATURE] Agent-invokable compaction** — [#71803](https://github.com/anthropics/claude-code/issues/71803) · 6 comments · 3 👍
   Users want the agent to trigger `/compact` on itself, rather than requiring manual intervention when context fills up. Essential for long-running automated workflows.

9. **[BUG] LSP returns silently incomplete results (cold-index race)** — [#76870](https://github.com/anthropics/claude-code/issues/76870) · 6 comments · 0 👍
   First LSP query in a session can return truncated results due to a race with the initial workspace index. Two distinct causes: cold-index race and stale file state.

10. **[FEATURE] Allow manual reordering of sidebar groups** — [#72126](https://github.com/anthropics/claude-code/issues/72126) · 3 comments · 19 👍
    Sidebar group order is driven entirely by metadata; users want manual drag-and-drop reordering. Modest discussion but high satisfaction when implemented.

## 4. Key PR Progress

1. **[fix] Make `**` glob patterns match zero-depth paths** — [#87079](https://github.com/anthropics/claude-code/pull/87079)
   `**/*.ts` in security-patterns.json was silently excluding top-level files because `fnmatch` treats bare `*` as not crossing `/`. This is a security-critical fix — rules were silently not matching.

2. **[fix] Repair invalid YAML frontmatter in all agents** — [#87077](https://github.com/anthropics/claude-code/pull/87077)
   Agent description fields containing dialogue lines like `Daisy: "..."` were parsed as invalid nested mappings, causing agents to load with empty frontmatter (no name/description/model). Fixes the YAML parsing for all agent configs.

3. **[chore] Create python-package-conda.yml** — [#87125](https://github.com/anthropics/claude-code/pull/87125)
   Adds a GitHub Actions workflow for publishing Python packages via Conda. Minimal engagement so far.

## 5. Feature Request Trends

- **Account & session management** — Multi-account switching (#18435), removing entries from "Recent" folders (#72181), configurable session title language (#72004), and multi-device session access (#72130) all point to a demand for richer identity and session portability.
- **Agent autonomy** — Self-triggered compaction (#71803), configurable auto-compaction thresholds (#72062), and per-subagent observability (#72287) show users want the agent to manage its own context and be observable during execution.
- **UI/UX polish** — Sidebar group reordering (#72126), visual distinction between Chat and Cowork projects (#71787), and feedback PII scrubbing (#72156) reflect ongoing requests for a more refined desktop and TUI experience.
- **MCP & tooling maturity** — Honoring `Annotations.Audience` on tool results (#72239) and the closed draft-07 schema fix (#86142) indicate the community is pushing MCP compatibility to production-grade levels.
- **Extensibility** — Debug command for full context window content (#72035) and more frequent local routines (#72152) show advanced users want deeper introspection and scheduling control.

## 6. Developer Pain Points

- **TUI regressions in terminal multiplexers** — The tmux garbled render (#74122) and the Kitty protocol allow-list issue (#71700) represent a pattern: Claude Code's terminal integration breaks under common dev tooling (tmux, Alacritty, Kitty) after updates. Capability-based detection is needed instead of terminal-name hardcoding.
- **Context window inefficiency** — Multiple issues (#70062, #71803, #72062, #72239) converge on the same frustration: MCP tool results and the `claude-api` area bloat context, and users lack granular control over compaction timing or visibility.
- **Plugin and session state corruption** — The `installed_plugins.json` overwrite bug (#75392) and `claude resume` silently creating a new session (#72118) both erode trust in stateful operations; users expect idempotent, merge-based updates.
- **Accidental interaction in TUI** — The AskUserQuestion auto-submit on click (#71547) causes real workflow disruption, especially for users navigating with a mouse in a terminal environment where keyboard confirmation is the expected pattern.
- **LSP reliability gaps** — The cold-index race (#76870) means the first code-assist query can silently return incomplete results, with no error signal — a particularly insidious class of bug for developers relying on LSP for navigation.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-17

---

## 1. Today's Highlights

Windows performance and stability dominate the conversation, with multiple reports of system-wide input lag, mouse stutter, and resource leaks in the desktop app—collectively drawing hundreds of upvotes. On the development side, the team shipped several behind-the-scenes hardening patches covering TUI compacting, permission profile validation, and `codex doctor` diagnostics, signaling active investment in app-server reliability and developer tooling.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

### #20214 — Codex App frequently freezes/stutters on Windows 11 Pro
**[OPEN] [bug, windows-os, app, performance]** · 106 comments · 85 👍
The highest-engagement issue this cycle. Users report persistent freezes despite ample hardware (Ryzen 5 5600, 32 GB RAM). The volume of comments suggests a widespread reproducibility problem tied to the Windows code path.
https://github.com/openai/codex/issues/20214

### #38546 — Desktop app causes system-wide mouse stutter without elevation
**[OPEN] [bug, windows-os, app, performance]** · 31 comments · 13 👍
A closely related Windows input-lag report, this time specifically noting the issue occurs *without* admin elevation. The pattern suggests a shared root cause across multiple Windows performance bugs.
https://github.com/openai/codex/issues/38546

### #25319 — Scope VS Code chats to current workspace/project
**[OPEN] [enhancement, extension, session]** · 29 comments · 62 👍
A highly upvoted feature request to scope IDE extension sessions to the active workspace, preventing cross-project context leakage. Directly addresses a workflow pain point for multi-repo developers.
https://github.com/openai/codex/issues/25319

### #23200 — Support headless remote Linux hosts for Codex mobile
**[OPEN] [enhancement, iOS, remote]** · 18 comments · 48 👍
Enables mobile-to-server workflows without requiring the desktop app to stay online—a key ask for developers whose primary compute lives on always-on SSH hosts.
https://github.com/openai/codex/issues/23200

### #20864 — Desktop App lags scanning all `~/.codex/sessions` rollout files
**[OPEN] [bug, app, session, performance]** · 21 comments · 6 👍
macOS users report severe slowdown when session history grows large, caused by the app re-scanning all rollout files instead of using an index. A clear performance regression for power users.
https://github.com/openai/codex/issues/20864

### #28855 — Intermittent system input lag on Windows despite clean logs
**[OPEN] [bug, windows-os, app, performance]** · 20 comments · 20 👍
Another Windows input-lag report, this one occurring even with plugins disabled and clean logs—pointing toward a deeper OS-level integration issue in the app.
https://github.com/openai/codex/issues/28855

### #35463 — Subagents drain full weekly quota overnight; usage counting broken
**[OPEN] [bug, rate-limits, CLI, subagent]** · 11 comments · 0 👍
Critical billing reliability issue: subagents exhaust the weekly quota silently overnight, with usage counts not reflecting actual consumption. Directly impacts Pro/Enterprise users relying on accurate quota tracking.
https://github.com/openai/codex/issues/35463

### #32797 — Desktop retains five MCP/Node process batches (147 node.exe, 13.9 GiB)
**[OPEN] [bug, windows-os, mcp, app, performance]** · 7 comments · 1 👍
Severe memory leak in the Windows MCP subsystem—nearly 14 GB of orphaned Node processes. A serious resource-management bug for users running MCP-heavy workflows.
https://github.com/openai/codex/issues/32797

### #38856 — Repeated `/responses/compact` 404 causes loss of session continuity
**[CLOSED]** · 6 comments · 0 👍
Session compaction failures on the app-server return 404s, silently breaking conversation history for remote steering. Now closed; likely addressed in recent server-side changes.
https://github.com/openai/codex/issues/38856

### #38929 — Launch spikes `mds_stores` to 250–700% CPU on macOS, host becomes unusable
**[OPEN] [bug, app, computer-use, performance]** · 1 comment · 0 👍
P0-tagged macOS issue: launching the desktop app triggers a catastrophic Spotlight-indexing storm that freezes the host until the app is force-quit. Critical for Mac users.
https://github.com/openai/codex/issues/38929

---

## 4. Key PR Progress

| PR | Status | Summary |
|----|--------|---------|
| [#38921](https://github.com/openai/codex/pull/38921) | ✅ Closed | **Compact successful command activity in the TUI** — Groups consecutive successful agent/exec commands into `Ran N commands` entries, preserving full transcripts while drastically reducing TUI visual noise. |
| [#38919](https://github.com/openai/codex/pull/38919) | ✅ Closed | **Reject obsolete app-server permission profile fields** — Prevents silent ignoring of unknown fields like `permissionProfile`, fixing a backwards-compatibility gap where client permission settings could be dropped. |
| [#38918](https://github.com/openai/codex/pull/38918) | ✅ Closed | **Improve `codex doctor` network diagnostics** — Adds probe-based diagnostics for the Responses inference endpoint, classifying TLS, proxy, resolution, and timeout failures into actionable categories. |
| [#38916](https://github.com/openai/codex/pull/38916) | ✅ Closed | **Honor legacy `:project_roots` permission entries** — Ensures permission profiles using the old `:project_roots` key (pre-` :workspace_roots` rename) continue to apply filesystem restrictions correctly. |
| [#38913](https://github.com/openai/codex/pull/38913) | ✅ Closed | **Stop rendering columns after filling their area** — TUI rendering optimization that skips visiting unused `ColumnRenderable` children once the available viewport is filled. |
| [#38907](https://github.com/openai/codex/pull/38907) | ✅ Closed | **Edit queued messages with Vim history-up** — In Vim normal mode, pressing the history-up binding on an empty composer now restores the latest queued follow-up for editing instead of doing nothing. |
| [#38902](https://github.com/openai/codex/pull/38902) | ✅ Closed | **Honor per-environment shell variable policies** — Carries `ShellEnvironmentPolicy` through resolved `EnvironmentConfig`, ensuring shell commands and user tasks respect the selected turn's environment policy. |
| [#38899](https://github.com/openai/codex/pull/38899) | ✅ Closed | **Move requirements policy ownership to execpolicy** — Extracts `RequirementsExecPolicy` into its own crate, improving modularity and making the policy type available across `codex-config` consumers. |
| [#38894](https://github.com/openai/codex/pull/38894) | ✅ Closed | **Add working-directory commands to the TUI** — Introduces `/cd [path]` for changing an idle local session's working directory while preserving conversation history, with `~` as the default. |
| [#38827](https://github.com/openai/codex/pull/38827) | ✅ Closed | **Add endpoint protection checks to `codex doctor`** — Detects supported endpoint protection products on macOS and Windows and reports which Codex exclusions need verification, reducing triage friction. |

---

## 5. Feature Request Trends

- **Workspace-scoped sessions** — Multiple requests (#25319, #32519) to keep Codex conversations bounded to a specific project or workspace, and to enable bidirectional handoff between ChatGPT mobile and Codex desktop.
- **Remote/mobile extensibility** — Headless remote host support (#23200) and improved remote steering without a persistent desktop app reflect a growing demand for mobile-as-control-plane workflows.
- **TUI ergonomics** — Vim keymap sharing (#38837), queued-message editing (#38907), working-directory commands (#38894), and command compaction (#38921) show sustained investment in CLI/TUI polish.
- **Fast model/reasoning switching** — Keyboard shortcuts for reasoning effort and model selection (#26819) remain a frequent ask for power users who toggle context constantly.
- **Diagnostics & observability** — Enhanced `codex doctor` (#38918, #38827) and better permission auditing (#38916, #38919) indicate the community values tooling that surfaces configuration problems early.

---

## 6. Developer Pain Points

1. **Windows input lag and stutter** — At least four distinct issues (#20214, #38546, #28855, #32797) describe system-wide mouse/keyboard lag or resource leaks on Windows, collectively receiving 118+ upvotes. This is the single most urgent problem area.

2. **macOS launch-time CPU storms** — Issue #38929 reports the desktop app triggering a 250–700% `mds_stores` spike on launch, rendering the host unusable. A new P0 that demands immediate attention.

3. **Session history performance degradation** — Issue #20864 shows the app re-scanning all rollout files on startup instead of using an index, causing severe slowdown as session counts grow.

4. **MCP process leaks on Windows** — Issue #32797 documents up to 147 orphaned `node.exe` processes consuming ~14 GB of RAM within a single task, indicating a critical resource-management gap in the MCP layer.

5. **Broken or inconsistent rate-limit tracking** — Issues #18018, #35463, and #38900 report conflicting behaviors around weekly quotas: limits not stopping execution, subagents draining quota overnight, and reset dates shifting unexpectedly. Trust in billing visibility is eroding.

6. **Windows sandbox and permission regressions** — Issues #28248 (sandbox ACL failures after power loss) and #32315 (Base64 payload exceeding `CreateProcessW` limits) highlight fragility in the Windows sandbox setup path.

7. **Session continuity loss from server compaction** — Issue #38856 (now closed) revealed that repeated 404s from `/responses/compact` silently drop usable conversation state, a reliability concern for long-running remote sessions.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-17

---

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly was released with a build fix adding a composite flag to the CLI's tsconfig. The community continues to report subagent reliability issues as the top concern, while Dependabot pushed a massive 73-update dependency sweep including a jump from `@google/genai` 1.30.0 → 2.16.0.

---

## 2. Releases

**v0.56.0-nightly.20260817.g9a15c45fb** — [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.56.0-nightly.20260816.g2a87e7be1...v0.56.0-nightly.2)

- [PR #28813](https://github.com/google-gemini/gemini-cli/pull/28813): Fixed build/typecheck failure by adding `"composite": true` to `packages/cli/tsconfig.json` so that `evals/tsconfig.json` can properly reference it.

---

## 3. Hot Issues

| # | Title | Priority | Comments | 👍 | Why It Matters |
|---|-------|----------|----------|-----|----------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | P1 | 12 | 2 | Subagents silently claiming success after hitting turn limits masks real failures and corrupts evaluation results. |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs forever | P1 | 8 | 8 | A high-upvote bug where simple operations (e.g., folder creation) cause the generalist agent to hang indefinitely; workaround is disabling subagents. |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage bash affinity via Zero-Dependency OS Sandboxing | P2 | 8 | 1 | Proposes using native POSIX tools (`grep`, `sed`, `awk`) without extra dependencies — a fundamental UX direction for codebase exploration. |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | P1 | 7 | 0 | Tracking behavioral eval infrastructure; 76 tests already generated across 6 Gemini versions — critical for release quality. |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess impact of AST-aware file reads, search, and mapping | P2 | 7 | 1 | Would reduce wasted turns and tokens by reading precise method bounds in a single call — high-ROI improvement. |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills/sub-agents enough | P2 | 6 | 0 | Users report custom skills (e.g., gradle, git) are ignored unless explicitly prompted, undermining the subagent architecture. |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory from retrying low-signal sessions indefinitely | P2 | 5 | 0 | Auto Memory re-surfaces unprocessed sessions, creating noise; a quality-of-life fix for memory accuracy. |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduce Auto Memory logging | P2 | 4 | 0 | 🔒 Security: secrets may reach model context before redaction; also concerns skill log exposure. |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck at "Waiting input" after completion | P1 | 4 | 3 | Simple CLI commands hang showing "Awaiting user input" even though they finished — high frustration signal. |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent resilience: session takeover & lock recovery | P3 | 4 | 0 | Current fail-fast strategy breaks persistent-browser workflows; a takeover mechanism would improve reliability. |

---

## 4. Key PR Progress

| # | Title | Status | Area | Summary |
|---|-------|--------|------|---------|
| [#28858](https://github.com/google-gemini/gemini-cli/pull/28858) | Bump version to v0.56.0-nightly.20260817 | Open | — | Automated nightly release bump. |
| [#28848](https://github.com/google-gemini/gemini-cli/pull/28848) | Handle `refreshAuth` failures gracefully in non-interactive mode | Open | Security | Fixes crash with raw stack traces during `--prompt` startup when auth refresh fails; adds a clean error path with dedicated exit code. |
| [#28815](https://github.com/google-gemini/gemini-cli/pull/28815) | Preserve original termination reason during subagent recovery | Open | Agent | Fixes [#22323](https://github.com/google-gemini/gemini-cli/issues/22323): subagents that hit MAX_TURNS but call `complete_task` during grace recovery were incorrectly reporting GOAL success. |
| [#28812](https://github.com/google-gemini/gemini-cli/pull/28812) | Prevent indefinite TUI hang by adding execution timeouts | Open | Core | Fixes [#21477](https://github.com/google-gemini/gemini-cli/issues/21477): the interactive TUI could hang forever at "Initializing…" due to `execAsync` on `ps` with no timeout. |
| [#28813](https://github.com/google-gemini/gemini-cli/pull/28813) | Add composite flag to packages/cli tsconfig | ✅ Closed | Platform | Build fix enabling `evals/tsconfig.json` to reference `packages/cli`. |
| [#28820](https://github.com/google-gemini/gemini-cli/pull/28820) | Clarify privacy notice wording and selection options | Open | Extensions | Fixes [#26120](https://github.com/google-gemini/gemini-cli/issues/26120): contradictory opt-out language in the privacy notice UI. |
| [#28814](https://github.com/google-gemini/gemini-cli/pull/28814) | Fix TypeScript strict-null errors in integration tests | Open | Platform | Resolves strict-null/union type errors in `hooks-system.test.ts` and other integration test files. |
| [#28847](https://github.com/google-gemini/gemini-cli/pull/28847) | Update `/clear` command docs to include context reset | Open | Agent | Fixes [#19239](https://github.com/google-gemini/gemini-cli/issues/19239): docs now correctly state that `/clear` resets active task context, not just the terminal screen. |
| [#28844](https://github.com/google-gemini/gemini-cli/pull/28844) | Add Homebrew deprecation notice | ✅ Closed | Docs | Warns that `gemini-cli` is deprecated in `homebrew-core`; redirects users to npm for updates. |
| [#28843](https://github.com/google-gemini/gemini-cli/pull/28843) | Add `--list-models` flag (prints JSON) | ✅ Closed | CLI | Enables programmatic model discovery for orchestrators without entering the interactive REPL; follows the existing `--help` / `--version` early-exit pattern. |

**Notable Dependabot sweeps (all closed):**

- [#28849](https://github.com/google-gemini/gemini-cli/pull/28849): 73 npm dependency updates, including `simple-git` 3.28.0→3.36.0, `@modelcontextprotocol/sdk` 1.23.0→1.30.0
- [#28851](https://github.com/google-gemini/gemini-cli/pull/28851): `@google/genai` 1.30.0→2.16.0
- [#28852](https://github.com/google-gemini/gemini-cli/pull/28852): `puppeteer-core` 24.0.0→25.5.0
- [#28850](https://github.com/google-gemini/gemini-cli/pull/28850): `undici` 7.10.0→8.10.0
- [#28855](https://github.com/google-gemini/gemini-cli/pull/28855): `eslint` 9.24.0→10.8.1
- [#28856](https://github.com/google-gemini/gemini-cli/pull/28856): `@types/node` 20.11.24→26.2.0

---

## 5. Feature Request Trends

- **Smarter subagent utilization** — Users repeatedly want the agent to proactively use custom skills, sub-agents, and browser agents without explicit prompting ([#21968](https://github.com/google-gemini/gemini-cli/issues/21968), [#22232](https://github.com/google-gemini/gemini-cli/issues/22232)).
- **AST-aware codebase tools** — Multiple linked issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)) explore whether AST-aware reads, searches, and mappings would significantly reduce turns and token waste.
- **Evaluation infrastructure maturity** — Component-level evals ([#24353](https://github.com/google-gemini/gemini-cli/issues/24353)) and behavioral test generation are active workstreams to formalize release quality gates.
- **Memory system reliability** — Auto Memory bugs around low-signal retry loops ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522)), invalid patch handling ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and redaction ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)) indicate the team is investing in memory accuracy and privacy.
- **Programmatic / headless ergonomics** — The new `--list-models` flag ([#28843](https://github.com/google-gemini/gemini-cli/pull/28843)) and `--prompt` auth hardening ([#28848](https://github.com/google-gemini/gemini-cli/pull/28848)) show a trend toward better non-interactive and CI/CD integration.

---

## 6. Developer Pain Points

1. **Subagent reliability** — The highest-friction area: agents hang ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409)), falsely report success after hitting limits ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323)), run without explicit permission ([#22093](https://github.com/google-gemini/gemini-cli/issues/22093)), and ignore configured settings like `maxTurns` ([#22267](https://github.com/google-gemini/gemini-cli/issues/22267)).
2. **Shell command hangs** — Commands completing normally leave the CLI stuck at "Waiting input" ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), a recurring and highly upvoted issue.
3. **Browser agent on Wayland** — The browser subagent fails on Wayland compositors ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)), blocking a segment of Linux users.
4. **Secrets exposure in Auto Memory** — Transcript content reaches the model before redaction occurs ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)), and invalid memory patches are silently skipped without user awareness ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)).
5. **Tool count limits** — Over 128–400 registered tools trigger 400 errors from the API ([#24246](https://github.com/google-gemini/gemini-cli/issues/24246)); users want smarter scoping.
6. **Destructive behavior** — The model occasionally runs `git reset --force` or similar dangerous commands when safer alternatives exist ([#22672](https://github.com/google-gemini/gemini-cli/issues/22672)).
7. **Broken symlink agents** — Custom agent definitions via symlinks in `~/.gemini/agents/` are not recognized ([#20079](https://github.com/google-gemini/gemini-cli/issues/20079)).
8. **Homebrew deprecation** — Users installing via Homebrew are hitting a deprecated path with no updates ([#28844](https://github.com/google-gemini/gemini-cli/pull/28844)), causing confusion.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-17

## 1. Today's Highlights

A cluster of session-resumption bugs surfaced overnight, with stale connection IDs (#4505), lost agent state (#4489), and silent archival without a restore UI (#4474) all reporting today. Authentication remains the dominant pain point: MCP OAuth regressed in 1.0.80 (#4490, #4463, #4472) and Slack session creation fails when the SDK server starts without an auth token (#4503). On the feature side, the community is pushing for a plugin dependency resolution mechanism (#4487) and a way to un-archive sessions marked Done (#4502).

## 2. Releases

No new releases in the last 24 hours. The affected version across multiple open issues is **1.0.80**, which introduced at least two regressions in MCP OAuth and sub-agent model routing.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#4503](https://github.com/github/copilot-cli/issues/4503) | SDK server reports ready without auth, then Slack session creation fails generically | The SDK server advertises readiness before authentication is established, causing opaque "couldn't create a session" errors for Slack DM users. 5 comments, actively triaged. |
| [#4490](https://github.com/github/copilot-cli/issues/4490) | Atlassian MCP OAuth broken in 1.0.80 (RFC 8414 §3.3 regression) | A confirmed regression: OAuth issuer-validation became stricter per RFC 8414, breaking Atlassian MCP servers that worked in 1.0.78. Direct productivity impact for enterprise users. |
| [#4463](https://github.com/github/copilot-cli/issues/4463) | MCP OAuth intermittently fails on Windows with socket error 10013 | Windows-specific socket-permission error during OAuth flow, affecting remote HTTP MCP servers. Intermittent nature makes it hard to reproduce but high-friction when it hits. |
| [#4506](https://github.com/github/copilot-cli/issues/4506) | Memory-pressure watchdog force-compacts at 23% context, loops until OOM | The watchdog triggers compaction based on process memory rather than context usage, creating an infinite loop that wastes tokens and can crash sessions. Critical for long-running workflows. |
| [#4505](https://github.com/github/copilot-cli/issues/4505) | Resumed session retains stale connection item IDs | After resuming, every prompt fails with `400 input item ID does not belong to this connection`. Forking doesn't help either — sessions become permanently broken post-interruption. |
| [#4472](https://github.com/github/copilot-cli/issues/4472) | Concurrent tool calls during OAuth token refresh spawn competing rmcp services | Two concurrent calls to the same OAuth-protected MCP server each trigger independent token refreshes, cancelling in-flight tool calls with "transport closed." A concurrency-safety bug with real reliability impact. |
| [#4488](https://github.com/github/copilot-cli/issues/4488) | Plugin updates fail with "Access is denied" when other sessions are open | File locks held by unrelated Copilot CLI or VS Code sessions block plugin updates even when the plugin is idle. Blocks maintenance for multi-session users. |
| [#4474](https://github.com/github/copilot-cli/issues/4474) | General Chat silently archived after session resume timeout with no restore UI | Sessions that fail to resume within 60s are archived invisibly. No UI exists to view or restore archived chats — data is lost from the user's perspective. |
| [#4486](https://github.com/github/copilot-cli/issues/4486) | Edit permission requests time out for overnight sessions | Permission prompts now expire after inactivity, breaking users who leave sessions open overnight or run multiple parallel sessions. A workflow-breaking regression. |
| [#4473](https://github.com/github/copilot-cli/issues/4473) | claude-haiku-4.5 sub-agent fails with "reasoning effort medium not supported" | Internal sub-agent routing incorrectly applies `medium` reasoning effort to haiku-4.5, which doesn't support it. Causes immediate execution failures for any task routed to that model. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#3163](https://github.com/github/copilot-cli/pull/3163) | ViewSonic monitor | Open | Community-maintained hardware compatibility PR referencing issues #2591, #3561, #3559. Appears to add GitHub Actions runner configuration for ViewSonic display support. Low activity (created May 2026, last updated Aug 16). |

*No other PRs were updated in the last 24 hours.*

## 5. Feature Request Trends

- **Plugin dependency management** (#4487): The community clearly wants a formal mechanism to declare and auto-install inter/intra-marketplace plugin dependencies, moving beyond manual installation.
- **Session recovery & archival UX** (#4502, #4474, #4505): Multiple requests converge on better session lifecycle controls — un-archiving Done sessions, restoring silently-archived chats, and fixing stale-ID bugs on resume. Users want durability and recoverability.
- **Non-interactive mode parity** (#4507): Repository-level `enabledPlugins` in `.github/copilot/settings.json` works interactively but is ignored in `copilot -p` mode, suggesting a need for feature parity between interactive and headless invocation.
- **Quota API correctness** (#4504): `account.getQuota` returning the request timestamp as `resetDate` instead of the actual quota reset date indicates a need for accurate quota reporting in the JSON-RPC interface.

## 6. Developer Pain Points

**Authentication fragility dominates.** Four of the top issues (#4503, #4490, #4463, #4472) involve OAuth or token-handling bugs, many introduced or exposed in 1.0.80. MCP OAuth in particular is unstable across platforms (Windows socket errors, concurrent-refresh races, RFC compliance regressions).

**Session resumption is unreliable.** Bugs #4505, #4489, and #4474 all relate to resuming sessions: stale connection IDs, lost agent selection, and silent archival. Users who keep sessions open overnight — a common workflow — are disproportionately affected.

**File locking blocks maintenance.** Plugin update failures due to locks from other sessions (#4488) create friction for developers managing multiple Copilot instances.

**Permission timeouts disrupt async workflows.** The new timeout on edit permission requests (#4486) breaks users who review prompts asynchronously, a pattern many rely on for parallel sessions.

**Memory watchdog misconfiguration** (#4506) causes destructive compaction loops that waste context and risk OOM crashes — a reliability concern for long-running agent sessions.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-17

---

## 1. Today's Highlights

This 24-hour window saw four active issues and three PRs on the Kimi Code CLI repo. The most notable development is the closure of PR #864, which adds the `--starting-prompt` flag to launch sessions without exiting the CLI. Two critical bug fixes from Ricardo-M-L address BrokenPipeError handling in the web runner and a string shortening logic flaw that could corrupt tool-call summaries.

---

## 2. Releases

**No new releases** in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| **#2600** | Windows PowerShell 7 default drive path issue | Users launching from a non-C drive (e.g., `D:`) encounter path resolution failures — a significant onboarding blocker on Windows with custom shell configurations. | Open, 5 comments. |
| **#2605** | No user-visible management for cron tasks | Scheduled tasks created via `CronCreate` are entirely invisible in the TUI — no `/cron` command, no `/tasks` panel entry. Users must manually hunt JSON files under `~/.kimi-code/cron/`. | Open, 1 comment. |
| **#1783** | Add `/delete` command to remove sessions | No built-in way to delete sessions; users must manually navigate `~/.kimi/sessions/`. Requests a `/delete <session_id>` command for session hygiene, disk cleanup, and sensitive-data removal. | Open, 6 comments, 1 👍. |
| **#1478** | Optimize the memory layer | Users working on large projects find the current memory system inadequate — limited to a single `agent.md`, with no persistent multi-day memory or structured recall visible in docs. | Open, 4 comments. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| **#864** | `feat: --starting-prompt` flag to prompt without exit | **CLOSED** ✅ | Adds `-s` / `--starting-prompt` flag allowing users to send an initial prompt on launch without the CLI exiting afterward. Closes #887. |
| **#2324** | `fix(web): handle BrokenPipeError in SessionProcess.send_message` | Open | Guards against a race condition where the subprocess exits between `start()` and the actual `stdin.write()` + `drain()` call in the web runner. Prevents unhandled BrokenPipeError crashes. |
| **#2449** | `fix(string): strip newlines in shorten_middle before length check` | Open | Fixes a bug where `shorten_middle()` with `remove_newline=True` returns early on short input *before* collapsing newlines, causing multi-line text to leak into single-line tool-call summaries rendered by `extract_key_argument`. |

---

## 5. Feature Request Trends

Two clear directions emerge from recent issues:

- **Session & task management via slash commands** — Users want built-in CLI commands (`/delete`, `/cron`) rather than manual filesystem traversal. The absence of management surfaces for sessions and cron jobs is a recurring frustration.
- **Persistent, structured memory** — Developers working on larger codebases need a more robust memory layer beyond a single `agent.md`, ideally with daily logs, selective retention, and clear documentation.

---

## 6. Developer Pain Points

1. **Hidden or absent management UX** — Both session deletion (#1783) and cron task oversight (#2605) require manual filesystem access, with no TUI or slash-command entry points. This pattern suggests a broader gap in discoverable command surfaces.
2. **Windows path resolution fragility** — Issue #2600 highlights that Kimi Code CLI assumes a C: drive working directory, breaking workflows where users configure non-default shell roots.
3. **Memory system under-documentation and under-capability** — Issue #1478 points out that the memory feature is neither well-documented nor architecturally suited for large-scale projects, creating friction for power users.

---

*Source: [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-17

---

## 1. Today's Highlights

OpenCode's recent activity centers on desktop and TUI reliability improvements: a major docs reorganization for V2 shipped alongside a CPU-optimized spinner and code-mode execution renderer for the Desktop app. On the issue front, community frustration is mounting around `Ctrl+C` clashing with the universal copy shortcut, Zen paid-model failures, and UI state stalls on unstable networks or with slow local providers.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**[49 👍] Ctrl+C should not exit OpenCode — conflicts with universal copy shortcut** [#7957](https://github.com/anomalyco/opencode/issues/7957)
One of the most upvoted open issues. `Ctrl+C` instantly exits the app, making it unusable for developers on Windows/Linux who habitually press it to copy. The community has long called for remapping or ignoring this key in normal input mode.

**"Copied to clipboard" doesn't work in VSCode Server / Docker** [#41470](https://github.com/anomalyco/opencode/issues/41470)
Users report the clipboard confirmation message appears but no actual text is copied when running OpenCode inside VSCode Server. This is a blocking usability issue for remote-development workflows.

**All paid Zen models fail with "Upstream request failed" — free models work** [#36506](https://github.com/anomalyco/opencode/issues/36506)
Paid Zen models (`opencode/MiniMax-M3`, `opencode/deepseek-v4-flash`, etc.) consistently fail while their free counterparts and Go models work fine, pointing to a billing-tier routing or auth bug in the Zen provider layer.

**Desktop hits 5-minute Headers Timeout with slow local providers** [#26602](https://github.com/anomalyco/opencode/issues/26502)
OpenCode Desktop aborts local OpenAI-compatible requests after exactly 5 minutes, even when the provider config sets `"timeout": false` or a larger value. This blocks long-running local inference tasks.

**Zen paid balance still hits FreeUsageLimitError despite $20 credit** [#33318](https://github.com/anomalyco/opencode/issues/33318)
After topping up a $20 Zen balance, users still receive "Free usage exceeded" errors within an hour of use, suggesting the daily free-limit check runs before the paid-balance fallback.

**[15 👍] Auto-sync projects in web UI from server** [#13626](https://github.com/anomalyco/opencode/issues/13626)
Users expect projects opened in the web UI on a new device or browser to sync automatically from the server — currently they must manually re-select or re-import.

**UI stuck on "thinking" indefinitely after stream error** [#32366](https://github.com/anomalyco/opencode/issues/32366)
When a stream error occurs (`AI_APICallError`, socket closed), the Desktop UI locks on "thinking…" with no error message and no recovery other than a restart — a critical reliability gap.

**Stuck in busy forever after toolcall** [#40468](https://github.com/anomalyco/opencode/issues/40468)
After a sequence of successful tool calls, the TUI can enter a permanent busy state where `Esc` to interrupt has no effect, leaving the session unusable without a process kill.

**Session silently stops on empty LLM response (0 tokens)** [#41469](https://github.com/anomalyco/opencode/issues/41469)
When a provider returns an empty completion, OpenCode treats it as a normal completed turn and exits the session loop silently — losing context and appearing to freeze.

**Unstable internet leaves opencode in stuck state** [#40625](https://github.com/anomalyco/opencode/issues/40625)
Packet drops on unstable connections cause OpenCode to stall permanently in a "thinking" state with no recovery path, highlighting the need for better network-resilience and timeout handling.

---

## 4. Key PR Progress

| PR | Summary |
|---|---|
| [#42952](https://github.com/anomalyco/opencode/pull/42952) ✅ | **Reduce session spinner CPU usage** — replaces 25 per-dot CSS opacity animations with a single pre-rendered APNG timeline, significantly lowering CPU cost during long sessions. |
| [#42949](https://github.com/anomalyco/opencode/pull/42949) | **Render code-mode executions in Desktop** — adds a dedicated Desktop renderer showing child tool progress, input summaries, failed-call states, and Code Mode runtime errors. |
| [#42947](https://github.com/anomalyco/opencode/pull/42947) ✅ | **Reorganize V2 documentation** — restructures V2 docs with focused CLI pages for config, providers, themes, keybinds, and plugins; updates branding and replaces `terminal.copy_on_select` with `terminal.copy`. |
| [#42944](https://github.com/anomalyco/opencode/pull/42944) ✅ | **Correct background subagent status** — subagents are now classified only after the parent tool completes, with proper animated progress and stop behavior on idle child sessions. |
| [#42945](https://github.com/anomalyco/opencode/pull/42945) ✅ | **Clarify skill timeline presentation** — shows skill icon, label, separator, and resolved name in timeline tool rows with muted detail text and expanded regression coverage. |
| [#42766](https://github.com/anomalyco/opencode/pull/42766) | **Refactor: use current session messages** — consolidates the Desktop's dual message representation (V2 stream + legacy `Message`/`Part` transcript) into a single source of truth. |
| [#42049](https://github.com/anomalyco/opencode/pull/42049) ✅ | **Hide background badge on interrupted shells** — `Background` badge now renders only when a completed tool explicitly reports a detached running state; shares the background-state predicate between shell and subagent rendering. |
| [#41144](https://github.com/anomalyco/opencode/pull/41144) ✅ | **Clarify saved permission copy** — renames "Allow always" → "Always allow", explains that saved rules apply to the current project, and removes the incorrect claim that they disappear on restart. |
| [#37392](https://github.com/anomalyco/opencode/pull/37392) ✅ | **Surface refusal category on content filter** — when Anthropic returns `stop_reason: "refusal"`, OpenCode now maps it to a `content-filter` finish with a descriptive message instead of a hardcoded generic one. |
| [#37374](https://github.com/anomalyco/opencode/pull/37374) ✅ | **Stream shell progress tail** — publishes shell progress as a replacement snapshot of the latest 25 output lines with a truncation notice, keeping final shell settlement behavior unchanged. |

---

## 5. Feature Request Trends

- **Cross-platform clipboard & input parity** — Users consistently report clipboard failures in remote environments (VSCode Server, Docker) and broken keybindings (`Ctrl+C`, `Cmd+A`). A unified input abstraction layer is the recurring ask.
- **Project/session sync across clients** — Auto-syncing projects from server to web UI and pinning/favoriting sessions for quick access (#13626, #42940) indicate demand for a persistent, device-agnostic workspace state.
- **Billing & plan transparency** — Multiple issues (#36506, #33318, #42938) point to confusion and bugs around Zen balance fallback, Go plan limits, and paid vs. free model routing.
- **Headless & scriptable CLI** — The V2 TUI-loading-on-headless-commands bug (#37671) and zsh completion gaps (#42913) highlight a need for a lightweight CLI surface separate from the interactive UI.
- **Network resilience** — Stalls on packet loss (#40625), empty responses (#41469), and 5-minute timeouts (#26602) suggest users need robust reconnection, backoff, and explicit error states.

---

## 6. Developer Pain Points

| Theme | Examples |
|---|---|
| **App freezes / unresponsive UI** | Stuck "thinking" after stream errors (#32366), stuck busy after toolcall (#40468), no recovery on interrupted sessions (#41469) |
| **Keyboard shortcut conflicts** | `Ctrl+C` exits instead of copying (#7957); `Cmd+A` highlights screen instead of selecting all (#25637, closed) |
| **Billing and model routing bugs** | Paid Zen models failing while free ones work (#36506); balance not applied despite being enabled (#33318, #42938) |
| **Remote / headless environment gaps** | Clipboard broken in VSCode Server (#41470); TUI libs loaded for `--version`/`--help` in V2 (#37671); shell progress not streamed properly (#37374) |
| **Provider timeout / network handling** | Hard 5-minute timeout on local providers (#26602); silent stalls on packet loss (#40625); 500 errors swallowed without display (#38644) |
| **Missing shell / session UX** | Top-level flags not in zsh completion (#42913); no session pinning/favorites (#42940); no email update flow (#42928) |

---

*Generated from [github.com/anomalyco/opencode](https://github.com/anomalyco/opencode) data as of 2026-08-17.*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-17

## 1. Today's Highlights

The pi-mono project saw no new releases in the last 24 hours, but developer activity remains high with **46 open/closed issues** and **9 pull requests** updated. The biggest themes this cycle are **catalog reliability fixes** (Kimi cached tokens, pi.dev timeout retries, GLM-5.2 context window correction), **token billing accuracy** (cache-inclusive totals now fixed), and **TUI stability improvements** (large-diff crash, theme switch artifacts, IME input handling).

---

## 2. Releases

No releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#5023](https://github.com/earendil-works/pi/issues/5023) | Terminal scrolls to beginning without reason | Random, non-deterministic terminal behavior breaks long sessions and is hard to reproduce/debug. Closed after community discussion. | 14 comments, 2 👍 |
| [#8029](https://github.com/earendil-works/pi/issues/8029) | Very slow performance moving in prompt editor | Arrow key latency scales linearly with buffer size — 1650 ms per press with ~7000 lines. Directly impacts UX for power users. Open, in-progress. | 9 comments |
| [#6300](https://github.com/earendil-works/pi/issues/6300) | Windows input line redrawn on every keystroke | Each character appears on a new line in cmd.exe / Windows Terminal — a severe regression for Windows users. | 7 comments |
| [#7870](https://github.com/earendil-works/pi/issues/7870) | Remote catalog overrides correct contextWindow for z-ai/glm-5.2 | Built-in catalog stuck at 262k tokens instead of real 1M, causing premature compaction and unnecessary truncation. Open, in-progress. | 3 comments |
| [#8036](https://github.com/earendil-works/pi/issues/8036) | Edit tool crashes TUI on large diff rendering | A ~14.5 MB diff from HTML files crashes the interactive TUI on both initial render and session resume. Open. | 3 comments |
| [#5581](https://github.com/earendil-works/pi/issues/5581) | Custom messages bypass `before_agent_start` event | `pi.sendMessage({ triggerTurn: true })` calls `_runAgentPrompt` directly, skipping the lifecycle hook — breaks extensions relying on it. | 4 comments, 1 👍 |
| [#7994](https://github.com/earendil-works/pi/issues/7994) | openai-completions reasoning_details round-trip broken | Signed-text replay is impossible; only encrypted entries are parsed. Filed by OpenRouter after an 870-trial benchmark. Open. | 3 comments |
| [#8198](https://github.com/earendil-works/pi/issues/8198) | pi.dev provider catalog endpoint times out | `pi update --models` consistently fails with a timeout; direct curl receives no response. Indicates server-side issues on pi.dev. | 2 comments |
| [#8061](https://github.com/earendil-works/pi/issues/8061) | Context budget ignores maxTokens output reservation | Request rejected at ~78% context because output reservation isn't accounted for; auto-retry also fails for the same reason. | 2 comments, 1 👍 |
| [#8223](https://github.com/earendil-works/pi/issues/8223) | Quit leaves orphaned pi process holding in-flight requests | Agent processes persist after pi exits, hogging GPU and generating unrequested completions (up to 16 min). Closed. | 1 comment |

---

## 4. Key PR Progress

| # | PR | Description |
|---|-----|-------------|
| [#8218](https://github.com/earendil-works/pi/pull/8218) | **fix: getStats tokens.total = billable only** | Cache tokens (billed at 1/120th rate) were inflating `tokens.total` ~120×, causing compaction budgets to trigger far too early. Fixed. |
| [#8217](https://github.com/earendil-works/pi/pull/8217) | **feat: add Kiro OAuth device login** | Full Kiro provider support — device-code auth, refresh, error handling (`authorization_pending`, `slow_down`, `fatal`), and regression coverage. |
| [#8209](https://github.com/earendil-works/pi/pull/8209) | **fix: defer non-turn custom messages during streaming** | Resolves [#8166](https://github.com/earendil-works/pi/issues/8166). `sendCustomMessage({ triggerTurn: false })` while streaming now correctly defers instead of pushing to the live message array. |
| [#8119](https://github.com/earendil-works/pi/pull/8119) | **fix: track Kimi cached tokens** | Resolves [#8075](https://github.com/earendil-works/pi/issues/8075). Kimi's top-level `usage.cached_tokens` is now included in `rawUsage` and applied as cache-read input tokens. |
| [#8124](https://github.com/earendil-works/pi/pull/8124) | **feat: route xAI through Responses API, default to Grok 4.6** | xAI models now use the Responses API instead of completions; default model bumped from Grok 4.5 → Grok 4.6; pi now sends its user agent. |
| [#8204](https://github.com/earendil-works/pi/pull/8204) | **fix: retry hung pi.dev catalog refreshes** | Resolves [#8198](https://github.com/earendil-works/pi/issues/8198). Per-attempt timeouts added to catalog fetches; `pi update --models` now survives transient hangs on `/api/models/providers/*`. |
| [#8193](https://github.com/earendil-works/pi/pull/8193) | **feat: image-to-image generation via MiniMax** | Adds a `minimax-images` API module, enabling reference-image generation for both regions through the image generation endpoint. |
| [#8222](https://github.com/earendil-works/pi/issues/8222) | **feat: validate/default tool parameter schemas** | Extensions registering tools without a `parameters` schema now get proper validation or defaults instead of silently serializing `undefined`. |
| [#8214](https://github.com/earendil-works/pi/issues/8214) | **feat: RPC get_argument_completions** | Exposes slash-command argument completions via RPC, enabling external tools to provide the same completion data the TUI already has. |
| [#8213](https://github.com/earendil-works/pi/issues/8213) | **feat: returnable agent_end for extension vetoes** | Extensions can now return a veto from `agent_end` / `before_agent_settle`, allowing them to block turn settlement and redirect the agent. |

---

## 5. Feature Request Trends

- **Provider API alignment** — Repeated requests to route models through the correct API surface (e.g., xAI → Responses, Qwen/OpenCode → Anthropic Messages, GLM thinking levels). The community expects pi's built-in catalog to accurately reflect each provider's actual endpoint.
- **Extension lifecycle hooks** — Growing demand for more granular agent-events (`agent_end` veto, `before_agent_start` consistency, RPC completions) so extensions can participate in turn boundaries rather than only observing.
- **TUI interactivity** — Mouse event opt-in for components, IME/dictation live re-layout, and themed UI consistency signal strong interest in a richer, more responsive terminal experience.
- **Catalog reliability** — Automatic model catalog refreshes, correct context windows, and retry logic are becoming table stakes; users expect pi to stay in sync with provider metadata without manual intervention.

---

## 6. Developer Pain Points

| Pain Point | Frequency |
|------------|-----------|
| **Catalog mismatch** — built-in catalog provides wrong context windows, API routes, or thinking-level support for models like GLM-5.2, Qwen, and Kimi. | High |
| **TUI performance at scale** — linear-latency editor with large buffers, crash on large diffs, Windows redraw bugs. | High |
| **Token billing inaccuracy** — cache tokens inflating usage stats and triggering premature compaction. Recently fixed but indicates a systemic gap. | Medium |
| **Extension lifecycle gaps** — custom messages bypassing lifecycle hooks, no way to veto turn settlement, unbounded subagent nesting. | Medium |
| **pi.dev infrastructure instability** — catalog endpoint hangs/ timeouts, forcing manual retries and breaking automated workflows. | Medium |
| **Orphaned processes on quit** — exiting pi leaves in-flight provider requests alive, wasting GPU and incurring unexpected costs. | Medium |

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-17

## 1. Today's Highlights

Qwen Code v0.21.11-nightly shipped with a significant autofix hardening: a deny-by-default footprint gate and positional window censuses (PR #9156). Meanwhile, the multi-agent runtime exposed several interrelated bugs — message delivery gaps between team members and leaders, manual task assignment without dispatch, and prompt/contract mismatches — all filed and actively patched in parallel (PRs #9284, #9289, #9292). The DSW EAS full E2E benchmark (SWE-bench Verified + Terminal-Bench 2.0) completed a successful rerun under the scoped proxy architecture.

## 2. Releases

**v0.21.11-nightly.20260817.195128a17a** — [PR #9156](https://github.com/QwenLM/qwen-code/pull/9156)

- `feat(autofix): deny-by-default footprint gate and positional window censuses` — tightens the autofix pipeline so changes outside the declared footprint are rejected by default, and positional window checks are enforced. This closes a class of drift issues flagged across prior review rounds.

## 3. Hot Issues

1. **[P1] autofix: PAT-bearing jobs share a host with untrusted branch code — needs runner-level isolation** [#9089](https://github.com/QwenLM/qwen-code/issues/9089) · `wenshao` · P1 / security · 5 comments
   The highest-priority open issue this cycle. The autofix pipeline's persistent-pool attack surface was partially hardened in PR #8961, but a class of findings was deliberately left open because they cannot be resolved from inside a GitHub Actions step. Runner-level isolation is the only path forward.

2. **[P2] Team members cannot send ordinary messages to their leader** [#9276](https://github.com/QwenLM/qwen-code/issues/9276) · `netbrah` · P2 / multi-agent · 5 comments
   A normal completion or status message from a team member is treated as a shutdown request and rejected with "Only the team leader can request shutdowns." This blocks a core multi-agent communication path and is actively being addressed.

3. **[P2] Unsupported image MIME can abort a Responses-compatible session** [#9291](https://github.com/QwenLM/qwen-code/issues/9291) · `netbrah` · P2 / core · 3 comments
   A `.heic` image forwarded as a data URI to a Responses-compatible endpoint triggers request-validation rejection and aborts the session. A fix (PR #9295) is already open to omit unsupported image media.

4. **[P2] Interactive session crashes when opening an errored, incomplete agent-team tab** [#9290](https://github.com/QwenLM/qwen-code/issues/9290) · `netbrah` · P2 / UI · 3 comments
   Selecting an agent-team member tab that returned an error and did not reach its normal completion path causes the entire interactive session to exit. Related PR #9292 is open to contain render errors instead of terminating.

5. **[P2] Manual team task assignment persists without dispatching work** [#9282](https://github.com/QwenLM/qwen-code/issues/9282) · `netbrah` · P2 / multi-agent · 3 comments
   `task_update({status: in_progress, owner: alice})` succeeds but the idle teammate never receives the task because the auto-claim path only scans unowned `pending` tasks. A dispatch fix (PR #9289) is in progress.

6. **[P2] Agent-team prompts contradict automatic delivery and promise unavailable peer summaries** [#9283](https://github.com/QwenLM/qwen-code/issues/9283) · `netbrah` · P2 / multi-agent · 3 comments
   Read-only teammate prompts describe automatic forwarding behavior, but normal and plan-required prompts require explicit `send_message` for final results — a contract mismatch that confuses both agents and users.

7. **[P2] task_list treats blank optional filters as active filters** [#9281](https://github.com/QwenLM/qwen-code/issues/9281) · `netbrah` · P2 / tools · 3 comments
   A `task_list` call with an empty-string `owner` or `blockedBy` returns "No tasks found" even when matching tasks exist. The tool description and task-store filter disagree on whether blank values are "absent."

8. **[P2] cannot use qwen under tmux** [#8962](https://github.com/QwenLM/qwen-code/issues/8962) · `freshui` · P2 / UI · 3 comments
   The interactive UI flickers severely in tmux or remote sessions; shrinking the terminal to ~400×300 is the only workaround. The community reaction is strongly negative given how central tmux usage is for remote developers.

9. **[P3] qwen serve host writer hard-codes new-file mode 0600** [#9250](https://github.com/QwenLM/qwen-code/issues/9250) · `VorlMaldor` · P3 / daemon · 3 comments
   In `qwen serve` (ACP host) sessions, new files are always created with mode `0600`, ignoring the process umask entirely. No settings key, flag, or environment variable exists to override this, creating permission surprises in shared environments.

10. **[P2] /review: chunk retirement silently does not fire in the reverse-audit loop** [#9206](https://github.com/QwenLM/qwen-code/issues/9206) · `wenshao` · P2 / closed · 3 comments
    In a 3B reverse-audit loop, chunks that returned substantive dry receipts in both rounds 1 and 2 should have been retired from round 3 onward (alternating-round cold checks). They were not — a correctness bug in the review retirement path that was resolved in PR #9213.

## 4. Key PR Progress

1. **[PR #9295] fix(core): omit image media the model endpoint cannot safely consume** — `yiliang114` · Opens to address #9291 by filtering out unsupported MIME types (`image/heic`, `image/tiff`, etc.) before forwarding as data URIs.

2. **[PR #9292] fix(cli): contain agent-tab render errors instead of exiting the session** — `yiliang114` · Addresses #9290 by moving the agent-tab render path behind a non-fatal error boundary, so tab-level failures no longer kill the entire interactive session.

3. **[PR #9289] fix(core): dispatch manually assigned team tasks to their owner** — `yiliang114` · Closes #9282 by adding a direct dispatch path so that `task_update` with an explicit owner actually delivers work to the named teammate, not just the auto-claim scanner.

4. **[PR #9284] fix(core): align agent-team prompts and TeamCreate description with actual delivery** — `yiliang114` · Resolves #9283 by bringing the normal and plan-required prompt texts in line with the runtime's automatic final-answer forwarding behavior.

5. **[PR #9228] fix(ci): narrow serve-ab's self-hosted wipe to the A/B checkout dirs** — `qwen-code-dev-bot` · On self-hosted ECS runners, the previous wipe step deleted the entire shared workspace including the root `.git` (~900 MB). This PR scopes the wipe to only the A/B checkout directories, preventing costly full-history re-downloads.

6. **[PR #9279] feat(review): enforce the resolved severity floor at the posting boundary** — `wenshao` · When a round resolves to a Critical-only floor (explicit `--severity-floor critical` or the round-6 adaptive default), any remaining Suggestions are moved into the review body's deferral list at the CLI level rather than posted as inline comments.

7. **[PR #9267] refactor(review): build the incremental scope from the PR's diff, not a check** — `wenshao` · Replaces the containment oracle in `fetch-pr` with a narrowing step. Incremental review now derives its scope directly from the PR's `base..head` diff rather than trying to prove it after the fact, eliminating a class of false-positive scope mismatches.

8. **[PR #9262] feat(autofix): audit the approach instead of stopping on growth-budget breach** — `wenshao` · Changes escalation semantics: when a managed PR's diff stays over its growth budget for multiple rounds, the system now continues auditing the approach rather than immediately handing off to a maintainer decision with no code changes.

9. **[PR #9226] feat(review): Aone Code read path (second review-platform provider)** — `wenshao` · Adds an Aone Code read path behind the review-platform seam introduced in #9096. Remotes on `gitlab.alibaba-inc.com` or `…/codereview/<id>` URLs are auto-detected and routed to the Aone Code read subcommands.

10. **[PR #9211] fix(review): lock the PR review worktree lease against concurrent sessions** — `wenshao` · Closes the race described in #9205 where the fixed-path worktree (` .qwen/tmp/review-pr-<n>`) was deleted mid-run by another session reviewing the same PR. The lease now acts as an explicit lock checked before destructive operations.

## 5. Feature Request Trends

- **Multi-agent runtime hardening** — Four interrelated P2 issues (#9276, #9281, #9282, #9283) and their companion PRs (#9284, #9289) show sustained community investment in making the agent-team model reliable: proper message routing, correct task dispatch, consistent prompt contracts, and robust error containment.
- **Review pipeline maturity** — A wave of review-refinement PRs (#9279, #9267, #9211) and the design issue for publish-time convergence advisory (#9278) indicate the team is pushing the `/review` system from early-stage toward production-grade, with emphasis on severity floors, scope accuracy, and worktree concurrency safety.
- **Authentication expansion** — Issue #9275 requests GitHub Copilot as an auth provider, signaling demand to broaden the identity surface beyond the current options and integrate with the Copilot ecosystem.
- **Ecosystem documentation** — Issue #9294 proposes adding ClawMetry (a local observability dashboard with a Qwen Code adapter) to the README ecosystem section, reflecting growing third-party tooling around Qwen Code.

## 6. Developer Pain Points

- **Multi-agent communication bugs are production-blocking.** The cluster of P2 issues around team messaging, task dispatch, prompt contracts, and session crashes (#9276, #9281–#9283, #9290) shows that the agent-team feature, while promising, has several delivery-path gaps that directly break workflows.
- **Tmux / remote-terminal rendering is unusable for many.** Issue #8962 has drawn strong community feedback: the interactive UI flickers badly in tmux and over SSH, with no fix yet landed beyond a workaround of shrinking the terminal.
- **Autofix growth-budget escalation halts progress.** The previous behavior (stop and hand off to a maintainer on budget breach) is being replaced (#9262) because developers found the hard stop disruptive to long-running autofix campaigns.
- **CI workspace wipes are over-broad on self-hosted runners.** PR #9228 addresses a real pain point: stale-workspace cleanup was deleting shared `.git` histories, forcing full re-downloads and increasing CI latency significantly.
- **File-permission surprises in daemon mode.** The hardcoded `0600` new-file mode in `qwen serve` (#9250) conflicts with user expectations around umask and shared-workspace permissions, creating friction in team or containerized environments.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-17

## Today's Highlights

The CodeWhale project (successor to `deepseek-tui`) released **v0.9.8** with a major honesty pass across every surface that renders guessed numbers—context windows, output ceilings, and telemetry provenance are now transparently marked. Simultaneously, the team shipped wide-terminal prose wrapping fixes, a slimmed agent tool schema (33 fields → 12), and DSH Responses-dialect route support.

---

## Releases

### v0.9.8
The legacy npm package `deepseek-tui` is **deprecated**; all future releases ship as `codewhale`. The `codewhale` command, npm package, and release-asset names remain lowercase technical identifiers. Migration path from v0.8.x legacy `deepseek` / `dsh` tools is documented.

> 🔗 [GitHub Releases](https://github.com/Hmbown/CodeWhale/releases)

---

## Hot Issues

| # | Title | Comments | Why It Matters |
|---|-------|----------|----------------|
| [#5123](https://github.com/Hmbown/CodeWhale/issues/5123) | Agent spawn surface has too many knobs — builder runs read-only and self-BLOCKED | 6 | Delegates ship with `## BLOCKED — cannot execute assigned gates` when labeled `builder` but live tool contract is read-only. Core UX friction for multi-agent workflows. |
| [#2693](https://github.com/Hmbown/CodeWhale/issues/2693) | v0.9.4 HarnessPosture: model-specific context and subagent policy | 6 | DeepSeek V4 and Xiaomi MiMo v2.5 benefit from cache-heavy/prefix-stable prompts; current one-size-fits-all context is suboptimal. |
| [#5056](https://github.com/Hmbown/CodeWhale/issues/5056) | Test reliability: flaky verifier background tests | 5 | Two verifier tests (`run_verifiers_background_advertises_detached_start`, `run_verifiers_background_starts_shell_jobs_and_returns_task_ids`) still flake under full-suite parallelism. CI trust is eroding. |
| [#1917](https://github.com/Hmbown/CodeWhale/issues/1917) | Universal PreToolUse/PostToolUse hook layer for Cancel/Pause/Resume | 5 | Proposes a unifying lifecycle hook for *any* action calling a tool — would standardize rollback, pause, and resume across slash commands and agent operations. |
| [#5424](https://github.com/Hmbown/CodeWhale/issues/5424) | v0.9.7: Codewhale TUI crashing after ~1 min | 5 | Reports spontaneous exit after prompting and waiting ~1 minute. High-severity regression affecting live sessions. |
| [#5322](https://github.com/Hmbown/CodeWhale/issues/5322) | Regression: output area doesn't fill wide terminals | 5 | In v0.8 the transcript expanded to fill terminal width; v0.9 caps it. Wide displays show cramped text with dead white space. **Closed** via PR #5446. |
| [#5367](https://github.com/Hmbown/CodeWhale/issues/5367) | Configurable model-visible read/tool-result size limits | 4 | Self-hosted long-context models (e.g., DeepSeek V4) need tunable `read` tool result bounds at the HarnessProfile level. **Closed**. |
| [#1708](https://github.com/Hmbown/CodeWhale/issues/1708) | Feature: Add `tui_help` tool for on-demand command reference | 3 | DeepSeek TUI's system prompt lacks slash-command documentation; agents hallucinate mode-switching instructions. **Closed**. |
| [#4719](https://github.com/Hmbown/CodeWhale/issues/4719) | Composer: large pasted prompts get byte-corrupted before submission | 3 | Multi-line prompts arrive mangled—paths truncated, lines dropped. Downstream agents misinterpret corrupted input. **Closed**. |
| [#4660](https://github.com/Hmbown/CodeWhale/issues/4660) | Custom provider/model config (reference: Kimi Code) | 3 | Users want a Kimi Code–style flexible provider config schema. **Closed**. |

---

## Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5459](https://github.com/Hmbown/CodeWhale/pull/5459) | fix(tui): honest context-window, output-ceiling and telemetry provenance | 🟢 Open | Every numeric surface (context windows, output ceilings, telemetry default-on state) is now shown with its config key—no more unverified guesses driving real budgets. |
| [#5458](https://github.com/Hmbown/CodeWhale/pull/5458) | feat(subagent): slim agent tool schema to 12 advertised fields | 🟢 Open | Model-facing `agent` tool now advertises 12 fields (`action, prompt, type, profile, name, agent_id, message, detached, worktree, write_roots, resume_from, until`) instead of 33. Unadvertised aliases remain parse-accepted for transcripts. |
| [#5457](https://github.com/Hmbown/CodeWhale/pull/5457) | test(pty): deflake agent_focus auto-review receipt test | 🟢 Open | Targets the macOS CI flake in `agent_focus_pty::auto_review_gates_a_workers_call_and_the_receipt_shows_in_focus`. |
| [#5445](https://github.com/Hmbown/CodeWhale/pull/5445) | fix(integrations): carry Responses-dialect DSH routes via pi-ai | ✅ Closed | Fixes `codewhale integrations dsh plan` refusing the default DeepSeek route (`deepseek/deepseek-v4-flash`). DSH now carries the Responses dialect correctly. |
| [#5456](https://github.com/Hmbown/CodeWhale/pull/5456) | feat(sandbox): bwrap container essentials + configurable extra roots | 🟢 Open | Linux bwrap sandbox now mounts private `--dev /dev`, `--proc /proc`, `--tmpfs /tmp` by default, and adds `bwrap_ro_roots` config for extra bind mounts (fixes `/dev/null` EROFS and system library linking). |
| [#5450](https://github.com/Hmbown/CodeWhale/pull/5450) | fix(tui): restore session cost when live pricing is unverifiable | 🟢 Open | Session cost no longer stays `unverifiable_live_pricing` forever when the control plane returns 503 or pricing data is missing. Honest fallback path shown. |
| [#5446](https://github.com/Hmbown/CodeWhale/pull/5446) | fix(tui): prose fills full content width; add transcript.prose_measure cap | ✅ Closed | Removed the `PROSE_MAX_MEASURE = 105` cap. Wide terminals now render prose at full content width alongside full-width tool cells. |
| [#5455](https://github.com/Hmbown/CodeWhale/pull/5455) | feat(tui): Signal Cut whale — empty-state hero art + Whale Teams role mapping | 🟢 Open | Redraws the empty-state whale from the Whale Teams roster. Fixes the old mark that read as "a bar with a shape drifting past it" instead of an animal. |
| [#5454](https://github.com/Hmbown/CodeWhale/pull/5454) | feat(web/i18n): add fr/de/ca/hi/tr/it/pl dictionaries (+ar with RTL plumbing) | 🟢 Open | Brings codewhale.net to parity with the v0.9.2 TUI locale packs; full key-parity dictionaries for 7 languages. |
| [#5452](https://github.com/Hmbown/CodeWhale/pull/5452) | docs(i18n): add fr/de/zh-TW/hi/tr/it/pl/ar README translations | 🟢 Open | README translations for all languages the TUI already ships, plus Arabic with RTL plumbing. |

---

## Feature Request Trends

1. **Honest numeric surfaces** — Users are tired of guessed context windows, output ceilings, and session costs displayed without provenance. The community strongly supports the "show the config key that fixes it" philosophy (PR #5459).

2. **Wide-terminal rendering** — Persistent demand for full-width prose on ultrawide displays. The `PROSE_MAX_MEASURE = 105` cap was a regression; its removal (PR #5446) is widely applauded.

3. **Model-specific harness posture** — DeepSeek V4, Xiaomi MiMo, and other long-context models need per-provider context strategies (cache-heavy vs. prefix-stable). Issue #2693 and PR #5445 reflect this trend.

4. **Sandbox flexibility** — bwrap sandbox restrictions (`/dev/null` EROFS, system library linking) are blocking real development workflows. PR #5456 adds configurable extra roots as a compromise.

5. **i18n parity** — The community wants the web UI, README, and TUI to ship with the same locale packs. French, German, Hindi, Turkish, Italian, Polish, and Catalan are the latest additions.

---

## Developer Pain Points

| Pain Point | Frequency | Evidence |
|------------|-----------|----------|
| **Flaky CI tests** | High | Issue #5056 (5 comments), PR #5457 (deflake attempt). Two verifier background tests and the `agent_focus_pty` test fail intermittently under full-suite parallelism. |
| **Spontaneous crashes** | High | Issue #5424 — TUI exits after ~1 minute of idle prompt-wait. Severity: session data loss. |
| **Sandbox `access denied`** | Medium | Issue #5410 (closed via PR #5456). `/dev/null` writes and system library links fail under bwrap's read-only root. |
| **Wide-terminal text cramming** | Medium | Issue #5322 (closed). Prose capped at 105 cols while tool cells use full width — visually disjointed on ultrawide screens. |
| **Unverifiable pricing display** | Medium | Issue #5241 / PR #5450. Session cost shows `unverifiable_live_pricing` indefinitely when the control plane is down. |
| **Agent tool schema bloat** | Medium | Issue #5123. 33 advertised fields on the `agent` tool overwhelms model context; PR #5458 slashes to 12. |
| **PyT/byte-corrupted pastes** | Low (resolved) | Issue #4719 — large multi-line prompts mangled before reaching the model. Closed but indicates composer input path fragility. |

---

*Generated from GitHub data — github.com/Hmbown/CodeWhale*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*