# OutisLi Skills

Personal skills for understanding research papers, learning through technical work, and continuing tasks across conversations. Works with Codex, Claude Code, Cursor, and other agents that support Agent Skills. Responses follow your language and the task you want to complete.

- [article-reading](skills/article-reading/SKILL.md): understand a paper's problem, method, evidence, and useful implications from a file, link, identifier, or excerpt.
- [toturial-skill](skills/toturial-skill/SKILL.md): learn the necessary concepts while working through a technical task, one manageable step at a time.
- [session-export](skills/session-export/SKILL.md): create a handover prompt you can paste directly into a fresh agent conversation, preserving the task and verified state without carrying over unsupported guesses.

Paper reading can draw on tutorial explanations for unfamiliar concepts, then return to the paper. Each skill also works on its own. The root `AGENTS.md` is a backup of personal instructions and is not installed.

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
Use session-export to prepare a handover I can paste into a fresh agent conversation.
```

For learning tasks, tell the agent what you already know and how deeply you need to understand the topic. You can ask for a simpler explanation, a concrete example, a derivation, or a faster pace at any point. Explanations stay in the conversation unless you request a separate document.
