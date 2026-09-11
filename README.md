# OutisLi Skills

Personal skills for understanding research papers and learning what you need to complete technical tasks. Works with Codex, Claude Code, Cursor, and other agents that support Agent Skills. Explanations follow your language and adapt to what you already know and what you want to achieve.

- [article-reading](skills/article-reading/SKILL.md): understand a paper's problem, method, evidence, and useful implications from a file, link, identifier, or excerpt.
- [toturial-skill](skills/toturial-skill/SKILL.md): learn the necessary concepts while working through a technical task, one manageable step at a time.

The skills work together: paper reading can draw on tutorial explanations for unfamiliar concepts, then return to the paper. Each skill also works on its own. The root `AGENTS.md` is a backup of personal instructions and is not installed.

## Install

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill '*'
```

Select the agents you use in the installer, then start a new agent session. Run the same command again to update the collection and include newly added skills.

## Use

Ask your agent to use a skill by name:

```text
Use article-reading to help me understand this paper: [link or file].
Use toturial-skill to teach me what I need to complete [task].
```

Tell it what you already know and how deeply you need to understand the topic. You can ask for a simpler explanation, a concrete example, a derivation, or a faster pace at any point. Explanations stay in the conversation unless you request a separate document.
