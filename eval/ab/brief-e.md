# How should we measure the causal impact of a subscription price increase on churn?

*Measurement mode: this is a "how do we estimate the causal effect of X on Y" question.*

**Bottom line:** run a randomized price holdout as the primary design — randomize who faces the increase, pre-register a 6–12 month horizon, and measure retained revenue per subscriber, not just churn. If a holdout is politically infeasible, phase the increase across cohorts or regions on a randomized schedule and analyze it with modern staggered difference-in-differences, not a naive pooled regression. Structural demand estimation is a complement for extrapolating to other price points, not a substitute for a causal design.

## 1. The estimand

The number the business needs is the average treatment effect on the treated (ATT) of *the specific planned price increase* — on *retention and net revenue per subscriber over a 6–12 month horizon* — among *the subscribers who would face it*. Three things this pins down:

- **Churn alone is the wrong metric.** A price increase moves subscribers across several margins: outright cancellation, downgrades to cheaper tiers, pauses, and — for the majority who stay — higher revenue per subscriber. The key metric is the causal change in retained revenue per subscriber, not headline churn.
- **The horizon is load-bearing.** Price responses grow over time as subscribers learn, evaluate alternatives, and hit renewal dates. A 30-day churn read systematically understates the full response.
- **ATT, not ATE.** Grandfathering or targeted rollout means the exposed group is selected (newer, more marginal subscribers). The measured effect describes them, not what a universal increase would do to the whole base — and elasticity will differ sharply by tenure, engagement, and plan tier.

## 2. Success criteria

A credible answer must satisfy five things: (1) a valid counterfactual — what would have happened to these subscribers absent the increase; (2) a pre-registered horizon of at least 6 months, fixed before results arrive; (3) all response margins measured (cancel, downgrade, pause, revenue), not just gross churn; (4) segment-level estimates, since elasticity differs by tenure, engagement, and plan; (5) a decision rule set in advance, so the result can't be reinterpreted afterward.

## 3. Candidate designs

The central tradeoff is speed × credibility × political feasibility. No design maximizes all three.

**A. Randomized price holdout.** Randomize renewing subscribers (or cohorts/regions) into the increase vs. a holdout at the old price. *Assumption:* randomization held (balance, no differential attrition) and SUTVA — no interference between arms. *Main threats:* word-of-mouth and social-media backlash contaminate the control group (randomize at cohort or geography level to blunt this); shared household accounts mean the billed unit and the deciding unit differ; the announcement itself is part of the treatment. *Cost:* the most credible read, but the slowest (needs the full horizon) and the hardest sell internally.

**B. Randomized staggered rollout.** Phase the increase across regions or cohorts on a randomized schedule; use the not-yet-treated as controls. *Assumption:* parallel trends absent treatment. *Main threats:* anticipation (subscribers who know the increase is coming churn early or lock in annual plans — contaminates the pre-period, so allow an anticipation window); a naive two-way fixed-effects regression is biased when effects differ across cohorts — you need group-time ATTs à la Callaway–Sant'Anna. *Cost:* politically easier than a holdout, but slower and only as credible as the parallel-trends story.

**C. Regression discontinuity at an eligibility threshold.** If the increase applies above a cutoff — tenure ≥ X keeps the old price, a premium tier only — compare subscribers just above and below. *Assumption:* no precise manipulation of the running variable at the cutoff. *Main threat:* the estimand is local to the threshold; subscribers at exactly-tenure-X may not represent the base. *Cost:* cheap and fast where a threshold exists; a complement, never the whole answer.

**D. Structural demand estimation (BLP-style).** Estimate heterogeneous elasticities from observational price variation with instruments (e.g., the same plan's price in other markets, cost shifters). *Assumption:* instrument exogeneity — the instrument affects churn only through price. *Main threats:* price is endogenous (you raise prices where demand is strong), instruments are often weak, and the discrete-choice functional form does heavy lifting. *Cost:* fast and extrapolates to any counterfactual price — but it's the least credible of the four without a real instrument. Best used to extend an experimental read to untested price points.

## 4. What established research says

- Randomized price variation shows demand responses grow over time: Karlan & Zinman (2019) find a price elasticity that rises from −1.1 in year one to −2.9 in year three — so a short test understates the churn effect, and the horizon choice is load-bearing. [Field experiment, *Review of Economic Studies*; well-established.]
- Cancellation lags the decision: DellaVigna & Malmendier (2006) document gym members waiting an average 2.3 months after their last visit to cancel — "still subscribed" is not "still engaged," and short-window churn misses the delayed margin. [AER; heavily cited behavioral classic.]
- Salience is part of the treatment: Chetty, Looney & Kroft (2009) find that posting tax-inclusive prices cuts demand 8% — how you announce the increase changes the response, so hold communication constant or randomize it. [AER field experiment; well-established.]
- Elasticity is heterogeneous: DellaVigna & Gentzkow (2019) show within-firm elasticity variation large enough that uniform pricing costs the median chain $16m/year — measure segment-level elasticities, because the optimal increase almost surely differs by segment. [QJE.]
- Staggered rollouts need modern estimators: Callaway & Sant'Anna (2021) show how to estimate group-time ATTs without the negative-weighting bias of naive two-way fixed effects — if you phase the increase, this is the toolkit. [J. Econometrics; 3,000+ RePEc citations, the current standard.]
- When experiments are infeasible, structural demand models (Berry, Levinsohn & Pakes 1995) recover heterogeneous elasticities from observational variation — useful for simulating counterfactual prices, but only as credible as the instruments. [Econometrica; the standard reference for demand estimation.]

## 5. Paper notes

> **Karlan, Dean & Zinman, Jonathan (2019), "Long-Run Price Elasticities of Demand for Credit: Evidence from a Countrywide Field Experiment in Mexico," *Review of Economic Studies* 86(4), 1704–1746.**
> - Question: how elastic is credit demand to interest rates over 29 months?
> - Identification: countrywide field experiment — randomized interest rates across 80 geographically distinct regions for Mexico's largest microlender (Compartamos). Region-level randomization directly addresses interference; the 29-month follow-up is rare for a price experiment.
> - Magnitude: dollars-borrowed elasticity of −1.9 over 29 months, rising from −1.1 in year one to −2.9 in year three (the treatment was a ~10% rate reduction).
> - Setting: Mexican microlending, 2011–13. Credit, not subscriptions — the *growing-elasticity pattern* is what transports, not the number.
> - Mechanism: learning vs. adjustment costs; the authors flag this as an open question rather than resolving it.
> - Critique: the no-crowd-out result from credit bureau data is imprecisely estimated; competitors didn't respond, so nothing is learned about equilibrium effects.
> - Status: well-established — published Rev. Econ. Stud., influential as one of the few long-horizon price experiments.
> - What this means for the question: pre-commit to a long measurement window — a 1–3 month churn read captures only a fraction of the true response.

> **DellaVigna, Stefano & Malmendier, Ulrike (2006), "Paying Not to Go to the Gym," *American Economic Review* 96(3), 694–719.**
> - Question: do consumers choose subscription contracts rationally?
> - Identification: descriptive/structural — contract choice vs. realized attendance for 7,752 members across three U.S. health clubs over three years. Not causal about price; precisely measured behavior.
> - Magnitude: monthly members paid $17+ per expected visit vs. a $10 ten-visit pass, forgoing ~$600 in savings; average lag between last attendance and cancellation was 2.29 months ($185 in fees after the last visit).
> - Setting: U.S. health clubs, early 2000s. Auto-renewing subscription — structurally close to your setting.
> - Mechanism: overconfidence about future attendance and underestimation of cancellation hassle — inattention, not preferences.
> - Critique: single industry, no price variation to identify elasticity. Its value is measurement, not a number.
> - Status: established behavioral classic, heavily cited.
> - What this means for the question: track disengagement alongside churn — subscribers stop using the product months before they cancel, so the effective churn response is larger and slower than the cancellation series shows.

> **Chetty, Raj, Looney, Adam & Kroft, Kory (2009), "Salience and Taxation: Theory and Evidence," *American Economic Review* 99(4), 1145–1177.**
> - Question: do consumers underreact to non-salient taxes/prices?
> - Identification: two complementary strategies — a three-week field experiment posting tax-inclusive prices on 750 grocery products, plus state-level excise vs. sales tax variation on alcohol. The grocery experiment is clean and randomized.
> - Magnitude: posting tax-inclusive prices reduced demand by 8%; excise taxes (in posted prices) cut alcohol consumption more than equivalent register-added sales taxes.
> - Setting: U.S. grocery store + state alcohol taxes, 2000s. The mechanism — attention mediates price response — generalizes to any billed price.
> - Mechanism: inattention to non-salient price components; consumers optimize against perceived, not actual, prices.
> - Critique: short-run experiment; long-run learning could erode the salience gap. A skeptic would ask whether the 8% persists.
> - Status: well-established — AER, heavily cited, the standard reference on salience and price response.
> - What this means for the question: a loudly announced increase and a quietly applied one are different treatments — standardize the announcement across test arms or, better, randomize the framing as a second experimental factor.

> **DellaVigna, Stefano & Gentzkow, Matthew (2019), "Uniform Pricing in U.S. Retail Chains," *Quarterly Journal of Economics* 134(4), 2011–2084.**
> - Question: why do chains price uniformly across heterogeneous stores?
> - Identification: descriptive on pricing uniformity (scanner data) plus structural demand estimates to benchmark optimal vs. uniform pricing. The uniformity fact is clean; the $16m/year profit sacrifice is a model-based counterfactual.
> - Magnitude: the median chain sacrifices $16 million in annual profit vs. segment-optimal prices; within-chain elasticity variation is substantial.
> - Setting: U.S. retail chains, 2010s. Retail goods, not subscriptions — the *heterogeneity magnitude* is the transportable fact.
> - Mechanism: managerial inertia and brand-image concerns sustain uniform pricing; underlying it, elasticity varies enormously within a firm.
> - Critique: the $16m figure leans on the structural benchmark; don't calibrate your churn number from it.
> - Status: well-established — QJE, well-cited for its age.
> - What this means for the question: don't estimate one pooled churn elasticity — cut by tenure, engagement, and plan tier, because the profitable move is almost certainly a differentiated increase.

> **Callaway, Brantly & Sant'Anna, Pedro H.C. (2021), "Difference-in-Differences with multiple time periods," *Journal of Econometrics* 225(2), 200–230.**
> - Question: how to do DiD with staggered treatment timing.
> - Identification: econometric theory — identifies group-time ATT(g,t) under conditional parallel trends, avoiding the negative-weighting pathology of two-way fixed effects. Proof-based; in application, credibility rests on parallel trends and a clean never-treated control group.
> - Magnitude: methodological — their minimum-wage illustration shows robust and TWFE estimators can materially disagree.
> - Setting: methods paper; applies wherever treatment rolls out in cohorts — exactly a phased price increase.
> - Mechanism: n/a (methods).
> - Critique: fixes the estimator, not the identification — you still need credible parallel trends, enough pre-periods, and standard errors clustered at the treatment-assignment level.
> - Status: established — J. Econometrics, 3,000+ RePEc citations, the current standard for staggered DiD.
> - What this means for the question: if the increase is phased rather than randomized, estimate cohort-by-cohort ATTs with a never-treated control and show pre-trends — never a single pooled before/after regression.

> **Berry, Steven, Levinsohn, James & Pakes, Ariel (1995), "Automobile Prices in Market Equilibrium," *Econometrica* 63(4), 841–890.**
> - Question: how to estimate demand and markups in differentiated-product markets from market-level data.
> - Identification: structural — random-coefficients logit with instrumental variables for price endogeneity (cost shifters / prices of the same product in other markets). Credibility rests on the instruments and functional form, not randomization.
> - Magnitude: the paper's contribution is the method, not a single number — subsequent applications routinely find own-price elasticities in the −2 to −4 range for differentiated consumer goods.
> - Setting: U.S. automobiles, 1971–1990. The *technique* transports to subscriptions; the *numbers* do not.
> - Mechanism: heterogeneous consumer tastes generate realistic substitution patterns — the right frame for "cancel vs. downgrade vs. stay."
> - Critique: misspecified heterogeneity or weak instruments bias every elasticity; a skeptic would demand an experimental cross-check before trusting a simulated price increase.
> - Status: established — Econometrica, the standard reference for demand estimation.
> - What this means for the question: use structural demand to extrapolate from one tested price point to others — never as the sole basis for the increase.

## 6. Recommended approach

**Primary: randomized holdout at renewal.** Randomize renewing subscribers into the increase vs. a clean holdout; randomize at the cohort or geography level to blunt interference; stratify by tenure, engagement, and plan tier so you get segment elasticities. Pre-register the primary horizon (6 months minimum, 12 preferred), the outcomes (retention, downgrade rate, net revenue per subscriber), and the decision rule before results arrive — e.g., "roll out if 12-month projected net revenue per subscriber exceeds control at 95% confidence, with no segment showing a churn increase above X pp." Randomize the announcement framing as a second factor.

**Fallback: randomized phased rollout + Callaway–Sant'Anna.** If a holdout is politically infeasible, randomize the rollout order across regions/cohorts, keep a clean never-treated control, estimate group-time ATTs, show pre-trends, and allow an anticipation window around the announcement date.

**Complement: light structural demand.** Once the experiment pins down the response at the tested increase, fit a simple segment-level demand curve to simulate other increase sizes — don't re-run the experiment for each candidate price.

**What would change the recommendation:** if randomization is entirely off the table, lead with structural demand plus any available RDD threshold and mark the answer as provisional; if interference across test cells is severe (viral backlash), randomize coarser, not finer; if you need an answer faster than 6 months, use engagement drops as a *leading indicator* but pre-commit to the full horizon — never stop the test early on a short-window read.

## 7. Open threads

- **Downgrade vs. cancel:** the relevant substitution may be to a cheaper tier — is the outcome churn, downgrade, or revenue per subscriber? Model all three margins.
- **Win-back:** gross churn overstates net loss if marginal subscribers return on promotion — track net retention, not just gross churn.
- **Competitive response:** a unilateral vs. market-wide increase are different counterfactuals; none of these designs capture competitor repricing.
- **Long-run trust:** repeated increases may erode goodwill in ways no single experiment captures; the trial literature's short horizons are the binding constraint everywhere.
- **Annual vs. monthly plans:** the two face the increase at different times with different salience — analyze them as separate experiments, not one pooled number.
