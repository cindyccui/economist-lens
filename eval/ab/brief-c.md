# Brief C (SKILL-EQUIPPED): How should we measure the causal impact of a subscription price increase on churn?

## 1. The question, restated

The decision margin is not "raise or not" — it is which measurement design credibly isolates the causal effect of a price increase on subscriber churn. In economic terms: the **price elasticity (more precisely, the semi-elasticity) of churn** — how many percentage points of churn a 1% price increase causes — plus its heterogeneity across segments. The relevant subfields are industrial organization (demand estimation), causal inference (experimental and quasi-experimental design), and behavioral economics (inattention and inertia, which blunt the price–churn link). The estimand to name up front: the **average treatment effect on the treated (ATT)** — the churn increase *among subscribers exposed to the increase* — which is not the same as the population elasticity, because exposure is selective (grandfathering, plan type, tenure).

## 2. What the canon says

- **Berry, Levinsohn & Pakes (1995):** random-coefficients demand estimation recovers heterogeneous price elasticities from observational data — the canonical toolkit for simulating counterfactual price changes when you cannot experiment.
- **Hoch, Kim, Montgomery & Rossi (1995):** price elasticities vary systematically across stores and are driven more by consumer demographics than by competition — expect churn elasticity to differ sharply by segment and tenure, and plan to estimate it that way.
- **DellaVigna & Malmendier (2006):** subscription cancellation is sluggish — a 2.31-month average lag between last use and termination — so short-window churn understates true price sensitivity and inertia contaminates naive before/after comparisons.
- **Handel (2013):** inertia in plan choice is large and separately identified from preferences — any churn-based elasticity blends "didn't notice the increase" with "noticed and didn't care," and you need a design that separates them.

## 3. What's new

- **DellaVigna & Gentzkow (2019):** within-firm price-elasticity variation is large enough that uniform pricing costs the median chain $16m/year — direct support for segment-specific elasticity measurement rather than one pooled number.
- **Ho, Hogan & Morton (2017):** inattentive consumers blunt the price–demand link and firms profit from the inertia — your measured churn elasticity is a lower bound on the "attentive" elasticity, and *how salient you make the increase* (email framing, notice period) is itself a treatment margin.
- **Callaway & Sant'Anna (2021) and Arkhangelsky et al. (2021):** the modern toolkit for staggered or geographic price rollouts — group-time ATTs and synthetic difference-in-differences replace the naive two-way fixed-effects regression, which is biased under heterogeneous effects.
- **Hall, Kendrick & Nosko (2015):** a natural-experiment case study of Uber surge pricing (a 26-minute surge outage as the control) — illustrative, not peer-reviewed, but the cleanest template for RDD-style identification around a price discontinuity.

## 4. Paper briefs

> **Berry, Steven, Levinsohn, James & Pakes, Ariel (1995), "Automobile Prices in Market Equilibrium," *Econometrica* 63(4), 841–890.**
> - Question: how to estimate demand and markups in differentiated-product markets from market-level data.
> - Identification: structural — random-coefficients logit with instrumental variables for price endogeneity (cost shifters / BLP instruments). Credibility rests on the instruments and the functional form, not on randomization; strong where exclusion holds, fragile where it doesn't.
> - Magnitude: the paper's contribution is the method, not a single elasticity; subsequent applications routinely find own-price elasticities in the −2 to −4 range for differentiated consumer goods. (Bijmolt, van Heerde & Pieters (2005) meta-analysis: grand mean −2.62 across 1,851 estimates — a benchmark, not a substitute for your own number.)
> - Setting: U.S. automobiles, 1971–1990. Methodological canon; the *technique* transports to subscriptions, the *numbers* do not.
> - Mechanism: heterogeneous consumer tastes generate realistic substitution patterns — essential for churn, where the relevant margin is "cancel vs. downgrade vs. stay," not just "buy vs. not."
> - Critique: structural assumptions do the heavy lifting; misspecified heterogeneity or weak instruments bias every elasticity. A skeptic would demand an experimental or quasi-experimental cross-check before trusting a simulated price increase.
> - Status: canonical — 2,000+ citations, Citation Laureate; the standard reference for demand estimation.

> **Hoch, Stephen J., Kim, Byung-Do, Montgomery, Alan L. & Rossi, Peter E. (1995), "Determinants of Store-Level Price Elasticity," *Journal of Marketing Research* 32(1), 17–29.**
> - Question: what explains variation in price elasticity across stores?
> - Identification: two-stage — first estimate category elasticities from scanner panel data (Dominick's), then regress them on demographics and competitive variables. Descriptive in the second stage; the elasticities themselves come from observed price variation with the usual endogeneity caveats.
> - Magnitude: category elasticities vary widely across the 18 categories and 83 stores studied; consumer demographics (education, household size, ethnicity) dominate competitive factors in explaining the variation.
> - Setting: Chicago supermarket chain scanner data, early 1990s. Grocery, not subscriptions — but the *heterogeneity* lesson is the point.
> - Mechanism: price sensitivity is a household trait, not a market trait — which is why segment-level churn elasticities will differ more than plan-level ones.
> - Critique: no exogenous price variation; elasticities are correlational. Treat as a heterogeneity prior, not a causal estimate.
> - Status: classic within marketing/IO; the standard citation for elasticity heterogeneity.

> **DellaVigna, Stefano & Malmendier, Ulrike (2006), "Paying Not to Go to the Gym," *American Economic Review* 96(3), 694–719.**
> - Question: do consumers choose subscription contracts rationally?
> - Identification: descriptive/structural — compares contract choice to realized attendance for 7,752 members across three U.S. health clubs over three years. Not causal about price, but precisely measured behavior.
> - Magnitude: monthly members paid $17+ per expected visit vs. a $10 ten-visit pass, forgoing ~$600 in savings; average lag between last attendance and cancellation was **2.31 months**; monthly members were 17% more likely than annual members to still be enrolled after a year.
> - Setting: U.S. health clubs, early 2000s. Subscription with auto-renewal — structurally close to your setting.
> - Mechanism: overconfidence about future attendance and underestimation of cancellation hassle — inattention/inertia, not preferences.
> - Critique: single industry, no price variation to identify elasticity. Its value here is measurement: churn lags the price signal by months, so any design needs a long enough window and must distinguish "still subscribed" from "still engaged."
> - Status: established classic in behavioral contract choice.

> **Handel, Benjamin R. (2013), "Adverse Selection and Inertia in Health Insurance Markets: When Nudging Hurts," *American Economic Review* 103(7), 2643–2682.**
> - Question: how much of plan stickiness is inertia vs. preferences?
> - Identification: natural experiment — a large firm's forced menu change — plus a structural choice model that separately identifies switching costs, risk preferences, and health risk. The menu change is the credible variation; the decomposition is model-dependent.
> - Magnitude: inertia is large — the structural estimates imply switching costs that dominate observed price differences; counterfactuals show inertia roughly doubles the welfare loss from adverse selection.
> - Setting: employer health insurance, one large U.S. firm. Regulated choice setting, not subscriptions — the *identification of inertia* is what transports.
> - Mechanism: status-quo bias / hassle costs, distinct from risk preferences.
> - Critique: the exact switching-cost dollar figure leans on the structural model. But the qualitative point — measured "price sensitivity" conflates inattention with preference — is robust and directly relevant: your churn elasticity will understate true willingness-to-pay sensitivity.
> - Status: classic (AER lead article); the benchmark for separately identifying inertia.

> **Ho, Kate, Hogan, Joseph & Morton, Fiona Scott (2017), "The impact of consumer inattention on insurer pricing in the Medicare Part D program," *RAND Journal of Economics* 48(4), 877–905.**
> - Question: how does consumer inattention shape equilibrium pricing?
> - Identification: structural model of plan choice with inattentive consumers, estimated on New Jersey Part D enrollee data; counterfactual repricing under full attention. Descriptive switching facts are solid; the "attentive counterfactual" is model-based.
> - Magnitude: consumers switch plans infrequently and search imperfectly; if all consumers were attentive, the average consumer would save **$1,050 over three years** and steady-state premiums would fall — i.e., observed demand is far less elastic than attentive demand.
> - Setting: Medicare Part D, 2006–2010. Regulated insurance — the mechanism (inattention dampens price response) generalizes to any auto-renewing subscription.
> - Mechanism: inattention + imperfect search → firms optimally price into the inertia.
> - Critique: the $1,050 figure depends on the supply-side repricing model. For your purpose the takeaway is design-relevant, not numerical: *salience is a treatment margin* — a loudly announced increase and a quietly applied one are different experiments.
> - Status: well-cited modern classic on inattention and pricing.

> **DellaVigna, Stefano & Gentzkow, Matthew (2019), "Uniform Pricing in U.S. Retail Chains," *Quarterly Journal of Economics* 134(4), 2011–2084.**
> - Question: why do chains charge nearly uniform prices across heterogeneous stores?
> - Identification: descriptive on pricing uniformity (scanner data, ~1,365 products × thousands of stores) plus structural demand estimates to benchmark optimal vs. uniform pricing. The uniformity fact is clean; the $16m figure is model-based.
> - Magnitude: prices rise only 0.47% per $10,000 of local income within chains despite large elasticity differences; the median chain sacrifices **$16 million/year** vs. store-optimal pricing.
> - Setting: U.S. food/drugstore/mass-merchandise retail, 2010s. The *within-firm elasticity heterogeneity* is the transportable fact.
> - Mechanism: managerial inertia and brand-image concerns sustain uniform pricing — plus the economic point that elasticity varies enough within a firm to matter.
> - Critique: retail goods, not subscriptions; the profit-sacrifice number is a structural counterfactual. Use it to justify segment-specific measurement, not to calibrate your churn number.
> - Status: modern classic (QJE, heavily cited for its age).

> **Callaway, Brantly & Sant'Anna, Pedro H.C. (2021), "Difference-in-Differences with multiple time periods," *Journal of Econometrics* 225(2), 200–230.**
> - Question: how to do DiD with staggered treatment timing.
> - Identification: econometric theory — identifies group-time ATT(g,t) under conditional parallel trends; aggregates without the negative-weighting pathology of TWFE. Proof-based; credibility in application depends on the parallel-trends assumption and a clean never-treated (or not-yet-treated) control group.
> - Magnitude: methodological; the minimum-wage illustration shows TWFE and robust estimators can materially disagree.
> - Setting: methods paper. Applies wherever treatment rolls out in cohorts — exactly your phased price increase.
> - Mechanism: n/a (methods).
> - Critique: needs a credible control group and enough pre-periods for pre-trends checks; with few treated cohorts, inference is delicate. It fixes the estimator, not the identification.
> - Status: modern methods canon (~3,000 citations); the default reference for staggered DiD.

> **Arkhangelsky, Dmitry, Athey, Susan, Hirshberg, David A., Imbens, Guido W. & Wager, Stefan (2021), "Synthetic Difference-in-Differences," *American Economic Review* 111(12), 4088–4118.**
> - Question: a panel estimator combining DiD and synthetic control.
> - Identification: econometric theory — reweights control units *and* pre-periods to relax the parallel-trends requirement; consistent under a latent-factor outcome model. Proof-based.
> - Magnitude: methodological; simulations and the California tobacco application show robustness where plain DiD or synthetic control alone struggle.
> - Setting: methods paper; the natural fit is a geographic phased rollout (treated regions vs. weighted donor pool of untreated regions).
> - Mechanism: n/a (methods).
> - Critique: needs a decent donor pool and pre-treatment fit; less transparent than a clean experiment. A complement to, not a replacement for, randomization.
> - Status: modern methods canon (AER, 500+ citations and climbing).

> **Hall, Jonathan, Kendrick, Cory & Nosko, Chris (2015), "The Effects of Uber's Surge Pricing: A Case Study," University of Chicago Booth.**
> - Question: what does surge pricing do to rider and driver behavior?
> - Identification: natural experiment — a 26-minute New Year's Eve surge-pricing outage in NYC as the control, plus an Ariana Grande concert surge (multipliers 1.2×–1.8×) as the treated event. Clever but a two-event case study; no formal RDD, no inference framework.
> - Magnitude: descriptive — app opens rose far more than completed rides during the surge (riders balked at the multiplier); driver supply rose into the surge zone. Directional, not a portable elasticity.
> - Setting: Uber NYC, 2014–15. Ride-hailing, not subscriptions — the *design template* is the point: price discontinuities with a clean counterfactual window.
> - Mechanism: rider price sensitivity at the point of purchase plus driver supply response.
> - Critique: n = 2 events, company-authored, never peer-reviewed. Do not cite as an elasticity; do cite as the intuition pump for discontinuity-based designs (e.g., grandfathering cutoffs, intro-price expiries).
> - Status: influential industry case study; **not** peer-reviewed science — labeled as illustrative only.

## 5. What economists would argue about

- **Short-run churn vs. the true outcome.** DellaVigna & Malmendier's 2.31-month cancellation lag means a 30-day churn read understates the effect; but long windows invite confounds. Related: is the outcome churn, *net* subscriber loss (churn minus win-back/reactivation), or long-run retention? Short-run proxies can misrank designs — the surrogate-index logic from the LTV literature applies: validate any short window against longer-run retention before trusting it.
- **Inertia vs. preferences.** Handel (2013) and Ho et al. (2017) imply your measured elasticity is a lower bound on attentive willingness-to-pay sensitivity. A structuralist would model the inattention explicitly (BLP-style); a reduced-form experimentalist would say: randomize salience too, and report both the "quiet" and "loud" elasticities.
- **Structural simulation vs. experimental measurement.** BLP/Nevo gives you elasticities for *any* counterfactual price from existing data — but rests on instruments and functional form. An RCT gives you one credible number at one price point. Economists would argue about which binds: if you can only run one price test, the structural model extrapolates further but less credibly.
- **SUTVA / interference.** Household account sharing means one "subscriber" is several viewers — the price is charged per account but the churn decision is per household, and shared accounts may coordinate cancellation. Annual vs. monthly plans face the increase at different times and with different salience (one big annual charge vs. twelve small ones). Referral/word-of-mouth and social-media backlash to an announced increase spill across treatment arms.
- **Anticipation and selection.** Announcing the increase moves churn *before* it takes effect (pull-forward cancellations, plan downgrades) — contaminating the pre-period. Grandfathering creates selection: the exposed group is disproportionately newer, more marginal subscribers, so the ATT overstates what a universal increase would do.

## 6. Bottom line for your question

**Run a randomized price experiment at renewal as the primary design; use a staggered or geographic rollout analyzed with modern DiD as the fallback; use structural demand estimation as a complement, not a substitute.**

1. **Gold standard: randomized holdout at renewal.** Randomize renewing subscribers (or renewal cohorts) into the increase vs. a holdout at the old price. The estimand is the ITT of the increase on churn — clean, no parallel-trends assumption, and it directly answers the business question. Pre-register 30/60/90-day churn *and* 6-month net retention (churn minus win-back), because DellaVigna & Malmendier's lags mean the short window understates. Stratify randomization by tenure, plan (monthly/annual), and segment — Hoch et al. and DellaVigna & Gentzkow say the elasticity will differ, and you want those numbers, not one pooled average. Cluster or block by household where account sharing is detectable (SUTVA).
2. **If randomization is infeasible (fairness/PR constraints): phase the rollout and analyze it properly.** Roll out by region or by renewal cohort, keep a clean not-yet-treated control group, and estimate group-time ATTs à la Callaway & Sant'Anna (2021) or synthetic DiD (Arkhangelsky et al. 2021) — *not* a naive two-way fixed-effects regression, which is biased when effects differ across cohorts or over time. Show pre-trends, cluster standard errors at the level of treatment assignment (region/cohort), and allow an anticipation window around the announcement date.
3. **Exploit thresholds as RDDs where they exist.** Grandfathering cutoffs (tenure ≥ X keeps the old price), plan-tier boundaries, or intro-price expiries create quasi-random assignment near the cutoff — check the McCrary density test and covariate balance, and remember the estimand is local to the threshold.
4. **Use IV/structural only with real instruments.** With purely observational price variation, price is endogenous (you raise prices where demand is strong). A Hausman instrument — the same plan's price in other markets — or cost shifters can identify demand in a BLP/Nevo-style model; that buys you counterfactual simulation at any price point, but verify the exclusion narrative and cross-check against any experimental read.
5. **Randomize salience, not just price.** Per Ho et al., a loudly announced increase and a quietly applied one are different treatments. If you test, test the communication too — otherwise your elasticity is specific to one announcement regime and won't transport to the actual rollout.

**What would change the answer:** (a) whether you can randomize — if yes, everything else is secondary; (b) the churn window that matches your decision (short-run churn vs. long-run net retention — validate the proxy); (c) how much of the base is annual vs. monthly and how much account sharing exists (both reshape the estimand and the SUTVA story); (d) whether grandfathering is on the table (it creates selection that makes the ATT unrepresentative of a universal increase); (e) whether you need one number or segment-specific elasticities (the literature says: segment-specific).

## 7. Open threads

- **Downgrade vs. cancel:** the relevant substitution may be to a cheaper tier, not exit — is your outcome churn, downgrade, or revenue per subscriber? The BLP substitution logic says model all three margins.
- **Win-back and reactivation:** gross churn overstates net loss if the increase pushes out marginal subscribers who return on promotion — track net retention, not just gross churn.
- **Competitive response:** a unilateral increase vs. a market-wide increase are different counterfactuals; none of the designs above capture competitor repricing (general equilibrium).
- **Optimal rollout of the answer:** once you have segment elasticities, the pricing question becomes Ramsey-style — which segments to raise, by how much — which is a second measurement problem the same toolkit can address.
- **Long-run brand and trust effects:** repeated increases may erode goodwill in ways no single experiment captures; the trial literature's short horizons are the binding constraint everywhere.
