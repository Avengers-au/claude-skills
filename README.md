# claude-skills

Open-source Claude Code skills from [Avengers-au](https://github.com/Avengers-au).

## Installation

Add this repo as a Claude Code marketplace, then install any plugin:

```bash
/plugin marketplace add Avengers-au/claude-skills
```

---

## Available Plugins

### `share-gist` — Create secret GitHub gists

Create a secret (unlisted) GitHub gist from any file and get a shareable URL — without exposing your private repo.

**Install:**
```
/plugin install share-gist@avengers-claude-skills
```

**Use:**
```
/share-gist:gist path/to/file.md
/share-gist:gist path/to/file.md "Optional description"
```

**What it does:**
- Creates a secret gist via `gh gist create` (unlisted, not indexed by search)
- Auto-extracts the document title from the H1 heading as the gist description
- Returns the URL and copies it to your clipboard
- Works with any text file — markdown, code, plain text

**Requirements:** [`gh` CLI](https://cli.github.com) installed and authenticated (`gh auth login`)

> **Note:** Secret gists are *unlisted*, not private. Anyone with the URL can view the content.
> Do not use for credentials or sensitive information.

---

## Structure

This repo is a Claude Code plugin marketplace. Adding plugins in future:

```
plugins/
├── share-gist/      ← Current plugin
└── your-plugin/     ← Add new plugins here
```

To add a new plugin, create a directory under `plugins/` with a `.claude-plugin/plugin.json` manifest and a `skills/` directory, then add it to `.claude-plugin/marketplace.json`.

## Contributing

PRs welcome. Each plugin lives in its own directory under `plugins/` and must include:

- `.claude-plugin/plugin.json` — plugin name, version, description
- `skills/<name>/SKILL.md` — skill instructions with YAML frontmatter

## License

MIT
