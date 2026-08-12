# AI CLI Tools Community Digest 2026-08-12

> Generated: 2026-08-12 02:27 UTC | Tools covered: 10

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
**Date: 2026-08-12**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in August 2026 is marked by rapid iteration and maturation: seven major tools shipped active development cycles, while one (Grok Build) was dormant. Claude Code and Gemini CLI are navigating post-launch growing pains around reliability and security, OpenCode is deep in a V2 rewrite with community-driven feature expansion, and OpenAI Codex is pushing through a dense alpha series with heavy Windows-facing friction. The dominant theme across all tools is the tension between agent autonomy (multi-agent workflows, skill discovery, persistent memory) and operational reliability (cost controls, config stability, platform-specific regressions).

---

## 2. Activity Comparison

| Tool | Issues (New/Active) | PRs (Merged/Active) | Release Status |
|------|---------------------|---------------------|----------------|
| **Claude Code** | 10 hot issues, multiple new v2.1.228 regressions | 8 PRs (2 closed) | v2.1.228 shipped with known debug issues |
| **OpenAI Codex** | 10 hot issues, Windows-dominated | 10 PRs (all closed) | 3 alpha releases (v0.148.0-alpha.7→.9) |
| **Gemini CLI** | 10 hot issues, 1 closed | 10 PRs (4 closed) | v0.55.1, v0.56.0-preview.1, nightly |
| **GitHub Copilot CLI** | 10 hot issues, config regression wave | 3 PRs (1 reverted) | No new release; v1.0.79 regressions |
| **Kimi Code CLI** | 3 new issues | 8 PRs (6 closed) | No release; active contributor fixes |
| **OpenCode** | 10 hot issues, 2 closed | 11 PRs (7 closed) | No release; V2 development active |
| **Pi** | 10 hot issues, 4 closed | 10 PRs (4 closed) | No release; v0.84.0 regression being fixed |
| **Qwen Code** | 10 hot issues, 1 closed | 10 PRs (5 closed) | v0.21.10, v0.21.11-preview.0 shipped |
| **DeepSeek TUI** | 10 hot issues, 1 closed | 5 PRs (1 closed) | No release; v0.9.5 regression |
| **Grok Build** | — | — | No activity |

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Need |
|-------|---------------|---------------|
| **Configurable reasoning effort** | Kimi Code (PR #2509, `/effort`), Qwen Code (v0.21.10 ACP effort config), Pi (#7553 compaction thinking control) | Users want explicit speed-vs-depth control over model reasoning, not opaque defaults |
| **Persistent session memory** | Kimi Code (#1283, 34 comments, 6 months), Gemini CLI (#26522 Auto Memory), Claude Code (#42996 MEP proposal) | CLI agents are treated as continuing partners; cold-start context loss is a competitive disadvantage |
| **TUI transcript cleanliness** | Codex (#21252, noise reduction), OpenCode (#41922 compact turn tokens), Pi (OSC 52 clipboard), Gemini CLI (#23297 Enter key) | Tool-call noise degrades long-session usability; users want scannable, compact displays |
| **Multi-account / multi-provider MCP** | Claude Code (#36024, 77 👍 Gmail accounts), Gemini CLI (#28681 SGLang + OpenAI-compatible), Qwen Code (#8714 DashScope native) | Single-provider lock-in is pushing users toward flexible provider abstraction layers |
| **Session resumption & cross-machine state** | Claude Code (#42996, #27801), Codex (#34663 resume performance), Pi (#7968 intercom) | `--resume` is insufficient; users want durable, stateful session handoff |
| **Agent cost controls** | Claude Code (#67636 parallel agent over-spawning), OpenCode (#16017 Go usage API), Gemini CLI (#26911 false 429s) | Unbounded agent fan-out and opaque quota reporting are eroding trust |
| **Skill / sub-agent autonomy** | Gemini CLI (#21968 model ignores skills), OpenCode slash commands batch, Kimi Code (skill system) | Models don't proactively discover or invoke tools without explicit prompting |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | OpenCode | Qwen Code | Kimi Code | Pi | Copilot CLI | DeepSeek TUI |
|-----------|------------|--------------|------------|----------|-----------|-----------|-----|-------------|--------------|
| **Maturity** | Mature, shipping frequent patches | Alpha (0.148), rapid iteration | Mature with security push | V2 rewrite in progress | Early but focused | Early-mid, contributor-driven | Mature, agent-focused | Mature, enterprise-facing | Niche TUI |
| **Platform focus** | Cross-platform, Windows/Git Bash pain | Windows-dominated issues | Cross-platform, OAuth fixes | Linux/SSH-heavy (ALSA issues) | Cross-platform | Windows path bugs | macOS CPU concerns | Windows parsing bugs |
| **Technical approach** | Anthropic ACP + MCP + Cowork VM | Rust, gRPC code-mode, Guardian security | Google-native + SGLang expansion | Go, V2 TUI, Durable Objects | ACP with reasoning effort | Python ACP, assertion safety | Kotlin/ JVM, Mermaid/LaTeX | TypeScript, config-sensitive | Rust TUI, code review focus |
| **Unique differentiator** | Opus 5 system-prompt injection controversy; Cowork VM | Computer Use plugin lifecycle | SSER vulnerability fix; component-level evals | Slash-command parity push (Claude Code Clone) | Native DashScope; bounded session rotation | Configurable thinking effort (`/effort`) | Copilot auth reliability; intercom sessions | Enterprise BYOK + MCP BigInt gap | Schema simplification for model compatibility |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **OpenAI Codex** — 3 alpha releases in 24 hours, 10 closed PRs, dense merge cadence. The Windows plugin lifecycle issues are a known technical debt surface being actively attacked.
- **OpenCode** — 7 closed PRs today, concentrated slash-command feature burst from a single contributor (`afonsoft`), V2 bootstrapping bugs being addressed in parallel.

**Steady maturation with reliability focus:**
- **Claude Code** — High community engagement (72-comment Cowork issue, 48-upvote prompt-injection concern) but release velocity is tempered by v2.1.228 debug window. The community is self-organizing around workarounds (MEP proposal).
- **Gemini CLI** — Security-first cycle (2 CVEs, SSRF fix, shell-quote upgrade) alongside genuine feature work (SGLang support, local eval reports). Maturity signal: investive eval infrastructure (#24353, 76 behavioral tests).

**Contributor-driven momentum:**
- **Kimi Code CLI** — 6 closed PRs from a single contributor (`hobostay`) targeting assertion safety and race conditions. Smaller community but high-impact maintenance.

**Stalled or regression-heavy:**
- **GitHub Copilot CLI** — No new release; v1.0.79 config regression wave (#4431, #4434, #4422) suggests a fragile settings pipeline. Momentum is reactive.
- **DeepSeek TUI** — v0.9.5 regression (#5323) blocks Auto-Review workflows; architecture refactor (EPIC-005) is long-term but near-term reliability is strained.
- **Grok Build** — Zero activity; effectively dormant.

---

## 6. Trend Signals

1. **Reasoning effort is becoming a first-class UX concern.** Three tools (Kimi Code, Qwen Code, Pi) are actively adding configurable thinking controls. Users are hitting the same wall: default reasoning is either too shallow for complex tasks or too expensive/slow for iterative work. This will likely become a table-stakes feature.

2. **Windows is the universal friction point.** Every tool with a Windows user base reports platform-specific bugs — path resolution (Claude Code, Kimi Code), plugin lock contention (Codex, Copilot CLI), shell parsing (DeepSeek TUI), registry never written (Codex). This is an underinvested surface across the ecosystem.

3. **Session memory and statefulness are the next frontier.** The longest-running feature requests across tools (#1283 on Kimi Code at 6 months, #27801 on Claude Code with 72 comments, MEP proposal) all converge on the same need: agents that remember. Tools that ship durable context will gain significant adoption advantage.

4. **Security is a differentiator, not a checkbox.** Gemini CLI's CVE-driven cycle and the `heron_brook` prompt-injection controversy on Claude Code show that security transparency directly impacts user trust. The tools treating security as a community narrative (Gemini's open CVE response) are building credibility.

5. **Slash-command parity is a community-driven standard.** The OpenCode `afonsoft` burst and Claude Code's existing `/config`, `/tui` command surface suggest users expect feature parity across tools via familiar command patterns. This is organic standardization from the bottom up.

6. **MCP is the integration layer everyone depends on, and everyone struggles with.** Silent dispatch failures (Claude Code #79986), BigInt serialization (Copilot CLI #4211), OAuth registration gaps (Codex, Gemini CLI) — MCP adoption is throttled by tooling immaturity, not model capability.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-12 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

### #1 — skill-creator: run_eval.py Recall Fix ([PR #1298](https://github.com/anthropics/skills/pull/1298)) · OPEN
The most-discussed PR in the repository. `run_eval.py` — the backbone of the skill description-optimization loop — reports `recall=0%` for every description regardless of content, causing the optimization to run on noise. The PR bundles fixes for the eval artifact installation, Windows stream reading, trigger detection, and parallel workers. **10+ independent reproductions** reported. Status: open.

### #2 — document-typography Skill ([PR #514](https://github.com/anthropics/skills/pull/514)) · OPEN
Addresses pervasive typographic defects in AI-generated documents: orphan line-ends, widow paragraphs, and numbering misalignment. Authors note these issues "affect every document Claude generates" and are rarely surfaced by users. A high-demand gap-filler. Status: open.

### #3 — testing-patterns Skill ([PR #723](https://github.com/anthropics/skills/pull/723)) · OPEN
Covers the full testing stack: Testing Trophy philosophy, AAA unit-test pattern, React Testing Library, and integration-testing guidance. Signals strong community appetite for **structured test-generation skills**. Status: open.

### #4 — skill-quality-analyzer & skill-security-analyzer ([PR #83](https://github.com/anthropics/skills/pull/83)) · OPEN
Two meta-skills that audit other Skills across five dimensions (Structure, Documentation, Examples, Security, Functionality). Represents a growing demand for **self-referential quality tooling** in the Skills ecosystem. Status: open.

### #5 — ODT Skill ([PR #486](https://github.com/anthropics/skills/pull/486)) · OPEN
Extends document-format coverage to OpenDocument Format (.odt/.ods) — reading, creation, template-filling, and ODT-to-HTML conversion. Complements the existing DOCX skill and responds to open-source/LibreOffice workflow demand. Status: open.

### #6 — Self-Audit Skill ([PR #1367](https://github.com/anthropics/skills/pull/1367)) · OPEN
Implements a two-phase output audit: mechanical file-existence verification followed by a four-dimension reasoning-quality gate (priority-ordered by damage severity). Universal across projects and tech stacks. Status: open.

### #7 — PDF Case-Sensitivity Fix ([PR #538](https://github.com/anthropics/skills/pull/538)) · OPEN
Corrects 8 uppercase references in `skills/pdf/SKILL.md` to match the actual lowercase filenames on case-sensitive filesystems (Linux, macOS). Critical fix for cross-platform reliability. Status: open.

### #8 — color-expert Skill ([PR #1302](https://github.com/anthropics/skills/pull/1302)) · OPEN
A specialized skill covering color naming systems (ISCC-NBS, Munsell, RAL, CSS named), color spaces with usage guidance (OKLCH for scales, OKLAB for gradients, CAM16 for perceptual work), and practical color-matching workflows. Status: open.

---

## 2. Community Demand Trends (from Issues)

| Trend | Key Issue | Engagement |
|---|---|---|
| **Org-wide skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) — shared skill library or direct share links within organizations | 16 comments · 8 👍 |
| **Security & trust boundaries** | [#492](https://github.com/anthropics/skills/issues/492) — community skills impersonating the `anthropic/` namespace | 43 comments · 2 👍 |
| **eval-toolchain reliability** | [#556](https://github.com/anthropics/skills/issues/556) — `claude -p` never triggers skills; #1169 confirms literal slash-command queries still fail | 12 comments · 7 👍 |
| **Context-window hygiene** | [#1487](https://github.com/anthropics/skills/issues/1487) — `claude-api` skill eagerly injects ~156k tokens in one call, exhausting context | 4 comments |
| **Planning artifact lifecycle** | [#1417 → #1479](https://github.com/anthropics/skills/issues/1417) — planning artifacts accumulate with no cleanup mechanism | — |
| **Duplicate-skill installs** | [#189](https://github.com/anthropics/skills/issues/189) — `document-skills` and `example-skills` plugins install identical content, wasting context | 6 comments · 9 👍 |
| **Compact persistent memory** | [#1329](https://github.com/anthropics/skills/issues/1329) — symbolic notation for compact agent state during long-running sessions | 9 comments |
| **Reasoning quality gates** | [#1385](https://github.com/anthropics/skills/issues/1385) — pre-task calibration → adversarial review → delivery verification pipeline | 4 comments |

---

## 3. High-Potential Pending Skills

These PRs have active discussion and address high-visibility gaps; they are strong candidates for near-term merge:

- **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — `skill-creator` eval pipeline fix. The single most critical PR: the description-optimization loop is currently broken. Multiple sub-fixes (Windows, trigger detection, parallel workers) are bundled, suggesting a comprehensive resolution is in progress.
- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit skill with mechanical + reasoning gates. Directly addresses the community's #1385 proposal and growing demand for pre-delivery quality assurance.
- **[PR #1479](https://github.com/anthropics/skills/pull/1479)** — `plan-file-hygiene` skill. Solves the acknowledged lifecycle gap for planning artifacts (issues #1417, #1329).
- **[PR #514](https://github.com/anthropics/skills/pull/514)** — Document-typography skill. Fills a universally experienced but rarely-reported quality gap; high practical value, low implementation risk.
- **[PR #723](https://github.com/anthropics/skills/pull/723)** — Testing-patterns skill. Broad developer demand across the full testing stack; well-scoped and practical.
- **[PR #1302](https://github.com/anthropics/skills/pull/1302)** — color-expert skill. Niche but high-quality; first dedicated color-knowledge skill in the collection.
- **[PR #486](https://github.com/anthropics/skills/pull/486)** — ODT skill. Natural companion to the existing DOCX skill; expands open-format coverage.

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable skill authoring tooling and pre-delivery quality gates** — the `skill-creator` eval pipeline is currently producing misleading metrics, and users are building self-audit, reasoning-quality, and security-audit skills to compensate for the lack of built-in verification.

---



# Claude Code Community Digest — 2026-08-12

## 1. Today's Highlights

Claude Code v2.1.228 shipped with fixes for TUI redraw stalls, a Windows Git Bash path resolution bug, and a `/tui` revert regression. Community attention remains heavy on three fronts: the Cowork VM service-not-running stall (#27801, 72 comments), the v2.1.219 `heron_brook` prompt-injection override affecting Opus 5 users (#80988, 48 👍), and a cascade of parallel-agent cost-overrun reports. A cluster of same-day issues on v2.1.228 (ECONNRESET, image-read deadlocks, auto-update stub binaries) suggests an active debug window on the latest release.

---

## 2. Releases

**v2.1.228** — [GitHub release](https://github.com/anthropics/claude-code/releases)

- Fixed interactive TUI sessions that could stop redrawing entirely while the process kept running, caused by a rare internal layout error.
- Fixed `git` / Git Bash detection on Windows when Claude Code is launched from a parent folder of the Git installation.
- Fixed `/tui` revert behavior.

> ⚠️ Multiple new reports filed against v2.1.228 today (ECONNRESET persistent resets, image-read deadlocks on macOS, auto-update leaving a non-functional stub binary). Worth monitoring before upgrading.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#27801](https://github.com/anthropics/claude-code/issues/27801) | Cowork: "Failed to start Claude's workspace" — VM service not running, persists after reboot | Blocks the entire Cowork VM workflow; reported for months with no resolution. | 72 comments · 41 👍 |
| [#54394](https://github.com/anthropics/claude-code/issues/54394) | v2.1.117 embedded `ugrep` wrapper amplifies regex backtracking into V8-heap-OOM (8 GB ceiling) on WSL2 | A 2023-era change resurfaces as a memory bomb under heavy `grep` usage; host freezes reported. | 27 comments · 4 👍 |
| [#80988](https://github.com/anthropics/claude-code/issues/80988) | v2.1.219 `heron_brook` section injects "Do not call AgentTool" for Opus 5 only, no opt-out | System-prompt injection silently overrides user delegation policy — a trust and transparency concern. | 21 comments · 48 👍 |
| [#36024](https://github.com/anthropics/claude-code/issues/36024) | Support multiple Gmail accounts in MCP integration | High-demand feature for users juggling personal + work accounts; 77 👍 signals strong appetite. | 25 comments · 77 👍 |
| [#79986](https://github.com/anthropics/claude-code/issues/79986) | Claude Desktop: external stdio MCP tools announced but never dispatched in Chat mode | MCP tool calls fail silently across all platforms after a recent Desktop update — breaks integrations. | 15 comments · 8 👍 |
| [#81703](https://github.com/anthropics/claude-code/issues/81703) | July 17 mass billing incident: credits charged despite plan allowance; $604.71 disputed | Direct financial impact; follows up on Anthropic's acknowledged incident with no reconciliation. | 12 comments |
| [#78775](https://github.com/anthropics/claude-code/issues/78775) | [Regression] Desktop session time-range filter only visible when Group by = State | UX regression that removes a key navigation feature unless a specific grouping is active. | 8 comments · 28 👍 |
| [#73468](https://github.com/anthropics/claude-code/issues/73468) | macOS sandbox: Seatbelt profile via `sandbox-exec -p` exceeds ARG_MAX with many git worktrees | Sandboxed Bash commands fail 100% of the time on repos with many worktrees — sandbox unusable. | 7 comments · 5 👍 |
| [#84841](https://github.com/anthropics/claude-code/issues/84841) | MSIX write redirection misdetected as junction-planting attack, breaking Cowork VM SDK install | Security check fires falsely on every app update, blocking the Cowork SDK on Windows. | 6 comments · 2 👍 |
| [#67636](https://github.com/anthropics/claude-code/issues/67636) | Parallel agent spawning causes excessive token consumption before crashing | 10 agents spawned for a task 1–2 could handle; millions of tokens burned — a cost-control gap. | 6 comments |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#42996](https://github.com/anthropics/claude-code/pull/42996) | Add MEP (Meat Puppet Elimination Protocol) — async state relay | Open | Community proposal for stateless session resumption across machines; three-file pattern, no infra. |
| [#57888](https://github.com/anthropics/claude-code/pull/57888) | Scope `child_process_exec` to JS/TS files (fix Python false-positive) | ✅ Closed | The `security_reminder_hook` was flagging Python `asyncio.create_subprocess_exec(` as a JS/TS `child_process.exec(` call. |
| [#85925](https://github.com/anthropics/claude-code/pull/85925) | Point remaining stale doc links at code.claude.com | Open | Doc cleanup: replaces `docs.claude.com` redirects with canonical `code.claude.com` URLs across plugins and templates. |
| [#85834](https://github.com/anthropics/claude-code/pull/85834) | HackerOne Bug Bounty Program access fix | Open | Updates `devcontainer.json` so the `hookify` plugin installs correctly for bounty program access. |
| [#70173](https://github.com/anthropics/claude-code/pull/70173) | Detect `[gone]` branches with `git branch -vv` in `clean_gone` | ✅ Closed | `/clean_gone` was never deleting anything because `git branch -v` omits the `[gone]` tag; switched to `-vv`. |
| [#85822](https://github.com/anthropics/claude-code/pull/85822) | Fix stale doc links and README drift in plugins/examples | Open | Companion cleanup to #85925; verifies all links against live redirects. |
| [#85806](https://github.com/anthropics/claude-code/pull/85806) | Skip XSS warnings in docs | Open | Reuses `_DOC_EXTS` filter to suppress XSS-family substring rules in documentation and prose only. |
| [#85243](https://github.com/anthropics/claude-code/pull/85243) | Use spec-conformant names in plugin-dev and hookify skills | Open | Eight bundled skills had title-cased, space-containing `name` fields — now normalized to spec. |
| [#85716](https://github.com/anthropics/claude-code/pull/85716) | Load rules from ancestor `.claude` directories to prevent silent bypass | Open | Fixes #85613: `hookify` plugin was silently dropping security rules when `.claude/` config sat in parent dirs. |
| [#85975](https://github.com/anthropics/claude-code/issues/85975) | Auto-update reports success with non-functional stub binary after postinstall link failure | Open (issue) | macOS auto-update from 2.1.222 → 2.1.228 leaves a stub at `bin/claude.exe` when the postinstall symlink fails. |

---

## 5. Feature Request Trends

- **Multi-account MCP integrations** — Issue #36024 (77 👍) is the strongest signal: users want parallel Gmail/Google Workspace accounts, and the same pattern likely extends to Slack, Notion, and other MCP-connected services.
- **Session resumption & cross-machine state** — The MEP proposal (#42996) and the persistent Cowork VM issue (#27801) both point to a community need for first-class stateful session handoff, not just CLI `--resume`.
- **UI polish & discoverability** — Issues #33502 (folder not added to recent list), #78775 (time-range filter regression), and #61675 (no "Show less" on long `/goal` prompts) reflect sustained friction with the Desktop/TUI navigation experience.
- **Agent cost controls** — Parallel-agent over-spawning (#67636) and the `heron_brook` policy override (#80988) suggest users want explicit guardrails on agent fan-out and system-prompt tamper resistance.
- **Remote Control transparency** — Issue #85980 flags that `/rc` re-enables itself with no persistent off-switch; users want durable opt-out, not session-scoped toggles.

---

## 6. Developer Pain Points

| Pain Point | Related Issues / PRs |
|---|---|
| **VM / Cowork reliability** — VM service fails to start, persists across reboots; MSIX write-check false positives block SDK installs. | #27801, #84841, #85978 |
| **Platform-specific regressions** — Windows Git discovery (#2.1.228 fix), macOS ARG_MAX sandbox blowup (#73468), macOS image-read deadlocks (#85884), Windows ECONNRESET (#85979). | #73468, #85884, #85979, #85798 |
| **Auto-update fragility** — Updates report success but leave broken binaries or stub symlinks; hard to recover without manual intervention. | #85975, #85798 |
| **Agent cost & policy opacity** — Parallel agents burn tokens before crashing; system prompt sections inject constraints users can't opt out of. | #67636, #80988, #85677 |
| **MCP tool dispatch failures** — Tools announce successfully but never receive `tools/call` messages, silently breaking integrations. | #79986 |
| **Billing confusion** — Auto-recharges triggered despite included plan limits; unreconciled charges from the July 17 incident. | #81703, #83062 |
| **Session management inconsistencies** — `--resume` lists sessions that `--continue` refuses; identical titles for parent/child sessions. | #85657 |

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-12

## 1. Today's Highlights

Three Rust releases (0.148.0-alpha.7 → .9) shipped in the last 24 hours. Windows continues to dominate the issue tracker, with plugin lifecycle and Computer Use bugs accounting for the majority of high-engagement reports. A wave of merged PRs targeted TUI rendering efficiency, gRPC code-mode session routing, and MCP OAuth/registration improvements.

---

## 2. Releases

| Version | Link |
|---|---|
| `rust-v0.148.0-alpha.7` | [GitHub](https://github.com/openai/codex/releases) |
| `rust-v0.148.0-alpha.8` | [GitHub](https://github.com/openai/codex/releases) |
| `rust-v0.148.0-alpha.9` | [GitHub](https://github.com/openai/codex/releases) |

Progression through the 0.148.0 alpha series continues; no detailed changelog was provided for these builds.

---

## 3. Hot Issues

1. **#20214 — Codex App frequently freezes/stutters on Windows 11 Pro** [Open](https://github.com/openai/codex/issues/20214)
   The highest-engagement issue (96 comments, 81 👍). Users report frequent UI freezes on Windows 11 despite adequate hardware (32 GB RAM, Ryzen 5 5600). Indicates a systemic performance concern on Windows.

2. **#17320 — Excessive SQLite WAL writes during streaming due to TRACE logs ignoring RUST_LOG** [Open](https://github.com/openai/codex/issues/17320)
   31 comments, 39 👍. TRACE-level logs bypass the `RUST_LOG` filter on Linux, causing excessive SQLite WAL writes that degrade I/O performance during streaming.

3. **#25391 — Windows Computer Use plugin fails to bootstrap: native pipe path unavailable** [Open](https://github.com/openai/codex/issues/25391)
   23 comments. The Computer Use native pipe fails to start on Windows 11, blocking browser/computer-use capabilities entirely.

4. **#26562 — Computer Use plugin unavailable in Codex Desktop on Windows** [Open](https://github.com/openai/codex/issues/26562)
   20 comments, 3 👍. Similar report: Computer Use shows as unavailable despite Pro subscription entitlement.

5. **#21670 — Chrome plugin and Browser Use setup hang; plugin uninstall fails with os error 5** [Open](https://github.com/openai/codex/issues/21670)
   15 comments, 7 👍. Chrome native messaging host locks plugin cache, making uninstall and update flows unreliable.

6. **#37403 — macOS Desktop cannot resume Remote Control / CLI thread after Aug 7 update** [Open](https://github.com/openai/codex/issues/37403)
   10 comments, 9 👍. Regression: `already has an active writer` error prevents resuming remote-controlled CLI threads post-update.

7. **#21252 — CLI Option to hide tool activity** [Open](https://github.com/openai/codex/issues/21252)
   9 comments, 17 👍. Strong community interest in a flag to reduce TUI transcript noise from tool-call cells during long sessions.

8. **#34663 — Resume renders full thread history instead of bootstrapping latest turn** [Open](https://github.com/openai/codex/issues/34663)
   8 comments, 5 👍. Performance-related: `codex resume` re-renders the entire thread history rather than starting from the latest turn, causing slowdowns on long sessions.

9. **#32802 — Chrome native host manifest and registry key never created on Windows** [Open](https://github.com/openai/codex/issues/32802)
   7 comments. Plugin reports installed/enabled in Chrome, but the native messaging host registration is never written to the registry.

10. **#30270 — Bundled Browser/Chrome/Computer Use plugins disappear after Windows app updates** [Open](https://github.com/openai/codex/issues/30270)
    12 comments. Stale bundled marketplace path after MS Store auto-updates causes plugins to vanish, requiring manual reinstallation.

---

## 4. Key PR Progress

1. **#38103 — Avoid cloning MCP invocations in TUI history** [Closed](https://github.com/openai/codex/pull/38103)
   Borrows invocation data instead of cloning when rendering TUI history cells, reducing memory pressure during heavy MCP usage.

2. **#38101 — Attach hosted app context to file uploads** [Closed](https://github.com/openai/codex/pull/38101)
   Includes connector ID, action name, and model in file creation requests for hosted app tool calls.

3. **#38094 — Test Guardian context for code mode commands** [Closed](https://github.com/openai/codex/pull/38094)
   Adds integration coverage verifying Guardian receives both the user prompt and outer code-mode `exec` source for nested escalated calls.

4. **#38092 — Simplify queued user message admission** [Closed](https://github.com/openai/codex/pull/38092)
   Resolves admission when Core accepts input as a new turn or steer, without waiting for rollout persistence. Removes hook-specific admission errors.

5. **#38089 — Add CIMD support to MCP OAuth registration** [Closed](https://github.com/openai/codex/pull/38089)
   Automatic MCP OAuth registration now prefers Client ID Metadata Documents (CIMD) when the authorization server advertises public-client support, falling back to advertised dynamic client registration.

6. **#38087 — Route gRPC code-mode sessions through the shared HTTP client** [Closed](https://github.com/openai/codex/pull/38087)
   Code-mode gRPC connections now use `HttpClientFactory`, gaining outbound proxy and custom CA support.

7. **#38086 — Support execution-host context when resolving cloud config** [Closed](https://github.com/openai/codex/pull/38086)
   Introduces `AbsolutePathBufGuard::with_home_directory` override so `~` paths resolve against an explicitly supplied home directory.

8. **#38084 — Allow empty input to start a turn** [Closed](https://github.com/openai/codex/pull/38084)
   Permits immediate user-message admission with no `Op::UserInput` items, allowing turns to proceed using generated environment context alone.

9. **#38080 — Allow nested Git repositories in the Windows sandbox** [Closed](https://github.com/openai/codex/pull/38080)
   Adds both worktree root and `/*` wildcard to sandbox trust rules, fixing the issue where Git rejects nested repos owned by the primary user.

10. **#38078 — Reduce cloning in world-state patch handling** [Closed](https://github.com/openai/codex/pull/38078)
    Deserializes section snapshots directly from borrowed JSON and applies merge patches in place instead of cloning entire snapshots.

---

## 5. Feature Request Trends

- **TUI cleanliness**: Users want finer control over what appears in the transcript. Issue #21252 (17 👍) and the PR on respecting rendered width (#38075) reflect demand for a less noisy, more scannable TUI experience.
- **Model alias/gateway support**: Issue #21594 requests first-class `model_aliases` mapping so enterprise gateway names resolve to canonical Codex model metadata — a recurring need for orgs behind API proxies.
- **Resume performance**: Issue #34663 and the empty-input admission change (#38084) both point to a desire for faster session restoration and leaner turn-start behavior.
- **MCP security & onboarding**: CIMD support (#38089) and the `ReviewDecision`-based MCP approval flow (#38081) show momentum toward smoother, standards-aligned MCP OAuth registration.

---

## 6. Developer Pain Points

**Windows plugin lifecycle is the dominant frustration.** At least a dozen top issues (#25391, #26562, #21670, #25571, #22114, #30270, #28950, #32802, #24296, #32706, #26792, #26929, #25780, #26501, #28275, #28084, #26078, #26151) trace back to the same root causes: the bundled marketplace snapshot becomes stale after app updates, Chrome native messaging hosts lock plugin cache files, and the Computer Use pipe fails to bootstrap on certain Windows builds. This is a high-frequency, cross-version problem affecting Browser, Chrome, and Computer Use skills equally.

**macOS Remote Control regression** (#37403) — an `already has an active writer` error after the Aug 7 desktop update breaks a workflow that multiple users depend on for overnight CLI sessions.

**Linux I/O degradation** (#17320) — TRACE logs bypassing `RUST_LOG` cause excessive SQLite WAL writes, degrading performance during streaming on Linux.

**Windows sandbox limitations** — nested Git repos (#38080) and app-root ACL gaps (#38064) indicate the sandbox permission model still needs refinement for common development workflows.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-12

## 1. Today's Highlights

Gemini CLI released **v0.55.1** and **v0.56.0-preview.1**, with the nightly stream hitting **v0.56.0-nightly.20260812**. A critical security push addressed two CVEs (shell-quote and simple-git) alongside fixes for false capacity-exhaustion errors and an SSRF vulnerability. Community discussion remains focused on shell command hangs and subagent reliability.

---

## 2. Releases

| Version | Key Changes |
|---|---|
| **v0.55.1** | Fixed `npm ci` ignore-scripts for release verification, prevented workspace binary shadowing, tool registry improvements |
| **v0.56.0-preview.1** | Preview release carrying forward v0.55.0 preview changelogs |
| **v0.56.0-nightly.20260812** | Fix for false model capacity exhaustion & quota lookup model mapping; added local eval report command with developer docs |
| **v0.55.0-preview.3** | Cherry-picked patch from PR #28730 for quota/capacity fixes |

🔗 Full changelog: https://github.com/google-gemini/gemini-cli/releases

---

## 3. Hot Issues

1. **[CLOSED] #26911 — 429 Too Many Requests after 5–10 min** (12 comments, 2 👍)
   Users report hitting 429s while under 10% quota, with CLI silently "thinking" for up to an hour. Root cause tied to false capacity-exhaustion messaging — now addressed in v0.55.1/v0.56 nightly. 🔗

2. **#22323 — Subagent reports GOAL success after MAX_TURNS** (12 comments, 2 👍)
   `codebase_investigator` subagent falsely reports success with `Termination Reason: GOAL` even when it hit the turn limit without doing analysis. Critical for eval accuracy. 🔗

3. **#23297 — Pressing Enter does nothing** (11 comments, 10 👍)
   High community support (10 👍). Terminal becomes unresponsive to Enter key; restart required. Likely a TTY/state management bug. 🔗

4. **#24353 — Component-level evaluations** (7 comments)
   Epic tracking 76 behavioral eval tests across 6 supported models. Signals growing investment in eval infrastructure and quality gates. 🔗

5. **#22745 — AST-aware file reads, search, and mapping** (7 comments, 1 👍)
   Investigation into whether AST-aware tools can reduce turn waste from misaligned file reads and noisy tokens. Potential perf win for codebase navigation. 🔗

6. **#21968 — Gemini doesn't use skills/sub-agents enough** (6 comments)
   Anecdotal but widely felt: the model won't autonomously invoke custom skills (e.g., "gradle", "git") unless explicitly prompted. Indicates a gap in skill discovery/triggering. 🔗

7. **#26522 — Auto Memory retries low-signal sessions indefinitely** (5 comments)
   Sessions the extraction agent skips remain unprocessed and get re-surfaced repeatedly. Memory system quality issue. 🔗

8. **#24828 — Sandbox doesn't forward `GOOGLE_GENAI_API_VERSION`** (5 comments)
   When using Vertex-compatible API paths in sandbox mode, the CLI 404s because the env var isn't forwarded. 🔗

9. **#24707 — `run_shell_command` hangs 5 min on interactive commands** (4 comments, 1 👍)
   Hardcoded 5-minute timeout with no way to handle interactive input (e.g., `git pull` credential prompts). 🔗

10. **#26525 — Deterministic redaction & Auto Memory logging** (4 comments)
    Secrets may leak into model context before redaction occurs. Community pushing for pre-context redaction and reduced logging. 🔗

---

## 4. Key PR Progress

1. **#28557 — SSRF vulnerability fix in web-fetch** [CLOSED]
   Switched from sync `isPrivateIp()` to async DNS resolution so hostnames resolving to internal IPs (e.g., `169.254.169.254`) are properly blocked. 🔗

2. **#28691 — Block `$VAR` / `${VAR}` expansion bypass** [OPEN]
   Closes an incomplete check in `detectBashSubstitution()` and `detectPowerShellSubstitution()` that allowed variable expansion to bypass the security gate (GHSA-wpqr-6v78-jr5g). 🔗

3. **#28780 — Upgrade shell-quote to 1.8.4 (CVE-2026-9277)** [OPEN]
   Critical CVE fix; upgrades the shell-quote dependency to patch a security vulnerability. 🔗

4. **#28778 — Upgrade simple-git to 3.32.3 (CVE-2026-28292)** [OPEN]
   Critical CVE fix for the simple-git dependency. 🔗

5. **#28681 — SGLang & local OpenAI-compatible endpoints** [OPEN]
   Adds support for SGLang and local OpenAI-compatible API endpoints, expanding model provider flexibility beyond Google's native APIs. 🔗

6. **#28730 — Fix false capacity exhaustion & quota mapping** [CLOSED]
   Resolves false model capacity exhaustion errors, corrects client-side quota lookup model mapping, and preserves "Keep trying" UI during transient surges. Merged into v0.56.0-nightly. 🔗

7. **#28688 — Cloud Workstations OAuth redirect fix** [CLOSED]
   Dynamically resolves the redirect URI for OAuth flows inside Cloud Workstations VMs instead of hardcoding `localhost`. 🔗

8. **#28678 — OAuth callback timeout leak fix** [OPEN]
   Centralizes OAuth callback server settlement and resource cleanup to prevent stale timeout callbacks and memory leaks. 🔗

9. **#28729 — IDE connection directory mismatch fix** [CLOSED]
   Fixes Gemini CLI's inability to connect to the IDE companion extension under Cider or VS Code forks using virtual/FUSE paths. 🔗

10. **#28369 — Local eval report command** [CLOSED]
    Adds `npm run eval:report` to aggregate pass rates by model from Vitest `report.json` files, with developer documentation. 🔗

---

## 5. Feature Request Trends

- **Agent autonomy & skill discovery** — Users want the model to proactively use custom skills and sub-agents without explicit prompting (#21968).
- **AST-aware codebase tooling** — Interest in AST-based reads/searches to reduce token waste and improve navigation precision (#22745, #22746).
- **Shell command resilience** — Better handling of interactive commands, timeout management, and "waiting input" states (#24707, #25166, #22465).
- **Memory system reliability** — Fixes for Auto Memory retry loops, invalid patch handling, and deterministic secret redaction (#26522, #26523, #26525, #26516).
- **Evaluation infrastructure** — Component-level behavioral evals and local reporting tools are a sustained investment (#24353, #28369).
- **Model provider flexibility** — Demand for SGLang and local OpenAI-compatible endpoints broadens deployment options (#28681).

---

## 6. Developer Pain Points

1. **Quota & rate-limiting false positives** — The 429 / capacity-exhaustion issue (#26911) causes long silent hangs despite low actual quota usage. Now partially patched but community trust is fragile.
2. **Shell command hangs** — Interactive commands (`git pull`, `vite` init) cause the CLI to stall for 5 minutes with no user feedback (#24707, #25166, #22465).
3. **Terminal unresponsiveness** — Pressing Enter doing nothing (#23297) with 10 👍 signals a high-frequency, high-friction bug.
4. **Subagent reliability** — Subagents reporting false success after hitting turn limits (#22323) and being ignored by the main agent (#21968) undermine trust in multi-agent workflows.
5. **Security surface** — Multiple CVEs in dependencies (shell-quote, simple-git) and security bypass vulnerabilities (#28691, #28557) require vigilant dependency auditing.
6. **Memory system edge cases** — Auto Memory retry loops and silent patch failures (#26522, #26523) create noisy, unreliable long-term context.
7. **Sandbox environment forwarding** — Environment variables like `GOOGLE_GENAI_API_VERSION` not propagating into containers (#24828) breaks Vertex-compatible setups.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-12

## 1. Today's Highlights

The Copilot CLI community is buzzing with a wave of issues filed on 2026-08-11 and 2026-08-12, many related to version 1.0.79's config and model handling regressions — including settings being wiped on `/config model`, user-level model defaults not applying in new sessions, and Claude models disappearing from Enterprise accounts. Windows plugin installation continues to be a pain point (Issue #4095 has 14 👍), while session resumption performance degraded significantly in 1.0.74. No new releases landed in the last 24 hours.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| #4095 | Windows plugin update fails with "Access is denied (os error 5)" | Plugin management is broken on Windows when VS Code holds file watcher handles — affects daily workflow. | 14 👍 |
| #4251 | Large session resume OOMs / 70-min stall in v1.0.74 | Memory regression (3–4×) makes long-lived sessions unusable; confirmed via A/B rollback test. | 1 👍 |
| #4431 | `/config model` wipes all settings in `settings.json` | A critical config regression introduced in v1.0.79 that destroys user preferences on model selection. | 0 👍 |
| #4211 | Copilot CLI can't serialize BigInt in MCP responses | Blocks MCP server adoption for any tool returning large numbers; causes task aborts. | 0 👍 |
| #4422 | All Claude models disabled under CLI for Enterprise accounts | Users report Claude models vanishing despite being enabled in GitHub settings; rollback doesn't help. | 3 👍 |
| #3976 | Native `tgrep` indexer OOM-kills on large monorepos | The tgrep experiment has no memory cap, making it unsafe for large codebases. | 0 👍 |
| #4451 | Explicit slash skill reloads redundantly and fails with "Skill not found" | Skills excluded from model invocation are still loaded through the model registry, causing silent failures. | 2 👍 |
| #4437 | `.claude/agents/*/AGENT.md` `model:` field overrides session model for Copilot agents | Copilot custom agents incorrectly inherit model settings from Claude Code agent definitions, breaking BYOK workflows. | 0 👍 |
| #4434 | User-level configured model not used in new sessions | Setting a default model via `/config model` requires a full CLI restart to take effect — surprising and disruptive. | 0 👍 |
| #4442 | Copilot CLI binary contains `adm-zip` v0.5.17 with CVE-2026-39244 (High) | Security scanners flag the CLI binary in Docker images; needs dependency bump. | 0 👍 |

## 4. Key PR Progress

| # | PR | Description |
|---|-----|------------|
| #4449 | Migrate PR automation away from `pull_request_target` | Improves security by keeping untrusted PR input in lower-privilege workflows and isolating repo-write actions. |
| #4428 | Add initial devcontainer configuration | Enables containerized development for the CLI project; LGTM'd. |
| #4452 | Revert 5 copilot/fix with copilot | Closed — reverted a set of fix commits. |

## 5. Feature Request Trends

- **Auto-allow permissions on session start** (#3877): Users want a persistent `permissions.auto_allow_all` setting to avoid repeated approval prompts.
- **Explicit file edit mode** (#4444): Fine-grained control over AI-proposed edits — accept/reject/comment per-change — to reduce "AI slop."
- **Condensed timeline for autopilot** (#2623): Collapse sequential tool calls in autopilot mode to reduce terminal noise.
- **Cross-platform `.claude/rules` support** (#4440): Read `.claude/rules` (and optionally `.agents/rules`) to avoid duplicating instructions across Claude Code and Copilot CLI.
- **Enterprise sandbox policy enforcement** (#4446): Let orgs configure and enforce CLI sandbox usage via policy.
- **Permission prompts distinguishing read vs. write outside cwd** (#4443): Currently every command touching paths outside the working directory prompts for full approval, even read-only operations like `docker compose ps`.

## 6. Developer Pain Points

- **Windows plugin lock contention** (#4095, #4151): File watcher handles held by VS Code on Windows cause persistent "Access is denied" errors on plugin install/update — a recurring and highly upvoted frustration.
- **Config/regression instability in v1.0.79**: Multiple issues (#4431, #4434, #4422) point to a fragile settings pipeline where model selection, session defaults, and Enterprise model availability are all breaking.
- **Session memory blowups**: Large session resume OOMs (#4251) and unbounded `tgrep` indexing (#3976) make the CLI unsafe for long-running or monorepo workflows.
- **MCP compatibility gaps**: BigInt serialization failures (#4211) and OAuth issuer mismatches with GitLab (#4439) limit MCP server adoption.
- **Security flagging**: The vulnerable `adm-zip` dependency (#4442) causes CI/CD pipeline failures for orgs using container scanning.
- **Subagent model handling**: Rubber Duck and custom agent model selection issues (#4380, #4377, #4432) indicate the subagent framework has unresolved model-resolution bugs, especially on BYOK setups.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-12

## 1. Today's Highlights

No new releases were published in the last 24 hours, but community activity remains active with three new issues and eight PRs merged or in progress. The most notable development is an open PR (#2509) introducing configurable thinking effort and a `/effort` slash command, directly addressing long-standing user demand for granular control over model reasoning depth. Meanwhile, a series of reliability fixes from contributor **hobostay** — replacing unsafe `assert` statements with proper exceptions and resolving a TOCTOU race condition — signal continued strengthening of the CLI's production-grade robustness.

## 2. Releases

*No new releases in the last 24 hours.*

---

## 3. Hot Issues

### #1283 — Memory System: Persistent Context Across Sessions
**[OPEN] | Author: CatKang | 34 comments | Created 2026-02-27 | Updated 2026-08-11**
🔗 [Issue #1283](https://github.com/MoonshotAI/kimi-cli/issues/1283)

The most discussed open feature request in the repository. Users want Kimi Code CLI to remember project patterns, code conventions, and preferences across sessions — both auto-managed (AI-generated notes) and manually defined (user instructions via config). With 34 comments and nearly six months of discussion, this reflects a fundamental gap: CLI agents currently start each session with no memory of prior interactions, forcing users to re-establish context repeatedly.

### #2601 — Quote & Reply on AI Responses (Kimi Web)
**[OPEN] | Author: topit | Created 2026-08-11**
🔗 [Issue #2601](https://github.com/MoonshotAI/kimi-cli/issues/2601)

A UX feature request for Kimi Web to support quoting and replying to specific spans of AI-generated content — paragraphs, code blocks, plan steps, or diff explanations. This would enable precise follow-up questions anchored to exact portions of a response, a pattern users are increasingly accustomed to in conversational AI interfaces.

### #2600 — PowerShell 7 Default Path Resolution Failure on Windows
**[OPEN] | Author: RooKichenn | Created 2026-08-11**
🔗 [Issue #2600](https://github.com/MoonshotAI/kimi-cli/issues/2600)

A practical Windows-specific bug: when PowerShell 7 is configured to launch from a non-system drive (e.g., `D:\`), Kimi Code CLI fails to resolve paths correctly. This affects users who deliberately separate their development environment from the OS drive — a growing segment among Windows developers managing multiple workspaces.

---

## 4. Key PR Progress

### #2509 — Configurable Thinking Effort & `/effort` Command **[OPEN]**
🔗 [PR #2509](https://github.com/MoonshotAI/kimi-cli/pull/2509)

The most significant open PR. Introduces a configurable reasoning effort level and a `/effort` slash command, resolving #2501. Builds on prior work (#318 closed, #2499) to expose explicit control over how much the model "thinks" before responding — a feature critical for balancing speed vs. depth in coding tasks.

### #2057 — Replace `assert` with `RuntimeError` in ACP Session **[CLOSED ✅]**
🔗 [PR #2057](https://github.com/MoonshotAI/kimi-cli/pull/2057)

Replaces 5 `assert` statements in `acp/session.py` with proper `RuntimeError` exceptions. Critical fix: Python's `-O` optimization flag strips all assertions, silently disabling invariant checks for tool call states. This PR ensures production safety regardless of runtime flags.

### #2056 — Fix TOCTOU Race in `WireFile.append_record` **[CLOSED ✅]**
🔗 [PR #2056](https://github.com/MoonshotAI/kimi-cli/pull/2056)

Resolves a time-of-check-to-time-of-use race condition where the file could be deleted between `exists()` and `stat()` calls. A real concurrency bug that could cause unhandled exceptions in multi-process or high-throughput scenarios.

### #2055 — Replace `assert` with `AgentSpecError` in Agentspec **[CLOSED ✅]**
🔗 [PR #2055](https://github.com/MoonshotAI/kimi-cli/pull/2055)

Another assertion-safety fix, this time in `agentspec.py`. Replaces `assert agent_spec.extend is None` with a proper `AgentSpecError`, preventing silent bypass when Python is run with `-O`.

### #1328 — Fix File Tool Replacement Count & UI Feedback **[CLOSED ✅]**
🔗 [PR #1328](https://github.com/MoonshotAI/kimi-cli/pull/1328)

Fixes a bug in `StrReplaceFile` where the replacement count was miscalculated when multiple edits were provided — the count was based on `original_content` without accounting for cumulative changes. Also improves UI feedback during file operations.

### #1082 — Fix PyInstaller `dateparser` Cache Collection **[CLOSED ✅]**
🔗 [PR #1082](https://github.com/MoonshotAI/kimi-cli/pull/1082)

Resolves a PyInstaller packaging issue where the lazily-generated `dateparser_tz_cache.pkl` file was referenced even when non-existent, causing collection failures in CI and fresh installs.

### #1077 — Remove Redundant Mode Validation in `WriteFile` **[CLOSED ✅]**
🔗 [PR #1077](https://github.com/MoonshotAI/kimi-cli/pull/1077)

Cleans up redundant runtime validation of the `mode` parameter in `WriteFile`, which was already enforced at a higher level. Reduces code duplication without sacrificing safety.

### #1393 — Route Shell Commands Through Terminal Args in ACP **[CLOSED ✅]**
🔗 [PR #1393](https://github.com/MoonshotAI/kimi-cli/pull/1393)

Fixes ACP shell terminal execution to properly separate the shell executable (`command`) from shell invocation arguments (`args`), adapting to the current ACP SDK response shape using `terminal_id`. Includes regression tests for both bash and PowerShell.

---

## 5. Feature Request Trends

| Trend | Evidence |
|---|---|
| **Persistent session memory** | Issue #1283 — the top-commented open issue; users consistently want the CLI to remember context, preferences, and project patterns across sessions |
| **Granular reasoning control** | PR #2509 (+ prior issues #2501, #318) — repeated demand for configurable thinking effort, suggesting users feel the default reasoning depth is either too shallow or too slow for their workflows |
| **Conversational UX refinements** | Issue #2601 — quote-and-reply on AI responses reflects growing expectation for fine-grained, anchored follow-ups rather than global re-prompts |
| **Windows / cross-platform parity** | Issue #2600 — ongoing path and shell-resolution bugs on Windows suggest the project still needs investment in Windows-first testing and development workflows |

---

## 6. Developer Pain Points

1. **Assertions in production code** — The cluster of PRs #2057, #2056, #2055 all targeting `assert` misuse and race conditions indicates a systemic issue: safety-critical invariants were guarded by assertions that vanish under `-O`. The community is benefiting from this cleanup, but it points to a prior lack of rigor in production error handling.

2. **Windows path and shell resolution** — Issue #2600 is a repeat of a known class of problems. Developers who customize their shell environment (non-default drives, alternative terminals) consistently hit path-resolution bugs, suggesting insufficient coverage of Windows edge cases in CI.

3. **No persistent state between sessions** — Issue #1283's longevity (6 months, 34 comments) reflects genuine frustration: users treat the CLI as a continuing partner, but each invocation is effectively a cold start. This is the single most requested capability and its absence is a competitive disadvantage versus tools that offer memory or context persistence.

4. **Reasoning depth is opaque** — The multi-PR arc around thinking effort (#2501 → #2499 → #2509) shows users feel blind about how much the model is reasoning. Without visibility or control, they can't optimize for speed vs. quality trade-offs — a basic expectation for any developer tool.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-12

## 1. Today's Highlights

OpenCode v2 development saw a productive day with 8 merged and 7 active PRs, led by maintainer `kitlangton`. The community pushed several long-requested slash commands (`/usage`, `/verify`, `/simplify`, `/btw`, `/context`) in a single issue batch, while critical V2 bootstrapping bugs — infinite LLM retries and Linux instance hangs — remain open. No new releases were published in the last 24 hours.

## 2. Releases

None.

## 3. Hot Issues

| # | Title | Status | Engagement |
|---|-------|--------|------------|
| [#16017](https://github.com/anomalyco/opencode/issues/16017) | Add Go plan usage/balance API endpoint | **Closed** | 34 comments · 137 👍 |
| [#27924](https://github.com/anomalyco/opencode/issues/27924) | Infinite compaction loop when compression fails to reduce context | Open | 8 comments |
| [#41763](https://github.com/anomalyco/opencode/issues/41763) | ALSA errors flood and corrupt the terminal during V2 TUI interaction | Open | 5 comments · 1 👍 |
| [#39831](https://github.com/anomalyco/opencode/issues/39831) | Zen: gpt-5.6-luna / gpt-5.6-terra fail with "Upstream request failed" | Open | 5 comments · 1 👍 |
| [#38193](https://github.com/anomalyco/opencode/issues/38193) | Desktop "Add server" dialog: fields cannot be edited | Open | 4 comments · 1 👍 |
| [#41848](https://github.com/anomalyco/opencode/issues/41848) | LLM retry has no max attempts — stream errors cause infinite retry loop | Open | 2 comments |
| [#41806](https://github.com/anomalyco/opencode/issues/41806) | Instance bootstrap hangs forever on Linux — git child never reaped | Open | 2 comments |
| [#41869](https://github.com/anomalyco/opencode/issues/41869) | V1 migration fails with SQLiteError on apostrophes in legacy data | **Closed** | 2 comments |
| [#41905](https://github.com/anomalyco/opencode/issues/41905) | New session inherits previous session cwd instead of launch cwd | Open | 1 comment |
| [#41751](https://github.com/anomalyco/opencode/issues/41751) | Exactly 2 project skills silently dropped when project is a git repo | Open | 2 comments |

**Why they matter:**

- **#16017** — The most-commented and most-upvoted issue in the window; the Go usage/balance API has been tracked for 5 months and was closed, likely shipped. Strong community signal that subscription visibility is a priority.
- **#27924** — A correctness bug that can trap sessions in an infinite compaction loop, consuming tokens and locking the UI. Directly impacts reliability for long-running sessions.
- **#41763 / #41890** — ALSA audio initialization on headless Linux systems corrupts the TUI display. Two related reports in one day indicate this is a persistent V2 regression affecting terminal-only deployments (SSH, mosh).
- **#39831** — A provider-level regression blocking two GPT-5.6 models in Zen mode, suggesting upstream API changes or key rotation issues.
- **#41848** — Missing retry ceiling means a single upstream stream error can freeze the UI indefinitely ("Thinking…" forever), a serious operational risk for server/daemon use.
- **#41806** — Zombie git processes on Linux bootstrap prevent session creation entirely — a blocker for containerized or headless deployments.
- **#41869** — V1 → V2 migration silently corrupts on legacy data containing apostrophes; now closed, likely patched.

## 4. Key PR Progress

| # | Title | Status |
|---|-------|--------|
| [#41918](https://github.com/anomalyco/opencode/pull/41918) | feat(server): workerd runtime profile and SDK entrypoint | Open |
| [#41923](https://github.com/anomalyco/opencode/pull/41923) | feat(tui): surface plugin failures | Open |
| [#41922](https://github.com/anomalyco/opencode/pull/41922) | feat(tui): compact turn token usage with expandable steps | Open |
| [#41900](https://github.com/anomalyco/opencode/pull/41900) | fix(tui): render instruction updates as compact notices | **Closed** ✅ |
| [#41884](https://github.com/anomalyco/opencode/pull/41884) | fix(core): gate tool snapshot on initial MCP registration | **Closed** ✅ |
| [#41883](https://github.com/anomalyco/opencode/pull/41883) | fix(tui): show completed write output | **Closed** ✅ |
| [#41880](https://github.com/anomalyco/opencode/pull/41880) | fix(tui): align running shell output | **Closed** ✅ |
| [#41789](https://github.com/anomalyco/opencode/pull/41789) | fix(core): expose local attachment paths | Open |
| [#41917](https://github.com/anomalyco/opencode/pull/41917) | feat(tui): experiments via devtools bar, drafts stay put | **Closed** ✅ |
| [#41899](https://github.com/anomalyco/opencode/pull/41899) | feat(session): record location switches | **Closed** ✅ |

**Highlights:**

- **#41918** — Enables running OpenCode servers inside Cloudflare Durable Objects (one server per DO), opening the door to Slack-bot-per-thread and other edge-compute deployments.
- **#41923** — TUI now surfaces plugin initialization failures with error details instead of silently ignoring them; critical for debugging MCP/plugin setups.
- **#41922** — Collapses verbose per-turn token tables into a single expandable summary line, dramatically reducing transcript noise on tool-heavy sessions.
- **#41900** — Instruction-update notices (e.g., Code Mode catalog changes) now render as one-liners instead of dumping hundreds of lines into the chat.
- **#41884** — Fixes a race where boot-resumed sessions snapshot tool catalogs before MCP tools are registered, causing stale or missing tool instructions.
- **#41883 / #41880** — TUI polish: restored write-tool output rendering and fixed shell output alignment jumping between running and settled states.
- **#41917** — Experiments are now accessed through the DevTools bar; the `/baldbeard` easter-egg command and `slash.secret` mechanism removed.
- **#41899** — Session location (cwd) switches are now recorded in the timeline and preserved through compaction, fixing context drift during directory changes.

## 5. Feature Request Trends

A concentrated burst of slash-command proposals from a single contributor (`afonsoft`) today signals a clear direction: **bringing Claude Code parity commands into OpenCode's TUI**. The requested commands form a coherent toolkit:

| Command | Purpose |
|---------|---------|
| `/usage` (alias `/cost`) | Session token & cost breakdown |
| `/security-review` | Scan diffs for secret leaks and hardcoded credentials |
| `/verify` | Run local test/lint pipeline to validate repo state |
| `/simplify` | Parallel multi-agent code sweep to deduplicate and refactor |
| `/btw` | Ephemeral side question, excluded from session context |
| `/approve on/off` | Toggle permission approval mode at runtime, per session |
| `/context` | Detailed token/cost breakdown panel per session component |

Additional notable requests:
- **#28191** — Configurable TUI permission-prompt height and default expanded state
- **#18134** — Desktop close-button minimizes to tray instead of exiting
- **#39936** — VS Code notifications when agents complete or need attention
- **#41857** — Ecosystem plugin registration for `opencode-pr-tracker`
- [#41904](https://github.com/anomalyco/opencode/pull/41904) — Claude Code ACP runtime adapter (community PR)

## 6. Developer Pain Points

1. **Infinite retry / hang loops** — Two independent reports (#41848: unbounded LLM retry; #27924: compaction loop) show that missing exit conditions in async pipelines freeze the UI. This is a structural reliability concern for server/daemon deployments.

2. **ALSA audio on headless systems** — V2 TUI repeatedly initializes ALSA even when no sound card exists, corrupting the terminal display (#41763, #41890). Users on SSH/mosh sessions are disproportionately affected.

3. **V1 → V2 migration fragility** — Legacy data containing single quotes breaks SQL interpolation during migration (#41869, now closed). This affects anyone upgrading from pre-v2 installations with existing session data.

4. **Plugin system instability** — False-positive "failed" plugin entries from leftover smoke-test plugins (#41897, closed), fractional mtime specifier bugs (#41891, closed), and now silent plugin failures (#41923, open) indicate the plugin discovery layer is still maturing.

5. **Desktop UX gaps** — Non-editable form fields in the "Add server" dialog (#38193) and missing tray-minimize behavior (#18134) point to unfinished desktop polish.

6. **Context inheritance bugs** — New sessions inheriting the wrong cwd (#41905) and project skills being silently dropped in git repos (#41751) suggest the daemon's session-isolation layer has edge-case gaps.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-12

## 1. Today's Highlights

Pi developers are actively resolving authentication reliability issues with GitHub Copilot (multiple 429 rate-limit and WSL hang bugs closed) while the coding-agent team shipped Mermaid diagram rendering improvements and a Qwen CN provider. A notable regression in streaming `usage` reporting from v0.84.0 is being fixed in PR #7982.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **[CLOSED] #6187 — Pi login hangs in WSL after Copilot device authorization** (25 comments)
   The most-discussed issue this cycle: browser-based GitHub Copilot device auth completes, but the WSL pi client never detects it. Community validation was strong; closed after a fix landed.

2. **[OPEN] #7730 — High CPU usage on macOS with long sessions** (10 comments · 8 👍)
   CPU swings between 50–110% during extended sessions, memory at 600–800 MB. Likely linked to context size or session length. Still open with strong community signal.

3. **[CLOSED] #7846 — Unable to start 0.84.0/0.84.1 with Bun runtime** (10 comments)
   Uncaught `TypeError: zlib.createZstdDecompress is not a function` in undici. Closed, suggesting a version-specific runtime incompatibility workaround or fix.

4. **[OPEN] #7553 — Configurable thinking level for compaction** (8 comments)
   Compaction unconditionally reuses the session's thinking level, making auto-compaction on reasoning models wasteful. A feature request to decouple compaction's thinking budget.

5. **[CLOSED] #7444 — WebSocket retry only handles two error codes** (8 comments)
   In `openai-codex-responses.js`, only `previous_response_not_found` and `websocket_connection_limit_reached` are retried; all other `response.failed` frames hard-stop the turn. Closed, likely fixed.

6. **[CLOSED] #7850 — Copilot login fails with 429 for orgs with many models** (7 comments · 7 👍)
   Organizations with 20+ activated models hit rate limits during device authorization. The 👍 count matches comments, indicating high community relevance.

7. **[OPEN] #7836 — Edit fuzzy match misses whitespace-differing lines** (6 comments · 1 👍)
   `normalizeForFuzzyMatch` doesn't collapse whitespace runs or strip leading whitespace, causing edit `oldText` fuzzy matching to fail on functionally identical content.

8. **[CLOSED] #7760 — LaTeX `\frac` renders incorrectly when denominator spans lines** (5 comments)
   Display-mode fractions with a multi-line denominator drop the denominator text and append it after the fraction bar. Closed after fix.

9. **[CLOSED] #7428 — Copilot subscription login fails with 429** (5 comments)
   Similar to #7850 but on personal subscriptions. Both closed as related/root-caused together.

10. **[OPEN] #7829 — Invalid `settings.json` silently ignored; misleading "bash not found" on Windows** (3 comments)
    Unescaped backslashes in a Windows path produce invalid JSON that is silently dropped, then the shell path fallback triggers a confusing error. Good catch on error UX.

## 4. Key PR Progress

1. **#7989 — feat(ai): add Qwen Token Plan Individual CN provider** (open)
   Adds the `qwen-token-plan-individual-cn` provider for the China region, mirroring #7659. Closes #7847.

2. **#7982 — fix(coding-agent): preserve usage in streaming events** (open)
   Restores cumulative `usage` on JSON and RPC `message_update` events stripped by the v0.84.0 fix for #7290. Closes #7911.

3. **#7981 — fix(ai): map models.dev cost tiers for every provider** (open)
   Extends `getModelsDevCost` to all providers instead of only the GitHub Copilot block, fixing inconsistent cost reporting. Closes #7912.

4. **#7956 — feat(coding-agent): render Mermaid diagrams in HTML exports** (open)
   Translates ANSI-rendered Mermaid tool calls into HTML so exports match the TUI rendering. Toggleable from the header.

5. **#7984 — fix(coding-agent): update grok-mermaid to 0.2.3** (open)
   Brings in upstream Mermaid rendering fixes; classes still ignored for now.

6. **#7978 — fix(edit): normalize single-object edits to array + collapse whitespace** (closed)
   Bundles both the single-object argument normalization and the fuzzy-match whitespace fix into one PR, addressing #7836 and a related edit schema issue.

7. **#7904 — fix(edit): normalize single-object edits argument to array** (closed)
   Standalone fix for models that pass a single `{oldText, newText}` object instead of an array to the edit tool.

8. **#7866 — feat(tui): add copyOnSelect option to TuiAltScreen** (closed)
   New `copyOnSelect` boolean option (default `true`) lets users disable automatic clipboard copy on mouse selection in fullscreen TUI mode.

9. **#7865 — fix(tui): handle pageUp/pageDown in SelectList and model-selector** (closed)
   Adds missing `tui.select.pageUp`/`pageDown` keybindings to the base `SelectList` component, fixing pagination in all selectors.

10. **#7905 — fix(config): refine pnpm detection and validate managed install** (closed)
    Fixes false-positive pnpm detection when the binary exists under `$PNPM_HOME` but isn't actually managing the project.

## 5. Feature Request Trends

- **Compaction & thinking control** (#7553): Users want independent thinking budgets for compaction vs. normal turns, especially on reasoning models.
- **Inline images in tmux via Kitty DCS** (#7936): Request to enable image rendering inside tmux when the outer terminal supports Kitty graphics.
- **Session-to-session messaging (intercom)** (#7968): Experimental live chat between running pi sessions for handoff Q&A and co-op workflows.
- **Qwen CN provider** (#7989): Community demand for first-class China-region provider support.
- **Theme override at runtime** (#7722): `--use-theme` flag for per-run theme selection without persistent config changes.

## 6. Developer Pain Points

- **Copilot auth reliability**: Three separate issues (#6187, #7850, #7428) centered on GitHub Copilot login failures — WSL hangs, 429 rate limits on orgs with many models, and subscription-specific failures. This is the dominant pain point this cycle.
- **WebSocket retry gaps** (#7444): The retry logic covers only two error codes; transient `response.failed` frames from other providers hard-stop turns.
- **Streaming `usage` regression** (#7911, #7982): The v0.84.0 fix for #7290 inadvertently removed cumulative usage from wire events, breaking monitoring.
- **Edit tool schema rigidity**: Models wrapping arguments as a single object instead of an array cause hard failures (#7836, #7904, #7978). The fuzzy-match whitespace issue adds to edit reliability concerns.
- **Invalid config silences errors**: Bad `settings.json` (e.g., unescaped Windows paths) is silently ignored, producing misleading downstream errors (#7829).
- **Fullscreen TUI clipboard inconsistency**: OSC 52 clipboard writes fail on several terminal emulators, making "Copied!" a lie (#7972).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-12

## 1. Today's Highlights
Qwen Code v0.21.10 introduces ACP reasoning‑effort configuration and Web‑Shell image preview, while a security patch bumps `sharp` to `0.35.0` to address a reported vulnerability. Community discussion centers on session‑restore stability, terminal‑rendering flickers in tmux/iTerm, and daemon performance improvements.

## 2. Releases
- **v0.21.11‑preview.0** – Prompt‑safe session navigation and session‑continuation logging.  
  [Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.11-preview.0)
- **v0.21.10** – ACP support for configurable reasoning effort (Default → Max), image preview in Web‑Shell, and other fixes.  
  [Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.10)
- **DSW‑EAS smoke** – Non‑production infrastructure smoke test; no SWE score published.  
  [Release](https://github.com/QwenLM/qwen-code/releases/tag/dsw-eas-smoke-20260812-281542bfdc)

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [#8678](https://github.com/QwenLM/qwen-code/issues/8678) | Preserve session on large restore timeout | Session‑restore reliability is critical for daemon users; a timeout can lose context. | 7 comments; implementation split into multiple PRs. |
| [#8562](https://github.com/QwenLM/qwen-code/issues/8562) | tmux flickering on macOS via SSH | Affects remote‑development workflows; screen flicker disrupts interaction. | 6 comments; similar to #8901 and #8962. |
| [#8504](https://github.com/QwenLM/qwen-code/issues/8504) | Provider‑update prompt repeats with custom models | Stale configuration prompts degrade the user experience and may cause confusion. | 5 comments; closed after fix. |
| [#8827](https://github.com/QwenLM/qwen-code/issues/8827) | Harden terminal‑teardown invariants | Improves test reliability and prevents edge‑case crashes during session cleanup. | 4 comments; follow‑up to #7837. |
| [#8959](https://github.com/QwenLM/qwen-code/issues/8959) | CI failure on E2E tests | Blocking for main‑branch development; indicates a regression in the test suite. | 4 comments; auto‑tracked by CI bot. |
| [#8901](https://github.com/QwenLM/qwen-code/issues/8901) | iTerm flickering on macOS | Direct terminal‑rendering bug that impacts daily use. | 4 comments; similar to #8562. |
| [#8897](https://github.com/QwenLM/qwen-code/issues/8897) | `--approval‑mode` and `--auth‑type` missing from `--help` | CLI usability issue; flags are registered but not documented in help output. | 4 comments; reported as a documentation gap. |
| [#8920](https://github.com/QwenLM/qwen-code/issues/8920) | OpenAI API errors emit success in `stream‑json` mode | Headless/error‑handling regression that masks real failures. | 4 comments; critical for automation pipelines. |
| [#8644](https://github.com/QwenLM/qwen-code/issues/8644) | Clicking file links fails on Windows | Cross‑platform compatibility bug; drive‑letter colon is URL‑encoded. | 4 comments; affects VS Code integration. |
| [#8182](https://github.com/QwenLM/qwen-code/issues/8182) | Daemon allocates full host memory to each ACP child | Memory‑usage bug that can lead to OOM kills when multiple children are spawned. | 4 comments; high‑impact performance issue. |

## 4. Key PR Progress
| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#8927](https://github.com/QwenLM/qwen-code/pull/8927) | `feat(channels): bound session lifetime with sessionRotation` | Open | Adds per‑channel `sessionRotation` to limit how long a route keeps the same session. |
| [#8736](https://github.com/QwenLM/qwen-code/pull/8736) | `fix(core): sweep peer socket files left behind by killed sessions` | Closed | Cleans up orphaned socket files after session termination. |
| [#8733](https://github.com/QwenLM/qwen-code/pull/8733) | `feat(core): address other sessions by name from send_message and list_agents` | Closed | Enables cross‑session messaging and agent listing by name. |
| [#8730](https://github.com/QwenLM/qwen-code/pull/8730) | `feat(core): accept cross‑session messages behind an inbound gate` | Closed | Introduces a gated channel for inter‑session communication. |
| [#7800](https://github.com/QwenLM/qwen-code/pull/7800) | `feat(cli): Add agent view PTY workers` | Open | Stacked PR adding PTY worker host layer for managed Agent View sessions. |
| [#8732](https://github.com/QwenLM/qwen-code/pull/8732) | `feat(cli): adopt Goal v3 in ACP sessions` | Open | Replaces legacy `/goal` hook with the canonical Goal v3 state machine. |
| [#8568](https://github.com/QwenLM/qwen-code/pull/8568) | `feat(computer‑use): use Qwen CUA driver by default` | Open | Switches built‑in Computer Use backend from `trycua` to the vendored Qwen CUA driver. |
| [#8872](https://github.com/QwenLM/qwen-code/pull/8872) | `feat(web‑shell): improve thinking and tool progress display` | Open | Enhances Web‑Shell compact mode with better thinking‑row handling and aggregate views. |
| [#8714](https://github.com/QwenLM/qwen-code/pull/8714) | `feat(core): add native DashScope integration` | Open | Adds a first‑class `dashscope` auth type that uses Alibaba ModelStudio’s native API wire format. |
| [#8675](https://github.com/QwenLM/qwen-code/pull/8675) | `feat(web‑shell): add model‑specific reasoning controls` | Open | Introduces a reasoning‑controls registry for Think and Effort across Core, ACP, daemon, SDK, and WebShell. |

## 5. Feature Request Trends
- **Session management** – Requests for bounded session lifetimes, selective restore, and cross‑session communication are frequent (#8927, #8733, #8730, #8743).
- **Performance & memory** – Users consistently ask for daemon memory‑allocation fixes and reduced rendering overhead (#8182, #8091, #8608).
- **UI/UX improvements** – Interest in better text selection, compact progress displays, and cleaner context‑usage presentation (#8738, #8872, #8695).
- **Integration & extensibility** – Demand for native DashScope support, updated Computer Use drivers, and more granular model‑specific controls (#8714, #8568, #8675).

## 6. Developer Pain Points
- **Terminal‑rendering flickers** – Multiple reports of screen flickering in tmux and iTerm on macOS, especially over SSH/remote sessions (#8562, #8901, #8962).
- **Session‑restore stability** – Large restores can timeout or lose context, causing frustration for daemon and ACP users (#8678, #8837).
- **Memory‑allocation bugs** – Daemon incorrectly allocates full host memory to each ACP child, leading to OOM risks (#8182).
- **CLI usability gaps** – Hidden flags, missing help entries, and inconsistent slash‑command history feedback (#8897, #8365).
- **Error‑handling regressions** – Headless `stream‑json` mode masks API failures as successful runs (#8920).
- **Cross‑platform compatibility** – Windows file‑link clicking fails due to URL‑encoding of drive‑letter colons (#8644).

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026‑08‑12

## 1. Today's Highlights
A critical regression in v0.9.5 (Issue #5323) silently blocks Bash and write operations in Auto‑Review mode, while maintainers address schema complexity to prevent model‑parsing errors (Issue #5324). Community feedback highlights persistent UX bugs in copy functionality (Issue #5314) and terminal‑width handling (Issue #5322) as top concerns.

## 2. Releases
*No new releases in the last 24 hours.*

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| #5323 | [bug] Regression in v0.9.5: Auto‑Review mode silently blocks every Bash call and write operation | Breaks autonomous workflows that rely on tool‑call auto‑approval; urgent for users on the latest release. | 2 comments, opened today. |
| #5324 | agent tool: simplify the 32‑field schema so models stop erroring on it | Directly reduces model‑tool mismatch errors; will improve reliability of agent interactions. | 0 comments, opened today. |
| #5314 | Copy message from context menu includes rail decorations (● ▏) | UX bug that makes copied transcript content unusable for external editing or pasting. | 2 comments, flagged as cosmetic/UX. |
| #4683 | Wrong deepseek completions url | Flaky network error that appears after long sessions; affects API connectivity stability. | 3 comments, labeled `bug`, `needs‑info`. |
| #4564 | codewhale exec --auto: --model and --toolsets flags consumed as single arg on Windows | Platform‑specific regression that breaks pre‑exec flag parsing on Windows installs. | 2 comments, labeled `bug`, `needs‑info`. |
| #5241 | Pricing endpoint returns 503 – all sessions show unverified_live_pricing | Breaks cost tracking across all providers; session‑level pricing data becomes unreliable. | 1 comment, labeled `needs‑info`. |
| #5322 | Regression: output area doesn't fill wide terminals (worked in v0.8.65) | UX regression that cramps text on wide displays; affects readability and workspace utilization. | 1 comment, labeled `bug`. |
| #4568 | 新版斜杠指令(/xxx)响应迟缓,性能不如上一版本 | Performance regression noticed by Chinese‑language users; slash commands feel noticeably slower. | 1 comment, labeled `needs‑info`. |
| #1261 | Pane zooming support | Long‑standing feature request for expanding table/pane content beyond terminal width; improves screen‑real‑estate management. | 1 comment, labeled `enhancement`. |
| #5316 | EPIC‑005: CodeWhale TUI Crate Decomposition (Umbrella) | Architectural refactor that will split the TUI crate into smaller, maintainable units; critical for long‑term project health. | 2 comments, labeled `epic`. |

## 4. Key PR Progress

| # | PR | Description | Status |
|---|-----|-------------|--------|
| #5326 | web: audit fixes — i18n parity, copy/spacing, test fixes | Polishes the community website; fixes i18n parity and copy/spacing issues; test corrections. | Open |
| #5318 | feat(tui): pin host terminal window as an always‑on‑top mini window | Adds a “shrink and pin on top” (PiP) capability for the host terminal on Windows; toggles between 640×400 pinned window and restored state. | Open |
| #5321 | feat: register OrcaRouter as a named provider | Extends provider support by registering OrcaRouter alongside existing OpenAI‑compatible gateways; unlocks 150+ models via a single API key. | Open |
| #5320 | fix(session): separate snapshot reads from crash recovery | Introduces side‑effect‑free snapshot reads (`load_session_snapshot`) and a dedicated crash‑recovery path (`recover_session_for_resume`) to improve session reliability. | Open |
| #5319 | fix(tui): copy messages without visual rails | Addresses Issue #5314 by copying canonical source content (user/assistant cells) instead of rendered Ratatui lines; preserves rail‑free copy. | Open |
| #5225 | feat(acp): expose file/search/git/patch/shell tools over session/prompt | Closes a feature gap by enabling ACP‑driven editors (Zed, third‑party adapters) to execute tool calls through the `session/prompt` stream. | Closed |

## 5. Feature Request Trends
- **Better command control for autonomous modes** – Request for a `/stop` command (Issue #4959) to allow runtime interruption of tool‑call loops in YOLO/autonomous workflows.
- **Performance optimization for slash commands** – Users report noticeable latency in v0.9.x (Issue #4568), indicating a demand for command‑dispatch speed improvements.
- **Flexible terminal layout options** – Long‑standing requests for pane zooming (Issue #1261) and wider output area filling (Issue #5322) reflect a desire for better use of modern wide displays.
- **Simplified configuration schemas** – The push to reduce the 32‑field agent tool schema (Issue #5324) shows a trend toward making tool definitions more model‑friendly and less error‑prone.

## 6. Developer Pain Points
- **Network connectivity instability** – Flaky API URLs (Issue #4683) and connection failures (Issue #4956) cause intermittent session errors.
- **Platform‑specific parsing bugs** – Windows flag consumption (Issue #4564) and potential shell‑escaping issues highlight the need for cross‑platform consistency.
- **Regressions in UX and behavior** – Auto‑Review blocking (Issue #5323), terminal‑width capping (Issue #5322), and stale UI hints (Issue #5291) erode user confidence after upgrades.
- **Complex tool schemas causing model errors** – The 32‑property agent tool schema (Issue #5324) leads to frequent parsing failures, adding friction to agent‑tool integration.
- **Pricing endpoint reliability** – 503 errors and `unverified_live_pricing` flags (Issue #5241) break session‑cost tracking, affecting billing transparency.

---
*Data sourced from github.com/Hmbown/DeepSeek‑TUI (Issues & PRs updated within the last 24 hours). This digest is generated for technical analysis purposes.*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*