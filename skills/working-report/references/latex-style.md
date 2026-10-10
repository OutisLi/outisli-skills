# Default LaTeX and Table Style

## Template Files

For a new report, copy `chap/`, `report-style.tex`, `.latexindent.yaml`, `.latexmkrc`, `.gitignore`, and the bundled class and bibliography dependencies with their notices into the report directory. Use the bundled `main.tex` as the entry point by default. Only when the user explicitly requests the arXiv template, copy `main_arxiv.tex` as the report's `main.tex` and include `arxiv-style.tex`. Keep the unused entry-point template in the skill directory. Supply author information only from confirmed context. For an existing report, integrate the shared settings and preserve its content and compatible file organization.

Keep the bundled class, bibliography style, journal-abbreviation files, and their notices together. They are runtime dependencies; copy them unchanged. The template is self-contained apart from standard TeX packages.

## Project Structure

Keep `main.tex` as a thin entry point containing metadata, preamble loading, and chapter inputs. Put the abstract and each chapter in separate files under `chap/`. Rename, add, or remove chapter files to match the study's argument. A large chapter can use a subdirectory such as `chap/methods/` and include its parts through `\input`; resolve paths from the project root.

Create `build/` for compilation products, formatter logs, and backups. The supplied `.latexmkrc` makes it the default build directory. Keep the finished `main.pdf` beside `main.tex`. Include the supplied `.gitignore` even when the report directory has not been initialized as a Git repository. It excludes build products and backups while leaving final PDFs, `.tex` files, references, and figure sources available for version control.

## Default Layout: wlscirep

Use `\documentclass[fleqn,12pt]{wlscirep}` and load `report-style.tex`. The bundled class defines:

- A single text column on US Letter paper, with 2 cm side margins and 2.25 cm top and bottom margins.
- 12 pt Times-family body text and mathematics through `mathptmx`, with Helvetica-family title and headings.
- A left-aligned bold 20 pt title, a structured author and affiliation block, and an abstract below the title.
- Left-aligned display mathematics through `fleqn`.
- Bold sans-serif caption labels and period separators. Single-line captions are centered; longer captions use ragged-right alignment.
- Superscript numerical citations and the `naturemag-doi` BibTeX style.
- Empty headers and a bottom-right page/total-pages footer; the first page has no footer.

Load `chap/abstract.tex` before `\begin{document}` because the class inserts its abstract through `\maketitle`. Keep the abstract to prose and inline mathematics. Use `\raggedbottom` and `\thispagestyle{empty}` as shown in the starter. The layout sets typography; choose scientific section headings and order for the study.

## Optional Layout: arXiv

The explicit arXiv entry point uses `\documentclass[11pt]{article}`, `report-style.tex`, and `arxiv-style.tex`. It defines:

- A single column on US Letter paper, with a 5.5 in text width, 9 in text height, and 1 in top margin.
- 11 pt Times-family body text, centered display equations, and bold serif headings.
- A centered bold title between a 4 pt upper rule and a 1 pt lower rule.
- Unindented paragraphs separated by 5.5 pt, and standard bottom-centered page numbers after the unnumbered title page.
- The same superscript numerical citations and `naturemag-doi` bibliography style as the default layout.

Load `chap/abstract.tex` inside the document after `\maketitle`, as shown in the arXiv starter. Keep table bodies, notes, status labels, and SI numbering on the same shared definitions in `report-style.tex`.

## Table of Contents

When including a table of contents, place `\tableofcontents` after the abstract and before the main sections. Use the shared `titletoc` settings in `report-style.tex` for both layouts. Section, subsection, and subsubsection entries begin at `0em`, `1em`, and `2em`, respectively. `\ReportContentsStyle` keeps the contents type compact and sets its baseline distance to `1.08` times the surrounding body-text value. Each entry occupies its own paragraph; its number is followed by the title, continuation lines align with the title, and page numbers align at the right margin. Keep headings concise and maintain these small spacing differences when adapting the report.

## Bibliography and Supplementary Information

Use one shared bibliography. Add `\bibliography{references}` when a populated, verified `references.bib` is present. The bundled bibliography style uses the DOI field directly as a link: store each verified DOI as a complete `https://doi.org/...` resolver URL and check the exported link.

Add `\input{chap/si}` when the report has supplementary material. That file calls `\beginsupplement` once, followed by `\section*{Supplementary Information}` and its sections. This resets section, equation, figure, and table numbering to the S-prefixed series and gives their hyperlinks distinct targets. Split long SI sections into additional files under `chap/` as needed.

Use PDF figure files in `\includegraphics` by default. Keep the separate figure requirement: Times New Roman inside figures, with readable text at the final insertion size. PNGs and other formats may accompany the PDF as previews or auxiliary outputs.

## Research Status Labels

Use `\ReportStatus{Hypothesis}`, `\ReportStatus{Preliminary}`, and `\ReportStatus{TODO}` at the start of the statement they qualify. The shared command renders a bold bracketed label, such as **[Hypothesis]**. Keep the explanation after the label in normal type. Use the same command in the main text, SI, and table notes.

## One Table Style Throughout

Apply `\PaperTableStyle` inside every table float in both the main text and SI. Its definition in `report-style.tex` sets centering, `\footnotesize`, 3 pt column padding, and a row-spacing multiplier of 1.10. Use `\PaperTableNotesStyle` for `\scriptsize` notes.

Use `threeparttable` to group the caption, table, and notes. Use a short, one-line caption as the table title, placed above the table, with the label immediately after it. Put definitions and qualifications in the notes below. Use `booktabs` rules: `\toprule`, `\midrule`, `\bottomrule`, and `\cmidrule(lr)` for grouped columns. Use horizontal rules only.

Place `tablenotes[flushleft]` immediately below the table body, inside the same `threeparttable`, and begin it with `\PaperTableNotesStyle`. Use `\item[]` for notes that apply to the whole table. For a specific heading or entry, attach a superscript marker with `\tnote{a}`, `\tnote{b}`, and so on, and explain it with the matching `\item[a]`, `\item[b]`. Keep notes within the table width and use the package's shared alignment and spacing. Write complete, concise sentences that define metrics, shared conditions, emphasis, missing values, sources, or comparison limits. Apply this format to notes in both the main text and SI.

Use bold column headings and put units in the headings or a second header row. Left-align text labels and right-align numerical columns; use `siunitx` alignment when decimal alignment is useful. Use `L{width}`, `C{width}`, and `R{width}` for fixed-width wrapping columns. Use compact italic group rows when they help organize related results. Explain the meaning of any bold numerical entries in the caption or notes.

For numerical tables, use `tabular*` at `\linewidth` with `@{\extracolsep{\fill}}` and an empty trailing edge. For prose-heavy tables, use `tabularx` at `\linewidth`, with fixed label columns and flexible `X` columns. Fit wide tables by wrapping headings, adjusting column widths, or splitting related blocks while retaining the shared type size and spacing.

This example shows the table structure. Replace its placeholder headings and entries with the report's actual quantities and verified values.

```latex
\begin{table}[t]
    \PaperTableStyle
    \begin{threeparttable}
        \caption{Comparison of the measured quantities.}
        \label{tab:comparison}
        \begin{tabular*}{\linewidth}{@{\extracolsep{\fill}}lrr@{}}
            \toprule
            \textbf{Quantity} & \textbf{Method A}\tnote{a} & \textbf{Method B}\tnote{b} \\
            \midrule
            Metric (unit) & -- & -- \\
            \bottomrule
        \end{tabular*}
        \begin{tablenotes}[flushleft]
            \PaperTableNotesStyle
            \item[] State conditions shared by all entries and the meaning of emphasis.
            \item[a] Explain the condition or qualification attached to Method A.
            \item[b] Explain the condition or qualification attached to Method B.
        \end{tablenotes}
    \end{threeparttable}
\end{table}
```

## Formatting and Build

Use the bundled `.latexindent.yaml` for one complete prose sentence per source line. Format authored `.tex` files, then build from the report directory:

```bash
mkdir -p build
latexindent -m -l=.latexindent.yaml -c=build -w main.tex report-style.tex chap/*.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
cp build/main.pdf main.pdf
```

For the arXiv layout, also format `arxiv-style.tex`; the report's entry point and final PDF remain `main.tex` and `main.pdf`. Include authored `.tex` files in nested chapter directories in formatting. Preserve the bundled third-party files unchanged. Let the build tool run BibTeX when actual citations require it, and retain the intermediate files between build passes. Inspect the rendered title page, tables, captions, SI numbering, and hyperlinks after the build.
