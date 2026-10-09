# Judge Design

Agent skill for designing, reviewing, and calibrating LLM-as-a-judge methods and evaluation rubrics.

Use `$judge-design` when you need scoring criteria, a judge prompt, aggregation rules, or a check of an automated grader. Ordinary review against a rubric that is already settled sits outside this skill.

It keeps three questions apart: whether the rubric measures the intended quality, whether the judge applies it correctly, and whether the scores can support the decision. Stable agreement among judges answers none of those by itself.

A new method comes back as a rubric and/or judge prompt, aggregation and exception rules, boundary examples, and a validation plan sized to the task. A review names each defect that changes an outcome, with a concrete case and a correction. Results are marked designed, checked on examples, or empirically validated, and the scope of that check is stated.

## Files

- `SKILL.md` is the entry point: scope, method choice, and what to deliver.
- `references/rubric-design.md` covers criteria, scales, and aggregation.
- `references/judge-protocol.md` covers evidence, the prompt skeleton, verdicts, and cost.
- `references/validation.md` covers calibration, metrics, and challenge cases.
- `references/evidence.md` lists the primary sources behind the design choices, and where they do not apply.
- `agents/openai.yaml` sets the display name and default prompt.
