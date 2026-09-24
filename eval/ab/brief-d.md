# Brief D (VANILLA): How should we measure the causal impact of a subscription price increase on churn?

## 1. Define the causal quantity first

Before choosing a method, pin down exactly what number the business needs. "The impact of the price increase on churn" is ambiguous in at least four ways, and each ambiguity changes the design:

- **Which price change?** A 10% increase is a different treatment from a $2 increase, and from a tier restructuring. The causal quantity is the effect of *the specific increase you plan to roll out*, not "price sensitivity" in the abstract.
- **Churn of whom, over what horizon?** The relevant estimand is usually the change in the probability of churning within H months of facing the increase, for the subscribers who would face it (the treated population). Churn is a duration outcome: some subscribers leave in month one, others downgrade, pause, or quietly disengage and leave in month nine.
- **Churn isn't the only margin.** A price increase moves subscribers across several margins: outright cancellation, downgrades to cheaper tiers, pauses, reduced engagement, and — for the majority who stay — higher revenue per subscriber. Measuring only cancellations understates the behavioral response and misstates the revenue tradeoff, which is the actual decision variable.
- **Short-run vs. long-run.** This distinction is first-order. Karlan & Zinman (2019), in a countrywide field experiment randomizing interest rates across 80 regions for Mexico's largest microlender, estimated a 29-month elasticity of demand for credit of −1.9 — but the elasticity grew from −1.1 in year one to −2.9 in year three (*Review of Economic Studies* 86(4)). A one-month read on churn will systematically understate the full response, because subscribers need time to evaluate alternatives, wait out annual commitments, or simply notice.

**Bottom line on the estimand:** you want the causal effect of *your planned increase* on *subscriber retention and revenue over a 6–12 month horizon*, for *the population that will face it* — not a generic "price elasticity," and not a 30-day cancellation blip.

## 2. Why the naive approaches fail

- **Before/after comparison** ("churn was 4% before the increase, 5.5% after") confounds the price change with seasonality, product changes shipped around the same time, marketing campaigns, and macro conditions. It has no counterfactual.
- **Comparing subscribers who got the increase vs. those who didn't**, when the increase wasn't randomized (e.g., grandfathered legacy plans vs. new plans), compares different populations. Grandfathered subscribers differ in tenure, vintage, and engagement — all predictors of churn.
- **Surveys and stated willingness-to-pay** measure what people say, not what they do when the renewal charge actually hits.

## 3. Research designs that can identify the effect

### A. Randomized price test (gold standard)

Randomize a subset of subscribers (or markets) to receive the price increase while a holdout stays at the current price, then compare churn and revenue over a pre-registered horizon.

**Why it's credible:** randomization makes the treated and control groups comparable on everything except the price, so the difference in churn is the causal effect. This is the same logic as Karlan & Zinman's randomized interest rates — the experiment *is* the identification.

**Key assumptions and threats:**
- **No interference between groups.** If treated subscribers tell control subscribers about the increase (social media, forums, shared household accounts), the control group is contaminated. Mitigate by randomizing at the level of geography or acquisition cohort rather than individual where spillover is likely — Karlan & Zinman randomized across 80 distinct regions for exactly this reason.
- **The announcement is part of the treatment.** How subscribers learn about the increase — email framing, in-app notice, timing relative to billing — changes the response. Chetty, Looney & Kroft (2009) showed in a field experiment that posting tax-inclusive prices reduced grocery demand by 8%, and that excise taxes folded into posted prices cut alcohol consumption far more than equivalent taxes added at the register (*American Economic Review* 99(4)). Salience is not a footnote; it *is* part of the treatment. Either hold communication constant across arms or — better — randomize the framing as a second experimental factor so you learn which communication minimizes churn for a given price.
- **Novelty and Hawthorne effects fade.** Early responses may reflect surprise rather than the steady-state demand curve. This is another reason the horizon must be long.
- **External validity.** The test estimates the effect on the tested population at the tested increase. A 10% test doesn't directly tell you the effect of 20%, and an effect on US subscribers doesn't directly transfer to price-sensitive emerging markets. Plan heterogeneity analysis by segment (see §5).

### B. Staggered or geographic rollout analyzed as a quasi-experiment

If a full randomized holdout is politically infeasible, the next best thing is to **randomize the rollout order** — phase the increase across regions or cohorts on a randomized schedule, and use the not-yet-treated as controls for the already-treated (difference-in-differences).

**Key assumption:** parallel trends — treated and not-yet-treated units would have followed the same churn path absent the increase. **Threats:** anticipation (subscribers who know the increase is coming may churn early or lock in annual plans — check pre-trends), cross-region spillover (same interference problem as above), and treatment-effect heterogeneity across rollout waves (early-wave regions may differ from late-wave ones; use estimators robust to staggered timing rather than a single pooled regression).

If the rollout order *wasn't* randomized, you can still do difference-in-differences, but the parallel-trends assumption is now a leap of faith rather than something randomization buys you — validate it with pre-period event-study plots and be honest about the gap.

### C. Regression discontinuity at eligibility thresholds

If the increase applies above a cutoff — e.g., only to subscribers past a tenure threshold, or only to a premium tier — compare subscribers just above and just below the cutoff. Near the threshold, assignment is as-good-as-random.

**Limitation:** this identifies a *local* effect — the churn response of subscribers at the threshold, who may be unrepresentative (e.g., exactly-at-tenure-X subscribers). Useful as a complement, rarely sufficient alone.

### D. Structural demand estimation (when experiments are infeasible)

When you cannot run any price variation, the industrial-organization toolkit estimates demand from observational price and quantity variation — but price is endogenous (you raise prices where demand is strong), so it requires **instruments**: variables that shift price without directly shifting demand. Berry, Levinsohn & Pakes (1995) built the canonical framework for this, using cost shifters and prices of the same product in other markets as instruments (*Econometrica* 63(4)).

**Key assumption:** instrument exogeneity — e.g., that a cost shock affects churn *only* through the price you set. **Threats:** weak instruments, and the strong functional-form assumptions of the discrete-choice model. For a subscription business with rich individual-level data, this is usually a complement to — not a substitute for — an experiment. Its real value is *extrapolation*: once an experiment pins down the response at one price point, a demand model lets you simulate others.

## 4. What the literature says about where the money is

DellaVigna & Gentzkow (2019) document that large US retail chains charge nearly *uniform* prices across stores despite wide variation in local demand, and estimate the median chain sacrifices roughly $16 million in annual profit relative to segment-optimized prices (*Quarterly Journal of Economics* 134(4)). The lesson for subscriptions: **elasticity varies enormously across segments** — by tenure, engagement, plan tier, acquisition channel, and geography — and a single average elasticity hides the profitable move. The churn response of a highly engaged 3-year subscriber and a month-two trial convert are different parameters; measure them separately, because the optimal price increase almost certainly differs by segment too.

## 5. Recommended measurement approach

1. **Run a randomized holdout test.** Randomize at the geographic or cohort level (to limit interference), with the increase applied to ~80–90% of the base and a clean holdout kept at the current price. Pre-register the primary horizon (6 months minimum, 12 preferred — per Karlan & Zinman, short windows understate the effect), the primary outcomes (retention/churn, downgrade rate, and net revenue per subscriber), and the segment breakdowns.
2. **Randomize the announcement as a second factor.** Test 2–3 communication framings (e.g., value-forward email vs. plain notice; advance warning vs. at-renewal). Chetty et al. imply the framing can move the response by economically meaningful amounts — this is free learning.
3. **Estimate segment-level elasticities, not one number.** Cut by tenure, engagement decile, plan tier, and market. The decision you actually face is which segments can bear the increase and which need grandfathering or a smaller bump (the DellaVigna–Gentzkow point).
4. **Track the full margin structure.** Report cancellations, downgrades, pauses, and engagement changes — and compute the net revenue effect, which is what the price decision optimizes. A 1.5-point churn increase that comes with 10% higher ARPU on the remaining 95%+ can still be strongly profitable.
5. **Use engagement as a leading indicator, not the answer.** Drops in logins or usage typically precede cancellation by weeks; useful for early reads, but don't stop the test early on engagement alone — pre-commit to the horizon.
6. **Extrapolate with a light demand model.** Once the experiment gives you causal responses at the tested increase for each segment, fit a simple demand curve per segment to simulate alternative increase sizes, rather than re-running the experiment for each candidate price.
7. **Set the decision rule in advance.** E.g., "roll out if projected 12-month net revenue is positive with churn increase below X in every segment" — decided before results arrive, so the test can't be reinterpreted afterward.

**What would change the answer:** a much longer horizon showing the Karlan–Zinman-style elasticity growth continuing past month 12 (arguing for an even longer test); evidence of strong interference between test cells (arguing for coarser randomization); or segment elasticities so uniform that a single increase dominates (simplifying the rollout).

**Papers cited** (all verified): Karlan & Zinman (2019), *Review of Economic Studies* 86(4); Berry, Levinsohn & Pakes (1995), *Econometrica* 63(4); DellaVigna & Gentzkow (2019), *Quarterly Journal of Economics* 134(4); Chetty, Looney & Kroft (2009), *American Economic Review* 99(4).
