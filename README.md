# OutisLi Skills

Personal skills for conducting, understanding, and documenting research, learning through technical work, and continuing tasks across conversations. Works with Codex, Claude Code, Cursor, and other agents that support Agent Skills. The agent follows your language in conversation.

- [research-skill](skills/research-skill/SKILL.md): carry out a study in an organized workspace, validate experiments, preserve useful records, and produce a working report.
- [article-reading](skills/article-reading/SKILL.md): understand a paper's problem, method, evidence, and useful implications from a file, link, identifier, or excerpt.
- [tutorial-skill](skills/tutorial-skill/SKILL.md): learn the necessary concepts while working through a technical task, one manageable step at a time.
- [session-export](skills/session-export/SKILL.md): create a handover prompt you can paste directly into a fresh agent conversation, preserving the task and verified state without carrying over unsupported guesses.
- [working-report](skills/working-report/SKILL.md): maintain a coherent research report with accessible explanations and supplementary material where needed, using English and LaTeX by default.

Research uses working-report for its final report. Paper reading and report writing can draw on tutorial methods to explain unfamiliar concepts. The root `AGENTS.md` is a backup of personal instructions and is not installed.

## Install

```bash
npx skills add https://github.com/OutisLi/outisli-skills --global --skill '*'
```

Select the agents you use in the installer, then start a new agent session. Run the same command again to update the collection and include newly added skills.

## Use

Ask your agent to use a skill by name:

```text
Use research-skill to investigate [question] in [workspace] with [resources and constraints].
Use article-reading to help me understand this paper: [link or file].
Use tutorial-skill to teach me what I need to complete [task].
Use session-export to prepare a handover I can paste into a fresh agent conversation.
Use working-report to develop this ongoing study into a clear research report.
```

For learning tasks, tell the agent what you already know and how deeply you need to understand the topic. You can ask for a simpler explanation, a concrete example, a derivation, or a faster pace at any point. Explanations stay in the conversation unless you request a separate document.
