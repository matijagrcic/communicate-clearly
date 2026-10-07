# Communicate Clearly

A reusable agent skill for preserving meaning and making intent explicit in agent handoffs and human explanations.

It combines SMCP-inspired message distinctions, STE-inspired clarity, and reflective attention to purpose. The aim is to make facts, interpretations, advice, requests, plans, and results easier to distinguish while keeping the user's objective and constraints in view.

## Use

Invoke the skill with a task such as:

```text
Use $communicate-clearly to rewrite this handoff. Preserve which steps are
required, which are recommendations, and what has actually been verified.
```

```text
Use $communicate-clearly to explain these findings to a nontechnical reader.
Keep the uncertainties and trade-offs clear, using natural prose.
```

Human explanations use ordinary language. Agent exchanges can use `INFORMATION`, `INFERENCE`, `QUESTION`, `REQUEST`, `RECOMMENDATION`, `PLAN`, `RESULT`, and `WARNING` when explicit distinctions help. The marker vocabulary is adapted for agent work.

The skill also notices when a proposed action optimizes a metric at the expense of the stated purpose. It distinguishes changes of method from changes of objective and carries forward decisions the user has already made.

## Install in Codex

The repository root is the skill folder. With GitHub CLI authenticated to an account that can access this private repository, clone it to a new skill directory:

```sh
gh repo clone matijagrcic/communicate-clearly "${CODEX_HOME:-$HOME/.codex}/skills/communicate-clearly"
```

If the directory already exists, inspect it before replacing anything. For other agents that support `SKILL.md`, place this folder in their documented skill location. The skill itself requires no tools, API keys, or runtime packages. Normal automatic skill discovery remains enabled.

## Contents

- [SKILL.md](SKILL.md): purpose, mode selection, meaning preservation, and proportional reflection.
- [Agent coordination](references/agent-coordination.md): marker meanings, optional context fields, status, and scoped handoffs.
- [Examples](references/examples.md): faithful rewrites, evidence limits, values, and corrections of framing.
- [Design notes](references/design-notes.md): sources and how their ideas shape the skill.
- [Behavioral cases](evals/cases.json) and [evaluation guide](evals/README.md): prompts and semantic review criteria.
