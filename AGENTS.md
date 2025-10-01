# Repository Guidelines

## Project Structure & Module Organization
The LaTeX sources are anchored in `main.tex`, which includes `tex/0_abs.tex`–`tex/7_Appendix.tex` for each manuscript section. Supporting macros live in `math_commands.tex` and `tex/command/`, so define any new math or notation there and `\input{}` them once. Figures and vector assets belong in `fig/`; keep both `.pdf` and `.png` versions when rasterization is needed. Table fragments sit under `tab/` and are assembled with `\input{}` from the main manuscript. Use `arxiv.tex` for the camera-ready bundle when a stripped preamble is required.

## Build, Test, and Development Commands
Run `latexmk -pdf main.tex` for the primary PDF; it handles BibTeX via `iclr2026_conference.bib` automatically. Use `latexmk -pdf arxiv.tex` to confirm the submission build. Execute `latexmk -c` after large changes to clear auxiliary files, or `latexmk -pdf -interaction=nonstopmode main.tex` during batch testing to surface warnings without manual prompts. `texcount main.tex` provides a section-wise word count before submission deadlines.

## Coding Style & Naming Conventions
Wrap lines at roughly 100 characters and break after sentences; this mirrors the existing style in `tex/*.tex`. Prefer semantic macros (e.g., `\model`) defined once in `math_commands.tex` over ad-hoc formatting. Section files start with `\section`/` \subsection` headers; keep titles in Title Case. Use `%` comments sparingly and group related equations with clearly labeled `\label{}` keys following the `section-topic` pattern (`sec:sink_analysis`). Figures and tables should use `fig:` and `tab:` prefixes.

## Testing Guidelines
Before pushing, run `latexmk -pdf -halt-on-error main.tex` to ensure the manuscript compiles without warnings. Rebuild `arxiv.tex` whenever bibliography or macro changes occur. Visual-diff key figures (`fig/`) after regenerating plots and confirm referenced filenames match case-sensitive filesystem paths. Cite only entries that exist in `iclr2026_conference.bib`; unused entries should be moved to `references.bib` or pruned.

## Commit & Pull Request Guidelines
This archive lacks Git history, so adopt Conventional Commits (`feat:`, `fix:`, `docs:`) with concise 72-character summaries. Reference the section you touched in the body (`tex/3_exp.tex: clarify ablation setup`). Pull requests should summarize manuscript changes, list any regenerated assets, and attach PDF diffs or screenshots for layout-affecting edits. Link to tracking issues or submission tasks when available.
