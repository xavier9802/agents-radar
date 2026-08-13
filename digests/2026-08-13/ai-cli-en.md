# AI CLI Tools Community Digest 2026-08-13

> Generated: 2026-08-13 02:27 UTC | Tools covered: 10

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
**Date: 2026-08-13**

---

## 1. Ecosystem Overview

The AI CLI tool landscape is maturing rapidly, with established players (Claude Code, Codex, Gemini CLI, Copilot CLI) pushing toward enterprise-grade reliability while challengers (OpenCode, Kimi Code CLI, Pi, Qwen Code) compete on flexibility, local-model support, and specialized workflows. Stability and session durability have emerged as the dominant engineering challenge across all tools — context management, subprocess reliability, and state persistence are the new "hello world." The competitive axis is shifting from raw model capability toward agent orchestration quality, with multi-agent coordination, MCP tooling, and configurable evaluation becoming key differentiators.

---

## 2. Activity Comparison

| Tool | New Releases (24h) | Open Hot Issues | Closed PRs (24h) | Active PRs (24h) |
|---|---|---|---|---|
| **Claude Code** | 1 (v2.1.229) | 10 | 2 (docs) | 1 (open) |
| **OpenAI Codex** | 0 | 10 | 10 | 0 |
| **Gemini CLI** | 1 (nightly) | 10 (3 closed) | 9 | 0 |
| **GitHub Copilot CLI** | 0 | 8 (2 closed) | 1 | 1 |
| **Kimi Code CLI** | 0 | 1 | 0 | 2 |
| **OpenCode** | 2 (v1.18.17/18) | 10 | 10 | 0 |
| **Pi** | 0 | 8 (4 closed) | 9 | 0 |
| **Qwen Code** | 1 (desktop v0.2.1) | 10 | 0 | 10 |
| **DeepSeek TUI (CodeWhale)** | 1 (v0.9.6) | 7 (3 closed) | 4 | 4 |
| **Grok Build** | 0 | — | 0 | 0 |

> **Key observation:** OpenAI Codex and Gemini CLI show the highest PR throughput (10 each), while Qwen Code has the most active PR pipeline (10 open). Claude Code and Copilot CLI are in quieter merge windows. Kimi Code CLI and Grok Build show minimal recent activity.

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|---|---|---|
| **Session durability & recovery** | Claude Code, Codex, Pi, CodeWhale, Qwen Code | Crash-safe state, durable transcripts, resume correctness — all tools report bugs where session recovery diverges from in-memory state |
| **Local/edge model integration** | Pi, OpenCode, Gemini CLI | Ollama proxy (Pi #8049), custom provider model discovery (Copilot #4358), local model listing demand across communities |
| **MCP tooling maturity** | Gemini CLI, Copilot CLI, OpenCode, CodeWhale | Auth fragility (Copilot #4464/#4463), spec compliance (CodeWhale #5335), tool visibility gaps (OpenCode #33027), config corruption risks (Gemini #28794) |
| **Multi-agent coordination** | Claude Code, Qwen Code, OpenCode | Cross-session messaging, durable replay, subagent model fidelity — repeatedly flagged as a pain point |
| **Config hot-reload** | OpenCode, Gemini CLI | Users want configuration changes without restart; OpenCode #6815 has 88 👍 |
| **Subscription/billing transparency** | Codex, OpenCode | Rate-limit accounting errors (Codex #31606), "free usage exceeded" false positives (OpenCode #42043/#42132/#42140/#42154/#42114) |
| **Windows desktop stability** | Codex, Claude Code, Copilot CLI | Process leaks, WMI exhaustion, GPU crashes, crash loops — Windows is the common weak spot |

---

## 4. Differentiation Analysis

| Dimension | Tools Leading | Tools Following |
|---|---|---|
| **Enterprise/managed deployment** | Codex (gRPC code-mode hosts, remote executors), Copilot CLI (CIMD OAuth, org model catalog) | Claude Code (self-hosted runner hooks), Qwen Code (web-shell workspace mgmt) |
| **Open-source flexibility** | OpenCode (multi-provider, local model support, skill system), Pi (Ollama proxy, custom providers) | Gemini CLI (eval infrastructure, A2A server) |
| **Desktop UX investment** | Qwen Code (Tauri desktop, workflow visualization), Pi (TUI mouse events, Mermaid export, themes) | Claude Code (desktop crash issues), CodeWhale (PiP window, interactive plugin manager) |
| **Local-first / lightweight** | Gemini CLI (power users advocating against Antigravity bloat), Kimi Code CLI (minimal footprint) | OpenCode (local skill paths, local model bridging) |
| **Model breadth** | OpenCode (Kimi, xAI, Azure, DeepSeek, Gemini), Pi (Grok 4.6, Ollama, Scaleway) | Claude Code (Anthropic-only), Codex (OpenAI-only), Copilot (multi-provider but org-restricted) |
| **Eval & testing infrastructure** | Gemini CLI (component-level behavioral evals, 76 tests), Pi (Mermaid/LaTex HTML export) | OpenCode (robust retry logic, jitter), CodeWhale (durable replay journal) |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **OpenAI Codex** — 10 PRs closed in 24h, aggressive investment in observability, thread durability, and executor infrastructure. The closed PR wave signals a team that is shipping hard.
- **Qwen Code** — 10 active PRs spanning workflow visualization, durable replay, and desktop architecture. The Tauri migration and web-shell expansion show strategic direction.
- **Gemini CLI** — Strong PR velocity (9 closed) with security hardening as a theme. Nightly releases indicate a rapid feedback loop.

**Stable but constrained:**
- **Claude Code** — Active issue resolution but low PR velocity. Docs-only PRs suggest the team is triaging community reports rather than shipping features. The Fable 5 safety-filter and prompt-cache issues are eroding confidence.
- **OpenCode** — Two releases in one day shows responsiveness, but the tool is absorbing bugs from its breadth (Azure hangs, DeepSeek multi-turn, Gemini function-calling failures).

**Growing communities:**
- **Pi** — High community engagement on local model integration and TUI polish. The Ollama proxy and Grok 4.6 additions show the team is listening.
- **CodeWhale** — Strong contributor momentum with harvested PRs; the interactive plugin manager and PiP features indicate a maturing ecosystem.

**Quiet / niche:**
- **Kimi Code CLI** — Minimal activity; the dominant issue (#1283 Memory System) has been open since February 2026.
- **GitHub Copilot CLI** — Quiet merge window; top issue (#1305 CIMD OAuth) remains open, suggesting enterprise auth is a long pole.
- **Grok Build** — Zero activity.

---

## 6. Trend Signals

1. **Session state is the new battleground.** Every tool is grappling with context overflow, compaction correctness, and crash recovery. The auto-compaction bug in Pi (#6879, 17 👍) and Codex (#32888) mirrors Qwen Code's MAX_TOKENS divergence (#8979). Developers should expect continued investment in durable state management across the ecosystem.

2. **MCP is becoming a compliance minefield.** From CodeWhale's `nextCursor: null` spec violation to Copilot's OAuth fragility to OpenCode's tool-visibility gaps, MCP integration is the fastest-growing surface area and the most error-prone. Tools that get MCP right (or at least spec-compliant) will gain enterprise trust.

3. **Windows is the universal weak point.** Five distinct Windows-specific issues in Codex alone, plus GPU crashes and crash loops in Claude Code, control-key regressions in Copilot CLI, and process-leak storms. Any tool targeting Windows users needs to demonstrate regression testing parity with macOS/Linux.

4. **The Antigravity bifurcation signals market segmentation.** Gemini CLI's community is actively pushing back against token-heavy agent patterns (#27858, 13 👍), favoring lightweight CLI efficiency. This suggests a durable split between "surgical CLI" and "full agent" philosophies.

5. **Local model access is table-stakes.** Pi's Ollama proxy, OpenCode's multi-provider flexibility, and Copilot's BYOK gaps (#4358) all point to a community that refuses to be locked into a single provider. Tools that make local model integration first-class will win developer loyalty.

6. **Billing transparency matters more than advertised.** OpenCode's subscription confusion thread and Codex's rate-limit accounting bug both indicate that users lose trust faster on billing issues than on feature gaps. Expect this to become a competitive differentiator.

7. **Multi-agent coordination is unsolved.** Claude Code's 12-coordination-failure post-mortem (#54393), Qwen Code's background agent gaps (#8097), and subagent model-fidelity issues in both Copilot CLI (#4432/#3565) and Gemini CLI (#22323) reveal that autonomous agent workflows remain fundamentally brittle. Tools that solve this reliably will define the next generation.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-13 · Source: github.com/anthropics/skills**

---

## 1. Top Skills Ranking

### #1 — Self-Audit Skill (`feat(skills): add self-audit — mechanical verification + four-dimension reasoning quality gate`)
**PR [#1367](https://github.com/anthropics/skills/pull/1367)** · Open · Author: YuhaoLin2005
A universal output-quality skill that performs mechanical file verification first, then applies a four-dimension reasoning audit ordered by damage severity. Works across any project, tech stack, or model. Represents a shift toward pre-delivery quality gates in agent workflows.

### #2 — Skill Creator Evaluation Fixes (`fix(skill-creator): run_eval.py always reports 0% recall`)
**PR [#1298](https://github.com/anthropics/skills/pull/1298)** · Open · Author: MartinCajiao
Addresses a critical bug where `run_eval.py` consistently reported `recall=0%` across all skill descriptions, breaking the entire description-optimization loop. Also fixes Windows stream reading, trigger detection, and parallel worker issues. Tied to Issue [#556](https://github.com/anthropics/skills/issues/556).

### #3 — Testing Patterns Skill (`feat: add testing-patterns skill`)
**PR [#723](https://github.com/anthropics/skills/pull/723)** · Open · Author: 4444J99
Covers the full testing stack: Testing Trophy philosophy, AAA unit-test pattern, pure-function/edge-case strategies, and React component testing with Testing Library. Fills a significant gap in the current skills collection.

### #4 — Skill Quality & Security Analyzers (`Add skill-quality-analyzer and skill-security-analyzer to marketplace`)
**PR [#83](https://github.com/anthropics/skills/pull/83)** · Open · Author: eovidiu
Two meta-skills that evaluate skills across five dimensions: Structure & Documentation (20%), Correctness, Completeness, Safety, and Usability. These provide tooling for the community to validate and score contributions.

### #5 — ServiceNow Platform Skill (`feat: add ServiceNow platform skill`)
**PR [#568](https://github.com/anthropics/skills/pull/568)** · Open · Author: Vanka07
A broad ServiceNow assistant covering ITSM, ITOM, ITAM/SAM Pro, FSM, HRSD/CSM, SPM/PPM, Vulnerability Response, Security Incident Response, and IntegrationHub. Targets enterprise workflows.

### #6 — Document Typography Skill (`Add document-typography skill`)
**PR [#514](https://github.com/anthropics/skills/pull/514)** · Open · Author: PGTBoos
Prevents common typographic defects in AI-generated documents: orphan word wraps, widow paragraphs, and numbering misalignment. Addresses a universally felt but rarely voiced pain point.

### #7 — ODT Skill (`Add ODT skill`)
**PR [#486](https://github.com/anthropics/skills/pull/486)** · Open · Author: GitHubNewbie0
Enables creation, filling, reading, and conversion of OpenDocument Format files (.odt, .ods). Triggers on mentions of ODT, ODF, LibreOffice, or open-source document standards. Fills a gap alongside the existing DOCX/PDF skills.

### #8 — Skill Creator Windows Fixes
**PR [#1099](https://github.com/anthropics/skills/pull/1099)** & **# [#1050](https://github.com/anthropics/skills/pull/1050)** · Open · Authors: joshuawowk, gstreet-ops
Two separate PRs fixing `run_eval.py` crashes and subprocess encoding issues on Windows. Critical for platform parity of the skill-creator toolchain.

---

## 2. Community Demand Trends

| Trend | Supporting Issues |
|---|---|
| **Trust & security validation** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍) — namespace impersonation concerns; [#412](https://github.com/anthropics/skills/issues/412) — agent governance skill proposal |
| **Organizational skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) — shared skill library or direct sharing links |
| **Context-window efficiency** | [#1487](https://github.com/anthropics/skills/issues/1487) — `claude-api` skill eagerly injects ~156k tokens in a single call |
| **Reasoning quality pipelines** | [#1385](https://github.com/anthropics/skills/issues/1385) — three-gate pipeline (calibration → adversarial review → delivery verification) |
| **Multi-platform support** | [#29](https://github.com/anthropics/skills/issues/29) — AWS Bedrock compatibility; [#16](https://github.com/anthropics/skills/issues/16) — expose skills as MCPs |
| **Context hygiene** | [#1329](https://github.com/anthropics/skills/issues/1329) — compact-memory symbolic notation for long-running agents |

---

## 3. High-Potential Pending Skills

| PR | Skill | Why It May Land Soon |
|---|---|---|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-audit** | Directly addresses the reasoning-quality-gate proposal (#1385); both by the same author |
| [#723](https://github.com/anthropics/skills/pull/723) | **Testing patterns** | Comprehensive scope with broad relevance; no conflicting reviews noted |
| [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow platform** | Enterprise-class coverage; most recently updated (2026-08-12) |
| [#514](https://github.com/anthropics/skills/pull/514) | **Document typography** | Solves a universal pain point with narrow, well-scoped functionality |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT skill** | Completes the document-format triad alongside existing DOCX and PDF skills |
| [#1538](https://github.com/anthropics/skills/pull/1538) | **Spec compliance fix** | Brings two skills back in line with the Agent Skills spec — likely quick merge |
| [#1479](https://github.com/anthropics/skills/pull/1479) | **Plan-file hygiene** | Addresses a recognized lifecycle gap (#1417); explicitly open to handoff |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for quality-gating and trust infrastructure** — skills that verify their own output, validate other skills, enforce security boundaries, and prevent context-window abuse — reflecting a maturing ecosystem where users are moving beyond single-task automation toward reliable, auditable agent workflows.

---



# Claude Code Community Digest — 2026-08-13

## 1. Today's Highlights

Anthropic shipped **v2.1.229** with SSE keepalive pings, remote-control session resumption docs, and server-supplied hook support for self-hosted runners. Community attention is dominated by **Fable 5 safety-flag false positives** hitting legitimate coding work and a **prompt-cache invalidation bug** triggered by background auto-updates — both generating fresh reports today.

## 2. Releases

**v2.1.229** — [GitHub](https://github.com/anthropics/claude-code/releases)

- Documented `claude remote-control --continue` for resuming the most recent Remote Control session.
- Added server-supplied Claude Code hook support for self-hosted runner sessions, matching managed-environment behavior.
- Added SSE keepalive pings to gateway streaming responses.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved org still receiving cyber-safeguard blocks | CVP-approved organizations are being blocked again; the Verification Portal shows "Under review" despite prior approval. Affects enterprise trust. | 82 comments · 12 👍 |
| [#14061](https://github.com/anthropics/claude-code/issues/14061) | `/plugin update` does not invalidate plugin cache | Plugin updates silently serve stale code until a full restart — a persistent pain point for plugin authors. | 25 comments · 31 👍 |
| [#75899](https://github.com/anthropics/claude-code/issues/75899) | Left arrow navigates to agents screen (not rebindable) | A core keybinding issue that breaks workflow; users can't recover the chat view without a restart. | 15 comments · 19 👍 |
| [#24172](https://github.com/anthropics/claude-code/issues/24172) | Conversations disappear when closing VSCode or navigating away | **Critical data-loss bug** — chat history becomes unrecoverable. Affects Windows users most. | 12 comments · 25 👍 |
| [#81698](https://github.com/anthropics/claude-code/issues/81698) | GPU process crash kills entire app and all sessions | RTX 5080 laptop GPU crash (exit code 101457950) takes down the whole desktop app and all Claude Code sessions. | 25 comments · 0 👍 |
| [#85199](https://github.com/anthropics/claude-code/issues/85199) | Desktop app repeatedly crashes, requires "Repair" | Windows users report a crash loop needing manual repair via Advanced Options — suggests a deeper regression. | 13 comments · 0 👍 |
| [#79366](https://github.com/anthropics/claude-code/issues/79366) | Worktree sessions reuse existing directories | Breaks worktree isolation guarantees; new sessions land in stale directories from prior unrelated work. | 11 comments · 7 👍 |
| [#82162](https://github.com/anthropics/claude-code/issues/82162) | Opus 5.0 quality regression | Users report Opus 5.0 producing worse results than previous versions, even after multiple retries. | 9 comments · 3 👍 |
| [#86241](https://github.com/anthropics/claude-code/issues/86241) | Frequent invalid Fable 5 safeguard flags | Legitimate coding, cybersecurity, and biology tasks are being blocked by over-broad safety filters. | 1 comment · 1 👍 |
| [#86244](https://github.com/anthropics/claude-code/issues/86244) | Background auto-update invalidates prompt cache | Every `--resume` after an auto-update re-caches the entire context, burning tokens and time. Filed today. | 1 comment · 0 👍 |

## 4. Key PR Progress

| # | Title | Status | Details |
|---|-------|--------|---------|
| [#85925](https://github.com/anthropics/claude-code/pull/85925) | docs: point remaining stale doc links at code.claude.com | ✅ Closed | Swaps remaining `docs.claude.com` links to canonical `code.claude.com` targets across plugins and issue templates. |
| [#85822](https://github.com/anthropics/claude-code/pull/85822) | docs: fix stale doc links and README drift in plugins | ✅ Closed | Fixed hooks and plugins doc links that only redirected; verified against live URLs. |
| [#41611](https://github.com/anthropics/claude-code/pull/41611) | add the missing source to claude code | 🔄 Open | Long-standing request to include source code in releases — no progress since March. |

> **Note:** Only 3 PRs were active in the last 24 hours, all docs-only or stale. No feature or bugfix PRs landed.

## 5. Feature Request Trends

- **Agent session lifecycle controls** — Users want the ability to mark agent sessions as completed/dismissed from the agents view without needing input ([#66202](https://github.com/anthropics/claude-code/issues/66202), 20 👍).
- **Collapsed thinking-block UX** — Desktop app needs a clear affordance for collapsing expanded thinking blocks and preserving scroll position ([#83418](https://github.com/anthropics/claude-code/issues/83418)).
- **Agent view "needs input" indicator** — The alive/sleeping distinction exists for done sessions but not for blocked ones; users want visual parity ([#86082](https://github.com/anthropics/claude-code/issues/86082)).
- **Rust rewrite for performance** — Persistent request to reimplement the terminal layer in Rust to eliminate CPU spikes and flickering ([#84192](https://github.com/anthropics/claude-code/issues/84192)).
- **Better plugin cache management** — Repeated requests for `/plugin update` to properly invalidate caches ([#14061](https://github.com/anthropics/claude-code/issues/14061)).

## 6. Developer Pain Points

1. **Safety-filter false positives (Fable 5)** — The top recurring complaint. Legitimate code, security research, and biology tasks are being flagged. Multiple fresh reports today ([#86197](https://github.com/anthropics/claude-code/issues/86197), [#86241](https://github.com/anthropics/claude-code/issues/86241), [#84352](https://github.com/anthropics/claude-code/issues/84352)).
2. **Prompt-cache invalidation** — Both background auto-updates ([#86244](https://github.com/anthropics/claude-code/issues/86244)) and `git status` changes ([#78720](https://github.com/anthropics/claude-code/issues/78720)) are silently busting the prompt cache, costing tokens and slowing sessions.
3. **Conversation data loss** — Chat history disappearing on VSCode close/navigate ([#24172](https://github.com/anthropics/claude-code/issues/24172)) remains an unresolved critical bug.
4. **Multi-agent coordination bugs** — Post-mortem documenting 12 coordination failures across a single overnight cycle highlights systemic instability in autonomous agent workflows ([#54393](https://github.com/anthropics/claude-code/issues/54393)).
5. **Opus 5.0 quality regression** — Users report hallucinated responses and worse output quality compared to Opus 4.8 ([#82162](https://github.com/anthropics/claude-code/issues/82162), [#82326](https://github.com/anthropics/claude-code/issues/82326), [#86205](https://github.com/anthropics/claude-code/issues/86205)).
6. **MCP server instability** — Servers being silently killed and respawned mid-session with sessionId leaks ([#86040](https://github.com/anthropics/claude-code/issues/86040)), and draft-07 outputSchema servers being rejected client-side ([#86142](https://github.com/anthropics/claude-code/issues/86142)).
7. **Windows desktop crashes** — GPU process crashes ([#81698](https://github.com/anthropics/claude-code/issues/81698)) and repeated crash loops requiring manual repair ([#85199](https://github.com/anthropics/claude-code/issues/85199)) are disrupting Windows users.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-13

## 1. Today's Highlights

No new releases landed in the last 24 hours, but community momentum remains intense around Windows Desktop stability, Computer Use reliability, and CLI configuration flexibility. A wave of 20+ closed PRs shipped today focused on plugin metrics collection, thread usage reporting, gRPC code-mode host support, and unified turn submission — signaling active investment in observability and executor infrastructure.

## 2. Releases

None in the last 24 hours.

## 3. Hot Issues

1. **[Bug] macOS `syspolicyd`/`trustd` CPU & memory runaway** (#25719) — 392 👍, 83 comments
   Codex Desktop on macOS repeatedly triggers system policy daemons, causing sustained CPU/memory spikes. This is the single most-upvoted open issue and affects a broad user base; it remains unresolved since June.
   https://github.com/openai/codex/issues/25719

2. **[Bug] Disable auto-resolve for `request_user_input` in 60 s** (#28969) — 194 👍, 70 comments
   Users want a configurable timeout (or indefinite wait) for `request_user_input` in Default mode. Strong demand from developers running long-running tasks who lose context when the question auto-resolves.
   https://github.com/openai/codex/issues/28969

3. **[Bug] Rate-limit reset wasted and not applied** (#31606) — 65 👍, 56 comments
   A Pro user reports a reset was consumed without being applied, dropping their counter from 2 to 1 with no functional effect. Highlights friction around subscription management and reset accounting.
   https://github.com/openai/codex/issues/31606

4. **[Bug] Windows unbounded `taskkill.exe`/`conhost.exe` cleanup storm exhausts WMI** (#34260) — 11 👍, 34 comments
   Hundreds of orphaned `taskkill` processes accumulate, repeatedly querying `Win32_Process` and exhausting the WMI provider quota, effectively freezing the machine. A severe Windows-specific regression.
   https://github.com/openai/codex/issues/34260

5. **[Bug] Windows `powershell.exe` spawned every second for process polling** (#25453) — 7 👍, 25 comments
   Continuous per-second spawning of short-lived PowerShell processes causes high CPU on Windows. Created in May; still open with growing frustration.
   https://github.com/openai/codex/issues/25453

6. **[Bug] Computer Use screenshot fails on Windows 10 22H2** (#25178) — 13 👍, 25 comments
   `get_window_state` calls with screenshot requests fail with `SetIsBorderRequired failed: 不支持此接口 (0x80004002)` on older Windows builds. Blocks Computer Use for a segment of Windows users.
   https://github.com/openai/codex/issues/25178

7. **[Bug] Windows Computer Use cannot enumerate or launch desktop apps** (#37932) — 3 👍, 3 comments
   New report (Aug 11): Computer Use plugin cannot see or control any desktop apps on a specific Windows machine, suggesting a possible regression in the latest build.
   https://github.com/openai/codex/issues/37932

8. **[Bug] Windows Computer Use returns EPERM after permission granted** (#38293) — 2 👍, 2 comments
   Another fresh Windows Computer Use issue (Aug 13): `sky.list_windows()` fails immediately with EPERM even after the user grants permission. Part of a cluster of Windows desktop-plugin issues.
   https://github.com/openai/codex/issues/38293

9. **[Bug] Auto-compaction uses stale token usage causing unrecoverable context overflow** (#32888) — 3 👍, 3 comments
   In long-running app-server turns, a large tool result can push context past the model limit before auto-compaction triggers, because compaction reads the last server-reported token count, not the newly appended tool output. A correctness bug with serious implications for extended sessions.
   https://github.com/openai/codex/issues/32888

10. **[Bug] Windows Desktop local state not crash-safe after power loss** (#26990) — 0 👍, 14 comments
    Pins, projects, and config can regress to stale states after unexpected power loss. Raises concerns about data integrity on Windows for always-on remote-host setups.
    https://github.com/openai/codex/issues/26990

## 4. Key PR Progress

1. **#38292 — Durable reverts for paginated threads** [CLOSED]
   Adds `ThreadStore::revert_thread` to create an immutable rollout snapshot before a selected turn, preserving logical thread ID and session metadata across repeated reverts. Enables safe thread rollback in the app.
   https://github.com/openai/codex/pull/38292

2. **#38288 — gRPC code-mode hosts in app server** [CLOSED]
   App server now accepts `http://` and `https://` URLs in `--code-mode-host`, routing them through a shared gRPC session provider, while `ws://`/`wss://` remain on the WebSocket transport. Expands deployment flexibility for remote executors.
   https://github.com/openai/codex/pull/38288

3. **#38283 — Plugin metrics from remote executors** [CLOSED]
   Resolves manifest-declared metric operations against the executor filesystem for remote plugin commands and creates the measurement sidecar in an executor-native temp directory. Critical for observability in distributed setups.
   https://github.com/openai/codex/pull/38283

4. **#38282 — Thread usage in TUI status surfaces** [CLOSED]
   Adds `thread-credits` and `estimated-thread-cost` to the configurable status line and terminal title for Enterprise workspaces, fetching a single shared estimate only when selected.
   https://github.com/openai/codex/pull/38282

5. **#38281 — Estimated thread usage in `/status`** [CLOSED]
   Extends `account/usage/read` with an optional `threadId` request and a backward-compatible `threadUsage` response containing estimated credits, USD cost, model, reasoning, speed, and token breakdowns.
   https://github.com/openai/codex/pull/38281

6. **#38275 — Unify turn input submission and routing** [CLOSED]
   Introduces `TurnInputRequest` and typed results for atomically starting, steering, or declining a turn. Exposes `start_or_steer_turn`, `start_turn_if_idle`, and `steer_turn` on `CodexThread`, reducing race conditions in concurrent workflows.
   https://github.com/openai/codex/pull/38275

7. **#38272 — Stamp conversation history items with creation times** [CLOSED]
   Adds fractional Unix creation times to all durable conversation items (user, developer, agent, tool-output), enabling deterministic ordering and replay across subsequent requests.
   https://github.com/openai/codex/pull/38272

8. **#38274 — Represent persisted world state as JSON objects** [CLOSED]
   Types the `state` field of world-state snapshots and merge patches as JSON objects, preventing replay code from encountering shapes that cannot represent valid world state.
   https://github.com/openai/codex/pull/38274

9. **#38265 — Bounded fallback ports for Windows managed proxies** [CLOSED]
   Windows managed proxies now try the explicitly configured port first, then scan the protocol's preferred port range. HTTP and SOCKS5 listeners are reserved independently to avoid cross-protocol collisions.
   https://github.com/openai/codex/pull/38265

10. **#38258 — Unify external authentication provider handling** [CLOSED]
    Uses each `ExternalAuth` provider's error classification for resolve, refresh, and validation failures, and allows runtime providers to be replaced, clearing permanent refresh failure state after a successful replacement.
    https://github.com/openai/codex/pull/38258

## 5. Feature Request Trends

- **Configurable input timeouts**: Multiple issues (#28969, #37472) request the ability to disable or extend the 60-second auto-resolve for `request_user_input`, including indefinite waits in Default mode.
- **Thread usage & cost observability**: Users consistently ask for per-thread credit/cost tracking (now partially addressed by PRs #38281 and #38282), reflecting demand for finer-grained billing transparency.
- **Credential and auth hardening**: Interest in the experimental credential broker (#29752) and unified external auth handling (#38258) signals a need for better credential management in managed/remote execution environments.
- **Plugin and tool extensibility**: Requests for MCP tool compatibility (#33263), file-upload support in Browser Use (#20785), and broader skill-root exposure (#38268) show users pushing the boundaries of what Codex can orchestrate.
- **Audible alerts for pending approvals** (#11604): A smaller but persistent request for CLI permission-approval sound cues, similar to Copilot CLI.

## 6. Developer Pain Points

- **Windows Desktop instability dominates complaints**: At least five open issues (#34260, #25453, #25178, #37932, #38293) report severe Windows-specific bugs — process-leak storms, WMI exhaustion, Computer Use plugin failures, and permission errors. Windows users are experiencing a degraded experience compared to macOS.
- **macOS system daemon resource exhaustion** (#25719): The most upvoted issue on the board, indicating that even the primary platform has a persistent, high-impact performance bug affecting `syspolicyd`/`trustd`.
- **Context management correctness**: Auto-compaction relying on stale token counts (#32888) and thread resume dropping turns on compacted threads (#38169) both point to fragile state tracking in long-running sessions — a recurring theme for power users.
- **App state durability**: Crash-unsafe local state on Windows (#26990), stale subagent locks causing blank screens (#38250), and SQLite backfill hangs (#28087) suggest the Desktop app's persistence layer needs hardening across platforms.
- **Rate-limit and subscription accounting** (#31606): Wasted resets and misapplied counters erode trust; users want reliable, auditable subscription mechanics.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-13

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly shipped with strengthened eval infrastructure, including a new tool call formatter and integrated failure summaries. The team also pushed critical security hardening around MCP config corruption handling and variable expansion bypasses, while community discussion intensifies around subagent reliability and the Antigravity CLI transition.

---

## 2. Releases

**v0.56.0-nightly.20260813.g1ac337739** — [PR #28795](https://github.com/google-gemini/gemini-cli/pull/28795)

- Eval validation improvements: tool call formatter and failure summary integration ([#28344](https://github.com/google-gemini/gemini-cli/pull/28344), [#28305](https://github.com/google-gemini/gemini-cli/pull/28305))
- Changelog for v0.55.1 [PR #28779](https://github.com/google-gemini/gemini-cli/pull/28779)
- Changelog for v0.56.0-preview.1 [PR #28776](https://github.com/google-gemini/gemini-cli/pull/28776)

---

## 3. Hot Issues

1. **[Stuck at thinking](https://github.com/google-gemini/gemini-cli/issues/26126)** — 18 comments · 11 👍 · 🔴 P1
   Intermittent hangs in the "Thinking" state with no output or timeout. High-rep bug affecting core UX. **Closed** (stale).

2. **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — 12 comments · 2 👍 · 🔴 P1
   `codebase_investigator` subagent returns `GOAL` status after hitting max turns, silently masking interruption. Under retesting.

3. **[Robust component-level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** — 7 comments · 🔴 P1
   Epic tracking behavioral evals (76 tests generated across 6 Gemini models). Core to the eval infrastructure push.

4. **[AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — 7 comments · 1 👍 · 🔴 P2
   Investigation into whether AST-aware tools reduce turns and token noise by reading precise method bounds in single calls.

5. **[CLI crashes with `ioctl(2) EBADF` in `node-pty`](https://github.com/google-gemini/gemini-cli/issues/27533)** — 7 comments · 🔴 P1
   Terminal resize crashes during SSH sessions on Linux. Points to a recurring `node-pty` instability pattern. **Closed** (stale).

6. **[Non-English characters in CLI output](https://github.com/google-gemini/gemini-cli/issues/27312)** — 6 comments · 1 👍 · 🔴 P2
   Random Chinese characters leaking into model responses despite non-Chinese default language settings. **Closed** (stale).

7. **[Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** — 6 comments · 🔴 P2
   Users report custom skills (e.g., "gradle", "git") are ignored unless explicitly prompted. A significant workflow friction point.

8. **[EBADF during folder creation breaks session](https://github.com/google-gemini/gemini-cli/issues/27541)** — 5 comments · 🔴 P2
   Terminal glitch during `mkdir` causes session crash — same `node-pty` `EBADF` root cause as #27533. **Closed** (stale/duplicate).

9. **[CLI crashes on startup with special characters in `GEMINI_API_KEY`](https://github.com/google-gemini/gemini-cli/issues/28575)** — 5 comments · 🔴 P2
   Keys containing `=` or `+` trigger a `ParseError: invalid key format`. Simple reproducible auth bug. **Closed**.

10. **[Antigravity CLI seen as a downgrade](https://github.com/google-gemini/gemini-cli/issues/27858)** — 4 comments · 13 👍 · 🔴 P2
    Community strongly flags the Antigravity unification as sacrificing lightweight CLI performance for broader agent patterns. High upvote count signals broad dissatisfaction.

---

## 4. Key PR Progress

1. **[Prevent fail-open on corrupt MCP config](https://github.com/google-gemini/gemini-cli/pull/28794)** — 🔴 P1 · size/m
   Fixes vulnerability where a corrupted `mcp-server-enablement.json` silently re-enabled all servers. Closes [#28786](https://github.com/google-gemini/gemini-cli/issues/28786).

2. **[Block `$VAR` / `${VAR}` expansion bypass](https://github.com/google-gemini/gemini-cli/pull/28691)** — 🔴 P1 · size/l · Security
   Closes GHSA-wpqr-6v78-jr5g: hardens `detectBashSubstitution()` and `detectPowerShellSubstitution()` against bypass patterns. Defense-in-depth for the automation workflow.

3. **[Context-aware silent retries for capacity errors](https://github.com/google-gemini/gemini-cli/pull/28790)** — 🔴 P1 · size/l
   Resolves the capacity-exhaustion retry regression [#28761](https://github.com/google-gemini/gemini-cli/issues/28761): unattended CLI runs now back off and retry automatically with up to 2 silent retries.

4. **[Fix `thoughtSignature` stripping causing 400 errors](https://github.com/google-gemini/gemini-cli/pull/28586)** — 🔴 P2 · size/m
   Fixes a v0.53.0 regression where `thoughtSignature` was dropped from functionCall parts, breaking parallel tool calls.

5. **[Skip diff hunk markers during `@` processing](https://github.com/google-gemini/gemini-cli/pull/28581)** — 🔴 P2 · size/m
   Prevents unified/combined diff hunk markers from being interpreted as `@file` references, eliminating recursive glob searches and `minimatch` heap growth on large diffs.

6. **[Behavioral evals for skills fetch](https://github.com/google-gemini/gemini-cli/pull/28788)** — size/l
   Adds evals for `activate_skill` and `web_fetch`, plus Windows compatibility fixes for the local eval environment and bug fixes in the EDK report aggregator.

7. **[VSCode companion: fix `stop()` hang and keep-alive leak](https://github.com/google-gemini/gemini-cli/pull/28789)** — size/m
   Resolves two stability bugs: `IdeServer.stop()` hanging on active streaming MCP sessions, and a resource leak in the keep-alive ping loop.

8. **[A2A server: enforce authentication & stop checkpoint path traversal](https://github.com/google-gemini/gemini-cli/pull/28699)** — size/l
   Custom REST routes were bypassing the `UserBuilder` entirely, accepting unauthenticated requests. Now enforces auth and closes the traversal vector.

9. **[Improve Vertex AI 401 error message](https://github.com/google-gemini/gemini-cli/pull/28679)** — 🔴 P2 · size/s · Security
   Better developer experience when a standard Gemini API key is used with the `vertex-ai` auth type instead of failing with a cryptic 401.

10. **[Fix TRUST_PARENT rule precedence in folder-trust resolution](https://github.com/google-gemini/gemini-cli/pull/28701)** — size/s
    Corrects behavior where `isPathTrusted()` was not properly applying "longest match wins" for trust rule selection.

---

## 5. Feature Request Trends

- **Smarter sub-agent and skill invocation** — Users consistently want Gemini CLI to autonomously detect when to use custom skills and sub-agents without explicit prompting (#21968).
- **AST-aware codebase tools** — Interest in AST-aware file reads and searches to reduce turns and token waste by targeting precise code boundaries (#22745).
- **Evaluation infrastructure investment** — Ongoing push for component-level behavioral evals and robust test coverage across all supported Gemini models (#24353, #28788).
- **Resilient browser agent** — Requests for automatic session takeover, lock recovery, and better Wayland support (#22232, #21983).
- **Lightweight CLI experience** — Strong community desire to preserve the surgical efficiency of Gemini CLI versus the token-heavy Antigravity variant (#27858, #27567).

---

## 6. Developer Pain Points

| Pain Point | Occurrence |
|---|---|
| **Subagents and skills not auto-invoked** | Users report Gemini ignores configured skills unless explicitly told to use them |
| **Terminal/PTY crashes (`EBADF`)** | Recurring `node-pty` failures during resize or command execution, especially over SSH on Linux |
| **Shell commands hanging after completion** | `Waiting input` state persists after non-interactive commands finish (#25166) |
| **Antigravity migration regressions** | Higher token consumption and loss of lightweight CLI behavior frustrates power users and VPS operators |
| **MCP config corruption vulnerabilities** | Corrupted configs could silently re-enable all servers — a security and data-loss risk |
| **Browser agent instability** | Fails on Wayland, ignores `settings.json` overrides, and lacks resilient session recovery |
| **Secrets in `GEMINI_API_KEY`** | Special characters (`=`, `+`) in keys cause startup crashes, blocking users with complex credentials |

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-13

## 1. Today's Highlights

A wave of new issues landed on 2026-08-12, concentrated around remote MCP OAuth failures, session resource leaks, and Docker container cleanup — signaling ongoing growing pains as the CLI scales its multi-session and MCP-heavy workflows. Meanwhile, two longstanding bugs (silenced subagent model overrides and CI-time MCP registry auth) were closed, while the community's top-voted open issue (#1305, 35 👍) remains a feature request for CIMD-style OAuth registration on remote MCP servers.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Status | 👍 | Comments | Why it matters |
|---|-------|--------|----|----------|----------------|
| [#1305](https://github.com/github/copilot-cli/issues/1305) | Support CIMD for Remote OAuth MCP Servers | OPEN | 35 | 5 | The highest-voted open issue by far. DCR-based "just-in-time" OAuth registration would remove the pre-registration barrier for enterprise remote MCP servers. |
| [#4390](https://github.com/github/copilot-cli/issues/4390) | Enabled org models missing from catalogue (Claude Sonnet 5/Opus 5/Kimi K3) | OPEN | 4 | 5 | Business-critical: Anthropic models disabled at the org level are entirely absent from the CLI catalogue, making them unreachable even when explicitly enabled. |
| [#2109](https://github.com/github/copilot-cli/issues/2109) | ACP: `ask_user` / `ask_question` extension method | OPEN | 7 | 3 | Extensibility gap — custom ACP clients can surface clarifying questions but currently lack a structured return path; only `session/request_permission` is supported. |
| [#1730](https://github.com/github/copilot-cli/issues/1730) | `sessionStart` hook in `.github/hooks/` does not fire (v0.0.420) | OPEN | 3 | 8 | Plugin authors report hooks in `.github/hooks/*.json` silently skipped at session start on Windows/PowerShell; breaks automation expectations. |
| [#4328](https://github.com/github/copilot-cli/issues/4328) | Ctrl+H misinterpreted as Ctrl+Backspace under WSL2 | OPEN | 0 | 6 | WT_SESSION leaking from Windows Terminal causes `ctrl+h` (backspace char) to behave like `ctrl+w` (backspace word) — a regression in WSL2 UX. |
| [#3976](https://github.com/github/copilot-cli/issues/3976) | Native `tgrep` indexer OOM-kills host on large monorepos | OPEN | 0 | 2 | No memory cap on the persistent `tgrep serve` daemon; large repos cause unbounded growth and host OOM — a scalability concern for enterprise monorepos. |
| [#4432](https://github.com/github/copilot-cli/issues/4432) | `rubber-duck` model argument silently overrides complementary strategy | OPEN | 0 | 2 | The `task` tool exposes a `model` arg that overrides the `complementary` subagent strategy, defeating the cross-family review design. |
| [#3565](https://github.com/github/copilot-cli/issues/3565) | Task tool silently downgrades subagent model to session model | CLOSED | 1 | 1 | **Closed.** Multiplier guard was forcing subagent model down to the parent session model, ignoring frontmatter and explicit `model` overrides. |
| [#4346](https://github.com/github/copilot-cli/issues/4346) | MCP registry policy fetch returns 403 for Actions `GITHUB_TOKEN` | CLOSED | 3 | 1 | **Closed.** PAT-less GitHub Actions setup could not fetch MCP registry policy, blocking all non-default MCP servers in CI workflows. |
| [#4358](https://github.com/github/copilot-cli/issues/4358) | BYOK: populate `/model` picker from provider's `/models` endpoint | OPEN | 2 | 1 | Custom providers (`COPILOT_PROVIDER_BASE_URL`) expose only a single model in-session; users must quit and reconfigure to switch models. |

## 4. Key PR Progress

| # | Title | Status | Author | Summary |
|---|-------|--------|--------|---------|
| [#4449](https://github.com/github/copilot-cli/pull/4449) | Migrate PR automation away from `pull_request_target` | OPEN | @mrecachinas | Replaces `pull_request_target` with a no-permission `pull_request` signal for prompt handling and uses an issue-scoped write token for direct issue closure, reducing attack surface. |
| [#4453](https://github.com/github/copilot-cli/pull/4453) | Julesdemangeot ship it patch 1 | CLOSED | @julesdemangeot-ship-it | Closed; details not yet published. |

> Only 2 PRs updated in the last 24 hours; the repository appears to be in a quiet merge window.

## 5. Feature Request Trends

- **MCP OAuth maturation** — Three distinct issues (#1305, #4464, #4463) target remote MCP auth: CIMD/DCR registration, silent refresh failures with AADSTS70011, and Windows socket errors. The community clearly wants smoother, token-rotation-friendly OAuth for remote MCP servers.
- **BYOK / custom provider discoverability** — #4358 and #4390 both flag that model visibility is broken for custom and org-scoped providers. Users want `/models` and the session picker to reflect what the provider actually offers.
- **Subagent model fidelity** — #4432, #3565 (closed), and #4458/#4462 (code-review override ignored) converge on a single theme: explicit per-agent model configurations are being silently overridden or downgraded by the session host.
- **Session lifecycle hygiene** — #4468 (orphaned extension-host processes), #4460/#4461 (Docker containers not cleaned up), and #4467 (event-store exhaustion on long sessions) point to a need for robust resource cleanup in long-running or multi-session environments.

## 6. Developer Pain Points

1. **Silent config overrides** — The most frequent frustration this cycle. Explicit `model:` settings in agent frontmatter, complementary strategies, and subagent definitions are being ignored or downgraded without warning (#3565, #4432, #4458/#4462).
2. **Remote MCP auth fragility** — OAuth for remote MCP servers is error-prone on multiple fronts: silent refresh loops (#4464), socket-access errors on Windows (#4463), and hard-fail on transient 5xx during `initialize` (#4466). Any transient network blip kills the server for the entire session.
3. **Resource leaks in long sessions** — Extension-host child processes (#4468), Docker containers (#4460/#4461), and event-store exhaustion (#4467) all accumulate when sessions are resumed repeatedly, degrading system stability over time.
4. **WSL2 / Windows Terminal edge cases** — Control-key remapping regressions (#4328) and hook non-firing on Windows/PowerShell (#1730) suggest the CLI's terminal-interaction layer needs tighter WSL2 validation.
5. **Organizational model visibility** — Business customers expect org-enabled models to appear in the CLI catalogue; their absence (#4390) breaks onboarding for Copilot Business/Enterprise teams.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-13

## 1. Today's Highlights

No new releases were published in the last 24 hours. The community's attention is focused on two open PRs addressing string formatting and subprocess error handling, both authored by Ricardo-M-L, while the long-standing feature request for a persistent Memory System (#1283) continues to accumulate discussion.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

**#1283 — Memory System: Persistent context across sessions** (Open · 36 comments · Author: CatKang)
This is the most-discussed open issue, requesting a comprehensive memory layer so Kimi Code CLI can retain project patterns, context, and user preferences between invocations. Its longevity (open since Feb 2026) and sustained comment volume signal strong community demand.
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)

## 4. Key PR Progress

**#2449 — fix(string): strip newlines in shorten_middle before the length check** (Open · Author: Ricardo-M-L)
Fixes a bug where `shorten_middle()` returns early on short input before collapsing newlines, causing multi-line output in tool-call summaries that are expected to be single-line. A targeted but meaningful correctness fix.
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/pull/2449)

**#2324 — fix(web): handle BrokenPipeError in SessionProcess.send_message** (Open · Author: Ricardo-M-L)
Addresses a race condition in `SessionProcess.send_message` where writing to `process.stdin` can raise `BrokenPipeError` if the subprocess exits between `start()` and the actual write. Guards the drain operation against this scenario.
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/pull/2324)

## 5. Feature Request Trends

The dominant trend is **statefulness and persistence**: the Memory System request (#1283) is the only open issue in the window and clearly represents the community's top wish — the ability to carry context across sessions without re-provisioning. No other feature requests appeared in the last 24 hours, suggesting the backlog may be quiet or that existing open issues continue to absorb community attention.

## 6. Developer Pain Points

- **Context loss between sessions**: Developers repeatedly want the CLI to "remember" project specifics, reducing the need to re-prompt on every invocation (#1283).
- **String formatting edge cases**: The `shorten_middle` PR (#2449) highlights that newline handling in tool-call argument rendering can produce malformed single-line output — a bug that likely affects developer readability in terminal UIs.
- **Subprocess reliability**: The `BrokenPipeError` fix (#2324) points to ongoing fragility in the web session runner when child processes terminate unexpectedly, a pain point for users running long-lived or interactive sessions.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-13

## 1. Today's Highlights

OpenCode released **v1.18.18** and **v1.18.17**, bringing Kimi system prompt fixes, improved session compaction for smaller models, and capped automatic retries with jitter to reduce spam. Community attention is dominated by Gemini 3 Pro function-calling failures, Azure OpenAI streaming hangs, and a persistent billing/subscription confusion thread.

---

## 2. Releases

**v1.18.18** — Core bugfixes: correctly selects the Kimi system prompt for official Moonshot/Kimi providers; fixes `xhigh` reasoning effort routing for xAI models.

**v1.18.17** — Session compaction now preserves complete recent turns and produces clearer summaries for smaller models; adds MERGE Gateway reasoning variants; caps automatic session retries and adds jitter to prevent repeated retry storms.

---

## 3. Hot Issues

| Issue | Summary | Why It Matters | Community |
|-------|---------|----------------|-----------|
| [#4832](https://github.com/anomalyco/opencode/issues/4832) | Gemini 3 Pro function calling fails — missing `thoughtSignature` support | Blocks a widely-used model from reliable tool use; 35 comments show sustained frustration | 35 comments · 14 👍 |
| [#41470](https://github.com/anomalyco/opencode/issues/41470) | "Copied to clipboard" doesn't work in VSCode Server / Docker | Clipboard integration is core UX; fails silently in remote environments | 11 comments |
| [#3366](https://github.com/anomalyco/opencode/issues/3366) | Mermaid rendering in chat | High-demand visual feature; 26 👍 makes it the most-liked open feature request | 10 comments · 26 👍 |
| [#6815](https://github.com/anomalyco/opencode/issues/6815) | Command palette action to reload config without restart | Configuration reload requires manual exit/restart — painful for iterative workflows | 8 comments · 88 👍 |
| [#33027](https://github.com/anomalyco/opencode/issues/33027) | MCP tools connected but not exposed to agent | MCP adoption is growing; tools visible via `tools/list` but invisible to the agent is a breaking integration gap | 7 comments · 3 👍 |
| [#42147](https://github.com/anomalyco/opencode/issues/42147) | Azure OpenAI large models (gpt-5.6/5.4, o3) hang in streaming | Enterprise Azure users cannot use large reasoning models; small models work fine — points to a streaming/payload issue | 4 comments |
| [#42135](https://github.com/anomalyco/opencode/issues/42135) | DeepSeek v4 Pro fails on multi-turn via `/responses` API | ACP + DeepSeek combo breaks after first turn; flash and official API both work — narrows the bug | 2 comments |
| [#42216](https://github.com/anomalyco/opencode/issues/42216) | Cyclic symlinks in global skills cause blank TUI & unbounded memory growth | A single misconfigured symlink can crash the entire TUI and consume 7+ GB — critical stability issue | 2 comments |
| [#42170](https://github.com/anomalyco/opencode/issues/42170) | Desktop fails to load sessions: `no such column: project_id` | Schema migration leaves SQLite broken on launch; blocks access to all sessions | 2 comments |
| [#17073](https://github.com/anomalyco/opencode/issues/17073) | Protect .env files in grep/glob results, not just direct read | Security-sensitive; current permission rules match on search pattern, not matched file paths, allowing .env leaks | 6 comments · 5 👍 |

---

## 4. Key PR Progress

| PR | Summary | Type |
|----|---------|------|
| [#42223](https://github.com/anomalyco/opencode/pull/42223) | Fixes `opencode -c` showing wrong working directory when resuming in a new directory; SDK `pick()` now falls back to `config.directory` | Bug fix |
| [#42219](https://github.com/anomalyco/opencode/pull/42219) | Adds hover highlight to the queued-prompts dock, making its interactive behavior discoverable | UX polish |
| [#42214](https://github.com/anomalyco/opencode/pull/42214) | Highlights shell tool commands with Bash syntax coloring in the TUI (inline and expanded blocks) | Feature |
| [#42020](https://github.com/anomalyco/opencode/pull/42020) | Retries local MCP server connections on transient spawn failures, improving parallel server startup reliability | Bug fix |
| [#39473](https://github.com/anomalyco/opencode/pull/39473) | Retries truncated provider streams instead of synthesizing a spurious `other` finish reason | Bug fix |
| [#42218](https://github.com/anomalyco/opencode/pull/42218) | Refreshes the ripgrep fallback file index on filesystem changes without requiring a daemon restart | Bug fix |
| [#42222](https://github.com/anomalyco/opencode/pull/42222) | Replaces `xdg-basedir` with a local implementation, removing one direct runtime dependency (~6.8 KB) | Refactor |
| [#42158](https://github.com/anomalyco/opencode/pull/42158) | Bridges the `question` tool to ACP elicitation, fixing indefinite blocking when `QuestionV2` request IDs weren't passed to `reply/reject` | Bug fix |
| [#42209](https://github.com/anomalyco/opencode/pull/42209) | Cancels native SSE fetch readers after handshake, reducing memory growth on reconnect/cancel | Bug fix |
| [#42186](https://github.com/anomalyco/opencode/pull/42186) | Requires authenticated service stop before a client can replace a managed service, preventing stale/rejected stop flows | Bug fix |

---

## 5. Feature Request Trends

- **Config hot-reload** — Users want to apply configuration changes without restarting; issue #6815 has 88 👍, signaling strong demand.
- **Mermaid / visual diagram rendering** — Issue #3366 (26 👍) shows sustained interest in rich in-chat visualization.
- **Voice input** — Issue #41364 requests mic-to-text prompt input and optional voice summaries for desktop/mobile workflows.
- **Per-MCP-server trust configuration** — Issue #40111 asks for TLS certificate override controls for private-network MCP servers (firewalls, NAS, K8s, Home Assistant).
- **Custom model aliases** — Issue #30519 requests the ability to reference official Models.dev definitions from custom providers by ID.
- **Shell tool command highlighting** — Being implemented in PR #42214, reflecting community interest in richer TUI feedback.

---

## 6. Developer Pain Points

- **Streaming & provider compatibility** — Azure OpenAI large models hang (#42147), DeepSeek v4 Pro multi-turn fails (#42135), and Gemini 3 Pro function calling breaks (#4832). Multiple providers are surfacing edge-case bugs in the streaming layer.
- **Subscription / billing confusion** — Several users report being told "Free usage exceeded, subscribe to Go" despite having an active subscription (#42043, #42132, #42140, #42154, #42114). This is a high-frequency support friction point.
- **Desktop stability** — Cyclic symlinks crashing the TUI with unbounded memory growth (#42216) and a broken SQLite migration (`no such column: project_id`) on launch (#42170) are critical quality gaps.
- **Clipboard in remote environments** — The clipboard "Copied to clipboard" message lies when running inside VSCode Server / Docker (#41470), breaking a basic workflow.
- **MCP tool visibility** — Tools connecting successfully but remaining invisible to the agent (#33027) indicate a gap in the MCP tool discovery pipeline.
- **Session resumption UX** — `opencode -c` picking up the wrong working directory (#42221) and the missing hot-reload for config (#6815) both reflect friction in the daily session management loop.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-13

## 1. Today's Highlights

The most-watched issue remains the auto-compaction bug (#6879), where context can grow past 100% without triggering compaction until the API rejects the request — a critical reliability gap for long agentic sessions. On the PR side, session persistence was made transactional, usage data is now preserved in streaming events, and the TUI now supports component-level mouse event dispatching.

---

## 2. Releases

No new releases published in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Comments | 👍 | Why It Matters |
|---|-------|--------|----------|-----|----------------|
| #6879 | auto-compaction never triggers after context grows past 100% | OPEN / bug | 18 | 17 | Long agentic turns can exhaust the context window before compaction runs, causing API rejections at 373k tokens. Directly impacts session reliability. |
| #7730 | High CPU usage on Mac OS with long sessions | OPEN / bug | 11 | 8 | CPU swings 50–110% during extended sessions; correlates with context length. Affects developer experience on macOS. |
| #7836 | Edit fuzzy match misses lines with whitespace differences | OPEN / inprogress | 10 | 1 | `normalizeForFuzzyMatch` doesn't collapse whitespace runs, causing edit tool failures when indentation differs. Impacts small-model edit accuracy. |
| #7683 | TUI: components receive mouse events on their own rows | CLOSED | 9 | 0 | Proposed `Component.onMouse` hook; now implemented via PR #8037. Enables rich interactive widgets in fullscreen TUI. |
| #7585 | Kitty graphics don't render inside `ctx.ui.custom()` on Ghostty | CLOSED | 5 | 0 | Images rendered through custom UI components appear blank on Ghostty despite Kitty support being detected. |
| #8055 | Ambiguous-width chars break table alignment on CJK terminals | CLOSED | 3 | 0 | Characters like `①` and `€` counted as 1 column but render as 2 in CJK fonts, misaligning TUI tables. |
| #8000 | `@` autocomplete: deep matches beat direct children on basename ties | OPEN | 3 | 0 | Typing `@~/<dir>/pro` ranks nested matches above the likely-intended direct child. Degrades file-picker UX. |
| #7783 | `agent_end` sendMessage with `triggerTurn:false` still starts a turn | CLOSED | 3 | 0 | Custom display messages from extension handlers consumed an unintended second assistant turn. Now fixed. |
| #7911 | 0.84.0 removed `usage` from streaming `message_update` events | CLOSED | 2 | 0 | Wire protocol no longer carries token usage until `message_end`, breaking real-time cost tracking. Now fixed via PR #7982. |
| #7805 | Root `.md` files in skill directories loaded as skills | OPEN / inprogress | 2 | 0 | `README.md`, `AGENTS.md`, etc. at skill-dir roots are parsed as skills and produce validation warnings. Fix in PR #8012. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| #8052 | fix(coding-agent): make session persistence transactional | CLOSED | `SessionManager._appendEntry()` now waits for JSONL write to complete before advancing the in-memory graph, preventing broken sessions after `ENOSPC` or similar failures. |
| #7982 | fix(coding-agent): preserve usage in streaming events | CLOSED | Cumulative provider usage is restored on JSON and RPC `message_update` events; closes #7911. |
| #8049 | feat: use local Ollama models via local proxy | CLOSED | Two dependency-free Node.js scripts (`ollama-proxy.mjs`) expose local Ollama models as a Pi-compatible endpoint. Works on Ubuntu, macOS, and Windows. |
| #8042 | feat(ai): add Grok 4.6 | CLOSED | Registers Grok 4.6 in the xAI Responses model set with `low`/`medium`/`high`/`xhigh` reasoning levels. |
| #7956 | feat(coding-agent): render Mermaid diagrams in HTML exports | CLOSED | HTML exports now render Mermaid graphs (and LaTex) the same way the TUI does, via ANSI-to-HTML translation. |
| #8037 | feat(tui): dispatch mouse events to components | CLOSED | Implements `Component.onMouse` hook; `TuiAltScreen` now hit-tests the `LayoutBox` tree and offers events innermost-first. |
| #8032 | feat(tui): let components receive mouse events (duplicate proposal) | OPEN | Alternative/cross-ref to #8037; same `Component.onMouse` implementation. |
| #7722 | feat(coding-agent): add theme override | CLOSED | New `--use-theme` flag supports single themes (`dark`) and appearance pairs (`dayowl/nightowl`). |
| #8022 | fix: triggerTurn: false should not start turn | CLOSED | Fixes #7783 — `sendCustomMessage()` no longer routes display-only messages through the streaming `agent.steer()` path when `triggerTurn: false`. |
| #8012 | fix: don't load root `.md` files as skills | CLOSED | `README.md`, `AGENTS.md`, and similar root-level docs in skill directories are now skipped unless they contain valid skill frontmatter. Addresses #7805. |

---

## 5. Feature Request Trends

- **Local model integration** — Strong recurring demand: Ollama proxy (#8049), Scaleway Generative APIs (#6165), local model listing (#8051), and the `add-local-model` slash command extension (#8039) all point to a community push for first-class local/edge model support.
- **TUI interactivity** — Mouse event dispatch (#7683/#8037), configurable scroll step (#7765), and theme override (#7722) show sustained interest in richer, more configurable terminal UIs.
- **Observability & debugging** — Durable custom-message publication (#8023), extension hooks to control displayed assistant messages (#8035), and restored streaming usage (#7982) reflect a need for better observability into agent execution.
- **Multi-format export** — Mermaid/LaTex rendering in HTML exports (#7956/#8041) indicates demand for feature parity between TUI and export views.

---

## 6. Developer Pain Points

1. **Context management fragility** — The auto-compaction bug (#6879) is the top concern: compaction fails to trigger during long agentic turns, leading to API rejections. This is the highest-engagement issue and directly impacts production session reliability.
2. **macOS performance** — High CPU usage on long sessions (#7730) is a persistent pain point, especially as context windows grow.
3. **Terminal rendering inconsistencies** — Multiple closed issues (#7585 Kitty graphics, #8055 ambiguous-width chars) show that TUI rendering remains fragile across terminal emulators (Ghostty, CJK terminals).
4. **Autocomplete ranking** — File `@` autocomplete (#8000) buries direct children under nested matches, degrading a高频 interaction pattern.
5. **Whitespace-sensitive edits** — The fuzzy match bug (#7836) causes edit tool failures when indentation differs from the source text, a common scenario with reformatted code.
6. **Silent protocol regressions** — The 0.84.0 change that dropped `usage` from streaming events (#7911) shows how wire-protocol changes can silently break downstream consumers; the community is now more vocal about requiring protocol stability guarantees.

---

*Data sourced from [github.com/badlogic/pi-mono](https://github.com/badlogic/pi-mono) · Generated 2026-08-13*

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-13

## 1. Today's Highlights

Qwen Code Desktop shipped v0.2.1 with workspace-scoped memory and telemetry lifecycle alignment, while the core team pushed forward on background workflow visualization, web-shell file uploads, and durable replay journals. Community attention is concentrated on three fronts: reliable auto-memory recall (RFC #7040), long-running task failures in CLI mode (#8963), and a regression causing image-load crashes since v0.21.2 (#8957).

---

## 2. Releases

**desktop-v0.2.1** ([PR #8856](https://github.com/QwenLM/qwen-code/pull/8856))
- Defaults project memory to workspace scope
- Aligns telemetry session lifecycle

**desktop-v0.2.0** ([PR #8914](https://github.com/QwenLM/qwen-code/pull/8914))
- Stabilizes web-shell transcript history pagination
- Adds session catalog sharing for web-shell

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#7040](https://github.com/QwenLM/qwen-code/issues/7040) | RFC: Reliable auto-memory recall | Core roadmap item tracking telemetry, bounded recall, and precision evaluation; two PRs already in review. |
| [#8963](https://github.com/QwenLM/qwen-code/issues/8963) | Cannot auto-run long tasks | Users report tasks hanging in both `yolo` and `auto` modes; direct comparison to Kimi Code highlights urgency. |
| [#8957](https://github.com/QwenLM/qwen-code/issues/8957) | Crash on image load since v0.21.2 | Regression — `qwen` instantly crashes when reading images; no working version since 0.21.1. |
| [#8678](https://github.com/QwenLM/qwen-code/issues/8678) | Preserve session on large restore timeout | P1 daemon fix; PR1 merged, providing safe timeout-contract and observability for session restore. |
| [#8562](https://github.com/QwenLM/qwen-code/issues/8562) | tmux flickering on SSH sessions | macOS → Ubuntu via iTerm2/tmux users report screen flicker in Qwen Code TUI; verified by Qwen 3.8 Max as a version regression. |
| [#8097](https://github.com/QwenLM/qwen-code/issues/8097) | Background agent coordination gap | Multi-subagent runs suffer duplicate work, premature completion, and broken `send_message` — critical for multi-agent workflows. |
| [#9002](https://github.com/QwenLM/qwen-code/issues/9002) | SDK rejects `permission_mode="auto"` | CLI supports the mode but Python SDK validation blocks it before it reaches the server — a public API inconsistency. |
| [#9016](https://github.com/QwenLM/qwen-code/issues/9016) | Vertex AI ADC auth failure | Keyless Vertex AI setups cannot authenticate; any API key value returns 401, breaking headless GCP deployments. |
| [#8922](https://github.com/QwenLM/qwen-code/issues/8922) | Shell ignores `truncateToolOutputThreshold` | Configured threshold is silently overridden by a hardcoded 30,000-char budget — docs vs. behavior gap. |
| [#8979](https://github.com/QwenLM/qwen-code/issues/8979) | MAX_TOKENS recovery duplicates turns | Durable transcript diverges from in-memory history after output-token recovery, causing duplicated turns on `--resume`. |

---

## 4. Key PR Progress

| PR | Title | Summary |
|----|-------|---------|
| [#8890](https://github.com/QwenLM/qwen-code/pull/8890) | Generalize Conversations runtime | Refactors the CLI conversations foundation for broader reuse across interactive and headless paths. |
| [#8848](https://github.com/QwenLM/qwen-code/pull/8848) | Redesign Channel policy & workspace mgmt | Web-shell channels now expose sender/group policies, allowlists, and workspace ownership controls per adapter. |
| [#8950](https://github.com/QwenLM/qwen-code/pull/8950) | Visualize dynamic workflow runs | First-class background workflow UI with live execution graphs, phase lanes, dependency edges, and pause/resume/stop/retry controls. |
| [#8989](https://github.com/QwenLM/qwen-code/pull/8989) | Localize background task notifications | Daemon attaches structured locale data to notification strings; no more hardcoded English in background alerts. |
| [#8974](https://github.com/QwenLM/qwen-code/pull/8974) | Configure Qwen 3.8 reasoning | Exact-match model manifest enables `qwen3.8-max` Thinking with `low`/`medium`/`xhigh` effort controls in Web Shell. |
| [#8735](https://github.com/QwenLM/qwen-code/pull/8735) | Durable replay journal | Workflow replay state written through a per-run queue with versioned checkpoints; pause/terminal states wait for durability. |
| [#9007](https://github.com/QwenLM/qwen-code/pull/9007) | Bound ACP HTTP pre-attach buffers | Adds byte-level bounds to ACP HTTP buffers, preventing unbounded memory growth during pre-attach phases. |
| [#9022](https://github.com/QwenLM/qwen-code/pull/9022) | Keep review context within file limit | Narrows repository review manifest expansion from full skills subtree to top-level TS impl/tests + bundled `SKILL.md` files. |
| [#8357](https://github.com/QwenLM/qwen-code/pull/8357) | Guard manual dream tool turns | Extends pinned-memory protection to `/dream` slash-command turns across TUI, headless, and ACP execution paths. |
| [#9014](https://github.com/QwenLM/qwen-code/pull/9014) | Honor Shell truncation threshold | Shell now respects `tools.truncateToolOutputThreshold` at both output boundaries; falls back to 30k only when unset. |

---

## 5. Feature Request Trends

- **Multimodal / Omni integration** — Issue #8197 tracks a protected `omni-experiment` branch with a design doc for multimodal file recognition and metadata; community interest in richer media handling is growing.
- **Hierarchical AGENTS.md discovery** — Issue #6101 calls for downward scans in monorepos and upward walks beyond project root, addressing polyrepo pain.
- **Desktop shell consolidation** — Issue #8596 proposes deprecating the Electron app and renaming the Tauri `desktop-shell` to `desktop`, signaling a strategic shift to Tauri.
- **Multi-agent coordination primitives** — Issue #8097 and PR #8730 both point to demand for reliable cross-session messaging, durable replay, and background agent orchestration.
- **Web-shell feature expansion** — File uploads (#8874), tmux-backed interactive sub-agents (#8613), and dynamic workflow visualization (#8950) show the Web Shell is a major investment area.

---

## 6. Developer Pain Points

1. **Long-running headless tasks hang** — Multiple reports (#8963, #9026) of non-interactive runs stalling or hard-failing with `NO_TOOL_RESULT_PROGRESS`, especially overnight jobs.
2. **Authentication fragility** — Vertex AI ADC issues (#9016, #9025) and SDK validation mismatches (#9002) indicate auth plumbing is a frequent friction point across cloud providers.
3. **Image-loading regression** — Crash on image read since v0.21.2 (#8957) is a high-impact regression for projects using multimodal inputs.
4. **TUI rendering glitches** — tmux flicker (#8562), project-list icon jitter on scrollbar appearance (#8985), and virtualized history selection issues (#8131) degrade the interactive experience.
5. **Config ≠ behavior drift** — Shell ignoring `truncateToolOutputThreshold` (#8922), `--approval-mode` missing from `--help` (#8897), and `permission_mode="auto"` rejected by SDK (#9002) all reflect a pattern where documented or CLI-accessible settings don't reach their targets.
6. **Session resumption correctness** — MAX_TOKENS recovery producing divergent transcripts (#8979) and session navigation canceling source prompts (#8923) undermine trust in `--resume` and `--continue` workflows.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / CodeWhale Community Digest — 2026-08-13

## 1. Today's Highlights

The CodeWhale project (formerly DeepSeek TUI) shipped **v0.9.6** and is actively closing out a series of v0.9.5 regressions, including a critical Auto-Review bypass bug and a MCP spec compliance fix. The community is also energized by the new **interactive extensions manager** (`/plugin`) and the **terminal pin-on-top** feature for Windows, both harvested from contributor PRs and merged directly by the maintainer.

---

## 2. Releases

**v0.9.6** — The latest public release. Note that the legacy `deepseek-tui` npm package is officially deprecated; all future releases ship under `codewhale` (lowercase). The `codewhale` command, npm package, and release-asset names remain as-is.

---

## 3. Hot Issues

| # | Issue | Why It Matters |
|---|-------|---------------|
| **#5323** [OPEN] [bug] Regression: Auto-Review mode silently blocks every Bash call and write op | Critical v0.9.5 regression that inverts Auto-Review from auto-approving to silently blocking all destructive actions. Users report zero visibility into why operations fail. |
| **#5322** [OPEN] [bug] Output area doesn't fill wide terminals (worked in v0.8.65) | UX regression on wide displays — text is cramped with unused whitespace. Easy to repro, high visual impact. |
| **#5335** [OPEN] [bug] `serve --mcp` returns `nextCursor: null`, breaking strict MCP clients | Violates the MCP specification (field must be string or absent). Claude Code and other strict clients reject the response outright. |
| **#5316** [OPEN] EPIC-005: TUI Crate Decomposition (Umbrella) | Long-running architectural epic to split the monolithic TUI crate into smaller, independent crates. Tracks all sub-EPICs and FEAT reports. |
| **#4949** [OPEN] Discussion: Chinese translation of "Constitution" | Community debate over whether "Constitution" should render as 宪法, 协作准则, or another term — touches on tone, authority, and political sensitivity in Chinese. |
| **#5337** [OPEN] Retire every `isZh` branch and inline `{en, zh}` module | Completing the i18n dictionary spine started in #4934. Removes a large remaining surface of locale-gated code. |
| **#5209** [CLOSED] File(`action=edit`) silently accepts wrong params and reports fake success | Subtle but destructive bug: using `new_str` instead of `replace` returns false-positive success, leading to 3–5× unnecessary re-edits per location. |
| **#5034** [CLOSED] Switching providers can retain an unrelated default model | Provider/model resolution was not updating coherently — switching to OpenAI could leave `gpt-5.5` as the default even when inherited from a different route. |
| **#5267** [CLOSED] Turn-stop honesty: status that says ending must end | Trust issue — when the footer says "ending"/"stopping" the model kept generating. Fixed by preferring deletion of false guards over adding more prose. |
| **#5250** [CLOSED] Only one API key can be saved across providers | Users with multiple providers (DeepSeek + GLM, etc.) had to re-obtain keys on every switch. Multiple-key persistence was a highly requested improvement. |

---

## 4. Key PR Progress

| # | PR | Summary |
|---|-----|---------|
| **#5339** [OPEN] `fix(engine): suppress child-owned shell completions` | Filters child-owned background shell completions out of the parent model stream; preserves unowned parent completions and task/status visibility. Closes #5325. |
| **#5336** [OPEN] `fix(mcp): omit nextCursor when there are no further pages` | Fixes #5335 — drops the invalid `null` nextCursor from MCP `tools/list` and `resources/list` responses per spec. |
| **#5333** [OPEN] `feat(tui): pin host terminal as always-on-top mini window` | Harvest of #5318 (SparkofSpike). Windows PiP: right-click or `/pin` shrinks to 640×400 and pins on top; toggling again restores. |
| **#5328** [OPEN] `feat-014: command contract crate boundary` | Prototype for the commands extraction — defines facets + shared types before full production rewiring. Part of EPIC-005/006. |
| **#5338** [OPEN] `feat(web): move docs guide page onto dictionary spine` | First slice of #5337. Retires `isZh` ternaries in `docs/guide/page.tsx` with a per-page `DocsGuideDict` pattern (9 keys). |
| **#5327** [CLOSED] `feat(tui): add interactive extensions manager` | New `/plugin` and `/plugins` commands with a localized interactive manager. Centralizes bundle lifecycle behind a digest-bound controller. |
| **#5331** [CLOSED] `fix(tui): copy messages without visual rails` | Harvest of #5319 (XhesicaFrost). "Copy message" now copies canonical source content instead of rendered Ratatui lines with rail decorations. |
| **#5330** [CLOSED] `fix(session): separate snapshot reads from crash recovery` | Harvest of #5320 (h3c-hexin). Adds `load_session_snapshot` for side-effect-free reads and `recover_session_for_resume` with repair stats. |
| **#5332** [CLOSED] `feat(config): register OrcaRouter as a named provider` | Harvest of #5321 (XiaoHuo888-hue). OrcaRouter now wires like OpenRouter — one `ORCAROUTER_API_KEY` unlocks 150+ models. |
| **#5329** [CLOSED] `fix(tui): move lru to 0.18 and unpin ratatui-core` | Addresses RUSTSEC-2026-0253 — `lru` 0.16.4's `LruCache::pop()` is panic-unsafe. Upgraded to 0.18.2 and unpinned ratatui-core. |

---

## 5. Feature Request Trends

- **Multi-provider key management**: #5250 and #5047 converged on the need for durable, per-provider API key storage rather than repo-scoped or single-key limitations.
- **i18n cleanup**: #5337 and #5334 show sustained effort to retire ad-hoc locale branches (`isZh`, partial-pack declarations) in favor of a unified dictionary spine.
- **Session durability and recovery**: #5000 (interrupted output as first-class session item), #5272 (prompt-scoped file recovery), and #5320 (snapshot vs. crash recovery separation) reflect a strong push toward resilient, recoverable agent sessions.
- **Terminal UX refinements**: PiP window pinning (#5318/5333), wide-terminal output filling (#5322), and rail-clean copy (#5314/5331) point to continued investment in the host-terminal experience.
- **MCP spec compliance**: #5335/#5336 highlights the project's push to align with strict MCP clients, suggesting broader ecosystem integration goals.

---

## 6. Developer Pain Points

1. **Regression sensitivity around v0.9.5**: Multiple high-impact regressions (Auto-Review silence-blocking, output-area width cap, file-edit false positives) suggest the v0.9.5 release window needs tighter regression testing, especially around mode-switching behavior.
2. **Base drift in community PRs**: Nearly every harvested community PR (#5318, #5320, #5321, #5319) failed CI only due to stale base commits (runtime-contract measurements, `release-credits.ts` parity). Maintainers are regularly re-landing identical changes — a signal that PR baselining guidance or CI auto-rebasing could reduce friction.
3. **Provider/model resolution coupling**: #5034 revealed that provider switches don't coherently update model defaults, a pattern that likely extends to other config surfaces and would benefit from explicit resolution contracts.
4. **Security surface of API keys**: #5047 showed keys sometimes persisting only in working-repo config rather than the global secret store — a trust and portability issue that users flagged repeatedly.
5. **MCP spec edge cases**: The `nextCursor: null` bug (#5335) is a spec-compliance gap that breaks strict clients. Similar edge cases in tool listing, resource pagination, or schema validation may lurk and warrant a compliance audit pass.

---

*Source: [github.com/Hmbown/CodeWhale](https://github.com/Hmbown/CodeWhale)*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*