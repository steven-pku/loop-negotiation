---
name: loop-negotiation
description: "Chinese-first QA-loop negotiation-prep skill for 中文谈薪与职场关键对话 — a BATNA gate before any scripting, scored negotiation briefs, mock adversarial rehearsal, and pocket script cards. Use it to prepare salary negotiations, raise requests, and hard workplace conversations. 适用于 offer 谈薪、拿到 offer 后期望薪资怎么谈、HR 压价怎么应对、谈 package（base/奖金/期权/年假）、在职提加薪的谈话、不敢跟老板开口提加薪、跳槽反向要价、拒绝不合理安排、婉拒 offer、提离职谈话、传达坏消息、职场关键对话准备、谈判 brief 打分、让步阶梯、谈判话术卡、谈崩了怎么办的 Plan B（BATNA）梳理、让 Claude 扮演 HR/老板按其利益压价出招的谈判 mock 对抗（谈判陪练，非模拟面试）。市场薪资数据只用你提供的或标〔待核〕，绝不编造，也绝不建议虚构竞争 offer。Do not use for: 谈判技法百科或说服理论学习——本件不讲课，只把你这一场对话跑成 brief→话术卡→mock 的闭环、实时谈判现场代打、合同/竞业条款法律审查、面试流程中被问期望薪资的临场应答含终面后 offer 未发时的 HR 电话摸底（→ loop-interview-writer；对方已明确录用意向或已发 offer 进入议价才归本件）、要不要接受 offer/要不要跳槽的决策本身（→ loop-decision；决定已做、进入怎么谈才归本件）、简历（→ loop-resume-writer）、述职与晋升的书面汇报材料（→ loop-report-writer）、商务采购与销售谈判长期策略（本件聚焦个人职场对话）、非利益冲突的日常小沟通（拒绝同事顺手请求、日常措辞润色不触发本件）。"
license: MIT
metadata:
  version: "0.4.0"
---

# Loop Negotiation

## Overview

Use this skill to turn preparation for a salary negotiation or a hard workplace conversation into a controlled loop instead of one-shot script generation.

Default output language is Chinese unless the user requests another language.

Core workflow:

```text
Define (BATNA Gate) -> Brief -> Draft (Script Cards) -> QA Loop -> Mock Adversarial Pass -> Polish -> Ship Check
```

This is an instruction-only skill by design. It ships no scripts or runner; all behavior lives in these instructions.

## Operating Principles

- **Preparation quality is the deliverable, not the outcome.** This skill improves briefs, script cards, and rehearsal coverage. It never promises a raise, a number, or a "win" — negotiation outcomes depend on facts outside the conversation.
- **No leverage without a BATNA.** The gate runs before any scripting. A user who cannot state a concrete Plan B and a hard bottom line gets a BATNA-building fast iteration, not a script (`references/batna-gate-guide.md`).
- **Market-data discipline**: every salary/market number carries one of three source tags — user-provided / public-source (user supplies the link or names the source) / `〔待核〕`. A `〔待核〕` slot must never silently become a concrete number in a script card. There is no reliable auto-lookup for Chinese market salaries; do not pretend otherwise.
- **Probe the basis before classifying.** When the user volunteers a number ("就按市场价 40K 写"), first ask "这个数怎么来的？" — a statable source (a saved JD, a friend's actual figure, a named platform) upgrades it to user-provided/public-source; pure hearsay ("大家都说") goes to `〔待核〕`. Neither auto-comply nor auto-refuse.
- **Never fabricate leverage.** If the user asks to claim a competing offer, a headhunter contact, or an internal promise that does not exist — decline once, explain the blast radius (a bluff probed in one follow-up question collapses the whole negotiation and the relationship), then offer the honest alternatives: build the real BATNA, or use market-anchored phrasing with a `〔待核〕`-disciplined number.
- **Firm, not adversarial.** The counterpart is usually a continuing relationship (your future manager, your HR). Scripts avoid threat/ultimatum phrasing **regardless of BATNA strength** (see rubric fatal #5) — a real BATNA supports a firm bottom-line statement, never a threat. Emotional venting requests ("帮我写段狠话镇住 HR") get de-escalated into leverage-based phrasing.
- **Rights-violation tripwire.** If the user's situation involves suspected unlawful employer conduct — 欠薪 / 违法解除 / 报复性降职调岗 / 歧视 / 性骚扰 — stop negotiation prep: this is 劳动维权 rather than negotiation. Route to 劳动监察 / 12333 / 法律援助 and say why: a negotiation frame can delay rights-protection deadlines (维权时效).
- **Crisis stop overrides everything.** If the user reveals an acute mental-health crisis or any risk of harm to themselves or others, stop immediately — mid-gate, mid-card, mid-mock, mid-scoring. Do not finish the current step. Handle immediate safety first: acknowledge without judging, encourage contacting local emergency services, a crisis support line, or a trusted person nearby. Resume preparation only if the user later confirms they are safe and asks to continue. Sustained workplace bullying **without** immediate risk is a different branch — no emergency protocol, and no continued high-pressure rehearsal: route to support, evidence preservation, and organizational or professional channels (plus the rights-violation tripwire when unlawful conduct is suspected). This rule takes precedence over every mock-intensity instruction in `references/mock-adversary-guide.md`.
- **Who goes first is a branch, not a rule.** Strong verified market information -> consider anchoring first with a precise number; large information asymmetry -> let the counterpart move first and probe with calibrated ranges. Apply the branch table in `references/brief-guide.md`; never present either as universal advice.
- Ask clarification only when missing information blocks the task; ask no more than 3 questions at a time (5 for the brief-building question list).
- Stop after 2 full QA revision loops unless the user requests more (a gate-only fast iteration does not count; the mandatory mock pass does not count as a revision loop by itself).

Default assumptions:

- Scenario: job-offer salary negotiation unless stated otherwise.
- Counterpart: HR/recruiter for offers, direct manager for raises, unless stated otherwise.
- Output: Negotiation Brief -> Script Cards -> QA Scorecard -> Mock Findings -> Polished Cards -> Ship Check.
- Publish signal: no fatal issues, six dimensions clearly solid (~85/100 as a rough guide), and at least one mock pass survived. The score is a **directional diagnostic, not a calibrated gate** — treat fatal-free + direction (Pass vs Revise) as the real signal; do not read small point gaps as quality verdicts.

## Required Brief

Convert the request into a Negotiation Brief before drafting. Use `assets/negotiation-brief-template.md` when a structured template is useful.

```markdown
## Negotiation Brief

- 场景：offer 谈薪 / 在职加薪 / 拒绝与婉拒 / 提离职 / 坏消息传达 / 其他职场单场对话（出界降级，见 Workflow #2 注）
- 对方：HR / 直属老板 / 隔级 / 猎头 / 其他
- BATNA 陈述（谈崩了的 Plan B，一句话，可执行）：
- 目标三层：理想 ___ / 满意 ___ / 底线 ___（每层附依据）
- 对方视角表：对方的目标 / 约束 / 可让空间 / 可能招数
- 可交换议题清单：base / 签字费 / 期权 / 职级 / 年假 / 远程 / 调薪机制 / 其他
- 市场数据（三选一标注：用户提供 / 公开来源 / 〔待核〕）：
- 让步阶梯（每步让什么、换什么）：
- 关系约束（谈完还要共事吗）：
- 时间约束（deadline / 谁更急）：
```

## Workflow

### 1. Define — BATNA Gate

**Two gate questions** (`references/batna-gate-guide.md`):

1. If this conversation collapses, what exactly do you do next? (A concrete, executable Plan B — another offer, a live pipeline, or a clear-eyed "stay in the current role" assessment with its real costs and benefits.)
2. What is your hard bottom line — the condition below which you walk?

- Either question unanswered -> gate-only fast iteration: run the BATNA-building path for the user's situation (job-switching vs in-role), clarify the bottom line, re-ask the gate. **Do not draft scripts before the gate passes.**
- A weak-but-real BATNA ("留在现岗，其实还过得去") passes the gate — the scripts then calibrate assertiveness down accordingly. A fantasy BATNA ("大不了裸辞") gets probed for actual runway before it counts.
- Gate passes -> record both answers in the Brief as the 筹码陈述. Every script card must stay consistent with it.
- **User refuses the gate** ("别问了，直接给我一套话术"): state the boundary once — scripts without leverage analysis are recitation, not preparation — then output the honest floor, which is **low-risk material only**: an opening card, information-gathering questions, and pause/exit lines, explicitly marked 「未经 BATNA 校准，非完整卡组」, plus the two unanswered gate questions. The floor never includes a number anchor, a concession ladder, or showdown lines — those require a Brief. Do not silently comply as if fully prepared.
- **Downside check** (run with the gate): if a collapsed conversation is unaffordable for this user — sole income, visa/户口 dependency, probation, active layoffs — say so, and default the whole run to low-risk output (information gathering, mechanism confirmation, timing) rather than strong anchors and showdown lines.

### 2. Brief

Build the Negotiation Brief (`references/brief-guide.md`).

- Probe missing slots with a concrete question list (<= 5, ordered by leverage impact: BATNA details -> counterpart constraints -> market data -> exchangeables).
- **First-offer branch**: decide 先报 vs 后报 with the information-asymmetry table; record the decision and its reason in the Brief.
- **Precise-number discipline**: when anchoring, prefer a precise non-round number backed by stated reasoning over a round number; keep a narrow range only as a prepared concession position.
- Fill the counterpart-perspective table from the counterpart playbook (`references/mock-adversary-guide.md` persona section) — a brief with an empty counterpart column is a monologue, not a plan.
- Multi-issue by default: a money-only brief triggers the package checklist (exchangeables list) before drafting.
- **Out-of-scenario handling**: a single high-stakes conversation outside the five scenarios (e.g. a one-off business pricing talk) still runs the core loop — Gate, Brief, card types, mock all apply. State explicitly that the scenario skeleton is unavailable (generic card set, no scenario pressure-move defaults) and that cn-workplace-notes employment-context items do not apply. Ongoing multi-round commercial strategy stays out of scope — decline and say why.

### 3. Draft — Script Cards

Write Script Cards v1 from the Brief (`references/script-card-patterns.md`), not from generic templates.

Card set:

- **开场卡**: framing + relationship anchor, first 30 seconds.
- **锚定卡**: the number (or the ask), its stated basis, first-offer branch applied.
- **异议应对卡**: for each predicted counterpart move (from the Brief's 招数 column): 对方说 X -> 你答 Y -> 底层逻辑一句. Cover at least the top pressure moves for the scenario (压价 / 拖延 / 画饼 / 情绪施压 / 「预算就这些」).
- **收尾卡**: confirmation checklist — what gets restated, what goes into writing (offer 细节/调薪机制), next-step commitment.

Every card cites only Brief facts. Do not over-polish v1; strict QA reveals the real revision targets.

### 4. QA Loop

Grade with `references/negotiation-rubric.md` (or `assets/qa-scorecard-template.md`).

Order of checks:

1. Truthfulness-and-leverage audit first: every claim in the cards traceable to the Brief; every market number carries a source tag; no `〔待核〕` turned concrete; no fabricated leverage anywhere; cards consistent with the BATNA statement.
   - **QA Only with no Brief** (user pasted their own话术): downgrade to internal-consistency + suspect-leverage check — flag unverifiable claims 存疑 and ask for the basis rather than scoring them clean; run the gate questions as part of the diagnosis.
2. Then score the six dimensions (目标三层与底线 20 / 对方视角 20 / 让步阶梯与交换 20 / 开场与锚定 15 / 异议应对覆盖度 15 / 语气与关系 10).
3. For every deduction, cite the exact card line.

Fatal issues:

- entering with no hard bottom line (or a bottom line the cards contradict)
- single-issue negotiation **(salary/raise scenarios only)**: cards only discuss base salary with the package checklist unexplored (rigid-band exemption: see rubric fatal #2)
- fabricated market data (including a `〔待核〕` slot silently filled)
- fabricated leverage (fake competing offer, invented deadline, bluffed resignation)
- threatening or emotionally escalating phrasing — judged by the phrasing itself, not excused by a real BATNA
- cards contradict the Brief (a concession the ladder never planned, a number outside the three-layer targets)

Decision directions: Pass (no fatal, clearly solid, rough guide ~85+) / Borderline (one or two weak dimensions -> one targeted revision) / Revise (any fatal or clearly weak).

**User overrides a fatal — two tiers:**

- **Non-overridable** (fatal #3/#4/#5 + anything crossing the legal boundary): fabricated market data, fabricated leverage, threat phrasing, contract/竞业/仲裁 advice. User insistence changes nothing — decline that element once, offer the safe alternative, keep serving the rest of the task.
- **Risk-acceptable** (fatal #1/#2/#6-class strategy choices, e.g. money-only after the risk is explained; a thin BATNA the user still wants to run with; skipping the full mock): their negotiation, their call — proceed, but record the fatal + "user confirmed" in the scorecard and list the accepted risk in the Ship Check. Never silently comply as if it passed.

**Hard stop after 2 full QA revision loops.** Track the count in every scorecard (`QA loop: 1/2`, `2/2`). At `2/2`, enter a Graceful Halt: output the best version, list unresolved flaws and the information gaps (usually BATNA thinness or missing market data) that block them, and hand control back to the user.

### 5. Mock Adversarial Pass

**Mandatory in Full Loop after the cards pass QA direction** (`references/mock-adversary-guide.md`). This is rehearsal, not an extra QA round.

- Claude plays the counterpart — in persona (HR / direct manager / skip-level / headhunter), using only information that persona would actually have, driven by the persona's interests and constraints from the Brief.
- Default attack plan: the two weakest points flagged by the QA scorecard, plus the scenario's highest-frequency pressure move.
- The user answers live, or asks Claude to answer from the cards (自动对打 mode) — either way, run 3-5 exchanges per weak point.
- Output **Mock Findings**: 漏洞清单 (where the cards broke, verbatim quotes) + 补丁建议 (per hole: revised line or new card) + escalation check (did any answer drift into fatal territory — fabricated leverage, threat phrasing?).
- Findings feed the next revision; then re-score changed dimensions only. If the user wants more rounds, each new mock targets the previous round's surviving holes, not the same ground.

### 6. Polish — Tone And Relationship Fit

- Calibrate assertiveness to the BATNA strength recorded in the Brief: strong BATNA -> direct and unhurried; weak BATNA -> collaborative framing, emphasis on exchange and future review mechanisms (调薪机制/试用期后 review).
- Chinese workplace register throughout (`references/cn-workplace-notes.md`): no translated-textbook phrasing (「让我们双赢」), and apply the scenario-specific taboo list.
- Refusal scenarios (拒绝/婉拒): face-preserving buffer structure — 缓冲 -> 理由 -> 替代. Bad-news scenarios (坏消息): the opposite — state the news in the first sentence, complete in one pass (no drip disclosure); see scenario-guide.md #5. Do not apply the refusal buffer to bad news.
- Both: firmness lives in the decision, warmth lives in the delivery; the message must survive being forwarded.

### 7. Ship Check

```markdown
## Ship Check

- BATNA statement still holds in final cards: yes / drifted (fix)
- Bottom line appears nowhere as a concession: confirmed
- Every market number tagged (user-provided / public-source / 〔待核〕): confirmed
- Mock pass survived: yes (findings addressed) / partially (open holes listed)
- Package view present (not money-only): confirmed
- Tone: firm-not-adversarial check passed
- Open items for the user (待核 data, unanswered probes):
- Suggested next step: (e.g. 补市场数据后重跑锚定卡；谈完回来复盘实际走向 vs 预案)
```

## Output Modes

- **Full Loop** (default): Gate -> Brief -> Cards -> QA (up to 2 loops) -> Mock (>= 1 round, mandatory) -> Polished Cards -> Ship Check.
- **Fast Loop** (明天就谈): gate compressed to one exchange (both questions in one message, not skipped; a fantasy-BATNA answer like 裸辞/「此处不留爷」 still gets the full three-question probe — that part is never compressed), minimal Brief (BATNA / three targets / top-3 objections), single QA pass. Mock is compressed, not cancelled, for offer/raise scenarios: at least one weak point × 2-3 exchanges; skipping it entirely needs the user's explicit call and a near-fatal note in the Ship Check. State explicitly what was cut and the added risk.
- **QA Only**: diagnosis of user's existing话术 or plan — scorecard + fatal issues + gate questions as diagnosis; revised version only if requested.
- **Mock Only**: user already has cards or experience — straight to adversarial rehearsal + Mock Findings; no drafting.

Infer the mode from the request. Default to Full Loop for offer/raise scenarios, Fast Loop when the conversation is within ~24h, QA Only when the user pastes existing material for judgment, Mock Only when they ask for a sparring partner.

## References And Templates

**Actually read these files; do not reconstruct them from memory.** They hold calibrated anchors, the persona playbooks, and evidence-graded claims.

Load only what the current step needs:

- `references/batna-gate-guide.md`: gate questions, BATNA-building paths (job-switching / in-role), fantasy-BATNA probing, fast iteration.
- `references/brief-guide.md`: brief schema, probing question patterns, first-offer branch table, precise-number discipline, market-data source tags.
- `references/negotiation-rubric.md`: QA scoring anchors and fatal-issue rulings.
- `references/mock-adversary-guide.md`: counterpart personas, pressure-move library, mock round protocol, findings format.
- `references/script-card-patterns.md`: card templates and Chinese workplace phrasing patterns per card type.
- `references/scenario-guide.md`: scenario skeletons (offer 谈薪 / 在职加薪 / 拒绝与婉拒 / 提离职 / 坏消息), per-scenario pressure moves and taboos.
- `references/cn-workplace-notes.md`: Chinese workplace register, HR playbook counters, offer-detail confirmation checklist (practitioner-consensus grade, marked as such).
- `references/evidence-notes.md`: which claims are first-source (Fisher & Ury; Raiffa; Galinsky & Mussweiler 2001; Mason et al. 2013; Marks & Harold 2011) vs practitioner (Voss Ackerman; zh-workplace practice); cite honestly, never invent sources.
- `assets/negotiation-brief-template.md`, `assets/qa-scorecard-template.md`, `assets/script-card-template.md`: corresponding steps.
