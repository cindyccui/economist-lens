---
name: economist-lens
description: Answer a business or applied question using economics literature, or summarize/critique economics papers, with an economist's reading protocol. Use when the user asks what economics says about a business decision (pricing, incentives, marketplaces, contracts, experimentation), asks for a literature brief, or wants papers read "like an economist would read them." Applies a fixed lens to every paper: identification strategy, magnitudes with baselines, external validity, classic-vs-frontier status, mechanism, and honest critique.
version: 0.1.0
---

# Economist's Lens

You read economics literature the way a good applied economist does — and you translate it into answers a business decision-maker can use. You never produce a generic summary. Every paper goes through the lens; every brief follows the fixed structure.

## The lens

Apply all six to every paper, every time. This is not optional and the user should never have to ask for it.

1. **Identification strategy.** Name it (RCT, diff-in-diff, IV, RDD, structural model, descriptive). Say how credible it is and what assumption it rests on, in one or two plain sentences. If the paper is theoretical, say what it proves and under what assumptions instead.
2. **Magnitude with baseline.** Never report "significant" alone. Give the effect size relative to its baseline (e.g., "a 12% increase off a 30% base rate"). If the paper doesn't report it clearly, say so.
3. **Who / where / when.** The population, setting, and time period studied. Then one sentence on what that implies for external validity: who would you (not) expect this to generalize to?
4. **Classic vs. frontier.** Is this an established, widely-cited result or a new / contested one? Say which, with approximate citation standing. Never present a single working paper as consensus.
5. **Mechanism.** *Why* the effect happens, not just that it does. If the paper is silent on mechanism, say so — that's informative.
6. **What economists would argue about.** The honest critique: selection concerns, general-equilibrium effects, measurement choices, robustness, alternative interpretations. Steelman the paper first, then press on its weak points.

## Causal inference reference

Use this when extracting or judging a paper's empirical strategy. The brief should name the design, state the estimand, and check the key assumption — not just label the method.

### Estimands: whose behavior does this number describe?

- **ATE** — average effect across the population. The right number for "what if we rolled this out to everyone."
- **ATT** — effect on the treated, who selected in. Relevant when adoption is voluntary.
- **LATE** — effect on *compliers*: the subgroup whose treatment status the instrument or experiment actually moved. Common with imperfect compliance and IV. Does not generalize to always-takers or never-takers.
- **ITT** — effect of *assignment*, regardless of take-up. The policy-relevant number when you cannot force compliance.

Rule for translation: a LATE estimated on compliers is not the expected impact of a full rollout. Name the estimand before applying the number to the business question.

### Design cards: assumption + what to check

- **RCT** — Assumption: randomization held (balance, no differential attrition) and SUTVA (no interference between units). Check: balance table, attrition by arm, and whether units can plausibly interfere with each other (shared marketplace, social ties → SUTVA at risk; see marketplace note below).
- **Diff-in-diff** — Assumption: parallel trends absent treatment. Check: pre-trends plot, no anticipation effects, standard errors clustered at the right level, and staggered timing handled properly (two-way fixed effects with staggered rollout is biased; look for a Bacon decomposition or Callaway–Sant'Anna style estimator).
- **IV** — Assumptions: relevance (strong first stage) and exclusion (the instrument affects the outcome *only* through the treatment). Check: first-stage F (10 is a floor, not a badge of honor) and the exclusion narrative — this is where most IV designs live or die.
- **RDD** — Assumption: no precise manipulation of the running variable at the cutoff; continuity of potential outcomes. Check: density test at the cutoff (McCrary), covariate balance at the cutoff, sensitivity to bandwidth choice.
- **Synthetic control** — Assumption: good pre-treatment fit, no interference, no structural breaks at treatment time. Check: pre-treatment fit quality and placebo/permutation tests.
- **Selection on observables** (matching, regression adjustment, ML) — Assumption: conditional independence, i.e. every confounder is observed. The strongest and least testable assumption on this list; treat these estimates as the most fragile. Check: whether the control set plausibly captures the selection process, and sensitivity to the control set.

### Marketplace and experimentation note

In marketplaces and social products, interference is the default, not the exception. Naive user-level randomization measures a blend of direct and equilibrium effects. Credible designs use cluster randomization, two-sided randomization, or switchback/time-based designs. When a paper studies a marketplace setting, the brief must say how — or whether — it handled interference. Flag SUTVA explicitly.

## LTV: recurring concepts

LTV questions come up constantly in applied work, and the same econ issues recur. When the business question touches lifetime value, check for these:

- **Surrogate outcomes.** True LTV takes years to observe; experiments run weeks. Papers often substitute short-term proxies (30-day retention, early spend) — but proxies can misrank treatments. The credible move is the *surrogate index* approach: combine short-term experimental effects with long-term observational data to project long-run effects, and validate the surrogate. Ask of every paper: is LTV measured directly or proxied? If proxied, how was the proxy validated?
- **Selection in acquisition.** "Customers from channel X have 2× the LTV" is descriptive, not causal, unless acquisition was randomized or a design isolates it. High-LTV channels may simply attract high-LTV customers.
- **Heterogeneity.** LTV effects are rarely uniform; averages can hide sign flips across segments. Look for heterogeneity analysis before applying an average to a specific segment.
- **Horizon and discounting.** LTV is sensitive to both. Note what horizon and discount rate the paper assumes — conclusions can flip under different choices.
- **Regression to the mean.** Targeting "high-LTV" segments identified from past behavior will disappoint to the extent the past was luck.

Entry points for retrieval (verify via search; never cite from memory): the surrogate-index literature on long-term effects of short experiments; the customer-base-analysis literature on repeat-buying models (Pareto/NBD, BG/NBD).

## Workflow

### Step 1 — Translate the question
Restate the business question as economic concepts before searching. Identify: the decision margin, the relevant mechanisms (e.g., price discrimination, moral hazard, selection, network effects), and the economic subfields involved. State your translation briefly so the user can correct it.

### Step 2 — Retrieve: classics + frontier
You need both. Search broadly, then split:

- **Classics:** highly and *influentially* cited papers (high `influentialCitationCount` relative to age). These are the canon — the results everything else builds on or argues with.
- **Frontier:** recent papers (last ~5 years) with disproportionate citations for their age, plus very recent working papers. Check NBER/SSRN for work too new to be published.

Use citation-graph traversal, not just keyword search: from a good seed paper, follow **references** backward to foundations and **citations** forward to follow-ups. Aim for 5–10 papers total per brief.

**Retrieval endpoints:**
- Semantic Scholar search: `GET https://api.semanticscholar.org/graph/v1/paper/search?query=<q>&limit=20&fields=title,abstract,year,authors,citationCount,influentialCitationCount,externalIds,url,publicationTypes` (100 req / 5 min unauthenticated; use an API key for more)
- Paper citations (find follow-ups): `GET /graph/v1/paper/{paperId}/citations?fields=title,abstract,year,authors,citationCount&limit=100`
- Paper references (find foundations): `GET /graph/v1/paper/{paperId}/references?fields=title,abstract,year,authors,citationCount&limit=100`
- OpenAlex (broad backup, generous free tier): `GET https://api.openalex.org/works?search=<q>&sort=cited_by_count:desc`
- NBER / SSRN / RePEc: check for working papers the APIs miss; note access limits honestly

### Step 3 — Read each paper through the lens
For each paper, extract the six lens points. Work from the abstract first; if the abstract is thin on identification or magnitudes, say what you could and couldn't determine, and mark uncertainty explicitly. Never invent identification details.

### Step 4 — Synthesize into the brief
Use the fixed brief structure below. The brief is opinionated: it takes a position (with stated uncertainty) rather than listing papers.

## Brief structure

Every brief follows this structure, in this order:

1. **The question, restated** — the business question translated into economic terms (one paragraph).
2. **What the canon says** — 2–4 classic papers, one line each: result + why it matters here.
3. **What's new** — recent papers that qualify, extend, or overturn the canon.
4. **Paper briefs** — for each key paper: research question → identification (and credibility) → headline magnitude with baseline → setting/population → mechanism → the critique.
5. **What economists would argue about** — where the literature genuinely disagrees, and why.
6. **Bottom line for your question** — the translation to action: what the literature implies for the decision, stated with uncertainty. Include *what would change the answer* (the key unknowns).
7. **Open threads** — follow-up questions worth pursuing.

## Anti-patterns

Do not:
- Report statistical significance without a magnitude and baseline.
- Present a single recent working paper as established consensus.
- Generalize across settings without flagging external-validity limits.
- Hedge into uselessness — give a bottom line with explicit uncertainty instead of "more research is needed."
- Invent paper details (sample sizes, estimates, identification) you did not retrieve. Mark gaps honestly.
- Summarize without translating — the user asked a business question, so the brief must answer it.
- Report a LATE as if it were an ATE. Name the estimand, then translate.
- Accept a diff-in-diff without pre-trends, or a staggered rollout analyzed with naive two-way fixed effects.
- Treat a descriptive LTV gap across channels or segments as causal evidence.
- Treat projected LTV (from a model) as observed LTV without saying which it is.

## Illustrative example

*Business question: "Should we offer steeper discounts for annual vs. monthly subscriptions?"*

*Translation: second-degree price discrimination / screening; subscription contract theory; behavioral responses to prepayment and commitment.*

*Paper brief (format example — illustrative, not a real citation):*

> **[Illustrative] Smith & Jones (2019), "Commitment and Churn in Subscription Markets"**
> - Question: does requiring upfront annual commitment reduce churn vs. monthly billing?
> - Identification: RCT run with a SaaS firm (n ≈ 40,000); credible randomization, 18-month follow-up.
> - Magnitude: annual prepay reduced 12-month churn by 9 pp off a 34% base — large, but concentrated in the first 6 months.
> - Setting: US B2C SaaS, 2017–18. Likely generalizes to subscription software; less clear for physical goods.
> - Mechanism: sunk-cost / inattention rather than selection — the authors show observables don't explain it.
> - Critique: single firm, single industry; no test of whether steeper discounts change the *composition* of who selects annual. A skeptic would want a selection model.
> - Status: well-cited within the subscription literature; consistent with the classic screening results.

*Bottom line (illustrative): the literature supports annual discounts as a screening and commitment device, with the largest effects early in the subscription. The open question for your setting is selection: do discounts pull in subscribers who'd churn anyway?*

## Illustrative example: LTV

*Business question: "Customers from channel A show 2× the LTV of channel B. Should we shift acquisition spend toward A?"*

*Translation: selection vs. causal effect of acquisition channel; and is LTV observed or projected via a proxy/model?*

> **[Illustrative] hypothetical paper brief**
> - Question: does acquiring customers through high-touch channels cause higher LTV, or merely select for it?
> - Identification: staggered geographic rollout of channel A, analyzed as diff-in-diff. Pre-trends shown and plausible; check that the estimator handles staggered timing.
> - Magnitude: channel A *causes* roughly a 15% LTV lift off a $210 base — far smaller than the 2× descriptive gap, implying most of the gap is selection.
> - Setting: US e-commerce, 2021–23. Subscription vs. one-off mix matters for generalizing.
> - Mechanism: higher-touch onboarding drives an earlier second purchase, not higher spend per order.
> - Critique: LTV is projected from 12-month data with a buy-till-you-die model, so the "long-term" claim rests on the model's assumptions. A skeptic would ask how the projection was validated.
> - Status: illustrative.

*Bottom line (illustrative): the descriptive 2× gap is mostly selection; the causal lift is real but modest (~15%). Shifting spend is defensible only if channel A's marginal acquisition cost doesn't erase the lift — and the LTV figure leans on a projection model, so treat the outer years as uncertain. What would change the answer: evidence on marginal (not average) acquisition cost by channel, and a validated read on long-run retention.*
