# AI CLI Tools Community Digest 2026-08-07

> Generated: 2026-08-07 02:56 UTC | Tools covered: 10

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



# Cross-Tool AI CLI Comparison Report — 2026‑08‑07

## 1. Ecosystem Overview
The AI CLI tools landscape is marked by rapid iteration, with each major vendor advancing subagent orchestration, MCP integration, and cross‑platform desktop clients. Community feedback is increasingly focused on **reliability** (session‑resume regressions, data‑loss bugs) and **enterprise readiness** (proxy support, permission scoping, context transparency). The rise of standardized MCP tool registries and plugin ecosystems signals a maturing developer‑tooling layer, while persistent cross‑platform quirks (Windows resource leaks, Linux desktop gaps, NixOS compatibility) highlight ongoing fragmentation.

## 2. Activity Comparison

| Tool | Open Issues (Hot List) | PRs Updated (24h) | Release Activity |
|------|------------------------|-------------------|------------------|
| **Claude Code** | 10 | 3 | None |
| **OpenAI Codex** | 10 | 9 | v0.147.0 (stable) |
| **Gemini CLI** | 10 | 9 | v0.55.0‑preview.2, v0.54.2, nightly |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.79‑6 (patch) |
| **Kimi Code CLI** | 9 | 3 | None |
| **OpenCode** | 10 | 9 | None |
| **Pi** | 10 | 8 | v0.84.0 (stable) |
| **Qwen Code** | 10 | 15 | v0.21.7, nightly, live‑host‑v0.1.0 |
| **DeepSeek TUI** | 10 | 9 | None |

*Counts reflect the number of issues/PRs highlighted in the community digests; actual repository metrics may differ.*

## 3. Shared Feature Directions
| Theme | Tools Mentioning | Specific Needs |
|-------|------------------|----------------|
| **MCP ecosystem maturity** | Codex, Gemini CLI, Copilot CLI, OpenCode, Kimi CLI, DeepSeek TUI | Project‑scoped server pools, auto‑recovery after OAuth, lazy‑loading schemas, zero‑env registry discovery |
| **Cross‑platform desktop clients** | Codex (933 👍), Pi, Qwen Code, OpenCode | Linux desktop app, Windows stability, macOS dock persistence, SSH‑based auth flows |
| **Session & context transparency** | Claude Code, OpenCode (129 👍), Pi, Qwen Code | Token‑usage breakdown, context‑window visibility, cross‑session memory, evidence checkpointing |
| **Prompt‑/permission‑model robustness** | Claude Code, Gemini CLI, Pi, Qwen Code | Compound‑command prompt explosion, “ask”‑list bypasses, reset‑mid‑run state leaks, trusted‑folder inheritance bugs |
| **TUI/terminal UX polish** | Codex, Pi, Qwen Code, DeepSeek TUI | Markdown export, multi‑line status, clickable links, inline image rendering, scrollback preservation |
| **Subagent orchestration** | Codex, OpenCode, Kimi CLI, DeepSeek TUI | Persistent subagent sessions, checkpoint resume, depth‑budget isolation, silent‑failure masking |

## 4. Differentiation Analysis
| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi CLI |
|-----------|-------------|--------------|------------|---------------------|----------|----|-----------|--------------|----------|
| **Primary focus** | Enterprise‑grade agent orchestration | Research‑oriented subagent workflows | Google‑ecosystem integration, evaluation‑driven | GitHub‑native developer workflows | Open‑source flexibility, multi‑provider | Personal AI assistant, TUI‑first | Chinese‑language + enterprise, multimodal | Lightweight TUI with runtime API | Moonshot‑focused coding agent |
| **Target users** | Large‑team, regulated environments | Researchers, power users | Google‑cloud / Vertex users | GitHub Copilot subscribers | Individual developers, tinkerers | Terminal‑power users, SSH workflows | Chinese‑speaking devs, enterprise | Hobbyist / embedded‑host users | Asian‑market developers |
| **Technical approach** | Plugin‑dev validation, Cowork/Cloud session isolation | Portable plugin catalogs, subagent context tracking | Component‑level evals, AST‑aware tooling | ACP server, BYOM model switching | Queue‑based prompt steering, bound tool output | Fullscreen TUI with sticky editor, harness‑v2 | Inline image rendering, checkpointed Goals | Runtime API endpoints, MCP registry discovery | StrReplaceFile byte‑preservation, memory persistence |
| **Release cadence** | Low (no patch) | Moderate (monthly stable) | High (preview + maintenance) | Low (patch only) | Low (ongoing outage) | Moderate (major UX release) | High (multiple patches) | Moderate (integration cycle) | Low (no release) |

## 5. Community Momentum & Maturity
- **Most active communities** (by issue upvotes & discussion volume):  
  – **OpenAI Codex**: Linux desktop demand (933 👍), strong Windows‑resource‑leak engagement.  
  – **OpenCode**: Context‑usage transparency (129 👍), clickable links (119 👍), sustained upstream‑outage discussion.  
  – **Qwen Code**: OAuth free‑tier backlash (150 comments), Windows crash & hook‑regression urgency.  
  – **Claude Code**: Permission‑model bugs (19 👍), copy‑paste indentation (72 👍).  
- **Rapidly iterating tools** (multiple releases/PRs per cycle):  
  – **Gemini CLI** (preview + maintenance + nightly), **Qwen Code** (stable + nightly + host installer), **DeepSeek TUI** (Layer 5.3 rollout).  
- **Maturity signals**: Tools with enterprise‑facing features (Copilot, Codex, Claude Code) show more security‑oriented regressions (trusted‑folder bypass, session‑limit discrepancies) but also faster hotfix cycles. Open‑source‑first tools (OpenCode, Pi) exhibit stronger community‑driven feature requests (context transparency, TUI polish).

## 6. Trend Signals
1. **MCP as a strategic layer** – Every major tool is investing in MCP lifecycle management (project‑scoped pools, registry discovery, post‑OAuth recovery). Developers should expect standardized tool‑integration patterns and vendor‑agnostic plugin ecosystems.
2. **Reliability over novelty** – High‑severity bugs (data‑loss #26856, hook regression #8622, Windows resource leaks) dominate community attention; vendors are shifting focus from feature expansion to stability hardening.
3. **Cross‑platform parity gaps** – Linux desktop demand, Windows process‑table exhaustion, and NixOS compatibility remain unresolved pain points. Tool selection should account for target OS support maturity.
4. **Token‑budget transparency** – Requests for context‑usage breakdowns, model‑fallback warnings, and quota attribution reflect growing need for cost‑predictable AI agent workflows.
5. **Subagent orchestration maturity** – Persistent sessions, checkpoint resume, and depth‑budget isolation are becoming table stakes for multi‑turn agent systems.
6. **Enterprise‑ready permissions** – Compound‑command prompt explosions, trusted‑folder inheritance bugs, and permission‑model inconsistencies signal that fine‑grained, auditable authorization is still a key differentiator.

*Data sourced from community digests dated 2026‑08‑07. Issue counts, upvotes, and PR activity reflect highlighted items only.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
**Data as of 2026-08-07 | Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

### #1 — skill-creator (eval/trigger fix cluster)
- **Functionality:** The meta-skill for authoring, testing, and iteratively optimizing other skills. The central bottleneck in the ecosystem.
- **Discussion highlights:** A cascade of interrelated bugs — `run_eval.py` reporting `recall=0%` on every iteration ([#556](https://github.com/anthropics/skills/issues/556), [PR #1298](https://github.com/anthropics/skills/pull/1298)), Windows subprocess crashes ([PR #1099](https://github.com/anthropics/skills/pull/1099), [#1050](https://github.com/anthropics/skills/pull/1050)), trigger-detection missing real skill names ([PR #1323](https://github.com/anthropics/skills/pull/1323)), and sandbox leakage of eval artifacts into live projects ([PR #1261](https://github.com/anthropics/skills/pull/1261)). At least 10+ independent reproductions of the recall bug.
- **Status:** All fixes **OPEN** — none merged yet.

### #2 — docx skill
- **Functionality:** Create, edit, and manipulate `.docx` files via OOXML tooling.
- **Discussion highlights:** Tracked-change `w:id` collisions corrupting documents with existing bookmarks ([PR #541](https://github.com/anthropics/skills/pull/541)); whitespace reformatting breaking document readability ([#12](https://github.com/anthropics/skills/issues/12)). Both are high-severity correctness issues.
- **Status:** Bug-fix PR **OPEN**; issue **OPEN**.

### #3 — pdf skill
- **Functionality:** PDF creation, extraction, and form handling.
- **Discussion highlights:** 8 case-sensitivity mismatches in `SKILL.md` reference paths breaking skill loading on Linux/macOS ([PR #538](https://github.com/anthropics/skills/pull/538)).
- **Status:** Fix PR **OPEN**.

### #4 — skill-quality-analyzer / skill-security-analyzer
- **Functionality:** Meta-skills that audit other skills across five dimensions (structure, documentation, examples, security, etc.) with weighted scoring.
- **Discussion highlights:** First community contribution of governance/quality tooling; 2 👍, sustained discussion since Nov 2025.
- **Status:** **OPEN**.

### #5 — testing-patterns skill
- **Functionality:** Comprehensive testing guidance covering the Testing Trophy, AAA pattern, React component testing with Testing Library, and test naming conventions.
- **Discussion highlights:** Broad relevance — testing is one of the most requested skill categories in the issues (see §2).
- **Status:** **OPEN**.

### #6 — document-typography skill
- **Functionality:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents.
- **Discussion highlights:** Addresses a universally felt pain point; clearly scoped and self-contained.
- **Status:** **OPEN**.

### #7 — plan-file-hygiene skill
- **Functionality:** Manages the lifecycle of planning artifacts (plans, notes, memory) to prevent context-window accumulation.
- **Discussion highlights:** Directly addresses [issue #1417](https://github.com/anthropics/skills/issues/1417); community credits specific issue commenters for the framing.
- **Status:** **OPEN**.

### #8 — claude-api skill
- **Functionality:** Wraps the Claude API for programmatic use within agent workflows.
- **Discussion highlights:** Criticized for eagerly injecting ~156k tokens in a single tool call, exhausting the context window ([#1487](https://github.com/anthropics/skills/issues/1487)). Highlights a broader tension around skill token budgets.
- **Status:** **OPEN** (usage issue).

---

## 2. Community Demand Trends (from Issues)

| Trend | Evidence |
|---|---|
| **Agent governance & safety** | [#412](https://github.com/anthropics/skills/issues/412) — policy enforcement, threat detection, trust scoring; [#1385](https://github.com/anthropics/skills/issues/1385) — three-gate reasoning quality pipeline |
| **Organization-wide skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) — 8 👍, explicit request for shared skill libraries or direct-share links |
| **Compact / symbolic agent state** | [#1329](https://github.com/anthropics/skills/issues/1329) — "compact-memory" skill to reduce prose-based persistent memory overhead |
| **Security & trust boundaries** | [#492](https://github.com/anthropics/skills/issues/492) — 43 comments, 2 👍; community skills impersonating the `anthropic/` namespace |
| **Skill-creator tooling reliability** | [#556](https://github.com/anthropics/skills/issues/556), [#1169](https://github.com/anthropics/skills/issues/1169) — eval/trigger pipeline is fundamentally broken; 7 👍 on the recall bug |
| **MCP-style skill exposure** | [#16](https://github.com/anthropics/skills/issues/16) — expose skills as discoverable MCP endpoints rather than file-based installations |
| **Context-window discipline** | [#1487](https://github.com/anthropics/skills/issues/1487) — skills must be token-aware; eager injection is a community concern |

---

## 3. High-Potential Pending Skills

These PRs have active community discussion and address clear gaps; all remain **OPEN**:

| PR | Skill | Why it may land soon |
|---|---|---|
| [PR #514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Narrow scope, universally relevant, no controversial dependencies |
| [PR #723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | High demand trend; comprehensive but well-scoped |
| [PR #1302](https://github.com/anthropics/skills/pull/1302) | **color-expert** | Self-contained domain skill; no infrastructure risk |
| [PR #1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Extends the quality-analyzer concept with mechanical + reasoning gates |
| [PR #1479](https://github.com/anthropics/skills/pull/1479) | **plan-file-hygiene** | Directly solves a named, well-documented lifecycle problem (#1417) |
| [PR #525](https://github.com/anthropics/skills/pull/525) | **pyxel** | Niche but complete (MCP server + workflow); low-risk addition |
| [PR #83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer** + **skill-security-analyzer** | Meta-tooling the ecosystem clearly needs; already has 👍 traction |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is for **reliable skill-creator tooling** — the eval/trigger pipeline is broken in multiple confirmed ways, and until `run_eval.py` produces trustworthy recall numbers, the entire skill-optimization loop is optimizing against noise, making every other skill contribution harder to validate and iterate on.

---



# Claude Code Community Digest — 2026-08-07

## 1. Today's Highlights

No new releases were published in the last 24 hours. The community is focused on several escalating issues: a WSL2 memory-OOM regression from the v2.1.117 embedded ugrep wrapper (#54394), a persistent permissions bug that ignores `ask` lists when Bash is allowlisted (#6527), and a growing cluster of Cowork/Cloud session bugs including git proxy blocks (#76248) and session-global worktree isolation leaks (#84685). Developer tooling improvements are advancing via plugin-dev validation fixes in two open PRs.

## 2. Releases

No releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#54394](https://github.com/anthropics/claude-code/issues/54394) | v2.1.117 embedded ugrep amplifies regex backtracking → V8 heap OOM on WSL2 | A recent perf change routes all `grep` through an embedded `ugrep` wrapper, causing 8 GB ceiling hits and host freezes. Directly impacts WSL2 users running regex-heavy workflows. | 24 comments, 2 👍 |
| [#6527](https://github.com/anthropics/claude-code/issues/6527) | `ask` list ignored when "Bash" is in allow list | Permissions model is broken for a common configuration — users can't restrict interactive Bash prompts while keeping non-interactive commands allowed. Open since Aug 2025 with sustained interest. | 23 comments, **19 👍** |
| [#57371](https://github.com/anthropics/claude-code/issues/57371) | Disable bundled Cowork background service (CoworkVMService) on Windows | The CoworkVMService runs invisibly for users who don't use Cowork, consuming resources. Strong demand for a toggle. | 18 comments, **42 👍** |
| [#13378](https://github.com/anthropics/claude-code/issues/13378) | 2-space indent + hard wrap at 80 breaks copy-paste | A fundamental UX issue: copied terminal output carries unwanted indentation, requiring manual cleanup. One of the most upvoted issues ever. | 16 comments, **72 👍** |
| [#76248](https://github.com/anthropics/claude-code/issues/76248) | Cloud/Cowork git proxy blocks pushes outside authorized repo set | Mid-July rollout (CCR_TEST_GITPROXY) broke PAT pass-through for Cowork sessions, preventing pushes to any non-whitelisted repo. Regression with active impact. | 14 comments, 5 👍 |
| [#37796](https://github.com/anthropics/claude-code/issues/37796) | Copied text includes 2-space leading indentation from rendered output | Duplicate-flavored variant of #13378 — terminal rendering padding leaks into clipboard. High frustration, low friction fix. | 13 comments, **49 👍** |
| [#54750](https://github.com/anthropics/claude-code/issues/54750) | Session limit reaches 100% despite low visible usage | Users are being blocked from further Claude Code usage due to a discrepancy between reported and actual session consumption. Affects billing-tracked tiers. | 16 comments, 9 👍 |
| [#79584](https://github.com/anthropics/claude-code/issues/79584) | Assistant text before tool calls intermittently not rendered (Windows) | Plugin-driven workflows using `AskUserQuestion` lose preceding assistant text on Windows, breaking observability. TUI rendering race condition. | 9 comments, 7 👍 |
| [#76718](https://github.com/anthropics/claude-code/issues/76718) | Compound-command permission prompting breaks multi-session orchestration | Every segment of a compound command triggers a prompt even when individually allowlisted, generating 700+ prompts in fan-out workflows. Blocks parallel agent patterns. | 7 comments |
| [#78775](https://github.com/anthropics/claude-code/issues/78775) | Session time-range filter hidden unless Group by = State (Desktop regression) | Desktop UI regression makes a key navigation feature inaccessible unless users accidentally set the right grouping. 7 comments, 23 👍 |

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#84600](https://githubp/anthropics/claude-code/pull/84600) | Enable frontend-design plugin at project scope | Registers the official marketplace and enables the frontend-design skill via `.claude/settings.json`, auto-loading for all repo contributors. |
| [#84427](https://github.com/anthropics/claude-code/pull/84427) | Fix plugin-dev: prevent `validate-agent.sh` exiting on first warning | Follows up on #76985 — the validator was terminating prematurely under `set -e` due to Bash arithmetic exit codes, skipping remaining checks. |
| [#84381](https://github.com/anthropics/claude-code/pull/84381) | Fix plugin-dev: handle wrapped hook schemas in `validate-hook-schema.sh` | Adds support for top-level `"hooks"` key wrapper and optional matchers in hook schema validation, improving developer tooling accuracy. |

*Note: Only 3 PRs were updated in the last 24 hours; all are listed above.*

## 5. Feature Request Trends

- **Notification & observability**: Multiple requests for system-level notifications when Claude needs attention or completes tasks (#26581, 32 👍), plus terminal tab title updates to reflect agent state (#71369).
- **Proactive context management**: Users want Claude to self-initiate context compaction rather than waiting for the system threshold (#33026, 15 👍) — currently closed but signal remains strong.
- **Plugin/hook ergonomics**: A `handled` decision type for `UserPromptSubmit` hooks would let hooks inject output without the "blocked" framing (#72327, 4 👍).
- **Resource transparency**: Clearer session-limit reporting (#54750) and budget attribution (#84612) are recurring asks, especially around Fable consumption and cross-account carry-over.
- **Platform polish**: Windows MSIX stability (#81123), Desktop grouping/filtering UX (#78775), and CoworkVMService opt-out (#57371) reflect ongoing cross-platform maturity efforts.

## 6. Developer Pain Points

1. **Permissions model inconsistency**: The `ask`-list bypass when Bash is allowlisted (#6527) and compound-command prompt explosion (#76718) make permission scoping unreliable for complex workflows, especially multi-session orchestration.
2. **Copy-paste cleanliness**: The 2-space indentation leak from terminal rendering (#13378, #37796) is a persistent, high-volume frustration with no fix in sight despite 72+ 👍.
3. **Memory regression from native tooling**: The v2.1.117 embedded `ugrep`/`bfs` change (#54394) improved some workflows but introduced a severe OOM path on WSL2, suggesting native wrapper integration needs tighter resource bounding.
4. **Cowork/Cloud session instability**: A cluster of bugs — git proxy blocks (#76248), scheduled-path overlaps (#71307), silent permission-stream closures on macOS (#59707), and session-global worktree state leaks (#84685) — indicates the Cowork infrastructure is a pain frontier.
5. **Plugin & hook tooling gaps**: Validation scripts are brittle (#84427, #84381), and hooks lack a "success-handled" semantic, forcing awkward "blocked" framing for legitimate short-circuits (#72327).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-07

## 1. Today's Highlights

Codex **v0.147.0** shipped with portable Agent Plugin installation across local, personal, workspace, and remote catalogs, plus persistent manually-ordered conversation sections for long transcripts. Community momentum remains heavily focused on a Linux desktop app (933 👍) and on diagnosing serious Windows resource leaks and MCP memory bloat in recent desktop builds. A cluster of PRs landed today addressing subagent context tracking, MCP server recovery after OAuth, and improved TUI UX.

---

## 2. Releases

**rust-v0.147.0** — [GitHub](https://github.com/openai/codex)

- **Portable Agent Plugins:** Install and search plugins across local, personal, workspace, and remote catalogs (#36544, #36409, #36919, #36796).
- **Conversation sections:** Organize conversations into persistent, manually ordered sections and browse long transcripts incrementally (#35722, #36007, #36380, #36948).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#11023](https://github.com/openai/codex/issues/11023) | Codex desktop app for Linux | No official Linux desktop release; users on Linux are left with CLI only despite strong demand. | 203 comments · 933 👍 |
| [#33776](https://github.com/openai/codex/issues/33776) | Windows: ChatGPT.exe spawns hundreds of taskkill/conhost processes | Causes WMI storms and DWM degradation — a severe resource leak on Windows Desktop. | 32 comments · 27 👍 |
| [#2880](https://github.com/openai/codex/issues/2880) | Copy/Export Message as Markdown (CLOSED) | Long-requested TUI feature for exporting conversations to Markdown; now addressed. | 28 comments · 78 👍 |
| [#28080](https://github.com/openai/codex/issues/28080) | Desktop thread tools intermittently lose handlers | Tool-call handlers drop mid-session on Windows, breaking agent workflows unpredictably. | 23 comments · 2 👍 |
| [#20883](https://github.com/openai/codex/issues/20883) | Project-scoped MCP process pool | MCP servers currently start per-session instead of being shared per project, wasting resources. | 17 comments · 4 👍 |
| [#6060](https://github.com/openai/codex/issues/6060) | HTTP proxy config via config.toml | Enterprise and academic users cannot route Codex traffic through corporate proxies. | 15 comments · 68 👍 |
| [#19694](https://github.com/openai/codex/issues/19694) | Model picker filters out catalog models (CLOSED) | Desktop model selector was silently hiding models returned by `model_catalog_json`. | 14 comments · 35 👍 |
| [#26820](https://github.com/openai/codex/issues/26820) | CLI cannot acquire Chrome extension backend | CLI and Desktop app compete for the same Chrome extension, blocking terminal-based use. | 12 comments · 9 👍 |
| [#21653](https://github.com/openai/codex/issues/21653) | Multi-line status line in TUI | Long status lines truncate instead of wrapping, hiding critical context from users. | 12 comments · 58 👍 |
| [#37247](https://github.com/openai/codex/issues/37247) | macOS Desktop leaks zombie child processes (CLOSED) | Thousands of zombies exhaust the process table, crashing the app and blocking new forks. | 2 comments · 0 👍 |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#37358](https://github.com/openai/codex/pull/37358) | Add Markdown conversation export to the TUI | Adds `/export` with clipboard and file destinations, preserving structured conversation history. |
| [#37360](https://github.com/openai/codex/pull/37360) | Use consistent TUI input placeholders | Standardizes placeholder text across main and side conversation inputs; removes randomized examples. |
| [#37356](https://github.com/openai/codex/pull/37356) | Support agent identity endpoint overrides | Honors `CODEX_AGENT_IDENTITY_AUTHAPI_BASE_URL` and `JWKS_BASE_URL` env vars for custom deployments. |
| [#37347](https://github.com/openai/codex/pull/37347) | Track context windows per agent | Subagent context windows now identified by agent name, preventing forked children from inheriting stale compaction state. |
| [#37345](https://github.com/openai/codex/pull/37345) | Send model routing hints to the Codex backend | Adds `x-codex-routing-hint` header with model and service tier on Responses HTTP, compaction, and WebSocket connections. |
| [#37344](https://github.com/openai/codex/pull/37344) | Fix subagent MCP startup status settling | Clears deferred MCP expectations for active subagents, preventing TUI from stuck "running" indicators. |
| [#37337](https://github.com/openai/codex/pull/37337) | Recover MCP servers after OAuth reauthentication | Streamable HTTP MCP servers that fail on bad credentials now auto-recover after successful OAuth sign-in. |
| [#37352](https://github.com/openai/codex/pull/37352) | Configure default code-mode exec yield timeout | Adds `features.code_mode.default_exec_yield_time_ms` (default 30s) for code-mode `exec` calls. |
| [#37349](https://github.com/openai/codex/pull/37349) | Mount minimal `/dev` in Bubblewrap sandboxes | Prevents host device-tree leakage into network-isolated full-filesystem sandboxes. |
| [#37350](https://github.com/openai/codex/pull/37350) | Allow `ThreadManager` to customize thread ID generation | Adds configurable thread ID allocation while preserving UUIDv7 as default and stored IDs on resume. |

---

## 5. Feature Request Trends

- **Cross-platform desktop clients:** The #1 demand remains a Linux desktop app (#11023), with Windows and macOS already served.
- **Enterprise networking:** HTTP proxy support (#6060) and configurable origins/connectors (#37338) reflect growing enterprise deployment needs.
- **MCP server lifecycle management:** Users want project-scoped pools (#20883), post-OAuth recovery (#37337), and deterministic tool ordering (#37351).
- **TUI usability:** Markdown export (#2880 / #37358), multi-line status (#21653), copy-paste improvements (#24685), and placeholder control (#13466) dominate CLI feedback.
- **Session & conversation organization:** Persistent sections (#37358), subagent thread visibility (#25341), and remote dual-turn prevention (#34767) show users managing increasingly complex agent workflows.

---

## 6. Developer Pain Points

- **Resource leaks on Windows:** Multiple issues report process table exhaustion — `taskkill.exe`/`conhost.exe` storms (#33776), MCP suite memory reaching 10.9 GB (#33531), and zombie child leaks (#37247). These are the most impactful stability bugs this cycle.
- **Intermittent handler & auth failures:** Tool handlers dropping mid-session (#28080), OAuth silently falling back to a hardcoded dummy key on network change (#37192), and model picker filtering (#19694) create unreliable developer experiences.
- **Quota & rate-limit accounting bugs:** Subagents draining full weekly quotas overnight (#35463) and requests blocked by incorrect usage limits post-reset (#37250) erode trust in the billing system.
- **CLI–Desktop extension contention:** Both the CLI and Desktop app competing for the Chrome extension backend (#26820) forces users to choose one interface.
- **Sandbox & security friction:** Elevated sandbox re-arming WFP firewall on nearly every command on Windows (#31556) causes constant UAC prompts, and the "Allow once" permission dialog is unresponsive (#36115).

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-07

## 1. Today's Highlights

Gemini CLI released **v0.55.0-preview.2** as a patched follow-up to preview.1, and **v0.54.2** landed as a maintenance release. The community is actively tracking a high-profile data-loss bug (#26856) involving agent misbehavior, while multiple PRs address capacity-exhaustion error handling, infinite auth-loop fixes, and Docker runtime modernization to Node 22/24.

---

## 2. Releases

| Version | Notes |
|---|---|
| **v0.55.0-preview.2** | Patched preview release; cherry-picks commit `2139b12` from the preview.1 branch. [PR #28719](https://github.com/google-gemini/gemini-cli/pull/28719) · [Changelog PR #28722](https://github.com/google-gemini/gemini-cli/pull/28722) |
| **v0.54.2** | Maintenance bump across all monorepo packages. [PR #28712](https://github.com/google-gemini/gemini-cli/pull/28712) |
| **v0.56.0-nightly.20260807** | Nightly snapshot. [PR #28720](https://github.com/google-gemini/gemini-cli/pull/28720) |

---

## 3. Hot Issues

1. **[#26856](https://github.com/google-gemini/gemini-cli/issues/26856) — Agent disobedience causing data loss (47 comments, 16 👍)**  
   A P1 bug where the agent reportedly ignored user instructions, leading to irreversible deletion of tens of thousands of Obsidian files. Community demand for exported chat-history JSON is high; the issue remains open and manually triaged.

2. **[#20773](https://github.com/google-gemini/gemini-cli/issues/20773) — PowerShell 5.1 `&&` parser error (17 comments, closed)**  
   Gemini CLI emits `git status && git branch` which fails on legacy Windows PowerShell. Closed; a fix was merged.

3. **[#10704](https://github.com/google-gemini/gemini-cli/issues/10704) — MCP Client Sampling support (13 comments, 9 👍, closed)**  
   Feature request to let MCP servers call LLMs through Gemini CLI per the MCP spec. Closed, likely implemented or deferred.

4. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent MAX_TURNS reported as GOAL success (12 comments)**  
   The `codebase_investigator` subagent marks itself successful after hitting the turn limit without producing results, silently hiding the interruption. Maintainer-only; flagged for retesting.

5. **[#25867](https://github.com/google-gemini/gemini-cli/issues/25867) — Backspace deletes word on Windows (10 comments, closed)**  
   Backspace behavior regressed to word-deletion on Windows. Closed after fix.

6. **[#25884](https://github.com/google-gemini/gemini-cli/issues/25884) — Invalid whitespace/newlines in terminal commands (10 comments, closed)**  
   Gemini injects stray whitespace or newlines inside single commands, breaking copy-paste into Zsh. Closed.

7. **[#27132](https://github.com/google-gemini/gemini-cli/issues/27132) — VS Code UI lockup from globalState I/O (7 comments)**  
   Long sessions or window reloads cause the VS Code extension to block the main thread via `globalState` storage, triggering "not responding" prompts. Open, P2.

8. **[#24353](https://github.com/google-gemini/gemini-cli/issues/24353) — Component-level evaluations (7 comments)**  
   Epic tracking behavioral eval infrastructure for the 76+ eval tests run across supported Gemini models. Maintainer-only workstream.

9. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — AST-aware file reads and search (7 comments)**  
   Epic investigating whether AST-aware tooling reduces turn count and token noise by reading precise method bounds. Maintainer-only.

10. **[#28698](https://github.com/google-gemini/gemini-cli/issues/28698) — High memory usage (5 comments)**  
    User reports memory growing unboundedly during idle/break periods in v0.53.1. Open, P2; chat-history JSON requested for diagnosis.

---

## 4. Key PR Progress

| PR | Title | Status | Summary |
|---|---|---|---|
| [#28716](https://github.com/google-gemini/gemini-cli/pull/28716) | Reclassifying Capacity Exhaustion as Terminal Error | ✅ Closed | Capacity exhaustion and insufficient credits are now terminal errors, triggering immediate model fallback instead of retry loops. |
| [#28519](https://github.com/google-gemini/gemini-cli/pull/28519) | Prevent Infinite Auth Loop | ✅ Closed | Fixes [#28430] by awaiting async `oauth_creds.json` write and forcing consent, stopping auth-loop hangs. |
| [#28597](https://github.com/google-gemini/gemini-cli/pull/28597) | Load Env Vars Before Resolving Settings Placeholders | 🔄 Open | Fixes a load-order race: `.env` variables are now available when settings files are parsed and expanded. |
| [#28602](https://github.com/google-gemini/gemini-cli/pull/28602) | Update Docker Base to `node:24-slim` | 🔄 Open | Bumps builder and runtime images from Node 20 → 24; aligns with current LTS. |
| [#28603](https://github.com/google-gemini/gemini-cli/pull/28603) | Upgrade Sandbox Dockerfile to Node 22 | ✅ Closed | Addresses Node 20 EOL (2026-04-30); sandbox now runs on Node 22 for security compliance. |
| [#28596](https://github.com/google-gemini/gemini-cli/pull/28596) | `--list-all-sessions` CLI Flag | 🔄 Open | Lists sessions across all registered workspaces, grouped by path — resolves a frequent discoverability complaint. |
| [#28592](https://github.com/google-gemini/gemini-cli/pull/28592) | Keep Auto Model Visible Without Preview Access | 🔄 Open | The `/model` Auto option now remains selectable even when the user lacks preview-tier model access. |
| [#28526](https://github.com/google-gemini/gemini-cli/pull/28526) | Stop Leaking VS Code Disposables | 🔄 Open | Fixes a stray parenthesis that collapsed two `context.subscriptions.push(...)` calls into a comma expression, leaking `gemini.diff.accept` and workspace-folder listeners. |
| [#28718](https://github.com/google-gemini/gemini-cli/pull/28718) | Record Usage on Aborted Streams | 🔄 Open | Usage metadata is now flushed on stream abort, closing a gap where aborted requests reported zero token usage. |
| [#28700](https://github.com/google-gemini/gemini-cli/pull/28700) | Stop Message Fusing After Interrupted Tool Calls | ✅ Closed | Fixes the "model finishes your sentence" bug: interrupted tool calls no longer merge the next user message into the incomplete turn. |

---

## 5. Feature Request Trends

- **MCP Ecosystem Maturity** — Client sampling (#10704), Figma MCP MIME-type handling (#27731), and Calendar MCP input-shaping bugs (#27725) signal growing MCP adoption and demand for robust tool integrations.
- **Cross-Workspace Session Management** — The `--list-all-sessions` flag (#28596) reflects repeated user need to locate sessions created across multiple project directories.
- **AST-Aware Codebase Tooling** — The epic in #22745 points to a strategic direction: replacing broad text search with structural, AST-aware reads to cut token waste and turn count.
- **Evaluation & Reliability Infrastructure** — Component-level evals (#24353) and robust subagent recovery (#22323) show investment in measurable agent quality and fault tolerance.

---

## 6. Developer Pain Points

| Theme | Representative Issues |
|---|---|
| **Agent reliability & data safety** | #26856 (data loss), #22672 (destructive behavior), #22323 (silent subagent failure) |
| **Shell / terminal integration** | #20773 (PowerShell `&&`), #25867 (backspace), #25884 (whitespace injection), #25933 (execvp permission), #25166 (stuck "Waiting input") |
| **Session & state persistence** | #27180 (session loss on shutdown), #27721 (history deleted on update) |
| **Auto Memory quirks** | #26522 (low-signal retry loops), #26525 (redaction/logging), #26523 (invalid patches) |
| **Platform-specific bugs** | #27386 (Unicode corruption), #27387 (selection keys), #27132 (VS Code main-thread block) |
| **Resource limits** | #24246 (400 error >128 tools), #28698 (memory growth), #19638 (search result overflow) |

---

*Data sourced from [github.com/google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) on 2026-08-07.*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-07

## 1. Today's Highlights

A new patch release **v1.0.79-6** arrived, fixing a rare internal delay diagnostic and a session-history loading failure that silently blanked transcripts for the remainder of a session. The issue tracker saw a wave of fresh reports over the weekend, with community attention concentrated on session-resume regressions in 1.0.74, NixOS Bash-tool breakage, and several permission/interactivity bugs surfacing in v1.0.78–1.0.79.

---

## 2. Releases

### v1.0.79-6
- **Fixed:** A rare internal delay no longer prints a diagnostic warning on top of the interactive UI.
- **Fixed:** Failed session-history loads no longer leave the timeline permanently empty — the failure was previously silently discarded, keeping the transcript blank for the entire session with no logged error.

> *Notably, there were no PRs merged in the last 24 h; this patch appears to be a targeted hotfix release.*

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4313](https://github.com/github/copilot-cli/issues/4313) | Scroll through current conversation history | Mouse wheel / PageUp/Down currently don't scroll within the active prompt buffer — a basic UX gap for long sessions. | 4 comments, opened 2026-07-31 |
| [#3392](https://github.com/github/copilot-cli/issues/3392) | Bash tool breaks on NixOS (≥ v1.0.49) | NixOS users cannot run any bash commands via the agent; a hard blocker for that distro. | 3 comments, **7 👍** — strong signal |
| [#4174](https://github.com/github/copilot-cli/issues/4174) | ACP server does not expose token/context usage | Non-interactive / ACP users have zero visibility into cost or context consumption. | 3 comments, 2 👍, **CLOSED** |
| [#4251](https://github.com/github/copilot-cli/issues/4251) | Resume of large sessions OOMs in v1.0.74 | Regression vs v1.0.73: ~3–4× memory spike causes OOM on long-lived sessions — directly impacts power users. | 2 comments, 1 👍 |
| [#4311](https://github.com/github/copilot-cli/issues/4311) | Transcript renders as blank lines until children/width change | Rendering bug: content exists but is invisible until a trigger repaints the UI; `/resume` does not recover it. | 2 comments |
| [#4212](https://github.com/github/copilot-cli/issues/4212) | Prompt box invisible in tmux (dark-on-dark) | Users running inside tmux see unreadable prompts and selected menu items — a common dev-environment setup. | 2 comments |
| [#4211](https://github.com/github/copilot-cli/issues/4211) | BigInt in MCP responses causes fatal error | `TypeError: Do not know how to serialize a BigInt` aborts all ongoing tasks — breaks MCP integrations that return large integers. | 2 comments, **triaged** |
| [#4380](https://github.com/github/copilot-cli/issues/4380) | Rubber Duck uses same model family as primary session | Undermines adversarial review: the reviewer model should be independent but currently isn't. | 2 comments |
| [#4392](https://github.com/github/copilot-cli/issues/4392) | Orphaned stdio MCP server processes after auth | Post-auth MCP rebuild leaks child processes that are neither killed nor reaped — resource leak and cleanup concern. | 1 comment, **triage** |
| [#4346](https://github.com/github/copilot-cli/issues/4346) | MCP registry policy returns 403 under GITHUB_TOKEN in Actions | Blocks all non-default MCP servers in CI when using the documented PAT-less Actions setup — a CI reliability issue. | 1 comment, 1 👍, **triaged** |

---

## 4. Key PR Progress

**No pull requests were updated in the last 24 hours.** The v1.0.79-6 release appears to have been shipped without a tracked PR in this window.

---

## 5. Feature Request Trends

1. **Session history navigation** — Users want mouse-wheel and keyboard scrolling within the active conversation buffer (#4313), indicating a desire for richer in-session UX parity with terminal conventions.

2. **`.agents` discovery beyond Git repos** — Extending the `.agents/skills` convention to instructions, agents, and hooks in any opened folder would let users standardize Copilot customizations across non-repo directories (#4204).

3. **BYOM model switching without restart** — Current BYOM config requires a single `COPILOT_MODEL` value; users want in-session model discovery and switching, especially with Google Vertex AI through OpenAI-compatible endpoints (#4376).

4. **Transparent permission prompts** — When approval is requested, users want the prompt to explain *which specific rule or command characteristic* triggered the safeguard, enabling better evaluation (#4386).

5. **Shell-mode Tab completion** — Prefixing a command with `!` should use normal terminal tab-completion (files, commands, flags) rather than switching focus to the Issues view (#4387).

6. **Worktree branch-name conventions** — Preserve repo-specific username/branch naming guidelines when creating and moving worktrees via `/worktree` or `/move` (#3914).

---

## 6. Developer Pain Points

- **Session resume regressions** — v1.0.74 introduced a severe memory regression (3–4× peak RSS) that OOMs large sessions (#4251), and v1.0.79-6 only partially addressed history-loading failures. Power users with long-lived sessions are the hardest hit.

- **NixOS and non-standard environments** — The Bash tool breakage on NixOS (#3392, 7 👍) and tmux rendering issues (#4212) show that Copilot CLI still struggles outside the primary supported terminal stacks.

- **MCP integration fragility** — Three separate issues in one week: BigInt serialization crashes (#4211), orphaned stdio processes after auth rebuild (#4392), and 403 policy failures under GITHUB_TOKEN in Actions (#4346). MCP reliability is a recurring pain point.

- **Permission mode bugs** — Switching from auto back to interactive mode leaves the agent executing without permission requests (#4388, #4389), creating both a UX and a safety concern.

- **Queued / pending message stalls** — Messages sent while another is pending get stuck in queue with no cancellation path (#4373), and shell background tasks that exit prematurely leave the model waiting forever (#4385).

- **Copied text clearing the screen on Windows** — Copying selected text resets the terminal on certain codepages (e.g., CP 936) (#4391), disrupting Windows users with non-ASCII locales.

---

*Generated 2026-08-07 · Source: github.com/github/copilot-cli*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-07

## 1. Today's Highlights

The most notable activity this period centers on a **binary-file corruption bug** in `StrReplaceFile` (issues #2591, #2594, #2595), where non-UTF-8 bytes outside the edit region were silently overwritten with replacement characters — two competing fix PRs landed within hours of each other. Meanwhile, the community continues to push for **session memory persistence** (#1283) and **MCP context optimization** (#2147), signaling growing demand for scalability and efficiency improvements in long-running coding workflows.

## 2. Releases

No new releases were published in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#2591](https://github.com/MoonshotAI/kimi-cli/issues/2591) | StrReplaceFile corrupts undecodable bytes outside the edited region | Data-integrity bug: any binary or non-UTF-8 file edited via `StrReplaceFile` risks silent corruption, even when the edit target is far from the corrupted bytes. | New, 3 comments |
| [#2317](https://github.com/MoonshotAI/kimi-cli/issues/2317) | Plan mode file path not clickable in chat webview | UX regression in VSCode extension — plan-mode file paths should be interactive links for quick navigation; currently dead text. | 4 comments, 1 👍 |
| [#2474](https://github.com/MoonshotAI/kimi-cli/issues/2474) | CLI interface keeps shaking / re-rendering entire conversation | Severe UX issue causing visual instability and perceived slowness; affects Linux users on K2.7 Code thinking model. | 2 comments, 2 👍 |
| [#1283](https://github.com/MoonshotAI/kimi-cli/issues/1283) | Feature Request: Memory System — Persistent context across sessions | Long-discussed enhancement (created Feb 2026) for cross-session memory; critical for developers who want the CLI to retain project patterns and preferences. | 20 comments, active through Aug 6 |
| [#2147](https://github.com/MoonshotAI/kimi-cli/issues/2147) | Lazy-load MCP tool schemas into context | MCP servers currently inject all tool schemas at session start, burning thousands of tokens before any user input — a scalability bottleneck. | 1 comment, 1 👍 |
| [#621](https://github.com/MoonshotAI/kimi-cli/issues/621) | [CLOSED] First WriteFile always errors with Invalid path | Resolved issue where relative paths failed on first `WriteFile` call; users worked around with absolute paths. | 2 comments |
| [#821](https://github.com/MoonshotAI/kimi-cli/issues/821) | [CLOSED] Missing authorization checks + dependency updates | Security review flagged 2 IDOR vulnerabilities and 5 dependency CVEs (CVSS 7.0–8.0); now closed, likely addressed. | 0 comments |
| [#2593](https://github.com/MoonshotAI/kimi-cli/issues/2593) | Quick mode-switch (auto/yolo/manual) in VSCode panel | Feature request for faster workflow toggling and quota visibility (5-hour remaining) directly in the extension panel. | New, 0 comments |

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#2595](https://github.com/MoonshotAI/kimi-cli/pull/2595) | fix(StrReplaceFile): refuse to edit files that are not valid UTF-8 | Bug fix | Conservative fix: `StrReplaceFile` now refuses to process files containing non-UTF-8 bytes, preventing silent corruption. Closes #2591. |
| [#2594](https://github.com/MoonshotAI/kimi-cli/pull/2594) | fix(tools): preserve non-UTF-8 bytes in StrReplaceFile edits | Bug fix | Constructive fix: applies `old`/`new` as raw UTF-8 byte substrings on the buffer, preserving all untouched non-UTF-8 bytes. Also closes #2591. |
| [#2255](https://github.com/MoonshotAI/kimi-cli/pull/2255) | feat(shell): support Shift+Enter for inserting newlines | Feature | Adds `Shift+Enter` as a third newline shortcut alongside existing `Ctrl-J` and `Alt-Enter`, improving ergonomics for shell input. Closes #2254. |

## 5. Feature Request Trends

- **Cross-session memory & context retention** (#1283) remains the most upvoted and discussed enhancement, reflecting developer desire for the CLI to "learn" project conventions over time.
- **MCP efficiency** (#2147) points to growing friction as users configure more tools — lazy-loading schemas is seen as essential for scaling.
- **VSCode panel ergonomics** (#2593, #2317) — users want faster mode switching, clickable plan-mode paths, and visible quota counters within the extension UI.
- **Input shortcut parity** (#2255) — the community values familiar editor keybindings (Shift+Enter) in the CLI prompt.

## 6. Developer Pain Points

1. **Silent data corruption** — The `StrReplaceFile` UTF-8 bug (#2591) is a high-severity pain point for anyone editing binary assets, compiled output, or non-ASCII source files; two PRs landed simultaneously, indicating urgency.
2. **UX instability in plan mode** — Non-clickable file paths (#2317) and terminal jitter/re-renders (#2474) disrupt workflow continuity, particularly on Linux.
3. **Token waste from eager MCP loading** — All tool schemas injected at session start (#2147) leaves less budget for actual code context, a growing concern as MCP ecosystems expand.
4. **Lack of persistent memory** — Developers repeatedly request cross-session context (#1283) to avoid re-explaining project structure and conventions.
5. **Cumbersome mode switching** — No quick-panel toggle for auto/yolo/manual modes (#2593) forces keyboard-heavy or menu-diving workflows.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-07

## 1. Today's Highlights

A sustained upstream-provider outage continues to impact OpenCode Go and Zen subscribers, with 10+ open issues reporting `401 Request blocked by upstream provider` errors across all paid models — a problem that appears server-side given direct API keys work fine. On the development front, the team shipped meaningful fixes for session summary memory bloat, ACP MCP tool isolation, and TUI permission prompt handling, while several feature PRs advance the subagent session model and queue-based prompt steering.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#38257](https://github.com/anomalyco/opencode/issues/38257) | Go subscription models return 401 "Request blocked by upstream provider" | Largest affected issue (44 comments) — all Go-tier `/chat/completions` calls fail while `/v1/models` works, pointing to a backend auth/routing problem | 👍 11 |
| [#38218](https://github.com/anomalyco/opencode/issues/38218) | Same upstream-block bug, broader reproduction | Confirms the outage spans multiple machines and clients (Desktop, Hermes, Windows) | 👍 13 |
| [#38195](https://github.com/anomalyco/opencode/issues/38195) | Go subscription 401 across Desktop & Hermes | Cross-platform confirmation; free models unaffected | 👍 17 |
| [#6152](https://github.com/anomalyco/opencode/issues/6152) | Session context usage breakdown (like `/context` in Claude) | High-visibility feature request for transparent context-window tracking in the TUI | 👍 129 · 22 comments |
| [#31932](https://github.com/anomalyco/opencode/issues/31932) | Cross-project session list/picker for TUI | Addresses multi-repo workflow friction — current `/sessions` is project-scoped | 👍 6 · 15 comments |
| [#39875](https://github.com/anomalyco/opencode/issues/39875) | Privacy wording removal + telemetry/retention policy | Go subscriber raises concerns about sudden policy changes and lack of transparency | 👍 44 · 6 comments |
| [#1168](https://github.com/anomalyco/opencode/issues/1168) | Make links clickable (Ctrl+Left Click) | Long-standing usability request for in-TUI URL interaction | 👍 119 · 11 comments |
| [#39827](https://github.com/anomalyco/opencode/issues/39827) | Zen models also blocked by upstream | Confirms outage spans both Go and Zen tiers; direct provider keys unaffected | 👍 4 |
| [#40502](https://github.com/anomalyco/opencode/issues/40502) | Web interface not auto-refreshing conversations | UX bug requiring manual page refresh to see new messages in real time | 7 comments |
| [#40958](https://github.com/anomalyco/opencode/issues/40958) | DeepSeek V4 Flash Free metadata shows 200K context vs 1M native | Configuration bug artificially capping context window for a popular free model | 3 comments |

## 4. Key PR Progress

| # | PR | Type | Description |
|---|-----|------|-------------|
| [#40981](https://github.com/anomalyco/opencode/pull/40981) | fix(app): complete translation coverage | Bug fix | Adds 8 missing session-export strings across all 27 non-English locales; localizes usage-limit actions and titlebar labels |
| [#40861](https://github.com/anomalyco/opencode/pull/40861) | fix(opencode): stop storing full patch text in session summary diffs | Bug fix | Fixes #32005 — `SessionSummary.summarize()` previously stored complete `Snapshot.diffFull()` patches, causing memory bloat in long sessions |
| [#40979](https://github.com/anomalyco/opencode/pull/40979) | fix(acp): isolate session MCP tools | Bug fix | Tracks which ACP session owns each dynamically registered MCP server name per directory, preventing cross-session tool leakage (#40978) |
| [#40977](https://github.com/anomalyco/opencode/pull/40977) | fix(i18n): use 词元 instead of 令牌 for token in zh locale | Bug fix | Replaces the misleading API-credential term 「令牌」with the correct LLM-context term 「词元」across 7 occurrences in the Chinese locale |
| [#40974](https://github.com/anomalyco/opencode/pull/40974) | fix(desktop): preserve macOS app on window close | Bug fix | Keeps the macOS app alive when the last window closes and restores the persisted window on Dock activation; Windows/Linux behavior unchanged |
| [#40973](https://github.com/anomalyco/opencode/pull/40973) | fix(provider): forward agent temperature for config-defined custom models | Bug fix | Custom models defined in `opencode.json` previously defaulted to `temperature: false`, silently dropping the agent-level setting |
| [#40971](https://github.com/anomalyco/opencode/pull/40971) | feat(tui): expose prompt action commands | New feature | Exposes stable prompt-action commands (`form.option.previous`, etc.) to TUI plugins for form and permission prompts (#40953) |
| [#40931](https://github.com/anomalyco/opencode/pull/40931) | feat(core): continue subagent sessions | New feature | Adds optional `sessionID` input to resume existing foreground subagent sessions, preserving child history while validating parent ownership |
| [#40922](https://github.com/anomalyco/opencode/pull/40922) | feat(tui): queue prompts with option enter | New feature | `Option+Enter` / `Alt+Enter` queues prompts across TUI composer paths; queued work displays in a compact dock with `<count> queued · <first prompt>` summary |
| [#40929](https://github.com/anomalyco/opencode/pull/40929) | feat(core): bound tool output | New feature | Enforces configurable line and byte limits on top-level local tool text; retains full truncated text in managed files with 7-day cleanup; honors `metadata.truncated` markers |

## 5. Feature Request Trends

- **Context awareness & transparency** — The #6152 request for a session context usage panel (129 👍) signals strong demand for visibility into token consumption and context-window utilization, similar to Claude's `/context` command.
- **Multi-project workflow tooling** — Cross-project session pickers (#31932), session search (#38973), and per-directory stats (#37760) reflect a growing power-user base working across multiple repositories who need better session navigation and overview.
- **Prompt queuing & delivery semantics** — The queue-vs-steer feature (#32157, 67 👍) and the completed Option+Enter PR (#40922) show the community prioritizing fine-grained control over how interjected prompts interact with ongoing model responses.
- **Subagent session continuity** — The #40931 PR to continue subagent sessions indicates demand for resumable, stateful multi-turn subagent workflows rather than fire-and-forget spawns.
- **Usability polish** — Clickable links (#1168, 119 👍) and real-time web UI refresh (#40502) are perennial quality-of-life requests that remain unresolved.

## 6. Developer Pain Points

1. **Upstream provider outage (Go & Zen tiers)** — The dominant concern this period. Dozens of users across #38257, #38218, #38195, #39827, and others report that all paid models return `401 Request blocked by upstream provider` since 2026-07-21. Direct provider API keys work fine, confirming the issue is on OpenCode's proxy/billing layer, not the underlying providers. Free models remain unaffected.

2. **Session memory bloat** — Issue #32005 (addressed by PR #40861) highlights that session summaries previously stored full patch diffs, causing performance degradation in long-running sessions. This is a recurring architectural pain point (#17622, #20990 referenced).

3. **Configuration drift for custom models** — PR #40973 exposes that config-defined custom models silently drop agent-level settings (temperature, etc.) due to a default of `false`, creating inconsistent behavior between built-in and custom providers.

4. **Privacy & policy transparency** — Issue #39875 (44 👍) reflects community frustration over unilateral changes to privacy wording and the absence of clear telemetry/retention documentation, eroding trust among paying subscribers.

5. **Platform-specific UI bugs** — TUI freezes on Linux (#35494, #40871), PowerShell garbled output after CLI exit (#11748), and Windows 10 startup failures on Node 26 (#40957) indicate ongoing stability challenges across non-macOS environments.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-07

## 1. Today's Highlights
Pi v0.84.0 introduces a fullscreen TUI mode with sticky editor, independently scrollable transcript, and draggable scrollbars, marking a major UX shift for terminal‑based workflows. The community is actively refining the new selection/copy behavior, addressing TUI crashes on over‑wide lines, and improving multi‑click word selection. Meanwhile, several high‑visibility bugs around auto‑compaction, platform‑specific authentication, and agent‑reset state leaks have drawn significant discussion and early fixes.

## 2. Releases
**v0.84.0** – Adds **Fullscreen TUI mode** with runtime switching, a sticky editor/footer, independently scrollable transcript, and draggable scrollbars.  
[UI & Display docs](https://github.com/earendil-works/pi/blob/v0.84.0/packages/coding-agent/docs/settings.md)

## 3. Hot Issues
| # | Title | Status | Why It Matters | Community Reaction |
|---|-------|--------|----------------|-------------------|
| #7547 | How do you use Pi on Windows? What issues are you seeing? | OPEN | Windows adoption is critical; fragmented setup paths make it hard to prioritize fixes and documentation. | 22 comments, 1 👍 |
| #6879 | Auto‑compaction never triggers after context grows past 100% until provider overflow | OPEN | Compaction is essential for long sessions; failure forces manual intervention and risks context‑window rejections. | 12 comments, 15 👍 |
| #7128 | New default `PI_*` guideline over‑encourages unnecessary bash calls | OPEN | System‑prompt changes can bias agent behavior; this guideline causes noisy, unnecessary environment inspections. | 10 comments, 5 👍 |
| #5323 | Improve Vertex + GCP metadata server support | OPEN | Auth detection for Vertex is currently synchronous and fragile; better support expands cloud‑AI usability. | 7 comments, 1 👍 |
| #7413 | Compaction fails on GitHub Copilot GHE.com enterprise accounts | CLOSED | Enterprise users hit a hard block when compaction tries to summarize; normal chat works, but long sessions break. | 7 comments, 1 👍 |
| #7703 | `Agent.reset()` during an active run leaves an assistant‑only transcript | CLOSED | Reset while streaming corrupts transcript state; the fix rejects reset during active runs. | 4 comments, 0 👍 |
| #7702 | 400: `reasoning_content` must be passed back for DeepSeek models via opencode zen gateway | OPEN | DeepSeek V4 Flash requires reasoning‑content round‑tripping; without it, multi‑turn tool‑call conversations fail. | 4 comments, 0 👍 |
| #7691 | Anthropic login over SSH redirects to localhost instead of offering a code to copy | CLOSED | SSH‑based login flows are broken when the target machine lacks a browser; users expect a copy‑able auth code. | 4 comments, 0 👍 |
| #7720 | Allow disabling select‑to‑copy in fullscreen TUI mode | OPEN | Terminal power‑users often highlight text for their shell; accidental clipboard overwrites disrupt workflow. | 3 comments, 0 👍 |
| #7600 | `pi‑coding‑agent` leaks X11 connections, fills the X server client table | OPEN | Long‑running Pi processes on X11 can exhaust the 256‑client limit, breaking all X applications. | 3 comments, 0 👍 |

## 4. Key PR Progress
| # | Title | Status | Description |
|---|-------|--------|-------------|
| #7745 | fix(ai): preserve Gemini thought signatures in OpenAI completions | CLOSED | Captures `extra_content.google/thought_signature` from streamed tool calls and replays the signature on follow‑up requests. |
| #7742 | feat(ai): Ollama Cloud support | OPEN | Adds Ollama Cloud as a built‑in provider using `OLLAMA_API_KEY`, following existing provider patterns. |
| #7733 | fix(tui): correct multi‑click text selection | CLOSED | Fixes double‑click behavior so it no longer includes trailing whitespace or treats whitespace groups as words. |
| #7721 | fix(tui): avoid unwanted newlines when copying in fullscreen | CLOSED | Tracks which row belongs to which visual line, preventing wrapped lines from being pasted with inserted newlines. |
| #7710 | feat(agent): restore suspended harness operations | OPEN | Implements R3 of the harness‑v2 plan, allowing a new harness to be created from a session with existing local state. |
| #7715 | feat(agent): allow blocked tool calls to terminate | CLOSED | Adds an optional `terminate` hint to blocked `beforeToolCall` results, letting extensions signal that the agent should end its turn. |
| #7717 | fix(agent): reject reset during active runs | CLOSED | `Agent.reset()` now rejects while a run is in‑flight, preserving transcript and runtime state until the response settles. |
| #7680 | fix(tui): handle selection page keybindings | OPEN | Routes `tui.select.pageUp/pageDown` through built‑in selection components, editor autocomplete, and coding‑agent selectors. |
| #7718 | fix(tui): preserve scrollback on content‑driven full redraws | CLOSED | Prevents loss of terminal scrollback when streaming reflows a message above the current viewport. |
| #7681 | Support AGENTS.override.md as a per‑directory context override | CLOSED | Introduces `AGENTS.override.md` as the highest‑priority context file for a directory, layering with other directory contexts. |

## 5. Feature Request Trends
- **TUI interaction refinements** – Selection/copy behavior, word‑boundary double‑click, page‑scroll keybindings, and disabling auto‑copy are top requests, reflecting heavy terminal‑UI usage.
- **Platform‑specific onboarding** – Windows setup guidance, SSH‑based authentication, and Android/Termux paste support show demand for broader OS compatibility.
- **Provider/agent extensibility** – Ollama Cloud, Qwen Token Plan, Amazon Bedrock Mantle, and server‑side built‑in tools (e.g., DeepSeek web search) indicate growing interest in diverse model‑provider integrations.
- **State‑management robustness** – Fixes for `Agent.reset()` mid‑run, compaction triggers, and harness‑v2 recovery highlight a focus on reliable long‑session behavior.
- **Documentation & environment‑variable visibility** – Users want consistent env‑var docs, clear keybinding references, and better model‑list synchronization.

## 6. Developer Pain Points
- **Auto‑compaction not triggering** before context exceeds the window, forcing manual intervention and causing API rejections.
- **Terminal‑width crashes** in the TUI when a rendered line exceeds the terminal width, leading to uncaught exceptions.
- **Multi‑line paste breaks** on terminals without bracketed‑paste support (e.g., Termux), as carriage returns are interpreted as submit.
- **X11 connection leaks** in long‑running processes, eventually exhausting the server’s client table and breaking all X applications.
- **Model‑list drift** – Provider model lists (especially Qwen Token Plan and GLM on Fireworks) are out of sync with actual API availability, causing confusing errors.
- **Authentication redirects** – SSH‑based logins (Anthropic) redirect to localhost instead of offering a copy‑able code, breaking headless workflows.
- **Windows fragmentation** – Too many ways to run Pi on Windows make it difficult to focus core effort on fixes and documentation.
- **Over‑eager bash calls** – A default system‑prompt guideline biases the agent toward unnecessary environment‑variable inspections, cluttering output.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-07

## 1. Today's Highlights

Qwen Code v0.21.7 shipped with the removal of the 50-turn Goal limit, enabling uninterrupted long-running tasks, and added inline terminal image rendering for supported terminals. A nightly patch (v0.21.7-nightly) surfaced a CI fix for blocked autofix takeover admission, while the Qwen Live Host v0.1.0 installer became available for stable distribution. Community activity remains intense around hook regressions, desktop startup crashes on Windows, and trusted-folder security edge cases.

## 2. Releases

### v0.21.7 (Stable)
- **Removed the 50-turn limit for Goals** — tasks can now resume and continue beyond the previous hard boundary ([#8421](https://github.com/QwenLM/qwen-code/pull/8421)).
- **Inline terminal image rendering** enabled for KiTTY, Warp, and other supported terminals, allowing model outputs with images to render directly in the interactive CLI.
- CI improvements: Windows merge-queue tests now run on ECS ([#8386](https://github.com/QwenLM/qwen-code/pull/8386)).

### v0.21.7-nightly.20260807.fca8f3c1f
- Fix: surfaced blocked autofix takeover admission in CI ([#8410](https://github.com/QwenLM/qwen-code/pull/8410)).

### live-host-v0.1.0
- First stable Qwen Live Host installer feed released.

## 3. Hot Issues

| # | Issue | Why It Matters |
|---|-------|---------------|
| [#3203](https://github.com/QwenLM/qwen-code/issues/3203) | Qwen OAuth Free Tier Policy Adjustment | 150 comments — the most-discussed issue. Users are pushing back on a proposed reduction from 1,000 to 100 daily free requests. Closure triggered significant community concern. |
| [#8622](https://github.com/QwenLM/qwen-code/issues/8622) | 0.21.6 hook regression: PreToolUse/PostToolUse/PreCompact/SessionStart hooks never dispatched | P1 regression from v0.21.5 — hooks that gate tool execution silently stop firing. Directly impacts users relying on custom workflow automation. |
| [#8615](https://github.com/QwenLM/qwen-code/issues/8615) | Desktop v0.1.0 Windows crash on workspace open: EISDIR lstat 'C:' | P1 crash on startup for Windows users; bundled Node.js v22.20.0 fails with `EISDIR` when opening any workspace. Blocks new desktop adopters. |
| [#8643](https://github.com/QwenLM/qwen-code/issues/8643) | Trusted-folder bug: `.env` loaded from `DO_NOT_TRUST` ancestor | Security-critical: a workspace explicitly marked `DO_NOT_TRUST` can still have its parent's `.env` loaded because trust is evaluated only once at the start directory. |
| [#8627](https://github.com/QwenLM/qwen-code/issues/8627) | `DO_NOT_TRUST` overridden by ancestor `TRUST_FOLDER` | Related to #8643 — explicit distrust rules are silently ignored when an ancestor has a trust rule, allowing untrusted workspaces to inject bearer tokens. |
| [#8316](https://github.com/QwenLM/qwen-code/issues/8316) | Prompt not restored on Ctrl+C cancellation | UX friction: cancelling a prompt loses the input text, forcing re-typing. High daily-usage impact. |
| [#8557](https://github.com/QwenLM/qwen-code/issues/8557) | Terminal resize reprints transcript blocks on macOS | Scrollback duplication when shrinking terminal width in Warp on macOS — visual corruption of conversation history. |
| [#8584](https://github.com/QwenLM/qwen-code/issues/8584) | Anthropic model-ID parsing rejects dotted-minor aliases (`claude-opus-4.8`) | Proxy deployments using dotted minor versions (e.g., `claude-opus-4.8`) are rejected. Also lacks Opus 5 token limits. |
| [#8625](https://github.com/QwenLM/qwen-code/issues/8625) | Pinyin invisible when typing Chinese in Windows terminal | IME composition text (pinyin) is rendered invisibly, making Chinese input unusable in the CLI on Windows. |
| [#7634](https://github.com/QwenLM/qwen-code/issues/7634) | WSL + Windows Terminal: streaming text duplicated N times | Known bug with ConPTY — each character is re-rendered proportionally to output length. A top-voted community pain point. |

## 4. Key PR Progress

| # | PR | Description |
|---|-----|------------|
| [#8456](https://github.com/QwenLM/qwen-code/pull/8456) | fix(cli): scope startup warnings to dev sessions | Startup build warnings are now scoped to the dev session that produced them, preventing noise in production runs. |
| [#8436](https://github.com/QwenLM/qwen-code/pull/8436) | fix(triage): finalize status comment on cancellation | Cancellation was excluded from the triage status comment step; this fix ensures cancelled reviews are properly closed out. |
| [#8637](https://github.com/QwenLM/qwen-code/pull/8637) | feat(cli): mirror Live Host downloads through OSS | macOS Live Host onboarding now prefers the public OSS mirror with GitHub as fallback, including 60-minute timeout and integrity checks. |
| [#7897](https://github.com/QwenLM/qwen-code/pull/7897) | fix(cli): skip terminal redraw optimizer on WSL/ConPTY | Targets #7634 — disables the batched cursor-up optimizer that ConPTY mishandles, eliminating the N-times character duplication in WSL. |
| [#8614](https://github.com/QwenLM/qwen-code/pull/8614) | feat(web-shell): fullscreen view for right artifact panel | Adds an expand/collapse toggle to the Web Shell right panel for artifacts, subagents, and scheduled tasks. |
| [#8390](https://github.com/QwenLM/qwen-code/pull/8390) | feat(review): warn when bundle is older than review code | Reviews now warn before running if the bundle digest doesn't match the current working tree, preventing stale-bundle runs. |
| [#8658](https://github.com/QwenLM/qwen-code/pull/8658) | perf(review): move remote matching into CLI | `qwen review match-remote` subcommand parses fetch URLs structurally, reducing model-authored prose in `/review` runs. |
| [#8657](https://github.com/QwenLM/qwen-code/pull/8657) | fix(cli): preserve slash command names in narrow terminals | Command names stay intact when the completion menu lacks horizontal space; argument hints wrap instead of truncating the token. |
| [#8365](https://github.com/QwenLM/qwen-code/pull/8365) | fix(cli): improve slash command history feedback | Transient slash commands (auth, settings, status, help, theme) are excluded from visible TUI history, reducing clutter. |
| [#8465](https://github.com/QwenLM/qwen-code/pull/8465) | feat(core): checkpoint long-running Goal evidence | Adds durable evidence checkpointing for Goals approaching the hard evidence limit — pauses continuation and compresses evidence via a verifier tool. |
| [#8640](https://github.com/QwenLM/qwen-code/pull/8640) | fix(memory): refresh live instructions after memory writes | `/remember` now propagates persisted memory writes into the active session's live system instruction, closing a refresh gap. |
| [#8654](https://github.com/QwenLM/qwen-code/pull/8654) | feat(review): add repository context manifest | First real repo-context manifest declaring bounded review domains, related paths, recommended tests, and `.qwen/review` config support. |
| [#8440](https://github.com/QwenLM/qwen-code/pull/8440) | feat(channels): support group pairing | Group chats can now be approved once by stable chat ID and used by every member, with per-use approval storage. |
| [#8525](https://github.com/QwenLM/qwen-code/pull/8525) | fix(core): resolve Qwen 3.8 reasoning budget conflicts | Prevents `reasoning_effort` and `thinking_budget` from both being sent when they originate from different config layers. |
| [#8320](https://github.com/QwenLM/qwen-code/pull/8320) | feat(workflows): cooperative pause and resume | Whole-run pause/resume for Dynamic Workflows — scheduler stops dequeuing, in-flight work converges, and results gate until resume. |
| [#8388](https://github.com/QwenLM/qwen-code/pull/8388) | feat(review): capture-tui Phase 2 | `qwen review capture-tui` drives code under review in a private tmux server and captures rendered pixels for terminal-claim verification. |
| [#8619](https://github.com/QwenLM/qwen-code/pull/8619) | fix(desktop): strip Windows verbatim prefix from workspace paths | Replaces `std::fs::canonicalize` with `dunce::canonicalize` to fix the Windows `EISDIR` crash (#8615). |
| [#8569](https://github.com/QwenLM/qwen-code/pull/8569) | feat(feishu): enrich observed contact labels | Feishu contacts now resolve and store sender display names and group names alongside ID-based observations. |

## 5. Feature Request Trends

- **Long-running Goals without hard limits** — The removal of the 50-turn cap (#8421) reflects strong community demand for unbounded, resumable tasks. Related: evidence checkpointing (#8465) and cooperative workflow pause/resume (#8320).
- **Multimodal and voice integrations** — Issue #8629 proposes adding the `qwen-audio-agent` voice frontend to the README ecosystem. The Omni multimodal roadmap (#8197, #8185) continues tracking S3 upload reliability and file-recognition pipelines.
- **Terminal rendering fidelity** — Inline image support (v0.21.7), WSL/ConPTY fix (#7897), and prompt restoration on cancel (#8316) all address the same underlying demand: a smoother, more reliable CLI experience across platforms.
- **Review automation maturity** — Multiple PRs (#8390, #8658, #8654, #8388) show a push toward structured, deterministic review tooling: context manifests, remote matching subcommands, and TUI capture for evidence.
- **Cross-platform desktop parity** — Korean docs localization (#8551), desktop language persistence (#8592 / #8641), and Windows path handling (#8619) indicate ongoing effort to bring the Desktop app to parity with CLI across i18n and OS quirks.

## 6. Developer Pain Points

1. **Windows Desktop crashes on launch** — The `EISDIR lstat 'C:'` error (#8615) blocks new Windows Desktop users. A fix is in progress via `dunce::canonicalize` (#8619).
2. **Hook regression in v0.21.6** — Critical hooks (`PreToolUse`, `PostToolUse`, `PreCompact`, `SessionStart`) silently stopped dispatching (#8622). This breaks custom automation pipelines and is a top-priority regression.
3. **Trusted-folder security bypass** — Two related issues (#8643, #8627) show that `DO_NOT_TRUST` rules can be overridden by ancestor `TRUST_FOLDER` entries, potentially leaking `.env` credentials and bearer tokens into untrusted workspaces.
4. **Chinese IME input broken on Windows** — Pinyin composition text is invisible (#8625), making the CLI unusable for Chinese-speaking developers on Windows.
5. **WSL/ConPTY streaming duplication** — Characters render N times during streaming (#7634). A fix is pending in #7897 but has not yet landed in a release.
6. **OAuth free-tier policy reversal backlash** — Issue #3203 drew 150 comments as the community reacted strongly to a proposed 10× quota reduction, signaling high sensitivity around access costs.
7. **Animated GIF/inline image rendering gaps** — While v0.21.7 added inline image support, animated GIFs and certain terminal emulators remain unaddressed, with users requesting broader coverage.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-07

## 1. Today's Highlights

The project wrapped up the **command-boundary refactor epic** (#2870) and shipped Layer 5.3 of the staged rollout via PR #5255, consolidating palette, completion, and discovery filtering. A v0.9.4 release train completed its integration cycle (PR #5135), and several runtime API endpoints for memory, goals, and MCP lifecycle were exposed to external clients.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5250](https://github.com/Hmbown/CodeWhale/issues/5250) | Multiple API keys per provider | Users juggling DeepSeek, GLM, and other providers must currently overwrite keys manually — a daily friction point. |
| [#5244](https://github.com/Hmbown/CodeWhale/issues/5244) | Unknown model IDs silently fall back to 128K context | A 1M-window model can silently compact at 128K with no warning, wasting token budget. Open; 2 comments. |
| [#4978](https://github.com/Hmbown/CodeWhale/issues/4978) | Anthropic API 400 on `openmodel` compat layer | Intermittent `'type' must be in ["enabled","disabled","auto"]` errors make the OpenModel bridge unreliable. Closed. |
| [#5253](https://github.com/Hmbown/CodeWhale/issues/5253) | Nested subagent `max_depth` can widen root budget | A subagent can supply an explicit depth that exceeds the host's ceiling, breaking guaranteed recursion limits. Open; 1 comment. |
| [#4828](https://github.com/Hmbown/CodeWhale/issues/4828) | macOS underwater shell breaks `open` / `osascript` / `launchctl` | Post-v0.9.0, `exec_shell` on macOS returns exit code -54 for system commands. Downgrading to v0.8.67 resolves it. Closed. |
| [#5223](https://github.com/Hmbown/CodeWhale/issues/5223) | Mouse wheel scrolls input history instead of content | Long conversations are hard to review because scroll events hijack the composer history rather than the transcript. Closed. |
| [#4681](https://github.com/Hmbown/CodeWhale/issues/4681) | `<turn_meta>` blocks reappear on session reopen | Meta blocks that are hidden during an active session become visible again after restarting, cluttering the view. Closed. |
| [#5178](https://github.com/Hmbown/CodeWhale/issues/5178) | Admin digest POST returns `ok:true` while posting nothing | A false-success bug in the web admin endpoint; drafts reappear in Pending indefinitely. Closed. |
| [#5046](https://github.com/Hmbown/CodeWhale/issues/5046) | Fleet agents ignore configured role bindings | Models with generic roles + `model_strength: same` cloned the operator's model five times instead of respecting fleet config. Closed. |
| [#5035](https://github.com/Hmbown/CodeWhale/issues/5035) | Workflow authoring failures hidden by parallel fan-out | Failed parallel branches were silently treated as `null` and reported success, masking real orchestration errors. Release blocker. Closed. |

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5255](https://github.com/Hmbown/CodeWhale/pull/5255) | Layer 5.3: Palette, completion & discovery filtering | OPEN | Final layer of the command-boundary refactor; verifies acceptance criteria for user-command integration in the palette and slash-completion surfaces. |
| [#5242](https://github.com/Hmbown/CodeWhale/pull/5242) | Resume interrupted subagents from checkpoint | MERGED | `agents/followup` on `interrupted_continuable` children now actually resumes the run instead of queuing a dead-letter. |
| [#5240](https://github.com/Hmbown/CodeWhale/pull/5240) | Surface real wait elapsed time in tool content | MERGED | `duration_ms` is now visible in tool results, preventing the model from busy-polling short waits and misjudging long stalls. |
| [#5238](https://github.com/Hmbown/CodeWhale/pull/5238) | MCP Registry discovery with Registry-first selection | MERGED | Agents now consult the public MCP Registry for zero-env stdio servers before falling back to `exec_shell` or custom code. |
| [#5234](https://github.com/Hmbown/CodeWhale/pull/5234) | Fix mouse scroll hijacking input history | MERGED | Resolved the root cause in PR #5223 by preventing `EnableMouseCapture` from armning xterm alternate-scroll during active mouse capture. |
| [#5252](https://github.com/Hmbown/CodeWhale/pull/5252) | Subagent runtime-state root isolation | OPEN | Adds `EngineConfig::subagent_state_root` so embedding hosts can isolate child session state without affecting the parent cwd or file authority. |
| [#5077](https://github.com/Hmbown/CodeWhale/pull/5077) | Progressively disclose fresh context | MERGED | Keeps `AGENTS.md` / `CLAUDE.md` discovery eager, caps ambient skills block at 2,400 chars, and defers skill bodies to first-turn `load_skill`. |
| [#5246](https://github.com/Hmbown/CodeWhale/pull/5246) | Split shipping profile from local release gate | MERGED | Stops paying fat LTO on every pre-push build by decoupling `cargo build --release` from the shipping profile. |
| [#5245](https://github.com/Hmbown/CodeWhale/pull/5245) | Decouple HEAD SHA stamp from compilation | MERGED | Eliminates forced full rebuilds of `codewhale-tui` (682k lines) on every local commit by un-linking the embedded short SHA from the build trigger. |
| [#5131](https://github.com/Hmbown/CodeWhale/pull/5131) | Runtime API memory endpoints | OPEN | Adds `/v1/memory` endpoints (bounded inspection, lifecycle controls) gated behind `require_runtime_token`, enabling managed clients to query and manage active memory. |

## 5. Feature Request Trends

- **Multi-provider key management** — Issue #5250 surfaces repeated frustration with single-key storage; users want per-provider key persistence.
- **Model-capability transparency** — Issue #5244 highlights demand for explicit warnings when an unknown model ID falls back to a legacy context window.
- **Subagent isolation & resilience** — PR #5252 (state root isolation) and PR #5242 (checkpoint resume) both reflect community interest in robust, inspectable subagent lifecycles.
- **MCP ecosystem integration** — PR #5238 (Registry-first discovery) signals a push toward standardized, zero-config tool discovery across providers.
- **Runtime API extensibility** — PRs #5130–#5133 collectively expand the HTTP runtime boundary (MCP lifecycle, skills, goals, memory), responding to embedded-host and managed-client needs.

## 6. Developer Pain Points

1. **Build-performance tax** — The monorepo's HEAD-SHA stamp and fat-LTO profile forced full rebuilds of `codewhale-tui` on every commit (PRs #5245, #5246). Both have been addressed.
2. **macOS shell regression** — The v0.9.0 "underwater" shell broke system command invocation (`open`, `osascript`, `launchctl`) with exit -54 (#4828), a breaking change for macOS users that required a downgrade to recover.
3. **Subtle context-window fallback** — Unknown model IDs silently defaulting to 128K without any user-facing signal (#5244) risks silent quality degradation, especially for 1M+ window models.
4. **Input-history scroll hijacking** — Mouse-wheel events routing to the composer instead of the transcript (#5223, now fixed) created a poor UX for long conversations.
5. **Workflow error masking** — Parallel fan-out treating all failed branches as `null` and reporting success (#5035) made debugging orchestration failures opaque; now closed as a v0.9.4 release blocker.
6. **Single API key per provider** — Users managing multiple providers must manually overwrite keys each session (#5250), a recurring ask with no fix yet shipped.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*