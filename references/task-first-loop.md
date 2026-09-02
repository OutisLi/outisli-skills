# Task-First Loop

Use this protocol to keep teaching attached to a concrete technical outcome.

## 1. Establish the Outcome Contract

Infer as much as possible before asking. Capture internally:

- the deliverable or decision;
- what counts as success;
- constraints such as time, accuracy, compute, safety, format, or scope;
- available artifacts, tools, data, and prior attempts;
- which parts the user wants to perform versus delegate.

After the baseline/target calibration, ask at most one additional blocking
question, and only if different answers would lead to materially different
actions. If the user has already said they are new to the required background,
do not ask them to rate that background again.

## 2. Inspect Before Teaching

When the task involves existing reality, inspect it:

- read the relevant file, code path, configuration, log, plot, or data sample;
- check the installed version or current official documentation when behavior
  may have changed;
- identify what is observed, what is inferred, and what is still unknown;
- reproduce a failure minimally when diagnosis is part of the task.

Do not teach an imagined version of the user's system when direct evidence is
available.

## 3. Build the Minimum Map

Separate two dependency types:

- **Task dependencies:** actions or decisions that must happen in order.
- **Knowledge dependencies:** concepts needed to choose, understand, or verify
  those actions.

Keep only dependencies on the critical path to the requested outcome. Mark
others as skip-for-now. Expose the map only when the user needs orientation;
normally, state the current step and the next one.

## 4. Select the Next Executable Step

Choose the smallest step that produces useful evidence or unlocks the next
decision. Favor steps that are:

- reversible or read-only when uncertainty is high;
- discriminating between competing explanations;
- small enough that failure is interpretable;
- representative enough to reveal whether the approach is viable.

If several concepts are missing, teach the earliest one that blocks this
step, not all of them.

## 5. Deliver a Step Packet

For a nontrivial step, communicate the following information in a natural
order:

1. **Now:** the single action or decision.
2. **Why:** the causal or logical reason it is needed.
3. **Model:** the minimum concept required to understand the action.
4. **Inputs:** data, assumptions, units, interfaces, and preconditions.
5. **Expected output:** the observable result, including shape or range when
   relevant.
6. **Verification:** how to distinguish success from apparent success.
7. **Branches:** what different outcomes imply.

Do not mechanically print all seven labels for a simple step. The information
must be present when it affects a decision, not when it would add ceremony.

## 6. Execute or Hand Off

If the agent can safely perform the action within the user's request, do so.
Explain the decision before or alongside the action, then report only observed
results.

If the user must act, provide one copyable action and say exactly what output,
measurement, screenshot, or decision to return. Stop there. Do not simulate
their response or continue down a branch without evidence.

## 7. Interpret the Evidence

After an action:

- compare observed output with the stated expectation;
- explain what the evidence supports;
- state what it cannot establish;
- update the task hypothesis and the user's mental model;
- choose the next smallest discriminating action.

A successful command is not automatically a valid scientific result. A
plausible plot is not automatically evidence for the intended mechanism.
Verify at the level required by the deliverable.

## 8. Handle Failure as Information

Do not jump to a broad rewrite or a new theory. First determine whether the
failure is in:

- the conceptual model;
- assumptions or boundary conditions;
- data or measurement;
- method selection;
- implementation or configuration;
- environment or dependency;
- interpretation of otherwise valid output.

Change one variable at a time when practical. Repair the earliest confirmed
cause, then repeat the smallest relevant verification.

## 9. Completion Gate

A task is complete only when the deliverable's success criterion is observed,
or when a clearly identified external dependency prevents further progress.
Close in the conversation with:

- the verified result;
- the causal chain from inputs through method to output;
- how to reproduce the essential steps;
- assumptions and remaining uncertainty.

Do not replace this with a claim that the user has mastered the wider field,
and do not create a separate learning document unless explicitly requested.
