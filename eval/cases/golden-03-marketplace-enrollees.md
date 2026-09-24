# Golden case: marketplace enrollee composition

## Business question

"As our marketplace matures, how should we expect participant composition to evolve — and what does that imply for pricing and risk?"

## Paper (ground truth — you co-authored it)

Donohue, Julie M., Eros Papademetriou, Rochelle R. Henderson, Sharon Glave Frazee, Christine Eibner, Andrew W. Mulcahy, Ateev Mehrotra, Shivum Bharill, **Can Cui**, Bradley D. Stein, and Walid F. Gellad. "Early Marketplace Enrollees Were Older and Used More Medication Than Later Enrollees; Marketplaces Pooled Risk." *Health Affairs* 34(6), 2015, 1049–56.

> **DRAFT — written by Ace from the published abstract and press coverage. For Cindy to verify, correct, and sharpen — especially design details, magnitudes, and the "marketplaces pooled risk" interpretation.**

## Ground truth

- **Design / method:** **Descriptive — no causal identification.** Cross-sectional comparisons using pharmacy claims: (1) early vs. late marketplace enrollees, (2) all marketplace enrollees vs. an employer-sponsored insurance comparison group. Medication use is used as an early proxy for health status / risk. This case is deliberately a *descriptive* paper: the skill must describe it accurately without inventing a design.

- **Estimand:** N/A (descriptive). Reported contrasts: differences in age, average drug spending, and likelihood of using specific medication classes between early and late enrollees, and between marketplace and employer-sponsored enrollees.

- **Headline magnitude + baseline:** Among >1M Express Scripts marketplace enrollees (Jan–Sep 2014): early enrollees (Oct 2013–Feb 2014) were **older and used more medication** than later enrollees. Overall, marketplace enrollees had **lower average drug spending** and were **less likely to use most medication classes** than the employer-sponsored comparison group — **except** hepatitis C and HIV medications, where marketplace enrollees were *more* likely to use them (particularly HIV). (Exact figures: TODO — verify from the paper's tables.)

- **Setting / population:** First-year ACA marketplace enrollees (2014), >1 million people in Express Scripts (largest US pharmacy benefit manager) claims data, Jan–Sep 2014. Comparison group: employer-sponsored enrollees in the same data. Context: 7.3M Americans enrolled via ACA marketplaces in 2014; essentially nothing was known about the health status of the new risk pool.

- **Mechanism:** Selection into *timing* of enrollment: people with greater health needs (older, more medication use) had more to gain and enrolled first — pent-up demand / adverse selection on the enrollment margin. At the market level, though, the pool looked *healthier* than the previously insured on drug spending ("marketplaces pooled risk") — with risk concentrated in specific high-cost conditions (HIV, hepatitis C), plausibly reflecting previously uninsured people gaining access to expensive specialty drugs.

- **Known threats — what the referees pushed on:** [INFERRED — Cindy to confirm/correct] Likely pressure points: (1) **Medication use ≠ health status** — it's a proxy, affected by access and benefit design, not just need. (2) **Observation-window confounding** — early enrollees are observed for more months (Jan–Sep window), mechanically inflating their measured medication use vs. late enrollees. (3) **Express Scripts ≠ all marketplace enrollees** — selection into the PBM's data. (4) **Employer-sponsored comparison** — the two populations differ on age, income, and employment by construction. (5) Descriptive only: can't separate pent-up demand from selection, or say what the *next* year's pool will look like.

- **Classic vs. frontier:** Early ACA-evaluation literature — one of the first empirical looks at the actual risk pool of the 2014 marketplaces, published while the ink was still wet (June 2015). Descriptive but influential; it spoke directly to the live policy fear of marketplace adverse-selection death spirals. Related canon: the ACA adverse-selection / mandate literature (e.g., Hackmann–Kolstad–Kowalski 2015; Kowalski on the individual mandate). Frontier-at-the-time; now a historical baseline for later marketplace risk-pool studies.

- **Traps for generic AI:** (1) **Inventing a causal claim** — there is no design here; "early enrollees were sicker" must not become "enrolling early *causes* higher spending." (2) **Missing the observation-window confound** (early enrollees mechanically observed longer). (3) Overclaiming "no adverse selection" — the finding is about *drug spending* in year one, not the full risk profile, and HIV/hep C use ran the other way. (4) Getting authorship wrong — Donohue is lead author; Cui is a middle co-author (RAND). (5) Treating a 2015 descriptive snapshot as current evidence about today's marketplaces.

## Expected retrieval

TODO (suggestions to confirm): ACA marketplace adverse-selection literature — Hackmann–Kolstad–Kowalski (2015); Kowalski (2014) on the mandate; later marketplace risk-pool / risk-adjustment studies as frontier.
