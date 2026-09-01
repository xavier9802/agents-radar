# AI CLI Tools Community Digest 2026-09-01

> Generated: 2026-09-01 04:39 UTC | Tools covered: 10

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
**Date: 2026-09-01**

---

## 1. Ecosystem Overview

The AI CLI tool landscape in early September 2026 is characterized by rapid iteration and growing pain from maturity: major players (Claude Code, Codex, Gemini CLI, Copilot CLI) are pushing agent-level features while wrestling with reliability regressions, while mid-tier tools (Pi, Qwen Code, Codewhale, OpenCode) are carving out differentiated positions around developer experience and extensibility. The dominant cross-cutting theme is **session and workflow reliability** — every tool community reports session-resume, subagent-hang, or retry-loop bugs as top pain points. A secondary theme is **MCP/ecosystem integration fragility**, with OAuth, auth, and cross-platform sync emerging as universal friction zones rather than tool-specific quirks.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Releases (Last 24h) | Closed Issues/PRs |
|---|---|---|---|---|
| **Claude Code** | 10 | 4 | v2.1.252 | 2 (AGENTS.md, session rename) |
| **OpenAI Codex** | 10 | ~12 | v0.152.0, 2 alpha | 0 |
| **Gemini CLI** | 10 | ~16 | v0.59.0-nightly | 0 |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.83-0 | 0 |
| **Kimi Code CLI** | 1 | 2 | None | 2 (task UX, sub-task hang) |
| **OpenCode** | 10 | ~10 | None | 0 |
| **Pi** | 5 open / 5 closed | ~11 | None (0.84.4 stable) | 5 (TUI corruption, auto-compaction, CLI flags, Bedrock, fork race) |
| **Qwen Code** | 10 (1 closed in digest) | 0 explicit | v0.22.3-nightly | 4 (cross-session messaging, task_list loops/filters, resume hazard, archive) |
| **Codewhale (DeepSeek TUI)** | 1 open / 9 closed | ~20 | None | 9 (rebrand, auth, provider authority, session resume, parallel tests, wires, UI) |

*Note: PR/Issue counts reflect items mentioned in the digest, not total project activity.*

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|---|---|---|
| **Cross-agent standardization** | Claude Code, Codex, Cursor, Amp | AGENTS.md as a unified codebase descriptor; Claude Code's #6235 (5,094 👍) closed with ecosystem impact |
| **Session resilience & deterministic resume** | Copilot CLI, Pi, Codewhale, Qwen Code | Session state fidelity on resume (agent config, context injection, custom MCP), idempotent retry budgets, bounded startup timeouts |
| **MCP ecosystem maturity** | Claude Code, Codex, Gemini CLI, Copilot CLI | OAuth token auto-refresh (#65036), pagination support, production-grade connectivity beyond read-only connectors |
| **Agent utilization & subagent reliability** | Gemini CLI, Pi, OpenCode, Kimi Code | Subagents that activate without explicit prompting, correct completion reporting, no silent hangs or false-success status |
| **Context & cost transparency** | Copilot CLI, Pi, Codex, Claude Code | Unbounded retry costs (#4663), context budget miscalculation (#8061), usage accounting regressions (#40067), silent context growth |
| **Cross-platform session continuity** | Claude Code, Gemini CLI, OpenCode | Skills sync across Desktop/CLI, conversation persistence across Web/Android/Desktop, consistent behavior across OS boundaries |
| **Vim/developer-native TUI ergonomics** | Codex, OpenCode, Pi | Vim-mode search/undo (#41941), inline diff preview (#8003), TUI rendering stability under long output |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Pi | Qwen Code | Codewhale | OpenCode | Kimi Code |
|---|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Enterprise agent with Claude ecosystem | General-purpose CLI with ChatGPT integration | Deep ecosystem tooling, security-first | GitHub-integrated agent workflows | Embeddable agent engine, provider diversity | Web-shell polish, review pipelines | Rebranding + architectural decomposition | Plugin extensibility, browser tooling | Migration path from legacy CLI |
| **Target users** | Enterprise/individual devs | Broad developer base | Power users, security-conscious | GitHub Enterprise users | Researchers, embedders, multi-provider users | llama.cpp/local model users | Migrating Codex CLI users | Open-source plugin builders | Legacy Kimi CLI users |
| **Technical approach** | Skills, AGENTS.md, Remote Control | TUI-first with Vim parity | Subagent architecture, environment sanitization | ACP (Agent Control Protocol), MCP-heavy | In-memory fork model, TCP/WS transports | Web-shell, per-session auth tokens | Crate decomposition, Unix-socket daemon | Plugin RPC, Firecrawl search | One-key migration flow |
| **Key differentiator** | Ecosystem convergence leadership (AGENTS.md) | Vim-mode TUI, rate-limit banners | Security hardening (env var sanitization, NTFS 8.3) | mTLS proxy, herdr multiplexer detection | Provider diversity (CoralBricks, Melious), embeddability | Local model support, cross-session messaging | Native PKCE auth, unified provider authority | Browser plugin, VS Code diff preview | Migration automation from kimi-cli |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **Codewhale** — 9 of 10 hot issues closed in 24h with ~20 PRs landed. The rebrand is accompanied by aggressive architectural cleanup (crate decomposition, provider authority unification, session resume fixes). A project in transformation mode with strong contributor velocity.
- **Pi** — 5 issues closed in one cycle (fork races, compaction, CLI parsing, Bedrock normalization, TUI rendering). The project is addressing deep lifecycle correctness bugs, indicating a transition from feature accumulation to stability hardening.
- **Gemini CLI** — 16 PRs focused on security (env var sanitization, symlink dedup, NTFS short names, SSRF validation) and documentation. The security-focused iteration suggests the project is maturing its trust surface.

**Steady iteration, enterprise pace:**
- **Claude Code** — 4 PRs, one major closed issue (AGENTS.md). The project is managing ecosystem-level standardization pressure while addressing regression fixes. Lower PR volume but higher-impact decisions.
- **OpenAI Codex** — 12 PRs with Vim-mode parity and rate-limit UX. Active feature work but overshadowed by 8–11× Windows performance regressions, indicating velocity is outpacing QA on platform-specific paths.

**Maintenance mode / transition:**
- **GitHub Copilot CLI** — 0 PRs, 10 hot issues, all tracing back to 1.0.81/82 regressions. The project is in a reactive triage posture; the 192-second ACP stall and unbounded billing retries are trust-damaging.
- **Kimi Code CLI** — Minimal activity (2 PRs, 3 issues). The project is in migration mode toward Kimi Code; community energy is shifting to the successor product.
- **Qwen Code** — Nightly build shipped with web-shell polish and review pipeline improvements. Active but focused on incremental refinement rather than breakthrough features.
- **OpenCode** — 10 PRs with browser plugin and CodeMode refactoring. Steady progress but no release this cycle; community pain points (Zen rate limits, infinite loops) suggest platform reliability gaps.

---

## 6. Trend Signals

**1. Session state is the new battleground.** Every tool community reports session-resume, context duplication, or state-loss bugs. Developers are running longer, multi-turn agent workflows, and the tools that guarantee deterministic session fidelity will earn trust. *Reference: Copilot CLI's 7+ resume regressions, Pi's fork races, Codewhale's session ID fix, Qwen Code's resume hazard.*

**2. Retry and cost accounting are trust risks.** Unbounded compaction retries burning paid model calls (Copilot CLI #4663), 72× under-reported budgets (Claude Code #83048), and unexplained quota depletion (Codex #40067) are creating financial risk without user visibility. Tools that surface bounded budgets and idempotent retries will differentiate.

**3. MCP is becoming production-critical but remains fragile.** OAuth token refresh gaps (Claude Code #65036), ACP startup stalls (Copilot CLI #4678), legacy handshake conflicts (Copilot CLI #4525), and missing pagination (Codex #28858) indicate the MCP ecosystem is still in its adolescence. Tools that harden MCP integration will reduce enterprise friction.

**4. Cross-agent standardization is converging on AGENTS.md.** Claude Code's community overwhelmingly voted for it (5,094 👍, issue closed). This signals a market expectation that tool-agnostic codebase descriptors will replace per-tool conventions — developers should plan for multi-tool interoperability.

**5. Platform-specific regressions are the #1 reliability killer.** Windows shell-execution latency (Codex 8–11×), GBK encoding (Kimi Code), Wayland browser failures (Gemini CLI), npm 11.11.6.0 script blocking (Pi), and TLS-inspecting proxy auth (Copilot CLI) show that cross-platform compatibility is where bugs hide. Multi-platform QA investment is underpricing relative to user impact.

**6. Subagent architecture needs correctness guarantees.** Gemini CLI's subagents reporting false success, Pi's fork races, and Copilot CLI's lost agent config on resume all point to a common gap: subagent lifecycle management is not yet deterministic. Tools that formalize subagent contracts (commit/abort semantics, bounded turn limits, truthful status reporting) will lead.

**7. Security hardening is shifting from reactive to proactive.** Gemini CLI's env var sanitization, Codewhale's explicit credential consent, and NTFS short-name path traversal fixes show the ecosystem is moving toward defense-in-depth. Developers should expect stricter default security postures across tools.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-09-01 | Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

### 1. `skill-creator` — Evaluation & Pipeline Fixes
- **PR [#1298](https://github.com/anthropics/skills/pull/1298)** · Open · MartinCajiao
- **PR [#1099](https://github.com/anthropics/skills/pull/1099)** · Open · joshuawowk
- **PR [#1050](https://github.com/anthropics/skills/pull/1050)** · Open · gstreet-ops
- **Functionality:** The meta-skill that automates skill creation; its evaluation harness (`run_eval.py`) is fundamentally broken — it reports 0% recall on every description due to Windows subprocess crashes, unquoted YAML parsing failures, and trigger-detection bugs.
- **Status:** Multiple open fixes converge on the same root cause. PR #1298 is the umbrella fix; #1099 and #1050 are Windows-specific sub-fixes.

### 2. `testing-patterns` — Comprehensive Testing Framework
- **PR [#723](https://github.com/anthropics/skills/pull/723)** · Open · 4444J99
- **Functionality:** Covers the full testing stack — Testing Trophy model, AAA unit-test pattern, React component testing (Testing Library), edge-case guidance, and what *not* to test.
- **Status:** Open; widely anticipated as a first-class testing skill.

### 3. `claude-api` — Model Registry & Usage Guidance
- **PR [#1607](https://github.com/anthropics/skills/pull/1607)** · Open · adi-IL
- **Issue [#1487](https://github.com/anthropics/skills/issues/1487)** · Open · DaKev
- **Functionality:** Authoritative reference for Claude API model IDs, including legacy/deprecated listings. Users flag that the skill eagerly injects ~156k tokens, exhausting context in a single tool call.
- **Status:** PR #1607 is a small correctness update (marking 4 retired models); the token-bloat issue in #1487 remains open.

### 4. `document-typography` — Typographic Quality Control
- **PR [#514](https://github.com/anthropics/skills/pull/514)** · Open · PGTBoos
- **Functionality:** Detects and prevents orphan words, widow paragraphs, and numbering misalignment in AI-generated documents — a quality layer for any prose/document output.
- **Status:** Open; addresses a universally felt pain point with no existing skill coverage.

### 5. `hivemind` — Zero-Cost Multi-Agent Orchestration
- **PR [#1628](https://github.com/anthropics/skills/pull/1628)** · Open · Hanishchow
- **Functionality:** Delegates mechanical work to headless [opencode](https://opencode.ai) workers running on free models while Claude Code remains the sole planner/reviewer/merger.
- **Status:** Open; novel approach to cost-aware multi-agent scaling.

### 6. `odt` — OpenDocument Format Skill
- **PR [#486](https://github.com/anthropics/skills/pull/486)** · Open · GitHubNewbie0
- **Functionality:** Create, fill, read, and convert `.odt`/`.ods`/`.odf` files, including OpenDocument-to-HTML parsing.
- **Status:** Open; fills the gap left by the existing DOCX and PDF skills.

### 7. `service-now` — Enterprise IT Platform Skill
- **PR [#568](https://github.com/anthropics/skills/pull/568)** · Open · Vanka07
- **Functionality:** Broad ServiceNow platform assistant covering ITSM, ITOM, ITAM/SAM, FSM, HRSD, CSM, SPM/PPM, Vulnerability Response, Security IR, and IntegrationHub.
- **Status:** Open; represents enterprise-platform demand.

### 8. `skill-quality-analyzer` & `skill-security-analyzer`
- **PR [#83](https://github.com/anthropics/skills/pull/83)** · Open · eovidiu
- **Functionality:** Meta-skills that evaluate skills across five quality dimensions (20% each: Structure & Documentation, Examples, Triggers, Resource Usage, Error Handling) and security posture.
- **Status:** Open; directly supports the self-audit workflow proposed in Issue #1385.

---

## 2. Community Demand Trends

Analysis of open Issues reveals four dominant demand vectors:

| Trend | Signal | Representative Issue |
|---|---|---|
| **Trust & security governance** | Highest comment volume (43) | [#492](https://github.com/anthropics/skills/issues/492) — namespace impersonation attacks |
| **Org-wide sharing & collaboration** | 16 comments, 8 👍 | [#228](https://github.com/anthropics/skills/issues/228) |
| **Testing & quality gates** | 2 issues, 1 proposal | [#723](https://github.com/anthropics/skills/pull/723), [#1385](https://github.com/anthropics/skills/issues/1385) |
| **Enterprise / platform skills** | 3+ PRs (ServiceNow, HPC, SharePoint) | [#568](https://github.com/anthropics/skills/pull/568), [#1615](https://github.com/anthropics/skills/pull/1615), [#1175](https://github.com/anthropics/skills/issues/1175) |

Additional signal: users want skills that **audit output before delivery** (#1367, #1385), and are actively proposing compact state-management (#1329) and agent-governance (#412) patterns.

---

## 3. High-Potential Pending Skills

These PRs are open, have substantive community engagement, and address clear gaps:

| Skill | PR | Why It Could Land |
|---|---|---|
| **Hivemind** — multi-agent cost orchestration | [#1628](https://github.com/anthropics/skills/pull/1628) | Novel architecture; directly addresses token-cost concerns |
| **HPC cluster skill (SCNet)** | [#1615](https://github.com/anthropics/skills/pull/1615) | Fills a niche (HPC/Slurm) with no existing coverage |
| **Self-audit / reasoning quality gate** | [#1367](https://github.com/anthropics/skills/pull/1367) | Aligns with the v1.3.0 pipeline proposal in Issue #1385 |
| **Evaluation harness fixes** | [#1602](https://github.com/anthropics/skills/pull/1602) | Critical infrastructure; without it, skill evaluation is unreliable |
| **Frontend-design clarity improvement** | [#210](https://github.com/anthropics/skills/pull/210) | Hardens an existing popular skill rather than adding a new one |
| **Compact-memory skill** | [#1329](https://github.com/anthropics/skills/issues/1329) (issue-proposal) | Solves long-running agent context bloat; author has prior repo engagement |

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **trustworthy evaluation and governance tooling** — not more raw capabilities, but the plumbing (self-audit, quality gates, security analysis, correct eval harnesses) that makes adding and distributing new Skills safe and reliable at scale.

---



# Claude Code Community Digest — 2026-09-01

## Today's Highlights

Anthropic shipped **v2.1.252**, fixing a macOS Bash "task output swap refused" crash, a broken "always allow" persistence bug, and Remote Control session stalls. The community remains overwhelmingly focused on the push for **AGENTS.md standardization** (#6235, 5,094 👍), which is now closed after driving significant platform discussion, while Fable 5 safeguard regressions are causing fresh friction for active users.

---

## Releases

**v2.1.252** — [GitHub](https://github.com/anthropics/claude-code)
- Fixed Bash commands failing with *"task output swap refused (tasks dir moved or linked)"* on certain Macs
- Fixed "always allow" permission decisions not persisting in projects lacking a `.claude/settings.local.json`
- Fixed Remote Control sessions hosted by Claude Desktop or VS Code stalling for a minute

---

## Hot Issues

### 1. Support AGENTS.md — *CLOSED · 389 comments · 5,094 👍*
[#6235](https://github.com/anthropics/claude-code/issues/6235)
Codex, Amp, and Cursor are converging on AGENTS.md as a cross-agent codebase descriptor. The community overwhelmingly wants Claude Code to adopt it instead of treating `CLAUDE.md` as the sole standard. This issue's massive engagement signals a major ecosystem expectation.

### 2. CVP-approved orgs still hit cyber-safeguard blocks — *OPEN · 168 comments · 25 👍*
[#84352](https://github.com/anthropics/claude-code/issues/84352)
Organizations with Cyber Verification Program approval continue receiving blocks in Claude Code. The Verification Portal shows "Under review" despite prior approval emails, creating a trust gap for enterprise users.

### 3. Sync Skills between Claude Desktop and Claude Code CLI — *OPEN · 43 comments · 150 👍*
[#20697](https://github.com/anthropics/claude-code/issues/20697)
Users want Skill configurations to stay in sync across Desktop and CLI environments, avoiding duplication and inconsistency. A clean cross-platform experience is a recurring theme.

### 4. Programmatically rename sessions — *CLOSED · 15 comments · 92 👍*
[#29355](https://github.com/anthropics/claude-code/issues/29355)
Agents should auto-rename sessions when a ticket ID (e.g., `TICKET-123`) is mentioned, eliminating manual `/rename` calls. The closure suggests a built-in solution may have shipped.

### 5. Cross-platform sync failure causing conversation disappearance — *OPEN · 14 comments · 4 👍*
[#81658](https://github.com/anthropics/claude-code/issues/81658)
Cowork conversations and chats are disappearing across Desktop/Web/Android, suspected server-side incident. Critical for users relying on cloud-synced sessions.

### 6. Fable 5 `reasoning_extraction` false-positive on one-word greeting — *OPEN · 12 comments · 14 👍*
[#87640](https://github.com/anthropics/claude-code/issues/87640)
Fable 5 returns a safeguard error for the word "Hi," flagging it as chain-of-thought extraction. Indicates the classifier is oversensitive and needs tuning.

### 7. MCP OAuth access tokens not auto-refreshed — *OPEN · 10 comments · 34 👍*
[#65036](https://github.com/anthropics/claude-code/issues/65036)
Daily "Connection expired" errors despite valid refresh tokens. Affects every MCP-connected workflow and signals a gaps in the OAuth lifecycle.

### 8. Cloud Cowork OTLP telemetry missing identity attributes — *OPEN · 7 comments · 19 👍*
[#88490](https://github.com/anthropics/claude-code/issues/88490)
Since ~Aug 18, 2026, cloud-run Cowork sessions export traces with no `user.email`, `account_uuid`, or `organization.id`. Blocks observability for platform users.

### 9. Fable 5 `reasoning_extraction` regression blocks 100% of sessions — *OPEN · 2 comments · 0 👍*
[#90922](https://github.com/anthropics/claude-code/issues/90922)
Since ~Aug 30, a regression causes every session in a multi-session monitoring repo to be blocked. A sharper, more disruptive variant of #87640.

### 10. `bypassPermissions` silently downgraded to Manual in daemon sessions — *OPEN · 1 comment · 1 👍*
[#80412](https://github.com/anthropics/claude-code/issues/80412)
On Windows, daemon-dispatched sessions always land in Manual mode despite `bypassPermissions` being set. Detaching/reattaching an interactive session also strips bypass. A consistent permission-gate bug.

---

## Key PR Progress

### #75541 — fix(sweep): paginate issue events and honor unlabeled
[CLOSED](https://github.com/anthropics/claude-code/pull/75541)
Fixes the sweep script's `closeExpired()` to properly paginate GitHub events and respect the `unlabeled` event when determining when lifecycle labels were applied.

### #75537 — fix(hook-development): recognize all five hook handler types
[CLOSED](https://github.com/anthropics/claude-code/pull/75537)
Closes the gap where the plugin-dev skill only knew two of five supported hook handler types, correcting both the docs and the bundled validator.

### #75529 — docs(code-review plugin): clarify relationship to bundled /code-review skill
[CLOSED](https://github.com/anthropics/claude-code/pull/75529)
Clarifies that the `code-review` plugin (PR review via `gh`) is distinct from the bundled `/code-review` skill (local working-diff review), and namespaces the plugin command to avoid collision.

### #89404 — validate-agent.sh: don't abort at first warning
[OPEN](https://github.com/anthropics/claude-code/pull/89404)
Fixes a `set -euo pipefail` interaction in the plugin-dev skill's validation script where `((warning_count++))` would abort on the first warning instead of collecting them. Addresses [issue #83803](https://github.com/anthropics/claude-code/issues/83803).

---

## Feature Request Trends

1. **Cross-agent standardization (AGENTS.md)** — The dominant request. The community wants a unified `.md` convention that works across Claude Code, Codex, Cursor, and Amp, reducing fragmentation.
2. **Programmatic session control** — Multiple open and closed issues (#29355, #75733) request the ability to rename, manage, and audit sessions via tools/hooks, enabling agent-driven workflows tied to ticketing systems.
3. **MCP ecosystem expansion** — Gmail file-attachment support (#28575) and robust OAuth token refresh (#65036) show the community is pushing MCP beyond read-only, single-purpose connectors toward production-grade integrations.
4. **Cross-platform session sync** — Skills syncing (#20697) and conversation continuity (#81658) reflect demand for a seamless experience across Desktop, CLI, Web, and mobile.
5. **Permission mode reliability** — `bypassPermissions` inconsistencies (#86478, #80412) and the auto-mode rollout regression suggest users want permission configuration to be deterministic and respect explicit user intent.

---

## Developer Pain Points

- **Auth and OAuth fragility:** MCP OAuth tokens aren't auto-refreshed (#65036), and logging out/switching accounts discards all grants (#90647). Connection drops (#87500) and CVP block mismatches (#84352) compound trust issues for enterprise users.
- **Safeguard false positives:** Fable 5's `[reasoning_extraction]` guard is blocking legitimate sessions, including single-word greetings (#87640) and causing 100% session blockage in a regression (#90922).
- **Permission mode unreliability:** `bypassPermissions` is being ignored or silently downgraded in daemon and detached sessions (#86478, #80412), forcing users into Manual mode despite explicit configuration.
- **macOS Bash and sandbox issues:** The v2.1.252 fix addresses a recurring "task output swap refused" error (#86000 context), and Tahoe 26.x `EPERM` in `~/Documents` (#58952) continues to disrupt terminal process trees.
- **Cost accounting failures:** A SEV-1 report (#83048) shows `budget.spent()` under-reporting by 72×, which could cause budget overruns without user awareness.
- **Cowork observability gaps:** Missing identity attributes in OTLP telemetry (#88490) and cross-platform session disappearance (#81658) make it hard to debug or audit multi-session workflows.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-01

## 1. Today's Highlights

Codex CLI **v0.152.0** shipped with Vim-mode search and navigation in drafts, actionable rate-limit banners, and terminal UI improvements. Meanwhile, the community surfaced significant concerns around **Windows shell-execution latency regressions (8–11×)**, **pro-rated quota depletion bugs**, and **auth-loop failures** on both Windows and macOS, drawing strong engagement across multiple open issues.

---

## 2. Releases

- **rust-v0.152.0** — [GitHub](https://github.com/openai/codex/releases)
  - Vim mode: `/` and `?` search within drafts, highlighted matches, repeat navigation with `n`/`N` (#41586)
  - Rate-limit banners now expose actionable links for usage checks, credit management, limit resets, and plan changes (#41742)
  - Terminal UI and `codex exec` improvements (summary truncated in source)

- **rust-v0.152.0-alpha.7.2** and **v0.152.0-alpha.7** — [GitHub](https://github.com/openai/codex/releases)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#25828](https://github.com/openai/codex/issues/25828) | Phone verification bug — unable to send codes to any number | Blocks login entirely for affected users; spans months without resolution | 31 comments · 5 👍 |
| [#27117](https://github.com/openai/codex/issues/27117) | Windows standalone update inherits PSModulePath into `powershell.exe`, breaking `Get-FileHash` | Update failures on Windows; cross-shell environment pollution | 26 comments · 18 👍 |
| [#41290](https://github.com/openai/codex/issues/41290) | Project creation/removal fails after switching Agent Environment to WSL on Windows | Blocks WSL workflow; affects Pro subscribers | 21 comments · 8 👍 |
| [#41059](https://github.com/openai/codex/issues/41059) | Desktop remains headless after external Codex CLI workaround | Regression from workaround; usability impact on Windows | 16 comments |
| [#39678](https://github.com/openai/codex/issues/39678) | Remote Android→macOS "No project" chat fails with trust error | Remote workflow broken; project trust validation issue | 14 comments · 10 👍 |
| [#41513](https://github.com/openai/codex/issues/41513) | Floating pets become click-through and undraggable on Windows | Polish regression; pets unresponsive since update | 13 comments · 2 👍 |
| [#41241](https://github.com/openai/codex/issues/41241) | Windows local tool host exits during handshake after update | Tool-calls broken post-update; affects GPT-5.6 exec paths | 12 comments |
| [#41472](https://github.com/openai/codex/issues/41472) | Non-image attachments rejected; long pasted instructions freeze composer on Windows | Two composer bugs: file-type filtering and paste-handler freeze | 9 comments |
| [#40067](https://github.com/openai/codex/issues/40067) | Weekly usage drained from ~99% to 0% within hours — possible usage accounting regression | Billing/credit integrity concern for Plus subscribers | 8 comments · 2 👍 |
| [#41942](https://github.com/openai/codex/issues/41942) | Shell execution latency regressed 8–11× on Windows between v0.146.0 and v0.151.0-alpha | Major perf regression impacting all CLI workflows; measured over 10 months | 6 comments |

---

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#41974](https://github.com/openai/codex/pull/41974) | Track TUI starts by app server mode | Emit `codex.tui.start` counter once per launch with `app_server_mode` label (`in_process`/`local_daemon`/`remote`); prevents reconnects from inflating launch metrics |
| [#41953](https://github.com/openai/codex/pull/41953) | Enforce marketplace source policy for curated plugins | Extends marketplace source restrictions to cover curated plugins backed by the OpenAI plugins repo, not just user-configured marketplaces |
| [#41950](https://github.com/openai/codex/pull/41950) | Improve tracing for nested tool calls and exec processes | Preserves execution context for code-mode callbacks that outlive their initial request; adds spans for nested calls |
| [#41949](https://github.com/openai/codex/pull/41949) | Add plugin reconciliation app-server API | New `plugin/reconcile` JSON-RPC method synchronizes installed remote plugin bundles and waits for hook updates; returns affected plugin IDs with refresh hints |
| [#41946](https://github.com/openai/codex/pull/41946) | Expand extension permission regression coverage | Verifies image-gen extensions rebind permissions per turn; covers executor skill reference reads under current filesystem permissions including paginated reads |
| [#41944](https://github.com/openai/codex/pull/41944) | Emit turn cost telemetry for ChatGPT sessions | Queries workspace-visible turn estimates and emits `codex.turn.cost_microusd` when the estimate is non-negative and visible |
| [#41941](https://github.com/openai/codex/pull/41941) | Add Vim undo to the TUI composer | Bounded, draft-level Vim undo history with `u`; restores complete draft state (attachments, mentions, deferred pastes) as a single edit |
| [#41940](https://github.com/openai/codex/pull/41940) | Preserve transcript layout caches during backtrack selection | Rerenders only the pre-selected portion of the transcript instead of rebuilding all renderables on each selection change |
| [#41938](https://github.com/openai/codex/pull/41938) | Clarify resume guidance in exit summaries | Shows exact `codex resume <thread-id>` command on its own line; explains named-thread picker when applicable; applies command highlighting |
| [#41937](https://github.com/openai/codex/pull/41937) | Limit background terminal input previews | Caps inline input previews at 12 rendered rows and 64 KiB of processing; shows a transcript hint when truncated |

---

## 5. Feature Request Trends

- **Vim-mode parity in TUI** — Multiple PRs landed this cycle (#41941, #41921) adding undo, Insert-mode defaults, and search navigation, responding to sustained community demand for vim-like drafting.
- **Cross-thread / sub-agent orchestration** — Issue #30499 requests explicit non-interrupt queued delivery for `send_message_to_thread`, reflecting a need for parent/worker thread coordination patterns.
- **Session recovery & durability** — Issue #40779 calls for a first-party conversation recovery/reindex tool on Windows, and #38631 asks for message bookmarks in the minimap, both pointing to a desire for better long-session navigability.
- **MCP pagination support** — Issue #28858 highlights the absence of `nextCursor` pagination in MCP `tools/list`, a recurring request from MCP-power-users.
- **Rate-limit transparency** — Issue #41969 and #40067 reflect demand for clearer usage accounting and proactive quota notifications.

---

## 6. Developer Pain Points

- **Windows performance regressions** dominate complaints: an 8–11× shell-execution latency regression (#41942), path-normalization bugs in WSL (#41463, #40100), and `PSModulePath` inheritance breaking updates (#27117) form a cluster of Windows-specific friction.
- **Auth & session reliability** — Phone verification lockouts (#25828), auth loops on macOS (#41044), and refresh-token revocation after login (#41973) indicate ongoing instability in the authentication surface.
- **Usage/accounting anomalies** — Multiple reports of unexplained quota depletion (#40067, #41969) and misrouted tasks burning Codex allowance instead of ChatGPT Work credits (#41965) erode trust in billing integrity.
- **Remote & WSL workflows** — Project creation failures after environment switches (#41290), Android remote-control timeouts (#36416), and path-deserialization bugs (#41463) make cross-platform development painful.
- **Long-running task fragility** — Tasks failing mid-execution with capacity errors and no graceful recovery (#41810, #41808) disrupt workflows that depend on extended Codex sessions.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-01

---

## 1. Today's Highlights

Gemini CLI v0.59.0-nightly is live, bringing continued focus on agent reliability, security hardening, and tooling robustness. The community is actively reporting agent-level issues—particularly around subagent hang/recognition and shell execution stalls—while a cluster of security-focused PRs addresses environment variable sanitization, configuration path validation, and symlink handling across the codebase.

---

## 2. Releases

**v0.59.0-nightly.20260901.g0bd1d4397**
Automated nightly release. Changelog: [v0.59.0-nightly.20260831 → v0.59.0-nightly.20260901](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260831.g0bd1d4397...v0.59.0-nightly.20260901.g0bd1d4397)

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | The `codebase_investigator` subagent incorrectly returns `status: "success"` with `Termination Reason: GOAL` even when it hits the turn limit before completing analysis, silently masking failures. | 13 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | The generalist agent hangs forever on simple tasks (e.g., folder creation) when deferring to sub-agents; disabling sub-agent use resolves it. | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model's bash affinity via OS sandboxing | Proposes zero-dependency OS sandboxing and post-execution intent routing to let Gemini 3 models use native bash chains (`grep`, `sed`, `awk`) securely. | 8 comments · 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and codebase mapping | Epic tracking whether AST-aware tools can reduce turn count by precisely reading method bounds and navigating code more efficiently. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Users report that custom skills and sub-agents are barely invoked unless explicitly instructed, even for highly related tasks. | 6 comments · 0 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Auto Memory redaction and logging reduction | Auto Memory reads transcripts and sends content to the extraction agent before redaction occurs; secrets may already be in model context. | 5 comments · 0 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck at "Waiting input" after completion | Simple, non-interactive CLI commands cause the agent to hang showing "Awaiting user input" even after the command finishes. | 4 comments · 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent session takeover and lock recovery | Browser agent uses a restrictive fail-fast strategy on locked profiles instead of attempting automatic session recovery. | 4 comments · 0 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | The browser subagent terminates with `GOAL` on Wayland sessions, blocking browser automation for Linux users. | 4 comments · 1 👍 |
| [#22186](https://github.com/google-gemini/gemini-cli/issues/22186) | get-shit-done output hook crash | The `get-shit-done` hook crashes Gemini CLI when the user summary is almost complete. | 3 comments · 0 👍 |

---

## 4. Key PR Progress

| # | PR | Description |
|---|-----|-------------|
| [#29022](https://github.com/google-gemini/gemini-cli/pull/29022) | feat(tool): retain ask_user question in text history | Introduces `ui.keepAskUserQuestionsInHistory` so answered questions persist in session history for review and resumption. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | fix(extensions): prompt for consent on env changes | Closes a security gap where extension updates could bypass consent and inject unauthorized env vars into MCP server processes. |
| [#28866](https://github.com/google-gemini/gemini-cli/pull/28866) | fix(core): ignore `.gemini` folder in file search | Adds `.gemini` to default ignored directories, preventing chokidar watchers and crawlers from indexing config directories. |
| [#29017](https://github.com/google-gemini/gemini-cli/pull/29017) | fix(core): dedupe symlinked/junctioned skill dirs | Fixes duplicate skill discovery when `.gemini` is symlinked or junctioned (e.g., Windows `mklink /J`). |
| [#29013](https://github.com/google-gemini/gemini-cli/pull/29013) | docs: document missing CLI flags | Adds six undocumented flags to the CLI reference: `--policy`, `--admin-policy`, `--session-id`, `--session-file`, `--raw-output`, `--accept-raw-output-risk`. |
| [#29011](https://github.com/google-gemini/gemini-cli/pull/29011) | docs: fix ACP flags in CLI reference | Corrects a stale flag, a wrong ACP acronym expansion, and a missing `--acp` entry. |
| [#29009](https://github.com/google-gemini/gemini-cli/pull/29009) | docs: correct env var redaction setting keys | Fixes documentation to match the actual schema keys for environment variable redaction. |
| [#29008](https://github.com/google-gemini/gemini-cli/pull/29008) | fix(core): strip execution-affecting GIT_* env vars | Closes a security issue where loaded `.env` files could inject unsafe git env vars into subprocess calls. |
| [#29004](https://github.com/google-gemini/gemini-cli/pull/29004) | fix(core): guard formatTruncatedToolOutput | Prevents output inflation when `maxChars` is 0 or negative, which previously caused `slice()` to duplicate output ~2×. |
| [#29116](https://github.com/google-gemini/gemini-cli/pull/29116) | fix(core): mitigate NTFS 8.3 short name path traversal | Hardens path validation against Windows short names (`git~1`, `node_m~1`) in both normalization and the AllowedPathChecker. |
| [#29120](https://github.com/google-gemini/gemini-cli/pull/29120) | fix(core): improve web fetch destination validation | Adds async DNS resolution and Undici transport binding to validate outbound request destinations and prevent SSRF-adjacent issues. |
| [#29148](https://github.com/google-gemini/gemini-cli/pull/29148) | fix(cli): prevent background git from hijacking stdin | Fixes background `git.listRemote`/`git.clone` operations from blocking on interactive terminal prompts when credentials are challenged. |
| [#29115](https://github.com/google-gemini/gemini-cli/pull/29115) | fix(config): enforce strict permission/ownership on system-wide config | Validates file ownership and ACLs on system-wide config paths on both Windows and POSIX before loading. |
| [#29118](https://github.com/google-gemini/gemini-cli/pull/29118) | fix(extensions): only strip trailing `.git` suffix | Fixes GitHub repo name parsing so internal `.git` strings (e.g., `blog.github.io`) are preserved. |
| [#29005](https://github.com/google-gemini/gemini-cli/pull/29005) | fix(sandbox): normalize DEBUG env var truthiness | Prevents string values like `"false"` and `"0"` from inadvertently enabling debug features (port publishing, `--inspect-brk`) in Docker/Podman. |

---

## 5. Feature Request Trends

- **Smarter agent utilization** — Users consistently want the model to use custom skills, sub-agents, and its own bash-native capabilities without explicit prompting (#19873, #21968).
- **AST-aware codebase tools** — Interest in precision file reads and codebase mapping via AST parsing to reduce token waste and improve turn efficiency (#22745, #22746).
- **Resilient browser agent** — Requests for automatic session recovery, lock handling, and cross-platform support (Wayland) (#22232, #21983).
- **Memory system hardening** — Desire for deterministic redaction, low-signal session pruning, and visible invalid patch quarantine in Auto Memory (#26525, #26522, #26523, #26516).
- **Session continuity** — Keeping `ask_user` questions and subagent trajectories in history for easier review and sharing (#29022, #22598).

---

## 6. Developer Pain Points

1. **Agent reliability** — Subagents frequently hang, report false success, or fail to activate without explicit instruction. This is the dominant complaint across multiple high-comment issues.
2. **Shell execution stalls** — Commands that should complete non-interactively cause the CLI to wait for input indefinitely (#25166), breaking workflow automation.
3. **Security surface from env vars** — Loaded `.env` files and extension updates can inject or leak environment variables into sensitive subprocess contexts, driving multiple security-focused fixes.
4. **Platform-specific browser failures** — Wayland support is broken for the browser agent, and persistent session locking causes fail-fast behavior instead of recovery.
5. **Configuration edge cases** — Symlinked agent directories, NTFS short names, `.git` suffix parsing, and system-wide config permissions all produce subtle bugs that erode trust in edge-case scenarios.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-01

## 1. Today's Highlights

Copilot CLI v1.0.83-0 ships with mTLS proxy certificate support and herdr terminal multiplexer detection, but the release cycle is overshadowed by a wave of session-resume regressions and MCP initialization failures introduced in 1.0.81/82. The community is flagging unbounded billing from retry loops and a 192-second session-creation stall as the most urgent reliability concerns.

---

## 2. Releases

### v1.0.83-0
- **Added:** Automatic HTTPS proxy mTLS client certificate support for model and web requests.
- **Added:** Detection of the `herdr` terminal multiplexer (previously mistaken for `tmux`), enabling Kitty keyboard protocol, color-scheme following, terminal progress, `/copy`, and notifications in herdr panes.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4663](https://github.com/github/copilot-cli/issues/4663) | Failed compaction retried unchanged — unbounded billed retries | Every retry is a full paid model call with no backoff or payload reconciliation, causing monotonic context growth and runaway costs. | Critical — no upvotes yet but severity is high; author is a Microsoft employee. |
| [#4678](https://github.com/github/copilot-cli/issues/4678) | ACP `session/new` blocks 192s on unresponsive MCP server | Three connection attempts at ~59s each with no bounded startup budget make ACP mode unusable with slow HTTP MCP servers. | Triage — needs a configurable timeout. |
| [#4673](https://github.com/github/copilot-cli/issues/4673) | Session restore auto-continues work the user aborted | The `working` flag is only cleared on `session.idle`, not on user abort, trapping loop-prone models in infinite loops on resume. | Triage — breaking workflow for interrupted sessions. |
| [#4674](https://github.com/github/copilot-cli/issues/4674) | Resuming a session does not restore the custom agent | A regression of #917: `mcp-servers:` and `tools:` allow-lists are not reapplied on resume, so sessions silently run without their configured agent. | Triage — directly impacts agent-based workflows. |
| [#4672](https://github.com/github/copilot-cli/issues/4672) | `/model` command broken with BYOK (1.0.82 regression) | Users who set models via environment variables can no longer switch models interactively, breaking BYOK workflows on multi-model backends like Azure AI Foundry. | Created today — fast-tracked for triage. |
| [#4525](https://github.com/github/copilot-cli/issues/4525) | 1.0.81-1 sends legacy `initialize` after successful `server/discover` | Breaks MCP compatibility with Python MCP SDK 2.0.0 dual-era runners; the modern probe succeeds but is followed by a conflicting legacy handshake. | Open since Aug 19 — 3 comments, signals a protocol incompatibility. |
| [#4671](https://github.com/github/copilot-cli/issues/4671) | OAuth login fails behind TLS-inspecting proxy (1.0.81 regression) | Both device-code and web flows fail when corporate proxies inspect TLS, a regression from 1.0.80. mTLS support in 1.0.83-0 may address this. | Open — 1 👍; affects enterprise users heavily. |
| [#4664](https://github.com/github/copilot-cli/issues/4664) | Heap OOM when resuming a long-standing session | V8 hits ~heap exhaustion during session load, making it impossible to resume. No workaround for users with large session history. | Open — blocking for power users. |
| [#4668](https://github.com/github/copilot-cli/issues/4668) | Interrupted `create_session` creates the session ~1.6h later | A delayed session kickoff silently duplicates agent work after the agent already completed the task itself. | Open — causes unexpected costs and duplicated output. |
| [#4665](https://github.com/github/copilot-cli/issues/4665) | `sessionStart` additionalContext duplicated on each turn | Every prompt reinjects the same context, inflating token usage and potentially exceeding context limits over time. | Open — impacts all hook-based session customization. |

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **Session reliability and resumption fidelity** — Users consistently report that resuming sessions loses agent configuration, duplicates context, or auto-resumes aborted work. The community wants session state to be fully deterministic and idempotent.
- **Bounded MCP startup and retry budgets** — The 192-second ACP stall and unbounded compaction retries both point to a need for configurable timeouts, backoff strategies, and circuit breakers around external service calls.
- **BYOK and enterprise proxy support** — Broken `/model` switching and OAuth failures behind TLS-inspecting proxies suggest enterprise deployments need more robust authentication and model-routing paths that don't depend on direct internet egress.
- **Context budget visibility** — Issue #1953 (9 👍) requests a permanent context-window indicator, reflecting growing awareness that silent context growth degrades LLM performance and increases cost.
- **Terminal multiplexer parity** — The herdr detection fix in 1.0.83-0 reflects ongoing demand for parity across less-common terminals (Kitty protocol, notifications, `/copy`).

---

## 6. Developer Pain Points

1. **Regression surface in 1.0.81/82** — At least seven open issues trace back to the 1.0.81 release, spanning OAuth, `/model`, MCP initialization, session resume, and agent restoration. The velocity of new bugs in a single patch release is eroding trust.
2. **Unbounded costs from retry loops** — Failed compaction retries (#4663) and duplicate session creation (#4668) both burn billed model calls without user-visible error or backoff, creating financial risk.
3. **Session state is fragile** — Custom agents, MCP servers, and context injections are lost or duplicated on resume. For users running long-running agent workflows, this is a reliability blocker.
4. **Enterprise network compatibility** — TLS-inspecting proxies and OAuth metadata paths with segments (#4662) continue to trip up corporate deployments, suggesting the auth stack needs more resilient discovery logic.
5. **Memory pressure on long sessions** — Heap OOM on session resume (#4664) indicates that session serialization or context accumulation lacks memory-aware bounds, penalizing power users the most.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-01

---

## 1. Today's Highlights

Two open PRs landed over the weekend: a bug fix that prevents `StrReplaceFile` from silently mangling files when given an empty search string, and a migration flow that auto-detects the Kimi CLI deprecation notice and guides users toward Kimi Code with a one-key transition. On the issue side, a Windows-specific encoding bug (`GBK` codec error) remains open, highlighting ongoing cross-platform compatibility work.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**#2629 — UnicodeEncodeError on Windows (GBK codec)** [OPEN] | 👍 0 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/2629)
> Running Kimi Code CLI v1.49.0 with model K2.7 Code on Windows 10 triggers a `UnicodeEncodeError` when output contains the character `\u0133`. This is a high-impact cross-platform issue affecting non-Latin script users on Windows and reflects a recurring pain point around default stdout encoding assumptions.

**#1287 — Unable to write next-task prompt while current task executes** [CLOSED] | 👍 0 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/1287)
> Users reported that the prompt input for subsequent tasks in a sequence is locked until the current task completes. Closed on 2026-09-01, suggesting a fix was shipped. This feature gap was notable for power users running multi-step automation workflows.

**#1292 — Task sub-tasks sometimes get stuck** [CLOSED] | 👍 0 | [Link](https://github.com/MoonshotAI/kimi-cli/issues/1292)
> Reports of the CLI hanging when invoking Task sub-tasks, with multiple sub-tasks potentially blocked simultaneously. Closed on 2026-09-01. This is significant for users relying on multi-step task orchestration, as silent hangs degrade trust in automated workflows.

---

## 4. Key PR Progress

**#2631 — fix(file): reject empty old string in StrReplaceFile** [OPEN] | [Link](https://github.com/MoonshotAI/kimi-cli/pull/2631)
> Prevents `StrReplaceFile` from silently inserting `new` text at the beginning of a file (or between every character with `replace_all=True`) when the `old` search string is empty. A malformed edit previously reported success, making this a quiet data-integrity fix that protects agents from self-inflicted corruption.

**#2630 — feat(shell): deprecation-aware update flow with one-key migration to Kimi Code** [OPEN] | [Link](https://github.com/MoonshotAI/kimi-cli/pull/2630)
> When the CDN publishes a deprecation/migration notice at `cdn.kimi.com/kimi-code-tips/kimi_cli/migration.json`, the CLI treats its own Python release as deprecated and drives a guided migration to Kimi Code. This PR is central to the sunset transition from `kimi-cli` to the new Kimi Code product line, reducing friction for the existing user base.

---

## 5. Feature Request Trends

- **Multi-step task orchestration UX** — Issues #1287 and #1292 both point to rough edges in sequential task execution (locked inputs, hanging sub-tasks). The community is clearly using the CLI for longer chains and needs those chains to be more responsive and resilient.
- **Cross-platform encoding robustness** — Issue #2629 underscores that Windows users remain underserved on the encoding front. Expect continued requests for explicit UTF-8 stdout/stderr handling across platforms.
- **Migration clarity** — PR #2630 signals an active product transition; the community will likely generate follow-up requests around migration edge cases, feature parity mapping, and backward-compatible workflows.

---

## 6. Developer Pain Points

| Pain Point | Frequency Signal |
|---|---|
| **Windows encoding errors** (`GBK` / non-Latin characters) | 1 open issue; historically recurring |
| **Task sub-system stability** (hanging, blocking) | 2 closed issues referencing sub-task stalls |
| **Sequential task input UX** (locked prompt fields) | 1 closed issue; indicates power-user workflow friction |
| **Migration uncertainty** (kimi-cli → Kimi Code) | 1 active PR; community will surface more as the cutoff approaches |
| **Silent tool failures** (StrReplaceFile with empty inputs) | 1 closed-bug precursor; reflects a pattern where bad agent inputs go unchecked |

---

*Digest generated from public GitHub data for `github.com/MoonshotAI/kimi-cli`. All timestamps reflect activity within the 24 hours prior to 2026-09-01.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-09-01

## 1. Today's Highlights

The most-discussed issue this cycle (#8003) remains a top community ask for VS Code diff-preview integration when reviewing code changes in the TUI. On the PR side, three back-to-back contributions landed around CodeMode catalog refactoring (schema comments, nested catalog) and the experimental `browser` plugin reached public API status. Session-message styling and a renderer fix for large diffs also moved forward.

---

## 2. Releases

No releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#8003](https://github.com/anomalyco/opencode/issues/8003) | VS Code Integration for Reviewing OpenCode Code Changes (Diff Preview) | 17 | 81 | The single highest-engagement issue in the dataset; users modifying large files find the TUI diff experience painful and want VS Code-style inline previews. |
| [#26459](https://github.com/anomalyco/opencode/issues/26459) | Clipboard copy fails in web-based VSCode terminals | 11 | 2 | Affects code-server, GitHub Codespaces, and Gitpod users—environments many teams depend on for remote development. |
| [#13318](https://github.com/anomalyco/opencode/issues/13318) | Keep getting rate limited on Zen | 11 | 2 | Zen (OpenCode's managed provider) users report rate limits even on paid plans, hurting reliability for Claude-based workflows. |
| [#26220](https://github.com/anomalyco/opencode/issues/26220) | OpenCode enters infinite loop after tool calls complete (Zen/big-pickle) | 10 | 4 | A correctness bug where the agent hangs and stops accepting input after tool execution—directly blocks productive use of managed models. |
| [#33632](https://github.com/anomalyco/opencode/issues/33632) | Crash when including a file with `@filename` | 6 | 1 | File inclusion via `@filename` crashes in certain directory structures, impacting reproducible session context. |
| [#29714](https://github.com/anomalyco/opencode/issues/29714) | Desktop GUI reopens session with wrong workspace path | 3 | 2 | Regression in desktop session persistence—selecting a different project still loads the previous workspace. |
| [#33126](https://github.com/anomalyco/opencode/issues/33126) | Local llama.cpp models extremely slow with session title generation | 3 | 0 | Self-hosted model users are penalized by default title-generation overhead; a configurable toggle is requested. |
| [#34984](https://github.com/anomalyco/opencode/issues/34984) | AsyncQueue leaks pending resolvers on abandoned iteration | 3 | 0 | Memory-leak bug in the `AsyncQueue` internal construct when consumers break early from `for await...of`. |
| [#34896](https://github.com/anomalyco/opencode/issues/34896) | Truncation cleanup failed: SyntaxError parsing BigInt | 4 | 0 | Crash in the context-truncation path when encountering an unparseable string; blocks long sessions. |
| [#35035](https://github.com/anomalyco/opencode/issues/35035) | OpenCode Go hangs forever after "build" on Windows | 4 | 0 | Windows users report indefinite hangs with multiple models (GLM-5.2, Qwen 3.6, DeepSeek V4) since a mid-July proxy change. |

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#46541](https://github.com/anomalyco/opencode/pull/46541) | refactor(core): nest code mode catalog | Refactor | Replaces sibling-namespace map with recursive `Tool \| Namespace` union; derives qualified paths at summarization time. |
| [#46542](https://github.com/anomalyco/opencode/pull/46542) | feat(codemode): label item and value schema comments | Feature | Uses readable labels above array/dict fields instead of comments embedded in type expressions. |
| [#46531](https://github.com/anomalyco/opencode/pull/46531) | feat(browser): add a public-API browser plugin | Feature | Experimental `browser` tool now available via public plugin interfaces; attachment state and RPC shared safely. |
| [#44838](https://github.com/anomalyco/opencode/pull/44838) | feat(desktop): connect browser pane through plugin RPC | Feature | Adds a Chromium-based browser pane to the desktop app with address bar and nav controls, wired to the new browser plugin. |
| [#46539](https://github.com/anomalyco/opencode/pull/46539) | fix(ai): preserve response reasoning items | Fix | Prevents flattening of summary arrays and preserves native fields required for continuation reasoning blocks. |
| [#46538](https://github.com/anomalyco/opencode/pull/46538) | Session message style | Styling | Adjusts message and text colours for a more distinctive TUI appearance. |
| [#46508](https://github.com/anomalyco/opencode/pull/46508) | fix(app): scope pane visibility to tabs | Fix | Terminal and review pane state is now persisted per-desktop-tab instead of globally. |
| [#46537](https://github.com/anomalyco/opencode/pull/46537) | fix(tui): show real duration for subagents over 60 minutes | Fix | Resolves a display bug where long-running subagent durations were computed incorrectly. |
| [#46534](https://github.com/anomalyco/opencode/pull/46534) | feat(core): add Firecrawl developer search provider | Feature | New `firecrawl-developer` provider queries the developer index (GitHub issues, PRs, READMEs, docs). |
| [#46530](https://github.com/anomalyco/opencode/pull/46530) | feat(plugin): expose permission assertions | Feature | Plugin API now exposes `ctx.permission.assert(input)` via Effect and Promise, reusing the existing permission engine. |

---

## 5. Feature Request Trends

1. **VS Code / IDE integration** — Issue #8003 dominates with 81 upvotes; the community clearly wants a richer in-editor diff and review experience alongside the TUI.
2. **Larger context-window variants** — Issue #46527 requests opt-in 1M-token variants for GPT-5.6 via OAuth, reflecting growing demand for extended context beyond defaults.
3. **Customizable UX controls** — Multiple requests for toggling session-title generation (#33126), disabling native menu accelerators (#34937), and folder-picker search (#35039) signal users want more granular control over the CLI and desktop experience.
4. **Plugin extensibility** — PRs #46531 and #46530 plus the browser-pane PR #44838 show the project is actively opening up the plugin API for new tool types.
5. **Search & discovery** — The Firecrawl developer provider PRs (#46534, #46512) indicate a push toward richer developer-centric web search within sessions.

---

## 6. Developer Pain Points

- **Zen / managed-provider reliability** — Rate limiting (#13318), infinite loops after tool calls (#26220), and a widespread proxy outage for DeepSeek via `opencode-go` (#34903, #35035) have all surfaced in the last week, creating friction for users relying on managed models.
- **Web-terminal clipboard failures** — Issue #26459 affects remote-workflow users on Codespaces, code-server, and Gitpod, a segment that grows as teams adopt cloud dev environments.
- **Desktop session-state regressions** — Wrong workspace path on reopen (#29714) and duplicate sessions on rapid Web UI submissions (#32541) suggest the desktop/gui session model has edge-case fragility.
- **Large-file performance** — Slow reads on massive files (#35044), 6–7s renderer freezes during diff computation (#32853), and the BigInt truncation crash (#34896) all point to bottlenecks when working with large codebases.
- **Billing / account issues** — Multiple closed issues (#46511, #46515, #46516) flagged subscription cancellations and perceived auto-renewal after bans, indicating a support gap around billing communication.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-01

---

## 1. Today's Highlights

The Pi team shipped several critical lifecycle fixes today, most notably a race condition where in-memory forks could steal in-flight tool results into the wrong session (PRs #8937, #8929). The parallel execution subsystem also received a fix to stop prepared tools from starting after a preflight abort (PR #8936). Two new inference providers — **CoralBricks** and **Melious** — joined the built-in catalog, alongside Fireworks GLM 5.3 model support and updated DeepSeek V4 pricing.

---

## 2. Releases

**No new releases in the last 24 hours.** The latest tracked version remains 0.84.4.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 |
|---|-------|--------|----------|----|
| [#8584](https://github.com/earendil-works/pi/issues/8584) | TUI row corruption during streaming: assistant text rendered one word per line after long tool output | ✅ CLOSED | 25 | 9 |
| [#5886](https://github.com/earendil-works/pi/issues/5886) | AgentSession settlement/continuation and assistant-tail lifecycle bugs | 🟢 OPEN | 10 | 4 |
| [#6600](https://github.com/earendil-works/pi/issues/6600) | `pi update --extensions` blocks npm scripts with new npm 11.16.0 | 🟢 OPEN | 5 | 0 |
| [#6552](https://github.com/earendil-works/pi/issues/6552) | Allow extensions to request a deferred canonical reload | 🟢 INPROGRESS | 5 | 1 |
| [#8134](https://github.com/earendil-works/pi/issues/8134) | Agent stops after the first tool call when a plain-HTTP provider is reached through a forward proxy | 🟢 OPEN | 5 | 0 |
| [#8884](https://github.com/earendil-works/pi/issues/8884) | Auto-compaction (`reserveTokens`) never checked mid-loop during long autonomous tool-calling sessions | ✅ CLOSED | 3 | 0 |
| [#8061](https://github.com/earendil-works/pi/issues/8061) | Context budget ignores maxTokens output reservation: 400 at 78% input, overflow recovery retry fails | 🟢 OPEN | 3 | 2 |
| [#8894](https://github.com/earendil-works/pi/issues/8894) | CLI value options consume the following flag when their value is missing | ✅ CLOSED | 3 | 0 |
| [#8752](https://github.com/earendil-works/pi/issues/8752) | Bedrock-converse: `usage.input` not normalized across model families — false cache-miss notices, doubled input cost | ✅ CLOSED | 3 | 0 |
| [#8845](https://github.com/earendil-works/pi/issues/8845) | Branch summarization deterministically fails: `generateBranchSummary` hardcodes maxTokens: 2048 | 🟢 OPEN | 2 | 0 |

**Why they matter:**
- **#8584** (25 comments, 9 👍) — The most-discussed issue this cycle. A TUI rendering bug that scatters streamed assistant text one word per line after long tool output is a major UX hit for developers using wide-file inspection tools.
- **#5886** (10 comments) — A meta-issue tracking recurring lifecycle bugs in `AgentSession` settlement; flagged by core maintainer `mitsuhiko`. Still open, indicating a deeper architectural fix is needed.
- **#6600** — npm 11.16.0 now blocks `npm install` scripts by default, which silently breaks Pi's extension update flow. No 👍 yet but affects all extension users on the latest npm.
- **#8061** — Context budget miscalculation causes provider 400 errors even at 78% input utilization, and the auto-retry fails identically. Critical for long-context workflows.
- **#8845** — The `/tree` branch "Summarize" feature hardcodes a 2048-token cap, making it unusable on any branch larger than a few hundred lines.

---

## 4. Key PR Progress

| # | Title | Status | Author |
|---|-------|--------|--------|
| [#8937](https://github.com/earendil-works/pi/pull/8937) | fix(coding-agent): settle active turn before in-memory fork | 🟢 OPEN | acmerfight |
| [#8936](https://github.com/earendil-works/pi/pull/8936) | fix(agent): stop prepared tools after preflight abort | 🟢 OPEN | acmerfight |
| [#8931](https://github.com/earendil-works/pi/pull/8931) | feat(ai): add thinking-level overrides for Fireworks GLM 5.3 | ✅ CLOSED | 8lank |
| [#8930](https://github.com/earendil-works/pi/pull/8930) | fix(coding-agent): expose queued agent message state | ✅ CLOSED | dingpuyu |
| [#8929](https://github.com/earendil-works/pi/pull/8929) | fix(coding-agent): settle active turn before in-memory fork | ✅ CLOSED | BetterAndBetterII |
| [#8925](https://github.com/earendil-works/pi/pull/8925) | feat(ai): add CoralBricks provider | ✅ CLOSED | divyvasal |
| [#8903](https://github.com/earendil-works/pi/pull/8903) | feat(ai): add Melious provider | ✅ CLOSED | sahil-melious |
| [#8908](https://github.com/earendil-works/pi/pull/8908) | fix(coding-agent): preserve compaction queued prompts | ✅ CLOSED | Dante-dan |
| [#8902](https://github.com/earendil-works/pi/pull/8902) | fix(coding-agent): route mid-loop compaction through full threshold check | ✅ CLOSED | johninthewinter |
| [#8901](https://github.com/earendil-works/pi/pull/8901) | feat(client,server,ai,coding-agent): TCP/WS transports, experimental Ollama provider | ✅ CLOSED | e-fity |

**Highlights:**
- **#8937 & #8929** — Two PRs addressing the same in-memory fork race: an in-flight tool turn could append its result to the wrong session when `newSession` was called before `teardownCurrent`. One landed (#8929), the other (#8937) remains open, possibly a re-spin.
- **#8936** — Prevents prepared parallel tools from executing after a sibling preflight aborts, closing the window where a cancelled-but-prepared tool could still fire side effects.
- **#8908** — Fixes a compaction race where queued prompts were lost when threshold compaction ended mid-turn; publishes streaming continuation intent before async input hooks.
- **#8901** — Adds raw TCP and WebSocket transports (Node built-in, zero deps) plus an experimental Ollama provider, expanding headless and embedded deployment options.
- **#8925 / #8903** — Two new built-in providers: CoralBricks (open models, 1M context) and Melious (European GDPR-compliant infrastructure).

---

## 5. Feature Request Trends

1. **Deferred / safe-reload APIs for extensions** — Issue #6552 (`requestReload()`) reflects repeated demand for extensions to trigger host reloads at safe runtime points, rather than requiring manual restarts.
2. **Provider catalog expansion** — Three new providers landed this cycle (CoralBricks, Melious, Fireworks GLM 5.3), and the community continues to request catalog updates (DeepSeek V4 pricing, Bedrock normalization). Providers are a top feature area.
3. **Context & compaction control** — Issues #8884, #8061, and #8845 all converge on the same theme: users want predictable, configurable context-budget behavior (output reservation, mid-loop compaction checks, branch summarization caps).
4. **Transport & embedding flexibility** — PR #8901 (TCP/WS transports) and PR #8930 (queued agent message state) signal growing demand for Pi as an embeddable engine, not just a CLI tool.
5. **CLI argument parsing robustness** — Issue #8894 (flag consumption bug) and #8684 (`PI_OFFLINE` scope misunderstanding) show users expect stricter, more documented CLI semantics.

---

## 6. Developer Pain Points

- **Lifecycle races under concurrent or parallel execution** — The top recurring frustration. Fork races (#8937), preflight abort races (#8936), and compaction queue races (#5886, #8908) all point to the same root: Pi's async session lifecycle has edge cases when multiple tool calls or branch operations overlap.
- **npm script blocking breaks extension workflows** — With npm 11.16.0 defaulting scripts off, `pi update --extensions` silently fails. Users need a clear workaround or a Pi-level fix to pass `--scripts-prepend` flags.
- **Context-budget math is unreliable** — Providers return 400 errors when the effective budget (input + reserved output) exceeds the window, but Pi's internal counter only tracks raw input tokens. This causes confusing overflow-retry loops (#8061).
- **TUI rendering fragility** — Row corruption after wide tool output (#8584), unreadable dark-theme dialogs (#8934), and fullscreen repaint gaps (#8923) suggest the TUI layer needs more robust boundary handling.
- **Credential-store locking under multi-session use** — Issue #8927 reports exclusive locks on snapshot reads with a ~200ms acquire budget, causing "Lock file already held" errors when multiple Pi sessions run in parallel.
- **Proxy / plain-HTTP provider breakage** — Issue #8134: sessions against `http://` OpenAI-compatible providers hang after the first tool call when `HTTP_PROXY` is set, a regression since 0.84.0.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-01

## 1. Today's Highlights
The Qwen Code team shipped a new nightly build focusing on web-shell polish and review pipeline reliability, while community attention is heavily concentrated on a llama.cpp grammar-parsing regression introduced in 0.22.3. Several session-management and UI stability fixes landed in the past 24 hours, and the web-shell is rapidly maturing with new workspace, workflow, and content-search capabilities. Cross-session messaging moved from proposal to secured implementation with per-session token authentication.

## 2. Releases
**v0.22.3-nightly.20260831.3a0c4c6108**
- `feat(web-shell)`: Git state hints now appear beside the branch picker actions for faster context awareness [#10397](https://github.com/QwenLM/qwen-code/pull/10397)
- `feat(review)`: Extended review pipeline with additional status emissions to improve CI traceability
Full changelog: https://github.com/QwenLM/qwen-code/releases/tag/v0.22.3-nightly.20260831.3a0c4c6108

## 3. Hot Issues
1. **[OPEN] toolSearch threshold triggers llama.cpp grammar parse failure (#10520)** – Setting `tools.toolSearch.threshold > 0` with local llama.cpp backends causes a hard `400 failed to parse grammar` error. Critical for developers using quantized or custom grammar configs. Community is tracking workarounds around threshold=0.
2. **[OPEN] 400 Failed to initialize samplers in 0.22.3 (#10530)** – Close relative of #10520; confirmed regression between 0.22.2 and 0.22.3 affecting Qwen 3.8/3.6 27b/35b models. Users note Gemma4 and other clients (Pi, OpenCode) do not reproduce the issue.
3. **[CLOSED] Cross-session messaging coordination (#8724)** – High-interest feature (13 comments) enabling sessions on the same host to discover and exchange messages via `list_agents`/`send_message`. Now gated with a fail-closed security policy and per-session tokens.
4. **[OPEN] `--resume` reconstructs dangling-unsigned-thought hazard (#8535)** – A correctness/security gap where `--resume`/`--continue` can re-create an unsigned trailing thought that PR #8260 previously patched for live sessions. Requires a session-store level fix.
5. **[OPEN] Archiving a live session recreates the active transcript (#9688)** – State conflict where an in-flight writer continues appending to `chats/<id>.jsonl` after the file is moved to archive, causing Web UI collisions. Impacts long-running daemon sessions.
6. **[OPEN] Auto-compaction fails permanently on HTTP 413 (#10380)** – Sessions behind reverse proxies with strict body limits become unrecoverable when the model context window exceeds the proxy limit. Closed with a compaction fallback strategy.
7. **[OPEN] `task_list` false-positive duplicate tool-call loop detection (#9450)** – Team state changes between identical `task_list` calls were misinterpreted as loops, prematurely stopping coordinated teammates. Closed after decoupling argument equality from result equality.
8. **[OPEN] `task_list` treats blank filters as active (#9281)** – Empty string serialization for optional `owner`/`blockedBy` fields incorrectly returned `No tasks found.` despite matching active tasks. Closed with explicit blank-skip logic.
9. **[OPEN] `ask` returns from PreToolUse hooks omit diffs (#9434)** – When hooks escalate Edit/WriteFile decisions to human review, the confirmation UI fails to render the expected diff. Limits auditability for path-filtering security hooks.
10. **[OPEN] Unnecessary `Press ctrl+s to show more

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-09-01

> **Note:** The project is undergoing a public rebrand to **Codewhale** (see PR #5742). References to "DeepSeek-TUI" and "CodeWhale" appear interchangeably in this digest; all GitHub links point to `github.com/Hmbown/DeepSeek-TUI`.

---

## 1. Today's Highlights

The Codewhale project closed out a major rebranding cycle, adopting "Codewhale" as the canonical public name across docs, TUI locales, and user-facing strings (PR #5742). Three critical TUI UX fixes landed: native ChatGPT/Codex PKCE sign-in without requiring the external Codex CLI (PR #5784), unified provider route authority across the picker/runtime/CLI (Issue #5755), and explicit credential consent to prevent silent leakage of `~/.codex/auth.json` paths (Issue #5772). On the engineering side, the flaky parallel-test issue (#5605) and the engine session-resume bug (#5750) were both resolved.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Why It Matters |
|---|-------|--------|----------------|
| #5316 | EPIC-005: CodeWhale TUI Crate Decomposition (Umbrella) | **OPEN** | The architectural backbone for splitting the monolithic TUI crate into focused sub-crates. Tracks every sub-EPIC and FEAT report. 20 comments, long-running since Aug 10. |
| #5778 | Native ChatGPT/Codex subscription sign-in without the Codex CLI | **OPEN** | Removes a hard dependency on the external `~/.codex/auth.json` credential file. Enables browser PKCE sign-in for ChatGPT/Codex subscribers — a frequently requested UX improvement. |
| #5772 | Make provider selection explicit; stop implicit external CLI credential reuse | **CLOSED** | Fixed a security/usability issue where disabled CLI credential locations were metadata-probed and unkeyed rows silently adopted credentials without confirmation. |
| #5755 | Unify provider route authority across picker, readiness, runtime, API, and CLI | **CLOSED** | Resolved conflicting provider states: ProviderLake/Models.dev rows could appear selectable while the runtime `RouteResolver` and CLI registry used different authorities. |
| #5605 | Flaky test: `separate_predispatch_crashes_on_one_run_get_distinct_recovery_turn_ids` | **CLOSED** | Reproduced under full-suite parallel load; confirmed unrelated to the decomposition moves in #5586. Test stability restored. |
| #5713 | Support `wire = "responses" \| "anthropic"` for `kind="openai-compatible"` | **CLOSED** | Custom providers were forced through ChatCompletions only. This fix enables Responses API and Anthropic Messages protocol wires for OpenAI-compatible endpoints. |
| #5771 | Give the active-session composer the shared `[↑]` send geometry | **CLOSED** | Aligned the active-session `ComposerWidget` with the startup Tideline shell's `[↑]` affordance, ensuring consistent submit hitbox and mouse path across sessions. |
| #5768 | Compose and verify the Tideline shell as one coherent running TUI | **CLOSED** | Verified that previously isolated startup slices (routing, composer enclosure, quiet boot, interactive route control) compose into a working binary, not just green unit tests. |
| #5775 | Make `Pod` the canonical public roster command and vocabulary | **CLOSED** | Eliminated competing nouns (`fleet`, `pod`, saved rosters, durable runs) that made the TUI harder to learn. Unified docs, CLI help, and setup under a single term. |
| #5767 | Fix public website auth links that resolve to localized 404s | **CLOSED** | `codewhale.net/signin`, `/signup`, and `/auth/callback` all redirected to `/en/...` 404s after localization. Links corrected. |

---

## 4. Key PR Progress

| PR | Title | Summary |
|----|-------|---------|
| [#5784](https://github.com/Hmbown/DeepSeek-TUI/pull/5784) | Native ChatGPT PKCE sign-in for `openai-codex` | Browser-based PKCE with localhost callback; refreshable tokens stored in Codewhale-owned storage. Closes #5778. |
| [#5750](https://github.com/Hmbown/DeepSeek-TUI/pull/5750) | Engine adopts host session ID for fresh turns | Fixed broken session resume: the engine was minting its own session ID instead of adopting the host's, causing resumed turns to land in a separate session. |
| [#5711](https://github.com/Hmbown/DeepSeek-TUI/pull/5711) | Rehydrate persisted goals and run host-managed continuation loop | Wired durable goal records into hosted engines; added the host-side re-arm loop so `update_goal` and the prompt surface operate on restored goals. |
| [#5749](https://github.com/Hmbown/DeepSeek-TUI/pull/5749) | Unix-socket transport + daemon/attach advertisement | Desktop Phase 0 foundation: daemon spawn → socket connect → round-trip → shutdown verified; permissions/traversal/stale-cleanup validated. |
| [#5782](https://github.com/Hmbown/DeepSeek-TUI/pull/5782) | Publish compaction survival contract; keep last round | Ported the contract schema onto current `main` (closure of #4394), with documented schema next to the implementation. |
| [#5788](https://github.com/Hmbown/DeepSeek-TUI/pull/5788) | Label `auth list` rows by provider, not by credential slot | Fixed misleading output where `siliconflow` appeared twice and `modelstudio-token-plan` four times due to slot collapsing. |
| [#5790](https://github.com/Hmbown/DeepSeek-TUI/pull/5790) | Isolate remote recovery lease generations | Blank classic lease IDs now start fresh recovery generations instead of inheriting stale same-run pre-dispatch leases. |
| [#5792](https://github.com/Hmbown/DeepSeek-TUI/pull/5792) | Emergency recovery trims with hysteresis | Fixes per-step thrashing in long sessions (351-message transcripts) where emergency compaction logged repeated budget warnings without progress. |
| [#5751](https://github.com/Hmbown/DeepSeek-TUI/pull/5751) | Op/EventMsg parity + compile-enforced guard | Rust core and TS surfaces now enforce parity at compile time, preventing silent drift between protocol layers. |
| [#5742](https://github.com/Hmbown/DeepSeek-TUI/pull/5742) | Use the public name "Codewhale" in prose | Swept ~100 lines of docs, all 15 TUI locale packs, 37 Rust string literals, and build scripts to adopt the ratified public name. Identifiers unchanged. |
| [#5783](https://github.com/Hmbown/DeepSeek-TUI/pull/5783) | Catalog authority: descriptors not compiled model lists | Pi/OMP and similar providers use live-fetched descriptors rather than hand-edited model lists. Baseten/Groq/Cerebras rosters are no longer compiled into the binary. |
| [#5721](https://github.com/Hmbown/DeepSeek-TUI/pull/5721) | Codewhale-account machine tokens (`CODEWHALE_API_KEY`) | CLI authentication as the account with no local session file and no browser — follows the control-plane contract's asymmetry. |
| [#5719](https://github.com/Hmbown/DeepSeek-TUI/pull/5719) | Wire `responses`/`anthropic` for `openai-compatible` + opencode-zen | Rescue of #5716; carries whp233's commits intact. Full credit to @whp233 for the wire-dialect design. |
| [#5753](https://github.com/Hmbown/DeepSeek-TUI/pull/5753) | Restore approved startup mark | Replaces the retired fluke projection in the Tideline startup hero with the approved generated diving-whale mark; preserves goldens and ASCII fallback. |
| [#5758](https://github.com/Hmbown/DeepSeek-TUI/pull/5758) | Restore rounded active composer enclosure | Real rounded `ComposerWidget` enclosure at viable sizes; legacy `composer_border` retained as a documented compact opt-out. |
| [#5791](https://github.com/Hmbown/DeepSeek-TUI/pull/5791) | Delete proven-dead helpers and stale `dead_code` allows | Workspace-wide reference search + `rustc -D dead_code` on `codewhale-tui --lib` validated every deletion. |
| [#5789](https://github.com/Hmbown/DeepSeek-TUI/pull/5789) | Drop co-author trailer gate, keep harvested credit | Relaxed the `Lint` job's rejection of agent commits that include `Co-authored-by` trailers — ordinary agent commits were being wrongly rejected. |

---

## 5. Feature Request Trends

- **Native auth without external CLI dependencies** — The #5778/#5784 thread (ChatGPT PKCE sign-in) reflects strong community demand to decouple Codewhale from the Codex CLI's credential files.
- **Explicit provider/credential consent** — Issue #5772 and #5755 show a clear trend: users want credential sources and provider routes to be surfaced explicitly rather than inferred, to avoid silent fallbacks and confusion.
- **Protocol flexibility for custom providers** — Issues #5713 and #5719 (Responses/Anthropic wire support for `openai-compatible` kind) indicate users are running providers that expose non-ChatCompletions endpoints and want first-class support.
- **Unified public vocabulary** — Issue #5775 (adopting `Pod` as the canonical roster command) and the broader rebrand to "Codewhale" signal a community desire for consistent, learnable terminology across docs, CLI, and TUI.
- **Multi-agent session durability** — PRs #5711 (persisted goals) and #5792 (emergency recovery with hysteresis) reflect ongoing investment in long-running, crash-resilient agent sessions.

---

## 6. Developer Pain Points

- **Flaky parallel test suites** — The full-suite parallel load exposed a crash in `separate_predispatch` (#5605), and PR #5790 isolated the lease-generation logic to prevent stale lease inheritance. Concurrency in the recovery path remains a pain point.
- **Provider authority fragmentation** — Issue #5755 documented that `ProviderLake`, `RouteResolver`, and the CLI registry could disagree on the same provider's state. Unifying this authority was a significant engineering effort.
- **Session resume correctness** — PR #5750 fixed a root-cause bug where the engine minted its own session ID instead of adopting the host's, silently breaking resume. This points to fragile session ID orchestration between host and engine.
- **Credential leakage risk** — Issue #5772 revealed that normal picker UI could expose `HOME`/temp credential paths, and unkeyed external rows could adopt credentials without explicit consent. Hardened in the closed fix.
- **CI/CD false positives** — PR #5740 highlighted a workflow where a `402 Insufficient Balance` LLM error was silently downgraded to a warning with a green checkmark, giving a misleading `Codewhale review ✓` status. The review visibility was corrected.
- **Dead code and stale tooling** — PR #5791 performed a high-confidence dead-code sweep, and PR #5789 relaxed an overly strict co-author trailer gate that was rejecting ordinary agent commits. Maintenance hygiene is an ongoing effort.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*