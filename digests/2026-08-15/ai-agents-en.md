# OpenClaw Ecosystem Digest 2026-08-15

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-15 01:37 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw Deep Dive



# OpenClaw Project Digest — 2026-08-15

---

## 1. Today's Overview

OpenClaw registered **500 issue updates** and **500 PR updates** in the last 24 hours, with 485 issues remaining open/active and 400 PRs still open. Only 15 issues were closed and 100 PRs merged or closed today, indicating a **high-inflow, moderate-clearance** project state. No new releases were published. The dominant concern across the issue stream is **gateway memory growth and session-state corruption**, alongside recurring message-delivery failures on WhatsApp, LINE, and Telegram. Developer velocity is visible in several merged security and UX improvements, but critical production-impacting bugs remain unresolved.

---

## 2. Releases

**No new releases** were published today. The latest known stable versions referenced in issues include `2026.7.2-beta.4`, `2026.7.2-beta.7`, and `2026.5.12`, with users reporting regressions across multiple channels.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Title | Status |
|---|---|---|
| [#123914](https://github.com/openclaw/openclaw/pull/123914) | `fix(cron): keep agent-less schedules running after adding an agent` | ✅ Closed |
| [#123901](https://github.com/openclaw/openclaw/pull/123901) | `fix(workers): bound Gateway bundle cache growth` | ✅ Closed |
| [#123913](https://github.com/openclaw/openclaw/pull/123913) | `refactor(sessions): avoid duplicate SQLite conformance runs` | ✅ Closed |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | `feat(security): require acknowledgement for install policy warnings` | ✅ Closed |

### Key Advancements
- **Cron agent-less regression fixed** — schedules created before any agent was bound no longer silently fail after a second agent is added.
- **Gateway bundle cache growth bounded** — content-addressed tarballs under `state/cache/worker-bundles` are now lifecycle-managed, preventing unbounded disk growth during dev/upgrade cycles.
- **Security hardening** — the install-policy warning flow now requires explicit admin acknowledgement before proceeding with potentially risky plugin installs.
- **Test conformance cleaned up** — duplicate SQLite scenarios in the session accessor matrix were removed, reducing CI noise.

---

## 4. Community Hot Topics

### Most Discussed Issues (by comment count)

1. **[#121058](https://github.com/openclaw/openclaw/issues/121058)** — *Silent reply failures still recurring after #116277 closed* (94 comments)
   > Users report that a previously-closed bug reappears; the monitoring cron continues logging new occurrences. Reflects persistent frustration with reply-delivery reliability.

2. **[#7707](https://github.com/openclaw/openclaw/issues/7707)** — *Memory Trust Tagging by Source* (51 comments)
   > Feature request to tag agent memory entries by trust level based on origin, preventing memory poisoning from untrusted content. Signals growing adoption of OpenClaw in security-sensitive environments.

3. **[#42475](https://github.com/openclaw/openclaw/issues/42475)** — *Per-agent cost budget enforcement at the gateway level* (25 comments)
   > Users want hard daily/monthly spend caps enforced at the gateway before model calls are dispatched — a clear signal of production-scale cost management needs.

4. **[#91588](https://github.com/openclaw/openclaw/issues/91588)** — *Gateway Memory Leak — RSS grows from 350MB to 15.5GB* (24 comments, 🐚 platinum hermit)
   > Critical production bug: the gateway RSS grows unboundedly over days, triggering OOM kills and repeated restart cycles.

5. **[#91009](https://github.com/openclaw/openclaw/issues/91009)** — *Codex PreToolUse hook spawns CPU-bound processes and stalls gateway RPC* (20 comments, 🐚 platinum hermit)
   > The `openclaw-hooks` relay for Codex tool calls consumes 100%+ CPU per process, stalling the gateway event loop.

### Most Discussed PRs (by comment count)

1. [#123597](https://github.com/openclaw/openclaw/pull/123597) — *Sidebar updates as focused call to action*
2. [#123276](https://github.com/openclaw/openclaw/pull/123276) — *Start new sessions with folder group defaults*
3. [#120491](https://github.com/openclaw/openclaw/pull/120491) — *Per-turn per-target send budget guard for message tools*

---

## 5. Bugs & Stability

### 🔴 P0 / Critical

| Issue | Title | Severity | Fix PR |
|---|---|---|---|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | Gateway memory leak: RSS → 15.5GB, OOM crashes | 🐚 platinum hermit | — |
| [#119270](https://github.com/openclaw/openclaw/issues/119270) | File tools strip leading `@` from destination paths, writing to wrong files | 🦞 diamond lobster | — |
| [#92186](https://github.com/openclaw/openclaw/issues/92186) | Foreground reply fence cancels delivery of completed replies to earlier group messages | 🦞 diamond lobster | — |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | Silent reply failures recurring after previous fix closed | — | — |

### 🟠 P1 / High

| Issue | Title | Severity | Fix PR |
|---|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook CPU stall | 🐚 platinum hermit | — |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer mode does not inject messages mid-turn | 🦞 diamond lobster | — |
| [#121953](https://github.com/openclaw/openclaw/issues/121953) | Cron agent turns stall on DeepSeek due to deprioritized prefix | 🐚 platinum hermit | — |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | Gateway heap grows to 1073MB+ at idle, cron jobs fail silently | 🦞 diamond lobster | — |
| [#123557](https://github.com/openclaw/openclaw/issues/123557) | ACP session `cwd` not propagated to Gateway `chat.send` | 🦞 diamond lobster | — |
| [#86012](https://github.com/openclaw/openclaw/issues/86012) | LINE messages silently lost due to reply token expiry | 🦞 diamond lobster | — |
| [#86050](https://github.com/openclaw/openclaw/issues/86050) | Gateway buffers claude-cli stream events, surfaces see only final message | 🦞 diamond lobster | — |
| [#122618](https://github.com/openclaw/openclaw/issues/122618) | Compaction-safeguard evicts structured summary body on oversized suffix | 🦞 diamond lobster | — |

### 🟡 P2 / Medium

| Issue | Title | Severity | Fix PR |
|---|---|---|---|
| [#50093](https://github.com/openclaw/openclaw/issues/50093) | WhatsApp backfill missed messages after reconnection | 🐚 platinum hermit | — |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | Live Docs ahead of release (IsolatedSessions missing) | 🦞 diamond lobster | — |
| [#47975](https://github.com/openclaw/openclaw/issues/47975) | Subagent sessions persist after completion, main session unresponsive | 🦪 silver shellfish | — |
| [#120563](https://github.com/openclaw/openclaw/issues/120563) | Conversation history not sent to model on custom/Ollama provider | 🦐 gold shrimp | — |
| [#120735](https://github.com/openclaw/openclaw/issues/120735) | Telegram inbound stickers arrive as raw file refs, not staged to disk | 🦞 diamond lobster | — |
| [#122625](https://github.com/openclaw/openclaw/issues/122625) | Matrix room targets cannot resolve session route (one-way) | 🦞 diamond lobster | — |
| [#53540](https://github.com/openclaw/openclaw/issues/53540) | Embedded runner "Network connection lost" on large tool parameters | 🦞 diamond lobster | — |
| [#86119](https://github.com/openclaw/openclaw/issues/86119) | Orphaned `node server.js` worker processes accumulate after subagent/cron runs | 🦐 gold shrimp | — |
| [#95566](https://github.com/openclaw/openclaw/issues/95566) | WebChat renders assistant reply before user prompt and duplicates inbound messages | 🦪 silver shellfish | — |
| [#84662](https://github.com/openclaw/openclaw/issues/84662) | Codex app-server stores per-turn OpenClaw runtime context in native user history | 🦞 diamond lobster | — |

### Notable Merged Fixes
- [#123914](https://github.com/openclaw/openclaw/pull/123914) — Cron agent-less schedule regression fixed
- [#123901](https://github.com/openclaw/openclaw/pull/123901) — Gateway bundle cache growth bounded
- [#123541](https://github.com/openclaw/openclaw/pull/123541) — `branches.list` event-loop stall on long-lived sessions (in review)

---

## 6. Feature Requests & Roadmap Signals

| Issue | Title | Comments | Likelihood |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source | 51 | Medium — architectural change, needs product decision |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | Per-agent cost budget enforcement | 25 | High — directly addresses production cost concerns; has a linked PR |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent-triggered context compaction (self-compact tool) | 8 | Medium — aligns with ongoing compaction-safeguard work |
| [#71142](https://github.com/openclaw/openclaw/issues/71142) | Configurable upload size limit for Control UI | 8 | Low-Medium — straightforward config addition |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | UI quality update based on UX scoring | 8 | High — multiple UI refactoring PRs already in flight (sidebar, chat header, side rails) |
| [#54373](https://github.com/openclaw/openclaw/issues/54373) | Context Provenance: source/volatility metadata for injected context | 8 | Medium — RFC-stage, would improve memory quality |
| [#50093](https://github.com/openclaw/openclaw/issues/50093) | WhatsApp backfill after reconnection | 12 | Medium — channel-specific, depends on WhatsApp API capabilities |
| [#87362](https://github.com/openclaw/openclaw/issues/87362) | Task flow lifecycle hook events for plugin observability | 5 | Medium — would enable better monitoring integrations |
| [#90788](https://github.com/openclaw/openclaw/pull/90788) | Chain-of-Thought pre-flight planning for long-running goals | — | Low-Medium — large feature, still needs proof |

**Prediction for next release:** Expect the per-agent cost budget (#42475), UI sidebar consolidation (#123597, #123682, #123874), and install-policy acknowledgement (#116489) to land. Context compaction improvements and memory trust tagging are less likely in the immediate next version.

---

## 7. User Feedback Summary

### Pain Points
- **Memory leaks are the #1 production concern.** Multiple users report RSS growing from ~350MB to 15GB+ over days (#91588, #87109), causing OOM crashes and silent cron failures. This is the most cited stability issue across the board.
- **Message delivery is unreliable on group channels.** WhatsApp group replies are dropped when foreground reply fencing cancels earlier concurrent messages (#92186). LINE messages are silently lost due to reply token expiry (#86012). Telegram stickers arrive as raw refs with no description (#120735).
- **File tool path handling is dangerously incorrect.** The `@` prefix stripping bug (#119270) can cause writes and deletes on unintended files — a data-loss risk.
- **Cron reliability degrades under memory pressure.** Cron jobs silently fail with no output or error when the gateway heap is near capacity (#87109, #121953).
- **Ollama/custom provider context loss.** Every turn sends a fixed-size context instead of full conversation history on custom/Ollama providers (#120563), breaking multi-turn coherence.
- **Steer mode broken for main sessions.** User messages are queued instead of injected mid-turn at tool boundaries (#48003), a regression from March 2026.

### Satisfactions
- **Security hardening is appreciated.** The install-policy acknowledgement flow (#116489) and per-turn send budget guard (#120491) address real operational concerns.
- **UI improvements are well-received.** Multiple PRs targeting sidebar consolidation, chat header identity, and incognito session clarity show responsiveness to UX feedback.
- **The project is actively merging fixes.** Several long-standing bugs now have linked PRs in review (#123541, #97175, #91479).

---

## 8. Backlog Watch

### ⚠️ Critical Issues Needing Maintainer Attention

| Issue | Age | Why It's Stalled |
|---|---|---|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | ~2.5 months | P0 memory leak; `clawsweeper:needs-live-repro` — may require a reproducer |
| [#119270](https://github.com/openclaw/openclaw/issues/119270) | ~11 days | P0 file-tool bug with data-loss risk; `clawsweeper:source-repro` |
| [#92186](https://github.com/openclaw/openclaw/issues/92186) | ~2 months | P1 reply-fence bug affecting group WhatsApp usage; no fix PR yet |
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | ~2 months | P1 Codex hook CPU stall; `clawsweeper:needs-live-repro` |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | ~5 months | P1 steer-mode regression since March; `clawsweeper:fix-shape-clear` |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | ~2.5 months | P1 heap growth causing silent cron failures; linked to #86613, #86509 |
| [#50611](https://github.com/openclaw/openclaw/issues/50611) | ~5 months | P2 memory flush never triggers when `reserveTokensFloor == contextWindow`; simple fix but unaddressed |
| [#54409](https://github.com/openclaw

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — Personal AI Agent Open-Source Ecosystem
**Date: 2026-08-15**

---

## 1. Ecosystem Overview

The personal AI agent open-source ecosystem is characterized by **heterogeneous maturity levels** and a common tension between rapid feature expansion and production-grade stability. Eight tracked projects span architectures from full gateway platforms (OpenClaw, IronClaw) to specialized desktop agents (Hermes, CoPaw) to lightweight embeddable runtimes (NanoClaw, PicoClaw). A dominant industry-wide challenge is **session-state integrity** — memory leaks, stale background saves, and cross-session contamination appear across every active project. The community is simultaneously pushing for **multi-channel parity** (WhatsApp, LINE, Telegram, Slack, Discord, WeChat/QQ) and **enterprise-grade reliability** (cost budgets, multi-tenancy, auth diagnostics). Projects that ship faster are accumulating a "stability tax" in the form of unresolved P0/P1 bugs, while those stabilizing are seeing their feature velocity slow.

---

## 2. Activity Comparison

| Project | Open Issues | Open PRs | Today's Updates | Releases (24h) | Net Clear Rate | Health |
|---|---|---|---|---|---|---|
| **OpenClaw** | 485 | 400 | 1,000 | None | −77% (500 in / 100 out) | 🔴 Inflow-heavy, critical bugs |
| **Hermes Agent** | ~120* | ~95* | 100 | None | Moderate | 🟡 Active, Windows pain |
| **CoPaw (QwenPaw)** | ~130* | ~100* | 91 | None (pre-release) | Moderate | 🟡 Pre-release stabilization |
| **ZeroClaw** | 30 | 47 | 83 | None (v0.8.5 freeze) | Healthy | 🟢 Post-intake freeze, hardening |
| **NanoBot** | ~15* | ~20* | 25 | None | Strong | 🟢 High velocity, clean |
| **IronClaw** | ~40* | ~55* | 72 | 1.2.0 line merged | Strong | 🟢 Active, structured QA |
| **LobsterAI** | 2 | ~25* | 29 | ✅ v2026.8.14 | Strong | 🟢 Shipping, Polish-focused |
| **NanoClaw** | 2 | 11 | 13 | None | Moderate | 🟡 Setup friction |
| **PicoClaw** | 3 | 9 | 12 | None | Moderate | 🟡 Critical hang unaddressed |
| **Moltis** | ~5* | ~6* | 0 | None | Stalled | 🟡 Quiet development |
| **NullClaw** | 0 | 0* | ~1 | None | Stable | 🟢 Low activity, no blockers |
| **ZeptoClaw** | — | — | 0 | — | No data | ⚪ Inactive |

*\*Estimated from digest context; exact counts not stated.*

**Health Score Definition:** Combines issue/PR clearance rate, severity distribution of open bugs, release cadence, and community engagement depth.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Largest community and issue stream** — 485 open issues and 400 open PRs indicate the broadest user base and most extensive testing surface. More eyes on the codebase, but also more reported failures.
- **Rich extensibility architecture** — Gateway-bundle caching, cron agent-less scheduling, install-policy acknowledgement, and per-turn send budgets show a mature plugin/security framework unmatched by lighter projects.
- **Deep channel integration** — WhatsApp, LINE, Telegram, Discord, Slack, Matrix, and WeChat/QQ coverage exceeds most competitors.

**Technical approach differences:**
- OpenClaw is a **gateway-centric platform** (agents bound to a central relay), whereas NanoBot and PicoClaw are **agent-first** (single agent with optional channels). Hermes sits in between with a desktop/TUI gateway.
- OpenClaw uses **content-addressed tarballs** for worker-bundle lifecycle management — a sophisticated approach to dependency isolation that few peers match.
- Unlike IronClaw's structured automation epic or ZeroClaw's goal-mode RFC, OpenClaw's architecture is more **event-loop driven** with gateway memory as the central concern.

**Community size:** OpenClaw has the largest community by far (evidenced by comment counts: #121058 with 94 comments, #7707 with 51). Hermes (~31 comments on top issue), ZeroClaw (~22), and NanoBot (lower but more concentrated) follow.

**Key vulnerability:** OpenClaw's scale is its liability — P0 memory leaks (#91588: RSS → 15.5 GB) and file-tool data-loss bugs (#119270) remain unresolved for months, eroding production trust. No peer has a worse stability story at this scale.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Memory / Session-State Integrity** | OpenClaw, NanoBot, CoPaw, Hermes, ZeroClaw | Unbounded RSS growth (#91588), stale background saves overwriting live data (#5271, NanoBot), session identity cross-contamination (#7011, CoPaw), memory flush never triggers (#50611, OpenClaw) |
| **Multi-Channel Parity** | OpenClaw, Hermes, CoPaw, NanoBot, IronClaw | Web UI features (session management, media support) absent on messaging channels; WhatsApp/Telegram stickers as raw refs; LINE reply token expiry; DingTalk/Deltachat parity gaps |
| **Windows / Cross-Platform Compatibility** | Hermes, NanoBot, CoPaw, OpenClaw, ZeroClaw | CRLF memory overwrite (#85825, Hermes), gateway restart kills WeChat/QQ (#83683, Hermes), Windows `os.replace()` crash (#5382, NanoBot), 74 Windows test failures (#7462, ZeroClaw), cmd window flash (#4832, CoPaw) |
| **MCP / Tool Integration Reliability** | CoPaw, PicoClaw, NanoClaw, OpenClaw | MCP tool-not-found after upgrade (#6405, CoPaw), duplicate tool results (#6958, CoPaw), MCP hang on connection failure (#3269, PicoClaw), file tool `@` prefix stripping (#119270, OpenClaw) |
| **Cost / Budget Enforcement** | OpenClaw, ZeroClaw | Per-agent cost budget at gateway (#42475, OpenClaw), atomic action-budget accounting (#9996, ZeroClaw), per-turn send budget guard (#120491, OpenClaw) |
| **Structured Automation / Goal Mode** | IronClaw, ZeroClaw, OpenClaw | Structured automation specs for unattended runs (#6879, IronClaw), goal mode v1 for bounded foreground work (#8303, ZeroClaw), cron reliability under memory pressure (#87109, OpenClaw) |
| **Plugin / Skill Ecosystem** | CoPaw, NanoBot, Hermes, LobsterAI | Dynamic skill loading + auto-unload (#7033, CoPaw), marketplace skills shadowing builtins (#5309, NanoBot), skills index staleness (#66616, Hermes), Creator plugin breaking others (#7025, CoPaw) |
| **Chat Completions / Provider Compatibility** | ZeroClaw, CoPaw, LobsterAI | Chat Completions API profile for OpenAI-protocol (#8603, ZeroClaw), OpenAI-compatible provider 404s (#2303, CoPaw), Gemini URL bug (#1153, LobsterAI) |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | IronClaw | Hermes | NanoBot | CoPaw | PicoClaw | ZeroClaw | LobsterAI |
|---|---|---|---|---|---|---|---|---|
| **Architecture** | Gateway + agents | Gateway + structured automation | Desktop/TUI + gateway | Agent-first | Agent-first + console | Lightweight agent | Agent-first + goal mode | Cowork multi-agent |
| **Primary Users** | Production enterprises, multi-channel ops | Automation workflows, dev teams | Desktop power users, Windows/Mac | Individual developers | Chinese-market users (Feishu/WeChat) | Hardware/embedded (Sipeed) | Privacy/security-conscious | Team collaboration |
| **Technical Differentiator** | Unbounded scale, deep channel coverage | Structured automation specs, pluggable memory | Skill ecosystem (106 social skills), Discord Omniscience | Type safety (Pyright strict), OAuth polish | Dynamic skill lifecycle, per-session model overrides | MCP resilience, TTS integrations | Goal mode, structured execution contracts | WebUI polish, cowork session UX |
| **Deployment Model** | Self-hosted gateway | Self-hosted + hosted | Desktop app | npm/pip package | Desktop + web | Sipeed hardware | Docker/container | Web + desktop |
| **Key Weakness** | Memory leaks, message delivery | Windows stability | Multi-tenant isolation gap | Session data-loss risk | agentscope version incompatibility | MCP hang on failure | Windows CI gap | Windows setup friction |
| **Release Cadence** | Beta (slow) | Bi-weekly EPIC-driven | Monthly | Weekly | Pre-release 2.1.0 | Ad-hoc | Weekly freeze cuts | Frequent |

---

## 6. Community Momentum & Maturity

### Tier 1: Rapidly Iterating (High Velocity, High Churn)
- **OpenClaw** — 1,000 updates/day but only 115 closed. Massive community but critical stability gaps. Maturity paradox: most tested, least reliable in production.
- **Hermes Agent** — 100 updates with 23 merged. Aggressive feature push (Discord Omniscience, 106 social skills) with Windows regressions accumulating.
- **CoPaw** — 91 updates, pre-release 2.1.0 stabilization. High community engagement but critical version incompatibilities (#6612) blocking adoption.

### Tier 2: Active & Structured (Healthy Balance)
- **IronClaw** — 72 updates, 1.2.0 release line merged, v1.3.0 epic in progress. Best structured QA cycle observed. Automation reliability is the focus.
- **NanoBot** — 25 updates, 22 PRs merged. Clean development cadence, rapid bug resolution, strong WebUI polish momentum.
- **ZeroClaw** — 83 updates in post-intake freeze. Hardening phase with architectural RFCs driving decisions. Most disciplined backlog management.

### Tier 3: Stabilizing / Low Activity
- **LobsterAI** — 29 updates but only 2 open issues. Heavy polish/release cycle. Low bug volume, high feature velocity on UI.
- **NanoClaw** — 13 updates. Setup and container edge cases being resolved. Supply-chain signing in progress.
- **PicoClaw** — 12 updates. Critical MCP hang bug unmerged. Small team, constrained bandwidth.
- **Moltis** — 0 updates. Steady backend development but no community buzz.
- **NullClaw** — 1 PR merged. Stable but quiet. Infrastructure-focused.
- **ZeptoClaw** — No activity. Dormant.

---

## 7. Trend Signals

### 1. Session-State Integrity Is the #1 Industry Challenge
Every active project reports memory leaks, stale-schedule corruption, or cross-session contamination. This is not a project-specific problem — it is an **architectural challenge** inherent to long-running agent gateways with event-loop models. Projects investing in bounded caches (OpenClaw's tarball lifecycle), atomic budget accounting (ZeroClaw #9996), and lease-based turn serialization (Hermes #67454) are pioneering solutions the industry will adopt.

### 2. Multi-Channel Parity Expectations Are Rising
Users increasingly expect **feature parity between Web UI and messaging channels** — session management, media handling, and tool results should work identically on WhatsApp as in the browser. Projects lagging here (PicoClaw #3307 closed stale, OpenClaw LINE/WhatsApp gaps) risk losing users to platforms that deliver consistency.

### 3. Windows Is the New Frontline
Three projects (Hermes, NanoBot, ZeroClaw) report Windows-specific P0/P1 bugs in a single day. The industry has historically optimized for Linux/CI, creating a **reliability gap** for desktop users. Projects that invest in Windows-equivalent test coverage (ZeroClaw's 74 failures is a canary) will gain enterprise trust.

### 4. Structured Automation Is the Next Competitive Frontier
IronClaw's v1.3.0 automation epic and ZeroClaw's goal-mode v1 signal that the market is shifting from "chat with an agent" to "reliable unattended execution." Deterministic no-result suppression, model pinning, and preflight grants are the features that will separate hobby projects from production tools.

### 5. Skill/Plugin Ecosystems Are Scaling but Fragmenting
Hermes (106 skills), CoPaw (dynamic loading), and NanoBot (marketplace shadowing) all face index-staleness, conflict, and quality-control challenges. The trend is toward **modular, hot-loadable skill systems** — but the operational complexity (stale indices, shadowing conflicts, Creator-plugin breakage) is outpacing tooling.

### 6. Cost Budgeting Is Moving from Niche to Required
OpenClaw's per-agent gateway budget (#42475) and ZeroClaw's atomic action-budget accounting (#9996) reflect a market shift: agents are no longer free experiments. Enterprises need **hard spend caps at the gateway**, not post-hoc billing alerts. This will become table-stakes.

### 7. Chat Completions Compatibility Is a Force Multiplier
ZeroClaw's Chat Completions RFC (#8603, 19 comments) enables integration with Open WebUI, Aider, Continue.dev, and LangChain. Projects that adopt OpenAI-protocol compatibility will expand their developer ecosystem dramatically — those that don't risk becoming walled gardens.

---

**Bottom Line for Developers:** The ecosystem is moving from "can it chat?" to "can it run reliably at scale?" The projects winning in 2026–2027 will be those that solve session-state integrity and multi-channel parity while maintaining fast feature velocity — currently, **IronClaw** and **ZeroClaw** demonstrate the strongest balance, while **OpenClaw** has the most to gain from fixing its stability tax. **NanoBot** is the dark horse with the cleanest development cadence.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-15

## 1. Today's Overview

NanoBot is experiencing **high development velocity**, with 22 PRs updated in the last 24 hours and active issue triage (3 issues updated, 2 closed). The project is in a strong refinement phase, with significant work on WebUI polish, session management hardening, and type-safety improvements. No new releases were published today, but several merged PRs signal preparation for an upcoming release. Community engagement is healthy with consistent contributor participation.

## 2. Releases

*No new releases published today.*

## 3. Project Progress

**Merged/Closed PRs today:**

- **[#5392](https://github.com/HKUDS/nanobot/pull/5392)** — Fixed Anthropic streaming idle timeout bug (closes #5391), treating `NANOBOT_STREAM_IDLE_TIMEOUT_S` as inactivity-only rather than total timeout.
- **[#5395](https://github.com/HKUDS/nanobot/pull/5395)** — Refined conversation group terminology and shared UI shapes across the WebUI.
- **[#5393](https://github.com/HKUDS/nanobot/pull/5393)** — Polished sidebar hierarchy, session transitions, and grouping visuals (extracted from #5358).
- **[#4689](https://github.com/HKUDS/nanobot/pull/4689)** — Surfaces OAuth status and proactive token expiry warnings across CLI, WebUI, and runtime sessions.
- **[#5018](https://github.com/HKUDS/nanobot/pull/5018)** — Enabled explicit context loading for skills via `ContextBuilder.skill_names`.
- **[#5390](https://github.com/HKUDS/nanobot/pull/5390)** — Agent/knowledge graph feature landed.

**Key open PRs advancing today:**
- [#5396](https://github.com/HKUDS/nanobot/pull/5396) — Narrows Pyright strict-mode suppressions to file level (addresses #5161).
- [#5309](https://github.com/HKUDS/nanobot/pull/5309) — Allows marketplace skills to shadow built-in skills.
- [#5152](https://github.com/HKUDS/nanobot/pull/5152) — Marks partial subagent completion results to prevent model confusion.
- [#5271](https://github.com/HKUDS/nanobot/pull/5271) — Prevents stale background saves from overwriting session data (P0).
- [#5367](https://github.com/HKUDS/nanobot/pull/5367) — Localizes WebUI agent activity labels across 10 locales.
- [#5389](https://github.com/HKUDS/nanobot/pull/5389) — Adds drag-and-drop session organization in WebUI.
- [#5179](https://github.com/HKUDS/nanobot/pull/5179) — Migrates MCP integration to SDK v2 with legacy SSE compatibility.

## 4. Community Hot Topics

- **[Issue #5161](https://github.com/HKUDS/nanobot/issues/5161) / [PR #5396](https://github.com/HKUDS/nanobot/pull/5396)** — Narrowing Pyright `strict`-mode suppressions. Community interest reflects a push toward higher type-safety standards across the codebase.
- **[PR #5309](https://github.com/HKUDS/nanobot/pull/5309)** — Marketplace skills shadowing builtins. Addresses a real friction point for users who want to override bundled skills with custom marketplace versions.
- **[PR #5152](https://github.com/HKUDS/nanobot/pull/5152)** — Partial subagent result marking. Users running multi-subagent workflows reported confusion when partial results were indistinguishable from completed ones.
- **[PR #5356](https://github.com/HKUDS/nanobot/pull/5356)** — Improved WebUI channel setup flows. Reflects demand for a smoother onboarding experience across chat channels.
- **[PR #5358](https://github.com/HKUDS/nanobot/pull/5358)** — Session collaboration via `@mentions`. Signals interest in multi-user or multi-session coordination features.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **P0** | [#5391](https://github.com/HKUDS/nanobot/issues/5391) | Anthropic stream idle timeout kills long but active generations | [#5392](https://github.com/HKUDS/nanobot/pull/5392) ✅ **Merged** |
| **P1** | [#5378](https://github.com/HKUDS/nanobot/issues/5378) | File-cap archive failure mutates session before persistence, causing data loss on callback error | No fix PR yet |
| **P1** | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | Stale background task saves overwrite live session data after `/new` | [#5271](https://github.com/HKUDS/nanobot/pull/5271) 🔶 Open |
| **P2** | [#5382](https://github.com/HKUDS/nanobot/pull/5382) | `os.replace()` transient Windows `PermissionError` crashes the gateway during cron heartbeat saves | [#5382](https://github.com/HKUDS/nanobot/pull/5382) 🔶 Open |
| **P2** | [#5371](https://github.com/HKUDS/nanobot/pull/5371) | Assistant copy/fork actions visible mid-turn in WebUI | [#5371](https://github.com/HKUDS/nanobot/pull/5371) 🔶 Open |

**Notable regression:** The Anthropic timeout bug (#5391) was a regression where a streaming idle timeout was incorrectly applied as a total timeout, prematurely terminating long but active generations. Fixed and merged.

## 6. Feature Requests & Roadmap Signals

- **Session collaboration via mentions** ([#5358](https://github.com/HKUDS/nanobot/pull/5358)) — Users can reference peer sessions with `@name`, indicating demand for multi-session workflows.
- **Drag-and-drop session organization** ([#5389](https://github.com/HKUDS/nanobot/pull/5389)) — Enhanced sidebar UX with grouping and reordering.
- **Interactive particle hero background** ([#5340](https://github.com/HKUDS/nanobot/pull/5340)) — Visual polish for the empty-thread landing state.
- **Native TypeScript terminal UI** ([#4329](https://github.com/HKUDS/nanobot/pull/4329)) — Long-standing request to rebuild the CLI as a TypeScript/OpenTUI client while retaining the Python agent core.
- **OAuth status & expiry warnings** ([#4689](https://github.com/HKUDS/nanobot/pull/4689)) ✅ Merged — Proactive token management.
- **Weather skill** ([#4145](https://github.com/HKUDS/nanobot/pull/4145)) — Community-contributed skill example, still open.

**Prediction:** The next release will likely feature the WebUI collaboration suite (mentions, drag-and-drop, activity localization) and the MCP SDK v2 migration as headline items.

## 7. User Feedback Summary

- **Pain point — Long Anthropic generations getting killed:** Users running extended streaming tasks via Anthropic encountered premature timeouts. Resolved in #5392.
- **Pain point — Session data loss on file-cap overflow:** When the archive callback failed, the session was already mutated, making recovery impossible. Awaiting a fix.
- **Pain point — Gateway crashes on Windows:** Transient `PermissionError` during `os.replace()` in the heartbeat cron job crashes the entire gateway. A Windows-specific reliability gap.
- **Satisfaction — WebUI polish:** Multiple PRs (#5393, #5389, #5371) show the team is actively responding to UX feedback on sidebar organization, action visibility, and visual consistency.
- **Satisfaction — Skill system improvements:** Allowing marketplace skills to shadow builtins (#5309) and supporting explicit context loading (#5018) address real user workflow needs.

## 8. Backlog Watch

| Item | Type | Age | Concern |
|------|------|-----|---------|
| [#5378](https://github.com/HKUDS/nanobot/issues/5378) | Bug (P1) | ~2 days | File-cap archive failure causes silent data mutation — no fix PR yet |
| [#5382](https://github.com/HKUDS/nanobot/pull/5382) | Bug (P2) | ~2 days | Windows `os.replace()` crash — open, no merge yet |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) | Bug (P0) | ~9 days | Stale background save overwrite — open, conflicts possible |
| [#4145](https://github.com/HKUDS/nanobot/pull/4145) | Feature | ~2 months | Weather skill — community contribution, still open |
| [#4329](https://github.com/HKUDS/nanobot/pull/4329) | Enhancement | ~2 months | TypeScript TUI — high interest, long-open, likely needs maintainer decision on scope |

**Overall project health:** **Strong.** High PR throughput, rapid bug resolution (especially P0/P1), and clear momentum on WebUI and session management features. The main risk is the backlog of open session-related bug fixes (#5271, #5378, #5382) which, if left unresolved, could affect data integrity in production.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-15

## 1. Today's Overview

Hermes Agent shows **high development velocity** today with 50 issue updates and 50 PR updates in a single 24-hour window. The project is heavily activity around Discord platform alignment, skill-ecosystem expansion, and Windows/Desktop stability fixes. No new releases were published, but 23 PRs were merged or closed, indicating steady integration momentum. Maintainer attention is sharply focused on the Discord Omniscience campaign and cross-platform session-state bugs.

## 2. Releases

No new releases were published today. The latest version in context is **Hermes 0.20.0** (2026.8.3), with several reported regressions tied to it.

## 3. Project Progress

**Merged / Closed Today:**

- **#86572** (closed) — Escalates repeated stream-drop stalls to the fallback chain, addressing provider streaming failures (e.g., the OpenRouter incident on 2026-08-14). [PR #86572](https://github.com/NousResearch/hermes-agent/pull/86572)
- **#86374** (closed) — Prepends Hermes tool dirs to `slash_worker` PATH, fixing browser-use CLI discovery in Desktop/TUI (salvage of #83854). [PR #86374](https://github.com/NousResearch/hermes-agent/pull/86374)
- **#84859** (closed) — Strips parent venv pointers from `browser-use` subprocess environment, fixing `pydantic_core` ABI mismatch crashes. [PR #84859](https://github.com/NousResearch/hermes-agent/pull/84859)
- **#83785** (closed) — Durable row-id addressing for rewind/edit/regenerate truncation in Desktop/TUI sessions. [PR #83785](https://github.com/NousResearch/hermes-agent/pull/83785)
- **#67017** (closed) — Restores positional `agent` parameter for `anthropic_prompt_cache_policy`. [PR #67017](https://github.com/NousResearch/hermes-agent/pull/67017)
- **#86562** (closed) — Marked duplicate; superseded by #86557.
- **#86576** (closed) — Strips encrypted reasoning tokens on cross-provider delegation/model switch. [PR #86576](https://github.com/NousResearch/hermes-agent/pull/86576)
- **#78647** (closed) — "All Gods Must Die" refactoring epic completed: all god files sharded. [Issue #78647](https://github.com/NousResearch/hermes-agent/issues/78647)

**Notable Open PRs Advancing:**

- **#86183** — Self-repairs FTS5 indexes on SQLite engine change. [PR #86183](https://github.com/NousResearch/hermes-agent/pull/86183)
- **#86575** — New secret-scanner security skill (`detect-secrets` / `trufflehog` backends). [PR #86575](https://github.com/NousResearch/hermes-agent/pull/86575)
- **#86557** — Skills ecosystem Phase 0+1.3 + Phase 1.1: 106 social-media skills, new categories (data-engineering, cloud-native, security). [PR #86557](https://github.com/NousResearch/hermes-agent/pull/86557)
- **#86322** — A2A custom per-peer headers + User-Agent. [PR #86322](https://github.com/NousResearch/hermes-agent/pull/86322)
- **#86355** — Route Matrix project sessions explicitly. [PR #86355](https://github.com/NousResearch/hermes-agent/pull/86355)
- **#86433** — GLM-5.3 support via ZAI provider. [PR #86433](https://github.com/NousResearch/hermes-agent/pull/86433)
- **#86440** — Discord structured inbound message model (Omniscience M1). [PR #86440](https://github.com/NousResearch/hermes-agent/pull/86440)
- **#64384** — Normalize raw Codex Responses stream payloads. [PR #64384](https://github.com/NousResearch/hermes-agent/pull/64384)
- **#67454** — Cross-process turn serialization with DB-level leases. [PR #67454](https://github.com/NousResearch/hermes-agent/pull/67454)

## 4. Community Hot Topics

1. **#78647** — *All Gods Must Die: 20/20 killed* — **78 comments**. The completed god-file sharding epic. [Issue #78647](https://github.com/NousResearch/hermes-agent/issues/78647)
   - Community deeply engaged in architectural cleanup; reflects strong investment in codebase maintainability.

2. **#34352** — *Solving the Multi-Tenant Hermes Problem* — **31 comments, 3 👍**. [Issue #34352](https://github.com/NousResearch/hermes-agent/issues/34352)
   - Memory operations bypassing the hook system makes tenant isolation impossible without forking core. Multiple production deployments are affected. This is a **structural gap** the community is waiting on.

3. **#66616** — *Skills index stale or degraded* — **31 comments**. [Issue #66616](https://github.com/NousResearch/hermes-agent/issues/66616)
   - Automated freshness probe reports index 29.8h old (limit 26h). Impacts `/docs/skills` downstream consumers.

4. **#83683** — *Desktop restart reaps live gateway, never relaunches (WeChat/QQ silent)* — **27 comments, P1**. [Issue #83683](https://github.com/NousResearch/hermes-agent/issues/83683)
   - Windows regression in 0.20.0; messaging gateways go permanently silent after desktop restart. High user impact.

5. **#4064** — *Enable mouse support in TUI* — **13 comments**. [Issue #4064](https://github.com/NousResearch/hermes-agent/issues/4064)
   - Long-standing UX request; `mouse_support=False` hard-coded in `cli.py:1755`.

6. **#67798** — *Lifecycle hooks as shared runtime contract* — **10 comments**. [Issue #67798](https://github.com/NousResearch/hermes-agent/issues/67798)
   - Hooks are currently gateway-owned; other execution surfaces (CLI, cron, TUI) lack them. Community wants parity.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|---|---|---|---|
| **P0** | [#85825](https://github.com/NousResearch/hermes-agent/issues/85825) | `memory replace/remove` silently overwrites entire `MEMORY.md` on Windows (CRLF mismatch) | — |
| **P1** | [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Desktop restart kills gateway, never relaunches (WeChat/QQ silent) — Windows regression | — |
| **P2** | [#84969](https://github.com/NousResearch/hermes-agent/issues/84969) | Persistent Docker reuse ignores immutable config drift | — |
| **P2** | [#85834](https://github.com/NousResearch/hermes-agent/issues/85834) | Per-profile SSH remote resume fails "Session not found" | — |
| **P2** | [#79625](https://github.com/NousResearch/hermes-agent/issues/79625) | Desktop sessions ignore `checkpoints.enabled` — filesystem checkpoints never created | — |
| **P2** | [#86558](https://github.com/NousResearch/hermes-agent/issues/86558) | `gateway restart` crashes with `PermissionError` when `XDG_RUNTIME_DIR` leaks from another user | — |
| **P2** | [#30449](https://github.com/NousResearch/hermes-agent/issues/30449) | `reasoning_content` / `reasoning_effort` never reach OpenAI-compatible SSE stream (DeepSeek backend) | — |
| **P2** | [#86510](https://github.com/NousResearch/hermes-agent/issues/86510) | `read_file` total_lines off-by-one for files without trailing newline | — |
| **P2** | [#86513](https://github.com/NousResearch/hermes-agent/issues/86513) | File dedup/write-staleness stats host FS for remote/container backends | — |
| **P3** | [#86565](https://github.com/NousResearch/hermes-agent/issues/86565) | Session dot stays blue while blocked on approval; only turns amber after opening session | — |
| **P3** | [#68876](https://github.com/NousResearch/hermes-agent/issues/68876) | Provider/model switch leaves UI out of sync with live request | — |
| **P3** | [#85622](https://github.com/NousResearch/hermes-agent/issues/85622) | External memory provider suppresses built-in MEMORY.md injection — contradicts "additive" contract | — |

**Fixed today:** Browser PATH (#86374), browser venv crash (#84859), stream-drop fallback (#86572), FTS5 index repair (#86183), encrypted reasoning token leak (#86576), dotenv CWD warning noise (#85703).

## 6. Feature Requests & Roadmap Signals

- **#34352** — Multi-tenant isolation for memory operations. *High signal; production deployments blocked.*
- **#67798** — Lifecycle hooks as shared runtime contract across all execution surfaces.
- **#4064** — Mouse support in TUI (`mouse_support=True` toggle).
- **#85159** — Route `file://` links and raw local paths through `#media:` in Desktop chat.
- **#86561** — Move existing sessions into Projects post-hoc.
- **Discord Omniscience Campaign** (#79564) — 8+ sub-issues (I1, I3, I4, M1, R3, T5, V1, W3) all opened today, with passing tests. Full API v10 parity push is active.
- **GLM-5.3 support** (#86433) — Added via ZAI provider; rides existing 5.2 wiring.
- **Secret-scanner skill** (#86575) — New security skill with `detect-secrets`/`trufflehog`.

**Predicted for next release:** Discord Omniscience features (I1–I4, M1, R3, T5, V1, W3), secret-scanner skill, GLM-5.3 provider, A2A per-peer headers, Matrix project routing, and the FTS5 self-repair fix.

## 7. User Feedback Summary

- **Windows is a pain point.** Three P0/P1/P2 bugs today are Windows-specific (CRLF memory overwrite, gateway restart regression, file line-count off-by-one). Desktop users report silence from WeChat/QQ/Telegram after restart — a **regression in 0.20.0** causing real workflow disruption.
- **Multi-tenancy is unblocked but fragile.** Enterprise users (#34352) report running production multi-tenant agents with a custom fork because the hook system doesn't cover memory operations.
- **Session state is inconsistent across surfaces.** SSH resume failures, checkpoint silence in Desktop, model-switch desync, and approval-status dot bugs all point to fragmented state management between CLI, Desktop, TUI, and gateway paths.
- **Skills ecosystem is expanding rapidly.** 106 social-media skills and new categories are being ingested, but the index freshness probe (#66616) is already flagging staleness — a scaling concern.
- **Satisfaction signal:** The completed god-file sharding epic (#78647, 78 comments) shows community enthusiasm for architectural hygiene; low reaction counts on bug reports suggests some resignation to the Windows/Desktop stability cycle.

## 8. Backlog Watch

- **#34352** (31 comments, open since May 2026) — Multi-tenant memory isolation. Long-standing, high-impact, no visible fix PR yet.
- **#4064** (13 comments, open since March 2026) — TUI mouse support. Simple toggle but unaddressed for 5 months.
- **#67798** (10 comments, open since July 2026) — Shared lifecycle hooks across execution surfaces. Architectural change needed; no PR yet.
- **#66616** (31 comments, open since July 2026) — Skills index freshness degradation. Cron job may need tuning; no fix merged.
- **#67454** (open since July 2026) — Cross-process turn serialization with DB-level leases. Critical for concurrent session safety; still open.
- **#64384** (open since July 2026) — Codex Responses stream normalization. P2, moderate blast radius.
- **#70375** (open since July 2026) — Redact secrets in Desktop local backend log ring. Security-relevant, still awaiting merge.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-15

---

## 1. Today's Overview

PicoClaw shows active development with 12 issues/PRs updated in the last 24 hours (3 issues, 9 PRs). The project is in a stabilization phase, with a critical bug fix PR (#3337) directly addressing a hang in the agent loop caused by MCP server failures. Five PRs were merged/closed today, focusing on dependency updates, channel fixes, model list refreshes, and new feature additions like DashScope TTS and DingTalk image support. No new releases were published during this window, suggesting the team may be consolidating fixes before the next tag.

---

## 2. Releases

**None.** No new releases were published in the last 24 hours.

---

## 3. Project Progress

**Merged/Closed PRs (5):**

| PR | Author | Description |
|----|--------|-------------|
| [#3303](https://github.com/sipeed/picoclaw/pull/3303) | dependabot[bot] | Bumped `actions/stale` from v10 to v11 — CI housekeeping |
| [#3283](https://github.com/sipeed/picoclaw/pull/3283) | MrTreasure | Added inbound picture/image message support for DingTalk channel |
| [#3279](https://github.com/sipeed/picoclaw/pull/3279) | MrTreasure | Fixed tool-call format leakage into LLM summaries via seahorse's `partsToReadableContent` |
| [#3271](https://github.com/sipeed/picoclaw/pull/3271) | LeaderOnePro | Updated default model names across 9 providers to 2026-07 latest (e.g., OpenAI `gpt-5.6-terra/luna/sol`) |
| [#3270](https://github.com/sipeed/picoclaw/pull/3270) | MrTreasure | Added DashScope (Alibaba Cloud Bailian) TTS provider and WeChat audio file sending |

**Key advances:** TTS capabilities expanded with DashScope support, DingTalk channel gained media handling, and model defaults were refreshed to match current provider catalogs.

---

## 4. Community Hot Topics

- **[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)** — *MCP server connection failure hangs agent loop* — 5 comments, 1 👍. This is the most-discussed open issue and has a corresponding fix PR [#3337](https://github.com/sipeed/picoclaw/pull/3337) (open). Users are heavily reliant on MCP tooling and cannot tolerate unresponsive chat interfaces.

- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222)** — *Deltachat cleanup (-200 LOC)* — Open since July 3. Refactors legacy features, drops hardcoded relay lists, and renames config fields. Signal of a push toward a leaner, more maintainable Delta Chat integration.

- **[Issue #3307](https://github.com/sipeed/picoclaw/issues/3307)** — *Session list/switch command for Telegram and other chat channels* — Closed as stale. Reflects a real user pain point: session management exists only in the Web UI, leaving Telegram/other-channel users without equivalent controls.

- **[Issue #3308](https://github.com/sipeed/picoclaw/issues/3308)** — *Code review: concurrency hazards, goroutine leaks, memory/speed optimizations* — Closed as stale. Indicates community interest in deeper code health audits beyond surface-level bugs.

**Underlying need:** Users demand parity between the Web UI and messaging-channel experiences (session management, media support), and expect robustness guarantees when integrating external MCP services.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|----------|----------|-------------|------------|
| 🔴 Critical | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP server connection failure causes agent loop to hang; chat interface stops replying entirely | PR [#3337](https://github.com/sipeed/picoclaw/pull/3337) open, not yet merged |
| 🟡 Medium | [#3279](https://github.com/sipeed/picoclaw/pull/3279) | Tool-call format leaking into LLM user messages via seahorse summaries | ✅ Merged |
| 🟡 Medium | [#3319](https://github.com/sipeed/picoclaw/pull/3319) | `exec` tool ignores per-run `timeout` and misdeclares `background`/`pty` as string types | ⏳ Open, awaiting review |

**Assessment:** The critical hang bug (#3269 / #3337) remains unresolved and is the top stability concern. If an MCP server is misconfigured or unreachable, the entire chat interface becomes unusable until restart. The exec timeout issue (#3319) is a correctness bug that could cause unexpected behavior in tool-heavy workflows.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Status | Likelihood for Next Release |
|---------|----------|--------|----------------------------|
| Session management for Telegram/other channels | [#3307](https://github.com/sipeed/picoclaw/issues/3307) | Closed (stale) | 🟡 Low — no active PR |
| Configurable default model fallback chain | [#3200](https://github.com/sipeed/picoclaw/pull/3200) | Open | 🟢 High — core reliability feature |
| DashScope TTS + WeChat audio sending | [#3270](https://github.com/sipeed/picoclaw/pull/3270) | ✅ Merged | Already shipped |
| DingTalk image message support | [#3283](https://github.com/sipeed/picoclaw/pull/3283) | ✅ Merged | Already shipped |
| Deltachat cleanup & hardening | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | Open | 🟡 Medium — depends on review bandwidth |
| MCP connection resilience | [#3337](https://github.com/sipeed/picoclaw/pull/3337) | Open | 🟢 High — directly addresses critical bug |

**Prediction:** The next release will likely prioritize the MCP hang fix (#3337) and the configurable fallback chain (#3200), as both address core reliability. Deltachat cleanup may follow if review cycles complete.

---

## 7. User Feedback Summary

**Pain points:**
- **MCP instability is a dealbreaker.** Issue #3269 shows that a single misconfigured MCP server can completely break the chat experience — users expect graceful degradation, not a frozen interface.
- **Channel parity gaps.** Issue #3307 highlights frustration that Web UI features (session management) are absent on Telegram and other channels, creating an inconsistent experience across platforms.
- **Tool schema correctness.** Issue #3319 (exec timeout ignored, boolean options declared as strings) suggests users are building tool-dependent workflows and encountering silent misbehavior.

**Satisfaction signals:**
- Active contributions from multiple maintainers (MrTreasure, LeaderOnePro, kuzmichus, trufae, lc6464) indicate a healthy contributor base.
- New integrations (DashScope TTS, DingTalk images) show the project is expanding ecosystem coverage.
- Dependabot automation keeps CI dependencies current.

---

## 8. Backlog Watch

| Item | Author | Open Since | Concern |
|------|--------|------------|---------|
| [#3307](https://github.com/sipeed/picoclaw/issues/3307) — Session management for Telegram | iamtoricool | 2026-07-30 | High-impact feature request; closed as stale but likely still desired by users |
| [#3308](https://github.com/sipeed/picoclaw/issues/3308) — Concurrency/code-review audit | Rehanasharmin | 2026-07-30 | Proactive community audit; no maintainer response, but relevance is high given Go concurrency patterns |
| [#3222](https://github.com/sipeed/picoclaw/pull/3222) — Deltachat cleanup | trufae | 2026-07-03 | Open for over 5 weeks with no merge activity; large refactor needing maintainer review |
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) — Configurable model fallback chain | lc6464 | 2026-07-01 | Open for over 6 weeks; high-value feature with no merge timeline |
| [#3319](https://github.com/sipeed/picoclaw/pull/3319) — Exec timeout fix | MrTreasure | 2026-08-07 | Open ~8 days; correctness fix awaiting review |
| [#3337](https://github.com/sipeed/picoclaw/pull/3337) — MCP hang fix | kuzmichus | 2026-08-14 | Open 1 day; critical fix, likely needs prompt merge |

**Recommendation:** The backlog is moderate but weighted toward long-open PRs that need reviewer attention. The MCP hang fix (#3337) should be prioritized for immediate merge given its critical severity. The Deltachat cleanup (#3222) and fallback chain (#3200) have been open the longest and would benefit from a maintainer triage decision.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-15

## 1. Today's Overview

NanoClaw saw moderate activity on 2026-08-14, with 2 open issues and 11 open PRs updated in the last 24 hours. No new releases were published. The project is actively resolving setup-time bugs and container-runtime edge cases, while two significant feature skills (Dial channel adapter, stage inbound Discord attachments) continue to advance through review. Community contribution volume is healthy, with six fix-oriented PRs landing on the same day, though no merged/closed PRs were recorded in the window.

## 2. Releases

No new releases were published on this date.

---

## 3. Project Progress

**Merged / Closed PRs (3):**

- **[PR #3242](https://github.com/nanocoai/nanoclaw/pull/3242)** — Closed (unmerged draft). Live-fire test of the signature approver pipeline. Part of a three-PR series by the core team validating agent-image signing workflows.
- **[PR #3243](https://github.com/nanocoai/nanoclaw/pull/3243)** — Closed (merged). Fixed a false-positive failure in `verify-agent-image` where `Enable auto-merge` being unavailable caused the job to fail on drafts and transient API errors. This hardens the supply-chain verification gate.
- **[PR #3244](https://github.com/nanocoai/nanoclaw/pull/3244)** — Closed (unmerged draft). Second live-fire iteration of the signature approver, depended on #3243 now being merged.

**Notable Open PRs Advanced:**

- **[PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050)** & **[PR #3041](https://github.com/nanocoai/nanoclaw/pull/3041)** — Both by @OmriBenShoham; add the Dial channel adapter (SMS + AI voice calls) and integrate it into the channel picker / wizard. These remain open and are the project's most significant feature push this cycle.
- **[PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752)** — Fixes inbound Discord attachment delivery so the agent receives readable content instead of bare `[file: message.txt]` placeholders.
- **[PR #3247](https://github.com/nanocoai/nanoclaw/pull/3247)** — Retires malformed cron strings gracefully instead of re-erroring every scheduler tick.
- **[PR #3246](https://github.com/nanocoai/nanoclaw/pull/3246)** — Fixes Windows container-orphan cleanup silently no-oping due to POSIX-quote handling in `execSync`.

---

## 4. Community Hot Topics

| Item | Type | Author | Link |
|------|------|--------|------|
| Prebuilt image requires AVX2 — SIGILL on Tremont/Elkhart Lake Atoms | Issue #3245 | @sergeykad | [Issue #3245](https://github.com/nanocoai/nanoclaw/issues/3245) |
| `setup.sh` cannot handle "too old" Node due to short-circuit in `install-node.sh` | Issue #3248 | @glifocat | [Issue #3248](https://github.com/nanocoai/nanoclaw/issues/3248) |
| Fix PR for Issue #3248 already open | PR #3249 | @glifocat | [PR #3249](https://github.com/nanocoai/nanoclaw/pull/3249) |
| Stage inbound Discord attachments | PR #2752 | @chubbicorn245 | [PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752) |
| Dial channel — SMS + AI voice | PR #3041 / #3050 | @OmriBenShoham | [PR #3041](https://github.com/nanocoai/nanoclaw/pull/3041) · [PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050) |

**Analysis:** Setup and runtime compatibility dominate current concern. Two issues published the same day both stem from environment assumptions (Node version routing, x86 baseline CPU features). The Discord attachment PR (#2752) being two months old with no merge signals a backlog in review throughput for non-core-team contributions. The Dial integration is the clearest roadmap signal — users want multi-modal channel support beyond chat.

---

## 5. Bugs & Stability

| Severity | Bug | Link | Fix PR |
|----------|-----|------|--------|
| **High** | Prebuilt hardened image fails with `SIGILL` on CPUs without AVX2 (Intel Tremont/Elkhart Lake Atoms) | [Issue #3245](https://github.com/nanocoai/nanoclaw/issues/3245) | — |
| **High** | `setup.sh` routes "too old" Node into install branch that short-circuits on any Node presence, making recovery impossible | [Issue #3248](https://github.com/nanocoai/nanoclaw/issues/3248) | [PR #3249](https://github.com/nanocoai/nanoclaw/pull/3249) |
| **Medium** | Container-orphan cleanup silently no-ops on Windows due to POSIX quotes in shell `execSync` | — | [PR #3246](https://github.com/nanocoai/nanoclaw/pull/3246) |
| **Medium** | Malformed cron strings re-error every sweep tick instead of being retired | — | [PR #3247](https://github.com/nanocoai/nanoclaw/pull/3247) |
| **Low** | Removal docs point at retired `data/env` mirror | — | [PR #3230](https://github.com/nanocoai/nanoclaw/pull/3230) |

**Assessment:** Two high-severity bugs — one a runtime crash on common low-end hardware, the other a broken setup recovery path. Both are actively addressed or have open fix PRs. The Windows container fix and cron fix address operational reliability gaps.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|--------|--------|------------|
| **Dial channel adapter (SMS + AI voice calls)** | [PR #3041](https://github.com/nanocoai/nanoclaw/pull/3041), [PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050) | High confidence — fully scoped feature skill, Wizard integration in progress. Likely in next minor release if review cycles continue. |
| **Discord attachment delivery fix** | [PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752) | High confidence — long-standing pain point, fix is ready but stalled in review. Should land soon. |
| **Attachment issues (general)** | [PR #2427](https://github.com/nanocoai/nanoclaw/pull/2427) | Medium confidence — older PR, unclear scope from summary alone. |
| **Agent-image supply-chain signing** | [PR #3242](https://github.com/nanocoai/nanoclaw/pull/3242), [PR #3243](https://github.com/nanocoai/nanoclaw/pull/3243), [PR #3244](https://github.com/nanocoai/nanoclaw/pull/3244) | In progress — core-team working live-fire tests; not a user-facing feature but infrastructure hardening. |
| **AVX2 baseline or fallback image** | [Issue #3245](https://github.com/nanocoai/nanoclaw/issues/3245) | Implied feature request — users on non-AVX2 CPUs need a working hardened image build. |

---

## 7. User Feedback Summary

- **Setup frustration is the dominant pain point.** Two issues today (#3248, #3245) both describe `setup.sh` or prebuilt images failing on real hardware, with no graceful fallback. Users are hitting walls before they can even run the agent.
- **Discord attachment blindness** ([PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752)) is a high-impact UX gap — users send files in Discord and the agent sees only placeholders. Two-month stall suggests review bottlenecks.
- **Windows container cleanup** ([PR #3246](https://github.com/nanocoai/nanoclaw/pull/3246)) and **malformed cron handling** ([PR #3247](https://github.com/nanocoai/nanoclaw/pull/3247)) indicate users are running production schedules and container workloads on mixed OS environments, hitting edge cases that the core team is now addressing.
- **Supply-chain confidence** is being built through live-fire testing of image signing, suggesting the project is maturing toward enterprise deployment expectations.

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [PR #2427](https://github.com/nanocoai/nanoclaw/pull/2427) — fix: attachment issues | ~3 months | Stale fix for a user-reported bug (#2426) with no merge signal. |
| [PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752) — stage inbound Discord attachments | ~2 months | Critical UX gap; fix is ready but unreviewed. |
| [Issue #3245](https://github.com/nanocoai/nanoclaw/issues/3245) — AVX2 / SIGILL on prebuilt image | 1 day | No fix PR yet. Affects a large segment of low-end/x86 CPU users. Needs either a non-AVX2 build or a clear runtime warning. |
| [PR #3041](https://github.com/nanocoai/nanoclaw/pull/3041) / [PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050) — Dial channel | ~1 month | Feature PRs still open; if this is the next release's flagship addition, continued review momentum is essential. |

**Overall Health Assessment:** NanoClaw is in a solid maintenance-and-features cycle. The core team is actively hardening supply-chain infrastructure and fixing setup/runtime bugs, while external contributors have ready PRs for high-visibility gaps. The main risk is review throughput on non-core-team PRs — three of the four oldest open PRs (including two fix-critical ones) have been open for weeks to months without resolution.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-15

---

## 1. Today's Overview

NullClaw activity on 2026-08-15 is **low**, with no new issues opened and no new releases published. The only notable movement is the merge of a single pull request (#986) addressing SQLite memory database path configurability. The project appears to be in a calm maintenance phase with no active bugs or feature requests being discussed in the last 24 hours. Development momentum is modest but focused on infrastructure flexibility rather than new user-facing features.

---

## 2. Releases

No new releases were published today. The repository shows no version bump or changelog update in the past 24 hours.

---

## 3. Project Progress

**Merged/Closed PR Today:**

- **#986 — GEN-548: make SQLite memory database path configurable** ([PR #986](https://github.com/nullclaw/nullclaw/pull/986))
  - *Author:* gently-whitesnow
  - *Merged:* 2026-08-14
  - *Summary:* Introduces a new `memory.database_path` configuration option for SQLite-backed primary memory engines. When unset, the default behavior is preserved (`<workspace>/memory.db`). The change supports both relative paths (resolved from the workspace) and absolute paths, enabling read-only workspace deployments. Documentation for the new setting was added alongside the code change.
  - *Significance:* This is a **configurability and deployment flexibility** improvement. It matters particularly for users running NullClaw in restricted or read-only filesystem environments where the default workspace-relative path is not viable.

---

## 4. Community Hot Topics

No issues were opened or actively discussed in the last 24 hours. The single relevant item is:

- **[PR #986](https://github.com/nullclaw/nullclaw/pull/986)** — SQLite memory database path configurability
  - *Reactions:* 0 👍 | *Comments:* undefined
  - *Analysis:* The lack of discussion activity suggests this was a straightforward, well-scoped change that didn't require community debate. The feature addresses a niche but real operational need — read-only deployments and custom database placement — indicating the user base includes environments beyond typical local workspaces.

---

## 5. Bugs & Stability

**No bugs, crashes, or regressions were reported today.** Zero open issues and zero closed bug-related items in the last 24 hours suggest the project is in a stable state with no active stability concerns.

---

## 6. Feature Requests & Roadmap Signals

No new feature requests were opened today. However, the merged PR #986 signals that the project is **incrementally expanding deployment flexibility** — supporting read-only workspaces and configurable storage paths. This suggests the roadmap includes continued attention to **operational and infrastructure concerns** rather than bold new feature launches at this time.

---

## 7. User Feedback Summary

No direct user feedback (issues, comments, reactions) was recorded today. The PR #986 itself reflects an underlying user need for **flexible database path configuration**, likely raised by users encountering deployment constraints in read-only or restricted filesystem environments. There is no evidence of widespread dissatisfaction; activity levels are quiet across the board.

---

## 8. Backlog Watch

No items currently require urgent maintainer attention. With zero open issues and no stale or unanswered PRs flagged in the 24-hour window, the backlog appears manageable. The team may want to monitor whether the configurability work in #986 surfaces related requests (e.g., other storage backends beyond SQLite, or additional deployment mode support) in the coming days.

---

**Overall Health Assessment:** 🟡 **Stable / Low Activity** — No blockers, no new releases, and a single infrastructure-focused merge. The project is healthy but not in an active development sprint.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-15

## 1. Today's Overview

IronClaw is in an active development cadence with **25 issues** and **47 PRs** updated in the last 24 hours, indicating a healthy and fast-moving project. The team is simultaneously shipping the **1.2.0 release line** back into `main`, advancing the **unbound-turns architecture switchover**, and making significant progress on **structured automation specs** (part of the v1.3.0 epic #6879). No new releases were published today, but PR #7657 merged the validated `release/2026-08-11` line back into `main`, and PR #7663 forward-ported 1.2 fixes — signaling that 1.2.0 stabilization is wrapping up. QA bug-bashing is underway (epic #7414), and the WebUI design-system hardening is progressing in parallel.

## 2. Releases

**No new releases published today.** The most recent release activity involves the **1.2.0 release line**:

- **#7657** — Merged the `release/2026-08-11` line back into `main`, carrying state-preserving 1.0/1.1→1.2 startup migrations, Windows filesystem/smoke fixes, and release-artifact upgrade canaries.
- **#7663** — Forward-ported independently validated 1.2 fixes (thread-index projection repair, Windows reliability, clean JSON output, runtime `curl` healthchecks) onto `main` without legacy migration baggage.

The next anticipated release is **v1.3.0**, currently targeting structured automation reliability and several unbound-turns follow-ups.

## 3. Project Progress

### Merged / Closed Today

| PR | Summary |
|---|---|
| [#7668](https://github.com/nearai/ironclaw/pull/7668) | Surface provider auth diagnostics in extensions — preserves bounded GitHub error messages and stable codes instead of collapsing 401s to generic re-auth context. |
| [#7666](https://github.com/nearai/ironclaw/pull/7666) | Extension-card truth batch — fixes misleading "Finish Setup" / "Reconnect" UI state and improves install guidance. |
| [#7665](https://github.com/nearai/ironclaw/pull/7665) | Support origin-scoped hosted MCP OAuth (MKT1 shape). |
| [#7658](https://github.com/nearai/ironclaw/pull/7658) | Fix Telegram 2FA gate on migrated DCs; clarify where login codes arrive. |
| [#7655](https://github.com/nearai/ironclaw/pull/7655) | Re-pin Slack/Telegram integration coverage floors to observed reality. |
| [#7657](https://github.com/nearai/ironclaw/pull/7657) | Merge 1.2.0 release line back into `main`. |
| [#7652](https://github.com/nearai/ironclaw/pull/7652) | Measure production DB write workloads (harness for #7591). |
| [#7592](https://github.com/nearai/ironclaw/issue/7592) | Per-turn DB write measurement harness — closed/completed. |
| [#7569](https://github.com/nearai/ironclaw/issue/7569) | Introduced shared `SearchField` component for WebUI. |
| [#7565](https://github.com/nearai/ironclaw/issue/7565) | Fixed missing i18n coverage across exposed WebUI routes. |
| [#7183](https://github.com/nearai/ironclaw/issue/7183) | Per-user LLM model selection — feature request closed (likely addressed or deferred). |
| [#6869](https://github.com/nearai/ironclaw/issue/6869) | DOCX corruption bug — closed (likely fixed or workarounded). |

### Actively Advancing (Open)

- **[Unbound Turns](https://github.com/nearai/ironclaw/pull/7634)** — PR #7634 completes the switchover to prepared-context turns (71-clause conformance audit). Base PR #7562 landed phase-1 design + implementation.
- **[Structured Automations](https://github.com/nearai/ironclaw/issue/6879)** — Epic #6879 driving v1.3.0: PR #7651 adds deterministic no-result suppression; issues #7644–#7647 address preflight grants, model pinning, and structured execution contracts.
- **[Pluggable Memory](https://github.com/nearai/ironclaw/pull/7661)** — PR #7661 introduces an MCP-backed memory provider bound by configuration; issue #7664 tracks the full contract.
- **[ACP Harness Executor](https://github.com/nearai/ironclaw/pull/7648)** — Experimental PR adds a neutral per-run-profile router with an ACP-only harness executor.
- **[WebUI Hardening](https://github.com/nearai/ironclaw/issue/7637)** — Typing the design-system component boundary; shared `InlineNotice` component (#7639); thread-deletion toast replacement (#7638).

## 4. Community Hot Topics

| Topic | Link | Analysis |
|---|---|---|
| **Automation reliability** (#6879 + children) | [Issue #6879](https://github.com/nearai/ironclaw/issues/6879) | The dominant theme. Users report hit-or-miss unattended automation runs, especially on smaller models. The team is responding with a structured execution spec, model pinning, preflight grants, and deterministic suppression — a comprehensive architectural response. |
| **Unbound-turns switchover** (#7634, #7562) | [PR #7634](https://github.com/nearai/ironclaw/pull/7634) | Core architecture migration with heavy design-doc grounding. The 71-clause conformance audit signals rigor; this is a foundational change that will affect all future turn handling. |
| **Slack/Telegram QA bugs** (#7660, #7662, #7659) | [Issue #7660](https://github.com/nearai/ironclaw/issues/7660) · [Issue #7662](https://github.com/nearai/ironclaw/issues/7662) · [Issue #7659](https://github.com/nearai/ironclaw/issues/7659) | Three P2 bugs surfaced in the same QA cycle: false "Reconnect" UI state, MP4 mime-type rejection in Telegram, and cross-user extension state leakage. All indicate integration-layer regressions from recent changes. |
| **Pluggable memory** (#7664, #7661) | [Issue #7664](https://github.com/nearai/ironclaw/issues/7664) · [PR #7661](https://github.com/nearai/ironclaw/pull/7661) | Users want modular memory backends (Mnesis first). Moving from compiled factory arms to configuration-bound providers is a significant architectural shift that enables community extensions. |
| **Extension auth diagnostics** (#7668) | [PR #7668](https://github.com/nearai/ironclaw/pull/7668) | Rich error reporting for provider auth — directly addresses user frustration with opaque 401s and re-auth loops. |

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|---|---|---|---|
| **P1** | [#6879](https://github.com/nearai/ironclaw/issues/6879) | Automation runs are structurally unreliable — same prompt succeeds or produces nothing, especially on small models | In progress: structured spec epic (#6879 children #7644–#7647, PR #7651) |
| **P2** | [#7660](https://github.com/nearai/ironclaw/issues/7660) | Slack shows "Reconnect"/"Finish Setup" despite active connection | PR #7666 addresses card truth |
| **P2** | [#7662](https://github.com/nearai/ironclaw/issues/7662) | MP4 attachments fail with `invalid_value (attachments.mime_type)` in Telegram | Open — no fix PR yet |
| **P2** | [#7659](https://github.com/nearai/ironclaw/issues/7659) | Extensions installed by other users visible on Extensions/Registry page (state leakage) | Open — no fix PR yet |
| **P2** | [#7667](https://github.com/nearai/ironclaw/issues/7667) | Telegram phone-mode login code hint doesn't reflect `sentCode.type_` | PR #7658 partially addresses 2FA/migration path |
| **Bug** | [#6869](https://github.com/nearai/ironclaw/issues/6869) | Generated DOCX files unreadable by Word (corruption) | Closed — resolved |

**Stability assessment:** The project has 3 unresolved P2 bugs from the current QA cycle, all in integration layers (Slack, Telegram, extensions). The critical P1 automation reliability issue has a multi-PR remediation plan in flight. No crash reports or data-loss bugs were filed today.

## 6. Feature Requests & Roadmap Signals

| Request | Link | Likelihood in v1.3.0 |
|---|---|---|
| **Structured automation specs** (deterministic no-delivery, model pinning, preflight grants) | [Issue #6879](https://github.com/nearai/ironclaw/issues/6879) | **High** — already tagged v1.3.0, multiple PRs in flight |
| **Pluggable memory via MCP** (Mnesis as first consumer) | [Issue #7664](https://github.com/nearai/ironclaw/issues/7664) | **High** — PR #7661 is the provider crate; contract issue #7664 tracks completion |
| **Slack-to-Console bridge** with deep links and run metadata | [Issue #7656](https://github.com/nearai/ironclaw/issues/7656) | **Medium** — enhancement, no PR yet; may slip to v1.4.0 |
| **Per-user LLM model selection** | [Issue #7183](https://github.com/nearai/ironclaw/issues/7183) | **Uncertain** — closed today; may have been implemented or deferred internally |
| **ACP harness executor** (claude-code as loop) | [PR #7648](https://github.com/nearai/ironclaw/pull/7648) | **Experimental** — marked experimental; likely a v1.3.0 preview feature |
| **Structured Ask User cards in WebUI** | [Issue #7653](https://github.com/nearai/ironclaw/issues/7653) | **Medium** — OMP-inspired; no PR yet |
| **Shared WebUI components** (SearchField, InlineNotice, typed design system) | [#7569](https://github.com/nearai/ironclaw/issues/7569) · [#7639](https://github.com/nearai/ironclaw/issues/7639) · [#7637](https://github.com/nearai/ironclaw/issues/7637) | **High** — infrastructure hardening, already in progress |

## 7. User Feedback Summary

**Pain points expressed:**
- **Automation unreliability** is the top complaint (#6879). Users running unattended scheduled prompts experience inconsistent results — sometimes the agent responds usefully, sometimes it produces nothing. This is described as "structural, not model noise," which suggests users have lost trust in the automation feature.
- **Opaque extension auth failures** (#7668 context). Users hit generic 401s with no actionable diagnostics, making it hard to resolve provider auth issues.
- **False UI states in Slack** (#7660). The "Reconnect"/"Finish Setup" badge appears despite a working connection, causing confusion and unnecessary intervention.
- **DOCX corruption** (#6869). Users expect IronClaw to generate Office-compatible documents on par with ChatGPT/Claude; corruption breaks this expectation.
- **Telegram login flow confusion** (#7667). Migrated devices and 2FA gates produce unclear error messages about where login codes are delivered.

**Positive signals:**
- The rapid response to QA bugs (multiple fixes landed in the same cycle) suggests an active maintenance posture.
- The structured approach to automation reliability (epic with sub-issues for each concern) indicates the team is taking user feedback seriously with architectural depth.
- WebUI design-system investments (shared components, i18n coverage, typed props) show attention to long-term user experience.

## 8. Backlog Watch

| Issue | Concern |
|---|---|
| [#7662](https://github.com/nearai/ironclaw/issues/7662) — MP4 attachment failure in Telegram | P2 bug with no fix PR; video support is a common user expectation. |
| [#7659](https://github.com/nearai/ironclaw/issues/7659) — Cross-user extension state leakage | P2 bug with no fix PR; potential privacy/isolation concern that needs prompt attention. |
| [#7667](https://github.com/nearai/ironclaw/issues/7667) — Telegram phone-mode code hint | P2 UX bug; PR #7658 covers part of this but the `sentCode.type_` reflection may remain. |
| [#7653](https://github.com/nearai/ironclaw/issues/7653) — Structured Ask User cards in WebUI | Enhancement with no PR; blocks a cleaner interactive flow for WebUI users. |
| [#7664](https://github.com/nearai/ironclaw/issues/7664) — Pluggable memory contract | PR #7661 lands the provider crate, but the full contract (Mnesis integration, publisher docs) is incomplete. |
| [#7624](https://github.com/nearai/ironclaw/issues/7624) — ACP harness executor v0 | Marked as the only pluggable-loops item to build now; depends on validation before subsequent rungs (#7621–#7623) can proceed. |

---

*Generated from GitHub data for 2026-08-15. Project health: **Active** — strong PR velocity, focused QA cycle, clear v1.3.0 roadmap.*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-15

## 1. Today's Overview

LobsterAI saw strong development activity on 2026-08-14, with **27 PRs updated** (5 open, 22 merged/closed) and **2 open issues** remaining active. A new release (2026.8.14) was published, marking continued iteration on the cowork agent experience, UI polish, and dependency updates. Activity is healthy and sustained, with a high merge rate indicating efficient maintainer throughput. The project remains in an active development cadence with no major blockers visible.

---

## 2. Releases

### LobsterAI 2026.8.14

**Key changes:**
- **Sidebar check-in & banner carousel** — new onboarding/promotional UI components ([PR #2411](https://github.com/netease-youdao/LobsterAI/pull/2411))
- **Multi-agent task activity filter** — sidebar now filters activity by agent ([PR #2418](https://github.com/netease-youdao/LobsterAI/pull/2418))

*Note: Release notes were truncated in the provided data; additional changes likely included in the release branch merge ([PR #2498](https://github.com/netease-youdao/LobsterAI/pull/2498), 67 commits ahead, +24,736/-4,253 lines across 264 files), which introduced Team Edition account/quota flows, refreshed Skills and Connectors experiences.*

**Breaking changes / migration notes:** None explicitly reported. A default font-size bump ([PR #2495](https://github.com/netease-youdao/LobsterAI/pull/2495)) includes a "one-time migration," suggesting upstream styles may shift.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Area | Summary |
|----|------|---------|
| [#2499](https://github.com/netease-youdao/LobsterAI/pull/2499) | cowork, renderer | Fix: keep turn process expanded until an answer exists — resolves premature collapse during `sessions_yield` pauses |
| [#2496](https://github.com/netease-youdao/LobsterAI/pull/2496) | cowork, renderer | Fix: badge popovers now stay within viewport and render above later messages |
| [#2495](https://github.com/netease-youdao/LobsterAI/pull/2495) | renderer | Feature: bump default UI/code font sizes with one-time migration |
| [#2494](https://github.com/netease-youdao/LobsterAI/pull/2494) | renderer, account | Fix: replace credits icon with new stacked-points artwork, SVG inlined |
| [#2493](https://github.com/netease-youdao/LobsterAI/pull/2493) | cowork, renderer, artifacts | Fix: session export image and card toggle UI issues |
| [#2492](https://github.com/netease-youdao/LobsterAI/pull/2492) | renderer, account | Fix: align credits icon color across light/dark themes |
| [#2491](https://github.com/netease-youdao/LobsterAI/pull/2491) | openclaw, main | Fix: key `skills.entries` by frontmatter name instead of directory name |
| [#2490](https://github.com/netease-youdao/LobsterAI/pull/2490) | cowork, artifacts | Feature: preview browser annotation attachments in artifact panel |
| [#2497](https://github.com/netease-youdao/LobsterAI/pull/2497) | renderer, docs | Fix: improve cowork goal and steer copy wording (i18n) |
| [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) | openclaw, main | Fix: same skill-key mismatch fix as #2491 (alternative PR) |
| [#2422](https://github.com/netease-youdao/LobsterAI/pull/2422) | multiple | Fix: "btw tools" (merged) |
| [#2423](https://github.com/netease-youdao/LobsterAI/pull/2423) | multiple | Revert of #2422 (merged) |

### Open PRs Notable

- [#2374](https://github.com/netease-youdao/LobsterAI/pull/2374) — **Permanent sidebar ad banner hide toggle** (awaiting review)
- [#2460](https://github.com/netease-youdao/LobsterAI/pull/2460) — Bump `rimraf` 5.0.10 → 6.1.3 (dependabot)
- [#2465](https://github.com/netease-youdao/LobsterAI/pull/2465) — Bump `vite` 5.4.21 → 8.2.1 (dependabot, significant jump)

---

## 4. Community Hot Topics

- **[Issue #1154](https://github.com/netease-youdao/LobsterAI/issues/1154)** — *Add Vitest unit tests for `commandSafety` and `coworkMemoryJudge`* (1 comment, stale)
  - **Why it matters:** These are core safety modules. `commandSafety.ts` prevents destructive command execution; `coworkMemoryJudge.ts` guards memory write quality. Zero test coverage on both is a significant reliability risk, especially as the agent handles more autonomous actions.

- **[Issue #2489](https://github.com/netease-youdao/LobsterAI/issues/2489)** — *"快更新v4pro！"* (1 comment)
  - **Why it matters:** User eagerness for the latest model tier (v4 Pro) indicates strong demand for upgraded capabilities. No official response visible yet.

- **[PR #1153](https://github.com/netease-youdao/LobsterAI/pull/1153)** — *Fix Gemini `/v1` URL拼接错误* (stale)
  - **Why it matters:** Directly affects Gemini API users; a trivial one-line fix that's been open since March.

- **[PR #1155](https://github.com/netease-youdao/LobsterAI/pull/1155)** — *会话内页内搜索（Ctrl+F）* (stale)
  - **Why it matters:** High-utility feature for power users working in long cowork sessions.

---

## 5. Bugs & Stability

| Severity | Item | Details | Fix PR |
|----------|------|---------|--------|
| **Medium** | Turn process collapses prematurely during `sessions_yield` | cowork turn UI folds into an empty line mid-wait, appearing as a failure | [#2499](https://github.com/netease-youdao/LobsterAI/pull/2499) ✅ merged |
| **Low** | Badge popovers overflow viewport or render behind later messages | UI z-index/positioning bug in cowork | [#2496](https://github.com/netease-youdao/LobsterAI/pull/2496) ✅ merged |
| **Low** | Skill toggles silently ineffective when directory name ≠ frontmatter name | OpenClaw skill key mismatch | [#2491](https://github.com/netease-youdao/LobsterAI/pull/2491) & [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) ✅ merged |
| **Low** | Gemini `/v1` baseURL URL concatenation drops slash | `slice(0,-3)` over-trims | [#1153](https://github.com/netease-youdao/LobsterAI/pull/1153) ⏳ open |
| **Low** | Credits icon misaligned / wrong color in light & dark modes | UI consistency | [#2494](https://github.com/netease-youdao/LobsterAI/pull/2494) & [#2492](https://github.com/netease-youdao/LobsterAI/pull/2492) ✅ merged |

**Notable regression watch:** The revert of [#2422](https://github.com/netease-youdao/LobsterAI/pull/2422) via [#2423](https://github.com/netease-youdao/LobsterAI/pull/2423) suggests a tool-related fix may have introduced issues. No follow-up PR visible yet.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood (Next 1–2 Releases) |
|---------|--------|-------------------------------|
| **Permanent sidebar ad dismissal** | [#2374](https://github.com/netease-youdao/LobsterAI/pull/2374) (open PR) | **High** — already implemented, awaiting merge |
| **In-session Ctrl+F search** | [#1155](https://github.com/netease-youdao/LobsterAI/pull/1155) (stale) | **Medium** — feature is complete but not merged; likely needs maintainer review |
| **v4 Pro model support** | [#2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | **Unknown** — no official signal; user demand is clear |
| **Mark session as unread** | [#1228](https://github.com/netease-youdao/LobsterAI/pull/1228) ✅ merged | Already shipped |
| **Vitest test coverage for safety modules** | [#1154](https://github.com/netease-youdao/LobsterAI/issues/1154) | **High priority** — safety-critical; should be addressed soon |

**Signal:** The heavy cowork-area work this week (turn flow, badge popovers, annotation previews, session export) suggests the team is prioritizing the **multi-agent cowork experience** as the main product focus.

---

## 7. User Feedback Summary

- **Praise indicators:** No negative feedback observed in today's data. Merged PRs address real UX pain points (premature collapse, icon misalignment, silent skill toggle failures).
- **Pain points:**
  - Users want **longer-running agent turns** to remain visibly active during pauses — the collapse-to-empty-line bug was a real frustration ([#2499](https://github.com/netease-youdao/LobsterAI/pull/2499)).
  - **Ad banner fatigue** in the sidebar has led to a feature request for permanent dismissal ([#2374](https://github.com/netease-youdao/LobsterAI/pull/2374)).
  - **v4 Pro demand** ([#2489](https://github.com/netease-youdao/LobsterAI/issues/2489)) shows users are tracking model capability upgrades closely and may feel underserved if updates lag.
- **Satisfaction:** The 22 merged PRs in a single day suggest an active, responsive maintainership team, which is a positive signal for project health.

---

## 8. Backlog Watch

| Item | Age | Priority | Notes |
|------|-----|----------|-------|
| [#1154](https://github.com/netease-youdao/LobsterAI/issues/1154) — Vitest tests for safety modules | ~4.5 months | **Critical** | No test coverage on core safety components; stale flag applied |
| [#1153](https://github.com/netease-youdao/LobsterAI/pull/1153) — Gemini URL fix | ~4.5 months | **Medium** | Trivial fix, stale |
| [#1155](https://github.com/netease-youdao/LobsterAI/pull/1155) — In-session Ctrl+F search | ~4.5 months | **Medium** | Feature complete, not merged |
| [#2465](https://github.com/netease-youdao/LobsterAI/pull/2465) — Vite 5→8 bump | 5 days | **Low** | Large dependency jump; may need integration testing |
| [#2374](https://github.com/netease-youdao/LobsterAI/pull/2374) — Permanent ad hide | ~25 days | **Low** | Ready, pending review |

**Recommended maintainer action:** Prioritize reviewing and merging [#1154](https://github.com/netease-youdao/LobsterAI/issues/1154) (safety tests) and [#1153](https://github.com/netease-youdao/LobsterAI/pull/1153) (Gemini URL fix) — both are low-effort, high-impact items that have been pending since March.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-15

## 1. Today's Overview

Moltis shows low daily activity with zero new issues and no merged PRs in the last 24 hours. However, two substantive feature PRs remain open and actively discussed, indicating steady backend development momentum. No releases were published, and the project appears to be in a quiet but productive integration phase focused on channel connectors and durable persistence layers.

## 2. Releases

No new releases published today.

## 3. Project Progress

No PRs were merged or closed today. Active development is concentrated on two open feature branches:

- **[PR #1195](https://github.com/moltis-org/moltis/pull/1195)** — Adds Slack-native live task cards, enabling channel-neutral tool lifecycle updates to render directly within the Slack response stream. Includes privacy safeguards via opaque per-run IDs and canonical tool name registration, with error cleanup on failed streams.
- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — Introduces durable connectors for calendar (CalDAV), email (Gmail, Himalaya v2), and channel-history datasets with provider-neutral persistence, atomic snapshots, scheduling, projections, and bounded local full-text search. Both PRs target the same subsystem: expanding Moltis's channel and data connector surface.

## 4. Community Hot Topics

- **[PR #1195](https://github.com/moltis-org/moltis/pull/1195)** — *Add Slack native live task cards* (0 comments, 0 reactions)
- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — *Add durable calendar, channel, and email connectors* (0 comments, 0 reactions)

Both PRs are from a single author (**penso**) with no community comments yet. The underlying need is clear: Moltis users are pushing for deeper integrations with real-time collaboration and productivity platforms (Slack, Gmail, CalDAV). PR #1190's emphasis on provider-owned schemas and no copied credentials suggests a strong community appetite for privacy-preserving, token-scoped integrations rather than full credential mirroring.

## 5. Bugs & Stability

No bugs, crashes, or regressions reported today. No closed issues or fix PRs were created.

## 6. Feature Requests & Roadmap Signals

Two significant feature PRs on the horizon signal where the roadmap is heading:

- **Slack-native live cards** (PR #1195) — Suggests Moltis is moving toward richer channel-specific UI elements rather than text-only responses.
- **Durable multi-provider connectors** (PR #1190) — Indicates a roadmap shift toward persistent, schedulable integrations with calendar and email providers, with local search as a differentiator.

If both PRs merge without major blockers, the next release will likely be version-incrementing to reflect the connector expansion.

## 7. User Feedback Summary

No new user issues or feedback posted today. The two open PRs represent proactive feature development rather than reactive bug fixes, suggesting the maintainers are driving the roadmap from internal priorities. No expressed user dissatisfaction or pain points are visible in today's data.

## 8. Backlog Watch

- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — Open since **2026-08-11** with last update on 2026-08-14. No comments or reviews yet. This is a large, multi-component PR spanning connectors, persistence, and search — it may be awaiting maintainer review or internal testing before merge. Worth monitoring closely as it is the more structurally significant change of the two.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-15

## 1. Today's Overview

CoPaw (agentscope-ai/QwenPaw) showed **high activity** today with 50 issue updates and 41 PR updates in a 24-hour window, indicating an active development cycle around the 2.1.0 release train. The project closed 37 issues and 15 PRs today, with a healthy open-to-closed ratio of roughly 13:37 on issues. No new official releases were published today, but several feature PRs were merged or advanced significantly. The dominant themes are **skill-system lifecycle management**, **MCP tooling fixes**, **provider compatibility**, and **console UX improvements**.

---

## 2. Releases

No new releases were published today. The latest closed PRs reference version **2.1.0** and **2.0.x.post** variants, suggesting the team is in a stabilization phase prior to an upcoming release.

---

## 3. Project Progress

### Merged / Closed PRs Today
| PR | Description | Status |
|---|---|---|
| [#7031](https://github.com/agentscope-ai/QwenPaw/pull/7031) | feat(skill-system): dynamic skill loading + auto-unload + frontmatter fix | ✅ Closed |
| [#7029](https://github.com/agentscope-ai/QwenPaw/pull/7029) | 动态技能加载+自动卸载+frontmatter修复 (CN) | ✅ Closed |
| [#7030](https://github.com/agentscope-ai/QwenPaw/pull/7030) | feat(auto-title-sync): auto-memory linked chat title refresh | ✅ Closed |
| [#2105](https://github.com/agentscope-ai/QwenPaw/pull/2105) | docs: add Whisper installation instructions | ✅ Closed |
| [#6715](https://github.com/agentscope-ai/QwenPaw/pull/6715) | feat(onebot): localize inbound media before agent processing | ✅ Closed |
| [#6943](https://github.com/agentscope-ai/QwenPaw/pull/6943) | feat(channels): support interactive configurators for plugin channels | ✅ Closed |

### Key Open PRs Advanced
- **[PR #7033](https://github.com/agentscope-ai/QwenPaw/pull/7033)** — Dynamic skill loading + auto-unload + frontmatter fix (refactor/reopening of #7031 with improvements)
- **[PR #6969](https://github.com/agentscope-ai/QwenPaw/pull/6969)** — Fix for duplicate tool results when MCP returns `structuredContent` (addresses #6958)
- **[PR #7037](https://github.com/agentscope-ai/QwenPaw/pull/7037)** — Computer-use: observe related window surfaces, expanding UI Automation coverage
- **[PR #7035](https://github.com/agentscope-ai/QwenPaw/pull/7035)** — Console: organize subagent conversations into grouped views (Cron + subagent sessions)
- **[PR #7036](https://github.com/agentscope-ai/QwenPaw/pull/7036)** — Console: add media download controls (audio player download button)
- **[PR #6302](https://github.com/agentscope-ai/QwenPaw/pull/6302)** — Unify provider discovery, model metadata, routing, and agent controls (catalog-driven provider model)
- **[PR #5992](https://github.com/agentscope-ai/QwenPaw/pull/5992)** — Per-session model overrides (opt-in, disabled by default)
- **[PR #6869](https://github.com/agentscope-ai/QwenPaw/pull/6869)** — Fix background task timeout unification across `submit_to_agent`, CLI, and `spawn_subagent`

---

## 4. Community Hot Topics

### Most Discussed Closed Issues
1. **[Issue #3045](https://github.com/agentscope-ai/QwenPaw/issues/3045)** — 8 comments · Auto model fetch unavailable on Windows desktop (v1.0.1)
2. **[Issue #2418](https://github.com/agentscope-ai/QwenPaw/issues/2418)** — 7 comments · Request for skills-hub management page for easier skill downloads
3. **[Issue #2846](https://github.com/agentscope-ai/QwenPaw/issues/2846)** — 6 comments · Desktop auto-update + Windows taskbar icon fix
4. **[Issue #2303](https://github.com/agentscope-ai/QwenPaw/issues/2303)** — 6 comments · MiniMax `check_connection()` 404 — Anthropic-compatible provider incompatibility
5. **[Issue #7010](https://github.com/agentscope-ai/QwenPaw/issues/7010)** — 6 comments · No true daemon/background mode for `qwenpaw app` via SSH

### Most Discussed Open Issues
1. **[Issue #7011](https://github.com/agentscope-ai/QwenPaw/issues/7011)** — 5 comments · Console stop request cancels active Feishu session across UI sessions (v2.1.0)
2. **[Issue #4001](https://github.com/agentscope-ai/QwenPaw/issues/4001)** — 4 comments · Support manual deletion of individual messages in conversation
3. **[Issue #7025](https://github.com/agentscope-ai/QwenPaw/issues/7025)** — 4 comments · QwenPaw Creator plugin disables all other plugins after installation
4. **[Issue #7016](https://github.com/agentscope-ai/QwenPaw/issues/7016)** — 2 comments · Tool call returns 404 during streaming session
5. **[Issue #6958](https://github.com/agentscope-ai/QwenPaw/issues/6958)** — 2 comments · MCP tool result writes duplicate data to file

**Underlying needs:** Users are pushing for **runtime skill management** (hot-load/unload), **server/SSH deployment support** (daemon mode), **plugin ecosystem stability** (Creator plugin conflict), and **conversation granularity** (per-message delete, session splitting #4436).

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| 🔴 High | [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | Console stop request cancels an active Feishu session when multiple UI sessions exist; session identity cross-contamination | — |
| 🔴 High | [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | QwenPaw 2.0.1 incompatible with agentscope 2.0.4.post1: proactive crashes (Msg.content type) and tool-permission deadlock | — |
| 🟠 Medium | [#6958](https://github.com/agentscope-ai/QwenPaw/issues/6958) | MCP tool result file writes duplicate data (unstructured + structured) when truncation triggers | [#6969](https://github.com/agentscope-ai/QwenPaw/pull/6969) (open) |
| 🟠 Medium | [#6405](https://github.com/agentscope-ai/QwenPaw/issues/6405) | MCP tools report "Tool not found" after upgrading to 2.0; tool name prefix mismatch `[mcp-key]__[tool_name]` | — |
| 🟠 Medium | [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) | Tool call endpoint returns 404 `Tool call not found` during streaming sessions (v2.1.0) | — |
| 🟡 Low | [#6806](https://github.com/agentscope-ai/QwenPaw/issues/6806) | qwenpaw-creator plugin: cannot save any model config on Windows — "Internal Server Error" | — |
| 🟡 Low | [#6972](https://github.com/agentscope-ai/QwenPaw/issues/6972) | Chrome extension WebSocket disconnects after `tab.create` command; JSON-RPC protocol handling bug | — |
| 🟡 Low | [#7040](https://github.com/agentscope-ai/QwenPaw/issues/7040) | Typo: "Stopp Running" instead of "Stop Running" in UI | — |
| 🟡 Low | [#4832](https://github.com/agentscope-ai/QwenPaw/issues/4832) | Shell command subprocess flashes cmd window on Windows (missing `CREATE_NO_WINDOW` flag) | — |
| 🟡 Low | [#6951](https://github.com/agentscope-ai/QwenPaw/issues/6951) | After scroll-compression, pre-compression history invisible on re-entry; only eviction index shown | — |

**Notable:** Issue #6612 (agentscope version incompatibility) and #7011 (session identity collision) are the most severe open bugs, both affecting core agent runtime stability.

---

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Request | Likelihood for Next Release |
|---|---|---|
| [#2763](https://github.com/agentscope-ai/QwenPaw/issues/2763) | `/models` and `/model <provider>-<model>` CLI commands for in-chat model switching | 🟢 High — low-effort, high-value |
| [#4001](https://github.com/agentscope-ai/QwenPaw/issues/4001) | Per-message deletion in conversation (like WeChat long-press) | 🟢 High — UI-level, clearly requested |
| [#4436](https://github.com/agentscope-ai/QwenPaw/issues/4436) | Split conversation: transfer partial messages to a new session | 🟡 Medium — useful for long-context management |
| [#5551](https://github.com/agentscope-ai/QwenPaw/issues/5551) | Native computer use support | 🟡 Medium — PR #7037 shows active work in this direction |
| [#6433](https://github.com/agentscope-ai/QwenPaw/issues/6433) | Zero-setup local GGUF model download & run in-app | 🟡 Medium — significant backend work required |
| [#2314](https://github.com/agentscope-ai/QwenPaw/issues/2314) | Provider-agnostic conversation history (switch providers mid-session) | 🟡 Medium — blocked by format incompatibilities |
| [#7010](https://github.com/agentscope-ai/QwenPaw/issues/7010) | True daemon/background mode for server deployment | 🟡 Medium — infrastructure change |
| [#2846](https://github.com/agentscope-ai/QwenPaw/issues/2846) | Desktop auto-update + proper taskbar icon | 🟢 High — desktop UX polish, likely in next patch |
| [#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) | Per-session model overrides | 🟢 High — PR already open and under review |

**Roadmap signal:** The skill-system lifecycle PRs (#7033, #7029) and provider unification (#6302) suggest the next release will focus on **modularity** (dynamic skills, per-session models) and **provider neutrality**.

---

## 7. User Feedback Summary

**Pain points:**
- **Desktop UX gaps** (#2846, #3464, #4832): Users find manual uninstall-reinstall updates tedious; Windows taskbar shows Python icon instead of CoPaw; cmd windows flash during shell commands.
- **Plugin ecosystem fragility** (#7025, #6806): The Creator plugin breaks other plugins and fails to save configs on Windows — a significant trust issue for the plugin marketplace.
- **MCP integration bugs** (#6405, #6958, #6972): Tool not-found errors and duplicate data writes after the 2.0 upgrade indicate the MCP adapter layer needs hardening.
- **No daemon mode** (#7010): Server/SSH users cannot run CoPaw as a background service, limiting production use cases.
- **Conversation controls** (#4001, #4436): Users want granular control over conversation history — delete individual messages, split sessions — but these are absent.
- **Provider compatibility** (#2303, #3002, #944): OpenAI-compatible providers that only support Responses API (or lack `/models` endpoint) fail to connect, limiting provider choice.

**Positive signals:**
- Strong community engagement (50 issues, 41 PRs in 24h).
- First-time contributors actively participating (#5992, #2105).
- Bilingual PRs and issues (EN/ZH) show a healthy international contributor base.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|---|---|---|
| [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | ~15 days | Critical: agentscope 2.0.4.post1 incompatibility causing proactive crashes and tool-permission deadlocks. Blocks users on latest agentscope. |
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | 1 day (open) | High: Session identity cross-contamination between UI sessions cancels active Feishu conversations. Regression in 2.1.0. |
| [#3045](https://github.com/agentscope-ai/QwenPaw/issues/3045) | ~4 months | Auto model fetch broken on Windows desktop — affects basic onboarding. |
| [#2303](https://github.com/agentscope-ai/QwenPaw/issues/23

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-15

---

## 1. Today's Overview

ZeroClaw is experiencing high development velocity with **33 issues and 50 PRs** updated in the last 24 hours, signaling strong contributor momentum heading into the v0.8.5 stabilization window. The project is in a **post-intake freeze** phase (intake froze August 4); the active backlog of 30 open issues and 47 open PRs reflects ongoing hardening rather than new feature intake. Three issues were closed today, but no new releases were shipped. The security and platform-compatibility workstreams are the most active areas, with multiple high-risk RFCs and bugfixes advancing in parallel.

---

## 2. Releases

**No new releases today.** The project is currently in the v0.8.5 finite stabilization line, tracking through August 30, 2026 ([#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459)). Weekly cuts ship ready work without waiting for every milestone item.

---

## 3. Project Progress

### Merged / Closed Today
- **#6663** — Telegram draft progress during partial streaming ([closed](https://github.com/zeroclaw-labs/zeroclaw/issues/6663))
- **#9982** — Hosted memory proposal (ViBo Cloud API) — marked **wontfix** ([closed](https://github.com/zeroclaw-labs/zeroclaw/issues/9982))

### Key PRs Advanced
| PR | Description | Status |
|---|---|---|
| [#9574](https://github.com/zeroclaw-labs/zeroclaw/pull/9574) | Authorize approval responders across Telegram, Slack, Lark, and Matrix — binds tool approvals to originating chat/room | Open, needs-author-action |
| [#9999](https://github.com/zeroclaw-labs/zeroclaw/pull/9999) | Classify `finish_reason: "length"` as terminal output-limit failure; reject incomplete non-streaming text | Open |
| [#9996](https://github.com/zeroclaw-labs/zeroclaw/pull/9996) | Atomic action-budget accounting to prevent parallel calls from exceeding `max_actions_per_hour` | Open |
| [#9713](https://github.com/zeroclaw-labs/zeroclaw/pull/9713) | Expose token accounting (`tokens_before`/`tokens_after`) on history-trim events for observability | Open |
| [#9839](https://github.com/zeroclaw-labs/zeroclaw/pull/9839) | Block direct spellings of irreversible destructive shell commands via allowlist | Open |
| [#9002](https://github.com/zeroclaw-labs/zeroclaw/pull/9002) | Keep agent turns alive after viewer disconnect — WebSocket is viewer-only, not turn-owner | Open |
| [#9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) | `zeroclaw agents export` — portable agent bundles (manifest + config closure + workspace tree) | Open |
| [#9420](https://github.com/zeroclaw-labs/zeroclaw/pull/9420) | Anthropic stored OAuth profiles support (`auth_mode = "oauth"`) | Open |

---

## 4. Community Hot Topics

| Rank | Issue/PR | Comments | Topic |
|---|---|---|---|
| 1 | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | 22 | Goal mode v1 — bounded foreground Matrix work across agent turns |
| 2 | [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | 20 | Per-execution confirmation tier for high-risk shell commands |
| 3 | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | 19 | Chat Completions profile for OpenAI-protocol client compatibility |
| 4 | [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) | 16 | Pluggable inbound authentication & canonical principals |
| 5 | [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 15 | 74 Windows test failures — Unix-only test commands |
| 6 | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 14 | Runtime-owned conversation sessions & transport adapters |
| 7 | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 14 | Unified attachment architecture for web chat & channels |

**Analysis:** The community is most engaged on **architecture RFCs** — goal mode, shell safety, and Chat Completions compatibility. The top comment counts reflect deep technical debate rather than complaints, indicating a mature contributor base working through design trade-offs. The Windows CI gap (#7462, 15 comments, p1) remains a persistent pain point for non-Linux users.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|---|---|---|---|
| **S1** | [#9421](https://github.com/zeroclaw-labs/zeroclaw/issues/9421) | Incomplete terminal responses reported as successful — workflow blocked | [#9999](https://github.com/zeroclaw-labs/zeroclaw/pull/9999) (open) |
| **S1** | [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 74 Windows test failures — CI only runs on Linux, misses platform bugs | No PR yet |
| **S2** | [#9486](https://github.com/zeroclaw-labs/zeroclaw/issues/9486) | High-entropy detector redacts Solana wallet addresses on Telegram; `high_entropy_tokens=false` ineffective on channel path | No PR yet |
| **S2** | [#9919](https://github.com/zeroclaw-labs/zeroclaw/issues/9919) | Qdrant silently routed to MarkdownMemory fallback without storage config | [#9919](https://github.com/zeroclaw-labs/zeroclaw/pull/9919) (open) |
| **S2** | [#9759](https://github.com/zeroclaw-labs/zeroclaw/issues/9759) | Duplicate enabled webhook ports accepted by Quickstart | [#9759](https://github.com/zeroclaw-labs/zeroclaw/issues/9759) (open) |
| **S3** | [#9983](https://github.com/zeroclaw-labs/zeroclaw/issues/9983) | Fallback model without vision reports incorrect error cause | No PR yet |
| — | [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | cron test hits ETXTBSY race under parallel runtime gate | No PR yet |

**Assessment:** The S1 bug (#9421) has an open fix PR (#9999). The S1 Windows test gap (#7462) has no fix yet — a significant coverage blind spot. The S2 Solana redaction bug (#9486) is a notable usability issue for Web3 users.

---

## 6. Feature Requests & Roadmap Signals

| Feature | Issue | Priority | Signal |
|---|---|---|---|
| Chat Completions API profile | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | p2 | High community interest; enables Open WebUI, Continue.dev, Aider, LangChain integration |
| Goal mode v1 | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | p2 | RFC accepted; core multi-turn objective persistence |
| Agent evaluation harness | [#7065](https://github.com/zeroclaw-labs/zeroclaw/issues/7065) | p2 | In-progress; `zeroclaw eval` with replay + live modes |
| Portable agent bundles | [#9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) | — | PR open; `zeroclaw agents export` |
| Telegram /model picker (paginated, provider-grouped) | [#9895](https://github.com/zeroclaw-labs/zeroclaw/issues/9895) | p2 | Accepted; improves mobile UX |
| Discord role-based authorization | [#9970](https://github.com/zeroclaw-labs/zeroclaw/issues/9970) | p2 | In-progress; additive to existing user-ID allowlist |
| Shell dialect in system prompt | [#9788](https://github.com/zeroclaw-labs/zeroclaw/issues/9788) | p3 | Blocked; improves agent shell command accuracy |
| Staged opt-in telemetry | [#9621](https://github.com/zeroclaw-labs/zeroclaw/issues/9621) | p2 | Needs-maintainer-review; supports product decisions |

**Prediction for v0.8.5:** Chat Completions profile (#8603), goal mode v1 (#8303), and portable agent bundles (#9986) are the strongest candidates for the next release. The agent evaluation harness (#7065) may ship as a follow-up given its complexity.

---

## 7. User Feedback Summary

- **Multi-client compatibility demand:** The Chat Completions RFC (#8603, 19 comments) shows strong demand for OpenAI-protocol compatibility so users can plug ZeroClaw into familiar tooling (Open WebUI, Aider, Continue.dev).
- **Shell safety concerns:** Per-execution confirmation tiers (#7155, 20 comments) and irreversible-command blocking (#9839) indicate users are deploying ZeroClaw in environments where accidental `rm -rf`-style damage is a real risk.
- **Web3 / crypto workflow friction:** Solana wallet address redaction (#9486) is a direct pain point for users integrating blockchain tooling — the high-entropy detector is too aggressive for address formats.
- **Mobile UX on Telegram:** The paginated `/model` picker request (#9895) reflects mobile users struggling with text-based command selection across many configured routes.
- **Windows developer frustration:** 74 test failures (#7462) with no CI coverage signals Windows users feel the project prioritizes Linux, creating adoption friction.

---

## 8. Backlog Watch

| Issue | Days Open | Priority | Blocker |
|---|---|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — Windows test failures | ~66 days | **p1** | No fix PR; CI only runs on Linux |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) — Security posture RFC | ~80 days | p2 | Needs-maintainer-review; foundational for credential boundaries |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) — Provenance & reply contract | ~81 days | p2 | Needs-maintainer-review; revises Aug 5 but stalled |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue | ~42 days | p2 | Tracker for RFC/design decisions; itself needs triage |
| [#9621](https://github.com/zeroclaw-labs/zeroclaw/issues/9621) — Staged telemetry | ~45 days | p2 | Needs-maintainer-review |
| [#

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*