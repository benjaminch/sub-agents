# Codex sub-agents

A small, opinionated collection of project-scoped Codex sub-agents for engineering work. The first three roles are deliberately narrow: a demanding reviewer, a Rust backend developer, and a frontend developer with a design bar.

## Agents

| Agent | Job | Permissions |
| --- | --- | --- |
| `code-reviewer` | Finds concrete correctness, security, architecture, and maintainability problems in a change. | Read-only |
| `rust-backend-developer` | Implements and validates focused Rust backend changes. | Workspace write |
| `frontend-developer` | Builds or reshapes frontend work with intentional visual design and accessible behavior. | Workspace write |

## Use in a project

Codex discovers project agents in `.codex/agents/`. Copy the agents you want into the target repository:

```sh
mkdir -p /path/to/project/.codex/agents
cp .codex/agents/code-reviewer.toml /path/to/project/.codex/agents/
```

Or install all three globally for your local Codex setup:

```sh
mkdir -p ~/.codex/agents
cp .codex/agents/*.toml ~/.codex/agents/
```

Then delegate with the agent name and a bounded task. For example: “Use `code-reviewer` to review the diff against `main` and report only actionable findings.”

## Design choices

The agents do not set a model. They inherit the model and reasoning settings of the session that calls them, which keeps this repository useful across Codex configurations. The reviewer is read-only because a review should be evidence, not an unrequested patch. The implementers can edit the workspace because their roles include validation and delivery.

The Rust agent takes inspiration from the [VoltAgent Rust engineer](https://github.com/VoltAgent/awesome-codex-subagents/blob/main/categories/02-language-specialists/rust-engineer.toml), but adds explicit checks for ownership, error boundaries, async cancellation, unsafe invariants, and tests. The reviewer uses the [Conventional Comments](https://conventionalcomments.org/) format so each comment says whether it blocks the change and why.

## Contributing

Keep every agent focused on a real role. Instructions should describe decisions, constraints, and evidence expected at the end of a task. Do not add generic motivational language or a long catalog of tools.

## License

[MIT](LICENSE)

