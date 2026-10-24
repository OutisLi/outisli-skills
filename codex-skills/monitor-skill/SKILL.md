---
name: monitor-skill
description: >-
  Monitor long-running jobs in Codex with duration-aware waits and focused
  status checks. Use when a computation, build, batch, or remote job needs
  continued follow-up while it runs. Estimate the remaining time, advance
  independent work when available, and verify completion before continuing.
---

# Monitor Skill

Keep long-running work observable while minimizing repeated model calls and log output. Follow the user's authorized task through waiting, verification, and the next dependent action.

## Establish the Job and Its Signals

Identify the host, workspace, scheduler job ID or process identity, output paths, and the user's stopping condition. Reuse a running job when continuing existing work. Record these details and the next check in the existing task record when one is available.

Confirm that submission succeeded, then distinguish queueing, initialization, and useful progress. Check for startup errors and verify that the intended inputs are loaded. A queued job has not started its computation. Use the scheduler's state or the owned process's exit status as the primary lifecycle signal, with targeted log and artifact checks for health and progress.

Estimate remaining time from a comparable run, a small representative check, or observed progress and throughput. State the basis and uncertainty. Keep queue delay separate from runtime, and revise the estimate when actual progress differs from it.

## Choose the Next Check

After the startup check, aim to check again after half the estimated remaining time, capped at 30 minutes. Use a practical minimum interval suited to the job's output cadence so successive estimates do not produce rapid polling near completion. When runtime is unknown, begin with a short informative interval and increase it after healthy checks, up to the same cap. Bring a check forward for an error, a missed expected milestone, or a user request.

Set the next check time before choosing what to do while the job runs:

- If useful independent work is available, advance it within the authorized scope and return to the job by the check time. Keep work that requires the pending result until that result is verified.
- If no independent work remains, use an interruptible wait or sleep until the next check. Prefer an existing process handle that returns early on exit. Respect the harness's per-call wait limits; when a wait must be split, continue waiting for the remaining interval without issuing extra job-status commands between segments.

Waiting occurs in the tool or operating system. Keep routine waiting output quiet and avoid starting model-driven subagents merely to poll. Batch checks of related jobs when their check times coincide.

## Use the Available Continuation Mechanism

Use a native completion event when the active Codex environment provides one. If the user requests follow-up after the current turn ends and a same-chat scheduler is available, register the follow-up before ending the turn, using the next-check interval above. Retain its identifier, update its timing as the estimate changes, and remove or disable it when monitoring finishes. Scheduled checks still invoke the model; report only meaningful changes or decisions.

A background shell or asynchronous hook alone does not guarantee a new Codex turn. Keep waiting in the active turn when no verified continuation mechanism is available. If runtime limits prevent continued waiting, report the last verified state and the action needed to resume. This skill defines waiting behavior; installing it does not register hooks, schedules, or a background service.

## Inspect, Verify, and Continue

At each check, read the smallest useful status summary and new log segment. Check progress against the estimate and look for actionable errors. Treat quiet logs as inconclusive. Treat a failed SSH or status query as loss of visibility until a successful query establishes the job's state.

When execution ends, check the exit status or scheduler result, the expected artifacts, and the task's acceptance criteria separately. For scientific work, verify convergence and relevant numerical or physical checks before using the output. Preserve missing or incomplete results as such.

On failure or stalled progress, inspect the evidence before proposing recovery. Resume, rerun, cancel, or change a job only within the user's authorization, checking its current identity first. Keep the recorded status and evidence pointers current. Continue dependent work after validation, or report the completed result, a concrete blocker, or the user's stopping condition.
