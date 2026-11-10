# Repository guidance

This repository contains portable Codex agent definitions.

- Put each agent in `.codex/agents/<agent-name>.toml`.
- Keep TOML valid and use `name`, `description`, `sandbox_mode`, and `developer_instructions`.
- An agent instruction should define a narrow role, a decision process, validation expectations, and a useful final report.
- Do not bake a specific model into an agent unless its job truly needs one. Portability is the default.
- Keep public documentation honest about what has been tested and what depends on a user’s local skills or tools.

## Architecture toolkit maintenance

- Keep reusable architecture workflows in `.agents/skills/` and deliverable templates in `docs/architecture/templates/`.
- When changing the toolkit, run `python3 scripts/validate_toolkit.py`. Structural validation does not establish runtime compatibility or architecture quality.

