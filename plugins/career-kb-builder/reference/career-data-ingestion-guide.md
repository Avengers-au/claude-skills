# Career Data Ingestion: Building a Structured Career Knowledge Base Through Conversational Extraction

## Overview

This document is a comprehensive guide for extracting, structuring, and storing career data through a conversational interview process. The output — a structured career knowledge base — serves as the foundation for generating STAR/CARL stories, tailored resumes, optimised LinkedIn profiles, and company-specific behavioural interview preparation. Every claim in this guide is backed by evidence from career coaching research, behavioural interview frameworks, and recruiting industry data.

**What IS covered:** What career data to capture (with schema), conversational extraction techniques used by professional career coaches, how to surface hidden achievements, how to quantify impact without exact numbers, how to structure and tag stories for maximum reusability, and the recommended file format.

**What is NOT covered:** Resume generation (see `resume-linkedin-optimiser-guide.md`), STAR story generation (see `star-story-generator-guide.md`), or behavioural interview preparation (see `behavioural-interview-playbook.md`).

**Research date:** March 2026.

---

## Part 1: What Data to Capture

### The Career Story as the Atomic Unit

Career coaches and behavioural interview frameworks converge on one principle: **the career story is the atomic unit** of interview preparation. Everything — resumes, LinkedIn bullets, STAR answers, behavioural responses — is generated from the same story bank. Capturing stories well once means never scrambling to invent answers on the spot.

### Required Fields per Story

| Field | Description | Why It Matters |
|-------|-------------|----------------|
| **Story title** | Short memorable name (e.g., "The Payment Gateway Migration") | Quick retrieval during interviews; mental anchoring |
| **Company & role** | Employer, your title, team size | Context for interviewers; signals scope |
| **Date range** | Year or quarter | Recency matters — interviewers prefer last 3-5 years |
| **Duration** | How long the project/effort lasted | Signals complexity and commitment |
| **Situation** | The context, problem, or challenge (2-3 sentences) | Sets the scene for STAR/CARL answers |
| **Task** | Your specific responsibility or assignment | Distinguishes YOUR role from the team's |
| **Actions** | Exactly what YOU did, step by step (this should be 60% of any answer) | The core of what interviewers evaluate |
| **Result** | Quantified outcome — revenue, time saved, users impacted, uptime | The payoff; must be measurable |
| **Learnings** | What you'd do differently; what you took forward | Shows growth mindset; covers "failure" questions |
| **Tech stack** | Languages, frameworks, tools, infrastructure used | Enables matching stories to technical roles |
| **Scale indicators** | Team size, user count, request volume, data size, budget | Signals scope and level-appropriate complexity |
| **Competency tags** | Which competencies this story demonstrates | Enables mapping stories to interview questions |
| **Outcome type** | Success, failure, conflict, leadership, innovation, technical decision | Enables quick filtering by question type |

### The "Core 4" Story Categories

Research from recruiting industry frameworks identifies four essential story categories that cover the vast majority of behavioural questions. Each can be "branched" to answer multiple questions by emphasising different aspects.

| Category | What It Covers | Questions It Answers |
|----------|---------------|---------------------|
| **Most Successful Project** | Career highlight with strong results | Leadership, ownership, delivering results, technical depth |
| **Least Successful Project** | Failure, setback, or missed goal with learnings | Failure handling, growth mindset, self-awareness, resilience |
| **Most Difficult Stakeholders** | Conflict, pushback, political challenge | Conflict resolution, communication, influence, empathy |
| **Passion Project** | Work that genuinely excites and energises you | Motivation, drive, innovation, going above and beyond |

### Competency Categories to Map Against

Every story should be tagged with 1-3 competencies from this list. The tagging enables rapid retrieval when preparing for specific companies (e.g., Amazon interviewers are assigned specific Leadership Principles to evaluate).

| Competency | Maps To (Company-Specific) |
|------------|--------------------------|
| Leadership & influence | Amazon: Ownership, Think Big. Meta: Proactivity. Google: Leadership |
| Technical decision-making | Amazon: Dive Deep, Are Right A Lot. Google: RRK |
| Conflict resolution | Amazon: Earn Trust, Have Backbone. Meta: Conflict Resolution |
| Ownership & initiative | Amazon: Ownership, Bias for Action. Meta: Proactivity |
| Collaboration & teamwork | Google: Googleyness. Meta: Empathy |
| Learning agility | Amazon: Learn and Be Curious. Microsoft: Growth Mindset. Meta: Growth |
| Resilience & perseverance | Amazon: Deliver Results. Meta: Perseverance |
| Customer/stakeholder focus | Amazon: Customer Obsession (#1 LP). Stripe: Users First |
| Mentoring & growth | Amazon: Hire and Develop the Best. Meta: Growth |
| Communication | All companies evaluate this; Meta has explicit dimension |
| Prioritisation | Amazon: Deliver Results, Bias for Action |
| Innovation | Amazon: Invent and Simplify, Think Big |
| Ethical judgment | Anthropic: AI Safety. Netflix: Freedom and Responsibility |
| Self-awareness | Microsoft: Growth Mindset. All companies probe this |

### Target Volume

**8-12 distinct stories minimum**, with 2-3 stories mapped to each competency. The "story circle" method demonstrates that 7-10 well-crafted stories can cover 35-50 different behavioural questions when branched effectively by emphasising different aspects of the same story.

At Amazon specifically, prepare **2 stories per Leadership Principle** — interviewers are assigned specific LPs and will probe 3-4 levels deep on each.

---

## Part 2: The Recommended Schema

### File Format

A single structured Markdown file with YAML frontmatter per story works best for a personal knowledge base of 8-15 stories. It's human-readable, version-controllable, and parseable by skills/agents.

### Schema Template

```yaml
---
career_knowledge_base: true
owner: "[Your Name]"
last_updated: "2026-03-28"
total_stories: 0
---

# Career Knowledge Base

## Story: [Story Title]

### Metadata
- **Company:** [Company Name]
- **Role:** [Your Title]
- **Team size:** [Number]
- **Date:** [YYYY-QN or YYYY]
- **Duration:** [e.g., 3 months, 6 weeks]
- **Outcome type:** [success | failure | conflict | leadership | innovation | technical-decision]
- **Competencies:** [tag1, tag2, tag3]
- **Tech stack:** [Python, AWS Lambda, PostgreSQL, etc.]
- **Scale:** [users: 50K, transactions: $2M/month, team: 12 engineers, etc.]

### Situation
[2-3 sentences: What was the context? What problem existed? What were the stakes?]

### Task
[1-2 sentences: What was YOUR specific responsibility? What were you asked/expected to do?]

### Actions
[Numbered list of specific steps YOU took. This should be the longest section — 60% of any interview answer comes from here. Use "I", not "we".]

1. [First action you took]
2. [Second action you took]
3. [Third action you took]
4. [Fourth action you took]

### Result
[Quantified outcomes. Use numbers, percentages, dollar amounts, time saved. If exact numbers aren't available, use the estimation techniques from Part 3.]

### Learnings
[What would you do differently? What transferable insight did you gain? This section is what separates senior answers from mid-level ones.]

### Resume Bullet
[1-2 line compressed version ready for copy-paste into resumes. Format: Strong verb + what you did + quantified result.]

### LinkedIn Version
[Slightly expanded version (3-4 sentences) for LinkedIn experience descriptions. More narrative, keyword-rich.]

---
```

### Metadata Tags for Filterability

| Tag Category | Example Values | Purpose |
|-------------|---------------|---------|
| `competency` | leadership, conflict, technical-decision, ownership | Match to interview questions |
| `company` | Amazon, Startup X, current employer | Filter by employer context |
| `date` | 2023-Q2, 2024 | Prioritise recent stories |
| `tech_stack` | Python, AWS, Kubernetes, React | Match to technical role requirements |
| `outcome_type` | success, failure, conflict, leadership, innovation | Quick access by question type |
| `scale` | team size, user count, revenue impact | Signal seniority and scope |

---

## Part 3: Conversational Extraction Techniques

### The Extraction Interview Structure

Professional career coaches use a structured conversational flow to extract stories. The session should last 45-90 minutes and follow this arc:

| Phase | Duration | Purpose |
|-------|----------|---------|
| **Warm-up** | 5 min | Set context, explain the process, reduce performance anxiety |
| **Career timeline** | 10 min | Walk through each role chronologically, noting major projects |
| **Deep-dive extraction** | 25-50 min | For each promising story, probe using techniques below |
| **Gap analysis** | 5-10 min | Identify missing competency coverage, probe for overlooked stories |
| **Quantification pass** | 5-10 min | Go back through stories and add/estimate metrics |

### Questions That Unlock Hidden Achievements

People systematically undervalue their own contributions. These probing techniques surface stories candidates don't realise are valuable.

#### The "What Improved" Reframe

Most people describe what they *did*. This technique shifts to what *changed because of them*.

- "What improved because you were in this role?"
- "How much did it improve?"
- "Over what timeframe?"
- "What would have happened if you hadn't done this?"

#### The "Before/After" Probe

Forces concrete comparison that naturally produces metrics.

- "What was the state of things when you started?"
- "What was the state when you left or completed the project?"
- "What was the delta?"

#### The "Energy and Pride" Questions

People discount work that came naturally to them. These questions surface it.

- "When did you feel fully immersed and energised by your work?"
- "What past successes made you feel proud?"
- "What positive feedback did you receive from colleagues and managers?"
- "What do people come to you for help with?"

#### The "Firefighting" Questions

Crisis stories are often the most compelling, but people forget them because the stress overshadows the achievement.

- "Tell me about a time everything went wrong."
- "What was the biggest crisis you dealt with?"
- "What did you do that nobody else could have done in that moment?"
- "What's the worst production incident you were involved in?"

#### The "Invisible Impact" Questions

People undervalue preventive work and infrastructure they built.

- "What would have happened if you had not been there?"
- "What did you prevent from going wrong?"
- "What process or tool exists today because you created it?"
- "What work did you do that nobody ever noticed — because it worked perfectly?"

#### The "Stakeholder" Questions

Surfaces conflict and influence stories — the hardest to remember but the most asked about.

- "Who was the hardest person to work with, and how did you manage them?"
- "When did you have to tell someone bad news?"
- "When did you disagree with your manager and what happened?"
- "When did you convince someone to change their mind?"

#### The "Failure" Questions

People avoid these but they're critical — 100% of behavioural interviews include failure questions.

- "What project didn't go as planned?"
- "What decision do you regret?"
- "When were you wrong about something technical?"
- "What feedback have you received that was hard to hear but ultimately useful?"

### Identifying Stories People Don't Realise Are Valuable

| What They Say | What It Actually Is |
|---------------|-------------------|
| "I wrote the docs" | "I reduced new-hire ramp-up time by X%" |
| "I wrote a script" | "I saved the team 5 hours/week through automation" |
| "I helped a junior" | "I developed talent and accelerated team output" |
| "I suggested we change how we do X" | "I identified and fixed a systemic inefficiency" |
| "I talked to the other team" | "I resolved a cross-organisational dependency" |
| "I fixed the tests" | "I improved CI reliability from X% to Y%" |
| "I set up monitoring" | "I reduced mean time to detection from hours to minutes" |
| "I cleaned up the codebase" | "I reduced technical debt that was slowing feature velocity by X%" |

---

## Part 4: Quantifying Impact Without Exact Numbers

### The 6 Estimation Techniques

When you don't have precise metrics — which is most of the time — use these evidence-based techniques from career coaching research.

| Technique | How It Works | Example |
|-----------|-------------|---------|
| **Range estimation** | Provide a plausible range rather than an exact figure | "Served 20-30 customers per day" instead of "many customers" |
| **Frequency multiplication** | Count: how often × impact per unit × time period | "Reviewed 40-50 articles per week" → 2,000+/year |
| **Cost translation** | Convert time saved into salary cost equivalent | "Eliminated 10 hours/week manual work ≈ $25K/year saved" |
| **Scale indicators** | Describe the size of what you worked on | "Team of 12, codebase of 500K lines, 100K daily active users" |
| **Comparison anchors** | Compare to the previous state | "Reduced from 3 days to 4 hours" (even without dollar value) |
| **Proxy metrics** | Use related measurable outcomes | "Feature adopted by 85% of users within first month" |

### The "How Many, How Much, How Long, How Often" Framework

For every action in a story, ask these four questions:

- **How many?** People, systems, teams, features, customers affected
- **How much?** Revenue, cost savings, performance improvement, error reduction
- **How long?** Duration of effort, time saved, delivery timeline
- **How often?** Frequency of impact, recurring savings, ongoing benefit

### Rules for Estimation

- **Never fabricate numbers** — interviewers probe 3-4 levels deep, and invented statistics collapse under follow-up
- **Use "approximately" or "roughly"** — signals honesty while still providing scale
- **Round to memorable numbers** — "roughly 40%" is better than "39.7%" (which sounds suspiciously precise)
- **Provide ranges when uncertain** — "saved between $50K and $100K annually" is credible; a single precise number without supporting data isn't

---

## Part 5: The Unified Career Data System

### How Everything Connects

The career knowledge base is the **single source of truth** that generates all career materials:

```
Career Knowledge Base (detailed stories, 8-12+)
    │
    ├──→ Resume (compressed stories as bullet points, tailored per role)
    │
    ├──→ LinkedIn (expanded versions, keyword-optimised for discovery)
    │
    ├──→ STAR/CARL Stories (full delivery versions mapped to company competencies)
    │
    └──→ Behavioural Interview Prep (stories matched to likely questions)
```

### The "Story Seeding" Technique

Each story in the knowledge base should include a `resume_bullet` field — a compressed version designed to **invite the interviewer to ask about it**. This means:

1. **Contain a "hook"** — a specific, intriguing detail that invites follow-up ("Reduced transaction failure rate from 3% to 0.1%" begs "How?")
2. **Match a prepared story** — every resume bullet corresponds to a full CARL story you can deliver in 2-3 minutes
3. **Be selectively specific** — enough detail to show impact, enough mystery to invite questions
4. **Use metrics that prompt curiosity** — "$180K/year saved" or "zero-downtime migration" naturally leads to "Walk me through that"

This transforms the interview from an interrogation into a guided tour of your best work.

---

## Part 6: Quality Checklist for Extracted Stories

After extraction, every story should pass these checks:

| Check | Question | If No |
|-------|----------|-------|
| **Specificity** | Can someone picture exactly what happened? | Add concrete details: dates, team size, tech, constraints |
| **Personal contribution** | Is it clear what YOU did vs what the team did? | Rewrite actions in first person singular. 80% "I", 20% "we" |
| **Quantified result** | Is there at least one number in the result? | Use estimation techniques from Part 4 |
| **Learnings** | Is there a genuine insight, not a platitude? | "I learned communication is important" is useless. "I learned to involve the security team in the design phase, not after implementation" is useful |
| **Level-appropriate scope** | Does the scope match your target interview level? | L3-L4: individual task. L5: team project. L6+: cross-team/org initiative |
| **Reusability** | Can this story be branched to answer 2-3 different competency questions? | If not, it may be too narrow — look for adjacent angles |
| **Honesty** | Would this story hold up under 3-4 levels of probing? | If not, tone it down or pick a different story |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "I can't think of any good stories" | Start with the Core 4 categories. Everyone has a success, a failure, a difficult person, and a passion project |
| "All my stories are about the same competency" | Use the gap analysis checklist — identify which competencies have zero coverage and probe specifically for those |
| "I don't have metrics for anything" | Use the 6 estimation techniques. "Approximately" is always better than nothing. Compare before/after states |
| "My best stories are from 5+ years ago" | Older stories are fine if they're your strongest. Supplement with at least 2-3 recent stories from the last 2 years |
| "I was part of a team — I can't take individual credit" | Identify your specific contribution. What would NOT have happened without you? What did you personally decide, build, or fix? |
| "My stories feel boring" | Reframe around the challenge, not the task. "I built an API" is boring. "I designed the API under a 2-week deadline with no documentation for the upstream system" has tension |
| "I have too many stories" | Prioritise: most recent, most quantified, highest scope, most diverse competency coverage. Aim for 8-12 polished stories |

---

## Sources

- [Your Behavioral Story Bank (Andrew Today)](https://www.andrew.today/p/your-behavioral-story-bank) — Story bank methodology: map 2-3 stories per competency across 20 stories
- [Building Your Story Bank (Tech Interview Coach)](https://techinterview.coach/blog/building-your-story-bank-the-key-to-nailing-your-tech-job-interview/) — 5-8 stories with role-specific seeding questions for extraction
- [Core 4 Stories for Behavioral Interviews (Realistic Recruiting)](https://realisticrecruiting.beehiiv.com/p/core-4-stories-interviews) — Four essential story categories covering all major question types
- [How to Prepare for Behavioral Interviews (Hello Interview)](https://www.hellointerview.com/learn/behavioral/overview/how-to-prepare) — CARL framework and Decode-Select-Deliver methodology
- [STAR Method for Behavioral Stories Guide 2025 (JobLogr)](https://joblogr.com/blog/star-method-for-behavioral-stories-guide-2025) — Updated STAR with 60% action emphasis and time allocation
- [Essential Career Coaching Questions (Quenza)](https://quenza.com/blog/essential-career-coaching-questions-guide/) — Structured reflection frameworks for uncovering transferable skills and value
- [How to Quantify Resume Bullets Without Numbers (The Muse)](https://www.themuse.com/advice/how-to-quantify-your-resume-bullets-when-you-dont-work-with-numbers) — Range estimation, frequency multiplication, cost translation techniques
- [How to Quantify Achievements on Resume (Indeed)](https://www.indeed.com/career-advice/resumes-cover-letters/how-to-quantify-resume) — "How many, how much, how long, how often" questioning framework
- [Quantifying Achievements on Executive Resume (iCareer Solutions)](https://icareersolutions.com/mastering-the-art-of-quantifying-achievements-on-an-executive-resume/) — Strategic framework for scope, frequency, and context-based quantification
- [How to Quantify Your Resume (Resume Genius)](https://resumegenius.com/blog/resume-help/how-to-quantify-resume) — Estimation approaches when exact data is unavailable
- [Prepare for Interview Using Resume (ResumeCoach)](https://www.resumecoach.com/prepare-for-your-job-interview-using-your-resume/) — How interviewers use resume as conversational roadmap and story seeding
- [interviewing.io — How SWE Behavioral Interviews Are Evaluated at Meta](https://interviewing.io/blog/how-software-engineering-behavioral-interviews-are-evaluated-meta) — Meta's 8 behavioural dimensions and level-specific expectations informing what data to capture
- [interviewing.io — Amazon Leadership Principles Guide](https://interviewing.io/guides/amazon-leadership-principles) — All 16 LPs informing competency tagging strategy
- [Big Tech Careers Newsletter — Meta Behavioral Prep](https://newsletter.bigtechcareers.com/p/part-2-how-to-prepare-for-meta-behavioral-interviews) — Quantifying impact without exact numbers, story preparation depth
