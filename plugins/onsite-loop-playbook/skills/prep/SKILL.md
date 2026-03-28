---
name: onsite-loop-playbook
description: >-
  Use this skill when the user wants to prepare for an onsite interview or loop.
  Trigger on "onsite interview", "onsite prep", "the loop", "Amazon loop",
  "Meta onsite", "Google onsite", "prepare me for the onsite at [company]",
  "system design prep for onsite", "onsite coding prep", "final round interview",
  "virtual onsite", or any request to generate a personalised onsite/loop
  preparation playbook for a specific company and role.
---

# Onsite/Loop Technical Playbook Generator

Generate a personalised, company-specific onsite/loop preparation playbook covering
system design, coding rounds, domain-specific rounds, debrief prediction, energy
management, and post-onsite tactics. This is the final, most intensive stage — typically
4-8 rounds over 4-6 hours.

**CRITICAL:** The base guide is a foundation, NOT the source of truth. Company processes
change quarterly. You MUST conduct live research for every playbook you generate.

## Required Inputs

- **Company name** (required)
- **Role category** (required — infer from context): Backend, Frontend, Security, ML/AI, Infra/DevOps/SRE, Mobile, Data, Full-Stack, Cloud Architecture, Embedded

## Optional Inputs

- **Role title**: e.g., "Senior Security Engineer"
- **Role level**: L3-L7 or Junior/Mid/Senior/Staff/Principal
- **Interviewer names**: If known, enables question prediction
- **Known loop structure**: If the recruiter shared the round breakdown
- **Career KB / STAR stories**: For mapping behavioural components in technical rounds (Amazon)

## Step 1: Read the base guide

Read the reference playbook bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "onsite-loop-technical-playbook.md" -path "*/onsite-loop-playbook/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/onsite-loop-playbook/reference/onsite-loop-technical-playbook.md --jq '.content' | base64 -d
```

This contains company loop structures, system design framework, coding patterns,
debrief mechanics, and survival tactics. Use as foundation — supplement with live research.

## Step 2: LIVE company research (MANDATORY)

### Research checklist:

1. **Glassdoor onsite reports** — Search "[company] [role] onsite interview glassdoor [year]". Read 10+ most recent reports. Extract:
   - Exact number of rounds and what each covered
   - System design questions asked
   - Coding questions asked (difficulty, patterns)
   - Any domain-specific rounds
   - Format (virtual vs in-person, tools used)

2. **Company engineering blog** — Search "[company] engineering blog". Read 3-5 recent posts relevant to the role. These predict system design topics.

3. **Company values/careers page** — Verify the current framework. Has it changed since the base guide?

4. **interviewing.io / HelloInterview** — Search for recent guides specific to this company + level.

5. **Interviewer research** (if names provided):
   - LinkedIn: team, product area, tenure
   - Conference talks, blog posts, GitHub
   - Their technical interests predict their questions

6. **Recruiter intel** — What did the recruiter share about round structure, focus areas, interviewers?

7. **Recent news** — Last 90 days. Funding, launches, reorgs affect what topics are hot.

**If live research contradicts the base guide, live research wins.**

## Step 3: Build the playbook

Write to temp file and create a GitHub gist:

1. Write: `/tmp/onsite-playbook-[company]-[role].md`
2. Gist: `gh gist create /tmp/onsite-playbook-[company]-[role].md -d "Onsite Playbook: [Company] — [Role]"`
3. Clipboard: `echo "$URL" | pbcopy 2>/dev/null`
4. Return URL

### Playbook structure

```markdown
# Onsite/Loop Playbook: [Company Name] — [Role] ([Level])

## Loop Structure (from live research)
[Exact round breakdown from Glassdoor + recruiter intel. How many rounds, what each covers, duration, who conducts, virtual vs in-person.]

| Round | Duration | Focus | Format |
|-------|----------|-------|--------|
| 1 | [time] | [coding/SD/behavioural/domain] | [tool/whiteboard] |
| 2 | ... | ... | ... |

## System Design Preparation

### Predicted Question(s)
[Based on: company domain, role category, Glassdoor reports, engineering blog topics. List 3-5 most likely questions with probability estimate.]

1. **[Question]** (High probability) — Why: [evidence from Glassdoor/blog]
   - Key components: [list]
   - Deep-dive areas: [where to go deep for this company]
   - Trade-offs to discuss proactively: [list]

2. **[Question]** (Medium probability) — Why: [evidence]

### Framework Reminder
[Company-specific time allocation. E.g., Amazon: weave LPs into SD discussion. Netflix: SD is the most important round.]

### Back-of-Envelope Numbers
[Pre-calculated estimates relevant to the predicted questions. E.g., if Uber: "10M rides/day = ~115 rides/sec"]

## Coding Preparation

### Predicted Patterns
[Based on company coding style + Glassdoor reports. Which patterns to focus final prep on.]

| Pattern | Likelihood | Company Preference | Practice Problems |
|---------|-----------|-------------------|-------------------|
| [pattern] | High | [why this company favours it] | [specific LC problems] |

### Company Coding Style Notes
[E.g., Meta: NO DP, speed over perfection. Google: layers complexity, explain process. Stripe: practical engineering, code quality > optimality.]

### Role-Category Adaptations
[If security: expect find-the-vulnerability. If frontend: expect widget building. If ML: expect implement-from-scratch. Specific to this role.]

## Domain-Specific Round Preparation
[If the loop includes domain rounds (security threat modeling, ML system design, infra debugging, etc.), detailed preparation for those.]

## Interviewer Intel
[If names provided: background, interests, predicted question topics for each. If not: general notes from Glassdoor on what interviewers focus on.]

## Debrief Prediction
[How this company's debrief works. Who has authority. What tips the balance. What would need to happen for you to get a Strong Hire vs Lean Hire.]

## Energy Management Plan
[Tailored to this company's loop length. When to eat, break strategy, the lunch situation (Apple: it's an interview. Google: it's not).]

## Post-Onsite Plan
- Thank-you emails: [individual to each interviewer, within 2 hours]
- Team matching: [if applicable — Google, Meta]
- Timeline: [expected decision timeline for this company]
- Follow-up: [when to ping recruiter if no response]

## Pre-Onsite Checklist
- [ ] Loop structure confirmed: [rounds]
- [ ] Interviewers researched: [names or "unknown"]
- [ ] Engineering blog read: [specific posts]
- [ ] System design: [N] questions practiced with full framework
- [ ] Coding: [N] problems at [difficulty] focused on [patterns]
- [ ] Domain prep: [specific topics]
- [ ] CARL stories ready: [if Amazon or other LP-integrated rounds]
- [ ] BOE numbers memorised for predicted questions
- [ ] Energy plan: [meals, snacks, breaks]
- [ ] Thank-you templates drafted
- [ ] Reverse interview questions: [5 company-specific]
- [ ] Competing timelines: [if applicable]

## Sources
[Links to every Glassdoor report, blog post, interviewing.io guide, and resource referenced.]
```

## Rules

1. **ALWAYS conduct live research.** The base guide is a starting point. Search Glassdoor, interviewing.io, company engineering blogs, and recent candidate reports. If live research contradicts the base guide, live research wins.
2. **Predict questions by triangulating.** Use company domain + role category + Glassdoor reports + engineering blog + interviewer backgrounds. Don't just list generic system design questions.
3. **Source every claim.** Link to the specific Glassdoor report or blog post.
4. **Company-specific, not generic.** Every section must be tailored. If it could apply to any company, it's not good enough.
5. **Level-calibrate.** L4 onsite prep looks fundamentally different from L6. Scope expectations, difficulty, and who-drives-the-interview all change.
6. **Role-category-aware.** Include domain-specific round prep for the user's category (security, ML, frontend, etc.).
7. **Include debrief prediction.** The user should understand how decisions are made at THIS company so they know what matters most.
8. **Include energy management.** This is a marathon. Tailor to the company's loop length and format.
9. **Include post-onsite tactics.** Thank-you emails, team matching, timeline, negotiation leverage.
10. **Output as a secret GitHub gist.** Write to temp, `gh gist create`, return URL. Requires `gh` CLI.
