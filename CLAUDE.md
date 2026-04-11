# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About

A personal Claude Code plugin marketplace — a curated collection of reusable Claude Code skills (slash commands).

## Structure

Skills live in `skills/<skill-name>/SKILL.md`. Each `SKILL.md` has YAML frontmatter followed by the skill instructions.

### SKILL.md frontmatter fields

| Field | Notes |
|---|---|
| `name` | Lowercase, hyphens only, max 64 chars. Defaults to directory name. |
| `description` | How Claude decides when to auto-trigger. Max ~250 chars; front-load the trigger phrase. |
| `disable-model-invocation` | Set `true` for skills with side effects (deploys, commits) — Claude cannot auto-trigger. |
| `user-invocable` | Set `false` to hide from `/` menu; Claude can still auto-trigger. |
| `allowed-tools` | Space-separated list of tools available without prompting. |
| `context: fork` | Run in isolated subagent; requires `agent` field. |
| `agent` | Subagent type: `Explore`, `Plan`, `general-purpose`. |
| `model` | Override session model for this skill. |

### Dynamic content

- `` !`command` `` — shell output injected before Claude sees the prompt
- `$ARGUMENTS`, `$0`, `$1` — user-supplied arguments
- `${CLAUDE_SKILL_DIR}` — absolute path to the skill directory

## Conventions

- When adding a skill, add a one-line entry to the `## Skills` section in `README.md`
- Keep `SKILL.md` under 500 lines; move reference material to sibling files in the skill directory

## Adding a new skill

1. Create `skills/<skill-name>/SKILL.md` with YAML frontmatter and instructions
2. Add reference files to `skills/<skill-name>/references/` if needed
3. Add a one-line entry to `README.md` under `## Skills`
4. Add an entry to `.claude-plugin/marketplace.json` under `"plugins"`
5. Commit and push
