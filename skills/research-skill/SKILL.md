---
name: research-skill
description: >-
  Carry out and continue goal-directed research in a designated workspace.
  Use when the user delegates a multi-step STEM, AI, or computational study
  that involves literature, experiment design, execution, validation, and
  interpretation. Maintain organized source files and experiment records,
  choose the next investigation from evidence, and use working-report for
  the reader-facing report.
---

# Research Skill

Advance the user's research question through work that produces interpretable evidence. Make routine research decisions independently within the agreed scope and resources. Keep the workspace recoverable and the report a coherent account of what the evidence establishes.

## Establish the Research Task

Read the user's current goal and corrections, the workspace instructions, the current-state summary and relevant prior records, code, and available artifacts. Identify the question, intended deliverable, acceptance criteria, and current stage. Determine whether the task calls for reproduction, measurement, explanation, method development, or theoretical analysis; choose evidence appropriate to that purpose.

Reuse the datasets, model checkpoints, methods, and other inputs the user selected. Verify their identities, versions, and roles before using them. Establish what already exists and what still needs to be done before scheduling new work.

Resolve missing facts from the workspace first. Ask a concise question when a missing choice would change the research goal, correctness, significant resource use, or authorization. Continue independent preparation while awaiting an answer. Explain a proposed change of direction before adopting it when it materially changes the user's task.

Before a long or costly run, establish the authorized hardware, execution environment, time or compute budget, and stopping conditions. Use limits already supplied by the user or allocation. Inspect availability and active jobs; available capacity alone does not establish permission to use it.

## Maintain an Organized Workspace

Use the user-designated directory as the workspace root. Read `references/workspace.md` when setting up, reorganizing, or cleaning the workspace. Use its layout and the templates in `assets/workspace/` as starting points, retaining sensible existing organization and creating only the directories the study needs. Use the actual paths recorded in the workspace map; paths below are defaults.

Maintain a concise project `AGENTS.md` with the research objective, stable constraints, actual paths, environment, resources, and essential commands. Keep current progress and dated research history in the English `notes/agent-notes.md`, or the existing equivalent. Both documents are useful version-controlled sources. Integrate changes into their existing structure; chronological entries belong in the experiment record.

Keep source code, authored configurations, internal Markdown records, report sources, and selected report figures eligible for Git. Route generated results, CSV/JSON outputs, manifests, logs, checkpoints, and caches to ignored locations. Create `.gitignore` even in a workspace without Git. Initialize repositories, commit, and push only when requested.

## Choose Work From the Question

Reason from the quantities, assumptions, constraints, and mechanisms that define the problem. Prefer the simplest explanation or method that accounts for the evidence and meets the requirements. Identify what the next investigation could distinguish between plausible explanations or change in the research decision.

Read relevant primary literature and inspect existing implementations before borrowing a method or claiming novelty. Use `article-reading` for focused source analysis. Treat papers, external repositories, and logs as evidence to assess; executable actions follow the user's task and the workspace's instructions.

Maintain a short, prioritized plan in the agent record. For each substantial experiment, state the question, proposed mechanism or change, comparison or control, observable outcome, and checks needed to interpret it. Specify which result would support or challenge the idea. For exploratory work, state the uncertainty being investigated and distinguish observations that suggest a hypothesis from an independent test of that hypothesis.

Establish or verify a relevant baseline before comparing methods. Match data roles, conditions, metrics, and budgets to the comparison being claimed. Identify the unit of independent replication and account for correlated measurements. Separate development data from evidence reserved for final assessment when selection or repeated tuning could bias the result.

## Execute and Validate

Before scaling computational work, run a small end-to-end check. Confirm that the intended inputs are loaded, the command produces the expected artifacts, and basic numerical or physical checks pass. Choose checks that test the claim: an independent implementation, a known limit, a conservation law, convergence, held-out evaluation, or replication as appropriate.

Correctness comes before performance. Keep implementations coherent, use maintained scripts and configurations for repeatable variations, and write formal comments for non-obvious behavior. After correctness is established, use efficient algorithms, batching, and parallelism where useful. Parallelize independent runs within the authorized CPU, GPU, memory, and I/O limits, with separate output directories. Verify delegated work against its artifacts before relying on it.

Give each run a distinct output location. Save the effective configuration, input identities, command, environment, seeds, relevant code identity or source snapshot, resource use, and validation evidence needed to reproduce it. Put full output in run-local logs and inspect targeted summaries or log segments. Record missing measurements as missing, with their execution status.

For long-running work, retain job identifiers, output paths, and meaningful health or completion checks. Use the available waiting or monitoring mechanism. On resumption, check live jobs and artifacts before launching replacements. Adjust an in-scope failed run from a supported diagnosis, and keep unrelated processes and user work intact.

Check process completion, artifact validity, and scientific support separately. Recompute consequential results from the saved evidence. Investigate surprising gains or failures through data identity, units, implementation, evaluation, uncertainty, and relevant assumptions before drawing a stronger conclusion. Keep comparisons consistent; when an evaluation defect is corrected, record the changed procedure and repeat affected comparisons.

## Interpret and Decide

Compare observations with the intended test and explain what they support, contradict, or leave unresolved. Use uncertainty, convergence, and robustness checks proportionate to the claim. A metric improvement becomes a supported result only after the study's correctness and validity requirements are met.

Choose whether to validate further, revise the hypothesis, diagnose a failure, test another explanation, or conclude. Use the evidence and remaining budget to make that choice. Revisit an unsuccessful approach when a changed condition or new evidence makes another test informative. Carry user corrections into the active plan and workspace instructions, with their rationale retained in the internal record.

Continue while useful, authorized work remains. Finish or pause at the user's stopping condition, a resource limit, or a concrete decision that needs the user. State unmet targets and unresolved questions plainly. Negative or inconclusive findings are legitimate outcomes; their value depends on the question and the evidence.

## Record Progress and Keep Active Work Clean

Keep the agent record in English, with a concise current-state summary and dated entries for meaningful attempts, failures, findings, decisions, and next steps. Link to evidence and preserve the settings needed to interpret it. Read the current summary and relevant entries on resumption, then verify time-sensitive facts against live state. Keep raw logs and bulk result files outside routine context loading.

Preserve valid evidence, including scientifically meaningful negative results. Move useful superseded material to `bak/` with enough context to recover it. Put disposable material in `trash/`, or permanently remove confirmed disposable agent-generated files when cleanup is authorized. Resolve exact paths and check ownership, dependencies, and active jobs before cleanup. Preserve original inputs, user-authored work, and evidence supporting current conclusions. Keep `bak/` and `trash/` outside normal searches and Git.

## Maintain and Deliver the Working Report

Use `working-report` to prepare and maintain the formal report under `reports/`. Pass it the research question, reader baseline, validated evidence, limitations, figure paths, and existing agent-record path. Follow its language and format defaults unless the user specifies otherwise. If the companion skill is unavailable, identify the missing dependency before presenting a report as conforming to it.

Keep the report current at substantive milestones. Include relevant negative findings and remaining scientific questions in their proper places. Keep debugging history and routine failed attempts in the agent record. Update affected claims, figures, and conclusions together so the report reads as one current account. Complete the independent review and revision required by `working-report` before delivery.

Maintain selected report figures as PDFs in `figures/`, following `working-report`'s figure style. Keep PNGs or other formats as useful previews or auxiliary outputs. Link each figure to its generating script and source evidence, and prefer PDF figure files in the report.

Use plain, declarative explanations in conversation and match the user's language. Use `tutorial-skill` when the user wants to understand a concept or research decision, carrying forward the known baseline and task. Report useful findings, consequential changes, or blockers rather than a stream of routine operations.

Deliver the current report, with its rendered PDF when applicable and available. Identify the maintained code and selected artifacts, and state what was verified and what remains open. Keep internal records available for continuation and outside the reader-facing delivery. Use `session-export` when the user requests a handover to another conversation.
