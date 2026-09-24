# How should we measure the causal impact of a subscription price increase on churn?

*Measurement mode: this is a "how do we estimate the causal effect of X on Y" question.*

**Bottom line:** Randomize who faces the increase and compare against a holdout. Pre-register a 6–12 month window and measure retained revenue per subscriber, not just churn. If a holdout is not possible, phase the increase across regions or cohorts on a randomized schedule and analyze the rollout with group-time ATT estimators. Use structural demand models to extrapolate to other price points once an experiment pins down one point, not as the primary evidence.

## 1. The estimand

The target is the average treatment effect on the treated (ATT) of the specific planned price increase: the change in retention and net revenue per subscriber, over a 6–12 month window, among the subscribers who would face it.

Three choices shape this number:

- **Outcome.** Measure the change in retained revenue per subscriber. A price increase shifts subscribers across several margins: cancellation, downgrade, pause, and higher spend from stayers. Churn alone misses the last two.
- **Window.** Fix the window before seeing results. Price responses grow over time as subscribers notice, compare alternatives, and hit renewal dates. Karlan & Zinman (2019) estimate a dollars-borrowed elasticity of −1.1 in year one and −2.9 in year three. A 30-day read captures a fraction of the full response.
- **Population.** If the increase is grandfathered or targeted, the exposed group is selected. The ATT describes that group. A universal increase would hit a different mix. Estimate by segment: tenure, engagement, plan tier.

## 2. Success criteria

A credible answer needs five things: (1) a counterfactual — what these subscribers would have done without the increase; (2) a pre-registered window of at least 6 months; (3) all margins measured — cancel, downgrade, pause, revenue; (4) segment-level estimates; (5) a decision rule fixed before results arrive.

## 3. Candidate designs

**A. Randomized holdout.** Randomize renewing subscribers — or cohorts or regions — into the increase vs. a holdout at the old price. *Assumption:* randomization held. Check balance, attrition by arm, and SUTVA. *Main threats:* word-of-mouth and social-media backlash spill the increase into the control group — randomize at cohort or geography level to limit this. Shared household accounts mean the billed account and the deciding person differ. The announcement is part of the treatment; how subscribers learn about the increase changes the response. *Cost:* the most credible read. The slowest, since it needs the full window. The hardest to sell internally.

**B. Randomized staggered rollout.** Phase the increase across regions or cohorts on a randomized schedule. Use the not-yet-treated as controls. *Assumption:* parallel trends absent the increase. *Main threats:* anticipation — subscribers who hear the increase is coming may churn early or lock in annual plans, contaminating the pre-period. Allow an anticipation window around the announcement date. A pooled two-way fixed-effects regression misestimates effects that vary across cohorts; estimate group-time ATTs instead. *Cost:* easier to get approved than a holdout. Slower to read. Credible only if the parallel-trends story holds.

**C. Regression discontinuity at an eligibility threshold.** If the increase applies above a cutoff — tenure at or above X keeps the old price, or only the premium tier rises — compare subscribers just above and below. *Assumption:* no precise manipulation of the running variable at the cutoff. Check the density and covariate balance at the cutoff. *Main threat:* the estimand is local. Subscribers at exactly tenure X may not represent the base. *Cost:* cheap and fast where a threshold exists. It identifies a local effect; treat it as a complement to another design.

**D. Structural demand estimation.** Estimate heterogeneous elasticities from observed price variation, instrumenting price (e.g., the same plan's price in other markets, cost shifters). *Assumption:* instrument exogeneity — the instrument affects churn only through price. *Main threats:* price is endogenous, since firms raise prices where demand is strong. Instruments are often weak. The discrete-choice functional form does real work in the result. *Cost:* fast, and it extrapolates to any counterfactual price. The least credible of the four without a strong instrument. Best used to extend an experimental read to untested prices.

The tradeoff: credibility rises from D to A; speed and feasibility run the other way. No design maximizes all three.

## 4. What established research says

- Randomized price variation over 29 months shows the elasticity grows over time: −1.1 in year one, −2.9 in year three (Karlan & Zinman 2019). Fix the window before reading results.
- Gym members wait an average 2.3 months between their last visit and contract termination, paying $185 in monthly fees in between (DellaVigna & Malmendier 2006). Subscribers disengage before they cancel; track usage, not just cancellation.
- Posting tax-inclusive prices cut grocery demand 8% in a three-week field experiment (Chetty, Looney & Kroft 2009). The announcement is part of the treatment; standardize it across arms or randomize the framing.
- Price elasticities vary widely within a firm: the median retail chain sacrifices $16 million of annual profit against optimal prices (DellaVigna & Gentzkow 2019). Estimate by segment; one pooled elasticity hides the profitable move.
- For staggered rollouts, estimate group-time ATT(g,t) under conditional parallel trends (Callaway & Sant'Anna 2021). Pooled two-way fixed effects bias the estimate when effects differ across cohorts.
- Random-coefficients demand models recover heterogeneous elasticities from market-level price and quantity data (Berry, Levinsohn & Pakes 1995). Useful for simulating prices you did not test; the result rests on the instruments and the functional form.

## 5. Paper notes

> **Karlan, Dean & Zinman, Jonathan (2019), "Long-Run Price Elasticities of Demand for Credit: Evidence from a Countrywide Field Experiment in Mexico," *Review of Economic Studies* 86(4), 1704–1746.**
> - Question: how elastic is credit demand to interest rates over 29 months?
> - Identification: randomized interest rates across 80 geographically distinct regions at Mexico's largest microlender. Region-level randomization limits interference; the 29-month follow-up is rare for a price experiment.
> - Magnitude: dollars-borrowed elasticity −1.9 over 29 months; −1.1 in year one, −2.9 in year three.
> - Setting: Mexican microcredit, 2011–13. Credit, not subscriptions — the rising-elasticity pattern is what transports, not the number.
> - Mechanism: the authors leave open whether learning or adjustment costs drive the growth.
> - Critique: the no-competitor-response result rests on noisy estimates; nothing is learned about equilibrium effects.
> - Status: well-established — one of the few long-horizon price experiments.
> - What this means for the question: pre-register a 6–12 month window. A 1–3 month churn read will understate the response.

> **DellaVigna, Stefano & Malmendier, Ulrike (2006), "Paying Not to Go to the Gym," *American Economic Review* 96(3), 694–719.**
> - Question: do consumers choose subscription contracts rationally?
> - Identification: descriptive — contract choice vs. realized attendance for 7,752 members across three U.S. health clubs over three years.
> - Magnitude: 2.3 months on average between the last attendance and contract termination; $185 in monthly fees paid after the last visit.
> - Setting: U.S. health clubs, late 1990s–early 2000s. Auto-renewing subscription — structurally close to the question.
> - Mechanism: overconfidence about future attendance and underestimation of cancellation hassle.
> - Critique: no price variation, so nothing here identifies an elasticity. Its value is measurement.
> - Status: established behavioral classic.
> - What this means for the question: track engagement alongside churn. "Still subscribed" includes months of paying without using.

> **Chetty, Raj, Looney, Adam & Kroft, Kory (2009), "Salience and Taxation: Theory and Evidence," *American Economic Review* 99(4), 1145–1177.**
> - Question: do consumers underreact to prices they do not see?
> - Identification: three-week field experiment posting tax-inclusive prices on 750 grocery products, plus state excise-tax variation on alcohol. The grocery experiment is clean and randomized.
> - Magnitude: 8% demand reduction for treated products during the three weeks.
> - Setting: U.S. grocery, 2006; state alcohol taxes. The mechanism — attention mediates price response — applies to any billed price.
> - Mechanism: inattention to non-salient price components.
> - Critique: short-run; the salience gap may narrow as consumers learn.
> - Status: well-established.
> - What this means for the question: standardize the price-increase announcement across test arms, or randomize the framing as a second factor. Otherwise the measured elasticity is specific to one communication regime.

> **DellaVigna, Stefano & Gentzkow, Matthew (2019), "Uniform Pricing in U.S. Retail Chains," *Quarterly Journal of Economics* 134(4), 2011–2084.**
> - Question: why do chains charge nearly uniform prices across stores?
> - Identification: descriptive on pricing uniformity across U.S. food, drugstore, and mass-merchandise chains; structural demand estimates benchmark the profit cost. The $16m figure is a model-based counterfactual.
> - Magnitude: the median chain sacrifices $16 million of annual profit vs. segment-optimal prices; within-chain elasticity variation is wide.
> - Setting: U.S. retail, 2010s. Retail goods, not subscriptions — the heterogeneity is the transportable fact.
> - Mechanism: managerial inertia and brand-image concerns keep prices uniform.
> - Critique: the dollar figure leans on the structural benchmark; do not calibrate a churn number from it.
> - Status: well-established.
> - What this means for the question: estimate churn elasticity by tenure, engagement, and plan tier. The decision — who gets the increase, how large — runs on segments, not one pooled number.

> **Callaway, Brantly & Sant'Anna, Pedro H.C. (2021), "Difference-in-Differences with multiple time periods," *Journal of Econometrics* 225(2), 200–230.**
> - Question: how to estimate DiD with staggered treatment timing.
> - Identification: econometric theory — identifies group-time ATT(g,t) under conditional parallel trends. Proof-based; in application, credibility rests on the assumption and on a clean never-treated control group.
> - Magnitude: methodological. Their illustration shows robust and naive two-way fixed-effects estimators can differ materially.
> - Setting: methods paper; applies wherever treatment rolls out in cohorts.
> - Mechanism: n/a (methods).
> - Critique: fixes the estimator, not the identification. Still needs pre-trends checks and standard errors clustered at the assignment level.
> - Status: established — the current standard for staggered DiD.
> - What this means for the question: if the increase is phased, report cohort-by-cohort ATTs against a never-treated control and show pre-trends. Skip the single pooled regression.

> **Berry, Steven, Levinsohn, James & Pakes, Ariel (1995), "Automobile Prices in Market Equilibrium," *Econometrica* 63(4), 841–890.**
> - Question: how to estimate demand and markups in differentiated-product markets from market-level data.
> - Identification: structural — random-coefficients logit with instruments for price endogeneity (cost shifters, same-product prices in other markets). Credibility rests on the instruments and the functional form.
> - Magnitude: a methods paper, not an estimate. It contributes the toolkit, not a portable number.
> - Setting: U.S. autos, 1971–1990. The technique transports to subscriptions; the numbers do not.
> - Mechanism: heterogeneous tastes produce realistic substitution patterns — the right frame for cancel vs. downgrade vs. stay.
> - Critique: weak instruments or a wrong heterogeneity specification bias every elasticity. A skeptic wants an experimental cross-check.
> - Status: well-established — the standard reference for demand estimation.
> - What this means for the question: once an experiment pins down the response at one price, use a demand model to simulate other price points. Do not set the increase from the model alone.

## 6. Recommended approach

**Primary: randomized holdout at renewal.** Randomize renewing subscribers into the increase vs. a holdout at the old price. Randomize at cohort or geography level to limit spillover. Stratify by tenure, engagement, and plan tier to get segment elasticities. Pre-register the window (6 months minimum, 12 preferred), the outcomes (retention, downgrade rate, net revenue per subscriber), and the decision rule before results arrive — for example: roll out if 12-month projected net revenue per subscriber beats control, with no segment's churn increase above a set threshold. Randomize the announcement framing as a second factor.

**Fallback: randomized phased rollout.** Randomize the rollout order across regions or cohorts. Keep a never-treated control group. Estimate group-time ATTs, show pre-trends, and allow an anticipation window around the announcement date.

**Complement: a light demand model.** Fit a simple segment-level demand curve to the experimental read to simulate other increase sizes. Do not re-run the experiment for each candidate price.

**What would change the recommendation:** if randomization is off the table entirely, lead with structural demand plus any available threshold discontinuity and mark the answer provisional. If backlash spills across test cells, randomize at a coarser level. If an answer is needed before 6 months, use engagement drops as an early signal — but pre-commit to the full window. Do not stop the test early on a short-window read.

## 7. Open threads

- The margin may be downgrade, not cancel. Model churn, downgrade, and revenue per subscriber together.
- Gross churn overstates net loss if marginal subscribers return on promotion. Track net retention.
- A unilateral increase and a market-wide increase are different counterfactuals. None of these designs capture competitor repricing.
- Repeated increases may erode trust in ways one experiment misses.
- Annual and monthly plans face the increase at different times with different salience. Analyze them separately.
