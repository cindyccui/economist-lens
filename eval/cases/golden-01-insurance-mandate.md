# Golden case: insurance mandate rationale

## Business / policy question

"We run a voluntary marketplace and worry about adverse selection unraveling participation. Do we need a mandate or penalty to keep the market stable — and what's the economic rationale?"

## Paper (ground truth — you wrote it)

Cabral, Marika, Can Cui, and Michael Dworsky. "The Demand for Insurance and Rationale for a Mandate: Evidence from Workers' Compensation Insurance." *American Economic Review* 112(5), 2022, 1621–68. (NBER WP 26103.)


## Ground truth

- **Design / method:** Reduced-form difference-in-differences plus a sufficient-statistics welfare analysis (Einav–Finkelstein–Cullen style). Demand is estimated by exploiting idiosyncratic regulatory updates to relative premiums across industry-occupation classifications ("class codes") in Texas — the government sets relative premiums, and periodic updates create large within-class premium shocks (mean absolute update 9.3%, IQR 15.3%). Event-study DiD; robustness via more flexible controls and nonlinearities in the update algorithm. The welfare half traces out demand and (risk-adjusted) cost curves and computes counterfactuals (status quo vs. competitive optimum vs. mandate vs. subsidy).

- **Estimand:** (1) The price elasticity of demand for workers' compensation coverage: ≈ **-0.3** (a 1% premium increase → ~0.3% decline in coverage), precisely estimated. (2) A selection test: the slope of the insurer average-cost curve in quantity insured (EFC logic) — statistically zero. (3) Welfare counterfactuals in $ per $100 of risk-adjusted payroll, scaled to $/worker/year and % of mean premiums.

- **Headline magnitude + baseline:** Demand elasticity ≈ -0.3. No evidence of adverse selection: implied welfare cost of selection ≈ $0.001 per $100 of risk-adjusted payroll (0.04% of mean premiums), 95% CI rules out anything above $0.24 per $100 (10.9% of mean premiums). Market power: moving to the perfectly competitive optimum gains only ~$3.91/worker/year (0.4% of mean premiums). A mandate would *reduce* welfare by ~$100–206/worker/year (9.1–18.8% of mean premiums, depending on linear vs. constant-elasticity demand). A tax-funded subsidy to reach the optimum (25% marginal DWL of taxation) would reduce welfare by ~$26/worker/year.

- **Setting / population:** Texas workers' compensation insurance, 2006–2011, administrative data from the Texas Department of Insurance. Texas is the only state without a coverage mandate (employers choose; the outside option is tort exposure). ~$257B in covered payroll/year ≈ 74% of Texas private-industry payroll. Policy-relevant: several states (OK, TN, FL, SC, AR) have debated repealing mandates for a Texas-style voluntary system.

- **Mechanism:** The paper tests *justifications* rather than a single causal mechanism. Key economic logic: (a) demand is price-sensitive because employers weigh premiums against the outside option; (b) the *absence* of adverse selection is attributed to heavy risk adjustment — industry-occupation class rating plus experience rating leave little scope for private information (unlike individual health insurance or annuities); (c) the welfare result is that some workers are *efficiently* uninsured (willingness to pay below cost), so forcing them in destroys surplus.

- **Known threats — what the referees pushed on:** (1) the revealed-preference interpretation of demand — the employer buys, but welfare is employer+employee surplus; assumes employers/employees accurately value coverage vs. the tort outside option (behavioral biases or misinformation would break this); (2) external validity — Texas is unusual (tort exposure, no mandate history); (3) the selection test extrapolates from claim-cost data assuming insurer costs are proportional to claim costs; (4) partial-equilibrium welfare analysis holding product attributes and the tort system fixed; (5) sensitivity of the mandate-loss number to demand extrapolation ($206 linear vs. $100 constant-elasticity). The paper's Section 4.3 explicitly discusses which conclusions survive relaxing the demand interpretation.

- **Classic vs. frontier:** Method is the Einav-Finkelstein-Cullen sufficient-statistics framework for selection and welfare in insurance markets. The application is frontier-as-of-2022: first paper to investigate adverse selection and the efficiency consequences of government intervention in workers' compensation; one of few to do it in a large, policy-relevant market rather than a single employer/insurer. Closest analog: Hackmann–Kolstad–Kowalski (2015) on the MA individual mandate.

- **Traps for generic AI:** (1) "Mandates are bad" — the claim is narrower: *classic market-failure rationales* (adverse selection, market power, externalities) don't justify a mandate *in this setting*; the paper explicitly leaves open behavioral-bias and labor-market-friction justifications and does not compare a mandate to having no workers' comp system at all. (2) "No adverse selection" ≠ "this market works fine" — it's specific to a heavily risk-adjusted market; don't generalize to health insurance. (3) The employer is the purchaser — demand is not worker demand, and the welfare interpretation hinges on that assumption. (4) Don't cite this as evidence about the ACA individual mandate — different product, different outside option, different selection environment.

## Expected retrieval

classic papers: EFC 2010; Einav & Finkelstein 2011 handbook; HKK 2015. 
