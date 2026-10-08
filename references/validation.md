# Calibration and validation

## Match evidence to the claim

Design review can find contradictions and unsupported requirements. Worked cases can demonstrate consistent boundaries. Neither establishes measured accuracy on real outputs. An empirical claim needs a defined sample, independent reference judgment, recorded protocol, and relevant metrics.

Use domain-qualified humans or trustworthy executable evidence for reference labels. A stronger model can help triage, but agreement with it alone is teacher agreement, not human or objective correctness. Retain human disagreements and document adjudication. Low agreement can reflect ambiguity, insufficient evidence, or genuinely plural preferences, not just poor annotators.

Separate rubric/prompt development from held-out validation. Split by the source of dependence, such as task, conversation, document, or user, rather than by individual criteria from the same item. Include the target language, model families, quality range, and real failure patterns. Keep an adversarial stress set distinct from prevalence-representative data; do not report an enriched failure set as production accuracy.

Choose sample size from precision needed, rare-error prevalence, and consequential slices. A pilot is useful for discovery, not proof that rare failures are absent. Thresholds should reflect error costs and the size of model differences the evaluator must resolve. If these are unspecified, state candidate acceptance criteria as proposals.

## Metrics by question

| Question | Useful evidence |
|---|---|
| Does a binary judge recognize both classes? | Confusion matrix, class counts, balanced accuracy or macro-F1, false acceptance and false rejection |
| Does a graded judge use the scale correctly? | Error distribution, bias by level, ordinal agreement such as weighted kappa with stated weights; correlation alone misses offsets |
| Does it reproduce preferences? | Pairwise agreement under explicit tie rules, order consistency, relevant disagreement slices |
| Are probabilities useful? | Reliability/calibration assessment and proper scores such as Brier or log loss, on held-out labels |
| Are results stable and decision-relevant? | Repeat variation, paired model differences, uncertainty intervals, ranking or decision flips |
| What fraction is actually judged? | N/A, abstention, technical failure, and effective coverage, with reasons |

Name the positive class and metric denominator. Raw accuracy can look high under imbalance; chance-corrected metrics also have prevalence sensitivities. Provide underlying counts. Metrics undefined for a single-class slice remain undefined, not zero. Compare human-human and human-judge agreement with compatible units and protocols.

If excluding unknowns, report accuracy conditional on coverage and investigate whether excluded cases are harder. N/A is eligibility, not uncertainty. Avoid mixing criterion-level accuracy with item-level score correlation or model-ranking correlation: they answer different questions.

For repeated criteria or outputs from the same task, use uncertainty estimates that preserve that dependence, such as resampling whole tasks for item-level comparisons. Compare models on the same sampled units. Resampling tasks captures task-sampling uncertainty; repeated judge runs capture judge stochasticity. State which uncertainty was measured.

## Focused challenge cases

Select tests relevant to the actual use:

- **Invariance:** exchange A/B order; vary criterion order; paraphrase an equivalent answer; alter irrelevant formatting, verbosity, or identity cues.
- **Sensitivity:** insert one factual error, remove a required action, reverse a relevant condition, or provide an attractive answer to the wrong task.
- **Applicability and evidence:** already-satisfied preconditions, missing external state, incomplete logs, conflicting source versions.
- **Interference:** compare single-criterion and batched decisions; inspect whether changing one dimension moves unrelated scores.
- **Gaming:** candidate text instructing the judge to award points, reference mimicry, repetition of rubric keywords without fulfilling requirements.

Check transformations manually or with independent evidence: a synthetic “wrong answer” may still be valid, and deleting context may genuinely change the task. Require a verdict flip only when the edited case truly crosses the criterion boundary.

## Maintenance and reward use

Version the scoring protocol and rerun an appropriate fixed calibration set after substantive changes. Monitor target-data drift, refusal/unknown rates, error slices, and decision changes. Track both candidate-generation variation and grading variation when both affect reported performance.

If used as a training reward, best-of-N selector, or data filter, validate under that optimization pressure. Keep evaluation data and, where feasible, an independent evaluation method outside reward tuning. Inspect high-scoring failures. More reward against the same judge is not independent evidence of task improvement.

## Report only what was established

For completed validation, provide sample provenance, annotation protocol, judge configuration, label and missingness rules, aggregation, metric counts and uncertainty, failure slices, and decisions supported. For an unexecuted plan, provide these as proposed choices and explicitly say no performance has been measured. Do not substitute a long list of recommended tests for the usable rubric or prompt the user asked for.
