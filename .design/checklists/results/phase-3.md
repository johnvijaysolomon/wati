# Phase 3 — Structure · check results

Checked: 2026-08-19 · Checklist: `.design/checklists/phase-3-ia.md`
Result: **fail** — 21 pass · 1 fail · 0 human · 22 of 22 items

Item count verified against `.design/memory/phases.md` (**Per-phase item counts**): 22 expected,
22 found (`grep -c "^- \[ \]"`). No `<!-- check: … -->` executable assertions (`grep -c "check:"`
→ 0), so every verdict is a file read, a command output or a live-DOM evaluation.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Entities listed, each tied to a job; objects with no job in a separate "questionable" section | pass | `ia/sitemap.md` **Entities** — 11 entities, each naming the `jtbd.md` job that produces it. `:44` **Questionable** holds 3 with no job: `User/role` (the brief demands it, no job produces it), `Template` (the campaign composer was cut at `users.4`, so nothing sends outbound), `Contact` (every competitor has one, no job needs one) |
| 2 | Screen hierarchy derived from the product's own jobs, not a competitor's menu | pass | Every screen in the tree carries a job id. Structural evidence that it is not a copy: there is **no per-conversation queue for the primary persona** and no campaign surface — both are category defaults, and both were excluded by name with reasons (`research.4` pattern gate; `users.4` cut list) |
| 3 | Every screen annotated with the job it serves; screens with none marked `[ORPHAN]` | pass | 32 annotated lines in the tree; `ORPHAN` appears 7× across the tree, the traceability table and the resolution. Exactly one screen carries it: `People and access` |
| 4 | Screens and states not confused — empty/error/loading are states, never separate screens | pass | Grep for state-named screens in the tree → **0**. The tree states the rule inline ("Empty, error and loading are **states**, not screens — they belong in `wireframes/_screens.md`"), and the `ia.6` fix table records two specific states against their screens (`Validation` in-progress, `Export` empty) rather than inventing screens for them |
| 5 | Global navigation, 3–5 items, each justified by its job | pass | 5 items, each with a job cluster and a "why it earns a global slot" column. A sixth, `Inbox`, is explicitly **permission-gated on the Operator role** rather than counted in the five — the first concrete use of the brief's ten-role model |
| 6 | Tap depth from first screen to the main job counted for the primary persona | pass | `ia/sitemap.md` **Navigation** — a 7-row table of counted paths, primary persona named |
| 7 | Main job reachable within three taps, or the extra depth explicitly argued | pass | Main = **0** (landing screen), within budget. **Passes on a number the artifact itself argues is meaningless:** an honesty note states that a budget met by declaring the landing screen the answer is usually a budget being gamed, that the main job is closed by the AI working rather than by a screen, and that the counts later phases should be held to are the MVP-core ones — **R1 = 3, R2 = 1–2, R5 = 2**. R1 sits exactly at the limit on the same job the brief's 10-minute criterion measures |
| 8 | Main-job flow in Mermaid: screen steps, decision diamonds, empty/error/loading, both endings | pass | `ia/flows.md` Flow 1 — 5 screen nodes, 4 decision diamonds, 2 empty + 1 error + 2 loading states as their own nodes, and both endings: 2 successes and 1 dead end (the channel out of the buyer's hands) |
| 9 | 2–3 key related-job flows also drawn | pass | 4 flows total (`grep -c "^## Flow "` → 4): Main plus R1, R2, R5 — the three MVP-core jobs. Four rather than three because the core has three members and leaving one undrawn would hide it |
| 10 | Every screen node in every flow exists in `ia/sitemap.md`; screens discovered while drawing added back | pass | 17 distinct screen nodes extracted from the four diagrams and matched against the tree → **17/17 present, 0 missing**. `flows.md` records "Nodes added while drawing: None" — nothing was discovered late |
| 11 | Mermaid syntax valid — diagrams render as diagrams, not raw code blocks | pass | Proven twice, not asserted: all four extracted and rendered with `@mermaid-js/mermaid-cli@11` without error, before and again after the `ia.6` fixes; and in the live DOM, 4 `<svg>` elements with 24/19/24/18 nodes and `document.body.innerText.includes('flowchart TD')` → **false** |
| 12 | Coverage matrix with jobs as rows, screens as columns | pass | `ia/sitemap.md:204` **Traceability** — 10 job rows × 21 screen columns, 40 ticks |
| 13 | Orphan screens and orphan jobs listed explicitly | pass | `:229` **ORPHAN SCREENS** (1: `People and access`) and `:235` **ORPHAN JOBS** (2: S1, S2), each in its own table |
| 14 | Each orphan has a decision | pass | `People and access` → keep at Deep level, orphan status visible, revisit when phase 2's roles `[?]` closes. S1 → backlog, becomes a voice problem at phase 5. S2 → backlog, served incidentally. None deleted quietly, none given an invented job |
| 15 | Critique pass covering four defect classes recorded, checked against the existing matrix | pass | `.design/progress/phase-3.md` `ia.6` records the pass, the gate answer, the 9 defects across the four classes and their disposition; `ia/sitemap.md:117` records the five applied fixes with the defect id each closes; the orphan classes reconcile against the existing matrix rather than a new one (O1/O2 point at the tables at `:229`/`:235`). **Weakest pass in the set:** the substance of all nine findings is in the repo but **distributed** across `sitemap.md`, `CLAUDE.md` and `ia/ia.html` — there is no single place to read "what the IA critique found". The framework defines a critique artifact for phase 4 (`wireframes/_critique.md`) and none for phase 3, so this is a gap in the framework rather than a deviation from it; a phase-3 equivalent would be worth adding |
| 16 | Dead ends and missing states fixed, and the fix visible in the flows | pass | Three dead ends and two missing states approved at the gate and applied: **D1** the "nobody on duty" dead end replaced by a Handover fallback reply plus an `Overview` signal; **D2** channel failure now raises channel health on `Overview` before `Channel detail`, with a recoverable/unrecoverable split; **D3** the "waiting on Meta with nothing to do" branch removed as the competitor's behaviour drawn as ours, replaced by a real dead end (a number bound to another BSP); **M1** `Validation` gained the "Looking good" in-progress state; **M2** `Export` gained an empty state. All five visible in the diagrams, and all four re-rendered clean afterwards |
| 17 | `ia/ia.html` opens standalone with the screen tree, **live-rendered Mermaid diagrams** and the coverage matrix visible | **fail** | Two of three conjuncts hold: the page is standalone (0 external `script[src]` / `link[href]`, inline CSS only, no horizontal overflow) and the tree and matrix are visible (matrix shows 40 ticks with 2 orphan rows and 1 orphan column highlighted). **The diagrams are not live-rendered.** They are pre-rendered to SVG with `mermaid-cli` and inlined; the Mermaid library never runs in the page, so `/dsf:ia` step 7's "initialized on the dark theme" describes something that does not happen. The substitution was made to satisfy the no-CDN rule in `phases.md` — **but that rule did not force it.** Vendoring `mermaid.min.js` into `assets/` would satisfy both: the library would then be "already in the repo" and the page would still request nothing external. A cheaper route was taken and the item asks for the other one |
| 18 | `CLAUDE.md` → **Structure** block records the main flow and the navigation model | pass | Records the 5 global items with their job clusters, the permission-gated sixth, the tap-depth budget with the MVP-core counts named as binding, the main flow end to end, five structural decisions later phases must not undo, and the open orphans |
| 19 | `README.md` → Structure section links to `ia/ia.html` | pass | `README.md` **Structure** → `./ia/ia.html`, with a three-sentence summary rather than a bare link |
| 20 | `index.html` data block regenerated — phase 3 artifacts marked present | pass | Parsed from the block: `ia/sitemap.md`, `ia/flows.md`, `ia/ia.html` all `exists: true`; `ia.html` carries `link: true`; `steps` 10/10 with `current: ""`. `context` untouched — this phase fills none of its keys, and `chosenDirection` is still `""` |
| 21 | Phase committed; pushed since hosting is `active` | pass | `toolbox.md:43` Hosting = `active`. Commits `5cb8df4`, `5495ed5` and the ledger close. `git status --porcelain` → clean; `git rev-list --left-right --count origin/main...main` → `0 0`; Pages build `5495ed5` reports `built` |
| 22 | *(second half of item 21's section — pushed if hosting active)* | pass | Same evidence as item 21; the checklist's final section carries both a commit item and a push item and both are satisfied |

## Open

- **Item 17** — the diagrams are not live-rendered Mermaid. Two ways to close it, and they are
  genuinely different decisions rather than a fix and a workaround:
  1. **Vendor the library.** Add `mermaid.min.js` to `assets/`, keep the ```mermaid``` source in the
     page, and initialize on the dark theme. Satisfies the item as written and keeps the page
     self-contained. Cost: roughly 1 MB of vendored JS committed to a public repo, and the page
     stops rendering if the script fails.
  2. **Accept the substitution.** Pre-rendered SVG is self-contained, needs no JS, renders on any
     browser, and is the same artifact whose successful render proves the Mermaid valid. Cost: the
     checklist item is knowingly failed and logged as an accepted exception.
  Closed by `/dsf:ia` (a re-run of step 7) for route 1, or by a decision logged in
  `.design/decisions.md` for route 2. **Not closed by this command** — `/dsf:check` verifies and
  never fixes.

## Notes carried forward, not failures

- **Item 7 passes on a 0 the artifact itself distrusts.** The binding numbers for later phases are
  R1 = 3 (at the limit), R2 = 1–2, R5 = 2. A fourth setup step breaches this budget and the brief's
  10-minute success criterion in the same move.
- **Item 15's finding, restated because it is a framework gap:** phase 4 has a canonical critique
  artifact and phase 3 does not, so the IA critique lives distributed across three files. Worth an
  `ia/_critique.md` in the framework.
- **`[?]` email and SMS are now structural.** They appear under `Channels` on the brief's authority
  alone; phase 2 found no evidence the primary persona's customers arrive there. Phase 4 will draw
  states for channels the evidence does not support. Needs its own `/dsf:change`, together with the
  withdrawn TikTok request in `design-system/backlog.md`.
- **Deferred to phase 4 by the `ia.6` gate:** whether `Answers` is a real screen or a navigation
  container (defect A1). If it holds nothing but links it collapses into the nav and its two
  matrix ticks move to its children.
- **Phase 1 remains open**, passing 13/13 since 2026-08-18 and awaiting only the sign-off gate.
