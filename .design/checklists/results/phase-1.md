# Phase 1 — Brief · check results

Checked: 2026-08-17 · Checklist: `.design/checklists/phase-1-brief.md`
Result: **fail** — 12 pass · 1 fail · 0 human · 13 of 13 items

Item count verified against `.design/memory/phases.md` (**Per-phase item counts**): 13 expected,
13 found (`grep -c "^- \[ \]"`). The checklist carries no `<!-- check: … -->` executable
assertions (`grep -c "check:"` → 0), so every verdict below is a file read, a command output, or
a rendered-page evaluation.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Brief produced by a structured brainstorm — asked before it wrote | pass | `.design/progress/phase-1.md:4` records the `superpowers` brainstorming skill run, 8 questions; `:3` records the seed taken verbatim and not expanded. `.design/decisions.md` phase-1 `gate` entry holds the human's own words for every answer. No artifact existed before the gate: `git show --stat 0719b6b` is the first commit touching `CLAUDE.md` in this phase |
| 2 | `CLAUDE.md` → Brief block states, **each in one or two sentences**, what the product is / the problem / who it is for / platform / hard constraints | **fail** | All five subjects are present, but four exceed the stated form. `CLAUDE.md:18-24` **Who** = 5 sentences · `:26-29` **Problem** = 3 · `:31-32` **Platform** = 3 · `:40-44` **Constraints** = 4. Only `:15-16` (what it is) = 2 is within budget. Content complete, form over budget |
| 3 | Success criteria written and observable | pass | `CLAUDE.md:46-50` — (1) "under 10 minutes of in-product time", with Meta's external wait explicitly excluded so the measurement has a defined start and end; (2) "falls 30% against the previous BSP's blended cost, measured post-migration". Both are countable signals, not adjectives |
| 4 | Anything unanswered marked `[?]` with an explicit hypothesis | pass | `CLAUDE.md:55-59` — three `[?]`, each with a hypothesis and a named confirmer: 30% window → hypothesis 90 days, confirmed by the human or a phase-2 benchmark; non-designed roles → `ia/sitemap.md`; "the AI is fake" → phase-2 first-hand competitor capability |
| 5 | The brief names what the product is **not** doing | pass | `CLAUDE.md:52-53` — "Another WhatsApp API SaaS" (attributed to the human), "Not a chatbot builder", "Not shared-inbox-first". Scope boundary also stated positively at `:34-38` — inbox and campaigns secondary |
| 6 | Folder scaffolding — exactly the twelve folders in `phases.md`, none missing, none invented | pass | All twelve present (`research`, `people`, `ia`, `wireframes`, `voice`, `concept`, `ui`, `design-system`, `visuals`, `responsive`, `animations`, `handoff`). Top-level diff against the canonical list minus pre-existing `assets/` and `docs/` → no invented folders. Six named subfolders (`research/screens`, `design-system/{components,patterns,docs,examples}`, `handoff/spec`) are from the `/dsf:brief` step-5 tree, not inventions |
| 7 | `README.md` → Brief section filled in and matches `CLAUDE.md` | pass | `README.md:22-47` — same primary user, same problem, same five channels with the same connect/configure/monitor/govern framing, same platform + phase-8 inversion, same two success criteria with the same numbers and the same Meta exclusion, same three anti-goals. No fact present in one and absent from the other; `README.md:47` defers the `[?]` list to `CLAUDE.md` rather than duplicating and drifting from it |
| 8 | `index.html` renders standalone, shows phase 1 in progress with artifacts present, `context.product` and `oneLiner` filled | pass | Rendered at `https://johnvijaysolomon.github.io/wati/?v=phase1` (Pages build `0719b6b`, built 07:23:27Z) and evaluated in the live DOM: `context.product` = `"Wati"`, `oneLiner` = the full one-line pitch, phase 1 `status: in-progress` with `CLAUDE.md=true` and `README.md=true`, phase 2 unlocked, phases 3–10 locked, and `document.body.innerText` contains no `{{`. Standalone verified structurally: the only four asset loads are relative (`index.html:48,49,3365,3366` → `assets/`), `fonts.css` embeds both faces as `url(data:font/woff2;base64,…)`, and the sole `http://` in `assets/pipeline.js` is the SVG namespace string, not a request. **Stated limit:** a literal `file://` open was not executed — the Playwright MCP blocks the `file:` protocol and a local static server was denied by the sandbox, so the no-external-request property is evidence-backed rather than directly observed |
| 9 | `.design/memory/toolbox.md` has no `[?]` in the Status column | pass | Tools-table Status column parsed row by row → `active`, `fallback`, `active`, `active`, `fallback`, `active`, `active`. The four `[?]` in the file are at `:25`, `:27`, `:71`, `:91` — all prose in the status-vocabulary table and the fallback rules, none in a tool row |
| 10 | Repo under git with the brief committed | pass | `0719b6b` "feat: phase 1 — product brief and repo scaffolding" and `053a653` "chore: phase 1 — close the step ledger". `git status --porcelain` → clean |
| 11 | Pushed, since `toolbox.md` records hosting as `active` | pass | `toolbox.md:43` Hosting = `active`. `git rev-list --left-right --count origin/main...main` → `0 0`. Confirmed downstream: the Pages build for `0719b6b` reports `status: built` and the live page serves the phase-1 data block |
| 12 | No claim about audience or market appears without a source or a `[?]` | pass | `CLAUDE.md:12-13` sources the whole block to the gate ("Verbatim trace: `.design/decisions.md`"), where every audience fact appears in the human's own words. The one market claim that is not the human's direct experience — competitor AI capability, `:26-27` — is explicitly downgraded at `:57-59` as "the human's diagnosis, not yet a sourced finding". **Weakest pass in the set:** that `[?]` sits 30 lines below the claim rather than inline, so a reader hitting `:26` reads it as fact. Sourced and marked as the item requires, but not at the point of use |
| 13 | The brief fits on one screen | pass | `CLAUDE.md:10-59` = 50 lines including blanks, one screen at typical editor height. Judgement call, recorded as such: it was 66 lines when first written and was compressed at `brief.4` specifically to meet this item — see `.design/progress/phase-1.md:6` |

## Open

- **Item 2** — compress the **Who**, **Problem**, **Platform** and **Constraints** paragraphs of
  the `CLAUDE.md` Brief block to one or two sentences each. No content needs to be removed or
  re-decided; the facts are right and the gate that produced them stands. What has to move is the
  material that is elaboration rather than fact — the ten role names could be a bare list, the
  phase-8 inversion rationale belongs in the Platform context block or `.design/decisions.md`
  rather than in the brief, and the "that reading is what keeps 'all five' and 'deep, not broad'
  from contradicting each other" sentence is commentary on the brief, not the brief. Closed by
  `/dsf:brief` (a revision run, which re-interrogates only the changed area) or by a direct edit
  to that block, then `/dsf:check 1` again. **Not** closed by this command — `/dsf:check` fixes
  nothing.

## Notes carried forward, not failures

- **`/dsf:brief` step 6 is a framework bug**, recorded at `.design/decisions.md` (2026-08-17,
  `contradiction`). It orders every `{{PRODUCT_NAME}}` in `index.html` replaced in the markup;
  `.design/memory/phases.md:225` permits commands to touch only the `pipeline-data` block, and
  signed-off phase-0 checklist item 8 fails on exactly that edit. The same collision blocked
  `/dsf:init` at 08:34. Resolved per `CLAUDE.md` ("when a command and that file disagree, that
  file wins"). No phase-1 checklist item tests for the placeholder's absence, so this affects no
  verdict above.
- The live page logs one console error: `GET /favicon.ico → 404`. Pre-existing, outside the
  repo's own assets, and tested by no item here.
