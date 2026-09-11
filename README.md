# OutisLi Skills

Personal prompts and reusable skills for clear technical work, practical learning,
and research. Instructions are written in English; conversations follow the
user's language.

## Contents

| Component | Purpose |
| --- | --- |
| [AGENTS.md](AGENTS.md) | Backup of personal instructions for reasoning, communication, coding, and document maintenance. |
| [toturial-skill](skills/toturial-skill/SKILL.md) | Learn the concepts needed for a real technical task while completing it, with explanations calibrated to the reader's starting point and goal. |
| [article-reading](skills/article-reading/SKILL.md) | Understand a research paper's problem, mechanism, evidence, and useful implications, with depth adapted to the reading goal. |

The existing `toturial-skill` name is retained so previous invocations continue
to work. Its original instructions, references, and attribution are preserved.

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

Each directory under `skills/` is an independently installable skill. Its
`SKILL.md` uses the shared Agent Skills format, so both Codex and Claude Code can
use it. The optional `agents/openai.yaml` adds Codex display metadata. Supporting
files stay inside their skill; no sibling skill or repository-level prompt is
required to use an individual skill.

## Install All Skills

Use the [Skills CLI](https://github.com/vercel-labs/skills). The package name is
`skills`, plural. Install the whole collection globally for Codex and Claude Code:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill '*' --agent codex claude-code --yes
```

The quoted `'*'` selects every skill in the repository. Re-run this same command
to refresh installed skills and include any newly added ones. A new agent session
will discover them. Publishing a new skill does not automatically update other
machines; run the command on each machine that should receive it.

To inspect the available skills without installing them:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --list
```

To install one skill:

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill article-reading --agent codex claude-code --yes
```

The installer handles each agent's directory. Installing `toturial-skill` from
this collection replaces the earlier standalone installation under the same
skill name. Other supported agents can be selected with `--agent`.

## Prompt Backup

The root `AGENTS.md` is a backup for reference and version history. The installable
collection consists only of the directories under `skills/`. Installing or
updating this collection leaves global Codex and Claude Code instruction files
unchanged.

## Add a Skill

Create `skills/<skill-name>/SKILL.md` with YAML frontmatter containing `name` and
`description`. Use the same name for the directory and frontmatter. Add references,
scripts, or assets only when that skill needs them, and update the contents table.
The all-skills installation command discovers new directories without an
additional registry or a change to the installation command.

Teaching-source attribution is recorded in
[the tutorial notice](skills/toturial-skill/NOTICE.md).
