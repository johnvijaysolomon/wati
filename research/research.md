<!-- filled by /dsf:research — started from .design/templates/research.md, structure unchanged -->

# Research

Four sections, nothing else: **COMPETITORS · BENCHMARK · PATTERNS · CONCLUSIONS**.
Every factual claim carries a link or a screenshot path from `research/screens/`.
Where no source exists: `[?] unverified` plus the explicit hypothesis. Never round a guess
into a number.

Collected 2026-08-17. Tools: Playwright MCP (`active`) for screenshots, WebFetch/WebSearch for
sources. Six screenshots captured; **every in-product Administrator surface in this market sits
behind a login this project does not have**, so all captures are public marketing or pricing
pages and are labelled `access restricted` where the interesting screen is unreachable.

---

## COMPETITORS

Three groups, **max 5 per group**, **at least 5 products named in total**.
No searching in this list — it is a decision about scope, signed off by the human before any
data is collected.

Set approved at the `research.1` gate, 2026-08-17: *"remove Wati, cut soft group to Intercom,
Tidio, Zendesk"*. Twelve products. Wati's own current product was proposed as a hard comparator
and struck by the human, so this research argues against the market, not against the incumbent
being replaced.

### Hard — same product, same audience, same market

| Product | Why it belongs here | What specifically to learn from it |
|---|---|---|
| **AiSensy** | Named in the brief's seed. Same buyer, same channel, same "AI" claim | Count the steps from signup to first sendable message, and where the AI builder sits relative to the flow builder — the direct test of the 10-minute criterion |
| **Interakt** | Same Indian SMB WhatsApp buyer, Shopify-heavy, same migration-in motion | What the product shows *while* Meta's number and template approval is pending — the state the 10-minute criterion depends on being designed |
| **Gupshup** | Same market, API/CPaaS heritage rather than inbox heritage | Whether "channel" is a first-class object you connect and govern, or a bolt-on per feature |
| **Respond.io** | Closest structural match: omnichannel inbox + automation, mid-market | The role/permission model, and how AI→human handover is configured rather than described |

### Soft — different product, same underlying job

| Product | Why it belongs here | What specifically to learn from it |
|---|---|---|
| **Intercom** | Named in the brief's seed. The most mature AI-deflection product in the market | How Fin's quality is presented to the person tuning it, and what "resolved" is allowed to mean |
| **Tidio** | Self-serve SMB, deflection sold on a resolution-count basis | Their setup path and the only guaranteed resolution floor found in this research |
| **Zendesk** | Enterprise helpdesk retrofitting AI onto a ticket model | How AI config is bolted onto a permission system that predates it — the failure mode to avoid |

### Aspirational — international benchmarks in the category

| Product | Why it belongs here | What specifically to learn from it |
|---|---|---|
| **Sierra** | AI-agent-first by construction, no inbox heritage | How agent behaviour is authored and constrained — the "guardrails" surface the brief names but does not define |
| **Decagon** | Same generation, competing on measurable resolution quality | How AI failures are surfaced for review and turned into a fix — the Administrator's core loop |
| **Ada** | Longest-running AI-first automation product with a real admin console | The knowledge-ingestion surface: what an admin does on day one to make the AI competent |
| **Salesforce Agentforce** | Enterprise-scale answer with a real permission model | How agent permissions and human escalation are modelled when governance is non-negotiable |
| **Forethought** | Deflection-metric-led positioning | How deflection rate is defined and displayed — a definition someone cannot game |

### Comparison matrix

One row per competitor, the five fixed axes as columns. Cells are filled from collected data —
web fetch, product pages, screenshots in `research/screens/` — never from assumption.
A screen behind a login you do not have is captured as far as it is reachable and labelled
`access restricted`.

| Product | Audience | Product core | Key mechanic | Trust | Monetization | Source |
|---|---|---|---|---|---|---|
| **AiSensy** | Indian SMB / D2C on WhatsApp | WhatsApp campaigns + bots | **Drag & drop flow builder**; "WhatsApp AI Agent Builder" is a *separate product* with "Long-term user memory" | Meta BSP status; template approval | ₹2,500/mo builder · **₹3,500/mo AI Agent Builder** (incl. 3,500 AI messages) · marketing ₹1.09/msg, utility ₹0.145/msg from 2026-01-01 | [aisensy.com/pricing](https://aisensy.com/pricing) · `research/screens/aisensy-pricing-two-skus.png` |
| **Interakt** | Indian SMB, Shopify-heavy | WhatsApp commerce + support hub | `Basic [Linear Chatbot]` / `Advanced [Branching, Logical Flows, API calls]`; three named AI agents sold separately | Meta BSP status | Growth ₹2,799/mo · Advanced ₹3,799/mo · **AI Agents ₹3,000/mo add-on**, 100 free messages then ₹0.50/msg · "Unlimited agents (All Roles)" | [interakt.shop/pricing](https://www.interakt.shop/pricing/) · `research/screens/interakt-pricing-ai-addon.png` |
| **Gupshup** | Mid-market/enterprise, emerging markets | CPaaS + agent platform | "Autonomous AI Agents for Sales, Marketing & Customer Support", proprietary "ACE LLM model" | Enterprise scale; named bank logos | `[?] unverified` — no pricing published; `/pricing` returns 302→404. Hypothesis: sales-led, volume-committed. Confirmed by a quote or an analyst source | [gupshup.ai](https://www.gupshup.ai/) |
| **Respond.io** | Mid-market omnichannel sales + support | Omnichannel inbox + workflows | Workflows + "AI Agents", metered in **AI Credits** | SSO; explicit per-tier user counts | $79 / $159 / $279 per mo · 5–10 users incl., extra $12–24/user · AI **included** Growth+, 5k–40k credits, overage $15/1,000 capped at 200% | [respond.io/pricing](https://respond.io/pricing) · `research/screens/respondio-pricing-ai-credits.png` |
| **Intercom** | Product-led SaaS support teams | AI-first support platform | Fin answers from knowledge; **outcome is contractually defined** | **Published resolution definition + refund on reopen** | $29 / $85 / $132 per seat/mo, Fin included in all · **$0.99 per outcome** | [intercom.com/pricing](https://www.intercom.com/pricing) · `research/screens/intercom-pricing-fin-outcome.png` |
| **Tidio** | SMB ecommerce | Live chat + Lyro AI | Lyro conversations, quota-metered | **"Guaranteed 50% Lyro AI resolution rate"** (Premium) — the only floor found | Free · $24.17 · from $49.17 · from $300/mo + usage · Lyro quotas from $32.50/mo | [tidio.com/pricing](https://www.tidio.com/pricing/) |
| **Zendesk** | Enterprise service teams | Ticketing + AI agents | Automated resolution layered over a ticket model | Enterprise compliance posture | $19 / $55 / $115 per agent/mo · AI agents included, billed **"per automated resolution… without any escalation to a human agent"** | [zendesk.com/pricing](https://www.zendesk.com/pricing/) |
| **Sierra** | Enterprise CX | AI agent platform | **Ghostwriter** agent authoring; "built-in guardrails"; ingests "SOPs, transcripts, whiteboard photos, and audio recordings" | "Monitors" flag problematic interactions proactively; "Explorer" conversation analysis | "Outcome-based pricing" — *"Pay for a job well done"*; no rate card published | [sierra.ai](https://sierra.ai/) |
| **Decagon** | Enterprise CX | AI concierge | **Natural-language "Agent Operating Procedures (AOPs)"** | **"Watchtower" — "Always on QA"**; "Testing & QA — Simulations at scale" | `[?] unverified` — not published. Hypothesis: outcome- or volume-based, sales-led | [decagon.ai](https://decagon.ai/) · `research/screens/decagon-aop-watchtower.png` |
| **Ada** | Enterprise CX | AI agent platform | **Playbooks** ("automate your complex SOPs") + **Coaching** ("feedback loop… automatically applied to future interactions") | **Simulations** — "test changes safely before they go live" | `[?] unverified` — not published | [ada.cx/platform](https://www.ada.cx/platform/) · `research/screens/ada-coaching-simulations.png` |
| **Forethought** | Mid-market / enterprise support | AI agents over an existing helpdesk | **Discover Agent** — "AI Surfaced Insights", "detect knowledge gaps", "Fix gaps before they become problems" | `[?] unverified` — no trust mechanism stated on the page | `[?] unverified` — not published | [forethought.ai](https://forethought.ai/) |
| **Salesforce Agentforce** | Enterprise | Agent platform | `[?] unverified` | `[?] unverified` | `[?] unverified` | **`access restricted`** — salesforce.com returned HTTP 403 on both `/agentforce/` and `/agentforce/pricing/`. Not filled from memory. Hypothesis: Flex-Credit consumption pricing. Confirmed by fetching from a non-blocked network or a partner page |

<!-- every "evidence" below is a screenshot path or a link, never a summary of general
     impressions; a shared pattern is worth listing only if you can point at two products
     doing it -->

**Three shared market patterns** — what everyone does the same way:

1. **The billable unit has moved from the seat to the resolution.** — evidence: Intercom
   *"priced at $0.99 per outcome"* ([source](https://www.intercom.com/pricing)); Zendesk
   *"Paying per automated resolution means that you pay only for customer requests that were
   successfully resolved by the AI agent"* ([source](https://www.zendesk.com/pricing/)); Sierra
   *"outcome-based pricing"* ([source](https://sierra.ai/)). Seats still exist, but they are no
   longer where value is counted.
2. **Everyone publishes a rate; almost nobody publishes a method.** — evidence: Tidio *"up to
   67%"* and a *"Guaranteed 50%"* floor ([source](https://www.tidio.com/pricing/)); Zendesk
   *"Resolve up to 80%+"*; Ada *"over 80%"* and *"84%"*
   ([source](https://www.ada.cx/platform/)); Forethought *"Up to 98% Resolution rate"*
   ([source](https://forethought.ai/)); Decagon customer figures *"70% chat and voice
   resolution"* (Chime) and *"80% deflection rate"* (Duolingo)
   ([source](https://decagon.ai/)). **Intercom is the only one that defines what counts** —
   because it bills on it.
3. **The improvement loop is named in the aspirational group and nameless in the hard group.** —
   evidence: Ada's *Coaching* and *Simulations*, Decagon's *Watchtower* and *Testing & QA*,
   Sierra's *Monitors* and *Explorer*, Forethought's *Discover Agent*. Against that, AiSensy and
   Interakt ship a flow builder and **no vocabulary at all** for "the AI got it wrong, now what"
   — `research/screens/aisensy-pricing-two-skus.png`,
   `research/screens/interakt-pricing-ai-addon.png`.

**Three real differences** — where they genuinely diverge:

1. **In the WhatsApp BSP group the AI is a second SKU bolted onto a flow-builder core; in the
   soft and aspirational groups the AI *is* the product.** — evidence: AiSensy sells a
   *"Drag & Drop WhatsApp Chatbot Builder"* at ₹2,500/mo and a separate *"WhatsApp AI Agent
   Builder"* at ₹3,500/mo ([source](https://aisensy.com/pricing)); Interakt's plans list
   `Basic [Linear Chatbot]` / `Advanced [Branching, Logical Flows, API calls]` with AI Agents a
   ₹3,000/mo add-on ([source](https://www.interakt.shop/pricing/)). Intercom, Zendesk and
   Respond.io all include AI in the base plan.
   **This is the brief's load-bearing `[?]`, and it resolves with a correction:** the incumbents
   *do* have AI agents in 2026. What is fake is not the AI's existence — it is that AI is an
   upsell sitting on top of a keyword-flow product, so the default experience a buyer has
   already paid for is still a decision tree.
2. **Only one product sells a floor rather than a ceiling.** — evidence: Tidio's *"Guaranteed 50%
   Lyro AI resolution rate"* on Premium ([source](https://www.tidio.com/pricing/)) against
   "up to 80%+" (Zendesk), "up to 98%" (Forethought), "over 80%" (Ada). A guarantee is a
   different product promise and needs a different surface to back it.
3. **Only the aspirational group lets you test before customers do.** — evidence: Ada's
   simulations *"test changes safely before they go live"*; Decagon's *"Simulations at scale"*;
   Sierra's Ghostwriter *"includes automated testing during creation"*. Nothing in the hard
   group offers any way to try an agent before a real person meets it.

**Three open questions** only the product owner can answer:

1. **What is the current blended cost per resolved conversation?** The −30% success criterion
   has no baseline without it, and no public source can supply one.
2. **Does Wati intend to price by outcome?** If yes, the Administrator's world changes shape:
   they must be able to see what was billed, why, and contest it — a surface no competitor in
   the hard group has.
3. **How many real accounts use more than Administrator + Operator?** Ten roles were given at the
   brief gate; research cannot tell which are load-bearing and which are theoretical.

---

## BENCHMARK

One dimension, studied **across categories**. The matrix surfaces it — the axis where every
competitor is weak, or where the whole market converges. The human confirms or substitutes the
dimension before scoring starts.

**Dimension:** **Proving the AI works** — how a product defines a resolution, measures it, shows
the Administrator what the AI got wrong, and turns that into a fix. Confirmed at the `research.3`
gate, 2026-08-17 (*"confirmed"*); *time-to-live* was offered as the alternative and declined.

**Why this one (evidence from the matrix):** six products claim 67–98% resolution and exactly one
publishes the method. Intercom counts a **confirmed** resolution (the customer says it helped) or
an **assumed** one (the customer disengages for 24 hours without asking for more), does not charge
when the customer asks for a human or a configured Procedure fails, and **refunds the resolution
if the conversation is reopened**
([Fin AI Agent outcomes](https://www.intercom.com/help/en/articles/8205718-fin-ai-agent-outcomes)
— surfaced via search; the direct fetch of a neighbouring help article returned 404, so this is
sourced from the search-returned article rather than a page render).
Against that published definition, independent analysis puts Fin's production resolution rate at
**45–53%** ([CloneDesk](https://clonedesk.ai/blog/intercom-fin-limitations)) — `[?]` vendor-adjacent
source, treat as directional not authoritative. The gap between the claimed number and the real
one *is* the design problem. It also sits directly under both of the brief's success criteria:
if the product cannot prove them in its own UI, they are marketing rather than criteria. And the
buyer is arriving precisely because the last vendor's numbers did not survive contact.

### Criteria — 6 to 8, each scored 1–5

Each criterion is written so two people would score it the same way. "Feels trustworthy" is not
a criterion; "the seller's identity is verified before the first message" is.

| # | Criterion | What a 1 looks like | What a 5 looks like |
|---|---|---|---|
| 1 | Success is defined publicly and exactly | No success metric is named | The calculation is stated, including what does **not** count and what is reversed |
| 2 | Individual failures are enumerable | Aggregate charts only | Every failure is listed and openable; if the list is capped, the cap is disclosed |
| 3 | Cause is visible at the failure | No reason given | Full reason or trace shown inline on the item itself |
| 4 | Testable before it affects anyone | No preview of any kind | The change is replayed against **real historical data** and the predicted impact is diffed |
| 5 | Fix is authored where the failure is seen | Read-only view; fixing happens elsewhere entirely | The fix is created in place and stays linked to the failure that prompted it |
| 6 | Regression is detected automatically | Nothing notices when a fixed thing breaks again | The item changes state on its own and the system notifies |
| 7 | The system verifies the fix | No verification; you assume | An explicit validate flow with named states and a verdict |
| 8 | Change history is attributable | No record of who changed what | Who / what / when with before-and-after, and change markers on the performance chart |

### Scoring — 4 to 5 products, from any category

Crossing categories is the point: the best solution to this dimension is usually not in this
market. **At least two of the scored products must come from outside the product's own
category.**

**All five are from outside customer service.** A `[?]` cell is *unsourced*, not zero: it is
excluded from both the numerator and the denominator, so each product reports as
`score / scoreable`. Ranks with fewer than 8 scored criteria are provisional and say so.

| Product | Category | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | Total | Source |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LangSmith** | LLM app evaluation / dev tooling | 4 | 5 | 5 | 5 | 3 | 4 | 4 | 4 | **34/40** | [evaluation concepts](https://docs.langchain.com/langsmith/evaluation-concepts) · [audit logs](https://docs.langchain.com/langsmith/audit-logs) |
| **Stripe Radar** | Payments fraud ML | 3 | 5 | 4 | 5 | 4 | 2 | 3 | 5 | **31/40** | [Radar rules](https://docs.stripe.com/radar/rules) |
| **Sentry** | Software error monitoring | 2 | 5 | `[?]` | 1 | 2 | 5 | 4 | 4 | **23/35** *(7 scored)* | [issue states & triage](https://docs.sentry.io/product/issues/states-triage/) |
| **Google Search Console** | Search indexing diagnostics | 4 | 4 | 4 | 1 | 1 | 3 | 5 | 1 | **23/40** | [Page Indexing report](https://support.google.com/webmasters/answer/7440203) |
| **Datadog SLOs** | Infrastructure observability | 5 | 2 | `[?]` | `[?]` | `[?]` | 5 | 3 | `[?]` | **15/20** *(4 scored — provisional)* | [SLOs](https://docs.datadoghq.com/service_management/service_level_objectives/) · [burn rate alerts](https://docs.datadoghq.com/service_management/service_level_objectives/burn_rate/) |

Notes on individual scores, so they can be argued with:

- **Sentry C3** is almost certainly a 5 — stack traces are shown inline — but the page fetched
  covers triage only and did not state it, so it stays `[?]` rather than being scored from
  general knowledge.
- **Datadog C1 = 5** on a published formula: an SLO is *"a target percentage for an SLI over a
  specific period of time"* over rolling 7/30/90 days, and
  `error budget remaining = 100 * (current status - target) / (100 - target)`. It loses nothing
  for the fact that *what counts as a good event* is delegated to the monitor config — but see
  the disqualification below, because that delegation is the whole problem.
- **Radar C8 = 5**: the *Rule activity* log records *"when a rule was created, edited, enabled or
  disabled, and by which user on your team"* with *"the complete rule predicate before and after
  the update"* (180 days), and rule changes appear as *"triangular symbols on the graph lines"*
  so a change can be compared before and after.
- **The two highest scorers are both "evaluate an automated decision-maker" products** — one for
  LLM apps, one for fraud ML. Neither is a support tool. This is the strongest evidence that the
  dimension is unsolved inside this category.

**Three mechanics worth carrying into the MVP:**

1. **Backtest before enable** — from **Stripe Radar** and **LangSmith**, because a change to an
   AI's behaviour is a bet on conversations that have not happened yet, and both products turn
   that bet into evidence first. Radar *"runs a simulation on the last 6 months of charges to
   determine how many legitimate, fraudulent and blocked payments would have been affected by the
   rule, had it been implemented"*; LangSmith runs experiments over a dataset and supports
   *"comparing multiple experiments side-by-side"*. **Applied here:** before an Administrator
   changes a guardrail, a knowledge item or a handover rule, replay it against the last N real
   conversations and show which answers would have changed.
2. **Validate-fix with named states** — from **Google Search Console**, because it moves the
   burden of proof from the user to the product. `Validate fix` runs through
   `Not started → Started → Looking good → Passed / Failed`, with per-URL states
   `Pending / Passed / Failed / Other`. **Applied here:** when the Administrator fixes a failure
   theme, the product watches subsequent real conversations and returns a verdict, instead of
   leaving the loop open the way every product in the hard group does.
3. **Automatic regression** — from **Sentry** and **Datadog**, because the expensive failure is
   the one that comes back quietly. Sentry: *"If the same issue comes back in a newer release
   than the one you resolved it in, its status will automatically change to 'Regressed'."*
   Datadog adds burn-rate alerts that *"notify you when the rate of consumption of your SLO error
   budget has exceeded your specified threshold"*. **Applied here:** a theme the AI used to handle
   starts failing again → it changes state and says so.

**One that will not work here:** **Datadog's error-budget / SLO abstraction** — because it needs
an organisation that treats a percentage as a contract and an operator fluent in *"a burn rate is
a unitless value [coined by Google]"*. This Administrator is switching BSPs precisely because the
last vendor's numbers were marketing; a second layer of vendor math is the same failure in a
better chart. Worse, Datadog's own documentation delegates what counts as a "good event" to the
underlying monitor configuration — the exact ambiguity that makes the market's 67–98% claims
meaningless. **Keep the alerting (mechanic 3); drop the budget.**

---

## PATTERNS

**The key interaction problem of this product, in one sentence** (derived from the brief, not
invented): *How does an Administrator find what the AI got wrong, decide it matters, and change
the AI so it stops — without reading every conversation?*

**Five principled patterns — not five variations of one approach.** Two patterns that differ
only in layout are one pattern. These five differ in **mechanism**: item-by-item, grouped-by-cause,
statistical sample, counterfactual replay, natural-language authoring.

| # | Pattern | How it works | Where it is used in the wild | When it fits | When it breaks |
|---|---|---|---|---|---|
| 1 | **Queue triage** | Every failure becomes a work item with a state; the human works the queue toward zero | Sentry issues; Stripe's review queue; every helpdesk | Failure volume is bounded and each item is individually actionable | Volume is high — the queue becomes wallpaper and the badge is ignored within a week |
| 2 | **Clustered themes** | Failures are grouped by cause; the unit of work is the theme, never the conversation | Search Console's `Why pages aren't indexed`; Sentry issue grouping; Forethought's Discover Agent | Failures repeat and one fix serves a whole theme | Clustering is wrong — one bad group destroys trust in every group, and true singletons hide in the tail |
| 3 | **Sampled audit** | A sample is scored against a rubric; quality is inferred rather than enumerated | Decagon's "Watchtower — Always on QA"; call-centre QA; LangSmith evaluators over datasets | You need a defensible number more than you need every failure | Someone wants *this* angry customer fixed — sampling structurally cannot find them |
| 4 | **Counterfactual replay** | A change is evaluated against real past conversations before going live; the artifact is a diff of outcomes | Radar's 6-month rule simulation; LangSmith experiments; Ada's simulations | Changes are risky and history exists | There is no history — day one, which is exactly where the 10-minute criterion lives |
| 5 | **Natural-language authoring** | The operator states policy in words; the system writes the rule or procedure | Decagon's natural-language AOPs; Radar Assistant; Sierra's Ghostwriter | The operator is non-technical and the policy space is open-ended | They cannot verify what was written — a legible config UI is swapped for an opaque one |

- **Chosen:** **2 · Clustered themes** (gate `research.4`, *"2"*), with **4 · Counterfactual
  replay** as the action taken from a cluster — three reasons grounded in `CLAUDE.md`:
  1. **The Administrator is not the Operator.** The brief makes the inbox *"an exception surface,
     not the workspace"* and gives conversation-handling to the Operator. Pattern 1 hands Operator
     work to the Administrator and quietly rebuilds the shared inbox the brief rejects.
  2. **Five channels.** A per-item queue multiplies by channel; a theme is channel-agnostic, so
     "refund policy" surfaces once across WhatsApp, Instagram and email — which is the brief's
     *connect / configure / monitor / govern* framing rather than five parallel inboxes.
  3. **Success is a rate, and rates do not move item by item.** −30% cost per resolved
     conversation can only shift through fixes that change many future conversations. Clustering
     makes the unit of work the same size as the unit of measurement.
- **Second choice, under this condition:** **3 · Sampled audit** — if real accounts produce so
  much volume that even clustering yields hundreds of themes, the job shifts from fixing the tail
  to proving the number, and a scored sample becomes the honest surface.
- **Disqualified:** **1 · Queue triage** — because it is the incumbent's shape, it contradicts the
  brief's own line about the inbox, and it fails benchmark criterion C5: you can close items
  forever without the system ever getting better.

`[?]` **Open on the chosen pattern.** The gate answer was the single character `"2"` against a
recommendation that bundled 2 with 4. The pairing is carried forward as the recorded reading;
hypothesis: the human intended the recommendation as stated. Confirmed by the human before
`/dsf:ia`, since replay is a large build commitment that shapes the main screen.

---

## CONCLUSIONS

One entry per gap: the hypothesis, and the section above it follows from.

| Gap | Hypothesis | Follows from |
|---|---|---|
| No BSP publishes how resolution is counted | A published, conservative definition — including what does **not** count and what is reversed on reopen — is itself a differentiator for a buyer who has been burned once | COMPETITORS, shared pattern 2; BENCHMARK dimension |
| The market sells ceilings ("up to 80%"), not floors | The Administrator will not believe a ceiling from a second vendor; showing a *measured* rate for their own account beats any claimed rate | COMPETITORS, difference 2 |
| Nothing in the hard group can test a change before customers meet it | Counterfactual replay against the account's own history is the single highest-value unbuilt mechanic in this market | BENCHMARK, mechanic 1; PATTERNS, pattern 4 |
| The improvement loop has no name in the hard group | Naming the loop — theme → fix → validate → regression watch — is a product surface, not vocabulary | COMPETITORS, shared pattern 3; BENCHMARK mechanics 2 and 3 |
| The brief's problem statement said the incumbents' AI is fake | Partly wrong as stated, and the correction is sharper: the AI exists but is an upsell on a keyword-flow core, so the buyer's *paid default* is still a decision tree | COMPETITORS, difference 1 |
| No baseline exists for the −30% criterion | Only the product owner can supply it; until then the criterion is directionally right and numerically unverifiable | COMPETITORS, open question 1 |

**Numbered hypotheses for later phases to test:**

1. **An Administrator will trust a lower number that is defined over a higher number that is
   claimed.** Test in phase 2b with personas and in phase 4 by showing a measured deflection rate
   with its definition attached, rather than a headline percentage.
2. **The theme, not the conversation, is the right unit of work for this persona.** Test in
   phase 3: if the sitemap needs a per-conversation queue as a primary destination for the
   Administrator, the pattern choice was wrong.
3. **Replay before enable is worth its build cost to an SMB Administrator, not just an
   enterprise one.** Test in phase 2b — if the persona has no tolerance for a pre-flight step at
   all, mechanic 1 becomes a phase-2 aspiration rather than an MVP surface.
4. **The 10-minute criterion and counterfactual replay are in tension on day one.** A new account
   has no history to replay against. Test in phase 3/4: the first-run path may need a different
   proof mechanism (synthetic conversations, or a borrowed baseline) from the steady-state one.
5. **Naming the loop is what makes the product legible as "not another WhatsApp API SaaS".** Test
   in phase 5 (voice) — if the loop's vocabulary sounds like an observability tool, the brief's
   anti-goal has been missed in the other direction.

---

## Re-research after personas

Appended by `/dsf:users`. **Written in two passes, and the order is recorded because it deviates
from the command.** Pass 1 (`users.1`, below) was pulled forward *before* the persona gate: the
COMPETITORS section above is product evidence — pricing pages, docs, marketing — and contains no
review, forum post or interview. Building personas on it would have produced four blocks of
`[?]` including the quotes, and a persona gate with nothing in it to judge. Pass 2 is appended at
`users.6` after the self-critique, as the command intends.

### Pass 1 — customer voice, collected before the persona gate

**R1 · Team size is small, and the reviews say so directly.** Wati's Capterra reviewers self-report
as `2-10 employees` and `51-200 employees`; the design-role reviewer quoted at R5 is a 2–10-person
company. Pricing corroborates: Respond.io includes 5 users (Starter) and 10 (Growth), Interakt's
Sales CRM includes 5 agents at +₹499 each.
Source: [Wati reviews, Capterra](https://www.capterra.com/p/204314/WATI/reviews/) ·
[respond.io/pricing](https://respond.io/pricing) · [interakt.shop/pricing](https://www.interakt.shop/pricing/)

**R2 · The "10 minutes" claim is a vendor claim, and the tested reality is a staircase.** AiSensy
advertises *"10-minute API approval"*; the tested sequence is API activation ~10 min → display-name
verification **3–4 hours** → template approval **24–48 hours**, and *"users waiting for the complete
stack should expect 1-2 business days minimum"*. Separately, *"time from signup to working bot:
15-20 minutes"* for a basic FAQ bot.
Source: [AiSensy review, Chatbotscape](https://chatbotscape.com/reviews/aisensy-review)
**Bearing on the brief:** this supports the reading recorded at the phase-1 gate — 10 minutes of
*in-product* time with Meta's external wait excluded — and contradicts the looser reading that the
whole path takes hours. `[?]` single third-party source; a second would strengthen it.

**R3 · Billing and cancellation are where trust actually dies in this category.** Verbatim from Wati's
own Capterra page: *"support becomes unresponsive once you request cancellation"* (Nicholas S, CEO,
2–10 employees); *"The process is confusing and filled with unnecessary friction...the chatbot and
documentation use dark patterns that make it hard to find the actual cancellation form."* (Verified
Reviewer, CEO); *"they claim to offer monthly billing, but in reality, force annual payments once you
proceed to checkout."* (Tarek Mohamad Al Haddad T, Manager); *"I have been trying to cancel my
membership for three months now...Despite this, they continue to charge me every month."* (Zaid A,
Account Manager).
Source: [Wati reviews, Capterra](https://www.capterra.com/p/204314/WATI/reviews/)
**Scope note:** the human struck Wati from the competitor set at the `research.1` gate, so these are
**not** used as competitor evidence. They are used as *customer voice for this category's buyer* —
the richest available, because this buyer has been writing about this exact product. Flagged for the
human to strike if that reading is unwanted.

**R4 · Support latency is a recurring, cross-vendor complaint, worst for India-timezone teams.**
AiSensy TrustPilot: *"replies took 2-3 days"*. Third-party comparison reports Wati and Interakt's
email-only support as *"a material weakness for India-based teams"*, while AiSensy's 5-star cluster
praises Indian-timezone support.
Source: [Chatbotscape](https://chatbotscape.com/reviews/aisensy-review) ·
[CompareBizTech](https://www.comparebiztech.com/wati-vs-aisensy-vs-interakt/) · `[?]` both are
affiliate-shaped comparison sites; directional, not authoritative.

**R5 · Automation limits are felt, but described vaguely by the people who feel them.**
*"Sometimes it feels limited in automation options and not flexible enough for complex workflows"*
(Sulimam A, Design, 2–10 employees). AiSensy's stated constraints are concrete: **WhatsApp-only —
no Instagram, Messenger, SMS, email or website widget** — and **English-only AI Agent responses**
("multilingual response generation is coming soon").
Source: [Wati reviews, Capterra](https://www.capterra.com/p/204314/WATI/reviews/) ·
[Chatbotscape](https://chatbotscape.com/reviews/aisensy-review)
**Bearing on the brief:** the brief's five-channel scope is a real differentiator against the
hard group, not a checkbox.

**R6 · Setup is self-serve by design; developers appear only at the edges.** AiSensy *"targets
non-technical operators"* with a drag-and-drop builder, and *"user-friendly setup"* appears in
roughly 50% of recent G2 reviews; *"however, advanced integrations (custom APIs, BYOLLM) require
technical capability."* Interakt sells `Advanced [Branching, Logical Flows, API calls]` as the step
up.
Source: [Chatbotscape](https://chatbotscape.com/reviews/aisensy-review) ·
[interakt.shop/pricing](https://www.interakt.shop/pricing/)

**R7 · The economic frame the buyer already uses.** Indian SMBs spend roughly **₹1,500–5,000/month**
in platform fees plus message volume, and a basic chatbot is positioned as *"less than the cost of a
single additional support hire"*.
Source: [SpringEdge / category guides, via search](https://www.springedge.com/best-whatsapp-business-api-providers-india)
· `[?]` vendor-adjacent content marketing; treat the range as directional. A hard baseline for the
brief's −30% criterion still does not exist and remains owner-only.

**R8 · A platform constraint the brief said did not exist.** Effective **15 January 2026**, Meta bars
"AI Providers" from using the WhatsApp Business Solution to distribute general-purpose AI assistants
where such technology is *"the primary (rather than incidental or ancillary) functionality"* —
aimed at OpenAI, Perplexity, Luzia, Poke. Meta stated explicitly that *"this move doesn't affect
businesses that are using AI to serve customers on WhatsApp. For instance, a travel company running
a bot for customer service won't be barred."*
Source: [TechCrunch, 2025-10-18](https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform/)
**Bearing on the brief:** the brief records "no legal or regional fence stated". One now exists
nearby. On this evidence it does **not** bar Wati's use case — Wati equips businesses to serve their
own customers, which is the carve-out Meta named. It is recorded as a constraint to design *with*,
not around: an AI-first WhatsApp product should be able to show that its agent acts for the business
that owns the number. `[?]` residual risk unquantified — how Meta polices "primary functionality"
for a platform whose pitch is "the AI resolves the conversation" is not knowable from the article.

### Pass 2 — the three questions from the self-critique

Run at `users.6` against the dangerous subset in `people/personas.md`. Answers are **partial and
say so**; one came back as a useful negative.

**Q1 · Does a 2–10 person operator tolerate a test step before going live?**
**Partial — and it reframes the question from *whether* to *how much*.** The category's own
guidance is that *"setup time should be under 30 minutes"* because *"small business owners are
running a business, not a software project, and platforms requiring days of configuration are not
designed for them"*; separately, *"89% of customers face friction during onboarding, and 13% will
switch to a competitor after just one bad experience"*.
Source: [Conferbot](https://www.conferbot.com/blog/chatbot-builder-for-small-business) ·
[Wonderchat](https://wonderchat.io/blog/ai-user-onboarding-2026) · `[?]` both are vendor content
marketing; directional, and neither observes this persona directly.
**Effect on the design:** counterfactual replay is not disqualified for P1 — the constraint is the
**time budget**, not the concept. A replay that costs seconds and happens inline survives; a
replay that is its own ceremony, its own screen and its own decision does not. Dangerous-subset
item 1 narrows from "is this the wrong persona for replay?" to "replay must cost seconds". It does
**not** close: nobody in the corpus has been observed using a pre-flight.

**Q2 · Is there demand-side evidence for channels beyond WhatsApp?**
**Partial, and weaker than the brief assumes.** WhatsApp's dominance in this segment is
well-evidenced — *"78% of SMBs already use WhatsApp for business"* in India and *"98% open rates
versus 22% for email"*. For other channels the evidence is generic rather than segment-specific:
*"67% of customers find contacting customer support on social media convenient"* and *"80% of
consumers use social media to interact with brands"*. Tooling corroborates demand indirectly —
several products consolidate WhatsApp and Instagram inboxes specifically.
Source: [IAMAI Digital India 2026, via Indujitechnologies](https://www.indujitechnologies.com/blog/whatsapp-marketing-indian-smbs)
· [Kayako](https://kayako.com/blog/social-media-customer-service-statistics/) ·
[Spurnow](https://www.spurnow.com/en/blogs/shared-inbox-software)
**Effect on the design:** `[?]` **remains open and is now sized.** No source gives a channel-share
breakdown of inbound volume for this persona. WhatsApp + Instagram is defensible on evidence;
**email and SMS are not evidenced as inbound channels for this persona at all** and are carried on
the brief's authority alone. Dangerous-subset item 3 stands.

**Q3 · Does anyone describe leaving because the bot or AI failed?**
**Answered, and the answer is no — which is the most consequential finding of this pass.**
Searching one- and two-star reviews of Wati, AiSensy and Interakt for AI or chatbot failure
surfaces complaints about something else entirely: the platform *"was not working at all"* and a
contact list that would not upload while credits were consumed; implementation *"entirely left to
them with no support available when questions arose"*; a promised Relationship Manager who never
appeared; *"paid over $150 but the software never worked"* with a refund refused. Not one review
in the corpus describes the AI giving wrong answers.
Source: [Wati reviews, Capterra](https://www.capterra.com/p/204314/WATI/reviews/) ·
[AiSensy, Trustpilot](https://ca.trustpilot.com/review/aisensy.com) ·
[SaaSHub AiSensy status](https://www.saashub.com/aisensy-status)
**The sharpest single quote in the whole research** — a reviewer complaining that their BSP offers
*"no technical support available and only a chatbot is offered, with no human support even after
sending emails"*. The buyer's lived experience of AI support is **being stonewalled by one**. Any
product that asks this person to trust an AI with their own customers is arguing against that
memory.
**Effect on the brief:** phase 2a already corrected the problem statement once (the AI exists; it
is an upsell on a keyword core). Pass 2 pushes further in the same direction: **in this corpus,
nobody leaves because the AI answered badly. They leave because support did not answer at all,
because billing trapped them, and because the platform did not work.** The brief's stated reason
for switching is not the reason the evidence records. This is now a **two-finding contradiction**
against a signed-off artifact and belongs in `/dsf:change`, not in a patch here.
**Effect on the jobs:** R5 ("leave without a fight") and E1 ("check things myself") move from
well-evidenced to **the best-evidenced claims in the project**, and the MVP core selected at the
`users.4` gate is validated by a source the gate did not yet have.
