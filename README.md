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

### `career-kb-builder` — Build your career knowledge base through conversation

A conversational career coach that interviews you to extract, structure, and store your career achievements as a structured knowledge base file. Surfaces hidden achievements, helps quantify impact, and maps stories to interview competencies. The output feeds into all other interview prep plugins.

**Install:**
```
/plugin install career-kb-builder@avengers-claude-skills
```

**Use:**
```
/career-kb-builder:build
```

**What it does:**
- Walks through your career chronologically, then deep-dives into key stories
- Uses professional coaching techniques to surface achievements you'd overlook
- Helps quantify impact using 6 estimation techniques (range, frequency multiplication, cost translation, scale indicators, comparison anchors, proxy metrics)
- Structures output with competency tags mapped to Amazon LPs, Meta dimensions, Google attributes, etc.
- Generates compressed resume bullets and LinkedIn versions for each story
- Outputs a local structured markdown file — your personal career knowledge base

**Includes:** A bundled reference guide covering the extraction schema, probing techniques, quantification methods, and quality checklist.

### `resume-linkedin-optimiser` — ATS-optimised resume and LinkedIn profile generation

Generate a tailored, ATS-optimised resume and LinkedIn profile recommendations from your career knowledge base and a target job description. Every bullet is story-seeded — designed to invite interviewers to ask about your strongest achievements.

**Install:**
```
/plugin install resume-linkedin-optimiser@avengers-claude-skills
```

**Use:**
```
/resume-linkedin-optimiser:optimise
```

**What it does:**
- Analyses the target job description to extract keywords, required skills, and priority order
- Matches your career KB stories to JD requirements and selects the strongest bullets
- Applies action verb upgrades (eliminating "Responsible for", "Worked on", etc.)
- Mirrors JD language naturally (1-3 keyword occurrences, not stuffing)
- Generates a story-seeded resume where every bullet invites "Tell me more"
- Produces LinkedIn headline (R-S-I-C formula for 2.4x more recruiter replies), About section, and skills recommendations
- Runs ATS compliance checks (formatting, headings, keyword coverage)
- Outputs local files — resume and LinkedIn recommendations

**Includes:** A bundled reference guide covering ATS reality vs myths (2025 survey data), action verbs by competency, LinkedIn algorithm mechanics, and the story seeding technique.

### `star-story-generator` — Company-specific CARL story generation

Transform your career knowledge base into company-specific, level-appropriate CARL stories. Maps your achievements to the target company's competency framework, generates rehearsal-ready answers with scope calibration, and produces a coverage matrix showing gaps.

**Install:**
```
/plugin install star-story-generator@avengers-claude-skills
```

**Use:**
```
/star-story-generator:generate Amazon Senior
/star-story-generator:generate Meta IC5
/star-story-generator:generate Anthropic "Staff Security Engineer"
```

**What it does:**
- Reads your career knowledge base and maps stories to the target company's framework (Amazon 16 LPs, Meta 8 dimensions, Google Googleyness + Leadership, Stripe values, Netflix F&R, Anthropic safety alignment)
- Generates full CARL answers (Context/Actions/Results/Learnings) with company-specific framing
- Calibrates scope signalling to the target level (L3→individual task, L5→team project, L6→cross-team initiative)
- Produces a coverage matrix showing which competencies are covered and which have gaps
- Includes follow-up prep for each story ("Why?", "What else?", "What would you change?")
- Shows how to repurpose each story for 2-3 different competency questions
- Outputs local markdown file with all stories and the coverage report

**Includes:** A bundled reference guide covering CARL framework, Decode-Select-Deliver methodology, 15 competency clusters, company competency mappings, scope ladder, story repurposing, and naturalness techniques.

### `behavioural-interview-playbook` — Behavioural round prep with live company research

Generate a personalised behavioural interview playbook that combines proven frameworks with LIVE research on the specific company's current process. Maps your CARL stories to the company's competency framework, applies cognitive bias strategy (anchoring, halo effect, peak-end rule), and produces company-specific easy outs calibrated to their culture.

**Install:**
```
/plugin install behavioural-interview-playbook@avengers-claude-skills
```

**Use:**
```
/behavioural-interview-playbook:prep Amazon L5
/behavioural-interview-playbook:prep Meta IC6 "Staff Security Engineer"
/behavioural-interview-playbook:prep Anthropic
```

**What it does:**
- Conducts LIVE research on the company's current behavioural framework (Glassdoor reports, careers page, recent candidate experiences) — never relies solely on the base guide
- Maps your career KB stories to the company's specific competencies (Amazon 16 LPs, Meta 5 signal areas, Google Googleyness, Stripe values, Netflix culture traits, Anthropic safety alignment)
- Generates a cognitive bias strategy: which story opens (anchoring), which closes (peak-end), narrative arc across the round
- Produces company-calibrated easy outs (weakness, failure, conflict — tailored to what THIS company values)
- Identifies coverage gaps and suggests how to fill them
- Adapts expectations by role category (security, frontend, ML, infra, management)
- Sources every claim with links to Glassdoor reports, blog posts, and careers pages

**Includes:** A bundled reference playbook covering company frameworks with real candidate-reported questions, cognitive bias research (69% decide in 5 minutes — University of Toledo), naturalness techniques (Stanislavski method), role-category differences, and 2025-2026 trend adaptation.

**Requirements:** [`gh` CLI](https://cli.github.com) installed and authenticated (`gh auth login`). Career KB or STAR stories file (from `/career-kb-builder` and `/star-story-generator`).

---

## Structure

This repo is a Claude Code plugin marketplace.

```
plugins/
├── share-gist/                 ← Secret gist creation
├── recruiter-playbook/         ← Recruiter screen prep
├── hm-screen-playbook/         ← Hiring manager screen prep
├── tech-screen-playbook/       ← Technical phone screen prep (category-aware)
├── career-kb-builder/          ← Career knowledge base builder
├── resume-linkedin-optimiser/  ← Resume & LinkedIn optimisation
├── star-story-generator/               ← STAR/CARL story generation
├── behavioural-interview-playbook/    ← Behavioural round prep (live research)
└── your-plugin/                       ← Add new plugins here
```

To add a new plugin, create a directory under `plugins/` with a `.claude-plugin/plugin.json` manifest and a `skills/` directory, then add it to `.claude-plugin/marketplace.json`.

## Contributing

PRs welcome. Each plugin lives in its own directory under `plugins/` and must include:

- `.claude-plugin/plugin.json` — plugin name, version, description
- `skills/<name>/SKILL.md` — skill instructions with YAML frontmatter

## License

MIT
