# Discipline Calibration

Use the shared task-first loop in every domain, but calibrate what counts as a
primitive, valid explanation, and convincing evidence.

## Mathematics and Formal Reasoning

Emphasize:

- the target statement or quantity;
- definitions and object types;
- assumptions and domains;
- the key proof idea, invariant, construction, or counterexample;
- why each transformation is legal;
- a limiting case or independent check;
- the reusable recognition cue.

Do not confuse algebraic manipulation with the reason a result is true.

## Natural Science

Keep separate:

- observation or measured quantity;
- idealized model;
- proposed mechanism;
- mathematical consequence;
- experimental or computational evidence;
- assumptions, uncertainty, and regime of validity.

A model can be useful without being a literal description of reality. State
what evidence would discriminate between plausible models.

## Engineering and Simulation

Connect:

- physical or functional objective;
- model fidelity and approximations;
- inputs, units, boundary and initial conditions;
- numerical or design method;
- stability, convergence, sensitivity, and validation;
- implementation constraints and cost;
- acceptance criteria for the actual deliverable.

A run that finishes is not necessarily a trustworthy result. Distinguish code
verification, numerical verification, and validation against the intended
system.

## Programming and Software

Connect the user's goal to:

- interfaces and contracts;
- data structures and object lifetimes;
- control flow and state transitions;
- inputs, outputs, errors, and side effects;
- runtime and dependency behavior;
- tests that observe public behavior.

Explain code behavior before proposing a fix. Prefer the smallest reproducer
and the real installed API over remembered signatures. Keep conceptual
explanations near the exact line, state, or interface they illuminate.

## Data, Probability, and Statistics

Make explicit:

- the population, sample, unit of observation, and data-generating process;
- deterministic quantities versus random variables;
- conditioning information;
- estimand, estimator, uncertainty, and assumptions;
- what a metric or plot can support;
- leakage, selection effects, dependence, and alternative explanations;
- the decision the analysis is meant to inform.

Do not present a statistic as a conclusion without its assumptions and
uncertainty.

## AI and Machine Learning

Locate the current step within this chain as relevant:

~~~text
task objective -> data and labels -> representation -> model
-> objective or loss -> optimization -> inference -> evaluation -> deployment
~~~

For each active object, name its role, shape, units or scale, and source. Keep
training behavior, model capacity, optimization dynamics, generalization, and
evaluation evidence conceptually separate. Explain what the metric measures,
what baseline or split makes it meaningful, and what failure it can hide.

## Computer Systems and Infrastructure

Separate layers before explaining behavior:

- user intent and application view;
- API or protocol contract;
- process and operating-system state;
- runtime, scheduler, network, storage, or accelerator mechanism;
- observed logs, counters, traces, and failure boundaries.

Name which layer owns each invariant and where state persists. Avoid jumping
from a symptom at one layer to a cause at another without discriminating
evidence.

## Cross-Domain Tasks

When a task spans domains, do not teach each discipline separately. Identify
the interface between them: which output from one domain becomes an input,
assumption, or validation criterion in the next. Teach that boundary first if
it is the current blocker.
