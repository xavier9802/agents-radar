# AI CLI Tools Community Digest 2026-08-06

> Generated: 2026-08-06 03:16 UTC | Tools covered: 10

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



# Cross-Tool Comparison Report — AI CLI Ecosystem
**Date:** 2026-08-06

---

## 1. Ecosystem Overview

The AI CLI tool landscape is in a phase of rapid consolidation and maturity, with established players (Claude Code, Codex, Gemini CLI, Copilot CLI) pushing stable releases while smaller projects (Kimi, OpenCode, Pi, DeepSeek TUI) compete on differentiation and niche capabilities. Multi-agent orchestration, MCP interoperability, and context-management reliability have emerged as the top cross-cutting concerns across every community. Windows stability remains a systemic weakness, and terminal UX quality directly impacts developer retention. The market is bifurcating between hosted-cloud-first tools and self-hosted/local-first options, with provider-agnostic compatibility becoming a key differentiator.

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Release Today | Release Frequency |
|------|-----------|---------|---------------|-------------------|
| **Claude Code** | 10 | 5 | v2.1.223 | Weekly |
| **OpenAI Codex** | 10 | 17 | v0.146.1 + 5 alpha builds | Daily (alpha) |
| **Gemini CLI** | 10 | 10 | v0.54.0, v0.55.0-preview.1, 2 nightlies | Daily (nightly) |
| **GitHub Copilot CLI** | 11 (9 open) | 0 | v1.0.79-5 | Bi-weekly patches |
| **Kimi Code CLI** | 3 | 3 | None | Low |
| **OpenCode** | 10 | 10 | v1.18.14 | Weekly |
| **Pi** | 10 | 10 | None | Sporadic |
| **Qwen Code** | 10 | 10 | v0.21.6 + desktop-v0.1.0 | Weekly |
| **DeepSeek TUI** | 1 | 11 | v0.9.4 train (open) | Weekly train |
| **Grok Build** | 0 | 0 | None | None |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|-----------|---------------|---------------|
| **MCP interoperability & reliability** | Claude Code, Copilot CLI, Gemini CLI, OpenCode, DeepSeek TUI | Silent parameter dropping, `server/discover` rejection, OAuth 3LO gaps, non-GitHub remote failures |
| **Multi-agent orchestration** | Codex, Gemini CLI, Pi, DeepSeek TUI | Subagent hangs, recovery after timeout, permission enforcement, checkpoint resume |
| **Context management at scale** | Gemini CLI, Pi, Claude Code | Auto-compression on overflow, 400 errors past 128 tools, compaction timing failures |
| **Memory / persistent context** | Kimi Code, Gemini CLI, OpenCode, DeepSeek TUI | Cross-session retention, project pattern learning, low-signal session deduplication |
| **Provider-agnostic / custom model support** | Codex, Pi, Qwen Code, Gemini CLI | DeepSeek, Ollama, Bedrock, BYOK — all reporting friction in model selection and effort-flag parity |
| **Windows stability** | Claude Code, Codex, Copilot CLI, OpenCode, Qwen Code | Native crashes, OAuth failures, GPU renderer crashes, parent-shell termination |
| **Multimodal expansion** | Pi, Qwen Code, Gemini CLI, Kimi Code | Video/audio in prompts, image-returning MCP tool handling, Live Voice |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Kimi Code | Pi | Qwen Code | DeepSeek TUI |
|-----------|------------|-------------|-----------|------------|----------|-----------|-----|-----------|-------------|
| **Primary focus** | Enterprise workflows, marketplace, skills | Multi-agent V2, cyber-model safety | Agent reliability, memory system | Session management, UX polish | V2 migration, marketplace, hosted workspaces | Error recovery, robustness | Extension ecosystem, config flexibility | Desktop launch, live voice, TUI rendering | Runtime API surface, ACP protocol |
| **Target users** | Org-level admins, security teams | OpenAI power users, cyber-tool developers | General developers, Linux/Wayland users | GitHub enterprise teams | Self-hosted/local-first developers | Casual to mid-tier users | Extension authors, config-heavy users | Web-shell/desktop hybrid users | Advanced Rust/TUI users, ACP integrators |
| **Technical approach** | TypeScript/Electron, managed settings | Rust, Guardian safety layer, alpha-heavy | TypeScript, seatbelt profiles, auto-compression | TypeScript, concurrent session model | Rust, V1→V2 migration, plugin system | TypeScript, graceful degradation | TypeScript, event-bus architecture | Rust, Tauri desktop migration planned | Rust, ratatui TUI, REST runtime API |
| **Release cadence** | Steady weekly | Aggressive daily alpha | Daily nightly | Patch-focused | Weekly + active V2 PRs | Low | Sporadic | Weekly + desktop | Release trains |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **OpenAI Codex** leads in PR velocity (17 PRs, 5 alpha builds) — the team is shipping features fast but the alpha churn signals an unstable surface.
- **DeepSeek TUI** has disproportionate PR output (11 PRs) relative to its small issue count, indicating a focused maintainer-driven release train.
- **Gemini CLI** maintains a daily nightly pipeline with a healthy open-issue base, showing sustainable community engagement.

**Maturing with stable rhythms:**
- **Claude Code** and **Qwen Code** both ship weekly with balanced issue/PR ratios, indicating mature maintenance cycles.
- **OpenCode** is in an active migration phase (V1→V2) with 10 PRs and 10 issues, suggesting high community investment during a transition period.

**Slower or niche:**
- **Kimi Code** and **Pi** have low release activity but dedicated issue discussions, indicating smaller but engaged communities.
- **Copilot CLI** has zero PRs this cycle despite 11 hot issues — potential maintenance bottleneck or internal-only development cadence.
- **Grok Build** is inactive.

---

## 6. Trend Signals

1. **MCP is the new integration bottleneck.** Every major tool reports MCP pain — silent parameter loss (Claude Code), `server/discover` rejection (Copilot CLI), OAuth refresh failures (Gemini CLI), and non-GitHub remote 400s (Copilot CLI). Developers should expect continued tooling friction until the MCP spec stabilizes around error handling and authorization.

2. **Multi-agent reliability is the next frontier.** Subagent hangs, false-success reporting, and permission bypasses appear across Gemini CLI, Codex, and DeepSeek TUI. The market is moving from "can the agent work alone?" to "can the agent coordinate reliably with other agents?" — checkpoint resume and circuit-breaker patterns (Codex's Guardian) are early signals.

3. **Context management is becoming a first-class concern.** Auto-compression (Gemini CLI), configurable compaction thinking level (Pi), and 128-tool limits triggering 400 errors are all symptoms of the same problem: tool call counts are growing faster than context-window budget. Tools that solve this elegantly will gain developer loyalty.

4. **Windows is the universal weak point.** Six tools report Windows-specific crashes, regressions, or authentication failures. This is a consistent market gap — tools that achieve Windows parity will have a competitive advantage in enterprise adoption.

5. **Self-hosted / local-provider demand is surfacing.** DeepSeek, Ollama, and Bedrock compatibility issues (Codex, Pi, Qwen Code) signal that the market is fragmenting away from OpenAI-first assumptions. Tools that treat provider substitution as a first-class feature rather than an afterthought will capture this segment.

6. **Terminal UX quality directly impacts retention.** Alt-screen regressions (Copilot CLI), Wayland exclusion (Gemini CLI), tmux flickering (Qwen Code), and clipboard corruption (Copilot CLI) are not niche complaints — they are daily friction points that drive users away. Tools investing in terminal compatibility (Gemini CLI's seatbelt fallback, Qwen Code's WSL/ConPTY fixes) are building defensible UX moats.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-06 | Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | PR | Skill | Comments | Status |
|---|-----|-------|----------|--------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` (eval fix) | — | 🔵 Open |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | — | 🔵 Open |
| 3 | [#538](https://github.com/anthropics/skills/pull/538) | `pdf` (case-sensitivity fix) | — | 🔵 Open |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | `odt` | — | 🔵 Open |
| 5 | [#210](https://github.com/anthropics/skills/pull/210) | `frontend-design` (clarity improvement) | — | 🔵 Open |
| 6 | [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` / `skill-security-analyzer` | — | 🔵 Open |
| 7 | [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` | — | 🔵 Open |
| 8 | [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | — | 🔵 Open |

**Discussion highlights:**

- **[PR #1298](https://github.com/anthropics/skills/pull/1298) — `skill-creator` eval fix:** The most-featured PR. `run_eval.py` reports recall=0% for every skill description regardless of content, rendering the description-optimization loop (`run_loop.py`) ineffective. Multiple contributors (MartinCajiao, Polluelo978, Lubrsy706) filed related fixes for Windows stream reading, trigger detection, and isolated eval files — indicating a shared root cause still unresolved.

- **[PR #514](https://github.com/anthropics/skills/pull/514) — `document-typography`:** Addresses typographic quality in AI-generated documents — orphan words, widow paragraphs, numbering misalignment. Taps into a broad demand for production-quality document output beyond raw content generation.

- **[PR #83](https://github.com/anthropics/skills/pull/83) — `skill-quality-analyzer` & `skill-security-analyzer`:** Meta-skills that evaluate skills across five dimensions (structure, documentation, examples, etc.). Reflects growing community interest in skill *governance* and quality assurance as the marketplace scales.

- **[PR #1367](https://github.com/anthropics/skills/pull/1367) — `self-audit`:** Audits AI output before delivery with mechanical file verification followed by a four-dimension reasoning quality gate. Universal applicability across projects and tech stacks.

- **[PR #723](https://github.com/anthropics/skills/pull/723) — `testing-patterns`:** Covers the full testing stack — AAA pattern, React Testing Library, TDD philosophy, and test selection guidance. Responds to strong demand for structured testing expertise.

- **[PR #486](https://github.com/anthropics/skills/pull/486) — `odt`:** Adds OpenDocument Format support (creation, filling, ODT→HTML conversion), filling a gap for open-standard document workflows.

- **[PR #538](https://github.com/anthropics/skills/pull/538) — `pdf` case-sensitivity fix:** 8 reference mismatches in `SKILL.md` break skills on Linux/macOS. High practical impact despite narrow scope.

---

## 2. Community Demand Trends (from Issues)

| Trend | Key Issues | Signal |
|-------|-----------|--------|
| **Security & trust boundaries** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍), [#1175](https://github.com/anthropics/skills/issues/1175) | Community concerns about namespace impersonation and context-window exhaustion from skill injection (~156k tokens in [#1487](https://github.com/anthropics/skills/issues/1487)). |
| **Org-wide skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) | Strong demand for built-in organizational skill libraries; current workflow (download → share → manual upload) is friction-heavy. |
| **Skill-creator toolchain reliability** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍), [#1169](https://github.com/anthropics/skills/issues/1169), [#189](https://github.com/anthropics/skills/issues/189) (6 comments, 9 👍) | The eval loop's 0% recall bug is the single most-discussed technical issue. Duplicate skills from overlapping plugin installs is a top usability bug. |
| **Testing & quality assurance** | [#723](https://github.com/anthropics/skills/pull/723), [#83](https://github.com/anthropics/skills/pull/83), [#1385](https://github.com/anthropics/skills/issues/1385) | Clear appetite for structured testing guidance and pre-delivery quality gates. |
| **Documentation & governance** | [#412](https://github.com/anthropics/skills/issues/412), [#202](https://github.com/anthropics/skills/issues/202), [#509](https://github.com/anthropics/skills/pull/509) | Requests for agent governance patterns, skill-creator tone improvement, and a CONTRIBUTING guide. |

---

## 3. High-Potential Pending Skills

These active PRs are not yet merged and could land soon:

1. **[PR #1298](https://github.com/anthropics/skills/pull/1298) — `skill-creator` eval fixes** — Consolidates Windows stream, trigger detection, and parallel-worker fixes. High impact; multiple related PRs suggest urgency.

2. **[PR #1367](https://github.com/anthropics/skills/pull/1367) — `self-audit`** — Universal pre-delivery audit skill with mechanical verification + reasoning quality gate. Broad applicability.

3. **[PR #514](https://github.com/anthropics/skills/pull/514) — `document-typography`** — Fills a noticeable gap in document-output quality; low-risk, high-utility skill.

4. **[PR #723](https://github.com/anthropics/skills/pull/723) — `testing-patterns`** — Comprehensive testing skill with strong community interest (referenced in issue discussions).

5. **[PR #486](https://github.com/anthropics/skills/pull/486) — `odt`** — OpenDocument support is a clear extension of existing PDF/DOCX skills; incremental but valuable.

6. **[PR #1302](https://github.com/anthropics/skills/pull/1302) — `color-expert`** — Self-contained color-knowledge skill covering naming systems, color spaces, and practical guidance. Niche but well-scoped.

7. **[PR #1479](https://github.com/anthropics/skills/pull/1479) — `plan-file-hygiene`** — Addresses planning artifact accumulation (#1417); directly responds to community-identified lifecycle gap.

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable tooling and governance** — fixing the broken `skill-creator` evaluation loop and establishing trust/safety boundaries — rather than for new domain-specific skills; the highest-engagement discussions (#492, #556, #228) all center on platform integrity, not capability expansion.

---



# Claude Code Community Digest — 2026‑08‑06

## 1. Today’s Highlights
Claude Code v2.1.223 lands with managed‑setting support for owner‑wildcard marketplace rules and new warnings for workflow agents and forked skills. The community’s top concern is a regression in Cloud/Cowork sessions that blocks all pushes to unauthorized repositories—even when a fine‑grained PAT is supplied (Issue #76248). Meanwhile, a parser bug in the tag‑grammar tool‑call handler can silently drop parameters, raising reliability alarms for MCP integrations (Issue #84362).

## 2. Releases
**v2.1.223**  
- Added `owner/*` wildcard entries to `strictKnownMarketplaces` and `blockedMarketplaces` managed settings, enabling org‑level allow/block for marketplace repos.  
- Added warnings when workflow agents, forked skills, slash commands, or resumed background agents are invoked.  
[View release on GitHub](https://github.com/anthropics/claude-code/releases)

## 3. Hot Issues
1. **[BUG] Cloud/Cowork git proxy blocks all pushes** (#76248) — 11 comments, 5 👍  
   Fine‑grained PATs no longer bypass the “authorized repository set” check in remote sessions. Affects all Cowork/cloud users; high engagement signals broad impact.  
   [Link](https://github.com/anthropics/claude-code/issues/76248)

2. **[BUG] Opus 4.8/5.0 language quality & coherence** (#77136) — 8 comments, 8 👍  
   Users report toxic/unpleasant tone in Opus 4.8 and severe incoherence in Opus 5.0. Strong community backing indicates a model‑performance concern.  
   [Link](https://github.com/anthropics/claude-code/issues/77136)

3. **[BUG] Claude Desktop crashes near 5‑hour usage limit** (#83403) — 7 comments  
   Desktop becomes unrecoverable without a full reinstall after extended sessions. Points to a memory‑leak or state‑corruption bug in long‑running processes.  
   [Link](https://github.com/anthropics/claude-code/issues/83403)

4. **[BUG] `--continue` cannot find sessions created by `-p`** (#82536) — 7 comments  
   Interactive‑resume flag fails to locate sessions launched with the project‑focused `-p` flag, breaking workflow continuity for power users.  
   [Link](https://github.com/anthropics/claude-code/issues/82536)

5. **[BUG] MCP tool calls silently drop trailing parameters** (#72228) — 5 comments, 1 👍  
   Long parameter values cause subsequent fields to be omitted before the request leaves the client. Critical for MCP integrations that rely on complete argument sets.  
   [Link](https://github.com/anthropics/claude-code/issues/72228)

6. **[BUG] Bundled ugrep balloons to 9–14 GB RSS** (#83342) — 4 comments  
   Compiling a bounded‑interval BRE with the bundled `ugrep` binary triggers extreme memory growth, degrading performance on Linux agents.  
   [Link](https://github.com/anthropics/claude-code/issues/83342)

7. **[BUG] GPU process crash (exitCode 101457950) kills Desktop on Windows** (#83744) — 4 comments  
   A Windows‑specific GPU renderer failure brings down the entire app, highlighting stability issues in the Electron/Electron‑based desktop layer.  
   [Link](https://github.com/anthropics/claude-code/issues/83744)

8. **[BUG] “Always allow” for Claude‑in‑Chrome persists as duration “once”** (#74715) — 4 comments  
   Browser‑extension permissions are not saved across sessions, forcing repeated prompts and breaking automated web‑automation workflows.  
   [Link](https://github.com/anthropics/claude-code/issues/74715)

9. **[BUG] Tag‑grammar parser silently absorbs parameter blocks** (#84362) — 0 comments  
   Mismatched or malformed close tags cause the parser to swallow subsequent parameters, leading to silent data loss on MCP calls. A serious reliability bug for tool‑call pipelines.  
   [Link](https://github.com/anthropics/claude-code/issues/84362)

10. **[BUG] Model fabricated user messages as assistant output** (#84369) — 0 comments  
    During interactive sessions, the model emitted the user’s own messages (and a third‑party reply) as its own assistant output, then acted on them. Indicates a prompt‑injection or context‑blending failure.  
    [Link](https://github.com/anthropics/claude-code/issues/84369)

## 4. Key PR Progress
1. **fix(scripts): allow any user to prevent auto‑close with thumbs down** (#84365) — Aligns with the dedupe bot’s behavior; any user’s thumbs‑down now blocks automatic issue closure.  
   [Link](https://github.com/anthropics/claude-code/pull/84365)

2. **fix(hookify): fail closed on exceptions in pretooluse hook** (#84364) — Changes hook behavior so that exceptions (e.g., `ImportError`) now return `permissionDecision: 'deny'` instead of allowing the gated tool to execute. Security‑critical fix.  
   [Link](https://github.com/anthropics/claude-code/pull/84364)

3. **Add 14 Revolutionary Claude Code Plugins** (#41661) — Submitted a set of 14 production‑ready plugins covering security, performance, architecture, and fullstack automation, with marketplace registration and documentation.  
   [Link](https://github.com/anthropics/claude-code/pull/41661)

4. **fix(code-review): respect `--comment` flag for GitHub posting** (#16929) — Makes `/code-review` post inline comments to GitHub only when `--comment` is supplied, matching README documentation and user expectations.  
   [Link](https://github.com/anthropics/claude-code/pull/16929)

5. **fix: workaround for self‑signed certificate error in Cowork** (#84138) — Addresses a Bun‑runtime SSL issue on macOS where system certificates are not loaded, causing “Self‑signed certificate detected” errors in corporate environments.  
   [Link](https://github.com/anthropics/claude-code/pull/84138)

## 5. Feature Request Trends
- **Cross‑device browser control** – Request for reliable device identification when driving a connected browser from a remote host (Issue #77605).  
- **Portable session transcripts** – Desire to keep conversation history project‑bound while leaving scratch files local‑only, keyed by session ID (Issue #81946).  
- **Gesture & UI customization** – Users want to disable or rebind the left‑arrow detach‑to‑background gesture (Issue #84348) and have mobile typeahead for slash commands (Issue #56204).  
- **Session history management** – Proposal to pin sessions and define custom sort orders in the sidebar (Issue #84368).  

## 6. Developer Pain Points
- **Authentication & proxy regressions** – Git‑proxy blockage in Cloud/Cowork (#76248) and persistent login loops on macOS (#72875) disrupt remote workflows.  
- **Model‑quality & safety‑flag noise** – Tone/coherence complaints (Opus 4.8/5.0, #77136) and false‑positive T&S flags on defensive tooling (#84340, #84361) create friction for security‑focused development.  
- **MCP & tool‑call reliability** – Silent parameter dropping (#72228, #84362) and the GitHub MCP authorization‑header bug (#84367) undermine trust in external tool integrations.  
- **Desktop stability & performance** – GPU crashes on Windows (#83744), 5‑hour usage crashes (#83403), and ugrep memory bloat (#83342) point to resource‑management gaps in the Electron/desktop layer.  
- **Parser & context‑blending failures** – The tag‑grammar parser’s permissive absorption of mismatched close tags (#84362) and the model fabricating user messages as its own output (#84369) highlight risks in the tool‑call processing pipeline.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-06

---

## 1. Today's Highlights

The Codex team shipped **v0.146.1**, a bug-fix release introducing safer auto-review defaults for cyber-capable models and clearer permission-change messaging in the terminal interface. The most active developer discussion this week centers on **Multi-Agent V2 compatibility with non-OpenAI providers**, with three open issues reporting that encrypted task payloads and `agent_message` items fail across custom backends like DeepSeek and Ollama. On the feature side, the team is advancing a **unified image budget**, **durable message queuing**, and **skill system centralization** across several merged PRs.

---

## 2. Releases

### rust-v0.146.1
- **Safer auto-review defaults for cyber-capable models** — tightens automatic-review policies and clarifies permission changes visible in the terminal UI.
- Full changelog: https://github.com/openai/codex/compare/rust-v0.146.0...rust-v0.146.1

### rust-v0.147.0-alpha series (10, 11, 12, 13, 6.5)
- Multiple alpha iterations pushed for ongoing feature work; no individual release notes published beyond version labels.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Status |
|---|-------|----------|----|--------|
| [#25203](https://github.com/openai/codex/issues/25203) | GitHub OAuth callback fails with "Unable to find Electron app" on Windows | 38 | 21 | CLOSED |
| [#2880](https://github.com/openai/codex/issues/2880) | Copy/Export Message as Markdown | 27 | 78 | CLOSED |
| [#2020](https://github.com/openai/codex/issues/2020) | Support for light-background terminals | 24 | 60 | CLOSED |
| [#2909](https://github.com/openai/codex/issues/2909) | Support for multi-root workspaces | 23 | 143 | CLOSED |
| [#25319](https://github.com/openai/codex/issues/25319) | Scope Codex VS Code chats to current workspace/project | 22 | 54 | OPEN |
| [#27694](https://github.com/openai/codex/issues/27694) | Desktop crashes Dock via CodexDockTilePlugin recursion on macOS | 17 | 8 | CLOSED |
| [#34833](https://github.com/openai/codex/issues/34833) | MultiAgentV2 cross-provider subagent cannot consume encrypted task | 8 | 3 | OPEN |
| [#33551](https://github.com/openai/codex/issues/33551) | Multi-Agent V2 sends OpenAI-specific `agent_message` to external providers | 7 | 4 | OPEN |
| [#25934](https://github.com/openai/codex/issues/25934) | TUI markdown hyperlinks not clickable in OSC 8-capable terminals | 6 | 1 | OPEN |
| [#29242](https://github.com/openai/codex/issues/29242) | Chrome and Computer Use fail with "missing field sandboxPolicy" on Windows | 6 | 4 | CLOSED |

**Why these matter:**

- **#25203** — A persistent Windows auth blocker affecting the desktop app; high comment count signals ongoing community frustration despite being closed.
- **#2880** — One of the most upvoted feature requests (78 👍); users need portable markdown exports for documentation and issue tracking.
- **#2020** — Light-terminal support is a quality-of-life issue that contradicts Codex's "runs in your terminal" promise; 60 👍 shows strong demand.
- **#2909** — The single most upvoted open-issue-adjacent request (143 👍) for multi-root workspace support in the VS Code extension.
- **#25319** — Directly follows up on #2909; requests workspace-scoped chat history in VS Code, still open and actively discussed.
- **#34833 / #33551 / #36586** — A cluster of three related open issues exposing that Multi-Agent V2's encrypted task format is not portable to non-OpenAI providers, a critical gap for users of DeepSeek, Ollama, and other custom backends.
- **#29242** — Part of a recurring Windows Computer Use / sandboxPolicy failure pattern (also seen in #29238, #29267, #37043, #37201), indicating a platform-specific bug surface.

---

## 4. Key PR Progress

| PR | Title | Status |
|----|-------|--------|
| [#37206](https://github.com/openai/codex/pull/37206) | Add a unified image budget (6,000px / 10,000-patch limit) | OPEN |
| [#37204](https://github.com/openai/codex/pull/37204) | Add durable user-message queue dispatch (FIFO reorder, edit, delete) | CLOSED ✓ |
| [#37199](https://github.com/openai/codex/pull/37199) | Track thread archive analytics (`codex_thread_archive_event`) | CLOSED ✓ |
| [#37198](https://github.com/openai/codex/pull/37198) | Prefer persisted `cwd` when reading local threads | CLOSED ✓ |
| [#37191](https://github.com/openai/codex/pull/37191) | Preserve legacy semantics during rollout migration | CLOSED ✓ |
| [#37190](https://github.com/openai/codex/pull/37190) | Interrupt cyber-model turns after one Guardian denial (circuit breaker) | CLOSED ✓ |
| [#37189](https://github.com/openai/codex/pull/37189) | Track multi-agent usage hints in world state | CLOSED ✓ |
| [#37188](https://github.com/openai/codex/pull/37188) | Reserve `tool_search` namespace for the built-in search tool | CLOSED ✓ |
| [#37178](https://github.com/openai/codex/pull/37178) | Preserve image transparency metadata in app-server items | CLOSED ✓ |
| [#37177](https://github.com/openai/codex/pull/37177) | Move explicit skill selection into `codex-skills` crate | CLOSED ✓ |
| [#37175](https://github.com/openai/codex/pull/37175) | Add legacy rollout migration to paginated history | CLOSED ✓ |
| [#37174](https://github.com/openai/codex/pull/37174) | Centralize skill invocation helpers in `codex-skills` | CLOSED ✓ |
| [#37168](https://github.com/openai/codex/pull/37168) | Bound remote MCP handshake HTTP requests | CLOSED ✓ |
| [#37167](https://github.com/openai/codex/pull/37167) | Expose session sources to MCP contributors | CLOSED ✓ |
| [#37157](https://github.com/openai/codex/pull/37157) | Harden named session lookup in the TUI | CLOSED ✓ |

**Notable progress:** The team is consolidating the skill system into `codex-skills` (#37177, #37174, #37162), shipping a durable message queue (#37204), and hardening rollout migration paths (#37191, #37175). Security is being tightened with a Guardian circuit breaker for cyber models (#37190) and bounded MCP handshakes (#37168). Image handling gains both a unified budget (#37206) and transparency metadata preservation (#37178).

---

## 5. Feature Request Trends

1. **Cross-provider Multi-Agent compatibility** — Three open issues (#34833, #33551, #36586) all flag that Multi-Agent V2's encrypted task format and `agent_message` item type are OpenAI-specific and break with DeepSeek, Ollama, and other custom providers. This is the dominant unresolved theme.

2. **Workspace and project scoping** — #2909 (multi-root workspaces, 143 👍) and #25319 (scoped chat history) show sustained demand for workspace-aware behavior in the VS Code extension.

3. **Terminal UX improvements** — Light-background support (#2020, 60 👍) and clickable OSC 8 hyperlinks (#25934) reflect ongoing friction in the TUI experience.

4. **Message and session management** — Copy-as-markdown (#2880, 78 👍), durable message queuing (#37204), thread archive analytics (#37199), and recursive trusted roots (#19426, 23 👍) indicate users want finer control over session lifecycle and content portability.

5. **Image handling** — Unified image budget (#37206) and transparency metadata (#37178) show the team is standardizing image processing across the stack.

---

## 6. Developer Pain Points

- **Windows instability** — A cluster of at least six open/closed issues (#25203, #29242, #29238, #29267, #37043, #37201) report Computer Use failures, `sandboxPolicy` missing errors, OAuth crashes, and transparency bugs. Windows users consistently hit runtime metadata propagation failures.

- **Multi-Agent V2 + custom providers** — Encrypted task payloads and OpenAI-specific `agent_message` item types are unusable with non-OpenAI backends. This blocks anyone running Multi-Agent V2 with DeepSeek, Ollama, or other Responses-compatible providers.

- **Terminal UI limitations** — Hard-coded dark-theme colors (#2020) and non-clickable markdown links (#25934) force users into workarounds or abandoned tooling, contradicting Codex's terminal-native positioning.

- **Session and thread persistence** — Stale `cwd` values (#37198), archive sync gaps (#11907, #37199), and rollout migration edge cases (#37191, #37175) indicate the thread storage layer is still maturing, causing visible inconsistencies between local and remote states.

- **macOS Desktop crashes** — Recursion in `CodexDockTilePlugin` (#27694) and Mac-to-Mac remote control timeouts (#34010) suggest desktop plugin and remote-exec paths need harderening.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-06

## 1. Today's Highlights

Gemini CLI v0.54.0 shipped as the latest stable release, while the v0.55.0-preview.1 and a fresh nightly build landed overnight. The top development themes this cycle are agent reliability (subagent hangs and recovery), context-management safeguards against tool-limit 400 errors, and memory-system hardening. On the infrastructure side, a macOS seatbelt profile fallback fix and a signal-forwarding improvement were merged into the nightly.

## 2. Releases

- **v0.54.0** — Latest stable. See changelog [PR #28708](https://github.com/google-gemini/gemini-cli/pull/28708).
- **v0.55.0-preview.1** — Preview build with nightly bumps and changelog scaffolding [PR #28706](https://github.com/google-gemini/gemini-cli/pull/28706).
- **v0.55.0-nightly.20260806.g761f604c1** — Nightly build featuring:
  - `fix(cli): fall back to embedded macOS seatbelt profiles if missing` ([PR #28551](https://github.com/google-gemini/gemini-cli/pull/28551))
  - `feat(pr-generator-core): add environment config parser, command executor, GitHub …` ([PR](https://github.com/google-gemini/gemini-cli/pull/28551))
- **v0.56.0-nightly.20260806** — Upcoming nightly version bump [PR #28707](https://github.com/google-gemini/gemini-cli/pull/28707).

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Misreported subagent termination masks real errors, causing downstream confusion. P1 bug. | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | Agents defer to the generalist and stall indefinitely; a severe usability blocker for complex tasks. | 8 comments · 8 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | 76 behavioral evals generated but need structured component-level runs — critical for release confidence. | 7 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | Could reduce tool-turns and token noise by precisely reading method bounds. | 7 comments · 1 👍 |
| [#28698](https://github.com/google-gemini/gemini-cli/issues/28698) | High memory usage detected | Users report growing memory loops — a major stability concern for long-running sessions. | 5 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory retrying low-signal sessions | Background extractor can re-surface the same low-value sessions forever. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduce Auto Memory logging | Secrets may already reach model context before redaction; logging may leak skill prompts. Security-adjacent. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell commands stuck at "Waiting input" | Simple CLI commands complete but Gemini hangs awaiting input — affects core agent loops. | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Linux Wayland users cannot use the browser agent — blocks a key user segment. | 4 comments · 1 👍 |
| [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) | (Sub)agents running without permission since v0.33.0 | Agents activate despite `disabled` mode, undermining user control expectations. | 3 comments |

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#28586](https://github.com/google-gemini/gemini-cli/pull/28586) | fix(core): preserve thoughtSignature in functionCall parts | Fixes a 0.53.0 regression that stripped `thoughtSignature` from parallel tool calls, causing `API Error 400`. |
| [#28676](https://github.com/google-gemini/gemini-cli/pull/28676) | fix(cli): forward termination signals to relaunched child process | `kill -TERM` on the bootstrap parent now correctly takes down the child, preventing orphaned processes. |
| [#28481](https://github.com/google-gemini/gemini-cli/pull/28481) | fix(core): refresh MCP OAuth tokens with stored client ID | MCP OAuth refresh now works with dynamic client registration; previously deleted stored credentials on failure. |
| [#28581](https://github.com/google-gemini/gemini-cli/pull/28581) | fix(cli): skip diff hunk markers during @ processing | Prevents diff `@@` markers from triggering recursive workspace glob searches — stops heap growth on large diffs. |
| [#28485](https://github.com/google-gemini/gemini-cli/pull/28485) | fix(cli): add gemini-3.5-flash to model selector | Exposes `gemini-3.5-flash` / `gemini-3.6-flash` in the selector for all users (fixes #28483). |
| [#28488](https://github.com/google-gemini/gemini-cli/pull/28488) | feat(cli): auto-compress chat history on context overflow | New `model.autoCompressOnOverflow` setting — automatically compresses history instead of hard-stopping with a warning. |
| [#28660](https://github.com/google-gemini/gemini-cli/pull/28660) | fix(sdk): keep sendStream alive on malformed tool arguments | Defensively parses string-valued tool args; rejects non-object JSON and emits structured errors instead of crashing the stream. |
| [#28689](https://github.com/google-gemini/gemini-cli/pull/28689) | fix(core): unwrap nested gaxios streaming errors | Improves parsing of nested quota/rate-limit errors from the HTTP client for GCA compatibility. |
| [#28688](https://github.com/google-gemini/gemini-cli/pull/28688) | fix(core): dynamic Cloud Workstations proxy redirect URI | OAuth in Cloud Workstations now resolves the correct redirect URI instead of hard-coded `localhost`. |
| [#28695](https://github.com/google-gemini/gemini-cli/pull/28695) | fix(sdk): don't abort sendStream on malformed tool args | Complements #28660 — closes the specific crash when `JSON.parse()` throws on unguarded model output. |

## 5. Feature Request Trends

- **More resilient agent orchestration** — Subagent hangs, recovery after MAX_TURNS, and permission bypasses are top concerns. The community wants agents that respect configured boundaries and degrade gracefully.
- **Context management at scale** — Auto-compression, 400 errors past 128 tools, and thought-signature handling signal that context-window pressure is a growing problem as tool counts and session length increase.
- **AST-aware codebase tools** — Multiple linked issues (#22745, #22746) explore whether AST-level reads and mappings can replace blanket file reads, reducing tokens and improving precision.
- **Auto Memory maturity** — Redaction safety, low-signal session deduplication, and invalid patch quarantine are active tracks, suggesting the memory system is moving from "experimental" to "production-hardened."
- **Cross-platform browser-agent support** — Wayland failures (#21983) and settings overrides (#22267) show users expect the browser agent to work reliably across Linux environments.

## 6. Developer Pain Points

1. **Agent hangs and silent failures** — Generalist-agent hangs (#21409), stuck shell prompts (#25166), and subagents that report false success (#22323) are the most frequent sources of frustration.
2. **Regression-prone releases** — The 0.53.0 thought-signature stripping (#28586) and model-selector omission (#28485) both point to insufficient guard coverage around context and tool-introspection paths.
3. **Memory bloat** — High memory usage (#28698) and recursive glob searches on diff prompts (#28581) cause performance degradation on large repos.
4. **Linux/Wayland exclusion** — The browser agent's failure on Wayland (#21983) leaves a significant user segment without a core feature.
5. **Auto Memory privacy and correctness** — Secrets reaching model context before redaction (#26525) and infinite retry on low-signal sessions (#26522) erode trust in the memory subsystem.
6. **Subagent permission bypass** — Agents running despite disabled configuration (#22093) makes it hard for users to control what the CLI does autonomously.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-06

## 1. Today's Highlights

The v1.0.79-5 patch lands with a major UX feature: **concurrent multi-session management** from the Sessions tab and sidebar. Prompt pinning is now off by default, giving users finer control over terminal layout on smaller screens. Meanwhile, the issue tracker shows a spike in MCP connectivity problems and clipboard/rendering regressions, with #1799 (alt-screen) and #3172 (clipboard) drawing the most community engagement.

---

## 2. Releases

### v1.0.79-5 — Latest stable
- **Added:** Manage multiple concurrent sessions from the Sessions tab and sidebar
- **Improved:** Prompt pinning is now off by default; enable via `pinnedPrompts: true`
- **Fixed:** Sandboxed wrapper builds (`make` and friends) now receive dev tool caches based on the build manifest

### v1.0.79-3 — Worktree sessions
- **Improved:** Use `/worktree new` to start a new session in an isolated worktree

### v1.0.79-2 — Prompt pinning refinements
- **Improved:** Pinned prompt row is now positioned one row higher, preserving prompt shape while reducing timeline cost; pinned prompts are left off by default on terminals under 30 rows

> Full release chain: [v1.0.79-5](https://github.com/github/copilot-cli/releases), [v1.0.79-3](https://github.com/github/copilot-cli/releases), [v1.0.79-2](https://github.com/github/copilot-cli/releases)

---

## 3. Hot Issues

| # | Title | Engagement | Why It Matters |
|---|-------|-----------|----------------|
| [#1799](https://github.com/github/copilot-cli/issues/1799) | How to turn off alt-screen views? | 👍 8 · 💬 12 | The new alt-screen mode has introduced multiple regressions; users are actively seeking a toggle to revert. |
| [#3172](https://github.com/github/copilot-cli/issues/3172) | "Somebody else is owning the clipboard" breaks layout | 👍 7 · 💬 2 | A persistent clipboard-status message corrupts the terminal status line and UI layout. |
| [#4345](https://github.com/github/copilot-cli/issues/4345) | Reasoning effort 'medium' unsupported for claude-haiku-4.5 | 👍 4 · 💬 2 | Feature flags assign medium effort indiscriminately, causing repeated sub-agent execution failures. |
| [#4374](https://github.com/github/copilot-cli/issues/4374) | `/mcp search` fails with 400 on Azure DevOps remotes | 👍 4 · 💬 0 | MCP registry browser is broken for any repo whose git remote points to Azure DevOps — a significant blocker for multi-platform teams. |
| [#4026](https://github.com/github/copilot-cli/issues/4026) | Copilot CLI crashes repeatedly on Windows | 👍 0 · 💬 2 | Unpredictable native-runtime crashes persist across four versions since May 2026; Windows stability is a known concern. |
| [#4370](https://github.com/github/copilot-cli/issues/4370) | MCP init fails when `server/discover` returns -32602 | 👍 1 · 💬 2 | FastMCP servers that don't implement `server/discover` are silently rejected, breaking integration with a growing class of MCP toolchains. |
| [#3934](https://github.com/github/copilot-cli/issues/3934) | MCP server "blocked by policy" despite valid config | 👍 1 · 💬 2 | Enterprise users report that correctly configured MCP servers are rejected by an opaque policy check that doesn't occur in VSCode/IntelliJ. |
| [#4202](https://github.com/github/copilot-cli/issues/4202) | `view` tool reports "Path does not exist" in 1.0.73 | 👍 1 · 💬 5 | Regression in the built-in `view` tool introduces false-negative file-existence errors; isolated SDK probes still work. |
| [#3135](https://github.com/github/copilot-cli/issues/3135) | BYOK statusline shows medium effort despite `--effort high` | 👍 1 · 💬 3 | Statusline display is out of sync with the actual request, misleading users about which reasoning tier is being billed. |
| [#4379](https://github.com/github/copilot-cli/issues/4379) | Browser canvas: GitHub login never persists | 👍 0 · 💬 0 | Each canvas instance receives an isolated storage partition, making authentication impossible to carry across sessions. |

**Closed this period:**
- [#2147](https://github.com/github/copilot-cli/issues/2147) — CAIP 400 input item ID mismatch (closed)
- [#3013](https://github.com/github/copilot-cli/issues/3013) — Hooks don't fire for background/task agents (closed)
- [#4375](https://github.com/github/copilot-cli/issues/4375) — macOS `MallocStackLogging` stderr spam (closed)

---

## 4. Key PR Progress

**No pull requests were opened or merged in the last 24 hours.**

---

## 5. Feature Request Trends

Distilling from open issues and feature requests this period:

1. **MCP interoperability & discoverability** — Multiple issues (#3934, #4370, #4374, #4371) point to a need for more forgiving MCP server initialization, better OAuth 3LO support (URL elicitation), and cross-platform git-remote awareness in MCP registry lookups.
2. **Terminal UI resilience** — The alt-screen mode (#1799) and clipboard status message (#3172) suggest users want a configurable, non-intrusive rendering layer with an escape hatch to the previous mode.
3. **BYOK/BYOM parity with hosted models** — Issues #3135 and #4376 highlight that bring-your-own-key and bring-your-own-model paths lack the same feature depth (effort display, in-session switching, model discovery) as the default model stack.
4. **Multi-session & session isolation** — Concurrent sessions landed in v1.0.79-5, but canvas storage isolation (#4379) and worktree-based session splitting (#1.0.79-3) indicate demand for deeper session-level sandboxing and identity boundaries.

---

## 6. Developer Pain Points

- **MCP is fragile across configurations.** Policy checks reject valid servers, `server/discover` responses are treated as fatal errors, OAuth 3LO lacks URL elicitation, and non-GitHub remotes (Azure DevOps) cause 400s in `/mcp search`. This is the dominant pain cluster this period.
- **Terminal rendering regressions.** Alt-screen mode and clipboard notifications disrupt layout and offer no user-controlled off-ramp.
- **Windows stability remains a concern.** Repeat, unpredictable native crashes on Windows across multiple versions since May 2026.
- **BYOK effort/statusline desync.** The statusline reports a different reasoning tier than what the request actually carries, creating billing confusion for custom-provider users.
- **Reasoning-effort flag compliance.** Feature flags assign `medium` effort to models that don't support it (e.g., claude-haiku-4.5), causing repeated sub-agent execution failures.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-06

---

## 1. Today's Highlights

Two bug-fix PRs landed today addressing the same root issue (#2588): when a model lacks declared `capabilities`, image-returning MCP tools would abort mid-task *after* side effects were already applied, with no actionable error message. The fixes both degrade gracefully instead of crashing, and one PR also surfaces a clear config fix in the error output. A long-standing feature request for a persistent Memory System across sessions remains the top community discussion (#1283).

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**[#1283] Feature Request: Memory System — Persistent context across sessions**
- *Why it matters:* Users want Kimi CLI to retain project patterns, preferences, and AI-managed notes between invocations, turning it from a stateless tool into a persistent development assistant.
- *Community reaction:* 19 comments since February; low thumbs-up count suggests it's an ongoing ask rather than a spike.
- 🔗 [Issue #1283](https://github.com/MoonshotAI/kimi-cli/issues/1283)

**[#2591] StrReplaceFile corrupts undecodable bytes outside the edited region**
- *Why it matters:* A serious correctness bug — any non-UTF-8 byte anywhere in a file gets replaced with `U+FFFD`, silently corrupting binary or legacy-encoded files even when the edit target is far away.
- *Community reaction:* Open, no comments yet. High severity given silent data corruption.
- 🔗 [Issue #2591](https://github.com/MoonshotAI/kimi-cli/issues/2591)

**[#2588] Model declared without capabilities: image-returning MCP tool aborts mid-task**
- *Why it matters:* Two compounding problems — the run aborts *after* side effects have already run (non-atomic), and the error gives no hint about how to fix the config. This PRs #2592 and #2590 are direct responses.
- *Community reaction:* Open, no comments yet, but two PRs already targeting it signals active maintainer attention.
- 🔗 [Issue #2588](https://github.com/MoonshotAI/kimi-cli/issues/2588)

---

## 4. Key PR Progress

**[#2592] fix(soul): degrade unsupported tool media instead of aborting mid-task**
- Resolves #2588 by preventing the post-side-effect abort. When a model without `capabilities` receives an image from an MCP tool, the runner now degrades gracefully rather than crashing after irreversible work.
- 🔗 [PR #2592](https://github.com/MoonshotAI/kimi-cli/pull/2592)

**[#2590] fix(soul): name the config fix in the unsupported-capability error**
- Partially addresses #2588 — the error now tells users *what to add* to `config.toml` instead of just naming the missing capability. Self-contained and independent of #2592.
- 🔗 [PR #2590](https://github.com/MoonshotAI/kimi-cli/pull/2590)

**[#2589] docs: mention qwen-audio-agent as a voice ACP client**
- Adds documentation for `qwen-audio-agent`, an open-source full-duplex voice runtime that launches `kimi acp` as an agent for hands-free interaction. Expands the ACP client ecosystem list beyond editor/IDE tools.
- 🔗 [PR #2589](https://github.com/MoonshotAI/kimi-cli/pull/2589)

---

## 5. Feature Request Trends

- **Persistent memory & context retention** is the dominant long-term request (#1283). Users want the CLI to learn project conventions and user preferences over time, reducing repetitive setup across sessions.
- **Robust error recovery** is an emerging theme — the #2588 / #2591 cluster shows demand for tools that fail safely (no silent corruption, no post-side-effect crashes) and surface actionable fixes.
- **Multi-modal & voice support** is growing, with the new `qwen-audio-agent` integration (#2589) and the MCP image-handling fixes indicating expanding use cases beyond text-only workflows.

---

## 6. Developer Pain Points

1. **Non-atomic tool execution:** When an MCP tool returns unsupported media (e.g., an image), side effects from the tool are already applied before the runner aborts. Developers need confidence that a failed turn won't leave partial changes.
2. **Silent file corruption:** `StrReplaceFile`'s use of `errors="replace"` on the entire file means undecodable bytes far from the edit region are silently overwritten — a dangerous gotcha for projects with mixed encodings or binary-adjacent files.
3. **Unclear configuration errors:** Models declared without `capabilities` produce errors that name the missing capability but never say *how* to declare it, forcing users to dig into docs or source.
4. **Session statelessness:** The lack of a memory system means developers must re-establish context manually on every invocation, which becomes repetitive in long-running projects.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-06

## 1. Today's Highlights

OpenCode v1.18.14 landed with simplified xAI login and improved transient error retry logic, while V2 migration tooling and hosted workspace execution are advancing in parallel. Community demand is heavily focused on a unified marketplace/registry, plugin extensibility, and Windows terminal stability fixes.

## 2. Releases

**v1.18.14**
- **Improvement:** Simplified xAI login to a single device-code flow, better for headless/remote environments.
- **Bugfixes:** Preserved structured mid-stream provider errors for compatible retry support; improved retry coverage for transient provider and network errors.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#28696](https://github.com/anomalyco/opencode/issues/28696) | Plugin/Agent/Skills marketplace | Master issue for a unified distribution system — could define the extensibility ecosystem. | 23 👍, 7 comments |
| [#14026](https://github.com/anomalyco/opencode/issues/14026) | Some models do not generate code | Local Ollama models (qwen2.5-coder, ministral) emit tool calls but don't execute them. | 9 comments, 1 👍 |
| [#16226](https://github.com/anomalyco/opencode/issues/16226) | Send prompt only with button, not Enter | Complex multi-paragraph prompts get accidentally submitted on Enter. | 8 comments |
| [#27749](https://github.com/anomalyco/opencode/issues/27749) | `/exit` and `/quit` kill Windows terminal | `/exit` closes the parent shell on Windows — a regression affecting all PowerShell/ConPTY users. | 7 comments, 1 👍 |
| [#31042](https://github.com/anomalyco/opencode/issues/31042) | `small_model` ignored for title agent | Title generation always uses `deepseek-v4-flash-free` regardless of config. | 5 comments |
| [#31105](https://github.com/anomalyco/opencode/issues/31105) | Duplicate message markers in CLI | Number spam ("259 259 259…") floods the terminal on Windows across sessions. | 5 comments |
| [#31099](https://github.com/anomalyco/opencode/issues/31099) | Renderer freeze — Solid.js infinite loop | v1.16.2 desktop freezes after ~12 min on macOS due to `findDOMIndex` loop. | 5 comments |
| [#30057](https://github.com/anomalyco/opencode/issues/30057) | Add AI CLI tools to bash arity dictionary | Tools like `npx`, `bunx`, `uvx`, and `opencode` themselves are missing from permission checks. | 5 comments, 1 👍 |
| [#40791](https://github.com/anomalyco/opencode/issues/40791) | GO subscription unusable | Reports extreme slowness and 403 errors on GPT models — a paid-tier reliability concern. | 3 comments, 0 👍 |
| [#28673](https://github.com/anomalyco/opencode/issues/28673) | `/exit` + Ctrl+C kill parent terminal on Windows | Bisected to v1.14.25; affects all modern Windows terminals (Warp, WinTerm, VS Code). | 3 comments, 3 👍 |

## 4. Key PR Progress

| # | Title | Author | Status | Summary |
|---|-------|--------|--------|---------|
| [#40784](https://github.com/anomalyco/opencode/pull/40784) | Hosted workspace execution with modal driver | kitlangton | OPEN | Introduces durable workspace execution for V2 — a Workspace is a persistent machine/root environment, with sessions targeting a `workspaceID` via the runner graph. |
| [#38790](https://github.com/anomalyco/opencode/pull/38790) | Workspace flows in new layout | Hona | OPEN | Adds workspace selection for new sessions: local repo, isolated new workspace, or existing workspaces, with branch-aware context pills. |
| [#40787](https://github.com/anomalyco/opencode/pull/40787) | Remove obsolete and unreachable code | kitlangton | OPEN | Deletes ~1,500 lines of migration relics, dead exports, and draft code across the V2 package set. |
| [#40382](https://github.com/anomalyco/opencode/pull/40382) | Remove V1 compatibility layer | Brendonovich | CLOSED | Strips V1 protocol detection, legacy adapters, and the old SDK; all App traffic now routes through V2 exclusively. |
| [#40723](https://github.com/anomalyco/opencode/pull/40723) | Migrate V1 data to V2 | thdxr | CLOSED | Adds REST-triggered resumable V1→V2 session migration, including legacy JSON credentials and rebased session/ACP event handling. |
| [#40794](https://github.com/anomalyco/opencode/pull/40794) | Disable packaged console logging | opencode-agent[bot] | OPEN | Disables `electron-log` console transport in production Desktop builds to avoid pipe-inheritance issues; dev builds keep it. |
| [#35311](https://github.com/anomalyco/opencode/pull/35311) | Multiple clones of same repo are different projects | belisoful | OPEN | Fixes a long-standing issue where cloned copies of the same repo were treated as separate projects (closes 15 related issues). |
| [#40781](https://github.com/anomalyco/opencode/pull/40781) | Export session as JSON from UI | Hona | CLOSED | Adds `Export...` to the session menu, an export button in the Context tab, and a `/export` command palette action. |
| [#40590](https://github.com/anomalyco/opencode/pull/40590) | Support `GITHUB_TOKEN` auth in install script | rwenz2004 | OPEN | Allows GitHub token-based auth in the install script to avoid rate limits on anonymous requests. |
| [#40772](https://github.com/anomalyco/opencode/pull/40772) | Report missing auth method instead of crashing | shoemoney | OPEN | Guards `ProviderAuth.authorize` index lookups to return a clear error instead of an unhandled crash. |

## 5. Feature Request Trends

- **Extensibility & Marketplace:** Issue #28696 (23 👍) anchors community demand for a plugin/skills marketplace. The `/simplify` skill request (#29272) and system-prompt plugin API (#31158) reinforce a push toward a richer plugin ecosystem.
- **Workspace Abstraction:** Multiple PRs and issues point toward durable, named Workspaces — distinct from repositories — with hosted execution environments (#40784, #38790, #35311).
- **UX Control:** Users want finer control over submission behavior (Enter vs. button, #16226), session editing/splitting (#17251), and configurable keybindings (#31100).
- **Local/Offline Support:** Local LAN provider discovery (#27554), Ollama model compatibility (#14026), and workspace isolation reflect sustained interest in self-hosted workflows.
- **Portability & Tooling:** Bash arity expansion (#30057) and session export (#40781) show demand for tighter integration with existing developer toolchains.

## 6. Developer Pain Points

- **Windows terminal stability remains the top grievance.** Three separate issues (#27749, #28673, #30495) report that `/exit`, `/quit`, and Ctrl+C kill or corrupt the parent shell on Windows (ConPTY, psmux, conhost). This is a recurring, high-impact regression.
- **Renderer freezes and infinite loops** (#31099, #31105) on desktop cause session interruption and require restarts — particularly on macOS and Windows.
- **Provider reliability and error handling:** Transient errors (#31133), SSE memory growth (#31087), and compaction-induced retry loops (#39291) indicate fragile error-recovery paths, especially with local and third-party providers.
- **Configuration drift:** `small_model` ignored for title generation (#31042) and `project.icon_url_override` lost on refresh (#24197) suggest persistence and config-read bugs.
- **Windows CPU compatibility:** AVX2-required builds crash on older hardware (#31155), limiting accessibility.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑08‑06

## 1. Today’s Highlights
The Pi community is actively discussing Windows‑centric usage patterns and a critical auto‑compaction bug that can cause sessions to exceed context limits without triggering summarization. On the infrastructure side, a long‑running X11 connection leak in `pi‑coding‑agent` has drawn immediate attention, with a fix already proposed. New provider integrations (Amazon Bedrock Mantle, Qwen Token Plan Individual) and enhanced multimodal support remain top feature requests.

## 2. Releases
No new releases in the last 24 hours.

## 3. Hot Issues
1. **[Windows] sink‑thread usage discussion** (#7547) – Open community thread to consolidate Windows‑specific usage, bugs, and documentation focus. *18 comments, created 2026‑08‑03.*  
   https://github.com/badlogic/pi-mono/issues/7547

2. **Auto‑compaction never triggers after context exceeds 100%** (#6879) – Sessions can exceed the context window before compaction runs, causing API‑rejected requests. *13 likes, 11 comments.*  
   https://github.com/badlogic/pi-mono/issues/6879

3. **Ephemeral in‑session model/thinking changes** (#5263) – Proposal to make session‑local model or thinking‑level overrides temporary by default, with a global default setting. *12 likes, 11 comments.*  
   https://github.com/badlogic/pi-mono/issues/5263

4. **Video/audio content in `prompt` command** (#3200) – Request to extend the `prompt` RPC command to accept video and audio alongside images, enabling full multimodal pipelines. *4 likes, 7 comments.*  
   https://github.com/badlogic/pi-mono/issues/3200

5. **Configurable thinking level for compaction** (#7553) – Compaction currently reuses the session’s thinking level; users want independent control to avoid wasting reasoning budget. *7 comments.*  
   https://github.com/badlogic/pi-mono/issues/7553

6. **X11 connection leak in pi‑coding‑agent** (#7600) – A process running ~8 days leaked 182 X11 connections, filling the X server’s client table and breaking new clients. *2 comments, critical bug.*  
   https://github.com/badlogic/pi-mono/issues/7600

7. **Extension event‑bus listeners survive session reloads** (#7193) – Closed. Extensions subscribing via `pi.events.on()` were not cleaned up on reload, causing listener accumulation. *1 like, 2 comments.*  
   https://github.com/badlogic/pi-mono/issues/7193

8. **Copilot models missing after login** (#7634) – Closed. After authenticating with a Copilot account, `/model` showed no Copilot models because the API response format changed. *2 comments.*  
   https://github.com/badlogic/pi-mono/issues/7634

9. **Config folder out of place on Linux** (#534) – Closed. Community feedback (23 likes) urged adherence to the XDG Base Directory specification instead of placing config in `$HOME`.  
   https://github.com/badlogic/pi-mono/issues/534

10. **truncateToWidth leaves dangling OSC 8 hyperlink** (#7399) – Closed. The text‑truncation utility did not track hyperlink balance, producing malformed terminal output. *12 comments.*  
    https://github.com/badlogic/pi-mono/issues/7399

## 4. Key PR Progress
1. **Fix Linux clipboard X11 leaks** (#7694) – Replaces the native clipboard addon with `wl‑paste`, `xclip`, and `xsel` on Linux, preventing connection exhaustion. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7694

2. **Add Amazon Bedrock Mantle OpenAI Responses provider** (#6216) – Introduces a new provider using OpenAI’s Bedrock SDK, expanding AWS model access. *Open.*  
   https://github.com/badlogic/pi-mono/pull/6216

3. **Add Qwen Token Plan Individual provider** (#7659) – Supports the international Qwen Token Plan endpoint with its eight documented models and proper reasoning‑effort mapping. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7659

4. **Expose thinking‑token budget on OpenAI completions** (#7638) – Fixes a problem where reasoning and answer share `max_tokens`, causing the agent to terminate without output when thinking consumes the entire budget. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7638

5. **Colocate tool prompt contributions with tool definitions** (#7671) – Moves each built‑in tool’s system‑prompt snippet and guidelines next to its implementation, improving maintainability while preserving legacy output. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7671

6. **Add configurable Harness factory** (#7686) – Provides an internal coding‑agent factory for constructing the experimental Harness, allowing callers to attach prompt metadata and rebuild prompts from active tool objects. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7686

7. **Handle selection page keybindings** (#7680) – Brings `pageUp`/`pageDown` support to built‑in selection components, editor autocomplete, and coding‑agent selectors. *Open.*  
   https://github.com/badlogic/pi-mono/pull/7680

8. **Support line ranges in `@file` references** (#7679) – Closed. Enables 1‑based inclusive `#L<start>-L<end>` selectors on CLI `@file` references, with metadata included in prompt tags.  
   https://github.com/badlogic/pi-mono/pull/7679

9. **Restore Copilot models from account policy** (#7672) – Closed. Fixes the missing‑models‑after‑login issue by falling back to policy‑enabled models when the Individual endpoint returns no picker models.  
   https://github.com/badlogic/pi-mono/pull/7672

10. **Support `AGENTS.override.md` as per‑directory context override** (#7664) – Closed. Introduces a higher‑priority context file per directory that can replace `AGENTS.md`/`CLAUDE.md` in that directory while preserving ancestor layering.  
    https://github.com/badlogic/pi-mono/pull/7664

## 5. Feature Request Trends
- **Multimodal expansion** – Requests to handle video/audio alongside images (#3200) and to render mermaid diagrams in markdown (#7623).
- **Configuration flexibility** – Ephemeral session overrides (#5263), configurable compaction thinking level (#7553), context‑window size selection (#5064), and per‑directory context overrides (#7642).
- **Provider ecosystem growth** – New integrations for Amazon Bedrock Mantle (#6216), Qwen Token Plan Individual (#7659), and Meta’s Muse Spark (#7543).
- **Platform‑specific improvements** – Windows usage consolidation (#7547), XDG config compliance (#534), and Linux clipboard/X11 stability (#7694).

## 6. Developer Pain Points
- **Session reliability** – Auto‑compaction not triggering before context overflow (#6879), sessions hanging on “working” with certain subscriptions (#5291), and failed turns being non‑resumable from `/tree` (#7609).
- **Connection/resource leaks** – X11 connection exhaustion in long‑running agents (#7600), event‑bus listener leaks on extension reload (#7193), and transient update‑check failures aborting `pi update --self` (#6675).
- **Extension development friction** – No programmatic way to persist API‑key credentials to `auth.json` (#7658), invisible provider‑retry attempts lacking callbacks (#7649), and extension‑selector UI limitations with large diffs (#7597).
- **Environment and compatibility** – Crashes on Node 20 due to undici requirements (#7601), bash tool collapsing bare newlines into spaces (#7666), and overly encouraging bash‑inspection guideline in the system prompt (#7128).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-06

## 1. Today's Highlights

Qwen Code Desktop v0.1.0 shipped alongside the v0.21.6 release, introducing experimental native Live Voice support for WebShell on macOS. The community is actively filing desktop-first bugs on Windows (startup crashes, broken markdown links, unresponsive copy button) while the core team closes a silent-hang failure mode in `/review` CI runs and hardens the read-only shell classifier against command substitution bypasses.

---

## 2. Releases

**v0.21.6** and **desktop-v0.1.0** — See full changelog: [v0.21.6](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.6) · [desktop-v0.1.0](https://github.com/QwenLM/qwen-code/releases/tag/desktop-v0.1.0)

- Nightly v0.21.6-nightly.20260806 also published: deflaked glob external-path test by using a dedicated empty dir instead of `/tmp` ([#8604](https://github.com/QwenLM/qwen-code/pull/8604)).
- Key highlights in v0.21.6: experimental native Live Voice on WebShell (macOS global shortcut), conversation turns stay expanded during background activity, and CI bash-shell defaults were fixed in `qwen-triage` ([#7838](https://github.com/QwenLM/qwen-code/pull/7838)).

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#8582](https://github.com/QwenLM/qwen-code/issues/8582) | Read-only shell classifier auto-approves hidden command substitution (P1/security) | The AST-based and regex-based classifiers both miss commands that execute arbitrary code via line continuation or `${var@P}` — a serious security gap for sandboxed shells. |
| [#8136](https://github.com/QwenLM/qwen-code/issues/8136) | Provider warning sanitizer leaks passwords containing `@` (P2/security) | `sanitizeProviderWarning` strips credentials incorrectly when URLs contain a port, leaving `@`-delimited passwords exposed in `/status` payloads. 8 comments, active triage. |
| [#8615](https://github.com/QwenLM/qwen-code/issues/8615) | Desktop 0.1.0 crashes on Windows on workspace open (P1) | Bundled runtime throws `EISDIR lstat 'C:'` — a blocking issue for the newly shipped desktop on Windows 11. |
| [#8593](https://github.com/QwenLM/qwen-code/issues/8593) | Markdown links in assistant messages are styled but unclickable (P2) | Links render with hover effects but produce no action — silently swallowed clicks erode trust in the desktop UX. |
| [#8538](https://github.com/QwenLM/qwen-code/issues/8538) | Copy-response button does nothing on Windows Desktop (P2) | Clipped across restarts and reboots; the clipboard is never written to. High-friction for power users. |
| [#8560](https://github.com/QwenLM/qwen-code/issues/8560) | Web Shell session deep link returns 401 on refresh with bearer auth (P2) | Users authenticated via `qwen serve --token` get a hard 401 when refreshing a `/session/<id>` URL, breaking session continuity. |
| [#8584](https://github.com/QwenLM/qwen-code/issues/8584) | Anthropic dotted-minor model IDs rejected; Opus 5 limits missing (P2) | `claude-opus-4.8`-style IDs and new Opus 5 token limits are not recognized, blocking proxy deployments. |
| [#8592](https://github.com/QwenLM/qwen-code/issues/8592) | Desktop UI language switching has no effect (P2) | Selecting 简体中文 in Settings does not change any UI text — a localization gap in the new desktop. |
| [#8580](https://github.com/QwenLM/qwen-code/issues/8580) | TUI flickers continuously in tmux < 3.5 (P2) | Overflowing frames trigger full-screen clear+repaint due to unqueried DEC mode — affects Linux users in older tmux. |
| [#8606](https://github.com/QwenLM/qwen-code/issues/8606) | VSCode companion Edit/Write links resolve to `<root>/<basename>` (P2) | Nested file edits produce "file not found" because paths are resolved against the workspace root instead of their actual directory. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#8619](https://github.com/QwenLM/qwen-code/pull/8619) | `fix(desktop): strip Windows verbatim prefix from workspace paths` | Replaces `std::fs::canonicalize` with `dunce::canonicalize` to fix the Windows `EISDIR` crash on workspace open. |
| [#8399](https://github.com/QwenLM/qwen-code/pull/8399) | `fix(core): recognize OpenAI SDK APIUserAbortError as an abort` | Fixes missed user-abort detection for the OpenAI SDK, which carries no `.name` and no `ABORT_ERR` code. |
| [#8529](https://github.com/QwenLM/qwen-code/pull/8529) | `feat(core): resolve model modalities from API metadata` | Fetches missing input modalities from models.dev at runtime with disk caching; no cold-start penalty. |
| [#8616](https://github.com/QwenLM/qwen-code/pull/8616) | `feat(telemetry): align session lifecycle with OpenTelemetry` | Emits standard `session.start` / `session.end` LogRecords with `session.id`; resumed sessions also carry `session.previous_id`. |
| [#8445](https://github.com/QwenLM/qwen-code/pull/8445) | `fix(web-shell): allow session refresh with daemon auth` | Lets exact document navigations to `/session/<id>` load the public HTML shell before the bearer-auth gate, fixing the 401 issue. |
| [#8601](https://github.com/QwenLM/qwen-code/pull/8601) | `fix(web-shell): keep mobile composer at chat pane bottom` | Restores `position: static` for the mobile composer-wrap so it stays anchored at the bottom on narrow screens (≤760 px). |
| [#7897](https://github.com/QwenLM/qwen-code/pull/7897) | `fix(cli): skip terminal redraw optimizer on WSL/ConPTY` | Fixes streaming-text duplication on WSL + Windows Terminal where batched cursor-up sequences are mishandled by ConPTY. |
| [#8455](https://github.com/QwenLM/qwen-code/pull/8455) | `fix(cli): echo resume command to main screen on exit` | The "resume this session" hint now also echoes to the main buffer so users see it after alternate-buffer teardown in VP mode. |
| [#8602](https://github.com/QwenLM/qwen-code/pull/8602) | `fix(core): cap streaming response lifetime, slim review fan-out` | Adds a total-lifetime cap per streaming response (complementing the inactivity watchdog) to close the silent-hang in `/review` CI runs. |
| [#8620](https://github.com/QwenLM/qwen-code/pull/8620) | `fix(serve): allow approved same-host text reads outside workspace` | Aligns daemon text reads with CLI permissions so host files outside the registered workspace are accessible after tool approval. |

---

## 5. Feature Request Trends

- **Desktop consolidation** — Multiple issues converge on replacing the Electron desktop with a lower-maintenance Web-Shell-based Tauri app ([#8092](https://github.com/QwenLM/qwen-code/issues/8092), [#8596](https://github.com/QwenLM/qwen-code/issues/8596)).
- **Mobile / remote access** — QR-code pairing for phone control of local sessions ([#8595](https://github.com/QwenLM/qwen-code/issues/8595)) reflects demand for on-the-go session management.
- **SDK extensibility** — Request for inline `hooks` configuration in the TypeScript SDK `query()` call ([#8591](https://github.com/QwenLM/qwen-code/issues/8591)) to reduce boilerplate.
- **Asynchronous / cost-aware execution** — `/slow` or `/batch` mode for lower-cost async agent runs ([#8605](https://github.com/QwenLM/qwen-code/issues/8605)) targets users running long or high-volume workflows.
- **Background agent resilience** — `activeWork` tracking and recovery for background agents that outlive their foreground prompt ([#8586](https://github.com/QwenLM/qwen-code/issues/8586)).

---

## 6. Developer Pain Points

1. **Desktop v0.1.0 launch bugs dominate** — Windows crashes, broken markdown links, non-functional copy button, and language-switching no-ops are the top user-facing friction. The team is actively patching these alongside the release.
2. **TUI rendering across terminal emulators** — Flickering in tmux < 3.5 and text duplication on WSL/ConPTY indicate the redraw optimizer still has environment-specific edge cases.
3. **Web Shell auth round-trips** — Bearer-token sessions break on page refresh for deep-linked URLs; a fix is in PR [#8445](https://github.com/QwenLM/qwen-code/pull/8445).
4. **Security classifier gaps** — The read-only shell classifier is being stress-tested by community reports of command-substitution bypasses ([#8582](https://github.com/QwenLM/qwen-code/issues/8582)), and the provider-warning sanitizer still leaks certain password formats ([#8136](https://github.com/QwenLM/qwen-code/issues/8136)).
5. **VSCode extension path resolution** — Nested file edits resolving to `<workspace-root>/<basename>` ([#8606](https://github.com/QwenLM/qwen-code/issues/8606)) is a recurring pain point for monorepo and subdirectory workflows.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI (CodeWhale) Community Digest — 2026-08-06

---

## 1. Today's Highlights

The v0.9.4 integration train continues to accumulate commits across the runtime API surface, with a major push to expose memory, MCP server lifecycle, skill management, and verifier receipts via HTTP endpoints. Community momentum is also visible in the first Chinese Windows beginner guide and a fix for a ratatui version conflict causing startup crashes.

---

## 2. Releases

No new releases in the last 24 hours. The v0.9.4 release train (PR #5135) remains open and currently sits 77 commits ahead of `main`, consolidating all source candidates from the 2026-08-01 batch.

- [PR #5135 — Codewhale v0.9.4 release train](https://github.com/Hmbown/CodeWhale/pull/5135)

---

## 3. Hot Issues

**#4029 — Planning to create an interface similar to Reasonix?** · [Open] · Author: longASKme · Updated 2026-08-05 · 4 comments · [Link](https://github.com/Hmbown/CodeWhale/issues/4029)

The community is exploring whether CodeWhale could ship a Reasonix-like UI layer, signaling demand for richer visual context and reasoning workflows beyond the current TUI. Low engagement so far (0 👍), but the discussion has traction in comments.

---

## 4. Key PR Progress

### Runtime API Expansion (v0.9.4)

| PR | Author | Summary |
|----|--------|---------|
| [#5131](https://github.com/Hmbown/CodeWhale/pull/5131) | Copilot | Adds `/v1/memory` endpoints for bounded inspection and lifecycle controls of managed memory. |
| [#5130](https://github.com/Hmbown/CodeWhale/pull/5130) | Copilot | Exposes mutable MCP server configuration (`POST /v1/apps/mcp/servers`) so clients no longer need direct TOML/JSON edits. |
| [#5133](https://github.com/Hmbown/CodeWhale/pull/5133) | Copilot | Adds `/v1/threads/{id}/goal` endpoints for reading active goal state and driving lifecycle transitions. |
| [#5132](https://github.com/Hmbown/CodeWhale/pull/5132) | Copilot | Surfaces individual verifier receipts and evidence under `/v1/fleet/runs/{run_id}/`, enabling retry logic beyond aggregate counters. |
| [#5129](https://github.com/Hmbown/CodeWhale/pull/5129) | Copilot | Adds full skill lifecycle endpoints — install, update, uninstall, trust, and audit — behind `require_runtime_token`. |

### ACP & Tooling

| PR | Author | Summary |
|----|--------|---------|
| [#5225](https://github.com/Hmbown/CodeWhale/pull/5225) | rafaelcavalheri | Exposes file/search/git/patch/shell tools over the ACP `session/prompt` channel, enabling real code-editing for Zed and third-party bridges like `acp-deepseek-adapter`. |
| [#5240](https://github.com/Hmbown/CodeWhale/pull/5240) | SparkofSpike | Surfaces real wait elapsed time in tool content metadata so the model can distinguish short waits from long stalls and avoid busy-polling. |
| [#5242](https://github.com/Hmbown/CodeWhale/pull/5242) | SparkofSpike | Enables resuming interrupted subagent children from checkpoint via followup, fixing a dead-letter behavior for long-running multi-step tasks. |

### Bug Fixes

| PR | Author | Summary |
|----|--------|---------|
| [#5234](https://github.com/Hmbown/CodeWhale/pull/5234) | SparkofSpike | Fixes mouse-capture scroll hijacking by keeping alternate scroll mode off while capture is active (#5223). |
| [#5192](https://github.com/Hmbown/CodeWhale/pull/5192) | bistack | Pins `ratatui` to `=0.30.0` to avoid a blocking CPR query race in `Terminal::clear()` that crashes the TUI event loop at startup. |
| [#5095](https://github.com/Hmbown/CodeWhale/pull/5095) | shenjackyuanjie | Fixes OpenHarmony SDK builds where spaced paths broke linker argument quoting via `cmd %*` expansion. |

### Documentation

| PR | Author | Summary |
|----|--------|---------|
| [#5229](https://github.com/Hmbown/CodeWhale/pull/5229) | vFONGv | Adds a Chinese (zh-CN) Windows beginner guide covering installation, config, model switching, modes, permissions, and FAQs — validated on Windows 10 with real screenshots. |
| [#5236](https://github.com/Hmbown/CodeWhale/pull/5236) | Inference1 | Attaches live Model Studio evidence (terminal MP4 + token-plan screenshots) for PR #5203 proof. |

---

## 5. Feature Request Trends

1. **Full Runtime API surface** — The dominant trend is the community (via Copilot-authored PRs) pushing to expose every internal subsystem (memory, goals, skills, verifiers, MCP config) as REST endpoints, enabling managed client and web-dashboard integrations.
2. **ACP protocol maturity** — Making ACP a first-class agent bridge (PR #5225) reflects demand for CodeWhale to serve as a backend to editor-native agents (Zed, etc.) rather than a standalone CLI.
3. **Subagent reliability** — Checkpoint resume (PR #5242) and better wait-time signals (PR #5240) indicate users want long-running, interruptible subagent workflows to be robust and observable.
4. **Localized onboarding** — The zh-CN Windows guide (PR #5229) signals growing non-English user base needing region-specific setup paths.
5. **Reasonix-style visual UI** — Issue #4029 shows interest in a graphical reasoning/trace interface layered on top of the TUI.

---

## 6. Developer Pain Points

- **ratatui version drift** — The `ratatui` 0.31+ release introduced a blocking cursor-position query that races the TUI event loop, requiring an explicit pin to 0.30.0. This is a recurring dependency-compatibility frustration. ([PR #5192](https://github.com/Hmbown/CodeWhale/pull/5192))
- **Linker path quoting on Windows/ohos** — Spaces in SDK installation paths silently break the Rust→clang linker invocation on OpenHarmony targets. ([PR #5095](https://github.com/Hmbown/CodeWhale/pull/5095))
- **Scroll/input conflict during mouse capture** — When conversation transcripts overflow the terminal, mouse-wheel events toggle composer history instead of scrolling, degrading readability. ([PR #5234](https://github.com/Hmbown/CodeWhale/pull/5234))
- **ACP sessions lacking tool execution** — The ACP `session/prompt` endpoint previously streamed only model text, leaving editor bridges with a chat-only agent and no real editing capability. ([PR #5225](https://github.com/Hmbown/CodeWhale/pull/5225))
- **Subagent interrupts becoming permanent dead-letters** — Long-running child agents interrupted mid-task had no resume path, forcing full re-dispatch. ([PR #5242](https://github.com/Hmbown/CodeWhale/pull/5242))

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*