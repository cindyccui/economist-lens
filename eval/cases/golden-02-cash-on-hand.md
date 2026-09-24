# Golden case: cash on hand and credit demand

## Business question

"Should we expand credit / BNPL access to cash-constrained customers? What does the evidence say about cash on hand and demand for credit?"

## Paper (ground truth — you wrote it)

Cui, Can. "Cash-on-hand and demand for credit." *Empirical Economics* 52(3), 2017, 1007–1039. (Single-authored.)

## Ground truth

- **Design / method:** Quasi-experimental border design. Identification comes from variation in **state EITC generosity** across state borders **within the same commuting zones** — i.e., comparing payday-loan demand in areas that share a local labor market but sit on opposite sides of a state line with different EITC benefit levels. The commuting-zone fixed effect absorbs local economic conditions; the remaining variation in EITC generosity is treated as idiosyncratic policy variation. (Reduced-form; not structural.)

- **Estimand:** The causal effect of tax-rebate-like income (state EITC benefits) on the **demand** for small-dollar credit. Headline: a **$100 increase in EITC benefits → 8.3% fewer loan applications and 6.6% fewer borrowers**. Framed as income sensitivity of credit demand among subprime consumers — a test of liquidity constraints / consumption-smoothing frictions.

- **Headline magnitude + baseline:** $100 more in EITC benefits → −8.3% loan applications, −6.6% borrowers. (Baseline application/borrower counts: TODO — verify from the paper's tables.) The paper notes this translates into sizable reductions in loan volume and savings in finance charges.

- **Setting / population:** US subprime consumers using small-dollar credit (payday loans); proprietary loan-level dataset from a payday lender. EITC-eligible population = low-income working families. (Sample period and lender coverage: TODO — verify.)

- **Mechanism:** Cash on hand **substitutes** for high-cost borrowing: when liquidity-constrained households receive a lump-sum income boost, they borrow less at very high rates. Broader read: public income-benefit programs aid consumption smoothing in the presence of credit-market frictions. Note the outcome is *demand* (applications), so the mechanism runs through borrower behavior, not lender supply.

- **Known threats — what the referees pushed on:** (1) **EITC generosity correlates with other state policies** — states with generous EITCs may also regulate payday lending more strictly, have higher minimum wages, or more generous Medicaid; the border design handles local conditions but not state-level policy bundles. (2) **Single-lender data** — external validity to the whole small-dollar credit market. (3) **Applications vs. originations** — demand is measured as applications; equilibrium borrowing also reflects lender approval. (4) **EITC is anticipated** (annual lump sum at tax time), so the margin is cash-on-hand *timing*, not a permanent-income shock — the interpretation as liquidity constraints is exactly the point, but it bounds generalization. (5) Sorting across the border (borrowers crossing state lines for loans).

- **Classic vs. frontier:** Sits at the intersection of two literatures. Consumption-smoothing / fiscal-rebate canon: Agarwal–Liu–Souleles (2007), Parker–Souleles–Johnson–McClelland (2013), Gross–Notowidigdo–Wang (2014) on liquidity constraints and bankruptcy. Payday-lending literature: Melzer (2011 QJE), Bertrand & Morse (2009, "What Do High-Interest Borrowers Do with Their Tax Rebate?"), Skiba (2014) on tax rebates and payday borrowing cycles. Closest analogs are Bertrand & Morse (2009) and Skiba (2014) — same question (rebates → payday borrowing), different identification. Contribution: a *causal* estimate of income sensitivity of credit demand using policy variation rather than rebate timing.

- **Traps for generic AI:** (1) Reporting the 8.3%/6.6% as the effect of "giving people money" in general — it's specifically EITC-benefit variation at state borders among subprime payday borrowers. (2) Confusing applications (demand) with loan volume (equilibrium). (3) Missing the border-design logic and treating it as a simple cross-state comparison. (4) Overclaiming for BNPL policy — 2017 payday borrowers ≠ BNPL users; the mechanism (liquidity constraints) travels, the magnitudes may not.

## Expected retrieval

Bertrand & Morse (2009); Melzer (2011); Gross–Notowidigdo–Wang (2014); Skiba (2014); Agarwal–Liu–Souleles (2007). Frontier: recent BNPL / fintech small-dollar credit work.
