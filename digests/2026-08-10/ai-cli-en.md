# AI CLI Tools Community Digest 2026-08-10

> Generated: 2026-08-10 02:18 UTC | Tools covered: 10

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
**Date: 2026-08-10**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in August 2026 is marked by intense maturation across major providers and independent projects. Community-driven development is accelerating, with nightly releases, dependency overhauls, and rapid issue triage becoming standard. The dominant narrative across all tools is the push toward **reliable multi-agent orchestration**, **cross-platform session continuity**, and **provider-agnostic compatibility**. While incumbents (Claude Code, Codex, Copilot CLI) battle reliability regressions and enterprise integration gaps, independent and open projects (OpenCode, Pi, Qwen Code, DeepSeek TUI) are aggressively iterating on UX, session persistence, and composability.

---

## 2. Activity Comparison

| Tool | Open Issues (Hot) | PRs in 24h | Releases | Notable Activity |
|------|:-:|:-:|:-:|------|
| **Claude Code** | 10 | 5 (3 open) | — | Safety classifier false positives; 76-upvote session-resume feature request |
| **OpenAI Codex** | 10 (2 closed) | 8 (7 closed) | — | Windows line-ending fix closed after ~1 year; Windows Computer Use regression cluster |
| **Gemini CLI** | 10 | 9 (3 open) | v0.56.0-nightly | Major dep overhaul (74 packages); "agents calling agents" PR in review |
| **GitHub Copilot CLI** | 10 | 0 | — | MCP handshake fragility; Claude model availability regression for enterprise |
| **Kimi Code CLI** | 2 | 1 | — | Low activity; streaming hang bug; memory system request |
| **OpenCode** | 10 | 10 | — | Memory megathread (96 👍); clipboard bug (110 👍); compaction bounds fix |
| **Pi** | 10 | 9 | — | Remote session wire protocol merged; Copilot login rate-limit fix |
| **Qwen Code** | 10 | 10 | v0.21.8-nightly | Multi-agent coordination RFC; Goal v3 adoption in ACP; CI watchdog |
| **DeepSeek TUI** | 10 | 10 | v0.9.6 | Compaction rebuild; fleet loadout auto; CLI/TUI parity push |
| **Grok Build** | — | 0 | — | No activity |

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Multi-agent orchestration** | Gemini CLI, Qwen Code, OpenCode, DeepSeek TUI, Pi | Recursive agent composition, session coordination, shared task visibility, subagent permission handling |
| **Session continuity / cross-platform sync** | Codex, Claude Code, Qwen Code, Pi | Resume from any directory, conversation sync across web/desktop/IDE, durable session archival |
| **Provider/model compatibility depth** | OpenCode, Kimi Code, Pi, Claude Code | Non-streaming provider support, model fallback/failover, BYOK reliability, MCP tool-parameter normalization |
| **MCP ecosystem integration** | Gemini CLI, Copilot CLI, Qwen Code, OpenCode | Inbound notification support, configurable timeouts/retries, spec compliance (`server/discover`, optional GET/SSE) |
| **Session memory / persistence** | Kimi Code, OpenCode, Qwen Code, Pi | Cross-session context, Auto Memory quality, project-state retention, external context provider profiles |
| **IDE extension reliability** | Codex, OpenCode, Pi | Extension load failures, prompt queue bugs, clipboard integration, TUI viewport stability |

---

## 4. Differentiation Analysis

| Dimension | Incumbent-Backed Tools | Independent / Open Tools |
|-----------|----------------------|-------------------------|
| **Tools** | Claude Code, Codex, Copilot CLI, Gemini CLI | OpenCode, Pi, Qwen Code, DeepSeek TUI, Kimi Code |
| **Target users** | Enterprise/organizational users, mainstream developers | Power users, self-hosters, multi-provider workflows, researchers |
| **Feature focus** | Model availability, safety classification, IDE integration, remote sessions | Session control, provider compatibility, extensibility, UX polish |
| **Release cadence** | Slack (nightly or none in window) | Aggressive (Gemini nightly, Qwen nightly, DeepSeek patch) |
| **Technical approach** | Centralized provider lock-in; proprietary session formats | Open protocols (Pi wire protocol, ACP, Agent Skills spec), pluggable architectures |
| **Community voice** | Lower upvote density; enterprise pain points dominate | High engagement (OpenCode 110 👍, 96 👍); feature requests drive PRs |

---

## 5. Community Momentum & Maturity

**Most active communities (by issue engagement + PR velocity):**
1. **OpenCode** — 96+ upvotes on memory and clipboard issues; 10 PRs landed; strong self-organizing triage (memory megathread requesting heap snapshots).
2. **Pi** — 9 PRs including a merged remote-session protocol; extension system being stress-tested by real MCP deployments.
3. **Qwen Code** — 10 PRs with substantive features (multi-agent coordination, Goal v3, CI watchdog); nightly release cadence.
4. **Gemini CLI** — 9 PRs with a major dependency overhaul and "agents calling agents" capability; nightly builds signal rapid iteration.

**Rapidly iterating (smaller but focused):**
- **DeepSeek TUI** — v0.9.6 released with compaction rebuild; active RFC-style community discussion on fleet UX and translation.
- **Kimi Code CLI** — Low volume but targeted fixes (MCP metadata stripping); memory system is the #1 community ask.

**Maturity signals:**
- **Claude Code** and **Copilot CLI** show enterprise-grade friction (safety classifier overrides, model catalog regressions) rather than feature gaps — a sign of scale.
- **Codex** closed its longest-standing Windows bug (#4003, ~1 year), indicating backlog cleanup under pressure.
- **OpenCode's** memory megathread with 124 comments and 96 upvotes suggests a community ready to contribute diagnostics, not just complain.

---

## 6. Trend Signals

| Signal | Evidence | Implication |
|--------|----------|-------------|
| **Multi-agent is the new frontier** | Gemini "agents calling agents," Qwen native coordination RFC, OpenCode nested subagent hangs, DeepSeek Fleet loadouts | Tool builders must solve orchestration reliability (permission rendering, false success reporting, fan-out rate limits) or lose power-user trust. |
| **Session portability is a differentiator** | Codex #5609 (63 👍 for cross-platform sync), Claude Code #28745 (76 👍 for cross-directory resume), Qwen session registry | The tool that lets users take a session anywhere wins enterprise adoption. |
| **MCP is becoming bidirectional** | Gemini #15299 (inbound notifications), Copilot CLI MCP handshake fragility, Qwen SSE GET bug | MCP is evolving beyond tool-calling; bidirectional push models will be critical for agent loops and real-time integrations. |
| **Provider agnosticism is table stakes** | OpenCode model fallback, Kimi MCP metadata fix, Pi multi-provider, Qwen Google GenAI compat | Single-provider lock-in is a growing liability; tools that normalize across providers gain ecosystem reach. |
| **Streaming reliability gaps persist** | Kimi ACP silent hang, OpenCode non-streaming toggle, DeepSeek compaction opacity | Streaming is assumed correct until proven otherwise — silent hangs and missing `[DONE]` frames are trust-eroding. |
| **Enterprise integration is fragile** | Copilot CLI BYOK 403s, Claude Code sandbox bypass, Codex Windows Computer Use regression | Provider tooling for org/enterprise features (BYOK, model policies, remote sessions) is the weakest layer across all incumbent tools. |
| **Extensibility is being stress-tested** | Pi extension command routing, OpenCode OAuth form unification, Qwen Qoder plugins, Gemini skill gaps | The plugin/extension layer is where tools will differentiate — but current implementations are breaking under real-world load. |

---

*Report generated from community digest data across 10 AI CLI tools as of 2026-08-10.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights
*Data as of 2026-08-10 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | PR | Skill / Topic | What It Does | Status |
|---|-----|--------------|-------------|--------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator: run_eval.py recall fix** | Fixes the description-optimization loop that reports `recall=0%` universally due to broken trigger detection on Windows and parallel workers. | 🔴 Open |
| 2 | [#492](https://github.com/anthropics/skills/issues/492) *(Issue, 43 comments)* | **Trust-boundary security: impersonated `anthropic/` namespace skills** | Community-flagged vulnerability where unverified community skills are distributed under the `anthropic/` namespace, posing trust boundary abuse risk. | 🔴 Open |
| 3 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography skill** | Prevents orphan widows, widow paragraphs, and numbering misalignment in AI-generated documents — a universal pain point for every output. | 🔴 Open |
| 4 | [#228](https://github.com/anthropics/skills/issues/228) *(Issue, 16 comments, 8 👍)* | **Org-wide skill sharing in Claude.ai** | Feature request for in-platform skill sharing (links/library) instead of manual `.skill` file distribution via Slack/Teams. | 🔴 Open |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns skill** | Comprehensive testing skill covering the Testing Trophy, unit testing (AAA pattern, pure functions, edge cases), and React component testing. | 🔴 Open |
| 6 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** | Two meta-skills that audit other skills across 5 dimensions (structure, docs, examples, security, accuracy) with weighted scoring. | 🔴 Open |
| 7 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit skill (v1.3.0)** | Pre-delivery quality gate: mechanical file verification first, then four-dimension reasoning audit in damage-severity priority order. Universal across stacks. | 🔴 Open |
| 8 | [#181](https://github.com/anthropics/skills/pull/181) | **SAP-RPT-1-OSS predictor skill** | Skill for SAP's open-source tabular foundation model for predictive analytics on enterprise business data. | 🔴 Open |

> **Note:** All listed PRs remain **open** with no merges to date, indicating a crowded and slow-merging intake pipeline.

---

## 2. Community Demand Trends

From the issues and PRs, four demand clusters emerge:

1. **Skill quality & evaluation tooling** — The #556 `recall=0%` bug (with 7 👍 and 12 comments) and multiple PRs (#1298, #1099, #1050, #1323, #1329) fixing `run_eval.py` and `run_loop.py` show the community urgently needs the skill-creator pipeline to *actually work* before investing in new skills.
2. **Enterprise / document workflows** — Skills for DOCX (#541), ODT (#486), typography (#514), and SAP analytics (#181) indicate strong demand for production document and enterprise-data capabilities.
3. **Security & governance** — Issue #492 (43 comments) and proposals for agent-governance (#412) and self-audit (#1367) signal that trust boundaries, namespace hygiene, and output verification are top-of-mind.
4. **Collaboration & distribution** — Org-wide sharing (#228), MCP-exposed skills (#16), and skill-quality analyzers (#83) all point to a community ready to scale skill adoption beyond individual use.

---

## 3. High-Potential Pending Skills

These PRs have active discussion and clear scope — strong candidates for near-term merge:

| PR | Skill | Why It's Promising |
|----|-------|-------------------|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Solves a universal pre-delivery quality problem; covers any project/stack/model. |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Addresses a near-universal pain point in AI-generated documents; narrow, well-scoped. |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Covers the full testing stack including React; high practical utility. |
| [#302](https://github.com/anthropics/skills/pull/1302) | **color-expert** | Self-contained domain skill for color systems and spaces; unique and well-defined. |
| [#525](https://github.com/anthropics/skills/pull/525) | **pyxel retro-game dev** | Niche but complete workflow (write → run → inspect → iterate); stands out for creativity. |
| [#1479](https://github.com/anthropics/skills/pull/1479) | **plan-file-hygiene** | Directly addresses #1417's lifecycle gap for planning artifacts; solves a real accumulation problem. |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is **reliable skill quality and evaluation tooling** — the skill-creator pipeline itself is broken (recall consistently reports 0%), and until that foundation is fixed, even high-quality new skills struggle to be vetted and merged, creating a bottleneck that cascades into security concerns (unreviewed namespace skills) and stalled enterprise adoption.

---



# Claude Code Community Digest — 2026-08-10

## 1. Today's Highlights

No new releases landed in the past 24 hours. Community attention is concentrated on a cluster of Fable 5 safety-classifier false positives triggering involuntary model downgrades to Opus 4.8, a critical bug where denied tool calls are executed anyway, and a long-standing 76-upvote feature request to decouple conversation resumes from their originating directory.

## 2. Releases

None in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#31413](https://github.com/anthropics/claude-code/issues/31413) | UI language localization support | 13 comments, 8 👍 — Non-English developers have long requested i18n for the UI; still open since March. |
| [#67246](https://github.com/anthropics/claude-code/issues/67246) | Safety-classifier switches model on benign content, can't override with `/model` | 12 comments, 3 👍 — Mid-session silent downgrade to Opus 4.8 blocks workflow; `/model` override is non-functional. |
| [#28745](https://github.com/anthropics/claude-code/issues/28745) | Allow resuming conversations from different directories | 11 comments, **76 👍** — Conversations locked to original cwd; deleted worktrees or renamed dirs orphan the session forever. |
| [#72248](https://github.com/anthropics/claude-code/issues/72248) | Workflow tool delivers JSON args as string instead of parsed object | 10 comments, 1 👍 — Violates the documented "verbatim" contract; scripts receive a JSON-encoded string rather than a parsed dict/list. |
| [#83913](https://github.com/anthropics/claude-code/issues/83913) | Prompt cache invalidated when PreToolUse/PostToolUse additionalContext changes | 5 comments, 4 👍 — History rebuilds strip previously cached context, forcing full rewrites at cache-write rate on every turn. |
| [#85286](https://github.com/anthropics/claude-code/issues/85286) | Assistant fabricates conversation turns and role markers | 4 comments — The model runs past its own turn, generating fake user/system/tool blocks that corrupt session history. |
| [#84981](https://github.com/anthropics/claude-code/issues/84981) | Background tasks SIGTERMed on exact 30-minute internal timer | 3 comments — Undocumented kill path; `run_in_background: true` tasks are silently terminated every 1800s with exit 144. |
| [#85401](https://github.com/anthropics/claude-code/issues/85401) | Sessions execute destructive commands against shared host/remote resources | 1 comment — Safety sandbox can be bypassed, posing risk in multi-user or shared-host environments. |
| [#85398](https://github.com/anthropics/claude-code/issues/85398) | Stale persisted state (credentials, permissions, memory) | 1 comment — Credentials and permission grants persist across sessions despite changes, creating security drift. |
| [#85417](https://github.com/anthropics/claude-code/issues/85417) | Claude forgets outstanding to-do list items after multi-turn compactions | 0 comments — Long-running tasks with auto-generated checklists lose track of remaining items post-compaction. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#9262](https://github.com/anthropics/claude-code/pull/9262) | docs: enforce task tool and model metadata | **CLOSED** | Documents `claude-3-5-haiku-latest` via the `model` parameter on commit; enforces Task tool for context isolation. |
| [#85409](https://github.com/anthropics/claude-code/pull/85409) | security-guidance: update default model refs | OPEN | Updates hardcoded Opus 4.7 / Sonnet 4.6 references to Opus 5 / Sonnet 5 across the `security-guidance` plugin and `llm.py`. |
| [#85323](https://github.com/anthropics/claude-code/pull/85323) | fix(plugin-dev): parse block scalar agent descriptions | OPEN | Fixes YAML block-scalar parsing for multiline `description: \|` / `description: >` values in agent manifests. |
| [#17395](https://github.com/anthropics/claude-code/pull/17395) | [Plugin] Add `agent-session-commit` plugin | **CLOSED** | Introduces incremental `AGENTS.md` iteration via `/session-commit` manual trigger and Stop-hook auto-prompt. |
| [#85243](https://github.com/anthropics/claude-code/pull/85243) | fix(skills): use spec-conformant names in plugin-dev and hookify skills | OPEN | Corrects eight bundled skills that declared title-cased, space-containing `name` fields violating the spec. |

> Only 5 PRs were available in the 24h window; all five are listed above.

## 5. Feature Request Trends

- **Cross-directory conversation resumes** (#28745, 76 👍) — The single most-upvoted open issue; users want sessions to survive directory moves, renames, and worktree deletions.
- **UI localization / i18n** (#31413, 8 👍) — Sustained demand for non-English interface support.
- **Pinned-session protection** (#62104, closed) — Community pushed for preventing archive/delete of pinned sessions; the fix was merged.
- **Effort-level observability for subagents** (#85416) — New request to surface whether `effort:` frontmatter actually applies to background-dispatched subagents.

## 6. Developer Pain Points

1. **Safety classifier false positives halting work** — A cluster of issues (#67246, #85375, #85390–#85392, #85414, #85415) report Fable 5 / Opus 4.8 flagging benign or defensive-security content and forcing involuntary model downgrades. Users report no reliable override mechanism.
2. **Undocumented hard limits killing background work** — The exact 30-minute SIGTERM on background tasks (#84981) and the silent cache invalidation on history rebuilds (#83913) frustrate long-running workflows with no graceful exit or warning.
3. **Permission and sandbox bypasses** — Denied tool calls executing anyway (#83760), destructive commands targeting shared resources (#85401), and stale persisted credentials (#85398) raise security concerns for team and CI environments.
4. **Data loss from retention policies** — Desktop transcript sweeps deleting the only copy of sessions while leaving unopenable ghost entries (#81100) and to-do list items vanishing after compactions (#85417) cause real work loss.
5. **Directory-locked sessions** — The persistent inability to resume conversations outside their original working directory (#28745) remains the top community grievance, with 76 upvotes and no resolution.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-10

## 1. Today's Highlights

The most significant activity today centers on Windows line-ending preservation in `apply_patch` (PR #37757, closing issue #4003 after nearly a year), and a cluster of Windows Computer Use failures all pointing to `EnumWindows` error `0x80070003` across multiple recent reports. On the extension side, prompts disappearing in the VS Code/Cursor queue (#25928) and the extension failing to load resources (#37458) are generating notable friction.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

**#4003 — Patched files have mixed line endings on Windows** (33 comments, 74 👍) [CLOSED]
> The longest-standing Windows pain point: Codex normalizes line endings on `apply_patch`, silently rewriting CRLF files to LF. Closed today alongside the fix PRs. The 74 upvotes reflect community relief.

**#25928 — VS Code/Cursor Codex Extension: Submitted Prompts Randomly Disappear Before Entering Queue** (25 comments, 17 👍) [OPEN]
> Users on Cursor and VS Code report prompts vanishing before they're enqueued — a critical reliability issue for extension workflows. No resolution yet; the author is on ChatGPT Pro 20x.

**#37458 — Codex extension fails to start: "The extension couldn't load its resources"** (24 comments, 0 👍) [OPEN]
> A fresh report (filed Aug 7) where the Codex panel refuses to start after a VS Code update on Windows. Suggests a regression in the extension's resource-loading path.

**#11011 — Switching between threads is very slow** (22 comments, 19 👍) [OPEN]
> A persistent performance grievance: thread-switching latency in the Codex app is degrading daily use. Over 22 comments with no fix deployed.

**#37043 — Windows Computer Use fails at EnumWindows with 0x80070003** (18 comments, 4 👍) [OPEN]
> Part of a growing wave of Windows Computer Use failures. `sky.list_apps()` and `sky.list_windows()` both fail with "system cannot find the path specified." Multiple variants reported this week.

**#15299 — Support inbound MCP notifications routed into an active Codex CLI session** (15 comments, 14 👍) [OPEN]
> A feature request for pushing inbound MCP notifications (e.g., channel events) into a running CLI session. Highlights the growing use of MCP as a bidirectional interface.

**#37180 — Windows Computer Use approval prompt never appears; `launch_app` fails with `node_repl exec context not found`** (11 comments, 6 👍) [OPEN]
> Companion to the EnumWindows failures — the approval UI never surfaces, and app launch fails at the Node REPL context layer. Affects the Microsoft Store build.

**#37383 — Computer Use on Windows fails during app/window discovery with 0x80070003** (11 comments, 4 👍) [OPEN]
> Third distinct report this week of the same `EnumWindows` crash on Windows 11 25h2. The pattern suggests a regression in the bundled `@oai/sky` runtime (0.6.2).

**#20802 — Slow thread switching / loading on Codex macOS desktop app (v26.429.30905, regression)** (8 comments, 5 👍) [CLOSED]
> macOS counterpart to #11011. Filed after an update; now closed, suggesting a fix landed — but the broader thread-switching performance issue (#11011) remains open.

**#5609 — Sync my chats, conversation history between ChatGPT website, Codex in VSCode** (6 comments, 63 👍) [OPEN]
> A high-engagement feature request spanning nearly a year. Users want seamless conversation continuity across the ChatGPT web app, VS Code extension, and GitHub Codespaces.

## 4. Key PR Progress

**#37758 — Add a feature flag to preserve apply_patch line endings** [CLOSED]
> Introduces `apply_patch_preserve_line_endings` (disabled by default) to preserve CRLF, CR, and mixed line endings. Addresses #4003.

**#37757 — Add a line-ending preservation mode to `apply_patch`** [CLOSED]
> Opt-in `PreserveLineEndings` update mode threaded through the patch engine. Works alongside #37758's feature flag.

**#37747 — Bound Cursor project path resolution** [CLOSED]
> Fixes a performance issue where resolving a Cursor project name could recursively scan large directory trees. Now probes a bounded set of path candidates instead.

**#37745 — Add gRPC TCP transport to the code-mode host** [CLOSED]
> The code-mode host now accepts `grpc://IP:PORT` endpoints via `--listen`, serving the gRPC service over raw TCP. Useful for custom integration scenarios.

**#37723 — Report I/O subtypes for session config import failures** [CLOSED]
> `failed_to_load_session_config` errors now include a stable `std::io::ErrorKind` category (`invalid_data`, `not_found`, `permission_denied`), improving debuggability.

**#37709 — Keep wrapped composer whitespace with following text** [CLOSED]
> Fixes a TUI composer rendering bug where overflowing whitespace occupied a separate blank row instead of staying attached to the following text.

**#37654 — Advertise environment config read support** [CLOSED]
> Adds `environmentConfigRead` to the exec-server environment capabilities and advertises it for local executors. Backward-compatible with legacy responses defaulting to `false`.

**#31817 — Update models.json** [OPEN]
> Automated model registry update. No substantive changes.

## 5. Feature Request Trends

- **Cross-platform conversation sync** (#5609, 63 👍) remains the top unaddressed desire — users want threads to flow seamlessly between web, desktop, and IDE.
- **MCP as a bidirectional pipe** (#15299) — the community is pushing for inbound notification support, not just tool-calling out from Codex.
- **Model alias mapping for enterprise gateways** (#21594) — a niche but vocal request from enterprise users who need gateway model names to resolve to canonical Codex metadata.
- **Multi-agent steering** (#33885) — allowing child threads to accept corrections from the parent agent, enabling more interactive sub-agent workflows.

## 6. Developer Pain Points

- **Windows line endings** (#4003): A near-year-old bug that silently rewrote CRLF files. Finally closed today, but the community frustration is palpable (74 👍).
- **Windows Computer Use instability**: Four distinct issues this week (#37043, #37180, #37383, #37595) all tracing back to `EnumWindows` returning `0x80070003`. This is a clear regression in the `@oai/sky` runtime on Windows 11.
- **Extension reliability** (#25928, #37458): Prompts disappearing and extensions failing to load are high-severity UX breaks that erode trust in the IDE integration.
- **Thread-switching latency** (#11011, #20802): A cross-platform performance regression affecting both macOS and Windows, with no unified fix yet.
- **Session config fragility** (#33163): Reusing dead WebSocket connections after network loss breaks the next turn — a reliability gap in the CLI transport layer.
- **Zombie subprocesses** (#37311): The macOS app leaks idle child processes, a memory/leak concern for long-running sessions.

---

*Digest generated from github.com/openai/codex data as of 2026-08-10.*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-10

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly.20260810 shipped with a major dependency overhaul (74 npm packages updated, `@google/genai` bumped to v2.15.0). Community attention centered on agent reliability — subagent recovery misreporting successes, persistent `--resume` crashes on terminal resize, and skills/subagent adoption gaps remain top concerns. A key fix for `--resume` session poisoning and a new "agents calling agents" capability are in review.

---

## 2. Releases

**v0.56.0-nightly.20260810.gcf22ac7e8** — Nightly build with extensive dependency updates including `@google/genai` 1.30→2.15, `puppeteer-core` 24→25.4, `@modelcontextprotocol/sdk` 1.23→1.30, `@a2a-js/sdk` 0.3→1.0, and 74 total npm updates.
- [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.56.0-nightly.20260809.gcf22ac7e8...v0.56.0-nightly.20260810.gcf22ac7e8)

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | 12 | 2 | `codebase_investigator` falsely reports `status: success` when it hits max turns — masks failures and misleads downstream agent logic. |
| [#27373](https://github.com/google-gemini/gemini-cli/issues/27373) | `gemini --resume` crashes with `ioctl(2) failed, EBADF` | 11 | 0 | Terminal resize during session restore triggers a crash. **Closed** — likely fixed in a recent release. |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | 7 | 0 | Epic tracking 76 behavioral evals across 6 supported Gemini models — critical for quality assurance before wider rollout. |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | 7 | 1 | Investigating whether AST-aware tools can reduce turn count and token noise by reading precise method bounds. |
| [#27370](https://github.com/google-gemini/gemini-cli/issues/27370) | `activate_skill` missing from tool list in v0.43 | 6 | 0 | Built-in tools like `activate_skill`, `google_web_search`, `web_fetch` no longer listed — regression affecting skill-based workflows. **Closed.** |
| [#27023](https://github.com/google-gemini/gemini-cli/issues/27023) | Prorated refund request — Gemini 3.1 Pro quality issues | 6 | 1 | Paying AI Ultra subscriber cites persistent quality problems. Reflects growing enterprise-user friction. **Closed.** |
| [#27419](https://github.com/google-gemini/gemini-cli/issues/27419) | `shellExecutionService` non-interactive stability | 6 | 0 | Three critical bugs: hangs in non-interactive loops, non-UTF-8 byte handling, and buffer-to-string heap overflows. Impacts agent-loop reliability. **Closed.** |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents autonomously | 6 | 0 | Users report the agent ignores custom skills (e.g., gradle, git) unless explicitly told — a significant UX gap for power users. |
| [#27431](https://github.com/google-gemini/gemini-cli/issues/27431) | Cannot connect to different MCP servers | 5 | 0 | No error message when MCP connections fail — silent failures make debugging impossible. **Closed.** |
| [#27764](https://github.com/google-gemini/gemini-cli/issues/27764) | Terminal resize issue after `--resume` | 5 | 0 | Duplicate of #27373 — `ioctl(2) failed, EBADF` when resizing terminal post-resume. Open but likely stale. |

---

## 4. Key PR Progress

| # | Title | Author | Status | Summary |
|---|-------|--------|--------|---------|
| [#28624](https://github.com/google-gemini/gemini-cli/pull/28624) | Fix: prevent boolean thought parts leaking as `[Thought: true]` | Rajeev91691 | Open | Fixes #23525 — boolean `thought` parts were rendering as literal text in model output. Core correctness fix. |
| [#28744](https://github.com/google-gemini/gemini-cli/pull/28744) | Fix: don't start fresh chat before resuming | PranavMishra28 | Open | Fixes #28693 — `loadSession` was calling `initialize()` before `resumeChat()`, poisoning the session file with empty state. |
| [#28738](https://github.com/google-gemini/gemini-cli/pull/28738) | Allow agents to call agents | akash-manna-sky | Open | Fixes #22092 — enables subagents to delegate to other subagents or recurse via `tools:` frontmatter. Major capability unlock. |
| [#28743](https://github.com/google-gemini/gemini-cli/pull/28743) | Fix: preserve resolved model config systemInstruction and tools | kunalrawat425 | Open | Fixes config overwrite bug where `GeminiChat.sendMessageStream()` was discarding model-specific `systemInstruction` and `tools`. |
| [#28742](https://github.com/google-gemini/gemini-cli/pull/28742) | Fix: spec-valid names for triage-worker skills | bechor25 | Open | Underscores in skill names violated the Agent Skills spec. Two caretaker-agent skills renamed. |
| [#28758](https://github.com/google-gemini/gemini-cli/pull/28758) | chore: bump version to 0.56.0-nightly.20260810 | gemini-cli-robot | Open | Automated nightly version bump. |
| [#28746](https://github.com/google-gemini/gemini-cli/pull/28746) | chore: bump 74 npm dependencies | dependabot | Closed | Large dependency sweep: `simple-git` 3.28→3.36, `@modelcontextprotocol/sdk` 1.23→1.30, and many more. |
| [#28749](https://github.com/google-gemini/gemini-cli/pull/28749) | chore: bump `@google/genai` 1.30→2.15 | dependabot | Closed | Major version bump to the core GenAI SDK — likely brings new model features and API changes. |
| [#28752](https://github.com/google-gemini/gemini-cli/pull/28752) | chore: bump `puppeteer-core` 24→25.4 | dependabot | Closed | Browser automation dependency updated; relevant to browser agent stability. |
| [#28747](https://github.com/google-gemini/gemini-cli/pull/28747) | chore: bump `@a2a-js/sdk` 0.3→1.0 | dependabot | Closed | A2A protocol SDK reached v1.0 — signals stabilization of agent-to-agent communication layer. |

---

## 5. Feature Request Trends

- **Agent autonomy & composability** — Users want the model to independently choose skills/subagents (#21968) and for agents to compose recursively (#28738). The "agents calling agents" PR directly addresses this.
- **AST-aware codebase understanding** — Multiple issues (#22745, #22746) push for AST-based reads and mapping to reduce token waste and improve precision in `codebase_investigator`.
- **Evaluation & quality infrastructure** — Component-level evals (#24353) and subagent trajectory sharing via `/chat share` (#22598) show demand for better observability and testing.
- **Auto Memory reliability** — Three related issues (#26522, #26523, #26525) target Auto Memory: infinite retry on low-signal sessions, invalid patch handling, and deterministic redaction/logging reduction.
- **Non-interactive / headless stability** — Shell execution hangs (#27419, #25166), non-UTF-8 byte handling, and `enableInteractiveShell` compliance are recurring themes for CI/agent-loop users.

---

## 6. Developer Pain Points

1. **`--resume` instability** — Terminal resize crashes (`EBADF`) and session poisoning on resume are repeat complaints (#27373, #27764, #28744). Multiple users hit this; the fix PR (#28744) is promising.
2. **Subagent reliability** — False success reporting (#22323), missing permissions (#22093), browser agent failures on Wayland (#21983), and settings.json overrides being ignored (#22267) all point to a fragile subagent layer.
3. **Skill/tool discovery gaps** — Skills and subagents aren't used autonomously (#21968), `activate_skill` vanished from the tool list in v0.43 (#27370), and MCP connection failures are silent (#27431).
4. **Shell execution hangs** — Commands completing but leaving the agent stuck at "Awaiting user input" (#25166) and non-interactive loop hangs (#27419) disrupt automated workflows.
5. **Auto Memory quality** — Low-signal sessions retried indefinitely (#26522), invalid patches silently skipped (#26523), and secret redaction happening too late (#26525) erode trust in the memory system.
6. **Tool limit errors** — 400+ tools trigger a 400 error (#24246); users expect smarter scoping rather than a hard failure.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-10

---

## 1. Today's Highlights

A wave of fresh issues landed overnight, dominated by MCP handshake and initialization failures, model catalog regressions, and session lifecycle bugs. Community engagement remains strongest on the long-standing request to cancel enqueued messages before execution (#1857, 26 👍), while several new triage items in the 4400s range flag production-impacting regressions around Claude model availability and BYOK 403 errors.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | 👍 | Why It Matters |
|---|-------|-----|----------------|
| [#1857](https://github.com/github/copilot-cli/issues/1857) | Allow users to cancel or remove enqueued messages before they are executed | 26 | Long-requested UX improvement — messages queued via `Ctrl+Q` / `Ctrl+Enter` currently execute unconditionally once the agent is free, with no escape hatch. |
| [#2751](https://github.com/github/copilot-cli/issues/2751) | `Remote session disabled: could not resolve repository` on org repos | 13 | Blocks `/remote` usage for organization-owned repositories; affects v1.0.28+ and limits remote session adoption in enterprise settings. |
| [#4422](https://github.com/github/copilot-cli/issues/4422) | All Claude models disabled under CLI model selection | — | Enterprise users report a sudden regression: Claude Sonnet 5/4.8 models are unavailable despite being enabled in Copilot settings. Rollback did not help. |
| [#4390](https://github.com/github/copilot-cli/issues/4390) | Enabled organization models missing from catalogue (Claude Sonnet 5/Opus 5/Kimi K3) | 1 | Anthropic models return "This model is disabled" errors even when explicitly enabled for Copilot Business orgs — a related catalog-resolution bug. |
| [#4421](https://github.com/github/copilot-cli/issues/4421) | MCP initialize handshake has a fixed 60 s budget with no retry | — | npx-launched stdio servers fail to initialize in ~29 % of sessions and are never respawned for the session lifetime — a critical reliability gap. |
| [#4370](https://github.com/github/copilot-cli/issues/4370) | Copilot CLI 1.0.79-1 fails MCP initialization when `server/discover` returns -32602 | 1 | FastMCP-compliant servers that don't implement `server/discover` are treated as failed; hard break for a growing class of MCP implementations. |
| [#4414](https://github.com/github/copilot-cli/issues/4414) | BYOK custom providers return local 403 before requests reach provider | — | Custom OpenAI/Anthropic-compatible providers are blocked with a spurious authorization error; `/login` does not resolve it, indicating a routing/permission bug. |
| [#4416](https://github.com/github/copilot-cli/issues/4416) | Parallel explore subagent fan-out dies to per-model 429s | — | All parallel explore agents default to the same lightweight model bucket, hitting tight burst limits with no auto-switch or backoff — a scaling blocker for fleet operations. |
| [#4420](https://github.com/github/copilot-cli/issues/4420) | Parallel tool calling non-deterministic response order confuses bots | — | The harness drops request correlation for parallel tool calls, returning orphan responses and causing downstream agent confusion. |
| [#4419](https://github.com/github/copilot-cli/issues/4419) | Managed-settings interim fail-closed drops user MCP servers | — | During managed-settings resolution, an empty allow-list `([])` is applied as a deny-everything policy, permanently rejecting any MCP server registering in that window — even on accounts with no managed policy. |

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **Message control & session UX** — Users want the ability to cancel or dequeue messages before execution (#1857), and a more visible, configurable session HUD (#4418, #4417) to reduce confusion during prompt entry.
- **Model selection & auto-mode configurability** — Requests for finer-grained control over auto-mode (min/max model strength, bias settings) (#4412) and reliable model catalogue population across enterprise/org scopes (#4390, #4422).
- **Non-GitHub remote sessions** — `/remote` should work with GitLab, Bitbucket, and other hosts (#2922), decoupling session control from the git provider.
- **Internationalization** — Localized UI for Chinese (zh-CN) and other languages is requested (#4407).
- **MCP configurability** — Longer timeout budgets, retry/backoff, and configurable hub URLs (#4421, #4418) are recurring themes.

---

## 6. Developer Pain Points

| Pain Point | Related Issues |
|------------|---------------|
| **MCP initialization fragility** — Hardcoded 60 s timeouts, no retries, and strict `server/discover` requirements break common MCP server patterns (npx-launched, FastMCP, OAuth 3LO). | #4421, #4370, #4371, #4419 |
| **Model availability regressions** — Claude models disappear from the CLI catalogue for enterprise/org users with no clear recovery path; BYOK providers are silently rejected with 403s. | #4422, #4390, #4414 |
| **Parallel execution instability** — Fan-out of subagents or parallel tool calls hits rate limits or loses response correlation, producing flaky or confused agent behavior. | #4416, #4420 |
| **Remote session limitations** — `/remote` fails on organization repos and non-GitHub hosts, limiting cross-platform and enterprise workflows. | #2751, #2922 |
| **Session lifecycle bugs** — Kickoff prompts are silently dropped (#4423), subtasks freeze mid-execution (#4306), and `session.resume` replays stale provider metadata (#4413). | #4423, #4306, #4413 |
| **Opaque error states** — Settings like `cli_remote_control_enabled` show no feedback when disabled (#4409), and enterprise MCP authentication fails with cryptic cross-origin errors (#4408). | #4409, #4408 |

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026‑08‑10

## 1. Today’s Highlights
A new bug report (#2598) surfaces a silent‑hang issue in ACP streaming mode where completed responses never close the wire, leaving clients blocked with no idle‑timeout fallback. Meanwhile, the long‑standing memory‑system feature request (#1283) continues to gather interest, reflecting ongoing demand for persistent cross‑session context. A compatibility fix (#739) for Google GenAI tool parameters also saw recent activity, addressing validation errors with MCP tools that emit standard JSON‑Schema metadata.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
1. **#1283 – Memory System: Persistent context across sessions**  
   *Why it matters:* Users repeatedly request a way to retain project patterns, preferences, and AI‑managed notes between CLI invocations. The feature would bridge the gap between stateless tool calls and cohesive, multi‑session workflows.  
   *Community reaction:* 27 comments, 0 👍; discussion has been steady but no consensus on implementation scope.  
   [View on GitHub](https://github.com/MoonshotAI/kimi-cli/issues/1283)

2. **#2598 – ACP/print streaming response hangs silently**  
   *Why it matters:* In ACP mode (`kimi acp`), clients can receive all content deltas yet never see the `[DONE]`/finish frame. The absence of an idle‑timeout configuration causes the session to block indefinitely, and any subsequent user message silently replaces the hung wheel without persisting the partial response to `wire.jsonl`. This breaks reliability for streaming‑heavy workflows.  
   *Community reaction:* Opened today, 0 comments, 0 👍; likely still being triaged.  
   [View on GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2598)

*Note:* Only two issues were updated in the last 24 hours; the digest therefore cannot yet present a broader “top‑10” ranking.

## 4. Key PR Progress
1. **#739 – fix(kosong): strip JSON Schema metadata from Google GenAI tool parameters**  
   *What it does:* Removes extraneous JSON‑Schema metadata fields from tool definitions when routing requests through the Google GenAI provider. This resolves validation errors that occur with MCP tools (e.g., Exa MCP) that include standard metadata alongside functional parameters.  
   *Impact:* Unblocks users who combine Google GenAI as a provider with MCP‑style tool servers, improving cross‑provider compatibility.  
   [View on GitHub](https://github.com/MoonshotAI/kimi-cli/pull/739)

*Note:* Only one PR was updated in the reporting window; additional PRs will appear as the repository activity expands.

## 5. Feature Request Trends
- **Persistent session memory** – The #1283 request for an automatic/manual memory system indicates a clear trend toward stateful, context‑aware CLI experiences. Users want the tool to remember project conventions, prior decisions, and user‑defined instructions without re‑entering them each session.
- **Streaming‑mode reliability** – Issue #2598 highlights a demand for robust streaming behavior, including configurable idle timeouts and guaranteed delivery of partial results when connections hang.
- **Cross‑provider MCP compatibility** – PR #739 addresses a recurring friction point where MCP tools emit standard JSON‑Schema metadata that breaks non‑OpenAI providers. The community expects continued effort to normalize tool‑parameter shapes across providers.

## 6. Developer Pain Points
- **Silent streaming hangs with no timeout control** – Clients using ACP mode currently have no way to configure an idle timeout; when the server stops sending frames after content completion, the CLI blocks indefinitely and may drop the partial response without persisting it.
- **MCP‑tool metadata incompatibility** – Tools that adhere to standard JSON‑Schema metadata (e.g., `title`, `description`, `examples`) cause validation failures on providers like Google GenAI that expect cleaner parameter definitions.
- **Lack of session‑state persistence** – Without a memory system, developers must manually re‑provide context, project patterns, and preferences in every new CLI session, reducing productivity and increasing prompt‑engineering overhead.

---
*Digest generated from GitHub data for MoonshotAI/kimi-cli (last 24 hours). Activity volume is low; the sections “Hot Issues” and “Key PR Progress” currently reflect only the two most recent items.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-10

## 1. Today's Highlights

OpenCode continues to see significant community engagement around reliability and provider compatibility, with the Memory Megathread (#20695) and clipboard bug (#4283) remaining the most discussed issues. A cluster of DeepSeek V4 Flash bugs on OpenCode Go surfaced this week, all stemming from a leading-space issue in model-name relay validation, while PR activity focused on session robustness, renderer performance, and V2 integration refinements.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| #20695 | [Memory Megathread](https://github.com/anomalyco/opencode/issues/20695) | Centralized tracking for scattered OOM/heap-leak reports across sessions; the team is requesting heap snapshots rather than speculative fixes. | 124 comments · 96 👍 — highest engagement on record; active collaboration. |
| #4283 | [Copy To Clipboard not working](https://github.com/anomalyco/opencode/issues/4283) | Text selection in responses fails to write to clipboard, breaking a core copy-paste workflow across all platforms. | 122 comments · 110 👍 — widely felt pain point. |
| #7602 | [Native Model Fallback / Failover](https://github.com/anomalyco/opencode/issues/7602) | No cross-model fallback exists today; long-running agents stall when a provider rate-limits or errors. | 29 comments · 107 👍 — strong demand for resilience. |
| #785 | [Disable Streaming Mode](https://github.com/anomalyco/opencode/issues/785) | Some proxy providers (e.g. Credal OpenAI) don't support streaming, blocking users from those endpoints. | 29 comments · 38 👍 — practical compatibility gap. |
| #24649 | [Clarify self-hosted vs. proxied models (Go)](https://github.com/anomalyco/opencode/issues/24649) | Documentation ambiguity around OpenCode Go's infrastructure claims; users need clarity for compliance and cost planning. | 18 comments · 32 👍 — transparency request. |
| #34743 | [ACP from Xcode ignores model config](https://github.com/anomalyco/opencode/issues/34743) | Xcode 27 beta ACP integration uses `big-pickle` instead of the model specified in `opencode.json`, breaking local-model workflows. | 15 comments · 0 👍 — niche but blocking for macOS/Xcode users. |
| #13715 | [Nested subagent permission hangs](https://github.com/anomalyco/opencode/issues/13715) | Permission prompts from sub-subagents are never rendered, causing silent hangs indefinitely. | 11 comments · 24 👍 — correctness issue in agent orchestration. |
| #41300 / #41314 / #41306 / #41322 | [DeepSeek V4 Flash — leading space / HTTP 400 cluster](https://github.com/anomalyco/opencode/issues/41300) | A relay bug injects a leading space into `deepseek-v4-flash`, causing upstream 400 errors across Go and Console endpoints. | 6 + 3 + 4 + 3 comments — rapid fire from affected users; partially resolved but regression reported. |
| #39931 | [bash permission escape via `--`](https://github.com/anomalyco/opencode/issues/39931) | Commands containing `--` bypass `"bash": "ask"` permission checks — a security-relevant edge case. | 2 comments · 0 👍 — low visibility but high severity if exploited. |
| #41430 | [Go payment processed but subscription inactive](https://github.com/anomalyco/opencode/issues/41430) | Stripe payment completes but dashboard doesn't reflect Go subscription, blocking paid users. | 3 comments · 0 👍 — billing friction. |

---

## 4. Key PR Progress

| # | PR | Description |
|---|----|-------------|
| #41463 | [fix: omit tool defs for models that cannot call tools](https://github.com/anomalyco/opencode/pull/41463) | `resolveTools` was declaring tools for every model regardless of `capabilities.toolcall`; now correctly skips them. |
| #41460 | [chore: merge dev into v2](https://github.com/anomalyco/opencode/pull/41460) | Synchronizes `dev` changes into the V2 branch, preserving App/Desktop/Core/TUI/SDK architecture and V2 session export. |
| #38067 | [fix: edge-trigger build-switch reminder](https://github.com/anomalyco/opencode/pull/38067) | Replaces full-session-history scan with an edge-triggered check for the "plan → build" mode-change reminder. |
| #37584 | [fix: bound consecutive overflow compaction cycles](https://github.com/anomalyco/opencode/pull/37584) | Prevents infinite compaction loops when a provider rejects a turn due to context overflow. |
| #40427 | [experimental perf improvements](https://github.com/anomalyco/opencode/pull/40427) | Renderer entry size reduced from 7.45 MB to 1.82 MB (−75.5%) using immutable partial DB snapshots and a 24h corpus window. |
| #41350 | [feat: animated BusyWave loading indicator](https://github.com/anomalyco/opencode/pull/41350) | Replaces the shimmering "Thinking" label with a persistent TUI-inspired wave animation. |
| #39358 | [feat: durable session archival](https://github.com/anomalyco/opencode/pull/39358) | Adds a first-class `session.archived` fact with idempotent archival; separate from deletion to preserve context. |
| #40997 | [refactor: replace integration prompts with forms](https://github.com/anomalyco/opencode/pull/40997) | OAuth/key answers now use shared `Form.Fields` definitions validated in Core, unifying GitHub Copilot, Azure, and Cloudflare integrations. |
| #41450 | [fix: derive fallback message for empty AI SDK errors](https://github.com/anomalyco/opencode/pull/41450) | `AI_APICallError` with an empty `message` now surfaces structured details (`statusCode`, rate-limit headers) in the TUI instead of a blank error. |
| #41455 | [fix: include attachment path in model context](https://github.com/anomalyco/opencode/pull/41455) | Preserves a local attachment's `source.path` as text before the binary image, so providers that need the path can access it. |

---

## 5. Feature Request Trends

- **Resilience & failover** — Model fallback (#7602), persistent session daemon (#41453), and bounded compaction (#37584) all point to demand for agents that survive provider outages and context-pressure loops.
- **Session control & history** — Reverting question answers (#25555), durable archival (#39358), and clearer `/clear` semantics (#38392) reflect users wanting finer-grained conversation manipulation.
- **Provider compatibility depth** — Streaming toggle (#785), reasoning-options forwarding (#27361, #41294), and Ollama reasoning-field support (PR #36068) show the community pushing OpenCode to work reliably with diverse and non-standard providers.
- **UX polish** — Clipboard fixes (#4283, #39588), code-concealment defaults (#35093), and loading animations (#41350) indicate ongoing investment in surface-level workflow friction.

---

## 6. Developer Pain Points

1. **Clipboard & copy-paste broken on multiple surfaces** — Desktop (#4283) and VS Code extension on macOS (#39588) both report non-functional copy/paste, a high-frequency blocker.
2. **Provider-model name leakage / validation bugs** — The DeepSeek V4 Flash leading-space incident (#41300, #41314, #41306, #41322) reveals fragile relay validation that silently corrupts model strings.
3. **Streaming not universally supported** — Users behind proxies that lack streaming (#785) have no workaround, limiting provider choice.
4. **Nested-agent permission deadlocks** — Sub-subagent permission prompts never render (#13715), causing indefinite hangs with no visible feedback.
5. **Xcode ACP ignoring `opencode.json`** — The ACP integration defaults to `big-pickle` instead of the configured model (#34743), breaking local-model workflows on macOS.
6. **Free-tier rate limits appearing inconsistently** — Multiple users report free models becoming unavailable mid-session while direct API calls still work (#32971, #41448, #41414), suggesting a throttling or session-state bug.
7. **bash permission bypass via `--`** — A security-adjacent edge case (#39931) where double-hyphen arguments escape `"bash": "ask"` prompts.
8. **Billing sync delays** — Payment-processed-but-subscription-inactive reports (#41430) indicate friction in the Go subscription provisioning pipeline.
9. **TUI startup freezes** — Blank-screen hangs on macOS require force-kill (#41284), and Windows hangs without admin elevation (#41436) point to platform-specific initialization issues.
10. **Memory pressure** — The megathread (#20695) with 96 upvotes confirms that OOM and heap growth remain unresolved systemic concerns.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-10

## Today's Highlights

Pi 0.84.x continues to see a burst of activity as the community reports and fixes TUI rendering issues, Copilot login rate-limiting bugs, and llama.cpp startup race conditions. A new remote session wire protocol (`@earendil-works/pi-protocol`) was merged, and several critical agent-session fixes landed for extension command routing, structured argument validation, and context-file exposure.

---

## Releases

No new releases in the last 24 hours.

---

## Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#6922](https://github.com/earendil-works/pi/issues/6922) | Default model cannot be a llama.cpp model: "No models available" | Blocks users who want llama.cpp as their default provider; startup fails interactively or exits non-interactively. | 10 comments · 14 👍 |
| [#7730](https://github.com/earendil-works/pi/issues/7730) | High CPU usage on Mac OS with long session | 50–110% CPU swing on macOS during extended sessions; memory at 600–800 MB. Suggests a potential context/length-related loop. | 6 comments · 6 👍 |
| [#6948](https://github.com/earendil-works/pi/issues/6948) | llama.cpp defaultProvider/defaultModel not applied at startup (race condition) | Async model refresh races with session init — model appears in `/model` after start but session doesn't use it. Fixed in PR #7072. | 4 comments |
| [#7720](https://github.com/earendil-works/pi/issues/7720) | Allow disabling select-to-copy in fullscreen TUI | Terminal power users lose clipboard content when accidentally selecting text. Directly addressed by PR #7866. | 4 comments |
| [#7323](https://github.com/earendil-works/pi/issues/7323) | `pi update --models` fails entire refresh on transient stall | A single stalled HTTPS request to `pi.dev` aborts the whole model catalog refresh; no retry logic. | 4 comments |
| [#3159](https://github.com/earendil-works/pi/issues/3159) | Edit tool terminated — timeout | Qwen 27B (and other models) hit edit-tool timeouts; users report it's a persistent regression with fresh versions. | 4 comments · 0 👍 |
| [#7616](https://github.com/earendil-works/pi/issues/7616) | Chat scroll jumps when tool blocks grow above viewport | Differential renderer triggers a full-screen clear on viewport mismatch, losing the user's scroll position mid-session. | 3 comments |
| [#7740](https://github.com/earendil-works/pi/issues/7740) | TUI after `/reload` ignores custom tool render callbacks | Tools registered on `session_start` lose rendering state after reload — breaks MCP and similar extensions. | 3 comments |
| [#7869](https://github.com/earendil-works/pi/issues/7869) | AI21 API broken (retired) | AI21 Gateway retired; users get a hard 410 error. Needs deprecation from the built-in provider list. | 2 comments |
| [#7864](https://github.com/earendil-works/pi/issues/7864) | `ExtensionContext.exec` timeout never force-kills SIGTERM-ignoring child | Node reports `killed: true` when SIGTERM is sent, not when the process exits. SIGKILL escalation is skipped, leaving zombie processes. | 2 comments |

---

## Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#7872](https://github.com/earendil-works/pi/pull/7872) | Expose context files at session start | Feature | Exposes AGENTS/CLAUDE context files on `session_start`; enables extensions to read them at init time. |
| [#7072](https://github.com/earendil-works/pi/pull/7072) | Cache llama.cpp model catalog | Fix | Caches the llama.cpp catalog to resolve the race condition in #6948; model is available immediately at startup. |
| [#7866](https://github.com/earendil-works/pi/pull/7866) | Add `copyOnSelect` option to TuiAltScreen | Feature | Allows disabling the automatic clipboard copy on mouse selection in fullscreen TUI (addresses #7720). |
| [#7865](https://github.com/earendil-works/pi/pull/7865) | Add pageUp/pageDown to SelectList | Feature | Implements `tui.select.pageUp`/`pageDown` in the base `SelectList` and model selector — restores browsing to long lists. |
| [#7344](https://github.com/earendil-works/pi/pull/7344) | Add remote session wire protocol | Feature | New `@earendil-works/pi-protocol` package with CBOR-encoded, length-prefixed framing for transport-neutral remote sessions. |
| [#7858](https://github.com/earendil-works/pi/pull/7858) | Route extension commands regardless of `expandPromptTemplates` | Fix | Fixes `pi.sendUserMessage()` skipping extension commands because `expandPromptTemplates` defaults to `false`. |
| [#7856](https://github.com/earendil-works/pi/pull/7856) | Repair JSON-serialized structured tool arguments | Fix | Handles double-serialized nested tool arguments that arrive as strings instead of objects; two prior defects made retries impossible. |
| [#7851](https://github.com/earendil-works/pi/pull/7851) | Enable GitHub Copilot model policies sequentially | Fix | Sequentially enables Copilot policies after device auth, preventing HTTP 429 rate-limit failures for orgs with 20+ models. |
| [#7844](https://github.com/earendil-works/pi/pull/7844) | Prevent bulk policy updates during login | Fix | Removes concurrent bulk model-enabling from Copilot login; models can still be enabled explicitly via Copilot Chat. |
| [#7857](https://github.com/earendil-works/pi/pull/7857) | Expose `expandPromptTemplates` in `sendUserMessage` | Feature | Proposed extension to let external callers (e.g., toilet-pi) control template expansion when sending messages. |

---

## Feature Request Trends

- **TUI usability refinements** — Users consistently request controls over clipboard-on-select behavior, page-up/down navigation in selectors, scroll-position preservation, and mouse-click positioning in the input textarea.
- **Remote / headless session support** — The merged protocol package (#7344) signals strong demand for running Pi as a remote agent (desktop-host, CLI pipe, RPC consumers).
- **Per-model configuration persistence** — Feature request for configurable per-model thinking-level persistence (#7871) and the reported context-window override bug for `z-ai/glm-5.2` (#7870) reflect a desire for fine-grained model-level settings.
- **Extension system maturity** — Requests around session-start events, command routing, and context-file exposure show the extension API is being stress-tested by real-world MCP and custom-agent use cases.
- **oh-my-pi capability migration** — A proposal (#7845) to port stream rules, subagent tools, advisor, and cross-session memory indicates the community values these orchestration features.

---

## Developer Pain Points

1. **TUI scroll and viewport instability** — Multiple reports (#7616, #7495, #7861) describe the chat view jumping during streaming or after tool-block resizing. The differential renderer's full-screen clear path is a known pain point.
2. **llama.cpp startup race** — A persistent issue (#6922, #6948) where the default model isn't applied at session start due to async model-refresh ordering; resolved by caching but a fragile pattern.
3. **Copilot login rate-limiting** — Orgs with many models hit GitHub's 429 limit during concurrent policy-enablement (#7850); fixed by sequential requests (#7851, #7844) but highlights a broader issue with bulk external-API calls.
4. **Extension command routing broken by `expandPromptTemplates`** — The documented `sendUserMessage` → extension command pattern (#7859) silently fails because the template-expansion flag defaults to false; fix landed in #7858.
5. **Node process lifecycle management** — SIGTERM-ignoring children leak when `ExtensionContext.exec` times out (#7864), and EPIPE crashes occur when a desktop host closes stdout (#7860).
6. **Provider deprecation hygiene** — Retired providers (AI21, #7869) and incorrect catalog metadata (glm-5.2 context window, #7870) surface at runtime with opaque errors, frustrating users who expect Pi to handle lifecycle changes gracefully.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-10

## 1. Today's Highlights

Qwen Code released a new nightly build **v0.21.8-nightly.20260810**, introducing support for **Qoder plugin extensions** and automated issue triage. The community is actively debating multi-agent session coordination and external context provider profiles, while several CI autofix runs tackled sandbox hangs and test flakiness on the main branch.

---

## 2. Releases

**v0.21.8-nightly.20260810.55e20db328** — [PR #8661](https://github.com/QwenLM/qwen-code/pull/8661)
- `feat(core)`: Added support for Qoder plugin extensions, enabling third-party plugin integration.
- `feat(ci)`: Implemented auto-assignment of issues to area owners from triage signals.

---

## 3. Hot Issues

| # | Issue | Why It Matters |
|---|-------|---------------|
| [#8718](https://github.com/QwenLM/qwen-code/issues/8718) | RFC: Native coordination for independent Qwen sessions | Proposes a leader-follower dispatch model for multi-agent workflows — foundational for any serious multi-session orchestration. Open, P2, 8 comments. |
| [#7585](https://github.com/QwenLM/qwen-code/issues/7585) | Proposal: Direct External Context Provider Profile | Would let monorepo setups share repository-wide context across sessions via an administrator-bound profile. Open, P3, 12 comments. |
| [#8784](https://github.com/QwenLM/qwen-code/issues/8784) | Streamable HTTP MCP: optional GET/SSE rejection kills connection | A spec-compliance gap where an optional `GET` probe causes full MCP disconnect. Open, P2, critical for MCP integrations. |
| [#8659](https://github.com/QwenLM/qwen-code/issues/8659) | TUI flickering / screen tearing in web-based terminals | Affected by Alibaba Cloud Workbench and xterm TERM with no COLORTERM. Open, P3, marked welcome-pr — high visibility for cloud users. |
| [#7118](https://github.com/QwenLM/qwen-code/issues/7118) | Windows installer fails when `Get-FileHash` is unavailable | P3 Windows bug with 3 👍; impacts standalone installers on enterprise or minimal PowerShell environments. |
| [#8615](https://github.com/QwenLM/qwen-code/issues/8615) | Desktop v0.1.0 crashes on Windows startup (EISDIR lstat 'C:') | P1 Windows Desktop bug — workspace open triggers a runtime crash. Closed after fix. |
| [#8721](https://github.com/QwenLM/qwen-code/issues/8721) | `npm test` fails with unknown flag locally | Development workflow blocker; `make test` breaks with `EUNKNOWNSCRIPT` from npm workspaces. Open, P2. |
| [#8823](https://github.com/QwenLM/qwen-code/issues/8823) | Hidden unrecognized diagnostics mutate transcript state | Core daemon bug where unhandled events leak into the shared transcript reducer, corrupting visible state. Open, P2. |
| [#8678](https://github.com/QwenLM/qwen-code/issues/8678) | Preserve current session when large restore times out | Ensures late-arriving restore requests don't destroy active sessions. Partially resolved via PR #8691. Open, P1. |
| [#6666](https://github.com/QwenLM/qwen-code/issues/6666) | qwen 3.7 max returns `<think>` tags in `content` instead of `reasoning_content` | Model compliance bug with DashScope API where thinking content lands in the wrong field. Closed. |

---

## 4. Key PR Progress

| # | PR | Summary |
|---|-----|---------|
| [#8804](https://github.com/QwenLM/qwen-code/pull/8804) | feat(cli): add native multi-agent coordination | Draft implementation exposing the in-process Agent Team workflow; persistent dispatch/collect and structured acceptance are still TODO per the scope note. |
| [#8732](https://github.com/QwenLM/qwen-code/pull/8732) | feat(cli): adopt Goal v3 in ACP sessions | Replaces the legacy Stop-hook `/goal` with the canonical Goal v3 runtime — ACP sessions now support create, status, edit, pause, resume, replace, and clear. |
| [#8816](https://github.com/QwenLM/qwen-code/pull/8816) | fix(ci): watchdog kills silent sandbox hangs | Introduces a 20-minute idle watchdog (`QWEN_IDLE_TIMEOUT_MS`) to detect and kill frozen sandbox agents, reducing autofix round waste. |
| [#8791](https://github.com/QwenLM/qwen-code/pull/8791) | perf(review): guarantee compose survives reverse-audit stop | Carves a compose floor (default 20 min) out of the budget reserve, ensuring `compose-review` and submission always complete even after a budget halt. |
| [#8802](https://github.com/QwenLM/qwen-code/pull/8802) | fix(desktop): restore macOS window after closing | Closing the main window now hides it rather than destroying it, enabling proper Dock/Finder restore behavior. |
| [#8798](https://github.com/QwenLM/qwen-code/pull/8798) | fix(web-shell): reconcile mid-turn messages with daemon state | Makes the daemon the authoritative owner of accepted mid-turn messages; Web Shell now restores queued messages after refresh and stops resubmitting daemon-owned ones. |
| [#8818](https://github.com/QwenLM/qwen-code/pull/8818) | fix(core): catch thinking-tag leaks on all OpenAI-compatible providers | Extends the content-only thinking-tag leak defense universally and closes two bypass paths that previously let real-world leaks through. |
| [#8728](https://github.com/QwenLM/qwen-code/pull/8728) | feat(core): live-session registry & `qwen sessions ps` | Each interactive session registers itself at `~/.qwen/sessions/<pid>.json` while running — a foundation for session management tooling. |
| [#8801](https://github.com/QwenLM/qwen-code/pull/8801) | fix(acp-bridge): bound live journal replay chunks | Compacts consecutive text/thought chunks in replay snapshots (max 256 events per entry), improving ACP bridge performance. |
| [#8794](https://github.com/QwenLM/qwen-code/pull/8794) | feat(web-shell): context usage progress pill | Adds a circular progress ring to the Web UI composer showing real-time context-window occupancy, synced with `/context` thresholds. |

---

## 5. Feature Request Trends

- **Multi-agent orchestration** — The strongest signal this cycle: independent session coordination ([#8718](https://github.com/QwenLM/qwen-code/issues/8718)), native multi-agent CLI ([#8804](https://github.com/QwenLM/qwen-code/pull/8804)), and session registry ([#8728](https://github.com/QwenLM/qwen-code/pull/8728)) all point to a community demand for structured multi-agent workflows.
- **Enterprise integration profiles** — External context provider ([#7585](https://github.com/QwenLM/qwen-code/issues/7585)) and external-memory ([#7449](https://github.com/QwenLM/qwen-code/issues/7449)) proposals show interest in monorepo and enterprise-grade state sharing.
- **Mobile / remote access** — QR-code pairing for phone-based Local Control ([#8595](https://github.com/QwenLM/qwen-code/issues/8595)) suggests demand for out-of-browser session management.
- **MCP spec compliance** — The SSE optional-GET bug ([#8784](https://github.com/QwenLM/qwen-code/issues/8784)) highlights growing MCP adoption and the need for stricter spec adherence.

---

## 6. Developer Pain Points

- **CI flakiness and sandbox hangs** — Repeated E2E failures ([#8756](https://github.com/QwenLM/qwen-code/issues/8756), [#8822](https://github.com/QwenLM/qwen-code/issues/8822), [#8799](https://github.com/QwenLM/qwen-code/issues/8799)) and silent 2-hour sandbox hangs are consuming autofix cycles. The watchdog PR ([#8816](https://github.com/QwenLM/qwen-code/pull/8816)) directly addresses this.
- **Windows installation fragility** — Two distinct Windows bugs this cycle: installer `Get-FileHash` failure ([#7118](https://github.com/QwenLM/qwen-code/issues/7118)) and Desktop runtime crash on workspace open ([#8615](https://github.com/QwenLM/qwen-code/issues/8615)), indicating the Windows packaging pipeline needs hardening.
- **Local development friction** — `npm test` breaking with unknown flags ([#8721](https://github.com/QwenLM/qwen-code/issues/8721)) blocks contributors; a stable local test command is a recurring ask.
- **Web terminal rendering issues** — TUI flickering in cloud/web terminals ([#8659](https://github.com/QwenLM/qwen-code/issues/8659)) degrades the experience for users on Alibaba Cloud Workbench and similar platforms.
- **Transcript state corruption** — Unhandled daemon events mutating shared state ([#8823](https://github.com/QwenLM/qwen-code/issues/8823)) and thinking-tag leaks in model responses ([#6666](https://github.com/QwenLM/qwen-code/issues/6666), [#8818](https://github.com/QwenLM/qwen-code/pull/8818)) indicate ongoing stability challenges in the core event pipeline.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-10

## 1. Today's Highlights

v0.9.6 shipped as a subtractive runtime release, rebuilding compaction around a single provider summary with committed successor handoff. The community is actively debating the Chinese translation of "Constitution" and raising concerns about provider/model resolution coherence, API key persistence, and the new deny-by-default approval highlight behavior in v0.9.4+.

## 2. Releases

**v0.9.6** ([PR #5313](https://github.com/Hmbown/CodeWhale/pull/5313)) — A subtractive runtime release that removes harness-created obstruction while preserving explicit budgets, deadlines, cancellation, and truthful provider state. Compaction is rebuilt around one provider summary plus a committed successor handoff, without mailbox freezing. CNB asset download URLs were fixed in [PR #5308](https://github.com/Hmbown/CodeWhale/pull/5308) to ensure mirror mode receives asset bytes instead of release HTML.

## 3. Hot Issues

1. **[Fleet model classes & loadout auto](https://github.com/Hmbown/CodeWhale/issues/3205)** — 13 comments. The shared model/loadout selector now supports a clear "Fleet loadout auto" mode that resolves the full compute loadout for a role/slot, not just a model string. A foundational UX decision for multi-model orchestration.

2. **[CLI/TUI parity for subagent control surfaces](https://github.com/Hmbown/CodeWhale/issues/4022)** — 9 comments. Ensures subagent status, expand/collapse, and cancellation controls aren't trapped in the TUI, enabling future cloud and remote workbench integrations.

3. **[Chinese translation of "Constitution" debate](https://github.com/Hmbown/CodeWhale/issues/4949)** — 8 comments. Community discussion on whether to use "宪法" (Constitution), "协作准则" (Collaboration Guidelines), or another term, balancing authority connotation against political sensitivity in Chinese.

4. **[Fork UX improvement](https://github.com/Hmbown/CodeWhale/issues/576)** — 6 comments. Fork is currently CLI-only, requiring exit → `deepseek sessions` → manual ID copy → re-entry. Proposes an interactive `/fork` command within the TUI with session selection.

5. **[Compaction gain not visible](https://github.com/Hmbown/CodeWhale/issues/5096)** — 4 comments. After `/compact` completes, the token counter status doesn't reflect the reduction (e.g. 37K/128K stays unchanged), making it impossible to verify compaction actually shrank the context.

6. **[Switching providers retains unrelated default model](https://github.com/Hmbown/CodeWhale/issues/5034)** — 4 comments. Switching to OpenAI can leave `gpt-5.5` as default, inherited from a different route — provider and model resolution aren't updated coherently.

7. **[Deny-by-default approval highlight configurable](https://github.com/Hmbown/CodeWhale/issues/5293)** — 4 comments, 1 👍. v0.9.4 changed the default highlighted option in permission dialogs, causing users to accidentally deny actions. Community requests clearer explanation and configurability.

8. **[1M context model compacts at 128K](https://github.com/Hmbown/CodeWhale/issues/5239)** — 2 comments. Unknown model IDs fall back to the 128K legacy default with no surfaced hint, silently degrading 1M-window models ([also tracked in #5244](https://github.com/Hmbown/CodeWhale/issues/5244)).

9. **[Tasks panel: unified surface for shells, subagents & workers](https://github.com/Hmbown/CodeWhale/issues/5270)** — 3 comments. Operators need one list of "things still running for this session" — background shells, subagents, Fleet/lane workers, and workflow runs — currently scattered across separate surfaces.

10. **[IME candidate window jumps during input](https://github.com/Hmbown/CodeWhale/issues/5023)** — 2 comments. Windows 11 users report unstable IME candidate window positioning during TUI input, a recurring cross-platform UX pain point.

## 4. Key PR Progress

1. **[PR #5313](https://github.com/Hmbown/CodeWhale/pull/5313)** — v0.9.6 release preparation; subtractive runtime with rebuilt compaction.
2. **[PR #5308](https://github.com/Hmbown/CodeWhale/pull/5308)** — Fix: use CNB asset download URLs so mirror mode receives actual binary bytes instead of HTML release pages.
3. **[PR #5281](https://github.com/Hmbown/CodeWhale/pull/5281)** — Dependency bump: `jsonschema` from 0.46.10 to 0.49.6.
4. **[Issue #3205](https://github.com/Hmbown/CodeWhale/issues/3205)** (closed) — Fleet model classes and loadout auto-resolution.
5. **[Issue #4022](https://github.com/Hmbown/CodeWhale/issues/4022)** (closed) — CLI/TUI parity for subagent control surfaces.
6. **[Issue #3313](https://github.com/Hmbown/CodeWhale/issues/3313)** (closed) — Split `RuntimeThreadManager` into store, executor, events, and types crates.
7. **[Issue #3312](https://github.com/Hmbown/CodeWhale/issues/3312)** (closed) — Extract `run_event_loop` from `ui.rs` into context-owned handlers.
8. **[Issue #3956](https://github.com/Hmbown/CodeWhale/issues/3956)** (closed) — Refactor `prompts.rs` (3,745 lines) into separate loading, overrides, taxonomy, and composition modules.
9. **[Issue #3952](https://github.com/Hmbown/CodeWhale/issues/3952)** (closed) — Split chat client request building from stream decoding and prompt inspection in `chat.rs`.
10. **[Issue #5266](https://github.com/Hmbown/CodeWhale/issues/5266)** (closed) — v0.9.5 milestone tracker; foundation issues picked to unblock subsequent work.

## 5. Feature Request Trends

- **Unified task visibility**: A single operator-facing surface tracking shells, subagents, Fleet workers, and workflow runs is a recurring theme ([#5270](https://github.com/Hmbown/CodeWhale/issues/5270)).
- **Fork from within TUI**: Users want interactive session forking without leaving the TUI ([#576](https://github.com/Hmbown/CodeWhale/issues/576)).
- **Multimodal viewing**: First-class screenshot/image support for agents, rather than relying on incidental path reads ([#5102](https://github.com/Hmbown/CodeWhale/issues/5102)).
- **Multi-provider key management**: Saving separate API keys per provider instead of overwriting a single key ([#5250](https://github.com/Hmbown/CodeWhale/issues/5250)).
- **Transparent subagent identity**: Display fleet/session names instead of opaque `agent_<hex>` IDs or auto-generated nicknames ([#5287](https://github.com/Hmbown/CodeWhale/issues/5287)).
- **Compaction observability**: Users want visible before/after token counts and a structured survival contract for what compaction preserves ([#5096](https://github.com/Hmbown/CodeWhale/issues/5096), [#4394](https://github.com/Hmbown/CodeWhale/issues/4394), [#5043](https://github.com/Hmbown/CodeWhale/issues/5043)).

## 6. Developer Pain Points

- **Context management opacity**: Compaction triggers silently at 128K fallback for unknown models with no feedback, and post-compaction token counts don't reflect actual gains — users lose trust in the process.
- **Provider/model coupling bugs**: Switching providers leaves stale default models; API keys can persist in the wrong repo scope instead of the global store, creating security and UX friction.
- **Approval dialog regression**: The v0.9.4 change to deny-by-default highlight ordering causes accidental denials; users want it configurable and clearly explained.
- **TUI ergonomics**: IME candidate window instability on Windows, rail decoration characters leaking into copied text ([#5314](https://github.com/Hmbown/CodeWhale/issues/5314)), and the lack of in-TUI fork commands force context-switching between shell and TUI.
- **File edit reliability**: The `action=edit` mode silently accepts wrong parameter names and reports fake success, requiring 3–5x re-edits per location ([#5209](https://github.com/Hmbown/CodeWhale/issues/5209)).
- **Config shadowing**: Fleet config has an extra nesting layer causing silent shadowing between `.codewhale/agents/builder.toml` and other config sources ([#5098](https://github.com/Hmbown/CodeWhale/issues/5098)).

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*