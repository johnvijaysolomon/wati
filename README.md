# Wati

An agentic customer engagement platform.

This repo **is** the design file. The brief, research, structure, screens, voice, visual
language, design system and handoff all live here as versioned artifacts — not in a Figma file
and not in chat history. It is built with the
[design-spec-framework](https://github.com/denysosadchyi/design-spec-framework) pipeline,
driven by `/dsf:*` commands in Claude Code.

> Phase 0 wrote this skeleton. `/dsf:brief` (phase 1) replaces the one-liner above with the
> interrogated brief and fills the section links below as each phase produces them.

## Start here

**Project home page: <https://johnvijaysolomon.github.io/wati/>** — published from `main` by
GitHub Pages. It also opens straight from the local file, [`index.html`](index.html)
(`/Users/johnvijaysolomon/wati/index.html`), with no server needed.

It is the state view of the pipeline: which phase the project is in, every artifact produced so
far, the criteria each phase is verified against, and the prompt to send next. Status is derived
from the files on disk, the `/dsf:check` verdicts and the git tags — never declared.

> **This repo is public.** Pages on a private repo needs a paid GitHub plan, so the repo was made
> public at the phase-0 gate to publish the pipeline. Everything committed here — research,
> screenshots, personas, quotes — is world-readable. Anything that must stay private does not
> belong in this repo.

## The route

One line per section, filled in by the phase that produces it. `[?]` means "that phase has not
run yet" — it is a real state, not a gap to tidy.

| Section | What is in it | Status |
|---|---|---|
| Brief | What Wati is, who it is for, constraints, success criteria — `CLAUDE.md` | `[?]` |
| Research | Competitor matrix, benchmark, chosen pattern — `research/` | `[?]` |
| People | Personas and jobs-to-be-done — `people/` | `[?]` |
| Structure | Sitemap and flows — `ia/` | `[?]` |
| Wireframes | Every screen in every state — `wireframes/index.html` | `[?]` |
| Voice | Voice principles and the single copy source — `voice/` | `[?]` |
| Concept | Recorded taste, references, the chosen direction — `concept/` | `[?]` |
| Build | Tokens, components, the kit — `DESIGN.md`, `design-system/`, `ui/` | `[?]` |
| System | The design system showcase and patterns — `design-system/docs/` | `[?]` |
| Responsive | Breakpoints, grid, the adaptive shell — `responsive/` | `[?]` |
| Motion | Motion tokens and the inventory — `animations/` | `[?]` |
| Handoff | Behaviour spec, token map, a11y — `handoff/` | `[?]` |

## How the repo governs itself

- [`CLAUDE.md`](CLAUDE.md) — the agent's context: the brief, the toolbox, and one block per phase.
- [`.design/memory/constitution.md`](.design/memory/constitution.md) — the binding rules every
  `/dsf:*` command obeys.
- [`.design/memory/phases.md`](.design/memory/phases.md) — the canonical phase table.
- [`.design/memory/toolbox.md`](.design/memory/toolbox.md) — which tools this project has and
  what each fallback means downstream.
- [`.design/decisions.md`](.design/decisions.md) — append-only: every gate answer, verbatim.
- [`.design/progress/`](.design/progress/) — append-only step ledgers, one file per phase.
- [`.design/checklists/`](.design/checklists/) — the done-criteria `/dsf:check` verifies against.
- [`docs/FRAMEWORK.md`](docs/FRAMEWORK.md) — how the framework itself works.

## Next

`/dsf:brief` — the phase-1 interrogation that turns the one-liner above into a real brief.
`/dsf:status` at any time tells you where the project is and what to send next.

---

Built on [design-spec-framework](https://github.com/denysosadchyi/design-spec-framework) (MIT).
