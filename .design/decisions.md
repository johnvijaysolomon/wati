# Decisions

The project's decision log. Every human gate answer, every "keep it", every spec contradiction
resolved under constitution rule 12, and every change request lands here as one entry.

**Append-only.** Newest entry at the bottom. Nothing is edited after the fact and nothing is
deleted — a decision that was later reversed stays, and the reversal is a new entry that names
it. The log is the project's memory of *why*; rewriting it is how a repo starts lying about
itself.

**Written by** any `/dsf:*` command at its gates, and by the rule-12 guard whenever a request
contradicts something written. **Read by** `/dsf:status` (what has been decided so far) and
`/dsf:change` (whether this request has already been settled once).

## Entry format

One heading plus four fields per entry, nothing else:

```md
## YYYY-MM-DD · <trigger>

**Decided:** what was decided — the human's own words, verbatim, wherever they said it.
**Contradicts:** `file:line` + the line quoted — or `nothing`.
**Option:** spec-update | exception | withdrawn | n/a
**Propagated:** every file touched as a result — or `none`.
```

- **trigger** is one of: `gate` (a mandatory gate answer), `keep-it` (an experiment promoted to
  a rule), `contradiction` (the rule-12 guard fired), `change-request` (`/dsf:change`).
- **Option** is `n/a` for a plain gate answer that contradicted nothing.
- **Verbatim matters.** "Warmer, less corporate — like the second one" is a decision. "The human
  approved the palette direction" is a summary of one, and summaries are what drift is made of.
- Keep an entry to five lines. If the reasoning needs more, it belongs in the artifact; link it.

---

## 2026-08-17 · gate

**Decided:** "Product is Wati - An agentic customer engagement platform, Yes to all phase 0
gatgees.. Icons, let's go with solar" — answering the phase-0 toolbox and hosting gate: install
Playwright, leave `impeccable` and `superpowers` on fallback, Solar icons, local hosting.
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** `.design/memory/toolbox.md` (all seven Status rows, Rules for later phases,
Notes), `.mcp.json` (Playwright added), `CLAUDE.md` (Toolbox section), `index.html`
(`context.toolbox`, product name), `README.md`, `.design/progress/phase-0.md`.

## 2026-08-17 · gate

**Decided:** "let's start it as a greenfield project built on our primary hex 23a455" — the
brand green `#23A455` is recorded now, at phase 0, as an input the visual phases inherit.
Parked, not applied: no palette, ramp, token or role has been derived from it, and nothing in
the repo renders it yet. Colour is phase 5–6 work (constitution rule 13), so this is option (b)
— written where its phase will read it — rather than out-of-order execution.
**Contradicts:** `nothing` — no visual spec exists yet to contradict.
**Option:** n/a
**Propagated:** this log only. `/dsf:concept` (phase 5) must open by asking whether `#23A455` is
a hard lock or a starting point, and `/dsf:build` (phase 6) derives the ramp and the semantic
colour roles from whatever that answer is. Same green as the existing HDS 2.0 system, so a
divergence here is a decision, not an accident.

## 2026-08-17 · gate

**Decided:** re-run of `/dsf:init` — "impeccable skill, obra/superpowers" installed, "Keep Solar"
for icons, "GitHub + Pages" for hosting, repo `wati` "private". Reverses the 08:18 answer that
left `impeccable`, `superpowers` and hosting on fallback; the reversal is on new evidence, not a
change of mind — Homebrew is on this machine, so the "no `gh`" blocker recorded at 08:21 was never
real.
**Contradicts:** `.design/decisions.md` 08:18 gate — "leave `impeccable` and `superpowers` on
fallback, local hosting". Superseded deliberately at a re-run of the same gate, which is the one
sanctioned place to change a toolbox row.
**Option:** (1) update the spec — `toolbox.md` is the spec for tools, and it was rewritten.
**Propagated:** `.design/memory/toolbox.md` (3 rows fallback→active, Rules and Notes rewritten),
`CLAUDE.md` (Toolbox section), `README.md` (Pages URL, public-repo warning), `index.html`
(`context.toolbox`), `.design/progress/phase-0.md`.

## 2026-08-17 · gate

**Decided:** "Make it public, enable Pages" — after `POST /repos/johnvijaysolomon/wati/pages`
failed with HTTP 422, *"Your current plan does not support GitHub Pages for this repository"*.
Pages on a private repo needs a paid plan; this account is free. The repo had been created private
as asked, so the failure was reported and the choice handed back rather than the visibility being
flipped silently.
**Contradicts:** the answer given minutes earlier in the same gate — repo `wati`, **private**.
**Option:** (1) update the spec — visibility changed to public, `gh repo edit --visibility public`.
**Propagated:** repo visibility, Pages enabled on `main` root
(<https://johnvijaysolomon.github.io/wati/>), `.design/memory/toolbox.md` (Hosting note records
both the 422 and why the repo is public), `CLAUDE.md` and `README.md` (world-readable warning, so
later phases cannot commit private material by accident).

## 2026-08-17 · correction

**Decided:** two factual errors from the 08:12–08:38 run were corrected during the re-run, neither
of them a taste decision, so neither was gated.
**Contradicts:** (a) `toolbox.md` Notes, 08:21 — "the Icons8 MCP is connected (`search_icons`,
`get_icon_svg`) and serves the SVGs". No Icons8 MCP exists in this session or at account level
(`ToolSearch "+icons8"` → nothing). Solar is an open set needing no account, so the row stays
`active` on the strength of the *choice*; only the delivery claim was wrong. (b) `index.html`
lines 47 and 78 — `{{PRODUCT_NAME}}` had been substituted in the markup per `init.md` step 6,
which breaks phase-0 checklist item 8 ("nothing outside that data block was edited"). This was the
blocker `init.7` reported at 08:34 and could not resolve.
**Option:** n/a — restoring a false record and a shipped file, per `init.md`'s own recovery prompt.
**Propagated:** `toolbox.md` Icons note rewritten; `index.html` markup restored to
`{{PRODUCT_NAME}}` in `<title>` and `[data-product]`. Evidence the substitution was never needed:
`assets/pipeline.js:618-622` sets both from the JSON (`ctx.product || data.product`), and line 619
explicitly handles the un-substituted `{{` placeholder. **The template defect stands** — `init.md`
step 6 orders an edit checklist item 8 forbids — and is worth reporting upstream.

## 2026-08-17 · gate

**Decided:** "tag it" — phase-0 sign-off. `/dsf:check 0` returned 12 pass · 0 fail · 0 human
against `.design/checklists/phase-0-init.md`, verdict written to
`.design/checklists/results/phase-0.md`, and the human confirmed at the sign-off gate.
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** tag `phase-0-init` created; `index.html` phase 0 → `status: done` + `tagged: true`
with both artifact `exists` flags true, phase 1 → `in-progress`; phase 0 `criteria` written as all
twelve passed, `checkedAt: 2026-08-17`. Phase 0 is closed; `/dsf:brief` is the next command.

## 2026-08-17 · gate

**Decided:** "approved" — the phase-1 brief gate, on the brief played back in chat. The
answers it approves, in the human's words across the interrogation: `"an omnichannel app like
intercom, ai sensy"` (seed) · AI-first deflection · Administrator, from a ten-role model they
supplied · already on a WhatsApp BSP · "the AI is fake" · desktop web primary · greenfield,
`"Wati is the name, fresh visual identity"` · all five channels · `"10 minutes"`, `"30%"`,
`"against previous BSP-post migration"` · `"no"` hard constraints · `"this is not another
WhatsApp API based SAAS app"` · designed roles `"Admin, operator"`.
**Contradicts:** `nothing` — phase 1 authors the spec chain's first layer, so there was nothing
upstream to contradict. Two prior phase-0 entries were read and carried forward rather than
re-decided: the product name (`"Product is Wati - An agentic customer engagement platform"`)
and the parked brand green `#23A455`, which stays a phase-5 starting point, not a lock.
**Option:** n/a
**Propagated:** `CLAUDE.md` (Brief section + Brief context block), `README.md` (Brief section),
twelve scaffold folders, `index.html` (`context.product`, `context.oneLiner`, phase 1 artifacts,
phase 2 unlocked, `steps`), `.design/progress/phase-1.md`.

## 2026-08-17 · contradiction

**Decided:** not a human gate — recorded because the rule-12 guard fired against the framework
itself, not against a request. `/dsf:brief` step 6 orders every `{{PRODUCT_NAME}}` occurrence in
`index.html` replaced, including `<title>` and `[data-product]`. `.design/memory/phases.md`
(**The dashboard data block**) says the *only* part of that file any command may touch is the
`pipeline-data` block, and phase-0 checklist item 8 — signed off 12/12 — forbids the markup edit.
The same collision blocked `/dsf:init` at 08:34 and was resolved there by restoring the markup.
**Contradicts:** `.design/memory/phases.md` line 225, quoted: "the **only** part any command may
touch is the data block embedded in `index.html` itself". `CLAUDE.md` binds the tie: "When a
command and that file disagree, that file wins."
**Option:** (1) update the spec — the command file is what is wrong, and it is wrong in a way
that is now recorded twice. Verified rather than assumed: `assets/pipeline.js:618` reads
`ctx.product || data.product` and writes it into `document.title` and every `[data-product]`
node, so filling `context.product` renders the name everywhere and the markup substitution is
redundant as well as forbidden.
**Propagated:** `index.html` `context.product` set to `Wati`; the two `{{PRODUCT_NAME}}`
placeholders in the markup left intact by design. Reported at sign-off as a framework bug in
`/dsf:brief` step 6, not as a phase-1 defect.

## 2026-08-17 · gate

**Decided:** "tag it" — the phase-1 sign-off gate, on the re-check verdict of 13/13. Preceded by
"compress it" at the 12/13 verdict, which closed checklist item 2: the Brief block's Who,
Problem, Platform, Scope and Constraints paragraphs were each cut to two sentences. No fact was
re-decided and no gate answer was revisited — only elaboration was removed. Two implications that
would have been lost moved into the Brief context block rather than out of the repo: `Trial` being
one of the ten roles (so the trial state is designed, not an afterthought) and the phase-8
inversion warning.
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** `CLAUDE.md` (Brief block compressed, Brief context block extended),
`.design/checklists/results/phase-1.md` (fresh 13/13 verdict replacing the 12/13 one),
`index.html` (phase 1 `criteria` all-passed, `status: done`, `tagged: true`), git tag
`phase-1-brief`. Carried forward, not closed: checklist item 12 passes but rests on the human's
own diagnosis that the incumbents' AI is a keyword bot — if `/dsf:research` finds otherwise, the
brief's problem statement moves and phase 1 reopens through `/dsf:change`.

## 2026-08-17 · gate

**Decided:** "remove Wati, cut soft group to Intercom, Tidio, Zendesk" — the phase-2a competitor-set
gate. Wati's current product was proposed as a hard comparator and struck, so the research argues
against the market rather than against the incumbent being replaced. The soft group was cut from
five to three, taking the trade the proposal offered explicitly: fewer products, deeper evidence
per product. Crisp and Freshworks (Freddy) were the two dropped. Final set: 12 products — hard 4
(AiSensy, Interakt, Gupshup, Respond.io), soft 3 (Intercom, Tidio, Zendesk), aspirational 5
(Sierra, Decagon, Ada, Salesforce Agentforce, Forethought).
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** `.design/progress/phase-2.md`, and the collection scope of `research.2` — no
product outside this list is searched, per the command's own rule.

## 2026-08-17 · gate

**Decided:** "confirmed" — the phase-2a benchmark-dimension gate. The dimension is **proving the
AI works**: how a product defines a resolution, measures it, shows the Administrator what the AI
got wrong, and turns that into a fix. Proposed from the matrix, where six products claim 67–98%
resolution and only Intercom publishes what counts (confirmed vs assumed resolution, no charge
when the customer asks for a human, refund on reopen). The alternative offered and not taken was
time-to-live, which competes with the 10-minute success criterion; it was argued against because
it is a one-time event while proving-it-works is the loop the Administrator returns to weekly.
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** `research/research.md` BENCHMARK section, `index.html` `context.benchmarkDimension`,
`.design/progress/phase-2.md`. Phase 5 reads this dimension back when deriving the visual language.

## 2026-08-17 · gate

**Decided:** "2" — the phase-2a pattern gate. Chosen pattern: **clustered themes**, where failures
are grouped by cause and the unit of work is the theme, never the individual conversation. Chosen
against four alternatives that differ in mechanism: queue triage (item by item), sampled audit
(statistical), counterfactual replay (test against history), natural-language authoring.
**Reading recorded because the answer is terse:** the recommendation it selects was stated as
"2 · Clustered themes, with 4 · Counterfactual replay as the action taken from a cluster", so the
pairing is carried forward. If "2" meant clusters without replay, that is a correction to make
before `/dsf:ia` — replay is a large build commitment and it shapes the main screen.
**Rejected and why, so it is not re-litigated:** queue triage was disqualified — it contradicts the
brief's own line that the inbox is "an exception surface, not the workspace", it gives the
Administrator the Operator's job, and it fails benchmark criterion C5 (you can close items forever
without the system improving). Sampled audit is the named second choice, under the condition that
real accounts produce so many themes that the job becomes proving the number rather than fixing
the tail.
**Contradicts:** `nothing`
**Option:** n/a
**Propagated:** `research/research.md` PATTERNS + CONCLUSIONS, `CLAUDE.md` Research context block,
`.design/progress/phase-2.md`. `/dsf:ia` (phase 3) derives the sitemap from this pattern.

## 2026-08-17 · gate

**Decided:** "1" — the phase-2b persona gate. **Persona 1, "the one who has already failed once"
(2–10 person D2C business, set the BSP up themselves, watched it fail), is PRIMARY**, against a
recommendation for Persona 2 ("the one who owns the number", ops lead at a scaling brand). The
human chose the persona the evidence describes over the persona the arithmetic selects: every
verbatim quote in the corpus comes from a 2–10 employee company, while the case for Persona 2
rested on the −30% criterion's economics and not on a single user statement.
**Consequence, recorded because it is a real cost of the choice:** this changes which success
criterion drives the design. At Persona 1's volume, −30% cost per resolved conversation is close
to meaningless, so **10 minutes to live becomes the dominant criterion** and −30% now measures
value for a *secondary* persona. Left open for the human: re-scope the criterion to Persona 2,
replace it for Persona 1 with something their volume can move, or accept design-for-one and
measure-on-another. That is a `/dsf:change` against the signed-off brief when it is taken.
**Contradicts:** nothing written — but it puts the brief's second success criterion under strain,
which is logged here rather than silently absorbed.
**Option:** n/a
**Propagated:** `people/personas.md` (primary flag, both rationales, open-questions item 1,
self-critique table), and downstream `people/jtbd.md`, the coverage matrix and the MVP core, all
of which are now weighted to Persona 1. One invented clause ("inherited rather than chose") was
removed from Persona 2 in the same pass rather than kept with a label.

## 2026-08-17 · gate

**Decided:** "good to g[o]" — the phase-2b MVP-core gate. **Three core jobs kept:** (1) see it
working on my own real questions within the hour; (2) find out about a bad answer before the
customer tells me; (3) leave without a fight. All three score 3 for the primary persona and are
uncovered by the market, read off the matrix rather than argued.
**Five features cut:** campaign / broadcast composer; drag-and-drop flow builder; per-conversation
agent queue as an Administrator destination; error-budget / SLO dashboard; sampled QA scorecard
(a cut for now, conditional on theme volume that P1 does not have).
**Two consequences stated at the gate and accepted:** (a) the main job — repeat questions handled
without me — is deliberately **not** in the core, because every competitor claims it: table stakes,
not differentiation; (b) "a number I can defend", the job the whole benchmark dimension was built
around, **misses the core** because it scores 2 for the primary persona and 3 for the secondary
one. It re-enters the moment the primary persona flips back. That is the visible cost of the
`users.2` gate and it was shown before this gate was taken.
**Risk named and accepted:** cutting the flow builder removes the category's default fallback, so
the first-run experience has no safety net if the AI answers badly on day one. AiSensy and Interakt
both sell that builder as the core product.
**Contradicts:** `nothing` — but "leave without a fight" is a job no competitor designs for and the
brief does not mention, so it enters the spec here for the first time.
**Option:** n/a
**Propagated:** `people/jtbd.md` (MVP core + cut candidates), `CLAUDE.md` People block, and
`/dsf:ia` (phase 3), which turns these three jobs into the sitemap.

## 2026-08-17 · gate

**Decided:** "phase-2-discover" — the phase-2 sign-off gate, on a 25/25 verdict covering both
sub-commands (`/dsf:research` and `/dsf:users`, 19/19 steps). The human named the tag, which is
the confirmation the checklist alone could not give.
**Contradicts:** `nothing` in this pass — but the phase is signed off **carrying an open
contradiction against phase 1**, and that is recorded rather than resolved here: the brief's
problem statement ("the AI in the tool they have is fake — a keyword bot behind a flow builder")
has been contradicted twice by phase-2 evidence. 2a: the incumbents' AI exists and is an *upsell*
on a keyword-flow core. 2b Q3: a search specifically for people who left over bad AI answers found
none — the corpus records absent support, billing traps and platforms that did not work.
`CLAUDE.md` and `README.md` still carry the original wording, deliberately unpatched, because
editing a signed-off artifact from inside a later phase is exactly what constitution rule 13
forbids.
**Option:** n/a for this gate. The contradiction above is routed to `/dsf:change`, which sizes the
blast radius and decides whether phase 1 reopens.
**Propagated:** `.design/checklists/results/phase-2.md` (25/25 verdict), `index.html`
(phase 2 `criteria` 25/25, `status: done`, `tagged: true`; phase 3 `locked` → `in-progress`),
git tag `phase-2-discover`. Four further items are carried forward in the verdict's
*Carried forward* section: two dangerous `[?]` holding scope decisions, email and SMS unevidenced
as inbound channels, and Meta's 2026-01-15 AI-Provider policy as a constraint the brief records as
absent.

## 2026-08-18 · change-request

**Decided:** "carry on" at the rule-12 guard, then **"partial"** at the scope gate. The guard's
option (1) *update the spec* was taken — read from "carry on" and stated back before any file was
touched, with the scope gate immediately after as the real protection. **The change:** the brief's
Problem statement is rewritten from *"The AI in the tool they have is fake — a keyword bot behind a
flow builder that deflects nothing real…"* to *"The tool they have does have an AI, sold as an
upsell on a keyword-flow core, but that is not why they leave — they leave because support did not
answer, billing trapped them and the product did not work. They are not buying better answers;
they are buying a vendor they can verify and exit."*
**Contradicts:** `CLAUDE.md:25` (the line quoted above) and its duplicate at `README.md:32`. That
decision's recorded source is the human's own answer at the phase-1 problem gate — they picked
"The AI is fake" from four options. **It was recorded as provisional against exactly this test:**
`.design/decisions.md`, phase-1 sign-off entry — *"checklist item 12 passes but rests on the
human's own diagnosis that the incumbents' AI is a keyword bot — if `/dsf:research` finds
otherwise, the brief's problem statement moves and phase 1 reopens through `/dsf:change`."*
Research found otherwise, twice: COMPETITORS difference 1 (AiSensy ₹2,500 builder vs ₹3,500 AI
Agent Builder; Interakt AI Agents a ₹3,000/mo add-on) and Re-research Pass 2 Q3 (a search
specifically for people who left over bad AI answers returned none).
**Option:** **(1) update the spec**, at **partial** scope.
**Propagated:** `CLAUDE.md` — Problem rewritten, the third `[?]` struck through as closed by phase
2, a **Corrections** line added recording the old wording and its two overturning findings, and
the **Brief** context block corrected from "three `[?]` open" to two. `README.md` — the
front-page pitch (`:5`) and the Brief section (`:32-34`). Phase 1 reopened: `status` →
`in-progress` in `index.html` with `tagged`, `criteria` and `steps.done` deliberately intact;
`Reopened` line prepended to `.design/checklists/results/phase-1.md`; reopen line appended to
`.design/progress/phase-1.md`.
**Recorded debt** — `design-system/backlog.md`, created early for this purpose: four phase-2
references still describe this change as pending (`people/personas.md:44`,
`people/personas.html:325`, `research/research.md:469`,
`.design/checklists/results/phase-2.md:52`). Each is accurate as history; editing them would
reopen phase 2 and cost a re-check of 25 items, which the human declined at the scope gate.
Closed by the next `/dsf:change` that reopens phase 2 for another reason, or by a `/dsf:users`
re-run. **Do not reopen phase 2 solely for this.**
**Deliberately out of scope,** named at the restatement and unchanged here: the success criteria
(the −30% persona-scoping problem is its own change), the five channels (email and SMS are
unevidenced as inbound channels for the primary persona — recorded in the phase-2 verdict, needs
its own `/dsf:change`), platform, brand, the ten roles and the anti-goals.
**Known risk introduced:** the Brief section grew 50 → 56 lines, so phase-1 checklist item 13
("the brief fits on one screen") is now borderline where it was comfortable. Flagged rather than
pre-judged; `/dsf:check 1` decides.
