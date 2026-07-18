# AGENTS.md

This file provides guidance to AI Agents when working with code in this
repository.

## Update rule

Update `AGENTS.md` when:

- You make significant changes that needs to be remembered across session.
- You made a mistake that should not be repeated.
- The user told you a new rule that should be remembered.

> Note: `CLAUDE.md` is a symlink to `AGENTS.md`.

## Repository purpose

A personal collection of refined, general-purpose `SKILL.md` files authored by Jei-sKappa. Each skill is a standalone, context-agnostic capability usable in any project or workflow — none of them assume a particular methodology, thread layout, or surrounding process. Skills are distributed via [skills.sh](https://skills.sh) and installed by end users with:

```sh
npx skills add Jei-sKappa/skills --skill <skill-name>
```
There is no build, test, or lint pipeline — this is a content repository. Validation happens by reading the markdown and confirming the skill's instructions are coherent and progressively disclosed.

## Layout

Skills live directly under `skills/`, grouped into four capability groups:

```
skills/
├── documentation/           take-snapshot
├── handoff/                 brief-the-recipient, consult-the-expert, report-to-the-owner
├── research/                afk-exploration, the-librarian
└── support/                 meta-prompting, name-cracker
```

Rules:

- Every skill lives at `skills/<group>/<skill-name>/SKILL.md`. The leaf directory name MUST match the `name:` field in the frontmatter.
- `README.md` — index of available skills; update when adding/removing a skill (use the full nested path in links).
- `.claude-plugin/marketplace.json` — registers this repo as a `vercel-labs/skills` plugin per `skills/` group, so installs are grouped under a named heading (e.g. `JeisKappa Handoff`, `JeisKappa Support`) instead of `General` in `npx skills list`. Every skill folder MUST be listed in the plugin matching its group's `skills` array as `./skills/<group>/<skill-name>`. To introduce a new group/heading, add a new folder under `skills/` AND add the matching plugin entry (`JeisKappa-<folder-name>`) to the `plugins` array. **Plugin order**: entries in `plugins` MUST be sorted alphabetically by `name`. Display rule: the CLI splits `name` on `-`, uppercases the first char of each segment, then joins with spaces — so `JeisKappa-handoff` renders as `JeisKappa Handoff`. Dashes cannot survive into the displayed title.

## SKILL.md format

Every skill file starts with YAML frontmatter, then the skill body. Mirror the structure of `skills/handoff/consult-the-expert/SKILL.md`:

```yaml
---
name: <kebab-case, matches directory name>
description: <one sentence: what it does + when to use it. The "use when…" trigger is what the harness matches against, so make it concrete.>
disable-model-invocation: true
metadata:
  author: https://github.com/Jei-sKappa
  version: <semver>
---
```

There is no specific format for the skill body: every skill is different.

New skills start at `version: 1.0.0`. Bump `version` in the frontmatter on any meaningful change to a skill's behavior.

## Invocation roles

Every skill in this repo is a user-invoked entry point — a capability a person deliberately reaches for. Each one carries `disable-model-invocation: true` in its `SKILL.md` frontmatter, and ships an `agents/openai.yaml` with a universal `interface:` block of Codex-style picker metadata (`display_name` — the skill name in title case — and `short_description`, a terse 4–7-word human-facing picker line, written fresh — never a copy of the `SKILL.md` `description`), plus a `policy.allow_implicit_invocation: false` block beneath it.

The two harness declarations must never diverge: a skill must never be user-only in one harness and implicitly invocable in the other. Whenever you add or edit a skill, set the `SKILL.md` key and the `agents/openai.yaml` policy together.

Still-valid authoring guidance for every skill body:

- Keep `description` to one sentence that says what the skill does and when to trigger it. Do not include history, taxonomy, sibling counts, version names, or implementation notes.
- Keep the body focused on instructions for the invoked agent. Do not add "when to use this skill" sections — routing belongs in the frontmatter description.
- When a skill body points at one of its own reference files, cite the full direct skill-relative path (e.g. `references/document-template.md`) — never an indirect description like "the `document-template.md` format under `references/`", and never a bare folder.
- Do not leak repo-maintenance context into the body: no project-internal planning labels, decision IDs, phase numbers, or explanations of how this repository is organized, unless the invoked agent genuinely needs that fact to do the skill's own job. If a constraint matters at runtime, restate it plainly as behavior the agent must follow.

## Describe the current state, never the diff

When an edit replaces design A with design B, the resulting skill body or document must describe B as if A had never existed. Never write a negation or before/after contrast whose only referent is the removed design — "X is no longer …", "there is no X anymore", "unlike before, …": once A is removed it is not materially written anywhere, so a fresh reader cannot know it existed, and the sentence's only effect is to teach a dead concept while reading as a changelog. Test every negative statement you keep or add: does it forbid something a fresh reader with no memory of the old design would plausibly do anyway? A live guardrail against natural drift ("never treat the sequence as a checklist", "add no owner field") passes the test; a contrast with a previous version of the text does not.

## Deliverable skills — no preamble

Skills whose job is to produce a deliverable for the user to copy, paste, or hand off elsewhere (currently: `meta-prompting`, `consult-the-expert`, `report-to-the-owner`, `brief-the-recipient`) must enforce that the chat response IS the deliverable. No "Sure, here is…", no chat-style framing, no closing remark like "Hope this helps." Encode the rule explicitly in the skill's Tone or Output format section so a fresh model session honors it without relying on the harness picking up convention.

## When adding a new skill

1. Decide which group the skill belongs to: `documentation`, `handoff`, `research`, or `support`. If none fits, propose a new group folder and document it in this file's Layout section in the same change.
2. Create `skills/<group>/<skill-name>/SKILL.md` with the frontmatter shown above (start at `version: 1.0.0`), as a user-invoked entry point: set `disable-model-invocation: true`. Ship `agents/openai.yaml` with a universal `interface:` block (`display_name` in title case, a fresh terse `short_description`) and add `policy.allow_implicit_invocation: false` beneath it. The two harness declarations must never diverge.
3. Add a section to `README.md` under the matching group heading with the description and the `npx skills add …` install snippet, linking to the full nested path.
4. Register the skill folder in `.claude-plugin/marketplace.json` under the plugin matching its group's `skills` array as `./skills/<group>/<skill-name>` — there is one plugin per group. Keep `plugins` sorted alphabetically by `name`. If the group is new, also add a new plugin entry named `JeisKappa-<folder-name>` in the same change.
5. Add the skill's folder name (the leaf, not the full path) to `conventionalCommits.scopes` in `.vscode/settings.json` (keep the array sorted alphabetically) so it shows up as a commit scope.

## Commits

Never commit unless explicitly asked to do so.

This repo follows [Conventional Commits](https://www.conventionalcommits.org/). When the change is scoped to a single skill, the commit scope MUST be that skill's folder name — e.g. `refactor(brief-the-recipient): …`, `fix(report-to-the-owner): …`. The list of valid skill scopes lives in `conventionalCommits.scopes` inside `.vscode/settings.json`; if a new skill exists on disk but is missing from that array, add it there in the same commit (see "When adding a new skill" above).

Repo-wide changes (touching multiple skills, `README.md`, `.claude-plugin/`, `AGENTS.md`, etc.) should omit the scope: `chore: …`, `docs: …`, `feat: …`.
