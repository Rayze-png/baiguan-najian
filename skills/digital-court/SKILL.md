---
name: digital-court
description: Convene a real multi-agent “electronic imperial court” for decisions, dilemmas, policy choices, strategy, product trade-offs, personal choices, risk reviews, and other questions that benefit from independent perspectives, adversarial challenge, and synthesis. Use when the user asks to 开朝、召集电子朝廷、让群臣纳谏、廷议、从多个独立智能体或多方利益角度审议，or when a complex consequential decision clearly warrants structured multi-perspective deliberation.
---

# Electronic Imperial Court

Convene independent subagents as ministers, let them submit sealed memorials and challenge one another, then present a modern, actionable decision brief in a light imperial-court frame. Treat the user as the sovereign and preserve their final authority.

## Non-negotiable rules

- Use real subagents with isolated first-round contexts. Never present one model's role-play as a real multi-agent court.
- Keep the first round sealed: do not show a minister another minister's answer before all initial memorials are complete.
- Separate verified facts, inferences, assumptions, and value judgments.
- Do not treat votes or consensus as evidence.
- Preserve well-supported minority views.
- Use classical court language only for roles, headings, and brief transitions. Write the analysis in clear modern language.
- If real subagents are unavailable, state that plainly and ask before offering a single-agent substitute.

## Decide whether to convene

Convene when the user explicitly invokes the court or asks for independent multi-agent perspectives. Also convene for consequential trade-offs with multiple legitimate stakeholders or objectives when this skill has been triggered implicitly.

Do not convene for a simple factual lookup, translation, formatting task, or one-step operation. Answer directly unless the user explicitly insists on opening court.

Choose a scale:

- **小朝会**: four core ministers and one chancellor; no special envoys.
- **常朝**: four core ministers, two special envoys, and one chancellor. Use by default.
- **大朝会**: four core ministers, three or four special envoys, and one chancellor. Use for high-impact, high-risk, or cross-domain decisions.

Respect the user's requested scale. Otherwise prefer the smallest scale that gives materially different perspectives.

## Run the court

### 1. Establish the case

Create one neutral case brief containing:

- decision question;
- user's objective and success criteria;
- constraints and deadline;
- verified facts;
- unverified assumptions;
- relevant options, including doing nothing when appropriate.

Ask one concise question only if missing information could reverse the recommendation. For current, niche, or high-stakes factual claims, research reliable primary or authoritative sources before deliberation and include citations in the brief.

Do not express an initial recommendation in the case brief.

### 2. Appoint the court

Always appoint the four core ministers: 御史大夫, 谏议大夫, 民意使, and 史官. For 常朝 or 大朝会, select special envoys whose incentives and decision criteria differ materially. Read [references/roles.md](references/roles.md) before selecting them.

Tell the user which envoys were appointed and why. Do not pause for approval unless an appointment would materially change scope or require new authority.

For a clear binary choice, policy dispute, or polarized question, enable **廷辩模式**: assign support, opposition, and neutral-review duties while retaining each minister's substantive role.

### 3. Collect sealed memorials

Create a separate subagent for each minister. Prefer the runtime's team-agent tools (`spawn_agent`, followed by `wait_agent` or equivalent). Give every minister the same complete case brief plus only that minister's role packet. Use minimal or no inherited conversation context when the runtime supports it.

Start ministers in parallel up to the concurrency limit. If capacity is lower than the court size, run them in batches without exposing completed answers to later first-round ministers.

Use the sealed-memorial template in [references/prompts.md](references/prompts.md). Record each subagent ID and role. Require every memorial to include a claim, grounds, assumptions, benefits, costs, risks, recommended action, confidence, and evidence that would change the judgment.

### 4. Hold cross-examination

After all first-round memorials finish, make an anonymous, faithful digest labeled A, B, C, and so on. Remove role names but retain reasoning and uncertainty.

Send the digest back to each existing minister using `followup_task` or the runtime equivalent. Require each minister to identify the strongest opposing argument, missing evidence, false consensus, and any change to its own view. Use the cross-examination template in [references/prompts.md](references/prompts.md).

If an existing minister cannot be resumed, create a new reviewer with that role and disclose the replacement in the process note.

### 5. Ask the chancellor to synthesize

Create a new independent subagent as 丞相 only after memorials and rebuttals are complete. Give it the case brief and the complete, role-labeled deliberation record. Use the chancellor template in [references/prompts.md](references/prompts.md).

Require it to distinguish genuine consensus, main disagreements, supported minority views, and critical unknowns. It must compare the preferred option, an alternative, and doing nothing when meaningful, then supply conditions, actions, stop conditions, and calibrated confidence.

### 6. Submit the draft for censorial review

Send the chancellor's draft to the original 御史大夫. Ask for a focused review of unsupported facts, logical jumps, hidden costs, suppressed dissent, false precision, and safer reversible tests.

If the censor raises a material objection, ask the chancellor to revise once. Do not loop. Surface any unresolved objection to the user.

### 7. Present the throne brief

Lead with a concise bottom line, then use:

1. `《案情》`
2. `《百官奏议》`
3. `《廷议交锋》`
4. `《共识与分歧》`
5. `《丞相拟旨》`
6. `《御史封驳》`
7. `《请陛下圣裁》`

In `《请陛下圣裁》`, identify the decision still belonging to the user and give the smallest useful next action. Do not claim the user has decided.

## Evidence and high-risk discipline

For medical, legal, financial, safety, or other high-stakes questions:

- verify current claims with authoritative sources before convening;
- state knowledge and evidence limits;
- separate general information from individualized professional advice;
- recommend qualified professional help when appropriate;
- favor reversible validation before irreversible action.

Agents may debate interpretations and values, not manufacture facts.

## Failures and transparency

- Retry a failed or timed-out minister once. If it fails again, mark that office `缺席`; never fabricate its memorial.
- If the chancellor fails twice, present the memorials and disagreements without inventing a synthesis.
- If a key fact cannot be verified, list it under critical unknowns and explain how to obtain it.
- If concurrency is limited, batch the agents and say so only when it materially affects timing.
- If subagent tools are unavailable, stop before role-playing. Ask whether the user accepts a clearly labeled single-agent multi-perspective analysis.

## Resources

- Read [references/roles.md](references/roles.md) to appoint roles and keep incentives distinct.
- Read [references/prompts.md](references/prompts.md) for complete agent prompt templates.
- Read [references/evaluation.md](references/evaluation.md) when validating or updating this skill.

