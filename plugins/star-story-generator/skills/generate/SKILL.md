---
name: star-story-generator
description: >-
  Use this skill when the user wants to generate tailored STAR or CARL stories for
  behavioural interviews. Trigger on "generate STAR stories", "CARL stories", "story
  bank", "behavioural stories for [company]", "interview stories", "prep stories for
  Amazon", "map my stories to [company]", "prepare behavioural answers", or any request
  to create company-specific interview stories from career data.
---

# STAR/CARL Story Generator

Transform the user's career knowledge base into company-specific, level-appropriate
CARL stories ready for behavioural interviews. Maps career achievements to the target
company's competency framework (Amazon LPs, Meta dimensions, Google attributes, etc.)
and generates rehearsal-ready answers with appropriate scope signalling.

## Required Inputs

- **Company name** (required): The company the user is interviewing at
- **Career knowledge base** (required): Path to the user's structured career KB file (from `/career-kb-builder`)

## Optional Inputs

- **Role title**: e.g., "Senior Software Engineer". Infer from context if not stated
- **Role level**: L3/L4/L5/L6/L7 or Junior/Mid/Senior/Staff/Principal. Critical for scope calibration
- **Job description**: If available, enables more precise competency matching
- **Specific competencies to cover**: If the user knows what they'll be evaluated on

## Step 1: Read the base guide

Read the reference guide bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "star-story-generator-guide.md" -path "*/star-story-generator/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/star-story-generator/reference/star-story-generator-guide.md --jq '.content' | base64 -d
```

This contains the CARL framework, Decode-Select-Deliver methodology, company competency
mappings, repurposing techniques, scope signalling, and naturalness tactics.

## Step 2: Load the career knowledge base

Read the user's career KB:

```bash
find . -name "career-knowledge-base.md" -o -name "career-kb.md" -o -name "story-bank.md" 2>/dev/null | head -5
```

If not found, tell the user to run `/career-kb-builder` first.

Parse out all stories with their competency tags, tech stack, scale indicators, and outcome types.

## Step 3: Research the company's competency framework

Use `WebSearch` to find:

1. **Company values/tenets/leadership principles** — The exact framework they evaluate against
2. **Glassdoor behavioural interview reports** — What questions are actually asked
3. **Level-specific expectations** — What scope is expected at the target level

Map the company to the correct framework from the base guide:
- **Amazon**: 16 Leadership Principles (identify which LPs are heaviest for the target level)
- **Meta**: 8 Behavioural Dimensions (identify IC4/IC5/IC6 expectations)
- **Google**: Googleyness + Leadership + GCA + RRK
- **Stripe**: Users First, Rigor and Craft, Ownership, Urgency
- **Netflix**: Freedom and Responsibility, Keeper Test
- **Anthropic**: AI Safety alignment, intellectual humility
- **Other**: Extract values from careers page and map to standard competency clusters

## Step 4: Match stories to competencies

For each competency in the company's framework:

1. Search the career KB for stories tagged with matching competencies
2. Select the highest-scope story for each competency
3. Verify scope matches target level (see scope ladder in guide)
4. If a competency has no matching story, flag it as a **gap** for the user

Build a **coverage matrix** showing which stories cover which company competencies.

## Step 5: Generate CARL stories

For each story-competency match, generate a full CARL answer:

```markdown
## [Competency Name]: [Story Title]

**Target question:** "[Most likely question for this competency at this company]"

**Level:** [Target level] | **Duration:** ~[2-3] minutes | **Scope:** [team/cross-team/org]

### Context (~20% of answer)
[Rewritten from career KB situation/task. Include scope markers: team size, duration,
scale, stakeholders. Calibrated to target level.]

### Actions (~60% of answer)
[Rewritten from career KB actions. First-person singular ("I"). Plural actions showing
patterns. Reordered to front-load the actions most relevant to THIS competency.
Include decision rationale — "I chose X because Y".]

1. [Action 1 — with reasoning]
2. [Action 2 — with reasoning]
3. [Action 3 — with reasoning]
4. [Action 4 — with reasoning]

### Results (~10% of answer)
[Quantified outcomes from career KB. Highlight the metric most relevant to this
competency. Include business impact.]

### Learnings (~10% of answer)
[Rewritten from career KB learnings. Tailored to what THIS company values.
For Amazon: connect to an LP. For Meta: connect to growth dimension.
For Anthropic: connect to safety/humility.]

---

**Follow-up prep:**
- "Why that approach?" → [prepared answer]
- "What would you do differently?" → [prepared answer]
- "What was the measurable impact?" → [prepared answer]
- "What was your specific contribution vs the team?" → [prepared answer]

**Repurposing:** This story also works for: [list other competencies it covers]
```

## Step 6: Generate the coverage report

After all stories are generated, produce a summary:

```markdown
# Story Coverage Report: [Company Name] — [Level]

## Coverage Matrix
| Competency | Story | Scope | Strength |
|------------|-------|-------|----------|
| [Comp 1] | [Story Title] | [team/cross-team/org] | Strong/Adequate/Weak |
| [Comp 2] | [Story Title] | ... | ... |
| [Comp 3] | ⚠️ NO COVERAGE | — | Gap |

## Gaps (Action Required)
- [Competency X]: No story in career KB matches this. Suggestion: [probe question to surface a story]
- [Competency Y]: Story exists but scope is L4, target is L6. Suggestion: [how to reframe or find a higher-scope example]

## Strongest Stories
1. [Story Title] — covers [N] competencies, [scope]-level scope, strong quantification
2. [Story Title] — covers [N] competencies...

## Recommended Opening Story
[The story to use for the first behavioural question — highest scope, strongest signal, sets the best anchor]

## Practice Priority
1. [Story most likely to be asked — practice first]
2. [Second most likely]
3. [Third most likely]
```

## Step 7: Write output

Write all generated stories and the coverage report to a local file:

```
./star-stories-[company-name]-[date].md
```

## Rules

1. **CARL, not STAR** for L5+ roles. Include Learnings in every story. For L3-L4, STAR is acceptable but CARL is still preferred.
2. **60% Actions rule.** If the Context section is longer than the Actions section, rewrite. Actions are what interviewers evaluate.
3. **Scope must match level.** L4 stories for L6 interviews = down-levelling. Check every story against the scope ladder.
4. **Company framing, not company fabrication.** Reframe emphasis based on what the company values. Never change the facts of a story.
5. **2 stories per critical competency.** For Amazon, prepare 2 per LP. For Meta, 2 per dimension. Interviewers probe deep.
6. **Include follow-up prep.** Every story needs prepared answers for "Why?", "What else?", "What would you change?", "What was your specific role?"
7. **Flag gaps honestly.** If the career KB doesn't cover a competency, say so and suggest how to fill it. Never fabricate stories.
8. **Natural language.** Generated stories should sound like a person talking, not a template. Use conversational transitions and natural phrasing.
9. **Output locally.** Write to the current directory. These are personal interview prep materials.
10. **Include the coverage matrix.** The user needs to see which competencies are covered, which have gaps, and which stories are strongest.
