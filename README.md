# OutisLi Skills

Personal skills for understanding and documenting research, learning through technical work, and continuing tasks across conversations. Works with Codex, Claude Code, Cursor, and other agents that support Agent Skills. The agent follows your language in conversation.

- [article-reading](skills/article-reading/SKILL.md): understand a paper's problem, method, evidence, and useful implications from a file, link, identifier, or excerpt.
- [toturial-skill](skills/toturial-skill/SKILL.md): learn the necessary concepts while working through a technical task, one manageable step at a time.
- [session-export](skills/session-export/SKILL.md): create a handover prompt you can paste directly into a fresh agent conversation, preserving the task and verified state without carrying over unsupported guesses.
- [working-report](skills/working-report/SKILL.md): maintain a coherent research report with accessible explanations and supplementary material where needed, using English and LaTeX by default.

Paper reading and manuscript writing can draw on tutorial methods to explain unfamiliar concepts within their own reading or writing task. Each skill also works on its own. The root `AGENTS.md` is a backup of personal instructions and is not installed.

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
Use working-report to develop this ongoing study into a clear research report.
```

For learning tasks, tell the agent what you already know and how deeply you need to understand the topic. You can ask for a simpler explanation, a concrete example, a derivation, or a faster pace at any point. Explanations stay in the conversation unless you request a separate document.
