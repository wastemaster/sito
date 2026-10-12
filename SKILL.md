---
name: sito
description: A verification-first workflow for difficult research, engineering, analysis, debugging, and decision-making tasks. Use when a plausible answer is not enough and the work should reduce uncertainty through prior-evidence review, calibration, precommitted expectations, minimal intervention, blind criticism, cross-method checks, independence analysis, entropy accounting, archival, and handoff testing. Use the full SITO pass for high-stakes or ambiguous work; use the light pass when speed matters.
---

# SITO

Apply a verification-first workflow whose goal is not merely to produce an answer, but to leave the problem space more constrained, testable, and reusable than it was before.

## Modes

- **SITO**: run all 11 roles in order.
- **sito**: run the light pass: Prior Evidence -> Calibration -> Precommitment -> Blind Critic -> Entropy Balance.

Treat the user's capitalization as the mode selector when they explicitly invoke `SITO` or `sito`.

## Full workflow

### 1. Prior Evidence
Before deriving a new answer, inspect existing evidence that could already constrain it: source data, documentation, code, logs, prior decisions, experiments, issue history, version control, research, and relevant conversation context.

Do not start from a fresh theory when a published or recorded answer may already exist.

### 2. Calibration
Validate the measurement, heuristic, test, benchmark, or decision rule before applying it to the unknown case.

Use at least:
- one known positive case;
- one known negative case.

If the measure cannot distinguish them, treat the measure as broken and do not trust downstream results.

### 3. Precommitment
Before observing the result, record:
- the expected outcome;
- the metric or observable fact;
- the success/failure threshold.

Place thresholds next to a relevant baseline from the same population whenever possible. Do not invent an isolated target without context.

### 4. Minimal Intervention
Make the smallest change sufficient to test the hypothesis.

Prefer changes that are:
- additive;
- reversible;
- isolated from unrelated behavior.

When applicable, verify that the relevant test fails without the change and passes with it.

### 5. Blind Critic
Run criticism in two passes.

First, blind pass: present the result without revealing the favored hypothesis and ask what is wrong, missing, inconsistent, or weak.

Second, targeted pass: attack the specific hypothesis or suspected failure mode.

Keep blind findings separate from prompted findings.

### 6. Naive Examiner
Test the result as a literal reader or operator who does not know the author's intent.

Where practical, include hidden cases with known answers. Use them to measure the examiner as well as the artifact being examined.

A reviewer who cannot detect planted failures is not a reliable reviewer for the unknown cases.

### 7. Outsider Check
Repeat the key check using a materially different method, implementation, model family, toolchain, team, or reasoning path.

If an independent route is temporarily unavailable:
- mark the result as single-family or single-method evidence;
- queue the independent recheck;
- do not automatically block the task unless independence is essential to the user's decision.

### 8. Independence Check
For every corroborating witness, record what it shares with the primary method:
- source data;
- code;
- prompts or instructions;
- assumptions;
- model family;
- implementation;
- upstream derived artifacts.

Shared dependencies reduce independence. Two correlated witnesses do not count as two independent confirmations.

### 9. Entropy Balance
Estimate whether the work reduced or increased system complexity.

Count or otherwise make explicit the change in things such as:
- unresolved questions;
- rules and exceptions;
- documents;
- lines or modules of code;
- TODOs and errata;
- monitoring or guardrails;
- manual steps;
- duplicated sources of truth.

Prefer net entropy <= 0. If entropy increases, name the value purchased by that increase and make the trade explicit.

### 10. Archive
Preserve only the reusable evidence needed to reproduce or continue the work:
- inputs;
- precommitted expectation;
- observed result;
- failed predictions;
- calibration cases;
- disagreements;
- final verdict.

Move closed items out of the active work surface where the environment supports it. Update the project's canonical status or source of truth.

Do not archive the full stream of thought when a compact evidence record is sufficient.

### 11. Newcomer Test
Give the final artifact to a reader who has none of the working history.

The artifact passes only if that reader can determine:
- what is established;
- what remains uncertain;
- what evidence supports the conclusion;
- what to do next.

If continuation requires reconstructing the hidden work log, the handoff is incomplete.

## Core rules

1. Evidence before theory.
2. Calibration before measurement.
3. Prediction before observation.
4. A control must be capable of failing.
5. Run blind criticism before targeted criticism.
6. Test the reviewer, not only the reviewed artifact.
7. Correlated witnesses are not independent witnesses.
8. Do not resolve conflicting witnesses by simple majority. Preserve the disagreement as a finding until its cause is understood or explicitly bounded.
9. Every increase in complexity must buy explicit value.
10. Work is not finished when the author understands it; it is finished when a newcomer can continue from the final artifact.

## Output format

Keep the final report compact. Use one table:

| Role | Prediction / question | Observed fact | Verdict |
|---|---|---|---|
| Prior Evidence | ... | ... | PASS / WARN / FAIL |
| Calibration | ... | ... | PASS / WARN / FAIL |
| Precommitment | ... | ... | PASS / WARN / FAIL |
| ... | ... | ... | ... |

After the table, include only:

- **Misses:** predictions or assumptions that were wrong.
- **Disagreements:** independent checks that did not converge.
- **Entropy balance:** before -> after, using a number or explicit measurable units where possible.
- **Open:** what remains genuinely unknown.
- **Next step:** one concrete action.

## Light pass

For `sito`, run only:

1. **Prior Evidence** — What is already known?
2. **Calibration** — Can the method distinguish known positive and negative cases?
3. **Precommitment** — What do we expect before checking?
4. **Blind Critic** — What could be wrong without being told what to attack?
5. **Entropy Balance** — Did the work leave the system clearer and simpler?

## Success criterion

Do not optimize for an answer that merely sounds convincing.

Optimize for a result after which the space of plausible errors is smaller, important claims have appropriately independent support, failed expectations are visible, and continuation is easier than it was before.
