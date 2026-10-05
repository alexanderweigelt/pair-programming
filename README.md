# Pair Programming

An evidence-first agent skill for deliberate, human-led pair programming.

`pair-programming` changes a coding agent from an autonomous implementer into a collaborative partner. The developer makes decisions and explicitly approves each implementation slice; the agent investigates, explains trade-offs, implements only the agreed scope, verifies it, and stops for review.

## What it provides

- Evidence before recommendations: observations, inferences, and hypotheses stay distinct.
- Small, reviewable implementation slices rather than autonomous feature delivery.
- Mandatory approval before every implementation slice.
- A checkpoint before implementation and another after verification.
- Network access, API diagnostics, installs, commits, pushes, and security checks only through narrowly scoped, explicit approval.
- A compact, agent-independent handoff when a long session needs to continue elsewhere.

The skill is intentionally instruction-only: it includes no scripts, executables, MCP server, or required external service.

## Compatibility

The core skill is provider-neutral and designed for Claude Code first. It can also be installed for Codex, Cursor, and other agents supported by the [Skills CLI](https://skills.sh/docs/cli). Individual harnesses determine their own invocation syntax and available tools.

## Install

The repository is a GitHub source for the Skills CLI; it is not an npm package. Install the named skill with `npx` from a machine that has Node.js and a supported coding agent available.

### Choose scope and agent interactively

```bash
npx skills add alexanderweigelt/pair-programming --skill pair-programming
```

### Install globally for Claude Code

```bash
npx skills add alexanderweigelt/pair-programming --skill pair-programming --agent claude-code --global --yes
```

For another supported agent, replace `claude-code` with its Skills CLI identifier, such as `codex` or `cursor`. Omit `--global` for a project-scoped installation.

The Skills CLI may collect anonymous installation telemetry by default. If that is unsuitable, follow its documented telemetry opt-out before installing.

## Use

Open the target project in your coding-agent harness and invoke `pair-programming` using the harness's normal skill syntax—for example, `/pair-programming` where slash-invocation is supported. Alternatively, explicitly ask the agent to use the `pair-programming` skill.

At the beginning of a session, let the agent inspect the relevant repository and explain the evidence it found. Before every implementation slice, review and explicitly approve the stated scope. Network requests, API diagnostics, installation, Git operations, and security checks remain separately opt-in actions.

## Security model

The skill is deliberately conservative:

- It never treats a plausible explanation as an established fact.
- It does not use the network by default. Approved research is limited to a stated question and sources; API diagnostics require a separate approval.
- It does not install software, commit, push, or run a security scanner unless the developer approves the exact operation in advance.
- It does not transmit secrets, source code, customer data, or sensitive logs during approved research or diagnostics.

See [the skill instructions](skills/pair-programming/SKILL.md) for the complete workflow and authorization boundaries.

## Maintainer checks and releases

Before a release:

1. Confirm that the skill is discovered locally with `npx skills add . --list`.
2. With explicit approval, install it into a disposable local or test project and check one basic invocation in the intended agent.
3. With separate strict approval, run Mondoo SkillCheck and review the unmodified result.
4. Review the diff, then explicitly approve the commit and push.
5. Tag the reviewed first public release as `v0.1.0` and create the corresponding GitHub release.

The repository intentionally has no release automation. A release tag records a reviewed version; it does not grant an agent permission to publish or update anything.

## License

[MIT](LICENSE)
