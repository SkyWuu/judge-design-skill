# Rubric design and aggregation

## Criterion contract

A criterion should let qualified evaluators identify the same evidence and apply the same boundary. Use only the fields the task needs; this is a design vocabulary, not a mandatory data schema.

| Field | Question it resolves |
|---|---|
| ID and construct | What capability or outcome is being measured? |
| Requirement provenance | Which task instruction, policy, source, or stakeholder preference justifies it? |
| Applicability | Under what conditions should this criterion be assessed? |
| Evidence | Which observable text, artifacts, or state establish satisfaction? |
| Decision boundary | What passes, fails, or earns each level? |
| Equivalence and exclusions | Which valid alternatives count, and what should not affect this judgment? |
| Anchors | What are representative positive, negative, and boundary cases? |
| Role in aggregation | Diagnostic, weighted quality, penalty, or required gate? |

If provenance is only a design assumption, label it. Do not upgrade preferences such as politeness, length, or detailed explanations into universal requirements.

## Decompose without inflating the score

Split a criterion when its parts can fail independently and the distinction matters to the decision. Keep a composite requirement if the joint outcome is the actual construct and its boundary is explicit. Do not turn alternative valid methods into separate mandatory points.

Check four different defects:

- **Missing coverage:** important failures leave every criterion satisfied.
- **Wrong direction:** a criterion rewards behavior that harms the intended task.
- **Redundancy:** one improvement earns the same credit repeatedly.
- **Infeasibility:** the candidate cannot know or do what the criterion requires from its available inputs and tools.

Generic axes can organize reporting, while instance-specific checks supply the actual facts. A reference answer is one witness of success, not necessarily a complete definition of success. Verify reference accuracy and allow valid alternatives.

A useful diagnostic is to alter one property and score all criteria. Unexpected co-movement may reveal judge interference or repeated credit, but some dependence is intentional. Explain the construct before dropping correlated criteria. Model-generated criteria are proposals; audit them for unsupported requirements and candidate-specific overfitting.

## Scale and aggregation

Use binary labels for clear requirements. Use ordinal levels where partial quality has a meaningful interpretation, with observable distinctions between adjacent levels. Use pairwise preference for relative choices where absolute anchors are difficult. Do not force every task onto the same scale or assume ordinal distances have equal utility.

Define weights and thresholds from the decision context, not from the distribution that makes a preferred model win. If fitting them from labels, do so on development data and evaluate the frozen choice separately. Retain criterion-level outcomes even when a gate causes overall failure.

For nonnegative quality weights, one possible score is:

`sum(weight_i * normalized_score_i) / sum(weight_i)`

Specify the eligible criteria, normalization, and weights first. Renormalizing over applicable criteria changes the interpretation across items; report coverage and applicability composition. No eligible criteria yields an undefined score, not automatic success. An unknown verdict on an applicable criterion is not N/A and should not silently disappear from the denominator. Define review, incomplete-result, or bounded-score behavior.

For penalties, define the sign convention once: satisfying an undesirable-behavior predicate incurs a negative contribution. Specify normalization and clipping; clipping per item differs from clipping the final average. Avoid counting the same defect as both missed positive credit and a penalty unless that extra weight is intentional.

State whether aggregation is over criteria, items, users, or task groups. Pooling every criterion implicitly gives items with more criteria more influence. Choose equal-item, traffic-weighted, or another aggregation to match the intended population and report that choice. Keep adequacy gates distinct from relative preferences when relevant.

## Worked example: document-grounded answer

This is a fictional example. Source S1: “The museum is open Tuesday through Sunday, 10:00 to 18:00. It is closed on Monday.” Task: “Is it open Monday? If not, when can I go?”

| ID | Pass condition | Evidence and boundary |
|---|---|---|
| C1 | States that the museum is closed Monday | Equivalent wording is accepted; a contradictory opening claim fails |
| C2 | Gives at least one valid alternative visit window | “Tuesday at 11:00” or the full published schedule both count; listing every day is unnecessary |
| C3 | Every asserted opening time is supported by S1 | Unsupported extensions fail; absence of time assertions passes only this criterion |

“Closed Monday; try Tuesday at 11:00” passes all three. “Closed Monday; try Tuesday at 20:00” passes C1 but fails C2 and C3. “Have a lovely visit” fails C1 and C2, despite vacuously passing C3. Extra pleasant wording should not change these factual results.

C2 and C3 overlap on invalid alternatives. If both contribute numerically, disclose that overlap or change aggregation; alternatively, use C1/C2 for completion and C3 as a separately reported factuality gate. The example demonstrates a tradeoff to resolve, not universal weights or gates.
