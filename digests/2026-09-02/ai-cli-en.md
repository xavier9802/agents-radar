# AI CLI Tools Community Digest 2026-09-02

> Generated: 2026-09-02 04:01 UTC | Tools covered: 10

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
**Date: 2026-09-02**

---

## 1. Ecosystem Overview

The AI CLI tool landscape in early September 2026 is characterized by rapid iteration punctuated by growing pains around agent reliability, memory management, and cross-platform consistency. All eight major tools are actively shipping releases and addressing community-reported bugs, but the dominant concerns span a narrow set of systemic challenges: session stability under sustained load, transparent billing/model substitution, MCP protocol maturity, and platform-specific UX regressions. The gap between early-adopter enthusiasm and production readiness is most visible in memory leaks (Claude Code on macOS, Copilot CLI via libuv handle leaks), agent lifecycle bugs (Gemini CLI hangs, Pi tool-loop deadlocks), and inconsistent path/workspace management (OpenCode's stale-project issue, Qwen's permissions regression).

---

## 2. Activity Comparison

| Tool | Hot Issues | PRs Updated | Releases (24h) | Notable Release |
|---|---|---|---|---|
| **Claude Code** | 11 | 2 | v2.1.258, v2.1.257 | Fable 5.1 default, macOS 12 fix |
| **Gemini CLI** | 10 | 10 | v0.59.0-preview.0, nightly | NTFS hardening, OAuth RFC 9207 |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.83-1 | Session sorting, enterprise sign-in |
| **Kimi Code CLI** | 3 (all closed) | 4 | v1.50.0 | Deprecation-aware migration flow |
| **OpenCode** | 10 | 10 | v1.18.26 | Claude 5 session fixes, Bedrock reasoning |
| **Pi** | 10 | 9 | None | — |
| **Qwen Code** | 10 | 10 | cua-driver-rs v0.20.3 | ACP NDJSON backpressure fix |
| **DeepSeek TUI** | 10 | 10 | 0.9.12 (rollout) | Native ChatGPT PKCE, settings consolidation |

> **Note:** OpenAI Codex digest generation failed; no data available.

**Key observations:** Gemini CLI, OpenCode, Qwen Code, and DeepSeek TUI all show high PR velocity (10 each), indicating active contributor ecosystems. Copilot CLI and Kimi Code CLI show lower PR output but maintain release cadence. Claude Code's low PR count (2) contrasts with its high issue volume (11) and heavy community engagement (842 comments on a single billing issue).

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Needs |
|---|---|---|
| **Agent reliability & lifecycle management** | Gemini CLI, Pi, OpenCode, Claude Code | Subagent recovery, deadlock prevention, graceful cancellation, false-success reporting |
| **Memory & session stability** | Claude Code, Copilot CLI, OpenCode, Qwen Code | OOM prevention, kernel zone leak fixes, session resume reliability, context window management |
| **MCP protocol maturity** | Copilot CLI, Gemini CLI, DeepSeek TUI | OAuth refresh flows, RFC 9207 issuer validation, legacy `initialize` handling, bounded startup budgets |
| **XDG/config hygiene** | Kimi Code CLI, Pi | Adoption of `$XDG_CONFIG_HOME` / `$XDG_DATA_HOME` for Linux desktop compliance |
| **Cost transparency & billing control** | Claude Code, OpenCode | Clear session limit accounting, model substitution visibility, real-date limits vs. rolling boosts |
| **Tool surface customization** | Qwen Code, OpenCode, Gemini CLI | Opt-in tools, per-MCP-server trust pinning, permission granularity |
| **Provider/model catalog flexibility** | Pi, DeepSeek TUI, Qwen Code | Custom endpoint support, BYOK consistency, multi-provider routing, fleet model prioritization |
| **TUI/UX polish** | OpenCode, Qwen Code, DeepSeek TUI, Pi | Timeline controls, scroll behavior, image rendering, settings consolidation |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | Gemini CLI | Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi Code CLI |
|---|---|---|---|---|---|---|---|---|
| **Primary focus** | General-purpose coding agent | Multi-agent workflows with subagents | GitHub-integrated workflow | Agentic coding with ACP | Multi-provider coding agent | Self-hosted/local-first | Shell-native TUI | Migration-focused (kimi-cli → Kimi Code) |
| **Target user** | Broad developer base, Max plan subscribers | Developers wanting subagent autonomy | GitHub Enterprise users | Open-source/ACP adopters | Multi-provider power users | Self-hosted model operators | Terminal-centric users | Kimi ecosystem migrants |
| **Technical approach** | Claude-native, Fable integration | Subagent harness, AST-aware tools | GitHub-native, MCP-first | ACP protocol, Bedrock support | Extensible provider layer | CUA driver, self-hosted models | Shell-wave runtime, native PKCE | Python → Rust transition |
| **Key differentiator** | 1M context Fable 5.1, governance plugins | Zero-dependency sandboxing proposal | Vim mode (75 👍), enterprise sign-in pinning | Stale-path bug is the defining community pain | Fresh-context extension API, headless RPC | Bubblewrap sandbox, Telegram bot mode | Truthful Tideline chrome, diff word highlighting | Deprecation-aware migration path |

---

## 5. Community Momentum & Maturity

**Most active communities (by issue engagement):**
1. **Claude Code** — Highest single-issue engagement (842 comments on session limits), indicating a large, invested user base facing serious billing transparency concerns.
2. **Gemini CLI** — Strong contributor activity (10 PRs merged) with balanced open/closed issue ratio, suggesting a healthy feedback loop.
3. **OpenCode** — 10 PRs merged and a persistent cross-platform bug (stale paths) driving 20+ linked issues, indicating deep user investment.

**Rapidly iterating (by PR velocity):**
- **DeepSeek TUI** — 10 PRs in 24h, aggressive feature delivery (settings consolidation, PKCE sign-in, goal rehydration).
- **Qwen Code** — 10 PRs including critical backpressure fixes and release pipeline improvements.
- **Gemini CLI** — Consistent security-hardening PRs (NTFS, OAuth, extension consent) alongside UX fixes.

**Maturing but challenged:**
- **Claude Code** — Large user base but low PR velocity (2) and systemic issues (kernel leaks, billing opacity) suggest scaling challenges outpacing engineering capacity.
- **Pi** — No release in 24h but 9 PRs merged and strong community feature requests indicate steady iteration without frequent ship cycles.
- **Copilot CLI** — Zero PRs in 24h alongside three separate OOM regressions signals a tool struggling with memory management at scale.

---

## 6. Trend Signals

| Signal | Evidence | Implication for Developers |
|---|---|---|
| **Agent reliability is the bottleneck** | Gemini CLI subagent false-success (#22323), Pi tool-loop deadlocks (#4338, #8973), Claude Code session limit anomalies (#38335) | Production deployments of AI agents require explicit guardrails; no tool has fully solved autonomous reliability yet. |
| **Memory leaks are ecosystem-wide** | Claude Code macOS kernel zone leaks (#66020), Copilot CLI libuv handle leaks (#4686), OpenCode PDF encoding OOM (#42263) | Long-running sessions are inherently risky; developers should implement external health checks and session rotation. |
| **MCP is still finding its protocol footing** | Copilot CLI legacy `initialize` issues (#4525), Gemini CLI RFC 9207 enforcement (#29117), OpenCode per-server fingerprint pinning (#40125) | MCP server implementations should assume varying client behavior; defensive coding is essential. |
| **BYOK/custom providers are fragile** | Copilot CLI wrong model IDs (#4680), Pi plain-HTTP proxy hangs (#8134), Qwen Code streaming timeouts (#5975) | Bring-your-own-key workflows need thorough validation; tools are shipping regressions in this area. |
| **Cross-platform parity is a persistent gap** | Windows flag parsing (DeepSeek #4564), Wayland failures (Gemini #21983), case-sensitivity (OpenCode #44538), macOS 12 support (Claude #2.1.258) | Multi-platform tooling requires continuous investment; assume platform-specific bugs until proven otherwise. |
| **Community demands for transparency** | Claude Code billing opacity (842 comments), Kimi YOLO mode black box (#1298), Gemini Auto Memory leak concerns (#26525) | Tools that provide clear cost accounting and execution visibility will build stronger user trust. |
| **Migration/deprecation management matters** | Kimi Code's one-key migration flow (#2630), OpenCode stale-project recovery gaps | Tool ecosystems that guide users through transitions reduce churn and community frustration. |

---

**Bottom line for decision-makers:** The AI CLI tool ecosystem is in a high-velocity growth phase where agent reliability, memory safety, and billing transparency are the top differentiators. Gemini CLI and DeepSeek TUI show the strongest current momentum; Claude Code has the largest community but faces systemic trust issues around billing. For production use, any tool should be evaluated against the three recurring failure modes: session stability under sustained load, clarity of cost/accounting, and graceful degradation when subcomponents fail.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-09-02 · Source: github.com/anthropics/skills**

---

## 1. Top Skills Ranking

| # | PR | Skill | Status | Summary |
|---|-----|-------|--------|---------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator** (fix) | 🔴 Open | Fixes a critical bug where `run_eval.py` reports 0% recall for every skill description, breaking the entire optimization loop. Includes Windows stream/encoding fixes. |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** (new) | 🔴 Open | Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universal pain point in document output. |
| 3 | [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** (new) | 🔴 Open | HPC cluster operations skill covering profile-based SSH, Slurm workflows, partition/memory guidance, and accelerator setup for SCNet clusters. |
| 4 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer** & **skill-security-analyzer** (new) | 🔴 Open | Meta-skills for evaluating skills across 5 dimensions (structure, documentation, examples, security, correctness). Intended for the marketplace. |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** (new) | 🔴 Open | Comprehensive testing skill covering the Testing Trophy model, unit testing (AAA pattern), React component testing with Testing Library, and edge-case strategies. |
| 6 | [#486](https://github.com/anthropics/skills/pull/486) | **ODT** (new) | 🔴 Open | Full OpenDocument Format skill — create, fill, read, and convert .odt/.ods files. Triggers on ODT/ODS/ODF/LibreOffice keywords. |
| 7 | [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow** (new) | 🔴 Open | Broad platform skill covering ITSM, ITOM, ITAM/SAM, FSM, HRSD, CSDM, IntegrationHub, Vulnerability Response, and SecOps. |
| 8 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** (new) | 🔴 Open | Pre-delivery verification skill: mechanical file checks first, then four-dimension reasoning audit in damage-severity priority order. Universal across projects and models. |

---

## 2. Community Demand Trends

Analysis of open Issues reveals the following high-priority directions:

- **🔒 Trust & Security Governance** — The #1 concern: [Issue #492](https://github.com/anthropics/skills/issues/492) (43 comments) reports community skills being distributed under the `anthropic/` namespace, enabling trust-boundary abuse. Community calls for namespace verification or skill provenance.
- **🏢 Enterprise / Org-Wide Sharing** — [Issue #228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) requests built-in org skill sharing instead of manual .skill file distribution via Slack/Teams.
- **🧠 Meta-Skills for Quality & Governance** — [Issue #1385](https://github.com/anthropics/skills/issues/1385) proposes a three-gate reasoning pipeline (calibration → adversarial review → delivery verification); [Issue #412](https://github.com/anthropics/skills/issues/412) requests an agent-governance skill for policy enforcement and audit trails.
- **⚡ Context Window Efficiency** — [Issue #1487](https://github.com/anthropics/skills/issues/1487) flags the `claude-api` skill injecting ~156k tokens in a single call. [Issue #1329](https://github.com/anthropics/skills/issues/1329) proposes a `compact-memory` skill using symbolic notation to reduce agent state overhead.
- **🧪 Evaluation & Reliability Tooling** — [Issue #556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍) and [Issue #1390](https://github.com/anthropics/skills/issues/1390) both report broken evaluation harnesses (`run_eval.py` and `evaluation.py`), indicating strong demand for reliable skill testing tooling.
- **📄 Document Fidelity** — [Issue #12](https://github.com/anthropics/skills/issues/12) (4 comments) highlights docx/OOXML whitespace corruption; [Issue #1175](https://github.com/anthropics/skills/issues/1175) raises SharePoint security concerns for agent-handled documents.

---

## 3. High-Potential Pending Skills

These PRs show active development momentum and community alignment, making them strong candidates for near-term merge:

| PR | Skill | Why It's Promising |
|----|-------|-------------------|
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | Solves the cost-context bottleneck by offloading to free-model workers; aligns with the efficiency trend seen in Issues #1329 and #1487. |
| [#1607](https://github.com/anthropics/skills/pull/1607) | **claude-api** (update) | Simple, high-impact fix retiring stale model IDs; directly addresses Issue #1487's token-injection concern. |
| [#1602](https://github.com/anthropics/skills/pull/1602) | **mcp-builder** (fix) | Resolves serialization and encoding bugs blocking evaluation; paired with Issue #1390 fix demand. |
| [#538](https://github.com/anthropics/skills/pull/538) | **pdf** (fix) | Low-risk case-sensitivity fix with clear reproduction; same author also fixed docx in #541. |
| [#541](https://github.com/anthropics/skills/pull/541) | **docx** (fix) | Prevents document corruption from `w:id` collisions — directly relevant to Issue #12 and #1175. |
| [#1099](https://github.com/anthropics/skills/pull/1099) + [#1050](https://github.com/anthropics/skills/pull/1050) | **skill-creator** (Windows fixes) | Two complementary Windows compatibility fixes; collectively unblock the entire skill-creator pipeline for Windows users. |
| [#210](https://github.com/anthropics/skills/pull/210) | **frontend-design** (refactor) | Improves actionability and coherence; addresses Issue #202's critique that skill-creator reads like documentation rather than operational guidance. |

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is for *reliable evaluation and trust infrastructure*:** broken eval harnesses (#556, #1390), namespace impersonation (#492), and context-window bloat (#1487) are the three issues drawing the most engagement — signaling that as the Skills ecosystem scales, the community prioritizes verification tooling, provenance security, and efficiency over new domain-specific capabilities.

---



# Claude Code Community Digest — 2026-09-02

## 1. Today's Highlights

Claude Code v2.1.258 drops today, fixing a macOS 12 launch regression and a permission-approval crash, while v2.1.257 introduced Claude Fable 5.1 as the new default Fable model with 1M context and new time-format settings. The community is overwhelmingly focused on two issues: Max plan session limits burning abnormally fast (842 comments) and macOS kernel zone memory leaks causing panics in long-running sessions. Meanwhile, several new bugs landed today around fabricated user messages, silent model substitution, and broken remote control.

---

## 2. Releases

### v2.1.258 — 2026-09-02
- Fixed Claude Code failing to launch on macOS 12 (Monterey), a regression from v2.1.255
- Fixed remote/scheduled sessions crashing with `"user messages must have non-empty content"` when a re-sent permission approval could not be applied

### v2.1.257 — 2026-09-02
- Added **Claude Fable 5.1** (`claude-fable-5-1`) as the new default Fable model — 1M context, $10/$50 per Mtok, $0.25/Mtok cache reads
- Added `timeFormat` and `timeZone` settings supporting 12-hour, 24-hour, 24-hour UTC, or strftime patterns for turn-end clock display

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#38335](https://github.com/anthropics/claude-code/issues/38335) | Max plan session limits exhausted abnormally fast since 2026-03-23 | Core billing complaint affecting the largest user tier; session limits drain far faster than expected under CLI usage. | 842 comments · 476 👍 |
| [#80444](https://github.com/anthropics/claude-code/issues/80444) | Windows desktop GPU-process crash via in-app browser tab | Crashes leave the MSIX package unlaunchable until Repair; reproduces across GPU driver versions on Windows 11. | 100 comments · 16 👍 |
| [#79337](https://github.com/anthropics/claude-code/issues/79337) | Fable 5 requires usage credits on Max plan | On the day Fable 5 became standard on Max, Claude Code silently downgraded to Opus 4.8 and blocked Fable 5 with a credits error — a pricing/access regression. | 76 comments · 23 👍 · ✅ Closed |
| [#85891](https://github.com/anthropics/claude-code/issues/85891) | Desktop window always-on-top on Windows 11 | No in-app setting to disable; the window stays above all others. Windows counterpart to a known macOS issue. | 58 comments · 128 👍 |
| [#66020](https://github.com/anthropics/claude-code/issues/66020) | macOS kernel zone leak (`data.kalloc.1024`) | Leak rate scales from 21→1027/sec with agent load; `claude.exe` panics at ~20 GB. Directly impacts session stability on macOS. | 26 comments · 5 👍 |
| [#82941](https://github.com/anthropics/claude-code/issues/82941) | macOS kernel panic: `data.kalloc.1024` zone exhausted | Separate report of the same kernel zone exhaustion, this time from leaked file descriptors/kqueues in long-running sessions. | 3 comments · 0 👍 |
| [#91383](https://github.com/anthropics/claude-code/issues/91383) | Fabricated user messages injected into model context | Messages with literal `"user"` prefix injected without user input — a serious correctness and security concern. Filed today. | 0 comments · 0 👍 |
| [#91386](https://github.com/anthropics/claude-code/issues/91386) | Agent silently ran 10× more expensive model than instructed | Agent made ~280 API calls on `claude-fable-5` while telling the user it was on `claude-haiku-4-5`, resulting in ~$98 vs ~$10 in charges. Filed today. | 0 comments · 0 👍 |
| [#27474](https://github.com/anthropics/claude-code/issues/27474) | `claude --worktree` overwrites `core.hooksPath` | Persistent config mutation in shared git repos is a workflow-breaking bug for teams using worktrees. | 14 comments · 16 👍 |
| [#62659](https://github.com/anthropics/claude-code/issues/62659) | Windows Bash tool orphans survive command kill | No per-command Job Object means spawned processes (`cargo`, `node`, etc.) survive session end as unkillable orphans. | 11 comments · 1 👍 · ✅ Closed |

---

## 4. Key PR Progress

| # | PR | Status | Summary |
|---|-----|--------|---------|
| [#20448](https://github.com/anthropics/claude-code/pull/20448) | Add web4-governance plugin for AI governance with R6 workflow | Open | Lightweight AI governance plugin using T3 trust tensors, entity witnessing, and R6 audit trails. Aims to bring cryptographic provenance and verifiable accountability to agent workflows. |
| [#78371](https://github.com/anthropics/claude-code/pull/78371) | Harden ralph-wiggum plugin: bounded iterations, push/publish guard, stop-hook fixes | Closed | Safety hardening for the `ralph-wiggum` plugin — adds bounded iterations, prevents unattended loops from pushing/merging/publishing/deploying half-finished work, and fixes stop-hook behavior. Kept available for local experimentation only. |

> **Note:** Only 2 PRs were updated in the last 24 hours, both community-contributed. No official Anthropic PRs appeared in the window.

---

## 5. Feature Request Trends

1. **Cost transparency and control** — Users demand clear baseline limits, real dates (not rolling boosts), and visibility when agents switch models. Issue [#91282](https://github.com/anthropics/claude-code/issues/91282) calls out the UI for stating real numbers and real dates rather than vague "50% higher" boosts.

2. **Adversarial review gates** — Issue [#90887](https://github.com/anthropics/claude-code/issues/90887) requests a harness-enforced, unbypassable PreCommit gate for adversarial review, reflecting growing demand for safety controls in agent-driven commit pipelines.

3. **Time display customization** — The addition of `timeFormat`/`timeZone` in v2.1.257 responds to a recurring need for flexible turn-end clock formatting across locales.

4. **MCP interaction controls** — Issue [#89063](https://github.com/anthropics/claude-code/issues/89063) highlights that MCP tools with `requiresUserInteraction` still surface "don't ask again" options, suggesting a need for tighter permission semantics around MCP tooling.

5. **Multi-browser identity** — Issue [#90153](https://github.com/anthropics/claude-code/issues/90153) points to the need for meaningful browser names in `list_connected_browsers` to make multi-browser workflows usable.

---

## 6. Developer Pain Points

- **Session limit anomalies on Max plans** — The single hottest issue (#38335, 842 comments) reflects deep frustration that Max plan credits are consumed far faster than documented, with no clear explanation from Anthropic.

- **macOS kernel stability** — Two independent reports of `data.kalloc.1024` zone exhaustion (#66020, #82941) indicate a systemic memory management problem under agent load, leading to kernel panics and lost work.

- **Silent model substitution and billing opacity** — Issue [#91386](https://github.com/anthropics/claude-code/issues/91386) (filed today) describes an agent running a 10× more expensive model while reporting the cheaper one, raising trust and cost-control concerns.

- **Windows desktop UX regressions** — Always-on-top windows (#85891), GPU crashes (#80444), clipboard paste broken (#90657), and file-lock crashes (#90389) paint a picture of a Windows desktop client still maturing.

- **Context management blind spots** — Issue [#91385](https://github.com/anthropics/claude-code/issues/91385) reports that the context ring no longer warns before the window limit, causing sessions to die at "Prompt is too long" with no prior yellow-warning state.

- **macOS 12 compatibility** — Both the v2.1.258 fix and issue #91381 confirm that older macOS versions remain a fragility surface, especially for the bundled desktop app.

- **Permission hook regressions** — Issue [#74256](https://github.com/anthropics/claude-code/issues/74256) documents that `PermissionRequest` hooks for `ExitPlanMode` are ignored since v2.1.199, breaking automated approval workflows.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

⚠️ Summary generation failed.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-02

---

## 1. Today's Highlights

Gemini CLI v0.59.0-preview.0 landed alongside a new nightly build, with a spotlight fix for web fetch connection routing and symlink handling from v0.58.0. Community attention is heavily concentrated on agent reliability — subagent recovery, generalist agent hangs, and browser subagent failures dominate the issue tracker, while security hardening (NTFS path sanitization, OAuth issuer validation, extension consent) drove the top PRs this cycle.

---

## 2. Releases

| Version | Type | Key Changes |
|---|---|---|
| [v0.59.0-nightly.20260902.g4963a4456](https://github.com/google-gemini/gemini-cli/releases/tag/v0.59.0-nightly.20260902.g4963a4456) | Nightly | Fix: improved destination validation and connection routing in web fetch utilities ([#29120](https://github.com/google-gemini/gemini-cli/pull/29120)). New contributor @diegogodinezr. |
| [v0.59.0-preview.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.59.0-preview.0) | Preview | Version bump from nightly; changelog accumulated from v0.58.0-preview.0 cycle. |
| [v0.58.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.58.0) | Stable | Fix: consistent symlink evaluation in ignore path handling ([#28915](https://github.com/google-gemini/gemini-cli/pull/28915)). |

---

## 3. Hot Issues

1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS reported as GOAL success** (13 comments, 2 👍)
   The `codebase_investigator` subagent falsely reports `status: "success"` with `Termination Reason: "GOAL"` even when it hit the max turn limit without performing analysis. High-impact bug for agents that depend on subagent reliability.

2. **[#19873](https://github.com/google-gemini/gemini-cli/issues/19873) — Zero-Dependency OS Sandboxing & Post-Execution Intent Routing** (9 comments, 1 👍)
   Proposes leveraging the model's native bash affinity through sandboxed execution, aiming to let Gemini use POSIX tools freely without compromising security. Community interest in safer, more capable shell interaction.

3. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs forever** (8 comments, 8 👍)
   The generalist agent deadlocks on simple operations (e.g., folder creation) unless sub-agents are explicitly disabled. Strong community signal — 8 upvotes indicate widespread frustration with agent deferral logic.

4. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — AST-aware file reads, search, and mapping** (7 comments, 1 👍)
   Epic tracking investigation into whether AST-aware tools can reduce turn waste from misaligned file reads and improve codebase navigation precision. Directly impacts context efficiency.

5. **[#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — Gemini does not use skills and sub-agents enough** (6 comments)
   Anecdotal but resonant: the model rarely invokes custom skills or sub-agents unless explicitly told to. Raises concerns about agent autonomy and skill discoverability.

6. **[#26525](https://github.com/google-gemini/gemini-cli/issues/26525) — Deterministic redaction & reduce Auto Memory logging** (5 comments)
   Auto Memory sends transcript content to the model before redaction occurs, creating a potential secret-leak window. Security-focused concern with direct privacy implications.

7. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command hangs with "Waiting input" after completion** (4 comments, 3 👍)
   Simple CLI commands complete but Gemini remains stuck in an "Awaiting user input" state. Directly blocks workflow; 3 upvotes suggest frequent occurrence.

8. **[#22232](https://github.com/google-gemini/gemini-cli/issues/22232) — Browser agent session takeover & lock recovery** (4 comments)
   The browser agent uses a restrictive fail-fast strategy on locked profiles. Request for graceful session recovery instead of hard failure, especially for persistent session mode.

9. **[#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails on Wayland** (4 comments, 1 👍)
   Browser agent crashes under Wayland compositors. Important for Linux users adopting Gemini CLI in modern desktop environments.

10. **[#20079](https://github.com/google-gemini/gemini-cli/issues/20079) — Symlinked agent files not recognized** (4 comments)
    Subagent `.md` files that are symlinks are silently ignored. Overlaps with v0.58.0 symlink fix but scoped to the agents directory specifically.

---

## 4. Key PR Progress

1. **[#29116](https://github.com/google-gemini/gemini-cli/pull/29116) — Mitigate NTFS 8.3 short name (SFN) path traversal**
   Hardens path normalization and the AllowedPathChecker against Windows SFN attacks (`git~1`, `node_m~1`, etc.). Critical security patch for Windows users.

2. **[#28863](https://github.com/google-gemini/gemini-cli/pull/28863) — Consent on env changes & sanitize runtime-altering env vars in extensions**
   Extension updates previously bypassed consent and could inject env vars into MCP server processes. Now includes env config in consent strings and sanitizes dangerous variables. **Merged.**

3. **[#29163](https://github.com/google-gemini/gemini-cli/pull/29163) — Prevent crash during auth in git repos (macOS Seatbelt)**
   Fixes a startup crash when `useGitBranchName` encounters restricted `.git` access under macOS Seatbelt or similar sandboxing. High-impact for constrained environments.

4. **[#29117](https://github.com/google-gemini/gemini-cli/pull/29117) — Enforce RFC 9207 issuer identification in MCP OAuth flow**
   Adds `iss` parameter validation to prevent unintended token routing in MCP OAuth exchanges. Security-critical for multi-tenant MCP setups.

5. **[#29067](https://github.com/google-gemini/gemini-cli/pull/29067) — Remove misleading security schemes & hardcoded credentials in a2a-server**
   Cleans up agent card metadata and strips insecure hardcoded credentials from the custom user builder. **Merged.**

6. **[#28888](https://github.com/google-gemini/gemini-cli/pull/28888) — Allow launcher workspace outside home directory**
   Uses `CODER_AGENT_WORKSPACE_PATH` as the default confinement root, enabling Coder and similar launchers to operate outside the user home. **Merged.**

7. **[#28889](https://github.com/google-gemini/gemini-cli/pull/28889) — Restore paused stdin after capability detection**
   Fixes stdin state corruption after terminal capability detection, which could cause input loss. **Merged.**

8. **[#28893](https://github.com/google-gemini/gemini-cli/pull/28893) — Preserve explicit flash model IDs**
   Ensures explicit model IDs like `gemini-3.6-flash` are not silently rewritten during the Flash rollout. **Merged.**

9. **[#29063](https://github.com/google-gemini/gemini-cli/pull/29063) — Stop Plan Mode from waiting on user feedback in non-interactive sessions**
   Fixes non-interactive Plan Mode hangs (`gemini -p "..." -y`) where the agent waited for a user turn that never arrives. **Merged.**

10. **[#29087](https://github.com/google-gemini/gemini-cli/pull/29087) — Prevent concurrent extension install races**
    Uses `proper-lockfile` to serialize extension installs across processes, preventing interleaved file copies and metadata corruption.

---

## 5. Feature Request Trends

- **Agent reliability & autonomy**: The dominant thread — subagent recovery, better skill discovery, and fixing hangs in generalist/agent pathways. The community wants agents that work consistently without manual intervention.
- **AST-aware codebase tools**: Multiple linked issues (#22745, #22746) signal demand for precision code navigation that reduces context waste and turn count.
- **Secure sandboxed execution**: Both issue [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) and PR [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) point to a push for zero-dependency OS-level sandboxing and safer extension env handling.
- **Persistent & recoverable browser sessions**: Feature requests for graceful lock recovery (#22232) and Wayland support (#21983) indicate a need for robust browser automation across platforms.
- **Long-running task tracking**: Issue [#18836](https://github.com/google-gemini/gemini-cli/issues/18836) calls for replacing in-context todo lists with persistent file-based CRUD, addressing context rot and cross-session memory loss.
- **Auto Memory improvements**: Three linked issues (#26525, #26523, #26522) around redaction, invalid patch handling, and low-signal session deduplication show the community wants a more trustworthy and efficient memory system.

---

## 6. Developer Pain Points

- **Agent hangs and false successes**: Subagents reporting GOAL on max-turn exhaustion (#22323), generalist agent deadlocks (#21409), and Plan Mode waiting for phantom user input (#29063) form a pattern of agent lifecycle management bugs that disrupt real workflows.
- **Shell command state corruption**: Commands completing while Gemini remains stuck in "awaiting input" (#25166) and stdin pause/resume issues (#28889) suggest the I/O handling layer needs hardening.
- **Browser agent fragility**: Wayland failures (#21983), lock-strategy rigidity (#22232), and settings.json overrides being ignored (#22267) make browser automation unreliable across environments.
- **Security surface in extensions and OAuth**: Bypassed consent checks (#28863), hardcoded credentials (#29067), and missing RFC 9207 validation (#29117) have drawn repeated security-focused fixes, indicating the extension and auth surfaces are high-risk areas.
- **Context bloat from naive file reads**: The "tactful extraction" proposal (#19561) and AST-aware investigations (#22745) respond to a persistent pain point — large file reads flooding context with 15k+ tokens per turn.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-02

## 1. Today's Highlights

v1.0.83-1 ships with sorting persistence in the Sessions sidebar and enterprise sign-in pinning via `forceLoginOrgs`, alongside improved `/mcp config` editing. The community is closely watching several OOM regressions and MCP initialization bugs, while a long-anticipated Vim input mode feature continues to draw strong support (75 👍).

---

## 2. Releases

### v1.0.83-1

- **Added** — Recent, Created, Name, and classic None sorting to the Sessions sidebar, with the selected order persisted across restarts.
- **Added** — Enterprise admins can pin sign-in to approved GitHub organizations using the `forceLoginOrgs` managed setting.
- **Improved** — `/mcp config` command and the MCP add/edit workflow.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#13](https://github.com/github/copilot-cli/issues/13) | CLI input should have a vi/vim input mode | 9 | 75 | The most upvoted open issue — keyboard-driven modal editing is a high-demand feature for developer ergonomics. |
| [#4664](https://github.com/github/copilot-cli/issues/4664) | CLI crashes with JavaScript heap OOM when resuming a long-standing session | 5 | 0 | Critical reliability bug: sessions with large context history are unrecoverable, causing fatal V8 crashes. |
| [#4525](https://github.com/github/copilot-cli/issues/4525) | 1.0.81-1 sends legacy `initialize` after successful modern `server/discover`, causing -32022 | 4 | 0 | MCP servers using the Python SDK 2.0.0 dual-era runner break on connection — a protocol compatibility regression. |
| [#3421](https://github.com/github/copilot-cli/issues/3421) | Azure DevOps MCP Server Connected but CLI Commands Fail with "Dangerous Request.Path" | 3 | 0 | ADO MCP works in VS Code but not the CLI, blocking enterprise DevOps integration. |
| [#4438](https://github.com/github/copilot-cli/issues/4438) | `disable-model-invocation: true` makes a skill unreachable, not manual-only | 3 | 6 | Misleading behavior: slash-invoked skills become invisible to the model, breaking expected permission gating. |
| [#3688](https://github.com/github/copilot-cli/issues/3688) | Repository-level agents resolved relative to git root, but skills/.mcp.json relative to cwd | 3 | 3 | Inconsistent discovery paths cause subagent configs to resolve incorrectly — a real bug affecting multi-repo workflows. |
| [#4672](https://github.com/github/copilot-cli/issues/4672) | 1.0.82 Regression: Unknown command: `/model` with BYOK | 2 | 1 | A regression from 1.0.81/82 that breaks model switching for Bring-Your-Own-Key configurations. |
| [#4203](https://github.com/github/copilot-cli/issues/4203) | Remote MCP OAuth expired access token forces interactive re-auth instead of silent refresh | 1 | 0 | Users are interrupted by full OAuth flows when a cached `refresh_token` could handle it silently per RFC 6749. |
| [#4686](https://github.com/github/copilot-cli/issues/4686) | Node.js OOM crash after ~37 min — 31,965 leaked async libuv handles | 1 | 0 | SEA-embedded Node process leaks async handles, causing guaranteed OOM on sustained sessions. |
| [#4680](https://github.com/github/copilot-cli/issues/4680) | CLI sends wrong model ID to custom OpenAI-compatible endpoint, killing the session | 2 | 0 | Custom endpoints receive `gpt-5.4-nano` instead of the configured model (e.g. `mimo-v2.5`), breaking BYOK entirely. |

---

## 4. Key PR Progress

*No pull requests were updated in the last 24 hours.*

---

## 5. Feature Request Trends

- **Editor ergonomics:** Vim/vi input mode (#13, 75 👍) remains the top community wishlist item, signaling strong demand for modal editing parity.
- **MCP protocol maturity:** Multiple issues target deeper MCP compatibility — OAuth refresh flows (#4203), User-Agent header compliance (#4681), legacy initialize handling (#4525), and bounded startup budgets (#4678).
- **Session persistence & recovery:** Users need reliable session resume that respects model overrides (#4645), preserves repo-level instructions across compaction (#4687), and doesn't leak memory (#4664, #4686).
- **Permission granularity:** Path-scoped persistent write approvals (#4682) and proper `disable-model-invocation` semantics (#4438) show demand for finer-grained, declarative permission controls.
- **BYOK & custom providers:** Consistent behavior across custom endpoints (#4680), `/model` command retention (#4672), and proper 403 handling (#4414, closed) indicate BYOK UX is a recurring refinement area.

---

## 6. Developer Pain Points

1. **Memory leaks & OOM crashes** — Three separate issues (#4664, #4686, #4413) report session crashes from heap exhaustion or leaked libuv handles, pointing to a systemic memory management concern in long-running sessions.
2. **MCP initialization fragility** — Issues around legacy `initialize` probes (#4525), missing headers on OAuth (#4681), blocking on unresponsive servers (#4678), and ACP startup delays reflect a CLI that isn't yet resilient to diverse MCP server implementations.
3. **BYOK configuration regressions** — The `/model` command disappearing in 1.0.82 (#4672) and wrong model IDs sent to custom endpoints (#4680) suggest release validation gaps for bring-your-own-key scenarios.
4. **Inconsistent path resolution** — Repository-level agents resolving relative to git root while skills resolve relative to cwd (#3688) creates confusing developer experience across customization layers.
5. **Enterprise environment friction** — PowerShell ConstrainedLanguage mode spews false errors on every shell command (#4683), and AppLocker/WDAC-restricted environments are not well accommodated.
6. **Subagent load management** — The concurrency limiter is a static counter with no machine-load awareness, causing CPU oversubscription and UI freezes (#4688).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-02

---

## 1. Today's Highlights

Kimi Code CLI **v1.50.0** was released, introducing a deprecation-aware update flow that automatically guides users toward Kimi Code during migration, alongside a fix for the `anthropic-beta` header when no beta features are declared. Community discussion continues around YOLO mode transparency and better error handling when canceling subagents via the escape key.

---

## 2. Releases

### v1.50.0
- **[PR #2580](https://github.com/MoonshotAI/kimi-cli/pull/2580)** — Fixes a bug where the `anthropic-beta` header was incorrectly included in requests when no beta features were declared, preventing unnecessary API overhead.
- **[PR #2581](https://github.com/MoonshotAI/kimi-cli/pull/2581)** — Bumps the `kosong` dependency to v0.56.0 for underlying updates.
- **[PR #2630](https://github.com/MoonshotAI/kimi-cli/pull/2630)** — Introduces a **deprecation-aware update flow**: when the CDN publishes a migration notice, the CLI flags the Python release as deprecated and drives a one-key migration path to Kimi Code.

---

## 3. Hot Issues

### #1298 — YOLO mode: view shell execution and file write content
**[Issue #1298](https://github.com/MoonshotAI/kimi-cli/issues/1298)** | Author: Wolido | Closed | 👍 0
> Users running Kimi in YOLO mode (autonomous execution) want visibility into exactly which shell commands are executed and what file modifications are made, so they can intervene on serious errors. Long commands are currently truncated with `...`, hiding critical detail. This is a safety-critical transparency request.

### #1297 — Cancelling subagents with Escape shows unhandled errors
**[Issue #1297](https://github.com/MoonshotAI/kimi-cli/issues/1297)** | Author: chriswingler | Closed | 👍 1
> Pressing Escape to cancel subagents triggers an unhandled exception. A clean cancellation path is essential for interactive CLI usability — this bug directly impacts power users who rely on subagent parallelism and need to abort mid-flight.

### #1294 — Follow XDG Base Directory spec
**[Issue #1294](https://github.com/MoonshotAI/kimi-cli/issues/1294)** | Author: sisrfeng | Closed | 👍 1
> Requests migrating config storage from `~/.kimi` to `~/.config/kimi` per the XDG Base Directory specification. This is a growing community expectation for Linux desktop hygiene and tooling standards.

---

## 4. Key PR Progress

### #2614 — docs(plugins): document security and persistent data
**[PR #2614](https://github.com/MoonshotAI/kimi-cli/pull/2614)** | Open | Author: QIANLING-0831
> Clarifies the plugin contract for root `plugin.json`, command-based tools, `inject`, and installation under `~/.kimi/plugins/`. Improves security transparency for plugin developers.

### #2632 — chore(release): bump kimi-cli to 1.50.0
**[PR #2632](https://github.com/MoonshotAI/kimi-cli/pull/2632)** | Closed | Author: sailist
> Release coordination PR: bumps version, syncs `packages/kimi-code` wrapper to `kimi-cli==1.50.0`, and validates via `check_version_tag.py`.

### #742 — Add `$ list skills` like Codex
**[PR #742](https://github.com/MoonshotAI/kimi-cli/pull/742)** | Closed | Author: ZacharyZhang-NY
> Proposed adding a `$ skills` command to list available skills, mirroring the interface from OpenAI's Codex CLI — a feature parity request with a competing tool.

### #2630 — feat(shell): deprecation-aware update flow with one-key migration to Kimi Code
**[PR #2630](https://github.com/MoonshotAI/kimi-cli/pull/2630)** | Closed | Author: jackfish212
> Core migration bridge: detects CDN deprecation notices and prompts users to migrate from `kimi-cli` (Python) to Kimi Code in a single step. Part of the broader product transition strategy.

---

## 5. Feature Request Trends

| Trend | Evidence |
|---|---|
| **YOLO mode observability** | Issue #1298 — users want full command/file-write visibility during autonomous runs |
| **Product parity with Codex** | PR #742 — `$ skills` listing, suggesting users expect feature alignment with competing CLIs |
| **XDG compliance / config hygiene** | Issue #1294 — community pressure to follow Linux desktop standards |
| **Graceful cancellation** | Issue #1297 — need for clean abort paths in subagent workflows |
| **Migration path clarity** | PR #2630 — ongoing need for clear transition guidance from kimi-cli to Kimi Code |

---

## 6. Developer Pain Points

1. **YOLO mode is a black box** — When running in autonomous mode, users cannot inspect truncated shell commands or file mutations, creating a trust and safety gap. The community explicitly flagged the need for a real-time execution log.

2. **Subagent cancellation throws unhandled exceptions** — Hitting Escape to abort parallel subagents currently crashes instead of gracefully terminating. This erodes confidence in the tool's reliability during long-running tasks.

3. **Config storage doesn't follow platform conventions** — Storing data in `~/.kimi` instead of `~/.config/kimi` is increasingly viewed as non-compliant with Linux desktop standards, and a growing number of users are requesting XDG adoption.

4. **Migration from kimi-cli to Kimi Code is an active concern** — While PR #2630 addresses the technical path, the community still needs clear, frictionless transition guidance as the Python-based CLI is deprecated in favor of the new product.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-09-02

## 1. Today's Highlights

OpenCode v1.18.26 shipped with critical reliability fixes for Claude 5 sessions (stale thinking block tolerance) and Bedrock reasoning models (now accepting `none` reasoning effort). Meanwhile, the community continues to surface a persistent stale-project-path bug that resurfaces across Windows, macOS, and Linux, with over 20 related issues all pointing to the same root cause: workspace binding does not properly track directory renames or moves.

---

## 2. Releases

**v1.18.26** ([CHANGELOG](https://github.com/anomalyco/opencode/releases))
- **Claude 5 sessions** now tolerate stale thinking blocks instead of failing after prompt or tool changes.
- **Bedrock GPT-5.6 models** now accept `none` reasoning effort.
- **Bedrock reasoning and replay handling** made more reliable (@pengzh1).
- **Tool call timing** accuracy improved when… (release notes truncated).

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#33909](https://github.com/anomalyco/opencode/issues/33909) | Moving a project directory breaks all existing sessions | 5 👍 — sessions lose their `session.directory` binding after a rename, making all prior history unreachable. |
| [#35240](https://github.com/anomalyco/opencode/issues/35240) | Server keeps stale `project.worktree` after folder rename (remote) | 1 👍 — remote server + Desktop client setup shows the bug is not isolated to one platform. |
| [#46721](https://github.com/anomalyco/opencode/issues/46721) | PR #46721: Desktop silently returns empty response when directory is gone | 0 👍 — silent failure (completion sound plays but no response) instead of a clear error. |
| [#40986](https://github.com/anomalyco/opencode/issues/40986) | Renaming a folder breaks project↔directory binding (phantom project) | 2 👍 — app keeps pointing to non-existent paths; display name cannot be updated. |
| [#44538](https://github.com/anomalyco/opencode/issues/44538) | Case-sensitive path mismatch loses sessions on rename | 0 👍 — Windows path normalization inconsistency causes session disappearance. |
| [#34737](https://github.com/anomalyco/opencode/issues/34737) | Project path not updated after moving project directory | 0 👍 — same root cause, reported by a Windows user. |
| [#31074](https://github.com/anomalyco/opencode/issues/31074) | macOS keeps opening old project folder after move | 3 👍 — one of the earliest reports; strong community signal this is a cross-platform problem. |
| [#31869](https://github.com/anomalyco/opencode/issues/31869) | Windows workspace path stuck after rename | 2 👍 |
| [#31888](https://github.com/anomalyco/opencode/issues/31888) | Stale path persists even after full workspace reset (Windows) | 0 👍 |
| [#31401](https://github.com/anomalyco/opencode/issues/31401) | Deletes project folder → app reopens the dead path automatically | 2 👍 — auto-recovery behavior is actively harmful. |

---

## 4. Key PR Progress

| PR | Title | Summary |
|----|-------|---------|
| [#46726](https://github.com/anomalyco/opencode/pull/46726) | fix(tui): exit cleanly when startup probes cannot reach the server | Fixes #36688 — TUI no longer hangs when the background server is still electing or cold-booting. |
| [#46682](https://github.com/anomalyco/opencode/pull/46682) | fix(cli): await plugin activation before caching ACP catalog | Prevents partial catalog caching that pins built-in-only models until restart (@kitlangton). |
| [#46725](https://github.com/anomalyco/opencode/pull/46725) | fix(core): rebuild registry state on read | Resolves OAuth credential refresh ordering bug during plugin startup (@kitlangton). |
| [#46721](https://github.com/anomalyco/opencode/pull/46721) | refactor(core): carry typed job outcomes for stops | Stops are no longer reported as shell failures; subagent cancellations surface explicitly instead of collapsing into a generic "cancelled" error. |
| [#46723](https://github.com/anomalyco/opencode/pull/46723) | fix(app): stabilize optimistic prompt position | Fixes visual jump of the prompt row during virtualizer re-renders. |
| [#46717](https://github.com/anomalyco/opencode/pull/46717) | feat(app): add timeline detail presets and placement controls | Five presets (Everything → Text only) plus separate Placement/Details toggles in Settings and session toolbar. |
| [#46650](https://github.com/anomalyco/opencode/pull/46650) | fix(tui): show session scrollbar by default for long chats | Closes #46654 — scrollbar now visible, improving navigation in extended sessions. |
| [#46713](https://github.com/anomalyco/opencode/pull/46713) | fix(app): keep new local sessions in the selected directory | New sessions respect the folder the user actively selected instead of falling back to a cached canonical path. |
| [#46724](https://github.com/anomalyco/opencode/pull/46724) | feat(core): add hidden glob option | Exposes a `hidden` flag on the glob tool, forwarded to ripgrep; defaults unchanged. |
| [#46716](https://github.com/anomalyco/opencode/pull/46716) | feat(core): add grep matching options | Adds `literal` and `caseSensitive` options to the grep tool mapped to ripgrep flags. |

---

## 5. Feature Request Trends

1. **Path/workspace hygiene** — The dominant theme. Users want reliable directory tracking on move/rename, clear error messages instead of silent failures, and an easy way to unstick a phantom project binding.
2. **Plugin and provider management UI** — Issue [#33704](https://github.com/anomalyco/opencode/issues/33704) requests GUI controls for custom providers (LM Studio, Jan AI) and model lists, reducing the friction of config-file editing.
3. **Per-MCP-server trust configuration** — PR [#40125](https://github.com/anomalyco/opencode/pull/40125) enables fingerprint pinning per server instead of a global insecure toggle.
4. **Session organization** — Timeline detail presets and background hint improvements reflect demand for better long-session ergonomics.
5. **Plugin SDK examples** — PR [#46328](https://github.com/anomalyco/opencode/pull/46328) provides a `goal-loop` example, signaling community appetite for more SDK templates.

---

## 6. Developer Pain Points

- **Stale project paths are the top bug.** Over 20 issues filed across Windows, macOS, and Linux all describe the same failure mode: moving or renaming a project directory leaves the app pointing at the old location. Symptoms range from phantom projects and broken sessions to full app freezes and 500 errors on `POST /session/{id}/command`. There is no clean recovery path currently.
- **Silent failures instead of errors.** When a project directory disappears, the app plays the completion sound and returns nothing — no error banner, no guidance. Users report this as deeply confusing.
- **Case-sensitivity mismatches on Windows.** Path normalization differences between stored and resolved paths cause sessions to vanish after a rename, even when the new path is on the same volume.
- **Duplicate project IDs for same-remote clones.** Two local checkouts of the same git repository share a `project_id` derived from the remote URL, so the desktop sidebar shows only one.
- **Memory bloat from unbounded PDF encoding.** Issue [#42263](https://github.com/anomalyco/opencode/issues/42263) reports that large PDFs are base64-encoded into memory with no size cap and re-encoded every turn, causing OOM crashes.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-02

## 1. Today's Highlights
The Pi coding agent continues to mature with focus on provider compatibility (Gemini 3.x, OpenAI Responses, Bedrock) and TUI polish. Several long-standing tool-loop and session-management bugs were closed this week, while new proposals emerge around in-memory session forking and RPC abort semantics. No new release was published in the last 24 hours.

## 2. Releases
None in the last 24 hours.

## 3. Hot Issues

1. **[XDG Base Directory Compliance](https://github.com/earendil-works/pi/issues/2870)** — 21 comments · 54 👍 · 🔒 Closed
   The longest-running polish issue: Pi clutters `~` with config/state directories on Linux. The community overwhelmingly supports adopting `$XDG_CONFIG_HOME` / `$XDG_DATA_HOME`. Closed; likely landed in a recent release.

2. **[Gemini 3.x Tool-Use Failure](https://github.com/earendil-works/pi/issues/6996)** — 7 comments · 🟢 Open
   Gemini 3.5/3.6 Flash models crash during tool use because `thought_signature` is missing from conversation history. Critical for any user running Gemini reasoning models via tool-calling workflows.

3. **[Agent Stuck "Working" Loop](https://github.com/earendil-works/pi/issues/4338)** — 8 comments · 🔒 Closed
   The agent repeatedly says "working" with no progress or output, requiring manual interruption. A frustrating UX bug that affected multiple users; closed after fix.

4. **[Copy-Paste Artifacts in TUI](https://github.com/earendil-works/pi/issues/5931)** — 8 comments · 🔒 Closed
   Pasted text from Pi's TUI introduced spurious spaces and line-breaks at wrapping boundaries. Closed; likely resolved by a TUI rendering fix.

5. **[Plain-HTTP Provider Through Forward Proxy](https://github.com/earendil-works/pi/issues/8134)** — 7 comments · 🟢 Open
   Since v0.84.0, sessions against OpenAI-compatible providers over `http://` via `HTTP_PROXY` hang after the first tool call. Blocks proxy-first deployments.

6. **[Wide Inline Images Stretched](https://github.com/earendil-works/pi/issues/8938)** — 3 comments · 🟢 Open
   Very wide, short inline images (e.g. 615×86 PNG) render noticeably too tall due to an incorrect cell-to-pixel aspect-ratio calculation in the TUI. Visual bug affecting diagram/meme display.

7. **[RPC Abort Ignores Compaction](https://github.com/earendil-works/pi/issues/8920)** — 2 comments · 🟢 Open
   Calling `abort` during a manual compaction in RPC mode returns `success: true` but the compaction request remains pending. Client-side abort semantics are broken in this edge case.

8. **[Keybinding Rebind Ignored for Model Selector](https://github.com/earendil-works/pi/issues/8797)** — 2 comments · 🟢 Open
   Rebinding `app.models.save` in `keybindings.json` has no effect; the model selector and thinking selector hardcode `ctrl+s` instead of reading the binding.

9. **[Bedrock Tool Schema Validation](https://github.com/earendil-works/pi/issues/8804)** — 2 comments · 🔒 Closed
   Bedrock requires top-level `type: "object"` in tool input schemas; some built-in tool schemas violated this. Closed after fix.

10. **[Grok 4.6 Infinite Tool-Call Loop](https://github.com/earendil-works/pi/issues/8973)** — 2 comments · 🔒 Closed
    Through the `openai-responses` xAI routing, Grok 4.6 re-issues the identical tool call indefinitely, ignoring recorded tool results. A regression introduced in v0.84.3.

## 4. Key PR Progress

| PR | Status | Summary |
|----|--------|---------|
| [#8969](https://github.com/earendil-works/pi/pull/8969) | ✅ Merged | Subagent tool now accepts `model` and `effort` overrides at dispatch time instead of inheriting the parent session model. |
| [#8966](https://github.com/earendil-works/pi/pull/8966) | ✅ Merged | `--provider` without `--model` now correctly selects the provider's default model; auth failures now name the failing provider. |
| [#8951](https://github.com/earendil-works/pi/pull/8951) | ✅ Merged | Headless/RPC/subagent sessions are hidden from `/resume` by default, reducing noise in the session picker. |
| [#8941](https://github.com/earendil-works/pi/pull/8941) | ✅ Merged | Added `supportsMaxOutputTokens` compat flag for OpenAI Responses provider, fixing 400 errors from gateways that reject the parameter. |
| [#8898](https://github.com/earendil-works/pi/pull/8898) | ✅ Merged | Wraps `SIGWINCH` in a self-signal to work under restricted seccomp policies (fixes container/sandbox runs). |
| [#8972](https://github.com/earendil-works/pi/pull/8972) | ✅ Merged | New extension API: start a fresh model context window within the current session without creating a new session or compaction summary. |
| [#8737](https://github.com/earendil-works/pi/pull/8737) | ✅ Merged | Fixes `NO_PROXY` parsing for wildcard domains (`*.example.com`), bare domains, and IPv6 entries. |
| [#8936](https://github.com/earendil-works/pi/pull/8936) | ✅ Merged | Prepared parallel tool calls now stop cleanly after a later preflight abort, reporting `Operation aborted`. |
| [#8937](https://github.com/earendil-works/pi/pull/8937) | ✅ Merged | Fixes in-memory fork race: `teardownCurrent()` now runs before the session reset, preventing `toolResult` landing in the wrong session. |
| [#8980](https://github.com/earendil-works/pi/pull/8980) | 🟢 Open | Ingests external session entries into in-memory sessions, extending the fork/resume API surface. |

## 5. Feature Request Trends

- **Provider & model catalog hardening** — Multiple issues (Gemini 3.x, Bedrock schema, Grok loop, model catalog metadata) point to a trend of improving reliability across diverse provider integrations.
- **Extension API expansion** — Requests for fresh-context APIs, subagent model/effort overrides, and prompt-preflight callbacks show developers want more programmatic control over session lifecycle.
- **TUI polish** — Image aspect-ratio fixes, spinner redesign, fullscreen footer behavior, and theme-marker visibility indicate ongoing investment in the terminal UI experience.
- **RPC / automation support** — Compaction abort semantics, headless session filtering, and `get_commands` response schema corrections target the growing RPC-mode audience.
- **Environment & auth flexibility** — `CLAUDE_CODE_OAUTH_TOKEN`, `ANTHROPIC_WORKSPACE_ID`, and OAuth-type extensions reflect demand for CI/headless authentication paths.

## 6. Developer Pain Points

- **Provider-specific quirks** — Gemini 3.x, Bedrock, and xAI routing each expose unique schema or protocol incompatibilities, forcing per-provider compat flags and patches.
- **Tool-loop deadlocks** — The "agent stuck working" pattern (#4338) and the Grok 4.6 infinite tool call (#8973) both represent agents entering unrecoverable loops, a high-severity UX failure.
- **Proxy & auth friction** — Plain-HTTP providers break through forward proxies (#8134), and `NO_PROXY` parsing had long-standing bugs (#8737), complicating enterprise/network-restricted deployments.
- **TUI rendering inaccuracies** — Image stretching (#8938) and keybinding overrides not respected (#8797) erode confidence in visual fidelity and configuration portability.
- **Session lifecycle edge cases** — Fork races (#8937), stale pre-trust runtimes (#8946), and compaction-abort semantics (#8920) show that in-memory session management has several unguarded transitions.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-02

---

## 1. Today's Highlights

Qwen Code released **cua-driver-rs v0.20.3** with platform-specific prebuilt binaries across macOS (codesigned/notarized), Linux, and Windows. The TUI rendering migration from **ink to OpenTUI** continues to generate the most discussion (#8662, 18 comments), while the team shipped a critical **backpressure fix** (#10731) that prevents ACP NDJSON queue saturation from tearing down entire channels. A permissions semantic regression introduced in v0.22.1 (#10218) is drawing sharp community attention.

---

## 2. Releases

**cua-driver-rs v0.20.3** — Prebuilt Qwen CUA Driver binaries for all three platforms:
- **macOS**: codesigned + notarized universal binary with `QwenCuaDriver.app`
- **Linux**: unsigned, x86_64 + arm64, glibc 2.31 minimum
- **Windows**: unsigned UIAccess worker + native SDK payload (x86_64 + arm64)

[v0.20.3 Release](https://github.com/QwenLM/qwen-code/releases)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|------------|
| [#8662](https://github.com/QwenLM/qwen-code/issues/8662) | Migrate TUI rendering from ink to OpenTUI | Structural problems (flicker, rendering bugs) are hard to fix within ink; this migration is a long-term UX investment. | 18 comments |
| [#5975](https://github.com/QwenLM/qwen-code/issues/5975) | API Error: No stream activity for 120000ms | High-impact bug where v0.19.3+ shows frequent stream timeouts after model thought phases. | 15 comments, 1 👍 |
| [#10530](https://github.com/QwenLM/qwen-code/issues/10530) | 400 Failed to initialize samplers in 0.22.3 | Regression in grammar parsing with Qwen 3.x models via llama-server; Gemma4 unaffected. | 5 comments |
| [#10218](https://github.com/QwenLM/qwen-code/issues/10218) | `permissions.allow` semantic change in 0.22.1 | Tools not covered by allowlist are now **silently disabled** instead of prompting — a breaking behavioral shift undocumented in release notes. | 5 comments |
| [#10162](https://github.com/QwenLM/qwen-code/issues/10162) | Degrade gracefully on ACP NDJSON queue saturation | Current behavior tears down the whole channel on saturation; a graceful degradation would improve daemon stability. | 5 comments |
| [#10710](https://github.com/QwenLM/qwen-code/issues/10710) | Killed-turn output hidden on session reload | In `qwen serve`, a killed turn's assistant output is persisted but hidden from the transcript, causing confusing UX. | 4 comments |
| [#10749](https://github.com/QwenLM/qwen-code/issues/10749) | TUI scrolling loads prompts instead of scrolling | Mouse/trackpad scroll in the TUI injects old prompts into the input field rather than scrolling the conversation. | 3 comments |
| [#2339](https://github.com/QwenLM/qwen-code/issues/2339) | Telegram Bot Mode (`--telegram`) | Strong community interest (3 👍) for remote interaction via Telegram; consistently top-voted feature request. | 4 comments, 3 👍 |
| [#10583](https://github.com/QwenLM/qwen-code/issues/10583) | Lightweight Bubblewrap sandbox for Linux | Requests a native `bwrap` backend as an alternative to Docker/Podman for OS-level isolation without container dependencies. | 4 comments |
| [#10767](https://github.com/QwenLM/qwen-code/issues/10767) | OpenTUI output-style picker parity gaps | Post-migration regression: the `/output-style` picker has incomplete state and transcript behavior parity with the old TUI. | 2 comments |

---

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#10765](https://github.com/QwenLM/qwen-code/pull/10765) | Isolate release validation workloads | Introduces a dedicated `ecs-qwen-hk4-host` lane for release validation, decoupling it from shared runner contention. |
| [#10731](https://github.com/QwenLM/qwen-code/pull/10731) | **Backpressure on ACP NDJSON saturation** | Replaces immediate channel teardown with a bounded grace-window wait (`queueSaturationGraceMs`, default 5s) when the decoded NDJSON queue saturates. [Closes #10162](https://github.com/QwenLM/qwen-code/issues/10162). |
| [#10732](https://github.com/QwenLM/qwen-code/pull/10732) | Fix `[object Object]` in prompt-turn failure logs | Ensures non-`Error` rejections (e.g., bare JSON-RPC error objects) log meaningfully instead of degrading to `[object Object]`. |
| [#10687](https://github.com/QwenLM/qwen-code/pull/10687) | Guard channel pidfiles against PID reuse | Adds a Linux process-start token to pidfiles; recycled PIDs are treated as stale without signaling the new owner. |
| [#10645](https://github.com/QwenLM/qwen-code/pull/10645) | Make `todo_write` opt-in | Removes `todo_write` from the default tool surface; users must explicitly enable it via `tools.todoWrite.enabled: true`. |
| [#10527](https://github.com/QwenLM/qwen-code/pull/10527) | Fix heartbeat mint-skip test race | Stabilizes a flaky node:test helper that reddened CI without any product defect by fixing its fixed-wait timing. |
| [#9952](https://github.com/QwenLM/qwen-code/pull/9952) | Configurable Mem0 providers | Adds a versioned, immutable wire contract for Mem0-compatible external context providers, covering Mem0 Platform V3 and built-in presets. |
| [#10347](https://github.com/QwenLM/qwen-code/pull/10347) | Auto-retry transient EOF network errors | Reclassifies wrapped low-level EOF errors (e.g., `400 network error ... EOF`) as retryable transport errors instead of fail-fast client errors. |
| [#8927](https://github.com/QwenLM/qwen-code/pull/8927) | Bound session lifetime with `sessionRotation` | Adds per-channel `sessionRotation` (max turns or max duration) so stale routes automatically start fresh sessions. |
| [#9260](https://github.com/QwenLM/qwen-code/pull/9260) | Preserve manual session name across `/clear` | Web Shell now carries a user-assigned session title across `/clear` commands; auto-generated titles are excluded. |

---

## 5. Feature Request Trends

- **Alternative sandboxing**: Users want lightweight, container-free isolation options (Bubblewrap #10583) alongside Docker/Podman.
- **Remote/external access**: Telegram bot mode (#2339) remains a persistent community ask for headless and remote interaction.
- **TUI/UX maturity**: OpenTUI migration follow-ups (#10728, #10767), scroll behavior fixes (#10749), and session turn navigation (#10750) show sustained investment in terminal UX.
- **Session lifecycle control**: Session rotation (#8927), turn navigation (#10750), and session name persistence (#9260) indicate demand for finer-grained control over interactive sessions.
- **Tool surface customization**: Making `todo_write` opt-in (#10645) and the `permissions.allow` semantics debate (#10218) reflect a growing desire for configurable, minimal-by-default tool sets.

---

## 6. Developer Pain Points

- **Streaming timeouts**: Issue #5975 (15 comments) highlights a recurring pattern where slow self-hosted models trigger stream-activity timeouts after thought phases, suggesting the default 120s threshold needs configurability.
- **Permissions regression**: The v0.22.1 behavioral change in `permissions.allow` (#10218) — silently disabling uncovered tools instead of prompting — is a high-friction undocumented breaking change.
- **CI flakiness**: Multiple CI-related issues (#10422 on release pipeline slowdown, #10734 on CPU-budget assertion mismatch, #10527 on test race) point to growing pains as the test surface and release pipeline expand.
- **OpenTUI migration debt**: Several deferred review items (#10728) and parity gaps (#10767) from the ink→OpenTUI migration are creating a backlog of non-critical but user-facing regressions.
- **Extension installation bugs**: Windows `qwen extensions install` from `.zip` URLs silently exits 0 without installing (#10741, #10742), indicating a gap in error handling for the extension pipeline.
- **External editor failures**: Edit confirmation offers "Modify with external editor" even when the configured editor is unavailable (#10745), leading to silent flow failures.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-09-02

## 1. Today's Highlights

The 0.9.12 shell-wave release is actively landing across multiple PRs, bringing a redesigned settings surface, truthful Tideline chrome, native ChatGPT sign-in, and a persistent goal-loop rehydration. Meanwhile, the team is closing out legacy issues around provider auto-switching, Windows flag parsing, and i18n drift, while gauging interest in OpenDesign MCP compatibility.

## 2. Releases

No new releases in the last 24 hours. The 0.9.12 release lane is accumulating merged PRs and remains in active rollout.

## 3. Hot Issues

1. **[5806] OpenDesign compatibility** — *Open* · [Link](https://github.com/Hmbown/CodeWhale/issues/5806)
   New feature request to support the open-source OpenDesign studio (93k★, Apache-2.0), first via MCP then a native runtime adapter. Signals demand for design-engine workflows beyond pure coding.

2. **[5094] Typed Responses dialect for custom providers** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/5094)
   Named `openai-compatible` providers are hard-locked to Chat Completions. Allowing explicit Responses dialect selection would let users target newer API shapes without protocol guessing.

3. **[4720] Provider/model auto-switching under-baked** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/4720)
   The runtime silently switched providers (deepseek → zai) without clear intent, exposing a UX gap in how auto-switching is surfaced and controlled.

4. **[4564] Windows flag parsing bug** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/4564)
   On Windows, `--model` and `--toolsets` placed before `exec` are consumed as a single concatenated argument. Community proposed env-var fallbacks as a workaround.

5. **[4956] WSL2 provider connection failure** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/4956)
   Network error after restarting WSL2 shells; affects users running Codewhale in WSL2 and highlights fragility in provider connectivity across VM boundaries.

6. **[5522] First-run onboarding too heavy** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/5522)
   Users report a wall of English settings and telemetry disclosures before reaching a working session. The team committed to a progressive first-run experience.

7. **[2535] ACP+MCP co-support & stream output** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/2535)
   Chinese-language feature request for ACP mode to natively load MCP tools (not just serve as a transport protocol), enabling richer IM/chat integrations like Feishu.

8. **[4394] Compaction survival contract** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/4394)
   Calls for a documented, structured contract around compaction behavior — cache paths, pruning rules, retry semantics — to improve reliability and debugging.

9. **[5735] Flaky CI test under parallel load** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/5735)
   `runtime_chat_relay` test fails under CI parallel execution due to owner-lock conflicts, indicating a race in the relay/reopen logic.

10. **[1330] ZenMux as first-class provider** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/issues/1330)
    Feature request to treat ZenMux as a native provider rather than a ChatGPT-style workaround, reflecting growing demand for diverse proxy-provider routes.

## 4. Key PR Progress

1. **[5811] Honest info line under composer** — *Open* · [Link](https://github.com/Hmbown/CodeWhale/pull/5811)
   Session facts (owner/repo, branch, model, context %, help hint) now render as the shell's last row directly beneath the composer, replacing the previous posture row.

2. **[5814] `/fullscreen` and `/inline` runtime switch** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5814)
   Users can toggle between alternate-screen fullscreen and inline mode at runtime, preserving terminal scrollback when exiting inline.

3. **[5817] React/React-DOM alignment fix** — *Open* · [Link](https://github.com/Hmbown/CodeWhale/pull/5817)
   Fixes `npm ci` breakage caused by dependabot updating react-dom to 19.2.8 while react remained at 19.2.6 — a peer-dependency conflict.

4. **[5813] Diff cards emphasise changed words** — *Open* · [Link](https://github.com/Hmbown/CodeWhale/pull/5813)
   Replaced lines in diff cards now highlight only the changed words (bold + reversed), improving scannability over full-line changes.

5. **[5816] Rehydrate persisted goals post-restart** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5816)
   Goals set on a runtime thread now survive host restarts; `PUT /v1/threads/{id}/goal` re-arms the continuation loop on engine load.

6. **[5812] Tool output preserves ANSI colours** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5812)
   Shell tool output now retains colour instead of stripping ANSI codes — `cargo`, `git`, `gh` output renders with formatting intact.

7. **[5810] One settings schema, `/settings` projection** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5810)
   Consolidates settings into a single schema with a tabbed `/settings` panel matching the SHELL-DESIGN spec — labels, values, descriptions, and preview lines.

8. **[5815] Fleet models surface first** — *Open* · [Link](https://github.com/Hmbown/CodeWhale/pull/5815)
   The model picker prioritizes user-added fleet models; `⇧F` toggles a model into/out of the fleet.

9. **[5784] Native ChatGPT PKCE sign-in** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5784)
   First-class `openai-codex` route now supports browser-based PKCE sign-in without requiring the Codex CLI installed — refreshable tokens stored in Codewhale-owned storage.

10. **[5807] Stale bundled model catalog fix** — *Closed* · [Link](https://github.com/Hmbown/CodeWhale/pull/5807)
    Release-blocker fix: bundled model snapshot TTL reduced from 10 years to 30 days, re-enabling staleness detection so the catalog doesn't present stale entries forever.

## 5. Feature Request Trends

- **Provider diversity & first-class integration** — Multiple closed issues (#1330 ZenMux, #3751 Neuralwatt, #5094 Responses dialect, #5806 OpenDesign) show community appetite for natively supported providers beyond the OpenAI-compatible shim pattern, with emphasis on non-token pricing and protocol flexibility.
- **MCP tool access in all modes** — ACP+MCP coexistence (#2535) and background-task wait primitives (#5549) reflect demand for unified tool access regardless of interaction mode.
- **Progressive onboarding** — The recurring theme across #5522 and the new `isZh` ceiling test (#5805) is reducing first-run friction for both English and non-English users.
- **UI truthfulness & compactness** — Tideline chrome (#5754, #5756, #5757, #5761, #5764), info line (#5811), and diff emphasis (#5813) all point to a design philosophy of "truthful" rendering — no pretend activity, no hidden state, no inert controls.

## 6. Developer Pain Points

- **Platform-specific parsing bugs** — The Windows flag-consumption issue (#4564) and WSL2 connectivity break (#4956) indicate ongoing fragility in cross-platform CLI argument handling and VM-boundary networking.
- **CI flakiness under parallel load** — Owner-lock races in `runtime_chat_relay` (#5735) continue to plague parallel test execution, suggesting a systemic concurrency issue in the relay subsystem.
- **Stale bundled data** — The 10-year TTL on the model catalog (#5807) went undetected for a release cycle, highlighting a gap in automated staleness validation for embedded assets.
- **i18n drift** — The `isZh` branching count growing from 12 to 31 over 90 days (#5519) prompted a new ceiling test, but signals that locale-migration work is hard to track without dedicated tooling.
- **Settings surface complexity** — The legacy settings audit (#4721) and the consolidation PR (#5810) confirm that the settings menu has accumulated density, mislabeled rows, and dead code over time — a refactoring effort with community support.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*