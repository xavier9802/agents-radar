# OpenClaw Ecosystem Digest 2026-08-21

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-21 01:43 UTC

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



# OpenClaw Project Digest — 2026-08-21

## 1. Today's Overview

OpenClaw is experiencing high activity with 500 issues and 500 PRs updated in the last 24 hours, indicating an intense development and triage cycle ahead of the v2026.8.1-beta.2 validation window. The project is in a stabilization phase: 34 issues were closed and 127 PRs merged/closed today, yet 466 issues and 373 PRs remain open, suggesting a significant backlog. No new releases were published today, but release validation work for v2026.8.1-beta.2 (#125626) is actively underway. The dominant themes are session-state reliability, inbound message delivery guarantees, and gateway startup stability.

## 2. Releases

No new releases were published today. Release validation is ongoing for **v2026.8.1-beta.2** ([#125626](https://github.com/openclaw/openclaw/issues/125626)), with testers upgrading real gateways and reporting through the validation skill. The beta was created on 2026-08-18 and remains the latest active build under test.

## 3. Project Progress

**Notable merged/closed PRs today:**

- **[PR #126934](https://github.com/openclaw/openclaw/pull/126934)** — Fixes Nostr SecretRef accounts silently disappearing after configuration; accounts using env/file/exec/store refs now persist correctly.
- **[PR #126931](https://github.com/openclaw/openclaw/pull/126931)** — Stops persisting runtime-only skill catalogs, addressing session bloat for operators with many agent sessions (closes #126663).
- **[PR #126921](https://github.com/openclaw/openclaw/pull/126921)** — Fixes `openclaw sessions --json` rewriting router-owned provider/model pairs and reporting incorrect runtime identity.
- **[PR #126932](https://github.com/openclaw/openclaw/pull/126932)** — Stops auto-restoring hand-authored configs missing the `meta` block, preventing silent overwrites by `.bak` generation ([#126806](https://github.com/openclaw/openclaw/issues/126806)).
- **[PR #120900](https://github.com/openclaw/openclaw/pull/120900)** — Adds Control UI install-policy warning review, allowing admins to acknowledge and proceed with plugin installs.
- **[PR #125471](https://github.com/openclaw/openclaw/pull/125471)** — Fixes Claude CLI OAuth losing refresh ownership after gateway restart due to legacy auth profile entries.

**Active PRs awaiting review:**
- [#125451](https://github.com/openclaw/openclaw/pull/125451) — Tolerates sidecar deletion during state DB hardening (P1, high merge risk).
- [#123189](https://github.com/openclaw/openclaw/pull/123189) — Recovers embedded channel runs in chat startup projection (P1, XL size).
- [#122918](https://github.com/openclaw/openclaw/pull/122918) — Accepts Tailscale identity on Control UI HTTP reads (P1, security-boundary risk).
- [#126616–#126619](https://github.com/openclaw/openclaw/pull/126616) — Series of HTTP chat fixes from @RaviTharuma covering minimal tool profiles, session binding, and reasoning model token truncation.

## 4. Community Hot Topics

**Most-discussed open issues (by comment count):**

| Issue | Topic | Comments | Tags |
|-------|-------|----------|------|
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | Per-agent cost budget enforcement at gateway | 23 | P2, feature |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | Centralized filename encoding for multi-encoding Content-Disposition | 20 | P3, feature |
| [#125626](https://github.com/openclaw/openclaw/issues/125626) | v2026.8.1-beta.2 release validation | 18 | maintainer |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | Gateway fails to start after 2026.7.1 update (crash-loop) | 14 | P0, regression |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | "Cannot convert undefined or null to object" with google-vertex/gemini-3.1-pro-preview | 14 | P1, regression |

**Underlying needs:** Operators are increasingly running multi-agent gateways at scale and need **cost governance** (#42475) and **reliable multi-encoding file handling** (#48788) — both reflect production maturation. The crash-loop regression (#108435) and Gemini null-object bug (#38327) are blocking adoption for enterprise users.

## 5. Bugs & Stability

**P0 / Release-blocker bugs:**

- [#108435](https://github.com/openclaw/openclaw/issues/108435) — Gateway fails to start after updating to 2026.7.1; systemd/Ollama/manual launch all fail. Tagged `impact:crash-loop`, `P0`, `regression`. No fix PR visible yet.
- [#125431](https://github.com/openclaw/openclaw/issues/125431) — Codex restricted tool policy silently disables workspace `AGENTS.md`; reproduction confirmed on v2026.8.1-beta.2. Tagged `P1`, `security`, `data-loss`.

**P1 bugs with active impact:**

- [#113306](https://github.com/openclaw/openclaw/issues/113306) — SQLite snapshot restore lacks end-to-end crash and identity guarantees; `impact:data-loss`.
- [#119270](https://github.com/openclaw/openclaw/issues/119270) — File tools strip leading `@` from destination paths, silently writing/deleting wrong files; `impact:data-loss`, `P0`.
- [#126246](https://github.com/openclaw/openclaw/issues/126246) — Telegram durable outbound deliveries stuck in `send_attempt_started` and lost on restart; `impact:message-loss`.
- [#119475](https://github.com/openclaw/openclaw/issues/119475) — WhatsApp inbound DMs from LID-addressed chats silently dropped (79 unique senders lost in 24h); `impact:message-loss`.
- [#112259](https://github.com/openclaw/openclaw/issues/112259) — Visible inbound channel turns can be silently dropped with zero-payload dispatch, no retry, no dead-letter.
- [#97616](https://github.com/openclaw/openclaw/issues/97616) — Unreaped hook/tool child processes accumulate as zombies, causing runtime degradation.
- [#83598](https://github.com/openclaw/openclaw/issues/83598) — Anthropic claude-cli OAuth refresh dead-ends main lane despite prior fix (#73682).
- [#124284](https://github.com/openclaw/openclaw/issues/124284) — Subagent spawn fails with vLLM openai-completions + thinking since v2026.8.1-beta.2 (regression from new stream wrapper).
- [#92241](https://github.com/openclaw/openclaw/issues/92241) — Gateway holds stale module import paths after update/rollback, silently dropping inbound messages (`ERR_MODULE_NOT_FOUND`).

**Fix PRs in flight:**
- [#125451](https://github.com/openclaw/openclaw/pull/125451) addresses state DB hardening sidecar race.
- [#126420](https://github.com/openclaw/openclaw/pull/126420) makes failed claude-cli live turns diagnosable.
- [#125977](https://github.com/openclaw/openclaw/pull/125977) keeps failed assistant turns visible in replay.

## 6. Feature Requests & Roadmap Signals

- [#42475](https://github.com/openclaw/openclaw/issues/42475) — **Per-agent cost budgets enforced at the gateway.** High community interest (23 comments, 1 👍). Reflects a clear demand for operator-level spend control in multi-agent deployments. Likely candidate for a future release as a gateway-level policy feature.
- [#51441](https://github.com/openclaw/openclaw/issues/51441) — **Expose resolved backend model in session_status.** Operators using LiteLLM/routing proxies cannot see which actual model served a request. Small but high-value visibility feature.
- [#47910](https://github.com/openclaw/openclaw/issues/47910) — **Provider fallback by failure class** (quarantine auth-broken providers). Currently all failures trigger the same fallback chain, wasting latency on known-bad auth states.
- [#71142](https://github.com/openclaw/openclaw/issues/71142) — **Configurable upload size limit for Control UI** (currently hardcoded at 5MB).
- [#45501](https://github.com/openclaw/openclaw/issues/45501) — **Configurable `session.resetPrompt`** to replace the hardcoded startup message.
- [#50798](https://github.com/openclaw/openclaw/issues/50798) — **Visible agent-to-agent messaging** for ACP thread-bound sessions without main session creation.
- [#45564](https://github.com/openclaw/openclaw/issues/45564) — **Confirmation step for `/new` and `/reset`** to prevent accidental session wipes.

**Prediction:** Cost budgeting (#42475) and provider fallback by failure class (#47910) are the most production-relevant features and likely to appear in a subsequent minor release. The reset-confirmation (#45564) is a low-risk UX improvement that could ship sooner.

## 7. User Feedback Summary

**Pain points:**
- **Session state instability** is the dominant complaint: silent message loss (#112259, #119475, #126246), transcript rewrite races (#124393), and zombie process accumulation (#97616) erode operator trust.
- **Gateway startup reliability** remains fragile: crash-loop on update (#108435), stale module paths after rollback (#92241), and container PID reuse causing dead locks (#114234).
- **Channel-specific bugs** are widespread: Feishu filename encoding (#48788), WhatsApp LID DM drops (#119475), Telegram progress draft scope (#125778), and iOS app duplicate replies (#124751).
- **Configuration fragility:** hand-authored configs without `meta` blocks being overwritten (#126806), XDG_CONFIG_HOME not respected during skill install (#53628), and NVM node warnings that can't be resolved (#60612).

**Positive signals:**
- Operators are actively validating betas (#125626) and reporting precise repros.
- The community is submitting well-structured bug reports with logs, environment details, and sometimes local hotfixes (e.g., #90361).
- Multi-agent and multi-channel usage is mature enough to surface complex interaction bugs, indicating a growing production user base.

## 8. Backlog Watch

**Issues needing maintainer attention (stale or blocked):**

| Issue | Age | Blocker |
|-------|-----|---------|
| [#108435](https://github.com/openclaw/openclaw/issues/108435) — Gateway crash-loop on 2026.7.1 | 37 days | P0, no fix PR |
| [#119270](https://github.com/openclaw/openclaw/issues/119270) — File tools strip `@` from paths (data loss) | 47 days | P0, no fix PR |
| [#113306](https://github.com/openclaw/openclaw/issues/113306) — SQLite snapshot restore lacks guarantees | 58 days | P1, no fix PR |
| [#43374](https://github.com/openclaw/openclaw/issues/43374) — All LLM API calls time out simultaneously (multi-agent concurrency) | 163 days | P3, `needs-info` |
| [#43747](https://github.com/openclaw/openclaw/issues/43747) — Memory management inconsistency across agents | 163 days | P2, `clawsweeper-recovery-stuck` |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) — active-memory blocks replies, QMD boot overloads gateway | 118 days | P1, `clawsweeper-recovery-stuck` |
| [#119796](https://github.com/openclaw/openclaw/issues/119796) — Windows vitest teardown EBUSY on agent state DB | 46 days | P2, `clawsweeper-recovery-stuck` |

Several issues carry the `clawsweeper-recovery-stuck` tag, indicating automated triage has been unable to shape them for fixing — these likely need manual maintainer intervention to re-classify or request additional repro data.

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent & Personal Assistant Open-Source Ecosystem
**Date:** 2026-08-21 | **Projects Tracked:** 12

---

## 1. Ecosystem Overview

The 2026 personal AI assistant open-source landscape is dominated by **OpenClaw** as the most active and complex project, with 500+ PRs/issues cycled daily and a substantial stabilization backlog. Mid-tier projects like **CoPaw**, **NanoBot**, and **Hermes Agent** are in rapid iteration phases, shipping beta releases and expanding into multi-channel, multi-agent deployments. A cluster of specialized or smaller projects (**PicoClaw**, **NanoClaw**, **Moltis**, **LobsterAI**) show focused development on security hardening, channel fidelity, and UX polish, while **ZeroClaw** is investing heavily in security architecture and WASM plugin migration. Two projects (**NullClaw**, **ZeptoClaw**) showed no recent activity, suggesting dormancy or low-velocity maintenance.

---

## 2. Activity Comparison

| Project | Issues (Open/Closed) | PRs (Open/Merged) | Release Status | Health Signal |
|---------|---------------------|-------------------|----------------|---------------|
| **OpenClaw** | 466 open / 34 closed | 373 open / 127 merged | No new; beta.2 validation | High activity, significant backlog |
| **CoPaw** | 14 open / 14 closed | ~50 active | v2.1.1-beta.1 shipped | Strong; balanced open/closed ratio |
| **NanoBot** | 3 open / 2 closed | 17 open / 12 merged | None | High velocity; healthy issue ratio |
| **Hermes Agent** | ~50 updated | ~50 updated | v0.20.4 (Aug 18) | High activity; desktop-focused bugs |
| **ZeroClaw** | ~100 updated | ~100 updated | None | Architectural hardening phase |
| **NanoClaw** | 3 issues touched | 35 open / 15 merged | None | Active stabilization batch |
| **IronClaw** | 17 open / 4 closed | 21 open / 14 merged | None | Strong; multi-front development |
| **Moltis** | ~1 issue | 4 open / 2 merged | v20260820.01 shipped | Stable; security-focused |
| **LobsterAI** | 2 open | 1 open / 6 merged | None | Low velocity; UX polish phase |
| **PicoClaw** | 3 open | 5 open / 4 merged | None | Moderate; dependency upkeep |
| **NullClaw** | — | — | — | Dormant |
| **ZeptoClaw** | — | — | — | Dormant |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of operation:** OpenClaw handles 500+ daily issue/PR events — an order of magnitude above most peers — reflecting its position as the most production-hardened gateway with multi-agent, multi-channel support.
- **Channel breadth:** Native support for Nostr, Telegram, WhatsApp, Feishu, Slack, and more; the widest channel coverage in the ecosystem.
- **Operational maturity:** Community users run multi-agent gateways at scale, surfacing complex interaction bugs (Zombie processes, state.db races, silent message loss) that smaller projects have not yet encountered.

**Technical approach differences:**
- Unlike **CoPaw** (Alibaba-backed, agent-harness focus) or **NanoBot** (Python, WebSocket-centric), OpenClaw operates as a **gateway orchestration layer** with session-state persistence, router-owned provider/model pairs, and skill catalogs — a more infrastructure-grade architecture.
- **ZeroClaw** takes a parallel security-first approach but from a WASM/plugin isolation angle rather than gateway-scale operations.
- OpenClaw's backlog (466 open issues, 373 open PRs) is the largest in the ecosystem, reflecting both its scope and its bottleneck in triage capacity.

**Community size comparison:**
OpenClaw's community is the largest and most production-oriented, followed by CoPaw (active Chinese-language contributor base) and Hermes Agent (Nous Research-backed). NanoBot and IronClaw show strong contributor engagement relative to project size.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|-----------|------------------|----------------|
| **Session/State Reliability** | OpenClaw, Hermes Agent, CoPaw, ZeroClaw | Silent message loss, state.db corruption, transcript rewrite races, context-cap misconfiguration |
| **Security Hardening** | ZeroClaw, Moltis, NanoClaw, IronClaw | Plugin egress policy, supply-chain scan pinning (Snyk), SSRF prevention, OAuth hardening |
| **Multi-Channel Fidelity** | OpenClaw, NanoBot, Moltis, LobsterAI | WhatsApp attachment handling, Telegram Markdown rendering, Feishu filename encoding, Slack scope gaps |
| **Cost/Usage Observability** | OpenClaw, NanoClaw, CoPaw | Per-agent cost budgets, token usage tracking, resolved backend model visibility |
| **Deployment Reliability** | Hermes Agent, NanoBot, OpenClaw | Windows desktop update pipeline, Docker OAuth callback failures, Debian install regressions |
| **WASM/Plugin Architecture** | ZeroClaw, IronClaw, PicoClaw | WASM plugin migration, after-turn hooks, unbound-run gate posture, plugin permission model |
| **Streaming Resilience** | NanoBot, CoPaw, OpenClaw | Mid-stream retry gaps, transient error classification, provider fallback by failure class |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | CoPaw | NanoBot | Hermes Agent | ZeroClaw | IronClaw |
|-----------|----------|-------|---------|--------------|----------|----------|
| **Primary Focus** | Gateway orchestration | Agent harness + Hub | Multi-channel bot | Desktop agent | Security/WASM sandbox | Rust-native automation |
| **Target User** | Multi-agent operators | Enterprise/Alibaba ecosystem | Bot operators (Telegram/Slack) | Desktop/power users | Security-conscious deployers | Rust ecosystem users |
| **Language** | TypeScript/Node | Python | Python | Python/Electron | Rust | Rust |
| **Key Differentiator** | Session-state reliability at scale | Self-hosted multi-user Hub, marketplace | x402 micropayment MCP, SenseNova provider | Windows desktop update pipeline, Kanban workers | Per-execution shell policy, WASM egress hooks | AfterTurn lifecycle hooks, Design System |
| **Architecture** | Gateway + skill catalog + router | Console + drivers + marketplace | WebSocket agent + provider abstraction | Electron desktop + Kanban worker pool | WASM plugin + iron-proxy sandbox | Rust executor + capability ports |
| **Maturity Stage** | Production hardening | Rapid iteration (v2.1.x) | Feature expansion | Desktop stabilization | Architectural refinement | Design-system unification |

---

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Active Iteration:**
- **OpenClaw** — Largest project, but backlog suggests triage bottleneck; stabilization phase with beta validation underway.
- **CoPaw** — Consistent release cadence (v2.1.1-beta.1), balanced open/closed issue ratio, ambitious feature pipeline (Hub, always-on Skills).
- **NanoBot** — High PR throughput (29 in 24h), strong contributor base, expanding into new providers (SenseNova) and markets (China).

**Tier 2 — Focused Development, Steady Progress:**
- **Hermes Agent** — Active bug-fixing cycle targeting Windows desktop and multi-profile gateway reliability.
- **ZeroClaw** — Security-first architectural phase; high engagement on RFCs but slow release cadence.
- **IronClaw** — Multi-front development (hooks, sandbox proxy, Design System); strong Rust engineering discipline.
- **NanoClaw** — Coordinated fix stacks landing; install-scope hardening phase.

**Tier 3 — Low Velocity, Maintenance Mode:**
- **Moltis** — Stable with recent release; focused on security and WhatsApp polish.
- **LobsterAI** — UX polish phase; low issue count, small contributor base.
- **PicoClaw** — Dependency upkeep; stale issues accumulating, needs maintainer triage.

**Tier 4 — Dormant:**
- **NullClaw, ZeptoClaw** — No activity in trailing 24h.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|-------|-------------------------|-------------------------------|
| **Production-scale reliability is the #1 concern** | OpenClaw's message-loss bugs, Hermes Agent's state.db corruption, CoPaw's context-cap confusion, NanoBot's streaming retry gaps | Multi-channel, multi-agent deployments will surface state-management and reliability issues; operators should prioritize projects with active bug-fix cadences |
| **Security hardening is a sustained theme** | ZeroClaw's WASM egress policy + Snyk pinning, Moltis's sandbox image validation, NanoClaw's install-scope fixes, IronClaw's CI security guard | Supply-chain security and sandbox isolation are becoming table-stakes; developers should expect plugin permission models and network egress policies in new projects |
| **Cost governance demand is emerging** | OpenClaw's per-agent budget request (#42475, 23 comments), NanoClaw's token tracking PR (#3270), CoPaw's embedding timeout config | Multi-agent operators need spend visibility; projects with built-in budgeting/observability will have a competitive edge |
| **Channel fidelity is a differentiator** | WhatsApp media mounting (NanoClaw), Telegram sticker support (NanoBot), WhatsApp Markdown (Moltis), Feishu encoding (OpenClaw) | Channel-specific bugs are the most visible friction point; projects investing in channel primitives will attract power users |
| **WASM/plugin architecture is the emerging paradigm** | ZeroClaw's comprehensive WASM migration, IronClaw's capability ports, PicoClaw's multi-agent primitives | Modular, sandboxed plugin systems are replacing monolithic architectures; developers should evaluate plugin portability and security boundaries |
| **Desktop deployment remains fragile** | Hermes Agent's Windows ZIP fallback bug, OpenClaw's container PID reuse, NanoBot's Docker OAuth failure | Cross-platform desktop releases are a consistent pain point; projects with Electron/desktop focus need better update pipeline testing |
| **Chinese-market expansion is active** | SenseNova provider (NanoBot), CoPaw's Qwen ecosystem, LobsterAI's Youdao backing | Regional model providers and Chinese-language UX are significant growth vectors for the ecosystem |

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-21

## 1. Today's Overview

NanoBot shows **high development velocity** on 2026-08-21, with 29 PRs and 5 issues updated in the last 24 hours. The project maintains a healthy open/active issue ratio (3 open, 2 closed), and the PR throughput (17 open, 12 merged/closed) indicates an active contributor base. No new releases were published, but a notable closed PR (#5447) added a paid security-scan MCP integration (ScanPay + x402), and several bug fixes landed today across providers, channels, and the web UI.

## 2. Releases

No new releases published today.

## 3. Project Progress

**Merged / Closed PRs Today:**

- **#5447** [CLOSED] Paid security-scan MCP integration (nanobot + ScanPay x402) — #5447
  Added an autonomous agent revenue stack with Solana x402 micropayment security scanning, exposing nanobot as a paid MCP service.

- **#5452** [CLOSED] feat(tui): print resume command on exit — #5452
  The TUI now prints a ready-to-run `nanobot agent --session websocket:<id>` command after terminal restore, improving session resumption UX.

- **#5240** [CLOSED] refactor(webui): unify floating controls — #5240
  Centralized shared floating-surface and item styling across command menus, rich panels, and searchable choices in the web UI.

**PRs Advancing Key Features:**

- **#5420** [OPEN] feat(webui): add turn observability and safe recovery — #5420
  Projects user turns into a single answer surface with ordered reasoning, tool use, and intermediate activity tracking. Accumulates provider usage stats and marks interrupted work.

- **#5387** [OPEN] feat(telegram): support reusable sticker replies — #5387
  Exposes inbound Telegram sticker metadata and dispatches reusable sticker replies, preserving chat/topic routing.

- **#5453** [OPEN] feat(providers): add SenseNova (商汤日日新) provider — #5453
  Adds native support for SenseNova's OpenAI-compatible endpoint, including `sensenova-6.8-flash-lite`, `deepseek-v4-flash`, and `glm-5.2`.

- **#5179 / #5180** [OPEN] MCP SDK v2 migration evaluation and full migration — #5179, #5180
  Two competing PRs evaluating migration from MCP SDK v1 to v2, with #5179 being the full migration and #5180 a minimal viability baseline.

## 4. Community Hot Topics

1. **MCP SDK v2 Migration** — #5179 (39 comments), #5180 (29 comments)
   A major architectural discussion on migrating the entire MCP integration to SDK v2. Two parallel PRs reflect community split between a full migration and a cautious minimal evaluation. This is the highest-engagement topic and signals a significant dependency upgrade on the horizon.

2. **Turn Observability in Web UI** — #5420
   Users are pushing for better visibility into agent turns, reasoning traces, and tool activity. The high comment count indicates strong interest in debugging and transparency features.

3. **Telegram Sticker Support** — #5387
   Community-driven feature for richer Telegram interactions, reflecting growing use of nanobot as a Telegram bot with multimedia expectations.

4. **SenseNova Provider Addition** — #5453
   First-time native support for a Chinese LLM provider (SenseNova), indicating expanding international user base and demand for regional model access.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| 🔴 High | [#5454](https://github.com/HKUDS/nanobot/issues/5454) | Streaming providers skip retry after mid-stream `server_error` — transient errors are not retried once content has already been streamed | [#5455](https://github.com/HKUDS/nanobot/pull/5455) [OPEN] — adds `"server_error"` to `_TRANSIENT_ERROR_MARKERS` |
| 🔴 High | [#5444](https://github.com/HKUDS/nanobot/issues/5444) | OAuth login to OpenAI fails in Docker — `localhost:1455` callback URL unreachable in containerized environments | No fix PR yet |
| 🟡 Medium | [#5454](https://github.com/HKUDS/nanobot/issues/5454) / [#5455](https://github.com/HKUDS/nanobot/pull/5455) | Codex `server_error` not retried after initial content streamed | Fix PR #5455 open |
| 🟡 Medium | [#5425](https://github.com/HKUDS/nanobot/issues/5425) [CLOSED] | `socks://` proxy URLs rejected for custom OpenAI-compatible providers | Resolved (closed) |
| 🟡 Medium | [#5413](https://github.com/HKUDS/nanobot/pull/5413) | Provider exceptions escape fallback loop instead of being handled by fallback policy | Fix PR #5413 [OPEN] |
| 🟡 Medium | [#5414](https://github.com/HKUDS/nanobot/pull/5414) | Slack file downloads don't validate across redirects — potential SSRF vector | Fix PR #5414 [OPEN] |
| 🟢 Low | [#5458](https://github.com/HKUDS/nanobot/pull/5458) | Matrix error logs missing contextual values due to Loguru placeholder mismatch | Fix PR #5458 [OPEN] |
| 🟢 Low | [#5457](https://github.com/HKUDS/nanobot/pull/5457) | Dispatcher exception not scoped — one failed outbound message can stop all message delivery | Fix PR #5457 [OPEN] |
| 🟢 Low | [#5430](https://github.com/HKUDS/nanobot/pull/5430) | Background task groups not released, causing memory leak over time | Fix PR #5430 [OPEN] |
| 🟢 Low | [#5431](https://github.com/HKUDS/nanobot/pull/5431) | Background task failures silently swallowed | Fix PR #5431 [OPEN] |

**Notable:** Fix PR #5455 directly addresses the most impactful open bug (#5454). The OAuth-in-Docker issue (#5444) remains unresolved with no fix PR yet.

## 6. Feature Requests & Roadmap Signals

- **Google Vertex AI for Claude models** — [#5459](https://github.com/HKUDS/nanobot/issues/5459) [OPEN]
  Request for a first-class Anthropic Claude provider via Google Vertex AI. Nanobot currently lacks native Vertex support, and this is the most prominent feature request today. Likely to be considered for a future release given the growing demand for multi-cloud provider support.

- **SenseNova Provider** — [#5453](https://github.com/HKUDS/nanobot/pull/5453) [OPEN]
  Chinese LLM provider support is being actively developed. High probability of inclusion in the next release.

- **Telegram Sticker Support** — [#5387](https://github.com/HKUDS/nanobot/pull/5387) [OPEN]
  Richer Telegram bot capabilities. Moderate probability for a future release.

- **Turn Observability UI** — [#5420](https://github.com/HKUDS/nanobot/pull/5420) [OPEN]
  Major UX improvement for the web UI. Likely a priority feature given high community engagement.

- **MCP SDK v2 Migration** — [#5179](https://github.com/HKUDS/nanobot/pull/5179) [OPEN]
  A significant dependency upgrade. May be deferred until the evaluation in #5180 concludes, but the volume of discussion suggests it's a roadmap commitment.

## 7. User Feedback Summary

- **OAuth-in-Docker friction** (#5444): Users running nanobot in Docker containers hit a wall with OAuth callbacks to `localhost`, a common pain point for containerized deployments.
- **Proxy compatibility**: The `socks://` proxy bug (#5425, now closed) reflects real-world enterprise use cases where users route traffic through SOCKS proxies.
- **Streaming resilience**: The mid-stream retry bug (#5454) and its fix (#5455) indicate users rely heavily on long-running streaming sessions and expect robust error recovery.
- **Security-conscious deployments**: The Slack redirect validation fix (#5414) and MCP OAuth credential preservation (#5338) show users are deploying nanobot in security-sensitive environments.
- **Telegram power users**: Sticker support (#5387) suggests an active Telegram bot user base wanting richer media interactions.
- **Chinese market growth**: SenseNova provider addition (#5453) and the paid security-scan integration (#5447) point to expanding interest in Asian markets and agent monetization use cases.

## 8. Backlog Watch

| Issue/PR | Age | Concern |
|----------|-----|---------|
| [#5444](https://github.com/HKUDS/nanobot/issues/5444) — OAuth login fails in Docker | Opened 2026-08-19, no fix PR | Docker deployment is a common setup; OAuth callback URL is a fundamental usability blocker |
| [#5179](https://github.com/HKUDS/nanobot/pull/5179) — MCP SDK v2 migration | Opened 2026-07-30, 39 comments | Long-running discussion with no resolution; blocks MCP stability and future maintenance |
| [#5180](https://github.com/HKUDS/nanobot/pull/5180) — MCP v2 evaluation baseline | Opened 2026-07-30, 29 comments | Same age as #5179; dual-PR situation needs maintainer decision |
| [#5338](https://github.com/HKUDS/nanobot/pull/5338) — MCP OAuth credential preservation | Opened 2026-08-11, conflict label | Security-relevant fix with a merge conflict; unresolved since 10 days |
| [#5425](https://github.com/HKUDS/nanobot/issues/5425) — Legacy socks:// proxy | Closed 2026-08-20 | Resolved, but indicates ongoing proxy compatibility challenges |

**Overall Health Assessment:** NanoBot is in a **strong development phase** with high PR throughput and active community contributions. Bug fixes are landing steadily, and feature development is expanding into new providers and channels. The main risks are the unresolved MCP SDK v2 migration decision (two competing PRs since late July) and the Docker OAuth blocker (#5444) that lacks a fix PR. Maintainer attention is needed on #5179/#5180 to unblock the MCP roadmap and on #5444 for Docker deployment usability.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-21

## 1. Today's Overview

Hermes Agent saw **high activity** on 2026-08-21, with **50 issues** and **50 PRs** updated in the last 24 hours. No new releases were published. The day was dominated by a cluster of interrelated bug fixes targeting Windows desktop updates, multi-profile gateway handoff, and Kanban worker reliability, alongside two merged PRs. The project continues to address stability gaps in desktop deployment paths and session-state persistence under concurrent load.

---

## 2. Releases

**No new releases.** The most recent version remains v0.20.4 (2026-8.18).

---

## 3. Project Progress

**Merged/Closed PRs today:**
- **#91187** (closed) — Sanitizes imperative-shape and self-narration lines from Honcho peer-card data to prevent model context pollution.
- **#87978** (closed) — Fixes Desktop context-usage gauge being pinned to a pre-turn estimate; now reflects live gateway measurements.

**PRs advanced / opened today:**
- **#91219** — Bounds Node-toolchain `--version` probes with timeouts, preventing indefinite hangs when `agent-browser` is absent.
- **#91218** — Adds MiniMax M3 direct-provider pricing entries with `cache_write` rate.
- **#91217** — Fixes `/handoff` on multi-profile gateways (wrong `state.db`, wrong session key, wrong bot).
- **#91186** — Escalates to `taskkill /T /F` when `force=False` fails on Windows, preventing orphaned gateway processes.
- **#91214** — Fixes silent JSON config loss on Windows from UTF-8 BOM in memory-plugin and Qwen CLI config editors.
- **#91207** — Preserves Electron Framework JIT entitlements during macOS self-update re-signing.
- **#91205** — Preserves worktree repository bindings in Kanban to prevent `spawn_failed` loops.
- **#91206** — Requeues Kanban workers after transient provider failures instead of treating them as protocol violations.
- **#91192** — Adds A2A trusted-operator tier for named peer authorization on local tasks.
- **#91204** — Prototype for gateway-scoped account/resource control surface (`system.resources`, `account.usage` RPCs).
- **#91213** — Separates Bot Mode direct messages and groups in the Desktop roster.
- **#91194** (docs) — Adds structured run provenance contract v1.0.0/v1.1.0 to version control.
- **#91215** (deps) — Upgrades Photon sidecar `spectrum-ts` from 8.0.0 → 12.8.0; adds `ffmpeg-static` for MP3→AAC conversion.
- **#81432** — Fixes `/goal` loops incorrectly marking "blocked on user input" as DONE.

---

## 4. Community Hot Topics

| # | Issue | Comments | Reactions | Focus |
|---|-------|----------|-----------|-------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index stale/degraded (29.8h old, limit 26h) | 66 | 0 | Automation watchdog |
| [#87093](https://github.com/NousResearch/hermes-agent/issues/87093) | Debian installation broken (`uv.lock` & `npm install` failed) | 15 | 2 | Install path |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | ZIP fallback deletes built desktop app, never rebuilds | 13 | 1 | Windows desktop update |
| [#27649](https://github.com/NousResearch/hermes-agent/issues/27649) | Multiprocess logging writes to rotated `agent.log.N` files | 8 | 0 | Observability |
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) | Voice mode in browser dashboard — WebRTC audio capture | 7 | 6 | Feature request |
| [#22054](https://github.com/NousResearch/hermes-agent/issues/22054) | PATH injection from venv shadows system Python (outdated 3.11) | 7 | 2 | Windows/compatibility |
| [#75801](https://github.com/NousResearch/hermes-agent/issues/75801) | OpenCode Go gpt-5.6-luna false mid-stream classification | 7 | 1 | Streaming/agent |

**Analysis:** The top-commented issues reveal two dominant community needs: **(1) installation & update reliability** across platforms (Debian, Windows desktop updates, PATH pollution), and **(2) voice input accessibility** when running headlessly or remotely. The skills-index watchdog issue (#66616) with 66 comments indicates an ongoing infrastructure concern around automated deployment freshness.

---

## 5. Bugs & Stability

| Severity | Bug | Issue | Fix PR |
|----------|-----|-------|--------|
| **P1** | `state.db` corruption (3 incidents in 8 days on busy single-host); lock storm + journal_mode reverted to WAL | [#89293](https://github.com/NousResearch/hermes-agent/issues/89293) | — |
| **P1** | Debian install script fails (`uv.lock` & `npm install`) | [#87093](https://github.com/NousResearch/hermes-agent/issues/87093) | — |
| **P1** | Windows ZIP fallback silently deletes built desktop app; reports "Already up to date" on subsequent updates | [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | Related: #80500 (npm shim fix), #91219 (timeout bounds) |
| **P2** | `/handoff` broken on multi-profile gateways — wrong `state.db`, wrong session key, wrong bot | [#91216](https://github.com/NousResearch/hermes-agent/issues/91216) | **#91217** (open) |
| **P2** | Daily Desktop update fails — "desktop app not rebuilt" (fail-closed native-dep gate + corrupted `node_modules`) | [#90829](https://github.com/NousResearch/hermes-agent/issues/90829) | Related: #80500, #91219 |
| **P2** | `hermes update` orphanates non-systemd-supervised dashboard; respawn detaches | [#73379](https://github.com/NousResearch/hermes-agent/issues/73379) | — |
| **P2** | Desktop profile switch over SSH spawns LOCAL backend, reconnects to wrong host | [#90477](https://github.com/NousResearch/hermes-agent/issues/90477) | — |
| **P2** | Desktop status stack: completed background tasks stay "running" indefinitely | [#81114](https://github.com/NousResearch/hermes-agent/issues/81114) | — |
| **P2** | `auto_tts` plays audio twice on desktop (gateway + client both fire) | [#90297](https://github.com/NousResearch/hermes-agent/issues/90297) | Related: #78196 |
| **P2** | Windows ACP session hangs when `agent-browser` not installed (npx resolution timeout) | [#91087](https://github.com/NousResearch/hermes-agent/issues/91087) | **#91219** (open) |
| **P2** | Kanban task with `--initial-status blocked` promoted/spawned incorrectly | [#91178](https://github.com/NousResearch/hermes-agent/issues/91178) | — (closed as duplicate) |
| **P2** | POSIX rollover backup race in multi-process logging | [#27649](https://github.com/NousResearch/hermes-agent/issues/27649) | **#91210** (open) |
| **P3** | Model narrates stale list items over fresh tool result | [#91153](https://github.com/NousResearch/hermes-agent/issues/91153) | — |
| **P3** | React `useSyncExternalStore` re-entrant crash in workspace pane | [#90795](https://github.com/NousResearch/hermes-agent/issues/90795) | — |
| **P3** | Telegram `proxy_targets` ignores custom `base_url` hostname | [#47188](https://github.com/NousResearch/hermes-agent/issues/47188) | — |
| **P3** | Windows install fails under Constrained Language Mode | [#89857](https://github.com/NousResearch/hermes-agent/issues/89857) | — |

**Key observation:** The **Windows Desktop update pipeline** has a cascade of related failures (#83846, #90829, #91087) all addressed by parallel PRs (#80500, #91219). The **multi-profile gateway handoff** (#91216 → #91217) and **state.db corruption** (#89293) are the most impactful open stability concerns.

---

## 6. Feature Requests & Roadmap Signals

| # | Request | Priority | Signal |
|---|---------|----------|--------|
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) | Voice mode in browser dashboard via WebRTC (`getUserMedia`) | P3, 6 👍 | Strong user demand for remote voice input |
| [#54352](https://github.com/NousResearch/hermes-agent/issues/54352) | Browser-side microphone capture for voice input (alternative to server-side PortAudio) | P3, 2 👍 | Complements #20765 |
| [#90051](https://github.com/NousResearch/hermes-agent/issues/90051) | Client-mic capture for `/voice` on remote gateway connections | P3 | Extends voice to Desktop + remote gateway combo |
| [#91149](https://github.com/NousResearch/hermes-agent/issues/91149) | Route `localhost` dev servers through harness in preview pane (SSH remote) | P3 | Developer workflow improvement |
| [#91204](https://github.com/NousResearch/hermes-agent/pull/91204) | Gateway-scoped account/resource control surface (CPU, RAM, quota metrics) | P3, in progress | Active feature work — likely in next Desktop release |
| [#91192](https://github.com/NousResearch/hermes-agent/pull/91192) | A2A trusted-operator tier for named peer authorization | P3, in progress | Security hardening for agent-to-agent delegation |
| [#91213](https://github.com/NousResearch/hermes-agent/pull/91213) | Separate Bot Mode DMs and groups in roster | P3, in progress | UX polish for bot operators |
| [#88683](https://github.com/NousResearch/hermes-agent/issues/88683) | Single transactional deployment plan for install/update/bootstrap | P3, needs-decision | Architectural improvement — long-running pain point |
| [#90866](https://github.com/NousResearch/hermes-agent/issues/90866) | Observable state proof-carrying from source to side effect | P3, needs-decision | Follow-on to #88683; deeper architectural vision |

**Prediction:** Voice input improvements (#20765, #54352, #90051) and the account/resource control surface (#91204) are the most likely candidates for the next release cycle. The transactional deployment architecture (#88683) is a longer-term roadmap item.

---

## 7. User Feedback Summary

**Pain points:**
- **Desktop update failures on Windows** are the most acute user-facing issue. Users report the desktop app silently disappearing after updates, with no path to recovery (#83846, #90829). The fix PRs exist but are not yet merged/released.
- **Installation on Debian** is broken out of the box for many users (#87093), suggesting the `curl | bash` install path needs regression testing on newer Debian releases.
- **`state.db` corruption** on busy single-host deployments is causing production downtime with hours of manual recovery (#89293). Three incidents in 8 days is a serious reliability signal.
- **Remote voice input** is blocked by server-side PortAudio dependency when running headlessly (#20765, #54352). Users want browser-based microphone access.
- **Multi-profile gateway handoff** is non-functional (#91216), blocking users who run multiple bot profiles on one gateway.

**Satisfaction signals:**
- The community actively contributes fixes (e.g., #91217, #91210, #91205 show maintainer + community collaboration).
- Kanban and cron reliability improvements (#81432, #91205, #91206) address real operational pain.
- Documentation is being canonized (#80551, #91194), indicating maturation of the project's architectural discourse.

---

## 8. Backlog Watch

| # | Issue | Reason for Watch |
|---|-------|-----------------|
| [#89293](https://github.com/NousResearch/hermes-agent/issues/89293) | `state.db` corruption — 3 incidents in 8 days | **P1, no fix yet.** Production-impacting; requires root-cause analysis of lock storm + journal_mode regression. |
| [#87093](https://github.com/NousResearch/hermes-agent/issues/87093) | Debian installation broken | **P1, no fix yet.** Affects first-time users; install script may need platform detection updates. |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | ZIP fallback deletes desktop app, never rebuilds | **P1, related PRs open but not merged.** Desktop update pipeline is fragile on Windows. |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index stale/degraded (66 comments) | **P3 but highest engagement.** Automated watchdog firing repeatedly; may indicate cron/deployment issue. |
| [#27649](https

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-21

## 1. Today's Overview
PicoClaw maintained steady, moderate activity on 2026-08-21, with 3 open issues and 9 pull requests updated in the trailing 24 hours (5 open, 4 merged/closed). No new releases were published. Development momentum is currently split between backend dependency upkeep and community-driven feature requests, while a notable Web UI performance issue remains unresolved. Overall project health is stable, with active contributor engagement but a growing stale-tag backlog that warrants maintainer triage.

## 2. Releases
No new releases were published in this reporting window.

## 3. Project Progress
Four pull requests were closed or merged recently, advancing core tooling and protocol support:
- **PR #714** – Refactored the skills installation CLI into `skillsCmd`, added a `reinstall` subcommand, and introduced GitHub Trees API support for full-directory fetches and `repo@branch` specifications.
- **PR #1158** – Resolved #269 by implementing the `anthropic-messages` protocol, enabling native `/v1/messages` endpoint compatibility for Anthropic-compatible proxy services.
- **PR #423** – Closed a long-running WIP that established foundational multi-agent collaboration primitives (shared blackboard, thread-safe context pool, agent handoff tools).
- **PR #3318** – Fixed a broken `pnpm-lock.yaml` caused by duplicate mapping keys, restoring frontend build reliability.

## 4. Community Hot Topics
- **[Issue #3281](https://github.com/sipeed/picoclaw/issues/3281)** (6 comments, 1 👍) – Severe Web UI input lag when chat history grows. This is the most discussed item and signals a client-side rendering/state bottleneck that directly impacts daily conversational workflows.
- **[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)** – Requests a configuration flag to route `/audio/transcriptions` to non-Whisper ASR endpoints, reflecting demand for broader voice-model compatibility.
- **[Issue #3330](https://github.com/sipeed/picoclaw/issues/3330)** – Proposes dynamic model override for `delegate`, `spawn`, and `subagent` tools at call time, indicating users want runtime flexibility over static `config.json` assignments.

These topics collectively highlight a community pushing PicoClaw toward scalable orchestration, provider agnosticism, and performance hardening.

## 5. Bugs & Stability
- **High Severity:** [Issue #3281](https://github.com/sipeed/picoclaw/issues/3281) – Web UI chat input lag with moderate history. No fix PR is currently open; this requires frontend profiling and likely virtualization or state-debounce optimization.
- **Resolved:** [PR #3318](https://github.com/sipeed/picoclaw/pull/3318) eliminated a build-breaking duplicate-key issue in `pnpm-lock.yaml`, removing a critical frontend dependency blocker.
- No crash reports, data-loss regressions, or authentication failures were logged in this window.

## 6. Feature Requests & Roadmap Signals
- **Dynamic subagent model routing** ([Issue #3330](https://github.com/sipeed/picoclaw/issues/3330)) and **flexible ASR endpoints** ([Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)) both point toward a roadmap focused on runtime configurability and provider abstraction.
- The merged Anthropic native protocol ([PR #1158](https://github.com/sipeed/picoclaw/pull/1158)) and the closed multi-agent framework ([PR #423](https://github.com/sipeed/picoclaw/pull/423)) suggest upcoming iterations will prioritize agent-to-agent communication depth and LLM provider parity.
- **Prediction:** The next minor release will likely include improved subagent tool configurability, expanded voice model support, and Web UI performance optimizations.

## 7. User Feedback Summary
Users are actively adopting PicoClaw for multi-agent delegation, skill-driven workflows, and Anthropic-compatible API routing. Satisfaction is high around extensibility and protocol support, but frustration is mounting over frontend performance and rigid agent configuration. The repeated requests for runtime model switching and alternative ASR backends indicate that power users are moving beyond demo use cases into production-adjacent pipelines, where latency and configuration flexibility are critical.

## 8. Backlog Watch
Three open issues are currently flagged as stale and at risk of automatic closure:
- [Issue #3281](https://github.com/sipeed/picoclaw/issues/3281) – Performance bug
- [Issue #3331](https://github.com/sipeed/picoclaw/issues/3331) – ASR endpoint flexibility
- [Issue #3330](https://github.com/sipeed/picoclaw/issues/3330) – Subagent model override

Additionally, five Dependabot PRs remain open and unmerged ([#3332](https://github.com/sipeed/picoclaw/pull/3332)–[#3336](https://github.com/sipeed/picoclaw/pull/3336)), covering AWS SDK, Anthropic Go SDK, and Matrix client upgrades. Maintainer attention is recommended to triage these dependency updates and re-engage the stale issue contributors to prevent momentum loss.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-21

## 1. Today's Overview

NanoClaw saw elevated development activity today with **50 PRs updated** (35 open, 15 merged/closed) and **3 issues touched**, signaling a period of active stabilization and skill hardening. The core team shipped a coordinated batch of install-scope fixes (stacked on PR #3408), addressing multi-install host reliability across multiple skills. One bug was resolved (#2606), while two significant open issues remain around WhatsApp media mounting and mention-sticky engagement logic. No new releases were published today, suggesting the merged changes are still accumulating toward the next version.

## 2. Releases

*No new releases today.*

## 3. Project Progress

**Merged / Closed today:**
- **#2606** — `engage_mode='always'` silent message drop fixed (issue closed) ([link](https://github.com/nanocoai/nanoclaw/issues/2606))
- **#3421** — docs+setup: one-click Slack agent announcement merged ([link](https://github.com/nanocoai/nanoclaw/pull/3421))
- **#1311** — Feature: create new session (closed) ([link](https://github.com/nanocoai/nanoclaw/pull/1311))

**PRs advancing today:**
- **#3402** — Codex provider file delivery fix: introduces explicit `send_file` events with ownership contracts and safe outbox staging ([link](https://github.com/nanocoai/nanoclaw/pull/3402))
- **#3403** — Matrix skill: ESM patch for Node 22 compatibility ([link](https://github.com/nanocoai/nanoclaw/pull/3403))
- **#3247** — Scheduling: retires malformed cron strings instead of re-erroring every sweep tick ([link](https://github.com/nanocoai/nanoclaw/pull/3247))
- **#3423** — Slack setup: adds missing `app_mentions:read` bot scope ([link](https://github.com/nanocoai/nanoclaw/pull/3423))
- **#3422** — Router fix: `mention-sticky` now subscribes on mention, not on session creation ([link](https://github.com/nanocoai/nanoclaw/pull/3422))
- **#3355 / #3356** — New Cursor Agent SDK provider skill and payload support ([link](https://github.com/nanocoai/nanoclaw/pull/3355), [link](https://github.com/nanocoai/nanoclaw/pull/3356))
- **#3189** — New utility skill: `add-why` explains what happened to a single message ([link](https://github.com/nanocoai/nanoclaw/pull/3189))
- **#3270** — NCL token usage tracking feature ([link](https://github.com/nanocoai/nanoclaw/pull/3270))

**Core-team install-scope fix stack (all on PR #3408):**
- #3414 — `add-clidash`: caps refresh fan-out, repairs payload
- #3415 — `add-atomic-chat-tool`: moves config onto per-group MCP seam
- #3416 — `add-ollama-tool`: per-group MCP seam, live config path
- #3417 — `add-dashboard`: REMOVE.md, portable SQL, shutdown wiring
- #3418 — `add-tavily-tool`: honest smoke test, idempotent removal
- #3419 — `add-anydoc`: install-scoped ncl, portable skill test
- #3420 — `add-macos-statusbar`: Swift code and plist labels slug-aware
- #3401 — `add-whatsapp-cloud`: keeps skill payload compatible with main

## 4. Community Hot Topics

- **WhatsApp media unreachable by agent** — Issue #2715 ([link](https://github.com/nanocoai/nanoclaw/issues/2715)): Inbound images/docs/audio save to an unmounted `DATA_DIR/attachments` path, making them invisible inside the container. This is a high-impact usability bug for WhatsApp-wired agents and has been open since June with no fix merged yet.
- **mention-sticky false engagement** — Issue #3369 ([link](https://github.com/nanocoai/nanoclaw/issues/3369)): On threaded platforms like Slack, `engage_mode: 'mention-sticky'` with `ignored_message_policy: 'accumulate'` causes the agent to reply in threads where it was never mentioned. PR #3422 ([link](https://github.com/nanocoai/nanoclaw/pull/3422)) directly addresses this root cause.
- **Token usage tracking** — PR #3270 ([link](https://github.com/nanocoai/nanoclaw/pull/3270)): Community-requested feature for exposing NCL token consumption, reflecting user demand for observability into agent cost.
- **Cursor Agent SDK integration** — PRs #3355/#3356 ([link](https://github.com/nanocoai/nanoclaw/pull/3355), [link](https://github.com/nanocoai/nanoclaw/pull/3356)): New provider skill for Cursor, signaling community interest in expanding agent backend options beyond existing providers.

**Underlying needs:** Users are pushing for (1) reliable multi-platform attachment handling, (2) precise engagement control to avoid noise, (3) cost observability, and (4) broader provider coverage.

## 5. Bugs & Stability

| Severity | Item | Status | Fix PR |
|----------|------|--------|--------|
| **High** | `engage_mode='always'` silently drops all messages | Closed (#2606) | Merged |
| **High** | WhatsApp attachments inaccessible in container (unmounted volume) | Open (#2715) | None yet |
| **Medium** | `mention-sticky` engages without mention via accumulate | Open (#3369) | PR #3422 open |
| **Medium** | Matrix ESM imports fail under Node 22 | Open | PR #3403 open |
| **Medium** | Malformed cron strings re-error every sweep tick | Open | PR #3247 open |
| **Low** | Slack setup omits `app_mentions:read` scope | Open | PR #3423 open |
| **Low** | `add-whatsapp-cloud` skill payload incompatible with main | Open | PR #3401 open |

**Notable regression risk:** The install-scope fix stack (#3414–#3420) corrects dead-config and multi-install interference bugs but remains unmerged; if any PR in the stack conflicts, it could introduce new drift.

## 6. Feature Requests & Roadmap Signals

- **Cursor Agent SDK provider** (#3355/#3356) — Likely to ship in the next minor release as a new skill.
- **Token usage tracking** (#3270) — Observability feature with clear user demand; strong candidate for next release.
- **`add-why` diagnostic skill** (#3189) — Utility skill for message-level debugging; low-risk, high-utility, likely to be included.
- **One-click Slack agent setup** (#3421) — Already merged; docs announcement shipped.
- **macOS status bar app hardening** (#3420) — Install-scope aware; suggests ongoing investment in desktop experiences.

**Prediction:** The next release will likely feature the Cursor provider, token usage tracking, and the `add-why` skill, alongside the install-scope stability fixes.

## 7. User Feedback Summary

- **Pain point — WhatsApp file handling:** Users expect attachments to be immediately accessible to the agent. The unmounted volume bug (#2715) is a friction point for anyone using WhatsApp as a primary channel.
- **Pain point — Engagement precision:** The `mention-sticky` false-positive bug (#3369) causes unwanted thread replies, degrading the signal-to-noise ratio in Slack teams.
- **Satisfaction signal — Slack one-click setup:** The merged announcement PR (#3421) reflects positive momentum on onboarding experience.
- **Demand — Cost visibility:** Token usage tracking (#3270) indicates users are deploying agents at scale and need billing/usage transparency.
- **Demand — Provider diversity:** Cursor SDK integration (#3355/#3356) shows users want flexibility in agent backends.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| **#2715** — WhatsApp media unmounted | ~75 days open | High — blocks core WhatsApp use case |
| **#3369** — mention-sticky false engage | 1 day open | Medium — fix PR #3422 exists but unmerged |
| **#3247** — Malformed cron re-error | 7 days open | Medium — affects scheduling reliability |
| **#3403** — Matrix Node 22 ESM failure | 1 day open | Medium — compatibility blocker |
| **#3423** — Missing Slack scope | 1 day open | Low — trivial fix, unmerged |
| **#3401** — WhatsApp skill payload compat | 1 day open | Low — blocked on stack merge |

**Maintainer attention needed:** Issue #2715 has been open since mid-June with no fix in progress and directly impacts a major channel's functionality. Prioritizing a volume-mount fix should be a near-term goal.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-21

## 1. Today's Overview
The IronClaw repository shows **high activity** with 21 issues updated (17 open, 4 closed) and 35 PRs updated (21 open, 14 merged/closed) in the last 24 hours. No new releases were shipped. Maintainers are driving a coordinated push across three fronts: **extension of the agent lifecycle** (`AfterTurn` hooks, sandbox proxy egress), **WebUI design‑system unification** (Phases 1–5 epics, Storybook integration), and **daily CI hygiene** (clippy 1.98 migration, lint cascade clearing). The project health is strong—feature development and cleanup are proceeding in parallel, with several user‑facing capabilities (manual automation firing, actionable run‑gate notifications) landing this week.

## 2. Releases
*No new releases today.*

## 3. Project Progress
**Merged / closed PRs (today):**
- [#7729](https://github.com/nearai/ironclaw/pull/7729) – **feat(automations): add run‑now across trigger domain and WebUI** (closes #7193). Enables on‑demand automation firing from the model, product surface, and WebUI.
- [#7738](https://github.com/nearai/ironclaw/pull/7738) – **feat(slack): per‑field help text on the Slack deployment configuration card**.
- [#7763](https://github.com/nearai/ironclaw/pull/7763) – **docs(subagent): consolidate seven design docs into one canonical README** (−9,713 lines).
- [#7777](https://github.com/nearai/ironclaw/pull/7777) – **fix(ci): clear the clippy 1.98 lint cascade blocking the merge queue**.
- [#7778](https://github.com/nearai/ironclaw/pull/7778) – **fix(lints): Rust 1.98 clippy migration** (zero errors on `–D warnings`).
- [#7304](https://github.com/nearai/ironclaw/pull/7304) – **refactor(webui): place OAuth sign‑in above the gateway token form on login**.

**Key open PRs advancing features:**
- [#7765](https://github.com/nearai/ironclaw/pull/7765) – **feat(hooks): AfterTurn lifecycle point + memory curation as its first consumer** (phase 1 of #7770).
- [#7779](https://github.com/nearai/ironclaw/pull/7779) – **feat(sandbox): route user‑sandbox egress through a managed per‑user proxy** (step 2 of #7732).
- [#7699](https://github.com/nearai/ironclaw/pull/7699) – **feat(notifications): publish actionable run gates** (approval‑required, auth‑required, blocked‑run events).
- [#7750](https://github.com/nearai/ironclaw/pull/7750) – **chore(webui): integrate Storybook + design‑system catalog** (Epic phase 1).

**Cleanup & refactors:**
- [#7785](https://github.com/nearai/ironclaw/issues/7785) – split executor test‑support catch‑all.
- [#7784](https://github.com/nearai/ironclaw/issues/7784) – extract capability‑port test forest from production adapter.
- [#7773](https://github.com/nearai/ironclaw/pull/7773) – remove duplicate Settings and Extensions tabs.

## 4. Community Hot Topics
**Most discussed issues (by comments):**
- [#7732](https://github.com/nearai/ironclaw/issues/7732) – **Epic: Persistent per‑user sandbox with iron‑proxy** (8 comments). *Underlying need:* users require a durable, tenant‑isolated sandbox that survives per‑command container churn; the proxy sidecar is seen as essential for secure multi‑user deployments.
- [#7770](https://github.com/nearai/ironclaw/issues/7770) – **Epic: hook the agent lifecycle** (3 comments). *Underlying need:* extensibility is a core adoption driver; the community wants “when X happens, do Y” to be expressible via hooks rather than core edits.
- [#7038](https://github.com/nearai/ironclaw/issues/7038) – **Epic: Design System Phase 1** (2 comments). *Underlying need:* a consistent WebUI component library is required before the product can scale its interface.

**Most active PRs (open):**
- [#7765](https://github.com/nearai/ironclaw/pull/7765) – AfterTurn hook implementation (first consumer: memory curation).
- [#7779](https://github.com/nearai/ironclaw/pull/7779) – per‑user sandbox proxy egress.
- [#7699](https://github.com/nearai/ironclaw/pull/7699) – actionable run‑gate notifications.

## 5. Bugs & Stability
| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **High** | [#7783](https://github.com/nearai/ironclaw/issues/7783) | LLM timeout policy: finalization cannot measure TTFT; retry budget cannot fit the 75s deadline. A single transport stall can kill a structured‑output run. | None yet |
| **Medium** | [#7776](https://github.com/nearai/ironclaw/issues/7776) | `memory.write` with `append: false` is a read‑modify‑write; CAS protects against torn writes but not concurrent overwrites. Needs an `expected‑version` (compare‑and‑swap) mode. | None yet |
| **Low** | [#7767](https://github.com/nearai/ironclaw/issues/7767) | Automation presenter date tests assume UTC; fail in non‑UTC timezones (e.g., Asia/Shanghai). | No open PR |
| **Medium** | [#7308](https://github.com/nearai/ironclaw/issues/7308) *(closed)* | Hosted MCP OAuth registration for Attio fails with invalid scope; cannot be corrected. | Closed (likely fixed upstream or deferred) |

*Note:* The daily failure taxonomy (#7771) reports 58 non‑passing OfficeQA runs, “overwhelmingly genuine model‑quality errors” rather than system regressions.

## 6. Feature Requests & Roadmap Signals
- **AfterTurn lifecycle hook** (#7770 / #7765) – first act‑capable hook point; memory curation is its initial consumer.
- **Unbound runs skip gating** (#7775) – background work should not abort when a capability is unsupported; instead, gate posture should be preserved.
- **Extension setup visibility** (#7769) – surface setup phase and blockers in Configure; currently only OAuth auth‑selection is handled.
- **Persistent sandbox with per‑user proxy** (#7732 / #7779) – egress flows through `ironsh/iron‑proxy` sidecar instead of `--network none`.
- **Manual automation firing** (#7193 / #7729) – already merged; full automation surface now includes run‑now.
- **Design System Phases 2–5** (#7781, #7782) – governance, theme reskin, agentic interactions, and information‑architecture rollout.

*Predicted for next release (v1.4.0):* AfterTurn hook, unbound‑run gate posture, sandbox proxy egress, and Design System Phases 2–3.

## 7. User Feedback Summary
**Pain points expressed in issues:**
- LLM timeout finalization is opaque

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-21

## 1. Today's Overview

LobsterAI shows moderate development activity with 7 PRs updated in the last 24 hours (1 open, 6 merged/closed) and 2 open issues. No new releases were published today, indicating the team is focused on iterative bug fixes and feature refinements rather than major version releases. The project continues to see consistent contributor engagement across UI improvements, bug fixes, and settings navigation enhancements. Community-maintained issues marked as stale suggest some long-open items may need maintainer attention.

## 2. Releases

**No new releases** were published today.

## 3. Project Progress

**6 Merged/Closed PRs today:**

| PR | Author | Summary |
|----|--------|---------|
| [#1545](https://github.com/netease-youdao/LobsterAI/issues/1545) | stone333 | **Fix:** Syncs `activeSkillIds` immediately when updating an agent's skills, resolving the issue where skill badges didn't update without switching agents ([Fixes #1502](https://github.com/netease-youdao/LobsterAI/issues/1502)) |
| [#1546](https://github.com/netease-youdao/LobsterAI/issues/1546) | 0xFLX | **Feat:** Adds "Cancel Startup" and "View Logs" buttons to the engine overlay after 30 seconds, giving users an escape hatch when the OpenClaw engine startup hangs |
| [#1553](https://github.com/netease-youdao/LobsterAI/issues/1553) | noransu | **Feat:** Implements Write tool file cards (FileCard) with inline display and a resizable right-side preview panel (FilePreviewPanel, 320–900px) supporting Markdown, HTML sandbox, SVG, images, and syntax-highlighted code ([Closes #1552](https://github.com/netease-youdao/LobsterAI/issues/1552)) |
| [#1555](https://github.com/netease-youdao/LobsterAI/issues/1555) | liulingfeng | **Fix:** Resolves macOS `npm run dist:mac:x64` build failure by adding `shasum` compatibility to `build-openclaw-runtime.sh` (replacing `sha256sum` which macOS doesn't support natively) |
| [#1557](https://github.com/netease-youdao/LobsterAI/issues/1557) | kayo5994 | **Feat:** Adds a searchable filter to the settings panel sidebar, supporting NFKC-normalized multi-keyword AND matching across i18n labels with automatic tab fallback |
| [#1560](https://github.com/netease-youdao/LobsterAI/issues/1560) | flowell | **Fix:** Resolves a navigation bug where clicking an already-selected agent after editing in "My Agents" failed to switch back to the chat interface |

**1 Open PR:**

| PR | Author | Summary |
|----|--------|---------|
| [#1547](https://github.com/netease-youdao/LobsterAI/issues/1547) | gongzhi-netease | **Fix (open):** Scheduled task notification channel cannot be reset to "Do Not Notify" — fix patch available but not yet merged |

## 4. Community Hot Topics

- **[Issue #1552](https://github.com/netease-youdao/LobsterAI/issues/1552)** — *AI产物 Markdown 预览及文件卡片支持* (1 comment, created 2026-04-08): One of the most-discussed feature requests. Users repeatedly need inline preview for files generated by the Write tool (Markdown, HTML, code). **Status: Addressed** — PR #1553 merged with full file card + preview panel implementation.

- **[Issue #1556](https://github.com/netease-youdao/LobsterAI/issues/1556)** — *IM机器人配置指南404* (2 comments, created 2026-04-08): A broken documentation link on `lobsterai.youdao.com` remains unresolved. Reflects a broader content maintenance gap.

- **[PR #1547](https://github.com/netease-youdao/LobsterAI/issues/1547)** — Open PR fixing a UX bug where the notification channel dropdown doesn't reset to "Do Not Notify." Signals ongoing interest in scheduled task configurability.

**Underlying need:** Users are demanding better **in-app file workflow** (preview, manage, navigate) and **settings discoverability**, indicating the product is maturing beyond early-stage agent setup into daily-document-workflow territory.

## 5. Bugs & Stability

| Severity | Bug | PR Fix |
|----------|-----|--------|
| **Medium** | [#1560](https://github.com/netease-youdao/LobsterAI/issues/1560) — Agent list navigation fails to return to chat after editing (merged ✅) | [#1560](https://github.com/netease-youdao/LobsterAI/pull/1560) |
| **Medium** | [#1547](https://github.com/netease-youdao/LobsterAI/issues/1547) — Scheduled task notification channel stuck after switching to "Do Not Notify" (open ⏳) | [#1547](https://github.com/netease-youdao/LobsterAI/pull/1547) |
| **Low** | [#1555](https://github.com/netease-youdao/LobsterAI/issues/1555) — macOS build failure due to `sha256sum`/`shasum` incompatibility (merged ✅) | [#1555](https://github.com/netease-youdao/LobsterAI/pull/1555) |
| **Low** | [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) — IM配置指南 404 (unresolved) | — |

No crashes or regressions were reported today. The build infrastructure fix for macOS is notable for contributors who package from source.

## 6. Feature Requests & Roadmap Signals

| Request | Signal Strength | Notes |
|---------|----------------|-------|
| In-app file preview & file cards (Write tool output) | **High** | #1552 → #1553 merged; signals strong demand for document-generation workflows |
| Settings panel search/filter | **High** | #1557 merged; suggests settings complexity is growing and discoverability is a pain point |
| Engine startup escape hatch (cancel/view logs) | **Medium** | #1546 merged; users hit long timeouts and need visibility/control |
| Scheduled task notification configurability | **Medium** | #1547 open; users want fine-grained control over notification resets |
| IM bot configuration docs | **Low** | #1556 is a doc fix, not a feature, but broken docs hinder onboarding |

**Prediction:** The next release will likely emphasize **settings navigation improvements** and **file-centric agent outputs** (preview, side-by-side editing), as these are the most frequently requested areas.

## 7. User Feedback Summary

- **Satisfaction drivers:** Users appreciate the new file preview panel and file card for Write tool outputs — this directly solves a daily workflow pain point for document/writing scenarios.
- **Frustrations:** The "My Agents" navigation bug (#1560) caused confusion when switching between agent list and chat. The IM config doc 404 (#1556) blocks onboarding. Scheduled task notification UX is unintuitive (#1547).
- **Overall sentiment:** Positive momentum on UX polish. The project is shifting from core agent functionality toward **experience refinement** — better navigation, file management, and settings discoverability.

## 8. Backlog Watch

| Item | Age | Risk | Action Needed |
|------|-----|------|---------------|
| [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) — IM机器人配置指南404 | ~4.5 months (stale) | **Low** (doc) | Maintainer should restore or update the documentation link |
| [#1547](https://github.com/netease-youdao/LobsterAI/issues/1547) — Notification channel reset bug | ~4.5 months (open PR) | **Medium** (UX) | Review and merge PR #1547 |
| [#1552](https://github.com/netease-youdao/LobsterAI/issues/1552) — (now closed via #1553) | Resolved | — | — |

**Key concern:** Two items have been open since April 2026 and marked stale. The doc 404 (#1556) and the notification-channel fix (#1547) are low-effort, high-impact items that would improve contributor trust and user experience if addressed promptly.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-21

---

## 1. Today's Overview

Moltis recorded **6 PRs updated** in the last 24 hours with **4 still open** and **2 merged/closed**, alongside **1 new release** (v20260820.01) and **zero issues opened or closed**. The project shows moderate, focused development activity centered on security hardening, WhatsApp channel improvements, and cross-platform compatibility. No new bugs were reported today, and the issue tracker remains quiet, suggesting a stable recent period. The two closed PRs indicate active maintenance momentum, while the remaining open PRs point to ongoing work in sandbox validation, supply-chain security, and Windows shell-hook support.

---

## 2. Releases

**v20260820.01** (2026-08-20) — A new release was published today. No detailed changelog was available in the provided data. Based on the concurrent PR activity, this release likely incorporates fixes from recently merged work including WhatsApp push-name hardcoding (PR #1218) and the configurable untrusted-turn tool ceiling (PR #1219). Users should review the full release notes on the [Moltis GitHub releases page](https://github.com/moltis-org/moltis/releases) for exact change sets and migration guidance.

---

## 3. Project Progress

### Merged / Closed Today
- **[PR #1218](https://github.com/moltis-org/moltis/pull/1218)** — *fix(whatsapp): stop hardcoding the push name to "Moltis"* (Author: vikng-dev). The WhatsApp client previously asserted a hardcoded push name that appeared in group chats regardless of bot configuration. This fix removes that behavior, allowing the configured display name to surface correctly.
- **[PR #1219](https://github.com/moltis-org/moltis/pull/1219)** — *fix(channels): make the untrusted-turn tool ceiling configurable* (Author: vikng-dev). Resolves a regression where PR #1170's deny-all tool policy for untrusted turns inadvertently removed three tools registered for the public audience and made tool policy layers 4 and 5 unreachable in shared contexts.

### Open PRs Under Active Review
- **[PR #1220](https://github.com/moltis-org/moltis/pull/1220)** — *fix(whatsapp): render Markdown in outbound messages* (Author: rubenssoto). Converts model-generated Markdown to WhatsApp-native markup at delivery time while preserving original Markdown in session history and the web UI.
- **[PR #1222](https://github.com/moltis-org/moltis/pull/1222)** — *fix(web): validate sandbox image requests* (Author: tsauvajon). Adds pre-build validation for image references and package names, restricting package checks and image builds to operator administrators.
- **[PR #1221](https://github.com/moltis-org/moltis/pull/1221)** — *fix(gateway): pin Snyk Agent Scan* (Author: tsauvajon). Pins skill security scans to Snyk Agent Scan 0.5.17 via uvx and removes the standalone mcp-scan fallback to mitigate supply-chain attacks.

---

## 4. Community Hot Topics

The most discussed items today are the security and WhatsApp channel PRs, driven by operator and end-user feedback:

| PR | Topic | Author | Activity |
|---|---|---|---|
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | Sandbox image validation & access control | tsauvajon | Open — security hardening |
| [#1221](https://github.com/moltis-org/moltis/pull/1221) | Snyk Agent Scan pinning for supply-chain security | tsauvajon | Open — security hardening |
| [#1220](https://github.com/moltis-org/moltis/pull/1220) | WhatsApp Markdown rendering | rubenssoto | Open — UX improvement |
| [#468](https://github.com/moltis-org/moltis/pull/468) | Windows shell-hook compatibility (`cmd.exe`) | jmikedupont2 | Open — long-pending fix |
| [#1218](https://github.com/moltis-org/moltis/pull/1218) | WhatsApp hardcoded push name | vikng-dev | **Closed** |
| [#1219](https://github.com/moltis-org/moltis/pull/1219) | Untrusted-turn tool ceiling configurability | vikng-dev | **Closed** |

**Underlying needs:** Operators are prioritizing **security hardening** (sandbox image validation, pinned Snyk scans) and **channel fidelity** (WhatsApp name rendering, Markdown support). The long-open PR #468 (Windows shell hooks) signals an enduring cross-platform compatibility gap that deserves maintainer attention.

---

## 5. Bugs & Stability

No new bugs or crashes were reported via issues today. Two bugs were **fixed and closed** today:

| Severity | Bug | Fix | Link |
|---|---|---|---|
| **Medium** | WhatsApp bot displayed hardcoded name "Moltis" instead of configured identity in group chats | PR #1218 (closed) | [#1218](https://github.com/moltis-org/moltis/pull/1218) |
| **High** | Untrusted-turn policy regression (PR #1170) removed public-audience tools and made policy layers 4–5 unreachable in shared channels | PR #1219 (closed) | [#1219](https://github.com/moltis-org/moltis/pull/1219) |

The PR #1219 regression is notable — it was a **high-severity policy misconfiguration** affecting tool access in multi-user/shared deployments. No open bugs or regressions remain unaddressed today.

---

## 6. Feature Requests & Roadmap Signals

Based on current PR activity and closed fixes, the following signals point toward near-term roadmap priorities:

- **WhatsApp channel polish** — Three consecutive WhatsApp-focused PRs (#1218, #1219, #1220) suggest the team is actively maturing the WhatsApp integration. Markdown rendering (#1220) and display-name correctness are likely to land in the next release.
- **Security hardening as a sustained theme** — Pinned Snyk scans (#1221) and sandbox image validation (#1222) indicate a continued shift toward supply-chain and runtime security, likely driven by operator demand.
- **Windows compatibility** — PR #468 (open since March 2026) proposes `cmd.exe /C` for shell hooks on Windows. Its continued openness suggests it's queued but not yet prioritized; however, operator demand for Windows support remains a visible need.

**Predicted for next release:** WhatsApp Markdown rendering, sandbox image validation, and Snyk scan pinning are strong candidates for the next patch release given their open status and security/UX relevance.

---

## 7. User Feedback Summary

- **Pain point — WhatsApp identity:** Users configuring bots with custom names (e.g., "Ada") were frustrated to see "Moltis" displayed in group chats. This has been resolved in PR #1218.
- **Pain point — Tool access regression:** Operators sharing channels experienced unexpected tool denials after PR #1170, with public-audience tools and higher policy layers becoming unreachable. Addressed in PR #1219.
- **Pain point — WhatsApp Markdown:** Model-generated Markdown was not rendering correctly in WhatsApp messages, degrading UX. PR #1220 addresses this by converting to WhatsApp-native markup at delivery.
- **Satisfaction signal:** The WhatsApp channel is receiving focused improvement effort, and security fixes are being shipped promptly. The project appears responsive to operator feedback on access control and channel fidelity.

---

## 8. Backlog Watch

| PR | Age | Description | Risk |
|---|---|---|---|
| [#468](https://github.com/moltis-org/moltis/pull/468) | **5 months** (open since 2026-03-23) | Windows shell hooks fail due to missing `sh -c`; proposes `cmd.exe /C` fallback | **High** — Blocks Windows operator deployments |

**PR #468** is the most concerning backlog item. It has been open for approximately five months and addresses a fundamental compatibility gap for Windows users. Maintainer attention is recommended to either merge, request additional testing, or close with documentation.

---

*Digest generated from GitHub data as of 2026-08-21. Source: [moltis-org/moltis](https://github.com/moltis-org/moltis)*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-21

## 1. Today's Overview

QwenPaw (agentscope-ai/CoPaw) remains in an active development cycle around the v2.1.x beta series, with **28 issues** and **50 PRs** updated in the past 24 hours. The project is shipping a steady cadence of bug fixes and UX improvements alongside ambitious new features such as a self-hosted multi-user Hub (#7112) and workspace-scoped always-on Skills (#7183). Today's release, **v2.1.1-beta.1**, is a small beta patch focused on console navigation and provider logging. The open-issue count (14 of 28) is healthy, and several critical stability bugs—history.db bloat, streaming retry gaps, and orphaned tool messages—have been closed or are actively being addressed. Overall project health is **strong**, with consistent contributor engagement and a clear trajectory toward a polished v2.1 release.

---

## 2. Releases

### v2.1.1-beta.1
**Release page:** https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.1.1-beta.1

| PR | Change |
|---|---|
| [#6983](https://github.com/agentscope-ai/QwenPaw/pull/6983) | `feat(console)`: improve editor tab overflow navigation |
| [#6988](https://github.com/agentscope-ai/QwenPaw/pull/6988) | `feat(providers)`: lower rate-limiter init log level |
| — | Update release notes |

No breaking changes noted. Migration notes: none required for this beta patch.

---

## 3. Project Progress

### Merged / Closed PRs (today)
- [#7186](https://github.com/agentscope-ai/QwenPaw/pull/7186) — **Datapaw** now installable via `pip install qwenpaw[datapaw]` with a docker-compose one-shot demo and env-inheritance fix.
- [#6947](https://github.com/agentscope-ai/QwenPaw/pull/6947) — **Scroll context rebuild**: orphaned `role="tool"` messages are now dropped at the seam, fixing DeepSeek/OAI context corruption.
- [#7119](https://github.com/agentscope-ai/QwenPaw/pull/7119) — **Security**: master key file now written with `0o600` permissions as documented.
- [#7161](https://github.com/agentscope-ai/QwenPaw/pull/7161) — **Console**: assistant response cards now include artifacts.
- [#7174](https://github.com/agentscope-ai/QwenPaw/pull/7174) — **Drivers**: persistent drivers initialized concurrently at workspace startup, reducing cold-start latency.
- [#6880](https://github.com/agentscope-ai/QwenPaw/pull/6880) — **Marketplace**: apps, plugins, and skills unified under a single `/market` interface.
- [#6371](https://github.com/agentscope-ai/QwenPaw/pull/6371) — **File handling**: downloader fallback chain now correctly proceeds after `TimeoutExpired`.

### In Review / Open PRs of Note
- [#7112](https://github.com/agentscope-ai/QwenPaw/pull/7112) — **QwenPaw Hub**: self-hosted multi-user control plane (first-time production-grade feature).
- [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) — **PowerContext**: pluggable long-term memory backend option.
- [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) — **Always-on Skills**: workspace-scoped skill preloading before first agent decision.
- [#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133) — **ReMe 0.4.1.8** update with configurable embedding timeout.
- [#7176](https://github.com/agentscope-ai/QwenPaw/pull/7176) — **Console perf**: long-session responsiveness via deferred Markdown re-parsing.
- [#7167](https://github.com/agentscope-ai/QwenPaw/pull/7167) — **Creator**: dialogue-gated video dispatch, expanded effects library, project copy/recreate.

---

## 4. Community Hot Topics

| Issue | Status | Comments | 👍 | Topic |
|---|---|---|---|---|
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | OPEN | 10 | 0 | Agent stops mid-task after planning messages |
| [#7102](https://github.com/agentscope-ai/QwenPaw/issues/7102) | CLOSED | 9 | 0 | Freeze >10 min with GLM 5.3 |
| [#6643](https://github.com/agentscope-ai/QwenPaw/issues/6643) | CLOSED | 6 | 0 | Task output directory organization |
| [#6436](https://github.com/agentscope-ai/QwenPaw/issues/6436) | OPEN | 4 | 1 | Automatic model routing |
| [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) | CLOSED | 4 | 0 | Assistant message end-time display bug |
| [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | OPEN | 3 | 0 | Unified tool panel + web preview + terminal |

**Underlying needs:**
- **Task continuity** (#6921) is the top pain point—users report the agent planning steps but never executing them, a pattern that suggests the Scroll context rebuild or tool-message pairing is dropping execution triggers. This aligns with the recently merged fix in #6947.
- **Memory/history management** is a recurring theme: the 7.6 GB `history.db` bloat (#7168, now closed) and the proposal for cross-session recall toggles (#7184) show users want better control over context window costs.
- **Channel extensibility** (QQ, DingTalk) is actively requested (#7159, #7158), indicating the community is pushing QwenPaw beyond standalone console use into multi-platform agent deployments.
- **UX polish**—renaming "New Chat" to "New Task" (#6734, closed), optimizing agent-switch dropdowns (#7179), and reorganizing the deploy page (#7177)—reflects a user base that has moved past prototype-stage and demands production-grade ergonomics.

---

## 5. Bugs & Stability

| Severity | Issue | Status | Summary | Fix PR |
|---|---|---|---|---|
| **Critical** | [#7168](https://github.com/agentscope-ai/QwenPaw/issues/7168) | ✅ CLOSED | `history.db` grew to 7.6 GB due to `ToolResultCapMiddleware` writing full tool outputs on every `recall_history` expand; duplicates also written | Merged (details in close) |
| **Critical** | [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | 🔴 OPEN | Agent plans next steps but stops execution silently; requires user "continue" to proceed | Likely addressed by [#6947](https://github.com/agentscope-ai/QwenPaw/pull/6947) (merged) — awaiting user confirmation |
| **High** | [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | 🔴 OPEN | Embedding health check times out at 5s even when Ollama is warmed; timeout is hardcoded with no config | PR [#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133) adds configurable per-attempt timeout |
| **High** | [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) | 🔴 OPEN | Network restore after brief interruption does not auto-recover; all LLM requests continue to timeout | No fix PR yet |
| **High** | [#7162](https://github.com/agentscope-ai/QwenPaw/issues/7162) | ✅ CLOSED | `httpx.ReadError` mid-stream causes `UNKNOWN_AGENT_ERROR`; `_get_httpx_retryable()` missed `ReadError` | Merged (details in close) |
| **Medium** | [#7110](https://github.com/agentscope-ai/QwenPaw/issues/7110) | ✅ CLOSED | Unreachable image URL in conversation history breaks entire session; only `/clear` helps | Merged (details in close) |
| **Medium** | [#7118](https://github.com/agentscope-ai/QwenPaw/issues/7118) | ✅ CLOSED | Single corrupt byte in `envs.json` silently discards all stored env vars on next write | PR [#7119](https://github.com/agentscope-ai/QwenPaw/pull/7119) |
| **Medium** | [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) | ✅ CLOSED | `view_video` inline-media cap hardcoded at 2 MB; provider `max_inline_media_bytes` ignored | PR [#7061](https://github.com/agentscope-ai/QwenPaw/pull/7061) open |
| **Low** | [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) | ✅ CLOSED | Assistant message end-time display showed seconds instead of actual 2-min think time | Merged (details in close) |
| **Low** | [#7175](https://github.com/agentscope-ai/QwenPaw/pull/7175) | 🟡 OPEN | Free model listings incomplete in console after catalog changes | PR [#7175](https://github.com/agentscope-ai/QwenPaw/pull/7175) open |

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Type | Description | Likelihood for v2.1 |
|---|---|---|---|
| [#7182](https://github.com/agentscope-ai/QwenPaw/issues/7182) / [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | Feature | Workspace-scoped always-on Skills (preloaded into system prompt) | **High** — PR already open and scoped |
| [#7112](https://github.com/agentscope-ai/QwenPaw/pull/7112) | Feature | Self-hosted multi-user QwenPaw Hub | **Medium-High** — substantial PR, likely post-v2.1 or late v2.1 |
| [#6436](https://github.com/agentscope-ai/QwenPaw/issues/6436) | Feature | Automatic model routing (small/fast/local for simple turns, vision for images, big for reasoning) | **Medium** — popular request (1 👍), no PR yet |
| [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | Feature | Unified tool panel + web preview + interactive terminal in Chat | **Medium** — broad scope, likely phased |
| [#7184](https://github.com/agentscope-ai/QwenPaw/issues/7184) | Feature | Agent-level cross-session recall toggle for Scroll | **Medium** — complements the history bloat fix |
| [#7181](https://github.com/agentscope-ai/QwenPaw/issues/7181) | Feature | Support Qwen_Code as third-party agent harness | **Low-Medium** — niche, network-restricted users |
| [#7159](https://github.com/agentscope-ai/QwenPaw/issues/7159) | Feature | QQ group scheduled message / proactive push | **Medium** — channel feature, aligns with QQ SDK push |
| [#7158](https://github.com/agentscope-ai/QwenPaw/issues/7158) | Feature | Configurable DingTalk group context modes (isolated vs. shared) | **Medium** — PR [#7169](https://github.com/agentscope-ai/QwenPaw/pull/7169) addresses related QQ isolation |
| [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) | Feature | PowerContext long-term memory backend | **Low-Medium** — optional backend, good for specialized use cases |

---

## 7. User Feedback Summary

**Pain points:**
- **Agent task discontinuity** (#6921) is the most frequently reported issue—users describe the agent stopping after planning without any visual cue, forcing manual "continue" prompts. This suggests a gap between the planning phase and the execution phase in multi-step workflows.
- **History bloat** (#7168) — users running agents long-term saw `history.db` reach 7.6 GB.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-21

## 1. Today's Overview

ZeroClaw is in a phase of intense architectural refinement and security hardening, with 100 issues/PRs updated in the past 24 hours and no releases shipped. The project is simultaneously advancing three major thrusts: a comprehensive WASM plugin migration, per-execution shell-command policy, and plugin egress/network security enforcement. Community engagement is high, particularly around RFC design discussions, though no new releases were published this cycle. The high volume of `priority:p1` items and `risk:high` labels signals that maintainers are prioritizing security-correctness over feature velocity.

---

## 2. Releases

**No new releases in the last 24 hours.** The project has not shipped a new version; all active work is on `master` branches in open PRs or RFC trackers.

---

## 3. Project Progress

**Merged / Closed (last 24h):**

- **#10194** [CLOSED] — PR reviewer CI bug fixed: the AI reviewer was publishing results after a PR had already merged, causing noise. Resolved. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10194)
- **#10111** [CLOSED] — Duplicate of a known Windows desktop entry-point issue (`TaskDialogIndirect` missing on older Windows builds). Marked duplicate and closed. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10111)
- **#9016** [CLOSED] — OpenAI tool-turn failure when `reasoning_effort` is non-`none` was resolved; the provider now correctly handles the rejection path. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9016)

**PRs advancing today (notable):**

- **#9582** — Stage 2 of plugin egress policy: every `wasi:http` request from a plugin now passes through a host-owned `PluginEgressHooks` policy before any network connection is established. Stacked on ADR-014. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9582)
- **#9584** — Stage 3 (grant ceremony): makes the egress policy user-visible and interactive during plugin install. Depends on #9582. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9584)
- **#10072** — SSRF hardening for `file_download`: classifies operator-declared NAT64 prefixes at the SSRF gate, building on the private-host gate from #10070. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/10072)
- **#9637** — CI guard for a temporary React Router RSC dependency exception; makes dependency review stricter for the one allowed GHSA. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9637)
- **#9819** — Pixel-level image validation added to prevent corrupt images from silently failing provider requests. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9819)
- **#9678** — Git shell policy arguments hardened: normalized at the command-policy boundary so allowlisting, risk classification, and path inspection share the same quote/escape-aware representation. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9678)

---

## 4. Community Hot Topics

| Issue / PR | Comments | Focus |
|---|---|---|
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Per-execution shell-command confirmation tiers (Claude Code-style allow/ask/deny) | 23 | High-risk shell command policy |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned conversation sessions & transport adapters | 22 | Architecture ownership boundary |
| [#10118](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) — Rust anti-slop policy debt remediation tracker | 16 | 307 candidates across 1,078 Rust files |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) — Decouple memory lifecycle from storage backends | 14 | Memory governance |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) — Gemini Live realtime speech-to-speech channel | 14 | Voice channel |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue for RFCs | 13 | Governance |

**Analysis:** The community is heavily engaged on **security policy boundaries** (shell commands, memory lifecycle, plugin egress) and **architectural ownership** (runtime vs. channels vs. plugins). The shell-command RFC (#7155) has been in revision since June and remains the most-discussed open issue, indicating strong user demand for granular, per-execution confirmation tiers. The anti-slop tracker (#10118) reflects an internal quality push that also matters to downstream consumers who depend on ZeroClaw's Rust surface stability.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|---|---|---|---|
| **S1** | [#9016](https://github.com/zeroclaw-labs/zeroclaw/issues/9016) | OpenAI tool turns fail when `reasoning_effort` is non-`none` | ✅ Closed/resolved |
| **S2** | [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | Interactive agent session caps context at 32k tokens, ignoring `max_context_tokens` config | In progress |
| **S2** | [#10194](https://github.com/zeroclaw-labs/zeroclaw/issues/10194) | CI reviewer publishes results after PR merge | ✅ Closed |
| **S2** | [#10106](https://github.com/zeroclaw-labs/zeroclaw/issues/10106) | Exact proxy selectors reject supported transcription services | In progress |
| **S3** | [#10103](https://github.com/zeroclaw-labs/zeroclaw/issues/10103) | ZeroCode health-status labels misaligned in French/Spanish | In progress |

**Notable regression risk:** #10068 (context cap) is a config-ignored behavior affecting users who rely on `max_context_tokens = 131072` — this is a degraded-but-not-blocked issue. #10106 affects onboarding for users with proxy configurations for transcription providers.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for Near-Term Release |
|---|---|---|
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | Per-execution shell-command confirmation tiers (allow/ask/deny) | **High** — RFC accepted, multiple revisions, high engagement |
| [#8850](https://github.com/zeroclaw-labs/zeroclaw/issues/8850) | Move optional channels/tools from compile-time features to WASM plugins | **High** — tracker in progress, enables #10076 |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | Comprehensive WASM plugin architecture (hooks/backends/capabilities) | **Medium** — depends on #8850, accepted RFC |
| [#10025](https://github.com/zeroclaw-labs/zeroclaw/issues/10025) | `zeroclaw swarm` — ephemeral agent swarms with crush-style TUI | **Medium** — accepted, needs author action |
| [#10069](https://github.com/zeroclaw-labs/zeroclaw/issues/10069) | Agent portability (export/share bundles) | **Medium** — in progress, needs maintainer review |
| [#10168](https://github.com/zeroclaw-labs/zeroclaw/issues/10168) | Enable stall watchdog by default (`stall_timeout_secs`) | **High** — accepted, small config change |
| [#10166](https://github.com/zeroclaw-labs/zeroclaw/issues/10166) | Default `stream_mode` to `partial` | **High** — accepted, small config change |
| [#4668](https://github.com/zeroclaw-labs/zeroclaw/issues/4668) | MariaDB memory backend support | **Low** — accepted but low engagement (2 comments) |
| [#8398](https://github.com/zeroclaw-labs/zeroclaw/issues/8398) | Plugin permission/config/secrets model | **Medium** — open questions unresolved, needs author action |

**Predicted next-release inclusions:** The two config-default changes (#10166 streaming, #10168 stall watchdog) are low-risk and accepted. The shell-command policy RFC (#7155) and WASM plugin migration (#8850/#10076) are the most likely feature candidates.

---

## 7. User Feedback Summary

**Pain points surfaced:**

- **Context cap confusion:** Users configuring `max_context_tokens = 131072` are surprised the interactive agent still caps at 32k (#10068). This suggests documentation or config precedence needs clarification.
- **Transcription proxy rejection:** Users behind corporate proxies report that supported transcription services (Deepgram, AssemblyAI, etc.) fail because exact proxy selectors don't match the service keys (#10106).
- **Paste during active turns discarded:** ZeroCode silently drops pasted input while a turn is active, breaking workflow for users who rely on paste-heavy interaction (#10150, fix PR open).
- **Shared group-chat sessions cross-contaminate:** Telegram group users report that one person's file upload/context bleeds into another's follow-up question in the same group (#9772).
- **Memory isolation confusion:** ZeroCode's Code pane doesn't share persistent memory with Chat, but this boundary wasn't visible in the UI, leading to user misunderstanding (#9341).

**Satisfaction signals:** The community actively engages with RFCs (high comment counts on design issues) and contributes fixes (e.g., #9819 image validation, #9678 shell policy hardening), indicating a healthy contributor base.

---

## 8. Backlog Watch

| Issue | Days Open | Blocker |
|---|---|---|
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell confirmation tiers | ~79 days | Awaiting final normative scope sign-off; revision 3 accepted by maintainer |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned sessions | ~24 days | Awaiting `needs-maintainer-review`; coordinates with #9488/#9600 |
| [#8398](https://github.com/zeroclaw-labs/zeroclaw/issues/8398) — Plugin permission model | ~55 days | `needs-author-action` and `needs-maintainer-review`; two prior models rejected |
| [#10025](https://github.com/zeroclaw-labs/zeroclaw/issues/10025) — Swarm TUI | ~36 days | `needs-author-action`; design RFC accepted but implementation stalled |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue | ~48 days | Tracker needs sustained maintainer triage to unblock dependent RFCs |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) — Memory lifecycle decoupling | ~91 days | Long-standing; `needs-maintainer-review`; blocks backend consolidation |

**Key risk:** The maintainers' decision queue (#8692) is itself a tracker for unresolved RFCs. Until that queue is reduced, dependent features (shell policy, plugin permissions, memory lifecycle) will continue to stall. The 307 anti-slop candidates in the Rust crate (#10118) also represent a significant debt item that could delay a future release if not addressed before the next version boundary.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*