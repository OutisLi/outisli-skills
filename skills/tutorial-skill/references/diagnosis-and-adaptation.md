# Diagnosis and Adaptation

Use this protocol to choose the smallest intervention that restores progress. Diagnose a local, evidence-based blocker rather than assigning the user a fixed level.

## Gap Taxonomy

| Gap              | Signal                                                                   | Efficient response                                                    |
| ---------------- | ------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Goal             | The requested outcome or success criterion is ambiguous                  | Clarify the deliverable or decision with one question                 |
| Vocabulary       | A technical term has no usable meaning                                   | Define it plainly, then reconnect it to the step                      |
| Object type      | The user cannot tell what kind of thing a symbol or component is         | Name its type, role, inputs, and outputs                              |
| Notation         | Symbols, diagrams, units, or syntax block meaning                        | Translate each part before manipulating it                            |
| Conceptual model | Words are known but mechanism or relationship is missing                 | Build one concrete model and one contrast                             |
| Procedure        | The idea is understood but step order is unclear                         | Give a compact decision procedure and execute one step                |
| Recognition      | The method works after prompting but is not selected independently       | Teach cues and contrast with a near non-example                       |
| Reasoning        | Steps can be copied but not justified                                    | Expose the assumption, invariant, mechanism, or proof hinge           |
| Misconception    | A stable wrong model predicts the wrong behavior                         | Preserve the plausible part, show a counterexample, replace the model |
| Transfer         | The user succeeds only on an identical case                              | Extract the invariant pattern and vary one surface feature            |
| Execution        | The model is understood but tooling, state, or environment blocks action | Inspect the real interface, configuration, state, and error           |
| Evidence         | Output exists but does not establish the intended claim                  | Define a discriminating measurement or validation                     |
| Confidence       | Reasoning is sound but the user cannot trust or check it                 | Confirm the valid part and provide a self-check                       |
| Overload         | Too many new objects or branches are active                              | Reduce to one object, one relation, and one action                    |

The same visible mistake can come from different gaps. Diagnose from the user's explanation, action, and evidence, not from correctness alone.

## Ask or Explain

Explain directly when the user lacks a definition, object model, notation, tool context, or prerequisite. A guiding question would only make them guess.

Ask one guiding question when the user has shown the needed foundation and their next answer would reveal method recognition, reasoning, or transfer.

If urgency is explicit, answer or act first, then add the minimum reason and verification. Do not hide an urgent answer behind a Socratic sequence.

## Cognitive Load Budget

When the user is new or confused, keep each teaching unit small:

- introduce one or two connected concepts;
- use one concrete case or representation;
- connect it to one immediate action;
- ask one focused check when its answer changes the next step;
- pause when the user's answer or observation is needed to choose what follows.

A complete response can contain several small units in dependency order. Honor an explicit one-shot request while keeping the units readable; do not replace required coverage with a sequence of continuation prompts.

When the user demonstrates a prerequisite, replace its explanation with a one-line bridge. Increase depth through assumptions, derivation, edge cases, or transfer only when the task or user asks for it.

## Error-to-Intervention Map

- **Wrong symbol or object role:** translate roles and types.
- **Wrong mental model:** give a concrete contrast or counterexample.
- **Wrong method:** compare the cues and validity conditions of candidates.
- **Wrong setup:** translate the real task into quantities, state, or data structures.
- **Wrong proof or causal claim:** identify the missing hinge, invariant, mechanism, or assumption.
- **Local calculation or syntax slip:** repair locally and add a check habit; do not reteach the field.
- **Wrong transfer:** state the invariant pattern and give a nearby variation.
- **Execution failure:** reproduce or inspect the full error before changing the system.
- **Invalid evidence:** explain what the measurement can and cannot support, then choose a better test.

Explain why the wrong path was tempting. Preserve every part of the user's reasoning that remains valid.

## When the User Is Still Confused

Do not repeat the same explanation. Ask or infer the earliest sentence, symbol, object, or transition that stopped making sense. Then change one dimension:

- abstraction -> concrete case;
- symbols -> object roles and words;
- verbal description -> diagram, trace, or table;
- large case -> smallest nontrivial case;
- procedure -> mechanism;
- mechanism -> observable consequence;
- generic example -> the user's actual artifact;
- one long chain -> one causal link.

After repair, return immediately to the blocked step.

## Understanding and Readiness Checks

Use a check only when its answer changes what comes next. Choose one:

- explain the central relation in the user's own words;
- identify the object type or role;
- predict the next step or qualitative outcome;
- choose the method from its cues;
- spot a tempting error;
- apply the idea to one near variation;
- interpret actual task output.

Task evidence may be the best check: a user who can choose parameters, predict the output, run the step, and interpret the result has shown more than someone who can repeat a definition.

Advance when the current step is usable and no unresolved prerequisite can invalidate the next decision. Advance cautiously when execution works but reasoning or transfer remains uncertain. Review locally when one gap is known; step down only when a prerequisite is actually blocking progress.

Never claim broad mastery from exposure, self-report, or one correct answer.
