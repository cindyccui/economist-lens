# Canonical IO case: willingness to pay from market data (structural demand)

## Business question

"How should we price our new product? What are customers actually willing to pay, and how will demand respond?"

## Paper

Berry, Steven, James Levinsohn, and Ariel Pakes. "Automobile Prices in Market Equilibrium." *Econometrica* 63(4), 1995, 841–90.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** **Structural demand estimation** — random-coefficients logit (the "BLP" model). Recovers the full demand system from market-level data (prices, quantities, product characteristics). The core econometric problem it solves: **price is endogenous** (firms observe demand shocks the econometrician doesn't and set prices accordingly), so it instruments for price using **cost shifters** and sums of characteristics of rival products ("BLP instruments").

- **Estimand:** The distribution of consumer preferences / willingness to pay — price elasticities, substitution patterns, and markups for each product, plus welfare effects of product introductions (e.g., the minivan).

- **Headline magnitude + baseline:** No single headline number — the output is a demand system: own- and cross-price elasticities, implied markups, and dollar-valued consumer surplus from new goods. The paper's result *is* the credible measurement apparatus.

- **Setting / population:** US automobile market; market-level (not individual) data.

- **Mechanism:** Heterogeneous consumer tastes (random coefficients) generate realistic substitution — a price hike on one car diverts demand to *similar* cars, not proportionally to all cars (the failing of plain logit).

- **Known threats / what economists argue about:** (1) Instrument validity — the exclusion restriction on BLP instruments is debated; weak instruments in demand (see Armstrong 2016). (2) Functional-form and distributional assumptions do real work. (3) Supply-side modeling (Bertrand-Nash pricing) needed to get from demand to markups. (4) Frontier: modern demand estimation with microdata, machine learning, and credible experimental price variation as complements.

- **Classic vs. frontier:** **Canon.** The standard reference for "how economists estimate willingness to pay and elasticities from market data." Any pricing brief that estimates demand from observational price–quantity correlations without addressing endogeneity fails against this benchmark.

- **Traps for generic AI:** (1) Treating observed price–quantity correlations as demand curves — the endogeneity point is the entire paper. (2) Presenting WTP as a single number rather than a distribution over heterogeneous consumers. (3) Missing that instruments are the identifying assumption. (4) Confusing stated-preference (surveys/conjoint) with revealed-preference estimation.

## Expected retrieval

Berry, Levinsohn & Pakes (1995) as the classic; Berry (1994) as the precursor; Nevo (2001) as the applied follow-on; Conlon & Mortimer (2021, "Empirical Properties of Diversion Ratios") or similar as frontier.
