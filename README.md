# rekisei

A reusable [Claude Code](https://claude.com/claude-code) skill for editing a clean **2-page LaTeX resume** by chatting.

Built on the [Jake's Resume](https://github.com/jakegut/resume) base, plus a `CLAUDE.md` that teaches Claude how to add projects, update star counts, manage honors, and keep the layout on 2 pages — and a workflow that recompiles + auto-opens the PDF after every edit.

## Quick start

1. Clone the repo:
   ```bash
   git clone https://github.com/apoorvdarshan/rekisei.git
   cd rekisei
   ```

2. Install a LaTeX toolchain. macOS:
   ```bash
   brew install --cask basictex
   # open a new terminal so /Library/TeX/texbin lands on PATH
   sudo tlmgr install enumitem titlesec marvosym preprint cm-super collection-fontsrecommended
   ```

3. *(Optional but recommended)* Create `CLAUDE.local.md` with your private personal data — name, projects, honors, contact. It's gitignored. Claude Code reads it automatically alongside `CLAUDE.md`.

4. Open the folder in Claude Code:
   ```bash
   claude
   ```

5. Ask Claude to customize `resume.tex` for you — *"replace the placeholders with the info from CLAUDE.local.md"* — or just edit `resume.tex` directly. After every change Claude will recompile and open the rendered PDF.

## What's in the box
- **`CLAUDE.md`** — the skill: instructions for Claude on file structure, formatting patterns, common tasks, and workflow.
- **`resume.tex`** — sample template with placeholder content. Customize freely.
- **`resume.pdf`** — compiled sample output.
- **`.gitignore`** — keeps your personal `CLAUDE.local.md` and personal-named resume files out of git if you fork this.

## Why "rekisei"?
歴世 — a Japanese word meaning *"successive generations"* / *"the passage of years"* — what a resume captures.

## License

MIT. LaTeX base from [jakegut/resume](https://github.com/jakegut/resume) (also MIT).
