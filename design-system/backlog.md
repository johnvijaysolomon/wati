# Backlog

Things the system knows about and has not done. Phase 7 (`/dsf:system`) owns this file; it was
created early, at a `/dsf:change` partial-scope gate, because debt with no home is a surprise
rather than debt (constitution rule 6, and `/dsf:change` step 4).

---

## Recorded debt

### 2026-08-18 · Four phase-2 references describe a resolved change as pending

**What is stale.** The brief's problem statement was corrected on 2026-08-18 by `/dsf:change`
(partial scope). Four places written before that still describe the correction as something owed:

| File | Line | What it says |
|---|---|---|
| `people/personas.md` | 44 | "This is a `/dsf:change` against the brief, not a decision this file can make." |
| `people/personas.html` | 325 | "belongs in `/dsf:change` against the signed-off brief, not in a quiet patch here." |
| `research/research.md` | 469 | "against a signed-off artifact and belongs in `/dsf:change`, not in a patch here." |
| `.design/checklists/results/phase-2.md` | 52 | "**Closes with `/dsf:change`**, which sizes the blast radius" |

**Why it was not fixed.** Each sentence is **accurate as history** — it records what was true when
it was written. Editing them means touching phase-2 artifacts, which reopens phase 2 under
`/dsf:change` step 6 and costs a re-check of all **25** checklist items. The human took partial
scope at the 2026-08-18 gate rather than pay that to remove four sentences.

**Risk if left.** A reader of `people/personas.html` or `research/research.html` sees the
contradiction presented as unresolved and may re-raise a change that has already been made.
`CLAUDE.md` → **Brief** → **Corrections** is the authority; these four are commentary.

**What closes it.** Either the next `/dsf:change` that reopens phase 2 for another reason — fold
these edits into that blast radius for free — or `/dsf:users`, if it is re-run for any reason, at
which point the sentences are rewritten in the same pass. Do not reopen phase 2 solely for this.

**Not in this debt, and deliberately so.** Phase 2 also found that **email and SMS are unevidenced
as inbound channels** for the primary persona while the brief commits to five. That is a separate
change to a different part of the brief, was named out of scope at the 2026-08-18 restatement, and
is recorded in `.design/checklists/results/phase-2.md` → *Carried forward*. It needs its own
`/dsf:change`, not a line here.
