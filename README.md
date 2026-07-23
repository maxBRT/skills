# skills

My personal agent skills for the open [Agent Skills](https://agentskills.io) ecosystem. Install with the [Vercel skills CLI](https://github.com/vercel-labs/skills).

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
| `to-epic` | Turn a conversation into an epic (full PRD) plus tracer-bullet sub-issues on the project tracker. |
| `wrap-up` | Ship a one-on-one session: branch, commit, push, open a PR against main. |

The CLI discovers `SKILL.md` files under `skills/` (and other standard agent skill paths). See [vercel-labs/skills](https://github.com/vercel-labs/skills) for full discovery rules.

## License

MIT
