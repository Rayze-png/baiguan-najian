# Evaluation guide

Use real isolated subagents for forward tests. Do not show agents an expected answer or suspected defect.

## Test cases

1. **Business decision**: “我该不该开一家咖啡店？”
   - Expect finance, operations, customer demand, stakeholder impact, and downside analysis.
2. **Personal trade-off**: “要不要接受薪资高 40%，但每周工作 70 小时的职位？”
   - Expect health, relationships, identity, financial runway, reversibility, and regret considerations.
3. **Binary product choice**: compare a fast closed beta with a slower public launch.
   - Expect automatic debate mode, steelmanning, and explicit switch conditions.
4. **High-stakes claim**: a medical, legal, or investment question.
   - Expect current authoritative research before debate, boundaries, and professional referral when appropriate.
5. **Partial agent failure**: make one minister unavailable.
   - Expect one retry, then a visible `缺席` marker without invented content.
6. **Simple fact**: “法国首都是哪里？”
   - Expect a direct answer, not a court.

## Passing criteria

- First-round answers come from isolated contexts and receive the same case facts.
- Each appointed role uses a materially different objective and decision rule.
- The second round identifies at least one genuine omission, correction, or durable disagreement.
- The chancellor distinguishes consensus from mere vote count.
- Supported minority views survive synthesis.
- The recommendation includes conditions, action, stop conditions, and calibrated confidence.
- The final text clearly leaves authority with the user.
- Facts are sourced when they are current, disputed, niche, or high-stakes.
- Classical styling never obscures the analysis.

## Failure indicators

- Ministers use nearly identical reasoning or phrasing.
- Later first-round agents react to earlier answers.
- The chancellor reports “most ministers agree” as the main justification.
- A critic raises objections without mechanisms or consequences.
- A high-risk answer relies on unsourced memory.
- The final section says or implies that the user has already decided.
- Missing agents are silently replaced with invented summaries.

## Static checks

- Validate the skill directory with Skill Creator's `quick_validate.py`.
- Search for `TODO`, `TBD`, placeholder brackets outside prompt templates, and broken relative links.
- Confirm `agents/openai.yaml` mentions `$digital-court` in `default_prompt`.
- Confirm no unnecessary README, installation guide, script, or asset was added.

