---
name: behavioural-interview-playbook
description: >-
  Use this skill when the user wants to prepare for a behavioural interview round.
  Trigger on "behavioural interview", "behavioral interview", "behavioural round",
  "LP interview", "leadership principles interview", "Jedi round", "culture interview",
  "Googleyness interview", "behavioural prep for [company]", "prepare me for
  behavioural questions", or any request to generate a personalised behavioural
  interview playbook for a specific company and role.
---

# Behavioural Interview Playbook Generator

Generate a personalised, company-specific behavioural interview playbook. This is the
dedicated behavioural round — 45-60 minutes of competency-based questions scored against
the company's specific framework. The playbook combines the base guide's proven
frameworks with LIVE research on the specific company, role, and recent candidate
reports to produce a tactical briefing.

**CRITICAL:** The base guide is a foundation, NOT the source of truth. Company processes
change frequently. You MUST conduct live research for every playbook you generate.

## Required Inputs

- **Company name** (required): The company the user is interviewing at
- **Career knowledge base OR STAR stories file** (required): Path to career KB or generated CARL stories. If neither exists, tell the user to run `/career-kb-builder` and `/star-story-generator` first.

## Optional Inputs

- **Role title**: e.g., "Senior Security Engineer"
- **Role level**: L3/L4/L5/L6/L7 or Junior/Mid/Senior/Staff/Principal
- **Role category**: Backend, Frontend, Security, ML, Infra, Management, etc. (affects behavioural expectations)
- **Interviewer name(s)**: If known, enables social engineering research
- **Known format**: If the user knows the round structure (e.g., "Amazon loop with Bar Raiser")

## Step 1: Read the base guide

Read the reference playbook bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "behavioural-interview-playbook.md" -path "*/behavioural-interview-playbook/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/behavioural-interview-playbook/reference/behavioural-interview-playbook.md --jq '.content' | base64 -d
```

This contains company frameworks, question taxonomy, cognitive biases, easy outs, and
naturalness tactics. Use it as the foundation — but DO NOT rely on it exclusively.

## Step 2: LIVE company research (MANDATORY — do not skip)

The base guide captures the state of play as of March 2026. Companies evolve their
processes. You MUST conduct fresh research for EVERY playbook you generate.

### Research checklist:

1. **Glassdoor behavioural interview reports** — Search "[company] behavioural interview questions glassdoor [year]". Read the 10 most recent reports for the specific role. Extract:
   - What questions were actually asked
   - How many behavioural questions per round
   - Round duration and format
   - What differentiated pass from rejection

2. **Company careers/values page** — Search "[company] values" or "[company] leadership principles" or "[company] culture". Fetch the EXACT current language. Companies rebrand values regularly.

3. **Recent blog posts about the hiring process** — Search "[company] interview process [year]" on interviewing.io, Medium, Blind, or the company's own blog. Look for process changes.

4. **Role-category-specific behavioural expectations** — Search "[company] [role category] behavioural interview". Security roles get different questions than frontend roles.

5. **Interviewer research** (if names provided) — LinkedIn, talks, blog posts. Note their technical interests and management philosophy.

6. **Company engineering blog** — What problems are they working on? This context helps frame stories.

7. **Recent news** — Last 90 days. Funding, launches, reorgs. This affects what stories resonate.

### Cross-reference with base guide

After live research, compare what you found against the base guide's company section:
- Has the framework changed? (e.g., did the company add/remove values?)
- Are there new question patterns not in the base guide?
- Has the round format changed?
- Are there role-specific questions the base guide doesn't cover?

**If live research contradicts the base guide, the live research wins.**

## Step 3: Load the user's career data

Read their career KB or STAR stories file:

```bash
find . -name "career-knowledge-base.md" -o -name "star-stories-*.md" -o -name "career-kb.md" 2>/dev/null | head -5
```

Parse out:
- Available stories with competency tags
- Story coverage matrix (which competencies are covered)
- Scope level of each story

## Step 4: Map stories to this company's framework

Using the company's SPECIFIC competency framework (from live research + base guide):

1. For each competency the company evaluates, find the best-matching story from the user's bank
2. Identify scope mismatches (L4 story for L6 interview)
3. Identify coverage gaps (competency with no matching story)
4. For each match, determine the framing angle specific to this company

## Step 5: Generate the playbook

Write the playbook to a local file and create a GitHub gist:

1. Write to temp: `/tmp/behavioural-playbook-[company].md`
2. Create gist: `gh gist create /tmp/behavioural-playbook-[company].md -d "Behavioural Interview Playbook: [Company]"`
3. Copy URL: `echo "$URL" | pbcopy 2>/dev/null`
4. Return gist URL

### Playbook structure

```markdown
# Behavioural Interview Playbook: [Company Name] — [Role]

## Round Format (from live research)
[How many behavioural questions. Duration. Who conducts it. Any unique format (Amazon Bar Raiser, Meta Jedi, Google G&L, Netflix culture round). Source: Glassdoor/interviewing.io]

## Company Framework (verified current)
[The exact competency framework THIS company uses RIGHT NOW. Verified against their current careers page, not just the base guide. If it's changed since the base guide was written, note what's different.]

| Competency | What They're Testing | Weight at [Level] |
|------------|---------------------|-------------------|
| [Comp 1] | [Explanation] | [High/Medium/Critical] |
| [Comp 2] | [Explanation] | [Weight] |

## Most Likely Questions (from Glassdoor + live research)
[The specific questions that have been asked at this company for this role type in the last 12 months. Sourced from Glassdoor reports, NOT invented.]

1. "[Exact question from Glassdoor]" — Tests: [competency] — Your story: [story title from their bank]
2. "[Exact question]" — Tests: [competency] — Your story: [story title]
3. ...
(Aim for 10-15 questions)

## Your Story Assignments

### [Competency 1]: [Story Title]
**Most likely question:** "[question from above]"
**Company-specific framing:** [How to emphasise aspects of this story that align with THIS company's values. E.g., for Amazon: lead with customer impact. For Anthropic: lead with safety/judgment angle.]
**Scope check:** [Is this story's scope appropriate for the target level? If not, guidance on how to adjust framing.]
**Follow-up prep:**
- "Why that approach?" → [answer]
- "What would you do differently?" → [answer]
- "What was the measurable impact?" → [answer]

### [Competency 2]: [Story Title]
[Same structure]

## Coverage Gaps
[Competencies from this company's framework that have NO matching story in the user's bank. For each gap:]
- **[Competency]**: No coverage. Suggestions:
  - Probe question to surface a hidden story: "[specific question]"
  - Adjacent story that could be reframed: [story title] — but would need [adjustment]
  - If genuinely no story: use the hypothetical approach: "Based on my experience with [X], here's how I would handle that..."

## Easy Outs — Calibrated for [Company]
### Weakness Answer (calibrated for [company culture])
[The specific weakness framing that works at THIS company type. Not generic.]

### "Why [Company]?" (from live research)
[Specific recent news, product, blog post, or mission element to reference. Backed by actual research, not training data.]

### "Why Are You Leaving?"
[Framed as pull toward what THIS company specifically offers]

### Failure Story
[The user's best failure story reframed for this company's values]

## Cognitive Bias Strategy
**Opening anchor:** Use [story title] first — it's your highest-scope story and sets the level frame at [target level].
**Narrative arc:** [Story 1 — anchor] → [Stories 2-4 — breadth] → [Story 5 — growth/forward-looking close]
**Peak moment:** [Identify which story has the strongest emotional/impact peak — ensure it's placed mid-round]

## Role-Category Adaptations
[If the user's role category (security, frontend, ML, etc.) has specific behavioural expectations, include them here. Reference the role-category table from the base guide, supplemented with live research for this company's version.]

## Interviewer Intel
[If name(s) provided: background, talks, technical interests, management philosophy, rapport hooks. If not: general notes on what interviewers at this company tend to focus on.]

## Red Flags to Avoid (Company-Specific)
[Based on this company's values, what will get you rejected even if answers are otherwise good. E.g.:]
- Amazon: No metrics = reject. All "we" no "I" = reject.
- Meta: E6+ failure on behavioural = automatic No Hire.
- Anthropic: Dismissing safety concerns = instant disqualification.
- Netflix: Overly diplomatic = poor cultural fit signal.

## Pre-Round Checklist
- [ ] Company framework verified current (not just from base guide): [list values/LPs]
- [ ] 8-12 CARL stories mapped to framework
- [ ] First-answer story selected: [story title] — scope: [level]
- [ ] Easy outs prepared: weakness, why leaving, failure, conflict
- [ ] Follow-up prep for each story: why/what else/what differently/specific role
- [ ] Coverage matrix: [N] competencies covered / [M] gaps
- [ ] Practiced out loud with natural variation
- [ ] Reverse interview questions: [list 5]

## Sources
[Links to every Glassdoor report, blog post, careers page, and resource used. The user should be able to read each source before their interview.]
```

## Rules

1. **ALWAYS conduct live research.** The base guide is a starting point, not gospel. Search Glassdoor, interviewing.io, company careers pages, and recent candidate reports. If live research contradicts the base guide, live research wins.
2. **Company-specific, not generic.** Every section must be tailored to THIS company. If a section could apply to any company, it's not good enough.
3. **Source every claim.** Link to the Glassdoor report, blog post, or careers page where you found each question or framework detail.
4. **Map to the user's actual stories.** Don't just list competencies — match them to specific stories from the user's career KB. Flag gaps honestly.
5. **Calibrate by level.** L4 behavioural looks fundamentally different from L6. Scope expectations, question depth, and acceptable story types all change.
6. **Calibrate by role category.** Security behavioural ≠ frontend behavioural ≠ ML behavioural. Include role-specific expectations.
7. **Include the cognitive bias strategy.** Which story opens (anchoring), which closes (peak-end), what's the narrative arc.
8. **Easy outs must be company-specific.** A generic weakness answer fails. The weakness must be calibrated to what THIS company values.
9. **Output as a secret GitHub gist.** Write to temp, `gh gist create`, return URL. Requires `gh` CLI.
10. **Note what's uncertain.** If Glassdoor has sparse data for this company/role, say so. If the framework may have changed, flag it. Intellectual honesty about confidence levels is more useful than false certainty.
