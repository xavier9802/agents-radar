# OpenClaw Ecosystem Digest 2026-09-02

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-02 04:01 UTC

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



# OpenClaw Project Digest — 2026-09-02

## 1. Today's Overview

OpenClaw shows **very high activity** with 500 issues and 500 PRs updated in the last 24 hours, and **1 new release** (v2026.8.2) deployed today. The open-to-closed ratio is healthy: 290 open issues, 210 closed; 336 open PRs, 164 merged/closed. Activity is concentrated around post-upgrade stability problems (2026.8.1 → 2026.8.2 migration regressions) and ongoing session-state / message-delivery bugs. The project is in a high-intensity stabilization phase, with many P0/P1 bugs surfaced by the recent 2026.8.x upgrades.

## 2. Releases

### v2026.8.2 (released today)
- **New feature:** Home agent dock — open Home in a right or bottom dock with `Cmd/Ctrl+Shift+H`, preview or remove work-context snapshots, and attach selected text to messages. Related #133632 (#133676).
- **Desktop companion** features advanced (release notes truncated).
- **No explicit breaking-change notices** in the available release summary.
- ⚠️ **Caution:** Upgrades from 2026.7.1-2 → 2026.8.1/8.2 have been associated with multiple crash-loop and migration failures (see Bugs & Stability). The `openclaw doctor --fix` path has been reported as insufficient for several config-key migrations.

## 3. Project Progress

### Merged / Closed Today
- **#135561** — Docker upgrade survivor stopped before package update; fixed to ensure proper ordering.
- **#124343** (closed) — Fixed subagent yield-ownership settle-wake bug where completed subagent results were never delivered.
- **#134307** (closed) — Authenticated MCP servers (`auth: "oauth"`) missing from Claude CLI runtime tool catalog.
- **#134608** (closed) — Auth migration archived credentials without making them available, blocking repair.
- **#134331** (closed) — `doctor --fix` loop reporting legacy workspace conflicts on every run.
- **#135566** (closed) — Utility simple-completion ignored Claude CLI runtime for canonical and CLI model refs.
- **#135171** (closed) — Perplexity plugin capability-consent crash-loop on startup.
- **#134453** (closed) — Windows `doctor --fix` abort with bare "file not found" vs. interactive doctor succeeding.
- **#37634** (closed) — `sandbox.workspaceAccess: "none"` workspaces mounted read-only; now writable.
- **#107227** (closed) — 2026.7.1 startup-migration gate fatal; repair path not resolving conflict.

### Open PRs Advanced Today
- **#135884** — Fix Codex voice replies preserving inbound audio.
- **#135016** — Fix browser messages becoming interrupted during gateway startup recovery.
- **#135800** — Fix memory reindex livelock from concurrent writes.
- **#135812** — Codex MCP tool approvals now respect session posture; "Allow Always" persists.
- **#135870** — Discord bound voice capture consolidated under one lifecycle owner.
- **#135868** — Triage now owns recovery after update and startup failures.
- **#135851** — Control UI history loading speed improvement.
- **#135808** — Native standalone Apple Watch realtime voice client.
- **#135877** — Docker runtime image build speed improvement.
- **#135857** — Chrome MCP endpoint policy enforcement for CDP.

## 4. Community Hot Topics

### Most Commented Open Issues
| Issue | Comments | Highlights |
|-------|----------|------------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice retains unbounded provider/consult state | 59 | P1, gold shrimp; resource limits in voice sessions |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) — Large SQLite transcript cleanup blocks gateway event loop | 16 | P1, diamond lobster; full materialization on gateway thread |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) — WhatsApp 1:1 inbound image wedges main lane ~3 min | 14 | P1, platinum hermit; multimodal injection stalls `active_reply_work` |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) — Umbrella: duplicate transcript/replay/context across channels | 14 | P1, gold shrimp; systemic cross-channel bug class |
| [#53763](https://github.com/openclaw/openclaw/issues/53763) — Built-in headless browser for reliable web access | 12 | P3, tidepool; feature request for first-class Chromium bundling |
| [#133984](https://github.com/openclaw/openclaw/issues/133984) — 2026.7.1→2026.8.1 leaves Gateway unstartable | 11 | P1, diamond lobster; `doctor --fix` skips config-key migrations |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) — unreaped hook/tool child processes → zombie accumulation | 10 | P1, silver shellfish; runtime degradation over time |
| [#127229](https://github.com/openclaw/openclaw/issues/127229) — Telegram watchdog-false-tombstone on durable updates | 10 | P1, diamond lobster; message-loss under context-overflow compaction |

**Analysis:** The dominant theme is **session-state reliability and resource cleanup** — voice state leaks, SQLite contention, zombie processes, and duplicate transcript assembly across channels. The second theme is **upgrade migration pain** (2026.8.x). Users are also pushing for **more robust web access** (headless browser) and **A2A dispatch semantics** (#44309).

## 5. Bugs & Stability

### P0 / Critical (Today)
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#135171](https://github.com/openclaw/openclaw/issues/135171) | 2026.8.1–8.2 gateway crash-loop: Perplexity requires capability consent but cannot be inspected/enabled/disabled | — |
| [#107227](https://github.com/openclaw/openclaw/issues/107227) | 2026.7.1 startup-migration gate fatal; `doctor` cannot resolve | Closed |
| [#133984](https://github.com/openclaw/openclaw/issues/133984) | 2026.7.1→2026.8.1 Gateway unstartable; `doctor --fix` skips config-key migrations | — |
| [#134608](https://github.com/openclaw/openclaw/issues/134608) | Auth migration archives JSON without making credentials available, blocks repair | Closed |
| [#134453](https://github.com/openclaw/openclaw/issues/134453) | Windows `doctor --fix` aborts with bare "file not found" | Closed |
| [#134331](https://github.com/openclaw/openclaw/issues/134331) | `doctor --fix` loop; silently dead-letters all Discord messages | Closed |
| [#134307](https://github.com/openclaw/openclaw/issues/134307) | OAuth MCP servers absent from Claude CLI runtime tool catalog | Closed |
| [#135566](https://github.com/openclaw/openclaw/issues/135566) | Utility simple-completion ignores Claude CLI runtime for model refs | Closed |

### P1 High-Severity (Today)
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | Realtime voice unbounded provider/consult state retention | — |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | Large SQLite transcript cleanup blocks gateway event loop | — |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | WhatsApp 1:1 inbound image wedges main lane ~3 min | — |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | Umbrella: duplicate transcript/replay/context across channels | — |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | unreaped hook/tool child processes → zombie accumulation | — |
| [#127229](https://github.com/openclaw/openclaw/issues/127229) | Telegram watchdog falsely tombstones durable updates | — |
| [#115546](https://github.com/openclaw/openclaw/issues/115546) | CLI-budget compaction timeout fires far below deadline; 100% failure on large sessions | — |
| [#135347](https://github.com/openclaw/openclaw/issues/135347) | Forced memory reindex inflates shared agent DB to 35 GB; deleting it destroys sessions | #135800 |
| [#134925](https://github.com/openclaw/openclaw/issues/134925) | Gateway main thread hits ~100% CPU on every agent turn on ARM64/Pi | — |
| [#117262](https://github.com/openclaw/openclaw/issues/117262) | SQLite contention: 3 concurrent write handles cause ~33s event-loop stalls | — |
| [#87407](https://github.com/openclaw/openclaw/issues/87407) | Anthropic `UND_ERR_SOCKET` keep-alive failures → silent mid-turn fallback to OpenAI/Codex | — |
| [#118386](https://github.com/openclaw/openclaw/issues/118386) | Stuck-session recovery aborts healthy runs at 6 min when quiet window is a `model_call` | — |
| [#134570](https://github.com/openclaw/openclaw/issues/134570) | 2026.8.1 upgrade: 7 distinct crash-loop and dispatch-failure blockers | — |

### Notable Closed Today
- **#135171** (P0) — Perplexity capability-consent crash-loop → closed.
- **#107227** (P0) — Startup-migration gate fatal → closed.
- **#134453** (P0) — Windows `doctor --fix` abort → closed.

**Stability Assessment:** The 2026.8.1 → 2026.8.2 upgrade path is the **single largest source of instability**, with at least 7 distinct P0/P1 blockers reported today. SQLite contention, session-state leaks, and zombie process accumulation indicate systemic resource-management weaknesses. Several critical bugs have closed today, but many remain open without visible fix PRs.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Rating | Signals |
|-------|---------|--------|---------|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built-in headless Chromium for reliable web access | tidepool | Strong demand for dependable web browsing without external dependencies |
| [#44309](https://github.com/openclaw/openclaw/issues/44309) | One-way A2A dispatch mode (no reply-back ping-pong) | tidepool | Multi-agent operators need fire-and-forget handoffs |
| [#66252](https://github.com/openclaw/openclaw/issues/66252) | Per-agent TTS/STT overrides for multi-language | tidepool | Multi-language agent deployments |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | Self-hosted STT/TTS in webchat (bypass browser Speech API) | diamond lobster | Privacy-focused self-hosted deployments |
| [#49259](https://github.com/openclaw/openclaw/issues/49259) | Prune stale orphaned sessions from Dashboard | tidepool | Cleanup of dead sessions from deleted channels |
| [#8724](https://github.com/openclaw/openclaw/issues/8724) | Per-model generation timeout config | diamond lobster | Google/Gemini models stuck in infinite thinking loops |
| [#46058](https://github.com/openclaw/openclaw/issues/46058) | Chat-first Android surface (external fork discussion) | tidepool | Mobile-native OpenClaw usage |
| [#76247](https://github.com/openclaw/openclaw/issues/76247) | Native dispatch landing ACK / receiver-entry telemetry | diamond lobster | Multi-agent deployment observability |

**Likely next-version candidates:** The Apple Watch voice client (#135808) is already in PR and likely imminent. Per-model timeouts (#8724) and headless browser (#53763) have been open for months with sustained interest. A2A one-way dispatch (#44309) aligns with the multi-agent trajectory.

## 7. User Feedback Summary

**Pain Points:**
- **Upgrade path is broken:** Multiple users report that upgrading from 2026.7.1-2 → 2026.8.1/8.2 leaves the gateway crash-looping or unable to start, with `doctor --fix` providing misleading or no help. This is the #1 complaint today.
- **Session state leaks:** Voice sessions, SQLite transcripts, and child processes are not being properly cleaned up, causing degradation over time.
- **Cross-channel message loss:** WhatsApp images wedge the main lane, Telegram durable updates are falsely tombstoned, and Discord messages are silently dead-lettered.
- **Silent model fallback:** Anthropic socket failures silently switch to OpenAI/Codex without user awareness (#87407).
- **Internal reasoning leakage:** Users report agent chain-of-thought being exposed in responses after upgrading to 2026.6.5 (#91804).
- **Resource exhaustion on ARM64:** Gateway hits 100% CPU per turn on Raspberry Pi (#134925).
- **Poor UX for background tasks:** Long-running cron/droplet tasks fail silently with no recovery path (#88087); one user tore down their entire deployment.

**Satisfaction Signals:**
- The Home agent dock feature (#133676) is well-received as a quality-of-life improvement.
- Several bugs have been resolved in v2026.8.2 (Perplexity crash, Windows doctor, auth migration, MCP tool catalog).
- Performance PRs (Control UI history loading, Docker build speed) address real operational friction.

## 8. Backlog Watch

### Long-Standing P1 Issues Needing Maintainer Attention
| Issue | Created | Comments | Status |
|-------|---------|----------|--------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice unbounded state | 2026-07-30 | 59 | `no-new-fix-pr`, `needs-maintainer-review` |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) — SQLite transcript cleanup blocks event loop | 2026-07-21 | 16 | `no-new-fix-pr`, `needs-product-decision` |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) — WhatsApp image wedge | 2026-06-25 | 14 | `no-new-fix-pr`, `needs-live-repro` |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) — Umbrella: duplicate transcript across channels | 2026-04-20 | 14 | `no-new-fix-pr`, `needs-product-decision` |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) — Zombie child process leak | 2026-06-29 | 10 | `no-new-fix-pr`, `needs-maintainer-review` |
| [#117262](https://github.com/openclaw/openclaw/issues/117262) — SQLite contention (DEF-61) | 2026-08-01 | 6 | `no-new-fix-pr`, linked

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report — 2026-09-02

## 1. Ecosystem Overview

The 2026 personal AI agent open-source landscape is characterized by intense stabilization sprints across major platforms, with OpenClaw, Hermes Agent, and ZeroClaw driving the highest development velocity. A clear industry pattern has emerged: projects are moving from feature-heavy early growth phases into rigorous reliability hardening — focusing on session-state management, upgrade migration paths, multi-agent security boundaries, and Docker-deployment correctness. Community contributors are increasingly active in security and architecture RFC processes, while maintainers across all projects are battling similar systemic issues: SQLite contention, zombie process accumulation, and silent failure modes in provider integrations.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Open/Closed Ratio | Health |
|---------|-------------|-----------|---------|-------------------|--------|
| **OpenClaw** | 500 | 500 | v2026.8.2 (today) | 290 open / 210 closed | 🔴 High-intensity stabilization |
| **Hermes Agent** | 50 | 50 | None | ~35 open / 15 closed | 🟡 Stabilization sprint |
| **ZeroClaw** | 36 | 50 | None | 49 open / 1 merged | 🟢 Strong pipeline |
| **CoPaw (QwenPaw)** | 30 | 40 | v2.2.0-beta.6 | ~20+ open / several closed | 🟢 Strong |
| **IronClaw** | 13 | 19 | None | ~10+ open / several closed | 🟢 High-velocity refinement |
| **LobsterAI** | 12 | 9 | None | ~8+ open / several closed | 🟡 Stable with growing backlog |
| **NanoBot** | 3 | 15 | None | 3 open / 6 closed | 🟢 Healthy |
| **NanoClaw** | 2 | 12 | None | 2 open / ~6 merged | 🟢 Healthy |
| **Moltis** | 2 | 4 | None | 0 open / 2 merged | 🟢 Stable |
| **PicoClaw** | 3 | 4 | None | 3 open / 1 closed | 🟡 Stable, understaffed |
| **ZeptoClaw** | 0 | 2 | None | 0 open / 1 merged | ⚪ Quiet/maintenance |
| **NullClaw** | 0 | 0 | None | — | 🔴 Inactive |

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale of activity** is an order of magnitude above all other projects (500/500 vs. next-highest Hermes at 50/50), indicating the largest contributor base and most active community.
- **Release cadence** is the only project shipping daily releases with documented feature work (Home agent dock, Apple Watch voice client, Codex MCP approval persistence).
- **Multi-channel breadth** — Telegram, WhatsApp, Discord, Apple Watch, Docker, Chrome MCP — is unmatched; most competitors focus on 1–3 channels.

**Technical Approach Differences:**
- OpenClaw treats the gateway as a single-threaded event loop with SQLite-backed persistence, creating well-documented contention problems (#117262, #112423) that no other project has publicly exposed at this scale.
- ZeroClaw and Hermes are pursuing microkernel/WASM plugin architectures; OpenClaw remains a monolithic Rust/TypeScript gateway — simpler to deploy but harder to scale reliability-wise.
- OpenClaw's `doctor --fix` migration tool is the only project-wide repair mechanism reported, but it is currently failing users on the 2026.8.x upgrade path.

**Community Size:** OpenClaw's 500+ daily issue/PR volume dwarfs the next largest (Hermes at ~50), suggesting a contributor base 10× the size. CoPaw and ZeroClaw occupy a strong second tier.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Affected | Specific Needs |
|------------|------------------|----------------|
| **Session-state reliability** | OpenClaw, Hermes, ZeroClaw, CoPaw | Voice state leaks, SQLite contention, zombie process cleanup, duplicate transcript assembly across channels |
| **Upgrade/migration pain** | OpenClaw, CoPaw, Moltis | Broken `doctor --fix` paths, config-key migration failures, silent data loss on config save |
| **Multi-agent security boundaries** | ZeroClaw, CoPaw, OpenClaw | Delegate bypass of parent tool allowlists (#8279, #10165), MCP whitelist enforcement gaps (#7470), sub-agent credential inheritance |
| **Docker/deployment correctness** | IronClaw, Moltis, OpenClaw, LobsterAI | Rootless sandbox UID/GID mismatch (#8015), bind-mount SQLite permissions (#293), container runtime regressions |
| **Channel reliability** | OpenClaw, PicoClaw, NanoBot, Hermes | WhatsApp image wedging, Telegram reply threading, Feishu/Lark config regressions, Slack callback deduplication |
| **Token/cost efficiency** | IronClaw, OpenClaw | GitHub API response bloat (519 KB → compacted), OpenAI prompt cache hit collapse (82%→29%), tool-search envelope truncation |
| **Observability & state visibility** | CoPaw, ZeroClaw, Hermes | Multi-agent sub-status opacity, delegate progress receipts, cron duplicate firing, silent model fallback |
| **Provider compatibility** | ZeroClaw, Hermes, OpenClaw, CoPaw | Anthropic `thinking.display` passthrough, Bedrock Converse whitespace rejection, streaming vs. non-streaming gateway divergence |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | CoPaw (QwenPaw) | IronClaw | NanoBot |
|-----------|----------|-------------|----------|-----------------|----------|---------|
| **Primary focus** | Universal gateway + multi-channel | Desktop-first agent with session branching | RFC-driven architecture + WASM plugins | Enterprise-grade with test coverage sprint | Rust-native agent loop + WebUI unification | Lightweight TUI + Feishu/workspace integration |
| **Target users** | Power users, multi-channel operators | Desktop power users, multi-profile teams | Architecture-focused contributors, security-conscious deployers | Enterprise/organizational deployments | Developers wanting clean Rust architecture | Chinese-market (Feishu/Lark) users |
| **Architecture** | Monolithic gateway + SQLite | Desktop + gateway split | Modular WASM plugins + RFC governance | Plugin-based with aggressive test infrastructure | Rust agent-loop decomposition | Compact Python/TUI |
| **Release approach** | Frequent patch releases (daily) | Infrequent releases, rapid PR turnover | Release-hold for RFC/security validation | Beta-track with test sprints | Active QA sprint (epic #8026) | Steady, no major releases |
| **Key differentiator** | Channel breadth + Apple Watch client | Desktop session branching UX | Formal RFC process + security hardening | Test coverage (1,400+ cases/week) + ReMe memory | Agent-loop refactoring + token efficiency | File operations + ephemeral context |

---

## 6. Community Momentum & Maturity

| Tier | Projects | Characteristics |
|------|----------|-----------------|
| **Rapid Iteration** | OpenClaw, CoPaw, ZeroClaw | High daily volume, active PR pipelines, frequent community contributions, but also high bug-surface from velocity |
| **Stabilization Sprint** | Hermes Agent, IronClaw | Clear focus on fixing existing regressions (branching UX, agent-loop, Slack), fewer new features, more maintenance PRs |
| **Steady Growth** | NanoBot, NanoClaw, Moltis | Healthy contributor ratios, clear issue-to-PR alignment, manageable backlog, no critical blockers |
| **Maintenance Mode** | PicoClaw, LobsterAI | Active but understaffed; long-open issues (#3269 stale 44 days, #1105/#1107 at 5 months), backlog accumulation |
| **Quiet/Inactive** | ZeptoClaw, NullClaw | ZeptoClaw: dependency-only activity. NullClaw: zero activity |

**Maturity Signal:** OpenClaw and CoPaw are past the "feature race" stage and into reliability maturity challenges. ZeroClaw is the only project with a formal RFC governance process, indicating architectural maturity. Hermes and IronClaw are in the classic "fix what broke during scale-up" phase.

---

## 7. Trend Signals

**1. Session-State as the #1系统性 Challenge**
Every major project (OpenClaw, Hermes, ZeroClaw, CoPaw) reports SQLite contention, voice-state leaks, or zombie-process accumulation. This signals the industry is hitting a fundamental limit in single-process event-loop architectures with shared persistence. *Value for developers:* Multi-process or actor-model architectures may become the default for production deployments.

**2. Upgrade Migration as a Trust Crisis**
OpenClaw's `doctor --fix` failures and CoPaw's config-persistence bugs are eroding user confidence. The trend toward more complex state schemas (MCP servers, OAuth credentials, session branches) makes migration increasingly fragile. *Value for developers:* Invest in backward-compatible config schemas and additive-only migrations; assume `doctor` tools will fail in production.

**3. Multi-Agent Security Boundaries Are Porous**
ZeroClaw's delegate bypass bugs (#8279, #10165), CoPaw's MCP whitelist bypass (#7470), and OpenClaw's silent model fallback (#87407) all point to a pattern: sub-agent and tool-level trust boundaries are inconsistently enforced. *Value for developers:* Audit delegation chains and tool-permission inheritance in any multi-agent system before production deployment.

**4. Token Efficiency Is Now a First-Class Concern**
IronClaw's GitHub payload bloat fix and prompt-cache regression, combined with OpenClaw's memory-reindex inflation (35 GB DB), show that cost-per-turn is a user-facing metric. *Value for developers:* Implement response compaction, payload projection, and prompt-caching headers as default behavior.

**5. Docker/Rootless Deployment Is a Production Blocker**
IronClaw (#8015), Moltis (#293), and OpenClaw (Docker build regressions) all surface deployment-friction bugs. Non-root and bind-mount scenarios are consistently under-tested. *Value for developers:* Rootless Docker should be a CI test target, not an afterthought.

**6. RFC-Driven Architecture Is Emerging**
ZeroClaw's formal revision process (Rev 5, Rev 10) is the only project using structured design governance. This correlates with longer decision cycles but potentially more durable architecture. *Value for developers:* Consider lightweight RFC processes for projects with multi-contributor architecture decisions.

**7. Cron/Scheduled Automation Reliability Is Underinvested**
CoPaw (3 related cron issues in 48h), LobsterAI (ghost events after `stopPolling`), and OpenClaw (silent cron task failures #88087) all show that scheduled task systems are fragile across the ecosystem. *Value for developers:* Treat cron/droplet reliability as a differentiator — most projects treat it as secondary.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-02

## 1. Today's Overview

NanoBot shows strong development velocity with **15 PRs** and **3 issues** updated in the last 24 hours, indicating an active contributor base and a productive release cycle. Six PRs were merged or closed today, with notable fixes landing for agent lifecycle management, TUI input handling, and Dream prompt duplication. Two open issues highlight ongoing UX gaps — file copy operations remain broken in workspace contexts, and runtime context persistence lacks fine-grained control (though a fix PR is already open). No new releases were published during this window.

## 2. Releases

*No new releases in the last 24 hours.*

---

## 3. Project Progress

**Merged / Closed PRs (6):**

| PR | Summary |
|----|---------|
| [#5622](https://github.com/HKUDS/nanobot/pull/5622) | **Fix:** Stop duplicating SOUL/USER/MEMORY into the Dream prompt — eliminates redundant context injection that was inflating request size. |
| [#5621](https://github.com/HKUDS/nanobot/pull/5621) | **Fix:** Preserve input typed after submit in the TUI — seals deferred submissions before the next keyboard event, keeping drafts intact. |
| [#5603](https://github.com/HKUDS/nanobot/pull/5603) | **Fix:** Detect turns that claim to perform an action but never emit a tool call — closes part of #1697, addressing silent agent hallucination. |
| [#5569](https://github.com/HKUDS/nanobot/pull/5569) | **Refactor:** Extract tool execution boundary into `nanobot.agent.tools.execution` — decouples execution from `AgentRunner`, improving testability. |
| [#5430](https://github.com/HKUDS/nanobot/pull/5430) | **Fix:** Release completed task groups from `_active_tasks` — resolves memory leak in long-running gateways. |
| [#5604](https://github.com/HKUDS/nanobot/pull/5604) | **Docs:** Clarify that `edit_file` match selectors (`occurrence`, `line_hint`, `replace_all`) are mutually exclusive. |

**Key advances in progress (open PRs):**

- **#5627** — Implements `ephemeral` runtime-context blocks (addresses #5586), allowing transient context to bypass persistence across turns.
- **#5626** — Adds first-class `copy_file` and `move_file` tools to the agent toolset, directly responding to the workflow gap described in #2061.
- **#5624** — Fixes WebUI session deletion for unpersisted panes, including regression coverage for server-side drift after gateway restarts.
- **#5625** — Introduces a first-run AI setup flow replacing the current error-state UX.
- **#5614** — Adds streaming rich-message support for Telegram.

---

## 4. Community Hot Topics

| Item | Activity | Analysis |
|------|----------|----------|
| [#2061](https://github.com/HKUDS/nanobot/issues/2061) — *Unable to copy files inside workspace* | Open since 2026-03-15, updated 2026-09-01, 3 comments | Users relying on Feishu integration expect natural file operations; the agent's inability to complete copies is a persistent friction point. PR #5626 directly targets this gap. |
| [#5586](https://github.com/HKUDS/nanobot/issues/5586) — *Ephemeral runtime-context blocks* | Open since 2026-08-28, updated 2026-09-01, 1 comment | Advanced users need fine-grained control over what context persists across turns. This reflects a growing need for session hygiene in long-running or multi-turn workflows. PR #5627 is the corresponding fix. |
| [#5428 / #5623](https://github.com/HKUDS/nanobot/issues/5428) — *Empty active-task groups retained after session tasks finish* | Issue closed via PR #5430; PR #5623 also addresses cleanup | Long-running gateway instances accumulate orphaned dict entries. This is a stability concern for production deployments. |

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **P2 — Regression** | [#2061](https://github.com/HKUDS/nanobot/issues/2061) | File copy inside workspace never completes; agent loops on `list_dir`/`read_file` without executing a write or copy. | Fix in progress: [#5626](https://github.com/HKUDS/nanobot/pull/5626) adds native `copy_file`/`move_file` tools. |
| **P2 — Bug** | [#5621](https://github.com/HKUDS/nanobot/pull/5621) *(merged)* | TUI discards input typed after submit. | ✅ Merged. |
| **P2 — Bug** | [#5622](https://github.com/HKUDS/nanobot/pull/5622) *(merged)* | Dream prompt duplicates SOUL/USER/MEMORY, inflating context. | ✅ Merged. |
| **P2 — Bug** | [#5624](https://github.com/HKUDS/nanobot/pull/5624) *(open)* | Unpersisted WebUI panes cannot be deleted; also fails after gateway restart. | Open, awaiting review. |
| **P2 — Bug** | [#5603](https://github.com/HKUDS/nanobot/pull/5603) *(merged)* | Agent claims to perform actions without emitting tool calls (silent hallucination). | ✅ Merged; detection now in place. |
| **P2 — Bug** | [#5428 / #5623](https://github.com/HKUDS/nanobot/issues/5428) | Empty active-task groups leak in `AgentLoop._active_tasks`. | Partially fixed by #5430; #5623 provides additional cleanup. |

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Likelihood for Next Release |
|--------|--------|----------------------------|
| **Ephemeral runtime-context blocks** | #5586 / #5627 | **High** — PR is complete and directly addresses a user-requested gap in context lifecycle management. |
| **First-class `copy_file` / `move_file` tools** | #2061 / #5626 | **High** — Long-standing user need with a ready PR; removes a workaround-heavy workflow. |
| **Telegram rich-message streaming** | #5614 | **Medium** — PR is open and needs review; adds capability but may depend on Telegram channel integration priorities. |
| **First-run AI setup flow (WebUI)** | #5625 | **Medium** — Improves onboarding UX; replaces a harsh error state with a guided flow. |
| **Zalo integration refactor** | [#2078](https://github.com/HKUDS/nanobot/pull/2078) | **Low–Medium** — Follows modular plugin architecture; pending review. |

---

## 7. User Feedback Summary

- **File operations are a top pain point.** Issue #2061 (open for ~6 months) shows users are frustrated that nanobot can read and list files but cannot copy or move them natively. The workaround of chaining `read_file` → `write_file` is error-prone and incomplete.
- **Context persistence is too blunt.** Issue #5586 reflects advanced users' desire to control what context survives across turns — important for session hygiene in multi-day or multi-topic conversations.
- **TUI input handling has regressions.** The fixed input-loss-after-submit bug (#5621) suggests the terminal UI has been under active stress testing and refinement.
- **Silent hallucination is being addressed.** PR #5603 shows the team is taking user reports of "agent says it did X but didn't" seriously, adding detection logic to the transcript pipeline.
- **WebUI session management needs polish.** PR #5624 indicates ongoing friction around pane lifecycle, especially after gateway restarts — a signal that the WebUI is seeing heavier production use.

---

## 8. Backlog Watch

| Item | Age | Risk | Recommendation |
|------|-----|------|----------------|
| [#2061](https://github.com/HKUDS/nanobot/issues/2061) — Copy file inside workspace | ~6 months | **High** — Core workflow blocker for Feishu/workspace users. PR #5626 is ready but not yet merged. | Prioritize merge review for #5626. |
| [#2078](https://github.com/HKUDS/nanobot/pull/2078) — Zalo integration refactor | ~6 months | **Medium** — Blocked on review; follows new plugin architecture. | Assign reviewer; align with channel integration roadmap. |
| [#5624](https://github.com/HKUDS/nanobot/pull/5624) — Delete unpersisted WebUI panes | 1 day | **Medium** — Open, no comments yet. Impacts WebUI power users. | Request maintainer triage. |
| [#5614](https://github.com/HKUDS/nanobot/pull/5614) — Telegram rich-message streaming | 3 days | **Low–Medium** — Author notes they will review this week. | Follow up with author for review timeline. |

---

**Project Health Assessment:** 🟢 **Healthy** — High PR throughput, fast merge cycles on bugs, and clear alignment between open issues and in-progress PRs. The main concern is the longevity of #2061, which has been open since March without a merged fix.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-09-02

---

## 1. Today's Overview

Hermes Agent shows **very high activity** today, with 50 issues and 50 PRs updated in the last 24 hours — a strong signal of active development and community engagement. The project is in a rapid iteration phase, with 15 issues closed and 22 PRs merged, suggesting the team is actively clearing a backlog. No new releases were published today, but a cluster of P1 and P2 bug fixes landed, many targeting session-state reliability, desktop branching UX, and cross-platform compatibility. The project appears healthy but in a stabilization sprint, with significant focus on desktop session management and gateway reliability.

---

## 2. Releases

**No new releases today.** The latest version context from reported issues is **v0.21.0** (commit `18a76be124d7c16ed98b629a358b23fef76a7f46`) and **v0.20.6** for older reports.

---

## 3. Project Progress

### Closed/Merged PRs (Today)

| PR | Description | Link |
|----|-------------|------|
| #100879 | **fix(desktop):** branched session now loads on backend that owns its parent | [PR #100879](https://github.com/NousResearch/hermes-agent/pull/100879) |
| #70419 | **fix(desktop):** fall through to create when branch draft resume fails — fixes lost first message in new branches | [PR #70419](https://github.com/NousResearch/hermes-agent/pull/70419) |
| #97359 | **fix(desktop):** route project session branches by owner profile | [PR #97359](https://github.com/NousResearch/hermes-agent/pull/97359) |
| #97747 | **fix(desktop):** coalesce duplicate branch creates with single-flight guard | [PR #97747](https://github.com/NousResearch/hermes-agent/pull/97747) |
| #95992 | **fix(desktop):** navigate to branched session route after creation | [PR #95992](https://github.com/NousResearch/hermes-agent/pull/95992) |
| #94208 | **fix(gateway):** persist seeded branch children at `session.create` — fixes infinite spinner on branch | [PR #94208](https://github.com/NousResearch/hermes-agent/pull/94208) |
| #98551 | **fix(desktop):** route session branches through parent's owning connection | [PR #98551](https://github.com/NousResearch/hermes-agent/pull/98551) |
| #100316 | **fix(desktop):** honor active KDE icon theme in `_install_icon_to_hicolor()` | [PR #100316](https://github.com/NousResearch/hermes-agent/pull/100316) |
| #57921 | **fix(gateway):** resolve "database is locked" caused by dashboard sharing `hermes_state.py` under GIL pressure | [PR #57921](https://github.com/NousResearch/hermes-agent/pull/57921) |
| #93959 | **fix(desktop):** branch creation no longer hangs infinitely on existing sessions | [PR #93959](https://github.com/NousResearch/hermes-agent/pull/93959) |
| #99661 | **fix(agents):** background_review skill-nudge no longer floods pending queue — added session-end batching | [PR #99661](https://github.com/NousResearch/hermes-agent/pull/99661) |
| #99704 | **fix(cli):** `/skills approve` now handles multi-ID correctly; diff preview fixed for patch-type items | [PR #99704](https://github.com/NousResearch/hermes-agent/pull/99704) |
| #99729 | **fix(agents):** design resolution on skill_manage approval gate enforcement boundary | [PR #99729](https://github.com/NousResearch/hermes-agent/pull/99729) |
| #100436 | **fix(desktop):** intermittent "Couldn't open bot's chat" disk I/O error in read-only FTS probe | [PR #100436](https://github.com/NousResearch/hermes-agent/pull/100436) |
| #99832 | **fix(desktop):** suppress false-positive bundle-skew warnings on docs-only commits | [PR #99832](https://github.com/NousResearch/hermes-agent/pull/99832) |
| #99875 | **fix(plugins):** muse-spark-1.2-contributor 404 on `POST /v1/responses` via Hermes | [PR #99875](https://github.com/NousResearch/hermes-agent/pull/99875) |
| #99635 | **fix(security):** `delegate_task` subagents now inherit scrubbed env — process boundary added | [PR #99635](https://github.com/NousResearch/hermes-agent/pull/99635) |

**Key theme:** A major desktop session/branching subsystem was stabilized today with at least 7 interrelated PRs landing, addressing infinite spinners, duplicate sessions, and routing failures.

---

## 4. Community Hot Topics

| Issue/PR | Topic | Comments | Link |
|----------|-------|----------|------|
| #97681 | Bot Group Chats should survive Desktop closes | 19 | [Issue #97681](https://github.com/NousResearch/hermes-agent/issues/97681) |
| #97948 | Manual `/compress` timeout vs background worker success on large sessions | 13 | [Issue #97948](https://github.com/NousResearch/hermes-agent/issues/97948) |
| #62169 | Terminal sandbox CWD deletion breaks all subsequent commands (exit 126) | 7 | [Issue #62169](https://github.com/NousResearch/hermes-agent/issues/62169) |
| #57921 | `hermes_state.py` timeout causes "database is locked" with dashboard | 5 | [Issue #57921](https://github.com/NousResearch/hermes-agent/issues/57921) |
| #93959 | Branch creation hangs infinitely on existing sessions | 4 | [Issue #93959](https://github.com/NousResearch/hermes-agent/issues/93959) |
| #100858 | Auxiliary vision with `custom:<name>` provider sends wrong API key (401) | 4 | [Issue #100858](https://github.com/NousResearch/hermes-agent/issues/100858) |
| #39829 | Bedrock Converse rejects whitespace-only placeholder in history | 3 | [Issue #39829](https://github.com/NousResearch/hermes-agent/issues/39829) |
| #81427 | Memory provider tools not injected in desktop sessions | 3 | [Issue #81427](https://github.com/NousResearch/hermes-agent/issues/81427) |
| #100339 | Profile-cloned Anthropic OAuth strands sibling profiles after token rotation | 3 | [Issue #100339](https://github.com/NousResearch/hermes-agent/issues/100339) |

**Analysis:** The top-voted issue (#97681) reflects a core production use case — users running bots from heterogenous hardware (laptop, homelab, VPS) in group chats expect continuity when the Desktop app closes. The compression timeout issue (#97948) and terminal CWD bug (#62169) signal that long-running, large-session workflows on Windows are exposing state-management fragility. The Anthropic OAuth issue (#100339) is particularly significant for users running multi-profile agent teams.

---

## 5. Bugs & Stability

### P1 (High Severity)

| Issue | Description | Fix PR | Link |
|-------|-------------|--------|------|
| #100339 | Anthropic OAuth single-use refresh token strands sibling profiles after rotation; agent init hard-fails | — | [Issue #100339](https://github.com/NousResearch/hermes-agent/issues/100339) |
| #100689 | `async_delegation` wake self-post: 600s timeout + no per-session lock → duplicate/dropped turns | — | [Issue #100689](https://github.com/NousResearch/hermes-agent/issues/100689) |
| #100836 | `hermes doctor --fix` self-detects as live writer; leaked `COUNT(*)` connection never closed | — | [Issue #100836](https://github.com/NousResearch/hermes-agent/issues/100836) |
| #100752 (PR) | CI `e2e-desktop` job 0-jobbed since commit `24f5a60ed1` due to malformed `if: false` expression | [PR #100752](https://github.com/NousResearch/hermes-agent/pull/100752) | — |

### P2 (Medium Severity)

| Issue | Description | Fix PR | Link |
|-------|-------------|--------|------|
| #97948 | `/compress` 120s timeout while background worker succeeds; lease lost on large sessions | — | [Issue #97948](https://github.com/NousResearch/hermes-agent/issues/97948) |
| #100858 | `auxiliary.vision` with `custom:<name>` provider sends `no-key-required` key instead of API key (401) | — | [Issue #100858](https://github.com/NousResearch/hermes-agent/issues/100858) |
| #100835 | `auxiliary model: null` stringified to literal `"None"` model ID | — | [Issue #100835](https://github.com/NousResearch/hermes-agent/issues/100835) |
| #100600 | macOS DMG is stale bootstrap artifact; new users forced into full local install | [PR #100600](https://github.com/NousResearch/hermes-agent/pull/100600) | — |
| #96513 | Desktop branch takeover never updates URL; pane stuck on loader | [PR #100879](https://github.com/NousResearch/hermes-agent/pull/100879) (related) | [Issue #96513](https://github.com/NousResearch/hermes-agent/issues/96513) |
| #97414 | Desktop branch re-fires on failure; duplicate child sessions accumulate | [PR #97747](https://github.com/NousResearch/hermes-agent/pull/97747) | [Issue #97414](https://github.com/NousResearch/hermes-agent/issues/97414) |
| #100268 | `/proc/uptime` missing in Docker container post v0.21.0 | — | [Issue #100268](https://github.com/NousResearch/hermes-agent/issues/100268) |
| #100870 | Remote code kernel fails on Docker backend; brace-group rewriter omits separator after `}` | — | [Issue #100870](https://github.com/NousResearch/hermes-agent/issues/100870) |
| #96012 | Mid-session `/model` switch loses `reasoning_overrides`; GLM-5.3-Flash 400 | — | [Issue #96012](https://github.com/NousResearch/hermes-agent/issues/96012) |
| #100762 | Bare `/refine` silently dropped when `background_review.enabled=false` | [PR #100872](https://github.com/NousResearch/hermes-agent/pull/100872) | [Issue #100762](https://github.com/NousResearch/hermes-agent/issues/100762) |
| #98468 | Bedrock streaming reasoning_content shredded — `\n\n` inserted between every delta | [PR #100875](https://github.com/NousResearch/hermes-agent/pull/100875) | [Issue #98468](https://github.com/NousResearch/hermes-agent/issues/98468) |
| #100864 | Desktop Bots voice playback uses active profile's TTS instead of Bot's own config | — | [Issue #100864](https://github.com/NousResearch/hermes-agent/issues/100864) |
| #100561 | Nix package missing `hermes_state_registry` in installed modules | — | [Issue #100561](https://github.com/NousResearch/hermes-agent/issues/100561) |
| #81427 | Memory provider tools not injected in desktop sessions | — | [Issue #81427](https://github.com/NousResearch/hermes-agent/issues/81427) |
| #39829 | Bedrock Converse rejects whitespace-only placeholder; breaks assistant-first history resume | — | [Issue #39829](https://github.com/NousResearch/hermes-agent/issues/39829) |

### P3 (Lower Severity)

| Issue | Description | Link |
|-------|-------------|------|
| #100870 | Docker backend brace-group rewriter syntax error | [Issue #100870](https://github.com/NousResearch/hermes-agent/issues/100870) |
| #84721 | Inbound attachment support missing in Photon/iMessage | [Issue #84721](https://github.com/NousResearch/hermes-agent/issues/84721) |
| #100268 | `/proc/uptime` missing in container runtime | [Issue #100268](https://github.com/NousResearch/hermes-agent/issues/100268) |

**Stability Assessment:** The project is experiencing a **cluster of session-state and desktop UX regressions** around branching, compression, and multi-profile coordination. While many fixes landed today, P1 issues around OAuth token rotation (#100339) and async delegation concurrency (#100689) remain open and could affect production reliability for multi-profile users.

---

## 6. Feature Requests & Roadmap Signals

| PR/Issue | Description | Link |
|----------|-------------|------|
| #100877 | **Per-reply cost footer, spend warnings, `/new` handoff note** — surfaces cost data on messaging surfaces in real time | [PR #100877](https://github.com/NousResearch/hermes-agent/pull/100877) |
| #100764 | **Native audio/voice routing** for multimodal models — session-aware inbound voice note handling across gateway | [PR #100764](https://github.com/NousResearch/hermes-agent/pull/100764) |
| #100857 | **Pricing entry for `claude-opus-5`** — fills gap in usage cost tracking | [PR #100857](https://github.com/NousResearch/hermes-agent/pull/100857) |
| #100865 | **Orphan reaping for persistent browser daemons** — makes Browser Use CLI daemons visible to Hermes' reaper | [PR #100865](https://github.com/NousResearch/hermes-agent/pull/100865) |
| #97681 | **Bot group chat persistence across Desktop close** — foundational work on `main`; remaining work to connect to production | [Issue #97681](https://github.com/NousResearch/hermes-agent/issues/97681) |
| #92192 / #93632 | **Indonesian (Bahasa) documentation** — i18n locale seeded and root docs added | [PR #92192](https://github.com/NousResearch/hermes-agent/pull/92192), [PR #93632](https://github.com/NousResearch/hermes-agent/pull/93632) |

**Prediction:** The next release will likely include per-reply cost visibility (#100877), native audio routing (#100764), and the claude-opus-5 pricing entry (#100857) as user-facing improvements, alongside the desktop branching stability fixes.

---

## 7. User Feedback Summary

**Pain Points:**
- **Session branching in Desktop is unreliable** — multiple users reported infinite spinners, duplicate sessions, and lost messages when branching (#93959,

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-02

---

## 1. Today's Overview

PicoClaw shows moderate but focused activity today with 3 open issues and 4 pull requests updated in the last 24 hours. No new releases were published, indicating the team is concentrated on iterative fixes rather than version pushes. One PR (#3359) was merged/closed, while three remain open for review. The project maintains steady engagement on Telegram channel reliability and agent response threading — core UX concerns — while also addressing a notable MCP server hang bug and an edge-device feasibility proposal. Overall health appears stable with active contributor participation.

---

## 2. Releases

*No new releases today.*

---

## 3. Project Progress

**Merged / Closed Today:**

- **PR #3359** — *feat(repository-reviews): enforce product and retention contracts* (dkropachev) — Closes with an expansion of repository review infrastructure, introducing canonical product contracts, resource taxonomy, bounded API references, lifecycle/retention rules, and deterministic acceptance gates. This signals an investment in project governance and codebase reliability.

**Open PRs Awaiting Review (3):**

- **PR #3358** — *fix(agent): thread responses to the originating question message* (hugodeco) — Ensures agent replies carry `ReplyToMessageID`, restoring conversation context in group chats.
- **PR #3357** — *fix(telegram): treat replies to the bot's own messages as implicit mentions* (hugodeco) — Fixes a UX regression where replying to a bot message in `mention_only` groups was silently ignored.
- **PR #3356** — *fix(telegram): re-attach quoted documents when replying to a file message* (hugodeco) — Resolves a bug where quoted document media was dropped, leaving only a `[file]` placeholder for the agent.

*All three open PRs are by the same contributor (hugodeco) and target Telegram channel conversation continuity — a clear pattern of targeted stabilization.*

---

## 4. Community Hot Topics

| Item | Type | Author | Comments | Reactions | Link |
|------|------|--------|----------|-----------|------|
| #3269 | Issue (Bug) | ruiyigen | 8 | 1 👍 | [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269) |
| #3345 | Issue (Proposal) | kvnloo | 1 | 0 👍 | [Issue #3345](https://github.com/sipeed/picoclaw/issues/3345) |
| #3355 | Issue (Bug) | ttghub | 0 | 0 👍 | [Issue #3355](https://github.com/sipeed/picoclaw/issues/3355) |

**Analysis:**

- **#3269 (MCP server hang)** — The most discussed open issue (8 comments, stale-tagged). The core concern is a **dead loop / hang** when MCP server connections fail, which directly blocks the chat interface. This is a reliability-critical bug affecting the agent loop's resilience. The stale tag suggests it has been unanswered for some time despite community interest.
- **#3345 (Edge compute worker mode)** — A feature proposal to run lightweight PicoClaw on constrained devices (RISC-V boards, old Android phones, ~10–20 MB RAM). Reflects a growing community interest in **distributed, low-cost edge AI deployment** — users with multiple weak devices want to form a pooled agent network alongside a stronger PC.
- **#3355 (Feishu config error)** — A fresh, unresponsive issue about an unknown config field for Feishu (Lark) channel integration. Suggests either a breaking config change or incomplete documentation.

---

## 5. Bugs & Stability

| Rank | Item | Severity | Description | Fix Available? |
|------|------|----------|-------------|----------------|
| 1 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | **High** | MCP server connection failure causes agent loop to hang; chat interface stops responding entirely | No open fix PR yet |
| 2 | [#3355](https://github.com/sipeed/picoclaw/issues/3355) | **Medium** | Feishu channel config error — `channel_list.feishu.app_id` rejected as unknown field | No open fix PR yet |
| 3 | PR [#3358](https://github.com/sipeed/picoclaw/pull/3358) | **Medium** | Agent responses not threaded to originating message in group chats (Telegram) | In progress (PR #3358) |
| 4 | PR [#3357](https://github.com/sipeed/picoclaw/pull/3357) | **Medium** | Replies to bot's own messages ignored in `mention_only` Telegram groups | In progress (PR #3357) |
| 5 | PR [#3356](https://github.com/sipeed/picoclaw/pull/3356) | **Low** | Quoted document media dropped when replying to file messages in Telegram | In progress (PR #3356) |

*The most concerning item is #3269 — an unmitigated hang in the agent loop with no active fix PR, compounded by its stale status.*

---

## 6. Feature Requests & Roadmap Signals

- **Lightweight edge worker mode** (Issue [#3345](https://github.com/sipeed/picoclaw/issues/3345)) — User-driven proposal for deploying PicoClaw on resource-constrained devices (RISC-V, ARM, MIPS, old Android). This aligns with broader trends in distributed agent systems and low-code/edge AI. **Likelihood of inclusion:** moderate — fits the "low-cost hardware" niche but may require significant architectural changes.
- **Repository review infrastructure** (PR [#3359](https://github.com/sipeed/picoclaw/pull/3359) — now closed) — The merge of this PR signals a roadmap direction toward stronger code governance, product contracts, and automated acceptance gates. Expect more tooling around repository lifecycle management in future releases.

---

## 7. User Feedback Summary

**Pain Points:**
1. **Agent loop hangs on MCP failure** (#3269) — Users report the chat interface becoming completely unresponsive when the MCP server drops connection. This is a severe reliability issue that directly impacts daily usage.
2. **Feishu/Lark integration confusion** (#3355) — Config fields accepted in prior versions are now rejected, suggesting a breaking change without clear migration guidance.
3. **Telegram reply threading broken** (PRs #3358, #3357) — In group chats, bot answers appear disconnected from questions, and reply-based follow-ups are silently dropped in `mention_only` mode. These degrade UX in collaborative environments.
4. **Document quoting lost** (PR #3356) — Quoted file references are stripped to `[file]` placeholders, preventing agents from accessing attached media during replies.

**Use Cases Evident:**
- Multi-device distributed agent setups on low-cost hardware
- Telegram and Feishu as primary chat channels for agent interaction
- Group-chat bot behavior with threaded replies and media handling

**Satisfaction Signal:** Moderate. Active bug reporting and multiple fix PRs from a single contributor suggest a responsive but possibly understaffed maintainer base.

---

## 8. Backlog Watch

| Item | Type | Age | Concern |
|------|------|-----|---------|
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | Bug | ~44 days (stale) | **Critical** — Agent loop hang with no fix PR. Highest backlog priority. |
| [#3345](https://github.com/sipeed/picoclaw/issues/3345) | Proposal | ~8 days | Edge worker mode — no maintainer response yet. |
| [#3355](https://github.com/sipeed/picoclaw/issues/3355) | Bug | 1 day | Feishu config regression — new but unaddressed. |

**Recommendation:** Issue #3269 should be the immediate focus — a hanging agent loop is a severe reliability defect that affects core functionality, yet it carries the `stale` label with no active fix. Maintainer attention is needed to either assign a fix or close with a workaround.

---

*Digest generated from GitHub data as of 2026-09-02. Source: [github.com/sipeed/picoclaw](https://github.com/sipeed/picoclaw)*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-02

## 1. Today's Overview

NanoClaw shows moderate but focused development activity today, with **12 open PRs** and **2 open issues** under active review. The most significant event is the merge of **#3698** (Bun/Claude runtime bump), the only closed/merged PR in the last 24 hours. The project is in the midst of a large-scale provider-contract refactoring effort spanning six interlinked PRs, alongside several feature and fix PRs awaiting merge. No new releases were published. Overall, the project remains healthy with steady contributor engagement and a clear architecture-direction trend.

## 2. Releases

*No new releases published today.*

The previously merged PR [#3698](https://github.com/nanocoai/nanoclaw/pull/3698) bumped container runtimes (Bun 1.3.12→1.4.0, Claude Code 2.1.238→2.1.257, Claude Agent SDK 0.3.238→0.3.257) but did not accompany a new version tag.

## 3. Project Progress

**Merged today:**
- [#3698](https://github.com/nanocoai/nanoclaw/pull/3698) — **chore(container): bump Bun and Claude runtimes**. Updated the agent container's Bun from 1.3.12 to 1.4.0, Claude Code from 2.1.238 to 2.1.257, and Claude Agent SDK from 0.3.238 to 0.3.257. CI, registry-skill validation, and release verification now target Bun 1.4.0.

**PRs actively advancing:**
- A six-PR **provider-contract refactoring series** (#3581, #3584, #3585, #3586, #3588, #3591) by zvi-fried is progressing in parallel, implementing runtime, host, setup, codex, opencode, and provider-instructions contracts.
- [#3592](https://github.com/nanocoai/nanoclaw/pull/3592) introduces a **core-owned speed-inference property** for agent groups.
- [#3696](https://github.com/nanocoai/nanoclaw/pull/3696) adds **per-task missed-run policies** for recurring scheduled tasks.
- [#3697](https://github.com/nanocoai/nanoclaw/pull/3697) adds a new **Keenable MCP tool skill** for web search and page fetch.

## 4. Community Hot Topics

| Item | Type | Author | Engagement | Link |
|------|------|--------|-----------|------|
| #3700 | Issue | DawoudIO | 0 comments, 0 👍 | [Issue #3700](https://github.com/nanocoai/nanoclaw/issues/3700) |
| #3699 | Issue | DawoudIO | 0 comments, 0 👍 | [Issue #3699](https://github.com/nanocoai/nanoclaw/issues/3699) |
| #3427 | PR | glifocat | Open, 0 👍 | [PR #3427](https://github.com/nanocoai/nanoclaw/pull/3427) |
| #3680 | PR | prathish-ks | Open, 0 👍 | [PR #3680](https://github.com/nanocoai/nanoclaw/pull/3680) |

**Analysis:** The two open issues were created yesterday by a core contributor (DawoudIO) and address real operational pain points around destination lifecycle management and CLI ergonomics — both likely to see follow-up discussion as users hit them in production. The open PRs have not yet accumulated reactions, suggesting they are either recent or still in early review. The **provider-refactor series** (six PRs by zvi-fried) is the dominant thematic signal, reflecting a concerted effort to formalize provider contracts across the codebase — a structural change that will likely generate discussion as it lands.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| **High** | [#3700](https://github.com/nanocoai/nanoclaw/issues/3700) | Destination local-names fail to repoint when their target messaging-group is recreated, causing outbound sends to silently report success against a dead target | None yet |
| **High** | [#3680](https://github.com/nanocoai/nanoclaw/pull/3680) | Mount-security bypass: allowlisted-extra mount not closed in `validateSpec` | PR #3680 (open) |
| **Medium** | [#3427](https://github.com/nanocoai/nanoclaw/pull/3427) | `send_card` misleads agents by reporting success for callback actions silently dropped by the Chat SDK bridge | PR #3427 (open) |
| **Medium** | [#3646](https://github.com/nanocoai/nanoclaw/pull/3646) | Sweep idle timeout is hardcoded at 30 min and only ticks on provider stream events, causing slow local-model turns to be killed prematurely | PR #3646 (open) |

**Notes:** No crashes or regressions reported today. Issue #3700 is the most critical open bug — it affects data correctness in production deployments. Two fix PRs (#3680, #3427, #3646) are awaiting merge review.

## 6. Feature Requests & Roadmap Signals

| Item | Description | Signal Strength |
|------|-------------|----------------|
| [#3696](https://github.com/nanocoai/nanoclaw/pull/3696) | Per-task missed-run policy for recurring scheduled tasks (closes #2398) | **Strong** — PR is complete and awaiting merge |
| [#3697](https://github.com/nanocoai/nanoclaw/pull/3697) | Keenable MCP tool skill for web search and page fetch | **Moderate** — new skill contribution, may indicate partnership |
| [#3592](https://github.com/nanocoai/nanoclaw/pull/3592) | Core-owned speed-inference property for agent groups | **Strong** — addresses a known configuration gap |
| [#3581–#3591](https://github.com/nanocoai/nanoclaw/pull/3581) | Provider contract refactoring series (6 PRs) | **Strong** — major architectural initiative, likely to ship as a batch |

**Prediction:** The provider-contract refactoring and the missed-run scheduling policy are the most likely candidates for the next release. The Keenable skill may ship independently as a community contribution.

## 7. User Feedback Summary

- **Destination lifecycle frustration** (Issue #3700): Users are hitting real pain when messaging-groups are recreated — destination local-names become stale and sends silently fail. This suggests the CLI's group-scoped resource model needs better state reconciliation.
- **CLI inconsistency** (Issue #3699): The `ncl destinations create/remove` commands don't auto-fill `--agent-group-id` like other group-scoped commands do, creating an inconsistent developer experience.
- **Agent tool reliability** (PR #3427): Agents are being misled by `send_card` reporting success for actions the bridge drops — a trust/observability issue.
- **Local-model kills** (PR #3646): Users running slower local backends are experiencing premature task kills, indicating the sweep logic needs environment-aware timeouts.

Overall sentiment: users are engaged and reporting precise, actionable issues. No broad dissatisfaction signals, but several friction points in the CLI and agent-runtime boundary are emerging.

## 8. Backlog Watch

| Item | Type | Author | Age | Risk |
|------|------|--------|-----|------|
| [#3700](https://github.com/nanocoai/nanoclaw/issues/3700) | Bug | DawoudIO | 1 day | **High** — data-correctness bug in production |
| [#3699](https://github.com/nanocoai/nanoclaw/issues/3699) | Bug/UX | DawoudIO | 1 day | **Medium** — CLI inconsistency |
| [#3680](https://github.com/nanocoai/nanoclaw/pull/3680) | Security fix | prathish-ks | 3 days | **High** — mount bypass, unmerged |
| [#3427](https://github.com/nanocoai/nanoclaw/pull/3427) | Bug fix | glifocat | 12 days | **Medium** — long-open fix PR |
| [#3646](https://github.com/nanocoai/nanoclaw/pull/3646) | Bug fix | glifocat | 4 days | **Medium** — local-model users affected |

**Action items for maintainers:**
- Prioritize review of security fix [#3680](https://github.com/nanocoai/nanoclaw/pull/3680) and production bug [#3700](https://github.com/nanocoai/nanoclaw/issues/3700).
- PR [#3427](https://github.com/nanocoai/nanoclaw/pull/3427) has been open for 12 days — consider requesting a status update from glifocat or pulling it into the next merge window.
- The six-PR provider refactor series (#3581–#3591) should be reviewed as a coordinated batch to avoid partial merges that break contracts.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-02

## 1. Today's Overview

IronClaw shows strong daily velocity with **13 issues** and **19 pull requests** updated in the last 24 hours, indicating a healthy and active development cycle. No new releases were published today, suggesting the team is still iterating on the current cycle's changes. The project is in an active QA and dogfooding phase, with a new epic (#8026) launched for bug fixing through 2026-09-06. Activity is concentrated on WebUI component unification, agent-loop refactoring, and Slack/LLM reliability improvements.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Merged / Closed PRs Today

- **[PR #8031](https://github.com/nearai/ironclaw/pull/8031)** — `refactor(agent-loop): decompose capability stage mechanics` — Reduced `executor/capabilities.rs` from 2,938 to 890 lines by extracting batch scheduling, dispatch/recovery, failure normalization, outcome persistence, and record construction into focused submodules.
- **[PR #8028](https://github.com/nearai/ironclaw/pull/8028)** — `refactor(agent-loop): align state and stage ownership` — Split checkpoint state into compaction, recovery, reply-admission, and stop-control modules; moved model-usage bookkeeping into `ModelStage`.
- **[PR #8013](https://github.com/nearai/ironclaw/pull/8013)** — `ci: parallelize affected crate tests with nextest` — Switched affected-package tests to `nextest` with four parallel processes, significantly reducing CI feedback time.
- **[PR #8014](https://github.com/nearai/ironclaw/pull/8014)** — `fix(slack): preserve explicit mentions across callback dedup` — Fixed a bug where Slack threaded posts delivered as both `message` and `app_mention` callbacks caused mention loss during deduplication.
- **[PR #7996](https://github.com/nearai/ironclaw/pull/7996)** — `perf(github): compact repository list responses` — Projected `github.list_repos` onto model-useful fields instead of forwarding full GitHub REST objects, directly addressing the 519 KB bloat reported in issue #7986.
- **[PR #7997](https://github.com/nearai/ironclaw/pull/7997)** — `feat(webui): show model capability icons across Inference` — Added icon-only Text/Image input/output capability badges across all Inference model-selection surfaces with hover descriptions.
- **[PR #7984](https://github.com/nearai/ironclaw/pull/7984)** — `fix(tools): size tool_search replies to the first-look envelope` — Fixed a critical issue where `tool_search` replies (e.g., 16 KB serialized) were being truncated to ~857 B by the model envelope; now sized to the model's first-look budget.
- **[PR #8027](https://github.com/nearai/ironclaw/pull/8027)** — `fix(live-qa): find the Slack run by message identity, not envelope event_id` — Fixed a 33-run-canary failure where the test harness incorrectly matched Slack events, causing spurious timeout errors.
- **[PR #7971](https://github.com/nearai/ironclaw/issues/7971)** — Closed: WebUI model capability tags now rendered across Inference selectors.
- **[PR #7970](https://github.com/nearai/ironclaw/issues/7970)** — Closed: NEAR AI model modalities now preserved through model discovery.

### Key Themes
- **Agent-loop architecture** is undergoing major decomposition for maintainability (two large refactor PRs merged).
- **WebUI design-system unification** is advancing: shared `SearchField`, `InlineNotice`, `Input`, and `SelectMenu` components are being adopted across Workspace, Logs, Automations, and Extension Configure views (4 PRs open: #8024, #8022, #8023, #8021).
- **Slack integration reliability** saw targeted bug fixes for mention preservation and event deduplication.

---

## 4. Community Hot Topics

| Item | Type | Activity |
|------|------|----------|
| [#8025](https://github.com/nearai/ironclaw/issues/8025) — Special characters in input cause output errors | Issue | Created 2026-09-01, 1 comment. Likely regression from encoding changes. |
| [#7921](https://github.com/nearai/ironclaw/issues/7921) — OpenAI prompt cache miss (~82%→29% hit rate) | Issue | Open since 2026-08-27, high-impact performance issue affecting all OpenAI-family backends. |
| [#7986](https://github.com/nearai/ironclaw/issues/7986) — `github.list_repos` ships 81 raw fields / 519 KB | Issue | Closed via [PR #7996](https://github.com/nearai/ironclaw/pull/7996). |
| [#8026](https://github.com/nearai/ironclaw/issues/8026) — Epic: Dogfooding & QA 08/31–09/06 | Issue | New epic tracking the current QA sprint. |
| [#8016](https://github.com/nearai/ironclaw/issues/8016) — Intermittent CI timeout in `reborn_turn_state_lock_free` test | Issue | Open, blocks CI reliability. |
| [#8015](https://github.com/nearai/ironclaw/issues/8015) — Rootless Docker sandbox workspace not writable (UID/GID mismatch) | Issue | Open, blocks rootless deployment for non-root users. |

**Underlying needs:** Users and maintainers are prioritizing **encoding robustness**, **cost/performance optimization** (prompt caching, response sizing), and **deployment reliability** (rootless Docker, CI flakiness). The GitHub API bloat fix and tool_search envelope fix both reflect a community demand for token-efficient tool responses.

---

## 5. Bugs & Stability

### Reported Today (Ranked by Severity)

1. **🔴 [Issue #8025](https://github.com/nearai/ironclaw/issues/8025)** — *Special character handling regression* — Special characters in input cause incorrect output (stripping or errors). Likely tied to recent encoding changes. **No fix PR yet.**
2. **🔴 [Issue #8015](https://github.com/nearai/ironclaw/issues/8015)** — *Rootless Docker sandbox unwritable* — UID/GID namespace mismatch prevents non-root users from writing to persistent workspace. Blocks a key deployment scenario. **No fix PR yet.**
3. **🟡 [Issue #8016](https://github.com/nearai/ironclaw/issues/8016)** — *CI intermittent timeout* — `reborn_turn_state_lock_free_submit_parity` test exceeds 5s budget sporadically. Undermines CI confidence. **No fix PR yet.**
4. **🟡 [Issue #7921](https://github.com/nearai/ironclaw/issues/7921)** — *OpenAI prompt cache collapse* — Prompt cache hits drop from ~82% to ~29% past ~200 calls due to missing `prompt_cache_key`. Affects all OpenAI-family backends. **No fix PR yet.**
5. **🟢 [PR #8029](https://github.com/nearai/ironclaw/pull/8029)** — *Slack admission bug* — Follow-up fix for Slack run admission logic (still open, awaiting review).

### Fixed Today
- `github.list_repos` payload bloat → [PR #7996](https://github.com/nearai/ironclaw/pull/7996)
- `tool_search` reply envelope truncation → [PR #7984](https://github.com/nearai/ironclaw/pull/7984)
- Slack mention loss during dedup → [PR #8014](https://github.com/nearai/ironclaw/pull/8014)
- Slack canary false timeout → [PR #8027](https://github.com/nearai/ironclaw/pull/8027)

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Projection |
|--------|--------|------------|
| **Unified WebUI design system** — `SearchField`, `InlineNotice`, `Input`, `SelectMenu` adoption across all panels | [Issue #8020](https://github.com/nearai/ironclaw/issues/8020), [#8019](https://github.com/nearai/ironclaw/issues/8019), [#8018](https://github.com/nearai/ironclaw/issues/8018), [#8017](https://github.com/nearai/ironclaw/issues/8017) + 4 linked PRs | Likely to land in the next release; already 4 PRs in progress |
| **Model capability visualization** — Icons for text/image input/output on Inference selectors | [PR #7997](https://github.com/nearai/ironclaw/pull/7997) (merged) | Already shipped; sets precedent for richer model metadata display |
| **Durable progressive replies & native Slack Agent UI** | [PR #8006](https://github.com/nearai/ironclaw/pull/8006) (open) | Major feature; provider-neutral `ReplyDocument` seam with Slack-specific presentation |
| **Unified session-event transport for WebUI** | [PR #8010](https://github.com/nearai/ironclaw/pull/8010) (open) | WebSocket multiplexing + run-completion notifications; follows approved design doc |
| **NEAR AI model modality preservation** | [PR #7998](https://github.com/nearai/ironclaw/pull/7998) (merged) | New `list_model_catalog()` discovery API alongside legacy `list_models()` |

**Prediction:** The next release will likely emphasize the **WebUI component unification** and **Slack progressive replies** as headline features, with the agent-loop refactor as a behind-the-scenes stability improvement.

---

## 7. User Feedback Summary

- **Encoding sensitivity:** Users are hitting regressions with special characters in input ([#8025](https://github.com/nearai/ironclaw/issues/8025)), suggesting that recent encoding changes need careful regression testing.
- **Token efficiency matters:** The community actively reported and celebrated the fix for GitHub repo listing bloat ([#7986](https://github.com/nearai/ironclaw/issues/7986) → [#7996](https://github.com/nearai/ironclaw/pull/7996)) and tool search envelope sizing ([#7984](https://github.com/nearai/ironclaw/pull/7984)). Users are cost-conscious and sensitive to unnecessary token consumption.
- **Rootless Docker deployment:** Non-root users cannot use the persistent sandbox workspace due to UID/GID mismatch ([#8015](https://github.com/nearai/ironclaw/issues/8015)), a real blocker for security-conscious deployments.
- **Slack integration reliability:** Multiple Slack-related bugs ([#8014](https://github.com/nearai/ironclaw/pull/8014), [#8027](https://github.com/nearai/ironclaw/pull/8027), [#8029](https://github.com/nearai/ironclaw/pull/8029)) indicate the Slack channel is a high-traffic area with complex edge cases around callback deduplication and event matching.
- **Prompt caching cost:** The OpenAI cache hit collapse ([#7921](https://github.com/nearai/ironclaw/issues/7921)) is a significant cost concern for power users running many turns.

---

## 8. Backlog Watch

| Issue / PR | Age | Concern |
|------------|-----|---------|
| [#7921](https://github.com/nearai/ironclaw/issues/7921) — OpenAI prompt cache key missing | ~6 days open, 0 comments | High-impact performance bug affecting all OpenAI-family backends. No fix PR yet. |
| [#8025](https://github.com/nearai/ironclaw/issues/8025) — Special character handling regression | 1 day open, 1 comment | Likely encoding regression; needs triage before next release. |
| [#8015](https://github.com/nearai/ironclaw/issues/8015) — Rootless Docker sandbox UID/GID mismatch | 1 day open, 0 comments | Blocks rootless deployment; needs maintainer investigation. |
| [#8016](https://github.com/nearai/ironclaw/issues/8016) — CI flaky timeout in turn-state test | 1 day open, 0 comments | Undermines CI reliability; needs reproducer or fix. |
| [#8006](https://github.com/nearai/ironclaw/pull/8006) — Slack progressive replies & native UI | ~2 days open | Large XL PR; needs review bandwidth. |
| [#8010](https://github.com/nearai/ironclaw/pull/8010) — WebUI session-event transport unification | ~2 days open | Large XL PR; design-approved but needs review. |

**Overall health assessment:** IronClaw is in a high-velocity refinement phase. The agent-loop refactor and WebUI unification are structurally important improvements. The main risks are the **OpenAI prompt cache regression** (#7921), the **special-character encoding bug** (#8025), and the **rootless Docker issue** (#8015) — all three are open with no fix PRs yet and should be prioritized before the next release cycle.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-09-02

## 1. Today's Overview

LobsterAI showed moderate activity on 2026-09-02 with **12 issues** and **9 PRs** updated in the last 24 hours. No new releases were published. The project's active development is concentrated on onboarding UX polish, analytics instrumentation, and Windows build fixes, while a cluster of older stale issues remains unresolved. Overall project health is stable: maintenance and incremental feature work are proceeding, but the high volume of stale, unanswered issues signals a growing backlog that may warrant maintainer attention.

---

## 2. Releases

**No new releases** were published on this date.

---

## 3. Project Progress

### Merged / Closed PRs (2026-09-01 to 2026-09-02)

| PR | Author | Summary |
|----|--------|---------|
| [#2596](https://github.com/netease-youdao/LobsterAI/pull/2596) | liuzhq1986 | **Analytics:** Track chat login CTA clicks; update usage analytics spec |
| [#2595](https://github.com/netease-youdao/LobsterAI/pull/2595) | fisherdaddy | **Windows (NSIS):** Fix staging drive preflight check for Windows installer |
| [#2594](https://github.com/netease-youdao/LobsterAI/pull/2594) | liuzhq1986 | **Onboarding:** Polish guide transitions — smaller cursor, faster popover, smoother entrance animation, reuses login CTA rainbow style, fixes one-frame layout flash |
| [#2593](https://github.com/netease-youdao/LobsterAI/pull/2593) | liugang519 | **Artifacts:** Add model-generated video sharing — preserves task ID & output序 traceability, enforces source validation (no local video bypass), adds URL hash parsing for legacy sessions, reuses share permissions & state management |
| [#2592](https://github.com/netease-youdao/LobsterAI/pull/2592) | liuzhq1986 | **User Guide:** Fixes to user documentation |
| [#2591](https://github.com/netease-youdao/LobsterAI/pull/2591) | liuzhq1986 | **Onboarding Analytics:** First-run funnel tracking — login handoff, welcome task creation, welcome stream lifecycle; structured-state fields only (no prompt text upload) |

**Key themes:** Strong focus on **onboarding experience refinement** and **analytics instrumentation**, plus a meaningful **video-sharing feature** for generated artifacts.

---

## 4. Community Hot Topics

### Most Discussed / Long-Running Issues

| Issue | Author | Status | Comments | Link |
|-------|--------|--------|----------|------|
| [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) — Add hermes-agent as optional AI engine | shanxinstart-lab | Closed (stale) | 3 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1614) |
| [#1622](https://github.com/netease-youdao/LobsterAI/issues/1622) — Cannot add custom model | soitun | Closed (stale) | 3 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1622) |
| [#1627](https://github.com/netease-youdao/LobsterAI/issues/1627) — Client crashes on slightly complex tasks | godlike10 | Closed (stale) | 3 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1627) |
| [#1632](https://github.com/netease-youdao/LobsterAI/issues/1632) — Skills broken after switching to local model | wwtghx | Closed (stale) | 3 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1632) |
| [#1586](https://github.com/netease-youdao/LobsterAI/issues/1586) — Incomplete i18n after language switch | QinGang746 | Closed (stale) | 2 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1586) |
| [#1617](https://github.com/netease-youdao/LobsterAI/issues/1617) — Deleted skills remain visible in list | STUPIDDDD0 | Closed (stale) | 2 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1617) |
| [#1105](https://github.com/netease-youdao/LobsterAI/issues/1105) — DingTalk scheduled task IM notification routing failure | MaoQianTu | **Open** | 1 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1105) |
| [#1107](https://github.com/netease-youdao/LobsterAI/issues/1107) — pollOnce() no re-entrancy guard; ghost events after stopPolling | MaoQianTu | **Open** | 1 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1107) |

**Analysis:** The top issues reflect three recurring user needs: (1) **extensibility** — users want more AI engine options and reliable custom-model support; (2) **stability** — crashes and UI state desynchronization on complex tasks or after configuration changes; (3) **localization quality** — i18n coverage gaps. The two open issues by MaoQianTu relate to core scheduled-task reliability and have corresponding PRs (#1106, #1108) awaiting merge.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR | Link |
|----------|-------|-------------|--------|------|
| 🔴 High | [#1627](https://github.com/netease-youdao/LobsterAI/issues/1627) | Client crash on moderately complex tasks | — (closed stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1627) |
| 🔴 High | [#1587](https://github.com/netease-youdao/LobsterAI/issues/1587) | First-launch crash after update (macOS) | — (closed stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1587) |
| 🟠 Medium | [#1589](https://github.com/netease-youdao/LobsterAI/issues/1589) | Sessions & scheduled tasks unable to execute (macOS) | — (closed stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1589) |
| 🟠 Medium | [#1617](https://github.com/netease-youdao/LobsterAI/issues/1617) | Skill list not refreshed after deletion; persists across restarts | — (closed stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1617) |
| 🟠 Medium | [#1107](https://github.com/netease-youdao/LobsterAI/issues/1107) | `pollOnce()` race condition — duplicate IPC events & ghost events post-stop | [#1108](https://github.com/netease-youdao/LobsterAI/pull/1108) (open) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1107) |
| 🟠 Medium | [#1105](https://github.com/netease-youdao/LobsterAI/issues/1105) | DingTalk IM notification routing broken due to unstripped `direct:`/`group:` prefix | [#1106](https://github.com/netease-youdao/LobsterAI/pull/1106) (open) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1105) |
| 🟡 Low | [#1112](https://github.com/netease-youdao/LobsterAI/issues/1112) | Table component has unexplained top/bottom whitespace | — (open, stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1112) |
| 🟡 Low | [#1586](https://github.com/netease-youdao/LobsterAI/issues/1586) | Incomplete i18n after language switch (Terms, Tool Style remain in Chinese) | — (closed stale) | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1586) |

**Note:** Multiple high-visibility bugs (#1627, #1587, #1589) were closed as **stale** without a merged fix, which is a concern for user trust. Two medium-severity bugs have open PRs that remain unmerged.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Near-Term Roadmap |
|---------|--------|----------------------------------|
| **Hermes-agent as optional AI engine** | [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) | Medium — aligns with extensibility direction; no active PR |
| **System notifications on scheduled task completion** | [#1620](https://github.com/netease-youdao/LobsterAI/issues/1620) | High — well-specified feature with clear UX value; no active PR yet |
| **Model-generated video sharing** | [#2593](https://github.com/netease-youdao/LobsterAI/pull/2593) | ✅ Already merged — signals artifacts/sharing as a roadmap priority |
| **First-run onboarding analytics** | [#2591](https://github.com/netease-youdao/LobsterAI/pull/2591) | ✅ Already merged — indicates investment in user-funnel instrumentation |
| **Custom model support reliability** | [#1622](https://github.com/netease-youdao/LobsterAI/issues/1622) | Medium — user pain point but closed stale; likely to resurface |
| **Skill persistence after deletion** | [#1632](https://github.com/netease-youdao/LobsterAI/issues/1632) | Low-Medium — edge case but affects power users |

**Prediction:** Expect continued investment in **onboarding UX**, **analytics**, and **artifact sharing** (video → potentially images/documents). Scheduled-task notifications (#1620) are a strong candidate for the next feature release.

---

## 7. User Feedback Summary

**Pain Points:**
- **Stability on complex workloads:** Users report client crashes and session/scheduled-task failures, particularly on macOS (#1627, #1589). These are high-impact but were closed stale.
- **UI state desynchronization:** Skill deletion not reflected in the UI, persisting across restarts (#1617) — indicates a frontend state management gap.
- **Custom model & engine extensibility:** Adding custom models fails out-of-the-box (#1622), and users desire more engine options like hermes-agent (#1614).
- **i18n coverage gaps:** Language switching leaves UI elements in the original language (#1586).
- **First-launch crashes after updates** (#1587) erode confidence in the release process.

**Satisfaction Signals:**
- Positive reception of onboarding polish and analytics improvements (merged PRs #2591, #2594, #2596).
- Video sharing feature (#2593) addresses a clear content-creation workflow need.
- Users actively engage with detailed bug reports including logs and screenshots, indicating an invested community.

---

## 8. Backlog Watch

The following **open issues/PRs** have been stagnant for months and require maintainer action:

| Item | Age | Description | Link |
|------|-----|-------------|------|
| [#1105](https://github.com/netease-youdao/LobsterAI/issues/1105) + [#1106](https://github.com/netease-youdao/LobsterAI/pull/1106) | ~5 months | DingTalk IM notification routing bug; fix PR ready but unmerged | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1105) · [PR](https://github.com/netease-youdao/LobsterAI/pull/1106) |
| [#1107](https://github.com/netease-youdao/LobsterAI/issues/1107) + [#1108](https://github.com/netease-youdao/LobsterAI/pull/1108) | ~5 months | `pollOnce()` re-entrancy & ghost events; fix PR ready but unmerged | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1107) · [PR](https://github.com/netease-youdao/LobsterAI/pull/1108) |
| [#1112](https://github.com/netease-youdao/LobsterAI/issues/1112) | ~5 months | Table component whitespace bug; no PR | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1112) |
| [#1620](https://github.com/netease-youdao/LobsterAI/issues/1620) | ~5 months | Scheduled task system notification feature request; no PR | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1620) |
| [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) | ~5 months | Hermes-agent engine integration request; no PR | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1614) |

**Recommendation:** The two PRs (#1106, #1108) address core reliability bugs in the scheduled-task subsystem and have been awaiting review for ~5 months. Prioritizing their merge would resolve significant user-facing issues with minimal risk.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-02

## 1. Today's Overview

Moltis saw moderate activity on 2026-09-02, with **2 issues closed** and **4 PRs updated** in the past 24 hours (2 open, 2 merged). No new releases were published. The project is actively addressing bugs in its authentication and MCP doctor-validation paths, while also advancing reasoning-effort configuration and Docker deployment documentation. Overall project health is **stable**, with a clear pattern of community contributors closing gaps in deployment correctness and tooling validation.

- [moltis-org/moltis](https://github.com/moltis-org/moltis)

## 2. Releases

No new releases were published during this period. The most recent referenced version is `20260827.01`.

---

## 3. Project Progress

**Merged / Closed PRs:**

- **#1251** — `Fix doctor validation for streamable HTTP MCP servers` ([penso](https://github.com/moltis-org/moltis/pull/1251))  
  Introduces a shared typed MCP transport definition recognizing `streamable-http` and aliases. Validates resolved remote server URLs before reporting doctor success, and defers unresolved credential-store placeholders informatively instead of flagging them as errors. Directly addresses [#1250](https://github.com/moltis-org/moltis/issues/1250).

- **#1249** — `fix(auth): let Docker loopback-only deployments count as local` ([Saraswat123](https://github.com/moltis-org/moltis/pull/1249))  
  Closes [#1112](https://github.com/moltis-org/moltis/issues/1112). Fixes `is_local_connection()` to correctly treat Docker bridge-network deployments as local, restoring Tier 2 convenience features (including `auth_disabled`) for Docker users.

**Open PRs:**

- **#1253** — `feat(reasoning): add max effort level` ([GTanger](https://github.com/moltis-org/moltis/pull/1253))  
  Adds `max` to the `ReasoningEffort` schema and `@reasoning-max` model suffix parsing. Forwards the setting through the OpenAI Codex Responses API and exposes it in the reasoning selector and translations.

- **#1252** — `docs(docker): document the bind-mount permission fix for fresh deploys` ([Saraswat123](https://github.com/moltis-org/moltis/pull/1252))  
  Documents the workaround for [#293](https://github.com/moltis-org/moltis/issues/293), where `docker compose up` panics on fresh checkouts due to SQLite permission issues with bind-mounted volumes.

---

## 4. Community Hot Topics

| Item | Type | Activity |
|------|------|----------|
| [#1112](https://github.com/moltis-org/moltis/issues/1112) — Disabling auth in Docker | Bug | 1 comment, closed |
| [#1250](https://github.com/moltis-org/moltis/issues/1250) — Doctor misreports streamable-http MCP servers | Bug | 0 comments, closed |
| [#1253](https://github.com/moltis-org/moltis/pull/1253) — Add max reasoning effort level | Feature | Open |
| [#1252](https://github.com/moltis-org/moltis/pull/1252) — Docker bind-mount docs | Docs | Open |

**Analysis:** The two closed issues highlight a recurring theme: **Docker deployment friction**. Users expect local-dev convenience (auth disabled, valid MCP detection) but hit edge cases around network topology and bind-mount permissions. The open PR for `max` reasoning effort suggests growing demand for fine-grained control over model reasoning intensity, likely driven by power users running expensive or multi-step workflows.

---

## 5. Bugs & Stability

| Severity | Issue | Status | Fix PR |
|----------|-------|--------|--------|
| **High** | [#1112](https://github.com/moltis-org/moltis/issues/1112) — Auth disable ineffective in Docker | ✅ Closed | [#1249](https://github.com/moltis-org/moltis/pull/1249) merged |
| **Medium** | [#1250](https://github.com/moltis-org/moltis/issues/1250) — Doctor falsely reports working streamable-http MCP as missing | ✅ Closed | [#1251](https://github.com/moltis-org/moltis/pull/1251) merged |
| **Low** | [#293](https://github.com/moltis-org/moltis/issues/293) — Fresh deploy SQLite permission panic in Docker | 📄 Docs | [#1252](https://github.com/moltis-org/moltis/pull/1252) (docs only, not a code fix) |

Both confirmed bugs were resolved the same day they were highlighted, indicating responsive maintenance. No regressions or crash reports are active.

---

## 6. Feature Requests & Roadmap Signals

- **[#1253](https://github.com/moltis-org/moltis/pull/1253) — Max reasoning effort level**  
  The strongest roadmap signal in this cycle. Adding `@reasoning-max` as a model suffix and exposing it in the UI selector indicates Moltis is deepening its integration with reasoning-capable models (e.g., OpenAI Codex). If merged, this will likely ship in the next patch or minor release alongside the other reasoning-effort tiers (`low`, `medium`).

No other explicit feature requests were raised in the 24-hour window.

---

## 7. User Feedback Summary

- **Docker usability remains a pain point.** Two of three closed items this cycle relate to Docker-specific behavior: auth not disabling correctly due to bridge-network IP rewriting, and SQLite permission errors on fresh bind-mount deploys. Users are clearly running Moltis in containers and expect first-class Docker support, but the experience still has rough edges.
- **MCP tooling validation is maturing.** The streamable-http MCP bug shows users are configuring advanced transport types and relying on `moltis doctor` for correctness guarantees. The fix (accepting aliases, deferring unresolved credentials) suggests the project is broadening its MCP compatibility.
- **No overt satisfaction complaints** were raised; all reported issues were technical misconfigurations or gaps rather than dissatisfaction with core functionality.

---

## 8. Backlog Watch

| Item | Days Since Updated | Risk |
|------|-------------------|------|
| [#293](https://github.com/moltis-org/moltis/issues/293) — SQLite bind-mount permission panic on fresh Docker deploy | Open since before 2026-09-01; only documented, not code-fixed | **Medium** — workaround exists, but the underlying issue persists for users who can't adjust permissions |
| [#1252](https://github.com/moltis-org/moltis/pull/1252) — Docker docs PR | Open since 2026-09-01 | **Low** — documentation-only, low risk if stalled |

The most notable backlog item is **#293**: while a docs PR (#1252) provides a workaround, the root cause (SQLite unable to open `moltis.db` on fresh bind-mounted volumes under Docker) remains unaddressed in code. Maintainers should consider whether a permanent fix—e.g., auto-initializing the database with correct ownership—is warranted in an upcoming release.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# 📊 QwenPaw (CoPaw) Project Digest — 2026-09-02

---

## 1. Today's Overview

QwenPaw continues active development on the v2.2.0 beta track, with **30 issues** and **40 PRs** updated in the last 24 hours — a robust cadence indicating a healthy open-source contributor base. The latest release, **v2.2.0-beta.6**, shipped with critical ReMe plugin bundling fixes and a major console test expansion (+617 test cases). Cron job scheduling bugs and multi-agent state visibility remain the top user concerns, while stability work on MCP, memory indexing, and local model loading is well underway. Overall project health is **strong**, with a good balance of bug fixes, tests, and feature work.

---

## 2. Releases

### v2.2.0-beta.6 (2026-09-02)

**What's Changed:**
- `[fix(desktop)]` Bundle ReMe entry-point plugins — fixes silent ReMe failures on fresh installs [[PR #7458](https://github.com/agentscope-ai/QwenPaw/pull/7458)]
- `[test(console)]` Expand console unit tests by +617 cases, raising statement coverage by +10.61pp [[PR #7452](https://github.com/agentscope-ai/QwenPaw/pull/7452)]
- `[test(inte)]` Integration coverage sprint batch 6: +314 cases across channels, CLI, mail, hub, renderer, and harness adapter [[PR #7451](https://github.com/agentscope-ai/QwenPaw/pull/7451)]

**Migration Notes:**
- PR #7468 ensures ReMe initializes before model configuration is required, resolving failures on fresh desktop installations.
- PR #7472 patches a Tool Guard bypass via POSIX shell line-continuation — users should update immediately if running agent tool-guard policies.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Summary | Type |
|---|---|---|
| [#7458](https://github.com/agentscope-ai/QwenPaw/pull/7458) | Bundle ReMe entry-point plugins in desktop build | Fix |
| [#7452](https://github.com/agentscope-ai/QwenPaw/pull/7452) | Console unit test expansion (+617 cases) | Test |
| [#7465](https://github.com/agentscope-ai/QwenPaw/pull/7465) | Normalize backend-specific embedding dimensions for DashScope | Fix |
| [#7468](https://github.com/agentscope-ai/QwenPaw/pull/7468) | Start ReMe before model configuration — fixes fresh-install crash | Fix |
| [#7472](https://github.com/agentscope-ai/QwenPaw/pull/7472) | Prevent shell line-continuation bypasses in Tool Guard | Security Fix |
| [#7329](https://github.com/agentscope-ai/QwenPaw/pull/7329) | Abort hung MCP session RPCs on teardown; recover stale `list_tools` | Fix |
| [#7330](https://github.com/agentscope-ai/QwenPaw/pull/7330) | Add Streamable-HTTP dual-protocol MCP client with legacy fallback | Feature |
| [#7432](https://github.com/agentscope-ai/QwenPaw/pull/7432) | Expand `~` in agent workspace dirs for LLM/tool trend aggregation | Fix |
| [#7404](https://github.com/agentscope-ai/QwenPaw/pull/7404) | Surface `card_auto_layout` in Console DingTalk channel settings | Enhancement |
| [#7428](https://github.com/agentscope-ai/QwenPaw/pull/7428) | Avoid bundling optional GPL Pylint provider in runtime | Maintenance |
| [#7341](https://github.com/agentscope-ai/QwenPaw/pull/7341) | Integration coverage sprint batch 5 — 495 cases | Test |
| [#7260](https://github.com/agentscope-ai/QwenPaw/pull/7260) | Targeted coverage: workspace tree, MCP policy, plugin SDK (22 cases) | Test |
| [#7246](https://github.com/agentscope-ai/QwenPaw/pull/7246) | +39 router/module integration test files; hardened flaky cases | Test |
| [#7463](https://github.com/agentscope-ai/QwenPaw/pull/7463) | Closed as duplicate of #7459 (Spark-X2.5 GGUF) | — |

**Key Advances:**
- **MCP hardening**: Dual-protocol client (#7330) and hung-RPC abort (#7329) significantly improve MCP reliability.
- **Test coverage sprint** continues aggressively — three batches merged in a single week totaling **~1,400+ new test cases**.
- **Security**: Tool Guard bypass patched in #7472.

---

## 4. Community Hot Topics

| Issue | Comments | Description | Link |
|---|---|---|---|
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | 6 | Multi-agent task: sub-agent status only visible when user explicitly asks | 🔗 |
| [#7480](https://github.com/agentscope-ai/QwenPaw/issues/7480) | 2 | Cron duplicate firing after backend restart; inbox notification bugs | 🔗 |
| [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | 2 | Cron tasks duplicated within `misfire_grace` window | 🔗 |
| [#7483](https://github.com/agentscope-ai/QwenPaw/issues/7483) | 2 | `share_session=true` cron re-loads session context each run; stuck "running" state | 🔗 |
| [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | 2 | Codex provider returns empty responses via non-streaming third-party gateway | 🔗 |

**Analysis:**
- **Cron reliability** is the dominant pain point — three distinct but related issues filed in 48 hours. Users depend on cron for scheduled automation and duplicates or stuck states are unacceptable.
- **Multi-agent observability** (#7450) reflects a growing adoption pattern: power users are running complex multi-agent workflows and need transparent, proactive status reporting — not reactive queries.
- **Third-party gateway compatibility** (#7431) highlights a fragile integration surface when providers deviate from expected streaming behavior.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR | Link |
|---|---|---|---|---|
| 🔴 **High** | [#7481](https://github.com/agentscope-ai/QwenPaw/issues/7481) | macOS StdIO MCP spawn re-enters `backend_guard`, killing active backend | — | 🔗 |
| 🔴 **High** | [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | Dangerous instructions can evade safety filters | — | 🔗 |
| 🟠 **Medium** | [#7470](https://github.com/agentscope-ai/QwenPaw/issues/7470) | MCP per-tool whitelist not enforced on agent runtime path | — | 🔗 |
| 🟠 **Medium** | [#7464](https://github.com/agentscope-ai/QwenPaw/issues/7464) | Embedding index rebuild config persistently reports "unsaved" | — | 🔗 |
| 🟠 **Medium** | [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe background embedding fails — `as_embedding:default` accessed before `start()` | [#7468](https://github.com/agentscope-ai/QwenPaw/pull/7468) ✅ merged | 🔗 |
| 🟠 **Medium** | [#7446](https://github.com/agentscope-ai/QwenPaw/issues/7446) | Embedding index rebuild 500 error — `ReMe instance is None` | Related: #7468 | 🔗 |
| 🟡 **Low** | [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | Custom provider fails to load after `max_tokens` → `max_output_length` migration | — | 🔗 |
| 🟡 **Low** | [#7459](https://github.com/agentscope-ai/QwenPaw/issues/7459) | Bundled llama.cpp cannot load Spark-X2.5 GGUF (`spark2_5` unknown architecture) | — | 🔗 |
| 🟡 **Low** | [#7479](https://github.com/agentscope-ai/QwenPaw/issues/7479) | Misspelled commands forwarded to agent instead of being rejected | — | 🔗 |
| 🟡 **Low** | [#7467](https://github.com/agentscope-ai/QwenPaw/issues/7467) | `loop.rubric` forced confirmation + console auto-fold hides first response | — | 🔗 |
| 🟡 **Low** | [#7471](https://github.com/agentscope-ai/QwenPaw/issues/7471) | MCP clients page renders white background in dark mode | [#7473](https://github.com/agentscope-ai/QwenPaw/pull/7473) ✅ open | 🔗 |

**Notable:** The macOS StdIO MCP crash (#7481) and the whitelist bypass (#7470) are the most consequential unresolved bugs — both affect core agent execution paths. The ReMe indexing issues (#7469, #7446) are partially mitigated by the merged #7468, though #7464 (config persistence) remains open.

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Description | Likelihood |
|---|---|---|
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | A2A protocol support (currently only MCP is implemented in 2.x) | ⭐⭐ Medium-term |
| [#7461](https://github.com/agentscope-ai/QwenPaw/issues/7461) | In-round queued events — inject user messages mid-tool-execution into current trajectory | ⭐⭐⭐ High interest |
| [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) | PowerContext pluggable long-term memory backend | ⭐⭐ Under review |
| [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | Workspace-scoped skill preload configuration | ⭐⭐ Under review |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | Import flow from Codex/Qoder (Pawport) | ⭐⭐ Under review |
| [#7482](https://github.com/agentscope-ai/QwenPaw/pull/7482) | Agent Kanban PawApp localization (zh/en) | ⭐ Likely next beta |
| [#7433](https://github.com/agentscope-ai/QwenPaw/pull/7433) | Website discussion menu + blog update | ⭐ Likely next release |

**Prediction:** In-round message injection (#7461) and A2A support (#7484) are the most requested features and align with the 2.x architecture roadmap. If the team maintains current velocity, expect at least one of these in **v2.2.0-rc** or the stable v2.2.0 release.

---

## 7. User Feedback Summary

**Pain Points:**
- **Cron instability** is the #1 complaint — duplicate fires, stuck "running" states, and missed inbox notifications make scheduled automation unreliable for production use cases.
- **Multi-agent opacity**: Users building complex agent teams report that sub-agent states are invisible until explicitly queried, causing anxiety during long-running tasks.
- **Memory/Embedding fragility**: ReMe indexing failures and config persistence bugs disrupt long-term memory, a key differentiator of QwenPaw 2.x.
- **Third-party gateway incompatibility**: The codex provider silently returns empty responses when backends don't stream, making debugging difficult.

**Positive Signals:**
- Test coverage sprints are being recognized and appreciated by the community.
- The desktop installer experience is improving (ReMe bundling fix, onboarding-aware memory startup).
- Security hardening (Tool Guard bypass patch) shows the team is responsive to safety concerns.

---

## 8. Backlog Watch

| Issue / PR | Age | Why It Needs Attention |
|---|---|---|
| [#7481](https://github.com/agentscope-ai/QwenPaw/issues/7481) | 1 day | macOS-specific but crashes active sessions; no fix PR yet |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 2 days | Security — dangerous instructions evading filters; no fix PR yet |
| [#7470](https://github.com/agentscope-ai/QwenPaw/issues/7470) | 1 day | MCP whitelist bypass undermines tool-level access control |
| [#7461](https://github.com/agentscope-ai/QwenPaw/issues/7461) | 1 day | High-impact feature request with no implementation started |
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | 1 day | A2A support is a roadmap commitment; community is waiting |
| [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) | 16 days | Memory backend PR under review; stalled in `Under Review` |
| [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | 13 days | Skill preload PR under review; stalled in `Under Review` |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | 20 days | Pawport import feature; first-time contributor, no recent activity |

---

*Digest generated from GitHub data via CoPaw on 2026-09-02. Repository: [agentscope-ai/QwenPaw](https://github.com/agentscope-ai/QwenPaw).*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw Project Digest — 2026-09-02

## 1. Today's Overview

The ZeptoClaw project shows low activity today with zero new issues and no released versions in the past 24 hours. Two pull requests were updated, both handled by Dependabot, reflecting routine dependency maintenance rather than feature development. The project appears to be in a stable but quiet phase, with no open issues and only one open PR remaining. Overall health indicators are neutral — no bugs or regressions reported, but also no momentum on user-facing improvements.

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Project Progress

- **PR #649** [CLOSED] — `chore(deps): bump rust from 1.95-slim-trixie to 1.97-slim-trixie`
  - Merged on 2026-09-01 by Dependabot.
  - Updated the Rust base Docker image, improving security posture and accessing bug fixes present in the 1.97 patch cycle.
  - [View PR](https://github.com/qhkm/zeptoclaw/pull/649)

- **PR #658** [OPEN] — `chore(deps): bump rust from 1.95-slim-trixie to 1.98-slim-trixie`
  - Created 2026-09-01 by Dependabot; currently awaiting review/merge.
  - Proposes a further bump to 1.98-slim-trixie, suggesting the maintainer is pursuing a more recent Rust image than the just-merged 1.97 update.
  - [View PR](https://github.com/qhkm/zeptoclaw/pull/658)

---

## 4. Community Hot Topics

No issues or PRs generated significant community discussion today. The only visible activity comes from Dependabot automation, indicating that user engagement is currently low or that the project audience is small. No open issues exist to track.

---

## 5. Bugs & Stability

No bug reports, crashes, or regressions were filed today. The two PRs are purely dependency updates with no indication of stability issues. The project's issue tracker is clear, which is a positive signal for current stability.

---

## 6. Feature Requests & Roadmap Signals

No new feature requests were raised today. The Dependabot PRs suggest the maintainer is keeping the Rust runtime image current, which is a maintenance signal rather than a roadmap indicator. No user-driven feature momentum is evident at this time.

---

## 7. User Feedback Summary

No user feedback was recorded in the past 24 hours. With zero open issues and no new discussions, it is not possible to assess current user satisfaction or pain points. The project may have a low-traffic community or users are not actively reporting through GitHub at this time.

---

## 8. Backlog Watch

- **PR #658** — Open since 2026-09-01 with no merge activity. While this is a routine Dependabot bump, the existence of two consecutive Rust image PRs (1.97 merged, 1.98 pending) may indicate the maintainer is either processing updates in quick succession or there is a gap in review turnaround. No long-unanswered or stale issues were detected.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-02

## 1. Today's Overview

ZeroClaw shows high development velocity with 36 issues and 50 PRs updated in the last 24 hours, indicating a mature contributor base and active maintainers. The project is in a deep architectural refinement phase: multiple RFCs are circling back for revised votes (Revisions 5, 10, and new filings), while security hardening work dominates the bug landscape. No new releases were published, suggesting the team is prioritizing structural stability over shipping. Health is strong — the open PR count (49) far exceeds merged/closed (1), signaling a large pipeline of contributions awaiting review.

## 2. Releases

No new releases were published in the last 24 hours. The project appears to be holding before a future release to absorb the incoming security fixes, RFC ratifications, and WASM plugin runtime changes currently in review.

## 3. Project Progress

**Merged/Closed Today (1 PR):**
- **#10306** — [Task] Gate web/ TypeScript in required CI and suppress 75 misleading `tsc` errors. Resolved, unblocking web frontend CI reliability. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10306)

**Notable PRs Advanced (Open, Updated Today):**
- **#9678** — Harden Git shell policy arguments by normalizing command words at the policy boundary for quote- and escape-aware representation. Critical for security posture. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9678)
- **#10380** — Restore persisted ACP transcripts from durable session store instead of trimmed model history. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10380)
- **#10094** — Require PostgreSQL backend tests in CI, ensuring memory backend coverage on every PR. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10094)
- **#10248** — Canonical principals and shared grant resolution, amending the auth seam to the ratified RFC #7141 Rev 8 identity contract. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10248)
- **#10521** — Honor `ZEROCLAW_CONFIG_DIR` in `Config::default()`, fixing a path-resolution inconsistency. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10521)
- **#10480** — Quarantine provider-rejected images with typed rejection signals for compatible and Anthropic providers. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10480)
- **#10455** — Preserve config write invariants in the gateway, rejecting masked/empty values for secret fields. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10455)

## 4. Community Hot Topics

The most discussed issues are overwhelmingly RFCs on core architecture, reflecting a community deeply engaged in shaping the project's direction:

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #9487 | RFC: Runtime-owned conversation sessions and transport surface adapters (Rev 5) | 31 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |
| #9488 | RFC: Unified file and attachment architecture for conversation surfaces (Rev 10) | 25 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) |
| #6996 | RFC: Granular sandbox policy — filesystem and network restrictions | 20 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| #8396 | RFC: Make wire protocol first-class in provider construction and onboarding | 17 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) |
| #8692 | Tracker: Maintainer decision queue for RFCs and design issues | 14 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |

**Analysis:** The topDiscussion centers on **session architecture**, **sandbox policy**, and **provider wire protocols** — the three pillars of ZeroClaw's trust and integration model. The fact that #9487 and #9488 are material replacements (Rev 5 and Rev 10) with explicit "open votes do not carry forward" language suggests a rigorous RFC process that values fresh consensus over accumulated position. The maintainer decision queue (#8692) being actively tracked indicates a bottleneck risk: many RFCs are waiting on maintainers to close discussion windows.

## 5. Bugs & Stability

**High-Severity Bugs (S0 — Data Loss / Security Risk):**

| Issue | Description | Fix PR? | Link |
|-------|-------------|---------|------|
| #10165 | Independent delegate bypasses `block_high_risk_commands` on its own risk profile | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) |
| #10495 | `Config::save()` can replace a populated `config.toml` with a near-empty file (702 bytes vs 109 KB) | #10521 may partially address config direction | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10495) |
| #9779 | `sops_dir` documented default not honoured — SOPs silently never load | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) |
| #9395 | Plugin `wasi:http` egress has no destination policy or config knob | Closed | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9395) |
| #8279 | Delegate bypasses parent's tool allowlist — sub-agent can invoke excluded tools | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8279) |
| #10513 | RPC `sops.run` returns a run ID for a step nothing will execute | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10513) |

**Medium-Severity Bugs (S1–S2):**

| Issue | Description | Link |
|-------|-------------|------|
| #10523 | Bootstrap file truncation at 6000 chars is invisible to operator | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10523) |
| #10063 | Anthropic-backed compatible gateways reject `image_url` blocks inside tool results | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10063) |
| #9896 | Startup banner reports `Memory: none` when effective backend is SQLite | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9896) |
| #7899 | OpenAI STT provider ignores env-based credentials | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7899) |

**Assessment:** Six S0-severity bugs remain open, with **three directly involving delegate/tool security bypasses** (#10165, #8279, #9395). These are the most concerning for production deployments. PR #9678 (Git shell policy hardening) and #10480 (provider image quarantine) are active fix attempts in the security domain. The SOP subsystem (#9779, #10513) has two related open bugs, suggesting a systemic issue in that component.

## 6. Feature Requests & Roadmap Signals

| Issue | Title | Signal | Link |
|-------|-------|--------|------|
| #10050 | Verbatim channel send over the gateway without an agent turn | Direct API gap fill | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) |
| #10076 | Composable WASM plugin runtime architecture | Major architectural shift | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) |
| #7759 | Decouple gateway WebSocket lifetime from agent turn lifecycle | UX/reliability improvement | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7759) |
| #8850 | Move optional channels & tools from compile-time flags to runtime WASM plugins | Modularization | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8850) |
| #10526 | Append-only session event history, deterministic state replay | Core data model change | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) |
| #10531 | Expose delegate sub-agent progress to parent (receipts, partial output) | Observability | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10531) |
| #10530 | Pass Anthropic extended-thinking params through OpenAI-compatible gateways | Provider compatibility | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10530) |
| #10529 | Support Anthropic `thinking.display` progress updates | Provider feature parity | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10529) |

**Prediction for Next Release:** The WASM plugin runtime (#10076, #8850) and append-only session history (#10526) are the largest architectural changes and may span multiple releases. More likely to ship soon: gateway WebSocket decoupling (#7759), verbatim channel send (#10050), and delegate progress exposure (#10531). Anthropic thinking features (#10530, #10529) are small, scoped, and align with provider roadmap — probable inclusion.

## 7. User Feedback Summary

**Pain Points:**
- **Silent failures dominate complaints.** Three issues (#9779, #10495, #10523) involve the daemon silently ignoring misconfiguration or truncating data without warning — operators only discover problems after downstream failures.
- **Delegate security boundaries are porous.** Users running multi-agent workflows report that sub-agents can bypass parent tool allowlists (#8279) and high-risk command blocks (#10165), creating real data-loss risk.
- **Config fragility.** `Config::save()` overwriting a 109 KB config with 702 bytes (#10495) and `ZEROCLAW_CONFIG_DIR` being ignored (#10521) suggest the configuration subsystem needs hardening.
- **Provider compatibility gaps.** Image URLs rejected mid-turn (#10063), env-based credentials ignored by STT (#7899), and extended-thinking params dropped through compatible gateways (#10530) indicate the provider abstraction layer has friction points.

**Satisfaction Signals:**
- The `crates/crush` issue (#5269) praises the project and reports a DX gap in the `nix run` path — a constructive first-time user experience report.
- The blacksmith CI isolation work (#10041, #10040) shows the team is responsive to contributor workflow concerns.
- The docs reader enhancement request (#10509) is a positive signal — users are engaging deeply with documentation.

## 8. Backlog Watch

**Long-Open Issues Needing Maintainer Attention:**

| Issue | Age | Risk | Why It Stalls | Link |
|-------|-----|------|---------------|------|
| #6996 | ~3.5 months | High | RFC revision cycle — needs new discussion window & vote snapshot | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| #8279 | ~2.5 months | S0 | Security bypass — needs maintainer review before fix PR | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8279) |
| #10165 | ~13 days | S0 | Same delegate security class as #8279 | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) |
| #8692 | ~2 months | Medium | Tracker itself needs maintainers to populate the decision queue | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #8396 | ~2.5 months | High | RFC awaiting maintainer review before next revision cycle | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) |
| #9779 | ~27 days | S0 | SOP subsystem bug — likely needs runtime maintainer | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) |
| #10513 | ~2 days | S2 | SOP RPC bug — same subsystem as #9779, likely related | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10513) |

**Critical Watch:** The two SOP bugs (#9779, #10513) and the two delegate security bugs (#8279, #10165) form two clusters that need urgent maintainer triage. The RFC decision queue (#8692) is the structural bottleneck — until maintainers close discussion windows on the pending RFCs, those architectural decisions (and the PRs they unblock) remain stalled.

---

*Generated from ZeroClaw GitHub data on 2026-09-02. All issue and PR links point to github.com/zeroclaw-labs/zeroclaw.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*