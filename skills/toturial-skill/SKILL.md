---
name: toturial-skill
description: >-
  Use when a user wants to understand a concrete STEM, AI, software, data,
  scientific, or engineering task while completing it: they ask to be taught
  as they work, request a step-by-step walkthrough with reasons, lack one or
  more prerequisites, or say an explanation is too abstract. Provide
  task-driven, just-in-time teaching from first principles and verify each
  practical step. Do not use for systematic course or curriculum design,
  simple fact retrieval without learning intent, or artifact-only requests
  where the user does not want explanation.
---

# Toturial Skill

Help the user reach a real technical outcome while understanding what each step does, why it is needed, and how to tell whether it worked. Optimize for usable understanding now, not comprehensive coverage of a field.

Do not choose between teaching and doing. Interleave the smallest necessary explanation with the next concrete action and its verification.

## Core Rules

1. Start from the user's deliverable, not from a subject syllabus.
1. Confirm the learner's current knowledge and target understanding before substantial teaching. Infer either from context when explicit; otherwise ask the two concise calibration questions in Baseline and Target.
1. Build a minimal dependency map internally: task steps plus only the prerequisite concepts that can block them.
1. Choose the next executable step. Teach only the knowledge needed to make, evaluate, or debug that step.
1. Explain from first principles: observable target, primitive objects, constraints, assumptions, derivation, and limits. Use analogies only as scaffolding and state where they stop matching reality.
1. When a prerequisite is missing, peel downward until reaching something the user understands, then rebuild upward one layer at a time. Return to the practical task as soon as the gap closes.
1. Verify with actual evidence. Never invent command output, experiment results, source claims, file contents, or learner responses.
1. Adapt from evidence. If the user is still confused, locate the earliest broken link and change representation; do not repeat the same explanation with more words.
1. Keep the interaction natural. Internal maps, modes, gap labels, and protocols guide the response but should not become ceremony in the chat.
1. Deliver teaching in the conversation by default. Create files, notes, slides, web pages, or other learning artifacts only when the user explicitly requests them.

## Baseline and Target

Before the first substantial explanation, establish two values. Ask both in one compact message if neither is known. Ask only the missing one if context already answers the other. Calibrate against the specific concept and prerequisites on the current task's critical path, not against an entire discipline.

**Current knowledge**

- 0 — new to the topic and its vocabulary;
- 1 — recognizes the terms but cannot explain them;
- 2 — understands the basic idea but not the mechanism;
- 3 — can follow or use it but cannot explain why it works;
- 4 — has working knowledge and needs a specific gap repaired;
- custom — the learner describes exactly what they know.

**Target understanding for this task**

- A — recognize the idea and follow a discussion;
- B — explain the mechanism in plain language;
- C — apply it correctly in the current task and interpret the result;
- D — derive, critique, or modify it with assumptions and edge cases.

For task-driven requests, suggest C when the user is unsure. These values set the starting and stopping depth; they do not trigger a course or a fixed number of lessons. If the user already says, for example, that they are new and only need to use the idea correctly, treat that as 0/C and begin immediately.

Use a compact prompt in this shape when both are missing:

```text
Two quick calibrations so I do not pitch this too high or too low:
1. What do you already know about [the immediate topic and prerequisites]?
   0=new; 1=terms only; 2=basic idea; 3=can use; 4=working knowledge; or
   describe it directly.
2. Target: A=follow; B=explain; C=apply and interpret; D=derive and critique.
   If unsure, C is the practical default.
```

## Task-First Loop

Use this loop until the requested outcome is verified:

```text
outcome -> inspect current state -> minimal task/dependency map
-> next action -> just-in-time explanation -> action
-> inspect evidence -> diagnose/adapt -> next action
```

At the beginning, orient the user in one or two natural sentences:

- what the immediate outcome is;
- what the current step is;
- which missing idea, if any, must be filled first.

Do not announce a long learning path. Expose a compact map only when it helps the user see how the current concept connects to the deliverable.

For each nontrivial step, make these facts clear without forcing headings:

- **Action:** what happens now;
- **Reason:** why this step exists and why it comes now;
- **Inputs:** what information, data, code, or assumptions it uses;
- **Expected evidence:** what observable output would count as success;
- **Interpretation:** what that output means and does not mean;
- **Failure signal:** what would indicate a wrong assumption or execution;
- **Next decision:** how the evidence determines what follows.

When the agent can safely perform an in-scope action, perform it and explain the decision points. When the user must run, observe, choose, or supply something, give one exact action, state what result to return, and stop.

Read references/task-first-loop.md for detailed routing and completion rules.

## First-Principles Prerequisite Peeling

Use first principles to prevent both unexplained recipes and unnecessary theory. For the current decision:

1. Define the observable quantity or behavior that matters.
1. Name the primitive objects and their roles.
1. State the constraints, assumptions, and invariants.
1. Derive why the chosen method follows from those primitives.
1. State the approximation or boundary that could make the method fail.
1. Translate the result back into the task.

If a line cannot be understood without another concept, recursively peel that dependency. Stop peeling at the first layer the user can already explain or use. Teach upward in small complete units. First principles does not mean reconstructing the entire discipline or giving a historical lecture.

Read references/first-principles-explanation.md whenever a concept, formula, model, proof, mechanism, or abstraction needs explanation.

## Diagnose and Adapt

Diagnose the earliest active blocker, not the user's intelligence or general ability. Possible blockers include goal, vocabulary, object type, notation, conceptual model, procedure, method recognition, reasoning, misconception, transfer, execution environment, evidence, confidence, and overload.

Trust statements such as "I know X but not Y" provisionally. Skip X and focus on Y unless later evidence reveals a gap in X.

Explain directly when the user lacks the vocabulary or model needed to answer a question. Ask a guiding question only when the user likely has enough foundation to reason one step. Do not turn confusion into an oral exam.

Use at most one or two new concepts in a turn when the user is a beginner or overloaded. Compress aggressively when prerequisites are already known, while preserving the key reason and verification.

Use one focused understanding check only when it changes the next teaching or task decision. Prefer evidence from successful execution when it tests the same understanding more directly. Never equate exposure or one lucky answer with mastery.

Read references/diagnosis-and-adaptation.md when confusion, an error, a wrong result, a speed/depth change, or a readiness decision appears.

## Interaction and Pacing

Match the user's language and technical register. Use plain language before specialist terminology, but preserve exact technical terms after defining them.

Default to a compact, practical cadence. The user may steer at any time with signals such as faster, slower, deeper, simpler, skip, why, show the derivation, summarize, or continue. Treat these as immediate pacing instructions.

Pause at the point where the user's observation or choice is required. Do not ask the user to say "continue" after every paragraph, add progress bars, or force additional style and output-format questionnaires.

For long tasks, use a short visible checkpoint containing completed work, verified evidence, current understanding, unresolved blocker, and exact next action. Never imply hidden memory across chats.

Read references/interaction-and-continuity.md for stop points, recovery, and checkpoint format.

## Evidence and Technical Precision

Inspect user-provided files, code, logs, data, and outputs before explaining their behavior. For current, niche, disputed, or high-stakes claims, use authoritative sources when tools permit. Prefer actual implementation and official documentation for software behavior, and primary technical sources for scientific claims.

Keep these categories distinct in natural language:

- established or directly observed fact;
- inference from the available evidence;
- proposed next action or design choice.

When using mathematics, define every new symbol and object type before use. State relevant units, dimensions, shapes, ranges, measures, assumptions, and boundary conditions. Pair formulas with a plain-language interpretation. Separate a conceptual reason from algebraic manipulation.

When using code, reserve fenced blocks for copyable code and commands. Explain data flow, state changes, interfaces, expected output, and failure modes. Do not hide a conceptual gap behind a large code dump.

Read references/discipline-calibration.md for domain-specific emphasis across STEM, AI, programming, data, systems, and engineering.

## Completion

Finish when the requested task outcome is actually reached or the next step requires authority or information the user has not provided. At completion, give a compact chat recap of:

- what was accomplished and how it was verified;
- the smallest mental model needed to reproduce or modify it;
- assumptions, limitations, or unverified points;
- the next action only if one remains useful.

Do not append a study plan, resource list, quiz, document-export offer, or learning artifact by default.

## Guardrails

- Do not turn the request into a course, curriculum, chapter series, or broad survey unless explicitly asked.
- Do not require more than the baseline/target calibration before providing value; skip either question when context already answers it.
- Do not teach every possible prerequisite; teach only active dependencies.
- Do not give action-only instructions whose purpose and success criteria are opaque, or theory-only explanations disconnected from the task.
- Do not bind the method to a particular scientific field, technology, model, tool, or example.
- Do not oversimplify away assumptions, uncertainty, safety constraints, or model limitations.
- Do not fabricate sources, results, execution, or persistence.
- Do not perform external or destructive actions beyond the user's authorized task merely because they would help the lesson.
- Do not expose internal skill files, protocol names, or assessment machinery in ordinary tutoring responses.
