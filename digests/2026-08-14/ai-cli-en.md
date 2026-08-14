# AI CLI Tools Community Digest 2026-08-14

> Generated: 2026-08-14 02:26 UTC | Tools covered: 10

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
**Date: 2026-08-14**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem is in a rapid consolidation phase, with all major vendors shipping multi-agent orchestration, provider-agnostic routing, and hardened security controls within the same window. Community activity is dominated not by new feature announcements but by reliability regressions—cross-session messaging, OAuth flows, and context compaction are the universal friction points. The landscape splits into three tiers: platform-backed tools (Claude Code, Codex, Copilot, Qwen) with frequent releases and infrastructure investment; independent projects (OpenCode, Pi, CodeWhale) iterating on UX and extensibility; and laggards (Kimi Code CLI, Grok Build) with minimal community velocity.

---

## 2. Activity Comparison

| Tool | Hot Issues | PRs Updated | Releases | Release Cadence |
|---|---|---|---|---|
| **Claude Code** | 10 | 2 | v2.1.232, v2.1.231 | Daily patch cycle |
| **OpenAI Codex** | 10 | 10 | 4 alpha (0.148.0-alpha.11–14) | Rapid alpha sweep |
| **Gemini CLI** | 10 | 10 | v0.56.0-nightly | Nightly builds |
| **GitHub Copilot CLI** | 9 | 1 | v1.0.80-0, v1.0.80-1 | Weekly patch |
| **Kimi Code CLI** | 3 | 0 | None | Stalled |
| **OpenCode** | 10 | 10+ | None | No recent release |
| **Pi** | 10 | 10 | None | No recent release |
| **Qwen Code** | 10 | 10 | v0.21.11, v0.21.12-preview.1 | Bi-weekly stable |
| **CodeWhale** | 10 | 8 | v0.9.7 | Weekly |
| **Grok Build** | 0 | 0 | None | Inactive |

> **Note:** PR counts reflect activity in the last 24h. Claude Code and Copilot CLI show issue-heavy cycles; Codex, Gemini, Qwen, and OpenCode show balanced PR+issue velocity.

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|---|---|---|
| **Multi-agent / cross-session orchestration** | Claude Code, Codex, Qwen Code, Pi | Direct inter-session communication, fleet coordination, subagent reliability, background work queuing |
| **Context compaction & fidelity** | Claude Code, Codex, Pi, OpenCode | Accurate token tracking, preserving instructions across compaction, preventing premature compaction |
| **MCP OAuth & server reliability** | Claude Code, Codex, Copilot CLI, OpenCode | OAuth port conflicts, scope mismatches, silent failures across all four tools |
| **Provider-agnostic / multi-provider support** | Codex, Gemini CLI, Pi, Qwen Code | Bedrock, Ollama, Vertex AI, local models—users demand flexibility beyond the native provider |
| **Auto Memory / persistent context** | Gemini CLI, Kimi Code CLI, Codex | Cross-session memory, deterministic redaction, signal-quality filtering |
| **Subagent reliability & governance** | Gemini CLI, Claude Code, Codex, CodeWhale | Turn-limit abuse, silent failure claims, permission boundaries, explicit consent |
| **Windows-specific regressions** | Claude Code, Codex, Copilot CLI, Qwen Code, CodeWhale | Packaging (MSIX/AppX), paste/Input leaks, socket errors, stale processes |

---

## 4. Differentiation Analysis

| Dimension | Platform-Backed Tools | Independent Tools |
|---|---|---|
| **Focus** | Infrastructure depth: multi-agent fleets, Guardian hooks, telemetry, enterprise SSO | UX polish, localization, extensibility, community-driven features |
| **Release model** | Frequent patches + alpha sweeps; regression-prone but fast to fix | Irregular releases; slower to ship but often more stable per release |
| **Agent architecture** | Leader-follower with bounded delegation (Codex, Qwen), fork-based subagents (Claude Code) | Plugin/hook systems (OpenCode, Pi, CodeWhale) with user-controlled tool scopes |
| **Security posture** | Guardian V2 (Codex), PreToolUse hooks (Claude Code, Pi), A2A auth hardening (Gemini) | SSRF gaps (OpenCode), supply-chain RCE (Gemini), context-pruning integrity (OpenCode) |
| **Target user** | Enterprise teams, CI/CD pipelines, multi-session operators | Individual developers, open-source contributors, localization-first users |

**Notable divergence:** Qwen Code is the only tool shipping a native `/coordinate` fleet command with an RFC-driven architecture. Claude Code leads in subagent forking with prompt-cache inheritance. Codex leads in provider expansion (Bedrock, Ollama compat). OpenCode and Pi lead in plugin/hook extensibility. Kimi Code CLI and Grok Build are effectively dormant.

---

## 5. Community Momentum & Maturity

| Tier | Tools | Signal |
|---|---|---|
| **High momentum, rapid iteration** | Codex, Gemini CLI, Qwen Code | 10+ PRs/week, nightly/alpha releases, active RFCs, multi-provider roadmaps |
| **Mature but regression-prone** | Claude Code, Copilot CLI | Strong feature velocity (subagent forking, `@` mentions) but significant cross-session and OAuth regressions per cycle |
| **Steady but smaller community** | OpenCode, Pi, CodeWhale | Balanced PR/issue ratio, strong UX focus, but fewer contributors and slower release cycles |
| **Declining / inactive** | Kimi Code CLI, Grok Build | Minimal issue volume, no releases, no PR activity—signals low community engagement or prioritization |

**Community health indicators:**
- Claude Code: 12+ cross-session issues in one cycle = feature-gap signal
- Codex: 18 PRs merged in one sweep = strong engineering throughput
- Gemini CLI: CVE and RCE patches shipped same week = security-aware community
- OpenCode: Write-tool hang (#11112) with 78 comments = deep user attachment despite reliability pain

---

## 6. Trend Signals

1. **Multi-agent is the arms race.** Every major tool is shipping fleet coordination (Qwen `/coordinate`, Codex thread queues, Claude `@` mentions, Gemini subagent governance). The question is no longer *if* but *how well*—and all tools are currently shipping regressions in this area.

2. **Context management is the new frontier.** Premature compaction (Claude Code #53065), silent instruction loss (OpenCode #42437), and compaction-aware retention (Codex #38445) are all symptoms of tools outgrowing their context-handling architectures. Expect this to stabilize before end of 2026.

3. **MCP is the new POSIX.** OAuth regressions span Claude Code, Codex, Copilot CLI, and OpenCode in the same week. MCP is becoming the standard tool-integration layer, but provider implementations are immature. Developers should expect breakage on upgrades.

4. **Windows is the weakest platform across the board.** Every major tool has Windows-specific regressions (MSIX packaging, paste input, socket errors, stale processes). Linux/macOS remain the primary development targets.

5. **Security patches are accelerating.** Gemini CLI's supply-chain RCE fix (#28740), CodeWhale's model-guardian tier (#5353), and OpenCode's SSRF/context-pruning disclosures (#42435, #42437) show the ecosystem is maturing past "ship fast" into "ship safe." Tools without this posture (Kimi, Grok) are falling behind.

6. **Local-first routing is gaining traction.** CodeWhale's DS4 first-class setup (#5365), Codex's Bedrock provider (#38470), and Pi's Bedrock Mantle integration (#6216) signal that cost control and data sovereignty are driving provider diversification beyond cloud APIs.

---

*Report generated from community digest data across 10 AI CLI tools as of 2026-08-14.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-14 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking — Most-Discussed PRs

| # | PR | Skill / Focus | Status | Key Highlights |
|---|-----|--------------|--------|----------------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` — `run_eval.py` recall fix + Windows support | 🔵 Open | Fixes critical bug where evaluation reports 0% recall across all skills (#556, 10+ repros). Also addresses Windows stream reading, trigger detection, and parallel worker crashes. |
| 2 | [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` — mechanical verification + reasoning quality gate (v1.3.0) | 🔵 Open | Audits AI output before delivery: file-existence checks first, then four-dimension reasoning audit. Universal — any project, any stack. |
| 3 | [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` — typographic quality control | 🔵 Open | Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | `odt` — OpenDocument text creation & template filling | 🔵 Open | Covers .odt, .ods, .odf, LibreOffice documents; triggers on ODT/ODS/ODF/OpenDocument/LibreOffice keywords. |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` — full testing stack | 🔵 Open | Covers Testing Trophy model, AAA unit tests, React Testing Library, edge cases, and what *not* to test. |
| 6 | [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` — enterprise platform skill | 🔵 Open | Broad ServiceNow assistant: ITSM, ITOM, ITAM/SAM, FSM, HRSD/CSM, SPM/PPM, Vulnerability Response, Security IR, IntegrationHub. |
| 7 | [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` + `skill-security-analyzer` | 🔵 Open | Meta-skills evaluating structure/docs (20%), test coverage, security patterns, and more across the five-dimension rubric. |
| 8 | [#210](https://github.com/anthropics/skills/pull/210) | `frontend-design` — clarity & actionability rewrite | 🔵 Open | Revised to ensure every instruction is directly actionable by Claude within a single conversation. |

---

## 2. Community Demand Trends

Distilled from Issues and proposal PRs, the strongest demand signals are:

- **Skill evaluation & quality tooling** — The `run_eval.py` recall bug (#556, #1169, fixed in #1298) drew 12+ comments and 7 👍. The community wants reliable skill testing and validation.
- **Enterprise / platform-specific skills** — ServiceNow (#568, active since March), SAP-RPT-1-OSS (#181), and SharePoint security concerns (#1175) show appetite for domain-specific skills beyond generic coding.
- **Meta-skills for skill governance** — `skill-quality-analyzer` (#83), `agent-governance` (#412, closed proposal), and the Reasoning Quality Gate pipeline (#1385) all target skill lifecycle management and safety.
- **Cross-org skill sharing** — Issue #228 (16 comments, 8 👍) is the highest-engagement feature request: org-wide skill libraries instead of manual .skill file sharing.
- **Memory & context efficiency** — `compact-memory` proposal (#1329, 9 comments) and the `claude-api` context-bloat issue (#1487) signal demand for skills that manage agent state and token budgets.
- **Security & trust boundaries** — Issue #492 (43 comments, 2 👍) exposed community skills impersonating official Anthropic skills under the `anthropic/` namespace — a trust vulnerability.

---

## 3. High-Potential Pending Skills

These PRs have active discussion and address clear community pain points — strong candidates for near-term merge:

| PR | Skill | Why It May Land Soon |
|----|-------|---------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval + Windows fixes | Blocks the entire skill-creation pipeline; 10+ independent repros of the recall bug. |
| [#538](https://github.com/anthropics/skills/pull/538) | `pdf` case-sensitivity fix | Single-issue fix (8 reference mismatches); low risk, high impact on Linux/macOS users. |
| [#541](https://github.com/anthropics/skills/pull/541) | `docx` tracked-change ID collision | Prevents document corruption — a concrete correctness bug with a clear root cause. |
| [#539](https://github.com/anthropics/skills/pull/539) | `skill-creator` YAML warning | One-line validation addition preventing silent description truncation. |
| [#1099](https://github.com/anthropics/skills/pull/1099) | `skill-creator` Windows pipe fix | Directly enables Windows skill development; complements #1298. |
| [#1050](https://github.com/anthropics/skills/pull/1050) | `skill-creator` Windows subprocess fix | `[WinError 2]` on `claude.cmd` — another Windows enablement fix. |
| [#1538](https://github.com/anthropics/skills/pull/1538) | Spec compliance cleanup | Brings two skills in line with the Agent Skills spec the repo implements. |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` platform skill | Largest scope new-skill PR; covers an entire enterprise platform with active maintenance (last updated Aug 12). |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable skill evaluation tooling and Windows compatibility** — the `skill-creator` pipeline is broken for a significant user base, and until `run_eval.py` reports accurate recall, skill quality and onboarding remain bottlenecked.

---

*Report generated from [github.com/anthropics/skills](https://github.com/anthropics/skills) PR and Issue data.*

---



# Claude Code Community Digest — 2026-08-14

## 1. Today's Highlights

Claude Code v2.1.232 shipped with two major features: **subagent forking enabled by default** (inheriting full conversation and prompt cache) and **`@` mention support** to reference other Claude sessions by name. Meanwhile, the community is grappling with a wave of cross-session messaging regressions introduced in v2.1.227 that are silencing or dropping messages between sessions on Windows Desktop, while an active issue (#84352) flags that CVP-approved organizations are still hitting cyber-safeguard blocks.

---

## 2. Releases

### v2.1.232
- **Subagent forking enabled by default**: `subagent_type: "fork"` subagents now inherit the full conversation and prompt cache; non-teammate agents spawn in the background by default in interactive sessions.
- **`@` mention support**: Type `@` in the prompt to mention another Claude session by name.
- 🔗 [Release page](https://github.com/anthropics/claude-code/releases)

### v2.1.231
- Fixed **MCP OAuth sign-in** failing with a redirect URI mismatch for servers using a pre-registered OAuth client (e.g. Slack).
- 🔗 [Release page](https://github.com/anthropics/claude-code/releases)

---

## 3. Hot Issues

### 🔥 #84352 — CVP-approved org still hits cyber safeguard blocks
**94 comments · 14 👍** · A Claude.ai organization with prior Cyber Verification Program approval continues to receive safeguard blocks in Claude Code, despite the portal showing the application as "Under review." High community impact for enterprise users.
🔗 [Issue #84352](https://github.com/anthropics/claude-code/issues/84352)

### 🔥 #24798 — Inter-session communication for multi-Claude workflows
**66 comments · 21 👍** · Feature request for direct project workflow between siloed Claude sessions — users run multiple sessions in parallel and need a way to sequence dependent processes. Strongest upvoted issue in the period.
🔗 [Issue #24798](https://github.com/anthropics/claude-code/issues/24798)

### 🔥 #85603 — Typed input mid-turn silently dropped at turn end
**22 comments · 1 👍** · Text typed while a turn is running in the interactive TUI (inside tmux) is silently dropped at turn end — affects long-running agent sessions on macOS.
🔗 [Issue #85603](https://github.com/anthropics/claude-code/issues/85603)

### #53065 — `advisor()` inflates reported input tokens, triggering premature auto-compaction
**15 comments · 7 👍** · The advisor tool forwards the full transcript to a second model; its token usage is summed into the top-level `usage` block, causing auto-compaction to fire at ~50% of the real context window. Confirmed across Windows and Linux.
🔗 [Issue #53065](https://github.com/anthropics/claude-code/issues/53065)

### #86012 — Cross-session messages leave recipient unresponsive until idle timeout kills it
**15 comments · 3 👍** · After receiving a cross-session message, the target session's query remains unresponsive (`hadFirstResponse=false`, `reason=no_response`) for 15–20 minutes until the Desktop idle-timeout force-kills it. Windows Desktop regression.
🔗 [Issue #86012](https://github.com/anthropics/claude-code/issues/86012)

### #82092 — Apps gateway serves incorrect `otlpEndpoint` with no headers; all Desktop telemetry rejected
**10 comments · 5 👍** · Claude Desktop receives an `otlpEndpoint` pointing to a bearer-gated OTLP ingest without accompanying `otlpHeaders`, so every telemetry flush fails with `missing_token`.
🔗 [Issue #82092](https://github.com/anthropics/claude-code/issues/82092)

### #86138 — Cross-session `send_message` to paused sessions never delivered
**7 comments · 1 👍** · After the Desktop app's bundled CLI updated to v2.1.227, `send_message` to paused (idle-timed-out) sessions returns "Message sent" but the target never processes it.
🔗 [Issue #86138](https://github.com/anthropics/claude-code/issues/86138)

### #86069 — Cross-session messages land in composer but are never submitted
**6 comments · 1 👍** · Messages appear in the target session's composer UI but never reach the runtime input queue — session never responds. Windows MSIX regression since 2.1.227.
🔗 [Issue #86069](https://github.com/anthropics/claude-code/issues/86069)

### #79596 — Cowork/Claude in Chrome extension navigated to unrelated external site
**6 comments · 0 👍** · The Cowork extension in Chrome navigated a real tab to `aisle.wedding` with no prompt requesting it. Model behavior issue flagged for investigation.
🔗 [Issue #79596](https://github.com/anthropics/claude-code/issues/79596)

### #86237 — Cross-session messages never reach the runtime input queue (regression 2.1.222 → 2.1.227)
**5 comments · 1 👍** · Messages render in the target session's UI but are held for an approval the UI never offers, then expire after ~5 minutes.
🔗 [Issue #86237](https://github.com/anthropics/claude-code/issues/86237)

---

## 4. Key PR Progress

### #86537 — Fix duplicated word in CHANGELOG.md
Documentation-only typo fix correcting "to to" in the `CLAUDE_BASH_NO_LOGIN` entry for version 1.0.124.
🔗 [PR #86537](https://github.com/anthropics/claude-code/pull/86537)

### #60280 — chore(ci): SHA-pin remaining `actions/checkout` and `actions/github-script`
Follow-up to #56784; SHA-pinned third-party action references across 6 workflows including `auto-close-duplicates`, `backfill-duplicate-comments`, `claude-dedupe-issues`, `claude-issue-triage`, and others. **Closed.**
🔗 [PR #60280](https://github.com/anthropics/claude-code/pull/60280)

> *Note: Only 2 PRs were updated in the last 24h. The community activity this period is focused almost entirely on issues rather than pull requests.*

---

## 5. Feature Request Trends

1. **Cross-session communication & coordination** — The dominant theme. Issue #24798 (66 comments, 21 👍) calls for direct inter-session workflow, and the flood of 10+ cross-session messaging bugs (#86012, #86138, #86069, #86237, #86298, #86386, #86059, #86385, #86212, #86088, #86398, #86029) all stem from the same underlying need. The new `@` mention and subagent forking in v2.1.232 are direct responses.

2. **Multi-session multi-agent orchestration** — Users are running 15–25 concurrent local sessions coordinating via `mcp__ccd_session_mgmt__send_message`. The tooling is being pushed beyond its intended scope without a polished integration layer.

3. **Token usage accuracy & auto-compaction reliability** — Issues #53065 and #81620 both flag that the `advisor()` tool corrupts reported token counts, triggering premature compaction. Accurate context tracking is a recurring ask.

4. **Windows Desktop packaging & update reliability** — A cluster of Windows-specific issues (#73107, #77421, #86555, #77379, #79846) point to a desire for more robust MSIX packaging, clean update flows, and proper process cleanup.

---

## 6. Developer Pain Points

- **Cross-session messaging is broken on Windows Desktop (regression 2.1.222 → 2.1.227):** Messages are silently dropped, never trigger turns, or hang indefinitely. This is the single largest pain point this period, with 12+ related issues, many still unresolved in v2.1.231.

- **Windows Desktop packaging & updates:** AppX/MSIX containers left behind by orphaned processes block relaunch ("Another program is currently using this file"). Stale AppContainers and failed quit-for-update flows require reboots to clear. GPU process crashes (exit 0x060C201E) on Cloudflare Turnstile pages also deadlock the main process.

- **Cyber safeguard false positives for CVP-approved orgs:** Approved organizations are still being blocked, with the Verification Portal showing stale "Under review" status. This is blocking enterprise adoption.

- **`advisor()` tool corrupting context tracking:** The forwarded-transcript prompt doubles reported token counts, causing auto-compaction to fire prematurely on extended-context models.

- **Typed input lost in TUI during active turns:** Mid-turn keyboard input (especially inside tmux) is silently dropped, leading to lost work in long-running agent sessions.

- **PreToolUse hook denial reason lost:** When a hook denies a tool call, the `decisionReason` is discarded at transcript-write time, making post-hoc debugging of hook behavior impossible.

- **Telemetry broken for Claude Desktop:** The Apps gateway serves an `otlpEndpoint` without required auth headers, causing all Desktop telemetry flushes to be rejected with `missing_token`.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-14

## 1. Today's Highlights

The Codex team shipped four alpha releases in the 0.148.0-alpha series and merged a batch of 18 PRs focused on Guardian V2 hardening, multi-provider support (Amazon Bedrock), MCP OAuth flexibility, and multi-agent context fidelity. On the issue front, resource leaks in MCP stdio servers and a macOS regression blocking Remote Control thread resumption are the most-discussed bugs.

## 2. Releases

Four Rust alpha releases landed in the past 24 hours:

| Version | Notes |
|---|---|
| [rust-v0.148.0-alpha.14](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.14) | Latest alpha in the 0.148 sweep |
| [rust-v0.148.0-alpha.13](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.13) | |
| [rust-v0.148.0-alpha.12](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.12) | |
| [rust-v0.148.0-alpha.11](https://github.com/openai/codex/releases/tag/rust-v0.148.0-alpha.11) | |

These alpha increments ride alongside merged PRs for Bedrock provider support, skill model annotations, bounded delegation, and compaction-aware message retention—suggesting 0.148.0 is consolidating a broad feature set.

## 3. Hot Issues

1. **#26984** — MCP stdio servers leak pipe fds, causing cumulative EMFILE errors on long sessions. *[4 👍, 21 comments]* — Affects multi-server users running Codex CLI 0.137.0+; high signal because it directly blocks prolonged agent work. [Link](https://github.com/openai/codex/issues/26984)

2. **#37403** — macOS regression: Desktop cannot resume Remote Control / CLI threads after the Aug 7 update (`already has an active writer`). *[11 👍, 18 comments]* — Breaks a core remote-development workflow; community urgency is reflected in the top upvote count this cycle. [Link](https://github.com/openai/codex/issues/37403)

3. **#31553** — VS Code extension stopped auto-including IDE context after an update. *[12 👍, 17 comments, CLOSED]* — Widely impactful because IDE Context is foundational; closed status suggests a fix landed. [Link](https://github.com/openai/codex/issues/31553)

4. **#34920** — IDE Context fails with RPC serialization error in extension 26.715.x on Windows. *[5 👍, 10 comments, CLOSED]* — Paired with #31553 as a Windows-specific counterpart; both point to a regression in the IDE context serialization path. [Link](https://github.com/openai/codex/issues/34920)

5. **#2062** — Request to monitor background services (long builds / server runs). *[10 👍, 9 comments]* — Feature request that has simmered since Aug 2025; reflects persistent demand for non-blocking agent workflows. [Link](https://github.com/openai/codex/issues/2062)

6. **#23454** — `$skill` explicit invocation ignores local explicit-only skills absent from the implicit list. *[7 👍, 8 comments]* — Subtle but disruptive for users relying on custom explicit-only skills. [Link](https://github.com/openai/codex/issues/23454)

7. **#33551** — Multi-Agent V2 sends OpenAI-specific `agent_message` items to external Responses providers (e.g., Ollama), breaking compatibility. *[6 👍, 8 comments]* — Blocks multi-agent use with non-OpenAI backends; a compatibility gap the new Bedrock PR may partially address. [Link](https://github.com/openai/codex/issues/33551)

8. **#38455** — macOS Desktop repeatedly spawns Computer Use workers, hitting V8 OOM (SIGABRT) ~98 s after launch. *[3 comments]* — Crash-on-start is critical-severity for Computer Use adopters on Apple Silicon. [Link](https://github.com/openai/codex/issues/38455)

9. **#38468** — Severe macOS performance regression: 100%+ CPU, 10+ GB RAM, frequent UI hangs on build 26.810.41047. *[2 comments]* — Directly impacts productivity; the reporter compares against a prior working build. [Link](https://github.com/openai/codex/issues/38468)

10. **#38466** — Long-running Desktop sessions become huge and hard to inspect after repeated compaction; thread read output is truncated. *[3 comments]* — Signals a compaction/growth management gap in the app server. [Link](https://github.com/openai/codex/issues/38466)

## 4. Key PR Progress

1. **[PR #38470](https://github.com/openai/codex/pull/38470)** — Add Amazon Bedrock Runtime provider. Introduces a built-in `amazon-bedrock-runtime` provider with endpoint-specific SigV4 auth, per-provider AWS profiles/regions, and preserved bearer-token auth. Expands multi-provider support beyond OpenAI.

2. **[PR #38475](https://github.com/openai/codex/pull/38475)** — Add bounded skill model delegation instructions. Resolves Luna-only skill requests on Sol/Terra providers by bounding and validating model IDs, skill names, and tool names before delegation.

3. **[PR #38467](https://github.com/openai/codex/pull/38467)** — Parse model annotations from skill frontmatter. Adds an optional `model` field to skill metadata, recognizing `model: luna` while gracefully ignoring unsupported values.

4. **[PR #38441](https://github.com/openai/codex/pull/38441)** — Give Guardian V2 full tool action context. Exposes the pre-hook `ToolPayload` to tool lifecycle contributors so risk assessment sees the full requested action, not just a tool name and call ID.

5. **[PR #38448](https://github.com/openai/codex/pull/38448)** — Support per-server MCP OAuth callback ports. Adds `oauth.callback_port` to MCP server config and accepts `oauth.callbackPort` from plugin declarations and skill dependencies, resolving port-collision issues in multi-server setups.

6. **[PR #38456](https://github.com/openai/codex/pull/38456)** — Add experimental thread queue APIs to app server. Provides `thread/queue/{add,list,update,delete,reorder,start}` for persistent queued submissions, dispatched in FIFO order after turn completion or failure.

7. **[PR #38463](https://github.com/openai/codex/pull/38463)** — Preserve thread subscriptions across revert reloads. Restarts the listener task from preserved state so a replacement listener can serve existing subscriptions when the requesting connection closes during `thread/revert`.

8. **[PR #38440](https://github.com/openai/codex/pull/38440)** — Add app-server support for reverting paginated threads. Introduces experimental `thread/revert`, replacing a loaded paginated thread's durable history with the prefix before a given `beforeTurnId` while preserving the thread ID.

9. **[PR #38445](https://github.com/openai/codex/pull/38445)** — Retain client developer messages across context compaction. Ensures annotated client-authored developer instructions survive compaction when `retain_client_developer_messages` is enabled.

10. **[PR #38446](https://github.com/openai/codex/pull/38446)** — Refresh current-time reminders for full-history subagents. Excludes inherited reminders when copying parent history into a full-history subagent, preventing reminder accumulation while preserving the child's newly generated reminder.

## 5. Feature Request Trends

- **Multi-provider / non-OpenAI backends**: The Bedrock provider PR (#38470), the Ollama incompatibility bug (#33551), and the per-server MCP OAuth port support (#38448) all point to growing demand for running Codex against diverse model providers.
- **Non-blocking background work**: Issue #2062 (background service monitoring) and the thread-queue APIs (#38456) reflect repeated requests for agent workflows that don't tie up the user session.
- **Context fidelity across compaction and subagents**: PRs #38445, #38446, #38440 and issues #38466, #33551 show users care deeply about preserving instructions, reminders, and history when context is compacted or delegated to subagents.
- **Remote / mobile continuity**: Issue #37403 (macOS Remote Control regression) and #33396 (idle projectless task disappearing) highlight a desire for seamless handoff between mobile, remote, and desktop experiences.
- **Dynamic chat metadata**: Issue #24060 (auto-updating chat titles) is a lower-signal but consistent polish request.

## 6. Developer Pain Points

- **Resource leaks on long sessions**: MCP pipe-fd leaks (#26984) and V8 OOM crashes from runaway Computer Use workers (#38455) both punish sustained usage, which is exactly when agents are most valuable.
- **IDE Context regressions on Windows**: A cluster of closed but closely related issues (#31553, #34920, #35419, #34696, #35333) all trace back to IDE Context silently disabling or failing serialization after extension updates—suggesting a fragile update path for the Windows VS Code integration.
- **macOS Desktop performance instability**: Issues #38468 (CPU/RAM regression) and #38455 (OOM crashes) indicate the latest macOS build cycle introduced performance regressions that need stabilization before broader adoption.
- **Remote Control thread resumption blocked**: The `already has an active writer` regression (#37403) breaks a key workflow for off-hours mobile-to-desktop handoff, a scenario many power users depend on.
- **Multi-Agent V2 compatibility gaps**: Sending OpenAI-specific `agent_message` items to external providers (#33551) and model-resolution mismatches between bundled vs. standalone CLI (#38107) reveal that the multi-agent surface is still tight-coupled to OpenAI infrastructure.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-14

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly.20260814.gc0d192452 shipped with a critical capacity-exhaustion retry fix and e2e test stabilization. A security-critical supply-chain RCE patch in eval workflows (PR #28740) and a CVE-2026-28292 fix for simple-git landed this week, while the team continues to investigate subagent reliability gaps around Auto Memory and browser agent resilience.

## 2. Releases

**v0.56.0-nightly.20260814.gc0d192452** — [#28806](https://github.com/google-gemini/gemini-cli/pull/28806)
- **#28790** — Context-aware silent retries and availability TTL for capacity errors, addressing the critical regression from #28761. Unattended CLI runs now back off and retry automatically with up to 2 silent retries.
- **#28793** — Stabilized the flaky `file-system-interactive` e2e test on slow virtualized runners via prompt synchronization.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Subagents silently claim success when they hit the turn limit without doing work, corrupting agent orchestration. Maintainer-only, P1. | 12 comments, 2 👍 |
| [#23297](https://github.com/google-gemini/gemini-cli/issues/23297) | Pressing Enter does nothing | Core UX regression — users are completely stuck with no visible path forward; 10 upvotes signal broad impact. | 11 comments, 10 👍 |
| [#18811](https://github.com/google-gemini/gemini-cli/issues/18811) | `Request contains an invalid argument` | Persistent API error tied to CLI auto-update; 16 comments, closed but still referenced. | 16 comments, 5 👍 |
| [#19883](https://github.com/google-gemini/gemini-cli/issues/19883) | `No capacity available for gemini-3-flash-preview` | Model capacity issue blocks a specific preview model while others work; 14 comments, closed. | 14 comments, 8 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck "Waiting input" after completion | Agent shows active but command is done — a recurring reliability bug with P1 priority. | 4 comments, 3 👍 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retrying low-signal sessions indefinitely | Background extractor can loop on unprocessed sessions, wasting tokens and degrading memory quality. Maintainer-only. | 5 comments |
| [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) | Subagents running without permission since v0.33.0 | Regression where agents activate despite being explicitly disabled in config — trust and control issue. | 3 comments |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Anecdotal but widespread: custom skills and sub-agents are ignored unless explicitly prompted, undermining the agent architecture. | 6 comments |
| [#27911](https://github.com/google-gemini/gemini-cli/issues/27911) | Auto-memory storing project alias as project ID → 403 on GCP | Identity mismatch in Cloud Assist causes auth failures; affects enterprise users. | 2 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | Secrets may reach model context before redaction; critical security concern for Auto Memory. Maintainer-only. | 4 comments |

## 4. Key PR Progress

| PR | Title | Status | Summary |
|----|-------|--------|---------|
| [#28740](https://github.com/google-gemini/gemini-cli/pull/28740) | Prevent supply chain RCE in eval-pr workflows | OPEN | Fixes critical issue [#28336](https://github.com/google-gemini/gemini-cli/issues/28336): splits eval workflow into untrusted `pull_request` build + trusted `workflow_run` execution. |
| [#28778](https://github.com/google-gemini/gemini-cli/pull/28778) | Upgrade simple-git to 3.32.3 (CVE-2026-28292) | OPEN | Addresses CRITICAL CVE detected by trivy in the git helper dependency. |
| [#28790](https://github.com/google-gemini/gemini-cli/pull/28790) | Context-aware silent retries for capacity errors | CLOSED | Adds up to 2 silent retries with backoff for capacity-exhaustion errors in non-interactive runs. Closes [#28761](https://github.com/google-gemini/gemini-cli/issues/28761). |
| [#28803](https://github.com/google-gemini/gemini-cli/pull/28803) | Add Claude Sonnet 4.5 and Opus 4.8 model definitions | CLOSED | Adds model constants, alias resolution, and policy-chain fallbacks for two new Anthropic models. |
| [#28801](https://github.com/google-gemini/gemini-cli/pull/28801) | Rollback entire multi-turn request on cancellation | CLOSED | Fixes incomplete chat history state when a multi-turn prompt with tool calls is aborted mid-stream. |
| [#28679](https://github.com/google-gemini/gemini-cli/pull/28679) | Improve Vertex AI 401 error message | OPEN | Better DX when users mistakenly configure a standard Gemini API key as Vertex AI auth. |
| [#28699](https://github.com/google-gemini/gemini-cli/pull/28699) | Enforce auth and stop checkpoint path traversal in A2A server | OPEN | A2A server REST routes bypassed `UserBuilder` entirely — now enforces authentication and blocks path traversal. |
| [#28597](https://github.com/google-gemini/gemini-cli/pull/28597) | Load env vars before resolving settings placeholders | CLOSED | Fixes load-order race where `.env` values were unavailable during settings expansion at startup. |
| [#28603](https://github.com/google-gemini/gemini-cli/pull/28603) | Upgrade sandbox Dockerfile to Node 22 | CLOSED | Node 20 reached EOL 2026-04-30; sandbox runtime now uses a supported Node version. |
| [#28596](https://github.com/google-gemini/gemini-cli/pull/28596) | Add `--list-all-sessions` CLI flag | CLOSED | New flag lists sessions across all registered workspaces, grouped by path — addresses a frequent usability request. |

## 5. Feature Request Trends

- **Subagent reliability and governance** — Multiple open issues (#22323, #21968, #22093, #22672) converge on the need for subagents to respect configuration, use skills proactively, and avoid destructive actions without consent.
- **Auto Memory hardening** — Issues #26522, #26523, #26525 point to a clear demand for robust memory extraction: better signal detection, deterministic redaction, and invalid-patch quarantine.
- **Agent tool-scope management** — Issue #24246 (400 error with >128 tools) and #23571 (tmp scripts everywhere) highlight the need for smarter tool selection and workspace hygiene.
- **Cross-platform clipboard & terminal UX** — PRs #27588 (WSL2 clipboard paste) and #25378 (Windows ripgrep) show sustained interest in Windows/WSL parity.
- **Session and identity management** — `--list-all-sessions` (#28596) and the project-alias bug (#27911) reflect demand for better session discoverability and GCP identity handling.

## 6. Developer Pain Points

- **Capacity errors and silent retries** — The capacity-exhaustion regression (#28761 / #19883) was a high-friction pain point for unattended and CI runs; the retry fix (#28790) directly addresses it.
- **Agent state inconsistency on abort** — Canceled multi-turn requests leave dangling tool-response turns in chat history (#28801), causing confusing follow-up behavior.
- **Settings load-order race** — Environment variables from `.env` were not available when settings placeholders resolved, breaking configuration (#28597).
- **Browser agent fragility** — Wayland failures (#21983), locked-profile handling (#22232), and ignored `settings.json` overrides (#22267) make the browser subagent the most unreliable agent path.
- **Auto Memory loop and security gaps** — Low-signal sessions are retried indefinitely (#26522), invalid patches are silently dropped (#26523), and redaction happens too late in the pipeline (#26525).
- **Security surface in workflows and A2A server** — Supply-chain RCE via untrusted fork code in `pull_request_target` (#28740) and unauthenticated A2A REST routes with path traversal (#28699) are critical reliability and security concerns.
- **Docker base image EOL** — Node 20 reached EOL, forcing an urgent sandbox upgrade (#28603) and a broader runtime bump to Node 24 for the CLI image (#28602).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-14

## 1. Today's Highlights

v1.0.80-0/80-1 shipped with two notable additions: `--enable-mcp-server` lets users re-enable MCP servers disabled in settings for a single run, and shared-session visibility improved — the `--ahp` mode now surfaces a `2 clients` (or more) indicator on joined sessions. Community attention is dominated by a cluster of reasoning-effort compatibility bugs around `claude-haiku-4.5` and `gpt-5.4-mini`, plus a wave of MCP OAuth regressions filed in the last 48 hours.

## 2. Releases

**v1.0.80-1** — Patch over v1.0.80-0 (fixes and changes, no details disclosed in release notes).  
[github.com/github/copilot-cli/releases](https://github.com/github/copilot-cli)

**v1.0.80-0** — Two additions:
- `--enable-mcp-server` flag to re-enable MCP servers disabled in settings for the current run only.
- Shared-session indicator in `--ahp` mode: rows for joined sessions now lead with `2 clients` (or more) when another CLI is attached, visible in both the Sessions tab and inline output.

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| **#2904** | Custom Agent YAML frontmatter should support reasoning effort | Per-agent `model` pinning exists; `--effort` is only global. A frontmatter `effort` field would bring parity for custom agents. | 🔥 20 👍 · 6 comments · open since Apr 2026 |
| **#4345** | `medium` reasoning effort unsupported for `claude-haiku-4.5` | Sub-agent routing silently applies `medium` effort to Haiku, which rejects it — a hard execution failure for any org using that model. | 4 👍 · closed |
| **#4473** | Same Haiku + `medium` effort failure (regression) | Identical root cause filed again after v1.0.79, indicating the bug survived into the latest release. | 0 👍 · open |
| **#2133** | `model` frontmatter rejects array syntax | VS Code Copilot Chat supports `["model-a","model-b"]` in `.agent.md`; the CLI refuses to load such agents with a parse error. | 7 👍 · open since Mar 2026 |
| **#3954** | `explore` tool hardcodes `gpt-5.4-mini` | The built-in `explore` sub-agent ignores custom model / DeepSeek endpoint config and fires `gpt-5.4-mini` directly to the API — breaks self-hosted and cost-sensitive setups. | 3 👍 |
| **#4480** | Atlassian MCP OAuth broken since v1.0.79 | RFC 8414 issuer-mismatch error on OAuth discovery — a clean regression from v1.0.71 that blocks Atlassian MCP users on upgrade. | 0 👍 · open |
| **#4464** | Silent refresh fails with AADSTS70011 (scope bug) | Remote HTTP MCP servers using Microsoft Entra OAuth force interactive sign-in roughly every 60–75 min because the refresh request mixes `.default` and resource-specific scopes. | 0 👍 |
| **#4463** | MCP OAuth intermittently fails on Windows (sock error 10013) | Socket-access-denied errors before the browser flow opens — blocks Windows users connecting to remote MCP servers. | 0 👍 |
| **#4467** | Long-running sessions exhaust event store, appear cancelled | Sessions with many sub-agents can run out of remote event storage; status becomes unreliable while the CLI process stays alive. | 0 👍 |
| **#4468** | `--server --stdio` never releases extension-host processes | Each session spawns four child processes that accumulate until the server exits — a memory leak on Windows desktop app hosts. | 0 👍 |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| **#4476** | Document proposed custom-agent `effort` frontmatter (Option A) | Closed | Authors Option A (dedicated `effort` field parallel to `model`) and adds a "Custom Agents" reference section to README.md covering existing frontmatter (`name`, `description`, `model`) and the new proposed field. Closes against #2904. |

*No other PRs landed in the last 24 h; the rest of the activity is issue-driven.*

## 5. Feature Request Trends

- **Per-agent reasoning effort**: The dominant request (#2904, 20 👍). Users want `.agent.md` to control `--effort` the way it already controls `model`, enabling different agents to run at explore/medium/high without global flags.
- **Model array support in frontmatter**: #2133 (7 👍) — align CLI custom-agent parsing with VS Code Copilot Chat so `model: [a, b]` is accepted.
- **Session introspection**: #4470 requests a `copilot sessions --json` (or `claude agents --json`-equivalent) to list running sessions with id, cwd, and status for external dashboards.
- **Auto-update for extra marketplaces**: #4465 — `autoUpdate: true` on an `extraKnownMarketplaces` entry should trigger plugin updates at session start; currently it does not.
- **Archived-chat restore UI**: #4474 — sessions silently archived after a 60 s resume timeout with no way to recover them; users want a restore path.

## 6. Developer Pain Points

1. **MCP OAuth regressions are the top frustration**. Three distinct OAuth bugs landed in one day (#4480 Atlassian RFC mismatch, #4464 Entra scope mixing, #4463 Windows socket error), all affecting remote MCP servers. The common thread: upgrade pain and lost trust in the MCP init path.
2. **Reasoning-effort / model compatibility gaps**. Haiku rejecting `medium` effort (#4345, #4473) and the `explore` tool hardcoding `gpt-5.4-mini` (#3954) both break agent pipelines silently. Developers report repeated sub-agent failures with unhelpful errors.
3. **Session lifecycle leaks**. Orphaned `permission.requested` events replay on every resume (#4469), and extension-host processes accumulate under `--server --stdio` (#4468). Long sessions become unusable without manual cleanup.
4. **Permissions config not taking effect**. `allowed_directories` in `~/.copilot/permissions-config.json` fails to suppress the shell command prompt (#4482), forcing users to rely on the interactive `/add-dir` workaround per session.
5. **Ambiguous startup messaging**. "No `copilot-instructions.md` found" (#4475) doesn't clarify repo-scoped vs. user-scoped, leading to confusion about why custom instructions aren't loading.

---

*Digest generated from github.com/github/copilot-cli data current to 2026-08-14.*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-14

---

## 1. Today's Highlights

The Kimi Code CLI repo saw three newly updated issues today, headlined by a persistent streaming deadlock in ACP mode (#2598) where responses hang silently after content delivery, and a runaway generation bug producing 88k tokens of gibberish in a single step (#2597). The most-upvoted feature request for a persistent Memory System (#1283, 38 comments) continues to draw community interest despite remaining open since February. No new releases or pull requests were reported in the last 24 hours.

---

## 2. Releases

No releases in the last 24 hours.

---

## 3. Hot Issues

### #2598 — ACP/print streaming response hangs silently
**Author:** ai-agent-workbench | Updated: 2026-08-13 | Comments: 1
[View on GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2598)

A critical ACP-mode bug where, after all content deltas arrive, the `[DONE]`/finish frame never arrives — the terminal sits idle with no timeout and no error. Sending a new message silently replaces the hung turn, and the abandoned response is **never written to `wire.jsonl`**, causing data loss. Notably, v0.31.1 only covered the Esc scenario; this broader idle-timeout gap remains unfixed. This matters for any ACP user relying on deterministic streaming and session replay.

### #2597 — Runaway garbled generation: 88k tokens of gibberish
**Author:** kdp123 | Updated: 2026-08-13 | Comments: 1
[View on GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2597)

During a normal interactive session, a single LLM step ran for **3,214 seconds (~53 min)** and emitted **88,114 output tokens** of incoherent, repetitive gibberish. This is a severe correctness and resource-waste issue — one bad turn can consume minutes of wall time and tokens with no recoverable output. The lack of a per-step guard or max-token ceiling per step makes this especially dangerous in long-running sessions.

### #1283 — Memory System: Persistent context across sessions
**Author:** CatKang | Updated: 2026-08-13 | Comments: 38 | 👍: 0
[View on GitHub](https://github.com/MoonshotAI/kimi-cli/issues/1283)

The most persistent feature request: a comprehensive Memory System supporting both automatic (AI-managed notes) and manual (user-defined via config) memory, preserving project patterns and preferences across CLI sessions. 38 comments with no resolution since February signal strong community demand. This would elevate Kimi Code CLI from a per-session tool to a persistent development companion.

---

## 4. Key PR Progress

No pull requests updated in the last 24 hours.

---

## 5. Feature Request Trends

The dominant trend is **session persistence and reliability**. #1283 calls for a Memory System that spans sessions — a pattern that also touches streaming reliability (#2598) and runaway-generation safeguards (#2597). Community feedback suggests developers want:

- **Persistence**: memory, preferences, and project context that survive restarts.
- **Streaming robustness**: guaranteed idle timeouts, proper frame delivery, and wire logging of all turns — not just successful ones.
- **Generation safety**: per-step token limits and anomaly detection to prevent runaway outputs.

---

## 6. Developer Pain Points

1. **Silent streaming deadlocks in ACP mode** — Content arrives but the session never closes, with no configurable idle timeout. This is a high-friction bug because it appears as a frozen terminal with no actionable error.

2. **Lost responses from hung turns** — When a new message replaces a stuck stream, the abandoned response is never persisted to `wire.jsonl`, making debugging and session replay unreliable.

3. **No per-step generation guardrails** — A single bad step can run for 53 minutes and emit 88k tokens of gibberish with no automatic intervention, wasting tokens and confusing the user.

4. **No cross-session memory** — The absence of a memory system (#1283) means users must re-establish context manually on every session, reducing the tool's effectiveness for long-running projects.

---

*Digest generated from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) data as of 2026-08-14.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-14

## 1. Today's Highlights
The OpenCode community is closely tracking a persistent **write‑tool hang** (#11112) that has garnered 78 comments and 46 upvotes, alongside a **regression in v1.18.5+** where providers, models, and MCP servers frequently fail to load on startup (#40516). On the security front, two medium‑severity issues were reported: one concerning an unsafe `curl|bash` pattern in the upgrade script (#42434) and another highlighting that **context pruning can silently drop instruction‑bearing content** (#42437), raising integrity concerns.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
*   **#11112 – Always stuck at “Preparing write…”**  
    Author: yinzhou-jc | 78 comments | 46 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/11112)  
    A high‑visibility bug where the agent repeatedly aborts while preparing to write a file. The long thread indicates widespread impact and frustration with the write tool’s reliability.

*   **#37012 – [FEATURE] Keep legacy layout option**  
    Author: darkine24th | 37 comments | 41 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/37012)  
    Users advocate preserving the older UI layout, citing easier access to controls and workspace support. The strong upvote count reflects a significant portion of the community that prefers the previous design.

*   **#40516 – [Bug] Desktop app: provider/model/MCP fail to load on startup**  
    Author: ssc-esiemiat | 4 comments | 1 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/40516)  
    A regression introduced in v1.18.5 that breaks startup for many users. The issue notes that downgrading to v1.18.4 resolves the problem, highlighting a critical quality gap in recent releases.

*   **#26091 – LLM response headers are discarded**  
    Author: jtbnz | 4 comments | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/26091)  
    Response headers (e.g., `x-litellm-model-api-base`) from LiteLLM proxies are stripped, preventing plugins from accessing routing metadata. This blocks advanced proxy‑based model selection.

*   **#42434 – [SECURITY] `opencode upgrade` fetches remote script without integrity verification**  
    Author: shafqatevo | 3 comments | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/42434)  
    The upgrade command uses a `curl | bash` pattern, exposing users to supply‑chain risks. Severity is rated medium due to full user privileges once the action is confirmed.

*   **#42421 – [2.0] TODO tools missing in V2**  
    Author: kiliantgs | 3 comments | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/42421)  
    The `todowrite`/`todoread` tools available in V1 are no longer exposed in the V2 runtime, breaking workflow continuity for users who rely on the native todo list.

*   **#42437 – [SECURITY] Context pruning silently drops instruction‑bearing content**  
    Author: shafqatevo | 2 comments | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/42437)  
    The compaction mechanism may omit critical constraints from the context window, potentially allowing instruction bypass. Rated medium‑high severity due to integrity implications.

*   **#42435 – [SECURITY] `webfetch` can fetch loopback/private addresses (SSRF)**  
    Author: shafqatevo | 2 comments | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/42435)  
    The webfetch tool lacks proper URL filtering, enabling SSRF attacks against local services. A previously submitted guard PR (#40851) was closed unmerged.

*   **#35402 – Zen: byte‑identical requests intermittently reroute to cold‑cache provider**  
    Author: Marvinthebored | 2 comments | 8 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/35402)  
    Multi‑sourced models like `glm-5.2` suffer from cold‑cache penalties when consecutive identical requests land on different upstream providers. Users request sticky routing to improve performance and cost.

*   **#42451 – Legacy plugin loader pushes non‑Hooks return values, corrupting startup**  
    Author: clayleopardlabs | 1 comment | 0 👍  
    [GitHub](https://github.com/anomalyco/opencode/issues/42451)  
    The V1 plugin loader calls every exported function and pushes the return value into the hooks array without validation. A plugin that exports helper functions can crash the entire application.

## 4. Key PR Progress
*   **#42474 – fix(tui): refresh terminal size before resize**  
    Fixes a bug where Bun‑based PTY hosts leave `process.stdout` dimensions stale after a `SIGWINCH`. The fix ensures the TUI reads the correct terminal size before applying the resize. [GitHub](https://github.com/anomalyco/opencode/pull/42474)

*   **#42475 – feat(app): add Hebrew locale**  
    Introduces complete Hebrew translations for the app, shared UI, and desktop renderer. Registers `he-IL` for locale detection and enables the existing RTL layout path. Includes CLDR plural forms and locale coverage tests. [GitHub](https://github.com/anomalyco/opencode/pull/42475)

*   **#42456 – fix(tui): isolate tab scroll state**  
    Addresses a race condition where saving the scroll position of one session tab could inadvertently overwrite the position of another tab when the route advanced. Each tab now maintains its own independent scroll offset. [GitHub](https://github.com/anomalyco/opencode/pull/42456)

*   **#42471 – fix(tui): scope unread updates to focused terminal**  
    Prevents a background TUI from marking a session tab as unread (or clearing an unread marker) simply because it has a different tab selected. Unread state mutations are now confined to the foreground terminal. [GitHub](https://github.com/anomalyco/opencode/pull/42471)

*   **#42468 – perf(core): load MCP client lazily**  
    Defers loading the MCP SDK until an enabled MCP server is actually connected or OAuth authorization is triggered. This removes the SDK from startup evaluation when no MCP servers are configured, improving cold‑start performance. [GitHub](https://github.com/anomalyco/opencode/pull/42468)

*   **#42466 – fix(tui): load local TUI plugins via SEA‑safe runtime import**  
    Resolves a crash in Node SEA builds where local TUI plugins failed to import with `ERR_UNKNOWN_BUILTIN_MODULE`. The fix adapts the plugin loader to use an import path that works within the SEA sandbox. [GitHub](https://github.com/anomalyco/opencode/pull/42466)

*   **#42222 – refactor(util): replace xdg‑basedir**  
    Replaces the `xdg-basedir` dependency with a behavior‑compatible local implementation, removing one direct runtime dependency and saving ~6.8 KB unpacked. Preserves XDG environment overrides and home‑directory defaults. [GitHub](https://github.com/anomalyco/opencode/pull/42222)

*   **#40427 – some experimental perf improvements**  
    A performance‑focused series that isolates v2‑only changes, removing legacy‑layout, compatibility‑client, and other dev‑era modifications. Includes optimizations for session‑route loading and other hot paths. [GitHub](https://github.com/anomalyco/opencode/pull/40427)

*   **#42470 – refactor(cli): load semver lazily for update checks**  
    Defers the `semver` import until an update check has actually fetched a candidate version. Local installs, disabled checks, and network failures no longer pay the import cost during startup. [GitHub](https://github.com/anomalyco/opencode/pull/42470)

*   **#42469 – refactor(core): defer webfetch HTML parsing**  
    Postpones loading `htmlparser2` and its `entities` tables until an HTML response truly needs text or Markdown conversion. Raw HTML and non‑HTML responses avoid the conversion overhead. [GitHub](https://github.com/anomalyco/opencode/pull/42469)

## 5. Feature Request Trends
*   **UI Layout & Navigation** – A vocal segment of users continues to request retention of the legacy layout (#37012), citing ease of access and workspace support.
*   **Localization** – Expansion of supported locales is ongoing, with a new Hebrew translation PR (#42475) addressing a previously missing language.
*   **Provider Routing & Caching** – Users of multi‑sourced models (e.g., Zen) are asking for sticky provider routing to avoid cold‑cache penalties and ensure consistent performance (#35402).
*   **Tool Exposure** – The disappearance of V1 tools like `todowrite`/`todoread` in V2 (#42421) highlights a demand for parity in core agent capabilities during the transition.

## 6. Developer Pain Points
*   **Startup & Load Failures** – Regressions in v1.18.5+ cause providers, models, and MCP servers to fail loading on startup (#40516), forcing downgrades.
*   **Plugin Loader Instability** – The legacy plugin loader (#42451) can crash the application if a plugin exports non‑hook functions, while SEA builds fail to load local TUI plugins (#42

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-14

## 1. Today's Highlights

The most-discussed issue this cycle is [#6879](https://github.com/earendil-works/pi/issues/6879), where auto-compaction fails to trigger after context exceeds the window limit, drawing 19 comments and 17 upvotes. A cluster of terminal-hygiene fixes landed in [#8082](https://github.com/earendil-works/pi/pull/8082), resolving SIGINT state corruption and session-resume history flooding. Performance work continues with [#8066](https://github.com/earendil-works/pi/pull/8066) caching visual lines to address the slow prompt-editor reported in [#8029](https://github.com/earendil-works/pi/issues/8029).

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Status | Engagement |
|---|-------|--------|------------|
| [#6879](https://github.com/earendil-works/pi/issues/6879) | Auto-compaction never triggers after context grows past 100% until provider overflow | OPEN | 19 comments · 17 👍 |
| [#8029](https://github.com/earendil-works/pi/issues/8029) | Very slow performance on moving in prompt editor | OPEN, in-progress | 7 comments |
| [#7791](https://github.com/earendil-works/pi/issues/7791) | Global Undici dispatcher inherits 16 KiB maxHeaderSize, causing UND_ERR_HEADERS_OVERFLOW | CLOSED | 6 comments |
| [#2366](https://github.com/earendil-works/pi/issues/2366) | Rate limiting doesn't work | CLOSED | 5 comments |
| [#7779](https://github.com/earendil-works/pi/issues/7779) | Allow trusted Unix users to share PI_CODING_AGENT_DIR | OPEN | 5 comments |
| [#7829](https://github.com/earendil-works/pi/issues/7829) | Invalid settings.json silently ignored; misleading 'bash not found' error on Windows | OPEN, in-progress | 5 comments |
| [#4254](https://github.com/earendil-works/pi/issues/4254) | Speed up extension loading: shared jiti instance with moduleCache | CLOSED | 4 comments |
| [#7960](https://github.com/earendil-works/pi/issues/7960) | `/resume` progress total counts files, completed list counts parsed sessions | CLOSED | 4 comments |
| [#7607](https://github.com/earendil-works/pi/issues/7607) | pi-agent-core: per-tool opt-out of argument validation for host-validated tools | OPEN | 3 comments |
| [#5065](https://github.com/earendil-works/pi/issues/5065) | `/exit` command leaves terminal in broken state (kitty keyboard protocol not reset) | CLOSED | 3 comments |

**Why they matter:**
- **#6879** is a critical correctness bug — compaction is the primary mechanism for long-session viability, and its silence past 100% context can cause API-level failures.
- **#8029** directly impacts UX for power users working with large prompt buffers; a PR (#8066) is already addressing it.
- **#7791** and **#2366** are closed but highlight ongoing provider-compatibility and rate-limit reliability concerns.
- **#7779** touches multi-user/shared-environment deployments, a growing use case.
- **#7829** exposes a dangerous silent-failure mode on Windows where invalid JSON is swallowed and misdiagnosed.
- **#4254** closed via refactor — extension load time remains a top perf priority.
- **#7607** proposes a useful architecture pattern for hosts that want strict provider schemas but lenient local validation.
- **#5065** and the related **#8080** (SIGINT terminal corruption) form a recurring terminal-state reliability thread.

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#8082](https://github.com/earendil-works/pi/pull/8082) | fix(tui): render only visible viewport; restore terminal on SIGINT | CLOSED | Fixes history-flood on resume and raw-mode left behind by `kill -INT`. |
| [#8086](https://github.com/earendil-works/pi/pull/8086) | fix(ai): fall back to legacy Gemini tool schema | CLOSED | Workaround for generativelanguage endpoints rejecting unknown JSON Schema fields. |
| [#8085](https://github.com/earendil-works/pi/pull/8085) | feat(tui): cancel active mouse selection with Escape | OPEN | Standard text-editor behavior — press Escape mid-drag to clear selection without copying. |
| [#8084](https://github.com/earendil-works/pi/pull/8084) | fix(coding-agent): don't swallow prompt after boolean extension flags | CLOSED | `--plan "prompt"` now correctly passes the prompt through instead of discarding it. |
| [#8066](https://github.com/earendil-works/pi/pull/8066) | fix(tui): add visual lines caching | OPEN | Caches visual-line computation to fix the slow cursor movement reported in #8029. |
| [#8070](https://github.com/earendil-works/pi/pull/8070) | fix(coding-agent): validate extension flag defaults | OPEN | Discriminated union for `registerFlag()` prevents type/default mismatches at runtime. |
| [#7984](https://github.com/earendil-works/pi/pull/7984) | fix(coding-agent): update grok-mermaid to 0.2.3 | OPEN | Improves Mermaid rendering; classes still ignored. |
| [#6216](https://github.com/earendil-works/pi/pull/6216) | feat: Amazon Bedrock Mantle OpenAI Responses provider | OPEN | New provider wrapping Bedrock's OpenAI-compatible API. |
| [#8067](https://github.com/earendil-works/pi/pull/8067) | Use APP_NAME in user-facing messages | CLOSED | Enables clean rebranding without hardcoded "pi" strings. |
| [#8088](https://github.com/earendil-works/pi/issues/8088) | Add AbortSignal support to PackageManager extension resolution | CLOSED | Propagates cancellation through npm/Git install commands to fix a Windows cancellation gap. |

## 5. Feature Request Trends

- **Provider expansion:** New provider integrations remain a steady theme — Amazon Bedrock Mantle (#6216), Grok 4.6 model support (#8046), and Anthropic refusal-server-side fallback (#8017) all point to an actively broadening model/provider surface.
- **i18n / localization:** [#8077](https://github.com/earendil-works/pi/issues/8077) requests first-class locale support for CLI and TUI, signaling demand beyond English-only deployments.
- **Mermaid & LaTeX in HTML exports:** [#8041](https://github.com/earendil-works/pi/issues/8041) asks for parity between TUI rendering and HTML export, a recurring quality-of-life ask.
- **Tool-hook extensibility:** [#7607](https://github.com/earendil-works/pi/issues/7607) and [#7092](https://github.com/earendil-works/pi/issues/7092) both explore finer-grained authority and admission controls for tool execution, suggesting the extension ecosystem is pushing for more nuanced permission models.
- **Performance budgets:** [#7739](https://github.com/earendil-works/pi/issues/7739) calls for a measured startup-time budget targeting jcode-comparable latency, indicating the community is tracking Pi against competing tools.

## 6. Developer Pain Points

1. **Terminal state corruption on exit/interrupt:** A clear pattern across [#5065](https://github.com/earendil-works/pi/issues/5065), [#8080](https://github.com/earendil-works/pi/issues/8080), and the fix in [#8082](https://github.com/earendil-works/pi/pull/8082) — `SIGINT`, `/exit`, and raw-mode cleanup are fragile. This is the most recurring frustration.
2. **Silent configuration failures:** Invalid `settings.json` ( [#7829](https://github.com/earendil-works/pi/issues/7829)) and unknown slash commands ( [#8081](https://github.com/earendil-works/pi/issues/8081)) are both swallowed or misrouted, making debugging frustrating.
3. **Extension loading performance:** Despite the closed refactor in [#4254](https://github.com/earendil-works/pi/issues/4254), startup-time budgeting remains an open concern [#7739](https://github.com/earendil-works/pi/issues/7739).
4. **Context management reliability:** The compaction bug in [#6879](https://github.com/earendil-works/pi/issues/6879) and mid-stream Codex restarts in [#8031](https://github.com/earendil-works/pi/issues/8031) both point to fragility in long-running agentic sessions.
5. **Clipboard / copy-path compatibility:** [#7761](https://github.com/earendil-works/pi/issues/7761) reports TUI copy failures on VTE terminals (GNOME Terminal), a niche but impactful compatibility gap.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-14

## 1. Today's Highlights

Qwen Code v0.21.11 ships with **Agent Plugins v1** and native multi-agent `/coordinate` workflows, marking a major step toward fleet-style automation. The community is actively debating RFC #8718 for independent-session coordination, while Windows users report a pasting regression and auth friction on Vertex AI continues to surface.

---

## 2. Releases

### v0.21.11 (stable) — [PR #8834](https://github.com/QwenLM/qwen-code/pull/8834), [PR #8804](https://github.com/QwenLM/qwen-code/pull/8804)
- **Agent Plugins v1**: extensible plugin system for adding new agent capabilities at runtime.
- **Native multi-agent workflows**: `/coordinate` command enables leader-follower sessions with read-only teammates.

### v0.21.12-preview.1 & v0.21.11-nightly.20260814
- **Web-shell**: standalone session target preservation ([#9038](https://github.com/QwenLM/qwen-code/pull/9038)) and workspace file upload support.

---

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#8718](https://github.com/QwenLM/qwen-code/issues/8718) | RFC: Native coordination for independent Qwen sessions | Defines the architecture for multi-session fleet control — the blueprint behind the new `/coordinate` feature. | 9 comments, P2 |
| [#8678](https://github.com/QwenLM/qwen-code/issues/8678) | fix(serve): Preserve session when large restore times out | Session data loss on timeout is a reliability blocker for long-running daemon sessions. PR #8691 merged a partial fix. | 8 comments, P1 |
| [#7118](https://github.com/QwenLM/qwen-code/issues/7118) | Windows standalone installer fails — `Get-FileHash` unresolved | Blocks Windows users from a clean install; 3 upvotes signal broad impact. | 7 comments, P2 · 👍 3 |
| [#9019](https://github.com/QwenLM/qwen-code/issues/9019) | Gemini 2.5 on Vertex AI: `thinkingLevel` always sent | Every Vertex AI Gemini 2.5 request fails at the API layer before any tool call. Critical for cloud users. | 5 comments, P2 |
| [#9025](https://github.com/QwenLM/qwen-code/issues/9025) | Keyless Vertex AI not inferred from environment | Headless/CI runs crash at startup because auth type is never auto-detected from ADC. | 5 comments, P2 |
| [#9061](https://github.com/QwenLM/qwen-code/issues/9061) | Ctrl+V paste unresponsive on Windows CLI — regression since 0.21.x | AUsable UX regression; downgrading to 0.21.0 restores functionality. | 4 comments, P1 |
| [#8586](https://github.com/QwenLM/qwen-code/issues/8586) | Track `activeWork` and background Agent recovery | Needed for daemon resilience — agents that outlive their foreground prompt should be recoverable. | 4 comments, P2 |
| [#8845](https://github.com/QwenLM/qwen-code/issues/8845) | Redesign Channel/session/workspace management in Web Shell | Web Shell UX overhaul targeting connection-state clarity and per-adapter workspace ownership. | 4 comments |
| [#9108](https://github.com/QwenLM/qwen-code/issues/9108) | Web Shell external links still fail to open; MCP OAuth broken | Desktop webview silently drops link clicks; blocks OAuth-based MCP flows. *(Closed)* | 3 comments |
| [#8888](https://github.com/QwenLM/qwen-code/issues/8888) | Autofix pushes cancel in-progress review-pr (self-reinforcing loop) | Bot-authored PRs get stuck in an autofix ↔ review cancellation loop. *(Closed)* | 3 comments |

---

## 4. Key PR Progress

| PR | Title | Summary |
|----|-------|---------|
| [#9107](https://github.com/QwenLM/qwen-code/pull/9107) | Trace main agent invocations | Adds telemetry traces for top-level agent calls, enabling observability into agent execution flow. |
| [#9040](https://github.com/QwenLM/qwen-code/pull/9040) | Prevent dialog clipping in short terminals | `/statusline` and `/skills` dialogs now adapt to constrained terminal heights via a compact layout below 16 rows. |
| [#8890](https://github.com/QwenLM/qwen-code/pull/8890) | Generalize Conversations runtime foundation | Refactors the Conversations runtime to be reusable across session types, laying groundwork for multi-agent and daemon integration. |
| [#8677](https://github.com/QwenLM/qwen-code/pull/8677) | OpenTUI renderer backend (react track) | Single PR delivering the new flicker-free TUI renderer with first-class mouse support; replaces the legacy renderer. |
| [#9106](https://github.com/QwenLM/qwen-code/pull/9106) | Consolidate Local Control into one daemon-owned implementation | Merges the duplicate LAN pairing flow (phone → daemon) into a single implementation, removing code duplication and security-model drift. |
| [#8899](https://github.com/QwenLM/qwen-code/pull/8899) | Hold autofix rounds while review-pr is in flight | *(Closed)* Stops the autofix scanner from dispatching fixes while an automatic review is still running on the same PR, breaking the cancellation loop from #8888. |
| [#9039](https://github.com/QwenLM/qwen-code/pull/9039) | Privacy-safe tool-result boundary diagnostics | Adds diagnostic boundaries that surface tool-result truncation info without leaking full content, aiding debugging while preserving privacy. |
| [#9086](https://github.com/QwenLM/qwen-code/pull/9086) | Harden `/review` pipeline against four live-run failures | Fixes four defects observed when running `qwen review run` against real open PRs; each fix is regression-tested. |
| [#8853](https://github.com/QwenLM/qwen-code/pull/8853) | Surface loop-detection turn errors in Web Shell | Tool-loop protection stops now surface as structured errors with localized guidance instead of silently breaking the turn. |
| [#8332](https://github.com/QwenLM/qwen-code/pull/8332) | Audio bridge for attachments | Transcribes audio attachments via a batch voice model when the primary model lacks native audio support, enabling `@` audio in headless and interactive modes. |

---

## 5. Feature Request Trends

1. **Multi-agent / fleet coordination** — The dominant theme: RFC #8718, fleet stages 1A/1B/2/3 (#8840, #8841, #8842, #8843), and background-agent recovery (#8586) all point to a community push toward scalable, multi-session agent workflows.
2. **Daemon resilience & session management** — Persistent `activeWork` tracking, safe session restores, and project-snapshot cleanup (#9110) reflect demand for production-grade daemon stability.
3. **Web Shell & Desktop UX** — Channel redesign (#8845), external-link fixes (#9108, #9111), and dialog clipping (#9040) show sustained focus on making the web-based interface more robust.
4. **Multimodal (Omni) experiment** — A parallel track (#8197) covers file recognition, policy-driven compression, and memory minimization/recall, signaling long-term investment in multi-modal tool chains.
5. **Observability & telemetry** — Tracing agent invocations (#9107) and OpenTelemetry log correlation (#9084) indicate a push for production-grade debugging tooling.

---

## 6. Developer Pain Points

- **Windows CLI regressions**: Ctrl+V paste stoppage (#9061), installer hash resolution failure (#7118), and a stray terminal window on Desktop launch (#9043) are creating friction for Windows users across multiple versions.
- **Vertex AI auth & model compatibility**: Gemini 2.5's unsupported `thinkingLevel` parameter (#9019) and keyless ADC auto-detection failure (#9025) make Vertex AI unreliable for headless and CI workflows.
- **Context-window budgeting**: Compression side-queries with fixed `maxOutputTokens` can exceed small context windows, causing `COMPRESSION_FAILED_EMPTY_SUMMARY` (#7960).
- **Autofix review loops**: The autofix ↔ review-pr cancellation loop (#8888) wastes CI resources and creates confusing PR states; now partially addressed by PR #8899 and divergence escalation in #9104.
- **Web Shell link & artifact reliability**: External links silently drop in the desktop webview (#9108), and `record_artifact` can return success for missing files (#9083), confusing both models and users.
- **Terminal UI clipping**: Short terminals clip `/statusline` and `/skills` dialogs (#9037 / #9040), a recurring UX grievance for developers on cramped terminals.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / CodeWhale Community Digest — 2026-08-14

## 1. Today's Highlights

The project has officially rebranded to **CodeWhale** (legacy `deepseek-tui` npm package is now deprecated), with v0.9.7 released. The community is focused on v0.9.8 preparation, including a new model-guardian tier for Auto-Review, first-class local DS4 (DwarfStar) setup, and ongoing fixes for shell completion leaks, test isolation, and i18n coverage.

---

## 2. Releases

**v0.9.7** — Current public release. Legacy `deepseek-tui` npm package is deprecated; users should migrate to `codewhale`. See: [Issue #998 discussion thread](https://github.com/Hmbown/CodeWhale/issues/998)

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#998](https://github.com/Hmbown/CodeWhale/issues/998) | 文案展示不全 | UI text truncation in TUI transcript; users want hover-to-reveal tooltips for truncated content | 11 comments, 1 👍 |
| [#1004](https://github.com/Hmbown/CodeWhale/issues/1004) | `/dryrun` — preview next completion without sending | Critical for V4 Pro users iterating on long system prompts with cached repos and multi-step thinking; avoids accidental API calls | 9 comments |
| [#5324](https://github.com/Hmbown/CodeWhale/issues/5324) | Simplify 32-field agent tool schema | Model-facing schema has 32 properties, zero required, 8 actions — causes repeated model errors; PR #5369 addresses with schema degradation | 7 comments |
| [#2369](https://github.com/Hmbown/CodeWhale/issues/2369) | Config paths fragmented across OS/Cygwin | Config and secret paths diverge on Windows vs Cygwin; legacy migration bug leaves stale paths silently | 7 comments |
| [#894](https://github.com/Hmbown/CodeWhale/issues/894) | Image chaos during execution | Visual corruption of rendered images in TUI output | 6 comments |
| [#1425](https://github.com/Hmbown/CodeWhale/issues/1425) | Session hangs after large text processing | 10-subagent batch processing times out on `agent_wait`; session appears frozen but is actually interrupted | 6 comments |
| [#1482](https://github.com/Hmbown/CodeWhale/issues/1482) | NVIDIA NIM 404 errors | API calls to NIM return 404; affects Windows users with `deepseek doctor` reporting v0.8.29 | 6 comments |
| [#1732](https://github.com/Hmbown/CodeWhale/issues/1732) | Slow report merge/save | Cache hit rate is extremely low when merging analysis reports to local documents | 6 comments |
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | TUI Crate Decomposition EPIC | Umbrella tracking issue for the entire crate decomposition effort — architectural reorganization | 5 comments |
| [#5374](https://github.com/Hmbown/CodeWhale/issues/5374) | Agent writing text corrupted on macOS | Text output is garbled/corrupted during agent writing; affects readability on macOS | 3 comments (opened today) |

---

## 4. Key PR Progress

| # | PR | Status | Description |
|---|-----|--------|-------------|
| [#5365](https://github.com/Hmbown/CodeWhale/pull/5365) | feat(provider): add first-class local DS4 setup | OPEN | Makes DwarfStar a first-class local DeepSeek route — `/setup provider ds4` opens a prefilled keyless loopback preset; reuses OpenAI-compatible transport |
| [#5353](https://github.com/Hmbown/CodeWhale/pull/5353) | feat(tui): model guardian tier for Auto-Review | OPEN | Two-layer Auto-Review for v0.9.8: deterministic floor stays non-bypassable; fallback escalates to a one-shot model guardian instead of silently blocking |
| [#5369](https://github.com/Hmbown/CodeWhale/pull/5369) | fix(tools): degrade Moonshot schemas | OPEN | Addresses #5324 — degrades conditional schemas instead of refusing, keeping schema slice net-positive |
| [#5368](https://github.com/Hmbown/CodeWhale/pull/5368) | fix(tui): confine unguarded tests | OPEN | Fixes 4 tests from #5359 that read machine state (`~/.codewhale`, display probe); isolates lock-holder trust hole |
| [#5339](https://github.com/Hmbown/CodeWhale/pull/5339) | fix(engine): suppress child-owned shell completions | OPEN | Filters child background shell completions from parent model stream; preserves unowned parent completions |
| [#5364](https://github.com/Hmbown/CodeWhale/pull/5364) | feat(tui): render markdown blockquotes with quote rail | MERGED | Renders `>` blockquotes with a visual quote rail instead of literal markers; supports nesting and inline formatting |
| [#5358](https://github.com/Hmbown/CodeWhale/pull/5358) | feat(engine): auto-review denial rationale + circuit breaker | MERGED | P0 slice of #5352; Auto-Review blocks now include denial rationale to prevent model re-phrase loops |
| [#5336](https://github.com/Hmbown/CodeWhale/pull/5336) | fix(mcp): omit nextCursor when no further pages | MERGED | Fixes MCP spec violation where `nextCursor: null` was returned; strict clients like Claude Code reject null |
| [#5333](https://github.com/Hmbown/CodeWhale/pull/5333) | feat(tui): pin host terminal as always-on-top mini window | MERGED | Harvest of community PR #5318; right-click or `/pin` shrinks terminal to 640x400 and pins on top |
| [#5334](https://github.com/Hmbown/CodeWhale/pull/5334) | docs(i18n): retire stale zh-Hant partial-pack declaration | MERGED | Retires false `is_partial_pack()` declarations for zh-Hant now that it reaches en parity |

---

## 5. Feature Request Trends

1. **Local-first model routing** — DS4/DwarfStar first-class support (#5363, #5365); users want streamlined local DeepSeek V4 Flash/Pro setup without manual provider translation
2. **Auto-Review hardening** — Model guardian tier (#5353), denial rationale (#5358), circuit breaker semantics; community pushing for Fail-Closed defaults
3. **Input ergonomics** — Multi-line mode and configurable send shortcuts (#5345); users want `Enter` for newline, `Ctrl+Enter` to send (matching Grok Build / Codex patterns)
4. **Hook-based lifecycle** — PreToolUse/PostToolUse layer for cancel/pause/resume across all action types (#1917); unifying architectural pattern identified
5. **i18n expansion** — Continue broadening locale coverage beyond core UI chrome to commands, modals, widgets, and approval dialogs (#790)
6. **Read-only Fleet roles** — Classifier-bounded bash for `scout`/`reviewer`/`planner` roles (#5356); current role gate denies all shell access outright

---

## 6. Developer Pain Points

- **Schema explosion** — The 32-property agent tool schema with zero required fields and 8 actions causes repeated model errors; simplification is a top priority (#5324, #5369)
- **Test isolation** — Four TUI tests read real machine state (`~/.codewhale`, display probe), failing deterministically on dev boxes while CI stays green (#5359, #5368)
- **Config migration fragility** — Legacy migration leaves stale config/secret paths silently across Windows/Cygwin boundaries (#2369)
- **Shell completion leaks** — Child-owned shell completions pollute the parent model stream, causing confusion in multi-agent workflows (#5339)
- **Large-batch agent timeouts** — `agent_wait` times out when spawning many sub-agents (e.g., 10-chunk novel processing), appearing as session freeze (#1425)
- **macOS text corruption** — Agent-written text renders as garbled output on macOS (#5374), blocking readability
- **SSH sandbox blocking** — Built-in shell sandbox appears to block TCP 22 outbound, breaking SSH/scp from within TUI (#1829)
- **NIM API 404s** — NVIDIA NIM integration returns 404 on Windows; affects doctor diagnostics and API calls (#1482)
- **Slow report I/O** — Cache thrashing causes extremely low hit rates when merging analysis reports to local documents (#1732)
- **i18n gaps** — Chinese characters garble in Agent real-time output (#1675); many user-visible strings remain hardcoded in English (#790)

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*