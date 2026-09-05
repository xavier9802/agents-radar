# OpenClaw Ecosystem Digest 2026-09-05

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-05 03:58 UTC

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



# OpenClaw Project Digest — 2026-09-05

## 1. Today's Overview

OpenClaw is experiencing extremely high activity with 500 issues and 500 PRs updated in the last 24 hours, signaling a period of intense triage and remediation. The project has **no new releases**, suggesting the team is in a stabilization cycle absorbing a backlog of critical bugs rather than pushing features. Of the 500 issues reviewed today, 105 were closed while 395 remain open/active — a ~1:4 closure ratio that indicates significant unresolved pressure. Multiple P0-rated bugs and several platinum hermit-class issues were updated today, many related to session-state integrity, crash loops, and auth-provider failures. The overall health picture is one of a maturing platform confronting growing pains at scale, with active fix PRs covering the most damaging failure modes.

## 2. Releases

**No new releases were published today.** The most recent referenced versions in issues and PRs are `2026.8.1`, `2026.8.2`, and beta tracks `2026.7.x`/`2026.7.2-beta.7`.

## 3. Project Progress

**Key PRs advanced or merged today:**

- **#138731** — `fix(a2a): preserve tasks while reserving commands for users` — Addresses authenticated A2A peers incorrectly executing user slash commands during task submission. [PR #138731](https://github.com/openclaw/openclaw/pull/138731)
- **#138830** — `fix(transcripts): preserve capture identity across startup retries` — Fixes continuous transcript auto-start becoming permanently stuck after a failed provider startup due to SQLite daily-selector conflicts. [PR #138830](https://github.com/openclaw/openclaw/pull/138830)
- **#138798** — `fix(memory): bound overlap carry so chunks stay within the char budget` — Resolves `400: input length exceeds context length` errors when memory files contain long lines (e.g., repeated staged-media paths). [PR #138798](https://github.com/openclaw/openclaw/pull/138798)
- **#138829** — `fix(outbound): stop details blank-line trimming from backtracking` — Fixes quadratic regex backtracking in `trimMarkdownBlankLines` that degrades performance on messages with long blank-line runs. [PR #138829](https://github.com/openclaw/openclaw/pull/138829)
- **#138818** — `fix(gateway): stop repeated teardown after WebSocket failures` — Stops a WebSocket disconnect from repeatedly tearing down the same failed connection and emitting cascading errors. [PR #138818](https://github.com/openclaw/openclaw/pull/138818)
- **#138776** — `fix(ci): stabilize Control UI stream and recovery tests` — Fixes two flaky Control UI browser fixtures related to zero-delay timer clamping and responsive geometry timing. [PR #138776](https://github.com/openclaw/openclaw/pull/138776)
- **#138832** — `perf(plugins): avoid repeated installed record scans` — Eliminates quadratic plugin-inventory scans that grow with installed plugin count. [PR #138832](https://github.com/openclaw/openclaw/pull/138832)
- **#136073** — `perf: avoid temporary arrays when selecting redaction captures` — Reduces allocation overhead in log redaction and approval-display masking. [PR #136073](https://github.com/openclaw/openclaw/pull/136073)
- **#138816** [CLOSED] — `refactor(logbook): type reads and bound observation queries` — Applies existing Kysely boundaries and 200-observation limits to logbook reads, replacing handwritten SQL. [PR #138816](https://github.com/openclaw/openclaw/pull/138816)

**Large-scale efforts in progress:**
- **#136257** — `feat(models): direct model lists and provider login across surfaces` — Unifies model catalog and provider auth across Gateway, CLI, Control UI, and all channels. [PR #136257](https://github.com/openclaw/openclaw/pull/136257)
- **#130706** — `fix: prevent Gateway stalls with multiple workspaces` — Removes repeated plugin discovery from Gateway polling and repairs metadata-context escapes. [PR #130706](https://github.com/openclaw/openclaw/pull/130706)
- **#138780** — `feat: tune inbound batching without reconnecting channels` — Allows batch-tuning across all major channels (Discord, Slack, Telegram, iMessage, Matrix, etc.) without triggering reconnects. [PR #138780](https://github.com/openclaw/openclaw/pull/138780)

## 4. Community Hot Topics

**Most discussed issues (by comment count):**

1. **#91009** — *Codex PreToolUse hook spawns CPU-bound processes and stalls gateway RPC* (21 comments, 👍2, P0, platinum hermit) — The Codex integration's native hook relay can spawn unlimited short-lived `openclaw-hooks` processes that consume 100%+ CPU each, stalling the entire gateway. [Issue #91009](https://github.com/openclaw/openclaw/issues/91009)

2. **#48003** — *Steer mode does not inject messages mid-turn for main sessions* (20 comments, 👍4, P1, diamond lobster) — `messages.queue.mode: "steer"` fails to inject user messages into active turns; they queue until turn completion instead. Root cause traced to `KeyedAsyncQueue` introduced in March 2026. [Issue #48003](https://github.com/openclaw/openclaw/issues/48003)

3. **#104721** — *All tool results return literal "(see attached image)" string* (17 comments, 👍1, P0, platinum hermit, closed) — Regression where actual tool output is replaced with a placeholder string. Now closed. [Issue #104721](https://github.com/openclaw/openclaw/issues/104721)

4. **#87307** — *Matrix thread replies sent as normal replies on 2026.5.22* (15 comments, 👍1, P1, diamond lobster, closed) — Regression in Matrix channel where thread replies lose their thread context. Closed. [Issue #87307](https://github.com/openclaw/openclaw/issues/87307)

5. **#115908** — *Session transcript projection can livelock under sustained writes* (15 comments, P1, diamond lobster) — Synchronous transcript rebuild cycle occupies the Node main thread for tens of seconds, stalling all channel transports. [Issue #115908](https://github.com/openclaw/openclaw/issues/115908)

6. **#53628** — *$XDG_CONFIG_HOME not processed when installing a skill* (14 comments, 👍1, P2) — Docker deployments with `XDG_CONFIG_HOME` set in `.env` fail to resolve skill install paths correctly. [Issue #53628](https://github.com/openclaw/openclaw/issues/53628)

7. **#43367** — *Multi-agent orchestration is unstable* (14 comments, 👍1, P1, gold shrimp) — Concurrent `openclaw agents add` calls overwrite config, session locks fail, and child work detaches — making parallel multi-agent runs unreliable. [Issue #43367](https://github.com/openclaw/openclaw/issues/43367)

**Underlying needs:** The community is pushing hard on **reliability at scale** — concurrent agents, sustained write loads, and multi-workspace deployments all expose synchronization and lifecycle bugs. The steer-mode issue and the transcript livelock point to fundamental async-lifecycle gaps that need architectural attention, not just patches.

## 5. Bugs & Stability

**P0 / Critical bugs (updated today):**

| Issue | Summary | Status | Fix PR |
|-------|---------|--------|--------|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook spawns CPU-bound processes, stalls gateway RPC | Open | — |
| [#104721](https://github.com/openclaw/openclaw/issues/104721) | Tool results return literal "(see attached image)" instead of output | **Closed** | — |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | Gateway fails to start after update to 2026.7.1 | Open | — |
| [#138272](https://github.com/openclaw/openclaw/issues/138272) | Android Talk drops with "no live response owner" on task turns | Open | — |

**High-severity bugs (P1, diamond lobster / gold shrimp):**

- [#115908](https://github.com/openclaw/openclaw/issues/115908) — Transcript projection livelock under sustained writes blocks the main thread
- [#48003](https://github.com/openclaw/openclaw/issues/48003) — Steer mode mid-turn injection broken since March 2026
- [#86215](https://github.com/openclaw/openclaw/issues/86215) — Codex OAuth refresh failures wedge agents for hours (closed)
- [#107449](https://github.com/openclaw/openclaw/issues/107449) — Cron tool JSON Schema incompatible with llama.cpp parser (closed)
- [#97616](https://github.com/openclaw/openclaw/issues/97616) — Unreaped hook/tool child processes accumulate as zombies
- [#112259](https://github.com/openclaw/openclaw/issues/112259) — Inbound channel turns silently dropped with zero-payload dispatch, no retry or dead-letter
- [#70903](https://github.com/openclaw/openclaw/issues/70903) — Persistent file-based provider cooldown blocks users for hours after billing recovery
- [#131150](https://github.com/openclaw/openclaw/issues/131150) — Slack DMs silently dropped after gateway restart (multi-account socket mode)
- [#99947](https://github.com/openclaw/openclaw/issues/99947) — Codex harness mirrored-session-history read fails for ephemeral sessions
- [#114234](https://github.com/openclaw/openclaw/issues/114234) — Usage-cost refresh lock never releasable after restart in containers (PID reuse)
- [#120162](https://github.com/openclaw/openclaw/issues/120162) — Safeguard compaction qualityGuard audit killed by same timeout as summarization
- [#119720](https://github.com/openclaw/openclaw/issues/119720) — Synchronous agent persistence blocks Gateway event loop at scale
- [#135704](https://github.com/openclaw/openclaw/issues/135704) — iMessage reflections with `reply_to_guid` bypass echo cache
- [#118018](https://github.com/openclaw/openclaw/issues/118018) — Stale subagent completion delivered into replaced requester lifecycle
- [#118793](https://github.com/openclaw/openclaw/issues/118793) — Claude CLI session-limit error dies instead of triggering model fallback
- [#71689](https://github.com/openclaw/openclaw/issues/71689) — Tasks registry restore fails on malformed SQLite
- [#95840](https://github.com/openclaw/openclaw/issues/95840) — `contextPruning mode: cache-ttl` never fires on OpenAI (fixed by [#127992](https://github.com/openclaw/openclaw/pull/127992))
- [#138590](https://github.com/openclaw/openclaw/issues/138590) — Control UI context meter measures against catalog window, not effective budget (fixed by [#138666](https://github.com/openclaw/openclaw/pull/138666))

**Regressions noted today:**
- [#119087](https://github.com/openclaw/openclaw/issues/119087) — Gateway cold start regressed ~2.5x from 2026.7.1-beta.1 to 2026.7.2-beta.7 on 1-vCPU containers

**Closed bugs today:** #104721, #87307, #86215, #107449, #84393, #69008

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Priority |
|-------|---------|----------|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built-in headless browser for reliable web access without external dependencies | P3 (tidepool) |
| [#41366](https://github.com/openclaw/openclaw/issues/41366) | Durable natural-language rule learning + explicit multi-mention reply semantics | P3 (tidepool) |
| [#16670](https://github.com/openclaw/openclaw/issues/16670) | Onboarding wizard: Memory/Embedding setup as mandatory step | P2 (tidepool) |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | Expose resolved backend model in `session_status` and agent runtime | P2 (tidepool) |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent-triggered context compaction (self-compact tool) | P2 (tidepool) |
| [#45501](https://github.com/openclaw/openclaw/issues/45501) | `session.resetPrompt` — configurable session startup message | P3 (tidepool) |
| [#55249](https://github.com/openclaw/openclaw/issues/55249) | Session labels / nicknames for easier identification | P3 (tidepool) |
| [#28300](https://github.com/openclaw/openclaw/issues/28300) | Theme Customization System — Preset Themes + Custom Theme Studio | P3 (tidepool, 👍5) |
| [#42276](https://github.com/openclaw/openclaw/issues/42276) | Reasoning stream — write/overwrite lines like OpenAI/Grok thinking indicators | P3 (diamond lobster) |
| [#87362](https://github.com/openclaw/openclaw/issues/87362) | Emit task flow lifecycle hook events for plugin observability | P3 (tidepool) |
| [#88032](https://github.com/openclaw/openclaw/issues/88032) | Telegram quote/reply as first-class durable inbound contract | P2 (tidepool) |
| [#112375](https://github.com/openclaw/openclaw/issues/112375) | Cron shell precheck gate to skip LLM when no work | P2 (silver shellfish) |
| [#134815](https://github.com/openclaw/openclaw/issues/134815) | Allow OpenAI OAuth for Reef guard classification | P2 (gold shrimp) |

**Near-term roadmap predictions:** The `session.resetPrompt` configurability (#45501), session labels (#55249), and the Cron precheck gate (#112375) are all scoped as small-to-medium improvements with clear user demand and are likely candidates for the next patch release. The theme customization system (#28300) has the highest reaction count (👍5) among feature requests. The reasoning stream feature (#42276) is marked diamond lobster priority despite P3 classification, suggesting latent high demand.

## 7. User Feedback Summary

**Pain points dominating user reports:**

- **Session integrity under load:** Multiple users report silent message loss, livelocking transcripts, and subagent completions delivered to wrong lifecycles (#115908, #112

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date: 2026-09-05**

---

## 1. Ecosystem Overview

The open-source personal AI agent ecosystem is experiencing a **stabilization-and-scaling** phase across the board. Nine of twelve tracked projects show active development, but the dominant pattern is not feature discovery—it is **production reliability work**: crash loops, memory leaks, session lifecycle bugs, and multi-tenant deployment gaps. A handful of projects (LobsterAI, NanoBot) are still shipping rapid releases, while most (OpenClaw, Hermes, ZeroClaw, CoPaw) are in intense triage cycles absorbing critical bug backlogs. The ecosystem is maturing from experimental prototypes toward deployable infrastructure, with clear fragmentation along axes of architecture (Rust vs. TypeScript/Node), deployment model (desktop vs. container vs. cloud), and channel focus (Telegram, Feishu, WhatsApp, Discord).

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release (48h) | Closed/Open Ratio | Health Signal |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | None | 105/395 (~1:4) | ⚠️ Stabilization overload |
| **ZeroClaw** | 34 | 50 | v0.8.5 bumped (unpublished) | 24/10 | 🟡 Active stabilization |
| **CoPaw** | 23 | 26 | None (2.2.x beta) | 8/15 | 🟡 High activity, beta friction |
| **Hermes Agent** | 50 | 50 | None | 3/47 | ⚠️ Bug-heavy, fragile |
| **NanoBot** | 5 | 28 | None | ~3/2 | 🟢 High-velocity dev |
| **IronClaw** | 3 closed | 3 merged + 9 open | None | 3/0 (closed) | 🟢 Healthy resolution |
| **LobsterAI** | 1 | 33 | 2026.9.3, 2026.9.4 | 0/1 (stale) | 🟢 Rapid release cadence |
| **PicoClaw** | 3 | 22 | None | 0/1 (open) | 🟢 Strong backlog clearance |
| **NanoClaw** | 2 | 18 | None | 0/0 | 🟡 Moderate, architectural push |
| **Moltis** | 1 | 1 | None | 0/0 | 🟢 Stable, light dev |
| **NullClaw** | 1 | 0 | None | 0/0 | 🔴 Minimal activity |
| **ZeptoClaw** | 0 | 0 | None | — | 🔴 Inactive |

**Health Score Key:** 🟢 Strong / 🟡 Moderate / ⚠️ Strained / 🔴 At Risk

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Sheer scale of activity** (500 issues + 500 PRs) dwarfs all others, indicating the largest contributor base and most complex deployment surface.
- **Multi-channel depth**: Discord, Slack, Telegram, iMessage, Matrix — unmatched channel coverage.
- **Multi-agent orchestration** is a first-class concern; no other project addresses concurrent agent lifecycle bugs as critically.

**Technical Approach Differences:**
- Unlike **NanoClaw** (Rust workspace, provider-contract unification) or **ZeroClaw** (Rust multi-crate), OpenClaw is TypeScript/Node, making it more accessible to JavaScript contributors but more vulnerable to event-loop stalls (evidenced by #115908 transcript livelock, #91009 Codex hook CPU spin).
- Unlike **CoPaw** (AgentScope/Qwen integration) or **Hermes** (NousResearch), OpenClaw is channel-agnostic and does not ship a bundled LLM — it is purely an orchestration layer.

**Community Size:** OpenClaw's 500-issue/24h volume suggests a community an order of magnitude larger than any peer. Hermes (~50) and CoPaw (~49) are the next tier; most others sit below 30.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Session/Transcript Integrity** | OpenClaw (#115908), Hermes (#103339 SQLite), NanoClaw (#3716 OOM), LobsterAI (#1071 SQLite), ZeroClaw (#9487 RFC) | Unbounded growth, corruption under concurrent writes, crash loops on `PreCompact` — across every architecture |
| **Provider/Channel Authentication** | OpenClaw (#138818 WebSocket teardown), NanoBot (#5644 locale race), Hermes (#103313 SSH 401), ZeroClaw (#9397 RFC WhatsApp defaults) | Stale tokens, race conditions on startup, permissive defaults in security-sensitive channels |
| **Multi-Agent / Subagent Reliability** | OpenClaw (#43367), Hermes (#103375 tile starvation), ZeroClaw (#9002 viewer disconnect), CoPaw (#7567 stop ineffective) | Child processes orphaned, completions delivered to wrong lifecycles, no recovery path |
| **Enterprise/Feishu Integration** | NanoBot (#5567), CoPaw (#7534 consumer hang), LobsterAI (cowork login gating) | Fragmented replies, silent session hangs, no streaming card consolidation |
| **Container/Deployment Reliability** | NanoClaw (#3714 env passthrough), CoPaw (#7550 Docker config loss), Hermes (#102486 systemd), OpenClaw (#53628 XDG_CONFIG) | Env vars not reaching containers, config drift on restart, PID-reuse lock failures |
| **Windows/Desktop UX** | Hermes (#103398 terminal hang, #103400 QuickEdit), PicoClaw (#3281 Web UI lag), ZeroClaw (#10609 cwd bug), LobsterAI (#2615 Unicode paths) | Terminal deadlocks, input lag, launch directory ignored, unicode path crashes |
| **Rate-Limit / Quota Management** | OpenClaw (#70903 persistent cooldown), ZeroClaw (#9419 credential rotation), NanoBot (#5665 OAuth registry unbounded) | Silent failures, unbounded cache growth, no fallback on API limits |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | NanoBot | CoPaw | ZeroClaw | LobsterAI | NanoClaw | PicoClaw | IronClaw |
|---|---|---|---|---|---|---|---|---|---|
| **Language** | TypeScript/Node | TypeScript/Node | Rust | TypeScript | Rust | Electron/JS | Rust | TypeScript | Rust |
| **Core Focus** | Multi-channel orchestration | Desktop agent + group chats | Lightweight CLI/WebUI | QwenPaw ecosystem + mobile | Secure multi-agent gateway | Consumer desktop app | Provider-contract unification | Lightweight multi-channel | Telegram-first bot |
| **Target User** | Enterprise/self-hosted devs | Power users, multi-profile | Developers, CLI users | Chinese enterprise (Feishu) | Security-conscious operators | Consumer desktop users | Platform-agnostic providers | Embedded/IoT + channel agnostic | Telegram bot operators |
| **Architecture** | Gateway + plugins + channels | Desktop app + TUI + tools | WebUI + TUI + channels | Console + Desktop + mobile | Multi-crate workspace | Electron app | Provider SDK adapters | MCP-centric | Telegram Bot API native |
| **Deployment** | Docker, K8s, bare metal | Desktop, SSH remote | CLI, WebUI, container | Desktop, Docker, mobile | Container, workspace | Desktop (Win/Mac/Linux) | Container, operator mode | Docker, bare metal | Desktop, Telegram |
| **Key Differentiator** | Channel breadth (9+ channels) | Multi-profile + group chat continuity | 0.3.0 speed + WebUI polish | Qwen integration + mobile app | Rust security + session RFCs | In-app browser + cowork | Provider unification (Codex/OpenCode/Cursor) | Tiny footprint + MCP | Telegram onboarding UX |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (Releasing Frequently):**
- **LobsterAI**: 2 releases in 48h, 33 PRs, aggressive feature push (browser, cowork, publishing)
- **NanoBot**: 28 PRs in 24h, resolving regressions while adding features (OpenCode header, aimlapi provider)

**Tier 2 — High Activity, Stabilization Phase:**
- **OpenClaw**: 500/500 volume but 1:4 closure ratio — community is large but overwhelmed by scale bugs
- **ZeroClaw**: 84 activity items, v0.8.5 stabilization, strong RFC-driven architecture (sessions, computer-use)
- **Hermes Agent**: 100 activity items, 47/3 open/closed — bug-heavy but responsive to P1 regressions
- **CoPaw**: 49 items, 2.2.x beta friction — strong community shaping multi-tenant roadmap (#7318, 22 comments)

**Tier 3 — Moderate, Focused Development:**
- **PicoClaw**: 25 items, 20/22 PRs merged — efficient backlog clearance, one outstanding UX bug (#3281)
- **NanoClaw**: 20 items, provider-contract unification in progress — architectural depth over breadth
- **IronClaw**: 15 items, healthy resolution ratio — Telegram onboarding polish sprint

**Tier 4 — Low Velocity / At Risk:**
- **Moltis**: 2 items, stable but minimal momentum
- **NullClaw**: 1 item, 12-day-old enhancement unacknowledged
- **ZeptoClaw**: 0 items, effectively dormant

---

## 7. Trend Signals

**1. Session Lifecycle is the #1 Unresolved Problem Across All Projects**
Every major project reports session integrity bugs: OpenClaw (transcript livelock), NanoClaw (PreCompact OOM), LobsterAI (SQLite CASCADE failure), Hermes (SQLite WAL corruption), ZeroClaw (RFC on runtime-owned sessions). *Signal:* The industry lacks a robust, production-tested session abstraction. Developers building agent platforms should prioritize durable, bounded, atomic session storage — this is the bottleneck.

**2. Multi-Channel Aggregation is Maturing; Multi-Agent Orchestration is Not**
Projects with single-channel focus (IronClaw → Telegram, NanoBot → Feishu/Slack) ship faster and have fewer bugs. Projects attempting multi-agent concurrency (OpenClaw, Hermes, CoPaw) face livelocks, orphaned completions, and config races. *Signal:* Multi-agent is the next hard problem — expect a wave of architectural RFCs and failed approaches before a pattern stabilizes.

**3. Provider Contract Unification is the Emerging Standard**
NanoClaw's Codex/OpenCode/Cursor provider series, ZeroClaw's OpenAI-compatible cache passthrough, and OpenClaw's unified model catalog (#136257) all point to the same need: a typed, versioned provider interface that abstracts away per-API quirks. *Signal:* Projects that ship a clean provider SDK will attract the most integrations.

**4. Chinese Enterprise Channels (Feishu, Lark, WeCom) Are a High-Friction Frontier**
NanoBot (#5567 fragmented replies), CoPaw (#7534 consumer hang), and LobsterAI (cowork login gating) all show that Chinese messaging platforms require non-trivial channel-specific work. *Signal:* This is a defensible niche — projects that solve Feishu/WeCom properly gain loyal enterprise adopters.

**5. Self-Hosting and Operator Controls Are Table Stakes**
NullClaw's Firecrawl endpoint request, NanoClaw's env passthrough gap (#3714), CoPaw's Docker config loss (#7550), and ZeroClaw's WhatsApp default-deny RFC (#9397) all reflect operator demand for configuration transparency. *Signal:* Documentation of operator controls and env var forwarding is a trust signal — missing it erodes credibility.

**6. Windows/Desktop UX Remain Systematically Under-Addressed**
Hermes (terminal hangs, QuickEdit stalls), ZeroClaw (cwd bug), PicoClaw (Web UI lag), and LobsterAI (Unicode paths) all report Windows-specific failures. *Signal:* Cross-platform parity is still a gap — projects that invest in Windows CI and terminal emulation testing will stand out.

**7. Security Hardening is Accelerating**
NanoClaw's mount-bypass fix (#3680), PicoClaw's exec preflight hardening (#2298), ZeroClaw's image marker bypass (#9882), and IronClaw's pairing flow fixes all show security is moving from afterthought to first-class concern. *Signal:* Operator-grade deployments will demand audit trails, least-privilege defaults, and explicit approval gates — projects lacking these will be excluded from enterprise consideration.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-05

---

## 1. Today's Overview

NanoBot is in a high-velocity development phase, with 33 activity items in the last 24 hours (5 issues, 28 PRs). The project is resolving several critical bugs (most notably a 0.3.0 regression on runtime context and a race-condition bug in the WebUI locale registry) while simultaneously pushing forward new features. Three PRs were merged/closed today, and seven PRs landed on priority P1/P2 items. No new release was published during this window.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Merged / Closed PRs:**

| PR | Description |
|----|-------------|
| [#5639](https://github.com/HKUDS/nanobot/pull/5639) | Stabilized session labels, TUI streaming, and pairing prompts; upgraded OpenTUI from 0.5.3 → 0.5.10 |
| [#5660](https://github/HKUDS/nanobot/pull/5660) | Added model generation speed (tokens/sec) to the WebUI context-usage popover (closes #5631) |
| [#5657](https://github/HKUDS/nanobot/pull/5657) | Refactored WebUI outbound wire encoding — extracted typed `recovery_state` and `turn_end` encoders; replaced per-event transport methods with shared `send_payload` primitive |

**Notable Open PRs Advancing Features:**
- [#5662](https://github.com/HKUDS/nanobot/pull/5662) — P1: Send `x-opencode-session` header for OpenCode session affinity (required after 2026-09-06)
- [#5656](https://github.com/HKUDS/nanobot/pull/5656) — Expose context compaction as a live channel event with structured lifecycle emissions
- [#5626](https://github.com/HKUDS/nanobot/pull/5626) — Add `copy_file` / `move_file` as first-class filesystem tools
- [#5659](https://github.com/HKUDS/nanobot/pull/5659) — Add `ephemeral` opt-out flag for runtime-context blocks
- [#5666](https://github.com/HKUDS/nanobot/pull/5666) — Integrate aimlapi.com as a built-in OpenAI-compatible provider

---

## 4. Community Hot Topics

1. **[Issue #5567](https://github.com/HKUDS/nanobot/issues/5567)** — *Feishu multi-turn reply consolidation* (4 comments)
   Users on the Feishu (Lark) channel report that a single user message can generate *n* fragmented messages (tool progress, final reply). The ask is to merge them into a single streaming card. This reflects a growing user base on Chinese messaging platforms demanding parity with native bot experiences.

2. **[Issue #5661](https://github.com/HKUDS/nanobot/issues/5661) / [PR #5662](https://github.com/HKUDS/nanobot/pull/5662)** — *OpenCode session-affinity header* (0 comments, P1 priority)
   OpenCode announced that starting 2026-09-06, requests missing the `x-opencode-session` header will lose prompt-cache optimization and may error. This is an urgent infrastructure dependency that the maintainers are already addressing with a dedicated PR.

3. **[Issue #5631](https://github.com/HKUDS/nanobot/issues/5631) → [PR #5660](https://github.com/HKUDS/nanobot/pull/5660)** — *WebUI context & speed display*
   Closely modeled after DeepSeek Harness, users want inline visibility into model speed and context usage. The feature was implemented and merged in a single day.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| 🔴 High | [#5645](https://github.com/HKUDS/nanobot/issues/5645) | **Regression in 0.3.0:** `Current Time` runtime context no longer auto-injected for direct `ContextBuilder.build_messages()` calls | No open PR yet |
| 🔴 High | [#5644](https://github.com/HKUDS/nanobot/issues/5644) | **Race condition:** `loadChannelLocale()` drops a locale when two locales load concurrently at startup | No open PR yet |
| 🟡 Medium | [#5647](https://github.com/HKUDS/nanobot/issues/5647) → [#5658](https://github.com/HKUDS/nanobot/pull/5658) | WebUI session titles not generated when WebSocket envelope omits `webui: true` flag | [#5658](https://github.com/HKUDS/nanobot/pull/5658) [OPEN] |
| 🟡 Medium | [#5665](https://github.com/HKUDS/nanobot/pull/5665) | MCP OAuth flow registry grows without bound under rapid restarts | [#5665](https://github.com/HKUDS/nanobot/pull/5665) [OPEN] |
| 🟡 Medium | [#5664](https://github.com/HKUDS/nanobot/pull/5664) | Idle-session summary cache unbounded; abandoned sessions leak memory | [#5664](https://github.com/HKUDS/nanobot/pull/5664) [OPEN] |
| 🟡 Medium | [#5663](https://github.com/HKUDS/nanobot/pull/5663) | Mattermost thread-context cache never evicted | [#5663](https://github.com/HKUDS/nanobot/pull/5663) [OPEN] |
| 🟢 Low | [#5490](https://github.com/HKUDS/nanobot/pull/5490) | WebUI aggregate turn token count was misleading when multiple prompt reports were merged | [#5490](https://github.com/HKUDS/nanobot/pull/5490) [OPEN] |

> **Note:** The 0.3.0 runtime-context regression (#5645) and the locale race condition (#5644) are the most concerning unresolved bugs today — both were closed as fixed without a linked PR in the data, suggesting they may have been addressed outside the tracked PR flow.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| Context-compaction visibility / `/compact` command | [#5656](https://github.com/HKUDS/nanobot/pull/5656) | **High** — PR is ready, aligns with multi-turn UX improvements |
| Ephemeral runtime-context blocks (opt-out of persistence) | [#5659](https://github.com/HKUDS/nanobot/pull/5659) | **High** — addresses developer need for per-request context |
| Feishu single-card streaming replies | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | **Medium** — feature request; needs channel-level redesign |
| New filesystem tools (`copy_file`, `move_file`) | [#5626](https://github.com/HKUDS/nanobot/pull/5626) | **High** — small, self-contained, fills a clear gap |
| aimlapi.com built-in provider | [#5666](https://github.com/HKUDS/nanobot/pull/5666) | **Medium** — vendor-driven; 50/50 revenue partnership offer |
| Langfuse tracing for Codex provider | [#5520](https://github.com/HKUDS/nanobot/pull/5520) | **Medium** — observability for enterprise users |
| Heartbeat in shared session / cheaper model override | [#4551](https://github.com/HKUDS/nanobot/pull/4551), [#4549](https://github.com/HKUDS/nanobot/pull/4549) | **Low–Medium** — long-open, niche use case |

**Prediction for next release:** Context compaction visibility (#5656), ephemeral runtime-context blocks (#5659), and the `copy_file`/`move_file` tools (#5626) are strong candidates. The OpenCode session header fix (#5662) is likely a hotfix priority given the 2026-09-06 deadline.

---

## 7. User Feedback Summary

- **Pain point — fragmented chat messages:** Feishu users are frustrated that one user message produces *n* bot messages (tool tips, progress, final answer). This is a UX degradation compared to native chatbot behavior.
- **Pain point — 0.3.0 regression:** Users upgrading from 0.2.2 to 0.3.0 lost the automatic `Current Time` runtime context, breaking workflows that depended on it.
- **Pain point — memory leaks under load:** Multiple unbounded caches (MCP OAuth flows, idle summaries, Mattermost thread contexts) were reported in quick succession, suggesting the project needs a systematic capacity-bounding audit.
- **Positive — WebUI observability:** Users appreciate the new model-speed and context-usage display; the feature was requested and shipped in the same day.
- **Satisfaction trend:** The community is actively engaging with bugs and providing clear reproduction steps. The maintainers are responding with both fixes and refactors (e.g., the outbound wire encoding cleanup in #5657).

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) — Feishu card consolidation | Created 2026-08-27 | No PR yet; significant channel redesign required |
| [#5645](https://github.com/HKUDS/nanobot/issues/5645) — 0.3.0 runtime-context regression | Created 2026-09-03 | Closed but no linked PR; verify fix is in main |
| [#5644](https://github.com/HKUDS/nanobot/issues/5644) — Locale race condition | Created 2026-09-03 | Closed but no linked PR; verify fix is in main |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) — Heartbeat isolated_session | Created 2026-06-26 (~3 months) | Long-standing, low-priority config request |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) — Heartbeat model_override | Created 2026-06-26 (~3 months) | Same as above |
| [#5431](https://github.com/HKUDS/nanobot/pull/5431) — Background task failure reporting | Created 2026-08-18 | Important for production reliability; still open |
| [#5379](https://github.com/HKUDS/nanobot/pull/5379) — Memory consolidation input preservation | Created 2026-08-13 | Potential data-loss regression; still open |

**Key risk:** The two long-open heartbeat PRs (#4551, #4549) have been pending for ~3 months with no movement. The background-task failure reporting PR (#5431) is also notable — it improves observability for production deployments but has lingered since mid-August.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026‑09‑05

## 1. Today's Overview
Hermes Agent shows **high daily activity** with 50 issues and 50 pull requests updated in the last 24 hours. The project is in a **bug‑heavy stabilization phase**: 47 open issues remain active, while only 3 have been closed. No new release was published today, but several **P1 regressions** surfaced—SQLite WAL corruption, SSH authentication failures, and Windows terminal hangs—each with fix PRs already submitted. Community engagement is strong, as evidenced by the top issue accumulating 157 comments. Overall project health is **active but fragile**, with core stability concerns being addressed in real time.

## 2. Releases
*No new releases today.*

## 3. Project Progress
**Closed/Merged PRs today:**
- [#103394](https://github.com/NousResearch/hermes-agent/pull/103394) – `fix(cli): propagate non‑zero exit codes on cron and webhook subcommand failures` – ensures CLI commands forwarded via `_forward_command` return proper shell exit codes, and adds explicit error exits for `hermes webhook` and `hermes cron`.

**Key open PRs advancing features/fixes:**
- [#98307](https://github.com/NousResearch/hermes-agent/pull/98307) – `feat(bot‑mode): complete Group Chat continuity, control, and files` – enables bots on the same or different gateways to exchange messages and files while Desktop is closed; addresses #97681.
- [#98073](https://github.com/NousResearch/hermes-agent/pull/98073) – `feat(bot‑mode): control Group Chats from messaging` – adds commands and native menus to inspect, message, and manage group‑chat tasks from mobile/authorized Hermes clients.
- [#103369](https://github.com/NousResearch/hermes-agent/pull/103369) – `fix(cli): resume one‑shot sessions` – preserves `--resume` when top‑level `-z/--oneshot` dispatches into oneshot mode, and loads the resumed SessionDB transcript before the oneshot turn.
- [#103399](https://github.com/NousResearch/hermes-agent/pull/103399) – `fix(desktop): prevent background tile reconcile from starving pool slots` – fixes #103375 by stopping the 10s touch loop from cold‑starting pooled backends for hidden tiles.
- [#103400](https://github.com/NousResearch/hermes-agent/pull/103400) – `fix(desktop): disable QuickEdit so Select mode cannot block update handoff` – resolves Windows 11 update stalls when QuickEdit is enabled.
- [#103402](https://github.com/NousResearch/hermes-agent/pull/103402) – `fix(tools): prevent terminal probe hang and kill orphaned processes on Windows` – addresses the Git Bash wrapper deadlock that caused terminal tool hangs.

## 4. Community Hot Topics
| Issue/PR | Comments | Highlights | Underlying Need |
|----------|----------|------------|-----------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) (OPEN) | 157 | Skills index stale/degraded (29.8h old, limit 26h) | Users rely on an up‑to‑date skills index; cron rebuild failures disrupt skill availability. |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) (OPEN) | 23 | Bot Group Chats should keep working after Desktop closes | Demand for **continuous multi‑bot group collaboration** independent of the Desktop app. |
| [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) (OPEN) | 18 👍29 | Support remote Hermes agent with local tool execution | Desire to **separate agent reasoning from local tool sandbox** (e.g., remote LLM + local filesystem/browser). |
| [#103313](https://github.com/NousResearch/hermes-agent/issues/103313) (CLOSED) | 2 | Desktop SSH remote mode 401s every sensitive API call | **SSH‑remote Desktop connectivity** is a key deployment pattern; session‑token injection regression is painful. |

**Trend:** The community is heavily focused on **reliability of distributed deployments** (group chats, SSH remote, remote agent) and **data‑freshness automation** (skills index).

## 5. Bugs & Stability
**P1 (High Severity) – reported today:**
1. [#103339](https://github.com/NousResearch/hermes-agent/issues/103339) – SQLite `state.db` corruption under multi‑profile writes; upstream guards are fail‑open. *Proposed fix:* lazy flock single‑writer gate.
2. [#102486](https://github.com/NousResearch/hermes-agent/issues/102486) – Cron worker dispatch fails closed on systemd 249 (`OOMPolicy=kill` rejected).
3. [#103313](https://github.com/NousResearch/hermes-agent/issues/103313) – Desktop SSH remote mode returns 401 on every sensitive API call due to stale session token (regression from `5f1feb5344`). **Closed.**
4. [#103054](https://github.com/NousResearch/hermes-agent/issues/103054) – Dashboard serves stale session token after `--ssh‑session‑token‑file`; same 401 pattern.
5. [#103401](https://github.com/NousResearch/hermes-agent/issues/103401) – Profile switch times out waiting for a free local‑backend slot (duplicate).
6. [#103398](https://github.com/NousResearch/hermes-agent/issues/103398) – Windows terminal tool hangs for minutes; bash startup probe deadlocks and child survives `subprocess.run` kill.

**P2 (Medium Severity) – selected:**
- [#49664](https://github.com/NousResearch/hermes-agent/issues/49664) – `display.show_reasoning` toggle has no effect (rendering code never reads it).
- [#93817](https://github.com/NousResearch/hermes-agent/issues/93817) – Reasoning Blocks off still dumps entire agent trace (P0‑usability).
- [#85110](https://github.com/NousResearch/hermes-agent/issues/85110) – Desktop/TUI cannot hide thinking + tool/prompt‑call chrome (answer‑only broken across all APIs).
- [#100610](https://github.com/NousResearch/hermes-agent/issues/100610) – `pip install` from UI fails in podman/Docker containers (`messaging` toolset removal leftover).
- [#103375](https://github.com/NousResearch/hermes-agent/issues/103375) – Bot tiles auto‑reconnect in infinite loop, starving local‑backend pool (fix PR #103399 open).

**Fix PRs already in flight:**
- Terminal/Windows hangs: [#103402](https://github.com/NousResearch/hermes-agent/pull/103402)
- Background tile starvation: [#103399](https://github.com/NousResearch/hermes-agent/pull/103399)
- QuickEdit update stall: [#103400](https://github.com/NousResearch/hermes-agent/pull/103400)
- SQLite corruption: no fix PR yet; proposal in issue.

## 6. Feature Requests & Roadmap Signals
| Issue | Description | Likelihood for Next Release |
|-------|-------------|-----------------------------|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Bot Group Chats keep working after Desktop closes | **High** – PR #98307 is the complete field build. |
| [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) | Remote Hermes agent with local tool execution | Medium – architectural decision needed; 29 👍. |
| [#100428](https://github.com/NousResearch/hermes-agent/issues/100428) | `browser_exec` headed/headless per session | Low – niche use case. |
| [#100944](https://github.com/NousResearch/hermes-agent/issues/100944) | Kanban: deny worker create/link per profile | Low – scoped workflow request. |
| [#45562](https://github.com/NousResearch/hermes-agent/issues/45562) | Desktop preserve per‑session chat scroll position | Low – UX polish. |

**Signal:** The roadmap is heavily weighted toward **group‑chat continuity** and **remote/local decoupling**, with immediate stability fixes taking precedence.

## 7. User Feedback Summary
**Pain points:**
- **Reasoning‑block visibility:** Multiple users report that disabling `display.show_reasoning` does not hide model thinking or tool‑call traces (#49664, #93817, #85110). This makes Hermes Desktop unusable for users who want clean transcripts.
- **SQLite corruption:** Multi‑profile setups suffer repeated `state.db` corruption when a second writer opens the live WAL database (#103339).
- **SSH remote authentication:** Session‑token injection regression causes every sensitive `/api/*` call to 401 after SSH connection (#103313, #103054).
- **Windows terminal hangs:** The `terminal` tool deadlocks on trivial commands because the bash startup probe child survives process kill (#103398).
- **Containerized pip installs:** Removing the `messaging` toolset left a stale reference that breaks `pip install` from the UI in podman/Docker (#52382, #100610).
- **Model‑size misclassification:** Local Models pane tags models that fit easily on unified‑memory Macs (e.g., Qwen3.8 27B on 128 GB M5 Max) as “Too big” (#102619).

**Satisfaction signals:**
- Active fix PRs for the day’s regressions show a responsive community.
- Group‑chat continuity feature is being built out with comprehensive control and mobile access.

## 8. Backlog Watch
**Long‑open issues requiring maintainer attention:**
- [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) – Skills‑index stale/degraded (157 comments, open since 2026‑07‑18). No resolution thread visible.
- [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) – Remote Hermes agent with local tool execution (29 👍, open since 2026‑05‑02). High community interest, needs decision.
- [#45562](https://github.com/NousResearch/hermes-agent/issues/45562) – Desktop per‑session scroll position (open since 2026‑06‑13).
- [#24740](https://github.com/NousResearch/hermes-agent/issues/24740) – Honcho session titles override `sessionStrategy` (open since 2026‑05‑13).
- [#96418](https://github.com/NousResearch/hermes-agent/issues/96418) – Loopback bind disables WS keepalive ping, leaking PTY child (open since 2026‑08‑27). Verified source‑level defect.

**Risk:** Several P1 bugs (SQLite corruption, SSH token regression) remain without merged fixes. If not addressed in the next release cycle, they could cause widespread deployment issues for multi‑profile and SSH‑remote users.

---
*Data sourced from GitHub API snapshot of 2026‑09‑05. Links are direct to the relevant issue or pull request on `NousResearch/hermes-agent`.*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-05

---

## 1. Today's Overview

PicoClaw saw moderate activity today with **3 open issues** updated and **22 PRs** touched in the last 24 hours — notably **20 merged/closed**, indicating a strong backlog-clearing effort by maintainers. No new release was published, suggesting today's work is primarily incremental fixes and documentation rather than a version milestone. The project remains actively maintained with steady contributor engagement across agent, provider, and channel domains.

---

## 2. Releases

**No new releases today.** The latest activity is contained within PR merges rather than versioned shipments.

---

## 3. Project Progress

**20 PRs closed/merged today**, spanning multiple subsystems:

| Area | Notable Merges |
|---|---|
| **Agent** | #3337 — Fixed agent loop hang when MCP server connection fails; #2014 — SystemParts now included in token estimation; #2016 — Improved context overflow detection for Anthropic, ZhipuAI, GLM |
| **Providers** | #1683 — OpenAI Strict Mode compatibility with fail-safe sanitization; #1858 — Thinking/reasoning fallback for Ollama-compatible providers; #1860 — Azure AI Foundry host recognition for prompt caching; #2522 — Streaming usage support for OpenAI/Azure |
| **Channels** | #1541 — Merged PRs #1536/#1535/#1531 covering media tempdir, channel DoS hardening, DeepWiki badge; #1855 — Fixed negative integer Telegram group/channel ID parsing; #2089/#2090/#2091/#2092 — Slack mention race condition, Telegram streaming draft/routing fixes, Feishu group mention detection |
| **Security** | #2088 — Security audit for open-by-default bots; #2298 — Exec script preflight hardening (fail-closed on ambiguous interpreter commands) |
| **Documentation** | #3368 — Parallel Search MCP setup example (open); #3367 — Pilot MCP setup example (open) |

**Open PRs (2):**
- [#3368](https://github.com/sipeed/picoclaw/pull/3368) — Docs: Parallel Search MCP setup example
- [#3367](https://github.com/sipeed/picoclaw/pull/3367) — Docs: Pilot MCP setup example

---

## 4. Community Hot Topics

| # | Type | Title | Comments | 👍 | Link |
|---|---|---|---|---|---|
| #3287 | Feature | Better support long messages in IRC | 10 | 0 | [Issue](https://github.com/sipeed/picoclaw/issues/3287) |
| #3281 | Bug | Web UI chat input laggy with long history | 9 | 2 | [Issue](https://github.com/sipeed/picoclaw/issues/3281) |
| #3366 | Feature | Add support for OpenAI compatible providers | 0 | 0 | [Issue](https://github.com/sipeed/picoclaw/issues/3366) |

**Analysis:**
- **IRC long-message support (#3287)** — Users are sending messages that exceed IRC's 512-byte limit and expecting PicoClaw to reassemble them into a single coherent message. This reflects a need for deeper protocol awareness in multi-platform aggregators.
- **Web UI lag (#3281)** — The most reacted-to issue (2 👍). This is a UX-critical performance problem: as chat history grows, the input box becomes unusable. Indicates a need for virtualization or pagination in the web frontend.
- **OpenAI-compatible providers (#3366)** — A fresh feature request for self-hosted router support (e.g., 9Router). While strict OpenAI compat was partially addressed in merged PR #1683, this issue suggests demand for a dedicated provider profile with configurable bases.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Status |
|---|---|---|---|
| **High** | #3337 (merged) | Agent loop hangs and stops responding when MCP server connection fails | ✅ Fixed |
| **High** | #3281 (open) | Web UI chat input becomes very laggy with moderately long history | ⚠️ Open |
| **Medium** | #1855 (merged) | Telegram group/channel negative IDs misidentified as platform names | ✅ Fixed |
| **Medium** | #2088 (merged) | Bots with empty `allow_from` default to permissive/open state (security risk) | ✅ Fixed |
| **Medium** | #2298 (merged) | Exec script preflight silently skips validation for ambiguous interpreter commands | ✅ Fixed |
| **Low** | #2090 (merged) | Telegram streaming redundant drafts lingering after message delivery | ✅ Fixed |

**Outstanding bugs:** Only **#3281** (Web UI lag) remains open. All other reported issues have associated merged fix PRs.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood | Notes |
|---|---|---|---|
| OpenAI-compatible custom provider | #3366 | **High** | Directly aligns with merged #1683 (strict mode) and #1858 (Ollama thinking fallback). Likely to be packaged as a first-class provider profile. |
| IRC long-message reassembly | #3287 | **Medium** | Protocol-level enhancement; depends on IRCv3 capabilities awareness. |
| Web UI history virtualization | #3281 (implied) | **High** | Clear UX pain point with user upvotes. Likely a frontend refactor rather than a small fix. |
| MCP documentation coverage | #3368, #3367 (open) | **Active** | Two MCP setup PRs (Parallel Search, Pilot) in review — docs expansion is a current priority. |

**Prediction for next release:** Given the volume of merged provider-channel-agent fixes (20 PRs), a patch release incorporating #1683, #1855, #2088, #2298, and #3337 is plausible. The two open doc PRs may also ship.

---

## 7. User Feedback Summary

**Pain Points:**
- **Web UI performance degrades with history** (#3281) — Users find the chat interface unusable after modest conversation length. This is the most upvoted open issue.
- **IRC message fragmentation** (#3287) — Users expect PicoClaw to handle IRC's 512-byte limit transparently and reassemble split messages.
- **Security awareness gap** — #2088 confirms users were unknowingly running open-by-default bots; the fix adds informational hardening.

**Satisfaction Signals:**
- High merge rate (20/22 PRs) shows maintainers are responsive.
- Feature requests are being addressed with targeted PRs (e.g., strict mode compat, thinking-field fallback).
- Documentation PRs indicate the community is actively contributing guides.

---

## 8. Backlog Watch

| Item | Age | Risk | Action Needed |
|---|---|---|---|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC long message support | ~45 days | Medium | Needs maintainer triage; labeled `[stale]` |
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI lag | ~46 days | **High** | Performance bug with user impact; not yet assigned a fix PR |
| [#3366](https://github.com/sipeed/picoclaw/issues/3366) — OpenAI compatible providers | ~1 day | Low | Fresh request; likely to be addressed given recent strict-mode work (#1683) |
| [#3368](https://github.com/sipeed/picoclaw/pull/3368) — Parallel Search MCP docs | 今日 | Low | Open PR awaiting review |
| [#3367](https://github.com/sipeed/picoclaw/pull/3367) — Pilot MCP docs | ~1 day | Low | Open PR awaiting review |

**Key concern:** Issue #3281 (Web UI lag) has been open for 46 days with no fix PR yet, despite 2 upvotes. This is the highest-priority item for maintainer attention. Issue #3287 is marked `[stale]` and may need re-engagement.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-05

---

## 1. Today's Overview

NanoClaw activity is **moderately high**, with 18 PRs updated and 2 open issues in the last 24 hours, though no new releases were shipped. Development momentum centers on two fronts: finalizing provider-contract refactoring across Codex, OpenCode, and Cursor integrations, and hardening the skill-installation surface with operator-gated controls. Three PRs were merged/closed (CI workflow, chat SDK bridge fallback, raw-send flag), while 15 remain open for review. Two long-standing operational issues—unbounded conversation-file growth and operator env-var passthrough to session containers—remain unresolved and attract no maintainer engagement yet.

---

## 2. Releases

*No new releases today.*

---

## 3. Project Progress

**Merged / Closed PRs (3):**

| PR | Summary | Link |
|----|---------|------|
| #2403 | Replaced `bump-version` with an explicit Release workflow + concurrency guard; cleans up CI pipeline. | <https://github.com/nanocoai/nanoclaw/pull/2403> |
| #2232 | Falls back to URL fetch for chat-SDK adapters that lack `fetchData`, improving adapter compatibility. | <https://github.com/nanocoai/nanoclaw/pull/2232> |
| #2231 | Adds a `sendAsRaw` flag to bypass the adapter Markdown round-trip in the chat SDK bridge. | <https://github.com/nanocoai/nanoclaw/pull/2231> |

**Key Open PRs advancing today:**

- **#3584 / #3586 / #3588 / #3591 / #3722** — Provider-contract series (Codex, OpenCode, setup verifier, canonical instruction rendering). This is the project's core architectural push toward a unified, typed provider interface.
- **#3592** — Adds a `speed` inference property (fast/normal/slow) as a core-owned per-agent-group setting alongside `model` and `effort`.
- **#3355 / #3356** — Cursor Agent SDK payload and its `/add-cursor` install skill, completing Cursor as a first-class provider.
- **#3715** — New **Zapier MCP tool skill**, delivering a focused per-group skill without exposing private connection tokens in config.
- **#3720 / #3721** — Guarded source installation (`ncl skills list/plan/apply`) with operator policy enforcement; disables agent-bypassable install paths.
- **#3718 / #3719** — Agent-to-agent communication fixes: sender identity preservation and structured failure reporting back to the originating chat.
- **#3717** — Escapes embedded payloads in composed prompt blocks to prevent forged structure.
- **#3680** — Closes an allowlisted-extra mount bypass in `validateSpec` (container security hardening).

---

## 4. Community Hot Topics

| Topic | Type | Link | Comments | Reactions |
|-------|------|------|----------|-----------|
| PreCompact conversation archive writes unbounded full-rewrite files → production OOM crash loop | Issue #3716 | <https://github.com/nanocoai/nanoclaw/issues/3716> | 2 | 0 |
| Operator env overrides (auto-compact window, transcript rotation) never reach the session container | Issue #3714 | <https://github.com/nanocoai/nanoclaw/issues/3714> | 0 | 0 |

**Analysis:** Both issues are operational/deployment concerns, not feature requests. #3716 signals a **production reliability gap**—conversation history is rewritten entirely on each `PreCompact` fire with no rotation or size cap, directly causing OOM loops in memory-constrained container runs. #3714 is a follow-up to #1820 and highlights a **configuration passthrough gap** in the operator deployment model; env vars documented as "operator overrides" have no forwarding path into session containers. Neither issue has received maintainer comment or assignment yet, indicating a potential visibility problem for infra-layer bugs.

---

## 5. Bugs & Stability

**Reported today (ranked by severity):**

1. **[Critical] #3716 — PreCompact unbounded conversation-file growth causing OOM crash loops**
   Every `PreCompact` hook writes a new full-serialization of the entire conversation to disk with zero rotation or cap. Production deployments hit OOM and enter crash loops. *No fix PR opened yet.*

2. **[High] #3680 — Allowlisted-extra mount bypass in `validateSpec`** (PR open)
   Container mount validation allowed extra mounts outside the allowlist. Fix PR is already open and under review.

3. **[Medium] #3714 — Operator env overrides not forwarded to session containers**
   Env vars (`CLAUDE_CODE_AUTO_COMPACT_*`, transcript rotation) documented as operator controls have no forwarding path. Follow-up to #1820. *No fix PR yet.*

4. **[Medium] #3717 — Embedded payload escaping in composed prompt blocks** (PR open)
   Malicious or malformed payloads could forge block structure. Fix PR is open.

5. **[Low] Chat SDK adapter compatibility** (#2232 merged, #2231 merged)
   Previously reported; now resolved via fallback URL fetch and raw-send flag.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|--------|--------|------------|
| **Provider contract unification** (Codex, OpenCode, Cursor, Anthropic) | PRs #3584, #3586, #3588, #3591, #3722 | Near-term release. Core-facing typed contracts are being enforced; expect a "providers v2" release once all are merged. |
| **Structured skill installation CLI** (`ncl skills list/plan/apply`) | PR #3720 | High confidence for next release. Operator-gated source installation with guarded recovery is a standalone feature. |
| **Zapier MCP integration** | PR #3715 | Likely to land; it's a focused skill with no infrastructure changes. |
| **`speed` inference tier per agent group** | PR #3592 | Moderate confidence; crosses multiple subsystems (CLI, providers, config). |
| **Cursor Agent SDK as first-class provider** | PRs #3355, #3356 | High confidence; payload and skill are both open and near-complete. |
| **A2A (agent-to-agent) identity & failure feedback** | PRs #3718, #3719 | Moderate confidence; security-adjacent fixes that may see extra review. |

---

## 7. User Feedback Summary

- **Pain point — Disk/memory exhaustion in production:** The OOM crash loop from #3716 is the most pressing real-world complaint. Users running NanoClaw with `PreCompact` enabled are hitting unbounded disk growth with no cleanup, indicating the feature needs either a size cap, time-based rotation, or a streaming append mode.
- **Pain point — Operator configuration blind spots:** Env overrides documented as operator controls (#3714) silently fail to reach containers, forcing users to patch at runtime. This repeats a pattern seen in #1820 and erodes trust in the operator deployment model.
- **Satisfaction signal — Growing skill ecosystem:** The addition of Cursor, Zapier MCP, and a hardened install framework (#3720/#3721) shows the project is responding to demand for modular, operator-controlled capability delivery.
- **Satisfaction signal — Security hardening:** The mount-bypass fix (#3680) and prompt-injection escaping (#3717) address real attack surface concerns raised by deployment-sensitive users.

---

## 8. Backlog Watch

| Item | Open Since | Priority | Note |
|------|-----------|----------|------|
| **#1820** (referenced in #3714) | Unknown (parent issue) | High | Original report of container env-var override failures. Still the root cause for the unresolved #3714. |
| **#3714 — Operator env passthrough** | 2026-09-04 | High | No comments, no assigned PR. Directly blocks operator-mode correctness. |
| **#3716 — PreCompact OOM** | 2026-09-04 | Critical | No fix PR. Production-impacting; needs prioritization. |
| **#3584 / #3586 / #3588 / #3591** (provider contract series) | 2026-08-27 | Medium | Four PRs open since Aug 27 awaiting review/merge. Together they block the provider-unification milestone. |
| **#3592 — `speed` property** | 2026-08-28 | Low | Open since Aug 28; lower urgency relative to contract PRs. |

---

**Project Health Assessment:** Development is **healthy and active** with strong architectural progress on provider contracts and skill infrastructure. The main risk is **operational reliability** (#3716 OOM, #3714 env passthrough) — both are deployment-critical, have no assigned fixes, and have received no maintainer engagement. These should be the top priority for the next release cycle.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-09-05

## 1. Today's Overview

NullClaw saw minimal activity over the past 24 hours, with only **1 issue** updated and **no new pull requests** or releases. The project appears to be in a low-velocity maintenance phase, with no merged PRs or version bumps recorded. Community engagement remains quiet, as reflected by zero reactions and a single comment on the sole open issue. Overall project health is stable but lacks momentum.

## 2. Releases

No new releases were published today.

## 3. Project Progress

No pull requests were merged or closed today. No features were advanced or bugs fixed in the last 24 hours.

## 4. Community Hot Topics

- **[Issue #993](https://github.com/nullclaw/nullclaw/issues/993)** — *feat: make Firecrawl search endpoint configurable for self-hosted instances* (Updated 2026-09-04, 1 comment)
  - **Analysis:** This enhancement request highlights a real deployment pain point: users running self-hosted Firecrawl instances cannot leverage the built-in search provider because the API endpoint is hardcoded. While currently low-engagement (0 reactions), this reflects a broader need for **configurability of third-party service endpoints**, likely extending to other providers beyond Firecrawl. Maintainers should consider whether a generic endpoint-override mechanism would serve multiple use cases.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported today. No stability concerns flagged in the current data.

## 6. Feature Requests & Roadmap Signals

- **[Issue #993](https://github.com/nullclaw/nullclaw/issues/993)** — Configurable Firecrawl endpoint for self-hosted deployments. This is the only open issue and carries an **enhancement** label. It signals user demand for self-hosting flexibility within the agent's tooling stack. If adopted, a broader pattern of making provider URLs configurable (rather than per-provider ad-hoc fixes) would likely follow.

## 7. User Feedback Summary

The sole piece of user feedback today centers on **self-hosting limitations**. The requester wants to use their own Firecrawl instance instead of the default cloud endpoint, indicating that NullClaw's target audience includes privacy-conscious or cost-aware deployments where hardcoding external service URLs is a blocker. No satisfaction/dissatisfaction metrics are available beyond the single open issue.

## 8. Backlog Watch

- **[Issue #993](https://github.com/nullclaw/nullclaw/issues/993)** — Open since **2026-08-24** with no maintainer response beyond 1 community comment. At 12 days without a merge, triage, or even an acknowledgment, this issue is beginning to age out of the immediate backlog. It warrants maintainer attention to either confirm it as a valid enhancement or close with guidance.

---

**Summary:** NullClaw is in a quiet period with no releases, no PR activity, and only one aging enhancement issue. Project stability is unaffected, but the lack of maintainer engagement on Issue #993 is the one signal worth monitoring.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-05

## 1. Today's Overview

IronClaw shows active development today with **3 closed issues** and **3 merged PRs** resolved within the last 24 hours, alongside **9 open PRs** under review. The dominant theme is a coordinated effort to improve the Telegram integration experience — specifically pairing flows, error messaging, and command menu registration — suggesting the team is hardening the messaging-channel onboarding path ahead of broader adoption. No new releases were published today, indicating work is still in pre-release validation. The project's issue-to-PR resolution ratio (3 closed issues → 3 merged PRs) is healthy and signals efficient triage.

**Activity Level:** Moderate-High · **Contributor Mix:** Core team (ironclaw-ci[bot], henrypark133, italic-jinxin) + experienced external (thisisjoshford, jlwaugh)

---

## 2. Releases

*No new releases published today.*

---

## 3. Project Progress

### Merged / Closed PRs

| PR | Title | Author | Summary |
|----|-------|--------|---------|
| [#8073](https://github.com/nearai/ironclaw/pull/8073) | `fix(device-link): say "not configured by administrator" instead of blaming the user's account` | thisisjoshford | Replaces a generic "Something went wrong" error on Telegram personal-account linking with a clear message that the admin has not configured `telegram_api_id`/`telegram_api_hash`. Medium size, low risk. |
| [#8054](https://github.com/nearai/ironclaw/pull/8054) | `fix(assistant): check pairing before command admission so first contact gets the connect notice` | thisisjoshford | Fixes the root cause of #7956 — unpaired Telegram users now receive the pairing/connect notice on their very first `/start` message instead of the command inventory. Medium size, low risk. |
| [#8062](https://github.com/nearai/ironclaw/pull/8062) | `fix(llm): send conversation cache keys on OpenAI request paths` | henrypark133 | Derives a stable, domain-separated pseudonymous prompt-cache key per conversation at the gateway and sends it on every supported OpenAI Responses/Chat Completions request (OpenAI,-compatible providers). XL size, low risk. |

### Key Open PRs Advancing

- **#8072** — Registers the Telegram Bot API command menu (`/model`, `/status`, `/new`, `/stop`, `/interrupt`) at extension activation via `setMyCommands`, improving discoverability for first-time users.
- **#8067** — Introduces a boot/periodic sweep for stranded background subagent deliveries, closing a gap where durably-persisted results could be lost if a parent thread never restarts.
- **#8061** — Implements a concurrent-children cap for subagents (R2 debt) and verifies child-gate card replay behavior (R3 3b).
- **#8071 / #8070 / #8069 / #8068** — Four coordinated Web UI fixes by `italic-jinxin` covering command-result card dismissal, slash-command metadata alignment, active-command visibility during keyboard nav, and card-height preservation in the transcript.

---

## 4. Community Hot Topics

**Most Discussed / Linked Issues:**

- [#7956](https://github.com/nearai/ironclaw/issues/7956) — *Telegram unpaired /start shows command inventory instead of pairing notice* (Closed) — The canonical first-impression bug for new Telegram users. Resolved by #8054.
- [#7955](https://github.com/nearai/ironclaw/issues/7955) — *Telegram personal-account linking shows generic "Something went wrong" when admin hasn't configured API credentials* (Closed) — Poor error attribution confused users into thinking their account was at fault. Resolved by #8073.
- [#8074](https://github.com/nearai/ironclaw/issues/8074) — *Paired user in a not-connected shared channel gets pairing-notice copy instead of channel-not-connected copy* (Open) — Same error-messaging theme, still open; likely blocked on a follow-up PR.

**Underlying Need:** The community (or at least the active reporter `thisisjoshford`) is consistently flagging **onboarding friction in the Telegram channel** — first contact, pairing flows, and admin-configuration errors all produce confusing or misleading messages. The project is clearly investing in polishing this path, which is critical for a personal-AI-assistant product where the messaging channel is the primary user interface.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| **Medium** | [#8074](https://github.com/nearai/ironclaw/issues/8074) | Paired user in a not-connected shared channel receives incorrect error copy (pairing notice instead of channel-not-connected notice) | No linked fix PR yet — **needs attention** |
| **Low** | [#7956](https://github.com/nearai/ironclaw/issues/7956) | Unpaired user's first `/start` showed command inventory instead of pairing notice | ✅ Fixed in [#8054](https://github.com/nearai/ironclaw/pull/8054) (merged) |
| **Low** | [#7955](https://github.com/nearai/ironclaw/issues/7955) | Generic "Something went wrong" on Telegram personal-account linking when admin hasn't configured credentials | ✅ Fixed in [#8073](https://github.com/nearai/ironclaw/pull/8073) (merged) |
| **Medium** | [#8059](https://github.com/nearai/ironclaw/pull/8059) | `POST /api/v1/responses/{id}/cancel` returns 400 in all states; run continues despite cancel intent | Open PR — **unresolved** |

**Stability Assessment:** Bug velocity is low today with 2 of 3 reported issues resolved. The open cancellation bug (#8059) and the copy-mismatch bug (#8074) are the remaining items of note. No crashes or regressions reported.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Interpretation |
|--------|--------|----------------|
| Telegram command menu registration | [#8072](https://github.com/nearai/ironclaw/pull/8072) | Team is investing in native Bot API features for better UX — likely to ship soon |
| Subagent background-delivery sweep & concurrent-children cap | [#8067](https://github.com/nearai/ironclaw/pull/8067), [#8061](https://github.com/nearai/ironclaw/pull/8061) | R3/R4 subagent reliability work is progressing; expect these in the next minor release |
| Prompt-cache key propagation across OpenAI-compatible providers | [#8062](https://github.com/nearai/ironclaw/pull/8062) | Performance/cost optimization for long conversations — merge suggests this is production-ready |
| Web UI command-result card UX (dismiss, align, preserve height) | [#8071](https://github.com/nearai/ironclaw/pull/8071), [#8070](https://github.com/nearai/ironclaw/pull/8070), [#8069](https://github.com/nearai/ironclaw/pull/8069), [#8068](https://github.com/nearai/ironclaw/pull/8068) | Four coordinated PRs indicate a deliberate UI polish sprint — likely bundled in next release |

**Prediction:** The next release will prominently feature the Telegram onboarding fixes, the Web UI command-menu improvements, and the subagent reliability patches. The prompt-cache PR is a quieter but impactful backend improvement.

---

## 7. User Feedback Summary

**Pain Points Expressed:**
- First-time Telegram users are met with a command inventory instead of a pairing instructions — this creates confusion and may cause drop-off before the user ever connects their account. *(#7956, now fixed)*
- Error messages blame the user's account when the real cause is missing admin configuration — this generates support tickets and erodes trust. *(#7955, now fixed)*
- The same misattribution pattern persists for paired users in unconnected shared channels. *(#8074, open)*
- Canceling an in-progress LLM response is non-functional — users cannot stop a runaway generation. *(#8059, open)*

**Satisfaction Indicators:**
- The reporter (`thisisjoshford`) is highly engaged and methodical, filing paired issues with clear reproduction steps and seeing them resolved quickly — a healthy maintainer-response dynamic.
- Multiple coordinated Web UI improvements from `italic-jinxin` suggest the team is proactively refining the experience rather than reactively patching.

---

## 8. Backlog Watch

| Item | Author | Age | Risk |
|------|--------|-----|------|
| [#8074](https://github.com/nearai/ironclaw/issues/8074) — Paired user gets wrong error copy in not-connected shared channel | thisisjoshford | 1 day | Low-Medium (UX inconsistency, same pattern as recently-fixed #7956) |
| [#8059](https://github.com/nearai/ironclaw/pull/8059) — Cancel endpoint returns 400 in all states | jlwaugh | 2 days | Medium (functional bug: users cannot cancel running responses) |

**Maintainer Attention Needed:** #8059 is the higher-priority backlog item — a non-functional cancel API is a correctness issue that affects all users of the OpenAI-compatible Responses endpoint. #8074 is a lower-risk copy mismatch that should be resolved with a small follow-up PR consistent with the #8054/#8073 pattern.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-05

---

## 1. Today's Overview

LobsterAI is in a highly active release cadence, with two versions shipped in the past 48 hours (2026.9.3 and 2026.9.4), indicating a rapid iteration cycle. The project saw 33 PRs updated in the last 24 hours—28 merged/closed—reflecting strong contributor momentum, particularly around browser UX, cowork collaboration, and publishing/subscription flows. Only one open issue remains, and it is stale, suggesting the backlog is being aggressively cleared. Overall project health is strong, with balanced activity across feature development, bug fixes, and platform-specific hardening.

---

## 2. Releases

### LobsterAI 2026.9.4 (2026-09-04)
**What's Changed:**
- **feat(browser):** Restore interactive in-app browser — a follow-up enabling more polished browser interactions ([PR #2602](https://github.com/netease-youdao/LobsterAI/pull/2602))
- **feat(update):** Confirm before install and quitting the app — prevents accidental data loss or interrupted sessions ([PR #2609](https://github.com/netease-youdao/LobsterAI/pull/2609))
- **feat(publishing):** Subscription recovery guidance and resource status sync ([PR #2613](https://github.com/netease-youdao/LobsterAI/pull/2613))

**Breaking Changes / Migration Notes:** None reported. The update confirmation flow may surface a new dialog for existing users but is backward-compatible.

### LobsterAI 2026.9.3 (2026-09-03)
**What's Changed:**
- **feat(cowork):** Show login prompt before unauthenticated chat — gates anonymous conversation attempts behind auth ([PR #2573](https://github.com/netease-youdao/LobsterAI/pull/2573))
- **feat(browser):** Add interactive in-app browser — initial launch of the in-app browser feature ([PR #2574](https://github.com/netease-youdao/LobsterAI/pull/2574))
- **feat(onboarding):** Various onboarding improvements

**Breaking Changes / Migration Notes:** None reported. Unauthenticated users will now see a login modal instead of proceeding to a blank chat, which is a behavioral change but not a technical breaking change.

---

## 3. Project Progress

**Key merged/closed PRs today:**

| PR | Area | Summary |
|----|------|---------|
| [#2618](https://github.com/netease-youdao/LobsterAI/pull/2618) | Release | Release/2026.9.4 pipeline |
| [#2616](https://github.com/netease-youdao/LobsterAI/pull/2616) | CI/Build | Bound skill audit duration to 90s, disabling implicit lockfile-only audit |
| [#2615](https://github.com/netease-youdao/LobsterAI/pull/2615) | Browser/Windows | Support Unicode Windows install paths for the browser MCP launcher |
| [#2614](https://github.com/netease-youdao/LobsterAI/pull/2614) | Config | Fixed test-mode server API address back to standard intranet |
| [#2613](https://github.com/netease-youdao/LobsterAI/pull/2613) | Publishing | Subscription recovery guidance and resource sync |
| [#2612](https://github.com/netease-youdao/LobsterAI/pull/2612) | Cowork | Preserve model display during login refresh |
| [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | Browser | Improve in-app login feedback and tab controls (open) |
| [#2603](https://github.com/netease-youdao/LobsterAI/pull/2603) | i18n | Refined Chinese voice quota exhausted messaging |
| [#2599](https://github.com/netease-youdao/LobsterAI/pull/2599) | IM | Improved bot card layout with responsive two-column grid |
| [#2503](https://github.com/netease-youdao/LobsterAI/pull/2503) | Electron | Added edit context menu (Cut/Copy/Paste/Select All) for text inputs |
| [#2501](https://github.com/netease-youdao/LobsterAI/pull/2501) | Skills | Fixed portal upgrade progress overlay rendering |
| [#2521](https://github.com/netease-youdao/LobsterAI/pull/2521) | Cowork | Preserve message selection for context menu |
| [#2520](https://github.com/netease-youdao/LobsterAI/pull/2520) | Plugins | Keep install modal usable with long error messages |

**Trends:** Heavy investment in browser UX, cowork collaboration polish, and publishing/subscription reliability. Platform stability (Windows Unicode paths, CI audits) is also a clear focus.

---

## 4. Community Hot Topics

### Most Discussed Open Issue
- **[Issue #1071](https://github.com/netease-youdao/LobsterAI/issues/1071)** — *SQLite 存储层三个数据完整性/可靠性缺陷* (stale, 0 reactions, 1 comment)
  - **Three interrelated SQLite storage-layer defects:** CASCADE delete failure causing orphaned message accumulation, non-atomic `save()` writes risking corruption on crash, and `storeInitPromise` timeout causing permanent failure state.
  - **Underlying need:** Users are auditing data persistence reliability under production conditions. The issue was created in March but updated as recently as September 4, indicating persistent concern without resolution. This is a **high-severity reliability gap** that deserves maintainer attention.

No other open issues are currently tracked, making #1071 the sole community-reported item.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| 🔴 High | [#1071](https://github.com/netease-youdao/LobsterAI/issues/1071) | SQLite CASCADE失效/孤儿消息/非原子写/永久故障 | ❌ No fix PR yet — stale since March |
| 🟡 Medium | [#2615](https://github.com/netease-youdao/LobsterAI/pull/2615) | Unicode Windows install paths breaking browser MCP launcher | ✅ Merged |
| 🟡 Medium | [#2520](https://github.com/netease-youdao/LobsterAI/pull/2520) | Plugin install modal unusable with long errors | ✅ Merged |
| 🟢 Low | [#2501](https://github.com/netease-youdao/LobsterAI/pull/2501) | Skill upgrade overlay not covering full app shell | ✅ Merged |
| 🟢 Low | [#2614](https://github.com/netease-youdao/LobsterAI/pull/2614) | Test-mode API address pointing to wrong environment | ✅ Merged |

**Note:** No new crash reports or regressions were opened today. The SQLite issue (#1071) remains the most critical outstanding stability concern.

---

## 6. Feature Requests & Roadmap Signals

- **Subscription recovery & publishing workflows** ([PR #2613](https://github.com/netease-youdao/LobsterAI/pull/2613)) — Expanded tracking of recovery entry points, analytics, and status sync suggests the team is investing in monetization and retention infrastructure.
- **In-app browser** ([PR #2574](https://github.com/netease-youdao/LobsterAI/pull/2574), [PR #2602](https://github.com/netease-youdao/LobsterAI/pull/2602), [PR #2617](https://github.com/netease-youdao/LobsterAI/pull/2617)) — Rapid iteration across three PRs in two days signals this is a high-priority feature area. Expect continued browser enhancements (tab management, credential handling) in upcoming releases.
- **Login-gated cowork chat** ([PR #2573](https://github.com/netease-youdao/LobsterAI/pull/2573)) — Pushing authenticated-only workflows points to a roadmap direction around user identity and personalized experience.
- **Edit context menu for text inputs** ([PR #2503](https://github.com/netease-youdao/LobsterAI/pull/2503)) — Quality-of-life improvement for power users; suggests ongoing desktop-native polish efforts.

**Predicted next-release focus:** Browser tab UX refinements, deeper subscription/recovery analytics, and SQLite storage hardening (if #1071 is addressed).

---

## 7. User Feedback Summary

- **Pain points addressed:** Plugin install failures hiding action buttons (fixed in #2520), skill upgrade overlays rendering incorrectly (fixed in #2501), and unauthenticated users hitting dead-end chats (fixed in #2573).
- **Positive signals:** Responsive iteration on the in-app browser — three PRs in two days show the team is listening to user feedback on browser functionality. The update confirmation dialog (#2609) directly addresses accidental-quit/frustration concerns.
- **Dissatisfaction risk:** The stale SQLite issue (#1071) — reported for ~5 months with no fix — risks eroding trust among users who rely on local data persistence, especially as the app handles more conversation history.

---

## 8. Backlog Watch

| Issue / PR | Age | Priority | Status |
|-----------|-----|----------|--------|
| [#1071](https://github.com/netease-youdao/LobsterAI/issues/1071) — SQLite 存储层缺陷 | ~5 months | 🔴 Critical | Stale, no fix PR, 0 reactions |

**Recommendation:** This is the single most important item requiring maintainer attention. The three reported defects (CASCADE failure, non-atomic writes, permanent failure state) can cause silent data loss in production. A fix PR or at minimum a maintainer acknowledgment would significantly improve project credibility.

---

*Digest generated from GitHub data sourced via LobsterAI on 2026-09-05.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-05

## 1. Today's Overview

The Moltis project shows light but active development today, with one open issue and one open pull request updated in the last 24 hours. No new releases were published, and no PRs were merged or issues closed, suggesting the team is in a steady review cycle rather than a sprint finish. The focus remains on external agent integrations and UX customization, reflecting ongoing maturation of the platform's interoperability and configurability. Overall project health is stable with incremental progress.

## 2. Releases

No new releases today.

## 3. Project Progress

- **PR #1258** ([feat(external-agents): add direct AGY streaming](https://github.com/moltis-org/moltis/pull/1258)) — An open PR authored by GTanger that introduces a first-class streaming transport for the official `agy` CLI. It reuses AGY's existing Google OAuth session (eliminating the need for Gemini CLI or a separate API key) and translates AGY's versioned `stream-json` output into Moltis-native message types (text, reasoning, notice, tool, sub-agent, usage, and resumable-session). This represents meaningful advancement in the external-agent integration surface, though it has not yet been merged.

## 4. Community Hot Topics

- **Issue #1259** ([Configurable default reasoning/thinking level](https://github.com/moltis-org/moltis/issues/1259)) — A new enhancement request by Scentedtiger asking for a persistent, configurable default for the reasoning/thinking level across sessions. While it currently has zero comments and zero reactions, the very existence of this request signals that users are deepening their engagement with Moltis's reasoning controls and want them to stick across sessions rather than being reset each time. This is a quality-of-life feature that, if implemented, would reduce friction for power users.

## 5. Bugs & Stability

No bug reports, crashes, or regressions were filed today. The project appears stable from a defect-reporting perspective.

## 6. Feature Requests & Roadmap Signals

- **Issue #1259** requests persistent reasoning-level configuration. This aligns with a broader trend of users seeking granular, session-persistent control over agent behavior. If the maintainers prioritize configuration ergonomics, this feature is a strong candidate for inclusion in an upcoming minor release, particularly alongside the external-agent work in PR #1258.

## 7. User Feedback Summary

The day's activity is dominated by a single enhancement request and one integration PR, with no overt user dissatisfaction or pain-point complaints surfaced. The reasoning-level configurability request suggests users are moving past initial onboarding and are now optimizing their workflows — a sign of a growing, advanced user base. The AGY streaming PR indicates contributor-driven momentum around broader agent interoperability, which users benefit from indirectly through expanded tooling options.

## 8. Backlog Watch

- **PR #1258** ([add direct AGY streaming](https://github.com/moltis-org/moltis/pull/1258)) — Created on 2026-09-04 and still open with no visible merge activity. As a non-trivial feature adding a new streaming transport, this PR warrants timely maintainer review. Delaying merge risks contributor fatigue and slows the external-agent roadmap.
- **Issue #1259** ([configurable default reasoning level](https://github.com/moltis-org/moltis/issues/1259)) — Freshly opened with no maintainer response yet. While new, a prompt acknowledgment would help signal community engagement and guide the contributor on next steps.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-05

---

## 1. Today's Overview

CoPaw (agentscope-ai/QwenPaw) shows **high activity** with 49 issues and PRs updated in the last 24 hours (23 issues, 26 PRs). Of the 23 issues, 15 remain open and 8 were closed; of the 26 PRs, 20 are still open and 6 were merged/closed. No new releases were published. The project is in an active development cycle around the **2.2.x** series, with strong community engagement on multi-tenancy (QwenPaw Hub), desktop UX improvements, and runtime stability fixes.

---

## 2. Releases

**No new releases** in the past 24 hours. The latest tracked versions in issues are **2.2.0-beta.7** and **2.2.1b1**, suggesting the team is still iterating on beta releases ahead of a 2.2.0 stable push.

---

## 3. Project Progress

**Merged / Closed today:**

| Item | Type | Summary |
|------|------|---------|
| [PR #7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | Feature | Workspace-scoped skill preload configuration — closes issue #7182 |
| [PR #7504](https://github.com/agentscope-ai/QwenPaw/pull/7504) | Bugfix | Enforce per-tool MCP whitelist on the agent runtime path — closes issue #7470 |
| [PR #7560](https://github.com/agentscope-ai/QwenPaw/pull/7560) | Bugfix | Preserve selected loop mode query in console — closes issues #7552, #7555 |
| [Issue #6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Bug | Multi-step task execution stops without prompt after planning — closed |
| [Issue #7510](https://github.com/agentscope-ai/QwenPaw/issues/7510) | Bug | `/memory/status` returns 500 on v2.2.0-beta.7 Desktop — closed |
| [Issue #7552](https://github.com/agentscope-ai/QwenPaw/issues/7552) | Bug | Loop mode selection not reaching backend — closed |
| [Issue #7555](https://github.com/agentscope-ai/QwenPaw/issues/7555) | Bug | Loop mode UI resets to "Default" on page switch — closed |
| [Issue #7023](https://github.com/agentscope-ai/QwenPaw/issues/7023) | Bug | Desktop startup blocks ~60s on Playwright Chromium install — closed |

**Key advances:**
- **MCP governance** is being tightened: per-tool whitelist enforcement (#7504) directly addresses a security gap where disabled tools were still callable.
- **Loop mode persistence** across tab switches and backend communication is fixed, resolving two related UI/state bugs.
- **Skill preloading** (#7183) allows workspace-scoped optimization, reducing first-turn latency for frequently-used skills.

---

## 4. Community Hot Topics

| Issue | Title | Comments | Engagement |
|-------|-------|----------|------------|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | QwenPaw Hub multi-tenant edition — roadmap discussion | 22 | 👍 3 |
| [#7505](https://github.com/agentscope-ai/QwenPaw/issues/7505) | LAN LLM server frequent disconnects causing timeout failures | 12 | 👍 0 |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Multi-step tasks stop silently after planning | 12 | 👍 0 |

**Analysis:**
- **QwenPaw Hub (#7318)** is the top discussion — the community is actively shaping the multi-tenant product direction. This signals strong demand for team/organizational deployment beyond the personal assistant use case.
- **LAN LLM connectivity (#7505)** reflects a real-world deployment pattern: users running local LLM servers (LM Studio) on their network. The disconnect/retry storm suggests a client-side connection management issue worth prioritizing.
- **Silent task stops (#6921)** indicates a UX gap in multi-step agent workflows where the model plans but doesn't execute, leaving users confused.

---

## 5. Bugs & Stability

**Reported today (ranked by severity):**

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| 🔴 Critical | [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) | 409 error when submitting messages during active task execution; queue not handling concurrent input | — |
| 🔴 Critical | [#7534](https://github.com/agentscope-ai/QwenPaw/issues/7534) | Feishu session queue consumer hangs permanently; session silently unresponsive, new messages can't spawn consumer | — |
| 🟠 High | [#7549](https://github.com/agentscope-ai/QwenPaw/issues/7549) | Volcengine Ark API rejects requests ending with assistant text turn (400 "MissingParameter: partial") | — |
| 🟠 High | [#7567](https://github.com/agentscope-ai/QwenPaw/issues/7567) | Task stop button shows stopped but execution continues in background | — |
| 🟡 Medium | [#7554](https://github.com/agentscope-ai/QwenPaw/issues/7554) | Shell tool child processes inherit console stdin on Windows; Ctrl+C ineffective | — |
| 🟡 Medium | [#7548](https://github.com/agentscope-ai/QwenPaw/issues/7548) | Navigation history lost after conversation switch or restart | — |
| 🟡 Medium | [#7550](https://github.com/agentscope-ai/QwenPaw/issues/7550) | Docker镜像更新后codex cli等第三方agent配置丢失 | — |
| 🟢 Low | [#7541](https://github.com/agentscope-ai/QwenPaw/issues/7541) | Architectural concern: sessions separated/blocked by channel (web, desktop, Telegram) | — |

**Closed today:** #6921 (silent task stop), #7510 (memory/status 500), #7023 (Playwright startup block), #7552/#7555 (loop mode bugs).

**Notable:** The **Feishu consumer hang (#7534)** is a serious reliability issue for Chinese enterprise users — a single stuck consumer permanently breaks a session with no recovery path. The **409 concurrent-message bug (#7559)** suggests the message queue architecture needs review under concurrent input scenarios.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Feature | Likelihood for 2.2.x |
|-------|---------|---------------------|
| [#7568](https://github.com/agentscope-ai/QwenPaw/issues/7568) | Off-peak task scheduling (batch API / discount-hour execution) | Medium — cost optimization is compelling but non-trivial |
| [#7558](https://github.com/agentscope-ai/QwenPaw/issues/7558) | Pluggable relational storage backend (PostgreSQL/MySQL) for WAL-sensitive deployments | High — directly enables K8s/Docker Swarm HA; already has community interest |
| [#7557](https://github.com/agentscope-ai/QwenPaw/issues/7557) | Skill versioning and dependency metadata | Medium — important for fleet management |
| [#7556](https://github.com/agentscope-ai/QwenPaw/issues/7556) | MCP driver fallback chain when policy denies | Medium — operational resilience improvement |
| [#7553](https://github.com/agentscope-ai/QwenPaw/issues/7553) | Artifacts displayed above timestamps rather than collapsed in steps | Low-Medium — UX polish |
| [#7550](https://github.com/agentscope-ai/QwenPaw/issues/7550) | Pre-install codex cli and preserve config in Docker images | Low — niche but practical |
| [#7378](https://github.com/agentscope-ai/QwenPaw/pull/7378) | Native mobile app (Expo/React Native) | High — in progress, draft PR exists |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | PawPort: import from Codex/Qoder | Medium — portability feature |

**Strongest signals:** Multi-tenant Hub (#7318), mobile app (#7378), and PostgreSQL storage (#7558) appear to be the most impactful upcoming features. The **off-peak scheduling (#7568)** is a novel cost-reduction feature that could differentiate QwenPaw.

---

## 7. User Feedback Summary

**Pain points:**
- **Concurrent input handling** (#7559): Users expect queued messages during task execution, not 409 errors. The current architecture treats concurrent submissions as conflicts.
- **Task stop reliability** (#7567): The UI shows a stopped state but the backend continues executing — a trust-breaking bug for long-running tasks.
- **Local LLM connectivity** (#7505): LAN-based LLM servers (LM Studio) suffer from disconnect storms, suggesting the HTTP client needs better connection pooling and retry logic.
- **Navigation history persistence** (#7548): Switching conversations or restarting loses early message history from the UI navigation panel, though data exists in `history.db`.
- **Channel-based session isolation** (#7541): Users report that sessions are incorrectly partitioned by channel (web vs. desktop vs. Telegram), causing fragmented conversation state.
- **Startup performance** (#7367, #7023): Even with only the console channel enabled, startup takes 30-45s due to unconditional import of all 18 channel modules (Lark SDK alone is ~18.5s). Desktop startup also blocks on Playwright Chromium install.

**Satisfaction signals:**
- The community is actively engaging with roadmap discussions (#7318 has 22 comments, 3 upvotes), indicating strong product-market fit for the personal AI assistant space.
- Rapid closure of bugs (#6921, #7510, #7552/#7555) shows responsive maintenance.
- The skill preload feature (#7183) and MCP whitelist fix (#7504) demonstrate the team is acting on community feedback.

---

## 8. Backlog Watch

| Issue/PR | Age | Why It Needs Attention |
|----------|-----|----------------------|
| [#7534](https://github.com/agentscope-ai/QwenPaw/issues/7534) — Feishu consumer hang | Open 2 days, 3 comments | No fix PR yet. Critical for enterprise WeChat/Feishu users. |
| [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) — 409 on concurrent messages | Open <1 day, 4 comments | No fix PR. Affects all users running multi-step tasks while sending new input. |
| [#7549](https://github.com/agentscope-ai/QwenPaw/issues/7549) — Volcengine Ark 400 error | Open <1 day, 2 comments | No fix PR. Blocks users of Volcengine's LLM API. |
| [#7567](https://github.com/agentscope-ai/QwenPaw/issues/7567) — Stop button ineffective | Open <1 day, 1 comment | No fix PR. Undermines trust in task management. |
| [#7554](https://github.com/agentscope-ai/QwenPaw/issues/7554) — Windows stdin inheritance | Open <1 day, 1 comment | No fix PR. Affects Windows console users running shell tools. |
| [#7568](https://github.com/agentscope-ai/QwenPaw/issues/7568) — Off-peak scheduling | Open <1 day, 1 comment | Novel feature request; needs architecture review before implementation. |
| [#7558](https://github.com/agentscope-ai/QwenPaw/issues/7558) — Relational storage backend | Open <1 day, 1 comment | Important for production deployments but requires significant backend work. |
| [#7378](https://github.com/agentscope-ai/QwenPaw/pull/7378) — Mobile app (DRAFT) | Open 8 days | Marked "DO NOT MERGE"; draft state needs review to assess readiness. |
| [#7541](https://github.com/agentscope-ai/QwenPaw/issues/7541) — Channel-based session isolation | Open 2 days, 3 comments | Architectural concern raised by Russian-speaking user; may require design discussion. |

---

*Generated by Agnes-2.0-Flash · Data source: agentscope-ai/QwenPaw GitHub (2026-09-04 → 2026-09-05)*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-05

## 1. Today's Overview

ZeroClaw is exhibiting high development velocity on 2026-09-05, with **34 issues** and **50 pull requests** updated in the last 24 hours. The project is in an active stabilization window for v0.8.5 (tracker #9459), with no new releases shipped yet. Activity is heavily concentrated around security hardening, gateway reliability, and ZeroCode TUI improvements. The open-to-closed issue ratio (24 open / 10 closed) and a strong PR volume suggest healthy maintainer engagement, though several high-severity bugs remain open without merged fixes.

## 2. Releases

**No new releases published.** PR #10632 (JordanTheJet) bumped the coordinated 23-crate workspace and all generated surfaces from **v0.8.4 → v0.8.5**, pinning the final signed translation snapshot. However, the release itself has not yet been tagged/published. The v0.8.5 stabilization line is tracked in issue #9459, with intake frozen since August 4 and a target window through August 30 (now extended).

## 3. Project Progress

**Closed / Merged today:**
- **#10153** — WhatsApp Web ported to `whatsapp-rust` 0.7.0, replacing six git-pinned deps with crates.io releases, enabling `zeroclaw-channels` publication.
- **#9109** — Native Hailo-Ollama provider support added (blocked, awaiting review).
- **#9529** — ZeroCode TodoWrite tracker gained a visible close control.
- **#10571** — Twitch section added to the Social Channels guide.
- **#10357** — Tool execution error path fix: detailed error bodies now surface to agents instead of bare status codes.
- **#10223** — ZeroCode Ctrl+C blocking during reconnect resolved.

**Notable open progress:**
- **#10407** — Persistent session prompt attachments (SQLite-backed, up to 4 per session) with explicit single-use approval.
- **#9002** — Gateway now keeps agent turns alive after viewer disconnect.
- **#10632** — v0.8.5 version bump ready for release.

## 4. Community Hot Topics

| Issue / PR | Comments | Focus |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — RFC: Runtime-owned conversation sessions & transport adapters | 32 | Architecture overhaul of session lifecycle |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) — RFC: Computer-use desktop screen interaction | 16 | Desktop automation via screen/input control |
| [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) — RFC: WhatsApp `allowed_groups` empty = permit-none | 14 | Security fix for WhatsApp channel defaults |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) — RFC: Verbatim channel send via gateway | 13 | Gateway route for direct message delivery |
| [#8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720) — Disable cachePoint for Bedrock Nova 2 Lite | 10 | Configurable model caching |
| [#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) — Classify incomplete terminal responses | — | Fix for Anthropic provider response handling |

**Analysis:** The community is heavily focused on **session/transport architecture** (#9487) and **desktop computer-use capabilities** (#6909), signaling that ZeroClaw is maturing beyond messaging channels into general-purpose agent orchestration. The WhatsApp security RFC (#9397) reflects operator demand for stricter default-deny policies. The verbatim send RFC (#10050) addresses a real gap in gateway API surface.

## 5. Bugs & Stability

### P1 / High Severity (Open, unmerged)

| Issue | Component | Severity | Fix PR? |
|---|---|---|---|
| [#10603](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) — OpenCode missing `x-opencode-session` header | provider | S1 — workflow blocked | No |
| [#10609](https://github.com/zeroclaw-labs/zeroclaw/issues/10609) — ZeroCode ignores launch directory, forces agent workspace as cwd | zerocode/tui | S1 — workflow blocked | No |
| [#9882](https://github.com/zeroclaw-labs/zeroclaw/issues/9882) — Image markers bypass content validation on `run_model_query` | runtime/agent | S1 — security | No |
| [#9421](https://github.com/zeroclaw-labs/zeroclaw/issues/9421) — Incomplete terminal responses reported as successful | runtime/daemon | S1 — workflow blocked | [#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) (open) |
| [#10593](https://github.com/zeroclaw-labs/zeroclaw/issues/10593) — `backup.schedule_cron` silently schedules nothing | runtime/daemon | S1 — workflow blocked | No |

### P2 / Medium Severity (Open)

| Issue | Component | Severity |
|---|---|---|
| [#10594](https://github.com/zeroclaw-labs/zeroclaw/issues/10594) — cron records nothing on silent non-execution | runtime/daemon | S2 — degraded |
| [#10625](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) — `[media attachment]` placeholder leaked to text-only model users | channel | S2 — degraded |
| [#10626](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) — TTS synthesizes Markdown/emoji verbatim | provider | S2 — degraded |
| [#10585](https://github.com/zeroclaw-labs/zeroclaw/issues/10585) — log sink regression races migration tests | tooling/ci | S3 — minor |
| [#10390](https://github.com/zeroclaw-labs/zeroclaw/issues/10390) — Inactive Chat pane blocks ZeroCode navigation | zerocode/tui | S2 — degraded |

**Notable closed today:**
- [#10357](https://github.com/zeroclaw-labs/zeroclaw/issues/10357) — Tool error bodies now preserved (#10357 closed).
- [#10223](https://github.com/zeroclaw-labs/zeroclaw/issues/10223) — ZeroCode Ctrl+C blocking fixed.

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Summary | Likely in v0.8.5? |
|---|---|---|
| [#10407](https://github.com/zeroclaw-labs/zeroclaw/pull/10407) — Persistent session prompt attachments | SQLite-backed per-session prompt storage | Possible (XL size, in-progress) |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) — Verbatim channel send via gateway | Direct message relay without agent turn | Unlikely (RFC, not yet accepted) |
| [#10619](https://github.com/zeroclaw-labs/zeroclaw/issues/10619) — Anthropic prompt-cache passthrough for OpenAI-compatible providers | `cache_control` support through translating gateways | Unlikely (P1 feature, new) |
| [#10588](https://github.com/zeroclaw-labs/zeroclaw/issues/10588) — Raise `multimodal.max_image_size_mb` to 20 | Document ceiling and raise default from 5→20 | Possible (small, in-progress) |
| [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) — Native Hailo-Ollama provider | Hailo-Ollama 0.5.1 support | Blocked on review |
| [#9739](https://github.com/zeroclaw-labs/zeroclaw/pull/9739) — Multi-session panes with agent sidebar | ZeroCode UX enhancement | Possible (XL, in-progress) |

**Roadmap signal:** The project is clearly investing in **session permanence** (#10407), **gateway extensibility** (#10050), and **cross-provider cache compatibility** (#10619). Desktop computer-use (#6909 RFC) is a major long-term direction.

## 7. User Feedback Summary

**Pain points expressed:**
- **WhatsApp security defaults** are dangerously permissive — an empty `allowed_groups` permits all groups, and `mode=business` ignores personal-mode chat policies (#9348, #9397). Operators report this as a critical trust gap.
- **ZeroCode TUI** ignores launch directory and starts sessions in the agent workspace instead (#10609), and blocks keyboard input during reconnect (#10223, now fixed).
- **OpenCode relay** requests missing `x-opencode-session` header risk account flags for Go models (#10603).
- **TTS** reads Markdown and emoji names aloud, degrading voice UX (#10626).
- **Text-only model users** see raw `[media attachment]` placeholders in conversation history (#10625).
- **Bedrock Nova 2 Lite** caching errors are not configurable (#8720).

**Satisfaction signals:**
- WhatsApp port to crates.io deps (#10153) removes a maintenance burden.
- Tool error body preservation (#10357) improves agent debugging.
- Multi-session ZeroCode pane (#9739) addresses power-user workflow needs.

## 8. Backlog Watch

| Issue / PR | Age | Concern |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — RFC: Runtime-owned sessions & transport adapters | Open since 2026-07-28 | 32 comments, Rev 5 proposed; critical architecture decision pending |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) — RFC: Desktop computer-use support | Open since 2026-05-25 | 16 comments, Rev 2 accepted; long-running RFC needing implementation |
| [#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) — Classify incomplete terminal responses | Open since 2026-07-27 | Fix for P1 bug #9421; XL size, needs author action |
| [#9002](https://github.com/zeroclaw-labs/zeroclaw/pull/9002) — Keep agent turns alive after viewer disconnect | Open since 2026-07-11 | 3+ months open; high-risk XL fix, needs author action |
| [#9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419) — Rotate live credentials after rate limits | Open since 2026-07-26 | Blocked; security-relevant credential rotation |
| [#10241](https://github.com/zeroclaw-labs/zeroclaw/pull/10241) — Restore supervised shell approval routing | Open since 2026-08-22 | Blocked; security policy fix |
| [#10603](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) — OpenCode missing session header | Open since 2026-09-03 | P1, workflow-blocked, no fix PR yet |
| [#10609](https://github.com/zeroclaw-labs/zeroclaw/issues/10609) — ZeroCode cwd bug | Open since 2026-09-04 | P1, workflow-blocked, no fix PR yet |
| [#9882](https://github.com/zeroclaw-labs/zeroclaw/issues/9882) — Image markers bypass validation | Open since 2026-08-10 | P1 security, no fix PR yet |

**Maintainer attention needed:** Several P1 bugs (#10603, #10609, #9882, #10593) lack associated fix PRs. The v0.8.5 stabilization tracker (#9459) has no new items since 2026-09-04, suggesting the team may be focused on release preparation rather than new intake.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*