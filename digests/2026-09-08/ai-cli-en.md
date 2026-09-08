# AI CLI Tools Community Digest 2026-09-08

> Generated: 2026-09-08 04:06 UTC | Tools covered: 10

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
**Date: 2026-09-08**

---

## 1. Ecosystem Overview

The AI CLI tool landscape in September 2026 is characterized by rapid iteration on agent reliability, expanding provider ecosystems, and growing maturity in session management and extensibility. Community-driven bug reporting has become a dominant signal of tool health, with capacity/rate-limit issues, session persistence bugs, and cross-platform regressions emerging as shared pain points. Tools are diverging in strategy: some (Codex, Pi) are investing in voice and multi-modal interaction, while others (Gemini CLI, Kimi Code) are tightening security and sandboxing, and open-source projects (OpenCode, Qwen Code) are emphasizing local-model compatibility and self-hosting. The ecosystem is maturing from prototype-phase experimentation toward production-grade reliability expectations.

---

## 2. Activity Comparison

| Tool | Open Issues | Closed PRs (24h) | Open PRs (24h) | Release (24h) |
|------|------------|-------------------|----------------|---------------|
| **Claude Code** | 10 (high: #16157, #91870, #59248) | 1 | 2 | None |
| **OpenAI Codex** | 10 | 11 | 0 | `rust-v0.154.0-alpha.6` |
| **Gemini CLI** | 10 | 5 | 5 | `v0.60.0-nightly.20260908` |
| **GitHub Copilot CLI** | 7+ (partial data) | 0 | 0 | None |
| **Kimi Code CLI** | 2 | 0 | 1 | None |
| **OpenCode** | 10 | 7 | 0 | None |
| **Pi** | 10 | 4 | 6 | None |
| **Qwen Code** | 10 | 9 | 0 | `v0.23.1-preview.2`, `v0.23.0-nightly`, `cua-driver-rs-v0.20.4` |
| **CodeWhale (DeepSeek TUI)** | 7 | 8 | 2 | `v0.9.13` |
| **Grok Build** | 0 | 0 | 0 | None |

*Issue counts reflect top-listed items; actual totals may be higher. PR counts based on digested data only.*

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Agent reliability & observability** | Gemini CLI, Claude Code, OpenCode, Qwen Code | Subagent failure visibility, tool-loop stability, auto-recovery from hangs, deterministic turn-limit handling |
| **Session management & persistence** | Claude Code, Codex, Pi, OpenCode, Copilot CLI | Cross-session history preservation, reliable resume, session-state sync across devices, compaction transparency |
| **Extensibility / plugin architecture** | Claude Code, Gemini CLI, OpenCode, Qwen Code | MCP server lifecycle optimization, composable skills, AST-aware tooling, project-scoped process pools |
| **Local / self-hosted model support** | OpenCode, Qwen Code, Pi | Ollama reasoning support, self-signed TLS, local LLM routing, provider-agnostic session headers |
| **Cost transparency & billing** | Claude Code, Qwen Code | Real-time token-usage visibility, model-output bounding, usage forecasting before plan upgrades |
| **Voice interaction** | Codex, Pi | WebRTC audio, configurable mute, live transcript display, voice-as-first-class-input |
| **Security hardening** | Gemini CLI, Codex, CodeWhale | Env-var leak prevention, sandbox filesystem isolation, truncated-tool-call rejection, Secure Enclave auth |

---

## 4. Differentiation Analysis

| Dimension | Tool(s) | Approach |
|-----------|---------|----------|
| **Provider model** | Claude Code, Codex, Pi | Proprietary model providers with tight integration; focus on premium subscription UX and capacity management |
| **Open / self-hosted** | OpenCode, Qwen Code, CodeWhale | Provider-agnostic architectures; local model first-class support; plugin ecosystems open to community extension |
| **Voice-first** | Codex | Dedicated WebRTC pipeline, split-flap transcript UI, voice controls strip — treating voice as a parallel input modality |
| **Mobile pairing** | Kimi Code CLI | Build Remote Agent phone-pairing via `gbr/1` protocol for spectator/veto workflows — unique in the digest set |
| **IDE/plugin depth** | CodeWhale, Gemini CLI | CodeWhale has native VS Code extension with ACP schema; Gemini CLI pushes extension rollback safety and skill deduplication |
| **Workflow automation** | Qwen Code, Codex | Qwen Code emphasizes daemon sessions, cron/goal work, and web-shell visualization; Codex focuses on MCP pooling and project-scoped context |
| **Enterprise security** | Gemini CLI, CodeWhale | Gemini CLI leads with env-var sanitization, sandbox filesystem isolation, and deterministic redaction; CodeWhale addresses ACP schema compliance and truncated-call rejection |

---

## 5. Community Momentum & Maturity

| Tier | Tools | Rationale |
|------|-------|-----------|
| **High engagement, mature community** | Claude Code, Codex | Thousands of comments on top issues (#16157: 1,494 comments); rapid daily PR volume; structured community reporting |
| **Active iteration, growing community** | Pi, OpenCode, Gemini CLI | Strong PR cadence (Pi: 10 PRs, OpenCode: 7 closed PRs, Gemini: 10 closed PRs); clear feature-direction signals from issue clusters |
| **Steady development, niche focus** | Qwen Code, CodeWhale | Regular release cycle (Qwen: 3 artifacts, CodeWhale: v0.9.13); issues reflect power-user workflows rather than broad adoption |
| **Early-stage, low signal** | Kimi Code CLI, Grok Build | Minimal issue/PR volume; Kimi has 2 open issues with light engagement; Grok Build shows no activity |
| **Fragmented community** | GitHub Copilot CLI | High-severity issues (#4756, #4438) but partial digest data limits assessment; Windows session-archiving blocker suggests enterprise user friction |

---

## 6. Trend Signals

1. **Agent reliability is the #1 barrier to production adoption.** Across Gemini CLI, Claude Code, OpenCode, and Qwen Code, subagent failures, silent hangs, and tool-loop bugs dominate community frustration. Tools that solve deterministic subagent observability and recovery will gain significant trust.

2. **Cost opacity is eroding subscriber confidence.** Claude Code's #16157 (1,494 comments) and Qwen Code's #44 billing-trap issue signal that opaque token consumption and unexpected quota exhaustion are the most damaging UX failures in the ecosystem. Real-time cost visibility is becoming table-stakes.

3. **Local-model support is table-stakes for open-source tools.** OpenCode's Ollama reasoning fix, Qwen Code's llama-server sampler work, and Pi's Ollama Cloud support indicate that self-hosted model compatibility is no longer a niche feature but a core competitive differentiator.

4. **Security hardening is accelerating post-hallucination-era.** Gemini CLI's env-var leak fixes, CodeWhale's truncated-tool-call rejection, and Codex's Secure Enclave auth reflect an industry shift from "agent capabilities first" to "agent safety baseline." Truncated-argument execution and env-var leakage are being treated as P0 issues.

5. **Session management is the new competitive frontier.** From Pi's session-resume UX fixes to Codex's Guardian context centralization to OpenCode's undo/redo reliability, the ability to manage long-running, multi-turn, cross-device sessions reliably is emerging as the key differentiator between prototype tools and production-grade agents.

6. **Voice as a first-class modality is being validated by OpenAI.** Codex's WebRTC voice pipeline with split-flap transcripts and configurable controls signals that voice input is moving from novelty to parity with text — a signal worth watching for ecosystem-wide adoption.

---

*Report generated from 2026-09-08 community digests. Data reflects publicly available issue and PR information per tool repository.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
**Data as of 2026-09-08 · Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

### 1. `skill-creator` eval pipeline fixes — PR [#1298](https://github.com/anthropics/skills/pull/1298)
**Status:** Open | **Functionality:** Fixes `run_eval.py`, `run_loop.py`, and `improve_description.py` — the core toolchain for evaluating and iterating on skill descriptions. Without these fixes, every skill description optimization loop converges on noise (0% recall reported regardless of content). Also fixes Windows stream reading, trigger detection, and parallel worker bugs.
**Highlights:** Root cause traced back to a cascading series of issues (#556, #1099, #1050); affects the entire skill-authoring workflow.

### 2. `document-typography` — PR [#514](https://github.com/anthropics/skills/pull/514)
**Status:** Open | **Functionality:** Prevents orphan line-wraps, widow paragraphs, and numbering misalignment in AI-generated documents. Triggers on any document-generation request.
**Highlights:** Fills a gap — Claude frequently produces documents with poor typographic quality but users rarely specify it.

### 3. `testing-patterns` — PR [#723](https://github.com/anthropics/skills/pull/723)
**Status:** Open | **Functionality:** Comprehensive testing skill covering the Testing Trophy model, AAA pattern, React component testing with Testing Library, edge cases, and what *not* to test.
**Highlights:** Broad coverage across unit, component, and integration testing; addresses a frequently requested domain.

### 4. `ODT` — PR [#486](https://github.com/anthropics/skills/pull/486)
**Status:** Open | **Functionality:** Create, fill, read, and convert OpenDocument Format files (`.odt`, `.ods`). Triggers on mentions of ODT/ODS/ODF/LibreOffice.
**Highlights:** Expands document-format support beyond the existing PDF/DOCX skill family.

### 5. `mcp-builder` eval update — PR [#1724](https://github.com/anthropics/skills/pull/1724)
**Status:** Open | **Functionality:** Updates `evaluation.py` default model to `claude-sonnet-5`, replacing the outdated `claude-3-7-sonnet` snapshot in both code and documentation.
**Highlights:** Keeps the MCP evaluation harness in sync with current model availability.

### 6. `skill-quality-analyzer` & `skill-security-analyzer` — PR [#83](https://github.com/anthropics/skills/pull/83)
**Status:** Open | **Functionality:** Two meta-skills that evaluate other skills across five dimensions (structure, documentation, examples, security, etc.) with weighted scoring.
**Highlights:** Community-built tooling for skill self-auditing; directly responsive to security concerns (see Issue #492).

### 7. `frontend-design` clarity pass — PR [#210](https://github.com/anthropics/skills/pull/210)
**Status:** Open | **Functionality:** Revisions to improve actionability, coherence, and precision of the `frontend-design` skill so Claude can follow instructions within a single conversation.
**Highlights:** Addresses Issue #202 criticism that skill-creator reads like documentation rather than executable guidance.

### 8. `Hivemind` multi-agent orchestration — PR [#1628](https://github.com/anthropics/skills/pull/1628)
**Status:** Open | **Functionality:** Delegates mechanical work to headless `opencode` workers on free models while Claude Code remains the sole planner/reviewer/merger.
**Highlights:** Novel approach to cost-aware agent orchestration — context is the scarce resource, not intelligence.

---

## 2. Community Demand Trends

From the most-discussed issues, the dominant demand directions are:

| Trend | Evidence |
|---|---|
| **Security & trust boundaries** | Issue #492 (43 comments): community skills impersonating official Anthropic skills under the `anthropic/` namespace; calls for namespace hygiene and verification |
| **Org-wide skill sharing** | Issue #228 (16 comments, 8 👍): demand for built-in organizational skill libraries instead of manual file distribution |
| **Context window management** | Issue #1487: `claude-api` skill injects ~156k tokens eagerly; users want on-demand, selective injection |
| **Quality gates & reasoning verification** | Issue #1385 / PR #1367: demand for pre-task calibration, adversarial review, and delivery-verification pipelines |
| **Cross-platform skill evaluation** | Issue #556 (12 comments, 7 👍): `run_eval.py` never triggers skills, breaking the optimization loop |
| **Agent governance & safety patterns** | Issue #412: skill for policy enforcement, threat detection, trust scoring, and audit trails |

---

## 3. High-Potential Pending Skills

These PRs have active discussion and address clear community needs; likely to land soon:

- **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — `skill-creator` eval pipeline: foundational fix that unblocks the entire skill-improvement loop.
- **[PR #1724](https://github.com/anthropics/skills/pull/1724)** — `mcp-builder` model update: keeps evaluation harness current; low-risk, high-utility.
- **[PR #539](https://github.com/anthropics/skills/pull/539)** — `skill-creator` YAML validation: prevents silent description truncation from unquoted special characters.
- **[PR #1602](https://github.com/anthropics/skills/pull/1602)** — `mcp-builder` evaluation serialization fix: resolves 0/N scoring bug against real MCP servers.
- **[PR #541](https://github.com/anthropics/skills/pull/541)** — `docx` tracked-change ID collision fix: prevents document corruption when bookmarks already exist.
- **[PR #1627](https://github.com/anthropics/skills/pull/1627)** — `buffer-api` Agent Skill: portable social-scheduling skill via GraphQL, cross-agent compatible.
- **[PR #1615](https://github.com/anthropics/skills/pull/1615)** — `scnet-hpc` skill: HPC cluster orchestration via profile-based SSH/Slurm workflows.
- **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit skill with mechanical verification + four-dimension reasoning quality gate.

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **trustworthy, evaluatable skill infrastructure** — not just new domain skills, but the tooling and security guarantees (namespace hygiene, eval pipelines, context-window controls, and quality gates) needed to make skills reliable at scale.

---



# Claude Code Community Digest — 2026-09-08

## 1. Today's Highlights

The dominant concern this cycle is runaway token consumption on Max subscriptions, with issue #16157 (1,494 comments, 694 upvotes) detailing instant usage-limit exhaustion on the Max plan. Meanwhile, a critical data-loss bug (#59248) exposes users to silent transcript deletion with no opt-in or recovery path. On the feature front, Function Hooks (#91870) continue to generate strong community interest as a pathway to deeper plugin extensibility.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#16157](https://github.com/anthropics/claude-code/issues/16157) | Instantly hitting usage limits with Max subscription | 1,494 | 694 | **The highest-engagement issue in the repo.** Max-tier subscribers report immediate quota exhaustion, suggesting a billing or token-calculation regression. Community frustration is extreme. |
| [#91870](https://github.com/anthropics/claude-code/issues/91870) | Function Hooks — make plugins 10x more powerful | 137 | 83 | Proposed hook system using side-effect tracking and a continuation-based `next` model (Express/Koa-style). Could fundamentally expand the plugin ecosystem if adopted. |
| [#59248](https://github.com/anthropics/claude-code/issues/59248) | Silent retention cleanup deletes session transcripts | 42 | 32 | **Data-loss risk.** Old conversation transcripts are silently purged with no warning, opt-in, or recovery — directly threatening users who rely on session history. |
| [#91623](https://github.com/anthropics/claude-code/issues/91623) | Max 20x plan drained in ~22 hours after Fable 5.1 | 5 | 5 | Fable 5.1 emits ~2× the output per turn vs. Fable 5, causing unexpectedly rapid credit burn. Echoes the broader cost concerns of #16157. |
| [#26951](https://github.com/anthropics/claude-code/issues/26951) | Plugin install fails with HTTP 404; plugins.claude.ai does not resolve | 22 | 16 | DNS/infrastructure issue blocking plugin installation on macOS — blocks a core onboarding flow. |
| [#89467](https://github.com/anthropics/claude-code/issues/89467) | Windows: app window always-on-top, no disable option | 19 | 28 | UX regression on Windows desktop; no setting or shortcut to toggle, disrupting multi-window workflows. |
| [#33041](https://github.com/anthropics/claude-code/issues/33041) | Remote Control disconnects frequently | 13 | 29 | Auto-disconnect every few minutes makes Remote Control unreliable for production use. |
| [#92016](https://github.com/anthropics/claude-code/issues/92016) | Desktop auto-denies CLI SendMessage, breaking subagent resumption | 19 | 5 | Regression: Claude Desktop on macOS rejects the `SendMessage` tool used by CLI-native subagent handoff, breaking multi-session workflows. |
| [#66540](https://github.com/anthropics/claude-code/issues/66540) | Windows: terminal windows flash on every subprocess spawn | 13 | 6 | Each MCP/tool/subagent spawn flashes a visible terminal — extremely disruptive with multiple concurrent sessions. |
| [#92737](https://github.com/anthropics/claude-code/issues/92737) | Claude ran rm -rf on source photos before verifying move | 1 | 0 | **Severe safety incident.** A `rm -rf` was executed on irreplaceable personal photos before the move was confirmed, exposing gaps in tool-execution guardrails. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#26175](https://github.com/anthropics/claude-code/pull/26175) | fix: replace broken native installer bootstrap script | Closed | The `curl ... \| bash` bootstrap silently failed to create `~/.local/bin/claude` and deleted the user's existing npm install as "cleanup," leaving no working `claude` binary. A replacement was merged. |
| [#39043](https://github.com/anthropics/claude-code/pull/39043) | Remove "retro-futuristic" recommendation from Frontend Design Skill | Open | Removes a dated aesthetic recommendation from the bundled Frontend Design skill. |

*No other open PRs in the last 24 hours.*

---

## 5. Feature Request Trends

- **Plugin extensibility:** Function Hooks (#91870) and the request for MCP servers to replace the auto-memory backend (#48465) signal strong demand for deeper, composable plugin architectures.
- **Session portability & history preservation:** Multiple issues (#59248, #89831, #92734) converge on the need for transparent session lifecycle management — opt-in compaction, visible dropped-content records, and reliable web↔local teleport handoffs.
- **Desktop UX controls:** Requests for controllable window behavior (#89467), custom keybindings in the chat composer (#89673), and remote-control stability (#33041) reflect growing desktop-user expectations for parity with editor-grade UX.
- **Cost transparency:** #16157 and #91623 highlight a clear community demand for real-time cost visibility, model-output bounding, and clearer usage-forecasting before plan upgrades.

---

## 6. Developer Pain Points

1. **Uncontrolled spending / quota exhaustion** — The single largest pain point. Max-tier and 20x-plan users report unexpectedly rapid credit depletion, attributed to Fable 5.1's higher output volume and opaque billing.
2. **Data loss risk** — Silent transcript cleanup (#59248) and unsafe tool execution patterns (#92737) erode trust in the tool's safety guarantees for production and personal workflows.
3. **Windows desktop regressions** — Always-on-top behavior (#89467), terminal flashing on subprocess spawns (#66540), and keybinding modifier stripping (#92771) create a consistently poor Windows desktop experience.
4. **Remote Control reliability** — Frequent disconnects (#33041) and broken session handoffs after stealth updates (#92010) make Remote Control unusable for sustained workflows.
5. **Infrastructure / DNS instability** — Plugin registry resolution failures (#26951) and MCP shared-pool readiness timeouts (#92758) indicate platform-layer fragility affecting onboarding and plugin ecosystems.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-09-08

## 1. Today's Highlights

The Codex community is wrestling with a widespread "Selected model is at capacity" outage affecting GPT-5.5, GPT-5.6-Sol, and GPT-6 Astra across both CLI and Desktop clients, sparking dozens of reports in the last 24 hours. On the development front, the team shipped a significant voice-conversation overhaul to the TUI, introducing live WebRTC audio, split-flap transcript animations, and a dedicated voice controls strip, while also adding macOS Secure Enclave user verification. A new alpha release, `rust-v0.154.0-alpha.6`, landed alongside ongoing work on Guardian context centralization and tmux resize recovery.

---

## 2. Releases

**rust-v0.154.0-alpha.6** — Latest alpha for the Codex CLI runtime. No detailed changelog was published alongside this alpha; see the full release history for prior notes.
- [Release](https://github.com/openai/codex/releases)

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#28507](https://github.com/openai/codex/issues/28507) | Selected model is at capacity | The most upvoted open issue (46 👍, 46 comments). A Pro 5x user on Windows reports persistent capacity errors, signaling a systemic scaling or routing problem. | 🔥 Top-voted open issue; strong community resonance. |
| [#43398](https://github.com/openai/codex/issues/43398) | GPT-5.5/5.6-Sol/6-Astra all failing with capacity errors | Multiple models on a Pro 20x Ubuntu CLI install are all returning the same capacity error, suggesting a platform-wide backend issue rather than per-model throttling. | 7 👍, raised Sep 7 — part of a wave of duplicate reports. |
| [#43337](https://github.com/openai/codex/issues/43337) | Account-specific capacity errors despite available weekly allowance | A Pro 20x user on macOS Apple Silicon reports that `gpt-6-astra` and `gpt-5.6-luna` both fail with capacity errors even though their weekly allowance is fully available. Points to account-level rate-limit logic bugs. | Raised Sep 7; 0 👍 but technically detailed. |
| [#43682](https://github.com/openai/codex/issues/43682) | All model selections fail with "Selected model is at capacity" | Confirms the issue is not model-specific — every selection returns the same error. Suggests a global capacity or auth-layer problem. | 2 👍, filed today. |
| [#25271](https://github.com/openai/codex/issues/25271) | Computer Use cannot determine Chrome URL on Windows | A long-standing Windows-specific bug (31 comments) where Codex Desktop's Computer Use feature fails to read the Chrome URL, even on `chrome://newtab/`. | 9 👍; persistent pain point for Windows Power Users. |
| [#20883](https://github.com/openai/codex/issues/20883) | Project-scoped MCP process pool instead of per-session | MCP servers are restarted per chat session instead of being pooled per project, wasting resources and breaking stateful tool connections. | 6 👍, 21 comments — a recurring architectural grievance. |
| [#33282](https://github.com/openai/codex/issues/33282) | `create_thread` does not inherit auto-approval mode for worktree tasks (Windows) | Worktree tasks on Windows lose auto-approval settings when spawned via `create_thread`, forcing manual intervention. | 6 👍; impacts automated CI/worktree workflows. |
| [#17401](https://github.com/openai/codex/issues/17401) | `@include` directive for composable AGENTS.md | Allows modular AGENTS.md files via an `@path/to/file.md` directive resolved at instruction-assembly time. Highly requested for monorepo and team setups. | 21 👍 — strong, sustained interest. |
| [#38357](https://github.com/openai/codex/issues/38357) | Cloud Browser provisioning failure on ChatGPT Pro (Germany) | Cloud Browser fails to provision for a Pro user in Germany, blocking a key paid feature. | 0 👍 but significant for affected enterprise users. |
| [#37539](https://github.com/openai/codex/issues/37539) | Cloud Browser tab created but UI never surfaces (CDP timeout) | The backend returns a valid tab ID but the frontend panel never renders; CDP refresh checks time out. | 1 👍; web-based Cloud Browser users impacted. |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#43681](https://github.com/openai/codex/pull/43581) | Add live WebRTC voice conversations to the TUI | Feature-gated `/voice`, `/voice mute`, `/voice stop` commands with local WebRTC audio and app-server signaling. Shows live transcripts, conversation status, and mic/speaker levels. |
| [#43656](https://github.com/openai/codex/pull/43656) | Animate live voice transcripts with split-flap tiles | Renders live transcripts with a split-flap effect, black background, and speaker-colored character highlights. |
| [#43683](https://github.com/openai/codex/pull/43683) | Move voice controls into a dedicated composer strip | Gives voice controls their own strip above the footer, preventing truncation at narrow widths while keeping the status line visible. |
| [#43690](https://github.com/openai/codex/pull/43690) | Make the voice mute shortcut configurable | Wires `tui.keymap.chat.toggle_voice_mute` into runtime keybindings and the keymap picker, replacing the hard-coded `Ctrl+X`. |
| [#43624](https://github.com/openai/codex/pull/43624) | Add macOS user verification with Secure Enclave signing | Enables native biometric-protected credential verification on macOS, fixing the previous "unsupported provider" error. |
| [#43622](https://github.com/openai/codex/pull/43622) | Warn when the connected Codex service is older than the CLI | Shows an older-service notice at startup and reconnect when both versions are official stable releases, with compact fallback for small terminals. |
| [#43603](https://github.com/openai/codex/pull/43603) | Recover missed tmux resize notifications in the TUI | Adds a background size monitor for tmux on Unix that checks terminal dimensions every 500 ms, fixing stale-dimension bugs. |
| [#43595–#43602](https://github.com/openai/codex/pulls?q=is%3Apr+is%3Aclosed+author%3Acopyberry%5Bbot%5D+created%3A2026-09-07) | Centralize Guardian context registry | A coordinated set of PRs moves trusted-tool metadata, trusted-skill evidence, REPL evidence, image selection, and prior-review rendering into `codex-guardian-context` as dedicated async/sync context sections. |
| [#43645](https://github.com/openai/codex/pull/43645) | Expand TUI regression coverage for realtime voice | Adds app-to-RPC tests for voice startup, shutdown, thread switching, speech delivery, session retries, and typed/voice handoff using a recording app server without audio hardware. |
| [#43576](https://github.com/openai/codex/pull/43576) | Group adjacent computer actions in the TUI | Renders adjacent `cua_repl` calls as a compact "Using computer" / "Used computer" group with action and failure counts, prioritizing failures and screenshots in completed previews. |

---

## 5. Feature Request Trends

- **Modular prompt context**: The `@include` directive for AGENTS.md ([#17401](https://github.com/openai/codex/issues/17401), 21 👍) reflects sustained demand for composable, team-shareable instruction files.
- **MCP lifecycle optimization**: The request for a project-scoped MCP process pool ([#20883](https://github.com/openai/codex/issues/20883)) signals that users are running heavier MCP workloads and hit resource/stability limits with per-session spawning.
- **Event-driven background exec** ([#32188](https://github.com/openai/codex/issues/32188), 10 👍): Developers want the CLI to wake on background task completion rather than polling, reducing token waste and latency.
- **Host-side timestamps** ([#27203](https://github.com/openai/codex/issues/27203), 18 👍): A widely supported request for optional timestamps prefixed to every output block in the CLI TUI, generated at the UI layer rather than by the model.
- **Voice-first interaction**: The TUI voice PRs this week (WebRTC, split-flap transcripts, configurable mute) show the team is actively investing in voice as a first-class input modality alongside text.

---

## 6. Developer Pain Points

**1. Model capacity / rate-limit errors (critical, rising)**
A cluster of issues filed Sep 7–8 ([#28507](https://github.com/openai/codex/issues/28507), [#43398](https://github.com/openai/codex/issues/43398), [#43337](https://github.com/openai/codex/issues/43337), [#43682](https://github.com/openai/codex/issues/43682), [#43657](https://github.com/openai/codex/issues/43657), [#43649](https://github.com/openai/codex/issues/43649)) all report the same "Selected model is at capacity" error across multiple models (GPT-5.5, GPT-5.6-Sol, GPT-5.6-Luna, GPT-6-Astra) and platforms (Windows, macOS, Linux). This is the dominant pain point in the community right now.

**2. WebSocket and connectivity reliability on Windows CLI**
Two detailed reliability reports from the same author ([#43015](https://github.com/openai/codex/issues/43015), [#43022](https://github.com/openai/codex/issues/43022)) describe severe CLI stalls: 63+ MB image-history requests before compaction, WebSocket fallback overhead, and the idle watchdog tripping despite live Ping/Pong traffic. Windows loopback-only reproduction suggests a platform-specific transport bug.

**3. Cloud Browser instability**
Three issues ([#38357](https://github.com/openai/codex/issues/38357), [#37539](https://github.com/openai/codex/issues/37539), [#39950](https://github.com/openai/codex/issues/39950)) cover Cloud Browser provisioning failures, UI non-rendering with CDP timeouts, and handoff freezes — a pattern suggesting systemic browser-backend reliability problems.

**4. Windows Desktop quirks**
Persistent Windows-specific bugs include Computer Use URL detection failures ([#25271](https://github.com/openai/codex/issues/25271)), worktree auto-approval inheritance loss ([#33282](https://github.com/openai/codex/issues/33282)), Git LFS temp-copy leaks during repo refresh ([#34953](https://github.com/openai/codex/issues/34953)), a white-screen crash on launch ([#41871](https://github.com/openai/codex/issues/41871)), and a crash when closing the last Browser Use tab ([#43347](https://github.com/openai/codex/issues/43347)).

**5. Session and context management gaps**
Issues around experimental context management returning 404s on Pro ([#43194](https://github.com/openai/codex/issues/43194)), historical session loss after project re-add on Windows ([#43661](https://github.com/openai/codex/issues/43661)), and assistant replies missing from desktop history after mobile voice use ([#43267](https://github.com/openai/codex/issues/43267)) point to fragility in session state persistence and cross-device sync.

**6. Proxy and environment inheritance in Desktop**
The Node REPL not inheriting proxy environment on macOS ([#21713](https://github.com/openai/codex/issues/21713)) and Desktop reconnect loops caused by `markedStreaming=true` on restored turns ([#19690](https://github.com/openai/codex/issues/19690)) indicate ongoing sandbox/process-isolation bugs in the Desktop app.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-09-08

## 1. Today's Highlights

Gemini CLI shipped nightly **v0.60.0-nightly.20260908**, with three significant security patches merging today: a `GIT_*` env-var leak fix, a false 401-detection regression fix, and an extension-rollback bug that left backup dirs empty. Meanwhile, the community is pushing hard on agent reliability—subagent recovery after max-turns, generalist-agent hangs, and browser-agent failures on Wayland remain the most-discussed pain points.

---

## 2. Releases

### v0.60.0-nightly.20260908
**[Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.60.0-nightly.20260907.g85aca163f...v0.60.0-nightly.20260908.g85aca163f)**

Nightly build. No feature changelog published for this cycle; see closed PRs below for what shipped.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | A subagent that hits its turn limit silently reports `status: "success"` with `Termination Reason: "GOAL"`, masking the failure from the parent agent and making debugging nearly impossible. | 13 comments · 2 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Post-Execution Intent Routing | Proposes leveraging Gemini 3 models' native bash affinity through a sandboxing layer that doesn't require extra dependencies—key to unlocking safer, more capable codebase exploration. | 9 comments · 1 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | Simple tasks like folder creation cause the generalist agent to hang indefinitely; workaround is disabling sub-agents entirely. A serious UX breaker. | 8 comments · 8 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | Epic tracking whether AST-aware tools (reducing turn waste, improving codebase navigation) are worth the engineering investment. Directly impacts agent efficiency. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Users report the agent ignores custom skills and sub-agents unless explicitly prompted, undermining the entire extensibility model. | 6 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Auto Memory sends transcript content to the model *before* redaction, creating a privacy gap. Deterministic pre-context redaction is needed. | 5 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Sessions the extractor dismisses as low-signal remain unprocessed and resurface repeatedly, wasting cycles. | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck in "Waiting input" after completion | After running even trivial commands, the CLI shows the shell as still active and awaiting input—forces manual cancellation. | 4 comments · 3 👍 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Browser agent session takeover & lock recovery | Persistent browser sessions fail fast on lock conflicts instead of recovering, breaking long-running web automation workflows. | 4 comments |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | Linux users on Wayland hit a hard blocker: the browser agent terminates with `GOAL` without performing any work. | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#29008](https://github.com/google-gemini/gemini-cli/pull/29008) | Strip execution-affecting `GIT_*` env vars in `getSafeGitEnv` | ✅ Closed | Fixes [#29003](https://github.com/google-gemini/gemini-cli/issues/29003): three internal git call sites were only stripping `GIT_CONFIG_*` vars, leaking execution-affecting env from project `.env` files into git operations. |
| [#29242](https://github.com/google-gemini/gemini-cli/pull/29242) | Stop matching 401 as a substring in `isAuthenticationError` | 🔄 Open | `message.includes('401')` falsely matched port numbers, IDs, and line numbers containing "401", triggering spurious re-auth flows. Now uses precise error-code matching. |
| [#29005](https://github.com/google-gemini/gemini-cli/pull/29005) | Normalize `DEBUG` env var truthiness in sandbox | ✅ Closed | String values like `"false"` and `"0"` were inadvertently enabling debug features (port publishing, `--inspect-brk` pauses) in Docker/Podman sandboxes. |
| [#29004](https://github.com/google-gemini/gemini-cli/pull/29004) | Guard `formatTruncatedToolOutput` against non-positive `maxChars` | ✅ Closed | Negative `maxChars` caused `String.prototype.slice()` negative-index behavior, inflating truncated output to ~2× original size. |
| [#28995](https://github.com/google-gemini/gemini-cli/pull/28995) | Prevent output inflation on negative `maxChars` (duplicate fix) | ✅ Closed | Complementary fix for [#28620](https://github.com/google-gemini/gemini-cli/issues/28620) with the same root cause. |
| [#29166](https://github.com/google-gemini/gemini-cli/pull/29166) | Back up extension dir before update for rollback | 🔄 Open | `updateExtension` created an empty temp dir and on failure copied nothing back—rollback was a no-op. Now copies the extension into the temp dir before updating. |
| [#29214](https://github.com/google-gemini/gemini-cli/pull/29214) | Harden sandbox filesystem boundaries & isolate runtime state | 🔄 Open | Replaces host directory mounts with sanitized read-only config files, resolves symlinks during path checks, and decouples container environment from host config. |
| [#29239](https://github.com/google-gemini/gemini-cli/pull/29239) | Fix ghost text wrapping infinite loop at narrow widths | 🔄 Open | Fixes [#19985](https://github.com/google-gemini/gemini-cli/issues/19985): `getGhostTextLines` `while` loop could infinite-loop when word width exceeded input width at narrow terminal sizes. |
| [#29022](https://github.com/google-gemini/gemini-cli/pull/29022) | Retain `ask_user` questions in text history | ✅ Closed | New `ui.keepAskUserQuestionsInHistory` setting preserves answered questions in session history so users can review their choices after resuming. |
| [#29017](https://github.com/google-gemini/gemini-cli/pull/29017) | Dedupe symlinked/junctioned skill directories | ✅ Closed | Fixes [#28944](https://github.com/google-gemini/gemini-cli/issues/28944): symlinked `.gemini` → `.agents` dirs (common on Windows via `mklink /J`) caused skill deduplication errors. |

---

## 5. Feature Request Trends

Drawing from the open issues, three directions dominate community requests:

1. **Agent reliability & observability** — Users repeatedly want subagent failures to surface correctly (max-turns, hangs, Wayland crashes) and for subagent trajectories to be visible via `/chat share` [#22598](https://github.com/google-gemini/gemini-cli/issues/22598). The current "silent success" and "infinite hang" patterns erode trust.

2. **Memory system hardening** — Auto Memory issues [#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525), [#26516](https://github.com/google-gemini/gemini-cli/issues/26516) form a cluster: users want deterministic redaction before content enters model context, no infinite retry on low-signal sessions, and invalid patches to be quarantined rather than silently skipped.

3. **Extensibility that actually works** — Skills and sub-agents are ignored by the model unless explicitly prompted [#21968](https://github.com/google-gemini/gemini-cli/issues/21968), and AST-aware tooling [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) / bash affinity sandboxing [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) are requested to make the agent more capable natively rather than relying on fragile workarounds.

---

## 6. Developer Pain Points

**Subagent behavior is unpredictable and unobservable.** The top recurring frustrations are:

- **Silent false successes**: Subagents report `GOAL` success when they actually hit turn limits or crashed, making it impossible to distinguish real progress from failure [#22323](https://github.com/google-gemini/gemini-cli/issues/22323).
- **Infinite hangs**: The generalist agent and browser agent can hang indefinitely on simple tasks, with no timeout feedback to the user [#21409](https://github.com/google-gemini/gemini-cli/issues/21409), [#21983](https://github.com/google-gemini/gemini-cli/issues/21983).
- **Skills/sub-agents ignored**: The model defaults to not using custom skills or sub-agents even when they're directly relevant, requiring explicit user prompts to activate them [#21968](https://github.com/google-gemini/gemini-cli/issues/21968).

**Shell and session state get stuck.** Commands report completion but the CLI retains them as "awaiting input," and `/compress` state doesn't persist across sessions [#25166](https://github.com/google-gemini/gemini-cli/issues/25166), [#21335](https://github.com/google-gemini/gemini-cli/issues/21335).

**Security surface from env leaks.** Project `.env` files can leak `GIT_*` execution vars into git operations [#29008](https://github.com/google-gemini/gemini-cli/pull/29008), and Auto Memory processes transcripts before redaction [#26525](https://github.com/google-gemini/gemini-cli/issues/26525)—both are high-severity concerns for enterprise users.

**Platform-specific breakage.** Wayland browser agent failures [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) and symlinked skill directories on Windows [#29017](https://github.com/google-gemini/gemini-cli/pull/29017) indicate testing gaps across common developer environments.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026‑09‑08

## 1. Today's Highlights
The Copilot CLI community reports critical session‑management regressions in **v1.1.15** and **v1.0.83**, including Windows session‑archiving failures and MCP connection cancellations on resume. A high‑profile German‑keyboard input bug (Alt‑Gr + q) remains a usability concern, while experimental extension prototypes and installer improvements advance.

## 2. Releases
*No new releases in the last 24 h.*

## 3. Hot Issues
1. **#4756 [Windows session archiving required]**  
   Windows app requires archiving every idle project session before creating a new Local session. Blocks parallel local workflows and is the most up‑voted issue (👍 10).  
   [github/copilot‑cli#4756](https://github.com/github/copilot‑cli/issues/4756)

2. **#4438 [disable‑model‑invocation breaks skill discovery]**  
   A skill flagged `disable‑model‑invocation: true` becomes completely unreachable via the CLI’s `skill()` tool, undermining custom‑skill workflows. High engagement (👍 6, 4 comments).  
   [github/copilot‑cli#4438](https://github.com/github/copilot‑cli/issues/4438)

3. **#1999 [German keyboard @ input fails]**  
   Alt‑Gr + q produces no output, rendering the CLI unusable for German‑layout developers. Closed but updated as recently as 2026‑09‑07; community reaction strong (👍 2, 10 comments).  
   [github/copilot‑cli#1999](https://github.com/github/copilot‑cli/issues/1999)

4. **#4742 [Desktop app 1.1.15 blocks second Local session]**  
   Creating a new Local session while another is active fails with “This project already has an active Local workspace.” Regression affecting multi‑session workflows (👍 1, 7 comments).  
   [github/copilot‑cli#4742](https://github.com/github/copilot‑cli/issues/4742)

5. **#4017 [MCP OAuth for non‑first‑party servers fails silently]**  
   Remote MCP servers (e.g., Atlassian) using HTTP transport do not launch the deferred browser‑flow, leaving authentication stuck with no error. Community impact highlighted (👍 3, 3 comments).  
   [github/copilot‑cli#4017](https://github.com/github/copilot‑cli/issues/4017)

6. **#4753 [Session resume cancels in‑flight MCP connections]**  
   Resuming a session drops stdio MCP servers still initializing, causing them to be silently unavailable for the entire session. Noted as a regression from v1.0.82 (👍 1).  
   [github/copilot‑cli#4753](https://github.com/github/copilot‑cli/issues/4753)

7. **#1787 [Collapsible output sections per type]**  
   Feature request to collapse thinking, command

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-09-08

## 1. Today's Highlights

Two open issues landed in the last 24 hours, both flagged as bugs: one affecting Thai and other IME-based character input on Windows, and another involving an agent stuck in a repetitive Read-tool loop at version 0.41.0. A single open PR continues to advance remote-agent phone-pairing support via the `gbr/1` protocol. No new releases were published in the last 24 hours.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

**#2584 — Thai (and other IME-based) characters duplicated when typing in the prompt on Windows**
- **Author:** mgprona | **Created:** 2026-08-04 | **Updated:** 2026-09-07 | 👍 1 | 💬 1
- **URL:** [Issue #2584](https://github.com/MoonshotAI/kimi-cli/issues/2584)
- **Why it matters:** IME (Input Method Editor) support on Windows is a critical accessibility and usability concern for non-Latin-script users. Character duplication in the prompt severely degrades the typing experience and suggests a low-level event-handling bug in the CLI's input pipeline. The issue has lingered for over a month with minimal traction, signaling a gap in Windows-specific testing coverage.
- **Community reaction:** Light engagement (1 upvote, 1 comment); the niche scope likely limits visibility but the impact on affected users is high.

**#2637 — Agent stuck in repeated Read-tool loop, unable to emit intended Edit calls**
- **Author:** devalirzayev | **Created:** 2026-09-07 | **Updated:** 2026-09-07 | 👍 0 | 💬 0
- **URL:** [Issue #2637](https://github.com/MoonshotAI/kimi-cli/issues/2637)
- **Why it matters:** This is a functional-correctness bug in the agent loop at version 0.41.0. An agent that cannot transition from Read to Edit calls is effectively broken for any workflow requiring file modifications — the core value proposition of the tool. Early report with no community engagement yet; likely to gain traction as more users upgrade to 0.41.0.
- **Community reaction:** No reactions yet; fresh report awaiting confirmation.

## 4. Key PR Progress

**#2616 — Add Build Remote Agent phone pairing (gbr/1)**
- **Author:** LinespottingPrivate | **Created:** 2026-08-23 | **Updated:** 2026-09-07 | 👍 0
- **URL:** [PR #2616](https://github.com/MoonshotAI/kimi-cli/pull/2616)
- **What it does:** Introduces **Build Remote Agent** as a pairing device for the desktop agent, enabling a paid iOS/Android app to spectate (and optionally inject into) the local CLI session. The protocol used is the free MIT-licensed `gbr/1`, implemented via [`gbr-agent`](https://github.com/LinespottingOrg/GrokBuildRemote-Agents). The phone acts as a spectator with veto power — not full orchestration — keeping the desktop agent in control.
- **Significance:** This is the only PR activity in the window and represents an expanding ecosystem-integration direction: connecting the desktop CLI to mobile companion apps for remote observation and light intervention.

## 5. Feature Request Trends

- **IME and multi-script input support:** Issue #2584 highlights an ongoing need for robust non-Latin character input, particularly on Windows. This aligns with a broader trend in developer-tool communities toward inclusive input-method support.
- **Remote / mobile pairing:** PR #2616 signals community interest in extending the CLI beyond the local terminal — phone pairing for spectator and veto modes reflects a demand for hybrid desktop-mobile agent workflows.
- **Agent loop reliability:** Issue #2637 underscores a demand for stable tool-calling behavior (Read → Edit transitions), suggesting the community prioritizes agent correctness over new features at this stage.

## 6. Developer Pain Points

1. **Windows IME character duplication** — A persistent, high-impact bug for Thai and other IME-based language users. The month-long open status with minimal response suggests insufficient Windows regression testing in the release pipeline.
2. **Agent tool-loop stability** — The Read-loop bug in #2637 points to a deeper concern: as the agent's capabilities expand (new tools, more complex workflows), ensuring reliable state transitions between tools remains a fragile area. This is likely to recur as the toolset grows.
3. **Low community engagement on bugs** — Both issues have minimal upvotes and comments, which may reflect a smaller active community or a discovery problem. Developers relying on the CLI for production work may find it hard to gauge bug severity from community signals alone.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑09‑08

## 1. Today's Highlights
OpenCode developers are focusing on **reasoning persistence** and **local‑model compatibility**, with three bug‑fix PRs addressing Ollama reasoning support, reasoning loss across empty tool‑call deltas, and LongCat thinking‑variant mapping. Community engagement is high around **undo/redo reliability** and **clipboard behavior on Linux**, both now closed, while new integrations (Poe OAuth, Alibaba Cloud, Z.AI) and desktop SSH capabilities expand the platform’s reach.

## 2. Releases
*No new releases were published in the last 24 hours.*

## 3. Hot Issues
| # | Issue | Why It Matters | Community Reaction |
|---|-------|----------------|---------------------|
| [#4704](https://github.com/anomalyco/opencode/issues/4704) | `/undo` and `/timeline` undo does not revert file edits | Core undo functionality fails even in git‑tracked projects, breaking expected recovery workflows. | 23 comments, 22 👍 — **CLOSED** |
| [#24713](https://github.com/anomalyco/opencode/issues/24713) | Copy shows “copied” popup but clipboard remains unchanged on Linux terminal | Clipboard feedback is misleading; paste operations silently fail on Linux. | 12 comments, 8 👍 — **CLOSED** |
| [#12938](https://github.com/anomalyco/opencode/issues/12938) | Subagents can't use `todowrite` tool | Subagent tool access is broken despite explicit activation in the agent’s md file. | 8 comments, 5 👍 — **CLOSED** |
| [#18021](https://github.com/anomalyco/opencode/issues/18021) | Evaluate upstreaming native A2A (Agent‑to‑Agent) support | Shows strong interest in native multi‑agent protocol integration; a working prototype was provided. | 7 comments, 4 👍 — **CLOSED** |
| [#35365](https://github.com/anomalyco/opencode/issues/35365) | Self‑signed TLS certificate no longer working with v1.17.12+ | Regression that blocks local HTTPS LLM servers with self‑signed certs; startup stalls for over a minute. | 4 comments, 0 👍 — **CLOSED** |
| [#47624](https://github.com/anomalyco/opencode/issues/47624) | TUI: question dialog keyboard trapped after switching tabs | Keyboard input becomes completely unresponsive in multi‑tab question dialogs, requiring a full restart. | 2 comments, 0 👍 — **OPEN** |
| [#47019](https://github.com/anomalyco/opencode/issues/47019) | Native infinite agent mode (auto‑continue until done, with limits) | Users managing long migrations need the agent to continue without manual “continue” prompts, with configurable stop limits. | 2 comments, 1 👍 — **OPEN** |
| [#36124](https://github.com/anomalyco/opencode/issues/36124) | `opencode.exe` on Windows fails to start with leaked build‑time path | A hardcoded Bun fs root (`B:\~BUN\root`) leaks into the production binary, causing immediate startup failure on Windows. | 2 comments, 0 👍 — **CLOSED** |
| [#36120](https://github.com/anomalyco/opencode/issues/36120) | Claude Opus 4.8 via GitHub Copilot doesn't show thinking | Thinking output is hidden for high‑complexity models when using the Copilot provider. | 2 comments, 1 👍 — **CLOSED** |
| [#34798](https://github.com/anomalyco/opencode/issues/34798) | Conversations hang after first response when provider returns a reasoning field | The AI‑SDK extracts the `reasoning` field and re‑sends it as `reasoning_content`, causing local Ollama/Qwen models to stall. | 3 comments, 1 👍 — **CLOSED** |

## 4. Key PR Progress
| # | PR | Description |
|---|-----|-------------|
| [#47883](https://github.com/anomalyco/opencode/pull/47883) | `feat(core): add Poe browser OAuth` | Ports Poe’s browser‑login flow (PKCE, state validation, loopback callback, API‑key exchange) to the V2 plugin system. |
| [#47881](https://github.com/anomalyco/opencode/pull/47881) | `fix(opencode): support local Ollama reasoning` | Fixes Ollama thinking models on the OpenAI‑compatible endpoint so they can select a reasoning effort. |
| [#47880](https://github.com/anomalyco/opencode/pull/47880) | `fix(session): preserve reasoning across empty tool‑call deltas` | Backports a Vercel AI fix that prevents reasoning from being lost when tool‑call deltas are empty. |
| [#45472](https://github.com/anomalyco/opencode/pull/45472) | `fix(websearch): remove provider whitelist` | Enables the client‑side `websearch` tool for **all** providers by default, removing the previous provider‑specific restriction. |
| [#46344](https://github.com/anomalyco/opencode/pull/46344) | `feat(app): collapsible reasoning cards` | Renders reasoning content as compact, collapsible cards in the UI, improving readability of long reasoning traces. |
| [#43681](https://github.com/anomalyco/opencode/pull/43681) | `fix(core): resolve Bedrock AWS profile credentials for V2` | Properly resolves explicit `region`, `credentials.region`, and `AWS_REGION` for Bedrock Converse/Mantle, failing with a clear `AIError` when invalid. |
| [#47753](https://github.com/anomalyco/opencode/pull/47753) | `feat(desktop

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-09-08

---

## 1. Today's Highlights

Pi's community is buzzing around provider reliability: the long-running `openai-codex` streaming hang issue (#4945) continues to accumulate attention, while a cluster of new reports surface around aborted-stream handling and token-limit enforcement on OpenRouter free models. Meanwhile, several closed PRs land fixes for session resume UX, Orca terminal support, and Claude Fable 5 fallback cleanup.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4945](https://github.com/earendil-works/pi/issues/4945) | `openai-codex` / `gpt-5.5` TUI stuck on `Working…` | Core streaming reliability bug — interactive sessions hang with no visible error, requiring manual Escape. Repeated over multiple days. | 🔥 77 comments · 33 👍 — highest engagement across all open issues |
| [#7547](https://github.com/earendil-works/pi/issues/7547) | Windows usage survey & bug focus | Clarifies which Windows runtime paths (native, WSL, etc.) deserve core investment vs. community delegation. | 61 comments — active discussion on Windows prioritization |
| [#8823](https://github.com/earendil-works/pi/issues/8823) | Esc fails to cancel in-flight streaming | Pressing Escape only registers abort after the provider finishes naturally, causing wasted tokens and delayed cancellation. | 7 comments — directly affects agent-loop UX |
| [#8760](https://github.com/earendil-works/pi/issues/8760) | OpenRouter `:free` models return 400 | Pi sends `max_tokens` at the catalog limit, exceeding the provider's hard cap. Affects multiple free models. | 5 comments — practical bug with immediate workaround need |
| [#8684](https://github.com/earendil-works/pi/issues/8684) | `PI_OFFLINE` silently kills model discovery | Environment variable documented for update checks only, but in practice also disables all provider catalog discovery. | 6 comments — subtle but disruptive for offline-first workflows |
| [#8928](https://github.com/earendil-works/pi/issues/8928) | Parallel startup reports "No API key found" for ~48s | Expired OAuth credential for one provider triggers auth errors on the active provider during multi-process startup. | 4 comments — affects CI / orchestration setups |
| [#9055](https://github.com/earendil-works/pi/issues/9055) | `EventStream` quadratic CPU on drained buffer | Long-running server processes hit O(n²) cost from array `shift()` dequeue as the producer overtakes the consumer. | 4 comments — performance regression for agent-loop adopters |
| [#9267](https://github.com/earendil-works/pi/issues/9267) | Fuzzy session-search scan cost | Replaces O(n) char-by-char `fuzzyMatch()` with `String.indexOf()` to reduce session-list latency. | 3 comments · 1 👍 — already closed |
| [#6100](https://github.com/earendil-works/pi/issues/6100) | Compaction summary displays out of place after reload | UX inconsistency: compaction message jumps to top of conversation on session restore instead of remaining at its original position. | 3 comments — closed, UX polish |
| [#9290](https://github.com/earendil-works/pi/issues/9290) | `modelRegistry.complete()` missing `x-opencode-session` header | OpenCode AI enforcement of session headers breaks every extension call to opencode-go models. | 3 comments — closed, integration bug |

---

## 4. Key PR Progress

| # | PR | Type | Summary |
|---|-----|------|---------|
| [#9307](https://github.com/earendil-works/pi/pull/9307) | `fix(tui): recognize Orca terminal capabilities` | Fix | `[CLOSED]` Fixes OSC 8 hyperlink rendering on Orca terminal by recognizing `TERM_PROGRAM=Orca`. |
| [#9303](https://github.com/earendil-works/pi/pull/9303) | `fix(interactive): resume session before closing selector` | Fix | `[CLOSED]` Fixes silent selector disappearance on `/resume` by ensuring the session resumes *before* the selector closes. |
| [#9301](https://github.com/earendil-works/pi/pull/9301) | `feat(coding-agent): confirm device-code browser and clipboard actions` | Feature | `[OPEN]` Follow-up to #9282 — auto-opens browser and copies device code to clipboard for GitHub Copilot opt-in, without forcing it on other providers. |
| [#8635](https://github.com/earendil-works/pi/pull/8635) | `fix(ai): preserve aborted stop reason during lazy setup` | Fix | `[OPEN]` Fixes #8409 — abort signals now propagate through lazy stream setup wrappers, reporting setup failures as aborted when the request is already cancelled. |
| [#9297](https://github.com/earendil-works/pi/pull/9297) | `fix(ai): remove invalid Fable 5 fallback target` | Fix | `[OPEN]` Removes `claude-opus-4-8` from Fable 5's built-in `allowedFallbackModels` after the API started rejecting it with 400. |
| [#9253](https://github.com/earendil-works/pi/pull/9253) | `fix(ai): route Copilot GPT models through Responses` | Fix | `[CLOSED]` Fixes #9209 — routes GitHub Copilot GPT models through the Responses API instead of Completions, aligning with their current API surface. |
| [#9280](https://github.com/earendil-works/pi/pull/9280) | `feat: add implementation-backed documentation evals` | Feature | `[CLOSED]` Adds deterministic doc evals: generates implementation audits for every Markdown page in the coding-agent docs catalog. |
| [#9116](https://github.com/earendil-works/pi/pull/9116) | `feat(ai): add mid-conversation system messages` | Feature | `[OPEN]` First layer of a split allowing extensions to inject system messages mid-session without rewriting the entire prompt. |
| [#9117](https://github.com/earendil-works/pi/pull/9117) | `feat(coding-agent): deliver prompt and tool changes as system message deltas` | Feature | `[OPEN]` Second layer — wires the coding agent to deliver tool/prompt loadout changes as system message deltas instead of full prompt rewrites. |
| [#7742](https://github.com/earendil-works/pi/pull/7742) | `feat(ai): Ollama Cloud support` | Feature | `[OPEN]` Adds Ollama Cloud as a first-class provider using `OLLAMA_API_KEY`, with hybrid local/cloud connectivity preserved. |

---

## 5. Feature Request Trends

1. **Better abort/cancellation semantics** — Multiple issues (#8823, #8635, #9306) report that in-flight requests are not reliably cancelled, leaving orphaned tool calls or delayed aborts. The community expects `Escape` and explicit aborts to immediately tear down network activity.

2. **Device-code login polish** — Issue #9282 and PR #9301 show demand for automatic browser-open and clipboard-copy during OAuth device-code flows, especially for corporate environments where manual navigation is friction-heavy.

3. **Mid-conversation configuration changes** — PRs #9116/#9117 address the need for extensions and the coding agent to inject system messages and tool-loadout changes without rewriting the full conversation history.

4. **Provider-specific header / routing fixes** — OpenCode session headers (#9290), Copilot Responses routing (#9253), and Fable fallback cleanup (#9297) reflect a trend of providers evolving their APIs and Pi needing to keep adapters in sync.

5. **Performance budgets** — Issues #9055 (quadratic EventStream) and #9267 (fuzzy search cost) show users running Pi as a headless SDK in long-lived processes care deeply about O(n) and memory scaling.

---

## 6. Developer Pain Points

- **Streaming hangs with no feedback:** The `openai-codex` / `gpt-5.5` `Working…` stall (#4945) is the most-reported pain point — users are stuck with no error, no streamed output, and no tool call, forcing manual intervention.
- **Windows fragmentation:** Issue #7547 highlights that Windows has too many valid runtime paths (native, WSL, various node versions), making it hard for the core team to prioritize fixes that actually reach users.
- **Environment variable scope ambiguity:** `PI_OFFLINE` (#8684) is documented narrowly but has undocumented side effects that silently break model discovery, confusing users who rely on it for offline-first or CI setups.
- **Token-limit mismatches on free tiers:** OpenRouter `:free` models (#8760) reject requests when Pi sends the catalog `maxOutputTokens`, a gap between Pi's model registry and actual provider limits.
- **Auth credential bleed in parallel runs:** Expired OAuth tokens for unused providers (#8928) cause 48-second auth errors during parallel startup, misleading users into thinking their active provider's credentials are broken.
- **Session-resume UX regressions:** PR #9303 confirms a prior issue where the session selector closed before the resume action completed, leaving users with no feedback — a regression in perceived reliability.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026‑09‑08

## 1. Today's Highlights
New preview releases **v0.23.1‑preview.2** and **v0.23.0‑nightly** ship a visual workflow‑run manager for web‑shell and a performance fix for session workflow projection. The community continues to push for a major TUI rewrite (ink → OpenTUI) while flagging a severe Windows process‑leak bug and local‑llama‑server sampler failures.

## 2. Releases
- **v0.23.1‑preview.2** & **v0.23.0‑nightly.20260907.f1ed3bc31a**  
  *feat(web‑shell): visualize and manage dynamic workflow runs* (#10594) and *perf(web‑shell): derive the session workflow project* once per render instead of three times.  
  🔗 [Release v0.23.1‑preview.2](https://github.com/QwenLM/qwen‑code/releases/tag/v0.23.1‑preview.2) | [Release v0.23.0‑nightly](https://github.com/QwenLM/qwen‑code/releases/tag/v0.23.0‑nightly.20260907.f1ed3bc31a)

- **cua‑driver‑rs‑v0.20.4**  
  Prebuilt binaries for macOS (codesigned/universal), Linux (x86_64+arm64), and Windows (unsigned UIAccess worker + native SDK).  
  🔗 [cua‑driver‑rs‑v0.20.4](https://github.com/QwenLM/qwen‑code/releases/tag/cua‑driver‑rs‑v0.20.4)

## 3. Hot Issues
| # | Title | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [8662](https://github.com/QwenLM/qwen‑code/issues/8662) | Migrate TUI rendering from ink to OpenTUI | Resolves flicker, Virtual‑Viewport gaps, and structural limits of the current ink+React 19 stack. | 33 comments – high‑interest architectural track. |
| [44](https://github.com/QwenLM/qwen‑code/issues/44) | 百炼收费陷阱 (Billing trap) | Highlights perceived lack of transparency in cloud‑inference costs. | 20 comments – strong user frustration. |
| [11119](https://github.com/QwenLM/qwen‑code/issues/11119) | Background shell output dropped when session runtime recycles | Breaks long‑running daemon‑hosted workflows; output and wake notifications are silently lost. | 10 comments – P1 bug affecting automation. |
| [8586](https://github.com/QwenLM/qwen‑code/issues/8586) | Track activeWork and background Agent recovery | Proposes a five‑layer health/reporting system so background agents can be recovered after foreground turn ends. | 9 comments – feature request with detailed spec. |
| [11303](https://github.com/QwenLM/qwen‑code/issues/11303) | Windows qwen‑cli leaks headless conhost.exe processes | After ~12 h, 347 leaked ConPTY processes hold ~2.8 GB RAM; critical resource leak on Windows. | 6 comments – ready‑for‑human, urgent platform fix. |
| [10530](https://github.com/QwenLM/qwen‑code/issues/10530) & [10435](https://github.com/QwenLM/qwen‑code/issues/10435) | 400 Failed to initialize samplers with local llama‑server | Regression since v0.22.3; certain models (Qwen 3.8 27b, Qwen 3.6 35b) fail to parse grammar, while gemma4‑12b works. | 6/5 comments – local‑inference pain point. |
| [10865](https://github.com/QwenLM/qwen‑code/issues/10865) | Session workflow projection derived three times per render | Performance regression; the same projection is rebuilt on every render, defeating the once‑per‑render index. | 5 comments – linked to recent web‑shell changes. |
| [10684](https://github.com/QwenLM/qwen‑code/issues/10684) | First‑class self‑hosted semantic memory | Users want embedding‑based recall and timestamped cross‑session memory beyond the current keyword/title‑based auto‑memory. | 4 comments – clear demand for memory upgrade. |
| [7167](https://github.com/QwenLM/qwen‑code/issues/7167) | Fleet Shepherd Dashboard | Bot‑maintained CI/CD health dashboard; shows last tick, syncs, dispatches, releases, cleanups. | 3 comments – internal ops visibility. |
| [11272](https://github.com/QwenLM/qwen‑code/issues/11272) | Cancelling a long‑running stdio tool call kills the MCP server | In Channel deployments (e.g., DingTalk), canceling a slow tool permanently terminates the stdio server; unrecoverable in Channel mode. | 3 comments – reliability issue for external integrations. |

## 4. Key PR Progress
| # | Title | What It Does |
|---|-------|--------------|
| [9983](https://github.com/QwenLM/qwen‑code/pull/9983) | keep host‑trusted state out of container's writable surface | Moves lease files out of the bind‑mounted read‑write directory; stops host git from resolving through pointers inside the sandbox. |
| [10136](https://github.com/QwenLM/qwen‑code/pull/10136) | swap re‑review rounds to a fix‑audit shape | When a multi‑round `/review` is headed for the critical‑only posture, runs a narrowed fix‑audit shape instead of a full round. |
| [11322](https://github.com/QwenLM/qwen‑code/pull/11322) | cancel pending locate scroll timers on unmount | Prevents stale 150 ms scroll timers from firing after navigation; adds regression tests. |
| [10439](https://github.com/QwenLM/qwen‑code/pull/10439) | watch /resolve for consecutive failures | CI script files a tracking issue when the bot command fails in a row, updates it on changes, and closes it on success. |
| [11250](https://github.com/QwenLM/qwen‑code/pull/11250) | improve split‑view session navigation | Reuses sidebar popover for titles, adds header indicator for last‑interacted pane, and cycles through panes awaiting tool approval. |
| [10885](https://github.com/QwenLM/qwen‑code/pull/10885) | configure scheduled task model and group routing | Lets users choose per‑run model and session‑grouping (un分组, existing group, or named group) when a task creates a new session each run. |
| [11286](https://github.com/QwenLM/qwen‑code/pull/11286) | isolate protocol checks from model service in E2E tests | Makes ACP plan‑mode authorization and JSON‑output formatting tests deterministic by using the local OpenAI‑compatible test server. |
| [11302](https://github.com/QwenLM/qwen‑code/pull/11302) | remove heavy build/bundle from prepare hook | `prepare` now runs only `husky` and `npm run generate`; full build+bundle is no longer triggered on every install. |
| [11309](https://github.com/QwenLM/qwen‑code/pull/11309) | reap owned worktrees when daemon sessions are deleted | Deleting a daemon session that owns a worktree now also removes the checkout and its branch, with ownership‑chain validation. |
| [11196](https://github.com/QwenLM/qwen‑code/pull/11196) | journal failed agents and settle agent failures to null | Workflow resume journal now records agent‑level failures, distinguishing between a failed agent and an interrupted run. |

## 5. Feature Request Trends
- **Memory & Recall**: Strong push for semantic/embedding‑based memory (#10684) and structured on‑demand recall (#10183) to move beyond keyword‑title indexing.
- **Session & Daemon Management**: Requests for turn‑level navigation (#10750), explicit `activeWork` tracking with recovery paths (#8586), and proper handling of cron/goal work in session reclamation (#11118).
- **Configuration Flexibility**: Template variables in custom headers (`${session_id}`) (#10995), propagation

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# CodeWhale TUI Community Digest — 2026-09-08

## 1. Today's Highlights

CodeWhale v0.9.13 shipped after an intensive release cycle, addressing five recorded defects including a P0 offline-queue data-loss bug, an ACP schema violation breaking JetBrains integration, and a dangerous truncated-tool-call execution flaw. A significant multiline-paste regression from v9.12 was also resolved, alongside an IDE-stage-2 upgrade for the VS Code extension.

---

## 2. Releases

**v0.9.13** — Release preparation landed in [#6000](https://github.com/Hmbown/Codewhale/issues/6000), closing a batch of defects logged in [#5989](https://github.com/Hmbown/Codewhale/pull/5989). Key fixes included:

- **P0:** Offline queue no longer destroys concurrent sessions' unsent text
- **ACP schema:** `sessionCapabilities.list` now correctly advertised as an object, fixing JetBrains IDEA handshake failures
- **Metrics:** `tok/s` denominator and token-source audit
- **Truncated tool calls:** Engine now rejects (rather than repairs and executes) tool calls cut off by provider output limits
- **Goal-loop bound:** Added a goal-scoped step budget
- **Receipt integrity:** Session-id divergence now surfaced as a visible notice instead of a silent log line
- **Computer-use bundle:** Refreshed to plugin v0.2.0 with native macOS a11y backend

---

## 3. Hot Issues

| # | Title | Status | Why It Matters |
|---|-------|--------|----------------|
| [#5981](https://github.com/Hmbown/Codewhale/issues/5981) | Multiline paste split into separate messages (v9.12 regression) | ✅ Closed | Critical UX regression; fixed in [#5993](https://github.com/Hmbown/Codewhale/pull/5993). Bracketed-paste heuristic was incorrectly gated. |
| [#5969](https://github.com/Hmbown/Codewhale/issues/5969) | `serve --acp` initialize response violates ACP schema | ✅ Closed | Blocked JetBrains IDEA connection; fixed in [#5978](https://github.com/Hmbown/Codewhale/pull/5978). |
| [#5986](https://github.com/Hmbown/Codewhale/issues/5986) | Truncated tool call repaired and executed silently | ✅ Closed | Dangerous: a `write` could overwrite files with partial JSON. Fixed in [#5983](https://github.com/Hmbown/Codewhale/pull/5983). |
| [#5860](https://github.com/Hmbown/Codewhale/issues/5860) | Continuous self-learning from dialog (automatic skill evolution) | 🟢 Open | Could auto-extract recurring patterns into `SKILL.md` — a major quality-of-life upgrade for power users. |
| [#6004](https://github.com/Hmbown/Codewhale/issues/6004) | Hooks cannot observe session state (idle / fatal-error / waiting) | 🟢 Open | Extends the 11-hook event surface to cover session lifecycle states; important for automation tooling. |
| [#5991](https://github.com/Hmbown/Codewhale/issues/5991) | `allow_insecure_http` config key removed in v0.9.12 | ✅ Closed | Broke LAN/internal HTTP providers; restored in [#5995](https://github.com/Hmbown/Codewhale/pull/5995). |
| [#5950](https://github.com/Hmbown/Codewhale/issues/5950) | Bottom chrome (posture bar + metrics) not configurable | 🟢 Open | Users want `/statusline`-style control back; the v0.9.12 shell redesign hard-coded the bottom rows. |
| [#5994](https://github.com/Hmbown/Codewhale/issues/5994) | Goal/operate runs chopped by interactive `max_steps` | 🟢 Open | Goals are documented as unbounded but get truncated by a shared step counter — a real logic gap. |
| [#5975](https://github.com/Hmbown/Codewhale/issues/5975) | Model picker severely laggy; no per-column sort; mouse unsupported | 🟢 Open | Founder-reported perf issue on the `route · configured` picker with real catalogs. |
| [#6008](https://github.com/Hmbown/Codewhale/issues/6008) | Offload/swap operation for `/purge` (virtual-memory context eviction) | 🟢 Open | Extends context management beyond hard delete/compress — preserves potentially useful context for long sessions. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#6000](https://github.com/Hmbown/Codewhale/pull/6000) | `chore(release): prepare v0.9.13` | ✅ Closed | Release prep; bumps version across workspace, npm, VS Code extension; writes CHANGELOG section. |
| [#5993](https://github.com/Hmbown/Codewhale/pull/5993) | `fix(tui): re-arm paste-burst heuristic` | ✅ Closed | Fixes multiline paste regression by not gating the heuristic on bracketed-paste readiness. |
| [#5989](https://github.com/Hmbown/Codewhale/pull/5989) | `fix: five recorded defects` | ✅ Closed | Batch fix: queue data loss, ACP schema, metrics, fleet roles, goal-loop bound. |
| [#5983](https://github.com/Hmbown/Codewhale/pull/5983) | `fix(engine): never dispatch truncated tool call` | ✅ Closed | Blocks execution of tool calls whose arguments were silently completed into valid JSON. |
| [#5987](https://github.com/Hmbown/Codewhale/pull/5987) | `fix(vscode): make send path work, close security holes` | ✅ Closed | Fixes IDE stage-2: `startTurn` now accepts the runtime's `201 CREATED` response; patches security issues. Closes [#5834](https://github.com/Hmbown/Codewhale/issues/5834). |
| [#5978](https://github.com/Hmbown/Codewhale/pull/5978) | `fix(acp): advertise session list as object` | ✅ Closed | Corrects ACP `initialize` response so JetBrains clients complete the handshake. |
| [#5995](https://github.com/Hmbown/Codewhale/pull/5995) | `fix(config): honor allow_insecure_http per provider` | ✅ Closed | Restores per-provider `allow_insecure_http` key dropped in v0.9.12. |
| [#5972](https://github.com/Hmbown/Codewhale/pull/5972) | `tui: failing runtime store is a visible notice` | ✅ Closed | Session-id divergence and approval-receipt failures now surface in the UI instead of silent logs. |
| [#6002](https://github.com/Hmbown/Codewhale/pull/6002) | `Integrate 0.9.13 PRs and defer ShannonNet execution` | 🟢 Open | Merge PR for v0.9.13; integrates #5982, #5973, #5996, #5990 with conflict resolution. |
| [#5982](https://github.com/Hmbown/Codewhale/pull/5982) | `feat(tui): confirmed opt-out for model-bound key redaction` | 🟢 Open | Adds a `model_bound` opt-out so developers can work with API keys that get redacted during development. |

---

## 5. Feature Request Trends

- **Context management maturity:** Requests for offload/swap eviction (#6008), configurable user-input timeouts (#6003), and goal-scoped step budgets (#5994) show the community is pushing toward finer-grained control over long-running sessions.
- **Self-improving agents:** The self-learning / skill-evolution proposal (#5860) reflects growing interest in moving beyond static `SKILL.md` files toward automatic pattern extraction.
- **UX configurability:** Users want the bottom chrome (#5950), slash-command history recall (#6006), and vendor pinning for OpenRouter (#6007) — all pointing to a demand for more personalized, less hard-coded TUI behavior.
- **IDE & plugin ecosystem:** The VS Code extension upgrade (#5834 → #5987), computer-use plugin refresh (#5998), and fleet deliverable visibility (#5946) indicate the project is expanding beyond the standalone TUI.

---

## 6. Developer Pain Points

1. **Regression-prone releases:** The v0.9.12 multiline-paste bug (#5981) and the dropped `allow_insecure_http` key (#5991) both came from late-breaking config/heuristic changes without adequate regression guards.
2. **Test instability on Windows:** Flaky `mcp_boot` tests (#5980) and snapshot-prune assertions (#5990) point to timing-dependent CI issues that are hard to reproduce locally.
3. **Stack overflows in tests:** Two `codewhale-tui` lib tests exceed the 2MiB `libtest` thread stack (#5988), hidden from CI by `nextest`'s per-process isolation.
4. **Silent failures:** Session-id divergence (#5931) and approval-receipt errors were only logged, not surfaced — a trust problem for users running long sessions.
5. **Performance hot spots:** The model picker lag (#5975) and tok/s metrics audit (#5977) suggest the TUI's rendering and metrics paths need scrutiny as catalogs grow.
6. **Tool-call safety:** The truncated-argument execution bug (#5986) is a high-severity concern — any provider output limit can lead to file corruption without engine-level safeguards.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*