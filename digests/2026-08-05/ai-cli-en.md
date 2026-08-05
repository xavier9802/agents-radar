# AI CLI Tools Community Digest 2026-08-05

> Generated: 2026-08-05 03:13 UTC | Tools covered: 10

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



# AI CLI Tools Cross-Comparison Report — 2026-08-05

---

## 1. Ecosystem Overview

The AI CLI ecosystem is entering a phase of platform stabilization and enterprise hardening. All nine tracked tools are actively shipping security fixes, refining agent orchestration primitives, and expanding provider/protocol support. The dominant theme is **agent reliability at scale** — across Claude Code, Gemini CLI, OpenCode, and DeepSeek TUI, subagent hangs, context-compaction bugs, and turn-limit misreporting are the most common community complaints. A secondary wave concerns **cross-platform parity**, with Windows and macOS desktop instability (Claude Code GPU crashes, Codex resource runaways, Kimi IME bugs) contrasted against a persistent Linux desktop gap (Codex #11023 with 917 👍). Security remains front-and-center: Gemini shipped three critical fixes (SSRF, bash bypass, MCP consent reflection), Claude Code hardened isolated-session enforcement, and GitHub Copilot introduced a breaking sandbox-setting rename.

---

## 2. Activity Comparison

| Tool | Hot Issues | Key PRs | Release (24h) | Release Type |
|---|---|---|---|---|
| **Claude Code** | 10 | 11 | v2.1.222 | Security hardening |
| **OpenAI Codex** | 10 | 12 | v0.147.0-alpha.7 (+3 patches) | Rapid-fire alpha |
| **Gemini CLI** | 10 | 9 | None | — |
| **GitHub Copilot CLI** | 10 | 2 | v1.0.79-1 | Breaking rename |
| **Kimi Code CLI** | 6 | 3 | None | — |
| **OpenCode** | 10 | 10 | v1.18.13 | TUI + RTL fixes |
| **Pi** | 10 | 10 | None | — |
| **Qwen Code** | 10 | 11 | v0.21.6-preview.0 | Browser ext + docs |
| **DeepSeek TUI** | 10 | 11 | v0.9.4 train (open) | Integration build |

**Activity notes:** Codex leads in release velocity (4 alpha patches in 24h). DeepSeek TUI, OpenCode, and Qwen Code show the highest PR throughput relative to hot issues, indicating strong contributor engagement. GitHub Copilot CLI has the lowest PR count (2), suggesting a more internal roadmap pace.

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Need |
|---|---|---|
| **Subagent / multi-agent reliability** | Claude Code, Gemini CLI, OpenCode, DeepSeek TUI, Pi | Hang detection, turn-limit vs. goal misreporting, resume-from-checkpoint, steer/cancel/abort controls |
| **Context compaction fidelity** | OpenCode, Pi, Qwen Code, DeepSeek TUI | Preserve images in compaction tails, configurable summarization model/thinking level, avoid prompt-cache invalidation, accurate per-model context limits |
| **Cross-platform desktop parity** | All tools | Windows stability (GPU crashes, IME, polling lag), macOS resource management, Linux desktop absence (Codex #11023, 917 👍) |
| **MCP / extensibility maturity** | Claude Code, Gemini CLI, Copilot CLI, OpenCode, DeepSeek TUI | Consent dialog transparency, private-CA TLS on macOS, server/discover error handling, registry-first tool discovery, auto-updating plugins |
| **Persistent memory & session continuity** | Kimi Code, OpenCode, Pi, Copilot CLI | Cross-session context, remote session control from any device, session forking, cloud-synced sessions |
| **Agent trustworthiness & sandboxing** | Claude Code, Qwen Code, DeepSeek TUI | Deterministic execution boundaries, hook enforcement gaps in background agents, zero-dependency OS sandboxing |
| **ACP (Agent Client Protocol) parity** | Qwen Code, Kimi Code, DeepSeek TUI, Pi | Model discovery, mid-session switching, tool exposure, permission mode control across IDE and mobile clients |
| **Multi-provider / BYOK support** | OpenAI Codex, Gemini CLI, Pi, Qwen Code, Kimi Code | Local OpenAI-compatible endpoints, SGLang support, European providers (Cortecs), private-CA registry support |

---

## 4. Differentiation Analysis

| Dimension | Tools Leading Here | Tools Lagging |
|---|---|---|
| **Enterprise / security focus** | Claude Code (hook hardening, worktree isolation), Gemini CLI (SSRF fix, MCP consent reflection), Copilot CLI (managed-settings policy, Vault findings) | Kimi Code, OpenCode |
| **Rapid iteration velocity** | OpenAI Codex (4 alpha releases/24h), DeepSeek TUI (77-commit integration train) | Copilot CLI (2 PRs) |
| **Open-source contributor activity** | DeepSeek TUI (11 PRs), Qwen Code (11 PRs), OpenCode (10 PRs) | Copilot CLI (2 PRs — GitHub-internal pace) |
| **Desktop UX maturity** | OpenCode (RTL fixes, TUI history sidebar), Pi (Mermaid rendering, RPC embeddability) | Kimi Code (Windows crashes, IME bugs), Codex (no Linux desktop) |
| **Provider-agnostic flexibility** | Gemini CLI (SGLang + local OpenAI endpoints), Pi (Cortecs, LLM Gateway) | Claude Code (Anthropic-centric), Copilot CLI (GitHub-centric) |
| **Long-context agent workflows** | OpenCode (compaction tail images), Qwen Code (microcompaction cache preservation), DeepSeek TUI (1M-context model support) | Claude Code (10K hook-output truncation, memory leak at 15 GB) |
| **Plugin / skill ecosystem** | OpenCode (plugin extensibility gap acknowledged), Claude Code (hook system mature but leaky) | Kimi Code (ACP client model discovery incomplete) |

---

## 5. Community Momentum & Maturity

| Maturity Tier | Tools | Rationale |
|---|---|---|
| **High momentum, rapid iteration** | OpenAI Codex, DeepSeek TUI, Qwen Code | High PR counts, frequent releases/alpha trains, active integration work (ACP, compiler infra, compaction) |
| **Stable core, enterprise ramp-up** | Claude Code, Pi, OpenCode | Mature release cycles, security hardening focus, enterprise feature gaps (multi-account, billing, compaction reliability) still being addressed |
| **Growing community, platform gaps** | Gemini CLI, Kimi Code CLI | Strong PR activity and security focus, but subagent reliability and Windows/Linux desktop issues indicate maturation still underway |
| **Enterprise-gated, slower public cadence** | GitHub Copilot CLI | Low public PR count, breaking changes land without warning (sandbox rename), enterprise policy issues dominate open issues — signal of internal roadmap pacing |

**Community engagement signals:**
- **Highest vote concentration:** Codex Linux desktop (#11023, 917 👍) — a singular unmet need; Claude Code multi-account (#27302, 335 👍) — enterprise demand; Kimi Code remote control (#1282, 24 👍) — workflow continuity.
- **Most discussion per issue:** Codex Linux desktop (199 comments); Claude Code multi-account (335 👍); Gemini CLI subagent hangs (#21409, P1).
- **Fastest bug-to-fix turnaround:** Gemini CLI (3 security PRs in one cycle); OpenCode (compaction, subagent interrupt, OAuth hardening in same cycle).

---

## 6. Trend Signals

1. **Compaction is the new battleground.** Six tools (Claude Code, OpenCode, Pi, Qwen Code, DeepSeek TUI, Gemini CLI) have compaction-related issues or PRs. The community is moving from "does it compact?" to "does it compact *correctly*?" — preserving images, respecting prompt-cache windows, avoiding silent context loss, and making summarization model/thinking-level configurable.

2. **Agent reliability is the #1 product risk.** Subagent hangs, incorrect termination reporting (GOAL vs. MAX_TURNS), and hook bypass in background agents appear across Claude Code, Gemini CLI, OpenCode, and DeepSeek TUI. Tools that solve this first (steer/cancel/abort, checkpoint resume, deterministic turn-limit handling) will differentiate.

3. **Windows desktop remains the weakest link.** GPU crashes (Claude Code), resource runaways (Codex), IME duplication (Kimi), path-handling bugs (Pi, DeepSeek) — every tool with a desktop component has Windows-specific pain. Linux desktop absence (Codex) is the single highest-voted unmet request in the entire ecosystem.

4. **MCP is maturing but fragmentation persists.** Consent-dialog transparency (Gemini), discover-method strictness (Copilot), private-CA TLS (Copilot macOS), registry-first discovery (DeepSeek), and OAuth flow fixes (Gemini Cloud Workstations) show the protocol is settling but provider and platform gaps remain.

5. **ACP is becoming the integration standard.** Four tools (Qwen Code, Kimi Code, DeepSeek TUI, Pi) are actively shipping ACP features — model discovery, tool exposure, permission mode switching, and RPC embeddability. This signals a shift toward headless and cross-client agent orchestration beyond the CLI itself.

6. **Enterprise policy friction is surfacing.** GitHub Copilot's managed-settings validator rejecting valid enums (#4349), Claude Code's multi-account demand (#27302), and Codex's rate-limit reset confusion (#5999) all indicate that enterprise deployment is outpacing policy configurability. Tools that expose granular, overrideable policy surfaces will gain enterprise traction.

---

*Report generated from community digest data dated 2026-08-05. Data sourced from official GitHub repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
**Data as of 2026-08-05 · Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking

| # | Skill / PR | Functionality | Status | Discussion Highlights |
|---|-----------|--------------|--------|----------------------|
| 1 | **[PR #1298](https://github.com/anthropics/skills/pull/1298)** — `skill-creator` eval fix | Fixes a critical bug where `run_eval.py` reports **0% recall** on every skill description, breaking the entire description-optimization loop | 🟡 Open | 10+ independent reproductions; optimizes the skill-creator pipeline itself |
| 2 | **[PR #1367](https://github.com/anthropics/skills/pull/1367)** — Self-audit skill | Mechanical file verification + four-dimension reasoning quality gate; universal across any project/stack/model | 🟡 Open | Proposes a pre-delivery audit layer for AI output quality assurance |
| 3 | **[PR #514](https://github.com/anthropics/skills/pull/514)** — `document-typography` skill | Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents | 🟡 Open | Addresses a universal pain point affecting every document Claude produces |
| 4 | **[PR #83](https://github.com/anthropics/skills/pull/83)** — `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills evaluating skill quality across 5 dimensions (structure, docs, examples, etc.) and security posture | 🟡 Open | First dedicated quality/security analysis tools for the Skills ecosystem |
| 5 | **[PR #723](https://github.com/anthropics/skills/pull/723)** — `testing-patterns` skill | Comprehensive testing coverage: Testing Trophy model, AAA pattern, React component testing, edge cases | 🟡 Open | Addresses the high-demand testing domain across the full stack |
| 6 | **[PR #1302](https://github.com/anthropics/skills/pull/1302)** — `color-expert` skill | Color naming systems (ISCC-NBS, Munsell, XKCD, RAL), color spaces (OKLCH, OKLAB, CAM16), and practical "what to use when" guidance | 🟡 Open | Niche but well-scoped; fills a gap in design-adjacent tooling |
| 7 | **[PR #181](https://github.com/anthropics/skills/pull/181)** — `SAP-RPT-1-OSS` predictor skill | Leverages SAP's open-source tabular foundation model for predictive analytics on SAP business data | 🟡 Open | Enterprise / vertical-specific demand; Apache 2.0 licensed model |
| 8 | **[PR #525](https://github.com/anthropics/skills/pull/525)** — `pyxel` retro game dev skill | Workflow for Pyxel retro/pixel-art/8-bit game development via MCP server (write → run_and_capture → inspect → iterate) | 🟡 Open | Creative/gaming vertical; demonstrates Skills extending into toy engines |

---

## 2. Community Demand Trends

Analysis of the top issues reveals five clear demand directions:

1. **Reliability & Quality Assurance** — The most vocal demand (Issue #492, 43 comments; PR #1367, PR #83) centers on **trust and safety**: namespace impersonation risks, missing quality gates, and the need for pre-delivery verification pipelines.

2. **Cross-Platform Compatibility** — Three PRs and two issues (PR #1298, #1099, #1050, #1323, #1261 + Issue #1061) target **Windows support** for the skill-creator toolchain. The `run_eval.py` recall bug (Issue #556, 12 comments / 7 👍) is a community-wide blocker.

3. **Document & Content Tooling** — `document-typography` (PR #514), `ODT` (PR #486), and `docx` fixes (PR #541) signal strong demand for **production-quality document generation** beyond basic markdown.

4. **Testing & Code Quality** — `testing-patterns` (PR #723) and `skill-quality-analyzer` (PR #83) reflect a community that wants Claude Code to **self-audit and verify its own output** systematically.

5. **Enterprise & Vertical Integration** — `SAP-RPT-1-OSS` (PR #181), SharePoint concerns (Issue #1175), and org-wide sharing (Issue #228, 16 comments / 8 👍) point to growing **enterprise adoption** wanting domain-specific skills.

---

## 3. High-Potential Pending Skills

These active PRs are unresolved but show strong community engagement and clear value propositions — prime candidates for near-term merge:

| PR | Skill | Why It's High-Potential |
|----|-------|------------------------|
| **[PR #1298](https://github.com/anthropics/skills/pull/1298)** | `skill-creator` eval fix | **Blocker fix** — unblocks the entire description-optimization pipeline for all skill authors |
| **[PR #1367](https://github.com/anthropics/skills/pull/1367)** | Self-audit skill | Addresses the #1 community concern (output quality); directly responds to Issue #1385 proposal |
| **[PR #514](https://github.com/anthropics/skills/pull/514)** | `document-typography` | Universal usability fix; no competing skill; clear scope |
| **[PR #1479](https://github.com/anthropics/skills/pull/1479)** | `plan-file-hygiene` skill | Solves accumulating planning artifacts (Issue #1417); lifecycle management for agent outputs |
| **[PR #723](https://github.com/anthropics/skills/pull/723)** | `testing-patterns` | High-demand domain (testing) with comprehensive coverage; no existing skill fills this |
| **[PR #1302](https://github.com/anthropics/skills/pull/1302)** | `color-expert` | Well-scoped, self-contained, fills a visible gap in design-aware skills |
| **[PR #1050](https://github.com/anthropics/skills/pull/1050)** | Windows subprocess fix | **Blocker fix** — enables skill-creator usage on Windows, unlocking a large contributor segment |

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is for *reliable self-verification*: skills that audit, validate, and quality-gate AI output before delivery — driven by trust concerns over namespace impersonation, the broken skill-creator evaluation pipeline, and a widespread desire for pre-delivery reasoning checks.**

---



# Claude Code Community Digest — 2026-08-05

## 1. Today's Highlights

Claude Code v2.1.222 shipped with critical security fixes: worktree-isolated sessions can no longer run destructive git commands against the main checkout, and PreToolUse auto-allow hooks can no longer bypass tool restrictions in background agents. The community is actively reporting Windows MSIX browser pane GPU crashes, a growing list of Cowork bridge instability issues, and hook output truncation silently dropping data from context.

## 2. Releases

**v2.1.222** — Security hardening for isolated sessions and hook enforcement:
- Fixed worktree-isolated sessions and their subagents being able to run destructive git commands against the main checkout; isolation now applies to file edits and Bash in every session type
- Fixed PreToolUse auto-allow hooks bypassing tool restrictions in background agent tasks

[GitHub: anthropics/claude-code](https://github.com/anthropics/claude-code)

## 3. Hot Issues

| # | Title | Why It Matters | Community |
|---|-------|---------------|-----------|
| [#27302](https://github.com/anthropics/claude-code/issues/27302) | Support multiple Connector accounts | Enterprise users need per-account isolation; 335 👍 signals strong demand | 🔥 Top feature request |
| [#62466](https://github.com/anthropics/claude-code/issues/62466) | Repeated "Image couldn't be processed" errors consuming usage | Bug wastes rate limits on failed image uploads — direct cost impact | 30 comments, 20 👍 |
| [#53247](https://github.com/anthropics/claude-code/issues/53247) | Claude Desktop fails to launch on Windows after crash | Orphaned Job Objects leave the app unrecoverable without a reboot; 11 👍 | Windows reliability concern |
| [#21108](https://github.com/anthropics/claude-code/issues/21108) | Claude accesses git origin on startup before any commands | Security/privacy concern — unexpected network egress before user action | 13 comments, 15 👍 |
| [#81275](https://github.com/anthropics/claude-code/issues/81275) | Browser pane crashes entire app on GPU process exit | Exit code `0x60C201E` crashes on Intel, NVIDIA, and WARP — full app kill, not just the pane | New, 11 comments |
| [#21378](https://github.com/anthropics/claude-code/issues/21378) | Memory leak causes freeze after 20+ minutes (15 GB RAM) | Critical stability issue on WSL2; 12 👍 and "has repro" label | Long-standing pain point |
| [#53408](https://github.com/anthropics/claude-code/issues/53408) | MCP M365 connector rejects personal Microsoft accounts | OAuth flow halts for @hotmail/@outlook/@live users — blocks a large user segment | 7 comments, 19 👍 |
| [#66563](https://github.com/anthropics/claude-code/issues/66563) | Read tool falsely reports unencrypted PDFs as password-protected | False positive blocks legitimate file reads; forces workaround | 6 comments |
| [#81077](https://github.com/anthropics/claude-code/issues/81077) | PostToolUse additionalContext re-serialized between turns, invalidating prompt cache | Directly impacts cost and latency for hook-heavy workflows | 2 comments, 1 👍 |
| [#79953](https://github.com/anthropics/claude-code/issues/79953) | Workflow-internal agent() calls bypass PreToolUse hooks and runtime budget | Security/control gap — internal agents escape outer policy enforcement | 2 comments |

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#84004](https://github.com/anthropics/claude-code/pull/84004) | fix(plugin-dev): limit frontmatter parsing | Restricts YAML frontmatter parsing to the opening block only; rejects files missing markers. Fixes bug where horizontal rules in body text caused `sed` to match mid-file. |
| [#84003](https://github.com/anthropics/claude-code/pull/84003) | fix(scripts): propagate top-level failures | Maintenance scripts now return failing status when duplicate-maintenance rejects at the top level, instead of silently resolving. |
| [#83999](https://github.com/anthropics/claude-code/pull/83999) | fix(scripts): validate gh flag values | Rejects incomplete `gh` commands (e.g., `gh issue list --limit` without a value) before they reach the CLI wrapper. |
| [#83995](https://github.com/anthropics/claude-code/pull/83995) | fix(scripts): validate label option values | `--add-label` and `--remove-label` now require a label name before reading the next positional arg; prevents `$2: unbound variable` aborts under `set -u`. |
| [#83993](https://github.com/anthropics/claude-code/pull/83993) | fix(scripts): reject self-referential duplicates | Prevents `comment-on-duplicates.sh` from posting a duplicate comment referencing the triggering issue itself. |
| [#83992](https://github.com/anthropics/claude-code/pull/83992) | fix(plugin-dev): assert expected hook decision | `test-hook.sh` gains `--expect allow|deny|ask` flag; previously both allow and deny were treated as success, masking hooks that failed to deny. |
| [#83990](https://github.com/anthropics/claude-code/pull/83990) | fix(plugin-dev): report missing jq dependency | `test-hook.sh` now checks for `jq` before use and reports a clear error instead of suppressing the shell failure and misreporting valid input as malformed JSON. |
| [#83890](https://github.com/anthropics/claude-code/pull/83890) | Create pylint.yml | Adds a Pylint configuration file for Python linting in the repo. |
| [#83374](https://github.com/anthropics/claude-code/pull/83374) | docs(plugin-dev): document MessageDisplay streaming semantics | Documents the previously undocumented `MessageDisplay` hook event in the bundled plugin-dev skill, including trigger description and quick-reference table. |
| [#83738](https://github.com/anthropics/claude-code/pull/83738) | Fix symlink path expansion | Resolves broken `claude` symlinks on Linux by expanding `%h` to the real home directory instead of writing a literal placeholder. Fixes #83484. |

## 5. Feature Request Trends

- **Multi-account / multi-connector support** — Issue #27302 (335 👍) is the dominant feature request, reflecting enterprise and power-user demand for per-account isolation within the same connector.
- **Configurable hook/output thresholds** — Issues #84022 and #84021 together show community frustration with the hardcoded 10K `persistHookOutput` limit; users want it configurable rather than simply raised.
- **Model persistence / lock** — Issue #84020 requests the ability to pin a user-selected model and prevent automatic switching (e.g., blocking fallback to Opus).
- **Cross-machine browser driving** — Issue #77605 calls for reliable device identification when driving a connected Chrome browser from a remote machine.
- **Skill portability via dotfiles** — Issue #84014 (closed) requested `additionalSkillDirs` in settings.json so skills can live in version-controlled dotfiles repos alongside config.

## 6. Developer Pain Points

1. **Windows MSIX stability** — Recurring GPU process crashes (#81275, #83130, #84023), update failures (#84005), and Cowork bridge drops (#83933, #82574) indicate the Windows desktop path has significant reliability gaps.
2. **Hook semantics are leaky** — PreToolUse hooks can be bypassed by background agents (#2) and internal workflow agents (#79953); PostToolUse context re-serialization invalidates prompt cache (#81077); hook output over 10K is silently dropped (#84021). These erode trust in the plugin system's boundaries.
3. **Memory and resource leaks** — The 15 GB RAM leak on WSL2 (#21378) and startup git origin access (#21108) are recurring resource concerns.
4. **Image and PDF tool bugs** — False "image couldn't be processed" errors consuming usage (#62466) and false "password-protected" reports on clean PDFs (#66563) both block common file-handling workflows.
5. **MCP connector gaps** — Personal Microsoft accounts rejected by M365 connector (#53408) and Notion auth failures (#84025) suggest MCP onboarding is uneven across providers.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-05

## 1. Today's Highlights

The Codex team shipped four rapid-fire alpha patches for the Rust CLI (v0.147.0-alpha.6.1 through alpha.7), signaling active stabilization work. On the desktop side, community pressure is mounting around a long-pending Linux app request (#11023, 917 👍) and a macOS CPU/memory runaway bug (#25719, 387 👍) tied to `syspolicyd`/`trustd` polling. Behind the scenes, a wave of ~20 merged PRs addresses skill caching, deferred custom tools, paginated thread support, and remote compaction for Amazon Bedrock.

## 2. Releases

**Rust CLI — v0.147.0-alpha.7** (and patch variants alpha.6.4, alpha.6.3, alpha.6.1)

Four alpha releases landed within the last 24 hours, suggesting iterative bug fixes between versions rather than a single feature drop. No detailed changelogs were provided in the source data.

- [GitHub Releases](https://github.com/openai/codex/releases)

## 3. Hot Issues

**#11023 — Codex desktop app for Linux** [OPEN, 199 comments, 917 👍]
The single most-upvoted open issue by a wide margin. Users on Linux are eager for a native desktop experience, especially as macOS app issues push affected users to alternative platforms. *(https://github.com/openai/codex/issues/11023)*

**#25719 — macOS `syspolicyd`/`trustd` CPU & memory runaway** [OPEN, 81 comments, 387 👍]
Codex Desktop on macOS is triggering persistent background daemon activity, causing significant resource drain. Multiple users reporting the same pattern makes this a high-priority stability concern. *(https://github.com/openai/codex/issues/25719)*

**#13041 — WebSocket upgrade succeeds then server closes with 1008 Policy** [CLOSED, 74 comments, 170 👍]
A connectivity issue where the WebSocket transport is immediately rejected by server policy, forcing a fallback to HTTPS. Closed, but the root cause and resolution remain important for users on restrictive networks (e.g., corporate proxies, Arch Linux). *(https://github.com/openai/codex/issues/13041)*

**#5999 — Weekly limit reset date changed unexpectedly** [CLOSED, 43 comments, 17 👍]
Users reported their weekly limit reset date shifting from Nov 3 to Nov 7 without notice. While closed, this highlights ongoing confusion around rate-limit scheduling for Plus/Pro subscribers. *(https://github.com/openai/codex/issues/5999)*

**#31846 — GPT-5.3 Codex Spark fails with "Unsupported parameter: reasoning.summary"** [CLOSED, 35 comments, 37 👍]
A model-compatibility bug where the app sends an unsupported `reasoning.summary` parameter to GPT-5.3 Codex Spark. Closed, likely fixed in a subsequent release. *(https://github.com/openai/codex/issues/31846)*

**#9926 — Interactive `ask_user_question` tool (tabbed questionnaire UI)** [CLOSED, 27 comments, 48 👍]
A feature request for structured Q&A where the agent asks constrained clarifying questions instead of free-form chat. Closed, suggesting it was implemented or deprioritized. *(https://github.com/openai/codex/issues/9926)*

**#25928 — VS Code/Cursor extension: submitted prompts randomly disappear** [OPEN, 23 comments, 16 👍]
Users report prompts vanishing from the extension queue before entering processing. Affects Cursor and VS Code on Windows, with significant workflow disruption. *(https://github.com/openai/codex/issues/25928)*

**#18299 — Display dot files and folders (.agents/.codex etc.)** [CLOSED, 14 comments, 33 👍]
The Codex App file viewer silently hides dotfiles, making it hard to inspect agent config and skill files. Closed — likely addressed in a UI update. *(https://github.com/openai/codex/issues/18299)*

**#31754 — Regression in codex-cli 0.143.0: Unknown parameter `input[...].namespace`** [OPEN, 14 comments, 8 👍]
A breaking regression between v0.142.0 and v0.143.0 where existing conversations fail with an unexpected parameter error. Active issue affecting CLI power users. *(https://github.com/openai/codex/issues/31754)*

**#36176 — Windows Desktop: PowerShell/WMI polling causes system-wide input lag** [OPEN, 7 comments, 3 👍]
Ongoing performance issue where the Windows app's background process polling degrades overall system responsiveness. Users report local patches can mitigate it. *(https://github.com/openai/codex/issues/36176)*

## 4. Key PR Progress

**#37000 — Keep shared skill caches fresh across plugin loads** [CLOSED]
Keys cached skill snapshots by filesystem and plugin snapshot identity, preventing stale data reuse across compatible config loads. Coalesces concurrent loads for the same key.

**#36998 — Support deferred custom tools in tool search** [CLOSED]
Freeform top-level tools are now included in the tool-search index with deferred loading. Serialized as Responses API `custom` tools and deserialized back into executable specs after discovery.

**#36993 — Support `includeTurns` reads for paginated threads** [CLOSED]
Reconstructs full projected turns from paginated history for both stored and remote threads, ensuring clients using `thread/read` with `includeTurns: true` get the legacy full-history view.

**#36992 — Allow injecting model catalog caches** [CLOSED]
Introduced a public async `ModelsCache` contract, letting model providers and `OpenAiModelsManager` accept caller-provided cache implementations while retaining the existing file-backed default.

**#36990 — Remove legacy collaboration mode variants** [CLOSED]
Deleted the hidden `PairProgramming` and `Execute` variants from `ModeKind`, along with unused prompt templates, simplifying mode handling to `Default` and `Plan` only.

**#36989 — Preserve shared bundled skill caches** [CLOSED]
Ensures that a service with bundled skills disabled does not remove cache files needed by other services sharing the same `CODEX_HOME`.

**#36987 — Add opt-in concurrent exec-server request dispatch** [CLOSED]
New `--concurrent-requests <COUNT>` flag for local and remote exec-server connections, preventing long-running requests from blocking unrelated health checks and cleanup.

**#36986 — Add process-scoped PSP routing for ChatGPT requests** [CLOSED]
Hidden global `--psp` runtime flag propagates through TUI, exec, app-server, remote-control, and in-process startup paths, attaching the `oai-chat-psp=true` cookie to first-party ChatGPT requests when enabled.

**#36983 — Preserve ChatGPT auth for trusted staging MCP servers** [CLOSED]
MCP servers matching the configured HTTPS `chatgpt-staging.com` host or subdomains are now treated as trusted for ChatGPT authentication, with production origin continued as fallback.

**#36981 — Enable remote compaction for Amazon Bedrock** [CLOSED]
Added provider-owned remote compaction capabilities for v1 and v2 protocols. Bedrock is marked v1-only so both manual and automatic compaction use `/v1/responses/compact`.

## 5. Feature Request Trends

- **Cross-platform desktop parity** — The dominant theme. Linux support (#11023) is the most-voted request; Windows performance issues (#36176, #31762, #33288) and macOS resource bugs (#25719) indicate platform gaps are the #1 community concern.
- **Structured agent-user interaction** — The `ask_user_question` tool (#9926) and dotfile visibility (#18299) reflect demand for more intentional, UI-driven agent workflows rather than pure chat.
- **Extensibility & customization** — Disabling auto-updates (#18546), configurable token-budget identity (#36970), and deferred custom tool search (#36998) show users want deeper control over agent behavior and tool discovery.
- **Multi-platform auth & session continuity** — Remote SSH approval bugs (#34652), session import preserving working directories (#36964), and auth token override issues (#15151) highlight the need for consistent identity across environments.

## 6. Developer Pain Points

1. **Platform instability** — Windows and macOS desktop issues dominate open issues: CPU runaway (#25719), input lag from polling (#36176), unresponsive approval buttons in remote SSH (#34652), and task-creation timeouts (#31762, #33288). Linux users are locked out entirely (#11023).
2. **CLI regressions** — The v0.143.0 regression on `input[...].namespace` (#31754) and the `OPENAI_API_KEY` silently overriding OAuth (#15151) show that breaking changes and auth precedence bugs reach users before stabilization.
3. **IDE extension reliability** — Prompts disappearing from the Cursor/VS Code queue (#25928) and RPC serialization errors breaking IDE context (#34920) undermine the primary developer workflow for extension users.
4. **Model compatibility drift** — The `reasoning.summary` parameter error on GPT-5.3 Codex Spark (#31846) and the memory writer hardcoding `gpt-5.6-luna`/`gpt-5.6-terra` for non-OpenAI providers (#37009) indicate the toolchain struggles to keep pace with model-specific API changes.
5. **Rate-limit opacity** — Unexpected reset-date shifts (#5999) continue to frustrate Plus/Pro users who rely on predictable weekly quotas.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-05

## 1. Today's Highlights

Security remains the top priority this cycle, with three critical fixes landed: an SSRF vulnerability in `web-fetch.ts` resolved via async DNS resolution (#28557), a bash variable-expansion bypass patched (#28691), and full MCP server config reflection in consent dialogs (#28664). On the agent side, community discussion is intensifying around subagent reliability—particularly generalist-agent hangs (#21409, 8 👍) and incorrect `GOAL` termination reporting after `MAX_TURNS` (#22323).

---

## 2. Releases

No new releases in the past 24 hours.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | Misreported termination hides real failures, causing the orchestrator to believe analysis completed when it hit the turn limit silently. | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | A P1 bug where any task deferred to the generalist agent stalls indefinitely; users report waiting up to an hour. Disabling sub-agents is the only known workaround. | 8 comments · **8 👍** |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution stuck "Waiting input" | Simple CLI commands complete but the CLI retains the command as active, blocking further interaction. | 4 comments · 3 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | Users with well-defined custom skills (e.g., `gradle`, `git`) report the model ignores them unless explicitly instructed—undermining the skill system's value. | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Stop Auto Memory from retrying low-signal sessions | Sessions the extraction agent deems low-signal remain unprocessed and get re-surfaced indefinitely, creating noise in the memory index. | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction & reduce Auto Memory logging | Current redaction happens *after* content enters model context; a pre-transmission deterministic redaction pass is needed for security. | 4 comments |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent ignores settings.json overrides | Config like `maxTurns` set in `settings.json` is silently ignored by the browser agent, causing unexpected behavior in persistent-session mode. | 3 comments |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | P1 bug specific to Wayland displays; the browser agent terminates with `GOAL` without performing any work. | 4 comments · 1 👍 |
| [#24246](https://github.com/google-gemini/gemini-cli/issues/24246) | 400 error with >128 tools | The agent hits a 400 when more than ~128 tools are in scope; users expect smarter tool-limiting rather than a hard failure. | 3 comments |
| [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) | Subagents running without permission since v0.33.0 | Regression: subagents activate despite being disabled in all configs, breaking the expected MCP-only usage pattern. | 3 comments |

---

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#28691](https://github.com/google-gemini/gemini-cli/pull/28691) | Block `$VAR` / `${VAR}` expansion bypass | Fixes incomplete checks in `detectBashSubstitution()` and `detectPowerShellSubstitution()` that allowed variable expansion to bypass the security gate (GHSA-wpqr-6v78-jr5g). Defense-in-depth hardening included. |
| [#28557](https://github.com/google-gemini/gemini-cli/pull/28557) | SSRF fix via async DNS resolution | `isBlockedHost` previously called synchronous `isPrivateIp()`, which only flagged literal IPs. Domain names now resolve asynchronously, blocking hostnames pointing to internal ranges like `169.254.169.254`. |
| [#28597](https://github.com/google-gemini/gemini-cli/pull/28597) | Load env vars before resolving settings placeholders | Fixes a load-order race condition where `.env` values weren't available when settings files were parsed, causing placeholder expansion failures at startup. |
| [#28672](https://github.com/google-gemini/gemini-cli/pull/28672) | Repair `/compress` session reload & quota-fallback response loss | Two fixes: `/compress` no longer fails with "Failed to load resumed session data," and quota-limit fallbacks no longer silently drop tool responses. |
| [#28671](https://github.com/google-gemini/gemini-cli/pull/28671) | Resolve context corruption & quota error fallback | Addresses context corruption and model "autocomplete" prefix-continuation behavior when tool executions are interrupted or hit quota fallbacks. |
| [#28688](https://github.com/google-gemini/gemini-cli/pull/28688) | Dynamic Cloud Workstations OAuth redirect URI | OAuth flows in Cloud Workstations VMs now dynamically resolve the correct redirect URI instead of hardcoding `localhost`, which failed because the browser runs on the developer's machine. |
| [#28664](https://github.com/google-gemini/gemini-cli/pull/28664) | Full MCP server config in consent + stdio hardening | Consent prompts now show `env`, `cwd`, and `headers` fields (previously hidden), and stdio environment is hardened against leakage. |
| [#28641](https://github.com/google-gemini/gemini-cli/pull/28641) | Fix ghost-text infinite loop at narrow widths | Forces advancement of `splitIndex` in `getGhostTextLines` when `inputWidth` is narrower than a single wide codepoint (CJK/emoji), fixing hang reported in #19985. |
| [#28681](https://github.com/google-gemini/gemini-cli/pull/28681) | SGLang & local OpenAI-compatible endpoint support | Adds support for SGLang and other local OpenAI-compatible inference endpoints, expanding deployment flexibility beyond Google-hosted models. |
| [#28530](https://github.com/google-gemini/gemini-cli/pull/28530) | Caretaker Agent triage evaluation framework | Introduces an LLM-as-a-Judge rubric and parallel Git Worktree benchmark runner for evaluating the Caretaker Agent's issue-triage pipeline under `tools/caretaker-agent/evals/triage/`. |

---

## 5. Feature Request Trends

- **Agent reliability & observability** — The largest cluster of requests: subagent recovery (#22323), better skill/subagent utilization (#21968), subagent trajectory visibility via `/chat share` (#22598), and bug report context for subagents (#21763).
- **AST-aware codebase tools** — Two linked epics (#22745, #22746) explore whether AST-aware file reads, search, and codebase mapping (using tools like tilth or glyph) would reduce turn count and token noise.
- **Zero-dependency OS sandboxing** — #19873 proposes leveraging the model's native bash affinity through sandboxed execution, letting the model chain POSIX tools safely without extra dependencies.
- **Browser agent resilience** — #22232 requests automatic session takeover and lock recovery; #22267 highlights config override bugs. The community wants the browser agent to be production-ready on Linux/Wayland.
- **Auto Memory hardening** — Three issues (#26522, #26525, #26523) from the same author push for deterministic redaction, low-signal session quarantine, and invalid patch visibility—signaling that Auto Memory is maturing but needs guardrails.

---

## 6. Developer Pain Points

1. **Subagent reliability** — Generalist agent hangs (#21409, 8 👍), incorrect `GOAL` reporting after `MAX_TURNS` (#22323), and subagents running without permission since v0.33.0 (#22093) form a pattern: the subagent system is powerful but unpredictable.
2. **Auto Memory quality loops** — Low-signal sessions retried indefinitely (#26522), invalid patches silently skipped (#26523), and insufficient redaction (#26525) suggest the memory system needs stricter validation and quarantining.
3. **Browser agent platform gaps** — Wayland failures (#21983) and `settings.json` being ignored (#22267) indicate the browser agent isn't yet robust across Linux desktop environments.
4. **Shell execution hangs** — Commands completing but the CLI remaining stuck in "Awaiting user input" (#25166, 3 👍) directly blocks developer workflows.
5. **Tool quantity limits** — The 400 error past ~128 tools (#24246) forces users to manually curate tool scope rather than relying on the agent to self-limit.
6. **Context corruption on interruptions** — Quota fallbacks and user ESC queries can corrupt conversation context (#28671, #28672), making recovery difficult and losing tool output silently.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-05

## 1. Today's Highlights

GitHub Copilot CLI **v1.0.79-1** was released with a breaking change: the `allowDevToolCaches` sandbox setting has been renamed to `allowDevToolAccess` to accurately reflect its expanded scope. A new regression was reported where `/plugin-skill-name` slash commands no longer route correctly, and multiple enterprise/MCP configuration issues surfaced around TLS validation and managed-policy schema enforcement.

## 2. Releases

**v1.0.79-1** — [GitHub Copilot CLI Releases](https://github.com/github/copilot-cli/releases)

- **BREAKING CHANGE:** The sandbox setting `allowDevToolCaches` is renamed to `allowDevToolAccess`. The old key is silently ignored, meaning an existing `false` opt-out reverts to the default (`on`). Users should rename the key in their settings. The change broadens the setting's scope to cover dev-tool config and registries, not just caches.

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#1504](https://github.com/github/copilot-cli/issues/1504) | Add custom theme support | Enables full UI personalization and shareable themes — a widely requested accessibility and DX improvement. | 23 👍 · 8 comments |
| [#1697](https://github.com/github/copilot-cli/issues/1697) | Session forking | Allows branching a conversation into parallel sessions with shared context — critical for multi-track workflows. | 25 👍 · 3 comments |
| [#2019](https://github.com/github/copilot-cli/issues/2019) | Command to delete session | Users need session management primitives (delete/clean) alongside the existing `/resume`. | 13 👍 · 2 comments |
| [#1709](https://github.com/github/copilot-cli/issues/1709) | Auto-updating plugins | Manual per-plugin updates are a growing pain as the plugin ecosystem expands. | 29 👍 · 1 comment |
| [#4370](https://github.com/github/copilot-cli/issues/4370) | MCP init fails when `server/discover` returns `-32602` | New regression in v1.0.79-1 breaking FastMCP server compatibility. | 0 👍 · 1 comment |
| [#4364](https://github.com/github/copilot-cli/issues/4364) | Enterprise MCP registry unreachable on macOS (rustls / Apple -67901) | Private-CA MCP registries are fail-closed, blocking all MCP tools for enterprise macOS users. | 0 👍 · 1 comment |
| [#4349](https://github.com/github/copilot-cli/issues/4349) | Managed settings policy rejects `"enable"` enum for `disableBypassPermissionsMode` | Schema validator is too strict, blocking all local/custom MCP servers in enterprise environments. | 0 👍 · 1 comment |
| [#4361](https://github.com/github/copilot-cli/issues/4361) | Slash commands for plugin skills no longer work (regression) | Clients rewrite `/skill-name` to natural language; the new behavior invokes a doomed RPC instead. | 0 👍 · 1 comment |
| [#4005](https://github.com/github/copilot-cli/issues/4005) | Copilot billing entity not selected — can't save memories | Enterprise users report a regression blocking memory persistence despite everything else working. | 3 👍 · 4 comments |
| [#4196](https://github.com/github/copilot-cli/issues/4196) | BYOK completions wire API fails with `reasoning_content` in streaming | BYOK providers emitting `reasoning_content` in deltas trigger 5 retries and then hard-fail. | 0 👍 · 2 comments |

## 4. Key PR Progress

| # | Title | Status |
|---|-------|--------|
| [#4355](https://github.com/github/copilot-cli/pull/4355) | Merge | Open — details not yet populated. |
| [#4366](https://github.com/github/copilot-cli/pull/4366) | ACTION REQUIRED: Fundamental security findings resolution for copilot-cli | Open — addresses Vault security findings in `ci, production`. Review required before merge. |

## 5. Feature Request Trends

- **Custom theming & accessibility** — [#1504](https://github.com/github/copilot-cli/issues/1504) and [#3898](https://github.com/github/copilot-cli/issues/3898) both highlight the need for deeper UI customization and proper color/OSC handling.
- **Session management & persistence** — Multiple requests for cloud-synced sessions [#1947](https://github.com/github/copilot-cli/issues/1947), session forking [#1697](https://github.com/github/copilot-cli/issues/1697), session deletion [#2019](https://github.com/github/copilot-cli/issues/2019), and remote heartbeat reporting [#1343](https://github.com/github/copilot-cli/issues/1343) signal strong demand for cross-device and lifecycle session controls.
- **BYOK / custom model support** — [#4139](https://github.com/github/copilot-cli/issues/4139) requests bringing your own LLM endpoints (analogous to Claude CLI's Google Cloud AI support).
- **Plugin auto-updates** — [#1709](https://github.com/github/copilot-cli/issues/1709) remains the top-voted plugin infrastructure request.
- **Persistent context bar** — [#2532](https://github.com/github/copilot-cli/issues/2532) asks for a always-visible token/usage indicator.

## 6. Developer Pain Points

- **MCP reliability under v1.0.79-1:** The `server/discover` method is now mandatory and any non-zero error code (including `-32602 Invalid request parameters` from FastMCP) is treated as a fatal failure, silently dropping all MCP servers [#4370](https://github.com/github/copilot-cli/issues/4370).
- **Enterprise policy schema strictness:** The managed-settings validator rejects valid enum values (`"enable"` for `disableBypassPermissionsMode`), causing all local/custom MCP servers to fail-closed [#4349](https://github.com/github/copilot-cli/issues/4349).
- **macOS TLS / private CA rejections:** Apple's strict `rustls` validation rejects private-CA certificates with error `-67901`, breaking enterprise MCP registries on macOS [#4364](https://github.com/github/copilot-cli/issues/4364).
- **Plugin slash-command regression:** Plugin-provided skills invoked via `/skill-name` no longer work; the client now emits an RPC that fails instead of rewriting to natural language [#4361](https://github.com/github/copilot-cli/issues/4361).
- **BYOK streaming incompatibility:** Models that include `reasoning_content` in streaming deltas cause hard failures after 5 retries instead of being handled gracefully [#4196](https://github.com/github/copilot-cli/issues/4196).
- **WSL2 keyboard binding leak:** `Ctrl+H` is misinterpreted as `Ctrl+Backspace` when `WT_SESSION` leaks from Windows Terminal into WSL2 [#4328](https://github.com/github/copilot-cli/issues/4328).
- **Enterprise billing-entity regression:** Users can no longer save memories due to a missing billing-entity selection, despite other enterprise features working normally [#4005](https://github.com/github/copilot-cli/issues/4005).
- **Session state loss on switch:** Stashed (`Ctrl+S`) prompts are discarded when switching sessions, with no restore path on return [#4334](https://github.com/github/copilot-cli/issues/4334).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI Community Digest — 2026-08-05

## 1. Today's Highlights

Two new bug reports surfaced today: a crash during normal session progression on Windows (v0.29.2 / K3 high) and an IME-related character duplication bug affecting Thai and other input methods on Windows. The community continues to push for long-term architectural improvements, notably persistent memory across sessions and remote session control, while an agent reliability issue at high context fill (~500K tokens) has been flagged for investigation.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**[#1282] Remote Control — Continue local sessions from any device** · 👍 24 · 12 comments
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)

One of the most upvoted enhancement requests. Users want to step away from their desk while keeping their full local environment intact and continue the session from a phone, tablet, or browser. Strong community interest signals demand for workflow continuity.

**[#1283] Memory System — Persistent context across sessions** · 👍 0 · 17 comments
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1283)

A comprehensive memory feature proposal covering both AI-managed automatic notes and user-defined manual instructions. High comment count indicates active community discussion, though no upvotes yet — a foundational feature many users are waiting for.

**[#2586] Agent reliability degrades at high context fill (~500K tokens)** · CLOSED · 1 comment
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2586)

Critical finding: agentic sessions orchestrating multi-step code changes show sharp reliability drops — repetitive loops, no escalation, instruction drift — once context passes roughly 500K tokens. Reports suggest this is an operator-observed threshold, not a documented limit. Important for users running long-running agent workflows.

**[#2587] CLI exits abnormally during normal session progression** · OPEN · 0 comments
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2587)

Bug reported on Windows (v0.29.2, K3 high model). The CLI crashes mid-session without apparent error, disrupting workflow. Affects core stability.

**[#2584] Thai and IME-based characters duplicated on Windows** · OPEN · 0 comments
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2584)

Users typing Thai or other IME-based languages on Windows see characters duplicated in the prompt. Impacts international users and highlights a recurring input-handling gap on Windows.

**[#2583] feat(acp): advertise available models and support mid-session model switching** · OPEN · 0 comments
> [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/2583)

ACP clients (e.g., Happy Coder mobile app, Zed) cannot discover available models or switch mid-session. This limits programmable control and is a blocker for ACP integrations.

---

## 4. Key PR Progress

**[#2200] fix(shell): adapt timeouts for long commands**
Extends shell timeout automatically for slow command patterns (git submodule cleanup, clone/fetch, package installs, builds) while preserving the 60s default for normal commands and respecting explicit caller-supplied timeouts. Addresses a common frustration with long-running operations being prematurely killed.

**[#2585] feat(cli): set AI_AGENT for subprocesses**
Exposes `AI_AGENT=kimi` to all subprocesses launched from both pip/uv and standalone binary entrypoints, preserving explicit values from wrappers. Enables orchestrators to detect when commands are running under Kimi Code CLI.

**[#2364] feat(acp): support permission mode switching**
Adds protocol-level ACP permission mode switching for Kimi sessions, advertising default modes. Stacks on top of #2363 and resolves related Issue #1414. Expands ACP client control over agent behavior.

---

## 5. Feature Request Trends

- **Persistent Memory** — The most discussed architectural enhancement. Users want the CLI to retain project patterns, preferences, and context across sessions, reducing repetitive onboarding.
- **Remote / Cross-Device Access** — Strong signal (24 👍) for continuing local sessions from any device, reflecting a desire for seamless workflow continuity beyond the desk.
- **ACP Ecosystem Maturity** — Multiple requests center on improving the ACP protocol: model discovery, mid-session switching, and permission mode control. These are prerequisites for rich third-party integrations (mobile apps, IDEs).
- **Reliability at Scale** — Implicit but growing demand for robust long-context agent behavior, as evidenced by the 500K-token reliability degradation report.

---

## 6. Developer Pain Points

- **Windows stability and input bugs** — Two Windows-specific issues reported today (session crash, IME character duplication). The Windows experience remains a friction point compared to other platforms.
- **Long-running agent sessions** — Context fill beyond ~500K tokens triggers unreliability (repetition, drift, no escalation). Users running complex multi-step agent workflows hit a hard, undocumented ceiling.
- **Shell timeout rigidity** — Long commands (git operations, builds, package installs) are frequently killed by default timeouts, prompting the timeout-adaptation PR.
- **ACP client limitations** — Third-party ACP clients lack model discovery and mid-session switching, constraining integration depth and user control.
- **Lack of session persistence** — No built-in memory or remote access means users must re-establish context manually each session, a recurring top-of-mind request.

---

*Digest generated from [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) data as of 2026-08-05.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026‑08‑05

## 1. Today’s Highlights
OpenCode v1.18.13 ships with TUI context‑improvement and desktop RTL‑layout fixes. The community is actively tracking subagent reliability and billing‑engine bugs, while several high‑impact PRs advance compaction fidelity, subagent interruption, and OAuth hardening.

## 2. Releases
**v1.18.13**  
- **TUI:** GitHub pull‑request reviews now include the PR number and URL in context.  
- **Desktop:** Resolved multiple right‑to‑left layout issues across tabs, drawers, resizing, and titlebar interactions; unified directional icon behavior.

## 3. Hot Issues
1. **[CLOSED] #27593** – 402 Insufficient Balance with ds4‑flash despite session usage & spend quota. *(17 comments, 13 👍)*  
   Highlights billing‑model mismatch that blocks subscribed users on specific models.  
   <https://github.com/anomalyco/opencode/issues/27593>

2. **[CLOSED] #30862** – App stuck after update; no response/output despite session title changing. *(12 comments, 1 👍)*  
   Critical hang reported on both GUI and CLI reinstallations.  
   <https://github.com/anomalyco/opencode/issues/30862>

3. **[CLOSED] #20234** – WSL outputs only one word per line during thinking. *(10 comments, 4 👍)*  
   Cross‑platform rendering bug affecting terminal‑based thinking streams.  
   <https://github.com/anomalyco/opencode/issues/20234>

4. **[CLOSED] #20118** – Failed to run `PRAGMA journal_mode = WAL` after version downgrade. *(10 comments, 11 👍)*  
   Database‑migration error with poor error‑handling feedback.  
   <https://github.com/anomalyco/opencode/issues/20118>

5. **[OPEN] #33028** – Subagents hang indefinitely after quick bash tool call; stream never times out. *(9 comments, 6 👍)*  
   Open reliability issue impacting multi‑agent workflows with `glm‑5.2` and `minimax‑m3`.  
   <https://github.com/anomalyco/opencode/issues/33028>

6. **[CLOSED] #22233** – Feature request for improved subagent runtime visibility in chat UI. *(7 comments, 0 👍)*  
   Users cannot identify which agent is running, its state, or duration.  
   <https://github.com/anomalyco/opencode/issues/22233>

7. **[CLOSED] #17425** – Plugin extensibility gaps block dictation/voice‑input plugins. *(7 comments, 0 👍)*  
   High‑demand feature (#4695, #9264, #11345) hindered by plugin‑architecture limits.  
   <https://github.com/anomalyco/opencode/issues/17425>

8. **[CLOSED] #29626** – Feature request for agent presets. *(7 comments, 0 👍)*  
   Subagents are left unconfigured because per‑project setup is repetitive.  
   <https://github.com/anomalyco/opencode/issues/29626>

9. **[CLOSED] #29951** – Advanced‑settings toggles for desktop toolbar buttons have no effect in new layout. *(6 comments, 4 👍)*  
   Bug in `newLayoutDesigns` that disables File tree, Command palette, Terminal, and Server‑status toggles.  
   <https://github.com/anomalyco/opencode/issues/29951>

10. **[CLOSED] #30951** – Zen lists `nemotron‑3‑ultra‑free` but requests fail as unsupported. *(5 comments, 0 👍)*  
    Model‑catalog mismatch between the displayed catalog and the live Zen backend.  
    <https://github.com/anomalyco/opencode/issues/30951>

## 4. Key PR Progress
1. **#40566** – `feat(core): preserve compaction tail images`  
   Raises default retained compaction context from 8K to 15K tokens and preserves selected user/tool‑result images in the retained tail.  
   <https://github.com/anomalyco/opencode/pull/40566>

2. **#32425** – `feat(opencode): interrupt a running subagent — steer / cancel / abort`  
   Closes #38966; adds subagent‑control primitives (steer, cancel, abort) to address stuck‑session recovery.  
   <https://github.com/anomalyco/opencode/pull/32425>

3. **#40538** – `fix(core): make xAI OAuth device‑only`  
   Replaces loopback OAuth with RFC 8628 device authentication; exposes a single SuperGrok subscription method for local and remote use.  
   <https://github.com/anomalyco/opencode/pull/40538>

4. **#40561** – `chore: sync upstream‑20260805`  
   Upstream sync: 205 new refs, 20+ commits ahead of origin/dev.  
   <https://github.com/anomalyco/opencode/pull/40561>

5. **#33127** – `feat(tui): add sidebar history and scroll‑to‑message support`  
   Adds a History sidebar panel listing user messages with click‑to‑scroll navigation.  
   <https://github.com/anomalyco/opencode/pull/33127>

6. **#40126** – `feat(session): support Gemini image generation`  
   Carries Gemini inline image data through the session pipeline.  
   <https://github.com/anomalyco/opencode/pull/40126>

7. **#40556** – `test(app): harden flaky e2e synchronization`  
   Replaces timing‑sensitive review interactions with Playwright readiness assertions and FIFO‑sentinel heartbeat consumption.  
   <https://github.com/anomalyco/opencode/pull/40556>

8. **#40450** – `fix(opencode): include cache writes in ACP usage`  
   Ensures cache‑write tokens are reported in ACP context usage across both service paths.  
   <https://github.com/anomalyco/opencode/pull/40450>

9. **#40541** – `fix(llm): parse cache_creation_tokens from OpenAI‑compat usage`  
   Fixes a regression where OpenAI‑compatible proxies (e.g., LiteLLM) reported zero cache‑write tokens.  
   <https://github.com/anomalyco/opencode/pull/40541>

10. **#40558** – `fix(core): unify patch path resolution`  
    Adopts the shared `LocationMutation` path‑planning contract for patches, aligning authorization and canonical‑path behavior with edit/write.  
    <https://github.com/anomalyco/opencode/pull/40558>

## 5. Feature Request Trends
- **Subagent control & visibility** – Requests for steering/cancel/abort (#32425) and better runtime status in the UI (#22233) reflect a need for finer‑grained multi‑agent orchestration.
- **Plugin‑system extensibility** – Voice/ dictation input (#17425, #18226) and other plugins are blocked by current architectural gaps; the community wants a more open plugin interface.
- **Configuration reuse** – Agent presets (#29626) and auto‑attach to remote servers (#17322) aim to reduce repetitive setup across projects.
- **Terminal & editing UX** – Voice input (#18226), improved tab navigation (#40551), and reliable session switching (#37832) show ongoing demand for smoother desktop/TUI workflows.

## 6. Developer Pain Points
- **Reliability & hangs** – Subagent hangs (#33028), app freezes after dialogs (#30590), and crash on session‑switch (#37832) disrupt daily development.
- **Billing & model‑catalog mismatches** – “Insufficient balance” errors despite available quota (#27593, #30950) and missing models in Zen (#30951) cause subscription confusion.
- **Cross‑platform quirks** – WSL one‑word‑per‑line thinking output (#20234), terminal raw‑mode not restored after abort (#30920), and desktop RTL layout bugs (#18, #19 in release) require platform‑specific attention.
- **Tool‑call & schema handling** – Zod internal‑property leaks into JSON Schema (#28704) and malformed Responses tool‑call classification (#40549) lead to provider errors.
- **Operational overhead** – Manual server‑attach (#17322), missing shell‑workdir errors (#40542), and legacy‑provider cleanup (#40487) increase friction for advanced workflows.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-05

---

## 1. Today's Highlights

Compaction remains the dominant topic, with multiple interconnected issues around Copilot Enterprise 421 errors and configurable summarization models now addressed in PRs. The project continues broadening its provider ecosystem with new Cortecs and LLM Gateway integrations, while Mermaid diagram rendering lands in the coding agent.

---

## 2. Releases

No new releases in the last 24 hours.

---

## 3. Hot Issues

**1. Compaction with Copilot Enterprise fails (421 / unknown stamp)** [#6768](https://github.com/earendil-works/pi/issues/6768) · [#7413](https://github.com/earendil-works/pi/issues/7413) · [#7579](https://github.com/earendil-works/pi/issues/7579)
Three related compaction bugs, all closed, all rooted in the same theme: enterprise Copilot/GHE routes drop or misdirect the summarization request (421 Misdirected Request, invalid token, unknown stamp). 19 comments, 18 👍 on the flagship issue. High community impact — compaction is essential for long sessions.

**2. Windows Pi usability survey** [#7547](https://github.com/earendil-works/pi/issues/7547)
Open discussion on how developers run Pi on Windows and which codepaths deserve core investment. 13 comments — a signal that Windows support is a persistent friction point the team wants to triage systematically.

**3. Terminal auto-scrolls to top during model output** [#5023](https://github.com/earendil-works/pi/issues/5023)
Random jumps to the beginning of the session buffer, happening while the model is generating. 11 comments, closed. A long-standing UX bug that disrupts the reading flow.

**4. Anthropic `x-client-request-id` not sent** [#7161](https://github.com/earendil-works/pi/issues/7161)
The `anthropic-messages` path omits the header entirely, breaking session affinity on gateways that key off it (e.g. round-robin proxy setups). 10 comments, closed. Important for anyone routing through a proxy layer.

**5. OAuth refresh stalls freeze the session** [#7508](https://github.com/earendil-works/pi/issues/7508)
A stalled token refresh for GitHub Copilot / OpenAI Codex acquires the credential-store lock with no timeout, freezing the entire session for ~5 minutes. 5 comments, closed. High pain for users on flaky or proxied networks.

**6. Configurable thinking level for compaction** [#7553](https://github.com/earendil-works/pi/issues/7553)
Compaction unconditionally reuses the session's thinking level, making it impossible to give summarization a smaller budget on reasoning models. 6 comments, closed — addressed by PR #7602.

**7. iTerm2 inline images missing size param** [#7465](https://github.com/earendil-works/pi/issues/7465)
`@xterm/addon-image@0.9.0` silently rejects images without a `size` parameter. 7 comments, open. Blocks image rendering in xterm.js-based terminals.

**8. `find` tool fails on Windows path patterns** [#6817](https://github.com/earendil-works/pi/issues/6817)
Patterns containing path separators like `src/**/*.ts` return no results on Windows. 5 comments, open. Affects Windows users relying on glob-based file search.

**9. Fullscreen keybindings consumed by transcript** [#7574](https://github.com/earendil-works/pi/issues/7574)
Home/End/PageUp/PageDown are swallowed by the transcript viewport even when the editor is focused. 4 comments, closed.

**10. `node:sqlite` missing in release binary** [#7594](https://github.com/earendil-works/pi/issues/7594)
Extensions like `pi-total-recall` fail to load because the release binary ships without the `node:sqlite` built-in. 4 comments, closed.

---

## 4. Key PR Progress

**1. Render Mermaid diagrams in markdown** [#7624](https://github.com/earendil-works/pi/pull/7624) — *OPEN*
Closes #7623. Uses the `grok-mermaid` library to render Mermaid diagrams inline. Responds to community demand for better visualization in the TUI.

**2. Configurable summarization models and thinking levels** [#7602](https://github.com/earendil-works/pi/pull/7602) — *OPEN*
Closes #7553. Lets users configure both the model and thinking level used for compaction and branch summaries. Provider errors during compaction now handle context-window limits gracefully.

**3. Resume failed turns from `/tree`** [#7619](https://github.com/earendil-works/pi/pull/7619) — *OPEN*
Selecting an assistant entry that ended in an error (e.g. dropped connection) now retries the turn in-place rather than landing on a dead end. Closes #7609.

**4. Fix transient management HTTP request retries** [#7632](https://github.com/earendil-works/pi/pull/7632) — *OPEN*
Retries all idempotent management requests (pi.dev, GitHub releases, tools). Fixes #6675. No per-attempt timeout to avoid slowing slower networks.

**5. Add Cortecs provider** [#7571](https://github.com/earendil-works/pi/pull/7571) — *CLOSED*
Adds [Cortecs](https://cortecs.ai), a European AI provider/router, backed by models.dev. Expands the provider ecosystem for EU-based users.

**6. Add LLM Gateway providers** [#7610](https://github.com/earendil-works/pi/pull/7610) — *OPEN*
Adds [LLM Gateway](https://llmgateway.io) as built-in `openai-completions` providers. Replaces auto-closed #7480. Contributes an OpenRouter-style router option.

**7. Add size param to iTerm2 image encoder** [#7612](https://github.com/earendil-works/pi/pull/7612) — *OPEN*
Includes decoded byte count in OSC 1337 sequences, satisfying `@xterm/addon-image@0.9.0`. Directly addresses #7465.

**8. Expose argument completions via RPC** [#7621](https://github.com/earendil-works/pi/pull/7621) — *CLOSED*
New `get_argument_completions` RPC command enables embedded clients (e.g. web UIs) to surface slash-command subcommand completions.

**9. Server session backend with JSONL persistence** [#7396](https://github.com/earendil-works/pi/pull/7396) — *CLOSED*
Adds a durable `@earendil-works/pi-coding-agent/server` backend with exclusive cross-process locking, crash recovery, and project harness event projection. Foundational for multi-process deployments.

**10. Remove legacy server implementation** [#7614](https://github.com/earendil-works/pi/pull/7614) — *CLOSED*
Strips the experimental legacy child-process server, the `server` executable, and the `@earendil-works/pi-server/legacy` export. Cleans up the build tree now that the new backend (#7396) is in place.

---

## 5. Feature Request Trends

- **Compaction customization** — Users want independent control over the model, thinking level, and provider used for summarization (not just the session defaults).
- **Provider diversity** — Continued demand for more built-in providers (Cortecs, LLM Gateway, Qwen Token Plan Individual) and better proxy/gateway compatibility (session affinity headers, OAuth flexibility).
- **Terminal UX polish** — Image rendering in xterm.js, Mermaid diagram support, fullscreen keybinding fixes, and scroll-behavior improvements are recurring asks.
- **Windows parity** — Multiple Windows-specific issues (path patterns in `find`, skill-loading crashes, sink-thread confusion) signal a sustained need for Windows-first investment.
- **RPC and embeddability** — Exposing auth flows, argument completions, and durable session backends via RPC points to growing interest in embedding Pi in external tools and web UIs.

---

## 6. Developer Pain Points

- **Compaction is fragile on enterprise routes.** The 421 / "unknown stamp" errors on Copilot Enterprise seats are the highest-friction issue this cycle, affecting a power-user segment.
- **OAuth refresh deadlocks.** A stalled token refresh acquires a cross-process lock with no timeout, freezing the entire session for minutes. Users on corporate proxies or flaky connections hit this repeatedly.
- **Windows path handling is inconsistent.** The `find` tool and `loadSkills` both break on Windows-specific path conventions, suggesting the codebase still treats Windows as secondary.
- **JSON serialization overhead in `--mode json`.** Cumulative assistant state is re-serialized on every delta, causing quadratic output growth — a performance bug that scales badly with session length.
- **Error state is sticky.** Successful retries leave red error lines in the chat, and `validateToolArguments()` silently coerces `null` values in nullable unions, both degrading trust in the output.
- **Extension runtime gaps.** Missing `node:sqlite` in release binaries and vulnerable pinned dependencies (`undici@8.5.0`, `brace-expansion@5.0.7`) in the shrinkwrap show that the packaging pipeline needs tighter QA.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-05

## 1. Today's Highlights

Qwen Code released preview build **v0.21.6-preview.0** and a daily nightly, both carrying PR #6739 (alpha readiness diagnostics for the browser extension) and documentation for headless Goal workflows. On the issue front, a high-priority trustworthiness proposal (#8102) and a foundational reasoning-replay contract problem (#8533) are driving community discussion around runtime safety and provider compatibility.

---

## 2. Releases

### v0.21.6-preview.0
- **PR #6739** — `feat(browser-ext): add alpha readiness diagnostics` (@yiliang114)
- **Docs** — Documented headless Goal workflows (@DragonnZhang)

### v0.21.5-nightly.20260805.32e274157
- Same changes as above (nightly carry-forward)

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#8102](https://github.com/QwenLM/qwen-code/issues/8102) | Deterministic tool-execution boundaries for a trustworthy agent runtime | Proposes keeping the LLM outside the trust boundary and making the runtime able to **constrain, authorize, observe, and evaluate** model actions. 17 comments signal strong community interest in agent safety. |
| [#8519](https://github.com/QwenLM/qwen-code/issues/8519) | Severe screen flickering in tmux | P2 UX bug causing flicker ~1–2×/sec inside tmux. Closed but indicates ongoing terminal-rendering friction. |
| [#8051](https://github.com/QwenLM/qwen-code/issues/8051) | Bound multi-workspace daemon resource usage | Count-only workspace/session limits don't bound **bytes** from request bodies, WebSocket assembly, etc. Critical for production `qwen serve` deployments. |
| [#8136](https://github.com/QwenLM/qwen-code/issues/8136) | Provider warning sanitizer leaks passwords containing `@` | `sanitizeProviderWarningSegment` misidentifies user info in URLs with ports, leaking credentials in `/status` payloads. Security-relevant P2. |
| [#8532](https://github.com/QwenLM/qwen-code/issues/8532) | CI logs confuse mocked disk-full errors with real ENOSPC | Unit tests deliberately throwing `new Error('disk full')` produce production-looking stderr that masks real CI issues. |
| [#8356](https://github.com/QwenLM/qwen-code/issues/8356) | After `APIUserAbortError`, subsequent turns aren't written to session transcript | Session persistence gap after user abort — conversation history silently drops turns. |
| [#8550](https://github.com/QwenLM/qwen-code/issues/8550) | `qwen mcp list` hangs indefinitely on unresponsive SSE servers | MCP SDK timeout doesn't bound transport startup; a silent SSE server can block forever. |
| [#8533](https://github.com/QwenLM/qwen-code/issues/8533) | `Content[]`/`Part[]` cannot safely encode per-provider reasoning-replay contracts | Foundational compatibility issue affecting how different LLM providers handle reasoning traces in replay scenarios. |
| [#8412](https://github.com/QwenLM/qwen-code/issues/8412) | Live journal truncation loses turn ownership metadata | When a bounded journal (10k events / 8 MiB) truncates, the marker doesn't identify which prompt "owns" the lost events, breaking SDK replay. **Closed** via PR #8414. |
| [#8452](https://github.com/QwenLM/qwen-code/issues/8452) | Size-triggered microcompaction repeatedly invalidates prompt cache | Once a session crosses the 500k-char threshold, every subsequent ToolResult triggers a rewrite that **defeats provider prompt caching**, inflating latency and cost. **Closed** via PR #8463. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#8415](https://github.com/QwenLM/qwen-code/pull/8415) | `fix(serve): Coordinate caller-supplied session IDs` | Open | Ensures the daemon respects externally provided session IDs rather than overwriting them. |
| [#8425](https://github.com/QwenLM/qwen-code/pull/8425) | `feat(core): share compression cache with Gemini and Vertex AI` | Open | Reuses Google GenAI's provider-managed implicit caching for eligible same-model compression requests, with the existing cold path as fallback. |
| [#8440](https://github.com/QwenLM/qwen-code/pull/8440) | `feat(channels): support group pairing` | Open | Adds `pairing` as a `groupPolicy` value so a group chat can be approved once per stable chat ID and reused by every member. |
| [#8421](https://github.com/QwenLM/qwen-code/pull/8421) | `fix(core): remove fixed Goal continuation limit` | Open | Removes the hardcoded 50-continuation cutoff in Goal v3; active Goals now run until a lifecycle outcome, user pause, or explicit policy intervenes. |
| [#8414](https://github.com/QwenLM/qwen-code/pull/8414) | `fix(webui): recover complete turns after live journal truncation` | **Merged** | Truncation markers now carry authoritative prompt ownership and validated scope/limit metadata, enabling SDK consumers to reconstruct lost turns. |
| [#8512](https://github.com/QwenLM/qwen-code/pull/8512) | `feat(omni): S2 input expansion — image/audio/URL sources` | Open | Extends the omni experiment beyond video to image, audio, URL media, and tool-result media, with raw-resource token estimation and a transport guard. |
| [#8350](https://github.com/QwenLM/qwen-code/pull/8350) | `feat(voice): support trusted private ASR base URLs` | Open | Adds `security.allowedInsecureVoiceBaseUrls` allowlist so managed deployments can route transcription through private-network ASR gateways. |
| [#8442](https://github.com/QwenLM/qwen-code/pull/8442) | `fix: add onCompromised handlers to proper-lockfile calls` | **Merged** | Prevents daemon crashes when a file lock is lost during operation by handling the event with a warning log instead of an unhandled throw. |
| [#8332](https://github.com/QwenLM/qwen-code/pull/8332) | `feat(cli): add audio bridge for attachments` | Open | Transcribes user-supplied audio attachments through a configured batch voice model when the primary model lacks native audio support; replaces with an untrusted transcript. |
| [#8555](https://github.com/QwenLM/qwen-code/pull/8555) | `fix(cli): time out silent MCP SSE startup` | Open | Applies a wall-clock timeout to the full MCP connection attempt, closing the transport and reporting the error instead of hanging indefinitely — directly addresses Issue #8550. |

---

## 5. Feature Request Trends

- **Agent trustworthiness & sandboxing** — Issue #8102's deterministic execution boundaries and Issue #8533's reasoning-replay contract problem reflect a community push toward **verifiable, provider-agnostic agent runtimes**.
- **ACP (Agent Client Protocol) parity** — Three open issues (#8544, #8513, #8546, #8542) all request that ACP surfaces in JetBrains and other IDEs match CLI behavior: task-list rendering, context-usage indicators, `session_info_update` frames, and message queuing mid-turn.
- **Multi-modal input expansion** — PRs #8512 (omni S2) and #8332 (audio bridge) show active investment in treating image, audio, and URL sources as first-class inputs across all surfaces (CLI, headless, ACP).
- **Group & team collaboration** — PR #8440 (group pairing) and the broader channel-work features indicate momentum toward shared/group workspace workflows.
- **Resource governance for `qwen serve`** — Issues #8051 and #8182, plus PR #8423, form a cluster around making the multi-workspace daemon **predictably bounded** in memory, not just in session counts.

---

## 6. Developer Pain Points

1. **Prompt-cache sabotage by compaction** — The 500k-char microcompaction threshold (Issues #8452 / #8463) creates a rolling-rewrite steady state that repeatedly evicts cached prefixes, directly increasing latency and API cost for long sessions.
2. **MCP transport hangs** — Silent or slow SSE servers cause `qwen mcp list` to block indefinitely (Issue #8550); PR #8555 addresses this but it remains open.
3. **Daemon memory over-allocation** — Each ACP child receives a V8 heap ceiling based on the **host** memory, not divided by child count (Issue #8182), risking OOM in multi-child deployments.
4. **Provider warning sanitizer bugs** — Credentials containing `@` in URLs are incorrectly parsed and leaked in `/status` responses (Issue #8136).
5. **ACP feature gaps in JetBrains** — Task lists, usage indicators, and session-title updates are absent from the JetBrains ACP integration despite being available in the CLI (Issues #8544, #8513, #8546).
6. **`--resume` can reconstruct known hazards** — The replay path bypasses the fix from PR #8260, recreating the dangling-unsigned-thought bug (Issue #8535).
7. **Extension hooks are ignored** — Qwen Code loads extensions but does not invoke their hooks, breaking extensions that rely on them (Issue #8539).
8. **Copy-response button non-functional on Windows** — The desktop clipboard button on Windows does nothing (Issue #8538), a persistent UX defect.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-05

## 1. Today's Highlights

The CodeWhale team has launched the v0.9.4 integration release train (#5135, 77 commits ahead of `main`) while simultaneously opening a parallel series of build-performance epics (#5245–#5249) targeting the 682K-line monolith. On the product side, PRs for runtime API goal/memory/MCP lifecycle endpoints and ACP tool exposure signal rapid maturation of the managed-agent surface.

---

## 2. Releases

No new tagged releases landed in the last 24 hours. The **v0.9.4 release train** (#5135) remains open and is the active integration target, superseding #5044.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#5209](https://github.com/Hmbown/CodeWhale/issues/5209) | `File edit` silently accepts wrong param names & reports fake success | Agents can waste 3–5× edits on undetected failures — a correctness bug for the primary editing path | 3 comments, flagged critical |
| [#5244](https://github.com/Hmbown/CodeWhale/issues/5244) | Unknown model IDs silently degrade to 128K legacy context | A 1M-window model silently compacts at 128K with no warning — the author (Hmbown) confirms this is a residual bug behind #5239 | 1 comment |
| [#5239](https://github.com/Hmbown/CodeWhale/issues/5239) | 1M-context models compress at 128K | Same root issue as #5244, reported by a user; directly impacts long-context workflows | 1 comment |
| [#4978](https://github.com/Hmbown/CodeWhale/issues/4978) | Anthropic API 400 `invalid_request_error` with OpenModel | Intermittent `type` enum validation errors when routing through Anthropic-compatible providers; 6 comments, no fix yet | 6 comments |
| [#5241](https://github.com/Hmbown/CodeWhale/issues/5241) | Pricing endpoint returns 503 → all sessions unpriced | Cost display broke after upgrading to v0.9.3; every turn across every provider shows `unverified_live_pricing` | 1 comment |
| [#4991](https://github.com/Hmbown/CodeWhale/issues/4991) | Compilation times & the TUI crate monolith | Open discussion on painful build times during slash-command refactoring; echoes the v0.9.5 build-lane initiative | 4 comments |
| [#4955](https://github.com/Hmbown/CodeWhale/issues/4955) | Zero-sandbox / `--no-sandbox` mode for local dev | Kernel-level Seatbelt sandbox breaks basic shell commands daily; 1 👍 from community | 4 comments, 1 👍 |
| [#5250](https://github.com/Hmbown/CodeWhale/issues/5250) | Only one API key can be saved | Multi-provider users (DeepSeek + GLM etc.) must re-enter keys on every switch; no multi-key storage | 1 comment |
| [#5005](https://github.com/Hmbown/CodeWhale/issues/5005) | ✅ Filesystem path whitelist for sandbox | Closed — allowlisted external paths (e.g., Xcode DerivedData) for sandboxed builds | 2 comments |
| [#5243](https://github.com/Hmbown/CodeWhale/issues/5243) | OAuth token not auto-adopted after login | xAI & ChatGPT/Codex OAuth flows require a second manual trip to the provider picker after successful auth | 0 comments |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#5135](https://github.com/Hmbown/CodeWhale/pull/5135) | v0.9.4 release train | OPEN | 77-commit integration train; supersedes #5044. Primary merge target. |
| [#5242](https://github.com/Hmbown/CodeWhale/pull/5242) | Resume interrupted children from checkpoint | OPEN | `agents/followup` on `interrupted_continuable` children now properly resumes long-running tasks (doc review, multi-step search) instead of dead-lettering. |
| [#5225](https://github.com/Hmbown/CodeWhale/pull/5225) | Expose file/search/git/patch/shell tools over ACP | OPEN | ACP `session/prompt` previously streamed text only — now model tool calls are executed, enabling real code-editing agents via Zed & community adapters. |
| [#5133](https://github.com/Hmbown/CodeWhale/pull/5133) | Runtime API: goal-loop endpoints | OPEN | New `GET /v1/threads/{id}/goal` read + lifecycle transitions for managed clients. |
| [#5131](https://github.com/Hmbown/CodeWhale/pull/5131) | Runtime API: memory endpoints | OPEN | Bounded inspection and lifecycle controls for active memory under `/v1/memory`. |
| [#5130](https://github.com/Hmbown/CodeWhale/pull/5130) | Runtime API: MCP server config & lifecycle | OPEN | Full create/update/remove surface for MCP servers via HTTP; previously required direct TOML/JSON edits. |
| [#5129](https://github.com/Hmbown/CodeWhale/pull/5129) | Runtime API: skill lifecycle endpoints | OPEN | Install, update, uninstall, trust, and audit routes for skills — parity with the TUI. |
| [#5132](https://github.com/Hmbown/CodeWhale/pull/5132) | Runtime API: verifier receipts & evidence | OPEN | Replaces the single `verifier_failed` counter with per-task receipt listing under `/v1/fleet/runs/{run_id}/`. |
| [#5238](https://github.com/Hmbown/CodeWhale/pull/5238) | MCP Registry discovery (registry-first selection) | OPEN | Before falling back to custom code or `exec_shell`, the model consults a public MCP Registry for matching zero-env stdio servers. |
| [#5240](https://github.com/Hmbown/CodeWhale/pull/5240) | Surface real `wait` elapsed time in tool content | OPEN | `duration_ms` now visible to the model in Bash wait results, preventing busy-polling bias. |

---

## 5. Feature Request Trends

- **Build-performance overhaul** — Five linked issues (#5245–#5249) form an epic to decouple git-SHA stamping, split the shipping release profile from local gate builds, consolidate 25 integration-test binaries, and prune the 708-package dependency graph. This is the dominant enhancement theme.
- **Multi-provider key management** — Multiple API keys stored per-provider (#5250) is a recurring ask from multi-model users.
- **Sandbox flexibility** — Users want either a true `--no-sandbox` dev mode (#4955) or granular path allowlisting (#5005, now closed) for build artifacts outside the workspace.
- **Context-window awareness** — Accurate per-model context limits are expected; silent fallback to 128K is seen as a bug (#5244, #5239).
- **ACP & managed-agent parity** — The team is rapidly closing the gap between TUI-native capabilities and the ACP runtime API (tools, goals, memory, MCP, skills).

---

## 6. Developer Pain Points

1. **The monolith compile tax** — `codewhale-tui` (682K lines, 620 files) recompiles as a single unit on every edit, commit, and CI push. Contributors and agents alike feel the lag; the v0.9.5 build-lane epic is the direct response.
2. **Sandbox friction** — The Seatbelt kernel-level sandbox breaks common shell commands. Local developers need either a sandbox override or precise path allowlisting for build artifacts.
3. **Integrating-tool correctness** — #5209 reveals that the `File edit` action accepts misspelled or non-standard parameter names and returns fake success, causing agents to loop blindly. This is a high-severity UX flaw.
4. **OAuth UX gap** — After a successful device login (xAI, ChatGPT/Codex), the acquired token is not auto-applied; users must manually return to the provider picker. (#5243)
5. **Pricing regressions** — Upgrading to v0.9.3 broke live-cost display entirely across all providers (#5241), pointing to a fragile pricing endpoint dependency.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*