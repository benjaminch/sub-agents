# Codex sub-agents

A collection of portable Codex sub-agents for engineering work, with a distributed systems architecture toolkit.

## Agents

| Agent | Job | Permissions |
| --- | --- | --- |
| `code-reviewer` | Finds concrete correctness, security, architecture, and maintainability problems in a change. | Read-only |
| `rust-backend-developer` | Implements and validates focused Rust backend changes. | Workspace write |
| `frontend-developer` | Builds or reshapes frontend work with intentional visual design and accessible behavior. | Workspace write |
| `qovery-product-engineer` | Delegates Qovery product and engineering work to the locally installed Qovery product-engineer skill. | Workspace write |
| `architect` | Compares distributed system designs and writes architecture deliverables. | Workspace write |
| `architecture-reviewer` | Challenges correctness, consistency, and design tradeoffs. | Read-only |
| `reliability-reviewer` | Assesses failure recovery, SLOs, capacity, and performance. | Read-only |

## Use in a project

Codex discovers project agents in `.codex/agents/`. Copy the agents you want into the target repository:

```sh
mkdir -p /path/to/project/.codex/agents
cp .codex/agents/code-reviewer.toml /path/to/project/.codex/agents/
```

Or install the agent definitions globally for your local Codex setup (the architecture agents also need the toolkit skills in the target project):

```sh
mkdir -p ~/.codex/agents
cp .codex/agents/*.toml ~/.codex/agents/
```

Then delegate with the agent name and a bounded task. For example: “Use `code-reviewer` to review the diff against `main` and report only actionable findings.”

## Distributed systems architecture toolkit

This is a local implementation of the supplied toolkit description, not a copy of an upstream archive. It includes five self-contained skills in `.agents/skills/`, three architecture agents, and [RFC](docs/architecture/templates/RFC.md), [ADR](docs/architecture/templates/ADR.md), [review](docs/architecture/templates/REVIEW.md), and [failure matrix](docs/architecture/templates/FAILURE-MATRIX.md) templates.

The skills cover system design (`distributed-systems-architect`), independent critique (`architecture-reviewer`), messaging (`event-driven-architecture`), data invariants (`database-consistency`), and failure/capacity analysis (`reliability-performance`). They require explicit assumptions, quantitative reasoning, and validation plans. Architecture tasks produce documents; implementation needs authorization, including authorization already given in the session.

To use the complete toolkit in another repository, inspect existing files for naming conflicts, then copy the five skill directories, three architecture agent definitions, and template directory into matching paths. Preserve the target repository's `AGENTS.md`; this repository's guidance describes maintaining these definitions rather than application architecture policy. Keep skills and templates together: the skills refer to `docs/architecture/templates/` from the target repository root. No additional personal skills are required by these three agents.

Example request:

```text
Use $distributed-systems-architect to design an order processing platform
for 2,000 peak requests/second, 99.95% availability, and p99 below 250 ms.
Ask architecture-reviewer and reliability-reviewer to independently challenge it.
Produce an RFC, ADR, Mermaid diagram, failure matrix, capacity estimates,
and implementation roadmap. State assumptions and measurement gaps.
Do not modify application code or infrastructure without approval.
```

Run structural validation with Python 3.11 or later:

```sh
python3 scripts/validate_toolkit.py
```

Structural validation checks the bundled files, skill metadata, TOML definitions, permissions, and skill references. It does not test Codex discovery, agent delegation, Mermaid rendering, or real-world architecture quality. Those require verification in the consuming Codex environment and against actual workloads. Reviewers return their reports to the caller because their sandbox is read-only; the architect can incorporate them into documents.

## Design choices

The agents do not set a model. They inherit the model and reasoning settings of the session that calls them, which keeps this repository useful across Codex configurations. The reviewer is read-only because a review should be evidence, not an unrequested patch. The implementers can edit the workspace because their roles include validation and delivery.

The Rust agent takes inspiration from the [VoltAgent Rust engineer](https://github.com/VoltAgent/awesome-codex-subagents/blob/main/categories/02-language-specialists/rust-engineer.toml), but adds explicit checks for ownership, error boundaries, async cancellation, unsafe invariants, and tests. The reviewer uses the [Conventional Comments](https://conventionalcomments.org/) format so each comment says whether it blocks the change and why.

The Qovery product-engineer agent is intentionally a small adapter around a locally installed `qovery-product-engineer` skill. The skill can contain company-specific workflow and data-source guidance, so it is not copied into this public repository.

## Contributing

Keep every agent focused on a real role. Instructions should describe decisions, constraints, and evidence expected at the end of a task. Do not add generic motivational language or a long catalog of tools.

## License

[MIT](LICENSE)
