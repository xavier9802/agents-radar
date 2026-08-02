# OpenClaw Ecosystem Digest 2026-08-02

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-02 03:33 UTC

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

⚠️ Summary generation failed.

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date:** 2026-08-02  
**Scope:** 8 projects with digest data (OpenClaw, Hermes Agent, NullClaw, ZeptoClaw excluded due to failed/absent summaries)

## 1. Ecosystem Overview
The personal AI assistant open-source landscape is in a **maturity transition phase**, shifting from rapid feature prototyping to production hardening. Projects are concurrently addressing **memory lifecycle management**, **security/access‑control boundaries**, and **observability** while expanding provider and channel integrations. Activity velocity varies widely—from high‑frequency refactoring sprints to steady maintenance cycles—reflecting diverse deployment targets (self‑hosted, desktop, cloud) and user bases. The emergence of cross‑project themes (e.g., OrcaRouter support, OpenAI compatibility adapters, per‑account operator roles) indicates a converging technical stack around interoperability and operational reliability.

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Health Score | Key Focus |
|---------|--------------|-----------|---------|--------------|-----------|
| **NanoBot** | 5 | 25 | None | 🟢 Healthy | Session/cron stability, security hardening, WebUI UX |
| **NanoClaw** | 2 | 12 | v2.1.54 (rollup) | 🟢 Healthy | Channel unification (iMessage), rootless Docker, credential alerts |
| **IronClaw** | 12 | 22 | None | 🟢 Healthy (stressed) | Architectural refactoring (Wave 2), CI gate hardening, libSQL performance |
| **CoPaw (QwenPaw)** | 9 | 11 | None | 🟢 Healthy | Memory compression, provider alignment, critical bug fixes |
| **ZeroClaw** | 50 | 50 | None | 🔴 Stressed | Security RFCs, memory‑lifecycle redesign, eval‑system stack |
| **PicoClaw** | 1 | 3 | None | 🟡 Moderate | Provider expansion (Exa, OrcaRouter), localization, Matrix reliability |
| **LobsterAI** | 7 (closed) | 2 | None | 🟡 Moderate | i18n fixes, MCP HTTP transport, UI polish |
| **Moltis** | 0 | 3 | None | 🟢 Stable | Observability (Langfuse/OTLP), privilege‑boundary hardening, session UX |

**Health Score Legend:** 🟢 Healthy (active development, clear progress), 🟡 Moderate (steady but limited velocity or open backlog), 🔴 Stressed (high activity but bottlenecked or critical issues unresolved).

## 3. OpenClaw’s Position
*OpenClaw digest generation failed; analysis inferred from cross‑project references.*  
OpenClaw appears as a **core engine/reference implementation** mentioned in LobsterAI (“OpenClaw engine”) and PicoClaw (provider‑integration context). Its advantages over peers likely include:
- **Broad provider abstraction** – referenced by multiple projects as a compatibility layer.
- **MCP engine integration** – LobsterAI’s HTTP‑MCP gap suggests OpenClaw may already support SSE‑based MCP transports.
- **Established community** – implicit in its designation as “core reference.”

Technical approach differs from peers: while projects like NanoBot focus on session persistence and cron reliability, and IronClaw pursues deep architectural refactoring, OpenClaw’s role seems to be a **stable, interoperable backbone** that other agents build upon. Community size cannot be quantified from available data, but its reference status implies a significant user/developer base.

## 4. Shared Technical Focus Areas
| Focus Area | Projects Involved | Specific Needs |
|------------|-------------------|----------------|
| **Memory/Lifecycle Management** | NanoBot, ZeroClaw, CoPaw | Separation of conversation history from durable memory; auto‑compression triggers; eviction governance. |
| **Security & Access Control** | NanoBot, Moltis, ZeroClaw, NanoClaw | Per‑sender rate limiting, per‑account operator roles, credential‑expiry alerts, shell‑command confirmation tiers. |
| **Provider Interoperability** | PicoClaw, CoPaw, IronClaw, ZeroClaw | OrcaRouter multi‑vendor routing, OpenAI Chat Completions adapter, local‑provider keyword matching to prevent cloud‑model hijacking. |
| **Observability & Evaluation** | Moltis, ZeroClaw, CoPaw | Langfuse/OTLP instrumentation, eval‑system stack (JUnit, regression diffing), agent‑behavior traceability. |
| **Channel Reliability** | PicoClaw (Matrix), ZeroClaw (WhatsApp), NanoBot (cron) | Auto‑reconnection logic, silent‑failure prevention, output‑delivery mode fixes. |
| **Cross‑Session & Workspace UX** | NanoBot, ZeroClaw | Cross‑session search/`@`‑mentions, unified provider‑model routing, quick/temporary chat modes. |

## 5. Differentiation Analysis
| Project | Feature Focus | Target Users | Technical Architecture |
|---------|---------------|--------------|------------------------|
| **NanoBot** | Session persistence, cron reliability, WebUI polish, rate limiting | Self‑hosted operators, power users | Dense PR‑merge cycle; focus on stability hardening over new features. |
| **NanoClaw** | Channel unification (iMessage dual‑backend), rootless Docker, credential alerts | Multi‑provider users, security‑conscious deployers | Aggressive rollup releases; breaking‑change management (iMessage unification). |
| **IronClaw** | Architectural refactoring (Wave 2), CI gate hardening, libSQL performance recovery | Enterprise‑grade self‑hosted deployments | Structured sprint cycles; dependency inversion and contract segregation. |
| **CoPaw (QwenPaw)** | Memory compression, provider‑model alignment, desktop UX (hotkey, cleanup) | Desktop/long‑term users, storage‑sensitive workflows | Rapid bug‑fix cadence; 2.0‑release preparation with expanding contributor base. |
| **ZeroClaw** | Security RFCs, eval‑system stack, memory‑lifecycle redesign | Researchers, security‑focused operators | High‑velocity RFC discussion; bottlenecked at maintainer‑decision layer. |
| **PicoClaw** | Provider ecosystem expansion (Exa, OrcaRouter), localization (zh‑TW) | Multi‑lingual users, provider‑diverse deployments | Steady feature additions; moderate issue‑resolution velocity. |
| **LobsterAI** | i18n hardcoding fixes, MCP HTTP transport, UI polish | International users, MCP‑integration adopters | Focused maintenance; stale PRs indicate review bottlenecks. |
| **Moltis** | Observability (Langfuse/OTLP), privilege‑boundary hardening, session UX | Production‑oriented operators, multi‑tenant deployments | Low issue volume, high‑impact security/observability merges. |

## 6. Community Momentum & Maturity
**Tier 1 – High Velocity & Active Iteration**  
- **NanoBot, NanoClaw, IronClaw, CoPaw, ZeroClaw**  
  - Daily PR/issue counts >10; active bug fixing and feature development.  
  - ZeroClaw shows highest raw volume but faces maintainer‑decision bottlenecks.  
  - NanoClaw and IronClaw are in structured release/refactoring cycles.

**Tier 2 – Moderate & Steady Progress**  
- **PicoClaw, LobsterAI, Moltis**  
  - Lower PR/issue counts but targeted improvements (provider additions, security fixes, observability).  
  - Moltis is particularly stable with merged security/observability PRs and no new issues.

**Tier 3 – Low/No Recent Activity**  
- **OpenClaw, Hermes Agent, NullClaw, ZeptoClaw**  
  - Digest generation failed or no activity reported; cannot assess momentum.

**Maturity Indicators:**  
- **Release cadence:** NanoClaw (v2.1.54 rollup) leads; others rely on incremental PR merges.  
- **Bug‑fix ratio:** NanoBot and CoPaw show strong P1‑fix throughput; ZeroClaw has critical S1 bug open.  
- **Contributor diversity:** CoPaw notes several first‑time contributors; NanoBot has multiple authors.

## 7. Trend Signals
| Trend | Evidence from Community Feedback | Value for AI Agent Developers |
|-------|----------------------------------|-------------------------------|
| **Per‑session model switching** | NanoBot issue #5198; CoPaw provider‑alignment PRs | Users expect SaaS‑like flexibility; drives demand for dynamic provider routing. |
| **Plugin/channel installation robustness** | NanoBot #5205 (`ensurepip` missing); PicoClaw Matrix reconnection bug | Fresh‑install friction erodes trust; need for resilient runtime environments. |
| **Memory lifecycle separation** | ZeroClaw RFCs #9048, #9103; CoPaw auto‑compression fixes | Conflating history and durable memory causes bloat and eviction bugs; clear architecture required. |
| **Observability as production prerequisite** | Moltis Langfuse/OTLP merge; ZeroClaw eval‑system stack | Operators need traceability across providers and channels for debugging and compliance. |
| **Security hardening wave** | NanoBot rate‑limiting, Moltis privilege‑boundary fix, ZeroClaw security RFCs | Credential leaks, privilege escalation, and silent failures are top pain points; proactive hardening is expected. |
| **Cross‑session/workspace UX** | NanoBot cross‑session search/`@`‑mentions; CoPaw cleanup page | Multi‑agent and multi‑session workflows demand unified navigation and data management. |
| **Provider‑agnostic integration** | OrcaRouter additions (PicoClaw, CoPaw, IronClaw); OpenAI adapter (ZeroClaw) | Demand for routing through multi‑vendor APIs without manual custom‑provider setup. |
| **Rootless/container‑friendly deployments** | NanoClaw rootless Docker PR; ZeroClaw secure‑relay transport | Security‑conscious users require daemon‑owned CA, mutual TLS, and rootless support. |

**Strategic Takeaway:** The ecosystem is moving from **feature‑density** to **operational‑readiness**. Developers should prioritize memory‑lifecycle clarity, security‑boundary enforcement, and observability instrumentation. Projects that balance rapid iteration with maintainer‑decision efficiency (e.g., NanoBot, Moltis) are better positioned for sustained adoption than those with high RFC volume but low merge rates (e.g., ZeroClaw).

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-02

## 1. Today's Overview

NanoBot is in a high-velocity release cycle with **30 activity items** in the last 24 hours (5 issues, 25 PRs), indicating strong contributor momentum. The project is actively hardening its core — multiple P1 fixes were merged for session persistence, cron reliability, and message formatting, while new feature work is advancing WebUI UX and cross-session capabilities. No new releases were published in this window, suggesting changes are being batched. Activity is healthy and predominantly fix-oriented, with emerging feature contributions from multiple authors.

## 2. Releases

No new releases in the last 24 hours.

## 3. Project Progress

**Merged/Closed PRs today (11):**

- **#5183** — Cron manual runs now preserve completion state; fixes race between `CronService.run_job()` and concurrent WebUI/API reads ([link](https://github.com/HKUDS/nanobot/pull/5183))
- **#5208** — Dream cron job cursor now advances when durable changes are made, fixing repeated history reprocessing ([link](https://github.com/HKUDS/nanobot/pull/5208))
- **#5209** — WebUI sidebar selection highlight refactored to eliminate flicker ([link](https://github.com/HKUDS/nanobot/pull/5209))
- **#5153** — `MemoryStore._format_messages` now handles non-string timestamps and missing `role` fields in raw archive ([link](https://github.com/HKUDS/nanobot/pull/5153))
- **#5108** — Per-sender message rate limiting added across all channel adapters, closing a token-spend vulnerability ([link](https://github.com/HKUDS/nanobot/pull/5108))
- **#5199** — Pyright suppressions narrowed from file-level to line-level in CLI gateway and onboarding modules ([link](https://github.com/HKUDS/nanobot/pull/5199))
- **#5172** — Responses API reasoning state and compact context now preserved across tool calls and turns ([link](https://github.com/HKUDS/nanobot/pull/5172))
- **#5200** — `wait_for` targets in exec sessions now survive response truncation ([link](https://github.com/HKUDS/nanobot/pull/5200))
- **#5201** — Malformed persisted session summaries are now tolerated with graceful fallback ([link](https://github.com/HKUDS/nanobot/pull/5201))
- **#3732** — Local provider keyword matching now requires `api_base`, preventing silent hijacking of cloud-hosted models ([link](https://github.com/HKUDS/nanobot/pull/3732))
- **#5139** — Media paths preserved during session consolidation; fixes #5118 and #5135 ([link](https://github.com/HKUDS/nanobot/pull/5139))

**Key themes:** Stability hardening (cron, memory, session), security hardening (rate limiting, provider matching), and WebUI polish.

## 4. Community Hot Topics

| Item | Type | Comments | Focus |
|------|------|----------|-------|
| [#5185](https://github.com/HKUDS/nanobot/issues/5185) | Issue | 4 | Tool-call code leaking into responses |
| [#5205](https://github.com/HKUDS/nanobot/issues/5205) | Issue | 2 | Feishu plugin enable fails — missing `ensurepip` |
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | Issue | 1 | Cannot change models per-session without full reconfig |
| [#5163](https://github.com/HKUDS/nanobot/issues/5163) | Issue | 0 | Cron manual runs lose completion state (fixed in #5183) |
| [#5210](https://github.com/HKUDS/nanobot/pull/5210) | PR | — | Trusted proxy auth for WebUI bootstrap |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | PR | — | Cross-session search and `@` mentions |

**Analysis:** The most discussed issues center on **model switching UX** (#5198) and **plugin installation reliability** (#5205). Users expect SaaS-like flexibility (per-session model changes, one-command channel enable). The community is actively engaging with PRs that expand WebUI capabilities (#5210, #5211), signaling demand for richer collaboration and deployment flexibility.

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| **P1** | [#5185](https://github.com/HKUDS/nanobot/issues/5185) | Tool-call code injected into response text | Open — no fix yet |
| **P1** | [#5205](https://github.com/HKUDS/nanobot/issues/5205) | `ensurepip` missing prevents feishu plugin install | Open — no fix yet |
| **P1** | #5163 (closed) | Cron manual runs lose completion state | ✅ Fixed in [#5183](https://github.com/HKUDS/nanobot/pull/5183) |
| **P1** | #5118/#5135 (closed) | Media paths dropped during session consolidation | ✅ Fixed in [#5139](https://github.com/HKUDS/nanobot/pull/5139) |
| **P2** | [#4801](https://github.com/HKUDS/nanobot/issues/4801) | `KeyError` on malformed session entries missing `role` | ✅ Fixed in [#5153](https://github.com/HKUDS/nanobot/pull/5153) |
| **P2** | [#5198](https://github.com/HKUDS/nanobot/issues/5198) | Model switching per-session not possible | Open — feature gap |
| **P2** | #5206 (open) | Streamed responses logged twice | PR [#5206](https://github.com/HKUDS/nanobot/pull/5206) open |
| **P2** | #5201 (closed) | Malformed `_last_summary` crashes `AutoCompact` | ✅ Fixed in [#5201](https://github.com/HKUDS/nanobot/pull/5201) |
| **P2** | #5200 (closed) | `wait_for` targets lost on response truncation | ✅ Fixed in [#5200](https://github.com/HKUDS/nanobot/pull/5200) |

**Assessment:** The project is actively resolving its critical bug surface. Two open P1 issues (#5185, #5205) remain unaddressed and should be prioritized. The duplicate-log issue (#5206) is in review.

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Prediction |
|--------|--------|------------|
| Cross-session search & mentions (`@`) | [#5211](https://github.com/HKUDS/nanobot/pull/5211) | Likely in next minor release; high user demand for workspace navigation |
| Quick Chat & Temporary Chat | [#5184](https://github.com/HKUDS/nanobot/pull/5184) | Likely in next minor release; addresses casual/ad-hoc use cases |
| Trusted proxy bootstrap auth | [#5210](https://github.com/HKUDS/nanobot/pull/5210) | Likely in next minor release; needed for Cloudflare Tunnel deployments |
| Model preset switching discoverability | [#5202](https://github.com/HKUDS/nanobot/pull/5202) | Likely in next minor release; directly addresses #5198 complaint |
| Subagent model presets | [#5207](https://github.com/HKUDS/nanobot/pull/5207) | Possible in next release; enables finer-grained agent orchestration |
| Well-known `skills.sh` sources | [#5186](https://github.com/HKUDS/nanobot/pull/5186) | Possible; expands skill ecosystem discovery |
| Per-user rate limiting | [#5108](https://github.com/HKUDS/nanobot/pull/5108) | Merged; already shipped |

**Strongest signals:** Cross-session search, Quick/Temporary Chat, and model preset UX are the most user-facing features in flight and likely to appear in the next release.

## 7. User Feedback Summary

- **Frustration with model switching:** Users expect per-session model selection similar to Cloud SaaS AI UIs (#5198). The current behavior—locking to a top-choice model with limited fallback—is a notable pain point.
- **Plugin installation friction:** The feishu channel fails on clean installs without `ensurepip` (#5205), suggesting the packaging/runtime environment setup is not robust enough for fresh deployments.
- **Tool-call leakage into responses:** An unexpected regression (#5185) is producing raw tool-call code in responses, which disrupts the conversational flow and suggests a parsing or formatting regression.
- **Positive signal:** The merged PRs for cron reliability, session consolidation, and rate limiting directly address real operational pain points, indicating the maintainer team is responsive to community-reported issues.

## 8. Backlog Watch

| Item | Age | Priority | Concern |
|------|-----|----------|---------|
| [#3869](https://github.com/HKUDS/nanobot/pull/3869) | ~2 months (created 2026-05-16) | P2 | DeepSeek message hardening — `null` content causes 400 errors, `"(empty)"` placeholder leaks, assistant text unconditionally dropped. Open with conflicts. |
| [#5210](https://github.com/HKUDS/nanobot/pull/5210) | 1 day | P1 | Trusted proxy auth — open, needs review. |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | 1 day | Feature | Cross-session search — open, awaiting review. |
| [#5185](https://github.com/HKUDS/nanobot/issues/5185) | 3 days | P1 | Tool-call code in responses — no fix PR yet. |
| [#5205](https://github.com/HKUDS/nanobot/issues/5205) | 1 day | P1 | `ensurepip` missing on plugin enable — no fix PR yet. |

**Top priority for maintainers:** #3869 has been open for ~2 months with conflicts and directly affects DeepSeek users. The two open P1 issues (#5185, #5205) should also receive timely attention given their impact on core functionality.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ Summary generation failed.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-02

---

## 1. Today's Overview

PicoClaw showed moderate development activity on 2026-08-02, with one open issue and three pull requests updated in the last 24 hours. No new releases were published. The project continues to expand its provider ecosystem, with two open PRs adding new AI providers (OrcaRouter) and search tools (Exa), alongside a recently merged localization update for Traditional Chinese. The lone open issue (#3203) highlights a notable reliability gap in the Matrix channel's long-polling sync loop. Overall, the project is in a steady feature-expansion phase with no critical release pressure.

---

## 2. Releases

No new releases were published in the last 24 hours. The most recent tracked version remains **v0.2.9**.

---

## 3. Project Progress

**Merged/Closed PR (1):**

- **PR #3261** — *Add zh-TW locale and Traditional Chinese translations* (closed)
  - Author: PeterDaveHello
  - Brings consistent Taiwanese terminology to the WebUI and documentation, extending the localized experience through setup and channel guidance. This marks continued investment in multilingual support.
  - 🔗 [PR #3261](https://github.com/sipeed/picoclaw/pull/3261)

**Open PRs under active review (2):**

- **PR #3299** — *Add native Exa web search provider*
  - Introduces Exa as a first-class `tools.web` / `web_search` provider with `POST /search` API integration, `type: "auto"`, highlights support, and date-range filters.
  - 🔗 [PR #3299](https://github.com/sipeed/picoclaw/pull/3299)

- **PR #3309** — *Add OrcaRouter as an OpenAI-compatible provider*
  - Adds `orcarouter` as a new provider, routing requests through the OrcaRouter multi-vendor API at `https://api.orcarouter.ai/v1` using the standard OpenAI Chat Completions contract.
  - 🔗 [PR #3309](https://github.com/sipeed/picoclaw/pull/3309)

---

## 4. Community Hot Topics

### Issue #3203 — Matrix sync loop reconnection bug
- **Title:** Matrix sync loop has no reconnection logic — silent death after network/server disruption
- **Author:** weissfl | **Comments:** 7 | **👍:** 2 | **Created:** 2026-07-02 | **Updated:** 2026-08-01
- 🔗 [Issue #3203](https://github.com/sipeed/picoclaw/issues/3203)

**Analysis:** This is the most engaged issue in the recent window. The problem is significant for self-hosted deployments: because PicoClaw's main process remains alive, `systemd Restart=on-failure` never triggers, and the Matrix channel silently stops syncing after any network hiccup or homeserver restart. The 7 comments and 2 upvotes suggest multiple users have hit this wall. The underlying need is **resilience in always-on agent deployments**, where unattended reconnection is a hard requirement rather than a nice-to-have. No fix PR has been submitted yet.

---

## 5. Bugs & Stability

| Severity | Issue | Status |
|----------|-------|--------|
| 🔴 High | #3203 — Matrix `/sync` loop silent failure after network disruption; no auto-reconnect; bypasses systemd restart policies | Open, stale |

No other bugs were reported or updated in the last 24 hours. The Matrix reconnection issue is the sole stability concern and remains unfixed. No fix PR currently exists.

---

## 6. Feature Requests & Roadmap Signals

- **Native Exa search integration (PR #3299):** Reflects growing demand for diverse, high-quality web search backends beyond the existing providers. If merged, this signals PicoClaw's continued expansion of the `tools.web` ecosystem.
- **OrcaRouter provider support (PR #3309):** Indicates user interest in multi-vendor router abstraction layers, allowing seamless switching between upstream models through a single OpenAI-compatible endpoint.
- **zh-TW localization (PR #3261, merged):** Reinforces the project's commitment to broader linguistic accessibility.

**Prediction for next release:** The Exa search provider and OrcaRouter integration are the strongest candidates for inclusion in the next minor release, assuming review cycles complete. A v0.3.0 release including these provider additions would be consistent with recent velocity.

---

## 7. User Feedback Summary

- **Pain point — Matrix reliability:** Users running PicoClaw as a long-lived service (systemd-managed) are frustrated by the silent failure mode in the Matrix channel. When network or homeserver interruptions occur, the agent appears alive but stops functioning, creating a confusing "zombie" state with no restart trigger.
- **Satisfaction — Ecosystem growth:** The community is actively contributing new integrations (Exa, OrcaRouter, zh-TW), suggesting healthy engagement and satisfaction with the project's extensible architecture.
- **Unmet need — Auto-reconnect logic:** The #3203 issue points to a broader expectation: PicoClaw channels should self-heal after transient failures without requiring manual process restarts.

---

## 8. Backlog Watch

| Item | Author | Age | Notes |
|------|--------|-----|-------|
| [Issue #3203](https://github.com/sipeed/picoclaw/issues/3203) — Matrix sync reconnection | weissfl | ~31 days | Marked stale but still open with 7 comments. High-severity bug for self-hosted users. No fix PR in sight. Needs maintainer attention. |

**Recommendation:** Issue #3203 is the most urgent item in the backlog. A maintainer triage or a community-contributed fix PR would significantly improve deployment reliability for Matrix channel users.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-02

## 1. Today's Overview

NanoClaw is in a highly active development cycle, with 12 PRs and 2 issues updated in the past 24 hours, signaling strong contributor momentum. The project shipped a major rollup release (v2.1.54) and delivered a significant architectural change: the unification of iMessage into a single channel with dual backends. Setup flow bugs and broken skill dependencies were the primary focus of today's closed items, indicating active maintenance cleanup alongside feature work. Overall project health is strong — fast PR turnover, active issue triage, and a clean release cadence.

## 2. Releases

### v2.1.54 (Rollup)
A comprehensive rollup release covering everything merged between v2.1.17 and v2.1.54. Key highlights include:

- **[BREAKING]** iMessage unified into a single `imessage` channel with two backends via `/add-imessage`:
  - **Local** — Chat SDK bridge over `chat.db` (this Mac only)
  - **Hosted** — Native [Photon](https://photon.codes) backend via Spectra
- Credential expiry alerting (`feat(credentials): alert when a provider credential expires`)
- Rootless Docker support for agent containers
- iMessage hosted registration flow fix (PR #3164)
- Migration fix: `insertTask` → `insertTaskRow` rename correction

**Migration note:** Users upgrading from v2.1.17 or earlier should re-run `/add-imessage` to select their preferred backend. The previous dual-channel setup is superseded.

## 3. Project Progress

### Merged / Closed Today
| PR | Author | Summary |
|---|---|---|
| [#3170](https://github.com/nanocoai/nanoclaw/pull/3170) | glifocat | Fixed setup: dispatch failure-assist prompts to the user's picked provider instead of defaulting to Claude |
| [#3168](https://github.com/nanocoai/nanoclaw/pull/3168) | glifocat | Closed post-merge safety gaps in the release process |
| [#3167](https://github.com/nanocoai/nanoclaw/pull/3167) | AmiTal4 | Added credential expiry alerting — previously expired Codex credentials surfaced only as opaque "Read-only file system" errors |
| [#3166](https://github.com/nanocoai/nanoclaw/pull/3166) | petrolette | Fixed a `SyntaxError` in `migrate-v2` caused by a stale import (`insertTask` → `insertTaskRow`) |
| [#2999](https://github.com/nanocoai/nanoclaw/pull/2999) | underthestars-zhy | Merged the iMessage unification feature (local + hosted backends) |
| [#3164](https://github.com/nanocoai/nanoclaw/pull/3164) | glifocat | Superseded #2999 with a working hosted iMessage (Photon) registration flow |

### Open PRs Awaiting Review
- **#3174** — Rootless Docker support for agent containers ( Denver901 )
- **#3172** — Remove two qodo skills that depend on an unmaintained external integration ( glifocat )
- **#3173** — Egress update ( campbellrobertson )
- **#2956** — Suppress duplicate message delivery when final output repeats tool-sent content ( stumpjumper )
- **#3121** — Make reaction delivery best-effort ( zivisaiah )
- **#3090** — Prepend all top-level context Markdown in templates ( amit-shafnir )

## 4. Community Hot Topics

### Most Discussed / Active
1. **[iMessage Unification (#2999, #3164)](https://github.com/nanocoai/nanoclaw/pull/2999)** — The single biggest feature shipped this cycle. Two PRs converged: the initial unification and a follow-up fixing the hosted Photon registration flow. Community need: operators want a single entry point for iMessage regardless of deployment style (local Mac vs. hosted).

2. **[Setup provider routing fix (#3170 / #3169)](https://github.com/nanocoai/nanoclaw/issues/3169)** — Non-Claude users were being relentlessly prompted to install the Claude CLI during setup failures. Community need: respect the user's chosen provider throughout the entire setup flow, not just the initial selection.

3. **[Rootless Docker (#3174)](https://github.com/nanocoai/nanoclaw/pull/3174)** — Agent containers are completely unusable on rootless Docker daemons. This affects a growing segment of security-conscious users who deliberately avoid adding themselves to the `docker` group.

**Underlying signal:** Users are running NanoClaw in increasingly diverse environments (rootless containers, non-Claude providers, hosted messaging backends) and the project is responding with targeted fixes rather than one-size-fits-all defaults.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|---|---|---|---|
| 🔴 High | [#3169](https://github.com/nanocoai/nanoclaw/issues/3169) / [#3170](https://github.com/nanocoai/nanoclaw/pull/3170) | Setup incorrectly routes failure-assist prompts to Claude CLI even when user selected a different provider | ✅ Fixed (merged) |
| 🔴 High | [#3166](https://github.com/nanocoai/nanoclaw/pull/3166) | `migrate-v2` step crashes with `SyntaxError` due to stale `insertTask` import after rename to `insertTaskRow` | ✅ Fixed (merged) |
| 🟡 Medium | [#3171](https://github.com/nanocoai/nanoclaw/issues/3171) | Two bundled qodo skills (`get-qodo-rules`, `qodo-pr-resolver`) depend on a Qodo SaaS API key that nothing in the repo sets up; they also intercept normal coding requests | 🔄 PR #3172 open to remove them |
| 🟡 Medium | [#3167](https://github.com/nanocoai/nanoclaw/pull/3167) | Expired credentials produced opaque errors ("Read-only file system (os error 30)") with no actionable message | ✅ Fixed (merged) — now surfaces expiry alerts |
| 🟢 Low | [#2956](https://github.com/nanocoai/nanoclaw/pull/2956) | Duplicate message delivery when agent reply via `send_message` MCP tool is also repeated in final output | 🔄 PR open, no merge yet |

## 6. Feature Requests & Roadmap Signals

- **iMessage hosted backend (Photon)** — Already shipped in v2.1.54. Signals ongoing investment in multi-backend channel architecture.
- **Rootless Docker support** — PR #3174 is open; if merged, this will be a notable infrastructure parity feature.
- **Credential expiry alerts** — Shipped in v2.1.54 (#3167). Likely to become a pattern for other failure-mode observability.
- **Duplicate-delivery suppression** — PR #2956 addresses a quality-of-life issue in agent output routing.
- **Best-effort reaction delivery** — PR #3121 suggests the team is tightening reliability across messaging channels.

**Prediction:** The next release will likely include rootless Docker support, qodo skill removal, and the duplicate-delivery fix — all are in PRs with no outstanding blockers.

## 7. User Feedback Summary

- **Frustration with Claude-default assumptions:** Multiple users (glifocat) flagged that setup and skill flows assume Claude is the default provider, even when a different backend was explicitly chosen. This is a recurring pain point for multi-provider users.
- **Broken bundled dependencies:** The qodo skills are bundled but non-functional out of the box — they require an external SaaS account and API key that the project never configures. Users see them in their skill list but cannot use them, and they interfere with normal coding workflows.
- **Opaque credential errors:** Expired credentials previously surfaced as confusing filesystem errors rather than clear expiry messages. This has now been addressed.
- **Satisfaction with unification:** The iMessage consolidation is well-received — one channel, two backends, clear setup via `/add-imessage`.

## 8. Backlog Watch

| Item | Author | Age | Risk |
|---|---|---|---|
| [#3174](https://github.com/nanocoai/nanoclaw/pull/3174) — Rootless Docker support | Denver901 | ~1 day open | Medium — no blockers, but needs maintainer review to merge |
| [#2956](https://github.com/nanocoai/nanoclaw/pull/2956) — Suppress duplicate delivery | stumpjumper | ~27 days open | Medium — long-open fix for a real UX bug; no recent activity |
| [#3121](https://github.com/nanocoai/nanoclaw/pull/3121) — Best-effort reaction delivery | zivisaiah | ~10 days open | Low — incremental reliability improvement |
| [#3090](https://github.com/nanocoai/nanoclaw/pull/3090) — Prepend top-level context Markdown | amit-shafnir | ~13 days open | Low — template behavior change, needs review |

**Note:** PR #2956 has been open for nearly a month with no recent maintainer interaction. It addresses a clear duplicate-delivery bug and should be prioritized for merge.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-02

## 1. Today's Overview
IronClaw is operating at high velocity with 12 issue updates and 22 PR updates in the past 24 hours. The project is mid-sprint in a structured architectural refactoring wave (Wave 2), focusing on dependency inversion, contract segregation, and CI gate hardening. Core maintainers are actively closing legacy CI gaps and stabilizing LLM cache behavior, while new UI prototypes are transitioning from mock data to backend wiring. No new releases were published today; development momentum is concentrated on merged refactors and open performance/coverage work.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Project Progress
**Merged/Closed Today:**
- [#6998](https://github.com/nearai/ironclaw/pull/6998) — Inverted `extension_host` product-facing ports onto `product_contracts` (Wave 2, Slot 1).
- [#6996](https://github.com/nearai/ironclaw/pull/6996) — Closed path-keyed CI gate inventory; added inventory-driven discovery and fail-closed behavior.
- [#6995](https://github.com/nearai/ironclaw/pull/6995) — Wave 1 truth audit reconciling target-architecture docs with merged `main`.
- [#7002](https://github.com/nearai/ironclaw/pull/7002) — Inverted `webui` + `openai_compat` onto `product_contracts` (Wave 2, Slot 5).
- [#6761](https://github.com/nearai/ironclaw/pull/6761) — Added regression test for generic outbound registration.

**Advanced This Cycle:**
- Queue-steering logic forward-ported with turn-boundary race fixes [#5981](https://github.com/nearai/ironclaw/pull/5981)
- Postgres capacity recovery from row-native journal regression [#6973](https://github.com/nearai/ironclaw/pull/6973)
- Anthropic `cache_control` breakpoint hardening across both transports [#6997](https://github.com/nearai/ironclaw/pull/6997)
- Extension manager split from `extension_host` [#7003](https://github.com/nearai/ironclaw/pull/7003)
- WebChat v2 OOBE automation-tasks UI prototype landed [#6994](https://github.com/nearai/ironclaw/pull/6994)

## 4. Community Hot Topics
- [#6963](https://github.com/nearai/ironclaw/issues/6963) (7 comments, closed) — Path-keyed CI gate hardening. High engagement reflects community concern around CI reliability and gate coverage.
- [#6974](https://github.com/nearai/ironclaw/issues/6974) (2 comments) — libSQL `thread_store_writes` p95 degradation (37–135s) after #6696. Directly tied to #6973 performance recovery.
- [#7012](https://github.com/nearai/ironclaw/issues/7012) — Time-awareness without prompt-cache churn. Signals architectural interest in stable temporal context boundaries.
- [#6999](https://github.com/nearai/ironclaw/issues/6999) — Dependency-boundary rule gap for WebChat v2 routes. Highlights growing friction as the v2 web surface scales.

**Analysis:** Activity clusters around three needs: (1) CI/test coverage reliability under locale/encoding edge cases, (2) database-level performance regression from recent journal changes, and (3) explicit cache-control boundaries for LLM round-trips.

## 5. Bugs & Stability
| Severity | Item | Description | Related Fix/PR |
|----------|------|-------------|----------------|
| 🔴 High | [#6974](https://github.com/nearai/ironclaw/issues/6974) | libSQL `thread_store_writes` p95 spikes to 37–135s in tool-heavy cases post-#6696 | [#6973](https://github.com/nearai/ironclaw/pull/6973) (in review) |
| 🟡 Medium | [#6978](https://github.com/nearai/ironclaw/issues/6978) | `reborn-tests.yml` workflow_dispatch fails roll-up (`critical-mutation` skipped but disallowed) | CI logic gap; needs gate adjustment |
| 🟡 Medium | [#7006](https://github.com/nearai/ironclaw/issues/7006) | Changed-coverage gate trips on ~180 lines of untestable error paths (steering queue) | Triage needed; may require gate exemption or harness expansion |
| 🟢 Low | [#6999](https://github.com/nearai/ironclaw/issues/6999) | `server-lifecycle` dependency rule misses WebChat v2 route surface | Architectural call; no immediate fix required |

## 6. Feature Requests & Roadmap Signals
- [#7009](https://github.com/nearai/ironclaw/issues/7009) — Add OrcaRouter as a built-in LLM provider. Fills a gap in the `providers.json` gateway matrix.
- [#7012](https://github.com/nearai/ironclaw/issues/7012) — Append-only rollover context with duration evidence for time awareness without cache churn.
- [#6993](https://github.com/nearai/ironclaw/issues/6993) — Backend wiring for OOBE automation-tasks (following UI prototype #6994).
- [#6780](https://github.com/nearai/ironclaw/pull/6780) — IronHub deep-link register/install + private manifest source.

**Next Release Signals:** Expect merged PRs #7001 (cache-stable system prefix), #6997 (explicit cache breakpoints), #6993 (OOBE backend wiring), and #7009 (OrcaRouter) to land before the next tagged release, alongside Wave 2 contract inversions.

## 7. User Feedback Summary
- **Performance pain points:** Tool-heavy execution under libSQL/Postgres shows severe p95 regression (#6974). Users need stable latency for automation workloads.
- **Developer experience friction:** CI locale-sensitive sorting (#6992) and strict changed-lines coverage gates (#7006) cause false negatives/positives. Contributors are requesting more explicit exclusion rules for synthetic fault-injection paths.
- **Feature gaps:** Demand for broader LLM gateway support (OrcaRouter) and stable temporal context boundaries indicates users are pushing toward longer-running, multi-step agent sessions where cache churn and routing diversity matter.
- **Positive traction:** WebChat v2 attachment previews (#6917) and OOBE automation-tasks UI (#6994) are receiving early adoption interest.

## 8. Backlog Watch
Items requiring maintainer triage or awaiting downstream merges:
- [#5981](https://github.com/nearai/ironclaw/pull/5981) — Queued-message steering (ported, races fixed, merge-blocked on stack order)
- [#5982](https

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-08-02

---

## 1. Today's Overview

LobsterAI shows **moderate but focused activity** today, with 7 issues updated and 2 open PRs awaiting review. All 7 issue updates today correspond to closed/stale items, suggesting a recent round of triage and closure by maintainers or automated cleanup. No new releases were published. The project remains in a steady maintenance phase, with community-driven bug fixes and i18n improvements leading the current workflow.

---

## 2. Releases

*No new releases today.* The latest release cycle has not yet produced a tagged version as of this digest.

---

## 3. Project Progress

### Closed Issues (Triage / Resolution Today)

| Issue | Summary | Link |
|-------|---------|------|
| [#1293](https://github.com/netease-youdao/LobsterAI/issues/1293) | Custom HTTP MCP not recognized by the OpenClaw engine; only SSE MCPs work | [Issue #1293](https://github.com/netease-youdao/LobsterAI/issues/1293) |
| [#1296](https://github.com/netease-youdao/LobsterAI/issues/1296) | 3MB long-image upload causes page crash and task failure | [Issue #1296](https://github.com/netease-youdao/LobsterAI/issues/1296) |
| [#1298](https://github.com/netease-youdao/LobsterAI/issues/1298) | Short two-character input incorrectly triggers "content too long" error | [Issue #1298](https://github.com/netease-youdao/LobsterAI/issues/1298) |
| [#1302](https://github.com/netease-youdao/LobsterAI/issues/1302) | Feature request: line-number toggle for code blocks (merged via PR) | [Issue #1302](https://github.com/netease-youdao/LobsterAI/issues/1302) |
| [#1305](https://github.com/netease-youdao/LobsterAI/issues/1305) | Scheduled task history displays incorrect title after deletion | [Issue #1305](https://github.com/netease-youdao/LobsterAI/issues/1305) |
| [#1307](https://github.com/netease-youdao/LobsterAI/issues/1307) | Model provider config panel becomes read-only after closing and switching providers | [Issue #1307](https://github.com/netease-youdao/LobsterAI/issues/1307) |

### Open PRs Awaiting Review

| PR | Summary | Link |
|----|---------|------|
| [#1224](https://github.com/netease-youdao/LobsterAI/pull/1224) | Fixes i18n hardcoding, adds Escape key to close Agent modal, prevents double-click on delete | [PR #1224](https://github.com/netease-youdao/LobsterAI/pull/1224) |
| [#2358](https://github.com/netease-youdao/LobsterAI/pull/2358) | Shows localized error feedback when session rename fails | [PR #2358](https://github.com/netease-youdao/LobsterAI/pull/2358) |

---

## 4. Community Hot Topics

**Most Engaged Issue: [#1293](https://github.com/netease-youdao/LobsterAI/issues/1293)** — *1 👍, 2 comments*

The custom HTTP MCP incompatibility with the OpenClaw engine has drawn the most community interest. Users are integrating external MCP services and expecting parity between SSE and HTTP transports — a signal that LobsterAI's MCP ecosystem is expanding beyond the default configuration.

**Notable Discussion: [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223)** — UX/i18n hardcoding affecting non-Chinese users

This issue bundles three related concerns (i18n string leakage, missing Escape key, missing delete-protection) and has an active fix PR (#1224). It reflects a growing international user base requesting better localization and accessibility.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| 🔴 High | [#1296](https://github.com/netease-youdao/LobsterAI/issues/1296) | Uploading a 3MB long image crashes the page and breaks all subsequent tasks | Closed — needs verification |
| 🔴 High | [#1298](https://github.com/netease-youdao/LobsterAI/issues/1298) | Two-character input incorrectly rejected as exceeding model limits | Closed — needs verification |
| 🟡 Medium | [#1307](https://github.com/netease-youdao/LobsterAI/issues/1307) | Config panel goes read-only after switching model providers | Closed — needs verification |
| 🟡 Medium | [#1293](https://github.com/netease-youdao/LobsterAI/issues/1293) | HTTP-based MCP tools invisible to OpenClaw engine | Closed — needs verification |
| 🟢 Low | [#1305](https://github.com/netease-youdao/LobsterAI/issues/1305) | Historical scheduled task shows wrong title after deletion | Closed — needs verification |

> **Note:** All issues above are marked `stale` and `closed`, but no fix PRs are explicitly linked. Users are encouraged to verify whether closures indicate resolved fixes or were closed without a merge.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| **MCP HTTP transport support** | [#1293](https://github.com/netease-youdao/LobsterAI/issues/1293) | High — direct feature gap vs. SSE; likely next engine update |
| **Code block line-number toggle** | [#1302](https://github.com/netease-youdao/LobsterAI/issues/1302) | High — already implemented in a merged PR |
| **Escape key to close Agent modal** | [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | Medium — addressed in open PR #1224 |
| **Session rename error feedback** | [#670](https://github.com/netease-youdao/LobsterAI/issues/670) referenced in [#2358](https://github.com/netease-youdao/LobsterAI/pull/2358) | Medium — addressed in open PR #2358 |

**Prediction:** The next release will likely include code block line numbers, i18n hardcoding fixes, and session rename error feedback. HTTP MCP support is the most strategically important pending feature.

---

## 7. User Feedback Summary

- **Pain point — Image handling:** Large image uploads (3MB+) crash the renderer, blocking all tasks. This is a stability concern for users working with visual content.
- **Pain point — False validation errors:** Short inputs incorrectly triggering "content too long" suggests a bug in token/length calculation, frustrating users and eroding trust.
- **Pain point — i18n leaks:** English-language users see hardcoded Chinese strings in AI prompts, directly violating localization standards and affecting agent behavior.
- **Satisfaction signal:** The community is actively contributing fixes (PRs #1224, #2358), indicating strong contributor engagement and a healthy open-source ecosystem around the project.

---

## 8. Backlog Watch

| Item | Days Since Last Activity | Risk |
|------|-------------------------|------|
| [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) / [#1224](https://github.com/netease-youdao/LobsterAI/pull/1224) | Open since 2026-04-01 (~4 months) | Medium — fix is ready but unmerged; i18n impact is broad |
| [#2358](https://github.com/netease-youdao/LobsterAI/pull/2358) | Open since 2026-07-18 (~15 days) | Low — small, focused fix |
| [#1293](https://github.com/netease-youdao/LobsterAI/issues/1293) | MCP HTTP support — no fix PR yet | High — core feature gap for MCP integrations |

**Recommendation:** Maintainers should prioritize reviewing PR #1224 (long-standing i18n + UX fixes) and investigating a proper fix for the HTTP MCP engine issue (#1293), which affects a growing segment of power users.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-02

## 1. Today's Overview

Moltis saw moderate development activity on 2026-08-02, with **3 pull requests** updated in the last 24 hours and **no new issues** or releases. Two of the three PRs were merged/closed (PR #1174 and PR #1170), while one remains open (PR #1182). The project is actively hardening its session management, observability infrastructure, and channel-level access controls — signals of a project maturing toward production readiness rather than rapid feature expansion. No releases were published during this window.

## 2. Releases

**No new releases** were published in the last 24 hours.

## 3. Project Progress

**Merged/Closed PRs:**

- **[PR #1174](https://github.com/moltis-org/moltis/pull/1174)** — *Add instrumentation and feedback collection infrastructure* (Author: penso | Merged 2026-08-01)
  - Introduces backend-neutral agent instrumentation with Langfuse v4 export support, operational OTLP backends, and end-user reaction feedback.
  - Records immutable completion-only turns and observations with streaming/non-streaming parity, provider failover attribution, cache-aware token usage, and reasoning traces.
  - **Impact:** Significant — gives operators visibility into agent behavior across providers and is a prerequisite for production reliability monitoring.

- **[PR #1170](https://github.com/moltis-org/moltis/pull/1170)** — *fix(channels): gate /sh and privileged tools behind a per-account operators list* (Author: penso | Merged 2026-08-01)
  - Fixes a privilege escalation gap where channel senders on the access allowlist could reach privileged commands and host tools.
  - Introduces a per-account `operators` list to separate access from privilege across commands, callbacks, queue replay, chat execution, and external integrations.
  - **Impact:** Security-critical fix addressing a real access-control flaw in channel-based agent interaction.

**Open PRs:**

- **[PR #1182](https://github.com/moltis-org/moltis/pull/1182)** — *fix(sessions): allow deleting and archiving the main session* (Author: shixi-li | Open since 2026-08-01)
  - Removes the hard guard preventing the `main` session from being deleted or archived (PR #1132).
  - Preserves the current-active-channel-session archive restriction and keeps `sessions.clear_all` behavior intact.
  - **Status:** Awaiting review/merge.

## 4. Community Hot Topics

| PR/Issue | Activity | Link |
|---|---|---|
| PR #1182 | Open, 0 reactions, awaiting review | [moltis-org/moltis#1182](https://github.com/moltis-org/moltis/pull/1182) |
| PR #1174 | Merged, 0 reactions | [moltis-org/moltis#1174](https://github.com/moltis-org/moltis/pull/1174) |
| PR #1170 | Merged, 0 reactions | [moltis-org/moltis#1170](https://github.com/moltis-org/moltis/pull/1170) |

**Analysis:** No open issues were filed today, and community reaction counts are at zero across all items. The three PRs reflect maintainer-driven work rather than community-sourced requests. The underlying needs driving this activity are clear:

- **Observability** (PR #1174): Users and operators need traceability into multi-provider agent behavior — a common gap in agent frameworks.
- **Security hardening** (PR #1170): The privilege-boundary fix indicates the project is responding to real-world deployment concerns where channel-based access controls must be audit-grade.
- **Session UX flexibility** (PR #1182): Users want parity in session management; the `main` session being immutable was a usability friction point.

## 5. Bugs & Stability

**No new bug reports** were filed today (0 open issues). However, two significant issues were resolved:

| Severity | Issue | Resolution | Link |
|---|---|---|---|
| **High (Security)** | Privileged commands accessible to non-operator channel senders | Fixed in PR #1170 | [moltis-org/moltis#1170](https://github.com/moltis-org/moltis/pull/1170) |
| **Medium (UX)** | `main` session cannot be deleted or archived | Fix in PR #1182 (open) | [moltis-org/moltis#1182](https://github.com/moltis-org/moltis/pull/1182) |

The security fix in PR #1170 is the most stability-relevant item this cycle. No crashes or regressions were reported.

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|---|---|---|
| Session management parity (delete/archive `main` session) | PR #1182 (open) | Likely in next patch or minor release; small, targeted fix. |
| Agent observability / instrumentation | PR #1174 (merged) | Now merged — Langfuse v4, OTLP, and reaction feedback will ship with the next release. |
| Fine-grained operator roles | PR #1170 (merged) | Merged; per-account `operators` list is a new capability likely to be documented in release notes. |

**Prediction:** The next release will highlight the instrumentation and security features as the primary additions. PR #1182 may ship in a follow-up patch depending on review velocity.

## 7. User Feedback Summary

- **Satisfaction signals are low but stable** — zero new issues and zero reactions suggest either a quiet user base or users engaging through PRs rather than issue reports.
- **Pain points addressed:**
  - Session immutability of `main` was a known frustration (PR #1182 references issue #1132).
  - Privilege boundary violations in channels were a real security concern that has now been remediated (PR #1170).
- **Use cases emerging:** Multi-provider agent deployment with observability requirements (Langfuse, OTLP) and channel-based multi-tenant interaction with strict role separation.
- No negative feedback or dissatisfaction indicators were captured in this window.

## 8. Backlog Watch

| Item | Age | Risk | Link |
|---|---|---|---|
| PR #1182 — Allow deleting/archiving main session | Open since 2026-08-01 (1 day) | Low — small, scoped fix; needs maintainer review | [moltis-org/moltis#1182](https://github.com/moltis-org/moltis/pull/1182) |

**No long-standing unanswered issues or PRs** were detected in this cycle. The single open PR has been open for approximately one day and is a focused bug fix, not a backlog item.

---

**Project Health Assessment:** 🟢 **Stable & Progressing** — Two security and observability improvements merged, one UX fix awaiting review, zero regressions, and zero new open issues. Development is focused on production hardening.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw (QwenPaw) Project Digest — 2026-08-02

## 1. Today's Overview

QwenPaw (agentscope-ai/CoPaw) shows **high daily activity** with 9 open issues and 11 open pull requests touched in the last 24 hours, plus 1 merged PR. The project is in an active development phase around the 2.0 release, with contributors addressing a mix of bug fixes, provider integrations, and memory/compression improvements. No new releases were published today, but multiple fix PRs are poised for merge, indicating a steady bug-fix cadence. The contributor base is broadening — several first-time contributors submitted PRs today — which is a healthy signal for project sustainability.

## 2. Releases

**None.** No new versions were published in the last 24 hours. The latest known version referenced in issues is **QwenPaw 2.0.1** (desktop).

## 3. Project Progress

### Merged / Closed PRs (1)
| PR | Description |
|----|-------------|
| [#6598](https://github.com/agentscope-ai/QwenPaw/pull/6598) | **fix(skills):** Preserve plugin-sourced skill tags across reconcile cycles — fixes #6537. Skill tags set in the UI no longer disappear on restart. |

### Notable Open PRs Advanced Today
| PR | Description |
|----|-------------|
| [#6632](https://github.com/agentscope-ai/QwenPaw/pull/6632) | Follow-up fix for skill-tag persistence (reconcile cycles) — same root cause as #6537. |
| [#6631](https://github.com/agentscope-ai/QwenPaw/pull/6631) | **fix(providers):** Align Aliyun coding-plan models with the official website; removes unsupported `glm-5.1`/`glm-5.2`, adds missing `qwen3.7-plus`. Fixes #6551. |
| [#6630](https://github.com/agentscope-ai/QwenPaw/pull/6630) | **fix(agents):** Report empty model responses to the user instead of silent failure; improves UX for sessions approaching context limits. Fixes #6601. |
| [#6629](https://github.com/agentscope-ai/QwenPaw/pull/6629) | **fix(memory):** Trigger `summarize_when_compact` memory flow on auto-compression (scroll), not just on manual `/compact`. Fixes #6624. |
| [#6628](https://github.com/agentscope-ai/QwenPaw/pull/6628) | **fix(scroll):** Use `SystemMsg` for compressed-memory placeholder instead of `role=user`, preventing HTTP 400 from OpenAI-compatible APIs. Fixes #6541. |
| [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) | **fix(acp):** Prevent final-text loss when notifications race the prompt response (TCP-segment race condition). Fixes #6625. |
| [#6622](https://github.com/agentscope-ai/QwenPaw/pull/6622) | **feat(provider):** Add **OrcaRouter** as a built-in provider — users can paste an API key without manual custom-provider setup. |
| [#6620](https://github.com/agentscope-ai/QwenPaw/pull/6620) | **fix(providers):** Relay Gemini `thought_signature` via `extra_content` without mutating the strict `ToolCallBlock` schema. Fixes #6619 crash. |
| [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | **feat:** Unify provider discovery, model metadata, routing, and agent controls (addresses #6167). Large architectural PR, still open. |
| [#5490](https://github.com/agentscope-ai/QwenPaw/pull/5490) | **feat(console):** Render tool-card images inline with gallery navigation — improves media viewing UX. |

## 4. Community Hot Topics

| Issue | Title | Comments | Activity |
|-------|-------|----------|----------|
| [#6593](https://github.com/agentscope-ai/QwenPaw/issues/6593) | Unified QwenPaw cleanup page (memory/tool data bloat) | 2 | 🔥 High — reflects long-term users hitting storage bloat |
| [#6480](https://github.com/agentscope-ai/QwenPaw/issues/6480) | `nohup` shell commands cause agent to hang | 2 | 🔥 High — core usability bug for Linux users |
| [#6568](https://github.com/agentscope-ai/QwenPaw/issues/6568) | Global hotkey floating input box (Doubao-style) | 2 | 🔥 High — strong UX demand for quick-capture interaction |
| [#6621](https://github.com/agentscope-ai/QwenPaw/issues/6621) | Multi-agent collaboration guidance missing | 1 | Multi-agent onboarding friction |
| [#6627](https://github.com/agentscope-ai/QwenPaw/issues/6627) | How to use Loongsuite to trace with QwenPaw | 1 | Observability need |

**Underlying needs:** Users are transitioning from casual testing to **long-term, production-like usage**. Issues around data bloat (#6593), shell detachment (#6480), and multi-agent discovery (#6621) signal that the 2.0 user base is scaling in complexity and demanding enterprise-grade reliability and discoverability.

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Description |
|----------|-------|--------|-------------|
| 🔴 **Critical** | [#6619](https://github.com/agentscope-ai/QwenPaw/issues/6619) | [#6620](https://github.com/agentscope-ai/QwenPaw/pull/6620) | `ToolCallBlock` crash — `extra_content` field missing causes every streaming request with Gemini thought-signature to fail. |
| 🔴 **Critical** | [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625) | [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) | ACP `delegate_external_agent` returns "completed without text output" when notification races prompt response. |
| 🟠 **High** | [#6624](https://github.com/agentscope-ai/QwenPaw/issues/6624) | [#6629](https://github.com/agentscope-ai/QwenPaw/pull/6629) | Auto-compression (scroll) does not trigger `summarize_when_compact` memory flow; manual `/compact` works. |
| 🟠 **High** | [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) | [#6628](https://github.com/agentscope-ai/QwenPaw/pull/6628) | Compressed-memory placeholder injected as `role=user` causes HTTP 400 from DeepSeek/OpenAI APIs. |
| 🟡 **Medium** | [#6601](https://github.com/agentscope-ai/QwenPaw/issues/6601) | [#6630](https://github.com/agentscope-ai/QwenPaw/pull/6630) | Empty model responses are silently swallowed; no user-visible error. |
| 🟡 **Medium** | [#6537](https://github.com/agentscope-ai/QwenPaw/issues/6537) | [#6598](https://github.com/agentscope-ai/QwenPaw/pull/6598) ✅ merged / [#6632](https://github.com/agentscope-ai/QwenPaw/pull/6632) | Plugin-sourced skill tags lost on restart. |
| 🟡 **Medium** | [#6551](https://github.com/agentscope-ai/QwenPaw/issues/6551) | [#6631](https://github.com/agentscope-ai/QwenPaw/pull/6631) | Aliyun coding-plan lists unsupported models (`glm-5.1`, `glm-5.2`). |
| 🟡 **Low** | [#6626](https://github.com/agentscope-ai/QwenPaw/issues/6626) | — | CI `Real behavior proof` gate strips fenced Evidence blocks, causing false rejections. |
| 🔵 **Info** | [#6480](https://github.com/agentscope-ai/QwenPaw/issues/6480) | — | `nohup`/background shell commands cause agent to hang indefinitely. No fix PR yet. |

**Stability assessment:** 5 of 9 bugs have open fix PRs (1 already merged). The critical crashes (#6619, #6625) are well-addressed. The `nohup` hang (#6480) remains an open risk for Linux users.

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for Next Release |
|---------|-------|----------------------------|
| Global hotkey floating input box (Doubao/Raycast-style) | [#6568](https://github.com/agentscope-ai/QwenPaw/issues/6568) | 🟢 **High** — well-scoped, Tauri-native, strong user demand |
| Unified data cleanup page (manual + auto) | [#6593](https://github.com/agentscope-ai/QwenPaw/issues/6593) | 🟡 **Medium** — larger UX + storage engineering effort |
| OrcaRouter built-in provider | [#6622](https://github.com/agentscope-ai/QwenPaw/pull/6622) | 🟢 **High** — PR already submitted, low risk |
| Inline tool-card image gallery | [#5490](https://github.com/agentscope-ai/QwenPaw/pull/5490) | 🟡 **Medium** — PR open since June, needs review |
| Unified provider/model routing architecture | [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | 🟡 **Medium** — large PR, likely next minor version |
| Loongsuite tracing integration | [#6627](https://github.com/agentscope-ai/QwenPaw/issues/6627) | 🔵 **Low** — niche observability need |

**Prediction:** The next patch release (2.0.2) will likely ship the critical bug fixes (#6619, #6625, #6624, #6628, #6630) and the OrcaRouter provider (#6622). The hotkey feature (#6568) and cleanup page (#6593) are strong candidates for the 2.1 minor release.

## 7. User Feedback Summary

**Pain points:**
- **Storage bloat:** Long-term users report QwenPaw becoming "chaotic and space-heavy" due to unmanaged auto-memory, tool artifacts, backups, and history (#6593).
- **Shell process detachment:** Running commands with `nohup` or `&` causes the agent to hang forever — a blocker for Linux power users (#6480).
- **Multi-agent discoverability:** Users created multiple agents but found that the default agent never calls them unless explicitly instructed in `PROFILE.md`, leading to 50+ rounds of wasted debugging (#6621).
- **Silent failures:** Empty model responses and crashed streams provide no feedback, making debugging difficult (#6601, #6619).
- **Friction for quick questions:** Opening the full 1280×800 window for a simple query feels heavy; users want a Raycast/Doubao-style floating input (#6568).

**Satisfaction signals:**
- Manual `/compact` working while auto-compression doesn't suggests the memory pipeline is partially functional but incomplete.
- The community is actively filing detailed, well-reproduced bug reports with root-cause analysis — a sign of an engaged, technically literate user base.

## 8. Backlog Watch

| Item | Type | Age | Risk |
|------|------|-----|------|
| [#6480](https://github.com/agentscope-ai/QwenPaw/issues/6480) — `nohup` shell hang | Bug | 7 days | 🔴 High — no fix PR; affects Linux power users |
| [#6593](https://github.com/agentscope-ai/QwenPaw/issues/6593) — Cleanup page feature | Enhancement | 2 days | 🟡 Medium — user-visible, no PR yet |
| [#6568](https://github.com/agentscope-ai/QwenPaw/issues/6568) — Global hotkey input | Enhancement | 3 days | 🟡 Medium — well-defined, no PR yet |
| [#6626](https://github.com/agentscope-ai/QwenPaw/issues/6626) — CI gate strips fenced evidence | Bug | 1 day | 🟢 Low — dev-experience issue |
| [#6627](https://github.com/agentscope-ai/QwenPaw/issues/6627) — Loongsuite tracing | Question | 1 day | 🟢 Low — niche |
| [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) — Unified provider architecture | Feature PR | 12 days | 🟡 Medium — large PR needs maintainer review |
| [#5490](https://github.com/agentscope-ai/QwenPaw/pull/5490) — Inline image gallery | Feature PR | 39 days | 🟡 Medium — stale, needs triage |

**Key takeaway:** The most urgent backlog item is **#6480** (nohup hang) — a 7-day-old critical bug with no fix PR. The two feature requests (#6593, #6568) represent the strongest roadmap signals from users. PRs #6302 and #5490 have been open for 12 and 39 days respectively and may need maintainer attention to unblock.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-02

---

## 1. Today's Overview

ZeroClaw continues to exhibit high community velocity, with 50 issues and 50 PRs touched in the last 24 hours, though no pull requests were merged or closed and no new releases were published — suggesting a busy review and discussion cycle without yet reaching landing. Activity is heavily concentrated around security architecture RFCs, memory lifecycle redesign, and a batch of eval-system improvements. The project is squarely in the v0.9.0 prep phase, with multiple high-risk RFCs awaiting maintainer decisions tracked in issue #8692. No regressions beyond the WhatsApp security bug were flagged today.

---

## 2. Releases

*No new releases in the last 24 hours.* Version bump to `v0.8.4` is pending in PR [#9648](https://github.com/zeroclaw-labs/zeroclaw/issues/9648), but has not yet shipped.

---

## 3. Project Progress

**No PRs merged or closed today.** The following PRs advanced in review or discussion:

- **[#9220–#9248] Eval system stack** — Five PRs from `IftekharUddin` landed incrementally, adding comparable run receipts (#9220), LLM-judge grader (#9222), JUnit XML reporting (#9223), git-versioned baselines with regression diffing (#9221), append-only history (#9248), and isolated case memory with exact assertions (#9244). This forms a complete evaluation pipeline ready for calibration.
- **[#9091] Computer-use drivers** — Added native macOS, Linux X11, and Windows drivers for the `computer_use` tool (#9091), advancing the desktop agent capability from RFC (#6909) toward implementation.
- **[#9080] Secure relay transport** — Introduced mutual TLS, daemon-owned CA, CSR issuance, and revocation for remote WSS (#9080), a core piece of the v0.9.0 security architecture.
- **[#9420] Anthropic stored OAuth** — Added `auth_mode = "oauth"` for stored Anthropic profiles, preserving legacy inline-token paths (#9420).
- **[#9634] Telegram group authorization** — Added `allow_groups` config with live-resolved allowlists for Telegram (#9634).
- **[#8985] Slack lifecycle progress** — Added six typed agent lifecycle states so long-running Slack turns show progress instead of appearing stalled (#8985).
- **[#9571] WATI channel removal** — Began removal of the WATI channel module and all associated infrastructure (#9571).
- **[#9182] PowerShell on Windows** — Added native PowerShell support via `runtime.shell` on Windows (#9182).

---

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|---|---|---|---|
| #9048 | Separate conversation history from agent-curated long-term memory | 16 | [#9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048) |
| #8603 | OpenAI Chat Completions compatibility adapter | 13 | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| #9127 | Abstract a `KeySource` trait for master-key material | 13 | [#9127](https://github.com/zeroclaw-labs/zeroclaw/issues/9127) |
| #8933 | Cross-turn conversation correlation to OTel export | 12 | [#8933](https://github.com/zeroclaw-labs/zeroclaw/issues/8933) |
| #7155 | Per-execution confirmation tier for high-risk shell commands | 11 | [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) |
| #9103 | Separate authoritative memory storage from enrichment connectors | 10 | [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) |
| #9106 | A2A outbound client (A2ATool) | 10 | [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) |

**Analysis:** The top concerns cluster around three themes:

1. **Memory architecture** (#9048, #9103, #6850) — Users and maintainers agree that conflating conversation history, durable memory, and enrichment connectors creates maintenance debt and incorrect lifecycle behavior. The project is moving toward a clean separation.
2. **Interoperability** (#8603, #9106) — The OpenAI Chat Completions adapter and A2A outbound tool both respond to operator demand for ZeroClaw agents to plug into the broader agent ecosystem (Open WebUI, LangChain, other A2A agents) without custom integration work.
3. **Security hardening** (#9127, #7155, #7141, #6996) — A sustained wave of RFCs targets credential abstraction, shell-risk tiers, pluggable authentication, and sandbox policy. The v0.9.0 milestone is clearly the vehicle for this work.

---

## 5. Bugs & Stability

| Issue | Severity | Description | Fix PR | Link |
|---|---|---|---|---|
| #9348 | **S1 — security risk** | WhatsApp Web in `business` mode replies to *every* DM and group; `allowed_groups` empty list acts as permit-all, not deny-all | RFC #9397 in progress | [#9348](https://github.com/zeroclaw-labs/zeroclaw/issues/9348) |
| #9417 | **S2 — degraded** | WhatsApp Cloud `request_approval` leaks live approval token on send failure or cancellation | — | [#9417](https://github.com/zeroclaw-labs/zeroclaw/issues/9417) |
| #9340 | **P1** | CLI-created cron jobs have `delivery.mode = "none"` hardcoded; output is silently discarded | — | [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) |
| #6157 | **S3 — minor** | Nextcloud Talk uses wrong bot message API URL | — | [#6157](https://github.com/zeroclaw-labs/zeroclaw/issues/6157) |
| #9037 | **P2** | `<eom>` terminal markers from OpenRouter leak into visible transcript and history | PR #9037 (open) | [#9037](https://github.com/zeroclaw-labs/zeroclaw/issues/9037) |

**Notable:** The WhatsApp S1 bug (#9348) is the most critical open stability issue. Follow-up RFC #9397 is in progress. No closed bugs appeared today.

---

## 6. Feature Requests & Roadmap Signals

| RFC / Issue | Summary | Likely Target | Link |
|---|---|---|---|
| #8603 | OpenAI Chat Completions adapter | v0.9.0 | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| #9106 | A2A outbound client (A2ATool) | v0.9.0 | [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) |
| #8780 | Realtime speech-to-speech channel for Gemini Live | v0.9.0+ | [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) |
| #9631 | Stable `session_id` to OpenRouter for prompt-cache savings | Near-term | [#9631](https://github.com/zeroclaw-labs/zeroclaw/issues/9631) |
| #7155 | Per-execution confirmation tier for shell commands | v0.9.0 | [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) |
| #8568 | Mixture-of-Agents virtual model provider | Future | [#8568](https://github.com/zeroclaw-labs/zeroclaw/issues/8568) *(closed)* |
| #6909 | Computer-use desktop support | v0.9.0 (implementation in PR #9091) | [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) |

**Prediction:** The OpenAI Chat Completions adapter (#8603) and A2A outbound client (#9106) are the strongest candidates for v0.9.0, as both have RFC-accepted status and clear operator demand. The eval system (PRs #9220–#9248) is also likely to ship as a cohesive unit. Prompt-cache support for OpenRouter (#9631) is small-enough to land sooner.

---

## 7. User Feedback Summary

- **Memory conflation is painful.** Multiple RFCs (#9048, #9103, #6850) independently flag the same root issue: conversation history and long-term memory are incorrectly treated as the same lifecycle domain, causing autosave paths to pollute durable memory and making eviction/governance logic fragile.
- **OpenAI ecosystem compatibility is a top interoperability ask.** Issue #8603 lists Open WebUI, LobeChat, Continue.dev, Aider, and LangChain as target clients — users want ZeroClaw agents to be consumable as standard Chat Completions backends.
- **WhatsApp security misconfiguration causes real harm.** The S1 bug (#9348) means operators who believe they've locked down group access are actually exposing the agent to every group. This undermines trust in the channel configuration model.
- **Cron output loss is silently frustrating.** Issue #9340 shows that CLI cron jobs run successfully but deliver nowhere, with no error indication — a poor developer experience for automated agent workflows.
- **Eval tooling is highly valued.** The five-PR eval stack from `IftekharUddin` suggests strong internal commitment to testability; users will benefit from regression-gated capabilities and JUnit CI integration.
- **Compact skill injection (#8313)** addresses prompt-context bloat — a recurring pain point for users running agents with large skill sets.

---

## 8. Backlog Watch

| Issue | Days Open | Why It Needs Attention | Link |
|---|---|---|---|
| #8692 | ~29 days | Maintainer decision queue tracker — dozens of RFCs are stalled pending decisions | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #7432 | ~24 days | v0.9.0 auth/security/gateway tracker — blocking issues for the next milestone | [#7432](https://github.com/zeroclaw-labs/zeroclaw/issues/7432) |
| #6489 | ~58 days | Unified capability catalog tracker — no maintainer update in weeks | [#6489](https://github.com/zeroclaw-labs/zeroclaw/issues/6489) |
| #7141 | ~60 days | Pluggable inbound auth RFC Rev 5 — target is Identity & Access milestone but no decision recorded | [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) |
| #7142 | ~60 days | Runtime-owned security decision pipeline — paired with #7141, both p1 | [#7142](https://github.com/zeroclaw-labs/zeroclaw/issues/7142) |
| #6996 | ~66 days | Granular sandbox policy (filesystem + network) — no maintainer review since update | [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| #7897 | ~46 days | Apply security/channel config updates without full daemon reload — p3 but impacts UX | [#7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897) |
| #7929 | ~45 days | Unify slash-command registries across web UI, zerocode, and channel runtime — no maintainer review | [#7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929) |

**Assessment:** The project has a healthy volume of contributor work but a narrowing bottleneck at the maintainer-decision layer. The v0.9.0 security and auth RFCs (#7141, #7142, #6996) are the highest-priority items requiring triage, as they gate both the milestone and operator trust. The WATI removal (#9571) and version bump (#9648) are the most likely near-term landing candidates if reviewer capacity allows.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*