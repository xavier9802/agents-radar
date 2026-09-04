# AI CLI Tools Community Digest 2026-09-04

> Generated: 2026-09-04 04:02 UTC | Tools covered: 10

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



# Cross-Tool Comparison Report — AI CLI Tools Ecosystem
**Date: 2026-09-04**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in early September 2026 is characterized by rapid maturation across nine active projects, with strong competition between proprietary (Claude Code, Codex, Copilot CLI, Gemini CLI) and open-source (OpenCode, Pi, Qwen Code, DeepSeek TUI/CodeWhale) contenders. The dominant technical direction centers on multi-agent orchestration, plugin/extensibility architectures, and cost optimization via prompt caching and per-agent model routing. Windows platform fragility and session-state reliability remain the most widespread cross-platform pain points, while enterprise authentication (MCP OAuth, ACP protocol compliance) and sandboxed execution are emerging as critical differentiators.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Releases (24h) | Release Activity |
|------|-----------|----------|----------------|-----------------|
| **Claude Code** | 9 | 5 | v2.1.260 | Patch release with `/diff` panel, prompt-cache diagnostics |
| **OpenAI Codex** | 10 | 9 | rust-v0.153.2, v0.154.0-alpha.1–3 | Patch + alpha pre-releases |
| **Gemini CLI** | 10 | 10 | v0.60.0-nightly | Nightly with RFC 9207 OAuth fix, 3.8-flash default |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.83-4, v1.0.83-5 | Two patch releases; no PRs updated |
| **Kimi Code CLI** | 7 | 1 | None | Stable; one bug fix (completion budget clamping) |
| **OpenCode** | 10 | 10 | None | High issue/PR velocity; no release this cycle |
| **Pi** | 10 | 9 | None | Active fixes; Rust rewrite PR closed after review |
| **Qwen Code** | 10 | 11 | v0.23.0 | Release with branch picker UI + security fixes |
| **DeepSeek TUI** | 3 | 8 | v0.9.12 | Fleet UX overhaul; crate decomposition ongoing |
| **Grok Build** | — | — | — | No activity |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Multi-agent / subagent orchestration** | Claude Code, OpenAI Codex, Gemini CLI, OpenCode, Pi, Qwen Code | Per-agent model routing (#38698), ephemeral subagent spawning (#41474), subagent failure transparency (#22323), isolated workspaces (#17994) |
| **Plugin / extensibility architecture** | Claude Code, OpenCode, Pi, Qwen Code, DeepSeek TUI | Function Hooks (#91870), dynamic tool namespaces (#46530), plugin manager (#47180), hooks/lifecycle events (#1313) |
| **MCP / OAuth hardening** | Gemini CLI, GitHub Copilot CLI, Kimi Code CLI | RFC 9207 issuer verification (#29117), CIMD support (#1.0.83-4), reliable token cache reuse (#4695), MCP init regressions (#4525) |
| **Prompt-cache & cost optimization** | Claude Code, OpenAI Codex, OpenCode, Pi | Cache-miss diagnostics (#/cost), cross-turn cache accumulation (#91971), GLM-5.1 cache drops (#31348), context budget accounting (#8061) |
| **Windows cross-platform parity** | Claude Code, OpenAI Codex, Gemini CLI, Qwen Code | Always-on-top toggle (#85891), Job Object cleanup (#53247), path traversal via NTFS 8.3 (#29116), IME visibility (#9666) |
| **Session durability / resume** | OpenAI Codex, GitHub Copilot CLI, Pi, DeepSeek TUI | OOM on long --resume (#4699), state corruption after updates (#31995), checkpoint path traversal (#29192) |
| **Local/offline provider support** | OpenAI Codex, Pi, Qwen Code | GPT-6-Astra on Bedrock (#42619), musl-static binaries (#9070), open local model catalogs |

---

## 4. Differentiation Analysis

| Dimension | Proprietary Leaders | Open-Source Contenders |
|-----------|-------------------|----------------------|
| **Claude Code** | Mature plugin extensibility (Function Hooks), strong diff/UX polish, per-agent routing requests | — |
| **OpenAI Codex** | Deep GPT-6-Astra integration, worktree isolation for `exec` (#42652), enterprise Bedrock support | Windows Desktop is a major pain cluster; rate-limit accounting bugs erode trust |
| **Gemini CLI** | RFC 9207 OAuth compliance, flash-model promotion (3.8), AST-aware codebase understanding EPIC | Subagent reliability is the #1 community complaint; Wayland/browser agent blocked |
| **GitHub Copilot CLI** | Tightly integrated with GitHub ecosystem, CIMD OAuth, taskbar live-hover UX | OOM crashes on resumed sessions, MCP init regressions, no PR activity this cycle |
| **OpenCode** | Plugin manager in settings, dynamic tool namespaces, background shell execution (#47187), most engaged open issue (#266 — Gemini edit tool) | Gemini edit-tool brittleness is the top unresolved issue; installation friction on WSL/Nix |
| **Pi** | Meta/Muse OAuth provider merged, system-prompt mid-session refactor draft (#8998), Rust rewrite attempted (closed) | Quadratic TUI rendering (#8822), context budget miscalculations, plugin auth fragmentation |
| **Qwen Code** | OpenTUI migration (ink→OpenTUI), security-focused (P1 shell-allow-rule bypasses), branch picker UI polish | TUI flicker/structural bugs since Aug 2026, CI slowness (2223s collect vs 1372s tests) |
| **DeepSeek TUI** | Crate decomposition architecture (#5316), ACP session protocol work, reasoning-only retry configurability (#5867) | Small issue count (3 hot) suggests niche user base; ACP session endpoints incomplete (#5863, #5864) |

---

## 5. Community Momentum & Maturity

| Tier | Tools | Assessment |
|------|-------|------------|
| **High momentum, rapid iteration** | OpenCode, Qwen Code, DeepSeek TUI | 10+ hot issues and 8–11 PRs each; active issue resolution and architectural rework |
| **Steady evolution, enterprise focus** | Claude Code, OpenAI Codex, Gemini CLI | Balanced issue/PR ratios; patch releases addressing platform-specific pain; subscription-driven reliability investment |
| **Maturing with friction points** | GitHub Copilot CLI, Pi | Copilot CLI shows stability regressions (OOM, MCP init); Pi's Rust rewrite was rejected, signaling community preference for incremental improvement |
| **Niche / emerging** | Kimi Code CLI, DeepSeek TUI | Kimi has 7 issues, 1 PR — stable but slow-moving; DeepSeek TUI has fewest hot issues (3) but concentrated effort on ACP protocol and crate decomposition |
| **Inactive** | Grok Build | No activity recorded |

**Most engaged communities** (by comment volume and reaction density): OpenCode (#266 — 39 comments, 17 👍), Claude Code (#12346 GitLab — 131 👍), and GitHub Copilot CLI (#4218 — 13 👍).

---

## 6. Trend Signals

| Signal | Implication for Developers |
|--------|---------------------------|
| **Subagent reliability is the #1 cross-tool gap** | Every major tool has unresolved subagent/hang/loop issues. Tooling that solves transparent failure reporting and graceful recovery will differentiate. |
| **Windows platform debt is systemic** | 4 of 9 tools flag Windows as a major pain area (always-on-top, Job Objects, NTFS paths, ConstrainedLanguage). Cross-platform parity is a competitive advantage. |
| **Prompt-cache accounting is immature** | Cache misses, silent drops (GLM-5.1), and cross-turn accumulation failures are widespread. Cost-optimization tooling and diagnostics are undervalued. |
| **MCP / ACP protocol is the new extensibility layer** | Gemini CLI (RFC 9207), GitHub Copilot CLI (CIMD), DeepSeek TUI (ACP session endpoints) — all moving toward standardized plugin/agent protocols. |
| **Plugin ecosystems are converging on permission-first design** | OpenCode (permission assertions, tool namespaces), Pi (plugin auth-file keys), Claude Code (Function Hooks) — security-observable plugin models are expected, not optional. |
| **Local/offline provider demand is rising** | Bedrock GPT-6-Astra (#42619), musl-static binaries (#9070), local model allowlists (#10932) — enterprises want provider choice without cloud dependency. |
| **TUI rendering performance is a hidden bottleneck** | Pi's O(n²) markdown re-render (#8822), Qwen's ink-to-OpenTUI migration, DeepSeek's crate decomposition — visual responsiveness is becoming a differentiator for long-session workflows. |
| **Session durability (resume, compaction, OOM) is fragile** | Across Claude Code, Codex, Copilot CLI, and Pi, resumed sessions crash or leak memory. Robust session state management is an underserved need. |

---

*Report generated from community digest data dated 2026-09-04. Data sources: individual GitHub repositories for each tool.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-09-04 | Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

| # | PR | Skill | Status |
|---|-----|-------|--------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator (eval fix)** | Open |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Open |
| 3 | [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** | Open |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | **ODT** | Open |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Open |
| 6 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer / skill-security-analyzer** | Open |
| 7 | [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind (multi-agent orchestration)** | Open |
| 8 | [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow platform** | Open |

**Descriptions & Highlights:**

- **#1298 — skill-creator eval fix:** Fixes `run_eval.py` silently reporting 0% recall on every skill description, which broke the entire description-optimization loop. Also patches Windows stream reading and trigger detection. Critical infra PR with 10+ independent bug reports.
- **#514 — document-typography:** Prevents orphan lines, widow paragraphs, and numbering misalignment in AI-generated documents — issues that affect every document Claude produces but users rarely request explicitly.
- **#1615 — scnet-hpc:** Skill for operating SCNet HPC clusters via profile-based SSH and Slurm workflows; covers partition/memory/module discovery, job generation, and compute-node interaction.
- **#486 — ODT:** Full OpenDocument Format skill supporting creation, template filling, reading, and ODT→HTML conversion for `.odt`, `.ods`, and `.odf` files.
- **#723 — testing-patterns:** Comprehensive testing skill covering testing philosophy (Testing Trophy), AAA unit tests, React Testing Library, edge cases, and TDD workflows.
- **#83 — skill-quality-analyzer / skill-security-analyzer:** Meta-skills that evaluate other skills across five quality dimensions and security posture, designed for the marketplace audit pipeline.
- **#1628 — Hivemind:** Delegates mechanical work to headless open-code workers on free models while Claude Code remains the sole planner/reviewer/merger — a cost-optimization strategy for high-context sessions.
- **#568 — ServiceNow:** Broad platform skill covering ITSM, ITOM, ITAM/SAM, FSM, HRSD, CSM, SecOps, CSDM, and IntegrationHub — targeting enterprise ServiceNow developers.

---

## 2. Community Demand Trends

Distilled from the most-commented Issues:

| Trend | Signal | Key Issue |
|-------|--------|-----------|
| **Security & trust boundaries** | 43 comments, 2 👍 | [#492](https://github.com/anthropics/skills/issues/492) — Community skills impersonating the `anthropic/` namespace enable trust-boundary abuse |
| **Org-wide skill sharing** | 16 comments, 8 👍 | [#228](https://github.com/anthropics/skills/issues/228) — No native sharing mechanism; users manually distribute `.skill` files |
| **Testing & code quality tooling** | Strong | [#723](https://github.com/anthropics/skills/pull/723) + [#1385](https://github.com/anthropics/skills/issues/1385) — Demand for pre-delivery verification gates and adversarial review |
| **Platform-specific enterprise skills** | Active | [#568](https://github.com/anthropics/skills/pull/568) (ServiceNow), [#1615](https://github.com/anthropics/skills/pull/1615) (HPC), [#1175](https://github.com/anthropics/skills/issues/1175) (SharePoint) |
| **Agent governance & safety** | Growing | [#412](https://github.com/anthropics/skills/issues/412) — Missing skill for policy enforcement, threat detection, and audit trails in agent systems |
| **Memory efficiency** | Niche but active | [#1329](https://github.com/anthropics/skills/issues/1329) — Compact symbolic notation for long-running agent state to reduce context overhead |
| **Context window management** | Practical pain | [#1487](https://github.com/anthropics/skills/issues/1487) — `claude-api` skill injects ~156k tokens eagerly, exhausting context in one call |

---

## 3. High-Potential Pending Skills

These PRs have active discussion and address clear community needs — strong candidates for near-term merge:

| PR | Skill | Rationale |
|----|-------|-----------|
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | Directly addresses the #1487 context-exhaustion problem with a practical multi-model orchestration pattern |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-audit** | Implements the four-dimension reasoning quality gate from [#1385](https://github.com/anthropics/skills/issues/1385); closes a visible quality-gap in the delivery pipeline |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a universal pain point (every generated document) with zero existing coverage |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Fills a major gap — no testing skill exists; high upvote signal in related discussions |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT** | Completes the document-format coverage alongside the existing PDF and DOCX skills |
| [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** | Represents demand for HPC/cluster-specific skills; first of its kind in the repo |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **quality-gate and cost-optimization skills** — tools that verify output before delivery and reduce context-window spend — alongside a pressing need for **trust-boundary enforcement** to prevent namespace impersonation of official skills.

---



# Claude Code Community Digest — 2026-09-04

## 1. Today's Highlights

Claude Code v2.1.260 shipped with a new fullscreen diff panel for tracking uncommitted changes and better prompt-cache miss diagnostics via `/cost`. Windows 11 remains the biggest friction point this week, with three top-voted open issues covering the always-on-top window behavior, orphaned Job Objects after crashes, and masked screenshots. Community momentum is also building around Function Hooks for deep plugin extensibility and per-agent model provider routing.

---

## 2. Releases

**v2.1.260** — [GitHub](https://github.com/anthropics/claude-code)
- **New `/diff` panel:** Opens fullscreen beside the conversation, streaming your uncommitted changes as Claude edits files. Toggle with `/diff`.
- **Prompt-cache diagnostics:** `/cost` and `/tokens` now surface likely causes for cache misses (tool definition changes, system prompt shifts, idle past TTL).

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#85891](https://github.com/anthropics/claude-code/issues/85891) | Claude Desktop (Windows 11) always-on-top, no toggle | 76 comments · 167 👍 | The #1 Windows UX grievance this cycle; a long-standing Windows counterpart to an older macOS issue. Users report it breaks multi-monitor workflows. |
| [#91870](https://github.com/anthropics/claude-code/issues/91870) | Function Hooks — make plugins 10x more powerful | 64 comments · 35 👍 | Proposes a deep plugin extension model using side-effect tracking and an Express/Koa-style `next` continuation. High interest from plugin developers. |
| [#53247](https://github.com/anthropics/claude-code/issues/53247) | Windows: orphaned Silo/Job Object after crash | 55 comments · 25 👍 | A hard recovery bug — only logoff or reboot clears it. Impacts reliability for Windows power users. |
| [#12346](https://github.com/anthropics/claude-code/issues/12346) | GitLab Integration (MRs, repo connection) | 52 comments · 131 👍 | One of the most-requested integrations. GitLab users are the largest missing group vs. GitHub/GitHub-like tooling. |
| [#88093](https://github.com/anthropics/claude-code/issues/88093) | Windows always-on-top (duplicate) | 17 comments · 37 👍 | Separate report reinforcing the same Windows 11 issue; signals widespread impact. |
| [#81833](https://github.com/anthropics/claude-code/issues/81833) | Auto-memory inconsistently loaded in git-worktree sessions | 12 comments · 0 👍 | Memory content is either fully injected or completely absent across worktree sessions in the same repo — a consistency bug affecting project-context workflows. |
| [#38698](https://github.com/anthropics/claude-code/issues/38698) | Per-agent model provider routing | 11 comments · 43 👍 | Users want subagents on local/Ollama models while the orchestrator stays on Anthropic. Currently session-wide config only. |
| [#91650](https://github.com/anthropics/claude-code/issues/91650) | Bash cd-compound-read guard false-positive on Windows | 9 comments · 52 👍 | `Read()` deny rules trigger prompts on absolute `cd` targets even when no actual read occurs — a permissions UX regression in 2.1.257–2.1.259. |
| [#88937](https://github.com/anthropics/claude-code/issues/88937) | Screenshots return black/masked images on Windows | 3 comments · 0 👍 | `screenshotFiltering: mask` blocks all computer-use screenshots. Active repro on Windows. |
| [#91971](https://github.com/anthropics/claude-code/issues/91971) | Prompt cache never accumulates across chained `-p --resume` calls | 2 comments · 0 👍 | System-prompt prefix caches, but per-turn content never promotes — a cost/regression bug for scripted batch workflows. |

---

## 4. Key PR Progress

| # | PR | Status | Description |
|---|----|--------|-------------|
| [#87079](https://github.com/anthropics/claude-code/pull/87079) | fix(security-guidance): `**` glob match zero-depth paths | Open | Fixes a silent non-enforcement bug: `**/*.ts` in security-patterns.json was excluding top-level files because `fnmatch` requires an explicit `/`. Security-critical fix. |
| [#89404](https://github.com/anthropics/claude-code/pull/89404) | validate-agent.sh: don't abort at first warning | Open | Fixes false-flagging in the plugin-dev validator. `set -euo pipefail` caused aborts on `((warning_count++))` when count was zero. |
| [#66416](https://github.com/anthropics/claude-code/pull/66416) | fix(plugin-dev): validator scripts abort on first finding | Open | broader fix for the same `set -e` root cause across three validator scripts (agent, hook-linter, hook-schema). |
| [#79150](https://github.com/anthropics/claude-code/pull/79150) | docs: align code-review README with current validation command | Open | Updates stale docs — the old blame/history agent and 0–100 confidence scoring are no longer implemented. |
| [#91894](https://github.com/anthropics/claude-code/pull/91894) | Update /frontend-design SKILL.md | Closed | Skill documentation update for frontend design workflows. |

---

## 5. Feature Request Trends

- **Plugin & hook extensibility** — Function Hooks (#91870) signal strong community demand for deep, composable plugin architecture beyond the current tool/skill model.
- **Multi-provider / per-agent routing** — #38698 reflects a pattern: users want cost optimization (local Ollama for subagents) without sacrificing orchestrator quality.
- **GitLab parity** — #12346 continues to be the dominant integration request; the GitLab gap is a consistent top-voted enhancement.
- **Account/identity profiles** — #91770 asks for multiple profiles under one account with separate history, memory, and config — appealing to shared-machine and multi-project workflows.
- **Cross-platform UX parity** — Repeated requests for Windows behavior parity (always-on-top toggle, screenshot masking, permissions guards) suggest platform-specific feature gaps.

---

## 6. Developer Pain Points

1. **Windows platform fragility** — The dominant theme: always-on-top windows (#85891, #88093), orphaned Job Objects (#53247), masked screenshots (#88937, #91079), and cd-guard false positives (#91650). Windows users are experiencing a cluster of regressions and missing parity features.
2. **Permissions guard overreach** — The `cd-compound-read` guard (#91650) is triggering on absolute-path changes where no read occurs, breaking common shell workflows under `auto` mode.
3. **Prompt cache inefficiency** — Chained batch runs via `-p --resume` (#91971) fail to accumulate cache, inflating token costs for scripted/automated workflows.
4. **Auto-memory inconsistency** — Worktree sessions (#81833) intermittently receive full or zero memory content, making project context unreliable in multi-worktree setups.
5. **Validation tooling brittleness** — Plugin-dev validators (#89404, #66416) crash on zero-count arithmetic under `set -e`, flagging valid agents as errors.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-04

## 1. Today's Highlights

The 0.153.2 patch release ships a corrected GPT-6-Astra Fast tier description ("2x speed" instead of "1.5x"), while the 0.154.0-alpha series continues prepping for the next release cycle. Community attention is dominated by Windows Desktop session and project-creation bugs, recurring rate-limit reset failures, and ongoing GPT-6-Astra catalog adoption across platforms.

## 2. Releases

**rust-v0.153.2** — Bug fix patch correcting the GPT-6-Astra Fast tier display text from "1.5x speed" to "2x speed, increased usage" (impact: UI-only; no behavioral change). [[#42632](https://github.com/openai/codex/pull/42632)]

**rust-v0.153.1** — Backported GPT-6-Astra hidden model catalog to the 0.153 release line, enabling API-only configuration without exposing the model in the picker. [[#42605](https://github.com/openai/codex/pull/42605)]

**rust-v0.154.0-alpha.1 / .2 / .3** — Alpha pre-releases advancing the next minor version; no detailed notes yet.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#41290](https://github.com/openai/codex/issues/41290) | Windows/WSL project creation & removal fails after switching Agent Environment | Blocks core workflow for Windows+WSL users; session state corruption persists across restarts. | 30 comments · 21 👍 |
| [#25779](https://github.com/openai/codex/issues/25779) | Desktop meta-bug: unbounded session/turn state causes freezes & context bloat | A long-standing architectural issue affecting all long-running Desktop sessions; impacts stability at scale. | 17 comments · 8 👍 |
| [#39989](https://github.com/openai/codex/issues/39989) | Windows Desktop retains deleted conversations in Recents | Data consistency bug — deleted sessions reappear after restart, confusing users. | 16 comments · 1 👍 |
| [#31601](https://github.com/openai/codex/issues/31601) | Usage limit reset failed; quota gone | Direct billing/UX impact — Pro users report quota corruption after reset attempts. | 13 comments · 5 👍 |
| [#39121](https://github.com/openai/codex/issues/39121) | Historical local projects disappear after Desktop update | Data loss risk across multiple Desktop versions; users report tasks survive but project metadata is lost. | 12 comments · 1 👍 |
| [#31995](https://github.com/openai/codex/issues/31995) | Long conversations show only recent turns after update | Rollout history is intact locally but the UI no longer surfaces it — a regression in session rendering. | 7 comments · 1 👍 |
| [#42190](https://github.com/openai/codex/issues/42190) | Desktop pet hit-testing breaks after drag/resize | UX regression specific to Windows; the pet becomes non-interactive while remaining visible. | 6 comments · 1 👍 |
| [#37928](https://github.com/openai/codex/issues/37928) | "Usage limit resets" fails to load, hiding banked resets | Pro users cannot access their reset inventory — same family as #31601, indicating a systemic rate-limit UI bug. | 4 comments · 12 👍 |
| [#41275](https://github.com/openai/codex/issues/41275) | Windows Codex stuck on "Reconnecting" after Schannel cert failure | Enterprise/network-edge users hit a hard connectivity loop with no recovery path. | 4 comments · 3 👍 |
| [#42612](https://github.com/openai/codex/issues/42612) | Custom agent `service_tier = "fast"` ignored when parent runs Standard | Regression from 0.152.1; breaks subagent tiering strategies in CLI workflows. | 2 comments · 0 👍 |

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#42668](https://github.com/openai/codex/pull/42668) | Cancel remote control enrollment on stdio shutdown | Prevents app-server from hanging after EOF by cancelling pending remote-control enrollments and releasing thread writers. |
| [#42667](https://github.com/openai/codex/pull/42667) | Tailor TUI cyber refusal notices to Daybreak eligibility | Refines refusal messaging with cached eligibility checks and model-specific explanations for unsupported configurations. |
| [#42652](https://github.com/openai/codex/pull/42652) | Add managed worktrees to `codex exec` | New experimental `--worktree` flag creates isolated Git worktrees per session, binding each checkout as the session working directory. |
| [#42650](https://github.com/openai/codex/pull/42650) | Render assistant file citations as local links | Converts `codex-file-citation` directives into clickable local-file links, preserving Unicode, Windows separators, and location suffixes. |
| [#42641](https://github.com/openai/codex/pull/42641) | Restore inline TUI after full-screen overlays | Fixes stale overlay cells and scroll position loss when exiting alternate-screen modes in the TUI. |
| [#42640](https://github.com/openai/codex/pull/42640) | Harden TUI parsing of assistant markup | Adds a shared parser for assistant directives handling quoted/unquoted attributes, embedded braces, and malformed input consistently. |
| [#42639](https://github.com/openai/codex/pull/42639) | Warn when saved model defaults are overridden | Prevents misleading success messages by detecting when higher-priority config layers override saved model/reasoning-tier values. |
| [#42632](https://github.com/openai/codex/pull/42632) | Fix GPT-6-Astra Fast tier description | Patch for 0.153.2: updates Fast tier text from "1.5x" to "2x speed, increased usage" (UI-only). |
| [#42634](https://github.com/openai/codex/pull/42634) | Add injectable attachment store to ThreadManager | New `codex-attachment-store` crate provides a storage-neutral persistence interface for attachment metadata and media-typed bytes. |
| [#42619](https://github.com/openai/codex/pull/42619) | Add GPT-6-Astra to Amazon Bedrock catalogs | Extends GPT-6-Astra availability to Bedrock Runtime with global and US cross-region variants, preserving bundled metadata. |

## 5. Feature Request Trends

- **Commit-author attribution** — Issue [#938](https://github.com/openai/codex/issues/938) (14 👍, closed) requests Aider-compatible `(codex)` author tagging and `Co-authored-by: codex ${model}` support in commit messages.
- **Ephemeral subagent spawning** — Issue [#41474](https://github.com/openai/codex/issues/41474) surfaces demand for reliable `--ephemeral` custom subagent support without global agent placement.
- **Worktree isolation for `codex exec`** — PR [#42652](https://github.com/openai/codex/pull/42652) directly responds to community need for per-session isolated working directories in automated/CI workflows.
- **Cross-platform remote exec auth** — PR [#42606](https://github.com/openai/codex/pull/42606) adds trusted-header support for remote exec WebSockets, addressing enterprise embedding scenarios.
- **Daybreak / Astra eligibility granularity** — Multiple PRs (#42667, #42605, #42607, #42619) reflect growing demand for fine-grained model-tier control and cloud-provider (Bedrock) support for GPT-6-Astra.

## 6. Developer Pain Points

1. **Windows Desktop stability regressions** — A cluster of issues (#41290, #39989, #39121, #42190, #42061, #41275, #42501) point to persistent Windows-specific bugs in session management, project persistence, pet overlay input, and Schannel connectivity. This is the single largest pain category.
2. **Rate-limit and quota accounting bugs** — Issues #31601, #37928, #37934, #35116, #42660, #42346 form a recurring pattern where usage resets fail silently or quota reconciliation is broken, eroding trust among Pro/Plus users.
3. **Session/state corruption after updates** — Issues #31995, #42027, and #38972 report that app updates can truncate conversation history, break fork ordinals, or desynchronize turn-completion signals from the underlying JSONL rollout.
4. **macOS Computer Use crashes** — Issues #41374 and #42666 describe Accessibility permission conflicts causing SIGSEGV in Qt-based tools (Qt Creator, NVIDIA Nsight Systems), limiting adoption of Computer Use on macOS.
5. **CLI subagent tiering regression** — Issue #42612 reports that `service_tier = "fast"` on child agents is silently ignored when the parent runs Standard, breaking a previously working 0.152.1 configuration.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-04

## 1. Today's Highlights

The nightly v0.60.0 release shipped with a critical fix enforcing RFC 9207 issuer identification in the MCP OAuth flow, tightening security for enterprise SSO setups. Meanwhile, user complaints about model 3.6/3.7 Flash remaining unavailable in the picker — despite a PR to promote 3.8 Flash as the new default — signal an urgent UX gap that warrants tracking. Under the hood, the team continues hardening checkpoints and path validation across Windows and POSIX, while a persistent generalist-agent hang and subagent reliability bugs dominate community discussion.

---

## 2. Releases

### v0.60.0-nightly.20260904.g87a9c71d5
- **[PR #29117](https://github.com/google-gemini/gemini-cli/pull/29117)** — `fix(core)`: Enforces RFC 9207 issuer identification in the MCP OAuth flow, closing a credential-verification gap.
- **[PR #29196](https://github.com/google-gemini/gemini-cli/pull/29196)** — Automated nightly version bump.
- **[PR #29172](https://github.com/google-gemini/gemini-cli/pull/29172)** — Registered `gemini-3.5-flash-lite`, `3.6-flash`, `3.7-flash`, and `3.8-flash` as selectable models, promoting `3.8-flash` as the default flash variant (note: per #29164, 3.6/3.7 still aren't surfacing in the picker for all users).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#29164](https://github.com/google-gemini/gemini-cli/issues/29164) | 3.6 & 3.7 Flash missing from model picker | Blocks users from accessing recently added flash models; contradicts PR #29172 | 12 👍 · 6 comments |
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery misreported as GOAL success after MAX_TURNS | Subagent silently claims success when it actually hit its turn limit, hiding failures from the user | 2 👍 · 13 comments |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs forever | Simple folder-creation tasks can stall indefinitely; workarounds require disabling sub-agents entirely | 8 👍 · 8 comments |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Post-Execution Intent Routing | Proposes leveraging the model's native bash affinity with sandboxing — could redefine how shell tools are invoked securely | 1 👍 · 9 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and codebase mapping | EPIC tracking whether AST-aware tools reduce turn count and token noise — directly impacts agent performance | 1 👍 · 7 comments |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini under-uses skills and sub-agents | Users report the model ignores custom skills unless explicitly prompted, reducing autonomy value | 0 👍 · 6 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & Auto Memory logging reduction | Auto Memory reads transcripts before redaction, leaking secrets into model context — a genuine privacy risk | 0 👍 · 5 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell execution stuck "Awaiting user input" after completion | Simple CLI commands hang with a false "awaiting input" status, blocking subsequent tool calls | 3 👍 · 4 comments |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent lock recovery | Fails-fast on locked browser profiles instead of recovering — blocks persistent-session use cases | 0 👍 · 4 comments |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Linux users on Wayland can't run the browser agent at all; a hard blocker for that ecosystem | 1 👍 · 4 comments |

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#29185](https://github.com/google-gemini/gemini-cli/pull/29185) | Deflake `run_shell_command` & `file-system-interactive` tests | `test` | Resolves flakiness in slow E2E integration tests by fixing async timing around tool-allowlist checks. |
| [#29184](https://github.com/google-gemini/gemini-cli/pull/29184) | Validate git args in Windows sandbox | `security` | Blocks silent `git diff --output=<path>` on Windows, which previously truncated files without user confirmation. |
| [#29172](https://github.com/google-gemini/gemini-cli/pull/29172) | Add `gemini-3.8-flash` as default flash model | `feat` | Registers 3.5-flash-lite through 3.8-flash as selectable models and promotes 3.8-flash as the new default. |
| [#29115](https://github.com/google-gemini/gemini-cli/pull/29115) | Strict permission & ownership checks on config paths | `security` | Enforces ACL verification on system-wide config files (Windows POSIX) before loading — prevents config poisoning. |
| [#29116](https://github.com/google-gemini/gemini-cli/pull/29116) | Mitigate NTFS 8.3 short-name path traversal | `fix` | Handles SFN paths (`git~1`, `node_m~1`, etc.) in `AllowedPathChecker`, closing a path-traversal vector on Windows. |
| [#29106](https://github.com/google-gemini/gemini-cli/pull/29106) | Flush final SSE event on EOF without trailing blank line | `fix` | Fixes silent data loss of `finishReason`/usage metadata when a stream ends non-conformantly. |
| [#29110](https://github.com/google-gemini/gemini-cli/pull/29110) | Route `read_file` through `FileSystemService` | `fix` | Aligns `read_file` with `write_file`/`replace` so ACP clients with custom FS implementations get proper I/O routing. |
| [#29195](https://github.com/google-gemini/gemini-cli/pull/29195) | Degrade non-array history instead of crashing resume | `fix` | `/chat resume` no longer throws a raw `TypeError` when the checkpoint's `history` field is malformed. |
| [#29192](https://github.com/google-gemini/gemini-cli/pull/29192) | Contain legacy raw tag paths inside checkpoints dir | `security` | Fixes `../` tag traversal in `/chat delete`, which previously allowed deletion outside the checkpoints directory. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Consent prompt on extension env changes | `security` | Extensions can no longer inject unauthorized env vars into MCP server processes without user consent; sanitizes runtime-altering variables. |

---

## 5. Feature Request Trends

- **Subagent autonomy & reliability** — The dominant theme: users want subagents to actually use skills, recover gracefully from locks/hangs, and report failures honestly rather than masking them as success. (Issues #22323, #21409, #21968, #22232)
- **Model availability & selection** — Clear demand for flash models to appear in the picker consistently and for the default to be obvious. (Issues #29164, #29172)
- **AST-aware codebase understanding** — Investigation into whether parse-tree-aware tooling can reduce turn counts and token noise, directly tied to agent performance. (Issues #22745, #22746)
- **Secure sandboxing & redaction** — Multiple requests for deterministic pre-context redaction and sandboxed execution that doesn't leak secrets into model context. (Issues #26525, #26522, #26523)
- **Linux/Wayland compatibility** — Browser agent and Wayland-specific failures remain unaddressed, signaling an underserved ecosystem. (Issue #21983)

---

## 6. Developer Pain Points

1. **Subagent failures are invisible** — Agents report `GOAL` success when they hit turn limits or hang, making debugging extremely difficult. Users must explicitly disable subagents as a workaround (#22323, #21409, #21968).
2. **Model picker inconsistency** — Models registered in code (e.g., via PR #29172) don't always appear in the interactive picker, causing confusion and support tickets (#29164).
3. **Shell execution state bugs** — Commands that complete normally leave the agent stuck in an "awaiting input" state, blocking all subsequent actions (#25166, #29197).
4. **Windows-specific path hazards** — NTFS 8.3 short names, long paths, and silent file truncation via `git diff --output` create security and reliability risks unique to Windows developers (#29184, #29116, #28926).
5. **Auto Memory privacy gaps** — Transcript content reaches the model before redaction, and low-signal sessions are retried indefinitely, wasting tokens and potentially leaking data (#26525, #26522, #26523).
6. **Wayland & browser agent** — Linux Wayland users cannot run the browser agent at all, and persistent-session locks cause hard failures instead of graceful recovery (#21983, #22232).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-04

## 1. Today's Highlights

GitHub Copilot CLI released two patch versions (v1.0.83-4 and v1.0.83-5) introducing CIMD OAuth support, Windows 11 taskbar live-hover status cards, and tighter sandbox restrictions on macOS/Linux. Community discussion is dominated by MCP initialization regressions, OAuth token cache reliability, and a memory leak crash on long `--resume` sessions.

---

## 2. Releases

**v1.0.83-5** — Windows 11 taskbar now shows live Copilot session hover cards. Sandboxed commands on macOS/Linux are further restricted from reaching host services (including 127.0.0.1 servers spawned by the command itself).

**v1.0.83-4** — Added Client ID Metadata Document (CIMD) support for MCP OAuth sign-in. The CLI now starts without prompting to restore interrupted sessions by default, and resuming large sessions returns to the input prompt faster. Sandboxed file tools now read the same developer-tool restrictions consistently.

---

## 3. Hot Issues

1. **#4525** — [MCP] Legacy `initialize` sent after successful `server/discover`, causing error -32022 against Python MCP SDK 2.0.0 dual-era runners. *(6 comments, 3 👍)*
   [GitHub](https://github.com/github/copilot-cli/issues/4525)
   > Why it matters: MCP interop breaks with widely-used SDKs after protocol negotiation succeeds. High comment count signals active investigation.

2. **#3442** — [Sessions/Enterprise] Remote sessions disabled after v1.0.51 update; users told to contact admin despite no policy change. *(6 comments, 10 👍)* **CLOSED**
   [GitHub](https://github.com/github/copilot-cli/issues/3442)
   > Why it matters: Enterprise remote-session enablement is a common org requirement; the regression after a minor version bump affected many users.

3. **#2861** — [Context-Memory] Compaction fails with empty model response on Claude Opus 4.6, even after 3 retries and manual `/compact`. *(5 comments, 4 👍)*
   [GitHub](https://github.com/github/copilot-cli/issues/2861)
   > Why it matters: Compaction is critical for long sessions; failures force manual intervention or session restart.

4. **#4695** — [MCP OAuth] HTTP-server tokens not reliably reused across sessions; duplicate cache-key entries force repeated re-auth. *(5 comments)*
   [GitHub](https://github.com/github/copilot-cli/issues/4695)
   > Why it matters: OAuth friction degrades developer experience, especially for shared/dev workflows where token reuse is expected.

5. **#232** — [Configuration] Request for `--system-prompt` flag to pass system-level instructions outside repo-specific files. *(4 comments, 10 👍)*
   [GitHub](https://github.com/github/copilot-cli/issues/232)
   > Why it matters: High community interest (10 👍); no native path exists for global system prompts in the CLI.

6. **#4699** — [Sessions] OOM crash (`JavaScript heap out of memory`) during long `--resume` sessions; diagnostic dumps written into user's cwd. *(1 comment, 2 👍)*
   [GitHub](https://github.com/github/copilot-cli/issues/4699)
   > Why it matters: Crash at 4 GiB cap is reproducible; dump files polluting cwd is a secondary annoyance.

7. **#4218** — [Models] Request to let users configure the model pool available to Auto mode. *(1 comment, 13 👍)*
   [GitHub](https://github.com/github/copilot-cli/issues/4218)
   > Why it matters: Highest 👍 in the batch; Auto mode's unpredictability is a top community concern for cost and behavior control.

8. **#4683** — [Windows/Tools] Every shell command emits spurious errors under PowerShell ConstrainedLanguage mode (`$host.SetShouldExit()` blocked). *(2 comments)*
   [GitHub](https://github.com/github/copilot-cli/issues/4683)
   > Why it matters: Enterprise-managed Windows environments are increasingly common; this makes the CLI noisy and confusing.

9. **#4655** — [Agents/Plugins] Custom agents under `com.github.copilot/agents` not discovered in Agent Plugins 1.0. *(3 comments)*
   [GitHub](https://github.com/github/copilot-cli/issues/4655)
   > Why it matters: Plugin authoring is a growing area; discovery failures block the Agent Plugins 1.0 spec.

10. **#4706** — [Triaging] Tool/function calls intermittently emit malformed invocation markup (`<invoke>`) and silently no-op. *(generated by Copilot CLI itself)*
    [GitHub](https://github.com/github/copilot-cli/issues/4706)
    > Why it matters: Meta-issue — the agent tool produced the bug report, and the underlying call-formatting issue affects reliability.

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **System-level prompt injection** — Users want a `--system-prompt` flag or equivalent config to override repo-scoped instructions globally (#232, 10 👍).
- **Auto-mode model pool control** — Operators want to restrict which models Auto can select from for cost and behavior predictability (#4218, 13 👍).
- **Session scoping & filtering** — `/resume` and `/session` should filter by current working directory, making large session lists manageable (#4704, 1 👍).
- **Marketplace governance** — Enterprise users want the ability to block or hide built-in plugin marketplaces (#4715).
- **Per-agent provider selection** — Custom agents within the same session should support different provider endpoints, scoped per-agent rather than process-wide (#4703).

---

## 6. Developer Pain Points

- **OOM crashes on resumed sessions** — Long `--resume` sessions hit the 4 GiB V8 heap cap and crash, with diagnostic files deposited into the user's working directory (#4699).
- **MCP init & OAuth regressions** — Both the legacy `initialize` probe issue (#4525) and unreliable token cache reuse (#4695) degrade MCP server reliability, a core extension surface.
- **Windows path & shell friction** — ConstrainedLanguage mode throws spurious errors on every command (#4683); instruction-file dedup fails with backslash/forward-slash mismatches on Windows (#4702); and permission-gate previews truncate paths (#4701).
- **Session state leaks** — `allow-all` mode resets after inactivity (#4696); queued prompts get stuck (#4705); and `copilot-file-search` threads run unbounded while the session reports idle (#4710).
- **Plugin/agent visibility** — Subagents cannot access main-agent-installed skills (#4708); custom agent discovery under Agent Plugins 1.0 is broken (#4655); and large session histories crash extension startup (#4717).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-04

## 1. Today's Highlights

The community is focused on stability and workflow improvements across the Kimi CLI. Two notable closed bugs — an MCP timeout crash (#1316) and subagents persisting after ESC (#1315) — signal maturing reliability work, while a newly opened issue (#2633) raises concerns about the ACP auth gate blocking custom providers in 1.17+. No new releases were published in the last 24 hours.

---

## 2. Releases

No releases in the past 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Reaction |
|---|-------|--------|----------|
| #2633 | ACP auth gate (1.17+) blocks custom providers that don't need a Kimi account | **OPEN** | Newly reported; no reactions yet. |
| #1313 | Feature Request: Add Hooks System for Notifications and Lifecycle Events | **CLOSED** | 👍 3 — strongest community signal of any issue this period. |
| #1315 | Subagents keep running after hitting ESC | **CLOSED** | Bug in agent lifecycle management. |
| #1316 | MCP timeout causes kimi-cli to be unavailable | **CLOSED** | Critical reliability issue — one broken MCP connection crashes the entire CLI. |
| #1319 | Add methods for local skills operation management | **CLOSED** | Calls for `skills list`, `skills rm`-style tooling parity with `/mcp`. |
| #1320 | Smart arrow key navigation for multiline input | **CLOSED** | UX enhancement for multiline editing ergonomics. |
| #290 | Use OpenRouter with custom model returns 401 | **CLOSED** | Third-party provider auth regression; limited activity. |

**Why they matter:** Issue #1316 and #1315 expose foundational reliability gaps in MCP integration and agent lifecycle handling — both close-to-critical for power users running long tasks. Issue #2633 is the most urgent open item, potentially blocking adoption of non-Kimi models in 1.17+. Issue #1313, though closed, shows strong interest in a hooks/notification system for background agent work.

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| #2332 | fix(kimi): clamp completion budget dynamically | **CLOSED** | Replaces the hardcoded `max_tokens = 32000` with a per-request `max_completion_tokens` computed against the current context window. This prevents budget overflows on context-heavy sessions. |

No other PRs were updated in the last 24 hours.

---

## 5. Feature Request Trends

Three distinct direction themes emerged from this period's issues:

1. **Agent lifecycle & notification hooks** — Users want visibility into when agents need attention during long-running tasks (issue #1313). A hooks system for lifecycle events (start, pause, complete, error) is the most-upvoted request.
2. **Skills & MCP management parity** — The `/skill` and `/mcp` slash commands lack symmetric tooling for user-created resources. Requested commands include `skills list`, `skills rm`, version display, and trigger-word management (issue #1319).
3. **Input UX refinements** — Arrow-key navigation in multiline input currently conflates cursor movement with history traversal, a frequent ergonomic pain point (issue #1320).

---

## 6. Developer Pain Points

- **Single-point-of-failure MCP connections:** A timeout on one MCP server halts the entire CLI session (#1316). Developers expect fault isolation, not a full crash.
- **Agent lifecycle not cancellable:** Pressing ESC does not stop subagents that are already dispatched (#1315). This creates orphaned processes and unexpected API costs.
- **Auth gate blocking non-Kimi providers:** The 1.17+ ACP server requires a persisted Kimi OAuth token unconditionally, preventing use of providers that don't require a Kimi account (#2633).
- **Context budget overshooting:** Previously, the Kimi provider hardcoded `max_tokens = 32000`, which could exceed available context — now addressed in PR #2332 but indicative of a broader budget-management gap.
- **Sparse skill management tooling:** No equivalent to `/mcp` for inspecting or removing user-created skills, forcing manual filesystem navigation.

---

*Data source: [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-09-04

## 1. Today's Highlights

OpenCode saw no new releases in the last 24 hours, but the repo remains highly active with 50 fresh issue updates and 20 PRs. Key momentum centers on the plugin system (permission assertions, dynamic tool namespaces, browser plugin), Desktop V2 UX refinements, and a new plugin manager for the settings dialog. A persistent Gemini edit-tool bug continues to draw attention as the most-engaged open issue.

---

## 2. Releases

*No releases in the last 24 hours.*

---

## 3. Hot Issues

1. **[gemini doesn't handle edit tool very well](https://github.com/anomalyco/opencode/issues/266)** — Open · 39 comments · 17 👍
   The highest-engaged open issue. Gemini repeatedly fails with `"oldString not found"`, likely due to whitespace mismatches. The community is pushing for normalization logic in the edit pipeline.

2. **[Support for multi-agent orchestration in isolated workspaces](https://github.com/anomalyco/opencode/issues/17994)** — Closed · 24 comments · 2 👍
   Users want built-in support for running a "team" of coding agents in isolated workspaces — a feature gap compared to competing tools.

3. **[Add Dynamic workflows for repeatable multi-step automation](https://github.com/anomalyco/opencode/issues/29059)** — Closed · 17 comments · 22 👍
   The most-upvoted feature request this cycle. Developers want project-local reusable workflows, similar to the Claude Code feature referenced in the issue.

4. **[OpenRouter Service Tiers Support for Reducing Model Cost](https://github.com/anomalyco/opencode/issues/28566)** — Closed · 7 comments · 2 👍
   Requests `service_tier` configuration to route cheaper/lower-priority requests, directly impacting per-seat cost for org-wide deployments.

5. **[GLM-5.1 prompt cache randomly drops to 0 on opencode-go](https://github.com/anomalyco/opencode/issues/31348)** — Closed · 7 comments · 7 👍
   A real-cost-impact bug: GLM-5.1 loses prompt cache on long-running agent workflows while DeepSeek V4 Flash stays stable. Affects users running opencode-go in production.

6. **[Non-git projects use "/" as worktree, breaking permission path resolution](https://github.com/anomalyco/opencode/issues/24694)** — Closed · 6 comments · 3 👍
   Non-git directories cause permission paths to resolve incorrectly, breaking sandbox enforcement — a correctness and security concern.

7. **[Install Fails with Syntax Error on WSL](https://github.com/anomalyco/opencode/issues/29210)** — Closed · 6 comments
   Postinstall script crashes on WSL, blocking installation for a significant subset of users.

8. **[v1.17.11 tag: Nix build fails with stale bun.lock](https://github.com/anomalyco/opencode/issues/34117)** — Closed · 4 comments · 4 👍
   Repeated lockfile staleness issue in Nix builds; `bun install --frozen-lockfile` fails when `bun.lock` drifts from `package.json`.

9. **[Renderer crash when workspace files are deleted](https://github.com/anomalyco/opencode/issues/35493)** — Closed · 3 comments
   Desktop app crashes (`Cannot read properties of undefined (reading '_tag')`) when timeline entries reference deleted files — a stability gap in the renderer.

10. **[it constantly goes into repetitive loops](https://github/anomalyco/opencode/issues/47184)** — Open · 2 comments
    Users report the agent entering repetitive loops after recent updates, a quality-of-life and reliability concern.

---

## 4. Key PR Progress

1. **[fix(app): show server-known projects in project lists](https://github.com/anomalyco/opencode/pull/47208)** — Open
   Fixes stale local project lists by pulling from the server state, closing [#43072](https://github.com/anomalyco/opencode/issues/43072).

2. **[feat(opencode): add `run_in_background` to shell tool](https://github.com/anomalyco/opencode/pull/47187)** — Closed
   Adds first-class background shell execution with auto-notification, solving the long-running-command-blocking problem without resorting to `nohup` hacks.

3. **[feat(ai): add tool namespaces](https://github.com/anomalyco/opencode/pull/46530)** — Open
   Introduces recursive `ToolEntry` definitions and `ToolNamespace` groups, with native flattening for OpenAI Responses and related providers.

4. **[fix(tui): exit cleanly when startup probes cannot reach the server](https://github.com/anomalyco/opencode/pull/46726)** — Open
   Prevents the TUI from hanging indefinitely during server cold-start or post-update election cycles, fixing [#36688](https://github.com/anomalyco/opencode/issues/36688).

5. **[fix(client): back off reconnects when the stream never connects](https://github.com/anomalyco/opencode/pull/47204)** — Open
   Replaces fixed 1-second retry with exponential backoff when the event stream fails to connect, fixing [#47062](https://github.com/anomalyco/opencode/issues/47062).

6. **[fix(core): classify GitHub Copilot requests on every route](https://github.com/anomalyco/opencode/pull/47160)** — Closed
   Ensures `X-Interaction-Type` headers are set for Copilot models using the AI SDK route, which previously bypassed HTTP middleware.

7. **[feat(desktop): plugin manager — browse, install, manage plugins](https://github.com/anomalyco/opencode/pull/47180)** — Closed
   Adds a Plugins tab to Desktop settings, aggregating the official catalog, `awesome-opencode`, and opencode.cafe marketplace with npm metadata.

8. **[feat: suggest moving sessions into task worktrees](https://github.com/anomalyco/opencode/pull/47202)** — Closed
   Built-in plugin instruction guides users toward worktree isolation for task sessions.

9. **[fix(core): scope compaction Completed section to finished work](https://github.com/anomalyco/opencode/pull/47203)** — Closed
   Removes "verified facts" from the compaction summary template to prevent stale or incorrect information from persisting.

10. **[feat(simulation): expose and record real mouse input](https://github.com/anomalyco/opencode/pull/47194)** — Open
    Adds `ui.mouse` for hover/leave states and drag operations, enabling Drive to show pointer coordinates in recorded terminal output.

---

## 5. Feature Request Trends

- **Multi-agent orchestration** — Multiple requests (isolated workspaces, task worktree suggestions, sub-agent model selection) converge on the need for built-in agent teams with isolated contexts and per-agent model choice.
- **Reusable workflows** — Dynamic/project-local workflows for repeatable multi-step automation is the most upvoted feature request (22 👍), signaling strong demand for macro-like capabilities.
- **Plugin ecosystem tooling** — Permission assertions, tool namespaces, browser plugins, and a built-in plugin manager all point to the team investing heavily in a richer plugin surface.
- **Cost optimization** — OpenRouter service tiers and prompt-cache reliability issues highlight cost as a primary operational concern for power users.
- **Background execution** — `run_in_background` for shell commands and durable heartbeat monitoring reflect demand for long-running agent patterns without blocking.

---

## 6. Developer Pain Points

- **Edit-tool brittleness** — The Gemini edit tool's whitespace-sensitivity (Issue #266) remains unresolved and is the most-discussed open issue, affecting a large user base.
- **Prompt-cache instability** — GLM-5.1's random cache drops (Issue #31348) cause unpredictable cost spikes in long-running workflows, a production-grade reliability gap.
- **Installation friction on non-standard envs** — WSL syntax errors (Issue #29210) and Nix frozen-lockfile failures (Issues #34117, #34235) create repeated barriers for developers using those platforms.
- **Desktop renderer crashes** — Crashes on deleted files (Issue #35493) and unresponsive TUI (Issue #35474) erode trust in the desktop experience.
- **Repetitive agent loops** — Users report agents getting stuck in loops after updates (Issue #47184), suggesting regression in turn-limit or conversation-completion logic.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-04

## 1. Today's Highlights

The past 24 hours saw continued momentum on core reliability fixes — signal-killed processes now map to non-zero exit codes, the agent-loop timeout gap is acknowledged, and the Rust rewrite PR (#9106) has been closed after community review. A major system-prompt refactor by @mitsuhiko (PR #8998) landed as a draft, opening the door to mid-session dynamic updates without wiping tool state. On the provider side, a Meta/Muse OAuth provider was merged into review, and the OpenAI Responses top-level `instructions` format gained compatibility support.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#5023](https://github.com/earendil-works/pi/issues/5023) | Terminal scrolls to beginning without reason | High-engagement recurring bug (18 comments, 3 👍); session disruption for long-running agents. | 👍 3 · 18 comments · CLOSED |
| [#8845](https://github.com/earendil-works/pi/issues/8845) | Branch summarization hardcodes `maxTokens: 2048` | Deterministic failure on large branches; `generateBranchSummary` caps output regardless of context budget. | 14 comments · CLOSED |
| [#8061](https://github.com/earendil-works/pi/issues/8061) | Context budget ignores `maxTokens` output reservation | Requests rejected at ~78% input because output reservation isn't accounted for; retry also fails. | 👍 2 · 6 comments · OPEN |
| [#9105](https://github.com/earendil-works/pi/issues/9105) | `processFileArguments()` corrupts binary attachments | Lossy forced UTF-8 decode on `@file` mentions and the Read tool breaks image/binary handling entirely. | 2 comments · CLOSED |
| [#9097](https://github.com/earendil-works/pi/issues/9097) | DeepSeek/OpenRouter thinking turns bloat sessions | Every `thinking` block stores a redundant `thinkingSignature`, causing multi-day sessions to hit context limits. | 2 comments · CLOSED |
| [#8857](https://github.com/earendil-works/pi/issues/8857) | Agent loop has no tool-call execution timeout | Hanging tools (e.g. `psql` waiting on a DB) stall the agent indefinitely; neither stream timeout nor bash timeout covers this phase. | 2 comments · CLOSED |
| [#8822](https://github.com/earendil-works/pi/issues/8822) | Streaming output renders late — O(n²) markdown re-render | Every SSE delta triggers a full synchronous markdown re-render; TUI visually falls behind LLM at ~25 chunks/s. | 2 comments · OPEN |
| [#8684](https://github.com/earendil-works/pi/issues/8684) | `PI_OFFLINE` silently disables all provider model discovery | Undocumented behavior contradicts scope; any session with `PI_OFFLINE` loses model-catalog discovery entirely. | 3 comments · OPEN |
| [#9079](https://github.com/earendil-works/pi/issues/9079) | Plugin auth-file keys ignored; only `/login` store checked | Provider plugins storing keys in their own auth file report "No API key found" in `pi -ne` mode. | 2 comments · CLOSED |
| [#9104](https://github.com/earendil-works/pi/issues/9104) | Agent stuck repeating the same response indefinitely | No loop-detection or self-recovery; the agent acknowledged the dead loop but kept generating the same sentence. | 1 comment · CLOSED |

---

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#9106](https://github.com/earendil-works/pi/pull/9106) | **feat!: rewrite pi in rust** | Comprehensive Rust rewrite covering provider streaming, Bedrock/OAuth, agent loop, tools, TUI, CLI/RPC, sessions, extensions, protocol, SQLite, telemetry, evals, and docs. **CLOSED** after community review. |
| [#8734](https://github.com/earendil-works/pi/pull/8734) | **feat(ai): OpenAI Responses top-level `instructions`** | Adds `openai-responses` `systemPromptFormat` option; moves dynamic system prompt to top-level `instructions` without duplicating in `input`. Closes #8388. |
| [#9096](https://github.com/earendil-works/pi/pull/9096) | **feat(ai,coding-agent): Meta provider with Muse OAuth** | New `meta` sub-provider with Muse subscription auth. Notes daily re-minted API tokens and "fake" streaming (burst output). Resolves #7543. |
| [#9093](https://github.com/earendil-works/pi/pull/9093) | **fix(ai): remove Grok Build 0.1 from catalog** | Adds `grok-build-0.1` to `XAI_BUILTIN_EXCLUDED_MODEL_IDS` so only grok-4.3/4.5/4.6 are listed. |
| [#8998](https://github.com/earendil-works/pi/pull/8998) | **System prompt refactor** | Draft by @mitsuhiko enabling partial system-prompt updates mid-session for extensions, emitting updates as mid-conversation signals without wiping state. |
| [#9070](https://github.com/earendil-works/pi/pull/9070) | **fix(coding-agent): musl-static fd & ripgrep on Linux** | Downloads statically linked musl builds of `fd` and `ripgrep`, fixing breakage on NixOS/Alpine where glibc-linked binaries fail. Fixes #9033. |
| [#8994](https://github.com/earendil-works/pi/pull/8994) | **fix(agent): map signal-killed processes to non-zero exit codes** | `waitForChildProcess` now returns the correct signal-derived exit code instead of `null`, fixing the bug where OOM-killed processes appeared as success. Fixes #8992. |
| [#9080](https://github.com/earendil-works/pi/pull/9080) | **feat(tui): jump-to-latest control** | Adds a visible indicator and one-key jump to the latest message in scrolling sessions, based on prior work by @dgtlntv. |
| [#9087](https://github.com/earendil-works/pi/pull/9087) | **fix(ai): fail fast on dynamic model with no implementation** | Previously, every `openrouter/anthropic/*` model (e.g. `claude-opus-5`) returned an HTML 404 page as the error. Now fails fast with a clean error. |
| [#9081](https://github.com/earendil-works/pi/pull/9081) | **fix: let `registerProvider` apiKey read plugin auth files** | `apiKey` now accepts a function resolved at auth-check time, allowing plugins to serve keys from their own auth files instead of requiring `/login`. Closes #9079. |

---

## 5. Feature Request Trends

- **TUI/terminal ergonomics** — Clickable links (OSC 8), branch navigation fixes, jump-to-latest controls, and viewport configuration for large screens remain top community requests.
- **Provider catalog hygiene** — Dynamic model validation (fail-fast on unmapped models), auth-file key support for plugins, and musl-compatible binary distribution reflect ongoing pain with provider reliability.
- **Agent loop robustness** — Tool-call timeouts, reasoning-markup handling, and loop-detection are recurring themes; the community wants the agent to self-recover from stalled or repetitive states.
- **Context and token management** — Multiple issues (#8061, #9097) highlight the need for accurate context-budget accounting that factors in output reservations and strips redundant fields from long sessions.
- **Streaming performance** — The O(n²) markdown re-render (#8822) and quadratic argument parsing (#9062) indicate strong demand for incremental/diff-based rendering in the TUI.

---

## 6. Developer Pain Points

1. **Context budget miscalculations** — Input-only accounting causes rejections at ~78% utilization; output token reservations are ignored, and retry recovery fails for the same reason.
2. **Silent binary corruption** — `processFileArguments()` force-decodes attachments as UTF-8, silently mangling images and binary files in both `@file` mentions and the Read tool.
3. **Missing agent timeouts** — The agent loop has no guard against hung tool calls; only the LLM stream and optional bash timeouts exist, leaving a gap for blocking operations like database queries.
4. **Quadratic performance paths** — Both tool-argument parsing (#9062) and per-delta markdown re-rendering (#8822) scale poorly with streaming volume, causing visible lag at typical SSE chunk rates.
5. **Plugin auth fragmentation** — Plugin-stored API keys are ignored in `pi -ne` mode unless duplicated into the core `/login` store, creating a fragile two-auth-system problem.
6. **Undocumented environment behavior** — `PI_OFFLINE` was documented as disabling only housekeeping network ops, but it also kills provider model discovery — a gap that silently breaks offline-first workflows.
7. **Reasoning-markup bloat** — Redundant `thinkingSignature` fields from DeepSeek/OpenRouter routing inflate sessions to unusable sizes (4.5 MB+) and trigger context-limit failures on resume.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-04

## 1. Today's Highlights

Qwen Code v0.23.0 was released with improvements to the branch picker UI and several core fixes. The community is actively engaging with security reviews around shell allow-rule bypasses, ongoing work to migrate the TUI from ink to OpenTUI, and patches closing internal scaffolding leaks into user-visible output.

---

## 2. Releases

**v0.23.0** — Latest release (published 2026-09-03). No known breaking changes. Key user-facing improvement: the branch picker now displays git state hints (e.g., `↓3 · origin/main` or `Up to date`) beside the Update Project, Commit, and Push actions. See full changelog: [QwenLM/qwen-code](https://github.com/QwenLM/qwen-code)

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#8662](https://github.com/QwenLM/qwen-code/issues/8662) | Migrate TUI rendering layer from ink to OpenTUI | The current ink 7 + React 19 renderer requires ~1037 lines of patches and suffers from flicker and structural limitations. This tracking issue has **28 comments** and is the top community discussion. |
| [#10065](https://github.com/QwenLM/qwen-code/issues/10065) | LM Studio 0.4.21: "failed to parse grammar" error | Affects Qwen Code v0.22.1 users running local models via OpenAI-compatible APIs — even with zero MCP servers. **8 comments**, signals growing pain for local-deploy users. |
| [#10162](https://github.com/QwenLM/qwen-code/issues/10162) | Degrade gracefully when ACP NDJSON channel queue saturates | `qwen serve` currently tears down the entire channel on `NdJsonQueueLimitError`. A graceful degradation would improve production stability. **6 comments**, P2 priority. |
| [#10908](https://github.com/QwenLM/qwen-code/issues/10908) | CI test time bound by module import cost | Release runs spend **2223s on `collect` vs 1372s on tests** in the `cli` workspace. A systemic perf issue affecting CI velocity. **5 comments**, opened today. |
| [#10953](https://github.com/QwenLM/qwen-code/issues/10953) | Todo plan state goes stale during subagent delegation | The active-todo reminder never fires while work is delegated to foreground subagents; plan froze for **55m44s** in one reported session. **4 comments**, P2. |
| [#10791](https://github.com/QwenLM/qwen-code/issues/10791) | Balanced `<thinking>` blocks leak into user-visible output | A proper sanitizer gap: balanced thinking tags on content-only turns bypass current defenses. **4 comments**, welcome-pr. |
| [#9666](https://github.com/QwenLM/qwen-code/issues/9666) | Terminal IME candidate box low contrast on Windows | Chinese IME input is nearly unreadable in dark-terminal mode on Windows. Affects i18n UX significantly. **4 comments**. |
| [#10932](https://github.com/QwenLM/qwen-code/issues/10932) | Voice dictation cannot use Token Plan ASR models | Voice transcription is blocked because the model-ID allowlist hardcodes old IDs, rejecting `qwen-audio-3.0-asr-flash`. **4 comments**, P2. |
| [#10197](https://github.com/QwenLM/qwen-code/issues/10197) | Static loader env assignments can bypass Bash allow rules | Security finding: saved allow rules can be matched after stripping leading environment assignments that change runtime semantics. **3 comments**, P1 security. |
| [#10192](https://github.com/QwenLM/qwen-code/issues/10192) | Bash allow rules bypassed via command substitution in env assignments | Related to #10197 — command substitution hidden in environment assignments can turn a confirmed command into an auto-allowed one. **3 comments**, P1 security. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#10992](https://github.com/QwenLM/qwen-code/pull/10992) | fix(core): catch tool-result scaffolding and system-reminder echo leaks | Closes the two leak shapes from #10797 — fake tool-result XML blocks and system-reminder echoes that currently reach user-visible output. |
| [#10982](https://github.com/QwenLM/qwen-code/pull/10982) | fix(core): demote balanced content-only thinking blocks to thought parts | Extends the thinking-tag leak defense to balanced `<thinking>...</thinking>` blocks on content-only turns. Closes #10791. |
| [#10986](https://github.com/QwenLM/qwen-code/pull/10986) | fix(cli): resolve the OpenTUI slash submit from the live buffer | Fixes a render-lag bug where Enter submitted the wrong action because state trailed keystrokes by one render cycle. **Closed.** |
| [#10938](https://github.com/QwenLM/qwen-code/pull/10938) | feat(web-shell): make Session Workflow dependencies navigable | Closes navigation, shape, and documentation gaps in the Session Workflow surface after #8583; redesigns the plan DAG to lead with the step, not its status. |
| [#10954](https://github.com/QwenLM/qwen-code/pull/10954) | feat(serve): expose background agents the supervisor is running | Adds `GET /background-agents` to `qwen serve`, surfacing the sessions the Agent View supervisor is running and their current state. |
| [#10962](https://github.com/QwenLM/qwen-code/pull/10962) | feat(web-shell): bridge a browser-granted local directory into a session | Enables remote daemon users (cloud box, container) to hand a local directory to the agent via browser permission — a key enabler for distributed workflows. |
| [#10347](https://github.com/QwenLM/qwen-code/pull/10347) | feat(core): auto-retry transient network errors where Ctrl+Y is unavailable | Classifies 4xx errors that are actually wrapped low-level network failures (e.g., `EOF`) as retryable, instead of fail-fast client errors. |
| [#10915](https://github.com/QwenLM/qwen-code/pull/10915) | ci: give every workspace the shared-pool test timeout | Raises the vitest ceiling across all fifteen workspaces that were still using the 5000 ms default, preventing new workspaces from quietly degrading test reliability. |
| [#10421](https://github.com/QwenLM/qwen-code/pull/10421) | fix(review): screen content filters before the probe tree's restore | Fixes a safety gap where `scratch-tree` refused to reset trees when a repository defined a content filter; now screens filters before restore. |
| [#10991](https://github.com/QwenLM/qwen-code/pull/10991) | refactor(daemon): decouple extension activation refresh | Extension activation now completes after its policy is durably committed rather than refreshing every active session directly. New `extension_activation_explicit_refresh` capability signals this contract. |

---

## 5. Feature Request Trends

- **Pluggable thinking-output middleware** ([#10872](https://github.com/QwenLM/qwen-code/issues/10872)): A public middleware API to transform/translate user-visible thinking output before emission — applicable to both CLI and `qwen serve`. Signals demand for i18n support in reasoning output.
- **Standalone daemon sessions without a workspace** ([#8908](https://github.com/QwenLM/qwen-code/issues/8908)): Users want `qwen serve` to support casual chat sessions that don't require selecting or retaining a project workspace — a "global New Chat" experience.
- **Per-process config directories** ([#10984](https://github.com/QwenLM/qwen-code/issues/10984)): A `--config-dir` flag for both `qwen` and `qwen serve` to isolate configuration on a per-process basis, useful for CI and shared environments.
- **Token Plan auth documentation** ([#10620](https://github.com/QwenLM/qwen-code/issues/10620)): Community request to bring Token Plan setup docs to parity with the existing Coding Plan documentation.
- **Channels message prefix filtering** ([#10817](https://github.com/QwenLM/qwen-code/pull/10817)): Optional `messagePrefix` setting for Channels — user messages must begin with a configured prefix, enabling structured routing.

---

## 6. Developer Pain Points

- **Security review overhead**: Multiple P1 security issues around shell allow-rule bypasses (#10197, #10192, #10561) and a dependency CVE audit failure (#10850) are consuming maintainer bandwidth. The `fast-uri/qs/uuid` advisories alone caused a repo-wide CI break.
- **TUI rendering fragility**: The ink-to-OpenTUI migration (#8662) is a long-running effort driven by persistent flicker, patch bloat (~1037 lines), and structural bugs (slash-submit lag, VP alignment). Community frustration is high given the issue age (since Aug 2026).
- **CI slowness from module imports**: With `collect` time exceeding test execution time in multiple workspaces (#10908), developers are blocked on slow release feedback loops.
- **Scaffolding leaks into user output**: Content-only thinking blocks (#10791) and tool-result/system-reminder echoes (#10797) are leaking internal model scaffolding into visible output — a trust and UX issue that required two back-to-back PRs to close.
- **Voice/ASR model ID rigidity**: The hardcoded model-ID allowlist (#10932) blocks adoption of newer Token Plan ASR models, requiring code changes for what is essentially a configuration update.
- **Multi-workspace daemon bugs**: Stale settings resolution in ACP session handlers (#10094) and session spinner drops mid-turn (#9645, #10989) point to ongoing instability in daemon-side state management across workspaces.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-09-04

## 1. Today's Highlights

The CodeWhale TUI project shipped **v0.9.12** with a major fleet-only UX overhaul covering the workbar, underwater default theme, startup flow, and settings reorganization. Three PRs landed today addressing shell job origin tracking, OpenCode session header support, and configurable reasoning-only retry behavior — signaling active hardening of both the TUI layer and provider integrations.

---

## 2. Releases

**v0.9.12** landed via PR [#5862](https://github.com/Hmbown/CodeWhale/pull/5862), integrating 10 UX slices: unified hover contract across `Link`/`TruncatedText`, workbar rename (sidebar/rail → workbar, bottom default), settings regrouping, retro theme support, provider selection polish, logo updates, and the `Underwater` theme default. No further releases in the last 24h.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| #5864 | `serve --acp` missing `session/list` & `session/load` | ACP clients cannot enumerate or resume existing Codewhale sessions — blocks multi-session editor integrations. | New, 1 comment |
| #5863 | `serve --acp` missing session config options | Editors can't show or switch working modes/models/configOptions via ACP. Critical for editor-plugin parity. | New, 2 comments |
| #5316 | EPIC-005: CodeWhale TUI Crate Decomposition | Umbrella tracking issue for the entire crate-decomposition effort; all sub-EPICs and FEAT reports roll up here. | 21 comments, long-running |
| #5866 | Ophthalmology CPT & ICD-10 Updates for 2026 | Appears to be off-topic / spam; likely a bot-posted medical billing article. Low relevance to dev community. | 1 comment |

**Takeaway:** ACP session management gaps (#5863, #5864) are the most discussed open issues. Both flag missing endpoints that editor clients depend on for session discovery and configuration. The crate decomposition epic (#5316) remains the structural backbone for ongoing TUI rework.

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| #5869 | `fix(shell): preserve task origin in job snapshots` | Fix | Resolves a bug where background shell jobs lacked stable origin identifiers, causing error output to be projected onto the wrong tool card in multi-job sessions. |
| #5868 | `feat: send x-opencode-session header` | Feature | Adds the `\x-opencode-session` header for OpenCode Go/Zen providers, enabling prompt caching optimization and proper session attribution. Fixes UA classification issues. |
| #5867 | `feat(config): add [reasoning_only] section` | Feature | Makes `MAX_REASONING_ONLY_REPROMPTS` user-configurable instead of hardcoded at 2. Addresses silent retry behavior when reasoning models return only hidden thinking. |
| #5865 | `refactor(tui): re-land FEAT-020 plugin command shapes` | Refactor | Re-lands plugin command shapes onto `main` after the original PR was isolated on an integration branch. Tracked under epic #5316. |
| #5833 | `feat(memory): FEAT-019 memory capability` | Feature ✅ Closed | Adds `CommandCapabilities::MEMORY` bit, `CommandMemoryContext` facet, and a TUI memory adapter with typed outcomes for search/remember/get/export/reindex/delete. |
| #5858 | `tui: collapse ocean_treatment into ThemeId::Underwater` | Refactor ✅ Closed | Consolidates ocean-themed assets into a single `Underwater` theme, including deepsea alias, locale strings, picker list, and `OceanRamp` config migration. |
| #5862 | `Codewhale 0.9.12: Fleet-only UX` | Feature ✅ Closed | Integrates 10 UX slices (hover, workbar, settings, retro theme, provider, logo, roles) for the v0.9.12 release. |
| #5843 | `tui: align typed config and schema with live value spaces` | Refactor ✅ Closed | Aligns typed theme/config/schema with runtime values; drops orphaned locale keys. CI clean, 425 dead-code gates. |

---

## 5. Feature Request Trends

- **ACP session management** — Two concurrent issues (#5863, #5864) request `session/list`, `session/load`, and config option exposure, indicating strong demand for ACP protocol completeness to support editor integrations.
- **Configurability of reasoning model behavior** — PR #5867 reflects community demand for tunable reasoning-only retry parameters rather than hardcoded values.
- **Provider-specific protocol compliance** — PR #5868 shows ongoing effort to meet provider expectations (OpenCode session headers, prompt caching), a trend likely to continue as more providers are added.
- **TUI theming & UX polish** — The v0.9.12 release and related PRs (#5858, #5843) demonstrate sustained investment in visual identity, theme system simplicity, and config schema correctness.
- **Crate decomposition** — Epic #5316 and PR #5865 indicate a long-term architectural push to break the monolithic TUI crate into smaller, independently manageable components.

---

## 6. Developer Pain Points

1. **Shell job origin tracking** — Prior to PR #5869, background jobs in the same session couldn't be reliably distinguished, leading to error output misattribution. This points to a broader challenge in managing concurrent shell state in a TUI context.
2. **ACP protocol gaps** — Missing `session/list`, `session/load`, and config endpoints (#5863, #5864) block editor clients from offering full session management, creating friction for users who rely on Codewhale through IDE integrations.
3. **Hardcoded reasoning retries** — The previously hardcoded `MAX_REASONING_ONLY_REPROMPTS = 2` (#5867) left no room for users to tune behavior when reasoning-only models returned empty answers, a recurring tension between sensible defaults and configurability.
4. **Schema/config drift** — PR #5843's effort to re-align typed config with live value spaces suggests the config system had drifted from its runtime representation, a pain point for maintainers handling theme and locale migrations.
5. **Crate monolith size** — The multi-PR decomposition effort (#5316, #5865) reflects ongoing difficulty in managing a large, coupled TUI crate, with feature work needing to be re-landed after integration-branch isolation.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*