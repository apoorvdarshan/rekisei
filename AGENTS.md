# Resume — AGENTS.md skill

Drop this folder into Codex (or any agent that reads `AGENTS.md`) to get a live LaTeX resume editor: edit by chatting, recompile + auto-open the PDF on every change, keep the layout clean and concise — 1–2 pages preferred.

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
4. **Projects** — single merged list of one-liners (no current/legacy split)
5. **Open Source Contributions** — repos with star counts
6. **Honors & Awards** — newest first, single table
7. **Technical Skills** — Languages, Frameworks, Databases & Tools, AI Tools, Platforms

## Key formatting patterns
- One-line project: `\resumeProjectHeading{\textbf{name} \textnormal{ -- short description}}{}`
- With star count: `\resumeProjectHeading{\textbf{name} $|$ {\small $\bigstar$ Xk stars} \textnormal{ -- description}}{}`
- Closed source: `\textnormal{(closed source) -- description}`
- Honors row: `\textbf{Title} -- description & Date \\[0pt]`
- Header link: `\href{URL}{\underline{Label}}`

## Constraints
- 1–2 pages is the recommended sweet spot, but length is the user's call — don't enforce a cap. If the user wants to tighten the layout: tighten `\vspace` in `\resumeProjectHeading` (e.g. `-11pt`), or reduce honors row spacing from `\\[1pt]` → `\\[0pt]`. If they want it to breathe more: loosen those values.
- Section headers use `\scshape` (no bold available in OT1/cmr)
- FontAwesome5 not assumed — `\IfFileExists{fontawesome5.sty}{\usepackage{fontawesome5}}{}` for safe fallback; header uses plain text labels
- ATS-parseable: `\pdfgentounicode=1`
- No hyperlinks on project names — only the header has links

## Common tasks
- **Add a project**: copy a `\resumeProjectHeading` line into Projects
- **Update a star count**: find `$\bigstar$ Xk stars` in the relevant line
- **Add an honor**: add a `\textbf{Title} -- description & Date \\[0pt]` row to the Honors table
- **Recompile after every change**: `pdflatex resume.tex && open resume.pdf`
- **Tighten the layout** (user wants it shorter): reduce `\vspace` in `\resumeProjectHeading` or row spacing in honors

## Workflow notes (for the agent)
- After every edit to `resume.tex`, recompile and open the PDF so the user can visually verify.
- After any structural/formatting change, update this `AGENTS.md` to keep it accurate.
- Treat `resume.tex` as the source of truth for the user's personal data (name, projects, honors, etc.) — read it before suggesting changes.
- The structure, sections, page count, and formatting above are **recommendations, not rules**. If the user explicitly asks to change the template (drop a section, add one, reorder, switch color theme, ditch the Jake's Resume base entirely, target 3+ pages, etc.) — do it. Their resume, their call.

## Credits
LaTeX base: [Jake's Resume](https://github.com/jakegut/resume) (MIT).
This skill: [rekisei](https://github.com/apoorvdarshan/rekisei).
