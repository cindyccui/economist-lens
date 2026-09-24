# Canonical case: minimum wage and employment (DiD)

## Business question

"We're expanding into markets with different minimum wages. How will a wage floor affect our staffing levels and labor costs?"

## Paper

Card, David, and Alan B. Krueger. "Minimum Wages and Employment: A Case Study of the Fast-Food Industry in New Jersey and Pennsylvania." *American Economic Review* 84(4), 1994, 772–93.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** Difference-in-differences. New Jersey raised its minimum wage ($4.25 → $5.05, April 1992); Pennsylvania did not. Surveyed fast-food restaurants in both states before and after. Identifying assumption: parallel trends — NJ and PA employment would have evolved similarly absent the hike.

- **Estimand:** ATT — the effect of the minimum-wage increase on fast-food employment in New Jersey.

- **Headline magnitude + baseline:** Found **no employment decrease** in NJ relative to PA; point estimates slightly positive. (The famous null/positive result that launched the modern minimum-wage literature.)

- **Setting / population:** Fast-food restaurants in NJ and PA, 1992; surveyed employment counts (not admin data).

- **Mechanism:** Paper is largely reduced-form; candidate mechanisms discussed in the literature: monopsony power, efficiency wages, price pass-through, non-compliance. The paper itself doesn't pin one down.

- **Known threats / what economists argue about:** (1) **Neumark & Wascher (2000)** re-did it with BLS payroll data and found negative employment effects — a data-and-methods duel that ran for years. (2) Survey vs. administrative data quality. (3) Short-run vs. long-run effects. (4) External validity: fast food in 1992 ≠ all low-wage labor markets; the literature has since moved to border-discontinuity designs (Dube, Lester & Reich 2010) and the consensus is contested-to-modest-negative.

- **Classic vs. frontier:** **Canon.** The founding paper of the modern empirical minimum-wage literature and a landmark DiD application. Any brief on minimum wages that doesn't cite it has a retrieval failure.

- **Traps for generic AI:** (1) Presenting "no disemployment effect" as settled consensus — the literature is genuinely contested (Neumark & Wascher; later meta-analyses). (2) Missing the parallel-trends assumption. (3) Generalizing from fast food to all affected workers.

## Expected retrieval

Card & Krueger (1994) as the classic; Neumark & Wascher (2000) as the counterpoint; Dube, Lester & Reich (2010) and/or Cengiz et al. (2019) as frontier.
