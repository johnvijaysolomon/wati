<!-- filled by /dsf:ia — started from .design/templates/sitemap.md, structure unchanged -->

# Sitemap

Four sections, in this order: **Entities · Screens · Navigation · Traceability**.
Every screen serves a job. A screen with no job and a job with no screen are the same defect,
caught by the same matrix at the bottom of this file.

Job ids reference `people/jtbd.md`: **Main**, **R1**–**R5**, **E1**–**E2**, **S1**–**S2**.
Primary persona is **P1**, "the one who has already failed once" (`people/personas.md`).
MVP core, fixed at the `users.4` gate: **R1**, **R2**, **R5**.

---

## Entities

Objects before screens. The main things a person deals with in order to close their jobs.

| Entity | Fields and parts it contains | Which job produces it (`jtbd.md` reference) | Related to |
|---|---|---|---|
| **Channel** | type, handle or number, connection state, Meta approval state, health, live/paused | **R1** — "see it answering my own real questions within the hour" needs somewhere to answer | Workspace, Conversation |
| **Knowledge source** | origin (site, doc, FAQ, past conversations), last synced, item count, coverage, sync status | **R1** — the AI cannot answer the buyer's own questions until it has the buyer's own material | AI agent, Answer |
| **AI agent** | tone, guardrails, handover rules, channels covered, live/paused, current version | **Main** — the thing that handles the questions; **E2** — "feel I still control what it says" | Knowledge source, Guardrail, Conversation, Change |
| **Guardrail** | statement in the operator's own words, scope, active, author, created | **E2** — control over what it says. Pattern 5 risk applies: it must be readable back | AI agent, Change |
| **Conversation** | channel, customer, messages, who answered (AI or human), outcome label, reopened flag | **Main**, **R2**, **R3** — the unit everything is measured on | Channel, Theme, Resolution |
| **Failure theme** | name, size, channels affected, first seen, state (`new` / `fixing` / `validating` / `resolved` / `regressed`), example conversations | **R2** — "find out before they tell me". **The unit of work of the chosen pattern** (`research.4` gate: clustered themes, not items) | Conversation, Change |
| **Change** | what changed, author, timestamp, before/after, linked theme, validation state | **R2**, **E1** — "check things myself"; benchmark C8, attributable history | Theme, AI agent, Guardrail, Knowledge source, Replay |
| **Replay** | change under test, conversations sampled, diff of outcomes, run at | **R4** — "know what a change will do before customers see it". Benchmark mechanic 1 | Change, Conversation |
| **Resolution** | conversation, confirmed or assumed, reversed on reopen, definition version | **R3** — "a number I can defend". Modelled after the only published definition in the market (Intercom) | Conversation |
| **Account** | plan, billing cycle, invoices, usage, cancellation state | **R5** — "leave without a fight", the best-evidenced job in the project | Workspace |
| **Export bundle** | contents (contacts, knowledge, conversations, templates), format, generated at | **R5** — leaving without a fight requires taking your material with you | Account |

**Two notes the table cannot carry.**

- **Replay is an entity, not a screen.** Phase 2 Q1 found the primary persona's whole setup budget
  is *"under 30 minutes"* because they are *"running a business, not a software project"*, so
  replay survives **only if it costs seconds and happens inline**. It is modelled here and appears
  in the tree as a step inside a fix, never as a destination.
- **Channel carries the brief's weakest commitment.** WhatsApp is confirmed (78% of Indian SMBs),
  Instagram is generically supported. `[?]` **email and SMS are unevidenced as inbound channels**
  for P1 — the brief commits to five, so they are modelled, and marked here so no later phase
  reads the commitment as evidence.

### Questionable

<!-- entities with no job behind them. They stay here until a job claims them or they are cut. -->

- **User / role assignment** — assumed because the brief says the Administrator owns "users,
  roles… " and names ten roles. **No job in `jtbd.md` produces it.** P1 is a 2–10 person business
  (R1) where roles plausibly collapse to one person with ten checkboxes — an open `[?]` phase 2
  left unresolved. Modelled, but its screen is an `[ORPHAN]` below and is honest about it.
- **Template** — assumed because WhatsApp requires approved templates. But the campaign composer
  was **cut at the `users.4` gate**, and no remaining job sends outbound. `[?]` templates may still
  be required for service messages outside the 24-hour window — a platform constraint, not a job.
  Not given a screen until a job claims it.
- **Contact** — assumed because every competitor has a contact list. **No job requires one.**
  Conversations carry a customer reference; a CRM is not job-backed here. Cut unless phase 4
  surfaces a need.

---

## Screens

**An indented text tree, not a table.** Next to **every** screen, in parentheses, the job it
serves, referencing `jtbd.md`. A screen with no job is marked `[ORPHAN]`.

`[P]` = the primary persona needs it · `[S]` = secondary.
Empty, error and loading are **states**, not screens — they belong in `wireframes/_screens.md`.

```
Overview (Main — is it handling things without me?)                    [P]
├── Themes (R2 — find out before the customer tells me)                [P]
│   ├── Theme detail (R2 — what went wrong, and fix it here)           [P]
│   │   ├── Conversation (R2, E1 — read the actual exchange)           [P]
│   │   └── ‹inline: Replay› (R4 — what this change would have done)   [P]
│   └── Validation (R2 — did the fix hold, on real traffic?)           [P]
├── Answers (Main, E2 — what it knows and how it behaves)              [P]
│   ├── Knowledge (R1 — give it your own material)                     [P]
│   ├── Guardrails (E2 — what it must not say)                         [P]
│   └── Handover (E2, S1 — when a human takes over)                    [P]
├── Channels — settings (R1 — connect where customers message)         [P]
│   └── Channel detail (R1 — connect, configure, monitor, govern)      [P]
│       ·  one screen, parameterised by channel type, not six screens
│       ·  WhatsApp · Web chat widget · Instagram · Messenger
│       ·  Email [?] · SMS [?]  — five channels, per the brief
└── Account (R5 — leave without a fight)                               [P]
    ├── What it costs and saves (R3, S2 — a number I can defend)       [P]
    ├── Billing (R5 — plan, invoices, cancel)                          [P]
    ├── Export (R5 — take your material with you)                      [P]
    └── People and access [ORPHAN]                                     [S]

Setup — first run (R1 — live within the hour)
├── Connect a channel (R1)                                             [P]
├── Load your knowledge (R1)                                           [P]
└── Go live (R1 — watch it answer a question you wrote)                [P]

Inbox — the exception surface (Main, escalation path)                  [S]
└── Handled conversation (S1 — a person picks up where the AI stopped) [S]
```

**Four decisions this tree makes, stated so they can be argued with.**

1. **`Overview` is the landing screen, not an inbox.** The brief makes the inbox "an exception
   surface, not the workspace", and the `research.4` gate disqualified queue triage. `Inbox` is
   `[S]`, one level down, and belongs to the Operator rather than to P1.
2. **`Themes` sits directly under `Overview`, and there is no per-conversation queue for P1.**
   The chosen pattern's unit of work is the theme; `Conversation` exists only *inside* a theme,
   as evidence, not as a destination to work through.
3. **Replay is `‹inline›`, not a screen.** Marked in the tree with angle brackets to make the
   distinction visible. Making it a destination would break the <30-minute budget that phase 2
   Q1 established for this persona.
4. **`Account` is a first-class branch, not a footer link.** R5 — "leave without a fight" — is
   the best-evidenced job in the project and scores 3 for the primary persona. Burying billing,
   export and cancellation is precisely the pattern the reviews record as the reason people
   leave. `Export` is a peer of `Billing`, deliberately.

**Screen responsibilities added at the `ia.6` critique.** Fixes applied at the source here, then
propagated into `ia/flows.md`. Approved defects: D1, D2, D3, M1, M2.

| Screen | Responsibility added | Defect it closes |
|---|---|---|
| `Handover` | **Owns what happens when there is no human.** A fallback reply the Administrator writes, plus the rule for when it fires. P1 is a 2–10 person business, so "nobody on the Operator role" is the *normal* configuration, not the edge case | **D1** — a dead end that landed on the customer |
| `Overview` | **Carries the two signals that used to be silent:** channel health (replies are not landing) and unattended handovers (the AI asked for a person and no person came). The product notices; the Administrator is not required to already know | **D1, D2** |
| `Validation` | **Carries an in-progress state, not just pass/fail.** Benchmark mechanic 2 named the sequence — `Not started → Started → Looking good → Passed / Failed`. "Looking good" is what makes a validation trustworthy while it is still running | **M1** |
| `Export` | **Carries an empty state.** A new or already-emptied account exporting nothing is real, and a blank download on the way out is the worst possible last impression for the job this screen serves | **M2** |
| `Connect a channel` | **Distinguishes a recoverable rejection from a permanent one.** A name that violates policy is fixable; a number already bound to another BSP may not be, and the buyer is mid-migration | **D3** — replaced a dead end we had decided not to ship with the one that is real |

**The one orphan, kept visible.** `People and access` serves no job in `jtbd.md`. The brief
requires it — the Administrator owns "users, roles" and ten roles exist — but no job produces it,
and P1 is a business small enough that the roles may collapse to one person. It stays `[ORPHAN]`
`[S]` rather than being given an invented job.

**`Channels` is a settings surface, not a monitoring one** (human, at the `ia.2` gate: *"a
settings page of sorts"*). It lists every channel as a row with its connection and approval state;
**`Channel detail` is one screen parameterised by channel type, not one screen per channel** —
six near-identical screens would be six times the wireframes, the copy and the states for a
difference that is entirely in the connection mechanics. Per-channel divergence lives in the
states of that one screen, recorded in `wireframes/_screens.md` at phase 4.

`[?]` **Email and SMS** appear here on the brief's authority alone; phase 2 found no evidence
P1's customers arrive there. **TikTok** was requested at the `ia.2` gate, held at a rule-12
guard as a sixth channel the brief does not contain, and **withdrawn** by the human. It is not in
this tree and not in the traceability matrix; it is recorded in `design-system/backlog.md` with
what would let it in.

---

## Navigation

**Global navigation — 3 to 5 items.** Each item is an entrance to a main job cluster, and each
one states the job behind it. "Because everyone has it" is not a reason.

| Item | Job cluster it opens | Why it earns a global slot |
|---|---|---|
| **Overview** | **Main**, R3 | The one question this persona opens the product to ask — *is it handling things without me?* It is the landing screen, so it costs no tap |
| **Themes** | **R2** (MVP core) | Where a bad answer is found before the customer reports it. The chosen pattern's unit of work; without a global slot the improvement loop has no front door |
| **Answers** | **Main**, R1, E2 | What the AI knows and how it is allowed to behave — knowledge, guardrails, handover. The only place the product is *changed* rather than watched |
| **Channels — settings** | **R1** (MVP core) | Connect, configure, monitor, govern. Earns its slot on first run; afterwards it is visited rarely but must stay findable when a number or an approval breaks |
| **Account** | **R5** (MVP core), R3 | Cost, billing, export, cancellation. **A global slot for the exit is a deliberate trust decision** — R3 in `research.md` records dark patterns hiding the cancellation form as a top reason this persona leaves a vendor |

**Sixth item, permission-gated:** `Inbox` appears in global navigation **only for roles with the
Operator permission**. It is the exception surface, not P1's workspace (brief: the inbox is "an
exception surface"), so an Administrator without the Operator role does not see it at all. This is
the first concrete use of the brief's permission-gated model.

**Not in global navigation:** `Setup — first run`, which replaces the shell until it completes
rather than sitting alongside it. A first-run path that is also a permanent menu item is a first-run
path nobody finishes.

**Tap-depth budget.** Taps from the first screen to the **main job**, for the **primary
persona**. Budget: **≤ 3**.

| Path (screen → screen → screen) | Taps | Within budget? |
|---|---|---|
| **Main** — `Overview` (landing) | **0** | yes — see the honesty note below |
| **R2** (MVP core) — `Overview` → surfaced theme → `Theme detail` | **1** | yes |
| **R2** via the full list — `Overview` → `Themes` → `Theme detail` | **2** | yes |
| **R1** (MVP core) — `Setup` → `Connect a channel` → `Load your knowledge` → `Go live` | **3** | yes, at the limit |
| **R5** (MVP core) — `Overview` → `Account` → `Export` or `Billing` | **2** | yes |
| **R3** — `Overview` → `Account` → `What it costs and saves` | **2** | yes |
| **E2** — `Overview` → `Answers` → `Guardrails` | **2** | yes |

**Honesty note on the main job's 0.** A budget met by declaring the landing screen the answer is
usually a budget being gamed, so it is stated rather than claimed. The main job — *repeat questions
handled without me* — is closed by the **AI doing the work**, not by a screen. The Administrator's
only contact with it is confirming that it happened, which is what `Overview` is for. **The counts
that should be held against later phases are the MVP-core ones: R1 at 3, R2 at 1–2, R5 at 2.**
R1 sitting exactly at the limit is the number to watch — it is also the job the 10-minute success
criterion measures, and phase 2 found the category's whole setup budget is *"under 30 minutes"*.

**Trade-off, if over budget:** none taken — nothing exceeds three. The pressure point is R1, where
a fourth step would breach both this budget and the brief's success criterion at the same time.

**Levels**

| Level | Screens | Why here |
|---|---|---|
| **Global — always visible** | `Overview`, `Themes`, `Answers`, `Channels — settings`, `Account`; `Inbox` for the Operator role only | Five entrances, one per job cluster, plus a permission-gated sixth |
| **Contextual — appears inside a flow** | `Theme detail`, `Conversation`, `Validation`, `‹inline: Replay›`, `Knowledge`, `Guardrails`, `Handover`, `Channel detail`, `What it costs and saves`, `Billing`, `Export`, `Handled conversation` | Reached from their parent, in the middle of doing the thing. **`Billing` and `Export` are deliberately here and not in Deep** — R5 is an MVP-core job, and a buried exit is the defect this product is arguing against |
| **Deep — rare actions** | `People and access` | The tree's only `[ORPHAN]`. It has no job, so it gets the level that costs the most to reach — which is the honest placement for a screen the brief requires and the evidence does not |

---

## Traceability

Rows: **all** jobs from `jtbd.md`. Columns: **all** screens from the tree above.
`✓` = the screen genuinely takes part in closing that job.

Abbreviations, left to right: **Ov** Overview · **Th** Themes · **TD** Theme detail ·
**Cv** Conversation · **Vl** Validation · **An** Answers · **Kn** Knowledge · **Gd** Guardrails ·
**Hv** Handover · **Ch** Channels—settings · **CD** Channel detail · **Ac** Account ·
**Co** What it costs and saves · **Bi** Billing · **Ex** Export · **PA** People and access ·
**C1** Connect a channel · **L1** Load your knowledge · **G1** Go live · **In** Inbox ·
**HC** Handled conversation

| Job \ Screen | Ov | Th | TD | Cv | Vl | An | Kn | Gd | Hv | Ch | CD | Ac | Co | Bi | Ex | PA | C1 | L1 | G1 | In | HC |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Main** — handled without me | ✓ | | | | | ✓ | ✓ | ✓ | ✓ | | ✓ | | | | | | | | | ✓ | ✓ |
| **R1** — live within the hour | ✓ | | | | | | | ✓ | | ✓ | ✓ | | | | | | ✓ | ✓ | ✓ | | |
| **R2** — find out first | ✓ | ✓ | ✓ | ✓ | ✓ | | ✓ | ✓ | ✓ | | | | | | | | | | | | |
| **R3** — a number I can defend | ✓ | | | | | | | | | | | ✓ | ✓ | | | | | | | | |
| **R4** — know what a change does | | | ✓ | | | | ✓ | ✓ | | | | | | | | | | | | | |
| **R5** — leave without a fight | | | | | | | | | | | | ✓ | | ✓ | ✓ | | | | | | |
| **E1** — check things myself | ✓ | | ✓ | ✓ | ✓ | | | | | | | | ✓ | | | | | | | | |
| **E2** — control what it says | | | | | | ✓ | | ✓ | ✓ | | | | | | | | | | | | |
| **S1** — customers not fobbed off | | | | | | | | | | | | | | | | | | | | | |
| **S2** — look more capable | | | | | | | | | | | | | | | | | | | | | |

**ORPHAN SCREENS** — columns with no `✓`.

| Screen | Why does it exist? | Resolution |
|---|---|---|
| **People and access** | The brief requires it — the Administrator owns "users, roles" and ten roles exist — but no job in `jtbd.md` produces it, and phase 2 left `[?]` whether the ten roles map to ten people or to one person with ten checkboxes | **Keep, at Deep level, orphan status visible.** Not deleted: it is a brief commitment, and the permission model is already load-bearing (the `Inbox` global slot is gated on it). Not laundered with an invented job either. Revisit when phase 2's roles `[?]` closes |

**ORPHAN JOBS** — rows with no `✓`.

| Job | Where is the person supposed to do this? | Resolution |
|---|---|---|
| **S1** — *customers do not feel fobbed off* | **Nowhere, and that is the honest answer.** No Administrator-facing screen closes it. `Handover`, `Inbox` and `Handled conversation` *influence* it, but the job is about what the **customer** feels, and this product's screens are not where a customer stands | **Backlog, not a screen.** It is hypothesis **H2** in `jtbd.md`, and phase 2 recorded that this research has **no end-customer evidence at all** — every source describes the buyer, not the buyer's customer. It becomes a **voice and tone** problem at phase 5 rather than an IA one |
| **S2** — *look more capable than our headcount* | Nowhere as a destination. `What it costs and saves` was ticked in the first pass and the tick was **removed on the read-back** — that screen shows cost, not how the business is perceived | **Backlog.** Half-evidenced in `jtbd.md` (R7 confirms the cost-vs-hire comparison; the "how we are seen" half is `[?]`). Served incidentally by the main job working at all. No screen is invented for it |

**Read-back note, recorded because the first pass was wrong.** The first version of this matrix had
**zero orphan jobs** — S1 was ticked against `Handover`/`Inbox`/`Handled conversation` and S2
against `What it costs and saves`. Reading the rows out loud, naming the screen for each job, both
ticks turned out to be stretches placed to make the matrix look complete. They were removed. The
matrix now leaks in exactly the place the evidence is thinnest: **the two social jobs, which are
also the two weakest-evidenced jobs in `jtbd.md`.** That correlation is the matrix working.

**Result: 1 orphan screen, 2 orphan jobs, all three resolved above and none deleted quietly.**
