# Resume — CLAUDE.md skill

Drop this folder into Claude Code (or any Claude agent) to get a live LaTeX resume editor: edit by chatting, recompile + auto-open the PDF on every change, keep the layout clean and concise — 1–2 pages preferred.

## Files
- `resume.tex` — main LaTeX source (sample template, customize freely)
- `resume.pdf` — compiled output (1–2 pages preferred; user's call)

## How to compile
```bash
pdflatex resume.tex
```
Then `open resume.pdf` (macOS) / `xdg-open resume.pdf` (Linux) / `start resume.pdf` (Windows).

### Toolchain (one-time setup)
- macOS: `brew install --cask basictex` then open a new terminal so `/Library/TeX/texbin` lands on PATH
- Likely missing packages on first compile: `sudo tlmgr install enumitem titlesec marvosym preprint cm-super collection-fontsrecommended`

## Resume structure (recommended order)
1. **Header** — name + 5–6 link macros (email, website, GitHub, LinkedIn, X, etc.)
2. **Education** — newest first
3. **Experience** — newest first, with bullet items via `\resumeItemListStart` / `\resumeItem{...}` / `\resumeItemListEnd`
4. **Product showcases (optional)** — focused sections such as Apps, Games, or Chrome Extensions when the user's portfolio benefits from them
5. **Projects** — single merged list of one-liners (no current/legacy split)
6. **Open Source Contributions** — repos with star counts
7. **Honors & Awards** — newest first, single table
8. **Technical Skills** — Languages, Frameworks, Databases & Tools, AI Tools, Platforms

## Key formatting patterns
- One-line project: `\resumeProjectHeading{\textbf{name} \textnormal{ -- short description}}{}`
- With star count: `\resumeProjectHeading{\textbf{name} $|$ {\small $\bigstar$ Xk stars} \textnormal{ -- description}}{}`
- Closed source: `\textnormal{(closed source) -- description}`
- Honors row: `\textbf{Title} -- description & Date \\[0pt]`
- Header link: `\href{URL}{\underline{Label}}`
- **Clickable project / open-source name**: wrap the name in `\href{URL}{}` inside the existing `\textbf{}` — e.g. `\textbf{\href{https://github.com/you/repo}{repo}}`. `hyperref` is loaded with `hidelinks`, so the text looks identical in the PDF but is clickable. Use repo (or live-site) URLs for projects, merged-PR URLs for open-source contributions — mirroring the links in the GitHub profile README. Keep every project and OSS name linked; if adding them in bulk, batch it — don't ask one-by-one.

## Constraints
- 1–2 pages is the recommended sweet spot, but length is the user's call — don't enforce a cap. If the user wants to tighten the layout: tighten `\vspace` in `\resumeProjectHeading` (e.g. `-11pt`), or reduce honors row spacing from `\\[1pt]` → `\\[0pt]`. If they want it to breathe more: loosen those values.
- Section headers use `\scshape` (no bold available in OT1/cmr)
- FontAwesome5 not assumed — `\IfFileExists{fontawesome5.sty}{\usepackage{fontawesome5}}{}` for safe fallback; header uses plain text labels
- ATS-parseable: `\pdfgentounicode=1`
- Project & OSS names are clickable — each name wrapped in `\href{URL}{}` inside `\textbf{}`, linking to the same URLs as the GitHub profile README (repo/live URL for projects, merged-PR URL for open-source). `hidelinks` keeps them visually identical to plain text.

## Common tasks
- **Add a project**: copy a `\resumeProjectHeading` line into Projects
- **Update a star count**: find `$\bigstar$ Xk stars` in the relevant line
- **Add an honor**: add a `\textbf{Title} -- description & Date \\[0pt]` row to the Honors table
- **Make project / OSS names clickable**: wrap each name in `\href{URL}{}` inside `\textbf{}`. Project names → repo URL; open-source contributions → merged PR URL. For repos with multiple merged PRs, link to `https://github.com/owner/repo/pulls?q=author%3A<username>` so all show up.
- **Recompile after every change**: `pdflatex resume.tex && open resume.pdf`
- **Tighten the layout** (user wants it shorter): reduce `\vspace` in `\resumeProjectHeading` or row spacing in honors

## Private outreach tracking
- Use `outreach-leads.md` as the private working queue for prospects found during cold-outreach research, including founders, CEOs, HR/recruiting contacts, and relevant employees. Record available LinkedIn and X profiles alongside the person, role, and company.
- Use `outreach-sent.md` as the private archive of people who were successfully contacted or were found to have been contacted previously.
- Use `outreach-discarded.md` as the private archive of attempted contacts who could not be reached and should not be tried again, including InMail-only profiles, unavailable composers, unverified profiles, and accounts that do not accept new DMs.
- After an outreach attempt, remove the person's complete entry from `outreach-leads.md` immediately and move it to exactly one archive: `outreach-sent.md` after a successful or previously completed contact, or `outreach-discarded.md` after a failed/unreachable contact. Never keep the same person in multiple files.
- Before researching or contacting anyone, check both archives to prevent duplicate outreach and avoid retrying discarded contacts. The completed outreach history is the union of the sent and discarded archives; `outreach-leads.md` contains only unprocessed prospects.
- For job outreach, prioritize remote full-time software/product engineering roles.
- Keep the factual core of each outreach message consistent, but personalize the recipient, company/product observation, and proposed contribution for each founder or contact.
- Write outreach in a concise, natural, human voice. Keep it short and specific; avoid corporate phrasing, generic compliments, resume dumps, and AI-sounding filler.
- Read the current personal resume before drafting outreach, and attribute download and star milestones to their specific apps. Never generalize one app's metrics across multiple apps or reuse stale counts.
- All outreach files match the `outreach-*.md` rule in `.gitignore` and must remain private and untracked.

## Workflow notes (for Claude)
- After every edit to `resume.tex`, recompile and open the PDF so the user can visually verify.
- After compiling, sync **both** the `.tex` source and the compiled `.pdf` to `~/Documents/` so the canonical current resume — source *and* output — always lives there. Keep the two in sync (recompile, then copy both).
- After any structural/formatting change, update this `CLAUDE.md` to keep it accurate.
- Treat `resume.tex` as the source of truth for the user's personal data (name, projects, honors, etc.) — read it before suggesting changes.
- The structure, sections, page count, and formatting above are **recommendations, not rules**. If the user explicitly asks to change the template (drop a section, add one, reorder, switch color theme, ditch the Jake's Resume base entirely, target 3+ pages, etc.) — do it. Their resume, their call.

## Credits
LaTeX base: [Jake's Resume](https://github.com/jakegut/resume) (MIT).
This skill: [rekisei](https://github.com/apoorvdarshan/rekisei).
