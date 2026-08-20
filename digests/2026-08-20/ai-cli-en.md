# AI CLI Tools Community Digest 2026-08-20

> Generated: 2026-08-20 01:38 UTC | Tools covered: 10

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
**Date: 2026-08-20**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem is in a phase of aggressive maturation, with major vendors (Anthropic, OpenAI, Google, GitHub, Qwen) rapidly iterating on agent reliability, security hardening, and cross-platform parity. The dominant narrative this cycle is **operational trust**: teams are patching auth regressions, sandbox policy overrides, and session-state bugs faster than shipping new features. Meanwhile, a smaller but active wave of independent projects (OpenCode, Pi, DeepSeek TUI) is addressing niche pain points around billing transparency, extensibility hooks, and localization. The market is consolidating around two axes: enterprise-grade security/permission controls and developer-centric reliability (agent hangs, token leakage, and session persistence).

---

## 2. Activity Comparison

| Tool | Hot Issues | Open/Closed PRs | Releases (24h) | Community Signal |
|------|-----------|-----------------|----------------|------------------|
| **Claude Code** | 10 | 1 active | v2.1.237, v2.1.236 | High engagement on AGENTS.md (#6235, 4,677 👍); packaging instability eroding trust |
| **OpenAI Codex** | 10 | 10 closed | rust v0.149.0-alpha.2 | Safety-hardening focus; Windows browser trust bugs dominate |
| **Gemini CLI** | 10 | ~5 open, ~4 merged | v0.56.0-nightly, v0.57.0-preview.0, v0.56.0-stable | Multi-release cadence; agent reliability & security priorities |
| **GitHub Copilot CLI** | 10 | 0 active | v1.0.81-2 through v1.0.81-5 (4 patches) | Rapid-fire patching of auth/sandbox regressions; low PR visibility |
| **Kimi Code CLI** | 1 (closed) | 0 | None (v0.37.1) | Quiet cycle; ACP tool compatibility gap being addressed |
| **OpenCode** | 10 | ~8 in review | None | Billing/usage bugs surfacing; Bun install breakage |
| **Pi** | 10 (several closed) | ~7 closed, 2 open | None | Ephemeral session defaults shipped; Windows focus |
| **Qwen Code** | 10 | ~10 in progress | v0.21.14 | Session management & CI/CD isolation maturing; SWE-bench verified |
| **DeepSeek TUI** | 10 | ~8 merged (v0.9.10, 76 commits) | v0.9.10 | High commit velocity; Chinese localization initiative accelerating |

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Agent reliability & subagent lifecycle** | Gemini CLI, OpenCode, Qwen Code, DeepSeek TUI | Subagents falsely reporting success (#22323 Gemini), hanging on simple tasks (#21409 Gemini), token count leakage across model switches (#9454 Qwen), session hangs on large jobs (#1425 DeepSeek) |
| **Cross-session / cross-tool interoperability** | Claude Code, OpenAI Codex, Pi | AGENTS.md standardization (#6235 Claude Code, 4,677 👍); cross-session `notify_when_idle` (Claude Code v2.1.236); named sessions (#69836 Claude Code) |
| **Security hardening & sandbox integrity** | OpenAI Codex, Gemini CLI, GitHub Copilot CLI, Qwen Code | Codex stopping assumption that Git commands are safe (#39524); Gemini subprocess credential-leak prevention (#28898); Copilot sandbox policy overrides (#4522); Qwen autofix runner isolation (#9214, 11 review rounds) |
| **Windows platform parity** | OpenAI Codex, GitHub Copilot CLI, Pi, DeepSeek TUI | Codex browser trust-path bugs (#39136, 78 comments); Copilot `ctrl+shift+c` broken on Linux (#2082) and Windows terminal conflicts (Pi #8183); DeepSeek IME instability on Windows 11 (#5023) |
| **MCP / OAuth ecosystem stability** | OpenAI Codex, GitHub Copilot CLI, OpenCode, DeepSeek TUI | Atlassian MCP OAuth RFC 8414 regression (Copilot #4480, #4490); MCP server lifecycle leaks (#38754 Codex); MCP rate-limit after idle (#35855 OpenCode); MCP image content support (#5515 DeepSeek) |
| **Token / billing transparency** | OpenCode, Qwen Code, Claude Code | OpenCode abnormal credit consumption (#43409, 42% in 4h); Qwen token count leakage (#9454); Claude prompt caching fixes for custom base URLs (v2.1.237) |
| **Context compaction & session persistence** | Qwen Code, Claude Code, Pi, OpenCode | Qwen context compression producing incorrect results (#9309); Claude session unarchive (#67835); Pi prompt-cache-key loss on forks; OpenCode aborted streams recorded as clean stops (#37852) |
| **Extensibility & plugin ecosystems** | Claude Code, OpenCode, Pi, Gemini CLI | Claude Code plugin skills invisible in `<available_skills>` (#15178); OpenCode plugin tool decoding (#43460); Pi extension invisibility into slash commands (#8365); Gemini subagent auto-discovery (#21968) |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | Qwen Code | OpenCode | Pi | DeepSeek TUI | Kimi Code CLI |
|-----------|------------|--------------|------------|-------------------|-----------|----------|----|--------------|---------------|
| **Primary focus** | Agent config standardization, session management | Safety & security hardening, enterprise trust boundaries | Agent reliability, observability, security | Enterprise auth/OAuth, sandbox policy | Session management, CI/CD isolation, agent orchestration | Billing transparency, plugin/tool ecosystem | Windows parity, ephemeral defaults, extensibility hooks | Retention hardening, Chinese localization, durable approvals | ACP tool compatibility (narrow) |
| **Target user** | Individual developers → enterprise teams | Enterprise/security-conscious teams | Research & production agent workflows | GitHub Enterprise orgs | Open-source & Chinese-market developers | cost-sensitive individual & team users | Multi-profile, local-LLM power users | Chinese-speaking developers, long-session users | ACP/Zed integrators |
| **Technical approach** | CLAUDE.md → push for AGENTS.md; cross-session coordination | Guardian v2 consolidation; explicit trust-model for Git/commands | GCS trajectory logging; atomic model downloads; subprocess hardening | Rapid patch cadence; managed-policy enforcement | Ephemeral container isolation for autofix; agent-board filesystem coordination | Hot-reload config; optimistic prompt admission; resolved model limits | Session-scoped defaults; record-query recovery; reasoning-details round-trips | Dictionary-based i18n; durable approval persistence; stream state-machine refactor | Minimal—ACP runtime compatibility layer |
| **Release velocity** | Moderate (2 releases/24h) | Low (alpha, no notes) | High (nightly + preview + stable) | Very high (4 patches/24h, reactive) | Moderate (1 stable + nightly) | None | None | Moderate (v0.9.10, 76 commits) | None |
| **Open-source posture** | Full GitHub repo, issue-driven | Full GitHub repo, safety-PR heavy | Full GitHub repo, preview/nightly track | Full GitHub repo, enterprise-gated features | Full GitHub repo, benchmark-transparent | Full GitHub repo | Full GitHub repo | Full GitHub repo | Full GitHub repo |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **GitHub Copilot CLI** — 4 patch releases in 24 hours signals a tool in active stabilization, but the reactive cadence (auth regressions, sandbox overrides, terminal deadlocks) suggests the feature surface is outpacing quality control.
- **DeepSeek TUI** — 76 commits in v0.9.10 with strong merge velocity; Chinese localization push and durable approval state indicate a maturing community with clear priorities.
- **Gemini CLI** — Triple-release cadence (nightly + preview + stable) with merged PRs on security, atomic downloads, and trajectory logging shows disciplined iteration.

**Mature, steady cadence:**
- **Claude Code** — Large community (4,677 👍 on AGENTS.md) but low PR velocity (1 active PR) relative to issue volume. The team is shipping features but not keeping pace with community-driven standardization requests.
- **Qwen Code** — SWE-bench Verified success, session management maturing, but CI/CD isolation PR took 11 review rounds—indicating a tool where security hardening is deliberate and careful.

**Emerging / focused:**
- **OpenCode** — Active PR pipeline (plugin decoding, model limits, hot-reload) but no releases; billing bugs (#43409) suggest growth pains as the user base scales.
- **Pi** — Strong closed-PR velocity on session defaults and reasoning-details handling; Windows-focused community driving tangible product decisions.
- **OpenAI Codex** — High PR closure rate (10 PRs) with clear safety narrative, but Windows browser bugs (#39136) and model serialization costs (#35050) remain unresolved.
- **Kimi Code CLI** — Smallest activity footprint; ACP compatibility is the sole focus, suggesting a narrower audience.

---

## 6. Trend Signals

| Signal | Evidence | Implication for Developers |
|--------|----------|---------------------------|
| **AGENTS.md standardization is inevitable** | Claude Code issue #6235 (4,677 👍) is the highest-engagement issue across all tools; community explicitly wants portability across Codex, Amp, Cursor, and Gemini. | Tool-agnostic agent configs will become a de facto standard; invest in `agents.md` compliance early. |
| **Auth/OAuth regressions are the #1 reliability risk** | Copilot Atlassian OAuth break (#4480, #4490), Gemini OAuth redirect fixes, Codex AWS credential refresh (#39410), Pi catalog routing mismatches (#8206). | Enterprise deployments should pin CLI versions and test OAuth flows for non-Microsoft providers before upgrading. |
| **Agent reliability > feature count** | Subagent misreporting (Gemini #22323), hangs (Gemini #21409), false-success classifications (Qwen #9509), session state leakage (Qwen #9454). | Prioritize tools with visible subagent observability and clear termination-reason reporting; avoid tools where agent failures are silently swallowed. |
| **Windows is the fragmentation frontier** | Codex browser trust bugs (#39136), Pi Windows setup guidance demand (#7547), Copilot Linux clipboard break (#2082), DeepSeek IME instability (#5023). | Cross-platform parity is still uneven; Windows users should expect friction and validate core workflows before enterprise adoption. |
| **Billing transparency is a trust differentiator** | OpenCode abnormal credit consumption (#43409, 42% in 4h), Qwen token leakage (#9454), Codex serialization cost impact (#35050, 27–45% waste). | Monitor tools that expose usage telemetry; hidden cost overruns from model behavior (GPT-5.6 serialization) are a real enterprise risk. |
| **Security hardening is becoming table stakes** | Codex Git trust model overhaul (#39524), Gemini subprocess credential isolation (#28898), Qwen autofix container isolation (#9214), Copilot sandbox policy enforcement. | Tools that explicitly address supply-chain and sandbox security will gain enterprise adoption; assume any CLI with file-system access needs hardening. |
| **Session persistence & compaction fidelity** | Qwen compression producing incorrect results (#9309), Pi fork cache misses, OpenCode aborted-stream masking (#37852), Claude session unarchive (#67835). | Context compaction is the next frontier; tools that preserve durable context across compaction cycles will reduce token waste and improve multi-session workflows. |
| **MCP ecosystem is fragmenting** | Copilot RFC 8414 OAuth break, Codex per-server trusted OAuth issuer override request (#38944), OpenCode MCP rate-limit after idle (#35855), DeepSeek MCP image forwarding (#5515). | MCP server implementations vary widely in OAuth handling and lifecycle management; expect interoperability issues until the spec stabilizes. |

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
**Data as of 2026-08-20 · Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking — Most-Discussed Skills

| # | Skill / PR | Functionality | Discussion Highlights | Status |
|---|-----------|--------------|----------------------|--------|
| 1 | **#556 / #1298** — `skill-creator` eval fix | Fixes `run_eval.py` perpetually reporting 0% recall, making description optimization train against noise | 12+ comments on the bug; 2+ follow-up Windows compatibility PRs (#1099, #1050); 7 👍 on the original issue | **Open** — fixes merged in #1298 but Windows issues persist |
| 2 | **#83** — `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills evaluating skill quality (structure, docs, examples, security) across five weighted dimensions | First community contribution to add a *skill about skills*; sparks broader governance discussion (see #412) | **Open** |
| 3 | **#568** — `servicenow` platform skill | Broad ServiceNow platform assistant covering ITSM, ITOM, ITAM/SAM, FSM, Security, IntegrationHub | Active discussion with maintainer engagement (updated 2026-08-12); one of the most comprehensive enterprise-platform skills proposed | **Open** |
| 4 | **#723** — `testing-patterns` skill | Full testing stack: Testing Trophy philosophy, AAA pattern, React component testing, edge-case strategies | Addresses a clear gap — no testing-focused skill existed in the bundle | **Open** |
| 5 | **#514** — `document-typography` skill | Prevents orphan lines, widows, numbering misalignment in AI-generated documents | Targets a universal pain point ("affects every document Claude generates") | **Open** |
| 6 | **#1367** — `self-audit` skill (v1.3.0) | Four-dimension reasoning quality gate + mechanical file-verification before delivery | Directly addresses the "reasoning quality gate" proposal in Issue #1385; strong community alignment | **Open** |
| 7 | **#210** — `frontend-design` skill improvement | Revisions for clarity and actionability — every instruction must be executable within a single conversation | Responds to skill-quality feedback; focuses on reducing ambiguity in Claude's behavior | **Open** |
| 8 | **#486** — `odt` skill | OpenDocument Format creation, template filling, and ODT→HTML parsing | Expands document-format coverage beyond the existing DOCX/PDF skills | **Open** |

---

## 2. Community Demand Trends

Analysis of the top-commented Issues reveals five concentrated demand vectors:

1. **Reliability & Evaluation Tooling** — Issue #556 (12 comments, 7 👍) dominates. The community needs `run_eval.py` to actually reflect skill behavior; the entire skill-creation loop depends on it.
2. **Enterprise / Platform Skills** — ServiceNow (#568), SAP-RPT-1-OSS (#181), and SharePoint security (#1175) signal strong demand for domain-specific enterprise skills beyond general coding.
3. **Security & Governance** — Issue #492 (43 comments, 2 👍) on namespace trust-boundary abuse is the most-commented issue in the repo. Coupled with the agent-governance proposal (#412) and skill-security-analyzer (#83), security-aware skills are a top priority.
4. **Context Efficiency** — Issue #1487 flags a skill injecting ~156k tokens in one call, and Issue #1329 proposes a compact-memory skill. The community is actively seeking ways to reduce token waste.
5. **Workflow & Collaboration** — Issue #228 (16 comments, 8 👍) requests org-wide skill sharing; Issue #189 reports duplicate skills across plugins. Distribution and deduplication are unresolved pain points.

---

## 3. High-Potential Pending Skills

These PRs have active discussion, maintainer engagement, and a clear path to merge:

| PR | Skill | Why It's Close |
|----|-------|---------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval + Windows fixes | Directly resolves the highest-impact bug in the repo; Windows parity is a known blocker |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` (v1.3.0) | Builds on the community-proposed reasoning quality gate (#1385); two of three gates already proven |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Fills a confirmed gap; comprehensive scope matches the testing-trophy framework the community expects |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Largest enterprise-scope skill proposed; active maintainer updates as recently as Aug 12 |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` + `skill-security-analyzer` | First meta-skill contribution; addresses both quality and security governance demands |
| [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | Solves a universal document-quality problem; narrow scope, clear value |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable evaluation and governance tooling** — skills that can verify, audit, and securely distribute other skills — rather than for additional end-user domain skills, as evidenced by the 43-comment trust-boundary issue and the 7-👍 eval-repair issue both outpacing every other discussion in engagement.

---



# Claude Code Community Digest — 2026-08-20

## 1. Today's Highlights

Anthropic shipped **v2.1.237** with prompt caching fixes for LLM gateway/custom base URL sessions and a new "Concise" output style that skips preamble and narration. The community is heavily focused on the push toward **AGENTS.md standardization** (Issue #6235, 4,677 👍), while a wave of packaging and auth bugs in v2.1.237 is drawing fresh reports.

---

## 2. Releases

### v2.1.237 — [GitHub](https://github.com/anthropics/claude-code/releases)
- **Fixed** prompt caching for sessions routed through an LLM gateway or custom base URL.
- **Added** a built-in **"Concise"** output style — Claude leads with results and skips preamble/narration while retaining full thoroughness. Selectable via `/config` → Output style.

### v2.1.236 — [GitHub](https://github.com/anthropics/claude-code/releases)
- **Added** `ANTHROPIC_DEFAULT_MODEL` env var — sets the default model for new sessions; `/model` still overrides and persists across restarts (unlike `ANTHROPIC_MODEL`).
- **Added** `notify_when_idle` to cross-session `SendMessage` — lets one Claude Code session alert another when it becomes idle.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#6235](https://github.com/anthropics/claude-code/issues/6235) | Support AGENTS.md | Industry-wide move toward a unified agent config file; Claude Code's `CLAUDE.md` is seen as siloed. | 🔥 **4,677 👍 / 362 comments** — overwhelmingly positive |
| [#36151](https://github.com/anthropics/claude-code/issues/36151) | Multi-account switching in Claude Mobile | Mobile users can't switch accounts without shared email — blocks team/secondary workflows. | 611 👍 / 160 comments |
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved orgs still get cyber-safeguard blocks | Enterprise users with verified status face repeated blocks, breaking CI/CD and team pipelines. | 20 👍 / 127 comments |
| [#77136](https://github.com/anthropics/claude-code/issues/77136) | Opus 4.8 tone / Opus 5.0 incoherence | Model quality regression complaints for flagship models directly affect developer productivity. | 198 👍 / 31 comments |
| [#80988](https://github.com/anthropics/claude-code/issues/80988) | `heron_brook` injects hard-coded delegation restriction for Opus 5 | System prompt override with no opt-out silently changes agent behavior; raises transparency concerns. | 57 👍 / 30 comments |
| [#32479](https://github.com/anthropics/claude-code/issues/32479) | GitHub Connector recognized in Desktop but not Claude Code | Cross-product integration inconsistency blocks users who rely on the connector for PR workflows. | 140 👍 / 89 comments |
| [#81698](https://github.com/anthropics/claude-code/issues/81698) | GPU process crash on Windows kills all sessions | RTX 5080 laptop users report catastrophic crashes taking down Claude Code entirely. | 4 👍 / 44 comments |
| [#25286](https://github.com/anthropics/claude-code/issues/25286) | Claude Code freezes — no input accepted, 100% terminal write ratio | Reproducible hang requiring `kill`; impacts long-running sessions across platforms. | 18 👍 / 14 comments |
| [#15178](https://github.com/anthropics/claude-code/issues/15178) | Plugin skills not injected into `<available_skills>` context | Skills are executable but invisible to the model — defeats the purpose of the plugin system. | 33 👍 / 22 comments |
| [#88103](https://github.com/anthropics/claude-code/issues/88103) | v2.1.237 `latest` tag ships dead npm stub on 3 platforms | Critical release infrastructure bug — linux-x64, win32-x64, and linux-x64-musl packages are 500-byte stubs. | 0 👍 / 2 comments (brand new) |

---

## 4. Key PR Progress

| # | PR | Description |
|---|----|-------------|
| [#77977](https://github.com/anthropics/claude-code/pull/77977) | docs(plugin-dev): document `skipLfs` marketplace sources | Documents the `skipLfs` option for `github` and `git` marketplace source objects; adds examples for GitHub shorthand and generic Git URL sources that skip LFS downloads. Closes #63035. |

> **Note:** Only 1 PR was active in the last 24h. The team's PR velocity appears low relative to the issue volume.

---

## 5. Feature Request Trends

- **Cross-tool agent standardization:** Issue #6235 (AGENTS.md) is the dominant signal — the community wants Claude Code to adopt the emerging `agents.md` standard rather than maintaining a Claude-specific `CLAUDE.md`, enabling portability across Codex, Amp, Cursor, and other agents.
- **Multi-account & mobile parity:** Issue #36151 reflects growing demand for mobile feature parity, specifically account switching without email sharing — likely to expand as mobile usage grows.
- **Named sessions & session management:** Issue #69836 (named sessions via `--session`) and Issue #67835 (session unarchive) point to a desire for better session lifecycle tooling.
- **Cross-session communication:** The `notify_when_idle` addition in v2.1.236 suggests Anthropic is already moving in this direction; more cross-session coordination features are likely requested.

---

## 6. Developer Pain Points

1. **Release quality & packaging instability** — v2.1.237 shipped with dead npm stubs on three platforms (#88103, #86941), silently overwriting working installs. This erodes trust in the `latest` tag.
2. **System prompt opacity** — The `heron_brook` injection (#80988) overrides user-configured delegation policies without documentation or opt-out, raising concerns about hidden behavioral changes.
3. **Auth & token lifecycle bugs** — `remote-control` OAuth tokens expire after exactly 24h without refresh (#88054); CVP-approved orgs still get blocked (#84352); Chrome side-panel auth loops (#88104).
4. **Model consistency issues** — Users report Opus 4.8 as "toxic" in tone and Opus 5.0 as incoherent (#77136), directly impacting professional workflows.
5. **Plugin & MCP visibility gaps** — Plugin skills aren't surfaced in `<available_skills>` (#15178); background subagents lose MCP resource tools (#85230).
6. **Platform-specific crashes** — Windows GPU crashes (#81698), terminal freezes (#25286), and rendering corruption (#79025) create an uneven experience across OSes.
7. **Cross-product integration breaks** — GitHub Connector works in Desktop but not Claude Code (#32479); Cowork VM kernel fails to boot on ARM64 (#39636).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-20

## 1. Today's Highlights

The Codex team shipped **rust alpha v0.149.0-alpha.2** and closed a wave of safety-focused PRs, notably **stopping the assumption that Git commands are inherently safe** and **isolating automatic plugin Git operations** from repository-local config. On the issue side, the community's top concern is a **Windows browser-plugin trust-boundary bug** (#39136, 78 comments / 41 👍) that blocks in-app browser control, while a model-performance issue around **GPT-5.6 serializing independent Code Mode calls** (#35050, 40 👍) is drawing significant attention for its direct cost impact.

---

## 2. Releases

**rust-v0.149.0-alpha.2** — Latest alpha for the Codex CLI backend. No detailed release notes were published in the past 24 h; see the tag [here](https://github.com/openai/codex/releases).

---

## 3. Hot Issues

| # | Title | Why it matters | Community reaction |
|---|-------|---------------|-------------------|
| [#39136](https://github.com/openai/codex/issues/39136) | Browser plugin initialization fails on Windows — "Trusted RPC dependency not within a trusted code path" | Breaks the in-app browser entirely on Windows; touches the trust-boundary / sandbox architecture that underpins all browser control. | 78 comments · 41 👍 |
| [#35050](https://github.com/openai/codex/issues/35050) | GPT-5.6 serializes independent Code Mode calls; batching cuts weighted usage by 27–45 % | Direct cost & latency impact for Pro/Business users; suggests a model-behavior regression worth tracking. | 24 comments · 40 👍 |
| [#25178](https://github.com/openai/codex/issues/25178) | Windows Computer Use screenshots fail with `SetIsBorderRequired` on Win 10 22H2 | Blocks the entire Computer Use workflow on a widely-used OS version; root-cause is an unsupported COM interface call. | 28 comments · 15 👍 |
| [#39318](https://github.com/openai/codex/issues/39318) | Browser control fails: trusted RPC dependency outside configured trusted code path | Duplicate / related flavor of #39136, confirming the issue spans multiple Windows builds (26200, 22631). | 21 comments · 2 👍 |
| [#38350](https://github.com/openai/codex/issues/38350) | Recurring scheduled tasks in ChatGPT Work disable themselves after successful runs | Undermines trust in automation; tasks flip to paused without user action, affecting workflow reliability. | 21 comments · 0 👍 |
| [#39239](https://github.com/openai/codex/issues/39239) | `thread/archive` fails with os error 2 after `thread/resume` on Windows | Path-equality bug with `\\?\` verbatim rollout paths causes double-queueing; blocks session archival on Windows. | 17 comments · 0 👍 |
| [#28950](https://github.com/openai/codex/issues/28950) | Chrome plugin install fails to create Native Messaging Host on Windows | Extension is present but the native host registration step never completes, rendering browser-control features non-functional. | 12 comments · 0 👍 |
| [#30829](https://github.com/openai/codex/issues/30829) ✅ | `codex-windows-sandbox-setup.exe` not found after clean install due to bin junction | **Closed** — sandbox setup path resolution was broken after clean installs; fix landed. | 11 comments · 0 👍 |
| [#38754](https://github.com/openai/codex/issues/38754) | Local stdio MCP servers repeatedly spawned and not reaped within a single task | Resource leak per turn; each new turn respawns the MCP server instead of reusing it, increasing latency and CPU. | 10 comments · 2 👍 |
| [#23112](https://github.com/openai/codex/issues/23112) | Mobile pairing stuck after revoked enrollment | Desktop stays on "Approve on mobile device" even after logout/login, MFA re-enrollment, and restarts — no recovery path. | 6 comments · 3 👍 |

---

## 4. Key PR Progress

| PR | Status | Summary |
|----|--------|---------|
| [#39524](https://github.com/openai/codex/pull/39524) ✅ | Closed | **Stop treating Git commands as inherently safe.** Repository config can redirect remotes or invoke helpers even on read-only commands; Git args alone no longer establish trust. |
| [#39520](https://github.com/openai/codex/pull/39520) ✅ | Closed | **Isolate automatic plugin Git operations.** Background marketplace / plugin refreshes no longer inherit repo-local or command-scoped Git config from the launching project. |
| [#39474](https://github.com/openai/codex/pull/39474) ✅ | Closed | **Consolidate Guardian extensions into `codex-guardian-v2`.** Thread-lifecycle contributor and subagent-spawn risk scorer now share a single extension entry point, removing redundancy. |
| [#39410](https://github.com/openai/codex/pull/39410) ✅ | Closed | **Refresh expired AWS credentials for Bedrock.** Adds an `aws.auth_refresh` provider config so Bedrock sessions recover when credentials expire mid-request. |
| [#39523](https://github.com/openai/codex/pull/39523) ✅ | Closed | **Persist thread section moves before the first turn.** Non-ephemeral threads now materialize and flush their rollout so section-filtered lists work immediately. |
| [#31155](https://github.com/openai/codex/pull/31155) ✅ | Closed | **Release thread writer after failed shutdown.** Fixes a leaked live-writer lease that persisted in the local store when rollout persistence failed to flush. |
| [#39510](https://github.com/openai/codex/pull/39510) ✅ | Closed | **Track built-in control tool calls in analytics.** Emits `codex_control_tool_call_event` for `request_user_input`, `update_plan`, `view_image`, and goal tools with correlation / timing metadata. |
| [#39452](https://github.com/openai/codex/pull/39452) ✅ | Closed | **Remove feature gate for async user messages.** `send_user_message_async` is now exposed to root agents whenever the selected model advertises support. |
| [#39515](https://github.com/openai/codex/pull/39515) ✅ | Closed | **Use `mem::take` to drain unified exec output buffers.** Replaces a custom `HeadTailBuffer::drain` helper with stdlib semantics, simplifying the code path. |
| [#39493](https://github.com/openai/codex/pull/39493) ✅ | Closed | **Make head-tail buffer capacity const-generic.** `HeadTailBuffer` is now parameterized by `const MAX_BYTES`, keeping `UNIFIED_EXEC_OUTPUT_MAX_BYTES` as the production default. |

---

## 5. Feature Request Trends

1. **Configurable, decoupled context compaction model** (#22486, 6 👍) — Users want the compaction model to be independent of the active session model, since compaction is a distinct job from interactive coding.
2. **Explicit per-server trusted OAuth issuer override for MCP** (#38944, 1 👍) — Remote MCP servers whose protected-resource metadata points to a different issuer than their auth URL need a manual override.
3. **Prevent PR workflow pushes targeting the default branch** (#39560) — A new safety-enhancement request asking Codex to refuse pushes that would update the tracked default branch during PR creation.
4. **Async user messages (now GA)** (#39452) — The feature gate was removed; async message support is now available on models that advertise it.

---

## 6. Developer Pain Points

- **Windows browser / Chrome-extension trust path bugs** dominate the issue tracker (#39136, #39318, #28950). A common thread: the trusted-code-path validation for the in-app browser and its native messaging host is rejecting valid plugin installs on multiple Windows builds.
- **Model serialization overhead** (#35050) — GPT-5.6's tendency to serialize independent Code Mode tool calls is wasting tokens and increasing latency; users are requesting explicit batching or a model-level fix.
- **MCP server lifecycle leaks** (#38754) — Local stdio MCP servers are spawned per-turn instead of reused, causing repeated process creation and stale-state accumulation within a single task.
- **Scheduled automation reliability** (#38350, #34794) — Tasks self-disabling after success and failing to wake from DarkWake both erode confidence in the scheduling subsystem.
- **Session path / archive edge cases on Windows** (#39239, #37673) — Verbatim `\\?\` paths and silent truncation of large JSONL records (>16 MiB) during migration indicate fragility in rollout persistence.
- **Mobile / remote pairing recovery** (#23112, #35855, #37385) — Stale enrollment state, pairing failures across versions, and cross-platform history sync gaps are recurring friction points for the remote-control workflow.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026‑08‑20

## 1. Today's Highlights
The Gemini CLI team shipped two new nightly/preview releases (v0.56.0‑nightly.20260820, v0.57.0‑preview.0) with core fixes for empty‑text turn preservation and Cloud Workstations OAuth redirects. Several high‑impact PRs landed today, including hardened subprocess security, atomic Whisper model downloads, and GCS trajectory‑logging infrastructure. Community discussion remains focused on agent reliability, with top‑voted issues highlighting subagent recovery failures, generalist‑agent hangs, and Auto‑Memory retry loops.

## 2. Releases
- **v0.56.0‑nightly.20260820.ge90c63fa1** — Preserve empty text turns when tools/media are present (`#28892`); includes v0.57.0‑preview.0 changelog.  
  🔗 [Changelog](https://github.com/google-gemini/gemini-cli/pull/28918)
- **v0.57.0‑preview.0** — Fix dynamic resolution of Cloud Workstations proxy redirect URI for OAuth flows; fix swallowed directory‑mismatch errors in IDE connections.  
  🔗 [Changelog](https://github.com/google-gemini/gemini-cli/pull/28918)
- **v0.56.0** — Stable release; full changelog available.  
  🔗 [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.55.1...v0.56.0)

## 3. Hot Issues
| Issue | Summary | Why It Matters | Community |
|-------|---------|----------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports `GOAL` success after hitting `MAX_TURNS`, hiding the interruption. | Masks real failures in multi‑repo investigations; subagent state is misreported. | 12 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely on simple tasks (e.g., folder creation). | Blocks routine workflows; users must disable subagents as workaround. | 8 comments, 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model’s bash affinity via zero‑dependency OS sandboxing & post‑execution intent routing. | Enables secure, native bash‑tool chaining while preserving security/UX. | 8 comments, 1 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component‑level evaluations (76 behavioral evals generated). | Critical for measuring agent reliability across 6 supported Gemini models. | 7 comments, 0 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess impact of AST‑aware file reads, search, and codebase mapping. | Could reduce turn count and token noise by precisely reading method bounds. | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use custom skills/sub‑agents without explicit prompting. | Limits extensibility; users expect automatic skill discovery. | 6 comments, 0 👍 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low‑signal sessions indefinitely. | Causes unnecessary background processing and may re‑surface stale memory. | 5 comments, 0 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging. | Secrets may already be in model context before redaction; logging can leak sensitive skill names. | 4 comments, 0 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck in “Waiting input” after completion. | Simple commands appear hung, breaking automation flows. | 4 comments, 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser‑agent resilience with automatic session takeover & lock recovery. | Persistent browser profiles fail fast on lock; recovery would improve reliability. | 4 comments, 0 👍 |

## 4. Key PR Progress
| PR | Description | Status |
|----|-------------|--------|
| [#28892](https://github.com/google-gemini/gemini-cli/pull/28892) | Preserve empty text turns when they carry tool requests/responses or multimodal media. | ✅ Closed (merged) |
| [#28922](https://github.com/google-gemini/gemini-cli/pull/28922) | Implement GCS trajectory logging and debug‑artifact storage for production/evaluation runs. | 🟢 Open |
| [#28898](https://github.com/google-gemini/gemini-cli/pull/28898) | Harden subprocess execution security; prevent credential leakage into untrusted tool environments. | 🟢 Open |
| [#28915](https://github.com/google-gemini/gemini-cli/pull/28915) | Ensure consistent symlink evaluation in ignore‑path handling (`.geminiignore`, `.gitignore`). | 🟢 Open |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Prompt for consent on environment changes; sanitize runtime‑altering env vars in extensions. | 🟢 Open |
| [#28566](https://github.com/google-gemini/gemini-cli/pull/28566) | Propagate `InvalidStreamError` details to UI, enabling helpful `/compress` recommendations. | ✅ Closed (merged) |
| [#28655](https://github.com/google-gemini/gemini-cli/pull/28655) | Make Whisper model downloads failure‑atomic (no partial `.bin` files). | ✅ Closed (merged) |
| [#28916](https://github.com/google-gemini/gemini-cli/pull/28916) | Buffer partial stdout chunks in `WhisperTranscriptionProvider` to reassemble split timestamp lines. | 🟢 Open |
| [#28917](https://github.com/google-gemini/gemini-cli/pull/28917) | Atomic download + cleanup in `WhisperModelManager` (temp file → rename on success). | 🟢 Open |
| [#28914](https://github.com/google-gemini/gemini-cli/pull/28914) | Inject on‑retry nudge into conversation contents (preserves prefix caching). | 🟢 Open |

## 5. Feature Request Trends
- **Agent Reliability & Observability** — Strong demand for robust subagent recovery, clear termination‑reason reporting, and visibility into subagent trajectories (`#22323`, `#21409`, `#22598`).
- **Security & Sandboxing** — Interest in zero‑dependency OS sandboxing, deterministic secret redaction, and credential‑leak prevention in subprocesses (`#19873`, `#26525`, `#28898`).
- **Performance & Efficiency** — Exploration of AST‑aware tools to reduce turn count and token waste, plus better handling of large tool sets (`#22745`, `#22746`, `#24246`).
- **Memory System Improvements** — Requests to limit Auto Memory retries, quarantine invalid patches, and surface low‑signal session decisions (`#26522`, `#26523`, `#26516`).
- **Extensibility & Subagent Discovery** — Users want the agent to automatically leverage custom skills and sub‑agents without explicit prompting (`#21968`).

## 6. Developer Pain Points
- **Agent hangs & misreported successes** — Subagents and generalist agents frequently stall or falsely report goal completion, forcing manual cancellation or subagent disablement.
- **Shell command stalls** — Simple commands get stuck in “Waiting input” state after they have already finished, breaking automation.
- **Browser‑agent fragility** — Persistent browser profiles fail fast on lock contention; recovery mechanisms are missing.
- **Auto‑Memory loopiness** — Low‑signal sessions are retried indefinitely, and invalid patches are silently skipped without feedback.
- **Symlink & path‑normalization inconsistencies** — `.geminiignore`/`.gitignore` rules are not applied consistently across symbolic links.
- **Debug‑flag confusion** — The sandbox launcher and container entrypoint disagree on which values enable `DEBUG`, causing inconsistent behavior.
- **Tool‑limit errors** — Exceeding ~128–400 tools triggers a 400 error; users expect smarter scoping.
- **Whisper download robustness** — Interrupted downloads can leave partial model files; atomicity and chunk‑buffering fixes are critical.

---
*Generated from GitHub data for `google-gemini/gemini-cli` on 2026-08-20.*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-20

## 1. Today's Highlights

The Copilot CLI team shipped four rapid-fire patch releases (v1.0.81-2 through v1.0.81-5) in a single 24-hour window, signaling aggressive response to critical bugs in the MCP auth and sandbox subsystems. The hottest topic this cycle is a cluster of MCP/OAuth regressions affecting Atlassian and non-Microsoft providers, alongside enterprise users reporting that the sandbox is now forcing itself even when explicitly disabled via managed policy.

## 2. Releases

| Version | Notes |
|---|---|
| **v1.0.81-5** | Fixed: prompt submission while agent is working no longer leaves a `(pending)` ghost line in the transcript after the response completes. |
| **v1.0.81-4** | Fixes and changes |
| **v1.0.81-3** | Fixes and changes |
| **v1.0.81-2** | Fixes and changes |

> The multi-hotfix cadence suggests the team is patching several interrelated regressions introduced around v1.0.79–v1.0.81.

## 3. Hot Issues

1. **[CLOSED] #4390** — Enabled org models missing from CLI catalogue (Claude Sonnet 5 / Opus 5 / Kimi K3) · 7 👍 · 15 comments  
   Anthropic models explicitly enabled by Copilot Business orgs were silently unavailable. Affects every org-level Anthropic user; resolution likely included in the 1.0.81 patch series.  
   <https://github.com/github/copilot-cli/issues/4390>

2. **#4480** — Atlassian MCP OAuth fails with RFC 8414 §3.3 error on v1.0.79 (regression from 1.0.71) · 6 👍 · 6 comments  
   Remote MCP servers with issuer-URL mismatch during OAuth discovery are rejected. A clear regression that breaks existing Atlassian integrations.  
   <https://github.com/github/copilot-cli/issues/4480>

3. **#4490** — Atlassian MCP OAuth broken in v1.0.80 (same RFC 8414 regression) · 4 comments  
   Confirms the issue spans both 1.0.79 and 1.0.80, reinforcing it as a persistent auth-stack bug.  
   <https://github.com/github/copilot-cli/issues/4490>

4. **#2082** — `ctrl+shift+c` no longer copies to clipboard on Linux · 12 👍 · 24 comments  
   Long-standing bug (open since March) affecting a core Linux terminal expectation. High community empathy due to breadth of impact.  
   <https://github.com/github/copilot-cli/issues/2082>

5. **#4522** — Sandbox forces while managed policy is undetermined, overriding `sandbox.enabled=false` · 7 👍 · 2 comments  
   Enterprise users report that even with an explicit sandbox-disable config, a temporarily undetermined server policy causes the CLI to re-enable the sandbox. Directly conflicts with managed-permission workflows.  
   <https://github.com/github/copilot-cli/issues/4522>

6. **#4528** — Non-interactive sessions bypass `disableBypassPermissionsMode` managed setting · 0 👍 · 0 comments  
   `copilot -p` with `--allow-all` / `--yolo` grants permissions regardless of the org-managed `disableBypassPermissionsMode` setting, creating a security gap for automated pipelines.  
   <https://github.com/github/copilot-cli/issues/4528>

7. **#4533** — Terminal UI stops consuming events when parallel subagents spawn (1.0.81-4/5) · 0 👍 · 0 comments  
   UI deadlock: the Rust runtime continues working but the terminal panes go dead for input and scroll. A severe UX regression in the latest prerelease builds.  
   <https://github.com/github/copilot-cli/issues/4533>

8. **#4532** — Pending chat lines duplicate and fill the screen · 0 👍 · 0 comments  
   Submitting a prompt while the agent is working leaves a hanging `(pending)` line; repeated submissions stack duplicates. Related to the fix in v1.0.81-5.  
   <https://github.com/github/copilot-cli/issues/4532>

9. **#4519** — 400 "Missing namespace for function_call" on deferred/tool-search tools (1.0.80) · 0 👍 · 0 comments  
   Tools discovered via deferred search (e.g. `extensions_manage`) intermittently fail with a 400 error, indicating a namespace-tracking bug in the tool-catalog round-trip.  
   <https://github.com/github/copilot-cli/issues/4519>

10. **#4527** — `copilot -p` fails with 401 on GHEC data-residency tenants since 1.0.81-1 · 0 👍 · 0 comments  
    Non-interactive mode hits `api.githubcopilot.com` instead of the tenant endpoint for model-catalog fetch, breaking authenticated access for data-residency orgs.  
    <https://github.com/github/copilot-cli/issues/4527>

## 4. Key PR Progress

No pull requests were updated in the last 24 hours on the `github/copilot-cli` repository.

## 5. Feature Request Trends

- **Persistent session state** — Users want reasoning effort, model selection, and other config values to survive across CLI restarts (#4530, #4441).
- **Context compaction fidelity** — Request to preserve durable context (early decisions, gotchas) across repeated compaction cycles rather than recursively lossy summarization (#4441).
- **Plugin marketplace discoverability** — Search/filter support for `copilot plugin marketplace browse` as the marketplace grows (#4523).
- **Non-interactive security parity** — Ensure managed settings (e.g., `disableBypassPermissionsMode`) are respected in prompt mode just as they are in interactive mode (#4528).

## 6. Developer Pain Points

**Authentication & OAuth regressions** dominate the cycle. The Atlassian MCP OAuth break (spanning 1.0.79→1.0.80→1.0.81) and the GHEC data-residency 401 on `copilot -p` both point to an auth/endpoint routing regression introduced in recent patches. The forced `prompt=select_account` for non-Microsoft OAuth providers (#4526) is another symptom of over-eager Microsoft-centric auth handling.

**Sandbox policy overrides** are a second major friction point. Multiple reports (#4521, #4522, #4524) describe the sandbox either refusing to disable, re-enabling itself under undetermined policy, or being so restrictive it breaks `git` access — all eroding trust in enterprise permission controls.

**Terminal UX instability** in the 1.0.81 prereleases is acute: event deadlocks during parallel subagent spawns (#4533), duplicate pending lines (#4532), and Linux clipboard shortcut breakage (#2082) collectively make the CLI feel unstable for power users.

**Environment variable leakage** (#4531) — Copilot CLI exporting an empty `GIT_CONFIG_VALUE` breaks `git` discovery in child processes like VS Code, highlighting a gap in how the CLI sanitizes its env before spawning.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-20

## 1. Today's Highlights

One issue was resolved in the last 24 hours: issue #2609, where the built-in `Grep` and `Glob` tools consistently failed in ACP (Agent Control Protocol) sessions with the error "ACP runtime only supports interactive Bash tool processes." The issue has been closed, suggesting a fix or workaround was identified. No new releases or pull requests were published during this window.

## 2. Releases

No new releases in the last 24 hours. The current version remains **0.37.1**.

## 3. Hot Issues

**[#2609] Grep/Glob blocked in ACP sessions** — [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2609)
- **Summary:** The built-in `Grep` and `Glob` tools fail in ACP mode (via Zed) with the error "ACP runtime only supports interactive Bash tool processes." `Read` works fine, pointing to a tool-specific ACP compatibility gap.
- **Why it matters:** This directly blocks a core developer workflow — code search and file discovery — for users relying on ACP integration with Zed.
- **Status:** Closed (author: SolomonFang). No comments or upvotes yet.

*(Only 1 issue available from the last 24h.)*

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

Based on the available data:

- **ACP tool compatibility** — Users are hitting gaps where built-in tools (Grep, Glob) don't function within ACP sessions despite other tools (Read) working correctly. This signals a pattern of partial ACP integration that the community is actively encountering.
- **Terminal capability reporting** — The intermittent "ACP terminal capability is unavailable" error suggests tooling in ACP mode should be more robust about detecting and reporting terminal state.

## 6. Developer Pain Points

- **Inconsistent ACP tool support:** Built-in search and glob tools fail while other tools work, creating a frustrating experience for developers who expect parity across the toolset.
- **Intermittent terminal detection:** The "ACP terminal capability is unavailable" error appears sporadically, making debugging difficult and user experience unreliable.
- **Limited tool coverage in ACP mode:** Developers using Kimi Code CLI with ACP clients (e.g., Zed) are finding that the experience is not yet feature-complete compared to standard CLI usage.

---

*Data source: github.com/MoonshotAI/kimi-cli · Digest generated 2026-08-20*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑08‑20

## 1. Today's Highlights
No new releases were published in the last 24 hours. Community attention is focused on billing/usage discrepancies in OpenCode Go, provider integration stability (Bun, MCP, subagents), and core reliability fixes. Several pull requests advancing plugin tool decoding, model‑limit handling, and skill‑system improvements are in review.

## 2. Releases
*No new releases in the reporting window.*

## 3. Hot Issues
| Issue | Summary | Why It Matters | Community Reaction |
|-------|---------|----------------|---------------------|
| [#27906](https://github.com/anomalyco/opencode/issues/27906) | v1.15.1+ breaks Bun installs due to required postinstall scripts | Bun blocks postinstall scripts for global packages, breaking installation for many users | 14 👍, 24 comments |
| [#37852](https://github.com/anomalyco/opencode/issues/37852) | Aborted provider stream recorded as clean stop (finish=unknown, zero usage, no text) | Subagent returns empty responses without errors, masking generation failures | 56 👍, 19 comments |
| [#13626](https://github.com/anomalyco/opencode/issues/13626) | Auto‑sync projects in web UI from server | Users expect projects to appear automatically when opening OpenCode Web on a new device/browser | 15 👍, 12 comments |
| [#43367](https://github.com/anomalyco/opencode/issues/43367) | Subagents using `gpt‑5.6‑sol‑fast` fail when `prompt_cache_retention` is injected | Unsupported option causes subagent sessions to stop after tool execution | 10 👍, 2 comments |
| [#43409](https://github.com/anomalyco/opencode/issues/43409) | Abnormal credit consumption on OpenCode Go (42% used in ~4 hours) | Suggests a bug in usage tracking or model pricing, impacting subscription cost predictability | 3 comments |
| [#43424](https://github.com/anomalyco/opencode/issues/43424) | Weekly quota incorrectly exhausted — Go subscription (started Aug 18) | Quota depletion despite low actual spend (~$11), indicating possible billing reset issues | 3 comments |
| [#39876](https://github.com/anomalyco/opencode/issues/39876) | TUI temp copies consume 207 GiB | Tens of thousands of `libopentui.dylib` copies left in `$TMPDIR` fill disk space | 1 👍, 3 comments |
| [#40955](https://github.com/anomalyco/opencode/issues/40955) | Queued messages silently dropped when a turn is interrupted | Users lose messages when interrupting long turns (Esc or abort), causing data loss | 2 comments |
| [#43364](https://github.com/anomalyco/opencode/issues/43364) | Luna session not working in OpenCode Go | Provider returns `invalid_encrypted_content` error, breaking GPT‑5.6 Luna usage | 3 comments, 8 comments |
| [#43530](https://github.com/anomalyco/opencode/issues/43530) | MCP sessions rate‑limit after idle periods | Atlassian and GitHub Streamable HTTP MCP connections fail with rate limits after idle, unlike v1 | 2 comments |

## 4. Key PR Progress
| PR | Title | Description |
|----|-------|-------------|
| [#43460](https://github.com/anomalyco/opencode/pull/43460) | `fix(core): decode plugin tool input with the schema's own instance` | Fixes tool input decoding when a config plugin bundles a different `effect` version than the server. Closes #43322. |
| [#43282](https://github.com/anomalyco/opencode/pull/43282) | `fix(core): expose valid subagent IDs in the subagent tool` | The `subagent` tool now lists valid agent IDs in its schema, preventing invalid selections. Closes #36761. |
| [#43545](https://github.com/anomalyco/opencode/pull/43545) | `refactor(core): own resolved model limits` | Keeps catalog token limits on Core’s resolved model alongside capabilities/cost; simplifies compaction plumbing. |
| [#43541](https://github.com/anomalyco/opencode/pull/43541) | `fix(core): default unknown model token limits` | Defaults uncatalogued models to a 200k context window and 32k output limit, preserving explicit overrides. |
| [#42681](https://github.com/anomalyco/opencode/pull/42681) | `fix(desktop): show window on did‑finish‑load fallback for Wayland` | Adds a Linux‑only fallback to reveal the desktop window on `did‑finish‑load`, fixing window display on Wayland. Closes #42679. |
| [#42978](https://github.com/anomalyco/opencode/pull/42978) | `fix(app): show current worktree branch` | Correctly resolves the Git branch when a manually created worktree is opened in Desktop. Closes #42976. |
| [#42810](https://github.com/anomalyco/opencode/pull/42810) | `refactor(core): simplify interrupt continuation` | Replaces the run coordinator’s continuation state machine with a concise post‑cleanup check in `SessionExecution`. |
| [#43520](https://github.com/anomalyco/opencode/pull/43520) | `feat(client): optimistic prompt admission with client‑minted IDs` | Makes prompt sends idempotent and renders prompts immediately using client‑generated IDs, improving perceived responsiveness. |
| [#43538](https://github.com/anomalyco/opencode/pull/43538) | `feat: hot‑reload skills, commands, agents and config on file change` | Adds opt‑in hot‑reload (behind `OPENCODE_EXPERIMENTAL_HOT_RELOAD=true`) for skills, commands, agents, and config files. Closes #8751. |
| [#43537](https://github.com/anomalyco/opencode/pull/43537) | `feat

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑08‑20

## Today's Highlights
The community is focusing heavily on Windows compatibility and session‑scoped defaults, with the top‑commented issue (#7547) calling for clearer Windows‑setup guidance. A major behavioral change lands today: in‑session model and thinking‑level changes are now ephemeral by default (#5263/#8356), preventing accidental pollution of global settings. Gemini reasoning‑level handling and Bedrock redacted‑reasoning round‑trips receive bug‑fix attention in parallel PRs.

---

## Releases
No new releases published in the last 24 hours.

---

## Hot Issues

| # | Title | Status | Comments | Why It Matters |
|---|-------|--------|----------|----------------|
| #7547 | [Windows] sink‑thread – How do you use Pi on Windows? | OPEN | 31 | Centralized community feedback on Windows setup; shapes where docs, bug‑fixes, and out‑of‑box support will be prioritized. |
| #5263 | Make in‑session model/thinking changes ephemeral by default | CLOSED | 11 | Changes made during a session no longer leak into global defaults; users now must explicitly opt‑in via `/settings`. Community heavily upvoted (13 👍). |
| #5895 | Allow steering messages to opt out of waking the agent | CLOSED | 6 | Enables quiet background completions without interrupting an already‑finished turn. |
| #7829 | Invalid `settings.json` silently ignored; misleading ‘bash not found’ on Windows | CLOSED | 6 | Unescaped backslashes in `shellPath` now cause clear parse‑error feedback instead of cascading into “bash not found”. |
| #8183 | Document Windows Terminal `Ctrl+Shift+F` conflict | OPEN | 4 | Resolves a collision between Pi’s fullscreen transcript‑search shortcut and Windows Terminal’s own Find binding. |
| #8206 | `qwen3.6‑plus` & `minimax‑m2.7` routed as `openai‑completions` but only served on `/v1/messages` | OPEN | 4 | Catalog mismatch that can cause API‑endpoint confusion for developers using OpenCode Go. |
| #3966 | Add built‑in `--profile` support for isolated state | CLOSED | 4 | Allows completely separate auth, sessions, and settings per project (work vs. personal vs. local‑LLM). |
| #7994 | `reasoning_details` round‑trip only supports encrypted entries | CLOSED | 3 | OpenAI‑completions streams now preserve signed `reasoning.text`/`summary` entries, fixing replay for providers like OpenRouter. |
| #8323 | OpenAI client created with no timeout | CLOSED | 3 | Local models that think >10 min were being cut off by the SDK’s 600 s default; a timeout is now configurable. |
| #8322 | `isRecoverableLength` misses exact‑limit truncation | CLOSED | 3 | Fixes a bug where hitting `max_output_tokens` exactly was incorrectly treated as unrecoverable, dropping valid completions. |

**Community reaction:** Windows‑setup guidance and ephemeral‑session defaults generated the most discussion. Bug fixes for reasoning‑details round‑trips, timeout handling, and JSON‑parse errors received strong quiet support (no open debate, but many “no‑action” labels).

---

## Key PR Progress

| # | Title | Author | Status | Summary |
|---|-------|--------|--------|---------|
| #8383 | `fix(ai): derive Gemini's disabled‑thinking level from the catalog` | jingtao‑wisdomgraph | OPEN | Aligns Gemini’s thinking‑level detection with the model catalog instead of a hard‑coded regex, preventing incorrect “MINIMAL” assignment for models like `gemini‑3.7‑flash`. |
| #8356 | `fix(coding‑agent): keep model and thinking level changes session scoped` | cristinaponcela | CLOSED | Implements the ephemeral‑by‑default behavior requested in #5263. Model/thinking mutations now persist only for the active session unless explicitly saved via `/settings`. |
| #7784 | `refactor(agent): derive recovery state from record queries` | christianklotz | CLOSED | Removes recovery‑specific query APIs, derives state through bounded `findRecords()` calls, and retains write‑side open‑operation enforcement. Improves reliability and reduces SQLite query paths. |
| #8374 | `fix(coding‑agent): abort active run before forking from a user message` | elithecho | CLOSED | Prevents race conditions when forking during or immediately after a stop/retry, ensuring the active run is settled before creating the fork. |
| #8365 / #8366 | `feat: emit input event for built‑in slash commands` | kapkema | CLOSED | Exposes a deterministic `input` event for `/share`, `/export`, `/settings`, etc., giving extensions visibility into commands that previously executed before the LLM pipeline. |
| #8246 | `feat(ai): openai completions reasoning details` | cristinaponcela | CLOSED | Fixes dropping of signed `reasoning.text`/`summary` entries in `openai‑completions` streams, enabling round‑trip replay for providers like OpenRouter. |
| #8361 | `Add pi user‑agent to most api adapters` | davidbrai | CLOSED | Adds Pi’s default User‑Agent to seven API adapters (OpenAI‑responses/completions, Anthropic, Azure, Google, Mistral), aiding request tracking and provider‑side logging. |
| #8314 | `fix(ai): round‑trip Bedrock redacted reasoning` | seiji | CLOSED | Correctly handles Bedrock Converse’s encrypted `redactedContent` in `reasoningContent`, ensuring reasoning streams are preserved end‑to‑end. |
| #7953 | `fix(coding‑agent): expose tool metadata at stream start` | christianklotz | CLOSED | Includes `id` and `toolName` in `toolcall_start` events, giving extensions earlier access to tool context without paying for cumulative message snapshots. |
| #8346 | `fix(coding‑agent): repair unterminated session tails` | acmerfight | OPEN | Detects malformed or truncated JSONL session tails and repairs them before next append, preventing silent data loss on read‑only loads and forks. |

---

## Feature Request Trends

1. **Platform‑specific configuration** – Windows terminal key‑binding conflicts (#8183, #8372) and shell‑path parsing (#7829) highlight a need for platform‑aware defaults and clearer configuration guidance.
2. **State isolation & profiles** – Demand for `--profile` support (#3966) and per‑directory model‑selection persistence (#8376) shows users want clean separation between work, personal, and local‑LLM setups.
3. **Extensibility hooks** – Extensions frequently lack visibility into deterministic TUI operations (slash commands #8365, agent‑end continuations #8349). The community is pushing for more event emission points.
4. **Per‑model tuning** – Requests for model‑specific compaction profiles (#8133) and reasoning‑effort gating (#8381) indicate a desire for finer‑grained control over each provider’s behavior.
5. **Catalog accuracy** – Stale catalog entries (#8358) and routing mismatches (#8206) frustrate developers; there is a clear expectation that bundled catalogs stay in sync with upstream model listings.

---

## Developer Pain Points

- **Windows terminal conflicts** – Key bindings (e.g., `Ctrl+Shift+F` for fullscreen search) clash with terminal‑native shortcuts, forcing users to rebind or disable features.
- **Silent configuration failures** – Invalid JSON in `settings.json` (unescaped backslashes, UTF‑8 BOM) produces misleading downstream errors rather than explicit parse failures.
- **Reasoning‑details handling** – Providers that return `reasoning_details` in non‑encrypted form were dropping or mis‑routing signed text/summary entries, breaking replay and cost‑tracking.
- **Timeout & truncation edge cases** – Default 600 s timeouts cut off long‑running local models; exact‑hit `max_output_tokens` was incorrectly flagged as unrecoverable.
- **Catalog staleness** – Bundled model catalogs lag behind upstream listings, causing missing models or incorrect endpoint routing (e.g., `qwen3.6‑plus` routed to the wrong API surface).
- **Cache misses on forks** – Session‑scoped `prompt_cache_key` derivation means forking a session loses prompt‑cache hits, increasing cost and latency.
- **Extension invisibility** – Built‑in slash commands and agent‑end continuations execute outside the extension event pipeline, leaving extensions unable to intercept or monitor these operations.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-20

---

## 1. Today's Highlights

Qwen Code v0.21.14 shipped with the long-awaited `qwen sessions ps` command and live-session registry, enabling JSON-output-based management of running interactive sessions. The release also hardened CI/CD security by binding PAT-bearing autofix jobs to isolated container runners, and the SWE-bench Verified benchmark completed successfully across the full validation pipeline.

---

## 2. Releases

**v0.21.14** (latest stable)
- Added `qwen sessions ps` and a live-session registry for listing and managing active interactive sessions with JSON output.
- Introduced `clampReasoningEffort()` improvements for OpenAI-compatible providers.

**v0.21.11-nightly.20260819** — nightly build tracking the same feature set.

[Benchmarks](https://github.com/QwenLM/qwen-code): SWE-bench Verified 500 — **SUCCEEDED**; Terminal-Bench 2.0 89 — completed.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#9459](https://github.com/QwenLM/qwen-code/issues/9459) | `/effort max` bricks sessions on OpenAI-compatible providers | A UI-offered option causes every subsequent request to fail with a 400 until the tier is reverted. High-impact bug for users of external providers. |
| [#9089](https://github.com/QwenLM/qwen-code/issues/9089) | autofix PAT jobs share a host with untrusted branch code | Security-critical: runner-level isolation is required but cannot be solved from within a GitHub Actions step. Blocks full autofix hardening. |
| [#9509](https://github.com/QwenLM/qwen-code/issues/9509) | Agent launch failures reported as successful tool calls | The scheduler misclassifies agent failures as success because the `error` field is omitted. Affects subagent reliability. |
| [#9454](https://github.com/QwenLM/qwen-code/issues/9454) | Model switches reuse token counts from the previous route | `GeminiChat` leaks prompt/output counts across model/auth/wire switches, corrupting token accounting. |
| [#9450](https://github.com/QwenLM/qwen-code/issues/9450) | `task_list` falsely triggers duplicate tool-call loop detection | Identical `task_list` args can yield different results during team state changes, causing premature agent termination. |
| [#9219](https://github.com/QwenLM/qwen-code/issues/9219) | `/review` presubmit overlap matching is exact-line only | Multi-line comments and semantic duplicates pass undetected, weakening review quality. |
| [#9309](https://github.com/QwenLM/qwen-code/issues/9309) | Context compression produces incorrect results | `/compress-fast` followed by `/compress` yields unexpected token counts; users report context not actually shrinking. |
| [#9493](https://github.com/QwenLM/qwen-code/issues/9493) | Persistent "update available" notification on every Homebrew startup | Minor but annoying: the CLI shows an update banner each session even when no new release has landed. |
| [#9494](https://github.com/QwenLM/qwen-code/issues/9494) | Slash command menu resets while response streams | UX bug: selecting a non-first command in the `/` menu occasionally jumps back to the first item mid-stream. |
| [#8596](https://github.com/QwenLM/qwen-code/issues/8596) | Deprecate Electron desktop app, rename desktop-shell to desktop | Community signal that Tauri is the future; this issue tracks the transition and naming consolidation. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#9527](https://github.com/QwenLM/qwen-code/pull/9527) | fix(autofix): bind sandbox image to pulled digest | Re-lands a critical security fix from the frozen #9214: the exported sandbox image is now pinned to the digest it was pulled from, closing a trust-gap. |
| [#9214](https://github.com/QwenLM/qwen-code/pull/9214) | feat(autofix): run verification gate in ephemeral container | Phase 1+2 of runner-level isolation for PAT-bearing autofix steps. Still in review after 11 rounds; the diff grew from 329 to 2,700 lines. |
| [#9402](https://github.comgithub.com/QwenLM/qwen-code/pull/9402) | feat: agent board — share work across agents | Filesystem-backed board MVP letting independently started agents share and coordinate work. Earlier version was repurposed after a mistaken deletion proposal. |
| [#9520](https://github.com/QwenLM/qwen-code/pull/9520) | docs(agents): add agent orchestration contract | Design doc mapping all six agent launch routes (in-process, forks, named teammates, workflow agents, Cursor SDK, Cursor CLI) and their frontmatter resolution. |
| [#9441](https://github.com/QwenLM/qwen-code/pull/9441) | fix(core): show edit/exec diffs on PreToolUse ask | When a PreToolUse hook returns `ask`, the confirmation UI now shows the actual edit/exec diff instead of a synthetic plain-text prompt. |
| [#9297](https://github.com/QwenLM/qwen-code/pull/9297) | fix(autofix): BLOCKED handoff as first-class round outcome | The growth-brake `BLOCKED` handoff now produces valid round output instead of dying as "finished without required output files." |
| [#9303](https://github.com/QwenLM/qwen-code/pull/9303) | fix(web-shell): bound daemon transcript retention | Stops renderer OOM crashes by capping daemon session history retained in the browser; raw replay snapshots are released after injection. |
| [#9498](https://github.com/QwenLM/qwen-code/pull/9498) | fix(ci): heal symlinked workspace instead of wedging runner | Adds workspace healing to hardened pool wipes, preventing runner wedging when a previous job replaced the workspace with a symlink. |
| [#9350](https://github.com/QwenLM/qwen-code/pull/9350) | feat(dingtalk): support outbound file delivery | Native outbound file delivery for the DingTalk channel — validates, uploads, and sends local files via DingTalk's media API. |
| [#9426](https://github.com/QwenLM/qwen-code/pull/9426) | feat(serve): persist prompt terminal ledger | Each session now keeps an append-only ledger of prompt lifecycle outcomes as a sidecar file, enabling cold-load reconciliation. |

---

## 5. Feature Request Trends

- **Advisor / read-only review feedback loop** — Two linked issues (#6542, #9036) call for a Claude Code–aligned Advisor tool that inspects session context and returns structured guidance before major work, at stalls, and before task completion.
- **Subagent progress streaming & usage visibility** — Issue #9522 requests hierarchical subagent progress streaming and self/subtree token usage display in the terminal and agent panel.
- **Desktop shell consolidation** — Issue #8596 pushes for deprecating the Electron app and renaming the Tauri shell to `packages/desktop`, signaling community confidence in the Tauri path.
- **OpenAI Response API support** — Issue #889 continues to request native support for the OpenAI Responses API, critical for using models like gpt-5-codex.
- **Cross-package contract consistency** — Issue #9151 asks for a single owner of constants/contracts across package boundaries with drift-checking, reflecting pain from duplicated state.

---

## 6. Developer Pain Points

1. **Session & state management fragility** — Token count leakage across model switches (#9454), false duplicate-detection in team workflows (#9450), and compression producing incorrect results (#9309) all point to shared-state hygiene issues that compound during complex multi-session work.
2. **CI/CD runner isolation gaps** — The PAT-bearing job hardening (#9089, #9214) has consumed 11 review rounds with an expanding diff, highlighting the tension between security hardening and review velocity.
3. **UI regressions during streaming** — Slash command menu reset (#9494) and the `/effort max` brick (#9459) are examples of interactive UX breaking under live-state conditions.
4. **Error-handling invisibility** — Agent launch failures swallowed as successful tool calls (#9509) and `ask_user_question` returning opaque decline messages (#9011) make debugging agent behavior unnecessarily hard.
5. **Persistent low-grade noise** — The Homebrew update banner (#9493) and cross-package constant drift (#9151) are recurring annoyances that erode developer trust in release stability.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026‑08‑20

## 1. Today’s Highlights
No new release landed in the last 24 h, but the project shipped **v0.9.10** (PR #5513) focusing on retention hardening, first‑run identity, and durable approvals. Several high‑impact bugs were closed—including a VS Code crash with YOLO Agent (#1651), SSH‑sandbox connectivity failures (#1829), and an early emergency‑compaction regression on DeepSeek‑V4 routes (#5518)—while the Chinese‑documentation localization initiative (#5482) made concrete progress with Tier 1 deliverables (PR #5507).

## 2. Releases
*None in the past 24 h.*  
The most recent release, **v0.9.10**, was published yesterday (PR #5513) and carries 76 commits covering retention limits, first‑run identity handling, and durable one‑shot approval outcomes.

## 3. Hot Issues
| Issue | Why It Matters | Community Reaction |
|-------|----------------|-------------------|
| [#5056](https://github.com/Hmbown/CodeWhale/issues/5056) – flaky verifier background tests | Parallel‑suite test reliability is a blocker for fast CI and confident releases. | 9 comments, 0 👍 |
| [#1425](https://github.com/Hmbown/CodeWhale/issues/1425) – session hangs after large‑text multi‑agent processing | Multi‑chunk analysis (e.g., 3‑M‑word novels) triggers `agent_wait` timeout and leaves the session in a stuck state. | 8 comments, 0 👍 |
| [#1651](https://github.com/Hmbown/CodeWhale/issues/1651) – VS Code crashes when YOLO Agent runs tests in background | Stability regression for developers using the integrated terminal with autonomous test scripts. | 7 comments, 0 👍 |
| [#1829](https://github.com/Hmbown/CodeWhale/issues/1829) – SSH exit‑code 255 inside TUI shell sandbox | Outbound TCP 22 appears blocked in the sandboxed shell, breaking remote‑host workflows. | 7 comments, 0 👍 |
| [#5508](https://github.com/Hmbown/CodeWhale/issues/5508) – request for continuous‑loop mode | Users want an “infinite turn until interrupted” option for coordinator‑style AI workflows. | 3 comments, 0 👍 |
| [#5518](https://github.com/Hmbown/CodeWhale/issues/5518) – emergency compaction at ~85–105 K tokens despite 327 K context | Suggests excessive output‑headroom budgeting or handoff‑state contamination on DeepSeek‑V4 routes. | 3 comments, 0 👍 |
| [#5023](https://github.com/Hmbown/CodeWhale/issues/5023) – IME candidate window jumps during input | Unstable input‑method rendering degrades the authoring experience on Windows 11. | 2 comments, 0 👍 |
| [#5516](https://github.com/Hmbown/CodeWhale/issues/5516) – HTTP 400 `max_tokens=384000 exceeds model limit` after upgrade to v0.9.9 | Default `max_tokens` now exceeds the local vLLM model’s `max_total_tokens`, causing every request to fail. | 1 comment, 0 👍 |
| [#5472](https://github.com/Hmbown/CodeWhale/issues/5472) – every Bash call retains full stdout/stderr in memory for 1 h | Compounds memory pressure during long sessions with parallel builds or heavy tool output. | 1 comment, 0 👍 |
| [#5478](https://github.com/Hmbown/CodeWhale/issues/5478) – `/rename` mid‑turn leaves tool row stuck at “running” | UI state desynchronizes when session name is changed while a shell tool is in flight. | 1 comment, 0 👍 |

*Open issues worth watching:*  
[#5519](https://github.com/Hmbown/CodeWhale/issues/5519) – `isZh` migration losing ground;  
[#5482](https://github.com/Hmbown/CodeWhale/issues/5482) – EPIC to localize all docs into Chinese.

## 4. Key PR Progress
| PR | Summary |
|----|---------|
| [#5513](https://github.com/Hmbown/CodeWhale/pull/5513) – **v0.9.10 release** | 76‑commit lane covering retention limits, first‑run identity, and durable one‑shot approval persistence. |
| [#5515](https://github.com/Hmbown/CodeWhale/pull/5515) – fix MCP image forwarding | Converts standard MCP `image` content into provider‑neutral rich tool‑result blocks, preserving text/structured content and the existing 5 MiB single‑image limit. |
| [#5509](https://github.com/Hmbown/CodeWhale/pull/5509) – restore `/title` as independent command | Splits `/title` back from `/rename` so terminal window title can be set without altering the session name. |
| [#5514](https://github.com/Hmbown/CodeWhale/pull/5514) – refactor stream processing | Extracts the response‑stream state machine into `process_stream`, simplifying the turn‑loop and keeping post‑stream assembly in the outer context. |
| [#5517](https://github.com/Hmbown/CodeWhale/pull/5517) – move docs onto dictionary spine | Continues the `isZh` migration by wiring `docs/constitution` and `docs/runtime‑api` through the i18n dictionary system. |
| [#5507](https://github.com/Hmbown/CodeWhale/pull/5507) – Tier 1 Chinese docs localization | Restructures the docs tree into per‑language folders and migrates existing Chinese translations into `docs/zh_hans/`. |
| [#5510](https://github.com/Hmbown/CodeWhale/pull/5510) – restore README star‑history chart | Re‑adds the star‑history chart now that GitHub’s third‑party access restrictions no longer block it. |
| [#5455](https://github.com/Hmbown/CodeWhale/pull/5455) – Signal Cut whale empty‑state art | Redraws the empty‑state whale illustration with proper body‑fluke proportions and visual weight. |
| [#5390](https://github.com/Hmbown/CodeWhale/pull/5390) – bump `rmcp` 2.2.0 → 3.1.2 | Updates the Model Context Protocol Rust SDK to the latest stable release. |
| [#5491](https://github.com/Hmbown/CodeWhale/pull/5491) – persist approval outcomes before execution | Writes each approval request and its terminal outcome to a session log before the tool runs, enabling durable one‑shot approvals and stale‑decision rejection on resume. |

## 5. Feature‑Request Trends
* **Coordinator‑style infinite loops** (#5508) – users want a persistent turn mode for AI‑orchestrator workflows.
* **Granular terminal‑title control** – the community split `/title` from `/rename` (#5509) to allow independent window‑title management.
* **Chinese documentation localization** – a sustained push (EPIC #5482, PR #5507/#5517) to make all docs accessible to Mandarin‑speaking developers.
* **MCP image‑content support** (#5515) – demand for richer tool‑result rendering (images, structured content) while keeping size limits.
* **Durable approval state** (#5360, #5491) – desire for approval decisions to survive session restarts and be recorded in the log.

## 6. Developer Pain Points
* **Test‑suite flakiness under parallel execution** (#5056) – verifier background tests and workspace‑sensitive fixtures intermittently fail, slowing CI.
* **Session hangs on large‑scale multi‑agent jobs** (#1425) – `agent_wait` timeouts during parallel chunk processing leave the UI unresponsive.
* **Configuration drift after upgrades** (#5516) – default `max_tokens` now exceeds local model limits, breaking requests without manual config changes.
* **Sandboxed network restrictions** (#1829) – outbound SSH (TCP 22) is blocked inside the TUI shell, forcing workarounds for remote‑host workflows.
* **Memory retention from Bash output** (#5472) – full stdout/stderr of every shell command is kept in memory for an hour, aggravating swap pressure during long sessions.
* **Input‑method instability on Windows** (#5023) – IME candidate windows jump or become unstable during active typing.
* **UI desynchronization on mid‑turn rename** (#5478) – changing the session name while a shell tool is running leaves the tool row stuck in a “running” state.

---

*Generated from GitHub data for `github.com/Hmbown/DeepSeek-TUI` as of 2026‑08‑20.*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*