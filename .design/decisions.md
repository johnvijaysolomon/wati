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
