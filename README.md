# OutisLi Skills

Personal skills for conducting, understanding, and documenting research, learning through technical work, and continuing tasks across conversations. The shared collection works with Codex, Claude Code, Cursor, and other agents that support Agent Skills. The agent follows your language in conversation.

- [research-skill](skills/research-skill/SKILL.md): carry out a study in an organized workspace, validate experiments, maintain project memory and experiment records, and produce a working report.
- [article-reading](skills/article-reading/SKILL.md): understand a paper's problem, method, evidence, and useful implications from a file, link, identifier, or excerpt.
- [tutorial-skill](skills/tutorial-skill/SKILL.md): learn the necessary concepts while working through a technical task, one manageable step at a time.
- [session-export](skills/session-export/SKILL.md): create a handover prompt you can paste directly into a fresh agent conversation, preserving the task and verified state without carrying over unsupported guesses.
- [working-report](skills/working-report/SKILL.md): maintain a coherent research report with clear explanations, data plots, and explanatory figures, using English and LaTeX by default.
- [monitor-skill](codex-skills/monitor-skill/SKILL.md), Codex only: estimate job duration, use bounded waits, advance independent work, and verify results before continuing.

Research uses working-report for its final report. Paper reading and report writing can draw on tutorial methods to explain unfamiliar concepts. The root `AGENTS.md` is a backup of personal instructions and is not installed.

## Install

```bash
npx skills add https://github.com/OutisLi/outisli-skills/tree/main/skills --global --skill '*'
```

Select the agents you use for the shared collection. For Codex, also install the Codex-only skills:

```bash
npx skills add https://github.com/OutisLi/outisli-skills/tree/main/codex-skills --global --skill '*' --agent codex
```

Keep `monitor-skill` out of Claude Code, which has native background-task tools. The default setup also includes the third-party skills in [Recommended Skills](#recommended-skills); install each with its listed command. Start a new agent session after installation. Run the same commands again to update the installed skills and include new skills in each collection.

## Recommended Skills

### [anatomy](https://github.com/wheresryan22/anatomy)

Explain machines and technical concepts with detailed, interactive isometric illustrations. Produces SVG, standalone HTML, or React components, with optional WebGL effects.

```bash
npx skills add https://github.com/wheresryan22/anatomy --global
```

## Use

Ask your agent to use a skill by name:

```text
Use research-skill to investigate [question] in [workspace] with [resources and constraints].
Use article-reading to help me understand this paper: [link or file].
Use tutorial-skill to teach me what I need to complete [task].
Use session-export to prepare a handover I can paste into a fresh agent conversation.
Use working-report to develop this ongoing study into a clear research report.
Use monitor-skill in Codex to follow [job] and continue when its result is verified.
```

For learning tasks, tell the agent what you already know and how deeply you need to understand the topic. You can ask for a simpler explanation, a concrete example, a derivation, or a faster pace at any point. Explanations stay in the conversation unless you request a separate document.
