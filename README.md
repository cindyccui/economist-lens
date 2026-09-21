# economist-lens

An agent skill that answers business questions with economics literature — read the way an economist would read it.

**Status:** early draft / work in progress.

## What it is

Standard AI tools can summarize econ papers, but only if you already know what to ask for: check the identification strategy, report magnitudes with baselines (not just significance), separate canon from frontier, flag external validity. `economist-lens` compiles that expertise into the skill's defaults — a fixed six-point "econ lens" applied to every paper, every time, with no prompting or tweaking required.

## Layout

- `SKILL.md` — the skill: the lens, causal-inference reference, LTV notes, workflow, retrieval guide, brief template
- `spec.md` — product spec and positioning notes
- `eval/` — evaluation harness: scoring rubric, golden cases, adversarial cases, results log

## Evaluation

See `eval/README.md`. Pick a case, run the skill in a fresh session, score it with `eval/rubric.md`, log the run in `eval/results.md`.
