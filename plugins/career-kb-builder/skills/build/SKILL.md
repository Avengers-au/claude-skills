---
name: career-kb-builder
description: >-
  Use this skill when the user wants to build or update their career knowledge base
  for interview preparation. Trigger on "build my career KB", "career knowledge base",
  "extract my stories", "build my story bank", "interview story bank", "help me
  document my career", "capture my achievements", "I need to prepare my career stories",
  or any request to conversationally extract and structure career data for interviews.
---

# Career Knowledge Base Builder

Conversationally interview the user to extract, structure, and store their career data
as a structured knowledge base file. This knowledge base becomes the foundation for
generating STAR/CARL stories, tailored resumes, optimised LinkedIn profiles, and
company-specific behavioural interview preparation.

## How It Works

This is a **conversational extraction process**, not a form-filling exercise. You act as
a career coach — asking probing questions, surfacing hidden achievements, and helping
the user quantify their impact. The output is a structured local file.

## Step 1: Read the base guide

Read the reference guide bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "career-data-ingestion-guide.md" -path "*/career-kb-builder/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/career-kb-builder/reference/career-data-ingestion-guide.md --jq '.content' | base64 -d
```

This contains the schema, extraction techniques, quantification methods, and quality
checklist. Follow it precisely.

## Step 2: Check for existing career KB

Look for an existing career knowledge base file:

```bash
find . -name "career-knowledge-base.md" -o -name "career-kb.md" -o -name "story-bank.md" 2>/dev/null | head -5
```

If one exists, read it first. The session will UPDATE the existing KB rather than starting from scratch.

## Step 3: Set the stage

Explain to the user what you're about to do:

> "I'm going to interview you about your career to build a structured knowledge base
> of your achievements, projects, and experiences. This will take about 30-45 minutes
> across our conversation. I'll ask probing questions to surface stories you might not
> realise are valuable, and I'll help you quantify your impact. The output will be a
> structured file you can use for resume generation, STAR story preparation, and
> interview prep. Ready?"

## Step 4: Career timeline walkthrough

Start with the big picture:

1. "Walk me through your career chronologically — each company, role, and roughly how long you were there."
2. Note each role. For each, ask: "What was the most significant thing you accomplished there?"
3. This produces a skeleton of 5-15 potential stories to explore.

## Step 5: Deep-dive extraction (Core 4 first)

Work through the **Core 4 story categories** first to ensure minimum viable coverage:

### Most Successful Project
- "What's the project you're most proud of in your career?"
- "What made it challenging?"
- "What specifically did YOU do — not the team, but you personally?"
- "What was the measurable outcome?"
- "What would have happened if you hadn't been involved?"

### Least Successful Project
- "What project didn't go as planned?"
- "What went wrong and why?"
- "What was your role in the failure — what do you own?"
- "What did you learn that changed how you work?"
- "Can you point to a subsequent situation where you applied that learning?"

### Most Difficult Stakeholders
- "Who was the hardest person or team to work with?"
- "What made the relationship difficult?"
- "What did you do to manage the situation?"
- "How did it resolve? Is the relationship intact?"
- "What would you do differently?"

### Passion Project
- "When were you most energised and engaged at work?"
- "What was it about that work that excited you?"
- "What impact did it have?"
- "Why does this matter to you personally?"

## Step 6: Competency gap analysis

After the Core 4, check which competencies are NOT yet covered. For each gap, probe specifically:

**Uncovered competency prompts:**

| Missing Competency | Probing Question |
|-------------------|-----------------|
| Leadership/influence | "When did you drive a decision without being the boss?" |
| Technical decision-making | "Tell me about a significant technical trade-off you made" |
| Mentoring | "Have you helped develop a junior colleague? What happened?" |
| Innovation | "When did you create something new — a tool, process, or approach?" |
| Customer focus | "When did you prioritise the user's need over internal convenience?" |
| Communication | "When did you have to explain something complex to a non-technical audience?" |
| Prioritisation | "When did you have to cut scope or say no to something?" |
| Ethical judgment | "When did you push back on something because it was the right thing to do?" |

## Step 7: Quantification pass

Go back through each story and apply the estimation techniques:

- "You said you improved the system — by approximately how much?"
- "How many users/customers were affected?"
- "How many engineers were on the team?"
- "How long did this take?"
- "Can you estimate the dollar value of the time saved?"
- "What was the before vs after state?"

Use these techniques when the user says "I don't have numbers":
1. **Range estimation**: "Was it closer to 10% or 50%?"
2. **Frequency multiplication**: "How often did this happen per week? And for how many weeks?"
3. **Cost translation**: "About how many hours per week did this save? At roughly what hourly rate?"
4. **Comparison anchors**: "What was the old way? How long did it take? And the new way?"

## Step 8: Write the career KB file

Write the structured file to the user's local directory. Use this path convention:

```
./career-knowledge-base.md
```

Follow the schema from the base guide exactly. Include:
- YAML frontmatter with owner, date, total stories
- One `## Story: [Title]` section per story
- All metadata fields (company, role, team size, date, duration, outcome type, competencies, tech stack, scale)
- Situation, Task, Actions (numbered, first person), Result (quantified), Learnings
- Resume Bullet and LinkedIn Version for each story

## Step 9: Quality check

After writing, verify each story against the quality checklist:

- [ ] Specificity: Can someone picture exactly what happened?
- [ ] Personal contribution: Clear what YOU did vs the team?
- [ ] Quantified result: At least one number?
- [ ] Learnings: Genuine insight, not a platitude?
- [ ] Level-appropriate scope: Matches target interview level?
- [ ] Reusability: Can be branched to 2-3 competency questions?
- [ ] Honesty: Would hold up under 3-4 levels of probing?

Report the results to the user:
- Total stories captured
- Competency coverage (which are covered, which have gaps)
- Strongest stories (highest scope + quantification)
- Recommended next steps (stories to add, competencies to fill)

## Rules

1. **Act as a career coach, not a form filler.** Ask probing follow-up questions. Push for specifics. Challenge vague claims.
2. **Surface hidden achievements.** People systematically undervalue their contributions. Use the "invisible impact" and "energy and pride" questions.
3. **Push for quantification.** "Improved performance" is useless. "Reduced P99 latency from 450ms to 120ms" is gold. Use the 6 estimation techniques.
4. **Maintain 80/20 I/we ratio.** Every action should be in first person. If the user says "we", ask: "What specifically did YOU do?"
5. **Don't fabricate.** If the user genuinely can't quantify something, use qualitative comparison anchors. Never invent numbers.
6. **Cover the Core 4 minimum.** Even a short session should produce at least 4 stories (success, failure, conflict, passion).
7. **Tag competencies.** Every story must have 1-3 competency tags for later filtering.
8. **Include resume bullets.** Every story needs a compressed 1-2 line version for resume use.
9. **Output locally.** Write to `./career-knowledge-base.md` in the current working directory. Do not create gists or commit to repos — this is personal career data.
10. **Conversational pace.** Don't rapid-fire all questions at once. Process each story fully before moving to the next. Acknowledge and validate achievements as you go.
