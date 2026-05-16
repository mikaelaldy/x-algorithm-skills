Skills are organized into bucket folders under `skills/`.

- `growth/` — X account growth skills based on public X algorithm signals.

Every skill in `growth/` must have:

- a link in the top-level `README.md`
- an entry in `skills/growth/README.md`
- an entry in `.claude-plugin/plugin.json`

Skill frontmatter should stay AgentSkills-compatible: `name` and `description` only unless there is a strong reason to add platform-specific metadata. Keep descriptions specific and include "Use when..." triggers.
