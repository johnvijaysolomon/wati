<!-- filled by /dsf:ia — started from .design/templates/flows.md, structure unchanged -->

# Flows

**The main-job flow, complete, plus 2 to 3 key related-job flows** from `jtbd.md`. One
`flowchart TD` per flow, each under a heading naming its job.

Four flows: the main job, plus the three **MVP-core** jobs fixed at the `users.4` gate — R1, R2
and R5. Screen nodes are named exactly as in `ia/sitemap.md`.

---

## Flow 1 — Main job: repeat questions handled without me

*When the same questions keep arriving on WhatsApp and I am the one answering them, I want them
handled without me, so that I can spend my day on the work only I can do.*

```mermaid
flowchart TD
    Start([Customer messages the business]) --> Recv["Loading: AI reads the message"]
    Recv --> Known{Does the knowledge cover this?}
    Known -->|no| Gap["Empty: no confident answer"]
    Gap --> Hand[Handover]
    Known -->|yes| Guard{Does a guardrail forbid the answer?}
    Guard -->|yes| Hand
    Guard -->|no| Send["Loading: sending the reply"]
    Send --> Deliv{Did the channel accept it?}
    Deliv -->|no| ChErr["Error: channel rejected or window closed"]
    ChErr --> Alert1["Overview raises channel health"]
    Alert1 --> ChDet[Channel detail]
    ChDet --> Fixable{Can the Administrator fix it?}
    Fixable -->|yes| Send
    Fixable -->|no| Stuck1([Dead end: the channel is out of the buyer's hands])
    Deliv -->|yes| React{How did the customer respond?}
    React -->|asked for a human| Hand
    React -->|asked again| Recv
    React -->|satisfied or went quiet| Res["Resolution recorded, confirmed or assumed"]
    Res --> Over[Overview]
    Over --> Win([Job closed: handled without me])
    Hand --> Staffed{Is anyone on the Operator role?}
    Staffed -->|yes| Inbox[Inbox]
    Inbox --> HandledConv[Handled conversation]
    HandledConv --> Win2([Job closed by a person, not by the AI])
    Staffed -->|no| NoOne["Empty: nobody is on duty"]
    NoOne --> Fallback["Handover fallback reply, written by the Administrator"]
    Fallback --> Alert2["Overview raises an unattended handover"]
    Alert2 --> Over
```

**Decisions in words**

| Decision | Yes branch | No branch |
|---|---|---|
| Does the knowledge cover this? | Check the guardrails next | Empty state, hand to a person |
| Does a guardrail forbid the answer? | Hand to a person rather than answer badly | Send the reply |
| Did the channel accept it? | Wait for the customer | Channel error → **`Overview` raises channel health** (D2) |
| Can the Administrator fix the channel? | Back to sending | Out of the buyer's hands — number suspended or bound elsewhere. The one remaining dead end |
| Is anyone on the Operator role? | The exception surface does its job | **Fallback reply fires and `Overview` raises an unattended handover** (D1). No longer a dead end |

**States in words**

| State | What triggers it | The way out |
|---|---|---|
| Loading — AI reads / sending | Every inbound message, and every outbound reply | Resolves to an answer, a handover or a channel error |
| Empty — no confident answer | The knowledge does not cover the question | Handover; the gap becomes a **Failure theme**, which is where Flow 3 starts |
| Empty — nobody on duty | Handover fires with no Operator available | **Fixed at `ia.6` (D1):** the fallback reply the Administrator wrote fires, and `Overview` raises an unattended handover. P1 is a 2–10 person business, so this is the normal configuration, not the edge case |
| Error — channel rejected | Number suspended, template unapproved, or the 24-hour window closed | **Fixed at `ia.6` (D2):** `Overview` raises channel health first, then `Channel detail`. Recoverable failures return to sending; unrecoverable ones are the dead end |

**Endings:** success — two, the AI closes it or a person does · dead end — **one, after the `ia.6`
fixes**: the channel is out of the buyer's hands (suspended, or bound to another BSP). The
"nobody on duty" dead end was removed, not by pretending it cannot happen, but by giving it a
fallback reply and a signal on `Overview`.

---

## Flow 2 — R1: live within the hour (MVP core)

*When I am setting this up for the first time, I want to see it answering my own real questions
within the hour, so that I know I have not bought another thing that does not work.*

```mermaid
flowchart TD
    Start([Signed up, migrating from another BSP]) --> Conn[Connect a channel]
    Conn --> Meta["Loading: Meta is checking the number"]
    Meta --> Appr{Approved?}
    Appr -->|rejected| MErr["Error: Meta rejected the number or the display name"]
    MErr --> Recover{Is the rejection recoverable?}
    Recover -->|yes, fix the name| Conn
    Recover -->|no, the number is bound elsewhere| Bound([Dead end: the number cannot be migrated])
    Appr -->|still pending| Pend["Loading: approval pending, hours to days"]
    Pend --> Know[Load your knowledge]
    Appr -->|approved| Know
    Know --> Ingest["Loading: reading your material"]
    Ingest --> Found{Did it find anything usable?}
    Found -->|no| KEmpty["Empty: nothing readable at that source"]
    KEmpty --> Know
    Found -->|yes| Live[Go live]
    Live --> Ask["Ask it a question you wrote yourself"]
    Ask --> Good{Is the answer good enough to trust?}
    Good -->|no| Guard[Guardrails]
    Guard --> Ask
    Good -->|yes| Turn["Loading: turning the AI on for real traffic"]
    Turn --> Over[Overview]
    Over --> Win([Job closed: it answered my own question, and it is live])
```

**Decisions in words**

| Decision | Yes branch | No branch |
|---|---|---|
| Approved? | Straight to knowledge | Rejected → is it recoverable? · Pending → **setup continues regardless** |
| Is the rejection recoverable? | Fix the display name and retry | The number is bound to another BSP — a real dead end mid-migration |
| Did it find anything usable? | Go live | Empty state at the source, retry |
| Is the answer good enough to trust? | Turn it on | Adjust guardrails and ask again — the loop that makes going live a decision rather than a leap |

**States in words**

| State | What triggers it | The way out |
|---|---|---|
| Loading — Meta checking | Number and display-name verification | Approved, rejected, or the pending state below |
| Loading — approval pending | Display name 3–4 hours, templates 24–48 hours (`research.md` R2) | **Setup continues in parallel, unconditionally.** Fixed at `ia.6` (D3): the branch where it could not was the competitor's behaviour drawn as if it were ours, and it contradicted the brief's own 10-minute criterion |
| Empty — nothing readable | The knowledge source is unreachable, empty or unparseable | Back to `Load your knowledge` with a different source |
| Error — Meta rejected | Name violates policy, or the number is already bound | Back to `Connect a channel` |

**Endings:** success — the AI answers a question the buyer wrote, then goes live · dead end — the
number **cannot be migrated at all** because it is bound elsewhere. That replaced the earlier
"waiting on Meta with nothing to do", which was the category's failure (`research.md` R2:
*"1-2 business days minimum"* behind a *"10-minute API approval"* claim) drawn as if it were
this product's.

---

## Flow 3 — R2: find out before the customer tells me (MVP core)

*When a customer gets a bad answer, I want to find out before they tell me, so that I am not
learning about my own business from a complaint.*

```mermaid
flowchart TD
    Start([Bad answers accumulate quietly]) --> Cluster["Loading: grouping failures by cause"]
    Cluster --> Any{Any theme above the noise floor?}
    Any -->|no| TEmpty["Empty: nothing is failing in a pattern"]
    TEmpty --> Over[Overview]
    Any -->|yes| Over
    Over --> Themes[Themes]
    Themes --> TDetail[Theme detail]
    TDetail --> Read{Is the cluster actually one problem?}
    Read -->|no| Conv[Conversation]
    Conv --> Themes
    Read -->|yes| Fix{What kind of fix does it need?}
    Fix -->|missing knowledge| Know[Knowledge]
    Fix -->|it said something it should not| Guard[Guardrails]
    Fix -->|a person should have taken it| Hand[Handover]
    Know --> Replay["Inline replay: what this would have changed"]
    Guard --> Replay
    Hand --> Replay
    Replay --> Worse{Did it make anything worse?}
    Worse -->|yes| TDetail
    Worse -->|no| Apply["Loading: applying the change"]
    Apply --> Val[Validation]
    Val --> Watching["Looking good: holding so far, still watching"]
    Watching --> Held{Did it hold on real traffic?}
    Held -->|failed| VErr["Error: the fix did not hold"]
    VErr --> TDetail
    Held -->|passed| Done([Job closed: theme resolved, and it was found first])
    Done --> Regress{Does the theme come back later?}
    Regress -->|yes| Regressed["Theme reopens itself, marked regressed"]
    Regressed --> Themes
    Regress -->|no| Stay([Stays resolved])
```

**Decisions in words**

| Decision | Yes branch | No branch |
|---|---|---|
| Any theme above the noise floor? | Surface it on `Overview` | Empty state — the honest "nothing is wrong in a pattern" |
| Is the cluster actually one problem? | Fix it as one | Open a `Conversation` as evidence, then back — **the guard against the pattern's own failure mode**, a bad cluster destroying trust in every cluster |
| What kind of fix does it need? | Three routes: knowledge, guardrails, handover | — |
| Did it make anything worse? | Back to the theme, do not apply | Apply |
| Did it hold on real traffic? | Resolved | Error — the fix did not hold, back to the theme |
| Does the theme come back? | **Reopens itself, marked regressed** — nobody has to notice | Stays resolved |

**States in words**

| State | What triggers it | The way out |
|---|---|---|
| Loading — grouping by cause | Continuously, as conversations land | A theme list, or the empty state |
| Empty — nothing failing in a pattern | Genuinely no cluster above the floor | `Overview`; this state must read as reassurance, not as breakage |
| Inline replay | Any proposed change, before it applies | Seconds, in place — **never its own destination** (`research.md` Pass 2 Q1: a <30-minute setup budget) |
| Looking good — holding so far | Validation running, nothing failing yet | **Added at `ia.6` (M1).** Benchmark mechanic 2 named the sequence; without the intermediate state a validation is a coin flip with a delay |
| Error — the fix did not hold | Validation ran on real traffic and failed | Back to `Theme detail` with what still fails |

**Endings:** success — the theme is resolved, validated on real traffic, and watched for
regression · dead end — none by design; every branch returns to `Theme detail` or `Themes`. The
regression branch is deliberately a **loop, not an ending**: benchmark mechanic 3.

---

## Flow 4 — R5: leave without a fight (MVP core)

*When it stops being worth it, I want to leave without a fight, so that I am not trapped paying
for something I have stopped using.*

```mermaid
flowchart TD
    Start([Decides it is not worth it]) --> Over[Overview]
    Over --> Acct[Account]
    Acct --> Which{Leaving, or just want the numbers?}
    Which -->|checking the numbers| Cost[What it costs and saves]
    Cost --> Over
    Which -->|leaving| Exp[Export]
    Exp --> Build["Loading: assembling your material"]
    Build --> Any2{Is there anything to export?}
    Any2 -->|no| XEmpty["Empty: nothing to take, and why"]
    XEmpty --> Bill
    Any2 -->|yes| Ready{Export ready?}
    Ready -->|failed| XErr["Error: export failed"]
    XErr --> Exp
    Ready -->|yes| Got["Material downloaded: conversations, knowledge, contacts"]
    Got --> Bill[Billing]
    Bill --> Term{Is the plan mid-term?}
    Term -->|yes| Owed["What is owed, stated before cancelling"]
    Owed --> Confirm{Still cancelling?}
    Term -->|no| Confirm
    Confirm -->|no| Acct
    Confirm -->|yes| Cancel["Loading: cancelling"]
    Cancel --> Stopped(["Job closed: billing stopped, material in hand, no one to argue with"])
```

**Decisions in words**

| Decision | Yes branch | No branch |
|---|---|---|
| Leaving, or just want the numbers? | `Export` | `What it costs and saves`, then back — the same branch serves R3 |
| Export ready? | Material in hand | Error, retry — **export precedes cancellation deliberately**, so nobody loses their material by cancelling first |
| Is the plan mid-term? | State what is owed **before** the cancel decision | Straight to confirm |
| Still cancelling? | Cancel | Back to `Account`, nothing hidden and nothing punished |

**States in words**

| State | What triggers it | The way out |
|---|---|---|
| Loading — assembling material | Export requested | Download, the empty state, or the error below |
| Empty — nothing to take | New or already-emptied account | **Added at `ia.6` (M2).** Says why there is nothing and continues to `Billing`; a blank download is the worst possible last impression on the way out |
| Error — export failed | Bundle could not be built | Retry from `Export`. **No path forward that cancels without the material** |
| Owed — what is due mid-term | Cancelling before the term ends | Shown *before* the confirm, never after |

**Endings:** success — billing stops, material in hand · **dead end — none, deliberately.** This
is the one flow where the absence of a dead end *is* the design: `research.md` R3 records
*"support becomes unresponsive once you request cancellation"*, *"dark patterns that make it hard
to find the actual cancellation form"* and *"they continue to charge me every month"*. Every
branch here ends either in cancellation or in a voluntary return to `Account`.

---

## Coverage

Every flow traces back to a job in `jtbd.md`, and every node exists in `ia/sitemap.md`.

| Flow | Job | Screen nodes | States present | Both endings? |
|---|---|---|---|---|
| 1 — handled without me | Main | Handover, Channel detail, Inbox, Handled conversation, Overview | empty ×2 · error · loading ×2 | yes — 2 successes, 1 dead end |
| 2 — live within the hour | R1 | Connect a channel, Load your knowledge, Go live, Guardrails, Overview | empty · error · loading ×3 | yes — 1 success, 1 dead end (unmigratable number) |
| 3 — find out first | R2 | Overview, Themes, Theme detail, Conversation, Knowledge, Guardrails, Handover, Validation, ‹inline Replay› | empty · error · loading ×2 | success + regression loop; **no dead end, by design** |
| 4 — leave without a fight | R5 | Overview, Account, What it costs and saves, Export, Billing | **empty** · error · loading ×2 | success only; **the absence of a dead end is the design** |

**Nodes added to `ia/sitemap.md` while drawing these flows:**

- None. Every node above was already in the tree confirmed at the `ia.2` gate.

**Jobs with no flow of their own:** R3, R4, E1, E2, S1, S2. R3 and R4 appear as branches inside
flows 4 and 3 respectively; E1, E2, S1 and S2 are dispositions rather than paths and are traced in
the matrix instead. The command asks for the main job plus 2–3 related; four flows are drawn
because the MVP core has three members and leaving one undrawn would hide it.
