# Contributing to Pair Programming

Thank you for your interest. The highest authority is the skill instructions in [skills/pair-programming/SKILL.md](skills/pair-programming/SKILL.md) and the security model in the [README](README.md#security-model): what they say applies. Check every change against them.

## Skill rules

- The skill stays instruction-only: no scripts, executables, MCP servers, or required external services.
- The `SKILL.md` frontmatter defines name, description, and invocation behavior. The description states when the skill fits and when it does not.
- The core is provider-neutral. Agent-specific details belong in separate files under `agents/`, for example `agents/openai.yaml`, and must match `SKILL.md`.
- Assets under `assets/` are added only when an agent configuration references them.
- Approval and stop boundaries (network, installs, commits, pushes, security checks) are not weakened. Any relaxation needs an explicit justification in the pull request.
- No origin story, training references, or change history in `SKILL.md`.
- Invent nothing: no features, facts, commands, or check results. Anything that could not be verified is marked as unverified.

## Language

- Everything in this repository is in English: agent instructions (`SKILL.md`, `agents/openai.yaml`, `CLAUDE.md`), documentation, file names, and code.
- Wording is read literally: "should" is optional, "must" is mandatory. Do not tighten it.

## Branch model

- `main` contains only reviewed, stable states. Nobody works on it directly.
- `feature/<short-name>` for every change, branched from `main` and merged back via pull request.
- A release is a tag on `main`, see [Releases](#releases).
- Branch names are always English, lowercase, with hyphens, for example `feature/handoff-format`.

## Commits (Conventional Commits)

- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/) and are always in English: `<type>: <description>`, for example `fix: tighten approval boundaries`.
- Allowed types: `feat`, `fix`, `docs`, `refactor`, `ci`, `chore`.
- The description is in the imperative mood, without a trailing period. A rationale can go in the message body.
- One logical change per commit. A breaking change is marked with `!` after the type and `BREAKING CHANGE:` in the message body.

## Submitting changes

- Keep changes small and justify them by the purpose of the skill. Less is more: leave out anything without benefit.
- If the skill's behavior changes, check whether `README.md`, `CLAUDE.md`, and `agents/openai.yaml` need updating.
- Check locally that the skill is discovered: `npx skills add . --list`.
- Try changed instructions in a disposable test project with a real agent. Only what has been applied counts as verified.
- The Mondoo SkillCheck workflow must pass on the pull request.

## Releases

- A release is a reviewed Git tag in the `v0.1.0` format with a corresponding GitHub release. There is no release automation.
- Before every release, work through the checklist under [Maintainer checks and releases](README.md#maintainer-checks-and-releases).

## Working with agents

Agents working on this repository follow [CLAUDE.md](CLAUDE.md) and the branch and commit rules above. They do not commit, push, or delete without an explicit request.

## License

By contributing, you agree that your contribution is licensed under the [MIT License](LICENSE).
