# Eval

How to tell whether the economist-lens skill works.

## The loop

1. Pick a case from `cases/`.
2. Run the skill on the case input in a **fresh session**. No hints, no peeking at expected outputs.
3. Score the brief with `rubric.md` against the case's ground truth / expected flags.
4. Log the run in `results.md`: date, model, case, scores, and qualitative notes (especially failures).
5. Fix the skill, re-run the failed cases. Evals are regression tests — they should grow every time the skill embarrasses itself.

## Case types

- **Golden** (`golden-*`): your own papers. You are the ground truth — the stubs have TODOs for your expert notes (design, estimand, magnitudes, and crucially what the referees pushed on). These test lens fidelity against reality.
- **Canonical** (`canonical-*`): famous, textbook-stable papers anyone can score — one per design card (Card & Krueger for DiD, Angrist & Krueger for IV/LATE, LaLonde for selection-on-observables, Abadie et al. for synthetic control, Bloom et al. for RCT, Lee for RDD) plus IO cases outside your research area (BLP for structural demand/WTP, Allcott for nudge-vs-price). Ground truth is literature consensus; drafts are written, you review and veto/swap.
- **Adversarial** (`adversarial-*`): synthetic fixtures with known traps. Fully written, no prep needed. These test whether the skill catches the failure modes it was built to catch.

## Blind A/B (the demo that doubles as eval)

1. Same business question, two runs: skill-equipped agent vs. vanilla agent.
2. Strip the labels, shuffle the order.
3. Judge (you first, economist friends later) picks the better brief and writes *why*.
4. Log the winner and the reasons in `results.md` — the reasons are product feedback.

## Rules

- Score against what's written in the case file, not your memory of what you meant.
- A hallucinated paper detail fails Honesty even if the rest of the brief is excellent.
- When a case fails, fix the skill first and re-run — don't tune the case to fit the skill.
