# AI CLI Tools Community Digest 2026-09-06

> Generated: 2026-09-06 04:06 UTC | Tools covered: 10

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
**Date: 2026-09-06**

---

## 1. Ecosystem Overview

The AI CLI tool landscape is entering a maturation phase where reliability and session continuity dominate community concerns over raw capability. Claude Code, OpenAI Codex, Gemini CLI, and GitHub Copilot CLI represent the most mature ecosystems with high issue volumes and complex plugin/MCP architectures, while Qwen Code, OpenCode, and Codewhale (DeepSeek) show rapid iteration with novel architectural approaches like ACP delegation and workspace-scoped extensions. Two notable trends emerge: subagent and agent lifecycle management is now a cross-tool pain point, and MCP integration—while widely adopted—remains fragile across every ecosystem with recurring transport, timeout, and scope bugs.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Merged PRs | Release (24h) | Release Notes |
|---|---|---|---|---|---|
| **Claude Code** | 10 (top: 112c, 72👍) | 4 | 3 (87077, 87079, 89404) | v2.1.263 | Bug fixes & reliability |
| **OpenAI Codex** | 10 (top: 45👍) | 0 | 9 (43147, 43144, 43126, 43120, 43113, 43104, 43100, 43097, 43090, 43083) | None | — |
| **Gemini CLI** | 10 (top: P1 hangs) | 11 | 1 (28968) | v0.60.0-nightly.20260906 | Model-pin, checkpoint, MCP fixes |
| **GitHub Copilot CLI** | 10 (top: 28👍) | 0 | 0 | None | — |
| **Kimi Code CLI** | 4 (top: closed) | 1 | 0 | None | — |
| **OpenCode** | 10 (top: 15c, 13👍) | 0 | 9 (47559, 47394, 47224, 47574, 47570, 47573, 47572, 47571, 47561, 47444) | None | — |
| **Pi** | 10 (top: 52👍) | 4 | 5 (9219, 9214, 9215, 9170, 9172, 9163) | v0.85.1 | GPT-6 Astra support; dependency fix |
| **Qwen Code** | 11 (top: P1 bloat) | 0 | 6 (11086, 11003, 10439, 10938, 9466, 11145, 11144, 11103) | v0.23.1-preview.0, v0.23.0-nightly | Web-shell workflows, ACP delegation |
| **DeepSeek TUI (Codewhale)** | 10 (top: P1 claims) | 7 | 4 (5910, 5903, 5895, 5893) | v0.9.12 | Legacy package deprecated |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|---|---|---|
| **Subagent/Agent Lifecycle Reliability** | Gemini CLI, Claude Code, Codewhale, Qwen Code | Hang recovery (#21409), false GOAL terminations (#22323), tool inheritance gaps (#92426), write-claim leaks (#5906), ACP delegation (#11003) |
| **MCP Ecosystem Maturity** | Claude Code, Gemini CLI, Copilot CLI, OpenCode, Codewhale | Scope support in OAuth (#20503), HTTP transport reachability (#86875), per-server progress feedback (#5887), attachment passthrough (#35538), timeout cascades (#4731) |
| **Session Continuity & Compaction** | OpenAI Codex, Pi, Qwen Code, Copilot CLI | Post-compaction state corruption (#41922), server-side compaction via Responses API (#7317), reconnect floods (#10780), worktree loss after updates (#4734) |
| **Cross-Platform Consistency** | Claude Code, Gemini CLI, Pi, Codewhale, Copilot CLI | Windows desktop instability (#53247, #66516, #87895), IME support (#5200, #2323), CLI vs Desktop plugin identity (#92427), SSH clipboard parity (#4551) |
| **Extensibility & Plugin Architecture** | Claude Code, OpenCode, Qwen Code, Pi | Function Hooks with side-effect tracking (#91870), session-lifecycle hooks (#28695), workspace-scoped extensions (#11086), mid-sentence skill invocation (#9214) |
| **Model-Agnostic / Multi-Provider Support** | Pi, OpenCode, Qwen Code, Gemini CLI | GPT-6 Astra routing (#9209), Copilot third-party model block (#34030), Fable 5 fallback configurability (#74311), explicit model-pin preservation (#29217) |

---

## 4. Differentiation Analysis

| Tool | Technical Approach | Target Users | Key Differentiator |
|---|---|---|---|
| **Claude Code** | Express/Koa-style `next()` plugin model; side-effect-tracked hooks; Fable 5 safety classifier | Enterprise & power users | Deepest plugin extensibility surface; most active enhancement discussion (#91870) |
| **OpenAI Codex** | Bazel-managed native builds; managed worktree sessions; Guardian v2 context | OpenAI ecosystem users | Most aggressive native/voice infrastructure investment; `/worktree` for session isolation |
| **Gemini CLI** | Google's A2A server integration; checkpoint-resilient history; AST-aware tooling proposals | Google/Gemini users | Nightly cadence with rapid P1 fix turnaround; strong focus on model-pin accuracy |
| **GitHub Copilot CLI** | VS Code-integrated; queue-based message model; Canvas tooling | GitHub/Copilot subscribers | Queue cancellation gap (#1857) is unique; strongest desktop app coupling (also its fragility) |
| **Qwen Code** | ACP-based subagent delegation; Web Shell workflow visualization; per-workspace extensions | Chinese/global open-source users | Most architecturally ambitious—external agent delegation, session-wide turn navigation, daemon persistence |
| **OpenCode** | SQLite-backed sessions; event-stream reconnection with resync; catalog refetch coalescing | Self-hosted/enterprise | Strongest concurrency/SQLite story; "recently closed" UX polish; TUI + Desktop dual surface |
| **Pi** | OpenAI Responses API depth; Meta/Muse gateway support; Nix flake | Multi-provider power users | Fastest multi-provider integration (GPT-6 Astra, Meta, LLM Gateway); packaging fragility exposed |
| **DeepSeek TUI (Codewhale)** | Fleet menu with claim-based write scope; injectable Win32 backend; Cargo workspace | Chinese/Windows users | Most aggressive Windows computer-use hardening this cycle; npm package deprecation signals product rebrand |

---

## 5. Community Momentum & Maturity

**High Momentum (rapid iteration, high engagement):**
- **Gemini CLI** — 11 open PRs with a 6-hour fix turnaround on P1 model-pin bugs; nightly cadence shows aggressive development velocity.
- **Qwen Code** — 6 PRs merged including architecturally significant work (ACP delegation, turn navigation); preview builds ship weekly.
- **OpenCode** — 9 PRs in 24h covering reconnection, SQLite, request timeouts; community is actively using and stress-testing.

**Mature & Stable (lower velocity, deeper architecture):**
- **Claude Code** — Single bug-fix release but the highest single-issue engagement (#91870 with 112 comments); plugin ecosystem is the most discussed feature area across all tools.
- **OpenAI Codex** — 9 PRs landed but zero new issues resolved; focus is on infrastructure (voice, Bazel) rather than core CLI bugs.

**Volatile / Emerging:**
- **Pi** — v0.85.0 packaging defect (missing deps) forced an emergency v0.85.1; publish pipeline needs harderening.
- **Codewhale** — Transition from `deepseek-tui` to `codewhale` creates community fragmentation; legacy package deprecated.
- **Kimi Code CLI** — Smallest community (4 issues, minimal engagement); PR #2513 addresses a fundamental API quirk.

---

## 6. Trend Signals

1. **Subagent reliability is the #1 unsolved problem.** Every major tool has open P1 issues around agent hangs, false terminations, or claim leaks. The community is converging on the need for better lifecycle management primitives (visible trajectories, file-based task tracking, injection-testable backends).

2. **MCP is adopted but not reliable.** Six tools report distinct MCP bugs this cycle—scope omission, transport failures, timeout cascades, attachment drops, stale server states. This signals the MCP spec is still stabilizing and tool authors are iterating faster than the spec.

3. **Windows desktop is a consistent failure mode.** Claude Code, Codex, Pi, and Codewhale all report Windows-specific crashes, input issues, or session loss. Cross-platform parity remains a significant engineering gap.

4. **Session continuity architectures are diverging.** Three approaches are emerging: (a) server-side compaction via OpenAI Responses API (#7317), (b) ACP-based external delegation (#11003), and (c) local checkpoint resilience with graceful degradation (#29195). The winner will likely depend on whether the market favors cloud-stateful or local-stateful architectures.

5. **Export/shareable transcripts are a growing UX frontier.** Qwen Code's 19.5 MB empty exports (#11031), OpenCode's session migration bugs (#35690), and Pi's HTML export dropping hidden context (#8896) all indicate that session portability is an under-addressed pain point.

6. **Package integrity and publish pipeline maturity matters.** Pi's v0.85.0 defect and Codewhale's v0.9.12 publish verification gap (#5892) are cautionary signals—tools with complex plugin/extension ecosystems need stronger CI guards around dependency declarations and release verification.

---

*Report generated from community digests dated 2026-09-06 across 8 AI CLI tool repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
**Data as of 2026-09-06 · Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

| # | Skill | Status | Summary |
|---|-------|--------|---------|
| 1 | **frontend-design** | 🟡 Open PR #210 | Comprehensive rewrite for clarity and actionability; ensures every instruction is executable within a single Claude Code conversation. |
| 2 | **skill-creator (eval fix)** | 🟡 Open PR #1298 | Fixes a critical bug where `run_eval.py` always reported 0% recall, breaking the description-optimization loop (#556, 10+ reproductions). Includes Windows stream-reading and parallel-worker fixes. |
| 3 | **testing-patterns** | 🟡 Open PR #723 | Full-spectrum testing skill covering philosophy (Testing Trophy), unit testing (AAA pattern, naming, edge cases), and React component testing with Testing Library. |
| 4 | **Hivemind** | 🟡 Open PR #1628 | Multi-agent orchestration that offloads mechanical work to headless opencode workers on free models, reserving expensive Claude context for planning and review. |
| 5 | **claude-api** | 🟡 Open PR #1607 | Updates retired model IDs (`claude-opus-4-1`, `claude-sonnet-4-0`, `claude-opus-4-0`, `claude-3-haiku`). Addresses issue #1487 where the skill eagerly injected ~156k tokens and exhausted context windows. |
| 6 | **docx (tracked changes fix)** | 🟡 Open PR #541 | Fixes document corruption caused by `w:id` collisions between tracked changes and existing bookmarks in OOXML. |
| 7 | **document-typography** | 🟡 Open PR #514 | Prevents orphan word-wrap, widow paragraphs, and numbering misalignment in AI-generated documents — a widely recurring pain point. |
| 8 | **service-now** | 🟡 Open PR #568 | Broad ServiceNow platform skill covering ITSM, ITOM, SecOps, ITAM/SAM, FSM, SPM, CSDM, and IntegrationHub. |

**Key PR links:** [#210](https://github.com/anthropics/skills/pull/210) · [#1298](https://github.com/anthropics/skills/pull/1298) · [#723](https://github.com/anthropics/skills/pull/723) · [#1628](https://github.com/anthropics/skills/pull/1628) · [#1607](https://github.com/anthropics/skills/pull/1607) · [#541](https://github.com/anthropics/skills/pull/541) · [#514](https://github.com/anthropics/skills/pull/514) · [#568](https://github.com/anthropics/skills/pull/568)

---

## 2. Community Demand Trends (from Issues)

Analysis of the top commented issues reveals four dominant demand signals:

- **Security & Trust Boundaries** — Issue [#492](https://github.com/anthropics/skills/issues/492) (43 comments) flagged community skills impersonating the `anthropic/` namespace, creating elevated-permission trust boundary risks. Issue [#1175](https://github.com/anthropics/skills/issues/1175) raised concerns about embedding access-control logic in SKILL.md for sensitive systems (SharePoint).
- **Context Window Discipline** — Issue [#1487](https://github.com/anthropics/skills/issues/1487) (4 comments) exposed eager ~156k-token injection in `claude-api`, a recurring pattern where skills bloat context. Users want leaner, on-demand skill payloads.
- **Quality & Governance Tooling** — Multiple proposals point to demand for meta-level skills: **skill-quality-analyzer** & **skill-security-analyzer** (PR [#83](https://github.com/anthropics/skills/pull/83)), **compact-memory** (Issue [#1329](https://github.com/anthropics/skills/issues/1329)), and **agent-governance** (Issue [#412](https://github.com/anthropics/skills/issues/412)).
- **Organizational Collaboration** — Issue [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) is the most-upvoted open feature request: org-wide skill sharing without manual file distribution.

---

## 3. High-Potential Pending Skills

These open PRs have active community engagement and address well-documented pain points; they are strong candidates for near-term merge:

| PR | Skill | Why It's Ready |
|----|-------|---------------|
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | Novel multi-agent orchestration; directly addresses cost-throughput tradeoffs the community discusses frequently. |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Covers an underserved domain (testing philosophy + React) with a structured, opinionated approach. |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a universal formatting pain point with a narrowly-scoped, high-utility skill. |
| [#1607](https://github.com/anthropics/skills/pull/1607) | **claude-api (model refresh)** | Low-risk maintenance PR that resolves a high-severity bug (context exhaustion). |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Four-dimension reasoning quality gate with mechanical file verification — aligns with the community's governance trend. |
| [#1627](https://github.com/anthropics/skills/pull/1627) | **buffer-api** | Portable GraphQL-based social-scheduling skill; extends agent capabilities beyond code into ops workflows. |

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is for skills that enforce discipline — context efficiency, output quality, and organizational trust boundaries — rather than simply adding more domain coverage.**

Users are increasingly proposing meta-skills (self-audit, quality analysis, governance, compact memory) and fix PRs targeting reliability bugs (eval scripts, Windows compatibility, token bloat) more than new domain skills, signaling a maturation from "what can skills do?" to "how can skills do it reliably and safely?"

---



# Claude Code Community Digest — 2026-09-06

## 1. Today's Highlights

Claude Code v2.1.263 shipped with bug fixes and reliability improvements. The community is buzzing around a major Function Hooks enhancement proposal (#91870, 112 comments) that would let plugins deeply modify Claude Code behavior through a side-effect-tracked, continuation-based plugin model. Meanwhile, Windows Desktop stability remains a focal point with multiple reports of window focus issues, OAuth refresh failures, and a crash with no forensic trace.

---

## 2. Releases

**v2.1.263** — Bug fixes and reliability improvements.
[GitHub](https://github.com/anthropics/claude-code)

---

## 3. Hot Issues

1. **[Enhancement] Function Hooks — make plugins 10x more powerful** (#91870) · 112 comments · 72 👍
   A deep plugin system using side-effect tracking and an Express/Koa-style `next` continuation model. The community is highly engaged; this could redefine the extensibility surface. [Link](https://github.com/anthropics/claude-code/issues/91870)

2. **[Bug] Claude Desktop fails to launch on Windows — orphaned Silo/Job Object** (#53247) · 66 comments · 29 👍
   After a crash, Windows leaves orphaned Job Objects that block re-launch until logoff or reboot. A painful, recurring blocker for Windows users. [Link](https://github.com/anthropics/claude-code/issues/53247)

3. **[Bug] Claude Desktop window stays always on top — macOS** (#66516) · 31 comments · 5 👍 *(Closed)*
   Users reported the desktop window becoming permanently topmost with no setting to disable it. Closed, likely resolved in a recent release. [Link](https://github.com/anthropics/claude-code/issues/66516)

4. **[Bug] Claude Desktop window stays always on top — Windows** (#87895) · 17 comments · 72 👍 *(Closed)*
   Same issue on Windows; the high like count indicates strong community frustration. Closed. [Link](https://github.com/anthropics/claude-code/issues/87895)

5. **[Bug] Read Out Loud / Play voice degrades mid-playback** (#72123) · 8 comments · 1 👍
   Audio playback gets soft, speeds up, voice changes, and fades — a quality-of-life issue for accessibility users. [Link](https://github.com/anthropics/claude-code/issues/72123)

6. **[Bug] Cowork session reports zero connected folders** (#86647) · 7 comments · 2 👍
   The project UI shows a folder connected, but the Cowork session reports none — a syncing bug that breaks context. [Link](https://github.com/anthropics/claude-code/issues/86647)

7. **[Bug] Windows freeze-then-vanish crash, zero forensic trace** (#89679) · 5 comments · 0 👍
   Recurring crash with no logs across any standard channel, making it nearly impossible to diagnose. [Link](https://github.com/anthropics/claude-code/issues/89679)

8. **[Bug] Bash tool silently truncates commands over ~8 KB** (#85111) · 5 comments · 0 👍
   Commands exceeding ~8 KB are silently truncated and reported as a quoting error — a serious correctness issue for large scripts. [Link](https://github.com/anthropics/claude-code/issues/85111)

9. **[Bug] HTTP-transport MCP tools unreachable despite /mcp showing connected** (#86875) · 4 comments · 0 👍
   Tools appear in `/mcp` listings but fail at invocation time. A confusing experience for MCP consumers. [Link](https://github.com/anthropics/claude-code/issues/86875)

10. **[Feature Request] Configurable Fable 5 classifier fallback model and effort** (#74311) · 3 comments · 6 👍
    Users want control over which model and effort level the safety classifier fallback lands on, rather than a hardcoded Opus default. [Link](https://github.com/anthropics/claude-code/issues/74311)

---

## 4. Key PR Progress

1. **PR #87077** — Fix invalid YAML frontmatter in all agents
   Agent descriptions containing `key: value` dialogue lines were parsed as nested mappings, causing agents to load with empty frontmatter. This patch quotes the scalars properly. [Link](https://github.com/anthropics/claude-code/pull/87077)

2. **PR #87079** — Fix `**` glob patterns to match zero-depth paths
   Security guidance glob patterns were silently excluding top-level files because the underlying `fnmatch` behavior didn't match the documented `**` semantics. Critical fix for security rule coverage. [Link](https://github.com/anthropics/claude-code/pull/87079)

3. **PR #89404** — Don't abort validate-agent.sh at the first warning
   The plugin validation script's `set -euo pipefail` interaction with `((warning_count++))` caused false-flagging of valid agents. Fixes issue #83803. [Link](https://github.com/anthropics/claude-code/pull/89404)

---

## 5. Feature Request Trends

- **Extensibility & plugin depth** — Function Hooks (#91870) is the dominant request, signaling a community appetite for deeper, composable plugin architecture.
- **Cross-device configuration sync** — Syncing `~/.claude/` (skills, plugins, MCP, statusline) across machines (#66303) remains a recurring pain point for multi-device users.
- **Configurable safety/classifier behavior** — Users want control over Fable 5 fallback model and effort (#74311), as well as auto-fix capability for detected bugs (#92428) rather than just surfacing them.
- **Web/Cowork UX polish** — Controls for unread indicators on Recents rows (#92430), better session management in Remote Control (#91991).
- **Subagent autonomy** — Fixes for subagent tool/prompt inheritance (#92426) and missing tool references in agent definitions (#92134).

---

## 6. Developer Pain Points

- **Windows desktop instability** — Repeated reports of window focus bugs (#66516, #87895, #92337), orphaned Job Objects preventing relaunch (#53247), OAuth token race conditions after sleep/wake (#90688), and a crash with zero forensic trace (#89679). Windows is the most-frustrated platform this cycle.
- **Agent/tool system inconsistencies** — The `Agent` tool ignoring subagent definitions (#92426), built-in instructions pointing to non-existent `SendMessage` tool (#92134), and Bash being defaulted on Windows even in Fable 5.1 (#91477, #92407) all point to coordination gaps between the agent framework, tool registry, and platform detection.
- **MCP surface bugs** — HTTP-transport tools showing as connected but failing at invocation (#86875), and misleading timeout messaging (#91898).
- **CLI vs. Desktop plugin identity mismatch** — CLI and desktop resolving different plugin identities (#92427) breaks expectations for users running both.
- **Clipboard regression in VS Code** — Text selection in the chat panel copies nothing since 2.1.259 (#91860), a breaking regression for a core workflow.
- **Scheduled task correctness** — Tasks marking themselves complete without actually running (#92429), undermining reliability of automation.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-06

---

## 1. Today's Highlights

The Codex community is focused on a cluster of session and history integrity bugs on Windows, including a critical launch failure in version `26.901.1978.0` and recurring rollout-ordinal reuse in paginated histories. Meanwhile, a significant batch of Bazel-managed native voice-library PRs landed, broadening Windows MSVC build support and adding bounded RTP handling to the voice host.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#35746](https://github.com/openai/codex/issues/35746) | Paginated history drops valid flattened rollout records and reuses ordinals | Corrupts conversation history projection; affects `rust-v0.146.0-alpha.14` on Linux x86_64. | 39 comments, 3 👍 — top-discussed issue of the cycle. |
| [#16579](https://github.com/openai/codex/issues/16579) | Allow configuring the default session shell via config (Windows) | Windows defaults to PowerShell, blocking users who prefer Git Bash or other shells. | 45 👍 — most-upvoted open issue by far. |
| [#42853](https://github.com/openai/codex/issues/42853) | GPT-6 Astra missing from model picker for eligible ChatGPT Pro account | Model catalog inconsistency on Windows Desktop (`26.901.4073.0`); similar to #43143 which is now closed. | 10 comments — multiple reports of the same symptom. |
| [#42501](https://github.com/openai/codex/issues/42501) | Windows 26.901.1978.0 fails to launch UI | `cua_node` staging cannot copy `node_repl.exe`; processes start but `MainWindowHandle` stays 0. | 9 comments — blocks desktop use entirely for affected users. |
| [#16759](https://github.com/openai/codex/issues/16759) | Full Access still shows permission prompts | Defeats the purpose of the Full Access sandbox setting on VS Code extension. | 12 comments, 1 👍 — ongoing sandbox UX frustration. |
| [#41922](https://github.com/openai/codex/issues/41922) | Chats unusable after context compaction | Internal validation errors corrupt session state post-compaction on Windows Desktop. | 7 comments — reliability concern for long sessions. |
| [#41849](https://github.com/openai/codex/issues/41849) | Remote-SSH stale app-server blocks new sessions | Server reconnect leaves orphaned `app-server` holding thread writer; new sessions show "This is open in another app." | 6 comments, 4 👍 — painful for remote-development workflows. |
| [#20503](https://github.com/openai/codex/issues/20503) | MCP OAuth login omits scopes during dynamic client registration | Prevents login to MCP servers like Fastmail that require scopes at registration time. | 4 comments, 11 👍 — blocks MCP adoption for several providers. |
| [#43045](https://github.com/openai/codex/issues/43045) | GPT-6 Astra WebSocket reconnect loop consumes credits | Repeated WS failures on CLI `0.153.4` burn purchased credits until HTTPS fallback triggers. | 2 comments — direct billing impact. |
| [#32614](https://github.com/openai/codex/issues/32614) | Agent-created top-level tasks hidden from search & mobile | Tasks spawned by agents don't surface in desktop search or Codex Mobile Remote. | 6 comments, 2 👍 — discoverability gap for multi-session workflows. |

---

## 4. Key PR Progress

| # | PR | Summary |
|---|-----|---------|
| [#43147](https://github.com/openai/codex/pull/43147) | Gate experimental context by model capability at session startup | Fixes child-session inheritance of token-budget activation when starting fresh with a different model. |
| [#43144](https://github.com/openai/codex/pull/43144) | Add Windows MSVC Bazel targets for native voice libraries | Adds x64 and ARM64 native build targets, runtime prep, and linking for Windows voice builds. |
| [#43126](https://github.com/openai/codex/pull/43126) | Expose native Windows build tools through Bazel targets | Retains MSVC tools discarded during setup; fixes native tool unavailability for Bazel consumers. |
| [#43120](https://github.com/openai/codex/pull/43120) | Add managed worktree creation to TUI session commands | Adds `/worktree` for forking conversations into new managed checkouts; enhances `/new` and `/fork` options. |
| [#43113](https://github.com/openai/codex/pull/43113) | Save subagent and memory opt-ins through the app server | Routes TUI subagent/memory prompts through server config writes for new threads with clear success/failure reporting. |
| [#43104](https://github.com/openai/codex/pull/43104) | Move Guardian thread context into `guardianv2` configuration | Consolidates thread context under the `guardianv2` feature flag; updates schema and defaults. |
| [#43100](https://github.com/openai/codex/pull/43100) | Add bounded incoming Opus RTP handling to voice host | Limits outstanding media to 64 packets / 2 MiB; preserves timestamps without duplicating queued copies. |
| [#43097](https://github.com/openai/codex/pull/43097) | Add helper-backed realtime WebRTC session API | New `RealtimeWebrtcSession` with cloneable handles for negotiation, audio controls, level meters, and error reporting. |
| [#43090](https://github.com/openai/codex/pull/43090) | Send processed microphone audio over RTP in voice-host | Connects capture to the outgoing media track; previously audio was drained locally without sending. |
| [#43083](https://github.com/openai/codex/pull/43083) | Supply Bazel-managed CMake and Ninja for bundled Opus build | Pins CMake and Ninja via `rules_foreign_cc`; removes dependency on host `PATH` tools for Opus compilation. |

---

## 5. Feature Request Trends

- **Default shell configurability on Windows** (#16579, 45 👍) — strong community demand for Git Bash / custom shell support as the default Codex session shell.
- **Subagent visibility in the main TUI** (#43148) — persistent activity indicator requested so users can see subagent progress without manually running `/subagents`.
- **Continuous weekly quota consumption** (#43135) — users want the 5-hour rolling cap removed in favor of a simple weekly-pool mode for uninterrupted engineering work.
- **MCP OAuth scope support** (#20503, 11 👍) — enabling scope传递 during dynamic client registration is a prerequisite for broader MCP server adoption.
- **Managed worktree / fork workflows** — the merged `/worktree` command (#43120) signals ongoing demand for clearer session isolation and parallel-branch support.

---

## 6. Developer Pain Points

- **Rollout history corruption** (#35746, #43142): Paginated history drops valid records and reuses ordinals after resume, freezing desktop conversation view.
- **Session-state breakage after compaction** (#41922): Internal validation errors leave chats in an unrecoverable state post-compaction.
- **Windows desktop launch failures** (#42501, #42259): Recent updates (`26.901.1978.0`, `26.831.2377`) introduce blocking bugs — missing UI windows and infinite plugin-selector spinning.
- **Sandbox permission-prompt friction** (#16759): Full Access setting is ignored, forcing repeated prompts that undermine the configured permission model.
- **Remote-SSH stale-server syndrome** (#41849): Disconnections leave orphaned `app-server` processes that block all new sessions with misleading "open elsewhere" errors.
- **Credit burn from WebSocket reconnect loops** (#43045): GPT-6 Astra WS failures consume purchased credits before HTTPS fallback recovers, creating unexpected billing events.
- **Weekly quota discontinuity** (#42765, #43135): Limits drop from ~45% to 0% with no sessions run, and the 5-hour rolling cap interrupts long engineering tasks.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-06

## 1. Today's Highlights

Gemini CLI v0.60.0-nightly.20260906 was released with several critical fixes targeting model rewrite behavior, checkpoint resilience, and MCP prompt handling. The community is most actively discussing subagent reliability — particularly agent hangs, recovery after max-turn limits, and the underuse of custom skills and sub-agents. A cluster of security-adjacent issues around Auto Memory logging and deterministic redaction also surfaced this cycle.

---

## 2. Releases

**v0.60.0-nightly.20260906.g85aca163f** — Automated nightly bump ([PR #29223](https://github.com/google-gemini/gemini-cli/pull/29223)). This release is paired with a batch of fixes landing in the same window: explicit model-pin preservation, checkpoint fallback on malformed history, and MCP prompt text no longer being double-encoded. Full changelog: [compare](https://github.com/google-gemini/gemini-cli/compare/v0.60.0-nightly.20260905.g85aca163f...v0.60.0-nightly.20260906.g85aca163f).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Misleading termination status can hide failed investigations, causing the parent agent to proceed on stale assumptions. P1 bug. | 13 comments, 2 👍 — high engagement on a long-standing issue (open since Mar 2026). |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | Simple tasks like folder creation can hang indefinitely when deferring to the generalist subagent. Workaround: disable subagents. P1 bug. | 8 comments, 8 👍 — strong community signal; users are actively hitting this in daily workflows. |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Post-Execution Intent Routing | Proposes leveraging Gemini 3's native bash affinity through POSIX tool chaining with security sandboxing. Large effort, P2 enhancement. | 9 comments — architecturally significant; could reshape how the agent executes shell tasks. |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | Epic tracking whether AST-aware tools can reduce turn counts and token noise by reading precise method bounds. P2. | 7 comments — direct impact on context efficiency, a top community concern. |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Users report custom skills (e.g., gradle, git) are ignored unless explicitly invoked. P2 customer-issue. | 6 comments — reflects a gap between agent capability and agent behavior. |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduce Auto Memory logging | Auto Memory sends transcript content to the model *before* redaction, creating a secrets-in-context risk. P2 security bug. | 5 comments — growing concern around data privacy in memory extraction. |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell commands stuck "Waiting input" after completion | Simple CLI commands hang with "Awaiting user input" even when they produce no interactive prompt. P1 bug. | 4 comments, 3 👍 — repeated reports from power users. |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent session takeover & lock recovery | BrowserManager fail-fast on locked profiles blocks persistent sessions. Feature request for resilience. P2. | 4 comments — critical for users relying on `sessionMode: 'persistent'`. |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Browser agent terminates with GOAL on Wayland compositors. P1 bug with agent/browser labels. | 4 comments, 1 👍 — Linux desktop compatibility gap. |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores settings.json overrides | Config overrides like `maxTurns` in settings.json are silently ignored by the browser agent. P2 bug. | 3 comments — configuration drift between agent registry and browser agent runtime. |

---

## 4. Key PR Progress

| # | Title | Author | Status | Summary |
|---|-------|--------|--------|---------|
| [#29205](https://github.com/google-gemini/gemini-cli/pull/29205) | fix(cli): submit MCP prompt text without JSON encoding | CoralGarden52 | OPEN | MCP prompt responses were being JSON-encoded, breaking embedded quotes/newlines. Now submits text directly with a regression test. |
| [#29125](https://github.com/google-gemini/gemini-cli/pull/29125) | fix(cli): convert hook timeout from seconds to milliseconds | 0717lee | OPEN | Fixes migration bug where Claude Code's second-based timeouts were interpreted as milliseconds, causing hooks to fire prematurely. |
| [#29163](https://github.com/google-gemini/gemini-cli/pull/29163) | fix(cli): prevent crash during auth in git repos | ehsan-fj | OPEN | Prevents startup crash when `useGitBranchName` hook encounters `.git` under macOS Seatbelt or restricted permissions. P1 security fix. |
| [#29126](https://github.com/google-gemini/gemini-cli/pull/29126) | fix(a2a-server): mount express.json before a2a sdk routes | Anurag-M1 | OPEN | A2A SDK routes received `undefined` body because `express.json()` was mounted after route setup, breaking JSON-RPC parsing. |
| [#29124](https://github.com/google-gemini/gemini-cli/pull/29124) | fix(cli): correct SubagentStop event key in hooks migration | 0717lee | OPEN | `SubAgentStop` → `SubagentStop` key mismatch meant subagent-stop hooks were silently dropped during Claude-to-Gemini migration. |
| [#29195](https://github.com/google-gemini/gemini-cli/pull/29195) | fix(checkpoint): degrade non-array history instead of crashing | soroush5 | OPEN | Malformed checkpoint files with non-array `history` now degrade gracefully to empty rather than throwing a raw `TypeError` on `/resume`. |
| [#29217](https://github.com/google-gemini/gemini-cli/pull/29217) | fix(config): don't rewrite explicit gemini-2.5-flash selection | TECHIE-TITAN | OPEN | `isFlashModel()` was too broad (`endsWith('flash')`), silently upgrading explicitly pinned `gemini-2.5-flash` to `gemini-3.5-flash`. P1 fix. |
| [#29222](https://github.com/google-gemini/gemini-cli/pull/29222) | fix(config): prevent rewriting explicitly pinned flash models | HariomJangra | OPEN | Companion fix to #29217 — ensures `--model gemini-2.5-flash` is honored on backends with 3.5 Flash GA access. |
| [#29211](https://github.com/google-gemini/gemini-cli/pull/29211) | fix(cli): stop scheduling state updates from inside a state updater | linhongyu510 | OPEN | Fixes React invariant violation caused by `useInputHistoryStore.addInput()` nesting state updates (`setPastSessionMessages` inside `setCurrentSessionMessages`). |
| [#28968](https://github.com/google-gemini/gemini-cli/pull/28968) | fix(core): dedupe symlinked/junctioned skills directories | aniruddhaadak80 | **CLOSED** | Resolves double-discovery of skills when `.gemini` is symlinked/junctioned to `.agents` for open Agent Skills standard compatibility. |

---

## 5. Feature Request Trends

1. **AST-aware codebase tools** — Multiple issues (#22745, #22746) point to community demand for surgical file reads and navigation that reduce token waste and improve turn efficiency.
2. **Agent self-awareness & tooling accuracy** — Users want the agent to understand and correctly use its own CLI flags, hotkeys, and skills (#21432, #21968).
3. **Persistent task tracking** — Replacement of in-context `WriteToDo` with file-based CRUD tracking (#18836, #21000) to eliminate context rot and cross-session memory loss.
4. **Resilient subagent lifecycle** — Recovery from lock states (#22232), visible trajectories via `/chat share` (#22598), and better debugging context in bug reports (#21763).
5. **Tactful/token-frugal extraction** — Hierarchical code discovery (grep → read → edit) to avoid context firehosing on large files (#19561).
6. **Zero-dependency OS sandboxing** — Native bash execution with POSIX tool chaining and post-execution intent routing (#19873).

---

## 6. Developer Pain Points

- **Subagent unreliability** is the dominant theme: hangs (#21409), false GOAL terminations (#22323), ignored settings (#22267), and poor discovery of when to use skills (#21968) create a fragile agent experience.
- **Shell command state machine bugs**: Commands completing but leaving the agent in "Awaiting user input" (#25166), and interactive prompts causing indefinite hangs (#22465).
- **Configuration drift**: Explicit model pins get rewritten (#29217, #29222), hook timeouts are miscalibrated across migrations (#29125), and event keys don't match (#29124).
- **Auto Memory privacy concerns**: Secrets potentially entering model context before redaction (#26525), invalid patches silently dropped (#26523), and low-signal sessions retried indefinitely (#26522).
- **Terminal/UX friction**: Scrollback clearing on refresh (#28967), flicker on resize (#21924), and incorrect `\n` escape handling (#22466).
- **Tool overflow**: 400+ tools trigger 400 errors from the API (#24246), suggesting a need for smarter tool scoping.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-06

## 1. Today's Highlights

A flurry of issues landed overnight centering on session reliability after desktop upgrades, MCP server timeout cascades, and a JSON-RPC serialization bug corrupting Canvas tool calls. Community engagement remains strongest around a long-standing feature request to cancel enqueued messages before execution, which has accumulated 28 👍 and 11 comments.

## 2. Releases

No new releases were published in the last 24 hours.

## 3. Hot Issues

### 🔥 #1857 — Allow users to cancel or remove enqueued messages before execution
**[OPEN]** · 👍 28 · 💬 11 · Author: dorlugasigal
Messages enqueued via `Ctrl+Q` / `Ctrl+Enter` cannot be removed once the agent is busy or during `/compact`. This is the most upvoted open issue in the window and reflects a common workflow gap — users queue follow-ups while the agent is mid-task but have no escape hatch.

### 🔥 #4551 — Remote SSH clipboard reports "Copied" but text is empty
**[OPEN]** · 👍 1 · Author: Mariushrek
When using Copilot CLI over SSH from macOS Terminal, copy actions succeed silently but nothing reaches the macOS clipboard. Affects remote-development workflows where session continuity depends on clipboard round-trips.

### 🔥 #4725 — Frequent JavaScript heap out of memory
**[OPEN]** · Author: jbulow
The CLI crashes every few minutes with allocation-failure GC logs showing 3.9+ GB RSS. Memory pressure is the top reliability concern for long-running or context-heavy sessions.

### 🔥 #4728 — Auto-update rewrites `copilot.exe`, breaking the desktop app's bundled CLI
**[OPEN]** · Author: doomslayer2k
Running `copilot` in a terminal can silently overwrite the Copilot desktop app's own bundled executable, after which no existing session can reconnect. A critical regression for users who run both CLI and desktop simultaneously.

### 🔥 #4734 — "Worktree missing" on all sessions after desktop 2.98.0 / runtime 1.1.15 upgrade
**[OPEN]** · Author: petrsnd
Every worktree-backed project session reports missing worktrees immediately after the auto-update, blocking all existing and new work. Affected users are told to recreate worktrees from the session menu.

### #4731 — tools/list refresh dispatched into an MCP server still blocked by a cancelled call times out
**[OPEN]** · Author: tecrogue
When a stdio MCP tool call hits the client-side timeout, the runtime immediately dispatches a `tools/list` refresh **into that same server**, which is still processing the cancelled work. The refresh also times out, permanently stripping the server's tools for the process lifetime.

### #4732 — GPT-5 mini stops in the middle of tasks
**[OPEN]** · Author: yurivict
Users report GPT-5 mini generating patches, then immediately making them empty and stopping — with no error signal. Suggests a model-specific truncation or policy issue rather than a CLI bug.

### #4729 — Built-in research agent calls unavailable `github/get_me` tool
**[OPEN]** · Author: ayackel
The research subagent prompt instructs the agent to call `github/get_me` first, but the GitHub MCP server exposed in the same session does not provide it. The subagent visibly struggles to reconcile the mismatch.

### #4721 — Canvas `open_canvas` arguments corrupted by CLI JSON-RPC serialization bug
**[OPEN]** · Author: arisng
The CLI concatenates a trailing `}{}` suffix onto parsed arguments, corrupting JSON-RPC payloads for Canvas extensions. Results in "Unexpected end of JSON input" errors from the server side.

### #4722 — Leading underscores vanish in Copilot Chat due to Markdown emphasis parsing
**[OPEN]** · Author: YiyaoZhangSGM
Text beginning with an underscore (e.g., `_test`) is stripped in both sent messages and chat output because the Markdown parser treats it as unclosed emphasis. Middle underscores and agent-mode output are unaffected.

## 4. Key PR Progress

No new pull requests were merged or opened in the last 24 hours.

## 5. Feature Request Trends

| Trend | Evidence |
|---|---|
| **Input control & cancellation** | #1857 (cancel enqueued messages), #4736 (Ctrl+E accepts inline suggestions) |
| **Context-aware compaction** | #4724 — auto-compact on idle, aligned to model prompt-cache TTL (~5 min) rather than token thresholds alone |
| **Startup-prompt reliability** | #4723 — `--interactive` prompt silently dropped when launching with a local-plugin custom agent |
| **Remote-session parity** | #3498 (mobile rendering), #4551 (clipboard over SSH) — growing demand for parity across remote/mobile/local sessions |
| **MCP resilience** | #4731, #4729 — requests for better timeout handling and tool-discovery consistency in MCP servers |

## 6. Developer Pain Points

1. **Session continuity after updates** — Issues #4728 and #4734 both show that the desktop app's auto-update path can silently invalidate CLI sessions and worktrees, with no clear recovery guidance.

2. **MCP server fragility** — A single cancelled tool call can permanently disable an entire MCP server's tool list for the process lifetime (#4731), and built-in agents may reference tools that don't exist in the current session (#4729).

3. **Memory pressure** — The heap OOM in #4725 points to sustained memory growth during long sessions, likely driven by unbounded context accumulation.

4. **Non-interactive / automation breaking** — The `--interactive` startup-prompt drop (#4723) and the `streaming: false` delta leak (#4677, now closed) both indicate that non-interactive and programmatic usage paths are not keeping pace with feature development.

5. **Rendering & formatting bugs** — Trailing underscores disappearing (#4722), clipboard not round-tripping over SSH (#4551), and remote session UI failing on mobile (#3498) suggest the rendering layer lacks parity across output channels.

---

*Digest generated from [github.com/github/copilot-cli](https://github.com/github/copilot-cli) issues updated between 2026-09-05 and 2026-09-06.*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-06

---

## 1. Today's Highlights

Two bugs closed today address persistent pain points: a Windows Zed IDE ACP launch failure and a recurring authorization failure on Linux. Meanwhile, an open PR (#2513) tackles double-encoded tool-call arguments from the Moonshot API, and a new bug (#2635) reports character-level text loss in the VS Code extension's streamed chat rendering.

---

## 2. Releases

No new releases in the past 24 hours.

---

## 3. Hot Issues

| # | Title | Status | Why It Matters | Community Reaction |
|---|-------|--------|---------------|-------------------|
| #2635 | VS Code extension: streamed chat text drops individual characters | OPEN | Directly impacts developer productivity; verified the model output is correct, so the bug sits in the render/copy layer of the extension. | 0 👍, 0 comments |
| #1350 | Frequent `Authorization failed, please check your login status` | CLOSED | Auth instability disrupts workflow; reported on Debian 12 with kimi-for-coding model (v1.17.0). | 0 👍, 0 comments |
| #1284 | Does not launch in Zed IDE ACP panel in Windows | CLOSED | Blocks Windows users who rely on Zed as their primary IDE; affects Kimi Code CLI v1.14.0. | 0 👍, 1 comment |
| #1349 | Shell prompt no longer shows cwd/git branch; request configurable display | CLOSED | Developers lose contextual awareness (repo, branch) during interactive sessions — a regression in UX from recent versions. | 0 👍, 0 comments |

---

## 4. Key PR Progress

| # | Title | Status | Description |
|---|-------|--------|-------------|
| #2513 | fix(kosong): recursively decode double-encoded tool-call arguments | OPEN | Fixes a Moonshot API quirk where `function.arguments` returns nested values as JSON strings (double-encoded). After a single `json.loads`, values like `todos` remained strings and failed Pydantic validation. The PR introduces a shared `decode_tool_arguments` helper that recursively decodes until values are proper types. Author: **nitishagar**. |

---

## 5. Feature Request Trends

- **Configurable shell prompt display** — Issue #1349 reflects a broader desire for customizable prompt output, specifically restoring cwd and git branch info that was removed in recent versions.
- **Cross-IDE compatibility** — Issue #1284 highlights demand for deeper integration with emerging IDEs like Zed, beyond the mainstream VS Code offering.
- **Rendering reliability in the VS Code extension** — Issue #2635 underscores the need for robust streaming text rendering, as character drops at the presentation layer erode trust in the tool.

---

## 6. Developer Pain Points

1. **Authentication instability** — Repeated `Authorization failed` errors (Issue #1350) suggest login/session management is a fragile area, particularly on Linux.
2. **IDE integration gaps** — Windows Zed support (Issue #1284) remains unaddressed, leaving a segment of the developer community without CLI access in their preferred editor.
3. **Prompt regression** — The removal of cwd/git branch from the shell prompt (Issue #1349) was perceived as a step backward in usability, with users explicitly requesting configurability.
4. **Streaming render bugs** — Character-level dropouts in the VS Code chat panel (Issue #2635) point to a fragile rendering pipeline that desynchronizes from the actual model output.

---

*Links:*
- [Issue #1284](https://github.com/MoonshotAI/kimi-cli/issues/1284)
- [Issue #1350](https://github.com/MoonshotAI/kimi-cli/issues/1350)
- [Issue #1349](https://github.com/MoonshotAI/kimi-cli/issues/1349)
- [Issue #2635](https://github.com/MoonshotAI/kimi-cli/issues/2635)
- [PR #2513](https://github.com/MoonshotAI/kimi-cli/pull/2513)

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑09‑06

## 1. Today’s Highlights
The community is focused on reliability and UX refinements for the Desktop and TUI clients. Several PRs address event‑stream reconnection, SQLite concurrency, and request‑queue timeouts, while high‑impact issues surface persistent bugs in file indexing, session migration, and large‑file rendering.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [#32747](https://github.com/anomalyco/opencode/issues/32747) | `@` file mentions do not include files created after startup | Stale search state forces restarts, breaking workflow continuity. | 15 comments, 13 👍 |
| [#35009](https://github.com/anomalyco/opencode/issues/35009) | High resource usage after updating from 1.17.11 to 1.17.13 | Memory/CPU regression affects performance on normal conversations. | 10 comments, 2 👍 |
| [#34030](https://github.com/anomalyco/opencode/issues/34030) | Unable to invoke third‑party models added by enterprises in GitHub Copilot | Blocks enterprise users from using company‑specific models. | 9 comments, 2 👍 |
| [#25430](https://github.com/anomalyco/opencode/issues/25430) | `format.json_schema.retryCount` is ignored | Structured‑output requests fail immediately without retry, breaking deterministic pipelines. | 7 comments |
| [#16678](https://github.com/anomalyco/opencode/issues/16678) | “Failed to run the query ‘CREATE TABLE `project`’” and logging issues | Migration/exit race condition can corrupt database state. | 6 comments, 1 👍 |
| [#28695](https://github.com/anomalyco/opencode/issues/28695) | Session‑lifecycle context hooks for persistent plugin state | Enables plugins to maintain state across sessions—a foundational feature for advanced workflows. | 6 comments, 2 👍 |
| [#35690](https://github.com/anomalyco/opencode/issues/35690) | Session history disappears after updating | Auto‑update to v1.17.14 hides older sessions, causing data‑loss concerns. | 6 comments |
| [#31916](https://github.com/anomalyco/opencode/issues/31916) | TUI hangs on ‘Preparing to write…’ with large file content | Unbounded diff rendering freezes the TUI for files >150 lines. | 5 comments, 1 👍 |
| [#35741](https://github.com/anomalyco/opencode/issues/35741) | WebChat: LLM hallucinates user response | Agent answers its own clarifying questions, degrading interactive sessions. | 5 comments, 1 👍 |
| [#35538](https://github.com/anomalyco/opencode/issues/35538) | EmbeddedResource with text/markdown from Jira MCP omitted | MCP attachments are silently dropped, breaking remote‑resource workflows. | 4 comments |

## 4. Key PR Progress
| # | Title | Type | Summary |
|---|-------|------|---------|
| [#47559](https://github.com/anomalyco/opencode/pull/47559) | feat(core): add independent GPT and Claude tool optimization | Feature | Keeps model‑specific prompt selection and tool optimization in `optimize.ts` with independently configurable plugin registrations. |
| [#47394](https://github.com/anomalyco/opencode/pull/47394) | fix(ui): lighten dark contrast icon buttons | Bug fix | Gives shared contrast icon buttons a dedicated background to improve dark‑mode readability. |
| [#47224](https://github.com/anomalyco/opencode/pull/47224) | fix(provider): retain Zen discovery transport metadata | Bug fix | Resolves Zen authenticated model discovery dropping per‑model metadata by merging endpoint‑only IDs into empty provider entries. |
| [#47574](https://github.com/anomalyco/opencode/pull/47574) | feat(app): pulse the status dot while the event stream reconnects | Feature | Provides visual feedback during reconnection instead of leaving the status dot static. |
| [#47570](https://github.com/anomalyco/opencode/pull/47570) | feat(app): manage recently closed projects | Feature | Adds a “Recently closed” list (cap 5) to the home sidebar, enabling quick re‑opening of prior projects. |
| [#47573](https://github.com/anomalyco/opencode/pull/47573) | fix(app): refresh queued inputs when the connection returns | Bug fix | Ensures `session.pending` inputs are re‑loaded on reconnect by tying resource creation to the session ID. |
| [#47572](https://github.com/anomalyco/opencode/pull/47572) | fix(app): time out requests the server never answers | Bug fix | Prevents dead sockets (e.g., from a sleeping device) from wedging the request queue with minute‑long TCP timeouts. |
| [#47571](https://github.com/anomalyco/opencode/pull/47571) | fix(client): detect stalled event streams and resync on foreground | Bug fix | Detects stalled SSE connections after device sleep and forces a resync, rather than reporting a false “connected” status. |
| [#47561](https://github.com/anomalyco/opencode/pull/47561) | fix(client): coalesce catalog refetches from event bursts | Performance | Coalesces rapid `mcp.status.changed` events to avoid 192 API fetches in 7 seconds during directory settlement. |
| [#47444](https://github.com/anomalyco/opencode/pull/47444) | fix(app): scroll overflowing composer controls | Bug fix | Makes the agent/model/variant controls horizontally scrollable to prevent overflow in narrow windows. |

## 5. Feature Request Trends
- **Session‑lifecycle hooks** – Persistent plugin state across sessions (Issue #28695).
- **Unified client directories** – Merge Desktop and TUI session/plugin storage (Issue #35703).
- **Side‑panel browser preview** – In‑app web preview for real‑time editing, similar to Codex (Issue #35751).
- **Explicit reasoning‑model support** – Clear documentation/configuration for Claude thinking/reasoning on compatible providers (Issue #35733).
- **Improved large‑file handling** – Bounded diff rendering and non‑blocking TUI operations for large file writes (Issues #31916, #32046).
- **Structured‑output retry logic** – Honor `retryCount` in JSON‑schema requests (Issue #25430).
- **Cross‑platform remote session usage** – Fix remote‑server session/project loading from macOS to Windows (Issue #42627).

## 6. Developer Pain Points
- **Stale state after updates** – File‑mention index not refreshed (#32747) and session history hidden post‑migration (#35690, #35750).
- **SQLite concurrency** – Multiple processes contend for the write lock, causing `SQLITE_BUSY` errors (#47566) with a fix in PR #47567.
- **High resource usage** – Memory/CPU regressions after version bumps (#35009).
- **TUI/desktop hangs** – Unbounded diff rendering freezes the UI (#31916, #32046).
- **Session cross‑visibility** – Sessions created in Desktop do not appear in TUI session list (#29071).
- **Provider/model integration gaps** – Third‑party Copilot models unavailable (#34030), Bedrock credentials not auto‑discovered (#35798), and custom OpenAI‑compatible providers lacking a clear tool‑calling path (#35732).
- **MCP attachment handling** – Text/markdown resources from MCP servers are omitted (#35538).
- **Plugin update caching** – `--force` still pulls cached plugin versions (#35742).
- **Enterprise subscription billing confusion** – Monthly‑usage percentage calculation appears to sum per‑model caps rather than actual spend (#47547).

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-06

## 1. Today's Highlights

Pi v0.85.1 shipped with **GPT-6 Astra** support via OpenAI API keys and Codex subscriptions, though early adopters report routing issues through Copilot endpoints. A cluster of packaging defects in 0.85.0 — missing `@earendil-works/pi-server` and `@earendil-works/pi-client` dependencies — triggered rapid follow-up fixes and a new v0.85.1 release. Windows TUI regressions remain the dominant community frustration, with three separate high-visibility issues filed this week.

---

## 2. Releases

**v0.85.1** — [GitHub](https://github.com/earendil-works/pi/releases/tag/v0.85.1)
- Added **GPT-6 Astra** as a provider option through OpenAI API keys and OpenAI Codex subscriptions.
- Addresses dependency publishing issues from v0.85.0 (see Issues #9132, #9218).

---

## 3. Hot Issues

| # | Title | Comments | Why It Matters |
|---|-------|----------|----------------|
| [#7547](https://github.com/earendil-works/pi/issues/7547) | How do you use Pi on Windows? | 52 👍2 | Largest open discussion on Windows compatibility; requests a unified strategy for the many ways Pi runs on Windows rather than scattering effort across individual workarounds. |
| [#5023](https://github.com/earendil-works/pi/issues/5023) | Terminal scrolls to beginning without reason | 19 👍3 | Random, unexplained terminal buffer jumps during model output — affects workflow continuity and is difficult to reproduce deterministically. |
| [#8896](https://github.com/earendil-works/pi/issues/8896) | `/export HTML` silently drops `display:false` context | 8 | Exported HTML transcripts lose custom messages that were intentionally hidden in the TUI, breaking session review workflows. |
| [#6300](https://github.com/earendil-works/pi/issues/6300) | Input line redrawn on every keystroke (Windows) | 8 | Each character appears on a new line in cmd.exe and Windows Terminal — makes the TUI effectively unusable for affected users. |
| [#9132](https://github.com/earendil-works/pi/issues/9132) | 0.85.0 missing `pi-server` dependency | 5 👍5 | Published `dist/cli.js` statically imports `@earendil-works/pi-server` without declaring it, breaking fresh installs. Directly prompted the v0.85.1 patch. |
| [#8684](https://github.com/earendil-works/pi/issues/8684) | `PI_OFFLINE` silently disables model discovery | 5 | Environment variable documented as disabling only housekeeping network ops, but in practice also blocks all provider model-catalog discovery — undocumented and surprising. |
| [#9212](https://github.com/earendil-works/pi/issues/9212) | Sonnet-5 edit tool calls truncated via gateway | 3 | 13% of `edit` tool calls from `anthropic/claude-sonnet-5` arrive as `edits:[{}]` through vercel-ai-gateway — schema validation failures in production agentic sessions. |
| [#7317](https://github.com/earendil-works/pi/issues/7317) | OpenAI Responses: stateful continuation & compaction | 4 👍1 | Pi currently replays full session history after each tool result; the Responses API supports `previous_response_id` for server-side compaction, which would drastically reduce token usage on long runs. |
| [#5200](https://github.com/earendil-works/pi/issues/5200) | IME candidate window stuck in WezTerm | 3 | CJK input candidate window doesn't follow cursor in WezTerm on WSL — blocks non-Latin input users. Other TUI apps in the same env work correctly. |
| [#9209](https://github.com/earendil-works/pi/issues/9209) | GPT-6 Astra routed to unsupported Chat Completions endpoint | 3 | Copilot's GPT-6 Astra rejects `/chat/completions` with `unsupported_api_for_model`; Pi needs to route this model to the correct endpoint. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#9222](https://github.com/earendil-works/pi/pull/9222) | Reject reload during active session operations | Open | Fixes a race in RPC mode where an extension reload during tool execution causes the wrapper to access an invalidated runner, sending error results to the model. |
| [#9096](https://github.com/earendil-works/pi/pull/9096) | Add Meta provider with Muse subscription OAuth | Open | New sub-provider for Meta's Muse models. Notable quirk: refresh token is re-minted daily from the identity token rather than a rolling refresh. Streaming is currently burst-based. |
| [#9219](https://github.com/earendil-works/pi/pull/9219) | Preserve host UI prototype methods in `wrapUIPromptContext` | Closed | Fixes object-spread behavior that lost embedder-provided UI context methods. |
| [#9214](https://github.com/earendil-works/pi/pull/9214) | Invoke skills and prompt templates mid-sentence | Closed | Allows `/skill:name args` and `/template args` to expand inline anywhere in a message, not just at the start. Resolves feature request #8457. |
| [#9215](https://github.com/earendil-works/pi/pull/9215) | Allow zero-row custom footers | Closed | Fixes fullscreen mode leaving a blank terminal row when a custom footer renders empty. |
| [#9170](https://github.com/earendil-works/pi/pull/9170) | Declare `pi-server` runtime dependency | Closed | Direct fix for the v0.85.0 packaging defect — adds missing `@earendil-works/pi-server` to dependencies. |
| [#9172](https://github.com/earendil-works/pi/pull/9172) | Prevent broken package root publication | Closed | Follow-up to #9170; adds safeguards to prevent the same class of dependency omission from being published again. |
| [#9163](https://github.com/earendil-works/pi/pull/9163) | Simplify clipboard handling | Closed | Replaced the heavy Rust clipboard library with a lighter approach, enabling NixOS builds. |
| [#9137](https://github.com/earendil-works/pi/pull/9137) | Add Nix flake | Open | WIP Nix flake for declarative Pi installs, contributed by @mitsuhiko. |
| [#7610](https://github.com/earendil-works/pi/pull/7610) | Add LLM Gateway providers | Open | Adds [LLM Gateway](https://llmgateway.io) as built-in `openai-completions` providers (OpenRouter-style router). |

---

## 5. Feature Request Trends

- **New model provider integrations** — Meta/Muse (#9096), LLM Gateway (#7610), and Requesty (#5473) all reflect demand for more routing choices beyond the core OpenAI/Anthropic pairing.
- **OpenAI Responses API depth** — Stateful continuation (#7317), server-side compaction (#6676), async tool calling (#9113), and top-level `instructions` support (#8734) show the community pushing Pi to match the full capabilities of newer model APIs.
- **Mid-sentence command invocation** — Skills and templates now supported inline (#9214), closing a long-requested UX gap (#8457).
- **Windows-first parity** — Repeated requests for a coherent Windows strategy (#7547) and fixes for input/IME/fullscreen rendering suggest Windows support is a priority area.
- **Local / offline-first workflows** — `PI_OFFLINE` behavior clarification (#8684) and Ollama streaming fixes (#9216) indicate growing local-model usage.

---

## 6. Developer Pain Points

1. **Windows TUI regressions** — Three distinct bugs (input line redraw #6300, IME cursor #5200, fullscreen image rendering #9169) and one meta-discussion (#7547) signal that Windows TUI stability is a persistent gap.
2. **Packaging / dependency omissions** — v0.85.0 shipped without `pi-server` and `pi-client` declared (#9132, #9218), breaking fresh installs. A second related bug (#9223) caused `bun run eval` to recurse infinitely. The publish pipeline needs stronger guards.
3. **Gateway routing & caching inaccuracies** — Vercel AI Gateway issues span incorrect model routing (#9209, #9211), truncated tool calls (#9212), and misapplied cache pricing (`cacheWrite1h` billed at 5m rates) (#9210). Multi-provider gateway users are hit hardest.
4. **Session compaction edge cases** — Custom session-compact handlers miss the immediate overflow retry (#9051), and auto-compaction stops re-triggering after the first run with Ollama (#9216). Long agentic sessions remain fragile.
5. **Slash-command autocomplete races** — Fast typing or IME commit can submit partial commands like `/re` as messages before the autocomplete menu renders (#9220), causing confusing user experience.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-06

## 1. Today's Highlights

The Qwen Code team shipped three nightly/preview builds (v0.23.0-nightly and v0.23.1-preview) featuring a major web-shell workflow visualization feature and performance improvements to session derivation. Meanwhile, the community is actively addressing export-file bloat (19.5 MB empty transcripts) and MCP config persistence bugs that block reliable daemon restarts.

---

## 2. Releases

**v0.23.1-preview.0** and **v0.23.0-nightly.20260905** (two variants) were published in the last 24h.

Key changes:
- **[feat(web-shell)] visualize and manage dynamic workflow runs** — PR [#10594](https://github.com/QwenLM/qwen-code/pull/10594) adds a workflow inspection surface for dynamic runs in the Web Shell.
- **[perf(web-shell)] derive the session workflow project** — reduces redundant per-render derivations of the session workflow projection.

> ⚠️ Nightly release **v0.23.0-nightly.20260905.0c945a6136** failed its `integration_docker` job ([#11138](https://github.com/QwenLM/qwen-code/issues/11138)); preview **v0.23.1-preview.0** had three consecutive `quality`-check failures ([#11098](https://github.com/QwenLM/qwen-code/issues/11098), [#11114](https://github.com/QwenLM/qwen-code/issues/11114), [#11122](https://github.com/QwenLM/qwen-code/issues/11122)).

---

## 3. Hot Issues

| # | Title | Why It Matters | Activity |
|---|-------|---------------|----------|
| [#11091](https://github.com/QwenLM/qwen-code/issues/11091) | mermaid (~6 MB) still flattened into exported transcript | Exported HTML remains bloated even after the renderer was externalized in #9812; hurts shareability of transcripts. | 6 comments · P2 |
| [#7771](https://github.com/QwenLM/qwen-code/issues/7771) | Persisted `mcp_config` not loaded at daemon startup | MCP servers configured in settings are silently ignored after a restart, breaking any automation relying on them. | 5 comments · P1 |
| [#10710](https://github.com/QwenLM/qwen-code/issues/10710) | Killed-turn messages hidden on session reload | Assistant output from a turn torn down mid-flight is persisted but never surfaced, corrupting session state. | 5 comments · P2 · **Closed** |
| [#11031](https://github.com/QwenLM/qwen-code/issues/11031) | Stop embedding Web Shell runtime in every HTML export | Each exported file is ~19.5 MB because React + Web Shell runtime is duplicated per session; a P1 performance + UI bug. | 5 comments · P1 |
| [#10780](https://github.com/QwenLM/qwen-code/issues/10780) | Reconnect floods transport with full history replay | Long-lived daemon sessions (10⁵–10⁶ tokens) cause multi-MB floods on every client reconnect, stalling unrelated sessions. | 4 comments · P1 · **Closed** |
| [#9645](https://github.com/QwenLM/qwen-code/issues/9645) | Left-sidebar spinner drops mid-turn on long tasks | UI indicator lies to users about turn status; follow-up to #9487. | 4 comments · P2 · **Closed** |
| [#10989](https://github.com/QwenLM/qwen-code/issues/10989) | Daemon prompt authority only polled where sidebar is mounted | The #9487 fix is inert in the VS Code companion because the live-prompt fetch is scoped to the sidebar mount. | 3 comments · P2 |
| [#11119](https://github.com/QwenLM/qwen-code/issues/11119) | Background shell output silently dropped on session recycle | Sessions can wedge when `run_shell_command` output and wake notifications are lost after a runtime recycle. | 3 comments · P1 |
| [#10865](https://github.com/QwenLM/qwen-code/issues/10865) | Session workflow projection derived 3× per render | Redundant derivations rebuild an index each time; a perf enhancement flagged as ready-for-agent. | 3 comments · P2 |
| [#11146](https://github.com/QwenLM/qwen-code/issues/11146) | Pre-aborted tool requests can block behind active batch | `CoreToolScheduler.schedule()` leaves cancelled requests waiting, wasting slots and stalling subsequent work. | 2 comments · P2 |

---

## 4. Key PR Progress

| # | Title | Author | Summary |
|---|-------|--------|---------|
| [#11086](https://github.com/QwenLM/qwen-code/pull/11086) | `feat(serve): scope extensions to workspace runtimes` | @ytahdn | Makes the global extension catalog per-workspace; reconciles extension state into live runtimes and updates the composer `@` menu. |
| [#11003](https://github.com/QwenLM/qwen-code/pull/11003) | `feat: delegate a subagent turn to an external agent over ACP` | @wenshao | Subagent definitions can now declare an `executor` block and drive turns over ACP in an external process (Claude Code first), re-publishing everything as the subagent's output. |
| [#10439](https://github.com/QwenLM/qwen-code/pull/10439) | `ci: watch /resolve for consecutive failures and file a tracking issue` | @wenshao | Scheduled watch on `@qwen-code /resolve`; files one tracking issue on consecutive failures, updates when the picture changes, closes on success. |
| [#10938](https://github.com/QwenLM/qwen-code/pull/10938) | `feat(web-shell): make Session Workflow dependencies navigable` | @yiliang114 | Closes navigation/shape/docs gaps from #8583; plan DAG now leads with the step, not its status. |
| [#9466](https://github.com/QwenLM/qwen-code/pull/9466) | `refactor: anchor rewind mapping to stable prompt identity` | @yiliang114 | Rewind resolves targets through persisted prompt identity rather than positional turn order, surviving session resume and headless `-p --restore`. |
| [#11094](https://github.com/QwenLM/qwen-code/pull/11094) | `test(integration): deflake the /compress E2E event budget` | bot | Disables the background memory extractor and widens the wait for compression telemetry in the E2E suite. |
| [#11054](https://github.com/QwenLM/qwen-code/pull/11054) | `feat(web-shell): add headless global turn navigation` | @doudouOUC | Phase 2A of session-wide turn navigation: bounded turn metadata, historical transcript caches, exact live/persisted turn locators, and public React hooks. |
| [#11145](https://github.com/QwenLM/qwen-code/pull/11145) | `fix(serve): load persisted MCP config after ACP preheat at startup` | @kabishou11 | Calls `reconcileMcpConfiguration()` immediately after ACP preheat, fixing the #7771 startup-persistence gap. |
| [#11144](https://github.com/QwenLM/qwen-code/pull/11144) | `fix(cli): barrier live transcript reads behind tool-result writes` | @kabishou11 | Prevents concurrent session loads from observing half-written tool turns; routes restore cleanup through `finalizeDanglingForRestore`. |
| [#11103](https://github.com/QwenLM/qwen-code/pull/11103) | `ci: stop failing the Test job on a starved vitest worker RPC alone` | @yiliang114 | Adds `classify-infra-flake.mjs` so a worker-IPC timeout surfaces as a warning rather than a hard failure. |

---

## 5. Feature Request Trends

1. **Session-wide turn navigation** — Multiple PRs (#11054, #11053) and issues point to sustained interest in headless and client-side global turn navigation across long sessions.
2. **Named/owner-scoped channel sessions** — PRs #11015 (worktree reset) and #8927 (session rotation bounds) show the community pushing for finer-grained session lifecycle control.
3. **External agent delegation over ACP** — PR #11003 reflects demand to route subagent turns to external coding agents (Claude Code, etc.) rather than in-process execution.
4. **Workspace-scoped extensions** — PR #11086 signals a trend toward decoupling extension catalogs from the global daemon into per-workspace runtimes.
5. **Export transparency & size reduction** — Issues #11091, #11031, #11100, and #11142 form a cluster around making exported transcripts smaller, leaner, and free of daemon runtime dependencies.

---

## 6. Developer Pain Points

- **Export bloat** — Transcripts are 19.5 MB for empty sessions because the full React/Web Shell runtime and even 6 MB mermaid bundles are embedded per file. This is the most-discussed pain point across issues #11031, #11091, #11100, and #11142.
- **Daemon restart reliability** — MCP config (#7771, fixed in #11145), background shell output drops (#11119), and reconnect floods (#10780) all point to fragility in long-lived `qwen serve` sessions after restarts or reconnects.
- **Concurrent session load races** — Half-written tool turns (#11144, #9704) and pre-aborted requests blocking active batches (#11146) reveal ongoing concurrency issues in the ACP transport layer.
- **CI flakiness masquerading as failures** — Vitest worker IPC timeouts (#11103) and macOS E2E shard deaths (#11134) are costing developer time; the team is building infrastructure to classify and retry these rather than fail hard.
- **UI state desync in sidebar** — Spinner drops mid-turn (#9645, #10989) and Cmd+A selecting the page instead of the composer (#11108) show that the web-shell UI still has subtle reactivity bugs, particularly in the VS Code companion where sidebar mount scoping matters.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / Codewhale Community Digest — 2026-09-06

---

## 1. Today's Highlights

The project continues its transition from `deepseek-tui` to `codewhale`, with **v0.9.12** now live and the legacy npm package officially deprecated. The community is actively addressing Windows computer-use reliability bugs and streamlining the Fleet menu UX, while EPIC-005 drives the ongoing TUI crate decomposition.

---

## 2. Releases

**v0.9.12** — [GitHub](https://github.com/Hmbown/Codewhale)

Latest release ships with the `codewhale` binary and npm wrapper; the legacy `deepseek-tui` package is deprecated and will receive no further releases. Operator handoff documentation (`TAKEOVER-PROMPT-20260902-NIGHT.md`) and the product PRD are now the authoritative references. [Issue #5573](https://github.com/Hmbown/Codewhale/issues/5573) serves as the starting point for the v0.9.12 milestone.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5620](https://github.com/Hmbown/Codewhale/issues/5620) | Context pressure warning is transient; agent doesn't proactively react | Silent context degradation defeats a key safety signal — medium severity but erodes reliability over long sessions. |
| [#5909](https://github.com/Hmbown/Codewhale/issues/5909) | `write_file` silently converts CRLF → LF on overwrite | Inconsistent with `edit_file`, which preserves line endings. Affects Windows users across the board. |
| [#5908](https://github.com/Hmbown/Codewhale/issues/5908) | Win32 computer-use reports input success after PowerShell failure | Backend returns `{action_sent: true}` even when the subprocess never ran — dangerous for automated workflows. |
| [#5906](https://github.com/Hmbown/Codewhale/issues/5906) | Fleet claims: parked/cancelled agents hold write claims indefinitely | Sibling work on the same worktree path is refused with `write-scope contention` even after the parent cancels — blocks parallel agent execution. |
| [#5904](https://github.com/Hmbown/Codewhale/issues/5904) | web fetch: JS-shell 200s fail extraction with no retry | Cache-state dependent; agents report URLs as "unfetchable" when they actually need browser escalation. Intermittent and hard to reproduce. |
| [#5888](https://github.com/Hmbown/Codewhale/issues/5888) | Fleet menu has too many options at once | Founder feedback from v0.9.12 dogfooding — the surface makes it hard to identify the next useful action. |
| [#5887](https://github.com/Hmbown/Codewhale/issues/5887) | MCP startup stalls on "20 connecting" | Users can't tell if progress is being made or a server is stalled; no per-server progress feedback. |
| [#5482](https://github.com/Hmbown/Codewhale/issues/5482) | EPIC: localize docs to Chinese | Growing Chinese user base blocked by English-only docs; stale source documents compound the problem. |
| [#2323](https://github.com/Hmbown/Codewhale/issues/2323) | Chinese IME not supported (1 👍) | Pinyin input leaks into model input areas; task-hint overlay doesn't hide during IME composition. Long-open issue with sustained interest. |
| [#5820](https://github.com/Hmbown/Codewhale/issues/5820) **[CLOSED]** | Ollama input budget collapses to 1024 tokens on 32K models | Default output reservation of 64K clamps the window — resolved but illustrative of local-model config friction. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5911](https://github.com/Hmbown/Codewhale/pull/5911) | `write_file` preserves existing CRLF line endings | OPEN | Fixes #5909 — both write paths now normalize and restore line-ending style consistently. |
| [#5910](https://github.com/Hmbown/Codewhale/pull/5910) | Win32 input actions fail truthfully; targeted mouse-down presses | **CLOSED** | Fixes #5908 — User32 type now loaded per-process; `left_mouse_down` actually sends the press. |
| [#5903](https://github.com/Hmbown/Codewhale/pull/5903) | Win32 backend reports PowerShell failures truthfully | **CLOSED** | Fixes #5896 — `withUser32()` no longer swallows subprocess errors. |
| [#5912](https://github.com/Hmbown/Codewhale/pull/5912) | Injectable win32 runner for host-agnostic backend tests | OPEN | Test-only refactor — makes the win32 backend mockable without touching production logic. |
| [#5897](https://github.com/Hmbown/Codewhale/pull/5897) | Show MCP startup progress per-server | OPEN | Fixes #5887 — consumes connection tasks as they complete instead of buffering until the slowest finishes. |
| [#5905](https://github.com/Hmbown/Codewhale/pull/5905) | Prioritize the Fleet menu surface | OPEN | Closes #5888 — reduces `/fleet` verbs from 14 to 5 primary; nine others moved under `/fleet help`. |
| [#5907](https://github.com/Hmbown/Codewhale/pull/5907) | List custom themes in `/theme` picker | OPEN | Closes #5901 — discovers overlays from `$CODEWHALE_HOME/themes/` and appends them to the picker. |
| [#5899](https://github.com/Hmbown/Codewhale/pull/5899) | Show published Cargo sources without "(dev)" marker | OPEN | Fixes #5891 — unstamped crates.io packages now report clean version strings. |
| [#5895](https://github.com/Hmbown/Codewhale/pull/5895) | Scope HarmonyOS cleanup to owned temporary files | **CLOSED** | Fixes #5894 — downloads now go to a unique owned directory; `rm` only removes that directory. |
| [#5893](https://github.com/Hmbown/Codewhale/pull/5893) | Verify all crate tarballs before first upload | **CLOSED** | Fixes #5892 — release script now runs a dry-run across all 21 crates before any upload. |

---

## 5. Feature Request Trends

- **Fleet UX simplification** — #5888 → #5905: users want a smaller, scannable menu with deeper drill-downs rather than a flat list of 14 verbs.
- **Voice input with on-device STT** — #5846: on-device speech recognition as default, with a wired API-key fallback, keyboard shortcut, and level animation.
- **Custom theme discovery** — #5901 → #5907: user-authored theme overlays should appear in the `/theme` picker alongside compiled themes.
- **Chinese documentation** — #5482: full localization epic driven by a growing Mandarin-speaking user base.
- **ACP session management** — #5863 / #5864 (both closed): editor clients need `session/list` and `session/load` to enumerate and resume Codewhale sessions.
- **Reasoning-only config** — #5867 (closed): users want the `MAX_REASONING_ONLY_REPROMPTS` hard limit to be configurable via a `[reasoning_only]` section.

---

## 6. Developer Pain Points

- **Windows computer-use reliability** — Three issues this week (#5908, #5896, #5894) trace back to the same root: the Win32 backend's PowerShell subprocess model is fragile (per-call type registration, swallowed errors, overly aggressive cleanup). The fix cascade (#5903 → #5910 → #5912) shows the team is iterating hard, but Windows users will feel the instability until the injectable runner lands.
- **MCP startup opacity** — #5887: the "20 connecting" stall leaves users unable to diagnose whether a server is slow, stalled, or the count is stale. The per-server progress PR (#5897) directly addresses this.
- **Crate publish verification gap** — #5892 / #5891: the v0.9.12 release exposed that 16 embedded plugin files were outside the package root, yet the dry-run returned exit 0. The new pre-upload verification (#5893) and dev-marker fix (#5899) close these gaps.
- **Write-tool inconsistency** — #5909: `write_file` and `edit_file` historically diverged on line-ending preservation, surprising Windows users. The fix (#5911) aligns them.
- **Fleet claim leaks** — #5906: parked or cancelled agents holding write claims indefinitely is a concurrency bug that blocks legitimate sibling work — a high-severity issue for multi-agent workflows.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*