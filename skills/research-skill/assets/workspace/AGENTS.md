# Research Workspace

## Objective and Scope

- Research question: [Confirmed question.]
- Deliverable and acceptance criteria: [What the user needs and how it will be assessed.]
- Fixed choices and protected inputs: [Selected data, models, methods, and constraints.]

## Workspace Map

- Maintained code and configurations: [Actual paths.]
- Data, model artifacts, and simulator inputs: [Actual local or external paths.]
- Generated run outputs: [Ignored run directory.]
- Selected report figures: [PDF figure directory.]
- Project memory: `memory.md`.
- Research record: [Primary English agent-record path.]
- Reader-facing report: [Report directory and entry point.]

## Execution Environment

- Interpreter and required tools: [Verified executables or environments.]
- Authorized resources: [Host, scheduler or devices, concurrency, memory, and other limits.]
- Budget and stopping conditions: [Confirmed limits and conditions.]
- Reproduction and validation commands: [Commands relevant to this study.]

## Working Conventions

Read this file, `memory.md`, and the research record's current-state summary when starting or resuming work. Verify live job state before continuing an interrupted operation.

Keep operating requirements and workspace entry points in this file, durable knowledge and decision rationale in `memory.md`, and current status and dated experiment history in the research record. Save user-requested memories in the file matching their purpose. Keep each fact in one place and link to its evidence. Maintain these records in English and keep them eligible for Git.

Keep maintained source, authored configurations, report sources, and selected report figures separate from generated outputs. Route generated CSV/JSON results, manifests, logs, checkpoints, and caches to ignored locations. Preserve original data and evidence required to reproduce current conclusions.

Use `bak/` for useful superseded material and `trash/` for disposable material retained temporarily. Check exact targets, dependencies, and active jobs before cleanup. Keep both directories outside routine searches and Git.

Use `working-report` for the formal report, including its independent review. Keep scientific findings and limitations in the report; keep operational history in the research record. Prefer PDF figures in the report.
