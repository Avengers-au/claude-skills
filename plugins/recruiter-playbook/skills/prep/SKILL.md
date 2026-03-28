---
name: prep
description: >-
  Use this skill when the user wants to prepare for a recruiter screening call.
  Trigger on "recruiter screen", "recruiter call", "phone screen", "recruiter prep",
  "interview prep for [company]", "I have a call with a recruiter",
  "prepare me for [company]", "help me prep for [company] interview", or any request
  to generate a personalised recruiter screening playbook for a specific company.
user-invocable: true
allowed-tools: Bash(gh *), Read, WebSearch, WebFetch
argument-hint: <company-name> [recruiter-name] [hiring-manager-name]
---

# Recruiter Screen Playbook Generator

Generate a personalised, company-specific recruiter screening playbook that gives the
user an unfair advantage. This is not generic advice — it is a tactical briefing
tailored to the specific company, role, and people involved.

## Required Inputs

- **Company name** (required): The company the user is interviewing with

## Optional Inputs

- **Role title**: The specific role (e.g., "Senior Backend Engineer"). Infer from context if not stated.
- **Recruiter name**: If known, enables LinkedIn intelligence section
- **Hiring manager name**: If known, enables deeper social engineering angles
- **Role level**: Junior / Mid / Senior / Staff / Principal. Infer from context if possible.

## Research Phase

Before generating the playbook, conduct thorough research. **You MUST actually search — do not rely on training data alone.**

### Step 1: Read the base playbook

Read the reference playbook bundled with this plugin. It is located at `reference/recruiter-screen-playbook.md` relative to this plugin's root directory.

To find the plugin's installation path, search for the file:

```bash
find ~/.claude -name "recruiter-screen-playbook.md" -path "*/recruiter-playbook/*" 2>/dev/null | head -1
```

If not found locally, fetch it from the source repo:

```bash
gh api repos/Avengers-au/claude-skills/contents/plugins/recruiter-playbook/reference/recruiter-screen-playbook.md --jq '.content' | base64 -d
```

This reference doc contains proven frameworks, scripts, and category-specific adaptation strategies. Use it as the foundation for the personalised playbook.

### Step 2: Company research (mandatory)

Use `WebSearch` and `WebFetch` to find:

1. **Company values / tenets / leadership principles** — Search for "[company] values", "[company] leadership principles", "[company] culture". Find the EXACT language they use on their careers page.
2. **Recent news** (last 90 days) — Search "[company] news", "[company] funding", "[company] product launch"
3. **Engineering blog** — Search "[company] engineering blog" or "[company] tech blog". Read the 2-3 most recent posts.
4. **Glassdoor interview reviews** — Search "[company] [role] interview glassdoor" for recent reports on the screening process
5. **Company category** — Determine which category applies: FAANG/Big Tech, High-growth startup, Enterprise/traditional, Mission-driven, Defence/security, AI/ML. This determines the language strategy from the base playbook.

### Step 3: People research (if names provided)

If the **recruiter's name** is provided:
- Search LinkedIn: "[name] [company] recruiter linkedin"
- Look for: tenure at company, previous employers, shared connections, posts/content they've shared
- Note anything that creates a natural conversation hook (shared alma mater, previous employer, interests)

If the **hiring manager's name** is provided:
- Search LinkedIn: "[name] [company] linkedin"
- Search for talks/podcasts: "[name] conference talk", "[name] podcast"
- Search for articles: "[name] blog post", "[name] [company] engineering blog"
- Search GitHub: "[name] github" for open-source contributions
- Note specific technical opinions, projects, or achievements that can be referenced naturally

### Step 4: Salary research

- Search Levels.fyi: "[company] [role] [level] compensation levels.fyi"
- Search Glassdoor: "[company] [role] salary glassdoor"
- Determine the likely compensation band (base, equity, total comp range)

## Output Format

Generate the playbook as a **markdown file** and publish it as a **secret GitHub gist** so the user can pull it up on their phone right before the call.

### Step 1: Write the playbook to a temporary file

Write the playbook to a temp file (e.g., `/tmp/recruiter-playbook-[company].md`).

### Step 2: Create a secret GitHub gist

```bash
gh gist create /tmp/recruiter-playbook-[company].md -d "Recruiter Screen Playbook: [Company Name]"
```

### Step 3: Return the gist URL to the user

Copy the URL to clipboard on macOS:

```bash
echo "$URL" | pbcopy 2>/dev/null
```

### Playbook structure

The generated markdown file MUST follow this structure:

```markdown
# Recruiter Screen Playbook: [Company Name]

## Company Intel
[2-3 paragraphs covering: what the company does, their category, recent news (last 90 days), and current strategic focus. Be specific — dates, numbers, product names.]

## Company Values & Language Map
[Table mapping each company value/tenet to specific phrases the user should weave into conversation. Use the EXACT language from the company's careers page. For each value, provide 1-2 example sentences that sound natural, not rehearsed.]

| Value/Tenet | What It Means | Phrases to Use |
|-------------|---------------|----------------|
| [Value 1] | [Brief explanation] | "[Natural sentence example]" |
| [Value 2] | [Brief explanation] | "[Natural sentence example]" |

## Your Script

### Opening
[Exact opening line tailored to this company]

### "Tell Me About Yourself" — Tailored Version
[Rewrite the Present-Past-Future formula with specific language that resonates with this company's values. Include placeholders like [YOUR ACHIEVEMENT] where the user needs to fill in their own details.]

### "Why [Company Name]?"
[A ready-to-use answer that references specific, recent company information discovered during research. Include the blog post, product launch, or news item to reference.]

### "Why Are You Looking?"
[Framed as a pull toward what this specific company offers]

## Salary Intelligence
[Compensation band from Levels.fyi/Glassdoor. Include base, equity, and total comp ranges for the likely level. Deflection script if asked early.]

## Recruiter Intel
[If recruiter name was provided: their background, tenure, shared connections, conversation hooks. If not provided: general notes on what recruiters at this company tend to focus on based on Glassdoor reviews.]

## Hiring Manager Intel
[If hiring manager name was provided: their background, talks, blog posts, technical opinions, projects to reference. If not provided: skip this section.]

## Questions to Ask
[5 tailored questions — NOT generic. Each should reference something specific about the company, demonstrate knowledge, and invite the recruiter to share insider perspective.]

1. [Question referencing recent company news/product]
2. [Question about team structure or engineering culture]
3. [Question about the specific technical challenge this role addresses]
4. [Question showing interest in the recruiter personally: "What attracted you to [Company] from your previous role?"]
5. [Question about growth/trajectory: "Where do you see this team/product heading in the next 12 months?"]

## Red Flags to Avoid
[Company-specific red flags based on their values. E.g., for Amazon: never say "that wasn't my responsibility". For startups: never signal rigid role boundaries.]

## 5-Minute Pre-Call Checklist
- [ ] Viewed recruiter's LinkedIn profile
- [ ] Read [specific blog post discovered during research]
- [ ] Memorised [company]'s core values: [list them]
- [ ] Practised "Tell me about yourself" out loud (<90 seconds)
- [ ] Prepared "Why [Company]?" with reference to [specific news item]
- [ ] Salary range noted: $[X]-$[Y] total comp
- [ ] Quiet location, charged phone, water, smiling

## Sources
[Links to all blog posts, news articles, Glassdoor pages, and other resources referenced above — so the user can read them before the call.]
```

## Rules

1. **Always research live** — Do not generate a playbook from training data alone. The value is in CURRENT, SPECIFIC information (recent blog posts, news, Glassdoor reviews).
2. **Be concrete, not generic** — Every section should contain information specific to THIS company. If a section could apply to any company, it is not good enough.
3. **Natural language, not keywords** — The phrases should sound like something a real person would say in conversation, not like someone reciting a values page.
4. **Include sources** — At the bottom of the playbook, include links to the specific blog posts, news articles, and resources referenced so the user can read them before the call.
5. **Calibrate formality** — Match the company's culture. Startups get casual language; enterprise/defence gets formal. AI labs get intellectually curious.
6. **If people names are provided**, the social engineering section should be substantive — specific hooks for building rapport, not generic advice. If you cannot find information on a person, say so honestly rather than fabricating.
7. **Salary ranges must come from actual data** — Levels.fyi, Glassdoor, or Blind. If data is unavailable for the specific company, say so and provide market benchmarks for the role level.
8. **Output as a secret GitHub gist** — Write the playbook to a temp file and create a gist with `gh gist create`. Return the gist URL so the user can view it on any device. Requires `gh` CLI installed and authenticated.

## Error Handling

| Error | Response |
|-------|----------|
| `gh` not installed | Tell user to install from https://cli.github.com |
| `gh` not authenticated | Tell user to run `gh auth login` |
| Company not found in searches | Fall back to training data, clearly note which sections are based on general knowledge vs. live research |
| Recruiter/HM name returns no results | State honestly that no public information was found and skip that section |
| Levels.fyi has no data for the company | Provide market benchmarks for the role level and location instead |
