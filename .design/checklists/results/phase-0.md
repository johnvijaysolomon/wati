# Phase 0 — Init · check results

Checked: 2026-08-17 · Checklist: `.design/checklists/phase-0-init.md`
Result: **pass** — 12 pass · 0 fail · 0 human · 12 of 12 items

Checked against the repo at `e2c2d71`, after the `/dsf:init` re-run of 2026-08-17 09:30 that
revised three toolbox rows and switched hosting to GitHub Pages.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Every Tools row is `active` or `fallback`; no `[?]` survives | pass | Embedded assertion run verbatim: `awk '/^## Tools/,/^## Rules/' .design/memory/toolbox.md \| grep -cF '`[?]`'` → `0`. Seven rows: Browser `active`, Visual references `fallback`, Design quality laws `active`, Structured brief `active`, Imagery `fallback`, Icons `active`, Hosting `active` |
| 2 | Every `active` row has detection evidence, every `fallback` row its reason, in **Notes** | pass | `toolbox.md:109,114,121,127,134,139,150` — one Notes entry per row, each naming its evidence or reason. Sample: `:121` records `claude plugin list` plus verification that `plugin/skills/impeccable/SKILL.md` maps all four required passes; `:114` records `ToolSearch "+refero"` → no tools |
| 3 | **Rules for later phases** states operationally what each `fallback` means downstream | pass | `toolbox.md` Rules section — 2 fallback rules (Visual references, Imagery) plus 3 activation obligations for the rows that changed to `active`. Each is an instruction, not a restatement: e.g. the hosting rule tells later phases a phase is not done until its artifact is reachable at the public URL, and that the repo is world-readable |
| 4 | Git repo initialized; remote configured **or** local-only fallback recorded | pass | `git rev-parse --is-inside-work-tree` → `true`; `git remote get-url origin` → `https://github.com/johnvijaysolomon/wati.git` |
| 5 | Hosting decided: Pages enabled with the URL recorded, **or** local fallback recorded | pass | Pages API → `https://johnvijaysolomon.github.io/wati/`, source `main` / root, `status=built`, HTTPS enforced. URL recorded at `toolbox.md:94` (rule) and `:163` (note); the HTTP 422 that forced the private→public decision is recorded at `:155-161` |
| 6 | `index.html` renders: phase 0 `in progress`, 1–10 `locked`, every artifact missing | pass | Rendered live in Playwright at `https://johnvijaysolomon.github.io/wati/` (deployed `e2c2d71`). DOM: `[data-nav="0"]` → `status="in-progress"`; navs 1–10 all `status="locked"` (10 of 10); all 54 artifacts `exists: false`; footer "0 of 11 phases done" |
| 7 | Data block holds all eleven phases with canonical paths, and a `context` of empty strings | pass | Parsed block: 11 phases matching the 11 rows of `phases.md`; every backticked file path in that table's Key-artifacts column is present in the matching phase. All six `context` strings `""`, plus the sanctioned non-string `toolbox` key. Three paths were absent before this run and were added by `/dsf:init`: `wireframes/wireframes.css`, `ui/tokens-audit.md`, `handoff/README.md` |
| 8 | Nothing outside the data block edited in `index.html`, nothing in `assets/` | pass | Verified against the pristine upstream template, not against local history. `assets/fonts.css`, `pipeline.css`, `i18n-uk.js`, `pipeline.js` each byte-identical to `denysosadchyi/design-spec-framework@main` (`cmp -s` → identical ×4). `index.html` split at the data block: markup before and after both byte-identical to upstream (`diff` → no differences). Only the JSON block differs |
| 9 | `CLAUDE.md` **Toolbox** lists one line per `active` and per `fallback`; context blocks still `[?]` | pass | `CLAUDE.md` Toolbox section: 5 `active` entries, 2 `fallback` entries, matching `toolbox.md` row for row. Context blocks untouched: 12 `[?]` lines, one per phase block |
| 10 | `README.md` present from the template, with the `index.html` link if hosting is active | pass | `README.md:16-18` — Pages URL and the local `[index.html](index.html)` link. Hosting is `active`, so the public URL is required and present |
| 11 | First commit made; pushed only if hosting is `active` | pass | `2c5b0f6` (initial), `64284b6` (re-run), `e2c2d71` (ledger close). Hosting `active`, so the push is required: `git rev-parse HEAD` = `git rev-parse origin/main` = `e2c2d71`; working tree clean |
| 12 | The designer was handed their project page: link, what it is for, the one first move | pass | `.design/progress/phase-0.md` → `init.9` line, plus the handover message itself: the live URL, the "state view of the pipeline / the page tracks state, the chat executes" explanation, and one named first move. **Deviation, disclosed:** the move named was `/dsf:check 0`, not the checklist's parenthetical `/dsf:brief` — see Notes |

## Open

None. No item failed and no item was left unresolved.

## Notes — three template inconsistencies found, none of them project defects

These are defects in the framework template itself, surfaced while verifying. They are recorded
here so the next project built from the template does not rediscover them, and are logged in
`.design/decisions.md` under the 2026-08-17 correction entry.

1. **`init.md` step 6 orders an edit that checklist item 8 forbids.** Step 6 says to substitute
   `{{PRODUCT_NAME}}` "in the markup and in `context.product`"; item 8 says nothing outside the
   data block may be edited. The substitution is also unnecessary: `assets/pipeline.js:618-622`
   fills `document.title` and every `[data-product]` node from the JSON, and `:619` explicitly
   handles the un-substituted `{{` placeholder. The first run followed step 6 and failed item 8;
   the re-run restored the markup, which is why item 8 now verifies byte-identical to upstream.
   Item 7 independently requires `context.product` to stay `""`, contradicting step 6 a second
   time. **The template's own renderer settles it: the markup placeholder should be left alone.**
2. **Checklist item 12 names `/dsf:brief` as the first move, but phase 0 is not closable without
   `/dsf:check 0`.** The dashboard's own phase-0 Result panel renders "run `/dsf:check 0` to
   verify", and `phases.md` **States** makes a phase *done* only with a results file and a tag —
   both of which only `/dsf:check` produces. Naming `/dsf:brief` at handover would have skipped
   the gate. Item 12 is passed on substance: link, explanation and exactly one move were given.
3. **Three canonical artifacts were missing from the shipped `pipeline-data` block** —
   `wireframes/wireframes.css`, `ui/tokens-audit.md` and `handoff/README.md` — despite the first
   being listed in the *"Canonical paths — the ones that used to drift"* table of `phases.md`.
   Added during the re-run, so item 7 passes.
