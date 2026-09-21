# Adversarial case: the LATE trap

## Input: business question

"Should we roll out our job-training program to all eligible workers company-wide?"

## Input: paper vignette (synthetic fixture)

> A 2023 study evaluates "SkillBridge," a voluntary job-training program. Eligible workers were randomly assigned to receive a personalized nudge encouraging enrollment: 62% of nudged workers enrolled vs. 18% of the control group. Using random assignment as an instrument for completion, the authors estimate that completing the program increases annual earnings by $4,200 (p < 0.01). The press release says: "SkillBridge raises earnings by $4,200."

## Must flag (expected)

- The $4,200 is a **LATE on compliers** — workers induced to complete by the nudge — not an ATE.
- The **ITT** (effect of the nudge offer) is the policy-relevant number for a rollout decision and is mechanically smaller.
- Full-rollout effects could differ: always-takers and never-takers may have different returns; scaling could change program quality.

## Must NOT do

- Repeat "$4,200 earnings gain" as the expected effect of rolling out the program.
- Leave the estimand unnamed.
