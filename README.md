[![skills.sh](https://skills.sh/b/Jei-sKappa/skills)](https://skills.sh/Jei-sKappa/skills)

# Jei-sKappa's Skills

A personal collection of refined `SKILL.md` files — standalone, general-purpose, context-agnostic capabilities you install individually or all at once, and use in any project or workflow. Skills work inside Claude Code, Codex, Gemini CLI, OpenCode, or any harness that loads `SKILL.md` files.

## Installation

Install every skill at once:

```sh
npx skills add Jei-sKappa/skills
```

## Skills

#### [`afk-exploration`](./skills/afk-exploration/SKILL.md)

Start AFK exploration on a topic only when the user explicitly asks for AFK research or exploration.

```sh
npx skills add Jei-sKappa/skills --skill afk-exploration
```

#### [`brief-the-recipient`](./skills/brief-the-recipient/SKILL.md)

Draft a self-contained outcome briefing — verdict, rationale, caveats, and pointers — when the user wants the conclusion of the current discussion packaged as a paste-ready handoff for a fresh AI session, a follow-up task, or a teammate (manager, reviewer, future-you, anyone receiving the conclusion).

```sh
npx skills add Jei-sKappa/skills --skill brief-the-recipient
```

#### [`consult-the-expert`](./skills/consult-the-expert/SKILL.md)

Draft a casual, context-rich message to consult a more experienced developer when the user needs help framing a technical problem, decision, or blocker for someone with no prior context.

```sh
npx skills add Jei-sKappa/skills --skill consult-the-expert
```

#### [`meta-prompting`](./skills/meta-prompting/SKILL.md)

Refine a draft prompt for a fresh AI session only when the user explicitly mentions "meta-prompt" or "meta-prompting".

```sh
npx skills add Jei-sKappa/skills --skill meta-prompting
```

#### [`name-cracker`](./skills/name-cracker/SKILL.md)

Generate name candidates for a project, product, or tool by fanning out one generator subagent per naming-strategy category and merging the results into a single shortlisted file; use when the user wants to explore names broadly and pick a favorite.

```sh
npx skills add Jei-sKappa/skills --skill name-cracker
```

#### [`report-to-the-owner`](./skills/report-to-the-owner/SKILL.md)

Draft a casual, context-rich message to a code owner when the user has hit a blocker in code owned elsewhere and wants to hand off the issue with a proposed change rather than ask for advice.

```sh
npx skills add Jei-sKappa/skills --skill report-to-the-owner
```

#### [`take-snapshot`](./skills/take-snapshot/SKILL.md)

Derive a comprehensive, stack-agnostic snapshot document of an existing codebase when the user wants a hybrid SRS and PRD for a 1:1 rebuild, rewrite, port, or documentation pass without migration or target-stack guidance.

```sh
npx skills add Jei-sKappa/skills --skill take-snapshot
```

#### [`the-librarian`](./skills/the-librarian/SKILL.md)

Route local reference-repository work to stock, consult, or research flows when the user wants to clone repos into the library, consult stocked repos, or produce in-depth reports from them.

```sh
npx skills add Jei-sKappa/skills --skill the-librarian
```
