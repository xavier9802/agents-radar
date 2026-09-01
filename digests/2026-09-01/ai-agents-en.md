# OpenClaw Ecosystem Digest 2026-09-01

> Issues: 480 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-01 04:39 UTC

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



# OpenClaw Project Digest — 2026-09-01

---

## 1. Today's Overview

OpenClaw saw **very high activity** today with 480 issues and 500 PRs updated in the last 24 hours. Of those, 254 issues and 197 PRs were closed/merged, indicating a strong cleanup and resolution pass. No new releases were published, but a significant volume of maintenance work landed — including a major gateway-level conversation-delivery fix (PR #126424) that addresses multi-agent operator concerns. The project is in an active hardening phase, with heavy focus on migration robustness, cron reliability, and platform-UX polish.

---

## 2. Releases

*No new releases published today.*

---

## 3. Project Progress

### Key Merged/Closed PRs

| PR | Description | Impact |
|---|---|---|
| [#123535](https://github.com/openclaw/openclaw/pull/123535) | **UI** — Session catalog refresh storms avoided | Fixes redundant full-refresh triggers on browser focus/presence changes |
| [#128223](https://github.com/openclaw/openclaw/pull/128223) | **CLI** — Resolve alias targets from the write snapshot | Fixes `openclaw models aliases add` resolving stale targets (Closes #127618) |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | **Gateway** — Keep conversation delivery within agent bindings | **Major**: prevents multi-agent operators from inadvertently delivering across agent boundaries; spans 8+ channels (Discord, Telegram, Slack, iMessage, Matrix, Mattermost, Feishu, WhatsApp) |
| [#123975](https://github.com/openclaw/openclaw/pull/123975) | **Scripts** — Clean up tsgo process trees on timeout/signal | Prevents wedged compiler processes from accumulating; adds `OPENCLAW_TSGO_TIMEOUT_MS` watchdog |

### Notable Open PRs Awaiting Review

| PR | Description | Risk/Notes |
|---|---|---|
| [#134803](https://github.com/openclaw/openclaw/pull/134803) | Show Claude compaction progress for Telegram users | Fixes "no progress" UX during compaction burst |
| [#134758](https://github.com/openclaw/openclaw/pull/134758) | Persist doctor migrations for explicit agent rosters | Follow-up to upgrade-brick bug (#133984) |
| [#134303](https://github.com/openclaw/openclaw/pull/134303) | macOS: Preserve config on Browser Control changes | Fixes data-integrity issue where toggling could delete unrelated settings |
| [#127999](https://github.com/openclaw/openclaw/pull/127999) | Cron: Refuse doctor store rewrites when another process committed | Prevents silent job loss from stale doctor snapshots |
| [#131590](https://github.com/openclaw/openclaw/pull/131590) | Cron: Make one-shot terminal disables visible | Fixes silent job parking after permanent errors |
| [#134589](https://github.com/openclaw/openclaw/pull/134589) | Cron: Run one-shot main-session jobs even when heartbeat is disabled | Fixes deterministic skip bug (#134500) |
| [#129825](https://github.com/openclaw/openclaw/pull/129825) | Doctor: Report lossy WhatsApp ack-scope migration | Documents destructive scope change in #112796 |

---

## 4. Community Hot Topics

### Top Issues by Comment Count

1. **[Security] `gh-issues` skill injects raw issue bodies into sub-agent prompts** — [#45740](https://github.com/openclaw/openclaw/issues/45740) (17 comments, 🐚 platinum hermit)
   - *Analysis*: A critical sanitization gap. Issue bodies are injected directly into sub-agent prompts without filtering. High-severity security concern for any user running the `gh-issues` skill.

2. **[WhatsApp] Inbound image wedges main lane ~3 min before processing** — [#96834](https://github.com/openclaw/openclaw/issues/96834) (14 comments, 🦞 diamond lobster)
   - *Analysis*: Multimodal WhatsApp users experience a ~3-minute stall. Affects the `active_reply_work/queued_work_without_active_run` state machine. Root cause tied to native multimodal image injection.

3. **[MCP] Tools not injected into subagent sessions** — [#85030](https://github.com/openclaw/openclaw/issues/85030) (12 comments, 🦞 diamond lobster, 6 👍)
   - *Analysis*: `mcp.servers` registered tools are ignored by `sessions_spawn`. All three documented exposure mechanisms (`bundle-mcp`, per-tool allowlist, per-agent allowlist) are broken. Strong community signal (6 thumbs-up) for a fundamental subagent/MCP integration flaw.

4. **[Feature] Built-in headless Chromium** — [#53763](https://github.com/openclaw/openclaw/issues/53763) (10 comments, 🌊 off-meta tidepool)
   - *Analysis*: Users want a bundled Chromium to avoid fragile web-access layering (external Chrome dependency + third-party APIs). Signals demand for self-contained agent web capabilities.

5. **[Bug] Child process leak causing zombie accumulation** — [#97636](https://github.com/openclaw/openclaw/issues/97636) (10 comments, 🦐 gold shrimp)
   - *Analysis*: Hook/tool child processes (`openclaw-hooks`, `bash`, `codex`, occa) are not reaped, causing runtime degradation over time. A regression with production impact.

### Top Open PRs by Discussion

- [#134803](https://github.com/openclaw/openclaw/pull/134803) — Telegram Claude compaction UX fix
- [#127999](https://github.com/openclaw/openclaw/pull/127999) — Cron doctor race-condition guard (high merge-risk)

---

## 5. Bugs & Stability

### P0 / Critical

| Issue | Summary | Status | Fix PR |
|---|---|---|---|
| [#107133](https://github.com/openclaw/openclaw/issues/107133) | Memory Core `embedding_cache` conflict permanently blocks Gateway startup on 2026.7.1 | ✅ Closed | — |
| [#102749](https://github.com/openclaw/openclaw/issues/102749) | Startup legacy-state migration never converges when `.migrated` archive exists | ✅ Closed | — |
| [#133813](https://github.com/openclaw/openclaw/issues/133813) | 2026.8.1 upgrade crash-loops Gateway; `doctor --fix` blocked by `ExecApprovalsMigrationRequiredError` | ✅ Closed | — |

### P1 High-Severity

| Issue | Summary | Status | Fix PR |
|---|---|---|---|
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | Untrusted issue body injected into sub-agent prompt (security) | 🟡 Open | — |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | WhatsApp image wedges main lane ~3 min | 🟡 Open | — |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | MCP tools not injected into subagent sessions | 🟡 Open | — |
| [#97636](https://github.com/openclaw/openclaw/issues/97636) | Child process leak → zombie accumulation | 🟡 Open | — |
| [#126360](https://github.com/openclaw/openclaw/issues/126360) | `AgentSelectionRequiredError` floods logs in explicit multi-agent mode | 🟡 Open | — |
| [#91804](https://github.com/openclaw/openclaw/issues/91804) | Internal reasoning/thinking content leaks to users (regression in 2026.6.5) | 🟡 Open | — |
| [#115424](https://github.com/openclaw/openclaw/issues/115424) | Gateway V8 heap OOM → restart-recovery converts one crash into a 7-core-dump loop | 🟡 Open | — |
| [#102006](https://github.com/openclaw/openclaw/issues/102006) | Aborted `exec` run wedges subsequent exec calls in same session (regression from PR #94412) | ✅ Closed | — |
| [#133347](https://github.com/openclaw/openclaw/issues/133347) | 2026.8.1 migration quarantines valid cron jobs as `invalid-schedule`, silently drops inventory | ✅ Closed | — |
| [#134445](https://github.com/openclaw/openclaw/issues/134445) | `doctor --fix` never completes legacy workspace migration with zero-byte attestation file | ✅ Closed | — |
| [#124343](https://github.com/openclaw/openclaw/issues/124343) | `yield-owned` settle-wake parks completed subagent forever — no delivery, no retry | 🟡 Open | — |
| [#120162](https://github.com/openclaw/openclaw/issues/120162) | Safeguard compaction: `qualityGuard` audit retry shares timeout and is killed by same abort signal | 🟡 Open | — |
| [#134307](https://github.com/openclaw/openclaw/issues/134307) | `auth: "oauth"` MCP servers absent from tool catalog on `claude-cli` runtime turns | ✅ Closed | — |

### Notable Regressions

- **#91804** — Thinking/reasoning content now visible to users since 2026.6.5 (privacy + UX regression)
- **#102006** (closed) — `exec` tool wedge after aborted run (regression from PR #94412)
- **#133347** (closed) — Cron migration in 2026.8.1 silently drops valid jobs
- **#133813** (closed) — 2026.8.1 upgrade bricks Gateway startup

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Community Signal | Likelihood |
|---|---|---|---|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built-in headless Chromium for reliable web access | 10 comments | **Medium** — significant scope; addresses a well-known fragility |
| [#74594](https://github.com/openclaw/openclaw/issues/74594) | RFC: Skill Capability Manifests v0 | 7 comments | **Medium** — transparency-focused; low implementation risk |
| [#79170](https://github.com/openclaw/openclaw/issues/79170) | Post-update hook system | 7 comments, ✅ Closed | — |
| [#43564](https://github.com/openclaw/openclaw/issues/43564) | ACP Session Skill Context Injection | 7 comments | **Low-Medium** — niche (ACP/Codex users) |
| [#46656](https://github.com/openclaw/openclaw/issues/46656) | Webchat / Control UI inline button support | 8 comments, ✅ Closed | — |
| [#77886](https://github.com/openclaw/openclaw/issues/77886) | Owner-approved flow for protected config changes | 6 comments, 2 👍 | **Medium** — security posture improvement |
| [#80674](https://github.com/openclaw/openclaw/issues/80674) | Polling lifecycle + session persistence hook events for plugins | 5 comments | **Low** — plugin authoring DX |
| [#71216](https://github.com/openclaw/openclaw/issues/71216) | Config schema additions: `sandbox`, `routing.rules`, `instances`, `denyPaths` | 5 comments | **Medium** — operational maturity |

**Prediction**: The next release cycle will likely prioritize **MCP subagent injection** (issue #85030 is a blocker for multi-agent power users) and **compaction/timeout sharing** (issue #120162). Skill manifests (#74594) may land as a lightweight RFC before full implementation.

---

## 7. User Feedback Summary

### Pain Points
- **Migration fragility**: Multiple users reported that upgrades to 2026.8.xbrick gateways, silently drop cron jobs, or produce contradictory error messages from `doctor --fix`. The upgrade path is a significant trust issue. ([#133813](https://github.com/openclaw/openclaw/issues/133813), [#133347](https://github.com/openclaw/openclaw/issues/133347), [#134445](https://github.com/openclaw/openclaw/issues/134445), [#133999](https://github.com/openclaw/openclaw/issues/133999), [#134758](https://github.com/openclaw/openclaw/pull/134758))
- **WhatsApp experience**: Images wedge the main lane for ~3 minutes; ack-scope migrations are lossy and under-reported. ([#96834](https://github.com/openclaw/openclaw/issues/96834), [#129825](https://github.com/openclaw/openclaw/pull/129825))
- **Multi-agent operational friction**: `AgentSelectionRequiredError` log floods, MCP tools not propagating to subagents, conversation delivery crossing agent boundaries. ([#126360](https://github.com/openclaw/openclaw/issues/126360), [#85030](https://github.com/openclaw/openclaw/issues/85030), [#126424](https://github.com/openclaw/openclaw/pull/126424))
- **Platform inconsistency**: `message send --media` allowlists behave differently on WhatsApp vs Telegram for identical paths. ([#110346](https://github.com/openclaw/openclaw/issues/110346))
- **Long-running task UX**: Background tasks and cron wake failures are silent; users describe the experience as "not worth the cost." ([#88087](https://github.com/openclaw/openclaw/issues/88087))

### Satisfaction Signals
-

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: Personal AI Agent Open-Source Ecosystem
**Date:** 2026-09-01 | **Projects Analyzed:** 10

---

## 1. Ecosystem Overview

The open-source personal AI agent landscape is in a high-velocity consolidation phase, with projects split between aggressive feature iteration (OpenClaw, CoPaw, Hermes Agent, ZeroClaw) and security-hardening/maintenance cycles (ZeptoClaw, LobsterAI, NullClaw). Multi-agent orchestration, MCP tool integration, and channel reliability dominate the bug and feature discourse across nearly every project. The ecosystem is moving toward more modular, sandboxed architectures, but stability remains uneven — several projects shipped major releases in the past week and are now actively triaging regressions.

---

## 2. Activity Comparison

| Project | Issues Updated | PRs Updated | Closed/Merged | Releases | Open Issues | Health Signal |
|---|---|---|---|---|---|---|
| **OpenClaw** | 480 | 500 | 254 / 197 | None | High backlog | 🔴 High activity, high bug count |
| **CoPaw** | 29 | 39 | ~16 merged | 2 betas (v2.2.0-beta.4/5) | 15 active | 🟡 Pre-release stabilization |
| **Hermes Agent** | 50 | 50 | ~43 closed | v0.21.0 (Aug 31) | 43 open | 🟡 Post-release triage intensity |
| **ZeroClaw** | 26 | 50 | 1 / 0 | None | Elevated | 🟡 Heavy RFC pipeline, no merges |
| **NanoClaw** | 50 | 34 | 41 / 16 | None | 9 open | 🟢 Active triage, infra maturing |
| **IronClaw** | 14 | 20 | 3 merged | None | Moderate | 🟢 Solid cadence, design-system focus |
| **LobsterAI** | 11 | 27 | ~6 (stale-closed) | None | Moderate | 🟡 Maintenance + security hardening |
| **Moltis** | 2 | 4 | 3 merged | 20260831.01 | Low | 🟢 Stable, security-focused |
| **PicoClaw** | 1 | 5 | 0 | None | 1 tracked | 🟡 Moderate, responsive fixes |
| **ZeptoClaw** | 8 | 1 | 1 merged | None | 8 (all safety) | 🟢 Narrow security focus |
| **NullClaw** | 0 | 0 | 0 | None | 0 active | 🔴 Dormant / minimal maintenance |

**Health Score (qualitative):** OpenClaw 🔴 | Hermes Agent 🟡 | CoPaw 🟡 | ZeroClaw 🟡 | NanoClaw 🟢 | IronClaw 🟢 | Moltis 🟢 | ZeptoClaw 🟢 | PicoClaw 🟡 | LobsterAI 🟡 | NullClaw 🔴

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of activity:** 480 issues / 500 PRs updated in 24h is an order of magnitude above most projects, indicating the largest contributor base and most active maintenance pipeline.
- **Multi-agent depth:** OpenClaw is the only project with a merged gateway-level conversation-delivery fix (PR #126424) spanning 8+ channels — a capability no other project has attempted at this scope.
- **Platform coverage:** Native support for Discord, Telegram, Slack, iMessage, Matrix, Mattermost, Feishu, and WhatsApp is unmatched.

**Technical approach differences:**
- OpenClaw uses a **gateway-centric architecture** with agent bindings and cron reliability as first-class concerns, whereas projects like NanoBot and PicoClaw take a lighter, channel-per-driver approach.
- OpenClaw's **compaction/timeout sharing** and **MCP subagent injection** (issue #85030) are systemic problems that echo across the ecosystem, but only OpenClaw has open PRs actively addressing them.
- Unlike Hermes Agent (plugin-driven `pre_llm_call` overrides) or ZeroClaw (WASM plugin runtime RFCs), OpenClaw's extensibility is skill-based rather than runtime-based.

**Community size:** OpenClaw's activity volume (480+ issues/day) suggests a community 5–10x larger than NanoBot (6 issues) or Moltis (2 issues). Hermes Agent and CoPaw sit in a similar tier. NullClaw and ZeptoClaw appear to be smaller, niche communities.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **MCP tool injection / trust** | OpenClaw (#85030), Hermes Agent (#88858), IronClaw (#8008/#8009), ZeptoClaw (#653) | Tools not propagating to subagents/sessions; camelCase vs snake_case detection bugs; error flattening obscuring diagnosis |
| **Channel reliability & message loss** | OpenClaw (#96834), NanoClaw (#3085/#3105), Hermes Agent (#96384), PicoClaw (#3343) | WhatsApp image wedging, mention-detection failures, forwarded-message content loss, infinite edit loops |
| **Cron / recurring task correctness** | OpenClaw (#127999/#131590/#134589), NanoClaw (#5620), Hermes Agent (#99975), NanoClaw (#2997) | Silent job drops, doctor race conditions, recurring reminders with static text stopping after first fire |
| **Context / memory management** | NanoBot (#5610/#5570/#5571), CoPaw (#7133/#7447), ZeroClaw (#6850/#9103) | Cumulative memory summaries, explicit recall vs auto-preload, memory lifecycle decoupling from storage |
| **Migration / upgrade fragility** | OpenClaw (#133813/#133347/#134445), NanoClaw (#3105) | Doctor migration blockers, cron job quarantine, WhatsApp-cloud upgrade stranding — all producing silent data loss |
| **Child process / resource leaks** | OpenClaw (#97636), ZeptoClaw (#644) | Zombie accumulation, un-reaped process trees, missing environment scrubbing on spawn |
| **Security hardening** | ZeptoClaw (6/8 issues), LobsterAI (#2590), ZeroClaw (#10495), OpenClaw (#45740) | API token leakage, insecure file permissions, query-param auth, prompt injection from untrusted skill data |
| **Local-model support** | NanoClaw (#3643), LobsterAI (#1635), Hermes Agent (#99943) | Hardcoded container timeouts, Ollama compatibility gaps, compressor window clamping on cloud providers |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | CoPaw | NanoBot | ZeroClaw | IronClaw | NanoClaw | PicoClaw | ZeptoClaw | Moltis | LobsterAI | NullClaw |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Multi-agent gateway | Post-release triage | Memory + channels | Context management | Architecture RFCs | WebUI + MCP | Infrastructure hardening | Channel fidelity | Security hardening | Sandbox isolation | Desktop app | Dormant |
| **Target user** | Multi-agent operators | Power users / plugin authors | Enterprise teams | Researchers / devs | Systems architects | Web-first users | Self-hosted operators | IRC/Deltachat users | Security-conscious | DevOps / K8s | Desktop end-users | Niche |
| **Tech stack** | TypeScript gateway | Python + plugin hooks | TypeScript + ReMe memory | Rust | Rust + WASM | TypeScript + M3 design | TypeScript + containers | TypeScript | Rust | Rust | Electron + React | N/A |
| **Extensibility model** | Skills + MCP | Plugin hooks (`pre_llm_call`) | Slash commands + ReMe | Runtime context blocks | WASM plugins | MCP catalog + tool_search | In-tree skills | Tool feedback system | Dependency-pinned | Sandboxed executions | N/A | N/A |
| **Channel strategy** | 8+ native channels | Bot Group Chats + desktop | Multi-channel + browser SDK | WebSocket + Telegram focus | Transport adapters | Native Slack UI | WhatsApp/Signal/Slack | IRCv3 + Deltachat + Telegram | N/A | Docker-local | Desktop app | — |
| **Release cadence** | No release (hardening) | v0.21.0 shipped Aug 31 | Beta cycle (v2.2.0-beta.4/5) | No release | No release | No release | No release (pre-release) | No release | No release | v20260831.01 today | No release | None |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (high issue/PR volume, active merges):**
- **OpenClaw:** 480 issues + 500 PRs/day. Largest community, but also the largest bug backlog. In hardening mode.
- **CoPaw:** Two beta releases in one day. Pre-release stabilization with strong contributor momentum.
- **Hermes Agent:** 50/50 issue-PR ratio post-v0.21.0. High-velocity triage but regressive bugs dominating.

**Tier 2 — Steady Development (moderate activity, clear focus):**
- **ZeroClaw:** 26 issues + 50 PRs, but zero merges. Heavy RFC discussion phase — community is debating architecture before shipping.
- **NanoClaw:** 50 issues + 34 PRs, 41/16 closed. Infrastructure maturing (PR templates, changelog harvesting). Bug backlog is the bottleneck.
- **IronClaw:** 14 issues + 20 PRs, 3 merged today. Design-system epic driving coherent progress. Solid health.
- **LobsterAI:** 11 issues + 27 PRs, but 6 stale-closed. Dependency maintenance + one security PR. Energy is fading on older tickets.

**Tier 3 — Maintenance / Niche (low volume, specialized):**
- **Moltis:** 2 issues + 4 PRs, release shipped today. Small but responsive. Security and Docker-local focus.
- **PicoClaw:** 1 issue + 5 PRs. Responsive to bugs (9-day issue→PR turnaround). Niche channel focus.
- **ZeptoClaw:** 8 issues (all safety) + 1 merge. Deliberate, security-first cadence. Small community.

**Tier 4 — Stalled:**
- **NullClaw:** Zero activity. Only a stale Dependabot PR after 2 months. Effectively dormant.

---

## 7. Trend Signals

1. **MCP integration is the #1 cross-cutting challenge.** Every major project has open issues around MCP tool injection, trust gating, or error visibility. The ecosystem lacks a standardized MCP-to-subagent propagation pattern. *Value for developers:* Expect MCP compatibility to be a key differentiator in the next release cycle; projects that solve subagent tool injection will pull ahead.

2. **Channel reliability is fragile across the board.** WhatsApp image processing, Telegram edit loops, forwarded-message content loss, and mention-detection failures are recurring failure modes. *Value:* Any project that ships bulletproof multi-channel message handling will have a significant UX advantage.

3. **Memory architecture is being rethought everywhere.** NanoBot (explicit recall), ZeroClaw (lifecycle decoupling), CoPaw (explicit reindex), and Hermes Agent (SQLite migration RFC) are all moving away from implicit, auto-loaded memory. *Value:* The next generation of agents will treat memory as a pluggable, scoped resource rather than a global context store.

4. **Post-release triage is where projects go to die — or mature.** Hermes Agent's v0.21.0 shipped with compressor regressions and MCP trust-gate bugs; OpenClaw's hardening phase is drowning in migration issues. *Value:* Projects with strong pre-release stabilization (CoPaw's beta cadence) or automated regression guards (IronClaw's design-system phases) are likely to ship more reliable releases.

5. **Security hardening is no longer optional.** ZeptoClaw has 6 of 8 open issues as safety-critical; ZeroClaw has a P0 config-overwrite bug; LobsterAI has an unmerged MCP injection PR from 5 months ago. *Value:* Security-aware operators will prefer projects with visible hardening pipelines (ZeptoClaw's RustSec fixes, Moltis's Snyk pinning) over those with dormant security PRs.

6. **Local-model and self-hosted support is a growing demand.** Hardcoded container timeouts (NanoClaw), Ollama gaps (LobsterAI), and compressor window clamping (Hermes Agent) are blocking self-hosted workflows. *Value:* Projects that expose configuration seams for resource limits and provider-specific behavior will capture the self-hosted market.

7. **Multi-agent orchestration is the emerging frontier.** OpenClaw's gateway bindings, Hermes Agent's Bot Group Chat persistence, and ZeroClaw's session-ownership RFCs all point toward structured multi-agent systems. *Value:* The project that first delivers reliable, cross-agent tool sharing with bounded delivery will define the next iteration of the ecosystem.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-01

---

## 1. Today's Overview

NanoBot remains highly active with 6 issues and 18 PRs updated in the last 24 hours, split evenly between open (3 issues, 8 PRs) and closed/merged (3 issues, 10 PRs). No new releases were published today, but the merge velocity is strong, suggesting a steady cadence of incremental improvements. Development focus is concentrated on channel reliability (WebSocket portability fix, Telegram rich-message streaming), memory/context management refactoring, and cron delivery customization. Community engagement is moderate — most items carry zero reactions, indicating a contributor-heavy rather than broad-user base at this stage.

---

## 2. Releases

No new releases published today. The project continues to ship improvements through merged PRs without an official version bump yet.

---

## 3. Project Progress

**Merged / Closed PRs Today:**

| PR | Title | Author |
|---|---|---|
| [#5617](https://github.com/HKUDS/nanobot/pull/5617) | fix(websocket): stop treating SO_ACCEPTCONN as portable in listener health check | Krislu1221 |
| [#5615](https://github.com/HKUDS/nanobot/pull/5615) | feat(agent): support ephemeral runtime context | linhongyu510 |
| [#5619](https://github.com/HKUDS/nanobot/pull/5619) | feat(runtime-context): allow blocks to opt out of history persistence | xiexiahao |
| [#5620](https://github.com/HKUDS/nanobot/pull/5620) | feat(cron): support configurable delivery and batch archive | xiexiahao |
| [#5531](https://github.com/HKUDS/nanobot/pull/5531) | fix(telegram): upgrade streaming preview to rich in place at stream end | nolanchic |
| [#5612](https://github.com/HKUDS/nanobot/pull/5612) | refactor(agent): unify runner request fitting | chengyongru |
| [#5618](https://github.com/HKUDS/nanobot/pull/5618) | style(tui): simplify the runtime header | chengyongru |
| [#5598](https://github.com/HKUDS/nanobot/pull/5598) | docs(tools): clarify edit_file selector exclusivity | dajiaohuang |
| [#5604](https://github.com/HKUDS/nanobot/pull/5604) | docs(edit_file): state that match selectors are mutually exclusive | LWT1212 |
| [#5610](https://github.com/HKUDS/nanobot/pull/5610) | refactor(agent): make memory summaries cumulative | chengyongru |

**Key advances:**
- **Ephemeral runtime context** ([#5615](https://github.com/HKUDS/nanobot/pull/5615), [#5619](https://github.com/HKUDS/nanobot/pull/5619)): Agent runtime-context blocks can now opt out of session persistence, keeping sensitive or transient data out of durable history.
- **Cron result routing** ([#5620](https://github.com/HKUDS/nanobot/pull/5620)): Cron job outputs can now be delivered to configurable channels with batch archive support, decoupling operational noise from personal chat sessions.
- **Telegram rich-message streaming fix** ([#5531](https://github.com/HKUDS/nanobot/pull/5531)): The `rich_messages` + `streaming` combination now correctly upgrades the preview to a rich message at stream end, resolving a long-standing bug.
- **Memory system refactoring** ([#5610](https://github.com/HKUDS/nanobot/pull/5610), [#5612](https://github.com/HKUDS/nanobot/pull/5612), [#5568](https://github.com/HKUDS/nanobot/pull/5568)): Cumulative memory summaries, unified runner request fitting, and context compaction owned by the runner are consolidating the agent's context pipeline.
- **WebSocket portability fix** ([#5617](https://github.com/HKUDS/nanobot/pull/5617)): Removed non-portable `SO_ACCEPTCONN` usage, fixing crashes on macOS/BSD.

---

## 4. Community Hot Topics

| Item | Type | Comments | Trend |
|---|---|---|---|
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) — MCP Apps host support in WebUI | Issue (Open) | 3 | 🔥 Strong interest in MCP ecosystem integration |
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) — Feishu multi-turn message consolidation | Issue (Open) | 3 | 🔥 Chinese-market channel UX improvement |
| [#5283](https://github.com/HKUDS/nanobot/pull/5283) — Per-session sandbox isolation | PR (Open) | — | Security-focused; open since Aug 7, needs review |
| [#5571](https://github.com/HKUDS/nanobot/pull/5571) — Require explicit memory recall by default | PR (Open) | — | Architectural shift in memory behavior |
| [#4919](https://github.com/HKUDS/nanobot/pull/4919) — Custom Telegram Bot API base URL | PR (Open, conflict) | — | Open since Jul 14; enterprise/self-hosted Telegram use case |

**Analysis:**
- **MCP Apps support** (#5251) reflects growing demand to surface MCP server UI components (in addition to tool calls) directly in the WebUI — a natural extension of NanoBot's existing MCP client.
- **Feishu UX** (#5567) highlights pain for Chinese-language users who expect `1 message in → 1 message out` parity, a standard expectation in modern chat apps.
- **Memory recall redesign** (#5571, #5570) signals a fundamental philosophy shift: moving from automatic preload of all memory to explicit, on-demand recall, reducing context pollution.
- **Per-session sandbox** (#5283) and **custom Telegram API** (#4919) are open a long time and may need maintainer triage.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|---|---|---|---|
| 🔴 P1 | [#5617](https://github.com/HKUDS/nanobot/pull/5617) | WebSocket health check used non-portable `SO_ACCEPTCONN`, crashing on macOS/BSD | ✅ Merged |
| 🟠 P2 | [#5516](https://github.com/HKUDS/nanobot/issues/5516) | Rich messages never rendered when streaming enabled on Telegram | ✅ Fixed in [#5531](https://github.com/HKUDS/nanobot/pull/5531) |
| 🟡 P2 | [#5592](https://github.com/HKUDS/nanobot/issues/5592) | `edit_file` docs misleading on selector exclusivity | ✅ Fixed in [#5598](https://github.com/HKUDS/nanobot/pull/5598), [#5604](https://github.com/HKUDS/nanobot/pull/5604) |

**Summary:** Three bugs reported today, all with corresponding fixes already merged. The Telegram rich-message + streaming regression was the most impactful user-facing issue. No open crash reports or P1 bugs remain unaddressed.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---|---|---|
| MCP Apps host support in WebUI | [#5251](https://github.com/HKUDS/nanobot/issues/5251) | 🟡 Medium — design question, needs spec |
| Feishu multi-turn card consolidation | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 🟢 High — incremental channel improvement, clear scope |
| HTML/.txt/.md preview (iframe srcdoc) | [#5493](https://github.com/HKUDS/nanobot/issues/5493) | 🟡 Medium — channel-agnostic, needs sandbox review |
| Per-session filesystem sandbox | [#5283](https://github.com/HKUDS/nanobot/pull/5283) | 🟡 Medium — security feature, open 25 days, needs review |
| Custom Telegram Bot API endpoint | [#4919](https://github.com/HKUDS/nanobot/pull/4919) | 🟡 Medium — enterprise use case, has conflicts |
| MST (Meta-Search Tool) as provider | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | 🟡 Medium — new provider integration, unreviewed |
| Explicit memory recall by default | [#5571](https://github.com/HKUDS/nanobot/pull/5571) | 🟢 High — in progress, part of larger memory refactor |
| Pluggable memory recall backend | [#5570](https://github.com/HKUDS/nanobot/pull/5570) | 🟢 High — complements #5571, in progress |

**Roadmap signal:** The memory subsystem is undergoing a significant redesign (cumulative summaries, pluggable backend, explicit recall). Cron delivery customization and ephemeral runtime contexts are also maturing. These suggest an upcoming release focused on **context management quality** and **operational channel hygiene**.

---

## 7. User Feedback Summary

- **Telegram rich messages + streaming** was a notable pain point: users enabling both features expected rich output but got legacy HTML fallbacks. The fix (#5531) resolves this.
- **Feishu channel users** report fragmented conversations — agent tool calls, progress updates, and final replies arrive as separate messages, breaking the natural chat rhythm. Consolidation into a single streaming card is a clear UX win.
- **Cron job noise** in personal chat sessions is a real operational concern. Users running health checks and daily reports want output routed to dedicated channels with archive capabilities (#5513 / #5620).
- **`edit_file` documentation** confused users about mutually exclusive selectors, leading to runtime errors. Clarification PRs (#5598, #5604) address this.
- **WebUI file preview** (#5493) is a convenience request — users want to preview HTML, TXT, and MD content inline without leaving the interface.

**Satisfaction signal:** Most feedback is constructive feature requests and clear bug reports rather than frustration, indicating an engaged and technically literate user base.

---

## 8. Backlog Watch

| Item | Open Since | Days Open | Risk |
|---|---|---|---|
| [#5283](https://github.com/HKUDS/nanobot/pull/5283) — Per-session sandbox isolation | 2026-08-07 | 25 | 🟡 Security feature stalled; no review comment yet |
| [#4919](https://github.com/HKUDS/nanobot/pull/4919) — Custom Telegram Bot API base URL | 2026-07-14 | 49 | 🔴 Long-standing; has merge conflicts; enterprise users waiting |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) — MST as web search provider | 2026-08-03 | 29 | 🟡 New provider integration; unreviewed |
| [#5571](https://github.com/HKUDS/nanobot/pull/5571) — Explicit memory recall by default | 2026-08-27 | 25 | 🟡 Part of active refactor; conflicts noted |
| [#5570](https://github.com/HKUDS/nanobot/pull/5570) — Pluggable memory recall backend | 2026-08-27 | 25 | 🟡 Paired with #5571; conflicts noted |
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) — MCP Apps host support | 2026-08-05 | 27 | 🟡 Enhancement request; no PR yet |

**Recommendation:** PR [#4919](https://github.com/HKUDS/nanobot/pull/4919) (custom Telegram API) has been open the longest (49 days) with conflicts and should be triaged. The memory-related PRs (#5570, #5571) appear to be part of an coordinated refactor and may resolve conflicts together. The sandbox PR [#5283](https://github.com/HKUDS/nanobot/pull/5283) is a security feature that deserves prioritization.

---

*Digest generated from GitHub data on 2026-09-01. Source: [github.com/HKUDS/nanobot](https://github.com/HKUDS/nanobot)*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-09-01

## 1. Today's Overview

Hermes Agent is in a phase of intense post-release triage following v0.21.0 ("The Pantheon Release"), shipped on August 31, 2026. The project saw 50 issues and 50 PRs updated in the last 24 hours, with 43 open issues and 42 open PRs — indicating a high-velocity contributor base and active maintenance. The release itself reflects massive scale: ~5,800 commits, ~2,475 merged PRs, and 760+ contributors since v0.20.0. While no new releases landed today, the merge queue and issue pipeline remain heavily populated, suggesting the team is aggressively closing the gap between the new release and user-identified regressions.

## 2. Releases

**v0.21.0 (v2026.8.31)** — "The Pantheon Release"

- **Since v0.20.0:** ~5,800 commits · ~2,475 merged PRs · ~5,680 files changed · ~869K insertions · ~135K deletions · ~2,100 issues closed · 760+ contributors
- No breaking-change migration guide was published alongside the release notes provided, but several v0.21.0 regressions have already surfaced (see Bugs & Stability).
- Notable new capabilities on `main` at time of release: gateway-owned authority, same-gateway runner, and scoped cross-gateway transport for Bot Group Chats.

## 3. Project Progress

**Merged / Closed PRs (today):**

| PR | Author | Summary |
|----|--------|---------|
| [#99970](https://github.com/NousResearch/hermes-agent/pull/99970) | mineblow | Desktop: fan out durable user prompts live — user messages now publish on the ordered session event stream and render immediately without waiting for transcript polling |
| [#99975](https://github.com/NousResearch/hermes-agent/pull/99975) | fangliquanflq | Cron: keep bot-chat output when a live session owns the chat — fixes silent discarding of cron delivery output |
| [#98814](https://github.com/NousResearch/hermes-agent/issues/98814) *(closed)* | — | Windows: `update hermes` via natural language no longer kills its own process tree |
| [#96699](https://github.com/NousResearch/hermes-agent/issues/96699) *(closed)* | — | Desktop remote multi-profile: fixed model catalog launch-home and sticky composer provider |
| [#97046](https://github.com/NousResearch/hermes-agent/issues/97046) *(closed)* | — | Desktop SSH remote backend: fixed post-update 503 code-skew and stale restart advice |
| [#98680](https://github.com/NousResearch/hermes-agent/issues/98680) *(closed)* | — | Desktop: fixed keep-alive transcript ticks that flashed the composer and stole focus |
| [#92893](https://github.com/NousResearch/hermes-agent/pull/92893) | j0935586110-lgtm | Agent: `pre_llm_call` runtime_override hook — plugins can now proactively override model/provider at runtime |

**Actively advancing (open PRs):**

- **#99996** — Cron per-job `api_max_retries` override (end-to-end wired)
- **#99995** — Fix case-colliding email files breaking Windows checkouts
- **#84210** — Telegram: retry transient media downloads
- **#80927** — Security: keep custom endpoint API keys out of `config.yaml` via `key_env`
- **#99994 / #99976** — CLI: pass `max_iterations` to `AIAgent` in oneshot path
- **#99990** — Browser: fix `browser_console` selecting New Tab instead of navigated page
- **#99981** — Desktop: paste OS file copy as attachment in composer
- **#99980** — Desktop: click-to-expand link previews with SSRF-guarded resolver
- **#99497** — Desktop: complete messaging platform icon coverage (DingTalk, WeCom, Feishu/Lark)
- **#99934** — Docs: native NeMo Relay integration guide

## 4. Community Hot Topics

| Issue/PR | Comments | Tags | Summary |
|----------|----------|------|---------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | 133 | bug, skills, P3 | Automated freshness probe failing; index is 29.8h old vs 26h limit. Highest-commented open issue by a wide margin. |
| [#88168](https://github.com/NousResearch/hermes-agent/issues/88168) — Windows case-collision git dirty | 13 | bug, Windows, P1 | Two email files differing only in case cause permanent `git status` dirtiness on Windows. 2 👍. Fix PR #99995 submitted. |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) — Bot Group Chats survive Desktop close | 10 | feature, desktop, P2 | Core production work to connect gateway authority foundation to persistent group-chat sessions. |
| [#84418](https://github.com/NousResearch/hermes-agent/issues/84418) — Add Russian to Desktop UI | 7 | feature, i18n, P3 | Russian locale already exists in Hermes core but is absent from Desktop language picker. |
| [#94198](https://github.com/NousResearch/hermes-agent/issues/94198) — Hermes Chat standalone web UI | 6 | feature, dashboard | Community project (royabby365/hermes-chat) using FastAPI+Jinja2; model picker with tree-style provider browser. |
| [#52694](https://github.com/NousResearch/hermes-agent/issues/52694) — Background notifications reply to stale Discord DMs | 5 | bug, Discord, P2 | Background-process completion events misinterpreted as user messages, replying to stale anchors. |
| [#88858](https://github.com/NousResearch/hermes-agent/issues/88858) — MCP trust gate readOnlyHint ignored | 5 | bug, MCP, P2 | `readOnlyHint: true` never detected (camelCase vs snake_case mismatch); every tool gated as write-capable, making untrusted MCP servers unusable. |

**Analysis:** The skills-index watchdog (#66616) dominates community attention with 133 comments — users are highly sensitive to the reliability of the Skills Hub. Windows compatibility (#88168) and MCP trust-gate behavior (#88858) are the most pressing technical blockers. Bot Group Chat persistence (#97681) represents a major architectural feature request that the team has partially shipped but is still productionizing.

## 5. Bugs & Stability

**P1 — Critical:**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#99839](https://github.com/NousResearch/hermes-agent/issues/99839) | `hermes import` can overwrite default `~/.hermes` while displaying alternate `HERMES_HOME`; starts second gateway | No |
| [#97764](https://github.com/NousResearch/hermes-agent/issues/97764) *(closed)* | Desktop renderer never resumes stored session after mid-turn WS drop — chat frozen with "session-scoped RPC rejected" | Merged |
| [#98814](https://github.com/NousResearch/hermes-agent/issues/98814) *(closed)* | Windows: NL `update hermes` kills updater process tree | Merged |

**P2 — High:**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#96384](https://github.com/NousResearch/hermes-agent/issues/96384) | **P0-severity**: Forwarded Slack messages silently lose text AND files (`is_msg_unfurl`/`is_share` ambiguity) | No |
| [#99943](https://github.com/NousResearch/hermes-agent/issues/99943) | Compressor context window clamped to `ollama_num_ctx` on cloud providers — 1M window silently drops to 65,536 (v0.21.0 regression) | No |
| [#99897](https://github.com/NousResearch/hermes-agent/issues/99897) | Output-cap retry clamp computed but not applied to retried request — spins until max compression attempts | No |
| [#88858](https://github.com/NousResearch/hermes-agent/issues/88858) | MCP trust gate: `readOnlyHint` never detected — all tools gated as write-capable | No |
| [#52694](https://github.com/NousResearch/hermes-agent/issues/52694) | Background process notifications reply to stale Discord DM anchors | No |
| [#99956](https://github.com/NousResearch/hermes-agent/issues/99956) | Cron `bot-chat` delivery fails when target profile has active session lock | #99975 (closed, fix merged) |
| [#81860](https://github.com/NousResearch/hermes-agent/issues/81860) | QQ group handoff binds DM-shaped session key, orphaning session | No |
| [#99788](https://github.com/NousResearch/hermes-agent/issues/99788) | TUI Gateway Status hardcodes 4 platforms; Signal/A2A show "Not configured" when connected | No |
| [#88621](https://github.com/NousResearch/hermes-agent/issues/88621) | Desktop incoming messages interrupt active composer typing | No |
| [#99962](https://github.com/NousResearch/hermes-agent/issues/99962) | `browser_console` evaluates in Chrome New Tab instead of navigated page | #99990 (open) |
| [#99920](https://github.com/NousResearch/hermes-agent/issues/99920) | Long-session backfill causes full-window flicker in Desktop (post-#97293) | No |

**P3 — Medium:**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#62951](https://github.com/NousResearch/hermes-agent/issues/62951) | Bundled `chronos` plugin fails to load: `register_cron_scheduler` attr missing on v0.18.2+ | No |
| [#99959](https://github.com/NousResearch/hermes-agent/issues/99959) | `hermes insights` crashes on malformed session timestamp | No |
| [#94902](https://github.com/NousResearch/hermes-agent/issues/94902) | Context-file prompt-injection scanner is all-or-nothing and silent; no severity config | No |
| [#99867](https://github.com/NousResearch/hermes-agent/issues/99867) | Windows Desktop session scroll control overlaps right sidebar resize (3px hit area) | No |
| [#84106](https://github.com/NousResearch/hermes-agent/issues/84106) | `hermes config get mcp_servers` exposes resolved MCP secrets despite `redact_secrets: true` | No |
| [#49195](https://github.com/NousResearch/hermes-agent/issues/49195) | `hermes -z --resume` silently ignores resume flag; session never hydrated | No |

**Notable v0.21.0 regressions:** The compressor clamp (#99943) and output-cap retry (#99897) were introduced in or around the v0.21.0 release and directly impact non-Ollama cloud providers. The `chronos` plugin breakage (#62951) predates v0.21.0 but remains unfixed.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Type | Likelihood for Near-Term |
|----------|------|--------------------------|
| [#674](https://github.com/NousResearch/hermes-agent/issues/674) — Memory Storage Migration: Flat Files → SQLite | Feature | **High** — foundational for cognitive memory ops (#509), long-open since March 2026 |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) — Bot Group Chats persist after Desktop closes | Feature | **High** — core architectural work already on `main`, production polish in progress |
| [#99981](https://github.com/NousResearch/hermes-agent/pull/99981) — Paste OS file as composer attachment | Feature | **High** — PR already submitted, addresses common UX expectation |
| [#99980](https://github.com/NousResearch/hermes-agent/pull/99980) — Click-to-expand link previews with SSRF guard | Feature | **High** — PR submitted, security-conscious design |
| [#84418](https://github.com/NousResearch/hermes-agent/issues/84418) — Russian locale in Desktop UI | Feature | **Medium** — trivial to add, no apparent blocker |
| [#94198](https://github.com/NousResearch/hermes-agent/issues/94198) — Standalone web chat UI ("Hermes Chat") | Feature | **Low-Medium** — community project, not upstream |
| [#37253](https://github.com/NousResearch/hermes-agent/issues/37253) — Disable hardcoded system prompt injections | Feature | **Medium** — power-user request, no config gate exists |
| [#99996](https://github.com/NousResearch/hermes-agent/pull/99996) — Per-job cron `api_max_retries` | Feature | **High** — PR submitted, fills a real operational gap |

**Prediction:** v0.22.0 will likely include the Desktop file-paste (#99981), link previews (#99980), per-job cron retries (#99996), and the oneshot `max_iterations` fix (#99994/#99976). The SQLite memory migration (#674) is too large for a patch release but may see a design document or initial PR.

## 7. User Feedback Summary

**Pain points:**

- **Skills Hub reliability** (#66616, 133 comments): The single most-discussed open issue. Users depend on the skills index for discoverability; a 29.8h stale index breaks trust in the ecosystem.
- **Windows compatibility** (#88168, #99867, #98814): Multiple Windows-specific bugs — case-collision git dirtiness, scroll-control hit-area issues, and the updater killing itself — suggest the Windows QA pipeline needs strengthening post-v0.21.0.
- **MCP trust gate broken** (#88858): The camelCase vs snake_case mismatch renders `trust: untrusted` effectively useless, a security regression for users who rely on MCP sandboxing.
- **Slack forwarded messages lost** (#96384, marked P0 by author): A critical workflow break — forwarding is a primary Slack collaboration pattern and it silently drops content.
- **Compressor regression on cloud providers** (#99943): Users on non-Ollama providers with large context windows (1M+) are silently seeing their windows capped to 65,536 tokens — a severe usability regression.
- **Secrets leakage in config** (#84106, #80927): Two related issues — `hermes config get` exposes resolved MCP secrets, and the Desktop model-assignment flow was writing API keys into plaintext `config.yaml`. Both are security UX gaps.
- **Desktop composer interruptions** (#88621, #98680): Incoming messages and keep-alive ticks steal focus during typing, degrading the desktop experience.

**Satisfaction signals:** The community is actively contributing fixes (20+ open PRs today alone), and several critical bugs have already been resolved (Desktop session resume, Windows updater, SSH post-update 503). The `pre_llm_call` runtime override (#92893) shows the plugin system is maturing in user-requested directions.

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|----------------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale | ~45 days | Highest-commented open issue; directly impacts Skills Hub trust. No visible fix PR. |
| [#674](https://github.com/NousResearch/hermes-agent/issues/674) — SQLite memory migration | ~6 months | Foundational for cognitive memory (#509); no active PR. Blocker for long-term memory features. |
| [#37253](https://github.com/NousResearch/hermes-agent/issues/37253) — Disable hardcoded system prompt injections | ~3 months | Power-user request with no config gate; no fix PR. |
| [#49195](https://github.com/NousResearch/hermes-agent/issues/491

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-01

## 1. Today's Overview

PicoClaw shows moderate development activity on 2026-09-01, with five PRs updated in the last 24 hours and one open issue actively tracked. No new releases were published, and there were no merged or closed PRs today. The most notable development is the pairing fix PR (#3353) directly addressing the bug reported in issue #3343, indicating responsive maintainers on stability concerns. Overall project health is stable with ongoing feature expansion and bug remediation in parallel.

## 2. Releases

No new releases were published. The latest release information is unavailable.

## 3. Project Progress

- **PR #3299 — Add native Exa web search provider** [CLOSED] — The Exa integration was finalized, adding a native `tools.web` / `web_search` provider with Exa's `POST /search` API, full date-range filtering (`d`/`w`/`m`/`y`), and `X-Api-Key` authentication. This expands PicoClaw's web search capabilities beyond existing providers.
- **PR #3353 — Fix: bound tool feedback animations** [OPEN] — Directly addresses the runaway animation bug; caps edits at five minutes and stops on the first edit error. A targetted stability fix, awaiting merge.
- **PR #3354 — feat(irc): assemble IRCv3 multiline messages** [OPEN] — Adds IRCv3 `draft/multiline` support so multi-line IRC messages arrive as a single cohesive message in PicoClaw. Represents progress on IRC channel fidelity.
- **PR #3222 — refactor(deltachat): cleanup implementation** [OPEN] — Removes ~200 LOC of legacy code, drops outdated tests, renames config fields, and references the official relay list. A cleanup PR that improves maintainability.

## 4. Community Hot Topics

- **Issue #3343 — Tool feedback animation can edit a Telegram message indefinitely** — [Link](https://github.com/sipeed/picoclaw/issues/3343) · 2 comments · Created 2026-08-22
  The most-discussed open issue: a tool feedback animation looped `editMessageText` every 3 seconds for days after an agent turn stalled, generating 228,000+ edit attempts and triggering a Telegram server-side rate limit. This highlights a critical gap in lifecycle management for async channel operations — a concern shared by users of any agent that interacts with message-based platforms.
- **PR #3353 — fix(channels): bound tool feedback animations** — [Link](https://github.com/sipeed/picoclaw/pull/3353) · Created 2026-08-31
  The direct response to #3343; demonstrates healthy issue-to-PR turnaround from the community.

**Underlying need:** Users require robust error handling and bounded retries for all channel-mediated agent operations, especially on rate-limited platforms like Telegram.

## 5. Bugs & Stability

| Severity | Item | Details |
|----------|------|---------|
| **High** | Issue #3343 — Infinite Telegram edit loop | Tool feedback animations continued indefinitely after a failed agent turn, causing 228K+ edit attempts and a Telegram rate limit. Fix PR #3353 exists and is open. |

No other bugs or regressions were reported today. The project's stability picture is otherwise clean, with the above issue being the sole outstanding concern.

## 6. Feature Requests & Roadmap Signals

- **Exa web search provider** (#3299, now closed) — Suggests demand for diversified, high-quality web search backends. Expect Exa to become a default or easily enabled option in the next release cycle.
- **IRCv3 multiline message support** (#3354) — Signals continued investment in IRC channel parity. Users on IRC-based workflows need multi-line message coherence.
- **Build Remote Agent phone pairing** (#3344) — Adds a `gbr/1` protocol adapter so a phone can spectate the desktop agent via QR or 8-char code pairing. Reflects interest in mobile companion experiences.
- **Deltachat cleanup** (#3222) — While a refactor, the expanded deltachat documentation and config improvements signal that Deltachat integration is being matured for broader use.

**Prediction:** The next release will likely include the Exa search provider, bounded animation fix, and IRCv3 multiline support — all three are PR-ready and address clear user demand.

## 7. User Feedback Summary

- **Pain point:** Runaway tool feedback animations that spam channel APIs and trigger rate limits. This is a serious reliability issue for users running long-lived agent sessions on Telegram.
- **Use case expansion:** Users are actively requesting more search providers (Exa) and better support for legacy/protocol-specific channels (IRC multiline, Deltachat cleanup), indicating a user base that operates across diverse communication platforms.
- **Mobile companion interest:** The remote agent pairing PR (#3344) suggests users want to monitor and interact with their desktop agent from a phone, pointing toward a mobile-first companion workflow.
- **Satisfaction signal:** Quick community response to bug reports (issue #3343 → PR #3353 within 9 days) and ongoing contributor activity suggest a responsive and engaged project.

## 8. Backlog Watch

- **Issue #3343** — Still open but has an active fix PR (#3353). Monitor for merge.
- **PR #3344 — Build Remote Agent phone pairing** [OPEN, stale] — Created 2026-08-23, no maintainer response yet. Important for mobile spectating use case.
- **PR #3222 — Deltachat refactor** [OPEN, stale] — Created 2026-07-03, over a month old with no merge activity. Significant LOC reduction and docs improvement, worth maintainer review.
- **PR #3299 — Exa web search** [CLOSED but not released] — Merged/closed but no release has followed; users won't see the feature until a new version ships.

**Recommendation:** Maintainers should prioritize merging #3353 and triaging the stale PRs (#3222, #3344) to clear the backlog and ship the accumulated improvements.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-01

## 1. Today's Overview

NanoClaw saw sustained contributor activity today with 50 issues and 34 PRs updated in the last 24 hours, indicating a healthy development cadence. The project closed 41 issues and 16 PRs while maintaining 9 open issues and 18 open PRs, suggesting active triage and forward momentum. The dominant theme is infrastructure hardening — merged PRs this period focused on CI automation, PR template standardization, and skill delivery improvements. However, multiple high-severity bugs remain open, particularly around WhatsApp engagement, recurring task reliability, and container timeouts for local-model providers, signaling stability risks that demand maintainer attention before the next release.

## 2. Releases

No new releases were published. The project appears to be in a pre-release consolidation phase, with numerous infrastructure PRs merged to stabilize the development pipeline but no version tag cut.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#3695** — *feat(skills): Slack companion skills move in-tree; main is canonical* — Resolves a significant delivery pain point by making Slack agent skills available directly from the `main` checkout rather than requiring a separate branch fetch. ([link](https://github.com/nanocoai/nanoclaw/pull/3695))

**Merged infrastructure/process PRs (updated today):**

- **#3657** — *CI labels: report-only template-compliance status* — Automates PR template validation checks. ([link](https://github.com/nanocoai/nanoclaw/pull/3657))
- **#3648** — *CI labels: PR template v2 with token parsing and managed-kind reconcile* — Introduces the v2 PR template contract with automatic label classification. ([link](https://github.com/nanocoai/nanoclaw/pull/3648))
- **#3650** — *Release: harvest PR release-note blocks into draft changelog* — Contributors can now embed `release-note` blocks in PRs that feed directly into changelog generation. ([link](https://github.com/nanocoai/nanoclaw/pull/3650))
- **#3647** — *CI labels: automatic area/\* from changed paths and kind/\* from PR type* — Eliminates manual label triage for both area and kind classification. ([link](https://github.com/nanocoai/nanoclaw/pull/3647))
- **#3651** — *Docs: add issue-side intake section* — Documents the four-issue-form taxonomy and vulnerability reporting path. ([link](https://github.com/nanocoai/nanoclaw/pull/3651))
- **#3644** — *Chore: add GitHub issue forms* — Adds structured issue templates for bugs, skill requests, docs corrections, and security hardening. ([link](https://github.com/nanocoai/nanoclaw/pull/3644))

**Key open PRs advancing:**

- **#3646** — *fix(sweep): configurable idle timeout for container kills* — Addresses the hardcoded 30-minute absolute ceiling that prematurely terminates long local-model turns. ([link](https://github.com/nanocoai/nanoclaw/pull/3646))
- **#3691** — *test(update): isolate git fixtures from operator global config* — Fixes test brittleness caused by inheriting global git config in CI fixtures. ([link](https://github.com/nanocoai/nanoclaw/pull/3691))
- **#3581–3591** — *refactor(providers): contract declarations and implementations* — A multi-PR refactor establishing clean provider contracts for Codex, OpenCode, host, and runtime providers. ([links](https://github.com/nanocoai/nanoclaw/pull/3591))

## 4. Community Hot Topics

**Most discussed / highest-impact issues:**

1. **#3085** — *WhatsApp engage_mode=mention fails on typed @name text* [HIGH] — Users wired with `engage_mode='mention'` find that typing `@<agent>` without selecting the autocomplete pill silently drops the message. This is a critical UX failure for WhatsApp group integrations. ([link](https://github.com/nanocoai/nanoclaw/issues/3085))

2. **#3643** — *Hardcoded 30-min ABSOLUTE_CEILING_MS kills long local-model turns* [HIGH] — Local-model users (OpenCode provider) experience mid-turn container deaths that are impossible to configure around. This blocks a core use case for self-hosted inference. ([link](https://github.com/nanocoai/nanoclaw/issues/3643))
   - **Fix PR: #3646** is open and directly addresses this.

3. **#2997** — *Recurring reminders with fixed text stop arriving after first fire* [HIGH] — A deterministic bug where `hasIdenticalSend` matches against previous completions, silently dropping subsequent fires of recurring tasks. This undermines a fundamental agent capability. ([link](https://github.com/nanocoai/nanoclaw/issues/2997))

4. **#3105** — *WhatsApp-cloud upgrade strands messaging_groups rows* [HIGH] — Existing installations upgrading to the split `whatsapp-cloud` instance (from #2913) lose messaging silently with no migration path. This is a regression with no recovery. ([link](https://github.com/nanocoai/nanoclaw/issues/3105))

5. **#2868** — *`/update-skills` is a silent no-op for already-installed channels* [MEDIUM] — Channel updates are skipped silently, nullifying documented migration steps and leaving users on stale adapters. ([link](https://github.com/nanocoai/nanoclaw/issues/2868))

6. **#3694** — *Slack skills `add-slack` copy list breaks the build* [MEDIUM] — A by-the-book installation omits `slack-raw-text.ts`, causing lint and container suite failures on clean installs. ([link](https://github.com/nanocoai/nanoclaw/issues/3694))

**Underlying need:** The community is demanding reliability in core message-handling paths (WhatsApp mention detection, recurring tasks, skill updates) and configurability for resource constraints (local-model timeouts). The merged infrastructure PRs suggest maintainers are investing in process maturity, but the open bug backlog represents genuine user-facing blockers.

## 5. Bugs & Stability

**Open bugs ranked by severity:**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **HIGH** | [#3085](https://github.com/nanocoai/nanoclaw/issues/3085) | WhatsApp mention-mode ignores typed @mentions | — |
| **HIGH** | [#3643](https://github.com/nanocoai/nanoclaw/issues/3643) | Hardcoded 30-min container kill on local models | #3646 |
| **HIGH** | [#2997](https://github.com/nanocoai/nanoclaw/issues/2997) | Recurring reminders with static text silently stop | — |
| **HIGH** | [#3105](https://github.com/nanocoai/nanoclaw/issues/3105) | WhatsApp-cloud upgrade stranding messaging_groups | — |
| **MEDIUM** | [#3001](https://github.com/nanocoai/nanoclaw/issues/3001) | Pre-refactor agent groups keep stale skill copies | — |
| **MEDIUM** | [#3248](https://github.com/nanocoai/nanoclaw/issues/3248) | `setup.sh` Node-version-too-old branch is broken | — |
| **MEDIUM** | [#2868](https://github.com/nanocoai/nanoclaw/issues/2868) | `/update-skills` silent no-op on installed channels | — |
| **MEDIUM** | [#3694](https://github.com/nanocoai/nanoclaw/issues/3694) | Slack `add-slack` omits file, breaks build | — |
| **LOW** | [#3426](https://github.com/nanocoai/nanoclaw/issues/3426) | `send_card` drops callback buttons, misleading docs | #3427 |
| **LOW** | [#2464](https://github.com/nanocoai/nanoclaw/issues/2464) | CLI silently overrides explicit `--agent-group-id` | — |

**Closed bugs today:** The 41 closed issues include numerous automated merge-forward failure reports for skill branches (#892, #893, #895–#898, #1066, #1073–#1279). These are infrastructure noise rather than user-facing bugs, but they indicate ongoing friction in the skill branch merge workflow.

**Regression risk:** Issue #3105 describes a silent regression on upgrade with no migration path. Issue #2868 compounds this by making the remediation step (`/update-skills`) ineffective.

## 6. Feature Requests & Roadmap Signals

**Active feature/skill PRs:**

- **#2317** — *`/add-voice-transcription-free-whisper` skill* — Adds local voice transcription via openai-whisper or whisper.cpp backends. This signals demand for privacy-preserving, cost-free voice input. ([link](https://github.com/nanocoai/nanoclaw/pull/2317))
- **#2634** — *`add-paws4claws` skill* — Integrates an AWS credential proxy daemon, indicating interest in managed cloud credential handling for operator workloads. ([link](https://github.com/nanocoai/nanoclaw/pull/2634))
- **#3693** — *Signal: queue outbound sends while disconnected; forward voice audio without transcription* — Improves Signal resilience and adds raw voice forwarding capability. ([link](https://github.com/nanocoai/nanoclaw/pull/3693))
- **#3591, #3586, #3588, #3584, #3585, #3581** — *Provider contract refactor* — A systematic restructuring of provider abstractions across Codex, OpenCode, host, and runtime providers, suggesting a roadmap toward pluggable, contract-based provider architecture. ([links](https://github.com/nanocoai/nanoclaw/pull/3591))

**Roadmap prediction:** The next release is likely to include the Signal queue improvement (#3693), the voice transcription skill (#2317), and the initial provider contract refactor merges. The configurable sweep timeout (#3646) is also a strong candidate for inclusion, given its high-severity classification and direct user impact.

## 7. User Feedback Summary

**Pain points surfaced in issues:**

- **WhatsApp group engagement is unreliable.** Issue #3085 and #3105 both describe silent message loss — one on fresh installs (mention detection), one on upgrades (instance re-keying). Users depend on WhatsApp as a primary channel; these failures erode trust.
- **Local-model users are blocked by hardcoded limits.** Issue #3643 explicitly calls out the lack of a configuration seam, forcing users into either accepting mid-turn kills or patching the source. This is a common friction point for self-hosted AI deployments.
- **Recurring tasks are fundamentally broken for static-content reminders.** Issue #2997 affects any user relying on cron-like agent behavior with unchanged message bodies — a core personal-assistant use case.
- **Skill installation and updates are fragile.** Issues #2868, #3001, and #3694 all describe scenarios where following documented procedures produces a broken state. The merge-forward failures (#892–#1279) suggest the skill branch workflow needs operational attention.
- **CLI behavior is confusing.** Issue #2464 reports silent override of explicit CLI arguments, which operators interpret as a bug rather than a design choice.

**Satisfaction signals:** The merged PRs for Slack skills in-tree delivery (#3695), automated PR templates, and release-note harvesting indicate the maintainers are responsive to contributor workflow concerns. The open Signal PR (#3693) and voice transcription skill (#2317) show continued investment in channel reliability and multimodal input.

## 8. Backlog Watch

**Issues requiring maintainer attention:**

1. **#3085** (OPEN, HIGH) — WhatsApp mention detection. No fix PR yet. This is a first-order correctness issue for the WhatsApp channel.
2. **#2997** (OPEN, HIGH) — Recurring task deduplication bug. No fix PR. Affects any agent using scheduled reminders with static text.
3. **#3105** (OPEN, HIGH) — WhatsApp-cloud upgrade migration gap. No fix PR. Users upgrading are silently muted with no recovery documented.
4. **#3001** (OPEN, MEDIUM) — Stale skill copies in pre-refactor agent groups. No fix PR. Affects users who created groups before 2026-04-21.
5. **#3248** (OPEN, MEDIUM) — `setup.sh` cannot upgrade old Node installations. The error-handling branch is non-functional, leaving users stuck on incompatible Node versions.
6. **#2868** (CLOSED) — Though closed, the underlying problem of silent no-op skill updates may resurface until the `/update-skills` logic is corrected.

**PRs needing review/merge:**

- **#3646** (OPEN) — Configurable sweep timeout. Directly addresses #3643; high priority for local-model users.
- **#3693** (OPEN) — Signal disconnect queuing and voice forwarding. Small, scoped, and improves channel resilience.
- **#3691** (OPEN) — Git fixture isolation for tests. Low risk, improves CI reliability.

**Overall project health:** The project demonstrates strong contributor engagement and maturing development processes (automated labels, PR templates, changelog harvesting). However, the open high-severity bug backlog — particularly around message reliability and task scheduling — poses a risk to production stability. The maintainer team should prioritize resolving #3085, #2997, and #3105 before cutting the next release.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-09-01

---

## 1. Today's Overview

NullClaw shows minimal activity on 2026-09-01, with no issues or merged PRs updated in the last 24 hours. The only recent movement is a single open Dependabot pull request (#956) updating the Alpine Docker base image from 3.23 to 3.24. No new releases were published. The project appears to be in a low-activity maintenance phase, with automated dependency updates being the sole contributor-driven effort.

## 2. Releases

No new releases were published. The repository currently has no latest release on record.

## 3. Project Progress

- **Merged/Closed PRs today:** 0
- The only PR with recent activity is **#956** ([dependabot[bot] · ci(deps): bump alpine from 3.23 to 3.24](https://github.com/nullclaw/nullclaw/pull/956)), opened on 2026-06-15 and last updated on 2026-08-31. It remains **open** and has not been merged or closed. No feature development or bug fixes were advanced in the reporting window.

## 4. Community Hot Topics

No issues or PRs with significant community engagement were reported today. The sole PR (#956) has **0 reactions** and **no comments**, indicating low community visibility for this routine dependency bump. No hot topics to analyze.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported today. With zero new or updated issues, there is no new stability signal to assess.

## 6. Feature Requests & Roadmap Signals

No feature requests or roadmap-related issues were raised in the last 24 hours. The Dependabot PR (#956) signals only routine infrastructure maintenance, not user-driven feature demand.

## 7. User Feedback Summary

No user feedback was captured in the reporting window. With no issues or PR comments, it is not possible to assess satisfaction, pain points, or use cases at this time.

## 8. Backlog Watch

- **PR #956** ([ci(deps): bump alpine from 3.23 to 3.24](https://github.com/nullclaw/nullclaw/pull/956)) — Open since **2026-06-15** with the last update on **2026-08-31**. This Dependabot-managed PR has been pending for approximately **two months** without review or merge, which may indicate limited maintainer bandwidth. While low-risk, an unmerged Alpine upgrade could leave Docker images on a slightly older base.

---

**Health Assessment:** NullClaw is currently in a quiet maintenance period. Automated dependency updates are the only active signal, and the absence of contributor engagement over an extended window suggests the project may benefit from renewed maintainer visibility or a call for community participation.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-01

## 1. Today's Overview

IronClaw is showing strong daily activity with **14 issues** and **20 PRs** updated in the last 24 hours, indicating an active development cadence across WebUI, LLM tooling, and CI pipelines. Three PRs were merged today (loop termination fix, MCP catalog truncation, CI coverage stabilization), while the Design System epic (Phases 2–3) drove the most merged code. No new releases were published. The project is in a **solid health state** — multiple critical bugs have open fix PRs, and the design-system refactoring is progressing through clearly phased milestones.

## 2. Releases

**No new releases** were published today.

## 3. Project Progress

**Merged/Closed today (3 PRs):**

- **#7977** [CLOSED] — *fix(loop): terminate on dominant repeated output, cap interactive wall clock* — Closes a critical regression (from PR #7531) where the agent loop ran for 70+ minutes with 593 tool calls and zero progress due to a missing non-progress terminator. [PR Link](https://github.com/nearai/ironclaw/pull/7977)
- **#7964** [CLOSED] — *fix(mcp): a large tool catalog publishes zero tools instead of truncating* — Hosted-MCP discovery previously treated resource ceilings as validity checks, discarding the entire catalog when a single tool exceeded limits. Now properly truncates. [PR Link](https://github.com/nearai/ironclaw/pull/7964)
- **#7995** [CLOSED] — *fix(ci): stabilize main branch coverage checks* — Resolves stale `approval_required` Inbox notifications and isolates Railway sandbox tests from transient network allowlist overrides. [PR Link](https://github.com/nearai/ironclaw/pull/7995)

**Features advanced today (open PRs):**
- **#8010** — Session-event transport unification with web-app run-completion notifications (unified typed WebSocket + durable notices)
- **#8006** — Durable progressive replies and native Slack Agent UI
- **#7994** — `DESIGN.md` governance document and Storybook design-system guidelines (Epic #7781 Phase 2)
- **#8011** — M3 reskin: new palette (`#6b4eff` / `#00e5ff` / `#ff4e9e`), M3 tonal steps in OKLab, shim retirement

## 4. Community Hot Topics

- **Epic #7781: Design System Phases 2–3** — *2 comments, actively updated today* — Tracks `DESIGN.md` governance + M3 reskin. The project is reorganizing its 5-phase design-system program into clearly delineated epics (#7038 Phase 1 done, #7781 Phases 2–3 in progress, #7782 Phases 4–5 planned). [Issue Link](https://github.com/nearai/ironclaw/issues/7781)

- **Issue #8012: 47k-tool MCP catalog — zero tools reachable via `tool_search`** — *Created today, 0 comments* — A hosted MCP catalog of 47,337 tools ingests fully but no tool is ever found by `tool_search`; the same catalog at 2,000 tools works. Indicates a scaling bottleneck in search indexing. [Issue Link](https://github.com/nearai/ironclaw/issues/8012)

- **Issue #7892 (CLOSED): Deferred tool found 15x, never invoked — 123s run** — *0 comments, closed today* — The model repeated the same 4 distinct capability calls 31 times across runs of 79s, 86s, and 123s with no terminating guard. Closed by PR #7977. [Issue Link](https://github.com/nearai/ironclaw/issues/7892)

- **Issue #8009: MCP egress errors flatten to `"response_error"`** — *Created today* — Discovery failures are undiagnosable because all `RuntimeHttpEgressError` variants collapse to a single reason token. [Issue Link](https://github.com/nearai/ironclaw/issues/8009)

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Description |
|----------|-------|--------|-------------|
| 🔴 Critical | [#7987](https://github.com/nearai/ironclaw/issues/7987) | [#7999](https://github.com/nearai/ironclaw/pull/7999) [OPEN] | `flatten_top_level` rebuilds tool schemas from a whitelist, silently discarding all non-forbidden top-level constraints (e.g., `dependentRequired`, `$defs`, `minProperties`). |
| 🔴 Critical | [#8012](https://github.com/nearai/ironclaw/issues/8012) | — | 47k-tool MCP catalog ingests fully but `tool_search` finds nothing — scale-dependent indexing regression. |
| 🟠 High | [#8008](https://github.com/nearai/ironclaw/issues/8008) | [#7964](https://github.com/nearai/ironclaw/pull/7964) [CLOSED] | Hosted-MCP discovery: a single leak-blocked `tools/list` page discards the entire catalog. (Fix merged.) |
| 🟠 High | [#8009](https://github.com/nearai/ironclaw/issues/8009) | — | MCP egress errors flatten to `"response_error"`, making discovery failures impossible to diagnose. |
| 🟠 High | [#7986](https://github.com/nearai/ironclaw/issues/7986) | [#7996](https://github.com/nearai/ironclaw/pull/7996) [OPEN] | `github.list_repos` ships 81 raw fields per repo (519 KB for 98 repos); projection seam is unused. |
| 🟡 Medium | [#7984](https://github.com/nearai/ironclaw/pull/7984) [OPEN] | — | `tool_search` reply sized to independent budget instead of first-look envelope — 10-hit reply serializes to 16 KB but model sees only 857 B with entire `results` array replaced by `omitted`. |
| 🟡 Medium | [#7890](https://github.com/nearai/ironclaw/issues/7890) | — | `app.css` Tailwind colour-alias compat layer (~100 lines with `!important`) should be retired before WS3 reskin. |

## 6. Feature Requests & Roadmap Signals

- **Epic #7782 (Phases 4–5)** — *Agentic interactions, components & information architecture* — The final wave of the five-phase design-system program, still open. Signals continued WebUI polish expected in upcoming releases. [Issue Link](https://github.com/nearai/ironclaw/issues/7782)
- **#7890: Retire `app.css` Tailwind compat layer** — Removing legacy `--v2-*` token remapping ahead of the WS3 reskin. Should ship with the M3 reskin in the next minor release.
- **#8006: Durable progressive replies + Slack Agent UI** — New channel capability for native Slack integration with bounded `ReplyDocument` types. Likely a v1.4.0 feature.
- **#7997 (CLOSED): Model capability icons across Inference** — Icon-only Text/Image input/output indicators with hover descriptions and accessible labels. Merged; will appear in next release. [PR Link](https://github.com/nearai/ironclaw/pull/7997)
- **#7998: NEAR AI model capabilities through discovery** — Provider-neutral model catalog entry + additive `list_model_catalog()` API. Merged; likely in next release. [PR Link](https://github.com/nearai/ironclaw/pull/7998)

## 7. User Feedback Summary

- **MCP catalog search failure at scale** (Issue #8012): Users can ingest massive tool catalogs but cannot search them — a fundamental gap between ingestion and discoverability that limits the hosted-MCP value proposition.
- **Agent loop stuck in repetition** (Issue #7892, closed): Three production runs burned up to 123 seconds with the model repeating the same calls 15×. The closure via PR #7977 is a relief, but users will want confirmation the fix is stable in production.
- **Silent constraint loss in tool schemas** (Issue #7987): Schema flattening silently discards constraints like `$defs` and `dependentRequired` — a correctness issue that could produce wrong tool behavior for downstream providers.
- **MCP error opacity** (Issues #8008, #8009): Discovery failures are either all-or-nothing or collapse to a single `"response_error"` token, making troubleshooting extremely difficult for operators running hosted MCP servers.
- **GitHub API bloat** (Issue #7986 / PR #7996): Users are feeling the 519 KB per-repo cost; the fix PR is open and ready for review.

Overall satisfaction appears **moderate** — critical bugs are being addressed quickly (3 merges today), but several high-severity issues lack closed fixes, and the MCP tool-search scalability problem remains unresolved.

## 8. Backlog Watch

| Issue | Days Open | Priority | Why It Needs Attention |
|-------|-----------|----------|----------------------|
| [#7987](https://github.com/nearai/ironclaw/issues/7987) — Tool schema constraint loss | ~4 days | Critical | Fix PR #7999 is open but unmerged; silently discarding schema constraints is a correctness bug. |
| [#8012](https://github.com/nearai/ironclaw/issues/8012) — 47k catalog, zero searchable tools | <1 day (today) | Critical | New report, no fix yet; blocks large-scale MCP use. |
| [#8009](https://github.com/nearai/ironclaw/issues/8009) — MCP egress error flattening | <1 day (today) | High | No fix yet; operators cannot diagnose MCP failures. |
| [#8008](https://github.com/nearai/ironclaw/issues/8008) — Leak-blocked page kills catalog | ~1 day | High | Fix merged (#7964), but verify the fix handles all leak-detector edge cases. |
| [#7986](https://github.com/nearai/ironclaw/issues/7986) — GitHub `list_repos` 81-field payload | ~4 days | Medium | Fix PR #7996 is open; low risk but unmerged. |
| [#7890](https://github.com/nearai/ironclaw/issues/7890) — Retire `app.css` compat layer | ~7 days | Medium | Prerequisite for M3 reskin; PR #8011 is in progress but this cleanup should be confirmed. |
| [#8004](https://github.com/nearai/ironclaw/issues/8004) — Daily failure taxonomy | 1 day | Low | Automated tracking issue; useful for trend monitoring, no action required. |

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-01

## 1. Today's Overview

LobsterAI shows **active maintenance** with 11 issues and 27 PRs updated in the last 24 hours. The project is currently **stale-cleaning**: 6 of 11 closed issues carry the `[stale]` label, indicating automated purging of long-dormant tickets rather than active resolution. No new releases were published today. Developer activity is concentrated on **dependency bumps** (via Dependabot) and **security hardening** of MCP command handling. One new critical bug (#2577) and one pricing-related complaint (#2589) were opened today, both awaiting response.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged / Closed PRs today:**
- **#2588** — Liuzhq/user guide (closed) · Documentation update
- **#2462** — `mermaid` bumped 10.9.8 → 11.16.1 (closed) · Dependency upgrade
- **#2465** — `vite` bumped 5.4.21 → 8.2.1 (closed) · Major Vite upgrade
- **#2463** — `@vitejs/plugin-react` bumped 4.7.0 → 6.0.5 (closed) · React plugin upgrade
- **#2164** — `trufflehog` bumped 3.88.30 → 3.95.5 (closed) · Security scanner update
- **#2458** — `@types/react-dom` bumped 18.3.7 → 19.2.4 (closed) · Type definition upgrade
- **#2167** — `actions/stale` bumped 9.1.0 → 10.3.0 (closed) · CI stale-action update
- **#2165** — `actions/checkout` bumped 4 → 6 (closed) · CI checkout action update

**Open PRs of note:**
- **#2590** — Security hardening for MCP stdio commands and external URL boundaries (open)
- **#2587** — `mermaid` bump to 11.17.2 (open)
- **#2585** — DSH reasoning-effort metadata sync for LobsterAI models (open)
- **#2586 / #2584 / #2583 / #2582 / #2581 / #2580 / #2579** — Ongoing Dependabot dependency bumps

## 4. Community Hot Topics

| Issue / PR | Type | Comments | Summary |
|---|---|---|---|
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | Feature | 2 | Cross-agent awareness via Markdown-driven workflows |
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | Bug | 3 | `groupPolicy` being overwritten to `allowlist` |
| [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | Bug | 2 | Ollama local models unusable despite working in CherryStudio |
| [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | Feature | 1 | Keyboard shortcuts for tool-permission modal (Enter/Esc) |
| [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) | Feature | 1 | One-click Retry after session errors |
| [#2589](https://github.com/netease-youdao/LobsterAI/issues/2589) | Bug | 0 | Plan mode draining 200 credits — user frustration |

**Analysis:** Users consistently need **better keyboard workflows** (#1117) and **session recovery** (#1120), indicating the Cowork permission modal and error states are friction points for power users. The cross-agent awareness request (#1644) reflects a growing demand for multi-agent orchestration beyond LobsterAI's current isolated agent model.

## 5. Bugs & Stability

**Open bugs ranked by severity:**

| # | Severity | Description | Fix PR? |
|---|---|---|---|
| [#2577](https://github.com/netease-youdao/LobsterAI/issues/2577) | **High** | DSH built-in workspace cannot adjust reasoning effort for LobsterAI-synced models | [#2585](https://github.com/netease-youdao/LobsterAI/pull/2585) (open) |
| [#2589](https://github.com/netease-youdao/LobsterAI/issues/2589) | **Medium** | Plan mode deducting 200 credits per session — pricing/UX concern | None yet |
| [#1124](https://github.com/netease-youdao/LobsterAI/issues/1124) | **Medium** | "Lobster AI cannot close" dialog persists after logout and reinstall | None yet |
| [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) | **Low** | False "unsaved content" warning when saving scheduled tasks (v4.8 / Win11) | None yet |
| [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) | **Low** | MD→Word conversion fails mid-process with `sse response finish reason: full` | None yet |

**Security note:** PR [#2590](https://github.com/netease-youdao/LobsterAI/pull/2590) directly addresses MCP stdio command injection and URL validation — a potential precursor to resolving [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) (non-SSE MCP engines unusable).

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for Next Release |
|---|---|---|
| Keyboard shortcuts for Cowork permission modal | [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | **High** — low-effort UX win |
| One-click Retry after session error | [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) | **High** — clear pain point, well-scoped |
| Reasoning-effort control for LobsterAI models in DSH | [#2585](https://github.com/netease-youdao/LobsterAI/pull/2585) | **Very High** — PR already open, directly tied to #2577 |
| Cross-agent awareness / MD-based workflows | [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | **Low** — significant architecture change |
| Tool-permission modal keyboard support (destructive ops safe) | [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | **High** — complements the above |

## 7. User Feedback Summary

- **Frustration with credit billing:** Issue #2589 reflects genuine user anger over plan-mode credit consumption ("you guys don't expect a repeat customer!"). This needs a timely public response to avoid reputational damage.
- **DSH integration gaps:** Users syncing models via LobsterAI lose features (thinking strength) available when adding providers manually. This inconsistency erodes trust in the integration layer.
- **Ollama compatibility gaps:** Issue #1635 shows LobsterAI's Ollama integration lags behind alternative clients (CherryStudio), suggesting the MCP/transport layer needs attention.
- **Stale issue accumulation:** Multiple issues from April 2026 are being auto-closed as stale, indicating the team lacks bandwidth for older tickets rather than resolving them — a signal of resource constraints.

## 8. Backlog Watch

| Issue / PR | Age | Priority | Concern |
|---|---|---|---|
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) — Non-SSE MCP engines unusable | ~5 months | **High** | Core functionality broken for a significant MCP transport type |
| [#908](https://github.com/netease-youdao/LobsterAI/pull/908) — MCP stdio command injection fix | ~5 months | **Critical** | Unmerged security PR; superseded in part by #2590 but still the authoritative fix |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron 40→44 bump | ~5 months | **Medium** | Major framework upgrade stuck in stale limbo |
| [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) — Permission modal keyboard shortcuts | ~5 months | **Medium** | High-value UX improvement, long-pending |
| [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) — Session Retry button | ~5 months | **Medium** | High-value UX improvement, long-pending |
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) — Cross-agent workflow via Markdown | ~5 months | **Low** | Ambitious feature, needs architectural planning |

**Key takeaway:** The project is in a **maintenance and security-hardening phase**. Dependency updates are flowing steadily, and one critical security PR (#2590) has been opened to address MCP injection risks. However, the backlog of 5-month-old issues and the unmerged #908 suggest the team is prioritizing active development over backlog triage. The credit-billing complaint (#2589) requires urgent community management attention.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-01

## 1. Today's Overview

Moltis shows moderate daily activity with 2 updated issues and 4 updated pull requests in the last 24 hours, alongside a new release (`20260831.01`). The project is actively addressing both security hardening (Snyk pinning, sandbox image validation) and developer-experience fixes (Docker locality, explicit null node selection). One new feature request for Kubernetes-native sandbox backends remains open and unaddressed since June, signaling a potential gap between community demand and maintainer capacity. Overall project health appears stable with no critical regressions flagged.

---

## 2. Releases

**20260831.01** (released 2026-08-31)
- Changelog details not provided in source data. The release coincides with the merge of PRs #1221, #1222, and #1248, suggesting it likely includes security scan pinning, sandbox image validation, and the null node selection fix. No explicit breaking changes were noted.

---

## 3. Project Progress

| PR | Status | Description |
|----|--------|-------------|
| [#1248](https://github.com/moltis-org/moltis/issues/1248) | ✅ Merged | Fix: honor explicit `node: null` for local execution path |
| [#1221](https://github.com/moltis-org/moltis/pull/1221) | ✅ Merged | Fix: pin Snyk Agent Scan to v0.5.17, remove `mcp-scan` fallback |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | ✅ Merged | Fix: validate sandbox image requests, restrict package checks to operators |
| [#1249](https://github.com/moltis-org/moltis/pull/1249) | 🔵 Open | Fix: treat Docker loopback-only deployments as local connections |

Three security- and correctness-oriented fixes landed today. The only open PR (#1249) targets a Docker networking edge case that breaks local-dev convenience auth — likely to merge soon given its narrow scope.

---

## 4. Community Hot Topics

- **[Issue #1118](https://github.com/moltis-org/moltis/issues/1118)** — *Add Kubernetes-native sandbox backend with runtimeClassName support*
  - Open since 2026-06-12, 3 comments, 1 👍
  - Requests ephemeral Kubernetes pods for agent command execution with VM-level isolation (Kata Containers, gVisor, OCI runtimes).
  - **Signal:** Strong community interest in portable, cloud-native sandboxing. The gap between this request and the recent Docker/web sandbox hardening PRs suggests maintainers are prioritizing immediate security fixes over infrastructure expansion.

No other issues/PRs today carry significant engagement metrics.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|----------|----------|-------------|------------|
| 🟡 Medium | [#1246](https://github.com/moltis-org/moltis/issues/1246) | Can't run on sandbox after a node is added | ✅ Closed (2026-08-31) |
| 🟢 Low | [#1112](https://github.com/moltis-org/moltis/issues/1112) *(referenced in #1249)* | Docker bridge networking breaks `is_local_connection()` auth gate | 🔵 PR #1249 open |

No crashes or regressions reported. The #1246 bug (sandbox unusable post-node-add) appears resolved. The Docker locality issue (#1112 / #1249) is tracked but not yet merged.

---

## 6. Feature Requests & Roadmap Signals

- **[Issue #1118](https://github.com/moltis-org/moltis/issues/1118)** — Kubernetes-native sandbox backend with `runtimeClassName` support. This is the only open feature request in the current window and has been pending since June. Given Moltis's focus on sandbox isolation (evidenced by PRs #1221 and #1222), a K8s sandbox backend would align well with the security trajectory and is a strong candidate for the next release cycle.

---

## 7. User Feedback Summary

- **Pain point — Docker locality detection:** Users running Moltis in Docker report that `auth_disabled` / Tier 2 local-dev convenience fails because bridge networking rewrites the TCP source IP away from loopback. This blocks the expected local-development workflow ([#1112](https://github.com/moltis-org/moltis/issues/1112) → [PR #1249](https://github.com/moltis-org/moltis/pull/1249)).
- **Pain point — Sandbox broken after node addition:** A reported bug (#1246) made the sandbox unusable once a node provider was added; now closed, suggesting resolution.
- **Positive signal — Security hardening appreciated:** The community benefits from pinned Snyk scans and validated sandbox images, reducing supply-chain and image-injection attack surfaces.

---

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [#1118](https://github.com/moltis-org/moltis/issues/1118) — K8s sandbox backend | ~3 months open, 1 👍 | Feature backlog gap; high community interest but no maintainer response yet |
| [#1249](https://github.com/moltis-org/moltis/pull/1249) — Docker locality fix | Open 1 day | Low risk, small scope; likely merge-ready |

**Recommendation:** The three-month gap on #1118 warrants a maintainer triage. The Docker locality fix (#1249) should be reviewed and merged promptly to unblock local-dev workflows.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-01

## 1. Today's Overview
The QwenPaw project shows **very high activity** on 2026-09-01, with 29 issues updated and 39 pull requests updated in the last 24 hours. Two beta releases (v2.2.0-beta.4 and v2.2.0-beta.5) landed today, focusing on memory system stability, channel contract portability, and desktop/browser SDK fixes. Open‑issue count remains elevated (15 active), with several medium‑severity bugs reported for the new beta. The project is in a pre‑release stabilization phase for the upcoming v2.2.0 suite.

## 2. Releases
### v2.2.0‑beta.5 ([Release page](https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.2.0-beta.5))
**What's Changed**
- `fix(channels)`: make contract checks portable and complete ([#7267](https://github.com/agentscope-ai/QwenPaw/pull/7267))
- `fix(memory)`: make embedding reindex explicit and scoped ([#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133))
- `chore`: bump the version ([#7438](https://github.com/agentscope-ai/QwenPaw/pull/7438))

### v2.2.0‑beta.4 ([Release page](https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.2.0-beta.4))
**What's Changed**
- `fix(context)`: bound oversized single‑line tool results ([#7331](https://github.com/agentscope-ai/QwenPaw/pull/7331))
- `test(agent‑stats)`: align TC‑AGT‑06 with current agent scope ([#7021](https://github.com/agentscope-ai/QwenPaw/pull/7021))
- `fix(desktop)`: unify … (truncated in source data)

**Breaking Changes / Migration Notes**
- Both releases are **beta pre‑releases**; API contracts for channels and memory may change before final v2.2.0.
- Memory reindex is now an **explicit, scoped operation**—users must manually trigger rebuild after switching embedding spaces ([#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133)).
- Desktop bundles now ship a fixed OpenSSL 3.0.x‑era TLS stack; carriers that reset handshakes may see improved compatibility ([#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298)).

## 3. Project Progress
**Merged / Closed PRs Today** (16 total)
- `fix(channels)`: portable contract checks ([#7267](https://github.com/agentscope-ai/QwenPaw/pull/7267))
- `fix(memory)`: explicit embedding reindex ([#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133))
- `fix(context)`: bound oversized tool results ([#7331](https://github.com/agentscope-ai/QwenPaw/pull/7331))
- `fix(pack)`: bundle `reme-ai` Python core in PyInstaller onedir ([#7453](https://github.com/agentscope-ai/QwenPaw/pull/7453))
- `fix(browser)`: Chrome extension tab‑group reuse ([#7457](https://github.com/agentscope-ai/QwenPaw/pull/7457))
- `fix(e2e)`: re‑anchor approval‑level toggle selectors ([#7456](https://github.com/agentscope-ai/QwenPaw/pull/7456))
- `ci`: cut per‑PR concurrency to avoid GitHub‑hosted queue starvation ([#7435](https://github.com/agentscope-ai/QwenPaw/pull/7435))
- `test(console)`: expand unit tests (+617 cases, +10.61pp coverage) ([#7452](https://github.com/agentscope-ai/QwenPaw/pull/7452))
- `test(integration)`: coverage sprint batch 6 (314 cases) ([#7451](https://github.com/agentscope-ai/QwenPaw/pull/7451))
- `fix(console)`: revive dead dark‑mode overrides and rename Marketplace … ([#7454](https://github.com/agentscope-ai/QwenPaw/pull/7454))
- `fix`: save screenshots in active project directory ([#7439](https://github.com/agentscope-ai/QwenPaw/pull/7439))
- `feat(memory)`: unify ReMe slash commands ([#7444](https://github.com/agentscope-ai/QwenPaw/pull/7444))
- `feat(memory)`: add Auto Fin and upgrade ReMe to 0.4.1.11 ([#7441](https://github.com/agentscope-ai/QwenPaw/pull/7441))
- `test(providers)`: regression guard for Aliyun Coding Plan catalog alignment ([#7390](https://github.com/agentscope-ai/QwenPaw/pull/7390))
- `docs(intro)`: add Access Policy to security mechanisms ([#7440](https://github.com/agentscope-ai/QwenPaw/pull/7440))
- `chore`: bump version to 2.2.0b5 ([#7438](https://github.com/agentscope-ai/QwenPaw/pull/7438))

**Key Advancements**
- **Memory system** made more explicit and stable (reindex scoping, Auto Fin integration, ReMe upgrade).
- **Console/frontend** coverage and dark‑mode fixes improve user‑experience reliability.
- **Browser SDK** now reuses existing tab groups, addressing a resource‑leak pattern.
- **CI concurrency** tuned to prevent GitHub‑hosted runner starvation.

## 4. Community Hot Topics
| Issue / PR | Activity | Link |
|------------|----------|------|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) — QwenPaw Hub multi‑tenant edition roadmap discussion | 15 comments, 2 👍 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7318) |
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) — Desktop/Docker TLS stack carrier‑DPI resets | 9 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7298) |
| [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) — Tool results lost after `write_file` triggers doom‑loop | 8 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7420) |
| [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) — Console stream duplicated text chunks mid‑stream | 5 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7417) |
| [#7377](https://github.com/agentscope-ai/QwenPaw/issues/7377) — Agent Loop mode not persisted across task runs | 5 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7377) |

**Underlying Needs**
- Strong community demand for a **multi‑tenant Hub edition** (team/admin workflows).
- **Carrier/DPI compatibility** remains a pain point for desktop and Docker deployments.
- **Agent loop reliability** and **context‑window management** are critical for complex, long‑running tasks.

## 5. Bugs & Stability
| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **High** | [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | Tool results lost; agent re‑dispatches same command, hitting doom‑loop protection. | None yet |
| **High** | [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) | Long context leads to sudden loss of early history, task cannot continue. | None yet |
| **High** | [#7446](https://github.com/agentscope-ai/QwenPaw/issues/7446) | “Rebuild Memory Index” returns 500 (`ReMe instance is None`). | [#7453](https://github.com/agentscope-ai/QwenPaw/pull/7453) |
| **Medium** | [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Console stream shows large duplicated text chunks, then consolidated copy. | None yet |
| **Medium** | [#7377](https://github.com/agentscope-ai/QwenPaw/issues/7377) | Agent Loop mode reverts to default after task completion. | None yet |
| **Medium** | [#7397](https://github.com/agentscope-ai/QwenPaw/issues/7397) | Browser SDK spawns a new tab‑group per `open()`/`present()` call. | [#7457](https://github.com/agentscope-ai/QwenPaw/pull/7457) |
| **Medium** | [#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363) | Synchronous calls freeze event loop; timeout never fires. | None yet |
| **Medium** | [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | Codex‑based third‑party agent returns empty responses, usage 0. | None yet |
| **Low** | [#7419](https://github.com/agentscope-ai/QwenPaw/issues/7419) | Step accordion collapses all messages of a turn, not only consecutive tool‑call runs. | Closed |
| **Low** | [#7407](https://github.com/agentscope-ai/QwenPaw/issues/7407) | Console messages silently drift to wrong agent. | Closed |

**Trend**: Several medium‑high severity bugs surface in the v2.2.0 beta series, particularly around **agent loop stability**, **context retention**, and **memory‑index reliability**. Fix PRs are already in flight for two of the high‑severity issues.

## 6. Feature Requests & Roadmap Signals
| Request | Issue / PR | Likelihood for v2.2.0 |
|---------|------------|-----------------------|
| `/btw` side‑question command (like Claude Code) | [#7398](https://github.com/agentscope-ai/QwenPaw/issues/7398) | **Medium** – popular pattern, but requires UI integration |
| `tool_call_format` config for compact display in IM channels | [#7436](https://github.com/agentscope-ai/QwenPaw/issues/7436) | **High** – directly follows channel‑contract work; may ship as config toggle |
| Ability to disable built‑in “cloud providers” (Kilo Code, opencode) | [#7455](https://github.com/agentscope-ai/QwenPaw/issues/7455) | **Medium** – aligns with Hub multi‑tenant control; could be added to admin settings |
| Session icon fixed at top when sidebar collapsed | [#7125](https://github.com/agentscope-ai/QwenPaw/issues/7125) | **Low** – minor UI tweak, likely backlogged |
| Workspace‑scoped skill preload configuration | [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | **High** – already in review; matches “trusted core skills” pattern |

**Prediction**: `tool_call_format` config and workspace‑scoped preload are strong candidates for v2.2.0 final; `/btw` may appear in a later patch or as a beta feature.

## 7. User Feedback Summary
**Pain Points**
- **Long startup times** (up to 4 minutes) due to synchronous calls blocking the event loop ([#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363), [#7360](https://github.com/agentscope-ai/QwenPaw/issues/7360)).
- **Context loss** during long sessions, forcing re‑processing of large documents ([#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447)).
- **Tool‑result loss** and **doom‑loop** behavior after `write_file` operations ([#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420)).
- **Channel contract checks** failing on Windows due to encoding issues ([#7264](https://github.com/agentscope-ai/QwenPaw/issues/7264)).
- **Browser SDK** creating new tab groups per call, wasting resources ([#7397](https://github.com/agentscope-ai/QwenPaw/issues/7397)).

**Satisfaction Signals**
- Active engagement with beta releases (v2.2.0‑

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw Project Digest — 2026‑09‑01

## 1. Today’s Overview
ZeptoClaw’s development remains heavily focused on **security hardening** and **dependency remediation**, with eight open issues (all tagged `area:safety` or `chore(deps)`) and one merged pull request closed in the last 24 hours. No new releases were published. Activity is concentrated around patching critical vulnerabilities and enforcing stricter CI checks rather than delivering new features. The project’s health shows a clear, maintainer‑driven pivot toward security‑first hygiene.

## 2. Releases
**No new releases** were published in the reporting window.

## 3. Project Progress
- **PR #657** – `chore(deps): fix 8 RustSec advisories` (closed) merged updates for `h2`, `bcrypt`, `quinn‑proto`, `crossbeam‑epoch`, `anyhow`, `quick‑xml`, and `lopdf`, directly closing issue #651. This advances the dependency‑remediation effort and unblocks the restored `cargo‑deny` CI job (#646).

## 4. Community Hot Topics
- **#644 – Scrub subprocess environments & terminate process trees on timeout** (1 comment)  
  [qhkm/zeptoclaw#644](https://github.com/qhkm/zeptoclaw/issues/644)  
  Highlights a deep‑seated need for secure process isolation when the agent spawns child tasks.

- **#646 – Restore Clippy & cargo‑deny checks on current toolchain** (3 comments)  
  [qhkm/zeptoclaw#646](https://github.com/qhkm/zeptoclaw/issues/646)  
  Shows community engagement around strengthening CI quality gates and keeping dependencies free of known vulnerabilities.

- **#656 – Panel start prints full API token to stdout** (0 comments)  
  [qhkm/zeptoclaw#656](https://github.com/qhkm/zeptoclaw/issues/656)  
  A freshly reported pain point that affects every panel‑startup operator; likely to gain attention quickly.

Underlying need: **operators are demanding that credential‑leak vectors be eliminated** across CLI, API, and subprocess boundaries.

## 5. Bugs & Stability
Ranked by severity (all P1‑critical or `bug(safety)`):

1. **#644** – Subprocess environments inherit the full ZeptoClaw environment and spawned process trees are not terminated/reaped on timeout.  
   [qhkm/zeptoclaw#644](https://github.com/qhkm/zeptoclaw/issues/644)

2. **#656** – `src/cli/panel.rs:221` prints the full API token to stdout on every `zeptoclaw panel start`, leaking into terminal scrollback, CI logs, and screenshots.  
   [qhkm/zeptoclaw#656](https://github.com/qhkm/zeptoclaw/issues/656)

3. **#655** – Static bearer token compared with plain `==` in three places instead of constant‑time comparison.  
   [qhkm/zeptoclaw#655](https://github.com/qhkm/zeptoclaw/issues/655)

4. **#653** – WebSocket auth token passed as a query parameter (`?auth=`), exposing it to access logs, browser history, and telemetry.  
   [qhkm/zeptoclaw#653](https://github.com/qhkm/zeptoclaw/issues/653)

5. **#652** – Secret files (`config.toml`, `panel.token`) written without `0600` permissions.  
   [qhkm/zeptoclaw#652](https://github.com/qhkm/zeptoclaw/issues/652)

6. **#651** – 7 known‑vulnerable RustSec advisories (partially addressed by merged PR #657).  
   [qhkm/zeptoclaw#651](https://github.com/qhkm/zeptoclaw/issues/651)

7. **#646** – CI failures from Clippy warnings and cargo‑deny rejections due to outdated dependencies.  
   [qhkm/zeptoclaw#646](https://github.com/qhkm/zeptoclaw/issues/646)

**Fix PRs:** PR #657 addresses #651; no open PRs yet for the remaining issues.

## 6. Feature Requests & Roadmap Signals
- **#654** – Rate‑limit `POST /api/auth/login` (no lockout; bcrypt cost is the only brake).  
  [qhkm/zeptoclaw#654](https://github.com/qhkm/zeptoclaw/issues/654)  
  Signals a need for robust authentication‑layer security. Likely to be included in a security‑focused next patch release.

No other feature‑request issues appeared today; the roadmap is dominated by safety fixes.

## 7. User Feedback Summary
- **Credential leakage** is the top pain point (stdout token print, insecure file permissions, query‑param auth).
- **Subprocess security** remains a concern for users running untrusted commands.
- **Dependency hygiene** is a recurring theme; the community welcomes the recent CVE remediation but expects CI to stay strict.
- Satisfaction appears **low** on security‑sensitive deployments because multiple basic hardening gaps are still open.

## 8. Backlog Watch
- **#646** (updated 2026‑08‑31) – Still open, awaiting a fix that both restores the `cargo‑deny` job and addresses the new Clippy warnings on Rust 1.97.1.
- **#644** (updated 2026‑08‑31) – No linked PR; the environment‑scrubbing and process‑tree termination logic needs implementation.
- **#652** (updated 2026‑08‑31) – File‑permission hardening is a quick win but remains unaddressed.
- **#653** (updated 2026‑08‑31) – Moving the WebSocket token out of the query string is a straightforward API change pending action.

Maintainer attention should prioritize these four issues to close the current security‑hardening backlog.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026‑09‑01

## 1. Today’s Overview
ZeroClaw shows sustained development momentum with **26 issues** and **50 pull requests** updated in the last 24 hours. All PRs remain open (none merged/closed today), while one issue was closed. The project is heavily focused on architectural RFCs, safety‑hardening, and WASM plugin runtime stability. No new releases were published today.

## 2. Releases
*No new releases today.*

## 3. Project Progress
- **Closed Issue:** `#10497` (pairing‑code lifetime controls) was closed today, following the earlier pairing‑code policy work.
- **No PRs merged/closed** in the past 24 hours; all 50 updated PRs remain open.
- **Enhancement PRs advancing:** Several large‑scale features are in review, including voice‑channel WebSocket bridge (`#9740`), Hailo‑Ollama native provider support (`#9109`), multi‑model per‑provider profiles (`#9809`), and context‑compaction tied to model‑window ratio (`#9535`).

## 4. Community Hot Topics
| Issue | Comments | Focus |
|-------|----------|-------|
| [#9487 – Runtime‑owned conversation sessions & transport adapters](https://github.com/zeroclaw‑labs/zeroclaw/issues/9487) | 29 | RFC defining session ownership boundaries and durable admission semantics. |
| [#6850 – Decouple memory lifecycle from storage backends](https://github.com/zeroclaw‑labs/zeroclaw/issues/6850) | 24 | RFC to separate durable memory storage from higher‑level lifecycle policy. |
| [#9488 – Unified attachment architecture](https://github.com/zeroclaw‑labs/zeroclaw/issues/9488) | 23 | RFC (Rev 9) for a unified attachment system across web chat and channels. |
| [#6996 – Granular sandbox policy](https://github.com/zeroclaw‑labs/zeroclaw/issues/6996) | 18 | RFC to align filesystem/network restrictions across application‑layer and OS sandboxes. |
| [#9103 – Separate authoritative memory from enrichment connectors](https://github.com/zeroclaw‑labs/zeroclaw/issues/9103) | 17 | RFC that preserved the storage/enrichment architecture boundary after maintainer takeover. |
| [#6909 – Computer‑use support for desktop](https://github.com/zeroclaw‑labs/zeroclaw/issues/6909) | 15 | RFC (Rev 2) adding bounded approval units and execution‑time revalidation for desktop interaction. |

**Underlying needs:** The community is driving a clear agenda toward **stronger ownership boundaries** (sessions, memory, attachments), **finer‑grained sandbox controls**, and **desktop/computer‑use capabilities**. Many of these RFCs have been in discussion for months, indicating deep architectural debates that are now nearing resolution.

## 5. Bugs & Stability
| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **P0** | [#10495 – Config::save() can replace populated config with near‑empty file](https://github.com/zeroclaw‑labs/zeroclaw/issues/10495) | Data‑loss/security risk; workspace test run overwrote a 109 KB config with a 702‑byte file. | `#10521` (honor `ZEROCLAW_CONFIG_DIR`), `#10498` (refuse unsafe bare‑path overwrites) – both open. |
| **P1** | [#10513 – RPC `sops.run` returns run ID for a step nothing will execute](https://github.com/zeroclaw‑labs/zeroclaw/issues/10513) | Missing driver sink; run ID returned but no execution proceeds. | None yet. |
| **P1** | [#9850 – llm_task builds provider via legacy factory, losing alias‑specific config](https://github.com/zeroclaw‑labs/zeroclaw/issues/9850) | Azure/OAuth/requires_openai_auth config lost because legacy factory is used. | None yet. |
| **P1** | [#10501 – MCP tool‑result images 400 on OpenAI‑compatible providers](https://github.com/zeroclaw‑labs/zeroclaw/issues/10501) | Image part placed inside `role: "tool"` message, which providers reject. | `#10448` (adds compatible tool‑result image policy) – open. |
| **P2** | [#10523 – Bootstrap file truncation at 6000 chars is invisible](https://github.com/zeroclaw‑labs/zeroclaw/issues/10523) | `compact_context` truncates workspace bootstrap files without operator notification. | None yet. |
| **P2** | [#10505 – Plugin instantiation fails on WIT version skew](https://github.com/zeroclaw‑labs/zeroclaw/issues/10505) | Cryptic “no matching implementation in the linker” when host/world version drifts. | None yet. |
| **P2** | [#10506 – Sequential wasi:http requests intermittently fail](https://github.com/zeroclaw‑labs/zeroclaw/issues/10506) | Stale‑connection errors inside a single plugin invocation; batching avoids the issue. | None yet. |

**Stability note:** The P0 config‑overwrite bug is critical and has two open fix‑oriented PRs that may address different aspects. WASM plugin runtime issues (#10505, #10506) suggest ongoing integration‑test gaps with the Component Model.

## 6. Feature Requests & Roadmap Signals
- **RFCs (open, high‑risk/priority):**  
  - `#9487` – Runtime‑owned conversation sessions  
  - `#6850` – Memory‑lifecycle decoupling  
  - `#9488` – Unified attachment architecture  
  - `#6996` – Granular sandbox policy  
  - `#9103` – Separate authoritative memory from enrichment connectors  
  - `#6909` – Computer‑use desktop support  
  - `#10076` – Composable WASM plugin runtime architecture  
  - `#10222` – Opt‑in single‑tool provider rounds for interactive agents  

- **Enhancement PRs in flight:**  
  - `#9740` – VoiceHost WebSocket bridge  
  - `#9109` – Native Hailo‑Ollama provider  
  - `#9809` – Multiple models per provider profile  
  - `#9535` – Context compaction anchored to model‑window ratio  
  - `#10351` – Execution‑tree iteration budgets  

**Prediction:** The next release will likely include the **WASM plugin runtime architecture** (#10076), **context‑compaction improvements** (#9535), and **multi‑model provider profiles** (#9809). The computer‑use RFC (#6909) and granular sandbox policy (#6996) are advanced enough to enter a release candidate phase soon.

## 7. User Feedback Summary
- **Pain points:**  
  - Config safety: operators fear accidental overwrites (#10495).  
  - Provider compatibility: image‑part placement breaks OpenAI‑compatible endpoints (#10501).  
  - WASM plugin reliability: version skews and stale connections cause cryptic failures (#10505, #10506).  
  - Silent truncation: bootstrap files are truncated without warning (#10523).  

- **Satisfaction signals:**  
  - Strong community engagement on architectural RFCs (many high‑comment discussions).  
  - Rapid triage of new bugs (many issues created/updated today).  
  - Active contributor base submitting large‑scale enhancements (multiple XL‑size PRs).  

## 8. Backlog Watch
| Issue | Age | Needs Maintainer Review? | Note |
|-------|-----|--------------------------|------|
| [#9487 – Runtime‑owned sessions](https://github.com/zeroclaw‑labs/zeroclaw/issues/9487) | ~2 months | Yes (`needs‑maintainer‑review`) | Core RFC; needs closure or merge decision. |
| [#6850 – Memory lifecycle decoupling](https://github.com/zeroclaw‑labs/zeroclaw/issues/6850) | ~3 months | Yes | Long‑standing architectural RFC. |
| [#9488 – Unified attachments](https://github.com/zeroclaw‑labs/zeroclaw/issues/9488) | ~2 months | Yes | Rev 9; awaiting maintainer sign‑off. |
| [#6996 – Granular sandbox policy](https://github.com/zeroclaw‑labs/zeroclaw/issues/6996) | ~3 months | Yes | Critical for security hardening. |
| [#9103 – Separate memory storage](https://github.com/zeroclaw‑labs/zeroclaw/issues/9103) | ~2 months | Yes | Maintainer takeover revision; needs final review. |
| [#6909 – Computer‑use support](https://github.com/zeroclaw‑labs/zeroclaw/issues/6909) | ~3 months | Yes | Rev 2 with security clarifications; pending adoption. |
| [#7822 – WASM plugin observer subscriptions](https://github.com/zeroclaw‑labs/zeroclaw/issues/7822) | ~2 months | Yes | Observability capability for WASM runtime. |
| [#10076 – Composable WASM plugin runtime](https://github.com/zeroclaw‑labs/zeroclaw/issues/10076) | ~2 weeks | Yes | New RFC; high impact on plugin extensibility. |
| [#10222 – Single‑tool provider rounds](https://github.com/zeroclaw‑labs/zeroclaw/issues/10222) | ~2 weeks | Yes | Interactive‑agent improvement; early discussion. |

**Action required:** Maintainers should prioritize reviewing the long‑standing RFCs (#9487, #6850, #9488, #6996, #9103, #6909) to unblock the architectural roadmap. Several new WASM‑related RFCs also need timely assessment.

---
*Data source: ZeroClaw GitHub repository (zeroclaw‑labs/zeroclaw) as of 2026‑09‑01.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*