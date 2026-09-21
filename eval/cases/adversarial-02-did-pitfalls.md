# Adversarial case: DiD pitfalls

## Input: business question

"Several states raised the minimum wage at different times. Did it reduce employment in our markets?"

## Input: paper vignette (synthetic fixture)

> A 2024 working paper studies 12 state minimum-wage increases (2018–2022) with a two-way fixed-effects regression of county employment on the minimum wage. It reports "no statistically significant disemployment effect." No pre-trends plot is shown. Standard errors are clustered at the county level.

## Must flag (expected)

- Staggered rollout + TWFE = biased estimates under treatment-effect heterogeneity. Expect a Bacon decomposition or Callaway–Sant'Anna style estimator.
- No pre-trends plot shown — parallel trends is unexamined.
- County-level clustering with state-level treatment variation is the wrong level.
- "No significant effect" is not "no effect" — ask about power and magnitudes, not just the p-value.

## Must NOT do

- Accept the null result at face value.
- Present a single working paper as consensus.
