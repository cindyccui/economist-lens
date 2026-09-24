# Canonical IO-adjacent case: non-price interventions vs. price changes

## Business question

"Can nudges move customer behavior as much as a price change — and how do we compare them?"

## Paper

Allcott, Hunt. "Social Norms and Energy Conservation." *Journal of Public Economics* 95(9–10), 2011, 1082–95.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** **Large-scale randomized field experiments** (600,000 treatment and control households across US utilities) run by Opower: Home Energy Reports comparing a household's electricity use to neighbors', plus conservation tips. Random assignment identifies the causal effect of the reports.

- **Estimand:** ATE of receiving Home Energy Reports on household electricity consumption.

- **Headline magnitude + baseline:** Average reduction of **2.0%** of baseline electricity use — which Allcott benchmarks as **equivalent to an 11–20% short-run electricity price increase**. Strongly heterogeneous: the highest pre-treatment decile cut usage **6.3%**, the lowest decile only **0.3%**. (The price-equivalence framing is exactly the "magnitude relative to baseline" translation the skill demands.)

- **Setting / population:** US residential utility customers, 2000s; opt-out (not opt-in) program.

- **Mechanism:** Descriptive social norms (+ injunctive "smiley face" norms to prevent a **boomerang effect** where low users *increase* usage — tested with an embedded RDD). Candidate channels: social learning about efficient usage levels vs. moral cost of consumption.

- **Known threats / what economists argue about:** (1) **Persistence/decay**: effects decay between letters (quarterly arm) — attention is malleable, not a one-time learning effect. (2) **Targeting/profiling**: Allcott shows a statistical targeting rule could substantially raise cost-effectiveness — the policy-relevant heterogeneity point. (3) External validity: utility-run opt-out programs with repeated mailings ≠ one-shot corporate nudges. (4) Later literature debates long-run persistence and welfare interpretation (are the savings worth the "moral tax"?).

- **Classic vs. frontier:** **Canon** for behavioral/field-experimental IO-adjacent work and the standard "nudge vs. price" benchmark. Frontier: the broader nudge-units literature and welfare analyses of behavioral interventions (e.g., Allcott & Kessler 2019 on welfare effects).

- **Traps for generic AI:** (1) "Nudges reduce energy 2%" without the heterogeneity — the targeting insight is the business-relevant half. (2) Missing the price-equivalence benchmark (the magnitude translation). (3) Missing the boomerang/injunctive-norm design detail. (4) Treating decay as a footnote rather than the central caveat for repeated-intervention ROI.

## Expected retrieval

Allcott (2011) as the classic; Schultz et al. (2007) on the boomerang effect as precursor; Allcott & Rogers (2014) on persistence and Allcott & Kessler (2019) on welfare as frontier.
