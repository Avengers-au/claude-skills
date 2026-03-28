# Behavioural Interview Playbook: The Definitive Company-Specific Guide

## Overview

This document is the definitive, evidence-backed playbook for behavioural interviews in tech company interview pipelines. The behavioural round is a dedicated 45-60 minute session of "tell me about a time" questions where candidates are scored against company-specific competency frameworks. At senior levels (L5+), behavioural is frequently the deciding factor in levelling decisions and can override strong technical performance — a former Meta hiring committee chair stated they go "directly to behavioural feedback first" when reviewing staff-level packets.

This guide is a **foundation, not the absolute source of truth**. Every company evolves its process, and the skill that accompanies this guide is designed to conduct live research on the specific company, role, and interviewers before generating a personalised playbook.

**What IS covered:** How behavioural is scored at each major company (with real candidate-reported questions), the complete question taxonomy by competency, cognitive biases to leverage, the easy outs playbook, naturalness under pressure, role-category differences, company-specific frameworks, and post-round tactics.

**What is NOT covered:** STAR/CARL story generation (see `star-story-generator-guide.md`), career data extraction (see `career-data-ingestion-guide.md`), or resume/LinkedIn optimisation (see `resume-linkedin-optimiser-guide.md`).

**Research date:** March 2026. This guide should be supplemented with live research at the time of use — company processes change frequently.

---

## Part 1: How Behavioural Interviews Are Actually Scored

### The Weight of Behavioural by Level

Behavioural weight increases dramatically with seniority:

| Level | Behavioural Weight | Evidence |
|-------|-------------------|---------|
| L3-L4 (Junior/Mid) | Moderate — primarily a disqualifier | Technical is primary signal; behavioural must not show red flags |
| L5 (Senior) | High — co-equal with system design | Begins differentiating candidates |
| L6+ (Staff+) | Often the deciding factor | "No staff-level scope there, no staff-level offer" — ex-Meta HC chair |

At Amazon, **25% of SDEs who pass the technical bar are disqualified due to behavioural concerns**. At Meta E6+, failing the behavioural round is an **automatic No Hire** regardless of technical performance.

### Company Scoring Systems

| Company | Scoring Method | Decision Mechanism |
|---------|---------------|-------------------|
| **Amazon** | "Meets/Raises/Below the bar" per LP | Interviewers vote inclined/not-inclined at debrief; Bar Raiser has veto |
| **Meta** | Hire/No-hire on confidence spectrum (low→high) + recommended level (IC4/IC5/IC6) | Hiring committee reviews packet; system design + behavioural determine level |
| **Google** | 1-4 scale per attribute (3.5+ needed for HC) + overall recommendation (SNH→SH) | Hiring committee of senior SWEs who never met you review packet |
| **Microsoft** | 6 core competencies + growth mindset | AA interviewer fills gaps; team consensus |
| **Netflix** | 5 culture traits (40-50% of total assessment) | Keeper Test lens: "Would I fight to keep this person?" |
| **Stripe** | 4 operating principles + STAR-Rigor-Reflection | "Equally or more important than technical" |
| **Anthropic** | Values + safety alignment | Safety misalignment = automatic disqualification |

---

## Part 2: Company-Specific Behavioural Frameworks

**IMPORTANT:** The questions and frameworks below represent the state of research as of March 2026. Companies evolve their processes regularly. The accompanying skill conducts live Glassdoor/interviewing.io research to supplement these foundations.

### Amazon — 16 Leadership Principles

**Structure:** 4-6 onsite rounds. Each interviewer assigned 2-3 LPs. 15-20 minutes per LP. One Bar Raiser (identity unknown) with absolute veto power.

**Most frequently tested LPs (from 500+ interview analysis):**

| LP | Frequency | Level Weight | Real Questions Reported |
|----|-----------|-------------|------------------------|
| **Customer Obsession** | Very high (all levels) | Foundational — tested in every loop | "Tell me about solving a pain point for customers" / "Time you made a decision unpopular but right for the customer" |
| **Ownership** | Very high | All levels; scope increases with level | "Important decision made without manager input" / "Time you went above and beyond your job description" |
| **Deliver Results** | High | All levels | "Project not completed on time — what happened?" / "Tell me about delivering against a tight deadline" |
| **Bias for Action** | High | All ICs | "Calculated risk requiring speed" / "Time you were first to take action" |
| **Dive Deep** | High | Senior+ | "Time you discovered a problem by diving into data others overlooked" |
| **Earn Trust** | Critical at L6+ | Dealbreaker if negative | "Time you disagreed and how you resolved it" / "Time you were transparent about trade-offs" |
| **Have Backbone; Disagree and Commit** | Critical all levels | Dealbreaker if no stories | "Time you committed to a decision you disagreed with" |
| **Think Big** | Critical at L7 | "No Think Big = no L7 offer" | "Creative idea that was hard to implement" / "Time you encouraged big risk" |

**The Bar Raiser:**
- Has absolute veto — "If the Bar Raiser says no, you do not get hired, even if every other interviewer says yes"
- You will NOT know who they are
- Evaluates 2-3 year trajectory: "Will this person raise the bar?"
- Most interviewers tend to align with the Bar Raiser's assessment at debrief

**Rules for Amazon:** Metrics are mandatory — an answer without numbers scores poorly. Use "I" not "we" (80/20 ratio). Do NOT say LP names aloud — use natural equivalents. Prepare 2 stories per LP.

### Meta — Jedi Round (5 Signal Areas)

**Structure:** One dedicated behavioural round called the "Jedi" interview. Non-standardised — interviewers ask what they want. Medium-low importance at baseline, but **veto function at E6+**.

**Five signal areas with level expectations:**

| Signal Area | IC4 (Mid) | IC5 (Senior) | IC6 (Staff) |
|-------------|-----------|-------------|-------------|
| **Driving Results** | Feature-level impact | Project-level, cross-functional | Goal-level, long-term team health |
| **Embracing Ambiguity** | Ambiguous task, few stakeholders | Ambiguous project, team/org stakeholders | Two+ teams, org stakeholders |
| **Resolving Conflicts** | Implementation disagreements | Direction disagreements with leads | Disagreements between 2+ teams |
| **Growing Continuously** | Learning new technology | Skills affecting entire team | Skills affecting 2+ teams |
| **Communicating Effectively** | Clear within team | Clear across team boundaries | Clear across org and to leadership |

Plus unofficial sixth: **Scope** — "you might be 'Growing Continuously' at E3 but that looks very different than at E6."

**Real Jedi round questions:** "Time you worked with a difficult person" / "Time you worked on something outside your OKR" / "Project you're most proud of" / "Time you received constructive feedback" / "Time you showed leadership" / "Time a project took longer than expected"

**Key insight:** Coding decides "should we hire?" — system design and behavioural decide "how should we level?"

### Google — Googleyness & Leadership

**Structure:** One dedicated G&L interview. Mix of STAR + hypothetical questions. Hiring committee (senior SWEs who never met you) makes final decision.

**Four hiring attributes:**
1. **Role-Related Knowledge (RRK)** — domain expertise
2. **General Cognitive Ability (GCA)** — problem-solving, learning agility
3. **Leadership** — emergent leadership (stepping up when needed, not positional)
4. **Googleyness** — comfort with ambiguity, intellectual humility, bias for action, collaboration

**Scoring:** 1-4 scale. 4.0 = Strong Hire, 3.5 = Hire, 3.0 = Borderline, 2.5 = No Hire. Average 3.5+ needed.

**Real questions:** "A decision you made that you would change and why" / "Something you did that benefited the team — did people agree?" / "Imagine you work in a negative culture — what would you do?" / "If you were CEO of Google, what would you change?"

**Key differentiator from Amazon:** Google evaluates "emergent leadership" not LP-driven structured assessment. More hypothetical/situational questions. Hiring committee (strangers) decides, not interviewers.

### Apple — Decentralised, Craft-Obsessed

**Structure:** No company-wide standardised questions. Each team creates custom questions. Interviews may be cut short if you underperform.

**What Apple probes:**
- **Secrecy comfort:** Working effectively with limited information, delivering without seeing the full picture
- **Craft obsession:** "'It works' is not good enough; it has to work beautifully"
- **"Why Apple?" passion test:** "If I didn't feel their passion, that's usually a red flag" — disproportionate weight on motivation
- **"1+1=3" collaboration:** How you made team output exceed the sum of individual contributions
- **Privacy:** "Privacy is huge" — embedded in the interview, not just marketing

### Microsoft — Growth Mindset + AA Round

**Structure:** 4-5 back-to-back rounds. Final "As-Appropriate" (AA) interview with senior executive fills gaps — if behavioural was weak earlier, AA will focus heavily on it.

**Six core competencies:** Collaboration, Drive for Results, Customer Focus, Influencing for Impact, Judgment, Adaptability.

**Real questions:** "Time you were given a task but the client wanted you to pivot" / "Greatest failure and what you learned" / "Time you resolved a conflict within your team" / "Influencing without authority"

### Netflix — Culture Is 40-50% of Assessment

**Five core traits:** Candor, Context over Control, Self-Motivation, Accountability, Curiosity & Growth.

**The Keeper Test:** Managers ask: "If this person wanted to leave, would I fight to keep them?" Hiring managers evaluate candidates through this lens.

**Real questions:** "How have you demonstrated freedom and responsibility?" / "Time you gave and received direct feedback" / "What would you do if your manager was making a harmful decision?" / "Time you delivered results with minimal direction"

**Key:** Overly diplomatic answers signal poor cultural alignment. Netflix expects directness with respect.

### Stripe — Behavioural ≥ Technical

**Four principles tested:** Users First, Think Rigorously, Craft, Ownership.

**Real questions:** "Time you advocated for the user" / "Walk me through a complex technical decision — how did you evaluate alternatives?" / "Time you owned a project start to finish" / "Disagreement with a teammate"

**Strong hire = STAR + Rigor + Reflection:** Must include reasoning ("Why A over B") AND learning. Standard STAR without rigor falls flat.

### Anthropic — Safety Is Non-Negotiable

**Real questions:** "Time you made a safety-related decision" / "What's your biggest concern about AI?" / "If privacy measures reduce model performance, how would you balance these trade-offs?" / "What do you see as the greatest future safety risk from generative AI?"

**Disqualification flags:** Lone wolf tendencies, overconfidence, purely financial motivation, dismissing ethical concerns, claiming issues can be "fixed later."

**Strong signals:** Systematic risk evaluation, red-teaming approach, intellectual humility, genuine safety conviction (not just awareness).

---

## Part 3: The Psychology of Behavioural Decisions

### The Biases That Determine Your Outcome

Interviewers are NOT rational evaluators despite structured rubrics. These biases operate consistently:

| Bias | Evidence | Tactical Application |
|------|----------|---------------------|
| **Primacy / First impression** | 69% of decisions made within first 5 minutes (Journal of Occupational Psychology, 2015). University of Toledo: outcomes predicted from first 10 seconds | Your first answer is not a warm-up — it sets the frame for everything. Lead with your highest-scope, strongest story |
| **Anchoring** | 30% of hiring decisions swayed by first data point (NBER) | The scope of your first story becomes the anchor. If you open with individual-task scope, you're anchored at L4 regardless of later answers |
| **Halo effect** | One positive trait generalises across all dimensions (Westbury & King, 2024 — *Cognitive Science*) | Lead with your single strongest competency. The halo extends to weaker areas |
| **Confirmation bias** | After initial impression, interviewers seek confirming evidence and discount contradicting evidence | Make your first impression positive. Ambiguous later answers will be interpreted charitably |
| **Peak-end rule** | People judge experiences by the peak moment and the ending (Kahneman) | Save a strong story for your final answer. Close with genuine enthusiasm |

### How Interviewers Actually Decide

Despite scoring rubrics, the process is substantially subjective:
- Structured interviews have predictive validity of **.51** (vs .38 for unstructured) — still far from perfect (Schmidt & Hunter meta-analysis, 100 years of research)
- At Meta, scores are "designed to spark discussion" — **not used mathematically**
- Each interviewer presents ~10 minutes using the candidate's own words, then gives ranking
- Different interviewers observing identical behaviour perceive different signals

---

## Part 4: The Easy Outs Playbook

### "What's Your Weakness?"

**What ACTUALLY works (calibrated by company type):**

| Company Type | Effective Weakness | Why It Works |
|-------------|-------------------|-------------|
| FAANG/Big Tech | Process-oriented with mechanical fix: "I over-invest in solo debugging before asking for help. I now use the One Hour Rule — if I haven't made progress in 60 min, I reach out" | Shows self-awareness + systematic mitigation |
| Startups | Growth-oriented: "I tend to over-engineer. I've learned to explicitly ask 'what's the simplest thing that works?' and timebox design" | Aligns with startup pragmatism |
| AI Labs | Humility-oriented: "I sometimes underestimate how much context others need. I now front-load architectural decisions in written RFCs before discussing verbally" | Signals the intellectual humility Anthropic/OpenAI value |

**Universal structure:** Real weakness → specific example of it causing problems → concrete mechanical mitigation → evidence it's working. 60-90 seconds max.

### Being Fired

- Be truthful (lies surface through references)
- 2-3 sentences max: "The role wasn't the right fit for my working style at the time"
- Name ONE concrete lesson learned
- Pivot immediately to why THIS role is the right fit
- Never blame others

### Short Tenure (<1 year)

- Median tenure for 25-34 year olds is now ~2.8 years (2024 BLS)
- Lead with accomplishments: what you delivered in that period
- Create a coherent narrative connecting moves to growth
- Address proactively, don't wait for them to ask
- Explain what THIS role offers that previous ones didn't

### Career Gaps

**79% of hiring managers would hire someone with an employment gap** if properly explained.

| Gap Type | Strategy |
|----------|---------|
| Sabbatical | Present as deliberate choice. "I took intentional time to [activity]. I also [professional development]" |
| Health | "I took time to address a medical issue, now resolved. Fully ready to return." No diagnosis needed |
| Caregiving | "I was primary caregiver for [family member]. During that time I [transferable skills]" |
| Couldn't find work | "The market was challenging. I used the time to [upskilling]. That preparation is why I'm stronger now" |

### "Tell Me About a Conflict" When It Was YOUR Fault

**This is actually a strong answer if framed correctly.** It demonstrates the rarer combination of self-awareness, accountability, and growth:

1. Acknowledge your role immediately
2. Show self-awareness of WHY you acted that way
3. Detail how you repaired the relationship
4. Name the systemic change you made
5. Result: relationship stronger/more productive

### Overqualified for the Role

Address proactively: "I know my background might seem senior. Here's why I'm genuinely excited: [specific reasons]." Counter flight risk with evidence of long tenures. Frame experience as benefit: "I can be productive from day one."

---

## Part 5: Appearing Natural Under Pressure

### The Stanislavski Method for Interviews

Professional actors achieve "natural" delivery through techniques directly applicable:

- **The "Magic If":** Instead of reciting, ask: "How would I tell a friend this story right now?" — activates genuine emotional memory
- **Emotion Memory:** Let traces of real emotion show. If the failure made you anxious, a trace of that signals authenticity
- **Character Objectives:** Know the competency signal for each answer before speaking

### Memorisation (Bad) vs Internalisation (Good)

| Memorisation | Internalisation |
|-------------|----------------|
| Word-for-word recitation | Key beats with natural variation |
| Breaks when question varies | Adapts to any phrasing |
| Misaligned body language | Authentic alignment |
| Obvious to experienced interviewers | Indistinguishable from spontaneity |

**Process:** Write the answer → Read aloud → Put away and retell from memory (wording WILL differ — that's correct) → Practice with 3-5 question variations

### Spontaneity Markers

To sound natural, incorporate:
- **Self-corrections:** "Actually, let me clarify — it was Q3, not Q2"
- **Thinking pauses:** 1-2 seconds of genuine recall before specific details
- **Emotional inflection:** Energy rises for exciting parts, drops for reflective parts
- **Tangent awareness:** "I'm going on a tangent — let me get back to the key point"

### Vocal Variety

**Monotone delivery kills even great content.** Vary:
- **Speaking rate:** Faster for enthusiasm, slower for serious points
- **Pitch/volume:** Higher for key moments, lower for reflection
- **Strategic pausing:** 2-3 second pause before your key result is more powerful than rushing through

### Recovering from Lost Train of Thought

1. **Name it:** "Let me think for a second — I want to get this detail right" (reads as thoughtfulness)
2. **Recap:** Paraphrase what you've said — often triggers recall
3. **Bridge to conclusion:** "The key takeaway was..." and land on the result

---

## Part 6: Role-Category Behavioural Differences

Behavioural expectations differ significantly by role. The same "conflict" question expects different types of stories:

| Role Category | Distinctive Focus | Story Themes Expected |
|--------------|-------------------|----------------------|
| **Security Engineering** | Integrity, confidentiality, ethical reasoning, incident composure | Enforcing policy against senior stakeholders; managing vulnerability disclosure; balancing business needs with security |
| **Frontend Engineering** | User empathy, design collaboration, accessibility, performance mindset | Pushing back on designs for technical reasons; championing accessibility; optimising perceived speed |
| **Backend/Infrastructure** | Systems thinking, operational awareness, incident response, scalability | Diagnosing cascading failures; designing for graceful degradation; making the business case for reliability |
| **ML Engineering** | Research-to-production bridge, cross-team translation, experiment methodology | Taking a paper to production; working with non-ML teams on requirements; designing rigorous A/B tests |
| **Engineering Management** | Difficult conversations, team building, technical leadership through influence | Addressing underperformance; building teams from scratch; resolving cross-functional priority conflicts |
| **Data Engineering** | Stakeholder management, data quality advocacy, cross-functional communication | Explaining data concepts to non-technical stakeholders; pushing back on "good enough" data quality |

---

## Part 7: The Meta-Game

### The First Answer Sets Everything

Down-levelling occurs on the back of behavioural alone. Your first answer must demonstrate scope appropriate to your target level:

| Target Level | First Answer Must Show |
|-------------|----------------------|
| L3-L4 | Individual initiative, learning orientation, appropriate help-seeking |
| L5 | Team-level leadership, cross-functional facilitation, impact requiring 3+ people |
| L6 | Org-level strategy, multi-team coordination, influence requiring 2+ teams |
| L7 | Company-wide impact, setting strategic direction |

### Building a Narrative Arc

Treat the round as one story about who you are:
1. **Opening:** Strongest, highest-scope story (sets the anchor)
2. **Middle:** Breadth — different competencies, contexts, team sizes, technical domains
3. **Closing:** Growth/learning story, ending forward-looking

**Avoid:** All stories from the same project, team, or time period. Interviewers want **repeatable behaviour across contexts**.

### Reading Interviewer Signals

| Signal | Meaning | Adjust |
|--------|---------|--------|
| Leaning in, steady nods | Engaged — keep going | Go slightly deeper |
| Active note-taking | Capturing signal — good | Continue |
| Checking watch, fidgeting | Running long | Accelerate to result |
| "Can you tell me more about X?" | Strong positive — they want deeper evidence | Go deep on exactly what they asked |
| "Let's move on" | Either sufficient signal or need to cover more ground | Shorten subsequent answers |

### How Behavioural Interacts with Technical at Debrief

- At Meta, HC chairs read **behavioural feedback first** for senior/staff packets
- Behavioural is the **primary determinant of levelling** — "there are only so many ways to invert a binary tree, and that's not what senior engineers are for"
- A strong behavioural can offset borderline technical at senior+ levels
- A weak behavioural rarely gets overridden by strong technical, especially at L5+

---

## Part 8: 2025-2026 Trends

### What's Changing

- **Scenario-based questions rising:** 41% of companies moving from "tell me about a time" toward "walk me through how you'd handle this scenario"
- **In-person behavioural rounds:** Rose from 24% (2022) to 38% (2025) — partly to counter AI-assisted prep
- **Deeper probing:** 47% of hiring teams updated techniques to probe deeper as candidates use AI to prepare
- **Behavioural weight increasing:** Now accounts for ~90% of hiring manager assessment focus across industries (2026 hiring trends report)
- **Companies adapting to AI-prepped candidates:** 77% regularly encounter AI-assisted applications. Interviewers look for genuine depth vs polished surface

### What This Means for Preparation

The bar for naturalness is higher than ever. Rehearsed, template-sounding answers are more detectable because interviewers are now specifically trained to distinguish AI-coached answers from authentic responses. The winning strategy: **internalise frameworks deeply enough that delivery is genuinely spontaneous**, while the underlying structure remains sound.

---

## Part 9: Post-Round Tactics

### Follow-Up Email

Within 24 hours. 3-4 sentences max:
1. Reference a specific topic that sparked good discussion
2. Briefly extend it with one addendum you didn't mention
3. Do NOT repeat generic "thank you for your time"

### Addressing a Flubbed Answer

**Decision framework:** Is the error significant enough to misrepresent your capabilities? If yes, briefly address: "I reflected on our discussion about [topic] and realised I didn't capture [point]. A more complete answer includes [2-3 sentences]." Never apologise at length.

### Self-Debrief (Within 1-2 Hours)

1. Record each question and your answer (bullet points)
2. Rate each 1-5 on competency demonstration
3. Note interviewer reactions: where they leaned in, cut off, asked follow-ups
4. Identify the stronger story you could have told
5. Update story bank tags and fill gaps

---

## Quick Reference — Pre-Round Checklist

```
□ Identified company's behavioural framework (LPs / dimensions / attributes / values)
□ Researched recent Glassdoor behavioural interview reports for this company + role
□ Mapped 8-12 CARL stories to the company's competency model
□ First-answer story selected: highest scope, strongest competency, level-appropriate
□ Easy outs prepared: weakness, "why leaving?", failure story, conflict story
□ Follow-up prep for each story: "Why?", "What else?", "What would you change?", "Your specific role?"
□ Coverage matrix reviewed: every critical competency has 2+ stories
□ Practiced out loud with natural variation (NOT memorised scripts)
□ Reverse interview questions prepared (company-specific, not generic)
□ Quiet environment, water, notes accessible but not reading from them
```

---

## Sources

- [interviewing.io — How SWE Behavioral Interviews Are Evaluated at Meta](https://interviewing.io/blog/how-software-engineering-behavioral-interviews-are-evaluated-meta) — Meta's 5 signal areas, IC4-IC6 scope expectations, hire/no-hire confidence spectrum
- [interviewing.io — Amazon Leadership Principles Guide](https://interviewing.io/guides/amazon-leadership-principles) — 500+ interview analysis, LP frequency, Bar Raiser veto, 25% behavioural rejection rate
- [interviewing.io — Apple Hiring Process](https://interviewing.io/guides/hiring-process/apple) — Decentralised process, secrecy culture, craft obsession, passion test
- [interviewing.io — Meta/Facebook Hiring Process](https://interviewing.io/guides/hiring-process/meta-facebook) — Jedi round, E6+ veto function, behavioural determines levelling
- [OphyAI — Amazon LP Interview Guide](https://ophyai.com/blog/company-guides/amazon-leadership-principles-interview-guide) — Bar Raiser mechanics, metrics mandatory, question examples per LP
- [The Scarlet Ink — Interviewing at Amazon](https://www.scarletink.com/interviewing-at-amazon-leadership-principles/) — Customer Obsession and Ownership as most common, Bar Raiser depth
- [Big Tech Careers Newsletter — Meta Behavioral](https://newsletter.bigtechcareers.com/p/part-1-mastering-the-meta-behavioral-interview) — Five signal areas with definitions, E4/E5/E6 expectations
- [IGotAnOffer — Googleyness & Leadership Questions](https://igotanoffer.com/blogs/tech/googleyness-leadership-interview-questions) — G&L format, real question examples
- [Team Rora — Google Interview Process](https://www.teamrora.com/post/recruiters-perspective-on-the-google-interview-process) — HC composition, four attributes, behavioural red flags as disqualifiers
- [The Interview Guys — Netflix Interview Questions](https://blog.theinterviewguys.com/netflix-interview-questions-and-answers/) — 40-50% culture, Keeper Test, real questions
- [codinginterview.com — Stripe Behavioral](https://www.codinginterview.com/guide/stripe-behavioral-interview-questions/) — STAR + Rigor + Reflection, operating principles
- [LinkJob.ai — Anthropic Safety Question Bank](https://www.linkjob.ai/interview-questions/anthropic-safety-interview-question-bank-guideline/) — Safety questions, Lone Wolf red flag, values assessment
- [LinkJob.ai — Palantir Interview Process](https://www.linkjob.ai/interview-questions/palantir-interview-process-questions/) — Ethics questions, mission alignment, recruiter as heavy filter
- [Exponent — Microsoft Interview Process](https://www.tryexponent.com/blog/microsoft-interview-process) — AA interviewer role, six competencies, growth mindset
- [eng-leadership.com — Senior Behavioral](https://newsletter.eng-leadership.com/p/how-to-nail-big-tech-behavioral-interviews) — Decode-Select-Deliver, scope as levelling mechanism, HC chair quote
- [Hello Interview — Ace FAANG Behavioral](https://www.hellointerview.com/blog/ace-faang-behavioral-interview) — Level expectations E3-E6, down-levelling dynamics
- [Schmidt & Hunter Meta-Analysis](https://firstpersonnel.org/wp-content/uploads/2013/10/Summary-Schmidt-Hunter-1998.pdf) — Structured interview validity .51, 100 years of research
- [First Impressions in Hiring (Eddy)](https://eddy.com/hr-encyclopedia/first-impression-effect/) — University of Toledo 10-second study, 69% decision in 5 minutes
- [A Constant Error, Revisited (PMC, 2024)](https://pmc.ncbi.nlm.nih.gov/articles/PMC11614318/) — Updated halo effect research
- [Confirmation Bias in Interviews (Plum)](https://www.plum.io/blog/the-issue-with-the-interview-confirmation-bias) — How interviewers seek confirming evidence
- [Peak-End Rule in Interviews (Aspect HQ)](https://aspect-hq.com/hiring-decisions-psychology/kahneman-s-peak-end-rule-in-interviews) — Kahneman's peak-end applied to hiring
- [Does Being Authentic Help Candidates? (UCL)](https://onlinelearning.ucl.ac.uk/resources/authenticity-job-candidates/) — 26% hire rate increase for authentic candidates
- [HBR — How to Explain Job Hopping (2024)](https://hbr.org/2024/09/how-to-explain-job-hopping-in-an-interview) — Coherent narrative approach
- [Career Gaps (Wonsulting)](https://www.wonsulting.com/job-search-hub/how-to-talk-about-a-sabbatical-or-career-gap-without-feeling-awkward) — 79% would hire with explained gap
- [Stanislavski Method (MasterClass)](https://www.masterclass.com/articles/stanislavski-method) — Magic If, emotion memory for natural delivery
- [Paul Ekman — Micro Expressions](https://www.paulekman.com/resources/micro-expressions/) — Nonverbal leakage, Othello Error
- [InterviewQuery — AI Interview Trends 2025](https://www.interviewquery.com/p/ai-interview-trends-tech-hiring-2025) — In-person rounds rising, deeper probing, AI adaptation
- [Onrec — Hiring Trends 2026](https://www.onrec.com/news/news-archive/hiring-trends-report-2026-study-finds-ai-pushing-employers-away-from-traditional) — 77% encounter AI-assisted apps, 47% updated techniques, 90% behavioural focus
