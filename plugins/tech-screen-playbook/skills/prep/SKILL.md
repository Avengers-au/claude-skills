---
name: tech-screen-playbook
description: >-
  Use this skill when the user wants to prepare for a technical phone screen or
  coding interview. Trigger on "technical phone screen", "tech screen", "coding
  interview", "CoderPad interview", "HackerRank interview", "live coding prep",
  "prepare me for a technical screen at [company]", "security engineer interview",
  "frontend interview prep", "backend coding interview", or any request to generate
  a personalised technical phone screen playbook for a specific company and role category.
---

# Technical Phone Screen Playbook Generator

Generate a personalised, category-aware technical phone screen playbook. This is the
live coding/technical assessment — typically 45-60 minutes where you demonstrate you
can actually do the work. The playbook is tailored to both the company AND the specific
job category (backend, frontend, security, data, ML, infra, mobile, etc.).

## Required Inputs

- **Company name** (required): The company interviewing you
- **Job category** (required — infer from context if not stated): One of:
  - Backend / Server-Side
  - Frontend / UI
  - Security / AppSec / Cybersecurity
  - Data Engineering
  - ML/AI Engineering
  - Infrastructure / DevOps / SRE
  - Mobile (iOS / Android)
  - Full-Stack
  - Cloud / Solutions Architecture
  - Embedded Systems / Firmware

## Optional Inputs

- **Role title**: e.g., "Senior Security Engineer", "Staff Backend Engineer"
- **Role level**: Junior / Mid / Senior / Staff / Principal
- **Interviewer name**: If known, enables research on their technical interests
- **Known format**: If the candidate knows the format (CoderPad, take-home, pair programming)

## Research Phase

### Step 1: Read the base playbook

Read the reference playbook bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "technical-phone-screen-playbook.md" -path "*/tech-screen-playbook/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/tech-screen-playbook/reference/technical-phone-screen-playbook.md --jq '.content' | base64 -d
```

This contains the universal framework (rubrics, meta-skills, time management) and all
10 category-specific breakdowns. Extract the relevant category section.

### Step 2: Company research (mandatory)

Use `WebSearch` and `WebFetch` to find:

1. **Company tech stack** — Search "[company] tech stack", "[company] engineering blog". What languages, frameworks, and infrastructure do they use?
2. **Interview format** — Search "[company] [role] interview glassdoor", "[company] technical interview format". CoderPad? HackerRank? Take-home? System design?
3. **Recent Glassdoor interview reports** — Search "[company] [category] interview questions glassdoor". What specific questions have been asked recently?
4. **Engineering blog** — Technical challenges the team faces, which inform likely interview topics
5. **Company values/tenets** — How they might flavour technical evaluation (Amazon LPs influence even coding screens)

### Step 3: Category-specific research

Based on the job category, conduct targeted research:

- **Security**: Search "[company] security team", "[company] security blog", "[company] bug bounty". What security challenges are they known for? What compliance frameworks apply?
- **Backend**: Search "[company] architecture", "[company] scale". What scale do they operate at? What distributed systems challenges?
- **Frontend**: Search "[company] design system", "[company] frontend stack". React? Vue? Custom framework?
- **ML/AI**: Search "[company] ML platform", "[company] AI research". What models, what infrastructure?
- **Infra/DevOps**: Search "[company] infrastructure", "[company] SRE". Cloud provider? K8s? Custom tooling?

### Step 4: Interviewer research (if name provided)

- Search LinkedIn, GitHub, conference talks, blog posts
- Note their technical interests — likely to influence question selection

## Output Format

Generate the playbook as a **markdown file** and publish as a **secret GitHub gist**.

1. Write to temp file: `/tmp/tech-screen-playbook-[company]-[category].md`
2. Create gist: `gh gist create /tmp/tech-screen-playbook-[company]-[category].md -d "Tech Screen Playbook: [Company] — [Category]"`
3. Copy URL to clipboard: `echo "$URL" | pbcopy 2>/dev/null`
4. Return the gist URL

### Playbook structure

```markdown
# Tech Screen Playbook: [Company Name] — [Category]

## Interview Format
[What format to expect based on Glassdoor research. CoderPad? HackerRank? Take-home? Duration? Number of problems? Is system design included?]

## Company Tech Stack
[Languages, frameworks, infrastructure used by this company. What's relevant to your category.]

## What They'll Evaluate
[Map the 4-dimension rubric (Solve, Code, Communicate, Test) to this company's known philosophy. E.g., Meta = "What" company (results), Google = "How" company (process).]

## Category-Specific Preparation: [Category Name]

### Domains You'll Be Tested On
[From the base playbook's category section, filtered to what's relevant for this company. E.g., for a Security role at AWS, emphasise cloud security and IAM over general web app security.]

### Most Likely Questions
[Based on Glassdoor reports and company focus areas, list 10-15 specific questions with brief approach notes for each.]

1. [Question] — **Approach:** [Brief framework]
2. [Question] — **Approach:** [Brief framework]
...

### Level-Specific Expectations
[What "mid" vs "senior" vs "staff" looks like for this category at this company. Include scope expectations.]

### Domain Deep-Dive Checklist
[Category-specific knowledge checklist. For Security: OWASP Top 10, threat modeling, crypto, cloud security. For Backend: DS&A patterns, system design, API design. For Frontend: JS fundamentals, React patterns, CSS, a11y.]

## Company-Specific Angles
[How this company's values/culture influence their technical evaluation. E.g., Amazon interviewers are assigned specific LPs to evaluate even in coding rounds.]

## Practice Plan
[Specific resources and practice problems tailored to this company + category combination. Include estimated hours needed.]

| Resource | Focus Area | Time |
|----------|-----------|------|
| [Specific resource] | [What it covers] | [Hours] |

## Interviewer Intel
[If name provided: their technical interests, GitHub contributions, talks. If not: general notes on what interviewers at this company tend to focus on.]

## Common Traps for [Category] at [Company]
[Category-specific gotchas, informed by Glassdoor reports and company culture.]

## Pre-Screen Checklist
- [ ] Know the format: [format from research]
- [ ] Practiced on [platform]: [CoderPad/HackerRank/etc]
- [ ] Warm-up: solve 2-3 easy problems 30 min before
- [ ] Category domains reviewed: [list key domains]
- [ ] Company-specific topics: [list]
- [ ] Language chosen: [best language for this category]
- [ ] Environment ready: quiet room, stable internet, water
- [ ] Scratch pad/second screen for notes

## Sources
[Links to Glassdoor reports, engineering blog posts, and resources referenced.]
```

## Rules

1. **Always research live** — Glassdoor interview reports and company tech stack are the highest-value research.
2. **Category determines content** — A security playbook looks fundamentally different from a frontend playbook. Use the relevant section from the base doc.
3. **Company + category intersection is key** — "Security at AWS" is different from "Security at a startup". Tailor accordingly.
4. **Include practice resources** — Specific LeetCode problems, GitHub repos, courses. Not generic "study algorithms".
5. **Level-calibrate** — A mid-level and staff-level candidate at the same company need different preparation.
6. **Format matters** — If Glassdoor says they use CoderPad with 2 medium problems, that changes prep strategy vs a take-home.
7. **Include sources** — Link to every resource referenced.
8. **Output as a secret GitHub gist** — Write to temp, `gh gist create`, return URL. Requires `gh` CLI.
