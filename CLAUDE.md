# RevOps Growth Tools

A suite of standalone interactive HTML tools for the Revenue Operations department at Owner. Used by the RevOps team for career development, performance evaluation, capability planning, and team structure work.

Deployed from this repo: https://github.com/brandyvega-stack/revops-internal-tools

## Who you're working with

Brandy is a RevOps leader, **not a software engineer**. She directs work in natural language and reads diffs, not code.

When working with her:
- **Explain what you're about to do in plain English before doing it.** One or two sentences, no jargon.
- **Avoid technical terms without explaining them.** "Repo," "commit," "push," "branch" — assume nothing.
- **Tell her which file you're editing and why.** Not just "I'll update the rubric" — say "I'll edit `revops_rubric_combined.html` to change the L5 column wording, because…"
- **Ask before making big changes.** Anything beyond a small fix, copy edit, or styling tweak — confirm the approach first.
- **Default to small, reversible changes.** Don't refactor, don't introduce build tooling, don't reorganize files unless asked.
- **No surprise commits or pushes.** Always confirm before pushing to GitHub.

## How I like to work

- Show me a plain English summary of what you changed and why after every edit.
- Make one change at a time and check in with me before moving to the next.
- Always ask before pushing to GitHub — don't auto-push.
- If something could be done multiple ways, briefly explain the options before picking one.

## Practical guardrails

- Never delete or overwrite any file without explicitly asking me first.
- Don't refactor, reorganize, or "clean up" code unless I specifically ask for it.
- If you notice something else that could be improved while working on a task, flag it as a suggestion but don't touch it.
- Always tell me which file you're editing before you edit it.

## The files

All pages are self-contained HTML/CSS/JS. No build step, no framework, no package manager. Open any one in a browser and it works.

- **`index.html`** — Landing page. Sticky nav and a grid of tool cards linking to the other pages. Also links out to the Notion documentation.
- **`revops_org_chart.html`** — The current RevOps team org chart, plus a "Draft" mode for proposing reorgs. Drag-to-reparent, add proposed roles, save multiple named scenarios. Drafts are saved in the browser only (localStorage), not on a server.
- **`revops_periodic_table.html`** — A "periodic table" of every capability RevOps owns or is building. Two blocks (customer-facing GTM functions and infrastructure), ~27 cells, each tagged with maturity (active today / building now / future). Click cells for detail.
- **`revops_rubric_combined.html`** — Performance rubric with two tabs: IC track (L3–L8) and Management track (M6–SVP). Rate subcategories, add notes and next steps, and an "Summarize with AI" button drafts the overall write-up.
- **`revops_career_map.html`** — Visual reference showing the IC track and Management track side by side. Same-row alignment shows equivalent seniority (L6=M6, L7=M7, L8=M8). Dashed lines reinforce equivalence; thin gray arrows show within-track promotion paths. No interactivity — it's a read-only reference.
- **`revops_transition_guide.html`** — Three big career-shift conversations: IC→Management, Manager→Functional Owner, Functional Owner→Executive. Dual reflection fields, listen-for prompts, and an AI synthesis button per section.

## Design patterns to preserve

These are intentional and consistent across all five pages — don't break them without checking:

- **Sticky nav at the top of every page.** Same brand, same link list, same theme toggle. If you add a new page, it needs to appear in the nav on every other page too.
- **Color tokens (CSS variables).** `--green` = IC track, `--blue` = Management track, `--amber` = Functional Owner / launch / build, `--pink` = Executive / Notion accent, `--teal` = Org chart, `--purple` = Career Map. Reuse these — don't invent new colors.
- **Fonts.** DM Sans for body text, Space Mono or DM Mono for labels, level tags, and code-like elements.
- **Dark/light theme toggle.** Lives in localStorage under the key `revops_theme`. Every page reads/writes this same key so the theme is shared.
- **Plain HTML/CSS/JS only.** No React, no build step, no npm install. Anyone with a browser can open the files locally.

## Known issues to be aware of

- **AI summary buttons currently won't work in production.** The rubric and transition guide pages call the Anthropic API directly from the browser without an API key header. As written, those requests will fail. Fixing this needs either (a) a hosted backend/proxy that holds the key, or (b) some other workaround. Worth flagging if Brandy asks about getting AI summaries working.
- **Rubric and transition guide don't save user input.** If someone fills out a rubric and refreshes the page or closes the tab, their ratings and notes are lost. Only the org chart's drafts persist (via localStorage).
- **`.DS_Store`** files from macOS Finder are gitignored. Don't try to commit them.
- **`.claude/`** (this folder for Claude Code session state) is also gitignored.

## Git workflow

- Default branch is `main`. There's no staging/dev branch.
- Brandy authenticated `gh` CLI on this machine — `git push` works directly from the terminal now.
- Before now, she was uploading files via the GitHub web UI, which is why early commit messages say "Add files via upload." Going forward, commits should have meaningful messages.
- Always confirm with her before pushing.
