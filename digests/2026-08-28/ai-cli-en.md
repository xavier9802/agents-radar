# AI CLI Tools Community Digest 2026-08-28

> Generated: 2026-08-28 10:57 UTC | Tools covered: 10

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



# Cross-Tool AI CLI Ecosystem Report — 2026-08-28

---

## 1. Ecosystem Overview

The AI CLI tool landscape is in a phase of rapid convergence and differentiation. All major tools are converging on multi-provider agent architectures, but community feedback reveals that **reliability and observability** remain the top unresolved needs across every project. Security hardening (restricted modes, auth resilience, provider-neutral design) is a shared priority, while platform-specific bugs—particularly on Windows—continue to erode trust in release cadences. The ecosystem is moving from "does it work" to "can I rely on it at scale."

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Releases (24h) | Release Cadence |
|---|---|---|---|---|
| **Claude Code** | 10 | 1 | v2.1.250, v2.1.248 | Steady; security-focused (`--restricted`) |
| **OpenAI Codex** | 10 | 10 | 3 α releases (`.alpha.6`–`.alpha.8`) | Aggressive alpha sprint ahead of `0.151.0` |
| **Gemini CLI** | 10 | 9 | v0.59.0-nightly | Nightly; core fixes (Git env, SSE, MCP) |
| **GitHub Copilot CLI** | 10 | 0 | v1.0.82-0, v1.0.81 | GA features; v1.0.81 regression churn |
| **Kimi Code CLI** | 6 | 3 | None | Slow; security dependency bumps only |
| **OpenCode** | 10 | 9 | v1.18.25, v1.18.24 | Weekly; Azure auth, Bedrock fixes |
| **Pi** | 10 | 11 | None | No release; TUI/provider hardening |
| **Qwen Code** | 11 | 10 | v0.22.2-nightly | Nightly; TUI migration work ongoing |
| **DeepSeek TUI** | 10 | 9 | None | No release; crate decomposition + native search PRs |
| **Grok Build** | — | — | None | Inactive this cycle |

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|---|---|---|
| **TUI visibility & streaming controls** | Codex, OpenCode, Pi, Qwen Code | Toggle auto-collapse of command output, hide tool calls, disable streaming for non-streaming providers |
| **Multi-account / profile switching** | Claude Code, OpenCode | Seamless rotation between personal/org accounts; per-session model overrides |
| **Subagent reliability & observability** | Gemini CLI, Codex, Copilot CLI, OpenCode | Agents hang or report false success; no trajectory visibility; no resume/steering controls |
| **Shell execution robustness** | Claude Code, Codex, Gemini CLI, DeepSeek TUI | Host crashes during handshake, shell escaping bugs, "Waiting input" hangs, interactive prompt blocks |
| **Auth resilience** | Claude Code, Codex, Copilot CLI, OpenCode | Auth loops on Windows, delayed magic-link emails, token expiry recovery, GHEC data-residency gaps |
| **Session resume fidelity** | Gemini CLI, Copilot CLI, Qwen Code | Resumed sessions lose plugin hooks, MCP configs, model overrides; silently drop state |
| **OpenTelemetry / observability** | Claude Code, Copilot CLI, Qwen Code | OTel support for web sessions, hook-exposed tracing context, auditable review outputs |
| **Provider neutrality** | DeepSeek TUI, OpenCode, Pi, Qwen Code | Move away from hard-coded provider gates; first-party search adapters; consistent API contract handling |
| **Enterprise auth & compliance** | Claude Code, OpenCode, Qwen Code, Copilot CLI | Entra ID OAuth, strict read-before-write guarantees, rubber-duck review audit trails |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Qwen Code | DeepSeek TUI | Pi | OpenCode | Copilot CLI | Kimi CLI |
|---|---|---|---|---|---|---|---|---|---|
| **Core focus** | Security-hardened CLI with `--restricted` mode | Fast-moving alpha; Guardian safety gating | Nightly core fixes; Git env consistency | Web-shell + channel integrations (DingTalk) | Crate decomposition + native search adapters | TUI fidelity + XDG compliance | Enterprise auth + billing | Enterprise GHEC integration | API round-trip consistency |
| **Target user** | Security-conscious teams, enterprises | Power users testing cutting-edge features | Developers needing daily reliability | Multi-provider Chinese ecosystem users | Linux desktop / multi-provider | Desktop/laptop TUI users | Open-source / proxy-provider users | GitHub ecosystem users | API-first / self-hosted users |
| **Technical approach** | Conservative releases; permission model tightening | Rapid alpha iteration; feature-flag tool gating | Nightly fixes; fail-closed security hardening | Daemon-centric; hot-reload providers | Monolith → decomposed crates; Rust-native | Modular TUI; per-provider adapter layer | Plugin system; session deep links | Minimal; focused on API contract fixes |

---

## 5. Community Momentum & Maturity

- **Most actively iterating:** **OpenAI Codex** (3 α releases in one day, 10 PRs merged, fast Guardian hardening) and **Qwen Code** (nightly releases, 10 active PRs, TUI migration underway). These projects are in rapid development cycles.
- **Steady with maturing communities:** **Claude Code** and **Gemini CLI** show consistent nightly/daily fix cycles with high-issue engagement. Gemini's subagent reliability issues and Claude's multi-account demand signal growing user bases.
- **Moderate momentum with technical debt:** **OpenCode** and **Pi** have strong PR throughput but are visibly wrestling with TUI rendering, provider contract drift, and cross-session isolation. Pi's closure of #2870 (XDG compliance) and #8774 (compaction) shows responsiveness.
- **Early-stage / smaller communities:** **Kimi Code CLI** and **Grok Build** show the least community activity this cycle, with Kimi focused on security bumps and Grok inactive.
- **Most technically ambitious:** **DeepSeek TUI** — the 682k-line crate decomposition epic (#5316) and simultaneous push for 5 native web-search adapters signals a project under significant architectural transition.

---

## 6. Trend Signals

1. **Windows remains the universal pain point.** Auth loops, trust-verification failures, and shell-path regressions affect Codex, Claude Code, Copilot CLI, and Gemini CLI. Any tool targeting enterprise adoption must resolve Windows desktop stability first.

2. **Subagent reliability is the #1 open problem.** Across Gemini CLI, Codex, Copilot CLI, and OpenCode, agents hang, report false successes, or lose context on resume. This is the ecosystem's most critical unreliability gap.

3. **Provider-agnosticism is accelerating.** DeepSeek's 6 native search adapters, OpenCode's provider-neutral auth, and Pi's per-provider compaction fixes all signal a move away from vendor lock-in toward consistent multi-provider abstractions.

4. **Observability is becoming table stakes.** Claude Code's OTel request, Copilot CLI's hook-exposed tracing, and Qwen Code's event-integration hooks show that enterprise users expect production-grade observability, not just CLI convenience.

5. **TUI rendering quality is a differentiator—and a liability.** Codex's GPU-waste complaint, Pi's one-word-per-line streaming bug, Qwen's ink flicker, and OpenCode's GNU Screen incompatibility all indicate that terminal rendering is an under-resourced layer with high user impact.

6. **Release cadence ≠ release quality.** Copilot CLI's v1.0.81 regression churn (memory writes, MCP stripping, plugin hook loss) and DeepSeek's v0.9.12 lock regression (#5630) show that speed without adequate QA erodes community trust faster than slow cadence builds it.

7. **Session resume is a minefield.** Nearly every tool has documented bugs in `--resume` behavior—lost hooks, dropped MCP configs, ignored model overrides. As users rely more on long-running and cross-session workflows, this gap will become a blocking enterprise concern.

---

*Report generated from community digest data as of 2026-08-28. Data sourced from GitHub issue and PR feeds across 10 AI CLI tool repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data as of 2026-08-28 · Source: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

### #1 — Hivemind: Zero-Cost Multi-Agent Orchestration (PR #1628)
**Status:** Open | **Author:** Hanishchow | [Link](https://github.com/anthropics/skills/pull/1628)
Delegates mechanical coding work to headless [opencode](https://opencode.ai) workers running on free models, while Claude Code retains planner/reviewer/merger authority. Addresses the core pain point of expensive-model context scarcity by splitting orchestration from execution.

### #2 — Self-Audit: Mechanical Verification + Four-Dimension Reasoning Gate (PR #1367)
**Status:** Open | **Author:** YuhaoLin2005 | [Link](https://github.com/anthropics/skills/pull/1367)
Pre-delivery audit skill that first mechanically verifies every claimed output file exists, then runs a four-dimension reasoning quality check ordered by damage severity. Universal across projects and tech stacks.

### #3 — ServiceNow Platform Skill (PR #568)
**Status:** Open | **Author:** Vanka07 | [Link](https://github.com/anthropics/skills/pull/568)
Broad ServiceNow assistant covering ITSM, ITOM, ITAM/SAM Pro, FSM, HRSD, CSM, SPM/PPM, Vulnerability Response, Security Incident Response, and IntegrationHub. Notable for its enterprise-platform breadth and sustained discussion (active through Aug 2026).

### #4 — Testing Patterns Skill (PR #723)
**Status:** Open | **Author:** 4444J99 | [Link](https://github.com/anthropics/skills/pull/723)
Covers the full testing stack: Testing Trophy philosophy, AAA-pattern unit testing, React component testing with Testing Library, and clear boundaries on what *not* to test.

### #5 — Document Typography Skill (PR #514)
**Status:** Open | **Author:** PGTBoos | [Link](https://github.com/anthropics/skills/pull/514)
Prevents orphan word wraps, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universally felt but rarely-requested quality gap.

### #6 — ODT Skill (PR #486)
**Status:** Open | **Author:** GitHubNewbie0 | [Link](https://github.com/anthropics/skills/pull/486)
OpenDocument Format skill covering creation, template filling, parsing ODT→HTML, and triggers on ODT/ODS/ODF/LibreOffice references. Fills a gap for open-standard document workflows.

### #7 — Skill Quality & Security Analyzer (PR #83)
**Status:** Open | **Author:** eovidiu | [Link](https://github.com/anthropics/skills/pull/83)
Two meta-skills for the marketplace: `skill-quality-analyzer` (structure, docs, examples across 5 dimensions) and `skill-security-analyzer`. Directly responds to community trust concerns (see Issue #492).

### #8 — Frontend-Design Skill Rewrite (PR #210)
**Status:** Open | **Author:** justinwetch | [Link](https://github.com/anthropics/skills/pull/210)
Revised for clarity and actionability — every instruction must be executable by Claude within a single conversation, with specific enough guidance to steer behavior without overreach.

---

## 2. Community Demand Trends (from Issues)

| Trend | Key Issues | Signals |
|---|---|---|
| **Trust & Security Boundaries** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments, 2 👍), [#83](https://github.com/anthropics/skills/pull/83) | Namespace impersonation fears; demand for skill-level security auditing |
| **Evaluation & Reliability Tooling** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍), [#1390](https://github.com/anthropics/skills/issues/1390), [#1602](https://github.com/anthropics/skills/pull/1602) | `run_eval.py` trigger bugs; MCP evaluation harness fabricating 0/N scores — community actively debugging the eval pipeline |
| **Enterprise Platform Coverage** | [#568](https://github.com/anthropics/skills/pull/568), [#1487](https://github.com/anthropics/skills/issues/1487) | ServiceNow demand; `claude-api` skill token bloat (156k tokens in one call) |
| **Agent Governance & Quality Gates** | [#412](https://github.com/anthropics/skills/issues/412), [#1385](https://github.com/anthropics/skills/issues/1385), [#1367](https://github.com/anthropics/skills/pull/1367) | Policy enforcement, adversarial review, pre-delivery verification — a coherent quality-gate movement |
| **Context Efficiency** | [#1329](https://github.com/anthropics/skills/issues/1329), [#1487](https://github.com/anthropics/skills/issues/1487) | Compact symbolic memory; complaints about eager token injection exhausting context windows |
| **Organizational Sharing** | [#228](https://github.com/anthropics/skills/issues/228) (16 comments, 8 👍) | Strong demand for org-wide skill libraries and direct sharing links |
| **Cross-Platform Compatibility** | [#1099](https://github.com/anthropics/skills/pull/1099), [#1050](https://github.com/anthropics/skills/pull/1050), [#29](https://github.com/anthropics/skills/issues/29) | Windows subprocess/PPIPE bugs; AWS Bedrock integration |

---

## 3. High-Potential Pending Skills

These PRs have active discussion and address clear community pain points — strong candidates for upstream:

| PR | Skill | Why It May Land |
|---|---|---|
| [#1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** — multi-agent delegation to free-model workers | Solves the #1 cost bottleneck; unique architecture |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit** — mechanical + reasoning quality gate | Fills a missing pre-delivery verification layer |
| [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow** — enterprise platform skill | Broad enterprise coverage with sustained engagement |
| [#514](https://github.com/anthropics/skills/pull/514) | **Document Typography** — typographic QC | Universally relevant, niche but high-impact |
| [#723](https://github.com/anthropics/skills/pull/723) | **Testing Patterns** — full testing stack | Completes the dev-toolchain skill set |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT** — OpenDocument skill | Open-standard gap fill; ISO-compliant format support |
| [#83](https://github.com/anthropics/skills/pull/83) | **Skill Quality & Security Analyzer** — meta-skills | Directly addresses Issue #492 trust concerns |
| [#1602](https://github.com/anthropics/skills/pull/1602) | **Evaluation infra fixes** — serialization, metrics, encoding | Fixes broken eval pipeline; high practical value |

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is for **quality-gating and trust infrastructure** — skills that verify, audit, and secure other skills and agent outputs — reflecting a maturing ecosystem where raw capability is becoming table-stakes and reliability, security, and cost-efficiency are the differentiators.

---



# Claude Code Community Digest — 2026-08-28

## 1. Today's Highlights
Anthropic shipped **v2.1.248** introducing a `--restricted` flag for security‑focused deployments, while **v2.1.250** delivers routine bug fixes and reliability improvements. Community attention remains on long‑running feature requests (multi‑account switching, OpenTelemetry support) and persistent platform‑specific bugs, especially on Windows.

## 2. Releases
**v2.1.250** – Bug fixes and reliability improvements.  
**v2.1.248** – Added `--restricted` (or `CLAUDE_CODE_RESTRICTED=1`) mode: removes built‑in command‑execution and code‑running tools (plus `WebFetch` unless explicitly listed via `--tools`), confines file tools to the working directory, refuses `bypassPermissions`, and ignores user/project/local settings files.

## 3. Hot Issues
1. **#18435** – Multi‑account management with easy profile switching in Claude Desktop.  
   *Why it matters:* Enables teams to rotate between personal and organizational accounts without reinstalling.  
   *Reaction:* 170 comments, 761 👍 — top‑voted enhancement across the repo.  
   [Link](https://github.com/anthropics/claude-code/issues/18435)

2. **#53247** – Claude Desktop fails to launch on Windows after a crash (orphaned Silo/Job Object).  
   *Why it matters:* Blocks Windows users from recovering from app crashes without a full logoff/reboot.  
   *Reaction:* 29 comments, 18 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/53247)

3. **#61682** – GitHub connector shows “Connected” but exposes no tools in Cowork (Windows).  
   *Why it matters:* MCP‑based GitHub integration appears broken for many Windows users.  
   *Reaction:* 24 comments, 24 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/61682)

4. **#49655** – Claude Desktop update fails with 0x80073CF6 when CoworkVMService is running.  
   *Why it matters:* Installation‑time bug that prevents upgrades on Windows. (Closed.)  
   *Reaction:* 23 comments, 10 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/49655)

5. **#82049** – Claude.ai sign‑in magic‑link emails delayed 2‑5 minutes.  
   *Why it matters:* Affects login speed across all Claude Code clients, especially when sessions expire.  
   *Reaction:* 19 comments, 36 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/82049)

6. **#34692** – PreToolUse/PostToolUse hooks do not fire for subagent tool calls.  
   *Why it matters:* Hooks are critical for observability and policy enforcement; the gap undermines reliability. (Closed.)  
   *Reaction:* 10 comments, 7 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/34692)

7. **#32364** – Support OpenTelemetry (OTel) configuration in Claude Code on the Web.  
   *Why it matters:* Enables tracing and monitoring for web‑based Claude Code sessions.  
   *Reaction:* 8 comments, 35 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/32364)

8. **#66440** – Syntax highlighting of C# disappears after a brief moment (macOS).  
   *Why it matters:* Degrades the editing experience for C# developers using the desktop app.  
   *Reaction:* 8 comments, 10 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/66440)

9. **#88405** – Symlinked files in `.claude/rules/` are not auto‑loaded (contradicts docs).  
   *Why it matters:* Breaks shared‑rules workflows and violates documented behavior.  
   *Reaction:* 6 comments, 4 👍.  
   [Link](https://github.com/anthropics/claude-code/issues/88405)

10. **#90299** – Fullscreen sticky prompt header stopped rendering in v2.1.247 (macOS).  
    *Why it matters:* Regression that removes a key usability feature for terminal users.  
    *Reaction:* 1 comment, 1 👍 (fresh report).  
    [Link](https://github.com/anthropics/claude-code/issues/90299)

## 4. Key PR Progress
- **#69226** – Update frontend‑design skill (closed). Bumps plugin version to 1.1.0 so installed copies pick up the improvements.  
  [Link](https://github.com/anthropics/claude-code/pull/69226)

*(No other PRs were updated in the last 24 hours.)*

## 5. Feature Request Trends
- **Multi‑account & profile switching** – Users want seamless account management within the desktop app (#18435).
- **Observability & telemetry** – OpenTelemetry support for web‑based sessions is frequently requested (#32364).
- **Session synchronization controls** – Desire for opt‑out of cross‑device sync and ability to keep sessions local (#78776).
- **Data‑safety guarantees** – Calls to restore strict read‑before‑overwrite for the Write tool to prevent accidental data loss (#88518).
- **Knowledge‑base integration** – Request to import Claude Projects knowledge bases into Claude Code sessions (#87528).
- **Token‑scoping visibility** – Need to verify which org/account a `setup‑token` belongs to after generation (#90298).

## 6. Developer Pain Points
- **Windows launch & update failures** – Orphaned job objects after crashes (#53247) and installation errors when CoworkVMService runs (#49655) repeatedly block Windows users.
- **Inconsistent permission modes** – Forked sessions sometimes start in auto‑mode even when the parent uses bypass permissions, causing mid‑task refusals (#89911).
- **Shell‑tool escaping issues** – The Bash tool silently collapses `\\` to `\`, corrupting regexes and Windows paths (#88561).
- **Hook & subagent gaps** – Pre/Post‑tool hooks do not fire for subagent calls (#34692), and LSP tools are pruned from subagent tool sets in interactive sessions (#84125).
- **Auth & credential loops** – Endless SecurityAgent prompts on macOS due to keychain partition mismatches (#87348), and delayed magic‑link emails (#82049).
- **Rule‑loading bugs** – Symlinked files in `.claude/rules/` are ignored despite documentation (#88405).
- **MCP connector instability** – GitHub connector appears connected but exposes no tools (#61682), and remote‑devices filesystem MCP fails due to unsupported `outputSchema` dialect (#88988).
- **Malware‑read reminders** – System reminders still cause refusals on legitimate code, especially in unattended cloud seats (#90326).

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-28

## 1. Today's Highlights

OpenAI shipped three rapid-fire Rust alpha releases (`.alpha.6` → `.alpha.8`) in a single day, signaling active pre-`0.151.0` development. The community's top concern remains **Windows desktop reliability** — auth loops, dead renders, and trust-verification regressions dominate the issue feed. Meanwhile, a cluster of Guardian review and subagent governance PRs landed closed, pointing to an imminent hardening push around model-tier safety and tool-gating.

---

## 2. Releases

| Version | Notes |
|---|---|
| `rust-v0.151.0-alpha.6` | Alpha build — see [Release](https://github.com/openai/codex/releases/tag/rust-v0.151.0-alpha.6) |
| `rust-v0.151.0-alpha.7` | Alpha build — see [Release](https://github.com/openai/codex/releases/tag/rust-v0.151.0-alpha.7) |
| `rust-v0.151.0-alpha.8` | Alpha build — see [Release](https://github.com/openai/codex/releases/tag/rust-v0.151.0-alpha.8) |

Three alpha iterations in 24 hours suggest a fast-moving release cadence ahead of the `0.151.0` milestone.

---

## 3. Hot Issues

**#16857** — *High GPU usage while the app is "thinking"* (42 comments · 👍 51)
> Tiny idle animation is driving unnecessary GPU load on macOS ARM. The highest-engagement issue of the day; users report the animation is effectively useless but keeps the GPU awake during long reasoning pauses.

**#39903** — *Add option to disable "Ran N commands" collapsing in TUI* (33 comments · 👍 60)
> The single most-liked issue. Power users want full command visibility rather than auto-collapsed summaries — a persistent UX friction point in the CLI/TUI.

**#41049** — *code-mode host exits during handshake (Windows, GPT-5.6)* (32 comments · 👍 1)
> Shell execution completely broken on a subset of Windows machines. Author reports the host crashes during initialization before any project can be read.

**#32759** — *GPT-5.6 Sol fails to execute shell commands: host exited during handshake* (18 comments · 👍 5)
> Same root failure as #41049 but on macOS ARM. Suggests a cross-platform regression in the code-mode host spawn path, not Windows-only.

**#35746** — *Paginated history drops valid flattened rollout records and reuses ordinals* (31 comments · 👍 1)
> Core data-integrity bug in the Rust CLI's rollout history. Reused ordinals risk session corruption and incomplete turn reconstruction.

**#40036** — *Codex stuck in login loop on Windows 11* (14 comments · 👍 0)
> Auth flow broken after a recent update. Part of a broader Windows auth cluster (see also #40761, #41136).

**#11747** — *Add `/add-dir` slash command for mid-session directory addition* (14 comments · 👍 45)
> Highly requested usability gap. Users currently must quit and restart with `--add-dir` to expand context, which breaks session state.

**#39855** — *Windows Remote: projectless chats fail trust verification with malformed path* (12 comments · 👍 4)
> Remote Control broken for users starting a chat without an open project. Malformed path objects trigger a trust error before any work begins.

**#18396** — *Add way to hide tool calls/output in TUI* (10 comments · 👍 28)
> Community wants a toggle to declutter the TUI view. Tool-call noise is a recurring complaint, especially in long sessions.

**#41269** — *Rollouts persist each command's stdout 3× per item — 60% of session bytes* (3 comments · 👍 0)
> Storage bloat bug reported today. The same output is stored in `stdout`, `aggregated_output`, and `formatted_output`, tripling disk usage for command-heavy sessions.

---

## 4. Key PR Progress

| PR | Status | Summary |
|---|---|---|
| [#41309](https://github.com/openai/codex/pull/41309) | ✅ Closed | **Honor required reviews when reusing Guardian scores** — fixes a loophole where cached low-risk scores could bypass full reviews on model-switch. |
| [#41308](https://github.com/openai/codex/pull/41308) | ✅ Closed | **Subagents follow the root service tier** — ensures tier-based restrictions (rate limits, model access) propagate correctly through the agent tree. |
| [#41292](https://github.com/openai/codex/pull/41292) | ✅ Closed | **Forward history note images to the model** — converts `images` into `input_image` function-call items, keeping image data out of logs. |
| [#41260](https://github.com/openai/codex/pull/41260) | ✅ Closed | **History backend enforces tool output budgets** — removes redundant client-side truncation now that the backend budgets output before encryption. |
| [#41243](https://github.com/openai/codex/pull/41243) | ✅ Closed | **Configurable gating for the `sleep` tool** — new `features.sleep_tool` config with `model_driven` and `always_on` modes. |
| [#41239](https://github.com/openai/codex/pull/41239) | ✅ Closed | **Surface auth recovery progress** — new events (`authRecoveryStarted`, `authRecoveryCompleted`) expose credential-refresh status to users. |
| [#41232](https://github.com/openai/codex/pull/41232) | ✅ Closed | **Expose PowerShell version in environment context** — new `powershell_shell_version` feature flag includes major/minor in `<environment_context>`. |
| [#41227](https://github.com/openai/codex/pull/41227) | ✅ Closed | **Use compatible PowerShell for elevated Windows sandbox commands** — Workaround for Store PowerShell (`WindowsApps`) being inaccessible to the sandbox account. |
| [#41223](https://github.com/openai/codex/pull/41223) | ✅ Closed | **Recency sorting for `project/list`** — projects now sort by newest activity by default, with an explicit `recencyAt` field. |
| [#10192](https://github.com/openai/codex/pull/10192) | ✅ Closed | **Migrate TUI to use app-server v2** — longstanding community-driven PR to move the TUI off the internal harness protocol to the public app-server protocol. |

---

## 5. Feature Request Trends

- **TUI visibility controls** — Multiple high-engagement requests (#39903, #11747, #18396) ask for finer-grained control over what the TUI displays: collapse toggles, mid-session directory injection, and tool-call hiding.
- **Configurable tool gating** — The `sleep` tool PR (#41243) extends a pattern of making built-in tools opt-in via `config.toml` feature flags, a direction users have requested for other tools as well.
- **Remote & cross-device UX** — Issues #39855, #39678, and #38128 show strong demand for reliable Remote Control across platforms (Windows, Android, macOS), especially for projectless sessions and security-restricted devices.
- **Auth resilience** — Repeated auth-loop bugs (#40036, #40761, #41136) and the new auth-recovery events PR (#41239) indicate a community priority: smoother sign-in and faster recovery from token expiry.

---

## 6. Developer Pain Points

1. **Windows desktop instability** — Auth loops, headless failures, and trust-verification regressions are the dominant frustration. At least 6 high-comment issues and 3 merged PRs this week target Windows-specific path, sandbox, and routing bugs.
2. **Shell execution fragility** — The "host exited during handshake" failure (#41049, #32759) blocks core functionality across both Windows and macOS, suggesting a regression in the code-mode process spawn path.
3. **Storage bloat from redundant output** — Issue #41269 documents that command stdout is stored three to four times per item, consuming ~60% of session bytes. Users running large codebases report disproportionate disk usage.
4. **Paginated history data loss** — Issue #35746 reveals ordinal reuse and dropped rollout records, which can corrupt session replay and make debugging long-running sessions unreliable.
5. **GPU/idle resource waste** — Issue #16857 highlights that even trivial UI animations keep the GPU active during long "thinking" pauses, a concern for laptop users and those on restricted power profiles.

---

*Data sourced from [github.com/openai/codex](https://github.com/openai/codex) · Generated 2026-08-28*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-28

## 1. Today's Highlights

Gemini CLI released nightly build **v0.59.0-nightly.20260828.g3c311beac**, bringing a batch of critical fixes for core shell execution, Git environment consistency, and SSE streaming reliability. The community is heavily focused on subagent reliability, with top-voted issues covering agent hangs, recovery after turn limits, and browser agent failures on Wayland.

## 2. Releases

**v0.59.0-nightly.20260828.g3c311beac** — [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260827.g3c311beac...v0.59.0-nightly.20260828.g3c311beac)

Automated nightly bump; no new feature highlights in the changelog snippet.

## 3. Hot Issues

| # | Title | Author | 👍 | Comments |
|---|-------|--------|----|----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | matei-anghel | 2 | 13 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | turmanticant | 8 | 8 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Leverage model's bash affinity via Zero-Dependency OS Sandboxing | abhipatel12 | 1 | 8 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess AST-aware file reads, search, and mapping | gundermanc | 1 | 7 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | rnett | 0 | 6 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory from retrying low-signal sessions indefinitely | SandyTao520 | 0 | 5 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | SandyTao520 | 0 | 4 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck "Waiting input" after completion | rnett | 3 | 4 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser_agent resilience: session takeover and lock recovery | hsm207 | 0 | 4 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | sigmaSd | 1 | 4 |

**Why they matter:** Subagent reliability dominates the top issues — the generalist agent hang (#21409) has 8 upvotes and a P1 priority, while #22323 exposes a critical correctness bug where subagent turn-limit failures are silently reported as success. Shell execution hangs (#25166) affect everyday UX for all users. Auto Memory issues (#26522, #26525) signal growing pains as the memory system matures. The Wayland browser failure (#21983) highlights a platform coverage gap.

## 4. Key PR Progress

| # | Title | Author | Size | Status |
|---|-------|--------|------|--------|
| [#28971](https://github.com/google-gemini/gemini-cli/pull/28971) | Fix truncated MCP tool names uniqueness | chandlerm923 | M | Open |
| [#28930](https://github.com/google-gemini/gemini-cli/pull/28930) | Drop unsafe `diff.external` override | sharonyao1127 | M | Open |
| [#28938](https://github.com/google-gemini/gemini-cli/pull/28938) | Keep GIT_CONFIG_* environment triplets consistent | Shivansh1980 | L | Open |
| [#28939](https://github.com/google-gemini/gemini-cli/pull/28939) | Avoid persisting interrupted response placeholder | Shivansh1980 | L | Open |
| [#28942](https://github.com/google-gemini/gemini-cli/pull/28942) | Strict boolean parsing for DEBUG env var | dylanyunlon | L | Open |
| [#29110](https://github.com/google-gemini/gemini-cli/pull/29110) | Route `read_file` through FileSystemService | Abdullah-Builds | M/L | Open |
| [#29099](https://github.com/google-gemini/gemini-cli/pull/29099) | Enforce fail-closed workspace trust, filter mcpServers | luisfelipe-alt | M/L | Open |
| [#29106](https://github.com/google-gemini/gemini-cli/pull/29106) | Flush final SSE event on EOF | AnupamKumar-1 | M | Open |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Prompt for consent on env changes, sanitize runtime vars | amelidev | M/L | Open |
| [#28804](https://github.com/google-gemini/gemini-cli/pull/28804) | Evals tools expansion (read_many_files, MCP, docs) | ved015 | L | Closed |

**Highlights:** A cluster of P1 core fixes landed addressing Git environment sanitization (#28930, #28938), interrupted response artifacts (#28939), and DEBUG parsing (#28942). Security hardening continues with workspace trust enforcement (#29099) and extension env consent (#28863). The MCP tool name uniqueness fix (#28971) resolves a real collision bug. PR #29110 corrects a long-standing inconsistency where `read_file` bypassed `FileSystemService` unlike its write counterparts.

## 5. Feature Request Trends

- **AST-aware codebase tools** — Multiple linked issues (#22745, #22746, #19561) push for surgical file reads via AST parsing (tilth/glyph) to reduce context bloat and improve precision over naive grep/read patterns.
- **Subagent visibility & sharing** — #22598 requests subagent trajectories be surfaced via `/chat share`, enabling review and evaluation of subagent behavior.
- **Persistent task tracking** — #18836 proposes replacing in-context `WriteToDo` with file-based CRUD task tracking to eliminate context rot and cross-session memory loss.
- **Zero-dependency OS sandboxing** — #19873 advocates leveraging the model's native bash affinity with sandboxed execution rather than abstracting it away.
- **Browser agent resilience** — #22232 and #21983 together signal demand for better session takeover, lock recovery, and Wayland support in the browser subagent.

## 6. Developer Pain Points

1. **Subagent reliability** — The single biggest theme: agents hang (#21409), fail to use skills/subagents organically (#21968), report false successes on turn-limit exhaustion (#22323), and lack visible trajectories (#22598). Debugging subagent behavior remains opaque.
2. **Shell execution hangs** — Commands completing successfully still leave the CLI stuck in "Awaiting user input" (#25166), and interactive prompts (e.g., Vite scaffolding) cause infinite blocks (#22465).
3. **Git environment instability** — Multiple issues around `GIT_CONFIG_*` sanitization becoming unparsable (#28938), unsafe `diff.external` overrides (#28930), and the model creating stray temp scripts (#23571) create friction during version-controlled workflows.
4. **Auto Memory quality** — Low-signal sessions are retried indefinitely (#26522), invalid patches are silently dropped (#26523), and deterministic redaction is missing (#26525), raising both performance and security concerns.
5. **Tool registration collisions** — MCP tool name truncation can produce duplicate registry names (#28971), and the system errors with 400 responses beyond 128 tools (#24246), limiting extensibility.
6. **Platform gaps** — Wayland browser agent failure (#21983) and Windows long-path issues (#28926) indicate incomplete cross-platform coverage.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-28

## 1. Today's Highlights

v1.0.82-0 landed with fixes for the new plugins dashboard (now GA, opt-out via `PLUGINS_DASHBOARD=false`), MCP 2026-07-28 spec support across CLI/SDK/IDE, and OpenTelemetry hook exposure. Meanwhile, v1.0.81 continues to surface regressions: memory writes, MCP server stripping, and session-resume issues are driving the most community discussion this week.

## 2. Releases

| Version | Date | Highlights |
|---|---|---|
| **v1.0.82-0** | 2026-08-28 | Plugins dashboard enabled for all; MCP 2026-07-28 support shipped to CLI, SDK, IDE, and in-memory clients; hooks now receive current OpenTelemetry context. |
| **v1.0.81** | 2026-08-27 | See release notes above; multiple follow-up fixes in prereleases (see Hot Issues). |

## 3. Hot Issues

1. **[Bug] Runaway FileWatch host-event loop freezes TUI, grows debug log to 13 GB** — [#4612](https://github.com/github/copilot-cli/issues/4612)
   A tight loop on resumed/long-running sessions emits continuous `FileWatch` host events, unresponsive TUI, and massive log bloat. ⭐1 — high-severity for power users.

2. **[Bug] `store_memory` fails in v1.0.81 prereleases: `Instance id is required`** — [#4535](https://github.com/github/copilot-cli/issues/4535)
   Native memory writer invoked without a required instance ID; blocks any feature depending on `store_memory`. 7 comments.

3. **[Bug] Terminal UI dead on parallel subagent turns** — [#4533](https://github.com/github/copilot-cli/issues/4533)
   Input and scroll freeze at the moment a turn spawns a parallel subagent block; runtime continues working. Affects `1.0.81-4/5`.

4. **[Bug] `copilot -p` returns 401 on GHEC data-residency tenants since 1.0.81-1** — [#4527](https://github.com/github/copilot-cli/issues/4527)
   Prompt mode hits `api.githubcopilot.com` instead of the tenant endpoint; interactive mode works with same creds. ⭐3 — enterprise-impacting.

5. **[Bug] `session.resume` silently ignores the `model` parameter** — [#4645](https://github.com/github/copilot-cli/issues/4645)
   Resuming a session with a different model keeps the stale persisted model with no error. Affects scripted workflows.

6. **[Bug] `--additional-mcp-config` servers dropped during startup reconciliation in 1.0.81-11** — [#4636](https://github.com/github/copilot-cli/issues/4636)
   Server is discovered, then immediately removed with `session.mcp_server_removed`. Regression from 1.0.81.

7. **[Bug] Plugin hooks not loaded on `--resume`** — [#4629](https://github.com/github/copilot-cli/issues/4629)
   `loadDeferredRepoHooks()` runs only on fresh sessions; resumed sessions miss all plugin hooks.

8. **[Bug] Compaction fails with `Tool choice must be auto` on custom models** — [#4646](https://github.com/github/copilot-cli/issues/4646)
   Both manual `/compact` and automatic compaction error out when using a registered custom model (e.g. `~z-ai/glm-latest`).

9. **[Bug] Rubber-duck reviews leave no verifiable record** — [#4621](https://github.com/github/copilot-cli/issues/4621)
   Critiques, model provenance, and findings are lost at session end — raises auditability and independence concerns.

10. **[Bug] `userPromptTransformed` hook skipped for steering messages** — [#4640](https://github.com/github/copilot-cli/issues/4640)
    When a user message arrives while the agent is mid-turn, it's delivered as steering without invoking the hook; injected standing instructions are silently dropped.

## 4. Key PR Progress

No pull requests were updated in the last 24 hours on `github.com/github/copilot-cli`.

## 5. Feature Request Trends

- **Named-session auto-resume**: `--name` currently only creates new sessions; users want it to resume an existing session with that name ([#4642](https://github.com/github/copilot-cli/issues/4642)).
- **Published JSON Schema for `settings.json`** to enable editor autocomplete and validation ([#4641](https://github.com/github/copilot-cli/issues/4641)).
- **Auditable review outputs** — rubber-duck review results, model provenance, and findings should persist beyond the session for compliance workflows ([#4621](https://github.com/github/copilot-cli/issues/4621)).
- **Better context-window reporting** — model details currently double-count by summing prompt + output limits instead of using `max_context_window_tokens` ([#4638](https://github.com/github/copilot-cli/issues/4638)).
- **Session checkpoint transparency** — users want compaction events to reliably appear as checkpoints in `/session checkpoints` ([#4643](https://github.com/github/copilot-cli/issues/4643)).

## 6. Developer Pain Points

- **Regression churn around v1.0.81**: memory writes, MCP config stripping, plugin hooks, and tool-search tokenization all regressed in the same release window, eroding trust in the prerelease cadence.
- **Session resume is fragile**: plugins don't load ([#4629]), model overrides are ignored ([#4645]), and additional MCP configs are discarded ([#4636]) — every `--resume` path has a known bug.
- **Enterprise auth gaps**: prompt mode (`-p`) and custom-model compaction both hit walls on GHEC / data-residency tenants ([#4527](https://github.com/github/copilot-cli/issues/4527), [#4646](https://github.com/github/copilot-cli/issues/4646)).
- **TUI reliability under load**: runaway event loops ([#4612](https://github.com/github/copilot-cli/issues/4612)), input freeze on parallel subagents ([#4533](https://github.com/github/copilot-cli/issues/4533)), and low-contrast input fields ([#4648](https://github.com/github/copilot-cli/issues/4648)) all degrade day-to-day UX.
- **MCP configuration instability**: nested shell expansion corruption ([#4239](https://github.com/github/copilot-cli/issues/4239)), Python-to-pipx rewrite ([#1385](https://github.com/github/copilot-cli/issues/1385)), and Windows `npx` spawn failures ([#3576](https://github.com/github/copilot-cli/issues/3576)) remain unresolved.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-28

## 1. Today's Highlights

The most notable activity is a plan-mode infinite-loop bug (#2623) affecting K3 on Linux, and a security-driven dependency bump for `asyncssh` to patch two GHSA advisories (#2622). Community sentiment is mixed: a frustrated API-design complaint (#2621) garnered the only upvotes today, while documentation guidance on `openai_legacy` provider config landed with zero engagement.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Status | Why It Matters | Community Reaction |
|---|-------|--------|----------------|-------------------|
| #2623 | Plan mode agent loops indefinitely on Bash echo / ReadFile | OPEN | Agents in plan mode should terminate after exploration; an infinite loop wastes tokens and stalls workflows. Reported on kimi-code 0.38.0 + K3. | New, 1 comment, 0 👍 |
| #2621 | API returns empty `content` then rejects it on round-trip | OPEN | The Kimi API returns messages with empty `content`, but rejects the same payload when callers echo it back, forcing a workaround in user code (and reportedly in `kimi-cli` itself). | 0 comments, 1 👍 |
| #2624 | Docs: `openai_legacy` hosted `/v1` example | OPEN | Clarifies three common misconfigurations (`type` must be `openai_legacy`, not `openai_responses`; endpoint matters). Useful for self-hosted Chat Completions setups. | New, 0 comments |
| #1211 | Notion Remote MCP creds not stored beyond active session | CLOSED | MCP credential persistence is critical for long-running sessions; this was filed by a macOS M4 user on v1.12.0. Now closed, likely resolved. | 3 comments, 0 👍 |
| #1272 | JetBrains AI Assistant / ACP cannot recognize dropped files | CLOSED | Users expect files dropped into the editor to be auto-detected by the AI; requiring explicit paths is a friction point. Closed. | 1 comment, 0 👍 |
| #1279 | Feature Request: Native git-ai integration for AI code attribution | CLOSED | Proposes native `git-ai` support for per-line AI attribution in `git blame`, aligned with the emerging vendor-agnostic `git-ai` standard. Closed. | 0 comments |

## 4. Key PR Progress

| # | Title | Type | Description |
|---|-------|------|-------------|
| #2622 | `deps: bump asyncssh to 2.23.1 in pykaos` | Security | Addresses GHSA-2wxc-x7rj-hg8f and GHSA-qr67-gv47-xwwh by upgrading `asyncssh` from 2.21.1 → 2.23.1 in the `pykaos` workspace. |
| #2176 | `fix(hooks): extract text from ContentPart for UserPromptSubmit` | Bug Fix | Resolves #2148 — the `UserPromptSubmit` hook received an empty `prompt` when `user_input` was a `list[ContentPart]` (the default), because only the `str` branch was handled. |
| #2595 | `fix(StrReplaceFile): refuse to edit files that are not valid UTF-8` | Bug Fix | Resolves #2591 — previously, `StrReplaceFile` decoded invalid UTF-8 bytes with `errors="replace"`, corrupting unrelated file content by writing U+FFFD. Now refuses to edit non-UTF-8 files. |

## 5. Feature Request Trends

- **Provider configuration ergonomics**: Issue #2624 highlights ongoing confusion around `openai_legacy` vs `openai_responses` provider types, suggesting a need for clearer docs or CLI validation.
- **AI code attribution**: Issue #1279 reflects sustained interest in standardising AI-generated-code tracking (via `git-ai`) directly into tooling.
- **File/drop-zone integration**: Issue #1272 signals user expectation that dropped files should be auto-discovered without manual path specification in editor integrations.
- **MCP credential persistence**: Issue #1211 (now closed) pointed to a need for longer-lived credential storage beyond session boundaries.

## 6. Developer Pain Points

1. **API round-trip inconsistency** (#2621): The Kimi API returns messages with empty `content` but rejects them on echo-back, forcing developers to write custom filtering logic. This was severe enough that the maintainers' own `kimi-cli` was reportedly patched to work around it — a signal worth addressing at the API level.
2. **Plan-mode agent loops** (#2623): Agents that fail to exit plan mode after exploration create token waste and indefinite hangs, a reliability concern for automated workflows.
3. **Hook system missing `ContentPart` support** (#2176): The `UserPromptSubmit` hook silently received empty prompts for structured message types, a subtle bug that breaks regex-based automation expecting hook payloads.
4. **Non-UTF-8 file corruption** (#2595): `StrReplaceFile` silently corrupted binary/non-UTF-8 files by replacing invalid bytes with U+FFFD — a data-integrity risk for projects that mix encodings.

---

*Sources: [MoonshotAI/kimi-cli Issues](https://github.com/MoonshotAI/kimi-cli/issues) · [Pull Requests](https://github.com/MoonshotAI/kimi-cli/pulls)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-28

## 1. Today's Highlights

OpenCode v1.18.25 shipped with a critical Azure authentication fix enabling CLI sign-in without Bun, while v1.18.24 addressed Bedrock reasoning response caching and expanded Entra ID support. Community attention is dominated by the long-standing demand to disable streaming mode (#785, 38 👍) and ongoing billing/usage reporting discrepancies across OpenCode Go plans.

## 2. Releases

### v1.18.25
- **Bugfix:** Azure authentication now works with Azure CLI sign-in without requiring Bun as a runtime dependency.

### v1.18.24
- **Bugfix:** Bedrock reasoning responses no longer cached into unreplayable empty messages.
- **Improvement:** Azure providers can now authenticate via Microsoft Entra ID through the Azure CLI instead of requiring an API key.
- **Improvement:** V1 now reads supported V2 config fields for forward-compatible configuration handling.

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|-----|----------------|
| [#785](https://github.com/anomalyco/opencode/issues/785) | Disable streaming mode | 33 | 38 | High-priority compatibility need — proxy providers like Credal OpenAI don't support streaming, blocking entire user segments. |
| [#6536](https://github.com/anomalyco/opencode/issues/6536) | Mobile App [CLOSED] | 16 | 49 | Largest community demand for a native mobile experience; currently users are stuck with mobile browsers. |
| [#38255](https://github.com/anomalyco/opencode/issues/38255) | Discrepancy in Go usage dashboard | 10 | 0 | Usage telemetry inconsistency — users hit weekly limits while granular dashboards show minimal spend, causing confusion and workflow disruption. |
| [#45278](https://github.com/anomalyco/opencode/issues/45278) | Payment declined after 3 months | 7 | 1 | Subscription retention risk — a previously working payment method is suddenly declined with no card or bank changes. |
| [#45867](https://github.com/anomalyco/opencode/issues/45867) | Muse Spark 1.2 prompt cache miss on Zen Go | 5 | 0 | Intermittent cache misses on a production model endpoint, directly impacting cost and latency for enterprise users. |
| [#32985](https://github.com/anomalyco/opencode/issues/32985) | GNU Screen compatibility issues | 4 | 3 | Color rendering, copy/paste, and mouse support broken inside GNU Screen — limits use in managed/remote terminal environments. |
| [#33940](https://github.com/anomalyco/opencode/issues/33940) | Undo in one session reverts all sessions | 4 | 2 | Cross-session undo pollution is a significant UX regression for users managing multiple parallel workflows. |
| [#41206](https://github.com/anomalyco/opencode/issues/41206) | Go weekly/monthly quota mismatch | 4 | 1 | Reinforces the usage dashboard inconsistency theme (#38255) — quota limits fire prematurely against incorrect counters. |
| [#38550](https://github.com/anomalyco/opencode/issues/38550) | Manual todo management | 4 | 2 | Users need direct control over the agent's todo list when the agent forgets to update or clear items. |
| [#21658](https://github.com/anomalyco/opencode/issues/21658) | Azure AI Foundry Entra OAuth auth | 4 | 10 | Request for native Microsoft Entra OAuth support — partially addressed in v1.18.24 but still requested as a first-class feature. |

## 4. Key PR Progress

| # | Title | Type | Summary |
|---|-------|------|---------|
| [#45917](https://github.com/anomalyco/opencode/pull/45917) | docs: add opencode-local-context | New | Introduces a plugin for local agent context management, enabling `{env:SECRET}` syntax in AGENTS.md and custom agent configs. |
| [#45103](https://github.com/anomalyco/opencode/pull/45103) | feat(desktop): deep links for sessions | Feature | Adds `opencode://open-session?server=...&session=...` URL scheme so Desktop can open existing sessions from links. |
| [#45915](https://github.com/anomalyco/opencode/pull/45915) | fix(format): bound formatter subprocesses | Bugfix | Adds timeout and abort channel to formatter subprocesses, preventing hangs from tools like `mix format` or `ktlint`. |
| [#45609](https://github.com/anomalyco/opencode/pull/45609) | fix(core): skip file watcher on roots | Bugfix | Prevents the file watcher from targeting filesystem roots (C:/, /), eliminating permission errors and resource waste. |
| [#45607](https://github.com/anomalyco/opencode/pull/45607) | fix(server): reset session on async prompt failure | Bugfix | Resolves sessions stuck in `busy` state after async prompt errors by resetting status to `idle`. |
| [#45557](https://github.com/anomalyco/opencode/pull/45557) | fix(opencode): atomic auth.json writes | Bugfix | Serializes and atomically writes `auth.json` to prevent concurrency-related corruption. |
| [#28326](https://github.com/anomalyco/opencode/pull/28326) | feat(server): reverse proxy base path | Feature | Adds `--base-path` flag for deploying OpenCode behind reverse proxies under subpaths. |
| [#45903](https://github.com/anomalyco/opencode/pull/45903) | fix(webfetch): decode using declared charset | Bugfix | Respects `charset` from `Content-Type` headers and HTML `<meta charset>` instead of forcing UTF-8, fixing mojibake on GBK/Shift_JIS pages. |
| [#45898](https://github.com/anomalyco/opencode/pull/45898) | fix(core): glob requires external_directory approval | Bugfix | Adds permission checks for `glob` tool when searching outside the session location — closes a security gap. |
| [#45894](https://github.com/anomalyco/opencode/pull/45894) | fix(edit): write newString literally | Bugfix | Prevents `String.prototype.replace` from interpreting `$` replacement patterns in model-generated edit strings. |

## 5. Feature Request Trends

- **Streaming toggle:** The #1 compatibility feature request (#785) — users with proxy providers or enterprise gateways that don't support streaming need a graceful fallback.
- **Mobile native app:** #6536 remains the most-upvoted open feature (49 👍), with users demanding an experience beyond mobile browsers.
- **Agent autonomy controls:** Manual todo management (#38550) and subagent resume/steering (#36423) reflect demand for finer-grained user oversight over agent behavior.
- **Multi-session isolation:** Undo cross-contamination (#33940) and session switching performance (#45887) point to a need for stronger session boundaries as multi-task workflows scale.
- **Enterprise auth integration:** Azure Entra ID OAuth (#21658) and base-path reverse proxy support (#28326) signal growing enterprise deployment scenarios.
- **Session deep links:** PR #45103 addresses the need to share and reopen specific sessions from external contexts.

## 6. Developer Pain Points

- **Billing and quota opacity:** Three separate issues this week (#38255, #41206, #45899) report usage dashboard inaccuracies — quota limits firing prematurely, percentages calculating incorrectly, and credits not reflecting actual spend. This is the most recurring operational frustration.
- **Subscription/payment failures:** Users reporting sudden payment declines (#45278) and subscriptions not activating post-payment (#45907, #45893) indicate friction in the monetization pipeline.
- **Terminal environment incompatibility:** GNU Screen (#32985), tmux + ConnectBot scrolling (#45871), and Windows ARM64 native build failures (#45875) show that OpenCode's TUI layer struggles in non-standard terminal configurations.
- **Cross-session state leakage:** Undo operations in one session affecting others (#33940) and subagent tools lacking resume/steering in v2 (#36423) suggest regressions in session isolation as the product matures.
- **Tool correctness bugs:** A cluster of skyzhao1223 fixes this week (#45910, #45911, #45912, #45902, #45906, #45898, #45894, #45888) addresses glob truncation loss, hidden-file exclusion, trailing newline injection, webfetch charset handling, XHTML rendering, and edit-string dollar-sign expansion — indicating the V2 tooling layer needs continued hardening around edge cases.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-28

## 1. Today's Highlights

Pi saw a wave of TUI rendering and streaming fixes land in the last 24 hours, including a fix for soft line breaks in thinking blocks, a regression fix for `HttpsProxyAgent` with proxy configurations, and a CPU-stall issue with OpenRouter thinking models. Several issues were also closed around macOS Terminal crashes, compaction failures on OpenAI Responses models, and the Windows `shellPath` config not being honored in `!`-command resolution.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Title | Status | Comments | 👍 |
|---|-------|--------|----------|----|
| [#2870](https://github.com/earendil-works/pi/issues/2870) | Follow XDG Base Directory | ✅ Closed | 20 | 52 |
| [#8584](https://github.com/earendil-works/pi/issues/8584) | TUI row corruption during streaming: assistant text rendered one word per line | 🔄 Open | 14 | 6 |
| [#6922](https://github.com/earendil-works/pi/issues/6922) | Default model cannot be a llama.cpp model: startup shows "No models available" | ✅ Closed | 12 | 14 |
| [#8774](https://github.com/earendil-works/pi/issues/8774) | Compaction fails on OpenAI Responses models: tool_choice sent without tools (400) | ✅ Closed | 2 | 0 |
| [#8776](https://github.com/earendil-works/pi/issues/8776) | Crash: getContextUsage reads totalTokens when assistant usage is undefined | ✅ Closed | 1 | 0 |
| [#8711](https://github.com/earendil-works/pi/issues/8711) | TUI pegs 100% CPU and freezes while streaming OpenRouter thinking (GLM-5.3-flash) | ✅ Closed | 2 | 1 |
| [#8610](https://github.com/earendil-works/pi/issues/8610) | Regression in v0.84.3: 'HttpsProxyAgent is not a constructor' with proxy | ✅ Closed | 4 | 0 |
| [#8624](https://github.com/earendil-works/pi/issues/8624) | Kitty key-release sequences get typed into editor as literal text | ✅ Closed | 2 | 0 |
| [#8779](https://github.com/earendil-works/pi/issues/8779) | DeepSeek thinking model: 400001 'reasoning_content must be passed back' | ✅ Closed | 1 | 0 |
| [#8762](https://github.com/earendil-works/pi/issues/8762) | Session list fully parses every session file even though only names are displayed | ✅ Closed | 2 | 0 |

**Why they matter:**

- **#2870** — The top-voted open-issue legacy ticket: Linux users have long complained that Pi cluttered `$HOME` instead of following the XDG Base Directory spec. Its closure signals a major dev-experience win.
- **#8584** — An open, actively reproduced streaming-corruption bug where assistant text renders one word per line after long tool output. Still unresolved and affects wide-terminal workflows.
- **#6922** — Users couldn't set a llama.cpp model as default without hitting a "No models available" error at startup; closing unblocks a common local-model setup path.
- **#8774** — Compaction (context summarization) was silently failing on OpenAI Responses models because the provider sent `tool_choice` without a `tools` list. A real regression for anyone using auto-compact.
- **#8776** — A null-pointer crash when assistant usage metadata is missing after shell commands, affecting edge-case provider responses.
- **#8711** — A severe CPU-stall regression tied to how reasoning details are accumulated during streaming; the TUI became unresponsive under sustained OpenRouter thinking output.
- **#8610** — A v0.84.3 regression where code-splitting broke the `HttpsProxyAgent` import, killing all proxy-dependent Google Vertex flows.
- **#8624** — Kitty terminal key-release escape sequences leaking as literal text into the editor when split across stdin chunks.
- **#8779** — DeepSeek reasoning models now require `reasoning_content` to be echoed back on tool-only turns; Pi was dropping it, triggering 400 errors.
- **#8762** — Session-resume selector was unnecessarily parsing entire JSONL files, causing slowdowns with large sessions.

## 4. Key PR Progress

| # | Title | Status | Author |
|---|-------|--------|--------|
| [#8775](https://github.com/earendil-works/pi/pull/8775) | Remove issue-specific regression test placement rule | 🔄 Open | davidbrai |
| [#6848](https://github.com/earendil-works/pi/pull/6848) | Add retry logic to compaction summarization for transient stream failures | ✅ Closed | PiedPiper911 |
| [#8766](https://github.com/earendil-works/pi/pull/8766) | Make write and edit output easier to scan | 🔄 Open | Panoplos |
| [#8674](https://github.com/earendil-works/pi/pull/8674) | Render markdown soft line breaks as spaces, not hard breaks | ✅ Closed | manojbajaj95 |
| [#8764](https://github.com/earendil-works/pi/pull/8764) | Honor settings.shellPath for config/header '!' command resolution | ✅ Closed | EralChen |
| [#8262](https://github.com/earendil-works/pi/pull/8262) | Dispatch hooks on every turn-start path (cancellable turn preflight) | 🔄 Open | LogosZR |
| [#8731](https://github.com/earendil-works/pi/pull/8731) | Allow disable copy on fullscreen; Ctrl+X copies selection | ✅ Closed | cristinaponcela |
| [#8744](https://github.com/earendil-works/pi/pull/8744) | Add opt-in overlay selection exclusion | 🔄 Open | wutongyuonce |
| [#8723](https://github.com/earendil-works/pi/pull/8723) | Expose https-proxy-agent named export | ✅ Closed | rwachtler |
| [#8743](https://github.com/earendil-works/pi/pull/8743) | Ignore stale tool image conversions | 🔄 Open | wutongyuonce |

**Highlights:**

- **#6848** — Adds bounded exponential-backoff retries to `completeSummarization()`, preventing a single mid-stream socket drop from killing an entire compaction. Closes #6647.
- **#8674** — Fixes the ragged-thinking-block rendering (#8673) by making `marked` emit spaces for soft `\n` breaks instead of literal newlines.
- **#8764** — Fixes the Windows `!`-command shell-path bug (#8763) by threading `settings.shellPath` through `resolve-config-value.ts`.
- **#8731** — Implements the "disable copy on select" feature (#7720) with a `/settings` toggle and Ctrl+X fallback.
- **#8723** — Direct patch for the HttpsProxyAgent regression (#8610) by adding a bundler plugin that re-exposes the named export.
- **#8766** — Improves developer ergonomics by giving `write`/`edit` tool output a compact, file-focused presentation with line-numbered diffs.

## 5. Feature Request Trends

1. **TUI rendering fidelity** — Multiple recent issues (#8584, #8673, #8780, #8779) target streaming and thinking-block rendering. The community is pushing for cleaner, wider text flow and accurate line wrapping.
2. **Copy-on-select controls** — #7720 and #8731 show strong demand for configurable text selection behavior, especially for terminal-heavy users who already manage their own clipboard.
3. **Provider & proxy robustness** — #8610 (proxy regression), #8774 (OpenAI Responses compaction), and #8779 (DeepSeek reasoning echo) highlight a trend: as more providers are used in production, edge-case API contract mismatches surface. Users want more tolerant request builders.
4. **XDG compliance & config hygiene** — The long-standing #2870 reflects a broader expectation that developer tools respect Linux desktop standards for configuration and state directories.
5. **Session & startup performance** — #8762 (slow session parsing) and #8711 (CPU stall on long streams) signal growing pains as users run longer sessions and accumulate more data.

## 6. Developer Pain Points

- **TUI text corruption under load** — Streaming text fragments, one-word-per-line rendering, and soft-break raggedness recur across issues and models. The rendering pipeline struggles with wide tool output followed by assistant responses.
- **Provider API contract drift** — OpenAI Responses, DeepSeek thinking models, and Bedrock-converse each expose normalization gaps (tool_choice without tools, missing reasoning_content echo, unnormalized usage fields). Maintaining per-provider adapters is increasingly fragile.
- **Proxy and bundling regressions** — The v0.84.3 code-splitting change broke `HttpsProxyAgent`, illustrating how modular bundling can silently drop side-channel dependencies.
- **Terminal emulator compatibility** — Kitty escape-sequence leakage, Windows Wispr Flow paste failures, and macOS Terminal.app crashes indicate that the TUI's terminal integration layer needs more emulator-agnostic input handling.
- **Session resume performance** — Full JSONL parsing on every `--resume` invocation is a bottleneck for power users with large session histories.
- **Null-usage crashes** — Edge-case provider responses (missing usage metadata) cause crashes in `getContextUsage`, pointing to a need for more defensive usage-field handling across the codebase.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026‑08‑28

## 1. Today's Highlights
Qwen Code continues rapid iteration with a nightly release addressing web‑shell session‑diff restoration and DingTalk rich‑text preservation. Community attention remains focused on the long‑planned TUI migration (ink → OpenTUI) and a critical stream‑safety gap in the Anthropic wire. Parallel efforts are hardening CI triage, unblocking git operations in the web‑shell, and expanding hooks‑event integration with backend systems.

## 2. Releases
**v0.22.2‑nightly.20260828.7357136dd1**  
Bug fixes for the web‑shell (restores saved session diffs) and channels (preserves DingTalk rich‑text multi‑line formatting).  
🔗 [Release](https://github.com/QwenLM/qwen‑code/releases/tag/v0.22.2‑nightly.20260828.7357136dd1)

## 3. Hot Issues
| Issue | Summary | Why It Matters | Community Reaction |
|-------|---------|----------------|-------------------|
| [#8662](https://github.com/QwenLM/qwen‑code/issues/8662) | Migrate TUI rendering layer from ink to OpenTUI | The current ink‑based TUI exhibits flicker, rendering artifacts, and structural limits that are hard to fix within ink. A migration to OpenTUI is expected to improve stability and performance. | 11 comments, tracking status; active discussion around roadmap and implementation strategy. |
| [#9005](https://github.com/QwenLM/qwen‑code/issues/9005) | Anthropic wire missing stream‑safety protections | The Anthropic content generator lacks safety guards that the OpenAI wire already implements, posing a potential security/stability risk. Pinned for review at `33c330d`. | 8 comments, status `in‑progress`; contributors are actively examining the gap. |
| [#10227](https://github.com/QwenLM/qwen‑code/issues/10227) | Custom model vendor cannot converse | Users report invalid JSON‑schema errors when configuring third‑party model providers, blocking custom‑vendor workflows. | 7 comments, needs information; community is sharing workarounds and requesting schema validation improvements. |
| [#10210](https://github.com/QwenLM/qwen‑code/issues/10210) | Agent Team `team_delete` can report success after filesystem cleanup fails | Cleanup failures may leave orphaned files while the operation reports success, risking data‑integrity and storage leaks. | 4 comments, open; flagged as a P2 bug with potential impact on multi‑agent deployments. |
| [#10356](https://github.com/QwenLM/qwen‑code/issues/10356) | Main CI failed: E2E Tests | A main‑branch CI run failed before any test results were reported, indicating flaky E2E infrastructure or transient environment issues. | 4 comments, open; automated triage bot tracking the failure. |
| [#10348](https://github.com/QwenLM/qwen‑code/issues/10348) | Hooks trigger‑event enhancement | Request to support agent‑initiated question triggers in hooks, enabling background tasks to push notifications (e.g., Feishu, desktop) when the agent prompts the user. | 4 comments, closed; idea gained traction and was merged or deferred. |
| [#4542](https://github.com/QwenLM/qwen‑code/issues/4542) | Proposal: L2 capability layering for `/acp` | Architecture proposal to isolate file I/O, device‑flow login, agent CRUD, and memory CRUD behind a daemon‑scoped service, paving the way for a fully REST‑equivalent ACP transport. | 4 comments, open; design‑first discussion with references to related PRs (#4472, #3803). |
| [#10322](https://github.com/QwenLM/qwen‑code/issues/10322) | Triage subsumption check breaks silently at contents‑API size ceiling | Stage‑1‑pre triage downloads each production file via the GitHub contents API, which silently caps at ~1 MB, causing false‑positive subsumption results for large files. | 3 comments, open; impact on CI reliability highlighted. |
| [#10369](https://github.com/QwenLM/qwen‑code/issues/10369) | MCP Apps inline UI never renders in web‑shell | The MCP Apps renderer is present but silently falls back; payload delivery and stdio server stale‑ness make debugging difficult. | 3 comments, open; affects developers building MCP‑based UI integrations. |
| [#10391](https://github.com/QwenLM/qwen‑code/issues/10391) | Web‑shell session groups lose assignments after restart | Named session groups remain in the sidebar but appear empty after a `qwen serve` restart, breaking session‑organization workflows. | 2 comments, open; P2 bug impacting web‑shell power users. |

## 4. Key PR Progress
| PR | Summary | Status |
|----|---------|--------|
| [#8902](https://github.com/QwenLM/qwen‑code/pull/8902) | Derives bootstrap `qwen --help` output from shared CLI option definitions, eliminating stale hand‑maintained help text. | Open (autofix/takeover) |
| [#10396](https://github.com/QwenLM/qwen‑code/pull/10396) | Replaces per‑file contents‑API downloads in Stage‑1‑pre triage with a constant‑cost `gh pr diff` comparison, safe for large files. | Open (review/self‑reported) |
| [#9503](https://github.com/QwenLM/qwen‑code/pull/9503) | Folds completed read/search tool batches into the thought line, reducing visual clutter in the TUI. | Open |
| [#9741](https://github.com/QwenLM/qwen‑code/pull/9741) | Ensures screen content filters are applied before the probe tree’s restore step, fixing a regression introduced by #9566. | Open (autofix/takeover) |
| [#10214](https://github.com/QwenLM/qwen‑code/pull/10214) | Recovers protected `.qwen` leftovers (root‑owned, read‑only) in containerized CI jobs when abrupt termination leaves the tree in a locked state. | Open |
| [#10269](https://github.com/QwenLM/qwen‑code/pull/10269) | Adds a dedicated runtime sync path for model‑provider mutations, enabling hot‑reload of providers and models without restarting the daemon. | Open |
| [#9682](https://github.com/QwenLM/qwen‑code/pull/9682) | Deepens architecture ownership boundaries across five high‑churn seams, centralizing ACP transport safety and removing obsolete runtime selection logic. | Open (refactor) |
| [#9740](https://github.com/QwenLM/qwen‑code/pull/9740) | Makes `/review` Step 4 verification execution‑grade by adding a `qwen review ab‑drive` subcommand that runs scripts against paired trees. | Open (autofix/takeover) |
| [#10390](https://github.com/QwenLM/qwen‑code/pull/10390) | Unblocks the workspace “Update Project” action in the web‑shell when the working tree is dirty, presenting a resolution panel instead of a generic error. | Open |
| [#10024](https://github.com/QwenLM/qwen‑code/pull/10024) | Introduces managed public sharing for HTML artifacts in the web‑shell, with a guided flow supporting Cloudflare, Vercel, and Netlify. | Open |

## 5. Feature Request Trends
- **Hooks & Event Integration:** Multiple issues request richer hooks‑event coverage (e.g., #10348, #10388) to allow external systems to react to agent prompts, tool‑approval requests, and turn‑settlement lifecycle events.
- **Native Interactive Cards:** DingTalk channel users want tool‑permission requests presented as native interactive cards (#10388), reducing friction in non‑YOLO modes.
- **Programmatic Tool Calling:** Interest in a Codex‑style `CodeModeOnly` capability (#10377) where the model primarily invokes a restricted JavaScript runtime, enabling loops, concurrency, and filtering within a sandboxed environment.
- **Workflow & Memory Tasks:** Expansion of the daemon’s task contract to expose workflow execution (#9546) and scoped (project/user) managed‑memory tasks (#9895) for better multi‑session coordination.
- **Advisor & Reasoning Controls:** Opt‑in native advisor tool (#9636) and persistent reasoning‑effort selection (#10011) indicate demand for deeper model‑behavior tuning and second‑opinion integrations.
- **Architecture Decoupling:** Ongoing proposals (#4542, #10061) to separate transport from core logic and unify ACP paths, reflecting a trend toward more modular, daemon‑centric designs.

## 6. Developer Pain Points
- **CI Instability & Silent Failures:** Repeated E2E test failures (#10356, #10284, #10289) and triage checks breaking silently at API size ceilings (#10322, #10314) cause delays and require manual investigation.
- **UI State Mismatches:** Web‑shell session groups losing assignments (#10391), MCP inline UI silently failing to render (#10369), and message‑edit index bugs (#10385) lead to confusing user experiences.
- **Tool‑Approval & Channel Configuration:** Channel‑level `approvalMode` not applied to non‑webhook sessions (#10387) and custom‑vendor schema errors (#10227) create configuration pitfalls.
- **FileSystem & Cleanup Reliability:** Agent‑team delete operations reporting success despite cleanup failures (#10210) and protected `.qwen` leftovers breaking CI (#10214) highlight gaps in idempotent resource management.
- **Model‑Provider Hot‑Reload:** Lack of runtime provider reload forces daemon restarts, disrupting long‑running sessions (#10269) and causing session‑persistence issues.
- **TUI Flicker & Rendering Limits:** The current ink‑based TUI’s structural problems (flicker, Virtual Viewport issues) drive demand for the OpenTUI migration (#8662).
- **Security & Safety Gaps:** Missing stream‑safety protections in the Anthropic wire (#9005) compared to the OpenAI wire raise concerns about consistent security boundaries across providers.

---
*Digest generated from GitHub data as of 2026‑08‑28. All links point to the QwenLM/qwen‑code repository.*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-28

## 1. Today's Highlights

The standout theme this cycle is **provider-native web search expansion**, with six PRs landing to add first-party search adapters for DeepSeek, Qwen, Kimi, Z.AI/BigModel, and Xiaomi MiMo — closing a major feature gap against OpenAI/Anthropic/xAI. On the stability front, a **critical runtime lock regression** introduced in the v0.9.12 integration (Issue #5630) was identified, blocking multiple concurrent sessions on a single machine.

---

## 2. Releases

No new releases published in the last 24 hours.

---

## 3. Hot Issues

**[#5316] EPIC-005: CodeWhale TUI Crate Decomposition (Umbrella)** — [Link](https://github.com/Hmbown/CodeWhale/issues/5316)
The architectural backbone of the project's long-term health. This umbrella tracks the full decomposition of the monolithic `codewhale-tui` crate (682k lines, 620 files). Community interest is sustained (18 comments) as every sub-EPIC and FEAT reports completion here.

**[#5620] Context pressure warning is transient and the agent does not proactively react** — [Link](https://github.com/Hmbown/CodeWhale/issues/5620)
A medium-severity bug where the agent silently degrades context without responding to its own pressure warnings. Created just two days ago with 9 comments — strong signal that users are hitting this in production and want the agent to act on it.

**[#5588] Provider neutrality: 18 DeepSeek-exclusive gates that should be provider-neutral** — [Link](https://github.com/Hmbown/CodeWhale/issues/5588)
A comprehensive audit finding 18 hard-coded DeepSeek gates across 2,281 lines. The maintainers have already fixed the most critical (NVIDIA NIM env leak). This is a trust-and-accessibility issue for multi-provider users.

**[#4402] v0.9.2 Attention UX: focus-aware notifications** — [Link](https://github.com/Hmbown/CodeWhale/issues/4402)
A long-running UX enhancement (open since July 16, 2 comments) proposing focus-aware notifications, action-required title states, and return recaps. Still open — reflects an ongoing desire for tighter terminal-native attention management.

**[#5668] v0.9.12: add /copy for the last completed model output** — [Link](https://github.com/Hmbown/CodeWhale/issues/5668)
A practical, high-frequency pain point: no direct command to copy the last assistant response. Users currently resort to manual terminal text selection. Created Aug 27, already generating discussion.

**[#5249] Epic: v0.9.5 build-time lane — stop the monolith tax** — [Link](https://github.com/Hmbown/CodeWhale/issues/5249)
Directly tied to Issue #5316. The 682k-line TUI crate recompiles as one unit on every edit, commit, test, and release. This epic tracks eliminating that cost — a top developer-experience request.

**[#5617] Reduce background git command runs and avoid git probes holding `.git/index.lock`** — [Link](https://github.com/Hmbown/CodeWhale/issues/5617)
A real production bug: internal `git status` probes can lock `.git/index.lock`, causing `git commit` to fail inside working repositories. Two comments; high practical impact for daily users.

**[#5618] Replace internal `git` CLI reads with gix (gitoxide)** — [Link](https://github.com/Hmbown/CodeWhale/issues/5618)
The follow-on to #5617: replace all shell-outs to the real `git` CLI with the Rust-native `gix` library. Cuts process-spawn overhead and eliminates lock contention. Open, 2 comments.

**[#5579] Plugin UX parity with Claude Code** — [Link](https://github.com/Hmbown/CodeWhale/issues/5579)
Users want proactive plugin recommendations, reload discoverability, and hot-reload — feature parity with Claude Code. The codebase already has discovery and marketplace infrastructure; the gap is in UX polish.

**[#5630] Runtime store owner lock blocks multiple sessions** — [Link](https://github.com/Hmbown/CodeWhale/issues/5630) *(CLOSED)*
A hard regression in v0.9.12 where a machine-global single-owner lock makes it impossible to run more than one codewhale session. Closed Aug 27, but signals a release-quality gate that was missed.

---

## 4. Key PR Progress

**[#5683] feat(web): add DeepSeek native search adapter** — [Link](https://github.com/Hmbown/CodeWhale/pull/5683) *(CLOSED)*
Enables provider-native web search for DeepSeek V4 routes via the `web_search` tool contract. Fail-closed for custom endpoints to avoid unexpected behavior.

**[#5682] fix(web): enforce native search constraints before fallback** — [Link](https://github.com/Hmbown/CodeWhale/pull/5682) *(CLOSED)*
Ensures domain constraints are applied inside the backend chain before fallback. Empty native results now explicitly fall through with receipts instead of silently succeeding.

**[#5687] feat(web): add Xiaomi MiMo native search** — [Link](https://github.com/Hmbown/CodeWhale/pull/5687) *(OPEN)*
Adds `web_search` support for MiMo v2.5-pro and v2.5 on official routes. Enforces bounded search, citation verification, and structured annotation metadata.

**[#5686] feat(web): add Moonshot and Kimi native search** — [Link](https://github.com/Hmbown/CodeWhale/pull/5686) *(OPEN)*
Covers K3 Formula tools, legacy K2.6 `$web_search`, and Kimi Code membership `/search`. Bounded to four rounds and eight tool calls; recovers citations only from provider-controlled responses.

**[#5685] feat(web): add Z.AI and BigModel native search** — [Link](https://github.com/Hmbown/CodeWhale/pull/5685) *(OPEN)*
Selective routing: `search-prime` for `api.z.ai`, `search_std` for `open.bigmodel.cn`. Coding Plan and custom-compatible endpoints remain fail-closed.

**[#5684] feat(web): add Qwen native search adapter** — [Link](https://github.com/Hmbown/CodeWhale/pull/5684) *(OPEN)*
Adds `web_search` for `qwen3.8-max`, `qwen3.7-plus`, and `qwen3.7-max` on ModelStudio Token Plan's Responses Harness, using required `tool_choice`.

**[#5679] fix(chat): keep tool result batches contiguous** — [Link](https://github.com/Hmbown/CodeWhale/pull/5679) *(CLOSED)*
Ensures every assistant tool-call batch is followed by one contiguous tool-result run. Defers media until the batch is valid, discards deferred media on interruption, and rejects duplicate tool-call IDs.

**[#5658] feat(tui): surface MCP and plugin boot as a session set** — [Link](https://github.com/Hmbown/CodeWhale/pull/5658) *(CLOSED)*
Fixes the "working · 22s · 0 steps" silence on first turn by surfacing plugin discovery and MCP server boot as visible session state. Sequential `connect_all` previously hid failures behind toast-only notifications.

**[#5677] feat(tui): rescue MCP and plugin session boot** — [Link](https://github.com/Hmbown/CodeWhale/pull/5677) *(CLOSED)*
Cherry-picks PR #5658 onto `main` preserving all commit metadata, authorship, and sign-offs.

**[#5666] chore(tui): gate audited test-only helpers** — [Link](https://github.com/Hmbown/CodeWhale/pull/5666) *(CLOSED)*
Converts 13 audited test-only helper surfaces from `#[allow(dead_code)]` to `#[cfg(test)]` across TUI rendering/text fixtures (whale gallery constants, focus-texture assertions, ASCII render helpers).

---

## 5. Feature Request Trends

- **Provider-native web search** is the dominant feature direction this cycle. Five PRs (5683–5687) plus one design issue (5681) all target closing the gap between DeepSeek/Chinese-provider routes and the existing OpenAI/Anthropic/xAI search backends.
- **Plugin UX maturity** — Issue #5579 signals a clear demand for Claude Code–level plugin discoverability, hot-reload, and proactive recommendations.
- **/copy command for last model output** (Issue #5668) and **focused-block actions** (Issue #5551, closed) show a recurring theme: users want faster, more precise interaction with transcript content without manual selection.
- **MCP boot visibility** — Issues #5658/#5677 and the design for MCP secret scoping (#5637) reflect a push for transparent session initialization and per-runtime secret isolation.
- **Build-time optimization** — The build-time epic (#5249) and crate decomposition (#5316) remain the top long-term infrastructure requests from contributors.

---

## 6. Developer Pain Points

- **Git lock contention in working repositories** (Issues #5617, #5618): Internal `git status` probes spawn process overhead and hold `.git/index.lock`, breaking user commits. The migration to `gix` is the targeted fix.
- **Multi-session incompatibility** (Issue #5630): The v0.9.12 runtime lock regression made it impossible to run multiple codewhale sessions on one machine — a release-quality gap that was caught post-merge.
- **Monolith build tax** (Issue #5249): The 682k-line TUI crate recompiles as a single unit, making every edit, commit, test run, and release slow. The crate decomposition epic (#5316) is the long fix.
- **Context pressure silence** (Issue #5620): The agent emits transient warnings but does not proactively act on context degradation, leaving users to manually manage token budgets.
- **Dead-code accumulation** (Issue #5587): 379 `allow(dead_code)` sites across the TUI crate require ongoing audit and cleanup; Phase 1 landed 8 verified removals with 18 Tier B/C remaining.
- **Provider-neutrality debt** (Issue #5588): 18 hard-coded DeepSeek gates throughout the codebase create maintenance risk and alienate users of equivalent provider-neutral features.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*