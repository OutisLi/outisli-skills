# First-Principles Explanation

Use this protocol when the current task step depends on a concept, model,
formula, mechanism, proof, or abstraction the user does not yet understand.

## First-Principles Test

An explanation is first-principles enough for the current task when the user
can see:

1. what is being observed, predicted, controlled, or computed;
2. what the primitive objects are;
3. which relationships are definitions and which are empirical or modeled;
4. which constraints, assumptions, or invariants make the method valid;
5. how the conclusion follows;
6. where the conclusion stops being reliable;
7. how this changes the next action.

Do not appeal only to authority, a memorized recipe, or an analogy. Do not
derive below the level needed for the current decision.

## Prerequisite Peeling

Work backward from the current blocker:

~~~text
current decision
  <- required concept
    <- required representation or primitive
      <- first layer the user already understands
~~~

For each proposed prerequisite, ask internally:

- Is it genuinely required for the current action or verification?
- Does the user already show evidence of knowing it?
- Can it be replaced by a local operational definition for now?
- Would omitting it cause a wrong decision, not merely an incomplete survey?

Stop at the first stable layer. Rebuild upward one layer at a time. Each layer
must close one specific gap and reconnect to the task. Do not expose an
unbounded prerequisite tree.

## Micro-Explanation Loop

A useful layer usually contains five moves:

1. **Need:** the concrete problem the current concept solves.
2. **Object:** the new object, relationship, or rule in plain language.
3. **Reason:** why it works, derived from known objects and constraints.
4. **Consequence:** what becomes possible and what remains impossible.
5. **Return:** how it changes the current task step.

Use these as thinking moves, not mandatory user-facing headings. If the layer
needs only two sentences, use two sentences.

## Concrete to Formal

When the user lacks a mental model, prefer this order:

1. name the object and its purpose;
2. give one minimal concrete case or visual relation;
3. contrast it with the nearest tempting non-example;
4. give the formal definition, notation, or algorithm;
5. explain each symbol, type, unit, shape, or state transition;
6. show why the formal version matches the concrete case;
7. return to the real input and decision.

For an already advanced user, compress or reverse this order: state the formal
hinge first and expand only where evidence shows a gap.

## Formula and Derivation Rules

Before manipulating a formula:

- state the target quantity;
- define each symbol and its object type;
- state units, dimensions, shapes, domains, and measures when relevant;
- separate definitions, assumptions, conservation laws, approximations, and
  algebraic consequences;
- explain why each important transformation is valid;
- interpret the final expression in words;
- identify limiting cases or a sanity check.

Use rendered math for mathematics and fenced blocks only for literal code or
commands. A formula plus unexplained prose is not a dual explanation; the
plain-language interpretation must identify what changes with what and why.

## Analogy Discipline

An analogy is useful only when it maps specific relationships. State:

- what in the analogy corresponds to each technical object;
- which relationship it illustrates;
- where the mapping breaks.

Retire the analogy once the user can use the real model. Never let a vivid
story replace quantitative assumptions, mechanisms, or evidence.

## Explanatory Boundaries

Avoid these failure modes:

- beginning with jargon or symbols whose objects are unnamed;
- explaining the entire knowledge tree before the first useful action;
- giving a sequence of equations without the causal or logical hinge;
- treating implementation behavior as a fundamental law;
- treating a model as reality without stating assumptions;
- explaining only why a method is convenient, not why it is valid;
- continuing downward after the user has enough foundation to proceed.
