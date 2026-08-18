Reopened 2026-08-18 · by /dsf:change · the Problem statement in `CLAUDE.md` was rewritten after phase-2 evidence overturned it; items 2, 3 and 12 quote text that has changed.

# Phase 1 — Brief · check results

Checked: 2026-08-17 (re-check, replacing the 12/13 verdict of the same day) · Checklist:
`.design/checklists/phase-1-brief.md`
Result: **pass** — 13 pass · 0 fail · 0 human · 13 of 13 items

Item count verified against `.design/memory/phases.md` (**Per-phase item counts**): 13 expected,
13 found (`grep -c "^- \[ \]"`). The checklist carries no `<!-- check: … -->` executable
assertions (`grep -c "check:"` → 0). Every item below was re-verified from the repo at this run;
nothing was carried over green from the previous verdict.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Brief produced by a structured brainstorm — asked before it wrote | pass | `.design/progress/phase-1.md:4` records the `superpowers` brainstorming skill run, 8 questions; `:3` records the seed taken verbatim and not expanded. `.design/decisions.md` phase-1 `gate` entry holds the human's own words for every answer. `0719b6b` is the first commit in this phase to touch `CLAUDE.md`, and it lands after the gate line at `:5` |
| 2 | `CLAUDE.md` → Brief block states, **each in one or two sentences**, what the product is / the problem / who it is for / platform / hard constraints | pass | Re-counted after the compression in `9db6ec8`: what-it-is `:15-16` = 2 · **Who** `:18-23` = 2 · **Problem** `:25-28` = 2 · **Platform** `:30-31` = 2 · **Constraints** `:38-42` = 2. All five subjects present and all five inside the budget. (**Scope** `:33-36` = 2 and **It works if** `:44-48` = 2 are not among the item's five but were compressed with them; **It is not** `:50-51` = 3 short fragments, tested by item 5, which sets no sentence budget) |
| 3 | Success criteria written and observable | pass | `CLAUDE.md:44-48` — (1) "under 10 minutes of in-product time", with Meta's external wait explicitly excluded so the measurement has a defined start and end; (2) "falls 30% against the previous BSP's blended cost, measured post-migration". Both are countable signals, not adjectives |
| 4 | Anything unanswered marked `[?]` with an explicit hypothesis | pass | `CLAUDE.md:53-57` — three `[?]`, each with a hypothesis and a named confirmer: 30% window → hypothesis 90 days, confirmed by the human or a phase-2 benchmark; non-designed roles → `ia/sitemap.md`; "the AI is fake" → phase-2 first-hand competitor capability |
| 5 | The brief names what the product is **not** doing | pass | `CLAUDE.md:50-51` — "Another WhatsApp API SaaS" (attributed to the human), "Not a chatbot builder", "Not shared-inbox-first". Scope boundary also stated positively at `:33-34` — inbox and campaigns secondary |
| 6 | Folder scaffolding — exactly the twelve folders in `phases.md`, none missing, none invented | pass | All twelve present (`research`, `people`, `ia`, `wireframes`, `voice`, `concept`, `ui`, `design-system`, `visuals`, `responsive`, `animations`, `handoff`). Top-level diff against the canonical list minus pre-existing `assets/` and `docs/` → no invented folders. Six named subfolders (`research/screens`, `design-system/{components,patterns,docs,examples}`, `handoff/spec`) come from the `/dsf:brief` step-5 tree |
| 7 | `README.md` → Brief section filled in and matches `CLAUDE.md` | pass | `README.md:22-47` re-checked against the compressed block: same primary user, same problem, same five channels with the same connect/configure/monitor/govern framing, same platform + phase-8 inversion, same two success criteria with the same numbers and the same Meta exclusion, same three anti-goals. Spot-checked term by term — `Administrator`, `AiSensy`, `10 minutes`, `30%`, `desktop web`, `WhatsApp API SaaS` all present in both. The compression removed no fact from `CLAUDE.md` that `README.md` still asserts |
| 8 | `index.html` renders standalone, shows phase 1 in progress with artifacts present, `context.product` and `oneLiner` filled | pass | Re-evaluated in the live DOM at `https://johnvijaysolomon.github.io/wati/?v=recheck`: `context.product` = `"Wati"`, `oneLiner` present, phase 1 `status: in-progress`, `tagged: false`, `CLAUDE.md=true`, `README.md=true`, and `document.body.innerText` contains no `{{`. Standalone verified structurally: the only four asset loads are relative (`index.html:48,49,3365,3366` → `assets/`), `fonts.css` embeds both faces as `url(data:font/woff2;base64,…)`, and the sole `http://` in `assets/pipeline.js` is the SVG namespace string, not a request. **Stated limit, unchanged:** a literal `file://` open was not executed — the Playwright MCP blocks the `file:` protocol and a local static server was denied by the sandbox — so the no-external-request property is evidence-backed rather than directly observed |
| 9 | `.design/memory/toolbox.md` has no `[?]` in the Status column | pass | Tools-table Status column parsed row by row → `active`, `fallback`, `active`, `active`, `fallback`, `active`, `active`. The four `[?]` in the file are at `:25`, `:27`, `:71`, `:91` — all prose in the status-vocabulary table and the fallback rules, none in a tool row |
| 10 | Repo under git with the brief committed | pass | `0719b6b` (brief + scaffolding), `053a653` (ledger), `0d25c79` (first verdict), `9db6ec8` (compression closing item 2). `git status --porcelain` → clean |
| 11 | Pushed, since `toolbox.md` records hosting as `active` | pass | `toolbox.md:43` Hosting = `active`. `git rev-list --left-right --count origin/main...main` → `0 0`. Confirmed downstream: the Pages build for `9db6ec8` was accepted and the live page serves the current data block |
| 12 | No claim about audience or market appears without a source or a `[?]` | pass | `CLAUDE.md:12-13` sources the whole block to the gate ("Verbatim trace: `.design/decisions.md`"), where every audience fact appears in the human's own words. The one market claim that is not the human's direct experience — competitor AI capability, `:25-26` — is explicitly downgraded at `:55-57` as "the human's diagnosis, not yet a sourced finding". **Weakest pass in the set, unchanged by the compression:** that `[?]` sits below the claim rather than inline, so a reader hitting `:25` reads it as fact. Sourced and marked as the item requires, but not at the point of use. Phase 2 closes it with evidence rather than with wording |
| 13 | The brief fits on one screen | pass | `CLAUDE.md:10-59` = 50 lines including blanks. It was 66 when first written, compressed to 50 at `brief.4` for this item, and held at 50 through the item-2 compression in `9db6ec8` — sentences came out, line count stayed flat because the paragraphs re-wrapped |

## Open

None. All thirteen items pass; the phase is ready for the sign-off gate.

## Notes carried forward, not failures

- **`/dsf:brief` step 6 is a framework bug**, recorded at `.design/decisions.md` (2026-08-17,
  `contradiction`). It orders every `{{PRODUCT_NAME}}` in `index.html` replaced in the markup;
  `.design/memory/phases.md:225` permits commands to touch only the `pipeline-data` block, and
  signed-off phase-0 checklist item 8 fails on exactly that edit. The same collision blocked
  `/dsf:init` at 08:34. Resolved per `CLAUDE.md` ("when a command and that file disagree, that
  file wins"). No phase-1 checklist item tests for the placeholder's absence, so this affects no
  verdict above — but the command file is wrong and has now been wrong twice.
- **Item 12 is the one to watch.** It passes as written, and the claim it covers — that the
  competitors' AI is a keyword bot — is load-bearing for the entire brief. `/dsf:research` should
  treat closing it as a first-class job, not a footnote.
- The live page logs one console error: `GET /favicon.ico → 404`. Pre-existing, outside the
  repo's own assets, tested by no item here.
