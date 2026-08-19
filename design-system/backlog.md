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

### 2026-08-18 · TikTok as a sixth channel — withdrawn, not rejected

**What was asked.** At the `/dsf:ia` sitemap gate the human asked for `Channels` to contain
"instagram, messenger, tiktok, email, sms etc." Messenger needed no decision — the brief already
covers it as "Facebook DM". **TikTok is a sixth channel and the brief enumerates five**, so the
rule-12 guard fired and the human chose **withdraw**.

**Why it was not taken.** The brief already carries two channels on its own authority — phase 2
could evidence WhatsApp (78% of Indian SMBs) and Instagram generically, but found **no evidence
that email or SMS are inbound channels for the primary persona**. TikTok would have made three of
six unevidenced. Separately, `[?]` whether TikTok business messaging is reachable through an API a
BSP could integrate is unverified by this research — the connector would have been designed for a
capability nobody confirmed exists in that form.

**What would let it in.** Two things, in this order: (1) evidence that P1's customers actually
arrive on TikTok — a review, a case study or a channel-share figure for this segment; (2) a
verified integration path. Then `/dsf:change` against the brief's channel list, which is a change
that should be taken **together with** the outstanding email/SMS evidence gap rather than
separately — both touch the same line of the brief.

**Where the related debt lives.** `.design/checklists/results/phase-2.md` → *Carried forward*
records the email/SMS gap. Fold TikTok into that change when it is taken.
