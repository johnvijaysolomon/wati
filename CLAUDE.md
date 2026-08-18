# Project context

This repo is the design file. Everything about this product — brief, research, structure,
screens, voice, visual language, system, handoff — lives here as files, not in chat history.

Read this file first, then the artifacts it points to. Never re-ask what is already written.

---

## Brief

Approved at the phase-1 gate, 2026-08-17, by interrogation not drafting (`superpowers`
**brainstorming**). Verbatim trace: `.design/decisions.md`.

**Wati** — an agentic customer engagement platform. The AI resolves the conversation; the
product is where you build, watch and correct it.

**Who.** The **Administrator** of a business already running a WhatsApp BSP — Wati, AiSensy,
Interakt, Gupshup — arriving mid-category with templates, contacts and a connected number in
hand, and owning the workspace: users, roles, channels, numbers, billing, integrations. Ten roles
exist (Administrator, Campaign Manager, Template Manager, Operator, Developer, Contact Manager,
Dashboard Viewer, Automation Manager, Billing Manager, Trial); **Administrator and Operator get
designed views**, the other eight are permission-gated.

**Problem.** The tool they have does have an AI, sold as an upsell on a keyword-flow core, but
that is not why they leave — they leave because support did not answer, billing trapped them and
the product did not work. They are not buying better answers; they are buying a vendor they can
verify and exit.

**Platform.** **Desktop web, primary**; tablet and mobile adapt down. This **inverts phase 8** —
phase 4 designs at desktop width, phase 8 contracts — and the inversion is deliberate.

**Scope.** The Administrator's world, deep — set up the AI, watch it deflect, fix what it gets
wrong, control who can do what; inbox and campaigns are real but secondary. **Channels:**
WhatsApp, web chat widget, Instagram + Facebook DM, email, SMS — all five, reached as
**connect / configure / monitor / govern**, not five parallel inboxes.

**Constraints.** No deadline, team limit, or legal/regional fence stated, and the repo is
**public and world-readable**, accepted knowingly at this gate. Greenfield brand — Wati is the
name, the identity is designed fresh, the current Wati look constrains nothing, and phase 0's
brand green `#23A455` is a phase-5 starting point rather than a lock (`/dsf:concept` opens by
asking which).

**It works if.** (1) A migrating Administrator gets from signup to the AI answering live traffic
in **under 10 minutes of in-product time** — knowledge loaded, guardrails set, AI live; Meta's
own number-connection and template-approval wait (hours, external) is excluded and runs in
parallel. (2) Cost per resolved conversation falls **30%** against the previous BSP's blended
cost, measured post-migration.

**It is not.** *Another WhatsApp API SaaS* (the human's line). Not a chatbot builder. Not
shared-inbox-first.

**Corrections.** 2026-08-18 · `/dsf:change` — the Problem above replaces the phase-1 line
*"the AI in the tool they have is fake — a keyword bot behind a flow builder"*, overturned by
phase-2 evidence. Full record, sources and recorded debt: `.design/decisions.md`.

**Open `[?]`** — `[?]` the 30% measurement window: "post-migration" carries no period;
hypothesis **90 days**, confirmed by the human or a phase-2 category benchmark. `[?]` which
surfaces the eight non-designed roles reach — hypothesis: each gets a permission-filtered view of
the Administrator's surfaces rather than a destination of its own, except `Billing Manager` and
`Trial`, which probably need one. Phase-3 work, confirmed by `ia/sitemap.md`.
~~`[?]` what "the AI is fake" means concretely in the competitors~~ — **closed by phase 2**, and
the answer rewrote the Problem above rather than confirming it.

---

## First contact

If this looks like a fresh clone (toolbox rows still `[?]`, no `phase-0` ledger), your FIRST
message to the designer must, before anything else:

1. Hand them the project home page: the absolute local path to `index.html` (and, once
   hosting is active, its URL) with one sentence on how to open it in a browser.
2. Say what the page is: the state view of the pipeline — the phase you are in, derived from
   artifacts on disk plus `/dsf:check` verdicts plus tags, with every prompt to send and the
   done-criteria each phase is verified against.
3. Name the first move: open the page, read "How this works", then type `/dsf:init`.

The page tracks state; the chat executes. Neither one guesses the other's job.

---

## Rules of engagement

- **Constitution:** `.design/memory/constitution.md` — the binding rules for every
  `/dsf:*` command. Read it before acting.
- **Phases:** `.design/memory/phases.md` — the canonical phase table: commands, checklists,
  tags, canonical artifact paths, the done/in-progress/locked definitions, and the
  `index.html` data contract. When a command and that file disagree, that file wins.
- **Progress:** `.design/progress/phase-N.md` — the append-only step ledger. Every command
  appends one line the moment a numbered step or a gate finishes, reads its ledger before a
  re-run, and never runs work that belongs to a later phase without stopping first (constitution
  rule 13, the phase-order guard).
- **Toolbox:** `.design/memory/toolbox.md` — which tools this project has, which fallback to
  use when one is missing, and the only three status values (`active` / `fallback` / `[?]`).
  Read it before using any tool.
- **Fallback prompts:** `.design/prompts/` — `critique.md`, `audit.md`, `document.md`,
  `extract.md`, `brief-interrogation.md`. These run whenever the matching toolbox row is not
  `active`.
- **Checklists:** `.design/checklists/phase-N-*.md` — read-only done-criteria. Nobody ticks
  them; `/dsf:check` verifies them against the files and writes the verdict to
  `.design/checklists/results/phase-N.md`.
- **Decisions:** every gate answer, "keep it" and contradiction resolution is recorded in
  `.design/decisions.md`; changes after sign-off go through `/dsf:change`.
- **Dashboard:** `index.html` — current status, artifacts and links. **The project home page
  is `index.html` — keep its data block current.**

---

## Toolbox

Set at phase 0. Full detail, evidence and reasons in `.design/memory/toolbox.md` — read that
file before touching any tool. Only `/dsf:init` changes a row.

**Active**

- **Browser & screenshots — Playwright MCP.** Project-scoped in `.mcp.json` as `playwright`
  (`@playwright/mcp` 0.0.79). Screens are rendered and screenshotted, never described.
  Only loads for a session rooted at this repo.
- **Design quality laws — `impeccable` 4.1.1**, project scope. Every critique / audit / document /
  extract pass in phases 4–10 runs the `impeccable` command for that pass, not the file in
  `.design/prompts/`. The artifact still names the pass and which tool ran it.
- **Structured brief — `superpowers` 6.3.0**, project scope. `/dsf:brief` runs the `brainstorming`
  skill. The gate discipline is unchanged: never synthesise a brief from one answer, unanswered
  stays `[?]`.
- **Icons — Solar**, downloaded into the repo as SVG from the open set — no account, and **no
  Icons8 MCP is connected**, so nothing may plan around one. The single style (`linear` / `bold` /
  `bold-duotone`) is **not yet chosen** — it is locked at `/dsf:concept` and written to `DESIGN.md`
  at `/dsf:build`. No phase ships an icon before then.
- **Hosting — GitHub + Pages.** Repo `johnvijaysolomon/wati`, `origin/main`, Pages on `main` root:
  **<https://johnvijaysolomon.github.io/wati/>**. Every phase pushes and reports its artifact's
  public URL. **The repo is public** — research, screenshots, personas and quotes are all
  world-readable, so nothing that must stay private goes in this repo.

**Fallback in force**

- **Visual references — no Refero.** Use the Mobbin MCP first, web search second; every row of
  `concept/references.md` is tagged `[mobbin]` or `[web]` with the app and screen named.
- **Imagery — no Gemini key.** Higgsfield MCP `generate_image`, one locked colorway, every
  prompt recorded verbatim in `visuals/README.md` with its asset id.

**Session caveat.** `impeccable` and `superpowers` were installed on 2026-08-17 and load from the
**next** session start. A command that needs one must confirm it is actually available and use the
`.design/prompts/` fallback for that session if it is not — saying so in the artifact.

---

## Pipeline

Eleven phases (0–10) and seventeen commands, driven by `/dsf:*`. Each phase reads the previous
phases' artifacts, produces a Markdown artifact for the agent plus an HTML page for humans,
ends with a critique cycle and a human gate, updates the living docs, and commits.

| Phase | Command(s) | Output lives in | Tag |
|---|---|---|---|
| 0 · Init | `/dsf:init` | `.design/memory/toolbox.md`, `index.html` | `phase-0-init` |
| 1 · Brief | `/dsf:brief` | this file, `README.md`, folder scaffolding | `phase-1-brief` |
| 2 · Discover | `/dsf:research` + `/dsf:users` | `research/`, `people/` | `phase-2-discover` |
| 3 · Structure | `/dsf:ia` | `ia/` | `phase-3-ia` |
| 4 · Wireframes | `/dsf:wireframes` | `wireframes/` | `phase-4-wireframes` |
| 5 · Language | `/dsf:voice` + `/dsf:concept` | `voice/`, `concept/` | `phase-5-language` |
| 6 · Build | `/dsf:build` | `DESIGN.md`, `design-system/`, `ui/`, `visuals/` | `phase-6-build` |
| 7 · System | `/dsf:system` | `design-system/` — `docs/`, `patterns/`, `examples/` | `phase-7-system` |
| 8 · Responsive | `/dsf:responsive` | `responsive/`, breakpoint + grid tokens, the shell, `split-view` | `phase-8-responsive` |
| 9 · Motion | `/dsf:motion` | `animations/`, motion tokens, the components | `phase-9-motion` |
| 10 · Handoff | `/dsf:handoff` | `handoff/`, release | `phase-10-handoff` |

Cross-cutting, usable at any point: `/dsf:status` (where am I, what to type next),
`/dsf:critique` (defect table on any scope), `/dsf:check` (verify a phase against its
checklist and sign it off), `/dsf:change` (a request that invalidates signed-off work —
blast radius, re-opened phases, logged decision).

**Tags.** Exactly one tag per phase, as listed above — phases 2 and 5 have two commands and
still get one tag, created once both are done. Tags are created **only** by `/dsf:check`, on a
full pass, after the human confirms. Phase commands never tag. Phase 10 also carries the release
tag `v1.0`. A tag is the result of the gate, never a criterion inside it.

---

## Context blocks

Each phase appends its block below and keeps it current. A block is short — the facts later
phases need, plus paths. Not a retelling of the artifact.

### Brief
<!-- phase 1 · what the product is, who it is for, platform, constraints, success criteria -->
Done, 2026-08-17 — full text in the **Brief** section at the top of this file; gate trace in
`.design/decisions.md`. The five facts later phases need most: primary user is the
**Administrator** switching off another WhatsApp BSP · the job is **AI-first deflection**, so
the inbox is an exception surface, not the workspace · **desktop web is primary**, so phase 8
contracts instead of expanding · **five channels** as connect/configure/monitor/govern, not five
inboxes · success is **10 min of in-product time to live** and **−30% cost per resolved
conversation**. Two `[?]` remain open and are listed in the Brief section; the third was
closed by phase 2 and overturned the Problem statement — see **Corrections** there. Two implications the Brief block states only by naming them: `Trial` is one of the ten
roles, so the trial state is a designed experience rather than an afterthought (phase 3 owns
where it sits); and the phase-8 inversion means phase 4 designs at desktop width, so a later
phase reading "mobile-first" anywhere should treat it as a defect, not an instruction.

### Research
<!-- phase 2 · chosen interaction pattern · the three MVP mechanics · benchmark dimension · top three open questions · paths to research/ -->
Done 2026-08-17 (2a) — `research/research.md`, `research/research.html`, 6 screenshots in
`research/screens/`.
**Chosen interaction pattern: clustered themes** — failures are grouped by cause and the unit of
work is the theme, never the individual conversation; **counterfactual replay** is the action
taken from a cluster (carried as a recorded reading of a one-character gate answer — confirm
before `/dsf:ia`). Queue triage is **disqualified**: it contradicts the brief's "inbox is an
exception surface" and quietly rebuilds the shared inbox.
**Benchmark dimension: proving the AI works** — how a product defines a resolution, measures it,
shows what the AI got wrong, and turns that into a fix. Scored across categories; the two top
scorers (LangSmith 34/40, Stripe Radar 31/40) are both "evaluate an automated decision-maker"
products and neither is a support tool.
**Three MVP mechanics:** (1) backtest a change against the account's own recent conversations
before enabling it; (2) validate-fix with named states, so the product confirms the fix instead of
the human assuming it; (3) automatic regression when a handled theme starts failing again.
**Explicitly not carried:** error-budget / SLO framing — vendor math for a buyer who just left
over vendor math.
**Correction to the brief:** the incumbents' AI is not absent. It exists and is an *upsell* on a
keyword-flow core (AiSensy ₹2,500 builder vs ₹3,500 AI Agent Builder; Interakt AI Agents ₹3,000/mo
add-on), so the buyer's paid default is still a decision tree. The brief's problem statement holds
in spirit and is wrong in wording — phase 1's third `[?]` closes this way, not as a clean yes.
**Top three open questions:** the −30% baseline (owner-only, and the criterion is unverifiable
without it); whether Wati prices by outcome (it changes the Administrator's surface); which of the
ten roles are load-bearing.

### People
<!-- phase 2 · primary persona and why · main job in "when / I want / so that" form · top-3 MVP jobs · paths to people/ -->
Done 2026-08-17 (2b) — `people/personas.md`, `people/jtbd.md`, `people/personas.html`.
**Primary persona: "the one who has already failed once"** — a 2–10 person D2C or services
business, most often India, who bought a BSP on price, set it up themselves in an afternoon,
shipped a flow and watched it fail to hold a real conversation. Still answering WhatsApp
personally. Chosen by the human at the `users.2` gate over the higher-volume ops lead:
**evidence over inference** — every verbatim in the corpus comes from this segment.
**Main job:** *When the same questions keep arriving on WhatsApp and I am the one answering them,
I want them handled without me, so that I can spend my day on the work only I can do.*
**Top-3 MVP jobs** (high for the primary persona AND uncovered by the market): (1) see it working
on my own real questions within the hour; (2) find out about a bad answer before the customer
tells me; (3) **leave without a fight** — the best-evidenced job in the project and one no
competitor designs for.
**Cut at the `users.4` gate:** campaign composer, drag-and-drop flow builder, per-conversation
Administrator queue, error-budget dashboard, sampled QA scorecard.
**Two consequences later phases must not rediscover:** the **−30% success criterion now belongs to
a secondary persona** (at P1's volume it is not money), so **10 minutes to live is the dominant
criterion**; and counterfactual replay survives for P1 **only if it costs seconds inline** —
setup must stay under 30 minutes, so a pre-flight that is its own screen is out.
**Standing `[?]` that affect design:** R3's importance to P1 (a guess that kept the benchmark's
own job out of the MVP core); **email and SMS are unevidenced as inbound channels** for this
persona — WhatsApp confirmed, Instagram supported, the other two carried on the brief's authority.

### Structure
<!-- phase 3 · main flow · navigation model and tap depth to the main job · paths to ia/ -->
`[?]`

### Wireframes
<!-- phase 4 · where the screens live, naming convention, state pages, the navigator panel -->
`[?]`

### Voice
<!-- phase 5 · pointer to voice/voice.md principles and voice/microcopy.md as the single copy source -->
`[?]`

### Concept
<!-- phase 5 · chosen direction and why · recorded taste and anti-references · icon set · image source -->
`[?]`

### Build
<!-- phase 6 · token levels, where components live, the shell, the kit showcase, visuals colorway -->
`[?]`

### System
<!-- phase 7 · contribution rules, showcase location and URL, patterns, backlog -->
`[?]`

### Responsive
<!-- phase 8 · the two breakpoints and the behavior that set them, the grid tokens, the split-view pattern -->
`[?]`

### Motion
<!-- phase 9 · motion tokens and their roles, the three jobs, where micro-interactions live, reduced-motion -->
`[?]`

### Handoff
<!-- phase 10 · pointer to handoff/, the map, the a11y checklist, release tag and live URLs -->
`[?]`

---

## The "keep it" rule

When the human says **"keep it"** about an experiment, it stops being an experiment and
becomes a rule. Write the rule down here, and route the change to wherever the truth
currently lives. The destination escalates as the project matures — update this section at
the end of every phase that moves it.

**Current destination for a change:** the screen file itself.

<!-- Phase 4: the screen, plus wireframes/_conventions.md if it is a rule for all screens -->
<!-- Phase 5: voice/voice.md + voice/microcopy.md for copy; concept/concept.md for visual decisions -->
<!-- Phase 6: the kit component or the token — never the screen -->
<!-- Phase 7: design-system/ (component, pattern or token) first, then the screens -->
<!-- Phase 8: the responsive behavior lives in components and the shell -->
<!-- Phase 9: motion lives in components, never in a screen -->

**Kept rules**

- `[?]`
