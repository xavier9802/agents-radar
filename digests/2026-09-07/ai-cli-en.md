# AI CLI Tools Community Digest 2026-09-07

> Generated: 2026-09-07 04:04 UTC | Tools covered: 10

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



# AI CLI Tools Cross-Tool Comparison Report — 2026-09-07

## 1. Ecosystem Overview

The AI CLI tooling ecosystem is reaching maturity with eight major tools competing for developer mindshare, each exhibiting distinct community health profiles and technical trajectories. Platform compatibility—especially Windows regressions, line-ending normalization, and WSL support—is the dominant cross-cutting concern, while agent reliability (hangs, silent failures, recovery) and cost transparency (prompt caching, token tracking) are emerging as the next critical battlegrounds. Enterprise workflows are driving demand for features that smaller tools still lack: cross-device session continuity, repo-scoped plugins, fleet/model routing, and multi-agent collaboration infrastructure.

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Release Activity |
|------|-----------|---------|-----------------|
| **Claude Code** | 10 tracked | 10 (1 open, 9 closed) | None |
| **OpenAI Codex** | 10 tracked | 10 (all open/merged) | None (26.901.x cycle) |
| **Gemini CLI** | 10 tracked | 10 (3 open, 7 closed) | ✅ `v0.60.0-nightly.20260907` |
| **GitHub Copilot CLI** | 9 tracked | 1 (doc-only) | None |
| **Kimi Code CLI** | 4 tracked | 2 (both open) | None |
| **OpenCode** | 10 tracked | 10 (mixed) | None |
| **Pi** | 10 tracked | 10 (6 closed, 2 open, 2 closed) | None |
| **Qwen Code** | 10 tracked | 10 (mixed) | ✅ `v0.23.1-preview.1` + nightly |
| **DeepSeek TUI** | 10 tracked | 10 (mixed) | Preparing v0.9.13 |
| **Grok Build** | — | — | No activity |

## 3. Shared Feature Directions

| Direction | Tools | Specific Needs |
|-----------|-------|---------------|
| **Agent reliability & recovery** | Claude Code, Gemini CLI, OpenCode, Pi | Subagent hangs, silent MAX_TURNS failures, circuit breakers, graceful degradation |
| **Windows cross-platform parity** | Claude Code, Codex, Gemini CLI, OpenCode, DeepSeek TUI | Path separators, CRLF normalization, WSL support, bash-3 incompatibility, computer-use feature gaps |
| **Session continuity & portability** | Claude Code, Kimi Code, OpenCode, Pi | Cross-device resume, multi-account workflows, session migration, worktree awareness |
| **Cost transparency** | Codex, Gemini CLI, OpenCode, Pi, Qwen Code | Prompt caching (BYOK), accurate token counting, provider-reported cost, usage budget indicators |
| **MCP ecosystem maturity** | Claude Code, Gemini CLI, OpenCode, DeepSeek TUI | OAuth token reuse, skill discovery, config migration between tools, login-state visibility |
| **Plugin/tool ecosystem** | Claude Code, GitHub Copilot CLI, OpenCode | Repo-scoped plugins, marketplace reliability, per-call confirmation, skill configurability |
| **Context compaction reliability** | Claude Code, OpenCode, DeepSeek TUI | Configurable thresholds, behavioral-rule preservation, no-thrash compaction, cost-aware summarization |
| **Multi-agent collaboration** | Qwen Code, DeepSeek TUI | Mesh admission control, fleet model routing, agent turn boundaries, durable storage |

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi Code | Copilot CLI |
|-----------|------------|-------------|-----------|---------|-----|-----------|-------------|----------|------------|
| **Primary focus** | Enterprise CLI with strong CLI-first workflow | Desktop + CLI dual presence, computer-use | Research-grade agent with subagent architecture | Open-source, config-heavy, provider-flexible | Cross-provider TUI with fallback routing | Web Shell + mesh multi-agent | Rust-native TUI with fleet system | Growing ecosystem, planning workflows | GitHub-integrated, ACP mode |
| **Target user** | Enterprise/CI workflows | General developers, Windows users | Research, subagent power users | Linux/musl users, self-hosters | Multi-provider users, BYOK | Web-based collaboration | Rust developers, fleet ops | Emerging market, planning-heavy | GitHub orgs |
| **Technical approach** | TUI + memory compaction + plugin marketplace | Electron desktop + CLI + Remote SSH | Subagent orchestration + AST awareness | Go-based, extensive provider support | JS/TS, provider-agnostic with fallback | Rust, mesh admission, Web Shell | Rust, crate decomposition | TypeScript, MCP-first | TypeScript, GitHub-native |
| **Key differentiator** | Plugin marketplace, task tools | Computer-use on desktop | Subagent recovery, Node 22 sandbox | Alpine/musl support, OpenTUI migration | Cross-provider fallback, MagicDNS | Mesh multi-agent, Chrome Native Messaging | Fleet system, crate decomposition | Remote control vision | Repo-scoped plugins (just shipped) |

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **Gemini CLI** — Nightly releases, 7/10 PRs closed, active security hardening (EOL Node bump, git arg validation)
- **Qwen Code** — Dual release (preview + nightly), 10 PRs including multi-agent mesh foundation and Chrome Native Messaging
- **DeepSeek TUI** — Preparing v0.9.13 with 7 changelog receipts, aggressive bug-closure pace (6/10 issues closed)
- **Pi** — 6/10 PRs closed, strong founder-directed momentum on resilience features

**Steady maturation:**
- **Claude Code** — No releases but 9/10 PRs closed (mostly security/hook fixes); community pain points (compaction, hangs) are well-documented but slow to resolve
- **OpenCode** — Performance-focused PRs (persistence layer rewrite) address real bottlenecks; musl regression is a notable gap

**Slower cadence:**
- **OpenAI Codex** — No releases, Windows regression cluster in 26.901.x suggests release quality concerns
- **GitHub Copilot CLI** — Only 1 PR (documentation), 2 issues closed today but otherwise quiet; ACP security regression is unaddressed
- **Kimi Code** — Smallest issue tracker (4 tracked), 2 open PRs with modest community engagement

## 6. Trend Signals

1. **Agent reliability is the new feature arms race.** Communities across all tools are converging on subagent hangs, silent failures, and recovery mechanisms. Tools that solve this (Gemini CLI's subagent recovery, Pi's fallback routing, OpenCode's MCP loop circuit breaker) will gain enterprise trust.

2. **Windows is the universal stress test.** Every major tool has Windows-specific regressions this cycle—path separators, CRLF handling, computer-use gaps, bash-3 incompatibility. Tools with the strongest Windows story (Qwen Code's Native Messaging relay, DeepSeek TUI's P/Invoke fixes) signal maturity.

3. **Cost transparency is becoming a differentiator.** Prompt caching bugs (Copilot CLI's BYOK regression, OpenCode's Together AI zero-usage), inaccurate token counts (Codex Business tier draining 5–10× faster), and missing cost headers are eroding user trust. Tools that surface provider-reported costs (Pi's `usage.cost` PR, Qwen Code's spend indicators) are positioning for enterprise budgets.

4. **Multi-agent collaboration is moving from experimental to shipped.** Qwen Code's mesh admission foundation and DeepSeek TUI's fleet system indicate the market is shifting from single-agent CLI to coordinated multi-agent workspaces—a structural shift with long-term implications.

5. **Cross-tool interoperability is a rising demand.** Migration paths for MCP configs (Kimi Code), shared slash-command standards (`/goal`, `/plan`), and session portability (Kimi Code Remote Control) suggest users view these tools as a portfolio rather than standalone products, creating pressure for ecosystem-level standards.

**Recommendation for developers:** Prioritize agent reliability primitives (circuit breakers, recovery, explicit turn boundaries) and cost transparency over feature volume. Windows parity and multi-agent infrastructure are the two areas where community investment will most strongly correlate with enterprise adoption in H2 2026.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report

*Data as of 2026-09-07 · Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

| # | Skill | Description | Status |
|---|-------|-------------|--------|
| 1 | **skill-creator fixes** (PRs #1298, #1099, #1050, #539) | Fixes critical Windows subprocess/encoding bugs and a `run_eval.py` recall bug that caused all skill descriptions to score 0%. Part of an ongoing multi-PR debugging effort. | 🔴 All OPEN |
| 2 | **document-typography** (PR #514) | Prevents orphan lines, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a widely felt pain point in document production. | 🔴 OPEN |
| 3 | **Hivemind: Multi-Agent Orchestration** (PR #1628) | Delegates mechanical work to headless opencode workers on free models while Claude Code remains the sole planner/reviewer. Targets the "expensive model context is the scarce resource" problem. | 🔴 OPEN |
| 4 | **buffer-api Agent Skill** (PR #1627) | Portable GraphQL skill for scheduling and managing social media posts via Buffer's API. Designed to work across any agent (Claude, Cursor, Codex, etc.). | 🔴 OPEN |
| 5 | **self-audit** (PR #1367) | Pre-delivery quality gate: mechanical file verification + four-dimension reasoning audit. Universal across projects and tech stacks. | 🔴 OPEN |
| 6 | **skill-quality-analyzer & skill-security-analyzer** (PR #83) | Meta-skills for evaluating skill quality (structure, docs, examples, tests) and security (credential exposure, permission scope) across five dimensions. | 🔴 OPEN |
| 7 | **ServiceNow platform** (PR #568) | Broad ServiceNow assistant covering ITSM, ITOM, ITAM/SAM, FSM, Security Incident Response, and IntegrationHub. | 🔴 OPEN |
| 8 | **testing-patterns** (PR #723) | Comprehensive testing guidance covering the Testing Trophy, AAA pattern, React Testing Library, edge cases, and what *not* to test. | 🔴 OPEN |

> **Note:** All top PRs remain open. No merged items appear in the top-20 by discussion volume, indicating the community is actively debating before merge.

---

## 2. Community Demand Trends (from Issues)

| Trend | Evidence |
|-------|----------|
| **Org-wide skill sharing** | Issue #228 (16 comments, 8 👍) — users want a shared skill library or direct sharing link instead of manual .skill file distribution. |
| **Security & trust boundaries** | Issue #492 (43 comments, 2 👍) — the most-commented issue; community skills impersonating the `anthropic/` namespace is a top concern. |
| **Skill evaluation tooling** | Issue #556 (12 comments, 7 👍) + #1390 — `run_eval.py` and `evaluation.py` are unusable; community wants reliable quality gates. |
| **Context window efficiency** | Issue #1487, #1175 — skills that eagerly inject ~156k tokens or expose sensitive documents are flagged as harmful; demand for lazy-loading and scope-bounded skills. |
| **Agent governance & audit trails** | Issue #412, #1385 — proposals for policy enforcement, adversarial review, and pre-delivery reasoning quality gates. |
| **Compact/efficient memory** | Issue #1329 — demand for symbolic notation to reduce agent memory token bloat. |
| **Cross-platform skill packaging** | Issue #16, #29 — requests to expose skills as MCPs and support AWS Bedrock. |

---

## 3. High-Potential Pending Skills

These PRs have active community engagement and address clear pain points; they are the strongest candidates for imminent merge:

- **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — Fixes the skill-creator eval loop. Without this, the entire description-optimization pipeline is broken. Critical infrastructure fix.
- **[PR #514](https://github.com/anthropics/skills/pull/514)** — Document typography is a universal need; no existing skill addresses it. Low-risk, high-utility addition.
- **[PR #1628](https://github.com/anthropics/skills/pull/1628)** — Multi-agent cost optimization directly addresses the biggest user complaint about Claude Code pricing. Strong narrative.
- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit fills a gap in the delivery pipeline; pairs naturally with Issue #1385's quality gate proposal.
- **[PR #539](https://github.com/anthropics/skills/pull/539)** — YAML parsing guard prevents silent skill corruption. Small, defensive, high-impact.
- **[PR #1607](https://github.com/anthropics/skills/pull/1607)** — Retired model ID cleanup in `claude-api`. Low effort, high correctness value.

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **reliable evaluation and governance tooling** — not new domain skills, but the meta-infrastructure to verify that skills actually trigger, measure correctly, respect context budgets, and don't impersonate official Anthropic namespaces.

---



# Claude Code Community Digest — 2026‑09‑07

## 1. Today’s Highlights
No new releases were published in the last 24 hours. The community is actively tracking two high‑impact bugs: one where CVP‑approved organizations still receive cyber‑safeguard blocks, and another where Claude Code hangs on prompts for extended periods. Several feature requests around memory compaction, editor integration, and terminal graphics are gaining traction.

## 2. Releases
*No new releases in the last 24 hours.*

## 3. Hot Issues
| # | Title | Comments | 👍 | Why it matters |
|---|-------|----------|----|----------------|
| #84352 | CVP‑approved Claude.ai organization still receives cyber safeguard blocks | 197 | 27 | Directly impacts trusted enterprise users; verification status appears inconsistent between portal and CLI. |
| #26224 | Claude Code hanging/freezing on prompts for 5‑20+ minutes | 130 | 151 | Severe productivity blocker affecting long sessions; high community endorsement signals widespread pain. |
| #91188 | Make auto‑memory `MEMORY.md` compaction threshold configurable | 28 | 0 | Addresses recurring complaints about hardcoded context limits; enables power‑user customization. |
| #13517 | Custom `statusLine` command from `settings.json` not executed | 23 | 21 | Breaks expected TUI customization; affects macOS users relying on custom status displays. |
| #45810 | Marketplace update button disabled when update is available | 17 | 8 | Plugin workflow broken; users cannot refresh tools through the UI. |
| #80015 | Task‑list tools no longer exposed to the model after recent update | 14 | 13 | Regressions in core task‑management capabilities; affects any workflow relying on `TaskCreate/Update/List/Get`. |
| #82131 | Autocompact thrashing: context refills within 3 turns of previous compact | 12 | 1 | Shows instability in context‑window management; leads to excessive compaction cycles. |
| #76694 | Cowork: new projects lost “Choose a folder” after Chat/Cowork merge | 12 | 15 | Degrades collaboration experience; right‑click menu replaced with upload‑only knowledge picker. |
| #67500 | Context compaction recovery drops critical behavioral rules | 12 | 1 | Compaction silently loses session‑status blocks, memory writes, and no‑stop policies—undermining reliability. |
| #74662 | Allow opening/resuming local sessions across accounts in Desktop | 7 | 5 | Enables multi‑account workflows (personal/work) without manual session migration. |

**Links**  
[#84352](https://github.com/anthropics/claude-code/issues/84352) | [#26224](https://github.com/anthropics/claude-code/issues/26224) | [#91188](https://github.com/anthropics/claude-code/issues/91188) | [#13517](https://github.com/anthropics/claude-code/issues/13517) | [#45810](https://github.com/anthropics/claude-code/issues/45810) | [#80015](https://github.com/anthropics/claude-code/issues/80015) | [#82131](https://github.com/anthropics/claude-code/issues/82131) | [#76694](https://github.com/anthropics/claude-code/issues/76694) | [#67500](https://github.com/anthropics/claude-code/issues/67500) | [#74662](https://github.com/anthropics/claude-code/issues/74662)

## 4. Key PR Progress
| # | Title | Status | Why it matters |
|---|-------|--------|----------------|
| #87079 | `fix(security‑guidance): make ** glob patterns match zero‑depth paths` | OPEN | Fixes security‑rule bypass where top‑level files were excluded from pattern matching. |
| #68787 | `fix(scripts): add error message to edit‑issue‑labels.sh when called with no label arguments` | CLOSED | Improves CI/debugging by providing a clear error instead of silent exit. |
| #68786 | `fix(plugin‑dev): avoid shell injection in test‑hook.sh via stdin redirection` | CLOSED | Patches a potential command‑injection vulnerability in hook‑testing scripts. |
| #68785 | `fix(plugin‑dev): hook JSON to stdout, tighten su* glob, fix CI detection and JSON injection` | CLOSED | Corrects example hooks that wrote decision JSON to stderr, breaking parsing. |
| #68707 | `feat(bug‑reporter): add /bug command to file GitHub issues from the terminal` | CLOSED | Adds a native slash command for streamlined issue reporting. |
| #68702 | `fix(ralph‑wiggum): guard PROMPT_PARTS expansion against set -u on bash 3.x (macOS)` | CLOSED | Resolves macOS bash‑3 incompatibility that broke plugin setup. |
| #68701 | `fix(security‑guidance): strip CRLF from Python version probe on Windows` | CLOSED | Fixes Windows‑specific version comparison caused by CRLF line endings. |
| #68699 | `fix(hookify): add Python wrapper and normalize plugin root paths on Windows` | CLOSED | Addresses Windows path‑separator issues that prevented hookify from working. |
| #68694 | `fix(security‑guidance): normalize CLAUDE_PLUGIN_ROOT path separators on Windows` | CLOSED | Ensures security‑guidance hooks work correctly on Windows with backslash paths. |
| #68693 | `fix(scripts): add duplicate label additively, don’t replace existing labels` | CLOSED | Prevents accidental removal of platform/area/priority labels when closing duplicate issues. |

**Links**  
[#87079](https://github.com/anthropics/claude-code/pull/87079) | [#68787](https://github.com/anthropics/claude-code/pull/68787) | [#68786](https://github.com/anthropics/claude-code/pull/68786) | [#68785](https://github.com/anthropics/claude-code/pull/68785) | [#68707](https://github.com/anthropics/claude-code/pull/68707) | [#68702](https://github.com/anthropics/claude-code/pull/68702) | [#68701](https://github.com/anthropics/claude-code/pull/68701) | [#68699](https://github.com/anthropics/claude-code/pull/68699) | [#68694](https://github.com/anthropics/claude-code/pull/68694) | [#68693](https://github.com/anthropics/claude-code/pull/68693)

## 5. Feature Request Trends
- **Configurable memory compaction** – Users want the `MEMORY.md` compaction threshold to be adjustable (or suppressible) rather than hardcoded.
- **IDE/editor integration flexibility** – Requests to disable automatic editor‑group locking in VS Code and to support terminal graphics protocols for inline image display.
- **Multi‑account & session management** – Desire for Desktop to allow opening/resuming local sessions across different claude.ai accounts without manual migration.
- **Task‑tool restoration** – Strong interest in re‑exposing `TaskCreate/Update/List/Get` tools that were inadvertently removed in a recent update.
- **Plugin marketplace reliability** – Fixing broken update‑button states and ensuring sync/download cycles work correctly in per‑workspace plugin stores.

## 6. Developer Pain Points
- **Context‑compaction instability** – Multiple reports that compaction either thrashes (refills context within a few turns) or drops critical behavioral rules (session status, memory writes, no‑stop policies).
- **Bash‑tool environment bloat** – On Windows, the `CLAUDE_ENV_FILE` grows unboundedly across compactions, causing long sessions to fail with “command not found” errors.
- **Security‑safeguard false positives** – Approved organizations (CVP) still receive cyber‑safeguard blocks, creating confusion and support overhead.
- **Windows compatibility regressions** – Path‑separator issues, CRLF line‑ending mismatches, and bash‑3 incompatibilities continue to surface in plugins and hooks.
- **Plugin marketplace UX** – Update buttons are sometimes disabled, and sync indicators show green while downloads never complete, leaving users without clear error feedback.

---

*Digest generated from GitHub data for `anthropics/claude-code` as of 2026‑09‑07.*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — September 7, 2026

---

## 1. Today's Highlights

A cluster of Windows and VS Code extension regressions in the 26.901.x release cycle dominates the conversation, with the `chatgpt.openSidebar` command failure affecting multiple users simultaneously. Meanwhile, community heat remains on long-standing Windows UI gaps and a high-profile rate-limit anomaly that has Business subscribers reporting 5–10× faster usage depletion than Plus.

---

## 2. Releases

**No new releases in the last 24 hours.** The latest active builds referenced in issues are `26.901.x` (Windows desktop) and VS Code extension `26.901.22334`.

---

## 3. Hot Issues

1. **[Bug, Windows] Missing "Control Other Devices" tab in Settings** (#28919) — 63 comments, 59 👍
   The longest-running Windows-specific complaint: the Remote Control connection tab is absent from the Settings UI. Community impact is high because it blocks the computer-use workflow entirely on Windows.

2. **[Bug, App] Codex CLI binary not found / Electron resources missing bin/codex** (#22423) — 31 comments, 2 👍
   Users with WSL setups report the app refuses to launch, pointing to a packaging regression in how the Electron binary bundle is resolved at runtime.

3. **[Bug, Windows] Paginated thread history stalls on duplicate ordinal** (#41079) — 30 comments, 3 👍
   A local history-projection bug where newer messages exist in the canonical JSONL but never appear in the UI. Relevant to anyone with long-lived threads on Windows.

4. **[Bug, Windows] Pets do not respond to clicks or drag input** (#41960) — 20 comments, 24 👍
   The desktop "pets" feature is entirely non-interactive on Windows 11. Surprisingly high engagement for an UI nicety, indicating community expectation for the feature.

5. **[Bug, Remote SSH] VS Code extension fails to activate on Node 22 `using` syntax** (#42663) — 10 comments, 5 👑
   The 26.5901.22334 release uses top-level `using` declarations incompatible with the Node 22 runtime bundled with Remote SSH servers, blocking the extension on Linux hosts.

6. **[Bug, Windows] 26.901.1978.0 fails to launch — `cua_node` staging copy failure** (#42501) — 10 comments, 1 👍
   Microsoft Store users on 26.901.1978.0 see `ChatGPT.exe` processes spin up but no window appears; the `cua_node` runtime copy fails silently during staging.

7. **[Enhancement] Allow existing threads to update working directory after project rename** (#26836) — 9 comments, 5 👍
   A practical quality-of-life request: renamed folders leave threads pointing at stale CWDs, causing "directory missing" errors mid-session.

8. **[Bug, Rate-Limits] Business usage drains 5–10× faster than Plus** (#23671) — 8 comments, 5 👍
   Controlled reproduction shows identical GPT-5.5 tasks consuming far more tokens on Business than Plus. High concern for enterprise teams budgeting usage.

9. **[Bug, macOS] Ghost conversations persist in sidebar after deletion** (#41987) — 7 comments, 0 👍
   Deleted chats remain visible in the Recent list. Likely a caching/invalidation bug in the sidebar state sync.

10. **[Bug, CLI] GPT-6 Astra flags benign prompts as policy violations** (#43058) — 6 comments, 0 👍
    Isolated CLI reproductions report `invalid_prompt` on harmless requests like summarization, suggesting a model-level false-positive regression in the safety filter.

---

## 4. Key PR Progress

1. **Enable remote named permission profile selection in the TUI** (#43340) — Allows TUI users to select remote permission profiles, previously only available from the app server.
2. **Preserve saved permissions when resuming or forking remote tasks** (#43330) — Fixes a bug where local permission overrides clobbered remote server settings during resume/fork.
3. **Sort JSON schema object keys for consistent Cargo/Bazel output** (#43325) — Dedupes build artifacts across toolchains by stabilizing schema key order.
4. **Resolve session labels uniquely before acting on them** (#43315) — Prevents targeting the wrong conversation when duplicate labels exist; also fixes session command preview handling.
5. **Replace Windows app-server shutdown files with socket requests** (#43308) — Moves Windows server teardown to a cleaner `/daemon/shutdown` socket protocol with PID acknowledgment.
6. **Isolate Bazel build commit metadata from Rust compilation inputs** (#43304) — Prevents workspace status stamping from invalidating remote cache hits across developers.
7. **Defer managed worktree transitions to fresh TUI loop iterations** (#43298) — Splits synchronous `ChatWidget` work off the event loop to avoid blocking UI during worktree setup.
8. **Add capability-gated MCP user-verification handling** (#43289) — Routes `openai/userVerification` requests through `openai/elicitation/create` when the client advertises the capability.
9. **Add a managed worktree browser to the TUI** (#43286) — New `/worktree` browse subcommand listing repository checkouts with owner metadata and resume/copy actions.
10. **Connect voice-host RTP audio to speaker playback** (#43248) — Fixes the voice host draining RTP packets without playback by adding a GStreamer pipeline with jitter buffering.

---

## 5. Feature Request Trends

- **Project-aware session management** — Multiple issues (#26836, #43315) highlight demand for sessions that track and adapt to filesystem changes (renamed folders, linked worktrees) without manual reconfiguration.
- **Remote task fidelity** — PRs #43340 and #43330, alongside issue #42663, show sustained pressure to make remote-SSH and remote-task behavior parity with local sessions, especially around permissions and profile selection.
- **Voice UX reliability** — Issues #43226 (floating orb stuck) and the RTP playback fix in PR #43248 indicate the voice interaction layer needs continued polish on Windows.
- **Computer-use parity across platforms** — The missing Control Other Devices tab (#28919), non-responsive pets (#41960), and Danea Easyfatt window enumeration gap (#27874) all point to Windows computer-use as an area where feature completeness lags behind macOS.

---

## 6. Developer Pain Points

- **Windows UI regressions in 26.901.x** — At least five distinct issues (#41079, #41960, #42501, #43226, #42493) cluster around the latest Windows desktop build, suggesting the release introduced regressions in rendering, input handling, and process lifecycle.
- **VS Code extension sidebar broken** — Three closed issues (#42882, #42969, #43085) report the same `command 'chatgpt.openSidebar' not found` error after updating to 26.901.22334, a clear extension packaging regression.
- **Rate-limit and usage accounting inconsistency** — Issues #23671, #43341, and #43136 describe three distinct but related frustrations: Business tier draining faster, capacity errors on GPT-5.6 Sol, and sessions pinned to the wrong rate-limit bucket.
- **Model safety-filter false positives** — Issues #43058, #43237, and #43321 report benign prompts being rejected by GPT-6 Astra and GPT-5.6 Sol, pointing to a model-side regression in the policy classifier.
- **Long-lived thread history corruption** — Issues #41079 and #43124 both describe projection stalls on macOS/Windows where older message ordinals block newer history from rendering, a structural bug in the local transcript migration path.

---

*Digest generated from github.com/openai/codex issue and PR data as of 2026-09-07.*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-07

## 1. Today's Highlights

A new nightly release `v0.60.0-nightly.20260907` shipped with fixes for session deletion safety, line-ending normalization in diff snippets, and an EOL Node.js sandbox image upgrade. Enterprise Workspace authentication remains the top community concern with 35 comments, while the generalist agent hang and subagent recovery issues continue to dominate open bug discussions.

---

## 2. Releases

**v0.60.0-nightly.20260907.g85aca163f**
- Automated nightly bump; see changelog: [compare](https://github.com/google-gemini/gemini-cli/compare/v0.60.0-nightly.20260906.g85aca163f...v0.60.0-nightly.20260907.g85aca163f)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#29101](https://github.com/google-gemini/gemini-cli/issues/29101) | Authentication failure blocking Enterprise Workspace accounts | Blocks enterprise users from signing in after previously working setups; P1 triaged. | 35 comments · 2 👍 |
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Subagent silently hides interruption, causing incorrect results — critical for agent reliability. | 13 comments · 2 👍 |
| [#29133](https://github.com/google-gemini/gemini-cli/issues/29133) | `--list-sessions` never marks current session | Can accidentally delete the active session via `--delete-session`; a fix PR [#29134](https://github.com/google-gemini/gemini-cli/pull/29134) is open. | 9 comments |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model's bash affinity via Zero-Dependency OS Sandboxing | Proposes aligning with Gemini 3's native bash capabilities while maintaining security — large-effort enhancement. | 9 comments · 1 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs forever | Simple tasks like folder creation hang indefinitely when deferring to the generalist agent; 8 upvotes signal widespread impact. | 8 comments · 8 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and codebase mapping | Could reduce turn count and token noise by reading precise method bounds — tracked as an EPIC. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Anecdotal but broadly felt: custom skills are ignored unless explicitly prompted. | 6 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduce Auto Memory logging | Secrets may already be in model context before redaction occurs — security-critical for Auto Memory. | 5 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck "Waiting input" after completion | Repeatedly reported; simple CLI commands hang showing active shell state post-exit. | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Linux Wayland users cannot use the browser agent; tagged as P1. | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#29134](https://github.com/google-gemini/gemini-cli/pull/29134) | Protect current session from deletion | 🟢 Open | Fixes [#29133](https://github.com/google-gemini/gemini-cli/issues/29133) by passing active session ID through list/delete paths with suffix matching. |
| [#29132](https://github.com/google-gemini/gemini-cli/pull/29132) | Normalize line endings in diff context snippets | 🟢 Open | Normalizes CRLF/CR before computing diff context, preventing full-file diff dumps on Windows. |
| [#29131](https://github.com/google-gemini/gemini-cli/pull/29131) | Normalize line endings in `getDiffContextSnippet` | 🟢 Open | Companion fix for CRLF vs LF mismatch causing 100% file dumps into model context. |
| [#28975](https://github.com/google-gemini/gemini-cli/pull/28975) | Keep glob results for symlinked workspace roots | ✅ Closed | Fixes `No files found` on macOS `/tmp` (symlink to `/private/tmp`). |
| [#28971](https://github.com/google-gemini/gemini-cli/pull/28971) | Keep truncated MCP tool names unique | ✅ Closed | Fixes injective-name collision when qualified MCP tool names exceed the 30+30 char limit. |
| [#28983](https://github.com/google-gemini/gemini-cli/pull/28983) | Detect mixed line endings instead of flagging CRLF | ✅ Closed | `detectLineEnding()` no longer classifies mixed files as CRLF on a single match. |
| [#28973](https://github.com/google-gemini/gemini-cli/pull/28973) | Bump sandbox image to node:22-slim | ✅ Closed | Addresses EOL security risk — Node 20 reached end-of-life on 2026-04-30. |
| [#28972](https://github.com/google-gemini/gemini-cli/pull/28972) | Guard `formatTruncatedToolOutput` against non-positive `maxChars` | ✅ Closed | Prevents corrupt output when `maxChars ≤ 0` silently produces negative slice indices. |
| [#29184](https://github.com/google-gemini/gemini-cli/pull/29184) | Validate git args in Windows sandbox | 🟢 Open | Blocks silent `git diff --output` truncation attacks on Windows read-only commands. |
| [#29106](https://github.com/google-gemini/gemini-cli/pull/29106) | Flush final SSE event on EOF | ✅ Closed | Fixes lost `finishReason`/usage metadata when streams end without a trailing blank line. |

---

## 5. Feature Request Trends

1. **Agent reliability & self-correction** — Multiple requests address subagent hangs, recovery after turn limits, and better use of skills/sub-agents (#22323, #21409, #21968). The community wants agents that recover gracefully and use their tooling proactively.
2. **AST-aware codebase understanding** — Two linked issues (#22745, #22746) explore AST-based file reads and codebase mapping to reduce token waste and improve precision.
3. **Security hardening** — Deterministic redaction (#26525), git arg validation on Windows (#29184), and Auto Memory patch quarantine (#26523) show sustained demand for stronger security posture.
4. **Cross-platform & environment resilience** — Wayland browser support (#21983), symlink handling (#28975), and line-ending normalization (#29131, #28983) reflect ongoing investment in platform parity.
5. **Subagent visibility** — Sharing subagent trajectories via `/chat share` (#22598) and including subagent context in bug reports (#21763) indicate a desire for better observability into multi-agent workflows.

---

## 6. Developer Pain Points

- **Session management fragility:** `--delete-session` can erase the live session (#29133), and `/compress` state doesn't persist across resume (#21335).
- **Agent hangs and silent failures:** The generalist agent hangs indefinitely (#21409), and subagents mask MAX_TURNS as success (#22323) — both erode trust in automated workflows.
- **Enterprise auth instability:** Workspace authentication failures (#29101) directly block professional users, with the highest comment volume of any open issue.
- **Line-ending & path resolution bugs:** CRLF handling causes full-file diffs on Windows (#29131), and symlinked workspaces return empty glob results (#28975).
- **Skill/sub-agent underuse:** Users report the model ignores custom skills unless explicitly prompted (#21968), suggesting a gap in tool-discovery behavior.
- **Auto Memory reliability:** Low-signal sessions are retried indefinitely (#26522), and invalid inbox patches are silently skipped (#26523), reducing the quality of memory extraction.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-07

## 1. Today's Highlights

Two issues closed today — a long-standing feature request for repo-scoped plugins (#1665) and an invalid sandbox path report (#4745). The most critical open concern is a regression in ACP mode where `session/request_permission` is no longer sent, causing unattended tool execution (#4537), alongside a BYOK prompt-caching bug that may silently multiply costs by ~5x (#4720).

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#1665](https://github.com/github/copilot-cli/issues/1665) | **CLOSED** — Repo-scoped plugin support | Enables team-wide plugin distribution instead of per-user installs, a foundational multi-dev workflow. | 18 👍, 14 comments |
| [#4537](https://github.com/github/copilot-cli/issues/4537) | **OPEN** — ACP mode auto-approves tool calls (regression of #845) | Security regression: shell commands and file edits execute without permission prompts in `--acp` mode. | 2 👍, filed by Microsoft maintainer |
| [#4527](https://github.com/github/copilot-cli/issues/4527) | **CLOSED** — `copilot -p` fails with 401 on GHEC data residency | Non-interactive prompt mode breaks on data-residency tenants since 1.0.81-1, hitting `api.githubcopilot.com` instead of the tenant endpoint. | 4 👍 |
| [#4695](https://github.com/github/copilot-cli/issues/4695) | **OPEN** — MCP OAuth tokens not reliably reused | New token-cache entries are minted instead of reusing valid tokens, causing repeated PKCE re-auth flows. | 5 comments |
| [#4694](https://github.com/github/copilot-cli/issues/4694) | **OPEN** — WSL2: ~31 GB RSS / ~57% CPU on Claude Opus 5 | Severe resource consumption on long-running sessions, directly impacting developer machine usability. | Filed 2026-09-02 |
| [#4720](https://github.com/github/copilot-cli/issues/4720) | **OPEN** — BYOK silently disables prompt caching | Copilot CLI 1.0.82 sends no prompt-cache declaration, removing a major cost-saving mechanism for BYOK users. | |
| [#4735](https://github.com/github/copilot-cli/issues/4735) | **OPEN** — Assistant text reclassified as reasoning, never shown | Multi-paragraph user-facing text preceding a tool call is folded into collapsed "Thought for Ns" — users lose visibility into model output. | |
| [#4555](https://github.com/github/copilot-cli/issues/4555) | **OPEN** — `session/prompt` unconditionally aborts background sub-agents | ACP `session/prompt` calls `session.abort()` first, killing running background agents before the request is processed. | |
| [#4738](https://github.com/github/copilot-cli/issues/4738) | **OPEN** — `ask_user` form: early Enter discards typed input | High-severity data-loss bug: pressing Enter before the form is ready permanently loses user-authored content. | |
| [#2644](https://github.com/github/copilot-cli/issues/2644) | **OPEN** — Shift+Arrow / Ctrl+A selection support | Missing basic terminal text-selection shortcuts erodes UX parity with IDEs; 2 👍. | |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#4739](https://github.com/github/copilot-cli/pull/4739) | docs: propose terminal-owned macOS notifications | OPEN | Reference proposal documenting the macOS notification click problem with an MIT-licensed example and portable regression tests. Not a CLI code change. |

*No other PRs updated in the last 24 hours.*

## 5. Feature Request Trends

- **Project/Repo-scoped configuration**: Plugin scoping (#1665, now closed) signals strong demand for per-repository CLI settings, mirroring the pattern established by other tools (e.g., `.gitignore`, `.editorconfig`).
- **Terminal UX parity**: Repeated requests for IDE-like keyboard shortcuts — Shift+Arrow selection (#2644), Ctrl+E to accept inline suggestions (#4736) — indicate the interactive CLI is seen as lagging behind editor experiences.
- **MCP & BYOK reliability**: Users are pushing for more robust OAuth token caching (#4695) and correct prompt-cache headers in BYOK mode (#4720), both critical for cost and workflow friction.
- **macOS notification integration**: PR #4739 shows early community interest in terminal-driven notification clicks, a step toward desktop-parity UX.

## 6. Developer Pain Points

1. **Security regressions in ACP mode**: Issue #4537 (auto-approve tool calls) and #4555 (background agent abort on prompt) suggest the ACP pathway is introducing unsafe defaults and session-integrity bugs after the 1.0.81-1 update.
2. **Silent cost escalation in BYOK**: Issue #4720 describes prompt caching being disabled without warning, directly increasing API costs — a trust and budget concern for enterprise BYOK adopters.
3. **Data-residency authentication breaks**: GHEC data-residency tenants see `copilot -p` fail with 401 (#4527), while interactive mode works, pointing to inconsistent endpoint resolution.
4. **Resource consumption on WSL**: Issue #4694 reports ~31 GB RSS and 57% CPU on long-running Claude Opus 5 sessions, making the CLI impractical on resource-constrained environments.
5. **Input/data-loss bugs**: The `ask_user` form discarding typed input on early Enter (#4738) and the desktop app blocking concurrent Local sessions (#4742) are high-friction, user-visible defects eroding trust.
6. **Text-visibility bugs**: Issue #4735 folds assistant text into collapsed reasoning blocks, and #4743 reports `end_turn` arriving before background-shell completion — both make it difficult for users to follow what the model is doing.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-07

## 1. Today's Highlights

Two pull requests are advancing core fixes and performance improvements: one addresses a double-encoded tool-call argument parsing bug that breaks Pydantic validation, while another optimizes `get_share_dir` with caching. On the issues front, the Remote Control feature request (#1282) continues to gain significant community traction with 32 upvotes.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

### #1282 — Remote Control: Continue local sessions from any device [OPEN]
**Why it matters:** This is the most-voted open issue on the board (32 👍). The ability to resume a local Kimi Code CLI session from a phone, tablet, or browser would dramatically improve workflow continuity — a feature many users already expect from modern agent tools.
**Community reaction:** Strong support; the issue was opened in February and has accumulated substantial engagement.
**URL:** [MoonshotAI/kimi-cli#1282](https://github.com/MoonshotAI/kimi-cli/issues/1282)

### #2252 — Add `/goal` command & import coding plans into Codex [CLOSED]
**Why it matters:** Requests parity with Claude Code v138 and broader Codex ecosystem interoperability. The `/goal` command is becoming a de facto standard for structured, multi-step coding workflows.
**Community reaction:** Modest engagement (2 👍), but signals growing cross-tool comparison from users.
**URL:** [MoonshotAI/kimi-cli#2252](https://github.com/MoonshotAI/kimi-cli/issues/2252)

### #1354 — Plan mode request [CLOSED]
**Why it matters:** Users report Kimi Code executing autonomously before planning discussions conclude, undermining structured workflows. A dedicated plan mode would give users explicit control over the execute-vs-plan toggle.
**Community reaction:** 7 👍, with one comment; the pain point is relatable for users who rely on skill-based planning.
**URL:** [MoonshotAI/kimi-cli#1354](https://github.com/MoonshotAI/kimi-cli/issues/1354)

### #1356 — Seamless migration of MCP Skill configs from other agent CLIs [CLOSED]
**Why it matters:** As the MCP ecosystem expands, users juggle multiple agent tools. A migration path for MCP skill/server configurations would lower the barrier to adoption for users coming from Claude CLI, Cursor, Windsurf, Continue, etc.
**Community reaction:** Low engagement (0 👍), but the problem is real for power users managing multi-tool setups.
**URL:** [MoonshotAI/kimi-cli#1356](https://github.com/MoonshotAI/kimi-cli/issues/1356)

---

## 4. Key PR Progress

### #2636 — Optimize `get_share_dir` with caching and path handling [OPEN]
**Author:** gugu8intel-i9 | **Created:** 2026-09-07
A performance-focused PR that introduces caching to `get_share_dir`, reducing redundant path resolution calls. The author's casual note ("Was bored so did this") belies a genuinely useful optimization for users who interact with the CLI frequently.
**URL:** [MoonshotAI/kimi-cli#2636](https://github.com/MoonshotAI/kimi-cli/pull/2636)

### #2513 — Fix: recursively decode double-encoded tool-call arguments [OPEN]
**Author:** nitishagar | **Created:** 2026-07-19 | **Updated:** 2026-09-06
A critical bug fix. The Moonshot API occasionally returns `function.arguments` with nested array/object values as JSON strings (double-encoding). After a single `json.loads`, values like `todos` remain strings and fail Pydantic validation. This PR adds a shared `decode_tool_arguments` helper that recursively unwraps double-encoded values.
**Impact:** High — affects any tool call that passes structured data (lists, nested objects) as arguments.
**URL:** [MoonshotAI/kimi-cli#2513](https://github.com/MoonshotAI/kimi-cli/pull/2513)

---

## 5. Feature Request Trends

Three clear directions emerge from recent issues:

1. **Cross-device session continuity** — The Remote Control request (#1282) leads community interest, reflecting demand for always-available CLI access beyond the desktop.
2. **Structured planning workflows** — Both #1354 (plan mode) and #2252 (/goal command) point to a user base that wants explicit planning phases before autonomous execution, mirroring features in Claude Code and Codex.
3. **Ecosystem interoperability** — #1356 and #2252 both reference migration and compatibility with other agent tools (Codex, Claude CLI), suggesting users view Kimi Code as part of a broader toolchain rather than a standalone product.

---

## 6. Developer Pain Points

- **Autonomous execution disrupts planning:** Users attempting skill-based planning workflows report Kimi Code proceeding to execute before the plan is finalized (#1354). This suggests a need for clearer mode separation (plan vs. execute) with explicit user control.
- **Tool argument deserialization bugs:** Double-encoded arguments from the Moonshot API cause Pydantic validation failures (#2513), representing a reliability gap that affects structured tool calls.
- **Fragmented MCP configurations:** Users managing multiple agent tools face manual reconfiguration when switching or adding tools (#1356), highlighting an under-served need for config portability.
- **Feature parity pressure:** Multiple issues explicitly reference Claude Code and Codex features, indicating users benchmark Kimi Code against these tools and feel gaps acutely.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-09-07

## 1. Today's Highlights

OpenCode's issue tracker is seeing a surge in musl/TUI compatibility concerns, token-cost feedback, and desktop reliability regressions. The team is actively shipping performance gains to the renderer persistence layer and fixing several long-standing agent-loop and clipboard bugs across platforms.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#27589](https://github.com/anomalyco/opencode/issues/27589) | TUI fails on Alpine Linux (musl) in 1.14.50 — `getcontext` symbol not found | Hard break for Alpine/musl users; a clean regression from 1.14.48 → 1.14.50 | 39 comments · 12 👍 |
| [#1934](https://github.com/anomalyco/opencode/issues/1934) | Auto-run `aws sso login` when credentials expire | Daily pain for enterprise users with short SSO sessions; 14 👍 shows strong demand | 8 comments · 14 👍 |
| [#22225](https://github.com/anomalyco/opencode/issues/22225) | Skill usage tracking to CLI | Developer want visibility into which skills are actually used per session | 13 comments |
| [#33490](https://github.com/anomalyco/opencode/issues/33490) | GLM-5.2 via OpenCode Go rejects `instructions` field | Provider-model contract mismatch causing runtime errors on Z.AI-backed models | 7 comments · 3 👍 |
| [#32749](https://github.com/anomalyco/opencode/issues/32749) | Explore agent wastes tokens on every task | Sub-agent always spawns regardless of task size; no lightweight grep fallback | 6 comments · 1 👍 |
| [#35294](https://github.com/anomalyco/opencode/issues/35294) | Desktop "Local Server could not be reached" on startup (regression in v1.17.12+) | Blocking startup failure when network is slow due to synchronous `models.dev` fetch | 4 comments |
| [#34712](https://github.com/anomalyco/opencode/issues/34712) | Input token count inconsistent with Circle context | Token accounting bug in v1.17.12 — values don't decrease after compact | 5 comments · 5 👍 |
| [#47716](https://github.com/anomalyco/opencode/issues/47716) | Together AI token usage always 0 | `@ai-sdk/togetherai` bundle omits `stream_options.include_usage`, so cost tracking is broken | 2 comments |
| [#31942](https://github.com/anomalyco/opencode/issues/31942) | Agent loops 277 times on MCP `resource_list` without circuit breaker | No loop detection exhausts workspace token budget on missing resources | 3 comments |
| [#35954](https://github.com/anomalyco/opencode/issues/35954) | Editing `opencode.json` via MCP tools corrupts JSON and crashes | AI assistant bypasses safe JSON-editing rules, causing frequent crashes | 2 comments |

## 4. Key PR Progress

| # | PR | Summary |
|---|----|---------|
| [#47706](https://github.com/anomalyco/opencode/pull/47706) | **perf: externalize large draft text into content-addressed chunks** | Follows VS Code's `Memento` pattern — large pasted text is chunked instead of re-serialized on every keystroke. |
| [#47705](https://github.com/anomalyco/opencode/pull/47705) | **perf: serialize persisted stores on a schedule** | Stores now batch-serialize once per save window rather than per setter call. |
| [#47704](https://github.com/anomalyco/opencode/pull/47704) | **perf: cache storage namespaces and batch writes in the renderer** | Transport layer for the persistence rewrite — one bulk load per namespace, one bulk write per flush. |
| [#47724](https://github.com/anomalyco/opencode/pull/47724) | **fix(desktop): surface default path opening errors** | Non-empty errors from Electron's `shell.openPath()` now propagate to the UI instead of silently swallowing. |
| [#47720](https://github.com/anomalyco/opencode/pull/47720) | **fix(cli): resolve plugins in Node SEA builds** | Replaces missing `import.meta.resolve` in Node's SEA ESM entrypoint with a VM-backed resolver. |
| [#47666](https://github.com/anomalyco/opencode/pull/47666) | **fix(tui): derive tab busy state from execution only** | Tab spinners now follow active execution, not pending inbox items, fixing misleading busy indicators. |
| [#44825](https://github.com/anomalyco/opencode/pull/44825) | **fix(core): route filesystem through location environment** | File canonicalization, reads, and listings now go through the Location environment, fixing path-resolution bugs in worktrees. |
| [#47640](https://github.com/anomalyco/opencode/pull/47640) | **feat: preview and text extraction for office files and PDF** | Adds offline document preview and text extraction for Office/ PDF attachments. |
| [#47702](https://github.com/anomalyco/opencode/pull/47702) | **fix: route Muse Spark models to Responses API** | Fixes 0-token / HTTP 500 errors when using Muse Spark 1.2/1.3 through the CLI by switching to the Responses API. |
| [#47718](https://github.com/anomalyco/opencode/pull/47718) | **fix(ui): align unread avatar badges with the corner** | CSS-pixel-accurate badge positioning on avatars; minor but improves visual polish. |

## 5. Feature Request Trends

- **Session management & portability** — migration between machines ([#47713](https://github.com/anomalyco/opencode/issues/47713)), configurable retention/cleanup ([#34875](https://github.com/anomalyco/opencode/issues/34875)), and server-side pagination for long sessions ([#35895](https://github.com/anomalyco/opencode/issues/35895)).
- **Cloud credential automation** — auto-refresh for AWS SSO ([#1934](https://github.com/anomalyco/opencode/issues/1934)) and Vertex SDK env-var support ([#35880](https://github.com/anomalyco/opencode/issues/35880)).
- **Linux clipboard parity** — pre-bundling `xclip`/`xsel`/`wl-clipboard` for zero-config copy/paste ([#35977](https://github.com/anomalyco/opencode/issues/35977), [#35978](https://github.com/anomalyco/opencode/issues/35978)).
- **Agent efficiency & observability** — skill usage tracking ([#22225](https://github.com/anomalyco/opencode/issues/22225)), circuit breakers for MCP loops ([#31942](https://github.com/anomalyco/opencode/issues/31942)), and Plan Mode UX with a dedicated planning document ([#35900](https://github.com/anomalyco/opencode/issues/35900)).
- **Configurability** — SQLite PRAGMA settings for long-running deployments ([#35892](https://github.com/anomalyco/opencode/issues/35892)).

## 6. Developer Pain Points

- **musl / Alpine compatibility** — the highest-commented open issue (#27589) shows a hard blocking regression for non-glibc Linux users.
- **Token cost transparency** — multiple reports of incorrect or zero token counts (Together AI, GLM-5.2, Circle context inconsistency) erode trust in cost tracking.
- **Desktop startup regressions** — the v1.17.12 blocking `models.dev` fetch (#35294) causes a visible "Local Server could not be reached" error on slow networks.
- **MCP loop exhaustion** — no circuit breaker lets agents burn through workspace token limits on missing resources (#31942).
- **Linux clipboard friction** — new users hit a dead end without manually installing `xclip`/`xsel`/`wl-clipboard` (#35977, #35978).
- **AI-editing config files unsafely** — the `edit` tool corrupts `opencode.json` when the model violates safe-editing rules (#35954), causing crashes.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-07

## 1. Today's Highlights

The Pi coding-agent project shipped several critical fixes today, including cross-provider fallback routing, MagicDNS resolution repair, and proper handling of Copilot GPT models through the Responses API. Community attention remains focused on openai-codex connection reliability (#4945, 76 comments) and Windows UX fragmentation (#7547), while new contributions expanded the extension API surface with per-call tool confirmation and session-aware headers for OpenCode Go.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Comments | Why It Matters |
|---|-------|----------|----------------|
| [#4945](https://github.com/earendil-works/pi/issues/4945) | openai-codex Connection Reliability Issues | 76 👍32 | Repeated reports of the TUI hanging on `Working...` with no streamed output or error — the top-voted issue by far, affecting daily coding workflows. |
| [#7547](https://github.com/earendil-works/pi/issues/7547) | How do you use Pi on Windows? What issues are you seeing? | 57 👍2 | Windows has fragmented setup paths (native, WSL, etc.). The team needs a consolidated view of pain points to prioritize docs and out-of-box experience. |
| [#9052](https://github.com/earendil-works/pi/issues/9052) | Fullscreen mode scroll 3× slower than regular mode | 6 👍3 | Fullscreen mode is popular for its fixed input box, but the degraded scroll experience is a dealbreaker for power users reading long transcripts. |
| [#8826](https://github.com/earendil-works/pi/issues/8826) | Cap agent retry backoff for prolonged transient outages | 4 👍0 | During extended 503s (e.g., "too many open files"), exponential backoff can stall sessions indefinitely — users want a bounded cap. |
| [#9229](https://github.com/earendil-works/pi/issues/9229) | Windows: shell_path config ignored, prefers WSL bash | 4 👍0 | Even with WSL disabled, `shell_path` in `settings.json` is overridden — a direct configuration bug on Windows. **(Closed)** |
| [#9209](https://github.com/earendil-works/pi/issues/9209) | GitHub Copilot GPT-6 Astra routed to unsupported endpoint | 4 👍0 | `gpt-6-astra` was hitting `/chat/completions` which Copilot rejects; needs routing through the Responses API. **(Closed via #9253)** |
| [#8823](https://github.com/earendil-works/pi/issues/8823) | Esc during streaming often fails to cancel in-flight request | 3 👍0 | Pressing Escape doesn't reliably abort the HTTP call — the turn persists with `stopReason: "abort"` but the request still completes server-side. |
| [#9256](https://github.com/earendil-works/pi/issues/9256) | Resumed session re-renders tool-result images as full-size inline | 2 👍0 | Session resume (`pi -c`) blows up the viewport when prior turns contained images read from disk — layout regression. **(Closed)** |
| [#9230](https://github.com/earendil-works/pi/issues/9230) | opencode-go provider missing required `x-opencode-session` header | 2 👍1 | OpenCode Go now requires a stable session header; missing it causes requests to error. **(Closed)** |
| [#9240](https://github.com/earendil-works/pi/issues/9240) | Line changes above viewport trigger destructive full redraw | 2 👍0 | During long streaming sessions, any update above the visible area causes a full scroll-to-top jump — extremely disruptive to workflow. **(Closed)** |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#9259](https://github.com/earendil-works/pi/pull/9259) | Apply steering message promptly by interrupting the running turn | ✅ Closed | Users sending a steering message while a long tool call runs now get immediate interruption instead of queuing until completion. |
| [#9261](https://github.com/earendil-works/pi/pull/9261) | Add `sendStrictToolField` compat flag | ✅ Closed | Anthropic-compatible gateways (e.g., AWS Bedrock proxies) that require strict schema but reject the `strict` field itself can now opt out. |
| [#9253](https://github.com/earendil-works/pi/pull/9253) | Route Copilot GPT models through Responses API | ✅ Closed | Fixes #9209 — GPT models now hit the correct endpoint; also reflects Copilot's deprecation of GPT-4 catalog entries. |
| [#9252](https://github.com/earendil-works/pi/pull/9252) | Pin undici connect lookup to system dns.lookup | ✅ Closed | Fixes MagicDNS / split-horizon hostname resolution (#9244) by ensuring the HTTP dispatcher uses the OS resolver. |
| [#9251](https://github.com/earendil-works/pi/pull/9251) | Hop to a fallback provider on transport errors | ✅ Closed | Optional cross-provider fallback chain — when the active provider is unreachable, sessions continue on a configured backup. Fixes #9242. |
| [#6881](https://github.com/earendil-works/pi/pull/6881) | Use provider-reported cost when responses include it | 🔄 Open | Reads `usage.cost` from provider responses (including BYOK upstream share from OpenRouter) instead of relying solely on catalog rates. |
| [#9233](https://github.com/earendil-works/pi/pull/9233) | Resolve model auth live instead of from startup snapshot | ✅ Closed | Fixes a race where `hasConfiguredAuth()` reads an unsettled availability snapshot at startup, causing false auth-rejected errors. |
| [#9080](https://github.com/earendil-works/pi/pull/9080) | Add jump-to-latest control in TUI | ✅ Closed | New TUI control lets users jump back to the latest messages after scrolling up in a long conversation. |
| [#9137](https://github.com/earendil-works/pi/pull/9137) | Add Nix flake for pi | 🔄 Open | WIP contribution bringing Nix-based installation support; authored by @mitsuhiko. |
| [#9227](https://github.com/earendil-works/pi/pull/9227) | Add per-call tool confirmation extension | ✅ Closed | Opt-in extension for confirming state-changing custom tools before each call, complementing the existing `permission-gate` bash pattern guard. |

---

## 5. Feature Request Trends

- **Resilience & fallback routing** — Multiple issues (#8826, #9242) and a merged PR (#9251) converge on the need for graceful degradation: capped retry backoffs, cross-provider failover, and transport-error recovery.
- **Windows-first experience** — The Windows ecosystem (issues #7547, #9229, #7175) remains a sustained focus area, with demands for unified docs, correct `shell_path` handling, and terminal keybinding parity.
- **Extension API maturation** — Requests for `setTuiMode()` / `getLayoutRoot()` (#9238), `ModelRuntime` exposure (#8791), and acknowledged turn delivery (#9236) signal a community building richer side-panel and session-scoped extensions.
- **Cost transparency** — PR #6881 and related discussion reflect growing demand for accurate, provider-reported cost tracking rather than static catalog estimates.
- **TUI scroll & layout stability** — Fullscreen scroll speed (#9052), viewport jump-on-update (#9240), and jump-to-latest (#9080) all point to the TUI being used for increasingly long sessions where scroll behavior is critical.

---

## 6. Developer Pain Points

1. **Streaming stuck / no feedback loops** — The openai-codex `Working...` hang (#4945) and Esc abort reliability (#8823) both reflect a core frustration: when the model provider is slow or unresponsive, the TUI gives no recoverable signal.
2. **Windows configuration fragility** — `shell_path` ignored (#9229), WSL auto-preference, and Shift+Enter submit behavior (#7175) make the Windows experience feel like a collection of workarounds rather than a first-class path.
3. **DNS resolution in custom networks** — MagicDNS / Tailscale-hosted providers fail with `ENOTFOUND` (#9244) because undici doesn't delegate lookups to the OS resolver; now fixed but highlights a gap for enterprise/VPN users.
4. **Session resume layout regressions** — Image re-rendering at full size (#9256) and scroll-to-top on above-viewport updates (#9240) show that session persistence and streaming interactivity haven't been stress-tested together.
5. **Provider schema incompatibilities** — Gateways like Bedrock proxies reject the `strict` field even when they require strict schemas (#9261), and OpenRouter models vary in supported features (per-message `output_config` rejected by Claude Opus 5, #9165), forcing per-provider compat flags.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-07

## 1. Today's Highlights

Qwen Code released **v0.23.1-preview.1** and a corresponding nightly build, both introducing dynamic workflow visualization and management in the Web Shell alongside performance fixes for session workflow projection. The community is closely watching the long-planned TUI migration from `ink` to OpenTUI (#8662, 30 comments) and multiple performance bugs affecting the Web Shell export pipeline and mobile session switching.

---

## 2. Releases

| Version | Key Changes |
|---|---|
| **v0.23.1-preview.1** | `web-shell`: visualize and manage dynamic workflow runs; derive the session workflow project for performance (#10594) |
| **v0.23.0-nightly.20260906.92a8a8d179** | Same web-shell workflow visualization and projection fixes as above |

- PR: <https://github.com/QwenLM/qwen-code/pull/10594>

---

## 3. Hot Issues

1. **#8662 — Migrate TUI rendering layer from ink to OpenTUI (tracking)** · 30 comments
   The current ink 7 + React 19 renderer requires ~1,037 lines of patches and exhibits structural flicker and viewport issues. This tracking issue is the most-discussed open item and will shape the long-term TUI architecture.

2. **#3361 — Agent misinterprets shell output as empty despite successful execution** · 6 comments
   A persistent bug where Qwen Code runs shell commands successfully but the agent concludes the output is empty — particularly frustrating for git-related workflows. Open since April 2026.

3. **#11031 — Stop embedding the Web Shell runtime in every HTML export** · 6 comments · ✅ Closed
   Each exported HTML file was ~19.5 MB due to duplicated React + Web Shell runtime. Closed via a fix that eliminates the redundant embedding.

4. **#10865 — Session workflow projection derived three times per render** · 4 comments
   Performance regression follow-up to #8583; the same projection is computed redundantly, rebuilding an index designed to be constructed once per render.

5. **#11100 — Transcript entry still carries the daemon hook runtime** · 4 comments
   The read-only transcript type (`@qwen-code/web-shell/transcript`) leaks the daemon React SDK through three components, defeating the export-size fix from #11031.

6. **#11146 — Pre-aborted tool requests can wait behind an unrelated active batch** · 4 comments
   `CoreToolScheduler.schedule()` leaves cancelled requests queued behind unrelated work, causing stale or orphaned cancellations in the interactive CLI.

7. **#6181 — Mobile session switching is janky** · 3 comments
   Full-sync transcript render, uncompressed history loads, and per-frame O(transcript) costs cause multi-second freezes on mobile when switching sessions. Labeled P1.

8. **#11067 — PreToolUse hooks do not run when a skill is started with `/<skill-name>`** · 3 comments · ✅ Closed
   Skills declaring a `PreToolUse` safety-gate hook silently skip it when invoked directly via slash command, undermining the safety contract.

9. **#11198 — Telemetry uploads raw tool-error text including shell command lines to RUM without redaction** · 2 comments · P1 security
   Usage-statistics channel sends unredacted tool-error output (potentially containing secrets or sensitive command lines) to the RUM endpoint. Marked `ready-for-human`.

10. **#11228 — Open right-click context menu does not consume keys** · 2 comments
    `KeypressContext` broadcasts key events to all handlers without allowing a `ContextMenuOverlay` to consume them, causing the composer and tool-approval dialog to act on the same keystroke.

---

## 4. Key PR Progress

| PR | Title | Summary |
|---|---|---|
| **#11244** | `feat(web-shell): make the product name and logo configurable` | Enables white-label deployments by reading product name and SVG logo path from `settings.json` without source edits. |
| **#10938** | `feat(web-shell): make Session Workflow dependencies navigable` | Closes navigation and chrome gaps from #8583; reworks the plan DAG to lead with the step, not its status. |
| **#11206** | `feat(core): add multi-agent mesh admission foundation` | Introduces rules and durable storage for persistent workspace agents collaborating on shared threads — mention routing, per-thread turn gates, token gates, and atomic booking. |
| **#11252** | `feat(mesh): bind dispatcher runs to agent turns` · ✅ Closed | Connects the mesh dispatcher to real background-agent turn boundaries; records correlated delivery and token usage per turn. |
| **#11208** | `feat(web-shell): add bounded historical transcript viewport` · ✅ Closed | Phase 2B of session-wide turn navigation; enables read-only historical windows with gap recovery and live-tail return. |
| **#10237** | `fix(core): prevent duplicate task owner dispatch` | Rejects leader attempts to reassign an in-progress teammate task, returning an explicit error instead of persisting a duplicate dispatch. Fixes #10207. |
| **#11165** | `refactor(ci): extract release workflow scripts` | Moves release logic from `release.yml` into executable repo scripts, improving maintainability and preserving existing job semantics. |
| **#11242** | `feat(browser-use): add Chrome Native Messaging relay` | Bridges the Browser SDK to the user's Chrome via a local Native Messaging host and Qwen Chrome extension, forwarding CDP commands and events. |
| **#11090** | `feat(ipc): let a user-minted controller token drive a session` | Inbound gate delivers messages without per-message review between sessions in the same review class, while rejecting unclassed senders as strangers. |
| **#11251** | `feat(web-shell): expose assistant turn settlement lifecycle` | Adds an optional host callback reporting session/prompt identity, outcome, stop reason, and final retained message after each assistant turn completes. |

---

## 5. Feature Request Trends

- **Multi-agent collaboration infrastructure** — The mesh admission foundation (#11206), turn-bound dispatcher (#11252), and controller-token IPC (#11090) signal a coordinated push toward persistent, shared-thread multi-agent workspaces.
- **Web Shell experience hardening** — White-labeling (#11244), bounded historical viewport (#11208), split-view navigation (#11250), and sidebar scope alignment (#11240) all target a more mature, production-grade Web Shell.
- **Browser automation expansion** — The Chrome Native Messaging relay (#11242) extends browser-use capabilities beyond the existing SDK surface.
- **Goal and spending visibility** — PR #11248 adds token/usage spend indicators to Goal surfaces, addressing developer demand for budget transparency.
- **CI/CD reliability** — Release script extraction (#11165), macOS E2E retry (#11134), and timeout fixes (#11209) reflect ongoing investment in build stability.

---

## 6. Developer Pain Points

- **TUI flicker and structural rendering limits** — The ink-to-OpenTUI migration (#8662) remains the most-commented open issue, indicating sustained frustration with current rendering artifacts.
- **Web Shell export bloat and runtime leakage** — Two related issues (#11031 closed, #11100 open) show that even after fixing the 19.5 MB export, the daemon React SDK still leaks into transcript entries.
- **Mobile performance on session switch** — P1 issue #6181 highlights that transcript rendering and polling costs make the Web Shell unusable on mobile during session changes.
- **Tool cancellation and scheduling bugs** — Pre-aborted requests (#11146), skipped completion cleanup (#11162), and hook bypass on direct skill invocation (#11067) create unpredictable behavior in interactive flows.
- **SSE/transport error handling** — Statusless throttling errors (#11215) and Anthropic SSE false-success reports (#11217) cause turns to abort or report success incorrectly when using OpenAI-compatible backends.
- **Telemetry privacy** — Unredacted shell-command errors in RUM uploads (#11198) is a P1 security concern for users running sensitive workloads.
- **Key-event routing conflicts** — Context menus not consuming keys (#11228) leads to double-handling of keystrokes between the composer and tool-approval dialogs.
- **CI/CD timeout contention** — Flat 20-minute timeouts on the ECS pool (#11209) and release workflow duplication (#11109) cause spurious failures and wasted compute.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-09-07

## 1. Today's Highlights

The CodeWhale TUI team shipped a burst of fixes targeting the 0.9.12/0.9.13 transition, closing out seven previously unchangelogged feature commits and resolving critical fleet, MCP, and test-isolation bugs. A major architectural effort—**EPIC-005: CodeWhale TUI Crate Decomposition**—continues to accumulate discussion as the codebase restructures into smaller crates. Three PRs landed today that surface previously-silent runtime failures (session ID divergence, runtime store errors, MCP login states) as visible TUI notices instead of log-only events.

## 2. Releases

No new releases in the last 24 hours. The project is currently preparing for a **v0.9.13** cut; changelog receipts for seven merged feature commits were just added (PR #5967), unblocking the release path.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5316](https://github.com/Hmbown/Codewhale/issues/5316) | **EPIC-005: CodeWhale TUI Crate Decomposition** | Umbrella tracking issue for restructuring the monolithic TUI crate into smaller, focused crates. 22 comments reflect sustained architectural debate. |
| [#5620](https://github.com/Hmbown/Codewhale/issues/5620) | **Context pressure warning is transient; agent doesn't react** | Medium-severity bug where the agent silently ignores context-pressure signals, causing undetected context degradation. No crash, but defeats a key safety mechanism. |
| [#5929](https://github.com/Hmbown/Codewhale/issues/5929) | **Parallel-execution flakes in codewhale-tui lib suite** | Six tests fail under load but pass in isolation, each costing a 25-minute CI rerun. Root-caused and partially fixed in PR #5970. |
| [#5969](https://github.com/Hmbown/Codewhale/issues/5969) | **`serve --acp` initialize response violates ACP schema** | `sessionCapabilities.list` is emitted as a boolean instead of an object, breaking strict clients like JetBrains IDEA. Open as of today. |
| [#5950](https://github.com/Hmbown/Codewhale/issues/5950) | **Bottom chrome (posture bar + metrics line) is unconfigurable** | The 0.9.12 shell redesign hard-coded two rows under the composer; `/statusline` no longer controls them. Fixed via PRs #5962 and #5973. |
| [#5915](https://github.com/Hmbown/Codewhale/issues/5915) | **Fleet models: provider → model → shortlist → role** | Founder-directed design for a fleet model shortlist that sub-agents can be assigned to, with role-based cost classes. Still open. |
| [#5932](https://github.com/Hmbown/Codewhale/issues/5932) | **Test isolation leak: onboarding tests persist into real config** | Tests wrote a fixture provider into the founder's real `~/.codewhale/setup_state.json`, contaminating production state. Open. |
| [#5908](https://github.com/Hmbown/Codewhale/issues/5908) | **Win32 computer-use: input actions report success on failure** | Windows backend reports `{action_sent: true}` even when the OS call never ran; left mouse down drops the press. Closed. |
| [#5906](https://github.com/Hmbown/Codewhale/issues/5906) | **Fleet claims: parked/cancelled agents hold write claims indefinitely** | A cancelled child agent can block all sibling work on the same worktree path forever. Closed. |
| [#5909](https://github.com/Hmbown/Codewhale/issues/5909) | **`write_file` silently converts CRLF to LF on overwrite** | Inconsistent line-ending behavior between `edit_file` (preserves) and `write_file` (normalizes). Closed. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5973](https://github.com/Hmbown/Codewhale/pull/5973) | **Compact & hidden presets for bottom chrome** | 🟢 Open | Adds `full | compact | hidden` modes for posture bar and metrics line, settable live via `/config`. Closes #5950. |
| [#5970](https://github.com/Hmbown/Codewhale/pull/5970) | **Isolate five load-flaky tests** | ✅ Closed | Root-caused and fixed five of six parallel-flake tests; sixth analyzed as already parallel-safe. Closes #5929. |
| [#5972](https://github.com/Hmbown/Codewhale/pull/5972) | **Failing runtime store → visible notice** | 🟢 Open | Makes runtime store load failures surface as TUI notices instead of log lines. Closes the runtime-store half of #5931. |
| [#5971](https://github.com/Hmbown/Codewhale/pull/5971) | **`/mcp` leads with need-login servers** | ✅ Closed | Footer and `/mcp` now surface auth-required servers first with a login path, instead of reporting "8 failed". Closes #5926. |
| [#5968](https://github.com/Hmbown/Codewhale/pull/5968) | **Opt-in `rusty_alloc` global allocator** | ✅ Closed | Adds `rusty_alloc` as an off-by-default alternative to mimalloc—no C compiler or build script required. Closes #5872. |
| [#5966](https://github.com/Hmbown/Codewhale/pull/5966) | **Catalog-driven account keys + sandbox batch** | ✅ Closed | Dynamic account-key providers, first-class `codewhale` route, and sandbox/ShannonNet batch support. Rebased onto main. |
| [#5965](https://github.com/Hmbown/Codewhale/pull/5965) | **Tunable compaction summarizer prompt** | ✅ Closed | Adds configurable summarizer instructions suffix and verbatim retention for old user messages. Closes #5956. |
| [#5964](https://github.com/Hmbown/Codewhale/pull/5964) | **Command discoverability while typing** | ✅ Closed | Slash command usage and subcommands now appear inline while typing and in `/help`. Closes #5952. |
| [#5963](https://github.com/Hmbown/Codewhale/pull/5963) | **Configurable `request_user_input` limits** | ✅ Closed | Hard limits of 1–3 questions and 2–4 options are now configurable instead of compile-time constants. Closes #5949. |
| [#5958](https://github.com/Hmbown/Codewhale/pull/5958) | **Model filter matching nothing shows hint** | ✅ Closed | Fleet setup no longer panics with an index-out-of-bounds when a filter matches zero routes. Closes #5953. |

## 5. Feature Request Trends

- **Visibility of silent failures**: Multiple issues (#5931, #5926, #5908) highlight a pattern where the TUI logs problems silently instead of surfacing them to the operator. The community and founder are prioritizing "notice over log line" across runtime store, session identity, and MCP states.
- **Fleet UX simplification**: The fleet system is expanding rapidly (model shortlists, role profiles, worker deliverables) but the menu surface is overwhelming. Issue #5888 and PR #5945/#5946 show active efforts to streamline fleet interactions.
- **Configurability over hard-coding**: A recurring theme—bottom chrome (#5950), compaction prompts (#5956), user-input limits (#5949), and allocator choice (#5872)—is moving from compile-time constants to runtime-configurable knobs.
- **Cross-platform parity**: Windows-specific bugs (#5908, #5923) and CRLF handling (#5909) indicate sustained pressure to bring the Windows experience up to par with POSIX.
- **Custom theme discovery**: Issue #5901 (closed) requested that user-placed theme files appear in the `/theme` picker—a small but representative ask for better user-space extensibility.

## 6. Developer Pain Points

- **Test flakiness under parallel execution**: Six tests in `codewhale-tui` fail only under `--test-threads > 1`, each costing ~25 minutes of CI time per rerun. Partially resolved in PR #5970, but test isolation remains a fragile area (see #5932 leak).
- **Crate decomposition coordination**: EPIC-005 (#5316) is a large umbrella effort with 22 comments and no recent resolution, suggesting the team is still debating the right granularity for crate boundaries.
- **MCP lifecycle complexity**: OAuth token refresh failures, mid-turn catalog swaps, and stale connection counts (#5887, #5926, #5939) create a fragile startup and runtime experience that's hard to debug from logs alone.
- **Fleet claim lifecycle**: Cancelled or parked agents holding write claims indefinitely (#5906) points to a deeper design gap in resource ownership and cleanup within the fleet executor.
- **Windows P/Invoke reliability**: The win32 computer-use backend (#5908) and window-control pin (#5923) both suffer from cross-process API calls that silently fail or block the TUI thread, suggesting limited Windows-specific test coverage.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*