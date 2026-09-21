# Econ Literature Buddy — Product Spec (v0.1)

## One-liner
Ask a business question; get an answer grounded in economics literature — classic foundations and cutting-edge papers — with the econ nuance handled automatically.

## The problem
Standard AI tools *can* summarize econ papers, but only if you already know what to ask for. Out of the box they:
- Report statistical significance without magnitudes or baselines
- Don't distinguish ATE from LATE, or flag who the result actually applies to
- Treat one new working paper and a 30-year consensus result as equals
- Miss identification quality entirely — the thing economists care about most
- Need constant prompting and tweaking to produce an "economist's read"

The expertise required to get a good answer is the expertise the tool should have built in.

## Target user
People making business decisions who'd benefit from what economics knows: product/pricing/growth leaders, data scientists, and economists working on applied problems. (Start with marketplace & pricing — your home turf.)

## Core loop
1. User asks a business question in plain language.
   *"Should we offer steeper discounts for annual vs. monthly subscriptions?"*
2. Buddy maps it to the relevant economics: price discrimination, subscription/contract theory, behavioral responses to pricing.
3. Returns a brief built on real papers — classics *and* the recent frontier:
   - **What the canon says** (e.g., classic price discrimination results)
   - **What's new** (recent empirical work with new data/methods that qualifies or extends it)
   - **What it means for your question** (translation, not just summary)

## The "econ lens" — nuance by default
Your prompting expertise, compiled into the product's defaults. Every paper brief automatically includes:
1. **Identification strategy** — what it is, how credible, stated plainly
2. **Magnitude with context** — effect size relative to baseline, never just "significant"
3. **Who / where / when** — the population and setting; what that implies for external validity
4. **Classic vs. frontier** — is this established consensus or one new result?
5. **Mechanism** — *why* the effect happens, not just that it does
6. **What economists would argue about** — the honest critique: selection, GE effects, measurement, robustness

No tweaking required. This checklist *is* the product.

## V1 scope (keep it tight)
- Single-question flow: question in → structured brief out (5–10 papers)
- Paper briefs follow the econ-lens structure above
- Classic + frontier framing on every answer
- Follow-up questions ("what if our setting differs in X?")
- No accounts, no library management, no PDF upload in v1

## Data sources
- **Semantic Scholar API** (free) — papers, citations, influential-citation graph for finding both classics (highly cited) and frontier (recent, fast-accumulating cites)
- **OpenAlex / Crossref** — metadata backbone
- **RePEc / IDEAS, NBER, SSRN** — working papers where the frontier lives
- **arXiv econ** — quantitative/methodological edge
- EconLit is gated; skip for v1

## Tech sketch
- Retrieval over the above APIs (citation-graph-aware, not just keyword search)
- LLM synthesis constrained to the econ-lens brief structure
- Key design decision: the brief structure is fixed and opinionated — that's what makes it better than a chatbot

## Out of scope for v1
- PDF deep-reading / upload
- Personal library, alerts, or collaboration
- Covering all of economics — start with applied micro / IO / pricing / marketplaces

## Open questions
- How deep should the "economist's critique" go for a non-economist user?
- Business-question templates per domain (pricing, incentives, marketplace design)?
- What's the demo that makes someone say "I need this" — a side-by-side vs. ChatGPT on the same question?
