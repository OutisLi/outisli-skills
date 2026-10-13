# LaTeX Templates and Table Style

## Template Files

Choose `assets/latex/` for an English report and `assets/latex-zh/` for a Chinese report. Each directory supplies a complete template. Copy its `chap/`, `report-style.tex`, `.latexindent.yaml`, `.latexmkrc`, and `.gitignore` into the report directory. Use its `main.tex` as the entry point. For English, also copy `wlscirep.cls` and the bundled bibliography dependencies with their notices; for an explicitly requested arXiv layout, use `main_arxiv.tex` as `main.tex` and include `arxiv-style.tex`. Keep unused entry-point templates in the skill directory. Supply author information only from confirmed context. For an existing report, apply the selected typography while preserving its content and compatible file organization.

Keep the bundled class, bibliography style, journal-abbreviation files, and their notices together. They are runtime dependencies; copy them unchanged. The template is self-contained apart from standard TeX packages.

## Project Structure

Keep `main.tex` as a thin entry point containing metadata, preamble loading, and chapter inputs. Put the abstract and each chapter in separate files under `chap/`. Rename, add, or remove chapter files to match the study's argument. A large chapter can use a subdirectory such as `chap/methods/` and include its parts through `\input`; resolve paths from the project root.

Create `build/` for compilation products, formatter logs, and backups. The supplied `.latexmkrc` makes it the default build directory. Keep the finished `main.pdf` beside `main.tex`. Include the supplied `.gitignore` even when the report directory has not been initialized as a Git repository. It excludes build products and backups while leaving final PDFs, `.tex` files, references, and figure sources available for version control.

## English Layout: wlscirep

Use `\documentclass[fleqn,12pt]{wlscirep}` and load `report-style.tex`. The bundled class defines:

- A single text column on US Letter paper, with 2 cm side margins and 2.25 cm top and bottom margins.
- 12 pt Times-family body text and mathematics through `mathptmx`, with Helvetica-family title and headings.
- A left-aligned bold 20 pt title, a structured author and affiliation block, and an abstract below the title.
- Left-aligned display mathematics through `fleqn`.
- Bold sans-serif caption labels and period separators. Single-line captions are centered; longer captions use ragged-right alignment.
- Superscript numerical citations and the `naturemag-doi` BibTeX style.
- Empty headers and a bottom-right page/total-pages footer; the first page has no footer.

Load `chap/abstract.tex` before `\begin{document}` because the class inserts its abstract through `\maketitle`. Keep the abstract to prose and inline mathematics. Use `\raggedbottom` and `\thispagestyle{empty}` as shown in the starter. The layout sets typography; choose scientific section headings and order for the study.

## Optional English Layout: arXiv

The explicit arXiv entry point uses `\documentclass[11pt]{article}`, `report-style.tex`, and `arxiv-style.tex`. It defines:

- A single column on US Letter paper, with a 5.5 in text width, 9 in text height, and 1 in top margin.
- 11 pt Times-family body text, centered display equations, and bold serif headings.
- A centered bold title between a 4 pt upper rule and a 1 pt lower rule.
- Unindented paragraphs separated by 5.5 pt, and standard bottom-centered page numbers after the unnumbered title page.
- The same superscript numerical citations and `naturemag-doi` bibliography style as the default layout.

Load `chap/abstract.tex` inside the document after `\maketitle`, as shown in the arXiv starter. Keep table bodies, notes, status labels, and SI numbering on the same shared definitions in `report-style.tex`.

## Chinese Layout

Use `\documentclass[UTF8,zihao=-4,fontset=none]{ctexart}`, the Chinese `report-style.tex`, and XeLaTeX. The style file selects the fonts explicitly. The template provides:

- A single column on A4 paper with 2.5 cm margins, 12 bp Song-style body text, two-character paragraph indentation, and approximately 20 bp baseline spacing.
- Fandol Song for Chinese body text, Fandol Hei for headings and bold Chinese text, and NewTX for matched Times-style Latin text and mathematics. Explicit font faces provide the required weights.
- A centered 25 bp title, a compact optional author/date block, and a centered 14 bp abstract heading. The abstract uses the body font and remains ordinary text that can continue onto another page.
- Left-aligned headings at 15, 14, and 12 bp, with Arabic numbering such as `1`, `1.1`, and `1.1.1` and consistent spacing above and below.
- Chinese contents, bibliography, figure, and table labels. Captions use 10.5 bp Song-style text with labels such as `图 1` and `表 1`, followed by a one-em space. Short captions are centered; multi-line captions form a justified paragraph.
- A black, linked table of contents with a centered 18 bp heading, body-size entries, dotted leaders, and right-aligned page numbers. Pages have no running headers and use centered footer page numbers.
- A numerical GB/T 7714-2015 bibliography through `biblatex` and Biber, with 10.5 bp entries, a compact baseline, and 3 bp between entries. Use normal-case author names and leave missing publication information unfilled.

Load `chap/abstract.tex` inside the document after `\maketitle`. Add `\tableofcontents` after the abstract when useful. Use the selected template's table, status-label, and SI commands throughout. Keep figure interiors in English and write captions in Chinese. The required fonts are supplied by TeX Live; keep the template independent of operating-system fonts.

## Table of Contents

When including a table of contents, place `\tableofcontents` after the abstract and before the main sections. Use the selected template's definitions and keep headings concise. Continuation lines align with the entry title, and page numbers align at the right margin.

The English layouts use `titletoc`: section, subsection, and subsubsection entries begin at `0em`, `1em`, and `2em`. `\ReportContentsStyle` uses compact type with a baseline distance of `1.08` times the surrounding body-text value.

The Chinese layout uses `tocloft`: body-size entries with body-text line spacing, bold top-level entries, and dotted leaders at all three levels. Top-level entries have 6 bp of preceding space; subsection and subsubsection entries indent by one and two Chinese character widths. The heading is centered. The template applies `hidelinks` locally to the contents, preserving clickable entries and leaving citation and other link styles unchanged.

## Bibliography and Supplementary Information

Use one verified `references.bib` for the report and SI. Keep bibliographic metadata complete even when the selected output style hides particular fields.

For English, add `\bibliography{references}` where the bibliography belongs. The bundled `naturemag-doi` BibTeX style uses the DOI field directly as a link: store each verified DOI as a complete `https://doi.org/...` resolver URL and check the exported link.

For Chinese, add `\addbibresource{references.bib}` in the preamble and `\printbibliography[heading=bibintoc,title={参考文献}]` at the bibliography position. With this style, `\cite{key}` produces superscript bracketed citations and `\parencite{key}` produces inline bracketed citations. Use Biber with the bundled `biblatex` settings; store DOI identifiers in the normal `doi` field even when the output style omits them.

Add `\input{chap/si}` when the report has supplementary material. That file calls `\beginsupplement` once, followed by an unnumbered SI heading in the report's language and its sections. This resets section, equation, figure, and table numbering to the S-prefixed series and gives their hyperlinks distinct targets. Split long SI sections into additional files under `chap/` as needed.

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

Use the selected template's `.latexindent.yaml` for one complete prose sentence per source line. The Chinese configuration recognizes Chinese sentence punctuation as well as English punctuation. Format authored `.tex` files, then build from the report directory:

```bash
mkdir -p build
latexindent -m -l=.latexindent.yaml -c=build -w main.tex report-style.tex chap/*.tex
latexmk -interaction=nonstopmode -halt-on-error main.tex
cp build/main.pdf main.pdf
```

The selected `.latexmkrc` chooses pdfLaTeX for English or XeLaTeX for Chinese; retain that engine choice when building. Chinese reports require CTEX, Fandol, NewTX, `biblatex-gb7714-2015`, and Biber from the TeX installation. For the arXiv layout, also format `arxiv-style.tex`; the report's entry point and final PDF remain `main.tex` and `main.pdf`. Include authored `.tex` files in nested chapter directories in formatting. Preserve the bundled third-party files unchanged. Let the build tool run BibTeX for English or Biber for Chinese when references are present, and retain intermediate files between build passes. Inspect the rendered title, abstract, contents, headings, tables, captions, SI numbering, and hyperlinks after the build. Check mixed Chinese/Latin text, embedded fonts, and missing-glyph warnings in Chinese reports.
