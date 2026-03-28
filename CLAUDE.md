# Claude Skills — Open-Source Plugin Marketplace

## Overview

This repository is an open-source Claude Code plugin marketplace maintained by [Avengers-au](https://github.com/Avengers-au). It contains distributable plugins — each with one or more skills — that any Claude Code user can install. The marketplace is registered in Claude Code via `/plugin marketplace add Avengers-au/claude-skills`, and individual plugins are installed via `/plugin install <plugin-name>@avengers-claude-skills`.

**This is the PUBLIC repo.** Everything here is MIT-licensed and visible to the world. Do NOT add credentials, API keys, internal Notion database IDs, org-specific configuration, or proprietary business logic. For internal/private skills, use `Avengers-au/startup-factory-cc-plugin` instead.

---

## Repository Structure

```
claude-skills/
├── CLAUDE.md                                    # This file — repo conventions and agent instructions
├── README.md                                    # Public-facing install/usage documentation
├── .claude-plugin/
│   └── marketplace.json                         # Marketplace manifest — registers all plugins
└── plugins/
    ├── share-gist/                              # Plugin: create secret GitHub gists
    │   ├── .claude-plugin/
    │   │   └── plugin.json                      # Plugin manifest (name, version, description, author)
    │   └── skills/
    │       └── gist/
    │           └── SKILL.md                     # Skill definition
    └── recruiter-playbook/                      # Plugin: recruiter screen prep
        ├── .claude-plugin/
        │   └── plugin.json                      # Plugin manifest
        ├── reference/
        │   └── recruiter-screen-playbook.md     # Bundled reference document
        └── skills/
            └── prep/
                └── SKILL.md                     # Skill definition
```

### Architecture: Marketplace → Plugins → Skills

This repo has a **three-level hierarchy**:

| Level | What It Is | File | Purpose |
|-------|-----------|------|---------|
| **Marketplace** | The repo itself | `.claude-plugin/marketplace.json` | Lists all available plugins. Users register this once |
| **Plugin** | A directory under `plugins/` | `plugins/<name>/.claude-plugin/plugin.json` | A self-contained, installable unit. Has its own manifest with name, version, description |
| **Skill** | A directory under a plugin's `skills/` | `plugins/<name>/skills/<skill>/SKILL.md` | The actual instructions Claude follows. One plugin can have multiple skills |

**Users interact at the plugin level** — they install plugins, not individual skills. Once a plugin is installed, all its skills become available.

**Invocation pattern:** `/plugin-name:skill-name` (e.g., `/share-gist:gist`, `/recruiter-playbook:prep`)

---

## How to Install This Marketplace

### For Users

```bash
# Step 1: Register the marketplace (one-time)
/plugin marketplace add Avengers-au/claude-skills

# Step 2: Install a specific plugin
/plugin install share-gist@avengers-claude-skills
/plugin install recruiter-playbook@avengers-claude-skills
```

### For the Avengers-au Org

The marketplace is pre-registered in `~/.claude/settings.json` under `extraKnownMarketplaces`:

```json
{
  "extraKnownMarketplaces": {
    "avengers-claude-skills": {
      "source": {
        "source": "github",
        "repo": "Avengers-au/claude-skills"
      }
    }
  }
}
```

With this in place, plugins are available immediately via `/plugin install <name>@avengers-claude-skills`.

---

## How to Add a New Plugin

Follow these steps exactly. Every plugin requires three things: a plugin manifest, at least one SKILL.md, and a marketplace registration.

### Step 1: Create the Directory Structure

```bash
mkdir -p plugins/<plugin-name>/.claude-plugin
mkdir -p plugins/<plugin-name>/skills/<skill-name>
```

**Naming conventions:**
- `<plugin-name>`: lowercase, hyphens only, descriptive (e.g., `share-gist`, `code-review`, `daily-digest`)
- `<skill-name>`: lowercase, hyphens only, can be shorter than plugin name (e.g., `gist`, `review`, `digest`)
- If the plugin has only one skill, the skill name can be a shorter alias of the plugin name
- Never use underscores, camelCase, or spaces

### Step 2: Create the Plugin Manifest

Write `plugins/<plugin-name>/.claude-plugin/plugin.json`:

```json
{
  "name": "<plugin-name>",
  "description": "<1-sentence description — what does this plugin do?>",
  "version": "1.0.0",
  "author": {
    "name": "Avengers-au",
    "url": "https://github.com/Avengers-au"
  },
  "homepage": "https://github.com/Avengers-au/claude-skills",
  "repository": "https://github.com/Avengers-au/claude-skills",
  "license": "MIT",
  "keywords": ["<keyword1>", "<keyword2>", "<keyword3>"]
}
```

**Required fields:** `name`, `description`, `version`, `author`

**Conventions from existing plugins:**
- `name` must match the directory name exactly
- `version` starts at `1.0.0` — use semantic versioning for updates
- `author.name` is `"Avengers-au"` for org-authored plugins
- `license` is always `"MIT"` (this is an open-source repo)
- `homepage` and `repository` both point to this repo
- `keywords` should be 3-5 relevant tags for discoverability

### Step 3: Write the SKILL.md

Write `plugins/<plugin-name>/skills/<skill-name>/SKILL.md`.

#### Frontmatter (YAML)

The frontmatter is **critical** — it controls when and how the skill is invoked.

```yaml
---
name: <skill-name>
description: >-
  <Trigger description. MUST be specific about when to invoke. Include exact
  phrases the user might say. This field controls auto-invocation — vague
  descriptions mean the skill never fires automatically.>
user-invocable: true
allowed-tools: <optional tool restrictions>
argument-hint: <optional usage hint>
---
```

**Frontmatter field reference:**

| Field | Required | Type | Purpose | Example |
|-------|----------|------|---------|---------|
| `name` | Yes | string | Skill slug — used in `/plugin:skill` invocation | `gist`, `prep`, `review` |
| `description` | Yes | string | **CRITICAL**: Controls auto-invocation. Include explicit trigger phrases the user might say. Be exhaustive — list 5-10 trigger phrases | See examples below |
| `user-invocable` | No | boolean | Whether the user can invoke directly. Default `true` | `true` |
| `allowed-tools` | No | string | Restricts which tools the skill can use. Comma-separated. Omit for unrestricted access | `Bash(gh *), Read`, `Bash, Read, Write` |
| `argument-hint` | No | string | Shows expected arguments in help output | `<file-path> [description]` |
| `disable-model-invocation` | No | boolean | Set `true` to prevent auto-trigger (for destructive skills like deploy/delete) | `true` |
| `context` | No | string | Set `fork` to run in an isolated subagent with its own context | `fork` |

**Writing good descriptions (the most important field):**

The `description` field is NOT documentation — it is the **invocation trigger**. Claude Code reads this to decide whether to auto-invoke the skill when the user says something. Bad descriptions mean the skill never fires.

```yaml
# BAD — too vague, will rarely auto-trigger
description: Helps with GitHub gists.

# GOOD — explicit trigger phrases, clear scope
description: >-
  Create a secret GitHub gist from a file and return a shareable URL. Use when
  the user says "create a gist", "share this as a gist", "gist this file",
  "get a shareable link", "share this document", or wants to share a file with
  someone who doesn't have access to the private repo.
```

**Tool restrictions (`allowed-tools`):**

Restricting tools is a security measure. If a skill only needs `gh` CLI access, restrict it:

```yaml
# Only allow gh CLI commands
allowed-tools: Bash(gh *)

# Allow gh CLI + file reading
allowed-tools: Bash(gh *), Read

# Allow web research + file operations + gh
allowed-tools: Bash(gh *), Read, WebSearch, WebFetch

# Unrestricted — omit the field entirely
```

#### Body (Markdown)

The body contains the instructions Claude follows when the skill is invoked. Write it like you're giving instructions to a capable but literal-minded engineer.

**Structure pattern (from existing plugins):**

```markdown
# <Descriptive Title>

<1-2 sentence summary of what this skill does and why.>

## Arguments

- `$0` — <first argument> (required/optional). <What it is.>
- `$1` — <second argument> (optional). <What it is.>

## Steps

### 1. <Validate inputs>
<Check preconditions, verify tools are installed, validate arguments>

### 2. <Do the main work>
<Core logic with exact commands in code blocks>

### 3. <Produce output>
<Format and deliver results to the user>

## Error Handling

| Error | Response |
|-------|----------|
| <condition> | <what to tell the user / what to do> |

## Rules

1. <Constraint or quality rule>
2. <Another constraint>
```

**Quality rules for SKILL.md bodies:**

- **Be concrete**: Include exact commands in code blocks with language identifiers, not "run the appropriate command"
- **Include error handling**: What happens when `gh` isn't installed? When the file doesn't exist? When the API returns an error?
- **Include validation**: Check preconditions before acting (tool installed, file exists, auth configured)
- **Reference tools by name**: Use `Bash`, `Read`, `Write`, `WebSearch`, `WebFetch` — these are Claude Code tool names
- **Quantify expectations**: "Keep it under 90 seconds" not "Keep it brief"
- **No org-specific references**: No Notion database IDs, no internal URLs, no team-specific tooling. This is public

### Step 4: Add Reference Files (Optional)

If the skill needs bundled reference documents (like `recruiter-playbook` bundles a research doc), place them in a `reference/` directory inside the plugin:

```
plugins/<plugin-name>/
├── .claude-plugin/plugin.json
├── reference/
│   └── some-reference-doc.md     # Bundled docs the skill can read
└── skills/
    └── <skill-name>/SKILL.md
```

**IMPORTANT:** Reference files must be self-contained. The skill's SKILL.md must include instructions for finding the file — either by searching the local filesystem or fetching from the GitHub API:

```bash
# Find locally (after plugin install)
find ~/.claude -name "reference-doc.md" -path "*/<plugin-name>/*" 2>/dev/null | head -1

# Fetch from GitHub (fallback)
gh api repos/Avengers-au/claude-skills/contents/plugins/<plugin-name>/reference/reference-doc.md --jq '.content' | base64 -d
```

### Step 5: Register in marketplace.json

Edit `.claude-plugin/marketplace.json` — add an entry to the `plugins` array:

```json
{
  "name": "<plugin-name>",
  "source": "./plugins/<plugin-name>",
  "description": "<same 1-sentence description as plugin.json>"
}
```

**Rules:**
- `name` must match the plugin directory name AND the `name` in `plugin.json`
- `source` is always `./plugins/<plugin-name>` (relative path from repo root)
- `description` should match or closely paraphrase the description in `plugin.json`
- Add new entries at the END of the array (maintain chronological order)

### Step 6: Update README.md

Add a section for the new plugin following the existing pattern:

```markdown
### `<plugin-name>` — <Short tagline>

<2-3 sentence description of what it does and why it's useful.>

**Install:**
\```
/plugin install <plugin-name>@avengers-claude-skills
\```

**Use:**
\```
/<plugin-name>:<skill-name> <arguments>
\```

**What it does:**
- <Bullet 1 — key feature>
- <Bullet 2 — key feature>
- <Bullet 3 — key feature>

**Requirements:** <prerequisites, e.g., `gh` CLI>
```

### Step 7: Test Locally

```bash
cd ~/workplace/claude-skills
claude --plugin-dir ./plugins/<plugin-name>
```

Then invoke the skill with `/<skill-name>` and verify:
- The skill triggers correctly (auto-invocation and manual `/skill-name`)
- All steps execute without errors
- Output is formatted correctly
- Error handling works (try invalid inputs)

### Step 8: Commit and Push

```bash
cd ~/workplace/claude-skills
git add plugins/<plugin-name>/ .claude-plugin/marketplace.json README.md
git commit -m "Add <plugin-name> plugin — <short description>"
git push origin main
```

**Commit message conventions:**
- Start with `Add` for new plugins, `Update` for changes, `Fix` for bugs
- Include the plugin name
- Brief description after the dash
- One plugin per commit when adding new plugins

---

## Current Plugins

| Plugin | Skill(s) | Description | Version |
|--------|----------|-------------|---------|
| `share-gist` | `gist` | Create secret GitHub gists from files | 1.0.0 |
| `recruiter-playbook` | `prep` | Generate company-specific recruiter screening playbooks with live research | 1.0.0 |
| `hm-screen-playbook` | `prep` | Generate company-specific hiring manager screening playbooks with CARL templates | 1.0.0 |
| `tech-screen-playbook` | `prep` | Generate category-aware technical phone screen playbooks (10 job categories) | 1.0.0 |
| `career-kb-builder` | `build` | Conversationally extract career data into a structured knowledge base | 1.0.0 |
| `resume-linkedin-optimiser` | `optimise` | Generate ATS-optimised resumes and LinkedIn recommendations from career KB + JD | 1.0.0 |
| `star-story-generator` | `generate` | Transform career KB into company-specific CARL stories with coverage analysis | 1.0.0 |
| `behavioural-interview-playbook` | `prep` | Behavioural round prep with live research, bias strategy, company-specific easy outs | 1.0.0 |
| `onsite-loop-playbook` | `prep` | Onsite/loop technical prep with system design, coding, debrief prediction | 1.0.0 |

---

## File Reference

### `.claude-plugin/marketplace.json`

The marketplace manifest. This is the entry point that Claude Code reads when a user registers the marketplace. It lists all available plugins with their source paths.

```json
{
  "name": "avengers-claude-skills",
  "owner": {
    "name": "Avengers-au",
    "url": "https://github.com/Avengers-au"
  },
  "description": "Open-source Claude Code skills from Avengers-au",
  "homepage": "https://github.com/Avengers-au/claude-skills",
  "plugins": [
    {
      "name": "<plugin-name>",
      "source": "./plugins/<plugin-name>",
      "description": "<description>"
    }
  ]
}
```

**Fields:**
- `name`: Marketplace identifier — used in `/plugin install <plugin>@<marketplace-name>`
- `owner`: Organisation info displayed in plugin listings
- `plugins[]`: Array of available plugins. Each has `name`, `source` (relative path), and `description`

### `plugins/<name>/.claude-plugin/plugin.json`

Per-plugin manifest. Contains metadata about a single installable plugin.

### `plugins/<name>/skills/<skill>/SKILL.md`

The actual skill definition. YAML frontmatter + Markdown body. This is what Claude reads and follows when the skill is invoked.

### `plugins/<name>/reference/` (optional)

Bundled reference documents that a skill can read at runtime. Used when a skill needs access to static content (e.g., the recruiter-playbook bundles a comprehensive research document).

---

## Conventions and Rules

### What Belongs Here (Public Repo)

- Generic utility skills that any Claude Code user could benefit from
- Skills that wrap public tools and APIs (`gh`, `curl`, public web APIs)
- Skills that produce or transform content without requiring org-specific context
- Reference documents that are useful to a general audience

### What Does NOT Belong Here

- Skills that reference internal Notion databases, data source IDs, or private APIs
- Skills that contain credentials, tokens, or secrets
- Skills that are only useful to the Avengers-au team internally
- Proprietary business logic or internal workflows
- Skills that perform destructive operations without safeguards

**For internal/private skills**, use `Avengers-au/startup-factory-cc-plugin` instead.

### Code Quality

- Every SKILL.md must include an **Error Handling** section
- Every skill that uses external tools must **validate prerequisites** (is `gh` installed? is the user authenticated?)
- Every skill must have a **clear, exhaustive trigger description** in the frontmatter
- All code blocks must include **language identifiers** (```bash, ```json, etc.)
- No hardcoded paths — use `find` or environment variables for discovery
- Test locally with `claude --plugin-dir` before pushing

### Versioning

- Use semantic versioning in `plugin.json`: `MAJOR.MINOR.PATCH`
- `MAJOR`: Breaking changes to skill behaviour or arguments
- `MINOR`: New features, new skills added to an existing plugin
- `PATCH`: Bug fixes, documentation improvements
- Bump version in `plugin.json` when making changes to existing plugins

### Git Workflow

- Work on `main` branch directly (no feature branches required for this repo)
- One plugin per commit when adding new plugins
- Group related changes (e.g., fixing a bug in SKILL.md + updating README) in a single commit
- Always push to `origin main` after committing

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Plugin not showing after install | Run `/plugin marketplace add Avengers-au/claude-skills` to re-register, then `/plugin install <name>@avengers-claude-skills` |
| Skill doesn't auto-trigger | Check the `description` field in SKILL.md frontmatter — it must include the exact phrases the user says |
| Skill triggers but fails | Check `allowed-tools` — if set, the skill can only use those tools. Ensure required tools are listed |
| `gh` commands fail | User needs `gh` CLI installed (`https://cli.github.com`) and authenticated (`gh auth login`) |
| Reference files not found | Use the `find` + `gh api` fallback pattern documented in the skill's Step 1 |
| Changes not reflected after push | Users need to update: `/plugin marketplace add Avengers-au/claude-skills` re-fetches the latest |
| Plugin loads but skill is missing | Check that the skill directory matches the pattern: `plugins/<plugin>/skills/<skill>/SKILL.md` |
| marketplace.json syntax error | Validate with `jq . .claude-plugin/marketplace.json` — invalid JSON silently breaks all registrations |
