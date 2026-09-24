# Canonical case: measuring a cutoff-based policy (RDD)

## Business question

"We promote employees above a performance-score cutoff. How do we measure the causal effect of promotion itself on future performance?"

## Paper

Lee, David S. "Randomized Experiments from Non-random Selection in U.S. House Elections." *Journal of Econometrics* 142(2), 2008, 675–97.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** **Regression discontinuity.** Candidates who barely win an election (50%+ε vote share) are compared to those who barely lose (50%−ε) — near the cutoff, victory is "as good as random." Identifying assumptions: **no precise manipulation** of the running variable at the cutoff (McCrary density test logic), continuity of potential outcomes.

- **Estimand:** **LATE at the cutoff** — the incumbency advantage *for candidates in close elections*. Lee is explicit that this need not generalize to safe seats: the paper's lasting methodological point is that quasi-experiments buy internal validity at the cost of a *local* estimand.

- **Headline magnitude + baseline:** Barely winning raises the party's next-election vote share by about **8 percentage points** (the discontinuity jump).

- **Setting / population:** US House elections, 1946–1998.

- **Mechanism:** Name recognition, fundraising advantage, deterrence of challengers — discussed, not separately identified.

- **Known threats / what economists argue about:** (1) **External validity of the local estimand** — the paper itself stresses the LATE-at-cutoff point; later work (e.g., Hall & Snyder on scare-off) probes mechanisms. (2) Sorting/manipulation at the cutoff (less plausible in elections, very plausible in firm promotion cutoffs — a good business caveat). (3) Bandwidth and specification sensitivity in RDD generally.

- **Classic vs. frontier:** **Canon** — the paper that made RDD a standard tool in applied micro and the standard citation for "quasi-experimental variation as good as random near a cutoff."

- **Traps for generic AI:** (1) Presenting the 8pp as the incumbency advantage *in general* rather than at the cutoff. (2) Missing the no-manipulation assumption — which is the first thing to check in a business promotion-cutoff setting. (3) Confusing the LATE-at-cutoff with an ATE.

## Expected retrieval

Lee (2008) as the classic; McCrary (2008) density test and Imbens & Lemieux (2008) / Lee & Lemieux (2010) practical guidance as complements.
