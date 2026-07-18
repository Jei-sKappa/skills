[![skills.sh](https://skills.sh/b/Jei-sKappa/skills)](https://skills.sh/Jei-sKappa/skills)

# Jei-sKappa's Skills

A personal collection of refined `SKILL.md` files — standalone, general-purpose, context-agnostic capabilities you install and use one at a time, in any project or workflow. Skills work inside Claude Code, Codex, Gemini CLI, OpenCode, or any harness that loads `SKILL.md` files.

## Documentation

#### [`take-snapshot`](./skills/documentation/take-snapshot/SKILL.md)

Derive a comprehensive, stack-agnostic snapshot document of an existing codebase when the user wants a hybrid SRS and PRD for a 1:1 rebuild, rewrite, port, or documentation pass without migration or target-stack guidance.

```sh
npx skills add Jei-sKappa/skills --skill take-snapshot
```

## Handoff

#### [`brief-the-recipient`](./skills/handoff/brief-the-recipient/SKILL.md)

Draft a self-contained outcome briefing — verdict, rationale, caveats, and pointers — when the user wants the conclusion of the current discussion packaged as a paste-ready handoff for a fresh AI session, a follow-up task, or a teammate (manager, reviewer, future-you, anyone receiving the conclusion).

```sh
npx skills add Jei-sKappa/skills --skill brief-the-recipient
```

#### [`consult-the-expert`](./skills/handoff/consult-the-expert/SKILL.md)

Draft a casual, context-rich message to consult a more experienced developer when the user needs help framing a technical problem, decision, or blocker for someone with no prior context.

```sh
npx skills add Jei-sKappa/skills --skill consult-the-expert
```

#### [`report-to-the-owner`](./skills/handoff/report-to-the-owner/SKILL.md)

Draft a casual, context-rich message to a code owner when the user has hit a blocker in code owned elsewhere and wants to hand off the issue with a proposed change rather than ask for advice.

```sh
npx skills add Jei-sKappa/skills --skill report-to-the-owner
```

## Research

#### [`afk-exploration`](./skills/research/afk-exploration/SKILL.md)

Start AFK exploration on a topic only when the user explicitly asks for AFK research or exploration.

```sh
npx skills add Jei-sKappa/skills --skill afk-exploration
```

#### [`the-librarian`](./skills/research/the-librarian/SKILL.md)

Route local reference-repository work to stock, consult, or research flows when the user wants to clone repos into the library, consult stocked repos, or produce in-depth reports from them.

```sh
npx skills add Jei-sKappa/skills --skill the-librarian
```

## Support

#### [`meta-prompting`](./skills/support/meta-prompting/SKILL.md)

Refine a draft prompt for a fresh AI session only when the user explicitly mentions "meta-prompt" or "meta-prompting".

```sh
npx skills add Jei-sKappa/skills --skill meta-prompting
```

#### [`name-cracker`](./skills/support/name-cracker/SKILL.md)

Generate name candidates for a project, product, or tool by fanning out one generator subagent per naming-strategy category and merging the results into a single shortlisted file; use when the user wants to explore names broadly and pick a favorite.

```sh
npx skills add Jei-sKappa/skills --skill name-cracker
```

## Installation

Install any skill individually via:

```sh
npx skills add Jei-sKappa/skills --skill <skill-name>
```

For example, to install the codebase snapshot generator:

```sh
npx skills add Jei-sKappa/skills --skill take-snapshot
```

Skills are grouped under one marketplace plugin per `skills/` folder — `JeisKappa-documentation` (rendered as **`JeisKappa Documentation`**), `JeisKappa-handoff` (**`JeisKappa Handoff`**), `JeisKappa-research` (**`JeisKappa Research`**), and `JeisKappa-support` (**`JeisKappa Support`**). Dashes in the plugin name are split into spaces and each segment capitalized in `npx skills list`.
