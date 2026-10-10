---
name: working-report
description: >-
  Write and maintain formal reports for ongoing research, using English and
  LaTeX by default. Use for working papers and research reports that explain
  the study, document evidence, and identify open questions. Make the main
  text understandable from the reader's background, explain complex supporting
  tools in supplementary information, and keep execution history in separate
  agent notes.
---

# Working Report

Write a self-contained report of what the study establishes and what remains open. Make it suitable to share with an advisor or collaborator. Let the explanation and evidence determine its length.

## Set the Scope and Read the Sources

Default to English and LaTeX. Follow the user's requested language and format, including Markdown. Determine the research question, current stage, report scope, available materials, and target file from the conversation and workspace. Ask about missing information that would change the report. Keep edits in the requested report and its supporting files; a separate publication manuscript needs its own editing request.

Read the relevant report, project instructions, code, experimental records, results, and literature. Use code as evidence for implemented behavior, raw data or validated analyses for empirical findings, and primary literature for borrowed claims. Keep the source paths or identifiers needed to recheck important statements.

Write from available evidence. Run additional analyses or experiments within the user's requested scope. Describe pending research by its purpose and current status.

## Separate the Report From Agent Notes

The report and its supplementary information (SI) contain the science: motivation, necessary foundations, formulation, methods, setup, results, interpretation, limitations, hypotheses, and planned investigations.

Keep execution history in one agent-facing Markdown file. Reuse a suitable existing file; otherwise use `agent-notes.md` beside the report. Record significant attempts, errors, fixes, decisions, unresolved execution issues, evidence paths, and commands or settings needed to resume work. Keep a short current-state summary and dated execution entries. Keep this file outside the reader-facing deliverables.

Include scientifically meaningful negative results and rejected hypotheses in the report. State the method, assumptions, and conditions each finding concerns. If an error invalidates evidence, revise the report to state what the remaining valid evidence supports. Put the debugging and correction history in the agent notes.

## Structure the Report

Choose sections and their order to fit the study. Explain why the problem matters, what is modeled or measured, how the method follows from the formulation, what was done, what the evidence shows, and which questions remain.

Write connected paragraphs with one main point each. Explain why a concept, equation, figure, or experiment is needed before using it. State the reasoning that connects successive steps. Keep terminology and symbols consistent throughout the report.

Explain the scientific mechanism and why each methodological choice fits the problem. Distinguish deductions, assumptions, approximations, empirical choices, and interpretations. State the conditions under which each conclusion holds.

## Explain Concepts in Context

Assume secondary-school mathematics and science unless the user gives a different baseline. Explain unfamiliar concepts at their first use. Connect each new concept to quantities, observations, or relationships already introduced. Aim for enough understanding to follow and assess the study.

When `toturial-skill` is available, read it and use its prerequisite analysis and first-principles method. Use the known reader baseline and report objective. Apply the teaching method while composing the complete report.

Write natural, precise academic prose throughout the report and SI. Use specific claims, clear sentences, and transitions that follow the actual argument. Remove generic praise, inflated language, empty emphasis, stock transitions, and repetitive summaries. Integrate explanations where the argument needs them. Reader exercises and comprehension checks belong only in explicitly requested conversation.

For each formula or theorem, explain what it says, when it applies, how it is used here, and what the result means. Aim for understanding and correct use. Include proofs or detailed derivations when the user requests them or when they support the study's own theoretical contribution.

Explain simple tools in the main text. For a complex tool, give enough explanation in the main text to understand and use it in this study. Put the fuller explanation in a dedicated SI section and link to it at the point of use. Write the SI for the same reader baseline. Explain the tool's meaning, conditions, and application so the reader can understand it without searching for missing foundations. Use subsections when helpful.

Define new symbols before using them. Give domains, units, tensor axes or shapes, and boundary or initial conditions where relevant. Explain how illustrative calculations or diagrams relate to the study's actual evidence.

Use the user's questions to identify missing definitions or reasoning steps. During a requested revision, repair those gaps in the report and update affected passages. Keep each explanation proportional to its role in the study.

## Make Research Status Visible

Present scientific findings and open research questions in the main text. Report verified findings within their established scope in ordinary prose. Use these inline flags for unresolved content:

| Flag          | Meaning and required context                                                                                                                          |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Hypothesis`  | A proposed explanation or claim awaiting a discriminating test. State its basis and what evidence would bear on it.                                   |
| `Preliminary` | A finding supported by current evidence whose reliability or claimed scope still requires a specific check. State the evidence and the pending check. |
| `TODO`        | Research work still to perform, such as a derivation, comparison, measurement, or analysis. State what it should establish.                           |

Attach each flag to the specific passage, table entry, or figure statement it qualifies. Use consistent, unobtrusive formatting and explain the labels once if needed. Distinguish completed work from planned work, and state uncertainty beside the claim it affects. Keep execution fixes and agent reminders in the agent notes.

## Present Results, Figures, and References

For each result, state what it supports and what remains open. Give the setup, comparison, metric, units, uncertainty, and assumptions needed to assess it. Generate plots and tables from traceable data or stated calculations. Define axes and quantities, and write captions that can be understood on their own.

Draw publication-ready figures in the clean, precise style of Nature and PRL articles. Use clear layouts, crisp lines, and restrained colors that remain distinguishable. Use Times New Roman for figure text and compatible fonts for mathematical symbols. Size labels, legends, and annotations to look approximately as large as the body text after insertion at the intended width. Check exported figures at that size and verify their actual fonts. Keep editable sources. Use vector output where suitable and sufficient resolution for raster content.

Add verified references to the bibliography and cite them beside the claims they support. Check the bibliographic metadata and read the source to confirm its support. Reuse suitable existing entries. Use `article-reading` when the writing task requires help understanding a paper. Keep unverified reference candidates in the agent notes.

## Maintain a Coherent Current Version

Make each version of the report and SI a standalone account of the current study. Place new results where they belong in the argument. Replace outdated statements. Update all affected definitions, assumptions, methods, numbers, figures, tables, summaries, and conclusions. Adjust headings, transitions, and cross-references to keep the report consistent from beginning to end.

When a question or task is resolved, replace its flagged passage with the supported result or method. Remove outdated flags, caveats, and pending-work statements everywhere they appear. Keep only genuinely unresolved research questions open.

Order the report by scientific reasoning and experimental conditions. Keep the history of discovery, writing, debugging, and revision in the agent notes. Describe physical time evolution, experimental sequences, and algorithmic iterations when they are part of the science being studied.

Preserve source artifacts and valid user-authored content. Keep edits within the agreed scope. Record the evidence behind changed conclusions in the agent notes.

## Format and Verify

Use the project's file organization and build process where they fit the report. Start a new LaTeX report with a readable single-column layout and standard scientific typography. Choose packages and file structure to fit the content.

Format LaTeX with `latexindent`, enabling `oneSentencePerLine` and line-break modification. Keep each complete prose sentence on one source line, preserve paragraph breaks, and indent structured environments consistently. Disable fixed-width wrapping. Check that formatting preserves the content and LaTeX semantics.

Compile LaTeX with the available project toolchain and inspect the PDF. Check scientific consistency, references and citations, equations and symbols, figures and tables, and readability from the stated baseline. Fix build and presentation errors within scope. If compilation is unavailable, deliver the source and state that the rendered output is unverified.

## Review Independently and Deliver

By default, ask a fresh, independent subagent to review the report and SI before delivery. Give it the research goal, reader baseline, source files, rendered output, and supporting evidence. Let it assess the work directly from those materials.

Ask the reviewer to check:

- Section hierarchy and order, continuity of the argument, and consistency between the main text and SI.
- Technical correctness, assumptions, methods, results, citations, and whether the evidence supports each conclusion.
- The current scientific contribution, supporting evidence, originality relative to verified prior work, and remaining validation. Identify the further research needed for a future publication while preserving the working report's explanatory depth.
- Natural academic language, precise terminology, clear explanations, and unnecessary or formulaic wording.

Request specific, prioritized findings with locations and reasons. Check each finding against the evidence and make supported corrections throughout the affected parts. Rebuild and inspect changed output, then have the reviewer recheck substantive fixes. Continue until material issues that can be resolved within the writing task are addressed. Carry remaining research needs into the delivered report as limitations or TODOs. If subagents are unavailable, perform a self-review and state that independent review remains unperformed.

Deliver the report, any SI, and rendered PDFs when available. Briefly state what changed, what was checked, and what remains unresolved. Share or submit the report only when the user requests it.
