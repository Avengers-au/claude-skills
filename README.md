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

### `hm-screen-playbook` — Hiring manager screen prep with live research

Generate a personalised, company-specific hiring manager screening playbook. The HM screen is the 45-60 minute gate after the recruiter call — evaluating technical depth, team fit, career goals, leadership, and judgment. This plugin researches the company and (optionally) the hiring manager, then produces a tactical briefing with CARL story templates, reverse interview questions, and social engineering angles.

**Install:**
```
/plugin install hm-screen-playbook@avengers-claude-skills
```

**Use:**
```
/hm-screen-playbook:prep Google
/hm-screen-playbook:prep Anthropic "Dr. Bob Jones"
/hm-screen-playbook:prep Stripe "Jane Smith" "Senior Backend Engineer"
```

**What it does:**
- Researches the company's values, recent news, engineering blog, and Glassdoor HM interview reviews
- If the HM name is provided, finds their conference talks, blog posts, open-source work, and management philosophy
- Generates company-tailored CARL (Context-Actions-Results-Learnings) story templates for the 5 most likely questions
- Produces scripts for "Where do you see yourself?", "Why are you leaving?", "What's your weakness?"
- Creates 5 tailored reverse interview questions referencing specific company details
- Maps the 8 HM evaluation dimensions to this company's priorities
- Outputs as a secret GitHub gist you can pull up on your phone before the call

**Includes:** A bundled reference playbook covering evaluation rubrics, the HM's hidden agenda, psychological biases to leverage, and company-category adaptation for FAANG, startups, enterprise, mission-driven, defence, and AI/ML companies.

**Requirements:** [`gh` CLI](https://cli.github.com) installed and authenticated (`gh auth login`)

### `tech-screen-playbook` — Technical phone screen prep by job category

Generate a personalised, category-aware technical phone screen playbook. Covers 10 job categories — Backend, Frontend, Security/AppSec, Data Engineering, ML/AI, Infra/DevOps/SRE, Mobile, Full-Stack, Cloud Architecture, and Embedded Systems — each with category-specific domains, question types, and level expectations. Researches the company's tech stack, interview format, and recent Glassdoor reports.

**Install:**
```
/plugin install tech-screen-playbook@avengers-claude-skills
```

**Use:**
```
/tech-screen-playbook:prep Google Backend
/tech-screen-playbook:prep CrowdStrike Security "Senior Security Engineer"
/tech-screen-playbook:prep Stripe "Full-Stack" "Staff Engineer"
```

**What it does:**
- Determines the interview format (CoderPad, HackerRank, take-home, pair programming) from Glassdoor
- Researches the company's tech stack and engineering culture
- Pulls the relevant category breakdown (e.g., Security: OWASP Top 10, STRIDE, crypto, cloud security, IR)
- Lists the most likely questions based on Glassdoor reports and company focus areas
- Provides level-specific expectations (mid vs senior vs staff)
- Generates a practice plan with specific resources and time estimates
- Outputs as a secret GitHub gist

**Includes:** A bundled reference playbook with universal framework (rubrics from 100K+ interviews, meta-skills, time management) and deep breakdowns for all 10 job categories.

**Requirements:** [`gh` CLI](https://cli.github.com) installed and authenticated (`gh auth login`)

---

## Structure

This repo is a Claude Code plugin marketplace.

```
plugins/
├── share-gist/            ← Secret gist creation
├── recruiter-playbook/    ← Recruiter screen prep
├── hm-screen-playbook/    ← Hiring manager screen prep
├── tech-screen-playbook/  ← Technical phone screen prep (category-aware)
└── your-plugin/           ← Add new plugins here
```

To add a new plugin, create a directory under `plugins/` with a `.claude-plugin/plugin.json` manifest and a `skills/` directory, then add it to `.claude-plugin/marketplace.json`.

## Contributing

PRs welcome. Each plugin lives in its own directory under `plugins/` and must include:

- `.claude-plugin/plugin.json` — plugin name, version, description
- `skills/<name>/SKILL.md` — skill instructions with YAML frontmatter

## License

MIT
