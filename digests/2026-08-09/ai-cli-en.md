# AI CLI Tools Community Digest 2026-08-09

> Generated: 2026-08-09 02:10 UTC | Tools covered: 10

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
**Date: 2026-08-09**

---

## 1. Ecosystem Overview

The AI CLI landscape in August 2026 is defined by intense convergence around agent reliability, cross-surface session continuity, and platform stability. The "big four" incumbents (Claude Code, Codex, Gemini CLI, Copilot CLI) face competitive pressure from ambitious open-source challengers (OpenCode, Pi, CodeWhale), while Qwen Code and Kimi Code fill niche positions around open model access and cross-session memory. A defining pattern across all tools is the shift from single-turn assistants toward persistent, multi-session agent architectures — and the community frustration when those architectures fail silently.

---

## 2. Activity Comparison

| Tool | Hot Issues (24h) | PRs Updated (24h) | Release |
|------|:-:|:-:|------|
| **Claude Code** | 10 | 1 | v2.1.226 (bug fixes) |
| **OpenAI Codex** | 10 | 10 | v0.148.0-alpha.5 |
| **Gemini CLI** | 10 | 9 | v0.56.0-nightly |
| **GitHub Copilot CLI** | 10 | 0 | None |
| **OpenCode** | 10 | 10 | None |
| **Pi** | 10 | 10 | None |
| **Qwen Code** | 10 | 10 | v0.21.8 |
| **CodeWhale (DeepSeek TUI)** | 10 | 10 | v0.9.5 |
| **Kimi Code** | 2 | 0 | None |
| **Grok Build** | — | — | No activity |

*Note: "Hot Issues" reflects issues with meaningful community discussion or updates in the digest window, not total open issues.*

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Need |
|-------|---------------|---------------|
| **Persistent / cross-session memory** | Kimi Code (#1283), Qwen Code (#8724, #8718), OpenCode, Pi, CodeWhale | Users want tool state, preferences, and project context retained across sessions — not re-established each time. |
| **Agent-to-agent orchestration** | Gemini CLI (#28738 merged), OpenCode (#27167), Qwen Code (#8730), CodeWhale (#5270) | Subagent delegation, recursive calling, and unified task surfaces are top-requested capabilities. |
| **Session resilience & reliability** | All tools | Streaming retry logic (Pi, Codex), subagent hang handling (Gemini), context-compaction timing (Pi, CodeWhale), and stale-state cleanup (CodeWhale, OpenCode) are universal pain points. |
| **Cross-platform / cross-surface continuity** | Claude Code (#29006, #67303), Codex (#27284, #34076), Qwen Code (#8092) | Desktop ↔ CLI ↔ mobile session handoff remains imperfect across every major tool. |
| **Transparent model selection & cost control** | Claude Code (#79337, #60093), Pi (#7811, #7817), Copilot CLI (#4397) | Undisclosed model switches, silent billing tier changes, and opaque cost implications are the #1 trust issue. |
| **MCP / extensibility parity** | Claude Code (#19054), OpenCode (#31554), CodeWhale (#5130), Gemini CLI | Users expect consistent tool/metadata behavior across CLI, IDE extensions, and web surfaces. |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Pi | CodeWhale | Qwen Code | Kimi Code |
|-----------|------------|-------------|-----------|------------|---------|----|----------|----------|----------|
| **Primary focus** | Enterprise reliability, billing transparency | Rust rewrite, Computer Use, async hooks | Subagent orchestration, AST-aware tooling | GitHub-integrated workflows | Session goals, multi-instance isolation | Provider agnosticism, auto-compaction | Provider-agnostic, turn-loop honesty | Open-model access, DashScope native | Cross-session memory |
| **Target user** | Professional teams on Max/Pro plans | Power users, Windows Desktop users | Developers wanting agent recursion | GitHub-centric teams | Open-source contributors | Multi-provider power users | Rust-native users, high-fan-out workloads | Alibaba/DashScope users | Long-context personalization |
| **Technical approach** | Monolithic CLI with Desktop integration | Rust-first, gRPC code-mode host, hook generalization | Google-native agent graph, multi-agent delegation | GitHub ACP protocol, Copilot Enterprise integration | Go/TUI, SQLite-backed event sourcing | Bun/Node runtime, extension-driven | Rust monolith (682K-line crate), Runtime API | TypeScript, Web Shell target, turn-based runtime | Moonshot-native, persistent memory layer |
| **Release cadence** | Bi-weekly stable (v2.1.226) | Alpha cadence (v0.148.0-alpha.5) | Nightly (v0.56.0-nightly) | On-demand (no release this cycle) | Active PR volume, no release | Active PR volume, no release | Weekly milestones (v0.9.5) | Bi-weekly stable (v0.21.8) | Sparse releases |

---

## 5. Community Momentum & Maturity

**Most active communities (by issue discussion volume):**
1. **OpenCode** — #27167 (native `/goal`) has 128 👍 and 69 comments, the highest single-issue engagement across all tools. Copy/paste blocker (#13984) has 55 comments. Community is building fast around session lifecycle.
2. **Claude Code** — Billing regression (#79337) has 70 comments and 23 👍; message-queue request (#50246) has 184 👍 as the highest-upvoted open issue across the entire digest.
3. **Pi** — openai-codex reliability (#4945) has 76 comments and 31 👍; auto-compaction issues drive sustained discussion on long-session resilience.
4. **OpenAI Codex** — Multi-line status line (#21653) has 59 👍, the second-highest upvote count. Windows Computer Use cluster shows a mature but frustrated user base.
5. **Gemini CLI** — Agent reliability issues (#22323, #21409) are top of mind; the merged #28738 (agents calling agents) signals active community contribution.

**Rapidly iterating (highest PR throughput):**
- **OpenAI Codex, OpenCode, Pi, Qwen Code, CodeWhale** — all landed 10 PRs in 24 hours, indicating high contributor velocity.
- **Gemini CLI** — 9 PRs in 24 hours, strong release engineering.
- **Claude Code** — only 1 PR; slower cadence but higher-stakes releases.
- **Kimi Code, Copilot CLI, Grok Build** — lowest PR activity; either conservative release cycles or smaller contributor bases.

**Maturity signal:** CodeWhale's v0.9.5 consolidated release (removing legacy packages, aligning update surfaces) suggests a tool maturing past its alpha phase. OpenCode's v2 development with performance improvements (75.5% renderer size reduction) and structured plugin slots indicates a platform moving toward production readiness. Claude Code's single PR but high-impact billing fix suggests a mature product where incremental reliability work matters more than feature volume.

---

## 6. Trend Signals

| Signal | Evidence | Implication for Developers |
|--------|----------|---------------------------|
| **Agent reliability is the #1 unmet need** | Gemini CLI hangs (#21409), subagent false successes (#22323), Codex stale contexts (#37013), CodeWhale turn-stop honesty (#5267) | Tools that solve deterministic agent orchestration will win enterprise trust. Current generation struggles with silent failures. |
| **Cross-session continuity is the next battleground** | Kimi Code memory request (#1283, 25 comments over 6 months), Qwen cross-session messaging (#8724, #8718, #8730), OpenCode multi-instance (#31307) | Long-lived sessions and project context retention are table stakes. Tools without memory face a structural disadvantage. |
| **Windows is a fragmentation risk** | Claude Code GPU crash (#81698), Codex Computer Use cluster (4+ issues), Copilot CLI hook incompatibility (#4399), Pi clipboard overwrites (#7837) | Windows support is under-invested relative to macOS/Linux. Cross-platform testing gaps are a competitive differentiator for rivals. |
| **Billing opacity erodes trust** | Claude Code Fable 5 regression (#79337), Copilot session model reverts (#4397), OpenCode SQLite bloat (#33356) | Cost predictability and model-switch consent are trust issues, not just UX bugs. Tools that surface transparent pricing will retain power users. |
| **Open-source tools are closing the gap** | OpenCode (128 👍 goal feature), Pi (10 PRs/day, provider-agnostic), CodeWhale (Mistral integration, Runtime API) | The open-source CLI layer is maturing rapidly. Feature parity with Claude Code and Codex is within reach for ambitious projects. |
| **TUI quality is a differentiator** | OpenCode copy/paste broken (#13984, 55 comments), Pi fullscreen clipboard (#7837), Codex multi-line status (#21653, 59 👍), Gemini terminal bugs (#25166) | Terminal UX is no longer a nice-to-have. Poor TUI ergonomics drive high-engagement bug reports across all tools. |
| **Provider-agnostic architecture is winning** | Pi supports 10+ providers natively, CodeWhale added Mistral (#5295), OpenCode supports multiple backends, Qwen added DashScope native | Tools locking to a single provider risk obsolescence as model competition intensifies. Abstraction layers are becoming table stakes. |

---

*Report generated from GitHub community data — 2026-08-09 digests. Data reflects community-reported issues and PR activity, not internal development roadmaps.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-09 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

| # | PR | Skill | Status | Key Discussion |
|---|-----|-------|--------|----------------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator: run_eval recall fix** | 🟢 Open | Critical bug where `run_eval.py` reported `recall=0%` on every description regardless of content — the entire description-optimization loop (`run_loop.py`, `improve_description.py`) was optimizing against noise. Multiple Windows-specific sub-fixes also filed (#1099, #1050, #1323, #1261). |
| 2 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | 🟢 Open | Meta-skill that audits AI output before delivery: mechanical file verification first, then a four-dimension reasoning quality gate. Universal — works with any project, stack, or model. Builds on proposal [#1385](https://github.com/anthropics/skills/issues/1385). |
| 3 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | 🟢 Open | Comprehensive testing skill covering the Testing Trophy model, AAA unit tests, React Component Testing with Testing Library, and the full testing stack. Addresses strong demand for test-generation guidance. |
| 4 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** | 🟢 Open | Two meta-skills evaluating Skills across five dimensions (Structure & Documentation 20%, etc.) and security posture. Directly responds to trust-safety concerns raised in issue [#492](https://github.com/anthropics/skills/issues/492). |
| 5 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | 🟢 Open | Prevents orphan line wraps, widow paragraphs, and numbering misalignment in AI-generated documents — a pain point affecting every document output. |
| 6 | [#1479](https://github.com/anthropics/skills/pull/1479) | **plan-file-hygiene** | 🟢 Open | Addresses accumulated planning artifacts with no lifecycle (#1417). Credit attributed to `@halilxibrahim` (naming the problem) and `@xg-gh-25` (lifecycle framing). |
| 7 | [#1302](https://github.com/anthropics/skills/pull/1302) | **color-expert** | 🟢 Open | Self-contained color expertise covering ISCC-NBS, Munsell, OKLCH/OKLAB/CAM16 color spaces, and naming systems (XKCD, RAL, CSS named). Niche but well-scoped. |
| 8 | [#525](https://github.com/anthropics/skills/pull/525) | **pyxel** | 🟢 Open | MCP-server-backed skill for retro/pixel-art game development with the Pyxel engine. Covers the write → run_and_capture → inspect → iterate loop. |

---

## 2. Community Demand Trends

Distilled from the most-commented issues:

| Theme | Signal | Key Issues |
|-------|--------|------------|
| **Security & trust boundaries** | Highest-comment issue in the repo; namespace impersonation of official skills is a live concern | [#492](https://github.com/anthropics/skills/issues/492) (43 comments), [#1175](https://github.com/anthropics/skills/issues/1175) (SharePoint permissions in SKILL.md) |
| **Org-wide collaboration** | Strong desire for shared skill libraries within organizations, not just personal installs | [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) |
| **Eval & quality tooling** | The `run_eval.py` recall bug is a community-wide blocker; multiple independent reports confirm it | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍), [#1169](https://github.com/anthropics/skills/issues/1169) |
| **Context window hygiene** | Skills that eagerly inject massive content (#1487: ~156k tokens in one call) are flagged as harmful | [#1487](https://github.com/anthropics/skills/issues/1487), [#1329](https://github.com/anthropics/skills/issues/1329) (compact-memory proposal) |
| **Testing & code quality** | Clear demand for a comprehensive testing-patterns skill and better skill-creator best practices | [#723](https://github.com/anthropics/skills/pull/723), [#202](https://github.com/anthropics/skills/issues/202) (closed) |
| **Cross-platform & protocol** | Windows compatibility gaps in skill-creator; long-standing ask to expose Skills as MCPs | [#1050](https://github.com/anthropics/skills/pull/1050), [#16](https://github.com/anthropics/skills/issues/16), [#29](https://github.com/anthropics/skills/issues/29) (Bedrock) |
| **Duplicate content** | Installing multiple plugins from `anthropic-agent-skills` produces identical skills, wasting context | [#189](https://github.com/anthropics/skills/issues/189) (6 comments, 9 👍) |

---

## 3. High-Potential Pending Skills

These open PRs address high-impact problems and have the strongest chance of landing:

- **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — Fixes the `recall=0%` bug that has blocked the entire description-optimization workflow for months. Multiple corroborating issues (#556, #1169) make this a priority fix.
- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit skill; fills a clear gap in pre-delivery quality assurance. Directly addresses community concerns about output reliability.
- **[PR #723](https://github.com/anthropics/skills/pull/723)** — Testing-patterns skill; testing is one of the most common developer workflows and no comprehensive skill currently exists.
- **[PR #1479](https://github.com/anthropics/skills/pull/1479)** — Plan-file-hygiene; solves a real lifecycle problem (stale planning artifacts) with well-attributed community framing.
- **[PR #514](https://github.com/anthropics/skills/pull/514)** — Document-typography; niche but universally relevant to any document-generation use case.
- **[PR #83](https://github.com/anthropics/skills/pull/83)** — Meta-skills for quality and security analysis; directly responsive to the trust/safety concerns dominating issue #492.
- **[PR #538](https://github.com/anthropics/skills/pull/538)** and **[PR #541](https://github.com/anthropics/skills/pull/541)** — Case-sensitivity and DOCX tracked-change fixes; small, targeted, low-risk patches with clear root-cause analysis.

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for reliable self-improving tooling and trust guarantees** — the `skill-creator` eval pipeline is broken in a way that makes skill optimization impossible, while namespace impersonation and context-window bloat are eroding user trust in the skill ecosystem itself.

---



# Claude Code Community Digest — 2026-08-09

## 1. Today's Highlights

Claude Code v2.1.226 landed with bug fixes and reliability improvements. The community is most agitated by a breaking billing regression on Max plans: Fable 5, now standard as of July 20, silently downgrades sessions to Opus 4.8 and demands usage credits (#79337, 70 comments, 23 👍). Meanwhile, the long-standing request for a message-queue mode to avoid interrupting active tasks remains the most upvoted enhancement (#50246, 184 👍).

## 2. Releases

**v2.1.226** — Bug fixes and reliability improvements. No feature changes noted.

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| #79337 | Fable 5 prompts 'usage credits required' on Max plan | 70 | 23 | **Critical billing regression.** Max-plan users hit on the first day Fable 5 became standard; sessions silently downgrade to Opus 4.8. High engagement signals widespread impact. |
| #50246 | Message queue mode — queue messages instead of interrupting active tasks | 50 | 184 | **Most upvoted open issue.** Addresses a fundamental UX gap: developers must choose between interrupting work and forgetting follow-ups. |
| #29006 | Enable Remote Control for Claude Code sessions in Claude Desktop App | 36 | 119 | **High-visibility feature request.** Desktop users want to control CLI sessions from the Claude Desktop app, bridging two product surfaces. |
| #19054 | Claude Code For VS Code does not use MCP servers at all | 24 | 26 | **MCP integration gap in VS Code** continues to frustrate users who rely on MCP tooling in the CLI but see nothing in the extension. |
| #81698 | Windows Desktop app: GPU process crash kills entire app and all sessions | 15 | 0 | **Data-loss risk on Windows.** A GPU crash (RTX 5080) terminates all running Claude Code sessions with no recovery path. |
| #84352 | CVP-approved organization still receives cyber safeguard blocks | 13 | 0 | **Security/verification policy inconsistency.** Organizations with prior CVP approval are being re-blocked, causing confusion and workflow disruption. |
| #83436 | Cyber-safeguard false positives on scientific computing session | 11 | 0 | **Overzealous safety filters blocking legitimate research.** IR spectrometer calibration sessions flagged despite no policy violation. |
| #60093 | Model switched to Opus without consent — $1,050 overcharge | 10 | 0 | **Closed but illustrative.** A past case of undisclosed model switches causing massive cost spikes; resurfaced in discussion as a recurring concern. |
| #67303 | Dispatch permanently shows "Can't reach your desktop" | 8 | 0 | **Remote control reliability.** Desktop-pairing failures leave Dispatch sessions stranded, blocking mobile-to-desktop workflows. |
| #81693 | Claude Opus 5 context window size reported as 200k instead of 1M | 4 | 0 | **Instrumentation bug.** Statusline gauge saturates and `/compact` appears non-functional, misleading users about remaining context. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| #77492 | fix(hookify): match Write and prompt rules | Open | Fixes a root-cause bug where simple rules were inferred as absent. Maps prompt rules to `UserPromptSubmit` payload and adds regression coverage for Write, Edit, and prompt rules. |

*(Only 1 PR updated in the last 24h; no additional PRs to report.)*

## 5. Feature Request Trends

- **Non-blocking interaction models** — The message-queue feature (#50246) and remote-control integration (#29006) both point to a desire for asynchronous, parallel workflows without interrupting active sessions.
- **Cross-product session continuity** — Users want Claude Code sessions to be controllable from Claude Desktop and mobile (Dispatch), creating a seamless multi-client experience.
- **Transparent model selection & cost control** — Repeated requests for explicit model-switch notifications, consent-based upgrades, and accurate context-window reporting reflect frustration with opaque billing and model behavior.
- **MCP parity across surfaces** — The VS Code extension not using MCP servers (#19054) highlights a gap users expect to be closed as MCP becomes standard.

## 6. Developer Pain Points

1. **Billing opacity and model-switching without consent** — The Fable 5 regression (#79337) and prior Opus-switch overcharge case (#60093) share a pattern: users are charged at higher tiers without UI disclosure. Cost predictability is a top concern.
2. **Session interruptions with no queueing mechanism** — Developers working on long-running tasks have no way to defer follow-up prompts, forcing a choice between context loss and work derailment (#50246).
3. **Platform-specific crashes and instability** — Windows GPU crashes (#81698, #80912), Linux mouse-reporting bugs (#68602), and macOS image-click failures (#70619) indicate fragmented quality across platforms.
4. **Desktop-app bundled CLI connectivity issues** — ECONNRESET errors in the desktop-bundled CLI (#84818) while the system npm CLI works fine suggest environment-specific networking problems.
5. **False-positive safety guards** — Legitimate scientific and enterprise work (CVP-approved orgs, IR calibration) is being blocked by cyber-safeguard filters (#84352, #83436), creating friction for professional users.
6. **Dispatch pairing unreliability** — Persistent "Can't reach your desktop" states (#67303) and circular dependency issues with the mobile client (#84035) undermine remote-control workflows.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-09

## 1. Today's Highlights

A Windows-specific Computer Use regression dominates the discussion, with at least four issues tracing back to stale `node_repl` exec contexts and `@oai/sky` transport failures. On the CLI side, a new alpha release `0.148.0-alpha.5` ships alongside hooks-engine generalization and workload-identity token support landing in parallel. Community sentiment is split between excitement for async hook support and frustration over persistent Windows desktop instability.

---

## 2. Releases

**rust-v0.148.0-alpha.5** ([Issue link](https://github.com/openai/codex)) — Latest alpha for the Rust-based Codex CLI. No detailed changelog provided in source data; likely includes incremental fixes leading toward the next stable release.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#21653](https://github.com/openai/codex/issues/21653) | Support multi-line status line | Long status lines (configured items + model name) are truncated with no linebreak; affects TUI usability for power users. | 🔥 59 👍, 13 comments — the most-upvoted open issue in the dataset. |
| [#27284](https://github.com/openai/codex/issues/27284) | SSH remote shows "No chats" while threads exist in DB | Remote project sessions are invisible in the app despite being present in the state DB; breaks remote-workflow continuity. | 12 comments, 5 👍 — cross-platform (macOS → Linux SSH) impact. |
| [#37013](https://github.com/openai/codex/issues/37013) | Windows Computer Use reuses stale `node_repl` context | After first JS call, subsequent `node_repl/js` calls fail because the same `@oai/sky` transport is reused without re-initialization. | 11 comments, 3 👍 — blocks all multi-step Computer Use workflows on Windows. |
| [#37458](https://github.com/openai/codex/issues/37458) | Codex extension fails to load: "couldn't load its resources" | Extension cannot start in VS Code on Windows; blocks all IDE-integrated usage. | 11 comments, 0 👍 — high-severity but low engagement (likely few affected users have reported yet). |
| [#37180](https://github.com/openai/codex/issues/37180) | Windows Computer Use approval prompt never appears | `launch_app` fails with `node_repl exec context not found`; users cannot approve or deny computer-use actions. | 8 comments, 2 👍 — directly blocks safe automation on Windows. |
| [#37383](https://github.com/openai/codex/issues/37383) | Windows Computer Use app/window discovery fails with `0x80070003` | Native error `0x80070003` (path not found) during enumeration; Windows 11 25h2 specific. | 8 comments, 4 👍 — affects Pro-tier subscribers. |
| [#37649](https://github.com/openai/codex/issues/37649) | Frequent reconnect loops & stream-disconnect errors | CLI `0.147.0` on macOS drops streams even for simple prompts; impacts all model variants (`gpt-5.6-sol`, `gpt-5.6-luna`). | 6 comments, 0 👍 — new issue (created today), likely to grow. |
| [#34076](https://github.com/openai/codex/issues/34076) | Desktop loses local project registrations & hides active threads | App-side project list diverges from CLI/core DB; sessions appear missing despite healthy backend. | 6 comments — affects cross-client consistency. |
| [#33074](https://github.com/openai/codex/issues/33074) | Windows mouse stutter during startup & task switching | Severe UX degradation on Windows 11; no CPU/disk saturation explains the stutter. | 6 comments, 9 👍 — widely felt performance issue. |
| [#37563](https://github.com/openai/codex/issues/37563) | Desktop rehydrates closed terminal subagents as "Working" | After restart, completed/aborted subagents incorrectly appear active; misleads users about session state. | 4 comments, 2 👍 — state-reconciliation bug with trust implications. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#37645](https://github.com/openai/codex/pull/37645) | Improve plugin install failure analytics | ✅ Closed | Adds HTTP status subtypes for remote catalog, mutation, and bundle-download failures; enables better diagnostics for plugin issues. |
| [#37644](https://github.com/openai/codex/pull/37644) | Generalize hook handler execution | ✅ Closed | Routes all configured handlers through the hooks engine by kind; rejects MCP tool inputs containing `null` values that can't be hashable in TOML. |
| [#37641](https://github.com/openai/codex/pull/37641) | Use step context for command approval prefix rules | ✅ Closed | `allow_prefix_rules` now reads from the turn attached to the active step context, ensuring exec-policy selection uses current turn state. |
| [#37622](https://github.com/openai/codex/pull/37622) | Include buffered turns when editing prompts | ✅ Closed | Prompt editing now reconstructs buffered turns from notifications before lookup, fixing cases where live turns hadn't been flushed. |
| [#37618](https://github.com/openai/codex/pull/37618) | Use step environments for Guardian approval reviews | ✅ Closed | Guardian reviews now use the step's environment (not stale turn snapshot), fixing working-directory and permission mismatches. |
| [#37610](https://github.com/openai/codex/pull/37610) | Add workload identity token exchange support | ✅ Closed | New `codex-workload-identity` crate exchanges file-backed JWT assertions + federation rule IDs for short-lived ChatGPT credentials, with token caching and coalescing. |
| [#37607](https://github.com/openai/codex/pull/37607) | Prevent launch context from reaching child processes | ✅ Closed | `OPENAI_FEDERATION_RULE_ID` and `OPENAI_IDENTITY_TOKEN_FILE` are now non-inheritable (case-insensitive), preventing model-reachable children from leaking credentials. |
| [#37533](https://github.com/openai/codex/pull/37533) | Support asynchronous command hooks | ✅ Closed | Async command hooks now run in the background with per-session concurrency limits; previously they were silently skipped outside `SessionEnd`. |
| [#37530](https://github.com/openai/codex/pull/37530) | Implement gRPC code-mode host service | ✅ Closed | Exports `GrpcCodeModeHost` as a transport-independent code-mode gRPC implementation; supports leased sessions, execution/wait lifecycle, filtered nested tool-call subscriptions, and notifications. |
| [#37527](https://github.com/openai/codex/pull/37527) | Terminate timed-out hook process trees | ✅ Closed | Hook commands now run in process groups (Unix) / job objects (Windows); the full descendant tree is terminated on timeout, preventing orphaned processes. |

---

## 5. Feature Request Trends

1. **Multi-line / resizable TUI status lines** — Issue #21653 (59 👍) signals strong demand for TUI layout flexibility as status configurations grow more complex.
2. **Async hook support** — PR #37533 directly addresses a long-standing gap; the community has explicitly requested non-blocking hook execution.
3. **Codex cloud workspaces from ChatGPT Sites** — Issue #37633 proposes ephemeral cloud workspaces derived from Sites repositories, bridging two product surfaces.
4. **Better prompt-editing reliability** — PR #37622 and Issue #35292 (Esc-Esc model change) both reflect demand for deterministic in-session editing and state preservation.
5. **Remote/SSH session parity** — Issues #27284 and #34076 both highlight gaps between CLI-state reality and app-side visibility for remote projects.

---

## 6. Developer Pain Points

- **Windows Computer Use instability** — At least four distinct issues (#37013, #37180, #37383, #37281, #37595, #37509) all trace to the same root: `node_repl` exec context lifecycle management and `@oai/sky` transport failures on Windows. This is the single largest cluster of developer frustration this cycle.
- **Extension load failures on Windows** — Issues #37458 and #35182 show the VS Code extension repeatedly fails to start with resource-loading or error-dialog issues, blocking IDE integration.
- **Session-state desynchronization** — Issues #27284, #34076, and #37563 all describe scenarios where the app's view of sessions/subagents diverges from the CLI/core database, eroding user trust.
- **Stream reconnect loops** — Issue #37649 reports frequent disconnections even for trivial prompts on CLI/macOS, suggesting a regression in streaming reliability.
- **Windows mouse stutter** — Issue #33074 (9 👍) describes severe input latency on Windows 11 that persists across clean reinstalls, indicating a deep OS-level interaction problem.
- **TUI paste behavior asymmetry** — Issue #17103 notes that `Ctrl+V` is image-only when it reaches Codex as a key event, with no symmetric text-paste path — a consistent usability gap.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-09

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly.20260809 was published today. The community is focused heavily on agent reliability — a P1 bug where subagents report `GOAL` success after hitting `MAX_TURNS` (12 comments) and a separate P1 generalist-agent hang (8 👍) dominate the discussion. Several PRs landed addressing crash-on-startup, OAuth timeout leaks, and the long-requested "agents calling agents" capability.

## 2. Releases

**v0.56.0-nightly.20260809.gcf22ac7e8** — automated nightly bump. No user-facing changelog beyond the nightly cadence.

- [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.56.0-nightly.20260808.gcf22ac7e8...v0.56.0-nightly.20260809.gcf22ac7e8)

## 3. Hot Issues

| # | Issue | Why it matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports GOAL success after MAX_TURNS | Misleading `status: "success"` + `Termination Reason: GOAL` hides that the subagent hit its turn limit — users can't tell whether work actually completed. | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | Simple tasks like folder creation cause the generalist subagent to hang for hours; disabling subagents is the only known workaround. | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing via bash affinity | Proposes leveraging Gemini 3's native bash chaining while adding sandboxing — a significant architecture shift for secure codebase exploration. | 8 comments · 1 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | Tracks 76 behavioral eval tests across 6 supported models; critical for understanding agent quality at scale. | 7 comments · 0 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | Could reduce tool calls and token waste by reading precise method bounds — directly impacts agent efficiency. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini underuses skills and sub-agents | Anecdotal but widely felt: the model won't independently invoke custom skills or sub-agents even when tasks match their descriptions. | 6 comments · 0 👍 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Sessions the extractor skips remain unprocessed and resurface endlessly, wasting memory and compute. | 5 comments · 0 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Secrets can leak before the extraction prompt redacts them — a security concern as Auto Memory usage grows. | 4 comments · 0 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell commands stuck at "Waiting input" after completion | Simple non-interactive commands hang the CLI after finishing, requiring manual cancellation. | 4 comments · 3 👍 |
| [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) | Subagents run without permission since v0.33.0 | Regression: users who explicitly disabled agents mode still see subagents activating, breaking expected consent flows. | 3 comments · 0 👍 |

## 4. Key PR Progress

| # | PR | Description |
|---|-----|------------|
| [#28738](https://github.com/google-gemini/gemini-cli/pull/28738) | **Allow agents to call agents** | Subagents can now delegate to other subagents or recurse via `tools:` frontmatter. Fixes #22092. |
| [#28736](https://github.com/google-gemini/gemini-cli/pull/28736) | **Fix OAuth callback timeout leak** | Ensures the OAuth timeout is cleared and the callback server closes gracefully when auth completes. Fixes #28652. |
| [#28734](https://github.com/google-gemini/gemini-cli/pull/28734) | **Fix crash on startup with macOS Seatbelt** | `resolveToRealPath` now handles `EACCES` alongside existing error codes, preventing sandbox-enabled crashes in Git repos. Fixes startup issues on macOS. |
| [#28735](https://github.com/google-gemini/gemini-cli/pull/28735) | **Fix formatTruncatedToolOutput for non-positive maxChars** | Added a guard to prevent output inflation when `maxChars ≤ 0`. Fixes #28620. |
| [#28679](https://github.com/google-gemini/gemini-cli/pull/28679) | **Improve Vertex AI 401 error messages** | Better DX when users provide a standard Gemini API key with `vertex-ai` auth type — now fails fast with a clear message instead of a confusing 401. |
| [#28608](https://github.com/google-gemini/gemini-cli/pull/28608) | **Fallback to stable models on preview 404** | When a Gemini API key lacks preview model access, the CLI now falls back to stable models instead of surfacing a 404 NOT_FOUND error. Fixes #28600. |
| [#28619](https://github.com/google-gemini/gemini-cli/pull/28619) | **Update .gitignore for .env and .ai files** | Adds unit tests and ensures sensitive env/AI config files are ignored by default. |
| [#28526](https://github.com/google-gemini/gemini-cli/pull/28526) | **Fix VSCode extension disposable leak** | Fixes #27790 — `gemini.diff.accept` and `onDidChangeWorkspaceFolders` disposables were being dropped due to a stray parenthesis in `activate()`. |
| [#28739](https://github.com/google-gemini/gemini-cli/pull/28739) | **chore: bump to v0.56.0-nightly.20260809** | Automated nightly version bump. |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | **Browser agent session takeover** (issue → PR pending) | Requests automatic lock recovery for `browser_agent` when a persistent profile is already in use, replacing the current fail-fast strategy. |

## 5. Feature Request Trends

1. **Agent-to-agent orchestration** — Beyond #28738 (now merged), issues #21968, #22598, and #20195 all point to demand for richer subagent delegation, shared trajectory visibility, and local subagent support.
2. **AST/codebase-aware tooling** — Issues #22745 and #22746 push for parser-aware file reads and codebase mapping to reduce turn count and token waste.
3. **Security hardening** — Auto Memory redaction (#26525), invasive sandboxing (#19873), and anti-destructive-behavior (#22672) show a clear trend toward safer agent execution.
4. **Browser agent resilience** — Wayland support (#21983), session takeover (#22232), and settings override fixes (#22267) indicate the browser agent is maturing but still fragile across environments.
5. **CLI UX polish** — Terminal resize performance (#21924), external editor corruption (#24935), and `get-shit-done` crash fixes (#22186) reflect ongoing investment in editor-grade terminal experience.

## 6. Developer Pain Points

- **Agent reliability**: hangs (#21409), silent failures (#22323), and unauthorized subagent invocation (#22093) are the top reported frustrations. Users expect explicit control over when subagents activate.
- **Shell interaction bugs**: commands getting stuck at "Waiting input" (#25166) and interactive prompts blocking progress (#22465) cause repeated workflow interruption.
- **Auto Memory quality**: low-signal retry loops (#26522), unredacted secrets (#26525), and invalid patch handling (#26523) erode trust in the memory system.
- **Tool/skill discovery**: the model consistently underuses custom skills and subagents (#21968), suggesting a gap between what users configure and what the model independently invokes.
- **Platform-specific issues**: Wayland browser failures (#21983), macOS Seatbelt crashes (#28734), and symlinked agent files not recognized (#20079) indicate uneven cross-platform testing.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-09

## 1. Today's Highlights

The Copilot CLI community addressed several closing bugs around session persistence and model selection, including a fix for autopilot state loss on resume and a regression in the skill tool on Windows. A cluster of new issues flagged urgent cross-cutting concerns: auto-mode configurability, browser login URL wrapping, and a "No model available" error on Copilot Free in Codespaces.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **Sessions lose auto-mode state on resume** [#4329](https://github.com/github/copilot-cli/issues/4329) — Autopilot appears enabled in the statusline but silently fails on action approval. Users are losing trust in session persistence after restarts. *(Closed)*

2. **Typing latency degrades over long sessions** [#4299](https://github.com/github/copilot-cli/issues/4299) — Long-running sessions, especially with background agents, become unusable due to increasing keyboard latency. Upvoted by 1; closed. *(Closed)*

3. **`/agent` popup misidentifies AGENTS.md as a custom agent** [#4410](https://github.com/github/copilot-cli/issues/4410) — The CLI incorrectly treats `.github/agents/AGENTS.md` (repository guidance) as a custom agent definition, producing a malformed frontmatter error. *(Open)*

4. **ACP `contextTier` not exposed in session config** [#4275](https://github.com/github/copilot-cli/issues/4275) — Interactive CLI allows mid-session context-tier changes via `/model`, but the ACP server lacks this parity, forcing tier selection only at spawn time. *(Open)*

5. **Claude `cache_control` breakpoints missing** [#4256](https://github.com/github/copilot-cli/issues/4256) — Requests to Anthropic do not set `cache_control` breakpoints, so expensive repeated context (system prompt, tool definitions) is fully reprocessed each turn. 3 👍. *(Closed)*

6. **`allowed_directories` in permissions.config never loaded** [#4398](https://github.com/github/copilot-cli/issues/4398) — Directory allowances defined in `permissions.config` are silently ignored; `/list-dirs` never shows them. Users cannot configure granular filesystem access. *(Open)*

7. **Session resume reverts to default model** [#4397](https://github.com/github/copilot-cli/issues/4397) — Resuming a session that was started with a specific model (e.g., `gpt-5.6-terror`) automatically switches back to the default model. *(Open)*

8. **Windows: cross-tool Claude hooks with shell operators break** [#4399](https://github.com/github/copilot-cli/issues/4399) — `PreToolUse` hooks containing POSIX shell operators (`||`, `&&`) in `settings.local.json` fail to execute on Windows PowerShell, breaking cross-tool compatibility. *(Open)*

9. **Browser login URL wrapping and fallback broken** [#4400](https://github.com/github/copilot-cli/issues/4400) — The "Sign in with your browser" flow displays a malformed or wrapped URL, making login impossible in constrained terminal environments. *(Open)*

10. **Copilot Free in Codespaces: "No model available"** [#4405](https://github.com/github/copilot-cli/issues/4405) — After an update, Copilot Free users in GitHub Codespaces see every prompt fail with `No model available`, even though documentation states models should be enabled. *(Open)*

## 4. Key PR Progress

No new pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

- **Auto-mode configurability**: Two nearly identical requests [#4411](https://github.com/github/copilot-cli/issues/4411) / [#4412](https://github.com/github/copilot-cli/issues/4412) ask for minimum/maximum model strength bounds and bias controls within auto-mode, signaling community desire for finer-grained autonomy tuning.
- **Cross-platform UI localization**: Issue [#4407](https://github.com/github/copilot-cli/issues/4407) requests Chinese (zh-CN) UI support, part of a broader demand for non-English interface localization.
- **Session management UX**: Users want quick-delete for sessions [#4395](https://github.com/github/copilot-cli/issues/4395), the ability to remap Ctrl+C exit behavior [#4394](https://github.com/github/copilot-cli/issues/4394), and parity between interactive and ACP context-tier control [#4275](https://github.com/github/copilot-cli/issues/4275).
- **Cost optimization via caching**: The `cache_control` feature request [#4256](https://github.com/github/copilot-cli/issues/4256) reflects growing interest in reducing per-turn API costs through Anthropic prompt caching.

## 6. Developer Pain Points

- **Session state loss**: Recurring bugs where resume behavior drops configuration (model selection in #4397, autopilot state in #4329) erodes developer trust in session continuity.
- **Windows-specific regressions**: Multiple issues surface on Windows — skill tool regression (#4401), Claude hook operator incompatibility (#4399), and the silent exit-1 bug on specific log levels (#4285) — pointing to a pattern of platform-specific gaps.
- **Silent authentication failures**: The `cli_remote_control_enabled: false` entitlement produces opaque behavior across desktop and mobile (#4409), and browser login URL wrapping (#4400) blocks straightforward sign-in flows.
- **npm shims are unstable**: Issue #4402 reveals that the global `npm bin/copilot` shim is a loader that can serve different versions within seconds, with an undocumented `--prefer-version` workaround.
- **Permissions config silently ignored**: `allowed_directories` in `permissions.config` (#4398) being unconditionally ignored is a high-impact issue for users relying on workspace-level access controls.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-09

## 1. Today's Highlights
The community is actively requesting a **persistent Memory System** to retain context and preferences across sessions, signaling a demand for deeper personalization and workflow continuity. Meanwhile, a critical bug report highlights a **runaway generation incident** where a single LLM step produced over 88k tokens of incoherent gibberish, underscoring ongoing reliability concerns in interactive use.

## 2. Releases
*No new releases in the past 24 hours.*

## 3. Hot Issues
1. **[Enhancement] Memory System - Persistent context across sessions**  
   **URL:** https://github.com/MoonshotAI/kimi-cli/issues/1283  
   **Why it matters:** This feature request proposes a comprehensive memory layer that would allow Kimi Code CLI to remember project patterns, useful context, and user preferences across sessions. It reflects a strong community desire for the tool to adapt to individual workflows and maintain continuity, similar to advanced AI assistants.  
   **Community reaction:** Opened in February but actively updated as recently as August, with 25 comments indicating sustained interest and discussion around implementation scope (automatic vs. manual memory).

2. **[Bug] Runaway garbled generation — 88k tokens of gibberish in one LLM step**  
   **URL:** https://github.com/MoonshotAI/kimi-cli/issues/2597  
   **Why it matters:** This bug describes a severe reliability failure where a single LLM step ran for over 53 minutes and emitted 88,114 tokens of incoherent, repetitive output. Such events can disrupt workflows, waste resources, and erode trust in the CLI's interactive stability.  
   **Community reaction:** Reported on August 8 with no comments yet, but the severity of the failure (extreme token count and duration) suggests it will attract attention from users experiencing similar generative instability.

*Note: Only two issues were updated in the last 24 hours. No further issues were available for ranking.*

## 4. Key PR Progress
*No pull requests were updated in the past 24 hours.*

## 5. Feature Request Trends
The primary feature direction emerging from recent issues is **persistent context and personalization**. The Memory System request (#1283) is the most detailed and actively discussed enhancement, highlighting a community need for the CLI to learn and retain project-specific knowledge, user preferences, and session continuity. This trend aligns with broader AI tool evolution toward stateful, adaptive development assistants.

## 6. Developer Pain Points
- **Context continuity:** Developers are frustrated by the lack of persistent memory across sessions, forcing them to re‑establish project context repeatedly.
- **Generation reliability:** The runaway‑gibberish bug (#2597) points to instability in LLM output during interactive sessions, where uncontrolled token generation can halt productivity and require manual intervention.
- **Resource inefficiency:** Long‑running, high‑token‑count failures (e.g., 53 minutes, 88k tokens) suggest inadequate safeguards against anomalous model behavior, leading to wasted compute and time.

---

*Digest generated from GitHub data for MoonshotAI/kimi-cli. All links reference the original repository issues.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-09

## 1. Today's Highlights

The OpenCode community is buzzing around two front-running themes: **session lifecycle management** (native goals, multi-instance isolation, and branch-aware tabs) and a cluster of **OpenCode Go / deepseek-v4-flash relay bugs** causing HTTP 400 errors on the Console Go endpoint. Meanwhile, v2 development momentum is strong, with multiple contributor PRs landing Mermaid renderer fixes, plugin slot restructuring, and performance improvements.

## 2. Releases

No releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#27167](https://github.com/anomalyco/opencode/issues/27167) | Add native session goals with `/goal` | Introduces persistent session-level objectives, a foundational feature for agent workflows. | 128 👍 · 69 comments — the most-discussed open issue. |
| [#13984](https://github.com/anomalyco/opencode/issues/13984) | Cannot copy and paste in opencode CLI | Clipboard reporting success but `Ctrl+V` failing blocks basic text interaction in the TUI. | 27 👍 · 55 comments — a persistent usability blocker. |
| [#14965](https://github.com/anomalyco/opencode/issues/14965) | Slow startup (≥1.2.1) | Regression in startup time, terminal-specific (Ghostty vs. Terminal/Alacritty/Kitty). | 13 👍 · 19 comments — performance concern across users. |
| [#33356](https://github.com/anomalyco/opencode/issues/33356) | [2.0] Unbounded `event` table growth — DB reaches 13 GB+ | Event-sourcing table has no retention or compaction, filling volumes on long-running instances. Critical for v2 stability. | 4 👍 · 15 comments — high-severity infra issue. |
| [#30611](https://github.com/anomalyco/opencode/issues/30611) | Sessions fail on transient network errors instead of retrying | Only `ECONNRESET` is retried; other transient failures kill the session outright, reducing reliability. | 1 👍 · 6 comments — affects production resilience. |
| [#32548](https://github.com/anomalyco/opencode/issues/32548) | Step-cap message causes 400 on Claude models with thinking | Appending "MAXIMUM STEPS REACHED" as an assistant-role message triggers Anthropic's response-preflight rejection. | 0 👍 · 5 comments — model-compatibility bug. |
| [#41300](https://github.com/anomalyco/opencode/issues/41300) | Leading space in model name for `deepseek-v4-flash` | Gateway prepends a space to the model string, causing upstream 400 errors. | 1 👍 · 4 comments — active bug, multiple related issues. |
| [#41306](https://github.com/anomalyco/opencode/issues/41306) | `deepseek-v4-flash` still broken on Console Go after #41211 | Regression persisted despite prior fix; verified as recently as 2026-08-09. | 0 👍 · 3 comments — escalating frustration. |
| [#31307](https://github.com/anomalyco/opencode/issues/31307) | Multiple instances share the same SQLite session | Running two terminal tabs in the same project causes session bleeding, a major correctness issue. | 3 👍 · 4 comments — data-integrity concern. |
| [#31554](https://github.com/anomalyco/opencode/issues/31554) | MCP servers spawn 2–4 duplicate processes per server | Duplicate processes accumulate on restart, causing `TasksMax` exhaustion and `EAGAIN` errors on Linux. | 0 👍 · 2 comments — scaling/regression bug. |

## 4. Key PR Progress

| # | PR | Description |
|---|----|-------------|
| [#41350](https://github.com/anomalyco/opencode/pull/41350) | Animated BusyWave loading indicator | Replaces shimmering "Thinking" label with a persistent busy-wave animation inspired by TUI patterns. |
| [#40997](https://github.com/anomalyco/opencode/pull/40997) | Replace integration prompts with forms | Standardizes OAuth/key flows using shared `Form.Fields`; validates and persists provider config in Core. Affects GitHub Copilot, Azure, and Cloudflare integrations. |
| [#40427](https://github.com/anomalyco/opencode/pull/40427) | Experimental performance improvements | Initial renderer entry down **75.5%** (7.45 MB → 1.82 MB) measured against an immutable partial DB snapshot. |
| [#41347](https://github.com/anomalyco/opencode/pull/41347) | Sync Mermaid renderer fixes | Aligns v2 terminal Mermaid renderer with OpenTUI fixes: corrects branching/feedback state diagrams, supports connectors, decodes HTML entities, and imports spatial routing. |
| [#40861](https://github.com/anomalyco/opencode/pull/40861) | Stop storing full patch text in session summaries | Fixes unbounded DB growth (#32005) by stopping `Snapshot.diffFull()` from storing complete patch text in summaries. Directly addresses #33356. |
| [#41344](https://github.com/anomalyco/opencode/pull/41344) | Undo latest pending prompt | `/undo` now removes the newest pending user prompt before reverting session history, including queued and steering follow-ups. Fixes #39736. |
| [#41343](https://github.com/anomalyco/opencode/pull/41343) | Write prettier-stable generated manifests | Formats `.httpapi-codegen.json` through prettier at write time, eliminating the last red job on v2 CI. |
| [#41342](https://github.com/anomalyco/opencode/pull/41342) | Show session branches in vertical tabs | Non-default VCS branches now appear on session tabs as `project:branch`, giving users at-a-glance context. |
| [#41189](https://github.com/anomalyco/opencode/pull/41189) | Region structure for plugin slot placement | Plugin slots are restructured from position-encoded names to named regions with trees, enabling precise plugin placement. |
| [#41202](https://github.com/anomalyco/opencode/pull/41202) | Authorize file mutations before locking | Introduces a capability-permission-then-lock model for `write`, `edit`, and `patch`: resolves paths and requests permission first, then acquires process-global locks. |

## 5. Feature Request Trends

1. **Session lifecycle & goals** — The top-voted issue (#27167) calls for native `/goal` support, reflecting strong demand for persistent, session-level task management beyond ad-hoc prompts.
2. **MCP server management from the TUI** — Issue #38993 requests in-TUI add/remove of MCP servers with config persistence, complementing the HTTP runtime controls from #37712.
3. **Multi-instance session isolation** — Issue #31307 and the DB-growth issue #33356 both point to a trend: users are running OpenCode in long-lived, multi-session, and multi-instance workflows that the current SQLite-backed design doesn't fully support.
4. **Plugin hook depth** — Issues #41304 and #41325 reveal growing plugin-author interest in fine-grained lifecycle hooks (`tool.execute.after`, `permission.ask`) and the ability to mutate subagent outputs mid-task.
5. **Cross-platform terminal fidelity** — Repeated reports about terminal-specific behavior (Ghostty startup, Kitty link-clicking, PowerShell MSIX detection) indicate a trend toward demanding parity across terminal environments.

## 6. Developer Pain Points

- **OpenCode Go relay bugs (deepseek-v4-flash)** — A cluster of five issues (#41300, #41306, #41314, #41322, #40420) all trace back to the Console Go gateway mishandling model names (leading spaces, missing `finish_reason`). This is the most active pain point this cycle.
- **SQLite event-table bloat** — Issue #33356 and PR #40861 confirm that long-running instances can fill disks (13 GB+). No retention or compaction exists today; session summary diff storage is a known contributor.
- **Transient-network fragility** — Issue #30611 highlights that only `ECONNRESET` triggers retries; other transient failures (timeouts, dropped connections) hard-fail sessions, degrading reliability in unstable network conditions.
- **Multi-instance session collision** — Issue #31307 shows that concurrent OpenCode instances in the same project silently share state, producing confusing cross-talk between terminals.
- **Plugin/slash-command regressions in Desktop** — Issues #41339 and #34776 report that plugin slash commands pass through as raw text in Desktop v1.18.15, and that the `/{commands}` endpoint breaks when the ECC plugin is installed — a regression that doesn't affect CLI.
- **MCP process proliferation** — Issue #31554 documents 2–4× process duplication on Linux, causing `TasksMax` exhaustion and `EAGAIN` errors, especially damaging for users running many MCP servers.
- **Terminal-specific UX gaps** — Copy/paste failure (#13984), non-clickable wrapped links in Kitty (#35649), slow startup in Ghostty (#14965), and PowerShell MSIX detection on Windows (#41321) all point to a pattern: OpenCode's TUI behaves inconsistently across terminal emulators and OS shells.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-09

## 1. Today's Highlights

The community is focused on **reliability hardening** for the `openai-codex` provider (Issue #4945, 76 comments) and **auto-compaction timing** (Issues #6879, #7821), both critical for long-running agent sessions. On the feature side, support for **LLM Gateway**, **Meta Model API**, and **Cloudflare Workers AI Gateway** is advancing, while **DeepSeek native provider** improvements continue with proper `max_tokens` handling and reasoning-effort mapping.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| #4945 | [openai-codex Connection Reliability Issues](https://github.com/earendil-works/pi/issues/4945) | TUI gets stuck on "Working…" with no streamed text or error; requires manual Escape. ~30% of long streams experience transport failures. | 76 comments · 31 👍 — most-discussed open issue |
| #6879 | [auto-compaction never triggers after context grows past 100%](https://github.com/earendil-works/pi/issues/6879) | Context can exceed the window threshold without compaction kicking in, only stopping when the API rejects at 373k tokens. | 15 comments · 15 👍 |
| #7821 | [Auto-compaction waits for agent_end during long tool loops](https://github.com/earendil-works/pi/issues/7821) | Compaction check is deferred until `agent_end`, so long uninterrupted tool loops can overrun the configured window. (Now closed — addressed alongside #6879.) | 3 comments |
| #7782 | [Invalid tool call from Bedrock poisoned pi session](https://github.com/earendil-works/pi/issues/7782) | Pi accepted and replayed an invalid Bedrock tool call (`"": ""`), permanently bricking the session. Needs pre-execution validation. | 2 comments |
| #7820 | [openai-codex: stream requests have no retry wrapper](https://github.com/earendil-works/pi/issues/7820) | Mid-stream WebSocket disconnects (1006) are fatal — no retry logic exists for streaming calls through the Codex provider. | 2 comments |
| #7837 | [Fullscreen TUI mouse selection silently overwrites system clipboard](https://github.com/earendil-works/pi/issues/7837) | OSC 52 writes to clipboard on every selection with no opt-out, conflicting with user clipboard state. | 2 comments |
| #7734 | [print mode with extensions hangs at exit](https://github.com/earendil-works/pi/issues/7734) | When a subagent extension is loaded, Pi never exits after printing the final answer — process sits at 0% CPU. | 2 comments |
| #7815 | [glla: `replace` silently cancels a `wait` goal's scheduled resume](https://github.com/earendil-works/pi/issues/7815) | UX defect where replacing a goal cancels its resume, and `/goal resume` no-ops on archived goals. | 2 comments |
| #7814 | [Allow multiple logins for one provider](https://github.com/earendil-works/pi/issues/7814) | Users with multiple subscriptions (e.g., two ChatGPT Plus accounts) cannot use them concurrently without duplicating the OAuth flow. | 2 comments |
| #7829 | [Invalid settings.json silently ignored; misleading 'bash not found' error on Windows](https://github.com/earendil-works/pi/issues/7829) | Unescaped backslashes in Windows paths produce invalid JSON that is silently ignored, surface as a cryptic shell-not-found error. | 1 comment |

---

## 4. Key PR Progress

| # | PR | Description | Status |
|---|-----|------------|--------|
| #7610 | [feat(ai): add LLM Gateway and LLM Gateway DevPass providers](https://github.com/earendil-works/pi/pull/7610) | Adds LLM Gateway (OpenRouter-style router) as a built-in `openai-completions` provider. Replaces auto-closed #7480. | 🟢 Open |
| #7713 | [feat: stream assistant and config with telemetry](https://github.com/earendil-works/pi/pull/7713) | Implements `StreamAssistant` and `StreamAssistantConfig` with `telemetryContext` for harness v2. | 🟢 Open · In Progress |
| #7840 | [docs: add Aliyun Model Studio CLI to Related Tools](https://github.com/earendil-works/pi/pull/7840) | Documents `bailian-cli` as an official CLI extending coding agents with DashScope capabilities. | ✅ Closed (merged) |
| #7834 | [feat(coding-agent): annotate --version with runtime](https://github.com/earendil-works/pi/pull/7834) | `pi --version` now outputs runtime identifier (e.g. `0.84.1 (bun)`, `0.84.1 (node)`), closing #7244. | ✅ Closed (merged) |
| #7833 | [fix(examples): change notify extension from agent_end to agent_settled](https://github.com/earendil-works/pi/pull/7833) | `agent_end` fires before retries/compaction complete; switching to `agent_settled` ensures notifications are sent only when work is truly finished. | ✅ Closed (merged) |
| #7811 | [fix(ai): send max_tokens to native DeepSeek](https://github.com/earendil-works/pi/pull/7811) | DeepSeek silently ignores `max_completion_tokens`; this PR routes the correct field per provider. | ✅ Closed (merged) |
| #7823 | [feat: A-level capabilities from oh-my-pi](https://github.com/earendil-works/pi/pull/7823) | Ports stream rules (pattern-match abort + retry), subagent tools, advisor, and cross-session memory into core. | ✅ Closed (merged) |
| #7817 | [fix(ai): treat incomplete reason 'length' as a length stop](https://github.com/earendil-works/pi/pull/7817) | OpenAI-compatible providers like Doubao/Volcengine return `reason: 'length'` instead of `'max_output_tokens'`; now mapped correctly. | ✅ Closed (merged) |
| #7801 | [feat(coding-agent): lazily load uncommon syntax grammars](https://github.com/earendil-works/pi/pull/7801) | Experimental refactoring of syntax highlighting to load grammars on demand, reducing initial bundle size. | ✅ Closed (merged) |
| #7810 | [fix(coding-agent): reject concurrent compaction calls](https://github.com/earendil-works/pi/pull/7810) | Double-pressing `/compact` could crash the TUI with a signal-read error; now deduplicates in-flight compaction requests. | ✅ Closed (merged) |
| #7807 | [fix(ai): expose low reasoning effort for native DeepSeek V4 Flash](https://github.com/earendil-works/pi/pull/7807) | DeepSeek V4 Flash supports `low` reasoning effort separately from V4 Pro; PR adds per-model reasoning map. | 🟢 Open |
| #7721 | [fix(tui): avoid unwanted newlines when copying in fullscreen](https://github.com/earendil-works/pi/pull/7721) | Fullscreen mouse selection now tracks visual vs. logical rows, preventing inserted newlines on wrapped lines. | ✅ Closed (merged) |

---

## 5. Feature Request Trends

- **Multi-provider / multi-account support** — Users want concurrent logins per provider (#7814) and broader provider coverage (LLM Gateway #7610, Meta Model API #7543, Cloudflare AI Gateway #7838, Aliyun #7840).
- **Long-running session resilience** — Auto-compaction timing (#6879, #7821), stream retry logic (#7820), and session poisoning prevention (#7782) are top reliability concerns.
- **TUI ergonomics** — Configurable mouse wheel scroll (#7765), line-by-line transcript scrolling (#7830), horizontal scroll for long descriptions (#7827), and clipboard behavior (#7837) are frequently requested.
- **Extensibility surface** — Extension-side turn termination (#7824), message-identity in markdown transformers (#7828), and RPC session rebind fixes (#7831) show demand for richer extension APIs.
- **Session management** — Ability to delete the active session (#7818), multiple settings profiles (#7813), and immediate user-message display (#7819) round out the UX wishlist.

---

## 6. Developer Pain Points

1. **Streaming reliability** — The `openai-codex` provider lacks retry wrappers for mid-stream disconnects, causing frequent fatal failures on long turns (#4945, #7820).
2. **Compaction race conditions** — Compaction checks are deferred until `agent_end`, allowing tool loops to overshoot context limits; concurrent `/compact` presses can crash the TUI (#6879, #7821, #7810).
3. **Provider-specific field mismatches** — DeepSeek uses `max_tokens` not `max_completion_tokens`, and non-OpenAI providers return `reason: 'length'` instead of `'max_output_tokens'`, requiring per-provider workaround logic (#7811, #7817, #7807).
4. **Clipboard and TUI side-effects** — Fullscreen mode overwrites the system clipboard via OSC 52 without opt-out (#7837), and wrapped-line copying inserts spurious newlines (#7721).
5. **Silent failures masking real errors** — Invalid JSON in `settings.json` is silently ignored, surfacing as cryptic "bash not found" errors on Windows (#7829); invalid Bedrock tool calls poison sessions with no validation (#7782).
6. **Extension lifecycle hooks** — `agent_end` fires before retries/compaction finish, causing premature notifications; extensions need `agent_settled` and turn-termination hooks (#7833, #7824).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026‑08‑09

## 1. Today’s Highlights
Qwen Code v0.21.8 was released, restoring real‑time autofix for pull requests opened from forks and enabling compression‑cache sharing across OpenAI, Gemini, and Vertex AI backends. Community discussion is actively shaping cross‑session messaging and a unified turn‑based session runtime, while CI stability and trust‑scope edge cases remain top engineering priorities.

## 2. Releases
- **v0.21.8** ([release notes](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.8)) — Re‑enables PR autofix for fork‑originated pull requests by bridging review events to credentialed workflows. Adds compression‑cache sharing for OpenAI, Gemini, and Vertex AI providers.

## 3. Hot Issues
1. **[Feature] Build a lower‑maintenance desktop app around Web Shell** [#8092](https://github.com/QwenLM/qwen-code/issues/8092) — 6 comments. Proposes reusing the existing Web Shell as the primary UI to avoid maintaining a separate desktop product.
2. **[Bug] Main CI failed: E2E Tests** [#8756](https://github.com/QwenLM/qwen-code/issues/8756) — 5 comments. Tracks a main‑branch CI failure that completed without test results, triggering automated issue creation.
3. **[Bug] Main CI failed: E2E Tests — installs a local Qoder plugin** [#8766](https://github.com/QwenLM/qwen-code/issues/8766) — 4 comments. P1 bug with autofix already in progress; the E2E test for local plugin installation is failing.
4. **[Bug] CTRL+SHIFT+C not copying text** [#8317](https://github.com/QwenLM/qwen-code/issues/8317) — 4 comments. Users report that the standard terminal copy shortcut no longer works in the CLI.
5. **[Bug] Chrome remote‑debugging consent dialog re‑appears** [#8737](https://github.com/QwenLM/qwen-code/issues/8737) — 4 comments. The `chrome‑devtools` MCP with `--autoConnect` prompts for permission on every session.
6. **[Feature] Cross‑session messaging between sessions on the same machine** [#8724](https://github.com/QwenLM/qwen-code/issues/8724) — 4 comments. Enables one session to discover and send messages to another, gated by an explicit inbound permission check.
7. **[RFC] Native coordination for independent Qwen sessions** [#8718](https://github.com/QwenLM/qwen-code/issues/8718) — 4 comments. Suggests an experimental coordination path so a leader can dispatch worker sessions and collect structured results.
8. **[Bug] OTEL_METRICS_EXPORTER=otlp silently disables metrics export** [#8697](https://github.com/QwenLM/qwen-code/issues/8697) — 3 comments. When the standard OTel env var is set, Qwen Code’s telemetry SDK startup fails and native metrics stop flowing.
9. **[Bug] Auto session titles dominated by UserPromptSubmit hook context** [#8758](https://github.com/QwenLM/qwen-code/issues/8758) — 3 comments. Hooks that inject large `additionalContext` can cause auto‑generated titles to reflect hook metadata rather than the user’s actual request.
10. **[Bug] VS Code settings schema rejects supported prompt hooks** [#8752](https://github.com/QwenLM/qwen-code/issues/8752) — 3 comments. The generated VS Code schema validates against a outdated settings definition, flagging documented prompt hooks as invalid.

## 4. Key PR Progress
1. **#8762** — `fix(serve): stop usage_update frames from flooding the demo event log` — Stops `usage_update` frames from spamming the `/demo` Events tab; they now appear as a live context meter. ([PR](https://github.com/QwenLM/qwen-code/pull/8762))
2. **#8776** — `refactor(review): extract the toolchain adapter boundary` — Moves the npm implementation of `qwen review build‑test` behind an internal toolchain adapter, separating CLI routing from detection/verification logic. ([PR](https://github.com/QwenLM/qwen-code/pull/8776))
3. **#8764** — `fix(external-context): read the response body with a reader, not for-await` — Rewrites `readBoundedBody` to use an explicit `getReader()` loop, adding behavioral tests. ([PR](https://github.com/QwenLM/qwen-code/pull/8764))
4. **#8469** — `feat(acp): Protect against repeated tool execution failures` — Adds a conservative, prompt‑local guard that counts terminal execution failures and intervenes to prevent runaway tool loops. ([PR](https://github.com/QwenLM/qwen-code/pull/8469))
5. **#8614** — `feat(web-shell): add fullscreen view for the right artifact panel` — Adds a toggle to expand the right panel (artifacts, subagents, review changes, monitors) to fullscreen. ([PR](https://github.com/QwenLM/qwen-code/pull/8614))
6. **#8743** — `docs(design): Plan selective session restore` — Documentation‑only draft proposing selective daemon session restore as a performance‑focused slice of issue #8678. ([PR](https://github.com/QwenLM/qwen-code/pull/8743))
7. **#8714** — `feat(core): add native DashScope integration` — Introduces `dashscope` as a first‑class auth type that speaks Alibaba ModelStudio’s native generation API directly, bypassing the OpenAI‑compatible endpoint. ([PR](https://github.com/QwenLM/qwen-code/pull/8714))
8. **#8761** — `fix(ci): route workflow label mutations through REST` — Replaces all `gh pr edit` label mutations with REST `issues/labels` endpoints and adds a repo‑wide guard test. ([PR](https://github.com/QwenLM/qwen-code/pull/8761))
9. **#8675** — `feat(web-shell): add model‑specific reasoning controls` — Adds a built‑in registry for per‑model reasoning controls (Thinking, Effort) and wires it through Core, ACP, daemon, SDK, and WebShell. ([PR](https://github.com/QwenLM/qwen-code/pull/8675))
10. **#8730** — `feat(core): accept cross‑session messages behind an inbound gate` — Implements the messaging half of #8724; sessions can now be addressed by name and every inbound message is gated before model processing. ([PR](https://github.com/QwenLM/qwen-code/pull/8730))

## 5. Feature Request Trends
- **Cross‑session coordination & messaging** — Multiple issues (#8724, #8718, #8730) show strong community interest in allowing separate Qwen Code sessions to discover, message, and coordinate with each other, ideally with explicit safety gates.
- **Unified session runtime & reasoning controls** — The proposal to unify session reasoning loops on a turn‑based `SessionRuntime` (#8775) and add model‑specific reasoning controls (#8675) indicates a push toward consistent, configurable session behavior across all UI surfaces.
- **Desktop & terminal UX improvements** — Requests for a lower‑maintenance desktop app via the Web Shell (#8092), word‑wise drag selection in VP mode (#8738), and better `/clear` blocking messages (#8741) highlight demands for a more polished, familiar developer experience.

## 6. Developer Pain Points
- **CI fragility** — Several high‑comment issues track main‑branch CI failures (#8756, #8766) and test‑environment mismatches (macOS permission tests #8753, npm test flag errors #8721). Automated autofix tracking is active but instability remains a concern.
- **Configuration drift & schema mismatches** — The VS Code settings schema rejects documented prompt hooks (#8752), and a config flag `general.dynamicCommandTranslation` is exposed but non‑functional at runtime (#8748), pointing to maintenance gaps between documentation, schema generation, and core implementation.
- **Trust‑scope & security edge cases** — Issues around ancestor `TRUST_FOLDER` overriding explicit `DO_NOT_TRUST` rules (#8627) and read‑only git sub‑commands executing programs from `.git/config` (#8575) reveal pain around permission inheritance and supply‑chain‑adjacent risks.
- **Telemetry & environment interference** — Setting `OTEL_METRICS_EXPORTER=otlp` silently breaks native metrics export (#8697), a common pattern when multiple AI CLIs share an environment, causing frustration for observability‑focused users.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-09

## 1. Today's Highlights

CodeWhale v0.9.5 has landed, consolidating the terminal app into a single compiled runtime while removing default turn ceilings and aligning all release surfaces around the `codewhale` / `codew` commands. The v0.9.5 milestone tracker (issue #5266) is now open for triage, and Mistral AI has been added as a first-class provider route (PR #5295). The legacy `deepseek-tui` npm package remains deprecated with no further releases.

---

## 2. Releases

**v0.9.5** (published 2026-08-08) — [PR #5292](https://github.com/Hmbown/CodeWhale/pull/5292)
The centerpiece release consolidates `codewhale-tui` into one compiled runtime, removes the default turn ceilings that interrupted long work sessions, and aligns the updater, installers, release assets, website, and package surfaces. The `codewhale` command and npm package are now the sole supported entry points; the legacy `deepseek-tui` package is deprecated.

**v0.9.4** — [PR #5292](https://github.com/Hmbown/CodeWhale/pull/5292)
Preceding release; already included some mitigations for the 128K context-window fallback behavior later addressed in #5244.

---

## 3. Hot Issues

| # | Title | Why It Matters | Comments |
|---|-------|---------------|----------|
| [#4022](https://github.com/Hmbown/CodeWhale/issues/4022) | Define CLI/TUI parity for subagent and runtime control surfaces | Subagent controls became TUI-only during v0.8.67 hardening; the community needs parity so future cloud apps and remote workbench clients can expose the same surfaces. | 8 |
| [#4785](https://github.com/Hmbown/CodeWhale/issues/4785) | Dead-code sweep: 464 `#[allow(dead_code)]` attributes hiding drift | A wall of 464 suppressions across 143 files makes the compiler structurally unable to report dead-code drift, a growing maintenance liability. | 6 |
| [#4326](https://github.com/Hmbown/CodeWhale/issues/4326) | Perf: bound RSS after cancelling a 32-worker storm | Post-cancel RSS increase instead of settling raises the question of allocator high-water retention vs. real runtime leak — critical for high-fan-out workloads. | 6 |
| [#4416](https://github.com/Hmbown/CodeWhale/issues/4416) | Isolate stale failed-agent state between CodeWhale sessions | Opening a second instance in the same workspace shows red failed-agent rows from an earlier session — stale task prompts are visible as live work, eroding trust. | 4 |
| [#5034](https://github.com/Hmbown/CodeWhale/issues/5034) | Switching providers can retain an unrelated default model | Switching to OpenAI can leave the default model set to `gpt-5.5` inherited from a different route, indicating provider and model resolution are not updated coherently. | 3 |
| [#5272](https://github.com/Hmbown/CodeWhale/issues/5272) | Prompt-scoped file recovery (restore workspace from a prior prompt) | When an agent damages the tree, recovery is currently `git` archaeology; the community wants a session-snapshot restore that cooperates with git and confirms before destructive actions. | 2 |
| [#5270](https://github.com/Hmbown/CodeWhale/issues/5270) | Unified tasks surface (shell + subagents + durable workers) | Tasks panel pieces, Fleet (`crates/lane`), and Workflow exist but are fragmented; a single operator-facing list would unify background work visibility. | 2 |
| [#5271](https://github.com/Hmbown/CodeWhale/issues/5271) | Session peek (list / peek / answer approvals without full attach) | Multi-session control is currently a resume picker; users want to answer approvals and dispatch without losing their current composer context. | 2 |
| [#5267](https://github.com/Hmbown/CodeWhale/issues/5267) | Turn-stop honesty (status that says ending must end) | Users lose trust when the footer says "ending" / "stopping" and the model keeps talking; four resume paths (subagent drain, REPL fence, goal, etc.) need alignment. | 2 |
| [#5244](https://github.com/Hmbown/CodeWhale/issues/5244) | Unknown model IDs silently degrade to the 128K legacy context default | A 1M-window model silently compacts at 128K with no surfaced hint — a residual bug behind #5239 that the community flagged as a trust issue. | 2 |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5306](https://github.com/Hmbown/CodeWhale/pull/5306) | Validate crate publication order | ✅ Closed | Validates the 20-crate publication order against locked Cargo metadata; fails closed on duplicates, missing/extra crates, mixed versions, and dependency inversions. |
| [#5308](https://github.com/Hmbown/CodeWhale/pull/5308) | Use CNB asset download URLs | 🔄 Open | Uses the canonical `codewhale.net/codewhale` CNB repository slug and adds the required `/-/releases/download/vX.Y.Z` path so mirror mode receives asset bytes instead of release HTML. |
| [#5295](https://github.com/Hmbown/CodeWhale/pull/5295) | Add Mistral AI as a first-class provider route | ✅ Closed | First-time contributor @xavierpestel-ai adds Mistral (`mistral-code-latest`) with `provider = "mistral"`, `CODEWHALE_PROVIDER=mistral`, and `codewhale --provider mistral` support. |
| [#5301](https://github.com/Hmbown/CodeWhale/pull/5301) | Make compaction live and pressure-aware | ✅ Closed | Manual `/compact` now enqueues nonblocking with typed lifecycle IDs; aligns 128K/272K/1M auto-compaction eligibility with full conservative request pressure. |
| [#5300](https://github.com/Hmbown/CodeWhale/pull/5300) | Refactor(core): own primary request preparation | 🔄 Open | Replaces the unused synthetic `ChatRequest` scaffold with the production `MessageRequest` DTO family previously owned by the TUI crate; adds a provider-neutral `prepare_primary_turn_request` constructor. |
| [#5133](https://github.com/Hmbown/CodeWhale/pull/5133) | Expose persistent goal-loop state and completion controls | ✅ Closed | Adds `GET /v1/threads/{id}/goal` so managed clients can read active-goal state and drive lifecycle transitions through the runtime boundary. |
| [#5132](https://github.com/Hmbown/CodeWhale/pull/5132) | Expose verifier receipts and evidence | ✅ Closed | Three new read-only endpoints under `/v1/fleet/runs/{run_id}/` (including `GET receipts`) give managed clients visibility into which task failed and why. |
| [#5131](https://github.com/Hmbown/CodeWhale/pull/5131) | Runtime API memory endpoints | ✅ Closed | Adds `/v1/memory` routes for bounded inspection and lifecycle controls, gated behind `require_runtime_token`. |
| [#5130](https://github.com/Hmbown/CodeWhale/pull/5130) | Bounded MCP server configuration and lifecycle | ✅ Closed | Adds `POST /v1/apps/mcp/servers` and mutation routes, removing the need to edit TOML/JSON directly for MCP server management. |
| [#5129](https://github.com/Hmbown/CodeWhale/pull/5129) | Skill lifecycle endpoints | ✅ Closed | Adds install, update, uninstall, trust, and audit routes under the Runtime API, matching what the TUI already offered. |

---

## 5. Feature Request Trends

**Multi-session orchestration** — Issues #5270, #5271, and #4416 all point to the same direction: users want unified control across sessions, workers, and subagents without losing context or being misled by stale state. The emerging contract is a single tasks surface + session-peek workflow.

**Provider-agnostic architecture** — Issues #5103, #5092, #5093, #5094 and PR #5295 reflect a clear trend: rename `DeepSeekClient` internals to provider-neutral types, make Responses dialect behavior provider-profiled rather than hard-coded, and expose typed dialect selection for custom providers. The Mistral integration is the first visible outcome.

**Turn-loop reliability and honesty** — Issues #5267, #5268, and #5269 form a cluster around mid-turn controls, durable plan artifacts, and honest stop semantics. The community wants a crisp contract between "send-now" vs. "queue" vs. "cancel-keep-draft" and status chrome that accurately reflects agent state.

**Compaction as a first-class guarantee** — Issues #4394 and #5272 (along with PR #5301) show growing demand for compaction that preserves active intent, decisions, evidence, and tool continuity — not just transcript truncation. Prompt-scoped file recovery extends this further.

---

## 6. Developer Pain Points

- **Monolith build times** — Issue #5249 documents that the 682,959-line, 620-file `codewhale-tui` crate accounts for 86% of the workspace and recompiles as one unit, taxing every edit-compile, commit, test, and release loop. This is the single highest-friction item for contributors.

- **Stale state bleeding across sessions** — Issue #4416 and the RSS retention problem in #4326 both describe state from one session or operation leaking into another (failed-agent rows, post-cancel RSS spikes), eroding user trust in the TUI's accuracy.

- **Silent fallbacks that degrade silently** — Issue #5244 (unknown model IDs falling back to 128K context with no warning) and #5034 (wrong default model retained on provider switch) share a pattern: the system makes a reasonable-but-unexpected choice without surfacing it, causing confusion and lost productivity.

- **Dead-code wall** — Issue #4785's 464 `#[allow(dead_code)]` suppressions across 143 files represent a structural maintenance burden that makes it impossible for the compiler to flag drift, and the community has flagged this as a cleanup priority.

- **Fragmented notification UX** — Issue #5041 calls out that toasts and system notifications are not consistently actionable or branded, with unpredictable triggers and hard-to-discover controls.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*