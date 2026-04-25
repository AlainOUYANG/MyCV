# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

```bash
# Build English CV
latexmk cv.tex

# Build Chinese CV
latexmk cv_cn.tex

# Clean auxiliary files (keeps PDFs)
latexmk -c

# Clean everything including PDFs
latexmk -C
```

The `.latexmkrc` configures LuaLaTeX (`pdf_mode = 4`) with SyncTeX enabled and up to 5 compile passes.

## Architecture

This is a LaTeX CV repository with two parallel documents:

- [cv.tex](cv.tex) — English CV
- [cv_cn.tex](cv_cn.tex) — Chinese CV

Both use the custom class [mycv.cls](mycv.cls), which defines all the layout, environments, and commands. The class is based on the standard `article` class and licensed under LPPL-1.3c.

**Key files:**
- [mycv.cls](mycv.cls) — custom class; edit this to change layout, margins, or add new environments
- [CV collections.bib](CV%20collections.bib) — BibTeX bibliography used by `\publications[keyword={selected}]{...}` in both CVs
- [cv.xmpdata](cv.xmpdata) — PDF metadata (title, author, URL); update when forking for a new person
- KpFonts OTF files (`KpRoman-*.otf`, `KpSans-*.otf`, etc.) — bundled locally so no system font installation is needed

**Custom commands defined in `mycv.cls`** (key ones used in content files):
- `\name`, `\phone`, `\email`, `\homepage`, `\wechat`, `\linkedin` — header fields
- `\section`, `\subsection[location]` — section and dated/located subsection
- `\begin{positions} ... \entry{title}{date} \end{positions}` — job/role entries
- `\publications[keyword=...]{bibfile}` — filtered publication list from BibTeX
- `\printdate{...}` — right-aligned date in lists

## Formatting Conventions

- 2-space indentation, UTF-8, LF line endings (enforced by [.editorconfig](.editorconfig))
- `\vspace{-\parskip}` between subsections to control vertical spacing
- Commented-out blocks (`%`) are used to retain older content that may be toggled back in
