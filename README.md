# skills

Personal Claude Code plugin marketplace.

## Installation

Run inside Claude Code:

```
/plugin marketplace add p3l1/skills
/plugin install skills@p3l1-skills
```

Or manually add to `~/.claude/settings.json`:

```json
{
  "enabledPlugins": {
    "skills@skills": true
  },
  "extraKnownMarketplaces": {
    "skills": {
      "source": {
        "source": "github",
        "repo": "p3l1/skills"
      }
    }
  }
}
```

## Skills

| Skill | Description |
|---|---|
| `/obsidian-cli` | Interact with an Obsidian vault — read/write notes, search, manage tasks, and more |
| `/german` | Write and translate professional German business communication |
| `/commit` | Create GPG-signed git commits using conventional commits |
