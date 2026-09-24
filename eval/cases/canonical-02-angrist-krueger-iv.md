# Canonical case: returns to schooling (IV / LATE)

## Business question

"Should we require a college degree for this role — what's the causal return to an extra year of schooling for our applicant pool?"

## Paper

Angrist, Joshua D., and Alan B. Krueger. "Does Compulsory School Attendance Affect Schooling and Earnings?" *Quarterly Journal of Economics* 106(4), 1991, 979–1014.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** Instrumental variables. Quarter of birth instruments for years of schooling: compulsory-schooling laws let students born early in the year drop out with less schooling than those born later. Key assumptions: **relevance** (quarter of birth predicts schooling), **exclusion** (quarter of birth affects earnings only through schooling), **monotonicity** (no defiers).

- **Estimand:** **LATE** — the return to schooling for *compliers*: students whose schooling was actually shifted by compulsory-attendance laws (mostly would-be early dropouts). This is the canonical example of an IV estimate being a LATE, formalized later by Imbens & Angrist (1994).

- **Headline magnitude + baseline:** Roughly **7% higher earnings per additional year of schooling** (estimates in the 0.06–0.10 range across specifications), close to OLS — which was itself a notable finding.

- **Setting / population:** US men, Census data (1930–39 birth cohorts); compliers are marginal students at the dropout margin — not college graduates.

- **Mechanism:** Human capital vs. signaling is *not* resolved by this design; the paper identifies the earnings return, not the channel.

- **Known threats / what economists argue about:** (1) **Bound, Jaeger & Baker (1995):** the instrument is *weak* — quarter of birth explains little schooling variation, so 2SLS can be badly biased toward OLS; this paper launched the weak-instruments literature. (2) Exclusion: season of birth correlates with family background/health (later literature). (3) The LATE is for dropouts at the margin — it does not answer "the return to college for our applicants."

- **Classic vs. frontier:** **Canon.** The paper that made IV/LATE central to applied micro. Any brief touching IV that doesn't name the estimand as LATE fails the skill's own standard.

- **Traps for generic AI:** (1) Reporting "7% return to schooling" as the ATE for everyone — it is a LATE for compliers at the dropout margin. (2) Missing the weak-instrument critique. (3) Using it to justify a college-degree requirement (wrong population, wrong margin).

## Expected retrieval

Angrist & Krueger (1991) as the classic; Imbens & Angrist (1994) for LATE; Bound, Jaeger & Baker (1995) for weak IV.
