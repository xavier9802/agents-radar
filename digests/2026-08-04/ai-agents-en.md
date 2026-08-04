# OpenClaw Ecosystem Digest 2026-08-04

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-04 03:18 UTC

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



# OpenClaw Project Digest — 2026-08-04

## 1. Today's Overview

OpenClaw is operating at **very high activity** today, with 500 issues and 500 PRs updated in the last 24 hours (463 open/active issues, 139 PRs merged or closed). Two patch releases were shipped, targeting Codex turn-handling regressions and npm plugin metadata compatibility. The most prominent theme across open issues is **message loss and silent failure modes** in agent turns and subagent completions — a cluster of diamond-lobster-rated bugs suggests the project is under significant reliability pressure on its core messaging layer.

## 2. Releases

### v2026.7.1-2 (2026-08-04)
- **npm plugin updates:** accept singleton-array metadata from newer npm clients so tracked official plugins can install and update to correction releases. (#108336)

### v2026.7.1-1 (2026-08-04)
- **Codex progress replies:** keep app-server turns running after delivered progress messages so GPT/Codex reaches its authoritative terminal response instead of stopping mid-turn. (#106961, #108487)
- **Memory Core startup repair:** recover derived legacy-index and ca… (truncated in source data)

**Migration notes:** None explicitly called out. The Codex fix (#106961) addresses a regression where turns were terminating prematurely — users on v2026.5.27+ should upgrade.

## 3. Project Progress

**139 PRs merged/closed** in the last 24 hours. Notable closed items:
- **#106504** (CLOSED): Per-agent model override not surfaced in `openclaw models` — display/mismatch fixed.
- **#39807** (CLOSED): Billing error (402) infinite retry death spiral for inline-apiKey providers — addressed via auth.cooldowns fix.
- **#45765** (CLOSED): `OPENCLAW_HOME` set to `~/.openclaw` produced nested directory `~/.openclaw/.openclaw`.
- **#116277** (CLOSED): DeepSeek v4 Flash silent reply failure — resolved.

Key PRs advancing today:
- **#118884** — Control UI queueing of distinct repeated submissions (#118881)
- **#119050** — Activate exact prepared local model on macOS setup
- **#118409** — Keep sandboxed gateway locks out of live state dirs (#118371)
- **#118900** — Preserve runtime env during service refresh (#118898)

## 4. Community Hot Topics

| Issue | Comments | Tags | Focus |
|---|---|---|---|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | 101 | diamond lobster, P1, message-loss | DeepSeek v4 Flash silent reply failure — **now closed** |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | 52 | diamond lobster, P1, session-state | Realtime voice work retaining unbounded provider/consult state |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 24 | off-meta tidepool, P2, security | Memory trust tagging by source — prevent memory poisoning |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 23 | diamond lobster, P1, message-loss | Subagent completion silently lost on timeout/drain |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 20 | platinum hermit, P3 | Centralized filename encoding utility for multi-encoding Content-Disposition |

**Analysis:** The community is overwhelmingly focused on **reliability of message delivery and session state**. The #116277 DeepSeek issue (101 comments) dominated discussion before closing. The realtime voice state unbounded retention (#116201) and subagent loss (#44925) reflect a pattern: the agent orchestration layer is losing work silently, a theme that recurs across dozens of open bugs.

## 5. Bugs & Stability

**P0 / Critical:**
- [#117956](https://github.com/openclaw/openclaw/issues/117956) — `claude-cli` backend produced ~13.7M metered Anthropic tokens despite `CLAUDE_CLI_CLEAR_ENV` scrubbing the API key. **Needs investigation.**
- [#103804](https://github.com/openclaw/openclaw/issues/103804) — service-env generator double-quotes values, breaking `AWS_REGION` hostname. **P0.**

**P1 — Message Loss / Session State (cluster):**
- [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice retains unbounded state
- [#44925](https://github.com/openclaw/openclaw/issues/44925) — Subagent completion silently lost
- [#87744](https://github.com/openclaw/openclaw/issues/87744) — Codex-backed Telegram turns timeout, never reach `turn/completed`
- [#84516](https://github.com/openclaw/openclaw/issues/84516) — Codex replies truncated at ~1000-1100 chars (stop=null, aborted=false)
- [#67777](https://github.com/openclaw/openclaw/issues/67777) — Subagent completion delivery lost on direct-announce timeout
- [#39476](https://github.com/openclaw/openclaw/issues/39476) — A2A `sessions_send` back-call causes duplicate messages
- [#52249](https://github.com/openclaw/openclaw/issues/52249) — ACP parent session stuck until refresh
- [#115700](https://github.com/openclaw/openclaw/issues/115700) — `chat.send` rejected with "thread switched branches" after model completes
- [#115037](https://github.com/openclaw/openclaw/issues/115037) — Synthetic "No response requested" on resume triggers model fallback
- [#116022](https://github.com/openclaw/openclaw/issues/116022) — beta.5 `/new` reuses stable session ID, cannot recover retired Codex tombstone
- [#111010](https://github.com/openclaw/openclaw/issues/111010) — Detached native Codex subagents lose hook relay on parent turn release
- [#89315](https://github.com/openclaw/openclaw/issues/89315) — Gateway heap grows unbounded, OOM killed on long-running Linux systemd deployments
- [#114234](https://github.com/openclaw/openclaw/issues/114234) — Usage-cost refresh lock never releasable after PID-reusing container restart

**P1 — Auth/Security:**
- [#47910](https://github.com/openclaw/openclaw/issues/47910) — Provider fallback by failure class (quarantine auth-broken providers)
- [#45508](https://github.com/openclaw/openclaw/issues/45508) — Self-hosted STT/TTS in webchat

**Regressions:**
- [#112906](https://github.com/openclaw/openclaw/issues/112906) — `\`\` renders broken in v2026.7.1 / v2026.7.1-2 (rich messages regression)
- [#116010](https://github.com/openclaw/openclaw/issues/116010) — All persistent sessions capped at 128k context regardless of model
- [#44502](https://github.com/openclaw/openclaw/issues/44502) — Discord routing / mention-gating regression
- [#50490](https://github.com/openclaw/openclaw/issues/50490) — Feishu activation mode switch ineffective

**Fix PRs in progress:**
- [#118884](https://github.com/openclaw/openclaw/pulls/118884) — Control UI repeated submissions
- [#118683](https://github.com/openclaw/openclaw/pulls/118683) — Link-understanding error body cancellation
- [#118650](https://github.com/openclaw/openclaw/pulls/118650) — Compaction guard against missing contextWind
- [#118900](https://github.com/openclaw/openclaw/pulls/118900) — Preserve runtime env during service refresh

## 6. Feature Requests & Roadmap Signals

| Issue | Comments | Summary |
|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 24 | **Memory Trust Tagging by Source** — tag entries by origin to prevent memory poisoning |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 20 | **Centralized filename encoding** — handle Shift-JIS, EUC-KR, GB18030 across all channel adapters |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | 9 | **YAML config support** alongside JSON5 |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | 9 | **MathJax/LaTeX** in Control UI (10 👍) |
| [#13700](https://github.com/openclaw/openclaw/issues/13700) | 6 | **Session snapshots** — save/load context checkpoints |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) | 6 | **TTL/Expiry for delivery queue** messages |
| [#16670](https://github.com/openclaw/openclaw/issues/16670) | 8 | **Memory/Embedding setup** as mandatory onboarding step |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | 7 | **Expose resolved backend model** in session_status |
| [#80752](https://github.com/openclaw/openclaw/issues/80752) | 6 | Optional `model` override in CommitmentsConfig |

**Likely to ship next:** Centralized filename encoding (#48788) has an open PR path; session snapshots (#13700) and TTL for delivery queue (#16555) address clear reliability gaps. Memory trust tagging (#7707) is a significant security feature but requires design work.

## 7. User Feedback Summary

**Dominant pain points:**
1. **Silent message/turn loss** — Users repeatedly report that agent turns end without delivering a reply, with no error visible. This affects Codex, subagents, and the Telegram channel. (Issues #87744, #84516, #44925, #67777, #116277)
2. **API billing surprise** — Issue #117956 describes ~13.7M tokens billed despite environment scrubbing, raising trust concerns.
3. **Context cap hard-stop** — All persistent sessions capped at 128k regardless of model config (#116010).
4. **Channel-specific regressions** — Feishu activation mode (#50490), Discord mention-gating (#44502), Windows scheduled task instability (#91144).
5. **Setup/UX friction** — Nested home dirs (#45765), model override invisible in UI (#106504), local model activation (#119049).

**Satisfaction signals:** The #116277 DeepSeek closure (101 comments → resolved) was warmly received. The billing death spiral fix (#39807) addresses a critical reliability concern. Several regressions are being actively patched.

## 8. Backlog Watch

| Issue | Age | Tags | Status |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging | 6 months | P2, security, needs-maintainer-review | Stuck — needs product decision |
| [#87561](https://github.com/openclaw/openclaw/issues/87561) — Durable final fallback delivery semantics | ~2 months | P1, message-loss, needs-maintainer-review | Awaiting design |
| [#89315](https://github.com/openclaw/openclaw/issues/89315) — Gateway heap unbounded growth → OOM | ~2 months | P1, crash-loop | Needs repro + fix |
| [#112906](https://github.com/openclaw/openclaw/issues/112906) — `\`\`` broken in v2026.7.1 | 12 days | P2, regression, recovery-stuck | Likely needs urgent fix |
| [#117956](https://github.com/openclaw/openclaw/issues/117956) — Anthropic billing leak despite env scrub | 2 days | P1, security, recovery-stuck | **High priority** — trust impact |
| [#116010](https://github.com/openclaw/openclaw/issues/116010) — 128k context cap hard-stop | 6 days | P1, behavior bug | Needs product decision |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice unbounded state | 5 days | P1, diamond lobster | Needs product decision |

**Maintainer attention needed most urgently on:** #117956 (security/billing trust), #112906 (regression in latest release), #89315 (OOM on long-running deployments), and #116201 (unbounded state retention — architectural concern).

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date: 2026-08-04**

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape is experiencing a maturation wave, with projects shifting from feature expansion to reliability hardening and architectural structuring. Twelve projects were surveyed; eight show active development, three are in quiet maintenance or dormant states, and one (ZeptoClaw) reported zero activity. The dominant cross-cutting concern is **message and session reliability** — silent turn losses, session-state corruption, and audit-trail falsification appear across OpenClaw, ZeroClaw, CoPaw, and NanoClaw. A secondary wave of focus is **provider compatibility fragmentation**, as every active project invests in supporting an expanding set of LLM backends (Anthropic Opus 5, DeepSeek, Gemini, Codex, local Ollama). The ecosystem is clearly segmenting into tier-1 platforms (OpenClaw, Hermes, IronClaw, CoPaw) with enterprise-grade scope and tier-2/niche projects (PicoClaw, NullClaw, LobsterAI, Moltis) targeting specific deployment patterns.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Merged/Closed | Release | Health Score* |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 139 | ✅ v2026.7.1-2 | 7.2/10 |
| **Hermes Agent** | 50 | 50 | 6 | ✅ v0.20.0 (yesterday) | 8.5/10 |
| **IronClaw** | 47 | 50 | 17 | ❌ | 8.0/10 |
| **ZeroClaw** | 50 | 50 | ~1 | ❌ | 7.5/10 |
| **CoPaw** | 14 | 50 | ~10 | ✅ v2.1.0-beta.1 | 8.0/10 |
| **NanoBot** | 3 | 32 | 20 | ❌ | 8.5/10 |
| **LobsterAI** | 2 | 12 | 7 | ❌ | 6.5/10 |
| **NanoClaw** | 1 | 9 | 6 | ❌ (image pin only) | 7.0/10 |
| **NullClaw** | 1 | 5 | 2 | ❌ | 6.0/10 |
| **PicoClaw** | 8 | 5 | 3 | ❌ | 6.5/10 |
| **Moltis** | 0 | 1 | 0 | ❌ | 4.5/10 |
| **ZeptoClaw** | 0 | 0 | 0 | ❌ | 2.0/10 |

*Health Score synthesizes activity velocity, release cadence, bug-fix throughput, and community engagement signals from digest data.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of operation:** OpenClaw handles 500× the issue/PR volume of the next most-active projects, indicating the largest user base and broadest deployment surface (Codex, Telegram, A2A, ACP, DeepSeek, Realtime voice).
- **Release discipline:** Two patch releases in 24 hours demonstrates rapid regression-response capability — a pattern no other project matches.
- **Breadth of channel coverage:** The only project with deep integrations across Codex, Telegram, Discord, Feishu, and A2A/ACP agent-to-agent protocols.

**Technical approach differences:**
- OpenClaw's core reliability challenge is the **messaging/turn-delivery layer** — silent message loss across subagents and gateway timeouts form a distinct bug cluster absent in other projects. This suggests OpenClaw's multi-agent orchestration depth creates unique consistency problems.
- Unlike NanoBot (provider-compatibility focus) or IronClaw (Rust crate-layer restructuring), OpenClaw's complexity is **operational**: session state management, gateway heap growth, and billing-trust surface.
- OpenClaw's community is the most vocal about **silent-failure modes** (diamond-lobster-rated bugs), indicating users are running the system at production scale where reliability gaps are costly.

**Community size comparison:** OpenClaw's issue comment counts (101 on #116277, 52 on #116201) far exceed any other project's engagement, confirming it as the ecosystem's largest community by an order of magnitude.

---

## 4. Shared Technical Focus Areas

| Theme | Projects Involved | Specific Need |
|---|---|---|
| **Message/Turn Reliability** | OpenClaw, ZeroClaw, CoPaw, NanoClaw | Silent delivery failures, timeout-based subagent loss, session-state corruption on resume |
| **Provider Compatibility** | NanoBot, OpenClaw, CoPaw, LobsterAI | Opus 5 support, DeepSeek reasoning items, custom provider scaling (LobsterAI raised cap to 20), Responses API standardization |
| **Channel-Specific Bugs** | OpenClaw, Hermes, CoPaw, ZeroClaw, LobsterAI | Telegram duplicates, Feishu timeouts, Discord routing regressions, WeChat cron silent failures |
| **Session Lifecycle Management** | NanoClaw, CoPaw, ZeroClaw, PicoClaw | Missing transcripts on resume, premature cleanup of cold sessions, stale session identity after channel switches |
| **Desktop/UX Resilience** | CoPaw, Hermes, LobsterAI, PicoClaw | WebView2 crash recovery, zombie process handling, input lag with long history, IME/keyboard behavior |
| **MCP Integration Maturity** | NanoBot, NullClaw, Moltis, NanoClaw | Error envelope handling, remote MCP server support, structured streaming tool calls, managed repository bundles |
| **Observability & Audit** | ZeroClaw, OpenClaw, IronClaw | OTel trace correlation, audit-trail accuracy (timeout-as-denial bug), prompt-cache visibility |
| **Cost/Billing Trust** | OpenClaw, CoPaw | Token leakage despite env scrubbing, silent 44M-token cron burn, prompt-cache parameter support |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | CoPaw | NanoBot | ZeroClaw |
|---|---|---|---|---|---|---|
| **Core Strength** | Multi-channel orchestration at scale | Platform adapter breadth + desktop app | Rust-native crate architecture + safety | Qwen/Alibaba ecosystem integration | Provider compatibility density | Goal-mode architecture + observability |
| **Target User** | Enterprise/self-hosted operators | Multi-platform power users | Embedded/Rust-centric developers | Qwen model ecosystem users | LLM provider flexibility seekers | Architecture-forward researchers |
| **Architecture** | Node.js gateway + subagent model | Multi-language adapters + Electron | Rust crates with WIT/component model | TypeScript/JavaScript stack | Python backend + React WebUI | TypeScript with structured runtimes |
| **Key Differentiator** | Codex + A2A/ACP agent-to-agent | v0.20.0 monolithic release momentum | Wave-based refactoring discipline | GPT-5.6 prompt caching, model fallback | Deepest provider support (Opus 5, DeepSeek, Gemini, ModelScope, Eden AI) | Goal mode RFCs, structured observability |
| **Deployment Model** | npm/service + gateway | Service + desktop app | Cargo/Rust tooling | Desktop + web | WebUI + CLI | Web + daemon |

---

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Enterprise-Grade Scope:**
- **Hermes Agent** and **OpenClaw** lead in raw activity. Hermes benefits from a刚-shipped major release (v0.20.0, ~3,650 commits, 1,400 PRs, 650+ contributors) creating sustained follow-on activity. OpenClaw's volume reflects its larger user base but also its reliability压力.
- **IronClaw** and **CoPaw** show disciplined, high-throughput development with clear architectural roadmaps (Wave refactors, v2.1.0 stabilization).

**Tier 2 — Active & Focused:**
- **NanoBot** demonstrates the highest merge efficiency (20/32 PRs merged), indicating a lean, responsive contributor base. Its focus on provider compatibility makes it a canary for emerging model integration issues.
- **ZeroClaw** is in a design-intensive phase with multiple RFCs in flight, suggesting architectural ambition over shipping velocity.
- **NanoClaw** is in a hardening phase — session management fixes and image security are the priority, indicating a transition from feature-building to production readiness.

**Tier 3 — Maintenance/Steady State:**
- **LobsterAI** and **PicoClaw** show moderate, production-oriented activity focused on bug resolution and incremental features.
- **NullClaw** is steady but narrow, with recent wins in streaming tool-calls and proxy transport.

**Tier 4 — Dormant/Quiet:**
- **Moltis** is in a low-activity maintenance phase with a single PR in flight.
- **ZeptoClaw** shows zero activity, suggesting project dormancy or a very small community.

---

## 7. Trend Signals

1. **Streaming Tool-Call Pipelines Are Becoming Table Stakes** — NullClaw (#964, #965) and ZeroClaw's OTel trace work reflect a broader industry need for real-time, observable agent loops. Developers should prioritize streaming-native tool execution as a differentiator.

2. **Provider Fragmentation Is Driving Standardization Efforts** — NanoBot's `ResponsesCapabilities` refactor (#5204) and OpenClaw's provider-fallback quarantine (#47910) signal that the community is moving toward declarative provider capability profiles rather than ad-hoc per-model fixes.

3. **Silent Failure Is the #1 Trust Erosion Vector** — Across OpenClaw (message loss cluster), CoPaw (WeChat cron 44M-token burn), and ZeroClaw (timeout-as-denial audit falsification), the pattern is consistent: failures that don't surface errors are more damaging than loud failures. This is an emerging design principle — **fail-visible-by-default** should be a core architecture requirement.

4. **Goal Mode / Structured Agent Orchestration Is an Emerging Paradigm** — ZeroClaw's three-part goal mode RFC (#8303, #9702, #9703) and NanoBot's cross-session search (#5211) indicate the community is moving beyond turn-by-turn interaction toward bounded, multi-turn objective systems. This is a potential category-defining direction.

5. **Desktop-First Deployment Is maturing but Fragile** — WebView2 crash recovery (CoPaw #6647), zombie process handling (Hermes #78099), and Windows process cleanup (LobsterAI #2420) are all independent projects solving the same class of problem. Desktop agent resilience is a shared infrastructure gap.

6. **Cost-Aware Agent Design Is Entering Mainstream** — GPT-5.6 prompt caching (#6649), billing leak investigations (#117956), and token waste from silent cron failures (#6614) are converging signals that enterprise users are now measuring and minimizing agent operating costs. Prompt cache support and cost observability will be competitive differentiators.

7. **MCP Ecosystem Is Maturing Beyond Local-Only** — NullClaw's streaming MCP support, Moltis's managed repository bundles (#1183), and NanoClaw's remote Streamable HTTP MCP (#3092) all point toward distributed, shareable MCP topologies as the next infrastructure layer.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-04

## 1. Today's Overview

NanoBot shows strong development momentum with **32 PRs updated** and **3 issues touched** in the last 24 hours. Activity is heavily PR-driven: 20 PRs were merged or closed, indicating an active contributor base shipping fixes and features. No new releases were published today, so changes are accumulating on the main branch. The project is actively addressing both provider compatibility (Anthropic Opus 5, Gemini tool-call validation, DeepSeek reasoning items) and WebUI quality-of-life issues (i18n audit, IME stability, mobile keyboard behavior). Overall health is **good** — high merge throughput, clear bug-fix velocity, and expanding provider coverage.

## 2. Releases

*No new releases published today.*

---

## 3. Project Progress

### Merged / Closed PRs (Today)

| PR | Type | Summary |
|----|------|---------|
| [#5236](https://github.com/HKUDS/nanobot/pull/5236) | Fix · Anthropic · P1 | Support Opus 5 effort controls; replaces hard-coded sampling-param exclusions with model-family version thresholds |
| [#5228](https://github.com/HKUDS/nanobot/pull/5228) | Fix · WebUI · P1 | Persist and return actual local trigger messages in automation payloads; fixes session popover showing stale content |
| [#5227](https://github.com/HKUDS/nanobot/pull/5227) | Fix · WebUI · P1 | Complete i18n audit — key/interpolation parity, Chinese terminology corrections (`网页` → `网络`), accessibility label localization |
| [#5232](https://github.com/HKUDS/nanobot/pull/5232) | Feature · Mattermost · P2 | Separate `groupPolicyInThread` config for threads vs. main channels, exposed in WebUI (follow-up to #4459) |
| [#5214](https://github.com/HKUDS/nanobot/pull/5214) | Fix · Providers · P1 | Keep DeepSeek reasoning items wire-valid in OpenAI Responses API routing — fixes serde deserialization errors |
| [#1550](https://github.com/HKUDS/nanobot/pull/1550) | Feature · Codex · P2 | Dual-mode `openai_codex`: OAuth (original) + custom Responses mode when `api_base`/`api_key` are set |
| [#5038](https://github.com/HKUDS/nanobot/pull/5038) | Docs · Providers · P2 | Added ModelScope (魔搭) provider documentation with copyable JSON setup |
| [#4861](https://github.com/HKUDS/nanobot/pull/4861) | Feature · Providers · P2 | Added Eden AI as a built-in OpenAI-compatible gateway provider |
| [#5141](https://github.com/HKUDS/nanobot/pull/5141) | Fix · Cron · P2 | Validate cron expression syntax at schedule creation time instead of failing silently at trigger runtime |
| [#5229](https://github.com/HKUDS/nanobot/pull/5229) | Fix · WebUI · P2 | Stabilize thread during IME composition input — defer autosizing while composing, preserve scroll position |
| [#5226](https://github.com/HKUDS/nanobot/pull/5226) | Fix · WebUI · P2 | Dismiss mobile keyboard after send on touch-primary devices; adds regression test |
| [#5215](https://github.com/HKUDS/nanobot/pull/5215) | Fix · Gateway · P1 | Close agent resources deterministically on gateway stop — eliminates asyncio teardown noise and stall on shutdown |
| [#5213](https://github.com/HKUDS/nanobot/pull/5213) | Fix · Plugins · P2 | Fall back to `uv` when `pip` is unavailable (supports `uv tool` environments) |
| [#2186](https://github.com/HKUDS/nanobot/pull/2186) | Docs · P2 | Added QuackExchange joining instructions to README (closed after merge) |

**Key theme:** A wave of **provider compatibility fixes** (Opus 5, DeepSeek, Gemini, ModelScope, Eden AI) and **WebUI polish** (i18n, IME, mobile) were shipped today, alongside a new Metasearch provider proposal in progress.

---

## 4. Community Hot Topics

| Item | Type | Activity | Link |
|------|------|----------|------|
| [#5235](https://github.com/HKUDS/nanobot/issues/5235) | Bug · Anthropic · P1 | Created today, 1 comment | Issue tracker |
| [#5237](https://github.com/HKUDS/nanobot/issues/5237) | Bug · MCP · P1 | Created today, 0 comments | Issue tracker |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | Feature · Metasearch · P1 | Open, no comments yet | PR tracker |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | Feature · Sessions · P2 | Open, cross-session search | PR tracker |
| [#5204](https://github.com/HKUDS/nanobot/pull/5204) | Refactor · Providers · P1 | Open, Responses capabilities | PR tracker |
| [#5231](https://github.com/HKUDS/nanobot/pull/5231) | Feature · Memory · P2 | Open, idle session archival | PR tracker |

**Analysis:**

- **Opus 5 adoption** is driving both a bug report (#5235) and a fix PR (#5236) on the same day — users are pushing the new model and hitting configuration gaps immediately. This reflects active experimentation with the latest Claude models.
- **MCP error handling** (#5237) surfaced as a new pain point: business-level 404s wrapped in `isError=False` envelopes are invisible to the agent. This signals growing MCP integration usage where error semantics matter.
- **Metasearch integration** (#5234) and **cross-session search** (#5211) indicate users want deeper conversational context and richer web discovery — both are P1/P2 features in flight.
- **Responses capabilities refactor** (#5204) shows the maintainer is systematizing provider behavior declarations, a structural investment that should reduce future compatibility bugs.

---

## 5. Bugs & Stability

| Rank | Issue | Severity | Summary | Fix PR |
|------|-------|----------|---------|--------|
| 1 | [#5235](https://github.com/HKUDS/nanobot/issues/5235) | **High** | Opus 5 temperature config rejected by API — `omit_temperature` list missing `"opus-5"` | [#5236](https://github.com/HKUDS/nanobot/pull/5236) [OPEN, same day] |
| 2 | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | **High** | MCP tool returns business-error envelope with `isError=False`; agent treats it as success and waits for `tool_timeout` | *No fix yet* |
| 3 | [#5190](https://github.com/HKUDS/nanobot/issues/5190) | **Medium** | Frontend module scripts fail with MIME type `text/plain` — likely a server config issue | [#5190] closed 2026-08-03 (resolution not specified in data) |

**Notes:**
- The Opus 5 bug is already being addressed in real-time by PR #5236 (merged today), demonstrating healthy triage velocity.
- The MCP envelope issue (#5237) has no fix PR yet — this is a silent-correctness bug that could cause agents to loop indefinitely on failing tools.
- The MIME type issue (#5190) was closed within 3 days but appears to be an environment/config issue rather than a code defect.

---

## 6. Feature Requests & Roadmap Signals

| PR | Feature | Priority | Likelihood for Next Release |
|----|---------|----------|----------------------------|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | Meta-Search (MST) provider — RRF aggregation across DuckDuckGo, Google, Brave, Bing | P1 | **High** — well-scoped, follows existing provider pattern |
| [#5233](https://github.com/HKUDS/nanobot/pull/5233) | Mattermost thread-specific `groupPolicyInThread` config | P2 | **Medium** — niche channel, depends on #5232 precedent |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | Cross-session search and `@` mentions across persisted conversations | P2 | **Medium** — requires stable session references, non-trivial |
| [#5231](https://github.com/HKUDS/nanobot/pull/5231) | Archive idle Dream sessions to `history.jsonl` | P2 | **Low-Medium** — addresses an edge case in memory pipeline |
| [#5204](https://github.com/HKUDS/nanobot/pull/5204) | Declarative `ResponsesCapabilities` profile for provider routing | P1 | **High** — structural refactor benefiting all future providers |

**Roadmap inference:** The project is clearly investing in (1) **provider diversity** (new search, new LLM gateways, new model support), (2) **Responses API standardization**, and (3) **WebUI maturity** (i18n, mobile, IME). Expect the next release to highlight metasearch, Opus 5 support, and gateway shutdown stability.

---

## 7. User Feedback Summary

| Pain Point | Source | Sentiment |
|------------|--------|-----------|
| Opus 5 configuration silently fails — temperature parameter not dropped | #5235 | Frustrated; breaking new-model adoption |
| MCP business errors invisible to agent — no way to recover from 404s | #5237 | Confused; agent loops waiting for timeout |
| Frontend JS module load failure on startup | #5190 | Blocker for new users; resolved quickly |
| Trigger messages not shown in WebUI session popover | Pre-#5228 | Minor UX gap; now fixed |
| Chinese i18n terminology inconsistent (`网页` vs `网络`) | Pre-#5227 | Localization quality concern; now fixed |
| IME composition breaks thread layout | Pre-#5229 | Mobile/Asian-language user friction; now fixed |
| Mobile keyboard doesn't dismiss after send | Pre-#5226 | Minor mobile UX issue; now fixed |
| Gateway shutdown stalls with asyncio errors | Pre-#5215 | Operational reliability concern; now fixed |

**Overall:** Users report real integration-level bugs (MCP, Opus 5) that block production use, alongside WebUI polish issues affecting daily interaction. The maintainers are responding rapidly — 6 WebUI fixes merged in a single day, and the Opus 5 bug has a fix PR same-day. Satisfaction appears **moderate-to-high** given the velocity, though the MCP silent-failure bug remains unresolved.

---

## 8. Backlog Watch

| Item | Age | Reason for Attention |
|------|-----|---------------------|
| [#5237](https://github.com/HKUDS/nanobot/issues/5237) | 0 days | MCP business-error envelope bug — no fix PR yet; high-severity silent failure |
| [#5233](https://github.com/HKUDS/nanobot/pull/5233) | 1 day | Mattermost thread policy PR — open, may need maintainer review after #5232 merged |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | 1 day | Metasearch provider — P1 feature, open, awaiting review |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | 3 days | Cross-session search — longer-running feature PR, needs triage |
| [#5231](https://github.com/HKUDS/nanobot/pull/5231) | 1 day | Idle session archival — niche but correct; low priority for review |
| [#5204](https://github.com/HKUDS/nanobot/pull/5204) | 3 days | Responses capabilities refactor — structural, may need extended review |

**Recommended maintainer focus:**
1. **Issue #5237** — Acknowledge or assign a fix; silent MCP error handling is a correctness gap affecting production agents.
2. **PR #5234** — Metasearch is a high-value feature; timely review would expand the project's search capabilities.
3. **PR #5204** — The declarative capabilities refactor is foundational; getting it right now prevents future provider bugs.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-04

## 1. Today's Overview
Hermes Agent is in a high‑velocity development phase, with **50 issues and 50 PRs updated in the last 24 hours**. Activity is strongly driven by the recent **v0.20.0 (“The Herald Release”)** shipped yesterday, which aggregated ~3,650 commits and ~1,400 merged PRs. The project shows robust community engagement: 45 open/active issues, 44 open PRs, and 5 closed issues + 6 merged/closed PRs today. Health indicators are positive—bug‑fix momentum is strong, especially around platform adapters (Telegram, Slack, Discord, Feishu, WeCom) and desktop‑app stability.

## 2. Releases
**v0.20.0 (v2026.8.3) — released 2026‑08‑03**  
- **Scale:** ~3,650 commits, ~1,400 merged PRs, ~5,200 files changed, ~559K insertions, ~405K deletions, ~1,200 issues closed, 650+ contributors.  
- **Notes:** Release notes are light on detailed changelog; the “Herald” theme suggests major architectural or platform expansions. No explicit breaking‑change warnings were listed in the data provided.  
- **Link:** [NousResearch/hermes‑agent v0.20.0 release](https://github.com/NousResearch/hermes‑agent/releases/tag/v2026.8.3)

## 3. Project Progress
**Merged/Closed Today (6 PRs)**  
- **#77944** [CLOSED] – Fixes empty `tool_calls: []` causing HTTP 400 on strict providers (DeepSeek v4, Kimi). Drops stale empty arrays during session repair.  
- **Other merged/closed PRs** (from the 50‑item set) likely include additional bug fixes and test coverage, but only #77944 is explicitly marked closed in the top‑20 list.

**Key Closed Issues (5)**  
- #71319 – Fixed stale‑lock recovery for Windows `cua‑driver` installer.  
- #5333 – Tests now ignore runner‑auth/backend‑env leakage.  
- #78072 – Custom‑provider model.name now correctly uses runtime name, not display name.  
- #77320 – **P0 fix** for prompt‑cache loss caused by workspace‑prefix stripping in WebUI replay.  
- #78099 – Desktop app no longer exits silently when a zombie Electron process holds the singleton lock.

**Link to today’s merged/closed PRs:** [NousResearch/hermes‑agent/pulls?q=is%3Apr+updated%3A2026‑08‑04](https://github.com/NousResearch/hermes‑agent/pulls?q=is%3Apr+updated%3A2026‑08‑04)

## 4. Community Hot Topics
**Most‑commented open issues (by engagement):**

1. **#66589** – Telegram startup notification fails after planned restart (race between `_send_path_degraded` clear and startup notifications). **7 comments**.  
   → *Underlying need:* Reliable gateway‑restart signaling for Telegram admins.  
   [Link](https://github.com/NousResearch/hermes‑agent/issues/66589)

2. **#71047** – `hermes config set` duplicates top‑level keys; Telegram streaming + `reply_to_mode='first'` duplicates final message. **6 comments**.  
   → *Underlying need:* Config‑parsing robustness and correct streaming behavior.  
   [Link](https://github.com/NousResearch/hermes‑agent/issues/71047)

3. **#49363** – Desktop app should load dashboard plugins (runtime‑contract parity with web). **5 comments**.  
   → *Underlying need:* Feature parity between Electron desktop and web dashboard.  
   [Link](https://github.com/NousResearch/hermes‑agent/issues/49363)

4. **#75778** – Desktop update spawns duplicate `hermes‑setup` instance, causing “failed” window that masks real update. **4 comments**.  
   → *Underlying need:* Reliable desktop update flow on macOS.  
   [Link](https://github.com/NousResearch/hermes‑agent/issues/75778)

5. **#416** – Skill Validation & Linting for automated quality checks on skill create/edit. **4 comments, 1 👍**.  
   → *Underlying need:* Prevent broken skills from being accepted and failing at runtime.  
   [Link](https://github.com/NousResearch/hermes‑agent/issues/416)

**Link to most‑commented issues:** [NousResearch/hermes‑agent/issues?q=is%3Aissue+sort%3Acomments+updated%3A2026‑08‑04](https://github.com/NousResearch/hermes‑agent/issues?q=is%3Aissue+sort%3Acomments+updated%3A2026‑08‑04)

## 5. Bugs & Stability
**Reported today (ranked by severity):**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **P0** | [#77320](https://github.com/NousResearch/hermes‑agent/issues/77320) | WebUI user messages lose workspace prefix on replay, nuking prompt cache every turn. | ✅ Closed (merged) |
| **P2** | [#78106](https://github.com/NousResearch/hermes‑agent/issues/78106) | Slack mention triggers run but mention context is stripped before agent response. | – |
| **P2** | [#78105](https://github.com/NousResearch/hermes‑agent/issues/78105) | Desktop draft text carries over between chat sessions. | – |
| **P2** | [#78103](https://github.com/NousResearch/hermes‑agent/issues/78103) | `hermes config set` writes JSON‑array values as literal strings, discarding selection. | – |
| **P2** | [#78099](https://github.com/NousResearch/hermes‑agent/issues/78099) | Desktop silently exits when SingletonLock held by zombie Electron process (Linux/X11). | ✅ Closed |
| **P2** | [#78089](https://github.com/NousResearch/hermes‑agent/issues/78089) | Windows venv‑blocker preflight still aborts desktop Update for `.hermes‑runtime` gateways. | – |
| **P2** | [#75778](https://github.com/NousResearch/hermes‑agent/issues/75778) | Desktop update handoff produces duplicate `hermes‑setup` instance that fails. | – |
| **P2** | [#73692](https://github.com/NousResearch/hermes‑agent/issues/73692) | `agent.disabled_toolsets: [browser]` silently removes `web_search` due to conflicting implementations. | – |
| **P2** | [#71047](https://github.com/NousResearch/hermes‑agent/issues/71047) | Config set duplicates top‑level key; Telegram streaming duplicates final message. | – |
| **P2** | [#66589](https://github.com/NousResearch/hermes‑agent/issues/66589) | Telegram startup notification fails after planned restart (race condition). | – |
| **P2** | [#25620](https://github.com/NousResearch/hermes‑agent/issues/25620) | Feishu merge‑forward messages produce empty `[Merged forward message]`. | – |
| **P2** | [#11358](https://github.com/NousResearch/hermes‑agent/issues/11358) | Discord voice messages ship a flat waveform instead of real audio loudness. | – |
| **P2** | [#4913](https://github.com/NousResearch/hermes‑agent/issues/4913) | Custom endpoint metadata lookup can hit `/models` without auth. | – |
| **P2** | [#32201](https://github.com/NousResearch/hermes‑agent/issues/32201) | ACP `session/resume` replays history despite advertising resume capability. | – |
| **P2** | [#78139](https://github.com/NousResearch/hermes‑agent/issues/78139) | WeCom rate‑limit circuit breaker makes built‑in retry/backoff unreachable. | – |

**Notable closed bug:**  
- **#77944** – Fixes empty `tool_calls` causing HTTP 400 on DeepSeek/Kimi.  
- **#71319** – Windows installer stale‑lock recovery now works.  
- **#78072** – Custom‑provider name‑mismatch bug fixed.

**Link to open bug issues:** [NousResearch

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-04

## 1. Today's Overview
PicoClaw shows steady, production-oriented development momentum as of 2026-08-04, with 8 issues and 5 pull requests updated in the past 24 hours. Activity is skewed toward bug resolution and infrastructure hardening: 5 issues were closed and 3 PRs were merged, while 3 issues and 2 PRs remain open. No new releases were published, but the recent merge activity on routing normalization, authentication, and internationalization indicates a maturing codebase. Community engagement is healthy, with users rapidly reporting deployment friction and contributors responding with targeted fixes.

## 2. Releases
No new releases were published in the last 24 hours. The 3 merged PRs today will likely be bundled into the next patch or minor release.

## 3. Project Progress
**Merged/Closed Today:**
- [#3202](https://github.com/sipeed/picoclaw/pull/3202) – Fixed agent/account ID normalization to strip leading/trailing underscores, aligning with the `^[a-z0-9][a-z0-9_-]{0,63}$` routing regex.
- [#3267](https://github.com/sipeed/picoclaw/pull/3267) – Resolved an Antigravity provider scope bug that caused token refresh failures after primary auth succeeded.
- [#3273](https://github.com/sipeed/picoclaw/pull/3273) – Added complete Japanese (`ja`) localization to the WebUI, matching the existing documentation translation.

**Open/In-Progress:**
- [#3316](https://github.com/sipeed/picoclaw/pull/3316) – Restores history, summarization, compression, and seahorse bootstrap handling for agents routed via dispatch rules.
- [#3315](https://github.com/sipeed/picoclaw/pull/3315) – Extends Telegram topic support to private bot chats by leveraging `IsTopicMessage` instead of relying solely on `IsForum`.

## 4. Community Hot Topics
- [#3281](https://github.com/sipeed/picoclaw/issues/3281) (3 comments, 1 👍) – Web UI chat input lag with moderately long history. Reflects a growing need for frontend virtualization or lazy-loaded message rendering.
- [#3269](https://github.com/sipeed/picoclaw/issues/3269) (2 comments, 1 👍) – MCP connection failures cause the agent loop to hang, freezing the chat interface. Highlights production reliability expectations for tool integrations.
- [#3316](https://github.com/sipeed/picoclaw/pull/3316) – Directly addresses multi-agent dispatch routing, a core PicoClaw differentiator that users are stress-testing.
- [#3315](https://github.com/sipeed/picoclaw/pull/3315) – Fills a channel-parity gap in Telegram, enabling forum-style private bot conversations.

## 5. Bugs & Stability
**High Severity (Unresolved)**
- [#3269](https://github.com/sipeed/picoclaw/issues/3269) – MCP connection failure halts the agent loop and stops UI replies. No fix PR yet.
- [#3301](https://github.com/sipeed/picoclaw/issues/3301) – `/clear` and session auto-compression fail for chats routed to non-default agents. Open PR [#3316](https://github.com/sipeed/picoclaw/pull/3316) may resolve this but remains unverified.

**Medium Severity (Unresolved)**
- [#3281](https://github.com/sipeed/picoclaw/issues/3281) – Web UI input lag increases with chat history length.
- [#3264](https://github.com/sipeed/picoclaw/issues/3264) – `SplitMessage` enters an infinite loop when a fenced code block info string exceeds chunk boundaries. No fix PR yet.

**Resolved Today**
- [#3268](https://github.com/sipeed/picoclaw/issues/3268) – `exec` tool `action` parameter now defaults to `"run"`.
- [#3265](https://github.com/sipeed/picoclaw/issues/3265) – Gateway no longer crashes on unconfigured `deltachat` channel types.
- [#3276](https://github.com/sipeed/picoclaw/issues/3276) – Launcher correctly detects systemd-managed gateways without hard-failing.

## 6. Feature Requests & Roadmap Signals
- Japanese localization request [#3272](https://github.com/sipeed/picoclaw/issues/3272) → fulfilled via [#3273](https://github.com/sipeed/picoclaw/pull/3273), signaling a growing non-English user base.
- Systemd/external gateway lifecycle support [#3276](https://github.com/sipeed/picoclaw/issues/3276) → resolved, confirming maturing headless deployment workflows.
- Telegram private topic parity [#3315](https://github.com/sipeed/picoclaw/pull/3315) → indicates continued push for cross-channel feature alignment.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-04

## 1. Today's Overview

NanoClaw is showing strong development momentum with 9 PRs updated in the last 24 hours, of which 6 were merged or closed. The project is in an active hardening phase, with core-team-driven fixes targeting session management stability, image security, and channel-specific reliability. A single open issue (#3179) highlights a Node.js compatibility concern with `node:util`, while three PRs remain open for review. No new releases were shipped today, suggesting the team is consolidating fixes before the next version bump.

## 2. Releases

No new releases today. The most recent image pin was `hardened-2026-08-02` (PR #3182), which remains the latest baseline.

## 3. Project Progress

**Merged/Closed PRs:**

- **#3182** — Repinned the agent image to `hardened-2026-08-02` ([link](https://github.com/nanocoai/nanoclaw/pull/3182)). Same agent content; refreshed base for security hardening.
- **#3180** — Surfaces hardened image migration as an operational/container skill, enabling self-serve rollout ([link](https://github.com/nanocoai/nanoclaw/pull/3180)).
- **#3137** — Fixed engagement consistency and exposed self-serve wiring controls for group-scoped agents ([link](https://github.com/nanocoai/nanoclaw/pull/3137)). Agents can now inspect their wirings and request approved engagement-policy updates without triggering spurious warm-container follow-ups.
- **#3181** — iMessage channel now opts in via first message to the assigned line ([link](https://github.com/nanocoai/nanoclaw/pull/3181)).
- **#3143** — Resolved approval cards now persist their title, request details, and original body content even after button replacement with decision/timeout status ([link](https://github.com/nanocoai/nanoclaw/pull/3143)).
- **#3178** — Accidentally opened against the wrong repository; closed with no upstream change requested ([link](https://github.com/nanocoai/nanoclaw/pull/3178)).

**Still Open:**

- **#3184** — Fixes session resume crash when a stored continuation's transcript file is missing ([link](https://github.com/nanocoai/nanoclaw/pull/3184)).
- **#3183** — Pins `cleanupPeriodDays` to prevent retention cleanup from reaping still-active cold sessions ([link](https://github.com/nanocoai/nanoclaw/pull/3183)).
- **#3092** — Adds support for remote Streamable HTTP MCP servers ([link](https://github.com/nanocoai/nanoclaw/pull/3092)).

## 4. Community Hot Topics

- **Issue #3179** — `SyntaxError: The requested module 'node:util' does not provide an export named 'styleText'` ([link](https://github.com/nanocoai/nanoclaw/issues/3179)). Authored by `benjamin920102`. This is the only open issue and stems from `@clack/core@1.2.0` depending on a Node.js API unavailable in the user's runtime. It indicates a growing need for clearer Node.js version requirements or a fallback strategy for `styleText`.
- **PR #3092** — Remote Streamable HTTP MCP server support has been open since 2026-07-19 with no merge activity in the last two weeks ([link](https://github.com/nanocoai/nanoclaw/pull/3092)). The sustained interest signals user demand for distributed MCP topologies beyond local-only servers.

## 5. Bugs & Stability

Ranked by severity:

| # | Severity | Issue / PR | Description |
|---|----------|------------|-------------|
| 1 | **High** | [PR #3184](https://github.com/nanocoai/nanoclaw/pull/3184) | Missing transcript file causes session death with `No conversation found with session ID` — fixes rotate-on-missing-transcript behavior. |
| 2 | **High** | [PR #3183](https://github.com/nanocoai/nanoclaw/pull/3183) | Retention cleanup can reap cold-but-active sessions, producing the same `No conversation found` error for users messaging quiet channels after 30+ days. |
| 3 | **Medium** | [Issue #3179](https://github.com/nanocoai/nanoclaw/issues/3179) | `@clack/core` uses `node:util/styleText` which is unavailable on older Node.js versions; runtime crash on startup. |
| 4 | **Medium** | [PR #3143](https://github.com/nanocoai/nanoclaw/pull/3143) | Approval card content (title, body) was lost on resolution; now persisted. |
| 5 | **Low** | [PR #3181](https://github.com/nanocoai/nanoclaw/pull/3181) | iMessage opt-in flow was broken; fixed by requiring first message to the assigned line. |

The dominant stability theme is **session lifecycle management** — two high-severity fixes address the same `No conversation found` failure mode from different angles (missing transcript vs. premature cleanup).

## 6. Feature Requests & Roadmap Signals

- **Remote MCP server support** ([PR #3092](https://github.com/nanocoai/nanoclaw/pull/3092)) is the most notable open feature. If merged, it would enable agents to connect to MCP servers over HTTP rather than requiring local sockets — a significant architecture expansion.
- **Self-serve engagement policy controls** ([PR #3137](https://github.com/nanocoai/nanoclaw/pull/3137)) was recently merged, suggesting the team is moving toward decentralized agent governance rather than central policy enforcement.
- **Hardened image automation** ([PR #3180](https://github.com/nanocoai/nanoclaw/pull/3180)) indicates a roadmap toward secure-by-default deployments with minimal operator friction.

## 7. User Feedback Summary

- **Pain point: Session resurrection failures.** Users messaging dormant group channels receive raw `No conversation found with session ID` errors instead of graceful replies. This is a top frustration and the focus of two concurrent fixes (#3184, #3183).
- **Pain point: Node.js version compatibility.** The `styleText` crash (#3179) affects users on Node.js < 20.11, likely impacting containerized and enterprise environments with pinned runtimes.
- **Positive signal: Approval card fidelity.** Users now see resolved decisions reflected in card metadata rather than losing context — a quality-of-life improvement for auditability.
- **Positive signal: iMessage onboarding.** The opt-in flow fix (#3181) reduces friction for users migrating from traditional messaging channels.

## 8. Backlog Watch

- **[PR #3092](https://github.com/nanocoai/nanoclaw/pull/3092)** — Open since 2026-07-19 (16 days). Remote MCP support is a high-value feature that has not yet been merged. Needs maintainer review to unblock.
- **[Issue #3179](https://github.com/nanocoai/nanoclaw/issues/3179)** — Open since 2026-08-03 with 1 comment and 0 reactions. The Node.js compat issue may need a maintainer decision on minimum version enforcement vs. a polyfill/rollback of `@clack/core`.
- **[PR #3184](https://github.com/nanocoai/nanoclaw/pull/3184)** and **[PR #3183](https://github.com/nanocoai/nanoclaw/pull/3183)** — Both open and addressing the same class of session-resume bug. Maintainer coordination may be needed to avoid conflicting behavior if both land.

---

**Project Health Assessment:** Active and focused. The team is aggressively closing session-management bugs and hardening the deployment baseline. The main risk is the unresolved Node.js compatibility gap (#3179) and the stagnant remote-MCP PR (#3092). Overall trajectory is positive.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-04

## 1. Today's Overview

NullClaw saw moderate developer activity today with **5 PR updates** and **1 issue update** in the last 24 hours. Two PRs were closed/merged, indicating active development momentum around streaming tool-call infrastructure and proxy transport hardening. No new releases were published. The project is in a steady state — contributors are addressing streaming capability gaps and security-conscious transport improvements, though no release cadence shift is evident.

---

## 2. Releases

No new releases today. The last 24 hours did not produce a version bump or changelog event.

---

## 3. Project Progress

**Merged/Closed PRs:**

- **[#964](https://github.com/nullclaw/nullclaw/pull/964)** — *Enable native API-level tool calls during streaming* (mtdphn). Fixed a gap where `StreamChatResult` dropped structured tool-call deltas, preventing the agent from executing pure streamed tool responses. Provider-wide capability checks were also addressed. This is a **core capability advancement** for real-time tool use.

- **[#965](https://github.com/nullclaw/nullclaw/pull/965)** — *Structured streaming tool-call support for SSE parser* (mtdphn). Companion PR extending the SSE parser to handle model-emitted XML in `delta.content` during streaming, ensuring providers that don't use native tool-call deltas still function correctly.

Both PRs were merged and represent a **comprehensive fix for streaming tool-call pipelines** — a feature that was previously incomplete or broken for certain provider configurations.

**Open PRs advancing:**

- **[#983](https://github.com/nullclaw/nullclaw/pull/983)** — Routes non-streaming provider POSTs through a pinned, secure curl transport path when a safe pinned resolve entry is available, keeping credential headers out of `argv`.
- **[#982](https://github.com/nullclaw/nullclaw/pull/982)** — Directs Telegram Bot API POST requests through curl transport when an explicit proxy is configured, retaining native HTTP for direct connections.
- **[#956](https://github.com/nullclaw/nullclaw/pull/956)** — Dependabot Alpine 3.23 → 3.24 Docker image bump.

---

## 4. Community Hot Topics

- **[#915](https://github.com/nullclaw/nullclaw/issues/915)** — *Problem with scheduler unauthorized* (scabros, 4 comments, 1 👍). Open since 2026-05-15; the scheduler fails in Telegram and other channels while the LLM and general tool-calling work fine. This is the **most commented open issue** and reflects a real deployment pain point for users running NullClaw with external Ollama hosts on local networks. The long open duration (≈2.5 months) without resolution is a concern.

- **Streaming tool-call support** (#964, #965) — The merged PRs signal strong community demand for reliable streamed tool execution, likely driven by users running real-time agent loops with providers like OpenAI, Anthropic, and local Ollama setups.

---

## 5. Bugs & Stability

| Severity | Item | Status |
|----------|------|--------|
| **Medium** | [#915](https://github.com/nullclaw/nullclaw/issues/915) — Scheduler unauthorized error in Telegram/local channels | Open, no fix PR yet |

No crashes or regressions reported today. The scheduler bug (#915) is the only outstanding issue; it appears to be an auth/proxy routing problem specific to the scheduler component rather than a systemic stability concern.

---

## 6. Feature Requests & Roadmap Signals

- **Structured streaming tool calls** (#964, #965) — Now merged. This feature was highly requested by users running streaming pipelines with tool use.
- **Proxy-aware transport for all channels** (#982, #983) — The open PRs suggest continued investment in proxy/enterprise network support across all communication channels (Telegram, provider APIs).
- **Docker image modernization** (#956) — Alpine 3.24 bump indicates ongoing dependency maintenance but no major feature signal.

No new feature requests were filed today.

---

## 7. User Feedback Summary

The dominant user voice today comes from [#915](https://github.com/nullclaw/nullclaw/issues/915): a user running NullClaw on Ubuntu with an external Ollama host (qwen3.6:27b on RTX 3090) reports that **tool calling and LLM inference work, but the scheduler fails** — not just in Telegram but likely across other channels. This points to a **deployment pattern gap**: users running split LLM/NullClaw setups on local networks encounter scheduler auth issues that the core project may not have fully tested against. Satisfaction with the LLM and tool-calling paths is high; the scheduler is the friction point.

---

## 8. Backlog Watch

- **[#915](https://github.com/nullclaw/nullclaw/issues/915)** — Scheduler unauthorized bug, open since 2026-05-15 (~2.5 months), 4 comments, 1 reaction. **No fix PR assigned.** This is the most important backlog item requiring maintainer attention. Users deploying NullClaw with external/local LLM backends are likely affected.
- **[#983](https://github.com/nullclaw/nullclaw/pull/983)** and **[#982](https://github.com/nullclaw/nullclaw/pull/982)** — Open since 2026-08-03; waiting on maintainer review. These are small, focused fixes with low risk and could be merged quickly.
- **[#956](https://github.com/nullclaw/nullclaw/pull/956)** — Dependabot Alpine bump, open since 2026-06-15. Low priority but should be merged to keep Docker images current.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-04

## 1. Today's Overview

IronClaw is experiencing **high development velocity**, with 47 issues and 50 PRs updated in the last 24 hours. Activity is heavily concentrated around Wave 3 refactors (WS3) and WS6 checklist items, driven primarily by core contributor BenKurrek. No new releases were published today, but 17 PRs were merged/closed, indicating steady integration flow. The project is in a mature restructuring phase, with ongoing work to tighten crate-layer boundaries, fix CI planner gaps, and address a batch of user-facing bugs surfaced during a bug-bash sprint.

## 2. Releases

**No new releases today.** The most recent release was shipped via PR #5598 (created 2026-07-03), which updated `ironclaw_common` (0.4.2 → 0.5.0, ⚠ breaking), `ironclaw_safety` (0.2.2 → 0.2.3), and `ironclaw_skills` (0.3.0 → 0.4.0, ⚠ breaking).

## 3. Project Progress

**Key merged/closed items today:**

- **#7088** [CLOSED] `fix(extensions): expose custom MCP registration to model` — Made hosted-MCP registration model-visible via `builtin.extension_register_hosted_mcp`. ([link](https://github.com/nearai/ironclaw/pull/7088))
- **#7064** [CLOSED] `refactor(loop): shed the model gateway and tool disclosure into loop_host` — Wave 3 WS3 runner shed + WS4 re-layer, move-only with zero test loss. ([link](https://github.com/nearai/ironclaw/pull/7064))
- **#7024** [CLOSED] `fix(extensions): resolve custom MCP auth during registration` — Hosted-MCP auth now resolved before admitting a package definition; `Auto` mode performs credential-free handshake. ([link](https://github.com/nearai/ironclaw/pull/7024))
- **#7049** [CLOSED] `docs: add weekly Wednesday release strategy` — Internal strategy document aligning Monday RC cuts, Tuesday QA, Wednesday promotion. ([link](https://github.com/nearai/ironclaw/pull/7049))
- **#7023** [CLOSED] Dependabot dependency bump (base64, toml, rstest, etc.). ([link](https://github.com/nearai/ironclaw/pull/7023))
- **#7084** [OPEN, unblocked] `refactor(wasm): move wit/ inside its owning crate (Wave 3)` — Planner gap from #7087 was fixed within this PR (`1f66b58`), unblocking the Wave 3 `wit/` move. ([link](https://github.com/nearai/ironclaw/pull/7084))

**Active high-impact PRs:**
- **#7094** — Closes remaining Wave 2 sequence items (extension registry re-layer, `include_str!` kills, nested-tree coverage). ([link](https://github.com/nearai/ironclaw/pull/7094))
- **#7096** — Wave 3 secrets direct-consumer tightening; routes operator secrets through a `product_contracts` port. ([link](https://github.com/nearai/ironclaw/pull/7096))
- **#7065** — Wave 3 sandbox lane merge + `ironclaw_mcp` contracts flip, described as "one problem, not two." ([link](https://github.com/nearai/ironclaw/pull/7065))
- **#7101** — WS6: stops leaking `deadpool_postgres::Pool` in the public API of `ironclaw_reborn_event_store`. ([link](https://github.com/nearai/ironclaw/pull/7101))
- **#7099** — WS6: moves system-prompt content out of the composition root into `ironclaw_loop_host`. ([link](https://github.com/nearai/ironclaw/pull/7099))
- **#6994** — UI-only prototype for OOBE onboarding (carousel, inline cards, agent-mode pill). ([link](https://github.com/nearai/ironclaw/pull/6994))

## 4. Community Hot Topics

1. **#6284** [CLOSED] *error-recoverability endgame* — "the model recovers from 100% of the errors it sees" (15 comments). The top-commented issue of the period, reflecting deep community investment in making IronClaw resilient to mid-run failures. ([link](https://github.com/nearai/ironclaw/issues/6284))

2. **#6524** [CLOSED] *Hermetic capability and journey testing platform* (4 comments). Signals a need for deterministic, mechanizable coverage guarantees across all supported capabilities. ([link](https://github.com/nearai/ironclaw/issues/6524))

3. **#7087** [OPEN] *Reborn PR test planner hard-fails on Dockerfile, .githooks/, .claude/, crates/AGENTS.md, test-tools/* (3 comments). A CI planner gap that blocks Wave 3 work; filed during the `wit/` move. ([link](https://github.com/nearai/ironclaw/issues/7087))

4. **#7100** [CLOSED] *CI: Reborn test planner fails closed on `crates/AGENTS.md`* — The crate-family map was unreachable by any PR. Fixed the same day it was filed. ([link](https://github.com/nearai/ironclaw/issues/7100))

**Analysis:** The most-discussed topics center on **test reliability and error recoverability** — the community is pushing for IronClaw to be both structurally sound (hermetic testing, layer compliance) and operationally resilient (error recovery contracts). The Reborn CI planner issues (#7087, #7100) show active friction between rapid refactoring cadence and CI gate stability.

## 5. Bugs & Stability

| Priority | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| **P1** | [#7069](https://github.com/nearai/ironclaw/issues/7069) | Google services require repeated authentication; each service asks for its own OAuth flow | **#7077** (open, in review) |
| **P1** | [#7074](https://github.com/nearai/ironclaw/issues/7074) | Multi-tool meeting research fails after retrieving calendar data; model calls unavailable function | — |
| **P2** | [#7071](https://github.com/nearai/ironclaw/issues/7071) | "Reconnecting" status flashes during every streaming update | — |
| **P2** | [#7075](https://github.com/nearai/ironclaw/issues/7075) | Agent ignores follow-up question after failed run, resumes old task | — |
| **P2** | [#7073](https://github.com/nearai/ironclaw/issues/7073) | Agent exposes internal implementation details in user-facing responses | — |
| **P2** | [#7072](https://github.com/nearai/ironclaw/issues/7072) | Telegram messages render raw Markdown instead of formatted text | — |
| — | [#7082](https://github.com/nearai/ironclaw/issues/7082) | `builtin.skill_install`: inline multi-file installs unreachable; URL installs silently drop files/source fields | — |
| — | [#7085](https://github.com/nearai/ironclaw/issues/7085) | `check-version-bumps.sh` silently skips WIT_TOOL_VERSION cross-check on macOS (BSD sed incompatibility) | — |
| — | [#7081](https://github.com/nearai/ironclaw/issues/7081) | Docker fail-closed test gate wired to nothing (`IRONCLAW_REQUIRE_DOCKER_TESTS` never set) | — |
| — | [#7068](https://github.com/nearai/ironclaw/issues/7068) | Hosted MCP: omitted `destructiveHint` read as `false` instead of spec-default `true` | — |

**Assessment:** The bug-bash surfaced 6 P1/P2 user-facing issues today, primarily around **authentication friction, streaming UX, and error recovery behavior**. The P1 Google auth issue (#7069) has an active fix PR (#7077). Several pre-existing structural bugs (#7082, #7085, #7081) were discovered during the Wave 3 refactors but are not blockers for merging.

## 6. Feature Requests & Roadmap Signals

- **#7097** — *Billing support escalation pathways*: Users uncertain who handles NEAR AI billing issues; requests clear resolution pathways on the billing page. ([link](https://github.com/nearai/ironclaw/issues/7097))
- **#6941** [OPEN] *Epic: skills the model can self-create, find, choose, and use* — Subset of #6565, focused on measurable skill lifecycle. ([link](https://github.com/nearai/ironclaw/issues/6941))
- **#7044** [OPEN] *Onboarding to channel-first approach* — First-time users face a blank slate; the epic focuses on reducing adoption friction for the General Assistant use case. ([link](https://github.com/nearai/ironclaw/issues/7044))
- **#6957** [OPEN] *Manage installed package lifecycle* — Persist redacted IronHub installation receipts; add `ironhub.status` and `ironhub.update` lifecycle operations. ([link](https://github.com/nearai/ironclaw/pull/6957))
- **#6994** [OPEN] *OOBE automation-tasks prototype* — Carousel, inline cards, and agent-mode pill for WebChat v2 onboarding. ([link](https://github.com/nearai/ironclaw/pull/6994))

**Prediction:** The onboarding flow (#7044, #6994) and skill lifecycle management (#6957) are the strongest candidates for inclusion in the next user-facing release, as they directly address adoption and core workflow gaps.

## 7. User Feedback Summary

**Pain points from bug-bash (Railway instance):**
- **Authentication fatigue**: Users must re-authenticate for each Google service even after completing OAuth multiple times (#7069) — partially resolved by #7077.
- **Streaming UX degradation**: The "Reconnecting" status indicator flashes on every chunk, creating a perception of instability (#7071).
- **Post-failure behavior**: After a run fails, the agent resumes the old failed task instead of responding to new user input (#7075).
- **Information leakage**: Tool names and routing logic appear in user-facing responses (#7073).
- **Formatting loss**: Telegram messages display raw Markdown instead of rendered text (#7072).

**Satisfaction signals:** The structured Wave-based refactoring (WS2–WS8) and the Wednesday release cadence (#7049) indicate the team is responsive to maintainability concerns. The MCP registration fix (#7088, #7024) shows proactive hardening of the extension system.

## 8. Backlog Watch

| Issue | Days Open | Why It Matters |
|-------|-----------|----------------|
| [#6284](https://github.com/nearai/ironclaw/issues/6284) — error-recoverability endgame | 16 | Core reliability contract; 15 comments, epic-scale. |
| [#6524](https://github.com/nearai/ironclaw/issues/6524) — hermetic testing platform | 13 | Deterministic coverage is a prerequisite for confident releases. |
| [#6941](https://github.com/nearai/ironclaw/issues/6941) — self-creating skills epic | 4 | Key differentiator for agent autonomy; split from larger #6565. |
| [#7087](https://github.com/nearai/ironclaw/issues/7087) — Reborn PR test planner hard-fail | 1 | Blocks Wave 3; partially addressed in #7084 but the underlying planner policy remains frozen. |
| [#7083](https://github.com/nearai/ironclaw/issues/7083) — coverage dark for `crates/extensions/` family | 1 | Five crates invisible to Reborn coverage tooling since #7037. |
| [#7078](https://github.com/nearai/ironclaw/issues/7078) — shared-vendor OAuth scope ceiling is store-wide | 1 | Security-relevant; scope is broader than intended per #7077 review. |
| [#7067](https://github.com/nearai/ironclaw/issues/7067) — replace ResourceGovernor with reserve/reconcile/release port | 1 | Last two `runtimes → kernel` layer-matrix exceptions; blocks WS3 completion. |

**Overall project health: Strong.** High PR throughput, clear owner-driven refactors, active bug-bash response, and a documented release strategy. The main risk is CI planner fragility (#7087) under rapid restructuring, and a cluster of P1/P2 UX bugs that need triage before the next release.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-08-04

## 1. Today's Overview

LobsterAI (netease-youdao/LobsterAI) shows **moderate activity** today with 2 open issues and 12 PRs updated in the last 24 hours (5 open, 7 closed/merged). No new releases were published. The project is actively maintaining its Electron-based desktop AI agent, with focus on campaign fixes, Windows process cleanup, and multi-agent UI improvements. Community engagement remains steady on feature requests around session export and model customization.

## 2. Releases

*No new releases published today.*

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Description | Author |
|----|-------------|--------|
| [#2424](https://github.com/netease-youdao/LobsterAI/pull/2424) | **Revert credits campaign fix** — Reverted `aced16fc` to restore the active credits campaign, including subscription credit-reset entry and 500-credit claim flow for non-subscribers | btc69m979y-dotcom |
| [#2423](https://github.com/netease-youdao/LobsterAI/pull/2423) | **Revert "Liuzhq/fix btw tools"** — Reverted a previous tooling fix PR | liuzhq1986 |
| [#2422](https://github.com/netease-youdao/LobsterAI/pull/2422) | **Liuzhq/fix btw tools** — Closed (likely superseded by #2423 revert) | liuzhq1986 |
| [#2421](https://github.com/netease-youdao/LobsterAI/pull/2421) | **Liuzhq/fix btw tools** — Closed (duplicate/superseded) | liuzhq1986 |
| [#2420](https://github.com/netease-youdao/LobsterAI/pull/2420) | **fix(nsis): re-kill survivor processes on every stop poll round** — Stop-Process was only issued once; now re-issues per round with per-process survivor logging (name/pid/path) | fisherdaddy |
| [#2419](https://github.com/netease-youdao/LobsterAI/pull/2419) | **feat(activity): add startup credit campaign** — Configurable startup credit campaign popup for NetEase user acquisition | btc69m979y-dotcom |
| [#2418](https://github.com/netease-youdao/LobsterAI/pull/2418) | **feat(sidebar): add multi-agent task activity filter** — Codex-inspired filter button for finding tasks needing attention across multiple agents; hidden when sidebar collapsed | liuzhq1986 |

**Key Advances:**
- ✅ Windows NSIS installer now more aggressively cleans up lingering processes
- ✅ Sidebar gains a multi-agent task activity filter for better visibility
- ✅ Startup credit campaign feature added (though later reverted in #2424)

---

## 4. Community Hot Topics

### Most Discussed Open Items

| # | Type | Title | Comments | Updated |
|---|------|-------|----------|---------|
| [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Issue | Bug: Kimi 2.5 model re-repeats actions when analyzing documents | 1 | 2026-08-03 |
| [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | Issue | Feature request: Export session details as Markdown | 1 | 2026-08-03 |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | PR | feat(cowork): Manual retry button for transient errors (429, network) | — | 2026-08-03 |
| [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | PR | fix(web-search): Remove unsupported `--disable-blink-features=AutomationControlled` flag | — | 2026-08-03 |
| [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | PR | fix(model): Allow up to 20 custom providers (was capped at 10) | — | 2026-08-03 |
| [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | PR | feat: Export session as Markdown (implements #1213/#1345) | — | 2026-08-03 |

**Analysis:** Users are requesting **workflow efficiency** features — Markdown export for conversation archiving and a retry button for rate-limit errors. The custom provider limit increase (#1212) reflects power users managing many model configurations.

---

## 5. Bugs & Stability

### Reported Bugs

| Severity | # | Title | Status | Fix PR |
|----------|---|-------|--------|--------|
| 🔴 **High** | [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Kimi 2.5 model repeats actions when analyzing documents (private deployment, Win10, v2026.3.30) — switching models resolves it | Open / Stale | None yet |
| 🟡 **Medium** | [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | Web-search block due to unsupported `--disable-blink-features=AutomationControlled` Chrome flag (injected externally via残留 user data or env) | Open PR | #1209 |

### Stability Improvements Merged
- [#2420](https://github.com/netease-youdao/LobsterAI/pull/2420) — Fixed process cleanup on Windows (survivor processes now properly killed)

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| **Export session as Markdown** | [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) + [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | ✅ **High** — PR already implemented, awaiting merge |
| **Retry button for transient errors** | [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | ✅ **High** — PR ready, addresses 429/network errors |
| **More than 10 custom model providers** | [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | ✅ **High** — PR ready, simple cap increase |
| **Multi-agent task activity filter** | [#2418](https://github.com/netease-youdao/LobsterAI/pull/2418) | ✅ **Merged** — Already in progress |
| **Startup credit campaign** | [#2419](https://github.com/netease-youdao/LobsterAI/pull/2419) | ⚠️ **Uncertain** — Added then reverted in #2424 |

---

## 7. User Feedback Summary

| Theme | Sentiment | Details |
|-------|-----------|---------|
| Kimi 2.5 model behavior | ❌ **Dissatisfied** | Repetitive action prompts confuse users; switching models fixes it — suggests model-specific integration bug |
| Session export | 😐 **Frustrated** | Currently only supports image export; Markdown would enable better archiving and sharing |
| Error handling | 😐 **Inconvenienced** | 429/rate-limit errors require full re-sending of messages; inline retry button would improve UX |
| Custom providers | 😐 **Blocked** | 10-provider cap forces deletion of old configs when adding new ones |
| Process management | ✅ **Appreciated** | Fix for surviving processes after stop command improves stability |

---

## 8. Backlog Watch

| # | Type | Title | Open Since | Needs Attention |
|---|------|-------|------------|-----------------|
| [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Bug | Kimi 2.5 document analysis repetition | 2026-04-01 (4 months) | 🔴 **Yes** — No fix PR, stale but impactful |
| [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | Feature | Markdown export for sessions | 2026-04-01 (4 months) | 🟡 **Monitor** — PR #1214 implements it, awaiting merge |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | PR | Retry button for transient errors | 2026-04-01 | 🟡 **Monitor** — Ready, needs review |
| [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | PR | Web-search Chrome flag fix | 2026-04-01 | 🟡 **Monitor** — Ready, needs review |
| [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | PR | Allow 20 custom providers | 2026-04-01 | 🟡 **Monitor** — Ready, needs review |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | PR | Bump Electron 40→43 | 2026-04-02 | 🟢 Low — Routine dep update |

---

*Digest generated 2026-08-04 | Source: [netease-youdao/LobsterAI](https://github.com/netease-youdao/LobsterAI)*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-04

---

## 1. Today's Overview

Activity on Moltis remains low as of August 4, 2026, with zero new issues and no releases published in the last 24 hours. The sole notable update is one open pull request (#1183) introducing managed repository bundles for MCP servers, which suggests ongoing development toward a more structured, lifecycle-managed MCP configuration experience. The project appears to be in a quieter maintenance phase between feature pushes, with no merged PRs or closed issues today.

---

## 2. Releases

No new releases were published in the last 24 hours. The project has no new version to report.

---

## 3. Project Progress

**Merged/Closed PRs today:** None.

The one active PR, **#1183**, is still open and has not yet been merged. It advances the MCP server management surface by introducing managed Git repository bundles — a feature that enables discovering, previewing, installing, updating, rolling back, and removing MCP servers from structured repository sources. No bugs or fixes were merged today.

🔗 PR #1183: https://github.com/moltis-org/moltis/pull/1183

---

## 4. Community Hot Topics

| Item | Type | Comments | Reactions | Status |
|------|------|----------|-----------|--------|
| [#1183](https://github.com/moltis-org/moltis/pull/1183) — *feat(mcp): add managed repository bundles* | PR | — | 0 👍 | Open |

**Analysis:** The featured PR targets a clear user need: the desire to manage MCP server configurations through version-controlled, portable bundles rather than ad-hoc per-server installs. The emphasis on HTTPS credentials, pinned SSH transport, vault lifecycle integration, and web onboarding simplification signals that the community values **reproducibility, security, and ease of shared setup** — particularly for team or organizational deployments. No issues with high comment counts were reported today.

---

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported today. The open issue count is zero, and no stability concerns are indicated in the current data window.

---

## 6. Feature Requests & Roadmap Signals

**Signal: Managed MCP Repository Bundles (PR #1183)**

The most prominent roadmap signal is the managed repository bundles feature, which addresses several likely upcoming capabilities:

- **Repository-backed MCP configurations** — importing servers from Git-hosted bundles
- **Vault lifecycle integration** — secure credential and secret management tied to MCP server lifecycles
- **Web onboarding simplification** — reducing friction for new users setting up MCP servers through a GUI

These trends suggest the next release cycle will likely focus on **portable, shareable MCP configurations** and tighter integration with secret management tooling.

🔗 PR #1183: https://github.com/moltis-org/moltis/pull/1183

---

## 7. User Feedback Summary

No direct user feedback (issues, comments, reactions) was logged today. The project appears to have a quiet feedback channel at present. However, the direction of PR #1183 implies that users have been requesting better **organizational and collaborative MCP server management** — specifically around shared configurations, credential handling, and rollback capability. The absence of negative feedback or open bug reports is a positive signal for current user satisfaction.

---

## 8. Backlog Watch

No long-unanswered issues or PRs were identified in the current data window. With zero open issues and only one open PR, there is no backlog pressure to flag today. Maintainers should continue monitoring PR #1183 for timely review and merge, as it represents the primary active development effort.

---

*Digest generated from GitHub activity data for 2026-08-03 00:00 UTC to 2026-08-04 00:00 UTC.*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-04

## 1. Today's Overview

CoPaw (QwenPaw) continues to show strong development velocity with 50 PRs and 14 issues updated in the last 24 hours, indicating a healthy and active contributor base. The v2.1.0-beta.1 release was shipped, targeting stability fixes and UX improvements ahead of the stable 2.1.0 launch. Community engagement remains robust, with the most discussion centered on model fallback reliability, channel timeout handling, and desktop UI resilience. Overall project health is positive, though several medium-severity bugs in messaging channels and subagent orchestration warrant close monitoring before the next release candidate.

## 2. Releases

**v2.1.0-beta.1** (released 2026-08-03)

Key changes:
- **fix(chat):** Prevents stale channel identity from leaking into new chats after channel switches — [PR #6382](https://github.com/agentscope-ai/QwenPaw/pull/6382)
- **feat(inbox):** Adds wobble animation and color-coded badge dot on new approvals in the sidebar inbox — [PR](https://github.com/agentscope-ai/QwenPaw/pull/)

No breaking changes noted. Migration: none required. Release duty issue [#6656](https://github.com/agentscope-ai/QwenPaw/issues/6656) is tracking platform verification across all four checkpoints.

## 3. Project Progress

**Merged/Closed PRs today:**

| PR | Title | Author |
|----|-------|--------|
| [#6634](https://github.com/agentscope-ai/QwenPaw/pull/6634) | fix(skills): exclude full content from skill list endpoints to fix slow network timeouts | BlackBox-Labs |
| [#6666](https://github.com/agentscope-ai/QwenPaw/pull/6666) | fix(creator): put PawApp category under meta.pawapp for App Center | XiuShenAl |
| [#6665](https://github.com/agentscope-ai/QwenPaw/pull/6665) | chore: bump version to 2.1.0b2 | cuiyuebing |
| [#6661](https://github.com/agentscope-ai/QwenPaw/pull/6661) | ci(plugins): add platform publish workflow to enable manual dispatch | zhijianma |
| [#6650](https://github.com/agentscope-ai/QwenPaw/pull/6650) | fix(skill): loading redundancy — reduces API payloads | Leirunlin |
| [#6597](https://github.com/agentscope-ai/QwenPaw/pull/6597) | fix(checkpoints): restore auto snapshots in web workspace bootstrap | qbc2016 |
| [#6203](https://github.com/agentscope-ai/QwenPaw/pull/6203) | fix(utils): bound and hide the Windows tasklist liveness probe | Yigtwxx |

**Key feature PRs in progress:**
- [#6659](https://github.com/agentscope-ai/QwenPaw/pull/6659) — Model fallback with cooldown mechanism (addresses #2199, #1327, #2089)
- [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) — Unified provider discovery, model metadata, routing, and agent controls
- [#6525](https://github.com/agentscope-ai/QwenPaw/pull/6525) — User context transparent passthrough (Chat API → Agent → Tool → MCP → SKILL CLI)
- [#6645](https://github.com/agentscope-ai/QwenPaw/pull/6645) — OS enhancements: full-screen desktop, Dock, Spaces, Notification Center
- [#5930](https://github.com/agentscope-ai/QwenPaw/pull/5930) — Structured run outcome in SSE responses for API automation

## 4. Community Hot Topics

| Issue/PR | Topic | Comments | Link |
|----------|-------|----------|------|
| [#6649](https://github.com/agentscope-ai/QwenPaw/issues/6649) | GPT-5.6 prompt caching support in Responses API | 9 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6649) |
| [#6588](https://github.com/agentscope-ai/QwenPaw/issues/6588) | `spawn_subagent` treats empty `batch` as batch mode | 6 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6588) |
| [#6160](https://github.com/agentscope-ai/QwenPaw/issues/6160) | Standalone Python runtime for desktop | 4 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6160) |
| [#6655](https://github.com/agentscope-ai/QwenPaw/issues/6655) | Console channel ignores security approval prompts | 3 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6655) |
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | Long-running shell commands block Feishu sessions indefinitely | 3 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6608) |

**Analysis:** The top-voted discussion (#6649) reflects growing demand for cost-aware agent loops using GPT-5.6's prompt caching — a signal that enterprise users are scaling token budgets. The `spawn_subagent` batch placeholder bug (#6588) and the Feishu timeout issue (#6608) both point to a recurring theme: the project needs tighter contracts around optional parameters and per-channel lifecycle management. Multiple PRs are already addressing #6588 ([#6595](https://github.com/agentscope-ai/QwenPaw/pull/6595), [#6658](https://github.com/agentscope-ai/QwenPaw/pull/6658)).

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR | Link |
|----------|-------|---------|--------|------|
| 🔴 High | [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | Long-running shell commands block Feishu sessions for hours; no per-channel total timeout; orphan subprocess on cancel | None yet | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6608) |
| 🔴 High | [#6647](https://github.com/agentscope-ai/QwenPaw/issues/6647) | Desktop UI goes fully black on WebView2 crash; no recovery path (STATUS_IN_PAGE_ERROR 0xc0000006) | None yet | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6647) |
| 🟡 Medium | [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614) | WeChat cron pushes report `success` but never deliver (ret=-2, context_token expired); silent failure burning ~44M tokens | None yet | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6614) |
| 🟡 Medium | [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625) | ACP `delegate_external_agent` returns "completed without text output" when notifications race the prompt response | [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) (open) | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6625) |
| 🟡 Medium | [#6633](https://github.com/agentscope-ai/QwenPaw/issues/6633) | Skills/Skill Pool pages fail on slow networks (30s fetch timeout exceeded by MB payloads) | [#6634](https://github.com/agentscope-ai/QwenPaw/pull/6634) ✅ merged | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6633) |
| 🟡 Medium | [#6655](https://github.com/agentscope-ai/QwenPaw/issues/6655) | Console channel does not render security approval prompts, causing silent 300s timeouts | [#6663](https://github.com/agentscope-ai/QwenPaw/pull/6663) (open) | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6655) |
| 🟠 Low | [#6588](https://github.com/agentscope-ai/QwenPaw/issues/6588) | `spawn_subagent` misclassifies empty `batch` placeholders as batch mode | [#6595](https://github.com/agentscope-ai/QwenPaw/pull/6595) and [#6658](https://github.com/agentscope-ai/QwenPaw/pull/6658) (both open) | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/6588) |

**Note:** The two high-severity bugs (WebView2 crash recovery and Feishu session blocking) have no active fix PRs and should be prioritized before v2.1.0-stable.

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Signal |
|---------|-------|--------|
| GPT-5.6 prompt caching parameters (`prompt_cache_key`, `prompt_cache_options`, `prompt_cache_breakpoint`) | [#6649](https://github.com/agentscope-ai/QwenPaw/issues/6649) | Strong enterprise adoption signal; likely candidate for v2.1.0 |
| Per-task media directory isolation (instead of flat `media/` folder) | [#6643](https://github.com/agentscope-ai/QwenPaw/issues/6643) | UX organization improvement; moderate priority |
| Direct file path reading on drag-and-drop (skip upload/download cycle) | [#6642](https://github.com/agentscope-ai/QwenPaw/issues/6642) | Performance + UX win; aligns with desktop agent market |
| Multi-line file name display for bulk drag-in | [#6583](https://github.com/agentscope-ai/QwenPaw/issues/6583) | UI polish; likely in beta |
| Multi-file attachment preview wrapping in chat | [#6662](https://github.com/agentscope-ai/QwenPaw/pull/6662) | Already in PR; expected in v2.1.0 |
| Model fallback with cooldown | [#6659](https://github.com/agentscope-ai/QwenPaw/pull/6659) / [#2199](https://github.com/agentscope-ai/QwenPaw/pull/2199) | Major reliability feature; actively in review |

**Prediction:** GPT-5.6 prompt caching, model fallback, and multi-file UI improvements are the strongest candidates for inclusion in v2.1.0-stable. The direct-path file reading feature (#6642) may ship in a follow-up beta given its scope.

## 7. User Feedback Summary

- **Pain point — silent failures:** Users are frustrated by issues that report success but produce no output (WeChat cron [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614), ACP race condition [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625)). This erodes trust in automation reliability.
- **Pain point — slow network timeouts:** Skills pages failing on slower connections [#6633](https://github.com/agentscope-ai/QwenPaw/issues/6633) affects a segment of enterprise users; the merged fix [#6634](https://github.com/agentscope-ai/QwenPaw/pull/6634) should resolve this.
- **Pain point — desktop crashes:** WebView2 crash leaving the UI black with no recovery [#6647](https://github.com/agentscope-ai/QwenPaw/issues/6647) is a poor first impression for new desktop users.
- **Positive signal — proactive feature requests:** Users are requesting cost-optimization features (prompt caching) and developer experience improvements (independent Python env [#6160](https://github.com/agentscope-ai/QwenPaw/issues/6160), per-task media dirs [#6643](https://github.com/agentscope-ai/QwenPaw/issues/6643)), indicating a maturing user base operating at scale.

## 8. Backlog Watch

| Issue/PR | Age | Concern |
|----------|-----|---------|
| [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614) — WeChat cron silent failure | 4 days | No fix PR; ~44M tokens wasted; affects production cron workflows |
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) — Feishu session blocking | 4 days | No fix PR; orphan subprocess risk; long-running shells are a common pattern |
| [#6647](https://github.com/agentscope-ai/QwenPaw/issues/6647) — WebView2 black screen | 1 day | No fix PR; critical UX regression on desktop |
| [#6588](https://github.com/agentscope-ai/QwenPaw/issues/6588) — spawn_subagent batch placeholder | 5 days | Two fix PRs open but not merged; blocks single-task calls on certain providers |
| [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625) — ACP text output loss on race | 3 days | Fix PR [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) open, needs review |
| [#2199](https://github.com/agentscope-ai/QwenPaw/pull/2199) — Model fallback (original) | 133 days | Superseded by [#6659](https://github.com/agentscope-ai/QwenPaw/pull/6659) but original PR remains open; should be closed to reduce noise |

**Recommendation:** The three high-severity unpatched issues (#6614, #6608, #6647) should be escalated to the next release sprint. The stale model-fallback PR #2199 should be explicitly closed as superseded to keep the backlog clean.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-04

## 1. Today's Overview
ZeroClaw activity remains high with 50 issues and 50 pull requests updated in the last 24 hours. The project is in a design-intensive phase, with several high-priority RFCs advancing goal mode, observability, and security contracts. No new releases were published today, but multiple bug fixes and feature enhancements are in active review. Community engagement is strong, particularly around channel reliability, audit‑trail accuracy, and zerocode UX improvements.

## 2. Releases
*No new releases today.* The latest version remains at 0.8.3 (`fc8b4d83e3a5eacd9…`).

## 3. Project Progress
- **Merged/Closed PRs (last 24h):** 1 (details not in top‑20 list).  
- **Closed Issues:**  
  - [#6641](https://github.com/zeroclaw-labs/zeroclaw/issues/6641) – Turn‑level OTel trace correlation (feature completed).  
  - [#7113](https://github.com/zeroclaw-labs/zeroclaw/issues/7113) – Slack lifecycle progress updates (feature completed).  
  - [#9162](https://github.com/zeroclaw-labs/zeroclaw/issues/9162) – OAuth‑refresh retry refactor (completed).  
  - [#1](https://github.com/zeroclaw-labs/zeroclaw/issues/1) – XOR‑cipher secrets fix (closed, likely resolved).  
- **Open PRs advancing features:**  
  - [#9739](https://github.com/zeroclaw-labs/zeroclaw/pull/9739) – Multi‑session panes with agent sidebar (zerocode).  
  - [#9738](https://github.com/zeroclaw-labs/zeroclaw/pull/9738) – `keep_siblings` opt‑out for session persistence.  
  - [#9694](https://github.com/zeroclaw-labs/zeroclaw/pull/9694) – SOP pane as read‑only status view.  
  - [#9701](https://github.com/zeroclaw-labs/zeroclaw/pull/9701) – Gateway WebSocket keepalive pings.  
  - [#9726](https://github.com/zeroclaw-labs/zeroclaw/pull/9726) – TaskRecord as single background lifecycle owner.

## 4. Community Hot Topics
| Issue / PR | Comments | Focus |
|------------|----------|-------|
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) – Goal mode v1 RFC | 11 | Bounded foreground matrix work across agent turns. |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) – Maintainer decision queue tracker | 8 | RFC/design‑issue decision tracking. |
| [#6641](https://github.com/zeroclaw-labs/zeroclaw/issues/6641) – OTel trace correlation | 8 | Turn‑level span nesting (now closed). |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) – Unified attachment architecture RFC | 8 | Web‑chat and channel attachment unification. |
| [#7232](https://github.com/zeroclaw-labs/zeroclaw/issues/7232) – Structured observability RFC | 5 | Rich events, OTel bridge, refactoring. |
| [#9727](https://github.com/zeroclaw-labs/zeroclaw/issues/9727) – Epic: multi‑agent sidebar | 0 | zerocode sidebar for running multiple agents. |

**Analysis:** The community is heavily engaged in shaping the long‑term architecture (goal mode, observability, attachment unification) while simultaneously reporting acute channel‑delivery and audit‑trail bugs. The high comment counts on RFCs indicate a mature design‑review process.

## 5. Bugs & Stability
| Issue | Severity | Description | Fix PR? |
|-------|----------|-------------|---------|
| [#9642](https://github.com/zeroclaw-labs/zeroclaw/issues/9642) | **P1** | Timeout approval recorded as explicit denial (falsifies audit trail). | – |
| [#9672](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) | **P1** | All three `cron add` examples broken; empty‑state hint prints fourth broken form. | – |
| [#9697](https://github.com/zeroclaw-labs/zeroclaw/issues/9697) | **P1** | ZeroCode cannot connect to daemon launched by Windows Task Scheduler. | – |
| [#9718](https://github.com/zeroclaw-labs/zeroclaw/issues/9718) | **P2** | Telegram delivers duplicate messages when model emits both `tool_call` and `content`. | – |
| [#9736](https://github.com/zeroclaw-labs/zeroclaw/issues/9736) | **P2** | RPC prompt path never writes persisted `SessionState` (idle/running/error). | – |
| [#9724](https://github.com/zeroclaw-labs/zeroclaw/issues/9724) | **P2** | `always_ask` ignored under `Full` autonomy level. | [#9724](https://github.com/zeroclaw-labs/zeroclaw/pull/9724) |
| [#9472](https://github.com/zeroclaw-labs/zeroclaw/issues/9472) | **P2** | `vi_verify` incorrectly registered as model‑callable tool. | [#9472](https://github.com/zeroclaw-labs/zeroclaw/pull/9472) |
| [#9410](https://github.com/zeroclaw-labs/zeroclaw/issues/9410) | **P1** | Default command‑audit logging enabled (security‑honesty fix). | [#9410](https://github.com/zeroclaw-labs/zeroclaw/pull/9410) |

**Stability Assessment:** Several P1 bugs affect audit integrity, CLI usability, and cross‑platform daemon connectivity. Two have open fix PRs; the others remain unresolved.

## 6. Feature Requests & Roadmap Signals
| RFC / Tracker | Status | Predicted Inclusion |
|---------------|--------|---------------------|
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) – Goal mode v1 (bounded foreground work) | Open, active discussion | Likely next major version |
| [#9702](https://github.com/zeroclaw-labs/zeroclaw/issues/9702) – Goal mode v2 (durable continuation + Web controls) | Open, new today | Likely next major version |
| [#9703](https://github.com/zeroclaw-labs/zeroclaw/issues/9703) – Goal mode v3 (asynchronous child supervision) | Open, new today | Future roadmap |
| [#9682](https://github.com/zeroclaw-labs/zeroclaw/issues/9682) – SOP pane MVP (status visibility) | Accepted, PR [#9694](https://github.com/zeroclaw-labs/zeroclaw/pull/9694) in review | Near‑term (v0.9.0) |
| [#9621](https://github.com/zeroclaw-labs/zeroclaw/issues/9621) – Staged opt‑in telemetry | Open, needs‑review | Near‑term (v0.9.0) |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) – Unified attachment architecture | Open, proposed | Future roadmap |
| [#7232](https://github.com/zeroclaw-labs/zeroclaw/issues/7232) – Structured observability enhancement | Open, needs‑review | Future roadmap |

**Signal:** The team is actively scoping a “goal mode” system for multi‑turn bounded objectives, and a lightweight SOP status pane is the most advanced UI feature. Telemetry opt‑in and attachment unification are also gaining traction.

## 7. User Feedback Summary
**Pain Points:**
- **Audit‑trail falsification:** Timeout approvals recorded as denials (#9642) undermines security logging.
- **CLI inconsistency:** `cron add` examples are broken, causing operator confusion (#9672).
- **Channel duplication:** Telegram sends duplicate messages when the LLM returns both tool calls and content (#9718).
- **Windows deployment friction:** ZeroCode cannot connect to a daemon started via Task Scheduler (#9697).
- **Session‑state loss:** RPC prompt path fails to persist idle/running/error states (#9736).

**Positive Signals:**
- OAuth‑refresh retry loop refactor (#9162) appreciated for reducing duplication.
- Slack progress‑indicator feature (#7113) closed as completed.
- Maintainer decision tracker (#8692) welcomed for clearer RFC governance.

**Satisfaction/Dissatisfaction:** Users report frustration with channel‑delivery bugs and CLI example accuracy, while welcoming architectural RFCs and internal refactors that improve maintainability.

## 8. Backlog Watch
| Issue | Days Open | Risk | Needs Maintainer Review? |
|-------|-----------|------|--------------------------|
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) – Goal mode v1 RFC | 41 | High | Yes |
| [#7232](https://github.com/zeroclaw-labs/zeroclaw/issues/7232) – Structured observability RFC | 60 | High | Yes |
| [#9598](https://github.com/zeroclaw-labs/zeroclaw/issues/9598) – SOP permission contract RFC | 4 | High | Yes |
| [#9621](https://github.com/zeroclaw-labs/zeroclaw/issues/9621) – Telemetry opt‑in RFC | 3 | High | Yes |
| [#9005](https://github.com/zeroclaw-labs/zeroclaw/issues/9005) – Interaction‑harness context injection | 23 | High | Yes |
| [#9530](https://github.com/zeroclaw-labs/zeroclaw/issues/9530) – Risk precedence for test‑only changes | 6 | Low | Yes |
| [#8431](https://github.com/zeroclaw-labs/zeroclaw/issues/8431) – Temporary artifact lifecycle audit | 37 | Medium | – |

**Note:** A significant number of high‑risk RFCs and design trackers are awaiting maintainer review, which may slow progression toward v0.9.0. The goal‑mode series (#8303, #9702, #9703) is particularly critical for long‑term agent orchestration.

---
*Digest generated from ZeroClaw GitHub data on 2026-08-04. All links point to the public repository at github.com/zeroclaw-labs/zeroclaw.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*