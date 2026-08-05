# OpenClaw Ecosystem Digest 2026-08-05

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-05 03:13 UTC

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



# OpenClaw Project Digest — 2026-08-05

---

## 1. Today's Overview

OpenClaw remains in a high-velocity bug-fixing phase with **500 issues** and **500 PRs** updated in the last 24 hours (445 open/active issues, 376 open PRs). No new releases were published this period, suggesting the team is prioritizing stability fixes over shipping. The project's health is strained by multiple **P0/P1 session-state and message-loss bugs** that have persisted across versions; several are tagged `clawsweeper-recovery-stuck`, indicating automated triage has flagged them as blocked on maintainer action. Merge activity is heavy on channel adapters (Telegram, Discord, Slack, Feishu) and session delivery reliability, reflecting active hardening ahead of an anticipated release.

---

## 2. Releases

**None.** No new versions were published in this 24-hour window. The latest stable line remains **2026.7.1** / **2026.7.2-beta**, with multiple issues specifically referencing regressions introduced in 2026.7.x upgrades (see Issues #116277, #115326, #111498, #112395, #119263).

---

## 3. Project Progress

### Notable Merged/Closed Items (today or recently)
- **#116277 [CLOSED]** — DeepSeek v4 Flash silent reply failure (diamond-lobster severity, 104 comments). Likely resolved via the ongoing fixes to the `model-call-started` path.
- **#52249 [CLOSED]** — ACP parent session stuck after child completion (silver-shellfish). Root cause was identified in the parent-stream relay's transcript inspection logic.

### Active PRs Advancing Key Areas
| PR | Focus | Status |
|---|---|---|
| [#119374](https://github.com/openclaw/openclaw/pull/119374) | Defer optional xAI capability runtimes at startup | 📣 Needs proof |
| [#119169](https://github.com/openclaw/openclaw/pull/119169) | Fix `adapter_returned_no_identity` visibility classification | 📣 Needs proof |
| [#119221](https://github.com/openclaw/openclaw/pull/119221) | Reject transcript turns when session ID rotates mid-append | 📣 Needs proof |
| [#119371](https://github.com/openclaw/openclaw/pull/119371) | Retry delivery when outbound adapter is unavailable | ⏳ Waiting on author |
| [#119127](https://github.com/openclaw/openclaw/pull/119127) | Fix media TTL sweep deleting attached files from chat history (P0) | 📣 Needs proof |
| [#119449](https://github.com/openclaw/openclaw/pull/119449) | Refactor memory-wiki to reuse canonical plugin normalization | Open |
| [#119377](https://github.com/openclaw/openclaw/pull/119377) | Keep post-ready context cache warming responsive on large catalogs | ⏳ Waiting on author |
| [#119321](https://github.com/openclaw/openclaw/pull/119321) | macOS Talk realtime relay — native mic/playback lifecycle | ⏳ Waiting on author |
| [#116562](https://github.com/openclaw/openclaw/pull/116562) | Recover primary embedding provider after fallback activation | 📣 Needs proof |

---

## 4. Community Hot Topics

### Top Issues by Comment Count
1. **[#116277](https://github.com/openclaw/openclaw/issues/116277)** — *DeepSeek v4 Flash silent reply failure* (104 comments, now closed) — Users hit a "No reply was generated" fallback on Telegram group messages. High engagement indicates broad impact across the DeepSeek provider user base.
2. **[#116201](https://github.com/openclaw/openclaw/issues/116201)** — *Realtime voice unbounded state retention* (58 comments) — Resource leaks in voice sessions under bursty provider behavior. Diamond-lobster severity; maintainer + product-decision tags.
3. **[#115326](https://github.com/openclaw/openclaw/issues/115326)** — *Crash-loop breaker permanently suppresses Discord/WhatsApp* (25 comments, now closed) — Recovery via `channels.start` fails with WebSocket 1006.
4. **[#44925](https://github.com/openclaw/openclaw/issues/44925)** — *Subagent completion silently lost on timeout* (23 comments, 2 👍) — A cross-cutting orchestration bug affecting cron, subagent, and ACP flows.
5. **[#48788](https://github.com/openclaw/openclaw/issues/48788)** — *Centralized filename encoding for multi-encoding Content-Disposition* (20 comments, 1 👍) — Feishu Chinese filename handling expansion to a general utility.

### Underlying Needs
- **Message reliability** is the dominant user concern: issues #44925, #67777, #92433, #114690 all describe silent message loss in subagent/cron/Discord paths.
- **Session state integrity** under concurrent operations (resets, rotations, compaction) is a systemic weakness flagged across many top issues.
- **Provider diversity stress-testing** — DeepSeek, Poe media models, Google Antigravity, and Codex OAuth all surface distinct failure modes.

---

## 5. Bugs & Stability

### P0 / Critical
| Issue | Summary | Fix PR? |
|---|---|---|
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | DB v14→v15 migration fails — `no such column: entry_valid`; gateway refuses to start | None yet |
| [#112395](https://github.com/openclaw/openclaw/issues/112395) | Startup migration preflight blocks gateway after 6.11→7.1 upgrade; empty migration tables | None yet |
| [#118846](https://github.com/openclaw/openclaw/issues/118846) | Gateway main thread saturated at boot by plugin-metadata snapshot; RPC dies at ws_upgrade | None yet |
| [#119127](https://github.com/openclaw/openclaw/pull/119127) | Media TTL sweep deletes attachments still referenced in chat history (P0) | PR #119127 open |

### P1 High-Severity
| Issue | Summary | Fix PR? |
|---|---|---|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | Realtime voice sessions retain unbounded provider/consult state | None yet |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection livelocks under sustained writes, blocking main thread | None yet |
| [#117609](https://github.com/openclaw/openclaw/issues/117609) | Transient LLM/socket errors not retried at embedded-assistant stage | None yet |
| [#116116](https://github.com/openclaw/openclaw/issues/116116) | Anthropic `catalog.json` violates own schema; unguarded cost deref crashes all `openclaw models` CLI | None yet |
| [#115700](https://github.com/openclaw/openclaw/issues/115700) | `chat.send` rejected with "thread switched branches" after model completes — stale `expectedLeafEntryId` | None yet |
| [#116010](https://github.com/openclaw/openclaw/issues/116010) | All persistent sessions hard-capped at 128k context regardless of model or config | None yet |
| [#111498](https://github.com/openclaw/openclaw/issues/111498) | Main agent blocked by persistent workspace-state migration after Anthropic auth recovery | None yet |
| [#92433](https://github.com/openclaw/openclaw/issues/92433) | Subagent completion silently dropped when announce steers into requester run that ends early | None yet |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent completion delivery lost on direct-announce timeout/drain/orphan prune | None yet |

### P1 Medium
| Issue | Summary | Fix PR? |
|---|---|---|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Unreaped hook/tool child processes → zombie accumulation and runtime degradation | None yet |
| [#91363](https://github.com/openclaw/openclaw/issues/91363) | Isolated cron consistently fails with "LLM request failed" on model-call-started | None yet |
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | Codex OAuth refresh succeeds but cron/heartbeat fail with 10s auth refresh timeout | None yet |
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | Billing cooldown outlives provider outage; no probe-based recovery | None yet |
| [#75380](https://github.com/openclaw/openclaw/issues/75380) | `provider-payload.jsonl` and `cache-trace.jsonl` grow unbounded — no rotation policy | None yet |

### Regression (Confirmed)
- **#115326**, **#111498**, **#112395**, **#107873**, **#97616**, **#77733** — all tagged `regression` (worked before, now fails). The 6.x → 7.x upgrade path is particularly fragile.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood |
|---|---|---|
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | Self-hosted STT/TTS in webchat (bypass browser Speech API) | Medium — privacy-focused users |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | MathJax/LaTeX support in Control UI (10 👍) | Low-Medium — niche but vocal |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | YAML config file support | Low — JSON5 is established |
| [#44395](https://github.com/openclaw/openclaw/issues/44395) | Heading-aware chunking + entity extraction for memory search | Medium — directly improves RAG quality |
| [#9016](https://github.com/openclaw/openclaw/issues/9016) | Expose OpenRouter usage cost to agent runtime | Medium — cost transparency is frequently requested |
| [#79168](https://github.com/openclaw/openclaw/issues/79168) | Content-based prompt injection scanning on tool output | Medium-High — security surface is growing |
| [#71736](https://github.com/openclaw/openclaw/issues/71736) | Control UI plugin contribution slots (SDK surface) | High — maintainer-initiated RFC |
| [#46058](https://github.com/openclaw/openclaw/issues/46058) | Chat-first Android surface | Low — community fork, not direct upstream ask |

**Signal:** The strongest roadmap signals are **(1) memory/search quality improvements** (#44395), **(2) security hardening** (#79168, #95333), and **(3) platform SDK expansion** (#71736, #119321 for macOS Talk). The team is clearly investing in channel adapter robustness and session delivery correctness as prerequisites before feature expansion.

---

## 7. User Feedback Summary

### Pain Points (from issue language and reactions)
- **"Results are silently lost"** — The most repeated frustration. Users report subagent completions, cron job outputs, and embedded-assistant turns disappearing without error or retry (#44925, #67777, #92433, #114690). This erodes trust in the orchestration layer.
- **Upgrade breakage** — Multiple users cannot upgrade from 6.x to 7.x due to migration failures (#112395, #119263). The `doctor --fix` path itself is broken in some cases.
- **Context cap hardlock** — Session context capped at 128k regardless of model configuration (#116010) is causing confusion for users on larger-context models.
- **Provider-specific quirks** — DeepSeek silent failures (#116277), Google Antigravity false-positive bans from tool schema reloading (#44134), Poe media models rejected at runtime (#45655), Codex OAuth timing out cron heartsbeats (#89278).
- **Memory inconsistency** — Different users see different memory storage behaviors (chunking vs. raw storage) across agents (#43747).

### Satisfaction Signals
- The **MathJax/LaTeX request** (#42840) has 10 👍 — strong interest from technical users.
- The **YAML config request** (#45758) has 2 👍 — modest interest.
- The **cost-exposure feature** (#9016) has 1 👍 — niche.
- Several **feature requests are labeled `stale`** (#45655, #45573), indicating user follow-up has dropped — possible fatigue.

---

## 8. Backlog Watch

These items have been open for extended periods, carry high severity, and remain blocked on maintainer action:

| Issue | Open Since | Severity | Blocker |
|---|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 2026-03-13 (5 months) | P1 / diamond-lobster | `needs-maintainer-review`, `needs-product-decision` |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | 2026-04-16 (4 months) | P1 / diamond-lobster | `needs-maintainer-review` |
| [#92433](https://github.com/openclaw/openclaw/issues/92433) | 2026-06-12 (2 months) | P1 / diamond-lobster | `needs-maintainer-review`, `needs-product-decision` |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | 2026-07-29 (7 days) | P1 / diamond-lobster | `source-repro` — needs live reproduction |
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | 2026-08-04 (1 day) | P1 / diamond-lobster | Critical migration blocker; no fix PR yet |
| [#112395](https://github.com/openclaw/openclaw/issues/112395) | 2026-07-21 (15 days) | P0 / diamond-lobster | Startup-blocking regression; no fix PR yet |
| [#118846](https://github.com/openclaw/openclaw/issues/118846) | 2026-08-03 (2 days) | P1 / gold-shrimp | Gateway boot saturation; no fix PR yet |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 2026-06-29 (1 month) | P1 / silver-shellfish | Process leak causing runtime degradation |
| [#75380](https://github.com/openclaw/openclaw/issues/75380) | 2026-05-01 (3 months) | P1 / diamond-lobster | Unbounded log growth; no rotation policy |

**Assessment:** The backlog is heavily weighted toward **session-state correctness** and **upgrade migration reliability**. The project appears to be in a defensive hardening cycle — many high-visibility bugs from the 7.x launch are still unresolved, and several are blocking new users from upgrading. Maintainer bandwidth is the primary constraint; multiple issues carry `needs-maintainer-review` and `needs-product-decision` tags with no movement in weeks.

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: Personal AI Agent Open-Source Ecosystem
**Date: 2026-08-05**

---

## 1. Ecosystem Overview

The open-source personal AI assistant landscape is characterized by **high development velocity with uneven stability maturity**. Nine of twelve tracked projects are actively developing with significant daily issue/PR throughput, while three (Moltis, ZeptoClaw, NullClaw) show minimal recent activity. The dominant theme across projects is **reliability hardening**—session-state integrity, message delivery correctness, and upgrade migration robustness are universal concerns. No project has shipped a new release in the current window, suggesting the ecosystem is collectively in a defensive stabilization cycle ahead of anticipated feature launches.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release Status | Health Score |
|---------|-------------|-----------|----------------|-------------|
| **OpenClaw** | 500 | 500 | Stable: 2026.7.1 / 7.2-beta | 🟡 Strained |
| **IronClaw** | 50 | 50 | RC: v1.0.0-rc.1 / v1.1.0-rc.1 | 🟡 Consolidating |
| **Hermes Agent** | 50 | 50 | v0.20.0 | 🟡 Stabilizing |
| **ZeroClaw** | 42 | 50 | None | 🟢 Strong |
| **CoPaw** | 29 | 46 | Beta: v2.1.0-beta.1 | 🟡 Active |
| **NanoBot** | 5 | 26 | None | 🟢 Active |
| **LobsterAI** | 1 | 15 | Stable: 2026.8.3 | 🟢 Good |
| **PicoClaw** | 3 | 4 | None | 🟡 Stable |
| **NanoClaw** | 0 | 5 | None | 🟢 Stable |
| **NullClaw** | 0 | 1 | None | 🟡 Low |
| **Moltis** | 0 | 1 | None | 🔴 Quiet |
| **ZeptoClaw** | 0 | 0 | None | ⚪ Dormant |

**Health scoring rationale:** Based on activity volume, critical bug resolution pace, release cadence, and community engagement signals. "Strained" indicates high activity but significant unresolved P0/P1 issues blocking users. "Quiet/Dormant" reflects minimal maintainer or community momentum.

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale of engagement** — OpenClaw's 500-issue/500-PR daily volume dwarfs all other projects, indicating the largest and most active user base. This generates both rich feedback and proportionally more bug reports.
- **Channel adapter breadth** — Deep investment across Telegram, Discord, Slack, Feishu, and WebSocket-based delivery makes it the most polyglot in integration coverage.
- **Plugin normalization architecture** — The memory-wiki refactor (#119449) and canonical plugin normalization suggest a more mature extension system than competitors.

**Technical Approach Differences:**
- OpenClaw uses a **session-state-centric architecture** with transcript inspection, parent-child ACP streaming, and context cache warming—unlike ZeroClaw's RFC-driven architectural approach or IronClaw's crate-level dependency enforcement.
- Project distinguishes itself with **diamond-lobster severity labeling** and automated triage (`clawsweeper-recovery-stuck`), a more sophisticated issue classification system than any peer.

**Community Size Comparison:**
- OpenClaw (500 daily interactions) >> Hermes Agent (~50) ≈ IronClaw (~50) > ZeroClaw (~92) > CoPaw (~75) > NanoBot (~31) > LobsterAI (~16) > PicoClaw (~7) > NanoClaw (~5) > NullClaw (~1) > Moltis (~1) > ZeptoClaw (0)
- OpenClaw's community is **10–50x larger** than mid-tier projects by raw interaction metrics.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|------------|-------------------|----------------|
| **Session/Message Reliability** | OpenClaw, Hermes, CoPaw, PicoClaw | Silent message loss in subagent/cron flows (#44925, #67777, #92433); approval prompt visibility across channels; context compression breaking provider integrations |
| **Provider Integration Stress** | OpenClaw, NanoBot, CoPaw, LobsterAI | DeepSeek silent failures, Anthropic schema violations, OpenAI cache-key continuity, provider API key leakage (#4784) |
| **Upgrade Migration Integrity** | OpenClaw, IronClaw, Hermes | 6.x→7.x migration blockers (#112395, #119263); Reborn migration losslessness; PYTHONPATH leak across subprocesses (#79046) |
| **Windows Compatibility** | IronClaw, Hermes, LobsterAI | CI blockers, portable deployment gaps, console window noise, test suite POSIX assumptions |
| **MCP/Tool Server Stability** | PicoClaw, NanoBot, ZeroClaw | Agent loop hangs on MCP failure (#3269); business-error silent ignoring (#5237); tool-calling timeouts |
| **Context Window Management** | OpenClaw, Hermes, CoPaw | Hard 128k cap (#116010); prompt-cache invalidation across compression rotation (#79017); token waste from skill loading (#6699) |
| **Channel-Specific Edge Cases** | NanoBot, CoPaw, IronClaw, OpenClaw | Telegram polling stalls (#5156); WeChat token exhaustion (#6696); Discord approval inversion (#3185); Matrix auto-join failures (#5247) |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | IronClaw | ZeroClaw | Hermes Agent | CoPaw | NanoBot | LobsterAI | PicoClaw |
|-----------|----------|----------|----------|-------------|-------|---------|-----------|----------|
| **Primary Focus** | Session/message reliability at scale | Migration integrity & error recoverability | Security-first architecture via RFCs | Plugin ecosystem & cron reliability | Cross-channel desktop/mobile agents | WebUI polish & provider integration | Consumer UX & freemium campaigns | Local-first tooling & MCP |
| **Target Users** | Power users, multi-channel operators | Enterprise/Champions program | Security-conscious builders | Multi-project researchers | Desktop/mobile consumers | WebUI-focused users | Consumer/educational | Embedded/local users |
| **Architecture** | Monolithic gateway + channel adapters | Crate-level dependency graph (Target Crate) | RFC-driven design, security overlays | Plugin lifecycle hooks | Multi-platform (desktop/mobile/Web) | WebUI-first with dev ergonomics | Electron-based desktop | Modular provider abstraction |
| **Release Cadence** | Beta-focused, stability-first | RC phase with migration hardening | Design-heavy, no releases | Post-v0.20.0 stabilization | Beta testing (v2.1.0) | Post-release polish (2026.8.3) | Frequent minor updates | Steady incremental |
| **Key Differentiator** | Highest community scale; most channel adapters | Crate architecture rigor; Windows CI focus | Security RFCs; per-agent scoping | Distributed orchestrator vision; Honcho memory | GPT-5.6 caching; multi-model parallel | React 19 migration; ad-banner control | MCP metasearch; Exa search |

---

## 6. Community Momentum & Maturity

### Rapidly Iterating (High Velocity)
- **OpenClaw** — 500/500 daily interactions; defensive hardening cycle
- **IronClaw** — 50/50 daily; Windows CI unblocking, migration ratchets
- **ZeroClaw** — 42/50 daily; RFC-driven design accumulation
- **CoPaw** — 29/46 daily; desktop regression firefighting

### Steady Development (Medium Velocity)
- **Hermes Agent** — 50/50 daily but lower complexity issues; post-release stabilization
- **NanoBot** — 5/26 daily; responsive to WebUI polish and provider isolation
- **LobsterAI** — 1/15 daily; post-campaign polish, dependency modernization

### Quiet/Stable (Low Velocity)
- **PicoClaw** — 3/4 daily; infrastructure fixes, critical MCP hang unresolved
- **NanoClaw** — 0/5 daily; Dial channel feature in review
- **NullClaw** — 0/1 daily; provider expansion only
- **Moltis** — 0/1 daily; automated maintenance only
- **ZeptoClaw** — 0/0 daily; dormant

### Maturity Indicators
- **Most Mature:** OpenClaw (largest community, most sophisticated triage), IronClaw (structured crate architecture, Champions program)
- **Emerging:** ZeroClaw (security-first design culture, RFC governance)
- **Early Stage:** PicoClaw, NanoClaw (limited issue resolution velocity, critical bugs unaddressed)

---

## 7. Trend Signals

### Industry-Wide Trends

1. **Session-State Correctness is the Dominant Challenge**
   - OpenClaw (5+ P1 session bugs), Hermes (context compression cache), CoPaw (auto-compression flow gaps), ZeroClaw (session ownership RFCs)
   - **Signal:** The industry is converging on session management as the hardest problem in agent reliability. Projects that solve this cleanly will gain significant competitive advantage.

2. **Provider Isolation & Security Hardening**
   - NanoBot API key leakage (#4784), LobsterAI key exposure (#1202), ZeroClaw per-agent scoping (knowledge graph, session tools), OpenClaw Anthropic schema violations
   - **Signal:** Multi-provider deployments are becoming common, and security gaps in provider isolation are emerging as critical trust barriers. Fail-closed defaults and per-agent ownership models will be table stakes.

3. **Cross-Channel Consistency as a Differentiator**
   - OpenClaw (channel adapter hardening), CoPaw (approval visibility across channels), NanoBot (Telegram/WeCom/Mattermost parity), PicoClaw (MCP integration)
   - **Signal:** Users expect identical behavior across Web, mobile, Discord, Telegram, andMatrix. Channel-specific edge cases (token exhaustion, polling stalls, approval invisibility) erode trust faster than any other factor.

4. **Desktop/Local-First Stability Bottlenecks**
   - CoPaw v2.1.0b1 regressions (PYTHONHOME injection, browser SDK crashes), IronClaw Windows blockers, Hermes Windows portable gaps
   - **Signal:** Desktop deployments introduce subprocess environment management, platform-specific UI frameworks, and local tool integration that web-only projects avoid. Projects shipping desktop builds must invest disproportionately in environment isolation testing.

5. **Cost Transparency & Optimization Demand**
   - OpenClaw (context cap complaints, cost deref crashes), CoPaw (GPT-5.6 caching, skill token waste), Hermes (prompt_cache_key continuity), LobsterAI (model overload vs rate-limit distinction)
   - **Signal:** Users are becoming cost-aware and expect visibility into token usage, caching effectiveness, and rate-limit behavior. Projects that surface cost signals without requiring CLI expertise will win power-user adoption.

6. **RFC-Governed Architecture as an Emerging Pattern**
   - ZeroClaw's RFC pipeline (goal mode, chat-completions profile, security overlays), OpenClaw's plugin normalization RFC, Hermes' distributed orchestrator proposal
   - **Signal:** Mature projects are moving toward design-phase governance via RFCs rather than ad-hoc feature requests. This correlates with higher long-term architectural coherence and lower technical debt accumulation.

### Value for AI Agent Developers
- **Prioritize session-state correctness** before feature expansion—the market is saturated with features but starved for reliability.
- **Invest in provider isolation** as a security differentiator; API key leakage across providers is a trust-destroying class of bug.
- **Build cross-channel consistency tests** into CI; channel-specific edge cases are the fastest path to user churn.
- **Surface cost observability** (token usage, cache hit rates, rate-limit status) in the UI—not just CLI—to capture the growing cost-aware user segment.
- **Adopt RFC governance** for architectural decisions; the projects with formal design review (ZeroClaw, IronClaw) show stronger long-term direction.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-05

## 1. Today's Overview

NanoBot is in a high-activity development phase, with 26 PRs updated in the last 24 hours (19 merged/closed) and 5 issues addressed. The project shows strong momentum in WebUI refinement, channel reliability fixes, and provider integrations. No new releases were published today. The health of the codebase is being actively maintained through a mix of bug fixes, regressions patches, and feature expansions, though several open issues signal lingering stability concerns around MCP tooling, Matrix interoperability, and environment isolation.

## 2. Releases

No new releases were published on this date.

## 3. Project Progress

**Merged/Closed PRs (19):**

- **#5250** — Fixed feathered clipping on agent activity pane edges, improving visual continuity ([link](https://github.com/HKUDS/nanobot/pull/5250))
- **#5238** — Removed request-scoped access grants (`Tool.available()` layer), simplifying session authorization ([link](https://github.com/HKUDS/nanobot/pull/5238))
- **#5233** — Added Mattermost `groupPolicyInThread` config, enabling separate thread vs. channel mention policies, exposed in WebUI ([link](https://github.com/HKUDS/nanobot/pull/5233))
- **#5223** — Fixed WeCom filename sanitization fallback when cleanup strips all characters, preventing directory-targeted writes ([link](https://github.com/HKUDS/nanobot/pull/5223))
- **#5210** — Added trusted-proxy bootstrap auth for WebUI, supporting Cloudflare Tunnel + Access deployments ([link](https://github.com/HKUDS/nanobot/pull/5210))
- **#5222** — Fixed Telegram fenced code block parsing for languages with special characters (`c++`, `html+django`) ([link](https://github.com/HKUDS/nanobot/pull/5222))
- **#1776** — Closed after merging the missing `group_mode` field into Telegram `TelegramConfig` schema ([link](https://github.com/HKUDS/nanobot/pull/1776))
- **#5244** — Fixed WebUI prompt rail to render markdown in assistant answer previews ([link](https://github.com/HKUDS/nanobot/pull/5244))
- **#5245** — Aligned timestamp tooltip styling across WebUI footers with shared component ([link](https://github.com/HKUDS/nanobot/pull/5245))
- **#5240** — Unified floating control surfaces and item styling in WebUI ([link](https://github.com/HKUDS/nanobot/pull/5240))
- **#5243** — Moved automation trigger markers to footer alongside timestamps, improving visual consistency ([link](https://github.com/HKUDS/nanobot/pull/5243))
- **#5242** — Added malformed slash-command rejection with closest-match suggestions and command-only history persistence ([link](https://github.com/HKUDS/nanobot/pull/5242))
- **#5239** — Added integrated Vite dev mode (`nanobot webui --dev`) with HMR for contributors ([link](https://github.com/HKUDS/nanobot/pull/5239))
- **#5241** — Refined inline token highlights with solid accent color and semibold weight in WebUI ([link](https://github.com/HKUDS/nanobot/pull/5241))

**Key themes today:** WebUI visual consistency and developer ergonomics dominate, alongside channel-level bug fixes for Telegram, WeCom, and Mattermost.

## 4. Community Hot Topics

- **[Issue #4784](https://github.com/HKUDS/nanobot/issues/4784)** — *Security: Provider API keys leaked between providers via global `os.environ` mutation.* Open since July 6 with 2 comments. This is a critical security concern where `OpenAICompatProvider._setup_env()` overwrites or skips setting env vars, causing API key bleed across providers. Despite being open for a month, it remains unresolved — a clear signal that provider isolation is a community priority.

- **[Issue #5237](https://github.com/HKUDS/nanobot/issues/5237)** — *MCP tool returns "data not found" envelope but agent ignores it.* Open since Aug 4. Users are hitting a fundamental gap: business-level errors wrapped in `isError=False` are invisible to the agent loop. This will likely surface frequently as MCP adoption grows.

- **[PR #4919](https://github.com/HKUDS/nanobot/pull/4919)** — *Telegram custom Bot API base URL and extra headers.* Open since July 14. Self-hosted Telegram Bot API deployments are a known need; this PR remains pending, suggesting it may need maintainer review before merging.

- **[PR #5234](https://github.com/HKUDS/nanobot/pull/5234)** — *Integrate mst-python as a metasearch provider.* Open since Aug 3. Combines DuckDuckGo, Google, Brave, and Bing via Reciprocal Rank Fusion — a feature users have long requested for richer web search.

## 5. Bugs & Stability

| Severity | Item | Status | Fix PR |
|----------|------|--------|--------|
| 🔴 Critical | **#4784** — API key leakage via `os.environ` mutation across providers | Open | None yet |
| 🟠 High | **#5235** — Opus 5 temperature parameter rejected by Anthropic API (`omit_temperature` list missing `"opus-5"`) | Closed | #5235 |
| 🟠 High | **#5237** — MCP tool business errors silently ignored by agent | Open | None yet |
| 🟡 Medium | **#5247** — Matrix bot fails to auto-join rooms on Continuwity due to empty POST body | Open | **#5248** (open) |
| 🟡 Medium | **#5223** — WeCom media download writes to directory when filename sanitizes to empty | Closed | #5223 |
| 🟡 Medium | **#5156** — Telegram polling silently stalls after transient network blips | Open | #5156 (open) |
| 🟢 Low | **#5246** — `.gitignore` leaves `memory/.cursor` and `history.jsonl` untracked | Open | None yet |

**Notable:** The two highest-severity issues (#4784 security leak, #5237 MCP silent failure) have no linked fix PRs yet and are the most pressing stability concerns.

## 6. Feature Requests & Roadmap Signals

- **#5234** — MST metasearch provider integration (open, P1). Strong user demand for aggregated search; likely candidate for next release.
- **#4919** — Custom Telegram Bot API base URL (open since July 14). Enterprise/self-hosted deployments need this; may ship with Telegram channel updates.
- **#5184** — Quick Chat and Temporary Chat for WebUI (open, by Re-bin). In-memory ephemeral sessions and persistent quick-chat are popular UX patterns; could appear in a future WebUI release.
- **#5233** — Mattermost per-thread group policy (merged). Signals continued investment in Mattermost channel parity.
- **#5210** — Trusted proxy bootstrap auth (merged). Expands deployability behind reverse proxies and zero-trust gateways.

**Prediction:** The next release will likely highlight the MST provider, WebUI dev mode, and continued Telegram/Mattermost channel hardening.

## 7. User Feedback Summary

- **Provider isolation anxiety:** Issue #4784 reveals users are deploying multi-provider setups and hitting security regressions from shared environment mutation. Trust in provider key management is at risk.
- **MCP error handling gap:** Issue #5237 shows users are building MCP toolchains and expecting the agent to respect business-level errors — a fundamental expectation for production use.
- **Telegram reliability:** Two open Telegram issues (#5156 silent polling stall, #4919 custom API base) indicate users are running Nanobot in constrained network environments (proxies, self-hosted bots) and hitting edge cases.
- **WebUI polish appreciated:** Multiple merged PRs today (#5244, #5245, #5240, #5241, #5243) show responsive maintenance on visual consistency — users who use the WebUI daily will notice the improvement.
- **Dev ergonomics valued:** PR #5239 (Vite dev mode) directly addresses contributor friction, suggesting the maintainer team is listening to developer experience feedback.

## 8. Backlog Watch

| Issue/PR | Age | Risk |
|----------|-----|------|
| [#4784](https://github.com/HKUDS/nanobot/issues/4784) — API key leakage | ~30 days open | 🔴 Critical security; no fix PR yet |
| [#5237](https://github.com/HKUDS/nanobot/issues/5237) — MCP silent errors | 1 day | 🟠 High; blocking MCP production use |
| [#5156](https://github.com/HKUDS/nanobot/pull/5156) — Telegram polling stall | ~7 days | 🟡 Medium; no merge yet |
| [#4919](https://github.com/HKUDS/nanobot/pull/4919) — Custom Telegram API base | ~22 days | 🟡 Medium; blocked or pending review |
| [#5247](https://github.com/HKUDS/nanobot/issues/5247) — Matrix Continuwity join | 1 day | 🟡 Medium; fix PR #5248 open but not merged |
| [#5246](https://github.com/HKUDS/nanobot/issues/5246) — Memory `.gitignore` gap | 1 day | 🟢 Low; cosmetic but easy fix |

**Maintainer attention needed:** Issue #4784 is the highest-risk backlog item — a month-old security vulnerability with no attached fix. Issue #5237 and PR #5156 also warrant prompt review as they affect core agent reliability.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-05

## 1. Today's Overview

Hermes Agent shows sustained development velocity with **50 issues and 50 PRs** updated in the last 24 hours, indicating a highly active contributor and maintainer base. No new releases were published today, but a flurry of bug fixes and feature proposals landed in the PR queue, particularly around cron reliability, Windows compatibility, gateway stability, and plugin ecosystem maturity. The project appears to be in a stabilization phase following the v0.20.0 release, with maintainers (notably `zyz619963502zyz` and `teknium1`) addressing a backlog of community-reported issues across multiple components.

## 2. Releases

**No new releases today.** The latest known version remains **v0.20.0** (build 2026.8.3). Several pending PRs suggest a v0.20.1 release is imminent, particularly those addressing Windows test-suite breakage, PYTHONPATH leakage, and gateway startup regressions.

## 3. Project Progress

**Merged/Closed today:**
- **#73599** (CLOSED) — Dashboard tab stale-session issue after gateway restart resolved ([link](https://github.com/NousResearch/hermes-agent/issues/73599))
- **#50747** (CLOSED) — Feishu adapter container-rebuild requirements-failure fixed on main ([link](https://github.com/NousResearch/hermes-agent/issues/50747))
- **#18594** (CLOSED) — `get_hermes_home()` cross-profile data corruption fixed ([link](https://github.com/NousResearch/hermes-agent/issues/18594))
- **#66076** (CLOSED) — TUI npm install now hides the Windows console window properly ([link](https://github.com/NousResearch/hermes-agent/issues/66076))

**Notable PRs advancing today:**
- **#79049** — Cron email delivery now supports `{date}` in `subject_template` ([link](https://github.com/NousResearch/hermes-agent/pull/79049))
- **#79045** — Honcho memory consolidation now triggers at session end, not just on dream cycles ([link](https://github.com/NousResearch/hermes-agent/pull/79045))
- **#79046** — Critical regression fix: gateway no longer leaks `PYTHONPATH` to child subprocesses ([link](https://github.com/NousResearch/hermes-agent/pull/79046))
- **#76661** — P2P federation heartbeat for multi-device task relay ([link](https://github.com/NousResearch/hermes-agent/pull/76661))
- **#74300** — Windows test suite made functional by skipping POSIX-only tests and adding platform helpers ([link](https://github.com/NousResearch/hermes-agent/pull/74300))

## 4. Community Hot Topics

| Issue/PR | Comments | Key Theme |
|----------|----------|-----------|
| [#64182](https://github.com/NousResearch/hermes-agent/issues/64182) — Plugin Interface Expansion tracking | 21 | Community-driven plugin roadmap |
| [#64231](https://github.com/NousResearch/hermes-agent/issues/64231) — Lifecycle-event catalog & hook taxonomy | 17 | Standardizing plugin hook acceptance |
| [#16004](https://github.com/NousResearch/hermes-agent/issues/16004) — Configurable bounded auto-continue | 10 | Agent autonomy in long-running sessions |
| [#46199](https://github.com/NousResearch/hermes-agent/issues/46199) — Windows portable/isolated deployment | 7 | Enterprise security concerns on Windows |
| [#79042](https://github.com/NousResearch/hermes-agent/issues/79042) — RFC: Distributed Orchestrator | 0 (new) | Architectural shift: remote brain / local nodes |

**Analysis:** The plugin ecosystem is the dominant community focus — two tracking issues (#64182, #64231) together account for 38 comments and reflect a sustained push for a cleaner, more governable plugin lifecycle. The distributed orchestrator RFC (#79042) signals the community is already thinking beyond single-node deployments. The bounded auto-continue request (#16004) reveals a gap in long-running agent workflows, particularly for ACP/VS Code users.

## 5. Bugs & Stability

**P0 — Critical:**
- [#79017](https://github.com/NousResearch/hermes-agent/issues/79017) — `prompt_cache_key` loses continuity across context-compression session rotation; OpenAI cache effectiveness degraded.

**P1 — High:**
- [#18594](https://github.com/NousResearch/hermes-agent/issues/18594) (CLOSED) — `get_hermes_home()` silent fallback to `~/.hermes` causing cross-profile data corruption.

**P2 — Medium:**
- [#75791](https://github.com/NousResearch/hermes-agent/issues/75791) — Windows 11 25H2: `hermes dashboard --status` falsely reports no dashboard running
- [#75801](https://github.com/NousResearch/hermes-agent/issues/75801) — OpenCode Go `gpt-5.6-luna` omitting `finish_reason` causes 4 fake mid-stream drops; desktop strips streamed answer
- [#76457](https://github.com/NousResearch/hermes-agent/issues/76457) — `hermes config set` writes list-of-strings as stringified JSON instead of YAML list
- [#77047](https://github.com/NousResearch/hermes-agent/issues/77047) — `read_file` misclassifies valid CJK UTF-8 files as binary when sample cut lands mid-character
- [#78932](https://github.com/NousResearch/hermes-agent/issues/78932) — Rejected MEDIA delivery paths are silent to the model
- [#78862](https://github.com/NousResearch/hermes-agent/issues/78862) — Cron jobs die on reasoning-model non-stream stale timeout; fallback never engages
- [#78514](https://github.com/NousResearch/hermes-agent/issues/78514) — Feishu multiplex dedup is per-profile, not shared → replayed events processed twice
- [#78406](https://github.com/NousResearch/hermes-agent/issues/78406) — OpenAI transport not rebuilt until retry budget exhausted after mid-stream connection drops
- [#79047](https://github.com/NousResearch/hermes-agent/issues/79047) — Regression: `api_server` bypasses `get_tool_definitions()` cache, adding ~3.3s per request
- [#79044](https://github.com/NousResearch/hermes-agent/issues/79044) — Slack channel directory discovery can indefinitely block inbound Gateway startup
- [#79048](https://github.com/NousResearch/hermes-agent/issues/79048) — macOS: shared-token profile services mutually evict after updater regenerates plists
- [#78980](https://github.com/NousResearch/hermes-agent/issues/78980) — Cron lifecycle guard false-positives on Python scripts containing `~/...` path literals
- [#62254](https://github.com/NousResearch/hermes-agent/issues/62254) — `_get_named_custom_provider` silently ignores `api_key_env`, causing 401s
- [#51684](https://github.com/NousResearch/hermes-agent/issues/51684) — Feishu `FEISHU_ALLOWED_USERS=*` wildcard doesn't apply to approval card clicks
- [#53328](https://github.com/NousResearch/hermes-agent/issues/53328) — Desktop scans entire home directory for git repos with no config to disable

**Fix PRs in progress:**
- [#79046](https://github.com/NousResearch/hermes-agent/pull/79046) — Addresses PYTHONPATH leak (related to [#57470](https://github.com/NousResearch/hermes-agent/pull/57470), the original fix)
- [#52076](https://github.com/NousResearch/hermes-agent/pull/52076) — Feishu withdrawn-reply handling fix
- [#73955](https://github.com/NousResearch/hermes-agent/pull/73955) — Compression RPC timeout alignment

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Community Signal |
|---------|-------|-----------------|
| Distributed Orchestrator (remote brain ↔ local nodes) | [#79042](https://github.com/NousResearch/hermes-agent/issues/79042) | Major architectural proposal; high ambition |
| DeepSeek v4-flash responses API support | [#79039](https://github.com/NousResearch/hermes-agent/issues/79039) | Direct provider adoption request |
| Project-scoped memory pools (global + per-project) | [#16833](https://github.com/NousResearch/hermes-agent/issues/16833) | 4 comments, 1 👍 — addresses multi-project contamination |
| Configurable bounded auto-continue | [#16004](https://github.com/NousResearch/hermes-agent/issues/16004) | 10 comments, 1 👍 — long-pending P2 |
| Disable automatic project/repo discovery | [#64615](https://github.com/NousResearch/hermes-agent/issues/64615) | User-requested toggle for the Home-dir scanner |
| Desktop subscription/token usage in status bar | [#78997](https://github.com/NousResearch/hermes-agent/issues/78997) | Quality-of-life feature for heavy users |
| Cron `subject_template` with `{date}` | [#79049](https://github.com/NousResearch/hermes-agent/pull/79049) | PR already open; likely to merge |
| P2P federation heartbeat | [#76661](https://github.com/NousResearch/hermes-agent/pull/76661) | PR already open; enables resilient multi-device relay |
| Custom cron response wrappers | [#73332](https://github.com/NousResearch/hermes-agent/pull/73332) | PR open; configurable output format |
| Per-model rate-limit cooldown persistence | [#73380](https://github.com/NousResearch/hermes-agent/pull/73380) | PR open; improves fallback reliability |

**Prediction:** The next release (v0.20.1) will likely include the cron subject template, memory consolidation fix, PYTHONPATH leak fix, and Windows test-suite improvements. The distributed orchestrator RFC and DeepSeek responses API are more likely v0.21+ candidates.

## 7. User Feedback Summary

**Pain points:**
- **Windows UX fragility** — Multiple users report Windows-specific issues: dashboard status false negatives (#75791), portable deployment gaps (#46199), TUI console window noise (#66076), and test suite breakage (#74300). The project is clearly Linux/macOS-first with Windows as a secondary target.
- **Context compression cache invalidation** — [#79017](https://github.com/NousResearch/hermes-agent/issues/79017) highlights that session rotation breaks OpenAI prompt caching, directly impacting cost and latency for heavy users.
- **Cron reliability with reasoning models** — [#78862](https://github.com/NousResearch/hermes-agent/issues/78862) describes a race between the 600s reasoning floor and the 600s cron inactivity limit, causing legitimate jobs to die silently.
- **Multi-tenant Feishu dedup gap** — [#78514](https://github.com/NousResearch/hermes-agent/issues/78514) shows that multiplex mode creates isolated dedup caches per profile, causing double-processing on event replay.
- **Config serialization bug** — [#76457](https://github.com/NousResearch/hermes-agent/issues/76457) silently corrupts list-type config values, a data-integrity concern.
- **Desktop home-directory scanning** — [#53328](https://github.com/NousResearch/hermes-agent/issues/53328) and [#64615](https://github.com/NousResearch/hermes-agent/issues/64615) both flag the unconfigurable full-home-dir git scan as a performance and privacy nuisance.

**Satisfaction signals:**
- Users appreciate the move toward structured plugin governance (#64182, #64231) and the distributed orchestrator vision (#79042).
- The Honcho auto-memory consolidation fix (#79045) addresses a real workflow gap for server-side dream users.

## 8. Backlog Watch

| Issue | Age | Priority | Concern |
|-------|-----|----------|---------|
| [#16004](https://github.com/NousResearch/hermes-agent/issues/16004) — Bounded auto-continue | ~3 months | P2 | Core autonomy gap; 10 comments, no merge |
| [#16833](https://github.com/NousResearch/hermes-agent/issues/16833) — Project-scoped memory pools | ~3 months | P3 | Multi-project contamination; 4 comments |
| [#79017](https://github.com/NousResearch/hermes-agent/issues/79017) — prompt_cache_key continuity | New today | P0 | Cache breakage during compression rotation; 1 comment, no fix yet |
| [#79042](https://github.com/NousResearch/hermes-agent/issues/79042) — Distributed Orchestrator RFC | New today | P3/RFC | Architectural decision pending; needs maintainer response |
| [#79047](https://github.com/NousResearch/hermes-agent/issues/79047) — api_server tool_defs cache regression | New today | P2 | ~3.3s regression per request; no fix PR yet |
| [#78862](https://github.com/NousResearch/hermes-agent/issues/78862) — Cron reasoning-model timeout race | 2 days | P2 | Silent job deaths; no fix PR yet |
| [#78406](https://github.com/NousResearch/hermes-agent/issues/78406) — OpenAI transport retry delay | 2 days | P2 | 161 drops/day in production; no fix PR yet |
| [#53328](https://github.com/NousResearch/hermes-agent/issues/53328) — Home-dir git scan unconfigurable | ~1 month | P2 | Privacy/performance; no fix PR yet |

**Key risk:** The P0 cache-key issue (#79017) and the P2 cron timeout race (#78862) both lack fix PRs and affect production reliability. The `api_server` regression (#79047) is a fresh performance hit that should be prioritized. Maintainer attention on these three would significantly improve user trust.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-05

## 1. Today's Overview

PicoClaw (sipeed/picoclaw) shows moderate development activity today with 3 issues and 4 PRs updated in the last 24 hours. The project is actively addressing infrastructure-level concerns (OAuth auth flow, provider token tracking) while simultaneously grappling with three significant stability bugs that affect end-user experience — notably a critical agent-loop hang when MCP servers fail and a severe Web UI lag issue with chat history. No new releases were published. Overall project health is **stable but with emerging quality concerns** in production-edge scenarios.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged/Closed PRs today:**

- **[PR #3280](https://github.com/sipeed/picoclaw/pull/3280)** — Fixed browser OAuth login to survive real-world callback conditions. The auth login flow was failing after user consent on headless/remote setups, burning the authorization code and forcing a full restart. Four independent root causes were identified and patched.
- **[PR #3251](https://github.com/sipeed/picoclaw/pull/3251)** — Captured prompt cache token usage in Anthropic providers. Previously, cache-related token metrics from Claude were discarded, making it impossible to verify whether prompt caching was actually working.

**Open PRs awaiting review:**

- **[PR #3299](https://github.com/sipeed/picoclaw/pull/3299)** — Adds native Exa web search as a `tools.web` / `web_search` provider, supporting range filters and content highlights.
- **[PR #3317](https://github.com/sipeed/picoclaw/pull/3317)** — Logs prompt cache tokens in LLM response debug output, improving observability for gateway operators.

## 4. Community Hot Topics

| # | Type | Title | Comments | 👍 | Link |
|---|------|-------|----------|-----|------|
| 3281 | Issue | Web UI chat input is very laggy with long history | 3 | 1 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) |
| 3269 | Issue | MCP server connection failure causes agent loop to hang | 3 | 1 | [#3269](https://github/sipeed/picoclaw/issues/3269) |
| 3182 | Issue | Android version can't launch service | 6 | 0 | [#3182](https://github.com/sipeed/picoclaw/issues/3182) |

**Analysis:**
- **Issue #3281** reflects a growing user base running longer conversations — the Web UI rendering pipeline likely needs virtualization or debouncing for input fields when session history grows.
- **Issue #3269** is the most operationally critical: an MCP connection failure halts the entire agent loop, making the chat interface unresponsive. This signals a need for timeout/circuit-breaker patterns in tool calling.
- **Issue #3182** (6 comments, 0 reactions) suggests Android support is under-resourced — the app has permissions but cannot set paths or start services, pointing to potential Android-specific storage/access limitations.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| 🔴 Critical | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP server failure hangs the agent loop; chat stops responding entirely | None yet |
| 🟡 Medium | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI chat input extremely laggy with moderate history length | None yet |
| 🟠 Medium | [#3182](https://github.com/sipeed/picoclaw/issues/3182) | Android app cannot launch service or change path from settings (stale, closed) | None — marked stale |

**Notes:**
- The critical bug (#3269) has no associated fix PR. This is the highest-priority item for the maintainer team.
- The Android bug (#3182) was closed as stale after ~40 days with no resolution, which may signal low Android platform coverage.

## 6. Feature Requests & Roadmap Signals

| PR | Description | Likelihood for Next Release |
|----|-------------|----------------------------|
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Native Exa web search provider | **High** — well-scoped, self-contained, fills a clear gap in tool providers |
| [#3317](https://github.com/sipeed/picoclaw/pull/3317) | Log prompt cache tokens in debug output | **High** — observability improvement, low risk, complements PR #3251 |

**Signal:** The project is moving toward richer tool provider integrations (Exa search) and deeper observability (cache token logging). These align with PicoClaw's positioning as a local-first AI agent with extensible tooling.

## 7. User Feedback Summary

**Pain points:**
1. **Web UI responsiveness degrades with use** — users report input lag after building chat history, suggesting the frontend is not handling long DOM trees efficiently.
2. **Fragile MCP connectivity** — a single failed tool server connection brings the entire agent to a standstill, with no timeout or fallback.
3. **Android experience is broken** — permission grants don't translate to functional service startup; path configuration is impossible.

**Satisfaction signals:**
- OAuth auth flow improvements (PR #3280) address a real pain point for headless/remote deployments.
- Token cache visibility (PR #3251/#3317) shows responsiveness to operator needs for cost/performance monitoring.

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#3182](https://github.com/sipeed/picoclaw/issues/3182) — Android service launch failure | ~40 days, closed as stale | Android platform may be abandoned or under-supported; users on mobile have no resolution path |
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) — MCP hang / no fix PR | ~16 days open | Critical production bug with zero traction; should be prioritized before next release |
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI lag | ~15 days open | Degrading UX for power users; no fix PR yet |

**Recommendation:** The maintainer team should address [#3269](https://github.com/sipeed/picoclaw/issues/3269) before publishing the next release, as it represents a complete service outage scenario for any user running MCP tools with unreliable connections.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-05

## 1. Today's Overview

NanoClaw shows moderate development activity today with **5 PRs updated** and **zero issues opened or resolved**. There were no new releases, and issue activity remains at zero, indicating the project is in a quiet window between major milestones. The majority of today's action centers on an upcoming **Dial channel integration** (SMS + AI voice calls) spanning two parallel feature PRs, alongside a critical Discord webhook bug fix. One maintenance PR (#3154) was closed, likely merged, addressing scheduled task timing. Overall project health appears **stable and steadily progressing**, with no regressions or blockers reported today.

## 2. Releases

**No new releases today.** The project has not published a new version in the current window.

## 3. Project Progress

**Closed/Merged PRs today:**

- **[#3154](https://github.com/nanocoai/nanoclaw/pull/3154)** — `fix(agent-runner): give scheduled tasks current run time`
  - Renders a task's `time` from its effective scheduled occurrence (`process_after`), with creation timestamp retained as a fallback for legacy rows.
  - Adds task-only `current_time` including weekday and configured agent-group timezone context.
  - This improves scheduling accuracy and resolves edge cases where legacy tasks lacked proper time metadata.

**Open PRs under active review today:**

- **[#3186](https://github.com/nanocoai/nanoclaw/pull/3186)** — `refactor: add host seams for skill-owned capabilities` — structural refactor enabling skills to own their capabilities more cleanly.
- **[#3050](https://github.com/nanocoai/nanoclaw/pull/3050)** — `feat(setup): add Dial to the channel picker + wizard/skills` — extends setup UX to support the new Dial channel.
- **[#3041](https://github.com/nanocoai/nanoclaw/pull/3041)** — `feat(channels): add Dial channel adapter (SMS + AI voice calls)` — the core implementation of the Dial integration.

## 4. Community Hot Topics

The most discussed items today revolve around the **Dial channel integration** and a **Discord approval bug**:

| PR | Type | Author | Activity |
|---|---|---|---|
| [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) | Feature skill | OmriBenShoham | Open since 2026-07-14 |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | Feature skill | OmriBenShoham | Open since 2026-07-14 |
| [#3185](https://github.com/nanocoai/nanoclaw/pull/3185) | Bug fix | omerh | Open since 2026-08-04 |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | Refactor | zvi-fried | Open since 2026-08-04 |

**Underlying needs:**
- **Dial (SMS + AI voice)** is a significant new channel addition, suggesting the community is driving toward **omnichannel reach** — users want to interact with NanoClaw via phone/SMS, not just chat platforms. The dual PRs (core adapter + setup wizard) indicate a well-scoped feature.
- **Discord approval bugs** remain a pain point; webhook-based interaction handling continues to produce edge-case failures.

## 5. Bugs & Stability

**Bug reported today (High Severity):**

- **[#3185](https://github.com/nanocoai/nanoclaw/pull/3185)** — `fix(discord): strip \n delimiter in webhook interaction custom_id so approvals resolve correctly`
  - **Impact:** On Discord, *every* approval button click resolves to the wrong option — users clicking "Approve" are effectively getting "Reject."
  - **Root cause:** The Chat SDK bridge's raw HTTP-interaction (webhook) path decodes `custom_id` by splitting on `:...` without accounting for newline delimiters.
  - **Status:** Fix PR open, awaiting merge. This is a **data-correctness and trust issue** for Discord users relying on approval flows.

No other bugs or crashes were reported today.

## 6. Feature Requests & Roadmap Signals

- **Dial channel (SMS + AI voice calls)** — [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) + [#3050](https://github.com/nanocoai/nanoclaw/pull/3050). This is the most significant feature in the current cycle. If merged, it will likely ship in the **next minor release** alongside the setup wizard integration.
- **Skill-owned capabilities refactor** — [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) suggests a broader architectural shift toward modular skill ownership, which may precede a skill system overhaul in a future release.

**Prediction:** The next release will likely include the Dial channel adapter and the setup wizard update, assuming both PRs merge cleanly. The refactor in #3186 may be deferred to a follow-up if it touches core abstractions.

## 7. User Feedback Summary

- **Discord approval UX is broken** — The #3185 bug indicates that Discord users relying on button-based approvals are experiencing a complete inversion of intent (approve → reject). This is a **high-frustration issue** for anyone using NanoClaw's Discord integration for decision workflows.
- **Demand for phone/SMS channels** — The sustained effort on the Dial integration (two PRs, active since mid-July) signals strong community or roadmap demand for **voice and SMS as first-class interaction channels**.
- **Scheduling reliability** — The #3154 fix (closed today) addresses a subtle but important correctness issue with scheduled task timing, suggesting some users have encountered stale or incorrect task timestamps.

## 8. Backlog Watch

| PR | Age | Concern |
|---|---|---|
| [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) | ~21 days open | Core Dial channel adapter — long-open feature PR needs maintainer review |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | ~21 days open | Dial setup wizard — depends on #3041, blocked from merging independently |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | 1 day open | Refactor PR — fresh but may need architectural review before merge |

**Recommendation:** PRs #3041 and #3050 have been open for over three weeks. Maintainer attention is needed to unblock the Dial feature launch. The Discord fix (#3185) should be prioritized given its user-impacting severity.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-05

## 1. Today's Overview

NullClaw registered minimal activity over the last 24 hours, with zero issues updated and no new releases published. The only movement comes from a single open pull request (PR #981) proposing a new `grok-cli` provider for xAI's Grok CLI, last updated on 2026-08-04. No merged or closed PRs were recorded today, and there are no newly closed issues, suggesting a quiet development cycle. The project appears to be in a steady state with ongoing feature contributions but no urgent maintenance or release activity.

## 2. Releases

No new releases were published in the last 24 hours. The project has no latest release data available for review.

## 3. Project Progress

- **Merged/Closed PRs today:** None
- **Active PR:** [PR #981 — feat(provider): add grok-cli provider for xAI Grok CLI](https://github.com/nullclaw/nullclaw/pull/981) by **valonmulolli** (created 2026-07-29, updated 2026-08-04). This PR introduces a new CLI-based provider that delegates to the local `grok` CLI, following the established spawn-per-request pattern used by existing providers (`codex-cli`, `gemini-cli`, `claude-cli`). The provider is optional and requires the `grok` CLI to be installed and authenticated. While not yet merged, it represents a meaningful expansion of supported AI backends.

## 4. Community Hot Topics

- **[PR #981](https://github.com/nullclaw/nullclaw/pull/981)** — `feat(provider): add grok-cli provider for xAI Grok CLI` — This is currently the only active PR. The proposal to add a Grok CLI provider signals continued community interest in broadening the range of supported LLM providers within NullClaw's provider abstraction layer. The fact that it follows the same pattern as existing CLI providers (`codex-cli`, `gemini-cli`, `claude-cli`) suggests the maintainers have an established contribution model for new providers, making this a low-risk, high-value addition. No comments or reactions are recorded yet, indicating the PR is relatively early in review.

No issues with significant community engagement were reported today.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported in the last 24 hours. Zero issues were closed, so there is no data on fixes landed today. The project's stability posture appears unremarkable based on current activity.

## 6. Feature Requests & Roadmap Signals

- **[PR #981](https://github.com/nullclaw/nullclaw/pull/981)** — The `grok-cli` provider is both a feature request and a concrete implementation. Its existence on the roadmap (as an in-review PR) indicates the project is actively expanding provider coverage, particularly for CLI-hosted models. If merged, it would likely ship in the next release that focuses on provider additions. No other feature requests were active today.

## 7. User Feedback Summary

No new user feedback was recorded today. The open PR by **valonmulolli** reflects a user need for xAI Grok integration within NullClaw's provider ecosystem — a demand consistent with the project's pattern of supporting multiple CLI-based LLM frontends. With no issues open and zero comments on the active PR, there are no currently expressed pain points or dissatisfaction signals from the community.

## 8. Backlog Watch

- **[PR #981](https://github.com/nullclaw/nullclaw/pull/981)** — Created on 2026-07-29 with the last update on 2026-08-04. While not critically stale, the PR has been open for approximately 7 days with no recorded maintainer review activity (zero comments). This warrants monitoring to ensure it does not drift. No other issues or PRs require immediate maintainer attention based on today's data.

---

**Overall Health Assessment:** NullClaw is in a low-activity period with no releases, no bug fixes, and no closed issues. The single open PR (PR #981) is a positive signal of continued feature development. The project is stable but would benefit from maintainer review attention on the outstanding provider PR to keep the contribution pipeline moving.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-05

## 1. Today's Overview

IronClaw shows **very high activity** today with 50 issues and 50 PRs updated in the last 24 hours, though no new releases were published. The project is in an intense consolidation phase around the 1.1.0 release, with multiple architectural ratchet fixes, migration hardening, and Windows CI blockers being actively addressed. 12 issues and 17 PRs were closed/merged today, indicating strong forward momentum. The dominant theme is **Reborn migration integrity and delivery-layer correctness**, with significant work on making the 1.0.0-rc.1 → 1.1.0-rc.1 upgrade lossless.

## 2. Releases

**No new releases published today.** The current release candidates are:
- `ironclaw-v1.0.0-rc.1` (`82572157`)
- `ironclaw-v1.1.0-rc.1` (`ae1dc117`)

PR [#5598](https://github.com/nearai/ironclaw/pull/5598) recently shipped `ironclaw_common` 0.4.2→0.5.0 and `ironclaw_skills` 0.3.0→0.4.0 with API-breaking changes. The team is actively working on ensuring the upgrade path between rc versions is lossless (see #7178 / #7198).

## 3. Project Progress

### Merged / Closed Today

| Item | Description |
|------|-------------|
| [PR #7200](https://github.com/nearai/ironclaw/pull/7200) | **Fixed** Windows `icacls` writing to CLI stdout — fourth Windows defect blocking `v1.1.0-rc.1` |
| [PR #7197](https://github.com/nearai/ironclaw/pull/7197) | **Fixed** CI passing Windows identity variables to release smoke tests |
| [PR #7167](https://github.com/nearai/ironclaw/pull/7167) | **Fixed** per-package clippy on bin-only crates; fixed `.gitignore` classification |
| [PR #7156](https://github.com/nearai/ironclaw/pull/7156) | **Merged** Enforcement: same-layer edge inventory, composition absolute-LOC ceiling, D-E vendor census, ratchet slack |
| [PR #7181](https://github.com/nearai/ironclaw/pull/7181) | **In progress** — Waves 0–4 batch 2: adapter-registry move, registered-to-zero, accumulating the fleet |
| [PR #7198](https://github.com/nearai/ironclaw/pull/7198) | **In progress** — Preserve rc1 state during 1.1 startup migration (stacked on #7178) |
| [PR #7157](https://github.com/nearai/ironclaw/pull/7157) | **In progress** — Explicit channel delivery tool with two-lane model (conversation lifecycle + notification channels) |

### Key Advances
- **Migration hardening:** PR #7198 directly addresses issue #7178, ensuring all threads, append-only messages, channel roots, OAuth aliases, and extension installations survive the rc1→rc2 upgrade.
- **Windows stability:** Two PRs (#7197, #7200) resolved consecutive Windows blockers for the v1.1.0-rc.1 release.
- **CI/Clippy fixes:** PR #7167 unblocked the clippy gate that was failing on bin-only packages, and issue #7119 highlighted a package-set-dependent clippy configuration issue now resolved.
- **Documentation:** PR #6965 added IronHub docs (3 pages); PR #6970 upgraded V1 documentation and removed legacy "Reborn" terminology from public-facing content.

## 4. Community Hot Topics

| Issue/PR | Comments | Status | Focus |
|----------|----------|--------|-------|
| [#6284](https://github.com/nearai/ironclaw/issues/6284) — error-recoverability endgame | 15 | Closed | Model must recover from 100% of mid-run errors per recoverability contract |
| [#6524](https://github.com/nearai/ironclaw/issues/6524) — Hermetic testing platform | 4 | Closed | Deterministic, meaningful coverage for every capability and user journey |
| [#7119](https://github.com/nearai/ironclaw/issues/7119) — Clippy package-set-dependent | 4 | Closed | `main` was red for `{ironclaw, ironclaw_reborn_config}` clippy checks |
| [#6752](https://github.com/nearai/ironclaw/issues/6752) — Instance deletion stuck | 3 | Open | "Loading your agents..." hangs on re-login after instance deletion attempt |
| [#7145](https://github.com/nearai/ironclaw/issues/7145) — WS2 extension_host re-layer | 3 | Open | Correct sizing of `products → loops` flip from four-port residue |

**Analysis:** The top-voted closed issues (#6284, #6524) are both **epics** targeting fundamental reliability guarantees — error recoverability and test coverage. This signals the community and maintainers are prioritizing **production-readiness** over feature expansion. The instance deletion bug (#6752) drawing 3 comments indicates a painful user-facing block that remains unresolved.

## 5. Bugs & Stability

### Critical / High Severity

| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#7197](https://github.com/nearai/ironclaw/issues/7197) [CLOSED via #7197] | Windows identity variables not passed to release smoke — release blocker | ✅ PR #7197 merged |
| [#7200](https://github.com/nearai/ironclaw/issues/7200) [CLOSED via #7200] | `icacls` writing to CLI stdout on Windows — fourth blocking defect for rc.1 | ✅ PR #7200 merged |
| [#6752](https://github.com/nearai/ironclaw/issues/6752) | Instance deletion fails; "Loading your agents..." stuck on re-login | 🔴 No fix PR yet |
| [#7168](https://github.com/nearai/ironclaw/issues/7168) [CLOSED] | Agent-installed skills invisible — `skill_install` writes where discovery doesn't read | ✅ Closed |
| [#7148](https://github.com/nearai/ironclaw/issues/7148) [CLOSED] | `conversations → turns` migration has no owning CHECKLIST row; unreachable milestone | ✅ Closed |

### Medium Severity

| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#7192](https://github.com/nearai/ironclaw/issues/7192) | Optimistic user messages render below agent output in WebUI — conversation reads out of order | 🔴 Open |
| [#7191](https://github.com/nearai/ironclaw/issues/7191) | `builtin.time` lacks relative-offset arithmetic; opaque `input_error()` in production | 🔴 Open |
| [#7104](https://github.com/nearai/ironclaw/issues/7104) | Extractors report "no text found" as `Failed` instead of `Empty` — model receives wrong signal | 🔴 Open |
| [#7146](https://github.com/nearai/ironclaw/issues/7146) | 121 sites use `target = "…"` (field) instead of `target: "…"` (metadata) — events invisible to filters | 🔴 Open |
| [#7115](https://github.com/nearai/ironclaw/issues/7115) | Docker entrypoint gates legacy-Slack migration on dead env var — migration skipped per docs | 🔴 Open |
| [#7103](https://github.com/nearai/ironclaw/issues/7103) | Latency-trace field computed even when tracing is disabled (coding tool JSON byte count) | 🔴 Open |

**Assessment:** The Windows release blockers are resolved, which is positive for the v1.1.0-rc.1 timeline. However, **121 tracing-target bugs** (#7146) and the **extractor misclassification** (#7104) are systemic issues that could affect production observability. The instance deletion hang (#6752) remains unaddressed and is a high-visibility UX bug.

## 6. Feature Requests & Roadmap Signals

| Issue | Priority | Description | Likely in v1.1? |
|-------|----------|-------------|-----------------|
| [#7194](https://github.com/nearai/ironclaw/issues/7194) | Enhancement, M, high risk | Admin-allowed shared channel as outbound delivery target | ⚠️ Possible — scope is extensions |
| [#7193](https://github.com/nearai/ironclaw/issues/7193) | Enhancement, L, medium risk | `run-now` (manual fire) for automations across WebUI/model/product | ⚠️ Possible — large scope |
| [#7177](https://github.com/nearai/ironclaw/issues/7177) | Enhancement, P2 | Schema-aware ranked search for deferred tool retrieval | ✅ Likely — directly improves Reborn tool disclosure |
| [#6731](https://github.com/nearai/ironclaw/issues/6731) | Epic, v1.1.0 | Integrate IronHub into IronClaw | ✅ In progress — PR #6965 docs already merged |
| [#7183](https://github.com/nearai/ironclaw/issues/7183) | Enhancement | Per-user LLM model selection (currently admin-only) | ❌ Unlikely — flagged from Champions feedback, may defer to v1.2 |
| [#7105](https://github.com/nearai/ironclaw/issues/7105) | Feedback | Dedicated identity/session & payments service for cloud API | ❌ Architectural refactor — likely v1.2+ |

**Roadmap Signal:** The project is clearly prioritizing **reliability and migration correctness** for v1.1.0, with feature work confined to the delivery-tool redesign (#7157), skill discovery epic (#6565 / #6941), and IronHub integration. Per-user model selection and payments microservice are user-requested but appear deferred.

## 7. User Feedback Summary

**Pain points reported in Champions check-in (2026-07-23):**

1. **Memory not reliably recalled across conversations** (#7185) — Multiple testers independently observed that context established in one conversation is lost in later ones. This is a **core UX reliability issue** affecting multi-turn agent usefulness.

2. **Web scraping is hit-or-miss** (#7180) — Agent inconsistently uses `http` tool vs `web_search` for data retrieval; some sources succeed, others fail with no clear pattern. Users need predictable data-gathering behavior.

3. **Per-user LLM model selection** (#7183) — Users want control over which model powers their agent, but selection is admin-only. This was raised by Jeremy Koch (marketing) in the Champions call.

4. **Skill selection observability** (#7199) — A contributor building "FaceSeek" suggested logging whether a candidate skill existed but wasn't chosen vs. was chosen and changed the outcome. This helps prove skill ROI after selection cost — a **meta-level feedback** on the skill discovery system.

**Satisfaction indicators:** The high volume of closed issues (#6284, #6524, #7168, #7148) and the resolution of Windows blockers suggests the team is responsive. However, the instance deletion hang (#6752) and memory recall issues (#7185) are **high-visibility pain points** that could erode trust if not addressed soon.

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|----------------------|
| [#6752](https://github.com/nearai/ironclaw/issues/6752) — Instance deletion stuck | 8 days | User-facing hang with no fix PR; blocks clean instance lifecycle |
| [#6565](https://github.com/nearai/ironclaw/issues/6565) — Reliable Skill Discovery epic | 13 days | 21 acceptance criteria, 4 belonging to other open work; overly large for one person |
| [#3773](https://github.com/nearai/ironclaw/issues/3773) — Target Crate Architecture | 78 days | Epic labeled v1.2.0; governs physical crate layout, dependency graph, CI enforcement — foundational but uncompleted |
| [#7193](https://github.com/nearai/ironclaw/issues/7193) — Manual automation fire | 1 day | Large-scope enhancement with no PR yet; users cannot trigger automations on demand

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-05

---

## 1. Today's Overview

LobsterAI shows **active but focused development** today, with 15 PRs updated and 1 open issue in the last 24 hours. No new releases were published, though PR #2430 merged the `release/2026.8.3` branch into `main`, indicating the team is in a post-release stabilization phase. The majority of today's activity (11 PRs closed) centers on polishing the startup credit campaign experience, dependency updates, and minor UX fixes — suggesting the project is riding the tailwind of a recent feature rollout rather than initiating new major work.

---

## 2. Releases

**No new releases today.** PR #2430 (`https://github.com/netease-youdao/LobsterAI/pull/2430`) merged the `release/2026.8.3` branch into `main`, which introduced:

- Native credit-reward activities
- Streamlined first-run login experience
- Artifact auto-preview control
- Improved model-error handling
- Windows installer reliability fixes

No breaking changes or migration notes were reported for this cycle.

---

## 3. Project Progress

**Merged / Closed PRs Today (11):**

| PR | Area | Summary |
|----|------|---------|
| [#2433](https://github.com/netease-youdao/LobsterAI/pull/2433) | renderer | Polished startup credit campaign — cropped poster assets, localized failure messages, pre-retry campaign binding refresh |
| [#2432](https://github.com/netease-youdao/LobsterAI/pull/2432) | renderer | Disabled auto-popup of World Cup final reward poster; preserved manual claiming flow |
| [#2428](https://github.com/netease-youdao/LobsterAI/pull/2428) | renderer/main | Completed startup credit campaign analytics — full redirect URL reporting, error message coverage, Electron auth IPC update |
| [#2427](https://github.com/netease-youdao/LobsterAI/pull/2427) | renderer/cowork | Bundled startup credit campaign artwork locally; server retains control over availability and timing |
| [#2426](https://github.com/netease-youdao/LobsterAI/pull/2426) | renderer/main | Separated model capacity overload errors from generic rate-limit messages via `ModelOverloaded` classification |
| [#2429](https://github.com/netease-youdao/LobsterAI/pull/2429) | renderer/cowork | Optimized login page |
| [#2425](https://github.com/netease-youdao/LobsterAI/pull/2425) | renderer/cowork | Added artifact auto-preview toggle in settings |
| [#1282](https://github.com/netease-youdao/LobsterAI/pull/1282) | deps | Bumped `@headlessui/react` 1.7.19 → 2.2.9 |
| [#1283](https://github.com/netease-youdao/LobsterAI/pull/1283) | deps | Bumped `react` 18.3.1 → 19.2.4 |
| [#1284](https://github.com/netease-youdao/LobsterAI/pull/1284) | deps | Bumped `react-syntax-highlighter` 15.6.6 → 16.1.1 |
| [#2430](https://github.com/netease-youdao/LobsterAI/pull/2430) | release | Merged `release/2026.8.3` → `main` |

**Key takeaways:** The team is investing heavily in the **startup credit campaign** polish (PRs #2433, #2432, #2428, #2427) and **dependency modernization** (React 19, Headless UI 2). The model error handling improvement (#2426) addresses a real user confusion point.

---

## 4. Community Hot Topics

**Most Discussed / Active:**

1. **[Issue #1202](https://github.com/netease-youdao/LobsterAI/issues/1202)** — *Agent leaks model key information, security risk* — Open, stale, 1 comment. User `blueb0ne` reports that the agent reveals configuration file paths and environment variable details when asked, enabling sequential probing to extract actual model API keys. **Zero reactions.** This is a **security-critical** issue with no assigned fix yet.

2. **[PR #2374](https://github.com/netease-youdao/LobsterAI/pull/2374)** — *Permanent setting to hide sidebar ad banner* — Open since 2026-07-21. Adds a user-facing toggle in Settings → General, addressing [Issue #2342](https://github.com/netease-youdao/LobsterAI/issues/2342). Users have long complained about the inability to permanently dismiss ads; this PR directly answers that need.

3. **[PR #1205](https://github.com/netease-youdao/LobsterAI/pull/1205)** — *Show error toast when session rename fails* — Open, stale. Handles silently swallowed rename failures. Low severity but high usability impact.

**Underlying trend:** The community is most vocal about **privacy/security** (#1202) and **UX control over ads** (#2374). These represent the two strongest signals from users: trust and autonomy.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| 🔴 **High** | [Issue #1202](https://github.com/netease-youdao/LobsterAI/issues/1202) | Agent leaks model key / config info — potential credential exposure | None yet |
| 🟡 **Medium** | [PR #1205](https://github.com/netease-youdao/LobsterAI/pull/1205) | Session rename failures are silently swallowed; no user feedback | #1205 (open) |
| 🟢 **Low** | Model overload errors shown as generic rate-limit | Misleading users into immediate retry | #2426 (merged) |

**Note:** The merged PR #2426 addresses the model overload / rate-limit confusion. No new crash reports or regressions surfaced today.

---

## 6. Feature Requests & Roadmap Signals

- **Permanent ad banner control** ([PR #2374](https://github.com/netease-youdao/LobsterAI/pull/2374)): Directly user-requested; likely to be merged given the clear issue reference (#2342).
- **Artifact auto-preview toggle** ([PR #2425](https://github.com/netease-youdao/LobsterAI/pull/2425)): Added in the latest release cycle — shows responsiveness to power-user workflow needs.
- **React 19 migration** ([PR #1283](https://github.com/netease-youdao/LobsterAI/pull/1283)): Major dependency upgrade already in progress; signals commitment to staying current.
- **World Cup campaign auto-popup suppression** ([PR #2432](https://github.com/netease-youdao/LobsterAI/pull/2432)): Suggests the team is iterative-closing on promotional features based on user feedback.

**Prediction for next version:** Expect further hardening of the credit campaign flows, the React 19 upgrade to land fully, and a security patch addressing [Issue #1202](https://github.com/netease-youdao/LobsterAI/issues/1202).

---

## 7. User Feedback Summary

- **Pain point — key leakage:** Users are concerned that the agent's conversational interface can be socially engineered into revealing sensitive configuration. This undermines trust in the tool's security posture.
- **Pain point — ads:** Persistent sidebar ad banners with no permanent dismissal option are a recurring frustration; [PR #2374](https://github.com/netease-youdao/LobsterAI/pull/2374) is a direct response.
- **Pain point — silent failures:** Session rename failures without feedback cause confusion ([PR #1205](https://github.com/netease-youdao/LobsterAI/pull/1205)).
- **Satisfaction signal:** The model overload vs. rate-limit distinction (#2426) shows the team is listening to error-message confusion, a sign of improving observability.
- **Satisfaction signal:** Startup credit campaign artwork bundling (#2427) and analytics completeness (#2428) indicate investment in the freemium activation funnel, which users engaging with campaigns will appreciate.

---

## 8. Backlog Watch

| Item | Type | Age | Risk |
|------|------|-----|------|
| [Issue #1202](https://github.com/netease-youdao/LobsterAI/issues/1202) | Bug (Security) | ~4 months, stale | 🔴 **Critical** — unpatched credential leakage with no assigned fix |
| [PR #1205](https://github.com/netease-youdao/LobsterAI/pull/1205) | Bug (UX) | ~4 months, stale | 🟡 Medium — easy fix, high usability value |
| [PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | Chore (deps) | ~4 months, stale | 🟡 Low — Electron 40→43 + electron-builder upgrade pending |
| [PR #2374](https://github.com/netease-youdao/LobsterAI/pull/2374) | Feature | ~15 days, open | 🟡 Medium — ready for review, clear user demand |

**Recommendation:** Issue #1202 deserves immediate maintainer attention given its security implications. The stale Dependabot PRs (#1277, #1282–#1284) also warrant review to prevent dependency drift.

---

**Overall Project Health: 🟢 Good.** Active PR throughput (15 in 24h), clean release cadence (2026.8.3), and responsive dependency management. The primary risk is the unresolved security issue (#1202) and two stale PRs that could block maintenance momentum.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-05

## 1. Today's Overview

Moltis experienced minimal activity today, with no new issues opened or closed and no merged or closed pull requests. The only incoming change is a Dependabot-maintained dependency update (PR #1184) targeting the `/website` directory. The project appears to be in a low-activity phase with no releases or significant community engagement recorded over the past 24 hours.

## 2. Releases

**None.** No new releases were published today. The project has no recently tagged versions to report.

## 3. Project Progress

No PRs were merged or closed today. The sole open PR (#1184) is a routine dependency bump initiated by Dependabot, not a feature or bugfix contribution from the community. No features advanced or were fixed in the last 24 hours.

## 4. Community Hot Topics

No issues or PRs attracted significant community attention today. The only item, **PR #1184** ([dependabot/undici bump](https://github.com/moltis-org/moltis/pull/1184)), has zero comments and zero reactions. It reflects standard automated maintenance rather than community-driven discussion.

## 5. Bugs & Stability

**No bug reports were filed today.** There are no known crashes, regressions, or stability issues reported in the last 24 hours.

## 6. Feature Requests & Roadmap Signals

**None identified today.** No new feature requests or roadmap-related discussions were opened. The absence of feature-oriented issues suggests the community is not currently raising new enhancement proposals.

## 7. User Feedback Summary

No user feedback was collected today. The lack of issue activity means there are no new pain points, use cases, or satisfaction signals to report from the user base at this time.

## 8. Backlog Watch

**No backlog items flagged today.** With zero open issues and zero merged/closed PRs in the review period, there are no long-unanswered items requiring immediate maintainer attention. The Dependabot PR #1184 remains open but is a low-priority routine update with no urgency.

---

**Overall Health Assessment:** Low. The project is currently in a quiet state with only automated dependency maintenance activity. No active development, bug resolution, or community engagement was observed in the reporting window.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-05

## 1. Today's Overview

QwenPaw showed strong development velocity on 2026-08-05 with **29 issues** and **46 PRs** updated in the last 24 hours, indicating an active contributor base and responsive maintainers. The project remains in the **v2.1.0-beta.1** cycle, with no new release published today. Activity is concentrated on channel reliability fixes (Matrix, WeChat, OneBot), desktop stability (Windows Tauri crashes), and memory/compression edge cases. The overall health signal is positive: high PR throughput with a healthy open/closed ratio (~1.4:1), though several critical desktop and plugin bugs require attention before the stable v2.1.0 launch.

## 2. Releases

**No new releases published.** The latest version remains **v2.1.0-beta.1** (released 2026-08-03). The release-duty verification issue [#6656](https://github.com/agentscope-ai/QwenPaw/issues/6656) was closed, confirming the beta passed its installation checks across platforms.

## 3. Project Progress

### Merged / Closed Today

| Item | Type | Summary |
|---|---|---|
| [PR #6692](https://github.com/agentscope-ai/QwenPaw/pull/6692) | Bug fix | Stops logging raw conversation command arguments at INFO level; adds regression coverage for `/compact` hint redaction |
| [PR #6688](https://github.com/agentscope-ai/QwenPaw/pull/6688) | Bug fix | Fixes plugin namespace isolation — bare absolute imports now correctly scoped per plugin (closes #6683) |
| [PR #6685](https://github.com/agentscope-ai/QwenPaw/pull/6685) | Bug fix | Corrects naive-UTC timestamp timezone conversion bug (#6301) |
| [PR #6678](https://github.com/agentscope-ai/QwenPaw/pull/6678) | CI fix | Installs Playwright Chromium for integration test suite |
| [PR #6686](https://github.com/agentscope-ai/QwenPaw/pull/6686) | Test fix | Adds missing p-tier markers to integration tests, closing gate coverage holes |
| [PR #6679](https://github.com/agentscope-ai/QwenPaw/pull/6679) | Test fix | Aligns `import-local` with source-guard restriction and widens flaky poll window |
| [PR #6628](https://github.com/agentscope-ai/QwenPaw/pull/6628) | Bug fix | Uses `SystemMsg` for compressed memory placeholder in `_rebuild_context`, fixing DeepSeek 400 errors |
| [PR #4267](https://github.com/agentscope-ai/QwenPaw/pull/4267) | Feature | macOS file path whitelist with `sandbox-exec` pre-hook — **under review** |

### Key Open PRs Advancing

- **[PR #6645](https://github.com/agentscope-ai/QwenPaw/pull/6645)** — Major desktop OS enhancement: full-screen, menu bar, Dock, Launchpad, Spaces, Mission Control, notification center, and desktop context menus. Unified app registration for App Store, local apps, and PawApp plugins.
- **[PR #6691](https://github.com/agentscope-ai/QwenPaw/pull/6691)** — Persists cron `enabled` state on pause/resume (closes #6690).
- **[PR #6689](https://github.com/agentscope-ai/QwenPaw/pull/6689)** — Adds opt-in startup retry contract for channels with exponential backoff (addresses #6684).
- **[PR #6504](https://github.com/agentscope-ai/QwenPaw/pull/6504)** — Unifies project directory resolution and hardens file workspace across coding-enabled agent sessions.
- **[PR #6676](https://github.com/agentscope-ai/QwenPaw/pull/6676)** — Secures OneBot by binding loopback by default and requiring token when exposed.

## 4. Community Hot Topics

| Issue | Comments | Theme |
|---|---|---|
| [#6649](https://github.com/agentscope-ai/QwenPaw/issues/6649) — GPT-5.6 prompt caching support | 13 | Cost/latency optimization for multi-turn agents |
| [#6655](https://github.com/agentscope-ai/QwenPaw/issues/6655) — Console channel silent timeout on approval | 12 | UX gap: approval prompts invisible in non-Web channels |
| [#6643](https://github.com/agentscope-ai/QwenPaw/issues/6643) — Task output directory organization | 6 | File management usability |
| [#6667](https://github.com/agentscope-ai/QwenPaw/issues/6667) — DeepSeek thinking mode `reasoning_content` missing | 5 | Model compatibility with OpenAI formatter |
| [#6642](https://github.com/agentscope-ai/QwenPaw/issues/6642) — Direct file path read on drag-drop (closed) | 5 | Performance/UX for file handling |

**Analysis:** The top-voted issues reflect two dominant user needs: **(1) cost and latency optimization** (prompt caching, multi-model parallel execution in #6455), and **(2) cross-channel consistency** — users expect approval flows, file handling, and UI behaviors to work identically across Web, Console, WeChat, and Matrix. The DeepSeek thinking-mode issue (#6667) signals growing adoption of reasoning models and the need for formatter parity.

## 5. Bugs & Stability

### 🔴 Critical

| Issue | Description | Fix PR |
|---|---|---|
| [#6697](https://github.com/agentscope-ai/QwenPaw/issues/6697) | v2.1.0b1 desktop injects `PYTHONHOME` into child env → every Python subprocess crashes (`ModuleNotFoundError: encodings`) | None yet |
| [#6698](https://github.com/agentscope-ai/QwenPaw/issues/6698) | v2.1.0b1 Browser SDK `open()` always fails with `WireProtocolError: Target crashed` (isolated Playwright session) | [PR #6669](https://github.com/agentscope-ai/QwenPaw/pull/6669) in progress |
| [#6696](https://github.com/agentscope-ai/QwenPaw/issues/6696) | WeChat iLink: one-time `context_token` consumed by typing indicator → replies rejected (`ret=-2`), "working" indicator stuck | None yet |
| [#6695](https://github.com/agentscope-ai/QwenPaw/issues/6695) | Approval prompts unreachable when using WeChat channel only (auto-deny after 5 min) | Closed as wontfix/design limitation |

### 🟠 High

| Issue | Description | Fix PR |
|---|---|---|
| [#6700](https://github.com/agentscope-ai/QwenPaw/issues/6700) | Huge tool output (MBs) freezes web session on reload and risks context window overflow | None yet — feature request for truncation/pagination |
| [#6683](https://github.com/agentscope-ai/QwenPaw/issues/6683) | App Center plugin install fails: `utils` namespace collision (`No module named 'utils.env'`) | ✅ [PR #6688](https://github.com/agentscope-ai/QwenPaw/pull/6688) merged |
| [#6690](https://github.com/agentscope-ai/QwenPaw/issues/6690) | `cron pause/resume` state not persisted across restarts | ✅ [PR #6691](https://github.com/agentscope-ai/QwenPaw/pull/6691) open |
| [#6687](https://github.com/agentscope-ai/QwenPaw/issues/6687) | OpenRouter multimodal probe overwrites documented capabilities with `false` | None yet |

### 🟡 Medium

| Issue | Description | Fix PR |
|---|---|---|
| [#6624](https://github.com/agentscope-ai/QwenPaw/issues/6624) | Auto-compression (Scroll) does not trigger `summarize_when_compact` memory flow | ✅ [PR #6629](https://github.com/agentscope-ai/QwenPaw/pull/6629) under review |
| [#6667](https://github.com/agentscope-ai/QwenPaw/issues/6667) | DeepSeek V4 Pro: `reasoning_content` missing after OpenAI formatter skips ThinkingBlock | None yet |
| [#6301](https://github.com/agentscope-ai/QwenPaw/issues/6301) | Naive UTC timestamps treated as local time → incorrect session display | ✅ [PR #6685](https://github.com/agentscope-ai/QwenPaw/pull/6685) merged |
| [#5906](https://github.com/agentscope-ai/QwenPaw/issues/5906) | Anti-duplicate feature falsely triggers Doom loop on normal conversations | Closed |

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Likelihood for v2.1.0 |
|---|---|---|
| [#6699](https://github.com/agentscope-ai/QwenPaw/issues/6699) | **On-demand skill loading** — currently all 27+ skills consume 8-10K tokens in system prompt | High (directly addresses token budget pain) |
| [#6649](https://github.com/agentscope-ai/QwenPaw/issues/6649) | **GPT-5.6 prompt caching** — `prompt_cache_key`/`prompt_cache_options`/`prompt_cache_breakpoint` support | Medium (provider-specific, lower priority) |
| [#6455](https://github.com/agentscope-ai/QwenPaw/issues/6455) | **Multi-model parallel execution** — run multiple models independently and aggregate results | Medium (complex architecture change) |
| [#6694](https://github.com/agentscope-ai/QwenPaw/issues/6694) | **Global rules** — project-level `.agent`/`.claude`-style system prompt override | Low-Medium |
| [#6490](https://github.com/agentscope-ai/QwenPaw/issues/6490) | **New providers** — Volcengine Agent Plan & Xiaomi MiMo Standard API | Medium (straightforward integration) |
| [#6674](https://github.com/agentscope-ai/QwenPaw/issues/6674) | **Free-tier rate-limit handling** — better 429 recovery for deepseek-v4-flash | High (quality-of-life for free users) |

**Predicted v2.1.0 candidates:** On-demand skill loading (#6699), rate-limit resilience (#6674), cron state persistence (#6691), and channel retry logic (#6689) are the strongest signals for the next stable release.

## 7. User Feedback Summary

**Pain points:**
- **Desktop v2.1.0b1 regressions** are the dominant complaint: Python subprocess crashes (#6697), browser tool failures (#6698), and WeChat token exhaustion (#6696) are blocking adoption of the new desktop build.
- **Console channel UX gaps**: approval prompts are invisible (#6655), causing silent 300s timeouts that confuse users.
- **File handling friction**: drag-and-drop uploads create redundant copies in `media/` (#6642, now closed), and large tool outputs freeze the web UI (#6700).
- **Token waste from skills**: users with 27+ skills report 25-30% of the system prompt consumed by skill descriptions alone (#6699).
- **Free-tier rate limits** interrupt long-running tasks with deepseek-v4-flash (#6674).

**Satisfaction signals:**
- Multiple users praise the overall experience ("great personal AI assistant") despite rough edges (#6674).
- The WeChat channel works well when not exclusively used (#6695).
- App Center plugin ecosystem is growing, though namespace collisions remain (#6683).

## 8. Backlog Watch

| Issue | Age | Priority | Status |
|---|---|---|---|
| [#6697](https://github.com/agentscope-ai/QwenPaw/issues/6697) — Python subprocess crash in v2.1.0b1 | 1 day | 🔴 Critical | No fix PR |
| [#6698](https://github.com/agentscope-ai/QwenPaw/issues/6698) — Browser SDK `Target crashed` | 1 day | 🔴 Critical | [PR #6669](https://github.com/agentscope-ai/QwenPaw/pull/6669) open |
| [#6696](https://github.com/agentscope-ai/QwenPaw/issues/6696) — WeChat `context_token` exhaustion | 2 days | 🔴 Critical | No fix PR |
| [#6700](https://github.com/agentscope-ai/QwenPaw/issues/6700) — Huge output freezes session | <1 day | 🟠 High | No fix PR |
| [#6687](https://github.com/agentscope-ai/QwenPaw/issues/6687) — OpenRouter multimodal probe overwrites capabilities | 2 days | 🟡 Medium | No fix PR |
| [#6624](https://github.com/agentscope-ai/QwenPaw/issues/6624) — Auto-compression doesn't trigger summarize | 5 days | 🟡 Medium | [PR #6629](https://github.com/agentscope-ai/QwenPaw/pull/6629) under review |
| [#6649](https://github.com/agentscope-ai/QwenPaw/issues/6649) — GPT-5.6 prompt caching | 3 days | 🟡 Medium | No fix PR |
| [#4267](https://github.com/agentscope-ai/QwenPaw/pull/4267) — macOS sandbox-exec file whitelist | 54 days | — | Still under review |

**Maintainer attention needed:** The three critical bugs in v2.1.0b1 (#6697, #6698, #6696) are blocking the path to a stable desktop release. PR #6669 addresses one but #6697 (PYTHONHOME injection) and #6696 (WeChat token) remain unassigned. The long-pending PR #4267 (macOS sandbox) has been under review for nearly 2 months.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026‑08‑05

## 1. Today's Overview
ZeroClaw shows **high development velocity** with 42 issues and 50 pull requests updated in the last 24 hours. Activity is dominated by **RFC‑level architectural discussions** (goal mode, chat‑completions profile, session ownership, security overlays) rather than routine bug fixes. No new releases were published today, indicating the maintainers are focusing on design consolidation before the next version. The project’s health is strong: a robust pipeline of community‑driven proposals, active security‑focused PRs, and clear maintainers’ decision queues.

## 2. Releases
*No new releases were published in the last 24 hours.*

## 3. Project Progress
- **Two PRs were merged/closed** today (details not listed in the summary data).  
- **Closed RFC:** #8568 (Mixture‑of‑Agents virtual model provider) reached a resolution, moving the MoA design out of active discussion.  
- **Feature advancement:** Several RFCs progressed through revisions (#7155, #9488, #9487), indicating steady design‑phase momentum for security, attachment, and session‑ownership architectures.  
- **Security‑focused fixes landed:**  
  - #9410 – Defaults command‑audit logging to disabled (security‑honesty direction).  
  - #9362 – Fixes arbitrary file‑write escape in the browser‑tool screenshot action.  
  - #9320 – Adds wall‑clock timeout to cron agent jobs, preventing lock‑holding hangs.

## 6. Bugs & Stability
| Severity | Issue / PR | Summary | Fix Status |
|----------|------------|---------|------------|
| **P0** | [#9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) | Gateway webhook handlers do not fail closed (WhatsApp Cloud, Linq, WATI) – data‑loss/security risk. | No fix PR listed. |
| **P1** | [#9647](https://github.com/zeroclaw-labs/zeroclaw/issues/9647) | Knowledge graph lacks per‑agent attribution; any agent can read/mutate another’s knowledge. | No fix PR listed. |
| **P1** | [#9646](https://github.com/zeroclaw-labs/zeroclaw/issues/9646) | Session/channel read+write tools lack per‑agent ownership scoping (sessions, Discord search). | No fix PR listed. |
| **P1** | [#9362](https://github.com/zeroclaw-labs/zeroclaw/pull/9362) | Fixes arbitrary file‑write escape in browser‑tool screenshot path validation. | **PR open**, awaiting merge. |
| **P1** | [#9410](https://github.com/zeroclaw-labs/zeroclaw/pull/9410) | Defaults command‑audit logging to disabled (security‑honesty fix). | **PR open**, awaiting merge. |
| **P1** | [#9320](https://github.com/zeroclaw-labs/zeroclaw/pull/9320) | Bounds cron agent jobs with a wall‑clock timeout to release sqlite locks. | **PR open**, awaiting merge. |

**Stability note:** Three critical security bugs (P0/P1) lack immediate fix PRs, signaling a potential backlog in patching. The project’s security‑RFC work (#7141, #7142, #6971) may address these systematically.

## 7. Feature Requests & Roadmap Signals
| RFC / Tracker | Link | Signal |
|---------------|------|--------|
| Goal mode v1 (bounded foreground Matrix work) | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | Core agent‑turn durability; high engagement. |
| Chat Completions profile (OpenAI‑protocol gateway) | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | Broad client compatibility (Open WebUI, LangChain, etc.). |
| Per‑execution confirmation tier for shell commands | [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | Security‑UX evolution; normative scope narrowed. |
| Unified attachment architecture | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | Cross‑channel media handling. |
| Decouple memory‑lifecycle from storage backends | [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | Persistent‑memory parity with peer runtimes. |
| Mixture‑of‑Agents (MoA) virtual provider | [#8568](https://github.com/zeroclaw-labs/zeroclaw/issues/8568) | **Closed** – design accepted/deferred. |
| Plugin‑owned Kanban board for agent work | [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) | Work‑coordination plugin ecosystem. |
| Replace React/Vite web UI with Rust→Wasm | [#8132](https://github.com/zeroclaw-labs/zeroclaw/issues/8132) | Build‑chain simplification; low‑priority (p3). |
| Deterministic precondition gates for cron jobs | [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | Cron reliability; accepted status. |

**Predicted next‑version inclusions:**  
- Chat Completions profile (if RFC advances to accepted).  
- Goal mode v1 (core agent‑turn feature).  
- Memory‑lifecycle decoupling (tracker #8891).  
- Security‑UX defaults and per‑agent scoping (driven by bug fixes).

## 8. User Feedback Summary
- **Security & ownership:** Repeated requests for per‑agent data isolation (knowledge graph, session tools) and robust sandbox policies. Users want “fail‑closed” defaults and clear audit trails.  
- **Interoperability:** Strong demand for OpenAI‑protocol compatibility (Chat Completions profile) to integrate with existing AI tooling (Open WebUI, Continue.dev, LangChain).  
- **Multi‑session & attachment handling:** Need for unified attachment architecture and persistent conversation sessions across channels.  
- **Tool‑call parsing:** Improvements for DeepSeek DSML, `<tools>`‑tag recovery, and vision‑model capability detection show users are working with diverse model providers.  
- **UX polish:** Terminal‑width fixes, transient‑frame viewport slicing, and context‑exhaustion notices indicate attention to CLI/WebUI usability.

## 9. Backlog Watch
| Issue | Link | Reason |
|-------|------|--------|
| Maintainer decision queue for RFCs | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker needs maintainer attention to clear the RFC pipeline. |
| Goal mode v1 RFC | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | High‑impact feature; 16 comments, needs‑maintainer‑review. |
| Chat Completions profile | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | 16 comments; critical for ecosystem adoption. |
| Security UX & credential boundaries | [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) | 9 comments; needs‑author‑action. |
| Persistent‑memory parity tracker | [#8891](https://github.com/zeroclaw-labs/zeroclaw/issues/8891) | Multi‑PR rollout; needs coordination. |
| P0/P1 security bugs (#9565, #9647, #9646) | [9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) / [9647](https://github.com/zeroclaw-labs/zeroclaw/issues/9647) / [9646](https://github.com/zeroclaw-labs/zeroclaw/issues/9646) | Critical bugs without visible fix PRs; require urgent maintainer review. |

**Overall:** ZeroClaw is in a **design‑heavy phase** with active community RFCs and a clear security‑first direction. The backlog of open RFCs and critical bugs indicates a need for maintainer bandwidth to advance proposals and patch vulnerabilities. The project’s health is strong, but the pace of security‑fix deployment should be monitored.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*