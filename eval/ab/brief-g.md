# How should we measure the causal impact of a subscription price increase on churn?

*Measurement mode: this is a "how do we estimate the causal effect of X on Y" question.*

## 1. The estimand

The target is the average treatment effect on the treated (ATT) of the specific planned price increase: the change in retention and net revenue per subscriber, over a 6–12 month window, among the subscribers who would face it.

Three choices shape this number:

- **Outcome.** Measure retained revenue per subscriber. A price increase moves several margins: cancellation, downgrade, pause, and higher spend by stayers. Churn alone misses the last two. When Netflix raised US prices in January 2022, it lost 970,000 net subscribers in Q2 while revenue rose 9% year over year — the two metrics can point in opposite directions.
- **Window.** Fix the window before seeing results. Price responses grow over time as subscribers notice, compare alternatives, and hit renewal dates. Karlan & Zinman (2019) estimate a dollars-borrowed elasticity of −1.1 in year one and −2.9 in year three. A 30-day read captures a fraction of the full response.
- **Population.** A grandfathered or targeted increase hits a selected group. The ATT describes that group, not the full base. Estimate by segment: tenure, engagement, plan tier.

## 2. Success criteria

A credible answer needs five things: (1) a counterfactual — what these subscribers would have done without the increase; (2) a pre-registered window of at least 6 months; (3) all margins measured — cancel, downgrade, pause, revenue; (4) segment-level estimates; (5) a decision rule fixed before results arrive.

## 3. Candidate designs

**A. Randomized holdout.** Randomize renewing subscribers — or cohorts or regions — into the increase vs. a holdout at the old price. *Assumption:* randomization held. Check balance, attrition by arm, and SUTVA. *Main threats:* word-of-mouth and press coverage spill the increase into the control group — randomize at cohort or geography level to limit this. Shared household accounts separate the billed account from the deciding person. The announcement is part of the treatment. *Cost:* the most credible read. The slowest, since it needs the full window. The hardest to sell internally.

**B. Randomized staggered rollout.** Phase the increase across regions or cohorts on a randomized schedule; use the not-yet-treated as controls. *Assumption:* parallel trends absent the increase, plus no anticipation. *Main threats:* subscribers who hear the increase is coming may churn early or lock in annual plans, contaminating the pre-period — allow an anticipation window around the announcement date. A pooled two-way fixed-effects regression misestimates effects that vary across cohorts; estimate group-time ATTs instead. *Cost:* easier to approve than a holdout. Slower to read. Credible only if the parallel-trends story holds.

**C. Regression discontinuity at an eligibility threshold.** If the increase applies above a cutoff — tenure at or above X keeps the old price, or only the premium tier rises — compare subscribers just above and below. *Assumption:* no precise manipulation of the running variable at the cutoff. Check the density and covariate balance at the cutoff. *Main threat:* the estimand is local. Subscribers at exactly tenure X may not represent the base. *Cost:* cheap and fast where a threshold exists. Treat it as a complement to another design.

**D. Structural demand estimation.** Estimate heterogeneous elasticities from observed price variation, instrumenting price (same plan's price in other markets, cost shifters). *Assumption:* instrument exogeneity — the instrument affects churn only through price. *Main threats:* price is endogenous, since firms raise prices where demand is strong. Instruments are often weak. The discrete-choice functional form does real work in the result. *Cost:* fast, and it extrapolates to any counterfactual price. The least credible of the four without a strong instrument. Best used to extend an experimental read to untested prices.

The tradeoff: credibility rises from D to A; speed and feasibility run the other way. No design maximizes all three.

## 4. What established research says

- Price responses grow over time: a dollars-borrowed elasticity of −1.1 in year one, −2.9 in year three (Karlan & Zinman 2020). Fix the window before reading results.
- Subscribers disengage before they cancel: gym members wait an average 2.3 months between their last visit and contract termination, paying $185 in monthly fees in between (DellaVigna & Malmendier 2006). Track usage, not just cancellation.
- How the price is presented changes the response: posting tax-inclusive prices cut grocery demand 8% in a three-week field experiment (Chetty, Looney & Kroft 2009). Standardize the announcement across arms, or randomize the framing.
- Staggered rollouts need group-time ATTs estimated under conditional parallel trends (Callaway & Sant'Anna 2021). A pooled two-way fixed-effects regression misestimates effects that differ across cohorts.
- Random-coefficients demand models recover heterogeneous elasticities from market-level price and quantity data (Berry, Levinsohn & Pakes 1995). Useful for simulating prices you did not test; the result rests on the instruments and the functional form.

## 5. Industry practice

*Industry write-ups — not peer-reviewed. Companies publish wins; treat magnitudes as existence proofs, not estimates.*

> **Netflix, January 2022 price increase (press/earnings reporting).** Netflix raised all US plan prices in January 2022 (Standard $13.99 → $15.49) with no experimental holdout. In Q2 2022 it reported a net loss of 970,000 subscribers worldwide — 1.3 million in the US and Canada — while revenue rose about 9% year over year on higher average revenue per membership. Management attributed the subscriber miss to account sharing, competition, and connected-TV adoption; content strength (Stranger Things 4) partly offset the loss.
> - Caveat: observational. No control group, and the quarter mixed the price change with content, competition, and password-sharing headlines. Baselines and segment detail were not disclosed.
> - What this means for the question: without a holdout, Netflix could not separate the price effect from everything else that quarter. It also shows why the estimand must be net revenue per subscriber, not churn alone.

> **Spotify, 2023–2024 price increases (earnings calls).** Spotify raised the US individual Premium price $9.99 → $10.99 in July 2023 — its first US increase in over a decade — with a one-month grace period for existing subscribers, then $10.99 → $11.99 in June 2024. In Q3 2023 Premium subscribers grew 3% quarter over quarter to 226 million (+16% year over year). CEO Daniel Ek said on the Q2 2024 call: "We're seeing less churn in this round of increases than we did in our prior one, which was already very low by any measure."
> - Caveat: company-reported, no churn baseline disclosed, no control group; concurrent product changes (audiobooks) confound the read.
> - What this means for the question: two increases in twelve months with low reported churn — price sensitivity depends on perceived value and on how the increase is communicated (the grace period standardizes the announcement regime). Treat it as proof that low-churn increases are possible, not as an estimate of your elasticity.

> **Kohavi, Tang & Xu (2020), *Trustworthy Online Controlled Experiments* (Cambridge University Press); related KDD practitioner work.** Experimentation leaders from Amazon, Google, LinkedIn, and Microsoft codify the discipline: validate the instrument first (sample-ratio-mismatch checks, A/A tests) before reading any result, and choose an overall evaluation criterion that proxies long-term value. Kohavi et al. explicitly warn that raising prices can lift short-term profit while hurting long-term value, because users find alternatives over time.
> - Caveat: practitioner guidance, not peer-reviewed economics; the examples skew toward search and ads rather than subscriptions.
> - What this means for the question: pre-register a long-horizon criterion — retained revenue per subscriber over 6–12 months — rather than 30-day churn or short-run profit, and run randomization checks before reading the price test.

> **ProfitWell / Paddle pricing research (vendor).** In a correlational study of 55 low-discount vs. 33 heavy-discount SaaS companies drawn from its metrics platform, ProfitWell (via Patrick Campbell's practitioner talks) reports that discount-acquired customers churn at much higher rates and show roughly 32% lower lifetime value than full-price customers.
> - Caveat: vendor research — small samples, correlational, selection into discounting unaddressed, figures summarized via third-party compilations of Campbell's talks rather than a published study.
> - What this means for the question: price changes alter *who* stays, not just how many. A pooled churn number mixes the behavioral response with a composition shift, which is another reason to estimate effects by segment.

## 6. Paper notes

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
> - Identification: descriptive — contract choice vs. realized attendance for roughly 7,800 members across three US health clubs over three years.
> - Magnitude: 2.3 months on average between the last attendance and contract termination; $185 in monthly fees paid after the last visit.
> - Setting: US health clubs, late 1990s–early 2000s. Auto-renewing subscription — structurally close to the question.
> - Mechanism: overconfidence about future attendance and underestimation of cancellation hassle.
> - Critique: no price variation, so nothing here identifies an elasticity. Its value is measurement.
> - Status: established behavioral classic.
> - What this means for the question: track engagement alongside churn. "Still subscribed" includes months of paying without using.

> **Chetty, Raj, Looney, Adam & Kroft, Kory (2009), "Salience and Taxation: Theory and Evidence," *American Economic Review* 99(4), 1145–1177.**
> - Question: do consumers underreact to prices they do not see?
> - Identification: three-week field experiment posting tax-inclusive prices on 750 grocery products, plus state excise-tax variation on alcohol. The grocery experiment is clean and randomized.
> - Magnitude: 8% demand reduction for treated products during the three weeks.
> - Setting: US grocery, 2006; state alcohol taxes. The mechanism — attention mediates price response — applies to any billed price.
> - Mechanism: inattention to non-salient price components.
> - Critique: short-run; the salience gap may narrow as consumers learn.
> - Status: well-established.
> - What this means for the question: standardize the price-increase announcement across test arms, or randomize the framing as a second factor. Otherwise the measured elasticity is specific to one communication regime.

> **Callaway, Brantly & Sant'Anna, Pedro H.C. (2021), "Difference-in-Differences with Multiple Time Periods," *Journal of Econometrics* 225(2), 200–230.**
> - Question: how to estimate DiD with staggered treatment timing.
> - Identification: econometric theory — identifies group-time ATT(g,t) under conditional parallel trends. Proof-based; in application, credibility rests on the assumption and on a clean never-treated control group.
> - Magnitude: methodological. Their minimum-wage illustration shows robust and naive two-way fixed-effects estimators can differ materially.
> - Setting: methods paper; applies wherever treatment rolls out in cohorts.
> - Mechanism: n/a (methods).
> - Critique: fixes the estimator, not the identification. Still needs pre-trends checks and standard errors clustered at the assignment level.
> - Status: established — the current standard for staggered DiD.
> - What this means for the question: if the increase is phased, report cohort-by-cohort ATTs against a never-treated control and show pre-trends. Skip the single pooled regression.

> **Roth, Jonathan, Sant'Anna, Pedro H.C., Bilinski, Alyssa & Poe, John (2023), "What's Trending in Difference-in-Differences? A Synthesis of the Recent Econometrics Literature," *Journal of Econometrics* 235(2), 2218–2244.**
> - Question: what do the recent DiD advances imply for practitioners?
> - Identification: synthesis, not an empirical paper. Lays out a baseline set of DiD assumptions and maps recent methods to which assumption each relaxes — staggered timing, parallel-trends violations, or inference.
> - Magnitude: n/a.
> - Setting: methods synthesis; the practitioner recommendations are the product.
> - Mechanism: n/a (methods).
> - Critique: a map, not a test — it tells you which estimator fits your assumption, not whether your assumption holds.
> - Status: recent and widely used as the practitioner's entry point to the modern DiD literature.
> - What this means for the question: before choosing an estimator for a phased rollout, check the two assumptions price rollouts most often break — no anticipation (subscribers react to the announcement, not the billing date) and parallel trends across rollout cohorts — and pick the method that survives the weaker one.

## 7. Recommended approach

**Primary: randomized holdout at renewal.** Randomize renewing subscribers into the increase vs. a holdout at the old price. Randomize at cohort or geography level to limit spillover. Stratify by tenure, engagement, and plan tier to get segment elasticities. Pre-register the window (6 months minimum, 12 preferred), the outcomes (retention, downgrade rate, net revenue per subscriber), and the decision rule before results arrive — for example: roll out if 12-month projected net revenue per subscriber beats control, with no segment's churn increase above a set threshold. Randomize the announcement framing as a second factor.

**Fallback: randomized phased rollout.** Randomize the rollout order across regions or cohorts. Keep a never-treated control group. Estimate group-time ATTs, show pre-trends, and allow an anticipation window around the announcement date.

**Complement: a light demand model.** Fit a simple segment-level demand curve to the experimental read to simulate other increase sizes. Do not re-run the experiment for each candidate price.

**What would change the recommendation:** if randomization is off the table entirely, lead with structural demand plus any available threshold discontinuity and mark the answer provisional. If backlash spills across test cells, randomize at a coarser level. If an answer is needed before 6 months, use engagement drops as an early signal — but pre-commit to the full window. Do not stop the test early on a short-window read.

## 8. Open threads

- The margin may be downgrade, not cancel. Model churn, downgrade, and revenue per subscriber together.
- Gross churn overstates net loss if marginal subscribers return on promotion. Track net retention.
- A unilateral increase and a market-wide increase are different counterfactuals. None of these designs capture competitor repricing.
- Repeated increases may erode trust in ways one experiment misses.
- Annual and monthly plans face the increase at different times with different salience. Analyze them separately.
