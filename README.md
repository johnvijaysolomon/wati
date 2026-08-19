# Wati

An agentic customer engagement platform. The AI resolves the conversation; the product is where
you build, watch and correct it — designed around the Administrator switching off a WhatsApp BSP
they could neither verify nor escape.

This repo **is** the design file. Research, structure, screens, copy, visual language, the
design system and the handoff all live here as files. No Figma required.

**→ [Open the pipeline page](./index.html)** — this is your home: current phase, every
step and prompt to type, success criteria, and links to every viewable page. Live at
**<https://johnvijaysolomon.github.io/wati/>**.

**Current phase: 2 · Discover.** Phase 1 is signed off and tagged `phase-1-brief`. Research
(2a) is done; the next prompt to type is `/dsf:users`.

Built with [design-spec-framework](https://github.com/denysosadchyi/design-spec-framework) —
spec-driven development for product design. Work is driven by `/dsf:*` commands in Claude
Code; the rules live in `.design/memory/constitution.md`.

---

## Brief

<!-- phase 1 -->

**Wati** is an agentic customer engagement platform. The AI handles the conversation end to end;
humans are the exception path, and the product's job is to make that AI good.

It is built for the **Administrator** of a business already running a WhatsApp BSP — Wati,
AiSensy, Interakt, Gupshup. They arrive mid-category with templates, contacts and a connected
number already in hand. Their current tool does have an AI — sold as an upsell on a keyword-flow
core — but that is not why they leave. They leave because support did not answer, billing trapped
them and the product did not work. They are not buying better answers; they are buying a vendor
they can verify and exit.

Ten roles exist in the product; **Administrator and Operator get designed views** and the other
eight are permission-gated. Five channels are in scope — WhatsApp, web chat, Instagram and
Facebook DM, email, SMS — reached through the Administrator's lens: connect, configure, monitor,
govern. Not five parallel inboxes.

**Platform:** desktop web, primary — tablet and mobile adapt down. This inverts phase 8, and
that inversion is deliberate.

**It works if:** a migrating Administrator gets from signup to the AI answering live traffic in
**under 10 minutes of in-product time** (Meta's own approval wait excluded), and cost per
resolved conversation falls **30%** against their previous BSP.

**It is not:** another WhatsApp API SaaS. Not a chatbot builder. Not shared-inbox-first.

Open questions carried into phase 2 are marked `[?]` in `CLAUDE.md` → **Brief**.

## Research

<!-- phase 2 · competitors, benchmark, patterns -->
Twelve competitors in three groups, one benchmark dimension studied across categories, five
interaction patterns and the one chosen. The finding that shapes everything downstream: in the
WhatsApp BSP market the AI is a **second SKU bolted onto a keyword-flow core**, and of six
products claiming 67–98% resolution, exactly one publishes how it counts. The chosen pattern is
**clustered themes** — the unit of work is the theme, never the individual conversation.

→ **[research/research.html](./research/research.html)** — the readable page, with the evidence
inline · `research/research.md` — the agent-readable source of truth ·
`research/screens/` — six captures backing the claims. Everything unverified is marked `[?]`.

## People

<!-- phase 2 · personas and jobs -->
Three personas split by behaviour, ten jobs, and the three that make the MVP. The primary persona
is **the one who has already failed once** — a 2–10 person business that bought a BSP on price and
watched it fail. The MVP core is: see it working within the hour · find out about a bad answer
before the customer tells you · **leave without a fight**, which is the best-evidenced job in the
project and one no competitor designs for.

→ **[people/personas.html](./people/personas.html)** — personas, jobs, the coverage matrix and
what is still unknown · `people/personas.md` · `people/jtbd.md`. The `[?]` marks are visible on
purpose: they are where the evidence ran out.

## Structure

<!-- phase 3 · sitemap, navigation, flows -->
Nineteen screens, each derived from a job rather than from a competitor's menu, five global
navigation items plus a permission-gated Inbox, and four flows with their decisions, states and
both endings. The coverage matrix leaks in exactly two places — the two social jobs — and those
are the two weakest-evidenced jobs in the project, which is the matrix working.

→ **[ia/ia.html](./ia/ia.html)** — the screen tree with the job beside every screen, all four
flows as diagrams, and the coverage matrix with orphans highlighted · `ia/sitemap.md` ·
`ia/flows.md`.

## Wireframes

<!-- phase 4 · grey screens with all states -->
`[?]` → `wireframes/index.html`

## Voice

<!-- phase 5 · voice principles and the copy source of truth -->
`[?]` → `voice/voice.html`, `voice/microcopy.md`

## Concept

<!-- phase 5 · chosen visual direction -->
`[?]` → `concept/directions.html`, `concept/concept.html`

## UI

<!-- phase 6 · token audit, tokens, components, kit showcase -->
`[?]` → `ui/kit.html`, `ui/tokens-audit.md`

## Design system

<!-- phase 7 · the system as a product, with live docs -->
`[?]` → `design-system/docs/index.html`

## Responsive

<!-- phase 8 · behavior-based breakpoints, adaptive shell and components, split-view -->
`[?]` → `responsive/width-audit.html`

## Motion

<!-- phase 9 · motion tokens, the three jobs, reduced-motion -->
`[?]` → `animations/motion-inventory.html`

## Handoff

<!-- phase 10 · spec, map, a11y, release -->
`[?]` → `handoff/index.html`

---

## Repo map

| Path | What lives there |
|---|---|
| `.design/` | Constitution, phase table, toolbox, fallback prompts, artifact templates, phase checklists, `checklists/results/` (the `/dsf:check` verdicts), `progress/` (the append-only step ledgers), decision log |
| `.claude/commands/dsf/` | The `/dsf:*` commands |
| `CLAUDE.md` | Agent context — brief plus a block per phase |
| `index.html` | The project's home page — phases, artifacts, links, status |
| `research/` · `people/` | Phase 2 |
| `ia/` | Phase 3 |
| `wireframes/` | Phase 4 — the screens, layered by every later phase |
| `voice/` · `concept/` | Phase 5 |
| `ui/` · `design-system/` · `visuals/` | Phases 6–7 |
| `responsive/` | Phase 8 |
| `animations/` | Phase 9 |
| `handoff/` | Phase 10 |
