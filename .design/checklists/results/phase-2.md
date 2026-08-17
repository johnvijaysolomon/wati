# Phase 2 — Discover · check results

Checked: 2026-08-17 · Checklist: `.design/checklists/phase-2-discover.md`
Result: **pass** — 25 pass · 0 fail · 0 human · 25 of 25 items

Item count verified against `.design/memory/phases.md` (**Per-phase item counts**): 25 expected,
25 found (`grep -c "^- \[ \]"`). The checklist carries no `<!-- check: … -->` executable assertions
(`grep -c "check:"` → 0). Both sub-commands have run — `/dsf:research` (`research.1`–`research.9`)
and `/dsf:users` (`users.1`–`users.10`), 19/19 steps in `.design/progress/phase-2.md`.

| # | Item | Verdict | Evidence |
|---|---|---|---|
| 1 | Competitors in three groups, ≥5 products named | pass | `research/research.md:28,37,45` — three group headings; 12 products in the matrix (`grep -c '^\| \*\*[A-Z]'` → 29 rows incl. criteria/pattern tables; 12 distinct products named). **Framework note, not a defect:** the checklist says "direct, adjacent, aspirational" while `/dsf:research` and the artifact say "Hard, Soft, Aspirational". Same three groups, same semantics, different vocabulary in two framework files |
| 2 | Comparison matrix: products as rows, dimensions as columns, cells from collected data | pass | `research/research.md:55` **Comparison matrix** — 12 product rows × the five fixed axes (audience, product core, key mechanic, trust, monetization) + a Source column. Every cell carries a link or a screenshot path; unreachable cells are `[?] unverified` with a hypothesis, and Agentforce's row is labelled `access restricted` (HTTP 403) rather than filled |
| 3 | One benchmark dimension across categories: 6–8 criteria, 4–5 products, each scored | pass | 8 criteria rows and 5 scored products (`grep` → 8 criteria + 5 pattern rows = 13; 5 product rows matched by name). **All five are from outside customer service** — LangSmith, Stripe Radar, Sentry, Google Search Console, Datadog SLOs, exceeding the "at least two" requirement. Unsourced cells are `[?]` and excluded from both numerator and denominator, so each product reports `score / scoreable` and Datadog's rank is declared provisional at 4-of-8 |
| 4 | Five genuinely different patterns, one chosen, argued from this product's context | pass | `research/research.md` PATTERNS — 5 rows (`grep -c '^\| [1-5] \| \*\*'` → 5), differing in **mechanism** not layout: item-by-item / grouped-by-cause / statistical sample / counterfactual replay / natural-language authoring. Chosen = clustered themes, with three reasons each quoting `CLAUDE.md` (the inbox is "an exception surface", five channels, success is a rate). Queue triage disqualified with a reason; sampled audit named as conditional second |
| 5 | Hypotheses to test later, listed and numbered | pass | `research/research.md` CONCLUSIONS → 5 numbered hypotheses, each naming the phase that tests it. Separately `people/jtbd.md` **Hypotheses** holds H1–H4, each with what would confirm it and where to look |
| 6 | `research/screens/` holds screenshots of the products discussed, referenced by filename from `research.md` | pass | 6 `.png` present, 6 referenced (`grep -o "research/screens/…"` → 6 unique = `ls` → 6). No orphans in either direction. **Coverage stated rather than implied:** 6 of 12 products are captured, because every in-product Administrator surface in this market is behind a login this project does not have — the artifact says so in its header and labels the gaps |
| 7 | Every fact and number carries a link, a screenshot path, or "unverified" | pass | Matrix rows all carry a Source column; prose claims carry inline `([source](…))`; `[?] unverified` used 13× with an explicit hypothesis attached. **The one weak instance, named:** in COMPETITORS shared-pattern 2 the Zendesk figure *"Resolve up to 80%+"* has no inline link of its own — it is linked in Zendesk's matrix row instead. Traceable within the document, but not at the point of use |
| 8 | `research/research.html` opens standalone and links its screenshots | pass | Rendered at `https://johnvijaysolomon.github.io/wati/research/research.html` (Pages build `ef27df5`) and evaluated in the live DOM: 6 images, **0 broken**, 5 tables, 15 `[?]` marks and 1 `access restricted` label visible, no horizontal overflow. Standalone verified structurally: `grep -nE '<(script\|link)[^>]*(src\|href)='` → no external script or stylesheet; the only 6 absolute URLs are outbound `<a href>` source citations, and all `img src` are relative into `screens/` |
| 9 | `people/personas.md` holds 2–4 behaviour-based personas | pass | 3 personas (`grep -c '^## Persona [0-9]'` → 3), each named as a stance rather than a bracket: "the one who has already failed once", "the one who owns the number", "the one who gets called when it breaks". A **Merged personas** section records two rejected splits — geography (same jobs and pains, differing only in currency and timezone) and the Campaign/Template Manager roles (roles in the brief, not behaviours in the evidence) |
| 10 | Exactly one persona marked primary, with a stated reason | pass | `people/personas.md:22` — `**PRIMARY**` appears exactly once (`grep -c` → 1). Reason at `:24`: chosen by the human at the `users.2` gate over the recommended Persona 2, evidence over inference. Both non-primary personas carry an explicit "Why not primary" |
| 11 | Every persona block points at a specific place in `research.md` or carries `[?]` | pass | 11 `source:` attributions citing observation ids `R1`–`R8` in `research/research.md` → *Re-research after personas*, plus named COMPETITORS / BENCHMARK findings and two screenshot paths. Unsourced blocks carry `[?]` phrased as a hypothesis — Persona 3's pains, trust triggers and quote are all marked, and its quote is left **empty rather than composed** |
| 12 | `people/jtbd.md`: 1 main job, 3–5 related, all in "when / I want / so that", none named after a feature | pass | 1 main job + 5 related, all 5 matching the full `**When** … **I want** … **so that**` form. Feature-noun check run against "I want" clauses for dashboard/builder/inbox/queue/button/screen/widget/report/template/composer → **0 hits** |
| 13 | Emotional and social jobs listed separately from functional | pass | `people/jtbd.md:31` Related jobs · `:45` **Emotional jobs** (E1–E2) · `:54` **Social jobs** (S1–S2) — three distinct sections |
| 14 | Each job records where it came from | pass | Every row in the related, emotional and social tables carries a Source column entry (9 rows checked). Jobs with no data behind them are not in these tables at all — they are in **Hypotheses** (H1–H4) with what would confirm them |
| 15 | Jobs × personas × features matrix, with a column for whether competitors cover the job | pass | `people/jtbd.md` **Matrix** — 10 job rows × 3 persona columns + **FEATURE** + **COMPETITORS — already closed?**. 8 cells left `[?]` rather than averaged, per the template's own rule. Persona cells carry `<1–3> · <the place that shows it>` rather than a bare number |
| 16 | Matrix ends in a conclusion: three MVP-core jobs, and features that serve nothing named as cut candidates | pass | `:99` **MVP core — three jobs** (3 numbered entries, each citing the matrix score and coverage rather than re-arguing them) · `:121` **Cut candidates** — 5 features with the job each was assumed to close and why it closes nothing. The section also names what it excludes and why: the main job is table stakes, and R3 misses the core as a direct consequence of the `users.2` persona flip |
| 17 | A confirmed / hypothesis / invented audit of the persona and job claims is recorded | pass | `people/personas.md:197` **Self-critique** — 16 persona statements + 10 jtbd statements = 26 classified. Counts declared in the file header: 7 confirmed / 7 hypothesis / 1 absent. One row records a claim that was **removed rather than relabelled** ("inherited rather than chose" → *invented — removed*) |
| 18 | Claims that drive design decisions but rest on `[?]` are called out explicitly | pass | `people/personas.md:240` **The dangerous subset** — 5 items ordered by what they would cost if wrong. The top two are unverified matrix cells each carrying a scope decision: R4's score of 1 sits under the project's largest build commitment, and R3's score of 2 is what kept the benchmark dimension's own job out of the MVP core |
| 19 | At least one gap closed by targeted follow-up research, visible in `research/research.md` | pass | `research/research.md:324` **Re-research after personas**, in two passes: `:333` Pass 1 (R1–R8, customer voice) and `:413` Pass 2 (the three questions from the self-critique). Q3 returned a **negative finding** that changed the phase's conclusions; a *What changed after the targeted re-research* table in `people/personas.md` records one `[?]` dropped with a source, two narrowed and explicitly left open, and none un-marked without evidence |
| 20 | `[?]` marks survive into `people/personas.html` — visible, not tidied away | pass | Live DOM at `https://johnvijaysolomon.github.io/wati/people/personas.html` (build `e26cece`): **24** `.q` elements, plus 7 `hypothesis` and 7 `confirmed` labels rendered inline. The dangerous subset and the twice-contradicted brief statement are both rendered as visible callouts, not footnotes |
| 21 | `people/personas.html` opens standalone in a browser | pass | Same live evaluation: title `Wati · People`, 4 tables, exactly 1 `.card.primary`, **0 external `script[src]` / `link[href]`** (inline CSS only), no horizontal overflow, all 3 links relative (`../research/research.html`, `../index.html`) |
| 22 | `CLAUDE.md` → **People** block names the primary persona and the main job | pass | `CLAUDE.md` → *Context blocks* → **People**: names the primary persona and the main job verbatim, plus the top-3 MVP jobs, the five cuts, and two consequences later phases must not rediscover (the −30% criterion now belongs to a secondary persona; replay only survives if it costs seconds inline) |
| 23 | `README.md` → Research and People sections link to the HTML pages | pass | `README.md:61` → `./research/research.html` · `:74` → `./people/personas.html`, each with a two-to-three-sentence summary rather than a bare link |
| 24 | `index.html` data block regenerated — phase 2 artifacts present, `context` carries the benchmark dimension, the primary persona and the main job | pass | Parsed from the live block: `context.benchmarkDimension`, `context.primaryPersona` and `context.mainJob` all non-empty; all **6** phase-2 artifacts `exists: true`; `personas.html` carries `link: true`; `steps` 19/19 with `current: ""`. `status` and `tagged` untouched by this step, per the command |
| 25 | Phase committed; pushed since hosting is `active` | pass | `toolbox.md:43` Hosting = `active`. `git status --porcelain` → clean; `git rev-list --left-right --count origin/main...main` → `0 0`. Phase-2 commits: `ef27df5` (2a), `22dfac6` (2a ledger), `e26cece` (2b), `7d660cc` (impeccable scope). Pages build `e26cece` reports `built` and both artifact pages serve live |

## Open

None. All twenty-five items pass; the phase is ready for the sign-off gate.

## Carried forward, not failures

These are recorded because the next phase inherits them, not because any item failed.

- **The brief's problem statement has been contradicted twice** and no checklist item tests for
  it. Phase 2a: the incumbents' AI exists and is an upsell on a keyword-flow core, not absent.
  Phase 2b Q3: searching specifically for people who left over bad AI answers found **none** —
  the corpus records absent support, billing traps and platforms that did not work. `CLAUDE.md`
  and `README.md` still carry the original wording, deliberately unpatched. **Closes with
  `/dsf:change`**, which sizes the blast radius; a phase command editing a signed-off artifact
  silently is the failure that rule exists to prevent.
- **Two `[?]` in the dangerous subset carry scope decisions** and survive this pass by design:
  R4's importance to Persona 1 (narrowed at `users.6` to "replay must cost seconds inline", not
  closed) and R3's importance to Persona 1 (the cell that kept the benchmark dimension's own job
  out of the MVP core).
- **Email and SMS are unevidenced as inbound channels** for the primary persona. WhatsApp is
  confirmed (78% of Indian SMBs), Instagram is supported generically; the brief commits to five
  channels and two of them rest on its authority alone. Phase 3 will build IA for all five.
- **A discovered platform constraint** the brief records as absent: effective 2026-01-15 Meta bars
  "AI Providers" from distributing general-purpose assistants over the WhatsApp Business Solution.
  On the evidence it does **not** bar this product — Meta named the carve-out explicitly — but the
  brief's "no legal or regional fence stated" is no longer strictly true. Recorded at
  `research/research.md` R8 with the residual risk marked `[?]`.
- **`/dsf:brief` step 6 remains a framework bug** (`.design/decisions.md`, 2026-08-17
  `contradiction`), untouched by this phase and tested by no item here.
- **One `impeccable` finding suppressed**, disclosed rather than silently ignored:
  `side-tab` scoped to `people/personas.html` in `.impeccable/config.json`, on the grounds that the
  flagged line is a 2px neutral rule on a `<blockquote>` in a long-form document. The reason field
  records "Not user confirmed".
