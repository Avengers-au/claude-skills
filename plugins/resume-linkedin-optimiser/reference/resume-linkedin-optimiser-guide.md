# Resume & LinkedIn Optimiser: Evidence-Based Guide for Tech Roles (2025-2026)

## Overview

This document is a comprehensive, evidence-based guide for optimising resumes and LinkedIn profiles for tech roles. It covers ATS (Applicant Tracking System) reality vs myths with 2025 survey data, resume structure and action verb selection by competency, LinkedIn algorithm mechanics and recruiter search patterns, and the critical connection between your resume, LinkedIn, career knowledge base, and interview stories. Every claim is backed by recruiting industry data, ATS vendor documentation, or career coaching research.

**What IS covered:** ATS optimisation (debunking the 75% auto-rejection myth), resume formatting and content rules, action verbs by competency, LinkedIn headline/About/experience optimisation, recruiter search patterns, the story seeding technique, and the unified career data system.

**What is NOT covered:** Career data extraction (see `career-data-ingestion-guide.md`), STAR story generation (see `star-story-generator-guide.md`), or behavioural interview preparation (see `behavioural-interview-playbook.md`).

**Research date:** March 2026.

---

## Part 1: ATS Reality vs Myths (2025-2026)

### Myth 1: "75% of Resumes Are Auto-Rejected by ATS"

**False.** A 2025 HR.com survey of 384 recruiters found that **92% of recruiters manually review applications**, using ATS filters only to prioritise, not eliminate. ATS is a sorting and storage tool, not an autonomous rejection engine. However, **poorly formatted resumes can fail to parse correctly**, effectively making them invisible — not rejected, but unreadable.

### Myth 2: "Keyword Stuffing Works"

**Counterproductive in 2025.** Modern ATS systems use NLP (natural language processing) and semantic analysis — specifically Sentence-BERT embeddings and cosine similarity — to understand context, not just match exact strings. They **detect and penalise** obvious stuffing. The recommended approach is natural integration of keywords **1-3 times each**.

### Myth 3: "Only Exact Keyword Matches Count"

**Partially false.** Modern systems understand synonyms and related terms. "Project management" will partially match "programme management." However, including **both the acronym AND full form** remains important (e.g., "CI/CD (Continuous Integration/Continuous Deployment)") because some recruiter searches are still keyword-based.

### What Actually Matters for ATS

| Factor | Importance | Details |
|--------|-----------|---------|
| **Clean formatting** | Critical | No tables, columns, graphics, or images in the body |
| **Standard section headings** | Critical | "Experience," "Education," "Skills" — not creative alternatives |
| **Keywords from JD** | High | Natural integration, not stuffing; include acronyms AND full terms |
| **File format** | High | .docx is safest; PDF usually fine but some older ATS struggle |
| **Contact info NOT in header/footer** | High | Many ATS ignore header/footer content |
| **Consistent date formatting** | Medium | MM/YYYY or Month YYYY — pick one, be consistent |
| **Font choice** | Medium | Standard fonts (Arial, Calibri, Times New Roman); no decorative fonts |

### What Recruiters Actually Prioritise (2025 Survey Data)

| Priority | % of Recruiters |
|----------|----------------|
| Clear, easy to skim | 92% |
| Relevant experience and skills | 88% |
| Keywords used naturally (not stuffed) | 76% |
| Short bullet points (not paragraphs) | 72% |
| Simple, consistent formatting | 68% |
| 1-2 pages max | 64% |
| Achievements with measurable results | 52% |

### AI Screening Tools (2025 State)

Modern systems go beyond keyword matching:

- **Semantic vector analysis**: Convert resumes and job descriptions into dense vector representations, measure cosine similarity
- **Context-aware extraction**: Using KeyBERT and RapidFuzz for contextual keyword extraction
- **Skills inference**: Can infer skills from project descriptions even when not explicitly listed
- **Experience validation**: Cross-reference claimed experience duration with listed roles

---

## Part 2: Resume Optimisation

### Resume Length by Experience Level

| Experience | Recommended Length | Notes |
|------------|-------------------|-------|
| 0-5 years | 1 page | Strictly one page; no exceptions |
| 5-10 years | 1-2 pages | One page if it fits; two is acceptable |
| 10+ years | 2 pages | Expected by recruiters; three only for academic CVs |

Nearly **80% of recruiters** say content quality matters more than page count.

### Resume Structure (Top to Bottom)

```
[Name]
[Email] | [Phone] | [Location] | [LinkedIn URL] | [GitHub URL]

SUMMARY (2-3 lines — optional but recommended for senior roles)
[Your strongest value proposition with 2-3 top metrics]

EXPERIENCE
[Company Name] — [Title]                           [Date — Date]
• [Achievement bullet with quantified result]
• [Achievement bullet with quantified result]
• [Achievement bullet with quantified result]

[Previous Company] — [Title]                        [Date — Date]
• [Achievement bullet]
• [Achievement bullet]

SKILLS
[Category]: [Skill, Skill, Skill]
[Category]: [Skill, Skill, Skill]

EDUCATION
[Degree] — [University]                             [Year]
```

**IMPORTANT:** Contact info must be in the **body**, not in headers/footers. Many ATS systems ignore header/footer content entirely.

### Action Verbs by Competency

Using the right verb signals the right competency. These are ranked by impact — use verbs from the "Strong" column.

| Competency | Strong Verbs | Weak Verbs to Avoid |
|------------|-------------|---------------------|
| **Leadership** | Directed, Spearheaded, Championed, Orchestrated | Led, Managed, Oversaw |
| **Technical Execution** | Architected, Engineered, Optimised, Deployed | Worked on, Helped with |
| **Innovation** | Pioneered, Invented, Transformed, Revitalised | Was involved in, Participated |
| **Efficiency** | Streamlined, Automated, Consolidated, Accelerated | Was responsible for |
| **Collaboration** | Partnered, Liaised, Negotiated, Mediated | Assisted, Supported |
| **Analysis** | Diagnosed, Quantified, Forecasted, Validated | Looked at, Reviewed |
| **Results/Impact** | Generated, Accelerated, Exceeded, Secured | Contributed to |

**ATS killer phrases to eliminate:** "Responsible for," "Worked on," "Assisted with," "Helped," "Participated in" — these describe duties, not achievements. Every bullet should start with a strong verb and include a measurable outcome.

### The Resume Tailoring Process

For every application:

1. **Extract keywords** from the job description (especially skills, tools, and responsibilities listed first — order indicates priority)
2. **Mirror their language** naturally ("collaborate cross-functionally" if they say that, not "worked with other teams")
3. **Reorder bullet points** so the most relevant to THIS role appear first under each position
4. **Include both acronyms and full forms** (e.g., "CI/CD (Continuous Integration/Continuous Deployment)")
5. **Use each keyword 1-3 times maximum** — more is stuffing

### Common Mistakes That Get Resumes Rejected

| Mistake | Impact |
|---------|--------|
| Typos or grammatical errors | 77% of hiring managers reject immediately |
| Graphics, tables, or columns | ATS cannot parse; resume becomes invisible |
| Important info in header/footer | Many ATS systems ignore these sections |
| Inconsistent date formats | ATS misinterprets experience duration |
| Using only acronyms without full terms | Searches for full terms miss the resume |
| Duty-focused bullets without outcomes | Fails to differentiate from other candidates |
| Wrong file format | Some ATS cannot parse certain PDF types |

### The Story Seeding Technique

Every resume bullet should be a **compressed version of a story in your career knowledge base** — designed to invite the interviewer to ask about it.

**Rules for story-seeded bullets:**

1. **Contain a "hook"** — a specific, intriguing detail that invites follow-up. "Reduced transaction failure rate from 3% to 0.1%" begs "How?"
2. **Match a prepared story** — every bullet corresponds to a full CARL story you can deliver in 2-3 minutes
3. **Be selectively specific** — enough detail to show impact, enough mystery to invite questions
4. **Use metrics that prompt curiosity** — "$180K/year saved" or "zero-downtime migration" naturally leads to "Walk me through that"

**Example transformation:**

| Duty-Focused (Bad) | Story-Seeded (Good) |
|---------------------|---------------------|
| "Responsible for payment system maintenance" | "Architected zero-downtime migration of payment gateway processing $2M/month, reducing transaction failures from 3% to 0.1%" |
| "Worked on improving API performance" | "Optimised API response times from 450ms P99 to 120ms across 500M daily transactions by redesigning caching layer" |
| "Helped with team onboarding" | "Reduced new-hire ramp-up time from 6 weeks to 2 weeks by creating structured onboarding programme adopted across 3 teams" |

---

## Part 3: LinkedIn Profile Optimisation

### How Recruiters Actually Search LinkedIn

Recruiters use LinkedIn Recruiter with **Boolean search operators**: `AND`, `OR`, `NOT`, quotation marks for exact phrases, and parentheses for grouping. A typical search:

```
"Python" AND "AWS" AND ("Senior" OR "Lead") AND NOT "Manager"
```

**Key statistics:**
- Profiles with 5+ skills are **27x more likely** to be found in recruiter searches
- Keyword-optimised profiles receive **40% more profile views** and **3x more recruiter messages**
- **90% of recruiters** search LinkedIn using keywords

### LinkedIn Algorithm Ranking Factors

| Factor | Weight | What To Do |
|--------|--------|-----------|
| **Keyword relevance** | Very High | Match terms from target job descriptions |
| **Profile completeness** ("All-Star") | High | Fill every section; get to 100% completeness |
| **Engagement and activity** | High | Post, comment, share regularly |
| **Network connections** | Medium | Connect with people in target companies/roles |
| **Endorsements and recommendations** | Medium | Get endorsements on top 3-5 target skills |
| **Content freshness** | Medium | Update profile and post at least monthly |

### Headline (220 Characters Max)

The most effective formula (**R-S-I-C structure**, shown to produce **2.4x more recruiter replies**):

```
[Role] | [Speciality/Key Skills] | [Impact/Value Proposition]
```

**Examples:**
- `Senior Software Engineer | Python, AWS, Distributed Systems | Building scalable payment infrastructure`
- `Engineering Manager | Team Building, System Design | Led teams shipping to 10M+ users`
- `Security Engineer | Cloud Security, Threat Modeling, AppSec | Securing infrastructure at scale`

Keep to ~120 characters for full visibility on all devices. Front-load the most important keywords.

### About Section (2,600 Characters Max)

**Structure:**

1. **Hook** (first 2-3 lines visible before "see more"): Your strongest value proposition with 2-3 top metrics
2. **Narrative** (3-5 lines): Career story showing progression and what drives you
3. **Current focus** (2-3 lines): What you're working on now and what excites you
4. **Specialties list** (final section): Keyword-dense list of tools, technologies, and domains

**IMPORTANT:** The first 2-3 lines are all most people see. Front-load your strongest signal.

### Experience Section

- Mirror resume bullets but can be **more detailed** (LinkedIn has no length constraint)
- Include **quantified achievements** — same story seeding technique as resume
- Use keywords matching target job descriptions
- Include tools, certifications, and industry terminology

### Skills Section

- LinkedIn allows 50 skills; aim for **30-40 relevant ones**
- Reorder so **top 3 skills match target role keywords** (these are displayed prominently)
- Endorsements boost search ranking — most endorsed skills appear first by default
- Get endorsements from respected professionals for maximum credibility signal

### Signalling Availability

| Approach | Visibility | Risk |
|----------|-----------|------|
| "Open to Work" — recruiters only | Visible only to LinkedIn Recruiter users | Very low; recommended for employed job seekers |
| "Open to Work" — public green badge | Visible to everyone | 3x more outreach but may signal desperation |
| Headline signals ("Seeking opportunities") | Visible to all | Can look desperate; avoid |
| Active posting about industry topics | Signals engagement, not desperation | Best long-term strategy |

**Best practice:** Use the **recruiters-only** Open to Work setting, keep profile actively updated, and engage with content in your target industry.

---

## Part 4: The Unified Career Data System

### How Everything Connects

```
Career Knowledge Base (detailed stories, 8-12+)
    │
    ├──→ Resume (compressed stories as bullet points, tailored per role)
    │
    ├──→ LinkedIn (expanded versions, keyword-optimised for discovery)
    │
    ├──→ STAR/CARL Stories (full delivery for interviews)
    │
    └──→ Behavioural Interview Prep (stories matched to likely questions)
```

### The Flow

1. **Career KB** → source of truth with full stories, metrics, competency tags
2. **Resume** → each bullet is a compressed KB story with a hook that invites questions
3. **LinkedIn** → expanded resume bullets, keyword-optimised for recruiter Boolean search
4. **Interview** → full CARL delivery of the story the resume bullet seeded

This means: LinkedIn gets you found → Resume gets you the interview → Resume seeds questions about your best stories → Career KB provides the full stories to deliver.

### Schema Integration

Each story in the career KB should include:

| Field | Purpose |
|-------|---------|
| `resume_bullet` | 1-2 line compressed version for resume copy-paste |
| `linkedin_version` | 3-4 sentence expanded version for LinkedIn experience |
| `competency_tags` | For mapping to company frameworks during interview prep |
| `keywords` | For ATS/LinkedIn keyword matching during tailoring |

---

## Part 5: Resume Generation Workflow

### From Career KB to Tailored Resume

1. **Read the target job description** — extract keywords, required skills, priority order
2. **Read the career KB** — identify stories that match the JD requirements
3. **Select 3-5 bullets per role** — prioritise by relevance to THIS job, recency, and quantification
4. **Pull the `resume_bullet` field** from each selected story
5. **Tailor language** — mirror the JD's exact phrasing where natural
6. **Add a summary section** — 2-3 lines connecting your strongest signals to the specific role
7. **Order skills section** — put the JD's required skills first
8. **Format check** — no tables, no columns, standard headings, consistent dates, .docx output

### From Career KB to LinkedIn Profile

1. **Headline** — R-S-I-C formula using keywords from target roles
2. **About** — Hook with top 2-3 metrics, career narrative, specialties list
3. **Experience** — Pull `linkedin_version` from each story in the KB, supplemented with additional context
4. **Skills** — Extract from KB `tech_stack` and `keywords` fields across all stories; order by target role priority

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Resume not getting responses | Run it through an ATS simulator (Jobscan, ResuFit). Check for formatting issues. Ensure keywords match the JD |
| LinkedIn profile has low views | Check profile completeness score. Update headline with R-S-I-C formula. Add 30+ skills. Post/engage weekly |
| "I have no metrics" | Use the 6 quantification techniques from the career KB guide: range estimation, frequency multiplication, cost translation, scale indicators, comparison anchors, proxy metrics |
| Resume is too long | Cut oldest roles to 1-2 bullets. Remove non-relevant experience. Consolidate skills. Target 1-2 pages |
| Recruiter asked about something not on resume | This is normal — they search LinkedIn too. Ensure LinkedIn and resume tell the same story |
| ATS rejecting my PDF | Resubmit as .docx. Ensure no tables, columns, or graphics |
| LinkedIn headline too long | Keep to ~120 characters. Cut the least important keyword |

---

## Sources

- [ATS Rejection Myth Debunked: 92% of Recruiters Confirm (HR.com)](https://www.hr.com/en/app/blog/2025/11/ats-rejection-myth-debunked-92-of-recruiters-confi_mhp9v6yz.html) — Survey of 384 recruiters debunking auto-rejection myth
- [2025 ATS Technology Report (PassTheScan)](https://www.passthescan.com/blog/ats-technology-report-2025-what-changed-this-year) — NLP advances, semantic analysis, Sentence-BERT embeddings in modern ATS
- [ATS Resume Builder Myths Debunked (ResumeFlex)](https://resumeflex.com/ats-resume-builder-testing-results-and-myths-debunked-for-2025/) — Testing results showing what actually passes ATS
- [7 ATS Resume Myths Debunked 2026 (Maywise)](https://maywise.in/blog/common-ats-resume-myths-what-works-2026/) — Updated myth-busting with practical fixes
- [The 2025 Guide to ATS Hacks (AskCruit)](https://www.askcruit.com/resume/ats/trick-ats-myth) — Why keyword stuffing is counterproductive
- [AI Resume Screening Explained (Rezi)](https://www.rezi.ai/posts/ai-resume-screening) — How modern AI screening evaluates beyond keywords
- [100+ Powerful Action Verbs for Resume ATS 2025 (ResumeAdapter)](https://www.resumeadapter.com/blog/100-powerful-action-verbs-resume-ats-2025) — Categorised verb list with ATS performance notes
- [Resume Length Guide (ResumeWorded)](https://resumeworded.com/resume-length-key-advice) — Data-backed length recommendations by experience level
- [How to Tailor Resume to Job Description (Indeed)](https://www.indeed.com/career-advice/resumes-cover-letters/tailoring-resume) — Keyword mapping and mirroring technique
- [ATS Formatting Mistakes (Jobscan)](https://www.jobscan.co/blog/ats-formatting-mistakes/) — Critical formatting errors that break ATS parsing
- [Beat ATS Systems (BuildFastWithAI)](https://www.buildfastwithai.com/blogs/why-resumes-fail-ats-2025) — ATS rejection causes and statistics
- [LinkedIn Keywords Optimization Guide 2026 (ConnectSafely)](https://connectsafely.ai/articles/linkedin-keywords-optimization-guide-2026) — Algorithm ranking factors, visibility statistics
- [What Recruiters Search For on LinkedIn (Ana Goehner)](https://anagoehner.com/what-recruiters-search-on-your-linkedin-profile/) — Five sections recruiters check first, keyword mismatch as top barrier
- [LinkedIn Boolean Search for Recruiters (Leonar)](https://www.leonar.app/blog/linkedin-recruiter-boolean-search/) — Boolean search templates and recruiter patterns
- [LinkedIn Headlines That Get 2.4x More Recruiter Replies (LiGo)](https://ligosocial.com/blog/linkedin-headline-examples) — R-S-I-C headline structure data
- [LinkedIn Open to Work (Huntr)](https://huntr.co/blog/linkedin-open-to-work) — Strategic use of availability signals
- [LinkedIn Endorsements Playbook (HyperClapper)](https://www.hyperclapper.com/blog-posts/linkedin-endorsements-playbook) — Skills ordering and endorsement strategy
- [How to Quantify Resume Bullets Without Numbers (The Muse)](https://www.themuse.com/advice/how-to-quantify-your-resume-bullets-when-you-dont-work-with-numbers) — Quantification techniques
- [Prepare for Interview Using Resume (ResumeCoach)](https://www.resumecoach.com/prepare-for-your-job-interview-using-your-resume/) — Story seeding and resume as interview roadmap
