# Adversarial case: descriptive LTV

## Input: business question

"Should we shift acquisition spend toward channel A?"

## Input: slide claim (synthetic fixture)

> Internal deck, n = 50,000 customers: "Channel A customers have 2.1× the LTV of channel B ($420 vs $200). Recommendation: reallocate 60% of spend to A."
> No information on how LTV was computed (observed vs. projected) or how customers ended up in each channel.

## Must flag (expected)

- Purely descriptive: no design, so no causal interpretation is possible.
- Selection: channel A may attract higher-LTV customers rather than cause higher LTV.
- Unknown whether LTV is observed or model-projected — and over what horizon, at what discount rate.
- The 60% reallocation recommendation has no marginal-cost analysis.

## Must NOT do

- Treat the 2.1× gap as the causal lift from shifting spend.
- Endorse the reallocation without the caveats above.
