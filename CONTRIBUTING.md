# Contributing skills

## Add a skill

Create one directory under `skills/` using lowercase letters, digits, and hyphens:

```text
skills/my-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/   # optional
├── scripts/      # optional
└── assets/       # optional
```

`SKILL.md` must contain YAML frontmatter with these required fields:

```yaml
---
name: my-skill
description: Clear description of capability and trigger conditions.
---
```

Keep `SKILL.md` under 500 lines when possible. Put detailed material in directly linked references. Do not add README files inside individual skill directories unless a skill genuinely needs one as an output asset.

## Skill requirements

- State what the agent must do, not only what it should know.
- Define scope and non-goals.
- Prefer evidence, commands, and reproducible examples.
- Separate facts from assumptions and uncertainty.
- Never claim tools ran when they did not.
- Document destructive or external actions.
- Avoid hardcoded secrets, personal tokens, and private paths.
- Keep dependencies optional or document installation clearly.

## Validation

Run the relevant validator before opening a pull request. For Codex skills:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/my-skill
```

Also inspect links, scripts, examples, and git diff for accidental secrets or unrelated files.

## Pull requests

Use a focused branch and explain:

1. What problem skill solves.
2. What workflow it adds or changes.
3. How it was validated.
4. Known limitations or external dependencies.

Maintainer labels:

- `skill`
- `new-skill` or `enhancement`
- `needs-review`
- `validated` after verification
