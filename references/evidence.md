# Evidence behind the design choices

Primary sources checked on 2026-10-08. These pointers support methodological choices; results depend on tasks, models, and protocols. Follow links to verify exact numbers or current versions before citing them. The skill does not require a particular provider, model, API, benchmark, or another skill.

| Design question | Primary source and useful location | Boundary |
|---|---|---|
| Verifiers, outcomes, human calibration, unknowns | [Anthropic: Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents), Types of graders; Step 5 | Engineering guidance, not a universal controlled comparison |
| Choosing scoring forms and score anchors | [OpenAI: Evaluation best practices](https://platform.openai.com/docs/guides/evaluation-best-practices), Human evals; LLM-as-a-judge | Recommendations need local validation; provider model recommendations are time-sensitive |
| Eligibility before factuality; diverse judges | [Google DeepMind: FACTS Grounding](https://deepmind.google/blog/facts-grounding-a-new-benchmark-for-evaluating-the-factuality-of-large-language-models/), Collective judgement | Source-grounded long-form tasks; averages judge scores rather than establishing universal majority voting |
| Specific criteria, penalties, expert meta-evaluation | [HealthBench](https://arxiv.org/abs/2505.08775), sections 2, 4.3, 8, 9 | Main human calibration covers consensus criteria, not every unique criterion; medical content and weights are not generic rules |
| Reference materials reduce grading burden | [Prometheus](https://arxiv.org/abs/2310.08491), section 6.1 and Table 6 | Training ablations for a specialized evaluator, not proof that any generated reference is true |
| Generated rubrics can hurt; refine and filter | [Rethinking Rubric Generation / RRD](https://arxiv.org/abs/2602.05125), introduction and section 2 | Improvements on studied evaluation/training settings do not justify unlimited decomposition |
| Redundancy and criterion coupling | [RADAR](https://arxiv.org/abs/2608.01810), introduction and diagnostic framework | Coupling is an audit signal; may reflect intended dependencies rather than defects |
| Order bias and reference-guided judging | [MT-Bench and Chatbot Arena](https://arxiv.org/abs/2306.05685), sections 3.2 to 3.5 | Human preference agreement does not certify logical correctness; original self-enhancement evidence was limited |
| Verbosity confounding | [Length-Controlled AlpacaEval](https://arxiv.org/abs/2404.04475), abstract and method | Rank correlation improvements are not item accuracy; length adjustment depends on the construct |
| Rubric-option and criterion order | [Am I More Pointwise or Pairwise?](https://arxiv.org/abs/2602.02219), experimental results | Permutation reduces some biases but does not uniformly improve human correlation |
| Single versus batched checks; vote saturation | [RuVerBench](https://arxiv.org/abs/2606.29920), strategy analysis, Figures 5 and 6 | Long research/coding outputs; stronger batching degradation in coding; voting cannot fix systematic errors |
| Reasoning and score distributions | [G-Eval](https://arxiv.org/abs/2303.16634), section 2; [Judgment Distribution](https://arxiv.org/abs/2503.03064), method and CoT analysis | Different tasks/interfaces yield different CoT effects; distributional scores still require calibration |
| Human preference versus objective correctness | [JudgeBench](https://arxiv.org/abs/2410.12784), sections 1, 3, 4 | Difficult factual/logical pairs challenge judges differently from ordinary preference tasks |
| Agreement, abstention, and aggregation | [Agreement Metrics for LLM-as-Judge Evaluation](https://arxiv.org/abs/2606.00093), sections 3 to 7 | Statistic choice cannot repair a misdefined population or handling protocol |

The templates, worked example, and suggested reporting choices in this skill are synthesized design guidance, not a benchmark protocol reproduced from one paper. Evaluate them against the user's actual decision and data.
