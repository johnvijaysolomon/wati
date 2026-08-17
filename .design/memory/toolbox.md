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
| Design quality laws | `impeccable` skill (`critique` / `audit` / `document` / `extract`) | Claude Code plugin marketplace: `pbakaus/impeccable` | Built-in prompts in `.design/prompts/`: `critique.md`, `audit.md`, `document.md`, `extract.md` | `fallback` |
| Structured brief | `obra/superpowers` **brainstorming** skill | Skill bundle `obra/superpowers` | Built-in interrogation prompt `.design/prompts/brief-interrogation.md` | `fallback` |
| Imagery | Gemini API image generation — one colorway, prompts recorded in `visuals/README.md` | API key from **aistudio.google.com**, kept as `GEMINI_API_KEY` (or `GOOGLE_API_KEY`) in the environment — never committed | Unsplash, queried by content theme (interior for a room, portrait for a person) | `fallback` |
| Icons | Solar set, one style throughout (linear / bold / bold-duotone) | Open icon set — downloaded into the repo, no account needed (a choice, not an install) | Any single-style open set, recorded by name and style in `DESIGN.md` | `active` |
| Hosting | GitHub repo + GitHub Pages | `gh auth login`, run by the agent; Pages enabled on the default branch root | Any git host + a local static server the agent starts on request | `fallback` |

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

- **Visual references — no Refero.** Gather references with the Mobbin MCP (`search_screens`,
  `search_flows`, `search_sections`) first and web search second. Every row of
  `concept/references.md` names its source and how it was found, tagged `[mobbin]` or `[web]`,
  with the app and screen named. A reference that cannot be linked or screenshotted is `[?]` —
  never described from memory.
- **Design quality laws — no `impeccable`.** Every critique, audit, document and extract pass in
  phases 4–10 runs the matching file in `.design/prompts/` verbatim. The artifact it produces
  names which prompt was run, so a reader can tell a prompt-driven pass from a skill-driven one.
- **Structured brief — no `superpowers`.** Phase 1 *is* `.design/prompts/brief-interrogation.md`,
  run question by question at the human gate. Never synthesise a brief from a single answer and
  never fill an unanswered question with a plausible one — unanswered stays `[?]`.
- **Imagery — no Gemini key.** Product imagery is generated with the Higgsfield MCP
  (`generate_image`), one locked colorway for the whole project. Every prompt is recorded
  verbatim in `visuals/README.md` alongside the returned asset id. If Higgsfield is unreachable
  in a session, use Unsplash queried by content theme and label the source in the same file.
  Mixing generators or colorways is a defect, not a variation.
- **Hosting — no GitHub.** Commits stay local; nothing is pushed and no phase reports a public
  URL. `index.html` and every `*.html` artifact are opened either from the local file path or
  through a local static server the agent starts on request. Any command whose step says "push"
  or "record the Pages URL" records the local path instead and says why.

## Notes

Recorded by `/dsf:init`. Why a row is on `fallback`, plus keys, endpoints, model names, MCP
server names, the Pages URL, and anything else a later phase needs to reproduce a result.

- **Browser & screenshots — `active`.** Detection: `@playwright/mcp` was not present at init.
  Installed at the human gate and added to project scope in `.mcp.json` as server `playwright`
  (`npx -y @playwright/mcp@latest`). Evidence: `npx -y @playwright/mcp@latest --version` →
  `Version 0.0.79`. Project-scoped MCP config loads for sessions rooted at the repo root, so a
  session started elsewhere will not see it.
- **Visual references — `fallback`.** Reason: no Refero MCP server is configured and there is no
  refero.design account for this project. The Mobbin MCP is connected at the account level and
  covers the same job; it is a substitute for the fallback column, not a promotion of the row to
  `active` — Refero itself remains uninstalled.
- **Design quality laws — `fallback`.** Reason: declined at the phase-0 gate. The `impeccable`
  skill is a third-party marketplace plugin (`pbakaus/impeccable`) and the four shipped prompts
  in `.design/prompts/` cover the same four passes. Re-offer only on a re-run of `/dsf:init`.
- **Structured brief — `fallback`.** Reason: declined at the phase-0 gate. `obra/superpowers` is
  not installed; `.design/prompts/brief-interrogation.md` ships with the template and is phase 1.
- **Imagery — `fallback`.** Reason: neither `GEMINI_API_KEY` nor `GOOGLE_API_KEY` is set in this
  environment and no image-gen script is present in the repo. Substitute in force: Higgsfield MCP
  `generate_image` / `generate_image_batch`, connected at the account level.
- **Icons — `active`.** Set: **Solar**, chosen by the human at the phase-0 gate. Delivery: the
  Icons8 MCP is connected (`search_icons`, `get_icon_svg`) and serves the SVGs; icons are
  downloaded into the repo rather than linked. **Open item:** the single style — `linear`,
  `bold` or `bold-duotone` — is a visual decision and is not set here. It is locked at
  `/dsf:concept` (phase 5) and written into `DESIGN.md` at `/dsf:build` (phase 6). Until then no
  phase may ship an icon, and no phase may pick the style on its own.
- **Hosting — `fallback`.** Reason: the `gh` CLI is not installed on this machine
  (`gh auth status` → `command not found`), so no GitHub repo could be created and Pages could
  not be enabled. Local-only: git repo initialised at `/Users/johnvijaysolomon/wati`, branch
  `main`, no remote configured. Project home page opens at
  `/Users/johnvijaysolomon/wati/index.html`. To switch later: install `gh`, run `/dsf:init`
  again, and re-run `/dsf:check 0`.
