# Copilot instructions for dalarson/resume

Purpose
- Provide repository-specific guidance for Copilot-style assistants so suggestions and automations are accurate and safe.

Quick repo facts
- Minimal repo holding a LaTeX resume: resume.tex and generated resume.pdf
- No CI workflows, build scripts, or test suites detected in repository root

Build / preview commands
- Recommended (local):
  - pdflatex resume.tex            # single-pass PDF build
  - pdflatex resume.tex && pdflatex resume.tex  # rerun to resolve references
  - latexmk -pdf resume.tex       # robust full build (if available)
- No npm/pip/Makefile detected; do not assume package.json or CI scripts exist.

Testing & linting
- No automated tests or linters found. Treat edit-and-build as manual verification.

High-level architecture
- Single-document LaTeX resume using custom macros:
  - Key macros: \resumeItem, \resumeSubheading, \resumeSubItem, \resumeSubHeadingListStart/End
  - Styling is controlled in resume.tex (packages, page geometry, titleformat). 
- Generated artifact: resume.pdf (committed here for convenience)

Key conventions (for code/AI edits)
- Make localized changes to resume.tex only. Avoid adding unrelated build/config files unless requested.
- Preserve macro names and signatures when modifying sections; Copilot should prefer using existing macros for new entries.
- Keep personal/contact info in the header table near the top of resume.tex (lines ~76-80).
- When adding new tooling (e.g., latexmk, makefile), update this file and README.md.

Docs & other AI configs checked
- README.md inspected and incorporated.
- No CLAUDE.md, AGENTS.md, .cursorrules, .windsurfrules, CONVENTIONS.md, or other assistant configs found.

If editing guidance
- For small text edits, produce a diff/patch; prefer single-line edits where possible.
- For structural changes (new sections or macro changes), propose edits in a short plan before applying.

Contact for follow-up
- Suggest clarifying scope before adding CI, test harnesses, or toolchain files.

