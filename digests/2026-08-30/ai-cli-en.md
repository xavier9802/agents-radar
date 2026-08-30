# AI CLI Tools Community Digest 2026-08-30

> Generated: 2026-08-30 04:56 UTC | Tools covered: 10

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



# Cross-Tool Comparison Report: AI CLI Ecosystem
**Date: 2026-08-30**

---

## 1. Ecosystem Overview

The AI CLI tool ecosystem is entering a phase of aggressive feature convergence and stability maturation. Eight major tools competed for developer attention today, with OpenAI Codex and Claude Code leading in issue volume and community engagement, while Gemini CLI and Kimi Code show rapid iteration cycles via nightly builds. The dominant theme across all communities is **agent reliability**—subagent failures, session persistence, and tool-calling correctness are the top pain points. Two tools (Grok Build, DeepSeek TUI) showed minimal or pre-release activity, while OpenCode and Pi demonstrated strong technical momentum with multiple merged PRs. Platform stability, particularly Windows desktop reliability, remains the most widespread frustration across Claude Code, Codex, and Copilot CLI.

---

## 2. Activity Comparison

| Tool | Hot Issues | PRs (24h) | Releases (24h) | Release Status |
|------|-----------|-----------|----------------|----------------|
| **Claude Code** | 10 | 1 | None | Stable (no patch) |
| **OpenAI Codex** | 10 | 7 | v0.151.0, v0.152.0-alpha.1 | Active release cycle |
| **Gemini CLI** | 10 | 10 | v0.59.0-nightly | Nightly cadence |
| **GitHub Copilot CLI** | 10 | 2 | v1.0.82 | Post-release regression wave |
| **Kimi Code** | 1 | 0 | None | Quiet/stable |
| **OpenCode** | 10 | 10 | None | Active fix cycle |
| **Pi** | 10 | 11 | None | Feature-heavy iteration |
| **Qwen Code** | 10 | 10 | None | Multi-agent focus |
| **DeepSeek TUI** | 7 | ~9 | None (v0.9.12 RC) | Pre-release preparation |
| **Grok Build** | — | — | — | Inactive |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|-----------|---------------|---------------|
| **Session recovery & persistence** | Codex (#40779), DeepSeek TUI (#5715), Copilot CLI (#4664), Pi (#8232) | Users lose work on crash/force-quit; JSONL on disk but model cannot see it. Cross-tool demand for durable session state. |
| **Multi-agent / agent orchestration** | Qwen Code (#8724, #8172), Gemini CLI (#22323, #21409), OpenCode (#41249), Pi (hooks dispatch) | Subagent reliability, inter-session messaging, and ghost-member cleanup are universal concerns. |
| **MCP server integration & OAuth** | Copilot CLI (#4660, #4662), OpenCode (subprocess sharing), Gemini CLI (SSRF fixes), Qwen Code (llama.cpp grammar errors) | Enterprise OAuth issuer compatibility, subprocess deduplication, and local server grammar compliance are pain points. |
| **Cross-platform WSL / Windows parity** | Codex (#29639, #41290), Copilot CLI (#4165), Claude Code (#80444, #85199), OpenCode (#25668) | Windows is the most fragmented platform. WSL path mapping, sandbox ACLs, and headless startup hangs recur across tools. |
| **Context management & compaction** | Codex (#34971, #35355), Copilot CLI (#4663), Pi (#8061), Qwen Code (#8172) | Unbounded retries, context bloat, and incorrect compaction state are systemic issues affecting cost and reliability. |
| **Third-party provider flexibility** | DeepSeek TUI (#5725, #5350), Pi (#8844), Gemini CLI, OpenCode | Demand for pre-built templates, BYOK gateways, and non-native model support (Concentrate, Tencent, Moonshot). |
| **Tool-calling correctness** | Gemini CLI (#22323), Copilot CLI (#4027), Claude Code (#87971, #88041), Qwen Code (#10352) | Silent failures, wrong tool selection (bash vs Edit/Write), and missing tool registration erode trust. |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi Code |
|-----------|-------------|--------------|------------|-------------|----------|-----|-----------|--------------|-----------|
| **Primary focus** | Desktop UX + auto-mode tooling | General-purpose agent with browser use | Subagent framework + auto-memory | GitHub/ADO enterprise workflows | Open-source extensibility + plugins | Multimodal + provider diversity | Multi-agent teams + structured memory | Rust-based TUI + sandboxing | Lightweight CLI + caching |
| **Target user** | Individual developers, desktop-first | Power users, Windows desktop | Enterprise agent workflows | GitHub-connected teams | Plugin ecosystem builders | researchers, open-weight model users | Teams, Java/enterprise | Rust ecosystem, CI/CD | Cost-conscious subscribers |
| **Technical approach** | Electron/MSIX desktop, hardcoded system prompts | Rust CLI + TS extension layer | Go, hook-based subagent lifecycle | TypeScript, OAuth/WAM-centric | Go, plugin-first architecture | TypeScript, hook + RPC model | Rust, tree-structured recall | Rust, crate decomposition | Caching-focused billing model |
| **Release cadence** | Sporadic patches | Daily alpha → stable | Nightly builds | Bi-weekly minor versions | PR-driven, no fixed schedule | Weekly feature merges | Bi-weekly with roadmap | Pre-release RC (v0.9.12) | Minimal releases |
| **Platform strength** | macOS (TUI parity improving) | Windows Desktop | Cross-platform | GitHub ecosystem | macOS/Linux focus | All platforms | Cross-platform | Cross-platform | Growing |
| **Notable differentiator** | Hardcoded `bashFirst` steering (controversial) | Vim motions merged (#41586), WSL parity push | Subagent reliability P1 focus | OAuth issuer URL flexibility | MCP subprocess deduplication | Tencent/Concentrate provider support | Structured on-demand recall (#10183) | Sandbox `NoNewPrivs` opt-out demand | Cache-read billing anomaly |

---

## 5. Community Momentum & Maturity

| Signal | Leader | Runner-up | Late Mover |
|--------|--------|-----------|------------|
| **Issue volume (engagement)** | Claude Code (78+ comments on GPU crash), Codex (28 on phone auth) | Gemini CLI, Qwen Code | Kimi Code (1 issue) |
| **PR velocity** | Pi (11 PRs), Gemini CLI (10), OpenCode (10) | Qwen Code (10), Codex (7) | Copilot CLI (2), Kimi Code (0) |
| **Release activity** | Codex (3 releases: stable + 2 alphas) | Gemini CLI (nightly) | Grok Build (none), Kimi Code (none) |
| **Cross-tool maturity indicator** | Claude Code and Codex show the most mature (and most stressed) communities—high issue counts reflect high adoption. Gemini CLI and OpenCode show strong engineering velocity. DeepSeek TUI is in pre-release and building foundations. Kimi Code and Grok Build show minimal community pressure, suggesting either small user bases or early-stage products. |

**Rapidly iterating:** Gemini CLI (nightly), Codex (alpha cadence), OpenCode (multi-PR fix bursts)
**Mature but stressed:** Claude Code (high engagement, regression-heavy), Copilot CLI (post-release regression wave)
**Building foundation:** DeepSeek TUI (v0.9.12 prep, crate decomposition)
**Low activity:** Kimi Code, Grok Build

---

## 6. Trend Signals

| Trend | Evidence | Developer Implication |
|-------|----------|----------------------|
| **Subagent reliability is the #1 trust barrier** | Gemini CLI P1 hangs (#21409) and false-success reporting (#22323); Qwen Code ghost members (#10208); Copilot CLI unbounded retry loops (#4663) | Tools that solve subagent observability and failure signaling will win enterprise adoption. |
| **Windows desktop is the weakest link** | GPU crashes (Claude Code #80444), WSL path mapping (Codex #29639), headless hangs (Copilot #4165), plugin loading freezes (OpenCode #25668) | Any tool shipping a Windows desktop client should prioritize sandbox, path, and crash-recovery stability over new features. |
| **MCP integration is table stakes—but broken everywhere** | Grammar errors (Qwen Code #10520), OAuth issuer failures (Copilot #4662), subprocess explosion (OpenCode), SSRF gaps (Gemini) | MCP compatibility testing across local servers (llama.cpp, Ollama) and enterprise OAuth providers should be a core QA gate. |
| **Context compaction correctness is underinvested** | Codex reprocesses cached context (#34971), Copilot retries compaction unboundedly (#4663), Pi reserves no output tokens (#8061) | Tools that get compaction right (correct state, bounded retries, output reservation) will have a cost and latency advantage. |
| **Provider diversification is accelerating** | Pi added Tencent Token Plan (#8844), DeepSeek TUI added Concentrate (#5725) and Moonshot/Kimi search (#5720), OpenCode routes GLM-5.2 (#34598) | Multi-provider support is no longer a differentiator—it's expected. Tools that make third-party provider onboarding frictionless will attract enterprise users. |
| **Session durability matters more than session features** | Lost conversations despite on-disk JSONL (Codex #40779), crash-invisible context (DeepSeek #5715), OOM on resume (Copilot #4664) | Invest in session recovery, not just session creation. This is a recurring trust failure across all tools. |
| **Auto-mode tool steering is a landmine** | Claude Code's hardcoded `bashFirst` prompt overrides `CLAUDE.md` (#88041, #90450), regressed twice (#89731) | Any tool with auto-mode must make tool-steering policies transparent, configurable, and resistant to silent overrides. |

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-30**

---

## 1. Top Skills Ranking

| # | Skill | Functionality | Discussion Highlights | Status |
|---|-------|--------------|----------------------|--------|
| 1 | **Hivemind** (PR #1628) | Multi-agent orchestration — delegates mechanical work to headless opencode workers on free models while Claude Code remains planner/reviewer | Addresses the high-cost-context problem; enables zero-cost parallel execution. | Open |
| 2 | **self-audit** (PR #1367) | Mechanical verification + four-dimension reasoning quality gate for AI output before delivery | Universal skill; checks file existence, then audits reasoning quality by damage-severity priority. | Open |
| 3 | **skill-quality-analyzer / skill-security-analyzer** (PR #83) | Meta-skills for evaluating Skill quality across five dimensions (structure, documentation, examples, functionality, security) | First quality-assurance tooling for the marketplace; 20% weight each on structure & docs. | Open |
| 4 | **frontend-design** (PR #210) | Frontend design guidance for Claude Code workflows | Revised for clarity and actionability — ensures instructions are followable within a single conversation. | Open |
| 5 | **scnet-hpc** (PR #1615) | HPC cluster operations for SCNet via profile-based SSH and Slurm workflows | Covers partition discovery, job generation, module management, and accelerator guidance. | Open |
| 6 | **testing-patterns** (PR #723) | Comprehensive testing skill covering unit tests, React component tests, testing philosophy (Testing Trophy), and edge cases | Broad coverage from AAA pattern to pure function testing. | Open |
| 7 | **ODT skill** (PR #486) | OpenDocument Format creation, template filling, and ODT→HTML conversion | Triggers on ODT/ODS/ODF/LibreOffice keywords; fills a gap alongside the existing DOCX skill. | Open |
| 8 | **document-typography** (PR #514) | Typographic quality control for generated documents — fixes orphan lines, widow paragraphs, numbering misalignment | Addresses a widespread but rarely-requested document quality issue. | Open |

---

## 2. Community Demand Trends

From community Issues, the most-discussed and most-anticipated Skill directions are:

- **Agent orchestration & cost optimization** — Issue #228 (org-wide skill sharing) and the Hivemind PR both reflect strong demand for cheaper, distributed agent execution and organizational skill distribution.
- **Output quality gates** — Issues #1385 and #1367 converge on the need for pre-delivery verification pipelines (mechanical checks → adversarial review → delivery confirmation).
- **Enterprise platform coverage** — Issue #568 (ServiceNow skill, 9 comments) and Issue #1175 (SharePoint security concerns) signal demand for enterprise platform Skills that are security-aware.
- **Skill developer tooling** — Issues #556 and #1390 reveal frustration with broken evaluation scripts (`run_eval.py`, `evaluation.py`); the community wants reliable CI for Skill quality.
- **Meta-skills & governance** — Issue #412 (agent-governance) and Issue #83 (quality/security analyzers) show demand for Skills that audit and govern other Skills and agents.
- **Platform accessibility** — Issues #29 (Bedrock), #16 (Skills as MCPs), and #189 (duplicate skills on install) indicate demand for broader deployment targets and cleaner distribution.

---

## 3. High-Potential Pending Skills

These active PRs are open but have strong community interest and may merge soon:

- **[PR #1628] Hivemind: Zero-Cost Multi-Agent Orchestration** — [GitHub](https://github.com/anthropics/skills/pull/1628) · Addresses the most pressing cost bottleneck in current Claude Code usage patterns.
- **[PR #1367] self-audit: Mechanical Verification + Reasoning Quality Gate** — [GitHub](https://github.com/anthropics/skills/pull/1367) · Fills a critical pre-delivery quality gap; universal applicability makes it marketplace-worthy.
- **[PR #1615] scnet-hpc** — [GitHub](https://github.com/anthropics/skills/pull/1615) · Niche but dedicated HPC user base; fills a gap for Linux cluster workflows.
- **[PR #723] testing-patterns** — [GitHub](https://github.com/anthropics/skills/pull/723) · Broadly applicable; complements existing frontend-design and code-review Skills.
- **[PR #486] ODT skill** — [GitHub](https://github.com/anthropics/skills/pull/486) · Completes the document-format coverage alongside the existing DOCX skill.
- **[PR #83] skill-quality-analyzer & skill-security-analyzer** — [GitHub](https://github.com/anthropics/skills/pull/83) · First-mover meta-tooling for the marketplace; high utility for all Skill authors.
- **[PR #514] document-typography** — [GitHub](https://github.com/anthropics/skills/pull/514) · Solves a ubiquitous pain point (orphan/widow lines) with minimal friction.

**Notable fixes also pending:**
- [PR #1298] `run_eval.py` 0% recall fix (Windows + trigger detection) — [GitHub](https://github.com/anthropics/skills/pull/1298)
- [PR #1099] Windows subprocess pipe crash fix — [GitHub](https://github.com/anthropics/skills/pull/1099)
- [PR #1050] Windows `claude.cmd` PATH issue — [GitHub](https://github.com/anthropics/skills/pull/1050)
- [PR #541] DOCX tracked-change bookmark collision fix — [GitHub](https://github.com/anthropics/skills/pull/541)

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **cost-efficient multi-agent orchestration and pre-delivery quality assurance** — users want to offload cheap mechanical work to free-tier workers while ensuring Claude Code's output is mechanically verified and reasoning-audited before it reaches them.

---



# Claude Code Community Digest — 2026-08-30

## Today's Highlights

Two major Windows desktop stability issues dominate the discussion: a fatal GPU-process crash (#80444, 78 comments) and a recurring "freeze-then-vanish" crash with no forensic trace (#89679), both leaving users unable to launch the app without repair. Meanwhile, the Auto-mode `bashFirst` steering controversy continues to draw community frustration, with four linked issues reporting that Claude is instructed to use `sed`/heredoc instead of native Edit/Write tools.

---

## Releases

No releases in the last 24 hours.

---

## Hot Issues

| # | Issue | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#80444](https://github.com/anthropics/claude-code/issues/80444) | **Desktop GPU-process crash on Windows (0x060C201E)** | 78 | 14 | Electron/Chrome 148 GPU renderer crash leaves the MSIX package in a non-launchable state (`appxState=2`) requiring manual Repair. Reproduced on two driver versions across RTX 2080 hardware. |
| [#85199](https://github.com/anthropics/claude-code/issues/85199) | **Desktop repeatedly crashes — requires "Repair" on Windows** | 40 | 6 | Related stability regression; users report a pattern of repeated crashes forcing manual MSIX repair cycles. |
| [#87971](https://github.com/anthropics/claude-code/issues/87971) | **Auto Mode abuses Bash tools for reads, writes, and edits** | 8 | 38 | Highest upvote count among open tooling issues. Claude in Auto Mode is systematically bypassing Edit/Write tools in favor of `cat`/`sed`/heredoc, producing fragile diffs and unexpected side effects. |
| [#88041](https://github.com/anthropics/claude-code/issues/88041) | **bashFirst system prompt hardcodes sed/heredoc instead of Edit/Write** | 13 | 26 | Root-cause issue behind #87971 — the instruction is embedded in the CLI binary, not user-configurable, and directly contradicts documented tool guidance. |
| [#9631](https://github.com/anthropics/claude-code/issues/9631) | **Add Microsoft Word (.docx) editing with track changes support** | 26 | 31 | Most-requested feature by engagement. Users need native docx read/write with track-changes awareness for collaborative document workflows. |
| [#65844](https://github.com/anthropics/claude-code/issues/65844) | **Fullscreen TUI Cmd+C intercepted — breaks macOS mouse copy** | 9 | 22 | TUI mode hijacks clipboard shortcuts on macOS, making basic copy operations impossible in fullscreen terminal sessions. |
| [#88093](https://github.com/anthropics/claude-code/issues/88093) | **Desktop window stuck always-on-top on Windows** | 11 | 19 | UX regression where the Claude Desktop window refuses to lose focus or minimize, blocking multi-app workflows. |
| [#89731](https://github.com/anthropics/claude-code/issues/89731) | **Auto-mode Bash-first steering reverses 2.1.21 and 2.1.31 fixes** | 3 | 3 | A regression-in-reverse: earlier patches (#87575, #87971) fixed the bash-first behavior, but a subsequent auto-mode update reintroduced it. No documented opt-out exists. |
| [#90450](https://github.com/anthropics/claude-code/issues/90450) | **Bash-first instruction silently disables nested CLAUDE.md and path-scoped rules** | 2 | 1 | The hardcoded bash-first prompt not only changes tool behavior but also suppresses per-directory customization, breaking project-level agent configuration. |
| [#87440](https://github.com/anthropics/claude-code/issues/87440) | **Model selection reverts to Fable 5 mid-session** | 1 | 0 | In Desktop/Cowork, switching models mid-session silently falls back to Fable 5 until the app is restarted, causing unexpected extra-credit spend. |

---

## Key PR Progress

| # | PR | Author | Description |
|---|----|--------|-------------|
| [#61720](https://github.com/anthropics/claude-code/pull/61720) | **Add troubleshooting for Cowork queue not spawning follow-up turn** | @giruuuuj | Documents root cause (race between queue post-turn handler and rate-limit handler) and provides a workaround entry for a bug first reported in #61718. Closes #61718. |

*Note: Only 1 PR was updated in the last 24 hours. The digest team will continue tracking PR activity as more merges land.*

---

## Feature Request Trends

1. **Rich document format support** — #9631 (Word/docx with track changes) and prior requests for spreadsheet and presentation editing signal sustained demand for non-code document workflows.
2. **Desktop UX polish** — Collapsed sidebar showing active sessions (#83699), proper window focus behavior (#88093), and reliable crash recovery (#80444, #85199) indicate the desktop experience is a high-priority community concern.
3. **Tooling parity across platforms** — The removal of `Glob` and `Grep` as standalone tools in native macOS/Linux builds (#69849, #51781, #61845) has created confusion; users want consistent tool catalogs regardless of platform.
4. **Browser extension integration** — #90257 highlights interest in bidirectional Claude Code ↔ Chrome extension session sharing.
5. **Scheduled/unattended task reliability** — Multiple issues (#89639, #89632) around scheduled tasks wedging or requesting interactive confirmation reveal a need for robust unattended execution modes.

---

## Developer Pain Points

- **Auto-mode tool-steering is unreliable and undocumented.** The `bashFirst` instruction is hardcoded in the CLI binary, overrides per-directory `CLAUDE.md` rules, and has regressed multiple times across versions. Users report fragile file edits via `sed`/heredoc instead of the stable Edit/Write tool chain. ([#88041](https://github.com/anthropics/claude-code/issues/88041), [#87971](https://github.com/anthropics/claude-code/issues/87971), [#89731](https://github.com/anthropics/claude-code/issues/89731), [#90450](https://github.com/anthropics/claude-code/issues/90450))

- **Windows desktop stability is a recurring crisis.** GPU crashes (#80444), freeze-then-vanish failures (#89679), stealth-update child-process leaks (#89599), and messages stuck in "Queued" state (#90637) point to systemic Electron/MSIX packaging issues on Windows.

- **Diagnosability gaps compound debugging time.** Context-limit errors and custom base URL misconfigurations send users in the wrong diagnostic direction (#82931), and scheduled tasks with interactive permission prompts break unattended workflows (#89632).

- **macOS clipboard and permission friction.** Fullscreen TUI intercepts Cmd+C (#65844), and keychain credential rewrites create infinite `SecurityAgent` prompt loops (#87348).

- **Background bash exit-code reporting is unreliable.** Backgrounded commands can report `exit code 0` even when the command actually failed (#90659), leading to silent data corruption in agent workflows.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-30

## 1. Today's Highlights

Codex CLI shipped **v0.151.0** with configurable MCP server grace periods and extension-level tool result inspection, while Windows Desktop faced a cluster of release-bug issues spanning WSL workspace paths, sandbox ACL failures, and headless startup hangs. The community's top concern remains authentication and session reliability, with the phone-verification bug accumulating the most engagement (28 comments).

## 2. Releases

- **rust-v0.151.0** — The latest stable CLI release. Notable additions: a configurable grace period for discovering tools from optional MCP servers (#41199), the ability for extensions to inspect or replace MCP tool results before they reach the model (#41202), and plugin catalog improvements that combine per-repository config with invalid-project-marketplace reporting.
- **rust-v0.152.0-alpha.1** — Alpha preview of the next release cycle.
- **rust-v0.151.0-alpha.7.2** — Additional alpha patch for the 0.151 line.

## 3. Hot Issues

| # | Title | Why It Matters | Reaction |
|---|-------|---------------|----------|
| [#25828](https://github.com/openai/codex/issues/25828) | Phone verification bug — unable to send codes to any number | Blocks login for users in regions like Indonesia; auth flow is fundamental and this has been open since June with 28 comments. | 👍 5 · 28 comments |
| [#29639](https://github.com/openai/codex/issues/29639) | Browser Use / Node REPL fails in Windows + WSL workspaces | Unmapped `sandboxCwd` breaks the bundled `node_repl` MCP server when the project lives on the WSL filesystem — a growing developer workflow. | 👍 3 · 16 comments |
| [#39280](https://github.com/openai/codex/issues/39280) | macOS Chrome extension claims tabs but real-page actions fail policy verification | Core browser-use capability is non-functional on macOS Desktop despite successful tab enumeration, pointing to a policy-layer regression. | 👍 4 · 13 comments |
| [#34971](https://github.com/openai/codex/issues/34971) | [Regression] Massive cached context reprocessed every turn in long sessions | Severe latency, timeouts, JSONL bloat, and excessive credit usage — a critical performance regression for power users on Windows. | 👍 0 · 11 comments |
| [#41290](https://github.com/openai/codex/issues/41290) | Project creation/removal fails after switching Agent Environment to WSL | Directly blocks WSL-based development workflows on Windows Desktop (build 26.825.31414). | 👍 3 · 10 comments |
| [#41241](https://github.com/openai/codex/issues/41241) | Local tool host exits during handshake after update | Multiple users report the code-mode host crashing post-update, breaking all tool calls. | 👍 0 · 9 comments |
| [#36087](https://github.com/openai/codex/issues/36087) | Windows sandbox fails with `helper_unknown_error: apply deny-read ACLs` | Intermittent sandbox init failures on Windows 11 Pro suggest a permissions-edge-case regression in Desktop. | 👍 1 · 9 comments |
| [#41540](https://github.com/openai/codex/issues/41540) | Headless startup after Store auto-update (0x80071770) | MSIX relocation failure blocks the app from launching a UI for ~12 minutes, effectively a denial-of-service on update. | 👍 0 · 7 comments |
| [#35355](https://github.com/openai/codex/issues/35355) | Compaction promotes partial output from interrupted commands into confirmed state | A correctness/safety issue where ephemeral command output can be treated as durable task state — relevant to all long-running sessions. | 👍 0 · 6 comments |
| [#41433](https://github.com/openai/codex/issues/41433) | GitHub connector queries invalid `Repository.fullDatabaseId` | The `mark_pull_request_ready_for_review` operation fails with a GraphQL schema error, blocking a key Work feature. | 👍 5 · 3 comments |

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#41586](https://github.com/openai/codex/pull/41586) | Add Vim search motions to the composer | Draft-local forward/backward literal search (`/`, `?`) with wrapped repeat navigation (`n`, `N`); supports motions after delete, change, and yank operators. |
| [#41570](https://github.com/openai/codex/pull/41570) | Fix proactive multi-agent instruction grammar | Corrects grammar in multi-agent instruction handling. |
| [#41569](https://github.com/openai/codex/pull/41569) | Harden diagnostic report uploads | Sends core report event before attachments, uploads each attachment in a separate gzip-compressed envelope, and truncates oversized payloads with format-aware handling. |
| [#41567](https://github.com/openai/codex/pull/41567) | Restore thread cwd from owned settings snapshots | Resuming a thread without an explicit `cwd` now restores that thread's latest retained setting, fixing stale-cwd bugs across forked and compacted history. |
| [#41562](https://github.com/openai/codex/pull/41562) | Preserve turn lineage across goal continuations | Automatic goal continuations now remain attributable to the originating turn, preventing stale lineage metadata after external input or goal edits. |
| [#41477](https://github.com/openai/codex/pull/41477) | Organize bundled Rust resources under asset directories | Separates embedded runtime resources from source files and test fixtures in `core` and `tui` Bazel targets. |
| [#41476](https://github.com/openai/codex/pull/41476) | Use rules_rs platforms for release binaries | Maps each release platform to its Rust target triple and builds multiplatform binaries against `rules_rs` platforms instead of LLVM definitions. |

## 5. Feature Request Trends

- **External/async event injection into live sessions** — Users want webhooks, file-watcher signals, and incoming messages to wake and inject turns into an active visible session, not just headless remote-control threads ([#33556](https://github.com/openai/codex/issues/33556), 👍 5).
- **Session recovery and reindex tools** — Multiple Windows users report conversations disappearing from the UI while JSONL files persist on disk; a first-party recovery/reindex tool is requested ([#40779](https://github.com/openai/codex/issues/40779), [#35804](https://github.com/openai/codex/issues/35804)).
- **Cross-platform WSL / sandbox parity** — Strong demand for consistent behavior when Windows Desktop runs agents in WSL, including proper cwd mapping, project lifecycle, and sandbox ACL handling ([#29639](https://github.com/openai/codex/issues/29639), [#41290](https://github.com/openai/codex/issues/41290), [#36087](https://github.com/openai/codex/issues/36087)).
- **Vim-style navigation in the composer** — The merged PR (#41586) reflects sustained community interest in power-user editing gestures.

## 6. Developer Pain Points

1. **Windows Desktop reliability regressions** — A disproportionate cluster of high-comment issues (#29639, #34971, #41290, #41241, #36087, #41540, #41255, #40913, #41093, #41539) point to release-quality gaps in the Windows build, covering sandbox ACLs, tool-host handshakes, headless startup hangs, and memory bloat (#41240 — 5+ GB in minutes).
2. **Authentication and session persistence** — Phone verification is completely broken for some regions (#25828), and lost conversations despite on-disk JSONL files (#40779, #35804) erode trust in session continuity.
3. **Browser-use on macOS** — The Chrome extension can enumerate tabs but policy verification rejects every real-page action (#39280), rendering the feature unusable on macOS Desktop.
4. **Context compaction and performance** — Reprocessing massive cached context in long sessions (#34971) and compaction promoting ephemeral output as confirmed state (#35355) are correctness and cost concerns for power users.
5. **GitHub connector schema drift** — Invalid `fullDatabaseId` queries (#41433) suggest the connector is out of sync with GitHub's GraphQL schema, blocking PR workflow automation.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-30

---

## 1. Today's Highlights

A new nightly build (**v0.59.0-nightly.20260830**) has been released. The community is actively addressing subagent reliability issues, notably a P1 bug where subagents report false `GOAL` success after hitting turn limits, and another where the generalist agent hangs indefinitely. Several fixes landed today for hook migration bugs and terminal scrollback behavior.

---

## 2. Releases

**v0.59.0-nightly.20260830.g0bd1d4397**
Automated nightly bump. Changelog: [v0.59.0-nightly.20260829 → v0.59.0-nightly.20260830](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260829.g0bd1d4397...v0.59.0-nightly.20260830.g0bd1d4397)

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports GOAL success after MAX_TURNS | Critical reliability bug — subagents silently report success when they actually hit turn limits, hiding failures from users. | 13 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | P1 blocker for agent-based workflows; simple tasks like folder creation can hang for hours. | 8 comments, 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & bash affinity | Proposes leveraging Gemini's native bash capabilities securely — a significant architectural enhancement for agent tooling. | 8 comments, 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads and search | Epic tracking whether AST-aware tools can reduce token waste and misaligned reads — high impact on efficiency. | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini underuses skills and sub-agents | Users report custom skills are ignored unless explicitly prompted, undermining the agent framework's value. | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions | Bug where low-value sessions are never marked processed, causing infinite retry loops in the memory system. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Security concern: sensitive content reaches the model before redaction occurs in background extraction. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell execution stuck on "Waiting input" | P1 bug where completed commands still show as awaiting input, blocking subsequent operations. | 4 comments, 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent session takeover & lock recovery | Feature request to make the browser agent resilient to orphaned processes and locked profiles. | 4 comments |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | P1 bug specific to Wayland users — browser agent terminates with GOAL despite failure. | 4 comments, 1 👍 |

---

## 4. Key PR Progress

| # | PR | Type | Summary |
|---|-----|------|---------|
| [#29125](https://github.com/google-gemini/gemini-cli/pull/29125) | fix(cli): hook timeout units | Bug fix | Fixes hook migration incorrectly interpreting timeout values as milliseconds instead of seconds (matching Claude Code's behavior). |
| [#29124](https://github.com/google-gemini/gemini-cli/pull/29124) | fix(cli): SubagentStop event key | Bug fix | Corrects `SubAgentStop` → `SubagentStop` in the hooks migration event mapping; hooks were silently dropped. |
| [#29110](https://github.com/google-gemini/gemini-cli/pull/29110) | fix(core): route read_file through FileSystemService | Bug fix | Ensures `read_file` respects injected `FileSystemService` (e.g., ACP remoted fs), aligning it with `write_file` and `replace`. |
| [#28827](https://github.com/google-gemini/gemini-cli/pull/28827) | fix(core): 401 false authentication errors | Bug fix | Prevents unrelated strings containing "401" from being misidentified as auth failures. [Closed] |
| [#28828](https://github.com/google-gemini/gemini-cli/pull/28828) | fix(core): warn on preview model substitution | Bug fix | Now warns users when their requested preview model is silently downgraded to `auto-gemini-2.5` due to missing entitlements. [Closed] |
| [#28823](https://github.com/google-gemini/gemini-cli/pull/28823) | Feat/evals: tracker relationships error recovery | Feature | Adds behavioral evals for task graph dependency/visualization error recovery and shell command failure recovery. [Closed] |
| [#28824](https://github.com/google-gemini/gemini-cli/pull/28824) | Feat/evals: multi-tool chain & security bounds | Feature | Adds evals for multi-tool chain workflows, large-file context safety, and sensitive-file access enforcement. [Closed] |
| [#28968](https://github.com/google-gemini/gemini-cli/pull/28968) | fix(core): dedupe symlinked skill dirs | Bug fix | Fixes duplicate skill discovery when `.gemini` is symlinked/junctioned to `.agents` per the open Agent Skills standard. |
| [#28967](https://github.com/google-gemini/gemini-cli/pull/28967) | fix(cli): prevent scrollback clear on refresh | Bug fix | Stops `refreshStatic()` from clearing terminal scrollback on Linux/Unix emulators during static UI updates. |
| [#29120](https://github.com/google-gemini/gemini-cli/pull/29120) | fix(core): web fetch destination validation | Security | Improves `WebFetchTool` with async DNS validation and Undici-based connection routing to prevent SSRF-style misuse. |

---

## 5. Feature Request Trends

- **Subagent reliability & observability**: Multiple requests for better subagent recovery, trajectory visibility (`/chat share` — [#22598](https://github.com/google-gemini/gemini-cli/issues/22598)), and bug report context inclusion ([#21763](https://github.com/google-gemini/gemini-cli/issues/21763)).
- **AST-aware tooling**: Investigation into AST-based file reads and codebase mapping to reduce token waste and improve navigation precision ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)).
- **Persistent task tracking**: Push to replace in-context `WriteToDo` with file-based CRUD task tracking to avoid context rot ([#18836](https://github.com/google-gemini/gemini-cli/issues/18836), [#21000](https://github.com/google-gemini/gemini-cli/issues/21000)).
- **Security hardening**: Requests for deterministic secret redaction ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)), destructive-action guardrails ([#22672](https://github.com/google-gemini/gemini-cli/issues/22672)), and token-frugal "tactful" file reads ([#19561](https://github.com/google-gemini/gemini-cli/issues/19561)).
- **Agent self-awareness**: Users want the CLI to understand and accurately report its own flags, hotkeys, and mechanics ([#21432](https://github.com/google-gemini/gemini-cli/issues/21432)).

---

## 6. Developer Pain Points

- **Subagent silence on failure**: Subagents reporting `GOAL` success when they actually exhausted turns ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323)) or hung indefinitely ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409)) erode trust in agent-driven workflows.
- **Shell command stalls**: Commands completing but leaving the CLI stuck in "Waiting input" state ([#25166](https://github.com/google-gemini/gemini-cli/issues/25166)) and interactive prompts freezing the agent ([#22465](https://github.com/google-gemini/gemini-cli/issues/22465)).
- **Tool limit errors**: 400 errors triggered when more than 128–400 tools are available, with no smart scoping ([#24246](https://github.com/google-gemini/gemini-cli/issues/24246)).
- **Browser agent fragility**: Failures on Wayland ([#21983](https://github.com/google-gemini/gemini-cli/issues/21983)) and inability to recover from locked/orphaned profiles ([#22232](https://github.com/google-gemini/gemini-cli/issues/22232)).
- **Hook migration bugs**: Incorrect event key spelling and timeout unit mismatches when migrating from Claude Code configs ([#29125](https://github.com/google-gemini/gemini-cli/pull/29125), [#29124](https://github.com/google-gemini/gemini-cli/pull/29124)).
- **Auto Memory quirks**: Low-signal sessions retried indefinitely ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522)), invalid patches silently skipped ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)), and privacy concerns around unredacted transcript logging ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)).
- **Tmp script clutter**: Model-generated scripts scattered across directories, creating cleanup overhead ([#23571](https://github.com/google-gemini/gemini-cli/issues/23571)).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-30

## 1. Today's Highlights

GitHub Copilot CLI v1.0.82 was released yesterday, delivering key UX fixes including robust worktree/move transitions, Ctrl+E plan-card expansion, and richer authentication failure diagnostics. The community is actively reporting post-release regressions, notably a chroma-mcp compatibility break in v1.0.81 and a WAM/OAuth failure for Azure DevOps remote MCP servers in v1.0.81.

---

## 2. Releases

### v1.0.82 (2026-08-29)
- **Worktree resilience** — Messages typed while `/worktree` or `/move` is preparing the worktree no longer break the subsequent session switch.
- **Ctrl+E plan expansion** — Pressing Ctrl+E re-expands the plan approval card to show the full plan again.
- **Auth failure visibility** — Authentication failures (e.g., `401 Bad credentials`) now surface the specific error instead of only redirecting to `/login`.

> Full release: [github.com/github/copilot-cli](https://github.com/github/copilot-cli)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4027](https://github.com/github/copilot-cli/issues/4027) | Tool `str_replace` does not exist | Affects Java development workflows; Copilot silently falls back to an alternate tool but logs a confusing error. 13 👍. | 🔥 High — most upvoted issue in the window |
| [#4165](https://github.com/github/copilot-cli/issues/4165) | `copilot --resume` hangs on Windows | Blocks session continuity for Windows users; cold-start resume stalls at `Resuming session…` with no error. | Moderate — 1 👍, 4 comments |
| [#4660](https://github.com/github/copilot-cli/issues/4660) | Remote ADO MCP server OAuth fails in v1.0.81 WAM | Breaks enterprise Azure DevOps MCP integrations after a minor version bump. | New — reported 2026-08-29 |
| [#4647](https://github.com/github/copilot-cli/issues/4647) | v1.0.81 broke chroma-mcp compatibility | A regression from v1.0.80 → v1.0.81 that disables Chroma MCP server usage entirely. | New — reported 2026-08-28 |
| [#4664](https://github.com/github/copilot-cli/issues/4664) | OOM crash when resuming long sessions | Fatal V8 heap exhaustion prevents resumption of any large session, effectively data-loss for active work. | New — reported 2026-08-30 |
| [#4663](https://github.com/github/copilot-cli/issues/4663) | Failed compaction retried unboundedly on every turn | Each retry is a full billed model call with no backoff, causing runaway costs and context bloat. | New — reported 2026-08-30 |
| [#4662](https://github.com/github/copilot-cli/issues/4662) | AgentHost MCP client OAuth metadata discovery fails on issuer URLs with a path | Blocks OAuth-protected MCP servers whose issuer URL contains a path segment (e.g., `mcp.example.com/oauth`). | New — reported 2026-08-30 |
| [#4553](https://github.com/github/copilot-cli/issues/4553) | Infinite loop on JSON-wrapping error during `apply_patch` | Causes repeated failures and task stalls when modifying files; model retries identical payload. | Moderate — 0 👍, active since 2026-08-21 |
| [#2955](https://github.com/github/copilot-cli/issues/2955) | `/allow-all` does not suppress bash tool execution prompts | Permission bypass flag is ineffective, forcing repeated confirmations for shell tool calls. | Moderate — 1 👍, long-lived |
| [#4655](https://github.com/github/copilot-cli/issues/4655) | Custom agents under `com.github.copilot/agents` not discovered | Agent Plugins 1.0 creators cannot load custom agents, breaking a core plugin-extension path. | New — reported 2026-08-28 |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#2381](https://github.com/github/copilot-cli/pull/2381) | Install: add fish shell support for PATH configuration | **Closed** | Addresses the catch-all POSIX `export` in fish-shell profile detection, which was silently failing because fish does not source `~/.profile` and uses array-style PATH assignment. |
| [#4659](https://github.com/github/copilot-cli/pull/4659) | Initial commit with exported changes from codespace | **Open** | Import of externally contributed changes from a GitHub Codespace; awaiting review. |

> Only 2 PRs were active in the last 24h. No additional pull requests met the significance threshold for this digest.

---

## 5. Feature Request Trends

- **Expanded `.agents` discovery scope** — Issue [#4204](https://github.com/github/copilot-cli/issues/4204) requests extending the `.agents/` convention beyond Git repos to any opened folder, standardizing how instructions, agents, and hooks are loaded.
- **Agent Plugins 1.0 completeness** — Issue [#4655](https://github.com/github/copilot-cli/issues/4655) highlights gaps in custom-agent discovery, suggesting the plugin ecosystem needs more robust component registration.
- **Cross-platform session resumption** — Issue [#4165](https://github.com/github/copilot-cli/issues/4165) and [#4664](https://github.com/github/copilot-cli/issues/4664) together signal demand for reliable session lifecycle management across platforms, especially Windows.
- **OAuth / MCP interoperability** — Issues [#4660](https://github.com/github/copilot-cli/issues/4660) and [#4662](https://github.com/github/copilot-cli/issues/4662) reflect a trend of MCP server authors and enterprise users needing broader OAuth issuer URL and WAM compatibility.

---

## 6. Developer Pain Points

1. **Regression fragility** — Two distinct compatibility breakages (chroma-mcp in [#4647](https://github.com/github/copilot-cli/issues/4647) and ADO WAM OAuth in [#4660](https://github.com/github/copilot-cli/issues/4660)) surfaced shortly after v1.0.81, eroding trust in minor-version bumps for production MCP integrations.
2. **Silent retries with cost** — Issue [#4663](https://github.com/github/copilot-cli/issues/4663) describes unbounded, identical retry loops on compaction failures, burning credits and inflating context without any user-visible error or backoff.
3. **Session resumption instability** — Windows hangs ([#4165](https://github.com/github/copilot-cli/issues/4165)) and OOM crashes on large sessions ([#4664](https://github.com/github/copilot-cli/issues/4664)) make `--resume` unreliable, a critical path for daily workflow.
4. **Permission model bugs** — `/allow-all` ([#2955](https://github.com/github/copilot-cli/issues/2955)) failing to suppress shell prompts is a persistent frustration that undermines the permission-suppression workflow.
5. **Tool-existence errors** — The recurring `str_replace` tool-not-found message ([#4027](https://github.com/github/copilot-cli/issues/4027), 13 👍) indicates a gap in tool registration or fallback logic, particularly for Java workflows.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-30

## 1. Today's Highlights
The primary activity in the last 24 hours centers on an open billing‑anomaly report (Issue #2626), where a paying subscriber observed rapid quota depletion with zero cache‑creation events, suggesting a caching‑billing misconfiguration. No new releases or pull requests were published during this period.

## 2. Releases
No new versions were released in the last 24 hours.

## 3. Hot Issues
**[Issue #2626](https://github.com/MoonshotAI/kimi-cli/issues/2626) — Abnormal quota consumption: cache_read billed every turn with cache_creation always 0**  
*Why it matters:* The reporter (an annual‑plan subscriber) documented that approximately 40% of a 5‑hour quota window was consumed within minutes of light usage, with every turn incurring a `cache_read` charge while `cache_creation` remained at zero. This pattern indicates either a caching‑logic bug or a billing‑metering discrepancy that could lead to unexpectedly high costs for users relying on cache‑reduction features.  
*Community reaction:* The issue currently has one comment and no upvotes, but the severity of the billing anomaly and its direct impact on paying customers is likely to draw attention and demand a timely investigation from the Moonshot AI support team.

*(No other issues were reported in the last 24 hours.)*

## 4. Key PR Progress
No pull requests were updated in the last 24 hours.

*(No PRs were open or merged during this reporting window.)*

## 5. Feature Request Trends
From the active issue, the community’s most‑pressing feature directions are:
- **Transparent, real‑time quota‑consumption metrics** – users want clear visibility into how cache‑read vs. cache‑create charges are applied per session.
- **Reliable cache‑creation reporting** – a consistent indicator that caches are being populated (not just read) so subscribers can verify the cost‑saving benefit of caching.
- **Quota‑spike alerts** – proactive notifications when usage deviates from expected patterns, helping subscribers avoid surprise depletion.

## 6. Developer Pain Points
The recurring frustrations evident in the current issue are:
- **Unpredictable billing** – rapid quota loss with opaque per‑turn cost breakdowns.
- **Caching not delivering expected savings** – `cache_creation` remaining zero while `cache_read` charges accumulate undermines trust in the cache‑optimization feature.
- **Lack of immediate diagnostic feedback** – developers are forced to manually inspect CLI output and quota windows to identify anomalies, rather than receiving clear error or warning messages.

---  
*Digest generated from GitHub data for `github.com/MoonshotAI/kimi-cli` (last 24 hours).*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-30

## 1. Today's Highlights
No new releases were published in the last 24 hours. Community attention centers on billing/availability issues, model-configuration behavior in Xcode, and several performance fixes for large repositories and MCP subprocess management.

## 2. Releases
None in the last 24 hours.

## 3. Hot Issues
1. **#33264** [CLOSED] Credit card declined  
   *Why it matters:* Directly impacts subscription and usage. Closed after community discussion; still referenced by billing inquiries.  
   *Reaction:* 20 comments, 5 👍.

2. **#34743** [OPEN] opencode ACP from Xcode 27 beta 2 uses default model “big‑pickle” ignoring `opencode.json`  
   *Why it matters:* Breaks expected model‑selection behavior for users integrating opencode as an Xcode agent.  
   *Reaction:* 16 comments; high interest from macOS/Xcode users.

3. **#20235** [CLOSED] Request GitHub Copilot auto model routing API access + chat.model plugin hook  
   *Why it matters:* Would enable parity with VS Code’s Copilot routing and give plugin authors deeper control.  
   *Reaction:* 8 comments, **29 👍** — strongest engagement in the period.

4. **#34598** [CLOSED] opencode‑go GLM‑5.2 routes to Alibaba Cloud, which scans/filters user content with no ToS disclosure  
   *Why it matters:* Raises privacy and compliance concerns for enterprise users.  
   *Reaction:* 5 comments; highlighted data‑sovereignty issues.

5. **#25668** [CLOSED] Plugin loading intermittently hangs when `.git` directory exists (Windows)  
   *Why it matters:* Blocks startup for ~80% of Windows users in git‑tracked projects.  
   *Reaction:* 5 comments; frequent reproduction reports.

6. **#41249** [OPEN] Live Subagents sidebar section in the TUI  
   *Why it matters:* Extends the plugin ecosystem with a real‑time subagent view (already built as an external plugin).  
   *Reaction:* 6 comments; visible demand for enhanced session visibility.

7. **#27661** [CLOSED] Home/End keys in input box scroll message list instead of moving cursor  
   *Why it matters:* Degrades editing experience for long messages; affects all TUI users.  
   *Reaction:* 6 comments, 8 👍.

8. **#43477** [OPEN] Muse model fails with “Upstream request failed: Endpoint is unavailable”  
   *Why it matters:* Indicates provider‑side availability or routing problems for the Muse model.  
   *Reaction:* 4 comments; ongoing upstream errors.

9. **#46219** [OPEN] API inference blocked while authenticated model catalog remains accessible  
   *Why it matters:* New report of HTTP 401 `INFERENCE_ACCESS_BLOCKED` despite valid credentials and successful catalog fetch.  
   *Reaction:* 3 comments; early‑stage investigation.

10. **#24795** [CLOSED] Allow editing the “always” permission pattern before confirming  
    *Why it matters:* Improves permission‑management UX and reduces accidental broad approvals.  
    *Reaction:* 4 comments, 6 👍.

## 4. Key PR Progress
1. **#46214** [OPEN] fix(core): bound `ProjectCopy.refresh` concurrency and add no‑change fast path  
   *Fix:* Prevents process‑spawning explosion on large repositories by capping concurrent stat/git calls and skipping unchanged sources.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46214>

2. **#46211** [OPEN] fix(core): defer FFF initialization to avoid blocking cold location acquisition  
   *Fix:* Moves synchronous filesystem scan out of `Instance.layer` construction, eliminating 50+‑second freezes on monorepos.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46211>

3. **#46210** [OPEN] fix(mcp): share identical MCP subprocesses across Locations  
   *Fix:* Deduplicates MCP server processes per user‑global declaration, reducing subprocess multiplication (e.g., 5 locations × 3 servers → 3 processes).  
   *Link:* <https://github.com/anomalyco/opencode/pull/46210>

4. **#46218** [CLOSED] fix(ai): preserve forced reasoning signature  
   *Fix:* Maintains accumulated reasoning signature on `message_stop` and keeps route‑specific provider metadata for stateless continuation.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46218>

5. **#46215** [CLOSED] fix(app): recover sessions with unavailable locations  
   *Fix:* Brings unavailable‑location recovery flow to desktop/web session UI, showing saved transcript and recovery actions.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46215>

6. **#46193** [CLOSED] fix(ai): fail malformed converse output  
   *Fix:* Makes Bedrock Converse streams fail on `malformed_model_output`/`malformed_tool_use` instead of emitting a successful finish, surfacing raw error details.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46193>

7. **#46202** [CLOSED] fix(tui): scope reasoning‑effort variants to the agent, seed from agent config  
   *Fix:* Resolves regression where reasoning‑effort selection was stored per model instead of per agent, breaking variant pinning in agent frontmatter.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46202>

8. **#45235** [OPEN] fix(webfetch): apply timeout to body read and fail instead of dying  
   *Fix:* Extends `webfetch` timeout to cover body reading, preventing silent hangs when a server stalls after headers.  
   *Link:* <https://github.com/anomalyco/opencode/pull/45235>

9. **#46200** [OPEN] fix(app): inset iOS PWA navigation below native chrome  
   *Fix:* Adds safe‑area padding and landscape insets to keep the PWA shell below iOS navigation bars.  
   *Link:* <https://github.com/anomalyco/opencode/pull/46200>

10. **#41955** [CLOSED] feat(provider): add none reasoning variant for DeepSeek V4  
    *Fix/Feature:* Exposes a “none” thinking toggle for DeepSeek V4, allowing users to opt out of reasoning effort tiers.  
    *Link:* <https://github.com/anomalyco/opencode/pull/41955>

## 5. Feature Request Trends
- **Deeper provider/model routing control** – requests for Copilot‑style auto‑routing APIs, per‑agent reasoning‑effort pinning, and custom installation paths.
- **Plugin‑ecosystem visibility** – live subagent sidebar, parallel‑bash tool, and cross‑session error‑gate plugins (dejavu).
- **Session‑state and editing UX** – freshness polling, permission‑pattern editing, and TUI cursor‑key behavior.
- **Desktop/app polish** – close‑confirmation/minimize‑to‑tray, PWA safe‑area insets, and configurable plans directories.

## 6. Developer Pain Points
- **Startup hangs** – Windows plugin loading blocks in git directories; large‑repo FFF scans freeze cold starts.
- **Configuration being ignored** – model settings in `opencode.json` overridden by default picks

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑08‑30

## 1. Today’s Highlights
The Pi coding‑agent project delivered a major new browser‑based GUI (`pi web`) with full TUI parity and added a Tencent Token Plan provider, expanding offline and regional model access. The community is actively resolving Windows console‑child process detachment and TUI rendering glitches that affect long sessions, while a Mac performance regression remains open.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Hot Issues
| # | Title | Status | Engagement | Why it matters |
|---|-------|--------|------------|----------------|
| **#8584** | TUI row corruption during streaming: assistant text rendered one word per line after long tool output | OPEN | 25 comments · 9 👍 | Directly impacts readability of long agent conversations; high comment volume shows widespread impact. |
| **#7730** | High CPU usage on Mac OS with long session | OPEN | 13 comments · 9 👍 | Performance regression that can make Pi unusable on macOS; likely linked to context size or session length. |
| **#3200** | Support video/audio content in prompt command | OPEN | 10 comments · 6 👍 | Core multimodal request—extending `prompt` RPC to forward video/audio alongside images would enable Gemma 4, GPT‑4o, and other vision‑language models to accept full media. |
| **#8643** | Bedrock: OpenAI models reject images nested in toolResult.content | OPEN | 3 comments · 0 👍 | Bug where tool‑result images are not hoisted into sibling user blocks for OpenAI‑compatible Bedrock endpoints, breaking image‑aware tool loops. |
| **#8061** | Context budget ignores maxTokens output reservation: 400 at 78% input, overflow recovery retry fails too | OPEN | 3 comments · 2 👍 | Reliability issue—context‑budget calculations do not reserve space for output tokens, causing provider 400 errors and failed compaction retries. |
| **#8753** | 0.84.3 regression: reasoning_details echo deterministically degenerates Venice GLM reasoning | CLOSED | 3 comments · 0 👍 | Introduced a deterministic reasoning‑loop degeneration when `reasoning_details` were echoed back to Venice (GLM‑5‑3); now resolved. |
| **#8829** | wrapUIPromptContext copying by spread and lose ui prototype methods | CLOSED | 3 comments · 0 👍 | Spread‑based copy dropped prototype methods from class‑instance UIs; fix ensures custom UI implementations survive context wrapping. |
| **#8820** | omit tool_choice without tools, send tools: [] for xAI | CLOSED | 2 comments · 0 👍 | xAI 400ed when `tool_choice` was present without a `tools` array; now omitted or set to empty array, fixing compaction. |
| **#8751** | fix(tui): render markdown soft line breaks as spaces, not hard breaks | CLOSED | 2 comments · 1 👍 | Corrected CommonMark soft‑break rendering in TUI, eliminating visual noise in markdown output. |
| **#8846** | Windows: bash tool’s windowsHide:true detaches Git Bash from the console — native console children flash conhost windows | CLOSED | 1 comment · 0 👍 | `windowsHide:true` caused Git Bash to detach from the terminal, making every spawned console child (npm test, node) flash a black conhost window; now fixed. |

## 4. Key PR Progress
| # | Title | Status | Summary |
|---|-------|--------|---------|
| **#8844** | feat(ai): add Tencent Token Plan Individual provider | CLOSED | Adds a new provider for Tencent’s Token Plan endpoint, covering `tc‑code‑latest`, DeepSeek V4‑Flash/Pro, GLM‑5.2, and MiniMax‑M2.7 via `TENCENT_TOKEN_PLAN_API_KEY`. |
| **#8840** | feat: pi web GUI with full TUI parity | CLOSED | Introduces `pi web`, a browser‑based GUI that serves a static bundle over HTTP + WebSocket and delivers the same agent‑session, tool, and UI features as the TUI. |
| **#8262** | feat(coding‑agent): dispatch hooks on every turn‑start path (cancellable turn preflight) | OPEN | Fixes `sendCustomMessage(triggerTurn: true)` so it now fires the `input` and `before_agent_start` hooks, ensuring consistent extension lifecycle across all turn‑entry paths. |
| **#8828** | fix(tui): detect Zed terminal capabilities | OPEN | Adds capability detection for Zed (v1.17.2+), which uses Alacritty under the hood—enabling hyperlinks and true‑color support while documenting default hotkey bindings. |
| **#8112** | fix(coding‑agent): realpath extension entries before jiti import | OPEN | Resolves a pnpm‑isolated‑layout bug where jiti’s resolver did not realpath symlinks before resolving imports, causing extension loading failures. |
| **#8725** | fix(coding‑agent): settle active turn before in‑memory fork | CLOSED | Moves `teardownCurrent()` before the in‑memory session reset, preventing outgoing `toolResult` messages from landing in the replacement session and avoiding resource‑cleanup errors. |
| **#8297** | fix(coding‑agent): exclude superseded retry attempts from restored context | CLOSED | Records assistant‑entry IDs replaced by successful retries and excludes them from provider context, compaction input, token budgets, and branch summaries—improving context accuracy. |
| **#8818** | fix(ai): omit Responses tool_choice when no tools are sent | CLOSED | For xAI (Grok) compaction, now sends `tools: []` and omits `tool_choice` when the request has no immediate tools, eliminating the 400 error. |
| **#8819** | Fix project name from ‘pi’ to ‘Pi’ | CLOSED | Minor documentation/naming consistency fix across README and package metadata. |
| **#8232** | DONT MERGE: dev branch | OPEN | Internal CI/test branch—no user‑facing changes. |

## 5. Feature Request Trends
- **Multimodal input expansion** — Users increasingly want to feed video/audio alongside images to LLMs (`#3200`).
- **Isolated state profiles** — The `--profile` flag (`#3966`) and opt‑in `pi.namespace` for skills/templates (`#8834`) show demand for clean separation of work/personal/LLM setups.
- **Provider diversification** — New built‑in providers for Tencent Token Plan (`#8844`), Command Code (`#8836`), and DeepSeek `/responses` (`#7559`) indicate a trend toward regional/alternative endpoints.
- **Terminal/IDE compatibility** — Zed detection (`#8828`) and Windows console‑child handling (`#8846`) reflect ongoing effort to maintain parity across development environments.
- **Accessibility** — NVDA‑friendly output (`#8831`) and markdown‑rendering fixes (`#8751`) highlight a push toward screen‑reader and visual‑clarity improvements.

## 6.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-30

## 1. Today's Highlights

The community is focused on two critical bug waves: **MCP tool integration failures with llama.cpp** (threshold and grammar parsing issues) and **Windows Computer Use SDK crashes** on embedded runtime creation. Meanwhile, several PRs advancing Agent Team reliability, session lifecycle management, and workflow visibility are nearing merge.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#5975](https://github.com/QwenLM/qwen-code/issues/5975) | API stream timeout after 19 chunks (120s) | High-impact latency bug in v0.19.3+; users report stalled "Thought for 2s" cycles followed by stream-death errors. 14 comments, welcome-pr tag. | 🔥 Active |
| [#8724](https://github.com/QwenLM/qwen-code/issues/8724) | Cross-session messaging between Qwen Code sessions | Proposed feature for multi-agent discovery (`list_agents`) and inter-session `send_message` with fail-closed gate. 11 comments, marked roadmap/multi-agent. | 🔥 Active |
| [#8625](https://github.com/QwenLM/qwen-code/issues/8625) | [CLOSED] Chinese Pinyin display glitch on Windows terminal | Visual regression where pinyin input is unreadable. Closed after fix. | Resolved |
| [#10372](https://github.com/QwenLM/qwen-code/issues/10372) | [CLOSED] `closeDiff` skips workspace-relative path resolution | Follow-up bug from PR #9811; `showDiffCommand` now correctly resolves relative paths. Closed. | Resolved |
| [#10520](https://github.com/QwenLM/qwen-code/issues/10520) | MCP tool `toolSearch.threshold > 0` causes llama.cpp 400 grammar error | Directly blocks local llama.cpp users with MCP tools; threshold 0 works, 10 fails with `failed to parse grammar`. 4 comments, ready-for-human. | 🔥 New |
| [#10530](https://github.com/QwenLM/qwen-code/issues/10530) | 400 grammar error with Qwen 3.8/3.6 in llama-server v0.22.3 | Regression in 0.22.3; gemma4-12b unaffected. Pi/OpenCode don't reproduce. 3 comments. | 🔥 New |
| [#10538](https://github.com/QwenLM/qwen-code/issues/10538) | [OPEN] Computer Use SDK 0.20.0 panics on Windows x64 | Runtime crash on every embedded runtime creation; blocks CUA users on Windows. | 🔥 New today |
| [#8172](https://github.com/QwenLM/qwen-code/issues/8172) | [CLOSED] Teammate messages queue beyond current response | Agent Team: `send_message` delivery waited for `Idle` state too long, not just current response. Closed after fix. | Resolved |
| [#9025](https://github.com/QwenLM/qwen-code/issues/9025) | [CLOSED] Keyless Vertex AI auth not inferred from env | Headless ADC runs now correctly select `vertex-ai` auth type. Closed. | Resolved |
| [#10208](https://github.com/QwenLM/qwen-code/issues/10208) | [CLOSED] Agent Team ghost member from failed concurrent spawn | Rollback removed member from memory but not persisted roster; ghost entries persisted. Closed. | Resolved |

## 4. Key PR Progress

| # | PR | Description | Status |
|---|-----|-------------|--------|
| [#10390](https://github.com/QwenLM/qwen-code/pull/10390) | `feat(web-shell): unblock git update on dirty working tree` | The "Update Project" action now presents a resolution panel when a plain pull is blocked by uncommitted changes, instead of dead-ending. | Open |
| [#10283](https://github.com/QwenLM/qwen-code/pull/10283) | `feat(cli): select output style via config or flag` | Adds `general.outputStyle` setting and `--output-style` flag, resolving the first practical way to pick from styles shipped in #9565. | Open |
| [#10183](https://github.com/QwenLM/qwen-code/pull/10183) | `feat(memory): structured on-demand recall` | Replaces flat auto-memory prompt with a two-level ref/title tree push/pull protocol and a dedicated recall tool. | Open |
| [#10171](https://github.com/QwenLM/qwen-code/pull/10171) | `feat(goal): let model propose a Goal for user approval` | New `propose_goal` core tool: model drafts a goal, user sees it in an approval dialog, only approval sets it. | Open |
| [#10427](https://github.com/QwenLM/qwen-code/pull/10427) | `fix(hooks): close four trust-boundary holes` | Closes hook system vulnerabilities where repo-controlled config met code execution/network egress (reopen of #8396). | Open |
| [#10411](https://github.com/QwenLM/qwen-code/pull/10411) | `feat(serve): expose Workflow tasks and controls` | Opt-in extension letting clients inspect live/persisted workflow runs (phase, dispatch, token, log, approval, lineage) and control active runs. | Open |
| [#9070](https://github.com/QwenLM/qwen-code/pull/9070) | `fix(core): surface ask_user_question cancellation reasons` | Prevents broad permission-allow rules from silently bypassing the question; preserves cancellation reason from the confirmation pipeline. | Open |
| [#10263](https://github.com/QwenLM/qwen-code/pull/10263) | `feat(cli): reload project runtime after /cd` | Transactional reload of settings, file watching, context files, permissions, tools, hooks, skills, subagents, MCP servers after directory change. | Open |
| [#10534](https://github.com/QwenLM/qwen-code/pull/10534) | `fix(vscode): restore native diff approval after WebShell cutover` | Restores native VS Code Diff Accept/Reject commands to resolve WebShell permissions after the #9811 UI cutover. | Open |
| [#10169](https://github.com/QwenLM/qwen-code/pull/10169) | `feat(review): audit applied --fix for unpinned new assumptions` | After `/review --fix`, a bounded agent audits what was applied using a git tree snapshot, catching assumptions the fix may have introduced. | Open |

## 5. Feature Request Trends

- **Multi-agent orchestration** remains the dominant theme — cross-session messaging (#8724), Agent Team message queuing fixes (#8172, #10208), and ghost-member remediation show sustained demand for robust team-based workflows.
- **Structured memory & recall** (#10183) reflects a push beyond flat prompt-injection memory toward queryable, tree-structured recall protocols.
- **User-in-the-loop goal setting** (#10171) indicates a trend toward models proposing plans that require explicit user approval before commitment.
- **Workflow visibility** (#10411) and **review auditability** (#10169) signal demand for observability into agent execution and fix application.

## 6. Developer Pain Points

1. **llama.cpp / local server integration regressions** — Two related issues (#10520, #10530) report grammar-parse failures introduced in v0.22.3 when using MCP tools with `toolSearch.threshold > 0`, blocking local inference workflows.
2. **WebShell cutover side-effects** — Multiple issues (#10372, #10373, #10405, #10385, #10406, #10534) trace back to the #9811 WebShell UI migration, causing diff path resolution bugs, permanent session-switch locks, and infinite re-render loops.
3. **Windows terminal rendering** — Pinyin display (#8625) and Computer Use SDK panics (#10538) highlight ongoing Windows-specific stability gaps.
4. **CI flakiness** — Transient ENOSPC on high-concurrency runners (#10035) and E2E test failures (#10510, #10536) continue to consume triage bandwidth.
5. **MCP tool argument visibility** — AUTO-mode classifier received empty argument projections for MCP tools, degrading tool selection accuracy (#10352, now closed).

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-30

## 1. Today's Highlights

The project is in active pre-release preparation for **v0.9.12**, with the integration branch now code-complete and gated on changelog and version-bump gates. A **high-severity sandbox bug** (#5723) blocking production `sudo` workflows was reported today, and a wave of feature PRs landed covering provider support, CLI identity, and web runtime improvements.

## 2. Releases

No new releases published in the last 24 hours. The v0.9.12 release candidate remains in progress on the integration branch (#5573).

## 3. Hot Issues

| # | Title | Status | Why It Matters |
|---|-------|--------|----------------|
| **#5573** | v0.9.12 milestone tracker | 🔵 Open | Central release tracker — must-fix P0 items listed, ship target set for v0.9.12 with full release chain. 22 comments, high community attention. |
| **#5723** | Agent shell sets `NoNewPrivs`, blocking `sudo` | 🔵 Open · **High** | Blocks production deployment workflows on existing runners. Reported today by `ronohara`. Critical for enterprise users. |
| **#5316** | EPIC-005: Crate Decomposition (Umbrella) | 🔵 Open | Umbrella tracking issue for the TUI crate decomposition — all sub-EPICs and FEATs report here. 19 comments. |
| **#5715** | Session recovery invisible after force-quit | 🔵 Open | Users losing context after a crash; work is on disk but the model can't see it. Reported by community member Gary in WeChat group. |
| **#5713 / #5718** | `wire = "responses" | "anthropic"` for custom providers | 🔵 Open | OpenAI-compatible providers can't use Responses or Anthropic Messages wire — limits third-party provider flexibility. |
| **#5350** | Simplify third-party model config with pre-built templates | ✅ Closed | Addresses pain for newcomers configuring OpenCode Zen, Agnes, Sensenova, etc. — built-in templates slash setup from manual to ~1 min. |
| **#790** | Improve i18n coverage | ✅ Closed | Post-`zh-Hant` expansion; many user-visible strings still hardcoded in English. Closes a long-standing localization gap. |
| **#1754** | AI should select shell & lang for `tool_call` | ✅ Closed | AI defaulting to bash-style commands broke users on Windows (PowerShell/cmd). Community-voted improvement. |
| **#5668** | `/copy` for last completed model output | ✅ Closed | UX gap — no explicit command to copy the latest assistant response without manual terminal text selection. |
| **#2094** | `/hunt` jurisdiction system: LLM-as-judge | ✅ Closed | Lands full Codex-style LLM-as-judge with configurable policies (strict/evidentiary/permissive) and trajectory-aware verdicts. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| **#5725** | `feat(providers): Concentrate as BYOK Responses gateway` | 🔵 Open | Adds **Concentrate** (`concentrate`) as a first-class opt-in provider — OpenAI Responses-compatible gateway at `api.concentrate.ai/v1`. Mirrors Eden AI aggregator pattern. |
| **#5721** | `feat(cli): Codewhale-account machine tokens (CODEWHALE_API_KEY)` | 🔵 Open | CLI authenticates as the account using `CODEWHALE_API_KEY` with no local session file or browser — fills a gap in the CI/account identity path. |
| **#5720** | `feat(web): Moonshot & Kimi native search` | 🔵 Open | Rescue of #5686 — lands native search for Moonshot and Kimi models with authorship preserved from `@h3c-hexin`. |
| **#5712** | `feat(cli): cloud-dispatch remote runner` | 🔵 Open | Makes `/dispatch` real: confirmed dispatch now runs a cloud agent in a sandbox and opens the forge PR, with runner receipts in the status card. |
| **#5717** | `feat(tui): adopt command shapes in project group (FEAT-021)` | 🔵 Open | Converts `/init`, `/lsp`, `/share`, `/goal` to the external command shapes from FEAT-014/015. Structural refactor of TUI commands. |
| **#5724** | `fix(sandbox): match read deny-list against resolved path` | 🔵 Open | Restores green shared CI (`macos-latest` + `windows-latest`). Fixes 6 `sandbox::read_guard` test failures on hosted runners. |
| **#5722** | `feat(tui): wire header pod + notifications` | 🔵 Open | Last two header-group segments — `pod n/m` capacity display and notification rendering, styled to shipped topbar design language. |
| **#5703** | `feat(tui): match Operate to landed CWC OperateRecord` | 🔵 Open | Aligns `cw · operate` to the CWC `OperateRecord` — camelCase fields (`burnRate`, `leadPlan`, `pace`, `cancelled`) and matching runtime API. |
| **#5659** | `feat(web): land tailnet runtime web with usable rail` | ✅ Closed | Lands `codewhale web --tailscale` after #5648; fixes loopback Runtime web rail cramped on `127.0.0.1:7878`. |
| **#5628** | `Enterprise launch readiness` | ✅ Closed | Adds `docs/ENTERPRISE.md` operator/security review packet; closes #5585 and #5617. Covers local runtime, auth, and security handoff. |

**Merged this period:**
- **#5714** — `wire = responses|anthropic` for `kind="openai-compatible"` (by `whp233`, carried forward as #5719)
- **#5661** — `fix(tui): context pressure as agent directive`
- **#5675 / #5676** — `uuid` 1.24→1.25, `futures-util` 0.3.33→0.3.34
- **#5673** — `next` bumped 15.5.21→16.3.3 (security fixes)

## 5. Feature Request Trends

- **Third-party provider onboarding** — Users want one-command setup for non-native providers (Concentrate, Moonshot, Kimi, OpenCode Zen, Agnes). Pre-built templates and `wire` dialect support are recurring themes.
- **Enterprise / deployment workflows** — Machine tokens, cloud dispatch, Tailscale web runtime, and `ENTERPRISE.md` signal a push toward team and CI/CD integration.
- **Robustness under crash** — Session recovery (#5715) and context-persistence after force-quit are top community requests; users lose work when the process is killed mid-turn.
- **Sandbox configurability** — `NoNewPrivs` blocking `sudo` (#5723) and the read deny-list fix (#5724) show the community needs more control over the execution environment.
- **UX polish** — `/copy` (#5668), pane zooming (#1261), and i18n expansion (#790) reflect ongoing investment in usability for non-English and power-user workflows.

## 6. Developer Pain Points

1. **Sandbox too restrictive** — `NoNewPrivs` prevents `sudo` and breaks existing deployment pipelines on production hosts. Users need a way to opt out or configure privileges per-project.
2. **Session loss on crash** — Force-quitting the TUI leaves the model blind to in-progress work; the on-disk state exists but is not surfaced to the next session.
3. **Cross-platform shell mismatches** — AI-generated commands assume POSIX shells; Windows users hit PowerShell/cmd incompatibilities repeatedly (#1754).
4. **Third-party config friction** — Without pre-built templates, configuring non-native providers is error-prone and slow, especially for new users (#5350).
5. **CI instability** — Hosted macOS and Windows runners have been red due to sandbox deny-list mismatches (#5724), blocking PR merges and adding noise to the workflow.
6. **Wire dialect gaps** — Custom `openai-compatible` providers couldn't select `responses` or `anthropic` message APIs, limiting which models could be used (#5713/#5719).

---

*Repository: [github.com/Hmbown/DeepSeek-TUI](https://github.com/Hmbown/DeepSeek-TUI)*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*