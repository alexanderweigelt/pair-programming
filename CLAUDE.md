# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A [Skills CLI](https://skills.sh/docs/cli) source repository for the `pair-programming` skill. It contains no application code, build system, or test suite — the only artifact is the skill definition itself.

The skill is intentionally instruction-only: no scripts, executables, MCP server, or required external services.

## Repository structure

- `skills/pair-programming/SKILL.md` — the skill instructions consumed by coding agents (frontmatter defines name, description, and invocation behavior)
- `skills/pair-programming/agents/openai.yaml` — agent-specific interface metadata (display name, icon, default prompt, invocation policy)
- `skills/pair-programming/assets/` — icon assets referenced by the agent interface config

## How the skill is distributed

The repository is a GitHub source for the Skills CLI. Users install it via:

```bash
npx skills add alexanderweigelt/pair-programming --skill pair-programming
```

There is no npm package, no build step, and no release automation. A release is a reviewed git tag (`v0.1.0` format) with a corresponding GitHub release.

## Pre-release checklist

1. Verify local discovery: `npx skills add . --list`
2. Install into a disposable test project and verify one basic invocation in the target agent
3. Run Mondoo SkillCheck and review the unmodified result (requires explicit approval)
4. Review the diff, then explicitly approve commit and push
5. Tag the release and create the GitHub release manually