# AI CLI Tools Community Digest 2026-08-02

> Generated: 2026-08-02 03:33 UTC | Tools covered: 10

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
**Date:** 2026-08-02

---

## 1. Ecosystem Overview

The AI CLI tools landscape in August 2026 is characterized by rapid iteration toward production-grade reliability, with all major vendors actively hardening session management, subagent orchestration, and provider compatibility. The dominant theme is a shift from feature expansion to operational stability — communities are surfacing resource leaks, context-compaction failures, and credential-scoping bugs that indicate these tools are being adopted for sustained, complex workflows rather than single-turn experimentation. Multi-provider flexibility (BYOK, OpenAI-compatible gateways, Bedrock) and cross-platform parity (Windows/WSL2, macOS File Provider, Linux) remain the primary friction points distinguishing mature tools from early-stage ones.

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Release (Last 24h) |
|------|-----------:|--------:|-------------------|
| **Claude Code** | 10 | 3 | None |
| **OpenAI Codex** | 10 | 10 | None |
| **Gemini CLI** | 10 | 10 | v0.55.0-nightly.20260802 |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.78-2 |
| **Kimi Code CLI** | 5 | 5 | None |
| **OpenCode** | 10 | 10 | v1.18.11 |
| **Pi** | 10 | 10 | None |
| **Qwen Code** | 10 | 10 | v0.21.3 + nightly |
| **DeepSeek TUI** | 10 | 9 | None |
| **Grok Build** | 0 | 0 | None |

**Summary:** All tools except Grok Build showed substantive community activity. OpenAI Codex, Gemini CLI, OpenCode, Pi, and Qwen Code led with 10 PRs each, indicating high engineering throughput. Three tools shipped releases (Gemini CLI nightly, Copilot CLI patch, Qwen Code stable + nightly).

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Session reliability & resume** | Claude Code, Codex, Copilot CLI, OpenCode, DeepSeek | Auto-compact destroying sessions (#31033), session corruption on rename (#73638), V8 string-length crashes (#22004, #4325), sticky session state across restarts |
| **Subagent visibility & control** | Gemini CLI, OpenCode, Copilot CLI, DeepSeek | Subagent hangs (#21409), turn-limit misreporting (#22323), permission enforcement regressions (#22093), no TUI subagent view (#15223) |
| **BYOK / multi-provider support** | Copilot CLI, OpenCode, Qwen Code, DeepSeek | Multiple BYOK models per session (#3282), custom model provider parity (#29156), private ASR base URLs (#8286), Bedrock Mantle (#40119) |
| **Prompt-cache efficiency** | Qwen Code, DeepSeek | Cache prefix reuse during compaction (#8279), hit-rate telemetry (#8284), deferred tool lists busting cache (#4777) |
| **Voice / TTS input** | Codex, Claude Code | Voice transcription in CLI/TUI (#14630, #42700) |
| **Credential & config scoping** | DeepSeek, Copilot CLI | Global vs. repo-scoped keys (#5045, #5047), nested agent tool grants (#4320), OAuth scope minimization |
| **MCP lifecycle & reliability** | Codex, OpenCode, Copilot CLI | Subagent MCP process leaks (#17574), eager vs. lazy loading (#2901), SSE reconnect loops (OpenCode v1.18.11) |
| **Plugin / skill observability** | OpenCode, Gemini CLI, Kimi Code | Skills not listing via `/skills` (#21282), skills ignored by default (#21968), unified marketplace (#40108) |

---

## 4. Differentiation Analysis

| Tool | Primary Focus | Target User | Technical Differentiator |
|------|--------------|-------------|------------------------|
| **Claude Code** | Enterprise workflow & safety | Sysadmin, automation, VS Code power users | Safety guardrail transparency; embedded ugrep shim; billing/plan-integration complexity |
| **OpenAI Codex** | Desktop-first agent platform | General developers, Windows/WSL2 users | Portable plugins, two-stroke TUI chords, large MCP catalog (2,048 limit), subagent history isolation |
| **Gemini CLI** | Agent reliability & evals | Research-oriented users, eval-driven teams | Component-level eval infrastructure (76 tests), AST-aware tooling, zero-dependency sandboxing vision |
| **GitHub Copilot CLI** | Autopilot & enterprise integration | GitHub-centric teams, autopilot adopters | Autopilot state machine, split-view sidebar polish, BYOK multi-model sessions |
| **Kimi Code CLI** | Provider compatibility & encoding | OpenAI-compatible gateway users | Double-encoded JSON unwrapping, GBK console crash fix, StrReplaceFile accuracy |
| **OpenCode** | Plugin ecosystem & provider flexibility | Multi-provider users, privacy-conscious deployers | Unified marketplace vision, Bedrock Mantle support, grep deny-rule fix, lazy-scroll for large sessions |
| **Pi** | Compiler-grade TUI fidelity | Power users, terminal purists | Switchable terminal renderers, deterministic compaction contract, pre-dispatch durability barrier |
| **Qwen Code** | Code review & local model support | Enterprise monorepo users, local-model deployers | Enhanced `/review` command with test-plan validation, prompt-cache reuse, Java daemon E2E hardening |
| **DeepSeek TUI** | Rust-native reliability & multi-provider | Multi-provider Rust users, devcontainer workflows | Credential path safety, deterministic compaction continuation, workspace-scoped task listing |

---

## 5. Community Momentum & Maturity

**High Momentum (rapid iteration, high PR throughput):**
- **OpenAI Codex** — 10 PRs including portable plugins, MCP catalog doubling, two-stroke chords; strong engineering velocity
- **OpenCode** — 10 PRs covering marketplace, Bedrock, SQLite retry, lazy-scroll; diverse feature areas addressed simultaneously
- **Qwen Code** — Stable release (v0.21.3) with `/review` enhancements plus two nightly builds; balanced release cadence
- **Gemini CLI** — Nightly build with parallel tool serialization, symlink normalization, data-corruption mitigation

**Mature but Stabilizing (focus on bug-fixing over features):**
- **Claude Code** — Only 3 PRs but high-impact safety and billing fixes; community raising critical operational issues
- **DeepSeek TUI** — 9 PRs focused on credential safety, compaction semantics, and devcontainer support; Rust codebase health concerns (464 `#[allow(dead_code)]`) signal architectural debt

**Emerging / Smaller Community:**
- **Kimi Code CLI** — 5 issues, 5 PRs; smaller but responsive community with practical encoding and shell fixes
- **Pi** — 10 PRs but niche focus on TUI rendering fidelity and compaction reliability
- **GitHub Copilot CLI** — Patch release (v1.0.78-2) with UX polish; no PRs this cycle, suggesting a more conservative release strategy

**No Activity:**
- **Grok Build** — Zero community engagement this cycle

---

## 6. Trend Signals

| Signal | Evidence | Implication for Developers |
|--------|----------|---------------------------|
| **Context compaction is the #1 reliability frontier** | Codex #31033, OpenCode #22813, Pi #6879/#7020/#7048, DeepSeek PR #5064, Qwen Code PR #8339 | Tools that solve compaction correctly (deterministic contracts, cache reuse, summary fidelity) will gain enterprise trust |
| **Subagent orchestration is immature across all tools** | Gemini #21409/#22323/#22093, OpenCode #24342/#40115, Codex #17574, Copilot #4306 | Subagent transparency, permission enforcement, and lifecycle management are table-stakes differentiators in 2026 |
| **BYOK / multi-provider is a must-have, not a nice-to-have** | Copilot #3282/#2904/#4327, OpenCode #40119, Qwen #8286, DeepSeek #5034 | Tools with clean per-agent model config and session-scoped provider switching will win power-user adoption |
| **Windows/WSL2 remains the weakest platform** | Codex #35420/#25178/#28103, DeepSeek #4085/#4716, Kimi #2577, Copilot #4328 | Multi-platform parity is a competitive advantage; tools with Windows-native testing pipelines stand out |
| **Session state corruption is a silent trust-killer** | Claude #73638, Codex #22004/#31033, Copilot #4325, OpenCode #26159 | Tools that document session durability guarantees and provide recovery paths will reduce support burden |
| **Credential scoping failures are security-relevant** | DeepSeek #5045/#5047, Copilot #4320 | Tools that enforce global vs. repo-scoped config boundaries out of the box reduce operator risk |
| **Prompt-cache efficiency directly impacts cost** | Qwen #8279/#8284/#4777, DeepSeek PR #5064 | Cache-aware tooling that exposes hit-rate telemetry will attract cost-conscious enterprise users |
| **TUI rendering fidelity is a luxury differentiator** | Pi #5931/#7402, OpenCode #26625, DeepSeek #4716 | As CLI tools mature, terminal experience quality becomes a retention factor for power users |

---

*Report generated from community digest data dated 2026-08-02. Data sourced from official GitHub repositories for each tool.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-02 | Source: anthropics/skills**

---

## 1. Top Skills Ranking

| # | Skill | Functionality | Status | Link |
|---|-------|--------------|--------|------|
| 1 | **skill-creator** (run_eval fix) | Fixes the skill-description optimization loop, which consistently reported `recall=0%` due to broken trigger detection and Windows subprocess/encoding bugs. | 🔴 Open | [PR #1298](https://github.com/anthropics/skills/pull/1298) |
| 2 | **document-typography** | Prevents orphan lines, widow paragraphs, and numbering misalignment in AI-generated documents. Targets a universal pain point in Claude's document output. | 🔴 Open | [PR #514](https://github.com/anthropics/skills/pull/514) |
| 3 | **skill-quality-analyzer + skill-security-analyzer** | Two meta-skills that evaluate skills across five dimensions (structure, documentation, quality, security, correctness) — essentially an audit framework for the skills ecosystem itself. | 🔴 Open | [PR #83](https://github.com/anthropics/skills/pull/83) |
| 4 | **testing-patterns** | Covers the full testing stack: Testing Trophy philosophy, AAA unit tests, React Testing Library, edge cases. Addresses the community's demand for reliable test generation guidance. | 🔴 Open | [PR #723](https://github.com/anthropics/skills/pull/723) |
| 5 | **self-audit** | A pre-delivery quality gate that mechanically verifies claimed output files exist, then performs four-dimension reasoning quality analysis. Model-agnostic. | 🔴 Open | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| 6 | **ODT** | Enables creation, filling, and HTML conversion of OpenDocument Format files (.odt, .ods), targeting the LibreOffice/open-source document workflow. | 🔴 Open | [PR #486](https://github.com/anthropics/skills/pull/486) |
| 7 | **frontend-design** | Clarified and made actionable a previously vague skill, ensuring every instruction is executable within a single conversation context. | 🔴 Open | [PR #210](https://github.com/anthropics/skills/pull/210) |
| 8 | **plan-file-hygiene** | Solves the accumulation problem of planning artifacts (`.md` plans, scratch files) with no lifecycle management — a directly cited community pain point. | 🔴 Open | [PR #1479](https://github.com/anthropics/skills/pull/1479) |

---

## 2. Community Demand Trends

Analysis of top community Issues reveals five concentrated demand vectors:

- **🛡️ Trust & Security Boundaries** — Issue [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍) exposes a critical vulnerability: community skills are distributed under the `anthropic/` namespace, impersonating official skills and enabling trust-boundary abuse. This is the most-commented issue in the repo.
- **⚙️ Skill-Creator Tooling Reliability** — The `run_eval.py` 0% recall bug dominates community frustration (Issues [#556](https://github.com/anthropics/skills/issues/556), [#1169](https://github.com/anthropics/skills/issues/1169), [#1061](https://github.com/anthropics/skills/issues/1061)), with Windows compatibility as a recurring blocker. Users cannot iterate on skill descriptions without this pipeline working.
- **🏢 Organizational Skill Sharing** — Issue [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) requests native org-wide skill distribution, currently requiring manual file exchange via Slack/Teams.
- **🔄 Context & Lifecycle Hygiene** — Issues [#1417](https://github.com/anthropics/skills/issues/1417) (addressed by PR #1479) and [#1487](https://github.com/anthropics/skills/issues/1487) highlight that planning artifacts and oversized skills (156k-token injections) are degrading session quality.
- **🧠 Reasoning Quality Gates** — Issue [#1385](https://github.com/anthropics/skills/issues/1385) proposes a three-gate pipeline (pre-task calibration → adversarial review → delivery verification) for end-to-end output assurance.

---

## 3. High-Potential Pending Skills

These PRs are actively discussed, unresolved, and most likely to land in the near term:

| PR | Skill | Why It's Close |
|----|-------|---------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | skill-creator (run_eval fix) | Multiple converging PRs (#1099, #1050, #1323, #1261) all target the same subsystem — a merge wave is likely. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit | Directly extends Issue #1385's reasoning-quality-gate proposal; author is an active community contributor. |
| [#541](https://github.com/anthropics/skills/pull/541) | docx (tracked-change fix) | Specific OOXML root-cause fix from a recurring contributor; low-risk, high-impact. |
| [#1479](https://github.com/anthropics/skills/pull/1479) | plan-file-hygiene | Built on explicitly credited community framing; author offers to hand off — signals readiness for merge. |
| [#514](https://github.com/anthropics/skills/pull/514) | document-typography | Addresses a universal document-quality gap with a focused, well-scoped feature. |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for reliable skill authoring tooling and trust-safe skill distribution** — users are actively building skills but blocked by broken evaluation pipelines and exposed to namespace impersonation, making the *process of creating and deploying skills* a higher-priority pain point than any single skill domain.

---



# Claude Code Community Digest — 2026-08-02

## 1. Today's Highlights

A wave of new issues filed today centers on **Fable 5 / Opus 5 safety guardrail false-positives** blocking routine sysadmin and automation work, with multiple reports describing silent model downgrades and no fallback path. Concurrently, the long-running **embedded ugrep regex backtracking OOM problem** resurfaces with a new report showing ~29 GB allocations, and the VS Code auto-attach setting request continues to gather strong community support at 197 upvotes.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**#24726** — VS Code extension: setting to disable auto-attach of open file / selection
[Link](https://github.com/anthropics/claude-code/issues/24726)
The most-upvoted open issue (197 👍, 64 comments). Users repeatedly want granular control over when Claude Code attaches to the active editor context; the absence of a disable toggle forces workarounds every session.

**#54394** — v2.1.117 ugrep wrapper amplifies regex backtracking into V8-heap OOM on WSL2
[Link](https://github.com/anthropics/claude-code/issues/54394)
The shell-snapshot `exec -a ugrep` shim routes every `grep` through the embedded binary, and pathological regexes now cause host freezes. A concrete repro and memory-ceiling detail make this actionable but urgent.

**#82230** — Embedded ugrep allocates ~29 GB on bounded-alternation regexes, OOM-kills host
[Link](https://github.com/anthropics/claude-code/issues/82230)
Directly complements #54394 with a second independent repro showing the same root cause: `.{0,N}(a|b|c).{0,M}` triggers massive RSS allocation. Community sees these as the same underlying shim bug.

**#83233** — Fable 5 guardrails false-positive on routine sysadmin work → silent downgrade to Opus 5
[Link](https://github.com/anthropics/claude-code/issues/83233)
Filed today. Users report the safety classifier silently switches models with no explanation of what was flagged, removing agency and blocking legitimate work.

**#83245** — Safety classifier false-positives block legitimate automation on Fable 5 / Opus 5
[Link](https://github.com/anthropics/claude-code/issues/83245)
Today's follow-up: turns end with an AUP error and **no automatic fallback** to another model, leaving users with no answer and no path forward.

**#83242** — Fable 5 incorrectly draws from usage credits on Max 20× plan
[Link](https://github.com/anthropics/claude-code/issues/83242)
Today's billing issue: Fable 5 is reported as consuming extra-usage credits on a Max plan where it should draw from the included allowance, undermining plan value.

**#80750** — Usage credits consumed while plan allowance remains; extra-usage toggle breaks 5-hour window
[Link](https://github.com/anthropics/claude-code/issues/80750)
A re-report of stale-closed #64949. Credits drain while the plan window shows ~90% capacity, and enabling extra usage prevents the 5-hour plan window from starting — a compounding billing bug.

**#80279** — "Last Activity" filter disappears when grouping sessions by Project after 2.1.209 → 2.1.217 update
[Link](https://github.com/anthropics/claude-code/issues/80279)
Regression in the desktop app's session sidebar. The filter survives under other groupings but vanishes under Project view, degrading session navigation for power users.

**#73638** — Session rename mid-server-tool-call corrupts transcript permanently
[Link](https://github.com/anthropics/claude-code/issues/73638)
Renaming a session while a `server_tool_use` is in flight injects a synthetic user turn between the tool call and its result, causing 400 errors on every subsequent prompt. A serious correctness bug with no workaround once triggered.

**#75630** — Idle VSCode sessions leave native-binary/claude child spinning at 100% CPU for days
[Link](https://github.com/anthropics/claude-code/issues/75630)
Reopened with fresh detail. The child process never idle-exits after the VS Code session closes, accumulating CPU for days — a resource leak that compounds at scale.

---

## 4. Key PR Progress

**#77442** — Fix: repair issue-automation telemetry and dead `days_back` input
[Link](https://github.com/anthropics/claude-code/pull/77442)
Closes two workflow bugs: Statsig events from the dedupe workflow were timestamped at epoch (1970), and the `days_back` input was silently ignored. Cross-checked against invoking scripts for correctness.

**#77439** — Docs: sync security-guidance plugin listing with v2.0.0 manifest
[Link](https://github.com/anthropics/claude-code/pull/77439)
The marketplace listing files still described the old v1.0.0 security-reminder hook after the v2 rewrite in #62586/#62592. Now aligned with the current manifest.

**#77443** — Fix: make stop hook's jq error handling reachable under `set -e`
[Link](https://github.com/anthropics/claude-code/pull/77443)
The ralph-wiggum stop hook's jq failure path was unreachable because `set -euo pipefail` caused the script to exit before the `$?` check. Patch makes the friendly error path actually execute.

---

## 5. Feature Request Trends

- **Granular editor integration control** — The #24726 auto-attach toggle request (197 👍) signals strong demand for per-context control over when Claude Code attaches to VS Code sessions.
- **Voice / TTS accessibility for Remote Control** — #42700 (22 👍) requests TTS readback and voice mode, extending accessibility beyond the terminal.
- **Read-only OAuth scopes for setup-token** — #81015 (1 👍) asks for a `usage:read` or read-only scope so subscription accounts can bootstrap without full inference write access.
- **Transparent safety-classifier feedback** — Multiple today's issues (#83233, #83245, #83244) converge on a single request: when guardrails trigger, surface *what* was flagged and offer a fallback model rather than silently downgrading or aborting.

---

## 6. Developer Pain Points

1. **Embedded ugrep regex backtracking** — Two independent OOM reports (#54394, #82230) confirm the `exec -a ugrep` shim is a persistent stability hazard, especially on WSL2 and large codebases.
2. **Safety guardrail false-positives on newer models** — Fable 5 and Opus 5 are repeatedly flagging routine sysadmin, OS development, and business-automation tasks with no visibility into what triggered the block and no automatic model fallback.
3. **Billing / plan-allowance confusion** — Three issues this cycle (#80750, #82466, #83242) report credits being consumed incorrectly, default model settings not honored, and Fable 5 incorrectly hitting extra-usage on Max plans.
4. **Idle process resource leaks** — #75630 (and the related #83237 hang report) show that Claude Code child processes can spin at 100% CPU or wedge indefinitely after the parent session ends, with no auto-recovery.
5. **Transcript corruption from session rename** — #73638 reveals that renaming a session during an in-flight tool call irreversibly corrupts the conversation state, a fragility in an otherwise common workflow.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-02

## 1. Today's Highlights

No new releases landed in the past 24 hours. Community attention is dominated by performance and stability concerns: unbounded CPU usage on large thread histories (#24510), Windows-side MCP/WSL regressions, and a critical bug where context auto-compaction can ruin active sessions (#31033). Internally, the team shipped several quality-of-life improvements including portable plugin support, larger MCP catalog limits, and TUI two-stroke key chords.

## 2. Releases

*None in the last 24 hours.*

## 3. Hot Issues

1. **#24510 — Codex Desktop high CPU from unbounded thread metadata** (27 comments)
   Large local profiles with many active threads cause sustained CPU/GPU spikes due to unbounded metadata processing. A performance regression affecting power users with deep session histories. [Link](https://github.com/openai/codex/issues/24510)

2. **#35420 — Windows stream disconnects with OneDrive-backed workspaces** (23 comments)
   Requests repeatedly fail with stream-disconnect errors when the Windows workspace sits on a degraded OneDrive mount. Highlights friction between cloud-synced paths and Codex's streaming protocol. [Link](https://github.com/openai/codex/issues/35420)

3. **#25178 — Windows Computer Use screenshot fails on Windows 10 22H2** (19 comments · 11 👍)
   `get_window_state` calls that request screenshots throw `SetIsBorderRequired failed: 不支持此接口` on Windows 10 22H2. A platform-specific API incompatibility blocking Computer Use on older Windows builds. [Link](https://github.com/openai/codex/issues/25178)

4. **#14630 — Voice transcription for TUI** (19 comments · 49 👍)
   Strong community demand to expose OpenAI's voice transcription models in the CLI/TUI, mirroring the superior experience already available in the Codex app. [Link](https://github.com/openai/codex/issues/14630)

5. **#17574 — Subagents leak stdio MCP helper process trees** (14 comments)
   MCP helper trees for tools like `xcodebuildmcp` and `chrome-devtools-mcp` accumulate indefinitely when subagents are used, causing unbounded process growth. [Link](https://github.com/openai/codex/issues/17574)

6. **#18490 — Add 'Compact context and implement plan' to Plan Mode** (13 comments)
   Users want a middle-ground option between clearing context entirely and retaining it: compact rather than wipe, preserving useful history while managing token budget. [Link](https://github.com/openai/codex/issues/18490)

7. **#34773 — ChatGPT for macOS stuck blinking after launch on macOS Tahoe 26.5.2** (11 comments)
   App fails to initialize on the newest macOS release on Apple Silicon M5, suggesting a launch-time compatibility regression. [Link](https://github.com/openai/codex/issues/34773)

8. **#22004 — Windows main-process crash: `RangeError: Invalid string length`** (10 comments · 3 👍)
   Loading sessions whose rollout JSONL exceeds V8's string-length limit crashes the Codex Desktop main process on Windows. A hard ceiling hit by long-running users. [Link](https://github.com/openai/codex/issues/22004)

9. **#31033 — Context automatically compacted / ruins sessions** (9 comments)
   Described as critical: Codex's auto-compact feature triggers mid-session, losing context and consuming rate-limit resets. Users report severe workflow disruption. [Link](https://github.com/openai/codex/issues/31033)

10. **#28103 — MSIX build missing Linux codex binary, breaking WSL agent runs** (7 comments · 23 👍)
    The Microsoft Store / MSIX build of Codex Desktop 26.609.4994.0 omits the Linux `codex` binary from `app/resources`, making "Run agent in WSL" fail immediately. High upvote count signals broad impact on Windows users. [Link](https://github.com/openai/codex/issues/28103)

## 4. Key PR Progress

1. **#36544 — Support portable Agent Plugins throughout installation** (Closed)
   Fixes plugin packaging to handle schema-declared root `plugin.json` files with dotted names or versions that don't fit the legacy directory-safe format. [Link](https://github.com/openai/codex/pull/36544)

2. **#36534 — Raise the MCP catalog item limit to 2,048** (Closed)
   Doubles the maximum number of items collected across paginated MCP tool/resource/resource-template discovery requests, from 1,024 → 2,048. [Link](https://github.com/openai/codex/pull/36534)

3. **#30977 — Drop parent MCP lifecycle events from forked agent history** (Closed)
   Forked agents no longer inherit `McpToolCallBegin`/`McpToolCallEnd` events from the parent, preserving clean child histories while keeping full MCP context in the parent rollout. [Link](https://github.com/openai/codex/pull/30977)

4. **#36511 — Support two-stroke TUI key chords** (Closed)
   TUI keymap config now accepts multi-stroke bindings like `ctrl-x ctrl-s`, with pending-chord hints and proper cancellation on escape. [Link](https://github.com/openai/codex/pull/36511)

5. **#36507 — Retain attempted tool metadata across prompts** (Closed)
   Recorded `executed_tool_calls` metadata is reattached when output is included in subsequent prompts, bounded to 32 KiB with recent-call prioritization and truncation reporting. [Link](https://github.com/openai/codex/pull/36507)

6. **#36485 — Increase remote plugin bundle size limits** (Closed)
   Raises the max remote plugin bundle download from 50 MiB → 100 MiB and total extracted size from 250 MiB → 512 MiB. [Link](https://github.com/openai/codex/pull/36485)

7. **#31471 — Extract apps cache logic into ConnectorRuntimeManager** (Open)
   First in a four-part series refactoring the Codex Apps tools cache behind `ConnectorRuntimeManager` and `ConnectorRuntimeContext`, scoping runtime contexts by account/workspace. [Link](https://github.com/openai/codex/pull/31471)

8. **#36482 — Avoid querying terminal size on every TUI redraw** (Closed)
   Caches screen dimensions on resize events and reuses them for ordinary draws, refreshing only after resize settling, process resume, or external program execution. [Link](https://github.com/openai/codex/pull/36482)

9. **#15261 — Store guardian transcript boundary on review session** (Open)
   Guardian review sessions now cache the parent transcript checkpoint, slicing evidence from the last terminal review rather than reconstructing from rollout state. [Link](https://github.com/openai/codex/pull/15261)

10. **#36440 — Extract exec-server request dispatching** (Closed)
    Consolidates JSON-RPC request/notification/response/error handling into a dedicated `RequestDispatcher`, separating dispatch logic from the connection loop. [Link](https://github.com/openai/codex/pull/36440)

## 5. Feature Request Trends

- **Voice input for CLI/TUI** (#14630) — Users want the high-quality OpenAI voice transcription models available in the desktop app exposed to the command-line interface.
- **Smarter context management** (#18490, #31033) — Demand for granular control over context compaction: compact-and-retain options, user-triggered compaction, and protection against mid-session auto-compact surprises.
- **Custom model provider parity** (#29156) — Desktop users report that custom providers work in CLI/TUI but are "unusable" in the app, especially with existing chat history and the model picker.
- **Custom presets in model picker** (#32665) — Users want configurable presets on the Advanced model picker power slider rather than a fixed set.
- **Side-chat persistence** (#27716) — Request for the ability to reopen closed side chats, preserving history that is otherwise lost.
- **Two-stroke TUI key chords** (#36511) — Power users seeking complex keyboard shortcuts in the TUI (now shipped).

## 6. Developer Pain Points

- **Unbounded resource growth** (#24510, #17574, #22004, #35799): Multiple issues describe memory/CPU/process leaks triggered by large histories, subagent MCP trees, or background prefetch of heavy rollouts. The common thread is that Codex lacks sane bounding on historically accumulated state.
- **Windows-specific regressions** (#35420, #25178, #28103, #31989): A disproportionate number of active bugs target Windows — OneDrive path failures, missing WSL binary in the MSIX bundle, Computer Use screenshot API incompatibility, and intermittent native crashes (`0xc0000409`).
- **Context auto-compaction disrupting sessions** (#31033): Users report the auto-compact feature triggering mid-workflow and destroying in-progress sessions, consuming rate-limit resets in the process.
- **Session state staleness** (#28870, #34453): Stale `updatedAt` timestamps after SQLite/rollout metadata swaps, and Full Access sessions reverting to per-action approval after restart, both erode trust in session continuity.
- **MCP reliability gaps** (#36486, #25015): The TUI falsely reports MCP startup failures for servers that connected successfully, and subagent-spawned MCP process stacks are not cleaned up, pointing to a race/lifecycle fragility in the MCP integration layer.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-02

## 1. Today's Highlights

A new nightly build (`v0.55.0-nightly.20260802`) shipped overnight, continuing the v0.55 cadence. The community is actively flagging two high-impact agent reliability bugs — subagent turn-limit misreporting (#22323) and the generalist agent hanging indefinitely (#21409) — while core fixes land for parallel tool serialization, data corruption on massive writes, and symlink-aware project path resolution.

## 2. Releases

- **v0.55.0-nightly.20260802.gf47d6c6f7** — Nightly build for the v0.55 track. [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.55.0-nightly.20260801.gf47d6c6f7...v0.55.0-nightly.20260802.gf47d6c6f7)

## 3. Hot Issues

1. **#22323** — Subagent recovery after MAX_TURNS misreported as GOAL success *(12 comments, 2 👍)*
   The `codebase_investigator` reports `status: "success"` and `GOAL` termination even when it hit the turn limit without performing analysis. This misreporting can silently corrupt evaluation results and confuses users about agent behavior.

2. **#21409** — Generalist agent hangs indefinitely *(8 comments, 8 👍)*
   Simple tasks like folder creation cause the generalist subagent to hang forever, with workarounds requiring explicit instructions to avoid subagents. The high upvote count signals broad user impact.

3. **#19873** — Leverage bash affinity via Zero-Dependency OS Sandboxing *(8 comments, 1 👍)*
   Proposes using Gemini 3's native bash capabilities within a zero-dependency sandbox, chaining POSIX tools for codebase exploration — a significant architectural direction for the agent platform.

4. **#24353** — Robust component-level evaluations *(7 comments)*
   Tracks the evolution of behavioral eval infrastructure, now at 76 tests across 6 supported Gemini models. Critical for measuring agent reliability improvements.

5. **#22745** — AST-aware file reads, search, and mapping *(7 comments, 1 👍)*
   Evaluates whether AST-aware tools can reduce misaligned reads and token noise, potentially improving agent accuracy in codebase navigation.

6. **#21968** — Gemini does not use skills and sub-agents enough *(6 comments)*
   Users report the model ignores custom skills and subagents unless explicitly instructed, suggesting a gap between capability and default behavior.

7. **#26522** — Auto Memory retrying low-signal sessions indefinitely *(5 comments)*
   Sessions the extraction agent deems low-signal remain unprocessed and can be repeatedly surfaced, creating a noise loop in the memory inbox.

8. **#26525** — Deterministic redaction and reduced Auto Memory logging *(4 comments)*
   Secrets may reach model context before redaction occurs; this issue tracks tightening the security posture around transcript processing.

9. **#25166** — Shell commands stuck in "Waiting input" after completion *(4 comments, 3 👍)*
   Simple CLI commands that should be non-interactive leave the agent in a perpetual "Awaiting user input" state — a high-friction bug for power users.

10. **#22093** — Subagents running without permission since v0.33.0 *(3 comments)*
    Users with agents explicitly disabled report the generalist agent activating after upgrading, indicating a regression in permission enforcement.

## 4. Key PR Progress

1. **#28438** — Trim tool names before registry lookup *(CLOSED)*
    Fixes a bug where whitespace-padded tool names failed to resolve through the script registry. Includes a regression test. [Link](https://github.com/google-gemini/gemini-cli/pull/28438)

2. **#28535** — Use `resolveRipgrepPath` in perf test setup *(OPEN)*
   Updates the performance test global setup to use the current ripgrep resolver API, preventing failures after the `canUseRipgrep()` helper was removed. [Link](https://github.com/google-gemini/gemini-cli/pull/28535)

3. **#28534** — Retry `staging-tmp` dist-tag removal after npm publish *(OPEN)*
   Addresses a flaky CI issue where the dist-tag removal runs before npm acknowledges the publish; adds a retry script for robustness. [Link](https://github.com/google-gemini/gemini-cli/pull/28534)

4. **#27070** — Optimize virtual list v2 *(OPEN, Stale)*
   Performance work optimizing the virtualized list and scrolling checkpoint, fixing flaky plan-mode tests and updating tool-permission assertions after rebase. [Link](https://github.com/google-gemini/gemini-cli/pull/27070)

5. **#27351** — Serialize conflicting parallel mutator tools *(OPEN, Stale)*
   Resolves #27285 by enforcing sequential execution when the model proposes multiple edits to the same file in a single turn, replacing the previous `Promise.all` approach. [Link](https://github.com/google-gemini/gemini-cli/pull/27351)

6. **#27350** — Resolve symlinks when normalizing project paths *(OPEN, Stale)*
   Fixes a bug where different symlink paths to the same directory were treated as separate projects, causing fragmented session stores. [Link](https://github.com/google-gemini/gemini-cli/pull/27350)

7. **#27320** — Mitigate data corruption on massive `write_file` *(OPEN, Stale)*
   Addresses #27213: files with 6000+ character literal blocks (e.g., inline base64) were corrupted due to token limits and LLM attention degradation. [Link](https://github.com/google-gemini/gemini-cli/pull/27320)

8. **#27317** — Defensive directory checks in session/checkpoint scans *(OPEN, Stale)*
   Prevents `EISDIR` errors when directories matching session/checkpoint filename patterns are encountered during CLI scans. [Link](https://github.com/google-gemini/gemini-cli/pull/27317)

9. **#27310** — Subagent trajectory infrastructure, Stage 1 *(OPEN, Stale)*
   First in a 3-part series enabling visibility into subagent trajectories for chat saving, history export, and bug reports. [Link](https://github.com/google-gemini/gemini-cli/pull/27310)

10. **#27131** — Route personal OAuth users to stable models *(OPEN, Stale)*
    Fixes 404/400 errors when personal OAuth users resolve the `auto-gemini-3` alias to an unavailable model endpoint. [Link](https://github.com/google-gemini/gemini-cli/pull/27131)

## 5. Feature Request Trends

- **Subagent visibility & control** — Multiple requests (subagent trajectory sharing via `/chat share` #22598, better permission enforcement #22093, and improved skills utilization #21968) point to a community desire for more transparent and controllable subagent behavior.
- **AST-aware codebase tools** — Two linked issues (#22745, #22746) explore whether parsing-aware reads and searches can reduce token waste and improve navigation accuracy.
- **Zero-dependency sandboxing** — Issue #19873 proposes leveraging the model's native bash skills within a lightweight sandbox, reflecting interest in reducing runtime dependencies while preserving security.
- **Evaluation infrastructure** — Component-level evals (#24353) and behavioral test generation signal a sustained push toward measurable agent quality.
- **Auto Memory hardening** — Three related issues (#26522, #26525, #26523) target reliability and security gaps in the memory extraction pipeline.

## 6. Developer Pain Points

- **Agent reliability under edge conditions** — Subagent hangs (#21409), turn-limit misreporting (#22323), and agents activating without permission (#22093) are the most upvoted friction points. Users want agents to fail gracefully and respect explicit configuration.
- **Shell command stalls** — Commands completing but leaving the CLI in "Waiting input" (#25166) or interactive prompts trapping the agent (#22465) break automation workflows.
- **Filesystem & path handling** — Symlink-based project identity (#20079, #27350), tmp script sprawl (#23571), and data corruption on large writes (#27320) suggest the path and I/O layer needs continued hardening.
- **Tool registry scaling** — A 400 error threshold at ~128 tools (#24246) indicates the tool discovery and registration pipeline doesn't gracefully handle large tool counts, a growing concern as the ecosystem expands.
- **Browser agent robustness** — Wayland failures (#21983), settings.json overrides being ignored (#22267), and lack of session recovery (#22232) make the browser agent a persistent source of issues for users on non-Linux-X11 environments.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-02

## 1. Today's Highlights

GitHub Copilot CLI v1.0.78-2 landed today with UX refinements to the split-view sidebar and a fix for duplicate slash-command handler invocations. The community remains highly engaged on BYOK multi-model support and session resilience, with three new session-related bugs reported in the last 24 hours. Autopilot mode continues to surface edge-case issues around session resume, task enforcement, and nested agent tool grants.

---

## 2. Releases

**v1.0.78-2** — A patch release focused on polish and correctness:

- **[Improved]** Split-view sidebar: the red close confirmation now reads `x again to close` (or `x again to exit CLI` on the last session), making it unambiguous that a second press is required to close.
- **[Fixed]** Extension slash commands now run their handler exactly once per invocation when multiple extensions are active, eliminating duplicated behavior.

🔗 [github.com/github/copilot-cli](https://github.com/github/copilot-cli)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#3282](https://github.com/github/copilot-cli/issues/3282) | Add multiple BYOK model capability | Users with multiple custom models via BYOK must currently terminate sessions to switch — a major workflow blocker. | 🔥 19 👍 · 6 comments |
| [#2904](https://github.com/github/copilot-cli/issues/2904) | Custom Agent YAML: Support reasoning effort per agent | Reasoning effort is only configurable globally; per-agent control would let fine-tuned agents use the right effort level without affecting others. | 🔥 16 👍 · 3 comments |
| [#2901](https://github.com/github/copilot-cli/issues/2901) | Lazy-load MCP servers on first tool invocation | All MCP servers connect at startup, inflating latency for users with many configured servers (ADO, GitHub, Work IQ, custom agents). | 🔥 14 👍 · 2 comments |
| [#4305](https://github.com/github/copilot-cli/issues/4305) | `Undefined` → Rust `String` conversion error after 1.0.76 upgrade | A regression that surfaces on nearly every command after upgrading to 1.0.76, breaking the CLI entirely for affected users. | Closed · 5 👍 |
| [#4325](https://github.com/github/copilot-cli/issues/4325) | Session permanently unloadable when `events.jsonl` exceeds V8 max string length | Long-lived sessions can corrupt session resumes — the session is listed and its row exists, but no support can load it. | 2 👍 · 2 comments |
| [#4327](https://github.com/github/copilot-cli/issues/4327) | BYOK streaming drops `apply_patch` input before execution | When using `wireApi: "responses"`, the CLI invokes `apply_patch` with an empty argument string despite the SDK stream containing the full input. Critical for BYOK users relying on patching. | 1 👍 |
| [#4306](https://github.com/github/copilot-cli/issues/4306) | Subtasks freeze and stop responding in autopilot | Fleet-based autopilot workflows (`speckit-implement` ↔ `speckit-converge`) can freeze mid-loop, leaving sessions unresponsive. | 1 👍 |
| [#4299](https://github.com/github/copilot-cli/issues/4299) | Increasing typing latency over long sessions | Long-running sessions with background agents exhibit severe typing lag, degrading UX to the point of unusability. | 1 👍 |
| [#4318](https://github.com/github/copilot-cli/issues/4318) | Autopilot task-completion enforcement overrides explicit user instructions | The agent continues acting after a user narrows a task to research-only, contradicting explicit instructions. | 0 👍 |
| [#4329](https://github.com/github/copilot-cli/issues/4329) | Autopilot not re-enabled when resuming a session | Autopilot appears enabled in the statusline after `/resume`, but actions requiring approval fail — a silent misconfiguration. | Triage · 0 👍 |

---

## 4. Key PR Progress

*No pull requests were updated in the last 24 hours.*

---

## 5. Feature Request Trends

From the open issues this cycle, three clear directions emerge:

1. **BYOK Flexibility** — Users want to manage multiple bring-your-own-keys models within a single session without restarting, and to have finer-grained control over how BYOK interacts with autopilot and premium billing ([#3282](https://github.com/github/copilot-cli/issues/3282), [#2632](https://github.com/github/copilot-cli/issues/2632), [#4327](https://github.com/github/copilot-cli/issues/4327)).

2. **Per-Agent / Per-Context Configuration** — The community repeatedly requests that agent-level settings (reasoning effort, MCP tool grants, model selection) work at the `.agent.md` level rather than being restricted to global CLI flags ([#2904](https://github.com/github/copilot-cli/issues/2904), [#4320](https://github.com/github/copilot-cli/issues/4320)).

3. **Performance & Session Reliability** — Lazy-loading MCP servers ([#2901](https://github.com/github/copilot-cli/issues/2901)), fixing long-session typing latency ([#4299](https://github.com/github/copilot-cli/issues/4299)), and preventing session corruption from oversized event logs ([#4325](https://github.com/github/copilot-cli/issues/4325)) are all requests for the CLI to scale gracefully with longer, more complex workflows.

---

## 6. Developer Pain Points

- **Session lifecycle fragility:** Multiple bugs converge around session resume and state loss — V8 string-length overflows ([#4325](https://github.com/github/copilot-cli/issues/4325)), autopilot not persisting across resumes ([#4329](https://github.com/github/copilot-cli/issues/4329)), plan mode hanging after session switches ([#4319](https://github.com/github/copilot-cli/issues/4319)), and todo/plan drift after forking ([#4324](https://github.com/github/copilot-cli/issues/4324)). Users report sessions becoming permanently unusable after long runs.

- **Autopilot reliability in complex workflows:** Subtask freezing ([#4306](https://github.com/github/copilot-cli/issues/4306)), enforcement overriding explicit instructions ([#4318](https://github.com/github/copilot-cli/issues/4318)), and incorrect BYOK premium billing in autopilot ([#2632](https://github.com/github/copilot-cli/issues/2632)) suggest autopilot's state machine needs tighter validation.

- **MCP configuration friction:** Comments in `.mcp.json` silently invalidate the entire file ([#4323](https://github.com/github/copilot-cli/issues/4323)), nested agent tool grants are undocumented and break across levels ([#4320](https://github.com/github/copilot-cli/issues/4320)), and all MCP servers load eagerly at startup ([#2901](https://github.com/github/copilot-cli/issues/2901)).

- **Windows / WSL2 edge cases:** Git symlink handling for plugin installs on Windows ([#2286](https://github.com/github/copilot-cli/issues/2286)) and `Ctrl+H` being misinterpreted as `Ctrl+Backspace` under WSL2 with Windows Terminal ([#4328](https://github.com/github/copilot-cli/issues/4328)) continue to surface platform-specific input and filesystem issues.

- **Installation regressions:** Version-specific installs appear to always pull the latest version ([#4317](https://github.com/github/copilot-cli/issues/4317)), and a post-upgrade Rust/JS type mismatch crashes the CLI on every command ([#4305](https://github.com/github/copilot-cli/issues/4305)).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-02

---

## 1. Today's Highlights

The Kimi Code CLI community is focused on robustness fixes this week, with four pull requests addressing real-world regressions in shell handling, tool-call JSON parsing, string replacement counting, and Web UI session switching. A long-standing feature request for a persistent **Memory System** resurfaced with renewed attention, while a Web UI infinite-spinner bug in version 1.48.0 is drawing early community interest.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| #1283 | **Feature Request: Memory System — Persistent context across sessions** | A cross-session memory layer would let Kimi retain project patterns, preferences, and AI-managed notes without manual re-prompting — widely seen as essential for CLI maturity. | 11 comments since Feb; updated today. | [Issue #1283](https://github.com/MoonshotAI/kimi-cli/issues/1283) |
| #2526 | **StrReplaceFile reports too few total replacements for chained edits** | Chained file edits silently misreport success counts, misleading users about how many substitutions actually applied. | Open since Jul 21; 1 comment. | [Issue #2526](https://github.com/MoonshotAI/kimi-cli/issues/2526) |
| #2576 | **docs: document OmniRoute OpenAI-compatible provider setup** | OmniRoute users hit configuration walls (base URL, model declaration, env vars) that the docs don't currently cover. | Open since Aug 1; 0 comments. | [Issue #2576](https://github.com/MoonshotAI/kimi-cli/issues/2576) |
| #2574 | **Kimi Code Stuck on "Processing" and Doesn't Respond** | After a Unity MCP setup session, the agent hangs indefinitely — a regression that blocks real workflow use. | Open since Aug 1; 0 comments. | [Issue #2574](https://github.com/MoonshotAI/kimi-cli/issues/2574) |
| #2573 | **Bug: Web UI "Connecting to session…" infinite spinner when switching sessions** | The Web UI (technical preview) stalls on session switching in v1.48.0 on macOS arm64/Chrome — a UX blocker for the web interface. | Open since Aug 1; 0 comments. | [Issue #2573](https://github.com/MoonshotAI/kimi-cli/issues/2573) |

---

## 4. Key PR Progress

| # | PR | Description |
|---|-----|-------------|
| #2577 | **fix(web,vis): do not crash printing the startup banner on legacy console codecs** | Fixes a crash on GBK consoles (e.g. Chinese Windows) where the `➜` unicode character in `print_banner` cannot be encoded. Resolves #2532. | [PR #2577](https://github.com/MoonshotAI/kimi-cli/pull/2577) |
| #2572 | **fix(kosong): recursively unwrap double-encoded JSON in tool-call arguments** | Tool calls with array/object params (SetTodoList, ExitPlanMode, StrReplaceFile) fail with Pydantic errors when providers double-encode nested values. This PR recursively unwraps them. | [PR #2572](https://github.com/MoonshotAI/kimi-cli/pull/2572) |
| #2554 | **fix(tools): count StrReplaceFile replacements against running content** | The success message for `StrReplaceFile` previously counted replacements against the original file, not the progressively edited content — causing misleading output. A self-contained correctness fix. | [PR #2554](https://github.com/MoonshotAI/kimi-cli/pull/2554) |
| #2530 | **fix(shell): stop blocking until timeout when a detached child holds the pipes** | `_run_shell_command` waited for stdout/stderr EOF before checking exit code, causing hangs when a detached child (e.g. `some_daemon & echo done`) kept pipes open. Resolves #2468. | [PR #2530](https://github.com/MoonshotAI/kimi-cli/pull/2530) |
| #2575 | **fix(hooks): fire PostToolUse hooks through fire_and_forget_trigger** | `PostToolUse` and `PostToolUseFailure` hooks were launched with bare `asyncio.create_task(...)` and dropped, causing pending hook tasks to be silently GC'd by asyncio's `WeakSet`. | [PR #2575](https://github.com/MoonshotAI/kimi-cli/pull/2575) |

---

## 5. Feature Request Trends

The dominant theme across issues is **session-level persistence and reliability**:

- **Memory System (#1283)** — Users want Kimi to remember project context, patterns, and preferences across CLI sessions, both auto-managed and user-defined.
- **Provider documentation (#2576)** — Demand for clearer setup guides for third-party OpenAI-compatible gateways (OmniRoute) signals growing interest in provider flexibility.
- **Web UI stability (#2573)** — As the technical preview matures, users are hitting session-management bugs that need polish before wider adoption.

---

## 6. Developer Pain Points

1. **Tool-call argument encoding failures** — Double-encoded JSON from certain providers breaks Pydantic validation on array/object params. ([#2572](https://github.com/MoonshotAI/kimi-cli/pull/2572))
2. **Shell command hanging on detached children** — Foreground shell mode blocks indefinitely when a background process holds pipes open. ([#2530](https://github.com/MoonshotAI/kimi-cli/pull/2530), [#2468](https://github.com/MoonshotAI/kimi-cli/issues/2468))
3. **Misleading StrReplaceFile output** — Replacement counts are reported against original content, not running state, causing confusion after chained edits. ([#2526](https://github.com/MoonshotAI/kimi-cli/issues/2526), [#2554](https://github.com/MoonshotAI/kimi-cli/pull/2554))
4. **Async hook tasks being GC'd** — Bare `asyncio.create_task` calls for PostToolUse hooks result in silent task loss. ([#2575](https://github.com/MoonshotAI/kimi-cli/pull/2575), [#2564](https://github.com/MoonshotAI/kimi-cli/issues/2564))
5. **Windows GBK console crashes** — Startup banner rendering crashes on legacy Chinese Windows consoles due to unhandled unicode characters. ([#2577](https://github.com/MoonshotAI/kimi-cli/pull/2577), [#2532](https://github.com/MoonshotAI/kimi-cli/issues/2532))

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-02

## 1. Today's Highlights

OpenCode v1.18.11 landed with targeted bugfixes for MCP SSE reconnect loops, interleaved reasoning-field providers, and Desktop external-link handling. Community attention is heavily focused on session reliability — subagent freezes, large-session renderer hangs, and thinking-block state loss across multi-turn Anthropic conversations remain the top pain points.

## 2. Releases

**v1.18.11** — Core bugfixes: stops MCP SSE connections from looping on server errors, fixes provider model configs that use interleaved reasoning fields (`reasoning_text` or custom names), and resolves the Desktop external-link opening issue in the system browser.

## 3. Hot Issues

1. **[Privacy & Data Collection Clarification](https://github.com/anomalyco/opencode/issues/459)** (58 👍, 16 comments) — The most-liked issue in the dataset. Users continue to demand explicit local-first privacy documentation to make informed deployment decisions.

2. **[TUI system theme missing on macOS](https://github.com/anomalyco/opencode/issues/10661)** (4 👍, 21 comments) — The system theme doesn't appear in the `/theme` list. Plugin-dependent and persistent across versions.

3. **[`` tag rendering failure mid-conversation](https://github.com/anomalyco/opencode/issues/9674)** (8 👍, 19 comments) — Long sessions with the Oh My Open Code plugin frequently break tool-call rendering, interrupting auto-progression. High reproducibility makes this a daily annoyance.

4. **[Subagents randomly freeze; TUI stuck on "thinking"](https://github.com/anomalyco/opencode/issues/24342)** (4 👍, 13 comments) — Unpredictable freezes in both main and sub-agents with no error output, while the LLM inference has already terminated. Difficult to reproduce but widely felt.

5. **[`/timestamps` has no visible effect; `/exit` missing from autocomplete](https://github.com/anomalyco/opencode/issues/26625)** (9 comments) — Slash-command persistence works, but the UI toggle has no observable effect and basic commands are absent from autocomplete.

6. **[GitHub Copilot subagent model override ignores billing](https://github.com/anomalyco/opencode/issues/20859)** (1 👍, 7 comments) — All Premium requests route through the orchestrator model (Claude Opus 4.6) despite subagent model config, creating billing surprises.

7. **[Superpowers plugin skills not listing via `/skills`](https://github.com/anomalyco/opencode/issues/21282)** (3 👍, 7 comments) — Plugin loads but skills directory shows only default entries; community feature gap for plugin observability.

8. **[Live token/TPS in footer](https://github.com/anomalyco/opencode/issues/29909)** (7 👍, 7 comments) — Request for a concrete footer-level rolling token and TPS indicator, distinct from prior sidebar/progress requests.

9. **[Thinking block signature lost on model switch](https://github.com/anomalyco/opencode/issues/22813)** (10 👍, 6 comments) — Extended-thinking Anthropic sessions throw `thinking or redacted_thinking blocks cannot be modified` when the model changes mid-turn. High upvote count signals strong demand for a fix.

10. **[Subagent view in TUI](https://github.com/anomalyco/opencode/issues/15223)** (10 👍, 5 comments) — No way to discover spawned subagent sessions from the TUI without knowing the session ID. Consistently top-requested UX gap.

## 4. Key PR Progress

1. **[feat(opencode): add unified marketplace](https://github.com/anomalyco/opencode/pull/40108)** — Proposes a shared package model and runtime for plugins/skills/agents across Desktop, Web, TUI, CLI, and API clients. Directly addresses the plugin observability gap raised in #21282.

2. **[feat(ai): add native Bedrock Mantle support](https://github.com/anomalyco/opencode/pull/40119)** — Adds Amazon Bedrock Mantle Chat and Responses provider entrypoints backed by existing OpenAI protocols, with bearer auth and SigV4 signing.

3. **[feat(plugin): wrap native session HTTP](https://github.com/anomalyco/opencode/pull/40077)** — Replaces the native `session.request` mutation hook with `session.http` around full request/response exchanges, exposing Effect and Promise contracts and preserving streaming.

4. **[fix(core): merge model.request.headers into SDK options](https://github.com/anomalyco/opencode/pull/36620)** — Ensures custom per-model request headers are passed through `prepareOptions()`, closing the gap for providers requiring custom headers (e.g. auth proxies).

5. **[fix(tool): decode webfetch bodies using declared charset via iconv-lite](https://github.com/anomalyco/opencode/pull/35838)** — Fixes silent corruption of non-UTF-8 responses (e.g. `windows-1252`) where `Content-Type` charset was already parsed but ignored.

6. **[fix(tool): enforce grep deny rules by filtering matched files](https://github.com/anomalyco/opencode/pull/35696)** — Grep was passing the search regex to the permission check instead of file paths, bypassing deny rules entirely. Security-relevant fix.

7. **[fix(todo): retry SQLITE_BUSY/LOCKED on parallel todowrite calls](https://github.com/anomalyco/opencode/pull/40115)** — Parallel subagent `todowrite` calls collide on the same session's todo rows. Adds retry logic around SQLite contention.

8. **[fix(app): prevent Enter from sending/interrupting on empty input](https://github.com/anomalyco/opencode/pull/40110)** — Pressing Enter on an empty prompt could waste work or abort an ongoing task. Now a no-op.

9. **[docs(go): update DeepSeek privacy policy](https://github.com/anomalyco/opencode/pull/40120)** — Documents DeepSeek V4 Flash zero-day retention and monthly ZDR agreement through Aug 31, 2026; updates Go docs and homepage FAQ across locales.

10. **[fix(tui): Old messages disappearing during long sessions](https://github.com/anomalyco/opencode/pull/26861)** — Implements lazy-scroll loading: fetching older messages in chunks of 50 when the user scrolls within 5px of the top, addressing the long-session memory and rendering pressure described in #28844.

## 5. Feature Request Trends

- **Plugin & marketplace tooling** — The unified marketplace PR and multiple plugin-related issues (#21282, #30489) signal demand for a discoverable, cross-platform plugin ecosystem with a sidebar session list and skill registry.
- **Subagent UX & observability** — Requests for a TUI subagent view (#15223), parallel todo-write reliability (#40115), and billing transparency (#20859) show the community wants subagents to be first-class citizens, not hidden processes.
- **Session reliability at scale** — Large-session rendering hangs (#28844), thinking-block signature loss (#22813), and timestamp drift causing permanent unresponsiveness (#26159) all point to a push for more robust session state management and rendering virtualization.
- **Provider flexibility** — Bedrock Mantle (#40119), RFC 8628 OAuth (#34785), and custom-header support (#36620) reflect a trend toward broader provider coverage and finer-grained auth control.
- **Real-time feedback in the TUI** — Live token/TPS counters in the footer (#29909) and collapsible provider groups (#15026) indicate users want more operational visibility and a cleaner model picker.

## 6. Developer Pain Points

- **Session freezes and hangs** — The highest-friction category: random subagent freezes (#24342), large-session renderer crashes (#28844), and timestamp-drift lockups (#26159) all produce unresponsive UIs with no clear recovery path.
- **Reasoning / extended-thinking fragility** — Interleaved reasoning fields (#1.18.11 fix) and thinking-block signature loss on model switches (#22813) show that multi-turn Anthropic sessions are error-prone when state isn't preserved correctly.
- **Plugin observability gap** — Plugins load but their capabilities (skills, tools) aren't visible in the TUI (#21282), and MCP SSE connections can loop indefinitely on server errors (#1.18.11 fix), making debugging difficult.
- **Provider billing surprises** — GitHub Copilot subagent model configs are silently ignored in billing (#20859), and GPT-5.4 reasoning-effort tool incompatibilities surface at request time (#29545).
- **SQLite contention under parallelism** — Concurrent subagent writes to the todo store collide (#40115), and grep deny rules were bypassed due to a permission-check logic error (#35696), both indicating that concurrency primitives need tightening as the subagent workflow matures.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑08‑02

## 1. Today's Highlights
The Pi team addressed several persistent pain points: auto‑compaction now triggers reliably after context overflow, the Anthropic‑messages path will send `x‑client‑request‑id` for session affinity, and a new durability barrier prevents session loss during early provider calls. Community momentum is also building around bounded model‑catalog refreshes, which eliminate prolonged hangs when `pi.dev` is unreachable.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
1. **Auto‑compaction fails after context exceeds 100%** (#6879) – Compaction only triggers after an API rejection, leaving sessions in an unstable state. *7 👍, 9 comments.* [Link](https://github.com/earendil-works/pi/issues/6879)
2. **Anthropic path missing `x‑client‑request‑id`** (#7161) – Breaks gateway session affinity; a fix is already proposed. *8 comments.* [Link](https://github.com/earendil-works/pi/issues/7161)
3. **Compaction sometimes leaves Pi unable to continue** (#7020) – Long‑running “coordinator” sessions hit compaction warts that stall the agent. *2 👍, 7 comments.* [Link](https://github.com/earendil-works/pi/issues/7020)
4. **TUI copy‑paste introduces extra whitespace** (#5931) – Wrapped lines are copied with spurious spaces/breaks, degrading pasted output. *7 comments.* [Link](https://github.com/earendil-works/pi/issues/5931)
5. **Bengali text causes visual duplication on Space** (#7402) – A width‑overcounting bug desynchronizes the differential renderer. *6 comments.* [Link](https://github.com/earendil-works/pi/issues/7402)
6. **Normalize OpenAI tool schemas for `required`** (#7010) – Non‑normalized object schemas break some OpenAI‑compatible providers. *1 👍, 6 comments.* [Link](https://github.com/earendil-works/pi/issues/7010)
7. **Fireworks requests time out instantly** (#7315) – Transient timeouts produce empty responses and multiple auto‑retries. *4 comments.* [Link](https://github.com/earendil-works/pi/issues/7315)
8. **Core‑tool bugs: wrong byte count, false limit warning, surrogate split** (#7121) – Three independent bugs in `write.ts`, `find`, and `truncateLine` were fixed. *4 comments.* [Link](https://github.com/earendil-works/pi/issues/7121)
9. **Compaction summary truncated mid‑word** (#7048) – The summarizer does not check `stopReason === "length"`, persisting incomplete summaries. *4 comments.* [Link](https://github.com/earendil-works/pi/issues/7048)
10. **`pi update --extensions` blocked by npm 11.16.0** (#6600) – npm now disables script execution by default, breaking the extension‑update flow. *4 comments.* [Link](https://github.com/earendil-works/pi/issues/6600)

## 4. Key PR Progress
1. **#7471 – Retry transient provider errors in Google adapters** (Closed) – Adds retry logic for 429/5xx errors in `google‑vertex` and `google‑generative‑ai`, preventing immediate session failures. [Link](https://github.com/earendil-works/pi/pull/7471)
2. **#7468 – Accept Claude Code skill frontmatter** (Closed) – Makes both skill loaders compatible with Claude Code’s `SKILL.md` frontmatter, expanding skill portability. [Link](https://github.com/earendil-works/pi/pull/7468)
3. **#7467 – Add MiniMax video generation** (Closed) – Introduces a video‑generation API registry and providers for MiniMax global/CN endpoints. [Link](https://github.com/earendil-works/pi/pull/7467)
4. **#7466 – Opt‑in pre‑dispatch durability barrier** (Closed) – Persists session state before the first provider call, enabling at‑most‑once semantics for embedders. [Link](https://github.com/earendil-works/pi/pull/7466)
5. **#7463 – Fix `SessionManager._persist` ENOENT crash** (Closed) – Ensures the session directory exists before writing, avoiding crashes after workspace resets. [Link](https://github.com/earendil-works/pi/pull/7463)
6. **#7462 – Add `PI_JITI_CACHE` env var** (Closed) – Allows packagers (e.g., Nix) to point the JIT cache to a persistent directory. [Link](https://github.com/earendil-works/pi/pull/7462)
7. **#7456 – Support short‑lived OAuth tokens** (Closed) – Refreshes credentials only when less than one minute remains, preventing per‑request token refresh. [Link](https://github.com/earendil-works/pi/pull/7456)
8. **#7440 – Switchable terminal renderers** (Open) – Enables runtime switching between terminal renderers while preserving state. [Link](https://github.com/earendil-works/pi/pull/7440)
9. **#7451 – Bound model catalog refreshes** (Open) – Adds timeouts/cancellation to catalog requests, fixing hangs when `pi.dev` is unreachable. [Link](https://github.com/earendil-works/pi/pull/7451)
10. **#7441 – Tolerate missing `finish_reason` in OpenAI streams** (Closed) – Prevents session kills on gateways that omit the terminal `finish_reason` chunk. [Link](https://github.com/earendil-works/pi/pull/7441)

## 5. Feature Request Trends
- **Compaction reliability** – Multiple issues (#6879, #7020, #7048) highlight the need for more robust context management and summary generation.
- **Provider‑level session affinity** – The missing `x‑client‑request‑id` on the Anthropic path (#7161) shows demand for consistent request‑ID propagation across all providers.
- **Terminal rendering fidelity** – Copy‑paste whitespace (#5931), wide‑character duplication (#7402), and input‑lag scaling (#7385) indicate ongoing effort to perfect the TUI experience.
- **Graceful degradation on network issues** – Timeouts on Fireworks (#7315), catalog‑refresh hangs (#7418, #7443), and OAuth‑token bloat (#7457) reflect a need for better resilience in distributed environments.
- **Extensibility & skill compatibility** – Support for Claude Code skill frontmatter (#7468) and MiniMax video generation (#7467) points to a growing ecosystem of third‑party integrations.

## 6. Developer Pain Points
- **Session‑state loss** – Crashes between session persistence and first provider response (#7466) cause lost work and billing ambiguity.
- **Compaction edge cases** – Summaries truncated mid‑word, post‑compaction stalls, and failure to trigger after 100% context overflow (#6879, #7020, #7048) degrade long‑running sessions.
- **Terminal‑rendering desync** – Width‑calculation bugs for non‑Latin scripts (#7402) and cache bypasses causing keystroke lag (#7385) hurt usability.
- **Provider‑compatibility gaps** – Non‑normalized OpenAI tool schemas (#7010), missing `finish_reason` handling (#7441), and absent retry logic for Google adapters (#7471) create unpredictable failures.
- **Tool‑usage bloat** – Subagent transcripts unnecessarily persisted in parent sessions (#7452) inflates session JSONL files.
- **Infrastructure frictions** – npm script blocking (#6600), terminal‑title pollution (#7469), and scrollback destruction on startup (#7352) are recurring annoyances for power users.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026‑08‑02

## 1. Today's Highlights
Qwen Code released **v0.21.3** and a nightly build, bringing a significantly enhanced `/review` command with test‑plan validation, measured failure attribution, and new verification lenses. The community continues to push for better prompt‑cache reuse, extensibility, and daemon resource management, while several UI/UX fixes land to address long‑standing TUI and completion‑picker friction.

## 2. Releases
- **v0.21.3** – Stable release with an enhanced `/review` command that now validates test plans, attributes failures, and offers new verification lenses for deeper code‑change analysis.
- **v0.21.3‑nightly.20260802.184365390** – Nightly build includes documentation for the TUI keyboard‑shortcut reference and a fix to unblock history pagination on certain backends.
- **v0.21.2‑nightly.20260801.bc382c3ff** – Nightly build adds session source to lifecycle‑hook payloads and improves review‑cache identity checks.

> **Highlight:** The `/review` enhancements are the most visible change in this cycle, directly impacting code‑review workflows.  
> 🔗 [QwenLM/qwen‑code releases](https://github.com/QwenLM/qwen-code/releases)

## 3. Hot Issues
| Issue | Title | Why It Matters |
|-------|-------|----------------|
| [#176](https://github.com/QwenLM/qwen-code/issues/176) | Tool calling does not work with local model qwen3‑30b‑a3b | High‑engagement bug (23 comments, 7 👍) affecting local‑model users; no error output makes diagnosis difficult. |
| [#7585](https://github.com/QwenLM/qwen-code/issues/7585) | Proposal: Add a direct external context provider profile | Proposes a private monorepo integration for shared repository context—addresses enterprise‑deployment needs. |
| [#8051](https://github.com/QwenLM/qwen-code/issues/8051) | Track and deliver bounded multi‑workspace daemon resource usage | Daemon currently lacks byte‑level memory bounds; critical for production `qwen serve` stability. |
| [#8286](https://github.com/QwenLM/qwen-code/issues/8286) | Support explicitly trusted private ASR base URLs | Enables managed deployments to use internal voice endpoints over HTTP in isolated networks. |
| [#8131](https://github.com/QwenLM/qwen-code/issues/8131) | Statusline text cannot be selected in Virtualized History mode | UI bug that blocks copying session metadata; affects developers using long sessions. |
| [#8279](https://github.com/QwenLM/qwen-code/issues/8279) | Could chat compression reuse the main prompt‑cache prefix via a fork? | Design discussion on caching efficiency; directly impacts latency and token cost for long conversations. |
| [#2635](https://github.com/QwenLM/qwen-code/issues/2635) | Support installing extensions from qwen‑code repository | Feature request to simplify extension distribution and management from the main repo. |
| [#8330](https://github.com/QwenLM/qwen-code/issues/8330) | `@` completion tab switching is inaccessible in Warp | Terminal‑level shortcut conflict makes the completion picker unusable in popular terminals. |
| [#8284](https://github.com/QwenLM/qwen-code/issues/8284) | Expose prompt cache hit rate as telemetry | Adds a first‑class metric for monitoring cache effectiveness alongside existing token‑count signals. |
| [#4777](https://github.com/QwenLM/qwen-code/issues/4777) | Deferred‑tools listing busts prompt cache on every MCP discovery | Performance bug where deferred tool lists invalidate the cached system prompt, increasing latency. |

## 4. Key PR Progress
| PR | Title | Description |
|----|-------|-------------|
| [#8339](https://github.com/QwenLM/qwen-code/pull/8339) | `fix(core): reuse prompt cache during chat compression` | Allows chat compression to reuse the main conversation’s prompt‑cache prefix when the provider supports Anthropic‑/DashScope‑style caching, reducing redundant token usage. |
| [#8343](https://github.com/QwenLM/qwen-code/pull/8343) | `ci: auto‑update ECS runners on stable publish and harden update job` | Ensures self‑hosted ECS runners stay current with the released CLI version and prevents silent downgrades. |
| [#8132](https://github.com/QwenLM/qwen-code/pull/8132) | `feat(desktop): package Web Shell as a release‑ready desktop app` | Turns the Tauri proof‑of‑concept into a production desktop shell that owns native lifecycle around the shared Web Shell. |
| [#8354](https://github.com/QwenLM/qwen-code/pull/8354) | `fix(sdk-java): accept ERROR terminal in teardown E2E to fix flaky race` | Makes the Java daemon E2E test deterministic by allowing an `ERROR` terminal state during teardown, eliminating a race condition. |
| [#8348](https://github.com/QwenLM/qwen-code/pull/8348) | `docs: document compaction and image model selection` | Documents auxiliary model selectors for chat compression and built‑in image generation, including defaults and fallback behavior. |
| [#8342](https://github.com/QwenLM/qwen-code/pull/8342) | `fix(cli): allow pasting sensitive extension settings` | Enables multi‑character paste into sensitive‑setting prompts while masking characters, fixing a Windows‑specific UX gap. |
| [#8180](https://github.com/QwenLM/qwen-code/pull/8180) | `feat(telemetry): Track tool execution outcomes` | Adds an `executionStatus` field that records whether `invocation.execute()` was entered and succeeded, complementing the existing terminal status. |
| [#8331](https://github.com/QwenLM/qwen-code/pull/8331) | `fix(cli): enable ToolSearch by default for DeepSeek` | Activates ToolSearch for DeepSeek models while preserving opt‑out and the 10% deferred‑tool preload threshold. |
| [#8353](https://github.com/QwenLM/qwen-code/pull/8353) | `fix(cli): let ESC cancel ongoing work before popping queued messages` | Fixes ESC handling so that when the agent is streaming, ESC cancels the request instead of only popping the input queue. |
| [#8349](https://github.com/QwenLM/qwen-code/pull/8349) | `feat(review): drive — readiness polled, completion proven, cleanup guaranteed` | Introduces `qwen review drive` to start a task, wait until it is truly up, drive it, and capture factual results—replacing guess‑based sleeps. |

## 5. Feature Request Trends
Analysis of recent issues reveals several recurring direction themes:

1. **External Context & Integration** – Requests for direct external context providers (#7585) and repository‑based extension installation (#2635) point to a growing need for tightly integrated, workspace‑aware workflows.
2. **Daemon & Resource Management** – Bounded multi‑workspace daemon resource usage (#8051) and configurable sub‑session concurrency (#8341) show demand for production‑grade resource controls.
3. **Voice & ASR Customization** – Trusted private ASR base URLs (#8286) and general voice‑input support (#3110) indicate interest in extending voice capabilities to private deployments.
4. **Prompt‑Cache Optimization** – Multiple discussions (#8279, #8284, #4777, #8277) focus on reusing cache prefixes, exposing hit‑rate telemetry, and avoiding cache‑busting patterns.
5. **Observability & Telemetry** – Tool‑execution outcome tracking (#8180) and prompt‑cache hit‑rate metrics (#8284) reflect a push for richer diagnostic data.
6. **UI

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-02

## 1. Today's Highlights

The past 24 hours have been dominated by two urgent reliability concerns: **credential scoping bugs** (issues #5045 and #5047, plus PR #5075 fixing both) and a **release-blocker in v0.9.4** where switching providers can leave stale default models (issue #5034). On the PR front, the team shipped a batch of eight user-facing fixes (PR #5063), advanced compaction semantics with a deterministic continuation contract (PR #5064), and integrated community contributions for Windows devcontainer support (PR #5078) and workspace-scoped task listing (PR #5079).

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

**#5045 — Unify API key / secret storage: credentials must be user-global, not repo-scoped**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/5045)
Operator dogfood revealed that API keys entered during provider setup persist only within the current repository. This is a friction point for developers working across multiple projects and is being addressed in PR #5075.

**#5047 — API keys silently persist only in the working repo instead of durable global secret storage**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/5047)
A close relative of #5045: keys are sometimes saved to `<cwd>/.codewhale/config.toml` in plaintext, leaking credentials across repo boundaries. Seen as a security-adjacent reliability bug.

**#5034 — [v0.9.4 release-blocker] Switching providers can retain an unrelated default model**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/5034)
When a user switches to OpenAI, the default model may remain `gpt-5.5` inherited from a different route rather than the intended provider default. Labeled a release-blocker for v0.9.4.

**#4785 — Dead-code sweep: 464 `#[allow(dead_code)]` attributes are hiding drift**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/4785)
The maintainer flagged that 464 `#[allow(dead_code)]` attributes across 143 files structurally prevent the compiler from reporting dead-code drift. A long-overdue housekeeping item for the Rust codebase.

**#4683 — Wrong DeepSeek completions URL (flaky after long sessions)**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/4683)
Users report intermittent `Network error` failures against `api.deepseek.com/v1/chat/completions` after extended use. Described as flaky and recurring, suggesting a connection pool or URL-encoding issue.

**#4085 — Cannot read/write files under ~/Library/CloudStorage/Dropbox/ (macOS File Provider)**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/4085)
CodeWhale fails on macOS 12+ Dropbox paths due to the File Provider framework. The binary is ad-hoc signed with zero entitlements, confirming this is not a sandbox issue but a path-resolution gap.

**#4684 — `danger-full-access` does not disable tools-layer workspace boundary check**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/4684)
Setting `sandbox_mode = "danger-full-access"` disables the OS-level sandbox but the tools layer (`read_file`, `grep_files`, etc.) still enforces its own workspace boundary, breaking global skill access.

**#4716 — TUI exits immediately on launch in a fresh terminal [stop-ship]**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/4716)
On macOS, `codew` returns immediately with "[Process completed]" instead of entering the TUI. Author is the maintainer; tagged `stop-ship`, indicating high severity.

**#5057 — Retire stale lanes: dirty localization worktree and ten 0868-era branches**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/5057)
One dirty unmerged localization worktree and ten stale branches from July 2026 remain on disk. The maintainer proposes harvesting useful locale rollovers, archiving the rest, and closing intent issues.

**#5056 — Test reliability: flaky verifier background tests, workspace-sensitive fixtures, 12 ignored tests**
[GitHub](https://github.com/Hmbown/CodeWhale/issues/5056)
Two verifier tests still flake under parallel full-suite runs, and workspace-sensitive subagent tests have fixture issues. Twelve `#[ignore]` tests remain untriaged.

## 4. Key PR Progress

**PR #5075 — Make credential persistence path-safe**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5075)
Rejects relative `CODEWHALE_HOME` / `CODEWHALE_CONFIG_PATH` before they become repo-local global state; routes TUI config reads/writes through a shared fallible path; refuses automatic plaintext storage. Directly fixes #5045 and #5047.

**PR #5063 — Issue burn-down batch: eight user-facing fixes**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5063)
Seven commits covering Anthropic wire strictness, sandbox, workflow, config scoping, session layer, input handling, and TUI bugs. Each fix includes regression tests; root causes were adversarially verified before implementation.

**PR #5064 — Compaction: deterministic continuation contract**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5064)
Adds a runtime-extracted continuation contract to compaction summaries, preserving bounded working intent, decisions, verification evidence, and in-flight tool calls independently of the summarizer model.

**PR #5079 — Scope task listing by workspace (community integration)**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5079)
Integrates PR #4985 onto main, adding an optional `workspace` filter to `GET /v1/tasks` and including workspace path in `TaskSummary` so GUI clients can scope correctly.

**PR #5078 — Devcontainer: support Windows development (community integration)**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5078)
Integrates PR #4990 onto main. Uses a dedicated dev image with Rust toolchain and replaces host HOME bind mount with named volumes to avoid invalid Windows HOME expansion.

**PR #5068 — Centralize DeepSeek Pro effort mapping in a dated table**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5068)
Moves effort mapping into `client/deepseek_effort.rs` with a 2026-07-31 annotation. Both Chat and Responses paths now consume the same table.

**PR #5069 — Model capability badges in Fleet setup and roster**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5069)
Adds provider-aware resolver for concise, provenance-labelled capability badges. Merged Models.dev offerings take priority; unknown models render no badges and never block selection.

**PR #5077 — Progressively disclose fresh context in prompts**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5077)
Caps the ambient skills block at 2,400 characters while keeping every enabled skill discoverable via `load_skill name="list"`. Moves AGENTS.md/CLAUDE.md authority to eager discovery.

**PR #5067 — Operate goals run to completion gate; continuation cap is configurable**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5067>
Removes the hardcoded ten-continuation terminal stop. Goals now run until verified completion, block, or token/time budget exhaustion. Adds `[goal] max_continuations` with a default of 100.

**PR #5076 — Remove dormant Landlock prototype**
[GitHub](https://github.com/Hmbown/CodeWhale/pull/5076)
Deletes the 361-line Landlock sandbox prototype with no production callers. Bubblewrap selection/denial behavior remains unchanged; docs are updated accordingly.

## 5. Feature Request Trends

- **Credential & config scoping**: Multiple issues (#5045, #5047, #4684) converge on the need for proper per-user global secret storage that is isolated from repository state and honors sandbox boundaries.
- **Cross-platform parity**: Windows devcontainer support (#5078) and the macOS File Provider Dropbox bug (#4085) signal sustained demand for first-class multi-platform reliability.
- **Multi-provider experience**: The provider-switching bug (#5034), dead-code sweep (#4785), and capability badges (#5069) all reflect a community investing in a mature multi-provider routing experience.
- **Localization maturity**: Closed PRs for Korean, Spanish, Brazilian Portuguese, Hindi, Ukrainian, French, German, and Catalan show an aggressive push toward global locale coverage.
- **Runtime control & observability**: Features like turn-scoped tool restrictions (#5051), notification quiet mode (#5066), and workspace-scoped task listing (#5079) point toward finer-grained operator control.

## 6. Developer Pain Points

- **Flaky test suite**: The verifier background tests continue to under parallelism, and 12 `#[ignore]` tests remain untriaged (#5056). This slows CI confidence and local iteration.
- **Credential leakage into repo config**: Plaintext API keys saved under `<cwd>/.codewhale/config.toml` instead of a global store is a recurring and security-sensitive frustration (#5045, #5047).
- **Sandbox bypass is incomplete**: `danger-full-access` disables the OS sandbox but not the tools-layer workspace check (#4684), creating a false sense of permission and breaking global skill access.
- **macOS launch regressions**: The `stop-ship` issue where `codew` exits immediately in a fresh terminal (#4716) points to fragile terminal-environment assumptions.
- **Code health debt**: 464 `#[allow(dead_code)]` attributes (#4785) and 3,000+ line god files in `runtime_api.rs`, `shell.rs`, `mcp.rs`, and `web_search.rs` indicate accumulated architectural complexity that slows onboarding and safe refactoring.
- **Stale branch/worktree clutter**: Ten orphaned branches from July and a dirty localization worktree (#5057) are creating noise in the repository hygiene.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*