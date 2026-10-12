# SITO

**A verification-first Agent Skill for reducing uncertainty in research, engineering, analysis, debugging, and decision-making.**

SITO is a compact workflow for agents that should do more than produce a plausible answer. It forces the agent to check prior evidence, validate its measuring stick, state expectations before seeing results, seek independent criticism, and leave behind a result that another person or agent can continue from.

> **Evidence before theory. Calibration before measurement. Prediction before observation.**

## Install

SITO follows the Agent Skills convention: the reusable instructions live in [`SKILL.md`](./SKILL.md).

Use the repository root as the skill directory. SKILL.md is the entrypoint. The only required behavioral file is `SKILL.md`; [`agents/openai.yaml`](./agents/openai.yaml) provides optional OpenAI UI metadata.


## Usage

Invoke one of two modes:

```text
SITO <task>
```

Runs the full 11-role verification pass.

```text
sito <task>
```

Runs the light pass:

```text
Prior Evidence -> Calibration -> Precommitment -> Blind Critic -> Entropy Balance
```

## The 11 roles

| # | Role | Purpose |
|---|---|---|
| 1 | Prior Evidence | Find existing answers and constraints before deriving new ones. |
| 2 | Calibration | Prove the measuring stick works on known yes/no cases. |
| 3 | Precommitment | Record expected results and thresholds before observing them. |
| 4 | Minimal Intervention | Make the smallest reversible change that tests the hypothesis. |
| 5 | Blind Critic | Critique once without knowing the favored hypothesis, then again with it. |
| 6 | Naive Examiner | Test whether a literal outsider catches known planted failures. |
| 7 | Outsider Check | Recheck with a different model family, tool, method, implementation, or team. |
| 8 | Independence Check | Identify shared dependencies between supposedly independent witnesses. |
| 9 | Entropy Balance | Ensure the work reduces uncertainty and complexity, or name the trade. |
| 10 | Archive | Preserve compact, reproducible evidence and close resolved work. |
| 11 | Newcomer Test | Verify that someone with no work history can continue from the result. |

## Why SITO exists

Agents are very good at producing coherent explanations. Coherence is not verification.

Common failure modes include:

- using a broken metric confidently;
- choosing success criteria after seeing the result;
- asking critics only about suspected problems;
- treating correlated outputs as independent confirmation;
- adding more process, files, code, and exceptions than the problem justifies;
- producing a result that only its author can interpret.

SITO turns those failure modes into explicit checks.

## Output

A full SITO run should end with one compact table:

| Role | Prediction / question | Observed fact | Verdict |
|---|---|---|---|
| Calibration | Known positive and negative should separate | ... | PASS |
| Precommitment | Expected X >= baseline Y | ... | WARN |
| ... | ... | ... | ... |

Then only:

- **Misses**
- **Disagreements**
- **Entropy balance**
- **Open**
- **Next step**

## Design principles

- **No measurement before calibration.**
- **No result without a precommitted expectation.**
- **A control that cannot fail proves nothing.**
- **Blind criticism comes before targeted criticism.**
- **Correlated witnesses do not count as independent evidence.**
- **Disagreement is evidence, not a vote.**
- **Complexity must pay rent.**
- **A result must survive handoff.**

## Repository layout

```text
sito/
├── SKILL.md
├── README.md
├── LICENSE
└── agents/
    └── openai.yaml
```

## License

MIT. See [`LICENSE`](./LICENSE).
