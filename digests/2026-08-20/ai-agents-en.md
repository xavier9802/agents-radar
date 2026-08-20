# OpenClaw Ecosystem Digest 2026-08-20

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-20 01:38 UTC

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



# OpenClaw Project Digest — 2026-08-20

## 1. Today's Overview

OpenClaw is experiencing very high issue and PR volume today, with **500 issues** and **500 PRs** updated in the last 24 hours. The project shows robust community momentum: **38 issues closed** and **81 PRs merged/closed** in the same window. No new releases were published today. The backlog remains substantial with **462 open/active issues**, and several P0/P1 bugs affecting data integrity and gateway stability are drawing sustained attention.

## 2. Releases

**None today.** The latest tracked release validation effort is for **v2026.8.1-beta.2** ([Issue #125626](https://github.com/openclaw/openclaw/issues/125626)), currently in active community testing.

## 3. Project Progress

**Merged/Closed PRs today:**

- **[#126434](https://github.com/openclaw/openclaw/pull/126434)** — *refactor(llama-cpp): consolidate managed and existing server paths into one provider* (Closed)
- **[#126498](https://github.com/openclaw/openclaw/pull/126498)** — *fix(llama-cpp): make endpoint auth transitions reproducible* (Closed)
- **[#125740](https://github.com/openclaw/openclaw/pull/125740)** — *fix(skills): preserve routing descriptions on workshop updates* (Closed, addresses [#125570](https://github.com/openclaw/openclaw/issues/125570))
- **[#116489](https://github.com/openclaw/openclaw/pull/116489)** — *feat(security): require acknowledgement for install policy warnings* (Closed)
- **[#120900](https://github.com/openclaw/openclaw/pull/120900)** — *feat(ui): review install policy warnings in Control UI* (Closed)

**Notable in-progress work awaiting review:**

- [#126424](https://github.com/openclaw/openclaw/pull/126424) — Fix conversation delivery scoping to agent bindings (P1)
- [#126501](https://github.com/openclaw/openclaw/pull/126501) — Let `/v1/responses` callers set delivery targets for subagent results
- [#126486](https://github.com/openclaw/openclaw/pull/126486) — Restore MEMORY.md when in-place fallback write fails mid-way
- [#126504](https://github.com/openclaw/openclaw/pull/126504) — Honor configured system agent for ambient owner resolution (multi-agent fix)

## 4. Community Hot Topics

| Issue | Comments | Severity | Link |
|-------|----------|----------|------|
| Subagent completion silently lost — no retry/notification | 26 | 🦞 P0 Diamond Lobster | [#44925](https://github.com/openclaw/openclaw/issues/44925) |
| Track live dev agent behavior and trajectory | 22 | 🦪 P2 | [#77598](https://github.com/openclaw/openclaw/issues/77598) |
| "Cannot convert undefined or null to object" regression with Gemini | 14 | 🐚 P1 | [#38327](https://github.com/openclaw/openclaw/issues/38327) |
| Gateway fails to start after update to 2026.7.1 | 14 | 🦞 P0 | [#108435](https://github.com/openclaw/openclaw/issues/108435) |
| Write tool lacks append mode — cron sessions destroy shared files | 14 | 🦞 P1 | [#40001](https://github.com/openclaw/openclaw/issues/40001) |

**Underlying needs:** The top-voted issues consistently center on **data loss prevention** (silent subagent result loss, file overwrites, incomplete model turns) and **session/state reliability** (startup failures, regressions after updates). The community is clearly prioritizing production-grade stability over new features at this stage.

## 5. Bugs & Stability

### 🔴 P0 — Critical / Release-Blocking

| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent completion silently lost — no retry, no auto-restart on timeout | None yet |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | Gateway fails to start after updating to 2026.7.1 (OLLama/manual) | None yet |
| [#119270](https://github.com/openclaw/openclaw/issues/119270) | File tools strip leading `@` from destination paths, silently writing to wrong file | None yet |
| [#117742](https://github.com/openclaw/openclaw/issues/117742) | Multi-file `apply_patch` leaves earlier deletions committed on partial failure | None yet |
| [#123327](https://github.com/openclaw/openclaw/issues/123327) | Shared state WAL checkpoint corrupts SQLite page 1 on ext4 | None yet |

### 🟠 P1 — High Severity

| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | Write tool has no append mode — isolated cron sessions overwrite shared files | None yet |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) | DeepSeek V4 Flash produces incomplete turns (regression since 2026.5.26) | None yet |
| [#125679](https://github.com/openclaw/openclaw/issues/125679) | Matrix channel infinite restart loop on fresh account/room *(closed)* | — |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Unreaped hook/tool child process accumulation causes runtime degradation | None yet |
| [#114211](https://github.com/openclaw/openclaw/issues/114211) | Matrix room agents loop on no-reply output with stale session replay | None yet |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | Persistent file-based provider cooldown blocks users for hours after billing recovery | None yet |
| [#99586](https://github.com/openclaw/openclaw/issues/99586) | Runtime tool surface returns blank body after gateway-touching operations | None yet |
| [#123273](https://github.com/openclaw/openclaw/issues/123273) | Image attachments fail for named (non-default) agents | None yet |
| [#114234](https://github.com/openclaw/openclaw/issues/114234) | Usage-cost refresh lock never releasable after container PID reuse | None yet |
| [#112391](https://github.com/openclaw/openclaw/issues/112391) | Docker `:latest` tag regressed from 2026.7.1 to 2026.6.33 | None yet |
| [#124284](https://github.com/openclaw/openclaw/issues/124284) | Subagent spawn fails with vLLM + thinking: malformed XML tool calls (regression in beta.2) | None yet |
| [#113149](https://github.com/openclaw/openclaw/issues/113149) | CLI-backend empty_response fallback kills unrelated concurrent agent-tool sessions | None yet |
| [#112248](https://github.com/openclaw/openclaw/issues/112248) | `@openclaw/codex` plugin fails to register on gateway boot (TypeError) | None yet |
| [#86612](https://github.com/openclaw/openclaw/issues/86612) | Docker container restart loop with `OPENCLAW_SANDBOX=1` on Windows | None yet |
| [#84983](https://github.com/openclaw/openclaw/issues/84983) | Native cron agent-turn fire saturates gateway event loop | None yet |

**Closed today:**
- [#125679](https://github.com/openclaw/openclaw/issues/125679) — Matrix infinite restart loop (bisected to [#125302](https://github.com/openclaw/openclaw/issues/125302))
- [#120563](https://github.com/openclaw/openclaw/issues/120563) — Conversation history not sent to model on Ollama (resolved)

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Link |
|-------|---------|------|
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | Multi-Slot Memory Architecture — replace single `plugins.slots.memory` with purpose-specific slots | 6 comments, 3 👍 |
| [#63930](https://github.com/openclaw/openclaw/issues/63930) | Support Anthropic advisor tool (beta server-side tool) | 6 comments |
| [#56781](https://github.com/openclaw/openclaw/issues/56781) | Fallback model chain for compaction and LCM summaryModel | 6 comments |
| [#42276](https://github.com/openclaw/openclaw/issues/42276) | Reasoning stream — overwrite-mode thinking display | 6 comments |
| [#116470](https://github.com/openclaw/openclaw/issues/116470) | Runtime agent registry from config file + debug command exposure | 5 comments |

**Roadmap prediction:** The multi-slot memory architecture ([#60572](https://github.com/openclaw/openclaw/issues/60572)) and fallback model chain ([#56781](https://github.com/openclaw/openclaw/issues/56781)) address real production pain points (unbounded memory growth, silent compaction failures). These are likely candidates for the next stable release cycle once current P0/P1 bugs are resolved.

## 7. User Feedback Summary

**Key pain points expressed:**

- **Data loss anxiety** is the dominant theme — silent subagent result loss ([#44925](https://github.com/openclaw/openclaw/issues/44925)), file overwrites by cron sessions ([#40001](https://github.com/openclaw/openclaw/issues/40001)), and partial patch commits ([#117742](https://github.com/openclaw/openclaw/issues/117742)) all generate strong reactions (multiple diamond lobster ratings).
- **Multi-agent operators** report persistent friction: session state leakage across agents ([#114211](https://github.com/openclaw/openclaw/issues/114211)), wrong-file writes from `@` stripping ([#119270](https://github.com/openclaw/openclaw/issues/119270)), and concurrent session teardown ([#113149](https://github.com/openclaw/openclaw/issues/113149)).
- **Provider integration regressions** (DeepSeek V4 Flash, vLLM thinking mode, Codex plugin boot) suggest the rapid release cadence is outpacing integration test coverage.
- **Positive signal:** Several fixes landed today (llama-cpp consolidation, skill workshop description preservation, install policy warnings), indicating the team is actively responding.

## 8. Backlog Watch

**Stale or unaddressed issues requiring maintainer attention:**

| Issue | Age | Tags | Why It Matters |
|-------|-----|------|----------------|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 5 months | P0, diamond lobster, no-fix-pr | Silent subagent data loss — highest-impact open bug |
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | 5 months | P1, diamond lobster, no-fix-pr | Write tool missing append mode affects all cron-based agents |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | 4 months | P0, diamond lobster, stale | Billing cooldown persists across restarts, blocking users for hours |
| [#58957](https://github.com/openclaw/openclaw/issues/58957) | 5 months | P2, silver shellfish | Model switch fails silently with large context — no error clarity |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 2 months | P1, silver shellfish | Child process leaks degrade runtime over time |
| [#114612](https://github.com/openclaw/openclaw/issues/114612) | 1 month | P2, diamond lobster | SQLite memory tables have no retention policy — unbounded disk growth |
| [#84983](https://github.com/openclaw/openclaw/issues

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — Open-Source AI Agent Ecosystem
**Date:** 2026-08-20 | **Analyst:** Agnes

---

## 1. Ecosystem Overview

The open-source personal AI agent landscape is entering a stabilization-heavy phase, with nine of twelve tracked projects reporting active development and zero releases shipped project-wide—suggesting a collective pre-release hardening cycle rather than feature expansion. Data integrity and session reliability dominate community concerns across the board, while channel integration (Slack, Telegram, WhatsApp, Discord, LINE) remains the primary growth vector. The ecosystem is bifurcating: mature projects (OpenClaw, CoPaw, Hermes) are burning down P0 bugs in large backlogs, while smaller projects (Moltis, NanoBot, IronClaw) are shipping focused patches rapidly. Three projects (NullClaw, ZeptoClaw, and to a lesser extent PicoClaw) show minimal momentum, signaling potential consolidation or niche positioning.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Merged/Closed PRs | Releases | Open Issues | Health Signal |
|---|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 81 | None | 462 | 🔴 High volume, P0 backlog |
| **CoPaw** | 50 | 46 | 16 | None | 5 active | 🟢 Strong contributor momentum |
| **Hermes Agent** | 50 | 50 | 12 | None (v0.20.2 stale) | 41 | 🟡 Active, elevated risk |
| **ZeroClaw** | 44 | 50 | 1 | None (v0.8.3 stale) | Multiple RFCs | 🟡 Architecture transition |
| **NanoClaw** | 3 | 32 | 23 | None | 3 discussed | 🟢 High merge rate (72%) |
| **IronClaw** | 15 | 38 | ~10 | v1.3.0 (yesterday) | 6 | 🟢 Post-release stabilization |
| **LobsterAI** | 0 | 0 | 8 | None | 6 stale | 🟡 PRs outpacing issue resolution |
| **Moltis** | 4 | 9 | 6 | 20260818.10 (2d ago) | 0 open bugs | 🟢 Best bug-to-fix ratio (1:1) |
| **NanoBot** | — | 22 | 8 | None | 4 | 🟢 Strong, focused hardening |
| **PicoClaw** | 1 | 5 | 2 | None | 3 | 🟡 Low velocity, stale PRs |
| **NullClaw** | 0 | 0 | 0 | None | 0 (1 PR) | 🔴 Near-zero activity |
| **ZeptoClaw** | 0 | 0 | 0 | None | — | 🔴 Inactive |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of community engagement** is unmatched (500 issues/PRs daily) — indicative of the largest active user base and contributor pool in the ecosystem.
- **Most comprehensive multi-agent architecture** — subagent routing, delivery targets, and ambient owner resolution are production-grade concerns others are still conceptualizing (ZeroClaw's session-ownership RFC, IronClaw's sandbox epic).
- **Rich provider ecosystem** — llama-cpp consolidation, vLLM, DeepSeek, Gemini, and Anthropic support all under active pressure-testing.

**Technical approach differences:**
- OpenClaw favors a **gateway-centric monolith** with provider abstractions, whereas NanoClaw and IronClaw are moving toward **modular channel adapters** (Slack agents, local MCP transport). Moltis and NanoBot take a **single-agent-with-tools** approach, simpler but less multi-tenant.
- OpenClaw's **WAL/SQLite state model** is being stress-tested at scale (shared-state checkpoint corruption, P0 bug #123327) — a risk smaller projects avoid by design.

**Community size comparison:**
OpenClaw (~462 open issues, diamond-lobster-rated P0s) is an order of magnitude larger than its nearest competitor CoPaw (~5 active issues) or Hermes (~41 open issues). NanoClaw and IronClaw sit in a mid-tier with manageable but active backlogs. NullClaw and ZeptoClaw are effectively dormant.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Need |
|---|---|---|
| **Data loss / silent failure prevention** | OpenClaw, NanoBot, LobsterAI, ZeroClaw | Subagent result loss (#44925), stale background saves overwriting session data (#5271), file overwrites by cron (#40001), SOP step execution out of order (#10066) |
| **Session/state reliability** | OpenClaw, Hermes, ZeroClaw, NanoBot | Gateway startup failures (#108435), session history loss in multiplexed gateway (#90410), conversation cursor corruption (#5441), session persistence RFCs (#9487, #9600) |
| **Channel integration expansion** | NanoClaw, LobsterAI, Moltis, PicoClaw, IronClaw | Slack agents (#3357), Telegram groups (#3351), WhatsApp fixes (#1217, #1218), LINE webhooks (#3329), Discord parity (#79564), Dial SMS/voice (#3041) |
| **Multi-agent / multi-tenant architecture** | OpenClaw, IronClaw, ZeroClaw, CoPaw | Subagent delivery scoping (#126424), persistent per-user sandbox (#7732), session ownership RFC (#9487), multi-project directories (#6976) |
| **Windows compatibility** | Hermes, OpenClaw, ZeroClaw, CoPaw | BSOD from stale PID taskkill (#89614), Docker sandbox restart loop (#86612), 74 Windows test failures (#7462), desktop installer crash (#9290) |
| **Model provider regressions** | OpenClaw, Hermes, Moltis | DeepSeek V4 Flash incomplete turns (#88657), vLLM thinking XML malformed (#124284), GLM ultra reasoning rejected (#70058), GPT-5.6 Luna routing (#1181) |
| **Docker / deployment robustness** | NanoBot, OpenClaw, NanoClaw | OAuth in Docker (#5444), Node 26 / better-sqlite3 build failure (#3359), non-login shell setup bugs (#3354), `:latest` tag regression (#112391) |
| **Token/context management** | NanoBot, OpenClaw | Token count underestimation 30-50% (#5403), unbounded SQLite memory growth (#114612), compaction fallback chains (#56781) |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | CoPaw | Hermes Agent | NanoClaw | IronClaw | Moltis | NanoBot | LobsterAI |
|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Multi-agent orchestration + gateway | Desktop-first AI IDE + tooling | CLI + Desktop agent with skills | Slack/Telegram channel agents | Runtime/sandbox + automation | Lightweight multi-channel bot | Personal TUI agent | Desktop + IM agent |
| **Target user** | Operators, multi-agent teams | Developers, AI engineers | CLI power users, Windows desktop | Slack workspace admins | DevOps, automation teams | Self-hosted privacy-focused users | Individual personal assistants | Chinese-market desktop users |
| **Architecture** | Gateway monolith, provider-agnostic | Electron desktop + Qwen models | TUI/Desktop with IPC | Channel-adapter modular | Capability-response normalized | Apple Container sandboxes | Compact single-agent | Desktop + multi-IM |
| **Release cadence** | Beta-heavy (v2026.8.1-beta.2) | Stable (2.1.0) | v0.20.2 (Aug 16) | Continuous (no tags) | v1.3.0 (Aug 19) | Frequent patches | Intermittent | Sporadic |
| **Key differentiator** | Subagent routing + delivery targets | Email assistant + AI IDE integration | Skills hub + Copilot route | Slack agents feature parity | Persistent per-user sandbox | CWE-306 security hardening | Memory compaction + clarification tool | IM slash commands |

---

## 6. Community Momentum & Maturity

| Tier | Projects | Characterization |
|---|---|---|
| **Rapidly iterating** | NanoClaw, Moltis, IronClaw | High merge rates (72%, 67%), focused bug-bash cycles, recent releases, clean feedback loops |
| **High-velocity / high-risk** | OpenClaw, CoPaw, Hermes | Massive issue/PR throughput but P0 backlogs accumulating; stabilization phase outweighing feature velocity |
| **Steady maintenance** | NanoBot, LobsterAI | Moderate activity, healthy contributor base, LobsterAI's issue resolution lagging behind PR output |
| **Stalled / low momentum** | PicoClaw, NullClaw, ZeptoClaw | PicoClaw has open PRs going stale (>17 days); NullClaw and ZeptoClaw show near-zero engagement |

**Maturity signal:** The ecosystem is transitioning from "ship features" to "ship stability." Projects with the largest user bases (OpenClaw, CoPaw) are the most burdened by P0 data-loss bugs — a natural consequence of production scale. Smaller projects (Moltis, NanoBot) are benefiting from tighter scope and faster maintainer response times.

---

## 7. Trend Signals

| Trend | Evidence | Value for AI Agent Developers |
|---|---|---|
| **Session persistence is the new battleground** | ZeroClaw RFC #9487, OpenClaw subagent delivery scoping (#126424), IronClaw sandbox epic (#7732), CoPaw multi-project dirs (#6976) | Any agent product must solve state ownership across turns, channels, and restarts — this is the #1 architecture decision for 2026 |
| **Data-loss prevention is table stakes** | Diamond-lobster P0s across OpenClaw (#44925, #40001), NanoBot (#5271), ZeroClaw (#10066) | Silent failures are reputation-ending; observability and retry semantics must be built-in, not bolted on |
| **Channel expansion is the growth engine** | NanoClaw (Slack agents, Dial), LobsterAI (IM slash commands), Moltis (WhatsApp), PicoClaw (LINE, Telegram topics) | Multi-channel presence is expected; projects investing in adapter modularity will outperform monolithic ones |
| **Windows compatibility is an unpaid technical debt** | Hermes (#89614 BSOD, #83846 desktop destruction), ZeroClaw (74 test failures), OpenClaw (Docker loop) | CI parity with Linux is non-negotiable; projects without Windows test coverage will lose enterprise users |
| **Model-provider regression coverage is insufficient** | OpenClaw (DeepSeek, vLLM), Hermes (GLM, MiniMax), Moltis (GPT-5.6 Luna) | Rapid release cadence is outpacing integration test coverage — automated provider regression suites are a competitive advantage |
| **Self-hosted deployment robustness is a differentiator** | NanoClaw setup hardening (#3339, #3354), NanoBot Docker OAuth fix (#5445), Moltis security patches (#1216) | "It just works on first install" is a rare and valuable property; setup friction is the #1 churn driver |
| **Paid/monetized tooling is emerging** | NanoBot ScanPay x402 request (#5447), ClinePass provider in Hermes (#90416) | Agent ecosystems are maturing toward micropayment and marketplace models — early architectural support for tool monetization will matter |

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-20

## 1. Today's Overview

NanoBot is experiencing a **high-velocity patch cycle** with 22 PRs updated in the last 24 hours, 8 of which were merged or closed. Activity is overwhelmingly focused on **stability hardening and Docker/OAuth bug fixes**, with no new releases deployed. Four open issues remain, including one security-scanning feature request and three genuine bugs. The project's health is strong: maintainers are actively closing PRs at a ~36% merge rate, and critical session-data race conditions are being addressed.

## 2. Releases

**None.** No new versions were published today. The team appears to be accumulating bug fixes before a consolidated release.

## 3. Project Progress

### Merged / Closed PRs (8)

| PR | Title | Author |
|---|---|---|
| [#5443](https://github.com/HKUDS/nanobot/pull/5443) | fix(tui): expose `/exit` in command menu | KailBug |
| [#5440](https://github.com/HKUDS/nanobot/pull/5440) | perf(memory): reuse conversation prefix for local compaction | chengyongru |
| [#4527](https://github.com/HKUDS/nanobot/pull/4527) | Add `ask_clarification` tool | ZhouJ-sh |
| [#5438](https://github.com/HKUDS/nanobot/pull/5438) | fix(webui): return promptly after Ctrl-C | chengyongru |
| [#5341](https://github.com/HKUDS/nanobot/pull/5341) | fix(skills): make weather workflow Windows-safe | mercael91 |
| [#4282](https://github.com/HKUDS/nanobot/pull/4282) | Add file management features to the settings view | Liyulingyue |
| [#5430](https://github.com/HKUDS/nanobot/pull/5430) | fix(agent): release completed task groups | yu-xin-c |
| [#5379](https://github.com/HKUDS/nanobot/pull/5379) | fix(memory): preserve full consolidation input | dajiaohuang |

**Key advances:**
- **Memory compaction performance** improved by reusing the conversation prefix instead of rebuilding it ([#5440](https://github.com/HKUDS/nanobot/pull/5440))
- **Agent lifecycle cleanup** fixed — completed task groups are now properly released ([#5430](https://github.com/HKUDS/nanobot/pull/5430))
- **Windows compatibility** patched for the weather skill's bare `curl` usage ([#5341](https://github.com/HKUDS/nanobot/pull/5341))
- **WebUI responsiveness** restored after Ctrl-C ([#5438](https://github.com/HKUDS/nanobot/pull/5438))
- **Clarification tool** finally merged after ~2 months in review ([#4527](https://github.com/HKUDS/nanobot/pull/4527))

### Open PRs Requiring Attention (14)

Notable open PRs include OAuth storage routing ([#5446](https://github.com/HKUDS/nanobot/pull/5446)), WebUI turn observability ([#5420](https://github.com/HKUDS/nanobot/pull/5420)), and the long-standing `nano_timer` core tool ([#4853](https://github.com/HKUDS/nanobot/pull/4853), open since July 8).

## 4. Community Hot Topics

### Most Discussed Issues

1. **[Issue #5425](https://github.com/HKUDS/nanobot/issues/5425)** — *Support legacy socks:// proxy URLs for custom OpenAI-compatible providers*
   - Users configuring custom providers via `socks://` proxy URLs hit failures before requests reach the provider. This reflects a real deployment need: enterprise and privacy-conscious users rely on SOCKS proxies for API access.
   - **Signal:** The proxy handling code needs to support both `socks5://` (standard) and `socks://` (legacy alias). PR [#5439](https://github.com/HKUDS/nanobot/pull/5439) addresses the standard scheme but explicitly excludes the legacy alias — this issue may need a follow-up.

2. **[Issue #5447](https://github.com/HKUDS/nanobot/issues/5447)** — *Paid security-scan MCP integration (nanobot + ScanPay x402)*
   - A community member proposes integrating a Solana-based micropayment security scanner (0.0007 SOL per scan) as a paid MCP service. This is a **feature request, not a bug**, and represents an emerging use case: autonomous agents with paid tooling.
   - **Signal:** The agent ecosystem is maturing toward monetized tool integrations. The maintainers should evaluate whether to support x402 micropayment protocols.

3. **[Issue #5444](https://github.com/HKUDS/nanobot/issues/5444)** — *Failed to login OpenAI via OAuth in Docker*
   - OAuth login fails in Docker with a `PermissionError` when exchanging the authorization code. Directly blocked by PR [#5445](https://github.com/HKUDS/nanobot/pull/5445) (merged) and [#5446](https://github.com/HKUDS/nanobot/pull/5446) (open).
   - **Signal:** Docker-first workflows are a priority for the user base. OAuth persistence across container replacements is a real pain point.

### Most Active PRs

- **[PR #5420](https://github.com/HKUDS/nanobot/pull/5420)** — *WebUI turn observability* — adds turn-level visibility, tool activity tracking, and interrupted-work rendering. Users want **debuggability** into agent internals.
- **[PR #4853](https://github.com/HKUDS/nanobot/pull/4853)** — *nano_timer core tool* — open since July 8, adds dependency-free UTC/local time and calendar tools. A **long-pending feature** that users have wanted for months.
- **[PR #5271](https://github.com/HKUDS/nanobot/pull/5271)** — *Prevent stale background task saves* — priority p0, addresses session data corruption. Critical for **data integrity**.

## 5. Bugs & Stability

### Critical / High Severity

| Issue/PR | Description | Fix Status |
|---|---|---|
| [#5444](https://github.com/HKUDS/nanobot/issues/5444) | OAuth login fails in Docker (PermissionError) | Fix merged: [#5445](https://github.com/HKUDS/nanobot/pull/5445), [#5446](https://github.com/HKUDS/nanobot/pull/5446) |
| [#5441](https://github.com/HKUDS/nanobot/issues/5441) | Dream run blocks memory cursor after tool error recovery | Fix open: [#5442](https://github.com/HKUDS/nanobot/pull/5442) |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) | Stale background task saves overwrite session data (p0) | Fix open, not yet merged |
| [#5403](https://github.com/HKUDS/nanobot/pull/5403) | Token consolidation never triggers (API-reported vs local count mismatch) | Fix open, not yet merged |

### Medium Severity

- [#5425](https://github.com/HKUDS/nanobot/issues/5425) — Legacy `socks://` proxy URLs rejected (works around HTTPX limitation)
- [#5439](https://github.com/HKUDS/nanobot/pull/5439) — Proxy fix PR merged but **explicitly excludes** `socks://` alias, leaving #5425 unfixed

### Stability Assessment

**Session data corruption** remains the top stability concern. PR [#5271](https://github.com/HKUDS/nanobot/pull/5271) (p0) addresses stale background saves but is still open. The Dream cursor bug ([#5441](https://github.com/HKUDS/nanobot/issues/5441)) causes **infinite reprocessing** of the same history batch — a serious correctness issue. The token consolidation bug ([#5403](https://github.com/HKUDS/nanobot/pull/5403)) means users with modern models may exceed context windows without triggering compaction.

## 6. Feature Requests & Roadmap Signals

### User-Requested Features

1. **Paid MCP / x402 integration** ([#5447](https://github.com/HKUDS/nanobot/issues/5447)) — Micropayment-scanned security tools. Signals growing demand for **monetized agent tooling**.
2. **Follow-up suggestions** ([#5408](https://github.com/HKUDS/nanobot/pull/5408)) — Ephemeral, chat-scoped suggestions after WebUI turns. Matches DeerFlow interaction patterns.
3. **Manual-only skill invocation** ([#5405](https://github.com/HKUDS/nanobot/pull/5405)) — Side-effect skills (deployment, publishing) should require explicit user confirmation. **Safety-first design**.
4. **nano_timer core tool** ([#4853](https://github.com/HKUDS/nanobot/pull/4853)) — Dependency-free time/timezone/calendar. Open 43 days; likely in next minor release.
5. **WebUI turn observability** ([#5420](https://github.com/HKUDS/nanobot/pull/5420)) — Turn-level visibility, tool activity, interrupted-work rendering. Users want **debuggability**.

### Predicted Next Release Inclusions

- `ask_clarification` tool (just merged, [#4527](https://github.com/HKUDS/nanobot/pull/4527))
- `nano_timer` core tool ([#4853](https://github.com/HKUDS/nanobot/pull/4853))
- File management in settings view ([#4282](https://github.com/HKUDS/nanobot/pull/4282))
- Docker OAuth persistence fixes
- Memory compaction performance improvements

## 7. User Feedback Summary

### Pain Points

1. **Docker + OAuth is broken.** Multiple users report permission errors when logging in via OAuth in containerized environments. The root cause (unmanaged `platformdirs` default) is fixed, but the fix is still rolling out.
2. **Proxy configuration is fragile.** Custom OpenAI-compatible providers with `socks://` proxy URLs fail silently before reaching the provider. The `socks://` alias is a common convention that users expect to work.
3. **Dream runs can loop infinitely.** When a tool error is recovered by the model, the memory cursor still advances incorrectly, causing the same batch to be reprocessed by every subsequent Dream run.
4. **Token counts are inaccurate.** Local tiktoken estimation is 30-50% lower than API-reported counts for modern models, so consolidation never triggers. Users are at risk of exceeding context windows.
5. **Windows compatibility gaps.** Bare `curl` in skills resolves to PowerShell's `Invoke-WebRequest` alias, causing unexpected failures.

### Satisfaction Signals

- Users are **actively contributing fixes** — 8 PRs merged today with diverse authors.
- The `ask_clarification` tool was requested and is now merged after a long review, showing **maintainer responsiveness**.
- Docker-first workflows are a **priority concern** with multiple coordinated fixes.
- The community is building **extensions** (ScanPay x402, AgentBridge) on top of NanoBot, indicating ecosystem growth.

## 8. Backlog Watch

### Long-Unanswered Items Needing Maintainer Attention

| Item | Days Open | Severity | Notes |
|---|---|---|---|
| [#4853](https://github.com/HKUDS/nanobot/pull/4853) — nano_timer core tool | 43 | p1 | Dependency-free time tool, high user demand, no merge signal |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) — Prevent stale background saves | 14 | p0 | Session data corruption, still open |
| [#5403](https://github.com/HKUDS/nanobot/pull/5403) — Token consolidation fix | 4 | p1 | 30-50% undercount, context window risk |
| [#5405](https://github.com/HKUDS/nanobot/pull/5405) — Manual-only skill invocation | 4 | p2 | Safety feature, has conflicts |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) — WebUI turn observability | 2 | p2 | High user value, no merge signal |
| [#5446](https://github.com/HKUDS/nanobot/pull/5446) — OAuth storage routing | 1 | p2 | Depends on [#5445](https://github.com/HKUDS/nanobot/pull/5445) merge |

### Recommended Maintainer Actions

1. **Merge or close [#4853](https://github.com/HKUDS/nanobot/pull/4853)** — The nano_timer tool has been open for 6 weeks with no activity. Either merge it or request changes.
2. **Prioritize [#5271](https://github.com/HKUDS/nanobot/pull/5271)** — This is a p0 session-data corruption bug. It should ship before the next release.
3. **Resolve [#5425](https://github.com/HKUDS/nanobot/issues/5425) vs [#5439](https://github.com/HKUDS/nanobot/pull/5439)** — PR [#5439](https://github.com/HKUDS/nanobot/pull/5439) explicitly excludes `socks://` but the issue requests support. Clarify the decision with the reporter.
4. **Review [#5447](https://github.com/HKUDS/nanobot/issues/5447)** — The paid security-scan MCP request is outside the core project scope but represents an important ecosystem signal. A brief maintainer response would set expectations.

---

*Digest generated from GitHub data on 2026-08-20. Source: [HKUDS/nanobot](https://github.com/HKUDS/nanobot)*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-20

## 1. Today's Overview

Hermes Agent shows high development velocity with 50 issues and 50 PRs updated in the last 24 hours (41 open issues, 43 open PRs). Activity is intense but no new releases were published today. The project is in a heavy stabilization phase: several P1 bugs affecting Windows and the CLI update flow are active, while a batch of quality-of-life and desktop-compatibility fixes are landing via open PRs. The most-discussed issue (#66616, 60 comments) centers on skills-index freshness, suggesting ongoing tooling-catalog reliability concerns. Overall project health is **active with elevated risk** — multiple P1 regressions in the install/update path and Windows platform demand close monitoring.

## 2. Releases

No new releases published today. The latest referenced version remains **v0.20.2** (released 2026-08-16).

## 3. Project Progress

**Closed/Merged today (7 PRs + 5 Issues):**

- **[PR #90064](https://github.com/NousResearch/hermes-agent/pull/90064)** — *fix(title): honor reasoning_effort so thinking can be disabled on title generation* — Resolves a docstring/code gap where title generation was invoking reasoning models at `max_tokens=64`, causing empty responses.
- **[PR #90063](https://github.com/NousResearch/hermes-agent/pull/90063)** — *fix(title): retry without response_format when upstream rejects it* — Added graceful fallback when providers reject the `json_schema` structured-output shape.
- **[Issue #82140](https://github.com/NousResearch/hermes-agent/issues/82140)** — *feat(desktop): expose resolved connection mode to skills, MCP, and plugins* — Closed; connection mode (`local`/`remote`) now accessible to extensions.
- **[Issue #74295](https://github.com/NousResearch/hermes-agent/issues/74295)** — *Copilot route: reasoning_effort 'ultra' clamps to 'medium'* — Closed; silent weakening of the strongest reasoning setting on GitHub Copilot route.
- **[Issue #70058](https://github.com/NousResearch/hermes-agent/issues/70058)** — *reasoning_effort: "ultra" rejected by GLM API* — Closed; GLM-5.2 now handled when ultra is selected.
- **[Issue #89823](https://github.com/NousResearch/hermes-agent/issues/89823)** — *Bot Mode 'Create on' picker never appears* — Closed; IPC now returns an array instead of a registry object.
- **[Issue #72590](https://github.com/NousResearch/hermes-agent/issues/72590)** — *Focus layout tab-switch UI freeze* — Closed.

**Notable open PRs advancing:**

- [#90417](https://github.com/NousResearch/hermes-agent/pull/90417) — Restores inline reasoning for providers like MiniMax-M3 that stream `<think>…</think>` inside content.
- [#90414](https://github.com/NousResearch/hermes-agent/pull/90414) — Fixes peer-window state loss on shared gateways.
- [#90358](https://github.com/NousResearch/hermes-agent/pull/90358) — Prevents Bot Mode sweep from swallowing ordinary user sessions.
- [#90128](https://github.com/NousResearch/hermes-agent/pull/90128) — Provides a legible error instead of a cryptic .NET crash on Windows Constrained Language Mode.
- [#17938](https://github.com/NousResearch/hermes-agent/pull/17938) — Adds workspace-binding guard for repo side-effects (security-relevant, broad blast radius).

## 4. Community Hot Topics

| Rank | Issue/PR | Comments | Focus |
|------|----------|----------|-------|
| 1 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | 60 | Skills Hub index freshness (29.8h old vs 26h limit); cron reliability |
| 2 | [#84834](https://github.com/NousResearch/hermes-agent/issues/84834) — Webhook Feature Package meta-issue | 19 | Comprehensive webhook surface repair (ingress, execution, delivery, UI, docs) |
| 3 | [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) — ZIP fallback deletes built desktop app | 12 | P1: updates silently remove the desktop binary on Windows |
| 4 | [#79564](https://github.com/NousResearch/hermes-agent/issues/79564) — Discord Feature Parity meta-issue | 8 | API v10 / discord.py 2.7.1 alignment campaign |
| 5 | [#83529](https://github.com/NousResearch/hermes-agent/issues/83529) — `hermes update` destroys hermes | 6 | P1: catastrophic update failure on Debian Trixie |

**Analysis:** The skills-index staleness issue (#66616) dominates discussion, indicating users rely heavily on the Skills Hub and are frustrated by degraded freshness probes. The webhook meta-issue (#84834) and Discord campaign (#79564) reflect sustained interest in expanding Hermes's integration surface. The P1 install/update bugs (#83846, #83529) are the most operationally urgent community concerns.

## 5. Bugs & Stability

### P1 — Critical

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#89614](https://github.com/NousResearch/hermes-agent/issues/89614) | Hermes kills `svchost.exe` via stale-PID `taskkill /F /PID` → repeated `0xEF` BSODs on Windows 11 | None yet |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | ZIP fallback deletes the built desktop app; later updates report "Already up to date" | None yet |
| [#83529](https://github.com/NousResearch/hermes-agent/issues/83529) | `hermes update` fails catastrophically, destroying the install | None yet |
| [#90410](https://github.com/NousResearch/hermes-agent/issues/90410) | Multiplexed gateway: routed profile loses conversation history every turn (`history=0`) | None yet |

### P2 — High

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#90299](https://github.com/NousResearch/hermes-agent/issues/90299) | False-positive `TERMINAL_CWD` deprecation warning on every startup | — |
| [#84064](https://github.com/NousResearch/hermes-agent/issues/84064) | `hermes config set/unset` breaks on provider keys containing a literal dot | — |
| [#90229](https://github.com/NousResearch/hermes-agent/issues/90229) | Desktop right-sidebar file tree stuck on skeleton indefinitely (Windows) | — |
| [#85422](https://github.com/NousResearch/hermes-agent/issues/85422) | macOS installer predates remote-client onboarding; forces local bootstrap | — |
| [#89647](https://github.com/NousResearch/hermes-agent/issues/89647) | Desktop reasoning pane dead for MiniMax-M3 (reasoning not extracted) | [#90417](https://github.com/NousResearch/hermes-agent/pull/90417) open |
| [#90365](https://github.com/NousResearch/hermes-agent/issues/90365) | Desktop model settings: "Expensive Model Warning" has no confirm button | — |
| [#90360](https://github.com/NousResearch/hermes-agent/issues/90360) | `hermes sessions archive` filters return empty for desktop sessions newer than ~Aug 14 | — |
| [#85605](https://github.com/NousResearch/hermes-agent/issues/85605) | Desktop Electron fails WebSocket handshake with `hermes serve` (404 on session token) | — |
| [#90134](https://github.com/NousResearch/hermes-agent/issues/90134) | `hermes desktop` build fails on `blockmap.js` (Windows) | — |

### P3 — Medium

| Issue | Summary |
|-------|---------|
| [#90333](https://github.com/NousResearch/hermes-agent/issues/90333) | Desktop reauth via Nous portal — Google passkey 2FA fails on macOS ("try again" loop) |
| [#90316](https://github.com/NousResearch/hermes-agent/issues/90316) | Remote-primary Desktop starts a loopback agent for "This device" unnecessarily |
| [#89497](https://github.com/NousResearch/hermes-agent/issues/89497) | Bot Mode group chat hangs on "thinking" then reports "out of Nous credits" (bots don't use Nous) |

**Assessment:** Three P1 bugs (Windows BSOD risk, desktop app destruction on update, session history loss in multiplexed gateway) are unaddressed and represent significant stability risks, especially for Windows users. The MiniMax reasoning fix (#90417) is the only P2 with an active PR.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood for Next Release |
|----------|-------------|----------------------------|
| [#90007](https://github.com/NousResearch/hermes-agent/issues/90007) | Resource-aware low-memory Windows execution profile | Medium — niche but well-scoped |
| [#89995](https://github.com/NousResearch/hermes-agent/issues/89995) | Expose Bot Mode group chat rooms in web dashboard & gateway | Medium — requires desktop↔web sync |
| [#63852](https://github.com/NousResearch/hermes-agent/issues/63852) | Native fallback-chain readiness check without full agent sessions | Medium — improves DX significantly |
| [#90416](https://github.com/NousResearch/hermes-agent/pull/90416) | Add ClinePass provider (13 curated open models, $9.99/mo) | Medium — new provider integration |
| [#90411](https://github.com/NousResearch/hermes-agent/pull/90411) | CI-ready JSONL event output for one-shot runs | High — directly addresses automation/CI use case; PR is ready |
| [#84483](https://github.com/NousResearch/hermes-agent/issues/84483) | Desktop connect to remote backend with self-hosted auth_provider | Low-Medium — self-hosted OIDC is a smaller user segment |

**Prediction:** The JSONL event output PR (#90411) and the ClinePass provider PR (#90416) are the most likely feature inclusions in the next release, as both are complete, self-contained, and address clear user demand.

## 7. User Feedback Summary

**Pain points:**
- **Update/install path is fragile on Windows** — multiple reports of the desktop app being destroyed or failing to build (#83846, #83529, #90134, #89614). This is the dominant complaint.
- **Session history loss in multiplexed gateway mode** (#90410) — users sharing adapter credentials across contacts lose conversation context each turn, a critical reliability issue.
- **Reasoning pane broken for non-Anthropic providers** (#89647) — MiniMax-M3 streams reasoning inline but the desktop UI never renders it; partially addressed by PR #90417.
- **False-positive deprecation warnings** (#90299) — noise on every TUI startup erodes trust.
- **Config key parsing breaks on dots** (#84064) — provider names with version numbers (e.g., `providers.my-provider.v2`) silently corrupt `config.yaml`.
- **Bot Mode group chat credit reporting is incorrect** (#89497) — bots that don't use Nous credits are falsely flagged as out of credits.
- **macOS reauth loop** (#90333) — Google passkey 2FA is unusable for some users.

**Positive signals:**
- Active community engagement (50 issues/PRs in 24h).
- Several bot-mode session-ownership bugs are being fixed (#90358, #89901, #90329).
- Desktop connection-mode exposure (#82140) is now closed, improving plugin extensibility.
- Windows Constrained Language Mode now fails with a clear error (#90128).

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|----------------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Open since 2026-07-18 (33 days) | 60 comments, no resolution; skills-index reliability affects all users |
| [#84834](https://github.com/NousResearch/hermes-agent/issues/84834) | Open since 2026-08-12 (8 days) | Meta-issue tracking the entire webhook surface; 

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-20

---

## 1. Today's Overview

PicoClaw showed moderate development activity on 2026-08-20, with **5 PR updates** (3 open, 2 closed) and **1 issue resolved**. No new releases were published, indicating the project is in a steady-state maintenance window rather than a release cycle. The closed PRs suggest the team is prioritizing usability refinements (Telegram UX) and backend configuration fixes over major feature pushes. Community engagement, as measured by comments and reactions, remains low across all tracked items, which may signal either a quiet contributor base or issues not yet drawing broad attention.

---

## 2. Releases

**No new releases** were published in the last 24 hours. The latest known commit referenced in issue #1305 is `26f623e` (version 26f623e). Users should monitor the [releases page](https://github.com/sipeed/picoclaw/releases) for the next tagged version.

---

## 3. Project Progress

**Merged / Closed PRs today:**

- **[#3341](https://github.com/sipeed/picoclaw/pull/3341)** — *feat(telegram): add interactive command UX and formatted ephemeral fallback* (Closed/Merged)
  - Improved the Telegram command experience by reducing cognitive load for `/memory` and `/help` commands, replacing verbose full subcommand grammars with a more user-friendly interactive format. This addresses a real usability gap in the Telegram channel.

- **[#3200](https://github.com/sipeed/picoclaw/pull/3200)** — *feat(models): add configurable default fallback chain* (Closed)
  - Enabled users to configure a persistent default model fallback chain through the web UI and backend API, allowing drag-and-drop reordering. This is a meaningful quality-of-life improvement for multi-model deployments.

**Open PRs under active review:**

- [#3329](https://github.com/sipeed/picoclaw/pull/3329) — LINE webhook configuration fix
- [#3316](https://github.com/sipeed/picoclaw/pull/3316) — Routed-agent context management (stale)
- [#3315](https://github.com/sipeed/picoclaw/pull/3315) — Telegram topic support in private chats (stale)

---

## 4. Community Hot Topics

| Item | Type | Engagement | Link |
|------|------|-----------|------|
| Issue #1305 | Bug | 4 comments, 0 👍 | [Issue #1305](https://github.com/sipeed/picoclaw/issues/1305) |
| PR #3329 | Bug Fix | Active review | [PR #3329](https://github.com/sipeed/picoclaw/pull/3329) |
| PR #3316 | Bug Fix | Stale, no reactions | [PR #3316](https://github.com/sipeed/picoclaw/pull/3316) |
| PR #3315 | Feature | Stale, no reactions | [PR #3315](https://github.com/sipeed/picoclaw/pull/3315) |

**Analysis:** Issue #1305 is the most discussed item, with 4 comments — a relatively high count for this project. It concerns a banner being printed to STDOUT, which breaks shell completion flows. This suggests users are actively relying on PicoClaw's CLI completion features in production workflows, and even minor output pollution is felt acutely. The Telegram topic PR (#3315) and routed-agent context PR (#3316) are both marked stale, indicating they may need maintainer re-engagement to avoid stagnation.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR | Link |
|----------|------|-------------|--------|------|
| **Medium** | #1305 | New banner prints to STDOUT, breaking zsh completion flow | Closed (issue resolved) | [Issue #1305](https://github.com/sipeed/picoclaw/issues/1305) |
| **Medium** | #3328 (via #3329) | `webhook_host` / `webhook_port` declared but never read by LINE channel; mounted on shared gateway | In progress ([PR #3329](https://github.com/sipeed/picoclaw/pull/3329)) | [PR #3329](https://github.com/sipeed/picoclaw/pull/3329) |
| **High** | #3316 | Routed-agent context management ignores history, summarization, compression, and seahorse bootstrap | In progress ([PR #3316](https://github.com/sipeed/picoclaw/pull/3316)) | [PR #3316](https://github.com/sipeed/picoclaw/pull/3316) |

**Assessment:** The routed-agent context bug (#3316) is the most severe open issue — it causes agents to lose all conversation state across messages, which is a fundamental reliability failure for multi-agent deployments. The LINE webhook issue (#3329) is a configuration gap that could prevent the LINE channel from functioning correctly in production. No crashes or regressions were reported today.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Likelihood |
|--------|--------|-----------|
| Telegram interactive command UX | #3341 (merged) | ✅ Already shipped |
| Configurable model fallback chain | #3200 (merged) | ✅ Already shipped |
| Telegram topic support in private chats | #3315 | 🟡 Likely — PR exists, needs review |
| LINE webhook configuration fix | #3329 | 🟡 Likely — PR exists, needs review |
| Routed-agent context persistence | #3316 | 🟡 Uncertain — stale, complex fix |

**Outlook:** The project appears to be iterating on **channel-specific improvements** (Telegram, LINE) and **model configuration flexibility**. The merged fallback chain feature (#3200) suggests the roadmap continues to prioritize multi-model orchestration. If #3315 and #3329 are reviewed soon, the next release may focus on channel reliability and Telegram private-chat support.

---

## 7. User Feedback Summary

- **Pain Point — Shell Completion Breakage:** Users relying on PicoClaw's CLI completion (zsh/bash) are frustrated by banner output polluting stdout. This is a usability regression from PR #1008, as noted in #1305. Users expect clean shell integration.
- **Pain Point — Routed Agents Lose Context:** Users deploying routed-agent setups report that agents do not retain conversation history or trigger auto-compaction. This undermines the core value proposition of multi-agent routing and is a significant dissatisfaction signal.
- **Satisfaction — Telegram UX Improvements:** The merged PR #3341 directly addresses user complaints about verbose `/help` output and complex subcommand syntax, suggesting the team is responsive to Telegram-specific feedback.
- **Satisfaction — Model Fallback Configurability:** PR #3200 shows users value granular control over model fallback chains, and the web UI integration is well-received.

---

## 8. Backlog Watch

| Item | Age | Status | Risk | Link |
|------|-----|--------|------|------|
| #3316 — Routed-agent context management | 17 days | Stale, no maintainer response | 🔴 High — core feature broken for multi-agent users | [PR #3316](https://github.com/sipeed/picoclaw/pull/3316) |
| #3315 — Telegram topic support in private chats | 17 days | Stale, no maintainer response | 🟡 Medium — niche but important for forum-style Telegram bots | [PR #3315](https://github.com/sipeed/picoclaw/pull/3315) |
| #3329 — LINE webhook config fix | 9 days | Open, under review | 🟡 Medium — blocks LINE channel production use | [PR #3329](https://github.com/sipeed/picoclaw/pull/3329) |

**Recommendation:** Maintainers should prioritize reviewing PR #3316 and #3315, as both have been open for over two weeks without updates. PR #3329 is more recent and may be closer to merge. The routed-agent context bug is the highest-impact issue in the backlog and deserves immediate attention given its effect on a core deployment pattern.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-20

## 1. Today's Overview

NanoClaw shows strong development velocity with 32 PRs updated in the last 24 hours (23 merged/closed, 9 still open) and 3 actively discussed issues. No new releases were published today. The project is in an active integration and hardening phase: the core team is shipping Slack agents feature parity, expanding channel support (Dial, Telegram groups, Cursor), and upgrading runtime compatibility (Node 22+ baseline, better-sqlite3 13.x). All three open issues are setup/deployment-adjacent bugs rather than core runtime failures, suggesting baseline stability is intact.

## 2. Releases

No new releases published in the last 24 hours.

## 3. Project Progress

**Merged / Closed PRs (today):**

- **#3357** — `setup: --slack-agents installs the whole Slack agents feature` — The setup script now yields a base Slack experience with `bash nanoclaw.sh` and the full agents feature (child bots, shared a2a rooms, canvases, DM onboarding) with `--slack-agents`. [[Link](https://github.com/nanocoai/nanoclaw/pull/3357)]
- **#3358** — `slack: split the payload — base adapter in /add-slack, agents feature in /slack-agent-flow` — Companion structural split enabling the above. [[Link](https://github.com/nanocoai/nanoclaw/pull/3358)]
- **#3351** — `feat(telegram): add approved group connection picker` — Adds a `/connect_group` DM command backed by Telegram's native group picker, routed through existing approval flow. [[Link](https://github.com/nanocoai/nanoclaw/pull/3351)]
- **#3352** — `docs(telegram): document approved group connection flow` — Documents the `/connect_group` flow, security boundary, and troubleshooting in `/add-telegram`. [[Link](https://github.com/nanocoai/nanoclaw/pull/3352)]
- **#3340** — `fix(approvals): record the delivering instance on pending_approvals` — OneCLI credential cards are now posted and edited by the same bot identity that owns the DM. [[Link](https://github.com/nanocoai/nanoclaw/pull/3340)]
- **#3342** — `feat(slack): decline owner-absent channel invites instead of carding them` — Bot now declines channel invites from non-owner members in-place rather than escalating to the owner. [[Link](https://github.com/nanocoai/nanoclaw/pull/3342)]
- **#3339** — `fix(setup): fail closed when a stored sign-in cannot be verified` — Unverifiable stored account credentials now fail setup instead of being silently accepted. [[Link](https://github.com/nanocoai/nanoclaw/pull/3339)]
- **#3341** — `fix(provisioning): derive the Slack service from the credential's issuer` — Pairs install token (account service) with Slack service auth, fixing independent configuration drift. [[Link](https://github.com/nanocoai/nanoclaw/pull/3341)]
- **#3344** — `feat(provisioning): optional request-origin metadata on app creation` — Adds four additive metadata fields describing request origin during Slack app provisioning. [[Link](https://github.com/nanocoai/nanoclaw/pull/3344)]
- **#3345** — `feat(setup): forward optional client metadata on Slack service requests` — `setup/channels/slack-auto.ts` now forwards `client_version` and related metadata. [[Link](https://github.com/nanocoai/nanoclaw/pull/3345)]
- **#3025** — `fix(container): raise the agent SDK's 32000 output-token cap` — Raises the agent SDK output-token ceiling. [[Link](https://github.com/nanocoai/nanoclaw/pull/3025)]

## 4. Community Hot Topics

- **Node 26 / better-sqlite3 build failure** — Issue [#3359](https://github.com/nanocoai/nanoclaw/issues/3359): `check_node` in `setup.sh` only enforces a lower bound, letting Node 26 pass validation, but `better-sqlite3@11.10.0` cannot compile against it. A fix PR exists: [#3249](https://github.com/nanocoai/nanoclaw/pull/3249) ("handle an existing Node outside the supported range") and [#3360](https://github.com/nanocoai/nanoclaw/pull/3360) (upgrades better-sqlite3 to 13.0.3, raises min Node to 22). **Underlying need:** keep setup checks aligned with the actual supported runtime window as ecosystem Node versions advance.
- **Setup assumptions about interactive shells** — Issue [#3354](https://github.com/nanocoai/nanoclaw/issues/3354): Non-login/headless SSH installs produce 0-byte channel files and run `onecli` checks before PATH is fixed. **Underlying need:** robustness for server/container deployment scenarios.
- **Slack agents feature parity** — PR [#3362](https://github.com/nanocoai/nanoclaw/pull/3362) (open) continues the Slack agents work by validating flow prerequisites. High community interest expected as this is a flagship multi-agent capability.
- **Dial channel adapter** — PR [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) (open since Jul 14) and PR [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) add SMS + AI voice call support. Long-open but actively discussed, indicating strong user demand for telephony channels.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **High** | [#3353](https://github.com/nanocoai/nanoclaw/issues/3353) | Dial records SMS as `delivered` when the carrier rejects it post-send; retry budget and owner notification are never triggered. | No fix PR yet. |
| **Medium** | [#3359](https://github.com/nanocoai/nanoclaw/issues/3359) | Node 26 passes setup check but `better-sqlite3` fails to compile → `deps_failed` abort. | Fix in progress: [#3360](https://github.com/nanocoai/nanoclaw/pull/3360), [#3249](https://github.com/nanocoai/nanoclaw/pull/3249) |
| **Medium** | [#3354](https://github.com/nanocoai/nanoclaw/issues/3354) | Setup leaves 0-byte channel files and runs `onecli` before PATH fix on non-login shells. | No fix PR yet. |
| **Low** | #3339 (merged) | Previously unverifiable stored sign-ins were accepted; now correctly fails closed. | ✅ Merged |

## 6. Feature Requests & Roadmap Signals

- **Dial (SMS + AI voice)** — PRs [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) and [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) are open but advanced enough to signal imminent inclusion. Expect Dial as a first-class channel in the next release cycle.
- **Cursor Agent SDK integration** — PRs [#3355](https://github.com/nanocoai/nanoclaw/pull/3355) (`/add-cursor` setup skill) and [#3356](https://github.com/nanocoai/nanoclaw/pull/3356) (Cursor Agent SDK payload) were opened today. Strong signal that Cursor is being added as a supported agent provider.
- **Agent mailbox seam & registry** — PR [#3349](https://github.com/nanocoai/nanoclaw/pull/3349) introduces a pluggable mailbox abstraction (SQLite default). Suggests a forthcoming multi-tenant or cross-agent messaging backbone.
- **Telegram group connections** — Already merged (#3351, #3352). Group-level onboarding is now live.
- **Slack full agents feature** — With #3357 merged and #3362 open, the `--slack-agents` flag will likely ship as the default Slack experience in the next release.

## 7. User Feedback Summary

- **Deployment robustness is a top concern.** Two of three open issues (#3359, #3354) are setup-time failures on clean installs, particularly in non-interactive or newer-runtime environments. Users are installing on fresh macOS arm64 boxes and headless servers.
- **Delivery correctness matters.** Issue #3353 highlights that users rely on accurate delivery status for SMS retries and owner notifications — a silent misclassification erodes trust in the Dial channel.
- **Channel expansion demand is clear.** The sustained interest in Dial (#3041 open since Jul 14), Cursor (#3355 today), and Telegram groups (#3351) shows users want NanoClaw to bridge more communication surfaces, not just Slack/Discord/Telegram DMs.
- **Security-conscious deployment.** The merged fix #3339 (fail-closed on unverifiable credentials) and #3342 (decline unknown-member channel invites) indicate the community values strict identity and access boundaries.

## 8. Backlog Watch

| Item | Age | Risk | Note |
|------|-----|------|------|
| [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) — Dial channel adapter | ~37 days | Medium | Core feature, open but progressing. |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) — Dial in channel picker/wizard | ~37 days | Medium | Blocked on or coupled with #3041. |
| [#3359](https://github.com/nanocoai/nanoclaw/issues/3359) — Node 26 / better-sqlite3 | ~1 day | High | Fix PRs exist but not yet merged; blocks new-env installs. |
| [#3354](https://github.com/nanocoai/nanoclaw/issues/3354) — Setup non-login shell bugs | ~1 day | Medium | No fix PR; affects server/container users. |
| [#3353](https://github.com/nanocoai/nanoclaw/issues/3353) — Dial SMS false-delivered | ~1 day | High | No fix PR; undermines Dial channel reliability. |
| [#3362](https://github.com/nanocoai/nanoclaw/pull/3362) — Slack agent flow validation | ~1 day | Low | Open PR, likely close to merge. |

**Overall health:** Active and healthy. The core team shipped 11 merged/closed PRs in one day across Slack agents, Telegram groups, provisioning hardening, and runtime upgrades. Two high-severity bugs (Dial false-delivery, Node 26 compat) lack merged fixes and should be tracked closely. The project is clearly expanding its channel and provider surface while hardening installation and provisioning paths.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-20

## 1. Today's Overview

NullClaw remains a low-activity project as of 2026-08-20, with zero issues and no new releases in the past 24 hours. The sole observed activity is a single open pull request (#989) addressing a broken star history chart in the README. No merged or closed items were recorded, indicating a quiet maintenance cycle. Community engagement appears minimal, with no comments or reactions on the active PR. The project seems to be in a stable but passive phase, with no urgent blockers or momentum-building contributions.

## 2. Releases

No new releases were published today. The project has not issued a version update recently.

## 3. Project Progress

**No merged or closed PRs today.** The one active pull request remains open and unmerged:

- [#989 — fix: restore broken star history chart](https://github.com/nullclaw/nullclaw/pull/989) by **FaintFlower** (created 2026-08-19). This PR redirects the README's star history chart from the restricted GitHub stargazer API to the token-free alternative at `star-history.dera.page`, restoring visual accuracy. No other features or fixes advanced today.

## 4. Community Hot Topics

- [#989 — fix: restore broken star history chart](https://github.com/nullclaw/nullclaw/pull/989) — The only active item. While the PR itself has zero reactions and no comments, the underlying issue is notable: the original chart dependency on GitHub's stargazer API is a known fragility, as that API imposes access restrictions that can break visual displays. This suggests users or contributors value transparent, verifiable project metrics in documentation, even if engagement on the fix is currently low.

## 5. Bugs & Stability

**No bugs or regressions reported today.** The one relevant item is a cosmetic/documentation issue rather than a functional bug:

- **Broken star history chart** (PR #989) — Non-critical; affects README rendering only, not core functionality. A fix PR is already open.

## 6. Feature Requests & Roadmap Signals

**No feature requests surfaced today.** The absence of new issues or enhancement proposals is consistent with the project's current low-activity state. No roadmap signals can be inferred from today's data.

## 7. User Feedback Summary

**No user feedback collected today.** The lack of comments, reactions, and issues indicates either a small or inactive user base, or a period of quiet usage. No pain points or satisfaction indicators were observable in the 24-hour window.

## 8. Backlog Watch

- **[PR #989](https://github.com/nullclaw/nullclaw/pull/989)** — Open since 2026-08-19 with no maintainer review or merge activity. While low-severity, left unmerged the README will continue to display a broken chart, which may affect first-impression credibility for new visitors. Worth a maintainer look at the next opportunity.

---

**Overall Health Assessment:** NullClaw is in a low-activity maintenance phase. No critical issues, no releases, and minimal community engagement were observed. The single open PR is a reasonable housekeeping fix. No immediate risks are apparent.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-20

## 1. Today's Overview

IronClaw shows strong development velocity on 2026-08-20, with **15 issues** and **38 PRs** updated in the last 24 hours. The project is in a post-release stabilization phase following the **v1.3.0** promotion from rc.2. Active work spans three major tracks: persistent per-user sandboxing, a durable notification inbox, and onboarding (OOBE) improvements. CI stability has been a concern with unbounded `apt-get` operations causing merge-queue stalls, now addressed in PR #7756. Overall project health is positive—high PR throughput, active bug-bash cycles, and ongoing epic-driven feature development.

---

## 2. Releases

### ironclaw-v1.3.0 (2026-08-19)

Stable promotion of `1.3.0-rc.2`. Key fix:

- **Upgrades from 1.2 now preserve the `activation_state` extension field** instead of crash-looping during startup.

**Breaking changes / migration notes:** None announced beyond the rc.2 fixes. Upgraders from 1.2 should verify extension activation state is preserved post-upgrade.

---

## 3. Project Progress

### Merged / Closed PRs

| PR | Title | Author |
|----|-------|--------|
| [#7754](https://github.com/nearai/ironclaw/pull/7754) | chore(release): promote 1.3.0-rc.2 to 1.3.0 | henrypark133 |
| [#7752](https://github.com/nearai/ironclaw/pull/7752) | feat(turns): subagent activation provenance, activate() primitive, and derived autonomous-wake cap (slice 1) | henrypark133 |
| [#7756](https://github.com/nearai/ironclaw/pull/7756) | fix(ci): bound every unbounded CI operation — apt hangs, uncapped jobs, external downloads | henrypark133 |
| [#7697](https://github.com/nearai/ironclaw/pull/7697) | feat(notifications): add a durable user inbox and product APIs | italic-jinxin |
| [#6994](https://github.com/nearai/ironclaw/pull/6994) | feat(webui): OOBE automation-tasks prototype — carousel, inline cards, agent-mode pill | rdisandro |
| [#7686](https://github.com/nearai/ironclaw/pull/7686) | refactor(runtime): centralize capability outcome processing | henrypark133 |
| [#7491](https://github.com/nearai/ironclaw/pull/7491) | feat(coding): omp core-tool contract + engines + benchmark arm (slices 1-4) | serrrfirat |

### Key Advances

- **Capability-response normalization** (stack #7627) reached a milestone with PRs #7686 → #7692 → #7711 landing or in progress, centralizing how provider rejections and auth failures surface to models.
- **Notification infrastructure** moved from automation-only to a durable, server-backed inbox with lifecycle states (unread/read/resolved/archived) via #7697, with PR #7698 generalizing the WebUI notification center.
- **CI reliability** was critically addressed in #7756 after 69 cancelled runs and 1,193 stalled jobs were traced to unbounded `apt-get` operations.
- **Subagent activation provenance** (#7752) laid groundwork for autonomous subagent wake behavior without production behavior changes yet.
- **Coding tool contract cleanup** (#7491) consolidated six bare tool names (`read`, `write`, `edit`, `glob`, `grep`, `bash`) and removed legacy mixed-surface tools.

---

## 4. Community Hot Topics

| Issue/PR | Title | Comments | Activity |
|----------|-------|----------|----------|
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | Epic: Persistent per-user sandbox with iron-proxy; defer loop executors | 7 | Open, v1.4.0 |
| [#7692](https://github.com/nearai/ironclaw/pull/7692) | fix(extensions): normalize provider failures and auth diagnostics | — | Open, XL |
| [#7698](https://github.com/nearai/ironclaw/pull/7698) | feat(webui): generalize the notification center | — | Open, XL |
| [#6994](https://github.com/nearai/ironclaw/pull/6994) | OOBE automation-tasks prototype | — | Closed |
| [#7044](https://github.com/nearai/ironclaw/issues/7044) | Epic: Onboarding to channel-first approach | 0 | Closed |
| [#5998](https://github.com/nearai/ironclaw/issues/5998) | Reborn has no transport for a local MCP server | 1 | Open |

**Analysis:** The persistent sandbox epic (#7732) is the most-discussed open issue and represents a foundational architecture shift—from ephemeral per-command containers to a reusable per-(tenant, user) container with Docker Exec. The local MCP transport blockage (#5998) has been open since July 11 with low engagement, suggesting a gap between user need and maintainer visibility. The notification inbox work (#7697/#7698) is actively being built out, indicating the team is prioritizing product-level UX infrastructure.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Title | Fix Status |
|----------|----------|-------|------------|
| **P1** | [#7748](https://github.com/nearai/ironclaw/issues/7748) | IronClaw got confused and stopped working | No fix PR yet |
| **P2** | [#7745](https://github.com/nearai/ironclaw/issues/7745) | Copilot MCP extension install fails with auth_required, duplicate catalog entries, unclear token type | No fix PR yet |
| **P3** | [#7744](https://github.com/nearai/ironclaw/issues/7744) | Cron job UI missing edit and test buttons | No fix PR yet |
| — | #7753 | fix(capabilities): preserve terminal dispatch records | Merged — fixes dispatch-failure state loss |
| — | #7756 | fix(ci): bound every unbounded CI operation | Merged — resolves merge-queue stall pattern |

**Notable:** The "got confused and stopped working" bug (#7748) is vague but reported by a real user via Slack feedback and remains unassigned. The cron UI missing buttons (#7744) and Copilot MCP install issues (#7745) are both from QA bug-bash cycles on the Railway instance. The dispatch-record fix (#7753) addresses a durability gap where terminal dispatch records were discarded before outcome layer could materialize `Failed` edges.

---

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Title | Scope |
|----------|-------|-------|
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | Persistent per-user sandbox with iron-proxy | v1.4.0 epic |
| [#7742](https://github.com/nearai/ironclaw/issues/7742) | Automation creation preflight & missing prerequisites | v1.3.0 suggested |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) | Storybook + AI-first Design System | WebUI epic |
| [#7757](https://github.com/nearai/ironclaw/pull/7757) | Allow hosted MCP server on literal loopback IP | Open PR |
| [#7688](https://github.com/nearai/ironclaw/issues/7688) | Durable notification inbox contracts & ProductSurface APIs | Closed |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) | Operator surface for IronHub agent link | Open PR |

**Prediction for v1.4.0:** The persistent sandbox (#7732, Step 1 in #7751) and the onboarding channel-first approach (#7044, now closed) will likely ship. The notification inbox is fully implemented and should be available. The design system integration (#7750, #7038) is in Phase 1 and may be partial. The loopback MCP fix (#7757) is a small, low-risk PR likely to land soon.

---

## 7. User Feedback Summary

| Source | Feedback | Theme |
|--------|----------|-------|
| Slack #x-ai-product-feedback (bianca.guimaraes-chadwick) | "It just got confused and stopped working" (#7748) | Reliability / stability concern |
| QA Bug Bash (Railway instance) | Copilot MCP extension install: duplicate catalog entries, auth_required errors, unclear token type (#7745) | Onboarding friction, unclear auth flows |
| QA Bug Bash (Railway instance) | Cron job UI missing edit/test buttons (#7744) | Feature discoverability gap |
| Issue #5998 | Local MCP server unreachable — stdio rejected, loopback HTTP denied | Developer workflow limitation |
| Issue #7681 | Slack unlinked-user connect message is public | Privacy concern in shared channels | **Closed** |

**Satisfaction signals:** The public Slack connect-message issue (#7681) was resolved, showing responsiveness. However, the vague "confused and stopped working" report (#7748) and the persistent local MCP transport block (#5998, open since July 11) suggest gaps in both reliability observability and developer-oriented feature coverage.

---

## 8. Backlog Watch

| Issue | Title | Open Since | Risk |
|-------|-------|------------|------|
| [#5998](https://github.com/nearai/ironclaw/issues/5998) | Reborn has no transport for a local MCP server | 2026-07-11 (~40 days) | High — blocks a clear use case; PR #7757 exists but is unmerged |
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | Persistent per-user sandbox epic | 2026-08-18 | Medium — active work in #7751, but full epic is v1.4.0 |
| [#7748](https://github.com/nearai/ironclaw/issues/7748) | IronClaw got confused and stopped working | 2026-08-19 | Medium — vague but signals a real user-facing failure mode |
| [#7745](https://github.com/nearai/ironclaw/issues/7745) | Copilot MCP extension install fails | 2026-08-19 | Medium — QA-identified, multiple sub-issues |
| [#7744](https://github.com/nearai/ironclaw/issues/7744) | Cron job UI missing edit and test buttons | 2026-08-19 | Low — missing UI affordances, not a crash |
| [#7603](https://github.com/nearai/ironclaw/issues/7603) | Batch BeforeModel checkpoints per-N iterations | 2026-08-13 | Low — **Closed**; Tier 3 optimization (~14 rows/turn saved) |
| [#7602](https://github.com/nearai/ironclaw/issues/7602) | Cache the lease-fence token | 2026-08-13 | Low — **Closed**; Tier 2 read-pressure optimization |

**Maintainer attention needed:** #5998 is the longest-open item and has a directly relevant PR (#7757) that should be prioritized for review. #7748 needs triage to convert a vague user report into an actionable bug. The two closed optimization issues (#7603, #7602) from the checkpoint epic (#7591) suggest the remaining tiers are either deferred or handled elsewhere.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-20

## 1. Today's Overview

LobsterAI showed **high merge throughput** today with 8 PRs closed (all merged), while no new issues were opened and no releases were published. All 6 open issues were marked stale (last updated 2026-08-19), suggesting they have seen recent activity but remain unresolved. The project's active development momentum is strong on the contributor side, though issue resolution appears to lag behind PR turnover. No breaking changes or new releases were reported today.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**8 PRs merged/closed today:**

| PR | Area | Summary |
|----|------|---------|
| [#2512](https://github.com/netease-youdao/LobsterAI/pull/2512) | Windows Installer | Hide plugin-owned silent banner only for dictbind double-click-silent channel artifacts |
| [#2511](https://github.com/netease-youdao/LobsterAI/pull/2511) | Windows Installer | Support silent upload-first web builds with two-pass NOS-hosted payload flow |
| [#1570](https://github.com/netease-youdao/LobsterAI/pull/1570) | Scheduled Tasks | Fix bug where editing a disabled task incorrectly re-enabled it |
| [#1573](https://github.com/netease-youdao/LobsterAI/pull/1573) | IM Channels | Add slash-command support (`/help`, `/status`, `/new`, `/compact`) for Telegram/DingTalk/Feishu/Discord/QQ/WeChat |
| [#1576](https://github.com/netease-youdao/LobsterAI/pull/1576) | API / SSE | Fix race condition where old abort callbacks incorrectly cleared SSE listeners for new requests |
| [#1578](https://github.com/netease-youdao/LobsterAI/pull/1578) | UX / Permissions | Add Bash syntax highlighting to the permission approval modal for safer command review |
| [#1580](https://github.com/netease-youdao/LobsterAI/pull/1580) | UX / Input | Replace image attachment icon with 64×64 thumbnail preview in the prompt input box |
| [#1582](https://github.com/netease-youdao/LobsterAI/pull/1582) | Windows / pip | Fix pip malfunction caused by stale `__main__.py` not being overwritten during upgrades |

Key advances: **IM slash-command support** (PR #1573) is a significant feature addition expanding agent control from desktop to messaging platforms. **SSE race-condition fix** (PR #1576) addresses a critical streaming reliability issue. **Installer improvements** (PRs #2511, #2512) strengthen the Windows silent-install pipeline.

## 4. Community Hot Topics

| Issue | Title | Comments | Last Updated | Link |
|-------|-------|----------|--------------|------|
| #1569 | No response after提问, no output displayed | 5 | 2026-08-19 | [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) |
| #1561 | Model cannot access uploaded files | 2 | 2026-08-19 | [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) |
| #1566 | All inputs produce identical responses | 2 | 2026-08-19 | [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) |
| #1551 | Gateway restarts repeatedly after network changes | 1 | 2026-08-19 | [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) |
| #1563 | Typo in data package terms of service | 1 | 2026-08-19 | [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) |
| #1567 | Request quick-action buttons (stop, compact context) | 1 | 2026-08-19 | [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) |

**Analysis:** Issues #1569 and #1566 both describe core response-generation failures — the most damaging user-facing bugs. Issue #1561 (file upload not visible to model) and #1567 (request for quick-control buttons) reflect a need for **better file-handling reliability** and **user recoverability** during long contexts or hangs. The gateway restart issue (#1551) indicates a **deployment stability concern** in dynamic network environments.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| 🔴 High | [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | All inputs return identical responses (regression in v2026.4.3) | Open / no fix yet |
| 🔴 High | [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) | No response or output after user input | Open / no fix yet |
| 🟡 Medium | [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) | Uploaded files invisible to model (regression) | Open / no fix yet |
| 🟡 Medium | [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) | Gateway restart loop on network change | Open / no fix yet |
| 🟢 Low | [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) | Text errors in data package terms of service | Open / no fix yet |

**Already-fixed bugs today:**
- [#1570](https://github.com/netease-youdao/LobsterAI/pull/1570) — Scheduled task edit re-enabling bug ✅ Merged
- [#1576](https://github.com/netease-youdao/LobsterAI/pull/1576) — SSE listener race condition ✅ Merged
- [#1582](https://github.com/netease-youdao/LobsterAI/pull/1582) — Stale pip `__main__.py` on upgrade ✅ Merged

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood for Next Release |
|-------|---------|----------------------------|
| [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | Quick-action buttons in input box (stop conversation, compact context, help command) | **High** — aligns with IM slash-command feature already merged; desktop UX parity is a natural extension |
| [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) | Fix typos in service terms page | **High** — trivial fix, low risk |

The IM slash-command feature (PR #1573) signals a roadmap direction toward **cross-platform agent control** beyond the desktop client.

## 7. User Feedback Summary

**Pain points:**
- Core response generation is broken in at least two distinct ways (#1566, #1569), causing silent failures with no user feedback — the most damaging issue type.
- File upload regression (#1561) breaks a key multi-modal workflow; users note this worked in prior versions.
- No recovery mechanism when conversations hang or context overflows (#1567).
- Gateway instability under changing network conditions (#1551) affects production deployments.

**Satisfaction signals:**
- Users appreciate the new IM slash-command capability and syntax-highlighted permission modals.
- Thumbnail previews for image uploads (#1580) directly address a usability gap.

## 8. Backlog Watch

The following stale issues have been open since **2026-04-08** with no maintainer resolution in over four months and warrant attention:

| Issue | Title | Comments | Priority |
|-------|-------|----------|----------|
| [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) | No response/output after提问 | 5 | 🔴 Critical — core functionality broken |
| [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | All inputs return identical responses | 2 | 🔴 Critical — regression with log attachment |
| [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) | Model cannot access uploaded files | 2 | 🟡 High — file upload regression |
| [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) | Gateway restart loop on network change | 1 | 🟡 Medium — deployment stability |
| [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | Quick-action buttons for recovery | 1 | 🟢 Low — feature request |
| [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) | Typos in service terms | 1 | 🟢 Low — documentation |

**Recommendation:** The two critical response-generation bugs (#1566, #1569) should be prioritized, as they represent a complete failure of the agent's core function for affected users. The file-upload regression (#1561) also deserves urgent attention given its impact on multi-modal workflows.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-20

---

## 1. Today's Overview

Moltis is showing strong development velocity with **4 issues resolved** and **9 PRs updated** in the last 24 hours, indicating an active maintenance sprint. All four closed issues were bug fixes, and six of nine PRs have been merged — a 67% merge rate that reflects healthy contributor momentum. A new release artifact (`20260818.10`) was published two days ago and is likely the target for today's fixes. The project is in a tight feedback loop: security-critical issues are being triaged and patched rapidly, with maintainer `penso` and contributor `vikng-dev` driving most of the activity.

---

## 2. Releases

**`20260818.10`** — Published 2026-08-18. No release notes were included in the available data. Today's merged PRs (particularly the security patch for CWE-306, Apple Container fixes, and GPT-5.6 Luna routing) would likely be included in the next patch release. No breaking changes are indicated by today's activity.

---

## 3. Project Progress

**Merged / Closed PRs (6):**

| PR | Author | Summary |
|---|---|---|
| [#1217](https://github.com/moltis-org/moltis/pull/1217) | vikng-dev | WhatsApp: treat a reply to the bot as addressing it (fixes group chat mention handling) |
| [#1216](https://github.com/moltis-org/moltis/pull/1216) | penso | HTTPD: require authentication for vault unlock and recovery (CWE-306 fix) |
| [#1215](https://github.com/moltis-org/moltis/pull/1215) | penso | Apple Container: pass configured sandbox resource limits (`--memory`, `--cpus`, `pids_max`) |
| [#1213](https://github.com/moltis-org/moltis/pull/1213) | penso | Add GPT-5.6 Luna routing coverage to Responses test suite |
| [#1212](https://github.com/moltis-org/moltis/pull/1212) | penso | Preserve Responses routing for explicit OpenAI endpoints (URL-normalization fix) |
| [#1214](https://github.com/moltis-org/moltis/pull/1214) | penso | Apple Container: typed status decoder supporting both pre-1.x and 1.x JSON shapes |

**Open PRs under review (3):**

- [#1219](https://github.com/moltis-org/moltis/pull/1219) — `fix(channels): make the untrusted-turn tool ceiling configurable` (vikng-dev)
- [#1218](https://github.com/moltis-org/moltis/pull/1218) — `fix(whatsapp): stop hardcoding the push name to "Moltis"` (vikng-dev)
- [#1208](https://github.com/moltis-org/moltis/pull/1208) — `fix(cron): honor heartbeat active hours when the scheduler fires` (Lstarsky0)

---

## 4. Community Hot Topics

**Most discussed / reacted issues:**

1. **[Issue #1177](https://github.com/moltis-org/moltis/issues/1177)** — *Vault Unlock/Recovery Endpoints Missing Authentication (CWE-306)*
   - Created 2026-07-30, closed 2026-08-20 via PR #1216.
   - **Underlying need:** Users running Moltis with exposed HTTP APIs need assurance that vault credentials (used for model provider auth) cannot be brute-forced by unauthenticated remote callers. This is a trust-boundary issue for self-hosted deployments.

2. **[Issue #1185](https://github.com/moltis-org/moltis/issues/1185)** — *Apple Container 1.x sandbox starts but Moltis treats it as not running*
   - Created 2026-08-08, closed 2026-08-19 via PR #1214.
   - **Underlying need:** Apple Container 1.x changed its status JSON schema (nested `status.state` vs. scalar `status`), breaking Moltis's readiness probe. Users relying on Apple Container sandboxes for isolated tool execution need reliable lifecycle detection.

3. **[Issue #1181](https://github.com/moltis-org/moltis/issues/1181)** — *Issue with GPT 5.6 Luna*
   - Created 2026-07-31, closed 2026-08-19 via PRs #1212 and #1213.
   - **Underlying need:** OpenAI's GPT-5.6 Luna requires correct Responses API routing (reasoning + function tools). Users with custom `OPENAI_BASE_URL` configs or explicit endpoint overrides were losing this routing, causing silent fallback to incompatible API paths.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| **🔴 Critical** | [#1177](https://github.com/moltis-org/moltis/issues/1177) | Vault unlock/recovery endpoints had no authentication, allowing brute-force access to model provider credentials (CWE-306) | [#1216](https://github.com/moltis-org/moltis/pull/1216) ✅ Merged |
| **🟠 High** | [#1185](https://github.com/moltis-org/moltis/issues/1185) | Apple Container 1.x status parsing failure — sandbox runs but Moltis reports it as not running | [#1214](https://github.com/moltis-org/moltis/pull/1214) ✅ Merged |
| **🟠 High** | [#1188](https://github.com/moltis-org/moltis/issues/1188) | Sandbox resource limits (memory, CPU, pids) not passed to Apple Container | [#1215](https://github.com/moltis-org/moltis/pull/1215) ✅ Merged |
| **🟡 Medium** | [#1181](https://github.com/moltis-org/moltis/issues/1181) | GPT-5.6 Luna routing broken for explicit/custom OpenAI endpoints | [#1212](https://github.com/moltis-org/moltis/pull/1212) ✅ Merged; [#1213](https://github.com/moltis-org/moltis/pull/1213) ✅ Merged |

All four reported bugs have been resolved. No open regression reports remain. The project's bug-to-fix ratio today is **1:1**, which is strong.

---

## 6. Feature Requests & Roadmap Signals

- **[PR #1219](https://github.com/moltis-org/moltis/pull/1219)** — *Configurable untrusted-turn tool ceiling*: Extends the hardened tool policy from PR #1170 with a configuration knob, suggesting the community wants more granular control over tool access in shared/sharable chat contexts. Likely to land in the next release.
- **[PR #1208](https://github.com/moltis-org/moltis/pull/1208)** — *Heartbeat active hours honored by scheduler*: A long-standing dead-code issue (`is_within_active_hours` was implemented but never called). Closing this PR would restore documented behavior — a quiet but meaningful quality fix.
- **WhatsApp push-name fix [#1218](https://github.com/moltis-org/moltis/pull/1218)**: Addresses a UX frustration where bots display as "Moltis" instead of their configured name in groups. Suggests growing adoption in WhatsApp group contexts.

**Prediction:** The next release will likely include all three open PRs plus the merged batch above, with emphasis on Apple Container reliability and WhatsApp UX corrections.

---

## 7. User Feedback Summary

| Theme | Signal | Sentiment |
|---|---|---|
| **Security trust** | CWE-306 on vault endpoints drew a responsible disclosure-style report | ⚠️ Dissatisfaction — but rapid fix (21 days) is positive |
| **Apple Container reliability** | Two independent bugs (status parsing + resource limits) from the same backend user (`holgzn`, `penso`) | ⚠️ Frustration with sandbox maturity; maintainer is responsive |
| **OpenAI model coverage** | GPT-5.6 Luna routing regression affects users on custom endpoints | ⚠️ Pain point for enterprise/custom-deploy users; fixed promptly |
| **WhatsApp UX** | Hardcoded bot name and missed replies in groups | 😐 Mild annoyance — low-stakes but affects daily usability |
| **Tool policy flexibility** | Request for configurable ceiling on untrusted-turn tool restrictions | ➕ Constructive — users want more control, not less security |

Overall sentiment: **Cautiously positive.** The project is catching real security and reliability issues quickly. The maintainers are close to the codebase and merging fixes within days.

---

## 8. Backlog Watch

| Item | Age | Risk | Notes |
|---|---|---|---|
| [#1219](https://github.com/moltis-org/moltis/pull/1219) — Configurable untrusted-turn tool ceiling | 1 day | Low | Awaiting review; no blockers apparent |
| [#1218](https://github.com/moltis-org/moltis/pull/1218) — WhatsApp hardcoded push name | 1 day | Low | Straightforward fix, awaiting review |
| [#1208](https://github.com/moltis-org/moltis/pull/1208) — Heartbeat active hours | 3 days | Medium | Open longer than the others; may need maintainer nudge |

No long-standing unanswered issues remain — the current open backlog is small and consists entirely of PRs in review. The project is in a healthy state with no backlog accumulation.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-20

---

## 1. Today's Overview

CoPaw (QwenPaw) remains in a high-activity maintenance phase with 50 issues and 46 PRs touched in the last 24 hours. No new releases were published today. The project shows strong contributor momentum: 16 PRs were merged or closed, including several significant bug fixes and feature additions. Five issues remain open and active, two of which are user-facing bugs (a 10-minute freeze and an SSE automation gap). The overall project health is robust — a healthy open-to-closed ratio, active PR reviews, and rapid response to critical stability issues.

---

## 2. Releases

**No new releases today.** The latest stable version referenced in issues is **QwenPaw Desktop 2.1.0**.

---

## 3. Project Progress

### Merged / Closed PRs (today)

| PR | Type | Summary |
|---|---|---|
| [#6986](https://github.com/agentscope-ai/CoPaw/pull/6986) | Bug fix | **Sandbox: fix antivirus software blocking issues** — addresses frequent false-positive kills by AV software during agent execution |
| [#6800](https://github.com/agentscope-ai/CoPaw/pull/6800) | Feature | **Mailbox: intelligent email management assistant** — real-time monitoring, triage, and response across multiple providers |
| [#7103](https://github.com/agentscope-ai/CoPaw/pull/7103) | Test | **Expanded integration test coverage** — routing, channels (DingTalk, Feishu, QQ, Telegram, WeCom, etc.), MCP, and coding-project modules |
| [#7151](https://github.com/agentscope-ai/CoPaw/pull/7151) | Feature | **Console: add folder creation to directory browser** — backend endpoint + inline FolderPlus flow |
| [#7137](https://github.com/agentscope-ai/CoPaw/pull/7137) | UX | **Console: polish model selector styles** |

### Key Open PRs in Review

| PR | Description |
|---|---|
| [#7150](https://github.com/agentscope-ai/CoPaw/pull/7150) | **Stalled LLM stream recovery** — detects and recovers from frozen inference streams (fixes #7102) |
| [#7146](https://github.com/agentscope-ai/CoPaw/pull/7146) | **view_image: freeze remote images** — prevents remote image URLs from breaking subsequent turns via SSRF protection and bounded downloads |
| [#7112](https://github.com/agentscope-ai/CoPaw/pull/7112) | **QwenPaw Hub** — self-hosted multi-user control plane with local and Docker runtimes |
| [#6515](https://github.com/agentscope-ai/CoPaw/pull/6515) | **Volcengine Agent Plan & MiMo V2.5 providers** — new provider catalog entries |
| [#6936](https://github.com/agentscope-ai/CoPaw/pull/6936) | **Tool arg type coercion** — fixes JSON schema validation failures when models emit unquoted numbers for string fields |
| [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) | **Session-scoped multi-project directories** — binds chats to ordered directory lists with primary cwd resolution |
| [#7037](https://github.com/agentscope-ai/CoPaw/pull/7037) | **Computer use: observe related window surfaces** — tracks up to 3 additional windows beyond the top-level target |

---

## 4. Community Hot Topics

### Most Discussed Open Issues

1. **[Issue #7102](https://github.com/agentscope-ai/CoPaw/issues/7102)** — *Freeze more than 10 minutes long* (9 comments, OPEN)
   User reports the app freezing for over 5–10 minutes when running GLM 5.3, with no token output and no thinking progress. **PR #7150 is already addressing this** with a semantic stream watchdog. High visibility bug affecting model reliability perception.

2. **[Issue #7013](https://github.com/agentscope-ai/CoPaw/issues/7013)** — *Unified tool panel, web preview & interactive terminal for Chat* (2 comments, OPEN)
   Feature request for a consolidated "workbench" in the Chat page covering file previews, diff views, local web service preview, and an interactive web terminal. Signals strong demand for a complete Agent development workflow within the console.

### Most Discussed Closed Issues (ongoing community interest)

3. **[Issue #2884](https://github.com/agentscope-ai/CoPaw/issues/2884)** — *User directory wiped after CoPaw usage on Ubuntu 22.04* (27 comments, CLOSED)
   The highest-comment issue in the dataset. A user reported their home directory and CoPaw installation being清空 (cleared). While closed, the 27-comment thread indicates ongoing community concern about data safety and potential security vulnerabilities. **Related fix: PR #6986** (AV blocking) touches on system-level safety.

4. **[Issue #2301](https://github.com/agentscope-ai/CoPaw/issues/2301)** — *Comprehensive feature suggestions* (10 comments, CLOSED, 1 👍)
   Requests one-click update, approve-button UI, auto model-switching with leaderboards, self-reflection/evolution, cross-platform sync (browser ↔ mobile), and additional model providers (Zhipu, Meituan). Reflects power-user desires for automation and polish.

5. **[Issue #2035](https://github.com/agentscope-ai/CoPaw/issues/2035)** — *Multi-agent bot binding and collaboration* (10 comments, CLOSED)
   Users want each agent bound to a separate Bot instance and true multi-agent collaborative task execution. PR [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) (multi-project directories) partially addresses multi-task isolation needs.

---

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Status |
|---|---|---|---|
| **High** | [#7102](https://github.com/agentscope-ai/CoPaw/issues/7102) — LLM stream freeze >10 min | [#7150](https://github.com/agentscope-ai/CoPaw/pull/7150) | PR open, under review |
| **High** | [#6847](https://github.com/agentscope-ai/CoPaw/issues/6847) — AV software kills CoPaw process | [#6986](https://github.com/agentscope-ai/CoPaw/pull/6986) | **Merged** ✅ |
| **Medium** | [#7034](https://github.com/agentscope-ai/CoPaw/issues/7034) — TypeError in ReactAgent async tool calls | — | Closed, no linked fix PR visible |
| **Medium** | [#6624](https://github.com/agentscope-ai/CoPaw/issues/6624) — Auto-compact not triggering memory flow | — | Closed, needs maintainer triage |
| **Medium** | [#2377](https://github.com/agentscope-ai/CoPaw/issues/2377) — Tasks randomly interrupted despite batching | — | Closed, unresolved root cause |
| **Low** | [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) — LLM config 404 error in QwenPaw Creator 2.1.0 | — | Closed |
| **Low** | [#3177](https://github.com/agentscope-ai/CoPaw/issues/3177) — Windows CLI startup failure (encoding issue) | — | Closed |

**Notable:** The stalled-stream freeze (#7102) is the most impactful open bug. PR #7150 adds a semantic stream watchdog that should resolve it. The AV-killing issue (#6847 → #6986) has been merged, which should significantly improve Windows user experience.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood |
|---|---|---|
| **Self-hosted multi-user Hub** | [#7112](https://github.com/agentscope-ai/CoPaw/pull/7112) | **High** — PR is well-scoped and open for review |
| **Unified tool panel + web terminal in Chat** | [#7013](https://github.com/agentscope-ai/CoPaw/issues/7013) | **Medium** — aligns with power-user trend; no PR yet |
| **Multi-project directory per session** | [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) | **High** — PR in review, directly addresses multi-task workflows |
| **Reranker UI config panel** | [#6399](https://github.com/agentscope-ai/CoPaw/pull/6399) | **High** — complements existing reranker backend |
| **Volcengine / MiMo V2.5 provider support** | [#6515](https://github.com/agentscope-ai/CoPaw/pull/6515) | **High** — PR in review, catalog-driven architecture |
| **Structured SSE run outcomes for API automation** | [#5930](https://github.com/agentscope-ai/CoPaw/pull/5930) | **Medium** — niche but valuable for enterprise integrations |
| **Auto model fallback / leaderboards** | [#2301](https://github.com/agentscope-ai/CoPaw/issues/2301), [#2089](https://github.com/agentscope-ai/CoPaw/issues/2089) | **Low-Medium** — frequently requested but complex; no PR yet |
| **Browser use Apple Silicon native support** | [#2655](https://github.com/agentscope-ai/CoPaw/issues/2655) | **Medium** — closed, likely addressed in downstream Playwright update |
| **Email management assistant** | [#6800](https://github.com/agentscope-ai/CoPaw/pull/6800) | **High** — already merged ✅ |

**Prediction for next release:** Expect the Hub (multi-user), multi-project directories, reranker UI, Volcengine providers, and the AV-stability fix to land. The stalled-stream recovery (#7150) is also a strong candidate.

---

## 7. User Feedback Summary

**Pain points:**
- **Data safety anxiety** — Issue #2884 (27 comments) reflects deep concern about CoPaw potentially deleting user files. Even though closed, the community chatter indicates trust needs rebuilding.
- **AV false positives on Windows** — Issue #6847 was a recurring complaint; now addressed by merged PR #6986.
- **Stream freezes during long inference** — Issue #7102 and #2377 show users losing work during extended agent runs, especially with non-Qwen models (GLM).
- **Tool arg type mismatches** — Issue #6936 (now with a fix PR) highlights that model output format inconsistencies cause silent validation failures.
- **Mobile UI unusable** — Issue #2856 reported broken mobile browser layout; remains a UX gap.

**Satisfaction signals:**
- The merged **email management feature** (#6800) and **folder creation in directory browser** (#7151) show the team is responding to automation and workflow requests.
- Integration test expansion (#7103) and the AV fix (#6986) indicate investment in stability.
- The community actively submits QA-tagged PRs (e.g., "狄仁杰·Repairer@QPQAT", "秦琼·CIOps@QPQAT"), suggesting a maturing contributor base.

---

## 8. Backlog Watch

| Issue/PR | Age | Why It Needs Attention |
|---|---|---|
| [#2884](https://github.com/agentscope-ai/CoPaw/issues/2884) — Home directory wiped | ~4.5 months | 27 comments, highest engagement. Even closed, the underlying trust issue needs a public post-mortem or safety guarantee. |
| [#2301](https://github.com/agentscope-ai/CoPaw/issues/2301) — Comprehensive feature suggestions | ~5 months | 10 comments, 1 👍. Covers update mechanism, auto model-switching, cross-platform sync. No PRs spawned yet. |
| [#2035](https://github.com/agentscope-ai/CoPaw/issues/2035) — Multi-agent bot binding | ~5 months | 10 comments. Core multi-agent workflow request with no visible progress. |
| [#6624](https://github.com/agentscope-ai/CoPaw/issues/6624) — Auto-compact not triggering memory | ~3 weeks | Closed but the bug (manual `/compact` works, automatic doesn't) may still affect users. Needs maintainer confirmation. |
| [#2377](https://github.com/agentscope-ai/CoPaw/issues/2377) — Tasks randomly interrupted | ~5 months | 9 comments. User set up batching + resume but agent still quits after a few files. Root cause unclear. |
| [#5930](https://github.com/agentscope-ai/CoPaw/pull/5930) — Structured SSE run outcomes | ~1.5 months | Open, no recent activity. Important for enterprise/API users but low visibility. |

---

*Digest generated from GitHub data retrieved on 2026-08-20. Project: [agentscope-ai/CoPaw](https://github.com/agentscope-ai/CoPaw).*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-20

## 1. Today's Overview

ZeroClaw is in a period of high developer velocity, with 44 issues and 50 PRs updated in the past 24 hours and zero new releases shipped. The project is navigating a major architectural transition—RFCs around session ownership, WASM plugin expansion, and SOP permission contracts are all actively discussed—while simultaneously burning down a significant Windows compatibility debt (74 test failures) and a Rust code-quality initiative (307 anti-slop candidates). No new releases landed today, but the merged/closed PR count (1) and the volume of open review work suggest the team is deep in pre-release polish. Overall health is strong: active maintainer engagement, clear RFC discipline, and a robust back-and-forth on security-critical paths.

## 2. Releases

**None.** The latest release remains v0.8.3 (from mid-July). Several deferred follow-ups from v0.8.4—including Windows symlink issues (#9381)—remain outstanding.

## 3. Project Progress

**Merged / Closed (past 24h):** 1 PR merged, 1 issue closed.

**Key PRs advancing today:**

- **#10122** — *perf(release): stop compiling release tools from source* — Replaces `cargo install cross` and `cargo install tauri-cli` builds with repository-owned pinned binaries, significantly reducing CI release-time build latency.
- **#10150** — *fix(zerocode): accept paste during active turns* — Fixes a UX regression where terminal pastes were silently discarded during active Chat turns; now pasted input queues properly.
- **#9853** — *chore(workspace): remove aardvark-sys and zeroclaw-robot-kit* — Dead-code removal; `zeroclaw-robot-kit` has zero reverse dependencies and `aardvark-sys` is only reachable through an optional feature.
- **#9937** — *fix(security): enforce forbidden_paths under allowed roots* — Critical security fix: path-policy checks previously short-circuited on workspace-root matches, bypassing `forbidden_paths` sub-trees entirely.
- **#9715** — *fix(infra): make JSONL session migration retry-safe* — Session migration now uses shared mutation locks and atomic SQLite transactions, preventing data corruption on retry.

## 4. Community Hot Topics

**Top issues by comment count (actively discussed):**

| Issue | Title | Comments | Link |
|---|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC: Runtime-owned conversation sessions and transport surface adapters | 20 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | Bug: 74 test failures on Windows | 18 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) |
| [#10118](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) | RFC: Rust anti-slop policy debt remediation | 16 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) | RFC: Prefer a lighter ZeroClaw core through external integrations | 16 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: Maintainer decision queue for RFCs and design issues | 13 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) | RFC: Treat empty WhatsApp Web `allowed_groups` as permit-none | 13 | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) |

**Analysis:** The community is most engaged around **architectural ownership boundaries** (session persistence, core vs. external integrations) and **Windows/platform parity**. The anti-slop RFC and WhatsApp security RFC signal that maintainers are prioritizing both code hygiene and security-correct defaults. The maintainers' decision tracker (#8692) having 13 comments indicates active governance discussions around RFC triage.

## 5. Bugs & Stability

**P0 (workflow blocked):**
- [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) — *SOP engine promotes and runs later steps before recording a step's output-schema rejection* — Steps execute out of order when schema validation fails. **No fix PR identified yet.**

**P1 (high severity):**
- [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — *74 test failures on Windows* — Unix-only test commands, path semantics, and console encoding (code page 936) break the Windows test suite. CI runs Linux-only, so this is invisible in CI.
- [#9290](https://github.com/zeroclaw-labs/zeroclaw/issues/9290) — *Windows desktop installer fails at launch with missing TaskDialogIndirect* — v0.8.3 installer crashes on launch; likely a manifest/SDK linkage issue.
- [#9976](https://github.com/zeroclaw-labs/zeroclaw/issues/9976) — *Stop logging Anthropic credential fragments* — Debug logging exposes partial API keys (`credential_head`/`credential_tail`). **Fix PR #9937** is open for a related security path; a targeted fix is needed here.

**P2 (medium):**
- [#10067](https://github.com/zeroclaw-labs/zeroclaw/issues/10067) — *tool-result truncation is a fixed 50,000 chars* — Re-scoped from a 1 MB crash report; now tracked as degraded behavior.
- [#10045](https://github.com/zeroclaw-labs/zeroclaw/issues/10045) — *Persisted image markers can retain temporary source paths and repeatedly warn* — Temp-file path leakage in `[IMAGE:...]` markers.
- [#10106](https://github.com/zeroclaw-labs/zeroclaw/issues/10106) — *Exact proxy selectors reject supported transcription services* — Proxy config mismatch for Groq, Deepgram, AssemblyAI, Google transcription providers.

## 6. Feature Requests & Roadmap Signals

| RFC / Feature | Description | Likelihood for Next Release |
|---|---|---|
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | Comprehensive WASM plugin architecture — hook/backend/capability layers for "everything is a plugin" | **High** — builds on existing WASM Component Model host; significant architectural lift |
| [#9702](https://github.com/zeroclaw-labs/zeroclaw/issues/9702) | Goal mode v2 — durable continuation and paired Web controls | **Medium** — needs session-persistence ownership resolved first (#9600) |
| [#9598](https://github.com/zeroclaw-labs/zeroclaw/issues/9598) | SOP capability permission contract | **Medium** — Rev 3 split into interim + full paths; targeted at v0.9.0 |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) | Prefer a lighter ZeroClaw core through external integrations | **Low-Medium** — long-term architectural shift, not a quick win |
| [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) | Support Option-Backspace word deletion in ZeroCode | **High** — small, accepted, P3; likely to land soon |
| [#10086](https://github.com/zeroclaw-labs/zeroclaw/issues/10086) | Make ZeroCode Logs text selectable and copyable | **High** — small UX improvement, accepted |
| [#8486](https://github.com/zeroclaw-labs/zeroclaw/issues/8486) | OpenAI chat completions endpoint | **Medium** — large PR (XL), blocked; critical for IDE/LLM tool interoperability |

## 7. User Feedback Summary

- **Session management frustration:** [#10141](https://github.com/zeroclaw-labs/zeroclaw/issues/10141) — Users find it difficult to manage and navigate previous sessions; copy/referencing snippets is clunky.
- **macOS input expectations:** [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) — macOS users expect Option-Backspace for word deletion; its absence is a friction point in ZeroCode.
- **Copyable logs:** [#10086](https://github.com/zeroclaw-labs/zeroclaw/issues/10086) — Users cannot select or copy text from the ZeroCode Logs pane, forcing a hidden `y`-key workflow.
- **Windows desktop broken:** [#9290](https://github.com/zeroclaw-labs/zeroclaw/issues/9290) — Windows users cannot launch the desktop app after installation; this is a hard blocker for that platform.
- **Privacy concern:** [#9976](https://github.com/zeroclaw-labs/zeroclaw/issues/9976) — Partial credential logging in debug mode is a trust issue for operators handling API keys.
- **Translation gaps:** [#1003](https://github.com/zeroclaw-labs/zeroclaw/issues/10103) — French and Spanish labels overflow fixed-width TUI columns, causing misalignment.

**Overall sentiment:** Users value the multi-session and SOP features but are frustrated by platform inconsistencies (Windows), missing basic UX affordances (copy/paste, word deletion), and privacy lapses (credential logging).

## 8. Backlog Watch

| Issue / PR | Reason for Attention |
|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — 74 Windows test failures | 70+ days open; CI gap means Windows regressions are undiscovered. Needs a Windows CI job. |
| [#9290](https://github.com/zeroclaw-labs/zeroclaw/issues/9290) — Windows desktop installer crash | Blocks all Windows desktop users; P1 severity. |
| [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) — SOP out-of-order step execution | P0; no fix PR yet. Workflow-blocking bug in the SOP engine. |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Session ownership RFC | 20+ comments, needs-maintainer-review; central to multiple workstreams (#9600, #9702). |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) — Session-persistence contract tracker | Four independent workstreams touch the same contract with no designated owner. |
| [#10118](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) — Rust anti-slop remediation | 307 candidates across 1,078 files; tracker created today but remediation is a large undertaking. |
| [#8486](https://github.com/zeroclaw-labs/zeroclaw/issues/8486) — OpenAI chat completions endpoint | Blocked XL PR; high community demand for LLM tool interoperability. |
| [#9318](https://github.com/zeroclaw-labs/zeroclaw/issues/9318) — PostgreSQL session backend CI | Blocked; session backend lacks integration test coverage against a real PostgreSQL instance. |
| [#10041](https://github.com/zeroclaw-labs/zeroclaw/issues/10041) — Isolate Blacksmith debugging from attesting CI | Needed to enable interactive debugging without compromising CI attestation guarantees. |

---

*Digest generated from GitHub data as of 2026-08-20. Project: [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*