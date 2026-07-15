# ndelanhese/skills

Personal collection of reusable AI-agent skills for Codex and compatible agent runtimes.

This repository stores focused operating procedures, evaluation standards, review protocols, and domain workflows that make agents more reliable, more rigorous, and easier to steer.

## Available skills

### `independent-qa-challenge`

Independent senior-QA protocol for challenging feature tasks, pull requests, bug fixes, and test plans.

Core mission: try to invalidate each task fairly and with evidence. The skill actively searches for missing scenarios, edge cases, regression risks, broken assumptions, weak test oracles, and unverified acceptance criteria. It must distinguish verified defects from risks, questions, and recommendations.

Includes:

- anti-anchoring context protocol;
- adversarial but fair QA posture;
- input, state, actor, flow, time, dependency, concurrency, data, platform, operations, and security challenge matrix;
- durable test design across unit, component, integration, contract, and E2E layers;
- automation rules for deterministic, maintainable tests;
- AI-agent-specific testing for prompt injection, tool calls, grounding, refusal, variance, and side effects;
- P0–P3 severity and confidence calibration;
- mandatory evidence-based output contract;
- verdicts: `INVALIDATED`, `CONDITIONALLY VALID`, `SURVIVED CHALLENGE`, and `BLOCKED`.

## Repository structure

```text
.
├── README.md
├── CONTRIBUTING.md
├── LICENSE
└── skills/
    └── <skill-name>/
        ├── SKILL.md
        ├── openai.yaml
        ├── references/     # optional
        ├── scripts/        # optional
        └── assets/         # optional
```

Each skill is self-contained. A skill must not depend on another skill unless that dependency is documented explicitly.

## Installation

Install one skill from this repository:

```bash
npx skills add ndelanhese/skills --skill independent-qa-challenge
```

Install the full collection:

```bash
npx skills add ndelanhese/skills
```

For Codex, copy or symlink a skill folder into `~/.codex/skills/`:

```bash
cp -R skills/independent-qa-challenge ~/.codex/skills/
```

Invoke explicitly:

```text
$independent-qa-challenge
```

## Design principles

### Evidence over confidence

Skills should produce findings tied to source files, symbols, commands, test output, logs, contracts, or reproducible scenarios. They must never claim execution that did not happen.

### Adversarial toward behavior, fair toward people

Skills may challenge assumptions aggressively. They must not invent requirements, inflate severity, or turn style preferences into defects.

### Durable over cosmetic

Prefer contracts, invariants, properties, and observable behavior over implementation-coupled assertions.

### Progressive disclosure

Keep core workflow in `SKILL.md`. Move large references, templates, scripts, and framework-specific material into directly linked subfolders.

### Self-contained by default

A skill should work without requiring a proprietary service, hidden context, or another skill. Optional integrations must have a clear fallback.

## Quality bar for new skills

Every new skill should include:

- valid frontmatter with lowercase hyphenated `name` and precise `description`;
- explicit trigger conditions;
- concrete workflow, not only principles;
- failure modes and gotchas;
- deterministic output format when output quality matters;
- examples for common usage;
- no placeholder TODOs;
- validation with the appropriate skill validator;
- documentation of external dependencies, if any.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before adding or changing a skill.

## License

MIT. See [LICENSE](LICENSE).
