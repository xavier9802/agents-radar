# OpenClaw Ecosystem Digest 2026-08-28

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-28 10:57 UTC

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



# OpenClaw Project Digest — 2026-08-28

## 1. Today's Overview

OpenClaw shows very high engagement today with 500 issues and 500 PRs updated in the last 24 hours (329 open issues, 171 closed; 315 open PRs, 185 merged/closed). No new releases were published today. Activity is concentrated around bug fixes for session-state integrity, auth-provider reliability, and Control UI polish, with several high-severity P0/P1 issues still unresolved. The project is in a dense stabilization cycle around the 2026.8.1 beta trajectory, with active maintainer review on multiple fronts.

## 2. Releases

No new releases were published today. The latest tracked beta is **v2026.8.1-beta.3** (commit `5831b80`), with validation ongoing per Issue #125626.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#128223** — `fix(cli): resolve alias targets from the write snapshot` — Fixed alias resolution for `openclaw models aliases add` [#128223](https://github.com/openclaw/openclaw/pull/128223)
- **#123535** — `fix(ui): avoid session catalog refresh storms` — Prevented redundant full sidebar refreshes on browser focus changes [#123535](https://github.com/openclaw/openclaw/pull/123535)
- **#125471** — `fix(models): keep Claude CLI OAuth available in Control UI` — Restored Claude CLI OAuth persistence across gateway restarts by fixing provider-mode confusion [#125471](https://github.com/openclaw/openclaw/pull/125471)
- **#128371** — `fix(release): authorize focused beta evidence` — Unblocked beta.3 release by allowing focused Slack-test evidence instead of requiring full manifest [#128371](https://github.com/openclaw/openclaw/pull/128371)
- **#120900** — `feat(ui): review install policy warnings` — Added UI flow for admins to acknowledge and proceed past plugin install-policy warnings [#120900](https://github.com/openclaw/openclaw/pull/120900)
- **#123975** — `fix(scripts): clean up tsgo process trees on timeout or signal` — Routes `tsgo` through managed-process owner with watchdog timeout [#123975](https://github.com/openclaw/openclaw/pull/123975)
- **#126138** — `fix(sessions): suppress keyed channel-final mirrors` — Eliminates duplicate assistant messages in session transcripts from Telegram `routeReplyToOriginating` [#126138](https://github.com/openclaw/openclaw/pull/126138)
- **#128995** — `feat: make full session actions available from chat header` — Exposes pin, mark-unread, icon, copy-ID, and move-to-group from the header menu [#128995](https://github.com/openclaw/openclaw/pull/128995)

**Notable open PRs under review:**

- **#130993** — Fixes premature compaction in OpenAI Responses sessions (6 related failures) [#130993](https://github.com/openclaw/openclaw/pull/130993)
- **#130563** — Prevents early final responses in sequential subagent runs [#130563](https://github.com/openclaw/openclaw/pull/130563)
- **#126618** — Wraps native read/exec in tool_call for Tool Search directory/tools modes, fixing stalled loops on openai-completions models [#126618](https://github.com/openclaw/openclaw/pull/126618)
- **#127854** — Prevents stale cron results from appending to reset sessions [#127854](https://github.com/openclaw/openclaw/pull/127854)
- **#131575** — Restores truncated assistant reply endings on Android [#131575](https://github.com/openclaw/openclaw/pull/131575)
- **#131681** — Prevents duplicate answer rendering in Control UI during run completion [#131681](https://github.com/openclaw/openclaw/pull/131681)
- **#122604** — Fixes inherited auth-profile cooldown state being lost across multi-agent runs [#122604](https://github.com/openclaw/openclaw/pull/122604)

## 4. Community Hot Topics

1. **#42475** — [Feature] Per-agent cost budget enforcement at gateway level (23 comments, 1 👍) — Users running multiple agents need operator-level spend caps to prevent runaway model costs. This is a top-voted feature request indicating strong demand for multi-tenant budget controls. [Issue #42475](https://github.com/openclaw/openclaw/issues/42475)

2. **#125626** — OpenClaw 2026.8.1 beta feedback (22 comments) — Active community validation of the beta channel; release-validation workflow is in progress. [Issue #125626](https://github.com/openclaw/openclaw/issues/125626)

3. **#91009** — [P0] Codex PreToolUse hook spawns CPU-bound processes and stalls gateway RPC (21 comments, 2 👍) — A critical reliability issue where the codex integration spawns unbounded `openclaw-hooks` processes under tool-call load. [Issue #91009](https://github.com/openclaw/openclaw/issues/91009)

4. **#48003** — [P1] Steer mode does not inject messages mid-turn (20 comments, 4 👍) — A regression from March 2026 where `messages.queue.mode: "steer"` queues messages instead of injecting at tool boundaries, breaking real-time steering UX. [Issue #48003](https://github.com/openclaw/openclaw/issues/48003)

5. **#87744** — [P1] Codex-backed Telegram turns repeatedly time out (18 comments, 4 👍) — Reliability regression in Telegram + Codex integration where turns never reach terminal state. [Issue #87744](https://github.com/openclaw/openclaw/issues/87744)

**Theme analysis:** The community is heavily focused on **session-state correctness** and **auth/auth-profile reliability** — both are foundational reliability concerns. The cost-budget feature (#42475) signals users are scaling to multi-agent deployments and need operational guardrails.

## 5. Bugs & Stability

**P0 / Critical:**

- **#91009** — Codex PreToolUse hook spawns CPU-bound processes, stalls gateway RPC. No fix PR yet. [#91009](https://github.com/openclaw/openclaw/issues/91009)
- **#87109** — Gateway heap grows to 1073MB+ at idle on macOS; cron jobs fail silently under memory pressure. Refs #86613, #86509. [#87109](https://github.com/openclaw/openclaw/issues/87109)
- **#86215** — Codex OAuth refresh failures wedge agents for hours without alerting or profile rotation. [#86215](https://github.com/openclaw/openclaw/issues/86215)

**P1 / High:**

- **#48003** — Steer mode fails to inject messages mid-turn (regression from `KeyedAsyncQueue` commit). No fix PR yet. [#48003](https://github.com/openclaw/openclaw/issues/48003)
- **#87744** — Codex-backed Telegram turns time out without reaching `turn/completed`. [#87744](https://github.com/openclaw/openclaw/issues/87744)
- **#53408** — Write/exec tool parameters silently dropped after 15+ turn conversations. [#53408](https://github.com/openclaw/openclaw/issues/53408)
- **#98435** — MCP loopback transport doesn't auto-reconnect after gateway restart; `recovered=1` is misleading. [#98435](https://github.com/openclaw/openclaw/issues/98435)
- **#131150** — [P1] Slack DMs silently dropped for all accounts after gateway restart (`prepareSlackMessage` returns null). New issue from 2026.8.1. [#131150](https://github.com/openclaw/openclaw/issues/131150)
- **#100941** — Gateway drops concurrent tool-to-gateway WebSocket connections (1006) under parallel tool fan-out. [#100941](https://github.com/openclaw/openclaw/issues/100941)
- **#99947** — Codex harness mirrored-session-history read fails for ephemeral sessions and on failover. [#99947](https://github.com/openclaw/openclaw/issues/99947)
- **#53008** — Memory compaction blocks main processing lane for 10+ minutes, queueing all inbound messages. [#53008](https://github.com/openclaw/openclaw/issues/53008)
- **#41165** — Telegram DMs still route into `agent:main:main` after #40519 fix (regression). [#41165](https://github.com/openclaw/openclaw/issues/41165)

**P1/P2 Fixes Merged/Closed:**

- **#106914** (CLOSED) — `models list` crash on sonnet-5 cost lookup (2026.7.1 regression). Fixed. [#106914](https://github.com/openclaw/openclaw/issues/106914)
- **#103884** (CLOSED) — GPT-5.6 Sol rejected by OpenClaw Codex runtime. Fixed. [#103884](https://github.com/openclaw/openclaw/issues/103884)
- **#116010** (CLOSED) — All persistent sessions capped at 128k context regardless of model. Fixed. [#116010](https://github.com/openclaw/openclaw/issues/116010)
- **#112248** (CLOSED) — `@openclaw/codex` plugin fails to register on gateway boot. Fixed. [#112248](https://github.com/openclaw/openclaw/issues/112248)

## 6. Feature Requests & Roadmap Signals

- **#42475** — Per-agent cost budget enforcement at gateway — strong community signal for multi-agent operational tooling. [Issue #42475](https://github.com/openclaw/openclaw/issues/42475)
- **#60572** — Multi-Slot Memory Architecture — replacing single `plugins.slots.memory` with layered memory providers (8 comments, 3 👍). [Issue #60572](https://github.com/openclaw/openclaw/issues/60572)
- **#71736** — Control UI plugin contribution slots (SDK surface for chat modes, approval cards, event classifiers) — proposed but not yet implemented. [Issue #71736](https://github.com/openclaw/openclaw/issues/71736)
- **#88154** — Slack Modal Support for interactive workflows — structured input via native modals. [Issue #88154](https://github.com/openclaw/openclaw/issues/88154)
- **#52640** — Persistent task-status surface for long-running channel turns — Discord-first, generic abstraction later. [Issue #52640](https://github.com/openclaw/openclaw/issues/52640)
- **#71058** — Multiple Azure/Teams bots on a single gateway — currently limited to one Teams bot identity. [Issue #71058](https://github.com/openclaw/openclaw/issues/71058)
- **#28300** — Theme Customization System with preset themes + custom studio (6 comments, 5 👍 — highest reaction count). [Issue #28300](https://github.com/openclaw/openclaw/issues/28300)
- **#131370** — Goal management without slash commands in Control UI (open PR in progress). [PR #131370](https://github.com/openclaw/openclaw/pull/131370)

**Prediction:** Cost budgeting (#42475) and multi-slot memory (#60572) are the most operationally significant features and likely candidates for the next major

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report
**Date:** 2026-08-28 | **Source:** Community Digest Analysis

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape is undergoing a **stabilization and architectural maturation phase**. Projects are shifting from feature expansion to hardening session-state correctness, provider abstraction, and multi-agent operational tooling. Eight of eleven tracked projects show active development; three (NullClaw, ZeptoClaw, IronClaw) are dormant or unresponsive. The dominant trend is a move from monolithic agent designs toward composable, multi-tenant architectures with explicit ownership boundaries for sessions, credentials, and transport layers.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Latest Release | Open PRs | Health Score |
|---|---|---|---|---|---|
| **OpenClaw** | 500 (329 open) | 500 (315 open) | v2026.8.1-beta.3 | 315 | 🟡 6/10 — P0/P1 backlog |
| **NanoBot** | 1 resolved | 27 updated | None | N/A | 🟢 7/10 — Active refactoring |
| **Hermes Agent** | 50 updated | 50 updated | v0.20.6 (Aug 27) | Low | 🟢 8/10 — Responsive patch cycle |
| **PicoClaw** | 3 updated | 7 updated | None | 1 | 🟡 4/10 — Low engagement |
| **NanoClaw** | 10 touched | 50 touched | None | High | 🟢 8/10 — Very high velocity |
| **LobsterAI** | 5 closed | 12 merged | v2026.8.26 | None | 🟢 7/10 — Release-polish mode |
| **Moltis** | 0 new | 2 merged | None | None | 🟡 5/10 — Focused maintenance |
| **CoPaw** | 49 updated | 47 updated | v2.2.0-beta.2 | N/A | 🟢 8/10 — High throughput |
| **ZeroClaw** | 23 updated | 50 updated | v0.8.5 (in progress) | 47 | 🟢 7/10 — Active stabilization |
| **NullClaw** | — | — | — | — | 🔴 2/10 — No activity |
| **ZeptoClaw** | — | — | — | — | 🔴 2/10 — No activity |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of operation:** OpenClaw's 500-issue/PR volume dwarfs all competitors, indicating it serves the largest and most complex deployment base (multi-agent, multi-channel, gateway architecture).
- **Depth of channel integrations:** Supports Discord, Telegram, Slack, WebSocket, MCP loopback, and more — broader than NanoBot (focused TUI/web), Hermes (Desktop-first), or PicoClaw (IRC/Matrix).
- **Established release cadence:** Regular beta trajectory (v2026.8.1) with structured validation workflows, unlike NanoClaw and ZeroClaw which are still accumulating toward their next tagged release.

**Technical approach differences:**
- OpenClaw uses a **gateway-centric model** with separate auth providers and session catalogs, while NanoBot and Hermes are more agent-process-centric.
- OpenClaw's **Control UI** is the most feature-rich admin surface, but it also carries the heaviest bug burden (P0 Codex hook, heap growth, steer-mode regression).

**Community size:** OpenClaw has by far the largest issue/PR volume and comment engagement (#42475 with 23 comments on cost budgeting), suggesting a user base scaling into multi-agent/enterprise territory.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Need |
|---|---|---|
| **Session-state integrity** | OpenClaw, Hermes, ZeroClaw, NanoBot | Compaction correctness, duplicate-turn prevention, stale-profile resurrection |
| **Auth/provider reliability** | OpenClaw, NanoClaw, Hermes, NanoBot | OAuth refresh, stale-secret rejection, cooldown-state persistence across multi-agent runs |
| **Context/memory management** | NanoBot, Hermes, OpenClaw, ZeroClaw | Explicit recall over auto-injection, MCP schema budgets, token bloat control |
| **Multi-tenant / multi-agent ops** | OpenClaw, CoPaw, ZeroClaw | Per-agent cost budgets, team Hub, session-scoped prompt attachments |
| **Cross-platform Desktop/TUI** | Hermes, CoPaw, NanoBot | Windows stability (disproportionate bug surface), SSH profile routing, boot timeouts |
| **Channel attachment handling** | NanoClaw, ZeroClaw, OpenClaw | URL vs. fetchData contract mismatch, large-image session wedging |
| **Mobile experience** | CoPaw, OpenClaw | Android input UX, React Native exploration, truncated replies |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | CoPaw | NanoClaw | ZeroClaw | NanoBot |
|---|---|---|---|---|---|---|
| **Architecture** | Gateway + Control UI | Desktop-first app | Desktop + planned mobile | Provider-abstracted runtime | RFC-driven composable runtime | Event-loop agent runner |
| **Target user** | Multi-agent operators, enterprise | Individual power users, Desktop users | Team/multi-tenant (upcoming Hub) | Developer/plugin builders | Researchers/forward-leaning adopters | Embedded/single-agent users |
| **Lang / stack** | TypeScript | Python | Python + Rust (Tauri) | TypeScript | Rust | Python |
| **Key differentiator** | Deepest channel integrations | Fastest patch-cycle responsiveness | Planned multi-tenant Hub + mobile | Aggressive provider refactor | Mature RFC design process | Lean, refactoring-focused |
| **Session model** | Gateway-managed catalogs | Bot-mode + Desktop lifecycle | Workspace-scoped | Provider-abstracted | Runtime-owned (RFC) | Event-loop persistent |
| **Release cadence** | Beta trajectory | Rapid patch (v0.20.6) | Beta (v2.2.0-beta.2) | Pre-release hardening | Weekly stabilization cuts | Sprint-driven, no tags |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (high velocity, active releases):**
- **Hermes Agent** — v0.20.6 shipped; 50 PRs/day; responsive salvage cycle
- **CoPaw** — v2.2.0-beta.2 released; 49 issues/47 PRs; strong E2E test coverage push
- **NanoClaw** — 50 PRs/day; major provider refactor in flight

**Tier 2 — Active Stabilization (steady progress, in-progress releases):**
- **OpenClaw** — 500 volume but P0/P1 backlog; beta trajectory with unresolved criticals
- **ZeroClaw** — 50 PRs/23 issues; v0.8.5 stabilization with mature RFC process
- **NanoBot** — 27 PRs focused on architectural refactoring; no release yet
- **LobsterAI** — 12 PRs merged; post-release polish; 3 stale high-severity bugs

**Tier 3 — Low Maintenance (minimal activity):**
- **Moltis** — 2 PRs, correctness-focused; no new issues; quiet tracker
- **PicoClaw** — 7 PRs (mostly dependabot); 1 open UI fix; low community engagement

**Tier 4 — Dormant:**
- **NullClaw, ZeptoClaw** — No activity; **IronClaw** — digest generation failed

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Multi-tenant / team deployments** | OpenClaw #42475 (cost budgets), CoPaw Hub RFC, ZeroClaw session-scoped prompts | Expect operational tooling (budgets, team isolation) to become table stakes for production agents |
| **Explicit memory over implicit injection** | NanoBot #5571 (explicit recall), Hermes #96795 (memory governance), OpenClaw #60572 (multi-slot memory) | Memory architecture is maturing — plan for explicit `recall` tools rather than auto-injected context |
| **Provider abstraction hardening** | NanoClaw's 6-PR provider refactor, ZeroClaw wire-protocol RFC, OpenClaw auth-provider fixes | Multi-provider support is moving from bolted-on to first-class; vendor lock-in risk decreases |
| **Session ownership as architectural primitive** | ZeroClaw #9487 (runtime-owned sessions), NanoBot session persistence off event loop, Hermes Desktop lifecycle | Clean session boundaries are a prerequisite for cron, multi-agent, and relay workflows |
| **Cross-platform fragility** | Windows bugs across NanoBot, Hermes, OpenClaw; Android UX gaps in OpenClaw and CoPaw | Test on target platforms early; assume TUI/Desktop cross-platform is a ongoing effort, not a solved problem |
| **RFC-driven design for complex subsystems** | ZeroClaw's mature RFC process (9 revisions on attachments), NanoBot architectural PRs | Projects investing in design-discussion infrastructure produce more maintainable architectures |
| **Image/multimodal pipeline fragility** | OpenClaw Codex image 400s, Hermes vision session bricks, ZeroClaw S1 image rejection, NanoClaw WhatsApp photo wedging | Multimodal support is universally fragile — expect providers to diverge on image handling; build resize/retry defensively |

---

**Bottom line for technical decision-makers:** The ecosystem is converging on **explicit session ownership, provider abstraction, and multi-tenant operational tooling** as the three pillars of the next generation. Projects with active RFC processes (ZeroClaw) and rapid patch cycles (Hermes) are best positioned for predictability. OpenClaw offers the deepest integrations but carries the highest stability risk. For new deployments, watch CoPaw's multi-tenant Hub and NanoClaw's provider refactor as potential architectural reference patterns.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-28

## 1. Today's Overview

NanoBot shows strong development velocity today with 27 PRs updated and 1 issue resolved, indicating a period of active refactoring and stabilization. The primary effort is concentrated around architectural hardening — session persistence off the event loop, explicit tool-execution boundaries, and memory system redesign — rather than new feature shipping. No new releases were published today, suggesting the team is still integrating today's changes. Activity is heavily contributor-driven (chengyongru accounts for the majority), which signals focused maintenance sprints.

## 2. Releases

No new releases today.

---

## 3. Project Progress

**Merged/Closed PRs (6):**

| PR | Summary |
|---|---|
| [#5579](https://github.com/HKUDS/nanobot/pull/5579) | Session persistence moved off the event loop with cancellation-safe async APIs |
| [#5578](https://github.com/HKUDS/nanobot/pull/5578) | Fixed Windows clipboard-image test race condition |
| [#5577](https://github.com/HKUDS/nanobot/pull/5577) | Preserved full TUI in Herdr panes via alternate-screen layout |
| [#5576](https://github.com/HKUDS/nanobot/pull/5576) | Duplicate Herdr TUI fix (merged alongside #5577) |
| [#5574](https://github.com/HKUDS/nanobot/pull/5574) | Made provider fallback attempts explicit with immutable `ProviderAttempt` |
| [#5569](https://github.com/HKUDS/nanobot/pull/5569) | Extracted tool execution boundary out of `AgentRunner` |
| [#5575](https://github.com/HKUDS/nanobot/pull/5575) | Removed `consolidationRatio` config; simplified memory archiving |
| [#5572](https://github.com/HKUDS/nanobot/pull/5572) | Defaulted request concurrency to unlimited when unset |
| [#4346](https://github.com/HKUDS/nanobot/pull/4346) | Fixed image-path leak by marking stripped images as unviewable |

**Key theme:** A major refactoring sweep across session management, agent runner architecture, provider fallbacks, and memory consolidation — all aimed at long-term maintainability and stability.

---

## 4. Community Hot Topics

**Most discussed/open PRs requiring attention:**

- **[PR #5568](https://github.com/HKUDS/nanobot/pull/5568)** — *AgentRunner context compaction ownership* — High-priority architectural change; shifts context-pressure handling into the runner before each provider call. Signals a need for more predictable token management in long sessions.

- **[PR #5580](https://github.com/HKUDS/nanobot/pull/5580)** — *Session persistence off event loop (follow-up)* — P1 priority; introduces a `SessionIO` boundary for worker scheduling and cancellation. This is a continuation of #5579 and indicates the original fix needs further hardening.

- **[PR #5504](https://github.com/HKUDS/nanobot/pull/5504)** — *Model retry status surfacing in UI (NAN-34)* — P1; users need visibility into retry countdowns across TUI/WebUI. Reflects frequent pain around transient provider failures.

- **[PR #5571](https://github.com/HKUDS/nanobot/pull/5571)** — *Require explicit recall by default* — P1; stops auto-injecting memory files into the system prompt, routing durable memory through a dedicated `recall_memory` tool instead. Major behavior change that will affect power users relying on implicit memory.

- **[PR #5388](https://github.com/HKUDS/nanobot/pull/5388)** — *Budget model-visible MCP schemas* — Opt-in byte budget for MCP tool schemas. Addresses token bloat from large MCP registries.

**Underlying need:** The community is pushing hard on **context management** (compaction, memory recall, MCP schema budgets) and **observability** (retry status, session persistence reliability). These are the top pain points for long-running agent sessions.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|---|---|---|---|
| **P1** | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | Session persistence blocking the event loop — ongoing fix after #5579 | Open, in progress |
| **P1** | [#5504](https://github.com/HKUDS/nanobot/pull/5504) | Model retry status not surfaced to users | Open, in progress |
| **P2** | [#5581](https://github.com/HKUDS/nanobot/pull/5581) | Windows TUI cursor corruption on exit | Open, fix proposed |
| **P2** | [#5483](https://github.com/HKUDS/nanobot/pull/5483) | Deleted sessions recreated by delayed cross-session messages | Open, fix proposed |
| **P2** | [#5382](https://github.com/HKUDS/nanobot/pull/5382) | `os.replace()` crash on Windows `PermissionError` during heartbeat — crashes entire gateway | Open, unfixed |
| **P2** | [#5573](https://github.com/HKUDS/nanobot/pull/5573) | Expired OAuth tokens not auto-refreshed for MCP | Open, fix proposed |
| **P2** | [#5577/#5576](https://github.com/HKUDS/nanobot/pull/5577) | TUI UI lost in Herdr panes | ✅ Merged |

**Notable regression:** [#5382](https://github.com/HKUDS/nanobot/pull/5382) causes gateway crashes under Windows — confirmed twice in production logs. Still open with no merged fix.

---

## 6. Feature Requests & Roadmap Signals

| PR | Feature | Likelihood for Next Release |
|---|---|---|
| [#5571](https://github.com/HKUDS/nanobot/pull/5571) | Explicit memory recall (opt-out of auto-injection) | **High** — P1, already implemented, needs review |
| [#5570](https://github.com/HKUDS/nanobot/pull/5570) | Pluggable `MemoryBackend` with `ingest`/`recall` API | **High** — pairs with #5571, foundational |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) | Per-spawn model presets via `spawnPresets` allowlist | **Medium** — resolves #4231, design reviewed |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) | Byte budget for MCP tool schemas | **Medium** — opt-in, addresses token bloat |
| [#5573](https://github.com/HKUDS/nanobot/pull/5573) | Auto-refresh for expired MCP OAuth tokens | **Medium** — quality-of-life, fix-oriented |
| [#4429](https://github.com/HKUDS/nanobot/issue/4429) | Custom provider thinking-style configuration | **Low** — closed but no release yet; niche provider support |

**Roadmap signal:** The memory system is being fundamentally re-architected (explicit recall + pluggable backend). Expect a significant migration for users relying on the current auto-injected `MEMORY.md` / `history.jsonl` behavior.

---

## 7. User Feedback Summary

- **Windows stability remains a weak spot:** Multiple P2 bugs target Windows specifically — clipboard race (#5578, fixed), cursor corruption (#5581, open), gateway crash on `os.replace()` (#5382, open). Windows users should expect ongoing friction.
- **Session durability concerns:** Delayed messages recreating deleted sessions (#5483) and OAuth token expiry breaking MCP tools (#5573) indicate users are running long-lived gateways where these edge cases are impactful.
- **Context management pain:** The volume of PRs around compaction (#5568), memory recall (#5571), and MCP schema budgets (#5388) reflects community frustration with token bloat and unpredictable context growth.
- **Retry visibility gap:** Users cannot see model retry progress in the UI (#5504), causing confusion during transient provider failures — a clear UX deficit.

---

## 8. Backlog Watch

| Item | Age | Risk |
|---|---|---|
| [#5382](https://github.com/HKUDS/nanobot/pull/5382) — Windows `os.replace()` gateway crash | 16 days | **High** — crashes production gateways; no fix merged |
| [#5483](https://github.com/HKUDS/nanobot/pull/5483) — Deleted sessions recreated by delayed messages | 6 days | **Medium** — data integrity issue; fix ready but open |
| [#5581](https://github.com/HKUDS/nanobot/pull/5581) — Windows TUI cursor corruption | <1 day | **Low** — recent submission, fix proposed |
| [#5573](https://github.com/HKUDS/nanobot/pull/5573) — Expired OAuth tokens not refreshed | 1 day | **Medium** — fix open, blocks long-running MCP sessions |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) — Per-spawn model presets | 1 day | **Low** — feature request, awaiting review |

**Top concern:** [#5382](https://github.com/HKUDS/nanobot/pull/5382) has been open for 16 days and causes full gateway crashes on Windows. It should be prioritized before the next release.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-28

## 1. Today's Overview

Hermes Agent is in a period of intense patching and stabilization around the v0.20.6 release. With 50 issues and 50 PRs updated in the last 24 hours, the project is actively closing technical debt accumulated since v0.20.5, particularly around session resilience, Desktop reliability, and cross-platform edge cases. The velocity is high and maintainer-driven — multiple salvage PRs landed in a single day, indicating a focused effort to ship quality in the newest patch release. Activity is predominantly bug-fix oriented, with a handful of feature RFCs and improvements in flight.

## 2. Releases

### v0.20.6 (v2026.8.27) — Patch Release

- **Release date:** August 27, 2026
- **Scope:** Rolls up approximately **525 PRs** merged since v0.20.5 into a stable tagged release for Docker images, hosted deployments, and fresh installs.
- **Breaking changes:** None announced.
- **Migration notes:** Standard patch upgrade path — no config or session migration required.

## 3. Project Progress

**Merged/closed today (from PR & issue data):**

- **#97075** — Fix for generic image 400s (Alibaba/DashScope-style gateways) now strips images and retries instead of wedging the turn.
- **#97069** — Fix: deleted bots no longer resurrect from persisted session tiles.
- **#97077** — Fix: assistant-history image parts no longer replay as `input_image` 400s in OpenAI Responses API.
- **#97070** — Fix: "media exceeds size limit" 400s now shrink-and-retry instead of aborting.
- **#97071** — Fix: model picker recovers sessions after a completed failed resume build.
- **#97073** — Fix: dynamic tool schemas are now rebuilt at the compaction boundary (critical for forever-sessions in Bot Mode).
- **#97076** — Fix: fail fast on catalog-listed uncallable Muse Spark contributor.
- **#97074** — Fix: stop failed sends from delivering anyway in cross-connection relay.
- **#97066** — Fix: stale model/provider keys no longer survive session `model_config` writes.
- **#87891** — Fix: closes Anthropic OAuth CSRF gap, cross-process refresh race, and API-key shadowing.
- **#97055** — Security: pins `cua-driver` installer to a tagged ref and verifies sha256 (prevents supply-chain risk from mutable `main` fetches).
- **#60709** (issue closed) — `skills_guard` false-positive rules reduced; community installs unblocked.
- **#92376** (issue closed) — Security scanner no longer flags docs mentioning `AGENTS.md`/`CLAUDE.md` as critical.
- **#96282** (issue closed) — Desktop boot timeout from stdout redirect change resolved.
- **#94818** (issue closed) — Model switching in Bot/Group Chats fixed.

**Key themes:** Session state resilience, image-handling reliability across providers, security hardening of install/auth paths, and Desktop profile lifecycle correctness.

## 4. Community Hot Topics

| Rank | Issue / PR | Comments | Status | Topic |
|------|-----------|----------|--------|-------|
| 1 | [#69078](https://github.com/NousResearch/hermes-agent/issues/69078) | 14 | ✅ Closed | xAI grok-4.5 vision session brick |
| 2 | [#96282](https://github.com/NousResearch/hermes-agent/issues/96282) | 14 | ✅ Closed | Desktop boot timeout after stdout redirect |
| 3 | [#77111](https://github.com/NousResearch/hermes-agent/issues/77111) | 10 | 🟡 Open | RFC: RealtimeVoiceProvider ABC interface |
| 4 | [#90477](https://github.com/NousResearch/hermes-agent/issues/90477) | 9 | 🟡 Open | Desktop profile switch on SSH spawns local backend |
| 5 | [#80670](https://github.com/NousResearch/hermes-agent/issues/80670) | 5 | 🟡 Open | "Could not react" on resumed conversations |
| 6 | [#95188](https://github.com/NousResearch/hermes-agent/issues/95188) | 4 | 🟡 Open | Deleted profile resurrects on Windows |

**Analysis:** The top-voted discussions center on **session durability** (vision/image handling bricking sessions, stale profiles resurrecting) and **cross-platform Desktop reliability** (SSH profile routing, boot timeouts). The RealtimeVoiceProvider RFC (#77111) signals community demand for a clean abstraction over four competing duplex-voice PRs — users want a unified interface rather than a merge queue. The SSH profile-switch bug (#90477) highlights a growing use case: remote Desktop-to-backend connections that need profile isolation.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| 🔴 P1 | [#96282](https://github.com/NousResearch/hermes-agent/issues/96282) | Desktop boot timeout after stdout redirect change | ✅ Closed |
| 🔴 P2 | [#69078](https://github.com/NousResearch/hermes-agent/issues/69078) | xAI vision 400 permanently bricks session | ✅ Closed (via #97075 / #97077) |
| 🔴 P2 | [#95188](https://github.com/NousResearch/hermes-agent/issues/95188) | Deleted profile resurrects on Windows (stale `lastProfileByConnection` + cron) | 🟡 Open |
| 🔴 P2 | [#97019](https://github.com/NousResearch/hermes-agent/issues/97019) | `host_supervisor` uses `os.kill(pid, 0)` — unsafe on Windows | 🟡 Open |
| 🟡 P2 | [#90477](https://github.com/NousResearch/hermes-agent/issues/90477) | SSH profile switch spawns LOCAL backend, wrong profile | 🟡 Open |
| 🟡 P2 | [#80670](https://github.com/NousResearch/hermes-agent/issues/80670) | Message reaction fails on resumed/historical conversations (4040) | 🟡 Open |
| 🟡 P2 | [#96993](https://github.com/NousResearch/hermes-agent/issues/96993) | Windows real-profile cookie copy purged on first Chrome launch | 🟡 Open |
| 🟡 P2 | [#97029](https://github.com/NousResearch/hermes-agent/issues/97029) | `MCPServerTask._stdio_children_dead()` inverted — every stdio MCP call fails under `cron` | 🟡 Open |
| 🟡 P2 | [#97017](https://github.com/NousResearch/hermes-agent/issues/97017) | Desktop force-injects `desktop_ui` toolset into every request — severe latency | 🟡 Open |
| 🟡 P2 | [#97020](https://github.com/NousResearch/hermes-agent/issues/97020) | TUI loses reasoning & Fast status without local Agent | 🟡 Open |
| 🟡 P2 | [#93911](https://github.com/NousResearch/hermes-agent/issues/93911) | Desktop relay abandons `bot_relay.deliver` after 30s timeout | 🟡 Open |
| 🟢 P3 | [#78007](https://github.com/NousResearch/hermes-agent/issues/78007) | A2A long tasks never complete (client 120s < server 300s window) | 🟡 Open |
| 🟢 P3 | [#96729](https://github.com/NousResearch/hermes-agent/issues/96729) | Real-profile local launch leaves auth DBs 0644, injects mock-keychain flags | 🟡 Open |

**Notable regression pattern:** Multiple vision/image-related session-bricking bugs (#69078, #76884, #97077) suggest the image-handling pipeline has systemic fragility that is only now being addressed in v0.20.6.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Likelihood for Near-Term |
|-------|---------|--------------------------|
| [#77111](https://github.com/NousResearch/hermes-agent/issues/77111) | RealtimeVoiceProvider ABC — unified interface for 4 competing voice PRs | **High** — maintainer guidance already referenced in `AGENTS.md` |
| [#96954](https://github.com/NousResearch/hermes-agent/issues/96954) | Abbreviated text replies resolve to native clarify choices (e.g., `1번`, `첫 번째`) | **Medium** — UX polish, low risk |
| [#96795](https://github.com/NousResearch/hermes-agent/issues/96795) | Memory write governance — explicit-only writes + capacity warnings | **Medium** — addresses real power-user workflow |
| [#91813](https://github.com/NousResearch/hermes-agent/issues/91813) | Bot Mode group chat — per-bot live session transcript | **Medium** — multi-agent supervision need |
| [#92874](https://github.com/NousResearch/hermes-agent/pull/92874) | Create folders from Desktop file tree | **High** — PR already open, aligns with design-system rebuild (#96726) |
| [#96726](https://github.com/NousResearch/hermes-agent/pull/96726) | Rebuild Bot Mode on the app's design system | **High** — large refactor, already in progress |

## 7. User Feedback Summary

**Pain points expressed:**

- **Session fragility:** Users report sessions being permanently bricked by image-handling failures (xAI, MiniMax, Codex adapter) — a recurring and high-impact frustration. The v0.20.6 patch series directly addresses this, but multiple users experienced it before fixes landed.
- **Desktop lifecycle bugs:** Profile resurrection (#95188), SSH profile routing (#90477), and model caching divergence (#75128) indicate the Desktop app's state management needs harderening, especially for remote/SSH workflows.
- **Security scanner false positives:** Community skills and documentation are being hard-blocked by overly aggressive `skills_guard` rules (#60709, #92376), raising friction for plugin authors.
- **Cross-connection relay reliability:** Delivery failures and timeout issues (#93911, #97051, #78007) affect multi-machine Bot Mode setups, a growing use case.
- **Windows-specific issues:** A disproportionate number of today's bugs (#95188, #96360, #97019, #96993) are Windows-specific, suggesting the platform needs more focused testing investment.

**Satisfaction signals:** The rapid turnaround on salvage PRs and the v0.20.6 release demonstrate responsive maintenance. Users who reported issues see them closed within days.

## 8. Backlog Watch

| Issue | Days Open | Why It Needs Attention |
|-------|-----------|----------------------|
| [#77111](https://github.com/NousResearch/hermes-agent/issues/77111) | ~56 | Four competing voice PRs need an ABC — blocks feature consolidation |
| [#78007](https://github.com/NousResearch/hermes-agent/issues/78007) | ~86 | A2A long-task timeout is a hard blocker for multi-machine deployments |
| [#31980](https://github.com/NousResearch/hermes-agent/issues/31980) | ~95 | Background terminal processes lose tracking after gateway restart — affects cron/reliability workflows |
| [#61184](https://github.com/NousResearch/hermes-agent/issues/61184) | ~82 | `disabled_toolsets` doesn't block MCP tools in `hermes -z` — security/reliability gap |
| [#95188](https://github.com/NousResearch/hermes-agent/issues/95188) | 2 | Profile resurrection on Windows — data integrity issue, likely needs a targeted fix PR |
| [#97029](https://github.com/NousResearch/hermes-agent/issues/97029) | 0 | Inverted `_stdio_children_dead()` breaks all stdio MCP under cron — easy fix, high impact |
| [#97019](https://github.com/NousResearch/hermes-agent/issues/97019) | 0 | `os.kill(pid, 0)` on Windows is a correctness + safety issue |

---

**Overall project health:** 🟢 Active and responsive. The v0.20.6 release and rapid PR turnaround show strong maintenance velocity. The primary risk area is Windows platform stability and session-state resilience under edge-case provider responses. The backlog contains several high-impact but straightforward fixes that could be prioritized in the next patch cycle.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-28

## 1. Today's Overview

PicoClaw showed moderate activity over the last 24 hours with **3 issues updated** (1 open, 2 closed) and **7 PRs updated** (1 open, 6 merged/closed). No new releases were published. The project is in a healthy maintenance cadence: dependency updates dominate the merged PRs, while a single meaningful UI fix remains open. Community engagement is low on new features (zero reactions across all items), suggesting the contributor base is small but steady.

## 2. Releases

**No new releases** were published in the last 24 hours.

## 3. Project Progress

**Merged / Closed PRs:**

| PR | Description | Author |
|---|---|---|
| [#3332](https://github.com/sipeed/picoclaw/pull/3332) | Bump `aws-sdk-go-v2` from 1.42.0 → 1.43.4 | dependabot |
| [#3333](https://github.com/sipeed/picoclaw/pull/3333) | Bump `mautrix/go` from 0.27.0 → 0.29.0 | dependabot |
| [#3334](https://github.com/sipeed/picoclaw/pull/3334) | Bump `anthropic-sdk-go` from 1.55.1 → 1.62.0 | dependabot |
| [#3335](https://github.com/sipeed/picoclaw/pull/3335) | Bump `aws-sdk-go-v2/config` from 1.32.25 → 1.32.35 | dependabot |
| [#3336](https://github.com/sipeed/picoclaw/pull/3336) | Bump `aws-sdk-go-v2/service/bedrockruntime` from 1.53.3 → 1.57.1 | dependabot |
| [#1555](https://github.com/sipeed/picoclaw/pull/1555) | Merge backlog fixes from PRs #1390, #1389, #1383, #1381 | xuwei-xy |

**Open PR:**

- [#3347](https://github.com/sipeed/picoclaw/pull/3347) — **Fix for laggy web UI** when rendering large chat text. Tested on desktop and mobile (Brave). Author notes limited TypeScript/Node expertise; fix was externally analyzed.

## 4. Community Hot Topics

- **[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) — Better support for long messages in IRC** (8 comments, open)
  The most discussed open issue. Users want PicoClaw to reassemble IRCv3 messages split at 512 bytes into a single cohesive context. This reflects a real pain point for users running PicoClaw as an IRC bot with long conversation threads. No reactions yet, but sustained discussion (8 comments since July) indicates active interest.

- **[Issue #3330](https://github.com/sipeed/picoclaw/issues/3330) — Dynamic model override in delegate/spawn/subagent tools** (closed, stale)
  Users want per-call model selection in delegation tools rather than static config. Closed as stale, but the underlying need—flexible model routing—is likely to resurface.

- **[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331) — Support any model with /audio/transcriptions** (closed, stale)
  Request to allow non-Whisper models via the transcription endpoint. Closed as stale; feature gap remains unaddressed.

## 5. Bugs & Stability

- **[PR #3347](https://github.com/sipeed/picoclaw/pull/3347) — Web UI lag with large chat messages** (open)
  Severity: **Medium**. The web interface becomes unresponsive with large text volumes. Fix is pending review/merge. No crashes reported.

- No new bug reports or regression signals were filed today.

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Status | Likelihood |
|---|---|---|---|
| IRC long-message reassembly | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | Open | **High** — active discussion, concrete use case |
| Dynamic model override in delegate tools | [#3330](https://github.com/sipeed/picoclaw/issues/3330) | Closed (stale) | Medium — valid feature gap, may reappear |
| Non-Whisper ASR transcription models | [#3331](https://github.com/sipeed/picoclaw/issues/3331) | Closed (stale) | Medium — depends on maintainers' ASR priorities |

The IRC message-handling request is the strongest signal for the next feature iteration.

## 7. User Feedback Summary

- **Pain point: IRC message fragmentation.** Users sending long messages via IRCv3 see them split at 512 bytes, and PicoClaw treats each fragment as a separate message. This breaks conversation coherence.
- **Pain point: Web UI performance.** Large chat histories cause noticeable lag, particularly on mobile browsers. The pending PR #3347 directly addresses this.
- **Satisfaction signal:** Dependabot-driven dependency updates are being merged consistently, indicating the project is keeping its AWS, Anthropic, and Matrix dependencies current without manual intervention.
- **Dissatisfaction signal:** Two feature requests (#3330, #3331) were closed as stale without resolution, which may frustrate users seeking ASR flexibility and dynamic model routing.

## 8. Backlog Watch

- **[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)** — Open since 2026-07-22 with 8 comments. Requires maintainer attention to define an IRCv3 message-reassembly approach.
- **[PR #3347](https://github.com/sipeed/picoclaw/pull/3347)** — Open since 2026-08-27. A UI performance fix that has been tested by the author but awaits review. Timely merge would improve user experience significantly.
- **[Issue #3330](https://github.com/sipeed/picoclaw/issues/3330)** & **[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)** — Both closed as stale but represent unresolved feature gaps. Consider reopening or tracking as roadmap items if community interest grows.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-28

## 1. Today's Overview

NanoClaw shows **very high development velocity** today, with 50 PRs and 10 issues touched in the last 24 hours. The project is in a major **provider refactor cycle**, with six PRs from `zvi-fried` reshaping the provider contract layer (codex, opencode, runtime, host, setup verifier). No new releases were published today. Activity is heavily concentrated around provider architecture, Discord/WhatsApp channel stability fixes, and skill-scoping improvements — the project appears to be in a pre-release hardening phase despite the absence of a tagged version.

## 2. Releases

No new releases published today.

---

## 3. Project Progress

**Merged/Closed PRs (4 today):**

- **PR #3471** — Fixed pnpm `minimumReleaseAge` gate being silently ignored due to incorrect YAML nesting. ([Link](https://github.com/nanocoai/nanoclaw/pull/3471))
- **PR #3463** — OpenCode provider now falls back to `message.part.delta` text, closing a ~78ms race condition that dropped assistant replies. ([Link](https://github.com/nanocoai/nanoclaw/pull/3463))
- **PR #2878** — Codex auth now properly rejects stale OpenAI secrets on reconnect instead of falsely succeeding. ([Link](https://github.com/nanocoai/nanoclaw/pull/2878))
- **PR #2865** — OpenCode now rotates stale sessions on ceiling-kill signals and age thresholds. ([Link](https://github.com/nanocoai/nanoclaw/pull/2865))

**Notable Open PRs advancing today:**

- **PRs #3581–#3588** — Six-part provider refactor by `zvi-fried` implementing codex/opencode contracts, runtime/host/setup contracts, and canon-based instruction rendering. ([#3581](https://github.com/nanocoai/nanoclaw/pull/3581), [#3584](https://github.com/nanocoai/nanoclaw/pull/3584), [#3585](https://github.com/nanocoai/nanoclaw/pull/3585), [#3586](https://github.com/nanocoai/nanoclaw/pull/3586), [#3588](https://github.com/nanocoai/nanoclaw/pull/3588), [#3591](https://github.com/nanocoai/nanoclaw/pull/3591))
- **PRs #3592–#3593** — Core-owned tone/speed inference properties and Codex mapping of personality/service tier. ([#3592](https://github.com/nanocoai/nanoclaw/pull/3592), [#3593](https://github.com/nanocoai/nanoclaw/pull/3593))
- **PR #3594** — Scheduled task errors now counted as FAILED runs instead of silently dropping. ([Link](https://github.com/nanocoai/nanoclaw/pull/3594))
- **PR #3595** — CLI cross-session status lookup for agents. ([Link](https://github.com/nanocoai/nanoclaw/pull/3595))
- **PR #3356** — Cursor Agent SDK payload added as a provider feature. ([Link](https://github.com/nanocoai/nanoclaw/pull/3356))
- **PR #2136** — Google Gemini provider support (long-open, still awaiting merge). ([Link](https://github.com/nanocoai/nanoclaw/pull/2136))

---

## 4. Community Hot Topics

| Issue | Author | Comments | Summary |
|-------|--------|----------|---------|
| [#3456](https://github.com/nanocoai/nanoclaw/issues/3456) — Discord approval buttons corrupt `custom_id` via redundant `value` param | DawoudIO | 5 | High-severity: approval cards unusable on Discord |
| [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) — Discord drops image/file attachments, agent sees only metadata | eagansilverpathmarketing | 2 | Long-standing attachment handling gap |
| [#3572](https://github.com/nanocoai/nanoclaw/issues/3572) — Inbound attachments silently dropped: adapters supply `url`, consumers require `fetchData` | BuckG71 | 2 | Direct root-cause follow-up to #2888 |
| [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) — `add-*-tool` per-agent scoping misses later-created agent groups | glifocat | 1 | Scoping inconsistency after group creation |
| [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) — `update-nanoclaw` skill overwrites local adapters | glifocat | 1 | Skill refresh logic lacks opt-out |

**Analysis:** The dominant theme is **adapter–consumer contract mismatch**. Issues #2888 and #3572 are two sides of the same bug: Discord adapters publish attachment URLs but downstream consumers expect `fetchData`. The approval-button regression (#3456) suggests a recent refactor introduced a parameter collision. Users are increasingly hitting friction with **custom adapter preservation during updates** (#3529, #3579), signaling a need for better skill-over-source attribution.

---

## 5. Bugs & Stability

### 🔴 Critical

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#3456](https://github.com/nanocoai/nanoclaw/issues/3456) | Discord approval/`ask_question` cards broken — every click resolves to wrong option due to redundant `value` param in button creation | None yet |
| [#3568](https://github.com/nanocoai/nanoclaw/issues/3568) | Pending `system` rows starve the inbound queue; agent silently stops responding after ~10 system messages | None yet |
| [#3575](https://github.com/nanocoai/nanoclaw/issues/3575) | One large WhatsApp photo (>2000px) wedges the entire SDK session until `/clear` | None yet |

### 🟠 High

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) / [#3572](https://github.com/nanocoai/nanoclaw/issues/3572) | Inbound attachments silently dropped — URL supplied but `fetchData` never called, no error emitted | None yet |
| [#3576](https://github.com/nanocoai/nanoclaw/issues/3576) | Rate-limited turns flood the channel with duplicate error notices — no backoff/dedup on `deliverErrorResult` | None yet |

### 🟡 Medium

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) | `add-*-tool` scoping misses agents created after the tool was scoped | None yet |
| [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | `update-nanoclaw` skill refresh overwrites or blocks local adapters | None yet |
| [#3579](https://github.com/nanocoai/nanoclaw/issues/3579) | Registry skills' `nc:copy` lists can drift from their source channels/providers | None yet |

**Three critical bugs with no fix PRs today** represent the most urgent stability risk. The session-starvation bug (#3568) and WhatsApp photo wedge (#3575) both cause complete agent unresponsiveness in production.

---

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood in Next Release |
|----------|-------------|---------------------------|
| [#3577](https://github.com/nanocoai/nanoclaw/issues/3577) | Auto-wire sole eligible agent group instead of prompting "Choose an agent" | **High** — low-effort UX win, already opened today |
| [#3575](https://github.com/nanocoai/nanoclaw/issues/3575) | Downscale inbound WhatsApp images to 2000px to prevent session wedging | **High** — labeled as `fix`, opened today |
| [#2136](https://github.com/nanocoai/nanoclaw/pull/2136) | Google Gemini provider support | **Medium** — open since April, architectural fit confirmed |
| [#1995](https://github.com/nanocoai/nanoclaw/pull/1995) | Custom OpenAI-compatible endpoint support + `/add-local-llama` skill | **Medium** — open since April, env-gated feature |
| [#3356](https://github.com/nanocoai/nanoclaw/pull/3356) | Cursor Agent SDK payload | **Medium** — open since Aug 19 |
| [#2872](https://github.com/nanocoai/nanoclaw/pull/2872) | Per-group model override via `container_configs.model` | **Medium** — open since June |

The provider refactor (PRs #3581–#3593) strongly signals the next release will unify the provider contract layer, likely consolidating codex/opencode/Cursor/Gemini under a single interface.

---

## 7. User Feedback Summary

- **Discord channel is the hardest-hit area.** Three separate issues (#3456, #2888, #3572) report broken approvals and dropped attachments — users on Discord are experiencing a degraded or non-functional agent interaction.
- **WhatsApp users report session-wedging from a single large image.** The current behavior (complete silence until `/clear`) is reported as production-impacting.
- **Skill/update friction is a recurring pain point.** Custom adapters are overwritten or blocked by `update-nanoclaw` (#3529), and registry skills can drift from source (#3579). Users building on top of NanoClaw feel the update path is not safe for modified installs.
- **Rate-limit error spam** (#3576) suggests production installations are hitting provider throttling frequently enough to warrant dedup logic.
- **Admin ergonomics:** The "choose an agent" prompt every time a new channel is created (#3577) is a low-severity but high-friction UX issue for single-group installs.

---

## 8. Backlog Watch

| Issue/PR | Open Since | Status | Why It Needs Attention |
|----------|-----------|--------|----------------------|
| [#2136](https://github.com/nanocoai/nanoclaw/pull/2136) — Google Gemini provider | 2026-04-29 | Open, no merge | 4-month backlog; first-class Gemini support is a major competitive feature |
| [#1995](https://github.com/nanocoai/nanoclaw/pull/1995) — Custom OpenAI-compat + local Llama skill | 2026-04-24 | Open, no merge | 4-month backlog; self-hosted deployment users depend on this |
| [#1994](https://github.com/nanocoai/nanoclaw/pull/1994) — Per-group custom endpoint routing | 2026-04-24 | Open, no merge | Blocks #1995 from being fully usable |
| [#2872](https://github.com/nanocoai/nanoclaw/pull/2872) — Per-group model override | 2026-06-27 | Open, no merge | 2-month backlog; pairs with the provider refactor |
| [#2878](https://github.com/nanocoai/nanoclaw/pull/2878) — Codex stale-secret reconnect fix | 2026-06-28 | Open, no merge | Auth reliability issue for production Codex users |
| [#3456](https://github.com/nanocoai/nanoclaw/issues/3456) — Discord button corruption | 2026-08-23 | Open, no fix PR | Critical bug, 5 comments, no assignee yet |

**Recommendation:** The five long-open PRs (#2136, #1995, #1994, #2872, #2878) represent the largest feature backlog. With the current provider refactor (PRs #3581–#3593) likely to reshape the same contract surface, maintainers should aim to land those refactors first and then rebase these PRs to avoid duplicate review cycles. The three critical unfixed bugs (#3456, #3568, #3575) should be prioritized in the next patch release regardless.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

⚠️ Summary generation failed.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-28

## 1. Today's Overview

LobsterAI shows **high commit velocity** with 12 PRs merged and 5 issues closed in the last 24 hours, indicating a strong release-candidate cadence. The recent 2026.8.26 release was followed by a rapid 2026.8.24 release branch polish, suggesting the team is actively stabilizing for an upcoming stable cut. Activity is heavily concentrated around renderer fixes, installer hardening, and test coverage — consistent with a pre-release polish phase. No new open issues or open PRs were reported in the last 24 hours, which is a positive signal for release readiness.

## 2. Releases

**LobsterAI 2026.8.26** — Published 2026-08-26

| Change | Detail |
|---|---|
| `fix(installer)` | Support silent upload-first web builds [#2511](https://github.com/netease-youdao/LobsterAI/pull/2511) |
| `fix(installer)` | Hide banner for dictbind silent package [#2512](https://github.com/netease-youdao/LobsterAI/pull/2512) |

**Notable follow-ups merged after release:**
- **#2572** — Release/2026.8.24 branch merge (renderer, build, docs, openclaw, cowork)
- **#2567** — Hotfixes for 2026.8.24 build

**Migration notes:** The silent-install behavior changes for upload-first web builds may affect enterprise deployment scripts relying on the previous banner display.

## 3. Project Progress

### Merged PRs (12 total today)

| PR | Area | Summary |
|---|---|---|
| [#2572](https://github.com/netease-youdao/LobsterAI/pull/2572) | renderer, build, docs, main, openclaw, cowork | Release/2026.8.24 final merge |
| [#2571](https://github.com/netease-youdao/LobsterAI/pull/2571) | renderer | Phone nickname fix |
| [#2570](https://github.com/netease-youdao/LobsterAI/pull/2570) | renderer | Resolve phone masking merge conflict; replace real test data with synthetic fixtures |
| [#2569](https://github.com/netease-youdao/LobsterAI/pull/2569) | renderer | Phone nickname fix (secondary) |
| [#2568](https://github.com/netease-youdao/LobsterAI/pull/2568) | renderer, docs, main | Collapse "More Models" section by default; sync sidebar banner schedules with server + client-version gating |
| [#2567](https://github.com/netease-youdao/LobsterAI/pull/2567) | renderer | 2026.8.24 hotfixes |
| [#2566](https://github.com/netease-youdao/LobsterAI/pull/2566) | build, windows | Win installer truncated payload hardening |
| [#2565](https://github.com/netease-youdao/LobsterAI/pull/2565) | renderer | Library list query state optimization — prevents flickering, duplicate skeletons, and stale result pollution |
| [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) | renderer, main | Preserve app ready state across update installs |
| [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) | scheduled tasks | "Run now" UX feedback with optimistic update + Gateway status sync |
| [#1165](https://github.com/netease-youdao/LobsterAI/pull/1165) | openclaw, tests | 75 Vitest unit tests for `openclawMemoryFile` and `openclawLocalTimeContextPrompt` |
| [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) | agent | Prevent duplicate custom agent names at creation |

**Key advances:**
- **Library list stability** (#2565) — significant UX improvement for users with large knowledge bases
- **Model collapse + banner scheduling** (#2568) — cleaner default UI, server-gated feature rollout
- **Installer hardening** (#2566, #2511, #2512) — focused on enterprise/silent deployment reliability

## 4. Community Hot Topics

### Top Issues by Activity

1. **[#1179](https://github.com/netease-youdao/LobsterAI/issues/1179)** — *How to disable mandatory sandbox in v3.31?* (3 comments, stale)
   - User cannot find a toggle to disable the sandbox introduced in v3.31; had to roll back to v3.30. Reflects strong dependency on sandbox flexibility for enterprise/custom deployment scenarios.

2. **[#1173](https://github.com/netease-youdao/LobsterAI/issues/1173)** — *Program still runs after uninstall* (2 comments, stale)
   - User reports LobsterAI continues running and can send messages to Feishu even after Windows uninstall. Raises trust/privacy concerns. Needs explicit process-kill-on-uninstall behavior.

3. **[#1162 / #1165](https://github.com/netease-youdao/LobsterAI/issues/1162)** — *Vitest unit tests for openclaw modules* (2 comments)
   - Community contributor (MaoQianTu) added 75 tests for memory and time-context modules. Strong signal of community investment in code quality.

4. **[#1174](https://github.com/netease-youdao/LobsterAI/issues/1174)** — *Support multiple custom model providers* (2 comments, stale)
   - Feature request to allow switching between multiple custom providers while retaining history. Indicates power users managing hybrid AI routing.

5. **[#1180](https://github.com/netease-youdao/LobsterAI/issues/1180)** — *Modifying custom agent icon triggers gateway restart loop* (2 comments, stale)
   - Bug in v2026.3.31 where icon edits cause gateway instability. Deleting the agent resolves it — points to a state-management edge case.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|---|---|---|---|
| **High** | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | Gateway restart loop on custom agent icon edit (v2026.3.31) | No fix PR yet |
| **High** | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | Process persists after Windows uninstall; can still send messages | No fix PR yet |
| **Medium** | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | No UI toggle to disable mandatory sandbox in v3.31 | Unknown — may require config-file workaround |
| **Low** | — | [#2566](https://github.com/netease-youdao/LobsterAI/pull/2566) — Win installer truncated payload | ✅ Merged (hardening fix) |
| **Low** | — | [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — App state loss during update | ✅ Merged |

**Stability assessment:** Two high-severity bugs remain open without merged fixes. The gateway restart loop (#1180) is the most impactful for agent-power users. The post-uninstall process issue (#1173) is both a functional and trust concern.

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for Next Release |
|---|---|---|
| Multiple custom model providers | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | **Medium** — explicitly requested; aligns with multi-provider trend |
| Disable sandbox mode | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | **High** — user demand is clear; likely a config flag or settings toggle |
| Library list state preservation | [#2565](https://github.com/netease-youdao/LobsterAI/pull/2565) | ✅ Already merged — will ship in next release |
| "More Models" collapse + banner scheduling | [#2568](https://github.com/netease-youdao/LobsterAI/pull/2568) | ✅ Already merged |
| Scheduled task "Run now" feedback | [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) | ✅ Already merged |
| Duplicate agent name prevention | [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) | ✅ Already merged |

**Signal:** The team is actively converting community feature requests into shipped items. The sandbox-disable request and multi-provider request are the two most user-visible gaps.

## 7. User Feedback Summary

- **Sandbox rigidity** (#1179): Users feel locked out of configuration options they previously had. Rolling back to v3.30 is the workaround — a retention risk.
- **Uninstall trust** (#1173): The post-uninstall process running and sending messages triggered a strong "backdoor" accusation. This is a **reputational risk** beyond a simple bug.
- **Agent name collisions** (#1166, fixed): Users previously had no guard against duplicates, causing confusion in the agent list.
- **Library list flicker** (fixed via #2565): Users experienced visual glitches when switching queries — now resolved with snapshot-based state tracking.
- **Scheduled task UX** (fixed via #1163): "Run now" had no feedback, leading to duplicate clicks. Optimistic update + Gateway sync now addresses this.
- **Overall sentiment**: Mixed. Bug fixes are landing quickly, but two high-severity issues (sandbox, uninstall) remain unresolved and are eroding trust among power users.

## 8. Backlog Watch

| Issue | Age | Priority | Reason for Attention |
|---|---|---|---|
| [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | ~5 months (stale) | **Critical** | Post-uninstall process persistence; trust/privacy issue with no fix |
| [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | ~5 months (stale) | **High** | No sandbox disable path; users forced to downgrade |
| [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | ~5 months (stale) | **High** | Gateway restart loop on agent icon edit; no fix PR |
| [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | ~5 months (stale) | **Medium** | Multi-provider feature request; no implementation started |

**Recommendation:** Issues #1173, #1179, and #1180 have been stale since March 2026 with no resolved state. Given their severity and the active release cadence, these should be prioritized for the next patch cycle to prevent further community trust erosion.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-28

## 1. Today's Overview
Moltis showed focused maintenance activity with **2 merged/closed PRs** and **0 new issues** in the last 24 hours. No new releases were published, indicating the project is in a stabilization phase rather than a feature-release cycle. Activity centers on correctness and compatibility fixes (sandbox validation, OpenAI schema alignment) rather than new functionality. The issue tracker is currently quiet, suggesting no urgent community-reported problems.

## 2. Releases
*No new releases were published in the last 24 hours.*

## 3. Project Progress
Two PRs were closed/merged today, both addressing correctness and compatibility:
- **#1222** – `[fix(web)] validate sandbox image requests` – Enforces validation of image references and package names before container/Dockerfile use, restricts package checks and image builds to operator administrators, and preserves full administrative access for password, passkey, and trusted loopback identities.
- **#1232** – `[fix(tools)] make object schemas OpenAI-safe` – Patches OpenAI strict tool schemas that set `additionalProperties=false`, which previously forced Codex to send null/empty values for unspecified patch and map schemas. The fix declares webhook patch fields explicitly and represents MCP environment variables as fixed name/value entries.

## 4. Community Hot Topics
*No high‑engagement issues or PRs were recorded today.*  
Both merged PRs had zero comments and zero reactions, indicating low community visibility or that the fixes were straightforward and uncontroversial. No open issues are currently drawing discussion.

## 5. Bugs & Stability
Two bug‑fix PRs landed today; no new crash or regression reports were opened:
1. **#1222** – *High severity* – Unvalidated sandbox image requests could lead to insecure container builds or unauthorized package operations. **Fix merged.**
2. **#1232** – *Medium severity* – OpenAI‑strict schemas caused Codex to drop requested data (null/empty values), breaking patch and map schema round‑tripping. **Fix merged.**

## 6. Feature Requests & Roadmap Signals
*No new feature requests or enhancement issues were filed today.* The current activity is entirely remedial, suggesting the project is prioritizing stability and compatibility over new features in this sprint.

## 7. User Feedback Summary
User pain points addressed today (inferred from PR descriptions):
- **Security/validation concerns** around sandbox image and package references (#1222).
- **Tool‑schema compatibility** with OpenAI/Codex, where strict `additionalProperties=false` broke expected data flow (#1232).

No explicit user satisfaction/dissatisfaction signals were captured due to zero new issues or comments.

## 8. Backlog Watch
*No open issues require immediate maintainer attention.*  
The issue tracker is clear, and no long‑unanswered PRs or bugs were flagged in the last 24 hours.

---
**GitHub Links**  
- PR #1222: `moltis-org/moltis#1222`  
- PR #1232: `moltis-org/moltis#1232`

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw (QwenPaw) Project Digest — 2026-08-28

## 1. Today's Overview

CoPaw is experiencing high development velocity with **49 issues** and **47 PRs** updated in the last 24 hours. The project released **v2.2.0-beta.2** today and closed **33 issues** alongside **19 merged/closed PRs**, indicating strong maintenance throughput. Core infrastructure improvements dominate today's activity, including a Python 3.13 TLS stack upgrade, deferred startup architecture, and MCP protocol hardening. Community engagement is active around the upcoming multi-tenant Hub release and mobile experience exploration.

---

## 2. Releases

### v2.2.0-beta.2
**What's Changed:**
- **[fix]** Workspace startup failure cleanup is now cancellation-safe — prevents resource leaks when initialization is aborted mid-way ([#7194](https://github.com/agentscope-ai/QwenPaw/pull/7194))
- **[test]** E2E console coverage boosted with 23 targeted cases and extended assertions ([#7327](https://github.com/agentscope-ai/QwenPaw/pull/7327))

**Notes:** No breaking changes reported. This is a beta release focused on stability and test coverage.

---

## 3. Project Progress

**Merged/Closed Today:**

| PR | Type | Summary |
|----|------|---------|
| [#7384](https://github.com/agentscope-ai/QwenPaw/pull/7384) | `perf(app)` | Shared A-tier deferred startup architecture — reduces Desktop/Tauri startup latency by exposing health checks before full Python import completes |
| [#7328](https://github.com/agentscope-ai/QwenPaw/pull/7328) | `fix(ci)` | Bumped bundled Python from 3.11 → 3.13 across all desktop and Docker pipelines, resolving the OpenSSL 3.0.x carrier DPI issue ([#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298)) |
| [#7299](https://github.com/agentscope-ai/QwenPaw/pull/7299) | `fix(console)` | Rejects conflicting chat payloads — prevents silent message loss when a second non-reconnect `POST /api/console/chat` arrives during an active run |

**Notable Open PRs Advancing:**
- [#7329](https://github.com/agentscope-ai/QwenPaw/pull/7329) — Abort hung MCP session RPCs on teardown, recover stale `list_tools`
- [#7330](https://github.com/agentscope-ai/QwenPaw/pull/7330) — Dual-protocol Streamable-HTTP MCP client with legacy fallback
- [#7383](https://github.com/agentscope-ai/QwenPaw/pull/7383) — Avoid full `sys.modules` sweep after each plugin load (Windows startup perf)
- [#7378](https://github.com/agentscope-ai/QwenPaw/pull/7378) — **Draft:** Native mobile experience via Expo/React Native (Android + iOS)
- [#7331](https://github.com/agentscope-ai/QwenPaw/pull/7331) — Bound oversized single-line tool results to prevent context bloat

---

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | QwenPaw Hub multi-tenant edition: what should we build next? | 10 | [link](https://github.com/agentscope-ai/QwenPaw/issues/7318) |
| [#6314](https://github.com/agentscope-ai/QwenPaw/issues/6314) | RemoteProtocolError: peer closed connection without complete body | 9 | [link](https://github.com/agentscope-ai/QwenPaw/issues/6314) |
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | Desktop/Docker ship OpenSSL 3.0.x TLS — carrier DPI resets handshakes | 8 | [link](https://github.com/agentscope-ai/QwenPaw/issues/7298) |
| [#2814](https://github.com/agentscope-ai/QwenPaw/issues/2814) | Multi-agent chat history empty for running callee agent | 7 | [link](https://github.com/agentscope-ai/QwenPaw/issues/2814) |
| [#4770](https://github.com/agentscope-ai/QwenPaw/issues/4770) | Left sidebar column reorder — move time column leftward | 6 | [link](https://github.com/agentscope-ai/QwenPaw/issues/4770) |

**Analysis:** The #7318 discussion reflects strong community demand for team/multi-tenant capabilities — a clear signal that QwenPaw is outgrowing its single-user origins. The OpenSSL/TLS issue (#7298) has been addressed by the Python 3.13 bump (PR #7328). The empty chat history bug (#2814) and sidebar UX request (#4770) point to ongoing polish needs in multi-agent flows and the console UI.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR | Link |
|----------|-------|-------------|--------|------|
| 🔴 High | [#7379](https://github.com/agentscope-ai/QwenPaw/issues/7379) | Processing PDFs with long Chinese filenames fails — `No connection adapters found` | None yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/7379) |
| 🔴 High | [#7296](https://github.com/agentscope-ai/QwenPaw/issues/7296) | OpenAI Responses multi-turn fails with 400 "Referenced reasoning item not found" on stateless upstreams | None yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/7296) |
| 🟡 Medium | [#6314](https://github.com/agentscope-ai/QwenPaw/issues/6314) | `RemoteProtocolError` — QwenPaw主动 closes connection to LLM | None yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6314) |
| 🟡 Medium | [#6427](https://github.com/agentscope-ai/QwenPaw/issues/6427) | WebView2 renderer crash ~7s after startup on v2.0.0+post.4 (deterministic assertion failure) | None yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6427) |
| 🟡 Medium | [#6124](https://github.com/agentscope-ai/QwenPaw/issues/6124) | Editable install memory leak — 36 ReMe background loops consume 48GB+ at startup | None yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6124) |
| 🟢 Low | [#5344](https://github.com/agentscope-ai/QwenPaw/issues/5344) | `/api/console/chat` returns 200 but silently drops messages when agent is busy | Closed (PR #7299) | [link](https://github.com/agentscope-ai/QwenPaw/issues/5344) |
| 🟢 Low | [#4217](https://github.com/agentscope-ai/QwenPaw/issues/4217) | Concurrent cron tasks with `share_session=true` produce empty replies | Closed | [link](https://github.com/agentscope-ai/QwenPaw/issues/4217) |

**Key takeaway:** The v2.0.0+post.4 → post.5 regression window (WebView2 crash, #6427) needs investigation. The memory leak in editable installs (#6124) affects developers but not shipped bundles. The new Chinese-filename PDF bug (#7379) surfaced today and should be prioritized.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Votes/Comments | Likelihood |
|---------|----------|----------------|------------|
| **Multi-tenant Hub** | [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | 10 comments, 1 👍 | ✅ Confirmed for 2.2.0 |
| **Per-session model overrides** | [#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) | Open, under review | 🟡 Likely in 2.2.x |
| **Workspace-scoped skill preload** | [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | Open, first-time contributor | 🟡 Possible |
| **Native mobile app (React Native)** | [#7378](https://github.com/agentscope-ai/QwenPaw/pull/7378) | Draft, by core maintainer | 🟡 Exploration phase |
| **Auto model switch on failure** | [#5718](https://github.com/agentscope-ai/QwenPaw/issues/5718) | 3 comments | 🟡 Low priority |
| **In-chat shell command observability** | [#4237](https://github.com/agentscope-ai/QwenPaw/issues/4237) | 5 comments | 🟡 Future |
| **Prompt cache hit rate observability** | [#7335](https://github.com/agentscope-ai/QwenPaw/issues/7335) | 3 comments, shows 81% vs 96% OpenCode gap | 🟡 Niche |
| **Fallback model configuration** | [#4011](https://github.com/agentscope-ai/QwenPaw/issues/4011) | 4 comments | 🟡 Low priority |

**Roadmap prediction:** v2.2.0 will ship the multi-tenant Hub and deferred startup architecture. Per-session model overrides and the mobile app are the next most likely candidates for 2.2.x or 2.3.0.

---

## 7. User Feedback Summary

**Pain Points:**
- **Mobile/browser input UX** — Android Chrome input fields don't support newline (Enter submits instead) ([#7355](https://github.com/agentscope-ai/QwenPaw/issues/7355)); attachment icon only visible in landscape
- **File access friction** — Desktop users must leave the app to browse workspace output files; request for quick-access buttons in-console ([#6083](https://github.com/agentscope-ai/QwenPaw/issues/6083))
- **Chat history sort order** — Users expect last-active-time sorting; current order is considered "反人类" (unintuitive) compared to WorkBuddy, Trae, Doubao ([#4817](https://github.com/agentscope-ai/QwenPaw/issues/4817), [#4770](https://github.com/agentscope-ai/QwenPaw/issues/4770))
- **Real-time shell feedback** — Long-running shell commands show no progress; users can't distinguish "still generating" from "hung" ([#4986](https://github.com/agentscope-ai/QwenPaw/issues/4986), [#4865](https://github.com/agentscope-ai/QwenPaw/issues/4865))
- **Deployment upgrade transparency** — Platform upgrade flow is opaque; users can't see available versions ([#7366](https://github.com/agentscope-ai/QwenPaw/issues/7366))

**Satisfaction Signals:**
- Active community participation in design discussions (#7318)
- First-time contributors actively submitting PRs (MCP protocol, skills preload)
- High issue closure rate (33 closed in 24h) shows responsive maintenance

---

## 8. Backlog Watch

| Issue | Age | Comments | Status | Risk |
|-------|-----|----------|--------|------|
| [#2777](https://github.com/agentscope-ai/QwenPaw/issues/2777) | Apr 2026 | 5 | Closed | GPT-5.x `max_tokens` incompatibility — resolved but highlights hardcoded model list fragility |
| [#3014](https://github.com/agentscope-ai/QwenPaw/issues/3014) | Apr 2026 | 2 | Closed | Isolated/cron sessions with custom session — unimplemented |
| [#3187](https://github.com/agentscope-ai/QwenPaw/issues/3187) | Apr 2026 | 2 | Closed | Conversation archiving feature — unimplemented |
| [#3751](https://github.com/agentscope-ai/QwenPaw/issues/3751) | Apr 2026 | 4 | Closed | Windows system tray support — duplicate of [#5622](https://github.com/agentscope-ai/QwenPaw/issues/5622), both closed but feature still absent |
| [#6124](https://github.com/agentscope-ai/QwenPaw/issues/6124) | Jul 2026 | 3 | Open | Editable install memory leak (48GB+) — affects developers, blocked by ReMe version pinning |
| [#6427](https://github.com/agentscope-ai/QwenPaw/issues/6427) | Jul 2026 | 3 | Open | WebView2 deterministic crash on v2.0.0+post.4 — regression needs root-cause analysis |

**Maintainer attention needed:** #6427 (regression), #6124

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-28

## 1. Today's Overview

ZeroClaw is in an active stabilization phase heading toward the **v0.8.5 finite weekly cut** (tracker [#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459), intake froze Aug 4). The project saw **23 issues** and **50 PRs** updated in the last 24h, with 21 open/active issues and 47 open PRs — a strong signal of healthy contributor momentum. The day's activity is dominated by two themes: (1) **architectural RFCs around session ownership, transport adapters, and the internal-principal envelope** (Issues [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487), [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954), [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600)) and (2) a cluster of **S2-severity runtime bugs** touching session concurrency, Telegram history keying, and ZeroCode transcript restoration. No new releases shipped today.

---

## 2. Releases

*No new releases today.* The v0.8.5 stabilization line (tracker [#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459)) targets a weekly cut with items ready as of August 30, 2026. Maintainers have chosen to ship incremental work rather than wait for every milestone to land.

---

## 3. Project Progress

**Merged / closed today (3 PRs):**

| PR | Summary |
|---|---|
| [#10329](https://github.com/zeroclaw-labs/zeroclaw/pull/10329) | Closed as a bug — resilient wrapper truncation shadowing loop-level overflow recovery for OpenAI-compatible providers (see §5). |
| [#10343](https://github.com/zeroclaw-labs/zeroclaw/pull/10343) | Closed — dependabot rust-all bump (47 updates). |
| [#10306](https://github.com/zeroclaw-labs/zeroclaw/issues/10306) | Task accepted — TypeScript typecheck gate for `web/` in required CI (not yet merged; tracked as an open task). |

**Notable PRs advancing today:**

- **[PR #10425](https://github.com/zeroclaw-labs/zeroclaw/pull/10425)** — `feat(runtime): internal-principal envelope and separated cron run outcomes (RFC #6954, 1/3)`. First slice of the accepted RFC: introduces `InternalPrincipal` (`Cron { job_id, job_name }` | `PeerAgent { sender_alias }` | `Daemon`) as a shared primitive with **no behavior change** — purely mechanical, per the RFC's implementation-slicing section.
- **[PR #10412](https://github.com/zeroclaw-labs/zeroclaw/pull/10412)** — `feat(session): extract the atomic session-ownership claim into a shared SessionBackend contract`. Introduces `SessionBackend::claim_session_agent_alias` returning `ClaimOutcome` (`Claimed` / `Conflict(String)` / `NeedsMigration`). The compare-and-set is performed inside the backend's own lock to prevent concurrent callers from competing.
- **[PR #10214](https://github.com/zeroclaw-labs/zeroclaw/pull/10214)** — `feat(log): add entry-count rotation and multi-segment log queries`. New config `log_persistence_max_entries_per_segment` triggers time-based rotation when line count reaches the cap.
- **[PR #9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809)** — `feat(providers): support multiple models per provider profile`. One credential + endpoint can now host multiple models via a `[providers.models.<family>.<alias>.models.<model_alias>]` subtable.
- **[PR #9819](https://github.com/zeroclaw-labs/zeroclaw/pull/9819)** — `fix(multimodal): pixel-level image validation`. New `validate_image_content()` fully decodes images with the `image` crate to prove well-formedness before sending to providers.
- **[PR #9324](https://github.com/zeroclaw-labs/zeroclaw/pull/9324)** — `feat(a2a): outbound client config, shared wire-model, tools (#9106)`. Phase 1 of A2A outbound client RFC: four `a2a_*` tools, shared A2A v1.0 wire model in `zeroclaw-api`.

---

## 4. Community Hot Topics

| Topic | Link | Signals |
|---|---|---|
| **Runtime-owned conversation sessions + transport surface adapters** | [Issue #9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 27 comments, Revision 2 (Aug 3), RFC type, p2/high risk |
| **Unified attachment architecture for web chat & channels** | [Issue #9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 21 comments, Revision 9, RFC type, p2/high risk |
| **Provenance & reply contract for internally-initiated agent turns** | [Issue #6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | 16 comments, Revision 2 (Aug 5), RFC type, accepted |
| **Maintainer decision queue for RFCs & design issues** | [Issue #8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 14 comments, tracker type, accepted |
| **Session-persistence contract ownership & layer ordering** | [Issue #9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) | 14 comments, tracker type |
| **Composable WASM plugin runtime architecture** | [Issue #10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | 4 comments, RFC type, p2/high risk |
| **Wire protocol as first-class in provider onboarding** | [Issue #8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | 15 comments, RFC type, p2/high risk |

**Analysis:** The community is heavily focused on **ownership boundaries** — who owns sessions, who owns the transport layer, and how internally-initiated turns (cron, peer agents, daemon) are distinguished from user-originated ones. The RFC process is mature: issues #9487 and #9488 are on revisions 2 and 9 respectively, with cross-referencing (e.g., #9487/#9488/#9600 ownership boundary ratification). The high comment counts (14–27) indicate active, sustained design debate rather than noise. The WASM plugin RFC (#10076) signals a growing desire to extend the sandboxed runtime beyond the current narrow surface.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|---|---|---|---|
| **S1** | [#10063](https://github.com/zeroclaw-labs/zeroclaw/issues/10063) | Anthropic-backed compatible gateways reject `image_url` blocks inside tool results | — (open, follow-up) |
| **S2** | [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | Second message during an active turn starts a parallel run → duplicate work & reply | — (open) |
| **S2** | [#10324](https://github.com/zeroclaw-labs/zeroclaw/issues/10324) | Cron manual trigger & run-history reads are check-then-act across an agent rename | — (open, accepted, follow-up) |
| **S2** | [#10286](https://github.com/zeroclaw-labs/zeroclaw/issues/10286) | Restored ZeroCode transcripts omit persisted turns after history trimming | — (open, in-progress, follow-up) |
| **S2** | [#10237](https://github.com/zeroclaw-labs/zeroclaw/issues/10237) | Telegram reply-threads fragment conversation memory into per-thread history buckets | — (open) |
| **S2** | [#10186](https://github.com/zeroclaw-labs/zeroclaw/issues/10186) | Terminal fallback text bypasses live delivery seams | — (open, follow-up) |
| **S3** | [#10326](https://github.com/zeroclaw-labs/zeroclaw/issues/10326) | Reliable streaming errors report requested model instead of served pinned model | — (open, accepted, follow-up) |
| **Closed** | [#10329](https://github.com/zeroclaw-labs/zeroclaw/issues/10329) | Resilient wrapper truncation shadows loop-level context overflow recovery | Closed today |

**Analysis:** 7 of 8 open bugs are S2, concentrated in **runtime/daemon** and **channels**. The most operationally impactful is [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) (duplicate parallel runs on concurrent messages), which directly affects multi-turn user experience. The S1 bug [#10063](https://github.com/zeroclaw-labs/zeroclaw/issues/10063) (tool-result images rejected by Anthropic-compatible gateways) is a workflow-blocker for multimodal use cases. No fix PRs are yet linked for the top-priority open bugs.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Type | Summary |
|---|---|---|
| [#10419](https://github.com/zeroclaw-labs/zeroclaw/issues/10419) | Enhancement | Stream agent-loop tokens from `POST /webhook` via SSE |
| [#10422](https://github.com/zeroclaw-labs/zeroclaw/issues/10422) | Enhancement | Run SOP as heartbeat (`heartbeat.sop` config) |
| [#10421](https://github.com/zeroclaw-labs/zeroclaw/issues/10421) | Enhancement | Paginate persisted ACP transcript restoration in ZeroCode |
| [#10244](https://github.com/zeroclaw-labs/zeroclaw/issues/10244) | Enhancement | Add agent deletion & bulk cleanup to ZeroCode (in-progress) |
| [#10405](https://github.com/zeroclaw-labs/zeroclaw/issues/10405) | Tracker | Implement session-scoped prompt attachments (#9998) — accepted, coordination home |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | RFC | Composable WASM plugin runtime — core APIs, typed extension points |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | RFC | Make wire protocol first-class in provider construction |
| [#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459) | Tracker | v0.8.5 finite weekly stabilization line |

**Prediction for next version:** Session-scoped prompt attachments (#10405 / #9998) and agent deletion ( [#10244](https://github.com/zeroclaw-labs/zeroclaw/issues/10244)) are both **accepted** and have active trackers or in-progress PRs — high likelihood for v0.8.5. The SSE streaming feature (#10419) and paginated transcript restoration (#10421) are fresh (created Aug 28) with no PRs yet, making them less likely for the immediate cut. The WASM plugin RFC (#10076) is early-stage (4 comments) and will span multiple versions.

---

## 7. User Feedback Summary

**Pain points surfaced this cycle:**

1. **Concurrent message handling** — [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408): Users sending a second message during an active turn get duplicate parallel runs and duplicate replies. This is a UX breaker for fast-typing users and channel-based workflows.
2. **Telegram history fragmentation** — [#10237](https://github.com/zeroclaw-labs/zeroclaw/issues/10237): Telegram reply-threads create separate history buckets, losing multi-turn context across threads within the same session.
3. **Image support gaps** — [#10063](https://github.com/zeroclaw-labs/zeroclaw/issues/10063): Tool results containing images are rejected by Anthropic-compatible gateways, blocking multimodal agent workflows that rely on tool-return vision.
4. **ZeroCode transcript incompleteness** — [#10286](https://github.com/zeroclaw-labs/zeroclaw/issues/10286): After history trimming, restored transcripts omit previously persisted turns, making debugging and audit trails unreliable.
5. **Cron rename race** — [#10324](https://github.com/zeroclaw-labs/zeroclaw/issues/10324): Manual cron triggers and run-history reads are check-then-act across agent renames, creating a narrow window for incorrect attribution.

**Positive signals:** The RFC process is working well — proposals like #9487 and #9488 have sustained, revision-driven discussions with clear ownership. The `InternalPrincipal` envelope (PR #10425) addresses a long-standing ambiguity in turn provenance. The multi-model-per-provider feature (#9809) and pixel-level image validation (#9819) show responsive engineering to real user configurations.

---

## 8. Backlog Watch

| Issue | Age | Why it needs attention |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | ~31 days | RFC Revision 2; gate for session ownership architecture. 27 comments, needs-maintainer-review. |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | ~31 days | RFC Revision 9; unified attachment architecture. 21 comments, needs-maintainer-review. |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | ~62 days | RFC on wire protocol first-class status. 15 comments, needs-maintainer-review. |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | ~10 days | WASM plugin runtime RFC. 4 comments, needs-maintainer-review. |
| [#10063](https://github.com/zeroclaw-labs/zeroclaw/issues/10063) | ~11 days | S1 bug — tool-result images rejected. No fix PR yet. |
| [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | ~1 day | S2 bug — duplicate parallel runs. Critical UX impact, no fix PR. |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | ~55 days | Maintainer decision queue tracker. 14 comments, accepted but no visible progression. |

**Recommendation:** Issues #9487 and #9488 have been in RFC review for ~31 days with high comment counts and `needs-maintainer-review` tags. A maintainer synthesis or ratification decision would unblock multiple downstream workstreams (including the session-ownership tracker #9600). The S1 bug #10063 and the S2 bug #10408 lack fix PRs and should be prioritized for the v0.8.5 cut given their operational impact.

---

*Digest generated from ZeroClaw GitHub data on 2026-08-28. All links reference `github.com/zeroclaw-labs/zeroclaw`.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*