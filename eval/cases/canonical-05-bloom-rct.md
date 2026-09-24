# Canonical case: remote work (RCT with volunteer selection)

## Business question

"Should we let employees work from home? Will productivity collapse?"

## Paper

Bloom, Nicholas, James Liang, John Roberts, and Zhichun Jenny Ying. "Does Working from Home Work? Evidence from a Chinese Experiment." *Quarterly Journal of Economics* 130(1), 2015, 165–218.

> **DRAFT — canonical paper; ground truth is textbook consensus. For Cindy to review/adjust.**

## Ground truth

- **Design / method:** **RCT** at Ctrip (16,000-employee Chinese travel agency). Call-center employees who **volunteered** for WFH were randomized by even/odd birthday into home vs. office for 9 months. Randomization among volunteers identifies the causal effect cleanly *for volunteers*.

- **Estimand:** ATE **among volunteers** (effectively a TOT for the self-selected interested population) — not the ATE for all employees. This distinction is the whole external-validity story.

- **Headline magnitude + baseline:** **+13% performance** for home workers: ~9pp from more minutes worked per shift (fewer breaks/sick days), ~4pp from more calls per minute (quieter environment). **Attrition halved.** But **promotion rates conditional on performance fell ~50%**. Firm estimated savings of ~$2,000/employee/year (performance + office costs + attrition).

- **Setting / population:** Chinese call-center workers, 2010–11; individual, easily-monitored output; volunteers with home workspace and tenure.

- **Mechanism:** Fewer distractions/interruptions + fewer sick days (no commute on marginal days) → more effective minutes; isolation → lower promotion visibility.

- **Known threats / what economists argue about:** (1) **Volunteer selection**: after the experiment, when everyone could choose, gains nearly **doubled to 22%** — the RCT estimand understated the policy-relevant effect because of self-selection on gains. (2) Hawthorne effects. (3) No spillovers found (checked against the Nan Tong call center), but team-production settings could differ. (4) Generalizability: call centers ≠ creative/collaborative work; China 2010 ≠ everywhere.

- **Classic vs. frontier:** **Canon** for RCTs in firms; heavily cited in the post-Covid remote-work debate (where later work finds more mixed/negative selection effects — good "what economists argue about").

- **Traps for generic AI:** (1) "WFH raises productivity 13%" without the volunteer qualifier — the headline every manager misuses. (2) Missing the promotion-rate downside. (3) Missing that self-selection *increased* the gains (selection on gains, not just bias).

## Expected retrieval

Bloom et al. (2015) as the classic; post-2020 remote-work RCTs (e.g., Bloom, Han & Liang 2024 on hybrid) as frontier/comparison.
