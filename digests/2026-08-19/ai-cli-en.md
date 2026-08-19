# AI CLI Tools Community Digest 2026-08-19

> Generated: 2026-08-19 01:40 UTC | Tools covered: 10

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
**Date:** 2026-08-19 | **Analyst:** Agnes-2.0-Flash

---

## 1. Ecosystem Overview

The AI CLI tool landscape is entering a phase of rapid maturation, with the major players shipping substantive feature releases this cycle while community pain points converge around agent reliability, session management, and platform-specific regressions. OpenAI Codex, Gemini CLI, and DeepSeek TUI all shipped releases today, reflecting aggressive iteration cadences, while the open-source tools (OpenCode, Pi, Qwen Code) are investing heavily in architectural hardening—session sync engines, witness forms, and compaction improvements. A clear theme emerges: the battle is shifting from raw model access toward agent orchestration quality, cross-session collaboration, and trust/security boundaries.

---

## 2. Activity Comparison

| Tool | Issues (24h) | PRs (24h) | Release |
|------|-------------|-----------|---------|
| **Claude Code** | 10 hot | 1 | v2.1.235 ✅ |
| **OpenAI Codex** | 10 hot | ~10 | v0.148.0 ✅ |
| **Gemini CLI** | 10 hot | ~10 | v0.56.0-nightly ✅ |
| **GitHub Copilot CLI** | 10 hot | 1 | v1.0.81-1 ✅ |
| **Kimi Code CLI** | 2 | 2 | None |
| **OpenCode** | 10 hot | ~10 | None |
| **Pi** | 10 hot | ~10 | None |
| **Qwen Code** | 10 hot | ~10 | v0.21.14-preview.0 ✅ |
| **DeepSeek TUI** | 9 hot | ~10 | v0.9.9 ✅ |
| **Grok Build** | 0 | 0 | None |

*Issues count reflects hot/updated issues in the reporting window. PR counts reflect opened/updated PRs.*

---

## 3. Shared Feature Directions

| Theme | Tools Involved | Specific Needs |
|-------|---------------|----------------|
| **Multi-agent / cross-session collaboration** | Qwen Code, Gemini CLI, Claude Code, OpenCode | Peer-session messaging, leader-worker coordination, shared agent boards, subagent lifecycle management |
| **Session management & persistence** | OpenAI Codex, Pi, OpenCode, Qwen Code, Claude Code | Export/fork sessions, deterministic sync engines, archival reliability, transcript portability across hosts |
| **Agent reliability & observability** | Gemini CLI, Pi, Qwen Code, OpenCode | Subagent hang detection, turn-limit recovery, stream inactivity watchdogs, empty-response handling |
| **Context efficiency** | Gemini CLI, Pi, OpenCode, Qwen Code | AST-aware codebase navigation, compaction thresholds during agentic runs, context-cache invalidation, per-result read budgets |
| **MCP / extensibility robustness** | GitHub Copilot CLI, OpenAI Codex, Pi, OpenCode | OAuth bridging between GUI/CLI, process lifecycle management, trust-boundary enforcement for plugin and stdio servers |
| **Sandboxing & security hardening** | Claude Code, OpenAI Codex, Gemini CLI, Pi | Filesystem sandbox reliability, trusted-code-path enforcement, subprocess credential protection, policy compliance |
| **Billing / usage transparency** | Claude Code, OpenCode, GitHub Copilot CLI | Usage forecasting, post-incident reconciliation, per-agent metrics, free-tier cap bugs affecting paying users |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI | Kimi Code CLI |
|-----------|-------------|--------------|------------|-------------------|----------|-----|-----------|--------------|---------------|
| **Primary focus** | General-purpose CLI with Cowork VMs | IDE-integrated + mobile control layer | Agent-centric with SSR subagents | Enterprise GitHub-integrated workflows | Open-source TUI with provider flexibility | Extension-heavy, lifecycle-control oriented | Multi-session coordination + review pipelines | Rebranded DeepSeek with crate decomposition | Niche: third-party provider compatibility |
| **Target users** | Developers, teams (multi-account demand) | VS Code users, mobile controllers | Power users, agent workflow builders | GitHub Enterprise teams | Open-source adopters, self-hosted LLM users | Extension authors, custom workflow builders | Multi-agent teams, CI/CD reviewers | CN market, rebranding adopters | OpenAI-compatible backend users |
| **Technical approach** | Rust-based TUI, prompt-cache, spellcheck | Rust, trusted-code-path enforcement | TypeScript, subagent recovery, loop detection | TypeScript, MCP/OAuth lifecycle focus | Rust/Go, deterministic session sync engine | Rust, extension hooks, compaction | Rust, transcript contracts, witness forms | Rust, SSE UTF-8 handling, skill budgets | Minimal: provider fidelity focus |
| **Key differentiator** | Multi-account management (#18435, 732 👍) | Security-first trust model, browser control | Agent self-awareness, AST-aware tools | Per-agent reasoning effort, enterprise model catalogue | Zen/Go subscription model, provider-agnostic | Deep extension hooks, stream watchdogs | Review pipeline governance, team coordination | Crate decomposition, i18n expansion | Quant/trading domain benchmarks |

---

## 5. Community Momentum & Maturity

**High momentum, rapid iteration:**
- **OpenAI Codex** and **Gemini CLI** are shipping dense release cycles with significant PR volume (~10 each), indicating strong engineering velocity. Both are actively addressing agent reliability pain points.
- **DeepSeek TUI** (now CodeWhale) is undergoing a major architectural rebrand with active crate decomposition and i18n expansion, signaling a transitioning but energetic community.
- **Qwen Code** shows maturity in its review pipeline (witness forms, run disciplines) and multi-agent coordination work, with a notable 500/500 SWE-bench Verified result.

**Steady, focused iteration:**
- **Pi** demonstrates sophisticated extension-hook design and session-persistence hardening, with community proposals for retry classification and provider lineage auditing.
- **OpenCode** is investing in foundational architecture (deterministic session sync engine, stream file mutation previews) rather than feature bloat.

**Mature but constrained:**
- **Claude Code** has the strongest single feature signal (#18435 with 732 👍) but low PR volume (1), suggesting the team is focused on a smaller set of high-impact items while community frustration builds around Windows MSIX, Cowork regressions, and billing trust.
- **GitHub Copilot CLI** shows enterprise-grade concerns (MCP OAuth, sandbox policy regression) but minimal PR activity, indicating potential capacity constraints.

**Emerging / low volume:**
- **Kimi Code CLI** has the smallest community footprint (2 issues, 2 PRs) but shows early signals of domain-specific benchmarking and knowledge-plane feature development.

---

## 6. Trend Signals

| Trend | Evidence | Developer Implication |
|-------|----------|----------------------|
| **Agent reliability is the #1 competitive frontier** | Subagent hangs (Gemini #21409), false GOAL success (#22323), turn-limit masking, stream hangs across all tools | Tool selection should prioritize agent observability and graceful degradation, not just model quality |
| **Cross-session collaboration is becoming first-class** | Qwen Code's peer-session design, agent board, team health notifications; Gemini's cross-session messaging RFC | Multi-agent workflows will soon be a differentiator—evaluate tool support for session discovery and messaging |
| **Security trust boundaries are tightening** | Codex's burst of 8+ security PRs (worktree trust, hook scripts, OAuth, stdio sandboxes); Claude Code's git-origin egress concern | Expect stricter default policies; test your workflows against tightened trust models before adoption |
| **Platform-specific regressions are the dominant pain** | Windows MSIX updates (Claude), Intel Mac Cowork VM (Claude), Windows browser control (Codex), WSL detection (Codex), Windows `find` hangs (Pi) | Multi-platform teams should monitor release notes for platform-specific regressions; consider CI against target platforms |
| **Billing/usage transparency erodes trust quickly** | Claude Code July 17 incident + August charges (~$1,600), OpenCode Zen cap bugs, GitHub Copilot per-agent metrics | Tools with transparent per-agent usage and clear reconciliation tools (Copilot's `--usage-output-file`) reduce operational risk |
| **Open-source tools are building enterprise-grade ops** | Qwen Code's witness forms and review governance, OpenCode's deterministic session sync, Pi's provider lineage auditing | Open-source CLI tools are closing the reliability gap with proprietary offerings—viable for production with appropriate guardrails |
| **Context efficiency is a growing concern** | AST-aware navigation (Gemini), compaction thresholds (Pi), context cache invalidation (OpenCode/Claude), per-result read budgets (DeepSeek) | Tools that reduce token noise through structural awareness will gain adoption in large-codebase scenarios |
| **Provider-agnosticism is a community demand** | Kimi Code's OpenAI-compatible provider friction, Pi's OpenAI-compatible onboarding, OpenCode's Qwen sampling fix | Multi-provider strategies require tools that don't assume a single backend—evaluate provider flexibility before committing |

---

*Report generated from community digest data as of 2026-08-19. Analysis reflects open issue trends, PR activity, and release patterns across 9 AI CLI tools.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills — Community Highlights Report
*Data as of 2026-08-19 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

| # | Skill / PR | Comments | Status | Description |
|---|-----------|----------|--------|-------------|
| 1 | [#492](https://github.com/anthropics/skills/issues/492) — Trust boundary abuse via namespace impersonation | 43 | Open | Community skills are being distributed under the `anthropic/` namespace, impersonating official Anthropic skills. Users may grant elevated permissions to malicious skills believing them to be official. |
| 2 | [#228](https://github.com/anthropics/skills/issues/228) — Org-wide skill sharing | 16 | Open | Request to share skills directly within an organization without manual file exchange. Currently users must download `.skill` files and redistribute them via Slack/Teams. |
| 3 | [#556](https://github.com/anthropics/skills/issues/556) — `run_eval.py` never triggers skills (0% recall) | 12 | Open | Multiple independent reproductions confirm `claude -p` never triggers skill commands during evaluation, rendering the skill-creator optimization loop broken. |
| 4 | [#62](https://github.com/anthropics/skills/issues/62) — Skills disappear after file rename | 10 | Open | Skills vanish from Claude Code after a file in the download folder is renamed; users report losing ~12 custom skills. |
| 5 | [#1329](https://github.com/anthropics/skills/issues/1329) — `compact-memory` skill proposal | 9 | Open | Proposes a skill using symbolic notation to compress agent state/notes, reducing context consumed by long-running agent sessions. |
| 6 | [#189](https://github.com/anthropics/skills/issues/189) — Duplicate skills from `document-skills` + `example-skills` | 6 | Open | Two plugins install identical skill content, causing duplicate skills in the context window. |
| 7 | [PR #1298](https://github.com/anthropics/skills/pull/1298) — Fix `run_eval.py` recall = 0% | — | Open | Installs the eval artifact as a real skill; fixes Windows stream reading, trigger detection, and parallel workers. Directly addresses #556. |
| 8 | [PR #83](https://github.com/anthropics/skills/pull/83) — `skill-quality-analyzer` + `skill-security-analyzer` | — | Open | Meta-skills that evaluate other skills across five quality dimensions (structure, documentation, examples, security, trigger accuracy). |

---

## 2. Community Demand Trends

From open and closed issues, the most-anticipated new skill directions are:

- **Org-wide skill collaboration** (#228, 16 comments, 8 👍) — Share skills across teams without manual file transfer; a shared skill library is the #1 feature request.
- **Agent state & memory efficiency** (#1329) — Compact, symbolic notation for long-running agent memory to reduce context bloat.
- **Quality & security gates for skills** (#83, #1385) — Pre-delivery verification pipelines: mechanical file checks, reasoning audits, and adversarial review across the full session lifecycle.
- **Enterprise platform coverage** (#568) — Broad platform skills (ServiceNow, SAP) that act as comprehensive assistants rather than narrow scripting helpers.
- **Code review & testing guidance** (#723) — Full-stack testing patterns (unit, React, philosophy) reflecting strong demand for testing best-practice skills.
- **Document generation reliability** (#12, #541, #514) — Ongoing pain points around DOCX whitespace corruption, tracked-change ID collisions, and typographic quality control.

---

## 3. High-Potential Pending Skills

These active PRs are unresolved and address high-impact bugs or new capabilities — strong candidates for near-term merge:

| PR | Skill / Fix | Why It May Land Soon |
|----|-------------|---------------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `run_eval.py` recall fix + Windows stream reading | Fixes a critical evaluation loop bug with 10+ independent reproductions; directly resolves #556. |
| [#1099](https://github.com/anthropics/skills/pull/1099) | `run_eval.py` Windows crash fix | Part of the same Windows compat fix chain; blocks skill-creator on Windows. |
| [#1050](https://github.com/anthropics/skills/pull/1050) | Windows `subprocess.Popen` + encoding fixes | 1-line changes that unblock `run_loop.py` on Windows 11. |
| [#568](https://github.com/anthropics/skills/pull/568) | `servicenow` platform skill | Comprehensive ServiceNow skill covering ITSM, ITOM, SecOps, FSM, CSDM — actively updated (last 2026-08-12). |
| [#83](https://github.com/anthropics/skills/pull/83) | `skill-quality-analyzer` + `skill-security-analyzer` | Meta-skills for skill evaluation; fills a clear gap in the skill-creator workflow. |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` — mechanical verification + reasoning quality gate | Covers pre-delivery checks across any project/stack; complements #83. |
| [#514](https://github.com/anthropics/skills/pull/514) | `document-typography` skill | Addresses universal pain point (orphans, widows, numbering) in AI-generated documents. |
| [#539](https://github.com/anthropics/skills/pull/539) | YAML unquoted-description warning | Prevents silent truncation in skill frontmatter; small but high-impact validation fix. |
| [#541](https://github.com/anthropics/skills/pull/541) | DOCX tracked-change `w:id` collision fix | Fixes document corruption with existing bookmarks; directly related to issue #12. |

---

## 4. Skills Ecosystem Insight

The community's most concentrated demand is **trustworthy, shareable skill infrastructure** — org-wide distribution, namespace security, and reliable evaluation tooling — rather than any single domain-specific skill.

---



# Claude Code Community Digest — 2026-08-19

---

## 1. Today's Highlights

Claude Code v2.1.235 shipped with a new `spellcheck` prompt input feature and fixes for whole-prompt-cache invalidation during language server reconnects. The community is mobilizing around a major multi-account management feature request (#18435, 732 👍), while a wave of Windows and macOS Cowork regressions surfaced after the Aug 18 bundle update, alongside ongoing billing disputes from the July 17 incident.

---

## 2. Releases

**v2.1.235** — [GitHub](https://github.com/anthropics/claude-code)

- **New:** Optional `spellcheck` setting underlines misspelled words in prompt input as you type, leveraging installed `aspell`, `hunspell`, or `ispell`.
- **Fix:** Whole-prompt-cache invalidation now correctly handles language server disconnect/reconnect mid-session.
- **Fix:** Nested m… (changelog truncated in release notes).

---

## 3. Hot Issues

| # | Title | Comments | 👍 | Why It Matters |
|---|-------|----------|----|----------------|
| [#18435](https://github.com/anthropics/claude-code/issues/18435) | Manage multiple Claude accounts with easy profile switching in Desktop | 167 | 732 | The single most-watched feature request — users across personal/professional accounts need seamless switching without re-authentication. |
| [#2254](https://github.com/anthropics/claude-code/issues/2254) | Disable the welcome banner | 36 | 107 | Power users consistently want a quieter TUI; the welcome screen is seen as terminal real estate waste. |
| [#76357](https://github.com/anthropics/claude-code/issues/76357) | Windows MSIX: update fails — "Another program is currently using this file" | 26 | 6 | Every update on Windows MSIX requires a reboot; a persistent blocker for enterprise rollout. |
| [#21108](https://github.com/anthropics/claude-code/issues/21108) | Claude accesses git origin server on startup before any commands | 15 | 17 | Security-conscious users flag unauthorized network egress at process launch — a trustboundary concern. |
| [#81703](https://github.com/anthropics/claude-code/issues/81703) | July 17 mass billing incident: $604.71 unauthorized recharges | 12 | 0 | Follow-up to Anthropic's acknowledged billing fault; users report unreconciled charges and seek formal resolution. |
| [#87503](https://github.com/anthropics/claude-code/issues/87503) | Cowork VM connection timeout on Intel Mac after 1.32352.0 update | 11 | 0 | Regression introduced in the Aug 18 bundle — VM guest never connects, breaking Cowork entirely on x86_64 Macs. |
| [#87512](https://github.com/anthropics/claude-code/issues/87512) | Cowork VM: guest kernel does not enumerate NVMe disks on Intel Mac | 10 | 0 | Second Cowork Intel Mac regression; deeper hardware-level issue suggesting the new bundle broke virtio/NVMe passthrough. |
| [#73468](https://github.com/anthropics/claude-code/issues/73468) | macOS sandbox unusable with many git worktrees (ARG_MAX exceeded) | 9 | 5 | The Seatbelt profile passed inline via `sandbox-exec -p` blows past OS limits in worktree-heavy repos — sandbox becomes 100% broken. |
| [#78264](https://github.com/anthropics/claude-code/issues/78264) | Custom session titles overridden by AI-generated titles; /resume forks duplicates | 8 | 3 | Named sessions become unfindable — a usability regression for users relying on `/resume` to pick up context. |
| [#87805](https://github.com/anthropics/claude-code/issues/87805) | Jammed background tasks + Remote Control reconnect loops silently consume usage after forced token rotation | 2 | 0 | Auto-update triggers OAuth rotation, invalidating all sessions; stuck tasks and reconnect loops burn through the usage window unseen. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| [#41611](https://github.com/anthropics/claude-code/pull/41611) | Add the missing source to Claude Code | Open (stalled since Mar 2026) | Contributor added a missing source file; no merge activity in 5 months — likely needs rebase or maintainer review. |

*Note: Only 1 PR was updated in the last 24h. The repo is currently quiet on incoming contributions.*

---

## 5. Feature Request Trends

- **Multi-account & profile management** — Dominant theme (#18435, 732 👍). Users want profile switching without full re-auth, especially for teams sharing machines.
- **UI quieting & customization** — Disable welcome banner (#2254), interlinear gloss for non-native speakers (#87810), and better session title control (#78264) all point to a demand for a less opinionated, more customizable interface.
- **Cowork experience improvements** — Multi-choice question widget UX (#87807), worktree setup hooks (#27744, now closed), and NVMe/sandbox stability on Intel Macs are the top Cowork concerns.
- **Auto-memory provenance** — #87783 highlights a gap: memory notes persist claims but not source bindings, making it impossible to distinguish drifted vs. valid notes.
- **Billing transparency** — Recurring billing issues (#81703, #83062) signal demand for clearer usage forecasting and post-incident reconciliation tools.

---

## 6. Developer Pain Points

1. **Windows MSIX update reliability** — The "file in use" error on every update (#76357) and daemon refresh hanging ~9h before falling back to a non-existent keychain (#87812) make Windows the hardest platform to maintain.
2. **Cowork regressions on Intel Macs** — Two critical bugs (#87503, #87512) emerged from the Aug 18 bundle, breaking VM connectivity and NVMe enumeration on x86_64 Macs. These are blockers for any Intel Mac Cowork user.
3. **macOS sandbox ARG_MAX blowout** — In worktree-heavy repos, the inline Seatbelt profile exceeds the OS argument limit (#73468), completely disabling sandboxing with no workaround.
4. **Silent usage drain after token rotation** — Auto-updates can invalidate all sessions at once (#87805), and stuck background tasks + reconnect loops silently consume the entire usage window before the user notices.
5. **Cross-session messaging fragility** — Multiple agent-related bugs (#87694, #86608, #87323) show that `send_message`, inbox binding, and transcript inclusion are all unreliable — a sign the agent cross-session subsystem is still maturing.
6. **Billing incidents eroding trust** — The July 17 mass-billing event and an August 1 incident (#81703, #83062) resulting in ~$1,600 in unexpected charges have left a lasting impression; users are filing detailed public reports rather than closing tickets quietly.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex Community Digest — 2026-08-19

---

## 1. Today's Highlights

The Codex team shipped **v0.148.0** with highly requested TUI features: Markdown export via `/export`, session forking with `codex exec fork`, and draft-prompt support during initialization. Security remains a dominant focus, with a burst of fixes today tightening trusted-code-path enforcement across git worktrees, hook scripts, MCP stdio servers, and OAuth credential handling. Community bug reports are heavily concentrated on Windows browser-control failures and WSL integration issues.

---

## 2. Releases

### `rust-v0.148.0` — Stable
**Key changes:**
- **`/export`** — Export complete TUI conversations to Markdown, either to the clipboard or a new file. ([#37358](https://github.com/openai/codex/issues/37358))
- **`codex exec fork`** — Fork active sessions and archive/restore them from the TUI resume picker. ([#37367](https://github.com/openai/codex/issues/37367), [#37369](https://github.com/openai/codex/issues/37369), [#37371](https://github.com/openai/codex/issues/37371))
- **Draft prompts** — Start composing prompts while the TUI initializes, reducing idle wait time.

> Also released: `v0.148.0-alpha.23` and `v0.148.0-alpha.22` (alpha previews), plus `v0.149.0-alpha.1`.

---

## 3. Hot Issues

### 1. Browser plugin initialization fails — Trusted RPC not in trusted code path [#39136](https://github.com/openai/codex/issues/39136)
Windows users report the in-app browser can't initialize after the latest release. 63 comments, 21 👍. Appears tied to tightened trust checks. Multiple related reports opened the same day ([#39173](https://github.com/openai/codex/issues/39173), [#39318](https://github.com/openai/codex/issues/39318)), suggesting a regression in v26.814.

### 2. VS Code extension opens blank webview on Linux [#32041](https://github.com/openai/codex/issues/32041)
Extension v26.5707.* shows a blank webview; rolling back to v26.5623 works but loses features. 56 comments, 3 👍. Long-running issue affecting Linux IDE users.

### 3. Scope VS Code chats to current workspace/project [#25319](https://github.com/openai/codex/issues/25319)
Feature request to limit chat history to the active workspace. 33 comments, **65 👍** — one of the most upvoted open issues. Strong community signal for context-scoping.

### 4. Copy/Export Message as Markdown [#2880](https://github.com/openai/codex/issues/2880)
Now closed — the `/export` command in v0.148.0 directly addresses this request. 31 comments, **78 👍**. Community appreciation for finally getting this built-in.

### 5. Windows/WSL: valid repos marked as non-Git, "Git is unavailable" [#35119](https://github.com/openai/codex/issues/35119)
v26.721.3404.0 broke WSL repository detection; previous version worked. 23 comments, 17 👍. Regression affecting Windows + WSL2 developers.

### 6. Headless remote Linux hosts for Codex mobile [#23200](https://github.com/openai/codex/issues/23200)
Mobile is useful as a control layer but currently requires the desktop app to stay online. 19 comments, **48 👍**. Community wants SSH-based remote execution without a desktop host.

### 7. Failed to archive conversation / phantom threads [#28276](https://github.com/openai/codex/issues/28276)
Archiving fails silently; orphaned threads appear in the sidebar. 19 comments. Part of a cluster of session/archival bugs.

### 8. Owner-discovery timeout causing ~5s pause on chat load [#37398](https://github.com/openai/codex/issues/37398)
Opening any unloaded local chat stalls for ~5 seconds due to a fixed timeout before fallback. 16 comments, 10 👍. Performance papercut affecting desktop UX.

### 9. MCP stdio process stacks leak memory on Linux [#25015](https://github.com/openai/codex/issues/25015)
Subagent MCP child process trees aren't reaped after completion, causing linear memory growth. 8 comments, 4 👍. Critical for long-running agentic workloads.

### 10. `TurnDiffTracker` memory leak — OOM within hours [#39231](https://github.com/openai/codex/issues/39231)
The CLI's `TurnDiffTracker` grows unboundedly, causing out-of-memory crashes during extended sessions. 3 comments. New but severe regression reported by a power user.

---

## 4. Key PR Progress

| PR | Status | Summary |
|----|--------|---------|
| [#39337](https://github.com/openai/codex/pull/39337) | Open | **git-utils: validate linked worktree trust metadata** — Fixes trust inheritance through `.git` worktree files that point to arbitrary paths under a trusted repo. |
| [#39336](https://github.com/openai/codex/pull/39336) | Open | **hooks: bind command trust to script contents** — Prevents trusted hook commands from executing modified scripts without re-review by recording content hashes. |
| [#39334](https://github.com/openai/codex/pull/39334) | Open | **rmcp-client: sandbox executor stdio servers** — Attaches filesystem sandbox intent to MCP stdio startup so repository-controlled commands can't escape as native processes. |
| [#39333](https://github.com/openai/codex/pull/39333) | Open | **core-plugins: isolate curated plugin ls-remote** — Pre-trust plugin probes can no longer inherit local `url.*.insteadOf` or `core.sshCommand` to execute arbitrary code before trust is established. |
| [#39330](https://github.com/openai/codex/pull/39330) | Open | **rmcp-client: create OAuth fallback credentials privately** — Fixes a race where `CODEX_HOME/.credentials.json` could be created with world-readable permissions before `chmod` runs. |
| [#39329](https://github.com/openai/codex/pull/39329) | Open | **shell-command: require approval for git diff-driver subcommands** — Closes a bypass where untrusted repos could execute attacker-controlled diff drivers via `.gitattributes`/`.git/config`. |
| [#39328](https://github.com/openai/codex/pull/39328) | Open | **core-plugins: block ext transport during startup sync** — Prevents startup Git commands from using `ext::` transports before trust is established. |
| [#39322](https://github.com/openai/codex/pull/39322) | Closed | **Enforce workspace restrictions for header authentication** — Validates externally supplied header credentials against configured workspace `chatgpt-account-id` restrictions. |
| [#39319](https://github.com/openai/codex/pull/39319) | Closed | **Add the async user message tool** — Introduces `send_user_message_async` for root agents, enabling non-blocking agent messages that don't end the current turn. |
| [#39316](https://github.com/openai/codex/pull/39316) | Closed | **Support Edu Plus and Edu Pro account plans** — Recognizes education workspace plans across auth, rate-limiting, and app-server schemas. |

---

## 5. Feature Request Trends

- **Context/workspace scoping** — Users consistently want Codex to respect project boundaries (Issue [#25319](https://github.com/openai/codex/issues/25319), 65 👍). The request to scope VS Code chats to the current workspace is the most upvoted open feature ask.
- **Remote/headless support** — Mobile as a control layer for always-on remote Linux hosts is a recurring theme (Issue [#23200](https://github.com/openai/codex/issues/23200), 48 👍). Users want SSH-based execution without a persistent desktop app.
- **Session management** — Export, forking, and archival are highly requested. The closure of [#2880](https://github.com/openai/codex/issues/2880) and the new fork/export features in v0.148.0 show the team is moving in this direction.
- **Secrets/config portability** — Carrying `.env` and `.npmrc` files into worktrees (Issue [#10528](https://github.com/openai/codex/issues/10528)) remains an unaddressed need.
- **Model cache controls** — AWS Bedrock users want explicit prompt-cache controls for GPT-5.6 Sol to reduce costs (Issue [#37674](https://github.com/openai/codex/issues/37674)).

---

## 6. Developer Pain Points

- **Windows browser control is broken in v26.814** — A cluster of 4+ issues (#39136, #39173, #39318, #24040, #23283) point to the same root cause: the Trusted RPC dependency check now rejects the browser plugin's code path. This is the most urgent regression.
- **WSL integration regressions** — Repository detection failures (#35119) and integrated terminal silence (#37104) on Windows + WSL2 are causing friction for a significant developer subset.
- **MCP process/memory leaks** — Two separate issues (#25015, #38754) report MCP stdio servers being repeatedly spawned and not reaped on both Linux and Windows, causing memory bloat during agentic workflows.
- **Performance papercuts** — A fixed 5-second owner-discovery timeout (#37398) and unbounded `TurnDiffTracker` growth (#39231) degrade long-session UX, especially for CLI users.
- **Archival/session corruption** — Multiple bugs around archiving conversations (#28276, #39321) leave threads in a broken state with red exclamation marks, suggesting a reliability gap in session persistence.
- **macOS proxy config ignored** — `respect_system_proxies = true` doesn't actually route traffic through the system proxy (#39237), blocking users behind corporate proxies.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI Community Digest — 2026-08-19

---

## 1. Today's Highlights

Gemini CLI v0.56.0-nightly shipped with targeted fixes for subagent recovery after turn limits, symlinked agent support, and OAuth timeout handling. The community continues to push hard on agent reliability — subagent hangs, loop detection false positives, and Auto Memory edge cases dominate the open issue queue with significant engagement. Security-focused PRs around subprocess credential protection and extension environment sanitization landed this cycle.

---

## 2. Releases

**v0.56.0-nightly.20260819.g571851b10** ([PR #28899](https://github.com/google-gemini/gemini-cli/pull/28899))

Key changes in this nightly build:
- **[SSR Agent] Fix subagent recovery after MAX_TURNS** — Subagents that hit the turn limit were incorrectly reporting `GOAL` success, hiding the interruption from the user. ([PR #28865](https://github.com/google-gemini/gemini-cli/pull/28865), [Issue #22323](https://github.com/google-gemini/gemini-cli/issues/22323))
- **[SSR Agent] Prevent subagents when agents mode is disabled** — Subagents can no longer execute when the user has disabled agents mode. ([Issue #22093](https://github.com/google-gemini/gemini-cli/issues/22093))

---

## 3. Hot Issues

### #22323 — Subagent reports GOAL success after hitting MAX_TURNS (12 comments, 2 👍)
The `codebase_investigator` subagent signals `status: "success"` with termination reason `GOAL` even when it reached the maximum turn limit without completing its analysis. This masks failures and makes debugging subagent behavior nearly impossible. High-priority P1 bug affecting agent reliability.

### #21409 — Generalist agent hangs indefinitely (8 comments, 8 👍)
Users report the generalist agent hanging forever on simple tasks like folder creation, requiring manual cancellation after up to an hour. The workaround — instructing the model not to defer to sub-agents — confirms this is an agent-routing issue rather than a model capability problem. Strong community signal (8 upvotes) suggests this is a widespread pain point.

### #19873 — Zero-Dependency OS Sandboxing via bash affinity (8 comments, 1 👍)
An ambitious enhancement proposing Gemini 3 models leverage their native bash chaining capabilities through POSIX tools (`grep`, `sed`, `awk`) within a sandboxed execution layer. This would give the model its preferred execution paradigm without compromising security — a design-oriented feature request with large effort estimation.

### #24353 — Robust component-level evaluations (7 comments)
An epic tracking behavioral eval infrastructure. With 76 evals generated across 6 supported Gemini models since the original behavioral evals issue (#15300), this tracks the ongoing effort to make evaluation more granular and reliable. Critical for release quality assurance.

### #22745 — AST-aware file reads, search, and codebase mapping (7 comments, 1 👍)
Investigates whether AST-aware tools can reduce turns and token noise by precisely reading method bounds and navigating code structure. Could significantly improve codebase investigation efficiency if proven viable.

### #21968 — Gemini underutilizes skills and sub-agents (6 comments)
Anecdotal but widely relevant: Gemini does not autonomously invoke custom skills or sub-agents even when tasks strongly align with their descriptions. Users report having to explicitly instruct the model to use them. Points to a prompt/instruction gap in agent self-awareness.

### #26522 — Auto Memory retries low-signal sessions indefinitely (5 comments)
Sessions that the extraction agent deems low-signal remain perpetually unprocessed in the memory inbox, getting surfaced repeatedly. A quality-of-life bug for users with extensive conversation histories.

### #26525 — Add deterministic redaction, reduce Auto Memory logging (4 comments)
Security concern: Auto Memory sends transcript content to the extraction model *before* redaction occurs, meaning secrets may already be in model context. The request is for pre-transmission redaction and reduced logging of sensitive data.

### #25166 — Shell commands stuck at "Waiting input" after completion (4 comments, 3 👍)
Simple shell commands complete but Gemini remains in an "Awaiting user input" state indefinitely. Reproducible on trivially non-interactive commands. The 3 upvotes reflect frequent user frustration with this UX break.

### #22267 — Browser Agent ignores settings.json overrides (3 comments)
Configuration overrides in `settings.json` (e.g., `maxTurns`) are silently ignored by the Browser Agent despite `AgentRegistry` reading them correctly during initialization. A configuration drift bug that undermines user control over agent behavior.

---

## 4. Key PR Progress

### [#28892](https://github.com/google-gemini/gemini-cli/pull/28892) — Preserve empty text turns with tools or media
Fixes chat history validation to retain model turns with `text: ''` when they carry tool requests, responses, or multimodal payloads. Prevents loss of structured context in curated history.

### [#28898](https://github.com/google-gemini/gemini-cli/pull/28898) — Harden subprocess execution security
Enhances security for core orchestrator subprocesses, configuration ingestion, and GitHub API interactions. Includes credential protection to prevent token leakage into untrusted tool execution environments.

### [#28883](https://github.com/google-gemini/gemini-cli/pull/28883) — Support symlinked agent markdown files
Fixes [#20079](https://github.com/google-gemini/gemini-cli/issues/20079): subagent `.md` files that are symbolic links in `~/.gemini/agents/` are now correctly discovered and loaded.

### [#28877](https://github.com/google-gemini/gemini-cli/pull/28877) — Fix false-positive loop detection on uniform streaming content
Resolves [#18551](https://github.com/google-gemini/gemini-cli/issues/18551): loop detection no longer triggers on streamed responses containing uniform/padded characters (e.g., consecutive spaces).

### [#28876](https://github.com/google-gemini/gemini-cli/pull/28876) — Handle 404 API error in Cloud Shell default project
Fixes [#18062](https://github.com/google-gemini/gemini-cli/issues/18062): gracefully handles missing `cloudshell-gca` default project in Google Cloud Lab accounts.

### [#28873](https://github.com/google-gemini/gemini-cli/pull/28873) — Prevent unhandled promise rejection on OAuth callback timeout
Fixes [#28512](https://github.com/google-gemini/gemini-cli/issues/28512): OAuth callback server timeout after 5 minutes no longer causes an unhandled rejection crash.

### [#28871](https://github.com/google-gemini/gemini-cli/pull/28871) — Translate compact matchers to compress and update enum
Fixes [#14724](https://github.com/google-gemini/gemini-cli/issues/14724): hook configurations migrated from Claude Code that use `compact` matchers are now correctly translated to Gemini CLI's `compress` enum value.

### [#28870](https://github.com/google-gemini/gemini-cli/pull/28870) — Emit pending tool call update before requesting permission
Fixes [#21783](https://github.com/google-gemini/gemini-cli/issues/21783): in ACP mode, the agent now sends a `pending` tool call update before requesting user permission, complying with the protocol contract.

### [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) — Prompt for consent on environment changes, sanitize runtime-altering env vars
Prevents extension updates from bypassing consent checks and injecting unauthorized environment variables into spawned MCP server processes. Security-hardening for the extension system.

### [#28893](https://github.com/google-gemini/gemini-cli/pull/28893) — Preserve explicit flash model IDs
Fixes [#28859](https://github.com/google-gemini/gemini-cli/issues/28859): explicit model IDs like `gemini-3.6-flash` and `gemini-3.7-flash` are no longer rewritten during the Gemini 3.5 Flash rollout. The rewrite is now restricted to the generic `flash` alias and known rollout IDs.

---

## 5. Feature Request Trends

1. **Agent reliability and observability** — The dominant theme. Users want subagents that recover gracefully from turn limits, don't hang, and expose their internal trajectories via `/chat share` ([#22598](https://github.com/google-gemini/gemini-cli/issues/22598), [#21763](https://github.com/google-gemini/gemini-cli/issues/21763)).
2. **AST-aware codebase navigation** — Multiple issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)) point to demand for token-efficient, structurally aware code reading and search tools.
3. **Sandboxed execution with bash affinity** — [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) proposes leveraging the model's native bash capabilities in a zero-dependency sandbox, reflecting a desire for more natural codebase exploration.
4. **Memory system maturity** — Auto Memory ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522), [#26525](https://github.com/google-gemini/gemini-cli/issues/26525), [#26523](https://github.com/google-gemini/gemini-cli/issues/26523)) has multiple quality and security gaps that users want resolved before the feature is considered production-ready.
5. **Agent self-awareness** — [#21432](https://github.com/google-gemini/gemini-cli/issues/21432) calls for the agent to understand and accurately explain its own mechanics (CLI flags, hotkeys, self-execution), suggesting users want a more transparent and self-documenting tool.

---

## 6. Developer Pain Points

- **Subagent reliability**: Hangs (#21409), false GOAL success (#22323), ignored settings overrides (#22267), and browser agent failures on Wayland (#21983) indicate the subagent system is still fragile under real-world conditions.
- **Context and turn management**: Models firehosing context with large file reads (#19561), creating tmp scripts in random locations (#23571), and hitting 400 errors with >128 tools (#24246) all point to ongoing friction around context efficiency and tool management.
- **Shell execution UX**: Commands stuck at "Waiting input" (#25166) and interactive prompts causing hangs (#22465) are repeated frustrations, especially for users running automated or scripted workflows.
- **Auto Memory quality gaps**: Low-signal retry loops (#26522), missing redaction before model context (#26525), and silent invalid patch handling (#26523) erode trust in the memory feature.
- **Terminal rendering performance**: Terminal resize causing flickering and high CPU (#21924), plus ghost text infinite loops at narrow widths (#28641), indicate the rendering layer needs continued investment.
- **Configuration compatibility**: Users migrating from Claude Code face enum mismatches (#28871), and symlinked agent files aren't recognized (#20079), creating friction for multi-tool workflows.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI Community Digest — 2026-08-19

## 1. Today's Highlights

GitHub Copilot CLI v1.0.81-1 shipped with Gemini 3.7 Flash support, a new `Ctrl+E` shortcut for settings in `/sandbox`, and per-agent usage metrics in `--usage-output-file`. The biggest community concern today centers on a sandbox regression in 1.0.81 that forces sandboxing even when explicitly disabled, spawning three linked triage issues within hours. Additionally, a regression in 1.0.80 broke Atlassian MCP OAuth authentication, pointing to an RFC 8414 §3.3 compliance issue.

## 2. Releases

**v1.0.81-1** — [Latest Release](https://github.com/github/copilot-cli/releases)

| Type | Change |
|------|--------|
| **Added** | Gemini 3.7 Flash model support |
| **Added** | `Ctrl+E` in `/sandbox` to open `settings.json` in your editor |
| **Added** | Per-agent usage metrics in `--usage-output-file` JSON output |
| **Improved** | Press `x` to remove scheduled `/every` and `/after` prompts in Schedule Manager |
| **Fixed** | [Fix truncated in source data] |

## 3. Hot Issues

**#4390 — Organization models missing from catalogue** [OPEN · 10 comments · 7 👍](https://github.com/github/copilot-cli/issues/4390)
Anthropic models (Claude Sonnet 5/Opus 5) and Kimi K3, explicitly enabled at the org level, are invisible to the CLI. A high-impact enterprise issue affecting teams relying on managed model access.

**#2904 — Per-agent reasoning effort in custom agent YAML** [OPEN · 7 comments · 20 👍](https://github.com/github/copilot-cli/issues/2904)
The most-upvoted open issue. Custom agents can pin a model via frontmatter but cannot set `reasoning_effort` per-agent — it's only global. Strong community demand for granular control.

**#2958 — Per-mode default model configuration** [OPEN · 4 comments · 16 👍](https://github.com/github/copilot-cli/issues/2958)
Users want to configure different default models for plan mode vs. autopilot mode. High upvotes reflect a common workflow split between lightweight planning and heavier execution.

**#4490 — Atlassian MCP OAuth broken in 1.0.80** [OPEN · 3 comments](https://github.com/github/copilot-cli/issues/4490)
A regression from 1.0.78 → 1.0.80: OAuth discovery now fails with `Incompatible authorization server` (RFC 8414 §3.3). Directly breaks enterprise MCP integrations.

**#4522 — Sandbox forced despite `enabled: false` in 1.0.81** [OPEN · 2 comments · 6 👍](https://github.com/github/copilot-cli/issues/4522)
The most urgent bug: when managed policy is temporarily undetermined, the CLI overrides an explicit `sandbox.enabled=false` config. Three related sandbox issues (#4521, #4524, #4516) filed the same day suggest a broader regression.

**#4313 — Scroll through conversation history** [OPEN · 8 comments](https://github.com/github/copilot-cli/issues/4313)
Mouse wheel / PageUp/PageDown navigation is intercepted by the terminal instead of scrolling conversation history — a persistent UX friction point.

**#3162 — Custom MCP servers falsely reported as blocked by policy** [CLOSED · 7 comments](https://github.com/github/copilot-cli/issues/3162)
v1.0.42 incorrectly flagged registry-listed custom MCP servers as policy-blocked. Closed but indicative of ongoing registry-validation fragility.

**#4096 — Third-party MCP tools missing in CLI after app UI auth** [CLOSED · 6 comments](https://github.com/github/copilot-cli/issues/4096)
OAuth-authenticated MCP servers (e.g., Atlassian Remote MCP) show "Connected" in the app but tools never appear in CLI sessions — the auth token isn't bridged.

**#4392 — Orphaned stdio MCP server processes after auth rebuild** [OPEN · 2 comments](https://github.com/github/copilot-cli/issues/4392)
The CLI tears down and rebuilds the full MCP client post-auth, leaving stdio child processes unreaped. A resource leak with scaling implications.

**#3698 — MCP stdio server spawn leak under slow/unreachable upstream** [OPEN · 0 comments · 3 👍](https://github.com/github/copilot-cli/issues/3698)
Related to #4392: when an MCP server is slow or unreachable, child processes accumulate without bound across restarts, pinning CPU.

## 4. Key PR Progress

**#3163 — ViewSonic monitor** [OPEN](https://github.com/github/copilot-cli/pull/3163)
Initiates a GitHub Action workflow; references issues #2591, #3561, #3559. Limited detail available; appears to be an infrastructure/maintenance PR.

*(Note: Only 1 PR was updated in the last 24h. No other PRs are available for summary.)*

## 5. Feature Request Trends

1. **Granular model & reasoning control** — Issues #2904 and #2958 together signal strong demand for per-agent and per-mode configuration of both model selection and reasoning effort, moving beyond the current global-only knobs.
2. **MCP auth & lifecycle robustness** — Multiple open issues (#4096, #4490, #4392, #3698) point to a pattern: MCP OAuth bridging, token refresh, and process lifecycle management are under-specified and error-prone.
3. **Sandbox configurability** — The cluster of sandbox issues (#4521, #4522, #4524, #4516) reflects a need for clearer policy resolution logic and the ability to reliably opt out.
4. **Discovery & navigation** — Scrollable conversation history (#4313) and searchable plugin marketplace (#4523) are recurring quality-of-life requests.
5. **BYOK credential refresh** — #3682 requests the ability to rotate short-lived bearer credentials (Entra ID, AWS STS, OIDC) without restarting the CLI.

## 6. Developer Pain Points

- **Sandbox policy regression (1.0.81):** The most acute frustration today. Users who explicitly disabled sandboxing are finding it re-enabled when managed policy is undetermined, breaking workflows that depend on unrestricted filesystem access (e.g., JVM tooling — #4516, git — #4524).
- **MCP tool availability after auth:** Third-party OAuth MCP servers connect in the GUI but tools are invisible in CLI sessions (#4096), and token refresh at startup leaks stdio processes (#4392, #3698). This creates a disconnect between the app and CLI experiences.
- **Enterprise model catalogue gaps:** Org-enabled models (Claude Sonnet 5, Opus 5, Kimi K3) don't appear in the CLI catalogue (#4390), blocking enterprise users from using licensed models.
- **Per-agent configuration holes:** Custom agents can pin models but not reasoning effort (#2904), and built-in agents ignore custom instructions (#1990), creating inconsistent behavior across agent types.
- **Shell permission config not honored:** Paths added via `allowed_directories` in `permissions-config.json` don't suppress prompts for shell commands unless `/add-dir` is run interactively (#4482).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI — Community Digest
**Date:** 2026-08-19 | **Repo:** [MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

## 1. Today's Highlights

The Kimi Code CLI community saw two notable contributions today: a UI bug report involving assistant message re-rendering for non-Kimi OpenAI-compatible providers, and a user-published benchmark report documenting K3 + Kimi Code's performance on out-of-sample quantitative trading strategy generation. One maintenance PR (SSH failure logging) was closed, and a new "knowledge plane" feature PR entered review.

---

## 2. Releases

**No new releases in the last 24 hours.**

---

## 3. Hot Issues

Only 2 issues were updated in the reporting window. They are listed below in full.

| # | Title | Author | Reaction | [Link](https://github.com/MoonshotAI/kimi-cli/issues) |
|---|-------|--------|----------|------------------------------------------------------|
| #2607 | Web UI: assistant messages re-render as one-fragment-per-line after tab switch/reload for non-Kimi providers | chenxupeng1990-eng | 0 👍 · 1 💬 | [#2607](https://github.com/MoonshotAI/kimi-cli/issues/2607) |
| #2608 | Benchmarked K3 + Kimi Code on out-of-sample quant strategy generation — full report open-sourced | frank-quant | 0 👍 · 0 💬 | [#2608](https://github.com/MoonshotAI/kimi-cli/issues/2608) |

**Why they matter:**
- **#2607** — Affects the growing subset of users running Kimi Code CLI with third-party OpenAI-compatible backends (e.g., local Ollama, vLLM, OpenRouter). The one-fragment-per-line corruption after session remount is a significant UX regression that degrades readability and may indicate a serialization/diff issue in the Web UI's message reconciliation logic.
- **#2608** — Represents community-driven validation of Kimi Code CLI in a high-stakes domain (quantitative trading). The author has open-sourced a full benchmark report from two Bilibili/YouTube episodes covering ETH perpetual futures strategy generation with Freqtrade, offering the team real-world usage telemetry and potential collaboration signal.

---

## 4. Key PR Progress

Only 2 PRs were updated in the reporting window.

| # | Title | Author | Status | [Link](https://github.com/MoonshotAI/kimi-cli/pulls) |
|---|-------|--------|--------|------------------------------------------------------|
| #848 | fix(kaos): log ssh failures when enabled | powerfooI | **CLOSED** | [#848](https://github.com/MoonshotAI/kimi-cli/pull/848) |
| #2606 | Dev/knowledge plane | SoMiReMiReDo | **OPEN** | [#2606](https://github.com/MoonshotAI/kimi-cli/pull/2606) |

**PR #848 — fix(kaos): log ssh failures when enabled**
- A small but useful reliability fix for the KAOS (Kimi AI Operating System) component. When SSH is enabled in remote execution modes, failures were previously silent or insufficiently logged, making debugging difficult. The PR has been closed (merged), improving observability for users running Kimi Code CLI against remote hosts.
- Also reviewed via [Devin AI](https://app.devin.ai/review/moonshotai/kimi-cli/pull/848).

**PR #2606 — Dev/knowledge plane**
- An in-progress feature PR introducing a "knowledge plane" layer to the CLI. While the description is minimal, the naming suggests a structured context/knowledge injection system — potentially allowing the agent to ground responses in project-specific or user-curated documentation. The PR is still open and awaiting maintainer review.

---

## 5. Feature Request Trends

Based on the current issue landscape, two emerging directions stand out:

1. **Third-Party Provider Compatibility & Fidelity** — Issue #2607 highlights that the Web UI's message rendering pipeline assumes Kimi-native formatting. Users increasingly run OpenAI-compatible providers, and gaps in cross-provider rendering (stream delta merging, remount recovery) are surfacing. Expect continued reports along these lines as the non-Kimi provider base grows.

2. **Domain-Specific Benchmarks & Knowledge Grounding** — Issue #2608 and PR #2606 both point toward a community desire (and implicit demand) for Kimi Code CLI to perform reliably in specialized verticals — quantitative finance in this case. The "knowledge plane" PR appears to be a direct response to this trend: a mechanism for structured, project-aware context that could improve out-of-sample task performance.

---

## 6. Developer Pain Points

| Pain Point | Source | Severity |
|------------|--------|----------|
| **Web UI message corruption on remount** for non-Kimi providers | [#2607](https://github.com/MoonshotAI/kimi-cli/issues/2607) | 🔴 High — degrades core UX for a growing user segment |
| **Insufficient SSH/remote-execution error visibility** | [#848](https://github.com/MoonshotAI/kimi-cli/pull/848) (now closed) | 🟡 Medium — now resolved; signals prior opacity in KAOS remote modes |
| **Limited documented workflows for specialized domains** (quant, finance) | [#2608](https://github.com/MoonshotAI/kimi-cli/issues/2608) | 🟡 Medium — community is self-documenting; the team may want to engage |

**Summary:** The most pressing open concern is the Web UI rendering regression for OpenAI-compatible providers (#2607). The SSH logging gap has been addressed. The community is independently building domain-specific know-how (quant trading benchmarks), which could benefit from official guidance or integration with the proposed knowledge plane.

---

*Digest generated from GitHub data as of 2026-08-19. Only 2 issues and 2 PRs were updated in the 24-hour window; this report covers all available items.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode Community Digest — 2026-08-19

## 1. Today's Highlights

The OpenCode community is focused on two major reliability concerns: Zen/Go subscription limits incorrectly capping paying users (multiple open issues reporting $10+ balances still triggering free-tier 429 errors), and streaming/agent-loop bugs causing silent session failures and truncated responses. On the feature side, a deterministic session sync engine (PR #43302) and file mutation preview streaming (PR #38991) signal active progress toward more stable, transparent agent interactions.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues

1. **#3787 — Linear Agent integration** [CLOSED] | 🔑 34 👍
   Long-standing feature request to integrate Linear Agents directly into OpenCode. Closed, suggesting it's been addressed or deprioritized.

2. **#32149 — Opencode stops processing requests without response** [OPEN] | 💬 15 | 👍 6
   Users report the app hangs in a "thinking" state and never returns. A serious reliability bug affecting core functionality.

3. **#7648 — Prevent TUI scrolling when messages stream in** [CLOSED] | 🔑 18 👍
   Community requested a setting to disable auto-scroll during streaming. Closed — likely implemented.

4. **#26338 — Add CommandCode as a Provider** [CLOSED] | 🔑 36 👍
   Feature request to support CommandCode authentication. Closed, indicating provider support was added.

5. **#7226 — /resume and /pause commands** [CLOSED] | 🔑 28 👍
   Request for session control commands. Closed — feature was likely shipped.

6. **#33495 — Zen balance doesn't remove free usage cap** [OPEN] | 💬 7 | 👍 1
   Paying Zen users still hit the 200-request free limit and 429 errors. Multiple confirmations across accounts.

7. **#42729 — Add Qwen3.8-27B** [OPEN] | 💬 6 | 👍 4
   Request to include Qwen3.8-27B in the Go subscription catalog. Directly relevant to the Qwen sampling fix in PR #43310.

8. **#37489 — Context cache invalidation performance issues** [OPEN] | 💬 6 | 👍 1
   Significant slowdowns with local LLMs (vLLM/Ollama) during mode switches and compaction.

9. **#41469 — Session silently stops on empty LLM response** [OPEN] | 💬 5
   Empty completions (0 tokens, `finish: unknown`) cause the session loop to exit silently — a subtle but disruptive bug.

10. **#39831 — gpt-5.6-luna/terra fail with upstream error** [CLOSED] | 💬 5 | 👍 1
    Specific model failures via Zen provider. Closed, likely resolved.

## 4. Key PR Progress

1. **#43302 — Session sync engine** | Open
   Replaces the TUI's per-session sync with a deterministic engine: `view = render(fold(snapshot ⊕ durable log) ⊕ outbox ⊕ overlay)`. One snapshot fetch atomically hydrates a session; a server-merged stream replays durable events. Major architectural improvement.

2. **#38991 — Stream file mutation previews** | Open
   Closes #38972. File-writing tools now forward partial tool JSON to show live previews instead of a static "pending" label during generation.

3. **#43200 — Promote current design system** | Closed
   Lifted UI primitives to canonical `@opencode-ai/ui/*` exports, removed `/v2` component exports and duplicate legacy implementations.

4. **#32370 — Linux clipboard selection config** | Open
   Closes #43176. Adds `linux_clipboard_selection` option for primary buffer (clipboard vs. primary selection) support on Linux.

5. **#43319 — Injected text parts opt into markdown rendering** | Open
   Closes #43318. Allows injected text fragments to be rendered as markdown instead of plain text, matching assistant-path rendering behavior.

6. **#43314 — Degrade undecodable image attachments** | Open
   Closes #43262. Instead of failing the entire prompt when an image can't be decoded (AVIF, HEIC, BMP, TIFF) or exceeds resize limits, the system now degrades gracefully.

7. **#43310 — Remove Qwen sampling defaults** | Closed
   Stops forcing `temperature: 0.55` and `top_p: 1` on all Qwen models. Leaves sampling to provider/server defaults while preserving `chat.params` plugin overrides. Addresses community concern from #42775.

8. **#43282 — Expose valid subagent IDs in subagent tool** | Open
   Closes #36761. Fixes the subagent tool schema to list valid `agent` values instead of the vague "specialized agent type" description.

9. **#29831 — Resolve spawn completion on exit (Windows)** | Open
   Closes a Windows-specific hang where shell commands would wait forever because the parent process finished but the child kept output open.

10. **#43309 — Configurable generated title length** | Open
    Closes #43118. Adds `title_max_words` config to cap session title length via the title agent prompt.

## 5. Feature Request Trends

- **Session & agent control**: `/resume`, `/pause`, and subagent tool improvements (#7226, #43282) show demand for finer-grained agent lifecycle management.
- **Provider & model expansion**: CommandCode (#26338), Qwen3.8-27B (#42729), SCX.ai (#42520), and Linear Agents (#3787) reflect active interest in broadening supported providers and integrations.
- **UX & accessibility**: TUI scroll behavior (#7648), Mermaid detection in untagged fences (#43304), Linux clipboard (#32370), and i18n (#43307) indicate a community pushing for platform parity and localization.
- **Session portability**: Export/import sessions as first-class Desktop features (#32696) and the session sync engine (#43302) point to a demand for better session management and persistence.

## 6. Developer Pain Points

- **Zen/Go billing cap bugs**: Multiple users ( #33495, #43208) report paying subscribers still hitting free-tier 200-request limits and 429 errors — a high-impact trust issue.
- **Silent session failures**: Empty responses (#41469) and hung processing (#32149) cause sessions to stop without any error feedback, making debugging difficult.
- **Provider model regressions**: Hard-coded sampling defaults for Qwen (#42775, fixed in #43310) and truncated responses across DeepSeek/Kimi/MiMo models (#41582, #41528, #40176) suggest upstream model-serving instability.
- **Database bloat**: Event table stores full message snapshots per streaming update, causing `opencode.db` to grow to gigabytes (#41175, #42748). The quadratic write behavior is a known performance bottleneck.
- **Platform-specific quirks**: Windows detached-child hangs (#29831), Linux scrollbars missing (#43299), and narrow-viewport UI overlap (#43295) highlight ongoing cross-platform polish needs.
- **Project identification**: Same git remote URL producing identical `project_id` across clones (#42315) and stale project paths after moves (#34737) cause confusion in the Desktop sidebar.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi Community Digest — 2026‑08‑19

## 1. Today's Highlights
The Pi monorepo saw a wave of fixes addressing session‑persistence conflicts, stream‑hang resilience, and OpenAI‑compatible provider onboarding. Several high‑visibility bugs (TUI flash, long‑session jump, Windows `find` hangs) were closed, while extension‑hook proposals and a new `disabledCommands` setting signal a push toward greater configurability and recovery control.

## 2. Releases
No new releases in the last 24 hours.

## 3. Hot Issues
1. **#8251** [CLOSED] GitHub Enterprise Copilot login fails after successful device flow due to concurrent policy requests and HTTP 429  
   *Why it matters:* Concurrent model‑policy requests can invalidate a device‑flow login with rate limits, breaking enterprise Copilot flows. (4 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8251

2. **#8281** [CLOSED] TUI: full‑screen flash when content above the viewport changes in long transcripts  
   *Why it matters:* A reproducible UI bug that degrades the interactive experience during long sessions. (4 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8281

3. **#6339** [CLOSED] Auto‑compaction threshold is never evaluated during an agentic run  
   *Why it matters:* Compaction only runs at run boundaries, leaving long agentic loops without proactive context management. (3 comments)  
   🔗 https://github.com/earendil-works/pi/issues/6339

4. **#8138** [OPEN] Contribution Proposal: retry classification for openai‑codex “Sorry, something went wrong”  
   *Why it matters:* Would allow transient backend errors to be retried automatically instead of surfacing as terminal failures. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8138

5. **#8323** [CLOSED] OpenAI client created with no timeout  
   *Why it matters:* Local models that think >10 minutes are cut off mid‑generation because the client inherits the SDK’s 600 s default with no override. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8323

6. **#8317** [CLOSED] Add `agent_recovery_exhausted` extension hook after native recovery  
   *Why it matters:* Enables extensions to switch models and continue a session after retries and overflow compaction are exhausted. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8317

7. **#8309** [CLOSED] When the conversation becomes long, the interface jumps to the top and then back again each time a new command is executed  
   *Why it matters:* Recurring UX bug on both Mac and Windows that disrupts workflow. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8309

8. **#8292** [CLOSED] Expose a pre‑persistence message replacement hook in AgentHarness  
   *Why it matters:* Would let extensions mutate finalised user messages before they are logged, preserving session consistency. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8292

9. **#8286** [CLOSED] openai‑completions: pi silently fails over real network, only succeeds on loopback  
   *Why it matters:* Highlights a non‑deterministic network‑path bug that makes remote Ollama hosting unreliable. (2 comments)  
   🔗 https://github.com/earendil-works/pi/issues/8286

10. **#8282** [CLOSED] `find` in Windows scans huge directories, causing a hung process  
    *Why it matters:* On Windows, scanning directories like `C:\Windows` can occupy CPU for 20+ minutes and require manual termination. (2 comments)  
    🔗 https://github.com/earendil-works/pi/issues/8282

## 4. Key PR Progress
1. **#8320 / #8324** [CLOSED] `feat(coding‑agent): add OpenAI‑compatible API provider to /login flow`  
   *What it does:* Adds two synthetic provider entries (base URL, model name, API key) to the login selector, writing a `models.json` entry with sensible defaults (128k context, 16k max tokens).  
   🔗 https://github.com/earendil-works/pi/pull/8320  🔗 https://github.com/earendil-works/pi/pull/8324

2. **#6216** [OPEN] `feat: Add Amazon Bedrock Mantle OpenAI Responses provider`  
   *What it does:* Introduces a new provider for Bedrock Mantle’s OpenAI Responses API, superseding earlier attempts.  
   🔗 https://github.com/earendil-works/pi/pull/6216

3. **#8333** [CLOSED] `fix(coding‑agent): enforce session writer ownership and audit provider lineage`  
   *What it does:* Prevents two processes from writing the same session file; adds opt‑in provider‑payload lineage auditing.  
   🔗 https://github.com/earendil-works/pi/pull/8333

4. **#8330** [CLOSED] `agent: stream inactivity watchdog — a stalled provider stream no longer hangs the loop forever`  
   *What it does:* Adds a timeout so that an SSE stream that stops delivering events no longer blocks the agent loop indefinitely.  
   🔗 https://github.com/earendil-works/pi/pull/8330

5. **#8327** [CLOSED] `fix(tui): yield long markdown rendering`  
   *What it does:* Prevents large markdown renders from monopolising the TUI event loop by introducing a render context with a monotonic deadline.  
   🔗 https://github.com/earendil-works/pi/pull/8327

6. **#8326** [CLOSED] `feat: add disabledCommands setting to block built‑in slash commands`  
   *What it does:* Allows users to disable built‑in commands (e.g., `/share`, `/export`) via `settings.json`; disabled commands show an error and are hidden from autocomplete.  
   🔗 https://github.com/earendil-works/pi/pull/8326

7. **#8254** [OPEN] `fix(ai): prevent copilot policy login rate limits`  
   *What it does:* Fetches the account model catalog before policy updates, retries throttled requests, and extracts a `sleep` utility.  
   🔗 https://github.com/earendil-works/pi/pull/8254

8. **#8319** [OPEN] `fix(ai): anthropic fallback usage`  
   *What it does:* Correctly prices fallback usage with the model that actually served the response instead of the requested model.  
   🔗 https://github.com/earendil-works/pi/pull/8319

9. **#8307** [OPEN] `feat(coding‑agent): enable experimental cache‑friendly compaction`  
   *What it does:* Caches compaction requests within the active session, reducing cost compared to standalone compaction calls.  
   🔗 https://github.com/earendil-works/pi/pull/8307

10. **#8275** [CLOSED] `feat(ai): generalize openai‑completions thinking token budget fields`  
    *What it does:* Extends the `thinkingTokenBudgetField` flag to cover vLLM, Qwen/SGLang, and llama.cpp, ensuring consistent reasoning‑token clamping.  
    🔗 https://github.com/earendil-works/pi/pull/8275

## 5. Feature Request Trends
- **Extension hooks for lifecycle control** – Requests for pre‑persistence message hooks (`#8292`), agent‑recovery‑exhausted hooks (`#8317`), and namespace‑aware skill loading (`#8334`) show a strong desire for deeper integration points.
- **Configuration flexibility** – The `disabledCommands` setting (`#8325`, PR #8326) and the OpenAI‑compatible provider onboarding (`#8320`) reflect demand for easier customisation and provider diversity.
- **Resilience & observability** – Retry‑classification improvements (`#8138`), stream‑timeout watchdogs (`#8330`), and provider‑lineage auditing (`#8333`) indicate a focus on making Pi more robust under failure and network variability.
- **UX polish** – Fixes for TUI flashing (`#8281`), session‑file conflicts (`#8334`), and long‑session navigation jumps (`#8309`) demonstrate ongoing attention to interactive‑mode stability.

## 6. Developer Pain Points
- **Session persistence conflicts** – Multiple processes writing to the same JSONL file cause divergent branches and cross‑window message mixing (`#8334`, #8300).
- **Stream hangs** – A stalled SSE stream leaves the agent loop frozen behind a “Working” spinner (`#8331`, addressed by PR #8330).
- **Network‑path non‑determinism** – Remote Ollama endpoints fail silently over real networks while succeeding on loopback (`#8286`).
- **Windows‑specific tooling** – The `find` command hangs on large directories like `C:\Windows`, requiring manual termination (`#8282`).
- **Compaction threshold not evaluated** – Auto‑compaction is only checked at run boundaries, missing opportunities during long agentic runs (`#6339`).
- **Timeout defaults too aggressive** – The OpenAI client’s 600 s default cuts off slow local models (`#8323`).
- **TUI performance and layout bugs** – Full‑screen flashes, image‑collapsing issues, and markdown‑rendering stalls degrade the interactive experience (`#8281`, #8304, #8327).
- **Recovery and error‑handling gaps** – Lack of hooks for post‑recovery actions and silent failures on BOM‑prefixed `package.json` (`#8310`) frustrate extension authors and power users.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code Community Digest — 2026-08-19

## 1. Today's Highlights

Qwen Code v0.21.14-preview.0 landed with a new live-session registry (`qwen sessions ps`) and daemon skill-toggle metadata. Meanwhile, the community is heavily engaged on multi-agent session coordination—three interrelated PRs (peer collaboration design, leader-only shutdown enforcement, agent board sharing) plus ongoing cross-session messaging RFC work. The review pipeline continues to mature with new witness forms, run disciplines, and a flakiness-gate proposal.

## 2. Releases

**v0.21.14-preview.0** ([PR #8969](https://github.com/QwenLM/qwen-code/pull/8969))
- Added a live-session registry and `qwen sessions ps` subcommand for inspecting active sessions.
- Daemon now attaches skill-toggle mutation metadata for tighter review-cycle observability.

Several DSW end-to-end smoke runs (v0.21.13 benchmark ref) validated SWE-bench Verified (500/500 succeeded) and Terminal-Bench 2.0 (89 cases) on 2026-08-18; two full-run variants were quarantined for data-curve concerns.

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| [#9296](https://github.com/QwenLM/qwen-code/issues/9296) | Qwen Autofix: review-event storms & duplicate address dispatch | ~59% of ~500 autofix runs were cancelled; P0 finding that reviews on closed/merged PRs still fire. Directly impacts CI throughput. |
| [#656](https://github.com/QwenLM/qwen-code/issues/656) | API Error 400 on every message | Long-running (since Sep 2025) blocking bug; 11 comments, no resolution. Users report 12–16 h outages without config changes. |
| [#8718](https://github.com/QwenLM/qwen-code/issues/8718) | RFC: Native coordination for independent Qwen sessions *(CLOSED)* | Sparked the multi-session collaboration series; 10 comments shaped the design now carried in PRs #9399 and #9402. |
| [#8724](https://github.com/QwenLM/qwen-code/issues/8724) | Cross-session messaging on the same machine | Enables `list_agents` / `send_message` between independent sessions with a fail-closed gate—core primitive for multi-agent workflows. |
| [#9276](https://github.com/QwenLM/qwen-code/issues/9276) | Team members cannot send ordinary messages to their leader | Bug in the team subsystem: any message from a member is misrouted as a shutdown request. 7 comments, still open. |
| [#9438](https://github.com/QwenLM/qwen-code/issues/9438) | User message dropped after tool call on Ollama | Ollama requires a `role: user` turn; Qwen Code omits it post-tool-call, returning HTTP 500. Fresh (today) and P1. |
| [#8400](https://github.com/QwenLM/qwen-code/issues/8400) | Sessions silently auto-deleted after Desktop restart (Windows) | Workspace cwd mismatch causes the provider loader to return 0 messages, triggering unconditional session deletion. 4 comments, open. |
| [#9278](https://github.com/QwenLM/qwen-code/issues/9278) | /review publish-time convergence advisory | Documents the runaway review loop (finding → fix → larger diff → more findings) and proposes telemetry/operator-owned surfaces to dampen it. |
| [#9430](https://github.com/QwenLM/qwen-code/issues/9430) | Named teammates ignore `run_in_background: false` | Flag accepted but not enforced; teammates still launch concurrently. Indicates a gap in the coordinate skill. |
| [#9354](https://github.com/QwenLM/qwen-code/issues/9354) | Cross-host chat transcript contract prevalidation *(CLOSED)* | Established a read-only transcript contract across Web Shell, Tauri Desktop, VS Code, and HTML export—foundational for multi-host portability. |

## 4. Key PR Progress

| # | Title | Summary |
|---|-------|---------|
| [#9413](https://github.com/QwenLM/qwen-code/pull/9413) | `feat(review): record each round's posting volume in the ledger marker` | Machine-readable marker now carries the size of the posting set after the severity floor, enabling auditability of review throughput. |
| [#9401](https://github.com/QwenLM/qwen-code/pull/9401) | `fix(core): make team shutdown a leader-only tool` | Extracts shutdown into `request_shutdown` and removes the `type` enum from `send_message`, fixing the member→leader message bug (#9276). |
| [#9399](https://github.com/QwenLM/qwen-code/pull/9399) | `docs: add peer session collaboration design` | Documents how independently started sessions discover and message each other—complementing the leader-worker model. |
| [#9402](https://github.com/QwenLM/qwen-code/pull/9402) | `feat: agent board — share work across independently started agents` | Repurposed from a delete; now introduces a shared agent board UI for cross-session work coordination. |
| [#9388](https://github.com/QwenLM/qwen-code/pull/9388) | `feat(web-shell): add transcript contract prevalidation` | Freezes deterministic synthetic fixtures, hashes, and a closed V1 export schema; verifies existing export paths. |
| [#9443](https://github.com/QwenLM/qwen-code/pull/9443) | `Automated PR verification: distinguish "no behavioral change" from "never exercised"` | Addresses a false-positive pattern in serve A/B where unchanged PRs were reported as "no response changes" even when not driven. |
| [#9446](https://github.com/QwenLM/qwen-code/pull/9446) | `review: a live-service witness form and a graft` | Adds witness forms for claims that batch-shaped verification can't reach (live two-arm runs). |
| [#9445](https://github.com/QwenLM/qwen-code/pull/9445) | `feat(review): add runtime-axis, table-sweep and isolation witness forms` | Extends the verifier's brief with three new forms covering runtime-version claims and isolated execution guarantees. |
| [#9301](https://github.com/QwenLM/qwen-code/pull/9301) | `feat(goal): account the tokens a Goal spends` | `GoalRecord` gains a `tokensUsed` field, aggregated across turns and surfaced in `/stats` and `lastGoal`. |
| [#9392](https://github.com/QwenLM/qwen-code/pull/9392) | `fix(serve): let channel workers reach TLS-enabled daemons` | When `--tls-cert/--tls-key` is set, daemons now hand workers an `https://` loopback URL instead of the hardcoded `http://`. |

## 5. Feature Request Trends

1. **Multi-agent / cross-session collaboration** — The strongest signal: peer-session messaging (#8724), independent session coordination (#8718), agent board (#9402), and team health notifications (#9449) all converge on making multi-session workflows a first-class experience.
2. **Review pipeline observability & governance** — New witness forms, run disciplines, and a convergence-advisory design show the community pushing for verifiable, self-dampening review loops.
3. **Cross-platform transcript & session portability** — The transcript contract (#9354/#9388) and session-cursor fixes (#9419) point toward a goal of moving sessions and chat history seamlessly between Web Shell, Desktop, VS Code, and HTML export.
4. **Channel integrations** — DingTalk gains forwarded-chat parsing (#9339) and outbound file delivery (#9350), reflecting demand for richer messaging-platform support.

## 6. Developer Pain Points

- **Autofix CI waste:** Review-event storms and duplicate address dispatch are burning runner capacity (#9296); 59% of recent runs cancelled.
- **Ollama backend fragility:** User messages are dropped after tool calls, breaking all subsequent tool use with HTTP 500 (#9438).
- **Windows Desktop session loss:** Cwd mismatch on restart silently deletes sessions without confirmation (#8400).
- **Image MIME rejection:** Unsupported formats (e.g., `.heic`) abort Responses-compatible sessions instead of being gracefully rejected (#9291).
- **Web-shell artifact panel error spam:** Automatic refresh floods users with `Failed to fetch` toasts (#7427).
- **Session pagination duplication:** Activity-ordered cursors can duplicate rows when live entries retire mid-page (#9419).
- **Context-usage stale readout:** Status-line token-percentage doesn't update after `/compress` or `/compress-fast` (#6806).
- **Persistent API 400 errors:** A months-old unrooted bug (#656) continues to block users with no config change required.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI Community Digest — 2026-08-19

---

## 1. Today's Highlights

**v0.9.9** shipped under the new `codewhale` identity, marking the legacy `deepseek-tui` npm package as fully deprecated. The project continues its rebrand from "DeepSeek" to "CodeWhale / Shannon Labs" across all release surfaces. A batch of fixes landed simultaneously: SSE UTF-8 handling on macOS, configurable skill budgets, and CI runner timeouts to prevent hung-gate failures.

---

## 2. Releases

**v0.9.9** — [PR #5499](https://github.com/Hmbown/CodeWhale/issues/5499)

- Legacy `deepseek-tui` npm package deprecated; `codewhale` is the sole public product.
- Fixed narrow-terminal compact-row metrics below 60 columns (#5486) and strict rustdoc bare URLs (#5489).
- Stable contributor credits synchronized across root/TUI changelogs.

---

## 3. Hot Issues

| # | Title | Why It Matters |
|---|-------|---------------|
| #5316 | [EPIC-005] CodeWhale TUI Crate Decomposition | Umbrella tracking issue for the entire crate-split effort; every sub-EPIC and FEAT reports in here. Core architectural rework. |
| #5337 | Web: finish dictionary spine — retire `isZh` branches | Removes the last two-language ternaries from `docs/hooks` and `docs/troubleshooting`, completing the i18n spine migration. |
| #5437 | Formalize status-bar color grammar + repo/worktree state | External design review confirmed the color palette should be kept; PR #5511 already addressed the repo/worktree slice. |
| #5299 | Move npm publication to trusted publishing | npm wrapper currently gated on browser login + 2FA; automated publishes require trusted publishing to eliminate maintainer friction. |
| #5508 | [enhancement] Continuous loop | Users running AI coordinators want an infinite-turn mode until manually interrupted, rather than wrapping sleep cycles in a single turn. |
| #5505 | System prompt dropped after `/new` | **CLOSED** — model received no system prompt after a new session, only a folded `<context_update>`. Bug report by LmeSzinc. |
| #5512 | Header status indicator never renders since 0.9.7 | **OPEN** — `cw/whale/dots` indicator invisible on Windows 11 since the 0.9.7 upgrade. Reported by thejayjetson. |
| #5497 | Terminalize stuck durable executions | Durable Task Manager workers can block forever when `turn.completed` never fires; cancellation now has a grace period with terminal fallback. |
| #5482 | EPIC(docs): Chinese localization | Growing CN user base; docs tree restructured so translations live in `docs/zh_hans/` — PR #5507 already delivered Tier 1. |
| #5496 | Bound release-candidate and artifact workflow jobs | Follow-up to #5495; caps uncapped surfaces in `release-candidate.yml`, `release-artifacts.yml`, and `release.yml` jobs. |

---

## 4. Key PR Progress

| # | Title | Status | Summary |
|---|-------|--------|---------|
| #5506 | feat(tui): command context adapters & migration gate | ✅ Closed | FEAT-015 DI/migration infrastructure; zero production commands migrated yet — groundwork only. |
| #5507 | docs(i18n): Tier 1 Chinese localization | ✅ Closed | Relocates Chinese docs into `docs/zh_hans/`; restructures tree for per-language translation folders. |
| #5504 | feat(web): move docs/hooks + troubleshooting to spine | ✅ Closed | Removes remaining `isZh` ternaries from the two smallest page bodies (12 branches each). |
| #5511 | feat(tui): show repo context in git chrome | ✅ Closed | Header now displays `repo · branch*`, linked worktree path, and ahead/behind counts. |
| #5509 | fix(tui): restore `/title` as independent terminal title | 🟡 Open | Splits `/title` from `/rename` so terminal tab title is decoupled from session name. |
| #5510 | docs(readme): restore star history chart | 🟡 Open | Re-adds the GitHub star chart removed after API restrictions; PR #5414 had replaced it with a fan-out gif. |
| #5503 | test(web): spawn deploy preflight by decoded path | ✅ Closed | Fixes path-encoding bug where non-ASCII checkout paths caused `module-not-found` in preflight tests. |
| #5500 | test(ci): harden release gate concurrency | ✅ Closed | Serializes `telemetry_contract` under nextest; retries fixture lock during race window; uses 10s deadline. |
| #5491 | fix(tui): persist approval outcomes before execution | 🟡 Open | Ensures approval requests and terminal outcomes are logged to session before execution proceeds; closes stale decisions on resume. |
| #5404 | fix(client): fail closed on SSE UTF-8 split | ✅ Closed | Fixes garbled CJK streaming on macOS (U+FFFD) caused by HTTP/2 DATA splitting multi-byte characters across SSE lines. |

---

## 5. Feature Request Trends

- **Infinite-turn / coordinator mode** (#5508): Users running multi-agent loops want a native continuous-loop mode rather than manual sleep-cycle wrapping.
- **Configurable skill & read budgets** (#5405): Long-context V4 users want per-result read/tool-result limits to reduce redundant file reads.
- **Configurable router timeout** (#5494): Auto-router classifier timeout now user-configurable (`[auto.router] timeout_secs`), previously hardcoded at 4 s.
- **Terminal title independence** (#5509): Separating `/title` from `/rename` so the terminal tab reflects session identity without conflating rename semantics.
- **Trusted npm publishing** (#5299): Community interest in removing 2FA/browser-gated publication friction.

---

## 6. Developer Pain Points

- **CI runner hangs**: Uncapped `timeout-minutes` on release workflows allowed a stuck Lint job to block a gate for up to 6 hours (#5495, #5496). All CI jobs now capped.
- **Stuck durable task workers**: Task Manager can dead-lock when the runtime never emits `turn.completed` and cancellation lacks a grace period (#5497).
- **SSE streaming corruption on macOS**: UTF-8 multi-byte characters split across HTTP/2 DATA frames produced garbled output — fixed in #5404.
- **Header indicator regression**: Status indicator (`cw`/`whale`/`dots`) silently stopped rendering on Windows since 0.9.7 (#5512) — likely a regression from the crate decomposition work.
- **System prompt drop on `/new`**: New sessions lost the full system prompt, receiving only a folded context update (#5505, now closed).
- **Legacy package deprecation friction**: Users on v0.8.x transitioning to `codewhale` face naming and command-expectation mismatches during migration.

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

No activity in the last 24 hours.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*