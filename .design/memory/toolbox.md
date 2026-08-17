# Toolbox

What this project has, and what to use when it does not.

`/dsf:init` walks this table, offers to install each recommended tool, and records the answer
in **Status**. Nothing here is mandatory — every row has a fallback that keeps the pipeline
moving.

**Every `/dsf:*` command must read this file before it touches a tool.** If a row is not
`active`, use its fallback silently and note the substitution in the phase artifact. Never
block a phase, never ask the human to install something mid-phase, and never assume
availability from a previous session.

---

## Status vocabulary — defined here, used everywhere

Three values. No others. Every command, checklist and artifact that talks about tool status
refers to this list rather than restating it.

| Status | Meaning | What downstream commands do |
|---|---|---|
| `active` | installed and verified in this repo, with the detection evidence recorded | use the recommended tool |
| `fallback` | not in use — declined by the human, or the install failed, or it is unavailable here | use the fallback column, and say so in the artifact |
| `[?]` | not yet checked — `/dsf:init` has not walked this row | treat as `fallback` and report the `[?]` as an open phase-0 item |

A `[?]` left in the Status column after `/dsf:init` is a failed phase-0 gate, not a detail.
`declined`, `unavailable`, `installed` and `pending` are **not** status values here — they are
reasons, and reasons belong in the Notes section.

---

## Tools

| Purpose | Recommended | Install source | Fallback | Status |
|---|---|---|---|---|
| Browser & screenshots | Playwright MCP | MCP server `@playwright/mcp` — the agent adds it to this project's MCP config | WebFetch-only research; human-supplied screenshots dropped into `research/screens/` | `active` |
| Visual references | Refero MCP | Refero MCP server (account at refero.design, endpoint added to the project's MCP config) | Web search + competitor screenshots, every source listed in `concept/references.md` | `fallback` |
| Design quality laws | `impeccable` skill (`critique` / `audit` / `document` / `extract`) | Claude Code plugin marketplace: `pbakaus/impeccable` | Built-in prompts in `.design/prompts/`: `critique.md`, `audit.md`, `document.md`, `extract.md` | `active` |
| Structured brief | `obra/superpowers` **brainstorming** skill | Skill bundle `obra/superpowers` | Built-in interrogation prompt `.design/prompts/brief-interrogation.md` | `active` |
| Imagery | Gemini API image generation — one colorway, prompts recorded in `visuals/README.md` | API key from **aistudio.google.com**, kept as `GEMINI_API_KEY` (or `GOOGLE_API_KEY`) in the environment — never committed | Unsplash, queried by content theme (interior for a room, portrait for a person) | `fallback` |
| Icons | Solar set, one style throughout (linear / bold / bold-duotone) | Open icon set — downloaded into the repo, no account needed (a choice, not an install) | Any single-style open set, recorded by name and style in `DESIGN.md` | `active` |
| Hosting | GitHub repo + GitHub Pages | `gh auth login`, run by the agent; Pages enabled on the default branch root | Any git host + a local static server the agent starts on request | `active` |

---

## Rules

- A `fallback` row is not re-offered every phase. `/dsf:init` is the only place to change a
  row.
- When a fallback is used for an artifact, say so in that artifact — a reader must be able to
  tell a Refero-sourced reference from a web-searched one.
- Icon set and image generator are locked once chosen. Mixing sets or colorways is a defect,
  not a variation.
- Adding a tool later: re-run `/dsf:init`, update this table, and re-run the affected phase's
  `/dsf:check` — earlier artifacts are not retroactively regenerated unless the human asks.
- Fallback prompts live in `.design/prompts/` and ship with the template. They are not
  optional extras: with the `impeccable` row on `fallback`, they *are* the quality pass for
  phases 4–10, and `brief-interrogation.md` *is* phase 1.

## Rules for later phases

Written by `/dsf:init`, one line per `fallback` row, stating in words what later phases must
do instead. Actionable, not decorative — later commands act on this text.

Two rows are on `fallback` after the 2026-08-17 09:30 re-run. Their rules:

- **Visual references — no Refero.** Gather references with the Mobbin MCP (`search_screens`,
  `search_flows`, `search_sections`) first and web search second. Every row of
  `concept/references.md` names its source and how it was found, tagged `[mobbin]` or `[web]`,
  with the app and screen named. A reference that cannot be linked or screenshotted is `[?]` —
  never described from memory.
- **Imagery — no Gemini key.** Product imagery is generated with the Higgsfield MCP
  (`generate_image`), one locked colorway for the whole project. Every prompt is recorded
  verbatim in `visuals/README.md` alongside the returned asset id. If Higgsfield is unreachable
  in a session, use Unsplash queried by content theme and label the source in the same file.
  Mixing generators or colorways is a defect, not a variation.

Three rows moved from `fallback` to `active` in that re-run. They carry no fallback rule any
more, but they do carry an obligation, because a row going `active` changes what later phases
must do:

- **Design quality laws — `impeccable` is now the quality pass.** Every critique, audit,
  document and extract pass in phases 4–10 runs the `impeccable` command for that pass, not the
  matching file in `.design/prompts/`. The artifact still names which pass was run and which
  tool ran it, so a reader can tell a skill-driven pass from a prompt-driven one — the shipped
  prompts stay in the repo as the recorded fallback, unused while this row is `active`.
- **Structured brief — `superpowers` drives phase 1.** `/dsf:brief` runs the `brainstorming`
  skill rather than `.design/prompts/brief-interrogation.md`. The gate discipline is unchanged
  and is not the skill's to relax: never synthesise a brief from a single answer, and never fill
  an unanswered question with a plausible one — unanswered stays `[?]`.
- **Hosting — GitHub Pages is live, and the repo is public.** Commits are pushed to
  `origin/main`; every phase that produces an HTML artifact reports its public URL under
  `https://johnvijaysolomon.github.io/wati/`. Two consequences later phases must respect:
  a phase is not done until its artifact is pushed and reachable at that URL, and **everything
  committed is world-readable** — research screenshots, competitor data, personas, quotes and
  interview material included. Anything that must not be public does not go in this repo at all;
  there is no private corner of it.

## Notes

Recorded by `/dsf:init`. Why a row is on `fallback`, plus keys, endpoints, model names, MCP
server names, the Pages URL, and anything else a later phase needs to reproduce a result.

Statuses below are as of the **2026-08-17 09:30 `/dsf:init` re-run**, which re-detected every
row with fresh evidence and re-opened the phase-0 gate. Three rows changed and one factual error
from the 08:21 run was corrected.

- **Browser & screenshots — `active`.** Unchanged by the re-run. Added to project scope in
  `.mcp.json` as server `playwright` (`npx -y @playwright/mcp@latest`). Evidence, re-verified
  09:30: MCP tools present in session and `npx -y @playwright/mcp@latest --version` →
  `Version 0.0.79`. Project-scoped MCP config loads for sessions rooted at the repo root, so a
  session started elsewhere will not see it.
- **Visual references — `fallback`.** Unchanged by the re-run. Reason: no Refero MCP server is
  configured and there is no refero.design account for this project. Evidence, 09:30:
  `ToolSearch "+refero"` → no matching tools. Not re-offered at the gate as an install, because
  it needs an account this project does not have — activating it later means creating the
  account, adding the endpoint to `.mcp.json`, and re-running `/dsf:init`. The Mobbin MCP is
  connected at the account level and covers the same job; it is a substitute for the fallback
  column, not a promotion of the row to `active` — Refero itself remains uninstalled.
- **Design quality laws — `active` (changed 09:35, was `fallback`).** Installed at the re-run
  gate. Marketplace `pbakaus/impeccable` added, plugin `impeccable@impeccable` **4.1.1**
  installed at **project** scope. Evidence: `claude plugin list` → enabled; and the row's four
  required passes were verified present in the skill rather than assumed —
  `plugin/skills/impeccable/SKILL.md` maps `document`, `extract`, `critique` and `audit` to
  their own reference files. **Loads from the next session start**, not this one.
- **Structured brief — `active` (changed 09:36, was `fallback`).** Installed at the re-run gate.
  Marketplace `obra/superpowers` added (registers as `superpowers-dev`), plugin
  `superpowers@superpowers-dev` **6.3.0** installed at **project** scope. Evidence:
  `claude plugin list` → enabled; and the specific skill this row needs was verified present —
  `skills/brainstorming/SKILL.md`. **Loads from the next session start**, not this one, so
  `/dsf:brief` must confirm the skill is actually available before relying on it and fall back to
  `.design/prompts/brief-interrogation.md` for that session if it is not.
- **Imagery — `fallback`.** Unchanged by the re-run. Reason: neither `GEMINI_API_KEY` nor
  `GOOGLE_API_KEY` is set in this environment and no image-gen script is present in the repo
  (re-verified 09:30). Offered at the re-run gate and declined — a key must be fetched from
  aistudio.google.com by hand first. Substitute in force: Higgsfield MCP `generate_image` /
  `generate_image_batch`, connected at the account level.
- **Icons — `active`.** Set: **Solar**, chosen by the human at the 08:18 gate and re-confirmed at
  the 09:30 gate. **Correction:** the note written at 08:21 said the SVGs are served by a
  connected Icons8 MCP (`search_icons`, `get_icon_svg`). That was wrong — no Icons8 MCP is
  connected in this project or at account level (evidence, 09:30: `ToolSearch "+icons8"` → no
  matching tools), and no phase should plan around one. Solar is an open set that needs no
  account: the SVGs are downloaded into the repo directly from the set's own distribution, and
  icons are committed rather than linked. The choice of set is what makes this row `active`; the
  delivery mechanism was never an install. **Open item, unchanged:** the single style — `linear`,
  `bold` or `bold-duotone` — is a visual decision and is not set here. It is locked at
  `/dsf:concept` (phase 5) and written into `DESIGN.md` at `/dsf:build` (phase 6). Until then no
  phase may ship an icon, and no phase may pick the style on its own.
- **Hosting — `active` (changed 09:45, was `fallback`).** The 08:21 note recorded `gh` as absent
  and treated that as final; it was not — Homebrew 6.0.15 is on this machine, so at the re-run
  gate the human chose GitHub and `gh` **2.97.0** was installed with `brew install gh`.
  Authenticated as **`johnvijaysolomon`** (device flow, run by the human — the browser step is the
  one thing the agent cannot do for them; token scopes `gist`, `read:org`, `repo`).
  - Repo: **`johnvijaysolomon/wati`**, remote `origin`, branch `main` tracking `origin/main`.
  - **Visibility: public — and this was a second gate, not a default.** The repo was created
    private as asked, and `POST /repos/.../pages` failed with HTTP 422, *"Your current plan does
    not support GitHub Pages for this repository"* — Pages on a private repo needs a paid plan
    and this account is free. Rather than silently flip the visibility the human had chosen, the
    failure was reported and the choice put back to them; they answered "Make it public, enable
    Pages". The repo was then flipped with `gh repo edit --visibility public` and Pages enabled.
  - Pages: enabled on **`main` / root**, HTTPS enforced. Project home page:
    **`https://johnvijaysolomon.github.io/wati/`** — Pages serves `index.html` at the repo root,
    so no file name is needed in the URL. `assets/` is committed and published with it.
  - Consequence for every later phase: this repo is **world-readable**. See the hosting rule
    above before committing anything sourced from a real customer, interview or internal system.
