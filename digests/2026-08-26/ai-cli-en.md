# AI CLI Tools Community Digest 2026-08-26

> Generated: 2026-08-26 01:44 UTC | Tools covered: 10

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
**Date: 2026-08-26**

---

## 1. Ecosystem Overview

The AI CLI tool ecosystem is entering a phase of intense iteration and fragmentation, with eight of nine tracked tools shipping active releases or PRs in a single day. Vendor-locked architectures are under scrutiny — multiple communities are pushing for provider neutrality, multi-model support, and transparent cost tracking. Reliability concerns around session lifecycle, sub-agent orchestration, and platform-specific regressions (particularly Windows MSIX and Linux ARM64) dominate community frustration. The tools are diverging in positioning: Claude Code and Codex target enterprise productivity, while OpenCode and DeepSeek TUI lean into modularity and extensibility.

---

## 2. Activity Comparison

| Tool | Hot Issues | Open PRs | Releases | Release Cadence |
|------|-----------|----------|----------|----------------|
| **Claude Code** | 10 | 1 | 2 (v2.1.245, v2.1.246) | Daily hotfixes |
| **OpenAI Codex** | 10 | 10 | 1 (rust alpha x3) | Rapid pre-release |
| **Gemini CLI** | 10 | 10 | 3 (nightly + preview + stable) | Multi-channel |
| **GitHub Copilot CLI** | 10 | 1 | 2 (v1.0.81-10/11) | Frequent prerelease |
| **Kimi Code CLI** | 2 | 0 | 0 | Stalled |
| **OpenCode** | 10 | 9 | 1 (v1.18.23) | Weekly-ish |
| **Pi** | 10 | 10 | 0 | Moderate |
| **Qwen Code** | 10 | 10 | 0 | Moderate |
| **DeepSeek TUI** | 10 | ~5 (1 WIP) | 0 | Integration-cycle |

**Key observation:** DeepSeek TUI and Kimi Code show the lowest activity. Kimi Code has only 2 hot issues and zero PRs — a possible signal of lower community velocity or slower triage. DeepSeek is in a major integration push (v0.9.12, 72 commits) but gated on release checks.

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Multi-provider / vendor neutrality** | Gemini CLI, Qwen Code, DeepSeek TUI, OpenCode | Remove DeepSeek-exclusive hardlocks; support OpenAI-compatible endpoints; fix reasoning-effort clamping across providers |
| **Context & session management** | Claude Code, Gemini CLI, OpenCode, Qwen Code, Pi | Compaction reliability; persistent task tracking; sub-agent lifecycle; session recovery across reboots |
| **Cost / usage transparency** | OpenCode, DeepSeek TUI, Qwen Code | Model pricing in picker; tool and MCP schema cost display; token usage breakdowns |
| **Windows platform parity** | Claude Code, Codex, Qwen Code, DeepSeek TUI, Pi | MSIX/AppX reliability; paste/clipboard fixes; path handling; process leak prevention |
| **MCP interoperability** | Claude Code, Codex, Gemini CLI, Copilot CLI | OAuth fixes; draft-07 schema support; enterprise IdP integration; workspace-level config attachment |
| **Sub-agent reliability** | Gemini CLI, OpenCode, DeepSeek TUI | Turn-limit misreporting; hang recovery; config override respect; Wayland support |
| **Plugin / extension ecosystem** | OpenCode, Copilot CLI, Pi | Git-based plugin install; explicit update controls; version visibility; lifecycle robustness |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Qwen Code | DeepSeek TUI | OpenCode | Pi | Copilot CLI | Kimi Code |
|-----------|------------|-------------|------------|-----------|-------------|----------|-----|-------------|-----------|
| **Primary focus** | Enterprise agents | Desktop + CLI parity | Multi-agent reliability | Open-source modularity | Provider-neutral TUI | Plugin extensibility | Local/self-hosted | GitHub-integrated workflows | Emerging |
| **Target user** | Corporate/enterprise | General developers | Researchers & power users | OSS contributors | Multi-provider users | Self-hosted / cost-conscious | Local model users | GitHub Enterprise | macOS/Windows |
| **Technical approach** | Rule-based permissions, auto-mode classifier | Electron + Rust SDK; Codex thread affinity | Sub-agent orchestration, AST-aware reads | Transparent context lifecycle, DAP support | Control sockets, lifecycle outbox, supervised ops | Effect runtime, tool-call reliability | Eager tool execution, compaction tuning | Microsoft ecosystem integration | Minimal activity |
| **Release model** | Patch-heavy, security-focused | Alpha cadence toward v0.150 | Nightly + preview + stable | Architecture review in progress | Crate decomposition (EPIC-005) | Provider-driven fixes | Provider compatibility patches | GitHub-prerelease channel | Stable but quiet |

**Notable divergence:** DeepSeek TUI is the only tool explicitly building for *supervised/automated operation* (control sockets, lifecycle outbox, `/relaunch`), targeting CI and unattended workflows. Qwen Code is the only tool conducting a formal *architecture review* of its core type system. OpenCode is uniquely focused on *provider-agnostic tool-call reliability* across third-party endpoints.

---

## 5. Community Momentum & Maturity

| Tier | Tools | Rationale |
|------|-------|-----------|
| **High momentum** | Gemini CLI, Qwen Code, DeepSeek TUI | 10 PRs each; Gemini shipping 3 releases; DeepSeek in a 72-commit integration; Qwen conducting structural refactors |
| **Moderate momentum** | OpenCode, Pi, Claude Code | Active PRs and releases but fewer feature directions; Claude Code driven more by issue triage than community contributions |
| **Low momentum** | OpenAI Codex, Copilot CLI | High issue volume but PRs are mostly internal/closed; community contribution is limited |
| **Low activity** | Kimi Code | 2 issues, 0 PRs, 0 releases in 24h; critical silent-failure bug (#2617) unresolved — potential signal of under-resourcing |

**Maturity signal:** Claude Code and Copilot CLI show enterprise-grade issue tracking (CVP blocks, policy opacity) but low community PR velocity — typical of closed-roadmap products. OpenCode and DeepSeek TUI show healthier open-source contribution patterns with visible feature-driven PRs.

---

## 6. Trend Signals

| Trend | Evidence | Developer Implication |
|-------|----------|----------------------|
| **Windows is the weakest platform** | 7+ distinct Windows issues in Claude Code; Codex v26.820 regression cluster; Qwen Ctrl+V broken since 0.21.x; DeepSeek verbatim-path failures | Prioritize Linux/macOS for production workflows; Linux ARM64 also shows severe instability (Claude Code Bun crashes) |
| **Context compaction is an unsolved problem** | Pi compaction reserve bug (#8651), OpenCode session stuck after reboot (#43277), Qwen Skill Context Lifecycle (#6762), DeepSeek structured survival contract (#4394) | Expect context-management bugs in long-running sessions; favor tools with explicit compaction contracts |
| **Provider compatibility is the #1 integration friction point** | Qwen reasoning-effort clamping (#9459), OpenCode tool-call failures on Ox/Zen (#44300, #33618), Gemini OAuth SSRF fix (#29081), DeepSeek 18-gate audit (#5588) | Multi-provider deployments require careful endpoint testing; expect silent failures with non-native providers |
| **Sub-agent orchestration is outpacing stability** | Gemini subagent hangs (#21409), misreported success (#22323); OpenCode multi-question tool-call regression (#35434) | Disable or tightly constrain sub-agents in production until tool reliability improves |
| **Cost transparency is becoming table stakes** | OpenCode model pricing request (#14524, 11 👍); DeepSeek schema cost display (#5611); Qwen token usage panel (#9988) | Tools without cost visibility will face community pressure; budget-aware workflows need explicit tooling |
| **Enterprise policy opacity erodes trust** | Claude Code CVP re-blocks (#84352, 156 comments); Copilot model grey-out (#4272); both flagged as critical friction | Enterprise deployments need clearer policy surfacing; expect community backlash on opaque blocks |
| **MCP is maturing but fragmented** | Draft-07 rejection (Claude Code #86142), OAuth SSRF (Gemini #29081), workspace config gaps (Copilot #4542), enterprise IdP integration (Codex #40739) | MCP interoperability remains unreliable across tools; validate server schemas before production adoption |

---

**Bottom line for developers:** The ecosystem is technically vibrant but platform and reliability uneven. For production use, **Linux/macOS** is significantly more stable than Windows. For multi-provider workflows, **OpenCode** and **Gemini CLI** show the most active compatibility work. For long-running sessions, **DeepSeek TUI** and **Qwen Code** are investing in context management, but all tools carry compaction risk. **Kimi Code** warrants close observation — a silent `Write` no-op (#2617) with no active PRs is a red flag for reliability-sensitive workflows.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
*Data as of 2026-08-26 · Source: [anthropics/skills](https://github.com/anthropics/skills)*

---

## 1. Top Skills Ranking

| # | Skill / PR | Functionality | Discussion Highlights | Status |
|---|---|---|---|---|
| 1 | [PR #1298](https://github.com/anthropics/skills/pull/1298) · `skill-creator` eval fix | Fixes `run_eval.py` reporting 0% recall on every description, rendering the optimization loop useless; also patches Windows stream reading, trigger detection, and parallel workers | 10+ independent reproductions of the bug; critical path for the skill-creator workflow | 🟡 Open |
| 2 | [PR #514](https://github.com/anthropics/skills/pull/514) · `document-typography` | Enforces typographic quality in AI-generated documents — prevents orphan lines, widow paragraphs, and numbering misalignment | Addresses a widespread but often-unnoticed quality issue; no merged alternative yet | 🟡 Open |
| 3 | [PR #1628](https://github.com/anthropics/skills/pull/1628) · `hivemind` | Multi-agent orchestration skill: delegates mechanical work to headless OpenCode workers on free models while Claude Code retains planning/review/merge control | Novel cost-optimization architecture; taps into the growing "agent swarm" pattern | 🟡 Open |
| 4 | [PR #538](https://github.com/anthropics/skills/pull/538) · `pdf` case-sensitivity fix | Fixes 8 case-sensitive reference mismatches (`REFERENCE.md`, `forms.md`) in `SKILL.md` that break skills on Linux/macOS | Single-author fix with clear reproducibility; no competing PRs | 🟡 Open |
| 5 | [PR #83](https://github.com/anthropics/skills/pull/83) · `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills evaluating skills across five dimensions: structure, documentation, examples, quality scoring, and security review | Ambitious scope; positions itself as a governance layer for the skills ecosystem | 🟡 Open |
| 6 | [PR #541](https://github.com/anthropics/skills/pull/541) · `docx` tracked-change fix | Fixes document corruption when the DOCX skill adds tracked changes to files with existing bookmarks (OOXML `w:id` collision) | Directly addresses a data-loss bug; second fix from same author as PR #538 | 🟡 Open |
| 7 | [PR #723](https://github.com/anthropics/skills/pull/723) · `testing-patterns` | Comprehensive testing skill covering testing philosophy, unit testing (AAA, naming, edge cases), and React component testing with Testing Library | Targets the largest category of developer workflow needs | 🟡 Open |
| 8 | [PR #568](https://github.com/anthropics/skills/pull/568) · `servicenow` | Broad ServiceNow platform skill spanning ITSM, ITOM, ITAM/SAM, FSM, HRSD, CSM, SPM/PPM, SecOps, and IntegrationHub | Enterprise-specific; single broadest-scope platform skill submitted | 🟡 Open |

---

## 2. Community Demand Trends

Analysis of top community Issues reveals five concentrated demand vectors:

| Demand Vector | Key Issues | Summary |
|---|---|---|
| **Trust & Security Governance** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments), [#1175](https://github.com/anthropics/skills/issues/1175), [#412](https://github.com/anthropics/skills/issues/412) | Namespace impersonation, permission scoping, and governance patterns are the most-discussed concerns. Users want built-in safety gates for agent-authored output. |
| **Evaluation & Quality Tooling** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍), [#1385](https://github.com/anthropics/skills/issues/1385), [#1390](https://github.com/anthropics/skills/issues/1390) | The `run_eval.py` trigger bug is a top-priority fix. Parallel demand exists for reasoning-quality gates and honest MCP evaluation harnesses. |
| **Enterprise Platform Skills** | [#228](https://github.com/anthropics/skills/issues/228) (8 👍), [#568](https://github.com/anthropics/skills/pull/568), [#1487](https://github.com/anthropics/skills/issues/1487) | Organizations need org-wide skill sharing, platform-specific skills (ServiceNow, HPC), and context-window-safe API skills. |
| **Cross-Platform Reliability** | [#1099](https://github.com/anthropics/skills/issues/1099), [#1050](https://github.com/anthropics/skills/issues/1050) | Windows subprocess and encoding bugs in `skill-creator` are recurring pain points blocking adoption. |
| **Testing & Code Review** | [#723](https://github.com/anthropics/skills/pull/723), [#202](https://github.com/anthropics/skills/issues/202) | Demand for structured testing-pattern guidance and an improved, action-oriented skill-creator. |

---

## 3. High-Potential Pending Skills

These PRs show active community engagement, clear problem-solution framing, and alignment with top demand signals — strong candidates for near-term merge:

| PR | Skill | Why It's Promising |
|---|---|---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill-creator` eval fix | Blocks the entire skill-improvement loop; multiple authors (MartinCajiao, joshuawowk, gstreet-ops) have patched overlapping bugs — convergence suggests a fix is imminent |
| [#1628](https://github.com/anthropics/skills/pull/1628) | `hivemind` | Directly addresses the #1 community cost concern (expensive model context as scarce resource); novel architecture with clear value prop |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` / `skill-security-analyzer` | Answers the security governance demand from Issue #492; positions as ecosystem infrastructure |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Only broad enterprise platform skill in the repo; long lead time (open since Mar 2026) with recent activity suggests final review |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Testing is the highest-volume developer workflow; comprehensive scope matches Issue #202's call for best-practice skill-creator guidance |
| [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` | Solves a universal pain point for document output; no competing PRs, clean scope |

---

## 4. Skills Ecosystem Insight

> The community's most concentrated demand is **trustworthy evaluation and governance tooling** — not more endpoint skills, but the meta-infrastructure (honest evaluation harnesses, security auditors, namespace integrity) that lets the ecosystem scale safely.

---



# Claude Code Community Digest — 2026-08-26

---

## 1. Today's Highlights

Claude Code v2.1.246 lands with a critical Bash allow-rule warning and a new Auto mode tab in `/permissions`, while v2.1.245 patches a startup crash on glibc 2.44 distros. Community attention remains dominated by cyber-safeguard blocks affecting CVP-approved organizations (156 comments), persistent Windows desktop reliability issues, and a surge of Linux ARM64 crash reports.

---

## 2. Releases

### v2.1.246
- **Bash wildcard warning:** Added a startup warning for allow rules using wildcards before the subcommand (e.g. `Bash(git * main)`), since they also match options inserted before the subcommand.
- **Auto mode tab:** New `/permissions` tab for viewing and editing auto mode classifier rules.

### v2.1.245
- **glibc 2.44 crash fix:** Resolved a startup crash on Linux distributions shipping glibc 2.44 (Arch Linux, CachyOS, Fedora Rawhide).

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#84352](https://github.com/anthropics/claude-code/issues/84352) | CVP-approved org still blocked by cyber safeguards | 156 | 24 | Organizations with prior Cyber Verification Program approval are being re-blocked in Claude Code despite "Under review" status in the portal. Affects enterprise trust. |
| [#80444](https://github.com/anthropics/claude-code/issues/80444) | Windows desktop: fatal GPU-process crash via browser tab | 56 | 9 | GPU crash (0x060C201E) renders the MSIX package unlaunchable until manual repair. Reproduces across two driver versions on RTX 2080. |
| [#85891](https://github.com/anthropics/claude-code/issues/85891) | Windows desktop always-on-top with no toggle | 25 | 37 | Highest-engagement desktop UX complaint of the period; no in-app setting exists to disable the topmost behavior. Windows counterpart to #66516. |
| [#82056](https://github.com/anthropics/claude-code/issues/82056) | Auto-memory index load status opaque to sessions | 34 | 1 | Sessions cannot determine whether auto-memory loaded fully, was truncated, or failed entirely — a critical gap for teams relying on persistent context. |
| [#86142](https://github.com/anthropics/claude-code/issues/86142) | MCP draft-07 outputSchema rejected client-side | 29 | 12 | **CLOSED.** MCP servers declaring draft-07 schemas are blocked before dispatch with "unsupported dialect." Blocks a large class of existing MCP tooling. |
| [#82049](https://github.com/anthropics/claude-code/issues/82049) | Sign-in magic link emails delayed 2–5 minutes | 14 | 25 | Progressive email delay since mid-July 2026. Directly impacts session recovery and developer productivity; 25 upvotes signal widespread frustration. |
| [#89370](https://github.com/anthropics/claude-code/issues/89370) | `claude` and `install.sh` both segfault on Linux | 9 | 10 | Segfault across both binary and installer paths suggests a systemic compatibility issue on certain Linux configurations. |
| [#78027](https://github.com/anthropics/claude-code/issues/78027) | Injected grep wrapper consumes 20+ GB RAM on bounded-repeat regex | 2 | 0 | The bundled `ugrep` wrapper can hard-freeze machines under common regex patterns — a serious stability risk for large codebases. |
| [#89539](https://github.com/anthropics/claude-code/issues/89539) | Linux ARM64 SIGABRT/SIGSEGV crashes (2.1.231–2.1.243) | 1 | 0 | Recurring Bun-runtime crashes on glibc 2.34 ARM64, clustered across multiple versions. Corrupted stack frames suggest memory corruption. |
| [#89680](https://github.com/anthropics/claude-code/issues/89680) | Stealth update leaves orphaned processes; new version unlaunchable | 0 | 0 | Auto-update via Windows AppX leaves old-container locks; requires full reboot to recover. Part of a broader Windows MSIX reliability pattern. |

---

## 4. Key PR Progress

| # | Title | Author | Summary |
|---|-------|--------|---------|
| [#89404](https://github.com/anthropics/claude-code/pull/89404) | `validate-agent.sh`: don't abort at first warning | bcherny | Fixes false positives from `set -euo pipefail` — `((warning_count++))` arithmetic now handles zero-valued counters without triggering abort. Resolves #83803. |

> *Only 1 PR updated in the last 24h; the community is driving more issue reporting than contribution activity this period.*

---

## 5. Feature Request Trends

- **Prompt-topic triggers for `.claude/rules/`** (#87804) — Users want conditional rule loading based on subject/topic, not just file paths. Current `paths:` covers files only; no equivalent exists for semantic triggers.
- **Auto-memory visibility** (#82056) — In-session transparency into whether the memory index loaded whole, truncated, or failed — essential for debugging and reliability.
- **Bash rule precision** (v2.1.246 response) — The new wildcard warning and `/permissions` Auto mode tab indicate Anthropic is addressing community requests for finer-grained permission controls.
- **Cross-session peer discovery** (#89658) — Windows MSIX sessions cannot discover desktop app pipes because `\\.\pipe\LOCAL\` is not scanned, suggesting a need for unified inter-process communication across install contexts.

---

## 6. Developer Pain Points

| Theme | Issues |
|-------|--------|
| **Windows desktop reliability** | #80444 (GPU crash), #85891 (always-on-top), #85901 (missing CodeIntegrity.cat), #73694 (AppX lock), #82277 (servicing kills agents), #89658 (pipe discovery), #89680 (orphaned update) — **7 distinct issues** in one cycle. |
| **Linux compatibility** | #89370 (segfault), #89539 (ARM64 Bun crashes), #77753 (WSL install), #78027 (grep memory blowup), #84352 (CVP blocks on Linux orgs) |
| **Sign-in / auth friction** | #82049 (email delays), #84352 (cyber-safeguard blocks) |
| **MCP server interoperability** | #86142 (draft-07 rejected), #67432 (spawn_task missing external MCPs) |
| **macOS permission churn** | #83841 (re-prompts per session, cannot clear) |
| **Model behavior drift** | #89579 (scope overrun), #89244 (rule binding inconsistency), #89464 (CLAUDE.md prohibitions ignored incrementally) |

**Most acute:** Windows MSIX packaging and update reliability is the dominant pain vector this period, with at least 5 issues stemming from the same underlying AppX/container model. Linux ARM64/glibc instability is a close second given the crash severity.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-26

## 1. Today's Highlights

Three Rust SDK alpha releases (v0.150.0-alpha.9/10/11) shipped in the last 24 hours, signaling an active pre-v0.150 release cadence. The Windows Desktop app experienced a rough rollout with v26.820 — multiple users report startup failures, MCP transport errors, and process leaks — while the community simultaneously pushes hard for a permanent removal of the 5-hour usage cap (#34035, 140 👍).

## 2. Releases

- **rust-v0.150.0-alpha.9** → **rust-v0.150.0-alpha.11** — Three consecutive alpha releases in one day; each incrementally progresses toward the v0.150 milestone. No changelog summary provided.

## 3. Hot Issues

1. **#13993 — Support standalone Windows installer** [81 comments, 187 👍]
   The single most-upvoted open issue. Windows users blocked by Store restrictions, corporate policies, and offline environments need a traditional `.exe` installer.

2. **#34035 — Make the 5-hour usage limit removal permanent** [14 comments, 140 👍]
   After OpenAI temporarily lifted the cap on July 12, users want it made permanent across Plus/Pro/Business tiers while retaining the weekly allowance. Directly impacts daily workflow.

3. **#39162 — macOS auth invalidation on conversation open** [57 comments, 32 👍]
   Opening an existing ChatGPT-authed conversation on macOS 26.814 forces a re-sign-in. A regression from 26.810 that blocks long-session users.

4. **#28919 — Missing "Control Other Devices" tab on Windows** [44 comments, 42 👍]
   Pro users on Windows cannot access device-connection settings; the tab is absent despite existing in earlier builds.

5. **#33776 — Hundreds of `taskkill.exe`/`conhost.exe` processes spawned** [34 comments, 27 👍]
   Windows Desktop 26.707 leaks child processes, triggering WMI storms and DWM degradation. A serious resource-leak regression.

6. **#40715 — MCP transport failure in 26.820 (Windows)** [23 comments, 16 👍]
   Stable build 26.820.60940 fails with "invalid transport in mcp_servers.codex_app"; the prior Beta 26.727 works. A clear regression.

7. **#25179 — Stale subagents accumulate and cannot be closed** [21 comments, 3 👍]
   Long-running Desktop sessions leave orphaned subagents visible in UI and cache; stop/close actions return "thread not found."

8. **#20930 — Remote notifications don't fire** [14 comments, 18 👍] · **CLOSED**
   When using Codex App with a remote Linux host, turn-complete notifications are silently dropped on the macOS desktop.

9. **#34026 — Completed threads remain "thinking" on Windows** [14 comments]
   Windows Desktop 26.715 queues new messages locally and refuses to start a turn after a thread completes — users are effectively stuck.

10. **#39144 — GPT-5.6 Sol receives only 272K context vs. 872K for Terra/Luna** [13 comments, 6 👍]
    After the long-context rollout, Sol is still capped at 272K while Terra and Luna got 872K. A parity and rollout-completeness concern.

## 4. Key PR Progress

1. **#40751 — Preserve transcript overlay state across updates** (CLOSED)
   Detaches and restores the live-tail overlay when transcript renderables are rebuilt after history operations.

2. **#40748 — Fix MCP denial assertion for structured output** (CLOSED)
   Updates permission tests to read denial messages from structured-output text content items instead of raw strings.

3. **#40742 — Prepare isolated Guardian reviewer sessions** (CLOSED)
   Adds a policy prompt and output contract for synchronous Guardian reviews, with fallback to the parent model.

4. **#40739 — Enterprise IdP identity resolution for MCP OAuth** (CLOSED)
   Resolves stored enterprise sessions against discovered OIDC metadata; requires issuer, public-client auth, and ID-JAG token exchange support.

5. **#28798 — Plugin install entry metadata in TUI** (CLOSED)
   Parses nested `entries`/`categories` metadata so desktop clients can render per-candidate Install buttons.

6. **#40737 — Preserve MCP tool output as content items** (CLOSED)
   Converts unstructured MCP results into typed function-call output items instead of raw text serialization.

7. **#40728 — Honor attachment-owned permissions for MCP servers** (CLOSED)
   MCP servers attached to executor environments now retain their owner's permission profile rather than inheriting thread-wide sandbox authority.

8. **#40724 — Plugin-attributed skill telemetry** (CLOSED)
   Adds `plugin_id`, `model_slug`, and `reasoning_effort` dimensions to `codex.skill.injected` metrics.

9. **#40722 — Enterprise ID-JAG exchange for MCP OAuth** (CLOSED)
   Adds a non-interactive two-step exchange: obtains an ID-JAG from an enterprise IdP and trades it for a resource-bound MCP bearer token.

10. **#40720 — Preserve composer hyperlinks across wrapped lines** (CLOSED)
    Detects visible HTTP(S) URLs and attaches complete OSC 8 destinations to every wrapped fragment, including scrolled-off-screen portions.

## 5. Feature Request Trends

- **Standalone Windows distribution** (#13993) — the #1 most-requested feature; users want a non-Store installer for enterprise and offline scenarios.
- **Permanent removal of the 5-hour usage cap** (#34035) — strong community appetite to replace temporary policy with a lasting change.
- **Configurable tool-call visibility** (#39819) · **CLOSED** — demand for a `config.toml` toggle to restore pre-collapsed tool-call display.
- **Auto-accept "Keep Waiting"** (#32139) — users want the manual approval step removed for extended-wait confirmations.
- **Trusted hook installation for IDE wrappers** (#21615) — a supported mechanism for local IDEs to request trust for installed hooks without manual intervention.

## 6. Developer Pain Points

- **Windows v26.820 regression cluster** — Multiple users report that the latest Desktop build breaks startup entirely (#40700, #40752), fails MCP transport (#40715), leaks `node_repl` processes per thread (#35485), and crashes on startup in `chrome.dll` (#39443). The MSIX EFS-encrypted bundled codex also fails relocation on encrypted drives (#38696). This is the dominant frustration theme.
- **Auth/session bugs on macOS** (#39162) — unexpected sign-out loops when reopening conversations.
- **Process/resource leaks on Windows** (#33776, #35485) — `taskkill.exe`/`conhost.exe` storms and MCP child-process leaks degrade system performance.
- **Stale subagent state** (#25179, #37041) — orphaned or rehydrated subagents that cannot be closed, cluttering the UI and session state.
- **CLI binary resolution** (#22423) — Electron app cannot locate the bundled `codex` CLI, especially with WSL configurations.
- **Rate-limit confusion** (#40741, #31818) · **CLOSED** — users report the 5-hour cap consumes roughly half the weekly allowance, creating opaque and frustrating quota behavior.
- **Missing UI elements** (#28919, #30385) — settings tabs and sidebar threads disappearing after updates, suggesting regressions in Windows Desktop rendering/data paths.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-26

## 1. Today's Highlights

The v0.59.0 nightly continues to roll out alongside fixes for MCP OAuth SSRF vulnerabilities and extension install race conditions. The community is heavily focused on agent reliability, with multiple P1 issues around subagent hangs and recovery circling back this week.

---

## 2. Releases

**v0.59.0-nightly.20260826.g64b5b79a6** — Latest nightly build.

**v0.58.0-preview.0** — Preview release including a symlink evaluation fix in ignore path handling (`#28915`).

**v0.57.0** — Changelog PR `#29084` merged. Key fixes: dynamic Cloud Workstations proxy redirect URI for OAuth flows (`#28688`) and resolution of swallowed directory mismatch errors in IDE connections (`#28688`).

---

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Critical P1: subagents silently claim success after hitting turn limits, corrupting investigation flows | 13 comments, 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs indefinitely | P1: simple operations like folder creation hang for hours when deferring to the generalist agent; community workaround is disabling sub-agents entirely | 8 comments, 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing & Post-Execution Intent Routing | P2 vision: leverage Gemini's native bash affinity while maintaining security — signals strong community interest in safer, more capable shell execution | 8 comments, 1 👍 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and mapping | P2 epic: could drastically reduce token waste from misaligned file reads; tracks investigation into `tilth`/`glyph` as AST tooling backends | 7 comments, 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | P2: users report sub-agents are ignored unless explicitly prompted, undermining the multi-agent design | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | P2: sessions that look uninteresting to the extraction agent are never marked processed, causing repetitive surfacing | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | P2 security: secrets may reach model context before redaction occurs; calls for pre-transmission sanitization | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell commands stuck at "Waiting input" after completion | P1 core bug: simple CLI commands appear to hang, blocking the agent loop | 4 comments, 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | P1: browser agent terminates with GOAL on Wayland sessions, blocking Linux desktop users | 4 comments, 1 👍 |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores `settings.json` overrides | P2: `maxTurns` and other config overrides are silently ignored, making it impossible to control browser agent behavior | 3 comments |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#29081](https://github.com/google-gemini/gemini-cli/pull/29081) | Prevent SSRF in MCP OAuth metadata discovery | Open | Enforces HTTPS for remote OAuth endpoints and validates origin matching per RFC 9728 / RFC 8414 |
| [#29089](https://github.com/google-gemini/gemini-cli/pull/29089) | Forward abortSignal to retryWithBackoff in BaseLlmClient | Open | Fixes abort propagation through retry logic used by session summary, chat compression, and the classifier |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Consent prompts for extension env changes | Open | Prevents extensions from injecting unauthorized env vars into MCP server processes; sanitizes runtime-altering variables |
| [#29088](https://github.com/google-gemini/gemini-cli/pull/29088) | Resolve `stop()` hang with open MCP stream | Open | Fixes VS Code extension deactivation blocking when MCP streaming connections are active |
| [#29087](https://github.com/google-gemini/gemini-cli/pull/29087) | Prevent concurrent extension install races | Open | Uses `proper-lockfile` to serialize extension installs across simultaneous Gemini CLI processes |
| [#28983](https://github.com/google-gemini/gemini-cli/pull/28983) | Detect mixed line endings properly | Open | Fixes naive CRLF detection that flagged files with even a single `\r\n` as CRLF |
| [#28930](https://github.com/google-gemini/gemini-cli/pull/28930) | Drop unsafe `diff.external` override | Open, Merged | Reverts a git env override that broke external diff tools inside the shell sandbox |
| [#28789](https://github.com/google-gemini/gemini-cli/pull/28789) | Fix `stop()` hang & keep-alive leak in VS Code companion | Closed | Resolves indefinite hang on active MCP streams and intermittent ping failure resource leak |
| [#28699](https://github.com/google-gemini/gemini-cli/pull/28699) | Enforce auth & stop checkpoint path traversal in A2A server | Closed | Secures A2A REST routes that were previously accepting unauthenticated requests |
| [#28701](https://github.com/google-gemini/gemini-cli/pull/28701) | Fix TRUST_PARENT rule precedence | Closed | Corrects folder-trust resolution to honor the most specific matching rule |

---

## 5. Feature Request Trends

- **Surgical context reads** — AST-aware file mapping (`#22745`, `#22746`) and "tactful extraction" (`#19561`) to replace firehose-style reads that bloat context by 15k+ tokens/turn.
- **Sub-agent reliability & visibility** — Better sub-agent discovery (`#21968`), shareable trajectories via `/chat share` (`#22598`), and inclusion of sub-agent context in bug reports (`#21763`).
- **Persistent task tracking** — Replace in-context `WriteToDo` with file-based CRUD tracking (`#18836`) to survive context rot and session boundaries.
- **Native bash affinity with sandboxing** — Zero-dependency OS sandboxing that lets Gemini chain POSIX tools safely (`#19873`), paired with destructive-behavior discouragement (`#22672`).
- **Browser agent resilience** — Auto session takeover, lock recovery (`#22232`), and Wayland support (`#21983`).

---

## 6. Developer Pain Points

1. **Agents hanging indefinitely** — The generalist agent (`#21409`) and shell commands (`#25166`) repeatedly get stuck, requiring manual cancellation. This is the most upvoted frustration (8 👍 on `#21409`, 3 👍 on `#25166`).
2. **Sub-agent reliability** — Subagents misreport success after hitting turn limits (`#22323`), ignore config overrides (`#22267`), and fail on Wayland (`#21983`). The multi-agent architecture is outpacing its stability.
3. **Auto Memory looping** — Low-signal sessions are retried indefinitely (`#26522`) and invalid inbox patches are silently dropped (`#26523`), eroding trust in the memory system.
4. **Symlink handling** — Agent symlinks in `~/.gemini/agents/` are not recognized (`#20079`), and symlink evaluation in ignore paths was only recently fixed in `v0.58.0-preview.0`.
5. **Workspace pollution** — The model creates temp scripts in random directories (`#23571`), forcing users to clean up before commits.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-26

## 1. Today's Highlights

GitHub shipped **v1.0.81-11** (and v1.0.81-10), bringing a fix for enterprise-blocked MCP servers incorrectly showing as "pending," opening the plugins dashboard to all users, and standardizing `x` as the delete key across the CLI. The community is actively debating vi/vim input mode support (74 👍) and reporting new prerelease regressions around MCP auth token injection and session state handling.

---

## 2. Releases

### v1.0.81-11 — [PR #4607](https://github.com/github/copilot-cli/pull/4607)
- **Fixed:** MCP servers blocked by enterprise policy now display as `blocked` in `/mcp` instead of remaining stuck in a `pending` spinner indefinitely.

### v1.0.81-10
- **New:** Plugins dashboard is now universally available — run `/plugin`, `/mcp`, or `/skills` to access it. Set `PLUGINS_DASHBOARD=false` to opt out.
- **Improved:** `x` is now the delete key consistently across `/sandbox config`, `/settings`, `/mcp`, the sessions dialog, and diff views.

---

## 3. Hot Issues

| # | Title | 👍 | Comments | Why It Matters |
|---|-------|----|----------|----------------|
| [#13](https://github.com/github/copilot-cli/issues/13) | CLI input should have a vi/vim input mode | 74 | 8 | The highest-engagement open issue. Modal-editor users represent a significant developer segment; lack of vim bindings is a frequent friction point. |
| [#4535](https://github.com/github/copilot-cli/issues/4535) | `store_memory` fails in v1.0.81 prereleases: `Instance id is required` | 0 | 6 | Blocks memory-persisting agents on the latest prerelease channel; regression from a working state. |
| [#3709](https://github.com/github/copilot-cli/issues/3709) | Allow `/model` to switch between models including BYOK/local providers | 28 | 6 | BYOK users cannot currently swap to local models mid-session, limiting flexibility for on-prem/air-gapped workflows. |
| [#4035](https://github.com/github/copilot-cli/issues/4035) | Voice installer fails on private Azure Artifacts feed (401) | 0 | 4 | Voice mode installation is broken for users without Azure DevOps access, despite the package being public on NuGet. |
| [#4542](https://github.com/github/copilot-cli/issues/4542) | Workspace `.mcp.json` detected but not connected in agent sessions | 1 | 2 | MCP servers configured at the workspace level are listed as enabled but never actually attach during interactive sessions — a functional gap. |
| [#3380](https://github.com/github/copilot-cli/issues/3380) | Add `--disable-repo-mcps` flag to skip `.mcp.json` loading | 0 | 2 | No clean way to run `copilot` while ignoring repo-level MCP definitions; current workaround requires per-server disabling. |
| [#4272](https://github.com/github/copilot-cli/issues/4272) | New models greyed out with org policy message | 3 | 1 | Users report models being silently disabled with no discoverable admin settings to re-enable them — poor transparency. |
| [#4560](https://github.com/github/copilot-cli/issues/4560) | Model `auto` always runs with reasoning effort disabled | 0 | 1 | The auto router strips `reasoningEffort` entirely, making it impossible to control reasoning depth when using model auto-selection. |
| [#4590](https://github.com/github/copilot-cli/issues/4590) | Extension SDK reconnect disposes session hook processor | 0 | 1 | Multiple active extensions cause hook-processor teardown on MCP host reload, breaking session continuity. |
| [#4593](https://github.com/github/copilot-cli/issues/4593) | Archiving a worktree session fails on Windows (os error 32) | 0 | 1 | Windows file-locking behavior prevents worktree session archival — the session process tree isn't terminated before deletion. |

---

## 4. Key PR Progress

| # | Title | Status | Notes |
|---|-------|--------|-------|
| [#4607](https://github.com/github/copilot-cli/pull/4607) | Prepare public prerelease v1.0.81-11 | ✅ Closed | Advance commit timestamp before publishing; includes the enterprise MCP policy fix. |

*No other pull requests were open or updated in the last 24 hours.*

---

## 5. Feature Request Trends

- **Editor ergonomics:** vi/vim keybindings (#13) remain the top community request by far, signaling strong demand for power-user input modes.
- **Model & BYOK flexibility:** Users want full model switching mid-session (#3709), working `auto` reasoning-control (#4560), and transparent policy management (#4272).
- **MCP configuration ergonomics:** Requests for `--disable-repo-mcps` (#3380), workspace-level MCP connection fixes (#4542), and persistent instruction-file exclusion (#4603) show MCP tooling is maturing but still has gaps.
- **Cross-session/cross-machine sharing:** Session export (#1153) and multi-device session sharing (#3537) reflect a desire for collaborative and portable workflows.
- **Plugin & extension stability:** The new plugins dashboard (#4607) is welcomed, but extension SDK reconnection bugs (#4590) suggest the plugin surface needs more robust lifecycle handling.

---

## 6. Developer Pain Points

1. **MCP auth instability on the prerelease channel** — Issues #4542, #4604, and #4606 all concern MCP servers failing to authenticate or connect. The 1.0.81-10 release introduced a token-injection regression (#4604), and Google's OAuth trailing-slash mismatch (#4606) blocks a major provider out of the gate.
2. **Prerelease update regressions** — #4605 shows the `latest-prerelease` lookup logic ranks by `created_at` rather than semantic version, stranding users on an older build. This, combined with #4535 (`store_memory` broken), means prerelease users are hitting multiple blockers.
3. **Session lifecycle bugs on Windows** — #4593 (file-lock error during archival) and #4590 (hook-processor disposal on reconnect) indicate session management has platform-specific and multi-extension edge cases that remain unresolved.
4. **Enterprise policy opacity** — #4272 and the v1.0.81-11 fix for #4607 both highlight that enterprise model/MCP restrictions are poorly surfaced to end users, creating confusion when features appear "greyed out" or "stuck pending."
5. **Missing shell-level flags** — #3380 and #4035 reflect a pattern: users frequently need programmatic control over what gets loaded (repo MCPs, voice dependencies) without GUI or interactive opt-outs.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-26

## 1. Today's Highlights

Two open issues were updated in the last 24 hours, both raising concerns about reliability. The most pressing is **#2617**, where the `Edit` and `Write` tools silently no-op since August 25th on version 0.38.0 (macOS), returning success messages without actually writing to disk — a 100% reproducible bug affecting core functionality. Additionally, **#2523** resurfaced with a long-standing context compaction bug causing Kimi Code to re-open already completed and deleted tasks.

No new releases or pull requests were published in the last 24 hours.

---

## 2. Releases

No new releases in the last 24 hours. The current latest reported version is **0.38.0**.

---

## 3. Hot Issues

**[#2617] Edit/Write tools report success but never write to disk** (0.38.0, macOS)
*Author: tizerluo | Created: 2026-08-25 | 2 comments*
⭐ Why it matters: This is a critical reliability bug affecting the two most fundamental file-editing tools in the CLI. A 100% reproducible silent no-op means users receive false success confirmations while nothing is persisted to disk — potentially causing data loss or broken workflows. macOS-specific but severity is high given the core impact.
*Community reaction:* Awaiting triage; no upvotes yet but the immediacy of the issue (created today) and severity suggest rapid escalation.
🔗 https://github.com/MoonshotAI/kimi-cli/issues/2617

**[#2523] Context compaction bug — Kimi Code reopens an already completed and deleted task** (v0.6.3)
*Author: Frogzter | Created: 2026-07-20 | Updated: 2026-08-25 | 1 comment*
⭐ Why it matters: A persistent context management bug where completed and deleted tasks are unexpectedly re-opened. This indicates a flaw in the session/task lifecycle management and context compaction logic, which is essential for long-running coding sessions. Reported on Windows with the K2.7 coding model, suggesting a cross-platform concern.
*Community reaction:* Issue has been open since July 20th with a recent update — the long open duration suggests it may be difficult to reproduce or diagnose.
🔗 https://github.com/MoonshotAI/kimi-cli/issues/2523

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

Based on the current issue landscape, the dominant themes emerging are:

- **Tool Reliability & Trustworthiness** — The #2617 bug highlights a growing concern that tool output (success messages) cannot be trusted, eroding user confidence in the CLI's core edit/write capabilities.
- **Context & Session Management** — The #2523 compaction bug points to ongoing challenges with task state persistence and session lifecycle management, especially in long-running or complex workflows.
- **Cross-Platform Consistency** — Issues are being reported across both macOS and Windows, suggesting parity gaps in bug behavior and tool consistency between platforms.

---

## 6. Developer Pain Points

1. **Silent Failures in Core Tools** — The #2617 bug is a textbook example of the most damaging class of issues: tools that *appear* to succeed while producing no observable effect. For developers relying on Kimi Code CLI as an automated editor, this is a dealbreaker-level problem.

2. **Context Compaction Unreliability** — Long-running sessions that rely on context compaction to manage memory are at risk of state corruption or task resurrection (#2523), forcing developers to either restart sessions (losing context) or work around the bug.

3. **Platform-Specific Reproducibility** — Both issues are reported on specific platforms (macOS and Windows respectively), raising the concern that platform-specific regressions may slip through CI and reach users unpredictably.

4. **Slow Triage on High-Severity Bugs** — Issue #2617, affecting core write functionality at 100% reproducibility, has received minimal engagement after 24 hours, which may slow resolution for time-sensitive workflows.

---

*Data sourced from github.com/MoonshotAI/kimi-cli · Digest generated 2026-08-26*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-26

## 1. Today's Highlights
OpenCode **v1.18.23** shipped with critical fixes for Cloudflare AI Gateway routing, ensuring third‑party and Anthropic models work correctly through the gateway. The community is actively troubleshooting widespread **tool‑call failures** on Ox Alpha Free and Zen providers, while several PRs target persistent session management, plugin updates, and refined model resolution.

## 2. Releases
**v1.18.23** – Core bugfixes  
- Fixed Cloudflare AI Gateway routing for third‑party providers so non‑Workers models work through the gateway's REST API.  
- Fixed Anthropic models through Cloudflare AI Gateway by converting dotted model IDs (e.g., `claude‑haiku‑4.5`) to the dashed slug Anthropic expects.  
🔗 [GitHub Release](https://github.com/anomalyco/opencode/releases)

## 3. Hot Issues
| Issue | Why It Matters | Community Reaction |
|-------|----------------|-------------------|
| [#44300](https://github.com/anomalyco/opencode/issues/44300) Zen API: Ox Alpha Free fails with "Endpoint is unavailable" for any request containing tools | Tool‑calling endpoints are completely broken for a popular free model, blocking many agent workflows. | 13 comments, 5 👍 |
| [#33618](https://github.com/anomalyco/opencode/issues/33618) Qwen 3.7 Plus/Max (via OpenRouter) unknown/invalid tool calls | Sporadic empty tool names cause repeated retries and aborted sessions with widely used Qwen models. | 10 comments, 4 👍 |
| [#35434](https://github.com/anomalyco/opencode/issues/35434) Multi‑question tool calls fail silently in TUI since v1.17.13 | Regression that silently drops multi‑question tool calls, breaking interactive workflows. | 7 comments, 0 👍 (closed) |
| [#44850](https://github.com/anomalyco/opencode/issues/44850) Ox Alpha Free fails with "Endpoint is unavailable" when OpenCode uses tools | Same root cause as #44300 but on the Console route; confirms cross‑provider impact. | 7 comments, 2 👍 |
| [#14524](https://github.com/anomalyco/opencode/issues/14524) Display model cost in the model picker | Users lack visibility into pricing when selecting models, hindering cost‑aware development. | 5 comments, 11 👍 |
| [#43277](https://github.com/anomalyco/opencode/issues/43277) Sessions permanently stuck during normal use — survive reboots | Sessions become unrecoverable even after full system restarts, forcing manual intervention. | 5 comments, 0 👍 |
| [#45087](https://github.com/anomalyco/opencode/issues/45087) Auto‑updater ate 266 GB by reinstalling OpenCode every 10 minutes | A critical bug in the update loop caused massive npm cache bloat, disrupting long‑running server processes. | 4 comments, 0 👍 |
| [#44799](https://github.com/anomalyco/opencode/issues/44799) Model resolution fails when model ID contains "/" (NVIDIA NIM) | Provider‑prefix duplication breaks model lookup for NVIDIA NIM models and similar IDs. | 2 comments, 0 👍 |
| [#44910](https://github.com/anomalyco/opencode/issues/44910) Zen Go `/v1/responses` returns 500 for all non‑DeepSeek models | Gateway endpoint regression that breaks any non‑DeepSeek model when using the `/responses` route. | 2 comments, 0 👍 |
| [#45055](https://github.com/anomalyco/opencode/issues/45055) Qwen3.8‑27B + SGLang: multiple system messages cause failures | OpenCode still emits multiple `role: "system"` fragments, breaking strict chat‑template backends. | 2 comments, 0 👍 |

## 4. Key PR Progress
| PR | Description |
|----|-------------|
| [#45122](https://github.com/anomalyco/opencode/pull/45122) `fix(sdk): keep packaged Effect runtime coherent` | Resolves incompatible Effect RC resolution in fresh npm installs, fixing Cloudflare Worker health‑check failures. |
| [#45110](https://github.com/anomalyco/opencode/pull/45110) `feat(core): support git plugin packages` | Enables installation of plugins from Git repositories, closing a gap for private/in‑repo plugins. |
| [#44971](https://github.com/anomalyco/opencode/pull/44971) `feat(tui): add persistent session terminals` | Introduces a fixed session frame with a persistent terminal pane, simplifying terminal management within sessions. |
| [#45118](https://github.com/anomalyco/opencode/pull/45118) `feat(core): support explicit plugin updates` | Allows plugins to be checked and updated deliberately, avoiding in‑memory state loss during updates. |
| [#45120](https://github.com/anomalyco/opencode/pull/45120) `fix(tool): simplify the glob path parameter description` | Clarifies the `path` parameter description to reduce unstable tool‑calling behavior with models like Qwen3‑Coder. |
| [#45114](https://github.com/anomalyco/opencode/pull/45114) `fix(provider): resolve model IDs that repeat the provider prefix` | Fixes model resolution for IDs that already include a vendor segment (e.g., NVIDIA NIM models). |
| [#45119](https://github.com/anomalyco/opencode/pull/45119) `feat(tui): add plugin update controls` | Exposes plugin version visibility and safe update actions in the `/plugins` dialog. |
| [#45107](https://github.com/anomalyco/opencode/pull/45107) `feat(core): add directory projects` | Directories without Git/Hg repos are now treated as independent projects instead of falling into a global project. |
| [#45029](https://github.com/anomalyco/opencode/pull/45029) `feat(tui): browse projects, directories, and worktrees` | Enhances the Open dialog to show nested directories, Git worktrees, and non‑Git locations associated with existing sessions. |
| [#45108](https://github.com/anomalyco/opencode/pull/45108) `feat(ai): add native Groq and DeepInfra providers` | Adds first‑class support for Groq and DeepInfra via the existing OpenAI Chat protocol. |

## 5. Feature Request Trends
- **Cost visibility** – Users consistently request model pricing in the picker (#14524).  
- **Plugin management** – Demand for Git‑based plugin installation, explicit update controls, and version visibility.  
- **Session & terminal UX** – Persistent session terminals, browsing of directories/worktrees, and clearer prompt‑metadata display.  
- **Provider expansion** – Native integration for Groq, DeepInfra, and more stable handling of NVIDIA NIM and OpenRouter models.  
- **Tool‑call reliability** – Simplified parameter descriptions and robust handling of multi‑question tool calls.

## 6. Developer Pain Points
- **Tool‑call failures** across multiple providers (Ox Alpha Free, Qwen, Zen) leading to silent errors or endpoint‑unavailable messages.  
- **Session stability** – Sessions becoming permanently stuck, surviving reboots, and requiring force‑quit.  
- **Update‑loop bloat** – Auto‑updater misbehaving and consuming hundreds of gigabytes in npm cache.  
- **Model resolution** – Breaking changes when model IDs contain slashes or repeat provider prefixes.  
- **Logging & debugging** – `--log-level DEBUG` failing to output logs when log files exceed a threshold.  
- **Platform quirks** – Windows console flashes on subprocess spawn, TUI freezes on certain Linux desktops, Electron renderer loops.  
- **API‑key confusion** – Users accidentally misconfiguring API settings and receiving persistent invalid‑key errors.  

---
*Digest generated from GitHub data for 2026-08-26. All links point to the OpenCode repository on GitHub.*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-26

## Today's Highlights

A wave of fixes landed overnight targeting compaction reliability, provider compatibility (Bedrock, OpenRouter reasoning, Codex thread affinity), and a bundled CLI extension-load regression in 0.84.3. The community also surfaced a persistent Windows onboarding question and a new eager tool-execution experiment, signaling momentum around both stability and performance.

---

## Releases

No releases in the last 24 hours.

---

## Hot Issues

1. **[Windows onboarding survey** (#7547) — The most-discussed open issue (49 comments). Developers want a unified story for running Pi on Windows across the many available paths (native, WSL, etc.). Community reaction: high engagement, 2 👍. [Link](https://github.com/badlogic/pi-mono/issues/7547)

2. **TUI row corruption during streaming** (#8584, CLOSED) — Assistant text renders one word per line after long tool output. Caused by `reasoning_details` chunks arriving as separate objects without merging into `thinkingSignature`, producing a one-word-per-line artifact. 9 comments, 5 👍. [Link](https://github.com/badlogic/pi-mono/issues/8584)

3. **AgentSession lifecycle bugs** (#5886, OPEN) — Meta-issue tracking post-run continuation failures where the agent tries to resume from a transcript that's no longer valid. Open by mitsuhiko with 9 comments and 4 👍. [Link](https://github.com/badlogic/pi-mono/issues/5886)

4. **Truncated response errors** (#7855, CLOSED) — Random "Response was truncated before completion." messages across OpenAI-compatible APIs, including local VLLM. Required manual continue prompts. 7 comments, 4 👍. [Link](https://github.com/badlogic/pi-mono/issues/7855)

5. **PowerShell 5.1 fallback in interactive mode** (#8582, CLOSED) — Built-in `powershell` tool defaults to Windows PowerShell 5.1 on interactive mode despite `pwsh` being on PATH; `-p` mode correctly uses pwsh. 6 comments. [Link](https://github.com/badlogic/pi-mono/issues/8582)

6. **Node.js 24 `taskkill` ENOENT** (#6596, OPEN) — `killProcessTree()` spawns `taskkill` without an absolute System32 path, breaking on Node.js 24. Patch in progress with 5 comments. [Link](https://github.com/badlogic/pi-mono/issues/6596)

7. **Gemini 3.7 Flash rejects `/tree` summarization** (#8456, CLOSED) — The built-in branch-summary request omits `reasoning`, causing Gemini 3.7 Flash to reject it with "MINIMAL thinking not supported." 4 comments, 2 👍. [Link](https://github.com/badlogic/pi-mono/issues/8456)

8. **npm 11.16.0 blocking extension installs** (#6600, OPEN) — New npm default blocks lifecycle scripts, breaking `pi update --extensions`. Workaround not obvious to users. 4 comments. [Link](https://github.com/badlogic/pi-mono/issues/6600)

9. **Compaction reserve not scaled to context window** (#8651, CLOSED) — Fixed a bug where `compaction.reserveTokens` (default 16384) could exceed the usable budget on small local models, triggering spurious compaction. 3 comments. [Link](https://github.com/badlogic/pi-mono/issues/8651)

10. **`thinkingTokenBudgetField` ignored** (#8444, CLOSED) — Setting a custom budget field name had no effect; only `supportsThinkingTokenBudget: true` worked, and it wasn't compatible with llama.cpp. 3 comments. [Link](https://github.com/badlogic/pi-mono/issues/8444)

---

## Key PR Progress

1. **#8656 — Repair startup after `pi update`** (CLOSED) — Fixes jiti v2.6.1 breaking the `./static` export and ambient module augmentation targets. [Link](https://github.com/badlogic/pi-mono/pull/8656)

2. **#8650 — Omit Responses `tool_choice` when no tools sent** (CLOSED) — Fixes compaction failures on xAI/Grok which reject `tool_choice: "none"` without tool definitions. [Link](https://github.com/badlogic/pi-mono/pull/8650)

3. **#8642 — Hoist Bedrock tool-result images for OpenAI models** (CLOSED) — OpenAI models on Bedrock reject images nested in `toolResult.content`; this moves them to sibling content blocks. Fixes #8643. [Link](https://github.com/badlogic/pi-mono/pull/8642)

4. **#8639 — Add Opper provider** (CLOSED) — New built-in OpenAI-compatible provider (`api.opper.ai/v3/compat`) with full catalog, env key, and docs. [Link](https://github.com/badlogic/pi-mono/pull/8639)

5. **#8635 — Preserve aborted stop reason during lazy setup** (OPEN) — Passes abort signal through lazy stream wrappers so setup failures report as aborted when the request is already cancelled. Fixes #8409. [Link](https://github.com/badlogic/pi-mono/pull/8635)

6. **#8629 — Eager tool execution (V1)** (CLOSED) — Opt-in eager execution for discard-safe tools; local `read` calls start at `toolcall_end` and reuse outcomes without normal lifecycle events. [Link](https://github.com/badlogic/pi-mono/pull/8629)

7. **#8627 — Use `ctx.cwd` for cwd-sensitive tools** (CLOSED) — Tools now resolve paths against the session's real cwd when available, fixing path resolution for extensions. [Link](https://github.com/badlogic/pi-mono/pull/8627)

8. **#8570 — Preserve Codex thread-affinity headers** (CLOSED) — Adds the missing `thread-id` header to OpenAI Codex Responses requests, matching the upstream Codex client behavior. [Link](https://github.com/badlogic/pi-mono/pull/8570)

9. **#8623 — Fix off-by-one in read tool line count** (CLOSED) — Stops counting trailing newline as an extra line (`split("\n")` phantom element). Fixes #7329. [Link](https://github.com/badlogic/pi-mono/pull/8623)

10. **#8614 — Derive OpenRouter reasoning controls** (CLOSED) — Fixes OpenRouter reasoning control mapping. [Link](https://github.com/badlogic/pi-mono/pull/8614)

---

## Feature Request Trends

- **Provider expansion** — Continued demand for new built-in providers (Opper added; SiliconFlow requested in #4742) and better handling of provider-specific quirks (Bedrock image nesting, OpenRouter reasoning fields, Gemini thinking-level compatibility).
- **Eager / performance optimizations** — The eager tool execution PR (#8629) and the O(n²) streaming re-parse fix (#7698) reflect growing community interest in reducing latency for tool-heavy sessions.
- **Windows-first onboarding** — Issue #7547 shows a clear demand for a streamlined, well-documented Windows experience rather than delegating to community workarounds.
- **Session reliability** — Recurring themes around compaction correctness, abort handling, and transcript lifecycle suggest users want more robust long-running agent sessions.

---

## Developer Pain Points

- **Windows PowerShell mismatch** — The built-in tool silently falls back to PowerShell 5.1 in interactive mode (#8582), creating confusion for users who expect `pwsh`.
- **npm breaking changes** — `pi update --extensions` is fragile against npm default changes (#6600); users need clear guidance on script approval.
- **Node.js 24 compatibility** — Hardcoded `taskkill` paths break on newer Node (#6596), a recurring pattern of platform-path assumptions causing ENOENT errors.
- **Vision/image budget limits** — Accumulated image tool results brick sessions on vision models with patch budgets (#8636, #8643); users need either auto-hoisting or file-reference strategies (#8617).
- **Compaction edge cases** — Multiple interrelated issues (#8651, #8652, #8653, #8444) around compaction reserves, reasoning effort clamping, and thinking budget fields indicate the compaction pipeline still has rough edges, especially for smaller/local models.
- **Bundled CLI extension loading** — Version 0.84.3 introduced a regression where extensions importing `@earendil-works/pi-coding-agent` fail to load (#8620), disrupting users who rely on the bundled CLI.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-26

## 1. Today's Highlights

A major architectural review of `packages/core` and `packages/cli` surfaced 14 structural issues (notably the core type system being coupled to `@google/genai` across 136 files), while multiple bugs around OpenAI-compatible provider reasoning-effort clamping and Windows Ctrl+V paste regressions drew community attention. On the CI front, the team is migrating macOS/Windows lanes off PR triggers and routing release jobs to a persistent ECS runner pool to address flaky and costly runs.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#4063](https://github.com/QwenLM/qwen-code/issues/4063) | **Core + CLI architecture review — 14 structural issues** | P0 finding: `ContentGenerator` interface is coupled to `@google/genai` across 136 files, creating a vendor-lock risk and refactoring bottleneck. | 10 comments, 1 👍 — active discussion on remediation priority. |
| [#9459](https://github.com/QwenLM/qwen-code/issues/9459) | **`/effort max` bricks sessions on OpenAI-compatible providers** | `clampReasoningEffort()` fails to clamp the `"max"` value, causing every subsequent request in a session to return 400 errors until the tier is changed. | 10 comments — high-impact bug for users of non-native providers. |
| [#9061](https://github.com/QwenLM/qwen-code/issues/9061) | **Ctrl+V paste unresponsive in CLI on Windows (regression since 0.21.x)** | Clipboard works system-wide; the regression broke a core UX interaction for Windows CLI users. Downgrading to 0.21.0 restores functionality. | 7 comments — confirmed regression with clear workaround. |
| [#6762](https://github.com/QwenLM/qwen-code/issues/6762) | **Skill Context Lifecycle Management** | SKILL.md bodies remain in conversation history forever; no mechanism to unload or compress them, causing context bloat in long-running sessions. | 6 comments — aligns with ongoing context-performance roadmap. |
| [#9198](https://github.com/QwenLM/qwen-code/issues/9198) | **OOM crash during extended runs on 1TB-memory servers** | User reports OOM after a week-long run, followed by terminal input corruption (tmux key乱码). Memory capacity is not the issue; likely a leak. | 6 comments — serious reliability concern for production use. |
| [#8227](https://github.com/QwenLM/qwen-code/issues/8227) | **Windows `@`-file reads lose `O_NOFOLLOW` protection** | Follow-up to PR #7206: symlink/TOCTOU hardening is materially weaker on Windows because `O_NOFOLLOW` doesn't exist, and the fallback idiom is untested there. | 5 comments — security-relevant, needs platform-specific test coverage. |
| [#9733](https://github.com/QwenLM/qwen-code/issues/9733) | **Loop detection false-positives kill unattended turns** | Legitimate state-advancing tool-call sequences (write → run → edit → verify) trigger loop detection, terminating the turn with no recovery path except a human message. | 4 comments — blocks long automation workflows. |
| [#9827](https://github.com/QwenLM/qwen-code/issues/9827) | **`permissions.allow` doesn't restrict tool schemas sent to the model** | The allowlist correctly filters the CLI `/tools` display but the full built-in tool set is still sent in the API request, undermining permission enforcement. | 4 comments — security/privacy gap. |
| [#5823](https://github.com/QwenLM/qwen-code/issues/5823) | **`/loop` cron tasks fire silently with no visibility** | Model cannot list or stop its own scheduled cron tasks; orphaned loops auto-start fresh sessions with zero prompting, wasting tokens. | 5 comments — automation observability gap. |
| [#10000](https://github.com/QwenLM/qwen-code/issues/10000) | **`/find-simplifications` candidate ledger** | Ongoing append-only ledger tracking dead files, stale allowlist rows, orphan locale keys, and exports without consumers across the repo. | 5 comments — community-maintained hygiene tool. |

## 4. Key PR Progress

| # | PR | Description |
|---|-----|-------------|
| [#10060](https://github.com/QwenLM/qwen-code/pull/10060) | **fix(cli): make review cleanup prefix-free across dash-extended targets** | Fixes `qwen review cleanup` incorrectly sweeping a concurrent review's side files when one target token is a dash-prefix of another (e.g. `src/foo` vs `src/foo-bar`). |
| [#10059](https://github.com/QwenLM/qwen-code/pull/10059) | **ci: take macOS and Windows lanes off PR triggers** | Moves flaky macOS/Windows jobs off the PR path; they retain nightly, merge-queue, and dispatch schedules. Addresses cost and noise. |
| [#9993](https://github.com/QwenLM/qwen-code/pull/9993) | **feat(web-shell): make compact view the only mode** | Retires the compact-mode toggle, removes Ctrl+O shortcut and related i18n copy; compact rendering becomes the default-and-only path. |
| [#9441](https://github.com/QwenLM/qwen-code/pull/9441) | **fix(core): show edit/exec diffs when a PreToolUse hook returns ask** | When a PreToolUse hook bounces a call to `awaiting_approval`, the user now sees the actual diff rather than a synthetic plain-text prompt. |
| [#9607](https://github.com/QwenLM/qwen-code/pull/9607) | **fix(core): demote balanced inline thinking blocks instead of failing the turn** | Hybrid-thinking models on OpenAI-compatible endpoints that emit a second balanced `<think>` block inside `content` no longer crash the turn. |
| [#9995](https://github.com/QwenLM/qwen-code/pull/9995) | **fix(cli): preserve bridge timeouts for mid-turn media** | Image/audio/resource attachments injected mid-turn now use their media bridge's own timeout/retry policy while preserving turn-cancellation. |
| [#10032](https://github.com/QwenLM/qwen-code/pull/10032) | **fix(core): scan archived sessions in findSessionTitlesByPrefix** | Branching a session now correctly checks archived `chats/` titles to avoid `(Branch N)` collisions. |
| [#9739](https://github.com/QwenLM/qwen-code/pull/9739) | **feat(core): bind PRs created via `gh pr create` in the session shell** | Closes the last gap in session↔PR binding: sessions where the agent created the PR via shell command (vs. the Web Shell Git dialog) are now detected. |
| [#9761](https://github.com/QwenLM/qwen-code/pull/9761) | **feat(review): keep deferred suggestions recoverable off the PR page** | Suggestions deferred after review convergence round 6+ are now recoverable by tooling that arrives after the review finishes. |
| [#9988](https://github.com/QwenLM/qwen-code/pull/9988) | **feat(web-shell): add session token usage panel** | Opt-in panel showing total usage, per-model breakdown, subagent invocations, and localized tool stats with manual refresh and background polling. |

## 5. Feature Request Trends

- **Context & token management** — Skill context lifecycle (Issue #6762), telemetry on LLM spans with context breakdown (Issue #10015), and compression correctness (Issue #9309) all point to growing demand for finer-grained control over what enters and persists in the model's context window.
- **Automation observability** — Silent `/loop` cron tasks (Issue #5823) and the need for in-session task listing/stop suggest users want the agent to have first-class control over its own scheduled work.
- **Debugging integration** — Native DAP support (Issue #10051) is a new request, indicating users want programmatic debugger interaction beyond terminal output and static analysis.
- **Session management** — Session rotation per channel (PR #8927, Issue #8583) and archived-session title resolution (PR #10032) show continued investment in long-running, multi-session workflows.
- **Web Shell maturity** — Compact-only view (PR #9993), interactive browser terminal (PR #9984), and token usage panel (PR #9988) reflect a push toward a more complete browser-based IDE experience.

## 6. Developer Pain Points

- **Provider compatibility friction** — Multiple issues surface around OpenAI-compatible endpoints: reasoning-effort clamping failure (#9459), hybrid-thinking model crashes (#9607, now fixed in PR #9607), and Auto Mode classifier unavailability on OpenRouter (#9757). The model routing and streaming-layer assumptions are tightly coupled to native providers.
- **Windows-specific regressions** — Ctrl+V paste broken since 0.21.x (#9061), weaker symlink protection on `@`-file reads (#8227), and the Windows test lane being red for an extended period (#9481) indicate platform parity remains a persistent challenge.
- **Loop detection over-aggression** — False-positive loop kills (#9733) block legitimate multi-stage automation (write → run → verify cycles), forcing manual intervention and breaking unattended workflows.
- **Permission model inconsistency** — `permissions.allow` filters the CLI surface but not the API request payload (#9827), creating a gap between what users see and what the model receives.
- **CI cost and flakiness** — High-concurrency ENOSPC errors (#10035), vitest RPC timeouts from synchronous test suites (#10050), and the decision to remove macOS/Windows from PR triggers (#10059) all signal that CI infra is a recurring pain point driving architectural changes.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-26

## 1. Today's Highlights

The v0.9.12 integration branch (#5576) is now code-complete with 72 commits, gated only on version-bump and changelog checks. The team closed a major provider-neutrality audit (#5588), eliminating 18 DeepSeek-exclusive gates across 279 files, while three supervised-operation features — control socket, `/relaunch`, and lifecycle outbox — shipped together this cycle.

---

## 2. Releases

No new releases in the last 24 hours. v0.9.11 remains the latest published version (released 2026-08-23).

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#5316](https://github.com/Hmbown/CodeWhale/issues/5316) | EPIC-005: CodeWhale TUI Crate Decomposition | Umbrella tracking issue for the entire crate restructuring effort; all sub-EPICs and FEAT reports roll up here. | 16 comments — active coordination. |
| [#5588](https://github.com/Hmbown/CodeWhale/issues/5588) | Provider neutrality: 18 DeepSeek-exclusive gates | Audit of 2,281 lines found 18 suspect gates where behavior was hard-locked to DeepSeek despite being conceptually provider-neutral. All fixed in this batch. | 5 comments — leads the v0.9.12 neutrality push. |
| [#5556](https://github.com/Hmbown/CodeWhale/issues/5556) | Onboarding: opt-in `/tutorial` pager | First-run spine exists but lacks a guided tour; this adds `/tutorial`/`/tour` with a "Coming from Claude, Cursor, or Codex?" entry page. | 4 comments — UX onboarding gap identified. |
| [#4394](https://github.com/Hmbown/CodeWhale/issues/4394) | Compaction: structured survival contract | Compaction has substantial implementation but no explicit contract governing what survives; a formal spec is needed for reliability. | 4 comments — long-open reliability concern. |
| [#5583](https://github.com/Hmbown/CodeWhale/issues/5583) | Workflow responseSchema failures need bounded repair | Schema-mismatched child responses currently abort runs with no repair attempt or raw-output receipt. | 4 comments — v0.9.12 workflow reliability blocker. |
| [#5582](https://github.com/Hmbown/CodeWhale/issues/5582) | Workflow owner snapshots collapse Degraded into Completed | `WorkflowRunStatus::Degraded` was mapped to `OwnerState::Completed`, hiding failure states from users. | 4 comments — visible state corruption bug. |
| [#5533](https://github.com/Hmbown/CodeWhale/issues/5533) | Control surface for supervised operation | Per-session control socket (message/interrupt/relaunch/status) plus `RuntimeBackendKind::External` for automation harnesses. | 3 comments — enables unattended/CI workflows. |
| [#5562](https://github.com/Hmbown/CodeWhale/issues/5562) | Stale write-claims lock sub-agents out | Write-claim locks persist forever after sub-agent sessions, cascading into total command-execution lockout on Windows. | 3 comments — reproduces across restarts. |
| [#5617](https://github.com/Hmbown/CodeWhale/issues/5617) | Reduce background git command runs & `.git/index.lock` | Internal read-only git probes spawn the real `git` CLI, occasionally holding `.git/index.lock` and blocking user `git commit`. | 2 comments — direct developer productivity impact. |
| [#5601](https://github.com/Hmbown/CodeWhale/issues/5601) | Fresh install: MiniMax/Xiaomi return 404 | Built-in URLs for MiniMax and Xiaomi models are incorrect; DeepSeek works fine. Forces downgrade to v0.6 for config. | 3 comments — blocks new user onboarding. |

---

## 4. Key PR Progress

| # | PR | Description | Status |
|---|-----|-------------|--------|
| [#5576](https://github.com/Hmbown/CodeWhale/pull/5576) | v0.9.12 integration: must-fix + UX fixes | 72-commit integration branch; release-blocker fixes are complete, gated on version bump + changelog. | **OPEN** (WIP, not to merge until gates are green) |
| [#5616](https://github.com/Hmbown/CodeWhale/pull/5616) | Move `git_status`/`git_diff` off async executor thread | `std::process::Command::output()` was called directly inside async `execute()`, stalling the tokio worker pool and hanging sessions with no error or timeout. | **CLOSED** |
| [#5608](https://github.com/Hmbown/CodeWhale/pull/5608) | Focused transcript actions | `y`/`Y`/`Enter` on focused blocks: copy content, copy metadata/receipt, open fullscreen pager. Addresses #5551. | **CLOSED** |
| [#5611](https://github.com/Hmbown/CodeWhale/pull/5611) | Show tool and MCP schema costs | Context inspector now displays bounded schema-cost estimates per tool and per MCP server from the last model tool catalog. Rebase of #5603. | **CLOSED** |
| [#5594](https://github.com/Hmbown/CodeWhale/pull/5594) | Control socket — part d (final) | Opt-in Unix-only newline-framed JSON-RPC socket per running session for remote supervision. Closes #5533. | **CLOSED** |
| [#5593](https://github.com/Hmbown/CodeWhale/pull/5593) | `/relaunch` command — part c | Self-relaunch so `/update` can switch to the new binary in one step without manual restart. Closes #5532. | **CLOSED** |
| [#5592](https://github.com/Hmbown/CodeWhale/pull/5592) | Lifecycle outbox — part b | Opt-in `[lifecycle_outbox]` config writing one JSONL line per lifecycle event (including `turn_stalled`/`turn_failed`) to a file. Closes #5531. | **CLOSED** |
| [#5584](https://github.com/Hmbown/CodeWhale/pull/5584) | Persist child approval receipts | Child approvals now inherit the session approval receipt store; `Asked` is committed before exposing the prompt, outcomes before closing. Closes #5543. | **CLOSED** |
| [#5610](https://github.com/Hmbown/CodeWhale/pull/5610) | Preserve Windows verbatim-path operands | Fixes two Windows CI failures in FEAT-019 where verbatim paths were incorrectly POSIX-split. | **CLOSED** |
| [#5609](https://github.com/Hmbown/CodeWhale/pull/5609) | Adopt command shapes in memory group (FEAT-019) | Converts `/note` and `/memory` to external command shapes per the FEAT-014/015/018 pattern. | **CLOSED** |

---

## 5. Feature Request Trends

1. **Supervised/automated operation** — Control socket, lifecycle outbox, and `/relaunch` form a coordinated push to make CodeWhale sessions callable from external harnesses, CI, and terminal multiplexer wrappers without a human at the screen.
2. **Provider neutrality** — The 18-gate audit (#5588) signals a deliberate shift toward multi-provider parity; DeepSeek-specific hardlocks are being replaced with abstracted adapter layers.
3. **Cost transparency** — Tool and MCP schema cost display (#5611, #5553) and the compaction survival contract (#4394) both aim to give users visibility into token spend and context lifecycle.
4. **Workflow reliability** — Bounded responseSchema repair (#5583), degraded-state snapshot fixes (#5582), and child approval persistence (#5584) address a cluster of workflow-engine bugs surfacing in v0.9.12.
5. **Onboarding UX** — The `/tutorial` pager (#5556) and focused-block actions (#5608) reflect sustained investment in reducing friction for new users, especially migrants from Claude Code, Cursor, and Codex.

---

## 6. Developer Pain Points

- **Git CLI blocking the async runtime** — Internal read-only git probes spawning blocking `std::process::Command` calls on the tokio worker pool caused session hangs and `.git/index.lock` collisions (#5617, #5616). A follow-up proposes replacing the CLI entirely with `gix`/gitoxide (#5618).
- **Windows path handling** — Verbatim `\\?\` paths were incorrectly split by POSIX word-splitting logic, breaking both shell and subagent tests (#5610).
- **Stale lock/state bugs** — Write-claim locks persisting across sub-agent sessions (#5562) and degraded workflow states collapsing into completed (#5582) indicate that lifetime management of ephemeral runtime resources needs stronger cleanup contracts.
- **Built-in provider URLs are wrong** — Fresh installs for MiniMax and Xiaomi return 404 due to incorrect hardcoded endpoints (#5601), forcing users to downgrade or configure manually.
- **Approval receipts not durable** — Child agent approvals could be granted from in-memory state without a persisted record, creating audit gaps (#5584).

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*