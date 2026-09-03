# AI CLI Tools Community Digest 2026-09-03

> Generated: 2026-09-03 04:00 UTC | Tools covered: 10

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



# AI CLI Tools Ecosystem Comparison Report
**Date:** 2026-09-03

---

## 1. Ecosystem Overview

The AI CLI tools landscape in September 2026 is characterized by intense competition across six major vendors, with communities collectively reporting 70+ open issues and 60+ active PRs daily. The dominant theme is **agent reliability** — subagent recovery, session resumption stability, and permission system integrity appear across every tool's hot issues. Enterprise adoption pressures are reshaping feature priorities: multi-model support, cost accounting transparency, and headless automation capabilities are now table stakes. Windows desktop stability remains a persistent cross-platform weakness, while security hardening (variable expansion bypasses, config-path ACLs, dependency CVE patches) reflects maturing production use cases.

---

## 2. Activity Comparison

| Tool | Issues (Hot) | PRs (24h) | Release | Activity Level |
|------|-------------|-----------|---------|---------------|
| **Claude Code** | 10 | 4 | v2.1.259 | High — enterprise features |
| **OpenAI Codex** | 10 | 12 | rust-v0.153.0 | High — UX polish wave |
| **Gemini CLI** | 10 | 10 | None (nightly failed) | Medium — security focus |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.83-3 | Low — issue-driven |
| **Kimi Code CLI** | 5 | 0 | None | Low — parity catching |
| **OpenCode** | 10 | 12 | v1.18.27 | High — plugin expansion |
| **Pi** | 10 | 10 | None | Medium — provider compat |
| **Qwen Code** | 10 | 15 | live-host-v0.2.0 | High — CI hardening |
| **DeepSeek TUI** | 10 | 10 | None (v0.9.12) | Medium — structural refactor |
| **Grok Build** | 0 | 0 | None | None — dormant |

**Key metrics:**
- **Most active PRs:** Qwen Code (15), OpenCode (12), Codex (12)
- **Most engaged issues:** OpenCode #6231 (225 👍 auto-discover models), OpenCode #27167 (140 👍 native session goals)
- **Release velocity:** 5 tools shipped releases; 3 had no activity; 1 dormant

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Multi-model support** | Claude Code, Codex, Copilot CLI, OpenCode, Pi | Switch models mid-session, BYOK/local providers, per-agent model lists |
| **Session resumption stability** | Claude Code, Codex, Copilot CLI, Pi, Qwen | OOM crashes on resume, stale cache invalidation, handle leaks |
| **Windows desktop hardening** | Claude Code, Codex, Pi, OpenCode, Qwen | Orphaned processes, AppX container locks, stealth update failures |
| **MCP server reliability** | Claude Code, Codex, Copilot CLI, OpenCode, DeepSeek | OAuth token reuse, tool connection loss, OAuth DCR discovery |
| **Headless/automation mode** | Claude Code, Codex, OpenCode, DeepSeek | `--permission-prompts none`, unattended CI pipelines, control sockets |
| **Cost/billing transparency** | Claude Code, Codex, Copilot CLI, OpenCode | Per-model rate limits in status line, OTel span billing, quota depletion tracking |
| **Agent orchestration** | Gemini CLI, OpenCode, Pi, DeepSeek | Subagent turn-limit handling, generalist hangs, skill utilization |
| **Local-first workflows** | OpenCode, DeepSeek, Pi | Auto-discover Ollama/LM Studio models, small-model routing, input budget fixes |

---

## 4. Differentiation Analysis

| Dimension | Leaders | Approach |
|-----------|---------|----------|
| **Enterprise focus** | Claude Code, Copilot CLI | Centralized config (`managedMcpServers`), org-wide policy, cost accounting |
| **Open-source extensibility** | OpenCode, DeepSeek TUI | Plugin RPC APIs, permission assertions, browser pane integration |
| **Provider neutrality** | DeepSeek TUI, Pi | Removing vendor-specific gates, multi-provider auth, universal model discovery |
| **Agent reliability** | Gemini CLI, OpenCode | Subagent recovery nudges, turn-limit signaling, stop-repeated-call loops |
| **Structural refactoring** | DeepSeek TUI | Crate decomposition epic, mega-file splitting (18k→modular), provider neutrality audit |
| **CI/DevOps integration** | Qwen Code, Copilot CLI | ECS lane isolation, shared-pool timeout ceilings, daemon shell guards |
| **UX polish** | Codex, OpenCode | Vim mode undo/redo, session goal tracking, workbar rename, experimental settings |

**Target user divergence:**
- **Claude Code/Copilot CLI:** Enterprise teams, production automation, regulated environments
- **OpenCode/DeepSeek:** Open-source contributors, local-first workflows, plugin developers
- **Gemini CLI/Codex:** General developers, speed-focused users, multi-provider adopters
- **Qwen Code:** CI/CD pipelines, cloud-hosted deployments, Chinese ecosystem users

---

## 5. Community Momentum & Maturity

| Maturity Tier | Tools | Indicators |
|---------------|-------|------------|
| **Mature & Active** | Claude Code, OpenCode, Codex | Regular releases, high-issue engagement (100+ 👍), enterprise feature demand |
| **Rapidly Iterating** | Qwen Code, DeepSeek TUI | High PR volume, structural refactors, CI hardening focus |
| **Stable but Issue-Driven** | Gemini CLI, Pi | No recent releases but active security PRs, provider-compat fixes |
| **追赶中** | Copilot CLI, Kimi Code CLI | Release activity but zero PRs, community reports systemic bugs (OOM, MCP) |
| **Dormant** | Grok Build | No activity |

**Community health signals:**
- **Highest engagement:** OpenCode #6231 (225 👍) — auto-discover models; #27167 (140 👍) — native session goals
- **Most contentious:** Claude Code Windows crash (#53247, #85199) — production-blocking stability issues
- **Fastest PR velocity:** Qwen Code (15 PRs) — CI and OpenTUI migration driving activity
- **Security maturation:** Gemini CLI patched 2 critical CVEs (`simple-git`, `shell-quote`) in one day

---

## 6. Trend Signals

### Industry Trends from Community Feedback

1. **Agent reliability is the new battleground** — Every tool community reports subagent hangs, turn-limit silence, and session state corruption. The market is shifting from "can it code?" to "can it reliably complete multi-step workflows?"

2. **Windows is the canary for desktop maturity** — Orphaned processes, AppX locks, and stealth-update failures appear across Claude Code, Codex, Pi, OpenCode, and Qwen. Cross-platform parity remains unfinished business.

3. **Cost transparency is table stakes** — Rate limit visibility, per-model billing, and quota depletion tracking are top-voted requests everywhere. Enterprise buyers demand spend predictability.

4. **MCP is fragile at scale** — Token reuse failures, connection drops, and OAuth discovery bugs affect every major tool. The ecosystem is outpacing the protocol's reliability guarantees.

5. **Local-first is mainstream** — Ollama/LM Studio auto-discovery (#6231 with 225 👍) and small-model routing signals that local LLM workflows are no longer niche.

6. **Plugin extensibility is differentiating** — OpenCode's permission assertions (#46530) and browser plugin API (#44838), plus DeepSeek's marketplace management (#5842), show the platform layer is becoming the product.

### Reference Value for Developers

- **For enterprise adoption:** Claude Code and Copilot CLI offer the strongest org-management features, but monitor Windows stability before production rollout.
- **For open-source contribution:** OpenCode and DeepSeek TUI have the most active PR pipelines and clearest contribution paths (crate decomposition, provider neutrality audits).
- **For local-first workflows:** OpenCode's auto-discover and small-model routing, combined with DeepSeek's Ollama budget fixes, make them the strongest local-model choices.
- **For CI/CD integration:** Qwen Code's ECS lane isolation and control sockets, plus DeepSeek's per-session Unix sockets, are production-ready patterns.
- **Risk areas:** Copilot CLI's OOM-on-resume (#4664, #4686, #4699) and Claude Code's Windows crash loops (#53247, #85199) indicate systemic issues that warrant caution for long-running deployments.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-09-03 • Source: anthropics/skills*

---

## 1. Top Skills Ranking

| # | Skill / PR | Functionality | Discussion Highlights | Status |
|---|------------|---------------|-----------------------|--------|
| 1 | **[PR #1298](https://github.com/anthropics/skills/pull/1298) `skill-creator: run_eval.py fix`** | Fixes the skill‑creator evaluation harness that always reported `recall=0%` due to Windows‑specific stream‑reading and trigger‑detection bugs. | >10 independent reproductions; the bug broke the entire description‑optimization loop. | 🟡 Open |
| 2 | **[PR #1628](https://github.com/anthropics/skills/pull/1628) `Hivemind`** | Multi‑agent orchestration skill that delegates mechanical work to headless `opencode` workers while Claude Code remains the sole planner/reviewer. | Addresses cost‑per‑token friction by splitting expensive‑model planning from cheap‑model execution. | 🟡 Open |
| 3 | **[PR #723](https://github.com/anthropics/skills/pull/723) `testing‑patterns`** | Comprehensive testing‑stack skill covering philosophy, unit testing (AAA pattern, edge cases), and React‑component testing with Testing Library. | Fills a gap in test‑generation guidance; broad scope spans unit, integration, and frontend. | 🟡 Open |
| 4 | **[PR #568](https://github.com/anthropics/skills/pull/568) `servicenow`** | Enterprise‑platform skill covering ITSM, ITOM, SecOps, ITAM/SAM, FSM, SPM, CSDM, and IntegrationHub workflows. | First major IT‑service‑management skill; aims at enterprise‑workflow automation. | 🟡 Open |
| 5 | **[PR #514](https://github.com/anthropics/skills/pull/514) `document‑typography`** | Typographic‑quality‑control skill that prevents orphan words, widow paragraphs, and numbering misalignment in AI‑generated documents. | Targets a universal pain point in document generation; no prior skill addresses print‑quality layout. | 🟡 Open |
| 6 | **[PR #1367](https://github.com/anthropics/skills/pull/1367) `self‑audit`** | Pre‑delivery quality‑gate skill that performs mechanical file verification followed by a four‑dimension reasoning audit. | Universal, stack‑agnostic; proposes a “damage‑severity priority order” for output inspection. | 🟡 Open |
| 7 | **[PR #83](https://github.com/anthropics/skills/pull/83) `skill‑quality‑analyzer` & `skill‑security‑analyzer`** | Meta‑skills that evaluate other skills across five dimensions (structure, documentation, examples, security, performance). | First formal skill‑quality framework; could become a gate for marketplace submissions. | 🟡 Open |
| 8 | **[PR #486](https://github.com/anthropics/skills/pull/486) `odt`** | Skill for creating, filling, reading, and converting OpenDocument Format files (`.odt`, `.ods`) and parsing ODT to HTML. | Extends document‑skill coverage beyond DOCX/PDF to the ISO‑standard OpenDocument family. | 🟡 Open |

---

## 2. Community Demand Trends

Analysis of the top‑commented issues reveals four concentrated demand areas:

| Trend | Representative Issues | Core Request |
|-------|-----------------------|--------------|
| **Security & Trust Boundaries** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments), [#1175](https://github.com/anthropics/skills/issues/1175) (4 comments) | Prevent namespace impersonation, enforce permission scoping, and validate skill provenance before execution. |
| **Tooling & Evaluation Rigor** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments), [#1390](https://github.com/anthropics/skills/issues/1390) (4 comments), [#202](https://github.com/anthropics/skills/issues/202) (8 comments) | Fix broken evaluation harnesses, ensure metrics reflect real behavior, and improve the `skill‑creator` workflow to match best practices. |
| **Enterprise & Platform Integration** | [#568](https://github.com/anthropics/skills/pull/568) (ServiceNow), [#1615](https://github.com/anthropics/skills/pull/1615) (SCNet HPC), [#1487](https://github.com/anthropics/skills/issues/1487) (claude‑api token bloat) | Skills that encapsulate complex enterprise systems (ITSM, HPC clusters, API management) with predictable context‑window footprints. |
| **Multi‑Agent & Orchestration Patterns** | [#1628](https://github.com/anthropics/skills/pull/1628) (Hivemind), [#1385](https://github.com/anthropics/skills/issues/1385) (Reasoning Quality Gate), [#1329](https://github.com/anthropics/skills/issues/1329) (compact‑memory) | Lightweight delegation between specialized agents, pre‑task calibration, adversarial review, and compact state representation. |

---

## 3. High‑Potential Pending Skills

These open PRs show active community engagement, recent updates, and clear functional value—making them strong candidates for upcoming merges.

| PR | Skill | Why It’s High‑Potential |
|----|-------|--------------------------|
| [#1628](https://github.com/anthropics/skills/pull/1628) | `Hivemind` | Solves the cost‑context trade‑off with a novel planner/worker split; appeals to both individual developers and enterprise teams. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self‑audit` | Provides a universal quality‑gate that can be adopted as a pre‑delivery step across any project or stack. |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing‑patterns` | Fills a documented gap in test‑generation guidance; covers both backend and frontend testing philosophies. |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | First comprehensive enterprise‑IT‑service skill; broad coverage (ITSM, SecOps, FSM) matches high‑value enterprise workflows. |
| [#514](https://github.com/anthropics/skills/pull/514) | `document‑typography` | Addresses a near‑universal pain point in document generation; simple, focused, and widely applicable. |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill‑quality‑analyzer` / `skill‑security‑analyzer` | Could become de‑facto standards for skill validation, especially as the marketplace grows. |

---

## 4. Skills Ecosystem Insight

The community’s most concentrated demand is for **enterprise‑grade, security‑aware skills that encapsulate complex platform workflows (IT service management, HPC, document pipelines) while preserving context efficiency and enabling reliable evaluation.**

--- 

*Report generated from public GitHub data. All PRs and issues remain open as of 2026‑09‑03.*

---



# Claude Code Community Digest — 2026-09-03

## 1. Today's Highlights
Claude Code v2.1.259 ships with organizational `managedMcpServers` provisioning and a `--permission-prompts none` flag for headless automation. Community attention is heavily focused on Windows Desktop stability regressions tied to stealth updates, while a v2.1.259 regression has introduced unexpected permission prompts on compound Bash commands. Enterprise control and hook reliability remain the dominant themes in ongoing discussions.

## 2. Releases
**v2.1.259**
- **`managedMcpServers`**: New managed setting allowing organizations to push HTTP/SSE MCP server entries to every user (same shape as `.mcp.json`). Command-based entries are automatically skipped.
- **`--permission-prompts none`**: New CLI flag for unattended/headless hosts that suppresses all permission prompts that would normally interrupt automation pipelines.

## 3. Hot Issues
1. **[Multi-account switching on Claude Mobile](https://github.com/anthropics/claude-code/issues/36151)** (169 comments, 676 👍)  
   High-demand workflow feature for toggling accounts without shared email. The strong community signal indicates mobile parity with desktop/CLI multi-tenant flows is a top priority.
2. **[Windows Desktop always-on-top](https://github.com/anthropics/claude-code/issues/85891)** (65 comments, 145 👍)  
   Missing window Z-order control on Windows mirrors an existing macOS issue (#66516). Users report it disrupts multi-window IDE workflows.
3. **[Windows crash: orphaned Silo/Job Object after crash](https://github.com/anthropics/claude-code/issues/53247)** (51 comments, 22 👍)  
   Critical stability bug where `0x80070020` blocks re-launch until logoff/reboot. Directly impacts production environments relying on desktop client uptime.
4. **[Windows Desktop repeatedly crashes, requires Repair](https://github.com/anthropics/claude-code/issues/85199)** (50 comments, 10 👍)  
   Related to the Job Object/Silo issue; indicates the repair pathway is not self-healing and requires manual intervention.
5. **[Cowork git proxy blocks non-authorized repo pushes](https://github.com/anthropics/claude-code/issues/76248)** (32 comments, 12 👍)  
   `CCR_TEST_GITPROXY` rollout broke fine-grained PAT pass-through for repositories outside the session's authorized set. Impacts remote/cluster workflows.
6. **[Auto mode classifier unavailable](https://github.com/anthropics/claude-code/issues/63819)** (19 comments, 27 👍)  
   When `claude-opus-4-8` is throttled, auto mode falls back to blocking Bash/Write/Edit entirely. Highlights a fragility in the safety classifier fallback path.
7. **[Stealth update leaves orphaned processes](https://github.com/anthropics/claude-code/issues/89680)** (8 comments, 0 👍)  
   New report confirming the same Windows update pattern: old AppX container remains locked, preventing relaunch until reboot.
8. **[Permission bypass routes around PreToolUse hooks via Bash](https://github.com/anthropics/claude-code/issues/89251)** (4 comments, 1 👍)  
   Security-adjacent: when `bypassPermissions` is active, the system prompt instructs the model to perform writes through Bash, sidestepping native `Write|Edit|NotebookEdit` hooks.
9. **[v2.1.259 regression: bypassPermissions prompts on `cd && grep`](https://github.com/anthropics/claude-code/issues/91683)** (1 comment, 0 👍)  
   Compound commands now trigger permission prompts despite `bypassPermissions` being set. Directly impacts users who just upgraded.
10. **[Expose per-model weekly rate limits in status line](https://github.com/anthropics/claude-code/issues/73770)** (3 comments, 7 👍)  
    Feature request to surface Opus/Sonnet/Fable rate meters in the status line JSON. Low friction, high value for cost-aware teams.

## 4. Key PR Progress
*(4 active PRs in the 24h window)*
1. **[Add Linux/macOS Bash script for DevContainer startup](https://github.com/anthropics/claude-code/pull/41938)** — Closes a platform gap by providing a POSIX-compatible launcher alongside the existing Windows PowerShell script.
2. **[fix(security-guidance): make `**` glob patterns match zero-depth paths](https://github.com/anthropics/claude-code/pull/87079)** — Fixes a critical fnmatch delegation bug where `**/*.ts` excluded top-level files, silently weakening security rule coverage.
3. **[Fix duplicated word in CHANGELOG.md](https://github.com/anthropics/claude-code/pull/86537)** — Documentation-only typo correction (`to to` → `to`).
4. **[Add diagnostic script for GitHub connector showing 'Connected' but no tools](https://github.com/anthropics/claude-code/pull/61691)** — Addresses a persistent Cowork bug (#61682) by providing a PowerShell repair utility for the zero-tool state.

## 5. Feature Request Trends
- **Enterprise & Org Management**: Rapid demand for centralized config distribution (`managedMcpServers`) and granular observability (per-model rate limits in status line).
- **Headless & Automation First**: New CLI flags (`--permission-prompts none`) and requests for robust unattended execution signal a growing production/CI use case.
- **Cross-Platform & Cross-App Parity**: Mobile multi-account switching and DevContainer launcher parity show users expect feature consistency across web, desktop, CLI, and mobile clients.
- **Security & Hook Integrity**: Community is actively stress-testing the permission system, flagging both bypass paths and glob-matching gaps in security guidelines.

## 6. Developer Pain Points
- **Windows Desktop Update Pipeline**: Repeated reports of stealth updates leaving orphaned processes, locked AppX containers, and DACL-locked services (`0x80070020`, `0x80073CF6`, `0x80073D28`). Manual repair or reboots remain the only recovery path.
- **Permission System Fragility**: The `bypassPermissions` mode is triggering unexpected prompts on compound Bash commands (v2.1.259 regression), and hook writers are concerned about Bash-mediated writes circumventing `PreToolUse` safeguards.
- **Remote/Cowork Session Limits**: Git proxy restrictions are blocking legitimate PAT-based pushes outside the authorized repo set, and the GitHub MCP connector intermittently reports connected but exposes zero tools.
- **CLI Reliability Edge Cases**: Bash command truncation at ~8KB, silent hangs in local scheduled tasks, and auto-mode deadlocks when the Opus classifier is rate-limited.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-03

---

## 1. Today's Highlights

The `rust-v0.153.0` release lands with long-awaited Vim-mode undo/redo support and early plugin CLI capabilities, while a wave of 20+ closed PRs delivers major UX improvements including session resumption in the agent command center, coordinated MCP OAuth refresh, and Windows app-server daemon support. Community attention remains focused on quota management friction, persistent Windows app bugs, and session-handling edge cases.

---

## 2. Releases

### rust-v0.153.0 (Stable)
- **Vim mode** now supports undo (`u`) and redo (`Ctrl+R`), preserving complete drafts including pasted content and attachments ([#41941](https://github.com/openai/codex/pull/41941), [#42140](https://github.com/openai/codex/pull/42140))
- Plugin CLI gains `list`, `install`, and `remove` subcommands
- See also: `v0.153.0-alpha.6` and `v0.153.0-alpha.5.1` prerelease channels

---

## 3. Hot Issues

| # | Title | Engagement | Why It Matters |
|---|-------|------------|----------------|
| [#39903](https://github.com/openai/codex/issues/39903) | Disable "Ran N commands" collapsing | 59 comments · 79 👍 | Power users want full command visibility; high signal that the auto-collapse UX is frustrating for audit/debug workflows |
| [#41622](https://github.com/openai/codex/issues/41622) | Disable automatic conversation recaps | 15 comments · 41 👍 | Recaps add token overhead for experienced users; strong demand for a config toggle |
| [#40219](https://github.com/openai/codex/issues/40219) | Server-deleted conversations repopulate in Recents | 15 comments · 14 👍 | Data inconsistency bug; deleted conversations reappear, suggesting stale local caches |
| [#25828](https://github.com/openai/codex/issues/25828) | Phone verification bug (Indonesia) | 32 comments · 5 👍 | Auth roadblock for users in specific regions; impacts onboarding |
| [#41540](https://github.com/openai/codex/issues/41540) | Windows headless startup after node_repl.exe relocation failure | 15 comments · 1 👍 | MSIX auto-update triggers a runtime extraction failure, blocking the app for ~12 min |
| [#39989](https://github.com/openai/codex/issues/39989) | Windows desktop keeps deleted conversations in Recents | 15 comments · 1 👍 | Same stale-cache pattern as #40219 but on Windows |
| [#39823](https://github.com/openai/codex/issues/39823) | Session resume fails with "already has an active writer" | 13 comments · 2 👍 | Approval-mode and session-switching workflows can corrupt session state |
| [#31017](https://github.com/openai/codex/issues/31017) | Codex cannot access `gh` despite being logged in | 10 comments · 12 👍 | Auth token propagation issue between desktop and CLI tools |
| [#41541](https://github.com/openai/codex/issues/41541) | Pro weekly quota depletion accelerated by ~1.6–1.8× throughput | 8 comments · 0 👍 | Model runtime upgrades materially increase token consumption; users need visibility/transparency |
| [#41969](https://github.com/openai/codex/issues/41969) | Sudden weekly quota depletion + banked reset disappeared | 6 comments · 0 👍 | Billing/credit accounting issue reported by Pro Lite users |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#42428](https://github.com/openai/codex/pull/42428) | Use shared composer in agent command center | Replaces single-line input with full chat composer — multiline editing, Vim mode, keybindings, paste handling |
| [#42419](https://github.com/openai/codex/pull/42419) | Session resume in agent command center | New `agents.resume` action (`Ctrl+O`) opens the session resume picker directly from the command center |
| [#42425](https://github.com/openai/codex/pull/42425) | Discover TUI experimental features from server | Loads `/experimental` catalog at runtime; shows beta features with server-reported names, descriptions, and confidence |
| [#42417](https://github.com/openai/codex/pull/42417) | Expose managed application network requirements | Adds `application.network` managed requirements with exact-domain allow/deny rules and normalization |
| [#42413](https://github.com/openai/codex/pull/42413) | Coordinated MCP OAuth refresh | RMCP now refreshes and persists credentials through the pinned credential store for streamable HTTP MCP connections |
| [#42410](https://github.com/openai/codex/pull/42410) | Review and continue misalignment-paused chats | Users can now inspect misalignment findings and explicitly choose to proceed |
| [#42408](https://github.com/openai/codex/pull/42408) | Harden embedded composer input | `!`, `/`, `?` prefixes are now literal in plain-text composers; Vim-mode and paste-burst behavior preserved |
| [#42405](https://github.com/openai/codex/pull/42405) | App-server daemon on Windows | Enables daemon lifecycle commands and `codex agents` startup on Windows via AF_UNIX sockets |
| [#42392](https://github.com/openai/codex/pull/42392) | Managed daemon updates on Windows | Daemon update loop runs via non-interactive PowerShell; readiness handshake coordinates ownership transfer |
| [#42388](https://github.com/openai/codex/pull/42388) | Recover deferred environments after provisioning failure | Valid Ready reports can now replace a failed provisioning attempt on the same environment instance |

---

## 5. Feature Request Trends

- **Configurable UX polish:** Multiple requests for toggleable features (disable command collapsing, disable auto-recaps) reflect a desire for per-user control over defaults
- **Per-thread and per-session granularity:** Requests for per-thread skill/plugin selection (#30967), per-thread collaboration modes (#42401), and first-class session resumption indicate users want finer control over agent contexts
- **Cross-platform parity:** Windows-specific issues (#41540, #39989, #39933) and the new Windows daemon PR (#42405) show active investment in bringing Windows to feature parity with Unix
- **Long-thread navigation:** Proposal for a user-intent navigation rail (#35975) signals demand for better UX in extended agent sessions

---

## 6. Developer Pain Points

1. **Quota unpredictability:** Runtime upgrades (0.147 → 0.150) materially increased throughput, causing faster-than-expected weekly quota depletion (#41541, #41969). Users report difficulty tracking real consumption.
2. **Windows app stability:** Recurring issues with headless startup after updates, stale conversation caches, and IDE extension command failures suggest the Windows desktop layer needs sustained hardening.
3. **Session state corruption:** Session resume failures ("already has an active writer") and misalignment-pause state loss indicate fragile session lifecycle management, particularly around approval-mode and cross-platform handoff.
4. **Auth propagation gaps:** `gh` CLI access denial (#31017), MCP OAuth DCR discovery failures (#42427), and phone verification blocks (#25828) point to persistent auth token and credential-flow issues across integrations.
5. **Rate-limit exposure:** High-reasoning workloads and background backfill operations (#41130) are hitting rate limits aggressively, suggesting need for better throttling or queue management in the app server.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-03

## 1. Today's Highlights

The Gemini CLI project sees a notable security-focused push this week, with two critical CVE patches landing and a variable-expansion bypass fix merged. Agent reliability remains the dominant concern: subagent recovery, generalist-agent hangs, and browser-agent failures account for the most engagement on open issues. On the feature side, support for `gemini-3.8-flash` as the new default flash model is in review.

---

## 2. Releases

No new releases in the last 24 hours. The nightly-release workflow **failed** on 2026-09-03 — tracked in [#29174](https://github.com/google-gemini/gemini-cli/issues/29174).

---

## 3. Hot Issues

1. **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 · 13 comments · 2 👍
   The `codebase_investigator` subagent reports `status: "success"` with `Termination Reason: GOAL` even when it hit the turn limit without producing results. This silently hides interruptions and misleads the parent agent. High comment count signals repeated community encounters.

2. **[Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1 · 8 comments · 8 👍
   Deferring to the generalist agent causes indefinite hangs even for trivial tasks like folder creation. Workaround: explicitly disabling sub-agents. The strong 👍 count reflects broad pain.

3. **[Leverage model's bash affinity via Zero-Dependency OS Sandboxing](https://github.com/google-gemini/gemini-cli/issues/19873)** — P2 · 9 comments · 1 👍
   Proposes using Gemini 3's native bash chaining capability within a zero-dependency sandbox, preserving security without sacrificing UX. A forward-looking architecture discussion attracting strong interest.

4. **[Assess impact of AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — P2 · 7 comments
   Epic tracking whether AST-aware tools can reduce turn count and context noise by precisely reading method bounds and navigating codebase structure. Potential significant efficiency gain.

5. **[Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** — P2 · 6 comments
   Users report the agent ignores custom skills and sub-agents unless explicitly prompted. Anecdotal but widely felt; points to a prompt/orchestration gap.

6. **[Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)** — P2 · 5 comments · Security
   Auto Memory sends transcript content to the extraction agent before redaction occurs, creating a secrets-in-context risk. Security-conscious users are watching closely.

7. **[Shell command execution stuck with "Waiting input" after completion](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1 · 4 comments · 3 👍
   Simple CLI commands complete but Gemini continues showing "Awaiting user input." Repeatedly affects workflow; strong 👍 signals high frustration.

8. **[Browser subagent fails in Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** — P1 · 4 comments · 1 👍
   The browser agent crashes on Wayland compositors. Linux users without X11 are effectively blocked from browser automation.

9. **[Enhance browser_agent resilience: session takeover and lock recovery](https://github.com/google-gemini/gemini-cli/issues/22232)** — P2 · 4 comments
   Current "fail-fast" strategy on locked browser profiles leaves users stranded. Request for automatic session recovery is practical and well-scoped.

10. **[Gemini CLI encounters 400 error with >128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** — P2 · 3 comments
    Over 400 available tools trigger a 400 error. The agent needs smarter tool scoping — a growing concern as the ecosystem expands.

---

## 4. Key PR Progress

1. **[fix: inject on-retry nudge into conversation contents](https://github.com/google-gemini/gemini-cli/pull/28914)** — ✅ Closed
   Moves the recovery nudge from `systemInstruction` to the `contents` array, preserving static prompt prefix caching. Critical for latency-sensitive retry flows.

2. **[fix: block $VAR and ${VAR} variable expansion bypass](https://github.com/google-gemini/gemini-cli/pull/28902)** — ✅ Closed · Security · P1
   Closes an incomplete check in `detectBashSubstitution()` / `detectPowerShellSubstitution()` that allowed env-var expansion to bypass the security gate (GHSA-wpqr-6v78-jr5g). Defense-in-depth hardening included.

3. **[fix: atomic download and failure cleanup in WhisperModelManager](https://github.com/google-gemini/gemini-cli/pull/28917)** — ✅ Closed
   Writes to a temp file, respects backpressure, verifies download length, cleans up on failure, and atomically renames. Fixes [#28644](https://github.com/google-gemini/gemini-cli/issues/28644).

4. **[fix: buffer partial stdout chunks in WhisperTranscriptionProvider](https://github.com/google-gemini/gemini-cli/pull/28916)** — ✅ Closed
   Line-buffers stdout chunks so timestamped transcription lines split across `data` events are correctly assembled instead of dropped.

5. **[fix: keep useInputHistoryStore state updaters pure](https://github.com/google-gemini/gemini-cli/pull/29098)** — 🔄 Open · P1
   Removes side-effecting calls (`recalculateHistory`, `setPastSessionMessages`) from inside React state updaters, preventing double-invocation bugs under StrictMode.

6. **[fix: upgrade simple-git to 3.32.3 (CVE-2026-28292)](https://github.com/google-gemini/gemini-cli/pull/29094)** — 🔄 Open · Critical CVE
   Addresses a critical vulnerability in the `simple-git` dependency. Essential for users with supply-chain scanning enabled.

7. **[fix: upgrade shell-quote to 1.8.4 (CVE-2026-9277)](https://github.com/google-gemini/gemini-cli/pull/29095)** — 🔄 Open · Critical CVE
   Patches a critical CVE in `shell-quote`. Complements the simple-git upgrade for a cleaner dependency surface.

8. **[feat: add support for gemini-3.8-flash as default flash model](https://github.com/google-gemini/gemini-cli/pull/29172)** — 🔄 Open
   Registers `gemini-3.5-flash-lite` through `gemini-3.8-flash` and promotes `gemini-3.8-flash` as the new default. Extends `VALID_GEMINI_MODELS` and model config aliases.

9. **[fix: enforce strict permission and ownership checks on system-wide config paths](https://github.com/google-gemini/gemini-cli/pull/29115)** — 🔄 Open
   Adds ACL verification (PowerShell on Windows, POSIX equivalents) before loading system-wide config files, preventing privilege-escalation vectors via writable config paths.

10. **[fix: enhance workspace path boundary checks and symlink resolution](https://github.com/google-gemini/gemini-cli/pull/29170)** — 🔄 Open
    Strengthens workspace boundary enforcement and symlink resolution across command safety heuristics and file discovery on both POSIX and Windows.

---

## 5. Feature Request Trends

- **Agent reliability & recovery** — The #1 theme: subagent turn-limit handling, generalist-agent hangs, browser-agent session recovery, and skill/subagent utilization all point to a community craving more robust agent orchestration.
- **AST-aware codebase tooling** — Multiple issues (#22745, #22746) push for parser-aware reads and navigation to cut context waste and turn count.
- **Security hardening** — Redaction-before-context (#26523), variable-expansion bypass fixes, config-path ACLs (#29115), and symlink boundary checks (#29170) show a clear trend toward defense-in-depth.
- **Sandboxing & POSIX affinity** — The zero-dependency OS sandboxing proposal (#19873) reflects interest in letting the model's native bash capabilities shine within strict boundaries.
- **Model catalog expansion** — The gemini-3.8-flash PR (#29172) indicates ongoing expansion of the Flash model lineup as default options.

---

## 6. Developer Pain Points

- **Subagent silence on failure** — Agents reporting `GOAL` success when they actually hit turn limits (#22323) or hang indefinitely (#21409) creates invisible failures that are hard to debug. The community repeatedly requests better termination signaling.
- **Shell command state stuck** — Commands that complete but leave Gemini in an "Awaiting user input" loop (#25166) break automation workflows and frustrate power users.
- **Browser agent fragility on Linux** — Wayland failures (#21983) and locked-profile dead-ends (#22232) make browser automation unreliable for a significant subset of the user base.
- **Tool inventory bloat** — The 400-tool 400-error ceiling (#24246) means users with rich skill/extension setups hit hard limits unexpectedly.
- **Auto Memory privacy concerns** — Sending raw transcripts to extraction agents before redaction (#26525) is a recurring worry for users handling sensitive codebases.
- **Dependency security debt** — Critical CVEs in `simple-git` and `shell-quote` (#29094, #29095) highlight the risk of transitive dependencies in a tool that executes arbitrary shell commands.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-03

## 1. Today's Highlights

GitHub Copilot CLI v1.0.83-3 was released with fixes and new features including multi-model support for custom agents and a new `claude-fable-5.1` model. Meanwhile, the community flagged significant regressions in session resumption, MCP server reliability, and a Node.js OOM crash affecting long-running sessions.

## 2. Releases

**v1.0.83-3** ([Release](https://github.com/github/copilot-cli/releases/tag/v1.0.83-3))
- Custom agents can now list several models in `model` (tried in order until one is available), with `model-policy: required` to enforce model restrictions.
- Added support for `claude-fable-5.1`.
- Linux sandboxes now restrict network egress to the configured proxy.

## 3. Hot Issues

1. **#4664 — Heap OOM crash on session resume** ([Issue](https://github.com/github/copilot-cli/issues/4664))
   The CLI crashes with a V8 heap OOM when resuming a long-standing session, blocking users from continuing their work. Multiple reports confirm the same pattern, making this a high-impact reliability concern.

2. **#4695 — MCP OAuth tokens not reliably reused** ([Issue](https://github.com/github/copilot-cli/issues/4695))
   HTTP MCP servers with OAuth (PKCE) generate duplicate cache-key entries instead of reusing valid tokens, forcing repeated re-authentication and degrading session continuity.

3. **#4224 — OTel subagent spans omit billing attributes** ([Issue](https://github.com/github/copilot-cli/issues/4224))
   Subagent calls are invisible to external cost accounting because spans lack `github.copilot.nano_aiu` and cost metadata, undercounting actual billing. Critical for enterprise users tracking spend.

4. **#4438 — `disable-model-invocation: true` makes skills unreachable** ([Issue](https://github.com/github/copilot-cli/issues/4438))
   A skill marked to disable model invocation becomes entirely inaccessible, even via explicit user invocation, instead of being restricted to manual use only. 6 👍 indicates strong interest in the fix.

5. **#4680 — Wrong model ID sent to custom OpenAI-compatible endpoints** ([Issue](https://github.com/github/copilot-cli/issues/4680))
   The CLI sends `gpt-5.4-nano` instead of the configured model name (e.g., `mimo-v2.5`) to custom endpoints, killing the session with an immediate error.

6. **#4686 — Node.js OOM after ~37 min with 31,965 leaked libuv handles** ([Issue](https://github.com/github/copilot-cli/issues/4686))
   A severe memory leak in SEA builds causes every session to crash after ~37 minutes. The issue persists across environments and points to a fundamental handle management bug.

7. **#2630 — Custom agent `mcp-servers` not connected in sub-agent or `--prompt` contexts** ([Issue](https://github.com/github/copilot-cli/issues/2630))
   Custom agents with declared MCP servers lose their tool connections when invoked as sub-agents or in `--prompt` mode, silently degrading agent capability.

8. **#3709 — `/model` should switch to BYOK/local models in one session** ([Issue](https://github.com/github/copilot-cli/issues/3709))
   BYOK mode pins a session to a single model and `/model` only lists GitHub-hosted options, excluding local providers. 29 👍 makes this the most upvoted open issue, signaling high demand.

9. **#4671 — OAuth login fails behind TLS-inspecting proxy (regression in 1.0.81)** ([Issue](https://github.com/github/copilot-cli/issues/4671))
   A regression in v1.0.81 broke both device-code and web OAuth flows behind corporate HTTP proxies with TLS inspection. Closed, but highlights a persistent enterprise onboarding blocker.

10. **#4699 — OOM on long `--resume` sessions with crash dumps in cwd** ([Issue](https://github.com/github/copilot-cli/issues/4699))
    Reports repeated V8 heap OOM crashes at the 4 GiB cap during resumed sessions, with diagnostic dumps written into the user's working directory. Corroborates #4664 and #4686 as a pattern.

## 4. Key PR Progress

No pull requests were opened or merged in the last 24 hours.

## 5. Feature Request Trends

- **Multi-model flexibility**: Users want to switch models (including BYOK/local) mid-session via `/model` (#3709), and per-agent provider selection (#4703). The v1.0.83-3 release partially addresses this with multi-model lists.
- **Enterprise cost accounting**: OTel span enhancements (#4224) and ACP context-tier configuration (#4275) show demand for better observability and parity between interactive and ACP modes.
- **Shell/config flexibility**: Support for configurable shell types on Windows (#2271) and better handling of instruction files (#4702) indicate ongoing needs for enterprise and Windows environment customization.

## 6. Developer Pain Points

- **Session resumption instability**: Three separate issues (#4664, #4686, #4699) report OOM crashes during session resume, pointing to a systemic memory-leak problem in long-running or resumed sessions.
- **MCP server fragility**: Repeated reports of servers failing to connect (#2630), losing handles mid-session (#4598), and OAuth tokens not being reused (#4695) suggest the MCP host layer needs substantial hardening.
- **Enterprise proxy & Windows compat**: Proxy-related auth failures (#4671), Windows path-truncation in permission prompts (#4701), and spurious PowerShell errors in ConstrainedLanguage mode (#4683) continue to create friction for corporate users.
- **Skill/agent configuration bugs**: `disable-model-invocation` making skills unreachable (#4438), wrong model IDs sent to custom endpoints (#4680), and `skillDirectories` ignored in ACP mode (#4700) reflect a pattern of configuration options not behaving as documented.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-03

## 1. Today's Highlights

The Kimi Code CLI community saw five issues closed in the last 24 hours, with no new releases or pull requests merged. The most engaged issue this period is the `--agent-file` feature request for `kimi web` (#1307), which has gathered three upvotes, followed by discussions around SSH remote-server usability and an undo feature request.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **[Enhancement] --agent-file for 'kimi web' as in 'kimi'** — [Issue #1307](https://github.com/MoonshotAI/kimi-cli/issues/1307)
   **Why it matters:** `--agent-file` is available on the `kimi` subcommand but missing from `kimi web`, creating an inconsistent developer experience. The author has already implemented the fix. **Community reaction:** 3 👍 — the highest engagement this period.

2. **[Bug] SSH remote server communication failure** — [Issue #1393](https://github.com/MoonshotAI/kimi-cli/issues/1293)
   **Why it matters:** Users running Kimi CLI on remote SSH servers without graphical interfaces or DNS modification privileges report inability to communicate, a real blocker for server-side workflows. **Community reaction:** 1 👍, 1 comment.

3. **[Enhancement] Undo function** — [Issue #1311](https://github.com/MoonshotAI/kimi-cli/issues/1311)
   **Why it matters:** The lack of an undo feature is a notable gap compared to peers like opencode, and users are explicitly requesting parity. **Community reaction:** 1 👍.

4. **[Enhancement] Inline Mermaid diagrams in webui** — [Issue #1310](https://github.com/MoonshotAI/kimi-cli/issues/1310)
   **Why it matters:** Mermaid parsing already exists in the codebase; enabling inline rendering in the web UI would significantly improve visual output without heavy lift. **Community reaction:** 1 👍.

5. **[Enhancement] Optional Openclaw-like features (heartbeat, cron, memories)** — [Issue #1309](https://github.com/MoonshotAI/kimi-cli/issues/1309)
   **Why it matters:** A forward-looking request for persistent background features (heartbeat system, cron jobs, memories) that would expand Kimi CLI beyond interactive sessions. References a potential lightweight integration with nanobot. **Community reaction:** 0 👍.

## 4. Key PR Progress

No new pull requests reported in the last 24 hours.

## 5. Feature Request Trends

The community is pushing in three clear directions:

- **Feature parity with peers** — Undo (#1311), `--agent-file` support in `kimi web` (#1307), and inline Mermaid rendering (#1310) all reflect a desire for Kimi CLI to match capabilities found in competing tools like opencode and Openclaw.
- **Persistent / asynchronous capabilities** — The Openclaw-like feature request (#1309) signals interest in heartbeat, cron jobs, and memory systems for long-running agent workflows.
- **Remote & headless usability** — SSH server communication (#1293) highlights a need for better headless/remote-server support.

## 6. Developer Pain Points

- **Inconsistent CLI subcommand APIs:** `--agent-file` works in `kimi` but not `kimi web`, forcing users to adapt workflows or lose customization.
- **SSH / remote-server support gaps:** Running Kimi CLI on headless SSH servers without DNS modification rights remains problematic.
- **Missing undo functionality:** Developers familiar with opencode's undo feature are finding the absence in Kimi CLI a workflow disruption.
- **Limited visual rendering in webui:** Users want Mermaid diagrams rendered inline rather than as raw text output.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-09-03

## 1. Today's Highlights

OpenCode v1.18.27 shipped with critical timeout defaults and an Anthropic thinking-mode fix, while the community pushes hard on native session goals (`/goal`), auto-discovery of local provider models, and browser pane integration. A wave of Windows-specific bugs has been resolved, and plugin extensibility is expanding with permission assertions and a new browser plugin API.

## 2. Releases

**v1.18.27** — Core bugfixes addressing reliability under slow model startups:
- Default provider header timeouts to **5 minutes** (previously aggressive defaults caused premature failures).
- Default streamed chunk timeouts to **5 minutes**, with `false` supported to disable entirely.
- Anthropic `thinking.blockBinding` now opt-out-able via config, fixing `prefix_mismatch_behavior` errors on Amazon Bedrock (`claude-opus-5`).

[GitHub Releases](https://github.com/anomalyco/opencode/releases)

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#27167](https://github.com/anomalyco/opencode/issues/27167) | **Native session goals with `/goal`** | Long-requested persistent session lifecycle — agents could track multi-step goals without manual orchestration. | 🔥 140 👍, 78 comments — top-voted open issue |
| [#6231](https://github.com/anomalyco/opencode/issues/6231) | **Auto-discover models from OpenAI-compatible providers** | Eliminates manual model listing for LM Studio, Ollama, llama.cpp — critical for local AI workflows. | 225 👍, 48 comments — highest engagement overall |
| [#46729](https://github.com/anomalyco/opencode/issues/46729) | **Bedrock Anthropic `prefix_mismatch_behavior` error** | Blocks `claude-opus-5` on Bedrock after v1.18.26 upgrade; fixed in v1.18.27. | 13 👍, 6 comments |
| [#37650](https://github.com/anomalyco/opencode/issues/37650) | **Optional search metadata breaks permission listing** | Schema encoding failure when optional `glob`/`grep` fields are omitted — impacts session permission flows. | 6 comments |
| [#36413](https://github.com/anomalyco/opencode/issues/36413) | **`opencode run` exits 0 with empty stdout on auto-rejected tool** | Breaks automation pipelines — no machine-detectable signal when tool calls are rejected and no final message is produced. | 7 comments |
| [#46929](https://github.com/anomalyco/opencode/issues/46929) | **Small/fast model for lightweight agent turns** | Long-running tasks waste tokens on simple confirmations; `Catalog.model.small()` exists but isn't used for agent turns. | Closed (PR #46928) |
| [#28590](https://github.com/anomalyco/opencode/issues/28590) | **`writeOsc52` broken under GNU screen** | screen uses different escape sequences than tmux — clipboard writes produce garbled output. | Closed |
| [#45823](https://github.com/anomalyco/opencode/issues/45823) | **houseCARL + Muse Spark 1.2 recursive JSON schema crash** | Specific model + MCP combo fails immediately; other models work fine with the same MCP enabled. | 2 comments |
| [#46868](https://github.com/anomalyco/opencode/issues/46868) | **Configuring clang-format/air/uv silently disables formatter** | Name-based formatter config in `opencode.json` silently kills the formatter — subtle and hard to debug. | 3 comments |
| [#46931](https://github.com/anomalyco/opencode/issues/46931) | **Go usage dashboard double-charges `glm-5.3-flash`** | Half-price promotion not reflected in dashboard billing — shows full cost, confusing users on budget plans. | 2 comments |

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#46974](https://github.com/anomalyco/opencode/pull/46974) | **Fix: preserve revert consistency** | Bug fix | V2 sessions could accept new prompts while an undo was still saving, causing revert state corruption. Supersedes #42461. |
| [#46928](https://github.com/anomalyco/opencode/pull/46928) | **Allow agents to use small model for lightweight turns** | Feature | Closes #46929. Reuses `Catalog.model.small()` for non-critical agent turns, reducing latency and cost on multi-step tasks. |
| [#46970](https://github.com/anomalyco/opencode/pull/46970) | **Reuse current location for directory browsing** | Bug fix | Directory completion was booting a new runtime (and inherited MCP servers) per directory. Now keeps one stable Location. |
| [#46973](https://github.com/anomalyco/opencode/pull/46973) | **Dedicated experimental settings page** | Feature | Moves Tabs and Show project names into a separate Experimental settings tab for cleaner organization. |
| [#46972](https://github.com/anomalyco/opencode/pull/46972) | **Remove background running indicator** | Bug fix | Cleans up the TUI — removes redundant `Running` label/spinner below transcript while preserving `Working` state logic. |
| [#46971](https://github.com/anomalyco/opencode/pull/46971) | **Bind embedded transport at request time** | Bug fix | Effect apps supplying custom `FetchHttpClient` could redirect embedded SDK requests away from localhost. Now binds per-request. |
| [#46530](https://github.com/anomalyco/opencode/pull/46530) | **Expose permission assertions to plugins** | Feature | Adds `ctx.permission.assert(input)` to Effect and Promise plugins, reusing the existing permission engine without a new HTTP endpoint. |
| [#44838](https://github.com/anomalyco/opencode/pull/44838) | **Connect browser pane through plugin RPC** | Feature | Adds a `Browser` tab to the review pane with address bar, nav controls, and sandboxed Chromium connected via plugin RPC. |
| [#46272](https://github.com/anomalyco/opencode/pull/46272) | **Stop repeated identical tool call loops** | Bug fix | Closes #45442. Terminates sessions after 10 consecutive calls with the same tool name and canonical arguments. |
| [#46912](https://github.com/anomalyco/opencode/pull/46912) | **Wait for stdout writes before exit (piped JSON)** | Bug fix | Closes #29330. `export`, `session list --format json`, and `db --format json` now flush stdout before `process.exit()`, preventing truncated output in pipes. |

## 5. Feature Request Trends

- **Session-level orchestration**: Native `/goal` and `/loop` commands (#27167, #46328) signal strong demand for built-in multi-step goal tracking without plugin scaffolding.
- **Local provider ergonomics**: Auto-discovery of models (#6231) and small-model routing for lightweight turns (#46928/#46929) reflect a growing local-first AI workflow.
- **Plugin extensibility**: Permission assertions (#46530) and the browser plugin API (#46531/#44838) show the platform moving toward richer third-party tooling.
- **Diagnostic transparency**: Users want clearer error signals in automation modes (#36413) and better visibility into cost/billing (#46931, #35072).

## 6. Developer Pain Points

- **Windows compatibility debt**: A cluster of 6+ Windows-specific bugs (file watcher paths #35329, terminal title restore #35328, `Stop-Process` killing opencode #35332, `@file` autocomplete #35330, NSIS updater killing CLI #35331) indicates uneven cross-platform testing.
- **Timeout defaults too aggressive**: The v1.18.27 fix for 5-minute default timeouts (#46729) suggests previous defaults were breaking real-world slow-model and Bedrock scenarios.
- **Formatter config trap**: Name-only formatter configuration silently disables the tool (#46868) — poor discoverability for a common setup path.
- **Streaming edge cases**: Orphan `tool-input-delta` events rendering as `⚙unknown` (#35336) and stalled local tool execution (#46934) point to gaps in the AI SDK runtime's event lifecycle handling.
- **Revert/undo state race**: V2 session reverts could corrupt state when new prompts arrive mid-undo (#46974, #42461) — a consistency bug in concurrent operation handling.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑09‑03

## 1. Today’s Highlights
The community addressed critical provider‑compatibility bugs: Gemini 3.x tool‑use failures due to missing `thought_signature`, OpenRouter free models rejecting requests with 400 errors because of exceeded `max_tokens`, and Windows `find` tool path‑pattern issues. On the development side, an opt‑in `AgentHarness` runtime and capability‑policy hook were merged, while several stale‑session‑write and Codex‑SSE‑parsing fixes were closed.

## 2. Releases
No new releases in the last 24 hours.

## 3. Hot Issues
1. **[Gemini 3.x tool‑use failure](https://github.com/earendil-works/pi/issues/6996)** – Models like `gemini-3.5-flash` fail when tool results are fed back because `thought_signature` is omitted from history. *8 comments* – high impact for Gemini users.
2. **[Branch summarization hard token cap](https://github.com/earendil-works/pi/issues/8845)** – `/tree` branch summarization deterministically fails on large branches because `maxTokens: 2048` is hardcoded. *7 comments* – affects repo‑scale workflows.
3. **[Windows `find` path‑pattern bug](https://github.com/earendil-works/pi/issues/6817)** – Patterns containing a path separator (e.g., `src/**/*.ts`) return no results on Windows. *6 comments* – breaks cross‑platform file discovery.
4. **[Core tool bugs (byte count, limit warning, surrogate split)](https://github.com/earendil-works/pi/issues/7121)** – Three independent issues in `write`, `find`, and `truncateLine` tools. *6 comments* – closed with fixes.
5. **[OpenRouter `:free` models return 400](https://github.com/earendil-works/pi/issues/8760)** – Pi sends `max_tokens` equal to the catalog’s `maxOutputTokens`, exceeding the provider’s hard limit. *4 comments* – impacts many free‑tier model users.
6. **[Bedrock OpenAI image rejection](https://github.com/earendil-works/pi/issues/8643)** – Images nested in `toolResult.content` are rejected; they must be hoisted to sibling user content blocks. *4 comments, 1 👍* – required for Bedrock/OpenAI image workflows.
7. **[Z.AI forced‑thinking reasoning leak](https://github.com/earendil-works/pi/issues/8706)** – When thinking is toggled off, GLM models still leak reasoning tokens into the output. *3 comments* – affects cost and output cleanliness.
8. **[Codex cached WebSocket retains old account](https://github.com/earendil-works/pi/issues/6513)** – Changing credentials within a session can reuse the previous account’s authenticated socket. *3 comments* – security/correctness concern.
9. **[OpenAI Responses `tool_choice` without tools](https://github.com/earendil-works/pi/issues/8820)** – xAI 400s compaction when `tool_choice` is sent without a `tools` array. *3 comments* – closed with fix.
10. **[Editor presentation options](https://github.com/earendil-works/pi/issues/9032)** – Request to expose `frameless` and `prompt‑prefix` controls on the TUI editor. *3 comments* – closed, accepted.

## 4. Key PR Progress
1. **[PR #8383](https://github.com/earendil-works/pi/pull/8383)** – *fix(ai): send LOW to disable thinking on gemini-3.7-flash* – Corrects the thinking‑level mapping that caused 400 errors.
2. **[PR #8994](https://github.com/earendil-works/pi/pull/8994)** – *fix(agent): map signal‑killed processes to non‑zero exit codes* – Ensures OOM‑killed child processes are reported as failures.
3. **[PR #9044](https://github.com/earendil-works/pi/pull/9044)** – *feat(agent): add initial recoverable harness runtime and capability policy* – Introduces `AgentHarness` lifecycle and opt‑in `ToolPolicy` for audit‑gable tool decisions.
4. **[PR #9041](https://github.com/earendil-works/pi/pull/9041)** – *fix(agent): reject stale JSONL session writes after delete* – Prevents recreation of headerless session files after a delete.
5. **[PR #9039](https://github.com/earendil-works/pi/pull/9039)** – *feat(coding-agent): add PI_DISABLE_MOUSE to opt out of fullscreen mouse tracking* – Allows disabling mouse‑sequence emission in fullscreen TUI mode.
6. **[PR #8818](https://github.com/earendil-works/pi/pull/8818)** – *fix(ai): omit Responses tool_choice when no tools are sent* – Fixes xAI compaction 400 errors.
7. **[PR #9037](https://github.com/earendil-works/pi/pull/9037)** – *fix(ai): bound and CRLF‑aware Codex SSE parsing* – Fixes heap OOM from unbounded SSE buffering.
8. **[PR #8998](https://github.com/earendil-works/pi/pull/8998)** – *System prompt refactor* – Draft to support mid‑session dynamic system‑prompt updates without wiping history.
9. **[PR #9031](https://github.com/earendil-works/pi/pull/9031)** – *feat(coding-agent): add opencode-go limits extension* – Extends footer to show OpenCode Go quota from response headers.
10. **[PR #9004](https://github.com/earendil-works/pi/pull/9004)** – *feat(ai): add vllmPriority compat flag for vLLM scheduler priority* – Allows sending vLLM’s `priority` field for queue‑ordering control.

## 5. Feature Request Trends
- **Provider‑specific compatibility fixes** – Gemini, OpenRouter, Bedrock, xAI, and Z.AI issues dominate recent discussions, reflecting rapid ecosystem changes.
- **Cross‑platform tool reliability** – Windows path‑separator handling, Linux musl‑linked binaries (`fd`, `rg`), and platform‑specific installation quirks are frequent asks.
- **Extensibility & policy hooks** – Requests for capability‑policy hooks, `AgentHarness` runtime, and extension‑API improvements signal a push toward safer, more sandboxed tool execution.
- **UI/UX customization** – Frameless editor, mouse‑tracking opt‑out, and OpenCode quota display show demand for configurable, information‑rich terminals.
- **Streaming & cancellation robustness** – Multiple issues around Esc‑to‑cancel, abort‑during‑compaction, and stale‑session writes indicate ongoing pain with async request lifecycle management.

## 6. Developer Pain Points
- **Authentication/session caching bugs** – Cached WebSockets reusing old credentials, parallel startups failing when another provider’s OAuth is expired.
- **Token‑limit misconfigurations** – Hardcoded or catalog‑based `max_tokens` values exceeding provider limits, causing 400 errors on free/open models.
- **Platform‑specific path and encoding issues** – Windows `find` patterns, non‑Latin characters in install paths, surrogate‑pair handling in truncation.
- **Memory and streaming leaks** – Unbounded SSE buffers causing heap OOM, incomplete cancellation of in‑flight requests, and stale JSONL writes.
- **Provider‑specific quirks** – Gemini’s missing `thought_signature`, Bedrock’s image‑nesting rejection, xAI’s `tool_choice` requirement, Z.AI’s thinking‑toggle behavior.
- **Tool‑result validation** – Extensions returning non‑`AgentToolResult` values (e.g., bare strings) cause TUI crashes, highlighting a need for stricter output normalization.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-03

## 1. Today's Highlights
Qwen Code shipped **live-host-v0.2.0**, advancing the OpenTUI migration and making CI concurrency tunable. Community attention is focused on daemon shell‑guard transparency, core content‑generation leaks, and stabilizing CI on the shared ECS pool.

## 2. Releases
**[live-host-v0.2.0](https://github.com/QwenLM/qwen-code/releases/tag/live-host-v0.2.0)**  
- `fix(ci)`: make shared ECS Vitest concurrency tunable  
- `feat(cli)`: OpenTUI migration batch 4  

## 3. Hot Issues
| # | Title | Why it matters |
|---|-------|----------------|
| [#8662](https://github.com/QwenLM/qwen-code/issues/8662) | Migrate TUI rendering layer from ink to OpenTUI (tracking) | Long‑running architectural shift to resolve flicker and structural limits of the ink 7 renderer. |
| [#9942](https://github.com/QwenLM/qwen-code/issues/9942) | Hide skill commands from top‑level slash completion | UX cleanup—skill commands currently clutter the `/` menu when many are installed. |
| [#10860](https://github.com/QwenLM/qwen-code/issues/10860) | `qwen serve` shell guard ignores session approval mode | Security/reliability: the daemon guard blocks git and non‑git commands outside the session directory without operator visibility or configuration. |
| [#10818](https://github.com/QwenLM/qwen-code/issues/10818) | Monitor pulse storm can DoS an interactive session | Closed bug where ESC cancel was ineffective and user input starved during high‑frequency agent polls. |
| [#10859](https://github.com/QwenLM/qwen-code/issues/10859) | Serve shell guard blocks every git command outside session dir | Closed enhancement highlighting the same daemon‑guard opacity; operator cannot override or audit. |
| [#9521](https://github.com/QwenLM/qwen-code/issues/9521) | Align follow‑up suggestion copy across TUI and Web Shell | Documentation/UI consistency follow‑up from review. |
| [#10782](https://github.com/QwenLM/qwen-code/issues/10782) | Removed workspaces leave stale selections that block new starts | Closed daemon bug where detaching a Channel Worker left stale entries in `committedSelection`. |
| [#8977](https://github.com/QwenLM/qwen-code/issues/8977) | Retain manual session name after `/clear` | Closed Web Shell bug causing manually labeled sessions to lose identity after clear. |
| [#10865](https://github.com/QwenLM/qwen-code/issues/10865) | Session workflow projection derived three times per render | Performance issue—rebuilds an index that should be built once. |
| [#10866](https://github.com/QwenLM/qwen-code/issues/10866) | Make session workflow DAG navigable | Feature request to add clickable dependencies and better navigation to the plan DAG. |

## 4. Key PR Progress
| # | Title | Status |
|---|-------|--------|
| [#10869](https://github.com/QwenLM/qwen-code/pull/10869) | ci: record host occupancy alongside disk‑pressure samples | Open |
| [#10870](https://github.com/QwenLM/qwen-code/pull/10870) | test: stop millisecond budgets from measuring the shared pool | Open |
| [#10857](https://github.com/QwenLM/qwen-code/pull/10857) | fix(web‑shell): scope select‑all in the cell value dialog to the value | Open |
| [#9099](https://github.com/QwenLM/qwen-code/pull/9099) | feat(review): add Maven multi‑module verification | Closed |
| [#10458](https://github.com/QwenLM/qwen-code/pull/10458) | fix(review): keep quoted code from blinding the footer strip | Open |
| [#10837](https://github.com/QwenLM/qwen-code/pull/10837) | feat(serve): add session resource catalog | Open |
| [#10575](https://github.com/QwenLM/qwen-code/pull/10575) | ci: give seconds‑long jobs their own ECS lane | Closed |
| [#10123](https://github.com/QwenLM/qwen-code/pull/10123) | fix(ci): salvage superseded review runs and hold the loop's report‑time base refresh | Open |
| [#10868](https://github.com/QwenLM/qwen-code/pull/10868) | fix(ci): retry a contended unit attempt and bound a hung one | Closed |
| [#10643](https://github.com/QwenLM/qwen-code/pull/10643) | feat(channels): Add worktree‑isolated named tasks | Open |
| [#10687](https://github.com/QwenLM/qwen-code/pull/10687) | fix(cli): guard channel pidfiles against PID reuse | Open |
| [#10754](https://github.com/QwenLM/qwen-code/pull/10754) | fix(web‑shell): disable Push while the branch is behind its upstream | Open |
| [#10756](https://github.com/QwenLM/qwen-code/pull/10756) | ci: split lint and static checks out of the Test job | Closed |
| [#10858](https://github.com/QwenLM/qwen-code/pull/10858) | fix(ci): give the scripts test suite the shared‑ECS timeout ceiling | Open |
| [#10532](https://github.com/QwenLM/qwen-code/pull/10532) | fix(acp‑bridge): deflake the exhaustive UTF‑16 byte‑estimate test | Closed |
| [#10828](https://github.com/QwenLM/qwen-code/pull/10828) | docs(design): Define relaxed standalone daemon ownership | Open |
| [#10805](https://github.com/QwenLM/qwen-code/pull/10805) | fix(release): report a workspace test run that fails with nothing failing | Open |
| [#10315](https://github.com/QwenLM/qwen-code/pull/10315) | fix(cli): deliver Agent View queued follow‑ups from the provider | Open |
| [#10800](https://github.com/QwenLM/qwen-code/pull/10800) | feat(ipc): keep the peer inbox reachable, and say so when it is not | Open |
| [#10842](https://github.com/QwenLM/qwen-code/pull/10842) | fix(release): stop one flaky test from failing a stable release | Closed |

## 5. Feature Request Trends
- **OpenTUI migration** – ongoing batched work to replace the ink 7 renderer.
- **Shell guard configurability** – operators want visibility, auditability, and override ability for daemon shell guards.
- **Skill command organization** – hide skill‑specific slash commands from the top‑level completion menu.
- **Session workflow DAG navigation** – clickable dependencies and better panning/zooming.
- **Worktree isolation for named tasks** – opt‑in Git worktree isolation per channel task.
- **Relaxed daemon ownership** – allow daemons to mount a shared Conversations runtime instead of enforcing a single process‑global owner.

## 6. Developer Pain Points
- **CI instability** – repeated main‑branch CI failures and flaky tests blocking releases; community is adding retries, timeouts, and separate lanes for light jobs.
- **Daemon shell guard opacity** – the built‑in guard blocks git and non‑git commands outside the session directory without operator configuration or audit trails.
- **Content‑generation leaks** – several open bugs where XML tool calls, thinking blocks, and scaffolding tags leak into user‑visible output.
- **Performance regressions** – session workflow projections derived multiple times per render; MCP images bypass the read_file image budget and enter context at full resolution.
- **Test‑suite timeouts on shared ECS** – millisecond budgets and script‑test suites hit the shared pool’s time limits, prompting dedicated timeout ceilings and budget‑skipping helpers.

---
*Digest generated from GitHub data for 2026‑09‑03.*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / Codewhale Community Digest — 2026-09-03

## 1. Today's Highlights

The Codewhale v0.9.12 integration wave continues to land, with 15+ PRs merged or open today covering UX rebranding, provider-neutrality gates, plugin infrastructure, memory commands, and the per-session control socket. The most-visible change is the unified "whale" brand surface and the rename of the sidebar/rail to **workbar**, signaling a push toward a consistent fleet-first identity ahead of the 0.9.12 release.

---

## 2. Releases

**No new releases** published in the last 24 hours. The v0.9.12 milestone (#5573) remains the active integration target, with today's PRs feeding directly into the `fix/0912-ux-20260902` branch and related integration slices.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5573](https://github.com/Hmbown/CodeWhale/issues/5573) | v0.9.12 milestone tracker | The single source of truth for the current release. Lists operator handoff docs, working branch, and all gated slices. 23 comments show active coordination. |
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | EPIC-005: Crate Decomposition (Umbrella) | Tracks the full structural split of the monolithic TUI crate. 21 comments indicate sustained community interest in maintainability. |
| [#5588](https://github.com/Hmbown/CodeWhale/issues/5588) | Provider neutrality: 18 DeepSeek-exclusive gates | Audited 2,281 lines across 279 files; 18 suspect gates found and fixed. Critical for multi-provider support. **Closed** via PR #5832. |
| [#5586](https://github.com/Hmbown/CodeWhale/issues/5586) | Decompose mega files (lib.rs 18.7k, config.rs 12.3k, client.rs 11.1k) | The pain point that drives EPIC-005. Users report these files cause merge conflicts and slow iteration. |
| [#5533](https://github.com/Hmbown/CodeWhale/issues/5533) | Control surface for supervised operation | Per-session control socket (`message / interrupt / relaunch / status`) over a Unix JSON-RPC socket. Enables CI/automation harnesses. **Closed** via PR #5831. |
| [#5268](https://github.com/Hmbown/CodeWhale/issues/5268) | Mid-turn control (queue / send-now / Esc-keep-draft) | Addresses the "locked chat bubble" feeling when steering an active turn. Community has requested clearer queue-vs-cancel semantics. |
| [#5637](https://github.com/Hmbown/CodeWhale/issues/5637) | Scope MCP secret providers to owning runtime | Embedded hosts need per-runtime credential scoping instead of process-wide env mutation. Security-relevant for multi-tenant setups. |
| [#5575](https://github.com/Hmbown/CodeWhale/issues/5575) | Fleet/subagent role posture has no single source of truth | Role definitions drifted across 5+ locations; the verifier contradiction in #5562 was a symptom. Needs centralization. |
| [#5820](https://github.com/Hmbown/CodeWhale/issues/5820) | Ollama: input budget collapses to 1024 tokens on 32K models | Default output reservation of 64K clamps the input window. Reported by a Windows user; blocks local-model workflows. |
| [#5824](https://github.com/Hmbown/CodeWhale/issues/5824) | Lane TTL cleanup can recursively delete unverified paths | Destructive failure mode: `remove_dir_all` runs without verifying the path is a managed worktree. **Closed** via PR #5854 with a verification gate. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5862](https://github.com/Hmbown/CodeWhale/pull/5862) | Codewhale 0.9.12: Fleet-only UX | Open | Integrates 10 UX slices: hover contract, workbar rename, startup flow, underwater default, provider/settings regroup, logo, roles, retro theme. |
| [#5861](https://github.com/Hmbown/CodeWhale/pull/5861) | Serve the canonical whale on account-entry pages | Open | Fixes sign-in/sign-up rendering a different whale mark than the rest of the product. Brand consistency fix. |
| [#5858](https://github.com/Hmbown/CodeWhale/pull/5858) | Collapse `ocean_treatment` into `ThemeId::Underwater` | Open | 11 commits unifying the ocean/deep-sea theme pipeline into a single picker and theme ID. |
| [#5843](https://github.com/Hmbown/CodeWhale/pull/5843) | Align typed config and schema with live value spaces | Open | Drops orphaned locale keys; typed theme carries custom themes. Dead-code budget at 425. |
| [#5854](https://github.com/Hmbown/CodeWhale/pull/5854) | Require verified managed-worktree identity before TTL cleanup | **Closed** | Fixes #5824. Adds a verification gate before `remove_dir_all` in lane TTL cleanup. |
| [#5857](https://github.com/Hmbown/CodeWhale/pull/5857) | Thinking fold toggles relative to expanded baseline | Open | Truth-table fix for fold behavior; keyboard inline-expand follows in a separate half. |
| [#5844](https://github.com/Hmbown/CodeWhale/pull/5844) | Delete `AppMode` pretenders and `VerifierVerdictPolicy` | **Closed** | Removes `AppMode::Auto`, finishes YOLO as a parse alias, deletes obsolete harness profile schema. |
| [#5833](https://github.com/Hmbown/CodeWhale/pull/5833) | FEAT-019 memory capability + typed outcomes | **Closed** | Re-lands memory commands (`search, remember, get, export, reindex, delete`) with a TUI adapter and `CommandCapabilities::MEMORY` bit. |
| [#5855](https://github.com/Hmbown/CodeWhale/pull/5855) | Computer-use bundle: screenshot, click, type over MCP | Open | First independent plugin on the bundle boundary. 9/9 server protocol tests pass; live 1920px JPEG screenshot verified on macOS. |
| [#5842](https://github.com/Hmbown/CodeWhale/pull/5842) | Plugin + marketplace management over `/v1/apps` | Open | Engine-side API for the gated local plugin system. App-side PR follows separately. |

---

## 5. Feature Request Trends

1. **Provider neutrality** — Multiple issues (#5588, #5443) and PRs converge on removing DeepSeek-specific gating, retiring legacy env aliases (`DEEPSEEK_YOLO`), and making the TUI a true multi-provider surface.
2. **Structured code intelligence** — Issues #3980, #3975, #3981, #3358 all request AST-backed search, LSP rename/code actions, a debugger protocol, and Playwright browser automation. The community wants the agent to reason at the structural level, not just text.
3. **Fleet / sub-agent observability** — Issues #5479, #5271, #5575 push for a persistent agents rail, session peek without full attach, and a single source of truth for role posture. Multi-agent workflows are a clear growth area.
4. **Supervised & automated operation** — The control socket (#5533), mid-turn queue semantics (#5268), and skill self-learning (#5860) all point to users running Codewhale in CI/harness contexts and wanting finer-grained human-in-the-loop controls.
5. **Local-model support** — The Ollama budget bug (#5820) and MCP secret scoping (#5637) reflect growing local-first usage that needs different defaults and security models.

---

## 6. Developer Pain Points

- **Mega files** (#5586, #5316): The 10k–18k line `lib.rs`, `config.rs`, `client.rs`, and `runtime_threads.rs` are the top structural complaint. They cause painful diffs, slow compilation awareness, and block feature work. The decomposition epic is the community's most-upvoted maintainability effort.
- **Legacy identifier drift** (#5443, #5575): `DEEPSEEK_*` env vars and role-posture definitions exist in 5+ places with inconsistent naming. The tiered migration (#5443) is the remediation, but cleanup is ongoing.
- **Setup wizard bloat** (#3954): The 3,847-line `setup/mod.rs` is a catch-all for runtime presets, constitution drafting, credential entry, and persistence. Users and contributors find it hard to navigate.
- **Destructive cleanup paths** (#5824): Lane TTL cleanup previously ran `remove_dir_all` without verifying worktree ownership. The fix (PR #5854) adds a gate, but the incident highlights a broader concern around destructive operations lacking safety checks.
- **Local-model token budget miscalculation** (#5820): The hardcoded 64K output reservation silently crushes input windows on 32K local models. Suggests the config layer needs model-aware budget arithmetic rather than a single global default.
- **Copy/UI consistency** (#5861, #5859): Brand assets and English copy were drifting across surfaces (account pages, launch, pickers). The 0.9.12 UX wave is addressing this, but it signals a recurring maintenance gap.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*