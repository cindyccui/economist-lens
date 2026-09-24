# Canonical case: when selection-on-observables fails

## Business question

"Can we evaluate our job-training program using observational data and matching, instead of running an expensive RCT?"

## Paper

LaLonde, Robert J. "Evaluating the Econometric Evaluations of Training Programs with Experimental Data." *American Economic Review* 76(4), 1986, 604–20.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** A *meta*-design: LaLonde took the **experimental** NSW job-training data (where the true effect is known from the RCT) and asked whether **nonexperimental** methods — selection models, DiD, matching on observables — applied to the same data could recover the experimental benchmark. They couldn't: estimates swung wildly across methods and comparison groups, often with the wrong sign.

- **Estimand:** The paper's estimand is second-order: the *bias* of nonexperimental estimators, measured against the experimental ATT benchmark.

- **Headline magnitude + baseline:** Nonexperimental estimates ranged across a wide band (including negative estimates) while the experimental benchmark was positive (~$800–900 in 1982 dollars earnings gain). The point is variance and fragility, not a single number.

- **Setting / population:** US National Supported Work Demonstration (1970s); disadvantaged workers; comparison groups drawn from CPS/PSID.

- **Mechanism:** The failure mechanism is **selection on unobservables** — trainees differ from comparison workers in ways no covariate set captures (motivation, local labor markets, application behavior).

- **Known threats / what economists argue about:** (1) **Dehejia & Wahba (1999, 2002)** showed propensity-score matching *could* get close to the benchmark — then **Smith & Todd (2005)** showed that result was fragile to sample and specification choices. The argument itself is the lesson: matching "working" once doesn't make it reliable. (2) Modern take: with richer admin data and better designs (e.g., double-ML), the pessimism is qualified — but the burden of proof stays on the method.

- **Classic vs. frontier:** **Canon.** The canonical cautionary tale about selection-on-observables. The correct brief *recommends against* the business question's premise — a good test of whether the skill pushes back.

- **Traps for generic AI:** (1) Treating this as "matching doesn't work, period" — the real lesson is about unobservables and fragility, and the subsequent debate. (2) Missing that the experimental benchmark is what makes the paper credible. (3) Recommending matching anyway with enough covariates.

## Expected retrieval

LaLonde (1986) as the classic; Dehejia & Wahba (1999) and Smith & Todd (2005) as the debate; modern ML-causal-methods as frontier.
