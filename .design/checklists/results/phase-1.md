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


---

# Re-check after reopening

Checked: 2026-08-18 · Checklist: `.design/checklists/phase-1-brief.md`
Result: **pass** — 13 pass · 0 fail · 0 human · 13 of 13 items

Triggered by the `Reopened` line at the top of this file. The 2026-08-17 verdict above it is the
record of what was originally signed off and is left intact. This section **replaces an earlier
re-check of the same reopening** (2026-08-18, 12/13, item 4 failed); that verdict was superseded
when the item was fixed in `493e760`, and is not retained — the reopening it belongs to is the
same one, so a single current re-check is the honest record rather than a stack of them.

Every item was re-verified from the repo at `493e760`. Nothing was carried over green, including
the twelve that passed hours earlier.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Brief produced by a structured brainstorm | pass | `.design/progress/phase-1.md:4` — `superpowers` brainstorming skill, 8 questions, seed taken verbatim at `:3`; gate answers verbatim in `.design/decisions.md`. Untouched by the change and the fix |
| 2 | Brief block states, each in **one or two sentences**, product / problem / audience / platform / constraints | pass | Re-counted at `493e760`: what-it-is = 2 · **Who** = 2 · **Problem** = 2 · **Platform** = 2 · **Constraints** = 2. Survived both the `/dsf:change` rewrite and the item-4 fix |
| 3 | Success criteria written and observable | pass | `CLAUDE.md` **It works if** — (1) "under 10 minutes of in-product time", Meta's external wait excluded so start and end are defined; (2) "falls 30% against the previous BSP's blended cost, measured post-migration". Unchanged throughout |
| 4 | Anything unanswered marked `[?]` with an **explicit hypothesis** | pass | **Fixed in `493e760`, the failure this re-check was called for.** Both open `[?]` now carry one: *"hypothesis **90 days**"* for the 30% window, and *"hypothesis: each gets a permission-filtered view of the Administrator's surfaces rather than a destination of its own, except `Billing Manager` and `Trial`, which probably need one"* for the roles question. The third `[?]` is struck through as closed by phase 2 rather than deleted |
| 5 | The brief names what the product is **not** doing | pass | `CLAUDE.md` **It is not** — "Another WhatsApp API SaaS" (attributed to the human), "Not a chatbot builder", "Not shared-inbox-first" |
| 6 | Folder scaffolding — exactly the twelve folders | pass | 12/12 present, checked by name. `design-system/backlog.md` sits inside an existing folder and invents none |
| 7 | `README.md` → Brief section filled in and matches `CLAUDE.md` | pass | Term-by-term at `493e760`: `keyword-flow` 2/2, "support did not answer" 1/1, "billing trapped" 1/1, "verify and exit" 1/1, "10 minutes", "30%", "desktop web", "WhatsApp API SaaS", "Administrator and Operator" all present in both. The **Corrections** line is provenance and correctly has no `README.md` counterpart |
| 8 | `index.html` renders standalone, phase 1 in progress with artifacts present, `context.product` and `oneLiner` filled | pass | Live DOM at `https://johnvijaysolomon.github.io/wati/?v=recheck2` (Pages build `493e760`): `context.product` = `"Wati"`, `oneLiner` present, phase 1 `status: in-progress`, `tagged: true`, `CLAUDE.md=true`, `README.md=true`, no `{{` in the rendered body. Standalone property unchanged since the phase-1 sign-off — four relative asset loads, fonts embedded as data URIs. **Stated limit, unchanged:** a literal `file://` open is still not executable here (Playwright blocks the `file:` protocol; a local server was denied), so it remains evidence-backed rather than directly observed |
| 9 | `.design/memory/toolbox.md` has no `[?]` in the Status column | pass | Tools table parsed row by row → `active`, `fallback`, `active`, `active`, `fallback`, `active`, `active` |
| 10 | Repo under git with the brief committed | pass | `94394e2` (the change), `bb809f0` (the failing re-check), `493e760` (the item-4 fix). `git status --porcelain` → clean |
| 11 | Pushed, since hosting is `active` | pass | `toolbox.md:43` Hosting = `active`. `git rev-list --left-right --count origin/main...main` → `0 0`; Pages build `493e760` reports `built` |
| 12 | No claim about audience or market without a source or a `[?]` | pass | The Problem is sourced through the **Corrections** line to `.design/decisions.md`, whose 2026-08-18 `change-request` entry (`:310-311`) names the evidence with figures — *"COMPETITORS difference 1 (AiSensy ₹2,500 builder vs ₹3,500 AI Agent Builder; Interakt AI Agents a ₹3,000/mo add-on) and Re-research Pass 2 Q3"* — which in turn carry links and screenshot paths in `research/research.md`. **A real weakening, recorded rather than hidden:** compressing Corrections to protect item 13 removed the direct `research/research.md` citations from `CLAUDE.md`, so the chain is now two hops (brief → decision log → research) where it was one. It still satisfies the item, and it is worse than it was |
| 13 | The brief fits on one screen | pass | `CLAUDE.md` Brief section = **56 lines**, the same as before the item-4 fix. The fix added 2 lines and the **Corrections** compression returned them. Baseline was 50 before `/dsf:change`. **The tripwire written into the previous verdict was honoured early** — Corrections moved out of the Brief block to a pointer at 58 lines rather than being allowed to reach a third growth event |

## Open

None. All thirteen items pass; the phase is ready to be re-closed on its existing tag.

## Notes carried forward, not failures

- **Item 12 is now the weakest pass in the set**, and it got weaker in this cycle rather than
  stronger. Protecting item 13 cost a citation hop. If the Brief block is ever restructured, the
  right fix is to cite `research/research.md` inline at the Problem and drop the pointer, not to
  re-expand Corrections.
- **`/dsf:brief` step 6 remains a framework bug** (`.design/decisions.md`, 2026-08-17
  `contradiction`), tested by no item here.
- **Recorded debt is open by choice:** `design-system/backlog.md` holds four phase-2 references
  that still describe the problem-statement change as pending. Phase 2 was not reopened for them.
- **Two brief-level questions remain unaddressed and outside this checklist:** the −30% criterion
  now measures value for a *secondary* persona, and email and SMS are unevidenced as inbound
  channels while the brief commits to five. Each needs its own `/dsf:change`.
