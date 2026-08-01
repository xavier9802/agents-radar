# AI CLI Tools Community Digest 2026-08-01

> Generated: 2026-08-01 03:33 UTC | Tools covered: 10

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
**Date: 2026-08-01**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in August 2026 is characterized by rapid feature convergence around agent reliability, cross-platform stability, and session persistence, while simultaneously fragmenting along architectural lines—daemon-based vs. single-process, sandboxed vs. open execution. The most active release cadences belong to OpenAI Codex and Gemini CLI, both shipping iterative fixes for fundamental reliability issues. Enterprise-grade concerns (permission management, SSO, resource tracking) are emerging as a distinct product frontier, particularly from Qwen Code's multi-workspace RFC and GitHub Copilot's organizational settings request. Safety and model-compatibility gaps remain the dominant source of community friction across nearly every tool.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Closed/Merged PRs | Releases (24h) |
|---|---|---|---|---|
| **Claude Code** | 9 | 5 | 2 | None |
| **OpenAI Codex** | 10 | 1 | ~18 | 3 alpha builds |
| **Gemini CLI** | 10 | 7 | 3 | 3 (nightly + 2 patches) |
| **GitHub Copilot CLI** | 10 | 2 | 0 | 1 (v1.0.78-0) |
| **Kimi Code CLI** | 4 | 1 | 0 | None |
| **OpenCode** | 10 | 6 | 3 | None |
| **Pi** | 10 | 4 | 6 | None |
| **Qwen Code** | 10 | 1 | 9 | 1 (v0.21.2) |

*Notes: PR counts reflect actively discussed/merged PRs in the digest window. OpenAI Codex shows the highest velocity with three alpha releases and ~18 merged PRs. Gemini CLI matches this with three release variants and active patching.*

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Need |
|---|---|---|
| **Session persistence & cross-device continuity** | Kimi Code CLI (#1282), Pi (#7396/#7409), OpenCode (server backend interest) | Resume sessions from any device; durable session storage across process restarts |
| **Multi-workspace / daemon architecture** | Qwen Code (RFC #6378/#8051), OpenCode (background commands #39978) | Single daemon managing multiple workspaces with bounded resource allocation |
| **Sandbox & permission hardening** | OpenCode (`OPENCODE_AIRGAP` #39994, permissions bypass #16331), DeepSeek (path whitelist #5005), Claude Code (`rm -rf` bypass #82165/#81273) | Configurable file-system allowlists, prevention of destructive command execution, air-gapped deployment |
| **Agent reliability & loop resilience** | Gemini CLI (subagent hangs #21409/#22323), OpenCode (debugging-loop detection #39990), Pi (compaction fixes #7420/#7421) | Subagents must surface failure states; agents must detect and break repetitive failure cycles |
| **Model-provider compatibility** | OpenCode (schema drift #18131), Kimi Code (double-encoded JSON #2572), Claude Code (Fable 5 provisioning #79337), Pi (provider SDK inconsistencies) | Stable tool-call contracts across non-Anthropic providers; consistent argument serialization |
| **Enterprise / organizational management** | GitHub Copilot (#3909), Qwen Code (RFC #8051), OpenCode (air-gapped deployment) | Centralized config, env var injection, and session tracking for team deployments |
| **Context management & token efficiency** | Claude Code (auto-memory #82056), OpenCode (prompt cache PRs #14743/#27378), Pi (compaction #6879) | Reducing redundant context loading, stabilizing prompt caches, intelligent session compaction |

---

## 4. Differentiation Analysis

| Dimension | Tools | Approach |
|---|---|---|
| **Release velocity** | OpenAI Codex, Gemini CLI | Rapid alpha/patch cadence; iterative fix-and-release cycles targeting core reliability |
| **Architecture philosophy** | Qwen Code, Pi, OpenCode | Moving toward daemon-based, multi-process, server-backed architectures for durability |
| **Security posture** | OpenCode, DeepSeek | Aggressive sandbox hardening (airgap switch, path whitelists) as a differentiator |
| **Model strategy** | Kimi Code CLI, DeepSeek TUI | Native DeepSeek model integration as core value proposition; OpenCode pursuing broad provider support |
| **Enterprise focus** | GitHub Copilot CLI, Qwen Code | Org-level config management, resource tracking RFCs, and auditability |
| **UX / TUI maturity** | OpenCode, Pi, DeepSeek | Heavy investment in TUI state management, plugin systems, and desktop parity |
| **Developer profile** | Claude Code | Focus on individual power users; deep VS Code/IDE integration; cross-platform session sync as top request |

---

## 5. Community Momentum & Maturity

**High momentum (rapid iteration):**
- **OpenAI Codex** — 3 alpha releases in 24h with ~18 merged PRs covering sandbox, approval policies, and thread management. Signals a team in active stabilization mode ahead of a minor release.
- **Gemini CLI** — Consistent patch cadence (v0.53.1, v0.54.0-preview.1, nightly v0.55.0) with targeted reliability fixes. Community engagement is strong on agent-subagent trust issues.

**Mature and stable:**
- **GitHub Copilot CLI** (v1.0.78-0) — Past initial launch turbulence; now in steady maintenance with incremental feature additions (`/permissions`, `closeSession`). The primary friction is regression management from version bumps.

**Emerging with strong community signal:**
- **Qwen Code** — The multi-workspace daemon RFC (#6378) with 31+ comments represents the most ambitious architectural discussion across all tools this cycle. Session branching (#8274) and resource tracking (#8051) indicate a community pushing toward production-grade multi-tenant usage.
- **OpenCode** — The stacked prompt-cache PR series (4 PRs targeting #5416/#5224) and the `OPENCODE_AIRGAP` feature show a community willing to contribute at depth, not just report issues. The DeepSeek V4 Flash support demand (#39823, 20 👍) reflects a model-aware user base.

**Niche but focused:**
- **Kimi Code CLI** — Smallest issue volume (4 hot issues) but the #1282/#1283 duo (23 👍) shows a clear, unified vision from a key contributor around cross-device continuity and persistent memory.

---

## 6. Trend Signals

| Signal | Evidence | Implication |
|---|---|---|
| **Session durability is table stakes** | Pi's server backend, Kimi's Remote Control + Memory System, Qwen's session branching | Tools that treat sessions as ephemeral will lose users to those offering durable, resumable, cross-device workflows |
| **Agent loops need self-correction** | OpenCode's debugging-loop detection, Gemini's subagent reliability issues, Pi's compaction fixes | The next frontier in CLI agents is not capability but *reliability*—agents that can detect and recover from their own failure modes |
| **Model-provider fragmentation is a systemic risk** | Double-encoded JSON (Kimi), schema drift (OpenCode), Fable 5 provisioning (Claude), missing thought signatures (Pi) | Tool vendors that abstract provider differences more effectively will win multi-provider deployments |
| **Enterprise deployment is emerging as a market segment** | GitHub Copilot #3909, Qwen Code multi-workspace RFC, OpenCode airgap support | The "single developer at a terminal" model is expanding to team and organizational contexts, creating demand for centralized management |
| **Windows-specific instability is universal** | GPU crashes (Claude, Codex), WSL regressions (Codex, Qwen), PATH corruption (DeepSeek), silent failures (Claude bash mode) | Windows remains the hardest platform across the ecosystem; tools with systematic Windows test coverage will have a reliability advantage |
| **Prompt cache determinism is a cost lever** | OpenCode's 4-PR stacked series, Claude Code's session sync request, Qwen Code's history consolidation bugs | Deterministic prompt caching directly reduces token costs; tools that solve this reliably will have a measurable economic advantage for power users |
| **Sandboxing is moving from optional to expected** | OpenCode airgap, DeepSeek path whitelists, Claude Code `rm -rf` bypasses | Security-conscious users expect sandboxing as a baseline; tools without configurable execution boundaries will face trust deficits in enterprise contexts |

---

*Report generated from community digest data current as of 2026-08-01.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-01 | Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

### #1 — `skill-creator` eval & trigger bug fixes (PR #1298, #1099, #1050, #1323, #1339)
**Status:** Open | **Focus:** Critical infrastructure for skill development
Multiple PRs target the `run_eval.py` / `run_loop.py` pipeline — the core toolchain for building and iterating on skills. The recurring bug: skills report `recall=0%` because trigger detection fails silently on both Unix and Windows. Related Windows fixes address subprocess encoding, `PATHEXT` handling, and pipe selection. This is the most-discussed cluster because it blocks the entire skill-improvement feedback loop.
- [PR #1298](https://github.com/anthropics/skills/pull/1298) · [PR #1099](https://github.com/anthropics/skills/pull/1099) · [PR #1050](https://github.com/anthropics/skills/pull/1050) · [PR #1323](https://github.com/anthropics/skills/pull/1323)

### #2 — `claude-api` context window exhaustion (Issue #1487)
**Status:** Open | **Focus:** Bundled skill performance
The `claude-api` skill eagerly injects ~156k tokens in a single tool call, exhausting the context window immediately. Raised as a blocker by a core-user contributor; reflects tension between bundled convenience and context efficiency.
- [Issue #1487](https://github.com/anthropics/skills/issues/1487)

### #3 — `document-typography` skill (PR #514)
**Status:** Open | **Focus:** Document quality
Prevents typographic defects (orphans, widows, numbering misalignment) in AI-generated documents. Addresses a pain point felt across all document generation workflows. No community comments yet but thematically high-value.
- [PR #514](https://github.com/anthropics/skills/pull/514)

### #4 — `skill-quality-analyzer` + `skill-security-analyzer` (PR #83)
**Status:** Open | **Focus:** Meta-tooling / governance
Two meta-skills that evaluate skills across five dimensions (structure, documentation, security, etc.) and flag security patterns. Directly addresses community concerns about skill trust boundaries.
- [PR #83](https://github.com/anthropics/skills/pull/83)

### #5 — `security` namespace impersonation (Issue #492)
**Status:** Open | **Focus:** Security / trust
Community report that unofficial skills are being distributed under the `anthropic/` namespace, impersonating official skills and requesting elevated permissions. 43 comments, 2 👍 — the highest-engagement security issue in the repo.
- [Issue #492](https://github.com/anthropics/skills/issues/492)

### #6 — `testing-patterns` skill (PR #723)
**Status:** Open | **Focus:** Software engineering
Comprehensive testing skill covering the Testing Trophy, AAA pattern, React Testing Library, and edge-case strategies. Fills a clear gap in the engineering toolkit.
- [PR #723](https://github.com/anthropics/skills/pull/723)

### #7 — `plan-file-hygiene` skill (PR #1479)
**Status:** Open | **Focus:** Agent workflow hygiene
Addresses accumulation of planning artifacts with no lifecycle management. Proposed by Palo Alto AI Research Lab; directly responds to community feedback on agent planning bloat.
- [PR #1479](https://github.com/anthropics/skills/pull/1479)

### #8 — `color-expert` skill (PR #1302)
**Status:** Open | **Focus:** Design / creative
Self-contained color expertise covering naming systems (ISCC-NBS, Munsell, XKCD, RAL), color spaces (OKLCH, OKLAB, CAM16), and practical selection guidance. Niche but indicates demand for domain-specialist skills.
- [PR #1302](https://github.com/anthropics/skills/pull/1302)

---

## 2. Community Demand Trends (from Issues)

| Demand Area | Key Issues | Sentiment |
|---|---|---|
| **Organization-wide skill sharing** | #228 (8 👍) | Strong — current manual transfer via Slack/Teams is painful |
| **Skill quality & security tooling** | #83, #492 | Critical — community wants built-in audit and trust verification |
| **Context efficiency** | #1487, #1175 | High — eager token injection in bundled skills is a known pain point |
| **Testing & QA coverage** | #723, #202 | Growing — demand for structured testing skills and creator best practices |
| **Cross-platform reliability** | #1061, #556 | Persistent — Windows support in skill-creator remains a gap |
| **MCP / API exposure** | #16, #29 | Aspirational — community wants skills as callable MCPs and Bedrock-compatible |

---

## 3. High-Potential Pending Skills

These active PRs are unmerged but have clear scope, community validation, and actionable proposals:

| PR | Skill | Why It May Land |
|---|---|---|
| [PR #1367](https://github.com/anthropics/skills/pull/1367) | **Self-audit** — mechanical file verification + four-dimension reasoning quality gate | Directly extends the `skill-quality-analyzer` meta-tooling vision; universal applicability |
| [PR #1479](https://github.com/anthropics/skills/pull/1479) | **Plan-file-hygiene** — lifecycle management for agent planning artifacts | Named the problem precisely by community; author is an org partner (PAIRL) |
| [PR #1261](https://github.com/anthropics/skills/pull/1261) | **Trigger-eval isolation** — isolates synthetic command files from live project registries | Fixes a real isolation bug that blocks parallel skill evaluation |
| [PR #539](https://github.com/anthropics/skills/pull/539) | **YAML description validation** — prevents silent truncation from special characters | One-line safety net; low risk, high reliability value |
| [PR #1302](https://github.com/anthropics/skills/pull/1302) | **Color-expert** — comprehensive color knowledge skill | Well-scoped, domain-specialist; reflects growing demand for niche expertise skills |
| [PR #525](https://github.com/anthropics/skills/pull/525) | **Pyxel retro game dev** — MCP-based pixel-art workflow | Unique creative-domain use case; low overlap with existing skills |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable skill evaluation tooling and trust guarantees** — not more skills, but tools that let developers *prove* a skill works correctly (trigger accuracy, context efficiency, security posture) before it ships.

The parallel clusters of `recall=0%` bugs, quality-analyzer proposals, namespace impersonation concerns, and context-exhaustion reports all point to the same friction: the skill lifecycle is immature, and the community is voting with its attention for better guardrails.

---



# Claude Code Community Digest — 2026-08-01

## 1. Today's Highlights

Fable 5 cost and auth bugs continue to dominate the issue tracker, with users on Max plans reporting silent model downgrades and misleading "usage credits required" errors across CLI, VS Code, and web environments. Simultaneously, a cluster of Windows-specific GPU crashes in Claude Desktop and multiple reports of safety-guard bypasses leading to destructive `rm -rf` execution are raising urgent stability and security concerns.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#79337](https://github.com/anthropics/claude-code/issues/79337) | Fable 5 prompts 'usage credits required' on Max plan | 51 | 20 | **Top issue.** Fable 5 became standard on Max on 2026-07-20, but the CLI silently downgrades to Opus 4.8 and blocks Fable 5 with a credit error. Affects core model routing on the flagship plan. |
| [#28791](https://github.com/anthropics/claude-code/issues/28791) | Sync conversation history between CLI and desktop | 30 | 111 | **Most upvoted open issue.** Long-standing feature request for cross-platform session continuity. Community strongly desires parity between CLI and desktop app. |
| [#11139](https://github.com/anthropics/claude-code/issues/11139) | Claude Code Web cannot use `gh` CLI (Permission Denied) | 28 | 31 | Web environment blocks `gh` auth, crippling GitHub-centric workflows. High impact for remote/cloud users. |
| [#79441](https://github.com/anthropics/claude-code/issues/79441) | VS Code extension blocks Fable 5 with "requires usage credits" | 13 | 10 | Duplicate/sibling of #79337 — confirms the bug spans both CLI and VS Code, suggesting a server-side provisioning issue rather than a client bug. |
| [#81159](https://github.com/anthropics/claude-code/issues/81159) | GPU process crash kills Claude Desktop during browser actions | 9 | 0 | Exit code `101457950` (0x60C201E) crashes the entire desktop app when Opus 5 performs in-page browser actions on Windows 11. |
| [#81275](https://github.com/anthropics/claude-code/issues/81275) | Browser pane crash — same GPU exit code on all renderers | 7 | 0 | Confirms #81159 is a systemic Chromium GPU issue, reproducing on Intel, NVIDIA, and WARP software rendering alike. |
| [#77768](https://github.com/anthropics/claude-code/issues/77768) | Recurring silent GPU crashes during web research (4–5×/day) | 5 | 1 | Same root cause as #81159/#81275 but on a different timeline — no crash dump, no recovery, making it extremely disruptive. |
| [#74113](https://github.com/anthropics/claude-code/issues/74113) | Background agents go idle without delivering final report | 5 | 5 | Agent `SendMessage` final reports are lost silently; a re-ping recovers them. Impacts reliability of autonomous agent workflows. |
| [#82165](https://github.com/anthropics/claude-code/issues/82165) | Agent-built command expanded to `rm -rf /*`, ran detached | 1 | 0 | **Critical safety incident.** Fable 5 in auto-mode on WSL2 constructed a cache-clearing command that expanded to root-wide deletion. Safety classifier then blocked kill attempts. |
| [#81273](https://github.com/anthropics/claude-code/issues/81273) | `rm -rf` inside backtick substitution bypasses auto-mode guard | 1 | 0 | Confirms a specific bypass vector: dangerous commands wrapped in backticks execute without the interactive confirmation prompt. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#82987](https://github.com/anthropics/claude-code/pull/82987) | Fix CI cron failures, exclude PRs, propose TUI latency fix | Open | Addresses scheduled job failures and proposes an architectural fix for TUI input latency degradation under high agent workloads (#82984). |
| [#82794](https://github.com/anthropics/claude-code/pull/82794) | Implement confidence scoring and `--threshold` flag for code-review | Open | Reconciles README drift in the `code-review` plugin: adds the documented 0–100 confidence scoring as a single validate-and-score pass. |
| [#39872](https://github.com/anthropics/claude-code/pull/39872) | Upgrade Node.js from 20 to 24 | Open | Preparation for upcoming LTS transition. Long-open PR, no merge yet. |
| [#81540](https://github.com/anthropics/claude-code/pull/81540) | Fix usage leak (#80705) | Closed | Automated contribution by Atlas 2; closes the usage-leak bug. |
| [#17776](https://github.com/anthropics/claude-code/pull/17776) | Add README for security-guidance plugin | Closed | Finalizes plugin documentation coverage. |
| [#82981](https://github.com/anthropics/claude-code/pull/82981) | (Unclear purpose) | Open | PR title appears truncated or auto-generated; lacks description. |

---

## 5. Feature Request Trends

- **Cross-platform session continuity** — The #28791 request for CLI/desktop history sync (111 👍) signals strong demand for a unified session experience across client types.
- **Intelligent context management** — Two related requests: pluggable context retrieval (#80751) and auto-memory load-status visibility (#82056) both reflect a desire for more transparent, configurable context control.
- **Cost-aware auto-mode workflows** — #77134 proposes surfacing Claude's authored text for approval without a second model pass, directly targeting token-cost reduction in remote/mobile scenarios.
- **Shell semantics consistency** — #74746 requests the Bash tool to run under actual `bash` rather than the user's login shell (`zsh`), addressing a frequent source of command failures.
- **Prompt suggestions in GUI** — #79919 highlights that ghost-text prompt suggestions work in CLI but not in desktop/web, suggesting feature parity gaps.

---

## 6. Developer Pain Points

1. **Fable 5 provisioning bugs** — The most urgent pain point. Max-plan users are blocked from using Fable 5 across all clients (CLI, VS Code, web), with silent downgrades to Opus 4.8 and misleading credit-error messages. A duplicate report (#82319, #82466) confirms the model-selection and fallback paths are both unreliable.

2. **Windows GPU instability in Claude Desktop** — A recurring crash loop (exit code `0x60C201E`) triggered by the in-app browser pane affects all GPU vendors. Multiple reports (#81159, #81275, #77768, #82962) describe total app death with no crash dump, making diagnosis impossible for users.

3. **Safety-guard bypasses in auto-mode** — Three independent reports (#80830, #81273, #82165) document `rm -rf` executing without confirmation, including a catastrophic `rm -rf /*` expansion. Backtick-substitution and detached command execution appear to bypass the auto-mode guard.

4. **Secret leakage from IDE state** — #71566 reports that closed, unsaved editor selections are injected into model context via `<ide_selection>`, leaking live credentials.

5. **Bash mode (`!`) silent failures** — #83046 documents that interactive commands (e.g., `sudo`) in bash mode exit with no output, prompt, or status — leaving users unable to distinguish success from failure.

6. **Session limit ambiguity** — #83042 highlights confusion around the 5-hour session window, with a single request consuming the entire allocation, suggesting unclear telemetry or accounting.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-01

## 1. Today's Highlights

Three alpha builds of the Codex Rust CLI shipped in the last 24 hours (0.147.0-alpha.1.1 through -alpha.4), signaling an active release cadence ahead of the next minor bump. Community attention is dominated by a high-engagement feature request to make auto-resolve of `request_user_input` explicit, and several Windows-specific regressions around WSL detection and sandboxed execution. Internally, the team is shipping foundational work on thread section management, paginated history, and strict auto-review for MCP elicitation approvals.

---

## 2. Releases

| Version | Notes |
|---|---|
| **rust-v0.147.0-alpha.4** | Latest alpha in the 0.147.0 track. |
| **rust-v0.147.0-alpha.3** | Preceding alpha; bundled with Codex App `26.721.3404.0`. |
| **rust-v0.147.0-alpha.1.1** | Earlier alpha in the 0.147.0 track. |

Three rapid-fire alpha releases suggest the team is iterating on sandbox, approval-policy, and V8-sandbox fixes before stabilizing the next minor. See the [GitHub releases page](https://github.com/openai/codex/releases) for full changelogs.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|---|---|---|
| [#28969](https://github.com/openai/codex/issues/28969) | Disable auto-resolve in 60 s for `request_user_input` | Current behavior silently auto-resolves unanswered prompts, causing agents to proceed with stale assumptions. A required `isBlocking` signal was recently landed in PR #36410; this issue tracks the UX/config surface. | 186 👍 / 64 comments — by far the most-discussed open issue. |
| [#35058](https://github.com/openai/codex/issues/35058) | Codex Diff crashes in VS Code on macOS | The diff tab is unusable across all repos after any edit, blocking a core review workflow. | 109 👍 / 42 comments. |
| [#34133](https://github.com/openai/codex/issues/34133) | Windows screenshot crashes GPU process | `Page.captureScreenshot` fails when Code Integrity rejects `vk_swiftshader.dll`, causing freezes or unopens on Windows. | 30 comments; 0 👍 (newer, niche). |
| [#35420](https://github.com/openai/codex/issues/35420) | Stream disconnects on OneDrive-backed Windows workspaces | OneDrive degradation leaks into Codex as repeated `"stream disconnected before completion"` errors, killing long-running agents. | 20 comments. |
| [#31786](https://github.com/openai/codex/issues/31786) | Remote control Windows → Android never connects | Pairing succeeds but the phone stays stuck on "connecting"; blocks mobile remote-use workflows. | 17 comments. |
| [#32323](https://github.com/openai/codex/issues/32323) | PR integration fails in WSL (`gh: Expected VAR_SIGN, actual: COLON`) | `gh` token/env parsing breaks Codex's PR workflow when run from WSL, blocking CI-adjacent automation. | 14 👍 / 12 comments. |
| [#35119](https://github.com/openai/codex/issues/35119) | 26.721.3404 marks valid WSL repos as non-Git | A regression in the latest MSIX build causes Codex to report `"Git is unavailable"` on WSL ext4 repos that worked in 26.715. | 11 👍 / 11 comments. |
| [#28316](https://github.com/openai/codex/issues/28316) | Large base64 image tool outputs persist in context | Images are resent on every subsequent turn, inflating token costs and hitting rate limits. | 10 comments / 3 👍. |
| [#35871](https://github.com/openai/codex/issues/35871) | Sandbox fails with MSIX PowerShell (`error 5`) | `CreateProcessAsUserW` refuses to launch the Store-bundled `pwsh` under the sandbox token, breaking exec in sandboxes. | 9 comments / 1 👍. |
| [#17401](https://github.com/openai/codex/issues/17401) | `@include` directive for composable `AGENTS.md` | Enables modular system prompts by resolving `@path/to/file.md` at assembly time — a foundational DX improvement for power users. | 15 👍 / 9 comments. |

---

## 4. Key PR Progress

| # | Title | Status | Description |
|---|---|---|---|
| [#36410](https://github.com/openai/codex/pull/36410) | Make user input blocking behavior explicit | ✅ Closed | Adds a required `isBlocking` field to `request_user_input`, decoupling the blocking decision from `autoResolutionMs`. Directly addresses [#28969](https://github.com/openai/codex/issues/28969). |
| [#36413](https://github.com/openai/codex/pull/36413) | Add realtime delegation acknowledgement control | ✅ Closed | Adds optional `delegationAckFiller` to `thread/realtime/start`; forwards `true`/`false` to V3 Frameless Bidi sessions. |
| [#36408](https://github.com/openai/codex/pull/36408) | Allow custom instructions for realtime transitions | ✅ Closed | Adds `realtimeStartInstructions` / `realtimeEndInstructions` to `thread/realtime/start`, letting users customize entry/exit prompts. |
| [#36409](https://github.com/openai/codex/pull/36409) | Implement remote plugin search | ✅ Closed | Implements `plugin/search` against the remote service (bypassing the catalog cache), supporting global/workspace/personal scopes. |
| [#36389](https://github.com/openai/codex/pull/36389) | Enforce single-writer ownership for all thread histories | ✅ Closed | Legacy thread histories now acquire the same writer lock as paginated histories, preventing concurrent-write races. |
| [#36385](https://github.com/openai/codex/pull/36385) | Add acknowledged user message submission to core | ✅ Closed | Adds `CodexThread::submit_user_input_and_wait_for_admission` and exports `UserMessageAdmission`, enabling the explicit-blocking path from PR #36410. |
| [#36384](https://github.com/openai/codex/pull/36384) | Load turn summaries with paginated queries | ✅ Closed | Joins summary-view item queries into the paginated turn query, eliminating one request per turn. |
| [#36380](https://github.com/openai/codex/pull/36380) | Add thread section management APIs | ✅ Closed | Introduces `threadSection/create`, `/update`, `/delete` with SQLite persistence and UUIDv7 identities — foundational for the sidebar section UI. |
| [#36374](https://github.com/openai/codex/pull/36374) | Enable sandboxed V8 for code mode | ✅ Closed | Forces the `v8_enable_sandbox` feature for Windows MSVC and package builds, closing a security gap in code-mode execution. |
| [#36373](https://github.com/openai/codex/pull/36373) | Add `--approve-for-me` CLI flag | ✅ Closed | Routes approval requests through automatic review for the invoking user; sets `approval_policy="on-request"` with `workspace-write` sandbox. |

*Also closed this cycle: [#36402](https://github.com/openai/codex/pull/36402) (declare experimental `plugin/search` API), [#36393](https://github.com/openai/codex/pull/36393) (avoid redundant filesystem probes), [#36388](https://github.com/openai/codex/pull/36388) (track image prep in turn analytics), [#36378](https://github.com/openai/codex/pull/36378) (load local session pickers from state DB), [#36372](https://github.com/openai/codex/pull/36372) (native Windows Bazel + MSVC), [#36367](https://github.com/openai/codex/pull/36367) (keep effective tool exposure in registry), [#36365](https://github.com/openai/codex/pull/36365) (strict auto-review for MCP elicitation), [#36411](https://github.com/openai/codex/pull/36411) (Git-repo pre-tool-hook test markers). Open PR: [#31471](https://github.com/openai/codex/pull/31471) (extract apps-cache logic into `ConnectorRuntimeManager`).*

---

## 5. Feature Request Trends

1. **Explicit, configurable `request_user_input` blocking** — The community overwhelmingly wants control over whether unanswered prompts auto-resolve. PR #36410 landed the protocol change; the next step is a user-facing config/flag.
2. **Modular prompt composition** — The `@include` directive for `AGENTS.md` (#17401) reflects demand for reusable, composable system-prompt fragments across projects.
3. **Per-thread auto-mode routing** — [#34278](https://github.com/openai/codex/issues/34278) asks for atomically setting both model and reasoning effort per thread, rather than globally.
4. **Enterprise SSO / MCP OAuth reliability** — [#35006](https://github.com/openai/codex/issues/35006) tracks end-to-end OAuth lifecycle improvements for corporate identity providers.
5. **Realtime-mode customization** — Two PRs this cycle (#36413, #36408) added delegation ack and custom transition instructions, signaling that power users want finer control over the realtime loop.

---

## 6. Developer Pain Points

- **Windows regressions are the top complaint.** Three separate issues this cycle — WSL repo detection broken in 26.721.3404 (#35119), sandbox `CreateProcessAsUserW` failure with MSIX PowerShell (#35871), and GPU crash on screenshot (#34133) — point to fragile integration between the MSIX packaging, sandbox token, and Windows subsystems.
- **Rate-limit and quota accounting bugs are frequent.** Multiple reports of incorrect weekly-usage tracking (#36353, #28331, #33216, #36369) and over-consumption during polling/wait loops (#35259) erode trust in the billing surface.
- **Base64 image bloat in context.** [#28316](https://github.com/openai/codex/issues/28316) describes unbounded token costs from re-sending full image payloads across turns — a performance and cost issue that affects any workflow involving screenshots or generated images.
- **Connectivity fragility on shared-storage workspaces.** OneDrive-backed repos (#35420) and WebSocket-to-HTTPS fallback (#15014) both cause silent stream disconnects that are hard to diagnose.
- **IDE-extension regressions.** The VS Code extension diff crash (#35058) and steer-message loss in the latest extension build (#36418) disrupt the two most common Codex entry points.

---

*Digest generated from [github.com/openai/codex](https://github.com/openai/codex) data current as of 2026-08-01.*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-01

## 1. Today's Highlights

The Gemini CLI team shipped two patch releases (v0.53.1 and v0.54.0-preview.1) cherry-picking the capacity-exhaustion terminal-state fix and the `InvalidStreamError` UI propagation fix from commit `f47d6c6`. A new nightly v0.55.0 also dropped with those same stabilizing changes. Meanwhile, the top community concerns remain agent reliability — subagent hangs, shell command stalls, and browser agent failures on Wayland continue to draw the most discussion.

---

## 2. Releases

**v0.55.0-nightly.20260801.gf47d6c6f7** — Nightly build carrying two core fixes:
- [Capacity exhaustion now classified as terminal](https://github.com/google-gemini/gemini-cli/pull/28599), preventing retry loops that hang the CLI when rate limits are hit.
- [InvalidStreamError details propagated to UI](https://github.com/google-gemini/gemini-cli/pull/28566), surface guidance such as recommending `/compress` when responses are empty due to context limits.

**v0.54.0-preview.1** — Preview patch created by cherry-picking commit `f47d6c6` onto `v0.54.0-preview.0` ([PR #28609](https://github.com/google-gemini/gemini-cli/pull/28609)).

**v0.53.1** — Stable patch with the same cherry-pick; merge conflicts were flagged and require manual resolution ([PR #28610](https://github.com/google-gemini/gemini-cli/pull/28610)).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports GOAL success after MAX_TURNS | Agent reliability: `codebase_investigator` masks turn-limit failures as success, silently hiding incomplete work. | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | Classic production blocker — simple tasks (folder creation) deadlock when deferring to the generalist. Workaround: disable subagents. | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & bash affinity | Envisions leveraging Gemini 3's native bash workflow while adding secure post-execution routing — a high-ambition architectural request. | 8 comments · 1 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Component-level eval infra | Tracking behavioral eval coverage (76 tests across 6 Gemini models) — critical for regression safety as the agent surface grows. | 7 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | Could reduce token waste and turn count by letting agents read method-boundary-aware code slices instead of raw line ranges. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills/subagents proactively | Anecdotal but widely felt — custom skills are ignored unless explicitly instructed, undermining the agent's autonomy. | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Memory system bug: sessions dismissed as low-signal are never marked processed, causing infinite re-surfaces. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Security concern — secrets may reach model context before redaction; background extractor also logs skill paths. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell execution stuck at "Waiting input" | Post-execution hang on simple commands that never prompt for input — breaks automated workflows. | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser agent fails on Wayland | Linux users on Wayland hit a hard blocker; browser subagent terminates immediately with GOAL without doing work. | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| # | Title | Status | Impact |
|---|-------|--------|--------|
| [#28613](https://github.com/google-gemini/gemini-cli/pull/28613) | Replace `console.error` with `debugLogger` in SDK session | Open · xs | Improves logging consistency across the SDK. |
| [#28607](https://github.com/google-gemini/gemini-cli/pull/28607) | Preserve `functionCall` `thoughtSignature` when stripping thoughts | Open · m | Fixes a v0.53.0 regression causing `API Error 400: Function call is missing a thought_signature` — high-priority correctness fix. |
| [#28526](https://github.com/google-gemini/gemini-cli/pull/28526) | Stop leaking `gemini.diff.accept` and `onDidChangeWorkspaceFolders` disposables | Open · s · pr-nudge-sent | Fixes resource leak in VS Code IDE companion caused by a stray parenthesis collapsing disposables into a comma expression. |
| [#28551](https://github.com/google-gemini/gemini-cli/pull/28551) | Fall back to embedded macOS Seatbelt profiles if missing | Open · l | Critical startup crash fix for sandbox mode (`-s`) on macOS/gMac where `.sb` profiles are absent from runfiles. |
| [#28566](https://github.com/google-gemini/gemini-cli/pull/28566) | Propagate `InvalidStreamError` details to UI | Merged | Surfaces actionable guidance (e.g., `/compress`) when empty responses stem from streaming errors. |
| [#28608](https://github.com/google-gemini/gemini-cli/pull/28608) | Fall back to stable models when preview model 404s | Open · m | Fixes auth flow for keys that lack preview-model access — prevents crashes on startup with `USE_GEMINI` auth. |
| [#28481](https://github.com/google-gemini/gemini-cli/pull/28481) | Refresh MCP OAuth tokens with stored client ID | Open · m · pr-nudge-sent | Fixes broken OAuth token refresh for dynamically-registered MCP servers; previously forced re-auth on every session. |
| [#28612](https://github.com/google-gemini/gemini-cli/pull/28612) | Bump version to 0.55.0-nightly.20260801 | Open · s | Automated nightly release bump. |
| [#28609](https://github.com/google-gemini/gemini-cli/pull/28609) | Cherry-pick `f47d6c6` to v0.54.0-preview.1 | Closed | Patch release automation for preview track. |
| [#28610](https://github.com/google-gemini/gemini-cli/pull/28610) | Cherry-pick `f47d6c6` to v0.53.1 | Closed (conflicts) | Patch release automation for stable track — merge conflicts require manual resolution. |

---

## 5. Feature Request Trends

- **Agent autonomy & subagent trust:** Multiple requests (#[21968](https://github.com/google-gemini/gemini-cli/issues/21968), #[22323](https://github.com/google-gemini/gemini-cli/issues/22323), #[22598](https://github.com/google-gemini/gemini-cli/issues/22598)) signal that the community wants agents to *reliably* discover and use skills/subagents on their own, with transparent trajectories.
- **AST-aware tooling:** Issues #[22745](https://github.com/google-gemini/gemini-cli/issues/22745) and #[22746](https://github.com/google-gemini/gemini-cli/issues/22746) reflect growing demand for semantic code understanding (method-boundary reads, codebase mapping) over naive line-based tools.
- **Sandboxing & security:** The zero-dependency OS sandboxing concept (#[19873](https://github.com/google-gemini/gemini-cli/issues/19873)) and Auto Memory redaction concerns (#[26525](https://github.com/google-gemini/gemini-cli/issues/26525)) point to a community that wants powerful agent capabilities with stronger security guarantees out of the box.
- **Destructive-operation guardrails:** Issue #[22672](https://github.com/google-gemini/gemini-cli/issues/22672) calls for the agent to discourage or block risky commands (e.g., `git --force`), a theme that recurs across agent tooling requests.

---

## 6. Developer Pain Points

1. **Subagent reliability** — The single largest pain cluster. Generalist hangs (#[21409](https://github.com/google-gemini/gemini-cli/issues/21409)), false GOAL successes (#[22323](https://github.com/google-gemini/gemini-cli/issues/22323)), and agents running without permission (#[22093](https://github.com/google-gemini/gemini-cli/issues/22093)) all point to an agent loop that doesn't yet handle its own failure modes gracefully.
2. **Shell/command execution stalls** — Commands completing but leaving the CLI in a permanent "Awaiting user input" state (#[25166](https://github.com/google-gemini/gemini-cli/issues/25166)) and interactive prompts freezing (#[22465](https://github.com/google-gemini/gemini-cli/issues/22465)) break automated and hand-off workflows.
3. **Browser agent platform gaps** — Wayland failure (#[21983](https://github.com/google-gemini/gemini-cli/issues/21983)) and ignored `settings.json` overrides (#[22267](https://github.com/google-gemini/gemini-cli/issues/22267)) leave Linux and power-user configurations unsupported.
4. **Auto Memory quality** — Infinite retry of low-signal sessions (#[26522](https://github.com/google-gemini/gemini-cli/issues/26522)), silent invalid patches (#[26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and redaction-after-context-leak (#[26525](https://github.com/google-gemini/gemini-cli/issues/26525)) form a coherent set of memory-system bugs that erode trust in persistent context.
5. **MCP & auth fragility** — Token refresh failures (#[28481](https://github.com/google-gemini/gemini-cli/pull/28481)) and preview-model 404s (#[28608](https://github.com/google-gemini/gemini-cli/pull/28608)) indicate the auth layer is brittle under non-standard key configurations.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-01

## 1. Today's Highlights

GitHub Copilot CLI **v1.0.78-0** shipped with a new `/permissions` command for switching between approval modes, ACP session-close support, and a sandbox cache optimization (`allowDevToolCaches`). The issue queue remains active with a regression in plan-mode shell blocking, a scheduled-prompt queue bug, and several new sessions/triage reports surfacing around version 1.0.74–1.0.78.

---

## 2. Releases

### v1.0.78-0
- **Added:** `/permissions` command to switch between approval modes
- **Added:** ACP mode now supports `closeSession` request to close sessions
- **Improved:** New sandbox setting `allowDevToolCaches` (on by default) grants sandboxed builds access to toolchain caches, registries, and installs

> See the release at [github.com/github/copilot-cli/releases](https://github.com/github/copilot-cli/releases)

---

## 3. Hot Issues

### #4188 — [CLOSED] Plan-mode regression: shell commands blocked
Regression in plan mode where shell commands (e.g., `gh` CLI) used to enrich plans are now blocked. 7 comments, 3 👍.
[View Issue](https://github.com/github/copilot-cli/issues/4188)

### #4305 — [CLOSED] JS undefined → Rust String crash on 1.0.76
Upgrading to 1.0.76 triggers a `Failed to convert JavaScript value 'Undefined' into rust type 'String'` error on nearly every command. 4 comments, 4 👍.
[View Issue](https://github.com/github/copilot-cli/issues/4305)

### #4078 — [OPEN] Scheduled prompts kill the existing prompt queue
When a scheduled prompt fires (`/every` or `/after`), it processes but does **not** continue the prompt queue, leaving remaining items stuck. 4 comments.
[View Issue](https://github.com/github/copilot-cli/issues/4078)

### #4161 — [CLOSED] `task_complete` tool unavailable after switching back to autopilot
Regression of #1523 — `task_complete` is missing after switching modes despite being documented as always available since v1.0.4. 4 comments, 4 👍.
[View Issue](https://github.com/github/copilot-cli/issues/4161)

### #3183 — [CLOSED] Orphan `tool_use` after hard-kill + resume causes persistent 400 errors
Long-lived sessions that are hard-killed and resumed leave orphan `tool_use` blocks in the persisted conversation, triggering `tool_use ids were found without tool_result blocks` errors. 4 comments.
[View Issue](https://github.com/github/copilot-cli/issues/3183)

### #3909 — [OPEN] Enterprise/org server-managed settings for local CLI
Org admins currently cannot centrally push config (especially env vars) to local CLI installs. This issue requests that capability, paralleling GitHub-hosted Agents/Codespaces secrets. 4 comments.
[View Issue](https://github.com/github/copilot-cli/issues/3909)

### #1352 — [OPEN] `sessionStart` hook stdout silently discarded
`sessionStart` hooks run but their output is never displayed in the terminal UI, blocking reminders, checklists, and banners at session start. 3 comments, 3 👍.
[View Issue](https://github.com/github/copilot-cli/issues/1352)

### #4251 — [OPEN] Resume of large sessions OOMs in 1.0.74 (regression vs 1.0.73)
A/B testing confirms resuming long-lived sessions now causes ~3–4× memory usage and a ~70 min grind or OOM in v1.0.74. 1 comment, 1 👍.
[View Issue](https://github.com/github/copilot-cli/issues/4251)

### #2109 — [OPEN] ACP `ask_user` / `ask_question` extension method
Request to add a dedicated user-question extension to ACP, beyond the existing `session/request_permission`, so custom clients can surface structured clarifying questions. 2 comments, 6 👍.
[View Issue](https://github.com/github/copilot-cli/issues/2109)

### #4311 — [OPEN] Transcript renders as blank lines until width change or new message
In interactive mode, the transcript blanks (bottom region) and stays blank until the user submits a new message or changes terminal width — `/resume` does not fix it. 1 comment.
[View Issue](https://github.com/github/copilot-cli/issues/4311)

---

## 4. Key PR Progress

### #3163 — ViewSonic monitor (Open)
Related to monitors #2591, #3561, #3559; initiates a GitHub action to provision runners.
[View PR](https://github.com/github/copilot-cli/pull/3163)

### #4316 — Create devcontainer.json (Open)
Adds a devcontainer configuration to the repo.
[View PR](https://github.com/github/copilot-cli/pull/4316)

> _Note: Only 2 PRs were updated in the last 24h. The issue list above captures the bulk of active community development discussion._

---

## 5. Feature Request Trends

1. **Enterprise / organizational management for local CLI** — Repeated requests (#3909) for org-admins to centrally manage settings and env vars for developers' local installs, matching the cloud-side secret model.
2. **ACP extensibility** — Beyond permission prompts, developers want richer ACP hooks: `ask_user` for clarifying questions (#2109) and token/context usage telemetry (#4174).
3. **Terminal UI / session navigation** — Requests for scrollable conversation history (#4313), arrow-key navigation in the session sidebar (#4304), and a dedicated pinned-sessions section in the left nav (#4321).
4. **Hook and rendering reliability** — `sessionStart` hook output visibility (#1352) and transcript repaint correctness (#4311) point to a broader desire for a more stable and predictable terminal interface.

---

## 6. Developer Pain Points

- **Regressions from version bumps:** The most common theme is that upgrading the CLI (especially to 1.0.74 and 1.0.76) introduces breaking behaviors — plan-mode shell blocking (#4188), `task_complete` vanishing after mode switches (#4161), large-session OOM on resume (#4251), and JS→Rust type crashes (#4305).
- **Scheduled prompt queue corruption:** Scheduled `/every` and `/after` prompts consume the queue but fail to resume it (#4078), a bug that directly impacts automated workflows.
- **Session durability:** Long-lived sessions face multiple failure modes — orphan `tool_use` after hard-kill (#3183), V8 string-length limits making sessions permanently unloadable (#4325), and plan review UI not reappearing after session switches (#4319).
- **MCP configuration fragility:** Comments in `.mcp.json` cause the entire file to be rejected (#4323), nested agent tool grants depend on undocumented parent behavior (#4320), and the interactive MCP wizard lacks env-var format help text (#1478).
- **Permission & autopilot enforcement:** Autopilot's task-completion logic can override explicit user instructions to limit scope to research/explanation only (#4318), and installing a specific CLI version in Docker currently always pulls the latest (#4317).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-01

## 1. Today's Highlights

The Kimi Code CLI community is actively pushing for cross-device continuity and persistent context, with two major enhancement requests from long-time contributor CatKang reaching updated status this week. A new PR addresses a Pydantic validation bug affecting tool-call argument parsing when providers double-encode nested JSON values.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**[#1282] Remote Control — Continue local sessions from any device** 👍 23
One of the most-upvoted open issues, this request calls for a Remote Control feature enabling users to resume local Kimi Code CLI sessions from phones, tablets, or browsers. The strong community support (23 👍, 9 comments) signals clear demand for workflow continuity beyond the desktop.
https://github.com/MoonshotAI/kimi-cli/issues/1282

**[#1283] Memory System — Persistent context across sessions**
CatKang's companion feature to #1282, proposing an AI-managed and user-defined memory layer so the CLI retains project patterns, preferences, and context between sessions. Still at 0 👍 but actively discussed (8 comments).
https://github.com/MoonshotAI/kimi-cli/issues/1283

**[#2422] Auto-scroll to bottom after conversation completes (Linux)**
A UX bug affecting Kimi Code CLI v1.46.0 on Linux, where manually scrolling up to review output triggers automatic re-scrolling to the bottom. Reported by venus0707 on 2026-06-04; still open after 2 comments.
https://github.com/MoonshotAI/kimi-cli/issues/2422

**[#796] LLM provider error: message at position 1 with role** ❌ Closed
A resolved issue from early 2026 involving a 400 error from the kimi-for-coding model during initial setup on macOS. Closed on 2026-07-31; useful as a reference for similar provider-configuration errors.
https://github.com/MoonshotAI/kimi-cli/issues/796

---

## 4. Key PR Progress

**[#2572] fix(kosong): recursively unwrap double-encoded JSON in tool-call arguments**
A new fix by aalhadxx addressing Pydantic validation failures in tools like `SetTodoList`, `ExitPlanMode`, and `StrReplaceFile`. The root cause: certain LLM providers (e.g., Moonshot API) return `function.arguments` with nested arrays/objects already JSON-stringified a second time, causing type mismatches. This PR recursively unwraps the extra encoding layer.
https://github.com/MoonshotAI/kimi-cli/pull/2572

---

## 5. Feature Request Trends

The dominant trend this period is **session persistence and portability**: users want Kimi Code CLI to behave as a continuous, cross-device assistant rather than a lock-step terminal tool. The two CatKang proposals (#1282 Remote Control, #1283 Memory System) together outline a vision for always-on, context-aware CLI sessions that follow the user across devices and over time. Secondary needs include input robustness (handling provider-specific JSON encoding quirks) and polished UX (scroll behavior fixes).

---

## 6. Developer Pain Points

- **Provider compatibility quirks**: The double-encoded JSON issue (#2572) highlights the friction of supporting diverse LLM backends with inconsistent argument serialization — a recurring pain point as the tool supports more providers.
- **Cross-device workflow gaps**: The high vote count on #1282 confirms developers are leaving their desks mid-session and losing context, pointing to a gap in mobile/tablet/browser access.
- **Session memory loss**: The absence of a persistent memory system (#1283) forces users to re-establish context every session, reducing productivity for long-running projects.
- **CLI UX polish**: Auto-scroll bug (#2422) reflects a broader need for refinement in the interactive terminal experience, especially on Linux.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-01

---

## 1. Today's Highlights

No new releases landed in the last 24 hours, but development activity remains intense with over 15 merged/closed PRs and 30+ active issues. The community is rallying around three major themes: **prompt cache stabilization** for Anthropic (multiple stacked PRs targeting issue #5416), **TUI plugin system hardening** (Kit Langton's series of fixes for desktop plugin discovery, runtime, and tab state), and **shell/agent loop improvements** (background command execution, debugging-loop detection, and concise error output). Additionally, DeepSeek V4 Flash's formal release has sparked significant discussion about native support.

---

## 2. Releases

No new releases published in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#16331](https://github.com/anomalyco/opencode/issues/16331) | Permissions ignored | 41 | 11 | Core security concern — file-level permission rules in `opencode.json` (e.g., deny `*.env`) are being bypassed, undermining the allow/deny model users depend on for sensitive-file protection. |
| [#39823](https://github.com/anomalyco/opencode/issues/39823) | DeepSeek V4 Flash formal version (0731) — is it live? | 23 | 20 | DeepSeek's July 31 formal release of V4-Flash (Terminal Bench 82.7, DeepSWE 54.4) has the community eager for native support. High interest signals strong demand for expanding model coverage beyond the preview. |
| [#18131](https://github.com/anomalyco/opencode/issues/18131) | Write tool called with invalid parameters | 12 | 4 | Recurring schema-validation failure when using Qwen 3.5 35B-A3B via LM Studio — highlights ongoing compatibility friction between OpenCode's tool contracts and non-Anthropic model providers. |
| [#28480](https://github.com/anomalyco/opencode/issues/28480) | OpenCode Windows 11 not starting anymore | 11 | 0 | Silent startup failure on Windows with no error output — a frustrating onboarding blocker that suggests an environment-specific initialization bug. |
| [#7769](https://github.com/anomalyco/opencode/issues/7769) | Support desktop version of git submodules | 9 | 13 | Desktop users cannot properly manage submodule sessions, creating a gap between TUI and GUI feature parity. Strong community endorsement (13 👍). |
| [#20527](https://github.com/anomalyco/opencode/issues/20527) | New PowerShell tool confuses agents | 7 | 2 | Post-PR #16069, agents on Windows still proactively use `tail` instead of PowerShell-native tooling — a regression in platform-appropriate shell behavior. |
| [#26558](https://github.com/anomalyco/opencode/issues/26558) | Git GUI for Commit, Staging, and Push Workflow | 6 | 4 | Feature request for an in-app lightweight Git UI (view, stage, commit, push) to reduce terminal dependency — reflects desktop users' desire for a more integrated IDE-like experience. |
| [#23595](https://github.com/anomalyco/opencode/issues/23595) | `<system-reminder>` keeps moving, breaking llama.cpp cache | 5 | 11 | Non-deterministic repositioning of `<system-reminder>` tags causes prompt-cache thrashing in llama.cpp, directly impacting latency and token costs for local-model users. |
| [#14848](https://github.com/anomalyco/opencode/issues/14848) | Billing sync lag and TUI session loss | 5 | 1 | After credit top-up, the TUI fails to reflect updated billing state and loses active sessions — a reliability gap in the Zen account-sync pipeline. |
| [#20989](https://github.com/anomalyco/opencode/issues/20989) | Random characters printed after exit | 4 | 2 | Terminal escape-sequence corruption on exit (Ctrl+C ineffective) leaves users with a broken terminal state, requiring manual process kill. |

---

## 4. Key PR Progress

| # | PR | Status | Description |
|---|-----|--------|-------------|
| [#39997](https://github.com/anomalyco/opencode/pull/39997) | `feat(opencode): dedup unchanged file reads` | 🟢 Open | Introduces a `file_unchanged` stub that short-circuits read calls when a file's contents are already in the context window and unchanged on disk — reduces redundant I/O and token usage. |
| [#39994](https://github.com/anomalyco/opencode/pull/39994) | `feat: add OPENCODE_AIRGAP` | 🟢 Open | Adds a single kill-switch env var (`OPENCODE_AIRGAP=1`) to disable all automatic internet access, enabling intranet and air-gapped deployments. |
| [#39978](https://github.com/anomalyco/opencode/pull/39978) | `feat(background): run long-running shell commands without blocking` | 🔴 Closed | Shell commands now run asynchronously; new HTTP API lets users list/cancel background jobs, and the TUI shows a badge when background activity is active. |
| [#39985](https://github.com/anomalyco/opencode/pull/39985) | `feat(app): configurable send key` | 🔴 Closed | Adds a Settings → General → Input option for Send key mode: **Enter** (default), **Shift+Enter**, or **Ctrl/Cmd+Enter** — improves workflow ergonomics for power users. |
| [#39389](https://github.com/anomalyco/opencode/pull/39389) | `fix(tui): prevent diff viewer re-entry` | 🟢 Open | Fixes the Diff Viewer's palette actions to match the current route, preventing re-entry loops when navigating from inside the viewer. |
| [#27378](https://github.com/anomalyco/opencode/pull/27378) | `fix(cache): stabilize system prefix` (behind `OPENCODE_EXPERIMENTAL_CACHE_STABILIZATION`) | 🔴 Closed | Part 3 of 4 in the prompt-caching stacked PRs — stabilizes the system prompt prefix to improve Anthropic prompt cache hit rates. |
| [#14743](https://github.com/anomalyco/opencode/pull/14743) | `fix(cache): improve Anthropic prompt cache hit rate` | 🟢 Open | Fixes cross-repo and cross-session prompt-cache misses by ensuring system prompt splitting and tool-call stability — closes #5416 and #5224. |
| [#39990](https://github.com/anomalyco/opencode/pull/39990) | `feat(session): inject debugging-loop hint` | 🟢 Open | Detects repeated failures of the same shell command across a conversation and injects a hint to break the agent out of hypothesis-cycling loops. |
| [#39988](https://github.com/anomalyco/opencode/pull/39988) | `fix(tui): discover plugins across config roots` | 🟢 Open | Expands TUI plugin discovery to the global config directory and every ancestor `.opencode/plugins/tui` — supersedes the narrower #39981. |
| [#39983](https://github.com/anomalyco/opencode/pull/39983) | `fix(tui): share runtime with external TSX plugins` | 🔴 Closed | External V2 TSX plugins now share the host TUI's OpenTUI/Solid runtimes, fixing the "frozen after first frame" bug in packaged Bun executables. |

---

## 5. Feature Request Trends

1. **Prompt Cache Reliability** — Multiple issues (#5416, #5224, #23595) and a 4-PR stacked series converge on making Anthropic prompt caching deterministic and cross-session. This is clearly a top-priority engineering effort.

2. **Local/Air-Gapped Deployment** — The `OPENCODE_AIRGAP` PR (#39994) and requests for WSL support (#30230), Termux compatibility (#30248), and local model integration (llama.cpp cache concerns) signal growing demand for running OpenCode in constrained or offline environments.

3. **Desktop GUI Polish** — Feature requests for Git workflow UI (#26558), git submodule support (#7769), configurable send keys (#39985), and transparency control (#5657) show the desktop team is actively expanding beyond terminal-centric workflows.

4. **Agent Loop Resilience** — Debugging-loop detection (#39990), concise error output for failed commands (#39982), and smart timeouts (#39978) reflect a trend toward making agents more self-correcting and less prone to repetitive failure cycles.

5. **Plugin Ecosystem Maturity** — The TUI plugin discovery and runtime fixes (#39988, #39981, #39983) and the request for custom side-effect slash commands (#30268) indicate the plugin system is moving from prototype to production readiness.

---

## 6. Developer Pain Points

- **Model-provider schema drift**: Multiple issues (#18131, #24604, #29142) report `write`/`edit` tool calls failing with `SchemaError` when using OpenAI-compatible or local models (Qwen, LM Studio). The tool contract appears to expect fields that some models consistently omit — a recurring friction point for non-Anthropic providers.

- **Windows-specific instabilities**: Silent startup failures (#28480), PowerShell tooling confusion (#20527), Nushell blacklist concerns (#20573), and WSL integration gaps (#30230) suggest the Windows experience needs systematic hardening.

- **TUI state hygiene**: Tab-reorder persistence bugs (#39942, #39941, #39940), symlink-path session loss (#30260), and project-list deduplication issues (#30223) indicate the Desktop TUI's state layer needs closer scrutiny for edge cases.

- **Directory/folder sync lag**: File-tree staleness after external edits (#30052) and `GET /session/status` no longer aggregating across subdirectories (#30094) point to reactivity gaps between the filesystem watcher and the UI layer.

- **Billing/session sync reliability**: Issue #14848 highlights that account updates (credit top-ups, limit changes) can take significant time to propagate to the TUI, and active sessions may be lost in the interim — a trust issue for paid users.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-01

## 1. Today's Highlights

The biggest news today is a cluster of bugfixes from **a-yeyang** addressing stalled availability refreshes, truncated compaction summaries, and dual compaction triggers — all critical reliability fixes for long-running sessions. Simultaneously, **christianklotz** shipped a major backend rewrite introducing a server session backend, per-session store queues, SQLite optimization, and remote session coordination, marking the largest architectural shift in recent months. A new **Baseten** provider and **direct image URL** support round out the day's feature additions.

---

## 2. Releases

No new releases published in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#6187](https://github.com/earendil-works/pi/issues/6187) | Pi login hangs in WSL after GitHub Copilot device auth | WSL + Copilot is a popular dev setup; authorization completes server-side but the client never detects it, leaving users stuck. | 19 comments, active investigation |
| [#6665](https://github.com/earendil-works/pi/issues/6665) | TUI pins a full core while streaming | Uncached `Intl.Segmenter` and per-chunk Markdown rebuild cause 100% CPU on one core during long streams — affects all users of extended sessions. | 11 comments, marked in-progress |
| [#7267](https://github.com/earendil-works/pi/issues/7267) | Custom provider docs vs. implementation mismatch | Critical discrepancy between `docs/custom-provider.md` and `pi-coding-agent` Extension API — extension authors cannot reliably build providers. | Closed; 8 comments |
| [#7020](https://github.com/earendil-works/pi/issues/7020) | Pi sometimes doesn't continue after compaction | Long-running "coordinator" sessions hit compaction warts where the agent stalls post-compaction, breaking workflow continuity. | 7 comments, 2 👍, in-progress |
| [#6879](https://github.com/earendil-works/pi/issues/6879) | Auto-compaction never triggers past 100% context | Context can exceed the window without compaction kicking in; only API rejection at 373k tokens forces it. Affects heavy agentic workloads. | 7 comments, 5 👍 |
| [#7161](https://github.com/earendil-works/pi/issues/7161) | Anthropic path missing `x-client-request-id` | Gateway session affinity breaks for Anthropic conversations; round-robin proxy setups can't group sessions correctly. | 6 comments |
| [#7319](https://github.com/earendil-works/pi/issues/7319) | Kimi-coding OAuth 401 stops the turn | No refresh-on-401 and 401 excluded from retry classifiers — intermittent auth failures halt entire turns for Kimi Code subscribers. | Closed; 5 comments |
| [#7301](https://github.com/earendil-works/pi/issues/7301) | Stalled availability refresh is permanently unrecoverable | `forceRefreshAvailability()` chains onto a stuck promise, so the runtime never recovers even after the underlying cause clears. | 3 comments; **fixed in PR #7421** |
| [#7290](https://github.com/earendil-works/pi/issues/7290) | `--mode json` emits O(n²) stdout for a single tool call | Every `message_update` carries the full cumulative assistant message, causing OOM on agents that generate large outputs (e.g., 64 KB HTML files). | 2 comments; **fixed in PR #7394** |
| [#7384](https://github.com/earendil-works/pi/issues/7384) | Concurrent writes to settings.json lose data | Two processes writing different settings concurrently can silently lose one update due to a race in `withLock()` before file creation. | Closed; 2 comments |

---

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#7421](https://github.com/earendil-works/pi/pull/7421) | Recover model availability after stalled refresh | **Fix** | Closes #7301. Breaks the promise chain so `forceRefreshAvailability()` always initiates a fresh rebuild instead of chaining onto a stuck one. |
| [#7420](https://github.com/earendil-works/pi/pull/7420) | Fail compaction when summary is truncated at token cap | **Fix** | Closes #7048. Previously `stopReason: "length"` was treated as success, persisting truncated summaries. Now correctly surfaces the failure. |
| [#7419](https://github.com/earendil-works/pi/pull/7419) | Normalize optional object tool schemas for OpenAI | **Fix** | Closes #7010. TypeBox omits `required` for all-optional objects, which strict OpenAI-compatible endpoints reject. The adapter now normalizes these schemas. |
| [#7422](https://github.com/earendil-works/pi/pull/7422) | Support direct image URLs in ImageContent | **Feature** | Closes #6151. Callers can now pass image URLs directly to providers that support them, avoiding unnecessary base64 fetch-and-encode. |
| [#7396](https://github.com/earendil-works/pi/pull/7396) | Add server session backend | **Feature** | Durable `@earendil-works/pi-coding-agent/server` backend persisting sessions as JSONL with cross-process locking and crash recovery. Major architecture addition. |
| [#7409](https://github.com/earendil-works/pi/pull/7409) | Add remote session client coordination | **Feature** | Introduces `PiClient` with connection ownership, idempotent disposal, shared/exclusive session leases, and server detach reconciliation. |
| [#7408](https://github.com/earendil-works/pi/pull/7408) | Add storage-owned session readers | **Feature** | Replaces eager `SessionSnapshot` loading with store-owned `SessionReader`, letting SQLite perform indexed reads while memory/JSONL use live arrays. |
| [#7398](https://github.com/earendil-works/pi/pull/7398) | Add per-session store queues | **Feature** | Serializes memory and JSONL ops per session while allowing unrelated sessions to progress concurrently; bounds JSONL filesystem concurrency to 4 ops. |
| [#7404](https://github.com/earendil-works/pi/pull/7404) | Add Baseten provider | **Feature** | New built-in OpenAI-compatible provider for Baseten-served models. Set `BASETEN_API_KEY` and use Baseten models via pi. |
| [#7394](https://github.com/earendil-works/pi/pull/7394) | Make JSON streaming output linear | **Fix** | Closes #7290. Emits delta-only `message_update` records in JSON/RPC modes, applies stdout backpressure, and preserves cumulative snapshots for internal handlers. |

---

## 5. Feature Request Trends

- **Provider expansion**: Continued demand for new built-in providers (Baseten just landed; Amazon Bedrock Mantle #6216 still open; Kimi K3 #7199 closed as done).
- **JSON/RPC mode improvements**: Multiple reports of O(n²) output and missing headers in JSON mode indicate users are pushing pi harder as a headless agent framework.
- **Server-side / remote session support**: The massive PR batch from christianklotz (server backend, remote coordination, per-session queues, storage-owned readers) signals strong community need for durable, multi-process session management.
- **Long-session reliability**: Compaction fixes, availability refresh recovery, and parallel tool-result handling (#7053) show users are running pi in extended agentic workflows that stress these subsystems.
- **Terminal / TUI parity**: Wayland clipboard (#7248), Orca terminal Kitty-image support (#7357), and input lag fixes (#7385) reflect ongoing investment in cross-platform TUI quality.

---

## 6. Developer Pain Points

1. **Compaction reliability**: A cluster of issues (#7020, #6879, #7253, #7413) around compaction — post-compaction stalls, auto-compaction not triggering, double-triggers, and GHE.com failures — indicates this is the #1 friction area for long-running sessions.
2. **Provider SDK inconsistencies**: Non-standard streaming responses (Gemini missing `thought_signature` #6996, Databricks array content #7062, Anthropic missing `x-client-request-id` #7161) force workarounds and break gateway integrations.
3. **Authentication edge cases**: OAuth refresh failures (Kimi 401 #7319), WSL login hangs (#6187), and enterprise stamp errors (#7413) show auth flows are fragile across provider and environment combinations.
4. **JSON mode scaling**: The O(n²) stdout bug (#7290) and related input lag (#7385) reveal that pi's JSON/RPC output path wasn't designed for high-throughput agent workloads — now being addressed (#7394).
5. **Concurrent write safety**: The `settings.json` race condition (#7384) and parallel tool-result loss (#7053) point to broader concurrency gaps as multi-process usage grows.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-01

---

## 1. Today's Highlights

Qwen Code v0.21.2 was released with a significant autofix improvement: the system now defers lower-severity suggestions after five rounds and posts visible notices when it refuses to proceed due to round limits ([#7913](https://github.com/QwenLM/qwen-code/pull/7913), [#8067](https://github.com/QwenLM/qwen-code/pull/8067)). Meanwhile, the community is actively shaping the future of multi-workspace daemon support through RFC [#6378](https://github.com/QwenLM/qwen-code/issues/6378) and a companion resource-tracking RFC [#8051](https://github.com/QwenLM/qwen-code/issues/8051), while a new session-branching feature with optional Git worktree isolation is taking shape ([#8271](https://github.com/QwenLM/qwen-code/issues/8271), [#8274](https://github.com/QwenLM/qwen-code/pull/8274)).

---

## 2. Releases

**v0.21.2** — Bug-fix and refinement release. See [release notes](https://github.com/QwenLM/qwen-code/releases).

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#6378](https://github.com/QwenLM/qwen-code/issues/6378) | RFC: Multiple workspaces in one daemon | The single most-discussed issue (31 comments) — proposes evolving the `1 daemon = 1 workspace` model to support multi-tenant daemons, a foundational architecture shift. |
| [#5199](https://github.com/QwenLM/qwen-code/issues/5199) | Minified React error #185 | High comment count (9) on a persistent UI rendering bug; affects CherryStudio-packaged builds on Windows. |
| [#8051](https://github.com/QwenLM/qwen-code/issues/8051) | Track multi-workspace daemon resource usage | Directly follows the RFC above; flags that count-only limits don't bound bytes held by request bodies and WebSocket assembly. |
| [#8039](https://github.com/QwenLM/qwen-code/issues/8039) | Anthropic 4.6+ assistant-prefill 400 | P1 bug affecting every Claude Opus/Sonnet 4.6+ and 5.x model; closed with a fix for prefill and `thinking.display` issues. |
| [#8182](https://github.com/QwenLM/qwen-code/issues/8182) | Daemon memory: each ACP child gets 50% of host memory | P2 bug where `getAcpMemoryArgs()` never divides the host memory ceiling by child count, risking OOM in multi-child setups. |
| [#8207](https://github.com/QwenLM/qwen-code/issues/8207) | JSON tool-call arguments leak as plain text | P2 production bug where long sessions cause the model to serialize tool arguments as raw text instead of structured `tool_call` objects. |
| [#8227](https://github.com/QwenLM/qwen-code/issues/8227) | Windows O_NOFOLLOW protection is vacuous | Security follow-up to [#7206]; the symlink/TOCTOU hardening doesn't work on Windows where `O_NOFOLLOW` doesn't exist, and it's untested. |
| [#8258](https://github.com/QwenLM/qwen-code/issues/8258) | Gemini history consolidation drops reasoning episodes | P2 bug where `geminiChat.ts` keeps only the first `thoughtSignature` per turn, silently dropping later reasoning in parallel tool-call scenarios. |
| [#7752](https://github.com/QwenLM/qwen-code/issues/7752) | Daemon writer-lifecycle P0 fix | All three P0 phases (managed shutdown, sealed handoff, session-maintenance isolation) are now merged; closes a critical daemon stability gap. |
| [#8003](https://github.com/QwenLM/qwen-code/issues/8003) | XML tool calls in long sessions | P2 bug where `qwen3.8-max-preview` outputs tool calls as raw `<invoke>`/`<parameter>` XML in 200+ turn sessions; closed with a fix. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#8274](https://github.com/QwenLM/qwen-code/pull/8274) | feat: fork from any conversation | Enables session branching from any visible Assistant response, not just the latest state — addresses tool-call safety concerns in branch-point selection. |
| [#8245](https://github.com/QwenLM/qwen-code/pull/8245) | feat(serve): resolve and report daemon memory budget | Gives the daemon a notion of its own memory budget by exposing RSS/heap samples and defining a `limits` field under `memory`. |
| [#8166](https://github.com/QwenLM/qwen-code/pull/8166) | fix(anthropic): cascade-strip stale thinking siblings | Fixes [#8159] by stripping orphaned `thinking`/`redacted_thinking` blocks when their paired `tool_use` is removed during history consolidation. |
| [#8215](https://github.com/QwenLM/qwen-code/pull/8215) | feat(review): Test Plan claim check, A/B harness | Adds three verification capabilities to `/review`: a test-plan claim check, base-tree A/B harness, and per-hunk probes for more rigorous PR review. |
| [#8240](https://github.com/QwenLM/qwen-code/pull/8240) | feat(workflows): bubble workflow agent approvals | Completes the foreground Dynamic Workflow permission path — shell/edit/MCP requests from nested workflow agents now surface through the parent TUI. |
| [#8141](https://github.com/QwenLM/qwen-code/pull/8141) | refactor(cli): remove ACP private serve dependencies | Relocates lifecycle-free ACP/daemon contracts from `packages/cli/src/serve/**` to `packages/cli/src/runtime/**` for cleaner module ownership. |
| [#7897](https://github.com/QwenLM/qwen-code/pull/7897) | fix(cli): skip terminal redraw on WSL/ConPTY | Fixes the streaming text-duplication bug on WSL + Windows Terminal where each character rendered N times due to ConPTY batched cursor-up processing. |
| [#8262](https://github.com/QwenLM/qwen-code/pull/8262) | fix(web-shell): isolate automatic recap by session | Prevents a recap generated for one Web Shell session from being inserted into another session's transcript; each request now records its owning session. |
| [#8272](https://github.com/QwenLM/qwen-code/pull/8272) | fix(vscode): traverse distinct resolved versions | Fixes the notices generator so packages at different resolved versions (e.g. `content-type@1.0.5` and `content-type@2.0.0`) are counted separately. |
| [#8251](https://github.com/QwenLM/qwen-code/pull/8251) | fix(webui): make long tool output collapsible | Replaces the 500-char hard truncation for Bash/Execute output with an expandable view, keeping full text available while collapsed by default. |

---

## 5. Feature Request Trends

- **Multi-workspace daemon architecture** — RFC [#6378](https://github.com/QwenLM/qwen-code/issues/6378) and its resource-tracking companion [#8051](https://github.com/QwenLM/qwen-code/issues/8051) represent the top-priority architectural feature request, with 40+ combined comments.
- **Session branching & fork-from-history** — [#8271](https://github.com/QwenLM/qwen-code/issues/8271) and [#8274](https://github.com/QwenLM/qwen-code/pull/8274) show strong community appetite for branching sessions at arbitrary conversation points, ideally with Git worktree isolation.
- **Skill lifecycle management** — [#8054](https://github.com/QwenLM/qwen-code/issues/8054) (disable all bundled skills) and the auto-skill curator PR [#7846](https://github.com/QwenLM/qwen-code/pull/7846) indicate demand for better skill discoverability and bulk configuration.
- **Native desktop shell** — PR [#8132](https://github.com/QwenLM/qwen-code/pull/8132) packaging the Web Shell as a release-ready Tauri app signals community interest in a standalone desktop experience.
- **Browser extension diagnostics** — PR [#6739](https://github.com/QwenLM/qwen-code/pull/6739) extending alpha readiness diagnostics suggests growing use of the browser automation path.

---

## 6. Developer Pain Points

- **Daemon memory management is fragile** — Multiple issues (#8182, #8051, #7752) point to the same root pain: the daemon lacks a coherent memory budget and per-child allocation logic, causing OOM risk in production multi-workspace setups.
- **Model format drift in long sessions** — Bugs #8003 (XML as plain text) and #8207 (JSON args leaked as text) both describe the model abandoning structured tool-call formats under context pressure, a recurring quality concern for production users.
- **Web Shell session isolation gaps** — Issues #8267 (SGR mouse escape sequences in input buffer) and #8214 (selected AI responses don't render visually) indicate the Web Shell TUI layer still has rendering and input-handling quirks.
- **CI E2E test flakiness** — Three separate CI failures (#8237, #8256, #8244) around cron, MCP server async handlers, and subagent delegation suggest integration test stability needs attention.
- **Windows-specific hardening gaps** — Issue #8227 highlights that security improvements (O_NOFOLLOW) are untested and ineffective on Windows, reflecting a broader pattern of platform-parity gaps in the security surface.
- **Anthropic API format compliance** — Issues #8039, #8159, #8160, #8161 (all closed) and #8258 (open) collectively point to persistent pain around the Anthropic converter's handling of tool-use IDs, thinking block ordering, and orphan cleanup across model versions.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI (CodeWhale) Community Digest — 2026-08-01

---

## 1. Today's Highlights

v0.9.3 shipped with DeepSeek V4 Flash support and canonical tooling; the legacy `deepseek-tui` npm package is now deprecated in favor of the `codewhale` command. The community is actively engaging on rendering fixes (circled digits, CRLF-heavy C files), Windows installer PATH preservation, and sandbox path-whitelist support for Xcode workflows.

---

## 2. Releases

**v0.9.3** — [PR #4993](https://github.com/Hmbown/CodeWhale/pull/4993)
- DeepSeek V4 Flash direct response integration
- Canonical tool dispatch and user-command shadowing semantics (Layer 5.2)
- 72 single-concern commits merged via fast-forward from clean lanes
- The legacy npm package `deepseek-tui` is deprecated; `codewhale` is the public product identifier going forward ([PR #4993 summary](https://github.com/Hmbown/CodeWhale/pull/4993))

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5007](https://github.com/Hmbown/CodeWhale/issues/5007) | Youtuber using Codex instead of CodeWhale for DeepSeek-v4-flash | Community visibility — a creator with an audience is demoing a competing TUI; raises awareness question around CodeWhale's positioning as the de facto DeepSeek CLI. |
| [#4949](https://github.com/Hmbown/CodeWhale/issues/4949) | Chinese translation of "Constitution" — 宪法 vs 协作准则 | Localization debate with cultural nuance; the author of PR #4908 reopened discussion after "宪法" (Constitution) sparked controversy over political connotations in Chinese. |
| [#5003](https://github.com/Hmbown/CodeWhale/issues/5003) | File `edit`/`patch` fails repeatedly on 700-line C files with CRLF + Chinese comments | Critical bug: 15+ failed tool attempts, 3 full `git checkout` rollbacks before a Python workaround. Directly impacts power-user workflows. |
| [#5005](https://github.com/Hmbown/CodeWhale/issues/5005) | Filesystem path whitelist for sandbox (Xcode DerivedData) | Sandbox `workspace-write` mode blocks access to external build artifacts; users need a allowlist to read Xcode logs outside the workspace. |
| [#5000](https://github.com/Hmbown/CodeWhale/issues/5000) | Interrupted assistant output should be a durable first-class session item | Engine-level gap: text emitted before `MessageComplete` is lost from the authoritative session, causing duplication on retry. |
| [#5002](https://github.com/Hmbown/CodeWhale/issues/5002) | `tool issue · Failed to locate tool: Tool 'task' is not available` | Runtime error when the `task` tool isn't registered; affects users expecting built-in task management. |
| [#5009](https://github.com/Hmbown/CodeWhale/issues/5009) | Ophthalmology billing spam | Noise; no technical relevance. |
| [#4382](https://github.com/Hmbown/CodeWhale/issues/4382) ✅ | Removed unmaintained `ttf-parser` / `lopdf` / `pdf-extract` dependency chain | Closed by maintainer — cleaned up a transitive dependency flagged by `RUSTSEC-2026-0192` (unmaintained, not vulnerable). |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5017](https://github.com/Hmbown/CodeWhale/pull/5017) | fix(ci): repair three shared check failures | 🔵 Open | Unblocks 7 dependabot + 2 community PRs by skipping the `closes-an-issue` gate for GitHub-verified bot accounts. |
| [#4981](https://github.com/Hmbown/CodeWhale/pull/4981) ✅ | feat(tui): LaTeX environments, text, and command support | 🔒 Closed | Full math rendering: environment blocks, inline commands, accents, sub/superscripts, case-insensitive matching. |
| [#4985](https://github.com/Hmbown/CodeWhale/pull/4985) | feat(runtime-api): scope task listing by workspace | 🔵 Open | Adds optional `workspace` filter to `GET /v1/tasks` and includes workspace path in `TaskSummary`; regression test included. |
| [#4992](https://github.com/Hmbown/CodeWhale/pull/4992) | Layer 5.2: User command dispatch precedence | 🔵 Open | Gherkin acceptance tests for user-command shadowing of built-ins/aliases, fallback semantics, and error handling for invalid commands. |
| [#5008](https://github.com/Hmbown/CodeWhale/pull/5008) | fix(tui): actionable File edit diagnostics + stale-line tolerance | 🔵 Open | Direct fix for [#5003](https://github.com/Hmbown/CodeWhale/issues/5003) — improves error messaging and tolerance for line-number drift during large patch operations. |
| [#5001](https://github.com/Hmbown/CodeWhale/pull/5001) | fix(tui): measure circled digits & keycaps as 2 columns | 🔵 Open | Fixes rendering glitches where `①②Ⓐ1️⃣` and similar Unicode were measured as 1 column instead of 2 in CJK terminals. |
| [#5006](https://github.com/Hmbown/CodeWhale/pull/5006) | fix(installer): preserve long Windows user PATH | 🔵 Open | NSIS `ReadRegStr` truncation caused the installer to overwrite existing long PATH values; now appends instead of replacing. |
| [#4977](https://github.com/Hmbown/CodeWhale/pull/4977) ✅ | fix(tui): AltGr-typed "/" reaches composer | 🔒 Closed | Fixes [#4723](https://github.com/Hmbown/CodeWhale/issues/4723) — on Windows ABNT2 layout, `AltGr+Q` was hijacked as `Ctrl-/` help chord; now routes to the input composer. |
| [#5013](https://github.com/Hmbown/CodeWhale/pull/5013) | chore(deps): bump ratatui 0.30.0 → 0.30.2 | 🔵 Open | Dependabot maintenance bump for the core TUI framework. |
| [#5016](https://github.com/Hmbown/CodeWhale/pull/5016) | chore(deps): bump libc 0.2.186 → 0.2.189 | 🔵 Open | Adds Emscripten pthread support; standard security/maintenance update. |

---

## 5. Feature Request Trends

1. **Sandbox flexibility** — Multiple issues (#5005) and PRs point to demand for configurable path allowlists so the workspace-write sandbox can access build artifacts, logs, and external toolchains (Xcode, etc.).
2. **CJK & Unicode rendering parity** — Issues around circled digits (#5001), CRLF + Chinese-comment file editing (#5003), and AltGr key routing (#4977) show sustained pressure to make CodeWhale behave identically across CJK and Western terminal configurations.
3. **Session durability** — The interrupted-output gap (#5000) reflects a broader expectation that the engine treats partial assistant output as a first-class, recoverable session artifact rather than transient display text.
4. **Workspace-scoped task API** — PR #4985 signals GUI client demand for `workspace`-filtered task listing, enabling multi-workspace IDE integrations.

---

## 6. Developer Pain Points

- **File tool edit/patch reliability** — Large replacements (100+ lines) on files with CRLF endings and non-ASCII content cause cascading failures with no actionable diagnostics. The workaround (external Python script) cited in [#5003](https://github.com/Hmbown/CodeWhale/issues/5003) is a red flag for production tooling.
- **Windows installer PATH corruption** — The NSIS installer overwrites long user PATH entries due to registry-read truncation ([#5006](https://github.com/Hmbown/CodeWhale/pull/5006)). High-impact for Windows users with existing toolchains in PATH.
- **Key-chord collisions on non-US layouts** — AltGr-derived characters being consumed by global shortcuts (e.g., `Ctrl-/` help) breaks typing flow for Brazilian ABNT2 and similar layouts ([#4977](https://github.com/Hmbown/CodeWhale/pull/4977)).
- **CI bottlenecks for bot-driven PRs** — The issue-link gate blocked all dependabot PRs until [#5017](https://github.com/Hmbown/CodeWhale/pull/5017) added a bot-type exemption, indicating a process gap in automation-friendly review workflows.
- **Missing tool registrations** — Runtime errors like `Tool 'task' is not available` ([#5002](https://github.com/Hmbown/CodeWhale/issues/5002)) suggest gap between documented tool surfaces and runtime availability, confusing end users.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*