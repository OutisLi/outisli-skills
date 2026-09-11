---
name: article-reading
description: >-
  Help a reader understand, evaluate, and use research papers, especially in
  science, engineering, mathematics, and computing. Use for a paper walkthrough,
  an unfamiliar method or result, a relevance assessment, or a comparison of
  papers. Adapt to the reader's knowledge and purpose, explain the core argument
  from first principles, and connect claims to evidence. Accept files, links,
  identifiers, or excerpts; a PDF upload is not required.
---

# Article Reading

Help the reader understand what problem a paper addresses, how its central idea works, what its evidence establishes, and what they can use. Optimize for useful understanding at the requested depth across research disciplines. Use this skill on its own or draw on `toturial-skill` for prerequisite teaching within the reading task.

## Establish the Reading Goal

Use the conversation to establish the reader's starting knowledge and purpose: assessing relevance, understanding a mechanism, following a derivation, reproducing a result, or adapting an idea. Calibrate the prerequisites of this paper, rather than rating the reader's expertise in an entire field.

Before a substantial explanation, briefly ask about whichever of the starting point and target depth is genuinely missing. Use natural questions and accept plain descriptions. A degree, job title, or familiarity with one field does not establish knowledge of a neighboring field. While awaiting calibration, inspect the source and give a short, accessible orientation. If the user delegates the choice of depth, start with the central mechanism and the evidence needed to judge it, then adapt from their response.

Honor a focused question directly. For an open-ended reading request, identify the main contribution and begin explaining the concept that unlocks it. For a requested complete review or walkthrough, cover the full requested scope with detail proportional to its importance.

## Establish What Can Be Read

Accept a local file, accessible paper page, DOI, preprint identifier, title, or excerpt. Resolve the actual paper and version using the available tools. Identify the paper briefly; include bibliographic details when they help distinguish it. When several works match and the choice matters, clarify the identity.

Read the source before attributing details to it. Inspect enough of the methods, results, and relevant supporting material to follow the central argument; selective explanation still requires checking its basis. Open a figure or table visually when its axes, structure, or formatting carry information that text extraction misses. Check ambiguous equations against the rendered source.

If only an abstract, excerpt, or inaccessible link is available, state that coverage limit and explain what the accessible material supports. Seek the missing source when it affects the answer. Distinguish information absent from the paper from information not found in the material inspected.

## Explain the Argument at the Reader's Level

Organize the explanation around the dependencies of the idea. Follow paper order when useful or requested. The following questions guide the reading; use the ones that matter, without turning them into a fixed output template.

- What is the precise question? Identify the relevant objects, inputs, outputs, objective or proposition, and constraints. For an empirical study, name what is measured and what relationship is being investigated.
- What would the simplest relevant baseline do? Explain the concrete limitation the paper addresses and the conditions under which that limitation appears.
- What changes in this work? Separate the central insight from standard machinery and supporting implementation choices. Explain how the proposed change is supposed to address the limitation.
- What makes the method valid? Separate definitions, assumptions, established laws, approximations, and deductions. Identify the assumption or logical step on which the result depends, including where it may fail.
- What evidence tests the claim? Connect a decisive result, comparison, experiment, or proof to the specific question it answers.

Reconstruct a useful design rationale from the problem and constraints: why a reasonable researcher might consider this change, and what alternatives remain. Present this as an explanatory reconstruction unless the authors document their motivation. A plausible rationale does not establish their historical thought process, and a design choice need not be uniquely forced by first principles.

When an unfamiliar concept, formula, or method blocks progress, use `toturial-skill` if it is available: read its instructions and apply the prerequisite-peeling and adaptive teaching guidance relevant to that gap. Carry forward the reader's established knowledge, target depth, the paper's notation, and the exact passage or result being explained. Keep the paper-reading goal and evidence distinctions in force throughout the explanation.

For a simple definition, or when the companion skill is unavailable, use the teaching guidance here directly. Step back to the nearest prerequisite the reader understands, then name the concrete objects and explain their relationship before introducing formal notation. A small worked example, a limiting case, or a diagram can make the mechanism visible; identify an invented example as an illustration and preserve the method's essential assumptions.

For equations, define new symbols and their roles, with units, shapes, domains, or boundary conditions when relevant. Explain why an important transformation is valid and what the result means. Expand algebra only when it supports the reader's goal. For algorithms, track what enters, what changes, and what leaves; short pseudocode is useful when it reveals a mechanism that prose obscures.

Keep each teaching unit small enough to close one meaningful gap. Connect the explanation back to the specific equation, method choice, or result that required it, and show what the reader can now interpret before resuming the paper's argument. Trust stated prerequisites provisionally. If the reader remains confused, locate the earliest unclear object or transition and change the representation. A guiding question helps when the reader has enough foundation to reason; an explanation helps when that foundation is missing.

## Separate Claims, Evidence, and Interpretation

Make the source of important statements clear in ordinary prose: what the paper reports, what comes from background knowledge or another source, and what you infer or suggest. Mark a shift to background, inference, or advice explicitly when it could otherwise be mistaken for the paper's content. A reported result is not an independently reproduced result.

Keep citations useful and light. Link the paper on identification and cite the relevant figure, equation, section, or source near a quantitative, disputed, or otherwise consequential claim. Give page numbers when they help the reader locate material or are requested; distinguish PDF and printed numbering if necessary. Avoid attaching a locator to every explanatory sentence.

Select results for their evidential value. Explain what was compared, under which conditions, what the metric measures, and what the result supports or leaves unresolved. Retain the denominator, baseline, uncertainty, and evaluation setting needed to interpret a reported improvement.

Apply criticism to the actual claim and study design. Inspect relevant threats such as mismatched baselines or budgets, leakage or dependence, insufficient controls, selection effects, numerical convergence, approximation error, and the gap between a theoretical guarantee and its tested conditions. A missing analysis matters when it prevents a specific conclusion, not merely because it would appear on a generic review checklist.

Attribute novelty claims to the authors unless the relevant prior work has been checked. Read primary prior work when a novelty judgment or apparent contradiction affects the user's decision. Separate a demonstrated weakness from an untested regime or an interesting extension; the latter two are not established defects.

## Make the Reading Useful

Connect the paper to the user's stated research or practical goal. Identify the reusable idea, the assumptions that must transfer, and the parts specific to the paper's setting. When useful, propose a small discriminating experiment with a baseline and an observable outcome that would support or challenge the idea. Label that proposal as a suggestion rather than a validated application.

For reproduction or implementation goals, recover the needed data, preprocessing, objective, algorithm, parameters, boundary conditions, evaluation procedure, and compute requirements as applicable. Inspect supplements or linked code to close important gaps and identify their version when it matters. Keep reported settings separate from your proposed defaults. Reading alone does not authorize launching experiments or modifying a project.

For research opportunities, explain the mechanism behind a plausible limitation, the conditions likely to expose it, and the evidence needed to investigate it. Treat publication potential as a hypothesis requiring a substantive contribution and prior-work comparison, rather than a property of any missing experiment.

Recommend further reading only when it resolves a concrete dependency or changes a research decision. Point to the specific part worth reading and explain why.

## Read Several Papers Together

Establish each paper's contribution and supporting evidence, then compare along dimensions relevant to the user's question. Align problem definitions, assumptions, data, metrics, and computational budgets before comparing outcomes. Preserve a distinct identity for each paper when attributing claims.

Explain which ideas complement one another and whether apparent disagreements reflect different settings, definitions, or actual conflicting evidence. A compact comparison table is useful when it reveals those distinctions. Suggest a reading order from conceptual dependencies and relevance; build a survey outline when the user wants a survey.

## Conversation and Completion

Match the user's language and use plain, declarative explanations. In Chinese, pair an unfamiliar technical term with its standard English name on first use when that helps the reader recognize it in the paper. Keep the explanation in chat; create notes, slides, or other reading artifacts when requested.

Lead with a short orientation, then explain enough of the mechanism and evidence to make it useful. Adjust depth as the reader asks for a faster overview, a concrete example, a derivation, or a closer critique. In an interactive walkthrough, pause at a natural conceptual boundary where the reader's response will shape the next explanation. Complete an explicitly requested one-shot deliverable without introducing artificial continuation gates.

Translate passages when translation is requested or wording itself needs attention. Select figures and equations for what they explain; enumerate every item only when comprehensive coverage serves the request. If a requested item is absent, say so briefly and continue with the available evidence.

Close when the requested reading goal is met. State the usable understanding, the decisive evidence and its limits, and the next useful decision if one remains. Ask a follow-up only when its answer would materially improve what happens next.
