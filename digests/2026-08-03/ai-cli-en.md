# AI CLI Tools Community Digest 2026-08-03

> Generated: 2026-08-03 03:35 UTC | Tools covered: 10

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



# Cross-Tool Comparison Report: AI CLI Developer Tools Ecosystem
**Date: 2026-08-03**

---

## 1. Ecosystem Overview

The AI CLI tools landscape is in a phase of intense consolidation and maturation. All major players are moving beyond single-session chat toward persistent, agent-driven workflows with multi-session orchestration, cross-device continuity, and cost-aware operation. The dominant theme across every community is reliability under concurrency — session-state corruption, token-waste from polling loops, and sub-agent management gaps are the top pain points. Meanwhile, feature requests are converging around dynamic model routing, persistent memory, and granular cost controls, suggesting the market is shifting from "can it code?" to "can it run reliably at scale?"

---

## 2. Activity Comparison

| Tool | Open Issues | PRs Landed/In Review | Release (Last 24h) |
|------|------------|---------------------|-------------------|
| **Claude Code** | 10 hot | 4 (2 closed, 2 open) | None |
| **OpenAI Codex** | 10 hot | 5 (3 closed, 2 open) | None |
| **Gemini CLI** | 10 hot | 9 (2 closed, 7 open) | ✅ Nightly v0.55.0 |
| **GitHub Copilot CLI** | 10 hot | 0 | None |
| **Kimi Code CLI** | 4 hot | 1 (closed) | None |
| **OpenCode** | 10 hot | 11 (6 closed, 5 open) | None |
| **Pi** | 10 hot | 12 (7 closed, 5 open) | None |
| **Qwen Code** | 9 hot | 11 (all open/in-progress) | ✅ Nightly v0.21.3 |
| **DeepSeek TUI** | 9 hot | 10 (1 closed, 9 open) | None (v0.9.4 train merged) |
| **Grok Build** | — | — | None |

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Need |
|-------|---------------|---------------|
| **Persistent cross-session memory** | Kimi Code (#1283), OpenCode (implicit), Pi (facts/queries), Claude Code (Cowork instructions) | Users want context retention across invocations, not stateless REPLs |
| **Dynamic model routing** | OpenCode (#18793, #18844), Pi (#7487), Gemini CLI (model selection) | Per-request or per-complexity model selection via plugins/config |
| **Token-cost transparency & control** | OpenAI Codex (#2916, #13733, #35259), Pi, Claude Code (Fable 5 billing #83242) | Service-tier support, visible usage limits, and fixes for polling-induced token waste |
| **Multi-agent/sub-agent orchestration** | DeepSeek TUI (#425, #5136, #5138), Kimi Code (#2578), Claude Code (concurrency bugs #82491, #83457), Gemini CLI (#22323) | Reliable session resumption, continuation chains, and fault-tolerant batch execution |
| **Remote/cross-device session control** | Kimi Code (#1282), Gemini CLI (headless VPS #28446), Qwen Code (daemon sessions #8389) | Continue sessions from phones/browsers; wake channels for external agents |
| **Session-state reliability** | Claude Code (#4329 cluster), OpenAI Codex (#35420, #36663), Qwen Code (#8382, #7164, #8411) | State persistence across resume, session ID coordination, duplicate ID prevention |

---

## 4. Differentiation Analysis

| Tool | Differentiator | Target User | Technical Approach |
|------|--------------|-------------|-------------------|
| **Claude Code** | Deepest plugin/hook ecosystem; MCP integration; Cowork team features | Enterprise & team workflows | Hook-based extensibility; plugin marketplace; concurrent subagent model |
| **OpenAI Codex** | Tight ChatGPT/Work/Desktop integration; Max reasoning effort controls | OpenAI platform subscribers; VS Code users | Desktop + CLI dual surface; token-waste from polling is a known architectural flaw |
| **Gemini CLI** | Fastest release cadence (daily nightlies); security-focused dependency bumps; AST-aware tooling探索 | Android/Linux power users; security-conscious developers | Node.js-based; zero-dependency sandboxing proposals; sub-agent recovery focus |
| **GitHub Copilot CLI** | ACP (Agent Context Protocol) integration; autopilot mode; Microsoft ecosystem | GitHub/Copilot subscribers; enterprise | SDK-driven; autopilot state management is fragile; model API surface inconsistency |
| **Kimi Code CLI** | Swarm-mode parallel subagents; remote control; cross-device continuation | Chinese/English bilingual users; multi-device workflow adopters | Minimal CLI; plugin-light; batch resilience is a gap |
| **OpenCode** | Most active PR pipeline (11 PRs); `chat.model` hook enables dynamic routing; air-gapped mode | Privacy-conscious; plugin developers; air-gap deployments | Go-based; SQLite persistence; per-MCP-server trust; `OPENCODE_AIRGAP` env var |
| **Pi** | In-memory session backend; experiment-backed compaction; DeepInfra/LLM Gateway providers | Power users; self-hosted/enterprise | Rust/TS hybrid; faceted session repositories; hardware cursor & IME terminal quirks |
| **Qwen Code** | `qwen --serve` daemon mode; Plan & Review workflow; audio bridge; Maven workspace support | Enterprise Java/Node monorepos; daemon-powered workflows | TypeScript; OpenAI-compatible provider abstraction; desktop Tauri client |
| **DeepSeek TUI** | Fleet named agents; `send_later` scheduled tool; `/dryrun` cost preview; zh-Hant i18n | Chinese-language users; fleet-scale agent orchestration | Rust-based; v0.9.4 hardening sprint; exec-policy and security bypass fixes |

---

## 5. Community Momentum & Maturity

**High Momentum (rapid iteration, high issue velocity):**
- **OpenCode** — 11 PRs in 24h with a clean landing of the long-requested `chat.model` hook; active fix pipeline for persistence, Unicode, and OAuth edge cases.
- **Pi** — 12 PRs including experimental in-memory sessions, provider additions, and compaction fixes; strongest signal of a team iterating fast on infrastructure.
- **Gemini CLI** — Daily nightlies with substantive security and fix PRs; 9 PRs including a major GenAI SDK bump (1.30 → 2.13).

**Maturing with Depth (large communities, entrenched pain points):**
- **Claude Code** — 96-comment unresolved visualize outage; cross-session concurrency bugs signal growing pains of a complex multi-agent system.
- **OpenAI Codex** — Token-waste from polling is the #1 community concern (30+ 👍, multiple related issues); indicates a mature user base hitting production-scale costs.

**Emerging (smaller issue counts but focused direction):**
- **Kimi Code CLI** — 4 hot issues all pointing toward session continuity and swarm resilience; fewer complaints but clear roadmap signals from the maintainer.
- **Qwen Code** — Daemon-first architecture and Plan & Review workflow suggest differentiation toward enterprise automation.
- **DeepSeek TUI** — v0.9.4 release train (77 commits) followed by an immediate hardening sprint (R1/R3) indicates a team responding aggressively to production feedback.

**Low Activity:**
- **GitHub Copilot CLI** — 0 PRs, 11 open issues with no maintainer response; the weakest engagement signal.
- **Grok Build** — No activity.

---

## 6. Trend Signals

| Signal | Evidence | Implication for Developers |
|--------|----------|---------------------------|
| **Polling-induced token waste is systemic** | OpenAI Codex (#13733, #35259, #22411), Claude Code (#83288 SDK CPU spin) | Any tool used in CI/production at scale will face cost surprises; evaluate token economics before adoption |
| **Session state is the new frontier** | Duplicate tool IDs (Qwen #8382), autopilot loss on resume (Copilot #4329), transcript corruption (Qwen #7164) | Reliable checkpoint/recovery is table-stakes; tools without it will struggle in agent-heavy workflows |
| **Dynamic model routing is becoming a plugin primitive** | OpenCode's `chat.model` hook, Pi's `/scoped-models`, Qwen's per-request provider selection | Multi-model strategies (cheap/fast for simple tasks, expensive for complex) will be a standard feature, not a manual toggle |
| **Cross-device and remote session control is a differentiator** | Kimi Code (#1282), Qwen daemon, Gemini headless fixes | Remote interrupt/continuation is a premium workflow; tools that support it well will attract distributed teams |
| **Security hardening is accelerating post-launch** | DeepSeek TUI's v0.9.4 hardening stack (exec-policy bypasses, MCP filtering gaps), Gemini's dependency bumps, OpenCode's air-gap mode | Mature tools are closing security surface areas; expect more security-focused releases across the board |
| **Sub-agent orchestration reliability is unsolved** | Gemini subagent hangs (#21409, #22323), Kimi swarm failures (#2578), Claude cross-session bleed (#82491) | Parallel agent execution remains a weak point; tools with proven resilience (or clear escape hatches) will win enterprise users |
| **Silent regressions erode trust** | OpenCode session titles (#20269), Claude Cowork instructions reverting (#40175), Codex sandbox SIGABRT (#35437) | Observability into state changes and explicit failure modes are needed; silent failures are a top community complaint |

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-03 | Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

Ranked by community attention (issue cross-references, update recency, and discussion volume). Comment counts for PRs were not populated in the dataset; rankings use proxy signals including linked issues, update frequency, and community endorsement.

| # | Skill / PR | Functionality | Discussion Highlights | Status |
|---|---|---|---|---|
| 1 | **#1367** — [Self-Audit Skill](https://github.com/anthropics/skills/pull/1367) | Pre-delivery audit of AI output: mechanical file verification + four-dimension reasoning quality gate. Works universally across projects and models. | Spawned from community proposal [#1385](https://github.com/anthropics/skills/issues/1385); directly implements the "reasoning quality gate pipeline" discussed by multiple users. Author YuhaoLin2005 is also the proposal author. | 🟡 Open |
| 2 | **#1298** — [Fix: run_eval.py recall = 0%](https://github.com/anthropics/skills/pull/1298) | Fixes the skill-creator evaluation pipeline so descriptions actually produce meaningful recall signals. | Multiple independent reproductions reported in [#556](https://github.com/anthropics/skills/issues/556), [#1169](https://github.com/anthropics/skills/issues/1169), and [#1323](https://github.com/anthropics/skills/issues/1323). Windows-specific variant in [#1099](https://github.com/anthropics/skills/issues/1099). The entire description-optimization loop depends on this fix. | 🟡 Open |
| 3 | **#83** — [Skill Quality & Security Analyzers](https://github.com/anthropics/skills/pull/83) | Two meta-skills: `skill-quality-analyzer` (5-dimension evaluation) and `skill-security-analyzer` (security audit). | Directly addresses security concerns raised in community issue [#492](https://github.com/anthropics/skills/issues/492) about unvetted community skills. Proposes structured quality gating before skill adoption. | 🟡 Open |
| 4 | **#525** — [Pyxel Retro Game Dev Skill](https://github.com/anthropics/skills/pull/525) | MCP-server-powered skill for 8-bit / pixel-art game development with Pyxel engine. | Distinct from the predominantly enterprise/developer-focused skills; reflects community interest in creative/education use cases. Last updated July 2026, suggesting sustained interest. | 🟡 Open |
| 5 | **#723** — [Testing-Patterns Skill](https://github.com/anthropics/skills/pull/723) | Comprehensive testing skill: testing philosophy, unit tests (AAA pattern), React component testing (Testing Library), TDD workflows. | Fills a gap identified in issue discussions around test generation and code review quality. Covers both theory and framework-specific guidance. | 🟡 Open |
| 6 | **#486** — [ODT Skill](https://github.com/anthropics/skills/pull/486) | OpenDocument Format skill: create, fill, read, and convert .odt / .ods files; triggers on ODT, ODS, ODF, LibreOffice keywords. | Addresses the open-standard / LibreOffice user segment underrepresented in the current skills catalog. | 🟡 Open |
| 7 | **#514** — [Document Typography Skill](https://github.com/anthropics/skills/pull/514) | Prevents orphan word wraps, widow paragraphs, and numbering misalignment in AI-generated documents. | Targets a universally experienced but rarely addressed pain point. Highlights demand for "polish" skills beyond pure code generation. | 🟡 Open |
| 8 | **#1302** — [Color-Expert Skill](https://github.com/anthropics/skills/pull/1302) | Color naming systems (ISCC-NBS, Munsell, XKCD, RAL), color space selection guide (OKLCH, OKLAB, CAM16), and practical color workflows. | Niche domain expertise made actionable; reflects demand for specialized knowledge skills outside the typical dev stack. | 🟡 Open |

---

## 2. Community Demand Trends

Distilled from the most-commented issues and recurring themes:

| Trend | Evidence |
|---|---|
| **🔒 Security & trust boundaries** | Issue [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍) — community skills impersonating the `anthropic/` namespace; users demand verification and trust-layer tooling |
| **🏢 Org-wide skill sharing** | Issue [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) — strong demand for built-in sharing within organizations, eliminating manual .skill file distribution |
| **✅ Evaluation & quality gating** | Issues [#556](https://github.com/anthropics/skills/issues/556), [#1169](https://github.com/anthropics/skills/issues/1169), [#1385](https://github.com/anthropics/skills/issues/1385) — multiple users hit the same `recall=0%` bug; demand for reliable skill evaluation and reasoning quality gates |
| **🧠 Agent memory & state management** | Issue [#1329](https://github.com/anthropics/skills/issues/1329) — proposal for `compact-memory` skill using symbolic notation to reduce context consumed by agent notes |
| **🔍 Code review & governance** | Issue [#412](https://github.com/anthropics/skills/issues/412) — proposal for `agent-governance` skill covering policy enforcement, threat detection, trust scoring, and audit trails |
| **🪟 Windows compatibility** | Issues [#1061](https://github.com/anthropics/skills/issues/1061), [#1099](https://github.com/anthropics/skills/issues/1099), [#1050](https://github.com/anthropics/skills/issues/1050) — persistent pain points with subprocess handling, PATHEXT, and encoding on Windows |
| **📐 Documentation & skill hygiene** | Issue [#189](https://github.com/anthropics/skills/issues/189) (6 comments, 9 👍) — duplicate skill installation from overlapping plugins; Issue [#1479](https://github.com/anthropics/skills/pull/1479) proposes `plan-file-hygiene` to manage planning artifact lifecycle |

---

## 3. High-Potential Pending Skills

PRs with active discussion or strong community signal, not yet merged as of 2026-08-03:

| PR | Skill | Why It May Land Soon |
|---|---|---|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit** | Direct implementation of a widely discussed proposal; covers a critical gap in the skill delivery pipeline |
| [#1298](https://github.com/anthropics/skills/pull/1298) | **run_eval.py fix** | Blocker for the entire skill-creator evaluation loop; 10+ independent reproductions make this a high-priority fix |
| [#83](https://github.com/anthropics/skills/pull/83) | **Skill Quality & Security Analyzers** | Addresses the #1 community concern (issue [#492](https://github.com/anthropics/skills/issues/492)); provides infrastructure the org already needs |
| [#1479](https://github.com/anthropics/skills/pull/1479) | **Plan-File-Hygiene** | Named and framed by community contributors; solves a recognized lifecycle gap for agent planning artifacts |
| [#1302](https://github.com/anthropics/skills/pull/1302) | **Color-Expert** | Latest update (July 21) suggests active refinement; fills a unique niche with no competing skill |
| [#1261](https://github.com/anthropics/skills/pull/1261) | **skill-creator trigger-eval isolation fix** | Fixes a concurrency bug that corrupts the user's project during parallel eval — a practical fix with clear impact |
| [#723](https://github.com/anthropics/skills/pull/723) | **Testing-Patterns** | Broad appeal across the developer community; addresses consistent demand for testing guidance in skill requests |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **trust and quality infrastructure** — skills that verify, evaluate, and govern other skills — rather than for additional domain-specific capabilities, reflecting a maturing ecosystem where reliability and security concerns now outweigh feature breadth.

---



# Claude Code Community Digest — 2026-08-03

---

## 1. Today's Highlights

No new releases were published in the last 24 hours. The community's most pressing concern remains the **`claude.ai` visualize feature outage** (#34820) with 96 comments and 39 upvotes, while a new class of bugs surfaced around concurrent tool-call payload misdelivery and SDK-related CPU spin in headless sessions.

---

## 2. Releases

*No releases in the last 24 hours.*

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#34820](https://github.com/anthropics/claude-code/issues/34820) | `claude.ai` visualize feature broken — DNS resolution failure for `claudemcpcontent.com` | Blocks a core browser-side debugging experience for all users relying on the web visualizer. | 96 comments · 39 👍 — persistent, unresolved since March. |
| [#2805](https://github.com/anthropics/claude-code/issues/2805) | Windows line endings on Linux systems | Causes scripts to fail with "No such file or directory"; affects every Linux developer in the loop. | 44 comments · 33 👍 — widely felt, reproducible. |
| [#32870](https://github.com/anthropics/claude-code/issues/32870) | `claude.exe` triggers Windows BSOD via `Wof.sys` during directory listing | Critical stability issue — a full OS crash triggered by normal CLI operation on Windows. | 38 comments · 1 👍 — low engagement but high severity. |
| [#40175](https://github.com/anthropics/claude-code/issues/40175) | Cowork global instructions silently revert to older version after saving | Undermines trust in shared instruction persistence across team workspaces. | 32 comments · 20 👍 — painful for collaborative workflows. |
| [#77966](https://github.com/anthropics/claude-code/issues/77966) | OAuth login loop on Linux — `state` parameter dropped on redirect | Blocks authentication entirely for affected users; a hard stopper. | 20 comments · 14 👍 — reproducible, blocking. |
| [#83288](https://github.com/anthropics/claude-code/issues/83288) | Headless SDK-spawned CLI burns ~33% CPU per session (futex spin) | Directly impacts any production or CI workload running Claude Code via the SDK at scale. | 2 comments · 0 👍 — newly reported, likely will grow. |
| [#82491](https://github.com/anthropics/claude-code/issues/82491) | Bash `tool_result` replaced by concurrent session's assistant output (cross-session bleed) | Data integrity issue in multi-session setups; assistant text from one session appears in another. | 2 comments · 0 👍 — closed, but signals a real concurrency bug class. |
| [#75900](https://github.com/anthropics/claude-code/issues/75900) | Assistant text between tool calls not rendered, saved, or visible in `ctrl-o` | Loses conversational context and breaks auditability of agent runs. | 2 comments · 2 👍 — reported by Jeremy Howard's team. |
| [#83457](https://github.com/anthropics/claude-code/issues/83457) | Remote MCP connector: response delivered to wrong concurrent tool call | Payload misdelivery in concurrent subagent calls causes 180s timeouts and incorrect behavior. | 0 comments · 0 👍 — brand new, high-severity concurrency bug. |
| [#31888](https://github.com/anthropics/claude-code/issues/31888) | Batch diff review mode — show all changes before approval | Aligns Claude Code with Cursor's native agent workflow; highly requested UX improvement. | 16 comments · 46 👍 — strongest community signal for a feature gap. |

---

## 4. Key PR Progress

| # | PR | Author | Summary |
|---|-----|--------|---------|
| [#77977](https://github.com/anthropics/claude-code/pull/77977) | `docs(plugin-dev): document skipLfs marketplace sources` | @superdiaodiao | Documents the `skipLfs` option for GitHub and generic Git marketplace sources, addressing a gap referenced in #63035. |
| [#83374](https://github.com/anthropics/claude-code/pull/83374) | `docs(plugin-dev): add MessageDisplay hook guidance` | @iCodeCraft | Adds the missing `MessageDisplay` hook to the bundled Hook Development skill — streaming behavior docs were previously omitted. |
| [#26056](https://github.com/anthropics/claude-code/pull/26056) | `Fix code-review plugin posting to GitHub without --comment flag` | @apoorvdarshan | Strengthens guardrails so the model stops at terminal output when `--comment` is absent; adds behavioral rule and step conditionals. Fixes #16606. |
| [#48343](https://github.com/anthropics/claude-code/pull/48343) | `fix(plugin-dev): make skill-reviewer frontmatter valid YAML` | @Rohan5commit | Rewrites the `skill-reviewer` frontmatter description as a YAML block scalar; fixes a parse error that blocked plugin validation. Part of #40370. |

---

## 5. Feature Request Trends

- **Batch diff review mode** (#31888, 46 👍) — Developers want a Cursor-like "see all changes before approving" flow rather than step-by-step review.
- **Agent Hierarchy Dashboard** (#24537, 17 👍) — Real-time multi-agent workflow visualization (TUI + Desktop) is a recurring ask for complex agent setups.
- **Scoped rate-limit data in statusline JSON** (#81940, 3 👍) — With Fable 5's separate weekly cap, users need per-model rate-limit visibility in tooling payloads.
- **Configurable session naming** (#83455, 0 👍) — Auto-generated session names don't scale for parallel or background jobs; users want template-driven naming.
- **Individual plan-level M365 write tools** (#81317, 2 👍) — Request to expose Microsoft 365 write permissions on a per-plan basis rather than a blanket toggle.
- **Persistent "keep sidebar open" setting** (#75523, 2 👍) — The `Ctrl+B` pin is undiscoverable; users want an explicit config option.

---

## 6. Developer Pain Points

1. **Concurrency & parallel-session bugs** — Cross-session output bleed (#82491), payload misdelivery in concurrent MCP calls (#83457), and assistant-text loss between tool calls (#75900) all point to a fragile multi-operation execution model.
2. **SDK performance regression** — The ~33% per-core CPU spin in headless SDK-spawned CLI sessions (#83288) is a serious blocker for CI/production use.
3. **Platform-specific line-ending bugs** — Windows CRLF on Linux (#2805) continues to break shell scripts and is a long-standing frustration.
4. **Authentication reliability** — OAuth state-parameter loss on Linux (#77966) creates hard login loops with no known workaround.
5. **Desktop app plugin instability** — Stale `gitCommitSha`, silent update no-ops, and sessions loading old plugin versions after `claude plugin update` (#73673, #83447) erode trust in the desktop plugin lifecycle.
6. **Worktree / submodule handling** — Desktop app sessions fail to initialize git submodules (#83411), silently breaking `CLAUDE.md` imports that work fine on the CLI.
7. **Model behavior drift** — Fable 5 applying code changes and restarting services before the user approves (#83458) and incorrectly drawing from usage credits on Max 20x plans (#83242) signal growing pains with newer model releases.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-03

## Today's Highlights
The community is overwhelmingly focused on token-waste bugs caused by background polling loops, with multiple reports of sessions consuming entire weekly allowances in hours. The macOS Codex Diff crash remains the top-voted open issue (115 👍), while a new batch of Windows-specific bugs appeared today around session resumption and migration from the standalone Codex app to the unified ChatGPT Desktop.

---

## Releases
No new releases in the last 24 hours.

---

## Hot Issues

### 1. Codex Diff crashes with "Oops, an error has occurred" in VS Code on macOS [#35058](https://github.com/openai/codex/issues/35058)
**115 👍 · 46 comments · Updated 2026-08-03**
The most-upvoted open issue. The Codex Diff tab is entirely unusable on macOS/Apple Silicon after any edit—every repository, including fresh workspaces, reproduces the crash. High community frustration given how central the diff view is to the extension workflow.

### 2. Background process polling wastes tokens: each write_stdin poll triggers full API turn [#13733](https://github.com/openai/codex/issues/13733)
**30 👍 · 35 comments · Updated 2026-08-03**
Every status check during a running background process (e.g. `cargo build`) fires a complete API round-trip with full conversation history. This makes long builds prohibitively expensive in tokens and is a known architectural pain point that has persisted since March.

### 3. OpenAI service tier support [#2916](https://github.com/openai/codex/issues/2916)
**54 👍 · 21 comments · Updated 2026-08-03**
Users want a `service_tier` config option to control API cost/latency trade-offs. With tiered pricing becoming more common, this is a high-priority feature request for cost-conscious teams and individual developers.

### 4. Tabbed interface for parallel chat sessions in Codex extension [#12098](https://github.com/openai/codex/issues/12098)
**55 👍 · 19 comments · Updated 2026-08-03**
Switching between chat sessions currently requires multiple steps. A tabbed UI would bring the VS Code extension in line with developer expectations for multi-session workflows.

### 5. Codex Desktop repeatedly re-enters model during wait/status polling, consuming credits [#35259](https://github.com/openai/codex/issues/35259)
**2 👍 · 11 comments · Updated 2026-08-03**
During Ultra and multi-agent work, polling for agent/terminal status accounts for ~20% of raw local token volume. Directly related to #13733 but from the Desktop app perspective.

### 6. Work/Codex stream disconnects on OneDrive-backed Windows workspaces [#35420](https://github.com/openai/codex/issues/35420)
**0 👍 · 27 comments · Updated 2026-08-03**
When OneDrive is degraded, the Windows ChatGPT Work surface repeatedly fails with stream disconnect errors. Two request IDs per failure suggests a non-deterministic retry pattern.

### 7. Weekly allowance drops ~1% per Luna task on ChatGPT Pro [#36644](https://github.com/openai/codex/issues/36644)
**1 👍 · 5 comments · Updated 2026-08-03**
Pro subscribers report disproportionately fast weekly allowance consumption on Luna tasks, suggesting a possible billing or quota-metric mismatch.

### 8. app-server loads ALL session files on every thread/list call — high CPU, slow startup, token waste [#22411](https://github.com/openai/codex/issues/22411)
**0 👍 · 5 comments · Updated 2026-08-03**
A performance regression that worsens over time: after months of use, the app-server deserializes every session file on each list call, causing catastrophic slowdowns and invisible token burn.

### 9. Max reasoning effort missing in VS Code extension [#35763](https://github.com/openai/codex/issues/35763)
**2 👍 · 7 comments · Updated 2026-08-03**
The Codex App surface exposes Max reasoning effort for GPT-5.6-Sol, but the VS Code extension lacks this control—an inconsistency users have flagged.

### 10. File-change approval prompt is blank when reason is absent [#36637](https://github.com/openai/codex/issues/36637)
**0 👍 · 4 comments · Updated 2026-08-03**
In Codex CLI 0.146.0, a file-change approval can show three blank rows and ask the user to approve an action without identifying the target. Reproducible and blocks clear decision-making.

---

## Key PR Progress

### 1. Capture rollout budget units from response usage — [#36641](https://github.com/openai/codex/pull/36641) ✅ Closed
Parses `codex_rollout_budget_units` from Responses API usage into `TokenUsage`, keeping the provider-only value out of serialized protocol and schema. Addresses rollout budgeting accuracy.

### 2. Preserve SQLite thread metadata during goal mutations — [#36632](https://github.com/openai/codex/pull/36632) ✅ Closed
Fixes a bug where setting/clearing a thread goal could overwrite SQLite-only metadata (including thread preview) by reconciling an already-indexed rollout.

### 3. Expose onboarding hints in login completion notifications — [#36635](https://github.com/openai/codex/pull/36635) ✅ Closed
Allows the `.onboarding_entrypoint=life_sciences` suffix on valid OAuth states and returns parsed callback metadata from the login server without exposing the suffix in responses.

### 4. Bound executor-controlled HTTP response buffering — [#31781](https://github.com/openai/codex/pull/31781) 🔄 Open
Mitigates a trust-boundary issue where the untrusted remote exec-server could cause app-server to retain very large response data before the existing 256-frame backpressure limit is hit. Code-reviewed.

### 5. Update models.json — [#31817](https://github.com/openai/codex/pull/31817) 🔄 Open
Automated model registry update (ongoing).

---

## Feature Request Trends

- **Cost/credit controls:** The strongest signal across issues—service tier support, visible usage limits, and token-waste reduction are recurring themes. Users want transparency and control over how fast their allowances burn.
- **UI/UX polish:** Tabbed chat sessions, timestamps on messages, and Max reasoning effort parity between Desktop and VS Code extension are consistently requested.
- **Autonomous goal resumption:** A new request [#36668](https://github.com/openai/codex/issues/36668) proposes a controlled resume/active transition for paused goals with audit history, signaling growing demand for reliable long-running agent workflows.

---

## Developer Pain Points

1. **Token waste from polling loops** — Multiple independent reports (#13733, #35259, #22411, #36665, #36664) describe the same root problem: Codex re-enters the model during wait/poll cycles, burning full-history API calls. Several users report consuming entire weekly allowances in under 6 hours.

2. **Windows app stability** — A cluster of new Windows-specific bugs appeared today: session resumption failures after encrypted tool-output decode errors (#36662), migration breaking project-to-thread associations (#36663), and execution-bridge crashes on simple commands (#36574, #35606). The unified ChatGPT Desktop migration is introducing friction.

3. **macOS Diff extension crash** — The most-upvoted open issue (#35058) with no resolution in ~10 days; the feature is completely broken on Apple Silicon.

4. **Sandbox configuration regressions** — macOS permission profile activation causes silent SIGABRT in sandboxed exec (#35437), blocking the only opt-out path for protected files like `.git`.

5. **Model scope adherence** — Two nearly identical reports (#36666, #36667) describe the agent repeatedly ignoring explicit one-item task scope and performing destructive out-of-scope changes, despite corrections being persisted as hooks.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026‑08‑03

## 1. Today’s Highlights
A new nightly build (`v0.55.0-nightly.20260803`) was released, accompanied by a security‑focused fix for OAuth token exchange on headless VPSes. The community’s attention remains squarely on agent reliability—particularly sub‑agent recovery, generalist‑agent hangs, and browser‑agent failures on Wayland—while a growing set of issues highlights the need for more deterministic tool‑selection and memory‑system hygiene.

## 2. Releases
- **v0.55.0‑nightly.20260803.gf47d6c6f7** – Automated nightly bump.  
  [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.55.0-nightly.20260802.gf47d6c6f7...v0.55.0-nightly.20260803.gf47d6c6f7)

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Sub‑agents incorrectly signal completion, masking turn‑limit interruptions and leaving the main agent in an inconsistent state. | 12 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | The generalist sub‑agent can freeze indefinitely on simple tasks (e.g., folder creation), forcing manual cancellation. | 8 comments, 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model’s bash affinity via Zero‑Dependency OS Sandboxing | Proposes a security‑preserving way to let the model use its native POSIX‑tool proficiency without compromising user UX. | 8 comments, 1 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component‑level evaluations | Tracks progress on behavioral evals (76 tests generated) to ensure consistent agent behavior across the 6 supported Gemini models. | 7 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess AST‑aware file reads, search, and mapping | Investigates whether AST‑based tools can reduce token noise and improve navigation precision. | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub‑agents enough | Anecdotal report that the model rarely invokes custom skills/sub‑agents unless explicitly prompted. | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory from retrying low‑signal sessions indefinitely | Low‑signal memory sessions are never marked processed, causing repeated, wasteful retrieval. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | Addresses privacy concerns by redacting secrets before they enter model context and trimming verbose skill logs. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution gets stuck “Waiting input” | Simple CLI commands complete but the agent remains in an “Awaiting user input” state, blocking further interaction. | 4 comments, 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser_agent resilience | Proposes automatic session takeover and lock recovery for persistent browser profiles. | 4 comments |

## 4. Key PR Progress
| # | Title | Summary |
|---|-------|---------|
| [#28446](https://github.com/google-gemini/gemini-cli/pull/28446) | `fix(auth): use native fetch for OAuth token exchange` | Replaces the default HTTP client with Node’s native `fetch` to resolve “Premature close” errors on headless VPSes during login. |
| [#28447](https://github.com/google-gemini/gemini-cli/pull/28447) | `docs(get-started): add Windows PowerShell troubleshooting` | Adds missing PowerShell‑specific guidance to the installation docs after reports of `gemini` command failures on Windows. |
| [#28638](https://github.com/google-gemini/gemini-cli/pull/28638) | `chore/release: bump version to 0.55.0-nightly.20260803` | Automated nightly version bump. |
| [#28637](https://github.com/google-gemini/gemini-cli/pull/28637) | `chore(deps): bump js-yaml 4.1.1 → 5.2.2` | Updates YAML parser to address security and compatibility fixes. |
| [#28635](https://github.com/google-gemini/gemini-cli/pull/28635) | `chore(deps): bump undici 7.10.0 → 8.9.0` | Upgrades the HTTP client; includes high‑severity security fixes. |
| [#28634](https://github.com/google-gemini/gemini-cli/pull/28634) | `chore(deps): bump chalk 4.1.2 → 6.0.0` | Updates the color library; requires Node.js 22+. |
| [#28632](https://github.com/google-gemini/gemini-cli/pull/28632) | `chore(deps-dev): bump eslint 9.24.0 → 10.8.0` | Major linter upgrade with new features and rule changes. |
| [#28631](https://github.com/google-gemini/gemini-cli/pull/28631) | `chore(deps): bump @google/genai 1.30.0 → 2.13.0` | Significant jump in the underlying GenAI SDK, bringing new model capabilities. |
| [#28624](https://github.com/google-gemini/gemini-cli/pull/28624) | `fix(core): prevent boolean thought parts leaking as [Thought: true]` | Fixes a display bug where internal boolean thought flags were rendered as literal text in the UI. |
| [#28526](https://github.com/google-gemini/gemini-cli/pull/28526) | `fix(vscode-ide-companion): stop leaking disposables` | Corrects a parenthesis typo that caused two disposables (`gemini.diff.accept` and `onDidChangeWorkspaceFolders`) to be retained, resolving a memory‑leak report. |

## 5. Feature Request Trends
- **AST‑aware tooling** – Multiple issues (#22745, #22746) explore using syntax‑tree‑aware reads and searches to reduce token waste and improve navigation precision.
- **Zero‑dependency OS sandboxing** – #19873 proposes a sandbox layer that lets the model leverage its native bash proficiency without external dependencies.
- **Sub‑agent visibility & control** – Requests for clearer sub‑agent trajectory sharing (#22598), better bug‑report context (#21763), and more reliable invocation of skills/sub‑agents (#21968).
- **Self‑awareness** – #21432 asks that the CLI accurately understand and communicate its own flags, hotkeys, and self‑execution mechanics.
- **Memory‑system hygiene** – Several issues (#26522, #26523, #26516) target Auto Memory’s retry loops, invalid‑patch handling, and overall quality.

## 6. Developer Pain Points
- **Agent reliability** – Recurring hangs (generalist agent #21409, shell command stuck #25166), incorrect termination signals (sub‑agent MAX_TURNS #22323), and crashes during output hooks (#22186).
- **Browser‑agent fragility** – Failures on Wayland (#21983), ignoring `settings.json` overrides (#22267), and lack of automatic session recovery (#22232).
- **Sub‑agent permission & invocation** – Sub‑agents running without explicit permission since v0.33.0 (#22093) and the model under‑utilizing custom skills/sub‑agents (#21968).
- **Memory‑system bugs** – Low‑signal sessions retried indefinitely (#26522), invalid patches silently skipped (#26523), and insufficient redaction of secrets in logs (#26525).
- **Environment‑specific issues** – OAuth token‑exchange failures on headless VPSes (#28440, addressed in #28446) and Windows PowerShell installation quirks.

---
*Generated by Agnes (Sapiens AI) from GitHub data for google‑gemini/gemini‑cli on 2026‑08‑03.*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-03

## 1. Today's Highlights

Today's activity centers on **11 open issues** with no new releases or pull requests landed in the past 24 hours. The most pressing concerns involve **autopilot session state not persisting on resume** (#4329), a **model availability mismatch** where `gpt-5.6-luna` is advertised but unreachable via `/chat/completions` (#4337), and **input cancellation being ignored in autopilot mode** (#4336). These three issues form a cluster around agent-state reliability that is drawing developer attention.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4337](https://github.com/github/copilot-cli/issues/4337) | `gpt-5.6-luna` advertised but not accessible via `/chat/completions` | Breaks MoA/aggregator tooling that depends on the OpenAI-compatible surface. Model listing and execution endpoints are out of sync, a sign of potential release-gap regressions. | New, 0 comments. |
| [#4336](https://github.com/github/copilot-cli/issues/4336) | Cancelled user input delivered to the agent as a valid turn | In autopilot mode, a cancelled input retains its original timestamp and reappears bundled into a later message — silently polluting agent context. | New, 0 comments. |
| [#4329](https://github.com/github/copilot-cli/issues/4329) | Autopilot not enabled when resuming a session | Statusline shows autopilot as on, but approval-gated actions still fail on session resume. A state-persistence bug directly impacting power users. | New, 0 comments. |
| [#4335](https://github.com/github/copilot-cli/issues/4335) | `toolCall.title` hides shell command in ACP client modals | In Agent Context Protocol mode, titles show high-level summaries (e.g. *"Search whole monorepo for double-entry"*) instead of the actual command, undermining human-in-the-loop approval workflows. | New, 0 comments. |
| [#4334](https://github.com/github/copilot-cli/issues/4334) | Stashed prompt discarded on session switch | `Ctrl+S` stash is lost when switching sessions; `Ctrl+S` pop restores nothing. A data-loss bug for users who rely on input staging. | New, 0 comments. |
| [#4202](https://github.com/github/copilot-cli/issues/4202) | Built-in `view` reports "Path does not exist" in 1.0.73 | Regression introduced in 1.0.72: the `view` tool fails on existing text files. Isolated Vally/Copilot SDK probe succeeds with 1.0.71, confirming a CLI-side regression. 3 comments. | 0 👍 |
| [#4328](https://github.com/github/copilot-cli/issues/4328) | `Ctrl+H` misinterpreted as `Ctrl+Backspace` under WSL2 | `WT_SESSION` leaks from Windows Terminal, causing the editor to treat "delete previous character" as "delete previous word." Affects WSL2 + Windows Terminal users. | New, 0 comments. |
| [#4292](https://github.com/github/copilot-cli/issues/4292) | Colors completely off in tmux with light theme | Light-theme rendering is broken inside tmux but correct outside it. Terminal multiplexer color passthrough is a known friction point. | 0 comments. |
| [#4332](https://github.com/github/copilot-cli/issues/4332) | No way to silence "Memory is disabled" notice | Every new session prints `Memory is disabled. Use /memory on to re-enable.` even when the user explicitly set `"memory": false`. No setting suppresses it. | New, 0 comments. |
| [#4333](https://github.com/github/copilot-cli/issues/4333) | Poor network connection | User reports unstable network conditions affecting CLI performance. Vague, but reflects a recurring infrastructure concern. | New, 0 comments. |

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

## 5. Feature Request Trends

- **Session state persistence**: Issues #4329 and #4334 both stem from the same root concern — the CLI does not reliably preserve agent state (autopilot mode, stashed input) across session switches and resumes.
- **User-control over UI noise**: Issue #4332 highlights a desire for granular control over startup/session messages, especially for users who have intentionally disabled features like memory.
- **ACP / editor integration fidelity**: Issue #4335 points to a demand for accurate, actionable tool-call metadata in host-editor approval modals — developers want to see the real command, not a summary.
- **Model API consistency**: Issue #4337 underscores a request for parity between the `/models` listing and the `/chat/completions` execution surface, especially as new models are rolled out.

## 6. Developer Pain Points

1. **Autopilot reliability** — The cluster of #4336 (cancelled input not discarded), #4329 (autopilot state lost on resume), and #4335 (unclear tool-call titles) signals that autopilot mode, while popular, has fragile state management and insufficient user feedback. Developers using autopilot report silent failures rather than clear errors.

2. **Regression awareness** — Issues #4202 (view tool broken since 1.0.72) and #4328 (keybinding regression under WSL2) suggest that version bumping introduces regressions that surface only after users adopt the new version. The community would benefit from clearer change logs and pre-release validation.

3. **Terminal-environment compatibility** — Issues #4292 (tmux colors) and #4328 (WSL2 keybinding leak) reflect ongoing friction between the CLI's terminal rendering/input layer and common developer environments (tmux, WSL2, Windows Terminal). These are high-frequency pain points for power-user setups.

4. **Configuration rigidity** — Issue #4332 shows that once a user opts out of a feature (memory), they still receive informational output they cannot suppress. The community wants settings to control *all* surface-level behavior, not just functional behavior.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-03

## 1. Today's Highlights

No new releases were published in the last 24 hours. The community is driving two major feature requests from author **CatKang** — persistent cross-session memory and remote session control — both of which remain open with strong engagement. Meanwhile, a new issue surfaced around batch resilience failures in swarm mode, and a streaming Monitor tool PR has been closed after review.

## 2. Releases

None in the last 24 hours.

## 3. Hot Issues

**#1282 — Remote Control: Continue local sessions from any device** ⭐ 24 👍
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1282)
Arguably the most upvoted open issue. Enables continuing a local Kimi Code CLI session from a phone, tablet, or browser — critical for developers who work across multiple devices or need to intervene while away from their desk. The 24 upvotes signal strong demand for workflow continuity.

**#1283 — Memory System: Persistent context across sessions**
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)
Proposes a two-tier memory system (AI-managed automatic notes + user-defined manual instructions via `c-` commands) so the CLI retains project patterns and preferences between invocations. Currently 0 upvotes but 14 comments, indicating active discussion around design and scope.

**#2579 — External wake channel for interactive sessions**
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2579)
A niche but clever request: an `inotifywait`-based mechanism to wake interactive TUI sessions when external agents drop Markdown messages into an inbox directory. Addresses multi-agent coordination on the same or SSH-connected machines. Fresh (created today), 0 comments so far.

**#2578 — Swarm batch 403/timeout: partial work lost, resume re-spends tokens**
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2578)
A reliability concern for swarm-mode parallel subagents: when a quota limit (HTTP 403) or fixed timeout kills subagents mid-batch, workspaces are left in a broken intermediate state and resumptions waste tokens re-processing completed work. Bilingual title suggests international user impact. Zero comments — likely needs maintainer attention.

## 4. Key PR Progress

**#2471 — feat(tools): add Monitor tool for per-line stdout streaming** [CLOSED]
[GitHub Link](https://github.com/MoonshotAI/kimi-cli/pull/2471)
Proposed a **Monitor** tool as a streaming counterpart to the existing background tool, enabling per-line stdout output for long-running commands. The PR was closed on 2026-08-02 after ~40 days of open review. No tracking issue was filed upstream, suggesting the maintainers may have declined the approach or deferred it.

## 5. Feature Request Trends

Three clear direction signals emerge from the current issue pool:

- **Session continuity** — Both #1282 (remote control) and #1283 (persistent memory) reflect a desire for Kimi Code CLI to behave more like a persistent workspace rather than a stateless REPL.
- **Multi-agent / multi-device orchestration** — #2579's wake-channel request and #1282's cross-device control point to a growing ecosystem of users running Kimi Code CLI alongside other agents or across devices.
- **Batch/swerm resilience** — #2578 highlights that parallel subagent workflows need better fault tolerance, checkpointing, and token-efficient resume semantics.

## 6. Developer Pain Points

- **Token waste on partial failures** — Swarm batch interruptions (403s, timeouts) leave workspaces half-written and force token-redundant re-execution on resume (#2578).
- **No cross-session state** — Users repeatedly lose project context between CLI invocations, driving the memory system request (#1283).
- **Device-lockated workflows** — Interactive CLI sessions cannot be accessed remotely, forcing developers to stay at their desk (#1282).
- **Multi-agent coordination gaps** — No built-in mechanism for external processes or sibling agents to signal or interact with a running Kimi Code CLI session (#2579).

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-03

## 1. Today's Highlights

No new releases were published in the past 24 hours. The most significant development is the landing of the long-requested `chat.model` plugin hook (PR #40188), enabling per-request model routing, while multiple persistence and input-handling fixes are in review. A new open issue (#40206) reports that **grok-4.5 on opencode go** has been returning HTTP 500 errors since August 2nd.

---

## 2. Releases

None in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#26338](https://github.com/anomalyco/opencode/issues/26338) | Add CommandCode as a Provider | Requests native authentication support for CommandCode — the most upvoted issue this cycle with **30 👍**. | 🔥 30 |
| [#18793](https://github.com/anomalyco/opencode/issues/18793) | `chat.model` plugin hook for dynamic model routing | Enables plugins to swap the active `{provider, model}` per-request before LLM calls; directly addresses agent-based routing needs. | 👍 6 |
| [#20269](https://github.com/anomalyco/opencode/issues/20269) | Session title generation silently failing since v1.3.3 | A stealth regression — every new session keeps the default timestamped title because an `effort` parameter leaks into the small-model call. | 👍 3 |
| [#12800](https://github.com/anomalyco/opencode/issues/12800) | macOS-friendly clipboard fallback | The CLI clipboard helper relies on `xclip`, which macOS lacks; a `pbcopy` fallback is needed for parity. | 👍 8 |
| [#24217](https://github.com/anomalyco/opencode/issues/24217) | TUI double-ESC loop & desktop stop button failure | Windows users report the TUI getting stuck in a loop on double-ESC and the desktop stop button failing to interrupt active sessions with DeepSeek V4. | 👍 1 |
| [#29619](https://github.com/anomalyco/opencode/issues/29619) | Kimi K2.6 `reasoning_content` missing in tool-call messages | Moonshot AI's K2.6 causes tool-call failures when thinking is enabled — a provider-specific bug affecting a growing user base. | — |
| [#18844](https://github.com/anomalyco/opencode/issues/18844) | Dynamic model routing based on prompt complexity | Complements #18793; users want lightweight models for simple prompts and heavy models for complex refactors, routed automatically. | — |
| [#22588](https://github.com/anomalyco/opencode/issues/22588) | TUI message list doesn't update for cross-instance agent messages | The agent-comms plugin works correctly, but the TUI conversation view is stale until restart — a real-time update gap. | — |
| [#24286](https://github.com/anomalyco/opencode/issues/24286) | Web UI shows lower version than CLI after update | After `opencode upgrade`, the web UI version number lags behind the CLI, causing confusion about which version is running. | — |
| [#30136](https://github.com/anomalyco/opencode/issues/30136) | Permission prompt loop | Users stuck in a permission-dialog loop where confirming or pressing ESC neither grants nor dismisses the prompt. | 👍 2 |

---

## 4. Key PR Progress

| # | PR | Description |
|---|-----|------------|
| [#40188](https://github.com/anomalyco/opencode/pull/40188) | `feat(plugin): add request-scoped chat.model hook` | **Closes #18793.** Fires before provider/model/auth resolution, letting a plugin replace the model for a single request. Also partially addresses #24006. |
| [#40207](https://github.com/anomalyco/opencode/pull/40207) | `fix(app): persist prompt drafts without base64` | Moves drafts/history to a dedicated SQLite WAL store with content-addressed BLOBs; persists image *references* instead of embedding base64, reducing storage bloat. |
| [#40197](https://github.com/anomalyco/opencode/pull/40197) | `fix(app): eliminate persistence write amplification` | Replaces setter-coupled `makePersisted` writes with a shared repository and a 500 ms checkpoint deadline; keeps prompt drafts/history reference-only, materializing base64 only on read. |
| [#40199](https://github.com/anomalyco/opencode/pull/40199) | `fix(opencode): handle removed OpenAI OAuth auth` | Guards against mid-session OAuth removal by reading auth state before applying mutations and passes requests through unchanged when auth was revoked. Includes a regression test. |
| [#40198](https://github.com/anomalyco/opencode/pull/40198) | `fix(opencode): match canonically equivalent Unicode in patches` | **Closes #31651.** Adds a canonical Unicode-equivalence pass to `seekSequence()` so patch verification no longer fails on NFC/NFD-normalized file content. |
| [#40163](https://github.com/anomalyco/opencode/pull/40163) | `fix(tui): let prompt Down arrow reach end of text` | **Closes #40161.** Fixes cursor offset calculation in the prompt textarea so the Down arrow can navigate to the actual end of multi-line text. |
| [#40125](https://github.com/anomalyco/opencode/pull/40125) | `feat(opencode): Allow per-MCP-server trust configuration` | **Closes #40111.** Adds fine-grained trust controls so each MCP server can be individually whitelisted, addressing long-standing security concerns (#23506, #14696). |
| [#40202](https://github.com/anomalyco/opencode/pull/40202) | `fix(app): search every known project in the open project dialog` | **Closes #39142.** The Open Project dialog now searches across all known projects instead of limiting results to the five most recent. |
| [#40030](https://github.com/anomalyco/opencode/pull/40030) | `feat(tui): add spinnerVerbs config` | **Closes #19401.** Users can now customize the verb text displayed next to the TUI spinner via `spinner_verbs` in `.opencode/tui.json`. |
| [#39994](https://github.com/anomalyco/opencode/pull/39994) | `feat: add OPENCODE_AIRGAP to disable automatic internet access` | **Addresses #18233, #37888.** A single kill-switch env var (`OPENCODE_AIRGAP=1`) that blocks all automatic internet access for intranet and air-gapped deployments. |

---

## 5. Feature Request Trends

1. **Dynamic model routing** — Multiple issues (#18793, #18844, #24006) converge on a single theme: users want plugins and the core to route requests to different models based on context, complexity, or prompt content, rather than a static global selection. The `chat.model` hook (now in PR #40188) is the core enabler.

2. **Provider ecosystem expansion** — Request for CommandCode support (#26338, 30 👍) and the ability for custom providers to reference official Models.dev definitions (#30519) show strong demand for broader provider coverage and standardization.

3. **Configurability & customization** — Configurable search paths for commands/agents (#14240), custom spinner text (#40030), and per-MCP-server trust (#40125) reflect a trend toward granular user control over behavior and security.

4. **Offline/air-gapped deployment** — The `OPENCODE_AIRGAP` feature (#39994) and the earlier request for offline-first behavior indicate a growing niche of enterprise and security-conscious users.

5. **Desktop UX parity** — Multiple desktop-specific complaints (session rename #16677, project edit persistence #24744, session review resize #30560, Markdown heading hierarchy #16046) point to an ongoing push to bring the desktop experience up to CLI parity.

---

## 6. Developer Pain Points

- **Persistence performance** — Write amplification from the old `makePersisted` pattern and base64-embedded images were chronic issues. The two adjacent PRs (#40197, #40207) show the team is actively addressing this, but the complexity suggests it will remain a friction point.

- **Clipboard & input on non-Linux platforms** — macOS clipboard fallback (#12800) and Windows Ctrl+C/V failures in cmd (#12595) are recurring cross-platform input issues that affect workflow for non-Linux users.

- **Silent regressions** — The session title generation bug (#20269) silently broke for months without error messages, making it hard for users and maintainers to diagnose. This pattern of silent failures is a recurring quality concern.

- **Interrupt/handling reliability** — ESC loop (#24217) and permission prompt loop (#30136) both involve the UI getting stuck in unresponsive states, suggesting the event-handling layer has edge-case gaps under interrupt conditions.

- **Version synchronization** — The web UI showing a stale version after CLI upgrade (#24286) indicates a deployment/sync gap that creates confusion and complicates troubleshooting.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-03

## Today's Highlights

The day's activity centered on two major themes: fixing a persistent auto-compaction bug that allowed context to balloon past 100% without triggering compaction (#6879), and resolving a wave of connectivity hangs — including an IPv6 blackhole issue (#7504) and a missing timeout on the post-login catalog refresh (#7505, #7113). A batch of provider additions (DeepInfra, LLM Gateway) and a new in-memory session backend also advanced in PRs.

---

## Releases

No new releases published in the last 24 hours.

---

## Hot Issues

| # | Title | Author | Comments | 👍 | Status |
|---|-------|--------|----------|----|--------|
| [#6879](https://github.com/earendil-works/pi/issues/6879) | auto-compaction never triggers after context grows past 100% | alexanderkreidich | 10 | 10 | OPEN |
| [#7062](https://github.com/earendil-works/pi/issues/7062) | fix(openai-completions): handle array content and missing finish_reason | TomeHirata | 6 | 0 | OPEN |
| [#7113](https://github.com/earendil-works/pi/issues/7113) | TUI freezes after entering API key when pi.dev model catalog is unreachable | Simonjks-dev | 4 | 0 | OPEN |
| [#7315](https://github.com/earendil-works/pi/issues/7315) | Fireworks requests sometimes fail instantly with "Request timed out." | ZeR020 | 4 | 0 | CLOSED |
| [#7486](https://github.com/earendil-works/pi/issues/7486) | Hardware cursor jumps in WezTerm when showHardwareCursor is enabled | fyeeme | 3 | 0 | CLOSED |
| [#7323](https://github.com/earendil-works/pi/issues/7323) | `pi update --models` fails the entire refresh on a transient catalog stall | vinayakravi | 3 | 0 | CLOSED |
| [#7413](https://github.com/earendil-works/pi/issues/7413) | Compaction fails on GitHub Copilot GHE.com enterprise accounts | timnee | 3 | 0 | CLOSED |
| [#7484](https://github.com/earendil-works/pi/issues/7484) | Extension-sent slash commands never execute | Agnostion | 2 | 0 | CLOSED |
| [#7321](https://github.com/earendil-works/pi/issues/7321) | Multi-line paste broken on terminals without bracketed paste support | 6mad | 2 | 1 | OPEN |
| [#7481](https://github.com/earendil-works/pi/issues/7481) | WezTerm inline kitty images degrade to a one-row sliver | nothankyouzzz | 2 | 0 | CLOSED |

**Why they matter:**

- **#6879** — The most upvoted open issue. Long-running agentic turns can push context well beyond the compaction threshold with no automatic recovery, risking API quota exhaustion. 10 thumbs-up signals strong community concern.
- **#7062** — A provider-compatibility bug affecting Databricks models (Qwen3, gpt-oss) that return typed array content deltas, causing JSON parsing errors in streaming responses.
- **#7113** — Post-login hangs for ~5 minutes when `pi.dev` is unreachable. Directly impacts onboarding UX; two related issues (#7504, #7505) filed the same day broaden the scope.
- **#7315** — Intermittent Fireworks timeouts with empty content and zero token usage, suggesting failures before the HTTP body is received.
- **#7484** — Extension tools sending `/command` strings via `sendUserMessage` silently bypass command dispatch and deliver raw text to the LLM, contradicting documentation.

---

## Key PR Progress

| # | Title | Author | Status |
|---|-------|--------|--------|
| [#7506](https://github.com/earendil-works/pi/pull/7506) | docs(agent): Add Chinese JSDoc comments to all agent source | WillfordZhan | CLOSED |
| [#7503](https://github.com/earendil-works/pi/pull/7503) | feat(agent): Add experimental in-memory sessions | christianklotz | OPEN |
| [#7501](https://github.com/earendil-works/pi/pull/7501) | Add DeepInfra provider | embeddedt | CLOSED |
| [#7498](https://github.com/earendil-works/pi/pull/7498) | fix(coding-agent): Defer idle compaction until next prompt | ogulcancelik | OPEN |
| [#7459](https://github.com/earendil-works/pi/pull/7459) | feat(coding-agent): Compose experimental CLI commands | christianklotz | CLOSED |
| [#7480](https://github.com/earendil-works/pi/pull/7480) | feat(ai): Add LLM Gateway provider with API key and OAuth | RATCHAW | CLOSED |
| [#7496](https://github.com/earendil-works/pi/pull/7496) | feat: Add cycle execution duration and /copy cycle command | mahernandezg | CLOSED |
| [#7494](https://github.com/earendil-works/pi/pull/7494) | fix(ai): Preserve Gemini 3 tool call IDs | muyiyr | OPEN |
| [#7493](https://github.com/earendil-works/pi/pull/7493) | Set AI_AGENT for child process attribution | renaudhartert-db | OPEN |
| [#7482](https://github.com/earendil-works/pi/pull/7482) | fix(tui): Prefer iTerm2 inline images over kitty on WezTerm | nothankyouzzz | CLOSED |

**Highlights:**

- **#7503** introduces an experimental in-memory session backend with full entry/lane/fact/query/log APIs, paving the way for transient or test sessions.
- **#7501** and **#7480** add DeepInfra and LLM Gateway as built-in providers, both following the OpenAI completions protocol.
- **#7498** addresses #6879 by deferring idle compaction to the next prompt, avoiding unnecessary token-wasting compactions on models with large context windows.
- **#7494** fixes Gemini 3 tool call ID handling, ensuring history replay works correctly for Google's latest models.
- **#7493** sets the `AI_AGENT=pi` environment variable for child processes, adopting an emerging cross-agent convention for process attribution.
- **#7482** resolves the WezTerm image degradation bug (#7481) by preferring iTerm2 inline images over kitty on WezTerm.

---

## Feature Request Trends

1. **In-memory / transient sessions** — #7503 and the related session storage refactors (#7478, #7455, #7396) show a push toward flexible session backends (in-memory, server-side JSONL, faceted repositories).
2. **Provider expansion** — DeepInfra (#7501), LLM Gateway (#7480), and DeepSeek on OpenRouter (#7476) all landed recently; the community continues requesting new OpenAI-compatible providers.
3. **Thinking level controls** — #7487 requests the ability to select and persist per-model thinking level (`provider/id:level`) via `/scoped-models`.
4. **Tool & command extensibility** — #7500 proposes `askWithFrozenContext()` for plugins to query the LLM without altering active context; #7484 highlights broken extension→slash-command handoff.
5. **CLI ergonomics** — #7475 requests `--exclude-extensions` for per-run extension gating; #7477 proposes a single-line footer to reclaim vertical space.

---

## Developer Pain Points

- **Context compaction not triggering reliably** (#6879, #7413, #7492) — Three distinct issues converge on compaction being the most frustrating area: it fails to fire at thresholds, breaks on enterprise Copilot accounts, and cancellation reasons are opaque.
- **Network connectivity hangs** (#7113, #7504, #7505, #7323) — A recurring theme: missing timeouts on catalog refreshes, IPv6 blackholes stalling for ~5 minutes, and single-retry model updates failing the entire `pi update --models` command.
- **Terminal rendering quirks** (#7486, #7490, #7481) — WezTerm-specific bugs (cursor jumping, IME ghosting, inline image degradation) appear frequently and suggest the terminal abstraction layer needs more robust capability detection.
- **Bracketed paste & input** (#7321) — Multi-line paste still broken on terminals like Termux that lack proper bracketed-paste support.
- **Tool schema duplication** (#7485) — Every request serializes tool schemas twice (text prompt snippet + JSON tools param), with no opt-out for models with native tool calling, inflating context usage.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026‑08‑03

## 1. Today’s Highlights
A new nightly build (`v0.21.3‑nightly.20260803.e1e5b42ce`) shipped with a complete TUI keyboard‑shortcut reference and a fix for history‑pagination blocking. Community attention is concentrated on session‑integrity bugs (duplicate tool‑call IDs, transcript corruption) and on several high‑impact features: an email channel, Maven‑scoped review, and an experimental Plan‑&‑Review workflow for daemon sessions.

---

## 2. Releases
**v0.21.3‑nightly.20260803.e1e5b42ce**  
- **docs:** Complete TUI keyboard‑shortcut reference  
- **fix:** Unblock history pagination on open session  
[GitHub Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.3-nightly.20260803.e1e5b42ce)

---

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [#4156](https://github.com/QwenLM/qwen-code/issues/4156) | `qwen --serve` TUI + in‑process HTTP daemon | Unlocks Mode‑A (TUI + daemon) that is currently impossible; would let local users run a daemon while keeping a TUI session. | 7 comments · proposed 3‑phase plan; marked **CLOSED** (likely implemented). |
| [#7306](https://github.com/QwenLM/qwen-code/issues/7306) | Harden tool‑output budgeting & artifact lifecycle | Core correctness & observability for long‑running ACP sessions; Phase 1 is complete. | 5 comments; active development discussion. |
| [#8123](https://github.com/QwenLM/qwen-code/issues/8123) | Desktop client cannot reference correct file | Desktop `@`‑mention search fails to locate existing Java files; blocks daily development on Windows/macOS. | 5 comments; reported as a bug in v0.5.5. |
| [#8376](https://github.com/QwenLM/qwen-code/issues/8376) | Change process name from `node.exe` to `qwen.exe` | External tooling (task managers, firewalls) cannot reliably identify Qwen Code; affects Windows users. | 4 comments; feature request with clear use‑case. |
| [#8281](https://github.com/QwenLM/qwen-code/issues/8281) | Add Email channel with IMAP/SMTP support | Would enable asynchronous, mailbox‑based agent interaction—expanding deployment scenarios beyond HTTP/CLI. | 4 comments; provider‑neutral design requested. |
| [#8389](https://github.com/QwenLM/qwen-code/issues/8389) | Experimental Plan & Review workflow for daemon sessions | Builds on earlier DAG‑visualization work; aims to make plan‑approval safe and opt‑in for daemon users. | 3 comments; status **in‑progress**. |
| [#8382](https://github.com/QwenLM/qwen-code/issues/8382) | Duplicate provider tool call id | Causes tool‑call failures and “not recorded” errors, breaking session continuity. | 3 comments; reproducible in production‑like setups. |
| [#8411](https://github.com/QwenLM/qwen-code/issues/8411) | Caller‑supplied session IDs not coordinated across daemon transports | Session‑ID uniqueness is only enforced per REST route, not across workspaces/transports—leads to collisions. | 2 comments; open bug. |
| [#8398](https://github.com/QwenLM/qwen-code/issues/8398) | `isAbortError` does not recognize OpenAI SDK’s `APIUserAbortError` | User‑cancel actions are mis‑classified as errors, corrupting transcript and abort semantics. | 2 comments; critical for OpenAI‑compatible providers. |
| [#7164](https://github.com/QwenLM/qwen-code/issues/7164) | Concurrent session writers fork transcript history | Two processes restoring the same session append to different in‑memory tails, causing divergent transcripts on restart. | 2 comments; P1 session‑management bug. |

---

## 4. Key PR Progress
| # | Title | Summary |
|---|-------|---------|
| [#8418](https://github.com/QwenLM/qwen-code/pull/8418) | Share compression caches with OpenAI providers | Extends prefix‑preserving cache‑sharing (previously DashScope‑only) to all OpenAI‑compatible endpoints. |
| [#8274](https://github.com/QwenLM/qwen-code/pull/8274) | Fork from any conversation | Allows session branching from any visible Assistant message, not just the latest active state. |
| [#8416](https://github.com/QwenLM/qwen-code/pull/8416) | Scope `/review` to Maven modules | Brings Maven multi‑module monorepos to parity with npm workspaces for deterministic build‑and‑test. |
| [#8171](https://github.com/QwenLM/qwen-code/pull/8171) | Configure background‑agent turn limits | Adds a shared `memory.agentMaxTurns` setting for extraction, dream, remember, and skill‑review agents. |
| [#8414](https://github.com/QwenLM/qwen-code/pull/8414) | Recover complete turns after live‑journal truncation | Makes bounded‑journal truncation precise and recoverable without altering the 10k‑event / 8 MiB limits. |
| [#8381](https://github.com/QwenLM/qwen-code/pull/8381) | Read Windows smoke log from `LocalAppData` | Fixes the packaged‑app smoke test to use the correct Tauri log path on Windows. |
| [#8332](https://github.com/QwenLM/qwen-code/pull/8332) | Audio bridge for attachments | Transcribes audio attachments through a batch voice model when the primary model lacks audio support. |
| [#8125](https://github.com/QwenLM/qwen-code/pull/8125) | External tool‑guard provider for `qwen serve` | Adds an opt‑in pre‑execution policy that requires an authenticated handshake with a loopback HTTP(S) provider. |
| [#8413](https://github.com/QwenLM/qwen-code/pull/8413) | Keep pending background agents active in Web Shell | Ensures a turn stays expanded while any background sub‑agent is still running. |
| [#8393](https://github.com/QwenLM/qwen-code/pull/8393) | Bind plan approval to its Todo revision | Guarantees that `exit_plan_mode` approvals are validated against the exact Todo plan ID and source tool‑call ID. |

---

## 5. Feature‑Request Trends
- **Multi‑channel integrations:** Email (IMAP/SMTP) and safe cloud‑deployment pipelines are the most‑requested new channels.
- **Session & workflow controls:** Plan‑&‑Review, background‑agent turn limits, and reliable session‑ID coordination show demand for finer‑grained, audit‑friendly automation.
- **UI/UX polish:** Image drag‑and‑drop in Web Shell, better theming, and Windows process‑name identification address daily‑use friction.
- **Cross‑platform parity:** Maven‑workspace support and voice‑ASR allowlist alignment extend Qwen Code beyond Node‑centric stacks.

---

## 6. Developer Pain Points
- **Transcript corruption & duplicate IDs:** Several high‑visibility bugs (`#8382`, `#7164`, `#8398`, `#8411`) indicate that session‑state management remains fragile under concurrency or provider‑error conditions.
- **Platform‑specific quirks:** Windows process identification (`#8376`), flickering output in ConEmu/Cmder (`#8385`), and desktop‑client file‑reference failures (`#8123`) highlight gaps in cross‑platform testing.
- **CI instability:** Repeated E2E and merge‑queue failures (`#8333`, `#8375`) suggest that test reliability and runner‑fleet maintenance need ongoing attention.
- **Integration gaps:** Users are asking for more channels (email, cloud deployment) and for existing ones (voice ASR, web‑shell image drops) to reach feature parity with the CLI/TUI.

---

*Data sourced from [github.com/QwenLM/qwen‑code](https://github.com/Qwen

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-03

## 1. Today's Highlights

The v0.9.4 release train (#5135) has landed on `main` with 77 commits, and an immediate hardening stack (R1/R3) is already chaining onto it to address critical runtime, security, and fleet-config issues discovered during dogfooding. A cluster of v0.9.4 release-blocker bugs was filed today covering exec-policy bypasses, MCP tool-call filtering gaps, state migration non-idempotency, and workflow gate handoff leaks.

## 2. Releases

No new releases in the last 24 hours. The v0.9.4 integration train (#5135) was merged today (77 commits ahead of main), superseding the prior source candidate from 2026-08-01.

## 3. Hot Issues

| # | Title | Comments | Why It Matters |
|---|-------|----------|----------------|
| [#2934](https://github.com/Hmbown/CodeWhale/issues/2934) | Sidebar sessions panel with auto-resume | 12 | Long-requested UX improvement; users currently rely on `Ctrl+R` popup or CLI flags to browse sessions — a persistent sidebar would reduce friction significantly. |
| [#998](https://github.com/Hmbown/CodeWhale/issues/998) | Text display truncated, no hover tooltip | 11 | 11 comments signal strong pain; Chinese-language users report truncated prompt output with no way to view the full text. |
| [#689](https://github.com/Hmbown/CodeWhale/issues/689) | `deepseek doctor` passes but `deepseek run` fails | 10 | Diagnostic tool reports healthy config while the runtime is non-functional — a trust-gap bug that erodes user confidence in the health-check flow. |
| [#1004](https://github.com/Hmbown/CodeWhale/issues/1004) | `/dryrun` — preview completion before sending | 8 | Critical for V4 Pro users iterating on long system prompts with tool definitions and @mentions; avoids unnecessary API cost and cache invalidation. |
| [#1425](https://github.com/Hmbown/CodeWhale/issues/1425) | Session hangs after large-text multi-agent processing | 6 | 3M-character novel analysis spawns 10 sub-agents; `agent_wait` timeout causes permanent session deadlock — a reliability concern for heavy workloads. |
| [#1732](https://github.com/Hmbown/CodeWhale/issues/1732) | Merged report save is extremely slow | 6 | Low cache-hit rate during document merge/saveroundtrips through the file system; impacts productivity for analysis-heavy workflows. |
| [#1482](https://github.com/Hmbown/CodeWhale/issues/1482) | NVIDIA NIM returns 404 on API call | 6 | NIM integration broken out-of-the-box for Windows users; `deepseek doctor` passes but the API endpoint is unreachable. |
| [#1651](https://github.com/Hmbown/CodeWhale/issues/1651) | VS Code crashes during YOLO Agent test runs | 5 | Autonomous test execution with v4-pro/v4-flash destabilizes the host IDE — a hard crash, not a graceful error. |
| [#1829](https://github.com/Hmbown/CodeWhale/issues/1829) | SSH exit code 255 — sandbox blocks TCP 22 outbound | 5 | Shell sandbox appears to block outbound SSH, breaking remote workflows; users report the same command works in a normal terminal. |
| [#425](https://github.com/Hmbown/CodeWhale/issues/425) | Subagent `resume_from` continuation chains | 4 | Enables subagents to inherit prior transcript lineage — preserves prefix-cache affinity across role transitions (explore → implement → verify). 👍 1 |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5135](https://github.com/Hmbown/CodeWhale/pull/5135) | v0.9.4 release train | ✅ CLOSED | 77 commits; the main integration branch. Contains all 2026-08-01 source-candidate changes plus 18 train-specific commits. |
| [#5148](https://github.com/Hmbown/CodeWhale/pull/5148) | Stack R3: runtime P0s | 🔄 OPEN | Chains on R1 (#5147). 9 commits covering transcript-escape corruption, #5099 route inheritance, roster shadowing, and trust-gate fixes. |
| [#5147](https://github.com/Hmbown/CodeWhale/pull/5147) | Stack R1: runtime truth + deletions | 🔄 OPEN | 17 commits; config-parse warnings (no more silent reverts to defaults), persistence-drop logging, execpolicy hardening, memory consolidation, and docs-truth updates. |
| [#5140](https://github.com/Hmbown/CodeWhale/pull/5140) | Fleet memory hardening | 🔄 OPEN | Bounded step budgets, retired-handle eviction from `HandleStore`, RSS telemetry, and explicit size regression tests for `subagents.v1.json`. |
| [#5139](https://github.com/Hmbown/CodeWhale/pull/5139) | Opt-in background advisor watcher | 🔄 OPEN | Addresses #3982 — a passive advisor reads a bounded transcript slice after each turn with tool calls and emits concise warnings without blocking the parent. |
| [#5142](https://github.com/Hmbown/CodeWhale/pull/5142) | `resume_from` continuation chains | 🔄 OPEN | Addresses #425 — new `resume_from` parameter on `agent_spawn` rehydrates prior subagent sessions, preserving prefix-cache affinity across role transitions. |
| [#5141](https://github.com/Hmbown/CodeWhale/pull/5141) | `SidebarFocus::Sessions` variant | 🔄 OPEN | Addresses #2934 — exposes a dedicated sessions sidebar panel via `/sidebar sessions`, independent of the Auto/Pinned panel stack. |
| [#5143](https://github.com/Hmbown/CodeWhale/pull/5143) | zh-Hant full locale promotion | 🔄 OPEN | Addresses #790 — lifts `zh-Hant` from a partial 502/1252-key pack to a fully shipped locale with parity to `en.json`. |
| [#5138](https://github.com/Hmbown/CodeWhale/pull/5138) | `send_later` delayed-continuation tool | 🔄 OPEN | Model-callable one-shot tool that schedules future messages into the current workspace — enables PR watcher loops and scheduled follow-ups without manual re-engagement. |
| [#5136](https://github.com/Hmbown/CodeWhale/pull/5136) | Fleet named agents bind to configured roles | 🔄 OPEN | Fixes stale-crosstalk where `model_strength: same` cloned the active model five times instead of using configured fleet profiles; only `general` now exposes model options. |

## 5. Feature Request Trends

- **Session & transcript UX**: A persistent sidebar for session browsing (#2934 / #5141) and `resume_from` subagent continuation chains (#425 / #5142) are the most visible UX feature requests — users want continuity across sessions and agent roles.
- **Pre-send visibility**: The `/dryrun` command (#1004) reflects a growing demand for cost-aware iteration workflows, especially among V4 Pro users managing long system prompts and tool definitions.
- **Background advisory/watcher**: The opt-in advisor (#3982 / #5139) extends the existing review/verifier primitives into a passive, non-blocking mode — users want continuous oversight without manual trigger overhead.
- **Fleet configurability**: Multiple named fleet configurations (#5137) and strict role-to-model binding (#5136) show demand for operator-scoped, deterministic fleet dispatch rather than a single global `[fleet]` table.
- **Delayed / scheduled actions**: The `send_later` tool (#5138) points to interest in asynchronous, model-driven workflow orchestration (PR watchers, release-drift checks).
- **i18n completeness**: Push to promote `zh-Hant` to a full locale (#790 / #5143) indicates the community wants parity across all shipped languages, not just partial packs.

## 6. Developer Pain Points

1. **Runtime reliability under heavy workloads**: Large multi-agent runs (#1425) and VS Code crashes during autonomous testing (#1651) reveal stability gaps when the TUI handles significant parallelism.
2. **Sandbox / network egress restrictions**: SSH exit code 255 (#1829) suggests the built-in shell sandbox blocks common outbound TCP ports, breaking remote-development workflows.
3. **Configuration trust gap**: `deepseek doctor` reporting healthy while the runtime fails (#689) and silent config reverts to defaults (#5147 pre-fix) erode diagnostic confidence.
4. **NIM & provider resolution bugs**: NVIDIA NIM 404 errors (#1482), provider-agnostic model resolution double-chains (#4851, #5098, #5099), and stale cross-provider model selection (#5107) create friction for users running multi-provider setups.
5. **Security-policy bypasses**: Today's cluster of v0.9.4 release-blockers (#5161 exec-policy `&` bypass, #5157/5158 MCP tool-filter and name-round-trip gaps, #5159 logout keyring asymmetry, #5160 state migration non-idempotency, #5154 persist_thread policy wipe, #5155/5156 workflow gate/budget bugs) indicates the hardening surface is broader than anticipated — multiple independent vectors were found in the same release window.
6. **Slow persistence paths**: Report-merge save latency (#1732) and state-migration duplicate-column errors (#5160) point to I/O and schema-migration pain in long-running sessions.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*