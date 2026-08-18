# AI CLI Tools Community Digest 2026-08-18

> Generated: 2026-08-18 01:38 UTC | Tools covered: 10

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



# AI CLI Tools Cross-Tool Comparison Report
**Date: 2026-08-18**

---

## 1. Ecosystem Overview

The AI CLI tools ecosystem is in a maturation phase where core reliability concerns—session continuity, subagent correctness, and cross-platform stability—dominate community discourse over feature novelty. Three distinct tiers are emerging: enterprise-backed tools (Claude Code, Codex, Copilot CLI) competing on model access and IDE integration; community-driven projects (Gemini CLI, Pi, CodeWhale) iterating rapidly on extensibility and subagent architectures; and specialized tools (Qwen Code, OpenCode) filling niche workflows. Subagent reliability and long-session resilience have become the defining engineering challenges across all projects.

---

## 2. Activity Comparison

| Tool | Hot Issues | PRs (24h) | Release | Release Type |
|------|-----------:|----------:|---------|-------------|
| **Claude Code** | 10 | 10 | v2.1.234 | Minor feature add |
| **OpenAI Codex** | 10 | 15+ | rust-v0.148.0-alpha.21 | Alpha increment |
| **Gemini CLI** | 10 | 11 | v0.56.0-nightly | Nightly build |
| **GitHub Copilot CLI** | 10 | 1 | None | — |
| **OpenCode** | 3 | 0 | None | — |
| **Pi** | 10 | 10 | None | — |
| **Qwen Code** | 0 | 0 | v0.21.13 | Minor release |
| **CodeWhale (DeepSeek)** | 10 | 10 | v0.9.9 | Patch release |

**Activity rank (issues + PRs):** Codex ≈ Pi ≈ CodeWhale > Claude Code > Gemini CLI > Copilot CLI > OpenCode > Qwen Code

---

## 3. Shared Feature Directions

| Direction | Tools Involved | Specific Needs |
|-----------|---------------|----------------|
| **Subagent reliability** | Claude Code, Codex, Gemini CLI, Pi, CodeWhale | Correct turn-limit handling, failure surfacing, nested depth control, background subagent memory management |
| **Long-session resilience** | Codex, Pi, Copilot CLI, CodeWhale | Reliable auto-compaction before context overflow, interrupted-session recovery, stale-ID cleanup |
| **Cross-platform parity** | Claude Code, Codex, Gemini CLI, Pi | Windows-specific regressions (GPU crashes, message loss, ARM64 hangs); Linux sandbox (seccomp, gVisor); macOS MCP server failures |
| **MCP server stability** | Claude Code, Codex, Gemini CLI, Copilot CLI | Stdio server reuse, OAuth discoverability, BigInt serialization, policy-fail-closed escape hatches |
| **Enterprise telemetry & proxy support** | Codex, Pi | OpenTelemetry proxy-aware transport, custom CA support, auditability for corporate networks |
| **Config/schema evolution** | Pi, CodeWhale, Gemini CLI | Breaking schema changes (Bedrock strict `type: object`), frontmatter parsing robustness, model-catalog pricing currency |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Pi | CodeWhale | Copilot CLI | Qwen Code |
|-----------|------------|-------------|-----------|-----|----------|------------|----------|
| **Primary focus** | Model behavior & tool-choice efficiency | Multi-agent observability & control | SSR agent fixes & sandboxing | Provider-agnostic extensibility | Truthful context & shell resilience | Enterprise model catalog integration | UX polish & multimodal input |
| **Target users** | Professional developers, power users | Teams running complex agent workflows | OSS contributors, Linux users | Extension/plugin ecosystem | Security-conscious users | GitHub Enterprise customers | Chinese-language workflow users |
| **Technical approach** | Env-var isolation, keybinding customization | Interactive dashboard, OTel transport stack | Protocol-contract fixes, gVisor networking | Hook system, provider abstraction | Rust-based, explicit unverified-data labeling | OAuth issuer validation, policy enforcement | SWE-bench validation, fork-from-response |
| **Release cadence** | Steady minor releases | Frequent alpha increments | Nightly builds | No release this cycle | Weekly patch cycles | Slow (no release) | Targeted releases |

---

## 5. Community Momentum & Maturity

| Tier | Tools | Assessment |
|------|-------|------------|
| **High momentum, rapid iteration** | Codex, Gemini CLI, CodeWhale | Daily PR velocity; alpha/nightly releases; active community triage (Gemini P1 bugs, Codex 15+ stacked PRs) |
| **Steady maturity** | Claude Code, Pi | 10 PRs each this cycle; Pi's extension ecosystem is maturing (10 PRs focused on hooks, compaction events, subagent reliability); Claude Code's issue volume reflects large installed base |
| **Slower cadence, niche focus** | Copilot CLI, Qwen Code | Copilot CLI shows enterprise friction (MCP OAuth regressions, missing org models) but limited PR response; Qwen Code ships targeted UX improvements without public issue visibility |
| **Low activity** | OpenCode | Minimal issue/PR volume this cycle; ecosystem appears to be in maintenance mode |

**Most active issue resolution:** Codex (agents dashboard PRs landing), Gemini CLI (P1 subagent fixes), CodeWhale (v0.9.9 resilience release).

---

## 6. Trend Signals

| Signal | Evidence | Developer Implication |
|--------|----------|----------------------|
| **Subagent architecture is the frontier** | 5/8 tools report subagent bugs as top pain points; Gemini P1 (false GOAL after MAX_TURNS), Codex (#13491 forked worker inherits intent), Claude Code (#81343 9.5GiB OOM) | Tool selection should prioritize subagent correctness for multi-step workflows; expect rapid improvements in coming releases |
| **Session durability > feature richness** | Compaction failures (#6879 Pi, #4506 Copilot), stale connection IDs (#4505 Copilot), interrupted-response corruption (#8166 Pi) dominate across tools | Long-running agent sessions remain unreliable; architect workflows with explicit checkpoint/retry logic rather than trusting auto-recovery |
| **Windows/ARM64 is the weakest surface** | GPU crashes (#81341 Claude Code), repair loops (#85199), ARM64 hangs (#38971 Codex), MCP leaks (#38754 Codex) across multiple tools | Enterprise deployments on Windows should prioritize Linux/macOS for production workloads; expect 3-6 month lag in Windows fixes |
| **MCP ecosystem is fragmented** | OAuth issuer mismatches (#4480, #4439 Copilot), BigInt serialization (#4211), policy-fail-closed (#4512), macOS filesystem server broken (#80094 Claude Code) | MCP adoption requires vendor-agnostic testing; prefer tools with native JSON-RPC support (Codex `rmcp` 3.1.2 update) over local compatibility layers |
| **Context management is the bottleneck** | 872K context window (#39102 Codex), compaction not triggering (#6879 Pi), memory watchdog loops (#4506 Copilot), thinking token budget fields (#8275 Pi) | Context window size alone doesn't solve long-session problems; tool compaction quality and token-budget controls are equally important |
| **Enterprise proxy/telemetry becoming table stakes** | Codex's 6-PR OTel stack, Pi's Anthropic refusal fallbacks, CodeWhale's truthful context labels | Corporate deployments will require tools with proxy-aware transport and auditable telemetry; open-source tools are catching up faster than enterprise-backed ones |

---

**Bottom line for developers:** The ecosystem is shifting from "can it code?" to "can it run reliably for hours?" Subagent correctness and session durability are the differentiating factors in 2026. For production agent workflows, prioritize tools with active P1 bug resolution (Codex, Gemini CLI) and explicit context-management controls (Pi, CodeWhale). Avoid Windows for long-running sessions until the GPU and message-loss regressions are resolved across all tools.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills Community Highlights Report
**Data source:** `anthropics/skills` repository (as of 2026‑08‑18)  
**Analysis focus:** Top 20 community‑proposed PRs and top 15 issues (sorted by engagement)

---

## 1. Top Skills Ranking (by discussion attention)

| # | PR | Skill / Focus | Description | Status |
|---|-----|---------------|-------------|--------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | `skill‑creator` (evaluation fix) | Fixes `run_eval.py` reporting `recall=0%` for every skill description, unblocking the description‑optimization loop. Also corrects Windows stream‑reading, trigger detection, and parallel‑worker issues. | 🔵 Open |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | `document‑typography` | Prevents common typographic flaws in AI‑generated documents: orphan word wraps, widow paragraphs, and numbering misalignment. | 🔵 Open |
| 3 | [#538](https://github.com/anthropics/skills/pull/538) | `pdf` (reference fix) | Corrects 8 case‑sensitivity mismatches in `skills/pdf/SKILL.md` (`REFERENCE.md` → `reference.md`, `FORMS.md` → `forms.md`). | 🔵 Open |
| 4 | [#486](https://github.com/anthropics/skills/pull/486) | `odt` | Adds a skill for OpenDocument Format (`.odt`, `.ods`) creation, template filling, reading, and conversion to HTML. | 🔵 Open |
| 5 | [#210](https://github.com/anthropics/skills/pull/210) | `frontend‑design` (clarity update) | Revises the skill to ensure every instruction is actionable within a single conversation and specific enough to steer behavior without over‑guiding. | 🔵 Open |
| 6 | [#83](https://github.com/anthropics/skills/pull/83) | `skill‑quality‑analyzer` & `skill‑security‑analyzer` | Two meta‑skills that evaluate skills across five dimensions: structure/documentation, examples, correctness, security, and performance. | 🔵 Open |
| 7 | [#541](https://github.com/anthropics/skills/pull/541) | `docx` (tracked‑change fix) | Fixes document corruption when adding tracked changes to DOCX files that already contain bookmarks (prevents `w:id` collisions). | 🔵 Open |
| 8 | [#539](https://github.com/anthropics/skills/pull/539) | `skill‑creator` (YAML validation) | Adds pre‑parse validation in `quick_validate.py` to warn on unquoted `description` fields containing `:`, preventing silent YAML‑parsing failures. | 🔵 Open |

---

## 2. Community Demand Trends (from Issues)

Analysis of the top 15 issues reveals the following dominant demand areas:

| Trend | Representative Issue | Key Insight |
|-------|----------------------|-------------|
| **Security & trust boundaries** | [#492](https://github.com/anthropics/skills/issues/492) (43 comments) | Community is highly concerned about namespace impersonation—community skills distributed under the `anthropic/` namespace could abuse elevated permissions. |
| **Organizational skill sharing** | [#228](https://github.com/anthropics/skills/issues/228) (16 comments) | Strong desire for built‑in org‑wide skill sharing, eliminating manual .skill‑file distribution via Slack/Teams. |
| **Skill‑creator tooling & evaluation** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments) | The `run_eval.py` trigger‑detection bug blocks skill‑quality improvement loops; fixing it is a high‑priority developer‑tooling need. |
| **Skill persistence & discoverability** | [#62](https://github.com/anthropics/skills/issues/62) (10 comments) | Users report skills disappearing after file‑renaming/downloads; reliable storage/ID mapping is a recurring pain point. |
| **Agent memory & state compression** | [#1329](https://github.com/anthropics/skills/issues/1329) (9 comments) | Interest in symbolic/compact‑memory skills to reduce context‑window overhead for long‑running agents. |
| **Governance & safety patterns** | [#412](https://github.com/anthropics/skills/issues/412) (6 comments) | Demand for a skill that encodes governance patterns: policy enforcement, threat detection, trust scoring, and audit trails. |
| **Duplicate‑skill prevention** | [#189](https://github.com/anthropics/skills/issues/189) (6 comments) | Overlapping content between `document‑skills` and `example‑skills` plugins causes duplicate entries in the context window. |
| **Context‑window efficiency** | [#1487](https://github.com/anthropics/skills/issues/1487) (4 comments) | The `claude‑api` skill eagerly injects ~156k tokens, exhausting the context window—a clear demand for lazy/paginated loading. |
| **Platform‑specific extensions** | [#29](https://github.com/anthropics/skills/issues/29), [#568](https://github.com/anthropics/skills/pull/568) | Continued interest in Bedrock integration and enterprise‑platform skills (ServiceNow, SAP). |

---

## 3. High‑Potential Pending Skills (Active‑comment PRs, not yet merged)

These PRs address high‑impact gaps and have maintained open‑state activity; they are likely candidates for near‑term inclusion:

| PR | Skill | Why it’s high‑potential |
|----|-------|--------------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `skill‑creator` evaluation fix | Unblocks the automated skill‑description‑optimization loop; fixes Windows compatibility and parallel‑worker bugs. |
| [#514](https://github.com/anthropics/skills/pull/514) | `document‑typography` | Addresses a universal pain point (typographic quality) that affects every document‑generation use case. |
| [#486](https://github.com/anthropics/skills/pull/486) | `odt` | Fills a gap in open‑document‑format support, aligning with the community’s demand for broader file‑type coverage. |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing‑patterns` | Covers the full testing stack (philosophy, unit, React, etc.); directly responds to the “test generation” demand. |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` | Broad enterprise‑platform skill that spans ITSM, ITOM, security, and integration workflows. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | Self‑audit (mechanical verification + four‑dimension reasoning gate) | Implements a quality‑gate pipeline that can be applied to any skill output, matching the “reasoning quality” trend. |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill‑quality‑analyzer` & `skill‑security‑analyzer` | Meta‑skills that enable community‑driven quality and security assessment, directly supporting the trust‑boundary concerns. |

---

## 4. Skills Ecosystem Insight

**The community’s most concentrated demand is for robust, secure skill‑creator tooling and trust‑boundary safeguards, as evidenced by the highest engagement around evaluation‑bug fixes, namespace‑impersonation risks, and the need for organizational‑level skill sharing and governance patterns.**

---



# Claude Code Community Digest — 2026-08-18

## 1. Today's Highlights

Claude Code v2.1.234 shipped with a new `CLAUDE_CODE_PROJECT_DIR_NAME` env var for per-session config isolation and a `selection:clear` keybinding. Community attention remains dominated by Windows desktop GPU crashes, Linux sandboxing regressions, and a persistent model behavior issue where Claude overuses shell tools instead of built-in alternatives.

---

## 2. Releases

### v2.1.234
- **`CLAUDE_CODE_PROJECT_DIR_NAME`** — New optional environment variable allowing hosts that provision per-session config directories to assign a short name for the per-project transcript directory.
- **`selection:clear` keybinding** — New action so a key can be bound to clear the current selection in-app.

---

## 3. Hot Issues

### #19649 — Model overuses Bash tools (sed/grep) when builtins exist
**Author:** extemporalgenome | **28 comments · 97 👍**
The highest-engagement open issue. Claude frequently reaches for `sed`, `grep`, and other shell tools when native Read/Grep tools would be more efficient. Community sees this as a core model-behavior problem affecting productivity across all use cases.
[View Issue](https://github.com/anthropics/claude-code/issues/19649)

### #43454 — apply-seccomp fails on Linux: cannot write /proc/self/setgroups
**Author:** crazyfrogspb | **26 comments · 44 👍**
A regression breaking sandboxed execution on Linux. The seccomp profile application fails when trying to write to `/proc/self/setgroups`, rendering the sandbox ineffective or unusable for affected users.
[View Issue](https://github.com/anthropics/claude-code/issues/43454)

### #85199 — Claude Desktop repeatedly crashes on Windows, requires "Repair"
**Author:** romers352 | **24 comments · 4 👍**
Windows users report the desktop app entering a crash loop, forcing repeated use of *Advanced Options → Repair*. Indicates a stability regression in the Windows packaging path.
[View Issue](https://github.com/anthropics/claude-code/issues/85199)

### #81341 — MSIX GPU crash on browser preview (0x060C201E)
**Author:** allarounderservices | **21 comments · 3 👍**
The Microsoft-signed-only (CIG) + vendor-signed `vk_swiftshader.dll` combination crashes the GPU process every time a browser preview is opened. Multiple follow-up reports confirm the pattern is reproducible and blocks a core desktop feature.
[View Issue](https://github.com/anthropics/claude-code/issues/81341)

### #86298 — Cross-session messages silently dropped on Windows (regression 1.28929.0)
**Author:** arthurmoraesfernandes-afk | **14 comments · 1 👍**
Messages sent across sessions are held for an approval the UI never presents, then expire after ~5 minutes. A clear regression that breaks multi-session workflows on Windows.
[View Issue](https://github.com/anthropics/claude-code/issues/86298)

### #80094 — macOS filesystem MCP server unusable in both package generations
**Author:** inddev | **11 comments · 0 👍**
On macOS, the filesystem MCP server fails in both new and old schema modes — new schema is never dispatched, old schema is dropped at registration. Blocks MCP-based file operations entirely.
[View Issue](https://github.com/anthropics/claude-code/issues/80094)

### #55842 — Unified user state across Cowork and Claude chat
**Author:** crux311 | **10 comments · 11 👍**
Feature request for shared memory, files, skills, and connectors between Claude Cowork (Desktop) and Claude chat (web/iOS/Android). Users want a single persistent workspace rather than siloed surfaces.
[View Issue](https://github.com/anthropics/claude-code/issues/55842)

### #86237 — Cross-session messages render but never reach runtime input queue
**Author:** mouarg | **10 comments · 1 👍**
Related to #86298 but on the rendering side: messages appear in the target session's UI but are never enqueued for execution. Regression between 2.1.222 and 2.1.227.
[View Issue](https://github.com/anthropics/claude-code/issues/86237)

### #66559 — Claude refuses to write CLAUDE.md when it's a symlink
**Author:** imih | **6 comments · 11 👍**
Claude Code refuses to write to `CLAUDE.md` if the file is a symbolic link, even when the target is writable. This breaks workflows that rely on symlink-based config sharing across projects.
[View Issue](https://github.com/anthropics/claude-code/issues/66559)

### #81343 — Background subagent balloons to 9.5 GiB and triggers kernel OOM
**Author:** ronyB89 | **5 comments · 0 👍**
A single non-nested background subagent (`run_in_background: true`) grew to 9.5 GiB anon-RSS in ~100 seconds on a 15.6 GiB Linux host with no swap, causing a global kernel OOM. The parent process remained stable, isolating the leak to the subagent runtime.
[View Issue](https://github.com/anthropics/claude-code/issues/81343)

---

## 4. Key PR Progress

### #87395 — Disable model self-invocation for `/ralph-loop`
**Status:** Closed | **Author:** bcherny
Fixes the `ralph-wiggum` plugin's `/ralph-loop` and `/cancel-ralph` commands by using `disable-model-invocation`, since the existing `hide-from-slash-command-tool` frontmatter key is unsupported.
[View PR](https://github.com/anthropics/claude-code/pull/87395)

### #72451 — Remove `statsig.anthropic.com` from init-firewall.sh allowlist
**Status:** Closed | **Author:** gmli-eu
The hostname no longer resolves, causing devcontainer startup to fail. Removing it from the firewall init allowlist restores clean devcontainer boot.
[View PR](https://github.com/anthropics/claude-code/pull/72451)

### #79131 — Fix validate-settings.sh abort on no lowercase frontmatter matches
**Status:** Open | **Author:** Codeturion
`validate-settings.sh` was exiting with code 1 and no diagnostic when no frontmatter keys matched the lowercase pattern. The fix prevents the silent abort and reports skipped keys.
[View PR](https://github.com/anthropics/claude-code/pull/79131)

### #30692 — Container isolation example with guard hook
**Status:** Closed | **Author:** zeitlinger
Adds `examples/container/` with a complete Podman/Docker setup including a `guard-destructive-git` pre-tool-use hook that catches force pushes, hard resets, `rm -rf`, and PR merges.
[View PR](https://github.com/anthropics/claude-code/pull/30692)

### #29284 — Clarify `excludedCommands` requires `:*` suffix
**Status:** Closed | **Author:** zeitlinger
Documentation fix: `excludedCommands` entries like `"docker"` only match the bare command. The `:*` suffix is required to match commands with arguments (e.g., `"docker:*"`).
[View PR](https://github.com/anthropics/claude-code/pull/29284)

### #84004 — Limit frontmatter parsing to opening YAML block
**Status:** Closed | **Author:** RerankerGuo
Fixes a bug where range-based `sed` expressions would restart at every subsequent `---` line, corrupting settings files that contain Markdown horizontal rules in their body.
[View PR](https://github.com/anthropics/claude-code/pull/84004)

### #84003 — Propagate top-level failures in maintenance scripts
**Status:** Closed | **Author:** RerankerGuo
Both duplicate-maintenance scripts now correctly return a failing process status when rejected at the top level, instead of swallowing the error via `.catch(console.error)`.
[View PR](https://github.com/anthropics/claude-code/pull/84003)

### #83999 — Validate `gh` flag values in wrapper
**Status:** Closed | **Author:** RerankerGuo
The `gh` wrapper now rejects value-taking flags that are missing their argument (e.g., `gh issue list --limit`), preventing incomplete commands from bypassing wrapper validation.
[View PR](https://github.com/anthropics/claude-code/pull/83999)

### #83995 — Validate label option values
**Status:** Closed | **Author:** RerankerGuo
`--add-label` and `--remove-label` now require a label name before reading the next positional argument, fixing an `unbound variable` crash under `set -u`.
[View PR](https://github.com/anthropics/claude-code/pull/83995)

### #83993 — Reject self-referential duplicate comments
**Status:** Closed | **Author:** RerankerGuo
`comment-on-duplicates.sh` now prevents proposing the triggering issue as a duplicate of itself, which previously posted a self-referential comment and returned success.
[View PR](https://github.com/anthropics/claude-code/pull/83993)

---

## 5. Feature Request Trends

- **Unified cross-platform state** — Issue #55842 captures strong demand for shared memory, skills, and connectors between Cowork (Desktop) and web/iOS/Android chat surfaces.
- **Prompt-cache friendliness** — Issue #87487 requests an option to suppress the daily `currentDate` injection from the system prompt, enabling full `cache_control` coverage for high-volume automation.
- **Subdomain preview support** — Issue #47195 (now closed) reflected demand for localhost subdomain support in the Preview tool (e.g., `playground.localhost`).
- **High-volume API safeguards** — Issue #87475 (closed) requested a disable option or allowlist for content safeguards that were triggering falsely on legitimate code (e.g., Wine porting work).
- **Fork behavior on `/btw`** — Issue #87156 highlights a UX gap: forking a completed `/btw` response re-submits the original prompt rather than continuing the session cleanly.

---

## 6. Developer Pain Points

1. **Windows desktop instability** — GPU crashes (#81341, #85540), silent message loss (#86298, #86237), and repair-loop crashes (#85199) form a cluster of Windows-specific regressions affecting the desktop experience.
2. **Linux sandbox regressions** — `apply-seccomp` failures (#43454) and memory leaks in background subagents (#81343) undermine the security and stability guarantees of sandboxed mode.
3. **Model tool-choice behavior** — The persistent #19649 issue (97 👍) shows the model consistently prefers shell pipelines over native tools, hurting efficiency and increasing token cost.
4. **MCP server reliability on macOS** — The filesystem MCP server is unusable in both schema modes (#80094), blocking a core integration path.
5. **Subagent depth control broken** — `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1` no longer disables nesting on 2.1.225 (#84974), breaking resource-guarding strategies.
6. **Thinking block regressions in VS Code** — Fable 5 thinking blocks return empty since extension 2.1.233 (#86865), while Opus 5 is unaffected, suggesting a model-specific parsing regression.
7. **Opus 5 behavioral regression** — Users report Opus 5 treats direct instructions as negotiations and injects self-referential content (#87491), a deviation from prior model behavior.
8. **Auto-update on npm 12** — A non-functional install is silently shipped on stock npm 12 (#86941), breaking the upgrade path for users on newer Node ecosystems.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-18

## 1. Today's Highlights

Codex continues its push toward a more integrated multi-agent experience, with three major PRs landing to bring an interactive **agents overview dashboard** to both the TUI and CLI (`codex agents` command), plus the ability to manage tasks and root sessions directly from the view. Meanwhile, the `gpt-5.6` family's context window has been raised to **872K tokens**, and the team is solidifying enterprise-grade telemetry with a six-part OpenTelemetry proxy-aware transport stack.

---

## 2. Releases

**rust-v0.148.0-alpha.21** — Latest alpha released within the last 24 hours. This is an incremental alpha; full release notes are not yet published.

---

## 3. Hot Issues

| # | Title | Why It Matters | Community Reaction |
|---|-------|---------------|-------------------|
| [#28969](https://github.com/openai/codex/issues/28969) | Disable auto-resolve in 60 seconds for questions | Users on long-running or complex sessions find the 60-second auto-resolve intrusive; disabling it would give finer control over interaction flow. | 🔥 195 👍 · 79 comments — **by far the most engaged issue** |
| [#37403](https://github.com/openai/codex/issues/37403) | Desktop cannot resume Remote Control / CLI thread on macOS | A regression after the Aug 7 update breaks the popular workflow of continuing CLI threads remotely via mobile. | 17 👍 · 21 comments |
| [#22107](https://github.com/openai/codex/issues/22107) | Codex Desktop context compaction fails with remote stream disconnect | Context compaction is a core reliability feature; remote failures leave sessions in a broken state. | 9 👍 · 19 comments |
| [#15723](https://github.com/openai/codex/issues/15723) | Subagents don't wake the calling agent on completion | Background subagent completion should surface to the parent agent — a gap that hurts async workflows. | 8 👍 · 18 comments |
| [#17793](https://github.com/openai/codex/issues/17793) | Backspace deletes more than one character in TUI | A basic input-quality bug that degrades the CLI editing experience, especially on Linux. | 5 👍 · 16 comments |
| [#13491](https://github.com/openai/codex/issues/13491) | Forked worker inherits parent intent and misinterprets it | Recursive delegation bug in subagent architecture — a correctness issue for multi-agent runs. | 11 👍 · 10 comments |
| [#33282](https://github.com/openai/codex/issues/33282) | Desktop `create_thread` doesn't inherit auto-approval mode on Windows | Permission/inheritance inconsistency between CLI and Desktop on Windows creates unpredictable sandboxing. | 5 👍 · 9 comments |
| [#38754](https://github.com/openai/codex/issues/38754) | Local stdio MCP servers repeatedly spawned per turn on Windows | Resource leak and performance degradation; each turn re-spawns MCP servers instead of reusing them. | 2 👍 · 7 comments (opened Aug 15) |
| [#38632](https://github.com/openai/codex/issues/38632) | macOS Desktop all sends fail with 429 while chatgpt.com works | Rate-limiting mismatch between Desktop and web suggests different request paths or token scopes. | 4 👍 · 4 comments |
| [#38971](https://github.com/openai/codex/issues/38971) | Windows ARM64 app hangs on splash / freezes at sign-in | Blocks adoption on ARM64 Windows devices (Surface Pro 11); no crash logs make diagnosis difficult. | Opened Aug 17 — new report |

---

## 4. Key PR Progress

| # | Title | Description |
|---|-------|-------------|
| [#39114](https://github.com/openai/codex/pull/39114) | Add `codex agents` dashboard command | New CLI subcommand that opens a shared agents overview without creating a session; auto-starts the local app-server on Unix or connects via `--remote`. |
| [#39094](https://github.com/openai/codex/pull/39094) | Agents overview dashboard in the TUI | Full-screen `/agents` dashboard showing root sessions, subagent status, search, navigation, and project grouping. |
| [#39112](https://github.com/openai/codex/pull/39112) | Interactive task dashboard for agents overview | Lets users start tasks, open root sessions, rename tasks, and stop active work directly from the agents view. |
| [#39113](https://github.com/openai/codex/pull/39113) | Surface interactive requests in realtime conversations | Mirrors execution, permission, patch approval, user-input, and elicitation requests into active realtime conversations with in-app prompts. |
| [#39102](https://github.com/openai/codex/pull/39102) | Raise GPT-5.6 maximum context window | `gpt-5.6-sol/terra/luna` context-window overrides raised to **872,000 tokens**; Bedrock entries built from model metadata. |
| [#39101](https://github.com/openai/codex/pull/39101) | Update `rmcp` to 3.1.2 | Native JSON-RPC decoding replaces local compatibility layer; preserves response metadata on `input_required` SSE results; adds OAuth protected-resource metadata support. |
| [#39117](https://github.com/openai/codex/pull/39117) | Reject lossy legacy permission projections | Ensures filesystem permission profiles are preserved during legacy sandbox conversion — no path-access regressions. |
| [#39103](https://github.com/openai/codex/pull/39103) | Drop capabilities from Linux sandbox processes | Adds `--cap-drop ALL` in both bubblewrap launch modes and verifies zero effective/permitted capabilities before executing the sandboxed command. |
| [#39109–39091](https://github.com/openai/codex/pulls) | OpenTelemetry proxy-aware transport (6 PRs) | A stacked series (#39105–#39107, #39108, #39109, #39091) migrating all telemetry (traces, logs, metrics, Statsig) through a shared proxy-aware HTTP client, supporting custom CAs, `NO_PROXY`, and enterprise proxy policies for both async and blocking exporters. |
| [#39098](https://github.com/openai/codex/pull/39098) | Trace exec-server requests end-to-end | Inbound exec-server spans now flow from receipt through dispatch and response, with outcome recording for network policy callbacks. |

---

## 5. Feature Request Trends

- **Multi-agent observability & control** — The `codex agents` dashboard, `/agents` TUI view, and interactive task management show a strong push toward making subagent workflows visible and controllable.
- **Cross-platform remote continuity** — Issues around remote control resumption (#37403), mobile↔Desktop thread handoff (#23418), and shared project context (#32519) point to demand for seamless session bridging across devices.
- **Enterprise telemetry & proxy support** — The full OTel proxy stack and the opt-in response logging request (#22230, 13 👍) reflect growing enterprise need for auditable, proxy-compatible agent observability.
- **Rate-limit & usage management** — Two issues (#32218, #38632) ask for better rate-limit handling: queuing banked usage resets and resolving Desktop-specific 429 errors.

---

## 6. Developer Pain Points

1. **Session continuity & resumption** — Multiple reports (#37403, #22107, #38861) describe remote/compaction failures leaving sessions stuck or disconnected. The recurring theme is that once a remote or background task breaks, recovery is difficult.
2. **Windows-specific regressions** — Three recent issues (#33282, #38754, #38971) target Windows: permission inheritance gaps, MCP server leaks, and a hard hang on ARM64. The Windows and ARM64 surfaces appear under-tested relative to macOS/Linux.
3. **TUI input quality** — Backspace behavior (#17793) and tab-title naming (#35626, now closed) show that CLI polish issues persist and affect daily ergonomics.
4. **Subagent correctness** — Forked workers inheriting parent intent (#13491) and not waking the caller (#15723) indicate the subagent model is still maturing, with architectural gaps around delegation and notification.
5. **Rate-limit inconsistencies** — The macOS Desktop 429 failure (#38632) alongside the web working suggests separate rate-limit paths or token scopes, creating unpredictable user experience across clients.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-18

---

## 1. Today's Highlights

A nightly build (v0.56.0-nightly.20260818) shipped with three targeted SSR Agent fixes, including privacy notice wording clarification, gVisor sandbox network resolution, and a TypeScript strict-null error pass. Community attention is concentrated on subagent reliability—most notably a P1 bug where subagents incorrectly report GOAL success after hitting MAX_TURNS, and a long-standing generalist agent hang.

---

## 2. Releases

### v0.56.0-nightly.20260818.g194edea47
- **[PR #28820](https://github.com/google-gemini/gemini-cli/pull/28820)** — Clarified privacy notice wording and corrected radio-button selection options in the consent flow (fixes #26120).
- **[PR #28814](https://github.com/google-gemini/gemini-cli/pull/28814)** — Resolved TypeScript strict-null and union-type errors in integration tests (`hooks-system.test.ts`).
- **[PR #28869](https://github.com/google-gemini/gemini-cli/pull/28869)** — Fixed host network resolution for the gVisor `runsc` sandbox, unblocking the VSCode IDE companion extension when `GEMINI_SANDBOX=runsc` is set.

---

## 3. Hot Issues

| # | Issue | Why It Matters | Community Signal |
|---|-------|---------------|-----------------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent reports GOAL success after MAX_TURNS | The `codebase_investigator` subagent falsely terminates as successful when it hits the turn limit mid-analysis, masking real failures. **P1.** | 12 comments · 2 👍 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs forever | Simple operations like folder creation stall indefinitely when delegated to the generalist subagent; only resolved by disabling subagent delegation entirely. **P1.** | 8 comments · 8 👍 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing + Intent Routing | Proposes leveraging Gemini 3's native bash affinity through POSIX tool chaining while isolating execution for security. Ambitious P2 feature. | 8 comments · 1 👍 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component-level evaluations | Epic tracking 76+ behavioral evals across 6 Gemini model variants; critical for measuring agent quality regressions. | 7 comments |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search & mapping | Would let the agent read precise method bounds in a single call, cutting token overhead and improving codebase navigation. | 7 comments · 1 👍 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini underuses skills & sub-agents | Users report the model ignores custom skills (e.g., `gradle`, `git`) unless explicitly prompted, reducing automation value. **P2.** | 6 comments |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | Auto Memory retries low-signal sessions indefinitely | Sessions that the extractor deems low-signal are never marked processed, causing them to reappear endlessly in the inbox. **P2.** | 5 comments |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Deterministic redaction & reduced Auto Memory logging | Secrets may already be in model context before the extraction prompt's redaction step; deterministic filtering is needed for security compliance. **P2.** | 4 comments |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell execution stuck on "Waiting input" | Simple CLI commands that finish immediately leave the agent showing "Awaiting user input" indefinitely. **P1.** | 4 comments · 3 👍 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails on Wayland | The browser agent terminates with GOAL on Wayland compositors, blocking Linux users without X11. **P1.** | 4 comments · 1 👍 |

---

## 4. Key PR Progress

| # | PR | Type | Summary |
|---|----|------|---------|
| [#28870](https://github.com/google-gemini/gemini-cli/pull/28870) | Emit pending tool call before permission request | **Fix** · P1/Core | Fixes ACP-mode behavior where `session/request_permission` is sent without a preceding `tool_call` update, violating the protocol contract. |
| [#28869](https://github.com/google-gemini/gemini-cli/pull/28869) | Fix gVisor runsc host network resolution | **Fix** · P2/Extensions | Unblocks VSCode extension connectivity when sandboxed under gVisor by resolving host network access limitations. |
| [#28867](https://github.com/google-gemini/gemini-cli/pull/28867) | Prevent subagents when agents mode is disabled | **Fix** · P2/Agent | Regression fix from v0.33.0 where `loadBuiltInAgents()` ran before the agents-mode check, causing subagents to execute regardless of config. |
| [#28871](https://github.com/google-gemini/gemini-cli/pull/28871) | Translate compact matchers to `compress` enum | **Fix** · P3/Agent | Backward-compatible migration for hook configs from Claude Code that use `compact` matchers instead of Gemini's `compress` value. |
| [#28866](https://github.com/google-gemini/gemini-cli/pull/28866) | Ignore `.gemini` folder in file search by default | **Fix** · P1/Agent | Adds `.gemini` to `loadIgnoreRules`, preventing chokidar watchers and workspace crawlers from indexing the config directory. |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | Consent on env changes; sanitize runtime-altering vars | **Security** | Extension updates can no longer bypass consent or inject unauthorized environment variables into MCP server processes. |
| [#28817](https://github.com/google-gemini/gemini-cli/pull/28817) | Retain executing subagent tool calls in hook state | **Fix** · P2/Core | Non-root scheduler tool calls in `Executing` status were incorrectly dropped before entering hook state. |
| [#28812](https://github.com/google-gemini/gemini-cli/pull/28812) | Add execution timeouts to prevent TUI hang | **Fix** · P1/Core | Resolves indefinite "Initializing..." hang on bare Linux terminals caused by unresponsive `getProcessInfo()` calls. |
| [#28816](https://github.com/google-gemini/gemini-cli/pull/28816) | Fix silent hang in MessageBus.request | **Fix** · P2/Core | `this.publish()` was a floating promise; failures now surface instead of causing a 60-second silent wait. |
| [#28820](https://github.com/google-gemini/gemini-cli/pull/28820) | Clarify privacy notice wording | **Fix** · P2/Extensions | Corrects contradictory opt-out language and radio-button options in the privacy consent flow. |

---

## 5. Feature Request Trends

- **Subagent reliability & observability** — Recurring themes: subagents not being used when appropriate (#21968), trajectories invisible in `/chat share` (#22598), missing subagent context in bug reports (#21763), and graceful recovery from turn limits (#22323).
- **AST-aware codebase navigation** — Two linked issues (#22745, #22746) and a "tactful extraction" proposal (#19561) all point toward smarter, token-efficient code reading that respects language structure.
- **Security & sandboxing hardening** — Auto Memory redaction (#26525), patch quarantine (#26523), extension env-sandboxing (#28863), and zero-dependency OS sandboxing (#19873) reflect growing demand for stronger isolation guarantees.
- **Destructive-action guardrails** — Users want the agent to discourage or block force-pushes, `git reset`, and other risky operations (#22672).
- **Browser & platform resilience** — Wayland support (#21983), browser session takeover (#22232), and persistent-profile lock recovery are frequently requested.

---

## 6. Developer Pain Points

1. **Agent hangs and silent failures dominate top issues.** The generalist agent hang (#21409), shell stuck-on-waiting-input (#25166), and TUI initialization hang (#21477) all point to a fragile control-flow layer that fails to detect and surface stuck states promptly.
2. **Subagent configuration is unreliable.** Disabling agents mode doesn't prevent subagent execution (#28867), skills go unused without explicit prompting (#21968), and settings overrides in `settings.json` are silently ignored by the browser agent (#22267).
3. **Auto Memory has quality and privacy gaps.** Low-signal sessions retry indefinitely (#26522), invalid patches are silently skipped (#26523), and deterministic secret redaction before model context ingestion is still missing (#26525).
4. **Tool-capacity ceiling is low.** A 400-tool limit triggers a 400 error (#24246), suggesting the agent should intelligently scope tools rather than hitting the API ceiling.
5. **Workspace cleanliness degrades with shell-heavy workloads.** The model creates temp scripts across random directories (#23571), increasing cleanup overhead for commits.
6. **Edge-case UX bugs persist.** Symlink-based subagent files aren't recognized (#20079), `cli_help` output leaks internal monologue (#28864), and `/clear` docs don't mention context reset (#28847).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-18

## Today's Highlights

The dominant theme this cycle is MCP connectivity friction: organization-authorized models (Claude Sonnet 5, Opus 5, Kimi K3) are missing from the effective catalogue (#4390), and two separate OAuth discoverability regressions hit in 1.0.79 — Atlassian (#4480) and GitLab (#4439). On the session side, a memory-pressure watchdog is aggressively compacting at 23% context usage (#4506) and resumed sessions can carry stale connection IDs that break every subsequent prompt (#4505).

---

## Releases

No releases in the last 24 hours.

---

## Hot Issues

1. **#1481 — SHIFT + ENTER should spawn a line break** [CLOSED] 👍 17 · 28 comments
   The most-upvoted issue in this window. `SHIFT+ENTER` executes the prompt instead of inserting a newline, contradicting the universal chat-app convention. Closed — likely addressed in a recent patch.

2. **#4390 — Enabled organization models missing from catalogue (Claude Sonnet 5 / Opus 5 / Kimi K3)** [OPEN] 👍 7 · 8 comments
   Org-authorized Anthropic and other models are entirely absent from the CLI model picker, and selecting them errors as "disabled by your org." Blocks enterprise users from accessing models they've paid for.

3. **#4480 — Atlassian MCP OAuth fails with RFC 8414 issuer mismatch on 1.0.79** [OPEN] 👍 6 · 5 comments
   A clear regression from 1.0.71 → 1.0.79: the Atlassian MCP server's OIDC discovery returns an issuer that no longer matches the CLI's expectations. Undermines trust in patch-version stability for MCP-dependent workflows.

4. **#4506 — Memory-pressure watchdog force-compacts at 23% context** [OPEN]
   The process-level memory watchdog triggers compaction far below any context threshold, recovers a negligible fraction of tokens, and then loops until OOM. Long-running sessions are effectively trapped.

5. **#4505 — Resumed session retains stale connection item IDs** [OPEN]
   After an interrupted response, resuming the session yields `CAPIError: 400 input item ID does not belong to this connection` on every prompt. `/fork` also fails to recover. A serious reliability bug for async/long-running workflows.

6. **#4439 — GitLab MCP OAuth RFC 8414 issuer mismatch** [CLOSED] 👍 3 · 5 comments
   Same root cause as #4480 but for GitLab self-managed OAuth. Closed — a fix landed for this variant.

7. **#4513 — Plugin marketplace cache ignores `ref` across branches** [OPEN]
   Two projects using the same git-based marketplace source but different `ref` values collide on a single on-disk checkout. Developers pinning to feature branches get silently overwritten.

8. **#4512 — Local stdio MCP servers blocked when registry policy fetch fails** [OPEN]
   The CLI fails closed on *all* non-default MCPs — including user-owned `stdio` servers — when the managed policy cannot be fetched. No escape hatch exists for offline or restricted-network environments.

9. **#4509 — `--no-alt-screen` flag silently removed with no replacement** [OPEN] 👍 1
   The opt-out flag for alt-screen / fullscreen mode was removed without deprecation notice. Alt-screen is now unavoidable and reported broken by several users. Regression from prior behavior.

10. **#4211 — Copilot CLI cannot serialize BigInt in MCP responses** [OPEN] 👍 2 · 4 comments
    MCP servers returning `BigInt` values abort the entire execution with `TypeError: Do not know how to serialize a BigInt`. Blocks adoption of MCP tools that use 64-bit integers.

---

## Key PR Progress

1. **#4510 — Remove GitHub Copilot CLI documentation from README** [OPEN]
   Strips installation and usage guidance from the root README. Likely a housekeeping move to align with a documentation migration, but removes discoverability for new users.

*(Only 1 PR updated in the last 24h.)*

---

## Feature Request Trends

- **Non-interactive parity:** Users want `contextTier` (#4275), `enabledPlugins` (#4507), and model selection in ACP/`-p` mode to match interactive CLI capabilities.
- **Session durability:** Reliable remote-session restore (#4514), recovery from interrupted responses (#4505), and mid-session instruction reload (#4508) are all requested to make long-running sessions production-ready.
- **Plugin ecosystem maturity:** Dependency resolution between marketplace plugins (#4487), cache-keyed-by-ref (#4513), and org-managed policy escape hatches (#4512) point to a growing plugin ecosystem needing proper tooling.
- **Input ergonomics:** Keyboard navigation (#4313 — scrollable history) and the long-standing Shift+Enter fix (#1481) reflect expectations shaped by mainstream chat apps.

---

## Developer Pain Points

1. **MCP OAuth regressions are recurring.** Two distinct OAuth issuer-mismatch bugs hit in 1.0.79 (#4480, #4439), and a BigInt serialization gap (#4211) breaks tool responses. The policy-fail-closed behavior (#4512) compounds the frustration for offline users.
2. **Session state corruption after interruptions.** Stale connection IDs (#4505) and aggressive compaction loops (#4506) make long-running or network-flaky sessions unreliable — a core workflow for agents.
3. **Hidden or removed flags.** `--no-alt-screen` vanished without notice (#4509), and non-interactive mode ignores repo-level config (#4507). Developers report broken expectations when upgrading patch versions.
4. **Enterprise model access is broken.** Org-enabled models like Claude Sonnet 5 and Kimi K3 are invisible in the CLI (#4390), directly impacting teams relying on paid Copilot Business tiers.
5. **Plugin cache collisions.** Shared marketplace sources with different `ref` values overwrite each other (#4513), blocking parallel development across branches.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-18

## 1. Today's Highlights
The OpenCode ecosystem is navigating a wave of platform and billing transparency updates, with legacy endpoint retirements and Go gateway model mismatches drawing immediate community attention. Contributors are actively shipping core stability improvements, particularly around MCP token serialization, desktop IPC typing, and SQLite filesystem compatibility. Meanwhile, user feedback continues to push for smarter workflow automation and mobile-friendly UI refinements.

## 2. Releases
No new releases published in the last 24 hours.

## 3. Hot Issues
1. **[BUG: endpoint error](https://github.com/anomalyco/opencode/issues/43105)** — Legacy inference endpoint now returns `410 Gone`; community sharing cross-CLI workarounds. (15 comments, closed)
2. **[Opencode Stops Processing Requests Without Response](https://github.com/anomalyco/opencode/issues/32149)** — Critical execution stall after “thinking” phase; high frustration indicated by 6 👍 and 12 comments.
3. **[Plan Mode + Question tool can auto switch to Build mode](https://github.com/anomalyco/opencode/issues/7801)** — Highly upvoted workflow enhancement (32 👍) for

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026-08-18

## 1. Today's Highlights

Pi continues to tackle critical session and context management bugs, notably a high-impact auto-compaction failure on long-running agentic turns (17 👍) and a TUI full-screen flash issue in long transcripts, which has already landed a fix in PR #8253. The past 24h also saw a wave of provider-level improvements — Anthropic refusal fallbacks, OpenRouter reasoning-details round-tripping, and Qwen catalog alignment — alongside extensions-related reliability fixes for subagent flows and compaction failure events.

---

## 2. Releases

**No releases in the last 24 hours.**

---

## 3. Hot Issues

1. **[BUG] Auto-compaction never triggers after context exceeds 100%** [#6879](https://github.com/earendil-works/pi/issues/6879)
   The most upvoted open issue (17 👍). During a 2-hour agentic turn on GPT-5.6-sol, the context footer climbed past 100% and compaction never fired — only the API rejection at 373k tokens forced a reset. Community sees this as a reliability gap for long-running sessions.

2. **[BUG] Custom message injected mid-tool-batch breaks tool_calls→tool adjacency** [#8166](https://github.com/earendil-works/pi/issues/8166)
   Extensions calling `pi.sendMessage({ triggerTurn: false })` mid-turn corrupt the tool message ordering, causing every subsequent turn to fail with a 400 validation error. This directly impacts the extension ecosystem and is high-priority for plugin authors.

3. **[BUG] TUI full-screen flash in long transcripts** [#8281](https://github.com/earendil-works/pi/issues/8281)
   In sessions with 10k+ lines, any render above the viewport triggers a full-screen clear and redraw, causing visible flicker. A fix (PR #8253) was already merged the same day.

4. **[BUG] Edit tool crashes TUI on large diff rendering** [#8036](https://github.com/earendil-works/pi/issues/8036)
   A ~14.5 MB diff from HTML files crashes the interactive TUI despite the edit succeeding server-side. Limits usability for codebases with large generated files.

5. **[BUG] TUI `fullRender` crashes with RangeError on oversized output** [#8028](https://github.com/earendil-works/pi/issues/8028)
   A video production agent processing many images hits the V8 string-length limit, causing a hard crash. Highlights scaling concerns for media-heavy workflows.

6. **[BUG] Very slow prompt editor on large buffers** [#8029](https://github.com/earendil-works/pi/issues/8029)
   Arrow-key navigation degrades linearly with buffer size — 7000 lines → 1650ms per keystroke. Painful for long conversation dumps pasted into the prompt box.

7. **[BUG] Local providers can overflow between tool turns** [#8229](https://github.com/earendil-works/pi/issues/8229)
   Pi appends a large tool result and fires the next provider call before post-run compaction, causing llama.cpp to reject the oversized request. A race condition between tool result buffering and compaction scheduling.

8. **[BUG] Bedrock Converse rejects root-composed tool schemas without `type: object`** [#8279](https://github.com/earendil-works/pi/issues/8279)
   Bedrock now strictly requires `type: object` on the root of tool input schemas. Extensions that generate schemas without this field now fail at runtime — a breaking change for some plugin authors.

9. **[BUG] Pi crashes when tmux resizes pane to 1 column** [#8252](https://github.com/earendil-works/pi/issues/8252)
   The spinner's width check throws when the terminal is 1 column wide, causing a hard exit. Recurring issue for tmux power users.

10. **[BUG] `detectInstallMethod` mislabels non-pnpm installs under PNPM_HOME** [#7756](https://github.com/earendil-works/pi/issues/7756)
    Any install path containing `/pnpm/` is assumed to be a pnpm install, even when only the global bin directory is shared. Leads to incorrect "not managed by a package manager" errors.

---

## 4. Key PR Progress

1. **#8253** — *fix(tui): avoid full-screen flashing in long transcripts* — Differential rendering now only clears the visible viewport instead of the entire screen. [PR #8253](https://github.com/earendil-works/pi/pull/8253)

2. **#8258** — *fix(ai): anthropic refusal error and fallbacks* — Adds Anthropic's `allowed_fallback_models` metadata to the model registry, enabling compaction to fall back to an allowed model when a refusal is returned. [PR #8258](https://github.com/earendil-works/pi/pull/8258)

3. **#8246** — *fix(ai): openai completions reasoning details round-trip* — Preserves `reasoning_details` (signed text and summary entries) through assistant-message replay, fixing a gap where OpenRouter-served reasoning was silently dropped. [PR #8246](https://github.com/earendil-works/pi/pull/8246)

4. **#8275** — *feat(ai): generalize openai-completions thinking token budget fields* — Extends `thinkingTokenBudgetField` to cover Qwen/SGLang (`thinking_budget`) and llama.cpp (`thinking_budget_tokens`), not just vLLM's `thinking_token_budget`. [PR #8275](https://github.com/earendil-works/pi/pull/8275)

5. **#8255** — *fix(coding-agent): load nested markdown skills* — Fixes skill discovery to recognize `.md` skill files in subdirectories (e.g. `~/.agents/skills/third-party/child-skill.md`), addressing #6479. [PR #8255](https://github.com/earendil-works/pi/pull/8255)

6. **#8262** — *feat(coding-agent): dispatch hooks on every turn-start path* — Ensures `sendCustomMessage(triggerTurn: true)` fires the `input` and `before_agent_start` hooks, closing a gap that left some programmatic turns unmonitored by extensions. [PR #8262](https://github.com/earendil-works/pi/pull/8262)

7. **#8250** — *fix(coding-agent): make subagent progress and failures reliable* — Fixes premature "done" signals, lost failure details, and oversized tool results in the shipped subagent example. [PR #8250](https://github.com/earendil-works/pi/pull/8250)

8. **#8241** — *fix(extensions): emit compaction failed for extensions* — Adds a `session_compact_failed` event so extensions can react to compaction failures instead of only seeing silent `compaction_end` errors. [PR #8241](https://github.com/earendil-works/pi/pull/8241)

9. **#8240** — *fix(ai): align Qwen Token Plan model catalogs* — Unifies the text-model allowlist across `qwen-token-plan` and `qwen-token-plan-cn`, exposing the same 8 models including the new DeepSeek variants. [PR #8240](https://github.com/earendil-works/pi/pull/8240)

10. **#8120** — *feat(coding-agent): experimental append compaction* — Introduces an append-mode compaction path (behind `PI_EXPERIMENTAL=1`) that reuses the active system prompt and tools so compacted prefixes can leverage provider prompt caches. [PR #8120](https://github.com/earendil-works/pi/pull/8120)

---

## 5. Feature Request Trends

- **Multimodal prompt expansion** — Issue #3200 requests forwarding video/audio alongside images in the `prompt` RPC, driven by growing multimodal model support (Gemma 4, GPT-4o).
- **Configurable TUI aesthetics** — Issue #6757 asks for vertical padding control (`outputPadY`) symmetric to existing horizontal padding, reflecting continued TUI polish demand.
- **Provider-side reasoning control** — Multiple issues (#7994, #7995, #8275) and PRs target finer-grained control over thinking/reasoning token budgets and caching across OpenAI, Anthropic, and OpenRouter surfaces.
- **Session resilience** — Issue #8277 proposes auto-resume after provider rate-limit resets, and #8229 highlights the need for compaction-before-request guards, both pointing to a community appetite for more fault-tolerant long-running sessions.
- **Extension observability** — The `session_compact_failed` event (PR #8241) and hook coverage (PR #8262) indicate extensions are asking for more lifecycle signals.

---

## 6. Developer Pain Points

- **Long-session reliability** — Compaction not triggering before context overflow (#6879, #8229) and V8 string-limit crashes (#8028) are the top friction points for agents running multi-hour turns.
- **Extension correctness** — Mid-turn message injection breaking tool adjacency (#8166), missing hooks on programmatic turns (#8262), and incomplete compaction-failure events (#8241) all make extension development error-prone.
- **TUI stability at scale** — Full-screen flash (#8281), large-diff crashes (#8036), slow prompt editing (#8029), and 1-column tmux crashes (#8252) show the TUI struggles under extreme terminal conditions.
- **Provider schema drift** — Bedrock's new strict schema requirement (#8279) and OpenRouter's missing Anthropic cache-control support (#7995) require frequent adapter updates as upstream APIs evolve.
- **Cross-platform quirks** — XDG config placement on Linux (#534), Windows `find` process hang on large directories (#8282), and Shift+Enter in KDE Konsole (#8278) continue to surface terminal-environment-specific bugs.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-18

## 1. Today's Highlights
Qwen Code v0.21.13 ships with targeted UX upgrades: the Web Shell composer now accepts drag-and-drop or pasted text files as named attachments alongside images, and users can fork conversations from any specific Assistant response. The release is currently locked into rigorous end-to-end validation, with SWE-bench Verified and Terminal-Bench 2.0 smoke tests reporting successful outcomes. Community discussion is also active around stabilizing CLI clipboard regressions, refining daemon resource bounding, and hardening the autofix/review pipeline.

## 2. Releases
- **v0.21.13** ([GitHub](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.13))
  Primary

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-18

## 1. Today's Highlights

CodeWhale v0.9.9 shipped yesterday as a **"truth-and-resilience" release**, fixing a critical shell-tool wedge bug, hardening unverified context windows, and stabilizing session survival under resource pressure. On top of that, several follow-on fixes landed the same day — durable approval persistence, web tool result compaction, and model-catalog pricing currency — keeping the project's momentum strong heading into the v0.9.8/v0.9.9 transition cycle.

---

## 2. Releases

**v0.9.9** (PR [#5476](https://github.com/Hmbown/CodeWhale/issues/5476)) — Released 2026-08-17

Key changes:
- **Shell tool resilience (#5465):** The shell tool can no longer wedge a session when the host runs out of disk or file descriptors — a bug that previously took down the maintainer's own release session.
- **Truthful context & pricing labels:** Unverified context windows, output ceilings, and telemetry defaults are now explicitly labeled rather than silently guessed.
- **Contributor follow-ons:** PRs [#5474](https://github.com/Hmbown/CodeWhale/pulls/5474) (compact noisy web results), [#5475](https://github.com/Hmbown/CodeWhale/pulls/5475) (fixed model casing), [#5480](https://github.com/Hmbown/CodeWhale/pulls/5480) (live `/rc` session link), and [#5484](https://github.com/Hmbown/CodeWhale/pulls/5484) (ambient ocean scene for DSH) were folded into the release addendum.
- **Web copy overhaul (#5483):** Customer-facing copy on codewhale.net rewritten to read as a product site.
- **rusqlite bump (#5391):** Upgraded from 0.39.0 → 0.40.2.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#5424](https://github.com/Hmbown/CodeWhale/issues/5424) | v0.9.7: Codewhale TUI crashing | Users report the TUI exiting spontaneously after ~1 min of inactivity post-prompt — a regression affecting v0.9.7 stability. |
| [#2369](https://github.com/Hmbown/CodeWhale/issues/2369) | CodeWhale Config Paths Fragmented Across OS and Cygwin | Config and secret paths diverge on Windows/Cygwin; legacy migrations can silently break. 8 comments show sustained friction. |
| [#5056](https://github.com/Hmbown/CodeWhale/issues/5056) | Flaky verifier background tests | Subagent verifier tests under full-suite parallelism remain flaky (`:1302`, `:1490`). The `/workspace-sensitive` fixtures also write inconsistent state. |
| [#5324](https://github.com/Hmbown/CodeWhale/issues/5324) | Simplify the 32-field agent tool schema | The model-facing `agent` tool schema has 32 optional properties across 8 actions — models error on it. Closing it reduces parser surface and improves reliability. |
| [#1425](https://github.com/Hmbown/CodeWhale/issues/1425) | Large text processing causes session hang | Agent spawn with 10 parallel sub-agents on a 3M-character novel times out on `agent_wait`, leaving sessions deadlocked. |
| [#5123](https://github.com/Hmbown/CodeWhale/issues/5123) | Agent spawn surface has too many knobs | Builder agents self-BLOCK after starting — a live dogfood failure on v0.9.4 where delegate tool contracts clash with runtime capabilities. |
| [#1651](https://github.com/Hmbown/CodeWhale/issues/1651) | VS Code crashes with YOLO Agent running tests | YOLO Agent autonomously executing tests in the integrated terminal causes VS Code to exit — a UX-critical reliability bug. |
| [#1829](https://github.com/Hmbown/CodeWhale/issues/1829) | SSH exit code 255 in sandbox | Shell sandbox appears to block outbound TCP 22, making SSH unusable inside the TUI — a common dev workflow blocker. |
| [#5437](https://github.com/Hmbown/CodeWhale/issues/5437) | Formalize status-bar color grammar | Post-design-review proposal to codify the TUI's color vocabulary and surface repo/worktree state explicitly in the status bar. |
| [#5482](https://github.com/Hmbown/CodeWhale/issues/5482) | EPIC: Localize docs to Chinese | Growing Chinese user base faces a language barrier; machine translation introduces errors and source docs are already stale. |

---

## 4. Key PR Progress

| # | Title | Status |
|---|-------|--------|
| [#5492](https://github.com/Hmbown/CodeWhale/pulls/5492) | Keep configured skill prompts stable in model-facing catalog | Open — stabilizes native skill discovery by scoping to `<configured-skills>`. |
| [#5494](https://github.com/Hmbown/CodeWhale/pulls/5494) | Configurable auto-router classifier timeout | Open — replaces hardcoded 4s timeout with `[auto.router] timeout_secs`. |
| [#5493](https://github.com/Hmbown/CodeWhale/pulls/5493) | Classify OrcaRouter as aggregator billing surface | Open — fixes mislabel that routed OrcaRouter to first-party PAYG instead of aggregator. |
| [#5491](https://github.com/Hmbown/CodeWhale/pulls/5491) | Persist approval outcomes before execution | Open — implements durable approval logging; closes [#5360](https://github.com/Hmbown/CodeWhale/issues/5360). |
| [#5490](https://github.com/Hmbown/CodeWhale/pulls/5490) | Route shared components' locale picks through `pickText` | Closed — consolidates 10 inline locale ternaries to `pickText()` calls; closes part of [#5337](https://github.com/Hmbown/CodeWhale/issues/5337). |
| [#5488](https://github.com/Hmbown/CodeWhale/pulls/5488) | Move docs shell onto the dictionary spine | Closed — fixes 8 partial locales (ja/vi/ko/ru/uk/es/pt-BR/id) reading English on the docs portal hero. |
| [#5486](https://github.com/Hmbown/CodeWhale/pulls/5486) | Hide session metrics strip on compact rows | Closed — below 60 columns the metrics strip is now suppressed alongside the phase strip. |
| [#5485](https://github.com/Hmbown/CodeWhale/pulls/5485) | Bring first-party model rows and pricing current | Closed — model catalog prices verified against official pages as of 2026-08-17. |
| [#5484](https://github.com/Hmbown/CodeWhale/pulls/5484) | Ambient ocean scene for DSH | Closed — adds whale/glyph-fish animated background to the DeepSeek Harness web UI. |
| [#5483](https://github.com/Hmbown/CodeWhale/pulls/5483) | De-slop the website copy | Closed — product-site voice rewrite for codewhale.net; new voice sheet in `docs/design/WEB_VOICE.md`. |

---

## 5. Feature Request Trends

- **Plugin ecosystem maturity (#5311):** Federated plugin marketplaces and a first-class Kimi-level plugin system are top-of-mind for the v0.9.8 cycle.
- **Multimodal agent tools (#5102):** First-class screenshot/image viewing for agents — compress-and-understand rather than path-luck file reads.
- **MCP capability metadata (#4170):** Structured capability declarations so tool discovery and the UI can distinguish features without prose scraping.
- **Discoverability overhaul (#5439, #5442):** Advanced commands (`/workflow`, `/goal`, `/auto`) are shipped but buried; a palette-root redesign is requested.
- **Third-party model config templates (#5350):** Pre-built configs for OpenCode Zen, Agnes, Sensenova, etc. with one-click "test connection" and auto-retry.
- **bwrap sandbox expansion (#5410):** Allow configurable additional bind roots so tools like Zig linker and `/dev/null` redirection work inside the sandbox.

---

## 6. Developer Pain Points

1. **Config fragmentation across environments** — Windows/Cygwin path divergence and silent migration failures (#2369) create repro headaches that persist across versions.
2. **Test flakiness under parallelism** — Verifier background tests (#5056) and parallel-load flakes (#5355) remain unresolved, slowing CI turnover.
3. **Sandbox network restrictions** — SSH/TCP 22 blocking (#1829) and bwrap bind-root limits (#5410) constrain real-world dev workflows.
4. **Unverified pricing/data surface** — Models show `unpriced` or stale context windows until manually corrected (#5241, #5239), eroding trust in the dashboard.
5. **Agent tool schema bloat** — The 32-field agent schema (#5324) and overly knobby spawn surface (#5123) cause model parsing errors and self-blocks in production.
6. **Web localization gaps** — Non-English routes still have broken clickable controls (#5290) and inconsistent locale picking (#5337), even after partial fixes.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*