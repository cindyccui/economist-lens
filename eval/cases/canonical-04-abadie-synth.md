# Canonical case: policy shock in one market (synthetic control)

## Business question

"A new regulation hit just one of our regional markets. We only have aggregate market-level data — how do we estimate what would have happened without it?"

## Paper

Abadie, Alberto, Alexis Diamond, and Jens Hainmueller. "Synthetic Control Methods for Comparative Case Studies: Estimating the Effect of California's Tobacco Control Program." *Journal of the American Statistical Association* 105(490), 2010, 493–505.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** **Synthetic control.** California passed Proposition 99 (1988 tobacco tax + control program). Built a "synthetic California" as a weighted average of donor states matching pre-1988 cigarette sales and predictors. Identifying assumptions: good pre-treatment fit, **no interference** (donor states unaffected by CA's program), no other CA-specific shocks post-1988.

- **Estimand:** ATT for California — the effect of Prop 99 on CA cigarette sales vs. the synthetic counterfactual.

- **Headline magnitude + baseline:** By 2000, annual per-capita cigarette sales in California were about **26 packs lower** than synthetic California — a large drop relative to baseline sales (~60–70 packs per capita).

- **Setting / population:** US states, 1970–2000; outcome is tax-revenue-derived cigarette sales (a proxy for consumption).

- **Mechanism:** Tax increase + media/education campaign; the design doesn't separate the tax channel from the program channel.

- **Known threats / what economists argue about:** (1) Donor-pool contamination — states with their own tobacco programs must be excluded, or the counterfactual is biased. (2) **Interference/SUTVA**: cross-border sales and national anti-smoking trends. (3) Inference is via **placebo/permutation tests** (p ≈ 0.026), not standard errors — a common thing for AI to mangle. (4) Pre-treatment fit quality determines credibility; poor fit = unreliable.

- **Classic vs. frontier:** **Canon** for comparative case studies; the method is now standard, with frontier extensions (synthetic DiD — Arkhangelsky et al. 2021; matrix completion).

- **Traps for generic AI:** (1) Calling it DiD — it's a generalization with different assumptions and inference. (2) Reporting a standard error or t-stat — inference is placebo-based. (3) Ignoring the donor-pool exclusion choices, which drive the result.

## Expected retrieval

Abadie, Diamond & Hainmueller (2010) as the classic; Abadie & Gardeazabal (2003) as the precursor; Arkhangelsky et al. (2021) synthetic DiD as frontier.
