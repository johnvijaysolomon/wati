<!-- filled by /dsf:users — started from .design/templates/jtbd.md, structure unchanged -->

# Jobs to be done

Every job is written as **"When [situation], I want [motivation], so that [outcome]"**, and
every job names the persona it belongs to and the research data it grew out of.

**If a feature name appears inside "I want", it is not a job — it is a feature.** Rewrite it as
human progress. A job backed by nothing goes to the **Hypotheses** section, not the main list.

Personas are `P1` (primary — the one who has already failed once), `P2` (the one who owns the
number), `P3` (the one who gets called when it breaks). Sources cite `R1`–`R8` in
`research/research.md` → *Re-research after personas*, plus named COMPETITORS / BENCHMARK
findings. **Feature-name check run on every line below: no product noun appears inside any
"I want".**

---

## Main job — exactly one

**When** the same questions keep arriving on WhatsApp and I am the one answering them,
**I want** them handled without me,
**so that** I can spend my day on the work only I can do.

- Persona: **P1** (primary), shared with P2
- Source: R5 (*"limited in automation options"* — the automation they bought does not hold a real
  conversation), R7 (a bot is positioned as *"less than the cost of a single additional support
  hire"*, i.e. the alternative to automation is hiring), R1 (2–10 person teams have no one to
  delegate to)

## Related jobs — 3 to 5, on the way to the main one

| # | When… I want… so that… | Persona | Source |
|---|---|---|---|
| 1 | **When** I am setting this up for the first time, **I want** to see it answering my own real questions within the hour, **so that** I know I have not bought another thing that does not work | P1 | R2 (*"time from signup to working bot: 15-20 minutes"*; the full stack is *"1-2 business days minimum"*), R6 (self-serve, non-technical), brief — the 10-minute criterion |
| 2 | **When** a customer gets a bad answer, **I want** to find out before they tell me, **so that** I am not learning about my own business from a complaint | P1, P2 | BENCHMARK mechanic 3 (Sentry's automatic `Regressed`, Datadog burn-rate alerts); COMPETITORS shared pattern 3 (the hard group has no vocabulary for this at all) |
| 3 | **When** someone asks me whether this is actually working, **I want** a number I can defend, **so that** I am not just repeating what a vendor told me | P2, P1 | COMPETITORS shared pattern 2 (six claim 67–98%, one defines); BENCHMARK dimension; Tidio needing to *guarantee* rather than claim |
| 4 | **When** I change how it answers, **I want** to know what that will do before customers see it, **so that** I am not experimenting on real people | P3, P2 | COMPETITORS difference 3 (only the aspirational group has a pre-flight); BENCHMARK mechanic 1. `[?]` no user in the corpus asks for this — inferred from what the aspirational vendors built |
| 5 | **When** it stops being worth it, **I want** to leave without a fight, **so that** I am not trapped paying for something I have stopped using | P1 | R3 — four separate verbatim reviews: *"support becomes unresponsive once you request cancellation"*, dark patterns on the cancellation form, *"force annual payments once you proceed to checkout"*, *"they continue to charge me every month"* |

Related job 5 is the **best-evidenced job in this file** and the one most products refuse to
design for. It is kept in the main list rather than the hypotheses precisely because the evidence
is stronger than for anything else here.

## Emotional jobs

<!-- how the person wants to feel; listed separately from functional jobs -->

| # | Job | Persona | Source |
|---|---|---|---|
| E1 | **When** I have been burned by a vendor once, **I want** to be able to check things myself, **so that** I never have to take another promise on faith | P1 | R3, R4 — the corpus is dominated by trust failures (billing, cancellation, support latency) rather than by feature complaints |
| E2 | **When** I let something answer my customers for me, **I want** to feel I still control what it says, **so that** I am not embarrassed by my own business | P1, P2 | `[?]` **hypothesis** — inferred from the aspirational group building guardrails and simulations, not from any user statement. See Hypotheses H1 |

## Social jobs

<!-- how the person wants to be seen by others -->

| # | Job | Persona | Source |
|---|---|---|---|
| S1 | **When** a customer messages my business, **I want** them to feel they reached a business that has its act together, **so that** we do not look like we are fobbing them off | P1 | `[?]` **hypothesis** — see H2 |
| S2 | **When** I am asked how we keep up with customer messages at our size, **I want** a good answer, **so that** we look more capable than our headcount | P1 | R7 (the category sells itself as cheaper than a hire — the comparison the buyer is already making is to *staff*, which is a social frame as much as an economic one). Partly evidenced; the "how we are seen" half is `[?]` |

## Hypotheses

<!-- jobs that sound right but have no data behind them. They stay here until data arrives. -->

| # | Job | What would confirm it | Where to look |
|---|---|---|---|
| H1 | **When** the AI answers unsupervised, **I want** to feel in control of what it says, **so that** I am not embarrassed by it | One user describing fear or embarrassment about an automated reply, in their own words | G2 / Capterra one- and two-star reviews filtered on "bot" or "AI"; r/ecommerce and r/smallbusiness threads on automated replies |
| H2 | **When** a customer is answered by a machine, **I want** them not to feel fobbed off | Evidence about *end-customer* reaction, which this research has none of — every source is about the buyer, not the buyer's customer | End-customer sentiment studies on WhatsApp support; a vendor case study reporting CSAT split by AI vs human |
| H3 | **When** I set up the AI, **I want** to hand the fiddly integration work to someone technical, **so that** I am not blocked on skills I do not have | A P1-persona user describing hiring an agency or a freelancer for BSP setup | Upwork / Fiverr listings for "WhatsApp API setup"; agency service pages; the `Developer` role's real usage |
| H4 | **When** conversations arrive on channels beyond WhatsApp, **I want** them handled the same way, **so that** I am not running several systems | A P1 user complaining about channel fragmentation. Currently only the *vendor* side is evidenced — AiSensy is WhatsApp-only (R5) — not the demand side | Reviews mentioning Instagram or email alongside WhatsApp; Meta's own multi-channel adoption data |

---

## Matrix — jobs × personas × features

Rows: **every** job above (main, related, emotional, social). Columns: **every** persona from
`people/personas.md`, plus the two mandatory columns **FEATURE** and **COMPETITORS**.

Cell for a persona column: importance of that job to that persona, **1–3**, **and** what in
`research/research.md` confirms it. Unknown importance is `[?]` — never an averaged number.

| Job | P1 · primary | P2 | P3 | FEATURE — what closes it | COMPETITORS — already closed? |
|---|---|---|---|---|---|
| **Main** — repeat questions handled without me | **3** · R5, R7 — the whole category is sold against this | **3** · R7, BENCHMARK dimension | **1** · not their job; they build it | An AI that answers from the business's own material across all five channels | **Partly.** Every player claims it. AiSensy and Interakt sell it as a *paid add-on* on a keyword core (screens: `aisensy-pricing-two-skus.png`, `interakt-pricing-ai-addon.png`); Intercom, Zendesk, Tidio include it |
| **R1** — see it working on my real questions within the hour | **3** · R2, R6 — self-serve setup is how this market is bought | **2** · `[?]` an ops lead may accept a longer runway; unconfirmed | **2** · R6 — they are pulled in exactly when the hour runs out | First-run path that reaches a live answer on the buyer's own content, with Meta's external wait running in parallel rather than blocking | **No.** Vendors advertise "10-minute API approval" while the tested stack is *"1-2 business days minimum"* (R2). Nobody designs the waiting state |
| **R2** — find out about a bad answer before the customer tells me | **3** · R3, R4 — this persona learns about problems late and it is their top pain shape | **3** · BENCHMARK dimension | **2** · `[?]` hypothesis | Failure themes surfaced automatically, with regression when a fixed theme returns | **No.** Named in the aspirational group only (Watchtower, Monitors, Discover Agent); COMPETITORS shared pattern 3 shows the hard group has no vocabulary for it |
| **R3** — a number I can defend | **2** · `[?]` P1 may not be asked for a number by anyone; inferred, not confirmed | **3** · COMPETITORS shared pattern 2 | **1** · not their job | A published, conservative definition of a resolution, measured on the account's own traffic | **Barely.** Only Intercom defines it, and only because it bills on it. Nobody in the hard group publishes a method |
| **R4** — know what a change will do before customers see it | **1** · Pass 2 Q1 — a <30-min setup budget (*"running a business, not a software project"*) makes a separate pre-flight step intolerable; viable only if it costs seconds inline | **2** · COMPETITORS difference 3 | **3** · BENCHMARK C4 + C8 | Replay a change against the account's own recent conversations and diff the outcomes | **No.** Ada, Decagon and Sierra have it; nothing in the hard group does |
| **R5** — leave without a fight | **3** · R3 — four verbatim reviews, the strongest evidence in the corpus | **2** · `[?]` | **1** · not their job | Export, cancellation and billing that are as legible as signup — no dark patterns, no forced annual at checkout | **No — actively the opposite.** R3 documents dark patterns, forced annual billing and charges continuing after cancellation |
| **E1** — check things myself, never take a promise on faith | **3** · R3, R4 | **2** · `[?]` | **2** · `[?]` | Everything the product asserts is traceable to something the Administrator can open and inspect | **No.** The market's norm is an unexplained percentage |
| **E2** — feel in control of what it says | `[?]` · hypothesis H1 | `[?]` · hypothesis H1 | **2** · `[?]` | Guardrails the Administrator can read back in their own words | **Partly.** Sierra's "built-in guardrails", Decagon's natural-language AOPs; nothing in the hard group |
| **S1** — customers do not feel fobbed off | `[?]` · hypothesis H2 | `[?]` · hypothesis H2 | **1** · not their job | `[?]` — no feature proposed, because the job is unevidenced | `[?]` — no player measures end-customer reaction publicly |
| **S2** — look more capable than our headcount | **2** · R7, partly | **1** · `[?]` at 11–50 people this framing weakens | **1** · not their job | `[?]` — served incidentally by the main job rather than by a feature of its own | **Yes, rhetorically.** Every vendor sells this in copy; none builds for it |

---

## MVP core — three jobs

Important to the **primary persona** *and* **not covered by the market** (read both facts off
the matrix, do not re-argue them).

1. **R1 — see it working on my own real questions within the hour.**
   Matrix evidence: P1 = **3**; COMPETITORS = **No** — vendors advertise "10-minute API approval"
   against a tested *"1-2 business days minimum"*, and nobody designs the waiting state.
2. **R2 — find out about a bad answer before the customer tells me.**
   Matrix evidence: P1 = **3**; COMPETITORS = **No** — named only in the aspirational group, and
   COMPETITORS shared pattern 3 records the hard group as having no vocabulary for it.
3. **R5 — leave without a fight.**
   Matrix evidence: P1 = **3**; COMPETITORS = **No, actively the opposite** — four verbatim
   reviews document dark patterns, forced annual billing and charges after cancellation.

**Note on what this selection does *not* include.** The main job itself is not in the MVP core
because it scores **Partly** on coverage — every competitor claims it. It is table stakes: the
product is not viable without it, and it differentiates nothing. **R3 (a number I can defend)**
narrowly misses on the primary persona's score (**2**, and that 2 is itself a `[?]`) — it is the
strongest job for P2 and would enter the core the moment the primary persona flips back.
That is the visible cost of the `users.2` gate decision, read straight off the matrix.

## Cut candidates

<!-- features that close no job in the matrix above -->

| Feature | Which job it was assumed to close | Why it closes nothing |
|---|---|---|
| **Campaign / broadcast composer** | Assumed to close a growth job for P1 | No job in this matrix requires it. The brief scopes campaigns as a *secondary* surface, and no persona's evidenced pain touches outbound. It exists in the product; it does not belong in the MVP core |
| **Drag-and-drop flow builder** | The category's default answer to the main job | The main job is closed by an AI answering from the business's own material, not by authoring a decision tree. Keeping a flow builder alongside it rebuilds the competitor's shape — the exact thing COMPETITORS difference 1 identifies as the failure |
| **Per-conversation agent queue as an Administrator destination** | Assumed to close R2 | R2 is closed by *themes*, not items — the `research.4` pattern gate chose clustered themes and disqualified queue triage. A queue serves the Operator, who is not the primary persona |
| **Error-budget / SLO dashboard** | Assumed to close R3 | Explicitly rejected at the benchmark: vendor math for a buyer who left over vendor math. BENCHMARK, *"one that will not work here"* |
| **Sampled QA scorecard** | Assumed to close R2 and R3 | The named *second-choice* pattern, conditional on theme volume that does not exist at P1's scale. Not a cut forever — a cut for now |

> **HUMAN GATE.** The three core jobs and the cut list are a scope decision. Present them and
> stop; the human owns this one.
