# Research Workspace

## Establish the Root

Confirm the actual workspace path and host. Inspect existing files, instructions, Git state, data locations, and active jobs before reorganizing anything. Preserve a sensible existing layout. For a new workspace, use the categories below as needed and record the actual map in its `AGENTS.md`.

| Location                | Purpose                                                                                        | Default Git policy                                         |
| ----------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `AGENTS.md`             | Research objective, operating requirements, environment, resources, and workspace entry points | Track                                                      |
| `memory.md`             | Durable project knowledge, user-requested memories, and decision rationale with evidence       | Track                                                      |
| `.gitignore`            | Exclusions for generated and local-only material                                               | Track                                                      |
| `src/`                  | Maintained implementation, preparation, evaluation, analysis, and plotting scripts             | Track                                                      |
| `configs/`              | Authored experiment and execution configurations, including JSON or YAML                       | Track                                                      |
| `datasets/`             | Original and prepared datasets or pointers to external data stores                             | Ignore bulk contents                                       |
| `models/`               | Acquired or selected model weights and checkpoints                                             | Ignore bulk contents                                       |
| `simulations/`          | Maintained simulator inputs, setup files, and job scripts                                      | Track authored inputs                                      |
| `results/<run-id>/`     | Generated measurements, manifests, CSV/JSON results, logs, checkpoints, and intermediate plots | Ignore                                                     |
| `figures/`              | Selected report figures, preferably PDF, with stable descriptive names                         | Track selected figures                                     |
| `references/`           | Curated source notes or reference metadata                                                     | Track curated material                                     |
| `references/downloads/` | Downloaded papers and other source caches                                                      | Ignore                                                     |
| `reports/`              | Reader-facing report prepared with `working-report`                                            | Track source and final deliverables; ignore build products |
| `notes/agent-notes.md`  | English current-state summary and dated research record                                        | Track                                                      |
| `bak/`                  | Useful superseded material retained for recovery or reuse                                      | Ignore                                                     |
| `trash/`                | Disposable material retained temporarily                                                       | Ignore                                                     |

Create categories when they have content. Keep each artifact in one canonical location and use references to large external datasets or models when copying would be wasteful. Store the acquisition or preparation recipe and the identities of external inputs in tracked configuration or records.

Keep generated simulation output under `results/<run-id>/`, even when the maintained simulator inputs live in `simulations/`. Put model implementations in `src/` and selected weight files in `models/`. This keeps useful source files separate from bulk outputs.

Use `working-report`'s internal report layout under `reports/`: a thin `main.tex`, chapter files in `chap/`, compilation output in `build/`, and final `main.pdf` beside the entry point. Reference selected PDFs from `figures/` through paths that resolve from the report directory.

## Maintain Instructions, Memory, and Records

Use the templates in `assets/workspace/` for a new workspace. Fill their fields with confirmed facts and remove irrelevant placeholders. For existing files, merge the needed information into the current structure instead of overwriting valid instructions or records.

Keep `AGENTS.md` short and stable. It identifies the goal and acceptance criteria, protected inputs, environment and commands, resource boundaries, and canonical paths. Point to root-level `memory.md`, the primary agent record, and the report. Revise it when the user's goal or an operating requirement changes.

Organize `memory.md` by subject rather than chronology. Keep user context worth remembering, settled choices and their reasons, verified project knowledge, and reusable lessons. Each entry states its scope and a source or evidence pointer; include a version or verification date when the fact can change. Preserve uncertainty explicitly. When the user asks to remember an operating rule, put the rule in `AGENTS.md` and link to it from memory only when additional rationale is useful.

Keep one primary agent record. Start it with the active subtask, current findings, running work, unresolved decisions, remaining resources, and the next justified action. For running work, include the host, job identifier, output path, last check, and next check. Follow with dated entries that state the question, relevant inputs or run identifier, action, observed evidence, interpretation, and next decision. Record operational causes as hypotheses until supported. Preserve source pointers and enough context to understand earlier failed attempts without loading their full logs.

On entry or resumption, read `AGENTS.md`, `memory.md`, and the current-state summary, then open only the records needed for the next decision. Keep each fact in its primary file. Link from current state to established memory, and from memory to the experiment that supports it. Correct outdated summaries in place while retaining useful dated evidence in the agent record. Reuse established record paths when organizing an existing workspace.

For each run, keep the exact command, input identities, configuration, environment, seeds, validation evidence, and code version alongside its outputs. Identify the executed code with a commit plus tracked changes and relevant untracked files, or a snapshot of the source and configuration actually used. Keep these generated manifests and snapshots locally in the ignored run directory. Summarize their scientific meaning in the tracked Markdown record.

## Apply Git Policy by File Purpose

Use the provided `.gitignore` as a starting point and adapt paths to the actual workspace. Ignore a whole directory only when it contains local-only artifacts. If an existing `models/` directory holds source code, narrow its exclusions to weight files or checkpoint subdirectories. Generated CSV, JSON, manifests, predictions, logs, and similar outputs belong in ignored locations. Authored JSON configurations and small curated source inputs remain eligible for tracking. Preserve datasets and evidence on disk even when Git ignores them.

Check representative result and configuration paths with `git check-ignore` when Git is available. Inspect the staged paths before an authorized commit. Existing tracked files remain tracked when ignore rules change; explain any needed tracking change before removing them from the index. Keep credentials, raw private data, caches, and bulk artifacts outside commits. Keep internal Markdown records tracked and separate from reader-facing reports.

## Clean Without Losing the Evidence

Classify a file by its role before moving or deleting it:

- Keep original inputs, user-authored material, active checkpoints, and valid evidence needed by current conclusions or reproducibility.
- Keep valid negative findings with the relevant experiment evidence. A method's scientific failure differs from a broken command or invalid artifact.
- Move superseded material with a concrete recovery or reuse purpose to `bak/`. Give it a descriptive location and record why it was retained.
- Move disposable material to `trash/` when recovery may still be useful. Permanently delete only confirmed disposable agent-generated artifacts within the authorized workspace and cleanup scope.

Before cleanup, resolve the exact targets and check references from active jobs, analysis, figures, and reports. After moving retained artifacts, update evidence pointers and dependent paths so the files remain traceable. Treat symlink targets outside the workspace as external data. When ownership or retention value is unclear, preserve the files and ask. Summarize material cleanup and whether recovery is possible. Keep archived contents out of active plans and default recursive searches; consult them only to answer a specific question.
