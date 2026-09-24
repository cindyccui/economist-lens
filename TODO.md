# TODO

## Economist-lens skill

- [ ] Review Ace's draft golden-case ground truth: `eval/cases/golden-01-insurance-mandate.md`
      (design, estimand, magnitudes, setting, mechanism, what referees pushed on, traps)
- [ ] Review Ace's draft golden-case ground truth: `eval/cases/golden-02-cash-on-hand.md`
- [ ] Review Ace's draft golden-case ground truth: `eval/cases/golden-03-marketplace-enrollees.md`
- [ ] Review Ace's 8 draft canonical cases (`eval/cases/canonical-01` through `canonical-08`):
      Card & Krueger (DiD), Angrist & Krueger (IV/LATE), LaLonde (selection),
      Abadie et al. (synthetic control), Bloom et al. (RCT), Lee (RDD),
      BLP (structural demand/WTP), Allcott (nudge vs. price) — veto or swap any paper
- [x] Run the 4 adversarial cases: `eval/cases/adversarial-01-late-as-ate.md`,
      `adversarial-02-did-pitfalls.md`, `adversarial-03-descriptive-ltv.md`,
      `adversarial-04-working-paper-hype.md` — no prep needed;
      score with `eval/rubric.md`, log in `eval/results.md`
      (done 2026-09-24: all four scored 20/21; sole deduction was Magnitude
      because each vignette withheld baselines, honestly flagged each time)
- [x] Iterate on the `SKILL.md` draft — react to open decisions (name, structure, examples)
      (done 2026-09-24: added ITT back-out rule — LATE × first-stage gap —
      driven by adversarial-01; structure validated by 4/4 runs; name kept)
- [x] Run blind A/B: skill-equipped agent vs. vanilla agent on the same business
      question; log winner and reasons in `eval/results.md`
      (done 2026-09-24, two rounds: round 1 pick VOIDED — Cindy clicked before
      reading; round 2 on a causal-measurement question: **vanilla won** —
      Brief D preferred for brevity; feedback: lead with key metric, success
      criteria, tradeoff framework; drop the word "canon"; skill brief felt
      comprehensive but hard to grasp)
- [x] Iterate on `SKILL.md` from A/B feedback → v0.2.0 (done 2026-09-24):
      decision vs. measurement brief modes; answer-first structure;
      key metric / success criteria / tradeoff framework up front;
      3–6 condensed paper notes instead of 5–10 full briefs;
      "canon" replaced with "established research"; rubric updated to match
- [ ] Re-run blind A/B with the v0.2.1 skill vs. vanilla on a fresh question
      (decision-mode this time) to test whether the rewrite closes the gap

## Website

- [ ] Replace the "coming soon" projects placeholder with real projects
      (economist-lens can be the first project card) — `~/workspace/personal-website/index.html`
