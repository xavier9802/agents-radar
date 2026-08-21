# AI CLI Tools Community Digest 2026-08-21

> Generated: 2026-08-21 01:43 UTC | Tools covered: 10

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
**Date: 2026-08-21**

---

## 1. Ecosystem Overview

The AI CLI tool landscape in mid-2026 is characterized by rapid feature iteration across major providers (Anthropic, OpenAI, Google, GitHub, Moonshot) alongside maturing open-source agents (OpenCode, Pi, Qwen). Development activity is bifurcating into two tracks: **agent orchestration reliability** (subagent recovery, cross-session messaging, daemon mode) and **platform parity** (Windows/Linux/Wayland bugs persist across nearly every tool). The most mature tools (Claude Code, Codex, Gemini CLI) are shipping nightly builds and dashboard interfaces, while smaller communities (Kimi, DeepSeek) are investing heavily in foundational architecture (crate decomposition, plugin security docs). Performance regressions—particularly CPU and memory bloat under multi-session loads—are a cross-tool concern, signaling that current agent architectures are struggling to scale.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Releases | Activity Level |
|------|-----------|----------|----------|---------------|
| **Claude Code** | 10 | 0 | v2.1.238 | Moderate — quality regressions dominating discussion |
| **OpenAI Codex** | 10 | 10 | v0.149.0, v0.150.0-alpha.1 | High — strong PR velocity, Windows/auth pain |
| **Gemini CLI** | 10 | 10 | v0.56.0-nightly | High — nightly cadence, subagent focus |
| **GitHub Copilot CLI** | 7 open / 6 closed | 1 | v1.0.81-6 | Low — bug-fix cycle, several issues recently closed |
| **Kimi Code CLI** | 1 | 1 | None | Low — early-stage, documentation-driven |
| **OpenCode** | 10 | 10 | v1.18.19 | High — performance critical, v2 beta in flight |
| **Pi** | 10 | 10 | None | Moderate — compatibility flags, Windows focus |
| **Qwen Code** | 10 | 10 | v0.21.15, 2 nightlies | High — review pipeline hardening, Aone Code push |
| **DeepSeek TUI** | 6 | 5 | v0.9.10 | Moderate — structural refactors, localization |
| **Grok Build** | 0 | 0 | None | Inactive — no community report |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|-----------|---------------|---------------|
| **Agent reliability & self-healing** | Gemini CLI, OpenCode, Claude Code | Subagent hang detection, graceful failure, recovery without manual intervention |
| **Cross-session / multi-session orchestration** | Claude Code, Qwen Code, OpenCode, Codex | Daemon mode, session persistence, inter-session messaging, `--resume --bg` semantics |
| **Context window & token management** | Pi, Gemini CLI, Qwen Code, OpenCode | Per-model compaction profiles, AST-aware reads, unbounded memory growth fixes, compression accuracy |
| **Windows platform parity** | Claude Code, Codex, Pi, OpenCode, Gemini CLI | File-lock leaks, auth regressions, TUI rendering bugs, path handling (`\\?\` prefix) |
| **MCP reliability** | Claude Code, Copilot CLI, Gemini CLI, OpenCode | Token bridging between desktop/CLI, OAuth issuer validation, stdio process leaks, silent failures |
| **Multi-account / identity management** | Claude Code, Copilot CLI, Pi | Mobile account switching, OAuth refresh token lifetime, enterprise policy enforcement parity |
| **Plugin / extension ecosystem security** | Kimi Code CLI, Gemini CLI, Copilot CLI | Subprocess isolation docs, consent-gated env injection, registry allowlists |
| **Local/edge model support** | OpenCode, Qwen Code, Pi | Cloudflare AI Gateway passthrough, Bedrock provider flags, per-provider reasoning controls |

---

## 4. Differentiation Analysis

| Dimension | Leaders | Differentiators |
|-----------|---------|----------------|
| **Target user** | | |
| Enterprise / institutional | Claude Code, Copilot CLI, Qwen Code | Policy enforcement, Aone Code integration, OAuth refresh concerns |
| Power users / researchers | Gemini CLI, Codex, OpenCode | Agent orchestration depth, Bedrock/Guardian support, eval frameworks |
| Casual / multi-account | Claude Code Mobile, Pi | Mobile account switching, slash-command alias familiarity |
| Chinese-language markets | Kimi Code CLI, DeepSeek TUI, Qwen Code | Localization efforts, Aone Code, WebShell reasoning controls for DeepSeek/GLM/Kimi |
| **Technical approach** | | |
| Rust-native | Codex, DeepSeek TUI (CodeWhale crate) | Structured refactors (FEAT-018 command shapes, tool-call stage extraction) |
| TypeScript/Node | Claude Code, Gemini CLI, Copilot CLI, OpenCode | Plugin marketplace, ACP protocol, MCP stdio bridge |
| Lua/Go hybrid | Qwen Code | Review pipeline with capture-tui, worktree-residue security |
| **Maturity signals** | | |
| Shipping dashboards | Codex (`codex agents`), OpenCode v2 beta | Interactive session management, subagent lifecycle UI |
| Nightly cadence | Gemini CLI, Qwen Code | Rapid iteration with `nightly` suffix builds |
| Architecture decomposition | DeepSeek TUI (CodeWhale) | Multi-EPIC crate reorganization as prerequisite work |
| Plugin security first | Kimi Code CLI | Proactive docs on subprocess isolation and credential handling |

---

## 5. Community Momentum & Maturity

**High momentum (rapid iteration, active PRs):**
- **Gemini CLI** — 10 PRs in one day covering context bloat, A2A state corruption, Git env safety, and sandbox hardening. The PR-to-issue ratio suggests a responsive maintainership model.
- **Qwen Code** — Aggressive review-pipeline hardening with 10 PRs; convergence advisories, machine-readable diagnostics, and Aone Code parity are all shipping in parallel.
- **OpenCode** — 10 PRs including a +88% SSE throughput improvement and memory leak fix; v2 beta is actively surfacing bugs that the community is helping resolve.
- **OpenAI Codex** — 10 PRs closed in one day (Guardian v2 fix, Bedrock multi-agent, macOS sandbox hardening) paired with a new `agents` dashboard release.

**Moderate momentum (steady but narrower focus):**
- **Claude Code** — No PRs this cycle; discussion dominated by model-quality regressions and mobile multi-account requests. Suggests a feature-complete but quality-degradation phase.
- **Pi** — 10 PRs focused on compatibility flags and slash-command aliases; strong Windows TUI fix cycle but no release this period.
- **DeepSeek TUI** — 5 PRs on structural refactors and localization; building foundational architecture before feature expansion.

**Lower momentum (early-stage or niche):**
- **Kimi Code CLI** — 1 issue, 1 PR. Plugin ecosystem is nascent; documentation-first approach.
- **Copilot CLI** — 1 PR, but 6 issues recently closed (auth/MCP fixes). Stabilization phase post-1.0 launch.
- **Grok Build** — No activity reported.

---

## 6. Trend Signals

| Signal | Evidence | Developer Implication |
|--------|----------|----------------------|
| **Agent orchestration is the new moat** | Subagent recovery (#22323 Gemini), cross-session messaging (#8724 Qwen), daemon mode (#88197 Claude), `agents` dashboard (Codex) | Tooling will differentiate on multi-agent reliability, not single-turn accuracy. Invest in session lifecycle management. |
| **Context management is breaking under load** | Unbounded memory (#2128 Qwen, #35107 OpenCode), compaction gaps (#6879 Pi), token firehosing (#22745 Gemini) | Default context-window strategies are insufficient. AST-aware tooling and per-turn compaction checks are becoming table stakes. |
| **Windows is the universal bug surface** | Auth regressions (Codex #39162/#39189), file locks (Claude #42776), TUI rendering (Pi #6300, #7547), path prefixes (Codex #39150) | Any tool targeting enterprise must prove Windows hygiene. `\\?\` path handling and service-account auth remain unresolved systemically. |
| **MCP integration is fragile across all tools** | Silent failures (Claude #61044, #88370), token bridging gaps (Copilot #4096), stdio leaks (Copilot #3698), array stringification (Claude #86459) | MCP is the universal plugin bus but lacks lifecycle guarantees. Expect tool-specific workarounds until a shared protocol standard emerges. |
| **Model quality regressions are eroding trust** | Repetitive rhetorical tics (Claude #77136, 316 👍), Opus 5 negotiation drift (#87491), false subagent success (#22323 Gemini) | Users are developing skepticism toward newer model releases. Tooling that surfaces quality metrics or allows model version pinning will retain power users. |
| **Localization is a competitive differentiator** | Chinese docs (DeepSeek #5482, Qwen Aone Code), dictionary-spine architecture (DeepSeek #5520) | Non-English user bases are large and underserved. Structured localization (not machine translation) is becoming a visible commitment. |
| **Performance regressions outpace feature shipping** | 97% CPU on render thread (OpenCode #42657), 5 GB RSS growth (OpenCode #35107), +88% throughput fix (OpenCode #42980) | Long-running multi-session workflows are the canary. Tools that profile and bound resource consumption will win enterprise adoption. |
| **Enterprise policy enforcement is inconsistent** | Bypass permissions in non-interactive mode (Copilot #4528), registry false-negatives (Copilot #3162), auto-update override (Claude #75607) | Governance tooling (allowlists, policy checks) is being bolted on retroactively. Expect parity gaps between interactive/non-interactive/sandbox modes to persist. |

---

*Report generated from community digest data covering 2026-08-20 → 2026-08-21 across 9 active AI CLI tool repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-21 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | PR | Skill / Topic | Functionality | Discussion Highlights | Status |
|---|-----|--------------|--------------|----------------------|--------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` — eval recall fix | Fixes `run_eval.py` reporting `recall=0%` across all skills, breaking the description-optimization loop | 10+ independent reproductions; blocks the entire skill-improvement pipeline | 🟡 Open |
| 2 | [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Comprehensive testing skill: Testing Trophy model, AAA pattern, React Testing Library, edge cases | Well-scoped, high demand for test-generation guidance | 🟡 Open |
| 3 | [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Broad ServiceNow platform skill covering ITSM, ITOM, Security, FSM, IntegrationHub | Enterprise-focused; latest activity Aug 12 | 🟡 Open |
| 4 | [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | Prevents orphan lines, widow paragraphs, numbering misalignment in AI-generated documents | Addresses a near-universal pain point in document output | 🟡 Open |
| 5 | [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills that evaluate skill quality across 5 dimensions and check for security issues | First community-built skill-audit tools; marks a shift toward quality-gating | 🟡 Open |
| 6 | [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` | Mechanical file verification + four-dimension reasoning quality gate for AI output before delivery | Extends the quality-gate concept from PR #83 into a pre-delivery pipeline | 🟡 Open |
| 7 | [#486](https://github.com/anthropics/skills/pull/486) | `odt` | OpenDocument text creation, template filling, and ODT→HTML conversion | Fills a gap for LibreOffice/ISO-standard document workflows | 🟡 Open |
| 8 | [#181](https://github.com/anthropics/skills/pull/181) | `SAP-RPT-1-OSS` predictor | Uses SAP's open-source tabular foundation model for predictive analytics on business data | Niche but high-value enterprise ML use case | 🟡 Open |

---

## 2. Community Demand Trends (from Issues)

- **Security & trust boundaries** — Issue [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍) exposes community skills impersonating the `anthropic/` namespace. The #1 community concern is preventing privilege escalation via untrusted skills.
- **Enterprise / org-wide sharing** — Issue [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) is the most upvoted open issue. Users want a shared skill library or direct-sharing links instead of manual `.skill` file distribution.
- **Skill evaluation tooling** — Issues [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍) and the self-audit PRs (#1367, #83) show strong demand for reliable skill-testing and quality-gating infrastructure.
- **Code review & testing** — The `testing-patterns` PR (#723) and Issue [#412](https://github.com/anthropics/skills/issues/412) (agent governance) indicate appetite for skills that embed best practices rather than just syntax.
- **Context efficiency** — Issue [#1487](https://github.com/anthropics/skills/issues/1487) flags the `claude-api` skill injecting ~156k tokens in a single tool call. The community wants skills that respect context budget.
- **MCP / agentic integration** — Issues [#16](https://github.com/anthropics/skills/issues/16) and [#29](https://github.com/anthropics/skills/issues/29) show ongoing interest in exposing skills as MCPs and supporting AWS Bedrock.

---

## 3. High-Potential Pending Skills

These PRs have active community engagement and address widely felt needs — strong candidates for merge:

| PR | Skill | Why It's Promising |
|----|-------|-------------------|
| [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Covers the full testing stack; fills a gap in the official collection |
| [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | Universal pain point; low-risk, high-impact |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` | Addresses the quality-gate demand from Issue #1385; complements PR #83 |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` | First meta-skill; enables community-driven skill evaluation |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Enterprise platform coverage is scarce; broad scope signals strong demand |
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval fix | Not a new skill, but unblocks the entire skill-improvement loop — high infra priority |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **skill-quality and trust infrastructure** — evaluation tooling, security validation, and context-efficient design — rather than a single vertical use case, reflecting a maturing ecosystem where builders care as much about *how skills are made and verified* as about *what skills do*.

---



# Claude Code Community Digest — 2026-08-21

---

## 1. Today's Highlights

Claude Code v2.1.238 shipped with a new `keybindingFlavor` setting for readline-style Ctrl+W behavior and updated plugin marketplace header handling. Community attention remains dominated by the highly-upvoted request for multi-account switching on mobile (#36151, 621 👍) and a growing chorus of model-quality concerns around repetitive rhetorical tics across Claude 4.7–5.0 and Fable (#77136, 316 👍).

---

## 2. Releases

**v2.1.238** — [GitHub](https://github.com/anthropics/claude-code)

- Added `keybindingFlavor` config option; set to `"readline"` for Bash-like Ctrl+W word-deletion in the prompt (default `"classic"` unchanged).
- Updated plugin marketplace `headersHelper` behavior on URL marketplaces and catalog entries.

> ⚠️ Regression reported: v2.1.238 causes interactive CLI-entrypoint sessions to persist thinking blocks as signature-only husks (`"thinking": ""`) — [Issue #88383](https://github.com/anthropics/claude-code/issues/88383).

---

## 3. Hot Issues

| # | Title | Author | Comments | 👍 | Link |
|---|-------|--------|----------|----|------|
| #36151 | Multi-account switching in Claude Mobile without shared email | CorneAussems | 161 | 621 | [Issue](https://github.com/anthropics/claude-code/issues/36151) |
| #42776 | Desktop fails to relaunch on Windows — orphaned process file lock | RonGamzu | 125 | 62 | [Issue](https://github.com/anthropics/claude-code/issues/42776) |
| #77136 | Claude 4.7–5.0 & Fable default to repetitive rhetorical tics | pbower | 50 | 316 | [Issue](https://github.com/anthropics/claude-code/issues/77136) |
| #86012 | Cross-session messages leave recipient unresponsive until idle-timeout kill | WarmBed | 31 | 6 | [Issue](https://github.com/anthropics/claude-code/issues/86012) |
| #25286 | CLI freezes with no input accepted — 100% write ratio in terminal renderer | davidpmclaughlin | 19 | 18 | [Issue](https://github.com/anthropics/claude-code/issues/25286) |
| #61044 | MCP tool calls in CCR Routines fail with "requires approval", no UI shown | beer89447-spec | 18 | 6 | [Issue](https://github.com/anthropics/claude-code/issues/61044) |
| #66153 | Tool-use markup rendered as `"court"` instead of `"antml:invoke"` | tshirado1 | 10 | 14 | [Issue](https://github.com/anthropics/claude-code/issues/66153) |
| #75607 | Server-side `x-cc-atis` experiment silently strips Opus 4.8 thinking summaries; CLI self-updates despite `autoUpdates: false` | phase3dev | 8 | 12 | [Issue](https://github.com/anthropics/claude-code/issues/75607) |
| #88370 | MCP Apps widgets stop rendering after staged server rollout of version negotiation (2.1.234) | liran-ws | 5 | 0 | [Issue](https://github.com/anthropics/claude-code/issues/88370) |
| #87491 | Opus 5 treats direct instructions as negotiations; injects self-referential content | ExploreAITogether | 4 | 1 | [Issue](https://github.com/anthropics/claude-code/issues/87491) |

**Why they matter:**

- **#36151** is the most-requested feature by a wide margin (621 👍), reflecting pain for users managing separate personal/professional Anthropic accounts on mobile.
- **#42776** affects Windows Desktop users who find the app permanently stuck after crashes or force-kills due to a lingering file lock.
- **#77136** signals a cross-model quality regression; the 316 👍 count shows strong community concern about prose quality despite explicit style prompts.
- **#86012** and **#61044** both expose MCP cross-session reliability issues that break collaborative agent workflows.
- **#25286** is a long-standing (Feb 2026) CLI hang bug with no known workaround other than `kill`.
- **#66153** and **#88370** are parsing/protocol-level bugs that cause silent tool failures, making debugging especially painful.
- **#75607** raises trust concerns: a server-side experiment silently overrode user-configured settings and auto-updated the CLI.

---

## 4. Key PR Progress

No pull requests were opened or updated in the last 24 hours.

---

## 5. Feature Request Trends

| Trend | Representative Issues |
|-------|----------------------|
| **Multi-account & identity management** | #36151 (mobile switching), #78037 (OAuth refresh token lifetime) |
| **Daemon / background session persistence** | #88197 (daemon mode with session resurrection), #86092 (`--resume --bg` session forking) |
| **Cross-session agent messaging** | #86012 (unresponsive recipient), #87870 (Linux vs Windows feature parity) |
| **Plugin & hook ergonomics** | #79143 (hookify prefix missing in docs), #88405 (symlinked rules not auto-loaded) |

The community is pushing hard for more robust agent orchestration (daemon mode, cross-session inbox parity across platforms) and better multi-account workflows, especially on mobile.

---

## 6. Developer Pain Points

- **MCP instability:** Three separate issues this week (#61044, #86459, #88370) report MCP tool calls failing silently, array parameters being stringified, and widgets disappearing after server rollouts. MCP integration remains a fragile surface.
- **Model quality regressions:** The repetitive-tic complaint (#77136, 316 👍) and Opus 5's negotiation-style responses (#87491) suggest emerging behavioral drift in newer model releases that users find disruptive to professional writing tasks.
- **Windows / MSIX packaging bugs:** File-lock leaks on relaunch (#42776), MSIX container-silo leaks on update (#87879), and Cowork VM handle leaks blocking launch (#87607) point to persistent Windows Desktop packaging hygiene issues.
- **Auth token lifetime:** OAuth refresh tokens expiring after ~24 hours (#78037) forces daily re-login, especially painful for Max-subscription single-user setups.
- **Silent setting overrides:** The `x-cc-atis` experiment stripping thinking summaries and auto-updating despite `autoUpdates: false` (#75607) eroded user trust in configuration integrity.
- **Session management quirks:** `--resume --bg` unexpectedly forks (#86092), and waking idle agent forks forfeits prompt-cache inheritance (#88412) — both break expected persistence semantics for power users.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-21

## 1. Today's Highlights

The Codex CLI shipped **v0.149.0** with a new interactive `codex agents` dashboard and working-directory management commands (`/cd`, `/pwd`, `/cwd`) for TUI sessions, while a follow-up alpha (`v0.150.0-alpha.1`) is already in flight. The community is flagging a cluster of **Windows auth and session bugs** across recent Desktop builds, and a long-standing feature request for **headless remote Linux support on mobile** continues to draw the strongest engagement.

---

## 2. Releases

**rust-v0.149.0** — [#39094](https://github.com/openai/codex/issues/39094), [#39112](https://github.com/openai/codex/issues/39112), [#39114](https://github.com/openai/codex/issues/39114), [#39142](https://github.com/openai/codex/issues/39142)

- New interactive `codex agents` dashboard: search, start, open, rename, and stop tasks with configurable shortcuts.
- Added `/cd`, `/pwd`, and `/cwd` commands for managing the working directory in TUI sessions.

**rust-v0.150.0-alpha.1** — [GitHub Release](https://github.com/openai/codex/releases)

- Next alpha iteration; no detailed notes published yet.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#39162](https://github.com/openai/codex/issues/39162) | macOS auth invalidation on existing conversation | 28 | 21 | **Critical auth regression** in 26.814 — opening any existing chat signs users out. Affects the latest production build. |
| [#23200](https://github.com/openai/codex/issues/23200) | Headless remote Linux support for mobile | 20 | 49 | **Highest-engagement open issue.** Users on always-on Linux servers need mobile control without a desktop host online. |
| [#28276](https://github.com/openai/codex/issues/28276) | Failed to archive conversation | 23 | 5 | Archiving silently fails with no explanatory error, blocking session hygiene. |
| [#33493](https://github.com/openai/codex/issues/33493) | Local compaction v2 retains unbounded `input_image` payloads | 19 | 4 | Long image-heavy threads enter infinite auto-compaction loops — a **token-cost and stability risk**. |
| [#39189](https://github.com/openai/codex/issues/39189) | Windows 26.814 signs out on thread open | 16 | 3 | mirrors the macOS auth bug on Windows; personal Pro accounts are invalidated after workspace-only settings 401. |
| [#35746](https://github.com/openai/codex/issues/35746) | Paginated history drops valid rollout records | 16 | 0 | Rollout history loses records and reuses ordinals — **data integrity concern** for CLI power users. |
| [#20930](https://github.com/openai/codex/issues/20930) | Remote connection notifications don't fire | 12 | 18 | Mobile + remote workflows are broken for completion awareness; widely felt by distributed teams. |
| [#31973](https://github.com/openai/codex/issues/31973) | Windows Remote Control stuck in "Reconnecting…" | 12 | 1 | QR-paired remote sessions on Windows have no recovery path once stuck — **session killer**. |
| [#39150](https://github.com/openai/codex/issues/39150) | Windows can't archive with `\\?\` paths | 12 | 2 | Extended-length path prefix causes generic archive failure; Windows-specific but common in enterprise. |
| [#34026](https://github.com/openai/codex/issues/34026) | Windows threads stuck "thinking" | 11 | 0 | Completed threads remain in a thinking state; new messages queue locally and never start a turn. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#39827](https://github.com/openai/codex/pull/39827) | Add history and notes tools for token-budget sessions | ✅ Closed | Enables token-budget sessions to recover prior context and preserve state across compaction transitions via direct-model `history` tools. |
| [#39825](https://github.com/openai/codex/pull/39825) | Use Responses compaction for Amazon Bedrock | ✅ Closed | Switches Bedrock remote compaction to `/v1/responses` items, removing the legacy dedicated compaction protocol. |
| [#39822](https://github.com/openai/codex/pull/39822) | Preserve uncapped Guardian classifier instructions | ✅ Closed | Fixes Guardian v2 silently truncating classifier instructions by applying an unintended implicit token limit. |
| [#39813](https://github.com/openai/codex/pull/39813) | Defer legacy filesystem policy projection | ✅ Closed | Avoids unnecessary session rebuilds by only projecting legacy filesystem policy on cwd changes that can trigger rebindings. |
| [#39812](https://github.com/openai/codex/pull/39812) | Avoid materializing writable-root carveouts for presence checks | ✅ Closed | Adds `has_writable_roots_with_cwd` helper to detect effective writable roots without constructing read-only carveouts — performance win. |
| [#39811](https://github.com/openai/codex/pull/39811) | Restrict macOS preference reads to full-disk policies | ✅ Closed | Prevents the macOS preferences service from exposing data outside a sandbox's allowed read roots — **security hardening**. |
| [#39809](https://github.com/openai/codex/pull/39809) | Preserve `WINDIR` in core Windows shell environments | ✅ Closed | Adds `WINDIR` to the Windows env-var allowlist; case-variant retention tested. |
| [#39804](https://github.com/openai/codex/pull/39804) | Use multi-agent V1 for Amazon Bedrock models | ✅ Closed | Bedrock models now advertise `MultiAgentVersion::V1` since V2 response items are unsupported. |
| [#39795](https://github.com/openai/codex/pull/39795) | Add hostname to configurable TUI status line | ✅ Closed | New selectable status-line item showing the normalized OS hostname without triggering DNS resolution. |
| [#39786](https://github.com/openai/codex/pull/39786) | Support host-accepted exec-server WebSockets | ✅ Closed | Embedding hosts can now construct a remote environment from an already-authenticated Axum WebSocket via `from_accepted_websocket`. |

---

## 5. Feature Request Trends

- **Mobile-first remote workflows** — The #23200 request (49 👍) and #20930 (18 👍) both highlight a growing need for mobile as a genuine control layer, not just a companion app.
- **Cost and rate-limit transparency** — #37674 (Bedrock cache-control) and #39808 (subagent fan-out overhead) show users are actively managing spend and hitting unexpected cost walls with agentic workflows.
- **Session resilience** — Multiple requests target compaction reliability (#33493), history fidelity (#35746), and token-budget context recovery (#39827).
- **Remote Linux / headless support** — Beyond mobile, power users want Codex to operate cleanly on headless servers without requiring a persistent desktop session.

---

## 6. Developer Pain Points

1. **Windows is the dominant bug surface.** At least 8 of the top 30 issues this cycle are Windows-specific, spanning auth (#39162, #39189), session management (#34026, #31973), archiving (#39150, #39627), and sandbox permission errors (#38425). The `\\?\` path prefix issue and the `\\?\`-related archive duplication (#39705) point to a deeper Windows path-handling problem.

2. **Auth regressions are recurring.** Both macOS (#39162) and Windows (#39189) report the same symptom — opening an existing conversation signs the user out — suggesting a shared auth-state bug in the Desktop layer around build 26.814.

3. **Compaction and context management are immature.** Unbounded image payloads in compaction (#33493), infinite auto-compaction loops, and the need for new history/notes tools for token-budget sessions (#39827) indicate the context-window strategy is still evolving.

4. **Remote-control reliability is fragile.** Notifications not firing (#20930), remote sessions getting stuck (#31973), and large-idle-task timeouts (#38023) make remote workflows feel unreliable for production use.

5. **Subagent cost model is unclear.** #39808 reveals that multi-agent fan-out carries a fixed per-agent context/tool overhead that can exceed single-agent costs — a pricing/optimization gap users are surfacing.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-21

## 1. Today's Highlights

A new nightly build (v0.56.0-nightly.20260821) landed with core fixes for symlink evaluation and shell execution service cleanup. The community is buzzing around agent reliability—subagent recovery, generalist hangs, and browser agent failures dominate the issue queue—while PRs target context window bloat, Git environment safety, and A2A server state corruption.

---

## 2. Releases

**v0.56.0-nightly.20260821.g30573d2e4** — [PR #28941](https://github.com/google-gemini/gemini-cli/pull/28941)

Key changes in this nightly:
- **Fixed symlink evaluation in ignore path handling** — `.geminiignore` and `.gitignore` rules now resolve consistently across symbolic links ([PR #28915](https://github.com/google-gemini/gemini-cli/pull/28915)).
- **Cleaned up `shellExecutionService`** — removed `eslint-disable` and unsafe type assertions, improving type safety ([PR #28862](https://github.com/google-gemini/gemini-cli/pull/28862), merged).

---

## 3. Hot Issues

1. **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 · 12 comments · 2 👍
   The `codebase_investigator` subagent falsely reports `status: "success"` with `Termination Reason: "GOAL"` even when it hit the max-turn limit without completing analysis. This masks failures and makes debugging misleading. High comment volume signals broad impact.

2. **[Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1 · 8 comments · 8 👍
   Simple tasks like folder creation cause the generalist agent to hang indefinitely. Workaround: disable sub-agents. Eight upvotes suggest this is a common pain point affecting daily workflows.

3. **[Leverage model's bash affinity via Zero-Dependency OS Sandboxing](https://github.com/google-gemini/gemini-cli/issues/19873)** — P2 · 8 comments
   Proposes using native POSIX tools (`grep`, `sed`, `awk`) within a sandboxed environment to align with how Gemini models are trained. Reflects community appetite for deeper shell integration with stronger isolation guarantees.

4. **[Robust component-level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** — P1 · 7 comments
   Tracks progress on the behavioral evals framework (76 tests generated across 6 supported Gemini versions). Critical for maintaining quality as the agent system grows in complexity.

5. **[Assess impact of AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — P2 · 7 comments
   EPIC investigating whether AST-aware tooling can reduce context noise and improve codebase navigation precision. Directly addresses the "token firehosing" problem users report with large file reads.

6. **[Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** — P2 · 6 comments
   Users report the agent ignores custom skills and sub-agents unless explicitly prompted. This undermines the extensibility model and is a frequent source of frustration for power users.

7. **[Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** — P2 · 5 comments
   Sessions marked as low-signal by the extraction agent remain unprocessed and get re-surfaced perpetually, creating noise in the memory inbox.

8. **[Shell command execution gets stuck with "Waiting input" after command completes](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1 · 4 comments · 3 👍
   Simple CLI commands that finish immediately still leave the shell in an "Awaiting user input" state. Three upvotes confirm this is a recurring bug, not an edge case.

9. **[browser subagent fails on Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** — P1 · 4 comments · 1 👍
   The browser agent terminates with `GOAL` on Wayland sessions, blocking Linux users who don't use X11. A platform compatibility gap that affects an growing user segment.

10. **[Gemini CLI encounters 400 error with > 128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** — P2 · 3 comments
    The agent hits a 400 error when more than 400 tools are available, suggesting the tool-scope limiting logic needs improvement. Relevant for users with large extension ecosystems.

---

## 4. Key PR Progress

1. **[history rollback and retry nudge optimizations](https://github.com/google-gemini/gemini-cli/pull/28934)** — DavidAPierce
   Rolls back synthetic tool-call entries on cancellation and optimizes retry nudges to reduce context window bloat and API request volume. Directly addresses token waste on interrupted turns.

2. **[fix(a2a-server): clear stale cancellation error on new message turns](https://github.com/google-gemini/gemini-cli/pull/28940)** — amelidev
   Resolves a state corruption bug where subsequent prompts after an abort crash with `Execution aborted`. Fixes a critical reliability issue for Google Cloud Assistant users.

3. **[fix(core): keep GIT_CONFIG_* environment triplets internally consistent](https://github.com/google-gemini/gemini-cli/pull/28938)** — Shivansh1980
   Fixes a regression where `sanitizeEnvironment()` emitted malformed `GIT_CONFIG_*` variables that caused **every** git invocation to fail. Reproduced against git 2.50.1.

4. **[fix(core): avoid persisting interrupted response placeholder](https://github.com/google-gemini/gemini-cli/pull/28939)** — Shivansh1980
   Stops the CLI from inserting a synthetic `[The previous response was interrupted...]` model response into history, which was being carried into subsequent turns and polluting context.

5. **[fix(sandbox): isolate Docker and container runtime in macOS Seatbelt](https://github.com/google-gemini/gemini-cli/pull/28935)** — josebalius
   Denies access to container daemon sockets, CLI binaries, and shared memory in macOS Seatbelt profiles, closing a sandbox escape vector via Docker Desktop VirtioFS mounts.

6. **[fix(extensions): prompt for consent on environment changes](https://github.com/google-gemini/gemini-cli/pull/28863)** — amelidev
   Extensions can no longer bypass consent checks to inject unauthorized env vars into MCP server processes. Runtime-altering variables are now sanitized.

7. **[feat(pr-generation): iterative orchestrator state machine](https://github.com/google-gemini/gemini-cli/pull/28933)** — joneba-google
   Implements the central orchestrator for the PR generator: multi-turn coding, evaluation sandbox isolation, ESLint static analysis, and trajectory logging.

8. **[feat(pr-generation): Antigravity agent runner and async stream](https://github.com/google-gemini/gemini-cli/pull/28932)** — joneba-google
   Adds async agent execution with turn timeouts and chunk export for GCS trajectory logging, enabling multi-turn coding agents in the PR generator pipeline.

9. **[feat(pr-generation): triage-eval schema-agnostic helpers](https://github.com/google-gemini/gemini-cli/pull/28937)** — joneba-google
   Introduces centralized quality/effort accessors supporting both legacy and unified schemas, preserving empty-string effort semantics for non-OK issues.

10. **[fix(core): drop unsafe `diff.external` override](https://github.com/google-gemini/gemini-cli/pull/28930)** — sharonyao1127
    Reverts an unsafe `diff.external` empty-string override from a prior PR that broke git diff operations inside the shell sandbox.

---

## 5. Feature Request Trends

- **Agent reliability & self-healing:** Multiple high-priority issues target subagent recovery, hang detection, and resilient execution ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323), [#21409](https://github.com/google-gemini/gemini-cli/issues/21409), [#22232](https://github.com/google-gemini/gemini-cli/issues/22232)). The community wants agents that fail gracefully and recover without manual intervention.
- **AST-aware codebase tools:** Persistent interest in syntactic-level file reading and search to reduce context waste ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746), [#19561](https://github.com/google-gemini/gemini-cli/issues/19561)).
- **Sharable agent trajectories:** Demand for visible subagent execution paths via `/chat share` to improve debugging and evaluation ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598)).
- **Zero-dependency OS sandboxing:** A proposal to lean into the model's bash affinity while maintaining security isolation ([#19873](https://github.com/google-gemini/gemini-cli/issues/19873)).
- **Auto Memory quality improvements:** Requests to fix low-signal session loops and invalid patch handling in the memory system ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525)).

---

## 6. Developer Pain Points

- **Subagent opacity:** When subagents hang, fail, or report false successes, the main session has no visibility into what went wrong. Bug reports lack subagent context ([#21763](https://github.com/google-gemini/gemini-cli/issues/21763)), and trajectories aren't shareable ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598)).
- **Context window bloat:** Tool-call cancellations, interrupted responses, and large file reads all leak into context. Users see this as wasted tokens and degraded performance ([#28934](https://github.com/google-gemini/gemini-cli/pull/28934), [#28939](https://github.com/google-gemini/gemini-cli/pull/28939), [#19561](https://github.com/google-gemini/gemini-cli/issues/19561)).
- **Shell command stuck states:** Commands that complete normally leave the CLI in a perpetual "Awaiting user input" state ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), and interactive prompts (e.g., Vite scaffolding) cause permanent hangs ([#22465](https://github.com/google-gemini/gemini-cli/issues/22465)).
- **Git environment fragility:** Malformed `GIT_CONFIG_*` variables and unsafe `diff.external` overrides break all git operations inside the sandboxed shell ([#28938](https://github.com/google-gemini/gemini-cli/pull/28938), [#28930](https://github.com/google-gemini/gemini-cli/pull/28930)).
- **Platform compatibility gaps:** Wayland breaks the browser agent ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)), symlinks in agent directories are ignored ([#20079](https://github.com/google-gemini/gemini-cli/issues/20079)), and Windows users hit long-path and test-skipping issues ([#28926](https://github.com/google-gemini/gemini-cli/pull/28926), [#28832](https://github.com/google-gemini/gemini-cli/pull/28832)).
- **Auto Memory loops:** The memory inbox re-surfaces low-signal or invalid sessions endlessly, creating noise rather than value ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523)).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-21

## 1. Today's Highlights

Copilot CLI v1.0.81-6 ships with improved startup/session approval controls (`defaultMode`/`defaultPermissionMode`) and a new `--with-token` flag for stdin-based authentication, while ACP clients now receive subagent IDs and live metadata. The community is actively reporting authentication and MCP bridging gaps—most notably OAuth tokens not passing from the desktop app into CLI sessions—and a persistent Windows/WSL session-splitting bug continues to draw attention.

## 2. Releases

**v1.0.81-6** — [github.com/github/copilot-cli](https://github.com/github/copilot-cli)
- **Added:** `defaultMode` and `defaultPermissionMode` settings to control startup behavior and approval defaults for new interactive sessions.
- **Added:** `--with-token` flag on `copilot login` for reading an auth token from stdin (useful for scripted/CI auth flows).
- **Improved:** ACP clients now receive subagent IDs, raw event subscriptions, and live title/mod metadata for better observability and orchestration.

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#1481](https://github.com/github/copilot-cli/issues/1481) | SHIFT+ENTER executes instead of breaking line | Universal shortcut mismatch breaks UX for users of other chat apps | 28 comments · 17 👍 · **CLOSED** |
| [#4390](https://github.com/github/copilot-cli/issues/4390) | Org-enabled models missing from CLI catalogue (Claude Sonnet 5/Opus 5/Kimi K3) | Enterprise users can't access models enabled on their account via CLI | 15 comments · 7 👍 · **CLOSED** |
| [#4096](https://github.com/github/copilot-cli/issues/4096) | Third-party MCP OAuth token not bridged to CLI sessions | Desktop app shows "Connected" but CLI tools are unavailable | 6 comments · 2 👍 · **CLOSED** |
| [#4439](https://github.com/github/copilot-cli/issues/4439) | CLI 1.0.79 rejects GitLab MCP OAuth (RFC 8414 issuer mismatch) | GitLab self-managed MCP servers fail authentication after recent update | 5 comments · 3 👍 · **CLOSED** |
| [#3162](https://github.com/github/copilot-cli/issues/3162) | Custom MCP servers falsely reported as blocked by policy | Registry-allowlisted servers incorrectly rejected in 1.0.42 | 7 comments · 1 👍 · **CLOSED** |
| [#4524](https://github.com/github/copilot-cli/issues/4524) | Enforced sandbox blocks `git` on Windows | Sandbox overly restrictive; agents can't use git despite directory permissions | 3 comments · 0 👍 · **CLOSED** |
| [#4535](https://github.com/github/copilot-cli/issues/4535) | `store_memory` fails in v1.0.81 prereleases — missing instance ID | Native memory writer crashes without required `instanceId` | 3 comments · 0 👍 · **OPEN** |
| [#4528](https://github.com/github/copilot-cli/issues/4528) | Non-interactive sessions bypass `disableBypassPermissionsMode` policy | Enterprise managed settings ignored in `-p`/`--prompt` mode | 0 comments · 0 👍 · **OPEN** |
| [#4542](https://github.com/github/copilot-cli/issues/4542) | Workspace `.mcp.json` detected but not connected in agent sessions | `mcp list`/`mcp get` show enabled, but interactive sessions can't use them | 0 comments · 1 👍 · **OPEN** |
| [#3698](https://github.com/github/copilot-cli/issues/3698) | MCP stdio server leak — unbounded child process spawn | Slow/unreachable MCP servers cause CPU pinning via leaked processes | 1 comment · 3 👍 · **CLOSED** |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#4510](https://github.com/github/copilot-cli/pull/4510) | Remove GitHub Copilot CLI documentation from README | OPEN | Strips installation and usage docs from the repo README; likely a migration to centralized docs. |

*Note: No additional PRs were reported in the last 24 hours.*

## 5. Feature Request Trends

- **Auth token passthrough & stdin auth** — `--with-token` addresses a real need for CI/automated flows; users want more granular control over how credentials enter sessions.
- **Policy enforcement parity** — Multiple reports highlight that managed enterprise settings (e.g., `disableBypassPermissionsMode`) are inconsistently applied across interactive, non-interactive, and sandbox modes.
- **Cross-platform session continuity** — WSL, Remote-SSH, and desktop app restarts fragment session state; users want a single coherent session identity regardless of host environment.
- **MCP reliability** — Persistent issues around OAuth bridging, policy false-negatives, and stdio process leaks signal demand for a more robust MCP connection lifecycle.
- **UX parity with chat apps** — SHIFT+ENTER line-break expectations and multi-turn `/ask` support show users want the CLI to match familiar interface patterns.

## 6. Developer Pain Points

1. **MCP server connectivity is fragile.** Token bridging between the desktop app and CLI sessions (#4096), issuer mismatches with GitLab (#4439), and registry policy false-negatives (#3162) create a disjointed experience. The stdio process leak (#3698) compounds the frustration.
2. **Enterprise managed settings are inconsistently enforced.** Non-interactive sessions bypass `disableBypassPermissionsMode` (#4528), and enum validation rejects valid policy values (#4349), undermining organizational governance.
3. **Session state fragments across environments.** WSL vs. host splits (#4543), Remote-SSH reconnect blanks the transcript (#4529), and Ctrl+Z/restart loses recent sessions (#4539) all point to a lack of unified session persistence.
4. **Sandbox restrictions are overly aggressive.** The enforced sandbox blocks `git` (#4524) and doesn't support VS Code remote on WSL (#4546), limiting practical developer workflows.
5. **Authentication plumbing is ad-hoc.** Missing `instanceId` in memory storage (#4535), OAuth token not reaching CLI sessions (#4096), and Git credential helper removal during plugin clone (#4103) suggest auth handling needs systematic hardening.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-21

## 1. Today's Highlights
The Kimi Code CLI repository saw a single contributor, **QIANLING-0831**, drive both today's issue and PR — proposing **Kimi Memory Plus**, a workspace-scoped long-term memory plugin, alongside companion documentation for plugin security and persistent data handling. No new releases were published in the last 24 hours.

## 2. Releases
No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Author | Link |
|---|-------|--------|------|
| 1 | **Kimi Memory Plus — workspace-scoped long-term memory plugin** | QIANLING-0831 | [Issue #2613](https://github.com/MoonshotAI/kimi-cli/issues/2613) |

**Why it matters:** This is the only open issue in the reporting window and directly expands Kimi CLI's plugin architecture. The author proposes exposing long-term memory as a workspace-scoped plugin, built on the existing `explicit-memory` stdio MCP server integration. The compatibility update note (2026-08-21) signals active iteration and suggests the team is already exploring how to wire this into the CLI without requiring invasive changes.

**Community reaction:** No comments or upvotes yet — the issue is fresh and under public radar. Early engagement from plugin developers and memory-state users would be valuable.

## 4. Key PR Progress

| # | Title | Author | Link |
|---|-------|--------|------|
| 1 | **docs(plugins): document security and persistent data** | QIANLING-0831 | [PR #2614](https://github.com/MoonshotAI/kimi-cli/pull/2614) |

**What's changing:** This PR fills a critical documentation gap in the plugin ecosystem. It clarifies that plugin tools run as local subprocesses inheriting the current user's file and network access — a security-relevant detail developers need before distributing or relying on third-party plugins. It also documents credential handling for `inject` tools, warns against logging or committing injected values, and clarifies reinstall behavior (replacing the installed directory).

**Why it matters:** As the plugin system matures, security transparency is essential for adoption. This PR establishes the baseline trust model for the ecosystem.

## 5. Feature Request Trends
From the single issue this cycle, one clear trend emerges:

- **Workspace-scoped persistent memory** — Users want the ability to retain context across sessions at the project level, not just within a single conversation. The "Memory Plus" proposal points to a growing demand for stateful plugin ecosystems rather than purely ephemeral tooling.

## 6. Developer Pain Points
Based on the available data from this reporting period:

- **Security transparency for plugins** — The companion PR (#2614) indicates developers needed clearer answers about subprocess isolation, credential exposure, and data persistence. This is an emerging pain point as the plugin system gains traction.
- **Long-term memory without scaffolding** — Issue #2613 highlights that developers currently lack an official, workspace-level memory mechanism, forcing ad-hoc solutions.

---

*Data covers 2026-08-20 → 2026-08-21. Repository: [MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-21

---

## 1. Today's Highlights

OpenCode v1.18.19 shipped with native OpenAI and Anthropic passthroughs for Cloudflare AI Gateway and tighter Codex rate-limit alignment. The community is increasingly focused on performance — a persistent high-CPU issue (#30086, 24 👍) and a new TUI-lag report under multi-subagent loads (#42657) dominated discussion, while the 2.0 beta surfaced agent-switching and session-creation bugs.

---

## 2. Releases

**v1.18.19** — The latest release adds two core improvements and two bugfixes:

- **Cloudflare AI Gateway passthroughs** — OpenAI and Anthropic models are now natively routable through Cloudflare's AI Gateway without custom provider setup.
- **Codex rate-limit alignment** — Rate limits now more closely match ChatGPT subscription tiers (#30086 contributor @GameOn223).
- **Qwen sampling defaults removed** — Built-in defaults that sent unsupported settings to Qwen models have been stripped.
- **Bugfix truncated** in the source data; see the [release page](https://github.com/anomalyco/opencode/releases) for the full changelog.

---

## 3. Hot Issues

| # | Title | Status | 👍 | Comments | Why It Matters |
|---|-------|--------|----|----------|----------------|
| [#30086](https://github.com/anomalyco/opencode/issues/30086) | High CPU usage in newer versions | OPEN | 24 | 48 | Users report CPU spiking so severely that 3 concurrent sessions cause system lag — a critical usability regression. |
| [#4754](https://github.com/anomalyco/opencode/issues/4754) | Copy and Paste behaviour under Linux | CLOSED | 18 | 17 | Linux's dual clipboard buffers remain a pain point; the fix introduced a config toggle for primary-buffer support. |
| [#30158](https://github.com/anomalyco/opencode/issues/30158) | Terminal button disappears in web UI since v1.15.12 | OPEN | 14 | 12 | A visual regression that breaks terminal access from the web UI; downgrading restores it. |
| [#27474](https://github.com/anomalyco/opencode/issues/27474) | TypeError: Failed to fetch on Explore/Agents | OPEN | 0 | 10 | Network-failure error during navigation to sub-agents; points to a possible API or auth regression. |
| [#27875](https://github.com/anomalyco/opencode/issues/27875) | Enter key unresponsive during permission prompts | OPEN | 1 | 9 | Users are stuck when sub-agents request tool-call approval; `Ctrl+Enter` only inserts a newline. |
| [#43619](https://github.com/anomalyco/opencode/issues/43619) | subagent requires sessionID, blocking first child session | CLOSED | 0 | 9 | A 2.0 beta regression where the tool schema contradicts its own docs, preventing any initial child-session spawn. |
| [#20458](https://github.com/anomalyco/opencode/issues/20458) | Mouse escape sequences garbled after TUI exit | OPEN | 5 | 8 | Terminal artifacts after quitting; distinct from in-session mouse issues but equally disruptive. |
| [#35107](https://github.com/anomalyco/opencode/issues/35107) | Memory keeps growing until process is killed | OPEN | 0 | 4 | `structuredClone` on every `PartUpdated` event under Bun/mimalloc causes massive heap pressure (~4.9 GB RSS reported). |
| [#43054](https://github.com/anomalyco/opencode/issues/43054) | Non-free models return `Forbidden: {model:"big-pickle"}` | OPEN | 2 | 4 | A provider-level routing bug that locks Go-subscription users into only two free models. |
| [#42657](https://github.com/anomalyco/opencode/issues/42657) | TUI lag with multi-subagent sessions (97% CPU on render thread) | OPEN | 0 | 3 | Confirms the CPU regression in a multi-subagent context; affects all tested terminals (Warp, WezTerm, Windows Terminal). |

---

## 4. Key PR Progress

| # | Title | Status | Author | Summary |
|---|-------|--------|--------|---------|
| [#43724](https://github.com/anomalyco/opencode/pull/43724) | fix(core): steer manual compaction by default | OPEN | kitlangton | `/compact` during an active turn now runs at the next step boundary instead of silently queueing — fixes an unresponsive UX edge case. |
| [#43741](https://github.com/anomalyco/opencode/pull/43741) | refactor(core): remove dead AI SDK ID stripping | OPEN | opencode-agent[bot] | Removes unreachable request-body rewrite that stripped response item IDs for OpenAI/Azure/Bedrock; cleans up dead code. |
| [#43681](https://github.com/anomalyco/opencode/pull/43681) | fix(core): resolve Bedrock AWS profile credentials for V2 | OPEN | acorpstein | Fixes AWS Bedrock profile resolution in the 2.0 branch; tested locally for 1.5 weeks by an Amazon One Medical engineer. Closes #40663. |
| [#32370](https://github.com/anomalyco/opencode/pull/32370) | feat(tui): add linux_clipboard_selection config | OPEN | bornmw | Adds a `linux_clipboard_selection` config option (`clipboard` vs `primary`) to address the long-standing Linux clipboard issue (#4754). |
| [#43738](https://github.com/anomalyco/opencode/pull/43738) | fix(app): speed up cold home navigation | CLOSED | Hona | Warms the Home query cache on first navigation, cutting median cold-start latency from ~618 ms to ~86 ms. |
| [#42980](https://github.com/anomalyco/opencode/pull/42980) | fix(core): reduce Windows server CPU under parallel sessions | CLOSED | Hona | **+88.2% SSE throughput** (77k → 146k Events/s) with 48.4% less CPU by optimizing process spawning and executable resolution on Windows. |
| [#43736](https://github.com/anomalyco/opencode/pull/43736) | fix(opencode): preserve Cerebras completion limit | CLOSED | opencode-agent[bot] | Adds a built-in Cerebras plugin that suppresses the generic output cap when native `max_completion_tokens` is set. |
| [#43677](https://github.com/anomalyco/opencode/pull/43677) | fix(core): send console Anthropic API key header | CLOSED | opencode-agent[bot] | Translates OpenCode Console Bearer credentials to `x-api-key` for Anthropic Messages requests; covered by regression test. |
| [#43675](https://github.com/anomalyco/opencode/pull/43675) | fix(opencode): answer subagent permissions in run | CLOSED | opencode-agent[bot] | Auto-approves or auto-rejects permission requests for non-interactive run sessions, fixing the Enter-key-stuck problem (#27875). |
| [#43733](https://github.com/anomalyco/opencode/pull/43733) | fix(core): avoid deep cloning session parts | CLOSED | ColeLindfors | Addresses the memory-growth issue (#35107) by removing the `structuredClone` call on every `PartUpdated` event. |

---

## 5. Feature Request Trends

- **Clipboard & input parity across platforms** — Linux dual-buffer support (#4754 / #32370) and backspace handling in ConPTY environments (#34878, #43051) show repeated demand for terminal-emulator-agnostic input behavior.
- **Credential & provider flexibility** — Requests for per-provider token refresh without restart (#43281), per-MCP-server trust configuration (#40125), and configurable context-window limits for local models (#31433) indicate users want finer-grained control over provider plumbing.
- **Session & agent management** — The ability to hide inline diffs (#43739), store OpenCode root files in a user-selected directory (#43700), and switch agents/models programmatically via plugins (#43718) reflect a desire for more composability in multi-agent workflows.
- **Resource-conscious operation** — CPU and memory regressions have surfaced an implicit feature request: built-in profiling tools or resource limits that help users diagnose and contain runaway processes.

---

## 6. Developer Pain Points

1. **Performance regressions are the #1 complaint.** Issue #30086 (48 comments, 24 👍) and PR #42980 both point to CPU explosion under parallel sessions, especially on Windows. The TUI render thread hitting 97% CPU (#42657) confirms this is a systemic issue, not an edge case.

2. **Memory leaks under sustained use.** The `structuredClone`-on-every-part-update pattern (#35107) causes RSS to climb to nearly 5 GB; the fix in #43733 is a direct response but highlights a broader concern about Bun/mimalloc memory behavior in long-running sessions.

3. **2.0 beta stability gaps.** Multiple new issues (#43619, #43179, #43591) surfaced in the v2 beta — subagent session creation, silent model retention on agent switch, and segmentation faults — suggesting the 2.0 release train needs more integration coverage before GA.

4. **Terminal/input edge cases persist.** Backspace broken in Warp (#43051) and herdr/ConPTY (#34878), plus Linux clipboard fragmentation (#4754), show that OpenCode's TUI layer still struggles with terminal diversity. Each fix tends to be terminal-specific rather than systemic.

5. **Provider routing bugs block paid tiers.** The `Forbidden: {model:"big-pickle"}` error (#43054) locking Go subscribers to two free models is a revenue-impacting bug that points to insufficient provider-compatibility testing across the model catalog.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-21

## 1. Today's Highlights
The Pi community focused this period on clarifying Windows usage patterns and fixing a critical auto‑compaction bug that allowed sessions to exceed context limits before API rejection. Development momentum continued on slash‑command aliases (`/exit`, `/bye`) and TUI robustness improvements, while several Gemini 3.x and OpenAI‑gateway compatibility fixes moved into review.

## 2. Releases
No new releases in the last 24 hours.

## 3. Hot Issues
1. **#7547 – Windows usage discussion** – *36 comments, 1 👍*  
   Open survey to prioritize Windows‑specific fixes and documentation. The community highlighted the fragmentation of Windows runtimes and the need for a clear focus.  
   https://github.com/badlogic/pi-mono/issues/7547

2. **#6879 – Auto‑compaction never triggers after context grows past 100%** – *18 comments, 17 👍*  
   Agents running long sessions could exceed the context window without triggering compaction; the fix now checks after every agent turn rather than waiting for an API error.  
   https://github.com/badlogic/pi-mono/issues/6879

3. **#5023 – Terminal scrolls to beginning without reason** – *17 comments, 2 👍*  
   Random jumps to the start of the session during model‑working phases remain a persistent distraction; the thread continues to gather reproduction steps.  
   https://github.com/badlogic/pi-mono/issues/5023

4. **#3442 – WebSocket transport in openai‑responses** – *9 comments*  
   The provider currently ignores `transport: "websocket"`; adding support would align with modern streaming expectations.  
   https://github.com/badlogic/pi-mono/issues/3442

5. **#6300 – Windows TUI input line redrawn on every keystroke** – *8 comments*  
   Characters appear on new lines in both cmd.exe and Windows Terminal; a known Windows‑specific rendering bug.  
   https://github.com/badlogic/pi-mono/issues/6300

6. **#8157 – Migrate grok‑mermaid → lovely‑mermaid** – *7 comments, 1 👍*  
   The newer lovely‑mermaid library offers better parsing and fewer corner‑case limitations; migration would improve diagram rendering reliability.  
   https://github.com/badlogic/pi-mono/issues/8157

7. **#6093 – Scoped Anthropic API keys need request params** – *6 comments*  
   Scoped keys don’t follow the `sk‑ant‑oat…` prefix convention, causing incorrect header logic; the fix ensures proper parameter injection.  
   https://github.com/badlogic/pi-mono/issues/6093

8. **#5340 – Add `/config` and `/exit` aliases for `/settings` and `/quit`** – *5 comments*  
   Users coming from Claude Code expect familiar exit commands; the issue tracks the simplest alias implementation.  
   https://github.com/badlogic/pi-mono/issues/5340

9. **#6996 – Gemini 3.x models fail during tool use (missing thought_signature)** – *5 comments*  
   Tool‑call rounds on Gemini 3.5/3.6 flash drop the required `thought_signature`, causing immediate failures; a provider‑specific fix is needed.  
   https://github.com/badlogic/pi-mono/issues/6996

10. **#8133 – Per‑model compaction settings** – *3 comments, 3 👍*  
    Proposes a `compaction.profiles` map so large models can reserve more tokens than the global default; addresses pain from one‑size‑fits‑all compaction.  
    https://github.com/badlogic/pi-mono/issues/8133

## 4. Key PR Progress
1. **#4537 – Exit alias** – Added `/exit` as a drop‑in alias for `/quit` with identical similarity handling.  
   https://github.com/badlogic/pi-mono/pull/4537

2. **#8416 – Hold `triggerTurn:false` custom messages until tool batch ends** – Prevents custom messages from landing between a `toolCall` and its `toolResult`, which strict providers reject.  
   https://github.com/badlogic/pi-mono/pull/8416

3. **#8118 – `requiresNonNullAssistantContent` compat flag** – Allows forcing `""` instead of `null` for assistant content when replaying tool‑call‑only messages, satisfying certain OpenAI‑compatible gateways.  
   https://github.com/badlogic/pi-mono/pull/8118

4. **#8405 – Normalize kimi‑coding thinking signatures to base64url** – Fixes the second‑turn failure in reasoning‑enabled kimi‑coding conversations by correcting signature encoding.  
   https://github.com/badlogic/pi-mono/pull/8405

5. **#8407 – Preserve logical lines when copying soft‑wrapped text** – Fixes clipboard output in fullscreen TUI to keep actual line boundaries instead of viewport‑induced wraps.  
   https://github.com/badlogic/pi-mono/pull/8407

6. **#8363 – Prevent wrapped table link color leaks** – Resets link colors before table padding/borders, fixing style bleed in rendered markdown tables.  
   https://github.com/badlogic/pi-mono/pull/8363

7. **#5268 – Render hardware cursor by default** – Restores the terminal’s native cursor when the window loses focus, solving the “fake” cursor‑hollow bug.  
   https://github.com/badlogic/pi-mono/pull/5268

8. **#8302 – Amazon Bedrock Mantle provider** – Adds support for GPT/OpenAI models routed through Bedrock’s new Mantle API surface.  
   https://github.com/badlogic/pi-mono/pull/8302

9. **#8399 – Searchable default model/thinking in settings selector** – Makes the default label searchable in `/model` and `/thinking` selectors, improving discoverability.  
   https://github.com/badlogic/pi-mono/pull/8399

10. **#5160 – Add `/exit` and `/bye` as alternative quit commands** – Extends the builtin slash‑command list to include both aliases, matching user muscle memory from other CLIs.  
    https://github.com/badlogic/pi-mono/pull/5160

## 5. Feature Request Trends
- **Slash‑command aliases** – Strong demand for `/exit`, `/bye`, `/config` as synonyms for existing commands to match Claude Code/Codex conventions.
- **Windows‑first support** – Repeated requests for clearer Windows installation paths, documented fix priorities, and resolution of TUI rendering/input bugs.
- **Per‑model compaction profiles** – Users want granular control over context‑compaction thresholds per provider/model rather than a single global setting.
- **Provider compatibility flags** – Need for flags like `requiresNonNullAssistantContent` and thinking‑level toggles (e.g., Gemini’s MINIMAL→LOW) to work around gateway‑specific strictness.
- **TUI robustness** – Ongoing requests for stable cursor behavior, correct line‑wrap copying, and crash prevention on large diffs.

## 6. Developer Pain Points
- **Windows‑specific TUI bugs** – Input redraw, escape‑sequence leaks, and unknown command handling cause frequent friction for the large Windows developer base.
- **Auto‑compaction gaps** – Agents that exceed context limits without triggering compaction waste tokens and hit API errors; the community seeks more proactive, per‑turn checks.
- **Terminal scrolling & cursor quirks** – Random jumps to session start and incorrect cursor‑blur states disrupt long coding sessions.
- **Provider‑specific format strictness** – OpenAI‑compatible gateways, Gemini 3.x, and Anthropic scoped keys require workarounds for null content, thinking‑signature encoding, and header conventions.
- **SSH/passphrase interference** – Background git updates can prompt for SSH passphrases that overwrite the TUI, and `Ctrl+D` over SSH may leak escape sequences into the parent shell.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-21

## 1. Today's Highlights

Qwen Code v0.21.15 shipped with a major Web Shell enhancement: file attachments can now be inserted via the composer or `@` selection, with improved streaming and immediate sidebar sync. The `/review` pipeline continues its aggressive hardening cycle, landing convergence advisories, machine-readable diagnostics, and Aone Code PR-context support across multiple PRs in a single day.

---

## 2. Releases

| Version | Notes |
|---|---|
| **v0.21.15** | Latest stable release; includes Web Shell attachment support and improved streaming/sidebar sync ([#9405](https://github.com/QwenLM/qwen-code/pull/9405), [#9477](https://github.com/QwenLM/qwen-code/pull/9477)) |
| **v0.21.14-nightly.20260821** | `/review`: tells the author why a review loop is not settling; CI fallback fix ([#9461](https://github.com/QwenLM/qwen-code/pull/9461)) |
| **v0.21.11-nightly.20260820** | Web Shell approval/ask-user dialogs now rendered as in-flow sheets; background-agent false-failure fix ([#9xxx](https://github.com/QwenLM/qwen-code/pull/9xxx)) |

---

## 3. Hot Issues

1. **#9278 — `/review` publish-time convergence advisory** (8 comments) — Tracks the design and telemetry for diagnosing when review loops fail to settle. Author `wenshao` documents the "runaway loop" problem where each round's findings grow faster than the fixer can address them. *(Open, P2)*

2. **#8382 — Duplicate provider tool call id** (7 comments) — Recurring bug where tool calls fail with `"Duplicate provider tool call id"` and `"not recorded"` errors. High community impact as it blocks long sessions. *(Open, P2)*

3. **#8724 — Cross-session messaging** (7 comments) — Proposes inter-session communication on the same machine via `list_agents` / `send_message`, with an explicit fail-closed gate on the receiver. Could unlock powerful multi-agent workflows. *(Open)*

4. **#9309 — Context compression appears incorrect** (6 comments) — After `/compress-fast` then `/compress`, the second compression shows anomalous token counts (170k → …), suggesting a bug in the compression pipeline. *(Open, P3)*

5. **#7306 — Harden tool-output budgeting & artifact lifecycle** [CLOSED] (6 comments) — Phase 1 correctness and focused contract hardening are complete; shared finalization implementation merged. *(Closed)*

6. **#9485 — Web Shell copy buttons fail over non-localhost HTTP** [CLOSED] (5 comments) — Clipboard API unavailable when daemon serves over plain HTTP from a remote IP. Fix landed. *(Closed)*

7. **#2128 — Memory grows unboundedly during long sessions** (5 comments) — Root cause identified: `useHistoryManager.history` array grows without limit over dozens of hours. A persistent pain point for power users. *(Open, P1)*

8. **#9556 — Review pipeline code execution as invoking user** (5 comments) — Security discussion: whether the pipeline should keep granting code execution to the review's own user identity across worktrees. *(Open)*

9. **#9586 — Duplicate tool-call breaker leaves orphaned call** [CLOSED] (4 comments) — In ACP daemon sessions, repeated duplicate tool-call circuit breakers can leave a persisted `functionCall` without a terminal `tool_result`. Fix merged. *(Closed)*

10. **#9597 — Hierarchical memory loads same QWEN.md twice via symlink** (3 comments) — When a workspace `QWEN.md` is a symlink to an ancestor, it gets loaded twice, wasting context budget. *(Open, P2)*

---

## 4. Key PR Progress

1. **#9622 — docs: `/takeover from N` operator guide** — Adds a task-oriented guide for the takeover command, cross-linked with the design record. *(Open)*

2. **#9572 — fix(review): pin verified git identity across the probe tree** ([#9557](https://github.com/QwenLM/qwen-code/pull/9557)) — Fixes a security gap where `worktreeResidue` tripwires verified a tree's identity once then re-discovered it through writable `.git` files. *(Open)*

3. **#9303 — fix(web-shell): bound daemon transcript retention to stop renderer OOM** — Raw replay snapshots are now released after injection; replay builds run under the same block cap as live growth, preventing browser OOM crashes. *(Open)*

4. **#9621 — feat(review): back pr-context on Aone Code targets** — The `fetch-pr` subcommand was GitHub-only; this PR adds Aone Code support so review agents can read target metadata and existing discussion. *(Open)*

5. **#9590 — feat: support provider-aware reasoning controls** — Adds WebShell reasoning controls for DeepSeek V4, GLM 5.2, and Kimi models, matching each documented route (toggle hybrids, canonical effort tiers, mandatory-thinking). *(Open)*

6. **#9623 — feat(review): machine-readable convergence observation** — Extends the convergence diagnosis from human-readable prose (shipped in [#9461](https://github.com/QwenLM/qwen-code/pull/9461)) to a machine-readable signal the round report can act on. *(Open)*

7. **#9566 — fix(review): screen content filters before probe tree restore** ([#9558](https://github.com/QwenLM/qwen-code/pull/9558)) — `scratch-tree` now refuses to create/reset while a local content filter is defined, preventing `filter.<name>.smudge` from rewriting files unexpectedly. *(Open)*

8. **#8927 — feat(channels): bound session lifetime with `sessionRotation`** — New per-channel option: when a session exceeds `maxTurns` or time bounds, the next message starts a fresh session instead of reusing a bloated one. Addresses [#2128](https://github.com/QwenLM/qwen-code/issues/2128). *(Open)*

9. **#9273 — feat(review): capture-tui — rendering claims get pixels** — Adds `qwen review capture-tui` so verifiers can produce rendering evidence (`.ans`, `.png`) inside a private tmux server instead of arguing from code alone. *(Open)*

10. **#9609 — fix(web-shell): don't steal approval focus while user is typing** — The tool-approval dialog now yields keyboard focus when the active element is an editable composer, fixing a disruptive UX bug also reported in [#9571](https://github.com/QwenLM/qwen-code/issues/9571). *(Open)*

---

## 5. Feature Request Trends

- **Aone Code parity** — A cluster of 8+ open issues (#9620, #9613, #9616, #9618, #9615, #9617, #9614, #9619) driven by `wenshao` covers branch-based MRs, cross-round comment dedup, self-PR detection, incremental caching, inline anchoring on removed lines, cleanup audit, AI-comment merge gates, and residual gaps. Aone Code is clearly a prioritized integration surface.
- **Review loop observability & self-correction** — Convergence advisories, machine-readable diagnostics, capture-tui, and per-file content verdicts across rebases (#9191, #9190) show a strong push toward making the review pipeline auditable and incremental.
- **Multi-session orchestration** — Cross-session messaging (#8724) and session rotation bounds (#8927) indicate demand for coordinated, multi-session workflows with lifecycle control.
- **Provider-aware reasoning controls** — Support for DeepSeek, GLM, Kimi, and Xiaomi MiMo reasoning modes (#9590, #8368) reflects expanding model coverage needs.

---

## 6. Developer Pain Points

1. **Unbounded memory growth** (#2128) — Long-running sessions accumulate UI history without limit, causing OOM. A known, persistent issue with a partial mitigation via `sessionRotation` (#8927).
2. **Duplicate tool-call IDs** (#8382) — Repeated `"Duplicate provider tool call id"` errors disrupt sessions and are difficult to reproduce consistently.
3. **Context compression anomalies** (#9309) — Sequential compress operations produce incorrect token counts, eroding trust in the compression pipeline.
4. **Web Shell UX friction** — Focus stealing during approval dialogs (#9571, #9611), clipboard failures over HTTP (#9485), and slow sidebar pinning (#9465) are recurring UI complaints.
5. **Symlink-related memory duplication** (#9597) — Hierarchical memory loads the same `QWEN.md` twice through symlinks, wasting context in projects that use shared config files.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-21

---

## 1. Today's Highlights

The CodeWhale TUI crate decomposition continues to drive development, with three structural refactors landing today (FEAT-018 command shapes, tool-call stage extraction, and `read_lints` multi-file support). Meanwhile, the v0.9.10 release is addressing first-run UX friction by making the initial configuration experience progressive rather than front-loaded, and the team is moving aggressively on documentation localization for the growing Chinese-speaking user base.

---

## 2. Releases

**v0.9.10** — See the full announcement at [Hmbown/DeepSeek-TUI Releases](https://github.com/Hmbown/DeepSeek-TUI/releases).

> **Codewhale** is the public product from Shannon Labs. The `codewhale` command, npm package, and release-asset names remain lowercase technical identifiers. The legacy npm package `deepseek-tui` is deprecated and receives no further releases.

---

## 3. Hot Issues

| # | Title | Author | Why It Matters |
|---|-------|--------|----------------|
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | EPIC-005: CodeWhale TUI Crate Decomposition (Umbrella) | aboimpinto | The master tracking issue for the entire TUI crate reorganization. Every sub-EPIC and FEAT report ties back here — the architectural backbone of the current release cycle. |
| [#4070](https://github.com/Hmbown/CodeWhale/issues/4070) | feat: standalone read_lints tool for on-demand diagnostics | Hmbown | Fills a critical gap: agents could only read LSP diagnostics post-edit, with no on-demand way to check files they hadn't just modified. PR #5524 directly addresses this. |
| [#5345](https://github.com/Hmbown/CodeWhale/issues/5345) | 增加多行模式或者是允许自定义"发送"快捷键 | AiurArtanis | Users coming from Grok Build and Codex expect multi-line input mode and customizable send shortcuts. High practical impact for power users who write multi-paragraph prompts with markdown. |
| [#5526](https://github.com/Hmbown/CodeWhale/issues/5526) | Deprecated shell completion | RepentStar | PowerShell completions reference the outdated `codewhale-tui` command instead of `codew`. Affects users who rely on tab-completion in pwsh environments. |
| [#5482](https://github.com/Hmbown/CodeWhale/issues/5482) | EPIC(docs): review, partially restructure, and fully localize documentation to Chinese | SparkofSpike | Addresses a real accessibility barrier — English-only docs under `docs/` hinder Chinese-speaking users, and machine-translated versions are already stale. |
| [#5522](https://github.com/Hmbown/CodeWhale/issues/5522) | v0.9.10: make first run progressive instead of front-loading configuration | Hmbown | Direct user feedback: first launch has too much psychological cost — a wall of settings, key hints, and choices before reaching useful work. Non-English users especially hit a telemetry disclosure in English first. |

---

## 4. Key PR Progress

| # | Title | Author | Status | Description |
|---|-------|--------|--------|-------------|
| [#5524](https://github.com/Hmbown/CodeWhale/pull/5524) | feat(tui): add multi-file read_lints operation | wuisabel-gif | OPEN | Implements the approved scope of #4070. The `lsp` tool now supports a `read_lints` operation for multiple workspace-relative files, reusing the existing `LspManager` transport pool rather than spawning a new language-server lifecycle. |
| [#5525](https://github.com/Hmbown/CodeWhale/pull/5525) | refactor(tui): adopt command shapes in utility group (FEAT-018) | aboimpinto | OPEN | Converts the complete TUI utility command group to external command shapes (introduced in FEAT-014, hosted by FEAT-015). The seven command files stay under `codewhale-tui`; only their execution boundary changes. |
| [#5523](https://github.com/Hmbown/CodeWhale/pull/5523) | refactor(tui): extract tool call stages from turn loop | bistack | OPEN | Extracts three distinct stages from the turn loop: `plan_tool_calls`, `execute_planned_tools`, and `process_tool_results`. Preserves original control flow, mutable state, cancellation behavior, and indexed outcome collection. |
| [#5520](https://github.com/Hmbown/CodeWhale/pull/5520) | feat(web): move docs/sandbox and docs/web onto the dictionary spine | Lstarsky0 | CLOSED | Removes 29 `isZh` branches across `docs/sandbox` and `docs/web`, replacing them with proper dictionary-based localization. Files added to `check-locales.mjs`'s `OPTIONAL_FILES`. |
| [#5521](https://github.com/Hmbown/CodeWhale/pull/5521) | chore(tui): drop a single-argument concat! | Lstarsky0 | CLOSED | Fixes a `clippy::useless-concat` lint error in `crates/tui/src/runtime_handoff.rs:83`. |

---

## 5. Feature Request Trends

- **Multi-line input & customizable shortcuts** (#5345) — Users consistently want the ability to use `Enter` for line breaks and a modifier key for sending, matching the paradigm established by Grok Build and Codex.
- **On-demand diagnostics** (#4070) — The request for a standalone `read_lints` tool reflects a desire for agents to proactively check code quality without requiring an edit cycle first.
- **Progressive first-run experience** (#5522) — Users want to get to useful work faster; the current all-at-once configuration screen is a known friction point.
- **Localization** (#5482) — Chinese-language documentation is a high-priority need for a significant portion of the user base, with ongoing effort to restructure around a dictionary spine.

---

## 6. Developer Pain Points

1. **Shell completion drift** — Completions for PowerShell (and likely other shells) reference the old `codewhale-tui` binary name, creating confusion for users who've migrated to the `codewhale` / `codew` namespace.
2. **First-run psychological cost** — New users face an English-only telemetry disclosure followed by a dense settings wall before they can start using the tool. Non-English speakers are disproportionately affected.
3. **Documentation localization quality** — Machine-translated docs are already stale, and some source documents are themselves outdated. The team is restructuring around a dictionary spine to make future maintenance sustainable.
4. **LSP diagnostic gap** — The inability to read lints on non-edited files forced a workaround-heavy workflow; the community has been waiting on #4070 for over a month.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*