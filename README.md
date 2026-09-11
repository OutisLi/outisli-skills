# OutisLi Skills

Personal prompts and reusable skills for clear technical work, practical learning, and research. Instructions are written in English; conversations follow the user's language.

## Contents

| Component                                          | Purpose                                                                                                                                        |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [AGENTS.md](AGENTS.md)                             | Backup of personal instructions for reasoning, communication, coding, and document maintenance.                                                |
| [toturial-skill](skills/toturial-skill/SKILL.md)   | Learn the concepts needed for a real technical task while completing it, with explanations calibrated to the reader's starting point and goal. |
| [article-reading](skills/article-reading/SKILL.md) | Understand a research paper's problem, mechanism, evidence, and useful implications, with depth adapted to the reading goal.                   |

The existing `toturial-skill` name is retained so previous invocations continue to work. Its teaching approach and source attribution are preserved as the collection evolves.

## Layout

```text
outisli-skills/
├── AGENTS.md
├── README.md
└── skills/
    ├── article-reading/
    │   ├── SKILL.md
    │   └── agents/openai.yaml
    └── toturial-skill/
        ├── SKILL.md
        ├── agents/openai.yaml
        ├── references/
        └── NOTICE.md
```

Each directory under `skills/` is an independently installable skill. Its `SKILL.md` uses the shared Agent Skills format, so both Codex and Claude Code can use it. The optional `agents/openai.yaml` adds Codex display metadata. Supporting files stay inside their skill; no sibling skill or repository-level prompt is required to use an individual skill.

## Install All Skills

Use the [Skills CLI](https://github.com/vercel-labs/skills). The package name is `skills`, plural. Run this in a terminal to install the whole collection globally and select the agents you use, such as Codex, Claude Code, or Cursor:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill '*'
```

The quoted `'*'` selects every skill in the repository, while agent destinations remain a separate choice. Review those destinations in the CLI. Its universal directory is shared by compatible agents; additional agents receive their own links only when selected.

Keep this default interactive: `--all` selects every supported agent, and `--yes` can fall back to all agents when none are detected. For an unattended installation, explicitly select the installed agents with `--agent` before adding `--yes`. When an AI agent runs the CLI, it may automatically target that agent; use an explicit selection if you want additional agents in that situation. These behaviors are documented in the [CLI options](https://github.com/vercel-labs/skills#options) and implemented in [agent selection](https://github.com/vercel-labs/skills/blob/main/src/add.ts).

Re-run the all-skills command to refresh installed skills and include any newly added ones. Start a new agent session to use the refreshed collection. Run the command on each machine that should receive updates.

To inspect the available skills without installing them:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --list
```

To install one skill:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill article-reading
```

The installer handles each agent's directory. Reinstalling refreshes the shared skill content and selected destinations; it preserves any links previously installed in other agents. Other supported agents can be selected with `--agent`.

If migrating an older standalone tutorial installed across many agents, remove that skill's old global registrations before selecting the agents for this collection:

```bash
npx skills remove toturial-skill --global
npx skills add https://github.com/OutisLi/outisli-skills --global --skill '*'
```

The removal names only `toturial-skill`. The following installation restores it from this collection together with the other skills.

Invoke a skill by name, for example, ask the agent to use `article-reading` for a paper or `toturial-skill` for a technical task. Native invocation syntax is `$article-reading` in Codex and `/article-reading` in Claude Code. A matching request can also trigger the skill automatically.

## Prompt Backup

The root `AGENTS.md` is a backup for reference and version history. The installable collection consists only of the directories under `skills/`. Installing or updating this collection leaves global Codex and Claude Code instruction files unchanged.

## Add a Skill

Create `skills/<skill-name>/SKILL.md` with YAML frontmatter containing `name` and `description`. Use the same name for the directory and frontmatter. Add references, scripts, or assets only when that skill needs them, and update the contents table. The all-skills installation command discovers new directories without an additional registry or a change to the installation command.

Format Markdown from the repository root with:

```bash
uvx --with mdformat-gfm --with mdformat-frontmatter mdformat .
```

The committed `.mdformat.toml` keeps each prose paragraph on one line. The plugins preserve GitHub-style tables and skill frontmatter.

Teaching-source attribution is recorded in [the tutorial notice](skills/toturial-skill/NOTICE.md).
