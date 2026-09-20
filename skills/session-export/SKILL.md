---
name: session-export
description: >-
  Produce a ready-to-paste handover prompt for continuing the current task in a
  fresh conversation, another agent, or another harness. Use when the user asks
  for session context or a handover they can copy into another conversation.
  Carry the user's goal, relevant environment, and evidence-grounded progress
  forward, with concise pointers to existing artifacts. Deliver the complete
  prompt directly in chat.
---

# Session Export

Give the receiving agent enough context to resume the user's work from a fresh conversation. Preserve information that would otherwise be lost, point to accessible artifacts, and leave room for independent judgment. Deliver a complete prompt the user can paste and send as-is.

## Establish the Active Task

Recover the current goal from the user's requests, incorporating later corrections and retaining relevant earlier requirements. Identify the desired outcome, completion criteria, and current activity state: active, paused, awaiting input or approval, or complete. Carry earlier work forward when it affects this task.

Use the conversation to recover intent, decisions, and non-persistent state. Make a few inexpensive, read-only checks when they materially improve the handover's accuracy. Label unchecked information by its source and last observed state. Keep the export focused on inspecting context and composing the prompt; task execution belongs to the continuation workflow.

## Select the Context Needed to Resume

Retain information that changes what the next agent should do or how it should interpret the evidence:

- **Outcome and scope:** the user's goal, acceptance criteria, relevant constraints, explicitly chosen approaches, and the scope and conditions of approvals or pending decisions.
- **Work location:** the relevant host, workspace root, and a small set of paths, URLs, or identifiers for instructions, implementation, and evidence. Identify the branch or checkout when it is needed to locate the right work.
- **Execution environment:** hardware and software details that affect this task, such as the interpreter, runtime, toolchain, accelerator, or allocation. Describe required authentication through its configured mechanism or credential name while keeping secret values private.
- **Progress and evidence:** completed, in-progress, blocked, and unverified work; whether an implementation exists or is still being discussed; and relevant checks or failed attempts with their conditions and observed results.
- **Continuity:** user corrections that would otherwise be lost, the ownership or purpose of unfinished changes, actions already taken or pending, and ongoing jobs or external operations. Include usable job, process, run, or artifact identifiers together with their host and last known state.

For readable code, diffs, logs, documents, and existing plans, provide the entry point and the brief status needed to use it. Let the receiving agent inspect their contents. When essential information exists only in the conversation or an inaccessible source, preserve the minimum content needed to proceed. For a discussion or learning task, this may be the user's reported understanding, agreed definitions, and the question still being explored.

Make each path's host and workspace clear. Prefer stable artifact references that remain meaningful in a fresh conversation. Mark session-local handles according to their limited scope and provide a durable way to locate the work when available. Keep source-environment facts distinct from the destination's actual capabilities. Label old harness access limits as environment facts and user-imposed constraints as task requirements; the receiving agent determines access in its own environment.

## Preserve Evidence and Independent Judgment

Distinguish direct observations, supported findings, user decisions, and unresolved questions. Retain the conditions and evidence that make a finding usable. Express an uncertain cause as a question to investigate. Describe failed attempts through the action taken and the observed result, keeping causal claims proportional to their evidence.

Select prior assistant conclusions for their evidential support and relevance to the remaining task. Carry a tentative idea forward when the user specifically wants it investigated, identifying its status and any material counterevidence. Keep the user's settled choices explicit and leave open decisions available for reassessment.

Use assistant-written notes as guides to the underlying artifacts. Ask the receiving agent to reconstruct its understanding from the goal, constraints, and available evidence, applying first-principles reasoning to unresolved decisions. Ground the starting action in current state or a user-selected direction.

## Compose the Receiving Agent's Prompt

Return one fenced `markdown` block as the complete deliverable. Choose a fence longer than any fence inside the prompt. Match the user's language unless they request another language, and preserve technical names and identifiers exactly.

Address the receiving agent directly, opening with the concrete task it is taking over. Use short paragraphs or useful sections to make the goal, context, state, and continuation easy to find. Fill task-specific references with actual known values. Express an essential missing fact as a concrete uncertainty the recipient can resolve through available context or a targeted question.

Place each fact and constraint once, alongside the work it affects. Scale the detail to the decisions needed for resumption. Keep code and document details in their referenced sources, and give the recipient the conversation-specific information needed to interpret them.

For an active task, end with a direct instruction to verify relevant current state and proceed within the stated scope toward the requested outcome. For work awaiting input or approval, identify the required decision and any preparation that can proceed. For a paused task, retain the user's condition for resuming. For a completed task, state completion and any explicit follow-up.

Read the block once from the receiving agent's perspective. It should be able to locate the work, distinguish observation from uncertainty, and identify the next justified action. Consolidate repeated information and ensure that every instruction is supported by the user's request, the task's state, or its evidence.
