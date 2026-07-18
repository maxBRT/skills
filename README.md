# skills

Personal agent skills for the open [Agent Skills](https://agentskills.io) ecosystem. Install with the [Vercel skills CLI](https://github.com/vercel-labs/skills).

[![skills.sh](https://skills.sh/b/maxBRT/skills)](https://skills.sh/maxBRT/skills)

## Install

```bash
# List available skills
npx skills add maxBRT/skills --list

# Install all skills (interactive)
npx skills add maxBRT/skills

# Install a specific skill globally
npx skills add maxBRT/skills --skill wrap-up -g -y

# Install to a specific agent
npx skills add maxBRT/skills --skill wrap-up -a cursor -g -y
```

## Use without installing

```bash
npx skills use maxBRT/skills@wrap-up
```

## Available skills

| Skill | Description |
| --- | --- |
| `wrap-up` | Ship a one-on-one session: branch, commit, push, open a PR against main. |

## Add a skill

```bash
# From the repo root
npx skills init my-skill
mv my-skill skills/my-skill
```

Each skill is a directory under `skills/` with a `SKILL.md`:

```markdown
---
name: my-skill
description: What this skill does and when to use it
---

# My Skill

Instructions for the agent...
```

Optional extras per skill: `scripts/`, `references/`, and other supporting files.

Then commit, push, and install:

```bash
npx skills add maxBRT/skills --skill my-skill -g -y
```

## Layout

```
skills/
  wrap-up/
    SKILL.md
```

The CLI discovers `SKILL.md` files under `skills/` (and other standard agent skill paths). See [vercel-labs/skills](https://github.com/vercel-labs/skills) for full discovery rules.

## License

MIT
