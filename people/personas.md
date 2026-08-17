<!-- filled by /dsf:users — started from .design/templates/personas.md, structure unchanged -->

# Personas

**2 to 4 personas**, split by **behavior, not demographics**. If two personas have the same
jobs and the same pains and differ only in age or city, they are one persona — merge them and
say so here.

Personas are a **synthesis of research, not an act of authorship**. Every block below links
back to a specific place in `research/research.md` (a line, a link, or a screenshot path). Where
there is no data: `[?]`, phrased as a hypothesis, never as a fact.

**Exactly one persona is marked primary**, with a stated reason.

Sources below cite the observation ids `R1`–`R8` in `research/research.md` →
**Re-research after personas · Pass 1**, and the named sections of COMPETITORS / BENCHMARK.
**`[?]` count in this file: 12.** They are listed in *What we do not know about people* and
classified in the self-critique table.

---

## Persona 1 — The one who has already failed once  ·  **PRIMARY** / secondary

**Why primary:** chosen by the human at the `users.2` gate (*"1"*), against a recommendation for
Persona 2. The choice follows the evidence rather than the inference: this persona is the only one
the research corpus actually describes — Wati's own reviewers self-report as `2-10 employees` (R1),
and every verbatim quote available comes from this segment. The recommendation for Persona 2 rested
on arithmetic about the −30% criterion, not on a single user statement, and was overruled on that
basis.

**The consequence, recorded so no later phase has to rediscover it.** Making this persona primary
changes *which success criterion drives the design*. The brief's two criteria are **10 minutes of
in-product time to live** and **−30% cost per resolved conversation**. At this persona's volume the
second one is close to meaningless — 30% of a small number is not money, and no reviewer in this
corpus talks about cost per resolved conversation. So:

- **10 minutes to live becomes the dominant criterion**, together with the trust and exit-freedom
  pains that dominate the corpus (R3, R4).
- **−30% cost per resolved conversation becomes a criterion for a secondary persona.** It is not
  wrong, but it now measures value for Persona 2 while the product is shaped around Persona 1.
  `[?]` **unresolved tension, owned by the human.** Options when it matters (phase 3 at the
  latest): re-scope the criterion to Persona 2 explicitly, replace it for Persona 1 with something
  their volume can move, or accept that the product is designed for one persona and measured on
  another. This is a `/dsf:change` against the brief, not a decision this file can make.

- **Context** — a 2–10 person D2C or services business, most often India. They bought a BSP on
  price, set it up themselves in an afternoon with a drag-and-drop builder, shipped a flow, and
  watched it fail to hold a real conversation. They are still answering WhatsApp personally while
  paying ₹1,500–5,000/month plus per-message costs.
  source: R1, R6 (*"targets non-technical operators"*, `"user-friendly setup"` in ~50% of recent
  G2 reviews), R7
- **Jobs** — get the repeat questions answered without them; stop paying for something that does
  not work; be able to leave without a fight.
  source: R3, R5, R7
- **Pains** — the automation is felt to be shallow but they cannot articulate why: *"Sometimes it
  feels limited in automation options and not flexible enough for complex workflows"*. Support
  takes days (*"replies took 2-3 days"*). And the exit is worse than the product: dark patterns on
  the cancellation form, forced annual billing at checkout, charges continuing for months.
  source: R5, R4, R3
- **Trust triggers**
  - Convinces: a number they can check themselves rather than a number they are told. The market
    trained them the other way — six products claim 67–98% resolution and only Intercom publishes
    what counts. `[?]` **hypothesis, not confirmed:** no review in the corpus says "I want to
    verify the number"; this is inferred from the market's need to *guarantee* a rate (Tidio's
    "Guaranteed 50%") rather than merely claim one.
    source: COMPETITORS shared pattern 2; BENCHMARK dimension
  - Scares off: annual lock-in discovered at checkout, and support that disappears at exactly the
    moment they need it. *"support becomes unresponsive once you request cancellation"*;
    *"they claim to offer monthly billing, but in reality, force annual payments once you proceed
    to checkout."*
    source: R3
    **Added at `users.6`, and it is the sharpest evidence in the project:** what actually scares
    this persona off is *"no technical support available and only a chatbot is offered, with no
    human support even after sending emails"*. Their lived experience of AI support is **being
    stonewalled by one**. A product asking them to trust an AI with their own customers is
    arguing against that memory.
    source: Pass 2 · Q3
- **Quote** — verbatim
  *"Sometimes it feels limited in automation options and not flexible enough for complex
  workflows"* — Sulimam A, Design, 2–10 employees
  source: R5 · [Capterra](https://www.capterra.com/p/204314/WATI/reviews/)

## Persona 2 — The one who owns the number  ·  primary / **secondary**

**Why not primary:** proposed as primary and overruled at the `users.2` gate. The argument for it
still stands on its own terms — the brief's −30% criterion only pays out at this persona's volume,
a deflection rate is only worth proving to someone who reports it upward, and 5–10 seats (R1) is
where roles and handover stop being theoretical. What it lacked was evidence: not one verbatim in
the corpus comes from an ops lead describing this job. Secondary, and **the persona the −30%
criterion actually belongs to** — see the consequence recorded under Persona 1.

- **Context** — support or ops lead at a scaling D2C brand, roughly 11–50 people, with 5–10 agent
  seats and WhatsApp volume high enough that cost per conversation is a line item someone asks
  about. `[?]` how they came to own the tool — chose it, inherited it, or were handed it — is not
  in the evidence and is deliberately not asserted.
  source: R1 (Respond.io includes 5–10 users; Interakt Sales CRM 5 agents +₹499 each), R7
- **Jobs** — cut the cost of answering without visibly cutting the quality of answers; keep human
  agents on the conversations that actually need a human; be able to show a founder that the AI is
  working, in terms the founder will accept.
  source: BENCHMARK dimension; R7 (*"less than the cost of a single additional support hire"*)
- **Pains** — they cannot prove the number. The AI they have is a paid add-on bolted onto a
  keyword-flow core (AiSensy ₹2,500 builder vs ₹3,500 AI Agent Builder; Interakt AI Agents
  ₹3,000/mo), so the thing they are measured on is an upsell rather than the product. And the tool
  covers one channel while their customers use several — AiSensy is **WhatsApp-only: no Instagram,
  Messenger, SMS, email or website widget**.
  source: COMPETITORS difference 1, `research/screens/aisensy-pricing-two-skus.png`,
  `research/screens/interakt-pricing-ai-addon.png`, R5
- **Trust triggers**
  - Convinces: seeing *which* conversations the AI resolved and being able to disagree with the
    label. Intercom is the only product that makes the definition contestable — it does not charge
    when the customer asks for a human, and **refunds a resolution if the conversation is
    reopened**.
    source: BENCHMARK dimension, [Fin outcomes](https://www.intercom.com/help/en/articles/8205718-fin-ai-agent-outcomes)
  - Scares off: an AI answering customers unsupervised with no way to have tested it first.
    Nothing in the hard group offers a pre-flight; only the aspirational group does (Ada's
    simulations, Decagon's "Simulations at scale", Sierra's Ghostwriter testing). `[?]`
    **hypothesis:** that this absence is felt as *fear* rather than merely unnoticed is inferred
    from the aspirational group having built it, not from any review in the corpus.
    source: COMPETITORS difference 3; BENCHMARK mechanic 1
- **Quote** — verbatim, and **off-job**: the only review in the corpus from a company of this size
  is about marketing conduct, not about the product's daily use. Kept because it is real and
  labelled because it is not evidence about the workflow.
  *"Despite multiple requests—five, to be exact—to delete my data and stop emailing me, Wati.io
  has continued to flood my inbox with spam."* — Aaron B, Co-founder, Telecommunications,
  51–200 employees
  source: R3 · [Capterra](https://www.capterra.com/p/204314/WATI/reviews/)
  `[?]` **no verbatim exists in this corpus from an ops lead describing the AI-tuning job.** This
  is the single largest evidence gap behind the primary persona.

## Persona 3 — The one who gets called when it breaks  ·  primary / **secondary**

**Why not primary:** they are a dependency, not the buyer. They appear only at the edges of the
evidence — where self-serve stops.

- **Context** — an in-house developer or an implementation partner, pulled in when the no-code
  path runs out. The evidence puts them exactly at that boundary: setup is self-serve by design,
  *"however, advanced integrations (custom APIs, BYOLLM) require technical capability"*, and
  Interakt sells `Advanced [Branching, Logical Flows, API calls]` as the paid step up.
  source: R6, [interakt.shop/pricing](https://www.interakt.shop/pricing/)
- **Jobs** — wire the AI to the systems that hold the real answers (orders, CRM, shipping); hand
  control back to the business team so they stop being the bottleneck.
  source: R6; brief — `Developer` is one of the ten roles
- **Pains** — `[?]` **hypothesis:** they have no way to test a change before it reaches customers,
  and no record of who changed what. Inferred from the market gap (nothing in the hard group has a
  pre-flight or an audit trail, while Stripe Radar's rule-activity log records *"the complete rule
  predicate before and after the update"*), **not** from any developer saying so.
  source: BENCHMARK C4 + C8
- **Trust triggers**
  - Convinces: `[?]` **hypothesis:** an audit trail and a sandbox. source: BENCHMARK C8, C4
  - Scares off: `[?]` **hypothesis:** natural-language configuration they cannot read back or
    diff — the failure mode named in PATTERNS pattern 5, *"they cannot verify what was written"*.
    source: PATTERNS pattern 5
- **Quote** — `[?]` no verbatim from a developer or implementation partner exists in this corpus.
  Would be found in: BSP developer docs forums, r/india_startups or r/ecommerce threads on
  WhatsApp API integration, or Upwork/agency listings describing what clients ask for.

## Merged personas

- **"Indian SMB owner" and "SEA / LatAm SMB owner" were merged** — same jobs, same pains, same
  buying behaviour; they differed only in currency and timezone. Geography changes the support-hours
  complaint (R4 names India-timezone support as the differentiator) but not a single job or pain,
  so it is a property of Persona 1, not a persona of its own.
- **"Campaign Manager" and "Template Manager" were not made personas.** They are roles in the
  brief's ten-role model, not distinct behaviours in the evidence — nothing in the corpus
  describes a person whose whole job is templates. `[?]` if real accounts show a dedicated
  template owner, Persona 2 splits.

---

## What we do not know about people

Specific enough to research in step 6. This list is the input to the targeted re-research, so
"we need to know more about users" is not an entry.

1. **Whether the primary persona can carry the brief's economics.** Resolved one way at the
   `users.2` gate: Persona 1 is primary because it is the persona the evidence describes. What
   remains open is the consequence — at 2–10 person volume, does deflection save enough to be
   bought at all, or is this persona buying *relief* rather than *savings*? **Would be found in:**
   a review or case study naming a conversation volume, or one customer conversation. Until then
   the −30% criterion is aimed at Persona 2 while the design is aimed at Persona 1.
2. **What an Administrator actually does in a week.** No observed behaviour, no session data. Is
   tuning the AI a weekly ritual, a monthly panic, or something nobody ever does?
3. **Why they left the last BSP, in their own words.** The corpus gives billing and support
   complaints (R3, R4) but almost nothing about the AI itself failing — which is what the brief
   claims is the reason. **This gap sits directly under the brief's problem statement.**
4. **Who else is in the buying decision** — founder, agency, developer — and who has veto.
5. **Whether anyone has ever tuned a bot themselves**, or whether it was built once and abandoned.
6. **What they fear when an AI answers customers unsupervised**, in their words rather than
   inferred from what the aspirational vendors built.
7. **Whether the ten roles map to ten people or to one person with ten checkboxes.** R1 suggests
   the latter for Persona 1; unknown for Persona 2.
8. **Whether a pre-flight step is acceptable to an SMB at all**, or whether any friction before
   "it's live" is fatal given the 10-minute criterion.

---

## Self-critique — confirmed / hypothesis / invented

Walk **every statement** in this file and in `people/jtbd.md` and classify it. A clean pass on
the first attempt is suspicious, not impressive: honest personas almost always keep a few `[?]`.

Written at `users.5`; see that section of this file's companion critique for the dangerous subset
and the three targeted questions.

| Statement | Where it lives | confirmed / hypothesis / invented | Source or the gap |
|---|---|---|---|
| Teams in this market are 2–10 people | P1 context | **confirmed** | R1 — reviewer self-reported company sizes + seat counts in three pricing pages |
| The buyer set the BSP up themselves, non-technically | P1 context | **confirmed** | R6 — *"targets non-technical operators"*, `"user-friendly setup"` in ~50% of recent G2 reviews |
| They are "still answering WhatsApp personally" | P1 context | **hypothesis** | Consistent with R5 + R7 but stated by nobody. Would be confirmed by one interview |
| Cancellation and billing are where trust dies | P1 pains | **confirmed** | R3 — four separate verbatim reviews |
| Support takes 2–3 days | P1 pains | **confirmed** | R4 — TrustPilot verbatim, corroborated by a second source |
| P1 wants a number they can check themselves | P1 trust | **hypothesis** | Inferred from Tidio needing to *guarantee* a rate; no reviewer says it |
| −30% only pays at volume, so P2 is primary | P2 primary rationale | **hypothesis (structural), overruled** | Arithmetic on the brief's own criterion, not a user statement. Put to the human at the `users.2` gate and overruled in favour of the evidenced persona. The arithmetic is retained as the reason the −30% criterion now belongs to a secondary persona |
| P2 has 5–10 seats | P2 context | **confirmed** | R1 — three pricing pages price 5–10 seats as the normal team |
| ~~P2 inherited rather than chose the tool~~ | P2 context | **invented — removed** | Nothing supported it. Written in the first draft, flagged at the persona gate, and cut rather than kept with a label. Replaced by an explicit `[?]` |
| P2 cannot prove the number | P2 pains | **confirmed** | COMPETITORS shared pattern 2 — six products claim, one defines |
| The AI is a paid add-on on a keyword-flow core | P2 pains | **confirmed** | Two pricing screenshots |
| AiSensy is WhatsApp-only | P2 pains | **confirmed** | R5 |
| P2 fears unsupervised AI | P2 trust | **hypothesis** | Inferred from what aspirational vendors built, not from a user |
| P3 exists as a distinct behaviour | P3 context | **confirmed (weakly)** | R6 boundary + Interakt's `Advanced` tier + the `Developer` role in the brief. Real, but thin |
| P3's pains and trust triggers | P3 pains, trust | **hypothesis** | Entirely inferred from benchmark gaps. No developer voice in the corpus |
| P3's quote | P3 quote | **absent** | `[?]` — correctly left empty rather than composed |
| Geography does not split the personas | Merged | **hypothesis** | Defensible from R4 but not tested outside India |

### Coverage of `people/jtbd.md`

| Statement | Where it lives | confirmed / hypothesis / invented | Source or the gap |
|---|---|---|---|
| The main job — repeat questions handled without me | jtbd main | **confirmed** | R5, R7, R1 — the whole category is sold against this |
| R1 — see it working within the hour | jtbd related 1 | **confirmed** | R2 (*"15-20 minutes"* to a working FAQ bot), R6 |
| R2 — find out before the customer tells me | jtbd related 2 | **hypothesis (strong)** | The *gap* is confirmed (COMPETITORS pattern 3); that P1 wants it filled is inferred |
| R3 — a number I can defend | jtbd related 3 | **hypothesis for P1, confirmed for P2** | Market evidence is strong; P1's need for it is not evidenced at all |
| R4 — know what a change will do first | jtbd related 4 | **hypothesis** | Inferred from aspirational vendors, not from a user. Scored **1** for P1 |
| R5 — leave without a fight | jtbd related 5 | **confirmed** | R3 — four separate verbatim reviews. Strongest evidence in the corpus |
| E1 — check things myself | jtbd emotional | **hypothesis (strong)** | The trust failures are confirmed; the emotional framing is mine |
| E2 / S1 | jtbd emotional, social | **hypothesis** | Correctly parked as H1 / H2 rather than asserted |
| S2 — look more capable than our headcount | jtbd social | **hypothesis (half-evidenced)** | R7 confirms the cost-vs-hire comparison; the "how we are seen" half is not evidenced |
| 8 `[?]` cells in the matrix | jtbd matrix | **honest gaps** | Left unscored rather than averaged, per the template's own rule |

### The dangerous subset — statements that drive design decisions but rest on `[?]`

Ordered by what they would cost if wrong.

1. **R4 scores 1 for the primary persona.** ~~and that score is a `[?]`~~ — **narrowed at
   `users.6`, not closed.** Pass 2 Q1 finds the constraint is the *time budget*, not the concept:
   the category's own guidance is that setup must stay *"under 30 minutes"* because these buyers
   are *"running a business, not a software project"*. So counterfactual replay survives for P1
   **only if it costs seconds and happens inline** — as a separate screen with its own decision it
   does not. Still open: nobody in the corpus has been observed using a pre-flight at all.
2. **R3 scores 2 for P1, and that 2 is a `[?]`.** That cell alone kept the benchmark dimension's
   own job out of the MVP core. A scope decision is currently resting on a guess with a number
   attached.
3. **Five channels are justified entirely by vendor-side evidence.** **Sized at `users.6`, still
   open.** Pass 2 Q2 confirms WhatsApp (*"78% of SMBs already use WhatsApp for business"*) and
   supports social channels generically (*"80% of consumers use social media to interact with
   brands"*), and tools consolidating WhatsApp + Instagram corroborate that pair. **Email and SMS
   remain unevidenced as inbound channels for this persona** and are carried on the brief's
   authority alone. No source gives a channel-share breakdown for this segment.
4. **"Still answering WhatsApp personally"** (P1 context) is a hypothesis carrying the main job.
5. **E1's emotional framing is mine.** The trust failures are confirmed; "wants to check things
   himself" is my reading of them.

### Three targeted questions for `users.6`

| # | Question | Why it matters | Where the answer is |
|---|---|---|---|
| Q1 | Does a 2–10 person operator tolerate a test/preview step before going live, or is any friction before "it's live" fatal? | Decides whether counterfactual replay is MVP or a secondary-persona feature — dangerous subset 1 | One- and two-star reviews filtered on setup/onboarding; Tidio and AiSensy onboarding teardowns; category guides describing the first-run path |
| Q2 | Is there demand-side evidence that this persona's customers arrive on channels beyond WhatsApp? | The brief commits to five channels; only the vendor side is evidenced — dangerous subset 3 | Reviews mentioning Instagram or email alongside WhatsApp; multi-channel adoption data for Indian SMBs |
| Q3 | Does anyone in this segment describe leaving because the bot or AI failed, rather than because of billing or support? | Sits directly under the brief's problem statement, which phase 2a already had to correct once | One- and two-star G2/Capterra reviews filtered on "bot", "AI", "chatbot" |


---

## What changed after the targeted re-research (`users.6`)

Recorded because a `[?]` dropped without a source is the failure this file exists to prevent.

| What changed | Direction | Evidence |
|---|---|---|
| P1 "scares off" gained its strongest line | **confirmation, added** | Pass 2 Q3 — the buyer's BSP answers support requests with a bot and no human |
| Dangerous item 1 (replay for P1) | **narrowed, not closed** | Pass 2 Q1 — a <30-minute setup budget makes replay viable only if it costs seconds |
| Dangerous item 3 (five channels) | **sized, not closed** | Pass 2 Q2 — WhatsApp confirmed, Instagram supported, **email and SMS unevidenced** |
| The brief's stated reason for switching | **contradicted a second time** | Pass 2 Q3 — nobody in the corpus leaves because the AI answered badly; they leave over absent support, billing traps and a platform that did not work |
| R5 "leave without a fight" and E1 "check things myself" | **strengthened to best-evidenced in the project** | Pass 2 Q3 corroborating R3 |
| MVP core chosen at the `users.4` gate | **validated after the fact** | The gate was taken before Pass 2 existed; Pass 2 supports all three choices |

**Nothing was un-marked without a source.** The two `[?]` that remain in the dangerous subset are
still `[?]`, narrowed rather than resolved.
