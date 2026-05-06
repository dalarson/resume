# Copilot instructions for dalarson/resume

Purpose
- Provide repository-specific guidance for Copilot-style assistants so suggestions and automations are accurate and safe.

Quick repo facts
- Minimal repository containing a single LaTeX resume: resume.tex and generated resume.pdf (committed for convenience).
- No CI workflows, build scripts, or automated tests detected in the repository root.

Build / preview commands
- Local builds (macOS / Linux):
  - pdflatex resume.tex             # single-pass PDF build
  - pdflatex resume.tex && pdflatex resume.tex  # rerun to resolve cross-references
  - latexmk -pdf resume.tex        # recommended if available; auto-runs required passes
  - latexmk -c                      # clean auxiliary files
  - open resume.pdf                 # macOS: open generated PDF after build
- Notes: resume.pdf is committed but can be regenerated. Do not add unrelated toolchain files without confirmation.

Testing & linting
- No automated tests or linters exist. Changes should be validated by rebuilding the PDF and visually inspecting resume.pdf.
- If tests/linting are added later, update this file with commands to run a single test (e.g., test runner CLI) as well as full-suite commands.

High-level architecture
- Single-document LaTeX resume:
  - resume.tex contains all styling, macros, and content.
  - Uses custom macros to structure content and keep markup consistent (see macros below).
  - Generated artifacts: resume.pdf (committed) and standard LaTeX aux files (ignored via .gitignore).

Key macros and locations
- Primary macros (defined inside resume.tex):
  - \resumeItem{title}{body}
  - \headlessResumeItem{text}
  - \resumeSubheading{title}{location}{role}{dates}
  - \resumeSubItem{title}{body}
  - List helpers: \resumeSubHeadingListStart/End, \resumeItemListStart/End
- Styling (packages, page geometry, header/footer) are configured at the top of resume.tex.
- Header/contact block is near the document top (around the first tabular environment).

Key conventions
- Make localized edits to resume.tex only. Prefer adding content via existing macros rather than introducing new raw LaTeX blocks.
- Preserve macro names/signatures; modify macro implementations only if a project-wide formatting change is requested and approved.
- Keep personal/contact info in the header table near the top of resume.tex.
- Generated LaTeX files are gitignored (.aux, .log, .out, .fls, .fdb_latexmk, .synctex.gz). Do not commit intermediate build artifacts.
- If adding tooling (latexmk, Makefile, CI), update this doc and README.md to include build and clean commands.

Repo housekeeping
- .gitignore already excludes common LaTeX auxiliary files. Use `latexmk -c` to clean intermediate files locally.
- If resume.pdf is to be excluded later, remove it from the repository and add it to .gitignore; document that change here.

Docs & existing AI configs checked
- README.md inspected and reflected here.
- No other assistant config files detected (CLAUDE.md, AGENTS.md, .cursorrules, .windsurfrules, CONVENTIONS.md, etc.).

Editing guidance for Copilot sessions
- For mechanical text edits, return a minimal patch/diff and apply it to resume.tex.
- For structural changes (new macros, section rework, or adding toolchain), propose a short plan first and ask for confirmation.
- Avoid introducing unrelated files or complex CI/tooling without explicit approval.
- Do not stage or commit anything to the git repository unless the user explicitly asks for that.

Contact for follow-up
- Ask for scope clarification before adding CI, tests, or changing whether generated artifacts are committed.
