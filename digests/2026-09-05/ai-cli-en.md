# AI CLI Tools Community Digest 2026-09-05

> Generated: 2026-09-05 03:58 UTC | Tools covered: 10

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
**Date: 2026-09-05**

---

## 1. Ecosystem Overview

The AI CLI tools landscape in September 2026 is defined by rapid convergence on agent-centric workflows, multi-model routing, and desktop-grade UX — yet each tool occupies a distinct strategic niche. Claude Code and OpenAI Codex lead in enterprise feature depth and plugin ecosystems, while Gemini CLI and GitHub Copilot CLI emphasize platform integrations and security hardening. Open-source tools like OpenCode and Pi are closing capability gaps through community-driven feature requests, and Qwen Code is investing heavily in architectural modernization (OpenTUI migration). The dominant tension across all tools is between expanding model capability and maintaining session stability, memory efficiency, and permission transparency.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs (Updated/24h) | Releases (24h) | Release Status |
|------|-----------|------------------------|----------------|----------------|
| **Claude Code** | 10 | 2 | v2.1.261 | Active — org policy diagnostics, bash output limit config |
| **OpenAI Codex** | 10 | 14 | rust-v0.153.4, rust-v0.153.3 | Very Active — Astra hotfixes, TUI async question improvements, musl jemalloc |
| **Gemini CLI** | 10 | 10 | v0.60.0-nightly | Active — nightly hardening: env var sanitization, path boundary checks |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.84-1, v1.0.84-0, v1.0.83 | Moderate — Astra support, sandbox disable, Windows taskbar cards |
| **Kimi Code CLI** | 1 | 1 | None | Low — single key-binding issue, one fix PR for StrReplaceFile |
| **OpenCode** | 10 | 10 | v1.18.29, v1.18.28 | Active — OAuth fixes, Bedrock creds, npm timeout bounds |
| **Pi** | 6+ | N/A | v0.85.0 | Moderate — thinking effort persistence, new provider integrations |
| **Qwen Code** | 10 | 10 | None | Active — OpenTUI migration, Cerebras fix, HTML export bloat fix |
| **DeepSeek TUI** | 3 | 5 | None | Low-Moderate — token budget fix, CI restoration |
| **Grok Build** | — | — | None | Inactive |

---

## 3. Shared Feature Directions

| Trend | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **GPT-6 / Astra model support** | Claude Code, Codex, Copilot CLI, OpenCode | Model picker visibility, guidance tuning, async-question gating, subscription entitlement mapping |
| **Context & memory management** | Claude Code, Copilot CLI, OpenCode, DeepSeek TUI | Configurable compaction thresholds, auto-compaction loop fixes, token budget transparency for local models |
| **Plugin / extension extensibility** | Claude Code, OpenCode, Gemini CLI | Hook parity (PreToolUse/PostToolUse/Stop), lazy MCP loading, consent-driven env var injection |
| **Windows desktop stability** | Claude Code, Codex, Copilot CLI, Kimi Code | Orphaned process locks, key-binding regressions, AppX container leaks, EFS plugin loading |
| **Sandbox & permission transparency** | Claude Code, Codex, Gemini CLI, Copilot CLI | Diagnostic error messages on denial, sandbox permission inheritance across child sessions, auto-approval regressions |
| **Local / on-prem provider support** | OpenCode, DeepSeek TUI, Qwen Code, Gemini CLI | Ollama integration, AWS Bedrock default credential chains, Cerebras/Token-Plan ASR compatibility |
| **Async / multi-session orchestration** | Codex, Gemini CLI, Qwen Code, OpenCode | TUI async question UX, subagent recovery, background session management, turn navigation |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Qwen Code | DeepSeek TUI | Kimi Code | Pi |
|-----------|------------|--------------|------------|-------------|----------|-----------|-------------|-----------|----|
| **Core Focus** | Enterprise org policies, plugin ecosystem depth | GPT-6 model routing, Code Mode cost optimization | Security hardening, sandbox isolation, extension consent | GitHub integration, MCP OAuth, agent YAML config | Open-source extensibility, multi-provider OAuth | OpenTUI modernization, daemon lifecycle, channel routes | Local/Ollama model correctness, contributor accessibility | Windows Terminal key-binding parity | Provider flexibility (Bedrock, Meta, OrcaRouter) |
| **Target User** | Enterprise teams, org policy managers | Pro/Enterprise Codex users | Security-conscious developers, containerized workflows | GitHub-centric teams, MCP consumers | Open-source contributors, self-hosted deployments | Chinese/Alibaba Cloud ecosystem, daemon integrators | Local model practitioners, Ollama users | Windows power users | Multi-provider研究者, Mac users |
| **Technical Approach** | Bash/task output limits, org diagnostics | Rust-first, musl jemalloc, async TUI questions | Nightly releases, path-boundary enforcement, env var sanitization | YAML agent config, CIMD OAuth, session.resume model param | Go-based, npm plugin marketplace, ARB-based compaction | OpenTUI migration (ink→new renderer), channel session rotation | Rust TUI, route-window-aware budgeting | Minimalist, keymap-focused | Persistent thinking effort, Claude-native transports |

---

## 5. Community Momentum & Maturity

| Tier | Tools | Rationale |
|------|-------|-----------|
| **High Momentum** | Codex, Claude Code, OpenCode | High issue volume with rapid PR turnover; Codex shipped two hotfixes in 24h; Claude Code has the most upvoted issues (Function Hooks #91870 at 62 👍, Windows bug #42776 at 75 👍) |
| **Active & Iterating** | Gemini CLI, Qwen Code, Copilot CLI | Gemini ships nightly hardening; Qwen Code is undertaking a major OpenTUI rewrite with iterative sub-issues; Copilot CLI has steady releases but fewer community PRs |
| **Moderate** | Pi, DeepSeek TUI | Pi adds new providers and features but has lower issue volume; DeepSeek TUI is focused on correctness fixes (token budget, CI) with modest community engagement |
| **Niche / Low Activity** | Kimi Code, Grok Build | Kimi Code has one tracked issue this cycle; Grok Build had zero activity |

**Community Maturity Indicators:**
- **Claude Code** has the most mature plugin ecosystem discussion (Function Hooks proposal with 100 comments), but its Windows desktop stability issues are a maturity gap.
- **Codex** shows strong contributor activity with 14 PRs in 24h, but persistent Windows plugin bugs indicate fragmented QA across platforms.
- **OpenCode** has the most diverse feature request landscape (privacy, schema compat, dashboard analytics) — a sign of a maturing open-source community.
- **Gemini CLI** demonstrates Google's operational maturity through disciplined nightly security hardening and systematic sandbox isolation work.

---

## 6. Trend Signals

| Signal | Evidence | Developer Implication |
|--------|----------|----------------------|
| **Astra/GPT-6 rush** | Codex, Copilot CLI, OpenCode, Pi all shipping or fixing Astra model support this cycle | Model routing configuration is becoming a primary differentiator; expect per-model cost/behavior tuning to be a recurring requirement |
| **Permission system regressions are systemic** | Claude Code (#91650, #91683), Copilot CLI (#4537 ACP auto-approve), Codex (#33282 sandbox inheritance) | Tools are expanding tool execution scope faster than permission audit trails keep pace; demand for diagnostic transparency will intensify |
| **Context management is the new bottleneck** | Compaction loops (OpenCode #30680), token budget clamping (DeepSeek #5820), system prompt overhead (Copilot #2627, #232), silent context death (Claude #91385) | Tools that solve context efficiency — configurable thresholds, idle-aligned compaction, prompt-cache TTL integration — will gain enterprise adoption |
| **Windows desktop fragility is a category-wide risk** | Orphaned processes (Claude), EFS plugin failures (Codex), key-binding regressions (Kimi, Copilot), forced stealth updates (Claude #92246) | Windows-specific QA is consistently under-resourced; enterprise Windows deployments should monitor stability before upgrading |
| **MCP standardization friction** | Legacy initialize breakage (Copilot #4525), chroma-mcp incompatibility (Copilot #4647), lazy-loading demands (Claude #63251) | The MCP ecosystem is fragmenting across SDK versions; tools adopting lazy/on-demand MCP connections will reduce memory overhead significantly |
| **Agent behavior observability gap** | Subagent false success (Gemini #22323), child session visibility (OpenCode #29175), turn navigation (Qwen #11054), transcript replay breaks (Qwen #11060) | Multi-agent workflows are outpacing tooling for observability; deterministic status reporting and session-state persistence are emerging as critical needs |
| **Local model support is table stakes** | Ollama budget fixes (DeepSeek), Bedrock credential chains (OpenCode), Cerebras provider support (Qwen), Token-Plan ASR (Qwen) | Enterprise hybrid deployments require tools that treat local and cloud models with equal correctness — silent failures (1024-token clamping) are reputation-damaging |

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-09-05 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

### 1. `skill-creator` — Evaluation & Validation Pipeline Fixes
**[PR #1298](https://github.com/anthropics/skills/pull/1298) · OPEN · 🗓 2026-06-10**
Fixes the `run_eval.py` evaluation script that consistently reported `recall=0%` for every skill description, corrupting the optimization loop (`run_loop.py`, `improve_description.py`). Also patches Windows stream-reading, trigger detection, and parallel-worker bugs. The `skill-creator` toolchain had accumulated ~5 independent reproductions of this failure before this PR.

### 2. `document-typography` — Typographic Quality Control
**[PR #514](https://github.com/anthropics/skills/pull/514) · OPEN · 🗓 2026-03-04**
New skill targeting orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Authors note these issues affect every document Claude generates, yet users rarely request typographic correction — making the skill a strong proactive tool.

### 3. `odt` — OpenDocument Format Suite
**[PR #486](https://github.com/anthropics/skills/pull/486) · OPEN · 🗓 2026-03-01**
Covers creation, template filling, reading, and ODT→HTML conversion for `.odt` and `.ods` files. Triggered on mentions of ODT, ODS, ODF, LibreOffice, or ISO-standard document requests. Fills a gap left by the existing `docx` and `pdf` skills.

### 4. `testing-patterns` — Full Testing Stack
**[PR #723](https://github.com/anthropics/skills/pull/723) · OPEN · 🗓 2026-03-22**
Comprehensive skill spanning testing philosophy (Testing Trophy), unit testing (AAA pattern, edge cases), and React component testing (Testing Library, queries). Targets the community demand for structured test-generation guidance.

### 5. `service-now` — Enterprise Platform Assistant
**[PR #568](https://github.com/anthropics/skills/pull/568) · OPEN · 🗓 2026-03-08**
Broad ServiceNow skill covering ITSM, ITOM, ITAM/SAM Pro, FSM, HRSD, CSM, SPM/PPM, Vulnerability Response, Security IR, and IntegrationHub. Notable as one of the most ambitious domain-skills submitted, reflecting enterprise-user demand.

### 6. `mcp-builder` — Evaluation Harness Fixes
**[PR #1602](https://github.com/anthropics/skills/pull/1602) · OPEN · 🗓 2026-08-17**
Resolves serialization, benchmark metric, encoding, and script-stability bugs across the MCP builder evaluation pipeline. Tied to [Issue #1390](https://github.com/anthropics/skills/issues/1390) where `evaluation.py` silently fabricated tool errors, scoring 0/N on every real MCP server.

### 7. `pdf` & `docx` — Case-Sensitivity & Tracked-Change Fixes
**[PR #538](https://github.com/anthropics/skills/pull/538)** fixes 8 case-sensitive reference mismatches in `SKILL.md`; **[PR #541](https://github.com/anthropics/skills/pull/541)** prevents `w:id` collisions between tracked changes and existing bookmarks in DOCX output. Both authored by `Lubrsy706`.

### 8. `frontend-design` — Clarity & Actionability Overhaul
**[PR #210](https://github.com/anthropics/skills/pull/210) · OPEN · 🗓 2026-01-05**
Revised the existing frontend-design skill to ensure every instruction is executable within a single conversation, with specificity enough to steer behavior without ambiguity. One of the earliest sustained community improvement efforts.

---

## 2. Community Demand Trends

From the Issues backlog, the most-anticipated new Skill directions are:

| Trend | Signal |
|---|---|
| **Security & trust boundaries** | Issue #492 (43 comments, 2 👍) — community flagged namespace impersonation as a critical vulnerability |
| **Org-wide skill sharing** | Issue #228 (16 comments, **8 👍**) — the most-supported feature request; users want direct share links instead of manual `.skill` file distribution |
| **Agent governance & safety** | Issue #412 (6 comments) — proposal for policy enforcement, threat detection, trust scoring, and audit trails |
| **Compact persistent memory** | Issue #1329 (9 comments) — symbolic notation to reduce context overhead in long-running agents |
| **Quality & reasoning gates** | Issue #1385 (4 comments) — three-gate pipeline: pre-task calibration → adversarial review → delivery verification |
| **HPC / compute-cluster workflows** | PR #1615 — SCNet HPC skill with Slurm and SSH profile management |
| **Multi-agent delegation** | PR #1628 — "Hivemind" skill routing mechanical work to free-model workers while Claude Code remains planner/reviewer |

---

## 3. High-Potential Pending Skills

These PRs have active community engagement but remain **OPEN** — strong candidates for near-term merge:

| PR | Skill | Why It's Close |
|---|---|---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval fix | Critical infrastructure bug with 10+ reproductions; blocking the entire skill-creation loop |
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | Novel multi-agent delegation pattern addressing the "context is the scarce resource" pain point |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-audit** v1.3.0 | Mechanical verification + four-dimension reasoning quality gate; directly responsive to Issue #1385 |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Addresses a universal pain point; well-scoped, low-risk addition |
| [#1602](https://github.com/anthropics/skills/pull/1602) | `mcp-builder` evaluation fix | Critical for the MCP ecosystem; paired with Issue #1390 |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Broad testing coverage with strong community backing (Issue #202 called for skill-creator best practices) |
| [#1615](https://github.com/anthropics/skills/pull/1615) | **scnet-hpc** | Enterprise compute use case; fills a niche with no existing equivalent |
| [#486](https://github.com/anthropics/skills/pull/486) | **odt** | Completes the document-format triad (PDF + DOCX + ODT) |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **trustworthy, self-correcting skill infrastructure** — specifically, fixing broken evaluation tooling (the `skill-creator` and `mcp-builder` eval loops), preventing security boundary abuse via namespace impersonation, and enabling org-level skill governance — before adding new domain skills.

---



# Claude Code Community Digest — 2026-09-05

## 1. Today's Highlights

Claude Code **v2.1.261** shipped with organization policy diagnostics and configurable output limits for bash/task commands. The community is buzzing over a major **Function Hooks** enhancement proposal that could make plugins significantly more powerful, while Windows desktop users continue to report persistent session-killing bugs tied to auto-updates and orphaned process locks.

---

## 2. Releases

### v2.1.261

- Added an **"Organization policy" line** to `/status` and `claude doctor`, surfacing why an org policy failed to load (e.g., proxy not passing the endpoint through).
- Added `bashOutputMaxChars` and `taskOutputMaxChars` settings to raise the character limits on command and background task output.

🔗 Release details: [anthropics/claude-code](https://github.com/anthropics/claude-code)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#42776](https://github.com/anthropics/claude-code/issues/42776) | Claude Code Desktop fails to relaunch on Windows due to orphaned process file lock | Persistent Windows desktop bug where the app can't restart without a reboot; affects long-term reliability. | 🔥 159 comments · 👍 75 |
| [#91870](https://github.com/anthropics/claude-code/issues/91870) | Function Hooks — make plugins 10x more powerful | Major enhancement proposal for deep plugin modification via side-effect tracking and a continuation model (Express/Koa-style). Could redefine the plugin ecosystem. | 100 comments · 👍 62 |
| [#53247](https://github.com/anthropics/claude-code/issues/53247) | Desktop fails to launch on Windows — orphaned Silo/Job Object | Same family of Windows desktop crashes; requires logoff or reboot to recover (HRESULT 0x80070020). | 60 comments · 👍 28 |
| [#91650](https://github.com/anthropics/claude-code/issues/91650) | Bash cd-compound-read guard prompts on absolute cd targets with Read() deny rules | Regression in 2.1.257–2.1.259 causing excessive permission prompts, breaking common shell workflows on Windows Git Bash. | 10 comments · 👍 56 |
| [#91683](https://github.com/anthropics/claude-code/issues/91683) | bypassPermissions mode now prompts on `cd DIR && grep …` (regression in 2.1.259) | Related to #91650 — the bypassPermissions mode incorrectly triggers prompts, breaking expected permission-bypass behavior. | 7 comments · 👍 26 |
| [#89680](https://github.com/anthropics/claude-code/issues/89680) | Stealth update leaves orphaned processes holding old AppX container | Auto-updates fail to clean up, causing the new version to be unlaunchable until reboot — same 0x80070020 error family. | 15 comments · 👍 1 |
| [#91188](https://github.com/anthropics/claude-code/issues/91188) | Make auto-memory MEMORY.md compaction threshold configurable | Users want control over when the 200-line/25KB auto-memory compaction reminder triggers instead of the hardcoded target. | 20 comments |
| [#81658](https://github.com/anthropics/claude-code/issues/81658) | Cross-platform sync failure causing Cowork conversations to disappear | Suspected server-side incident disrupting sync between Desktop, Web, and Android — high-impact for Cowork users. | 16 comments · 👍 4 |
| [#89467](https://github.com/anthropics/claude-code/issues/89467) | Windows desktop window always-on-top with no disable option | UX regression leaving no way to make the window behave normally alongside other apps. | 15 comments · 👍 10 |
| [#92246](https://github.com/anthropics/claude-code/issues/92246) | Windows desktop self-updates restart over a running session — no opt-out | Users forced through repeated restarts (9 in 9 days reported) with no deferral or prompt, killing active work. | 1 comment · 👍 0 |

---

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#87079](https://github.com/anthropics/claude-code/pull/87079) | fix(security-guidance): make ** glob patterns match zero-depth paths | Fixes a silent security regression where `**/*.ts` patterns in `security-patterns.json` excluded top-level files because `fnmatch` bare `*` crosses `/`. Critical for security rule coverage. |
| [#61691](https://github.com/anthropics/claude-code/pull/61691) | [scripts] Add diagnostic script for GitHub connector showing 'Connected' but no tools | PowerShell repair script for the recurring Windows bug where the GitHub MCP connector in Cowork reports Connected but exposes zero tools (closes #61682). |

> **Note:** Only 2 PRs were updated in the last 24 hours.

---

## 5. Feature Request Trends

- **Plugin extensibility**: The Function Hooks proposal (#91870) signals strong community demand for deeper, safer plugin capabilities — side-effect tracking and composable continuations are key themes.
- **Configurability of memory & permissions**: Users want tunable thresholds for auto-memory compaction (#91188) and clearer diagnostic messages when permission denials fire (#87153).
- **MCP efficiency**: Multiple requests (#63251, #82952) call for lazy/on-demand MCP server connections and per-session scoping to reduce startup RAM and memory pressure.
- **Subagent & agent tooling**: Feature requests around subagent prompt-cache cost reduction (#74318), model selection for background task chips (#70610), and per-subagent tool allowlisting (#92259) reflect growing complexity in multi-agent workflows.
- **Cowork UX improvements**: Chat sorting by creation date (#87723) and better Cowork session management are recurring asks.

---

## 6. Developer Pain Points

1. **Windows desktop instability** dominates the conversation — orphaned process locks, AppX container leaks, and forced restarts from stealth updates create a cycle of broken sessions with no user-controlled recovery. This is the single biggest frustration (issues #42776, #53247, #89680, #92246).

2. **Permission system regressions** in recent patches (2.1.257–2.1.259) cause overly aggressive prompts on compound bash commands, breaking workflows for users with `Read()` deny rules (#91650, #91683).

3. **Lack of diagnostics** when permissions are denied — error messages don't indicate which rule or settings file fired (#87153), making troubleshooting opaque.

4. **Context management gaps** — the context ring no longer warns before hitting the limit, leading to silent session death at "Prompt is too long" (#91385).

5. **Remote Control and cross-session tooling regressions** — `ListAgents`/`SendMessage` missing from scheduled-task and remote-control sessions since Desktop 1.44121.x (#92249, #90243), and stale pairing records (800+) truncating reachability scans.

6. **MCP resource waste** — every session spawns all configured MCP servers regardless of use, causing significant RAM multiplication across concurrent sessions (#63251, #82952).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-05

## 1. Today's Highlights

The 0.153.x hotfix cycle addressed GPT-6-Astra visibility and guidance issues in the bundled model picker, while the community continues to push on persistent Windows plugin/UX bugs. On the feature side, async question handling in the TUI received a concentrated wave of improvements, and Linux musl builds now ship with jemalloc for better memory performance.

## 2. Releases

**rust-v0.153.4** — Hotfix release focusing on GPT-6-Astra:
- Fixed Astra's visibility in the bundled model picker; it is now the default when no model is explicitly configured.
- Updated Astra's guidance so async-question prompting is gated behind actual tool availability in the session.

**rust-v0.153.3** — Feature + fix release:
- Added GPT-6-Astra to the Amazon Bedrock model picker for Mantle and Runtime global/US routes.
- Corrected Astra's guidance for async clarification questions to use the supported tool and recognize text-only input.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#28919](https://github.com/openai/codex/issues/28919) | Windows Codex app missing "control other devices" tab in Settings | Blocks remote/device-control workflows on the largest desktop OS; affects Pro users on Win11. | 59 comments · 54 👍 |
| [#41049](https://github.com/openai/codex/issues/41049) | code-mode host exited during handshake; GPT-5.6 not working | Handshake failure prevents code-mode sessions from initializing — a core workflow breaker. | 46 comments · 1 👍 |
| [#35050](https://github.com/openai/codex/issues/35050) | GPT-5.6 serializes independent Code Mode calls | Explicit batching reduced weighted usage by 27–45%, directly impacting cost and latency for power users. | 30 comments · 41 👍 |
| [#25220](https://github.com/openai/codex/issues/25220) | Bundled plugins unavailable on EFS-encrypted WindowsApps | All bundled plugins (Computer Use, Browser, Chrome, LaTeX) fail to load on Microsoft Store installs with EFS — a platform-specific but high-impact bug. | 29 comments · 4 👍 |
| [#41463](https://github.com/openai/codex/issues/41463) | Cannot create projects on Windows + WSL2 | `AbsolutePathBuf` deserialization without a base path breaks project creation in the WSL2 co-run scenario. | 27 comments · 18 👍 |
| [#41513](https://github.com/openai/codex/issues/41513) | Pets become click-through and undraggable on Windows | Floating pets stop responding to input after certain conditions — a recurring Windows-specific UX regression. | 23 comments · 10 👍 |
| [#32069](https://github.com/openai/codex/issues/32069) | Hide Pets menu item; add configurable prompt polishing | Users want a cleaner menu and the ability to configure prompt-polishing behavior rather than having it forced. | 16 comments · 17 👍 |
| [#41960](https://github.com/openai/codex/issues/41960) | Windows Pets do not respond to clicks or drag | Second report of the same Windows Pets input regression; indicates an unresolved platform issue. | 15 comments · 17 👍 |
| [#41566](https://github.com/openai/codex/issues/41566) | Paginated rollout emits duplicate ordinal, freezing thread history | A rollout edge case causes thread history projection to permanently freeze — affects Pro users on Windows 10. | 15 comments · 0 👍 |
| [#33282](https://github.com/openai/codex/issues/33282) | `create_thread` does not inherit auto-approval mode for worktree tasks | Sandbox permission inheritance is broken between parent and child sessions, causing unexpected approval prompts. | 15 comments · 6 👍 |

## 4. Key PR Progress

| PR | Summary |
|----|---------|
| [#42904](https://github.com/openai/codex/pull/42904) | Use static instructions for Default collaboration mode — removes template rendering and `codex-utils-template` dependency for the default/plan modes. |
| [#42903](https://github.com/openai/codex/pull/42903) | Preserve TUI question state and integrate history/queue navigation — retains drafts, selections, and expanded state across reconnects and session refreshes. |
| [#42900](https://github.com/openai/codex/pull/42900) | Establish root turn identity for independent tasks and memory requests — fixes detached memory requests and background turns lacking a `root_turn_id`. |
| [#42897](https://github.com/openai/codex/pull/42897) | Add inline "Other" answers to async question choices — users can now type alternative answers directly in the question pane. |
| [#42894](https://github.com/openai/codex/pull/42894) | Support selectable answers for asynchronous TUI questions — renders numbered, wrapped choice buttons and requires full visibility before submission. |
| [#42891](https://github.com/openai/codex/pull/42891) | Integrate asynchronous questions into the TUI — displays questions from live agent messages with expandable answer editors and preserves the main composer draft. |
| [#42879](https://github.com/openai/codex/pull/42879) | List GPT-6-Astra in the model picker — sets bundled model visibility to `list` so it appears first. |
| [#42878](https://github.com/openai/codex/pull/42878) | Qualify Astra async-question guidance with "When available" — prevents the model from assuming `functions.request_user_input_async` exists in every session. |
| [#42870](https://github.com/openai/codex/pull/42870) | Avoid redundant filesystem sandbox path resolution — eliminates synchronous probes of unrelated permission roots on the executor runtime thread (Linux). |
| [#42850](https://github.com/openai/codex/pull/42850) | Use jemalloc for Linux musl binaries — switches both CLI and app server to `tikv-jemallocator` on x86_64 and aarch64 musl targets. |

## 5. Feature Request Trends

- **Async question UX in the TUI** — A concentrated set of PRs and community issues show strong demand for better asynchronous question handling, including inline answers, selectable choices, and draft preservation.
- **Pets customization** — Users want the option to hide the Pets menu item and configure prompt-polishing behavior, signaling a desire for a leaner, more configurable desktop experience.
- **Dynamic conversation titles** — An open enhancement asks for model-driven rename capability so conversation titles evolve with the work rather than staying static.
- **Automation after rate-limit windows** — Users would like Codex to automatically resume work once rate limits reset, rather than requiring manual re-initiation.
- **Native AI-generated commit messages** — The IDE extension community wants built-in commit message generation using chat context, eliminating reliance on third-party extensions.

## 6. Developer Pain Points

- **Windows plugin and UI regressions dominate** — Bundled plugins (Computer Use, Browser, LaTeX) failing on EFS-encrypted installs, Pets becoming click-through, and the missing "control other devices" tab point to persistent Windows-specific quality gaps that are frustrating Pro users.
- **Sandbox and permission inheritance issues** — Multiple reports (`#33282`, `#25590`, `#40125`) describe inconsistent auto-approval and sandbox mode propagation between parent and child threads, causing unexpected permission prompts.
- **Model routing and availability friction** — GPT-6-Astra visibility issues (`#42853`, `#42868`) and CLI/Luna Reserve entitlement mismatches (`#40939`) create confusion about which models and quotas are accessible across Codex App vs. CLI.
- **Serial vs. parallel execution cost** — Issue `#35050` highlights that GPT-5.6's tendency to serialize independent Code Mode calls is a significant cost and latency concern; batching is a known mitigation but not yet the default behavior.
- **Thread and session state persistence** — Duplicate ordinals from paginated rollouts (`#41566`), workspace root leaks across concurrent sessions (`#24224`), and deleted conversations lingering in Recents (`#41661`) all point to state-management fragility in long-running sessions.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-05

## 1. Today's Highlights
The Gemini CLI team shipped a nightly release (v0.60.0‑nightly.20260905.g85aca163f) that hardens extension environment‑variable handling and strengthens workspace path‑boundary checks. Community attention is focused on several persistent agent‑behavior bugs (subagent recovery, generalist‑agent hangs, shell‑command stalls) and ongoing work to improve Auto Memory’s security and reliability.

## 2. Releases
**v0.60.0‑nightly.20260905.g85aca163f** ([#29218](https://github.com/google-gemini/gemini-cli/pull/29218))  
- **Extensions** ([#28863](https://github.com/google-gemini/gemini-cli/pull/28863)): Prompt for consent on environment changes and sanitize runtime‑altering environment variables to prevent unauthorized injection into MCP processes.  
- **Core** ([#29170](https://github.com/google-gemini/gemini-cli/pull/29170)): Enhance workspace‑path boundary checks and symlink resolution across command‑safety heuristics, file‑discovery services, and directory‑listing tools on POSIX and Windows.

## 3. Hot Issues
| Issue | Title | Why It Matters | Community Reaction |
|-------|-------|----------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Misleading termination status can hide incomplete analysis, leading to silent failures in multi‑repo investigations. | 13 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | Simple tasks (e.g., folder creation) cause the generalist agent to hang indefinitely, blocking workflow. | 8 comments, 8 👍 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck “Waiting input” | Commands that complete normally still leave the agent in an interactive‑await state, requiring manual cancellation. | 4 comments, 3 👍 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction & reduce Auto Memory logging | Auto Memory reads transcripts before redaction, risking secret exposure in model context and service logs. | 5 comments, 0 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess impact of AST‑aware file reads, search, mapping | AST‑aware tools could reduce turn count and token noise by precisely reading method bounds and navigating code. | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills/sub‑agents enough | Anecdotal evidence suggests custom skills and sub‑agents are underutilized without explicit prompting. | 6 comments, 0 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser_agent resilience (session takeover, lock recovery) | Current fail‑fast strategy aborts when a locked browser profile is detected, interrupting persistent‑session workflows. | 4 comments, 0 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails in Wayland | Browser agent termination reports GOAL despite failure in Wayland environments, hindering cross‑platform reliability. | 4 comments, 1 👍 |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores settings.json overrides | Overrides like `maxTurns` in `settings.json` are ignored, causing unexpected behavior. | 3 comments, 0 👍 |
| [#26523](https://github.com/google-gemini/gemini-cli/issues/26523) | Surface or quarantine invalid Auto Memory inbox patches | Invalid patches are silently skipped, making debugging difficult and potentially masking data‑integrity issues. | 3 comments, 0 👍 |

## 4. Key PR Progress
| PR | Title | Summary |
|----|-------|---------|
| [#29218](https://github.com/google-gemini/gemini-cli/pull/29218) | chore/release: bump version to 0.60.0‑nightly.20260905.g85aca163f | Automated nightly version bump. |
| [#28951](https://github.com/google-gemini/gemini-cli/pull/28951) | feat(pr‑generation): add Cloud Run job & workflow orchestration | Adds production Cloud Run Job config, Cloud Workflow orchestration, and deployment automation for the PR‑generation pipeline. |
| [#28953](https://github.com/google-gemini/gemini-cli/pull/28953) | feat(pr‑generation): evaluation diff PR submission helper | Introduces `create_pr_from_diff.py` for automated diff application, CI verification, and PR submission with unit tests. |
| [#29116](https://github.com/google-gemini/gemini-cli/pull/29116) | fix(core): mitigate NTFS 8.3 short‑name path issues | Handles Windows short names (e.g., `git~1`) in path normalization and the AllowedPathChecker safety engine. |
| [#29215](https://github.com/google-gemini/gemini-cli/pull/29215) | fix(core): enforce envelope metadata provenance | Updates system prompt to require strict provenance checks for external tool/MCP outputs, deriving author identity from verified envelope properties. |
| [#29216](https://github.com/google-gemini/gemini-cli/pull/29216) | fix(cli): isolate settings directory in sandbox containers | Prevents host `~/.gemini` credentials (OAuth tokens, account creds) from being exposed when running inside Docker/Podman sandboxes. |
| [#29217](https://github.com/google-gemini/gemini-cli/pull/29217) | fix(config): don’t rewrite explicit gemini‑2.5‑flash selection | Fixes `isFlashModel()` broad matching that inadvertently auto‑upgraded explicitly pinned `gemini‑2.5‑flash` to `gemini‑3.5‑flash`. |
| [#29214](https://github.com/google-gemini/gemini-cli/pull/29214) | fix(sandbox): harden filesystem boundaries & isolate runtime state | Replaces host directory mounts with read‑only config files, resolves symlinks during path checks, and decouples container environment. |
| [#29170](https://github.com/google-gemini/gemini-cli/pull/29170) | fix(core): enhance workspace path boundary checks & symlink resolution | Strengthens boundary enforcement across command safety, file discovery, and directory listing on POSIX/Windows. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | fix(extensions): consent on environment changes & sanitize env vars | Incorporates MCP server environment configs into consent strings and sanitizes custom env variables to block unauthorized injection. |

## 5. Feature Request Trends
- **AST‑aware code navigation**: Multiple issues (#22745, #22746) request investigation into AST‑based file reading, searching, and mapping to reduce turn count and token noise.
- **Subagent resilience & observability**: Requests for better recovery after turn limits (#22323), visible trajectories via `/chat share` (#22598), and automatic session takeover for browser agents (#22232).
- **Security & sandbox hardening**: Emphasis on deterministic redaction (#26525), quarantine of invalid memory patches (#26523), isolation of settings in containers (#29216), and stricter file‑ownership checks (#29115).
- **Configuration robustness**: Fixes for `settings.json` overrides being ignored (#22267), symlink‑based agent recognition (#20079), and explicit model‑selection preservation (#29217).

## 6. Developer Pain Points
- **Agent hangs & stalls**: Generalist agent hangs (#21409), shell commands stuck in “Waiting input” (#25166), and browser agent failures in Wayland (#21983) repeatedly block workflows.
- **Subagent behavior inconsistencies**: Subagents sometimes report false success after hitting turn limits (#22323) and are underutilized without explicit prompting (#21968).
- **Security & credential exposure**: Auto Memory processes transcripts before redaction (#26525), and sandbox containers can leak host credentials (#29216).
- **Configuration pitfalls**: Extensions bypass consent for environment changes (#28863), browser agent ignores `settings.json` overrides (#22267), and NTFS short names cause path‑safety issues (#29116).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-09-05

## 1. Today's Highlights

GitHub Copilot CLI v1.0.84-1 ships with GPT-6 Astra support, while v1.0.84-0 introduces the ability to disable managed sandbox sessions via an approved bypass prompt. The community is increasingly focused on context management efficiency, plugin marketplace control, and resolving regressions in session persistence and MCP compatibility introduced in recent patches.

## 2. Releases

**v1.0.84-1** — Adds support for the GPT-6 Astra model.

**v1.0.84-0** — Managed sandbox sessions can now be disabled for the remainder of a session from an approved bypass prompt. Fixes a PowerShell sandbox write-block issue that offered to run commands outside the sandbox, and resolves a multi-account credential store bug affecting sandboxed `gh` commands.

**v1.0.83** (2026-09-04) — Windows 11 taskbar live hover status cards for running Copilot sessions; Client ID Metadata Document (CIMD) support for MCP OAuth sign-in; custom agents can now list multiple models in `model` (tried in order) with `model-policy: required` enforcement.

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#2904](https://github.com/github/copilot-cli/issues/2904) | Custom Agent YAML Frontmatter Should Support Reasoning Effort | 8 | 23 | Allows per-agent reasoning effort control without global flags — critical for cost/performance tuning across heterogeneous agent setups. |
| [#2627](https://github.com/github/copilot-cli/issues/2627) | Configurable System Prompt — Slim Down Fixed Token Overhead | 4 | 19 | System prompt alone consumes ~20,500 tokens (~10% of a 200K window). Users need the ability to trim unused instructions. |
| [#232](https://github.com/github/copilot-cli/issues/232) | Add System Prompt Parameter for Copilot-CLI | 5 | 10 | Foundational request for `--system-prompt` to inject instructions without repo-scoped files. |
| [#1688](https://github.com/github/copilot-cli/issues/1688) | Configurable Auto-Compaction Threshold | 3 | 5 | Context bloat degrades performance on slower models (e.g., Claude Opus 4.6) well before built-in compaction triggers fire. |
| [#4525](https://github.com/github/copilot-cli/issues/4525) ✅ | 1.0.81-1 Sends Legacy `initialize` After Modern `server/discover`, Causing -32022 | 6 | 3 | **Closed.** A regression breaking MCP stdio server initialization with Python MCP SDK 2.0.0 dual-era runners. |
| [#4537](https://github.com/github/copilot-cli/issues/4537) | ACP Mode Auto-Approves Tool Calls Again — Regression of #845 | 1 | 2 | Shell commands, file edits, and deletions execute unattended in `--acp` mode with no permission prompt — a security regression. |
| [#4328](https://github.com/github/copilot-cli/issues/4328) | Ctrl+H Misinterpreted as Ctrl+Backspace Under WSL2 | 7 | 0 | WT_SESSION leaking from Windows Terminal causes `ctrl+h` to delete whole words instead of characters. |
| [#4710](https://github.com/github/copilot-cli/issues/4710) | Runaway `copilot-file-search` Thread Consumes CPU and Disk While Idle | 1 | 0 | An internal search thread runs unbounded even when the session reports `idle`, pinning a CPU core and logging to `~/.copilot/logs`. |
| [#4725](https://github.com/github/copilot-cli/issues/4725) | Frequent JavaScript Heap Out of Memory | 1 | 0 | CLI crashes every few minutes with heap allocation failures (~4 GB), indicating a memory leak in sustained sessions. |
| [#4647](https://github.com/github/copilot-cli/issues/4647) | v1.0.81 Broke Compatibility with chroma-mcp | 3 | 0 | MCP config using `mcpServers` format fails after the 1.0.80 → 1.0.81 update. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#3771](https://github.com/github/copilot-cli/pull/3771) | Initial project setup | Open | Early-stage scaffolding PR from June 2026; no recent activity. |

*No other PRs were updated in the last 24 hours.*

## 5. Feature Request Trends

- **Granular context control** — Multiple overlapping requests (#232, #2627, #1688, #4724) call for user-configurable system prompts, adjustable compaction thresholds, and idle-aligned auto-compaction tied to prompt-cache TTL. The community wants to reduce fixed token overhead and avoid paying full price on every turn.
- **Per-agent model and reasoning configuration** — #2904 and the v1.0.83 multi-model support signal demand for agent-level tuning (model, reasoning effort) independent of global CLI flags.
- **Plugin marketplace governance** — #4715 asks for the ability to block built-in agent plugin marketplaces (e.g., `copilot-plugins`, `awesome-copilot`) in enterprise environments.
- **System-level instruction injection** — `--system-prompt` (#232) remains a top-voted feature for injecting global instructions without repo-scoped files.

## 6. Developer Pain Points

- **Session and permission regressions** — ACP mode silently auto-approves tools again (#4537), `session.resume` ignores the `model` parameter (#4645), and the built-in research agent references a non-existent `github/get_me` tool (#4729). These break expected workflows in agent mode.
- **MCP compatibility breakages** — v1.0.81 introduced a legacy `initialize` call that breaks modern stdio servers (#4525), and chroma-mcp compatibility was also lost (#4647).
- **Memory and resource leaks** — The CLI crashes with heap OOM during sustained use (#4725), and a background `copilot-file-search` thread can run indefinitely while idle, consuming CPU and disk (#4710).
- **Cross-platform input quirks** — Ctrl+H behaves incorrectly under WSL2 (#4328), and mouse scroll in integrated terminals cycles input history instead of scrolling (#3194).
- **BYOK cost surprise** — v1.0.82 silently disables prompt caching in BYOK mode (#4720), inflating costs by ~5× without any warning.
- **Desktop app breakage** — Auto-update can overwrite `copilot.exe`, breaking the bundled desktop app's ability to resume sessions (#4728).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-05

## 1. Today's Highlights

The community's most active discussion this cycle centers on a Windows Terminal key-binding regression: users report that custom key mappings (notably `Ctrl+V` for paste) fail to apply in version 0.40.1. In parallel, an open PR (#2524) proposes a fix for `StrReplaceFile` replacement counting, which had been incorrectly based on original file content rather than the live edited state.

---

## 2. Releases

**No new releases in the last 24 hours.** The latest referenced version in community discussions remains **v0.40.1**.

---

## 3. Hot Issues

### Issue #2634 — [bug] Key remapping fails in Windows Terminal (e.g., paste)
- **Author:** PANG-GIT-AI | **Created:** 2026-09-04 | **Comments:** 0 | 👍 0
- **Link:** [MoonshotAI/kimi-cli#2634](https://github.com/MoonshotAI/kimi-cli/issues/2634)
- **Why it matters:** A significant number of Windows users rely on custom terminal key bindings (especially `Ctrl+V` paste). If Kimi Code CLI ignores or overrides these settings, it creates a friction point for power users who manage workflows through terminal-level remaps. The issue affects version 0.40.1 on PowerShell/Windows Terminal specifically.
- **Community reaction:** No comments yet, but the topic is likely to draw interest from the Windows user base. The issue's specificity (version + platform + shell) suggests a reproducible regression worth tracking.

---

## 4. Key PR Progress

### PR #2524 — [fix(tools)] Count StrReplaceFile replacements against running content
- **Author:** Sreekant13 | **Created:** 2026-07-20 | **Updated:** 2026-09-04 | **Comments:** undefined | 👍 0
- **Link:** [MoonshotAI/kimi-cli#2524](https://github.com/MoonshotAI/kimi-cli/pull/2524)
- **What it does:** Resolves [#2526](https://github.com/MoonshotAI/kimi-cli/issues/2526). The `StrReplaceFile` tool applies edits sequentially but was computing the replacement count against the *original* file content. This caused chained edits—where an `old` string is produced by an earlier replacement—to fail silently because that string no longer exists in the original content. The fix aligns the reported count with the running (mutated) content state.
- **Significance:** This is a correctness fix for a core editing tool. Chained file replacements are a common pattern when refactoring code across multiple occurrences. The stale-count bug could lead to incorrect tool reports and missed edits.

---

## 5. Feature Request Trends

Based on the current issue landscape, the following direction is emerging:

- **Terminal / input customization parity:** The #2634 issue highlights a gap between Kimi Code CLI's key-binding handling and the expectations of users running inside Windows Terminal with custom PowerShell configurations. The community appears to want the CLI to respect and properly integrate with host-terminal key mappings rather than intercepting or ignoring them.

---

## 6. Developer Pain Points

1. **Key binding / paste on Windows:** The sole open issue this cycle points to a concrete pain point — Windows Terminal users cannot rely on standard key mappings like `Ctrl+V` working as expected inside Kimi Code CLI. This is especially disruptive for users who have configured custom remaps at the terminal level.

2. **Chained edit reliability:** PR #2524's fix for `StrReplaceFile` reveals an underlying fragility in multi-step file editing workflows. Developers performing sequential replacements across a file expect each step to build on the previous one; when the tool reports counts based on stale content, it breaks that expectation and can produce incomplete or incorrect diffs.

---

*Data sourced from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) as of 2026-09-05.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑09‑05

## 1. Today’s Highlights
OpenCode **v1.18.29** ships a quick bugfix release that restores Codex OAuth model filtering for integer GPT versions (e.g., `gpt-6`) and resolves a desktop authentication‑client‑ID issue. Meanwhile, the community is intensifying demand for native **Claude Code hooks** (`PreToolUse`, `PostToolUse`, `Stop`) compatibility (#12472), and several high‑traffic issues around auto‑compaction loops (#30680) and image‑reading regressions (#25832) remain open.

## 2. Releases
**v1.18.29** (Core & Desktop) – GitHub: [v1.18.29](https://github.com/anomalyco/opencode/releases/tag/v1.18.29)
- **Core**: Fixes Codex OAuth model filtering to recognize integer GPT versions (`gpt-6`); resolves `gpt-6-astra` not appearing for OpenAI subscription users.
- **Desktop**: Uses the correct desktop client ID during account device authentication; increases the “open‑in” app icon size for better visibility.

**v1.18.28** – GitHub: [v1.18.28](https://github.com/anomalyco/opencode/releases/tag/v1.18.28)
- **Core**: Sends the session ID as a GitHub Copilot interaction header to improve request tracking across a session.

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| #12472 | **Native Claude Code hooks compatibility** | Deepens Claude Code parity by exposing `PreToolUse`, `PostToolUse`, `Stop` hooks to plugins. | 🔥 19 comments, 👍 40 – top community‑vetted feature request. |
| #19948 | **Integration with Ollama Local** | Highlights a broken JSON‑response loop when using local Ollama models in Desktop. | 23 comments, 👍 5 – active debugging thread. |
| #25832 | **opencode cannot read images anymore** | Regression: image‑upload feature stopped working after April 29, blocking multimodal workflows. | 18 comments, 👍 5 – users seeking a rollback or fix. |
| #30680 | **OpenCode immediately enters auto‑compaction loop** | Severity‑high bug where the client loops compaction and stops generating responses, even in empty projects. | 17 comments – no thumbs‑up yet, but clearly impacts stability. |
| #35148 | **bad gateway error** | Persistent 502/504 errors in Desktop (v1.16.2) with Go plugin, causing infinite retry loops. | 9 comments, 👍 13 – strong signal of backend‑connectivity pain. |
| #44684 | **plugin installer times out fetching public deps** | npm install hangs when fetching from `registry.npmjs.org`, blocking boot and headless runs. | 5 comments – directly affects Windows/Unix plugin setups. |
| #17188 | **Default sharing to “disabled” — privacy by default** | Feature request to flip the default sharing behavior, addressing informed‑consent and privacy concerns. | 5 comments, 👍 13 – strong privacy‑advocacy support. |
| #47142 | **Issue with Overall Usage Percentage Calculation on Dashboard** | Dashboard incorrectly sums per‑model percentages instead of weighting by quota, skewing usage analytics. | 4 comments – impacts billing/monitoring accuracy. |
| #29175 | **Direct child sessions are hidden in parent session UI** | Plugin‑created child sessions do not appear in the parent’s TUI, breaking multi‑session visibility. | 4 comments – affects plugin authors and advanced workflows. |
| #35528 | **Tool schemas with `additionalProperties:false` missing “required”** | Strict JSON‑schema validators (e.g., ajv) reject tool definitions, causing AI‑API call failures. | 3 comments – schema‑compatibility issue for gateway users. |

## 4. Key PR Progress
| # | Title | Type | Summary |
|---|-------|------|---------|
| #47436 | **feat(ai): resolve Bedrock credentials through the AWS default chain** | Feature | Reads `AWS_PROFILE`, `~/.aws` config, SSO cache, web‑identity tokens, and instance metadata – removes the need for static credentials. |
| #47430 | **fix(core): bound npm installs with a configurable timeout** | Bugfix | Prevents `Npm.reify()` from hanging indefinitely; adds a timeout parameter to arborist reification. |
| #47427 | **fix(desktop): prevent large paste crashes** | Bugfix | Stops the Desktop UI from lagging/crashing when a large text payload is pasted into the prompt (Windows‑specific repro). |
| #47424 | **fix(app): increase vertical tabs minimum width** | Bugfix | Raises vertical‑tab sidebar min‑width from 130px to 140px to eliminate label wrapping. |
| #47423 | **feat(core): support provider OAuth client credentials** | Feature | Adds opt‑in `client_credentials` OAuth with in‑memory token caching and automatic renewal on `401`/invalid‑token. |
| #47388 | **fix(tui): reload local plugin dependency graphs** | Bugfix | Forces the TUI to refresh cached plugin dependencies after a local CLI‑plugin helper is edited, preventing stale‑export errors. |
| #47342 | **fix(console): openai usage normalization and tier threshold config** | Bugfix | Subtracts `cached_tokens` and `cache_write_tokens` from `input_tokens` to avoid double‑counting; fixes `cost200K` tier threshold. |
| #47428 | **fix(app): defer background workspace discovery** | Perf | Lazily loads worktree inventories and MCP catalogs only when a session is opened, reducing bootstrap overhead. |
| #47391 | **perf(plugin): parallel internal plugin loading** | Perf | Switches plugin initialization to `Effect.forEach` with unbounded concurrency, speeding up startup without functional changes. |
| #47392 | **fix(lsp): idle TTL timeout and LRU eviction policy** | Bugfix | Introduces idle‑timeout and LRU eviction for LSP clients to prevent unbounded memory growth. |

## 5. Feature Request Trends
- **Claude Code hooks parity** – Users repeatedly ask for native support of `PreToolUse`, `PostToolUse`, and `Stop` hooks to align with Claude Code’s plugin ecosystem.
- **OAuth & credential flexibility** – Multiple requests (#47423, #47436) for streamlined provider authentication (OAuth client credentials, AWS default chain, Web Identity) to reduce manual configuration.
- **Privacy‑by‑default sharing** – Demand to flip the default sharing state to “disabled” (#17188) and provide per‑project/URL whitelisting (#35565).
- **Dashboard & usage transparency** – Requests for accurate usage‑percentage calculation (#47142), custom provider model filtering (#35506), and clear pricing display (#33881).
- **Plugin & session orchestration** – Interest in exposing session forms, session lists, and global event streams (#46690), plus finalization hooks for main/subagent sessions (#35540).

## 6. Developer Pain Points
- **Network & install timeouts** – npm install hangs (#44684) and bad‑gateway loops (#35148) disrupt both interactive and headless workflows.
- **Session‑management bugs** – Auto‑compaction loops (#30680), hidden child sessions (#29175), and large‑paste crashes (#47427) degrade stability.
- **Schema compatibility** – Strict JSON‑schema validators reject tool definitions when `additionalProperties: false` lacks `required` (#35528).
- **Image‑input regressions** – Several reported failures in image‑upload paths across custom providers (#33542) and MiniMax‑M3 via proxy (#34596).
- **Credential & OAuth friction** – Manual setup of static credentials, retired endpoints (#27764), and lack of integrated credential chains cause setup overhead.

---
*Generated from GitHub data for `anomalyco/opencode` on 2026‑09‑05.*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-05

## Today's Highlights
Release **v0.85.0** introduces persistent Claude thinking effort for Anthropic transports, while the community actively patches a critical packaging defect that breaks fresh installs. New provider integrations (Amazon Bedrock Mantle, Meta, OrcaRouter) and UX refinements (Alt‑accelerated scrolling, macOS Cmd+V image paste) advance the project’s extensibility and polish.

---

## Releases
- **v0.85.0**  
  New Feature: **Persistent Claude thinking effort** — Supported Anthropic transports preserve per‑turn effort and recover safely from signed‑thinking mismatches.  
  [Model Configuration](https://github.com/earendil-works/pi/blob/v0.85.0/packages/coding-agent/docs/models.md#model-configuration)

---

## Hot Issues
*Selected for impact, community engagement, and recurrence.*

1. **#5363** [OPEN] Add amazon‑bedrock‑mantle provider for OpenAI‑compatible models – 18 comments, 15 👍  
   *Why it matters:* Expands AWS Bedrock coverage to OpenAI‑compatible Mantle models, addressing a growing need for multi‑provider flexibility.  
   [Link](https://github.com/earendil-works/pi/issues/5363)

2. **#7730** [OPEN] High CPU usage on Mac OS with long session – 15 comments, 10 👍  
   *Why it matters:* Performance regression causing CPU swings of 50‑110% and 600‑800 MB memory usage; affects Mac users during extended sessions.  
   [Link](https://github.com/earendil-works/pi/issues/7730)

3. **#5593** [OPEN] Tab‑completing a slash command inserts trailing space – 7 comments  
   *Why it matters:* Bug that breaks argument autocomplete flow, degrading CLI usability.  
   [Link](https://github.com/earendil-works/pi/issues/5593)

4. **#8896** [OPEN] `/export` HTML silently drops context that was sent to the model – 6 comments  
   *Why it matters:* Export functionality loses data, compromising reproducibility and debugging.  
   [Link](https://github.com/earendil-works/pi/issues/8896)

5. **#9052** [OPEN] Fullscreen mode’s fixed input box is great, but wheel scrolling is 3× slower than regular mode – 5 comments, 2 👍  
   *Why it matters:* UX regression in fullscreen mode that hampers navigation.  
   [Link](https://github.com/earendil-works/pi/issues/9052)

6. **#8760** [OPEN] OpenRouter `:free` models not work, fail with 400 — Pi sends `max_tokens` above provider limit – 5 comments  
   *Why it matters:* Provider compatibility issue that breaks free‑tier model usage across multiple Open

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-09-05

## 1. Today's Highlights

The most significant activity centers on the ongoing OpenTUI migration (#8662), with slash-command rendering and early-input race conditions now surfacing as tracked bugs. On the infrastructure side, CI is hitting a severe module-import cost wall (8 comments, #10908), and the team shipped a targeted Cerebras provider fix (#11049) alongside an HTML export bloat reduction (#11035).

---

## 2. Releases

**No releases in the last 24 hours.** The last release cycle remains active but nothing landed today.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#8662](https://github.com/QwenLM/qwen-code/issues/8662) | **Migrate TUI rendering layer from ink to OpenTUI** | The #1 structural UX undertaking — the current ink 7 + React 19 renderer has a 1037-line patch and fundamental flicker/Virtual Viewport problems that are intractable to fix within ink. This is the architectural keystone for every TUI improvement since. | 30 comments; tracked as the parent for multiple sub-issues including slash-command output (#10905) and early-turn input drops (#11046). |
| [#10908](https://github.com/QwenLM/qwen-code/issues/10908) | **CI test time bound by module import cost, not scheduling** | Release runs spend 2223s on `collect` vs 1372s on `tests` in the `cli` workspace. The bottleneck is deterministic and fixable, but blocks CI velocity for the whole project. | 8 comments; clearly resonates with the infra team — a direct performance-pain signal. |
| [#10932](https://github.com/QwenLM/qwen-code/issues/10932) | **Voice dictation rejects Token Plan ASR models** | Model Studio's Token Plan serves `qwen-audio-3.0-asr-flash`, but Qwen Code hardcodes legacy model IDs, gating a live customer-facing feature. | 5 comments; narrow scope bug with clear customer impact. |
| [#10872](https://github.com/QwenLM/qwen-code/issues/10872) | **Pluggable middleware for language-aware thinking output rewriting** | Would let integrators translate the model's English reasoning into the user's language before it hits the client — a growing demand from non-English developer communities. | 4 comments; design-discussion stage, notable for its cross-product relevance. |
| [#11031](https://github.com/QwenLM/qwen-code/issues/11031) | **Stop embedding Web Shell runtime in every HTML export** | Every exported HTML file is ~19.5 MB because React + WebShell runtime is duplicated per file. The fix (#11035) ships the runtime once from npm and loads it via unpkg. | 3 comments; clear win for export usability. |
| [#11045](https://github.com/QwenLM/qwen-code/issues/11045) | **Cerebras multi-turn requests fail with 400** | `reasoning_content` is non-standard on Cerebras; every turn after the first returns `400 status code (no body)`. Fix PR #11049 is already open. | 3 comments; provider-specific but affects a growing subset of users. |
| [#11063](https://github.com/QwenLM/qwen-code/issues/11063) | **Channel DELETE leaves orphaned workers when config is missing** | An explicit workspace-scoped channel delete returns `channel_instance_not_found` immediately if the persisted config is gone, but the daemon still owns the worker. Repeating DELETE cannot converge — a livelock. | 2 comments; daemon lifecycle correctness issue. |
| [#11060](https://github.com/QwenLM/qwen-code/issues/11060) | **Daemon promptId missing from active transcript** | The Daemon generates a stable `promptId` per prompt, but the live transcript projection omits it until the turn completes. Integration clients cannot correlate canonical history with the live journal during an active turn. | 2 comments; bilingual report (中文 + English); affects daemon integrators. |
| [#11019](https://github.com/QwenLM/qwen-code/issues/11019) | **AUTO mode: user approvals never reach the classifier** | A user answered "yes" three times to an `ask_user_question` prompt in an API-driven harness; each time the tool call was still blocked. Approval mode also reverts to AUTO on session rebuild. Security-relevant. | 2 comments; flagged P2; blocks production data-change workflows. |
| [#10984](https://github.com/QwenLM/qwen-code/issues/10984) | **Per-process user configuration directories** | Would let users run parallel Qwen Code processes with isolated config roots via `--config-dir`, equivalent to setting `QWEN_HOME` per-process rather than globally. | 3 comments; enables safer multi-tenant / CI scenarios. |

---

## 4. Key PR Progress

| # | PR | Description |
|---|----|-------------|
| [#11049](https://github.com/QwenLM/qwen-code/pull/11049) | **fix(core): strip `reasoning_content` from Cerebras requests** | Detects Cerebras hostnames in `determineProvider()` and removes the non-standard `messages[].reasoning_content` field at the outbound boundary — parity with the existing Mistral handling. Fixes #11045. |
| [#11035](https://github.com/QwenLM/qwen-code/pull/11035) | **fix(export): load transcript renderer from unpkg** | HTML exports now contain only transcript data + styles + a small bootstrap. The full React + WebShell renderer is built once per npm package and loaded at runtime, collapsing 19.5 MB exports to a fraction of that size. Addresses #11031. |
| [#11062](https://github.com/QwenLM/qwen-code/pull/11062) | **fix(daemon): persist prompt identity for active transcript replay** | Exposes `_meta.promptId` on transcript user updates before the turn settles, letting embedding clients correlate live-journal events with canonical history without timestamp guessing. Fixes #11060. |
| [#10943](https://github.com/QwenLM/qwen-code/pull/10943) | **feat(cli): start a background Agent View session with `--bg`** | `qwen --bg "<prompt>"` launches a background Agent View session, prints the session ID, and returns. The session outlives the originating shell; listable via `qwen sessions`. Part of a stacked PR series. |
| [#11054](https://github.com/QwenLM/qwen-code/pull/11054) | **feat(web-shell): add headless global turn navigation** | Phase 2A of session-wide turn navigation — introduces a bounded turn-index cache, immutable historical transcript page ranges, exact live/persisted turn locators, and provisional prompt reconciliation as a data layer. |
| [#11037](https://github.com/QwenLM/qwen-code/pull/11037) | **fix(core): coalesce concurrent `Config.initialize()` calls** | Previously a second caller during an in-flight initialize received `Config was already initialized`; now it awaits the same promise and returns the result. Fixes a real race in daemon startup. |
| [#10957](https://github.com/QwenLM/qwen-code/pull/10957) | **perf(cli): import core modules directly instead of the package root** | Teaches the CLI test runner to resolve individual sub-path imports, cutting module-import overhead that dominates CI `collect` time (addresses #10908). |
| [#11001](https://github.com/QwenLM/qwen-code/pull/11001) | **fix(test): wait for interactive PTY sessions to end during cleanup** | The test harness now blocks until each pseudo-terminal child has exited instead of signalling and moving on, eliminating flaky teardown races. |
| [#8927](https://github.com/QwenLM/qwen-code/pull/8927) | **feat(channels): bound session lifetime with `sessionRotation`** | Per-channel `sessionRotation` option supports `maxTurns` and time-based bounds; when a session exceeds its bound the next message on that route starts a fresh session. |
| [#10347](https://github.com/QwenLM/qwen-code/pull/10347) | **feat(core): auto-retry transient network errors (EOF) where Ctrl+Y is unavailable** | Wraps low-level network failures (e.g. `400 network error … EOF`) as retryable transport errors instead of fail-fast client errors. Critical for channel reliability. |

---

## 5. Feature Request Trends

1. **OpenTUI parity & terminal UX** — The single largest thematic cluster. Issues #8662, #10905, #11046, #9305 all feed into replacing the ink renderer and making the TUI production-grade.
2. **Daemon & channel lifecycle hygiene** — Orphan cleanup (#11063), prompt-ID persistence (#11060/#11062), worktree-scoped sessions (#11024/#11015), and session rotation (#8927) show a push toward robust long-running agent deployments.
3. **Extensibility middleware** — #10872 (thinking-output rewriting) and #10697 (workspace-scoped Skills runtime) reflect demand for pluggable hooks that work in both CLI and daemon modes.
4. **Session management & background execution** — `--bg` sessions (#10943), turn navigation (#11054), and per-process config (#10984) point to a need for non-interactive, embeddable Qwen Code workflows.
5. **Provider correctness** — Cerebras (`reasoning_content` strip, #11049) and Token-Plan ASR (#10932) fixes indicate the ecosystem is broadening beyond OpenAI-compatible endpoints.

---

## 6. Developer Pain Points

- **CI is import-bound, not parallelism-bound.** The `collect` phase dwarfs actual test execution (#10908). The team is attacking this from two angles: direct sub-path imports (#10957) and test-harness cleanup waits (#11001), but the root cause — monolithic package-entry imports — remains a structural drag.
- **OpenTUI migration exposes deep rendering bugs.** Slash-command output not reaching the screen (#10905), early-turn input drops (#11046), and VP bottom-alignment gaps (#9305) are all symptoms of a renderer still converging on parity. Expect these to surface iteratively through Batch 9 and beyond.
- **Daemon transcript replay is broken for active turns.** Missing `promptId` (#11060) means external clients cannot reconcile live journal events with canonical history while a turn is in-flight — a blocking issue for any tool built on top of the daemon.
- **Channel lifecycle edge cases leave state behind.** Orphaned workers after DELETE (#11063) and unoverridable approval blocks in AUTO mode (#11019) suggest the daemon's state machine needs more robust convergence guarantees, especially in programmatic/harness workflows.
- **Windows docs-local-preview workflow is non-functional.** Symlink creation without Developer Mode (#11055) is a documentation-gap pain point for Windows contributors.
- **HTML exports are prohibitively large.** 19.5 MB per file (#11031) is unusable for sharing or embedding; the unpkg-load fix (#11035) is eagerly awaited.
- **Provider support lags behind Model Studio model IDs.** Token-Plan ASR rejection (#10932) and Cerebras `reasoning_content` rejections (#11045) show that the provider allowlist and field-stripping logic need to keep pace with rapidly evolving model families.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-09-05

## 1. Today's Highlights

The community is focused on two major bug fixes: a token-budget regression for Ollama/local models (PR #5883 addresses the clamped 32K window, originally reported in #5820), and a transcript clutter issue where `todo_write` snapshots accumulated permanently in conversation history (PR #5873 closes #5871). Additionally, Dependabot continues steady dependency maintenance across Rust, npm, and GitHub Actions packages, while the team restored contributor CI baselines (PR #5882) to unblock ongoing evaluations.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Author | Why It Matters |
|---|-------|--------|----------------|
| #5820 | Ollama provider: input budget collapses to 1024 tokens on 32K local models | slowly247 | A critical correctness bug — the default output reservation of 64K silently clamps usable input to 1024 tokens on 32K-window models, effectively breaking local model usage. Open with 4 comments. [Link](https://github.com/Hmbown/DeepSeek-TUI/issues/5820) |
| #5860 | Continuous Self-Learning from Dialog (Automatic Skill Evolution) | Edouard-Legoupil | Proposes auto-extracting recurring problem patterns from conversation history into reusable Skills — a significant quality-of-life upgrade for power users who currently rely on manual `SKILL.md` curation. Open with 3 comments. [Link](https://github.com/Hmbown/DeepSeek-TUI/issues/5860) |
| #5871 | To-do list history clutters the transcript with no way to clear it | ronohara | Every `todo_write` snapshot persisted permanently in the transcript, creating an ever-growing "push-down history." Recently closed via PR #5873, but flagged significant UX frustration around context management. [Link](https://github.com/Hmbown/DeepSeek-TUI/issues/5871) |
| #5872 | Add rusty_alloc as an opt-in feature next to mimalloc | freedomlovesfrank | Lowers the barrier to Rust contribution by removing the C-compiler and build-script dependency for the allocator path, enabling easier cross-compilation. Open with 1 comment. [Link](https://github.com/Hmbown/DeepSeek-TUI/issues/5872) |
| #5866 | Key Ophthalmology CPT & ICD-10 Updates for 2026 | medicalbilling-usa | Appears to be off-topic promotional content; likely spam or misfiled. Closed. [Link](https://github.com/Hmbown/DeepSeek-TUI/issues/5866) |

---

## 4. Key PR Progress

| # | PR | Author | Summary |
|---|-----|--------|---------|
| #5883 | fix(tui): derive local output budget from route window | dajiaohuang | Fixes #5820 by deriving the automatic output reservation from a route's declared context window when no static catalogue row exists. Preserves explicit operator overrides, route output limits, and compatibility caps. Includes a synthetic 32K Ollama regression test. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5883) |
| #5873 | fix(tui): replace stale todo transcript snapshots | yiheng-kkk | Keeps only the newest successful `todo_write` snapshot in the visible transcript and hides empty current snapshots without clearing stored context. **Closed** — resolves #5871. [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5873) |
| #5882 | test: restore contributor CI baseline and process lifecycle checks | Hmbown | Restores working CI so unrelated PRs can be evaluated against a baseline. Fixes plugin lifecycle trust tokens, Windows symlink test gating, pointer assertions for the compact footer, and doc-comment formatting. **Closed.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5882) |
| #5870 | Fix: Tools — atomic commit splitting orders by dependency | goransh-walia | Addresses #3999 by ordering unrelated changes by dependency during atomic commit splitting and rejecting cycles. AI-assisted and syntax-validated. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5870) |
| #5881 | chore(deps): bump tower-http from 0.7.0 to 0.7.1 | dependabot[bot] | Routine Rust dependency bump in the HTTP middleware layer. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5881) |
| #5875 | chore(deps): bump base64 from 0.22.1 to 0.23.1 | dependabot[bot] | Routine Rust dependency bump for base64 encoding utilities. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5875) |
| #5876 | chore(deps): bump lru from 0.18.2 to 0.18.3 | dependabot[bot] | Routine Rust dependency bump for the LRU cache crate. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5876) |
| #5880 | chore(deps): bump jsonschema from 0.46.10 to 0.52.1 | dependabot[bot] | Major Python dependency bump for JSON Schema validation — cross-language dependency update. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5880) |
| #5877 | chore(deps): bump rmcp from 2.2.0 to 3.2.0 | dependabot[bot] | Significant bump in the Rust MCP SDK — may introduce API surface changes requiring review. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5877) |
| #5828 | chore(deps): bump npm_and_yarn group across 2 directories | dependabot[bot] | Updates `qs` and `fast-uri` in the Feishu bridge integration and VS Code extension directories. **Open.** [Link](https://github.com/Hmbown/DeepSeek-TUI/pull/5828) |

---

## 5. Feature Request Trends

- **Self-evolving knowledge base:** Issue #5860 reflects a growing demand for the agent to auto-learn and distill recurring patterns into reusable Skills, moving beyond static manual curation.
- **Local model budget transparency:** The #5820/5883 thread highlights the community's need for clear, model-window-aware token budget management — especially for local Ollama deployments where silent clamping is destructive.
- **Lower contributor friction:** Issue #5872 and PR #5882 both signal interest in reducing onboarding barriers — alternative allocators without C deps, and a reliable CI baseline for PR reviews.

---

## 6. Developer Pain Points

1. **Silent token-budget clamping:** The 32K input collapse to 1024 tokens on local Ollama models is a high-severity correctness issue that silently breaks workflows without clear error messaging.
2. **Transcript bloat from tool snapshots:** The `todo_write` accumulation bug (#5871) demonstrates how tool call history can degrade UX when not properly pruned — a recurring risk as more tools are added.
3. **CI instability blocking reviews:** The need to restore contributor CI baselines (PR #5882) suggests prior flakiness or misconfiguration was preventing community PRs from being evaluated, slowing contribution velocity.
4. **Dependency upgrade risk:** The large jump in `rmcp` (2.2.0 → 3.2.0, #5877) and `jsonschema` (0.46.10 → 0.52.1, #5880) represent major version leaps that carry breaking-change risk and require careful review.

---

*Digest generated from GitHub data for 2026-09-05. Repo: [Hmbown/DeepSeek-TUI](https://github.com/Hmbown/DeepSeek-TUI)*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*