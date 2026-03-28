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

### `recruiter-playbook` — Recruiter screen prep with live research

Generate a personalised, company-specific recruiter screening playbook. Conducts live research on the company's values, recent news, engineering blog, Glassdoor reviews, and salary data — then produces a tactical briefing with tailored scripts, company-specific language mapping, and social engineering angles.

**Install:**
```
/plugin install recruiter-playbook@avengers-claude-skills
```

**Use:**
```
/recruiter-playbook:prep Google
/recruiter-playbook:prep Anthropic "Jane Smith" "Dr. Bob Jones"
```

**What it does:**
- Researches the company's values, tenets, and leadership principles
- Finds recent news, engineering blog posts, and Glassdoor interview reviews
- Maps company values to natural conversation phrases
- Generates tailored scripts for "Tell me about yourself", "Why this company?", salary deflection
- If recruiter/hiring manager names are provided, gathers LinkedIn and public profile intelligence
- Outputs the playbook as a secret GitHub gist you can pull up on your phone before the call

**Includes:** A bundled reference playbook with proven frameworks covering FAANG, startups, enterprise, mission-driven, defence, and AI/ML company categories.

**Requirements:** [`gh` CLI](https://cli.github.com) installed and authenticated (`gh auth login`)

---

## Structure

This repo is a Claude Code plugin marketplace.

```
plugins/
├── share-gist/            ← Secret gist creation
├── recruiter-playbook/    ← Recruiter screen prep
└── your-plugin/           ← Add new plugins here
```

To add a new plugin, create a directory under `plugins/` with a `.claude-plugin/plugin.json` manifest and a `skills/` directory, then add it to `.claude-plugin/marketplace.json`.

## Contributing

PRs welcome. Each plugin lives in its own directory under `plugins/` and must include:

- `.claude-plugin/plugin.json` — plugin name, version, description
- `skills/<name>/SKILL.md` — skill instructions with YAML frontmatter

## License

MIT
