---
name: prep
description: >-
  Use this skill when the user wants to prepare for a hiring manager screening call.
  Trigger on "hiring manager screen", "HM screen", "HM call", "manager interview",
  "hiring manager prep", "prepare me for a hiring manager call", "I have a call with
  the hiring manager", "help me prep for the HM round", or any request to generate a
  personalised hiring manager screening playbook for a specific company.
user-invocable: true
allowed-tools: Bash(gh *), Read, WebSearch, WebFetch
argument-hint: <company-name> [hiring-manager-name] [role-title]
---

# Hiring Manager Screen Playbook Generator

Generate a personalised, company-specific hiring manager screening playbook. This is
the screen AFTER the recruiter call — typically 45-60 minutes with the actual hiring
manager or engineering manager, evaluating technical depth, team fit, career goals,
leadership, and judgment.

## Required Inputs

- **Company name** (required): The company the user is interviewing with

## Optional Inputs

- **Role title**: The specific role (e.g., "Senior Backend Engineer"). Infer from context if not stated.
- **Hiring manager name**: If known, enables deep social engineering section
- **Recruiter name**: If known, for continuity reference
- **Role level**: Junior / Mid / Senior / Staff / Principal. Infer from context if possible.

## Research Phase

Before generating the playbook, conduct thorough research. **You MUST actually search — do not rely on training data alone.**

### Step 1: Read the base playbook

Read the reference playbook bundled with this plugin. It is located at `reference/hiring-manager-screen-playbook.md` relative to this plugin's root directory.

To find the plugin's installation path, search for the file:

```bash
find ~/.claude -name "hiring-manager-screen-playbook.md" -path "*/hm-screen-playbook/*" 2>/dev/null | head -1
```

If not found locally, fetch it from the source repo:

```bash
gh api repos/Avengers-au/claude-skills/contents/plugins/hm-screen-playbook/reference/hiring-manager-screen-playbook.md --jq '.content' | base64 -d
```

This reference doc contains the CARL framework, 8 evaluation dimensions, HM's hidden agenda, proven scripts, company-category adaptation, and social engineering tactics. Use it as the foundation.

### Step 2: Company research (mandatory)

Use `WebSearch` and `WebFetch` to find:

1. **Company values / tenets / leadership principles** — Search for "[company] values", "[company] leadership principles", "[company] culture". Find the EXACT language from their careers page.
2. **Recent news** (last 90 days) — Search "[company] news", "[company] funding", "[company] product launch"
3. **Engineering blog** — Search "[company] engineering blog" or "[company] tech blog". Read the 2-3 most recent posts.
4. **Glassdoor HM interview reviews** — Search "[company] hiring manager interview glassdoor" for recent reports on what HMs ask
5. **Company category** — Determine: FAANG/Big Tech, High-growth startup, Enterprise/traditional, Mission-driven, Defence/security, AI/ML. This determines adaptation strategy.
6. **Team-specific info** — Search for the team/org mentioned in the job description.

### Step 3: Hiring manager research (if name provided)

If the **hiring manager's name** is provided, this is the most valuable research:
- Search LinkedIn: "[name] [company] linkedin"
- Search for conference talks: "[name] conference talk", "[name] [conference-name]"
- Search for blog posts: "[name] blog post", "[name] [company] engineering blog"
- Search for podcasts: "[name] podcast"
- Search GitHub: "[name] github" for open-source contributions
- Note: technical opinions, management philosophy, projects they're proud of, career trajectory
- Identify shared connections, alma mater, previous employers, or technical interests

### Step 4: Salary/level research

- Search Levels.fyi: "[company] [role] [level] compensation levels.fyi"
- Determine the likely level and what "scope" looks like at that level

## Output Format

Generate the playbook as a **markdown file** and publish it as a **secret GitHub gist**.

1. Write the playbook to a temp file: `/tmp/hm-screen-playbook-[company].md`
2. Create a gist: `gh gist create /tmp/hm-screen-playbook-[company].md -d "HM Screen Playbook: [Company Name]"`
3. Copy the URL to clipboard: `echo "$URL" | pbcopy 2>/dev/null`
4. Return the gist URL to the user

### Playbook structure

The generated markdown file MUST follow this structure:

```markdown
# HM Screen Playbook: [Company Name]

## Company Intel
[2-3 paragraphs: what the company does, category, recent news, strategic focus. Be specific.]

## Hiring Manager Intel
[If name provided: background, talks, blog posts, technical opinions, management style, projects to reference, shared connections. If not: general notes on what HMs at this company focus on from Glassdoor.]

## What This HM Will Evaluate
[Based on company category and Glassdoor reviews, list the specific dimensions this HM is likely to score on. Map to the 8 evaluation dimensions from the base playbook.]

## Company Values & Language Map
| Value/Tenet | What It Means | Phrases to Weave In |
|-------------|---------------|---------------------|
| [Value 1] | [Explanation] | "[Natural sentence]" |

## Your CARL Stories — Tailored
[For each of the top 5 likely questions at this company, provide a CARL story template with placeholders. Tailor the framing to this company's values.]

### Story 1: Technical Challenge
**Likely question:** "Walk me through a technically challenging project"
**Framing for [Company]:** [Company-specific angle]
**CARL template:**
- Context: [YOUR CONTEXT — include scale numbers]
- Actions: [YOUR ACTIONS — must be plural, specific to you]
- Results: [YOUR RESULTS — quantified]
- Learnings: [WHAT YOU'D DO DIFFERENTLY]

### Story 2: Conflict/Disagreement
### Story 3: Leadership Without Authority
### Story 4: Failure/Mistake
### Story 5: Ambiguity/Changing Priorities

## Scripts

### "Where do you see yourself in 2-3 years?"
[Tailored to growth paths available at this company.]

### "Why are you leaving your current role?"
[Framed as a pull toward what THIS company specifically offers]

### "What's your biggest weakness?"
[Calibrated for this company's culture]

## Reverse Interview Questions
[5 tailored questions referencing specific recent news, blog posts, or team details.]

## Red Flags to Avoid
[Company-specific red flags based on their values and culture.]

## Social Engineering Playbook
[Specific rapport-building hooks for this company/HM.]

## Pre-Screen Checklist
[Tailored checklist with company-specific items filled in.]

## Sources
[Links to all resources referenced.]
```

## Rules

1. **Always research live** — Do not generate from training data alone. Current, specific information is the value.
2. **Be concrete, not generic** — Every section must be specific to THIS company.
3. **CARL stories need company-specific framing** — Same story framed differently for Amazon (customer obsession) vs Anthropic (safety/judgment) vs startups (speed/ownership).
4. **HM intel is highest-value** — If the HM name is provided, invest the most research time here.
5. **Calibrate formality** — Startups casual, enterprise formal, AI labs intellectually curious.
6. **Include sources** — Link to every resource referenced.
7. **Distinguish from recruiter playbook** — This is a DEEPER conversation. 45-60 minutes of substantive discussion, not surface screening.
8. **Output as a secret GitHub gist** — Write to temp file, create with `gh gist create`, return URL. Requires `gh` CLI.

## Error Handling

| Error | Response |
|-------|----------|
| `gh` not installed | Direct to https://cli.github.com |
| `gh` not authenticated | Tell user to run `gh auth login` |
| Company not found in searches | Fall back to training data, note which sections are general vs. researched |
| HM name returns no results | State honestly, skip that section |
| Levels.fyi has no data | Provide market benchmarks instead |
