# AI CLI Tools Community Digest 2026-08-25

> Generated: 2026-08-25 01:39 UTC | Tools covered: 10

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
**Date: 2026-08-25**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in mid-2026 is defined by a maturation phase: early novelty has given way to reliability, observability, and enterprise-readiness concerns. Community discourse across tools converges on subagent/session lifecycle management, transparent token-cost attribution, and platform parity (especially Windows). The ecosystem is split between vendor-locked incumbents (Claude Code, Codex, Copilot) and more open or self-hosted alternatives (OpenCode, Pi, DeepSeek TUI), with the latter communities showing disproportionately high issue density relative to release cadence.

---

## 2. Activity Comparison

| Tool | New Issues | Open PRs | Release | Release Status |
|---|---|---|---|---|
| **Claude Code** | 10 | 3 (1 open) | v2.1.243 | ⚠️ Regression: Linux x64 segfault |
| **OpenAI Codex** | 10 | 10 (all merged/open) | v0.150.0-alpha.8 | Alpha, active development |
| **Gemini CLI** | 10 | 10 (4 closed, 6 open) | v0.56.0-nightly, v0.57.0-preview.1 | Nightly + preview |
| **GitHub Copilot CLI** | 10 | 1 (open) | v1.0.81-9 | Stable patch |
| **Kimi Code** | 0 | 1 (open) | None | Quiet day |
| **OpenCode** | 10 | 7+ (3 closed) | v1.18.22 | Bugfix release |
| **Pi** | 10 | 9 closed, 4 open | v0.84.3 | Stable release |
| **Qwen Code** | 10 | 12 (all open) | v0.22.0-nightly | Nightly |
| **DeepSeek TUI** | 8 | 8 (2 closed, 6 open) | None (v0.9.12 pre-release) | Pre-release gating |
| **Grok Build** | 0 | 0 | None | No activity |

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|---|---|---|
| **Subagent/Agent Lifecycle Reliability** | Gemini CLI, Copilot CLI, DeepSeek TUI, OpenCode, Pi | False success reports, hung subagents, silent state loss at turn boundaries, missing billing attribution |
| **Token/Cost Transparency** | Codex, Copilot CLI, Qwen Code, DeepSeek TUI | Per-tool cost attribution, OTEL billing gaps, /usage diagnostics, MCP server cost visibility |
| **Auth & Session Persistence** | Codex, Copilot CLI, Pi | Sign-in loops, rotated refresh-token invalidation, OAuth scope/issuer regressions across platforms |
| **Context & Memory Management** | Claude Code, Gemini CLI, Qwen Code, Pi | Invisible memory loads, configurable truncation limits, recall/forget asymmetry, compaction tuning |
| **Platform Parity (Windows/Linux)** | Claude Code, Codex, Copilot CLI, OpenCode, Pi, Gemini CLI | Windows Desktop UX gaps, Wayland breakage, symlink handling, terminal I/O stalling, proxy/SSO friction |
| **TUI/Rendering Performance** | OpenCode, Qwen Code, Pi, DeepSeek TUI | Flicker, full repaints, ink renderer limits, mouse support, VRAM/budget overruns |
| **MCP Reliability** | Claude Code, Copilot CLI, Qwen Code, DeepSeek TUI | OAuth fragility, reconnection after server restart, tool-schema explosion on non-Anthropic models |

---

## 4. Differentiation Analysis

| Dimension | Vendor-Locked (Claude Code, Codex, Copilot) | Open/Self-Hosted (OpenCode, Pi, Gemini CLI, DeepSeek TUI) | Niche (Kimi Code, Grok Build) |
|---|---|---|---|
| **Primary Focus** | Enterprise integration, model access breadth, OAuth/MCP ecosystems | Customization, transparency, multi-provider support, self-hosting | Specific model quality, encoding correctness |
| **Community Profile** | High issue volume, enterprise pain points (SSO, proxy, compaction) | High feature-request density, power-user-driven, rapid PR turnover | Low activity, targeted bug fixes |
| **Release Cadence** | Frequent stable + alpha/nightly splits | Mixed: nightly builds (Gemini, Qwen) vs. slower stable cycles (Pi, OpenCode) | Minimal; Kimi Code had one safety PR |
| **Technical Approach** | Closed architectures, proprietary telemetry, controlled model gateways | Open configs, plugin/skill systems, local model support (llama.cpp, Bedrock) | Minimalist; focuses on core correctness |
| **Windows Support** | Fragmented but prioritized (Copilot, Codex desktop) | Explicitly called out as a pain point; Pi shipped PowerShell tool | Not a focus |

---

## 5. Community Momentum & Maturity

| Tier | Tools | Rationale |
|---|---|---|
| **High Momentum** | Gemini CLI, Qwen Code, DeepSeek TUI | High open-PR counts, nightly release cadence, aggressive feature integration (relay, supervised ops, evals) |
| **Steady & Stable** | Pi, OpenCode | Regular releases with targeted fixes; PRs land quickly; community feedback directly shapes release notes |
| **Enterprise-Led** | Claude Code, Codex, Copilot CLI | High issue volume signals active usage but slower community PR contribution; releases driven internally with known regressions (Claude Code Linux segfault) |
| **Low Activity** | Kimi Code, Grok Build | Kimi Code had one correctness fix; Grok Build had zero activity — both in quiet phases |

**Most Active Community (by engagement):** Gemini CLI and OpenCode show the strongest combination of issue comments, upvotes, and contributor PRs relative to tool size. DeepSeek TUI's community is dense but focused on a single pre-release cycle.

---

## 6. Trend Signals

1. **Subagent Reliability Is the #1 Unresolved Category** — Every major tool surfaces false successes, hung delegations, or silent state loss. This signals the agentic paradigm is outpacing the orchestration layer. Developers should expect continued instability in multi-turn delegate workflows across all tools.

2. **Cost Attribution Is Becoming a Compliance Requirement** — OTEL gaps (Copilot CLI), invisible tool-schema costs (Gemini CLI, DeepSeek TUI), and subagent billing gaps (Copilot CLI) suggest enterprises will demand per-operation cost visibility. Tools that ship granular cost telemetry will gain organizational adoption advantage.

3. **MCP Is a Fragile Abstraction Layer** — Regressions in OAuth scope handling (Copilot CLI), reconnection after server restart (Qwen Code, DeepSeek TUI), and tool-schema inflation on non-Anthropic models (Copilot CLI) indicate MCP is still in its early adoption phase. Teams relying on MCP should pin versions and validate provider compatibility.

4. **Platform Parity Gaps Persist Across All Tools** — Windows terminal breakage (Codex, Copilot CLI), Wayland failure (Gemini CLI), Linux x64 segfaults (Claude Code), and symlink issues (OpenCode, Gemini CLI) show no tool has achieved reliable cross-platform stability. Enterprise deployments should validate on target OS before adoption.

5. **Nightly/Preview Cadence Signals Rapid Iteration Risk** — Gemini CLI and Qwen Code ship nightly builds with significant architectural changes (relay integration, OpenTUI migration). While innovation is high, regression risk is elevated. Stable releases (Pi v0.84.3, Copilot v1.0.81-9) offer more predictability for production use.

6. **TUI Rendering Is a Bottleneck** — Ink renderer limits (Qwen Code), flicker reports (OpenCode, DeepSeek TUI), and rendering bugs (Pi) suggest the terminal UI layer is a shared architectural constraint. Tools migrating to OpenTUI or custom renderers (DeepSeek TUI) may gain a quality edge.

---

**Bottom Line for Decision-Makers:** The ecosystem is mature enough for production use in controlled environments but lacks cross-platform reliability and subagent guarantees. For enterprise adoption, prioritize tools with stable release cadences (Pi, Copilot CLI) and clear observability (Codex, DeepSeek TUI). For experimental or self-hosted workflows, Gemini CLI and OpenCode offer the most active feature development. Avoid unpinning versions on Claude Code until the Linux x64 regression is resolved.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report

*Data as of 2026-08-25 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

### 1. Skill-Creator / Evaluation Pipeline (Multiple Fixes)
**PRs:** [#1298](https://github.com/anthropics/skills/pull/1298) · [#1099](https://github.com/anthropics/skills/pull/1099) · [#1050](https://github.com/anthropics/skills/pull/1050) · [#539](https://github.com/anthropics/skills/pull/539) · [#1602](https://github.com/anthropics/skills/pull/1602)
**Status:** All OPEN
The most-discussed cluster in the repo. `run_eval.py` and its parent scripts (`run_loop.py`, `improve_description.py`) consistently report `recall=0%` on every iteration due to trigger-detection failures and Windows subprocess bugs. Multiple contributors have filed independent patches; #1298 consolidates the eval-artifact, stream-reading, trigger, and parallel-worker fixes. **#556** (issue) documents 10+ independent reproductions. This is the single highest-friction area in the ecosystem.

### 2. Document Typographic Quality Control
**PR:** [#514](https://github.com/anthropics/skills/pull/514)
**Status:** OPEN
Blocks common typographic failures in AI-generated documents: orphan line-ends, widow paragraphs, and numbering misalignment. Addresses a widespread pain point — users rarely request good typography, so skills must proactively enforce it.

### 3. DOCX & PDF Skill Hardening
**PRs:** [#541](https://github.com/anthropics/skills/pull/541) · [#538](https://github.com/anthropics/skills/pull/538)
**Status:** Both OPEN
[#541] fixes tracked-change `w:id` collisions with existing bookmarks that corrupt DOCX files. [#538] corrects 8 case-sensitivity mismatches in the PDF skill's `SKILL.md`. Both reflect real-world breakage from community usage.

### 4. Hivemind — Zero-Cost Multi-Agent Orchestration
**PR:** [#1628](https://github.com/anthropics/skills/pull/1628)
**Status:** OPEN
Delegates mechanical coding work to headless opencode workers running on free models, while Claude Code retains planner/reviewer/merger control. Directly addresses the community concern (see Issue #1487) about expensive context consumption — a complementary design philosophy to the self-audit skill.

### 5. Self-Audit / Reasoning Quality Gate
**PR:** [#1367](https://github.com/anthropics/skills/pull/1367)
**Status:** OPEN
Mechanical file-verification step followed by a four-dimension reasoning audit, applied before delivery. Also proposed as a full pipeline in Issue [#1385](https://github.com/anthropics/skills/issues/1385). Universal across stacks.

### 6. Testing Patterns Skill
**PR:** [#723](https://github.com/anthropics/skills/pull/723)
**Status:** OPEN
Covers the full testing stack: Testing Trophy philosophy, AAA unit tests, React Testing Library, edge cases. Responds to sustained demand for structured test-generation guidance.

### 7. ODT / OpenDocument Skill
**PR:** [#486](https://github.com/anthropics/skills/pull/486)
**Status:** OPEN
Extends document-skill coverage to ODT/ODS/ODF formats — LibreOffice-native and ISO-standard — filling a gap between the existing DOCX and PDF skills.

---

## 2. Community Demand Trends

Distilled from the top Issues:

| Trend | Evidence |
|---|---|
| **Evaluation & self-verification** | Issues #556 (0% trigger rate), #1367 / #1385 (reasoning quality gates), #1487 (context exhaustion from eager injection) |
| **Trust & security boundaries** | Issue #492 (43 comments, 2 👍) — community skills impersonating the `anthropic/` namespace; Issue #1175 (SharePoint access-control concerns) |
| **Enterprise / platform skills** | Issue #228 (org-wide sharing, 8 👍); PR #568 (ServiceNow platform coverage across ITSM/ITOM/SecOps); PR #181 (SAP-RPT-1-OSS) |
| **Workflow automation & multi-agent** | PR #1628 (Hivemind orchestration); Issue #16 (expose Skills as MCPs) |
| **Document fidelity** | Issues #12 (docx whitespace corruption), #538/#541 (PDF/DOCX bugs) |
| **Creator tooling health** | Issue #202 (skill-creator reads like docs, not instructions); Issue #189 (duplicate skills from overlapping plugins) |

---

## 3. High-Potential Pending Skills

These PRs are active, well-scoped, and not yet merged — strong candidates for near-term landing:

| PR | Skill | Why It's Poised |
|---|---|---|
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a universal, high-frequency pain point with a narrow, self-contained skill |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Full-stack testing guidance; complements existing code-creation skills |
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | Novel multi-agent delegation model; addresses cost-awareness explicitly |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Pre-delivery quality gate; maps directly to the reasoning-quality pipeline proposal (#1385) |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT** | Fills a clear format gap; low-risk, high-utility addition |
| [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** | Niche but complete HPC cluster management skill; first of its kind in the repo |

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **reliable evaluation and self-verification tooling** — the skill-creator's broken trigger detection (#556, #1298) is the single highest-friction bug in the ecosystem, and the surge in quality-gate, self-audit, and reasoning-pipeline proposals (#1367, #1385, #1628) reflects a community trying to compensate for the lack of trustworthy automated skill validation.

---



# Claude Code Community Digest — 2026-08-25

## 1. Today's Highlights

Claude Code v2.1.243 lands with a new `/usage` loop breakdown and a customizable `modelPicker` setting, but the release is shadowed by a wave of Linux x64 segfault reports tied to a mimalloc/glibc interposition regression. Meanwhile, the auto-memory system faces growing criticism over its invisibility, rigidity, and the persistence of documented rule-violation patterns across sessions.

## 2. Releases

**v2.1.243** — First new build in the window. Key changes:

- **`/usage` loop breakdown:** `/usage` now surfaces per-loop run count, total tokens, tokens per run, and last-run timestamp, making runaway or chatty `/loop` tasks easy to detect.
- **`modelPicker` setting:** A new config option lets users curate the `/model` picker with an ordered, labeled list of models (accepts any ID spelling).

**⚠ Known regression:** v2.1.243 (and 2.1.242) introduce a **deterministic SIGSEGV on Linux x64** during startup. The root cause is the first build to export its bundled mimalloc as versioned glibc allocator symbols; `glibc 2.44`'s `newlocale` calls `free(NULL)` through the interposed allocator before `main`, triggering a crash. Affected distros include CachyOS. **Workaround:** pin to v2.1.241 or earlier.

- [#89360](https://github.com/anthropics/claude-code/issues/89360) — 24 comments, 8 👍
- [#89334](https://github.com/anthropics/claude-code/issues/89334) — 7 comments, 6 👍
- [#89371](https://github.com/anthropics/claude-code/issues/89371) — 5 comments, 6 👍
- [#89369](https://github.com/anthropics/claude-code/issues/89369) — 2 comments, 8 👍

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#82056](https://github.com/anthropics/claude-code/issues/82056) | Auto-memory index load state invisible | No in-session signal tells you whether `MEMORY.md` loaded whole, truncated, or not at all — making debugging persistent-memory behavior a guessing game. | 26 comments, 1 👍 |
| [#89360](https://github.com/anthropics/claude-code/issues/89360) | v2.1.243 segfault (Linux) | The flagship regression of the day; blocks all Linux x64 users on the latest release. | 24 comments, 8 👍 |
| [#54461](https://github.com/anthropics/claude-code/issues/54461) | Windows Desktop: cannot change working dir or open new chat | Long-standing Desktop UX blocker — 4 months old with high visibility. | 22 comments, 13 👍 |
| [#79217](https://github.com/anthropics/claude-code/issues/79217) | Make auto-memory index size limit configurable | Hard 200-line / 25KB cap truncates large `MEMORY.md` silently; users want a tunable limit. | 4 comments, 2 👍 |
| [#89316](https://github.com/anthropics/claude-code/issues/89316) | Duplicate Remote Control sessions on single prompt | Same task name multiplied across sessions — data integrity concern for collaborative workflows. | 2 comments, 0 👍 |
| [#85021](https://github.com/anthropics/claude-code/issues/85021) | Permission-mode indicators use unrenderable Unicode | U+23F5 (`⏵`) renders as tofu across most terminals; users have filed this 5+ times over 6 months. | 2 comments, 1 👍 |
| [#87825](https://github.com/anthropics/claude-code/issues/87825) | Persistent memory rules ignored before destructive actions | Documented pattern of rule violations across sessions; previous report closed as stale while the behavior continued. | 1 comment, 0 👍 |
| [#85660](https://github.com/anthropics/claude-code/issues/85660) | Custom diff color overrides ignored | Theme authors' `diffAdded`/`diffRemoved` overrides silently fall back to base defaults — a trust issue for theming. | 2 comments, 0 👍 |
| [#84878](https://github.com/anthropics/claude-code/issues/84878) | AWS SSO-OIDC hangs behind HTTPS proxy | Regression (>2.1.187): `awsAuthRefresh` pre-check ignores `HTTPS_PROXY`, causing indefinite hangs for enterprise users. | 1 comment, 3 👍 |
| [#88579](https://github.com/anthropics/claude-code/issues/88579) | Persistent memory is invisible and unverifiable | Broader critique: memory ships but is undocumented for most users, per-directory, and easily broken — fueling a 91k-star third-party replacement ecosystem. | 1 comment, 1 👍 |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#79898](https://github.com/anthropics/claude-code/pull/79898) | Claude apps gateway on AWS example deployment assets | ✅ Closed | Reference artifacts for running the Claude Apps Gateway on AWS with Amazon Bedrock; sibling to the existing GCP example. |
| [#75252](https://github.com/anthropics/claude-code/pull/75252) | Clarify plugin MCP configuration scope | ✅ Closed | Reopened from #74857; clarifies that plugin `mcpServers` config is separate from user-level MCP allow/deny in `~/.claude.json`. |
| [#83890](https://github.com/anthropics/claude-code/pull/83890) | Create pylint.yml | 🔄 Open | Community-contributed PyLint integration config. |

*Only 3 PRs landed in the 24h window; no additional PRs were available for selection.*

## 5. Feature Request Trends

1. **Persistent memory transparency and configurability** — Multiple issues (#82056, #79217, #88579) converge on the same theme: users want visibility into what memory loaded, the ability to tune size limits, and confidence that memory rules are actually enforced. The "invisible memory" problem is the dominant feature narrative.
2. **Model selection flexibility** — The new `modelPicker` setting in v2.1.243 directly responds to long-standing demand for curated model lists. Expect further requests around default model behavior and per-project model policies.
3. **CLI diagnostics visibility** — The `/usage` loop breakdown signals a trend toward richer diagnostic telemetry. Community will likely push for similar breakdowns on MCP calls, permission decisions, and sandbox events.

## 6. Developer Pain Points

- **Linux x64 startup crash (mimalloc/glibc interposition):** A release-introduced regression that bricks the CLI on glibc 2.44+ systems. At least 7 duplicate reports in a single day; the most urgent pain point in the window.
- **Auto-memory opacity:** No feedback on whether `MEMORY.md` loaded fully or was truncated; rules are silently ignored before destructive actions; the 25KB / 200-line cap is not configurable. This creates a trust deficit around a shipped feature.
- **Windows Desktop UX gaps:** Inability to change the working directory or open new chats remains unresolved for months (#54461, 13 👍).
- **Theme/rendering inconsistencies:** Custom diff color overrides (#85660) and unrenderable Unicode permission indicators (#85021) both signal that the TUI layer is not honoring user configuration reliably.
- **Proxy/SSO enterprise friction:** AWS SSO-OIDC hangs behind proxies (#84878) and MCP OAuth stale client registrations (#84614) point to recurring gaps in network-layer handling that disproportionately affect professional/enterprise users.
- **Sandbox performance and noise:** Glob re-expansion overhead (#84681) and sandbox artifacts appearing as untracked files (#84662) degrade the developer experience in large repos.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-25

## 1. Today's Highlights

Auth stability remains the dominant concern across the Codex Desktop app, with five separate issues in the last 24 hours reporting sign-in loops, rotated refresh tokens being invalidated, and 401 errors on thread resume. Meanwhile, the CLI team shipped a new alpha (`v0.150.0-alpha.8`) and landed a batch of ten merged PRs covering hook instrumentation, thread-title generation, and internal reliability hardening.

---

## 2. Releases

**rust-v0.150.0-alpha.8** — New alpha published today. No detailed release notes are available yet; see the full changelog for migration notes.

---

## 3. Hot Issues

| # | Summary | Why It Matters | Community |
|---|---------|---------------|-----------|
| [#39162](https://github.com/openai/codex/issues/39162) | macOS thread resume invalidates ChatGPT auth, redirects to sign-in | Blocks core workflow for a leading OS; auth state is lost when reopening existing conversations | 53 comments · 31 👍 |
| [#39903](https://github.com/openai/codex/issues/39903) | Disable "Ran N commands" collapsing in TUI | Users want full command visibility; the auto-collapse hides executed tool calls during long runs | 21 comments · 36 👍 |
| [#35746](https://github.com/openai/codex/issues/35746) | Paginated rollout history drops valid records and reuses ordinals | Data integrity bug in CLI history; affects auditability of multi-turn sessions | 25 comments · 1 👍 |
| [#39189](https://github.com/openai/codex/issues/39189) | Windows thread open signs out Pro account after workspace-only 401 | Auth failure cascades from workspace config to full sign-out on Windows; mirrors macOS #39162 | 20 comments · 4 👍 |
| [#34227](https://github.com/openai/codex/issues/34227) | Windows pet overlay hit region desynchronizes over time | Long-running sessions on Windows cause the mascot overlay to drift from its clickable bounds | 17 comments · 1 👍 |
| [#39803](https://github.com/openai/codex/issues/39803) | Repeated sign-in screen after completing a response | Auth refresh appears broken post-turn; users are prompted to re-sign-in repeatedly | 12 comments |
| [#37996](https://github.com/openai/codex/issues/37996) | Stream disconnected before completion | Server-side stream errors interrupt turns without clean retry; affects Pro users on Linux | 10 comments · 2 👍 |
| [#39841](https://github.com/openai/codex/issues/39841) | Windows workspace terminal fails with "setup refresh had errors" | Terminal tooling entirely non-functional on Windows for some users after config migration | 9 comments |
| [#21777](https://github.com/openai/codex/issues/21777) | Expose auto-compaction to the agent | Users want agents to decide when to compact rather than having it happen silently mid-turn | 9 comments · 9 👍 |
| [#40267](https://github.com/openai/codex/issues/40267) | macOS thread resume signs out; rotated refresh token never persisted | Auth poller gets `401 refresh_token_invalidated`; fresh login is also invalidated within 76s — a persistent, hard-to-resolve loop | 7 comments |

---

## 4. Key PR Progress

| # | Title | What's New |
|---|-------|-----------|
| [#40511](https://github.com/openai/codex/pull/40511) | Add hooks for interrupted turns | New `Interrupt` hook event fires before abort; flushes transcript with session, turn, model, and working directory context. |
| [#40509](https://github.com/openai/codex/pull/40509) | Add persisted thread artifact models | New `thread_artifacts` SQLite table with typed identities, JSON payloads, cascade deletion, and paginated reads. |
| [#40508](https://github.com/openai/codex/pull/40508) | Persist realtime events in the thread timeline | Clients now get a bounded view of realtime conversations preserving speech, agent work, and turn-lifecycle ordering. |
| [#40502](https://github.com/openai/codex/pull/40502) | Collapse home paths in AGENTS.md status summaries | Paths under `$HOME` render as `~` in `/status`, improving readability while preserving project-relative paths. |
| [#40501](https://github.com/openai/codex/pull/40501) | Deduplicate plugin skills in unified mentions | `skills/list` now returns a nullable `pluginId` so the `@` search no longer shows a plugin and its owned skills as separate entries. |
| [#40499](https://github.com/openai/codex/pull/40499) | Harden startup rollout migration against concurrent updates | Rollout migration now waits for in-progress rollouts to finish, preventing stale or empty-discovery paths. |
| [#40494](https://github.com/openai/codex/pull/40494) | Hide ephemeral system threads from TUI routing | `thread/started` notifications for `system`-source ephemeral threads are now ignored, keeping the agents overview clean. |
| [#40492](https://github.com/openai/codex/pull/40492) | Generate descriptive TUI thread titles | Unnamed threads now get an immediate provisional title from the first user message, later replaced by an async-generated title. |
| [#40488](https://github.com/openai/codex/pull/40488) | Export turn cost as an OTEL metric | New `codex.turn.cost_microusd` counter with turn, interruption, speed, and reasoning-effort attributes for observability. |
| [#40498](https://github.com/openai/codex/pull/40498) | Increase app-server model refresh interval | Background model refresh widened from 3 min to 4 min 30 sec, reducing unnecessary polling. |

---

## 5. Feature Request Trends

- **Transparent command visibility** — The #39903 request (36 👍) and the hooks feature work (#40511) both signal demand for full observability into tool execution and turn lifecycle events.
- **Agent-controlled context management** — Issue #21777 (expose compaction to the agent, 9 👍) reflects a growing desire for agents to make explicit context-window decisions rather than having compaction applied opaqueley.
- **Reliable auth/session persistence** — At least six separate auth-related issues in 24 hours indicate a strong community need for a durable, cross-platform session management strategy.
- **TUI UX polish** — Thread title generation (#40492), home-path collapsing (#40502), and system-thread filtering (#40494) show momentum toward a cleaner, more readable terminal interface.

---

## 6. Developer Pain Points

1. **Auth/session instability on desktop** — The single biggest pain point. Users on macOS and Windows report sign-in loops, rotated-but-invalidated refresh tokens, and 401 errors when resuming threads. This is the most upvoted and commented-on category right now.
2. **Windows terminal and sandbox breakage** — Issues #39841, #39933, #34928, and #40119 all report terminal startup failures, sandbox setup errors, or kernel crashes on Windows, making the platform unreliable for automated workflows.
3. **Subagent lifecycle leaks** — Issues #39694 and #35209 both report completed subagent threads remaining in `Active`/`Working` state, eventually hitting the agent-thread limit and blocking further work.
4. **Hook visibility gaps** — Issue #34289 documents that `PostToolUse` carries no failure signal and `PostToolUseFailure` never fires, making it impossible for hooks to distinguish succeeded from failed tool calls.
5. **Config migration regressions** — Issue #40339 reports that the automatic `config.toml` migration generates invalid `permissions` blocks that fail `--strict-config` parsing, breaking CLI sessions for affected users.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-25

## 1. Today's Highlights

Gemini CLI shipped a nightly release (v0.56.0-nightly.20260825) and a preview patch (v0.57.0-preview.1), both carrying a critical fix for the A2A server's stale cancellation bug that caused repeated `Execution aborted` crashes after user prompts. The community continues to surface subagent reliability as the top concern, with three P1 issues—subagent recovery, generalist agent hangs, and shell command stalling—generating the most engagement this week. A new PR also introduces `eval:from-log`, enabling contributors to convert real session transcripts into behavioral eval drafts.

---

## 2. Releases

**v0.56.0-nightly.20260825.g812f7a2bc** ([PR #29062](https://github.com/google-gemini/gemini-cli/pull/29062))
- Cherrypicks the A2A server cancellation fix and write-policy safety checker declaration from the nightly line.

**v0.57.0-preview.1** ([PR #29024](https://github.com/google-gemini/gemini-cli/pull/29024))
- Patch release over preview.0, carrying the same two fixes for downstream preview consumers. Changelog: [PR #29060](https://github.com/google-gemini/gemini-cli/pull/29060).

---

## 3. Hot Issues

1. **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 · 13 comments · 2 👍
   The `codebase_investigator` subagent surfaces a false `GOAL` success when it hits the turn limit, masking the real interruption. High comment volume signals this is a common failure mode for deep-research workflows.

2. **[Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1 · 8 comments · 8 👍
   The generalist agent deadlocks indefinitely whenever it defers to subagents. Eight upvotes indicate broad user impact; the workaround (disabling subagent use) is a painful restriction.

3. **[Zero-Dependency OS Sandboxing & Post-Execution Intent Routing](https://github.com/google-gemini/gemini-cli/issues/19873)** — P2 · 8 comments · 1 👍
   Proposes leveraging the model's native bash affinity through sandboxed execution and intent-aware routing—addresses both security and UX concerns around untrusted shell output.

4. **[AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — P2 · 7 comments · 1 👍
   An epic investigating whether AST-based tools can reduce turn waste and token noise by reading precise method bounds instead of whole files. Directly impacts codebase-investigator efficiency.

5. **[Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** — P2 · 6 comments
   Users report the model refuses to invoke custom skills and subagents unless explicitly prompted, severely limiting the value of the skills system. Anecdotal but widely felt.

6. **[Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** — P2 · 5 comments
   Sessions the extraction agent dismisses as low-signal remain unprocessed and repeatedly resurface, creating a noisy feedback loop in the memory inbox.

7. **[Deterministic redaction and reduced Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)** — P2 · 4 comments
   Auto Memory sends transcript content to the model before redaction occurs, and service logs may leak skill content. Security-focused issue with clear privacy implications.

8. **[Shell command execution stuck with "Waiting input" after completion](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1 · 4 comments · 3 👍
   Simple CLI commands hang with an "Awaiting user input" status even after they finish. Three upvotes confirm this is a frequent pain point across workflows.

9. **[Browser agent fails on Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** — P1 · 4 comments · 1 👍
   The browser subagent terminates with a `GOAL` status on Wayland sessions, making GUI automation unusable for Linux users on that display server.

10. **[get-shit-done output hook causes crash](https://github.com/google-gemini/gemini-cli/issues/22186)** — P1 · 3 comments
    The `get-shit-done` output hook crashes Gemini CLI right before it prints the user-facing summary, cutting off the result at the most critical moment.

---

## 4. Key PR Progress

1. **[Cherry-pick 812f7a2 to v0.57.0-preview.1](https://github.com/google-gemini/gemini-cli/pull/29024)** — Closed
   Automated patch release carrying the A2A server cancellation fix and safety checker declaration into the preview track.

2. **[fix(a2a-server): clear stale cancellation error on new message turns](https://github.com/google-gemini/gemini-cli/pull/28940)** — Closed
   Resolves the root cause of the `Execution aborted` crash after a cancelled request, restoring A2A server reliability for subsequent prompts.

3. **[fix(core): declare top-level safety checkers in write policy configuration](https://github.com/google-gemini/gemini-cli/pull/28961)** — Closed
   Realigns `write.toml` safety checker definitions to standard top-level `[[safety_checker]]` arrays, ensuring `AllowedPathChecker` registers correctly for `write_file` and `replace`.

4. **[fix(core): keep GIT_CONFIG_* environment triplets internally consistent](https://github.com/google-gemini/gemini-cli/pull/28938)** — Open
   Prevents Git from receiving unparsable incomplete key/value pairs when redaction strips one half of a `GIT_CONFIG_*` triplet; also blocks `ShellExecutionService` from restoring sanitized values.

5. **[fix(core): inject on-retry nudge into conversation contents](https://github.com/google-gemini/gemini-cli/pull/28914)** — Open
   Moves the retry nudge from `systemInstruction` to the end of the `contents` array, preserving static prompt prefix caching while ensuring the model sees the recovery hint before generating.

6. **[fix(core): avoid persisting interrupted response placeholder](https://github.com/google-gemini/gemini-cli/pull/28939)** — Open
   Stops Gemini CLI from writing the synthetic `[The previous response was interrupted before it completed.]` text into conversation history after a tool-response turn is aborted.

7. **[fix(history): rollback and retry nudge optimizations](https://github.com/google-gemini/gemini-cli/pull/28934)** — Closed
   Optimizes tool-call cancellation and retry nudges to prevent context-window bloat, reduce API request volume, and maximize prefix-cache hit rates on retries.

8. **[fix(extensions): prompt for consent on environment changes](https://github.com/google-gemini/gemini-cli/pull/28863)** — Open
   Closes a consent-bypass gap where extension updates could inject unauthorized environment variables into MCP server processes; now includes MCP env configs in consent strings and sanitizes runtime-altering vars.

9. **[feat(evals): add reviewable eval drafts from session logs](https://github.com/google-gemini/gemini-cli/pull/29019)** — Open
   Introduces `eval:from-log`, allowing contributors to convert real session transcripts—complete with tool usage and failure scenarios—into starting points for behavioral evaluations.

10. **[fix(core): dedupe symlinked/junctioned skill directories during discovery](https://github.com/google-gemini/gemini-cli/pull/29017)** — Open
    Fixes [#28944](https://github.com/google-gemini/gemini-cli/issues/28944) by deduplicating skills that resolve through Windows junctions or POSIX symlinks, preventing duplicate skill registration.

---

## 5. Feature Request Trends

- **Subagent reliability and observability** — Recurring demands for better subagent recovery, trajectory visibility via `/chat share` ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598)), and crash reporting that includes subagent context ([#21763](https://github.com/google-gemini/gemini-cli/issues/21763)).
- **AST-aware codebase tools** — Interest in surgical reads, precise method-bound extraction, and codebase mapping via AST tools (e.g., `tilth`, `glyph`) to reduce token waste ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)).
- **Token-efficient context management** — "Tactful extraction" for file reads ([#19561](https://github.com/google-gemini/gemini-cli/issues/19561)), persistent file-based task tracking to replace in-context `WriteToDo` ([#18836](https://github.com/google-gemini/gemini-cli/issues/18836)), and session-log-driven eval creation ([#29019](https://github.com/google-gemini/gemini-cli/pull/29019)).
- **Security and privacy hardening** — Deterministic redaction in Auto Memory ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)), quarantine of invalid memory patches ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and consent-aware extension env injection ([#28863](https://github.com/google-gemini/gemini-cli/pull/28863)).
- **Model self-awareness** — Users want the agent to accurately describe its own CLI flags, hotkeys, and self-execution mechanics ([#21432](https://github.com/google-gemini/gemini-cli/issues/21432)).

---

## 6. Developer Pain Points

- **Subagent instability dominates** — False success reports, hangs, and missed invocations are the most upvoted and commented issues. The gap between what the model *can* delegate and what it *actually* delegates effectively erodes trust in the agent workflow.
- **Shell execution gets stuck** — Commands that finish cleanly are reported as "Waiting input" ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), and interactive prompts (e.g., Vite scaffolding) cause indefinite hangs ([#22465](https://github.com/google-gemini/gemini-cli/issues/22465)). Both suggest the terminal I/O layer needs more robust state tracking.
- **Context bloat from retries and interruptions** — Synthetic placeholder text, un-rolled-back tool calls, and missing prefix-cache preservation all contribute to unnecessary token consumption and degraded performance.
- **Auto Memory quality loop** — Low-signal sessions are retried endlessly ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522)), invalid patches are silently skipped ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and redaction happens too late in the pipeline ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)).
- **Platform-specific breakage** — Wayland browser agent failures ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)) and symlinked skill directories ([#20079](https://github.com/google-gemini/gemini-cli/issues/20079), [#28944](https://github.com/google-gemini/gemini-cli/issues/28944)) point to incomplete cross-platform coverage.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-25

---

## 1. Today's Highlights

GitHub Copilot CLI v1.0.81-9 shipped with model data retention warnings surfaced directly in the `/model` picker, giving users clearer visibility into compliance posture. Community attention remains heavy on MCP OAuth reliability—three distinct Entra ID and Atlassian OAuth regressions were reported this week, and a long-standing tool-whitelist feature request continues to gather strong support (27 👍). Meanwhile, a new report flags that MCP tool deferral is silently disabled for all non-Anthropic models, inflating token costs dramatically.

---

## 2. Releases

**v1.0.81-9** ([github.com/github/copilot-cli/releases](https://github.com/github/copilot-cli))
- Shows model data retention warnings with links in the `/model` picker, improving transparency around enterprise data policies.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Response |
|---|-------|---------------|-------------------|
| [#1274](https://github.com/github/copilot-cli/issues/1274) | CLI constantly getting 400 errors for invalid request body | Affects ~95% of code-review attempts on diff files; unclear whether the bug is server-side validation or CLI request construction. | 27 comments · 11 👍 — highest engagement this cycle |
| [#1973](https://github.com/github/copilot-cli/issues/1973) | Tool whitelist for Interactive Mode | Interactive mode currently demands approval for every tool call, including read-only ops (grep, cat, find). No middle ground between `/allow-all` and manual approval. | 12 comments · **27 👍** — strongest consensus request |
| [#4490](https://github.com/github/copilot-cli/issues/4490) | Atlassian MCP OAuth broken in 1.0.80 (RFC 8414 §3.3 regression) | Regression from 1.0.78 → 1.0.80 breaks Atlassian MCP auth due to issuer-URL mismatch. Now closed, but signals a fragile OAuth path. | 5 comments · Closed |
| [#4224](https://github.com/github/copilot-cli/issues/4224) | OTel spans for subagent calls omit billing attributes | Subagent (task tool / custom agent) calls skip `github.copilot.nano_aiu` and `github.copilot.cost` in traces, causing external cost dashboards to undercount actual billing. | 3 comments · 1 👍 |
| [#4582](https://github.com/github/copilot-cli/issues/4582) | MCP OAuth authorize omits `scope` for Entra ID with static `oauthClientId` | Static-client-configured MCP servers behind Microsoft Entra ID fail with AADSTS900144 because the `scope` parameter is dropped from the authorize URL. | 2 comments |
| [#4421](https://github.com/github/copilot-cli/issues/4421) | MCP initialize handshake has fixed 60s budget with no retry | Hard-coded 60 s timeout means npx-launched stdio servers that time out are **never respawned** for the session lifetime. ~29% of npx sessions fail. | 2 comments |
| [#4566](https://github.com/github/copilot-cli/issues/4566) | Agent repeatedly acknowledges work without executing tool actions | On gpt-5.3-codex, the agent loops on acknowledgment without triggering actual tool calls, rendering sessions unproductive. | 2 comments · 1 👍 |
| [#4572](https://github.com/github/copilot-cli/issues/4572) | Background compaction can lose completed parallel GPT tool result | Long-context `gpt-5.6-sol` autopilot sessions crash after compaction with `400 No tool output found for function call`, even though the tool ran successfully. | 1 comment |
| [#4414](https://github.com/github/copilot-cli/issues/4414) | BYOK custom providers return local 403 before requests reach provider | Custom OpenAI/Anthropic-compatible providers get a local `Authorization error` on every inference; the request never leaves the CLI. `/login` does not help. | 1 comment · 2 👍 — closed |
| [#4588](https://github.com/github/copilot-cli/issues/4588) | MCP tool deferral disabled for all non-Anthropic models | Tool search is only active on Claude models; OpenAI, Gemini, Grok, and MAI ship **all** tool schemas every turn, inflating a one-word prompt to 21.6k input tokens vs. 47k on others. | New · 0 comments |

---

## 4. Key PR Progress

| # | Title | Author | Status |
|---|-------|--------|--------|
| [#4573](https://github.com/github/copilot-cli/pull/4573) | Rename README.md to README.mdmain | @phuongnam467 | Open |

> **Note:** Only one PR was opened in the last 24 hours. No merge activity to report this cycle.

---

## 5. Feature Request Trends

- **Granular tool-control in Interactive Mode** — The strongest recurring ask (Issue #1973, 27 👍). Users want a whitelist/safe-mode option so read-only tools can auto-approve while destructive actions still require consent.
- **Multi-turn `/ask` and `/fork` workflow improvements** — Two closed PRs (#4577, #4538) addressed multi-turn conversations in `/ask`, and two PRs (#4578, #4580) proposed a `copilot --fork` flag and terminal-aware forking. These signal demand for lighter-weight, parallel session workflows.
- **Token and cost transparency** — Requests to show raw token counts in the status line (#4589) and to fix subagent billing attribution (#4224) reflect growing operator need for spend visibility as agent complexity grows.
- **Multimodal input/output** — PDF upload support (#4583) and image-generation for developer assets like icons, favicons, and OG images (#4581) are fresh feature asks, indicating users want the CLI to match the broader multimodal capabilities of the underlying models.
- **MCP/OAuth hardening** — Multiple reports ( #4490, #4582, #4584, #4408) point to a pattern: OAuth flows for MCP servers (especially Entra ID and Atlassian) are fragile and inconsistently handled across versions.

---

## 6. Developer Pain Points

1. **MCP OAuth is the #1 reliability concern.** Four separate issues this cycle trace OAuth breakage across Atlassian, Microsoft Entra ID, and generic Enterprise-hosted MCP servers. The root causes range from missing `scope` parameters to issuer-URL mismatches, and fixes are not yet consolidated.
2. **Interactive Mode tool-approval friction.** The binary choice between approving every tool manually and using `/allow-all` is a recurring complaint. A fine-grained whitelist is the most-upvoted feature request.
3. **Model-agnostic token bloat from tool-schema explosion.** When tool deferral is disabled (as it is for all non-Anthropic models), every inference pays the full tool-schema cost, turning trivial prompts into 20k+ token requests.
4. **Windows-specific file-lock and plugin issues.** Stale `inuse.<pid>.lock` files after crashes (#3255), worktree archiving failures on Windows (#4593, os error 32), and VS Code holding plugin directories hostage during `copilot plugin update` (#4570) create a fragmented Windows experience.
5. **Subagent billing invisibility.** Custom agents and the `task` tool consume credits but do not emit billing attributes in OTel spans, making cost attribution unreliable for organizations tracking spend.
6. **Session lifecycle fragility on Windows.** Unclean exits leave lock files behind, blocking future session resumes—a persistent hygiene issue that surfaces frequently.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-25

## 1. Today's Highlights

Only one item saw activity in the last 24 hours: **PR #2595**, a fix for the `StrReplaceFile` command that prevents silent data corruption when editing non-UTF-8 files. No new releases or open issues were created, indicating a quiet day for the project.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

No new issues were updated in the last 24 hours.

## 4. Key PR Progress

- **[PR #2595](https://github.com/MoonshotAI/kimi-cli/pull/2595)** — `fix(StrReplaceFile): refuse to edit files that are not valid UTF-8`
  - **Status:** Open | **Author:** @shoemoney | **Updated:** 2026-08-24
  - Resolves **#2591**. The `StrReplaceFile` command currently decodes entire files with `errors="replace"`, then writes the full string back. This means any invalid UTF-8 byte in the file — even far from the edit location — is silently replaced with the Unicode replacement character (U+FFFD). The PR refuses to process non-UTF-8 files outright, preventing unintended data loss or corruption. This is a correctness and safety fix that matters for developers working with binary, legacy, or mixed-encoding files.

## 5. Feature Request Trends

Based on the available data, no new feature requests were opened in the last 24 hours. The linked issue **#2591** (tied to the above PR) reflects an ongoing concern around **robustness of file operations**, particularly around encoding handling and data safety.

## 6. Developer Pain Points

- **Non-UTF-8 file corruption via `StrReplaceFile`:** The most prominent pain point is the silent loss of data when editing files containing bytes outside the valid UTF-8 range. Developers working with mixed or legacy encodings risk corruption without any warning, which is a significant reliability concern for a CLI tool that operates at file-system level.
- **Lack of encoding-aware safeguards:** The broader implication is that the tool currently lacks robust pre-flight checks for file encoding before performing edits, suggesting a general gap in safety guarantees around file I/O operations.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-25

## 1. Today's Highlights

OpenCode v1.18.22 landed with targeted bugfixes for device login flows and provider compatibility. The community is buzzing around a major persistent terminal workspace effort from jlongster, while a regression in the TUI's "Modified Files" sidebar since v1.16.0 continues to generate friction across multiple linked issues.

---

## 2. Releases

**v1.18.22** — Bugfix release focusing on three areas:
- Removed outdated Go first-month discount messaging and pricing copy.
- Fixed device login link resolution when servers return relative verification URLs or operate behind a base path.
- Stopped sending `textVerbosity` to OpenAI-compatible providers that do not support the field.

---

## 3. Hot Issues

| # | Title | Reactivity | Why It Matters |
|---|-------|-----------|----------------|
| [#4489](https://github.com/anomalyco/opencode/issues/4489) | Ephemeral one-off sessions for `opencode run` | 15 👍 · 14 comments · **Closed** | Strong community demand for transient sessions that bypass the persistent store—key for CI/CD and quick tasks. Author volunteered to implement. |
| [#30877](https://github.com/anomalyco/opencode/issues/30877) | TUI sidebar "Modified Files" hidden after path truncation fix | 14 👍 · 11 comments · Open | A regression from a path-truncation patch that silently hides the entire Modified Files panel, leaving users unaware of uncommitted changes. |
| [#37823](https://github.com/anomalyco/opencode/issues/37823) | GitHub Action fails on repos created after 2026-07-15 | 11 👍 · 6 comments · **Closed** | GitHub's immutable OIDC `sub` format change broke OpenCode's action parser (`p.rest` error). Critical for anyone automating with OpenCode in newer repos. |
| [#43619](https://github.com/anomalyco/opencode/issues/43619) | subagent: required `sessionID` blocks spawning first child | 10 comments · **Closed** | Documentation says to omit `sessionID` for a new child session, but the schema requires it—blocking all first-child delegation workflows in V2. |
| [#6310](https://github.com/anomalyco/opencode/issues/6310) | Sessions become unusable due to large LSP diagnostics | 9 comments · **Closed** | Edit/write tools store full LSP diagnostic payloads in session metadata; Lua LSP (and likely others) return workspace-wide diagnostics that balloon session size to a crawl. |
| [#44300](https://github.com/anomalyco/opencode/issues/44300) | Zen API `ox-alpha-free` fails when requests include tools | 7 comments · Open | Any chat completion sent to the Ox Alpha free model with a `tools` array returns "Endpoint is unavailable"—a blocking bug for tool-using workflows on the free tier. |
| [#17797](https://github.com/anomalyco/opencode/issues/17797) | TUI: Modified files no longer shown | 6 comments · Open | Older report of the same "Modified Files" regression, confirming the issue predates the v1.16 path-truncation fix and may have multiple roots. |
| [#32852](https://github.com/anomalyco/opencode/issues/32852) | TUI sidebar "Modified Files" does not show session diffs | 3 👍 · 5 comments · Open | Files are modified on disk but the sidebar shows zero diffs—users can't verify what OpenCode changed during a session. |
| [#38986](https://github.com/anomalyco/opencode/issues/38986) | SIGILL crash on AMD Ryzen Zen 3 (no AVX-512) | 2 comments · Open | The packaged binary contains AVX-512 instructions incompatible with Zen 3, causing an immediate crash on every session start. |
| [#39632](https://github.com/anomalyco/opencode/issues/39632) | IME composition breaks on first keystroke in v2 prompt | 2 👍 · 2 comments · Open | Chinese/Japanese/Korean input fails on the first character in the V2 prompt field—the character commits as literal text instead of entering composition mode. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#44683](https://github.com/anomalyco/opencode/pull/44683) | queue and steer follow-up prompts | Open | Implements the Figma-designed queue/steer workflow for running sessions, with a durable inbox operation for correct reordering. Ctrl/Cmd+Enter uses the selected behavior. |
| [#28067](https://github.com/anomalyco/opencode/pull/28067) | reconcile compaction summary with preserved tail | **Closed** | Fixes stale work appearing under "Next Move" after repeated compaction cycles (closes #38530). |
| [#44840](https://github.com/anomalyco/opencode/pull/44840) | materialize mentioned skills on prompts | Open | Makes `@skill-id` selections deterministic by resolving and injecting skill instructions onto the owning prompt at materialization time. |
| [#44838](https://github.com/anomalyco/opencode/pull/44838) | add experimental desktop browser | Open | Consolidates prior browser PRs (#39270, #39277, #39278) into a single on-demand, opt-out Desktop browser with a public Node host SDK. |
| [#42654](https://github.com/anomalyco/opencode/pull/42654) | add persistent terminal panes | **Closed** | Adds persistent PTY backend, ordered group schemas, and a bridge to the `opencode-pty` sidecar with stale-registration recovery. |
| [#44837](https://github.com/anomalyco/opencode/pull/44837) | refine persistent terminal panes | Open | Refines terminal pane layout, headers, focus ownership, render timing, live foreground-process labels, and keybindings. |
| [#44836](https://github.com/anomalyco/opencode/pull/44836) | add persistent terminal workspaces | Open | Renders persistent embedded terminals beside

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-25

## 1. Today's Highlights

Pi **v0.84.3** shipped with a new optional native PowerShell tool for Windows and safer atomic managed updates. The most urgent engineering focus is a trio of fixes landing in parallel: stalled provider streams now terminate via idle timeout, per-model compaction profiles allow tuning across different context windows, and Gemini 3.x `thought_signature` round-tripping is restored through OpenAI-compatible endpoints.

## 2. Releases

### v0.84.3 — [GitHub](https://github.com/earendil-works/pi/releases/tag/v0.84.3)
- **PowerShell tool** — Optional native PowerShell command execution on Windows, with dedicated docs at [Windows docs](https://github.com/earendil-works/pi/blob/v0.84.3/packages/coding-agent/docs/windows.md#powershell-tool).
- **Safer managed updates** — New stage → verify → atomic-activate update path.

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#7547](https://github.com/earendil-works/pi/issues/7547) | How do you use Pi on Windows? | 44 comments — the community flagged fragmented Windows support paths and asked for clearer focus on first-class UX. | 🔥 44 comments, 2 👍 |
| [#6879](https://github.com/earendil-works/pi/issues/6879) | Auto-compaction never triggers after context grows past 100% | Compaction stayed dormant until the API rejected a 373k-token request. High-impact bug for long agentic turns. | 22 comments, 19 👍 |
| [#6922](https://github.com/earendil-works/pi/issues/6922) | Default model cannot be a llama.cpp model | Startup showed "No models available" and exited when `defaultProvider` was set to `llama.cpp`. Now closed. | 11 comments, 14 👍 |
| [#8167](https://github.com/earendil-works/pi/issues/8167) | Cannot pick a model with built-in llama.cpp support | llama-server router-mode models appeared via `/llama` but were invisible in the model picker. Now closed. | 11 comments |
| [#7444](https://github.com/earendil-works/pi/issues/7444) | WebSocket retry only handles two error codes | Any `response.failed` error outside the two special-cased codes hard-stopped the turn. Now closed. | 9 comments |
| [#7048](https://github.com/earendil-works/pi/issues/7048) | Compaction summary can persist truncated mid-word | `stopReason === "length"` was not checked, causing corrupted last-read summaries. Now closed. | 7 comments, 1 👍 |
| [#8166](https://github.com/earendil-works/pi/issues/8166) | Custom message injected mid-tool-batch breaks tool_calls→tool adjacency | Extensions calling `sendMessage({ triggerTurn: false })` corrupt tool-message ordering on DeepSeek 400. Open. | 7 comments |
| [#6996](https://github.com/earendil-works/pi/issues/6996) | Gemini 3.x models fail during tool use — missing `thought_signature` | Streamed function-call chunks dropped the Google `thought_signature` field, breaking subsequent tool results. Open. | 6 comments |
| [#8331](https://github.com/earendil-works/pi/issues/8331) | Agent loop hangs forever when a provider stream stalls | SSE streams that stopped delivering events but never closed caused the `for await` in `streamAssistantResponse` to hang indefinitely. Open. | 3 comments |
| [#8133](https://github.com/earendil-works/pi/issues/8133) | Per-model compaction settings | Requested a `compaction.profiles` map keyed by model ID so large-context and small-context models coexist without one-size-fits-all tuning. Open. | 4 comments, 3 👍 |

## 4. Key PR Progress

| # | Title | Author | Status |
|---|-------|--------|--------|
| [#8593](https://github.com/earendil-works/pi/pull/8593) | Fix: end stalled provider streams via idle timeout | nitishagar | ✅ Closed — resolves [#8331](https://github.com/earendil-works/pi/issues/8331) |
| [#8592](https://github.com/earendil-works/pi/pull/8592) | Feat: add per-model compaction profiles | nitishagar | ✅ Closed — resolves [#8133](https://github.com/earendil-works/pi/issues/8133) |
| [#8590](https://github.com/earendil-works/pi/pull/8590) | Fix: round-trip Gemini `thought_signature` via openai-completions | nitishagar | ✅ Closed — resolves [#6996](https://github.com/earendil-works/pi/issues/6996) |
| [#8585](https://github.com/earendil-works/pi/pull/8585) | Fix: abort OpenAI streams immediately when signal fires | danscofield | ✅ Closed — mirrors Anthropic's signal-check pattern for OpenAI paths |
| [#8578](https://github.com/earendil-works/pi/pull/8578) | Fix: pin `createProvider` TApi for xAI Responses provider | c0n419 | ✅ Closed — fixes TS build break after [#8124](https://github.com/earendil-works/pi/pull/8124) |
| [#8575](https://github.com/earendil-works/pi/pull/8575) | Fix: surface + bound torn-append replay loss in session JSONL | simonckemper | ✅ Closed — prevents silent double-entry loss on malformed JSONL lines |
| [#8570](https://github.com/earendil-works/pi/pull/8570) | Fix: preserve Codex thread affinity headers | valkyriweb | ✅ Closed — adds missing `thread-id` header to Codex Responses requests |
| [#8479](https://github.com/earendil-works/pi/pull/8479) | Fix: expose unloaded llama.cpp presets | KaelWD | ✅ Closed — resolves [#8167](https://github.com/earendil-works/pi/issues/8167) for router-mode `--models-preset` |
| [#8580](https://github.com/earendil-works/pi/pull/8580) | Feat: drop extra vertical padding on tool rows | vincelwt | ✅ Closed — removes 2–3 empty lines per tool call in transcripts |
| [#8512](https://github.com/earendil-works/pi/pull/8512) | Feat: add optional PowerShell tool | mitsuhiko | ✅ Closed — landed in v0.84.3, addresses Windows path-handling pain |

**Open PRs to watch:**
- [#8573](https://github.com/earendil-works/pi/pull/8573) — Bedrock Mantle Anthropic Messages support
- [#8559](https://github.com/earendil-works/pi/pull/8559) — Attach clipboard images as atomic markers
- [#8547](https://github.com/earendil-works/pi/pull/8547) — Move editor cursor on click
- [#8552](https://github.com/earendil-works/pi/pull/8552) — Keep skills available with bash-only tools

## 5. Feature Request Trends

1. **Provider expansion** — Repeated requests to add SiliconFlow, Merge Gateway, Eden AI, Parasail.io, and Amazon Bedrock Mantle as first-class providers. The community wants broader model access through OpenAI-compatible gateways.
2. **Per-model configuration** — The compaction-profiles request (#8133) reflects a broader desire to tune behavior (compaction, tools, providers) at the model level rather than globally.
3. **Windows parity** — The PowerShell tool (now shipped) and ongoing Windows issues (#7547) signal strong demand for a polished, first-class Windows experience rather than best-effort WSL/Bash compatibility.
4. **Portable agent configs** — `pi preset` for export/import of named agent configurations (#8588) would let users share and version-control agent setups.
5. **Session portability** — Moving a running session into a new working directory or git worktree (#8554) for automated/AFK agents.

## 6. Developer Pain Points

- **Stalled/aborted streams** — Two independent bugs (hanging SSE streams [#8331](https://github.com/earendil-works/pi/issues/8331) and OpenAI abort-signal gaps [#8585](https://github.com/earendil-works/pi/pull/8585)) showed that stream lifecycle management was inconsistent across providers. Both are now addressed.
- **Compaction tuning is one-size-fits-all** — Long sessions switching between 200K and 1M-context models (or using providers with aggressive context growth) hit compaction gaps. Per-model profiles are the fix.
- **Windows tooling fragmentation** — Multiple paths (WSL, Git Bash, PowerShell 5.1 vs 7) create confusion. The new optional PowerShell tool and the resolved `pwsh`-fallback issue (#8582) are steps forward, but #7547 shows the community still wants clearer guidance.
- **llama.cpp model discovery** — Models loaded via `llama-server` in router mode were invisible to the model picker (#8167) and the default-provider path errored on startup (#6922). Both are now closed; users should verify their config on v0.84.3.
- **JSONL session corruption** — Torn-append entries in session files silently doubled as replay losses (#8575), making debugging hard. The fix surfaces and bounds the issue.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-25

---

## 1. Today's Highlights

Qwen Code v0.22.0-nightly was released with key web-shell and desktop enhancements, including proper session workspace CWD handling and improved session organization synchronization. The community is actively engaged with 12+ open issues spanning MCP reconnection bugs, stream-activity timeouts, and architecture-level refactor proposals, while a strong wave of PRs targets TUI performance, review workflows, and multi-platform channel support.

---

## 2. Releases

### v0.22.0-nightly.20260825.22bb5e8b9f
**[GitHub](https://github.com/QwenLM/qwen-code/releases/tag/v0.22.0-nightly.20260825.22bb5e8b9f)**

- **Web-shell fix (PR #9730):** Passes session workspace cwd when opening shell from overview panel, resolving path-context errors in multi-workspace setups.
- **cua-driver-rs v0.20.0:** Updated Qwen Computer Use Agent driver with prebuilt binaries for macOS (codesigned + notarized universal), Linux (glibc 2.31+), and Windows (x86_64 + arm64), published under `packages/cua-driver`.

---

## 3. Hot Issues

### #5975 — API stream timeout after 19 chunks (12 comments, 👍 1)
**[Link](https://github.com/QwenLM/qwen-code/issues/5975)**
Users report frequent `No stream activity for 120000ms` errors after upgrading to v0.19.3, where the model enters a silent "Thought for 2s" state without output. This is a high-impact reliability issue affecting core conversational flow. Community reaction indicates it disrupts development workflows and remains unresolved since June 2026.

---

### #4063 — Core + CLI architecture review: 12 structural issues (9 comments, 👍 1)
**[Link](https://github.com/QwenLM/qwen-code/issues/4063)**
A deep audit flagged that 136 files directly import `@google/genai` types into the `ContentGenerator` interface, creating a dangerous coupling. Ranked P0, this architectural debt is viewed as critical for long-term maintainability. The community is awaiting discussion on remediation priorities and scope.

---

### #9944 — MCP reconnect reports success but tools remain unavailable (4 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/9944)**
After restarting an HTTP-transport MCP server, `qwen mcp reconnect --all` incorrectly reports success while tools return `"Tool not found"`. This is a critical reliability gap in MCP session management, especially for services like Zoteus that regenerate session IDs on restart. High relevance for production users relying on MCP integrations.

---

### #9005 — Anthropic wire missing stream-safety protections (4 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/9005)**
The Anthropic content generator lacks stream-safety guards present in the OpenAI wire, creating an inconsistent and fragile content-generation path. Pinned for review on `origin/main`, this is a structural parity issue affecting reliability when using Anthropic models.

---

### #8662 — Migrate TUI from ink to OpenTUI (4 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/8662)**
The current ink 7 + React 19 TUI with ~1037 lines of patches suffers from flicker, rendering bugs, and hard-to-fix structural limitations. This enhancement proposes a full migration to OpenTUI for flicker-free rendering and first-class mouse support. The community recognizes this as a necessary but non-trivial architectural investment.

---

### #9942 — Hide skill commands from top-level slash completion (4 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/9942)**
With many skills installed, typing `/` floods the completion menu, burying built-in commands. Users request skill commands be hidden from top-level slash completion to improve discoverability and reduce visual noise. A pragmatic UX improvement with broad appeal.

---

### #9927 — Artifact updatedAt stays stale on content changes (4 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/9927)**
Session artifact `updatedAt` only updates on registration-field changes (title, URL, size), not on content rewrites. This stale timestamp misleads users about the actual modification time of artifacts like workspace HTML files, creating confusion in session management and audit trails.

---

### #9905 — VP mode renders one row over budget, triggering full repaint (2 comments)
**[Link](https://github.com/QwenLM/qwen-code/issues/9966)**
In virtual-viewport mode, the "Press ctrl-s to show more" hint renders outside the allocated height budget, causing Ink to trigger a full terminal repaint. This is a subtle but performance-impacting rendering bug in the default UI mode.

---

### #9510 — Team shutdown requests overload message channel (3 comments, CLOSED)
**[Link](https://github.com/QwenLM/qwen-code/issues/9510)**
Teammates in extended Agent Team sessions had ordinary reports rejected with `"Only the team leader can request shutdowns"`. The bug confused report messages with shutdown requests, indicating a flaw in the multiplexed session message router. Now closed, but highlights multi-agent channel handling gaps.

---

### #9378 — Recall/forget scan-cap asymmetry (3 comments, CLOSED)
**[Link](https://github.com/QwenLM/qwen-code/issues/9378)**
After #8716 switched recall to uncapped `scanAll` variants, the forget/extraction path still uses capped scan functions. Documents beyond the 200-doc cap can be recalled but never forgotten, creating a memory-leak-adjacent bug in the auto-memory system. Closed but reveals a consistency issue in memory management.

---

## 4. Key PR Progress

### #9970 — Reduce TUI render overhead (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9970)**
By @DragonnZhang. Enables incremental terminal output in VP mode and isolates history rendering behind a memoized state slice. Focused regression tests ensure no visual regressions. This directly addresses performance concerns raised in issues #8662 and #9966.

---

### #9740 — Step 4 verification execution-grade for /review (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9740)**
By @wenshao. Adds execution-grade evidence forms to the `/review` skill, including a new `qwen review ab-drive` subcommand that runs scripts against two trees (PR worktree vs. base-tree) and reports paired captures. Strengthens review reliability with concrete, runnable evidence.

---

### #9723 — Run reviewed repo commands behind a container (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9723)**
By @wenshao. A review executes the code it reviews; this PR moves that execution behind a container boundary, making it a configurable policy rather than an environment-dependent property. Addresses security and consistency concerns in review workflows.

---

### #9394 — DingTalk Workspace channel (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9394)**
By @qqqys. Adds a built-in DingTalk Workspace channel supporting DMs, @mentions, ambient groups, document-mention notifications, native todo changes, source-scoped sessions, and final replies. Extends Qwen Code's multi-channel messaging to the Chinese enterprise ecosystem.

---

### #9844 — Restore telemetry aggregate on session swap failure (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9844)**
By @yiliang114. Fixes a bug where a failed `/resume` or `/branch` after `GeminiClient.initialize()` leaves replayed telemetry in the process-wide usage aggregate, causing double-counting on rollback. Critical for accurate telemetry in session-management workflows.

---

### #9871 — Neutralize legacy ##[ commands in autofix stdout (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9871)**
By @wenshao. Extends workflow-command neutralization to defuse both modern `::name::` and legacy `##[name]` syntaxes when autofix echoes reviewer content into job logs. Prevents accidental GitHub Actions workflow command injection.

---

### #8927 — Bound session lifetime with sessionRotation (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/8927)**
Adds a per-channel `sessionRotation` option with `maxTurns` and `maxAge` bounds. When a session exceeds its bound, the next message starts a fresh session instead of reusing it. Addresses context bloat and session-management concerns raised in #9510.

---

### #9969 — Accept contained symlinks in older-Git archive fallback (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9969)**
By @harjothkhara. The GitHub extension archive fallback (for Git < 2.37) previously rejected all tar link entries. Now accepts symbolic links whose targets provably resolve inside the archive, improving extension install compatibility on older Git versions.

---

### #9492 — Loop detection result-aware for task_list polls (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9492)**
By @yiliang114. Makes loop-detection guards result-aware for stateful read tools like `task_list`, where identical arguments may yield different results due to shared-state mutations by other teammates. Prevents false-positive loop detection in multi-agent scenarios.

---

### #9962 — Recover restarted HTTP MCP servers (OPEN)
**[Link](https://github.com/QwenLM/qwen-code/pull/9962)**
By @yiliang114. Fixes the root cause of issue #9944: four stacked defects in the MCP reconnection path now allow in-session and CLI recovery of HTTP MCP servers that restarted with a new `mcp-session-id`. Tool calls that previously failed now repair the connection automatically.

---

## 5. Feature Request Trends

1. **Multi-channel messaging expansion:** DingTalk (#9394, #9922) and existing bot integrations show strong demand for enterprise messaging channels with rich features (rich-text, multi-image, todo sync, source-scoped sessions).

2. **TUI/viewport rendering improvements:** Multiple issues and PRs (#8662, #9970, #9966, #9305) converge on a need for flicker-free, performant, first-class mouse support in the terminal UI, suggesting the current ink-based renderer is reaching its limits.

3. **MCP reliability and reconnection:** The #9944/#9962 pairing highlights community demand for robust MCP session management, especially for HTTP-transport servers that regenerate session IDs.

4. **Session and memory lifecycle management:** Features around session rotation (#8927), artifact timestamp accuracy (#9927), and memory recall/forget symmetry (#9378) indicate users want finer-grained control over session state and memory scoping.

5. **Review workflow automation:** PRs #9740, #9723, #8943, #9761 show a clear trend toward making `/review` more execution-grade, containerized, and tooling-recoverable—moving from static analysis to verified, runnable evidence.

---

## 6. Developer Pain Points

- **Stream timeout reliability:** The #5975 issue (12 comments, unresolved since June) reflects a persistent pain point where models enter silent "thought" states and trigger 120s stream timeouts, disrupting interactive workflows.

- **MCP reconnection fragility:** The #9944 bug—reconnect reporting success while tools remain broken—highlights a gap in error reporting and session-state reconciliation that frustrates users relying on MCP tools.

- **Architecture coupling to @google/genai:** Issue #4063 identifies 136 files directly importing Google GenAI types into core interfaces, creating maintainability risk and vendor lock-in that developers find difficult to untangle.

- **TUI rendering performance and flicker:** Issues #8662, #9966, and the ongoing VP-mode bugs (#9305) indicate developers are experiencing visual glitches, unnecessary full repaints, and rendering overhead that degrade the interactive experience.

- **Session state inconsistencies:** Stale artifact timestamps (#9927), telemetry double-counting on failed session swaps (#9844), and loop-detection false positives in shared-state tools (#9492) point to broader challenges in keeping session state consistent across subagents, remotes, and memory systems.

- **Cross-platform path handling:** PR #9841 reveals Windows-specific daemon worktree guard issues where POSIX-style path parsing collides with backslash literal semantics, a recurring pain point for cross-platform CLI tooling.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-25

## 1. Today's Highlights

The v0.9.12 release cycle is in full integration mode, with the must-fix blocker set approaching code-complete on the `codex/v0912-integration` branch (72 commits, PR #5576). The most impactful merged changes this window include the goal-continuation cadence fix, the lifecycle-outbox / control-socket / `/relaunch` supervised-operation stack, and the 0.9.12 relay integration unifying managed Chat with native runtime threads. Meanwhile, the community surfaced a pair of fresh-install 404s for MiniMax and Xiaomi provider URLs, and flagged that turn-owned subagents can silently lose work when the parent turn ends.

## 2. Releases

No new releases in the last 24 hours. v0.9.12 remains in pre-release gating (version bump + changelog/RC gates pending per tracker [#5573](https://github.com/Hmbown/CodeWhale/issues/5573)).

## 3. Hot Issues

| # | Title | Status | Why It Matters |
|---|-------|--------|----------------|
| [#5588](https://github.com/Hmbown/CodeWhale/issues/5588) | Provider neutrality: 18 DeepSeek-exclusive gates | OPEN | Full audit of 2,281 lines across 279 files found 18 suspect gates where behavior is DeepSeek-gated but conceptually provider-neutral. The NVIDIA NIM env-leak gate is already fixed. Critical for multi-provider adoption. |
| [#5601](https://github.com/Hmbown/CodeWhale/issues/5601) | Fresh install 404 on MiniMax & Xiaomi setup | OPEN | New users hit built-in URL errors on first-run model configuration. DeepSeek itself works fine — suggests provider URL table is incomplete or stale. High visibility for onboarding. |
| [#5596](https://github.com/Hmbown/CodeWhale/issues/5596) | Turn end silently cancels turn-owned subagents | CLOSED | A long-running reviewer child can lose all work without warning when the parent model's turn completes, despite UI context implying continued background execution. Directly impacts autonomous workflow reliability. |
| [#5597](https://github.com/Hmbown/CodeWhale/issues/5597) | Detached agents lose post-turn usage from session costs | OPEN | Usage from detached `detached=true` children no longer flows back to session/turn cost projections after `TurnComplete`. Worker records still accumulate locally, causing cost visibility gaps. |
| [#5595](https://github.com/Hmbown/CodeWhale/issues/5595) | Read-only inspection children reject `git -C` at execute time | OPEN | A live reviewer spent ~347k tokens producing no findings because it could not run the canonical `git -C <workspace> log` command — classification and role gates passed, but the final execution envelope rejected it. |
| [#5589](https://github.com/Hmbown/CodeWhale/issues/5589) | Fleet config view: Enter loops, model switching buried | OPEN | Users report `/fleet` config Enter-key is a no-op loop and model switching is hard to discover. PR #5604 addresses the approved slice; broader UX cleanup still open. |
| [#5585](https://github.com/Hmbown/CodeWhale/issues/5585) | Test `setup_confirm_toast_names_…` SIGABRTs on stack overflow | OPEN | Pre-existing flaky crash on macOS nextest default stack, reproduced on both `main` and the 0.9.12 integration branch. Not introduced by the current cycle but needs resolution before release. |
| [#5571](https://github.com/Hmbown/CodeWhale/issues/5571) | Request-extension invariant: debug-assert prefix continuity | OPEN | Adds a debug-assert that request N's prefix extends request N-1's, preventing silent provider-cache kills. Part of ops IMPROVEMENT-PLAN-0912 C5. |
| [#5553](https://github.com/Hmbown/CodeWhale/issues/5553) | `/context`: attribute token cost to tool definitions & MCP servers | OPEN | Current context inspector estimates only system layers and Skills. Users need per-tool and per-MCP-server cost rows to trim expensive servers. PR #5603 addresses the display-only slice. |
| [#5586](https://github.com/Hmbown/CodeWhale/issues/5586) | Decompose mega files for v0.9.12 | OPEN | `lib.rs` (18.7k), `config.rs` (12.3k), `client.rs` (11.1k), `runtime_threads.rs` (9.3k) — all exceeding comfortable maintenance thresholds. Community has requested the cleanup lane. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5576](https://github.com/Hmbown/CodeWhale/pull/5576) | 0.9.12 integration: must-fix + UX fixes | OPEN | Main integration branch — 72 commits, gated and code-complete for release blockers. Awaiting version bump and changelog/RC gates. |
| [#5606](https://github.com/Hmbown/CodeWhale/pull/5606) | 0.9.12 relay integration: unify managed Chat with native runtime threads | CLOSED | Managed Chat now rides native runtime threads (turn_operation_idempotency), plus R2 approval fix, `doctor --fix` with consent, and accumulated standby improvements. |
| [#5535](https://github.com/Hmbown/CodeWhale/pull/5535) | Supervised operation stack | CLOSED | Five-commit seam: lifecycle outbox (`[lifecycle_outbox]` opt-in JSONL), `/relaunch`, per-session control socket, and goal-continuation quiet-period fix — enabling machine-readable supervision of long-lived sessions. |
| [#5591](https://github.com/Hmbown/CodeWhale/pull/5591) | Goal continuation cadence fix (part a) | CLOSED | Fixed `continuation_delay_seconds` being wired into only one of two dispatch paths; within-turn path previously had no wait, causing instant resume in CLI/resumed sessions. |
| [#5594](https://github.com/Hmbown/CodeWhale/pull/5594) | Control socket — part d (final) | OPEN | Opt-in Unix-only newline-framed JSON-RPC socket per session (`[control_socket] enabled = true`). Completes the supervised-operation control surface. |
| [#5593](https://github.com/Hmbown/CodeWhale/pull/5593) | `/relaunch` command — part c | OPEN | Self-relaunch after `/update` installs a new binary, so a session switches to the current binary in one step without manual restart. |
| [#5592](https://github.com/Hmbown/CodeWhale/pull/5592) | Lifecycle outbox — part b | OPEN | Opt-in `[lifecycle_outbox]` config emits one JSONL line per lifecycle event (`turn_start/end/stalled`, `subagent_spawn/complete`, `session_start/end`) for both interactive and headless runs. |
| [#5603](https://github.com/Hmbown/CodeWhale/pull/5603) | Show tool and MCP schema costs | OPEN | Context inspector now displays bounded schema-cost estimates from the last model tool catalog: catalog total, per-built-in-tool rows sorted by cost, and omitted-count summary for large catalogs. |
| [#5604](https://github.com/Hmbown/CodeWhale/pull/5604) | Fleet roster editing discoverability | OPEN | Makes member editing discoverable in Fleet roster: selected members show explicit `[edit]` affordance, footer advertises `m` for model switching, and pressing `m` opens the Fleet detail editor. |
| [#5584](https://github.com/Hmbown/CodeWhale/pull/5584) | Persist child approval receipts | OPEN | Child approval prompts now inherit the session approval receipt store; `Asked` is committed before exposing the prompt and terminal outcomes before closing the runtime, fixing durable evidence gaps. |

## 5. Feature Request Trends

- **Multi-provider neutrality** — Removing DeepSeek-specific gates (#5588) and fixing provider URL tables (#5601) reflects strong community demand for true vendor-agnostic operation.
- **Supervised/autonomous workflow reliability** — The stacked PRs around lifecycle outbox, control sockets, `/relaunch`, and goal-continuation cadence (#5535, #5594, #5593, #5592, #5591) show a clear push toward production-grade long-running session supervision.
- **Cost transparency** — `/context` token-cost attribution for tools and MCP servers (#5553, #5603) and the request-extension prefix invariant (#5571) indicate users want granular visibility into what consumes context window and credits.
- **Focused-block UX actions** — Per-block `y`/`Y` copy content/metadata, Enter fullscreen, `r` raw markdown (#5551) — users want richer in-transcript interactions without leaving the TUI.
- **Terminal polish** — OSC 12 cursor accent (#5554, #5599 merged) and dead-code sweep (#5587) reflect ongoing attention to TUI ergonomics and code hygiene.

## 6. Developer Pain Points

- **Subagent lifecycle fragility** — Two open issues (#5596, #5597) and a merged fix (#5591) in rapid succession show that turn-owned and detached subagents consistently lose state or usage data at turn boundaries. This is the hottest reliability gap.
- **Provider URL regressions on fresh install** — #5601 reveals that bundled provider URLs for MiniMax and Xiaomi are broken at first-run config time, blocking new users before they can evaluate the tool.
- **Mega-file maintenance burden** — #5586 and #5587 highlight that 10k+-line Rust files are actively hurting developer velocity; the community has explicitly requested decomposition.
- **Flaky tests under parallel load** — #5585 (stack overflow in toast test) and #5605 (remote_control test failing under full-suite parallel) indicate test stability is a concern as the suite grows.
- **Execution envelope mismatches** — #5595 shows a recurring pattern where classification/gate logic permits a command but the final execution layer rejects it, wasting tokens and confusing users.
- **Fleet config UX confusion** — #5589 (Enter-loop, buried model switching) and the targeted fix in #5604 suggest the Fleet configuration surface needs sustained redesign attention.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*