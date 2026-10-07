# AI-tools

Public, open-standard Agent Skills for repeatable AI-assisted workflows.

## Skills

| Skill | What it does |
| --- | --- |
| [`session-task-benchmark`](skills/session-task-benchmark/SKILL.md) | Reviews up to 20 accessible recent sessions and creates one fictional prompt based on recurring small tasks, for comparing models. |

Skills are kept in the top-level `skills/` directory as distributable packages, not in a project-local agent configuration directory. The repository root is also the Claude Code plugin root, with marketplace/plugin metadata in `.claude-plugin/`. No special GitHub repository setting is required. Skills use the open [Agent Skills `SKILL.md` format](https://agentskills.io/specification) and are exposed through this repository's [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces).

## Install

### GitHub Copilot

To install the skill from this public repository with GitHub CLI for the current project, run:

```sh
gh skill preview amdor/AI-tools session-task-benchmark
gh skill install amdor/AI-tools session-task-benchmark
```

To install it for Copilot across projects for your user, choose user scope:

```sh
gh skill install amdor/AI-tools session-task-benchmark --scope user
```

The preview command lets you inspect the skill before installing it. `gh skill` is a GitHub CLI public-preview feature and requires GitHub CLI 2.90.0 or later. See GitHub's [agent skills guide](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) for other scopes and options.

### Claude Code: plugin marketplace

Register this public marketplace and install its plugin:

```sh
claude plugin marketplace add amdor/AI-tools
claude plugin install ai-tools@ai-tools-marketplace --scope user
```

User scope makes the plugin available across Claude Code projects on that machine. Skills in the plugin are namespaced by its name; invoke this one as `/ai-tools:session-task-benchmark`. You can also add the marketplace and install the plugin from the `/plugin` interface.

### Claude Code or Copilot: direct skill installation

GitHub CLI can install the skill directly into Claude Code's user skill location, without the plugin marketplace:

```sh
gh skill preview amdor/AI-tools session-task-benchmark
gh skill install amdor/AI-tools session-task-benchmark --agent claude-code --scope user
```

For manual installation, copy the skill directory from `skills/session-task-benchmark/` into a supported destination: `.claude/skills/` for a project-level Claude Code skill, `~/.claude/skills/` for a personal Claude Code skill, `.github/skills/`, `.claude/skills/`, or `.agents/skills/` for a project-level Copilot skill, or `~/.copilot/skills/` or `~/.agents/skills/` for a personal Copilot skill.

Skills contain instructions that affect agent behavior. Review a skill's contents before installing it, especially when installing from an unfamiliar repository.